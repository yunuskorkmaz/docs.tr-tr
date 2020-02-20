---
title: Microsoft. NET. SDK için MSBuild özellikleri
description: .NET Core SDK anlayan MSBuild özelliklerine yönelik başvuru.
ms.date: 02/14/2020
ms.topic: reference
ms.openlocfilehash: 00d9152d864ac0727a511f4c3c15abba82aab904
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503815"
---
# <a name="msbuild-properties-for-net-core-sdk-projects"></a><span data-ttu-id="95b73-103">.NET Core SDK projeleri için MSBuild özellikleri</span><span class="sxs-lookup"><span data-stu-id="95b73-103">MSBuild properties for .NET Core SDK projects</span></span>

<span data-ttu-id="95b73-104">Bu sayfa, .NET Core projelerini yapılandırmaya yönelik MSBuild özelliklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="95b73-104">This page describes MSBuild properties for configuring .NET Core projects.</span></span>

> [!NOTE]
> <span data-ttu-id="95b73-105">Bu sayfa devam eden bir çalışmadır ve .NET Core SDK için tüm yararlı MSBuild özelliklerini listelemez.</span><span class="sxs-lookup"><span data-stu-id="95b73-105">This page is a work in progress and does not list all of the useful MSBuild properties for the .NET Core SDK.</span></span> <span data-ttu-id="95b73-106">Ortak MSBuild özelliklerinin bir listesi için bkz. [Ortak MSBuild özellikleri](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="95b73-106">For a list of common MSBuild properties, see [Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="framework-properties"></a><span data-ttu-id="95b73-107">Çerçeve özellikleri</span><span class="sxs-lookup"><span data-stu-id="95b73-107">Framework properties</span></span>

- [<span data-ttu-id="95b73-108">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="95b73-108">TargetFramework</span></span>](#targetframework)
- [<span data-ttu-id="95b73-109">Targetçerçeveler</span><span class="sxs-lookup"><span data-stu-id="95b73-109">TargetFrameworks</span></span>](#targetframeworks)
- [<span data-ttu-id="95b73-110">Netstandardımplicitpackageversion</span><span class="sxs-lookup"><span data-stu-id="95b73-110">NetStandardImplicitPackageVersion</span></span>](#netstandardimplicitpackageversion)

### <a name="targetframework"></a><span data-ttu-id="95b73-111">targetFramework</span><span class="sxs-lookup"><span data-stu-id="95b73-111">TargetFramework</span></span>

<span data-ttu-id="95b73-112">`TargetFramework` özelliği, uygulamanın hedef Framework sürümünü belirtir ve bu, dolaylı olarak bir [metapackage](../packages.md#metapackages)'e başvurur.</span><span class="sxs-lookup"><span data-stu-id="95b73-112">The `TargetFramework` property specifies the target framework version for the app, which implicitly references a [metapackage](../packages.md#metapackages).</span></span> <span data-ttu-id="95b73-113">Geçerli hedef çerçeve takma adların listesi için bkz. [SDK stili projelerde hedef çerçeveler](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="95b73-113">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="95b73-114">Daha fazla bilgi için bkz. [SDK stili projelerde hedef çerçeveler](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="95b73-114">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="targetframeworks"></a><span data-ttu-id="95b73-115">Targetçerçeveler</span><span class="sxs-lookup"><span data-stu-id="95b73-115">TargetFrameworks</span></span>

<span data-ttu-id="95b73-116">Uygulamanızın birden çok platformu hedeflemesini istediğinizde `TargetFrameworks` özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="95b73-116">Use the `TargetFrameworks` property when you want your app to target multiple platforms.</span></span> <span data-ttu-id="95b73-117">Geçerli hedef çerçeve takma adların listesi için bkz. [SDK stili projelerde hedef çerçeveler](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="95b73-117">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

> [!NOTE]
> <span data-ttu-id="95b73-118">`TargetFramework` (tekil) belirtilmişse bu özellik yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="95b73-118">This property is ignored if `TargetFramework` (singular) is specified.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="95b73-119">Daha fazla bilgi için bkz. [SDK stili projelerde hedef çerçeveler](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="95b73-119">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="netstandardimplicitpackageversion"></a><span data-ttu-id="95b73-120">Netstandardımplicitpackageversion</span><span class="sxs-lookup"><span data-stu-id="95b73-120">NetStandardImplicitPackageVersion</span></span>

> [!NOTE]
> <span data-ttu-id="95b73-121">Bu özellik yalnızca `netstandard1.x`kullanan projeler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="95b73-121">This property only applies to projects using `netstandard1.x`.</span></span> <span data-ttu-id="95b73-122">`netstandard2.x`kullanan projeler için uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="95b73-122">It doesn't apply to projects that use `netstandard2.x`.</span></span>

<span data-ttu-id="95b73-123">[Metapackage](../packages.md#metapackages) sürümünden daha düşük bir çerçeve sürümü belirtmek istediğinizde `NetStandardImplicitPackageVersion` özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="95b73-123">Use the `NetStandardImplicitPackageVersion` property when you want to specify a framework version that's lower than the [metapackage](../packages.md#metapackages) version.</span></span> <span data-ttu-id="95b73-124">Aşağıdaki örnekteki proje dosyası `netstandard1.3` hedefler, ancak `NETStandard.Library`1.6.0 sürümünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="95b73-124">The project file in the following example targets `netstandard1.3` but uses the 1.6.0 version of `NETStandard.Library`.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.3</TargetFramework>
    <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
  </PropertyGroup>
</Project>
```

## <a name="publish-properties"></a><span data-ttu-id="95b73-125">Özellikleri Yayımla</span><span class="sxs-lookup"><span data-stu-id="95b73-125">Publish properties</span></span>

- [<span data-ttu-id="95b73-126">Runtimeıdentifier</span><span class="sxs-lookup"><span data-stu-id="95b73-126">RuntimeIdentifier</span></span>](#runtimeidentifier)
- [<span data-ttu-id="95b73-127">Runtimetanımlayıcıtanımlayıcıları</span><span class="sxs-lookup"><span data-stu-id="95b73-127">RuntimeIdentifiers</span></span>](#runtimeidentifiers)
- [<span data-ttu-id="95b73-128">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="95b73-128">UseAppHost</span></span>](#useapphost)

### <a name="runtimeidentifier"></a><span data-ttu-id="95b73-129">Runtimeıdentifier</span><span class="sxs-lookup"><span data-stu-id="95b73-129">RuntimeIdentifier</span></span>

<span data-ttu-id="95b73-130">`RuntimeIdentifier` özelliği, proje için tek bir [çalışma zamanı tanımlayıcısı (RID)](../rid-catalog.md) belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="95b73-130">The `RuntimeIdentifier` property lets you specify a single [runtime identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="95b73-131">RID, kendi kendine içerilen bir dağıtımı yayımlamayı mümkün.</span><span class="sxs-lookup"><span data-stu-id="95b73-131">The RID enables publishing a self-contained deployment.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
  </PropertyGroup>
</Project>
```

### <a name="runtimeidentifiers"></a><span data-ttu-id="95b73-132">Runtimetanımlayıcıtanımlayıcıları</span><span class="sxs-lookup"><span data-stu-id="95b73-132">RuntimeIdentifiers</span></span>

<span data-ttu-id="95b73-133">`RuntimeIdentifiers` özelliği, proje için bir [çalışma zamanı tanımlayıcıları (RID 'ler)](../rid-catalog.md) için noktalı virgülle ayrılmış bir liste belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="95b73-133">The `RuntimeIdentifiers` property lets you specify a semicolon-delimited list of [runtime identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="95b73-134">Birden çok çalışma zamanı için yayımlamanız gerekiyorsa bu özelliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="95b73-134">Use this property if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="95b73-135">`RuntimeIdentifiers`, doğru varlıkların grafikte olduğundan emin olmak için geri yükleme sırasında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="95b73-135">`RuntimeIdentifiers` is used at restore time to ensure the right assets are in the graph.</span></span>

> [!TIP]
> <span data-ttu-id="95b73-136">`RuntimeIdentifier` (tekil), yalnızca tek bir çalışma zamanı gerektiğinde daha hızlı derlemeler sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="95b73-136">`RuntimeIdentifier` (singular) can provide faster builds when only a single runtime is required.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

### <a name="useapphost"></a><span data-ttu-id="95b73-137">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="95b73-137">UseAppHost</span></span>

<span data-ttu-id="95b73-138">`UseAppHost` özelliği .NET Core SDK 2.1.400 sürümünde tanıtılmıştı.</span><span class="sxs-lookup"><span data-stu-id="95b73-138">The `UseAppHost` property was introduced in the 2.1.400 version of the .NET Core SDK.</span></span> <span data-ttu-id="95b73-139">Dağıtım için yerel bir yürütülebilir dosyanın oluşturulup oluşturulmayacağını denetler.</span><span class="sxs-lookup"><span data-stu-id="95b73-139">It controls whether or not a native executable is created for a deployment.</span></span> <span data-ttu-id="95b73-140">Kendi kendine kapsanan dağıtımlar için yerel bir yürütülebilir dosya gereklidir.</span><span class="sxs-lookup"><span data-stu-id="95b73-140">A native executable is required for self-contained deployments.</span></span>

<span data-ttu-id="95b73-141">.NET Core 3,0 ve sonraki sürümlerinde, çerçeveye bağlı bir yürütülebilir dosya varsayılan olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="95b73-141">In .NET Core 3.0 and later versions, a framework-dependent executable is created by default.</span></span> <span data-ttu-id="95b73-142">Yürütülebilir dosyanın üretilmesini devre dışı bırakmak için `UseAppHost` özelliğini `false` olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="95b73-142">Set the `UseAppHost` property to `false` to disable generation of the executable.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <UseAppHost>false</UseAppHost>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="95b73-143">Dağıtım hakkında daha fazla bilgi için bkz. [.NET Core uygulama dağıtımı](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="95b73-143">For more information about deployment, see [.NET Core application deployment](../deploying/index.md).</span></span>

## <a name="compile-properties"></a><span data-ttu-id="95b73-144">Derleme özellikleri</span><span class="sxs-lookup"><span data-stu-id="95b73-144">Compile properties</span></span>

### <a name="langversion"></a><span data-ttu-id="95b73-145">LangVersion</span><span class="sxs-lookup"><span data-stu-id="95b73-145">LangVersion</span></span>

<span data-ttu-id="95b73-146">`LangVersion` özelliği, belirli bir programlama dili sürümü belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="95b73-146">The `LangVersion` property lets you specify a specific programming language version.</span></span> <span data-ttu-id="95b73-147">Örneğin, C# önizleme özelliklerine erişmek istiyorsanız `LangVersion` `preview`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="95b73-147">For example, if you want access to C# preview features, set `LangVersion` to `preview`.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <LangVersion>preview</LangVersion>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="95b73-148">Daha fazla bilgi için bkz [ C# . dil sürümü oluşturma](../../csharp/language-reference/configure-language-version.md#override-a-default).</span><span class="sxs-lookup"><span data-stu-id="95b73-148">For more information, see [C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).</span></span>

## <a name="nuget-packages"></a><span data-ttu-id="95b73-149">NuGet paketleri</span><span class="sxs-lookup"><span data-stu-id="95b73-149">NuGet packages</span></span>

- [<span data-ttu-id="95b73-150">PackageReference</span><span class="sxs-lookup"><span data-stu-id="95b73-150">PackageReference</span></span>](#packagereference)

### <a name="packagereference"></a><span data-ttu-id="95b73-151">PackageReference</span><span class="sxs-lookup"><span data-stu-id="95b73-151">PackageReference</span></span>

<span data-ttu-id="95b73-152">`PackageReference` öğesi bir NuGet bağımlılığı belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="95b73-152">The `PackageReference` item lets you specify a NuGet dependency.</span></span> <span data-ttu-id="95b73-153">Örneğin, [metapackage](../packages.md#metapackages)yerine tek bir pakete başvurmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="95b73-153">For example, you may want to reference a single package instead of a [metapackage](../packages.md#metapackages).</span></span> <span data-ttu-id="95b73-154">`Include` özniteliği paket KIMLIĞINI belirtir.</span><span class="sxs-lookup"><span data-stu-id="95b73-154">The `Include` attribute specifies the package ID.</span></span> <span data-ttu-id="95b73-155">Aşağıdaki örnekteki proje dosyası kod parçacığı [System. Runtime](https://www.nuget.org/packages/System.Runtime/) paketine başvurur.</span><span class="sxs-lookup"><span data-stu-id="95b73-155">The project file snippet in the following example references the [System.Runtime](https://www.nuget.org/packages/System.Runtime/) package.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <ItemGroup>
    <PackageReference Include="System.Runtime" Version="4.3.0" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="95b73-156">Daha fazla bilgi için bkz. [Proje dosyalarındaki paket başvuruları](/nuget/consume-packages/package-references-in-project-files).</span><span class="sxs-lookup"><span data-stu-id="95b73-156">For more information, see [Package references in project files](/nuget/consume-packages/package-references-in-project-files).</span></span>

### <a name="pack-and-restore-targets"></a><span data-ttu-id="95b73-157">Paket ve geri yükleme hedefleri</span><span class="sxs-lookup"><span data-stu-id="95b73-157">Pack and restore targets</span></span>

<span data-ttu-id="95b73-158">MSBuild 15,1, bir derleme kapsamında NuGet paketleri oluşturmak ve geri yüklemek için `pack` ve `restore` hedeflerinin tanıtılmıştır.</span><span class="sxs-lookup"><span data-stu-id="95b73-158">MSBuild 15.1 introduced `pack` and `restore` targets for creating and restoring NuGet packages as part of a build.</span></span> <span data-ttu-id="95b73-159">`PackageTargetFallback`da dahil olmak üzere bu hedeflerin MSBuild özellikleri hakkında bilgi için bkz. [NuGet Pack ve geri yükleme MSBuild hedefleri olarak](/nuget/reference/msbuild-targets).</span><span class="sxs-lookup"><span data-stu-id="95b73-159">For information about the MSBuild properties for these targets, including `PackageTargetFallback`, see [NuGet pack and restore as MSBuild targets](/nuget/reference/msbuild-targets).</span></span>

## <a name="see-also"></a><span data-ttu-id="95b73-160">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="95b73-160">See also</span></span>

- [<span data-ttu-id="95b73-161">MSBuild şema başvurusu</span><span class="sxs-lookup"><span data-stu-id="95b73-161">MSBuild schema reference</span></span>](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [<span data-ttu-id="95b73-162">Ortak MSBuild özellikleri</span><span class="sxs-lookup"><span data-stu-id="95b73-162">Common MSBuild properties</span></span>](/visualstudio/msbuild/common-msbuild-project-properties)
- [<span data-ttu-id="95b73-163">NuGet paketi için MSBuild özellikleri</span><span class="sxs-lookup"><span data-stu-id="95b73-163">MSBuild properties for NuGet pack</span></span>](/nuget/reference/msbuild-targets#pack-target)
- [<span data-ttu-id="95b73-164">NuGet geri yükleme için MSBuild özellikleri</span><span class="sxs-lookup"><span data-stu-id="95b73-164">MSBuild properties for NuGet restore</span></span>](/nuget/reference/msbuild-targets#restore-properties)
- [<span data-ttu-id="95b73-165">Bir derlemeyi özelleştirme</span><span class="sxs-lookup"><span data-stu-id="95b73-165">Customize a build</span></span>](/visualstudio/msbuild/customize-your-build)
