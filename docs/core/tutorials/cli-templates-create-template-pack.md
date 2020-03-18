---
title: dotnet yeni için bir şablon paketi oluşturma
description: Dotnet yeni komutu için bir şablon paketi oluşturacak bir csproj dosyası oluşturmayı öğrenin.
author: thraka
ms.date: 12/10/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: 5bc926861dd6a501d7c2d24bd5f7c4116cc78b2c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503496"
---
# <a name="tutorial-create-a-template-pack"></a><span data-ttu-id="4761c-103">Öğretici: Şablon paketi oluşturma</span><span class="sxs-lookup"><span data-stu-id="4761c-103">Tutorial: Create a template pack</span></span>

<span data-ttu-id="4761c-104">.NET Core ile, projeler, dosyalar ve hatta kaynaklar oluşturan şablonlar oluşturabilir ve dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4761c-104">With .NET Core, you can create and deploy templates that generate projects, files, even resources.</span></span> <span data-ttu-id="4761c-105">Bu öğretici, `dotnet new` komutla birlikte kullanmak üzere şablonoluşturma, yükleme ve kaldırma yı öğreten bir serinin üçüncü bölümüdür.</span><span class="sxs-lookup"><span data-stu-id="4761c-105">This tutorial is part three of a series that teaches you how to create, install, and uninstall templates for use with the `dotnet new` command.</span></span>

<span data-ttu-id="4761c-106">Serinin bu bölümünde nasıl öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="4761c-106">In this part of the series you'll learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="4761c-107">Şablon \*paketi oluşturmak için .csproj projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="4761c-107">Create a \*.csproj project to build a template pack</span></span>
> * <span data-ttu-id="4761c-108">Paketleme için proje dosyasını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="4761c-108">Configure the project file for packing</span></span>
> * <span data-ttu-id="4761c-109">NuGet paket dosyasından şablon yükleme</span><span class="sxs-lookup"><span data-stu-id="4761c-109">Install a template from a NuGet package file</span></span>
> * <span data-ttu-id="4761c-110">Şablonu paket kimliğine göre kaldırma</span><span class="sxs-lookup"><span data-stu-id="4761c-110">Uninstall a template by package ID</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4761c-111">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="4761c-111">Prerequisites</span></span>

* <span data-ttu-id="4761c-112">Bu öğretici serisinin [bölüm 1](cli-templates-create-item-template.md) ve [bölüm 2](cli-templates-create-project-template.md) tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="4761c-112">Complete [part 1](cli-templates-create-item-template.md) and [part 2](cli-templates-create-project-template.md) of this tutorial series.</span></span>

  <span data-ttu-id="4761c-113">Bu öğretici, bu öğreticinin ilk iki parçasında oluşturulan iki şablonu kullanır.</span><span class="sxs-lookup"><span data-stu-id="4761c-113">This tutorial uses the two templates created in the first two parts of this tutorial.</span></span> <span data-ttu-id="4761c-114">Şablonu klasör olarak kopyaladığınız sürece farklı bir şablon _kullanabilirsiniz.\\ _</span><span class="sxs-lookup"><span data-stu-id="4761c-114">You can use a different template as long as you copy the template, as a folder, into the _working\templates\\_ folder.</span></span>

* <span data-ttu-id="4761c-115">Bir terminal açın ve _\\ çalışma_ klasörüne gidin.</span><span class="sxs-lookup"><span data-stu-id="4761c-115">Open a terminal and navigate to the _working\\_ folder.</span></span>

## <a name="create-a-template-pack-project"></a><span data-ttu-id="4761c-116">Şablon paketi projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="4761c-116">Create a template pack project</span></span>

