---
title: Microsoft. NET. SDK. Desktop için MSBuild özellikleri
description: WPF ve WinForms içeren, .NET masaüstü SDK 'Sı tarafından anlayan olan MSBuild özellikleri ve öğeleri için başvuru.
ms.date: 02/04/2021
ms.topic: reference
author: adegeo
ms.author: adegeo
ms.custom: updateeachrelease
no-loc:
- App.xaml
- Application.xaml
- ApplicationDefinition
- Page
- EmbeddedResource
- Compile
- None
ms.openlocfilehash: 6d1903558dd03776a72eb6ee56ddae09fb66615b
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100488368"
---
# <a name="msbuild-reference-for-net-desktop-sdk-projects"></a><span data-ttu-id="daaef-103">.NET masaüstü SDK projeleri için MSBuild başvurusu</span><span class="sxs-lookup"><span data-stu-id="daaef-103">MSBuild reference for .NET Desktop SDK projects</span></span>

<span data-ttu-id="daaef-104">Bu sayfa, .NET masaüstü SDK ile Windows Forms (WinForms) ve Windows Presentation Foundation (WPF) projelerini yapılandırmak için kullandığınız MSBuild özelliklerine ve öğelerine yönelik bir başvurudur.</span><span class="sxs-lookup"><span data-stu-id="daaef-104">This page is a reference for the MSBuild properties and items that you use to configure Windows Forms (WinForms) and Windows Presentation Foundation (WPF) projects with the .NET Desktop SDK.</span></span>

> [!NOTE]
> <span data-ttu-id="daaef-105">Bu makale, masaüstü uygulamalarıyla ilişkili olarak .NET SDK için MSBuild özelliklerinin bir alt kümesini belgeler.</span><span class="sxs-lookup"><span data-stu-id="daaef-105">This article documents a subset of the MSBuild properties for the .NET SDK as it relates to desktop apps.</span></span> <span data-ttu-id="daaef-106">Ortak .NET SDK 'ya özgü MSBuild özelliklerinin bir listesi için bkz. [.NET SDK projeleri Için MSBuild başvurusu](msbuild-props.md).</span><span class="sxs-lookup"><span data-stu-id="daaef-106">For a list of common .NET SDK-specific MSBuild properties, see [MSBuild reference for .NET SDK projects](msbuild-props.md).</span></span> <span data-ttu-id="daaef-107">Ortak MSBuild özelliklerinin bir listesi için bkz. [Ortak MSBuild özellikleri](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="daaef-107">For a list of common MSBuild properties, see [Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="enable-net-desktop-sdk"></a><span data-ttu-id="daaef-108">.NET masaüstü SDK 'sını etkinleştir</span><span class="sxs-lookup"><span data-stu-id="daaef-108">Enable .NET Desktop SDK</span></span>

<span data-ttu-id="daaef-109">WinForms veya WPF kullanmak için, proje dosyanızı yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="daaef-109">To use WinForms or WPF, configure your project file.</span></span>

### <a name="net-50"></a><span data-ttu-id="daaef-110">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="daaef-110">.NET 5.0</span></span>

<span data-ttu-id="daaef-111">WinForms veya WPF projenizin proje dosyasında aşağıdaki ayarları belirtin:</span><span class="sxs-lookup"><span data-stu-id="daaef-111">Specify the following settings in the project file of your WinForms or WPF project:</span></span>

