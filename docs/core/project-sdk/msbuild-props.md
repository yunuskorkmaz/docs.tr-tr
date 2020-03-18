---
title: Microsoft.NET.Sdk için MSBuild özellikleri
description: .NET Core SDK tarafından anlaşılan MSBuild özellikleri için başvuru.
ms.date: 02/14/2020
ms.topic: reference
ms.openlocfilehash: d4a204a1e0216313418d278ec3bd333f72db8751
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399184"
---
# <a name="msbuild-properties-for-net-core-sdk-projects"></a><span data-ttu-id="4015a-103">.NET Core SDK projeleri için MSBuild özellikleri</span><span class="sxs-lookup"><span data-stu-id="4015a-103">MSBuild properties for .NET Core SDK projects</span></span>

<span data-ttu-id="4015a-104">Bu sayfada .NET Core projelerini yapılandırmak için MSBuild özellikleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4015a-104">This page describes MSBuild properties for configuring .NET Core projects.</span></span>

> [!NOTE]
> <span data-ttu-id="4015a-105">Bu sayfa devam eden bir çalışmadır ve .NET Core SDK için yararlı MSBuild özelliklerinin tümlerini listelemiyor.</span><span class="sxs-lookup"><span data-stu-id="4015a-105">This page is a work in progress and does not list all of the useful MSBuild properties for the .NET Core SDK.</span></span> <span data-ttu-id="4015a-106">Ortak MSBuild özelliklerinin listesi [için](/visualstudio/msbuild/common-msbuild-project-properties)bkz.</span><span class="sxs-lookup"><span data-stu-id="4015a-106">For a list of common MSBuild properties, see [Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="framework-properties"></a><span data-ttu-id="4015a-107">Çerçeve özellikleri</span><span class="sxs-lookup"><span data-stu-id="4015a-107">Framework properties</span></span>

- [<span data-ttu-id="4015a-108">Hedef Çerçeve</span><span class="sxs-lookup"><span data-stu-id="4015a-108">TargetFramework</span></span>](#targetframework)
- [<span data-ttu-id="4015a-109">Hedef Çerçeveler</span><span class="sxs-lookup"><span data-stu-id="4015a-109">TargetFrameworks</span></span>](#targetframeworks)
- [<span data-ttu-id="4015a-110">NetStandardimplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="4015a-110">NetStandardImplicitPackageVersion</span></span>](#netstandardimplicitpackageversion)

### <a name="targetframework"></a><span data-ttu-id="4015a-111">Hedef Çerçeve</span><span class="sxs-lookup"><span data-stu-id="4015a-111">TargetFramework</span></span>

<span data-ttu-id="4015a-112">Özellik, `TargetFramework` uygulamanın hedef çerçeve sürümünü belirtir ve bu sürüm de örtülü olarak bir [meta pakete](../packages.md#metapackages)başvurur.</span><span class="sxs-lookup"><span data-stu-id="4015a-112">The `TargetFramework` property specifies the target framework version for the app, which implicitly references a [metapackage](../packages.md#metapackages).</span></span> <span data-ttu-id="4015a-113">Geçerli hedef çerçeve monikers listesi için, [SDK tarzı projelerde Hedef çerçeveleri](../../standard/frameworks.md#supported-target-framework-versions)bakın.</span><span class="sxs-lookup"><span data-stu-id="4015a-113">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="4015a-114">Daha fazla bilgi için, [SDK tarzı projelerde Hedef çerçeveleri'ne](../../standard/frameworks.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="4015a-114">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="targetframeworks"></a><span data-ttu-id="4015a-115">Hedef Çerçeveler</span><span class="sxs-lookup"><span data-stu-id="4015a-115">TargetFrameworks</span></span>

<span data-ttu-id="4015a-116">Uygulamanızın `TargetFrameworks` birden çok platformu hedeflemesini istediğinizde özelliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="4015a-116">Use the `TargetFrameworks` property when you want your app to target multiple platforms.</span></span> <span data-ttu-id="4015a-117">Geçerli hedef çerçeve monikers listesi için, [SDK tarzı projelerde Hedef çerçeveleri](../../standard/frameworks.md#supported-target-framework-versions)bakın.</span><span class="sxs-lookup"><span data-stu-id="4015a-117">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

> [!NOTE]
> <span data-ttu-id="4015a-118">(Tekil) `TargetFramework` belirtilmişse bu özellik yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="4015a-118">This property is ignored if `TargetFramework` (singular) is specified.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="4015a-119">Daha fazla bilgi için, [SDK tarzı projelerde Hedef çerçeveleri'ne](../../standard/frameworks.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="4015a-119">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="netstandardimplicitpackageversion"></a><span data-ttu-id="4015a-120">NetStandardimplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="4015a-120">NetStandardImplicitPackageVersion</span></span>

> [!NOTE]
> <span data-ttu-id="4015a-121">Bu özellik yalnızca `netstandard1.x`.</span><span class="sxs-lookup"><span data-stu-id="4015a-121">This property only applies to projects using `netstandard1.x`.</span></span> <span data-ttu-id="4015a-122">Bu kullanan `netstandard2.x`projeler için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="4015a-122">It doesn't apply to projects that use `netstandard2.x`.</span></span>

<span data-ttu-id="4015a-123">`NetStandardImplicitPackageVersion` [Metapackage](../packages.md#metapackages) sürümünden daha düşük bir çerçeve sürümü belirtmek istediğinizde özelliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="4015a-123">Use the `NetStandardImplicitPackageVersion` property when you want to specify a framework version that's lower than the [metapackage](../packages.md#metapackages) version.</span></span> <span data-ttu-id="4015a-124">Aşağıdaki örnekteki proje dosyası `netstandard1.3` hedefleri, ancak 1.6.0 sürümünü `NETStandard.Library`kullanır.</span><span class="sxs-lookup"><span data-stu-id="4015a-124">The project file in the following example targets `netstandard1.3` but uses the 1.6.0 version of `NETStandard.Library`.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.3</TargetFramework>
    <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
  </PropertyGroup>
</Project>
```

## <a name="publish-properties"></a><span data-ttu-id="4015a-125">Özellikleri yayımlama</span><span class="sxs-lookup"><span data-stu-id="4015a-125">Publish properties</span></span>

- [<span data-ttu-id="4015a-126">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="4015a-126">RuntimeIdentifier</span></span>](#runtimeidentifier)
- [<span data-ttu-id="4015a-127">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="4015a-127">RuntimeIdentifiers</span></span>](#runtimeidentifiers)
- [<span data-ttu-id="4015a-128">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="4015a-128">UseAppHost</span></span>](#useapphost)

### <a name="runtimeidentifier"></a><span data-ttu-id="4015a-129">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="4015a-129">RuntimeIdentifier</span></span>

<span data-ttu-id="4015a-130">Özellik, `RuntimeIdentifier` proje için tek bir [çalışma zamanı tanımlayıcısı (RID)](../rid-catalog.md) belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="4015a-130">The `RuntimeIdentifier` property lets you specify a single [runtime identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="4015a-131">RID, bağımsız bir dağıtımyayımlanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="4015a-131">The RID enables publishing a self-contained deployment.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
  </PropertyGroup>
</Project>
```

### <a name="runtimeidentifiers"></a><span data-ttu-id="4015a-132">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="4015a-132">RuntimeIdentifiers</span></span>

<span data-ttu-id="4015a-133">Özellik, `RuntimeIdentifiers` proje için yarı sütunlu sınırlı bir [çalışma zamanı tanımlayıcıları (RIDs)](../rid-catalog.md) listesini belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="4015a-133">The `RuntimeIdentifiers` property lets you specify a semicolon-delimited list of [runtime identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="4015a-134">Birden çok çalışma süreleri için yayımlamanız gerekiyorsa bu özelliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="4015a-134">Use this property if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="4015a-135">`RuntimeIdentifiers`doğru varlıkların grafikte olduğundan emin olmak için geri yükleme zamanında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4015a-135">`RuntimeIdentifiers` is used at restore time to ensure the right assets are in the graph.</span></span>

> [!TIP]
> <span data-ttu-id="4015a-136">`RuntimeIdentifier`(tekil) yalnızca tek bir çalışma süresi gerektiğinde daha hızlı yapılar sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="4015a-136">`RuntimeIdentifier` (singular) can provide faster builds when only a single runtime is required.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

### <a name="useapphost"></a><span data-ttu-id="4015a-137">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="4015a-137">UseAppHost</span></span>

<span data-ttu-id="4015a-138">Özellik `UseAppHost` .NET Core SDK'nın 2.1.400 sürümünde tanıtıldı.</span><span class="sxs-lookup"><span data-stu-id="4015a-138">The `UseAppHost` property was introduced in the 2.1.400 version of the .NET Core SDK.</span></span> <span data-ttu-id="4015a-139">Bir dağıtım için yerel yürütülebilir oluşturulup oluşturulmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="4015a-139">It controls whether or not a native executable is created for a deployment.</span></span> <span data-ttu-id="4015a-140">Kendi kendine yeten dağıtımlar için yerel yürütülebilir bir işlem gereklidir.</span><span class="sxs-lookup"><span data-stu-id="4015a-140">A native executable is required for self-contained deployments.</span></span>

<span data-ttu-id="4015a-141">.NET Core 3.0 ve sonraki sürümlerinde, varsayılan olarak çerçeveye bağımlı bir yürütülebilir oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="4015a-141">In .NET Core 3.0 and later versions, a framework-dependent executable is created by default.</span></span> <span data-ttu-id="4015a-142">`UseAppHost` Özelliği, yürütülebilir nesli devre dışı bırakacak şekilde `false` ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4015a-142">Set the `UseAppHost` property to `false` to disable generation of the executable.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <UseAppHost>false</UseAppHost>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="4015a-143">Dağıtım hakkında daha fazla bilgi için [bkz.](../deploying/index.md)</span><span class="sxs-lookup"><span data-stu-id="4015a-143">For more information about deployment, see [.NET Core application deployment](../deploying/index.md).</span></span>

## <a name="compile-properties"></a><span data-ttu-id="4015a-144">Özellikleri derleme</span><span class="sxs-lookup"><span data-stu-id="4015a-144">Compile properties</span></span>

### <a name="langversion"></a><span data-ttu-id="4015a-145">LangVersion</span><span class="sxs-lookup"><span data-stu-id="4015a-145">LangVersion</span></span>

<span data-ttu-id="4015a-146">Özellik, `LangVersion` belirli bir programlama dili sürümünü belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="4015a-146">The `LangVersion` property lets you specify a specific programming language version.</span></span> <span data-ttu-id="4015a-147">Örneğin, C# önizleme özelliklerine erişmek istiyorsanız, `LangVersion` `preview`' e ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4015a-147">For example, if you want access to C# preview features, set `LangVersion` to `preview`.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <LangVersion>preview</LangVersion>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="4015a-148">Daha fazla bilgi için [C# dil sürümüne](../../csharp/language-reference/configure-language-version.md#override-a-default)bakın.</span><span class="sxs-lookup"><span data-stu-id="4015a-148">For more information, see [C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).</span></span>

## <a name="nuget-packages"></a><span data-ttu-id="4015a-149">NuGet paketleri</span><span class="sxs-lookup"><span data-stu-id="4015a-149">NuGet packages</span></span>

- [<span data-ttu-id="4015a-150">PaketReferans</span><span class="sxs-lookup"><span data-stu-id="4015a-150">PackageReference</span></span>](#packagereference)
- [<span data-ttu-id="4015a-151">VarlıkTargetFallback</span><span class="sxs-lookup"><span data-stu-id="4015a-151">AssetTargetFallback</span></span>](#assettargetfallback)

### <a name="packagereference"></a><span data-ttu-id="4015a-152">PaketReferans</span><span class="sxs-lookup"><span data-stu-id="4015a-152">PackageReference</span></span>

<span data-ttu-id="4015a-153">Öğe, `PackageReference` bir NuGet bağımlılığı belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="4015a-153">The `PackageReference` item lets you specify a NuGet dependency.</span></span> <span data-ttu-id="4015a-154">Örneğin, [meta paket](../packages.md#metapackages)yerine tek bir pakete başvurmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4015a-154">For example, you may want to reference a single package instead of a [metapackage](../packages.md#metapackages).</span></span> <span data-ttu-id="4015a-155">Öznitelik `Include` paket kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4015a-155">The `Include` attribute specifies the package ID.</span></span> <span data-ttu-id="4015a-156">Aşağıdaki örnekteki proje dosyası snippet [System.Runtime](https://www.nuget.org/packages/System.Runtime/) paketine başvurur.</span><span class="sxs-lookup"><span data-stu-id="4015a-156">The project file snippet in the following example references the [System.Runtime](https://www.nuget.org/packages/System.Runtime/) package.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <ItemGroup>
    <PackageReference Include="System.Runtime" Version="4.3.0" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="4015a-157">Daha fazla bilgi için [proje dosyalarındaki Paket başvurularına](/nuget/consume-packages/package-references-in-project-files)bakın.</span><span class="sxs-lookup"><span data-stu-id="4015a-157">For more information, see [Package references in project files](/nuget/consume-packages/package-references-in-project-files).</span></span>

### <a name="assettargetfallback"></a><span data-ttu-id="4015a-158">VarlıkTargetFallback</span><span class="sxs-lookup"><span data-stu-id="4015a-158">AssetTargetFallback</span></span>

<span data-ttu-id="4015a-159">Özellik, `AssetTargetFallback` projenizin başvurulup tükettiği projeler ve NuGet paketleri için ek uyumlu çerçeve sürümleri belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="4015a-159">The `AssetTargetFallback` property lets you specify additional compatible framework versions for projects that your project references and NuGet packages that your project consumes.</span></span> <span data-ttu-id="4015a-160">Örneğin, bir paket bağımlılığı nı `PackageReference` kullanarak belirtirseniz, ancak bu paket projelerinizinkiyle `TargetFramework`uyumlu `AssetTargetFallback` varlıklar içermiyorsa, özellik devreye girer.</span><span class="sxs-lookup"><span data-stu-id="4015a-160">For example, if you specify a package dependency using `PackageReference` but that package doesn't contain assets that are compatible with your projects's `TargetFramework`, the `AssetTargetFallback` property comes into play.</span></span> <span data-ttu-id="4015a-161">Başvurulan paketin uyumluluğu, ''' `AssetTargetFallback`'de belirtilen her hedef çerçeve kullanılarak yeniden denetlenir.</span><span class="sxs-lookup"><span data-stu-id="4015a-161">The compatibility of the referenced package is rechecked using each target framework that's specified in `AssetTargetFallback`.</span></span>

<span data-ttu-id="4015a-162">Özelliği bir veya daha fazla [hedef çerçeve sürümüne](../../standard/frameworks.md#supported-target-framework-versions)ayarlayabilirsiniz. `AssetTargetFallback`</span><span class="sxs-lookup"><span data-stu-id="4015a-162">You can set the `AssetTargetFallback` property to one or more [target framework versions](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <PropertyGroup>
    <AssetTargetFallback>net461</AssetTargetFallback>
  </PropertyGroup>
</Project>
```

### <a name="pack-and-restore-targets"></a><span data-ttu-id="4015a-163">Hedefleri paketleme ve geri yükleme</span><span class="sxs-lookup"><span data-stu-id="4015a-163">Pack and restore targets</span></span>

<span data-ttu-id="4015a-164">MSBuild 15.1 `pack` tanıtıldı `restore` ve nuget paketleri oluşturmak ve bir yapının parçası olarak geri için hedefler.</span><span class="sxs-lookup"><span data-stu-id="4015a-164">MSBuild 15.1 introduced `pack` and `restore` targets for creating and restoring NuGet packages as part of a build.</span></span> <span data-ttu-id="4015a-165">Bu hedefler için MSBuild özellikleri hakkında `PackageTargetFallback`bilgi için, [bkz.](/nuget/reference/msbuild-targets)</span><span class="sxs-lookup"><span data-stu-id="4015a-165">For information about the MSBuild properties for these targets, including `PackageTargetFallback`, see [NuGet pack and restore as MSBuild targets](/nuget/reference/msbuild-targets).</span></span>

## <a name="see-also"></a><span data-ttu-id="4015a-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4015a-166">See also</span></span>

- [<span data-ttu-id="4015a-167">MSBuild şema başvurusu</span><span class="sxs-lookup"><span data-stu-id="4015a-167">MSBuild schema reference</span></span>](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [<span data-ttu-id="4015a-168">Ortak MSBuild özellikleri</span><span class="sxs-lookup"><span data-stu-id="4015a-168">Common MSBuild properties</span></span>](/visualstudio/msbuild/common-msbuild-project-properties)
- [<span data-ttu-id="4015a-169">NuGet paketi için MSBuild özellikleri</span><span class="sxs-lookup"><span data-stu-id="4015a-169">MSBuild properties for NuGet pack</span></span>](/nuget/reference/msbuild-targets#pack-target)
- [<span data-ttu-id="4015a-170">NuGet geri yüklemesi için MSBuild özellikleri</span><span class="sxs-lookup"><span data-stu-id="4015a-170">MSBuild properties for NuGet restore</span></span>](/nuget/reference/msbuild-targets#restore-properties)
- [<span data-ttu-id="4015a-171">Yapıyı özelleştirme</span><span class="sxs-lookup"><span data-stu-id="4015a-171">Customize a build</span></span>](/visualstudio/msbuild/customize-your-build)
