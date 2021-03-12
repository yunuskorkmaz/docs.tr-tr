---
title: Microsoft. NET. SDK için MSBuild özellikleri
description: MSBuild özellikleri ve .NET SDK tarafından anlaşılan öğeler için başvuru.
ms.date: 02/14/2020
ms.topic: reference
ms.custom: updateeachrelease
ms.openlocfilehash: 18f2be734fa10e2fd4977166ab4334332b120a91
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/10/2021
ms.locfileid: "102604768"
---
# <a name="msbuild-reference-for-net-sdk-projects"></a><span data-ttu-id="d2b6e-103">.NET SDK projeleri için MSBuild başvurusu</span><span class="sxs-lookup"><span data-stu-id="d2b6e-103">MSBuild reference for .NET SDK projects</span></span>

<span data-ttu-id="d2b6e-104">Bu sayfa, MSBuild özelliklerine ve .NET projelerini yapılandırmak için kullanabileceğiniz öğelere yönelik bir başvurudur.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-104">This page is a reference for the MSBuild properties and items that you can use to configure .NET projects.</span></span>

> [!NOTE]
> <span data-ttu-id="d2b6e-105">Bu sayfa devam eden bir çalışmadır ve .NET SDK için tüm kullanışlı MSBuild özelliklerini listelemez.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-105">This page is a work in progress and does not list all of the useful MSBuild properties for the .NET SDK.</span></span> <span data-ttu-id="d2b6e-106">Ortak MSBuild özelliklerinin bir listesi için bkz. [Ortak MSBuild özellikleri](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="d2b6e-106">For a list of common MSBuild properties, see [Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="framework-properties"></a><span data-ttu-id="d2b6e-107">Çerçeve özellikleri</span><span class="sxs-lookup"><span data-stu-id="d2b6e-107">Framework properties</span></span>

