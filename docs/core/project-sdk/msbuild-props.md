---
title: Microsoft. NET. SDK için MSBuild özellikleri
description: MSBuild özellikleri ve .NET Core SDK anlayan öğeler için başvuru.
ms.date: 02/14/2020
ms.topic: reference
ms.custom: updateeachrelease
ms.openlocfilehash: 866253a0526741f5554971a5202c179106503951
ms.sourcegitcommit: 43d5aca3fda42bad8843f6c4e72f6bd52daa55f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89598017"
---
# <a name="msbuild-reference-for-net-core-sdk-projects"></a><span data-ttu-id="a63d9-103">.NET Core SDK projeleri için MSBuild başvurusu</span><span class="sxs-lookup"><span data-stu-id="a63d9-103">MSBuild reference for .NET Core SDK projects</span></span>

<span data-ttu-id="a63d9-104">Bu sayfa, .NET Core projelerini yapılandırmak için kullanabileceğiniz MSBuild özelliklerine ve öğelerine yönelik bir başvurudur.</span><span class="sxs-lookup"><span data-stu-id="a63d9-104">This page is a reference for the MSBuild properties and items that you can use to configure .NET Core projects.</span></span>

> [!NOTE]
> <span data-ttu-id="a63d9-105">Bu sayfa devam eden bir çalışmadır ve .NET Core SDK için tüm yararlı MSBuild özelliklerini listelemez.</span><span class="sxs-lookup"><span data-stu-id="a63d9-105">This page is a work in progress and does not list all of the useful MSBuild properties for the .NET Core SDK.</span></span> <span data-ttu-id="a63d9-106">Ortak MSBuild özelliklerinin bir listesi için bkz. [Ortak MSBuild özellikleri](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="a63d9-106">For a list of common MSBuild properties, see [Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="framework-properties"></a><span data-ttu-id="a63d9-107">Çerçeve özellikleri</span><span class="sxs-lookup"><span data-stu-id="a63d9-107">Framework properties</span></span>

- [<span data-ttu-id="a63d9-108">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="a63d9-108">TargetFramework</span></span>](#targetframework)
- [<span data-ttu-id="a63d9-109">Targetçerçeveler</span><span class="sxs-lookup"><span data-stu-id="a63d9-109">TargetFrameworks</span></span>](#targetframeworks)
- [<span data-ttu-id="a63d9-110">Netstandardımplicitpackageversion</span><span class="sxs-lookup"><span data-stu-id="a63d9-110">NetStandardImplicitPackageVersion</span></span>](#netstandardimplicitpackageversion)

### <a name="targetframework"></a><span data-ttu-id="a63d9-111">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="a63d9-111">TargetFramework</span></span>

<span data-ttu-id="a63d9-112">`TargetFramework`Özelliği, uygulamanın hedef Framework sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="a63d9-112">The `TargetFramework` property specifies the target framework version for the app.</span></span> <span data-ttu-id="a63d9-113">Geçerli hedef çerçeve takma adların listesi için bkz. [SDK stili projelerde hedef çerçeveler](../../standard/frameworks.md#supported-target-frameworks).</span><span class="sxs-lookup"><span data-stu-id="a63d9-113">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-frameworks).</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>
```

<span data-ttu-id="a63d9-114">Daha fazla bilgi için bkz. [SDK stili projelerde hedef çerçeveler](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="a63d9-114">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="targetframeworks"></a><span data-ttu-id="a63d9-115">Targetçerçeveler</span><span class="sxs-lookup"><span data-stu-id="a63d9-115">TargetFrameworks</span></span>

<span data-ttu-id="a63d9-116">`TargetFrameworks`Uygulamanızın birden çok platformu hedeflemesini istediğinizde özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a63d9-116">Use the `TargetFrameworks` property when you want your app to target multiple platforms.</span></span> <span data-ttu-id="a63d9-117">Geçerli hedef çerçeve takma adların listesi için bkz. [SDK stili projelerde hedef çerçeveler](../../standard/frameworks.md#supported-target-frameworks).</span><span class="sxs-lookup"><span data-stu-id="a63d9-117">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-frameworks).</span></span>

> [!NOTE]
> <span data-ttu-id="a63d9-118">`TargetFramework`(Tekil) belirtilmişse bu özellik yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="a63d9-118">This property is ignored if `TargetFramework` (singular) is specified.</span></span>

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
</PropertyGroup>
```

<span data-ttu-id="a63d9-119">Daha fazla bilgi için bkz. [SDK stili projelerde hedef çerçeveler](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="a63d9-119">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="netstandardimplicitpackageversion"></a><span data-ttu-id="a63d9-120">Netstandardımplicitpackageversion</span><span class="sxs-lookup"><span data-stu-id="a63d9-120">NetStandardImplicitPackageVersion</span></span>

> [!NOTE]
> <span data-ttu-id="a63d9-121">Bu özellik yalnızca kullanan projeler için geçerlidir `netstandard1.x` .</span><span class="sxs-lookup"><span data-stu-id="a63d9-121">This property only applies to projects using `netstandard1.x`.</span></span> <span data-ttu-id="a63d9-122">Kullanan projeler için uygulanmaz `netstandard2.x` .</span><span class="sxs-lookup"><span data-stu-id="a63d9-122">It doesn't apply to projects that use `netstandard2.x`.</span></span>

<span data-ttu-id="a63d9-123">`NetStandardImplicitPackageVersion`Metapackage sürümünden daha düşük bir çerçeve sürümü belirtmek istediğinizde özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a63d9-123">Use the `NetStandardImplicitPackageVersion` property when you want to specify a framework version that's lower than the metapackage version.</span></span> <span data-ttu-id="a63d9-124">Aşağıdaki örnekteki proje dosyası hedefler, `netstandard1.3` ancak 1.6.0 sürümünü kullanır `NETStandard.Library` .</span><span class="sxs-lookup"><span data-stu-id="a63d9-124">The project file in the following example targets `netstandard1.3` but uses the 1.6.0 version of `NETStandard.Library`.</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netstandard1.3</TargetFramework>
  <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
</PropertyGroup>
```

## <a name="package-properties"></a><span data-ttu-id="a63d9-125">Paket özellikleri</span><span class="sxs-lookup"><span data-stu-id="a63d9-125">Package properties</span></span>

<span data-ttu-id="a63d9-126">`PackageId` `PackageVersion` `PackageIcon` `Title` `Description` Projenizden oluşturulan paketi betimleyen,,, ve gibi özellikleri belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a63d9-126">You can specify properties such as `PackageId`, `PackageVersion`, `PackageIcon`, `Title`, and `Description` to describe the package that gets created from your project.</span></span> <span data-ttu-id="a63d9-127">Bu ve diğer özellikler hakkında daha fazla bilgi için bkz. [Pack Target](/nuget/reference/msbuild-targets#pack-target).</span><span class="sxs-lookup"><span data-stu-id="a63d9-127">For information about these and other properties, see [pack target](/nuget/reference/msbuild-targets#pack-target).</span></span>

```xml
<PropertyGroup>
  ...
  <PackageId>ClassLibDotNetStandard</PackageId>
  <Version>1.0.0</Version>
  <Authors>John Doe</Authors>
  <Company>Contoso</Company>
</PropertyGroup>
```

## <a name="publish-properties-and-items"></a><span data-ttu-id="a63d9-128">Özellikleri ve öğeleri Yayımla</span><span class="sxs-lookup"><span data-stu-id="a63d9-128">Publish properties and items</span></span>

- [<span data-ttu-id="a63d9-129">Runtimeıdentifier</span><span class="sxs-lookup"><span data-stu-id="a63d9-129">RuntimeIdentifier</span></span>](#runtimeidentifier)
- [<span data-ttu-id="a63d9-130">Runtimetanımlayıcıtanımlayıcıları</span><span class="sxs-lookup"><span data-stu-id="a63d9-130">RuntimeIdentifiers</span></span>](#runtimeidentifiers)
- [<span data-ttu-id="a63d9-131">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="a63d9-131">TrimmerRootAssembly</span></span>](#trimmerrootassembly)
- [<span data-ttu-id="a63d9-132">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="a63d9-132">UseAppHost</span></span>](#useapphost)

### <a name="runtimeidentifier"></a><span data-ttu-id="a63d9-133">Runtimeıdentifier</span><span class="sxs-lookup"><span data-stu-id="a63d9-133">RuntimeIdentifier</span></span>

<span data-ttu-id="a63d9-134">`RuntimeIdentifier`Özelliği, proje için tek bir [çalışma zamanı tanımlayıcısı (RID)](../rid-catalog.md) belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="a63d9-134">The `RuntimeIdentifier` property lets you specify a single [runtime identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="a63d9-135">RID, kendi kendine içerilen bir dağıtımı yayımlamayı mümkün.</span><span class="sxs-lookup"><span data-stu-id="a63d9-135">The RID enables publishing a self-contained deployment.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
</PropertyGroup>
```

### <a name="runtimeidentifiers"></a><span data-ttu-id="a63d9-136">Runtimetanımlayıcıtanımlayıcıları</span><span class="sxs-lookup"><span data-stu-id="a63d9-136">RuntimeIdentifiers</span></span>

<span data-ttu-id="a63d9-137">`RuntimeIdentifiers`Özelliği, proje için bir [çalışma zamanı tanımlayıcıları (RID 'ler)](../rid-catalog.md) için noktalı virgülle ayrılmış bir liste belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="a63d9-137">The `RuntimeIdentifiers` property lets you specify a semicolon-delimited list of [runtime identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="a63d9-138">Birden çok çalışma zamanı için yayımlamanız gerekiyorsa bu özelliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="a63d9-138">Use this property if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="a63d9-139">`RuntimeIdentifiers` , doğru varlıkların grafikte olduğundan emin olmak için geri yükleme zamanında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a63d9-139">`RuntimeIdentifiers` is used at restore time to ensure the right assets are in the graph.</span></span>

> [!TIP]
> <span data-ttu-id="a63d9-140">`RuntimeIdentifier` (tekil) yalnızca tek bir çalışma zamanı gerektiğinde daha hızlı derlemeler sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="a63d9-140">`RuntimeIdentifier` (singular) can provide faster builds when only a single runtime is required.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
</PropertyGroup>
```

### <a name="trimmerrootassembly"></a><span data-ttu-id="a63d9-141">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="a63d9-141">TrimmerRootAssembly</span></span>

<span data-ttu-id="a63d9-142">`TrimmerRootAssembly`Öğe, bir derlemeyi [*kırpmanıza*](../deploying/trim-self-contained.md)dışlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="a63d9-142">The `TrimmerRootAssembly` item lets you exclude an assembly from [*trimming*](../deploying/trim-self-contained.md).</span></span> <span data-ttu-id="a63d9-143">Kırpma, çalışma zamanının kullanılmayan parçalarını paketlenmiş bir uygulamadan kaldırma işlemidir.</span><span class="sxs-lookup"><span data-stu-id="a63d9-143">Trimming is the process of removing unused parts of the runtime from a packaged application.</span></span> <span data-ttu-id="a63d9-144">Bazı durumlarda, kırpma gerekli başvuruları yanlış kaldırabilir.</span><span class="sxs-lookup"><span data-stu-id="a63d9-144">In some cases, trimming might incorrectly remove required references.</span></span>

<span data-ttu-id="a63d9-145">Aşağıdaki XML, `System.Security` derlemeyi kırpmaya dışlar.</span><span class="sxs-lookup"><span data-stu-id="a63d9-145">The following XML excludes the `System.Security` assembly from trimming.</span></span>

```xml
<ItemGroup>
  <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

### <a name="useapphost"></a><span data-ttu-id="a63d9-146">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="a63d9-146">UseAppHost</span></span>

<span data-ttu-id="a63d9-147">`UseAppHost`Özelliği, .NET Core SDK 2.1.400 sürümünde tanıtılmıştı.</span><span class="sxs-lookup"><span data-stu-id="a63d9-147">The `UseAppHost` property was introduced in the 2.1.400 version of the .NET Core SDK.</span></span> <span data-ttu-id="a63d9-148">Dağıtım için yerel bir yürütülebilir dosyanın oluşturulup oluşturulmayacağını denetler.</span><span class="sxs-lookup"><span data-stu-id="a63d9-148">It controls whether or not a native executable is created for a deployment.</span></span> <span data-ttu-id="a63d9-149">Kendi kendine kapsanan dağıtımlar için yerel bir yürütülebilir dosya gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a63d9-149">A native executable is required for self-contained deployments.</span></span>

<span data-ttu-id="a63d9-150">.NET Core 3,0 ve sonraki sürümlerinde, çerçeveye bağlı bir yürütülebilir dosya varsayılan olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a63d9-150">In .NET Core 3.0 and later versions, a framework-dependent executable is created by default.</span></span> <span data-ttu-id="a63d9-151">`UseAppHost` `false` Yürütülebilir dosyanın üretilmesini devre dışı bırakmak için özelliğini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a63d9-151">Set the `UseAppHost` property to `false` to disable generation of the executable.</span></span>

```xml
<PropertyGroup>
  <UseAppHost>false</UseAppHost>
</PropertyGroup>
```

<span data-ttu-id="a63d9-152">Dağıtım hakkında daha fazla bilgi için bkz. [.NET Core uygulama dağıtımı](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="a63d9-152">For more information about deployment, see [.NET Core application deployment](../deploying/index.md).</span></span>

## <a name="compile-properties"></a><span data-ttu-id="a63d9-153">Derleme özellikleri</span><span class="sxs-lookup"><span data-stu-id="a63d9-153">Compile properties</span></span>

- [<span data-ttu-id="a63d9-154">Embeddedresourceusebağımlıtuponconvention</span><span class="sxs-lookup"><span data-stu-id="a63d9-154">EmbeddedResourceUseDependentUponConvention</span></span>](#embeddedresourceusedependentuponconvention)
- [<span data-ttu-id="a63d9-155">LangVersion</span><span class="sxs-lookup"><span data-stu-id="a63d9-155">LangVersion</span></span>](#langversion)

### <a name="embeddedresourceusedependentuponconvention"></a><span data-ttu-id="a63d9-156">Embeddedresourceusebağımlıtuponconvention</span><span class="sxs-lookup"><span data-stu-id="a63d9-156">EmbeddedResourceUseDependentUponConvention</span></span>

<span data-ttu-id="a63d9-157">Özelliği, kaynak dosyaları `EmbeddedResourceUseDependentUponConvention` ile birlikte bulunan kaynak dosyalardaki tür bilgilerden kaynak bildirim dosyası adlarının oluşturulup oluşturulmayacağını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a63d9-157">The `EmbeddedResourceUseDependentUponConvention` property defines whether resource manifest file names are generated from type information in source files that are colocated with resource files.</span></span> <span data-ttu-id="a63d9-158">Örneğin, *Form1. resx* , *Form1.cs*ile aynı klasörssa ve olarak `EmbeddedResourceUseDependentUponConvention` ayarlanırsa `true` , oluşturulan *. resources* dosyası, *Form1.cs*içinde tanımlanan ilk türden alır.</span><span class="sxs-lookup"><span data-stu-id="a63d9-158">For example, if *Form1.resx* is in the same folder as *Form1.cs*, and `EmbeddedResourceUseDependentUponConvention` is set to `true`, the generated *.resources* file takes its name from the first type that's defined in *Form1.cs*.</span></span> <span data-ttu-id="a63d9-159">Örneğin, `MyNamespace.Form1` *Form1.cs*içinde tanımlanan ilk tür ise, oluşturulan dosya adı *MyNamespace. Form1. resources*olur.</span><span class="sxs-lookup"><span data-stu-id="a63d9-159">For example, if `MyNamespace.Form1` is the first type defined in *Form1.cs*, the generated file name is *MyNamespace.Form1.resources*.</span></span>

> [!NOTE]
> <span data-ttu-id="a63d9-160">`LogicalName`,, `ManifestResourceName` Veya `DependentUpon` meta veriler bir öğe için belirtilmişse `EmbeddedResource` , bu kaynak dosyası için oluşturulan bildirim dosyası adı bu meta verileri temel alır.</span><span class="sxs-lookup"><span data-stu-id="a63d9-160">If `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for an `EmbeddedResource` item, the generated manifest file name for that resource file is based on that metadata instead.</span></span>

<span data-ttu-id="a63d9-161">Varsayılan olarak, yeni bir .NET Core projesinde, bu özellik olarak ayarlanır `true` .</span><span class="sxs-lookup"><span data-stu-id="a63d9-161">By default, in a new .NET Core project, this property is set to `true`.</span></span> <span data-ttu-id="a63d9-162">`false`, Ve öğesi için, `LogicalName` `ManifestResourceName` Proje dosyasındaki öğe için, veya olarak ayarlanırsa,, `DependentUpon` `EmbeddedResource` kaynak bildirim dosyası adı projenin kök ad alanını ve *. resx* dosyasının göreli dosya yolunu temel alan olur.</span><span class="sxs-lookup"><span data-stu-id="a63d9-162">If set to `false`, and no `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for the `EmbeddedResource` item in the project file, the resource manifest file name is based off the root namespace for the project and the relative file path to the *.resx* file.</span></span> <span data-ttu-id="a63d9-163">Daha fazla bilgi için bkz. [kaynak bildirim dosyalarının adlandırılması](../resources/manifest-file-names.md).</span><span class="sxs-lookup"><span data-stu-id="a63d9-163">For more information, see [How resource manifest files are named](../resources/manifest-file-names.md).</span></span>

```xml
<PropertyGroup>
  <EmbeddedResourceUseDependentUponConvention>true</EmbeddedResourceUseDependentUponConvention>
</PropertyGroup>
```

### <a name="langversion"></a><span data-ttu-id="a63d9-164">LangVersion</span><span class="sxs-lookup"><span data-stu-id="a63d9-164">LangVersion</span></span>

<span data-ttu-id="a63d9-165">`LangVersion`Özelliği, belirli bir programlama dili sürümü belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a63d9-165">The `LangVersion` property lets you specify a specific programming language version.</span></span> <span data-ttu-id="a63d9-166">Örneğin, C# önizleme özelliklerine erişmek istiyorsanız, `LangVersion` olarak ayarlayın `preview` .</span><span class="sxs-lookup"><span data-stu-id="a63d9-166">For example, if you want access to C# preview features, set `LangVersion` to `preview`.</span></span>

```xml
<PropertyGroup>
  <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="a63d9-167">Daha fazla bilgi için bkz. [C# dil sürümü oluşturma](../../csharp/language-reference/configure-language-version.md#override-a-default).</span><span class="sxs-lookup"><span data-stu-id="a63d9-167">For more information, see [C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).</span></span>

## <a name="code-analysis-properties"></a><span data-ttu-id="a63d9-168">Kod Analizi özellikleri</span><span class="sxs-lookup"><span data-stu-id="a63d9-168">Code analysis properties</span></span>

### <a name="analysislevel"></a><span data-ttu-id="a63d9-169">AnalysisLevel</span><span class="sxs-lookup"><span data-stu-id="a63d9-169">AnalysisLevel</span></span>

<span data-ttu-id="a63d9-170">`AnalysisLevel`Özelliği, bir kod analizi düzeyi belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="a63d9-170">The `AnalysisLevel` property lets you specify a code analysis level.</span></span> <span data-ttu-id="a63d9-171">Örneğin, önizleme kodu Çözümleyicileri için erişim istiyorsanız, `AnalysisLevel` olarak ayarlayın `preview` .</span><span class="sxs-lookup"><span data-stu-id="a63d9-171">For example, if you want access to preview code analyzers, set `AnalysisLevel` to `preview`.</span></span> <span data-ttu-id="a63d9-172">Varsayılan değer: `latest`.</span><span class="sxs-lookup"><span data-stu-id="a63d9-172">The default value is `latest`.</span></span>

```xml
<PropertyGroup>
  <AnalysisLevel>preview</AnalysisLevel>
</PropertyGroup>
```

<span data-ttu-id="a63d9-173">Aşağıdaki tabloda kullanılabilir seçenekler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a63d9-173">The following table shows the available options.</span></span>

| <span data-ttu-id="a63d9-174">Değer</span><span class="sxs-lookup"><span data-stu-id="a63d9-174">Value</span></span> | <span data-ttu-id="a63d9-175">Anlamı</span><span class="sxs-lookup"><span data-stu-id="a63d9-175">Meaning</span></span> |
|-|-|
| `latest` | <span data-ttu-id="a63d9-176">Yayınlanan en son kod Çözümleyicileri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a63d9-176">The latest code analyzers that have been released are used.</span></span> <span data-ttu-id="a63d9-177">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="a63d9-177">This is the default.</span></span> |
| `preview` | <span data-ttu-id="a63d9-178">Önizleme aşamasında olsalar dahi, en son kod Çözümleyicileri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a63d9-178">The latest code analyzers are used, even if they are in preview.</span></span> |
| `5.0` | <span data-ttu-id="a63d9-179">.NET 5,0 sürümü için etkinleştirilen kurallar kümesi, daha yeni kurallar kullanılabilir olsa bile kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a63d9-179">The set of rules that was enabled for the .NET 5.0 release is used, even if newer rules are available.</span></span> |
| `5` | <span data-ttu-id="a63d9-180">.NET 5,0 sürümü için etkinleştirilen kurallar kümesi, daha yeni kurallar kullanılabilir olsa bile kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a63d9-180">The set of rules that was enabled for the .NET 5.0 release is used, even if newer rules are available.</span></span> |

### <a name="codeanalysistreatwarningsaserrors"></a><span data-ttu-id="a63d9-181">CodeAnalysisTreatWarningsAsErrors</span><span class="sxs-lookup"><span data-stu-id="a63d9-181">CodeAnalysisTreatWarningsAsErrors</span></span>

<span data-ttu-id="a63d9-182">`CodeAnalysisTreatWarningsAsErrors`Özelliği, kod analizi uyarılarının uyarı olarak kabul edilip edilmeyeceğini yapılandırmanıza ve derlemeyi kesmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="a63d9-182">The `CodeAnalysisTreatWarningsAsErrors` property lets you configure whether code analysis warnings should be treated as warnings and break the build.</span></span> <span data-ttu-id="a63d9-183">Projelerinizi oluştururken bayrağını kullanırsanız `-warnaserror` , [.NET kod analizi](../../fundamentals/productivity/code-analysis.md) uyarıları da hata olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="a63d9-183">If you use the `-warnaserror` flag when you build your projects, [.NET code analysis](../../fundamentals/productivity/code-analysis.md) warnings are also treated as errors.</span></span> <span data-ttu-id="a63d9-184">Yalnızca derleyici uyarılarının hata olarak değerlendirilmesini istiyorsanız, `CodeAnalysisTreatWarningsAsErrors` MSBuild özelliğini `false` proje dosyanızda olarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a63d9-184">If you only want compiler warnings to be treated as errors, you can set the `CodeAnalysisTreatWarningsAsErrors` MSBuild property to `false` in your project file.</span></span>

```xml
<PropertyGroup>
  <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
</PropertyGroup>
```

### <a name="enablenetanalyzers"></a><span data-ttu-id="a63d9-185">Enablenetçözümleyiciler</span><span class="sxs-lookup"><span data-stu-id="a63d9-185">EnableNETAnalyzers</span></span>

<span data-ttu-id="a63d9-186">.Net [Code Analysis](../../fundamentals/productivity/code-analysis.md) , .NET 5,0 veya üstünü hedefleyen projeler için varsayılan olarak etkinleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a63d9-186">[.NET Code analysis](../../fundamentals/productivity/code-analysis.md) is enabled, by default, for projects that target .NET 5.0 or later.</span></span> <span data-ttu-id="a63d9-187">Özelliği true olarak ayarlayarak .NET 'in önceki sürümlerini hedefleyen projeler için .NET kod analizini etkinleştirebilirsiniz `EnableNETAnalyzers` .</span><span class="sxs-lookup"><span data-stu-id="a63d9-187">You can enable .NET code analysis for projects that target earlier versions of .NET by setting the `EnableNETAnalyzers` property to true.</span></span> <span data-ttu-id="a63d9-188">Herhangi bir projede kod analizini devre dışı bırakmak için bu özelliği olarak ayarlayın `false` .</span><span class="sxs-lookup"><span data-stu-id="a63d9-188">To disable code analysis in any project, set this property to `false`.</span></span>

```xml
<PropertyGroup>
  <EnableNETAnalyzers>true</EnableNETAnalyzers>
</PropertyGroup>
```

> [!TIP]
> <span data-ttu-id="a63d9-189">.NET 5,0 ' den önceki .NET sürümlerini hedefleyen projelerde .NET kod analizini etkinleştirmenin bir diğer yolu, [Analysislevel](#analysislevel) özelliğini olarak ayarlamadır `latest` .</span><span class="sxs-lookup"><span data-stu-id="a63d9-189">Another way to enable .NET code analysis on projects that target .NET versions prior to .NET 5.0 is to set the [AnalysisLevel](#analysislevel) property to `latest`.</span></span>

## <a name="run-time-configuration-properties"></a><span data-ttu-id="a63d9-190">Çalışma zamanı yapılandırma özellikleri</span><span class="sxs-lookup"><span data-stu-id="a63d9-190">Run-time configuration properties</span></span>

<span data-ttu-id="a63d9-191">Uygulamanın proje dosyasında MSBuild özelliklerini belirterek bazı çalışma zamanı davranışları yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a63d9-191">You can configure some run-time behaviors by specifying MSBuild properties in the project file of the app.</span></span> <span data-ttu-id="a63d9-192">Çalışma zamanı davranışını yapılandırmanın diğer yolları hakkında daha fazla bilgi için bkz. [.NET Core çalışma zamanı yapılandırma ayarları](../run-time-config/index.md).</span><span class="sxs-lookup"><span data-stu-id="a63d9-192">For information about other ways of configuring run-time behavior, see [.NET Core run-time configuration settings](../run-time-config/index.md).</span></span>

- [<span data-ttu-id="a63d9-193">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="a63d9-193">ConcurrentGarbageCollection</span></span>](#concurrentgarbagecollection)
- [<span data-ttu-id="a63d9-194">Invariantgenelleştirme</span><span class="sxs-lookup"><span data-stu-id="a63d9-194">InvariantGlobalization</span></span>](#invariantglobalization)
- [<span data-ttu-id="a63d9-195">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="a63d9-195">RetainVMGarbageCollection</span></span>](#retainvmgarbagecollection)
- [<span data-ttu-id="a63d9-196">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="a63d9-196">ServerGarbageCollection</span></span>](#servergarbagecollection)
- [<span data-ttu-id="a63d9-197">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="a63d9-197">ThreadPoolMaxThreads</span></span>](#threadpoolmaxthreads)
- [<span data-ttu-id="a63d9-198">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="a63d9-198">ThreadPoolMinThreads</span></span>](#threadpoolminthreads)
- [<span data-ttu-id="a63d9-199">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="a63d9-199">TieredCompilation</span></span>](#tieredcompilation)
- [<span data-ttu-id="a63d9-200">Tieredcompilationquickjıt</span><span class="sxs-lookup"><span data-stu-id="a63d9-200">TieredCompilationQuickJit</span></span>](#tieredcompilationquickjit)
- [<span data-ttu-id="a63d9-201">Tieredcompilationquickjıtfordöngüleri</span><span class="sxs-lookup"><span data-stu-id="a63d9-201">TieredCompilationQuickJitForLoops</span></span>](#tieredcompilationquickjitforloops)

### <a name="concurrentgarbagecollection"></a><span data-ttu-id="a63d9-202">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="a63d9-202">ConcurrentGarbageCollection</span></span>

<span data-ttu-id="a63d9-203">`ConcurrentGarbageCollection`Özelliği [Background (eşzamanlı) Çöp toplamanın](../../standard/garbage-collection/background-gc.md) etkinleştirilip etkinleştirilmeyeceğini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="a63d9-203">The `ConcurrentGarbageCollection` property configures whether [background (concurrent) garbage collection](../../standard/garbage-collection/background-gc.md) is enabled.</span></span> <span data-ttu-id="a63d9-204">`false`Arka plan atık toplamayı devre dışı bırakmak için değerini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a63d9-204">Set the value to `false` to disable background garbage collection.</span></span> <span data-ttu-id="a63d9-205">Daha fazla bilgi için bkz. [arka plan GC](../run-time-config/garbage-collector.md#background-gc).</span><span class="sxs-lookup"><span data-stu-id="a63d9-205">For more information, see [Background GC](../run-time-config/garbage-collector.md#background-gc).</span></span>

```xml
<PropertyGroup>
  <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
</PropertyGroup>
```

### <a name="invariantglobalization"></a><span data-ttu-id="a63d9-206">Invariantgenelleştirme</span><span class="sxs-lookup"><span data-stu-id="a63d9-206">InvariantGlobalization</span></span>

<span data-ttu-id="a63d9-207">`InvariantGlobalization`Özelliği, uygulamanın *Genelleştirme sabit* modunda çalışıp çalışmadığını yapılandırır, bu, kültüre özgü verilere erişimi olmayan anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a63d9-207">The `InvariantGlobalization` property configures whether the app runs in *globalization-invariant* mode, which means it doesn't have access to culture-specific data.</span></span> <span data-ttu-id="a63d9-208">Değeri `true` Genelleştirme sabit modunda çalışacak şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a63d9-208">Set the value to `true` to run in globalization-invariant mode.</span></span> <span data-ttu-id="a63d9-209">Daha fazla bilgi için bkz. [sabit mod](../run-time-config/globalization.md#invariant-mode).</span><span class="sxs-lookup"><span data-stu-id="a63d9-209">For more information, see [Invariant mode](../run-time-config/globalization.md#invariant-mode).</span></span>

```xml
<PropertyGroup>
  <InvariantGlobalization>true</InvariantGlobalization>
</PropertyGroup>
```

### <a name="retainvmgarbagecollection"></a><span data-ttu-id="a63d9-210">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="a63d9-210">RetainVMGarbageCollection</span></span>

<span data-ttu-id="a63d9-211">`RetainVMGarbageCollection`Özelliği, çöp toplayıcıyı, daha sonra kullanılmak üzere veya serbest bırakmak için silinen bellek segmentlerini bir bekleme listesine koymak üzere yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="a63d9-211">The `RetainVMGarbageCollection` property configures the garbage collector to put deleted memory segments on a standby list for future use or release them.</span></span> <span data-ttu-id="a63d9-212">Değeri, `true` çöp toplayıcıya kesimleri bir bekleme listesine koymasını söyler.</span><span class="sxs-lookup"><span data-stu-id="a63d9-212">Setting the value to `true` tells the garbage collector to put the segments on a standby list.</span></span> <span data-ttu-id="a63d9-213">Daha fazla bilgi için bkz. [VM 'Yi koruma](../run-time-config/garbage-collector.md#retain-vm).</span><span class="sxs-lookup"><span data-stu-id="a63d9-213">For more information, see [Retain VM](../run-time-config/garbage-collector.md#retain-vm).</span></span>

```xml
<PropertyGroup>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
</PropertyGroup>
```

### <a name="servergarbagecollection"></a><span data-ttu-id="a63d9-214">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="a63d9-214">ServerGarbageCollection</span></span>

<span data-ttu-id="a63d9-215">`ServerGarbageCollection`Özelliği, uygulamanın [iş istasyonu çöp toplamayı veya sunucu çöp toplamayı](../../standard/garbage-collection/workstation-server-gc.md)kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="a63d9-215">The `ServerGarbageCollection` property configures whether the application uses [workstation garbage collection or server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span> <span data-ttu-id="a63d9-216">Değerini `true` sunucu çöp toplamayı kullanacak şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a63d9-216">Set the value to `true` to use server garbage collection.</span></span> <span data-ttu-id="a63d9-217">Daha fazla bilgi için bkz. [Workstation vs Server](../run-time-config/garbage-collector.md#workstation-vs-server).</span><span class="sxs-lookup"><span data-stu-id="a63d9-217">For more information, see [Workstation vs. server](../run-time-config/garbage-collector.md#workstation-vs-server).</span></span>

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

### <a name="threadpoolmaxthreads"></a><span data-ttu-id="a63d9-218">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="a63d9-218">ThreadPoolMaxThreads</span></span>

<span data-ttu-id="a63d9-219">`ThreadPoolMaxThreads`Özelliği, çalışan iş parçacığı havuzu için en fazla iş parçacığı sayısını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="a63d9-219">The `ThreadPoolMaxThreads` property configures the maximum number of threads for the worker thread pool.</span></span> <span data-ttu-id="a63d9-220">Daha fazla bilgi için bkz. [en fazla iş parçacığı](../run-time-config/threading.md#maximum-threads).</span><span class="sxs-lookup"><span data-stu-id="a63d9-220">For more information, see [Maximum threads](../run-time-config/threading.md#maximum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
</PropertyGroup>
```

### <a name="threadpoolminthreads"></a><span data-ttu-id="a63d9-221">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="a63d9-221">ThreadPoolMinThreads</span></span>

<span data-ttu-id="a63d9-222">`ThreadPoolMinThreads`Özelliği, çalışan iş parçacığı havuzu için en az iş parçacığı sayısını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="a63d9-222">The `ThreadPoolMinThreads` property configures the minimum number of threads for the worker thread pool.</span></span> <span data-ttu-id="a63d9-223">Daha fazla bilgi için bkz. [En düşük iş parçacıkları](../run-time-config/threading.md#minimum-threads).</span><span class="sxs-lookup"><span data-stu-id="a63d9-223">For more information, see [Minimum threads](../run-time-config/threading.md#minimum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
</PropertyGroup>
```

### <a name="tieredcompilation"></a><span data-ttu-id="a63d9-224">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="a63d9-224">TieredCompilation</span></span>

<span data-ttu-id="a63d9-225">`TieredCompilation`Özelliği, Just-In-Time (JIT) derleyicisinin [katmanlı derlemeyi](../whats-new/dotnet-core-3-0.md#tiered-compilation)kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="a63d9-225">The `TieredCompilation` property configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="a63d9-226">`false`Katmanlı derlemeyi devre dışı bırakmak için değerini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a63d9-226">Set the value to `false` to disable tiered compilation.</span></span> <span data-ttu-id="a63d9-227">Daha fazla bilgi için bkz. [katmanlı derleme](../run-time-config/compilation.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="a63d9-227">For more information, see [Tiered compilation](../run-time-config/compilation.md#tiered-compilation).</span></span>

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

### <a name="tieredcompilationquickjit"></a><span data-ttu-id="a63d9-228">Tieredcompilationquickjıt</span><span class="sxs-lookup"><span data-stu-id="a63d9-228">TieredCompilationQuickJit</span></span>

<span data-ttu-id="a63d9-229">`TieredCompilationQuickJit`Özelliği, JIT derleyicisinin hızlı JIT kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="a63d9-229">The `TieredCompilationQuickJit` property configures whether the JIT compiler uses quick JIT.</span></span> <span data-ttu-id="a63d9-230">`false`Hızlı JIT 'i devre dışı bırakmak için değerini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a63d9-230">Set the value to `false` to disable quick JIT.</span></span> <span data-ttu-id="a63d9-231">Daha fazla bilgi için bkz. [hızlı JIT](../run-time-config/compilation.md#quick-jit).</span><span class="sxs-lookup"><span data-stu-id="a63d9-231">For more information, see [Quick JIT](../run-time-config/compilation.md#quick-jit).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

### <a name="tieredcompilationquickjitforloops"></a><span data-ttu-id="a63d9-232">Tieredcompilationquickjıtfordöngüleri</span><span class="sxs-lookup"><span data-stu-id="a63d9-232">TieredCompilationQuickJitForLoops</span></span>

<span data-ttu-id="a63d9-233">`TieredCompilationQuickJitForLoops`Özelliği, JIT derleyicisinin döngüleri içeren yöntemlerde hızlı JIT kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="a63d9-233">The `TieredCompilationQuickJitForLoops` property configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span> <span data-ttu-id="a63d9-234">`true`Döngüleri içeren yöntemlerde hızlı JIT 'i etkinleştirmek için değerini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a63d9-234">Set the value to `true` to enable quick JIT on methods that contain loops.</span></span> <span data-ttu-id="a63d9-235">Daha fazla bilgi için bkz. [döngüler Için hızlı JIT](../run-time-config/compilation.md#quick-jit-for-loops).</span><span class="sxs-lookup"><span data-stu-id="a63d9-235">For more information, see [Quick JIT for loops](../run-time-config/compilation.md#quick-jit-for-loops).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
</PropertyGroup>
```

## <a name="reference-properties-and-items"></a><span data-ttu-id="a63d9-236">Başvuru özellikleri ve öğeleri</span><span class="sxs-lookup"><span data-stu-id="a63d9-236">Reference properties and items</span></span>

- [<span data-ttu-id="a63d9-237">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="a63d9-237">AssetTargetFallback</span></span>](#assettargetfallback)
- [<span data-ttu-id="a63d9-238">PackageReference</span><span class="sxs-lookup"><span data-stu-id="a63d9-238">PackageReference</span></span>](#packagereference)
- [<span data-ttu-id="a63d9-239">ProjectReference</span><span class="sxs-lookup"><span data-stu-id="a63d9-239">ProjectReference</span></span>](#projectreference)
- [<span data-ttu-id="a63d9-240">Başvuru</span><span class="sxs-lookup"><span data-stu-id="a63d9-240">Reference</span></span>](#reference)
- [<span data-ttu-id="a63d9-241">Özellikleri geri yükle</span><span class="sxs-lookup"><span data-stu-id="a63d9-241">Restore properties</span></span>](#restore-properties)

### <a name="assettargetfallback"></a><span data-ttu-id="a63d9-242">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="a63d9-242">AssetTargetFallback</span></span>

<span data-ttu-id="a63d9-243">`AssetTargetFallback`Özelliği, proje başvuruları ve NuGet paketleri için ek uyumlu çerçeve sürümlerini belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a63d9-243">The `AssetTargetFallback` property lets you specify additional compatible framework versions for project references and NuGet packages.</span></span> <span data-ttu-id="a63d9-244">Örneğin, kullanarak bir paket bağımlılığı belirtirseniz `PackageReference` ancak bu paket, projelerinizle uyumlu olan varlıkları içermiyorsa `TargetFramework` , `AssetTargetFallback` özelliği yürütmeye gelir.</span><span class="sxs-lookup"><span data-stu-id="a63d9-244">For example, if you specify a package dependency using `PackageReference` but that package doesn't contain assets that are compatible with your projects's `TargetFramework`, the `AssetTargetFallback` property comes into play.</span></span> <span data-ttu-id="a63d9-245">Başvurulan paketin uyumluluğu, içinde belirtilen her bir hedef çerçeve kullanılarak yeniden denetlenir `AssetTargetFallback` .</span><span class="sxs-lookup"><span data-stu-id="a63d9-245">The compatibility of the referenced package is rechecked using each target framework that's specified in `AssetTargetFallback`.</span></span>

<span data-ttu-id="a63d9-246">`AssetTargetFallback`Özelliğini bir veya daha fazla [hedef çerçeve sürümüne](../../standard/frameworks.md#supported-target-frameworks)ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a63d9-246">You can set the `AssetTargetFallback` property to one or more [target framework versions](../../standard/frameworks.md#supported-target-frameworks).</span></span>

```xml
<PropertyGroup>
  <AssetTargetFallback>net461</AssetTargetFallback>
</PropertyGroup>
```

### <a name="packagereference"></a><span data-ttu-id="a63d9-247">PackageReference</span><span class="sxs-lookup"><span data-stu-id="a63d9-247">PackageReference</span></span>

<span data-ttu-id="a63d9-248">`PackageReference`Öğe, bir NuGet paketine bir başvuru tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a63d9-248">The `PackageReference` item defines a reference to a NuGet package.</span></span>

<span data-ttu-id="a63d9-249">`Include`Öznitelik, paket kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a63d9-249">The `Include` attribute specifies the package ID.</span></span> <span data-ttu-id="a63d9-250">`Version`Öznitelik, sürümü veya sürüm aralığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a63d9-250">The `Version` attribute specifies the version or version range.</span></span> <span data-ttu-id="a63d9-251">En düşük sürüm, en yüksek sürüm, Aralık veya tam eşleşme belirtme hakkında bilgi için bkz. [Sürüm aralıkları](/nuget/concepts/package-versioning#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="a63d9-251">For information about how to specify a minimum version, maximum version, range, or exact match, see [Version ranges](/nuget/concepts/package-versioning#version-ranges).</span></span> <span data-ttu-id="a63d9-252">Aşağıdaki meta verileri bir proje başvurusuna de ekleyebilirsiniz: `IncludeAssets` , `ExcludeAssets` , ve `PrivateAssets` .</span><span class="sxs-lookup"><span data-stu-id="a63d9-252">You can also add the following metadata to a project reference: `IncludeAssets`, `ExcludeAssets`, and `PrivateAssets`.</span></span>

<span data-ttu-id="a63d9-253">Aşağıdaki örnekteki proje dosyası kod parçacığı [System. Runtime](https://www.nuget.org/packages/System.Runtime/) paketine başvurur.</span><span class="sxs-lookup"><span data-stu-id="a63d9-253">The project file snippet in the following example references the [System.Runtime](https://www.nuget.org/packages/System.Runtime/) package.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="System.Runtime" Version="4.3.0" />
</ItemGroup>
```

<span data-ttu-id="a63d9-254">Daha fazla bilgi için bkz. [Proje dosyalarındaki paket başvuruları](/nuget/consume-packages/package-references-in-project-files).</span><span class="sxs-lookup"><span data-stu-id="a63d9-254">For more information, see [Package references in project files](/nuget/consume-packages/package-references-in-project-files).</span></span>

### <a name="projectreference"></a><span data-ttu-id="a63d9-255">ProjectReference</span><span class="sxs-lookup"><span data-stu-id="a63d9-255">ProjectReference</span></span>

<span data-ttu-id="a63d9-256">`ProjectReference`Öğe, başka bir projeye yönelik bir başvuru tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a63d9-256">The `ProjectReference` item defines a reference to another project.</span></span> <span data-ttu-id="a63d9-257">Başvurulan proje bir NuGet paket bağımlılığı olarak eklenir, diğer bir deyişle, ile aynı şekilde işlenir `PackageReference` .</span><span class="sxs-lookup"><span data-stu-id="a63d9-257">The referenced project is added as a NuGet package dependency, that is, it's treated the same as a `PackageReference`.</span></span>

<span data-ttu-id="a63d9-258">`Include`Öznitelik, projenin yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="a63d9-258">The `Include` attribute specifies the path to the project.</span></span> <span data-ttu-id="a63d9-259">Aşağıdaki meta verileri bir proje başvurusuna de ekleyebilirsiniz: `IncludeAssets` , `ExcludeAssets` , ve `PrivateAssets` .</span><span class="sxs-lookup"><span data-stu-id="a63d9-259">You can also add the following metadata to a project reference: `IncludeAssets`, `ExcludeAssets`, and `PrivateAssets`.</span></span>

<span data-ttu-id="a63d9-260">Aşağıdaki örnekteki proje dosyası kod parçacığı adlı bir projeye başvurur `Project2` .</span><span class="sxs-lookup"><span data-stu-id="a63d9-260">The project file snippet in the following example references a project named `Project2`.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\Project2.csproj" />
</ItemGroup>
```

### <a name="reference"></a><span data-ttu-id="a63d9-261">Başvuru</span><span class="sxs-lookup"><span data-stu-id="a63d9-261">Reference</span></span>

<span data-ttu-id="a63d9-262">`Reference`Öğe, derleme dosyasına bir başvuru tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a63d9-262">The `Reference` item defines a reference to an assembly file.</span></span>

<span data-ttu-id="a63d9-263">`Include`Öznitelik, dosyanın adını belirtir ve `HintPath` meta veriler derlemenin yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="a63d9-263">The `Include` attribute specifies the name of the file, and the `HintPath` metadata specifies the path to the assembly.</span></span>

```xml
<ItemGroup>
  <Reference Include="MyAssembly">
    <HintPath>..\..\Assemblies\MyAssembly.dll</HintPath>
  </Reference>
</ItemGroup>
```

### <a name="restore-properties"></a><span data-ttu-id="a63d9-264">Özellikleri geri yükle</span><span class="sxs-lookup"><span data-stu-id="a63d9-264">Restore properties</span></span>

<span data-ttu-id="a63d9-265">Başvurulan bir paketin geri yüklenmesi, tüm doğrudan bağımlılıklarını ve bu bağımlılıkların tüm bağımlılıklarını yükler.</span><span class="sxs-lookup"><span data-stu-id="a63d9-265">Restoring a referenced package installs all of its direct dependencies and all the dependencies of those dependencies.</span></span> <span data-ttu-id="a63d9-266">Ve gibi özellikler belirterek paket geri yüklemesini özelleştirebilirsiniz `RestorePackagesPath` `RestoreIgnoreFailedSources` .</span><span class="sxs-lookup"><span data-stu-id="a63d9-266">You can customize package restoration by specifying properties such as `RestorePackagesPath` and `RestoreIgnoreFailedSources`.</span></span> <span data-ttu-id="a63d9-267">Bu ve diğer özellikler hakkında daha fazla bilgi için bkz. [hedefi geri yükleme](/nuget/reference/msbuild-targets#restore-target).</span><span class="sxs-lookup"><span data-stu-id="a63d9-267">For more information about these and other properties, see [restore target](/nuget/reference/msbuild-targets#restore-target).</span></span>

```xml
<PropertyGroup>
  <RestoreIgnoreFailedSource>true</RestoreIgnoreFailedSource>
</PropertyGroup>
```

## <a name="see-also"></a><span data-ttu-id="a63d9-268">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a63d9-268">See also</span></span>

- [<span data-ttu-id="a63d9-269">MSBuild şema başvurusu</span><span class="sxs-lookup"><span data-stu-id="a63d9-269">MSBuild schema reference</span></span>](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [<span data-ttu-id="a63d9-270">Ortak MSBuild özellikleri</span><span class="sxs-lookup"><span data-stu-id="a63d9-270">Common MSBuild properties</span></span>](/visualstudio/msbuild/common-msbuild-project-properties)
- [<span data-ttu-id="a63d9-271">NuGet paketi için MSBuild özellikleri</span><span class="sxs-lookup"><span data-stu-id="a63d9-271">MSBuild properties for NuGet pack</span></span>](/nuget/reference/msbuild-targets#pack-target)
- [<span data-ttu-id="a63d9-272">NuGet geri yükleme için MSBuild özellikleri</span><span class="sxs-lookup"><span data-stu-id="a63d9-272">MSBuild properties for NuGet restore</span></span>](/nuget/reference/msbuild-targets#restore-properties)
- [<span data-ttu-id="a63d9-273">Bir derlemeyi özelleştirme</span><span class="sxs-lookup"><span data-stu-id="a63d9-273">Customize a build</span></span>](/visualstudio/msbuild/customize-your-build)
