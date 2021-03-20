---
title: Microsoft. NET. SDK için MSBuild özellikleri
description: MSBuild özellikleri ve .NET SDK tarafından anlaşılan öğeler için başvuru.
ms.date: 02/14/2020
ms.topic: reference
ms.custom: updateeachrelease
ms.openlocfilehash: f6a49a0040bcb38dbaf433f6ea53bb8aad24c65b
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759891"
---
# <a name="msbuild-reference-for-net-sdk-projects"></a><span data-ttu-id="08f67-103">.NET SDK projeleri için MSBuild başvurusu</span><span class="sxs-lookup"><span data-stu-id="08f67-103">MSBuild reference for .NET SDK projects</span></span>

<span data-ttu-id="08f67-104">Bu sayfa, MSBuild özelliklerine ve .NET projelerini yapılandırmak için kullanabileceğiniz öğelere yönelik bir başvurudur.</span><span class="sxs-lookup"><span data-stu-id="08f67-104">This page is a reference for the MSBuild properties and items that you can use to configure .NET projects.</span></span>

> [!NOTE]
> <span data-ttu-id="08f67-105">Bu sayfa devam eden bir çalışmadır ve .NET SDK için tüm kullanışlı MSBuild özelliklerini listelemez.</span><span class="sxs-lookup"><span data-stu-id="08f67-105">This page is a work in progress and does not list all of the useful MSBuild properties for the .NET SDK.</span></span> <span data-ttu-id="08f67-106">Ortak MSBuild özelliklerinin bir listesi için bkz. [Ortak MSBuild özellikleri](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="08f67-106">For a list of common MSBuild properties, see [Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="framework-properties"></a><span data-ttu-id="08f67-107">Çerçeve özellikleri</span><span class="sxs-lookup"><span data-stu-id="08f67-107">Framework properties</span></span>

<span data-ttu-id="08f67-108">Aşağıdaki MSBuild özellikleri bu bölümde belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="08f67-108">The following MSBuild properties are documented in this section:</span></span>

- [<span data-ttu-id="08f67-109">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="08f67-109">TargetFramework</span></span>](#targetframework)
- [<span data-ttu-id="08f67-110">Targetçerçeveler</span><span class="sxs-lookup"><span data-stu-id="08f67-110">TargetFrameworks</span></span>](#targetframeworks)
- [<span data-ttu-id="08f67-111">Netstandardımplicitpackageversion</span><span class="sxs-lookup"><span data-stu-id="08f67-111">NetStandardImplicitPackageVersion</span></span>](#netstandardimplicitpackageversion)

### <a name="targetframework"></a><span data-ttu-id="08f67-112">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="08f67-112">TargetFramework</span></span>

<span data-ttu-id="08f67-113">`TargetFramework`Özelliği, uygulamanın hedef Framework sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="08f67-113">The `TargetFramework` property specifies the target framework version for the app.</span></span> <span data-ttu-id="08f67-114">Geçerli hedef çerçeve takma adların listesi için bkz. [SDK stili projelerde hedef çerçeveler](../../standard/frameworks.md#supported-target-frameworks).</span><span class="sxs-lookup"><span data-stu-id="08f67-114">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-frameworks).</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>
```

<span data-ttu-id="08f67-115">Daha fazla bilgi için bkz. [SDK stili projelerde hedef çerçeveler](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="08f67-115">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="targetframeworks"></a><span data-ttu-id="08f67-116">Targetçerçeveler</span><span class="sxs-lookup"><span data-stu-id="08f67-116">TargetFrameworks</span></span>

<span data-ttu-id="08f67-117">`TargetFrameworks`Uygulamanızın birden çok platformu hedeflemesini istediğinizde özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="08f67-117">Use the `TargetFrameworks` property when you want your app to target multiple platforms.</span></span> <span data-ttu-id="08f67-118">Geçerli hedef çerçeve takma adların listesi için bkz. [SDK stili projelerde hedef çerçeveler](../../standard/frameworks.md#supported-target-frameworks).</span><span class="sxs-lookup"><span data-stu-id="08f67-118">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-frameworks).</span></span>

> [!NOTE]
> <span data-ttu-id="08f67-119">`TargetFramework`(Tekil) belirtilmişse bu özellik yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="08f67-119">This property is ignored if `TargetFramework` (singular) is specified.</span></span>

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
</PropertyGroup>
```

<span data-ttu-id="08f67-120">Daha fazla bilgi için bkz. [SDK stili projelerde hedef çerçeveler](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="08f67-120">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="netstandardimplicitpackageversion"></a><span data-ttu-id="08f67-121">Netstandardımplicitpackageversion</span><span class="sxs-lookup"><span data-stu-id="08f67-121">NetStandardImplicitPackageVersion</span></span>

> [!NOTE]
> <span data-ttu-id="08f67-122">Bu özellik yalnızca kullanan projeler için geçerlidir `netstandard1.x` .</span><span class="sxs-lookup"><span data-stu-id="08f67-122">This property only applies to projects using `netstandard1.x`.</span></span> <span data-ttu-id="08f67-123">Kullanan projeler için uygulanmaz `netstandard2.x` .</span><span class="sxs-lookup"><span data-stu-id="08f67-123">It doesn't apply to projects that use `netstandard2.x`.</span></span>

<span data-ttu-id="08f67-124">`NetStandardImplicitPackageVersion`Metapackage sürümünden daha düşük bir çerçeve sürümü belirtmek istediğinizde özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="08f67-124">Use the `NetStandardImplicitPackageVersion` property when you want to specify a framework version that's lower than the metapackage version.</span></span> <span data-ttu-id="08f67-125">Aşağıdaki örnekteki proje dosyası hedefler, `netstandard1.3` ancak 1.6.0 sürümünü kullanır `NETStandard.Library` .</span><span class="sxs-lookup"><span data-stu-id="08f67-125">The project file in the following example targets `netstandard1.3` but uses the 1.6.0 version of `NETStandard.Library`.</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netstandard1.3</TargetFramework>
  <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
</PropertyGroup>
```

## <a name="package-properties"></a><span data-ttu-id="08f67-126">Paket özellikleri</span><span class="sxs-lookup"><span data-stu-id="08f67-126">Package properties</span></span>

<span data-ttu-id="08f67-127">`PackageId` `PackageVersion` `PackageIcon` `Title` `Description` Projenizden oluşturulan paketi betimleyen,,, ve gibi özellikleri belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08f67-127">You can specify properties such as `PackageId`, `PackageVersion`, `PackageIcon`, `Title`, and `Description` to describe the package that gets created from your project.</span></span> <span data-ttu-id="08f67-128">Bu ve diğer özellikler hakkında daha fazla bilgi için bkz. [Pack Target](/nuget/reference/msbuild-targets#pack-target).</span><span class="sxs-lookup"><span data-stu-id="08f67-128">For information about these and other properties, see [pack target](/nuget/reference/msbuild-targets#pack-target).</span></span>

```xml
<PropertyGroup>
  ...
  <PackageId>ClassLibDotNetStandard</PackageId>
  <Version>1.0.0</Version>
  <Authors>John Doe</Authors>
  <Company>Contoso</Company>
</PropertyGroup>
```

## <a name="publish-related-properties"></a><span data-ttu-id="08f67-129">Yayınla ilgili özellikler</span><span class="sxs-lookup"><span data-stu-id="08f67-129">Publish-related properties</span></span>

<span data-ttu-id="08f67-130">Aşağıdaki MSBuild özellikleri bu bölümde belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="08f67-130">The following MSBuild properties are documented in this section:</span></span>

- [<span data-ttu-id="08f67-131">Appendruntimeıdentifiertooutputpath</span><span class="sxs-lookup"><span data-stu-id="08f67-131">AppendRuntimeIdentifierToOutputPath</span></span>](#appendruntimeidentifiertooutputpath)
- [<span data-ttu-id="08f67-132">AppendTargetFrameworkToOutputPath</span><span class="sxs-lookup"><span data-stu-id="08f67-132">AppendTargetFrameworkToOutputPath</span></span>](#appendtargetframeworktooutputpath)
- [<span data-ttu-id="08f67-133">CopyLocalLockFileAssemblies</span><span class="sxs-lookup"><span data-stu-id="08f67-133">CopyLocalLockFileAssemblies</span></span>](#copylocallockfileassemblies)
- [<span data-ttu-id="08f67-134">PreserveCompilationContext</span><span class="sxs-lookup"><span data-stu-id="08f67-134">PreserveCompilationContext</span></span>](#preservecompilationcontext)
- [<span data-ttu-id="08f67-135">PreserveCompilationReferences</span><span class="sxs-lookup"><span data-stu-id="08f67-135">PreserveCompilationReferences</span></span>](#preservecompilationreferences)
- [<span data-ttu-id="08f67-136">Runtimeıdentifier</span><span class="sxs-lookup"><span data-stu-id="08f67-136">RuntimeIdentifier</span></span>](#runtimeidentifier)
- [<span data-ttu-id="08f67-137">Runtimetanımlayıcıtanımlayıcıları</span><span class="sxs-lookup"><span data-stu-id="08f67-137">RuntimeIdentifiers</span></span>](#runtimeidentifiers)
- [<span data-ttu-id="08f67-138">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="08f67-138">UseAppHost</span></span>](#useapphost)

### <a name="appendtargetframeworktooutputpath"></a><span data-ttu-id="08f67-139">AppendTargetFrameworkToOutputPath</span><span class="sxs-lookup"><span data-stu-id="08f67-139">AppendTargetFrameworkToOutputPath</span></span>

<span data-ttu-id="08f67-140">`AppendTargetFrameworkToOutputPath`Özelliği, [hedef çerçeve adının (TFI)](../../standard/frameworks.md) çıkış yolunun ( [OutputPath](/visualstudio/msbuild/common-msbuild-project-properties#list-of-common-properties-and-parameters)tarafından tanımlanan) eklenip eklenmeyeceğini denetler.</span><span class="sxs-lookup"><span data-stu-id="08f67-140">The `AppendTargetFrameworkToOutputPath` property controls whether the [target framework moniker (TFM)](../../standard/frameworks.md) is appended to the output path (which is defined by [OutputPath](/visualstudio/msbuild/common-msbuild-project-properties#list-of-common-properties-and-parameters)).</span></span> <span data-ttu-id="08f67-141">.NET SDK, hedef çerçeveyi otomatik olarak ekler ve varsa, çalışma zamanı tanımlayıcısını çıkış yoluna ekler.</span><span class="sxs-lookup"><span data-stu-id="08f67-141">The .NET SDK automatically appends the target framework and, if present, the runtime identifier to the output path.</span></span> <span data-ttu-id="08f67-142">`AppendTargetFrameworkToOutputPath`İçin ayarı `false` , TFI 'nin çıkış yoluna eklenmesini engeller.</span><span class="sxs-lookup"><span data-stu-id="08f67-142">Setting `AppendTargetFrameworkToOutputPath` to `false` prevents the TFM from being appended to the output path.</span></span> <span data-ttu-id="08f67-143">Ancak, çıkış yolunda TFı olmadan, birden çok derleme yapıtları birbirinin üzerine yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="08f67-143">However, without the TFM in the output path, multiple build artifacts may overwrite each other.</span></span>

<span data-ttu-id="08f67-144">Örneğin, bir .NET 5,0 uygulaması için çıkış yolu, ' dan ' ı `bin\Debug\net5.0` `bin\Debug` aşağıdaki ayarla olarak değişir:</span><span class="sxs-lookup"><span data-stu-id="08f67-144">For example, for a .NET 5.0 app, the output path changes from `bin\Debug\net5.0` to `bin\Debug` with the following setting:</span></span>

```xml
<PropertyGroup>
  <AppendTargetFrameworkToOutputPath>false</AppendTargetFrameworkToOutputPath>
</PropertyGroup>
```

### <a name="appendruntimeidentifiertooutputpath"></a><span data-ttu-id="08f67-145">Appendruntimeıdentifiertooutputpath</span><span class="sxs-lookup"><span data-stu-id="08f67-145">AppendRuntimeIdentifierToOutputPath</span></span>

<span data-ttu-id="08f67-146">`AppendRuntimeIdentifierToOutputPath`Özelliği, [çalışma zamanı TANıMLAYıCıSıNıN (RID)](../rid-catalog.md) çıkış yolunun sonuna eklenip eklenmeyeceğini denetler.</span><span class="sxs-lookup"><span data-stu-id="08f67-146">The `AppendRuntimeIdentifierToOutputPath` property controls whether the [runtime identifier (RID)](../rid-catalog.md) is appended to the output path.</span></span> <span data-ttu-id="08f67-147">.NET SDK, hedef çerçeveyi otomatik olarak ekler ve varsa, çalışma zamanı tanımlayıcısını çıkış yoluna ekler.</span><span class="sxs-lookup"><span data-stu-id="08f67-147">The .NET SDK automatically appends the target framework and, if present, the runtime identifier to the output path.</span></span> <span data-ttu-id="08f67-148">`AppendRuntimeIdentifierToOutputPath`İçin ayarı `false` , RID 'nin çıkış yoluna eklenmesini önler.</span><span class="sxs-lookup"><span data-stu-id="08f67-148">Setting `AppendRuntimeIdentifierToOutputPath` to `false` prevents the RID from being appended to the output path.</span></span>

<span data-ttu-id="08f67-149">Örneğin, bir .NET 5,0 uygulaması ve bir RID 'si için `win10-x64` çıkış yolu, ' dan ' ı `bin\Debug\net5.0\win10-x64` `bin\Debug\net5.0` aşağıdaki ayarla olarak değişir:</span><span class="sxs-lookup"><span data-stu-id="08f67-149">For example, for a .NET 5.0 app and an RID of `win10-x64`, the output path changes from `bin\Debug\net5.0\win10-x64` to `bin\Debug\net5.0` with the following setting:</span></span>

```xml
<PropertyGroup>
  <AppendRuntimeIdentifierToOutputPath>false</AppendRuntimeIdentifierToOutputPath>
</PropertyGroup>
```

### <a name="copylocallockfileassemblies"></a><span data-ttu-id="08f67-150">CopyLocalLockFileAssemblies</span><span class="sxs-lookup"><span data-stu-id="08f67-150">CopyLocalLockFileAssemblies</span></span>

<span data-ttu-id="08f67-151">`CopyLocalLockFileAssemblies`Özelliği, diğer kitaplıklara bağımlılıkları olan eklenti projeleri için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="08f67-151">The `CopyLocalLockFileAssemblies` property is useful for plugin projects that have dependencies on other libraries.</span></span> <span data-ttu-id="08f67-152">Bu özelliği olarak ayarlarsanız `true` , herhangi bir NuGet paketi bağımlılığı çıkış dizinine kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="08f67-152">If you set this property to `true`, any NuGet package dependencies are copied to the output directory.</span></span> <span data-ttu-id="08f67-153">Diğer bir deyişle, `dotnet build` herhangi bir makinede kendi eklentisini çalıştırmak için çıkışını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08f67-153">That means you can use the output of `dotnet build` to run your plugin on any machine.</span></span>

```xml
<PropertyGroup>
  <CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>
</PropertyGroup>
```

> [!TIP]
> <span data-ttu-id="08f67-154">Alternatif olarak, `dotnet publish` sınıf kitaplığını yayımlamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08f67-154">Alternatively, you can use `dotnet publish` to publish the class library.</span></span> <span data-ttu-id="08f67-155">Daha fazla bilgi için bkz. [DotNet Publish](../tools/dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="08f67-155">For more information, see [dotnet publish](../tools/dotnet-publish.md).</span></span>

### <a name="preservecompilationcontext"></a><span data-ttu-id="08f67-156">PreserveCompilationContext</span><span class="sxs-lookup"><span data-stu-id="08f67-156">PreserveCompilationContext</span></span>

<span data-ttu-id="08f67-157">`PreserveCompilationContext`Özelliği, derleme zamanında kullanılan ayarların aynısını kullanarak, oluşturulmuş veya yayımlanmış bir uygulamanın çalışma zamanında daha fazla kod derlemesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="08f67-157">The `PreserveCompilationContext` property allows a built or published application to compile more code at run time using the same settings that were used at build time.</span></span> <span data-ttu-id="08f67-158">Derleme zamanında başvurulan derlemeler, çıkış dizininin *ref* alt dizinine kopyalanacak.</span><span class="sxs-lookup"><span data-stu-id="08f67-158">The assemblies referenced at build time will be copied into the *ref* subdirectory of the output directory.</span></span> <span data-ttu-id="08f67-159">Başvuru derlemelerinin adları, derleyicisine geçirilen seçeneklerle birlikte uygulamanın.deps.jsdosya *üzerinde* depolanır.</span><span class="sxs-lookup"><span data-stu-id="08f67-159">The names of the reference assemblies are stored in the application's *.deps.json* file along with the options passed to the compiler.</span></span> <span data-ttu-id="08f67-160">Ve özelliklerini kullanarak bu bilgileri alabilirsiniz <xref:Microsoft.Extensions.DependencyModel.DependencyContext.CompileLibraries?displayProperty=nameWithType> <xref:Microsoft.Extensions.DependencyModel.DependencyContext.CompilationOptions?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="08f67-160">You can retrieve this information using the <xref:Microsoft.Extensions.DependencyModel.DependencyContext.CompileLibraries?displayProperty=nameWithType> and <xref:Microsoft.Extensions.DependencyModel.DependencyContext.CompilationOptions?displayProperty=nameWithType> properties.</span></span>

<span data-ttu-id="08f67-161">Bu işlevsellik çoğunlukla, Razor dosyalarının çalışma zamanı derlemesini desteklemek için ASP.NET Core MVC ve Razor sayfaları tarafından dahili olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="08f67-161">This functionality is mostly used internally by ASP.NET Core MVC and Razor pages to support run-time compilation of Razor files.</span></span>

```xml
<PropertyGroup>
  <PreserveCompilationContext>true</PreserveCompilationContext>
</PropertyGroup>
```

### <a name="preservecompilationreferences"></a><span data-ttu-id="08f67-162">PreserveCompilationReferences</span><span class="sxs-lookup"><span data-stu-id="08f67-162">PreserveCompilationReferences</span></span>

<span data-ttu-id="08f67-163">`PreserveCompilationReferences`Özelliği [Preservecompilationcontext](#preservecompilationcontext) özelliğine benzerdir, ancak yalnızca başvurulan derlemeler dosya *.deps.js* değil yayımlama dizinine kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="08f67-163">The `PreserveCompilationReferences` property is similar to the [PreserveCompilationContext](#preservecompilationcontext) property, except that it only copies the referenced assemblies to the publish directory, and not the *.deps.json* file.</span></span>

```xml
<PropertyGroup>
  <PreserveCompilationReferences>true</PreserveCompilationReferences>
</PropertyGroup>
```

<span data-ttu-id="08f67-164">Daha fazla bilgi için bkz. [Razor SDK özellikleri](/aspnet/core/razor-pages/sdk#properties).</span><span class="sxs-lookup"><span data-stu-id="08f67-164">For more information, see [Razor SDK properties](/aspnet/core/razor-pages/sdk#properties).</span></span>

### <a name="runtimeidentifier"></a><span data-ttu-id="08f67-165">Runtimeıdentifier</span><span class="sxs-lookup"><span data-stu-id="08f67-165">RuntimeIdentifier</span></span>

<span data-ttu-id="08f67-166">`RuntimeIdentifier`Özelliği, proje için tek bir [çalışma zamanı tanımlayıcısı (RID)](../rid-catalog.md) belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="08f67-166">The `RuntimeIdentifier` property lets you specify a single [runtime identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="08f67-167">RID, kendi kendine içerilen bir dağıtımı yayımlamayı mümkün.</span><span class="sxs-lookup"><span data-stu-id="08f67-167">The RID enables publishing a self-contained deployment.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
</PropertyGroup>
```

### <a name="runtimeidentifiers"></a><span data-ttu-id="08f67-168">Runtimetanımlayıcıtanımlayıcıları</span><span class="sxs-lookup"><span data-stu-id="08f67-168">RuntimeIdentifiers</span></span>

<span data-ttu-id="08f67-169">`RuntimeIdentifiers`Özelliği, proje için bir [çalışma zamanı tanımlayıcıları (RID 'ler)](../rid-catalog.md) için noktalı virgülle ayrılmış bir liste belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="08f67-169">The `RuntimeIdentifiers` property lets you specify a semicolon-delimited list of [runtime identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="08f67-170">Birden çok çalışma zamanı için yayımlamanız gerekiyorsa bu özelliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="08f67-170">Use this property if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="08f67-171">`RuntimeIdentifiers` , doğru varlıkların grafikte olduğundan emin olmak için geri yükleme zamanında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="08f67-171">`RuntimeIdentifiers` is used at restore time to ensure the right assets are in the graph.</span></span>

> [!TIP]
> <span data-ttu-id="08f67-172">`RuntimeIdentifier` (tekil) yalnızca tek bir çalışma zamanı gerektiğinde daha hızlı derlemeler sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="08f67-172">`RuntimeIdentifier` (singular) can provide faster builds when only a single runtime is required.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
</PropertyGroup>
```

### <a name="useapphost"></a><span data-ttu-id="08f67-173">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="08f67-173">UseAppHost</span></span>

<span data-ttu-id="08f67-174">`UseAppHost`Özelliği, bir dağıtım için yerel yürütülebilir dosyanın oluşturulup oluşturulmayacağını denetler.</span><span class="sxs-lookup"><span data-stu-id="08f67-174">The `UseAppHost` property controls whether or not a native executable is created for a deployment.</span></span> <span data-ttu-id="08f67-175">Kendi kendine kapsanan dağıtımlar için yerel bir yürütülebilir dosya gereklidir.</span><span class="sxs-lookup"><span data-stu-id="08f67-175">A native executable is required for self-contained deployments.</span></span>

<span data-ttu-id="08f67-176">.NET Core 3,0 ve sonraki sürümlerinde, çerçeveye bağlı bir yürütülebilir dosya varsayılan olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="08f67-176">In .NET Core 3.0 and later versions, a framework-dependent executable is created by default.</span></span> <span data-ttu-id="08f67-177">`UseAppHost` `false` Yürütülebilir dosyanın üretilmesini devre dışı bırakmak için özelliğini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="08f67-177">Set the `UseAppHost` property to `false` to disable generation of the executable.</span></span>

```xml
<PropertyGroup>
  <UseAppHost>false</UseAppHost>
</PropertyGroup>
```

<span data-ttu-id="08f67-178">Dağıtım hakkında daha fazla bilgi için bkz. [.NET uygulama dağıtımı](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="08f67-178">For more information about deployment, see [.NET application deployment](../deploying/index.md).</span></span>

## <a name="compilation-related-properties"></a><span data-ttu-id="08f67-179">Derlemeden ilgili özellikler</span><span class="sxs-lookup"><span data-stu-id="08f67-179">Compilation-related properties</span></span>

<span data-ttu-id="08f67-180">Aşağıdaki MSBuild özellikleri bu bölümde belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="08f67-180">The following MSBuild properties are documented in this section:</span></span>

- [<span data-ttu-id="08f67-181">Embeddedresourceusebağımlıtuponconvention</span><span class="sxs-lookup"><span data-stu-id="08f67-181">EmbeddedResourceUseDependentUponConvention</span></span>](#embeddedresourceusedependentuponconvention)
- [<span data-ttu-id="08f67-182">LangVersion</span><span class="sxs-lookup"><span data-stu-id="08f67-182">LangVersion</span></span>](#langversion)

### <a name="embeddedresourceusedependentuponconvention"></a><span data-ttu-id="08f67-183">Embeddedresourceusebağımlıtuponconvention</span><span class="sxs-lookup"><span data-stu-id="08f67-183">EmbeddedResourceUseDependentUponConvention</span></span>

<span data-ttu-id="08f67-184">Özelliği, kaynak dosyaları `EmbeddedResourceUseDependentUponConvention` ile birlikte bulunan kaynak dosyalardaki tür bilgilerden kaynak bildirim dosyası adlarının oluşturulup oluşturulmayacağını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="08f67-184">The `EmbeddedResourceUseDependentUponConvention` property defines whether resource manifest file names are generated from type information in source files that are colocated with resource files.</span></span> <span data-ttu-id="08f67-185">Örneğin, *Form1. resx* *Form1. cs* ile aynı klasörssa ve olarak `EmbeddedResourceUseDependentUponConvention` ayarlanırsa `true` , oluşturulan *. resources* dosyası, adını *Form1. cs* dosyasında tanımlanan ilk türden alır.</span><span class="sxs-lookup"><span data-stu-id="08f67-185">For example, if *Form1.resx* is in the same folder as *Form1.cs*, and `EmbeddedResourceUseDependentUponConvention` is set to `true`, the generated *.resources* file takes its name from the first type that's defined in *Form1.cs*.</span></span> <span data-ttu-id="08f67-186">Örneğin, `MyNamespace.Form1` *Form1. cs* içinde tanımlanan ilk tür ise, oluşturulan dosya adı *MyNamespace. Form1. resources* olur.</span><span class="sxs-lookup"><span data-stu-id="08f67-186">For example, if `MyNamespace.Form1` is the first type defined in *Form1.cs*, the generated file name is *MyNamespace.Form1.resources*.</span></span>

> [!NOTE]
> <span data-ttu-id="08f67-187">`LogicalName`,, `ManifestResourceName` Veya `DependentUpon` meta veriler bir öğe için belirtilmişse `EmbeddedResource` , bu kaynak dosyası için oluşturulan bildirim dosyası adı bu meta verileri temel alır.</span><span class="sxs-lookup"><span data-stu-id="08f67-187">If `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for an `EmbeddedResource` item, the generated manifest file name for that resource file is based on that metadata instead.</span></span>

<span data-ttu-id="08f67-188">Varsayılan olarak, yeni bir .NET projesinde, bu özellik olarak ayarlanır `true` .</span><span class="sxs-lookup"><span data-stu-id="08f67-188">By default, in a new .NET project, this property is set to `true`.</span></span> <span data-ttu-id="08f67-189">`false`, Ve öğesi için, `LogicalName` `ManifestResourceName` Proje dosyasındaki öğe için, veya olarak ayarlanırsa,, `DependentUpon` `EmbeddedResource` kaynak bildirim dosyası adı projenin kök ad alanını ve *. resx* dosyasının göreli dosya yolunu temel alan olur.</span><span class="sxs-lookup"><span data-stu-id="08f67-189">If set to `false`, and no `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for the `EmbeddedResource` item in the project file, the resource manifest file name is based off the root namespace for the project and the relative file path to the *.resx* file.</span></span> <span data-ttu-id="08f67-190">Daha fazla bilgi için bkz. [kaynak bildirim dosyalarının adlandırılması](../resources/manifest-file-names.md).</span><span class="sxs-lookup"><span data-stu-id="08f67-190">For more information, see [How resource manifest files are named](../resources/manifest-file-names.md).</span></span>

```xml
<PropertyGroup>
  <EmbeddedResourceUseDependentUponConvention>true</EmbeddedResourceUseDependentUponConvention>
</PropertyGroup>
```

### <a name="langversion"></a><span data-ttu-id="08f67-191">LangVersion</span><span class="sxs-lookup"><span data-stu-id="08f67-191">LangVersion</span></span>

<span data-ttu-id="08f67-192">`LangVersion`Özelliği, belirli bir programlama dili sürümü belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="08f67-192">The `LangVersion` property lets you specify a specific programming language version.</span></span> <span data-ttu-id="08f67-193">Örneğin, C# önizleme özelliklerine erişmek istiyorsanız, `LangVersion` olarak ayarlayın `preview` .</span><span class="sxs-lookup"><span data-stu-id="08f67-193">For example, if you want access to C# preview features, set `LangVersion` to `preview`.</span></span>

```xml
<PropertyGroup>
  <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="08f67-194">Daha fazla bilgi için bkz. [C# dil sürümü oluşturma](../../csharp/language-reference/configure-language-version.md#override-a-default).</span><span class="sxs-lookup"><span data-stu-id="08f67-194">For more information, see [C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).</span></span>

## <a name="default-item-inclusion-properties"></a><span data-ttu-id="08f67-195">Varsayılan öğe içerme özellikleri</span><span class="sxs-lookup"><span data-stu-id="08f67-195">Default item inclusion properties</span></span>

<span data-ttu-id="08f67-196">Aşağıdaki MSBuild özellikleri bu bölümde belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="08f67-196">The following MSBuild properties are documented in this section:</span></span>

- [<span data-ttu-id="08f67-197">DefaultExcludesInProjectFolder</span><span class="sxs-lookup"><span data-stu-id="08f67-197">DefaultExcludesInProjectFolder</span></span>](#defaultexcludesinprojectfolder)
- [<span data-ttu-id="08f67-198">DefaultItemExcludes</span><span class="sxs-lookup"><span data-stu-id="08f67-198">DefaultItemExcludes</span></span>](#defaultitemexcludes)
- [<span data-ttu-id="08f67-199">Enabledefaultcompileıtems</span><span class="sxs-lookup"><span data-stu-id="08f67-199">EnableDefaultCompileItems</span></span>](#enabledefaultcompileitems)
- [<span data-ttu-id="08f67-200">Enabledefaultembeddedresourceıtems</span><span class="sxs-lookup"><span data-stu-id="08f67-200">EnableDefaultEmbeddedResourceItems</span></span>](#enabledefaultembeddedresourceitems)
- [<span data-ttu-id="08f67-201">Enabledefaultıtems</span><span class="sxs-lookup"><span data-stu-id="08f67-201">EnableDefaultItems</span></span>](#enabledefaultitems)
- [<span data-ttu-id="08f67-202">Enabledefaultnoneıtems</span><span class="sxs-lookup"><span data-stu-id="08f67-202">EnableDefaultNoneItems</span></span>](#enabledefaultnoneitems)

<span data-ttu-id="08f67-203">Daha fazla bilgi için bkz. [varsayılan içerme ve dışladığı](overview.md#default-includes-and-excludes).</span><span class="sxs-lookup"><span data-stu-id="08f67-203">For more information, see [Default includes and excludes](overview.md#default-includes-and-excludes).</span></span>

### <a name="defaultitemexcludes"></a><span data-ttu-id="08f67-204">DefaultItemExcludes</span><span class="sxs-lookup"><span data-stu-id="08f67-204">DefaultItemExcludes</span></span>

<span data-ttu-id="08f67-205">`DefaultItemExcludes`Include, exclude ve Remove genelleştirmeler dışında tutulması gereken dosya ve klasörler için glob desenleri tanımlamak üzere özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="08f67-205">Use the `DefaultItemExcludes` property to define glob patterns for files and folders that should be excluded from the include, exclude, and remove globs.</span></span> <span data-ttu-id="08f67-206">Varsayılan olarak, *./bin* ve *./obj* klasörleri, glob desenlerinden çıkarılır.</span><span class="sxs-lookup"><span data-stu-id="08f67-206">By default, the *./bin* and *./obj* folders are excluded from the glob patterns.</span></span>

```xml
<PropertyGroup>
  <DefaultItemExcludes>$(DefaultItemExcludes);**/*.myextension</DefaultItemExcludes>
</PropertyGroup>
```

### <a name="defaultexcludesinprojectfolder"></a><span data-ttu-id="08f67-207">DefaultExcludesInProjectFolder</span><span class="sxs-lookup"><span data-stu-id="08f67-207">DefaultExcludesInProjectFolder</span></span>

<span data-ttu-id="08f67-208">`DefaultExcludesInProjectFolder`Dahil etme, hariç tutma ve kaldırma genelleştirmeler dışında tutulacak proje klasöründeki dosya ve klasörler için glob desenlerini tanımlamak üzere özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="08f67-208">Use the `DefaultExcludesInProjectFolder` property to define glob patterns for files and folders in the project folder that should be excluded from the include, exclude, and remove globs.</span></span> <span data-ttu-id="08f67-209">Varsayılan olarak, `.` *. git* ve *. vs* gibi bir noktayla başlayan klasörler, glob desenlerinden çıkarılır.</span><span class="sxs-lookup"><span data-stu-id="08f67-209">By default, folders that start with a period (`.`), such as *.git* and *.vs*, are excluded from the glob patterns.</span></span>

<span data-ttu-id="08f67-210">Bu özellik, `DefaultItemExcludes` yalnızca proje klasöründeki dosya ve klasörleri dikkate almak dışında özelliğine çok benzer.</span><span class="sxs-lookup"><span data-stu-id="08f67-210">This property is very similar to the `DefaultItemExcludes` property, except that it only considers files and folders in the project folder.</span></span> <span data-ttu-id="08f67-211">Bir glob deseninin proje klasörü dışındaki öğeleri bir göreli yol ile istenmeden eşleşmesi durumunda, özelliği `DefaultExcludesInProjectFolder` yerine özelliğini kullanın `DefaultItemExcludes` .</span><span class="sxs-lookup"><span data-stu-id="08f67-211">When a glob pattern would unintentionally match items outside the project folder with a relative path, use the `DefaultExcludesInProjectFolder` property instead of the `DefaultItemExcludes` property.</span></span>

```xml
<PropertyGroup>
  <DefaultExcludesInProjectFolder>$(DefaultExcludesInProjectFolder);**/myprefix*/**</DefaultExcludesInProjectFolder>
</PropertyGroup>
```

### <a name="enabledefaultitems"></a><span data-ttu-id="08f67-212">Enabledefaultıtems</span><span class="sxs-lookup"><span data-stu-id="08f67-212">EnableDefaultItems</span></span>

<span data-ttu-id="08f67-213">`EnableDefaultItems`Özelliği derleme öğelerinin, katıştırılmış kaynak öğelerinin ve `None` öğelerin projeye örtük olarak dahil edilip edilmeyeceğini denetler.</span><span class="sxs-lookup"><span data-stu-id="08f67-213">The `EnableDefaultItems` property controls whether compile items, embedded resource items, and `None` items are implicitly included in the project.</span></span> <span data-ttu-id="08f67-214">`true` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="08f67-214">The default value is `true`.</span></span> <span data-ttu-id="08f67-215">`EnableDefaultItems` `false` Tüm örtük dosya dahil edilmesini devre dışı bırakmak için özelliğini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="08f67-215">Set the `EnableDefaultItems` property to `false` to disable all implicit file inclusion.</span></span>

```xml
<PropertyGroup>
  <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

### <a name="enabledefaultcompileitems"></a><span data-ttu-id="08f67-216">Enabledefaultcompileıtems</span><span class="sxs-lookup"><span data-stu-id="08f67-216">EnableDefaultCompileItems</span></span>

<span data-ttu-id="08f67-217">`EnableDefaultCompileItems`Özelliği, derleme öğelerinin projeye örtük olarak dahil edilip edilmeyeceğini denetler.</span><span class="sxs-lookup"><span data-stu-id="08f67-217">The `EnableDefaultCompileItems` property controls whether compile items are implicitly included in the project.</span></span> <span data-ttu-id="08f67-218">`true` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="08f67-218">The default value is `true`.</span></span> <span data-ttu-id="08f67-219">`EnableDefaultCompileItems` `false` \*. Cs ve diğer dil uzantısı dosyalarının örtük olarak eklenmesini devre dışı bırakmak için özelliğini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="08f67-219">Set the `EnableDefaultCompileItems` property to `false` to disable implicit inclusion of \*.cs and other language-extension files.</span></span>

```xml
<PropertyGroup>
  <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

### <a name="enabledefaultembeddedresourceitems"></a><span data-ttu-id="08f67-220">Enabledefaultembeddedresourceıtems</span><span class="sxs-lookup"><span data-stu-id="08f67-220">EnableDefaultEmbeddedResourceItems</span></span>

<span data-ttu-id="08f67-221">`EnableDefaultEmbeddedResourceItems`Özelliği, katıştırılmış kaynak öğelerinin projeye örtük olarak dahil edilip edilmeyeceğini denetler.</span><span class="sxs-lookup"><span data-stu-id="08f67-221">The `EnableDefaultEmbeddedResourceItems` property controls whether embedded resource items are implicitly included in the project.</span></span> <span data-ttu-id="08f67-222">`true` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="08f67-222">The default value is `true`.</span></span> <span data-ttu-id="08f67-223">`EnableDefaultEmbeddedResourceItems` `false` Gömülü kaynak dosyalarının örtük olarak eklenmesini devre dışı bırakmak için özelliğini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="08f67-223">Set the `EnableDefaultEmbeddedResourceItems` property to `false` to disable implicit inclusion of embedded resource files.</span></span>

```xml
<PropertyGroup>
  <EnableDefaultEmbeddedResourceItems>false</EnableDefaultEmbeddedResourceItems>
</PropertyGroup>
```

### <a name="enabledefaultnoneitems"></a><span data-ttu-id="08f67-224">Enabledefaultnoneıtems</span><span class="sxs-lookup"><span data-stu-id="08f67-224">EnableDefaultNoneItems</span></span>

<span data-ttu-id="08f67-225">`EnableDefaultNoneItems`Özelliği, `None` öğelerin (yapı işleminde rolü olmayan dosyalar) örtük olarak projeye dahil edilip edilmeyeceğini denetler.</span><span class="sxs-lookup"><span data-stu-id="08f67-225">The `EnableDefaultNoneItems` property controls whether `None` items (files that have no role in the build process) are implicitly included in the project.</span></span> <span data-ttu-id="08f67-226">`true` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="08f67-226">The default value is `true`.</span></span> <span data-ttu-id="08f67-227">`EnableDefaultNoneItems`Özelliği `false` örtük olarak öğelerin dahil edilmesini devre dışı bırakmak için olarak ayarlayın `None` .</span><span class="sxs-lookup"><span data-stu-id="08f67-227">Set the `EnableDefaultNoneItems` property to `false` to disable implicit inclusion of `None` items.</span></span>

```xml
<PropertyGroup>
  <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

## <a name="code-analysis-properties"></a><span data-ttu-id="08f67-228">Kod Analizi özellikleri</span><span class="sxs-lookup"><span data-stu-id="08f67-228">Code analysis properties</span></span>

<span data-ttu-id="08f67-229">Aşağıdaki MSBuild özellikleri bu bölümde belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="08f67-229">The following MSBuild properties are documented in this section:</span></span>

- [<span data-ttu-id="08f67-230">AnalysisLevel</span><span class="sxs-lookup"><span data-stu-id="08f67-230">AnalysisLevel</span></span>](#analysislevel)
- [<span data-ttu-id="08f67-231">AnalysisMode</span><span class="sxs-lookup"><span data-stu-id="08f67-231">AnalysisMode</span></span>](#analysismode)
- [<span data-ttu-id="08f67-232">CodeAnalysisTreatWarningsAsErrors</span><span class="sxs-lookup"><span data-stu-id="08f67-232">CodeAnalysisTreatWarningsAsErrors</span></span>](#codeanalysistreatwarningsaserrors)
- [<span data-ttu-id="08f67-233">Enablenetçözümleyiciler</span><span class="sxs-lookup"><span data-stu-id="08f67-233">EnableNETAnalyzers</span></span>](#enablenetanalyzers)
- [<span data-ttu-id="08f67-234">Enforcecodestyleınbuild</span><span class="sxs-lookup"><span data-stu-id="08f67-234">EnforceCodeStyleInBuild</span></span>](#enforcecodestyleinbuild)

### <a name="analysislevel"></a><span data-ttu-id="08f67-235">AnalysisLevel</span><span class="sxs-lookup"><span data-stu-id="08f67-235">AnalysisLevel</span></span>

<span data-ttu-id="08f67-236">`AnalysisLevel`Özelliği, kod analizi düzeyi belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="08f67-236">The `AnalysisLevel` property lets you specify a code-analysis level.</span></span> <span data-ttu-id="08f67-237">Örneğin, önizleme kodu Çözümleyicileri için erişim istiyorsanız, `AnalysisLevel` olarak ayarlayın `preview` .</span><span class="sxs-lookup"><span data-stu-id="08f67-237">For example, if you want access to preview code analyzers, set `AnalysisLevel` to `preview`.</span></span>

<span data-ttu-id="08f67-238">Varsayılan değer:</span><span class="sxs-lookup"><span data-stu-id="08f67-238">Default value:</span></span>

- <span data-ttu-id="08f67-239">Projeniz .NET 5,0 veya üstünü hedefliyorsa veya [Analysismode](#analysismode) özelliğini eklediyseniz, varsayılan değer olur `latest` .</span><span class="sxs-lookup"><span data-stu-id="08f67-239">If your project targets .NET 5.0 or later, or if you've added the [AnalysisMode](#analysismode) property, the default value is `latest`.</span></span>
- <span data-ttu-id="08f67-240">Aksi takdirde, açıkça proje dosyasına eklemediğiniz takdirde bu özellik atlanır.</span><span class="sxs-lookup"><span data-stu-id="08f67-240">Otherwise, this property is omitted unless you explicitly add it to the project file.</span></span>

```xml
<PropertyGroup>
  <AnalysisLevel>preview</AnalysisLevel>
</PropertyGroup>
```

<span data-ttu-id="08f67-241">Aşağıdaki tabloda kullanılabilir seçenekler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="08f67-241">The following table shows the available options.</span></span>

| <span data-ttu-id="08f67-242">Değer</span><span class="sxs-lookup"><span data-stu-id="08f67-242">Value</span></span> | <span data-ttu-id="08f67-243">Anlamı</span><span class="sxs-lookup"><span data-stu-id="08f67-243">Meaning</span></span> |
|-|-|
| `latest` | <span data-ttu-id="08f67-244">Yayınlanan en son kod Çözümleyicileri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="08f67-244">The latest code analyzers that have been released are used.</span></span> <span data-ttu-id="08f67-245">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="08f67-245">This is the default.</span></span> |
| `preview` | <span data-ttu-id="08f67-246">Önizleme aşamasında olsalar dahi, en son kod Çözümleyicileri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="08f67-246">The latest code analyzers are used, even if they are in preview.</span></span> |
| `5.0` | <span data-ttu-id="08f67-247">.NET 5,0 sürümü için etkinleştirilen kurallar kümesi, daha yeni kurallar kullanılabilir olsa bile kullanılır.</span><span class="sxs-lookup"><span data-stu-id="08f67-247">The set of rules that was enabled for the .NET 5.0 release is used, even if newer rules are available.</span></span> |
| `5` | <span data-ttu-id="08f67-248">.NET 5,0 sürümü için etkinleştirilen kurallar kümesi, daha yeni kurallar kullanılabilir olsa bile kullanılır.</span><span class="sxs-lookup"><span data-stu-id="08f67-248">The set of rules that was enabled for the .NET 5.0 release is used, even if newer rules are available.</span></span> |

> [!NOTE]
> <span data-ttu-id="08f67-249">Bu özelliğin, [Proje SDK 'sına](overview.md)başvurmayan projeler (örneğin, Microsoft. CodeAnalysis. Netçözümleyiciler NuGet paketine başvuran eski .NET Framework projeleri) üzerinde kod analizi üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="08f67-249">This property has no effect on code analysis in projects that don't reference a [project SDK](overview.md), for example, legacy .NET Framework projects that reference the Microsoft.CodeAnalysis.NetAnalyzers NuGet package.</span></span>

### <a name="analysismode"></a><span data-ttu-id="08f67-250">AnalysisMode</span><span class="sxs-lookup"><span data-stu-id="08f67-250">AnalysisMode</span></span>

<span data-ttu-id="08f67-251">.NET SDK, .NET 5,0 ile başlayarak ["CA" kod kalitesi kurallarıyla](../../fundamentals/code-analysis/quality-rules/index.md)birlikte gönderilir.</span><span class="sxs-lookup"><span data-stu-id="08f67-251">Starting with .NET 5.0, the .NET SDK ships with all of the ["CA" code quality rules](../../fundamentals/code-analysis/quality-rules/index.md).</span></span> <span data-ttu-id="08f67-252">Varsayılan olarak, yalnızca [bazı kurallar](../../fundamentals/code-analysis/overview.md#enabled-rules) derleme uyarıları olarak etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="08f67-252">By default, only [some rules are enabled](../../fundamentals/code-analysis/overview.md#enabled-rules) as build warnings.</span></span> <span data-ttu-id="08f67-253">`AnalysisMode`Özelliği, varsayılan olarak etkinleştirilen kuralların kümesini özelleştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="08f67-253">The `AnalysisMode` property lets you customize the set of rules that are enabled by default.</span></span> <span data-ttu-id="08f67-254">Daha Agresif (geri çevirme) çözümleme moduna veya daha koruyucu (katılım) analiz moduna geçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08f67-254">You can either switch to a more aggressive (opt-out) analysis mode or a more conservative (opt-in) analysis mode.</span></span> <span data-ttu-id="08f67-255">Örneğin, varsayılan olarak tüm kuralları derleme uyarıları olarak etkinleştirmek istiyorsanız, değerini olarak ayarlayın `AllEnabledByDefault` .</span><span class="sxs-lookup"><span data-stu-id="08f67-255">For example, if you want to enable all rules by default as build warnings, set the value to `AllEnabledByDefault`.</span></span>

```xml
<PropertyGroup>
  <AnalysisMode>AllEnabledByDefault</AnalysisMode>
</PropertyGroup>
```

<span data-ttu-id="08f67-256">Aşağıdaki tabloda kullanılabilir seçenekler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="08f67-256">The following table shows the available options.</span></span>

| <span data-ttu-id="08f67-257">Değer</span><span class="sxs-lookup"><span data-stu-id="08f67-257">Value</span></span> | <span data-ttu-id="08f67-258">Anlamı</span><span class="sxs-lookup"><span data-stu-id="08f67-258">Meaning</span></span> |
|-|-|
| `Default` | <span data-ttu-id="08f67-259">Belirli kuralların derleme uyarıları olarak etkinleştirildiği varsayılan mod, Visual Studio IDE önerisi olarak bazı kurallar etkinleştirilir ve geri kalanı devre dışı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="08f67-259">Default mode, where certain rules are enabled as build warnings, certain rules are enabled as Visual Studio IDE suggestions, and the remainder are disabled.</span></span> |
| `AllEnabledByDefault` | <span data-ttu-id="08f67-260">Tüm kuralların, derleme uyarıları olarak varsayılan olarak etkinleştirildiği agresif veya kabul etme modu.</span><span class="sxs-lookup"><span data-stu-id="08f67-260">Aggressive or opt-out mode, where all rules are enabled by default as build warnings.</span></span> <span data-ttu-id="08f67-261">Bağımsız kuralların devre dışı [bırakılacağını seçerek devre dışı bırakabilirsiniz](../../fundamentals/code-analysis/configuration-options.md) .</span><span class="sxs-lookup"><span data-stu-id="08f67-261">You can selectively [opt out](../../fundamentals/code-analysis/configuration-options.md) of individual rules to disable them.</span></span> |
| `AllDisabledByDefault` | <span data-ttu-id="08f67-262">Klasik veya kabul etme modu, tüm kurallar varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="08f67-262">Conservative or opt-in mode, where all rules are disabled by default.</span></span> <span data-ttu-id="08f67-263">Bunları etkinleştirmek için tek tek kuralların seçmeli olarak [tercih](../../fundamentals/code-analysis/configuration-options.md) edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08f67-263">You can selectively [opt into](../../fundamentals/code-analysis/configuration-options.md) individual rules to enable them.</span></span> |

> [!NOTE]
> <span data-ttu-id="08f67-264">Bu özelliğin, [Proje SDK 'sına](overview.md)başvurmayan projeler (örneğin, Microsoft. CodeAnalysis. Netçözümleyiciler NuGet paketine başvuran eski .NET Framework projeleri) üzerinde kod analizi üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="08f67-264">This property has no effect on code analysis in projects that don't reference a [project SDK](overview.md), for example, legacy .NET Framework projects that reference the Microsoft.CodeAnalysis.NetAnalyzers NuGet package.</span></span>

### <a name="codeanalysistreatwarningsaserrors"></a><span data-ttu-id="08f67-265">CodeAnalysisTreatWarningsAsErrors</span><span class="sxs-lookup"><span data-stu-id="08f67-265">CodeAnalysisTreatWarningsAsErrors</span></span>

<span data-ttu-id="08f67-266">`CodeAnalysisTreatWarningsAsErrors`Özelliği, kod kalitesi analizi uyarılarının (CAxxxx) uyarı olarak değerlendirilip derlenmeyeceğini yapılandırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="08f67-266">The `CodeAnalysisTreatWarningsAsErrors` property lets you configure whether code quality analysis warnings (CAxxxx) should be treated as warnings and break the build.</span></span> <span data-ttu-id="08f67-267">Projelerinizi oluştururken bayrağını kullanırsanız `-warnaserror` , [.net Code Quality Analysis](../../fundamentals/code-analysis/overview.md#code-quality-analysis) uyarıları da hata olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="08f67-267">If you use the `-warnaserror` flag when you build your projects, [.NET code quality analysis](../../fundamentals/code-analysis/overview.md#code-quality-analysis) warnings are also treated as errors.</span></span> <span data-ttu-id="08f67-268">Kod kalitesi analiz uyarılarını hata olarak kabul etmek istemiyorsanız, `CodeAnalysisTreatWarningsAsErrors` MSBuild özelliğini `false` proje dosyanızda olarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08f67-268">If you do not want code quality analysis warnings to be treated as errors, you can set the `CodeAnalysisTreatWarningsAsErrors` MSBuild property to `false` in your project file.</span></span>

```xml
<PropertyGroup>
  <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
</PropertyGroup>
```

### <a name="enablenetanalyzers"></a><span data-ttu-id="08f67-269">Enablenetçözümleyiciler</span><span class="sxs-lookup"><span data-stu-id="08f67-269">EnableNETAnalyzers</span></span>

<span data-ttu-id="08f67-270">.Net [Code Quality Analysis](../../fundamentals/code-analysis/overview.md#code-quality-analysis) , .NET 5,0 veya üstünü hedefleyen projeler için varsayılan olarak etkinleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="08f67-270">[.NET code quality analysis](../../fundamentals/code-analysis/overview.md#code-quality-analysis) is enabled, by default, for projects that target .NET 5.0 or later.</span></span> <span data-ttu-id="08f67-271">Özelliğini olarak ayarlayarak .NET 'in önceki sürümlerini hedefleyen SDK stilindeki projeler için .NET kod analizini etkinleştirebilirsiniz `EnableNETAnalyzers` `true` .</span><span class="sxs-lookup"><span data-stu-id="08f67-271">You can enable .NET code analysis for SDK-style projects that target earlier versions of .NET by setting the `EnableNETAnalyzers` property to `true`.</span></span> <span data-ttu-id="08f67-272">Herhangi bir projede kod analizini devre dışı bırakmak için bu özelliği olarak ayarlayın `false` .</span><span class="sxs-lookup"><span data-stu-id="08f67-272">To disable code analysis in any project, set this property to `false`.</span></span>

```xml
<PropertyGroup>
  <EnableNETAnalyzers>true</EnableNETAnalyzers>
</PropertyGroup>
```

> [!NOTE]
> <span data-ttu-id="08f67-273">Bu özellik özellikle .NET 5 + SDK 'daki yerleşik çözümleyiciler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="08f67-273">This property applies specifically to the built-in analyzers in the .NET 5+ SDK.</span></span> <span data-ttu-id="08f67-274">Bir NuGet kod analizi paketi yüklediğinizde kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="08f67-274">It should not be used when you install a NuGet code analysis package.</span></span>

### <a name="enforcecodestyleinbuild"></a><span data-ttu-id="08f67-275">Enforcecodestyleınbuild</span><span class="sxs-lookup"><span data-stu-id="08f67-275">EnforceCodeStyleInBuild</span></span>

> [!NOTE]
> <span data-ttu-id="08f67-276">Bu özellik şu anda deneysel ve .NET 5 ve .NET 6 sürümleri arasında değişebilir.</span><span class="sxs-lookup"><span data-stu-id="08f67-276">This feature is currently experimental and may change between the .NET 5 and .NET 6 releases.</span></span>

<span data-ttu-id="08f67-277">[.NET kod stili Analizi](../../fundamentals/code-analysis/overview.md#code-style-analysis) , varsayılan olarak tüm .NET projeleri için derleme üzerinde devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="08f67-277">[.NET code style analysis](../../fundamentals/code-analysis/overview.md#code-style-analysis) is disabled, by default, on build for all .NET projects.</span></span> <span data-ttu-id="08f67-278">Özelliğini olarak ayarlayarak .NET projeleri için kod stili analizini etkinleştirebilirsiniz `EnforceCodeStyleInBuild` `true` .</span><span class="sxs-lookup"><span data-stu-id="08f67-278">You can enable code style analysis for .NET projects by setting the `EnforceCodeStyleInBuild` property to `true`.</span></span>

```xml
<PropertyGroup>
  <EnforceCodeStyleInBuild>true</EnforceCodeStyleInBuild>
</PropertyGroup>
```

<span data-ttu-id="08f67-279">Uyarı veya hata olarak [yapılandırılan](../../fundamentals/code-analysis/overview.md#code-style-analysis) tüm kod stili kuralları, derleme ve rapor ihlalleri üzerinde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="08f67-279">All code style rules that are [configured](../../fundamentals/code-analysis/overview.md#code-style-analysis) to be warnings or errors will execute on build and report violations.</span></span>

## <a name="run-time-configuration-properties"></a><span data-ttu-id="08f67-280">Çalışma zamanı yapılandırma özellikleri</span><span class="sxs-lookup"><span data-stu-id="08f67-280">Run-time configuration properties</span></span>

<span data-ttu-id="08f67-281">Uygulamanın proje dosyasında MSBuild özelliklerini belirterek bazı çalışma zamanı davranışları yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08f67-281">You can configure some run-time behaviors by specifying MSBuild properties in the project file of the app.</span></span> <span data-ttu-id="08f67-282">Çalışma zamanı davranışını yapılandırmanın diğer yolları hakkında daha fazla bilgi için bkz. [çalışma zamanı yapılandırma ayarları](../run-time-config/index.md).</span><span class="sxs-lookup"><span data-stu-id="08f67-282">For information about other ways of configuring run-time behavior, see [Run-time configuration settings](../run-time-config/index.md).</span></span>

- [<span data-ttu-id="08f67-283">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="08f67-283">ConcurrentGarbageCollection</span></span>](#concurrentgarbagecollection)
- [<span data-ttu-id="08f67-284">Invariantgenelleştirme</span><span class="sxs-lookup"><span data-stu-id="08f67-284">InvariantGlobalization</span></span>](#invariantglobalization)
- [<span data-ttu-id="08f67-285">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="08f67-285">RetainVMGarbageCollection</span></span>](#retainvmgarbagecollection)
- [<span data-ttu-id="08f67-286">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="08f67-286">ServerGarbageCollection</span></span>](#servergarbagecollection)
- [<span data-ttu-id="08f67-287">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="08f67-287">ThreadPoolMaxThreads</span></span>](#threadpoolmaxthreads)
- [<span data-ttu-id="08f67-288">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="08f67-288">ThreadPoolMinThreads</span></span>](#threadpoolminthreads)
- [<span data-ttu-id="08f67-289">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="08f67-289">TieredCompilation</span></span>](#tieredcompilation)
- [<span data-ttu-id="08f67-290">Tieredcompilationquickjıt</span><span class="sxs-lookup"><span data-stu-id="08f67-290">TieredCompilationQuickJit</span></span>](#tieredcompilationquickjit)
- [<span data-ttu-id="08f67-291">Tieredcompilationquickjıtfordöngüleri</span><span class="sxs-lookup"><span data-stu-id="08f67-291">TieredCompilationQuickJitForLoops</span></span>](#tieredcompilationquickjitforloops)

### <a name="concurrentgarbagecollection"></a><span data-ttu-id="08f67-292">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="08f67-292">ConcurrentGarbageCollection</span></span>

<span data-ttu-id="08f67-293">`ConcurrentGarbageCollection`Özelliği [Background (eşzamanlı) Çöp toplamanın](../../standard/garbage-collection/background-gc.md) etkinleştirilip etkinleştirilmeyeceğini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="08f67-293">The `ConcurrentGarbageCollection` property configures whether [background (concurrent) garbage collection](../../standard/garbage-collection/background-gc.md) is enabled.</span></span> <span data-ttu-id="08f67-294">`false`Arka plan atık toplamayı devre dışı bırakmak için değerini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="08f67-294">Set the value to `false` to disable background garbage collection.</span></span> <span data-ttu-id="08f67-295">Daha fazla bilgi için bkz. [arka plan GC](../run-time-config/garbage-collector.md#background-gc).</span><span class="sxs-lookup"><span data-stu-id="08f67-295">For more information, see [Background GC](../run-time-config/garbage-collector.md#background-gc).</span></span>

```xml
<PropertyGroup>
  <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
</PropertyGroup>
```

### <a name="invariantglobalization"></a><span data-ttu-id="08f67-296">Invariantgenelleştirme</span><span class="sxs-lookup"><span data-stu-id="08f67-296">InvariantGlobalization</span></span>

<span data-ttu-id="08f67-297">`InvariantGlobalization`Özelliği, uygulamanın *Genelleştirme sabit* modunda çalışıp çalışmadığını yapılandırır, bu, kültüre özgü verilere erişimi olmayan anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="08f67-297">The `InvariantGlobalization` property configures whether the app runs in *globalization-invariant* mode, which means it doesn't have access to culture-specific data.</span></span> <span data-ttu-id="08f67-298">Değeri `true` Genelleştirme sabit modunda çalışacak şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="08f67-298">Set the value to `true` to run in globalization-invariant mode.</span></span> <span data-ttu-id="08f67-299">Daha fazla bilgi için bkz. [sabit mod](../run-time-config/globalization.md#invariant-mode).</span><span class="sxs-lookup"><span data-stu-id="08f67-299">For more information, see [Invariant mode](../run-time-config/globalization.md#invariant-mode).</span></span>

```xml
<PropertyGroup>
  <InvariantGlobalization>true</InvariantGlobalization>
</PropertyGroup>
```

### <a name="retainvmgarbagecollection"></a><span data-ttu-id="08f67-300">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="08f67-300">RetainVMGarbageCollection</span></span>

<span data-ttu-id="08f67-301">`RetainVMGarbageCollection`Özelliği, çöp toplayıcıyı, daha sonra kullanılmak üzere veya serbest bırakmak için silinen bellek segmentlerini bir bekleme listesine koymak üzere yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="08f67-301">The `RetainVMGarbageCollection` property configures the garbage collector to put deleted memory segments on a standby list for future use or release them.</span></span> <span data-ttu-id="08f67-302">Değeri, `true` çöp toplayıcıya kesimleri bir bekleme listesine koymasını söyler.</span><span class="sxs-lookup"><span data-stu-id="08f67-302">Setting the value to `true` tells the garbage collector to put the segments on a standby list.</span></span> <span data-ttu-id="08f67-303">Daha fazla bilgi için bkz. [VM 'Yi koruma](../run-time-config/garbage-collector.md#retain-vm).</span><span class="sxs-lookup"><span data-stu-id="08f67-303">For more information, see [Retain VM](../run-time-config/garbage-collector.md#retain-vm).</span></span>

```xml
<PropertyGroup>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
</PropertyGroup>
```

### <a name="servergarbagecollection"></a><span data-ttu-id="08f67-304">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="08f67-304">ServerGarbageCollection</span></span>

<span data-ttu-id="08f67-305">`ServerGarbageCollection`Özelliği, uygulamanın [iş istasyonu çöp toplamayı veya sunucu çöp toplamayı](../../standard/garbage-collection/workstation-server-gc.md)kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="08f67-305">The `ServerGarbageCollection` property configures whether the application uses [workstation garbage collection or server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span> <span data-ttu-id="08f67-306">Değerini `true` sunucu çöp toplamayı kullanacak şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="08f67-306">Set the value to `true` to use server garbage collection.</span></span> <span data-ttu-id="08f67-307">Daha fazla bilgi için bkz. [Workstation vs Server](../run-time-config/garbage-collector.md#workstation-vs-server).</span><span class="sxs-lookup"><span data-stu-id="08f67-307">For more information, see [Workstation vs. server](../run-time-config/garbage-collector.md#workstation-vs-server).</span></span>

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

### <a name="threadpoolmaxthreads"></a><span data-ttu-id="08f67-308">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="08f67-308">ThreadPoolMaxThreads</span></span>

<span data-ttu-id="08f67-309">`ThreadPoolMaxThreads`Özelliği, çalışan iş parçacığı havuzu için en fazla iş parçacığı sayısını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="08f67-309">The `ThreadPoolMaxThreads` property configures the maximum number of threads for the worker thread pool.</span></span> <span data-ttu-id="08f67-310">Daha fazla bilgi için bkz. [en fazla iş parçacığı](../run-time-config/threading.md#maximum-threads).</span><span class="sxs-lookup"><span data-stu-id="08f67-310">For more information, see [Maximum threads](../run-time-config/threading.md#maximum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
</PropertyGroup>
```

### <a name="threadpoolminthreads"></a><span data-ttu-id="08f67-311">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="08f67-311">ThreadPoolMinThreads</span></span>

<span data-ttu-id="08f67-312">`ThreadPoolMinThreads`Özelliği, çalışan iş parçacığı havuzu için en az iş parçacığı sayısını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="08f67-312">The `ThreadPoolMinThreads` property configures the minimum number of threads for the worker thread pool.</span></span> <span data-ttu-id="08f67-313">Daha fazla bilgi için bkz. [En düşük iş parçacıkları](../run-time-config/threading.md#minimum-threads).</span><span class="sxs-lookup"><span data-stu-id="08f67-313">For more information, see [Minimum threads](../run-time-config/threading.md#minimum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
</PropertyGroup>
```

### <a name="tieredcompilation"></a><span data-ttu-id="08f67-314">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="08f67-314">TieredCompilation</span></span>

<span data-ttu-id="08f67-315">`TieredCompilation`Özelliği, Just-In-Time (JIT) derleyicisinin [katmanlı derlemeyi](../whats-new/dotnet-core-3-0.md#tiered-compilation)kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="08f67-315">The `TieredCompilation` property configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="08f67-316">`false`Katmanlı derlemeyi devre dışı bırakmak için değerini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="08f67-316">Set the value to `false` to disable tiered compilation.</span></span> <span data-ttu-id="08f67-317">Daha fazla bilgi için bkz. [katmanlı derleme](../run-time-config/compilation.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="08f67-317">For more information, see [Tiered compilation](../run-time-config/compilation.md#tiered-compilation).</span></span>

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

### <a name="tieredcompilationquickjit"></a><span data-ttu-id="08f67-318">Tieredcompilationquickjıt</span><span class="sxs-lookup"><span data-stu-id="08f67-318">TieredCompilationQuickJit</span></span>

<span data-ttu-id="08f67-319">`TieredCompilationQuickJit`Özelliği, JIT derleyicisinin hızlı JIT kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="08f67-319">The `TieredCompilationQuickJit` property configures whether the JIT compiler uses quick JIT.</span></span> <span data-ttu-id="08f67-320">`false`Hızlı JIT 'i devre dışı bırakmak için değerini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="08f67-320">Set the value to `false` to disable quick JIT.</span></span> <span data-ttu-id="08f67-321">Daha fazla bilgi için bkz. [hızlı JIT](../run-time-config/compilation.md#quick-jit).</span><span class="sxs-lookup"><span data-stu-id="08f67-321">For more information, see [Quick JIT](../run-time-config/compilation.md#quick-jit).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

### <a name="tieredcompilationquickjitforloops"></a><span data-ttu-id="08f67-322">Tieredcompilationquickjıtfordöngüleri</span><span class="sxs-lookup"><span data-stu-id="08f67-322">TieredCompilationQuickJitForLoops</span></span>

<span data-ttu-id="08f67-323">`TieredCompilationQuickJitForLoops`Özelliği, JIT derleyicisinin döngüleri içeren yöntemlerde hızlı JIT kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="08f67-323">The `TieredCompilationQuickJitForLoops` property configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span> <span data-ttu-id="08f67-324">`true`Döngüleri içeren yöntemlerde hızlı JIT 'i etkinleştirmek için değerini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="08f67-324">Set the value to `true` to enable quick JIT on methods that contain loops.</span></span> <span data-ttu-id="08f67-325">Daha fazla bilgi için bkz. [döngüler Için hızlı JIT](../run-time-config/compilation.md#quick-jit-for-loops).</span><span class="sxs-lookup"><span data-stu-id="08f67-325">For more information, see [Quick JIT for loops](../run-time-config/compilation.md#quick-jit-for-loops).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
</PropertyGroup>
```

## <a name="reference-properties"></a><span data-ttu-id="08f67-326">Başvuru özellikleri</span><span class="sxs-lookup"><span data-stu-id="08f67-326">Reference properties</span></span>

<span data-ttu-id="08f67-327">Aşağıdaki MSBuild özellikleri bu bölümde belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="08f67-327">The following MSBuild properties are documented in this section:</span></span>

- [<span data-ttu-id="08f67-328">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="08f67-328">AssetTargetFallback</span></span>](#assettargetfallback)
- [<span data-ttu-id="08f67-329">DisableImplicitFrameworkReferences</span><span class="sxs-lookup"><span data-stu-id="08f67-329">DisableImplicitFrameworkReferences</span></span>](#disableimplicitframeworkreferences)
- [<span data-ttu-id="08f67-330">Geri yükleme ile ilgili özellikler</span><span class="sxs-lookup"><span data-stu-id="08f67-330">Restore-related properties</span></span>](#restore-related-properties)

### <a name="assettargetfallback"></a><span data-ttu-id="08f67-331">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="08f67-331">AssetTargetFallback</span></span>

<span data-ttu-id="08f67-332">`AssetTargetFallback`Özelliği, proje başvuruları ve NuGet paketleri için ek uyumlu çerçeve sürümlerini belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="08f67-332">The `AssetTargetFallback` property lets you specify additional compatible framework versions for project references and NuGet packages.</span></span> <span data-ttu-id="08f67-333">Örneğin, kullanarak bir paket bağımlılığı belirtirseniz `PackageReference` ancak bu paket, projelerinizle uyumlu olan varlıkları içermiyorsa `TargetFramework` , `AssetTargetFallback` özelliği yürütmeye gelir.</span><span class="sxs-lookup"><span data-stu-id="08f67-333">For example, if you specify a package dependency using `PackageReference` but that package doesn't contain assets that are compatible with your projects's `TargetFramework`, the `AssetTargetFallback` property comes into play.</span></span> <span data-ttu-id="08f67-334">Başvurulan paketin uyumluluğu, içinde belirtilen her bir hedef çerçeve kullanılarak yeniden denetlenir `AssetTargetFallback` .</span><span class="sxs-lookup"><span data-stu-id="08f67-334">The compatibility of the referenced package is rechecked using each target framework that's specified in `AssetTargetFallback`.</span></span> <span data-ttu-id="08f67-335">Bu özellik kullanımdan kaldırılan özelliğin yerini alır `PackageTargetFallback` .</span><span class="sxs-lookup"><span data-stu-id="08f67-335">This property replaces the deprecated property `PackageTargetFallback`.</span></span>

<span data-ttu-id="08f67-336">`AssetTargetFallback`Özelliğini bir veya daha fazla [hedef çerçeve sürümüne](../../standard/frameworks.md#supported-target-frameworks)ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08f67-336">You can set the `AssetTargetFallback` property to one or more [target framework versions](../../standard/frameworks.md#supported-target-frameworks).</span></span>

```xml
<PropertyGroup>
  <AssetTargetFallback>net461</AssetTargetFallback>
</PropertyGroup>
```

### <a name="disableimplicitframeworkreferences"></a><span data-ttu-id="08f67-337">DisableImplicitFrameworkReferences</span><span class="sxs-lookup"><span data-stu-id="08f67-337">DisableImplicitFrameworkReferences</span></span>

<span data-ttu-id="08f67-338">`DisableImplicitFrameworkReferences`Özelliği, `FrameworkReference` .net Core 3,0 ve sonraki sürümlerini hedeflerken örtük öğeleri denetler.</span><span class="sxs-lookup"><span data-stu-id="08f67-338">The `DisableImplicitFrameworkReferences` property controls implicit `FrameworkReference` items when targeting .NET Core 3.0 and later versions.</span></span> <span data-ttu-id="08f67-339">.NET Core 2,1 veya .NET Standard 2,0 ve önceki sürümlerini hedeflerken, bir metapackage içindeki paketlere örtük [Packagereference](#packagereference) öğelerini denetler.</span><span class="sxs-lookup"><span data-stu-id="08f67-339">When targeting .NET Core 2.1 or .NET Standard 2.0 and earlier versions, it controls implicit [PackageReference](#packagereference) items to packages in a metapackage.</span></span> <span data-ttu-id="08f67-340">(Metapackage, yalnızca diğer paketlerdeki bağımlılıklardan oluşan çerçeve tabanlı bir pakettir.) Bu özellik ayrıca `System` , .NET Framework hedefleme gibi örtülü başvuruları da denetler `System.Core` .</span><span class="sxs-lookup"><span data-stu-id="08f67-340">(A metapackage is a framework-based package that consist only of dependencies on other packages.) This property also controls implicit references such as `System` and `System.Core` when targeting .NET Framework.</span></span>

<span data-ttu-id="08f67-341">`true`Örtük `FrameworkReference` veya [packagereference](#packagereference) öğelerini devre dışı bırakmak için bu özelliği olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="08f67-341">Set this property to `true` to disable implicit `FrameworkReference` or [PackageReference](#packagereference) items.</span></span> <span data-ttu-id="08f67-342">Bu özelliği olarak ayarlarsanız `true` , yalnızca ihtiyacınız olan çerçevelere veya paketlere açık başvurular ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08f67-342">If you set this property to `true`, you can add explicit references to just the frameworks or packages you need.</span></span>

```xml
<PropertyGroup>
  <DisableImplicitFrameworkReferences>true</DisableImplicitFrameworkReferences>
</PropertyGroup>
```

### <a name="restore-related-properties"></a><span data-ttu-id="08f67-343">Geri yükleme ile ilgili özellikler</span><span class="sxs-lookup"><span data-stu-id="08f67-343">Restore-related properties</span></span>

<span data-ttu-id="08f67-344">Başvurulan bir paketin geri yüklenmesi, tüm doğrudan bağımlılıklarını ve bu bağımlılıkların tüm bağımlılıklarını yükler.</span><span class="sxs-lookup"><span data-stu-id="08f67-344">Restoring a referenced package installs all of its direct dependencies and all the dependencies of those dependencies.</span></span> <span data-ttu-id="08f67-345">Ve gibi özellikler belirterek paket geri yüklemesini özelleştirebilirsiniz `RestorePackagesPath` `RestoreIgnoreFailedSources` .</span><span class="sxs-lookup"><span data-stu-id="08f67-345">You can customize package restoration by specifying properties such as `RestorePackagesPath` and `RestoreIgnoreFailedSources`.</span></span> <span data-ttu-id="08f67-346">Bu ve diğer özellikler hakkında daha fazla bilgi için bkz. [hedefi geri yükleme](/nuget/reference/msbuild-targets#restore-target).</span><span class="sxs-lookup"><span data-stu-id="08f67-346">For more information about these and other properties, see [restore target](/nuget/reference/msbuild-targets#restore-target).</span></span>

```xml
<PropertyGroup>
  <RestoreIgnoreFailedSource>true</RestoreIgnoreFailedSource>
</PropertyGroup>
```

## <a name="run-related-properties"></a><span data-ttu-id="08f67-347">Çalışma ile ilgili özellikler</span><span class="sxs-lookup"><span data-stu-id="08f67-347">Run-related properties</span></span>

<span data-ttu-id="08f67-348">Aşağıdaki özellikler, komutuyla bir uygulama başlatmak için kullanılır [`dotnet run`](../tools/dotnet-run.md) :</span><span class="sxs-lookup"><span data-stu-id="08f67-348">The following properties are used for launching an app with the [`dotnet run`](../tools/dotnet-run.md) command:</span></span>

- [<span data-ttu-id="08f67-349">RunArguments</span><span class="sxs-lookup"><span data-stu-id="08f67-349">RunArguments</span></span>](#runarguments)
- [<span data-ttu-id="08f67-350">RunWorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="08f67-350">RunWorkingDirectory</span></span>](#runworkingdirectory)

### <a name="runarguments"></a><span data-ttu-id="08f67-351">RunArguments</span><span class="sxs-lookup"><span data-stu-id="08f67-351">RunArguments</span></span>

<span data-ttu-id="08f67-352">`RunArguments`Özelliği, çalıştırıldığında uygulamaya geçirilen bağımsız değişkenleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="08f67-352">The `RunArguments` property defines the arguments that are passed to the app when it is run.</span></span>

```xml
<PropertyGroup>
  <RunArguments>-mode dryrun</RunArguments>
</PropertyGroup>
```

> [!TIP]
> <span data-ttu-id="08f67-353">[ `--` Seçeneğini `dotnet run` ](../tools/dotnet-run.md#options)kullanarak uygulamaya geçirilecek ek bağımsız değişkenler belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08f67-353">You can specify additional arguments to be passed to the app by using the [`--` option for `dotnet run`](../tools/dotnet-run.md#options).</span></span>

### <a name="runworkingdirectory"></a><span data-ttu-id="08f67-354">RunWorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="08f67-354">RunWorkingDirectory</span></span>

<span data-ttu-id="08f67-355">`RunWorkingDirectory`Özelliği, uygulamasında başlatılacak uygulama işleminin çalışma dizinini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="08f67-355">The `RunWorkingDirectory` property defines the working directory for the application process to be started in.</span></span> <span data-ttu-id="08f67-356">Bu, mutlak bir yol veya proje diziniyle ilişkili bir yol olabilir.</span><span class="sxs-lookup"><span data-stu-id="08f67-356">It can be an absolute path or a path that's relative to the project directory.</span></span> <span data-ttu-id="08f67-357">Bir dizin belirtmezseniz, `OutDir` çalışma dizini olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="08f67-357">If you don't specify a directory, `OutDir` is used as the working directory.</span></span>

```xml
<PropertyGroup>
  <RunWorkingDirectory>c:\temp</RunWorkingDirectory>
</PropertyGroup>
```

## <a name="hosting-related-properties"></a><span data-ttu-id="08f67-358">Barındırma ile ilgili özellikler</span><span class="sxs-lookup"><span data-stu-id="08f67-358">Hosting-related properties</span></span>

<span data-ttu-id="08f67-359">Aşağıdaki MSBuild özellikleri bu bölümde belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="08f67-359">The following MSBuild properties are documented in this section:</span></span>

- [<span data-ttu-id="08f67-360">EnableComHosting</span><span class="sxs-lookup"><span data-stu-id="08f67-360">EnableComHosting</span></span>](#enablecomhosting)
- [<span data-ttu-id="08f67-361">EnableDynamicLoading</span><span class="sxs-lookup"><span data-stu-id="08f67-361">EnableDynamicLoading</span></span>](#enabledynamicloading)

### <a name="enablecomhosting"></a><span data-ttu-id="08f67-362">EnableComHosting</span><span class="sxs-lookup"><span data-stu-id="08f67-362">EnableComHosting</span></span>

<span data-ttu-id="08f67-363">Özelliği, bir `EnableComHosting` derlemenin BIR com sunucusu sağladığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="08f67-363">The `EnableComHosting` property indicates that an assembly provides a COM server.</span></span> <span data-ttu-id="08f67-364">İçin ayarı `EnableComHosting` , `true` [EnableDynamicLoading](#enabledynamicloading) olduğunu da belirtir `true` .</span><span class="sxs-lookup"><span data-stu-id="08f67-364">Setting the `EnableComHosting` to `true` also implies that [EnableDynamicLoading](#enabledynamicloading) is `true`.</span></span>

```xml
<PropertyGroup>
  <EnableComHosting>True</EnableComHosting>
</PropertyGroup>
```

<span data-ttu-id="08f67-365">Daha fazla bilgi için bkz. [.net BILEŞENLERINI com 'Da kullanıma](../native-interop/expose-components-to-com.md)sunma.</span><span class="sxs-lookup"><span data-stu-id="08f67-365">For more information, see [Expose .NET components to COM](../native-interop/expose-components-to-com.md).</span></span>

### <a name="enabledynamicloading"></a><span data-ttu-id="08f67-366">EnableDynamicLoading</span><span class="sxs-lookup"><span data-stu-id="08f67-366">EnableDynamicLoading</span></span>

<span data-ttu-id="08f67-367">`EnableDynamicLoading`Özelliği, bir derlemenin dinamik olarak yüklenen bir bileşen olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="08f67-367">The `EnableDynamicLoading` property indicates that an assembly is a dynamically loaded component.</span></span> <span data-ttu-id="08f67-368">Bileşen bir [com kitaplığı](/windows/win32/com/the-component-object-model) veya [Yerel BIR konaktan kullanılabilecek](../tutorials/netcore-hosting.md)com olmayan bir kitaplık olabilir.</span><span class="sxs-lookup"><span data-stu-id="08f67-368">The component could be a [COM library](/windows/win32/com/the-component-object-model) or a non-COM library that can be [used from a native host](../tutorials/netcore-hosting.md).</span></span> <span data-ttu-id="08f67-369">Bu özelliğin olarak ayarlanması `true` aşağıdaki etkilere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="08f67-369">Setting this property to `true` has the following effects:</span></span>

- <span data-ttu-id="08f67-370">Dosyadaki bir *.runtimeconfig.js* oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="08f67-370">A *.runtimeconfig.json* file is generated.</span></span>
- <span data-ttu-id="08f67-371">[Ileri alma](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward) , olarak ayarlanır `LatestMinor` .</span><span class="sxs-lookup"><span data-stu-id="08f67-371">[Roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward) is set to `LatestMinor`.</span></span>
- <span data-ttu-id="08f67-372">NuGet başvuruları yerel olarak kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="08f67-372">NuGet references are copied locally.</span></span>

```xml
<PropertyGroup>
  <EnableDynamicLoading>true</EnableDynamicLoading>
</PropertyGroup>
```

## <a name="items"></a><span data-ttu-id="08f67-373">Öğeler</span><span class="sxs-lookup"><span data-stu-id="08f67-373">Items</span></span>

<span data-ttu-id="08f67-374">[MSBuild öğeleri](/visualstudio/msbuild/msbuild-items) , derleme sistemine giriş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="08f67-374">[MSBuild items](/visualstudio/msbuild/msbuild-items) are inputs into the build system.</span></span> <span data-ttu-id="08f67-375">Öğeler, öğe adı olan türlerine göre belirtilir.</span><span class="sxs-lookup"><span data-stu-id="08f67-375">Items are specified according to their type, which is the element name.</span></span> <span data-ttu-id="08f67-376">Örneğin, `Compile` ve `Reference` iki [ortak öğe türüdür](/visualstudio/msbuild/common-msbuild-project-items).</span><span class="sxs-lookup"><span data-stu-id="08f67-376">For example, `Compile` and `Reference` are two [common item types](/visualstudio/msbuild/common-msbuild-project-items).</span></span> <span data-ttu-id="08f67-377">Aşağıdaki ek öğe türleri .NET SDK tarafından kullanılabilir hale getirilir:</span><span class="sxs-lookup"><span data-stu-id="08f67-377">The following additional item types are made available by the .NET SDK:</span></span>

- [<span data-ttu-id="08f67-378">PackageReference</span><span class="sxs-lookup"><span data-stu-id="08f67-378">PackageReference</span></span>](#packagereference)
- [<span data-ttu-id="08f67-379">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="08f67-379">TrimmerRootAssembly</span></span>](#trimmerrootassembly)

<span data-ttu-id="08f67-380">Standart [öğe özniteliklerinden](/visualstudio/msbuild/item-element-msbuild#attributes-and-elements)herhangi birini, örneğin, `Include` ve `Update` , bu öğelerde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08f67-380">You can use any of the standard [item attributes](/visualstudio/msbuild/item-element-msbuild#attributes-and-elements), for example, `Include` and `Update`, on these items.</span></span> <span data-ttu-id="08f67-381">`Include`Yeni bir öğe eklemek ve `Update` var olan bir öğeyi değiştirmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="08f67-381">Use `Include` to add a new item, and use `Update` to modify an existing item.</span></span> <span data-ttu-id="08f67-382">Örneğin, `Update` genellikle .NET SDK 'sı tarafından dolaylı olarak eklenmiş bir öğeyi değiştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="08f67-382">For example, `Update` is often used to modify an item that has implicitly been added by the .NET SDK.</span></span>

### <a name="packagereference"></a><span data-ttu-id="08f67-383">PackageReference</span><span class="sxs-lookup"><span data-stu-id="08f67-383">PackageReference</span></span>

<span data-ttu-id="08f67-384">`PackageReference`Öğe, bir NuGet paketine bir başvuru tanımlar.</span><span class="sxs-lookup"><span data-stu-id="08f67-384">The `PackageReference` item defines a reference to a NuGet package.</span></span>

<span data-ttu-id="08f67-385">`Include`Öznitelik, paket kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="08f67-385">The `Include` attribute specifies the package ID.</span></span> <span data-ttu-id="08f67-386">`Version`Öznitelik, sürümü veya sürüm aralığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="08f67-386">The `Version` attribute specifies the version or version range.</span></span> <span data-ttu-id="08f67-387">En düşük sürüm, en yüksek sürüm, Aralık veya tam eşleşme belirtme hakkında bilgi için bkz. [Sürüm aralıkları](/nuget/concepts/package-versioning#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="08f67-387">For information about how to specify a minimum version, maximum version, range, or exact match, see [Version ranges](/nuget/concepts/package-versioning#version-ranges).</span></span>

<span data-ttu-id="08f67-388">Aşağıdaki örnekteki proje dosyası kod parçacığı [System. Runtime](https://www.nuget.org/packages/System.Runtime/) paketine başvurur.</span><span class="sxs-lookup"><span data-stu-id="08f67-388">The project file snippet in the following example references the [System.Runtime](https://www.nuget.org/packages/System.Runtime/) package.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="System.Runtime" Version="4.3.0" />
</ItemGroup>
```

<span data-ttu-id="08f67-389">[Bağımlılık varlıklarını](/nuget/consume-packages/package-references-in-project-files#controlling-dependency-assets) , gibi meta verileri kullanarak da denetleyebilirsiniz `PrivateAssets` .</span><span class="sxs-lookup"><span data-stu-id="08f67-389">You can also [control dependency assets](/nuget/consume-packages/package-references-in-project-files#controlling-dependency-assets) using metadata such as `PrivateAssets`.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Contoso.Utility.UsefulStuff" Version="3.6.0">
    <PrivateAssets>all</PrivateAssets>
  </PackageReference>
</ItemGroup>
```

<span data-ttu-id="08f67-390">Daha fazla bilgi için bkz. [Proje dosyalarındaki paket başvuruları](/nuget/consume-packages/package-references-in-project-files).</span><span class="sxs-lookup"><span data-stu-id="08f67-390">For more information, see [Package references in project files](/nuget/consume-packages/package-references-in-project-files).</span></span>

### <a name="trimmerrootassembly"></a><span data-ttu-id="08f67-391">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="08f67-391">TrimmerRootAssembly</span></span>

<span data-ttu-id="08f67-392">`TrimmerRootAssembly`Öğe, bir derlemeyi [*kırpmanıza*](../deploying/trim-self-contained.md)dışlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="08f67-392">The `TrimmerRootAssembly` item lets you exclude an assembly from [*trimming*](../deploying/trim-self-contained.md).</span></span> <span data-ttu-id="08f67-393">Kırpma, çalışma zamanının kullanılmayan parçalarını paketlenmiş bir uygulamadan kaldırma işlemidir.</span><span class="sxs-lookup"><span data-stu-id="08f67-393">Trimming is the process of removing unused parts of the runtime from a packaged application.</span></span> <span data-ttu-id="08f67-394">Bazı durumlarda, kırpma gerekli başvuruları yanlış kaldırabilir.</span><span class="sxs-lookup"><span data-stu-id="08f67-394">In some cases, trimming might incorrectly remove required references.</span></span>

<span data-ttu-id="08f67-395">Aşağıdaki XML, `System.Security` derlemeyi kırpmaya dışlar.</span><span class="sxs-lookup"><span data-stu-id="08f67-395">The following XML excludes the `System.Security` assembly from trimming.</span></span>

```xml
<ItemGroup>
  <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

## <a name="item-metadata"></a><span data-ttu-id="08f67-396">Öğe meta verileri</span><span class="sxs-lookup"><span data-stu-id="08f67-396">Item metadata</span></span>

<span data-ttu-id="08f67-397">Standart [MSBuild öğe özniteliklerine](/visualstudio/msbuild/item-element-msbuild#attributes-and-elements)ek olarak, aşağıdaki öğe meta veri ETIKETLERI .NET SDK tarafından kullanılabilir hale getirilir:</span><span class="sxs-lookup"><span data-stu-id="08f67-397">In addition to the standard [MSBuild item attributes](/visualstudio/msbuild/item-element-msbuild#attributes-and-elements), the following item metadata tags are made available by the .NET SDK:</span></span>

- [<span data-ttu-id="08f67-398">CopyToPublishDirectory</span><span class="sxs-lookup"><span data-stu-id="08f67-398">CopyToPublishDirectory</span></span>](#copytopublishdirectory)
- [<span data-ttu-id="08f67-399">Tabanlarını</span><span class="sxs-lookup"><span data-stu-id="08f67-399">LinkBase</span></span>](#linkbase)

### <a name="copytopublishdirectory"></a><span data-ttu-id="08f67-400">CopyToPublishDirectory</span><span class="sxs-lookup"><span data-stu-id="08f67-400">CopyToPublishDirectory</span></span>

<span data-ttu-id="08f67-401">`CopyToPublishDirectory`MSBuild öğesindeki meta veriler, öğe yayımlama dizinine kopyalandığında denetler.</span><span class="sxs-lookup"><span data-stu-id="08f67-401">The `CopyToPublishDirectory` metadata on an MSBuild item controls when the item is copied to the publish directory.</span></span> <span data-ttu-id="08f67-402">İzin verilen değerler `PreserveNewest` , yalnızca değiştirilirse öğeyi kopyalayan, `Always` her zaman öğeyi kopyalayan ve öğeyi `Never` hiçbir zaman kopyalamamış olan değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="08f67-402">Allowable values are `PreserveNewest`, which only copies the item if it has changed, `Always`, which always copies the item, and `Never`, which never copies the item.</span></span> <span data-ttu-id="08f67-403">Bir performans açısından, `PreserveNewest` artımlı bir derlemeyi sağladığından tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="08f67-403">From a performance standpoint, `PreserveNewest` is preferable because it enables an incremental build.</span></span>

```xml
<ItemGroup>
  <None Update="appsettings.Development.json" CopyToOutputDirectory="PreserveNewest" CopyToPublishDirectory="PreserveNewest" />
</ItemGroup>
```

### <a name="linkbase"></a><span data-ttu-id="08f67-404">Tabanlarını</span><span class="sxs-lookup"><span data-stu-id="08f67-404">LinkBase</span></span>

<span data-ttu-id="08f67-405">Proje dizini ve alt dizinleri dışında olan bir öğe için, Yayımla hedefi öğenin [bağlantı meta verilerini](/visualstudio/msbuild/common-msbuild-item-metadata) kullanarak öğenin nereye kopyalanacağını tespit edin.</span><span class="sxs-lookup"><span data-stu-id="08f67-405">For an item that's outside of the project directory and its subdirectories, the publish target uses the item's [Link metadata](/visualstudio/msbuild/common-msbuild-item-metadata) to determine where to copy the item to.</span></span> <span data-ttu-id="08f67-406">`Link` Ayrıca, proje ağacının dışındaki öğelerin Visual Studio 'nun Çözüm Gezgini penceresinde nasıl görüntüleneceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="08f67-406">`Link` also determines how items outside of the project tree are displayed in the Solution Explorer window of Visual Studio.</span></span>

<span data-ttu-id="08f67-407">`Link`Proje konisi dışında bir öğe için belirtilmemişse, varsayılan olarak öğesine ayarlanır `%(LinkBase)\%(RecursiveDir)%(Filename)%(Extension)` .</span><span class="sxs-lookup"><span data-stu-id="08f67-407">If `Link` is not specified for an item that's outside of the project cone, it defaults to `%(LinkBase)\%(RecursiveDir)%(Filename)%(Extension)`.</span></span> <span data-ttu-id="08f67-408">`LinkBase` Proje koni dışındaki öğeler için bir senerişilebilir taban klasörü belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="08f67-408">`LinkBase` lets you specify a sensible base folder for items outside of the project cone.</span></span> <span data-ttu-id="08f67-409">Taban klasörü altındaki klasör hiyerarşisi aracılığıyla korunur `RecursiveDir` .</span><span class="sxs-lookup"><span data-stu-id="08f67-409">The folder hierarchy under the base folder is preserved via `RecursiveDir`.</span></span> <span data-ttu-id="08f67-410">`LinkBase`Belirtilmemişse, `Link` yolundan çıkarılır.</span><span class="sxs-lookup"><span data-stu-id="08f67-410">If `LinkBase` is not specified, it's omitted from the `Link` path.</span></span>

```xml
<ItemGroup>
  <Content Include="..\Extras\**\*.cs" LinkBase="Shared"/>
</ItemGroup>
```

<span data-ttu-id="08f67-411">Aşağıdaki görüntüde, önceki öğe ile eklenen bir dosyanın `Include` Çözüm Gezgini ' de nasıl görüntüleyeceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="08f67-411">The following image shows how a file that's included via the previous item `Include` glob displays in Solution Explorer.</span></span>

:::image type="content" source="media/solution-explorer-linkbase.png" alt-text="Çözüm Gezgini bağlantı tabanının meta verileri içeren öğe gösteriliyor.":::

## <a name="see-also"></a><span data-ttu-id="08f67-413">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08f67-413">See also</span></span>

- [<span data-ttu-id="08f67-414">MSBuild şema başvurusu</span><span class="sxs-lookup"><span data-stu-id="08f67-414">MSBuild schema reference</span></span>](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [<span data-ttu-id="08f67-415">Ortak MSBuild özellikleri</span><span class="sxs-lookup"><span data-stu-id="08f67-415">Common MSBuild properties</span></span>](/visualstudio/msbuild/common-msbuild-project-properties)
- [<span data-ttu-id="08f67-416">NuGet paketi için MSBuild özellikleri</span><span class="sxs-lookup"><span data-stu-id="08f67-416">MSBuild properties for NuGet pack</span></span>](/nuget/reference/msbuild-targets#pack-target)
- [<span data-ttu-id="08f67-417">NuGet geri yükleme için MSBuild özellikleri</span><span class="sxs-lookup"><span data-stu-id="08f67-417">MSBuild properties for NuGet restore</span></span>](/nuget/reference/msbuild-targets#restore-properties)
- [<span data-ttu-id="08f67-418">Bir derlemeyi özelleştirme</span><span class="sxs-lookup"><span data-stu-id="08f67-418">Customize a build</span></span>](/visualstudio/msbuild/customize-your-build)
