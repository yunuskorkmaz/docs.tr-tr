---
title: Microsoft. NET. SDK için MSBuild özellikleri
description: MSBuild özellikleri ve .NET SDK tarafından anlaşılan öğeler için başvuru.
ms.date: 02/14/2020
ms.topic: reference
ms.custom: updateeachrelease
ms.openlocfilehash: effcb704056f553b2986ee4a61f73c0dc58af599
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636772"
---
# <a name="msbuild-reference-for-net-sdk-projects"></a><span data-ttu-id="9e569-103">.NET SDK projeleri için MSBuild başvurusu</span><span class="sxs-lookup"><span data-stu-id="9e569-103">MSBuild reference for .NET SDK projects</span></span>

<span data-ttu-id="9e569-104">Bu sayfa, MSBuild özelliklerine ve .NET projelerini yapılandırmak için kullanabileceğiniz öğelere yönelik bir başvurudur.</span><span class="sxs-lookup"><span data-stu-id="9e569-104">This page is a reference for the MSBuild properties and items that you can use to configure .NET projects.</span></span>

> [!NOTE]
> <span data-ttu-id="9e569-105">Bu sayfa devam eden bir çalışmadır ve .NET SDK için tüm kullanışlı MSBuild özelliklerini listelemez.</span><span class="sxs-lookup"><span data-stu-id="9e569-105">This page is a work in progress and does not list all of the useful MSBuild properties for the .NET SDK.</span></span> <span data-ttu-id="9e569-106">Ortak MSBuild özelliklerinin bir listesi için bkz. [Ortak MSBuild özellikleri](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="9e569-106">For a list of common MSBuild properties, see [Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="framework-properties"></a><span data-ttu-id="9e569-107">Çerçeve özellikleri</span><span class="sxs-lookup"><span data-stu-id="9e569-107">Framework properties</span></span>

<span data-ttu-id="9e569-108">Aşağıdaki MSBuild özellikleri bu bölümde belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="9e569-108">The following MSBuild properties are documented in this section:</span></span>

- [<span data-ttu-id="9e569-109">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="9e569-109">TargetFramework</span></span>](#targetframework)
- [<span data-ttu-id="9e569-110">Targetçerçeveler</span><span class="sxs-lookup"><span data-stu-id="9e569-110">TargetFrameworks</span></span>](#targetframeworks)
- [<span data-ttu-id="9e569-111">Netstandardımplicitpackageversion</span><span class="sxs-lookup"><span data-stu-id="9e569-111">NetStandardImplicitPackageVersion</span></span>](#netstandardimplicitpackageversion)

### <a name="targetframework"></a><span data-ttu-id="9e569-112">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="9e569-112">TargetFramework</span></span>

<span data-ttu-id="9e569-113">`TargetFramework`Özelliği, uygulamanın hedef Framework sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="9e569-113">The `TargetFramework` property specifies the target framework version for the app.</span></span> <span data-ttu-id="9e569-114">Geçerli hedef çerçeve takma adların listesi için bkz. [SDK stili projelerde hedef çerçeveler](../../standard/frameworks.md#supported-target-frameworks).</span><span class="sxs-lookup"><span data-stu-id="9e569-114">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-frameworks).</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>
```

<span data-ttu-id="9e569-115">Daha fazla bilgi için bkz. [SDK stili projelerde hedef çerçeveler](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="9e569-115">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="targetframeworks"></a><span data-ttu-id="9e569-116">Targetçerçeveler</span><span class="sxs-lookup"><span data-stu-id="9e569-116">TargetFrameworks</span></span>

<span data-ttu-id="9e569-117">`TargetFrameworks`Uygulamanızın birden çok platformu hedeflemesini istediğinizde özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="9e569-117">Use the `TargetFrameworks` property when you want your app to target multiple platforms.</span></span> <span data-ttu-id="9e569-118">Geçerli hedef çerçeve takma adların listesi için bkz. [SDK stili projelerde hedef çerçeveler](../../standard/frameworks.md#supported-target-frameworks).</span><span class="sxs-lookup"><span data-stu-id="9e569-118">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-frameworks).</span></span>

> [!NOTE]
> <span data-ttu-id="9e569-119">`TargetFramework`(Tekil) belirtilmişse bu özellik yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="9e569-119">This property is ignored if `TargetFramework` (singular) is specified.</span></span>

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
</PropertyGroup>
```

<span data-ttu-id="9e569-120">Daha fazla bilgi için bkz. [SDK stili projelerde hedef çerçeveler](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="9e569-120">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="netstandardimplicitpackageversion"></a><span data-ttu-id="9e569-121">Netstandardımplicitpackageversion</span><span class="sxs-lookup"><span data-stu-id="9e569-121">NetStandardImplicitPackageVersion</span></span>

> [!NOTE]
> <span data-ttu-id="9e569-122">Bu özellik yalnızca kullanan projeler için geçerlidir `netstandard1.x` .</span><span class="sxs-lookup"><span data-stu-id="9e569-122">This property only applies to projects using `netstandard1.x`.</span></span> <span data-ttu-id="9e569-123">Kullanan projeler için uygulanmaz `netstandard2.x` .</span><span class="sxs-lookup"><span data-stu-id="9e569-123">It doesn't apply to projects that use `netstandard2.x`.</span></span>

<span data-ttu-id="9e569-124">`NetStandardImplicitPackageVersion`Metapackage sürümünden daha düşük bir çerçeve sürümü belirtmek istediğinizde özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="9e569-124">Use the `NetStandardImplicitPackageVersion` property when you want to specify a framework version that's lower than the metapackage version.</span></span> <span data-ttu-id="9e569-125">Aşağıdaki örnekteki proje dosyası hedefler, `netstandard1.3` ancak 1.6.0 sürümünü kullanır `NETStandard.Library` .</span><span class="sxs-lookup"><span data-stu-id="9e569-125">The project file in the following example targets `netstandard1.3` but uses the 1.6.0 version of `NETStandard.Library`.</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netstandard1.3</TargetFramework>
  <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
</PropertyGroup>
```

## <a name="assembly-info-generation-properties"></a><span data-ttu-id="9e569-126">Derleme bilgileri oluşturma özellikleri</span><span class="sxs-lookup"><span data-stu-id="9e569-126">Assembly info generation properties</span></span>

- [<span data-ttu-id="9e569-127">GenerateAssemblyCompanyAttribute</span><span class="sxs-lookup"><span data-stu-id="9e569-127">GenerateAssemblyCompanyAttribute</span></span>](#generateassemblycompanyattribute)
- [<span data-ttu-id="9e569-128">GenerateAssemblyConfigurationAttribute</span><span class="sxs-lookup"><span data-stu-id="9e569-128">GenerateAssemblyConfigurationAttribute</span></span>](#generateassemblyconfigurationattribute)
- [<span data-ttu-id="9e569-129">GenerateAssemblyCopyrightAttribute</span><span class="sxs-lookup"><span data-stu-id="9e569-129">GenerateAssemblyCopyrightAttribute</span></span>](#generateassemblycopyrightattribute)
- [<span data-ttu-id="9e569-130">GenerateAssemblyDescriptionAttribute</span><span class="sxs-lookup"><span data-stu-id="9e569-130">GenerateAssemblyDescriptionAttribute</span></span>](#generateassemblydescriptionattribute)
- [<span data-ttu-id="9e569-131">GenerateAssemblyFileVersionAttribute</span><span class="sxs-lookup"><span data-stu-id="9e569-131">GenerateAssemblyFileVersionAttribute</span></span>](#generateassemblyfileversionattribute)
- [<span data-ttu-id="9e569-132">Generateassemblyınfo</span><span class="sxs-lookup"><span data-stu-id="9e569-132">GenerateAssemblyInfo</span></span>](#generateassemblyinfo)
- [<span data-ttu-id="9e569-133">Generateassemblyformationalversionattribute</span><span class="sxs-lookup"><span data-stu-id="9e569-133">GenerateAssemblyInformationalVersionAttribute</span></span>](#generateassemblyinformationalversionattribute)
- [<span data-ttu-id="9e569-134">GenerateAssemblyProductAttribute</span><span class="sxs-lookup"><span data-stu-id="9e569-134">GenerateAssemblyProductAttribute</span></span>](#generateassemblyproductattribute)
- [<span data-ttu-id="9e569-135">Generateassemblytitleözniteliği</span><span class="sxs-lookup"><span data-stu-id="9e569-135">GenerateAssemblyTitleAttribute</span></span>](#generateassemblytitleattribute)
- [<span data-ttu-id="9e569-136">GenerateAssemblyVersionAttribute</span><span class="sxs-lookup"><span data-stu-id="9e569-136">GenerateAssemblyVersionAttribute</span></span>](#generateassemblyversionattribute)
- [<span data-ttu-id="9e569-137">GeneratedAssemblyInfoFile</span><span class="sxs-lookup"><span data-stu-id="9e569-137">GeneratedAssemblyInfoFile</span></span>](#generatedassemblyinfofile)
- [<span data-ttu-id="9e569-138">GenerateNeutralResourcesLanguageAttribute</span><span class="sxs-lookup"><span data-stu-id="9e569-138">GenerateNeutralResourcesLanguageAttribute</span></span>](#generateneutralresourceslanguageattribute)

### <a name="generateassemblycompanyattribute"></a><span data-ttu-id="9e569-139">GenerateAssemblyCompanyAttribute</span><span class="sxs-lookup"><span data-stu-id="9e569-139">GenerateAssemblyCompanyAttribute</span></span>

<span data-ttu-id="9e569-140">Bu özellik, `Company` özelliğinin derleme için oluşturup üretmediğini denetler <xref:System.Reflection.AssemblyCompanyAttribute> .</span><span class="sxs-lookup"><span data-stu-id="9e569-140">This property controls whether or not the `Company` property generates the <xref:System.Reflection.AssemblyCompanyAttribute> for the assembly.</span></span> <span data-ttu-id="9e569-141">`true` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="9e569-141">The default value is `true`.</span></span>

```xml
<PropertyGroup>
  <GenerateAssemblyCompanyAttribute>false</GenerateAssemblyCompanyAttribute>
</PropertyGroup>
```

### <a name="generateassemblyconfigurationattribute"></a><span data-ttu-id="9e569-142">GenerateAssemblyConfigurationAttribute</span><span class="sxs-lookup"><span data-stu-id="9e569-142">GenerateAssemblyConfigurationAttribute</span></span>

<span data-ttu-id="9e569-143">Bu özellik, `Configuration` özelliğinin derleme için oluşturup üretmediğini denetler <xref:System.Reflection.AssemblyConfigurationAttribute> .</span><span class="sxs-lookup"><span data-stu-id="9e569-143">This property controls whether or not the `Configuration` property generates the <xref:System.Reflection.AssemblyConfigurationAttribute> for the assembly.</span></span> <span data-ttu-id="9e569-144">`true` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="9e569-144">The default value is `true`.</span></span>

```xml
<PropertyGroup>
  <GenerateAssemblyConfigurationAttribute>false</GenerateAssemblyConfigurationAttribute>
</PropertyGroup>
```

### <a name="generateassemblycopyrightattribute"></a><span data-ttu-id="9e569-145">GenerateAssemblyCopyrightAttribute</span><span class="sxs-lookup"><span data-stu-id="9e569-145">GenerateAssemblyCopyrightAttribute</span></span>

<span data-ttu-id="9e569-146">Bu özellik, `Copyright` özelliğinin derleme için oluşturup üretmediğini denetler <xref:System.Reflection.AssemblyCopyrightAttribute> .</span><span class="sxs-lookup"><span data-stu-id="9e569-146">This property controls whether or not the `Copyright` property generates the <xref:System.Reflection.AssemblyCopyrightAttribute> for the assembly.</span></span> <span data-ttu-id="9e569-147">`true` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="9e569-147">The default value is `true`.</span></span>

```xml
<PropertyGroup>
  <GenerateAssemblyCopyrightAttribute>false</GenerateAssemblyCopyrightAttribute>
</PropertyGroup>
```

### <a name="generateassemblydescriptionattribute"></a><span data-ttu-id="9e569-148">GenerateAssemblyDescriptionAttribute</span><span class="sxs-lookup"><span data-stu-id="9e569-148">GenerateAssemblyDescriptionAttribute</span></span>

<span data-ttu-id="9e569-149">Bu özellik, `Description` özelliğinin derleme için oluşturup üretmediğini denetler <xref:System.Reflection.AssemblyDescriptionAttribute> .</span><span class="sxs-lookup"><span data-stu-id="9e569-149">This property controls whether or not the `Description` property generates the <xref:System.Reflection.AssemblyDescriptionAttribute> for the assembly.</span></span> <span data-ttu-id="9e569-150">`true` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="9e569-150">The default value is `true`.</span></span>

```xml
<PropertyGroup>
  <GenerateAssemblyDescriptionAttribute>false</GenerateAssemblyDescriptionAttribute>
</PropertyGroup>
```

### <a name="generateassemblyfileversionattribute"></a><span data-ttu-id="9e569-151">GenerateAssemblyFileVersionAttribute</span><span class="sxs-lookup"><span data-stu-id="9e569-151">GenerateAssemblyFileVersionAttribute</span></span>

<span data-ttu-id="9e569-152">Bu özellik, `FileVersion` özelliğinin derleme için oluşturup üretmediğini denetler <xref:System.Reflection.AssemblyFileVersionAttribute> .</span><span class="sxs-lookup"><span data-stu-id="9e569-152">This property controls whether or not the `FileVersion` property generates the <xref:System.Reflection.AssemblyFileVersionAttribute> for the assembly.</span></span> <span data-ttu-id="9e569-153">`true` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="9e569-153">The default value is `true`.</span></span>

```xml
<PropertyGroup>
  <GenerateAssemblyFileVersionAttribute>false</GenerateAssemblyFileVersionAttribute>
</PropertyGroup>
```

### <a name="generateassemblyinfo"></a><span data-ttu-id="9e569-154">Generateassemblyınfo</span><span class="sxs-lookup"><span data-stu-id="9e569-154">GenerateAssemblyInfo</span></span>

<span data-ttu-id="9e569-155">`AssemblyInfo`Proje için öznitelik oluşturmayı denetler.</span><span class="sxs-lookup"><span data-stu-id="9e569-155">Controls `AssemblyInfo` attribute generation for the project.</span></span> <span data-ttu-id="9e569-156">`true` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="9e569-156">The default value is `true`.</span></span> <span data-ttu-id="9e569-157">`false`Dosya oluşturmayı devre dışı bırakmak için kullanın:</span><span class="sxs-lookup"><span data-stu-id="9e569-157">Use `false` to disable generation of the file:</span></span>

```xml
<PropertyGroup>
  <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
</PropertyGroup>
```

<span data-ttu-id="9e569-158">[Generatedassemblyınfofile](#generatedassemblyinfofile) ayarı oluşturulan dosyanın adını denetler.</span><span class="sxs-lookup"><span data-stu-id="9e569-158">The [GeneratedAssemblyInfoFile](#generatedassemblyinfofile) setting controls the name of the generated file.</span></span>

<span data-ttu-id="9e569-159">Değer olduğunda `GenerateAssemblyInfo` `true` , proje özellikleri `AssemblyInfo` özniteliklere dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="9e569-159">When the `GenerateAssemblyInfo` value is `true`, project properties are transformed into `AssemblyInfo` attributes.</span></span> <span data-ttu-id="9e569-160">Aşağıdaki tabloda, öznitelikleri üreten proje özellikleri ve bu nesli devre dışı bırakasağlayan özellikler listelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="9e569-160">The following table lists the project properties that generate the attributes, and the properties that can disable that generation:</span></span>

| <span data-ttu-id="9e569-161">Özellik</span><span class="sxs-lookup"><span data-stu-id="9e569-161">Property</span></span>               | <span data-ttu-id="9e569-162">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9e569-162">Attribute</span></span>                                                      | <span data-ttu-id="9e569-163">Devre dışı bırakılacak Özellik</span><span class="sxs-lookup"><span data-stu-id="9e569-163">Property to disable</span></span>                                                                               |
|------------------------|----------------------------------------------------------------|---------------------------------------------------------------------------------------------------|
| `Company`              | <xref:System.Reflection.AssemblyCompanyAttribute>              | [`GenerateAssemblyCompanyAttribute`](#generateassemblycompanyattribute)                           |
| `Configuration`        | <xref:System.Reflection.AssemblyConfigurationAttribute>        | [`GenerateAssemblyConfigurationAttribute`](#generateassemblyconfigurationattribute)               |
| `Copyright`            | <xref:System.Reflection.AssemblyCopyrightAttribute>            | [`GenerateAssemblyCopyrightAttribute`](#generateassemblycopyrightattribute)                       |
| `Description`          | <xref:System.Reflection.AssemblyDescriptionAttribute>          | [`GenerateAssemblyDescriptionAttribute`](#generateassemblydescriptionattribute)                   |
| `FileVersion`          | <xref:System.Reflection.AssemblyFileVersionAttribute>          | [`GenerateAssemblyFileVersionAttribute`](#generateassemblyfileversionattribute)                   |
| `InformationalVersion` | <xref:System.Reflection.AssemblyInformationalVersionAttribute> | [`GenerateAssemblyInformationalVersionAttribute`](#generateassemblyinformationalversionattribute) |
| `Product`              | <xref:System.Reflection.AssemblyProductAttribute>              | [`GenerateAssemblyProductAttribute`](#generateassemblyproductattribute)                           |
| `AssemblyTitle`        | <xref:System.Reflection.AssemblyTitleAttribute>                | [`GenerateAssemblyTitleAttribute`](#generateassemblytitleattribute)                               |
| `AssemblyVersion`      | <xref:System.Reflection.AssemblyVersionAttribute>              | [`GenerateAssemblyVersionAttribute`](#generateassemblyversionattribute)                           |
| `NeutralLanguage`      | <xref:System.Resources.NeutralResourcesLanguageAttribute>      | [`GenerateNeutralResourcesLanguageAttribute`](#generateneutralresourceslanguageattribute)         |

<span data-ttu-id="9e569-164">Bu ayarlarla ilgili notlar:</span><span class="sxs-lookup"><span data-stu-id="9e569-164">Notes about these settings:</span></span>

- <span data-ttu-id="9e569-165">`AssemblyVersion` ve `FileVersion` sonek olmadan değerine varsayılan değer `$(Version)` .</span><span class="sxs-lookup"><span data-stu-id="9e569-165">`AssemblyVersion` and `FileVersion` default to the value of `$(Version)` without the suffix.</span></span> <span data-ttu-id="9e569-166">Örneğin, ise, `$(Version)` `1.2.3-beta.4` değer olacaktır `1.2.3` .</span><span class="sxs-lookup"><span data-stu-id="9e569-166">For example, if `$(Version)` is `1.2.3-beta.4`, then the value would be `1.2.3`.</span></span>
- <span data-ttu-id="9e569-167">`InformationalVersion` Varsayılan değer olarak değeridir `$(Version)` .</span><span class="sxs-lookup"><span data-stu-id="9e569-167">`InformationalVersion` defaults to the value of `$(Version)`.</span></span>
- <span data-ttu-id="9e569-168">`$(SourceRevisionId)`Özelliği varsa, öğesine eklenir `InformationalVersion` .</span><span class="sxs-lookup"><span data-stu-id="9e569-168">If the `$(SourceRevisionId)` property is present, it's appended to `InformationalVersion`.</span></span> <span data-ttu-id="9e569-169">Kullanarak bu davranışı devre dışı bırakabilirsiniz `IncludeSourceRevisionInInformationalVersion` .</span><span class="sxs-lookup"><span data-stu-id="9e569-169">You can disable this behavior using `IncludeSourceRevisionInInformationalVersion`.</span></span>
- <span data-ttu-id="9e569-170">`Copyright``Description`Ayrıca, NuGet meta verileri için de Özellikler kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9e569-170">`Copyright` and `Description` properties are also used for NuGet metadata.</span></span>
- <span data-ttu-id="9e569-171">`Configuration`, varsayılan olarak `Debug` , tüm MSBuild hedefleri ile paylaşılır.</span><span class="sxs-lookup"><span data-stu-id="9e569-171">`Configuration`, which defaults to `Debug`, is shared with all MSBuild targets.</span></span> <span data-ttu-id="9e569-172">Bunu, `--configuration` `dotnet` Örneğin [DotNet Pack](../tools/dotnet-pack.md)gibi komutlar seçeneği aracılığıyla ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e569-172">You can set it via the `--configuration` option of `dotnet` commands, for example, [dotnet pack](../tools/dotnet-pack.md).</span></span>
- <span data-ttu-id="9e569-173">Bir NuGet paketi oluşturulurken bazı özelliklerden bazıları kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9e569-173">Some of the properties are used when creating a NuGet package.</span></span> <span data-ttu-id="9e569-174">Daha fazla bilgi için bkz. [paket özellikleri](#package-properties).</span><span class="sxs-lookup"><span data-stu-id="9e569-174">For more information, see [Package properties](#package-properties).</span></span>

#### <a name="migrating-from-net-framework"></a><span data-ttu-id="9e569-175">.NET Framework geçiş</span><span class="sxs-lookup"><span data-stu-id="9e569-175">Migrating from .NET Framework</span></span>

<span data-ttu-id="9e569-176">.NET Framework proje şablonları, bu derleme bilgileri öznitelikleri ayarlanmış bir kod dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9e569-176">.NET Framework project templates create a code file with these assembly info attributes set.</span></span> <span data-ttu-id="9e569-177">Dosya genellikle *.\Properties\AssemblyInfo.cs* veya *.\Properties\AssemblyInfo.vb* konumunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="9e569-177">The file is typically located at *.\Properties\AssemblyInfo.cs* or *.\Properties\AssemblyInfo.vb*.</span></span> <span data-ttu-id="9e569-178">SDK stili projeler, bu dosyayı proje ayarlarına göre sizin için oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9e569-178">SDK-style projects generate this file for you based on the project settings.</span></span> <span data-ttu-id="9e569-179">**Her ikisine birden sahip olamaz.**</span><span class="sxs-lookup"><span data-stu-id="9e569-179">**You can't have both.**</span></span> <span data-ttu-id="9e569-180">Kodunuzu .NET 5 (ve .NET Core 3,1) veya sonraki bir sürüme taşırken, aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="9e569-180">When porting your code to .NET 5 (and .NET Core 3.1) or later, do one of the following:</span></span>

- <span data-ttu-id="9e569-181">Olarak ayarlayarak derleme bilgisi özniteliklerini içeren geçici kod dosyasının oluşturulmasını devre dışı bırakın `GenerateAssemblyInfo` `false` .</span><span class="sxs-lookup"><span data-stu-id="9e569-181">Disable the generation of the temporary code file that contains the assembly info attributes by setting `GenerateAssemblyInfo` to `false`.</span></span> <span data-ttu-id="9e569-182">Bu, *AssemblyInfo* dosyanızı tutmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e569-182">This enables you to keep your *AssemblyInfo* file.</span></span>
- <span data-ttu-id="9e569-183">`AssemblyInfo`Dosyadaki ayarları proje dosyasına geçirin ve `AssemblyInfo` dosyayı silin.</span><span class="sxs-lookup"><span data-stu-id="9e569-183">Migrate the settings in the `AssemblyInfo` file to the project file, and delete the `AssemblyInfo` file.</span></span>

### <a name="generateassemblyinformationalversionattribute"></a><span data-ttu-id="9e569-184">Generateassemblyformationalversionattribute</span><span class="sxs-lookup"><span data-stu-id="9e569-184">GenerateAssemblyInformationalVersionAttribute</span></span>

<span data-ttu-id="9e569-185">Bu özellik, `InformationalVersion` özelliğinin derleme için oluşturup üretmediğini denetler <xref:System.Reflection.AssemblyInformationalVersionAttribute> .</span><span class="sxs-lookup"><span data-stu-id="9e569-185">This property controls whether or not the `InformationalVersion` property generates the <xref:System.Reflection.AssemblyInformationalVersionAttribute> for the assembly.</span></span> <span data-ttu-id="9e569-186">`true` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="9e569-186">The default value is `true`.</span></span>

```xml
<PropertyGroup>
  <GenerateAssemblyInformationalVersionAttribute>false</GenerateAssemblyInformationalVersionAttribute>
</PropertyGroup>
```

### <a name="generateassemblyproductattribute"></a><span data-ttu-id="9e569-187">GenerateAssemblyProductAttribute</span><span class="sxs-lookup"><span data-stu-id="9e569-187">GenerateAssemblyProductAttribute</span></span>

<span data-ttu-id="9e569-188">Bu özellik, `Product` özelliğinin derleme için oluşturup üretmediğini denetler <xref:System.Reflection.AssemblyProductAttribute> .</span><span class="sxs-lookup"><span data-stu-id="9e569-188">This property controls whether or not the `Product` property generates the <xref:System.Reflection.AssemblyProductAttribute> for the assembly.</span></span> <span data-ttu-id="9e569-189">`true` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="9e569-189">The default value is `true`.</span></span>

```xml
<PropertyGroup>
  <GenerateAssemblyProductAttribute>false</GenerateAssemblyProductAttribute>
</PropertyGroup>
```

### <a name="generateassemblytitleattribute"></a><span data-ttu-id="9e569-190">Generateassemblytitleözniteliği</span><span class="sxs-lookup"><span data-stu-id="9e569-190">GenerateAssemblyTitleAttribute</span></span>

<span data-ttu-id="9e569-191">Bu özellik, `AssemblyTitle` özelliğinin derleme için oluşturup üretmediğini denetler <xref:System.Reflection.AssemblyTitleAttribute> .</span><span class="sxs-lookup"><span data-stu-id="9e569-191">This property controls whether or not the `AssemblyTitle` property generates the <xref:System.Reflection.AssemblyTitleAttribute> for the assembly.</span></span> <span data-ttu-id="9e569-192">`true` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="9e569-192">The default value is `true`.</span></span>

```xml
<PropertyGroup>
  <GenerateAssemblyTitleAttribute>false</GenerateAssemblyTitleAttribute>
</PropertyGroup>
```

### <a name="generateassemblyversionattribute"></a><span data-ttu-id="9e569-193">GenerateAssemblyVersionAttribute</span><span class="sxs-lookup"><span data-stu-id="9e569-193">GenerateAssemblyVersionAttribute</span></span>

<span data-ttu-id="9e569-194">Bu özellik, `AssemblyVersion` özelliğinin derleme için oluşturup üretmediğini denetler <xref:System.Reflection.AssemblyVersionAttribute> .</span><span class="sxs-lookup"><span data-stu-id="9e569-194">This property controls whether or not the `AssemblyVersion` property generates the <xref:System.Reflection.AssemblyVersionAttribute> for the assembly.</span></span> <span data-ttu-id="9e569-195">`true` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="9e569-195">The default value is `true`.</span></span>

```xml
<PropertyGroup>
  <GenerateAssemblyVersionAttribute>false</GenerateAssemblyVersionAttribute>
</PropertyGroup>
```

### <a name="generatedassemblyinfofile"></a><span data-ttu-id="9e569-196">GeneratedAssemblyInfoFile</span><span class="sxs-lookup"><span data-stu-id="9e569-196">GeneratedAssemblyInfoFile</span></span>

<span data-ttu-id="9e569-197">Özelliği, oluşturulan derleme bilgi dosyasının göreli veya mutlak yolunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9e569-197">The property defines the relative or absolute path of the generated assembly info file.</span></span> <span data-ttu-id="9e569-198">Varsayılan olarak *[proje-adı] adlı bir dosya olarak adlandırılır. AssemblyInfo. [CS | vb]* `$(IntermediateOutputPath)` (genellikle *obj*) dizininde.</span><span class="sxs-lookup"><span data-stu-id="9e569-198">Defaults to a file named *[project-name].AssemblyInfo.[cs|vb]* in the `$(IntermediateOutputPath)` (usually the *obj*) directory.</span></span>

```xml
<PropertyGroup>
  <GeneratedAssemblyInfoFile>assemblyinfo.cs</GeneratedAssemblyInfoFile>
</PropertyGroup>
```

### <a name="generateneutralresourceslanguageattribute"></a><span data-ttu-id="9e569-199">GenerateNeutralResourcesLanguageAttribute</span><span class="sxs-lookup"><span data-stu-id="9e569-199">GenerateNeutralResourcesLanguageAttribute</span></span>

<span data-ttu-id="9e569-200">Bu özellik, `NeutralLanguage` özelliğinin derleme için oluşturup üretmediğini denetler <xref:System.Resources.NeutralResourcesLanguageAttribute> .</span><span class="sxs-lookup"><span data-stu-id="9e569-200">This property controls whether or not the `NeutralLanguage` property generates the <xref:System.Resources.NeutralResourcesLanguageAttribute> for the assembly.</span></span> <span data-ttu-id="9e569-201">`true` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="9e569-201">The default value is `true`.</span></span>

```xml
<PropertyGroup>
  <GenerateNeutralResourcesLanguageAttribute>false</GenerateNeutralResourcesLanguageAttribute>
</PropertyGroup>
```

## <a name="package-properties"></a><span data-ttu-id="9e569-202">Paket özellikleri</span><span class="sxs-lookup"><span data-stu-id="9e569-202">Package properties</span></span>

<span data-ttu-id="9e569-203">`PackageId` `PackageVersion` `PackageIcon` `Title` `Description` Projenizden oluşturulan paketi betimleyen,,, ve gibi özellikleri belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e569-203">You can specify properties such as `PackageId`, `PackageVersion`, `PackageIcon`, `Title`, and `Description` to describe the package that gets created from your project.</span></span> <span data-ttu-id="9e569-204">Bu ve diğer özellikler hakkında daha fazla bilgi için bkz. [Pack Target](/nuget/reference/msbuild-targets#pack-target).</span><span class="sxs-lookup"><span data-stu-id="9e569-204">For information about these and other properties, see [pack target](/nuget/reference/msbuild-targets#pack-target).</span></span>

```xml
<PropertyGroup>
  ...
  <PackageId>ClassLibDotNetStandard</PackageId>
  <Version>1.0.0</Version>
  <Authors>John Doe</Authors>
  <Company>Contoso</Company>
</PropertyGroup>
```

## <a name="publish-related-properties"></a><span data-ttu-id="9e569-205">Yayınla ilgili özellikler</span><span class="sxs-lookup"><span data-stu-id="9e569-205">Publish-related properties</span></span>

<span data-ttu-id="9e569-206">Aşağıdaki MSBuild özellikleri bu bölümde belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="9e569-206">The following MSBuild properties are documented in this section:</span></span>

- [<span data-ttu-id="9e569-207">Appendruntimeıdentifiertooutputpath</span><span class="sxs-lookup"><span data-stu-id="9e569-207">AppendRuntimeIdentifierToOutputPath</span></span>](#appendruntimeidentifiertooutputpath)
- [<span data-ttu-id="9e569-208">AppendTargetFrameworkToOutputPath</span><span class="sxs-lookup"><span data-stu-id="9e569-208">AppendTargetFrameworkToOutputPath</span></span>](#appendtargetframeworktooutputpath)
- [<span data-ttu-id="9e569-209">CopyLocalLockFileAssemblies</span><span class="sxs-lookup"><span data-stu-id="9e569-209">CopyLocalLockFileAssemblies</span></span>](#copylocallockfileassemblies)
- [<span data-ttu-id="9e569-210">PreserveCompilationContext</span><span class="sxs-lookup"><span data-stu-id="9e569-210">PreserveCompilationContext</span></span>](#preservecompilationcontext)
- [<span data-ttu-id="9e569-211">PreserveCompilationReferences</span><span class="sxs-lookup"><span data-stu-id="9e569-211">PreserveCompilationReferences</span></span>](#preservecompilationreferences)
- [<span data-ttu-id="9e569-212">Runtimeıdentifier</span><span class="sxs-lookup"><span data-stu-id="9e569-212">RuntimeIdentifier</span></span>](#runtimeidentifier)
- [<span data-ttu-id="9e569-213">Runtimetanımlayıcıtanımlayıcıları</span><span class="sxs-lookup"><span data-stu-id="9e569-213">RuntimeIdentifiers</span></span>](#runtimeidentifiers)
- [<span data-ttu-id="9e569-214">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="9e569-214">UseAppHost</span></span>](#useapphost)

### <a name="appendtargetframeworktooutputpath"></a><span data-ttu-id="9e569-215">AppendTargetFrameworkToOutputPath</span><span class="sxs-lookup"><span data-stu-id="9e569-215">AppendTargetFrameworkToOutputPath</span></span>

<span data-ttu-id="9e569-216">`AppendTargetFrameworkToOutputPath`Özelliği, [hedef çerçeve adının (TFI)](../../standard/frameworks.md) çıkış yolunun ( [OutputPath](/visualstudio/msbuild/common-msbuild-project-properties#list-of-common-properties-and-parameters)tarafından tanımlanan) eklenip eklenmeyeceğini denetler.</span><span class="sxs-lookup"><span data-stu-id="9e569-216">The `AppendTargetFrameworkToOutputPath` property controls whether the [target framework moniker (TFM)](../../standard/frameworks.md) is appended to the output path (which is defined by [OutputPath](/visualstudio/msbuild/common-msbuild-project-properties#list-of-common-properties-and-parameters)).</span></span> <span data-ttu-id="9e569-217">.NET SDK, hedef çerçeveyi otomatik olarak ekler ve varsa, çalışma zamanı tanımlayıcısını çıkış yoluna ekler.</span><span class="sxs-lookup"><span data-stu-id="9e569-217">The .NET SDK automatically appends the target framework and, if present, the runtime identifier to the output path.</span></span> <span data-ttu-id="9e569-218">`AppendTargetFrameworkToOutputPath`İçin ayarı `false` , TFI 'nin çıkış yoluna eklenmesini engeller.</span><span class="sxs-lookup"><span data-stu-id="9e569-218">Setting `AppendTargetFrameworkToOutputPath` to `false` prevents the TFM from being appended to the output path.</span></span> <span data-ttu-id="9e569-219">Ancak, çıkış yolunda TFı olmadan, birden çok derleme yapıtları birbirinin üzerine yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="9e569-219">However, without the TFM in the output path, multiple build artifacts may overwrite each other.</span></span>

<span data-ttu-id="9e569-220">Örneğin, bir .NET 5,0 uygulaması için çıkış yolu, ' dan ' ı `bin\Debug\net5.0` `bin\Debug` aşağıdaki ayarla olarak değişir:</span><span class="sxs-lookup"><span data-stu-id="9e569-220">For example, for a .NET 5.0 app, the output path changes from `bin\Debug\net5.0` to `bin\Debug` with the following setting:</span></span>

```xml
<PropertyGroup>
  <AppendTargetFrameworkToOutputPath>false</AppendTargetFrameworkToOutputPath>
</PropertyGroup>
```

### <a name="appendruntimeidentifiertooutputpath"></a><span data-ttu-id="9e569-221">Appendruntimeıdentifiertooutputpath</span><span class="sxs-lookup"><span data-stu-id="9e569-221">AppendRuntimeIdentifierToOutputPath</span></span>

<span data-ttu-id="9e569-222">`AppendRuntimeIdentifierToOutputPath`Özelliği, [çalışma zamanı TANıMLAYıCıSıNıN (RID)](../rid-catalog.md) çıkış yolunun sonuna eklenip eklenmeyeceğini denetler.</span><span class="sxs-lookup"><span data-stu-id="9e569-222">The `AppendRuntimeIdentifierToOutputPath` property controls whether the [runtime identifier (RID)](../rid-catalog.md) is appended to the output path.</span></span> <span data-ttu-id="9e569-223">.NET SDK, hedef çerçeveyi otomatik olarak ekler ve varsa, çalışma zamanı tanımlayıcısını çıkış yoluna ekler.</span><span class="sxs-lookup"><span data-stu-id="9e569-223">The .NET SDK automatically appends the target framework and, if present, the runtime identifier to the output path.</span></span> <span data-ttu-id="9e569-224">`AppendRuntimeIdentifierToOutputPath`İçin ayarı `false` , RID 'nin çıkış yoluna eklenmesini önler.</span><span class="sxs-lookup"><span data-stu-id="9e569-224">Setting `AppendRuntimeIdentifierToOutputPath` to `false` prevents the RID from being appended to the output path.</span></span>

<span data-ttu-id="9e569-225">Örneğin, bir .NET 5,0 uygulaması ve bir RID 'si için `win10-x64` çıkış yolu, ' dan ' ı `bin\Debug\net5.0\win10-x64` `bin\Debug\net5.0` aşağıdaki ayarla olarak değişir:</span><span class="sxs-lookup"><span data-stu-id="9e569-225">For example, for a .NET 5.0 app and an RID of `win10-x64`, the output path changes from `bin\Debug\net5.0\win10-x64` to `bin\Debug\net5.0` with the following setting:</span></span>

```xml
<PropertyGroup>
  <AppendRuntimeIdentifierToOutputPath>false</AppendRuntimeIdentifierToOutputPath>
</PropertyGroup>
```

### <a name="copylocallockfileassemblies"></a><span data-ttu-id="9e569-226">CopyLocalLockFileAssemblies</span><span class="sxs-lookup"><span data-stu-id="9e569-226">CopyLocalLockFileAssemblies</span></span>

<span data-ttu-id="9e569-227">`CopyLocalLockFileAssemblies`Özelliği, diğer kitaplıklara bağımlılıkları olan eklenti projeleri için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="9e569-227">The `CopyLocalLockFileAssemblies` property is useful for plugin projects that have dependencies on other libraries.</span></span> <span data-ttu-id="9e569-228">Bu özelliği olarak ayarlarsanız `true` , herhangi bir NuGet paketi bağımlılığı çıkış dizinine kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="9e569-228">If you set this property to `true`, any NuGet package dependencies are copied to the output directory.</span></span> <span data-ttu-id="9e569-229">Diğer bir deyişle, `dotnet build` herhangi bir makinede kendi eklentisini çalıştırmak için çıkışını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e569-229">That means you can use the output of `dotnet build` to run your plugin on any machine.</span></span>

```xml
<PropertyGroup>
  <CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>
</PropertyGroup>
```

> [!TIP]
> <span data-ttu-id="9e569-230">Alternatif olarak, `dotnet publish` sınıf kitaplığını yayımlamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e569-230">Alternatively, you can use `dotnet publish` to publish the class library.</span></span> <span data-ttu-id="9e569-231">Daha fazla bilgi için bkz. [DotNet Publish](../tools/dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="9e569-231">For more information, see [dotnet publish](../tools/dotnet-publish.md).</span></span>

### <a name="preservecompilationcontext"></a><span data-ttu-id="9e569-232">PreserveCompilationContext</span><span class="sxs-lookup"><span data-stu-id="9e569-232">PreserveCompilationContext</span></span>

<span data-ttu-id="9e569-233">`PreserveCompilationContext`Özelliği, derleme zamanında kullanılan ayarların aynısını kullanarak, oluşturulmuş veya yayımlanmış bir uygulamanın çalışma zamanında daha fazla kod derlemesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="9e569-233">The `PreserveCompilationContext` property allows a built or published application to compile more code at run time using the same settings that were used at build time.</span></span> <span data-ttu-id="9e569-234">Derleme zamanında başvurulan derlemeler, çıkış dizininin *ref* alt dizinine kopyalanacak.</span><span class="sxs-lookup"><span data-stu-id="9e569-234">The assemblies referenced at build time will be copied into the *ref* subdirectory of the output directory.</span></span> <span data-ttu-id="9e569-235">Başvuru derlemelerinin adları, derleyicisine geçirilen seçeneklerle birlikte uygulamanın.deps.jsdosya *üzerinde* depolanır.</span><span class="sxs-lookup"><span data-stu-id="9e569-235">The names of the reference assemblies are stored in the application's *.deps.json* file along with the options passed to the compiler.</span></span> <span data-ttu-id="9e569-236">Ve özelliklerini kullanarak bu bilgileri alabilirsiniz <xref:Microsoft.Extensions.DependencyModel.DependencyContext.CompileLibraries?displayProperty=nameWithType> <xref:Microsoft.Extensions.DependencyModel.DependencyContext.CompilationOptions?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="9e569-236">You can retrieve this information using the <xref:Microsoft.Extensions.DependencyModel.DependencyContext.CompileLibraries?displayProperty=nameWithType> and <xref:Microsoft.Extensions.DependencyModel.DependencyContext.CompilationOptions?displayProperty=nameWithType> properties.</span></span>

<span data-ttu-id="9e569-237">Bu işlevsellik çoğunlukla, Razor dosyalarının çalışma zamanı derlemesini desteklemek için ASP.NET Core MVC ve Razor sayfaları tarafından dahili olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9e569-237">This functionality is mostly used internally by ASP.NET Core MVC and Razor pages to support run-time compilation of Razor files.</span></span>

```xml
<PropertyGroup>
  <PreserveCompilationContext>true</PreserveCompilationContext>
</PropertyGroup>
```

### <a name="preservecompilationreferences"></a><span data-ttu-id="9e569-238">PreserveCompilationReferences</span><span class="sxs-lookup"><span data-stu-id="9e569-238">PreserveCompilationReferences</span></span>

<span data-ttu-id="9e569-239">`PreserveCompilationReferences`Özelliği [Preservecompilationcontext](#preservecompilationcontext) özelliğine benzerdir, ancak yalnızca başvurulan derlemeler dosya *.deps.js* değil yayımlama dizinine kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="9e569-239">The `PreserveCompilationReferences` property is similar to the [PreserveCompilationContext](#preservecompilationcontext) property, except that it only copies the referenced assemblies to the publish directory, and not the *.deps.json* file.</span></span>

```xml
<PropertyGroup>
  <PreserveCompilationReferences>true</PreserveCompilationReferences>
</PropertyGroup>
```

<span data-ttu-id="9e569-240">Daha fazla bilgi için bkz. [Razor SDK özellikleri](/aspnet/core/razor-pages/sdk#properties).</span><span class="sxs-lookup"><span data-stu-id="9e569-240">For more information, see [Razor SDK properties](/aspnet/core/razor-pages/sdk#properties).</span></span>

### <a name="runtimeidentifier"></a><span data-ttu-id="9e569-241">Runtimeıdentifier</span><span class="sxs-lookup"><span data-stu-id="9e569-241">RuntimeIdentifier</span></span>

<span data-ttu-id="9e569-242">`RuntimeIdentifier`Özelliği, proje için tek bir [çalışma zamanı tanımlayıcısı (RID)](../rid-catalog.md) belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="9e569-242">The `RuntimeIdentifier` property lets you specify a single [runtime identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="9e569-243">RID, kendi kendine içerilen bir dağıtımı yayımlamayı mümkün.</span><span class="sxs-lookup"><span data-stu-id="9e569-243">The RID enables publishing a self-contained deployment.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
</PropertyGroup>
```

### <a name="runtimeidentifiers"></a><span data-ttu-id="9e569-244">Runtimetanımlayıcıtanımlayıcıları</span><span class="sxs-lookup"><span data-stu-id="9e569-244">RuntimeIdentifiers</span></span>

<span data-ttu-id="9e569-245">`RuntimeIdentifiers`Özelliği, proje için bir [çalışma zamanı tanımlayıcıları (RID 'ler)](../rid-catalog.md) için noktalı virgülle ayrılmış bir liste belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="9e569-245">The `RuntimeIdentifiers` property lets you specify a semicolon-delimited list of [runtime identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="9e569-246">Birden çok çalışma zamanı için yayımlamanız gerekiyorsa bu özelliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="9e569-246">Use this property if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="9e569-247">`RuntimeIdentifiers` , doğru varlıkların grafikte olduğundan emin olmak için geri yükleme zamanında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9e569-247">`RuntimeIdentifiers` is used at restore time to ensure the right assets are in the graph.</span></span>

> [!TIP]
> <span data-ttu-id="9e569-248">`RuntimeIdentifier` (tekil) yalnızca tek bir çalışma zamanı gerektiğinde daha hızlı derlemeler sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="9e569-248">`RuntimeIdentifier` (singular) can provide faster builds when only a single runtime is required.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
</PropertyGroup>
```

### <a name="useapphost"></a><span data-ttu-id="9e569-249">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="9e569-249">UseAppHost</span></span>

<span data-ttu-id="9e569-250">`UseAppHost`Özelliği, bir dağıtım için yerel yürütülebilir dosyanın oluşturulup oluşturulmayacağını denetler.</span><span class="sxs-lookup"><span data-stu-id="9e569-250">The `UseAppHost` property controls whether or not a native executable is created for a deployment.</span></span> <span data-ttu-id="9e569-251">Kendi kendine kapsanan dağıtımlar için yerel bir yürütülebilir dosya gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9e569-251">A native executable is required for self-contained deployments.</span></span>

<span data-ttu-id="9e569-252">.NET Core 3,0 ve sonraki sürümlerinde, çerçeveye bağlı bir yürütülebilir dosya varsayılan olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9e569-252">In .NET Core 3.0 and later versions, a framework-dependent executable is created by default.</span></span> <span data-ttu-id="9e569-253">`UseAppHost` `false` Yürütülebilir dosyanın üretilmesini devre dışı bırakmak için özelliğini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9e569-253">Set the `UseAppHost` property to `false` to disable generation of the executable.</span></span>

```xml
<PropertyGroup>
  <UseAppHost>false</UseAppHost>
</PropertyGroup>
```

<span data-ttu-id="9e569-254">Dağıtım hakkında daha fazla bilgi için bkz. [.NET uygulama dağıtımı](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="9e569-254">For more information about deployment, see [.NET application deployment](../deploying/index.md).</span></span>

## <a name="compilation-related-properties"></a><span data-ttu-id="9e569-255">Derlemeden ilgili özellikler</span><span class="sxs-lookup"><span data-stu-id="9e569-255">Compilation-related properties</span></span>

<span data-ttu-id="9e569-256">Aşağıdaki MSBuild özellikleri bu bölümde belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="9e569-256">The following MSBuild properties are documented in this section:</span></span>

- [<span data-ttu-id="9e569-257">Embeddedresourceusebağımlıtuponconvention</span><span class="sxs-lookup"><span data-stu-id="9e569-257">EmbeddedResourceUseDependentUponConvention</span></span>](#embeddedresourceusedependentuponconvention)
- [<span data-ttu-id="9e569-258">LangVersion</span><span class="sxs-lookup"><span data-stu-id="9e569-258">LangVersion</span></span>](#langversion)

### <a name="embeddedresourceusedependentuponconvention"></a><span data-ttu-id="9e569-259">Embeddedresourceusebağımlıtuponconvention</span><span class="sxs-lookup"><span data-stu-id="9e569-259">EmbeddedResourceUseDependentUponConvention</span></span>

<span data-ttu-id="9e569-260">Özelliği, kaynak dosyaları `EmbeddedResourceUseDependentUponConvention` ile birlikte bulunan kaynak dosyalardaki tür bilgilerden kaynak bildirim dosyası adlarının oluşturulup oluşturulmayacağını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9e569-260">The `EmbeddedResourceUseDependentUponConvention` property defines whether resource manifest file names are generated from type information in source files that are colocated with resource files.</span></span> <span data-ttu-id="9e569-261">Örneğin, *Form1. resx* *Form1. cs* ile aynı klasörssa ve olarak `EmbeddedResourceUseDependentUponConvention` ayarlanırsa `true` , oluşturulan *. resources* dosyası, adını *Form1. cs* dosyasında tanımlanan ilk türden alır.</span><span class="sxs-lookup"><span data-stu-id="9e569-261">For example, if *Form1.resx* is in the same folder as *Form1.cs*, and `EmbeddedResourceUseDependentUponConvention` is set to `true`, the generated *.resources* file takes its name from the first type that's defined in *Form1.cs*.</span></span> <span data-ttu-id="9e569-262">Örneğin, `MyNamespace.Form1` *Form1. cs* içinde tanımlanan ilk tür ise, oluşturulan dosya adı *MyNamespace. Form1. resources* olur.</span><span class="sxs-lookup"><span data-stu-id="9e569-262">For example, if `MyNamespace.Form1` is the first type defined in *Form1.cs*, the generated file name is *MyNamespace.Form1.resources*.</span></span>

> [!NOTE]
> <span data-ttu-id="9e569-263">`LogicalName`,, `ManifestResourceName` Veya `DependentUpon` meta veriler bir öğe için belirtilmişse `EmbeddedResource` , bu kaynak dosyası için oluşturulan bildirim dosyası adı bu meta verileri temel alır.</span><span class="sxs-lookup"><span data-stu-id="9e569-263">If `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for an `EmbeddedResource` item, the generated manifest file name for that resource file is based on that metadata instead.</span></span>

<span data-ttu-id="9e569-264">Varsayılan olarak, yeni bir .NET projesinde, bu özellik olarak ayarlanır `true` .</span><span class="sxs-lookup"><span data-stu-id="9e569-264">By default, in a new .NET project, this property is set to `true`.</span></span> <span data-ttu-id="9e569-265">`false`, Ve öğesi için, `LogicalName` `ManifestResourceName` Proje dosyasındaki öğe için, veya olarak ayarlanırsa,, `DependentUpon` `EmbeddedResource` kaynak bildirim dosyası adı projenin kök ad alanını ve *. resx* dosyasının göreli dosya yolunu temel alan olur.</span><span class="sxs-lookup"><span data-stu-id="9e569-265">If set to `false`, and no `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for the `EmbeddedResource` item in the project file, the resource manifest file name is based off the root namespace for the project and the relative file path to the *.resx* file.</span></span> <span data-ttu-id="9e569-266">Daha fazla bilgi için bkz. [kaynak bildirim dosyalarının adlandırılması](../resources/manifest-file-names.md).</span><span class="sxs-lookup"><span data-stu-id="9e569-266">For more information, see [How resource manifest files are named](../resources/manifest-file-names.md).</span></span>

```xml
<PropertyGroup>
  <EmbeddedResourceUseDependentUponConvention>true</EmbeddedResourceUseDependentUponConvention>
</PropertyGroup>
```

### <a name="langversion"></a><span data-ttu-id="9e569-267">LangVersion</span><span class="sxs-lookup"><span data-stu-id="9e569-267">LangVersion</span></span>

<span data-ttu-id="9e569-268">`LangVersion`Özelliği, belirli bir programlama dili sürümü belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e569-268">The `LangVersion` property lets you specify a specific programming language version.</span></span> <span data-ttu-id="9e569-269">Örneğin, C# önizleme özelliklerine erişmek istiyorsanız, `LangVersion` olarak ayarlayın `preview` .</span><span class="sxs-lookup"><span data-stu-id="9e569-269">For example, if you want access to C# preview features, set `LangVersion` to `preview`.</span></span>

```xml
<PropertyGroup>
  <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="9e569-270">Daha fazla bilgi için bkz. [C# dil sürümü oluşturma](../../csharp/language-reference/configure-language-version.md#override-a-default).</span><span class="sxs-lookup"><span data-stu-id="9e569-270">For more information, see [C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).</span></span>

## <a name="default-item-inclusion-properties"></a><span data-ttu-id="9e569-271">Varsayılan öğe içerme özellikleri</span><span class="sxs-lookup"><span data-stu-id="9e569-271">Default item inclusion properties</span></span>

<span data-ttu-id="9e569-272">Aşağıdaki MSBuild özellikleri bu bölümde belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="9e569-272">The following MSBuild properties are documented in this section:</span></span>

- [<span data-ttu-id="9e569-273">DefaultExcludesInProjectFolder</span><span class="sxs-lookup"><span data-stu-id="9e569-273">DefaultExcludesInProjectFolder</span></span>](#defaultexcludesinprojectfolder)
- [<span data-ttu-id="9e569-274">DefaultItemExcludes</span><span class="sxs-lookup"><span data-stu-id="9e569-274">DefaultItemExcludes</span></span>](#defaultitemexcludes)
- [<span data-ttu-id="9e569-275">Enabledefaultcompileıtems</span><span class="sxs-lookup"><span data-stu-id="9e569-275">EnableDefaultCompileItems</span></span>](#enabledefaultcompileitems)
- [<span data-ttu-id="9e569-276">Enabledefaultembeddedresourceıtems</span><span class="sxs-lookup"><span data-stu-id="9e569-276">EnableDefaultEmbeddedResourceItems</span></span>](#enabledefaultembeddedresourceitems)
- [<span data-ttu-id="9e569-277">Enabledefaultıtems</span><span class="sxs-lookup"><span data-stu-id="9e569-277">EnableDefaultItems</span></span>](#enabledefaultitems)
- [<span data-ttu-id="9e569-278">Enabledefaultnoneıtems</span><span class="sxs-lookup"><span data-stu-id="9e569-278">EnableDefaultNoneItems</span></span>](#enabledefaultnoneitems)

<span data-ttu-id="9e569-279">Daha fazla bilgi için bkz. [varsayılan içerme ve dışladığı](overview.md#default-includes-and-excludes).</span><span class="sxs-lookup"><span data-stu-id="9e569-279">For more information, see [Default includes and excludes](overview.md#default-includes-and-excludes).</span></span>

### <a name="defaultitemexcludes"></a><span data-ttu-id="9e569-280">DefaultItemExcludes</span><span class="sxs-lookup"><span data-stu-id="9e569-280">DefaultItemExcludes</span></span>

<span data-ttu-id="9e569-281">`DefaultItemExcludes`Include, exclude ve Remove genelleştirmeler dışında tutulması gereken dosya ve klasörler için glob desenleri tanımlamak üzere özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="9e569-281">Use the `DefaultItemExcludes` property to define glob patterns for files and folders that should be excluded from the include, exclude, and remove globs.</span></span> <span data-ttu-id="9e569-282">Varsayılan olarak, *./bin* ve *./obj* klasörleri, glob desenlerinden çıkarılır.</span><span class="sxs-lookup"><span data-stu-id="9e569-282">By default, the *./bin* and *./obj* folders are excluded from the glob patterns.</span></span>

```xml
<PropertyGroup>
  <DefaultItemExcludes>$(DefaultItemExcludes);**/*.myextension</DefaultItemExcludes>
</PropertyGroup>
```

### <a name="defaultexcludesinprojectfolder"></a><span data-ttu-id="9e569-283">DefaultExcludesInProjectFolder</span><span class="sxs-lookup"><span data-stu-id="9e569-283">DefaultExcludesInProjectFolder</span></span>

<span data-ttu-id="9e569-284">`DefaultExcludesInProjectFolder`Dahil etme, hariç tutma ve kaldırma genelleştirmeler dışında tutulacak proje klasöründeki dosya ve klasörler için glob desenlerini tanımlamak üzere özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="9e569-284">Use the `DefaultExcludesInProjectFolder` property to define glob patterns for files and folders in the project folder that should be excluded from the include, exclude, and remove globs.</span></span> <span data-ttu-id="9e569-285">Varsayılan olarak, `.` *. git* ve *. vs* gibi bir noktayla başlayan klasörler, glob desenlerinden çıkarılır.</span><span class="sxs-lookup"><span data-stu-id="9e569-285">By default, folders that start with a period (`.`), such as *.git* and *.vs*, are excluded from the glob patterns.</span></span>

<span data-ttu-id="9e569-286">Bu özellik, `DefaultItemExcludes` yalnızca proje klasöründeki dosya ve klasörleri dikkate almak dışında özelliğine çok benzer.</span><span class="sxs-lookup"><span data-stu-id="9e569-286">This property is very similar to the `DefaultItemExcludes` property, except that it only considers files and folders in the project folder.</span></span> <span data-ttu-id="9e569-287">Bir glob deseninin proje klasörü dışındaki öğeleri bir göreli yol ile istenmeden eşleşmesi durumunda, özelliği `DefaultExcludesInProjectFolder` yerine özelliğini kullanın `DefaultItemExcludes` .</span><span class="sxs-lookup"><span data-stu-id="9e569-287">When a glob pattern would unintentionally match items outside the project folder with a relative path, use the `DefaultExcludesInProjectFolder` property instead of the `DefaultItemExcludes` property.</span></span>

```xml
<PropertyGroup>
  <DefaultExcludesInProjectFolder>$(DefaultExcludesInProjectFolder);**/myprefix*/**</DefaultExcludesInProjectFolder>
</PropertyGroup>
```

### <a name="enabledefaultitems"></a><span data-ttu-id="9e569-288">Enabledefaultıtems</span><span class="sxs-lookup"><span data-stu-id="9e569-288">EnableDefaultItems</span></span>

<span data-ttu-id="9e569-289">`EnableDefaultItems`Özelliği derleme öğelerinin, katıştırılmış kaynak öğelerinin ve `None` öğelerin projeye örtük olarak dahil edilip edilmeyeceğini denetler.</span><span class="sxs-lookup"><span data-stu-id="9e569-289">The `EnableDefaultItems` property controls whether compile items, embedded resource items, and `None` items are implicitly included in the project.</span></span> <span data-ttu-id="9e569-290">`true` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="9e569-290">The default value is `true`.</span></span> <span data-ttu-id="9e569-291">`EnableDefaultItems` `false` Tüm örtük dosya dahil edilmesini devre dışı bırakmak için özelliğini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9e569-291">Set the `EnableDefaultItems` property to `false` to disable all implicit file inclusion.</span></span>

```xml
<PropertyGroup>
  <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

### <a name="enabledefaultcompileitems"></a><span data-ttu-id="9e569-292">Enabledefaultcompileıtems</span><span class="sxs-lookup"><span data-stu-id="9e569-292">EnableDefaultCompileItems</span></span>

<span data-ttu-id="9e569-293">`EnableDefaultCompileItems`Özelliği, derleme öğelerinin projeye örtük olarak dahil edilip edilmeyeceğini denetler.</span><span class="sxs-lookup"><span data-stu-id="9e569-293">The `EnableDefaultCompileItems` property controls whether compile items are implicitly included in the project.</span></span> <span data-ttu-id="9e569-294">`true` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="9e569-294">The default value is `true`.</span></span> <span data-ttu-id="9e569-295">`EnableDefaultCompileItems` `false` \*. Cs ve diğer dil uzantısı dosyalarının örtük olarak eklenmesini devre dışı bırakmak için özelliğini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9e569-295">Set the `EnableDefaultCompileItems` property to `false` to disable implicit inclusion of \*.cs and other language-extension files.</span></span>

```xml
<PropertyGroup>
  <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

### <a name="enabledefaultembeddedresourceitems"></a><span data-ttu-id="9e569-296">Enabledefaultembeddedresourceıtems</span><span class="sxs-lookup"><span data-stu-id="9e569-296">EnableDefaultEmbeddedResourceItems</span></span>

<span data-ttu-id="9e569-297">`EnableDefaultEmbeddedResourceItems`Özelliği, katıştırılmış kaynak öğelerinin projeye örtük olarak dahil edilip edilmeyeceğini denetler.</span><span class="sxs-lookup"><span data-stu-id="9e569-297">The `EnableDefaultEmbeddedResourceItems` property controls whether embedded resource items are implicitly included in the project.</span></span> <span data-ttu-id="9e569-298">`true` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="9e569-298">The default value is `true`.</span></span> <span data-ttu-id="9e569-299">`EnableDefaultEmbeddedResourceItems` `false` Gömülü kaynak dosyalarının örtük olarak eklenmesini devre dışı bırakmak için özelliğini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9e569-299">Set the `EnableDefaultEmbeddedResourceItems` property to `false` to disable implicit inclusion of embedded resource files.</span></span>

```xml
<PropertyGroup>
  <EnableDefaultEmbeddedResourceItems>false</EnableDefaultEmbeddedResourceItems>
</PropertyGroup>
```

### <a name="enabledefaultnoneitems"></a><span data-ttu-id="9e569-300">Enabledefaultnoneıtems</span><span class="sxs-lookup"><span data-stu-id="9e569-300">EnableDefaultNoneItems</span></span>

<span data-ttu-id="9e569-301">`EnableDefaultNoneItems`Özelliği, `None` öğelerin (yapı işleminde rolü olmayan dosyalar) örtük olarak projeye dahil edilip edilmeyeceğini denetler.</span><span class="sxs-lookup"><span data-stu-id="9e569-301">The `EnableDefaultNoneItems` property controls whether `None` items (files that have no role in the build process) are implicitly included in the project.</span></span> <span data-ttu-id="9e569-302">`true` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="9e569-302">The default value is `true`.</span></span> <span data-ttu-id="9e569-303">`EnableDefaultNoneItems`Özelliği `false` örtük olarak öğelerin dahil edilmesini devre dışı bırakmak için olarak ayarlayın `None` .</span><span class="sxs-lookup"><span data-stu-id="9e569-303">Set the `EnableDefaultNoneItems` property to `false` to disable implicit inclusion of `None` items.</span></span>

```xml
<PropertyGroup>
  <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

## <a name="code-analysis-properties"></a><span data-ttu-id="9e569-304">Kod Analizi özellikleri</span><span class="sxs-lookup"><span data-stu-id="9e569-304">Code analysis properties</span></span>

<span data-ttu-id="9e569-305">Aşağıdaki MSBuild özellikleri bu bölümde belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="9e569-305">The following MSBuild properties are documented in this section:</span></span>

- [<span data-ttu-id="9e569-306">AnalysisLevel</span><span class="sxs-lookup"><span data-stu-id="9e569-306">AnalysisLevel</span></span>](#analysislevel)
- [<span data-ttu-id="9e569-307">AnalysisMode</span><span class="sxs-lookup"><span data-stu-id="9e569-307">AnalysisMode</span></span>](#analysismode)
- [<span data-ttu-id="9e569-308">CodeAnalysisTreatWarningsAsErrors</span><span class="sxs-lookup"><span data-stu-id="9e569-308">CodeAnalysisTreatWarningsAsErrors</span></span>](#codeanalysistreatwarningsaserrors)
- [<span data-ttu-id="9e569-309">Enablenetçözümleyiciler</span><span class="sxs-lookup"><span data-stu-id="9e569-309">EnableNETAnalyzers</span></span>](#enablenetanalyzers)
- [<span data-ttu-id="9e569-310">Enforcecodestyleınbuild</span><span class="sxs-lookup"><span data-stu-id="9e569-310">EnforceCodeStyleInBuild</span></span>](#enforcecodestyleinbuild)

### <a name="analysislevel"></a><span data-ttu-id="9e569-311">AnalysisLevel</span><span class="sxs-lookup"><span data-stu-id="9e569-311">AnalysisLevel</span></span>

<span data-ttu-id="9e569-312">`AnalysisLevel`Özelliği, kod analizi düzeyi belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="9e569-312">The `AnalysisLevel` property lets you specify a code-analysis level.</span></span> <span data-ttu-id="9e569-313">Örneğin, önizleme kodu Çözümleyicileri için erişim istiyorsanız, `AnalysisLevel` olarak ayarlayın `preview` .</span><span class="sxs-lookup"><span data-stu-id="9e569-313">For example, if you want access to preview code analyzers, set `AnalysisLevel` to `preview`.</span></span>

<span data-ttu-id="9e569-314">Varsayılan değer:</span><span class="sxs-lookup"><span data-stu-id="9e569-314">Default value:</span></span>

- <span data-ttu-id="9e569-315">Projeniz .NET 5,0 veya üstünü hedefliyorsa veya [Analysismode](#analysismode) özelliğini eklediyseniz, varsayılan değer olur `latest` .</span><span class="sxs-lookup"><span data-stu-id="9e569-315">If your project targets .NET 5.0 or later, or if you've added the [AnalysisMode](#analysismode) property, the default value is `latest`.</span></span>
- <span data-ttu-id="9e569-316">Aksi takdirde, açıkça proje dosyasına eklemediğiniz takdirde bu özellik atlanır.</span><span class="sxs-lookup"><span data-stu-id="9e569-316">Otherwise, this property is omitted unless you explicitly add it to the project file.</span></span>

```xml
<PropertyGroup>
  <AnalysisLevel>preview</AnalysisLevel>
</PropertyGroup>
```

<span data-ttu-id="9e569-317">Aşağıdaki tabloda kullanılabilir seçenekler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9e569-317">The following table shows the available options.</span></span>

| <span data-ttu-id="9e569-318">Değer</span><span class="sxs-lookup"><span data-stu-id="9e569-318">Value</span></span> | <span data-ttu-id="9e569-319">Anlamı</span><span class="sxs-lookup"><span data-stu-id="9e569-319">Meaning</span></span> |
|-|-|
| `latest` | <span data-ttu-id="9e569-320">Yayınlanan en son kod Çözümleyicileri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9e569-320">The latest code analyzers that have been released are used.</span></span> <span data-ttu-id="9e569-321">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="9e569-321">This is the default.</span></span> |
| `preview` | <span data-ttu-id="9e569-322">Önizleme aşamasında olsalar dahi, en son kod Çözümleyicileri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9e569-322">The latest code analyzers are used, even if they are in preview.</span></span> |
| `5.0` | <span data-ttu-id="9e569-323">.NET 5,0 sürümü için etkinleştirilen kurallar kümesi, daha yeni kurallar kullanılabilir olsa bile kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9e569-323">The set of rules that was enabled for the .NET 5.0 release is used, even if newer rules are available.</span></span> |
| `5` | <span data-ttu-id="9e569-324">.NET 5,0 sürümü için etkinleştirilen kurallar kümesi, daha yeni kurallar kullanılabilir olsa bile kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9e569-324">The set of rules that was enabled for the .NET 5.0 release is used, even if newer rules are available.</span></span> |

> [!NOTE]
> <span data-ttu-id="9e569-325">Bu özelliğin, [Proje SDK 'sına](overview.md)başvurmayan projeler (örneğin, Microsoft. CodeAnalysis. Netçözümleyiciler NuGet paketine başvuran eski .NET Framework projeleri) üzerinde kod analizi üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="9e569-325">This property has no effect on code analysis in projects that don't reference a [project SDK](overview.md), for example, legacy .NET Framework projects that reference the Microsoft.CodeAnalysis.NetAnalyzers NuGet package.</span></span>

### <a name="analysismode"></a><span data-ttu-id="9e569-326">AnalysisMode</span><span class="sxs-lookup"><span data-stu-id="9e569-326">AnalysisMode</span></span>

<span data-ttu-id="9e569-327">.NET SDK, .NET 5,0 ile başlayarak ["CA" kod kalitesi kurallarıyla](../../fundamentals/code-analysis/quality-rules/index.md)birlikte gönderilir.</span><span class="sxs-lookup"><span data-stu-id="9e569-327">Starting with .NET 5.0, the .NET SDK ships with all of the ["CA" code quality rules](../../fundamentals/code-analysis/quality-rules/index.md).</span></span> <span data-ttu-id="9e569-328">Varsayılan olarak, yalnızca [bazı kurallar](../../fundamentals/code-analysis/overview.md#enabled-rules) derleme uyarıları olarak etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="9e569-328">By default, only [some rules are enabled](../../fundamentals/code-analysis/overview.md#enabled-rules) as build warnings.</span></span> <span data-ttu-id="9e569-329">`AnalysisMode`Özelliği, varsayılan olarak etkinleştirilen kuralların kümesini özelleştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e569-329">The `AnalysisMode` property lets you customize the set of rules that are enabled by default.</span></span> <span data-ttu-id="9e569-330">Daha Agresif (geri çevirme) çözümleme moduna veya daha koruyucu (katılım) analiz moduna geçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e569-330">You can either switch to a more aggressive (opt-out) analysis mode or a more conservative (opt-in) analysis mode.</span></span> <span data-ttu-id="9e569-331">Örneğin, varsayılan olarak tüm kuralları derleme uyarıları olarak etkinleştirmek istiyorsanız, değerini olarak ayarlayın `AllEnabledByDefault` .</span><span class="sxs-lookup"><span data-stu-id="9e569-331">For example, if you want to enable all rules by default as build warnings, set the value to `AllEnabledByDefault`.</span></span>

```xml
<PropertyGroup>
  <AnalysisMode>AllEnabledByDefault</AnalysisMode>
</PropertyGroup>
```

<span data-ttu-id="9e569-332">Aşağıdaki tabloda kullanılabilir seçenekler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9e569-332">The following table shows the available options.</span></span>

| <span data-ttu-id="9e569-333">Değer</span><span class="sxs-lookup"><span data-stu-id="9e569-333">Value</span></span> | <span data-ttu-id="9e569-334">Anlamı</span><span class="sxs-lookup"><span data-stu-id="9e569-334">Meaning</span></span> |
|-|-|
| `Default` | <span data-ttu-id="9e569-335">Belirli kuralların derleme uyarıları olarak etkinleştirildiği varsayılan mod, Visual Studio IDE önerisi olarak bazı kurallar etkinleştirilir ve geri kalanı devre dışı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="9e569-335">Default mode, where certain rules are enabled as build warnings, certain rules are enabled as Visual Studio IDE suggestions, and the remainder are disabled.</span></span> |
| `AllEnabledByDefault` | <span data-ttu-id="9e569-336">Tüm kuralların, derleme uyarıları olarak varsayılan olarak etkinleştirildiği agresif veya kabul etme modu.</span><span class="sxs-lookup"><span data-stu-id="9e569-336">Aggressive or opt-out mode, where all rules are enabled by default as build warnings.</span></span> <span data-ttu-id="9e569-337">Bağımsız kuralların devre dışı [bırakılacağını seçerek devre dışı bırakabilirsiniz](../../fundamentals/code-analysis/configuration-options.md) .</span><span class="sxs-lookup"><span data-stu-id="9e569-337">You can selectively [opt out](../../fundamentals/code-analysis/configuration-options.md) of individual rules to disable them.</span></span> |
| `AllDisabledByDefault` | <span data-ttu-id="9e569-338">Klasik veya kabul etme modu, tüm kurallar varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="9e569-338">Conservative or opt-in mode, where all rules are disabled by default.</span></span> <span data-ttu-id="9e569-339">Bunları etkinleştirmek için tek tek kuralların seçmeli olarak [tercih](../../fundamentals/code-analysis/configuration-options.md) edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e569-339">You can selectively [opt into](../../fundamentals/code-analysis/configuration-options.md) individual rules to enable them.</span></span> |

> [!NOTE]
> <span data-ttu-id="9e569-340">Bu özelliğin, [Proje SDK 'sına](overview.md)başvurmayan projeler (örneğin, Microsoft. CodeAnalysis. Netçözümleyiciler NuGet paketine başvuran eski .NET Framework projeleri) üzerinde kod analizi üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="9e569-340">This property has no effect on code analysis in projects that don't reference a [project SDK](overview.md), for example, legacy .NET Framework projects that reference the Microsoft.CodeAnalysis.NetAnalyzers NuGet package.</span></span>

### <a name="codeanalysistreatwarningsaserrors"></a><span data-ttu-id="9e569-341">CodeAnalysisTreatWarningsAsErrors</span><span class="sxs-lookup"><span data-stu-id="9e569-341">CodeAnalysisTreatWarningsAsErrors</span></span>

<span data-ttu-id="9e569-342">`CodeAnalysisTreatWarningsAsErrors`Özelliği, kod kalitesi analizi uyarılarının (CAxxxx) uyarı olarak değerlendirilip derlenmeyeceğini yapılandırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="9e569-342">The `CodeAnalysisTreatWarningsAsErrors` property lets you configure whether code quality analysis warnings (CAxxxx) should be treated as warnings and break the build.</span></span> <span data-ttu-id="9e569-343">Projelerinizi oluştururken bayrağını kullanırsanız `-warnaserror` , [.net Code Quality Analysis](../../fundamentals/code-analysis/overview.md#code-quality-analysis) uyarıları da hata olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="9e569-343">If you use the `-warnaserror` flag when you build your projects, [.NET code quality analysis](../../fundamentals/code-analysis/overview.md#code-quality-analysis) warnings are also treated as errors.</span></span> <span data-ttu-id="9e569-344">Kod kalitesi analiz uyarılarını hata olarak kabul etmek istemiyorsanız, `CodeAnalysisTreatWarningsAsErrors` MSBuild özelliğini `false` proje dosyanızda olarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e569-344">If you do not want code quality analysis warnings to be treated as errors, you can set the `CodeAnalysisTreatWarningsAsErrors` MSBuild property to `false` in your project file.</span></span>

```xml
<PropertyGroup>
  <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
</PropertyGroup>
```

### <a name="enablenetanalyzers"></a><span data-ttu-id="9e569-345">Enablenetçözümleyiciler</span><span class="sxs-lookup"><span data-stu-id="9e569-345">EnableNETAnalyzers</span></span>

<span data-ttu-id="9e569-346">.Net [Code Quality Analysis](../../fundamentals/code-analysis/overview.md#code-quality-analysis) , .NET 5,0 veya üstünü hedefleyen projeler için varsayılan olarak etkinleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9e569-346">[.NET code quality analysis](../../fundamentals/code-analysis/overview.md#code-quality-analysis) is enabled, by default, for projects that target .NET 5.0 or later.</span></span> <span data-ttu-id="9e569-347">Özelliğini olarak ayarlayarak .NET 'in önceki sürümlerini hedefleyen SDK stilindeki projeler için .NET kod analizini etkinleştirebilirsiniz `EnableNETAnalyzers` `true` .</span><span class="sxs-lookup"><span data-stu-id="9e569-347">You can enable .NET code analysis for SDK-style projects that target earlier versions of .NET by setting the `EnableNETAnalyzers` property to `true`.</span></span> <span data-ttu-id="9e569-348">Herhangi bir projede kod analizini devre dışı bırakmak için bu özelliği olarak ayarlayın `false` .</span><span class="sxs-lookup"><span data-stu-id="9e569-348">To disable code analysis in any project, set this property to `false`.</span></span>

```xml
<PropertyGroup>
  <EnableNETAnalyzers>true</EnableNETAnalyzers>
</PropertyGroup>
```

> [!NOTE]
> <span data-ttu-id="9e569-349">Bu özellik özellikle .NET 5 + SDK 'daki yerleşik çözümleyiciler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="9e569-349">This property applies specifically to the built-in analyzers in the .NET 5+ SDK.</span></span> <span data-ttu-id="9e569-350">Bir NuGet kod analizi paketi yüklediğinizde kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="9e569-350">It should not be used when you install a NuGet code analysis package.</span></span>

### <a name="enforcecodestyleinbuild"></a><span data-ttu-id="9e569-351">Enforcecodestyleınbuild</span><span class="sxs-lookup"><span data-stu-id="9e569-351">EnforceCodeStyleInBuild</span></span>

> [!NOTE]
> <span data-ttu-id="9e569-352">Bu özellik şu anda deneysel ve .NET 5 ve .NET 6 sürümleri arasında değişebilir.</span><span class="sxs-lookup"><span data-stu-id="9e569-352">This feature is currently experimental and may change between the .NET 5 and .NET 6 releases.</span></span>

<span data-ttu-id="9e569-353">[.NET kod stili Analizi](../../fundamentals/code-analysis/overview.md#code-style-analysis) , varsayılan olarak tüm .NET projeleri için derleme üzerinde devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="9e569-353">[.NET code style analysis](../../fundamentals/code-analysis/overview.md#code-style-analysis) is disabled, by default, on build for all .NET projects.</span></span> <span data-ttu-id="9e569-354">Özelliğini olarak ayarlayarak .NET projeleri için kod stili analizini etkinleştirebilirsiniz `EnforceCodeStyleInBuild` `true` .</span><span class="sxs-lookup"><span data-stu-id="9e569-354">You can enable code style analysis for .NET projects by setting the `EnforceCodeStyleInBuild` property to `true`.</span></span>

```xml
<PropertyGroup>
  <EnforceCodeStyleInBuild>true</EnforceCodeStyleInBuild>
</PropertyGroup>
```

<span data-ttu-id="9e569-355">Uyarı veya hata olarak [yapılandırılan](../../fundamentals/code-analysis/overview.md#code-style-analysis) tüm kod stili kuralları, derleme ve rapor ihlalleri üzerinde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="9e569-355">All code style rules that are [configured](../../fundamentals/code-analysis/overview.md#code-style-analysis) to be warnings or errors will execute on build and report violations.</span></span>

## <a name="run-time-configuration-properties"></a><span data-ttu-id="9e569-356">Çalışma zamanı yapılandırma özellikleri</span><span class="sxs-lookup"><span data-stu-id="9e569-356">Run-time configuration properties</span></span>

<span data-ttu-id="9e569-357">Uygulamanın proje dosyasında MSBuild özelliklerini belirterek bazı çalışma zamanı davranışları yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e569-357">You can configure some run-time behaviors by specifying MSBuild properties in the project file of the app.</span></span> <span data-ttu-id="9e569-358">Çalışma zamanı davranışını yapılandırmanın diğer yolları hakkında daha fazla bilgi için bkz. [çalışma zamanı yapılandırma ayarları](../run-time-config/index.md).</span><span class="sxs-lookup"><span data-stu-id="9e569-358">For information about other ways of configuring run-time behavior, see [Run-time configuration settings](../run-time-config/index.md).</span></span>

- [<span data-ttu-id="9e569-359">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="9e569-359">ConcurrentGarbageCollection</span></span>](#concurrentgarbagecollection)
- [<span data-ttu-id="9e569-360">Invariantgenelleştirme</span><span class="sxs-lookup"><span data-stu-id="9e569-360">InvariantGlobalization</span></span>](#invariantglobalization)
- [<span data-ttu-id="9e569-361">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="9e569-361">RetainVMGarbageCollection</span></span>](#retainvmgarbagecollection)
- [<span data-ttu-id="9e569-362">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="9e569-362">ServerGarbageCollection</span></span>](#servergarbagecollection)
- [<span data-ttu-id="9e569-363">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="9e569-363">ThreadPoolMaxThreads</span></span>](#threadpoolmaxthreads)
- [<span data-ttu-id="9e569-364">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="9e569-364">ThreadPoolMinThreads</span></span>](#threadpoolminthreads)
- [<span data-ttu-id="9e569-365">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="9e569-365">TieredCompilation</span></span>](#tieredcompilation)
- [<span data-ttu-id="9e569-366">Tieredcompilationquickjıt</span><span class="sxs-lookup"><span data-stu-id="9e569-366">TieredCompilationQuickJit</span></span>](#tieredcompilationquickjit)
- [<span data-ttu-id="9e569-367">Tieredcompilationquickjıtfordöngüleri</span><span class="sxs-lookup"><span data-stu-id="9e569-367">TieredCompilationQuickJitForLoops</span></span>](#tieredcompilationquickjitforloops)

### <a name="concurrentgarbagecollection"></a><span data-ttu-id="9e569-368">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="9e569-368">ConcurrentGarbageCollection</span></span>

<span data-ttu-id="9e569-369">`ConcurrentGarbageCollection`Özelliği [Background (eşzamanlı) Çöp toplamanın](../../standard/garbage-collection/background-gc.md) etkinleştirilip etkinleştirilmeyeceğini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="9e569-369">The `ConcurrentGarbageCollection` property configures whether [background (concurrent) garbage collection](../../standard/garbage-collection/background-gc.md) is enabled.</span></span> <span data-ttu-id="9e569-370">`false`Arka plan atık toplamayı devre dışı bırakmak için değerini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9e569-370">Set the value to `false` to disable background garbage collection.</span></span> <span data-ttu-id="9e569-371">Daha fazla bilgi için bkz. [arka plan GC](../run-time-config/garbage-collector.md#background-gc).</span><span class="sxs-lookup"><span data-stu-id="9e569-371">For more information, see [Background GC](../run-time-config/garbage-collector.md#background-gc).</span></span>

```xml
<PropertyGroup>
  <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
</PropertyGroup>
```

### <a name="invariantglobalization"></a><span data-ttu-id="9e569-372">Invariantgenelleştirme</span><span class="sxs-lookup"><span data-stu-id="9e569-372">InvariantGlobalization</span></span>

<span data-ttu-id="9e569-373">`InvariantGlobalization`Özelliği, uygulamanın *Genelleştirme sabit* modunda çalışıp çalışmadığını yapılandırır, bu, kültüre özgü verilere erişimi olmayan anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="9e569-373">The `InvariantGlobalization` property configures whether the app runs in *globalization-invariant* mode, which means it doesn't have access to culture-specific data.</span></span> <span data-ttu-id="9e569-374">Değeri `true` Genelleştirme sabit modunda çalışacak şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9e569-374">Set the value to `true` to run in globalization-invariant mode.</span></span> <span data-ttu-id="9e569-375">Daha fazla bilgi için bkz. [sabit mod](../run-time-config/globalization.md#invariant-mode).</span><span class="sxs-lookup"><span data-stu-id="9e569-375">For more information, see [Invariant mode](../run-time-config/globalization.md#invariant-mode).</span></span>

```xml
<PropertyGroup>
  <InvariantGlobalization>true</InvariantGlobalization>
</PropertyGroup>
```

### <a name="retainvmgarbagecollection"></a><span data-ttu-id="9e569-376">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="9e569-376">RetainVMGarbageCollection</span></span>

<span data-ttu-id="9e569-377">`RetainVMGarbageCollection`Özelliği, çöp toplayıcıyı, daha sonra kullanılmak üzere veya serbest bırakmak için silinen bellek segmentlerini bir bekleme listesine koymak üzere yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="9e569-377">The `RetainVMGarbageCollection` property configures the garbage collector to put deleted memory segments on a standby list for future use or release them.</span></span> <span data-ttu-id="9e569-378">Değeri, `true` çöp toplayıcıya kesimleri bir bekleme listesine koymasını söyler.</span><span class="sxs-lookup"><span data-stu-id="9e569-378">Setting the value to `true` tells the garbage collector to put the segments on a standby list.</span></span> <span data-ttu-id="9e569-379">Daha fazla bilgi için bkz. [VM 'Yi koruma](../run-time-config/garbage-collector.md#retain-vm).</span><span class="sxs-lookup"><span data-stu-id="9e569-379">For more information, see [Retain VM](../run-time-config/garbage-collector.md#retain-vm).</span></span>

```xml
<PropertyGroup>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
</PropertyGroup>
```

### <a name="servergarbagecollection"></a><span data-ttu-id="9e569-380">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="9e569-380">ServerGarbageCollection</span></span>

<span data-ttu-id="9e569-381">`ServerGarbageCollection`Özelliği, uygulamanın [iş istasyonu çöp toplamayı veya sunucu çöp toplamayı](../../standard/garbage-collection/workstation-server-gc.md)kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="9e569-381">The `ServerGarbageCollection` property configures whether the application uses [workstation garbage collection or server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span> <span data-ttu-id="9e569-382">Değerini `true` sunucu çöp toplamayı kullanacak şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9e569-382">Set the value to `true` to use server garbage collection.</span></span> <span data-ttu-id="9e569-383">Daha fazla bilgi için bkz. [Workstation vs Server](../run-time-config/garbage-collector.md#workstation-vs-server).</span><span class="sxs-lookup"><span data-stu-id="9e569-383">For more information, see [Workstation vs. server](../run-time-config/garbage-collector.md#workstation-vs-server).</span></span>

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

### <a name="threadpoolmaxthreads"></a><span data-ttu-id="9e569-384">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="9e569-384">ThreadPoolMaxThreads</span></span>

<span data-ttu-id="9e569-385">`ThreadPoolMaxThreads`Özelliği, çalışan iş parçacığı havuzu için en fazla iş parçacığı sayısını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="9e569-385">The `ThreadPoolMaxThreads` property configures the maximum number of threads for the worker thread pool.</span></span> <span data-ttu-id="9e569-386">Daha fazla bilgi için bkz. [en fazla iş parçacığı](../run-time-config/threading.md#maximum-threads).</span><span class="sxs-lookup"><span data-stu-id="9e569-386">For more information, see [Maximum threads](../run-time-config/threading.md#maximum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
</PropertyGroup>
```

### <a name="threadpoolminthreads"></a><span data-ttu-id="9e569-387">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="9e569-387">ThreadPoolMinThreads</span></span>

<span data-ttu-id="9e569-388">`ThreadPoolMinThreads`Özelliği, çalışan iş parçacığı havuzu için en az iş parçacığı sayısını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="9e569-388">The `ThreadPoolMinThreads` property configures the minimum number of threads for the worker thread pool.</span></span> <span data-ttu-id="9e569-389">Daha fazla bilgi için bkz. [En düşük iş parçacıkları](../run-time-config/threading.md#minimum-threads).</span><span class="sxs-lookup"><span data-stu-id="9e569-389">For more information, see [Minimum threads](../run-time-config/threading.md#minimum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
</PropertyGroup>
```

### <a name="tieredcompilation"></a><span data-ttu-id="9e569-390">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="9e569-390">TieredCompilation</span></span>

<span data-ttu-id="9e569-391">`TieredCompilation`Özelliği, Just-In-Time (JIT) derleyicisinin [katmanlı derlemeyi](../whats-new/dotnet-core-3-0.md#tiered-compilation)kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="9e569-391">The `TieredCompilation` property configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="9e569-392">`false`Katmanlı derlemeyi devre dışı bırakmak için değerini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9e569-392">Set the value to `false` to disable tiered compilation.</span></span> <span data-ttu-id="9e569-393">Daha fazla bilgi için bkz. [katmanlı derleme](../run-time-config/compilation.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="9e569-393">For more information, see [Tiered compilation](../run-time-config/compilation.md#tiered-compilation).</span></span>

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

### <a name="tieredcompilationquickjit"></a><span data-ttu-id="9e569-394">Tieredcompilationquickjıt</span><span class="sxs-lookup"><span data-stu-id="9e569-394">TieredCompilationQuickJit</span></span>

<span data-ttu-id="9e569-395">`TieredCompilationQuickJit`Özelliği, JIT derleyicisinin hızlı JIT kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="9e569-395">The `TieredCompilationQuickJit` property configures whether the JIT compiler uses quick JIT.</span></span> <span data-ttu-id="9e569-396">`false`Hızlı JIT 'i devre dışı bırakmak için değerini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9e569-396">Set the value to `false` to disable quick JIT.</span></span> <span data-ttu-id="9e569-397">Daha fazla bilgi için bkz. [hızlı JIT](../run-time-config/compilation.md#quick-jit).</span><span class="sxs-lookup"><span data-stu-id="9e569-397">For more information, see [Quick JIT](../run-time-config/compilation.md#quick-jit).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

### <a name="tieredcompilationquickjitforloops"></a><span data-ttu-id="9e569-398">Tieredcompilationquickjıtfordöngüleri</span><span class="sxs-lookup"><span data-stu-id="9e569-398">TieredCompilationQuickJitForLoops</span></span>

<span data-ttu-id="9e569-399">`TieredCompilationQuickJitForLoops`Özelliği, JIT derleyicisinin döngüleri içeren yöntemlerde hızlı JIT kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="9e569-399">The `TieredCompilationQuickJitForLoops` property configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span> <span data-ttu-id="9e569-400">`true`Döngüleri içeren yöntemlerde hızlı JIT 'i etkinleştirmek için değerini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9e569-400">Set the value to `true` to enable quick JIT on methods that contain loops.</span></span> <span data-ttu-id="9e569-401">Daha fazla bilgi için bkz. [döngüler Için hızlı JIT](../run-time-config/compilation.md#quick-jit-for-loops).</span><span class="sxs-lookup"><span data-stu-id="9e569-401">For more information, see [Quick JIT for loops](../run-time-config/compilation.md#quick-jit-for-loops).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
</PropertyGroup>
```

## <a name="reference-properties"></a><span data-ttu-id="9e569-402">Başvuru özellikleri</span><span class="sxs-lookup"><span data-stu-id="9e569-402">Reference properties</span></span>

<span data-ttu-id="9e569-403">Aşağıdaki MSBuild özellikleri bu bölümde belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="9e569-403">The following MSBuild properties are documented in this section:</span></span>

- [<span data-ttu-id="9e569-404">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="9e569-404">AssetTargetFallback</span></span>](#assettargetfallback)
- [<span data-ttu-id="9e569-405">DisableImplicitFrameworkReferences</span><span class="sxs-lookup"><span data-stu-id="9e569-405">DisableImplicitFrameworkReferences</span></span>](#disableimplicitframeworkreferences)
- [<span data-ttu-id="9e569-406">Geri yükleme ile ilgili özellikler</span><span class="sxs-lookup"><span data-stu-id="9e569-406">Restore-related properties</span></span>](#restore-related-properties)

### <a name="assettargetfallback"></a><span data-ttu-id="9e569-407">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="9e569-407">AssetTargetFallback</span></span>

<span data-ttu-id="9e569-408">`AssetTargetFallback`Özelliği, proje başvuruları ve NuGet paketleri için ek uyumlu çerçeve sürümlerini belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e569-408">The `AssetTargetFallback` property lets you specify additional compatible framework versions for project references and NuGet packages.</span></span> <span data-ttu-id="9e569-409">Örneğin, kullanarak bir paket bağımlılığı belirtirseniz `PackageReference` ancak bu paket, projelerinizle uyumlu olan varlıkları içermiyorsa `TargetFramework` , `AssetTargetFallback` özelliği yürütmeye gelir.</span><span class="sxs-lookup"><span data-stu-id="9e569-409">For example, if you specify a package dependency using `PackageReference` but that package doesn't contain assets that are compatible with your projects's `TargetFramework`, the `AssetTargetFallback` property comes into play.</span></span> <span data-ttu-id="9e569-410">Başvurulan paketin uyumluluğu, içinde belirtilen her bir hedef çerçeve kullanılarak yeniden denetlenir `AssetTargetFallback` .</span><span class="sxs-lookup"><span data-stu-id="9e569-410">The compatibility of the referenced package is rechecked using each target framework that's specified in `AssetTargetFallback`.</span></span> <span data-ttu-id="9e569-411">Bu özellik kullanımdan kaldırılan özelliğin yerini alır `PackageTargetFallback` .</span><span class="sxs-lookup"><span data-stu-id="9e569-411">This property replaces the deprecated property `PackageTargetFallback`.</span></span>

<span data-ttu-id="9e569-412">`AssetTargetFallback`Özelliğini bir veya daha fazla [hedef çerçeve sürümüne](../../standard/frameworks.md#supported-target-frameworks)ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e569-412">You can set the `AssetTargetFallback` property to one or more [target framework versions](../../standard/frameworks.md#supported-target-frameworks).</span></span>

```xml
<PropertyGroup>
  <AssetTargetFallback>net461</AssetTargetFallback>
</PropertyGroup>
```

### <a name="disableimplicitframeworkreferences"></a><span data-ttu-id="9e569-413">DisableImplicitFrameworkReferences</span><span class="sxs-lookup"><span data-stu-id="9e569-413">DisableImplicitFrameworkReferences</span></span>

<span data-ttu-id="9e569-414">`DisableImplicitFrameworkReferences`Özelliği, `FrameworkReference` .net Core 3,0 ve sonraki sürümlerini hedeflerken örtük öğeleri denetler.</span><span class="sxs-lookup"><span data-stu-id="9e569-414">The `DisableImplicitFrameworkReferences` property controls implicit `FrameworkReference` items when targeting .NET Core 3.0 and later versions.</span></span> <span data-ttu-id="9e569-415">.NET Core 2,1 veya .NET Standard 2,0 ve önceki sürümlerini hedeflerken, bir metapackage içindeki paketlere örtük [Packagereference](#packagereference) öğelerini denetler.</span><span class="sxs-lookup"><span data-stu-id="9e569-415">When targeting .NET Core 2.1 or .NET Standard 2.0 and earlier versions, it controls implicit [PackageReference](#packagereference) items to packages in a metapackage.</span></span> <span data-ttu-id="9e569-416">(Metapackage, yalnızca diğer paketlerdeki bağımlılıklardan oluşan çerçeve tabanlı bir pakettir.) Bu özellik ayrıca `System` , .NET Framework hedefleme gibi örtülü başvuruları da denetler `System.Core` .</span><span class="sxs-lookup"><span data-stu-id="9e569-416">(A metapackage is a framework-based package that consist only of dependencies on other packages.) This property also controls implicit references such as `System` and `System.Core` when targeting .NET Framework.</span></span>

<span data-ttu-id="9e569-417">`true`Örtük `FrameworkReference` veya [packagereference](#packagereference) öğelerini devre dışı bırakmak için bu özelliği olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9e569-417">Set this property to `true` to disable implicit `FrameworkReference` or [PackageReference](#packagereference) items.</span></span> <span data-ttu-id="9e569-418">Bu özelliği olarak ayarlarsanız `true` , yalnızca ihtiyacınız olan çerçevelere veya paketlere açık başvurular ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e569-418">If you set this property to `true`, you can add explicit references to just the frameworks or packages you need.</span></span>

```xml
<PropertyGroup>
  <DisableImplicitFrameworkReferences>true</DisableImplicitFrameworkReferences>
</PropertyGroup>
```

### <a name="restore-related-properties"></a><span data-ttu-id="9e569-419">Geri yükleme ile ilgili özellikler</span><span class="sxs-lookup"><span data-stu-id="9e569-419">Restore-related properties</span></span>

<span data-ttu-id="9e569-420">Başvurulan bir paketin geri yüklenmesi, tüm doğrudan bağımlılıklarını ve bu bağımlılıkların tüm bağımlılıklarını yükler.</span><span class="sxs-lookup"><span data-stu-id="9e569-420">Restoring a referenced package installs all of its direct dependencies and all the dependencies of those dependencies.</span></span> <span data-ttu-id="9e569-421">Ve gibi özellikler belirterek paket geri yüklemesini özelleştirebilirsiniz `RestorePackagesPath` `RestoreIgnoreFailedSources` .</span><span class="sxs-lookup"><span data-stu-id="9e569-421">You can customize package restoration by specifying properties such as `RestorePackagesPath` and `RestoreIgnoreFailedSources`.</span></span> <span data-ttu-id="9e569-422">Bu ve diğer özellikler hakkında daha fazla bilgi için bkz. [hedefi geri yükleme](/nuget/reference/msbuild-targets#restore-target).</span><span class="sxs-lookup"><span data-stu-id="9e569-422">For more information about these and other properties, see [restore target](/nuget/reference/msbuild-targets#restore-target).</span></span>

```xml
<PropertyGroup>
  <RestoreIgnoreFailedSource>true</RestoreIgnoreFailedSource>
</PropertyGroup>
```

## <a name="run-related-properties"></a><span data-ttu-id="9e569-423">Çalışma ile ilgili özellikler</span><span class="sxs-lookup"><span data-stu-id="9e569-423">Run-related properties</span></span>

<span data-ttu-id="9e569-424">Aşağıdaki özellikler, komutuyla bir uygulama başlatmak için kullanılır [`dotnet run`](../tools/dotnet-run.md) :</span><span class="sxs-lookup"><span data-stu-id="9e569-424">The following properties are used for launching an app with the [`dotnet run`](../tools/dotnet-run.md) command:</span></span>

- [<span data-ttu-id="9e569-425">RunArguments</span><span class="sxs-lookup"><span data-stu-id="9e569-425">RunArguments</span></span>](#runarguments)
- [<span data-ttu-id="9e569-426">RunWorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="9e569-426">RunWorkingDirectory</span></span>](#runworkingdirectory)

### <a name="runarguments"></a><span data-ttu-id="9e569-427">RunArguments</span><span class="sxs-lookup"><span data-stu-id="9e569-427">RunArguments</span></span>

<span data-ttu-id="9e569-428">`RunArguments`Özelliği, çalıştırıldığında uygulamaya geçirilen bağımsız değişkenleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9e569-428">The `RunArguments` property defines the arguments that are passed to the app when it is run.</span></span>

```xml
<PropertyGroup>
  <RunArguments>-mode dryrun</RunArguments>
</PropertyGroup>
```

> [!TIP]
> <span data-ttu-id="9e569-429">[ `--` Seçeneğini `dotnet run` ](../tools/dotnet-run.md#options)kullanarak uygulamaya geçirilecek ek bağımsız değişkenler belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e569-429">You can specify additional arguments to be passed to the app by using the [`--` option for `dotnet run`](../tools/dotnet-run.md#options).</span></span>

### <a name="runworkingdirectory"></a><span data-ttu-id="9e569-430">RunWorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="9e569-430">RunWorkingDirectory</span></span>

<span data-ttu-id="9e569-431">`RunWorkingDirectory`Özelliği, uygulamasında başlatılacak uygulama işleminin çalışma dizinini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9e569-431">The `RunWorkingDirectory` property defines the working directory for the application process to be started in.</span></span> <span data-ttu-id="9e569-432">Bu, mutlak bir yol veya proje diziniyle ilişkili bir yol olabilir.</span><span class="sxs-lookup"><span data-stu-id="9e569-432">It can be an absolute path or a path that's relative to the project directory.</span></span> <span data-ttu-id="9e569-433">Bir dizin belirtmezseniz, `OutDir` çalışma dizini olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9e569-433">If you don't specify a directory, `OutDir` is used as the working directory.</span></span>

```xml
<PropertyGroup>
  <RunWorkingDirectory>c:\temp</RunWorkingDirectory>
</PropertyGroup>
```

## <a name="hosting-related-properties"></a><span data-ttu-id="9e569-434">Barındırma ile ilgili özellikler</span><span class="sxs-lookup"><span data-stu-id="9e569-434">Hosting-related properties</span></span>

<span data-ttu-id="9e569-435">Aşağıdaki MSBuild özellikleri bu bölümde belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="9e569-435">The following MSBuild properties are documented in this section:</span></span>

- [<span data-ttu-id="9e569-436">EnableComHosting</span><span class="sxs-lookup"><span data-stu-id="9e569-436">EnableComHosting</span></span>](#enablecomhosting)
- [<span data-ttu-id="9e569-437">EnableDynamicLoading</span><span class="sxs-lookup"><span data-stu-id="9e569-437">EnableDynamicLoading</span></span>](#enabledynamicloading)

### <a name="enablecomhosting"></a><span data-ttu-id="9e569-438">EnableComHosting</span><span class="sxs-lookup"><span data-stu-id="9e569-438">EnableComHosting</span></span>

<span data-ttu-id="9e569-439">Özelliği, bir `EnableComHosting` derlemenin BIR com sunucusu sağladığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9e569-439">The `EnableComHosting` property indicates that an assembly provides a COM server.</span></span> <span data-ttu-id="9e569-440">İçin ayarı `EnableComHosting` , `true` [EnableDynamicLoading](#enabledynamicloading) olduğunu da belirtir `true` .</span><span class="sxs-lookup"><span data-stu-id="9e569-440">Setting the `EnableComHosting` to `true` also implies that [EnableDynamicLoading](#enabledynamicloading) is `true`.</span></span>

```xml
<PropertyGroup>
  <EnableComHosting>True</EnableComHosting>
</PropertyGroup>
```

<span data-ttu-id="9e569-441">Daha fazla bilgi için bkz. [.net BILEŞENLERINI com 'Da kullanıma](../native-interop/expose-components-to-com.md)sunma.</span><span class="sxs-lookup"><span data-stu-id="9e569-441">For more information, see [Expose .NET components to COM](../native-interop/expose-components-to-com.md).</span></span>

### <a name="enabledynamicloading"></a><span data-ttu-id="9e569-442">EnableDynamicLoading</span><span class="sxs-lookup"><span data-stu-id="9e569-442">EnableDynamicLoading</span></span>

<span data-ttu-id="9e569-443">`EnableDynamicLoading`Özelliği, bir derlemenin dinamik olarak yüklenen bir bileşen olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="9e569-443">The `EnableDynamicLoading` property indicates that an assembly is a dynamically loaded component.</span></span> <span data-ttu-id="9e569-444">Bileşen bir [com kitaplığı](/windows/win32/com/the-component-object-model) veya [Yerel BIR konaktan kullanılabilecek](../tutorials/netcore-hosting.md)com olmayan bir kitaplık olabilir.</span><span class="sxs-lookup"><span data-stu-id="9e569-444">The component could be a [COM library](/windows/win32/com/the-component-object-model) or a non-COM library that can be [used from a native host](../tutorials/netcore-hosting.md).</span></span> <span data-ttu-id="9e569-445">Bu özelliğin olarak ayarlanması `true` aşağıdaki etkilere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="9e569-445">Setting this property to `true` has the following effects:</span></span>

- <span data-ttu-id="9e569-446">Dosyadaki bir *.runtimeconfig.js* oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9e569-446">A *.runtimeconfig.json* file is generated.</span></span>
- <span data-ttu-id="9e569-447">[Ileri alma](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward) , olarak ayarlanır `LatestMinor` .</span><span class="sxs-lookup"><span data-stu-id="9e569-447">[Roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward) is set to `LatestMinor`.</span></span>
- <span data-ttu-id="9e569-448">NuGet başvuruları yerel olarak kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="9e569-448">NuGet references are copied locally.</span></span>

```xml
<PropertyGroup>
  <EnableDynamicLoading>true</EnableDynamicLoading>
</PropertyGroup>
```

## <a name="items"></a><span data-ttu-id="9e569-449">Öğeler</span><span class="sxs-lookup"><span data-stu-id="9e569-449">Items</span></span>

<span data-ttu-id="9e569-450">[MSBuild öğeleri](/visualstudio/msbuild/msbuild-items) , derleme sistemine giriş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9e569-450">[MSBuild items](/visualstudio/msbuild/msbuild-items) are inputs into the build system.</span></span> <span data-ttu-id="9e569-451">Öğeler, öğe adı olan türlerine göre belirtilir.</span><span class="sxs-lookup"><span data-stu-id="9e569-451">Items are specified according to their type, which is the element name.</span></span> <span data-ttu-id="9e569-452">Örneğin, `Compile` ve `Reference` iki [ortak öğe türüdür](/visualstudio/msbuild/common-msbuild-project-items).</span><span class="sxs-lookup"><span data-stu-id="9e569-452">For example, `Compile` and `Reference` are two [common item types](/visualstudio/msbuild/common-msbuild-project-items).</span></span> <span data-ttu-id="9e569-453">Aşağıdaki ek öğe türleri .NET SDK tarafından kullanılabilir hale getirilir:</span><span class="sxs-lookup"><span data-stu-id="9e569-453">The following additional item types are made available by the .NET SDK:</span></span>

- [<span data-ttu-id="9e569-454">PackageReference</span><span class="sxs-lookup"><span data-stu-id="9e569-454">PackageReference</span></span>](#packagereference)
- [<span data-ttu-id="9e569-455">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="9e569-455">TrimmerRootAssembly</span></span>](#trimmerrootassembly)

<span data-ttu-id="9e569-456">Standart [öğe özniteliklerinden](/visualstudio/msbuild/item-element-msbuild#attributes-and-elements)herhangi birini, örneğin, `Include` ve `Update` , bu öğelerde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e569-456">You can use any of the standard [item attributes](/visualstudio/msbuild/item-element-msbuild#attributes-and-elements), for example, `Include` and `Update`, on these items.</span></span> <span data-ttu-id="9e569-457">`Include`Yeni bir öğe eklemek ve `Update` var olan bir öğeyi değiştirmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="9e569-457">Use `Include` to add a new item, and use `Update` to modify an existing item.</span></span> <span data-ttu-id="9e569-458">Örneğin, `Update` genellikle .NET SDK 'sı tarafından dolaylı olarak eklenmiş bir öğeyi değiştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9e569-458">For example, `Update` is often used to modify an item that has implicitly been added by the .NET SDK.</span></span>

### <a name="packagereference"></a><span data-ttu-id="9e569-459">PackageReference</span><span class="sxs-lookup"><span data-stu-id="9e569-459">PackageReference</span></span>

<span data-ttu-id="9e569-460">`PackageReference`Öğe, bir NuGet paketine bir başvuru tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9e569-460">The `PackageReference` item defines a reference to a NuGet package.</span></span>

<span data-ttu-id="9e569-461">`Include`Öznitelik, paket kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9e569-461">The `Include` attribute specifies the package ID.</span></span> <span data-ttu-id="9e569-462">`Version`Öznitelik, sürümü veya sürüm aralığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9e569-462">The `Version` attribute specifies the version or version range.</span></span> <span data-ttu-id="9e569-463">En düşük sürüm, en yüksek sürüm, Aralık veya tam eşleşme belirtme hakkında bilgi için bkz. [Sürüm aralıkları](/nuget/concepts/package-versioning#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="9e569-463">For information about how to specify a minimum version, maximum version, range, or exact match, see [Version ranges](/nuget/concepts/package-versioning#version-ranges).</span></span>

<span data-ttu-id="9e569-464">Aşağıdaki örnekteki proje dosyası kod parçacığı [System. Runtime](https://www.nuget.org/packages/System.Runtime/) paketine başvurur.</span><span class="sxs-lookup"><span data-stu-id="9e569-464">The project file snippet in the following example references the [System.Runtime](https://www.nuget.org/packages/System.Runtime/) package.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="System.Runtime" Version="4.3.0" />
</ItemGroup>
```

<span data-ttu-id="9e569-465">[Bağımlılık varlıklarını](/nuget/consume-packages/package-references-in-project-files#controlling-dependency-assets) , gibi meta verileri kullanarak da denetleyebilirsiniz `PrivateAssets` .</span><span class="sxs-lookup"><span data-stu-id="9e569-465">You can also [control dependency assets](/nuget/consume-packages/package-references-in-project-files#controlling-dependency-assets) using metadata such as `PrivateAssets`.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Contoso.Utility.UsefulStuff" Version="3.6.0">
    <PrivateAssets>all</PrivateAssets>
  </PackageReference>
</ItemGroup>
```

<span data-ttu-id="9e569-466">Daha fazla bilgi için bkz. [Proje dosyalarındaki paket başvuruları](/nuget/consume-packages/package-references-in-project-files).</span><span class="sxs-lookup"><span data-stu-id="9e569-466">For more information, see [Package references in project files](/nuget/consume-packages/package-references-in-project-files).</span></span>

### <a name="trimmerrootassembly"></a><span data-ttu-id="9e569-467">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="9e569-467">TrimmerRootAssembly</span></span>

<span data-ttu-id="9e569-468">`TrimmerRootAssembly`Öğe, bir derlemeyi [*kırpmanıza*](../deploying/trim-self-contained.md)dışlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e569-468">The `TrimmerRootAssembly` item lets you exclude an assembly from [*trimming*](../deploying/trim-self-contained.md).</span></span> <span data-ttu-id="9e569-469">Kırpma, çalışma zamanının kullanılmayan parçalarını paketlenmiş bir uygulamadan kaldırma işlemidir.</span><span class="sxs-lookup"><span data-stu-id="9e569-469">Trimming is the process of removing unused parts of the runtime from a packaged application.</span></span> <span data-ttu-id="9e569-470">Bazı durumlarda, kırpma gerekli başvuruları yanlış kaldırabilir.</span><span class="sxs-lookup"><span data-stu-id="9e569-470">In some cases, trimming might incorrectly remove required references.</span></span>

<span data-ttu-id="9e569-471">Aşağıdaki XML, `System.Security` derlemeyi kırpmaya dışlar.</span><span class="sxs-lookup"><span data-stu-id="9e569-471">The following XML excludes the `System.Security` assembly from trimming.</span></span>

```xml
<ItemGroup>
  <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

## <a name="item-metadata"></a><span data-ttu-id="9e569-472">Öğe meta verileri</span><span class="sxs-lookup"><span data-stu-id="9e569-472">Item metadata</span></span>

<span data-ttu-id="9e569-473">Standart [MSBuild öğe özniteliklerine](/visualstudio/msbuild/item-element-msbuild#attributes-and-elements)ek olarak, aşağıdaki öğe meta veri ETIKETLERI .NET SDK tarafından kullanılabilir hale getirilir:</span><span class="sxs-lookup"><span data-stu-id="9e569-473">In addition to the standard [MSBuild item attributes](/visualstudio/msbuild/item-element-msbuild#attributes-and-elements), the following item metadata tags are made available by the .NET SDK:</span></span>

- [<span data-ttu-id="9e569-474">CopyToPublishDirectory</span><span class="sxs-lookup"><span data-stu-id="9e569-474">CopyToPublishDirectory</span></span>](#copytopublishdirectory)
- [<span data-ttu-id="9e569-475">Tabanlarını</span><span class="sxs-lookup"><span data-stu-id="9e569-475">LinkBase</span></span>](#linkbase)

### <a name="copytopublishdirectory"></a><span data-ttu-id="9e569-476">CopyToPublishDirectory</span><span class="sxs-lookup"><span data-stu-id="9e569-476">CopyToPublishDirectory</span></span>

<span data-ttu-id="9e569-477">`CopyToPublishDirectory`MSBuild öğesindeki meta veriler, öğe yayımlama dizinine kopyalandığında denetler.</span><span class="sxs-lookup"><span data-stu-id="9e569-477">The `CopyToPublishDirectory` metadata on an MSBuild item controls when the item is copied to the publish directory.</span></span> <span data-ttu-id="9e569-478">İzin verilen değerler `PreserveNewest` , yalnızca değiştirilirse öğeyi kopyalayan, `Always` her zaman öğeyi kopyalayan ve öğeyi `Never` hiçbir zaman kopyalamamış olan değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="9e569-478">Allowable values are `PreserveNewest`, which only copies the item if it has changed, `Always`, which always copies the item, and `Never`, which never copies the item.</span></span> <span data-ttu-id="9e569-479">Bir performans açısından, `PreserveNewest` artımlı bir derlemeyi sağladığından tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="9e569-479">From a performance standpoint, `PreserveNewest` is preferable because it enables an incremental build.</span></span>

```xml
<ItemGroup>
  <None Update="appsettings.Development.json" CopyToOutputDirectory="PreserveNewest" CopyToPublishDirectory="PreserveNewest" />
</ItemGroup>
```

### <a name="linkbase"></a><span data-ttu-id="9e569-480">Tabanlarını</span><span class="sxs-lookup"><span data-stu-id="9e569-480">LinkBase</span></span>

<span data-ttu-id="9e569-481">Proje dizini ve alt dizinleri dışında olan bir öğe için, Yayımla hedefi öğenin [bağlantı meta verilerini](/visualstudio/msbuild/common-msbuild-item-metadata) kullanarak öğenin nereye kopyalanacağını tespit edin.</span><span class="sxs-lookup"><span data-stu-id="9e569-481">For an item that's outside of the project directory and its subdirectories, the publish target uses the item's [Link metadata](/visualstudio/msbuild/common-msbuild-item-metadata) to determine where to copy the item to.</span></span> <span data-ttu-id="9e569-482">`Link` Ayrıca, proje ağacının dışındaki öğelerin Visual Studio 'nun Çözüm Gezgini penceresinde nasıl görüntüleneceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="9e569-482">`Link` also determines how items outside of the project tree are displayed in the Solution Explorer window of Visual Studio.</span></span>

<span data-ttu-id="9e569-483">`Link`Proje konisi dışında bir öğe için belirtilmemişse, varsayılan olarak öğesine ayarlanır `%(LinkBase)\%(RecursiveDir)%(Filename)%(Extension)` .</span><span class="sxs-lookup"><span data-stu-id="9e569-483">If `Link` is not specified for an item that's outside of the project cone, it defaults to `%(LinkBase)\%(RecursiveDir)%(Filename)%(Extension)`.</span></span> <span data-ttu-id="9e569-484">`LinkBase` Proje koni dışındaki öğeler için bir senerişilebilir taban klasörü belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e569-484">`LinkBase` lets you specify a sensible base folder for items outside of the project cone.</span></span> <span data-ttu-id="9e569-485">Taban klasörü altındaki klasör hiyerarşisi aracılığıyla korunur `RecursiveDir` .</span><span class="sxs-lookup"><span data-stu-id="9e569-485">The folder hierarchy under the base folder is preserved via `RecursiveDir`.</span></span> <span data-ttu-id="9e569-486">`LinkBase`Belirtilmemişse, `Link` yolundan çıkarılır.</span><span class="sxs-lookup"><span data-stu-id="9e569-486">If `LinkBase` is not specified, it's omitted from the `Link` path.</span></span>

```xml
<ItemGroup>
  <Content Include="..\Extras\**\*.cs" LinkBase="Shared"/>
</ItemGroup>
```

<span data-ttu-id="9e569-487">Aşağıdaki görüntüde, önceki öğe ile eklenen bir dosyanın `Include` Çözüm Gezgini ' de nasıl görüntüleyeceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9e569-487">The following image shows how a file that's included via the previous item `Include` glob displays in Solution Explorer.</span></span>

:::image type="content" source="media/solution-explorer-linkbase.png" alt-text="Çözüm Gezgini bağlantı tabanının meta verileri içeren öğe gösteriliyor.":::

## <a name="see-also"></a><span data-ttu-id="9e569-489">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9e569-489">See also</span></span>

- [<span data-ttu-id="9e569-490">MSBuild şema başvurusu</span><span class="sxs-lookup"><span data-stu-id="9e569-490">MSBuild schema reference</span></span>](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [<span data-ttu-id="9e569-491">Ortak MSBuild özellikleri</span><span class="sxs-lookup"><span data-stu-id="9e569-491">Common MSBuild properties</span></span>](/visualstudio/msbuild/common-msbuild-project-properties)
- [<span data-ttu-id="9e569-492">NuGet paketi için MSBuild özellikleri</span><span class="sxs-lookup"><span data-stu-id="9e569-492">MSBuild properties for NuGet pack</span></span>](/nuget/reference/msbuild-targets#pack-target)
- [<span data-ttu-id="9e569-493">NuGet geri yükleme için MSBuild özellikleri</span><span class="sxs-lookup"><span data-stu-id="9e569-493">MSBuild properties for NuGet restore</span></span>](/nuget/reference/msbuild-targets#restore-properties)
- [<span data-ttu-id="9e569-494">Bir derlemeyi özelleştirme</span><span class="sxs-lookup"><span data-stu-id="9e569-494">Customize a build</span></span>](/visualstudio/msbuild/customize-your-build)
