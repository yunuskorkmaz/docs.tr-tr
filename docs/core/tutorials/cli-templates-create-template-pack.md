---
title: Dotnet için bir şablon paketi Yeni Oluştur
description: Dotnet yeni bir komut için bir şablon paketi oluşturacak bir csproj dosyasının nasıl oluşturulacağını öğrenin.
author: thraka
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: df8c33856195ba7feacd32203e4a885997b50ad2
ms.sourcegitcommit: 6472349821dbe202d01182bc2cfe9d7176eaaa6c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67877185"
---
# <a name="tutorial-create-a-template-pack"></a><span data-ttu-id="024c3-103">Öğretici: Bir şablon paketi oluşturma</span><span class="sxs-lookup"><span data-stu-id="024c3-103">Tutorial: Create a template pack</span></span>

<span data-ttu-id="024c3-104">.NET Core ile oluşturabilir ve projeleri, dosyaları, kaynaklar oluşturmak şablonlar dağıtın.</span><span class="sxs-lookup"><span data-stu-id="024c3-104">With .NET Core, you can create and deploy templates that generate projects, files, even resources.</span></span> <span data-ttu-id="024c3-105">Bu öğretici oluşan oluşturmak, yüklemek ve kaldırmak, şablonları ile kullanılmak öğretir bir serinin üçüncü bölümüdür `dotnet new` komutu.</span><span class="sxs-lookup"><span data-stu-id="024c3-105">This tutorial is part three of a series that teaches you how to create, install, and uninstall, templates for use with the `dotnet new` command.</span></span>

<span data-ttu-id="024c3-106">Serisinin bu bölümünde şunları öğrenirsiniz nasıl yapılır:</span><span class="sxs-lookup"><span data-stu-id="024c3-106">In this part of the series you'll learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="024c3-107">Bir şablon paketi oluşturmak için _.csproj\* proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="024c3-107">Create a _.csproj\* project to build a template pack</span></span>
> * <span data-ttu-id="024c3-108">Paket için proje dosyasını yapılandırın</span><span class="sxs-lookup"><span data-stu-id="024c3-108">Configure the project file for packing</span></span>
> * <span data-ttu-id="024c3-109">NuGet paket dosyasından bir şablonu yükleyin</span><span class="sxs-lookup"><span data-stu-id="024c3-109">Install a template from a NuGet package file</span></span>
> * <span data-ttu-id="024c3-110">Paket kimliğiyle bir şablonu Kaldır</span><span class="sxs-lookup"><span data-stu-id="024c3-110">Uninstall a template by package ID</span></span>

## <a name="prerequisites"></a><span data-ttu-id="024c3-111">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="024c3-111">Prerequisites</span></span>

* <span data-ttu-id="024c3-112">Tam [bölüm 1](cli-templates-create-item-template.md) ve [2. bölüm](cli-templates-create-project-template.md) Bu öğretici serisinin.</span><span class="sxs-lookup"><span data-stu-id="024c3-112">Complete [part 1](cli-templates-create-item-template.md) and [part 2](cli-templates-create-project-template.md) of this tutorial series.</span></span>

  <span data-ttu-id="024c3-113">Bu öğreticide, bu öğreticinin ilk iki bölümlerinde oluşturulan iki şablon kullanılır.</span><span class="sxs-lookup"><span data-stu-id="024c3-113">This tutorial uses the two templates created in the first two parts of this tutorial.</span></span> <span data-ttu-id="024c3-114">Şablon olarak bir klasöre kopyalamanız sürece farklı bir şablon kullanabilirsiniz mümkündür _working\templates\\_  klasör.</span><span class="sxs-lookup"><span data-stu-id="024c3-114">It's possible you can use a different template as long as you copy the template as a folder into the _working\templates\\_ folder.</span></span>

* <span data-ttu-id="024c3-115">Bir terminal açın ve gidin _working\templates\\_  klasör.</span><span class="sxs-lookup"><span data-stu-id="024c3-115">Open a terminal and navigate to the _working\templates\\_ folder.</span></span>

## <a name="create-a-template-pack-project"></a><span data-ttu-id="024c3-116">Bir şablon paketi projesi oluşturun</span><span class="sxs-lookup"><span data-stu-id="024c3-116">Create a template pack project</span></span>

