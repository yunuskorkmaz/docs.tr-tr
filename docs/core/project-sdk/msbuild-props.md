---
title: Microsoft. NET. SDK için MSBuild özellikleri
description: MSBuild özellikleri ve .NET Core SDK anlayan öğeler için başvuru.
ms.date: 02/14/2020
ms.topic: reference
ms.openlocfilehash: cda56b3e23592a341d9fe672fc1f1530adcdab49
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83206105"
---
# <a name="msbuild-reference-for-net-core-sdk-projects"></a><span data-ttu-id="c5e7e-103">.NET Core SDK projeleri için MSBuild başvurusu</span><span class="sxs-lookup"><span data-stu-id="c5e7e-103">MSBuild reference for .NET Core SDK projects</span></span>

<span data-ttu-id="c5e7e-104">Bu sayfa, .NET Core projelerini yapılandırmak için kullanabileceğiniz MSBuild özelliklerine ve öğelerine yönelik bir başvurudur.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-104">This page is a reference for the MSBuild properties and items that you can use to configure .NET Core projects.</span></span>

> [!NOTE]
> <span data-ttu-id="c5e7e-105">Bu sayfa devam eden bir çalışmadır ve .NET Core SDK için tüm yararlı MSBuild özelliklerini listelemez.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-105">This page is a work in progress and does not list all of the useful MSBuild properties for the .NET Core SDK.</span></span> <span data-ttu-id="c5e7e-106">Ortak MSBuild özelliklerinin bir listesi için bkz. [Ortak MSBuild özellikleri](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="c5e7e-106">For a list of common MSBuild properties, see [Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="framework-properties"></a><span data-ttu-id="c5e7e-107">Çerçeve özellikleri</span><span class="sxs-lookup"><span data-stu-id="c5e7e-107">Framework properties</span></span>

