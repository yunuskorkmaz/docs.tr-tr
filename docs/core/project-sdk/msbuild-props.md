---
title: Microsoft. NET. SDK için MSBuild özellikleri
description: MSBuild özellikleri ve .NET SDK tarafından anlaşılan öğeler için başvuru.
ms.date: 02/14/2020
ms.topic: reference
ms.custom: updateeachrelease
ms.openlocfilehash: faa0dc0e94800a49b56af8810562ee0540f118d2
ms.sourcegitcommit: c04535ad05e374fb269fcfc6509217755fbc0d54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2020
ms.locfileid: "91247585"
---
# <a name="msbuild-reference-for-net-sdk-projects"></a><span data-ttu-id="528e9-103">.NET SDK projeleri için MSBuild başvurusu</span><span class="sxs-lookup"><span data-stu-id="528e9-103">MSBuild reference for .NET SDK projects</span></span>

<span data-ttu-id="528e9-104">Bu sayfa, MSBuild özelliklerine ve .NET projelerini yapılandırmak için kullanabileceğiniz öğelere yönelik bir başvurudur.</span><span class="sxs-lookup"><span data-stu-id="528e9-104">This page is a reference for the MSBuild properties and items that you can use to configure .NET projects.</span></span>

> [!NOTE]
> <span data-ttu-id="528e9-105">Bu sayfa devam eden bir çalışmadır ve .NET SDK için tüm kullanışlı MSBuild özelliklerini listelemez.</span><span class="sxs-lookup"><span data-stu-id="528e9-105">This page is a work in progress and does not list all of the useful MSBuild properties for the .NET SDK.</span></span> <span data-ttu-id="528e9-106">Ortak MSBuild özelliklerinin bir listesi için bkz. [Ortak MSBuild özellikleri](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="528e9-106">For a list of common MSBuild properties, see [Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="framework-properties"></a><span data-ttu-id="528e9-107">Çerçeve özellikleri</span><span class="sxs-lookup"><span data-stu-id="528e9-107">Framework properties</span></span>

- [<span data-ttu-id="528e9-108">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="528e9-108">TargetFramework</span></span>](#targetframework)
- [<span data-ttu-id="528e9-109">Targetçerçeveler</span><span class="sxs-lookup"><span data-stu-id="528e9-109">TargetFrameworks</span></span>](#targetframeworks)
- [<span data-ttu-id="528e9-110">Netstandardımplicitpackageversion</span><span class="sxs-lookup"><span data-stu-id="528e9-110">NetStandardImplicitPackageVersion</span></span>](#netstandardimplicitpackageversion)

### <a name="targetframework"></a><span data-ttu-id="528e9-111">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="528e9-111">TargetFramework</span></span>

<span data-ttu-id="528e9-112">`TargetFramework`Özelliği, uygulamanın hedef Framework sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="528e9-112">The `TargetFramework` property specifies the target framework version for the app.</span></span> <span data-ttu-id="528e9-113">Geçerli hedef çerçeve takma adların listesi için bkz. [SDK stili projelerde hedef çerçeveler](../../standard/frameworks.md#supported-target-frameworks).</span><span class="sxs-lookup"><span data-stu-id="528e9-113">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-frameworks).</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>
```

<span data-ttu-id="528e9-114">Daha fazla bilgi için bkz. [SDK stili projelerde hedef çerçeveler](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="528e9-114">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="targetframeworks"></a><span data-ttu-id="528e9-115">Targetçerçeveler</span><span class="sxs-lookup"><span data-stu-id="528e9-115">TargetFrameworks</span></span>

<span data-ttu-id="528e9-116">`TargetFrameworks`Uygulamanızın birden çok platformu hedeflemesini istediğinizde özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="528e9-116">Use the `TargetFrameworks` property when you want your app to target multiple platforms.</span></span> <span data-ttu-id="528e9-117">Geçerli hedef çerçeve takma adların listesi için bkz. [SDK stili projelerde hedef çerçeveler](../../standard/frameworks.md#supported-target-frameworks).</span><span class="sxs-lookup"><span data-stu-id="528e9-117">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-frameworks).</span></span>

> [!NOTE]
> <span data-ttu-id="528e9-118">`TargetFramework`(Tekil) belirtilmişse bu özellik yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="528e9-118">This property is ignored if `TargetFramework` (singular) is specified.</span></span>

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
</PropertyGroup>
```

<span data-ttu-id="528e9-119">Daha fazla bilgi için bkz. [SDK stili projelerde hedef çerçeveler](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="528e9-119">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="netstandardimplicitpackageversion"></a><span data-ttu-id="528e9-120">Netstandardımplicitpackageversion</span><span class="sxs-lookup"><span data-stu-id="528e9-120">NetStandardImplicitPackageVersion</span></span>

> [!NOTE]
> <span data-ttu-id="528e9-121">Bu özellik yalnızca kullanan projeler için geçerlidir `netstandard1.x` .</span><span class="sxs-lookup"><span data-stu-id="528e9-121">This property only applies to projects using `netstandard1.x`.</span></span> <span data-ttu-id="528e9-122">Kullanan projeler için uygulanmaz `netstandard2.x` .</span><span class="sxs-lookup"><span data-stu-id="528e9-122">It doesn't apply to projects that use `netstandard2.x`.</span></span>

<span data-ttu-id="528e9-123">`NetStandardImplicitPackageVersion`Metapackage sürümünden daha düşük bir çerçeve sürümü belirtmek istediğinizde özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="528e9-123">Use the `NetStandardImplicitPackageVersion` property when you want to specify a framework version that's lower than the metapackage version.</span></span> <span data-ttu-id="528e9-124">Aşağıdaki örnekteki proje dosyası hedefler, `netstandard1.3` ancak 1.6.0 sürümünü kullanır `NETStandard.Library` .</span><span class="sxs-lookup"><span data-stu-id="528e9-124">The project file in the following example targets `netstandard1.3` but uses the 1.6.0 version of `NETStandard.Library`.</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netstandard1.3</TargetFramework>
  <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
</PropertyGroup>
```

## <a name="package-properties"></a><span data-ttu-id="528e9-125">Paket özellikleri</span><span class="sxs-lookup"><span data-stu-id="528e9-125">Package properties</span></span>

<span data-ttu-id="528e9-126">`PackageId` `PackageVersion` `PackageIcon` `Title` `Description` Projenizden oluşturulan paketi betimleyen,,, ve gibi özellikleri belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="528e9-126">You can specify properties such as `PackageId`, `PackageVersion`, `PackageIcon`, `Title`, and `Description` to describe the package that gets created from your project.</span></span> <span data-ttu-id="528e9-127">Bu ve diğer özellikler hakkında daha fazla bilgi için bkz. [Pack Target](/nuget/reference/msbuild-targets#pack-target).</span><span class="sxs-lookup"><span data-stu-id="528e9-127">For information about these and other properties, see [pack target](/nuget/reference/msbuild-targets#pack-target).</span></span>

```xml
<PropertyGroup>
  ...
  <PackageId>ClassLibDotNetStandard</PackageId>
  <Version>1.0.0</Version>
  <Authors>John Doe</Authors>
  <Company>Contoso</Company>
</PropertyGroup>
```

## <a name="publish-properties-and-items"></a><span data-ttu-id="528e9-128">Özellikleri ve öğeleri Yayımla</span><span class="sxs-lookup"><span data-stu-id="528e9-128">Publish properties and items</span></span>

- [<span data-ttu-id="528e9-129">Runtimeıdentifier</span><span class="sxs-lookup"><span data-stu-id="528e9-129">RuntimeIdentifier</span></span>](#runtimeidentifier)
- [<span data-ttu-id="528e9-130">Runtimetanımlayıcıtanımlayıcıları</span><span class="sxs-lookup"><span data-stu-id="528e9-130">RuntimeIdentifiers</span></span>](#runtimeidentifiers)
- [<span data-ttu-id="528e9-131">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="528e9-131">TrimmerRootAssembly</span></span>](#trimmerrootassembly)
- [<span data-ttu-id="528e9-132">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="528e9-132">UseAppHost</span></span>](#useapphost)

### <a name="runtimeidentifier"></a><span data-ttu-id="528e9-133">Runtimeıdentifier</span><span class="sxs-lookup"><span data-stu-id="528e9-133">RuntimeIdentifier</span></span>

<span data-ttu-id="528e9-134">`RuntimeIdentifier`Özelliği, proje için tek bir [çalışma zamanı tanımlayıcısı (RID)](../rid-catalog.md) belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="528e9-134">The `RuntimeIdentifier` property lets you specify a single [runtime identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="528e9-135">RID, kendi kendine içerilen bir dağıtımı yayımlamayı mümkün.</span><span class="sxs-lookup"><span data-stu-id="528e9-135">The RID enables publishing a self-contained deployment.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
</PropertyGroup>
```

### <a name="runtimeidentifiers"></a><span data-ttu-id="528e9-136">Runtimetanımlayıcıtanımlayıcıları</span><span class="sxs-lookup"><span data-stu-id="528e9-136">RuntimeIdentifiers</span></span>

<span data-ttu-id="528e9-137">`RuntimeIdentifiers`Özelliği, proje için bir [çalışma zamanı tanımlayıcıları (RID 'ler)](../rid-catalog.md) için noktalı virgülle ayrılmış bir liste belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="528e9-137">The `RuntimeIdentifiers` property lets you specify a semicolon-delimited list of [runtime identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="528e9-138">Birden çok çalışma zamanı için yayımlamanız gerekiyorsa bu özelliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="528e9-138">Use this property if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="528e9-139">`RuntimeIdentifiers` , doğru varlıkların grafikte olduğundan emin olmak için geri yükleme zamanında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="528e9-139">`RuntimeIdentifiers` is used at restore time to ensure the right assets are in the graph.</span></span>

> [!TIP]
> <span data-ttu-id="528e9-140">`RuntimeIdentifier` (tekil) yalnızca tek bir çalışma zamanı gerektiğinde daha hızlı derlemeler sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="528e9-140">`RuntimeIdentifier` (singular) can provide faster builds when only a single runtime is required.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
</PropertyGroup>
```

### <a name="trimmerrootassembly"></a><span data-ttu-id="528e9-141">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="528e9-141">TrimmerRootAssembly</span></span>

<span data-ttu-id="528e9-142">`TrimmerRootAssembly`Öğe, bir derlemeyi [*kırpmanıza*](../deploying/trim-self-contained.md)dışlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="528e9-142">The `TrimmerRootAssembly` item lets you exclude an assembly from [*trimming*](../deploying/trim-self-contained.md).</span></span> <span data-ttu-id="528e9-143">Kırpma, çalışma zamanının kullanılmayan parçalarını paketlenmiş bir uygulamadan kaldırma işlemidir.</span><span class="sxs-lookup"><span data-stu-id="528e9-143">Trimming is the process of removing unused parts of the runtime from a packaged application.</span></span> <span data-ttu-id="528e9-144">Bazı durumlarda, kırpma gerekli başvuruları yanlış kaldırabilir.</span><span class="sxs-lookup"><span data-stu-id="528e9-144">In some cases, trimming might incorrectly remove required references.</span></span>

<span data-ttu-id="528e9-145">Aşağıdaki XML, `System.Security` derlemeyi kırpmaya dışlar.</span><span class="sxs-lookup"><span data-stu-id="528e9-145">The following XML excludes the `System.Security` assembly from trimming.</span></span>

```xml
<ItemGroup>
  <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

### <a name="useapphost"></a><span data-ttu-id="528e9-146">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="528e9-146">UseAppHost</span></span>

<span data-ttu-id="528e9-147">`UseAppHost`Özelliği .NET SDK 'sının 2.1.400 sürümünde sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="528e9-147">The `UseAppHost` property was introduced in the 2.1.400 version of the .NET SDK.</span></span> <span data-ttu-id="528e9-148">Dağıtım için yerel bir yürütülebilir dosyanın oluşturulup oluşturulmayacağını denetler.</span><span class="sxs-lookup"><span data-stu-id="528e9-148">It controls whether or not a native executable is created for a deployment.</span></span> <span data-ttu-id="528e9-149">Kendi kendine kapsanan dağıtımlar için yerel bir yürütülebilir dosya gereklidir.</span><span class="sxs-lookup"><span data-stu-id="528e9-149">A native executable is required for self-contained deployments.</span></span>

<span data-ttu-id="528e9-150">.NET Core 3,0 ve sonraki sürümlerinde, çerçeveye bağlı bir yürütülebilir dosya varsayılan olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="528e9-150">In .NET Core 3.0 and later versions, a framework-dependent executable is created by default.</span></span> <span data-ttu-id="528e9-151">`UseAppHost` `false` Yürütülebilir dosyanın üretilmesini devre dışı bırakmak için özelliğini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="528e9-151">Set the `UseAppHost` property to `false` to disable generation of the executable.</span></span>

```xml
<PropertyGroup>
  <UseAppHost>false</UseAppHost>
</PropertyGroup>
```

<span data-ttu-id="528e9-152">Dağıtım hakkında daha fazla bilgi için bkz. [.NET uygulama dağıtımı](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="528e9-152">For more information about deployment, see [.NET application deployment](../deploying/index.md).</span></span>

## <a name="compile-properties"></a><span data-ttu-id="528e9-153">Derleme özellikleri</span><span class="sxs-lookup"><span data-stu-id="528e9-153">Compile properties</span></span>

- [<span data-ttu-id="528e9-154">Embeddedresourceusebağımlıtuponconvention</span><span class="sxs-lookup"><span data-stu-id="528e9-154">EmbeddedResourceUseDependentUponConvention</span></span>](#embeddedresourceusedependentuponconvention)
- [<span data-ttu-id="528e9-155">LangVersion</span><span class="sxs-lookup"><span data-stu-id="528e9-155">LangVersion</span></span>](#langversion)

### <a name="embeddedresourceusedependentuponconvention"></a><span data-ttu-id="528e9-156">Embeddedresourceusebağımlıtuponconvention</span><span class="sxs-lookup"><span data-stu-id="528e9-156">EmbeddedResourceUseDependentUponConvention</span></span>

<span data-ttu-id="528e9-157">Özelliği, kaynak dosyaları `EmbeddedResourceUseDependentUponConvention` ile birlikte bulunan kaynak dosyalardaki tür bilgilerden kaynak bildirim dosyası adlarının oluşturulup oluşturulmayacağını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="528e9-157">The `EmbeddedResourceUseDependentUponConvention` property defines whether resource manifest file names are generated from type information in source files that are colocated with resource files.</span></span> <span data-ttu-id="528e9-158">Örneğin, *Form1. resx* , *Form1.cs*ile aynı klasörssa ve olarak `EmbeddedResourceUseDependentUponConvention` ayarlanırsa `true` , oluşturulan *. resources* dosyası, *Form1.cs*içinde tanımlanan ilk türden alır.</span><span class="sxs-lookup"><span data-stu-id="528e9-158">For example, if *Form1.resx* is in the same folder as *Form1.cs*, and `EmbeddedResourceUseDependentUponConvention` is set to `true`, the generated *.resources* file takes its name from the first type that's defined in *Form1.cs*.</span></span> <span data-ttu-id="528e9-159">Örneğin, `MyNamespace.Form1` *Form1.cs*içinde tanımlanan ilk tür ise, oluşturulan dosya adı *MyNamespace. Form1. resources*olur.</span><span class="sxs-lookup"><span data-stu-id="528e9-159">For example, if `MyNamespace.Form1` is the first type defined in *Form1.cs*, the generated file name is *MyNamespace.Form1.resources*.</span></span>

> [!NOTE]
> <span data-ttu-id="528e9-160">`LogicalName`,, `ManifestResourceName` Veya `DependentUpon` meta veriler bir öğe için belirtilmişse `EmbeddedResource` , bu kaynak dosyası için oluşturulan bildirim dosyası adı bu meta verileri temel alır.</span><span class="sxs-lookup"><span data-stu-id="528e9-160">If `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for an `EmbeddedResource` item, the generated manifest file name for that resource file is based on that metadata instead.</span></span>

<span data-ttu-id="528e9-161">Varsayılan olarak, yeni bir .NET projesinde, bu özellik olarak ayarlanır `true` .</span><span class="sxs-lookup"><span data-stu-id="528e9-161">By default, in a new .NET project, this property is set to `true`.</span></span> <span data-ttu-id="528e9-162">`false`, Ve öğesi için, `LogicalName` `ManifestResourceName` Proje dosyasındaki öğe için, veya olarak ayarlanırsa,, `DependentUpon` `EmbeddedResource` kaynak bildirim dosyası adı projenin kök ad alanını ve *. resx* dosyasının göreli dosya yolunu temel alan olur.</span><span class="sxs-lookup"><span data-stu-id="528e9-162">If set to `false`, and no `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for the `EmbeddedResource` item in the project file, the resource manifest file name is based off the root namespace for the project and the relative file path to the *.resx* file.</span></span> <span data-ttu-id="528e9-163">Daha fazla bilgi için bkz. [kaynak bildirim dosyalarının adlandırılması](../resources/manifest-file-names.md).</span><span class="sxs-lookup"><span data-stu-id="528e9-163">For more information, see [How resource manifest files are named](../resources/manifest-file-names.md).</span></span>

```xml
<PropertyGroup>
  <EmbeddedResourceUseDependentUponConvention>true</EmbeddedResourceUseDependentUponConvention>
</PropertyGroup>
```

### <a name="langversion"></a><span data-ttu-id="528e9-164">LangVersion</span><span class="sxs-lookup"><span data-stu-id="528e9-164">LangVersion</span></span>

<span data-ttu-id="528e9-165">`LangVersion`Özelliği, belirli bir programlama dili sürümü belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="528e9-165">The `LangVersion` property lets you specify a specific programming language version.</span></span> <span data-ttu-id="528e9-166">Örneğin, C# önizleme özelliklerine erişmek istiyorsanız, `LangVersion` olarak ayarlayın `preview` .</span><span class="sxs-lookup"><span data-stu-id="528e9-166">For example, if you want access to C# preview features, set `LangVersion` to `preview`.</span></span>

```xml
<PropertyGroup>
  <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="528e9-167">Daha fazla bilgi için bkz. [C# dil sürümü oluşturma](../../csharp/language-reference/configure-language-version.md#override-a-default).</span><span class="sxs-lookup"><span data-stu-id="528e9-167">For more information, see [C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).</span></span>

## <a name="code-analysis-properties"></a><span data-ttu-id="528e9-168">Kod Analizi özellikleri</span><span class="sxs-lookup"><span data-stu-id="528e9-168">Code analysis properties</span></span>

### <a name="analysislevel"></a><span data-ttu-id="528e9-169">AnalysisLevel</span><span class="sxs-lookup"><span data-stu-id="528e9-169">AnalysisLevel</span></span>

<span data-ttu-id="528e9-170">`AnalysisLevel`Özelliği, bir kod analizi düzeyi belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="528e9-170">The `AnalysisLevel` property lets you specify a code analysis level.</span></span> <span data-ttu-id="528e9-171">Örneğin, önizleme kodu Çözümleyicileri için erişim istiyorsanız, `AnalysisLevel` olarak ayarlayın `preview` .</span><span class="sxs-lookup"><span data-stu-id="528e9-171">For example, if you want access to preview code analyzers, set `AnalysisLevel` to `preview`.</span></span> <span data-ttu-id="528e9-172">Varsayılan değer: `latest`.</span><span class="sxs-lookup"><span data-stu-id="528e9-172">The default value is `latest`.</span></span>

```xml
<PropertyGroup>
  <AnalysisLevel>preview</AnalysisLevel>
</PropertyGroup>
```

<span data-ttu-id="528e9-173">Aşağıdaki tabloda kullanılabilir seçenekler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="528e9-173">The following table shows the available options.</span></span>

| <span data-ttu-id="528e9-174">Değer</span><span class="sxs-lookup"><span data-stu-id="528e9-174">Value</span></span> | <span data-ttu-id="528e9-175">Anlamı</span><span class="sxs-lookup"><span data-stu-id="528e9-175">Meaning</span></span> |
|-|-|
| `latest` | <span data-ttu-id="528e9-176">Yayınlanan en son kod Çözümleyicileri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="528e9-176">The latest code analyzers that have been released are used.</span></span> <span data-ttu-id="528e9-177">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="528e9-177">This is the default.</span></span> |
| `preview` | <span data-ttu-id="528e9-178">Önizleme aşamasında olsalar dahi, en son kod Çözümleyicileri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="528e9-178">The latest code analyzers are used, even if they are in preview.</span></span> |
| `5.0` | <span data-ttu-id="528e9-179">.NET 5,0 sürümü için etkinleştirilen kurallar kümesi, daha yeni kurallar kullanılabilir olsa bile kullanılır.</span><span class="sxs-lookup"><span data-stu-id="528e9-179">The set of rules that was enabled for the .NET 5.0 release is used, even if newer rules are available.</span></span> |
| `5` | <span data-ttu-id="528e9-180">.NET 5,0 sürümü için etkinleştirilen kurallar kümesi, daha yeni kurallar kullanılabilir olsa bile kullanılır.</span><span class="sxs-lookup"><span data-stu-id="528e9-180">The set of rules that was enabled for the .NET 5.0 release is used, even if newer rules are available.</span></span> |

### <a name="analysismode"></a><span data-ttu-id="528e9-181">AnalysisMode</span><span class="sxs-lookup"><span data-stu-id="528e9-181">AnalysisMode</span></span>

<span data-ttu-id="528e9-182">.NET SDK, .NET 5,0 RC2 'den başlayarak ["CA" kod kalitesi kurallarıyla](../../fundamentals/code-analysis/rules/quality-rules-reference.md)birlikte gönderilir.</span><span class="sxs-lookup"><span data-stu-id="528e9-182">Starting with .NET 5.0 RC2, the .NET SDK ships with all of the ["CA" code quality rules](../../fundamentals/code-analysis/rules/quality-rules-reference.md).</span></span> <span data-ttu-id="528e9-183">Varsayılan olarak, yalnızca [bazı kurallar](../../fundamentals/code-analysis/overview.md#enabled-rules) derleme uyarıları olarak etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="528e9-183">By default, only [some rules are enabled](../../fundamentals/code-analysis/overview.md#enabled-rules) as build warnings.</span></span> <span data-ttu-id="528e9-184">`AnalysisMode`Özelliği, varsayılan olarak etkinleştirilen kuralların kümesini özelleştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="528e9-184">The `AnalysisMode` property lets you customize the set of rules that are enabled by default.</span></span> <span data-ttu-id="528e9-185">Daha Agresif (geri çevirme) çözümleme moduna veya daha koruyucu (katılım) analiz moduna geçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="528e9-185">You can either switch to a more aggressive (opt-out) analysis mode or a more conservative (opt-in) analysis mode.</span></span> <span data-ttu-id="528e9-186">Örneğin, varsayılan olarak tüm kuralları derleme uyarıları olarak etkinleştirmek istiyorsanız, değerini olarak ayarlayın `AllEnabledByDefault` .</span><span class="sxs-lookup"><span data-stu-id="528e9-186">For example, if you want to enable all rules by default as build warnings, set the value to `AllEnabledByDefault`.</span></span>

```xml
<PropertyGroup>
  <AnalysisMode>AllEnabledByDefault</AnalysisMode>
</PropertyGroup>
```

<span data-ttu-id="528e9-187">Aşağıdaki tabloda kullanılabilir seçenekler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="528e9-187">The following table shows the available options.</span></span>

| <span data-ttu-id="528e9-188">Değer</span><span class="sxs-lookup"><span data-stu-id="528e9-188">Value</span></span> | <span data-ttu-id="528e9-189">Anlamı</span><span class="sxs-lookup"><span data-stu-id="528e9-189">Meaning</span></span> |
|-|-|
| `Default` | <span data-ttu-id="528e9-190">Belirli kuralların derleme uyarıları olarak etkinleştirildiği varsayılan mod, Visual Studio IDE önerisi olarak bazı kurallar etkinleştirilir ve geri kalanı devre dışı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="528e9-190">Default mode, where certain rules are enabled as build warnings, certain rules are enabled as Visual Studio IDE suggestions, and the remainder are disabled.</span></span> |
| `AllEnabledByDefault` | <span data-ttu-id="528e9-191">Tüm kuralların, derleme uyarıları olarak varsayılan olarak etkinleştirildiği agresif veya kabul etme modu.</span><span class="sxs-lookup"><span data-stu-id="528e9-191">Aggressive or opt-out mode, where all rules are enabled by default as build warnings.</span></span> <span data-ttu-id="528e9-192">Bağımsız kuralların devre dışı [bırakılacağını seçerek devre dışı bırakabilirsiniz](../../fundamentals/code-analysis/configuration-options.md) .</span><span class="sxs-lookup"><span data-stu-id="528e9-192">You can selectively [opt out](../../fundamentals/code-analysis/configuration-options.md) of individual rules to disable them.</span></span> |
| `AllDisabledByDefault` | <span data-ttu-id="528e9-193">Klasik veya kabul etme modu, tüm kurallar varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="528e9-193">Conservative or opt-in mode, where all rules are disabled by default.</span></span> <span data-ttu-id="528e9-194">Bunları etkinleştirmek için tek tek kuralların seçmeli olarak [tercih](../../fundamentals/code-analysis/configuration-options.md) edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="528e9-194">You can selectively [opt into](../../fundamentals/code-analysis/configuration-options.md) individual rules to enable them.</span></span> |

### <a name="codeanalysistreatwarningsaserrors"></a><span data-ttu-id="528e9-195">CodeAnalysisTreatWarningsAsErrors</span><span class="sxs-lookup"><span data-stu-id="528e9-195">CodeAnalysisTreatWarningsAsErrors</span></span>

<span data-ttu-id="528e9-196">`CodeAnalysisTreatWarningsAsErrors`Özelliği, kod kalitesi analizi uyarılarının (CAxxxx) uyarı olarak değerlendirilip derlenmeyeceğini yapılandırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="528e9-196">The `CodeAnalysisTreatWarningsAsErrors` property lets you configure whether code quality analysis warnings (CAxxxx) should be treated as warnings and break the build.</span></span> <span data-ttu-id="528e9-197">Projelerinizi oluştururken bayrağını kullanırsanız `-warnaserror` , [.net Code Quality Analysis](../../fundamentals/code-analysis/overview.md#code-quality-analysis) uyarıları da hata olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="528e9-197">If you use the `-warnaserror` flag when you build your projects, [.NET code quality analysis](../../fundamentals/code-analysis/overview.md#code-quality-analysis) warnings are also treated as errors.</span></span> <span data-ttu-id="528e9-198">Kod kalitesi analiz uyarılarını hata olarak kabul etmek istemiyorsanız, `CodeAnalysisTreatWarningsAsErrors` MSBuild özelliğini `false` proje dosyanızda olarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="528e9-198">If you do not want code quality analysis warnings to be treated as errors, you can set the `CodeAnalysisTreatWarningsAsErrors` MSBuild property to `false` in your project file.</span></span>

```xml
<PropertyGroup>
  <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
</PropertyGroup>
```

### <a name="enablenetanalyzers"></a><span data-ttu-id="528e9-199">Enablenetçözümleyiciler</span><span class="sxs-lookup"><span data-stu-id="528e9-199">EnableNETAnalyzers</span></span>

<span data-ttu-id="528e9-200">.Net [Code Quality Analysis](../../fundamentals/code-analysis/overview.md#code-quality-analysis) , .NET 5,0 veya üstünü hedefleyen projeler için varsayılan olarak etkinleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="528e9-200">[.NET code quality analysis](../../fundamentals/code-analysis/overview.md#code-quality-analysis) is enabled, by default, for projects that target .NET 5.0 or later.</span></span> <span data-ttu-id="528e9-201">Özelliğini olarak ayarlayarak .NET 'in önceki sürümlerini hedefleyen projeler için .NET kod analizini etkinleştirebilirsiniz `EnableNETAnalyzers` `true` .</span><span class="sxs-lookup"><span data-stu-id="528e9-201">You can enable .NET code analysis for projects that target earlier versions of .NET by setting the `EnableNETAnalyzers` property to `true`.</span></span> <span data-ttu-id="528e9-202">Herhangi bir projede kod analizini devre dışı bırakmak için bu özelliği olarak ayarlayın `false` .</span><span class="sxs-lookup"><span data-stu-id="528e9-202">To disable code analysis in any project, set this property to `false`.</span></span>

```xml
<PropertyGroup>
  <EnableNETAnalyzers>true</EnableNETAnalyzers>
</PropertyGroup>
```

> [!TIP]
> <span data-ttu-id="528e9-203">.NET 5,0 ' den önceki .NET sürümlerini hedefleyen projelerde .NET kod analizini etkinleştirmenin bir diğer yolu, [Analysislevel](#analysislevel) özelliğini olarak ayarlamadır `latest` .</span><span class="sxs-lookup"><span data-stu-id="528e9-203">Another way to enable .NET code analysis on projects that target .NET versions prior to .NET 5.0 is to set the [AnalysisLevel](#analysislevel) property to `latest`.</span></span>

### <a name="enforcecodestyleinbuild"></a><span data-ttu-id="528e9-204">Enforcecodestyleınbuild</span><span class="sxs-lookup"><span data-stu-id="528e9-204">EnforceCodeStyleInBuild</span></span>

<span data-ttu-id="528e9-205">[.NET kod stili Analizi](../../fundamentals/code-analysis/overview.md#code-style-analysis) , varsayılan olarak tüm .NET projeleri için derleme üzerinde devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="528e9-205">[.NET code style analysis](../../fundamentals/code-analysis/overview.md#code-style-analysis) is disabled, by default, on build for all .NET projects.</span></span> <span data-ttu-id="528e9-206">Özelliğini olarak ayarlayarak .NET projeleri için kod stili analizini etkinleştirebilirsiniz `EnforceCodeStyleInBuild` `true` .</span><span class="sxs-lookup"><span data-stu-id="528e9-206">You can enable code style analysis for .NET projects by setting the `EnforceCodeStyleInBuild` property to `true`.</span></span>

```xml
<PropertyGroup>
  <EnforceCodeStyleInBuild>true</EnforceCodeStyleInBuild>
</PropertyGroup>
```

<span data-ttu-id="528e9-207">Uyarı veya hata olarak [yapılandırılan](../../fundamentals/code-analysis/overview.md#code-style-analysis) tüm kod stili kuralları, derleme ve rapor ihlalleri üzerinde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="528e9-207">All code style rules that are [configured](../../fundamentals/code-analysis/overview.md#code-style-analysis) to be warnings or errors will execute on build and report violations.</span></span>

## <a name="run-time-configuration-properties"></a><span data-ttu-id="528e9-208">Çalışma zamanı yapılandırma özellikleri</span><span class="sxs-lookup"><span data-stu-id="528e9-208">Run-time configuration properties</span></span>

<span data-ttu-id="528e9-209">Uygulamanın proje dosyasında MSBuild özelliklerini belirterek bazı çalışma zamanı davranışları yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="528e9-209">You can configure some run-time behaviors by specifying MSBuild properties in the project file of the app.</span></span> <span data-ttu-id="528e9-210">Çalışma zamanı davranışını yapılandırmanın diğer yolları hakkında daha fazla bilgi için bkz. [çalışma zamanı yapılandırma ayarları](../run-time-config/index.md).</span><span class="sxs-lookup"><span data-stu-id="528e9-210">For information about other ways of configuring run-time behavior, see [Run-time configuration settings](../run-time-config/index.md).</span></span>

- [<span data-ttu-id="528e9-211">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="528e9-211">ConcurrentGarbageCollection</span></span>](#concurrentgarbagecollection)
- [<span data-ttu-id="528e9-212">Invariantgenelleştirme</span><span class="sxs-lookup"><span data-stu-id="528e9-212">InvariantGlobalization</span></span>](#invariantglobalization)
- [<span data-ttu-id="528e9-213">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="528e9-213">RetainVMGarbageCollection</span></span>](#retainvmgarbagecollection)
- [<span data-ttu-id="528e9-214">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="528e9-214">ServerGarbageCollection</span></span>](#servergarbagecollection)
- [<span data-ttu-id="528e9-215">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="528e9-215">ThreadPoolMaxThreads</span></span>](#threadpoolmaxthreads)
- [<span data-ttu-id="528e9-216">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="528e9-216">ThreadPoolMinThreads</span></span>](#threadpoolminthreads)
- [<span data-ttu-id="528e9-217">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="528e9-217">TieredCompilation</span></span>](#tieredcompilation)
- [<span data-ttu-id="528e9-218">Tieredcompilationquickjıt</span><span class="sxs-lookup"><span data-stu-id="528e9-218">TieredCompilationQuickJit</span></span>](#tieredcompilationquickjit)
- [<span data-ttu-id="528e9-219">Tieredcompilationquickjıtfordöngüleri</span><span class="sxs-lookup"><span data-stu-id="528e9-219">TieredCompilationQuickJitForLoops</span></span>](#tieredcompilationquickjitforloops)

### <a name="concurrentgarbagecollection"></a><span data-ttu-id="528e9-220">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="528e9-220">ConcurrentGarbageCollection</span></span>

<span data-ttu-id="528e9-221">`ConcurrentGarbageCollection`Özelliği [Background (eşzamanlı) Çöp toplamanın](../../standard/garbage-collection/background-gc.md) etkinleştirilip etkinleştirilmeyeceğini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="528e9-221">The `ConcurrentGarbageCollection` property configures whether [background (concurrent) garbage collection](../../standard/garbage-collection/background-gc.md) is enabled.</span></span> <span data-ttu-id="528e9-222">`false`Arka plan atık toplamayı devre dışı bırakmak için değerini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="528e9-222">Set the value to `false` to disable background garbage collection.</span></span> <span data-ttu-id="528e9-223">Daha fazla bilgi için bkz. [arka plan GC](../run-time-config/garbage-collector.md#background-gc).</span><span class="sxs-lookup"><span data-stu-id="528e9-223">For more information, see [Background GC](../run-time-config/garbage-collector.md#background-gc).</span></span>

```xml
<PropertyGroup>
  <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
</PropertyGroup>
```

### <a name="invariantglobalization"></a><span data-ttu-id="528e9-224">Invariantgenelleştirme</span><span class="sxs-lookup"><span data-stu-id="528e9-224">InvariantGlobalization</span></span>

<span data-ttu-id="528e9-225">`InvariantGlobalization`Özelliği, uygulamanın *Genelleştirme sabit* modunda çalışıp çalışmadığını yapılandırır, bu, kültüre özgü verilere erişimi olmayan anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="528e9-225">The `InvariantGlobalization` property configures whether the app runs in *globalization-invariant* mode, which means it doesn't have access to culture-specific data.</span></span> <span data-ttu-id="528e9-226">Değeri `true` Genelleştirme sabit modunda çalışacak şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="528e9-226">Set the value to `true` to run in globalization-invariant mode.</span></span> <span data-ttu-id="528e9-227">Daha fazla bilgi için bkz. [sabit mod](../run-time-config/globalization.md#invariant-mode).</span><span class="sxs-lookup"><span data-stu-id="528e9-227">For more information, see [Invariant mode](../run-time-config/globalization.md#invariant-mode).</span></span>

```xml
<PropertyGroup>
  <InvariantGlobalization>true</InvariantGlobalization>
</PropertyGroup>
```

### <a name="retainvmgarbagecollection"></a><span data-ttu-id="528e9-228">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="528e9-228">RetainVMGarbageCollection</span></span>

<span data-ttu-id="528e9-229">`RetainVMGarbageCollection`Özelliği, çöp toplayıcıyı, daha sonra kullanılmak üzere veya serbest bırakmak için silinen bellek segmentlerini bir bekleme listesine koymak üzere yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="528e9-229">The `RetainVMGarbageCollection` property configures the garbage collector to put deleted memory segments on a standby list for future use or release them.</span></span> <span data-ttu-id="528e9-230">Değeri, `true` çöp toplayıcıya kesimleri bir bekleme listesine koymasını söyler.</span><span class="sxs-lookup"><span data-stu-id="528e9-230">Setting the value to `true` tells the garbage collector to put the segments on a standby list.</span></span> <span data-ttu-id="528e9-231">Daha fazla bilgi için bkz. [VM 'Yi koruma](../run-time-config/garbage-collector.md#retain-vm).</span><span class="sxs-lookup"><span data-stu-id="528e9-231">For more information, see [Retain VM](../run-time-config/garbage-collector.md#retain-vm).</span></span>

```xml
<PropertyGroup>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
</PropertyGroup>
```

### <a name="servergarbagecollection"></a><span data-ttu-id="528e9-232">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="528e9-232">ServerGarbageCollection</span></span>

<span data-ttu-id="528e9-233">`ServerGarbageCollection`Özelliği, uygulamanın [iş istasyonu çöp toplamayı veya sunucu çöp toplamayı](../../standard/garbage-collection/workstation-server-gc.md)kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="528e9-233">The `ServerGarbageCollection` property configures whether the application uses [workstation garbage collection or server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span> <span data-ttu-id="528e9-234">Değerini `true` sunucu çöp toplamayı kullanacak şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="528e9-234">Set the value to `true` to use server garbage collection.</span></span> <span data-ttu-id="528e9-235">Daha fazla bilgi için bkz. [Workstation vs Server](../run-time-config/garbage-collector.md#workstation-vs-server).</span><span class="sxs-lookup"><span data-stu-id="528e9-235">For more information, see [Workstation vs. server](../run-time-config/garbage-collector.md#workstation-vs-server).</span></span>

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

### <a name="threadpoolmaxthreads"></a><span data-ttu-id="528e9-236">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="528e9-236">ThreadPoolMaxThreads</span></span>

<span data-ttu-id="528e9-237">`ThreadPoolMaxThreads`Özelliği, çalışan iş parçacığı havuzu için en fazla iş parçacığı sayısını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="528e9-237">The `ThreadPoolMaxThreads` property configures the maximum number of threads for the worker thread pool.</span></span> <span data-ttu-id="528e9-238">Daha fazla bilgi için bkz. [en fazla iş parçacığı](../run-time-config/threading.md#maximum-threads).</span><span class="sxs-lookup"><span data-stu-id="528e9-238">For more information, see [Maximum threads](../run-time-config/threading.md#maximum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
</PropertyGroup>
```

### <a name="threadpoolminthreads"></a><span data-ttu-id="528e9-239">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="528e9-239">ThreadPoolMinThreads</span></span>

<span data-ttu-id="528e9-240">`ThreadPoolMinThreads`Özelliği, çalışan iş parçacığı havuzu için en az iş parçacığı sayısını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="528e9-240">The `ThreadPoolMinThreads` property configures the minimum number of threads for the worker thread pool.</span></span> <span data-ttu-id="528e9-241">Daha fazla bilgi için bkz. [En düşük iş parçacıkları](../run-time-config/threading.md#minimum-threads).</span><span class="sxs-lookup"><span data-stu-id="528e9-241">For more information, see [Minimum threads](../run-time-config/threading.md#minimum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
</PropertyGroup>
```

### <a name="tieredcompilation"></a><span data-ttu-id="528e9-242">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="528e9-242">TieredCompilation</span></span>

<span data-ttu-id="528e9-243">`TieredCompilation`Özelliği, Just-In-Time (JIT) derleyicisinin [katmanlı derlemeyi](../whats-new/dotnet-core-3-0.md#tiered-compilation)kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="528e9-243">The `TieredCompilation` property configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="528e9-244">`false`Katmanlı derlemeyi devre dışı bırakmak için değerini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="528e9-244">Set the value to `false` to disable tiered compilation.</span></span> <span data-ttu-id="528e9-245">Daha fazla bilgi için bkz. [katmanlı derleme](../run-time-config/compilation.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="528e9-245">For more information, see [Tiered compilation](../run-time-config/compilation.md#tiered-compilation).</span></span>

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

### <a name="tieredcompilationquickjit"></a><span data-ttu-id="528e9-246">Tieredcompilationquickjıt</span><span class="sxs-lookup"><span data-stu-id="528e9-246">TieredCompilationQuickJit</span></span>

<span data-ttu-id="528e9-247">`TieredCompilationQuickJit`Özelliği, JIT derleyicisinin hızlı JIT kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="528e9-247">The `TieredCompilationQuickJit` property configures whether the JIT compiler uses quick JIT.</span></span> <span data-ttu-id="528e9-248">`false`Hızlı JIT 'i devre dışı bırakmak için değerini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="528e9-248">Set the value to `false` to disable quick JIT.</span></span> <span data-ttu-id="528e9-249">Daha fazla bilgi için bkz. [hızlı JIT](../run-time-config/compilation.md#quick-jit).</span><span class="sxs-lookup"><span data-stu-id="528e9-249">For more information, see [Quick JIT](../run-time-config/compilation.md#quick-jit).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

### <a name="tieredcompilationquickjitforloops"></a><span data-ttu-id="528e9-250">Tieredcompilationquickjıtfordöngüleri</span><span class="sxs-lookup"><span data-stu-id="528e9-250">TieredCompilationQuickJitForLoops</span></span>

<span data-ttu-id="528e9-251">`TieredCompilationQuickJitForLoops`Özelliği, JIT derleyicisinin döngüleri içeren yöntemlerde hızlı JIT kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="528e9-251">The `TieredCompilationQuickJitForLoops` property configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span> <span data-ttu-id="528e9-252">`true`Döngüleri içeren yöntemlerde hızlı JIT 'i etkinleştirmek için değerini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="528e9-252">Set the value to `true` to enable quick JIT on methods that contain loops.</span></span> <span data-ttu-id="528e9-253">Daha fazla bilgi için bkz. [döngüler Için hızlı JIT](../run-time-config/compilation.md#quick-jit-for-loops).</span><span class="sxs-lookup"><span data-stu-id="528e9-253">For more information, see [Quick JIT for loops](../run-time-config/compilation.md#quick-jit-for-loops).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
</PropertyGroup>
```

## <a name="reference-properties-and-items"></a><span data-ttu-id="528e9-254">Başvuru özellikleri ve öğeleri</span><span class="sxs-lookup"><span data-stu-id="528e9-254">Reference properties and items</span></span>

- [<span data-ttu-id="528e9-255">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="528e9-255">AssetTargetFallback</span></span>](#assettargetfallback)
- [<span data-ttu-id="528e9-256">PackageReference</span><span class="sxs-lookup"><span data-stu-id="528e9-256">PackageReference</span></span>](#packagereference)
- [<span data-ttu-id="528e9-257">ProjectReference</span><span class="sxs-lookup"><span data-stu-id="528e9-257">ProjectReference</span></span>](#projectreference)
- [<span data-ttu-id="528e9-258">Başvuru</span><span class="sxs-lookup"><span data-stu-id="528e9-258">Reference</span></span>](#reference)
- [<span data-ttu-id="528e9-259">Özellikleri geri yükle</span><span class="sxs-lookup"><span data-stu-id="528e9-259">Restore properties</span></span>](#restore-properties)

### <a name="assettargetfallback"></a><span data-ttu-id="528e9-260">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="528e9-260">AssetTargetFallback</span></span>

<span data-ttu-id="528e9-261">`AssetTargetFallback`Özelliği, proje başvuruları ve NuGet paketleri için ek uyumlu çerçeve sürümlerini belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="528e9-261">The `AssetTargetFallback` property lets you specify additional compatible framework versions for project references and NuGet packages.</span></span> <span data-ttu-id="528e9-262">Örneğin, kullanarak bir paket bağımlılığı belirtirseniz `PackageReference` ancak bu paket, projelerinizle uyumlu olan varlıkları içermiyorsa `TargetFramework` , `AssetTargetFallback` özelliği yürütmeye gelir.</span><span class="sxs-lookup"><span data-stu-id="528e9-262">For example, if you specify a package dependency using `PackageReference` but that package doesn't contain assets that are compatible with your projects's `TargetFramework`, the `AssetTargetFallback` property comes into play.</span></span> <span data-ttu-id="528e9-263">Başvurulan paketin uyumluluğu, içinde belirtilen her bir hedef çerçeve kullanılarak yeniden denetlenir `AssetTargetFallback` .</span><span class="sxs-lookup"><span data-stu-id="528e9-263">The compatibility of the referenced package is rechecked using each target framework that's specified in `AssetTargetFallback`.</span></span>

<span data-ttu-id="528e9-264">`AssetTargetFallback`Özelliğini bir veya daha fazla [hedef çerçeve sürümüne](../../standard/frameworks.md#supported-target-frameworks)ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="528e9-264">You can set the `AssetTargetFallback` property to one or more [target framework versions](../../standard/frameworks.md#supported-target-frameworks).</span></span>

```xml
<PropertyGroup>
  <AssetTargetFallback>net461</AssetTargetFallback>
</PropertyGroup>
```

### <a name="packagereference"></a><span data-ttu-id="528e9-265">PackageReference</span><span class="sxs-lookup"><span data-stu-id="528e9-265">PackageReference</span></span>

<span data-ttu-id="528e9-266">`PackageReference`Öğe, bir NuGet paketine bir başvuru tanımlar.</span><span class="sxs-lookup"><span data-stu-id="528e9-266">The `PackageReference` item defines a reference to a NuGet package.</span></span>

<span data-ttu-id="528e9-267">`Include`Öznitelik, paket kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="528e9-267">The `Include` attribute specifies the package ID.</span></span> <span data-ttu-id="528e9-268">`Version`Öznitelik, sürümü veya sürüm aralığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="528e9-268">The `Version` attribute specifies the version or version range.</span></span> <span data-ttu-id="528e9-269">En düşük sürüm, en yüksek sürüm, Aralık veya tam eşleşme belirtme hakkında bilgi için bkz. [Sürüm aralıkları](/nuget/concepts/package-versioning#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="528e9-269">For information about how to specify a minimum version, maximum version, range, or exact match, see [Version ranges](/nuget/concepts/package-versioning#version-ranges).</span></span> <span data-ttu-id="528e9-270">Aşağıdaki meta verileri bir proje başvurusuna de ekleyebilirsiniz: `IncludeAssets` , `ExcludeAssets` , ve `PrivateAssets` .</span><span class="sxs-lookup"><span data-stu-id="528e9-270">You can also add the following metadata to a project reference: `IncludeAssets`, `ExcludeAssets`, and `PrivateAssets`.</span></span>

<span data-ttu-id="528e9-271">Aşağıdaki örnekteki proje dosyası kod parçacığı [System. Runtime](https://www.nuget.org/packages/System.Runtime/) paketine başvurur.</span><span class="sxs-lookup"><span data-stu-id="528e9-271">The project file snippet in the following example references the [System.Runtime](https://www.nuget.org/packages/System.Runtime/) package.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="System.Runtime" Version="4.3.0" />
</ItemGroup>
```

<span data-ttu-id="528e9-272">Daha fazla bilgi için bkz. [Proje dosyalarındaki paket başvuruları](/nuget/consume-packages/package-references-in-project-files).</span><span class="sxs-lookup"><span data-stu-id="528e9-272">For more information, see [Package references in project files](/nuget/consume-packages/package-references-in-project-files).</span></span>

### <a name="projectreference"></a><span data-ttu-id="528e9-273">ProjectReference</span><span class="sxs-lookup"><span data-stu-id="528e9-273">ProjectReference</span></span>

<span data-ttu-id="528e9-274">`ProjectReference`Öğe, başka bir projeye yönelik bir başvuru tanımlar.</span><span class="sxs-lookup"><span data-stu-id="528e9-274">The `ProjectReference` item defines a reference to another project.</span></span> <span data-ttu-id="528e9-275">Başvurulan proje bir NuGet paket bağımlılığı olarak eklenir, diğer bir deyişle, ile aynı şekilde işlenir `PackageReference` .</span><span class="sxs-lookup"><span data-stu-id="528e9-275">The referenced project is added as a NuGet package dependency, that is, it's treated the same as a `PackageReference`.</span></span>

<span data-ttu-id="528e9-276">`Include`Öznitelik, projenin yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="528e9-276">The `Include` attribute specifies the path to the project.</span></span> <span data-ttu-id="528e9-277">Aşağıdaki meta verileri bir proje başvurusuna de ekleyebilirsiniz: `IncludeAssets` , `ExcludeAssets` , ve `PrivateAssets` .</span><span class="sxs-lookup"><span data-stu-id="528e9-277">You can also add the following metadata to a project reference: `IncludeAssets`, `ExcludeAssets`, and `PrivateAssets`.</span></span>

<span data-ttu-id="528e9-278">Aşağıdaki örnekteki proje dosyası kod parçacığı adlı bir projeye başvurur `Project2` .</span><span class="sxs-lookup"><span data-stu-id="528e9-278">The project file snippet in the following example references a project named `Project2`.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\Project2.csproj" />
</ItemGroup>
```

### <a name="reference"></a><span data-ttu-id="528e9-279">Başvuru</span><span class="sxs-lookup"><span data-stu-id="528e9-279">Reference</span></span>

<span data-ttu-id="528e9-280">`Reference`Öğe, derleme dosyasına bir başvuru tanımlar.</span><span class="sxs-lookup"><span data-stu-id="528e9-280">The `Reference` item defines a reference to an assembly file.</span></span>

<span data-ttu-id="528e9-281">`Include`Öznitelik, dosyanın adını belirtir ve `HintPath` meta veriler derlemenin yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="528e9-281">The `Include` attribute specifies the name of the file, and the `HintPath` metadata specifies the path to the assembly.</span></span>

```xml
<ItemGroup>
  <Reference Include="MyAssembly">
    <HintPath>..\..\Assemblies\MyAssembly.dll</HintPath>
  </Reference>
</ItemGroup>
```

### <a name="restore-properties"></a><span data-ttu-id="528e9-282">Özellikleri geri yükle</span><span class="sxs-lookup"><span data-stu-id="528e9-282">Restore properties</span></span>

<span data-ttu-id="528e9-283">Başvurulan bir paketin geri yüklenmesi, tüm doğrudan bağımlılıklarını ve bu bağımlılıkların tüm bağımlılıklarını yükler.</span><span class="sxs-lookup"><span data-stu-id="528e9-283">Restoring a referenced package installs all of its direct dependencies and all the dependencies of those dependencies.</span></span> <span data-ttu-id="528e9-284">Ve gibi özellikler belirterek paket geri yüklemesini özelleştirebilirsiniz `RestorePackagesPath` `RestoreIgnoreFailedSources` .</span><span class="sxs-lookup"><span data-stu-id="528e9-284">You can customize package restoration by specifying properties such as `RestorePackagesPath` and `RestoreIgnoreFailedSources`.</span></span> <span data-ttu-id="528e9-285">Bu ve diğer özellikler hakkında daha fazla bilgi için bkz. [hedefi geri yükleme](/nuget/reference/msbuild-targets#restore-target).</span><span class="sxs-lookup"><span data-stu-id="528e9-285">For more information about these and other properties, see [restore target](/nuget/reference/msbuild-targets#restore-target).</span></span>

```xml
<PropertyGroup>
  <RestoreIgnoreFailedSource>true</RestoreIgnoreFailedSource>
</PropertyGroup>
```

## <a name="see-also"></a><span data-ttu-id="528e9-286">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="528e9-286">See also</span></span>

- [<span data-ttu-id="528e9-287">MSBuild şema başvurusu</span><span class="sxs-lookup"><span data-stu-id="528e9-287">MSBuild schema reference</span></span>](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [<span data-ttu-id="528e9-288">Ortak MSBuild özellikleri</span><span class="sxs-lookup"><span data-stu-id="528e9-288">Common MSBuild properties</span></span>](/visualstudio/msbuild/common-msbuild-project-properties)
- [<span data-ttu-id="528e9-289">NuGet paketi için MSBuild özellikleri</span><span class="sxs-lookup"><span data-stu-id="528e9-289">MSBuild properties for NuGet pack</span></span>](/nuget/reference/msbuild-targets#pack-target)
- [<span data-ttu-id="528e9-290">NuGet geri yükleme için MSBuild özellikleri</span><span class="sxs-lookup"><span data-stu-id="528e9-290">MSBuild properties for NuGet restore</span></span>](/nuget/reference/msbuild-targets#restore-properties)
- [<span data-ttu-id="528e9-291">Bir derlemeyi özelleştirme</span><span class="sxs-lookup"><span data-stu-id="528e9-291">Customize a build</span></span>](/visualstudio/msbuild/customize-your-build)
