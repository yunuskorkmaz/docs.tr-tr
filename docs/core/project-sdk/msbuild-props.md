---
title: Microsoft. NET. SDK için MSBuild özellikleri
description: .NET Core SDK anlayan MSBuild özelliklerine yönelik başvuru.
ms.date: 02/14/2020
ms.topic: reference
ms.openlocfilehash: 105b7d67ea24515ea88481cb4a4fe42d2a03cfd0
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82506798"
---
# <a name="msbuild-properties-for-net-core-sdk-projects"></a><span data-ttu-id="b40ac-103">.NET Core SDK projeleri için MSBuild özellikleri</span><span class="sxs-lookup"><span data-stu-id="b40ac-103">MSBuild properties for .NET Core SDK projects</span></span>

<span data-ttu-id="b40ac-104">Bu sayfa, .NET Core projelerini yapılandırmaya yönelik MSBuild özelliklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="b40ac-104">This page describes MSBuild properties for configuring .NET Core projects.</span></span>

> [!NOTE]
> <span data-ttu-id="b40ac-105">Bu sayfa devam eden bir çalışmadır ve .NET Core SDK için tüm yararlı MSBuild özelliklerini listelemez.</span><span class="sxs-lookup"><span data-stu-id="b40ac-105">This page is a work in progress and does not list all of the useful MSBuild properties for the .NET Core SDK.</span></span> <span data-ttu-id="b40ac-106">Ortak MSBuild özelliklerinin bir listesi için bkz. [Ortak MSBuild özellikleri](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="b40ac-106">For a list of common MSBuild properties, see [Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="framework-properties"></a><span data-ttu-id="b40ac-107">Çerçeve özellikleri</span><span class="sxs-lookup"><span data-stu-id="b40ac-107">Framework properties</span></span>

- [<span data-ttu-id="b40ac-108">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="b40ac-108">TargetFramework</span></span>](#targetframework)
- [<span data-ttu-id="b40ac-109">Targetçerçeveler</span><span class="sxs-lookup"><span data-stu-id="b40ac-109">TargetFrameworks</span></span>](#targetframeworks)
- [<span data-ttu-id="b40ac-110">Netstandardımplicitpackageversion</span><span class="sxs-lookup"><span data-stu-id="b40ac-110">NetStandardImplicitPackageVersion</span></span>](#netstandardimplicitpackageversion)

### <a name="targetframework"></a><span data-ttu-id="b40ac-111">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="b40ac-111">TargetFramework</span></span>

<span data-ttu-id="b40ac-112">`TargetFramework` Özelliği, bir [metapackage](../packages.md#metapackages)örtük olarak başvurduğu uygulamanın hedef Framework sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="b40ac-112">The `TargetFramework` property specifies the target framework version for the app, which implicitly references a [metapackage](../packages.md#metapackages).</span></span> <span data-ttu-id="b40ac-113">Geçerli hedef çerçeve takma adların listesi için bkz. [SDK stili projelerde hedef çerçeveler](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="b40ac-113">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="b40ac-114">Daha fazla bilgi için bkz. [SDK stili projelerde hedef çerçeveler](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="b40ac-114">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="targetframeworks"></a><span data-ttu-id="b40ac-115">Targetçerçeveler</span><span class="sxs-lookup"><span data-stu-id="b40ac-115">TargetFrameworks</span></span>

<span data-ttu-id="b40ac-116">Uygulamanızın birden `TargetFrameworks` çok platformu hedeflemesini istediğinizde özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="b40ac-116">Use the `TargetFrameworks` property when you want your app to target multiple platforms.</span></span> <span data-ttu-id="b40ac-117">Geçerli hedef çerçeve takma adların listesi için bkz. [SDK stili projelerde hedef çerçeveler](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="b40ac-117">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

> [!NOTE]
> <span data-ttu-id="b40ac-118">`TargetFramework` (Tekil) belirtilmişse bu özellik yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="b40ac-118">This property is ignored if `TargetFramework` (singular) is specified.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="b40ac-119">Daha fazla bilgi için bkz. [SDK stili projelerde hedef çerçeveler](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="b40ac-119">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="netstandardimplicitpackageversion"></a><span data-ttu-id="b40ac-120">Netstandardımplicitpackageversion</span><span class="sxs-lookup"><span data-stu-id="b40ac-120">NetStandardImplicitPackageVersion</span></span>

> [!NOTE]
> <span data-ttu-id="b40ac-121">Bu özellik yalnızca kullanan `netstandard1.x`projeler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b40ac-121">This property only applies to projects using `netstandard1.x`.</span></span> <span data-ttu-id="b40ac-122">Kullanan `netstandard2.x`projeler için uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="b40ac-122">It doesn't apply to projects that use `netstandard2.x`.</span></span>

<span data-ttu-id="b40ac-123">`NetStandardImplicitPackageVersion` [Metapackage](../packages.md#metapackages) sürümünden daha düşük bir çerçeve sürümü belirtmek istediğinizde özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="b40ac-123">Use the `NetStandardImplicitPackageVersion` property when you want to specify a framework version that's lower than the [metapackage](../packages.md#metapackages) version.</span></span> <span data-ttu-id="b40ac-124">Aşağıdaki örnekteki proje dosyası hedefler `netstandard1.3` , ancak 1.6.0 sürümünü kullanır. `NETStandard.Library`</span><span class="sxs-lookup"><span data-stu-id="b40ac-124">The project file in the following example targets `netstandard1.3` but uses the 1.6.0 version of `NETStandard.Library`.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.3</TargetFramework>
    <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
  </PropertyGroup>
</Project>
```

## <a name="publish-properties"></a><span data-ttu-id="b40ac-125">Özellikleri Yayımla</span><span class="sxs-lookup"><span data-stu-id="b40ac-125">Publish properties</span></span>

- [<span data-ttu-id="b40ac-126">Runtimeıdentifier</span><span class="sxs-lookup"><span data-stu-id="b40ac-126">RuntimeIdentifier</span></span>](#runtimeidentifier)
- [<span data-ttu-id="b40ac-127">Runtimetanımlayıcıtanımlayıcıları</span><span class="sxs-lookup"><span data-stu-id="b40ac-127">RuntimeIdentifiers</span></span>](#runtimeidentifiers)
- [<span data-ttu-id="b40ac-128">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="b40ac-128">TrimmerRootAssembly</span></span>](#trimmerrootassembly)
- [<span data-ttu-id="b40ac-129">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="b40ac-129">UseAppHost</span></span>](#useapphost)

### <a name="runtimeidentifier"></a><span data-ttu-id="b40ac-130">Runtimeıdentifier</span><span class="sxs-lookup"><span data-stu-id="b40ac-130">RuntimeIdentifier</span></span>

<span data-ttu-id="b40ac-131">`RuntimeIdentifier` Özelliği, proje için tek bir [çalışma zamanı tanımlayıcısı (RID)](../rid-catalog.md) belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="b40ac-131">The `RuntimeIdentifier` property lets you specify a single [runtime identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="b40ac-132">RID, kendi kendine içerilen bir dağıtımı yayımlamayı mümkün.</span><span class="sxs-lookup"><span data-stu-id="b40ac-132">The RID enables publishing a self-contained deployment.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
  </PropertyGroup>
</Project>
```

### <a name="runtimeidentifiers"></a><span data-ttu-id="b40ac-133">Runtimetanımlayıcıtanımlayıcıları</span><span class="sxs-lookup"><span data-stu-id="b40ac-133">RuntimeIdentifiers</span></span>

<span data-ttu-id="b40ac-134">`RuntimeIdentifiers` Özelliği, proje için bir [çalışma zamanı tanımlayıcıları (RID 'ler)](../rid-catalog.md) için noktalı virgülle ayrılmış bir liste belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="b40ac-134">The `RuntimeIdentifiers` property lets you specify a semicolon-delimited list of [runtime identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="b40ac-135">Birden çok çalışma zamanı için yayımlamanız gerekiyorsa bu özelliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="b40ac-135">Use this property if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="b40ac-136">`RuntimeIdentifiers`, doğru varlıkların grafikte olduğundan emin olmak için geri yükleme zamanında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b40ac-136">`RuntimeIdentifiers` is used at restore time to ensure the right assets are in the graph.</span></span>

> [!TIP]
> <span data-ttu-id="b40ac-137">`RuntimeIdentifier`(tekil) yalnızca tek bir çalışma zamanı gerektiğinde daha hızlı derlemeler sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="b40ac-137">`RuntimeIdentifier` (singular) can provide faster builds when only a single runtime is required.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

### <a name="trimmerrootassembly"></a><span data-ttu-id="b40ac-138">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="b40ac-138">TrimmerRootAssembly</span></span>

<span data-ttu-id="b40ac-139">Öğe `TrimmerRootAssembly` , bir derlemeyi [*kırpmanıza*](../deploying/trim-self-contained.md)dışlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b40ac-139">The `TrimmerRootAssembly` item lets you exclude an assembly from [*trimming*](../deploying/trim-self-contained.md).</span></span> <span data-ttu-id="b40ac-140">Kırpma, çalışma zamanının kullanılmayan parçalarını paketlenmiş bir uygulamadan kaldırma işlemidir.</span><span class="sxs-lookup"><span data-stu-id="b40ac-140">Trimming is the process of removing unused parts of the runtime from a packaged application.</span></span> <span data-ttu-id="b40ac-141">Bazı durumlarda, kırpma gerekli başvuruları yanlış kaldırabilir.</span><span class="sxs-lookup"><span data-stu-id="b40ac-141">In some cases, trimming might incorrectly remove required references.</span></span>

<span data-ttu-id="b40ac-142">Aşağıdaki XML, `System.Security` derlemeyi kırpmaya dışlar.</span><span class="sxs-lookup"><span data-stu-id="b40ac-142">The following XML excludes the `System.Security` assembly from trimming.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <TrimmerRootAssembly Include="System.Security" />
  </ItemGroup>
</Project>
```

### <a name="useapphost"></a><span data-ttu-id="b40ac-143">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="b40ac-143">UseAppHost</span></span>

<span data-ttu-id="b40ac-144">`UseAppHost` Özelliği, .NET Core SDK 2.1.400 sürümünde tanıtılmıştı.</span><span class="sxs-lookup"><span data-stu-id="b40ac-144">The `UseAppHost` property was introduced in the 2.1.400 version of the .NET Core SDK.</span></span> <span data-ttu-id="b40ac-145">Dağıtım için yerel bir yürütülebilir dosyanın oluşturulup oluşturulmayacağını denetler.</span><span class="sxs-lookup"><span data-stu-id="b40ac-145">It controls whether or not a native executable is created for a deployment.</span></span> <span data-ttu-id="b40ac-146">Kendi kendine kapsanan dağıtımlar için yerel bir yürütülebilir dosya gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b40ac-146">A native executable is required for self-contained deployments.</span></span>

<span data-ttu-id="b40ac-147">.NET Core 3,0 ve sonraki sürümlerinde, çerçeveye bağlı bir yürütülebilir dosya varsayılan olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b40ac-147">In .NET Core 3.0 and later versions, a framework-dependent executable is created by default.</span></span> <span data-ttu-id="b40ac-148">Yürütülebilir dosyanın `UseAppHost` üretilmesini devre `false` dışı bırakmak için özelliğini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b40ac-148">Set the `UseAppHost` property to `false` to disable generation of the executable.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <UseAppHost>false</UseAppHost>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="b40ac-149">Dağıtım hakkında daha fazla bilgi için bkz. [.NET Core uygulama dağıtımı](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="b40ac-149">For more information about deployment, see [.NET Core application deployment](../deploying/index.md).</span></span>

## <a name="compile-properties"></a><span data-ttu-id="b40ac-150">Derleme özellikleri</span><span class="sxs-lookup"><span data-stu-id="b40ac-150">Compile properties</span></span>

- [<span data-ttu-id="b40ac-151">LangVersion</span><span class="sxs-lookup"><span data-stu-id="b40ac-151">LangVersion</span></span>](#langversion)

### <a name="langversion"></a><span data-ttu-id="b40ac-152">LangVersion</span><span class="sxs-lookup"><span data-stu-id="b40ac-152">LangVersion</span></span>

<span data-ttu-id="b40ac-153">Özelliği `LangVersion` , belirli bir programlama dili sürümü belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b40ac-153">The `LangVersion` property lets you specify a specific programming language version.</span></span> <span data-ttu-id="b40ac-154">Örneğin, C# önizleme özelliklerine erişmek istiyorsanız, olarak `LangVersion` `preview`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b40ac-154">For example, if you want access to C# preview features, set `LangVersion` to `preview`.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <LangVersion>preview</LangVersion>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="b40ac-155">Daha fazla bilgi için bkz. [C# dil sürümü oluşturma](../../csharp/language-reference/configure-language-version.md#override-a-default).</span><span class="sxs-lookup"><span data-stu-id="b40ac-155">For more information, see [C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).</span></span>

## <a name="run-time-configuration-properties"></a><span data-ttu-id="b40ac-156">Çalışma zamanı yapılandırma özellikleri</span><span class="sxs-lookup"><span data-stu-id="b40ac-156">Run-time configuration properties</span></span>

<span data-ttu-id="b40ac-157">Uygulamanın proje dosyasında MSBuild özelliklerini belirterek bazı çalışma zamanı davranışları yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b40ac-157">You can configure some run-time behaviors by specifying MSBuild properties in the project file of the app.</span></span> <span data-ttu-id="b40ac-158">Çalışma zamanı davranışını yapılandırmanın diğer yolları hakkında daha fazla bilgi için bkz. [.NET Core çalışma zamanı yapılandırma ayarları](../run-time-config/index.md).</span><span class="sxs-lookup"><span data-stu-id="b40ac-158">For information about other ways of configuring run-time behavior, see [.NET Core run-time configuration settings](../run-time-config/index.md).</span></span>

- [<span data-ttu-id="b40ac-159">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="b40ac-159">ConcurrentGarbageCollection</span></span>](#concurrentgarbagecollection)
- [<span data-ttu-id="b40ac-160">Invariantgenelleştirme</span><span class="sxs-lookup"><span data-stu-id="b40ac-160">InvariantGlobalization</span></span>](#invariantglobalization)
- [<span data-ttu-id="b40ac-161">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="b40ac-161">RetainVMGarbageCollection</span></span>](#retainvmgarbagecollection)
- [<span data-ttu-id="b40ac-162">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="b40ac-162">ServerGarbageCollection</span></span>](#servergarbagecollection)
- [<span data-ttu-id="b40ac-163">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="b40ac-163">ThreadPoolMaxThreads</span></span>](#threadpoolmaxthreads)
- [<span data-ttu-id="b40ac-164">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="b40ac-164">ThreadPoolMinThreads</span></span>](#threadpoolminthreads)
- [<span data-ttu-id="b40ac-165">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="b40ac-165">TieredCompilation</span></span>](#tieredcompilation)
- [<span data-ttu-id="b40ac-166">Tieredcompilationquickjıt</span><span class="sxs-lookup"><span data-stu-id="b40ac-166">TieredCompilationQuickJit</span></span>](#tieredcompilationquickjit)
- [<span data-ttu-id="b40ac-167">Tieredcompilationquickjıtfordöngüleri</span><span class="sxs-lookup"><span data-stu-id="b40ac-167">TieredCompilationQuickJitForLoops</span></span>](#tieredcompilationquickjitforloops)

### <a name="concurrentgarbagecollection"></a><span data-ttu-id="b40ac-168">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="b40ac-168">ConcurrentGarbageCollection</span></span>

<span data-ttu-id="b40ac-169">`ConcurrentGarbageCollection` Özelliği [Background (eşzamanlı) Çöp toplamanın](../../standard/garbage-collection/background-gc.md) etkinleştirilip etkinleştirilmeyeceğini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="b40ac-169">The `ConcurrentGarbageCollection` property configures whether [background (concurrent) garbage collection](../../standard/garbage-collection/background-gc.md) is enabled.</span></span> <span data-ttu-id="b40ac-170">Arka plan atık toplamayı `false` devre dışı bırakmak için değerini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b40ac-170">Set the value to `false` to disable background garbage collection.</span></span> <span data-ttu-id="b40ac-171">Daha fazla bilgi için bkz. [System. GC. eşzamanlı/COMPlus_gcConcurrent](../run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent).</span><span class="sxs-lookup"><span data-stu-id="b40ac-171">For more information, see [System.GC.Concurrent/COMPlus_gcConcurrent](../run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>
</Project>
```

### <a name="invariantglobalization"></a><span data-ttu-id="b40ac-172">Invariantgenelleştirme</span><span class="sxs-lookup"><span data-stu-id="b40ac-172">InvariantGlobalization</span></span>

<span data-ttu-id="b40ac-173">`InvariantGlobalization` Özelliği, uygulamanın *Genelleştirme sabit* modunda çalışıp çalışmadığını yapılandırır, bu, kültüre özgü verilere erişimi olmayan anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="b40ac-173">The `InvariantGlobalization` property configures whether the app runs in *globalization-invariant* mode, which means it doesn't have access to culture-specific data.</span></span> <span data-ttu-id="b40ac-174">Değeri `true` Genelleştirme sabit modunda çalışacak şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b40ac-174">Set the value to `true` to run in globalization-invariant mode.</span></span> <span data-ttu-id="b40ac-175">Daha fazla bilgi için bkz. [sabit mod](../run-time-config/globalization.md#invariant-mode).</span><span class="sxs-lookup"><span data-stu-id="b40ac-175">For more information, see [Invariant mode](../run-time-config/globalization.md#invariant-mode).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <InvariantGlobalization>true</InvariantGlobalization>
  </PropertyGroup>
</Project>
```

### <a name="retainvmgarbagecollection"></a><span data-ttu-id="b40ac-176">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="b40ac-176">RetainVMGarbageCollection</span></span>

<span data-ttu-id="b40ac-177">`RetainVMGarbageCollection` Özelliği, çöp toplayıcıyı, daha sonra kullanılmak üzere veya serbest bırakmak için silinen bellek segmentlerini bir bekleme listesine koymak üzere yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="b40ac-177">The `RetainVMGarbageCollection` property configures the garbage collector to put deleted memory segments on a standby list for future use or release them.</span></span> <span data-ttu-id="b40ac-178">Değeri, çöp toplayıcıya kesimleri bir bekleme listesine koymasını `true` söyler.</span><span class="sxs-lookup"><span data-stu-id="b40ac-178">Setting the value to `true` tells the garbage collector to put the segments on a standby list.</span></span> <span data-ttu-id="b40ac-179">Daha fazla bilgi için bkz. [System. GC. RetainVM/COMPlus_GCRetainVM](../run-time-config/garbage-collector.md#systemgcretainvmcomplus_gcretainvm).</span><span class="sxs-lookup"><span data-stu-id="b40ac-179">For more information, see [System.GC.RetainVM/COMPlus_GCRetainVM](../run-time-config/garbage-collector.md#systemgcretainvmcomplus_gcretainvm).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>
</Project>
```

### <a name="servergarbagecollection"></a><span data-ttu-id="b40ac-180">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="b40ac-180">ServerGarbageCollection</span></span>

<span data-ttu-id="b40ac-181">`ServerGarbageCollection` Özelliği, uygulamanın [iş istasyonu çöp toplamayı veya sunucu çöp toplamayı](../../standard/garbage-collection/workstation-server-gc.md)kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="b40ac-181">The `ServerGarbageCollection` property configures whether the application uses [workstation garbage collection or server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span> <span data-ttu-id="b40ac-182">Değerini `true` sunucu çöp toplamayı kullanacak şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b40ac-182">Set the value to `true` to use server garbage collection.</span></span> <span data-ttu-id="b40ac-183">Daha fazla bilgi için bkz. [System. GC. Server/COMPlus_gcServer](../run-time-config/garbage-collector.md#systemgcservercomplus_gcserver).</span><span class="sxs-lookup"><span data-stu-id="b40ac-183">For more information, see [System.GC.Server/COMPlus_gcServer](../run-time-config/garbage-collector.md#systemgcservercomplus_gcserver).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>
</Project>
```

### <a name="threadpoolmaxthreads"></a><span data-ttu-id="b40ac-184">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="b40ac-184">ThreadPoolMaxThreads</span></span>

<span data-ttu-id="b40ac-185">`ThreadPoolMaxThreads` Özelliği, çalışan iş parçacığı havuzu için en fazla iş parçacığı sayısını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="b40ac-185">The `ThreadPoolMaxThreads` property configures the maximum number of threads for the worker thread pool.</span></span> <span data-ttu-id="b40ac-186">Daha fazla bilgi için bkz. [en fazla iş parçacığı](../run-time-config/threading.md#maximum-threads).</span><span class="sxs-lookup"><span data-stu-id="b40ac-186">For more information, see [Maximum threads](../run-time-config/threading.md#maximum-threads).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
  </PropertyGroup>
</Project>
```

### <a name="threadpoolminthreads"></a><span data-ttu-id="b40ac-187">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="b40ac-187">ThreadPoolMinThreads</span></span>

<span data-ttu-id="b40ac-188">`ThreadPoolMinThreads` Özelliği, çalışan iş parçacığı havuzu için en az iş parçacığı sayısını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="b40ac-188">The `ThreadPoolMinThreads` property configures the minimum number of threads for the worker thread pool.</span></span> <span data-ttu-id="b40ac-189">Daha fazla bilgi için bkz. [En düşük iş parçacıkları](../run-time-config/threading.md#minimum-threads).</span><span class="sxs-lookup"><span data-stu-id="b40ac-189">For more information, see [Minimum threads](../run-time-config/threading.md#minimum-threads).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  </PropertyGroup>
</Project>
```

### <a name="tieredcompilation"></a><span data-ttu-id="b40ac-190">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="b40ac-190">TieredCompilation</span></span>

<span data-ttu-id="b40ac-191">Özelliği `TieredCompilation` , Just-ın-TIME (JIT) derleyicisinin [katmanlı derlemeyi](../whats-new/dotnet-core-3-0.md#tiered-compilation)kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="b40ac-191">The `TieredCompilation` property configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="b40ac-192">Katmanlı derlemeyi devre dışı `false` bırakmak için değerini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b40ac-192">Set the value to `false` to disable tiered compilation.</span></span> <span data-ttu-id="b40ac-193">Daha fazla bilgi için bkz. [katmanlı derleme](../run-time-config/compilation.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="b40ac-193">For more information, see [Tiered compilation](../run-time-config/compilation.md#tiered-compilation).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TieredCompilation>false</TieredCompilation>
  </PropertyGroup>
</Project>
```

### <a name="tieredcompilationquickjit"></a><span data-ttu-id="b40ac-194">Tieredcompilationquickjıt</span><span class="sxs-lookup"><span data-stu-id="b40ac-194">TieredCompilationQuickJit</span></span>

<span data-ttu-id="b40ac-195">`TieredCompilationQuickJit` ÖZELLIĞI, JIT derleyicisinin hızlı JIT kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="b40ac-195">The `TieredCompilationQuickJit` property configures whether the JIT compiler uses quick JIT.</span></span> <span data-ttu-id="b40ac-196">Hızlı JıT 'i devre `false` dışı bırakmak için değerini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b40ac-196">Set the value to `false` to disable quick JIT.</span></span> <span data-ttu-id="b40ac-197">Daha fazla bilgi için bkz. [hızlı JIT](../run-time-config/compilation.md#quick-jit).</span><span class="sxs-lookup"><span data-stu-id="b40ac-197">For more information, see [Quick JIT](../run-time-config/compilation.md#quick-jit).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
  </PropertyGroup>
</Project>
```

### <a name="tieredcompilationquickjitforloops"></a><span data-ttu-id="b40ac-198">Tieredcompilationquickjıtfordöngüleri</span><span class="sxs-lookup"><span data-stu-id="b40ac-198">TieredCompilationQuickJitForLoops</span></span>

<span data-ttu-id="b40ac-199">`TieredCompilationQuickJitForLoops` ÖZELLIĞI, JIT derleyicisinin döngüleri içeren YÖNTEMLERDE hızlı JIT kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="b40ac-199">The `TieredCompilationQuickJitForLoops` property configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span> <span data-ttu-id="b40ac-200">Döngüleri içeren yöntemlerde hızlı `true` JIT 'i etkinleştirmek için değerini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b40ac-200">Set the value to `true` to enable quick JIT on methods that contain loops.</span></span> <span data-ttu-id="b40ac-201">Daha fazla bilgi için bkz. [döngüler Için hızlı JIT](../run-time-config/compilation.md#quick-jit-for-loops).</span><span class="sxs-lookup"><span data-stu-id="b40ac-201">For more information, see [Quick JIT for loops](../run-time-config/compilation.md#quick-jit-for-loops).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
  </PropertyGroup>
</Project>
```

## <a name="nuget-packages"></a><span data-ttu-id="b40ac-202">NuGet paketleri</span><span class="sxs-lookup"><span data-stu-id="b40ac-202">NuGet packages</span></span>

- [<span data-ttu-id="b40ac-203">PackageReference</span><span class="sxs-lookup"><span data-stu-id="b40ac-203">PackageReference</span></span>](#packagereference)
- [<span data-ttu-id="b40ac-204">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="b40ac-204">AssetTargetFallback</span></span>](#assettargetfallback)

### <a name="packagereference"></a><span data-ttu-id="b40ac-205">PackageReference</span><span class="sxs-lookup"><span data-stu-id="b40ac-205">PackageReference</span></span>

<span data-ttu-id="b40ac-206">Öğe `PackageReference` , bir NuGet bağımlılığı belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b40ac-206">The `PackageReference` item lets you specify a NuGet dependency.</span></span> <span data-ttu-id="b40ac-207">Örneğin, [metapackage](../packages.md#metapackages)yerine tek bir pakete başvurmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b40ac-207">For example, you may want to reference a single package instead of a [metapackage](../packages.md#metapackages).</span></span> <span data-ttu-id="b40ac-208">`Include` Öznitelik, paket kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b40ac-208">The `Include` attribute specifies the package ID.</span></span> <span data-ttu-id="b40ac-209">Aşağıdaki örnekteki proje dosyası kod parçacığı [System. Runtime](https://www.nuget.org/packages/System.Runtime/) paketine başvurur.</span><span class="sxs-lookup"><span data-stu-id="b40ac-209">The project file snippet in the following example references the [System.Runtime](https://www.nuget.org/packages/System.Runtime/) package.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <ItemGroup>
    <PackageReference Include="System.Runtime" Version="4.3.0" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="b40ac-210">Daha fazla bilgi için bkz. [Proje dosyalarındaki paket başvuruları](/nuget/consume-packages/package-references-in-project-files).</span><span class="sxs-lookup"><span data-stu-id="b40ac-210">For more information, see [Package references in project files](/nuget/consume-packages/package-references-in-project-files).</span></span>

### <a name="assettargetfallback"></a><span data-ttu-id="b40ac-211">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="b40ac-211">AssetTargetFallback</span></span>

<span data-ttu-id="b40ac-212">Özelliği `AssetTargetFallback` , projenizin başvurduğu projeler için ek uyumlu çerçeve sürümlerini belirtmenizi sağlar ve projenizin kullandığı NuGet paketleri.</span><span class="sxs-lookup"><span data-stu-id="b40ac-212">The `AssetTargetFallback` property lets you specify additional compatible framework versions for projects that your project references and NuGet packages that your project consumes.</span></span> <span data-ttu-id="b40ac-213">Örneğin, kullanarak `PackageReference` bir paket bağımlılığı belirtirseniz ancak bu paket `TargetFramework`, projelerinizle uyumlu olan varlıkları içermiyorsa, `AssetTargetFallback` özelliği yürütmeye gelir.</span><span class="sxs-lookup"><span data-stu-id="b40ac-213">For example, if you specify a package dependency using `PackageReference` but that package doesn't contain assets that are compatible with your projects's `TargetFramework`, the `AssetTargetFallback` property comes into play.</span></span> <span data-ttu-id="b40ac-214">Başvurulan paketin uyumluluğu, içinde `AssetTargetFallback`belirtilen her bir hedef çerçeve kullanılarak yeniden denetlenir.</span><span class="sxs-lookup"><span data-stu-id="b40ac-214">The compatibility of the referenced package is rechecked using each target framework that's specified in `AssetTargetFallback`.</span></span>

<span data-ttu-id="b40ac-215">`AssetTargetFallback` Özelliğini bir veya daha fazla [hedef çerçeve sürümüne](../../standard/frameworks.md#supported-target-framework-versions)ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b40ac-215">You can set the `AssetTargetFallback` property to one or more [target framework versions](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <PropertyGroup>
    <AssetTargetFallback>net461</AssetTargetFallback>
  </PropertyGroup>
</Project>
```

### <a name="pack-and-restore-targets"></a><span data-ttu-id="b40ac-216">Paket ve geri yükleme hedefleri</span><span class="sxs-lookup"><span data-stu-id="b40ac-216">Pack and restore targets</span></span>

<span data-ttu-id="b40ac-217">MSBuild 15,1 tanıtılan `pack` ve `restore` derleme kapsamında NuGet paketleri oluşturmak ve geri yüklemek için hedefler.</span><span class="sxs-lookup"><span data-stu-id="b40ac-217">MSBuild 15.1 introduced `pack` and `restore` targets for creating and restoring NuGet packages as part of a build.</span></span> <span data-ttu-id="b40ac-218">Bu hedeflerin `PackageTargetFallback`MSBuild özellikleri hakkında daha fazla bilgi için, bkz. [NuGet Pack ve geri yükleme MSBuild hedefleri](/nuget/reference/msbuild-targets).</span><span class="sxs-lookup"><span data-stu-id="b40ac-218">For information about the MSBuild properties for these targets, including `PackageTargetFallback`, see [NuGet pack and restore as MSBuild targets](/nuget/reference/msbuild-targets).</span></span>

## <a name="see-also"></a><span data-ttu-id="b40ac-219">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b40ac-219">See also</span></span>

- [<span data-ttu-id="b40ac-220">MSBuild şema başvurusu</span><span class="sxs-lookup"><span data-stu-id="b40ac-220">MSBuild schema reference</span></span>](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [<span data-ttu-id="b40ac-221">Ortak MSBuild özellikleri</span><span class="sxs-lookup"><span data-stu-id="b40ac-221">Common MSBuild properties</span></span>](/visualstudio/msbuild/common-msbuild-project-properties)
- [<span data-ttu-id="b40ac-222">NuGet paketi için MSBuild özellikleri</span><span class="sxs-lookup"><span data-stu-id="b40ac-222">MSBuild properties for NuGet pack</span></span>](/nuget/reference/msbuild-targets#pack-target)
- [<span data-ttu-id="b40ac-223">NuGet geri yükleme için MSBuild özellikleri</span><span class="sxs-lookup"><span data-stu-id="b40ac-223">MSBuild properties for NuGet restore</span></span>](/nuget/reference/msbuild-targets#restore-properties)
- [<span data-ttu-id="b40ac-224">Bir derlemeyi özelleştirme</span><span class="sxs-lookup"><span data-stu-id="b40ac-224">Customize a build</span></span>](/visualstudio/msbuild/customize-your-build)