- [<span data-ttu-id="c5e7e-108">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="c5e7e-108">TargetFramework</span></span>](#targetframework)
- [<span data-ttu-id="c5e7e-109">Targetçerçeveler</span><span class="sxs-lookup"><span data-stu-id="c5e7e-109">TargetFrameworks</span></span>](#targetframeworks)
- [<span data-ttu-id="c5e7e-110">Netstandardımplicitpackageversion</span><span class="sxs-lookup"><span data-stu-id="c5e7e-110">NetStandardImplicitPackageVersion</span></span>](#netstandardimplicitpackageversion)

### <a name="targetframework"></a><span data-ttu-id="c5e7e-111">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="c5e7e-111">TargetFramework</span></span>

<span data-ttu-id="c5e7e-112">`TargetFramework`Özelliği, bir [metapackage](../packages.md#metapackages)örtük olarak başvurduğu uygulamanın hedef Framework sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-112">The `TargetFramework` property specifies the target framework version for the app, which implicitly references a [metapackage](../packages.md#metapackages).</span></span> <span data-ttu-id="c5e7e-113">Geçerli hedef çerçeve takma adların listesi için bkz. [SDK stili projelerde hedef çerçeveler](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="c5e7e-113">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>
```

<span data-ttu-id="c5e7e-114">Daha fazla bilgi için bkz. [SDK stili projelerde hedef çerçeveler](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="c5e7e-114">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="targetframeworks"></a><span data-ttu-id="c5e7e-115">Targetçerçeveler</span><span class="sxs-lookup"><span data-stu-id="c5e7e-115">TargetFrameworks</span></span>

<span data-ttu-id="c5e7e-116">`TargetFrameworks`Uygulamanızın birden çok platformu hedeflemesini istediğinizde özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-116">Use the `TargetFrameworks` property when you want your app to target multiple platforms.</span></span> <span data-ttu-id="c5e7e-117">Geçerli hedef çerçeve takma adların listesi için bkz. [SDK stili projelerde hedef çerçeveler](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="c5e7e-117">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

> [!NOTE]
> <span data-ttu-id="c5e7e-118">`TargetFramework`(Tekil) belirtilmişse bu özellik yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-118">This property is ignored if `TargetFramework` (singular) is specified.</span></span>

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
</PropertyGroup>
```

<span data-ttu-id="c5e7e-119">Daha fazla bilgi için bkz. [SDK stili projelerde hedef çerçeveler](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="c5e7e-119">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="netstandardimplicitpackageversion"></a><span data-ttu-id="c5e7e-120">Netstandardımplicitpackageversion</span><span class="sxs-lookup"><span data-stu-id="c5e7e-120">NetStandardImplicitPackageVersion</span></span>

> [!NOTE]
> <span data-ttu-id="c5e7e-121">Bu özellik yalnızca kullanan projeler için geçerlidir `netstandard1.x` .</span><span class="sxs-lookup"><span data-stu-id="c5e7e-121">This property only applies to projects using `netstandard1.x`.</span></span> <span data-ttu-id="c5e7e-122">Kullanan projeler için uygulanmaz `netstandard2.x` .</span><span class="sxs-lookup"><span data-stu-id="c5e7e-122">It doesn't apply to projects that use `netstandard2.x`.</span></span>

<span data-ttu-id="c5e7e-123">`NetStandardImplicitPackageVersion` [Metapackage](../packages.md#metapackages) sürümünden daha düşük bir çerçeve sürümü belirtmek istediğinizde özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-123">Use the `NetStandardImplicitPackageVersion` property when you want to specify a framework version that's lower than the [metapackage](../packages.md#metapackages) version.</span></span> <span data-ttu-id="c5e7e-124">Aşağıdaki örnekteki proje dosyası hedefler, `netstandard1.3` ancak 1.6.0 sürümünü kullanır `NETStandard.Library` .</span><span class="sxs-lookup"><span data-stu-id="c5e7e-124">The project file in the following example targets `netstandard1.3` but uses the 1.6.0 version of `NETStandard.Library`.</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netstandard1.3</TargetFramework>
  <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
</PropertyGroup>
```

## <a name="package-properties"></a><span data-ttu-id="c5e7e-125">Paket özellikleri</span><span class="sxs-lookup"><span data-stu-id="c5e7e-125">Package properties</span></span>

<span data-ttu-id="c5e7e-126">`PackageId` `PackageVersion` `PackageIcon` `Title` `Description` Projenizden oluşturulan paketi betimleyen,,, ve gibi özellikleri belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-126">You can specify properties such as `PackageId`, `PackageVersion`, `PackageIcon`, `Title`, and `Description` to describe the package that gets created from your project.</span></span> <span data-ttu-id="c5e7e-127">Bu ve diğer özellikler hakkında daha fazla bilgi için bkz. [Pack Target](/nuget/reference/msbuild-targets#pack-target).</span><span class="sxs-lookup"><span data-stu-id="c5e7e-127">For information about these and other properties, see [pack target](/nuget/reference/msbuild-targets#pack-target).</span></span>

```xml
<PropertyGroup>
  ...
  <PackageId>ClassLibDotNetStandard</PackageId>
  <Version>1.0.0</Version>
  <Authors>John Doe</Authors>
  <Company>Contoso</Company>
</PropertyGroup>
```

## <a name="publish-properties-and-items"></a><span data-ttu-id="c5e7e-128">Özellikleri ve öğeleri Yayımla</span><span class="sxs-lookup"><span data-stu-id="c5e7e-128">Publish properties and items</span></span>

- [<span data-ttu-id="c5e7e-129">Runtimeıdentifier</span><span class="sxs-lookup"><span data-stu-id="c5e7e-129">RuntimeIdentifier</span></span>](#runtimeidentifier)
- [<span data-ttu-id="c5e7e-130">Runtimetanımlayıcıtanımlayıcıları</span><span class="sxs-lookup"><span data-stu-id="c5e7e-130">RuntimeIdentifiers</span></span>](#runtimeidentifiers)
- [<span data-ttu-id="c5e7e-131">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="c5e7e-131">TrimmerRootAssembly</span></span>](#trimmerrootassembly)
- [<span data-ttu-id="c5e7e-132">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="c5e7e-132">UseAppHost</span></span>](#useapphost)

### <a name="runtimeidentifier"></a><span data-ttu-id="c5e7e-133">Runtimeıdentifier</span><span class="sxs-lookup"><span data-stu-id="c5e7e-133">RuntimeIdentifier</span></span>

<span data-ttu-id="c5e7e-134">`RuntimeIdentifier`Özelliği, proje için tek bir [çalışma zamanı tanımlayıcısı (RID)](../rid-catalog.md) belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-134">The `RuntimeIdentifier` property lets you specify a single [runtime identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="c5e7e-135">RID, kendi kendine içerilen bir dağıtımı yayımlamayı mümkün.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-135">The RID enables publishing a self-contained deployment.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
</PropertyGroup>
```

### <a name="runtimeidentifiers"></a><span data-ttu-id="c5e7e-136">Runtimetanımlayıcıtanımlayıcıları</span><span class="sxs-lookup"><span data-stu-id="c5e7e-136">RuntimeIdentifiers</span></span>

<span data-ttu-id="c5e7e-137">`RuntimeIdentifiers`Özelliği, proje için bir [çalışma zamanı tanımlayıcıları (RID 'ler)](../rid-catalog.md) için noktalı virgülle ayrılmış bir liste belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-137">The `RuntimeIdentifiers` property lets you specify a semicolon-delimited list of [runtime identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="c5e7e-138">Birden çok çalışma zamanı için yayımlamanız gerekiyorsa bu özelliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-138">Use this property if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="c5e7e-139">`RuntimeIdentifiers`, doğru varlıkların grafikte olduğundan emin olmak için geri yükleme zamanında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-139">`RuntimeIdentifiers` is used at restore time to ensure the right assets are in the graph.</span></span>

> [!TIP]
> <span data-ttu-id="c5e7e-140">`RuntimeIdentifier`(tekil) yalnızca tek bir çalışma zamanı gerektiğinde daha hızlı derlemeler sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-140">`RuntimeIdentifier` (singular) can provide faster builds when only a single runtime is required.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
</PropertyGroup>
```

### <a name="trimmerrootassembly"></a><span data-ttu-id="c5e7e-141">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="c5e7e-141">TrimmerRootAssembly</span></span>

<span data-ttu-id="c5e7e-142">`TrimmerRootAssembly`Öğe, bir derlemeyi [*kırpmanıza*](../deploying/trim-self-contained.md)dışlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-142">The `TrimmerRootAssembly` item lets you exclude an assembly from [*trimming*](../deploying/trim-self-contained.md).</span></span> <span data-ttu-id="c5e7e-143">Kırpma, çalışma zamanının kullanılmayan parçalarını paketlenmiş bir uygulamadan kaldırma işlemidir.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-143">Trimming is the process of removing unused parts of the runtime from a packaged application.</span></span> <span data-ttu-id="c5e7e-144">Bazı durumlarda, kırpma gerekli başvuruları yanlış kaldırabilir.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-144">In some cases, trimming might incorrectly remove required references.</span></span>

<span data-ttu-id="c5e7e-145">Aşağıdaki XML, `System.Security` derlemeyi kırpmaya dışlar.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-145">The following XML excludes the `System.Security` assembly from trimming.</span></span>

```xml
<ItemGroup>
  <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

### <a name="useapphost"></a><span data-ttu-id="c5e7e-146">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="c5e7e-146">UseAppHost</span></span>

<span data-ttu-id="c5e7e-147">`UseAppHost`Özelliği, .NET Core SDK 2.1.400 sürümünde tanıtılmıştı.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-147">The `UseAppHost` property was introduced in the 2.1.400 version of the .NET Core SDK.</span></span> <span data-ttu-id="c5e7e-148">Dağıtım için yerel bir yürütülebilir dosyanın oluşturulup oluşturulmayacağını denetler.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-148">It controls whether or not a native executable is created for a deployment.</span></span> <span data-ttu-id="c5e7e-149">Kendi kendine kapsanan dağıtımlar için yerel bir yürütülebilir dosya gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-149">A native executable is required for self-contained deployments.</span></span>

<span data-ttu-id="c5e7e-150">.NET Core 3,0 ve sonraki sürümlerinde, çerçeveye bağlı bir yürütülebilir dosya varsayılan olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-150">In .NET Core 3.0 and later versions, a framework-dependent executable is created by default.</span></span> <span data-ttu-id="c5e7e-151">`UseAppHost` `false` Yürütülebilir dosyanın üretilmesini devre dışı bırakmak için özelliğini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-151">Set the `UseAppHost` property to `false` to disable generation of the executable.</span></span>

```xml
<PropertyGroup>
  <UseAppHost>false</UseAppHost>
</PropertyGroup>
```

<span data-ttu-id="c5e7e-152">Dağıtım hakkında daha fazla bilgi için bkz. [.NET Core uygulama dağıtımı](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="c5e7e-152">For more information about deployment, see [.NET Core application deployment](../deploying/index.md).</span></span>

## <a name="compile-properties"></a><span data-ttu-id="c5e7e-153">Derleme özellikleri</span><span class="sxs-lookup"><span data-stu-id="c5e7e-153">Compile properties</span></span>

- [<span data-ttu-id="c5e7e-154">Embeddedresourceusebağımlıtuponconvention</span><span class="sxs-lookup"><span data-stu-id="c5e7e-154">EmbeddedResourceUseDependentUponConvention</span></span>](#embeddedresourceusedependentuponconvention)
- [<span data-ttu-id="c5e7e-155">LangVersion</span><span class="sxs-lookup"><span data-stu-id="c5e7e-155">LangVersion</span></span>](#langversion)

### <a name="embeddedresourceusedependentuponconvention"></a><span data-ttu-id="c5e7e-156">Embeddedresourceusebağımlıtuponconvention</span><span class="sxs-lookup"><span data-stu-id="c5e7e-156">EmbeddedResourceUseDependentUponConvention</span></span>

<span data-ttu-id="c5e7e-157">Özelliği, kaynak dosyaları `EmbeddedResourceUseDependentUponConvention` ile birlikte bulunan kaynak dosyalardaki tür bilgilerden kaynak bildirim dosyası adlarının oluşturulup oluşturulmayacağını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-157">The `EmbeddedResourceUseDependentUponConvention` property defines whether resource manifest file names are generated from type information in source files that are colocated with resource files.</span></span> <span data-ttu-id="c5e7e-158">Örneğin, *Form1. resx* , *Form1.cs*ile aynı klasörssa ve olarak `EmbeddedResourceUseDependentUponConvention` ayarlanırsa `true` , oluşturulan *. resources* dosyası, *Form1.cs*içinde tanımlanan ilk türden alır.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-158">For example, if *Form1.resx* is in the same folder as *Form1.cs*, and `EmbeddedResourceUseDependentUponConvention` is set to `true`, the generated *.resources* file takes its name from the first type that's defined in *Form1.cs*.</span></span> <span data-ttu-id="c5e7e-159">Örneğin, `MyNamespace.Form1` *Form1.cs*içinde tanımlanan ilk tür ise, oluşturulan dosya adı *MyNamespace. Form1. resources*olur.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-159">For example, if `MyNamespace.Form1` is the first type defined in *Form1.cs*, the generated file name is *MyNamespace.Form1.resources*.</span></span>

> [!NOTE]
> <span data-ttu-id="c5e7e-160">`LogicalName`,, `ManifestResourceName` Veya `DependentUpon` meta veriler bir öğe için belirtilmişse `EmbeddedResource` , bu kaynak dosyası için oluşturulan bildirim dosyası adı bu meta verileri temel alır.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-160">If `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for an `EmbeddedResource` item, the generated manifest file name for that resource file is based on that metadata instead.</span></span>

<span data-ttu-id="c5e7e-161">Varsayılan olarak, yeni bir .NET Core projesinde, bu özellik olarak ayarlanır `true` .</span><span class="sxs-lookup"><span data-stu-id="c5e7e-161">By default, in a new .NET Core project, this property is set to `true`.</span></span> <span data-ttu-id="c5e7e-162">`false`, Ve öğesi için, `LogicalName` `ManifestResourceName` Proje dosyasındaki öğe için, veya olarak ayarlanırsa,, `DependentUpon` `EmbeddedResource` kaynak bildirim dosyası adı projenin kök ad alanını ve *. resx* dosyasının göreli dosya yolunu temel alan olur.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-162">If set to `false`, and no `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for the `EmbeddedResource` item in the project file, the resource manifest file name is based off the root namespace for the project and the relative file path to the *.resx* file.</span></span> <span data-ttu-id="c5e7e-163">Daha fazla bilgi için bkz. [kaynak bildirim dosyalarının adlandırılması](../resources/manifest-file-names.md).</span><span class="sxs-lookup"><span data-stu-id="c5e7e-163">For more information, see [How resource manifest files are named](../resources/manifest-file-names.md).</span></span>

```xml
<PropertyGroup>
  <EmbeddedResourceUseDependentUponConvention>true</EmbeddedResourceUseDependentUponConvention>
</PropertyGroup>
```

### <a name="langversion"></a><span data-ttu-id="c5e7e-164">LangVersion</span><span class="sxs-lookup"><span data-stu-id="c5e7e-164">LangVersion</span></span>

<span data-ttu-id="c5e7e-165">`LangVersion`Özelliği, belirli bir programlama dili sürümü belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-165">The `LangVersion` property lets you specify a specific programming language version.</span></span> <span data-ttu-id="c5e7e-166">Örneğin, C# önizleme özelliklerine erişmek istiyorsanız, `LangVersion` olarak ayarlayın `preview` .</span><span class="sxs-lookup"><span data-stu-id="c5e7e-166">For example, if you want access to C# preview features, set `LangVersion` to `preview`.</span></span>

```xml
<PropertyGroup>
  <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="c5e7e-167">Daha fazla bilgi için bkz. [C# dil sürümü oluşturma](../../csharp/language-reference/configure-language-version.md#override-a-default).</span><span class="sxs-lookup"><span data-stu-id="c5e7e-167">For more information, see [C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).</span></span>

## <a name="run-time-configuration-properties"></a><span data-ttu-id="c5e7e-168">Çalışma zamanı yapılandırma özellikleri</span><span class="sxs-lookup"><span data-stu-id="c5e7e-168">Run-time configuration properties</span></span>

<span data-ttu-id="c5e7e-169">Uygulamanın proje dosyasında MSBuild özelliklerini belirterek bazı çalışma zamanı davranışları yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-169">You can configure some run-time behaviors by specifying MSBuild properties in the project file of the app.</span></span> <span data-ttu-id="c5e7e-170">Çalışma zamanı davranışını yapılandırmanın diğer yolları hakkında daha fazla bilgi için bkz. [.NET Core çalışma zamanı yapılandırma ayarları](../run-time-config/index.md).</span><span class="sxs-lookup"><span data-stu-id="c5e7e-170">For information about other ways of configuring run-time behavior, see [.NET Core run-time configuration settings](../run-time-config/index.md).</span></span>

- [<span data-ttu-id="c5e7e-171">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="c5e7e-171">ConcurrentGarbageCollection</span></span>](#concurrentgarbagecollection)
- [<span data-ttu-id="c5e7e-172">Invariantgenelleştirme</span><span class="sxs-lookup"><span data-stu-id="c5e7e-172">InvariantGlobalization</span></span>](#invariantglobalization)
- [<span data-ttu-id="c5e7e-173">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="c5e7e-173">RetainVMGarbageCollection</span></span>](#retainvmgarbagecollection)
- [<span data-ttu-id="c5e7e-174">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="c5e7e-174">ServerGarbageCollection</span></span>](#servergarbagecollection)
- [<span data-ttu-id="c5e7e-175">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="c5e7e-175">ThreadPoolMaxThreads</span></span>](#threadpoolmaxthreads)
- [<span data-ttu-id="c5e7e-176">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="c5e7e-176">ThreadPoolMinThreads</span></span>](#threadpoolminthreads)
- [<span data-ttu-id="c5e7e-177">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="c5e7e-177">TieredCompilation</span></span>](#tieredcompilation)
- [<span data-ttu-id="c5e7e-178">Tieredcompilationquickjıt</span><span class="sxs-lookup"><span data-stu-id="c5e7e-178">TieredCompilationQuickJit</span></span>](#tieredcompilationquickjit)
- [<span data-ttu-id="c5e7e-179">Tieredcompilationquickjıtfordöngüleri</span><span class="sxs-lookup"><span data-stu-id="c5e7e-179">TieredCompilationQuickJitForLoops</span></span>](#tieredcompilationquickjitforloops)

### <a name="concurrentgarbagecollection"></a><span data-ttu-id="c5e7e-180">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="c5e7e-180">ConcurrentGarbageCollection</span></span>

<span data-ttu-id="c5e7e-181">`ConcurrentGarbageCollection`Özelliği [Background (eşzamanlı) Çöp toplamanın](../../standard/garbage-collection/background-gc.md) etkinleştirilip etkinleştirilmeyeceğini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-181">The `ConcurrentGarbageCollection` property configures whether [background (concurrent) garbage collection](../../standard/garbage-collection/background-gc.md) is enabled.</span></span> <span data-ttu-id="c5e7e-182">`false`Arka plan atık toplamayı devre dışı bırakmak için değerini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-182">Set the value to `false` to disable background garbage collection.</span></span> <span data-ttu-id="c5e7e-183">Daha fazla bilgi için bkz. [System. GC. eşzamanlı/COMPlus_gcConcurrent](../run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent).</span><span class="sxs-lookup"><span data-stu-id="c5e7e-183">For more information, see [System.GC.Concurrent/COMPlus_gcConcurrent](../run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent).</span></span>

```xml
<PropertyGroup>
  <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
</PropertyGroup>
```

### <a name="invariantglobalization"></a><span data-ttu-id="c5e7e-184">Invariantgenelleştirme</span><span class="sxs-lookup"><span data-stu-id="c5e7e-184">InvariantGlobalization</span></span>

<span data-ttu-id="c5e7e-185">`InvariantGlobalization`Özelliği, uygulamanın *Genelleştirme sabit* modunda çalışıp çalışmadığını yapılandırır, bu, kültüre özgü verilere erişimi olmayan anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-185">The `InvariantGlobalization` property configures whether the app runs in *globalization-invariant* mode, which means it doesn't have access to culture-specific data.</span></span> <span data-ttu-id="c5e7e-186">Değeri `true` Genelleştirme sabit modunda çalışacak şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-186">Set the value to `true` to run in globalization-invariant mode.</span></span> <span data-ttu-id="c5e7e-187">Daha fazla bilgi için bkz. [sabit mod](../run-time-config/globalization.md#invariant-mode).</span><span class="sxs-lookup"><span data-stu-id="c5e7e-187">For more information, see [Invariant mode](../run-time-config/globalization.md#invariant-mode).</span></span>

```xml
<PropertyGroup>
  <InvariantGlobalization>true</InvariantGlobalization>
</PropertyGroup>
```

### <a name="retainvmgarbagecollection"></a><span data-ttu-id="c5e7e-188">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="c5e7e-188">RetainVMGarbageCollection</span></span>

<span data-ttu-id="c5e7e-189">`RetainVMGarbageCollection`Özelliği, çöp toplayıcıyı, daha sonra kullanılmak üzere veya serbest bırakmak için silinen bellek segmentlerini bir bekleme listesine koymak üzere yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-189">The `RetainVMGarbageCollection` property configures the garbage collector to put deleted memory segments on a standby list for future use or release them.</span></span> <span data-ttu-id="c5e7e-190">Değeri, `true` çöp toplayıcıya kesimleri bir bekleme listesine koymasını söyler.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-190">Setting the value to `true` tells the garbage collector to put the segments on a standby list.</span></span> <span data-ttu-id="c5e7e-191">Daha fazla bilgi için bkz. [System. GC. RetainVM/COMPlus_GCRetainVM](../run-time-config/garbage-collector.md#systemgcretainvmcomplus_gcretainvm).</span><span class="sxs-lookup"><span data-stu-id="c5e7e-191">For more information, see [System.GC.RetainVM/COMPlus_GCRetainVM](../run-time-config/garbage-collector.md#systemgcretainvmcomplus_gcretainvm).</span></span>

```xml
<PropertyGroup>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
</PropertyGroup>
```

### <a name="servergarbagecollection"></a><span data-ttu-id="c5e7e-192">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="c5e7e-192">ServerGarbageCollection</span></span>

<span data-ttu-id="c5e7e-193">`ServerGarbageCollection`Özelliği, uygulamanın [iş istasyonu çöp toplamayı veya sunucu çöp toplamayı](../../standard/garbage-collection/workstation-server-gc.md)kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-193">The `ServerGarbageCollection` property configures whether the application uses [workstation garbage collection or server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span> <span data-ttu-id="c5e7e-194">Değerini `true` sunucu çöp toplamayı kullanacak şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-194">Set the value to `true` to use server garbage collection.</span></span> <span data-ttu-id="c5e7e-195">Daha fazla bilgi için bkz. [System. GC. Server/COMPlus_gcServer](../run-time-config/garbage-collector.md#systemgcservercomplus_gcserver).</span><span class="sxs-lookup"><span data-stu-id="c5e7e-195">For more information, see [System.GC.Server/COMPlus_gcServer](../run-time-config/garbage-collector.md#systemgcservercomplus_gcserver).</span></span>

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

### <a name="threadpoolmaxthreads"></a><span data-ttu-id="c5e7e-196">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="c5e7e-196">ThreadPoolMaxThreads</span></span>

<span data-ttu-id="c5e7e-197">`ThreadPoolMaxThreads`Özelliği, çalışan iş parçacığı havuzu için en fazla iş parçacığı sayısını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-197">The `ThreadPoolMaxThreads` property configures the maximum number of threads for the worker thread pool.</span></span> <span data-ttu-id="c5e7e-198">Daha fazla bilgi için bkz. [en fazla iş parçacığı](../run-time-config/threading.md#maximum-threads).</span><span class="sxs-lookup"><span data-stu-id="c5e7e-198">For more information, see [Maximum threads](../run-time-config/threading.md#maximum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
</PropertyGroup>
```

### <a name="threadpoolminthreads"></a><span data-ttu-id="c5e7e-199">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="c5e7e-199">ThreadPoolMinThreads</span></span>

<span data-ttu-id="c5e7e-200">`ThreadPoolMinThreads`Özelliği, çalışan iş parçacığı havuzu için en az iş parçacığı sayısını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-200">The `ThreadPoolMinThreads` property configures the minimum number of threads for the worker thread pool.</span></span> <span data-ttu-id="c5e7e-201">Daha fazla bilgi için bkz. [En düşük iş parçacıkları](../run-time-config/threading.md#minimum-threads).</span><span class="sxs-lookup"><span data-stu-id="c5e7e-201">For more information, see [Minimum threads](../run-time-config/threading.md#minimum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
</PropertyGroup>
```

### <a name="tieredcompilation"></a><span data-ttu-id="c5e7e-202">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="c5e7e-202">TieredCompilation</span></span>

<span data-ttu-id="c5e7e-203">`TieredCompilation`Özelliği, Just-In-Time (JIT) derleyicisinin [katmanlı derlemeyi](../whats-new/dotnet-core-3-0.md#tiered-compilation)kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-203">The `TieredCompilation` property configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="c5e7e-204">`false`Katmanlı derlemeyi devre dışı bırakmak için değerini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-204">Set the value to `false` to disable tiered compilation.</span></span> <span data-ttu-id="c5e7e-205">Daha fazla bilgi için bkz. [katmanlı derleme](../run-time-config/compilation.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="c5e7e-205">For more information, see [Tiered compilation](../run-time-config/compilation.md#tiered-compilation).</span></span>

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

### <a name="tieredcompilationquickjit"></a><span data-ttu-id="c5e7e-206">Tieredcompilationquickjıt</span><span class="sxs-lookup"><span data-stu-id="c5e7e-206">TieredCompilationQuickJit</span></span>

<span data-ttu-id="c5e7e-207">`TieredCompilationQuickJit`Özelliği, JIT derleyicisinin hızlı JIT kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-207">The `TieredCompilationQuickJit` property configures whether the JIT compiler uses quick JIT.</span></span> <span data-ttu-id="c5e7e-208">`false`Hızlı JIT 'i devre dışı bırakmak için değerini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-208">Set the value to `false` to disable quick JIT.</span></span> <span data-ttu-id="c5e7e-209">Daha fazla bilgi için bkz. [hızlı JIT](../run-time-config/compilation.md#quick-jit).</span><span class="sxs-lookup"><span data-stu-id="c5e7e-209">For more information, see [Quick JIT](../run-time-config/compilation.md#quick-jit).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

### <a name="tieredcompilationquickjitforloops"></a><span data-ttu-id="c5e7e-210">Tieredcompilationquickjıtfordöngüleri</span><span class="sxs-lookup"><span data-stu-id="c5e7e-210">TieredCompilationQuickJitForLoops</span></span>

<span data-ttu-id="c5e7e-211">`TieredCompilationQuickJitForLoops`Özelliği, JIT derleyicisinin döngüleri içeren yöntemlerde hızlı JIT kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-211">The `TieredCompilationQuickJitForLoops` property configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span> <span data-ttu-id="c5e7e-212">`true`Döngüleri içeren yöntemlerde hızlı JIT 'i etkinleştirmek için değerini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-212">Set the value to `true` to enable quick JIT on methods that contain loops.</span></span> <span data-ttu-id="c5e7e-213">Daha fazla bilgi için bkz. [döngüler Için hızlı JIT](../run-time-config/compilation.md#quick-jit-for-loops).</span><span class="sxs-lookup"><span data-stu-id="c5e7e-213">For more information, see [Quick JIT for loops](../run-time-config/compilation.md#quick-jit-for-loops).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
</PropertyGroup>
```

## <a name="reference-properties-and-items"></a><span data-ttu-id="c5e7e-214">Başvuru özellikleri ve öğeleri</span><span class="sxs-lookup"><span data-stu-id="c5e7e-214">Reference properties and items</span></span>

- [<span data-ttu-id="c5e7e-215">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="c5e7e-215">AssetTargetFallback</span></span>](#assettargetfallback)
- [<span data-ttu-id="c5e7e-216">PackageReference</span><span class="sxs-lookup"><span data-stu-id="c5e7e-216">PackageReference</span></span>](#packagereference)
- [<span data-ttu-id="c5e7e-217">ProjectReference</span><span class="sxs-lookup"><span data-stu-id="c5e7e-217">ProjectReference</span></span>](#projectreference)
- [<span data-ttu-id="c5e7e-218">Başvuru</span><span class="sxs-lookup"><span data-stu-id="c5e7e-218">Reference</span></span>](#reference)
- [<span data-ttu-id="c5e7e-219">Özellikleri geri yükle</span><span class="sxs-lookup"><span data-stu-id="c5e7e-219">Restore properties</span></span>](#restore-properties)

### <a name="assettargetfallback"></a><span data-ttu-id="c5e7e-220">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="c5e7e-220">AssetTargetFallback</span></span>

<span data-ttu-id="c5e7e-221">`AssetTargetFallback`Özelliği, proje başvuruları ve NuGet paketleri için ek uyumlu çerçeve sürümlerini belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-221">The `AssetTargetFallback` property lets you specify additional compatible framework versions for project references and NuGet packages.</span></span> <span data-ttu-id="c5e7e-222">Örneğin, kullanarak bir paket bağımlılığı belirtirseniz `PackageReference` ancak bu paket, projelerinizle uyumlu olan varlıkları içermiyorsa `TargetFramework` , `AssetTargetFallback` özelliği yürütmeye gelir.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-222">For example, if you specify a package dependency using `PackageReference` but that package doesn't contain assets that are compatible with your projects's `TargetFramework`, the `AssetTargetFallback` property comes into play.</span></span> <span data-ttu-id="c5e7e-223">Başvurulan paketin uyumluluğu, içinde belirtilen her bir hedef çerçeve kullanılarak yeniden denetlenir `AssetTargetFallback` .</span><span class="sxs-lookup"><span data-stu-id="c5e7e-223">The compatibility of the referenced package is rechecked using each target framework that's specified in `AssetTargetFallback`.</span></span>

<span data-ttu-id="c5e7e-224">`AssetTargetFallback`Özelliğini bir veya daha fazla [hedef çerçeve sürümüne](../../standard/frameworks.md#supported-target-framework-versions)ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-224">You can set the `AssetTargetFallback` property to one or more [target framework versions](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<PropertyGroup>
  <AssetTargetFallback>net461</AssetTargetFallback>
</PropertyGroup>
```

### <a name="packagereference"></a><span data-ttu-id="c5e7e-225">PackageReference</span><span class="sxs-lookup"><span data-stu-id="c5e7e-225">PackageReference</span></span>

<span data-ttu-id="c5e7e-226">`PackageReference`Öğe, bir NuGet paketine bir başvuru tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-226">The `PackageReference` item defines a reference to a NuGet package.</span></span> <span data-ttu-id="c5e7e-227">Örneğin, [metapackage](../packages.md#metapackages)yerine tek bir pakete başvurmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-227">For example, you may want to reference a single package instead of a [metapackage](../packages.md#metapackages).</span></span>

<span data-ttu-id="c5e7e-228">`Include`Öznitelik, paket kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-228">The `Include` attribute specifies the package ID.</span></span> <span data-ttu-id="c5e7e-229">`Version`Öznitelik, sürümü veya sürüm aralığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-229">The `Version` attribute specifies the version or version range.</span></span> <span data-ttu-id="c5e7e-230">En düşük sürüm, en yüksek sürüm, Aralık veya tam eşleşme belirtme hakkında bilgi için bkz. [Sürüm aralıkları](/nuget/concepts/package-versioning#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="c5e7e-230">For information about how to specify a minimum version, maximum version, range, or exact match, see [Version ranges](/nuget/concepts/package-versioning#version-ranges).</span></span> <span data-ttu-id="c5e7e-231">Aşağıdaki meta verileri bir proje başvurusuna de ekleyebilirsiniz: `IncludeAssets` , `ExcludeAssets` , ve `PrivateAssets` .</span><span class="sxs-lookup"><span data-stu-id="c5e7e-231">You can also add the following metadata to a project reference: `IncludeAssets`, `ExcludeAssets`, and `PrivateAssets`.</span></span>

<span data-ttu-id="c5e7e-232">Aşağıdaki örnekteki proje dosyası kod parçacığı [System. Runtime](https://www.nuget.org/packages/System.Runtime/) paketine başvurur.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-232">The project file snippet in the following example references the [System.Runtime](https://www.nuget.org/packages/System.Runtime/) package.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="System.Runtime" Version="4.3.0" />
</ItemGroup>
```

<span data-ttu-id="c5e7e-233">Daha fazla bilgi için bkz. [Proje dosyalarındaki paket başvuruları](/nuget/consume-packages/package-references-in-project-files).</span><span class="sxs-lookup"><span data-stu-id="c5e7e-233">For more information, see [Package references in project files](/nuget/consume-packages/package-references-in-project-files).</span></span>

### <a name="projectreference"></a><span data-ttu-id="c5e7e-234">ProjectReference</span><span class="sxs-lookup"><span data-stu-id="c5e7e-234">ProjectReference</span></span>

<span data-ttu-id="c5e7e-235">`ProjectReference`Öğe, başka bir projeye yönelik bir başvuru tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-235">The `ProjectReference` item defines a reference to another project.</span></span> <span data-ttu-id="c5e7e-236">Başvurulan proje bir NuGet paket bağımlılığı olarak eklenir, diğer bir deyişle, ile aynı şekilde işlenir `PackageReference` .</span><span class="sxs-lookup"><span data-stu-id="c5e7e-236">The referenced project is added as a NuGet package dependency, that is, it's treated the same as a `PackageReference`.</span></span>

<span data-ttu-id="c5e7e-237">`Include`Öznitelik, projenin yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-237">The `Include` attribute specifies the path to the project.</span></span> <span data-ttu-id="c5e7e-238">Aşağıdaki meta verileri bir proje başvurusuna de ekleyebilirsiniz: `IncludeAssets` , `ExcludeAssets` , ve `PrivateAssets` .</span><span class="sxs-lookup"><span data-stu-id="c5e7e-238">You can also add the following metadata to a project reference: `IncludeAssets`, `ExcludeAssets`, and `PrivateAssets`.</span></span>

<span data-ttu-id="c5e7e-239">Aşağıdaki örnekteki proje dosyası kod parçacığı adlı bir projeye başvurur `Project2` .</span><span class="sxs-lookup"><span data-stu-id="c5e7e-239">The project file snippet in the following example references a project named `Project2`.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\Project2.csproj" />
</ItemGroup>
```

### <a name="reference"></a><span data-ttu-id="c5e7e-240">Başvuru</span><span class="sxs-lookup"><span data-stu-id="c5e7e-240">Reference</span></span>

<span data-ttu-id="c5e7e-241">`Reference`Öğe, derleme dosyasına bir başvuru tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-241">The `Reference` item defines a reference to an assembly file.</span></span>

<span data-ttu-id="c5e7e-242">`Include`Öznitelik, dosyanın adını belirtir ve `HintPath` meta veriler derlemenin yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-242">The `Include` attribute specifies the name of the file, and the `HintPath` metadata specifies the path to the assembly.</span></span>

```xml
<ItemGroup>
  <Reference Include="MyAssembly">
    <HintPath>..\..\Assemblies\MyAssembly.dll</HintPath>
  </Reference>
</ItemGroup>
```

### <a name="restore-properties"></a><span data-ttu-id="c5e7e-243">Özellikleri geri yükle</span><span class="sxs-lookup"><span data-stu-id="c5e7e-243">Restore properties</span></span>

<span data-ttu-id="c5e7e-244">Başvurulan bir paketin geri yüklenmesi, tüm doğrudan bağımlılıklarını ve bu bağımlılıkların tüm bağımlılıklarını yükler.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-244">Restoring a referenced package installs all of its direct dependencies and all the dependencies of those dependencies.</span></span> <span data-ttu-id="c5e7e-245">Ve gibi özellikler belirterek paket geri yüklemesini özelleştirebilirsiniz `RestorePackagesPath` `RestoreIgnoreFailedSources` .</span><span class="sxs-lookup"><span data-stu-id="c5e7e-245">You can customize package restoration by specifying properties such as `RestorePackagesPath` and `RestoreIgnoreFailedSources`.</span></span> <span data-ttu-id="c5e7e-246">Bu ve diğer özellikler hakkında daha fazla bilgi için bkz. [hedefi geri yükleme](/nuget/reference/msbuild-targets#restore-target).</span><span class="sxs-lookup"><span data-stu-id="c5e7e-246">For more information about these and other properties, see [restore target](/nuget/reference/msbuild-targets#restore-target).</span></span>

```xml
<PropertyGroup>
  <RestoreIgnoreFailedSource>true</RestoreIgnoreFailedSource>
</PropertyGroup>
```

## <a name="see-also"></a><span data-ttu-id="c5e7e-247">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c5e7e-247">See also</span></span>

- [<span data-ttu-id="c5e7e-248">MSBuild şema başvurusu</span><span class="sxs-lookup"><span data-stu-id="c5e7e-248">MSBuild schema reference</span></span>](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [<span data-ttu-id="c5e7e-249">Ortak MSBuild özellikleri</span><span class="sxs-lookup"><span data-stu-id="c5e7e-249">Common MSBuild properties</span></span>](/visualstudio/msbuild/common-msbuild-project-properties)
- [<span data-ttu-id="c5e7e-250">NuGet paketi için MSBuild özellikleri</span><span class="sxs-lookup"><span data-stu-id="c5e7e-250">MSBuild properties for NuGet pack</span></span>](/nuget/reference/msbuild-targets#pack-target)
- [<span data-ttu-id="c5e7e-251">NuGet geri yükleme için MSBuild özellikleri</span><span class="sxs-lookup"><span data-stu-id="c5e7e-251">MSBuild properties for NuGet restore</span></span>](/nuget/reference/msbuild-targets#restore-properties)
- [<span data-ttu-id="c5e7e-252">Bir derlemeyi özelleştirme</span><span class="sxs-lookup"><span data-stu-id="c5e7e-252">Customize a build</span></span>](/visualstudio/msbuild/customize-your-build)