<span data-ttu-id="024c3-117">Şablon dosyası şeklinde bir veya daha fazla şablon paketidir.</span><span class="sxs-lookup"><span data-stu-id="024c3-117">A template pack is one or more templates packaged into a file.</span></span> <span data-ttu-id="024c3-118">Yüklediğinizde veya bir paketi kaldırın, tüm şablonları paketinde eklendiğinde veya kaldırıldığında, sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="024c3-118">When you install or uninstall a pack, all templates contained in the pack are added or removed, respectively.</span></span> <span data-ttu-id="024c3-119">Bu öğretici serisinin önceki bölümlerini yalnızca bireysel şablonlarıyla birlikte çalıştı.</span><span class="sxs-lookup"><span data-stu-id="024c3-119">The previous parts of this tutorial series only worked with individual templates.</span></span> <span data-ttu-id="024c3-120">Dolu olmayan bir şablon paylaşmak için şablonu klasörüne kopyalayıp bu klasöre yüklemek sahip.</span><span class="sxs-lookup"><span data-stu-id="024c3-120">To share a non-packed template, you have to copy the template folder and install via that folder.</span></span> <span data-ttu-id="024c3-121">Çünkü bir şablon paketi birden fazla şablon içinde olabilir ve tek bir dosya paylaşımı daha kolay olur.</span><span class="sxs-lookup"><span data-stu-id="024c3-121">Because a template pack can have more than one template in it, and is a single file, sharing is easier.</span></span>

<span data-ttu-id="024c3-122">Şablon paketleri, bir NuGet paketi tarafından temsil edilir ( _.nupkg_) dosyası.</span><span class="sxs-lookup"><span data-stu-id="024c3-122">Template packs are represented by a NuGet package (_.nupkg_) file.</span></span> <span data-ttu-id="024c3-123">Ayrıca, herhangi bir NuGet paketi gibi bir NuGet akışı için bir şablon paketi karşıya yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="024c3-123">And, like any NuGet package, you can upload the template pack to a NuGet feed.</span></span> <span data-ttu-id="024c3-124">`dotnet new -i` Komut akış NuGet paketinden şablon paketi yüklemeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="024c3-124">The `dotnet new -i` command supports installing template pack from a NuGet package feed.</span></span> <span data-ttu-id="024c3-125">Ayrıca, bir şablon paketini yükleyebilirsiniz. bir _.nupkg_ doğrudan dosya.</span><span class="sxs-lookup"><span data-stu-id="024c3-125">Additionally, you can install a template pack from a _.nupkg_ file directly.</span></span>

<span data-ttu-id="024c3-126">Normalde kullandığınız bir C# Kodu derlemek ve bir ikili oluşturmak için proje dosyası.</span><span class="sxs-lookup"><span data-stu-id="024c3-126">Normally you use a C# project file to compile code and produce a binary.</span></span> <span data-ttu-id="024c3-127">Ancak, projeyi bir şablon paketi oluşturmak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="024c3-127">However, the project can also be used to generate a template pack.</span></span> <span data-ttu-id="024c3-128">Ayarlarını değiştirerek _.csproj_, herhangi bir kod derlemesini önlemek ve bunun yerine şablonlarınızın kaynakları olarak tüm varlıkları içerir.</span><span class="sxs-lookup"><span data-stu-id="024c3-128">By changing the settings of the _.csproj_, you can prevent it from compiling any code and instead include all the assets of your templates as resources.</span></span> <span data-ttu-id="024c3-129">Bu proje oluşturulurken bir şablon paketi NuGet paketi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="024c3-129">When this project is built, it produces a template pack NuGet package.</span></span>

<span data-ttu-id="024c3-130">Oluşturduğunuz paketi içerecektir [öğe şablonu](cli-templates-create-item-template.md) ve [paketi şablonu](cli-templates-create-project-template.md) önceden oluşturulmuş.</span><span class="sxs-lookup"><span data-stu-id="024c3-130">The pack you'll create will include the [item template](cli-templates-create-item-template.md) and [package template](cli-templates-create-project-template.md) previously created.</span></span> <span data-ttu-id="024c3-131">Şu iki şablonlara gruplandırılmış çünkü _working\templates\\_  kullanabiliriz klasöründe _çalışma_ klasör _.csproj_ dosya.</span><span class="sxs-lookup"><span data-stu-id="024c3-131">Because we grouped the two templates into the _working\templates\\_ folder, we can use the _working_ folder for the _.csproj_ file.</span></span>

<span data-ttu-id="024c3-132">Terminalinizde gidin _çalışma_ klasör.</span><span class="sxs-lookup"><span data-stu-id="024c3-132">In your terminal, navigate to the _working_ folder.</span></span> <span data-ttu-id="024c3-133">Yeni proje oluşturma ve kümesinin adı `templatepack` ve geçerli klasörle çıkış klasörü.</span><span class="sxs-lookup"><span data-stu-id="024c3-133">Create a new project and set the name to `templatepack` and the output folder to the current folder.</span></span>

