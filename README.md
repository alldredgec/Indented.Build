# Indented.Build

Indented.Build centralises the build processes / scripts used by my modules.

The goal of this module is to act as a means of accessing and executing a well maintained set of steps which can apply across a very large module base (public and private).

My build process avoids use of dedicate build task runners such as psake or Invoke-Build on the basis that managing execution of the process is the smallest problem. The process is a bunch of sequentially executed functions with a very short overall build time.

The executor can only be used with PowerShell 5.0 or higher.

# Required modules

* Poshcode\Configuration
* Pester

# Optional modules

* platyPS
* PSScriptAnalyzer

# Tasks

 - [ ] Build
   - [x] Clean
   - [x] TestSyntax
   - [x] TestAttributeSyntax
   - [x] CopyModuleFiles
   - [x] Merge
   - [ ] CompileClass
     * When module\class\*.cs exist, and module\class\*.*proj and module\class\*.sln do not exist.
   - [x] BuildProject
     * When module\class\*.*proj exists and module\class\*.sln does not.
   - [x] BuildSolution
     * When module\class\*.sln exists.
   - [x] ImportDependencies
     * When module\modules.config exists.
   - [x] UpdateMetadata
 - [ ] Test
   - [x] TestModuleImport
   - [x] PSScriptAnalyzer
     * When the release type is minor or greater.
   - [x] TestModule
   - [x] TestSolution
     * When module\class\*.sln exists, and the nunitconsole (nuget package) has been restored.
 - [ ] Release
   - [ ] UpdateCatalog
     * When a code signing certificate is available.
   - [ ] SignModule
     * When a code signing certificate is available.
   - [ ] UpdateMarkdownHelp
     * When platyPS is available.
   - [ ] UpdateVersion
 - [ ] Publish
   - [ ] PublishGitHubRelease
   - [ ] PublishToCurrentUser
   - [ ] PublishToPSGallery