<span data-ttu-id="4761c-117">Şablon paketi, dosyaya paketlenmiş bir veya daha fazla şablondur.</span><span class="sxs-lookup"><span data-stu-id="4761c-117">A template pack is one or more templates packaged into a file.</span></span> <span data-ttu-id="4761c-118">Bir paketi yüklediğinizde veya kaldırdığınızda, pakette bulunan tüm şablonlar sırasıyla eklenir veya kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="4761c-118">When you install or uninstall a pack, all templates contained in the pack are added or removed, respectively.</span></span> <span data-ttu-id="4761c-119">Bu öğretici serinin önceki bölümleri yalnızca tek tek şablonlarla çalıştı.</span><span class="sxs-lookup"><span data-stu-id="4761c-119">The previous parts of this tutorial series only worked with individual templates.</span></span> <span data-ttu-id="4761c-120">Paketlenmemiş bir şablonu paylaşmak için şablon klasörünü kopyalamanız ve bu klasör üzerinden yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4761c-120">To share a non-packed template, you have to copy the template folder and install via that folder.</span></span> <span data-ttu-id="4761c-121">Şablon paketinde birden fazla şablon olabileceğinden ve tek bir dosya olduğundan, paylaşmak daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="4761c-121">Because a template pack can have more than one template in it, and is a single file, sharing is easier.</span></span>

<span data-ttu-id="4761c-122">Şablon paketleri nuget paketi (_.nupkg_) dosyası yla temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="4761c-122">Template packs are represented by a NuGet package (_.nupkg_) file.</span></span> <span data-ttu-id="4761c-123">Ayrıca, herhangi bir NuGet paketi gibi, şablon paketini bir NuGet akışına yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4761c-123">And, like any NuGet package, you can upload the template pack to a NuGet feed.</span></span> <span data-ttu-id="4761c-124">Komut, `dotnet new -i` NuGet paket akışından şablon paketi yüklemeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="4761c-124">The `dotnet new -i` command supports installing template pack from a NuGet package feed.</span></span> <span data-ttu-id="4761c-125">Ayrıca, bir _.nupkg_ dosyasından doğrudan bir şablon paketi yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4761c-125">Additionally, you can install a template pack from a _.nupkg_ file directly.</span></span>

<span data-ttu-id="4761c-126">Normalde kod derlemek ve ikili oluşturmak için bir C# proje dosyası kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="4761c-126">Normally you use a C# project file to compile code and produce a binary.</span></span> <span data-ttu-id="4761c-127">Ancak, proje bir şablon paketi oluşturmak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4761c-127">However, the project can also be used to generate a template pack.</span></span> <span data-ttu-id="4761c-128">_.csproj'un_ayarlarını değiştirerek, kodu derlemesini engelleyebilir ve bunun yerine şablonlarınızın tüm varlıklarını kaynak olarak ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4761c-128">By changing the settings of the _.csproj_, you can prevent it from compiling any code and instead include all the assets of your templates as resources.</span></span> <span data-ttu-id="4761c-129">Bu proje oluşturulduğunda, bir şablon paketi NuGet paketi üretir.</span><span class="sxs-lookup"><span data-stu-id="4761c-129">When this project is built, it produces a template pack NuGet package.</span></span>

<span data-ttu-id="4761c-130">Oluşturacağınız paket, daha önce oluşturulmuş [öğe şablonu](cli-templates-create-item-template.md) ve [paket şablonuna](cli-templates-create-project-template.md) dahil olur.</span><span class="sxs-lookup"><span data-stu-id="4761c-130">The pack you'll create will include the [item template](cli-templates-create-item-template.md) and [package template](cli-templates-create-project-template.md) previously created.</span></span> <span data-ttu-id="4761c-131">İki şablonu _çalışma\şablonlar\\ _ klasöründe gruplandırdığımız için _,.csproj_ dosyasının _çalışma_ klasörünü kullanabiliriz.</span><span class="sxs-lookup"><span data-stu-id="4761c-131">Because we grouped the two templates into the _working\templates\\_ folder, we can use the _working_ folder for the _.csproj_ file.</span></span>