```console
dotnet new console -n templatepack -o .
```

<span data-ttu-id="024c3-134">`-n` Parametre kümeleri _.csproj_ dosya adına _templatepack.csproj_ ve `-o` parametreleri geçerli dizinde dosyaları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="024c3-134">The `-n` parameter sets the _.csproj_ filename to _templatepack.csproj_ and the `-o` parameters creates the files in the current directory.</span></span> <span data-ttu-id="024c3-135">Aşağıdaki çıktıya benzer bir sonuç görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="024c3-135">You should see a result similar to the following output.</span></span>

```console
C:\working> dotnet new console -n templatepack -o .
The template "Console Application" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on .\templatepack.csproj...
  Restore completed in 52.38 ms for C:\working\templatepack.csproj.

Restore succeeded.
```

<span data-ttu-id="024c3-136">Ardından, açık _templatepack.csproj_ dosya sık kullandığınız düzenleyicinizde ve içeriği aşağıdaki XML ile değiştirin:</span><span class="sxs-lookup"><span data-stu-id="024c3-136">Next, open the _templatepack.csproj_ file in your favorite editor and replace the content with the following XML:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <PackageType>Template</PackageType>
    <PackageVersion>1.0</PackageVersion>
    <PackageId>AdatumCorporation.Utility.Templates</PackageId>
    <Title>AdatumCorporation Templates</Title>
    <Authors>Me</Authors>
    <Description>Templates to use when creating an application for Adatum Corporation.</Description>
    <PackageTags>dotnet-new;templates;contoso</PackageTags>

    <TargetFramework>netstandard2.0</TargetFramework>

    <IncludeContentInPack>true</IncludeContentInPack>
    <IncludeBuildOutput>false</IncludeBuildOutput>
    <ContentTargetFolders>content</ContentTargetFolders>
  </PropertyGroup>

  <ItemGroup>
    <Content Include="templates\**\*" Exclude="templates\**\bin\**;templates\**\obj\**" />
    <Compile Remove="**\*" />
  </ItemGroup>