- [<span data-ttu-id="d2b6e-108">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="d2b6e-108">TargetFramework</span></span>](#targetframework)
- [<span data-ttu-id="d2b6e-109">Targetçerçeveler</span><span class="sxs-lookup"><span data-stu-id="d2b6e-109">TargetFrameworks</span></span>](#targetframeworks)
- [<span data-ttu-id="d2b6e-110">Netstandardımplicitpackageversion</span><span class="sxs-lookup"><span data-stu-id="d2b6e-110">NetStandardImplicitPackageVersion</span></span>](#netstandardimplicitpackageversion)

### <a name="targetframework"></a><span data-ttu-id="d2b6e-111">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="d2b6e-111">TargetFramework</span></span>

<span data-ttu-id="d2b6e-112">`TargetFramework`Özelliği, uygulamanın hedef Framework sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-112">The `TargetFramework` property specifies the target framework version for the app.</span></span> <span data-ttu-id="d2b6e-113">Geçerli hedef çerçeve takma adların listesi için bkz. [SDK stili projelerde hedef çerçeveler](../../standard/frameworks.md#supported-target-frameworks).</span><span class="sxs-lookup"><span data-stu-id="d2b6e-113">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-frameworks).</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>
```

<span data-ttu-id="d2b6e-114">Daha fazla bilgi için bkz. [SDK stili projelerde hedef çerçeveler](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="d2b6e-114">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="targetframeworks"></a><span data-ttu-id="d2b6e-115">Targetçerçeveler</span><span class="sxs-lookup"><span data-stu-id="d2b6e-115">TargetFrameworks</span></span>

<span data-ttu-id="d2b6e-116">`TargetFrameworks`Uygulamanızın birden çok platformu hedeflemesini istediğinizde özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-116">Use the `TargetFrameworks` property when you want your app to target multiple platforms.</span></span> <span data-ttu-id="d2b6e-117">Geçerli hedef çerçeve takma adların listesi için bkz. [SDK stili projelerde hedef çerçeveler](../../standard/frameworks.md#supported-target-frameworks).</span><span class="sxs-lookup"><span data-stu-id="d2b6e-117">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-frameworks).</span></span>

> [!NOTE]
> <span data-ttu-id="d2b6e-118">`TargetFramework`(Tekil) belirtilmişse bu özellik yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-118">This property is ignored if `TargetFramework` (singular) is specified.</span></span>

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
</PropertyGroup>
```

<span data-ttu-id="d2b6e-119">Daha fazla bilgi için bkz. [SDK stili projelerde hedef çerçeveler](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="d2b6e-119">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="netstandardimplicitpackageversion"></a><span data-ttu-id="d2b6e-120">Netstandardımplicitpackageversion</span><span class="sxs-lookup"><span data-stu-id="d2b6e-120">NetStandardImplicitPackageVersion</span></span>

> [!NOTE]
> <span data-ttu-id="d2b6e-121">Bu özellik yalnızca kullanan projeler için geçerlidir `netstandard1.x` .</span><span class="sxs-lookup"><span data-stu-id="d2b6e-121">This property only applies to projects using `netstandard1.x`.</span></span> <span data-ttu-id="d2b6e-122">Kullanan projeler için uygulanmaz `netstandard2.x` .</span><span class="sxs-lookup"><span data-stu-id="d2b6e-122">It doesn't apply to projects that use `netstandard2.x`.</span></span>

<span data-ttu-id="d2b6e-123">`NetStandardImplicitPackageVersion`Metapackage sürümünden daha düşük bir çerçeve sürümü belirtmek istediğinizde özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-123">Use the `NetStandardImplicitPackageVersion` property when you want to specify a framework version that's lower than the metapackage version.</span></span> <span data-ttu-id="d2b6e-124">Aşağıdaki örnekteki proje dosyası hedefler, `netstandard1.3` ancak 1.6.0 sürümünü kullanır `NETStandard.Library` .</span><span class="sxs-lookup"><span data-stu-id="d2b6e-124">The project file in the following example targets `netstandard1.3` but uses the 1.6.0 version of `NETStandard.Library`.</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netstandard1.3</TargetFramework>
  <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
</PropertyGroup>
```

## <a name="package-properties"></a><span data-ttu-id="d2b6e-125">Paket özellikleri</span><span class="sxs-lookup"><span data-stu-id="d2b6e-125">Package properties</span></span>

<span data-ttu-id="d2b6e-126">`PackageId` `PackageVersion` `PackageIcon` `Title` `Description` Projenizden oluşturulan paketi betimleyen,,, ve gibi özellikleri belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-126">You can specify properties such as `PackageId`, `PackageVersion`, `PackageIcon`, `Title`, and `Description` to describe the package that gets created from your project.</span></span> <span data-ttu-id="d2b6e-127">Bu ve diğer özellikler hakkında daha fazla bilgi için bkz. [Pack Target](/nuget/reference/msbuild-targets#pack-target).</span><span class="sxs-lookup"><span data-stu-id="d2b6e-127">For information about these and other properties, see [pack target](/nuget/reference/msbuild-targets#pack-target).</span></span>

```xml
<PropertyGroup>
  ...
  <PackageId>ClassLibDotNetStandard</PackageId>
  <Version>1.0.0</Version>
  <Authors>John Doe</Authors>
  <Company>Contoso</Company>
</PropertyGroup>
```

## <a name="publish-properties-items-and-metadata"></a><span data-ttu-id="d2b6e-128">Özellikleri, öğeleri ve meta verileri Yayımla</span><span class="sxs-lookup"><span data-stu-id="d2b6e-128">Publish properties, items, and metadata</span></span>

- [<span data-ttu-id="d2b6e-129">Appendruntimeıdentifiertooutputpath</span><span class="sxs-lookup"><span data-stu-id="d2b6e-129">AppendRuntimeIdentifierToOutputPath</span></span>](#appendruntimeidentifiertooutputpath)
- [<span data-ttu-id="d2b6e-130">AppendTargetFrameworkToOutputPath</span><span class="sxs-lookup"><span data-stu-id="d2b6e-130">AppendTargetFrameworkToOutputPath</span></span>](#appendtargetframeworktooutputpath)
- [<span data-ttu-id="d2b6e-131">CopyLocalLockFileAssemblies</span><span class="sxs-lookup"><span data-stu-id="d2b6e-131">CopyLocalLockFileAssemblies</span></span>](#copylocallockfileassemblies)
- [<span data-ttu-id="d2b6e-132">CopyToPublishDirectory</span><span class="sxs-lookup"><span data-stu-id="d2b6e-132">CopyToPublishDirectory</span></span>](#copytopublishdirectory)
- [<span data-ttu-id="d2b6e-133">Tabanlarını</span><span class="sxs-lookup"><span data-stu-id="d2b6e-133">LinkBase</span></span>](#linkbase)
- [<span data-ttu-id="d2b6e-134">PreserveCompilationContext</span><span class="sxs-lookup"><span data-stu-id="d2b6e-134">PreserveCompilationContext</span></span>](#preservecompilationcontext)
- [<span data-ttu-id="d2b6e-135">PreserveCompilationReferences</span><span class="sxs-lookup"><span data-stu-id="d2b6e-135">PreserveCompilationReferences</span></span>](#preservecompilationreferences)
- [<span data-ttu-id="d2b6e-136">Runtimeıdentifier</span><span class="sxs-lookup"><span data-stu-id="d2b6e-136">RuntimeIdentifier</span></span>](#runtimeidentifier)
- [<span data-ttu-id="d2b6e-137">Runtimetanımlayıcıtanımlayıcıları</span><span class="sxs-lookup"><span data-stu-id="d2b6e-137">RuntimeIdentifiers</span></span>](#runtimeidentifiers)
- [<span data-ttu-id="d2b6e-138">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="d2b6e-138">TrimmerRootAssembly</span></span>](#trimmerrootassembly)
- [<span data-ttu-id="d2b6e-139">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="d2b6e-139">UseAppHost</span></span>](#useapphost)

### <a name="copytopublishdirectory"></a><span data-ttu-id="d2b6e-140">CopyToPublishDirectory</span><span class="sxs-lookup"><span data-stu-id="d2b6e-140">CopyToPublishDirectory</span></span>

<span data-ttu-id="d2b6e-141">`CopyToPublishDirectory`MSBuild öğesindeki meta veriler, öğe yayımlama dizinine kopyalandığında denetler.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-141">The `CopyToPublishDirectory` metadata on an MSBuild item controls when the item is copied to the publish directory.</span></span> <span data-ttu-id="d2b6e-142">İzin verilen değerler `PreserveNewest` , yalnızca değiştirilirse öğeyi kopyalayan, `Always` her zaman öğeyi kopyalayan ve öğeyi `Never` hiçbir zaman kopyalamamış olan değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-142">Allowable values are `PreserveNewest`, which only copies the item if it has changed, `Always`, which always copies the item, and `Never`, which never copies the item.</span></span> <span data-ttu-id="d2b6e-143">Bir performans açısından, `PreserveNewest` artımlı bir derlemeyi sağladığından tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-143">From a performance standpoint, `PreserveNewest` is preferable because it enables an incremental build.</span></span>

```xml
<ItemGroup>
  <None Update="appsettings.Development.json" CopyToOutputDirectory="PreserveNewest" CopyToPublishDirectory="PreserveNewest" />
</ItemGroup>
```

### <a name="linkbase"></a><span data-ttu-id="d2b6e-144">Tabanlarını</span><span class="sxs-lookup"><span data-stu-id="d2b6e-144">LinkBase</span></span>

<span data-ttu-id="d2b6e-145">Proje dizini ve alt dizinleri dışında olan bir öğe için, Yayımla hedefi öğenin [bağlantı meta verilerini](/visualstudio/msbuild/common-msbuild-item-metadata) kullanarak öğenin nereye kopyalanacağını tespit edin.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-145">For an item that's outside of the project directory and its subdirectories, the publish target uses the item's [Link metadata](/visualstudio/msbuild/common-msbuild-item-metadata) to determine where to copy the item to.</span></span> <span data-ttu-id="d2b6e-146">`Link` Ayrıca, proje ağacının dışındaki öğelerin Visual Studio 'nun Çözüm Gezgini penceresinde nasıl görüntüleneceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-146">`Link` also determines how items outside of the project tree are displayed in the Solution Explorer window of Visual Studio.</span></span>

<span data-ttu-id="d2b6e-147">`Link`Proje konisi dışında bir öğe için belirtilmemişse, varsayılan olarak öğesine ayarlanır `%(LinkBase)\%(RecursiveDir)%(Filename)%(Extension)` .</span><span class="sxs-lookup"><span data-stu-id="d2b6e-147">If `Link` is not specified for an item that's outside of the project cone, it defaults to `%(LinkBase)\%(RecursiveDir)%(Filename)%(Extension)`.</span></span> <span data-ttu-id="d2b6e-148">`LinkBase` Proje koni dışındaki öğeler için bir senerişilebilir taban klasörü belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-148">`LinkBase` lets you specify a sensible base folder for items outside of the project cone.</span></span> <span data-ttu-id="d2b6e-149">Taban klasörü altındaki klasör hiyerarşisi aracılığıyla korunur `RecursiveDir` .</span><span class="sxs-lookup"><span data-stu-id="d2b6e-149">The folder hierarchy under the base folder is preserved via `RecursiveDir`.</span></span> <span data-ttu-id="d2b6e-150">`LinkBase`Belirtilmemişse, `Link` yolundan çıkarılır.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-150">If `LinkBase` is not specified, it's omitted from the `Link` path.</span></span>

```xml
<ItemGroup>
  <Content Include="..\Extras\**\*.cs" LinkBase="Shared"/>
</ItemGroup>
```

<span data-ttu-id="d2b6e-151">Aşağıdaki görüntüde, önceki öğe ile eklenen bir dosyanın `Include` Çözüm Gezgini ' de nasıl görüntüleyeceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-151">The following image shows how a file that's included via the previous item `Include` glob displays in Solution Explorer.</span></span>

:::image type="content" source="media/solution-explorer-linkbase.png" alt-text="Çözüm Gezgini bağlantı tabanının meta verileri içeren öğe gösteriliyor.":::

### <a name="appendtargetframeworktooutputpath"></a><span data-ttu-id="d2b6e-153">AppendTargetFrameworkToOutputPath</span><span class="sxs-lookup"><span data-stu-id="d2b6e-153">AppendTargetFrameworkToOutputPath</span></span>

<span data-ttu-id="d2b6e-154">`AppendTargetFrameworkToOutputPath`Özelliği, [hedef çerçeve adının (TFI)](../../standard/frameworks.md) çıkış yolunun ( [OutputPath](/visualstudio/msbuild/common-msbuild-project-properties#list-of-common-properties-and-parameters)tarafından tanımlanan) eklenip eklenmeyeceğini denetler.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-154">The `AppendTargetFrameworkToOutputPath` property controls whether the [target framework moniker (TFM)](../../standard/frameworks.md) is appended to the output path (which is defined by [OutputPath](/visualstudio/msbuild/common-msbuild-project-properties#list-of-common-properties-and-parameters)).</span></span> <span data-ttu-id="d2b6e-155">.NET SDK, hedef çerçeveyi otomatik olarak ekler ve varsa, çalışma zamanı tanımlayıcısını çıkış yoluna ekler.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-155">The .NET SDK automatically appends the target framework and, if present, the runtime identifier to the output path.</span></span> <span data-ttu-id="d2b6e-156">`AppendTargetFrameworkToOutputPath`İçin ayarı `false` , TFI 'nin çıkış yoluna eklenmesini engeller.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-156">Setting `AppendTargetFrameworkToOutputPath` to `false` prevents the TFM from being appended to the output path.</span></span> <span data-ttu-id="d2b6e-157">Ancak, çıkış yolunda TFı olmadan, birden çok derleme yapıtları birbirinin üzerine yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-157">However, without the TFM in the output path, multiple build artifacts may overwrite each other.</span></span>

<span data-ttu-id="d2b6e-158">Örneğin, bir .NET 5,0 uygulaması için çıkış yolu, ' dan ' ı `bin\Debug\net5.0` `bin\Debug` aşağıdaki ayarla olarak değişir:</span><span class="sxs-lookup"><span data-stu-id="d2b6e-158">For example, for a .NET 5.0 app, the output path changes from `bin\Debug\net5.0` to `bin\Debug` with the following setting:</span></span>

```xml
<PropertyGroup>
  <AppendTargetFrameworkToOutputPath>false</AppendTargetFrameworkToOutputPath>
</PropertyGroup>
```

### <a name="appendruntimeidentifiertooutputpath"></a><span data-ttu-id="d2b6e-159">Appendruntimeıdentifiertooutputpath</span><span class="sxs-lookup"><span data-stu-id="d2b6e-159">AppendRuntimeIdentifierToOutputPath</span></span>

<span data-ttu-id="d2b6e-160">`AppendRuntimeIdentifierToOutputPath`Özelliği, [çalışma zamanı TANıMLAYıCıSıNıN (RID)](../rid-catalog.md) çıkış yolunun sonuna eklenip eklenmeyeceğini denetler.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-160">The `AppendRuntimeIdentifierToOutputPath` property controls whether the [runtime identifier (RID)](../rid-catalog.md) is appended to the output path.</span></span> <span data-ttu-id="d2b6e-161">.NET SDK, hedef çerçeveyi otomatik olarak ekler ve varsa, çalışma zamanı tanımlayıcısını çıkış yoluna ekler.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-161">The .NET SDK automatically appends the target framework and, if present, the runtime identifier to the output path.</span></span> <span data-ttu-id="d2b6e-162">`AppendRuntimeIdentifierToOutputPath`İçin ayarı `false` , RID 'nin çıkış yoluna eklenmesini önler.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-162">Setting `AppendRuntimeIdentifierToOutputPath` to `false` prevents the RID from being appended to the output path.</span></span>

<span data-ttu-id="d2b6e-163">Örneğin, bir .NET 5,0 uygulaması ve bir RID 'si için `win10-x64` çıkış yolu, ' dan ' ı `bin\Debug\net5.0\win10-x64` `bin\Debug\net5.0` aşağıdaki ayarla olarak değişir:</span><span class="sxs-lookup"><span data-stu-id="d2b6e-163">For example, for a .NET 5.0 app and an RID of `win10-x64`, the output path changes from `bin\Debug\net5.0\win10-x64` to `bin\Debug\net5.0` with the following setting:</span></span>

```xml
<PropertyGroup>
  <AppendRuntimeIdentifierToOutputPath>false</AppendRuntimeIdentifierToOutputPath>
</PropertyGroup>
```

### <a name="copylocallockfileassemblies"></a><span data-ttu-id="d2b6e-164">CopyLocalLockFileAssemblies</span><span class="sxs-lookup"><span data-stu-id="d2b6e-164">CopyLocalLockFileAssemblies</span></span>

<span data-ttu-id="d2b6e-165">`CopyLocalLockFileAssemblies`Özelliği, diğer kitaplıklara bağımlılıkları olan eklenti projeleri için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-165">The `CopyLocalLockFileAssemblies` property is useful for plugin projects that have dependencies on other libraries.</span></span> <span data-ttu-id="d2b6e-166">Bu özelliği olarak ayarlarsanız `true` , herhangi bir NuGet paketi bağımlılığı çıkış dizinine kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-166">If you set this property to `true`, any NuGet package dependencies are copied to the output directory.</span></span> <span data-ttu-id="d2b6e-167">Diğer bir deyişle, `dotnet build` herhangi bir makinede kendi eklentisini çalıştırmak için çıkışını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-167">That means you can use the output of `dotnet build` to run your plugin on any machine.</span></span>

```xml
<PropertyGroup>
  <CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>
</PropertyGroup>
```

> [!TIP]
> <span data-ttu-id="d2b6e-168">Alternatif olarak, `dotnet publish` sınıf kitaplığını yayımlamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-168">Alternatively, you can use `dotnet publish` to publish the class library.</span></span> <span data-ttu-id="d2b6e-169">Daha fazla bilgi için bkz. [DotNet Publish](../tools/dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="d2b6e-169">For more information, see [dotnet publish](../tools/dotnet-publish.md).</span></span>

### <a name="preservecompilationcontext"></a><span data-ttu-id="d2b6e-170">PreserveCompilationContext</span><span class="sxs-lookup"><span data-stu-id="d2b6e-170">PreserveCompilationContext</span></span>

<span data-ttu-id="d2b6e-171">`PreserveCompilationContext`Özelliği, derleme zamanında kullanılan ayarların aynısını kullanarak, oluşturulmuş veya yayımlanmış bir uygulamanın çalışma zamanında daha fazla kod derlemesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-171">The `PreserveCompilationContext` property allows a built or published application to compile more code at run time using the same settings that were used at build time.</span></span> <span data-ttu-id="d2b6e-172">Derleme zamanında başvurulan derlemeler, çıkış dizininin *ref* alt dizinine kopyalanacak.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-172">The assemblies referenced at build time will be copied into the *ref* subdirectory of the output directory.</span></span> <span data-ttu-id="d2b6e-173">Başvuru derlemelerinin adları, derleyicisine geçirilen seçeneklerle birlikte uygulamanın.deps.jsdosya *üzerinde* depolanır.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-173">The names of the reference assemblies are stored in the application's *.deps.json* file along with the options passed to the compiler.</span></span> <span data-ttu-id="d2b6e-174">Ve özelliklerini kullanarak bu bilgileri alabilirsiniz <xref:Microsoft.Extensions.DependencyModel.DependencyContext.CompileLibraries?displayProperty=nameWithType> <xref:Microsoft.Extensions.DependencyModel.DependencyContext.CompilationOptions?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="d2b6e-174">You can retrieve this information using the <xref:Microsoft.Extensions.DependencyModel.DependencyContext.CompileLibraries?displayProperty=nameWithType> and <xref:Microsoft.Extensions.DependencyModel.DependencyContext.CompilationOptions?displayProperty=nameWithType> properties.</span></span>

<span data-ttu-id="d2b6e-175">Bu işlevsellik çoğunlukla, Razor dosyalarının çalışma zamanı derlemesini desteklemek için ASP.NET Core MVC ve Razor sayfaları tarafından dahili olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-175">This functionality is mostly used internally by ASP.NET Core MVC and Razor pages to support run-time compilation of Razor files.</span></span>

```xml
<PropertyGroup>
  <PreserveCompilationContext>true</PreserveCompilationContext>
</PropertyGroup>
```

### <a name="preservecompilationreferences"></a><span data-ttu-id="d2b6e-176">PreserveCompilationReferences</span><span class="sxs-lookup"><span data-stu-id="d2b6e-176">PreserveCompilationReferences</span></span>

<span data-ttu-id="d2b6e-177">`PreserveCompilationReferences`Özelliği [Preservecompilationcontext](#preservecompilationcontext) özelliğine benzerdir, ancak yalnızca başvurulan derlemeler dosya *.deps.js* değil yayımlama dizinine kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-177">The `PreserveCompilationReferences` property is similar to the [PreserveCompilationContext](#preservecompilationcontext) property, except that it only copies the referenced assemblies to the publish directory, and not the *.deps.json* file.</span></span>

```xml
<PropertyGroup>
  <PreserveCompilationReferences>true</PreserveCompilationReferences>
</PropertyGroup>
```

<span data-ttu-id="d2b6e-178">Daha fazla bilgi için bkz. [Razor SDK özellikleri](/aspnet/core/razor-pages/sdk#properties).</span><span class="sxs-lookup"><span data-stu-id="d2b6e-178">For more information, see [Razor SDK properties](/aspnet/core/razor-pages/sdk#properties).</span></span>

### <a name="runtimeidentifier"></a><span data-ttu-id="d2b6e-179">Runtimeıdentifier</span><span class="sxs-lookup"><span data-stu-id="d2b6e-179">RuntimeIdentifier</span></span>

<span data-ttu-id="d2b6e-180">`RuntimeIdentifier`Özelliği, proje için tek bir [çalışma zamanı tanımlayıcısı (RID)](../rid-catalog.md) belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-180">The `RuntimeIdentifier` property lets you specify a single [runtime identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="d2b6e-181">RID, kendi kendine içerilen bir dağıtımı yayımlamayı mümkün.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-181">The RID enables publishing a self-contained deployment.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
</PropertyGroup>
```

### <a name="runtimeidentifiers"></a><span data-ttu-id="d2b6e-182">Runtimetanımlayıcıtanımlayıcıları</span><span class="sxs-lookup"><span data-stu-id="d2b6e-182">RuntimeIdentifiers</span></span>

<span data-ttu-id="d2b6e-183">`RuntimeIdentifiers`Özelliği, proje için bir [çalışma zamanı tanımlayıcıları (RID 'ler)](../rid-catalog.md) için noktalı virgülle ayrılmış bir liste belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-183">The `RuntimeIdentifiers` property lets you specify a semicolon-delimited list of [runtime identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="d2b6e-184">Birden çok çalışma zamanı için yayımlamanız gerekiyorsa bu özelliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-184">Use this property if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="d2b6e-185">`RuntimeIdentifiers` , doğru varlıkların grafikte olduğundan emin olmak için geri yükleme zamanında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-185">`RuntimeIdentifiers` is used at restore time to ensure the right assets are in the graph.</span></span>

> [!TIP]
> <span data-ttu-id="d2b6e-186">`RuntimeIdentifier` (tekil) yalnızca tek bir çalışma zamanı gerektiğinde daha hızlı derlemeler sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-186">`RuntimeIdentifier` (singular) can provide faster builds when only a single runtime is required.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
</PropertyGroup>
```

### <a name="trimmerrootassembly"></a><span data-ttu-id="d2b6e-187">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="d2b6e-187">TrimmerRootAssembly</span></span>

<span data-ttu-id="d2b6e-188">`TrimmerRootAssembly`Öğe, bir derlemeyi [*kırpmanıza*](../deploying/trim-self-contained.md)dışlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-188">The `TrimmerRootAssembly` item lets you exclude an assembly from [*trimming*](../deploying/trim-self-contained.md).</span></span> <span data-ttu-id="d2b6e-189">Kırpma, çalışma zamanının kullanılmayan parçalarını paketlenmiş bir uygulamadan kaldırma işlemidir.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-189">Trimming is the process of removing unused parts of the runtime from a packaged application.</span></span> <span data-ttu-id="d2b6e-190">Bazı durumlarda, kırpma gerekli başvuruları yanlış kaldırabilir.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-190">In some cases, trimming might incorrectly remove required references.</span></span>

<span data-ttu-id="d2b6e-191">Aşağıdaki XML, `System.Security` derlemeyi kırpmaya dışlar.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-191">The following XML excludes the `System.Security` assembly from trimming.</span></span>

```xml
<ItemGroup>
  <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

### <a name="useapphost"></a><span data-ttu-id="d2b6e-192">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="d2b6e-192">UseAppHost</span></span>

<span data-ttu-id="d2b6e-193">`UseAppHost`Özelliği, bir dağıtım için yerel yürütülebilir dosyanın oluşturulup oluşturulmayacağını denetler.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-193">The `UseAppHost` property controls whether or not a native executable is created for a deployment.</span></span> <span data-ttu-id="d2b6e-194">Kendi kendine kapsanan dağıtımlar için yerel bir yürütülebilir dosya gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-194">A native executable is required for self-contained deployments.</span></span>

<span data-ttu-id="d2b6e-195">.NET Core 3,0 ve sonraki sürümlerinde, çerçeveye bağlı bir yürütülebilir dosya varsayılan olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-195">In .NET Core 3.0 and later versions, a framework-dependent executable is created by default.</span></span> <span data-ttu-id="d2b6e-196">`UseAppHost` `false` Yürütülebilir dosyanın üretilmesini devre dışı bırakmak için özelliğini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-196">Set the `UseAppHost` property to `false` to disable generation of the executable.</span></span>

```xml
<PropertyGroup>
  <UseAppHost>false</UseAppHost>
</PropertyGroup>
```

<span data-ttu-id="d2b6e-197">Dağıtım hakkında daha fazla bilgi için bkz. [.NET uygulama dağıtımı](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="d2b6e-197">For more information about deployment, see [.NET application deployment](../deploying/index.md).</span></span>

## <a name="compile-properties"></a><span data-ttu-id="d2b6e-198">Derleme özellikleri</span><span class="sxs-lookup"><span data-stu-id="d2b6e-198">Compile properties</span></span>

- [<span data-ttu-id="d2b6e-199">Embeddedresourceusebağımlıtuponconvention</span><span class="sxs-lookup"><span data-stu-id="d2b6e-199">EmbeddedResourceUseDependentUponConvention</span></span>](#embeddedresourceusedependentuponconvention)
- [<span data-ttu-id="d2b6e-200">LangVersion</span><span class="sxs-lookup"><span data-stu-id="d2b6e-200">LangVersion</span></span>](#langversion)

### <a name="embeddedresourceusedependentuponconvention"></a><span data-ttu-id="d2b6e-201">Embeddedresourceusebağımlıtuponconvention</span><span class="sxs-lookup"><span data-stu-id="d2b6e-201">EmbeddedResourceUseDependentUponConvention</span></span>

<span data-ttu-id="d2b6e-202">Özelliği, kaynak dosyaları `EmbeddedResourceUseDependentUponConvention` ile birlikte bulunan kaynak dosyalardaki tür bilgilerden kaynak bildirim dosyası adlarının oluşturulup oluşturulmayacağını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-202">The `EmbeddedResourceUseDependentUponConvention` property defines whether resource manifest file names are generated from type information in source files that are colocated with resource files.</span></span> <span data-ttu-id="d2b6e-203">Örneğin, *Form1. resx* , *Form1.cs* ile aynı klasörssa ve olarak `EmbeddedResourceUseDependentUponConvention` ayarlanırsa `true` , oluşturulan *. resources* dosyası, *Form1.cs* içinde tanımlanan ilk türden alır.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-203">For example, if *Form1.resx* is in the same folder as *Form1.cs*, and `EmbeddedResourceUseDependentUponConvention` is set to `true`, the generated *.resources* file takes its name from the first type that's defined in *Form1.cs*.</span></span> <span data-ttu-id="d2b6e-204">Örneğin, `MyNamespace.Form1` *Form1.cs* içinde tanımlanan ilk tür ise, oluşturulan dosya adı *MyNamespace. Form1. resources* olur.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-204">For example, if `MyNamespace.Form1` is the first type defined in *Form1.cs*, the generated file name is *MyNamespace.Form1.resources*.</span></span>

> [!NOTE]
> <span data-ttu-id="d2b6e-205">`LogicalName`,, `ManifestResourceName` Veya `DependentUpon` meta veriler bir öğe için belirtilmişse `EmbeddedResource` , bu kaynak dosyası için oluşturulan bildirim dosyası adı bu meta verileri temel alır.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-205">If `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for an `EmbeddedResource` item, the generated manifest file name for that resource file is based on that metadata instead.</span></span>

<span data-ttu-id="d2b6e-206">Varsayılan olarak, yeni bir .NET projesinde, bu özellik olarak ayarlanır `true` .</span><span class="sxs-lookup"><span data-stu-id="d2b6e-206">By default, in a new .NET project, this property is set to `true`.</span></span> <span data-ttu-id="d2b6e-207">`false`, Ve öğesi için, `LogicalName` `ManifestResourceName` Proje dosyasındaki öğe için, veya olarak ayarlanırsa,, `DependentUpon` `EmbeddedResource` kaynak bildirim dosyası adı projenin kök ad alanını ve *. resx* dosyasının göreli dosya yolunu temel alan olur.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-207">If set to `false`, and no `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for the `EmbeddedResource` item in the project file, the resource manifest file name is based off the root namespace for the project and the relative file path to the *.resx* file.</span></span> <span data-ttu-id="d2b6e-208">Daha fazla bilgi için bkz. [kaynak bildirim dosyalarının adlandırılması](../resources/manifest-file-names.md).</span><span class="sxs-lookup"><span data-stu-id="d2b6e-208">For more information, see [How resource manifest files are named](../resources/manifest-file-names.md).</span></span>

```xml
<PropertyGroup>
  <EmbeddedResourceUseDependentUponConvention>true</EmbeddedResourceUseDependentUponConvention>
</PropertyGroup>
```

### <a name="langversion"></a><span data-ttu-id="d2b6e-209">LangVersion</span><span class="sxs-lookup"><span data-stu-id="d2b6e-209">LangVersion</span></span>

<span data-ttu-id="d2b6e-210">`LangVersion`Özelliği, belirli bir programlama dili sürümü belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-210">The `LangVersion` property lets you specify a specific programming language version.</span></span> <span data-ttu-id="d2b6e-211">Örneğin, C# önizleme özelliklerine erişmek istiyorsanız, `LangVersion` olarak ayarlayın `preview` .</span><span class="sxs-lookup"><span data-stu-id="d2b6e-211">For example, if you want access to C# preview features, set `LangVersion` to `preview`.</span></span>

```xml
<PropertyGroup>
  <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="d2b6e-212">Daha fazla bilgi için bkz. [C# dil sürümü oluşturma](../../csharp/language-reference/configure-language-version.md#override-a-default).</span><span class="sxs-lookup"><span data-stu-id="d2b6e-212">For more information, see [C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).</span></span>

## <a name="default-item-inclusion-properties"></a><span data-ttu-id="d2b6e-213">Varsayılan öğe içerme özellikleri</span><span class="sxs-lookup"><span data-stu-id="d2b6e-213">Default item inclusion properties</span></span>

- [<span data-ttu-id="d2b6e-214">DefaultExcludesInProjectFolder</span><span class="sxs-lookup"><span data-stu-id="d2b6e-214">DefaultExcludesInProjectFolder</span></span>](#defaultexcludesinprojectfolder)
- [<span data-ttu-id="d2b6e-215">DefaultItemExcludes</span><span class="sxs-lookup"><span data-stu-id="d2b6e-215">DefaultItemExcludes</span></span>](#defaultitemexcludes)
- [<span data-ttu-id="d2b6e-216">Enabledefaultcompileıtems</span><span class="sxs-lookup"><span data-stu-id="d2b6e-216">EnableDefaultCompileItems</span></span>](#enabledefaultcompileitems)
- [<span data-ttu-id="d2b6e-217">Enabledefaultembeddedresourceıtems</span><span class="sxs-lookup"><span data-stu-id="d2b6e-217">EnableDefaultEmbeddedResourceItems</span></span>](#enabledefaultembeddedresourceitems)
- [<span data-ttu-id="d2b6e-218">Enabledefaultıtems</span><span class="sxs-lookup"><span data-stu-id="d2b6e-218">EnableDefaultItems</span></span>](#enabledefaultitems)
- [<span data-ttu-id="d2b6e-219">Enabledefaultnoneıtems</span><span class="sxs-lookup"><span data-stu-id="d2b6e-219">EnableDefaultNoneItems</span></span>](#enabledefaultnoneitems)

<span data-ttu-id="d2b6e-220">Daha fazla bilgi için bkz. [varsayılan içerme ve dışladığı](overview.md#default-includes-and-excludes).</span><span class="sxs-lookup"><span data-stu-id="d2b6e-220">For more information, see [Default includes and excludes](overview.md#default-includes-and-excludes).</span></span>

### <a name="defaultitemexcludes"></a><span data-ttu-id="d2b6e-221">DefaultItemExcludes</span><span class="sxs-lookup"><span data-stu-id="d2b6e-221">DefaultItemExcludes</span></span>

<span data-ttu-id="d2b6e-222">`DefaultItemExcludes`Include, exclude ve Remove genelleştirmeler dışında tutulması gereken dosya ve klasörler için glob desenleri tanımlamak üzere özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-222">Use the `DefaultItemExcludes` property to define glob patterns for files and folders that should be excluded from the include, exclude, and remove globs.</span></span> <span data-ttu-id="d2b6e-223">Varsayılan olarak, *./bin* ve *./obj* klasörleri, glob desenlerinden çıkarılır.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-223">By default, the *./bin* and *./obj* folders are excluded from the glob patterns.</span></span>

```xml
<PropertyGroup>
  <DefaultItemExcludes>$(DefaultItemExcludes);**/*.myextension</DefaultItemExcludes>
</PropertyGroup>
```

### <a name="defaultexcludesinprojectfolder"></a><span data-ttu-id="d2b6e-224">DefaultExcludesInProjectFolder</span><span class="sxs-lookup"><span data-stu-id="d2b6e-224">DefaultExcludesInProjectFolder</span></span>

<span data-ttu-id="d2b6e-225">`DefaultExcludesInProjectFolder`Dahil etme, hariç tutma ve kaldırma genelleştirmeler dışında tutulacak proje klasöründeki dosya ve klasörler için glob desenlerini tanımlamak üzere özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-225">Use the `DefaultExcludesInProjectFolder` property to define glob patterns for files and folders in the project folder that should be excluded from the include, exclude, and remove globs.</span></span> <span data-ttu-id="d2b6e-226">Varsayılan olarak, `.` *. git* ve *. vs* gibi bir noktayla başlayan klasörler, glob desenlerinden çıkarılır.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-226">By default, folders that start with a period (`.`), such as *.git* and *.vs*, are excluded from the glob patterns.</span></span>

<span data-ttu-id="d2b6e-227">Bu özellik, `DefaultItemExcludes` yalnızca proje klasöründeki dosya ve klasörleri dikkate almak dışında özelliğine çok benzer.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-227">This property is very similar to the `DefaultItemExcludes` property, except that it only considers files and folders in the project folder.</span></span> <span data-ttu-id="d2b6e-228">Bir glob deseninin proje klasörü dışındaki öğeleri bir göreli yol ile istenmeden eşleşmesi durumunda, özelliği `DefaultExcludesInProjectFolder` yerine özelliğini kullanın `DefaultItemExcludes` .</span><span class="sxs-lookup"><span data-stu-id="d2b6e-228">When a glob pattern would unintentionally match items outside the project folder with a relative path, use the `DefaultExcludesInProjectFolder` property instead of the `DefaultItemExcludes` property.</span></span>

```xml
<PropertyGroup>
  <DefaultExcludesInProjectFolder>$(DefaultExcludesInProjectFolder);**/myprefix*/**</DefaultExcludesInProjectFolder>
</PropertyGroup>
```

### <a name="enabledefaultitems"></a><span data-ttu-id="d2b6e-229">Enabledefaultıtems</span><span class="sxs-lookup"><span data-stu-id="d2b6e-229">EnableDefaultItems</span></span>

<span data-ttu-id="d2b6e-230">`EnableDefaultItems`Özelliği derleme öğelerinin, katıştırılmış kaynak öğelerinin ve `None` öğelerin projeye örtük olarak dahil edilip edilmeyeceğini denetler.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-230">The `EnableDefaultItems` property controls whether compile items, embedded resource items, and `None` items are implicitly included in the project.</span></span> <span data-ttu-id="d2b6e-231">`true` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-231">The default value is `true`.</span></span> <span data-ttu-id="d2b6e-232">`EnableDefaultItems` `false` Tüm örtük dosya dahil edilmesini devre dışı bırakmak için özelliğini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-232">Set the `EnableDefaultItems` property to `false` to disable all implicit file inclusion.</span></span>

```xml
<PropertyGroup>
  <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

### <a name="enabledefaultcompileitems"></a><span data-ttu-id="d2b6e-233">Enabledefaultcompileıtems</span><span class="sxs-lookup"><span data-stu-id="d2b6e-233">EnableDefaultCompileItems</span></span>

<span data-ttu-id="d2b6e-234">`EnableDefaultCompileItems`Özelliği, derleme öğelerinin projeye örtük olarak dahil edilip edilmeyeceğini denetler.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-234">The `EnableDefaultCompileItems` property controls whether compile items are implicitly included in the project.</span></span> <span data-ttu-id="d2b6e-235">`true` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-235">The default value is `true`.</span></span> <span data-ttu-id="d2b6e-236">`EnableDefaultCompileItems` `false` \*. Cs ve diğer dil uzantısı dosyalarının örtük olarak eklenmesini devre dışı bırakmak için özelliğini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-236">Set the `EnableDefaultCompileItems` property to `false` to disable implicit inclusion of \*.cs and other language-extension files.</span></span>

```xml
<PropertyGroup>
  <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

### <a name="enabledefaultembeddedresourceitems"></a><span data-ttu-id="d2b6e-237">Enabledefaultembeddedresourceıtems</span><span class="sxs-lookup"><span data-stu-id="d2b6e-237">EnableDefaultEmbeddedResourceItems</span></span>

<span data-ttu-id="d2b6e-238">`EnableDefaultEmbeddedResourceItems`Özelliği, katıştırılmış kaynak öğelerinin projeye örtük olarak dahil edilip edilmeyeceğini denetler.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-238">The `EnableDefaultEmbeddedResourceItems` property controls whether embedded resource items are implicitly included in the project.</span></span> <span data-ttu-id="d2b6e-239">`true` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-239">The default value is `true`.</span></span> <span data-ttu-id="d2b6e-240">`EnableDefaultEmbeddedResourceItems` `false` Gömülü kaynak dosyalarının örtük olarak eklenmesini devre dışı bırakmak için özelliğini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-240">Set the `EnableDefaultEmbeddedResourceItems` property to `false` to disable implicit inclusion of embedded resource files.</span></span>

```xml
<PropertyGroup>
  <EnableDefaultEmbeddedResourceItems>false</EnableDefaultEmbeddedResourceItems>
</PropertyGroup>
```

### <a name="enabledefaultnoneitems"></a><span data-ttu-id="d2b6e-241">Enabledefaultnoneıtems</span><span class="sxs-lookup"><span data-stu-id="d2b6e-241">EnableDefaultNoneItems</span></span>

<span data-ttu-id="d2b6e-242">`EnableDefaultNoneItems`Özelliği, `None` öğelerin (yapı işleminde rolü olmayan dosyalar) örtük olarak projeye dahil edilip edilmeyeceğini denetler.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-242">The `EnableDefaultNoneItems` property controls whether `None` items (files that have no role in the build process) are implicitly included in the project.</span></span> <span data-ttu-id="d2b6e-243">`true` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-243">The default value is `true`.</span></span> <span data-ttu-id="d2b6e-244">`EnableDefaultNoneItems`Özelliği `false` örtük olarak öğelerin dahil edilmesini devre dışı bırakmak için olarak ayarlayın `None` .</span><span class="sxs-lookup"><span data-stu-id="d2b6e-244">Set the `EnableDefaultNoneItems` property to `false` to disable implicit inclusion of `None` items.</span></span>

```xml
<PropertyGroup>
  <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

## <a name="code-analysis-properties"></a><span data-ttu-id="d2b6e-245">Kod Analizi özellikleri</span><span class="sxs-lookup"><span data-stu-id="d2b6e-245">Code analysis properties</span></span>

- [<span data-ttu-id="d2b6e-246">AnalysisLevel</span><span class="sxs-lookup"><span data-stu-id="d2b6e-246">AnalysisLevel</span></span>](#analysislevel)
- [<span data-ttu-id="d2b6e-247">AnalysisMode</span><span class="sxs-lookup"><span data-stu-id="d2b6e-247">AnalysisMode</span></span>](#analysismode)
- [<span data-ttu-id="d2b6e-248">CodeAnalysisTreatWarningsAsErrors</span><span class="sxs-lookup"><span data-stu-id="d2b6e-248">CodeAnalysisTreatWarningsAsErrors</span></span>](#codeanalysistreatwarningsaserrors)
- [<span data-ttu-id="d2b6e-249">Enablenetçözümleyiciler</span><span class="sxs-lookup"><span data-stu-id="d2b6e-249">EnableNETAnalyzers</span></span>](#enablenetanalyzers)
- [<span data-ttu-id="d2b6e-250">Enforcecodestyleınbuild</span><span class="sxs-lookup"><span data-stu-id="d2b6e-250">EnforceCodeStyleInBuild</span></span>](#enforcecodestyleinbuild)

### <a name="analysislevel"></a><span data-ttu-id="d2b6e-251">AnalysisLevel</span><span class="sxs-lookup"><span data-stu-id="d2b6e-251">AnalysisLevel</span></span>

<span data-ttu-id="d2b6e-252">`AnalysisLevel`Özelliği, kod analizi düzeyi belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-252">The `AnalysisLevel` property lets you specify a code-analysis level.</span></span> <span data-ttu-id="d2b6e-253">Örneğin, önizleme kodu Çözümleyicileri için erişim istiyorsanız, `AnalysisLevel` olarak ayarlayın `preview` .</span><span class="sxs-lookup"><span data-stu-id="d2b6e-253">For example, if you want access to preview code analyzers, set `AnalysisLevel` to `preview`.</span></span>

<span data-ttu-id="d2b6e-254">Varsayılan değer:</span><span class="sxs-lookup"><span data-stu-id="d2b6e-254">Default value:</span></span>

- <span data-ttu-id="d2b6e-255">Projeniz .NET 5,0 veya üstünü hedefliyorsa veya [Analysismode](#analysismode) özelliğini eklediyseniz, varsayılan değer olur `latest` .</span><span class="sxs-lookup"><span data-stu-id="d2b6e-255">If your project targets .NET 5.0 or later, or if you've added the [AnalysisMode](#analysismode) property, the default value is `latest`.</span></span>
- <span data-ttu-id="d2b6e-256">Aksi takdirde, açıkça proje dosyasına eklemediğiniz takdirde bu özellik atlanır.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-256">Otherwise, this property is omitted unless you explicitly add it to the project file.</span></span>

```xml
<PropertyGroup>
  <AnalysisLevel>preview</AnalysisLevel>
</PropertyGroup>
```

<span data-ttu-id="d2b6e-257">Aşağıdaki tabloda kullanılabilir seçenekler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-257">The following table shows the available options.</span></span>

| <span data-ttu-id="d2b6e-258">Değer</span><span class="sxs-lookup"><span data-stu-id="d2b6e-258">Value</span></span> | <span data-ttu-id="d2b6e-259">Anlamı</span><span class="sxs-lookup"><span data-stu-id="d2b6e-259">Meaning</span></span> |
|-|-|
| `latest` | <span data-ttu-id="d2b6e-260">Yayınlanan en son kod Çözümleyicileri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-260">The latest code analyzers that have been released are used.</span></span> <span data-ttu-id="d2b6e-261">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-261">This is the default.</span></span> |
| `preview` | <span data-ttu-id="d2b6e-262">Önizleme aşamasında olsalar dahi, en son kod Çözümleyicileri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-262">The latest code analyzers are used, even if they are in preview.</span></span> |
| `5.0` | <span data-ttu-id="d2b6e-263">.NET 5,0 sürümü için etkinleştirilen kurallar kümesi, daha yeni kurallar kullanılabilir olsa bile kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-263">The set of rules that was enabled for the .NET 5.0 release is used, even if newer rules are available.</span></span> |
| `5` | <span data-ttu-id="d2b6e-264">.NET 5,0 sürümü için etkinleştirilen kurallar kümesi, daha yeni kurallar kullanılabilir olsa bile kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-264">The set of rules that was enabled for the .NET 5.0 release is used, even if newer rules are available.</span></span> |

> [!NOTE]
> <span data-ttu-id="d2b6e-265">Bu özelliğin, [Proje SDK 'sına](overview.md)başvurmayan projeler (örneğin, Microsoft. CodeAnalysis. Netçözümleyiciler NuGet paketine başvuran eski .NET Framework projeleri) üzerinde kod analizi üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-265">This property has no effect on code analysis in projects that don't reference a [project SDK](overview.md), for example, legacy .NET Framework projects that reference the Microsoft.CodeAnalysis.NetAnalyzers NuGet package.</span></span>

### <a name="analysismode"></a><span data-ttu-id="d2b6e-266">AnalysisMode</span><span class="sxs-lookup"><span data-stu-id="d2b6e-266">AnalysisMode</span></span>

<span data-ttu-id="d2b6e-267">.NET SDK, .NET 5,0 ile başlayarak ["CA" kod kalitesi kurallarıyla](../../fundamentals/code-analysis/quality-rules/index.md)birlikte gönderilir.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-267">Starting with .NET 5.0, the .NET SDK ships with all of the ["CA" code quality rules](../../fundamentals/code-analysis/quality-rules/index.md).</span></span> <span data-ttu-id="d2b6e-268">Varsayılan olarak, yalnızca [bazı kurallar](../../fundamentals/code-analysis/overview.md#enabled-rules) derleme uyarıları olarak etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-268">By default, only [some rules are enabled](../../fundamentals/code-analysis/overview.md#enabled-rules) as build warnings.</span></span> <span data-ttu-id="d2b6e-269">`AnalysisMode`Özelliği, varsayılan olarak etkinleştirilen kuralların kümesini özelleştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-269">The `AnalysisMode` property lets you customize the set of rules that are enabled by default.</span></span> <span data-ttu-id="d2b6e-270">Daha Agresif (geri çevirme) çözümleme moduna veya daha koruyucu (katılım) analiz moduna geçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-270">You can either switch to a more aggressive (opt-out) analysis mode or a more conservative (opt-in) analysis mode.</span></span> <span data-ttu-id="d2b6e-271">Örneğin, varsayılan olarak tüm kuralları derleme uyarıları olarak etkinleştirmek istiyorsanız, değerini olarak ayarlayın `AllEnabledByDefault` .</span><span class="sxs-lookup"><span data-stu-id="d2b6e-271">For example, if you want to enable all rules by default as build warnings, set the value to `AllEnabledByDefault`.</span></span>

```xml
<PropertyGroup>
  <AnalysisMode>AllEnabledByDefault</AnalysisMode>
</PropertyGroup>
```

<span data-ttu-id="d2b6e-272">Aşağıdaki tabloda kullanılabilir seçenekler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-272">The following table shows the available options.</span></span>

| <span data-ttu-id="d2b6e-273">Değer</span><span class="sxs-lookup"><span data-stu-id="d2b6e-273">Value</span></span> | <span data-ttu-id="d2b6e-274">Anlamı</span><span class="sxs-lookup"><span data-stu-id="d2b6e-274">Meaning</span></span> |
|-|-|
| `Default` | <span data-ttu-id="d2b6e-275">Belirli kuralların derleme uyarıları olarak etkinleştirildiği varsayılan mod, Visual Studio IDE önerisi olarak bazı kurallar etkinleştirilir ve geri kalanı devre dışı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-275">Default mode, where certain rules are enabled as build warnings, certain rules are enabled as Visual Studio IDE suggestions, and the remainder are disabled.</span></span> |
| `AllEnabledByDefault` | <span data-ttu-id="d2b6e-276">Tüm kuralların, derleme uyarıları olarak varsayılan olarak etkinleştirildiği agresif veya kabul etme modu.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-276">Aggressive or opt-out mode, where all rules are enabled by default as build warnings.</span></span> <span data-ttu-id="d2b6e-277">Bağımsız kuralların devre dışı [bırakılacağını seçerek devre dışı bırakabilirsiniz](../../fundamentals/code-analysis/configuration-options.md) .</span><span class="sxs-lookup"><span data-stu-id="d2b6e-277">You can selectively [opt out](../../fundamentals/code-analysis/configuration-options.md) of individual rules to disable them.</span></span> |
| `AllDisabledByDefault` | <span data-ttu-id="d2b6e-278">Klasik veya kabul etme modu, tüm kurallar varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-278">Conservative or opt-in mode, where all rules are disabled by default.</span></span> <span data-ttu-id="d2b6e-279">Bunları etkinleştirmek için tek tek kuralların seçmeli olarak [tercih](../../fundamentals/code-analysis/configuration-options.md) edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-279">You can selectively [opt into](../../fundamentals/code-analysis/configuration-options.md) individual rules to enable them.</span></span> |

> [!NOTE]
> <span data-ttu-id="d2b6e-280">Bu özelliğin, [Proje SDK 'sına](overview.md)başvurmayan projeler (örneğin, Microsoft. CodeAnalysis. Netçözümleyiciler NuGet paketine başvuran eski .NET Framework projeleri) üzerinde kod analizi üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-280">This property has no effect on code analysis in projects that don't reference a [project SDK](overview.md), for example, legacy .NET Framework projects that reference the Microsoft.CodeAnalysis.NetAnalyzers NuGet package.</span></span>

### <a name="codeanalysistreatwarningsaserrors"></a><span data-ttu-id="d2b6e-281">CodeAnalysisTreatWarningsAsErrors</span><span class="sxs-lookup"><span data-stu-id="d2b6e-281">CodeAnalysisTreatWarningsAsErrors</span></span>

<span data-ttu-id="d2b6e-282">`CodeAnalysisTreatWarningsAsErrors`Özelliği, kod kalitesi analizi uyarılarının (CAxxxx) uyarı olarak değerlendirilip derlenmeyeceğini yapılandırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-282">The `CodeAnalysisTreatWarningsAsErrors` property lets you configure whether code quality analysis warnings (CAxxxx) should be treated as warnings and break the build.</span></span> <span data-ttu-id="d2b6e-283">Projelerinizi oluştururken bayrağını kullanırsanız `-warnaserror` , [.net Code Quality Analysis](../../fundamentals/code-analysis/overview.md#code-quality-analysis) uyarıları da hata olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-283">If you use the `-warnaserror` flag when you build your projects, [.NET code quality analysis](../../fundamentals/code-analysis/overview.md#code-quality-analysis) warnings are also treated as errors.</span></span> <span data-ttu-id="d2b6e-284">Kod kalitesi analiz uyarılarını hata olarak kabul etmek istemiyorsanız, `CodeAnalysisTreatWarningsAsErrors` MSBuild özelliğini `false` proje dosyanızda olarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-284">If you do not want code quality analysis warnings to be treated as errors, you can set the `CodeAnalysisTreatWarningsAsErrors` MSBuild property to `false` in your project file.</span></span>

```xml
<PropertyGroup>
  <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
</PropertyGroup>
```

### <a name="enablenetanalyzers"></a><span data-ttu-id="d2b6e-285">Enablenetçözümleyiciler</span><span class="sxs-lookup"><span data-stu-id="d2b6e-285">EnableNETAnalyzers</span></span>

<span data-ttu-id="d2b6e-286">.Net [Code Quality Analysis](../../fundamentals/code-analysis/overview.md#code-quality-analysis) , .NET 5,0 veya üstünü hedefleyen projeler için varsayılan olarak etkinleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-286">[.NET code quality analysis](../../fundamentals/code-analysis/overview.md#code-quality-analysis) is enabled, by default, for projects that target .NET 5.0 or later.</span></span> <span data-ttu-id="d2b6e-287">Özelliğini olarak ayarlayarak .NET 'in önceki sürümlerini hedefleyen SDK stilindeki projeler için .NET kod analizini etkinleştirebilirsiniz `EnableNETAnalyzers` `true` .</span><span class="sxs-lookup"><span data-stu-id="d2b6e-287">You can enable .NET code analysis for SDK-style projects that target earlier versions of .NET by setting the `EnableNETAnalyzers` property to `true`.</span></span> <span data-ttu-id="d2b6e-288">Herhangi bir projede kod analizini devre dışı bırakmak için bu özelliği olarak ayarlayın `false` .</span><span class="sxs-lookup"><span data-stu-id="d2b6e-288">To disable code analysis in any project, set this property to `false`.</span></span>

```xml
<PropertyGroup>
  <EnableNETAnalyzers>true</EnableNETAnalyzers>
</PropertyGroup>
```

> [!NOTE]
> <span data-ttu-id="d2b6e-289">Bu özellik özellikle .NET 5 + SDK 'daki yerleşik çözümleyiciler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-289">This property applies specifically to the built-in analyzers in the .NET 5+ SDK.</span></span> <span data-ttu-id="d2b6e-290">Bir NuGet kod analizi paketi yüklediğinizde kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-290">It should not be used when you install a NuGet code analysis package.</span></span>

### <a name="enforcecodestyleinbuild"></a><span data-ttu-id="d2b6e-291">Enforcecodestyleınbuild</span><span class="sxs-lookup"><span data-stu-id="d2b6e-291">EnforceCodeStyleInBuild</span></span>

> [!NOTE]
> <span data-ttu-id="d2b6e-292">Bu özellik şu anda deneysel ve .NET 5 ve .NET 6 sürümleri arasında değişebilir.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-292">This feature is currently experimental and may change between the .NET 5 and .NET 6 releases.</span></span>

<span data-ttu-id="d2b6e-293">[.NET kod stili Analizi](../../fundamentals/code-analysis/overview.md#code-style-analysis) , varsayılan olarak tüm .NET projeleri için derleme üzerinde devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-293">[.NET code style analysis](../../fundamentals/code-analysis/overview.md#code-style-analysis) is disabled, by default, on build for all .NET projects.</span></span> <span data-ttu-id="d2b6e-294">Özelliğini olarak ayarlayarak .NET projeleri için kod stili analizini etkinleştirebilirsiniz `EnforceCodeStyleInBuild` `true` .</span><span class="sxs-lookup"><span data-stu-id="d2b6e-294">You can enable code style analysis for .NET projects by setting the `EnforceCodeStyleInBuild` property to `true`.</span></span>

```xml
<PropertyGroup>
  <EnforceCodeStyleInBuild>true</EnforceCodeStyleInBuild>
</PropertyGroup>
```

<span data-ttu-id="d2b6e-295">Uyarı veya hata olarak [yapılandırılan](../../fundamentals/code-analysis/overview.md#code-style-analysis) tüm kod stili kuralları, derleme ve rapor ihlalleri üzerinde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-295">All code style rules that are [configured](../../fundamentals/code-analysis/overview.md#code-style-analysis) to be warnings or errors will execute on build and report violations.</span></span>

## <a name="run-time-configuration-properties"></a><span data-ttu-id="d2b6e-296">Çalışma zamanı yapılandırma özellikleri</span><span class="sxs-lookup"><span data-stu-id="d2b6e-296">Run-time configuration properties</span></span>

<span data-ttu-id="d2b6e-297">Uygulamanın proje dosyasında MSBuild özelliklerini belirterek bazı çalışma zamanı davranışları yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-297">You can configure some run-time behaviors by specifying MSBuild properties in the project file of the app.</span></span> <span data-ttu-id="d2b6e-298">Çalışma zamanı davranışını yapılandırmanın diğer yolları hakkında daha fazla bilgi için bkz. [çalışma zamanı yapılandırma ayarları](../run-time-config/index.md).</span><span class="sxs-lookup"><span data-stu-id="d2b6e-298">For information about other ways of configuring run-time behavior, see [Run-time configuration settings](../run-time-config/index.md).</span></span>

- [<span data-ttu-id="d2b6e-299">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="d2b6e-299">ConcurrentGarbageCollection</span></span>](#concurrentgarbagecollection)
- [<span data-ttu-id="d2b6e-300">Invariantgenelleştirme</span><span class="sxs-lookup"><span data-stu-id="d2b6e-300">InvariantGlobalization</span></span>](#invariantglobalization)
- [<span data-ttu-id="d2b6e-301">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="d2b6e-301">RetainVMGarbageCollection</span></span>](#retainvmgarbagecollection)
- [<span data-ttu-id="d2b6e-302">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="d2b6e-302">ServerGarbageCollection</span></span>](#servergarbagecollection)
- [<span data-ttu-id="d2b6e-303">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="d2b6e-303">ThreadPoolMaxThreads</span></span>](#threadpoolmaxthreads)
- [<span data-ttu-id="d2b6e-304">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="d2b6e-304">ThreadPoolMinThreads</span></span>](#threadpoolminthreads)
- [<span data-ttu-id="d2b6e-305">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="d2b6e-305">TieredCompilation</span></span>](#tieredcompilation)
- [<span data-ttu-id="d2b6e-306">Tieredcompilationquickjıt</span><span class="sxs-lookup"><span data-stu-id="d2b6e-306">TieredCompilationQuickJit</span></span>](#tieredcompilationquickjit)
- [<span data-ttu-id="d2b6e-307">Tieredcompilationquickjıtfordöngüleri</span><span class="sxs-lookup"><span data-stu-id="d2b6e-307">TieredCompilationQuickJitForLoops</span></span>](#tieredcompilationquickjitforloops)

### <a name="concurrentgarbagecollection"></a><span data-ttu-id="d2b6e-308">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="d2b6e-308">ConcurrentGarbageCollection</span></span>

<span data-ttu-id="d2b6e-309">`ConcurrentGarbageCollection`Özelliği [Background (eşzamanlı) Çöp toplamanın](../../standard/garbage-collection/background-gc.md) etkinleştirilip etkinleştirilmeyeceğini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-309">The `ConcurrentGarbageCollection` property configures whether [background (concurrent) garbage collection](../../standard/garbage-collection/background-gc.md) is enabled.</span></span> <span data-ttu-id="d2b6e-310">`false`Arka plan atık toplamayı devre dışı bırakmak için değerini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-310">Set the value to `false` to disable background garbage collection.</span></span> <span data-ttu-id="d2b6e-311">Daha fazla bilgi için bkz. [arka plan GC](../run-time-config/garbage-collector.md#background-gc).</span><span class="sxs-lookup"><span data-stu-id="d2b6e-311">For more information, see [Background GC](../run-time-config/garbage-collector.md#background-gc).</span></span>

```xml
<PropertyGroup>
  <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
</PropertyGroup>
```

### <a name="invariantglobalization"></a><span data-ttu-id="d2b6e-312">Invariantgenelleştirme</span><span class="sxs-lookup"><span data-stu-id="d2b6e-312">InvariantGlobalization</span></span>

<span data-ttu-id="d2b6e-313">`InvariantGlobalization`Özelliği, uygulamanın *Genelleştirme sabit* modunda çalışıp çalışmadığını yapılandırır, bu, kültüre özgü verilere erişimi olmayan anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-313">The `InvariantGlobalization` property configures whether the app runs in *globalization-invariant* mode, which means it doesn't have access to culture-specific data.</span></span> <span data-ttu-id="d2b6e-314">Değeri `true` Genelleştirme sabit modunda çalışacak şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-314">Set the value to `true` to run in globalization-invariant mode.</span></span> <span data-ttu-id="d2b6e-315">Daha fazla bilgi için bkz. [sabit mod](../run-time-config/globalization.md#invariant-mode).</span><span class="sxs-lookup"><span data-stu-id="d2b6e-315">For more information, see [Invariant mode](../run-time-config/globalization.md#invariant-mode).</span></span>

```xml
<PropertyGroup>
  <InvariantGlobalization>true</InvariantGlobalization>
</PropertyGroup>
```

### <a name="retainvmgarbagecollection"></a><span data-ttu-id="d2b6e-316">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="d2b6e-316">RetainVMGarbageCollection</span></span>

<span data-ttu-id="d2b6e-317">`RetainVMGarbageCollection`Özelliği, çöp toplayıcıyı, daha sonra kullanılmak üzere veya serbest bırakmak için silinen bellek segmentlerini bir bekleme listesine koymak üzere yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-317">The `RetainVMGarbageCollection` property configures the garbage collector to put deleted memory segments on a standby list for future use or release them.</span></span> <span data-ttu-id="d2b6e-318">Değeri, `true` çöp toplayıcıya kesimleri bir bekleme listesine koymasını söyler.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-318">Setting the value to `true` tells the garbage collector to put the segments on a standby list.</span></span> <span data-ttu-id="d2b6e-319">Daha fazla bilgi için bkz. [VM 'Yi koruma](../run-time-config/garbage-collector.md#retain-vm).</span><span class="sxs-lookup"><span data-stu-id="d2b6e-319">For more information, see [Retain VM](../run-time-config/garbage-collector.md#retain-vm).</span></span>

```xml
<PropertyGroup>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
</PropertyGroup>
```

### <a name="servergarbagecollection"></a><span data-ttu-id="d2b6e-320">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="d2b6e-320">ServerGarbageCollection</span></span>

<span data-ttu-id="d2b6e-321">`ServerGarbageCollection`Özelliği, uygulamanın [iş istasyonu çöp toplamayı veya sunucu çöp toplamayı](../../standard/garbage-collection/workstation-server-gc.md)kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-321">The `ServerGarbageCollection` property configures whether the application uses [workstation garbage collection or server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span> <span data-ttu-id="d2b6e-322">Değerini `true` sunucu çöp toplamayı kullanacak şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-322">Set the value to `true` to use server garbage collection.</span></span> <span data-ttu-id="d2b6e-323">Daha fazla bilgi için bkz. [Workstation vs Server](../run-time-config/garbage-collector.md#workstation-vs-server).</span><span class="sxs-lookup"><span data-stu-id="d2b6e-323">For more information, see [Workstation vs. server](../run-time-config/garbage-collector.md#workstation-vs-server).</span></span>

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

### <a name="threadpoolmaxthreads"></a><span data-ttu-id="d2b6e-324">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="d2b6e-324">ThreadPoolMaxThreads</span></span>

<span data-ttu-id="d2b6e-325">`ThreadPoolMaxThreads`Özelliği, çalışan iş parçacığı havuzu için en fazla iş parçacığı sayısını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-325">The `ThreadPoolMaxThreads` property configures the maximum number of threads for the worker thread pool.</span></span> <span data-ttu-id="d2b6e-326">Daha fazla bilgi için bkz. [en fazla iş parçacığı](../run-time-config/threading.md#maximum-threads).</span><span class="sxs-lookup"><span data-stu-id="d2b6e-326">For more information, see [Maximum threads](../run-time-config/threading.md#maximum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
</PropertyGroup>
```

### <a name="threadpoolminthreads"></a><span data-ttu-id="d2b6e-327">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="d2b6e-327">ThreadPoolMinThreads</span></span>

<span data-ttu-id="d2b6e-328">`ThreadPoolMinThreads`Özelliği, çalışan iş parçacığı havuzu için en az iş parçacığı sayısını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-328">The `ThreadPoolMinThreads` property configures the minimum number of threads for the worker thread pool.</span></span> <span data-ttu-id="d2b6e-329">Daha fazla bilgi için bkz. [En düşük iş parçacıkları](../run-time-config/threading.md#minimum-threads).</span><span class="sxs-lookup"><span data-stu-id="d2b6e-329">For more information, see [Minimum threads](../run-time-config/threading.md#minimum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
</PropertyGroup>
```

### <a name="tieredcompilation"></a><span data-ttu-id="d2b6e-330">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="d2b6e-330">TieredCompilation</span></span>

<span data-ttu-id="d2b6e-331">`TieredCompilation`Özelliği, Just-In-Time (JIT) derleyicisinin [katmanlı derlemeyi](../whats-new/dotnet-core-3-0.md#tiered-compilation)kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-331">The `TieredCompilation` property configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="d2b6e-332">`false`Katmanlı derlemeyi devre dışı bırakmak için değerini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-332">Set the value to `false` to disable tiered compilation.</span></span> <span data-ttu-id="d2b6e-333">Daha fazla bilgi için bkz. [katmanlı derleme](../run-time-config/compilation.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="d2b6e-333">For more information, see [Tiered compilation](../run-time-config/compilation.md#tiered-compilation).</span></span>

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

### <a name="tieredcompilationquickjit"></a><span data-ttu-id="d2b6e-334">Tieredcompilationquickjıt</span><span class="sxs-lookup"><span data-stu-id="d2b6e-334">TieredCompilationQuickJit</span></span>

<span data-ttu-id="d2b6e-335">`TieredCompilationQuickJit`Özelliği, JIT derleyicisinin hızlı JIT kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-335">The `TieredCompilationQuickJit` property configures whether the JIT compiler uses quick JIT.</span></span> <span data-ttu-id="d2b6e-336">`false`Hızlı JIT 'i devre dışı bırakmak için değerini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-336">Set the value to `false` to disable quick JIT.</span></span> <span data-ttu-id="d2b6e-337">Daha fazla bilgi için bkz. [hızlı JIT](../run-time-config/compilation.md#quick-jit).</span><span class="sxs-lookup"><span data-stu-id="d2b6e-337">For more information, see [Quick JIT](../run-time-config/compilation.md#quick-jit).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

### <a name="tieredcompilationquickjitforloops"></a><span data-ttu-id="d2b6e-338">Tieredcompilationquickjıtfordöngüleri</span><span class="sxs-lookup"><span data-stu-id="d2b6e-338">TieredCompilationQuickJitForLoops</span></span>

<span data-ttu-id="d2b6e-339">`TieredCompilationQuickJitForLoops`Özelliği, JIT derleyicisinin döngüleri içeren yöntemlerde hızlı JIT kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-339">The `TieredCompilationQuickJitForLoops` property configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span> <span data-ttu-id="d2b6e-340">`true`Döngüleri içeren yöntemlerde hızlı JIT 'i etkinleştirmek için değerini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-340">Set the value to `true` to enable quick JIT on methods that contain loops.</span></span> <span data-ttu-id="d2b6e-341">Daha fazla bilgi için bkz. [döngüler Için hızlı JIT](../run-time-config/compilation.md#quick-jit-for-loops).</span><span class="sxs-lookup"><span data-stu-id="d2b6e-341">For more information, see [Quick JIT for loops](../run-time-config/compilation.md#quick-jit-for-loops).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
</PropertyGroup>
```

## <a name="reference-properties-and-items"></a><span data-ttu-id="d2b6e-342">Başvuru özellikleri ve öğeleri</span><span class="sxs-lookup"><span data-stu-id="d2b6e-342">Reference properties and items</span></span>

- [<span data-ttu-id="d2b6e-343">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="d2b6e-343">AssetTargetFallback</span></span>](#assettargetfallback)
- [<span data-ttu-id="d2b6e-344">DisableImplicitFrameworkReferences</span><span class="sxs-lookup"><span data-stu-id="d2b6e-344">DisableImplicitFrameworkReferences</span></span>](#disableimplicitframeworkreferences)
- [<span data-ttu-id="d2b6e-345">PackageReference</span><span class="sxs-lookup"><span data-stu-id="d2b6e-345">PackageReference</span></span>](#packagereference)
- [<span data-ttu-id="d2b6e-346">ProjectReference</span><span class="sxs-lookup"><span data-stu-id="d2b6e-346">ProjectReference</span></span>](#projectreference)
- [<span data-ttu-id="d2b6e-347">Başvuru</span><span class="sxs-lookup"><span data-stu-id="d2b6e-347">Reference</span></span>](#reference)
- [<span data-ttu-id="d2b6e-348">Geri yükleme ile ilgili özellikler</span><span class="sxs-lookup"><span data-stu-id="d2b6e-348">Restore-related properties</span></span>](#restore-related-properties)

### <a name="assettargetfallback"></a><span data-ttu-id="d2b6e-349">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="d2b6e-349">AssetTargetFallback</span></span>

<span data-ttu-id="d2b6e-350">`AssetTargetFallback`Özelliği, proje başvuruları ve NuGet paketleri için ek uyumlu çerçeve sürümlerini belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-350">The `AssetTargetFallback` property lets you specify additional compatible framework versions for project references and NuGet packages.</span></span> <span data-ttu-id="d2b6e-351">Örneğin, kullanarak bir paket bağımlılığı belirtirseniz `PackageReference` ancak bu paket, projelerinizle uyumlu olan varlıkları içermiyorsa `TargetFramework` , `AssetTargetFallback` özelliği yürütmeye gelir.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-351">For example, if you specify a package dependency using `PackageReference` but that package doesn't contain assets that are compatible with your projects's `TargetFramework`, the `AssetTargetFallback` property comes into play.</span></span> <span data-ttu-id="d2b6e-352">Başvurulan paketin uyumluluğu, içinde belirtilen her bir hedef çerçeve kullanılarak yeniden denetlenir `AssetTargetFallback` .</span><span class="sxs-lookup"><span data-stu-id="d2b6e-352">The compatibility of the referenced package is rechecked using each target framework that's specified in `AssetTargetFallback`.</span></span> <span data-ttu-id="d2b6e-353">Bu özellik kullanımdan kaldırılan özelliğin yerini alır `PackageTargetFallback` .</span><span class="sxs-lookup"><span data-stu-id="d2b6e-353">This property replaces the deprecated property `PackageTargetFallback`.</span></span>

<span data-ttu-id="d2b6e-354">`AssetTargetFallback`Özelliğini bir veya daha fazla [hedef çerçeve sürümüne](../../standard/frameworks.md#supported-target-frameworks)ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-354">You can set the `AssetTargetFallback` property to one or more [target framework versions](../../standard/frameworks.md#supported-target-frameworks).</span></span>

```xml
<PropertyGroup>
  <AssetTargetFallback>net461</AssetTargetFallback>
</PropertyGroup>
```

### <a name="disableimplicitframeworkreferences"></a><span data-ttu-id="d2b6e-355">DisableImplicitFrameworkReferences</span><span class="sxs-lookup"><span data-stu-id="d2b6e-355">DisableImplicitFrameworkReferences</span></span>

<span data-ttu-id="d2b6e-356">`DisableImplicitFrameworkReferences`Özelliği, `FrameworkReference` .net Core 3,0 ve sonraki sürümlerini hedeflerken örtük öğeleri denetler.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-356">The `DisableImplicitFrameworkReferences` property controls implicit `FrameworkReference` items when targeting .NET Core 3.0 and later versions.</span></span> <span data-ttu-id="d2b6e-357">.NET Core 2,1 veya .NET Standard 2,0 ve önceki sürümlerini hedeflerken, bir metapackage içindeki paketlere örtük [Packagereference](#packagereference) öğelerini denetler.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-357">When targeting .NET Core 2.1 or .NET Standard 2.0 and earlier versions, it controls implicit [PackageReference](#packagereference) items to packages in a metapackage.</span></span> <span data-ttu-id="d2b6e-358">(Metapackage, yalnızca diğer paketlerdeki bağımlılıklardan oluşan çerçeve tabanlı bir pakettir.) Bu özellik ayrıca `System` , .NET Framework hedefleme gibi örtülü başvuruları da denetler `System.Core` .</span><span class="sxs-lookup"><span data-stu-id="d2b6e-358">(A metapackage is a framework-based package that consist only of dependencies on other packages.) This property also controls implicit references such as `System` and `System.Core` when targeting .NET Framework.</span></span>

<span data-ttu-id="d2b6e-359">`true`Örtük `FrameworkReference` veya [packagereference](#packagereference) öğelerini devre dışı bırakmak için bu özelliği olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-359">Set this property to `true` to disable implicit `FrameworkReference` or [PackageReference](#packagereference) items.</span></span> <span data-ttu-id="d2b6e-360">Bu özelliği olarak ayarlarsanız `true` , yalnızca ihtiyacınız olan çerçevelere veya paketlere açık başvurular ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-360">If you set this property to `true`, you can add explicit references to just the frameworks or packages you need.</span></span>

```xml
<PropertyGroup>
  <DisableImplicitFrameworkReferences>true</DisableImplicitFrameworkReferences>
</PropertyGroup>
```

### <a name="packagereference"></a><span data-ttu-id="d2b6e-361">PackageReference</span><span class="sxs-lookup"><span data-stu-id="d2b6e-361">PackageReference</span></span>

<span data-ttu-id="d2b6e-362">`PackageReference`Öğe, bir NuGet paketine bir başvuru tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-362">The `PackageReference` item defines a reference to a NuGet package.</span></span>

<span data-ttu-id="d2b6e-363">`Include`Öznitelik, paket kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-363">The `Include` attribute specifies the package ID.</span></span> <span data-ttu-id="d2b6e-364">`Version`Öznitelik, sürümü veya sürüm aralığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-364">The `Version` attribute specifies the version or version range.</span></span> <span data-ttu-id="d2b6e-365">En düşük sürüm, en yüksek sürüm, Aralık veya tam eşleşme belirtme hakkında bilgi için bkz. [Sürüm aralıkları](/nuget/concepts/package-versioning#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="d2b6e-365">For information about how to specify a minimum version, maximum version, range, or exact match, see [Version ranges](/nuget/concepts/package-versioning#version-ranges).</span></span> <span data-ttu-id="d2b6e-366">Ayrıca, bir paket başvurusuna [varlık öznitelikleri](#asset-attributes) ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-366">You can also add [asset attributes](#asset-attributes) to a package reference.</span></span>

<span data-ttu-id="d2b6e-367">Aşağıdaki örnekteki proje dosyası kod parçacığı [System. Runtime](https://www.nuget.org/packages/System.Runtime/) paketine başvurur.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-367">The project file snippet in the following example references the [System.Runtime](https://www.nuget.org/packages/System.Runtime/) package.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="System.Runtime" Version="4.3.0" />
</ItemGroup>
```

<span data-ttu-id="d2b6e-368">Daha fazla bilgi için bkz. [Proje dosyalarındaki paket başvuruları](/nuget/consume-packages/package-references-in-project-files).</span><span class="sxs-lookup"><span data-stu-id="d2b6e-368">For more information, see [Package references in project files](/nuget/consume-packages/package-references-in-project-files).</span></span>

#### <a name="asset-attributes"></a><span data-ttu-id="d2b6e-369">Varlık öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="d2b6e-369">Asset attributes</span></span>

<span data-ttu-id="d2b6e-370">`IncludeAssets`, `ExcludeAssets` Ve `PrivateAssets` meta veriler bir paket başvurusuna eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-370">The `IncludeAssets`, `ExcludeAssets`, and `PrivateAssets` metadata can be added to a package reference.</span></span>

| <span data-ttu-id="d2b6e-371">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d2b6e-371">Attribute</span></span> | <span data-ttu-id="d2b6e-372">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d2b6e-372">Description</span></span> |
| - | - |
| `IncludeAssets` | <span data-ttu-id="d2b6e-373">Tarafından belirtilen pakete ait olan varlıkların `<PackageReference>` tüketilmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-373">Specifies which assets belonging to the package specified by `<PackageReference>` should be consumed.</span></span> <span data-ttu-id="d2b6e-374">Varsayılan olarak, tüm paket varlıkları dahil edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-374">By default, all package assets are included.</span></span> |
| `ExcludeAssets`| <span data-ttu-id="d2b6e-375">Tarafından belirtilen pakete ait olan varlıkların `<PackageReference>` tüketilmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-375">Specifies which assets belonging to the package specified by `<PackageReference>` should not be consumed.</span></span> |
| `PrivateAssets` | <span data-ttu-id="d2b6e-376">Tarafından belirtilen pakete ait olan varlıkların `<PackageReference>` tüketilmesi ancak bir sonraki projeye akolmaması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-376">Specifies which assets belonging to the package specified by `<PackageReference>` should be consumed but not flow to the next project.</span></span> <span data-ttu-id="d2b6e-377">`Analyzers` `Build` Bu öznitelik mevcut olmadığında,, ve `ContentFiles` varlıkları varsayılan olarak özeldir.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-377">The `Analyzers`, `Build`, and `ContentFiles` assets are private by default when this attribute is not present.</span></span> |

<span data-ttu-id="d2b6e-378">Bu öznitelikler, birden fazla listeleniyorsa noktalı virgülle ayırarak aşağıdaki öğelerden birini veya daha fazlasını içerebilir `;` :</span><span class="sxs-lookup"><span data-stu-id="d2b6e-378">These attributes can contain one or more of the following items, separated by a semicolon `;` if more than one is listed:</span></span>

- <span data-ttu-id="d2b6e-379">`Compile` – *LIB* klasörünün içeriği, derleme için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-379">`Compile` – the contents of the *lib* folder are available to compile against.</span></span>
- <span data-ttu-id="d2b6e-380">`Runtime` – *çalışma zamanı* klasörünün içeriği dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-380">`Runtime` – the contents of the *runtime* folder are distributed.</span></span>
- <span data-ttu-id="d2b6e-381">`ContentFiles` – *ContentFiles* klasörünün içeriği kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-381">`ContentFiles` – the contents of the *contentfiles* folder are used.</span></span>
- <span data-ttu-id="d2b6e-382">`Build` – *Build* klasöründeki props/targets kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-382">`Build` – the props/targets in the *build* folder are used.</span></span>
- <span data-ttu-id="d2b6e-383">`Native` – Yerel varlıklardan içerik çalışma zamanı için *Çıkış* klasörüne kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-383">`Native` – the contents from native assets are copied to the *output* folder for runtime.</span></span>
- <span data-ttu-id="d2b6e-384">`Analyzers` – çözümleyiciler kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-384">`Analyzers` – the analyzers are used.</span></span>

<span data-ttu-id="d2b6e-385">Alternatif olarak, öznitelik şunları içerebilir:</span><span class="sxs-lookup"><span data-stu-id="d2b6e-385">Alternatively, the attribute can contain:</span></span>

- <span data-ttu-id="d2b6e-386">`None` – varlıkların hiçbiri kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-386">`None` – none of the assets are used.</span></span>
- <span data-ttu-id="d2b6e-387">`All` – Tüm varlıklar kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-387">`All` – all assets are used.</span></span>

### <a name="projectreference"></a><span data-ttu-id="d2b6e-388">ProjectReference</span><span class="sxs-lookup"><span data-stu-id="d2b6e-388">ProjectReference</span></span>

<span data-ttu-id="d2b6e-389">`ProjectReference`Öğe, başka bir projeye yönelik bir başvuru tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-389">The `ProjectReference` item defines a reference to another project.</span></span> <span data-ttu-id="d2b6e-390">Başvurulan proje bir NuGet paket bağımlılığı olarak eklenir, diğer bir deyişle, ile aynı şekilde işlenir `PackageReference` .</span><span class="sxs-lookup"><span data-stu-id="d2b6e-390">The referenced project is added as a NuGet package dependency, that is, it's treated the same as a `PackageReference`.</span></span>

<span data-ttu-id="d2b6e-391">`Include`Öznitelik, projenin yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-391">The `Include` attribute specifies the path to the project.</span></span> <span data-ttu-id="d2b6e-392">Aşağıdaki meta verileri bir proje başvurusuna de ekleyebilirsiniz: `IncludeAssets` , `ExcludeAssets` , ve `PrivateAssets` .</span><span class="sxs-lookup"><span data-stu-id="d2b6e-392">You can also add the following metadata to a project reference: `IncludeAssets`, `ExcludeAssets`, and `PrivateAssets`.</span></span>

<span data-ttu-id="d2b6e-393">Aşağıdaki örnekteki proje dosyası kod parçacığı adlı bir projeye başvurur `Project2` .</span><span class="sxs-lookup"><span data-stu-id="d2b6e-393">The project file snippet in the following example references a project named `Project2`.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\Project2.csproj" />
</ItemGroup>
```

### <a name="reference"></a><span data-ttu-id="d2b6e-394">Başvuru</span><span class="sxs-lookup"><span data-stu-id="d2b6e-394">Reference</span></span>

<span data-ttu-id="d2b6e-395">`Reference`Öğe, derleme dosyasına bir başvuru tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-395">The `Reference` item defines a reference to an assembly file.</span></span>

<span data-ttu-id="d2b6e-396">`Include`Öznitelik, dosyanın adını belirtir ve `HintPath` meta veriler derlemenin yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-396">The `Include` attribute specifies the name of the file, and the `HintPath` metadata specifies the path to the assembly.</span></span>

```xml
<ItemGroup>
  <Reference Include="MyAssembly">
    <HintPath>..\..\Assemblies\MyAssembly.dll</HintPath>
  </Reference>
</ItemGroup>
```

### <a name="restore-related-properties"></a><span data-ttu-id="d2b6e-397">Geri yükleme ile ilgili özellikler</span><span class="sxs-lookup"><span data-stu-id="d2b6e-397">Restore-related properties</span></span>

<span data-ttu-id="d2b6e-398">Başvurulan bir paketin geri yüklenmesi, tüm doğrudan bağımlılıklarını ve bu bağımlılıkların tüm bağımlılıklarını yükler.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-398">Restoring a referenced package installs all of its direct dependencies and all the dependencies of those dependencies.</span></span> <span data-ttu-id="d2b6e-399">Ve gibi özellikler belirterek paket geri yüklemesini özelleştirebilirsiniz `RestorePackagesPath` `RestoreIgnoreFailedSources` .</span><span class="sxs-lookup"><span data-stu-id="d2b6e-399">You can customize package restoration by specifying properties such as `RestorePackagesPath` and `RestoreIgnoreFailedSources`.</span></span> <span data-ttu-id="d2b6e-400">Bu ve diğer özellikler hakkında daha fazla bilgi için bkz. [hedefi geri yükleme](/nuget/reference/msbuild-targets#restore-target).</span><span class="sxs-lookup"><span data-stu-id="d2b6e-400">For more information about these and other properties, see [restore target](/nuget/reference/msbuild-targets#restore-target).</span></span>

```xml
<PropertyGroup>
  <RestoreIgnoreFailedSource>true</RestoreIgnoreFailedSource>
</PropertyGroup>
```

## <a name="run-properties"></a><span data-ttu-id="d2b6e-401">Çalıştırma özellikleri</span><span class="sxs-lookup"><span data-stu-id="d2b6e-401">Run properties</span></span>

<span data-ttu-id="d2b6e-402">Aşağıdaki özellikler, komutuyla bir uygulama başlatmak için kullanılır [`dotnet run`](../tools/dotnet-run.md) :</span><span class="sxs-lookup"><span data-stu-id="d2b6e-402">The following properties are used for launching an app with the [`dotnet run`](../tools/dotnet-run.md) command:</span></span>

- [<span data-ttu-id="d2b6e-403">RunArguments</span><span class="sxs-lookup"><span data-stu-id="d2b6e-403">RunArguments</span></span>](#runarguments)
- [<span data-ttu-id="d2b6e-404">RunWorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="d2b6e-404">RunWorkingDirectory</span></span>](#runworkingdirectory)

### <a name="runarguments"></a><span data-ttu-id="d2b6e-405">RunArguments</span><span class="sxs-lookup"><span data-stu-id="d2b6e-405">RunArguments</span></span>

<span data-ttu-id="d2b6e-406">`RunArguments`Özelliği, çalıştırıldığında uygulamaya geçirilen bağımsız değişkenleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-406">The `RunArguments` property defines the arguments that are passed to the app when it is run.</span></span>

```xml
<PropertyGroup>
  <RunArguments>-mode dryrun</RunArguments>
</PropertyGroup>
```

> [!TIP]
> <span data-ttu-id="d2b6e-407">[ `--` Seçeneğini `dotnet run` ](../tools/dotnet-run.md#options)kullanarak uygulamaya geçirilecek ek bağımsız değişkenler belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-407">You can specify additional arguments to be passed to the app by using the [`--` option for `dotnet run`](../tools/dotnet-run.md#options).</span></span>

### <a name="runworkingdirectory"></a><span data-ttu-id="d2b6e-408">RunWorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="d2b6e-408">RunWorkingDirectory</span></span>

<span data-ttu-id="d2b6e-409">`RunWorkingDirectory`Özelliği, uygulamasında başlatılacak uygulama işleminin çalışma dizinini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-409">The `RunWorkingDirectory` property defines the working directory for the application process to be started in.</span></span> <span data-ttu-id="d2b6e-410">Bu, mutlak bir yol veya proje diziniyle ilişkili bir yol olabilir.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-410">It can be an absolute path or a path that's relative to the project directory.</span></span> <span data-ttu-id="d2b6e-411">Bir dizin belirtmezseniz, `OutDir` çalışma dizini olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-411">If you don't specify a directory, `OutDir` is used as the working directory.</span></span>

```xml
<PropertyGroup>
  <RunWorkingDirectory>c:\temp</RunWorkingDirectory>
</PropertyGroup>
```

## <a name="hosting-properties"></a><span data-ttu-id="d2b6e-412">Barındırma özellikleri</span><span class="sxs-lookup"><span data-stu-id="d2b6e-412">Hosting properties</span></span>

- [<span data-ttu-id="d2b6e-413">EnableComHosting</span><span class="sxs-lookup"><span data-stu-id="d2b6e-413">EnableComHosting</span></span>](#enablecomhosting)
- [<span data-ttu-id="d2b6e-414">EnableDynamicLoading</span><span class="sxs-lookup"><span data-stu-id="d2b6e-414">EnableDynamicLoading</span></span>](#enabledynamicloading)

### <a name="enablecomhosting"></a><span data-ttu-id="d2b6e-415">EnableComHosting</span><span class="sxs-lookup"><span data-stu-id="d2b6e-415">EnableComHosting</span></span>

<span data-ttu-id="d2b6e-416">Özelliği, bir `EnableComHosting` derlemenin BIR com sunucusu sağladığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-416">The `EnableComHosting` property indicates that an assembly provides a COM server.</span></span> <span data-ttu-id="d2b6e-417">İçin ayarı `EnableComHosting` , `true` [EnableDynamicLoading](#enabledynamicloading) olduğunu da belirtir `true` .</span><span class="sxs-lookup"><span data-stu-id="d2b6e-417">Setting the `EnableComHosting` to `true` also implies that [EnableDynamicLoading](#enabledynamicloading) is `true`.</span></span>

```xml
<PropertyGroup>
  <EnableComHosting>True</EnableComHosting>
</PropertyGroup>
```

<span data-ttu-id="d2b6e-418">Daha fazla bilgi için bkz. [.net BILEŞENLERINI com 'Da kullanıma](../native-interop/expose-components-to-com.md)sunma.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-418">For more information, see [Expose .NET components to COM](../native-interop/expose-components-to-com.md).</span></span>

### <a name="enabledynamicloading"></a><span data-ttu-id="d2b6e-419">EnableDynamicLoading</span><span class="sxs-lookup"><span data-stu-id="d2b6e-419">EnableDynamicLoading</span></span>

<span data-ttu-id="d2b6e-420">`EnableDynamicLoading`Özelliği, bir derlemenin dinamik olarak yüklenen bir bileşen olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-420">The `EnableDynamicLoading` property indicates that an assembly is a dynamically loaded component.</span></span> <span data-ttu-id="d2b6e-421">Bileşen bir [com kitaplığı](/windows/win32/com/the-component-object-model) veya [Yerel BIR konaktan kullanılabilecek](../tutorials/netcore-hosting.md)com olmayan bir kitaplık olabilir.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-421">The component could be a [COM library](/windows/win32/com/the-component-object-model) or a non-COM library that can be [used from a native host](../tutorials/netcore-hosting.md).</span></span> <span data-ttu-id="d2b6e-422">Bu özelliğin olarak ayarlanması `true` aşağıdaki etkilere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="d2b6e-422">Setting this property to `true` has the following effects:</span></span>

- <span data-ttu-id="d2b6e-423">Dosyadaki bir *.runtimeconfig.js* oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-423">A *.runtimeconfig.json* file is generated.</span></span>
- <span data-ttu-id="d2b6e-424">[Ileri alma](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward) , olarak ayarlanır `LatestMinor` .</span><span class="sxs-lookup"><span data-stu-id="d2b6e-424">[Roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward) is set to `LatestMinor`.</span></span>
- <span data-ttu-id="d2b6e-425">NuGet başvuruları yerel olarak kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-425">NuGet references are copied locally.</span></span>

```xml
<PropertyGroup>
  <EnableDynamicLoading>true</EnableDynamicLoading>
</PropertyGroup>
```

## <a name="see-also"></a><span data-ttu-id="d2b6e-426">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2b6e-426">See also</span></span>

- [<span data-ttu-id="d2b6e-427">MSBuild şema başvurusu</span><span class="sxs-lookup"><span data-stu-id="d2b6e-427">MSBuild schema reference</span></span>](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [<span data-ttu-id="d2b6e-428">Ortak MSBuild özellikleri</span><span class="sxs-lookup"><span data-stu-id="d2b6e-428">Common MSBuild properties</span></span>](/visualstudio/msbuild/common-msbuild-project-properties)
- [<span data-ttu-id="d2b6e-429">NuGet paketi için MSBuild özellikleri</span><span class="sxs-lookup"><span data-stu-id="d2b6e-429">MSBuild properties for NuGet pack</span></span>](/nuget/reference/msbuild-targets#pack-target)
- [<span data-ttu-id="d2b6e-430">NuGet geri yükleme için MSBuild özellikleri</span><span class="sxs-lookup"><span data-stu-id="d2b6e-430">MSBuild properties for NuGet restore</span></span>](/nuget/reference/msbuild-targets#restore-properties)
- [<span data-ttu-id="d2b6e-431">Bir derlemeyi özelleştirme</span><span class="sxs-lookup"><span data-stu-id="d2b6e-431">Customize a build</span></span>](/visualstudio/msbuild/customize-your-build)