<span data-ttu-id="4761c-132">Terminalinizde, _çalışma_ klasörüne gidin.</span><span class="sxs-lookup"><span data-stu-id="4761c-132">In your terminal, navigate to the _working_ folder.</span></span> <span data-ttu-id="4761c-133">Yeni bir proje oluşturun ve `templatepack` adı ve çıktı klasörünü geçerli klasöre ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4761c-133">Create a new project and set the name to `templatepack` and the output folder to the current folder.</span></span>

```dotnetcli
dotnet new console -n templatepack -o .
```

<span data-ttu-id="4761c-134">Parametre `-n` _.csproj_ dosya adını _templatepack.csproj_olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4761c-134">The `-n` parameter sets the _.csproj_ filename to _templatepack.csproj_.</span></span> <span data-ttu-id="4761c-135">Parametre `-o` geçerli dizindeki dosyaları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4761c-135">The `-o` parameter creates the files in the current directory.</span></span> <span data-ttu-id="4761c-136">Aşağıdaki çıktıya benzer bir sonuç görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4761c-136">You should see a result similar to the following output.</span></span>

```dotnetcli
dotnet new console -n templatepack -o .
```

```console
The template "Console Application" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on .\templatepack.csproj...
  Restore completed in 52.38 ms for C:\working\templatepack.csproj.

Restore succeeded.
```

<span data-ttu-id="4761c-137">Ardından, en sevdiğiniz düzenleyicide _templatepack.csproj_ dosyasını açın ve içeriği aşağıdaki XML ile değiştirin:</span><span class="sxs-lookup"><span data-stu-id="4761c-137">Next, open the _templatepack.csproj_ file in your favorite editor and replace the content with the following XML:</span></span>

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

<span data-ttu-id="4761c-138">Yukarıdaki `<PropertyGroup>` XML'deki ayarlar üç gruba ayrılır.</span><span class="sxs-lookup"><span data-stu-id="4761c-138">The `<PropertyGroup>` settings in the XML above is broken into three groups.</span></span> <span data-ttu-id="4761c-139">İlk grup, NuGet paketi için gerekli özelliklerle ilgilenir.</span><span class="sxs-lookup"><span data-stu-id="4761c-139">The first group deals with properties required for a NuGet package.</span></span> <span data-ttu-id="4761c-140">Üç `<Package` ayar, paketinizi NuGet akışında tanımlamak için NuGet paket özellikleriyle ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="4761c-140">The three `<Package` settings have to do with the NuGet package properties to identify your package on a NuGet feed.</span></span> <span data-ttu-id="4761c-141">Özellikle `<PackageId>` değer, dizin yolu yerine tek bir adla şablon paketini kaldırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4761c-141">Specifically the `<PackageId>` value is used to uninstall the template pack with a single name instead of a directory path.</span></span> <span data-ttu-id="4761c-142">NuGet akışından şablon paketini yüklemek için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4761c-142">It can also be used to install the template pack from a NuGet feed.</span></span> <span data-ttu-id="4761c-143">NuGet akışında `<Title>` `<PackageTags>` görüntülenen meta veriler gibi kalan ayarlar ve ilgili.</span><span class="sxs-lookup"><span data-stu-id="4761c-143">The remaining settings such as `<Title>` and `<PackageTags>` have to do with metadata displayed on the NuGet feed.</span></span> <span data-ttu-id="4761c-144">NuGet ayarları hakkında daha fazla bilgi için [NuGet ve MSBuild özelliklerine](/nuget/reference/msbuild-targets)bakın.</span><span class="sxs-lookup"><span data-stu-id="4761c-144">For more information about NuGet settings, see [NuGet and MSBuild properties](/nuget/reference/msbuild-targets).</span></span>

<span data-ttu-id="4761c-145">Ayarı, `<TargetFramework>` projeyi derlemek ve paketlemek için paket komutunu çalıştırdığınızda MSBuild'in düzgün çalışacak şekilde ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4761c-145">The `<TargetFramework>` setting must be set so that MSBuild will run properly when you run the pack command to compile and pack the project.</span></span>

