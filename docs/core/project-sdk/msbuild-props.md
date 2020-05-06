---
title: Microsoft. NET. SDK için MSBuild özellikleri
description: .NET Core SDK anlayan MSBuild özelliklerine yönelik başvuru.
ms.date: 02/14/2020
ms.topic: reference
ms.openlocfilehash: 800ff59310d8437d7f770bf20a5bdf37714f8515
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795579"
---
# <a name="msbuild-properties-for-net-core-sdk-projects"></a><span data-ttu-id="ae72f-103">.NET Core SDK projeleri için MSBuild özellikleri</span><span class="sxs-lookup"><span data-stu-id="ae72f-103">MSBuild properties for .NET Core SDK projects</span></span>

<span data-ttu-id="ae72f-104">Bu sayfa, .NET Core projelerini yapılandırmaya yönelik MSBuild özelliklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="ae72f-104">This page describes MSBuild properties for configuring .NET Core projects.</span></span> <span data-ttu-id="ae72f-105">Özelliğin alt öğeleri olarak her bir özellik için *meta verileri* belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ae72f-105">You can specify *metadata* for each property as child elements of the property.</span></span>

> [!NOTE]
> <span data-ttu-id="ae72f-106">Bu sayfa devam eden bir çalışmadır ve .NET Core SDK için tüm yararlı MSBuild özelliklerini listelemez.</span><span class="sxs-lookup"><span data-stu-id="ae72f-106">This page is a work in progress and does not list all of the useful MSBuild properties for the .NET Core SDK.</span></span> <span data-ttu-id="ae72f-107">Ortak MSBuild özelliklerinin bir listesi için bkz. [Ortak MSBuild özellikleri](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="ae72f-107">For a list of common MSBuild properties, see [Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="framework-properties"></a><span data-ttu-id="ae72f-108">Çerçeve özellikleri</span><span class="sxs-lookup"><span data-stu-id="ae72f-108">Framework properties</span></span>

- [<span data-ttu-id="ae72f-109">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="ae72f-109">TargetFramework</span></span>](#targetframework)
- [<span data-ttu-id="ae72f-110">Targetçerçeveler</span><span class="sxs-lookup"><span data-stu-id="ae72f-110">TargetFrameworks</span></span>](#targetframeworks)
- [<span data-ttu-id="ae72f-111">Netstandardımplicitpackageversion</span><span class="sxs-lookup"><span data-stu-id="ae72f-111">NetStandardImplicitPackageVersion</span></span>](#netstandardimplicitpackageversion)

### <a name="targetframework"></a><span data-ttu-id="ae72f-112">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="ae72f-112">TargetFramework</span></span>

<span data-ttu-id="ae72f-113">`TargetFramework` Özelliği, bir [metapackage](../packages.md#metapackages)örtük olarak başvurduğu uygulamanın hedef Framework sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="ae72f-113">The `TargetFramework` property specifies the target framework version for the app, which implicitly references a [metapackage](../packages.md#metapackages).</span></span> <span data-ttu-id="ae72f-114">Geçerli hedef çerçeve takma adların listesi için bkz. [SDK stili projelerde hedef çerçeveler](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="ae72f-114">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>
```

<span data-ttu-id="ae72f-115">Daha fazla bilgi için bkz. [SDK stili projelerde hedef çerçeveler](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="ae72f-115">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="targetframeworks"></a><span data-ttu-id="ae72f-116">Targetçerçeveler</span><span class="sxs-lookup"><span data-stu-id="ae72f-116">TargetFrameworks</span></span>

<span data-ttu-id="ae72f-117">Uygulamanızın birden `TargetFrameworks` çok platformu hedeflemesini istediğinizde özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ae72f-117">Use the `TargetFrameworks` property when you want your app to target multiple platforms.</span></span> <span data-ttu-id="ae72f-118">Geçerli hedef çerçeve takma adların listesi için bkz. [SDK stili projelerde hedef çerçeveler](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="ae72f-118">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

> [!NOTE]
> <span data-ttu-id="ae72f-119">`TargetFramework` (Tekil) belirtilmişse bu özellik yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="ae72f-119">This property is ignored if `TargetFramework` (singular) is specified.</span></span>

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
</PropertyGroup>
```

<span data-ttu-id="ae72f-120">Daha fazla bilgi için bkz. [SDK stili projelerde hedef çerçeveler](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="ae72f-120">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="netstandardimplicitpackageversion"></a><span data-ttu-id="ae72f-121">Netstandardımplicitpackageversion</span><span class="sxs-lookup"><span data-stu-id="ae72f-121">NetStandardImplicitPackageVersion</span></span>

> [!NOTE]
> <span data-ttu-id="ae72f-122">Bu özellik yalnızca kullanan `netstandard1.x`projeler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="ae72f-122">This property only applies to projects using `netstandard1.x`.</span></span> <span data-ttu-id="ae72f-123">Kullanan `netstandard2.x`projeler için uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="ae72f-123">It doesn't apply to projects that use `netstandard2.x`.</span></span>

<span data-ttu-id="ae72f-124">`NetStandardImplicitPackageVersion` [Metapackage](../packages.md#metapackages) sürümünden daha düşük bir çerçeve sürümü belirtmek istediğinizde özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ae72f-124">Use the `NetStandardImplicitPackageVersion` property when you want to specify a framework version that's lower than the [metapackage](../packages.md#metapackages) version.</span></span> <span data-ttu-id="ae72f-125">Aşağıdaki örnekteki proje dosyası hedefler `netstandard1.3` , ancak 1.6.0 sürümünü kullanır. `NETStandard.Library`</span><span class="sxs-lookup"><span data-stu-id="ae72f-125">The project file in the following example targets `netstandard1.3` but uses the 1.6.0 version of `NETStandard.Library`.</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netstandard1.3</TargetFramework>
  <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
</PropertyGroup>
```

## <a name="package-properties"></a><span data-ttu-id="ae72f-126">Paket özellikleri</span><span class="sxs-lookup"><span data-stu-id="ae72f-126">Package properties</span></span>

<span data-ttu-id="ae72f-127">Projenizden oluşturulan paketi betimleyen, `PackageId`, `PackageVersion`, `PackageIcon`ve `Title` `Description` gibi özellikleri belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ae72f-127">You can specify properties such as `PackageId`, `PackageVersion`, `PackageIcon`, `Title`, and `Description` to describe the package that gets created from your project.</span></span> <span data-ttu-id="ae72f-128">Bu ve diğer özellikler hakkında daha fazla bilgi için bkz. [Pack Target](/nuget/reference/msbuild-targets#pack-target).</span><span class="sxs-lookup"><span data-stu-id="ae72f-128">For information about these and other properties, see [pack target](/nuget/reference/msbuild-targets#pack-target).</span></span>

```xml
<PropertyGroup>
  ...
  <PackageId>ClassLibDotNetStandard</PackageId>
  <Version>1.0.0</Version>
  <Authors>John Doe</Authors>
  <Company>Contoso</Company>
</PropertyGroup>
```

## <a name="publish-properties"></a><span data-ttu-id="ae72f-129">Özellikleri Yayımla</span><span class="sxs-lookup"><span data-stu-id="ae72f-129">Publish properties</span></span>

- [<span data-ttu-id="ae72f-130">Runtimeıdentifier</span><span class="sxs-lookup"><span data-stu-id="ae72f-130">RuntimeIdentifier</span></span>](#runtimeidentifier)
- [<span data-ttu-id="ae72f-131">Runtimetanımlayıcıtanımlayıcıları</span><span class="sxs-lookup"><span data-stu-id="ae72f-131">RuntimeIdentifiers</span></span>](#runtimeidentifiers)
- [<span data-ttu-id="ae72f-132">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="ae72f-132">TrimmerRootAssembly</span></span>](#trimmerrootassembly)
- [<span data-ttu-id="ae72f-133">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="ae72f-133">UseAppHost</span></span>](#useapphost)

### <a name="runtimeidentifier"></a><span data-ttu-id="ae72f-134">Runtimeıdentifier</span><span class="sxs-lookup"><span data-stu-id="ae72f-134">RuntimeIdentifier</span></span>

<span data-ttu-id="ae72f-135">`RuntimeIdentifier` Özelliği, proje için tek bir [çalışma zamanı tanımlayıcısı (RID)](../rid-catalog.md) belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="ae72f-135">The `RuntimeIdentifier` property lets you specify a single [runtime identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="ae72f-136">RID, kendi kendine içerilen bir dağıtımı yayımlamayı mümkün.</span><span class="sxs-lookup"><span data-stu-id="ae72f-136">The RID enables publishing a self-contained deployment.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
</PropertyGroup>
```

### <a name="runtimeidentifiers"></a><span data-ttu-id="ae72f-137">Runtimetanımlayıcıtanımlayıcıları</span><span class="sxs-lookup"><span data-stu-id="ae72f-137">RuntimeIdentifiers</span></span>

<span data-ttu-id="ae72f-138">`RuntimeIdentifiers` Özelliği, proje için bir [çalışma zamanı tanımlayıcıları (RID 'ler)](../rid-catalog.md) için noktalı virgülle ayrılmış bir liste belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="ae72f-138">The `RuntimeIdentifiers` property lets you specify a semicolon-delimited list of [runtime identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="ae72f-139">Birden çok çalışma zamanı için yayımlamanız gerekiyorsa bu özelliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="ae72f-139">Use this property if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="ae72f-140">`RuntimeIdentifiers`, doğru varlıkların grafikte olduğundan emin olmak için geri yükleme zamanında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ae72f-140">`RuntimeIdentifiers` is used at restore time to ensure the right assets are in the graph.</span></span>

> [!TIP]
> <span data-ttu-id="ae72f-141">`RuntimeIdentifier`(tekil) yalnızca tek bir çalışma zamanı gerektiğinde daha hızlı derlemeler sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="ae72f-141">`RuntimeIdentifier` (singular) can provide faster builds when only a single runtime is required.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
</PropertyGroup>
```

### <a name="trimmerrootassembly"></a><span data-ttu-id="ae72f-142">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="ae72f-142">TrimmerRootAssembly</span></span>

<span data-ttu-id="ae72f-143">Öğe `TrimmerRootAssembly` , bir derlemeyi [*kırpmanıza*](../deploying/trim-self-contained.md)dışlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="ae72f-143">The `TrimmerRootAssembly` item lets you exclude an assembly from [*trimming*](../deploying/trim-self-contained.md).</span></span> <span data-ttu-id="ae72f-144">Kırpma, çalışma zamanının kullanılmayan parçalarını paketlenmiş bir uygulamadan kaldırma işlemidir.</span><span class="sxs-lookup"><span data-stu-id="ae72f-144">Trimming is the process of removing unused parts of the runtime from a packaged application.</span></span> <span data-ttu-id="ae72f-145">Bazı durumlarda, kırpma gerekli başvuruları yanlış kaldırabilir.</span><span class="sxs-lookup"><span data-stu-id="ae72f-145">In some cases, trimming might incorrectly remove required references.</span></span>

<span data-ttu-id="ae72f-146">Aşağıdaki XML, `System.Security` derlemeyi kırpmaya dışlar.</span><span class="sxs-lookup"><span data-stu-id="ae72f-146">The following XML excludes the `System.Security` assembly from trimming.</span></span>

```xml
<ItemGroup>
  <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

### <a name="useapphost"></a><span data-ttu-id="ae72f-147">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="ae72f-147">UseAppHost</span></span>

<span data-ttu-id="ae72f-148">`UseAppHost` Özelliği, .NET Core SDK 2.1.400 sürümünde tanıtılmıştı.</span><span class="sxs-lookup"><span data-stu-id="ae72f-148">The `UseAppHost` property was introduced in the 2.1.400 version of the .NET Core SDK.</span></span> <span data-ttu-id="ae72f-149">Dağıtım için yerel bir yürütülebilir dosyanın oluşturulup oluşturulmayacağını denetler.</span><span class="sxs-lookup"><span data-stu-id="ae72f-149">It controls whether or not a native executable is created for a deployment.</span></span> <span data-ttu-id="ae72f-150">Kendi kendine kapsanan dağıtımlar için yerel bir yürütülebilir dosya gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ae72f-150">A native executable is required for self-contained deployments.</span></span>

<span data-ttu-id="ae72f-151">.NET Core 3,0 ve sonraki sürümlerinde, çerçeveye bağlı bir yürütülebilir dosya varsayılan olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ae72f-151">In .NET Core 3.0 and later versions, a framework-dependent executable is created by default.</span></span> <span data-ttu-id="ae72f-152">Yürütülebilir dosyanın `UseAppHost` üretilmesini devre `false` dışı bırakmak için özelliğini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ae72f-152">Set the `UseAppHost` property to `false` to disable generation of the executable.</span></span>

```xml
<PropertyGroup>
  <UseAppHost>false</UseAppHost>
</PropertyGroup>
```

<span data-ttu-id="ae72f-153">Dağıtım hakkında daha fazla bilgi için bkz. [.NET Core uygulama dağıtımı](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="ae72f-153">For more information about deployment, see [.NET Core application deployment](../deploying/index.md).</span></span>

## <a name="compile-properties"></a><span data-ttu-id="ae72f-154">Derleme özellikleri</span><span class="sxs-lookup"><span data-stu-id="ae72f-154">Compile properties</span></span>

- [<span data-ttu-id="ae72f-155">LangVersion</span><span class="sxs-lookup"><span data-stu-id="ae72f-155">LangVersion</span></span>](#langversion)

### <a name="langversion"></a><span data-ttu-id="ae72f-156">LangVersion</span><span class="sxs-lookup"><span data-stu-id="ae72f-156">LangVersion</span></span>

<span data-ttu-id="ae72f-157">Özelliği `LangVersion` , belirli bir programlama dili sürümü belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="ae72f-157">The `LangVersion` property lets you specify a specific programming language version.</span></span> <span data-ttu-id="ae72f-158">Örneğin, C# önizleme özelliklerine erişmek istiyorsanız, olarak `LangVersion` `preview`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ae72f-158">For example, if you want access to C# preview features, set `LangVersion` to `preview`.</span></span>

```xml
<PropertyGroup>
  <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="ae72f-159">Daha fazla bilgi için bkz. [C# dil sürümü oluşturma](../../csharp/language-reference/configure-language-version.md#override-a-default).</span><span class="sxs-lookup"><span data-stu-id="ae72f-159">For more information, see [C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).</span></span>

## <a name="run-time-configuration-properties"></a><span data-ttu-id="ae72f-160">Çalışma zamanı yapılandırma özellikleri</span><span class="sxs-lookup"><span data-stu-id="ae72f-160">Run-time configuration properties</span></span>

<span data-ttu-id="ae72f-161">Uygulamanın proje dosyasında MSBuild özelliklerini belirterek bazı çalışma zamanı davranışları yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ae72f-161">You can configure some run-time behaviors by specifying MSBuild properties in the project file of the app.</span></span> <span data-ttu-id="ae72f-162">Çalışma zamanı davranışını yapılandırmanın diğer yolları hakkında daha fazla bilgi için bkz. [.NET Core çalışma zamanı yapılandırma ayarları](../run-time-config/index.md).</span><span class="sxs-lookup"><span data-stu-id="ae72f-162">For information about other ways of configuring run-time behavior, see [.NET Core run-time configuration settings](../run-time-config/index.md).</span></span>

- [<span data-ttu-id="ae72f-163">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="ae72f-163">ConcurrentGarbageCollection</span></span>](#concurrentgarbagecollection)
- [<span data-ttu-id="ae72f-164">Invariantgenelleştirme</span><span class="sxs-lookup"><span data-stu-id="ae72f-164">InvariantGlobalization</span></span>](#invariantglobalization)
- [<span data-ttu-id="ae72f-165">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="ae72f-165">RetainVMGarbageCollection</span></span>](#retainvmgarbagecollection)
- [<span data-ttu-id="ae72f-166">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="ae72f-166">ServerGarbageCollection</span></span>](#servergarbagecollection)
- [<span data-ttu-id="ae72f-167">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="ae72f-167">ThreadPoolMaxThreads</span></span>](#threadpoolmaxthreads)
- [<span data-ttu-id="ae72f-168">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="ae72f-168">ThreadPoolMinThreads</span></span>](#threadpoolminthreads)
- [<span data-ttu-id="ae72f-169">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="ae72f-169">TieredCompilation</span></span>](#tieredcompilation)
- [<span data-ttu-id="ae72f-170">Tieredcompilationquickjıt</span><span class="sxs-lookup"><span data-stu-id="ae72f-170">TieredCompilationQuickJit</span></span>](#tieredcompilationquickjit)
- [<span data-ttu-id="ae72f-171">Tieredcompilationquickjıtfordöngüleri</span><span class="sxs-lookup"><span data-stu-id="ae72f-171">TieredCompilationQuickJitForLoops</span></span>](#tieredcompilationquickjitforloops)

### <a name="concurrentgarbagecollection"></a><span data-ttu-id="ae72f-172">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="ae72f-172">ConcurrentGarbageCollection</span></span>

<span data-ttu-id="ae72f-173">`ConcurrentGarbageCollection` Özelliği [Background (eşzamanlı) Çöp toplamanın](../../standard/garbage-collection/background-gc.md) etkinleştirilip etkinleştirilmeyeceğini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="ae72f-173">The `ConcurrentGarbageCollection` property configures whether [background (concurrent) garbage collection](../../standard/garbage-collection/background-gc.md) is enabled.</span></span> <span data-ttu-id="ae72f-174">Arka plan atık toplamayı `false` devre dışı bırakmak için değerini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ae72f-174">Set the value to `false` to disable background garbage collection.</span></span> <span data-ttu-id="ae72f-175">Daha fazla bilgi için bkz. [System. GC. eşzamanlı/COMPlus_gcConcurrent](../run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent).</span><span class="sxs-lookup"><span data-stu-id="ae72f-175">For more information, see [System.GC.Concurrent/COMPlus_gcConcurrent](../run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent).</span></span>

```xml
<PropertyGroup>
  <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
</PropertyGroup>
```

### <a name="invariantglobalization"></a><span data-ttu-id="ae72f-176">Invariantgenelleştirme</span><span class="sxs-lookup"><span data-stu-id="ae72f-176">InvariantGlobalization</span></span>

<span data-ttu-id="ae72f-177">`InvariantGlobalization` Özelliği, uygulamanın *Genelleştirme sabit* modunda çalışıp çalışmadığını yapılandırır, bu, kültüre özgü verilere erişimi olmayan anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="ae72f-177">The `InvariantGlobalization` property configures whether the app runs in *globalization-invariant* mode, which means it doesn't have access to culture-specific data.</span></span> <span data-ttu-id="ae72f-178">Değeri `true` Genelleştirme sabit modunda çalışacak şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ae72f-178">Set the value to `true` to run in globalization-invariant mode.</span></span> <span data-ttu-id="ae72f-179">Daha fazla bilgi için bkz. [sabit mod](../run-time-config/globalization.md#invariant-mode).</span><span class="sxs-lookup"><span data-stu-id="ae72f-179">For more information, see [Invariant mode](../run-time-config/globalization.md#invariant-mode).</span></span>

```xml
<PropertyGroup>
  <InvariantGlobalization>true</InvariantGlobalization>
</PropertyGroup>
```

### <a name="retainvmgarbagecollection"></a><span data-ttu-id="ae72f-180">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="ae72f-180">RetainVMGarbageCollection</span></span>

<span data-ttu-id="ae72f-181">`RetainVMGarbageCollection` Özelliği, çöp toplayıcıyı, daha sonra kullanılmak üzere veya serbest bırakmak için silinen bellek segmentlerini bir bekleme listesine koymak üzere yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="ae72f-181">The `RetainVMGarbageCollection` property configures the garbage collector to put deleted memory segments on a standby list for future use or release them.</span></span> <span data-ttu-id="ae72f-182">Değeri, çöp toplayıcıya kesimleri bir bekleme listesine koymasını `true` söyler.</span><span class="sxs-lookup"><span data-stu-id="ae72f-182">Setting the value to `true` tells the garbage collector to put the segments on a standby list.</span></span> <span data-ttu-id="ae72f-183">Daha fazla bilgi için bkz. [System. GC. RetainVM/COMPlus_GCRetainVM](../run-time-config/garbage-collector.md#systemgcretainvmcomplus_gcretainvm).</span><span class="sxs-lookup"><span data-stu-id="ae72f-183">For more information, see [System.GC.RetainVM/COMPlus_GCRetainVM](../run-time-config/garbage-collector.md#systemgcretainvmcomplus_gcretainvm).</span></span>

```xml
<PropertyGroup>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
</PropertyGroup>
```

### <a name="servergarbagecollection"></a><span data-ttu-id="ae72f-184">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="ae72f-184">ServerGarbageCollection</span></span>

<span data-ttu-id="ae72f-185">`ServerGarbageCollection` Özelliği, uygulamanın [iş istasyonu çöp toplamayı veya sunucu çöp toplamayı](../../standard/garbage-collection/workstation-server-gc.md)kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="ae72f-185">The `ServerGarbageCollection` property configures whether the application uses [workstation garbage collection or server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span> <span data-ttu-id="ae72f-186">Değerini `true` sunucu çöp toplamayı kullanacak şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ae72f-186">Set the value to `true` to use server garbage collection.</span></span> <span data-ttu-id="ae72f-187">Daha fazla bilgi için bkz. [System. GC. Server/COMPlus_gcServer](../run-time-config/garbage-collector.md#systemgcservercomplus_gcserver).</span><span class="sxs-lookup"><span data-stu-id="ae72f-187">For more information, see [System.GC.Server/COMPlus_gcServer](../run-time-config/garbage-collector.md#systemgcservercomplus_gcserver).</span></span>

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

### <a name="threadpoolmaxthreads"></a><span data-ttu-id="ae72f-188">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="ae72f-188">ThreadPoolMaxThreads</span></span>

<span data-ttu-id="ae72f-189">`ThreadPoolMaxThreads` Özelliği, çalışan iş parçacığı havuzu için en fazla iş parçacığı sayısını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="ae72f-189">The `ThreadPoolMaxThreads` property configures the maximum number of threads for the worker thread pool.</span></span> <span data-ttu-id="ae72f-190">Daha fazla bilgi için bkz. [en fazla iş parçacığı](../run-time-config/threading.md#maximum-threads).</span><span class="sxs-lookup"><span data-stu-id="ae72f-190">For more information, see [Maximum threads](../run-time-config/threading.md#maximum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
</PropertyGroup>
```

### <a name="threadpoolminthreads"></a><span data-ttu-id="ae72f-191">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="ae72f-191">ThreadPoolMinThreads</span></span>

<span data-ttu-id="ae72f-192">`ThreadPoolMinThreads` Özelliği, çalışan iş parçacığı havuzu için en az iş parçacığı sayısını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="ae72f-192">The `ThreadPoolMinThreads` property configures the minimum number of threads for the worker thread pool.</span></span> <span data-ttu-id="ae72f-193">Daha fazla bilgi için bkz. [En düşük iş parçacıkları](../run-time-config/threading.md#minimum-threads).</span><span class="sxs-lookup"><span data-stu-id="ae72f-193">For more information, see [Minimum threads](../run-time-config/threading.md#minimum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
</PropertyGroup>
```

### <a name="tieredcompilation"></a><span data-ttu-id="ae72f-194">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="ae72f-194">TieredCompilation</span></span>

<span data-ttu-id="ae72f-195">Özelliği `TieredCompilation` , Just-ın-TIME (JIT) derleyicisinin [katmanlı derlemeyi](../whats-new/dotnet-core-3-0.md#tiered-compilation)kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="ae72f-195">The `TieredCompilation` property configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="ae72f-196">Katmanlı derlemeyi devre dışı `false` bırakmak için değerini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ae72f-196">Set the value to `false` to disable tiered compilation.</span></span> <span data-ttu-id="ae72f-197">Daha fazla bilgi için bkz. [katmanlı derleme](../run-time-config/compilation.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="ae72f-197">For more information, see [Tiered compilation](../run-time-config/compilation.md#tiered-compilation).</span></span>

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

### <a name="tieredcompilationquickjit"></a><span data-ttu-id="ae72f-198">Tieredcompilationquickjıt</span><span class="sxs-lookup"><span data-stu-id="ae72f-198">TieredCompilationQuickJit</span></span>

<span data-ttu-id="ae72f-199">`TieredCompilationQuickJit` ÖZELLIĞI, JIT derleyicisinin hızlı JIT kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="ae72f-199">The `TieredCompilationQuickJit` property configures whether the JIT compiler uses quick JIT.</span></span> <span data-ttu-id="ae72f-200">Hızlı JıT 'i devre `false` dışı bırakmak için değerini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ae72f-200">Set the value to `false` to disable quick JIT.</span></span> <span data-ttu-id="ae72f-201">Daha fazla bilgi için bkz. [hızlı JIT](../run-time-config/compilation.md#quick-jit).</span><span class="sxs-lookup"><span data-stu-id="ae72f-201">For more information, see [Quick JIT](../run-time-config/compilation.md#quick-jit).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

### <a name="tieredcompilationquickjitforloops"></a><span data-ttu-id="ae72f-202">Tieredcompilationquickjıtfordöngüleri</span><span class="sxs-lookup"><span data-stu-id="ae72f-202">TieredCompilationQuickJitForLoops</span></span>

<span data-ttu-id="ae72f-203">`TieredCompilationQuickJitForLoops` ÖZELLIĞI, JIT derleyicisinin döngüleri içeren YÖNTEMLERDE hızlı JIT kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="ae72f-203">The `TieredCompilationQuickJitForLoops` property configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span> <span data-ttu-id="ae72f-204">Döngüleri içeren yöntemlerde hızlı `true` JIT 'i etkinleştirmek için değerini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ae72f-204">Set the value to `true` to enable quick JIT on methods that contain loops.</span></span> <span data-ttu-id="ae72f-205">Daha fazla bilgi için bkz. [döngüler Için hızlı JIT](../run-time-config/compilation.md#quick-jit-for-loops).</span><span class="sxs-lookup"><span data-stu-id="ae72f-205">For more information, see [Quick JIT for loops](../run-time-config/compilation.md#quick-jit-for-loops).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
</PropertyGroup>
```

## <a name="reference-properties"></a><span data-ttu-id="ae72f-206">Başvuru özellikleri</span><span class="sxs-lookup"><span data-stu-id="ae72f-206">Reference properties</span></span>

- [<span data-ttu-id="ae72f-207">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="ae72f-207">AssetTargetFallback</span></span>](#assettargetfallback)
- [<span data-ttu-id="ae72f-208">PackageReference</span><span class="sxs-lookup"><span data-stu-id="ae72f-208">PackageReference</span></span>](#packagereference)
- [<span data-ttu-id="ae72f-209">ProjectReference</span><span class="sxs-lookup"><span data-stu-id="ae72f-209">ProjectReference</span></span>](#projectreference)
- [<span data-ttu-id="ae72f-210">Başvuru</span><span class="sxs-lookup"><span data-stu-id="ae72f-210">Reference</span></span>](#reference)
- [<span data-ttu-id="ae72f-211">Özellikleri geri yükle</span><span class="sxs-lookup"><span data-stu-id="ae72f-211">Restore properties</span></span>](#restore-properties)

### <a name="assettargetfallback"></a><span data-ttu-id="ae72f-212">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="ae72f-212">AssetTargetFallback</span></span>

<span data-ttu-id="ae72f-213">Özelliği `AssetTargetFallback` , proje başvuruları ve NuGet paketleri için ek uyumlu çerçeve sürümlerini belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="ae72f-213">The `AssetTargetFallback` property lets you specify additional compatible framework versions for project references and NuGet packages.</span></span> <span data-ttu-id="ae72f-214">Örneğin, kullanarak `PackageReference` bir paket bağımlılığı belirtirseniz ancak bu paket `TargetFramework`, projelerinizle uyumlu olan varlıkları içermiyorsa, `AssetTargetFallback` özelliği yürütmeye gelir.</span><span class="sxs-lookup"><span data-stu-id="ae72f-214">For example, if you specify a package dependency using `PackageReference` but that package doesn't contain assets that are compatible with your projects's `TargetFramework`, the `AssetTargetFallback` property comes into play.</span></span> <span data-ttu-id="ae72f-215">Başvurulan paketin uyumluluğu, içinde `AssetTargetFallback`belirtilen her bir hedef çerçeve kullanılarak yeniden denetlenir.</span><span class="sxs-lookup"><span data-stu-id="ae72f-215">The compatibility of the referenced package is rechecked using each target framework that's specified in `AssetTargetFallback`.</span></span>

<span data-ttu-id="ae72f-216">`AssetTargetFallback` Özelliğini bir veya daha fazla [hedef çerçeve sürümüne](../../standard/frameworks.md#supported-target-framework-versions)ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ae72f-216">You can set the `AssetTargetFallback` property to one or more [target framework versions](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<PropertyGroup>
  <AssetTargetFallback>net461</AssetTargetFallback>
</PropertyGroup>
```

### <a name="packagereference"></a><span data-ttu-id="ae72f-217">PackageReference</span><span class="sxs-lookup"><span data-stu-id="ae72f-217">PackageReference</span></span>

<span data-ttu-id="ae72f-218">, `PackageReference` Bir NuGet paketine bir başvuruyu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ae72f-218">The `PackageReference` defines a reference to a NuGet package.</span></span> <span data-ttu-id="ae72f-219">Örneğin, [metapackage](../packages.md#metapackages)yerine tek bir pakete başvurmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ae72f-219">For example, you may want to reference a single package instead of a [metapackage](../packages.md#metapackages).</span></span>

<span data-ttu-id="ae72f-220">`Include` Öznitelik, paket kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ae72f-220">The `Include` attribute specifies the package ID.</span></span> <span data-ttu-id="ae72f-221">`Version` Öznitelik, sürümü veya sürüm aralığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ae72f-221">The `Version` attribute specifies the version or version range.</span></span> <span data-ttu-id="ae72f-222">En düşük sürüm, en yüksek sürüm, Aralık veya tam eşleşme belirtme hakkında bilgi için bkz. [Sürüm aralıkları](/nuget/concepts/package-versioning#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="ae72f-222">For information about how to specify a minimum version, maximum version, range, or exact match, see [Version ranges](/nuget/concepts/package-versioning#version-ranges).</span></span> <span data-ttu-id="ae72f-223">Aşağıdaki meta verileri bir proje başvurusuna de ekleyebilirsiniz: `IncludeAssets`, `ExcludeAssets`, ve. `PrivateAssets`</span><span class="sxs-lookup"><span data-stu-id="ae72f-223">You can also add the following metadata to a project reference: `IncludeAssets`, `ExcludeAssets`, and `PrivateAssets`.</span></span>

<span data-ttu-id="ae72f-224">Aşağıdaki örnekteki proje dosyası kod parçacığı [System. Runtime](https://www.nuget.org/packages/System.Runtime/) paketine başvurur.</span><span class="sxs-lookup"><span data-stu-id="ae72f-224">The project file snippet in the following example references the [System.Runtime](https://www.nuget.org/packages/System.Runtime/) package.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="System.Runtime" Version="4.3.0" />
</ItemGroup>
```

<span data-ttu-id="ae72f-225">Daha fazla bilgi için bkz. [Proje dosyalarındaki paket başvuruları](/nuget/consume-packages/package-references-in-project-files).</span><span class="sxs-lookup"><span data-stu-id="ae72f-225">For more information, see [Package references in project files](/nuget/consume-packages/package-references-in-project-files).</span></span>

### <a name="projectreference"></a><span data-ttu-id="ae72f-226">ProjectReference</span><span class="sxs-lookup"><span data-stu-id="ae72f-226">ProjectReference</span></span>

<span data-ttu-id="ae72f-227">Öğe `ProjectReference` , başka bir projeye yönelik bir başvuru tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ae72f-227">The `ProjectReference` item defines a reference to another project.</span></span> <span data-ttu-id="ae72f-228">Başvurulan proje bir NuGet paket bağımlılığı olarak eklenir, diğer bir `PackageReference`deyişle, ile aynı şekilde işlenir.</span><span class="sxs-lookup"><span data-stu-id="ae72f-228">The referenced project is added as a NuGet package dependency, that is, it's treated the same as a `PackageReference`.</span></span>

<span data-ttu-id="ae72f-229">`Include` Öznitelik, projenin yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="ae72f-229">The `Include` attribute specifies the path to the project.</span></span> <span data-ttu-id="ae72f-230">Aşağıdaki meta verileri bir proje başvurusuna de ekleyebilirsiniz: `IncludeAssets`, `ExcludeAssets`, ve. `PrivateAssets`</span><span class="sxs-lookup"><span data-stu-id="ae72f-230">You can also add the following metadata to a project reference: `IncludeAssets`, `ExcludeAssets`, and `PrivateAssets`.</span></span>

<span data-ttu-id="ae72f-231">Aşağıdaki örnekteki proje dosyası kod parçacığı adlı `Project2`bir projeye başvurur.</span><span class="sxs-lookup"><span data-stu-id="ae72f-231">The project file snippet in the following example references a project named `Project2`.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\Project2.csproj" />
</ItemGroup>
```

### <a name="reference"></a><span data-ttu-id="ae72f-232">Başvuru</span><span class="sxs-lookup"><span data-stu-id="ae72f-232">Reference</span></span>

<span data-ttu-id="ae72f-233">Öğe `Reference` , derleme dosyasına bir başvuru tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ae72f-233">The `Reference` item defines a reference to an assembly file.</span></span>

<span data-ttu-id="ae72f-234">`Include` Öznitelik, dosyanın adını belirtir ve `HintPath` alt öğe derleme yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="ae72f-234">The `Include` attribute specifies the name of the file, and the `HintPath` child element specifies the path to the assembly.</span></span>

```xml
<ItemGroup>
  <Reference Include="MyAssembly">
    <HintPath>..\..\Assemblies\MyAssembly.dll</HintPath>
  </Reference>
</ItemGroup>
```

### <a name="restore-properties"></a><span data-ttu-id="ae72f-235">Özellikleri geri yükle</span><span class="sxs-lookup"><span data-stu-id="ae72f-235">Restore properties</span></span>

<span data-ttu-id="ae72f-236">Başvurulan bir paketin geri yüklenmesi, tüm doğrudan bağımlılıklarını ve bu bağımlılıkların tüm bağımlılıklarını yükler.</span><span class="sxs-lookup"><span data-stu-id="ae72f-236">Restoring a referenced package installs all of its direct dependencies and all the dependencies of those dependencies.</span></span> <span data-ttu-id="ae72f-237">`RestorePackagesPath` Ve `RestoreIgnoreFailedSources`gibi özellikler belirterek paket geri yüklemesini özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ae72f-237">You can customize package restoration by specifying properties such as `RestorePackagesPath` and `RestoreIgnoreFailedSources`.</span></span> <span data-ttu-id="ae72f-238">Bu ve diğer özellikler hakkında daha fazla bilgi için bkz. [hedefi geri yükleme](/nuget/reference/msbuild-targets#restore-target).</span><span class="sxs-lookup"><span data-stu-id="ae72f-238">For more information about these and other properties, see [restore target](/nuget/reference/msbuild-targets#restore-target).</span></span>

```xml
<PropertyGroup>
  <RestoreIgnoreFailedSource>true</RestoreIgnoreFailedSource>
</PropertyGroup>
```

## <a name="see-also"></a><span data-ttu-id="ae72f-239">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae72f-239">See also</span></span>

- [<span data-ttu-id="ae72f-240">MSBuild şema başvurusu</span><span class="sxs-lookup"><span data-stu-id="ae72f-240">MSBuild schema reference</span></span>](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [<span data-ttu-id="ae72f-241">Ortak MSBuild özellikleri</span><span class="sxs-lookup"><span data-stu-id="ae72f-241">Common MSBuild properties</span></span>](/visualstudio/msbuild/common-msbuild-project-properties)
- [<span data-ttu-id="ae72f-242">NuGet paketi için MSBuild özellikleri</span><span class="sxs-lookup"><span data-stu-id="ae72f-242">MSBuild properties for NuGet pack</span></span>](/nuget/reference/msbuild-targets#pack-target)
- [<span data-ttu-id="ae72f-243">NuGet geri yükleme için MSBuild özellikleri</span><span class="sxs-lookup"><span data-stu-id="ae72f-243">MSBuild properties for NuGet restore</span></span>](/nuget/reference/msbuild-targets#restore-properties)
- [<span data-ttu-id="ae72f-244">Bir derlemeyi özelleştirme</span><span class="sxs-lookup"><span data-stu-id="ae72f-244">Customize a build</span></span>](/visualstudio/msbuild/customize-your-build)
