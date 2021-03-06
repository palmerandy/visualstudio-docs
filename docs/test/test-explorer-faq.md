---
title: "Visual Studio Test Explorer FAQ"
ms.date: 1/15/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
  - "Test Explorer"
  - "Test window"
  - "Visual Studio Test Explorer"
  - "summary line"
  - "unit tests"
  - "Test Explorer FAQ"
ms.author: "kehavens"
ms.workload:
  - "multiple"
author: kendrahavens
manager: douge
---
# Visual Studio Test Explorer FAQ

## Dynamic test discovery
**The Test Explorer is not discovering my tests that are dynamically defined. (For example, theories, custom adapters, custom traits, #ifdefs, etc.) How can I discover these tests?**

  Build your project and make sure assembly-based discovery is turned on in **Tools** > **Options** > **Test**.

  [Real time test discovery](https://go.microsoft.com/fwlink/?linkid=862824) is source-based test discovery. It can’t discover tests that use theories, custom adapters, custom traits, `#ifdef` statements, etc. because they're defined at runtime. A build is required for those tests to be accurately discovered. In Visual Studio 2017 version 15.6 and later, assembly-based discovery (the traditional discoverer) runs only after builds. This setting means Real Time Test Discovery discovers as many tests as it can while you're editing, and assembly-based discovery allows dynamically defined tests to appear after a build. Real Time Test Discovery improves responsiveness, but stills allow you to get complete and accurate results after a build.

## Test Explorer '+' (plus) symbol
**What does the '+' (plus) symbol that appears in the top line of Test Explorer mean?**

  The '+' (plus) symbol indicates that more tests may be discovered after a build as long as assembly-based discovery is turned on. It appears if dynamically defined tests are detected in your project.

  ![Plus symbol summary line](media/testex-plussymbol.png)

## Assembly-based discovery
**Assembly-based discovery is no longer working for my project. How do I turn it back on?**

  Go to **Tools** > **Options** > **Test** and check the box for **Additionally discover tests from built assemblies after builds.**

  ![Assembly-based option](media/testex-toolsoptions.png)

## Real time test discovery
**Tests now appear in Test Explorer while I type, without having to build my project. What changed?**

  This feature is called [Real time test discovery](https://go.microsoft.com/fwlink/?linkid=862824). It uses a Roslyn analyzer to discover tests and populate Test Explorer in real time, without requiring you to build your project. For more information about test discovery behavior for dynamically defined tests such as theories or custom traits, see FAQ #1 .

## Real time test discovery compatibility
**What languages and test frameworks can use Real Time Test Discovery?**

  [Real time test discovery](https://go.microsoft.com/fwlink/?linkid=862824) only works for the managed languages (C# and Visual Basic), since it is built using the Roslyn compiler. For now, Real Time Test Discovery only works for the xUnit, NUnit, and MSTest frameworks.

## Test Explorer logs
**How can I turn on logs for the Test Explorer?**

  Navigate to **Tools** > **Options** > **Test** and find the Logging section there.

## UWP test discovery
**Why are my tests in UWP projects not discovered until I deploy my app?**

  UWP tests target a different runtime when the app is deployed. This means that to discover tests accurately for UWP projects you not only need to build your project, but also deploy.

## Test Explorer sorting
**How does sorting test results work in the hierarchy view?**

  The hierarchy view sorts tests alphabetically as opposed to by outcome. The other group by settings normally sort test results by outcome and then alphabetically. See the different group by options in the following image for comparison. You can provide feedback about the design [in this GitHub issue](https://github.com/Microsoft/vstest/issues/1425).

  ![SortingExamples](media/testex-sortingex.png)

## Test Explorer hierarchy view
**In the hierarchy view, there are passed, failed, skipped, and not run icons next to the Project, Namespace, and Class groupings. What do these icons mean?**

  The icons next to the Project, Namespace, and Class groupings reflect the state of the tests within that grouping. See the following table.

  ![Test Explorer Hierarchy Icons](media/testex-hierarchyicons.png)

## Search by file path
**There is no longer a "File Path" filter in the Test Explorer search box.**

The file path filter in the **Test Explorer** search box was removed in Visual Studio 2017 version 15.7 preview 3. This feature had low usage, and the Test Explorer can retrieve test methods faster by excluding this feature. If this change interrupts your development flow, please let us know by submitting feedback on [Developer Community](https://developercommunity.visualstudio.com/).

## Test adapter NuGet reference
**In Visual Studio 2017 version 15.8 my tests are discovered, but don't execute.**

All test projects must include their .NET test adapter NuGet reference in their .csproj file. If they don't, the following test output appears on the project if discovery by a test adapter extension is kicked off after a build, or if the user tries to run the selected tests: 

**Test project {} does not reference any .NET NuGet adapter. Test discovery or execution might not work for this project. It is recommended to reference NuGet test adapters in each .NET test project in the solution.**

Instead of using test adapter extensions, projects are required to use test adapter NuGet packages. This greatly improves performance and causes fewer issues with continuous integration. Read more about .NET Test Adapter Extension deprecation in the [release notes](/visualstudio/releasenotes/vs2017-preview-relnotes#testadapterextension).

> [!NOTE]
> If you are using the NUnit 2 Test Adapter and are unable to migrate to the NUnit 3 test adapter, you can turn off this new discovery behavior in Visual Studio version 15.8 in **Tools** > **Options** > **Test**. 

  ![Test Explorer Adapter behavior in tools options](media/testex-adapterbehavior.png)

## UWP TestContainer was not found
**My UWP tests are no longer being executed in Visual Studio 2017 version 15.7 and higher.**

Recent UWP test projects specify a test platform build property that allows better performance for identifying test apps. If you have a UWP test project that was initialized before Visual Studio version 15.7 you may see the following error in **Output** > **Tests**:

**System.AggregateException: One or more errors occurred. ---> System.InvalidOperationException: The following TestContainer was not found {} at Microsoft.VisualStudio.TestWindow.Controller.TestContainerProvider <GetTestContainerAsync>d__61.MoveNext()**
  
To fix this:
- Update your test project build property to the following:

```XML
<UnitTestPlatformVersion Condition="'$(UnitTestPlatformVersion)' == ''">$(VisualStudioVersion)</UnitTestPlatformVersion>
```

- Update the TestPlatform SDK version to the following:

```XML
<SDKReference Include="TestPlatform.Universal, Version=$(UnitTestPlatformVersion)" />
```

## Using feature flags
**How can I turn on feature flags to try out new testing features?**

Feature flags are used to ship experimental or unfinished parts of the product to avid users who would like to give feedback before the features ship officially. They may destabilize your IDE experience. Use them only in safe development environments, such as virtual machines. Feature flags are always use-at-your-own-risk settings. You can turn on experimental features with the [feature flags extension](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.FeatureFlagsExtension), or through the developer command prompt.

![Feature Flag Extension](media/testex-featureflag.png)

To turn on a feature flag through the Visual Studio developer command prompt, use the following command. Change the path to where Visual Studio is installed on your machine, and change the registry key to the desired feature flag.

```shell
vsregedit set “C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise" HKLM FeatureFlags\TestingTools\UnitTesting\HierarchyView Value dword 1
```

> [!NOTE]
> You can turn off the flag with the same command, by using a value of 0 instead of 1 after dword.

## See also

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=fullName>
- [Create and run unit tests for existing code](http://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173)
- [Unit test your code](unit-test-your-code.md)
- [Live unit testing FAQ](live-unit-testing-faq.md)