<span data-ttu-id="4761c-146">Son üç ayar, oluşturulduğunda şablonları NuGet paketindeki uygun klasöre eklemek için projeyi doğru şekilde yapılandırmakile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="4761c-146">The last three settings have to do with configuring the project correctly to include the templates in the appropriate folder in the NuGet pack when it's created.</span></span>

<span data-ttu-id="4761c-147">İki `<ItemGroup>` ayar içerir.</span><span class="sxs-lookup"><span data-stu-id="4761c-147">The `<ItemGroup>` contains two settings.</span></span> <span data-ttu-id="4761c-148">Ayar, `<Content>` _şablonlar_ klasöründeki her şeyi içerik olarak içerir.</span><span class="sxs-lookup"><span data-stu-id="4761c-148">First, the `<Content>` setting includes everything in the _templates_ folder as content.</span></span> <span data-ttu-id="4761c-149">Ayrıca, derlenmiş herhangi bir kodun (şablonlarınızı test ettiyseniz ve derlediyseniz) eklenmesini önlemek için herhangi bir _depo kutusu_ klasörünü veya _obj_ klasörünü hariç tutmak için ayarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="4761c-149">It's also set to exclude any _bin_ folder or _obj_ folder to prevent any compiled code (if you tested and compiled your templates) from being included.</span></span> <span data-ttu-id="4761c-150">İkinci olarak, `<Compile>` ayar, nerede olurlarsa olsunlar tüm kod dosyalarının derlemisini hariç tutar.</span><span class="sxs-lookup"><span data-stu-id="4761c-150">Second, the `<Compile>` setting excludes all code files from compiling no matter where they're located.</span></span> <span data-ttu-id="4761c-151">Bu ayar, şablon paketi oluşturmak için kullanılan projenin _şablonlar_ klasörü hiyerarşisinde kodu derlemeye çalışmasına engel lenir.</span><span class="sxs-lookup"><span data-stu-id="4761c-151">This setting prevents the project being used to create a template pack from trying to compile the code in the _templates_ folder hierarchy.</span></span>

## <a name="build-and-install"></a><span data-ttu-id="4761c-152">Oluşturma ve yükleme</span><span class="sxs-lookup"><span data-stu-id="4761c-152">Build and install</span></span>

<span data-ttu-id="4761c-153">Bu dosyayı kaydedin ve paket komutunu çalıştırın</span><span class="sxs-lookup"><span data-stu-id="4761c-153">Save this file and then run the pack command</span></span>

```dotnetcli
dotnet pack
```

<span data-ttu-id="4761c-154">Bu komut projenizi oluşturur ve bu _çalışma\bin\Hata Ayıklama_ klasöründe bir NuGet paketi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4761c-154">This command will build your project and create a NuGet package in This should be the _working\bin\Debug_ folder.</span></span>

```dotnetcli
dotnet pack
```

```console
Microsoft (R) Build Engine version 16.2.0-preview-19278-01+d635043bd for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 123.86 ms for C:\working\templatepack.csproj.

  templatepack -> C:\working\bin\Debug\netstandard2.0\templatepack.dll
  Successfully created package 'C:\working\bin\Debug\AdatumCorporation.Utility.Templates.1.0.0.nupkg'.
```

<span data-ttu-id="4761c-155">Ardından, şablon paketi dosyasını `dotnet new -i PATH_TO_NUPKG_FILE` komutla yükleyin.</span><span class="sxs-lookup"><span data-stu-id="4761c-155">Next, install the template pack file with the `dotnet new -i PATH_TO_NUPKG_FILE` command.</span></span>

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