</Project>
```

<span data-ttu-id="024c3-137">`<PropertyGroup>` Yukarıdaki XML ayarlarında üç gruplar halinde ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="024c3-137">The `<PropertyGroup>` settings in the XML above is broken into three groups.</span></span> <span data-ttu-id="024c3-138">İlk grup, bir NuGet paketi için gerekli özellikleri ile ilgilenir.</span><span class="sxs-lookup"><span data-stu-id="024c3-138">The first group deals with properties required for a NuGet package.</span></span> <span data-ttu-id="024c3-139">Üç `<Package` ile NuGet paketinizi üzerinde bir NuGet akışı tanımlamak için özellikleri paketlemek ayarlara sahip.</span><span class="sxs-lookup"><span data-stu-id="024c3-139">The three `<Package` settings have to do with the NuGet package properties to identify your package on a NuGet feed.</span></span> <span data-ttu-id="024c3-140">Özellikle `<PacakgeId>` değeri bir dizin yolu yerine tek bir ada sahip bir şablon paketi kaldırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="024c3-140">Specifically the `<PacakgeId>` value is used to uninstall the template pack with a single name instead of a directory path.</span></span> <span data-ttu-id="024c3-141">Ayrıca, bir NuGet akışı tarafından bir şablon paketi yüklemek için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="024c3-141">It can also be used to install the template pack from a NuGet feed.</span></span> <span data-ttu-id="024c3-142">Diğer ayarlar gibi `<Title>` ve `<Tags>` NuGet üzerinde görüntülenen meta verilerle akışa sahip.</span><span class="sxs-lookup"><span data-stu-id="024c3-142">The remaining settings such as `<Title>` and `<Tags>` have to do with metadata displayed on the NuGet feed.</span></span> <span data-ttu-id="024c3-143">NuGet ayarları hakkında daha fazla bilgi için bkz. [NuGet ve MSBuild özellikleri](/nuget/reference/msbuild-targets).</span><span class="sxs-lookup"><span data-stu-id="024c3-143">For more information about NuGet settings, see [NuGet and MSBuild properties](/nuget/reference/msbuild-targets).</span></span>

<span data-ttu-id="024c3-144">`<TargetFramework>` Derlemek ve proje paketi için paketi komutu çalıştırdığınızda MSBuild düzgün şekilde çalışması ayarı ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="024c3-144">The `<TargetFramework>` setting must be set so that MSBuild will run properly when you run the pack command to compile and pack the project.</span></span>

<span data-ttu-id="024c3-145">Son üç ayarları oluşturulduğunda, proje düzgün uygun NuGet klasöründe şablonları içerecek şekilde yapılandırarak paketi gerekir.</span><span class="sxs-lookup"><span data-stu-id="024c3-145">The last three settings have to do with configuring the project correctly to include the templates in the appropriate folder in the NuGet pack when it's created.</span></span>

<span data-ttu-id="024c3-146">`<ItemGroup>` İki ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="024c3-146">The `<ItemGroup>` contains two settings.</span></span> <span data-ttu-id="024c3-147">İlk olarak, `<Content>` ayarı her şeyi içeren _şablonları_ klasör içeriği.</span><span class="sxs-lookup"><span data-stu-id="024c3-147">First, the `<Content>` setting includes everything in the _templates_ folder as content.</span></span> <span data-ttu-id="024c3-148">Ayrıca tüm hariç tutmak için ayarlanmış _bin_ klasör veya _obj_ herhangi önlemek için klasör derlenmiş kod (test ve şablonlarınızı derlenmiş varsa) dahil olan.</span><span class="sxs-lookup"><span data-stu-id="024c3-148">It's also set to exclude any _bin_ folder or _obj_ folder to prevent any compiled code (if you tested and compiled your templates) from being included.</span></span> <span data-ttu-id="024c3-149">İkinci olarak, `<Compile>` ayarı derlenmesini bulundukları fark etmeksizin tüm kod dosyaları hariç tutar.</span><span class="sxs-lookup"><span data-stu-id="024c3-149">Second, the `<Compile>` setting excludes all code files from compiling no matter where they're located.</span></span> <span data-ttu-id="024c3-150">Bu ayar, kodu derlemek çalışan bir şablon paketi oluşturmak için kullanılan proje engeller _şablonları_ klasör hiyerarşisi.</span><span class="sxs-lookup"><span data-stu-id="024c3-150">This setting prevents the project being used to create a template pack from trying to compile the code in the _templates_ folder hierarchy.</span></span>

## <a name="build-and-install"></a><span data-ttu-id="024c3-151">Derleme ve yükleme</span><span class="sxs-lookup"><span data-stu-id="024c3-151">Build and install</span></span>

<span data-ttu-id="024c3-152">Bu dosyayı kaydedin ve ardından Paketi komutu çalıştırın</span><span class="sxs-lookup"><span data-stu-id="024c3-152">Save this file and then run the pack command</span></span>

```console
dotnet pack
```

<span data-ttu-id="024c3-153">Bu komut, projeyi oluşturun ve bu pakette olmalıdır bir NuGet oluşturma _working\bin\Debug_ klasör.</span><span class="sxs-lookup"><span data-stu-id="024c3-153">This command will build your project and create a NuGet package in This should be the _working\bin\Debug_ folder.</span></span>

```console
C:\working> dotnet pack
Microsoft (R) Build Engine version 16.2.0-preview-19278-01+d635043bd for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 123.86 ms for C:\working\templatepack.csproj.

  templatepack -> C:\working\bin\Debug\netstandard2.0\templatepack.dll
  Successfully created package 'C:\working\bin\Debug\AdatumCorporation.Utility.Templates.1.0.0.nupkg'.
```

<span data-ttu-id="024c3-154">Ardından, şablon paketi dosyasını yükleyin `dotnet new -i PATH_TO_NUPKG_FILE` komutu.</span><span class="sxs-lookup"><span data-stu-id="024c3-154">Next, install the template pack file with the `dotnet new -i PATH_TO_NUPKG_FILE` command.</span></span>

```console
C:\working> dotnet new -i C:\working\bin\Debug\AdatumCorporation.Utility.Templates.1.0.0.nupkg
Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.

... cut to save space ...

