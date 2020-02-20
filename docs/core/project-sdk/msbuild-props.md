---
title: Microsoft. NET. SDK için MSBuild özellikleri
description: .NET Core SDK anlayan MSBuild özelliklerine yönelik başvuru.
ms.date: 02/02/2020
ms.topic: reference
ms.openlocfilehash: f5dc2079bc313b8dd9fa5556cd941521a597ae38
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453813"
---
# <a name="msbuild-properties-for-net-core-sdk-projects"></a><span data-ttu-id="33ff4-103">.NET Core SDK projeleri için MSBuild özellikleri</span><span class="sxs-lookup"><span data-stu-id="33ff4-103">MSBuild properties for .NET Core SDK projects</span></span>

<span data-ttu-id="33ff4-104">Bu sayfa, .NET Core projelerini yapılandırmaya yönelik MSBuild özelliklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="33ff4-104">This page describes MSBuild properties for configuring .NET Core projects.</span></span>

> [!NOTE]
> <span data-ttu-id="33ff4-105">Bu sayfa devam eden bir çalışmadır ve .NET Core SDK için tüm yararlı MSBuild özelliklerini listelemez.</span><span class="sxs-lookup"><span data-stu-id="33ff4-105">This page is a work in progress and does not list all of the useful MSBuild properties for the .NET Core SDK.</span></span> <span data-ttu-id="33ff4-106">Ortak MSBuild özelliklerinin bir listesi için bkz. [Ortak MSBuild özellikleri](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="33ff4-106">For a list of common MSBuild properties, see [Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="framework-properties"></a><span data-ttu-id="33ff4-107">Çerçeve özellikleri</span><span class="sxs-lookup"><span data-stu-id="33ff4-107">Framework properties</span></span>

- [<span data-ttu-id="33ff4-108">Netstandardımplicitpackageversion</span><span class="sxs-lookup"><span data-stu-id="33ff4-108">NetStandardImplicitPackageVersion</span></span>](#netstandardimplicitpackageversion)
- [<span data-ttu-id="33ff4-109">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="33ff4-109">TargetFramework</span></span>](#targetframework)
- [<span data-ttu-id="33ff4-110">Targetçerçeveler</span><span class="sxs-lookup"><span data-stu-id="33ff4-110">TargetFrameworks</span></span>](#targetframeworks)

### <a name="netstandardimplicitpackageversion"></a><span data-ttu-id="33ff4-111">Netstandardımplicitpackageversion</span><span class="sxs-lookup"><span data-stu-id="33ff4-111">NetStandardImplicitPackageVersion</span></span>

> [!NOTE]
> <span data-ttu-id="33ff4-112">Bu özellik yalnızca `netstandard1.x`kullanan projeler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="33ff4-112">This property only applies to projects using `netstandard1.x`.</span></span> <span data-ttu-id="33ff4-113">`netstandard2` ve üstünü kullanan projeler için uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="33ff4-113">It doesn't apply to projects that use `netstandard2` and later.</span></span>

<span data-ttu-id="33ff4-114">[Metapackage](../packages.md#metapackages) sürümünden daha düşük bir çerçeve sürümü belirtmek istediğinizde `NetStandardImplicitPackageVersion` özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="33ff4-114">Use the `NetStandardImplicitPackageVersion` property when you want to specify a framework version that's lower than the [metapackage](../packages.md#metapackages) version.</span></span> <span data-ttu-id="33ff4-115">Aşağıdaki örnekteki proje dosyası `netstandard1.3` hedefler, ancak `NETStandard.Library`1.6.0 sürümünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="33ff4-115">The project file in the following example targets `netstandard1.3` but uses the 1.6.0 version of `NETStandard.Library`.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.3</TargetFramework>
    <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
  </PropertyGroup>
</Project>
```

### <a name="targetframework"></a><span data-ttu-id="33ff4-116">targetFramework</span><span class="sxs-lookup"><span data-stu-id="33ff4-116">TargetFramework</span></span>

<span data-ttu-id="33ff4-117">`TargetFramework` özelliği, uygulamanın hedef Framework sürümünü belirtir ve bu, dolaylı olarak bir [metapackage](../packages.md#metapackages)'e başvurur.</span><span class="sxs-lookup"><span data-stu-id="33ff4-117">The `TargetFramework` property specifies the target framework version for the app, which implicitly references a [metapackage](../packages.md#metapackages).</span></span> <span data-ttu-id="33ff4-118">Geçerli hedef çerçeve takma adların listesi için bkz. [SDK stili projelerde hedef çerçeveler](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="33ff4-118">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="33ff4-119">Daha fazla bilgi için bkz. [SDK stili projelerde hedef çerçeveler](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="33ff4-119">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="targetframeworks"></a><span data-ttu-id="33ff4-120">Targetçerçeveler</span><span class="sxs-lookup"><span data-stu-id="33ff4-120">TargetFrameworks</span></span>

<span data-ttu-id="33ff4-121">Uygulamanızın birden çok platformu hedeflemesini istediğinizde `TargetFrameworks` özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="33ff4-121">Use the `TargetFrameworks` property when you want your app to target multiple platforms.</span></span> <span data-ttu-id="33ff4-122">Geçerli hedef çerçeve takma adların listesi için bkz. [SDK stili projelerde hedef çerçeveler](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="33ff4-122">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

> [!NOTE]
> <span data-ttu-id="33ff4-123">`TargetFramework` (tekil) belirtilmişse bu özellik yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="33ff4-123">This property is ignored if `TargetFramework` (singular) is specified.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="33ff4-124">Daha fazla bilgi için bkz. [SDK stili projelerde hedef çerçeveler](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="33ff4-124">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

## <a name="publish-properties"></a><span data-ttu-id="33ff4-125">Özellikleri Yayımla</span><span class="sxs-lookup"><span data-stu-id="33ff4-125">Publish properties</span></span>

- [<span data-ttu-id="33ff4-126">Runtimeıdentifier</span><span class="sxs-lookup"><span data-stu-id="33ff4-126">RuntimeIdentifier</span></span>](#runtimeidentifier)
- [<span data-ttu-id="33ff4-127">Runtimetanımlayıcıtanımlayıcıları</span><span class="sxs-lookup"><span data-stu-id="33ff4-127">RuntimeIdentifiers</span></span>](#runtimeidentifiers)
- [<span data-ttu-id="33ff4-128">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="33ff4-128">UseAppHost</span></span>](#useapphost)

### <a name="runtimeidentifier"></a><span data-ttu-id="33ff4-129">Runtimeıdentifier</span><span class="sxs-lookup"><span data-stu-id="33ff4-129">RuntimeIdentifier</span></span>

<span data-ttu-id="33ff4-130">`RuntimeIdentifier` özelliği, proje için tek bir [çalışma zamanı tanımlayıcısı (RID)](../rid-catalog.md) belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="33ff4-130">The `RuntimeIdentifier` property lets you specify a single [runtime identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="33ff4-131">RID, kendi kendine içerilen bir dağıtımı yayımlamayı mümkün.</span><span class="sxs-lookup"><span data-stu-id="33ff4-131">The RID enables publishing a self-contained deployment.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
  </PropertyGroup>
</Project>
```

### <a name="runtimeidentifiers"></a><span data-ttu-id="33ff4-132">Runtimetanımlayıcıtanımlayıcıları</span><span class="sxs-lookup"><span data-stu-id="33ff4-132">RuntimeIdentifiers</span></span>

<span data-ttu-id="33ff4-133">`RuntimeIdentifiers` özelliği, proje için bir [çalışma zamanı tanımlayıcıları (RID 'ler)](../rid-catalog.md) için noktalı virgülle ayrılmış bir liste belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="33ff4-133">The `RuntimeIdentifiers` property lets you specify a semicolon-delimited list of [runtime identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="33ff4-134">Birden çok çalışma zamanı için yayımlamanız gerekiyorsa bu özelliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="33ff4-134">Use this property if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="33ff4-135">`RuntimeIdentifiers`, doğru varlıkların grafikte olduğundan emin olmak için geri yükleme sırasında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="33ff4-135">`RuntimeIdentifiers` is used at restore time to ensure the right assets are in the graph.</span></span>

> [!TIP]
> <span data-ttu-id="33ff4-136">`RuntimeIdentifier` (tekil), yalnızca tek bir çalışma zamanı gerektiğinde daha hızlı derlemeler sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="33ff4-136">`RuntimeIdentifier` (singular) can provide faster builds when only a single runtime is required.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

### <a name="useapphost"></a><span data-ttu-id="33ff4-137">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="33ff4-137">UseAppHost</span></span>

<span data-ttu-id="33ff4-138">`UseAppHost` özelliği .NET Core SDK 2.1.400 sürümünde tanıtılmıştı.</span><span class="sxs-lookup"><span data-stu-id="33ff4-138">The `UseAppHost` property was introduced in the 2.1.400 version of the .NET Core SDK.</span></span> <span data-ttu-id="33ff4-139">Dağıtım için yerel bir yürütülebilir dosyanın oluşturulup oluşturulmayacağını denetler.</span><span class="sxs-lookup"><span data-stu-id="33ff4-139">It controls whether or not a native executable is created for a deployment.</span></span> <span data-ttu-id="33ff4-140">Kendi kendine kapsanan dağıtımlar için yerel bir yürütülebilir dosya gereklidir.</span><span class="sxs-lookup"><span data-stu-id="33ff4-140">A native executable is required for self-contained deployments.</span></span>

<span data-ttu-id="33ff4-141">.NET Core 3,0 ve sonraki sürümlerinde, çerçeveye bağlı bir yürütülebilir dosya varsayılan olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="33ff4-141">In .NET Core 3.0 and later versions, a framework-dependent executable is created by default.</span></span> <span data-ttu-id="33ff4-142">Yürütülebilir dosyanın üretilmesini devre dışı bırakmak için `UseAppHost` özelliğini `false` olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="33ff4-142">Set the `UseAppHost` property to `false` to disable generation of the executable.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <UseAppHost>false</UseAppHost>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="33ff4-143">Dağıtım hakkında daha fazla bilgi için bkz. [.NET Core uygulama dağıtımı](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="33ff4-143">For more information about deployment, see [.NET Core application deployment](../deploying/index.md).</span></span>

## <a name="compile-properties"></a><span data-ttu-id="33ff4-144">Derleme özellikleri</span><span class="sxs-lookup"><span data-stu-id="33ff4-144">Compile properties</span></span>

### <a name="langversion"></a><span data-ttu-id="33ff4-145">LangVersion</span><span class="sxs-lookup"><span data-stu-id="33ff4-145">LangVersion</span></span>

<span data-ttu-id="33ff4-146">`LangVersion` özelliği, belirli bir programlama dili sürümü belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="33ff4-146">The `LangVersion` property lets you specify a specific programming language version.</span></span> <span data-ttu-id="33ff4-147">Örneğin, C# önizleme özelliklerine erişmek istiyorsanız `LangVersion` `preview`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="33ff4-147">For example, if you want access to C# preview features, set `LangVersion` to `preview`.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <LangVersion>preview</LangVersion>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="33ff4-148">Daha fazla bilgi için bkz [ C# . dil sürümü oluşturma](../../csharp/language-reference/configure-language-version.md#override-a-default).</span><span class="sxs-lookup"><span data-stu-id="33ff4-148">For more information, see [C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).</span></span>

## <a name="nuget-packages"></a><span data-ttu-id="33ff4-149">NuGet paketleri</span><span class="sxs-lookup"><span data-stu-id="33ff4-149">NuGet packages</span></span>

- [<span data-ttu-id="33ff4-150">PackageReference</span><span class="sxs-lookup"><span data-stu-id="33ff4-150">PackageReference</span></span>](#packagereference)

### <a name="packagereference"></a><span data-ttu-id="33ff4-151">PackageReference</span><span class="sxs-lookup"><span data-stu-id="33ff4-151">PackageReference</span></span>

<span data-ttu-id="33ff4-152">`PackageReference` öğesi bir NuGet bağımlılığı belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="33ff4-152">The `PackageReference` item lets you specify a NuGet dependency.</span></span> <span data-ttu-id="33ff4-153">Örneğin, [metapackage](../packages.md#metapackages)yerine tek bir pakete başvurmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="33ff4-153">For example, you may want to reference a single package instead of a [metapackage](../packages.md#metapackages).</span></span> <span data-ttu-id="33ff4-154">`Include` özniteliği paket KIMLIĞINI belirtir.</span><span class="sxs-lookup"><span data-stu-id="33ff4-154">The `Include` attribute specifies the package ID.</span></span> <span data-ttu-id="33ff4-155">Aşağıdaki örnekteki proje dosyası kod parçacığı [System. Runtime](https://www.nuget.org/packages/System.Runtime/) paketine başvurur.</span><span class="sxs-lookup"><span data-stu-id="33ff4-155">The project file snippet in the following example references the [System.Runtime](https://www.nuget.org/packages/System.Runtime/) package.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <ItemGroup>
    <PackageReference Include="System.Runtime" Version="4.3.0" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="33ff4-156">Daha fazla bilgi için bkz. [Proje dosyalarındaki paket başvuruları](/nuget/consume-packages/package-references-in-project-files).</span><span class="sxs-lookup"><span data-stu-id="33ff4-156">For more information, see [Package references in project files](/nuget/consume-packages/package-references-in-project-files).</span></span>

### <a name="pack-and-restore-targets"></a><span data-ttu-id="33ff4-157">Paket ve geri yükleme hedefleri</span><span class="sxs-lookup"><span data-stu-id="33ff4-157">Pack and restore targets</span></span>

<span data-ttu-id="33ff4-158">MSBuild 15,1, bir derleme kapsamında NuGet paketleri oluşturmak ve geri yüklemek için `pack` ve `restore` hedeflerinin tanıtılmıştır.</span><span class="sxs-lookup"><span data-stu-id="33ff4-158">MSBuild 15.1 introduced `pack` and `restore` targets for creating and restoring NuGet packages as part of a build.</span></span> <span data-ttu-id="33ff4-159">`PackageTargetFallback`da dahil olmak üzere bu hedeflerin MSBuild özellikleri hakkında bilgi için bkz. [NuGet Pack ve geri yükleme MSBuild hedefleri olarak](/nuget/reference/msbuild-targets).</span><span class="sxs-lookup"><span data-stu-id="33ff4-159">For information about the MSBuild properties for these targets, including `PackageTargetFallback`, see [NuGet pack and restore as MSBuild targets](/nuget/reference/msbuild-targets).</span></span>

## <a name="see-also"></a><span data-ttu-id="33ff4-160">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="33ff4-160">See also</span></span>

- [<span data-ttu-id="33ff4-161">MSBuild şema başvurusu</span><span class="sxs-lookup"><span data-stu-id="33ff4-161">MSBuild schema reference</span></span>](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [<span data-ttu-id="33ff4-162">Ortak MSBuild özellikleri</span><span class="sxs-lookup"><span data-stu-id="33ff4-162">Common MSBuild properties</span></span>](/visualstudio/msbuild/common-msbuild-project-properties)
- [<span data-ttu-id="33ff4-163">NuGet paketi için MSBuild özellikleri</span><span class="sxs-lookup"><span data-stu-id="33ff4-163">MSBuild properties for NuGet pack</span></span>](/nuget/reference/msbuild-targets#pack-target)
- [<span data-ttu-id="33ff4-164">NuGet geri yükleme için MSBuild özellikleri</span><span class="sxs-lookup"><span data-stu-id="33ff4-164">MSBuild properties for NuGet restore</span></span>](/nuget/reference/msbuild-targets#restore-properties)
- [<span data-ttu-id="33ff4-165">Bir derlemeyi özelleştirme</span><span class="sxs-lookup"><span data-stu-id="33ff4-165">Customize a build</span></span>](/visualstudio/msbuild/customize-your-build)