<span data-ttu-id="4761c-156">NuGet paketini nuget akışına yüklediyseniz, `dotnet new -i PACKAGEID` _.csproj_ dosyasındaki `<PackageId>` ayarla aynı olan `PACKAGEID` komutu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4761c-156">If you uploaded the NuGet package to a NuGet feed, you can use the `dotnet new -i PACKAGEID` command where `PACKAGEID` is the same as the `<PackageId>` setting from the _.csproj_ file.</span></span> <span data-ttu-id="4761c-157">Bu paket kimliği NuGet paket tanımlayıcısı ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="4761c-157">This package ID is the same as the NuGet package identifier.</span></span>

## <a name="uninstall-the-template-pack"></a><span data-ttu-id="4761c-158">Şablon paketini kaldırma</span><span class="sxs-lookup"><span data-stu-id="4761c-158">Uninstall the template pack</span></span>

<span data-ttu-id="4761c-159">Şablon paketini doğrudan _.nupkg_ dosyasıyla veya NuGet akışıyla nasıl yüklediğinizönemli olursa olsun, şablon paketini kaldırmak aynıdır.</span><span class="sxs-lookup"><span data-stu-id="4761c-159">No matter how you installed the template pack, either with the _.nupkg_ file directly or by NuGet feed, removing a template pack is the same.</span></span> <span data-ttu-id="4761c-160">Kaldırmak `<PackageId>` istediğiniz şablonun kullanın.</span><span class="sxs-lookup"><span data-stu-id="4761c-160">Use the `<PackageId>` of the template you want to uninstall.</span></span> <span data-ttu-id="4761c-161">`dotnet new -u` Komutu çalıştırarak yüklenen şablonların bir listesini alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4761c-161">You can get a list of templates that are installed by running the `dotnet new -u` command.</span></span>

```dotnetcli
dotnet new -u
```

```console
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

<span data-ttu-id="4761c-162">Şablonu kaldırmak için çalıştırın. `dotnet new -u AdatumCorporation.Utility.Templates`</span><span class="sxs-lookup"><span data-stu-id="4761c-162">Run `dotnet new -u AdatumCorporation.Utility.Templates` to uninstall the template.</span></span> <span data-ttu-id="4761c-163">Komut, `dotnet new` daha önce yüklediğiniz şablonları atlayacak yardım bilgilerini çıktıracaktır.</span><span class="sxs-lookup"><span data-stu-id="4761c-163">The `dotnet new` command will output help information that should omit the templates you previously installed.</span></span>

<span data-ttu-id="4761c-164">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="4761c-164">Congratulations!</span></span> <span data-ttu-id="4761c-165">bir şablon paketi yüklemiş ve kaldırmışsınız.</span><span class="sxs-lookup"><span data-stu-id="4761c-165">you've installed and uninstalled a template pack.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4761c-166">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="4761c-166">Next steps</span></span>

<span data-ttu-id="4761c-167">Çoğu zaten öğrenmiş olduğunuz şablonlar hakkında daha fazla bilgi edinmek [için dotnet yeni](../tools/custom-templates.md) makalesi için Özel şablonlara bakın.</span><span class="sxs-lookup"><span data-stu-id="4761c-167">To learn more about templates, most of which you've already learned, see the [Custom templates for dotnet new](../tools/custom-templates.md) article.</span></span>

* [<span data-ttu-id="4761c-168">dotnet/templating GitHub repo Wiki</span><span class="sxs-lookup"><span data-stu-id="4761c-168">dotnet/templating GitHub repo Wiki</span></span>](https://github.com/dotnet/templating/wiki)
* [<span data-ttu-id="4761c-169">dotnet/dotnet-şablon-örnekleri GitHub repo</span><span class="sxs-lookup"><span data-stu-id="4761c-169">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
* [<span data-ttu-id="4761c-170">json Schema Mağazası'nda *template.json* şema</span><span class="sxs-lookup"><span data-stu-id="4761c-170">*template.json* schema at the JSON Schema Store</span></span>](http://json.schemastore.org/template)