Templates                                         Short Name            Language          Tags
-------------------------------------------------------------------------------------------------------------------------------
Example templates: string extensions              stringext             [C#]              Common/Code
Console Application                               console               [C#], F#, VB      Common/Console
Example templates: async project                  consoleasync          [C#]              Common/Console/C#8
Class library                                     classlib              [C#], F#, VB      Common/Library
```

<span data-ttu-id="024c3-155">NuGet paketi için bir NuGet akışı karşıya yüklediyseniz, kullanabileceğiniz `dotnet new -i PACKAGEID` komut nerede `PACKAGEID` aynı `<PackageId>` ayarını _.csproj_ dosya.</span><span class="sxs-lookup"><span data-stu-id="024c3-155">If you uploaded the NuGet package to a NuGet feed, you can use the `dotnet new -i PACKAGEID` command where `PACKAGEID` is the same as the `<PackageId>` setting from the _.csproj_ file.</span></span> <span data-ttu-id="024c3-156">Bu paket kimliği, NuGet paket tanımlayıcısı ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="024c3-156">This package ID is the same as the NuGet package identifier.</span></span>

## <a name="uninstall-the-template-pack"></a><span data-ttu-id="024c3-157">Şablon paketi kaldırma</span><span class="sxs-lookup"><span data-stu-id="024c3-157">Uninstall the template pack</span></span>

<span data-ttu-id="024c3-158">Şablon paketi, ile nasıl yüklediğiniz ne olursa olsun _.nupkg_ dosyası doğrudan veya NuGet akışı, bir şablon paketi kaldırma aynıdır.</span><span class="sxs-lookup"><span data-stu-id="024c3-158">No matter how you installed the template pack, either with the _.nupkg_ file directly or by NuGet feed, removing a template pack is the same.</span></span> <span data-ttu-id="024c3-159">Kullanım `<PackageId>` kaldırmak istediğiniz şablonu.</span><span class="sxs-lookup"><span data-stu-id="024c3-159">Use the `<PackageId>` of the template you want to uninstall.</span></span> <span data-ttu-id="024c3-160">Çalıştırarak yüklü şablonları listesini alabilirsiniz `dotnet new -u` komutu.</span><span class="sxs-lookup"><span data-stu-id="024c3-160">You can get a list of templates that are installed by running the `dotnet new -u` command.</span></span>

```console
C:\working> dotnet new -u
Template Instantiation Commands for .NET Core CLI

Currently installed items:
  Microsoft.DotNet.Common.ItemTemplates
    Templates:
      dotnet gitignore file (gitignore)
      global.json file (globaljson)
      NuGet Config (nugetconfig)
      Solution File (sln)
      Dotnet local tool manifest file (tool-manifest)
      Web Config (webconfig)

... cut to save space ...

  NUnit3.DotNetNew.Template
    Templates:
      NUnit 3 Test Project (nunit) C#
      NUnit 3 Test Item (nunit-test) C#
      NUnit 3 Test Project (nunit) F#
      NUnit 3 Test Item (nunit-test) F#
      NUnit 3 Test Project (nunit) VB
      NUnit 3 Test Item (nunit-test) VB
  AdatumCorporation.Utility.Templates
    Templates:
      Example templates: async project (consoleasync) C#
      Example templates: string extensions (stringext) C#
```

<span data-ttu-id="024c3-161">Çalıştırma `dotnet new -u AdatumCorporation.Utility.Templates` şablonu kaldırmak için.</span><span class="sxs-lookup"><span data-stu-id="024c3-161">Run `dotnet new -u AdatumCorporation.Utility.Templates` to uninstall the template.</span></span> <span data-ttu-id="024c3-162">`dotnet new` Komut önceden yüklenmiş şablonlar atlamak Yardım bilgilerini çıktısı.</span><span class="sxs-lookup"><span data-stu-id="024c3-162">The `dotnet new` command will output help information that should omit the templates you previously installed.</span></span>

<span data-ttu-id="024c3-163">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="024c3-163">Congratulations!</span></span> <span data-ttu-id="024c3-164">yüklemiş ve bir şablon paketi kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="024c3-164">you've installed and uninstalled a template pack.</span></span> 

## <a name="next-steps"></a><span data-ttu-id="024c3-165">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="024c3-165">Next steps</span></span>

<span data-ttu-id="024c3-166">Daha fazla şablonları hakkında en zaten hangisinin öğrendiğinize göre bilgi edinmek için [yeni dotnet için özel şablonları](../tools/custom-templates.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="024c3-166">To learn more about templates, most of which you've already learned, see the [Custom templates for dotnet new](../tools/custom-templates.md) article.</span></span>

* [<span data-ttu-id="024c3-167">DotNet/şablon GitHub deposunu Wiki</span><span class="sxs-lookup"><span data-stu-id="024c3-167">dotnet/templating GitHub repo Wiki</span></span>](https://github.com/dotnet/templating/wiki)
* [<span data-ttu-id="024c3-168">DotNet/dotnet-şablonu-örnekleri GitHub deposu</span><span class="sxs-lookup"><span data-stu-id="024c3-168">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
* [<span data-ttu-id="024c3-169">*Template.JSON* JSON şema Store şema</span><span class="sxs-lookup"><span data-stu-id="024c3-169">*template.json* schema at the JSON Schema Store</span></span>](http://json.schemastore.org/template)