- <span data-ttu-id="daaef-112">.NET SDK 'sını hedefleyin `Microsoft.NET.Sdk` .</span><span class="sxs-lookup"><span data-stu-id="daaef-112">Target the .NET SDK `Microsoft.NET.Sdk`.</span></span> <span data-ttu-id="daaef-113">Daha fazla bilgi için bkz. [proje dosyaları](overview.md#project-files).</span><span class="sxs-lookup"><span data-stu-id="daaef-113">For more information, see [Project files](overview.md#project-files).</span></span>
- <span data-ttu-id="daaef-114">[`TargetFramework`](msbuild-props.md#targetframework)Olarak ayarlayın `net5.0-windows` .</span><span class="sxs-lookup"><span data-stu-id="daaef-114">Set [`TargetFramework`](msbuild-props.md#targetframework) to `net5.0-windows`.</span></span>
- <span data-ttu-id="daaef-115">UI çerçevesi özelliği ekleyin (veya gerekirse her ikisi de):</span><span class="sxs-lookup"><span data-stu-id="daaef-115">Add a UI framework property (or both, if necessary):</span></span>
  - <span data-ttu-id="daaef-116">[`UseWPF`](#usewpf)WPF 'yi `true` içeri ve daha sonra kullanmak için olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="daaef-116">Set [`UseWPF`](#usewpf) to `true` to import and use WPF.</span></span>
  - <span data-ttu-id="daaef-117">[`UseWindowsForms`](#usewindowsforms) `true` WinForms içeri aktarıp kullanmak için olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="daaef-117">Set [`UseWindowsForms`](#usewindowsforms) to `true` to import and use WinForms.</span></span>
- <span data-ttu-id="daaef-118">Seçim `OutputType` Olarak ayarlayın `WinExe` .</span><span class="sxs-lookup"><span data-stu-id="daaef-118">(Optional) Set `OutputType` to `WinExe`.</span></span> <span data-ttu-id="daaef-119">Bu, bir kitaplık yerine bir uygulama oluşturur.</span><span class="sxs-lookup"><span data-stu-id="daaef-119">This produces an app as opposed to a library.</span></span> <span data-ttu-id="daaef-120">Bir kitaplık oluşturmak için bu özelliği atlayın.</span><span class="sxs-lookup"><span data-stu-id="daaef-120">To produce a library, omit this property.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>net5.0-windows</TargetFramework>

    <UseWPF>true</UseWPF>
    <!-- and/or -->
    <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>

</Project>
```

### <a name="net-core-31"></a><span data-ttu-id="daaef-121">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="daaef-121">.NET Core 3.1</span></span>

<span data-ttu-id="daaef-122">WinForms veya WPF projenizin proje dosyasında aşağıdaki ayarları belirtin:</span><span class="sxs-lookup"><span data-stu-id="daaef-122">Specify the following settings in the project file of your WinForms or WPF project:</span></span>

- <span data-ttu-id="daaef-123">.NET SDK 'sını hedefleyin `Microsoft.NET.Sdk.WindowsDesktop` .</span><span class="sxs-lookup"><span data-stu-id="daaef-123">Target the .NET SDK `Microsoft.NET.Sdk.WindowsDesktop`.</span></span> <span data-ttu-id="daaef-124">Daha fazla bilgi için bkz. [proje dosyaları](overview.md#project-files).</span><span class="sxs-lookup"><span data-stu-id="daaef-124">For more information, see [Project files](overview.md#project-files).</span></span>
- <span data-ttu-id="daaef-125">[`TargetFramework`](msbuild-props.md#targetframework)Olarak ayarlayın `netcoreapp3.1` .</span><span class="sxs-lookup"><span data-stu-id="daaef-125">Set [`TargetFramework`](msbuild-props.md#targetframework) to `netcoreapp3.1`.</span></span>
- <span data-ttu-id="daaef-126">UI çerçevesi özelliği ekleyin (veya gerekirse her ikisi de):</span><span class="sxs-lookup"><span data-stu-id="daaef-126">Add a UI framework property (or both, if necessary):</span></span>
  - <span data-ttu-id="daaef-127">[`UseWPF`](#usewpf)WPF 'yi `true` içeri ve daha sonra kullanmak için olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="daaef-127">Set [`UseWPF`](#usewpf) to `true` to import and use WPF.</span></span>
  - <span data-ttu-id="daaef-128">[`UseWindowsForms`](#usewindowsforms) `true` WinForms içeri aktarıp kullanmak için olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="daaef-128">Set [`UseWindowsForms`](#usewindowsforms) to `true` to import and use WinForms.</span></span>
- <span data-ttu-id="daaef-129">Seçim `OutputType` Olarak ayarlayın `WinExe` .</span><span class="sxs-lookup"><span data-stu-id="daaef-129">(Optional) Set `OutputType` to `WinExe`.</span></span> <span data-ttu-id="daaef-130">Bu, bir kitaplık yerine bir uygulama oluşturur.</span><span class="sxs-lookup"><span data-stu-id="daaef-130">This produces an app as opposed to a library.</span></span> <span data-ttu-id="daaef-131">Bir kitaplık oluşturmak için bu özelliği atlayın.</span><span class="sxs-lookup"><span data-stu-id="daaef-131">To produce a library, omit this property.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>

    <UseWPF>true</UseWPF>
    <!-- and/or -->
    <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>

</Project>
```

## <a name="wpf-default-includes-and-excludes"></a><span data-ttu-id="daaef-132">WPF varsayılan içerir ve dışlar</span><span class="sxs-lookup"><span data-stu-id="daaef-132">WPF default includes and excludes</span></span>

<span data-ttu-id="daaef-133">SDK projeleri, dosyaları projeden örtük olarak dahil etmek veya hariç tutmak için bir kurallar kümesi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="daaef-133">SDK projects define a set of rules to implicitly include or exclude files from the project.</span></span> <span data-ttu-id="daaef-134">Bu kurallar, dosyanın derleme eylemini de otomatik olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="daaef-134">These rules also automatically set the file's build action.</span></span> <span data-ttu-id="daaef-135">Bu, varsayılan içerme veya dışlama kuralları olmayan, daha eski SDK olmayan .NET Framework projelerinin aksine.</span><span class="sxs-lookup"><span data-stu-id="daaef-135">This is unlike the older non-SDK .NET Framework projects, which have no default include or exclude rules.</span></span> <span data-ttu-id="daaef-136">.NET Framework projeler, projeye hangi dosyaların ekleneceğini açıkça bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="daaef-136">.NET Framework projects require you to explicitly declare which files to include in the project.</span></span>

<span data-ttu-id="daaef-137">.NET proje dosyaları, dosyaları otomatik olarak işlemeye yönelik [Standart bir kurallar kümesi](overview.md#default-includes-and-excludes) içerir.</span><span class="sxs-lookup"><span data-stu-id="daaef-137">.NET project files include a [standard set of rules](overview.md#default-includes-and-excludes) for automatically processing files.</span></span> <span data-ttu-id="daaef-138">WPF projeleri ek kurallar ekler.</span><span class="sxs-lookup"><span data-stu-id="daaef-138">WPF projects add additional rules.</span></span>

<span data-ttu-id="daaef-139">Aşağıdaki tabloda, [](https://en.wikipedia.org/wiki/Glob_(programming)) [`UseWPF`](#usewpf) Proje özelliği olarak ayarlandığında .net masaüstü SDK 'sına dahil edilen ve çıkarılan öğelerin ve genelleştirmeler gösterilmektedir `true` :</span><span class="sxs-lookup"><span data-stu-id="daaef-139">The following table shows which elements and [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are included and excluded in the .NET Desktop SDK when the [`UseWPF`](#usewpf) project property is set to `true`:</span></span>

| <span data-ttu-id="daaef-140">Öğe</span><span class="sxs-lookup"><span data-stu-id="daaef-140">Element</span></span>               | <span data-ttu-id="daaef-141">Glob 'yi dahil et</span><span class="sxs-lookup"><span data-stu-id="daaef-141">Include glob</span></span>                 | <span data-ttu-id="daaef-142">Glob 'yi hariç tut</span><span class="sxs-lookup"><span data-stu-id="daaef-142">Exclude glob</span></span>                                                                                           | <span data-ttu-id="daaef-143">Glob 'yi kaldır</span><span class="sxs-lookup"><span data-stu-id="daaef-143">Remove glob</span></span>  |
|-----------------------|------------------------------|--------------------------------------------------------------------|--------------|
| ApplicationDefinition | <span data-ttu-id="daaef-144">App.xaml veya Application.xaml</span><span class="sxs-lookup"><span data-stu-id="daaef-144">App.xaml or Application.xaml</span></span> | <span data-ttu-id="daaef-145">Yok</span><span class="sxs-lookup"><span data-stu-id="daaef-145">N/A</span></span>                                                                | <span data-ttu-id="daaef-146">Yok</span><span class="sxs-lookup"><span data-stu-id="daaef-146">N/A</span></span>          |
| Page                  | <span data-ttu-id="daaef-147">\*\*/\*. xaml</span><span class="sxs-lookup"><span data-stu-id="daaef-147">\*\*/\*.xaml</span></span>                 | <span data-ttu-id="daaef-148">\*\*/\*kullanıcısını \*\*/\*.\* PROJ \*\*/\*. sln \*\*/\*. vssscc</span><span class="sxs-lookup"><span data-stu-id="daaef-148">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span><br><span data-ttu-id="daaef-149">Tarafından tanımlanan XAML *ApplicationDefinition*</span><span class="sxs-lookup"><span data-stu-id="daaef-149">Any XAML defined by *ApplicationDefinition*</span></span> | <span data-ttu-id="daaef-150">Yok</span><span class="sxs-lookup"><span data-stu-id="daaef-150">N/A</span></span>          |
| None                  | <span data-ttu-id="daaef-151">Yok</span><span class="sxs-lookup"><span data-stu-id="daaef-151">N/A</span></span>                          | <span data-ttu-id="daaef-152">Yok</span><span class="sxs-lookup"><span data-stu-id="daaef-152">N/A</span></span>                                                                | <span data-ttu-id="daaef-153">\*\*/\*. xaml</span><span class="sxs-lookup"><span data-stu-id="daaef-153">\*\*/\*.xaml</span></span> |

<span data-ttu-id="daaef-154">Tüm proje türleri için varsayılan içerme ve dışlama ayarları aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="daaef-154">Here are the default include and exclude settings for all project types.</span></span> <span data-ttu-id="daaef-155">Daha fazla bilgi için bkz. [varsayılan içerme ve dışladığı](overview.md#default-includes-and-excludes).</span><span class="sxs-lookup"><span data-stu-id="daaef-155">For more information, see [Default includes and excludes](overview.md#default-includes-and-excludes).</span></span>

| <span data-ttu-id="daaef-156">Öğe</span><span class="sxs-lookup"><span data-stu-id="daaef-156">Element</span></span>           | <span data-ttu-id="daaef-157">Glob 'yi dahil et</span><span class="sxs-lookup"><span data-stu-id="daaef-157">Include glob</span></span>                              | <span data-ttu-id="daaef-158">Glob 'yi hariç tut</span><span class="sxs-lookup"><span data-stu-id="daaef-158">Exclude glob</span></span>                                                  | <span data-ttu-id="daaef-159">Glob 'yi kaldır</span><span class="sxs-lookup"><span data-stu-id="daaef-159">Remove glob</span></span>              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| Compile           | <span data-ttu-id="daaef-160">\*\*/\*.cs \*\*/\*. vb (veya diğer dil uzantıları)</span><span class="sxs-lookup"><span data-stu-id="daaef-160">\*\*/\*.cs; \*\*/\*.vb (or other language extensions)</span></span> | <span data-ttu-id="daaef-161">\*\*/\*kullanıcısını  \*\*/\*.\* PROJ  \*\*/\*. sln  \*\*/\*. vssscc</span><span class="sxs-lookup"><span data-stu-id="daaef-161">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="daaef-162">Yok</span><span class="sxs-lookup"><span data-stu-id="daaef-162">N/A</span></span>          |
| EmbeddedResource  | <span data-ttu-id="daaef-163">\*\*/\*. resx</span><span class="sxs-lookup"><span data-stu-id="daaef-163">\*\*/\*.resx</span></span>                              | <span data-ttu-id="daaef-164">\*\*/\*kullanıcısını \*\*/\*.\* PROJ \*\*/\*. sln \*\*/\*. vssscc</span><span class="sxs-lookup"><span data-stu-id="daaef-164">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="daaef-165">Yok</span><span class="sxs-lookup"><span data-stu-id="daaef-165">N/A</span></span>                      |
| None              | \*\*/\*                                   | <span data-ttu-id="daaef-166">\*\*/\*kullanıcısını \*\*/\*.\* PROJ \*\*/\*. sln \*\*/\*. vssscc</span><span class="sxs-lookup"><span data-stu-id="daaef-166">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="daaef-167">\*\*/\*.cs \*\*/\*. resx</span><span class="sxs-lookup"><span data-stu-id="daaef-167">\*\*/\*.cs; \*\*/\*.resx</span></span> |

### <a name="errors-related-to-duplicate-items"></a><span data-ttu-id="daaef-168">"Yinelenen" öğelerle ilgili hatalar</span><span class="sxs-lookup"><span data-stu-id="daaef-168">Errors related to "duplicate" items</span></span>

<span data-ttu-id="daaef-169">Projenize açıkça dosya eklediyseniz ya da XAML genelleştirmeler otomatik olarak dosya eklemek istiyorsanız, aşağıdaki hatalardan birini alabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="daaef-169">If you explicitly added files to your project, or have XAML globs to automatically include files in your project, you might get one of the following errors:</span></span>

* <span data-ttu-id="daaef-170">Yinelenen ' ApplicationDefinition ' öğeleri eklendi.</span><span class="sxs-lookup"><span data-stu-id="daaef-170">Duplicate 'ApplicationDefinition' items were included.</span></span>
* <span data-ttu-id="daaef-171">Yinelenen ' Page ' öğeleri eklendi.</span><span class="sxs-lookup"><span data-stu-id="daaef-171">Duplicate 'Page' items were included.</span></span>

<span data-ttu-id="daaef-172">Bu hatalar, ayarlarınızdaki örtük *ekleme* genelleştirmeler çelişen bir sonucudur.</span><span class="sxs-lookup"><span data-stu-id="daaef-172">These errors are a result of the implicit *Include* globs conflicting with your settings.</span></span> <span data-ttu-id="daaef-173">Bu sorunu geçici olarak çözmek için ya da [`EnableDefaultApplicationDefinition`](#enabledefaultapplicationdefinition) [`EnableDefaultPageItems`](#enabledefaultpageitems) olarak ayarlayın `false` .</span><span class="sxs-lookup"><span data-stu-id="daaef-173">To work around this problem, set either [`EnableDefaultApplicationDefinition`](#enabledefaultapplicationdefinition) or [`EnableDefaultPageItems`](#enabledefaultpageitems) to `false`.</span></span> <span data-ttu-id="daaef-174">Bu değerleri `false` , projenizde varsayılan genelleştirmeler açıkça tanımlamanız gereken önceki SDK 'ların davranışına geri dönmek veya projeye dahil edilecek dosyaları açıkça tanımlamanız için ayarlamak.</span><span class="sxs-lookup"><span data-stu-id="daaef-174">Setting these values to `false` reverts to the behavior of previous SDKs where you had to explicitly define the default globs in your project, or explicitly define the files to include in the project.</span></span>

<span data-ttu-id="daaef-175">[ `EnableDefaultItems` Özelliğini](msbuild-props.md#enabledefaultitems) olarak ayarlayarak tüm örtük eklemeleri tamamen devre dışı bırakabilirsiniz `false` .</span><span class="sxs-lookup"><span data-stu-id="daaef-175">You can completely disable all implicit includes by setting the [`EnableDefaultItems` property](msbuild-props.md#enabledefaultitems) to `false`.</span></span>

## <a name="wpf-settings"></a><span data-ttu-id="daaef-176">WPF ayarları</span><span class="sxs-lookup"><span data-stu-id="daaef-176">WPF settings</span></span>

- [<span data-ttu-id="daaef-177">UseWPF</span><span class="sxs-lookup"><span data-stu-id="daaef-177">UseWPF</span></span>](#usewpf)
- [<span data-ttu-id="daaef-178">EnableDefaultApplicationDefinition</span><span class="sxs-lookup"><span data-stu-id="daaef-178">EnableDefaultApplicationDefinition</span></span>](#enabledefaultapplicationdefinition)
- [<span data-ttu-id="daaef-179">EnableDefault Page öğeleri</span><span class="sxs-lookup"><span data-stu-id="daaef-179">EnableDefaultPageItems</span></span>](#enabledefaultpageitems)

<span data-ttu-id="daaef-180">WPF 'e özgü olmayan proje ayarları hakkında daha fazla bilgi için bkz. [.NET SDK projeleri Için MSBuild başvurusu](msbuild-props.md).</span><span class="sxs-lookup"><span data-stu-id="daaef-180">For information about non-WPF-specific project settings, see [MSBuild reference for .NET SDK projects](msbuild-props.md).</span></span>

### <a name="usewpf"></a><span data-ttu-id="daaef-181">UseWPF</span><span class="sxs-lookup"><span data-stu-id="daaef-181">UseWPF</span></span>

<span data-ttu-id="daaef-182">`UseWPF`ÖZELLIĞI WPF kitaplıklarına başvuruların eklenip eklenmeyeceğini denetler.</span><span class="sxs-lookup"><span data-stu-id="daaef-182">The `UseWPF` property controls whether or not to include references to WPF libraries.</span></span> <span data-ttu-id="daaef-183">Bu Ayrıca, bir WPF projesini ve ilgili dosyaları doğru şekilde işlemek için MSBuild ardışık düzenini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="daaef-183">This also alters the MSBuild pipeline to correctly process a WPF project and related files.</span></span> <span data-ttu-id="daaef-184">`false` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="daaef-184">The default value is `false`.</span></span> <span data-ttu-id="daaef-185">`UseWPF` `true` WPF desteğini etkinleştirmek için özelliğini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="daaef-185">Set the `UseWPF` property to `true` to enable WPF support.</span></span> <span data-ttu-id="daaef-186">Yalnızca bu özellik etkinleştirildiğinde Windows platformunu hedefleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="daaef-186">You can only target the Windows platform when this property is enabled.</span></span>

```xml
<PropertyGroup>
  <UseWPF>true</UseWPF>
</PropertyGroup>
```

<span data-ttu-id="daaef-187">Bu özellik olarak ayarlandığında `true` , .NET 5.0 + projeleri, [.net masaüstü SDK 'sını](#enable-net-desktop-sdk)otomatik olarak içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="daaef-187">When this property is set to `true`, .NET 5.0+ projects will automatically import the [.NET Desktop SDK](#enable-net-desktop-sdk).</span></span>

<span data-ttu-id="daaef-188">.NET Core 3,1 projelerinin, bu özelliği kullanmak için [.net masaüstü SDK 'sını](#enable-net-desktop-sdk) açık bir şekilde hedeflemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="daaef-188">.NET Core 3.1 projects need to explicitly target the [.NET Desktop SDK](#enable-net-desktop-sdk) to use this property.</span></span>

### <a name="enabledefaultapplicationdefinition"></a><span data-ttu-id="daaef-189">EnableDefaultApplicationDefinition</span><span class="sxs-lookup"><span data-stu-id="daaef-189">EnableDefaultApplicationDefinition</span></span>

<span data-ttu-id="daaef-190">`EnableDefaultApplicationDefinition`Özelliği, `ApplicationDefinition` öğelerin projeye örtük olarak dahil edilip edilmediğini denetler.</span><span class="sxs-lookup"><span data-stu-id="daaef-190">The `EnableDefaultApplicationDefinition` property controls whether `ApplicationDefinition` items are implicitly included in the project.</span></span> <span data-ttu-id="daaef-191">`true` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="daaef-191">The default value is `true`.</span></span> <span data-ttu-id="daaef-192">`EnableDefaultApplicationDefinition` `false` Örtük dosya eklemeyi devre dışı bırakmak için özelliğini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="daaef-192">Set the `EnableDefaultApplicationDefinition` property to `false` to disable the implicit file inclusion.</span></span>

```xml
<PropertyGroup>
  <EnableDefaultApplicationDefinition>false</EnableDefaultApplicationDefinition>
</PropertyGroup>
```

<span data-ttu-id="daaef-193">Bu özellik, varsayılan ayar olan [ `EnableDefaultItems` özelliği](msbuild-props.md#enabledefaultitems) özelliğinin olarak ayarlanmasını gerektirir `true` .</span><span class="sxs-lookup"><span data-stu-id="daaef-193">This property requires that the [`EnableDefaultItems` property](msbuild-props.md#enabledefaultitems) property is set to `true`, which is the default setting.</span></span>

### <a name="enabledefaultpageitems"></a><span data-ttu-id="daaef-194">EnableDefault Page öğeleri</span><span class="sxs-lookup"><span data-stu-id="daaef-194">EnableDefaultPageItems</span></span>

<span data-ttu-id="daaef-195">`EnableDefaultPageItems`Özelliği, `Page` _. xaml_ dosyaları olan öğelerin projeye örtük olarak dahil edilip edilmeyeceğini denetler.</span><span class="sxs-lookup"><span data-stu-id="daaef-195">The `EnableDefaultPageItems` property controls whether `Page` items, which are _.xaml_ files, are implicitly included in the project.</span></span> <span data-ttu-id="daaef-196">`true` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="daaef-196">The default value is `true`.</span></span> <span data-ttu-id="daaef-197">`EnableDefaultPageItems` `false` Örtük dosya eklemeyi devre dışı bırakmak için özelliğini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="daaef-197">Set the `EnableDefaultPageItems` property to `false` to disable the implicit file inclusion.</span></span>

```xml
<PropertyGroup>
  <EnableDefaultPageItems>false</EnableDefaultPageItems>
</PropertyGroup>
```

<span data-ttu-id="daaef-198">Bu özellik, varsayılan ayar olan [ `EnableDefaultItems` özelliği](msbuild-props.md#enabledefaultitems) özelliğinin olarak ayarlanmasını gerektirir `true` .</span><span class="sxs-lookup"><span data-stu-id="daaef-198">This property requires that the [`EnableDefaultItems` property](msbuild-props.md#enabledefaultitems) property is set to `true`, which is the default setting.</span></span>

## <a name="windows-forms-settings"></a><span data-ttu-id="daaef-199">Windows Forms ayarları</span><span class="sxs-lookup"><span data-stu-id="daaef-199">Windows Forms settings</span></span>

- [<span data-ttu-id="daaef-200">UseWindowsForms</span><span class="sxs-lookup"><span data-stu-id="daaef-200">UseWindowsForms</span></span>](#usewindowsforms)

<span data-ttu-id="daaef-201">WinForms 'e özgü olmayan proje özellikleri hakkında daha fazla bilgi için bkz. [.NET SDK projeleri Için MSBuild başvurusu](msbuild-props.md).</span><span class="sxs-lookup"><span data-stu-id="daaef-201">For information about non-WinForms-specific project properties, see [MSBuild reference for .NET SDK projects](msbuild-props.md).</span></span>

### <a name="usewindowsforms"></a><span data-ttu-id="daaef-202">UseWindowsForms</span><span class="sxs-lookup"><span data-stu-id="daaef-202">UseWindowsForms</span></span>

<span data-ttu-id="daaef-203">`UseWindowsForms`Özelliği, uygulamanızın Windows Forms hedefte oluşturulup oluşturulmayacağını denetler.</span><span class="sxs-lookup"><span data-stu-id="daaef-203">The `UseWindowsForms` property controls whether or not your application is built to target Windows Forms.</span></span> <span data-ttu-id="daaef-204">Bu özellik, bir Windows Forms projesini ve ilgili dosyaları doğru şekilde işlemek için MSBuild ardışık düzenini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="daaef-204">This property alters the MSBuild pipeline to correctly process a Windows Forms project and related files.</span></span> <span data-ttu-id="daaef-205">`false` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="daaef-205">The default value is `false`.</span></span> <span data-ttu-id="daaef-206">`UseWindowsForms` `true` Windows Forms desteğini etkinleştirmek için özelliğini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="daaef-206">Set the `UseWindowsForms` property to `true` to enable Windows Forms support.</span></span> <span data-ttu-id="daaef-207">Bu ayar etkinleştirildiğinde yalnızca Windows platformunu hedefleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="daaef-207">You can only target the Windows platform when this setting is enabled.</span></span>

```xml
<PropertyGroup>
  <UseWindowsForms>true</UseWindowsForms>
</PropertyGroup>
```

<span data-ttu-id="daaef-208">Bu özellik olarak ayarlandığında `true` , .NET 5.0 + projeleri, [.net masaüstü SDK 'sını](#enable-net-desktop-sdk)otomatik olarak içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="daaef-208">When this property is set to `true`, .NET 5.0+ projects will automatically import the [.NET Desktop SDK](#enable-net-desktop-sdk).</span></span>

<span data-ttu-id="daaef-209">.NET Core 3,1 projelerinin, bu özelliği kullanmak için [.net masaüstü SDK 'sını](#enable-net-desktop-sdk) açık bir şekilde hedeflemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="daaef-209">.NET Core 3.1 projects need to explicitly target the [.NET Desktop SDK](#enable-net-desktop-sdk) to use this property.</span></span>

## <a name="shared-settings"></a><span data-ttu-id="daaef-210">Paylaşılan ayarlar</span><span class="sxs-lookup"><span data-stu-id="daaef-210">Shared settings</span></span>

- [<span data-ttu-id="daaef-211">Disablewinexeoutputçıkarımı</span><span class="sxs-lookup"><span data-stu-id="daaef-211">DisableWinExeOutputInference</span></span>](#disablewinexeoutputinference)

### <a name="disablewinexeoutputinference"></a><span data-ttu-id="daaef-212">Disablewinexeoutputçıkarımı</span><span class="sxs-lookup"><span data-stu-id="daaef-212">DisableWinExeOutputInference</span></span>

<span data-ttu-id="daaef-213">.NET 5,0 SDK ve üzeri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="daaef-213">Applies to .NET 5.0 SDK and later.</span></span>

<span data-ttu-id="daaef-214">Bir uygulama `Exe` özelliği için ayarlanan değere sahip olduğunda `OutputType` , uygulama bir konsoldan çalışmıyorsa bir konsol penceresi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="daaef-214">When an app has the `Exe` value set for the `OutputType` property, a console window is created if the app isn't running from a console.</span></span> <span data-ttu-id="daaef-215">Bu, genellikle bir Windows masaüstü uygulamasının istenen davranışından değildir.</span><span class="sxs-lookup"><span data-stu-id="daaef-215">This is generally not the desired behavior of a Windows Desktop app.</span></span> <span data-ttu-id="daaef-216">Değeri ile `WinExe` bir konsol penceresi oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="daaef-216">With the `WinExe` value, a console window isn't created.</span></span> <span data-ttu-id="daaef-217">.NET 5,0 SDK ile başlayarak, `Exe` değer otomatik olarak olarak dönüştürülür `WinExe` .</span><span class="sxs-lookup"><span data-stu-id="daaef-217">Starting with the .NET 5.0 SDK, the `Exe` value is automatically transformed to `WinExe`.</span></span>

<span data-ttu-id="daaef-218">`DisableWinExeOutputInference`Özelliği olarak davranma davranışını geri döndürür `Exe` `WinExe` .</span><span class="sxs-lookup"><span data-stu-id="daaef-218">The `DisableWinExeOutputInference` property reverts the behavior of treating `Exe` as `WinExe`.</span></span> <span data-ttu-id="daaef-219">`true`Özellik değerinin davranışını geri yüklemek için bu değeri olarak ayarlayın `OutputType` `Exe` .</span><span class="sxs-lookup"><span data-stu-id="daaef-219">Set this value to `true` to restore the behavior of the `OutputType` property value of `Exe`.</span></span> <span data-ttu-id="daaef-220">`false` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="daaef-220">The default value is `false`.</span></span>

```xml
<PropertyGroup>
  <DisableWinExeOutputInference>true</DisableWinExeOutputInference>
</PropertyGroup>
```

## <a name="see-also"></a><span data-ttu-id="daaef-221">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="daaef-221">See also</span></span>

- [<span data-ttu-id="daaef-222">.NET projesi SDK 'Ları</span><span class="sxs-lookup"><span data-stu-id="daaef-222">.NET project SDKs</span></span>](overview.md)
- [<span data-ttu-id="daaef-223">.NET SDK projeleri için MSBuild başvurusu</span><span class="sxs-lookup"><span data-stu-id="daaef-223">MSBuild reference for .NET SDK projects</span></span>](msbuild-props.md)
- [<span data-ttu-id="daaef-224">MSBuild şema başvurusu</span><span class="sxs-lookup"><span data-stu-id="daaef-224">MSBuild schema reference</span></span>](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [<span data-ttu-id="daaef-225">Ortak MSBuild özellikleri</span><span class="sxs-lookup"><span data-stu-id="daaef-225">Common MSBuild properties</span></span>](/visualstudio/msbuild/common-msbuild-project-properties)
- [<span data-ttu-id="daaef-226">Bir derlemeyi özelleştirme</span><span class="sxs-lookup"><span data-stu-id="daaef-226">Customize a build</span></span>](/visualstudio/msbuild/customize-your-build)
