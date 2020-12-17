---
title: DotNet New için bir şablon paketi oluşturma
description: DotNet yeni komut için bir şablon paketi oluşturacak bir csproj dosyası oluşturmayı öğrenin.
author: adegeo
ms.date: 12/11/2020
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: 2aea143f1e41d580de41a9cc9e924d70b55695db
ms.sourcegitcommit: 635a0ff775d2447a81ef7233a599b8f88b162e5d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97633604"
---
# <a name="tutorial-create-a-template-pack"></a><span data-ttu-id="9a110-103">Öğretici: şablon paketi oluşturma</span><span class="sxs-lookup"><span data-stu-id="9a110-103">Tutorial: Create a template pack</span></span>

<span data-ttu-id="9a110-104">.NET ile, projeler, dosyalar ve hatta kaynaklar üreten şablonlar oluşturabilir ve dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a110-104">With .NET, you can create and deploy templates that generate projects, files, even resources.</span></span> <span data-ttu-id="9a110-105">Bu öğretici, komutuyla kullanmak üzere şablon oluşturmayı, yüklemeyi ve kaldırmayı öğretir ve bir serinin üçüncü bölümüdür `dotnet new` .</span><span class="sxs-lookup"><span data-stu-id="9a110-105">This tutorial is part three of a series that teaches you how to create, install, and uninstall templates for use with the `dotnet new` command.</span></span>

<span data-ttu-id="9a110-106">Serinin bu bölümünde şunları nasıl yapacağınızı öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="9a110-106">In this part of the series you'll learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="9a110-107">\*Bir şablon paketi oluşturmak için bir. csproj projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="9a110-107">Create a \*.csproj project to build a template pack</span></span>
> * <span data-ttu-id="9a110-108">Paketleme için proje dosyasını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="9a110-108">Configure the project file for packing</span></span>
> * <span data-ttu-id="9a110-109">NuGet paket dosyasından şablon yükler</span><span class="sxs-lookup"><span data-stu-id="9a110-109">Install a template from a NuGet package file</span></span>
> * <span data-ttu-id="9a110-110">Bir şablonu paket KIMLIĞIYLE kaldır</span><span class="sxs-lookup"><span data-stu-id="9a110-110">Uninstall a template by package ID</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9a110-111">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="9a110-111">Prerequisites</span></span>

* <span data-ttu-id="9a110-112">Bu öğretici serisinin [1](cli-templates-create-item-template.md) . ve [2. bölümünü](cli-templates-create-project-template.md) doldurun.</span><span class="sxs-lookup"><span data-stu-id="9a110-112">Complete [part 1](cli-templates-create-item-template.md) and [part 2](cli-templates-create-project-template.md) of this tutorial series.</span></span>

  <span data-ttu-id="9a110-113">Bu öğretici, Bu öğreticinin ilk iki bölümünde oluşturulan iki şablonu kullanır.</span><span class="sxs-lookup"><span data-stu-id="9a110-113">This tutorial uses the two templates created in the first two parts of this tutorial.</span></span> <span data-ttu-id="9a110-114">Şablonu, klasör olarak _working\templates \\_ klasörüne kopyaladığınız sürece farklı bir şablon kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a110-114">You can use a different template as long as you copy the template, as a folder, into the _working\templates\\_ folder.</span></span>

* <span data-ttu-id="9a110-115">Bir Terminal açın ve _çalışma \\_ klasörüne gidin.</span><span class="sxs-lookup"><span data-stu-id="9a110-115">Open a terminal and navigate to the _working\\_ folder.</span></span>

## <a name="create-a-template-pack-project"></a><span data-ttu-id="9a110-116">Şablon paketi projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="9a110-116">Create a template pack project</span></span>

<span data-ttu-id="9a110-117">Bir şablon paketi, bir dosyada paketlenmiş bir veya daha fazla şablondur.</span><span class="sxs-lookup"><span data-stu-id="9a110-117">A template pack is one or more templates packaged into a file.</span></span> <span data-ttu-id="9a110-118">Bir paketi yüklediğinizde veya kaldırdığınızda, paketin içerdiği tüm şablonlar sırasıyla eklenir veya kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="9a110-118">When you install or uninstall a pack, all templates contained in the pack are added or removed, respectively.</span></span> <span data-ttu-id="9a110-119">Bu öğretici serisinin önceki kısımları yalnızca bireysel şablonlarla birlikte çalışmıştır.</span><span class="sxs-lookup"><span data-stu-id="9a110-119">The previous parts of this tutorial series only worked with individual templates.</span></span> <span data-ttu-id="9a110-120">Paketlenmiş olmayan bir şablonu paylaşmak için, şablon klasörünü kopyalamanız ve bu klasör aracılığıyla kurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9a110-120">To share a non-packed template, you have to copy the template folder and install via that folder.</span></span> <span data-ttu-id="9a110-121">Bir şablon paketi içinde birden fazla şablon olabileceğinden ve tek bir dosya olduğundan, paylaşma daha kolay olur.</span><span class="sxs-lookup"><span data-stu-id="9a110-121">Because a template pack can have more than one template in it, and is a single file, sharing is easier.</span></span>

<span data-ttu-id="9a110-122">Şablon paketleri, bir NuGet paketi (_. nupkg_) dosyası tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="9a110-122">Template packs are represented by a NuGet package (_.nupkg_) file.</span></span> <span data-ttu-id="9a110-123">Tüm NuGet paketleri gibi, şablon paketini bir NuGet akışına de yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a110-123">And, like any NuGet package, you can upload the template pack to a NuGet feed.</span></span> <span data-ttu-id="9a110-124">`dotnet new -i`Komut, bir NuGet paketi akışından şablon paketi yüklemeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="9a110-124">The `dotnet new -i` command supports installing template pack from a NuGet package feed.</span></span> <span data-ttu-id="9a110-125">Ayrıca, bir _. nupkg_ dosyasından doğrudan bir şablon paketi de yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a110-125">Additionally, you can install a template pack from a _.nupkg_ file directly.</span></span>

<span data-ttu-id="9a110-126">Normalde, kod derlemek ve bir ikili oluşturmak için C# proje dosyası kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="9a110-126">Normally you use a C# project file to compile code and produce a binary.</span></span> <span data-ttu-id="9a110-127">Ancak, proje bir şablon paketi oluşturmak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9a110-127">However, the project can also be used to generate a template pack.</span></span> <span data-ttu-id="9a110-128">_. Csproj_ ayarlarını değiştirerek, bu kodun herhangi bir kodu derlemesine engel olabilir ve bunun yerine şablonlarınızın tüm varlıklarını kaynak olarak dahil edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a110-128">By changing the settings of the _.csproj_, you can prevent it from compiling any code and instead include all the assets of your templates as resources.</span></span> <span data-ttu-id="9a110-129">Bu proje oluşturulduğunda, bir şablon paketi NuGet paketi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9a110-129">When this project is built, it produces a template pack NuGet package.</span></span>

<span data-ttu-id="9a110-130">Oluşturacağınız paket, daha önce oluşturulan [öğe şablonunu](cli-templates-create-item-template.md) ve [paket şablonunu](cli-templates-create-project-template.md) içerir.</span><span class="sxs-lookup"><span data-stu-id="9a110-130">The pack you'll create will include the [item template](cli-templates-create-item-template.md) and [package template](cli-templates-create-project-template.md) previously created.</span></span> <span data-ttu-id="9a110-131">İki şablonu _working\templates \\_ klasörüne grupladığımızda, _. csproj_ dosyası için _çalışma_ klasörünü kullanabiliriz.</span><span class="sxs-lookup"><span data-stu-id="9a110-131">Because we grouped the two templates into the _working\templates\\_ folder, we can use the _working_ folder for the _.csproj_ file.</span></span>

<span data-ttu-id="9a110-132">Terminalinizde _çalışma_ klasörüne gidin.</span><span class="sxs-lookup"><span data-stu-id="9a110-132">In your terminal, navigate to the _working_ folder.</span></span> <span data-ttu-id="9a110-133">Yeni bir proje oluşturun ve adı `templatepack` ve çıkış klasörünü geçerli klasöre ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9a110-133">Create a new project and set the name to `templatepack` and the output folder to the current folder.</span></span>

```dotnetcli
dotnet new console -n templatepack -o .
```

<span data-ttu-id="9a110-134">`-n`Parametresi _. csproj_ dosya adını _templatepack. csproj_ olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9a110-134">The `-n` parameter sets the _.csproj_ filename to _templatepack.csproj_.</span></span> <span data-ttu-id="9a110-135">`-o`Parametresi, geçerli dizindeki dosyaları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9a110-135">The `-o` parameter creates the files in the current directory.</span></span> <span data-ttu-id="9a110-136">Aşağıdaki çıktıya benzer bir sonuç görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9a110-136">You should see a result similar to the following output.</span></span>

```console
The template "Console Application" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on .\templatepack.csproj...
  Restore completed in 52.38 ms for C:\working\templatepack.csproj.

Restore succeeded.
```

<span data-ttu-id="9a110-137">Ardından, en sevdiğiniz düzenleyicide _templatepack. csproj_ dosyasını açın ve IÇERIĞI aşağıdaki XML ile değiştirin:</span><span class="sxs-lookup"><span data-stu-id="9a110-137">Next, open the _templatepack.csproj_ file in your favorite editor and replace the content with the following XML:</span></span>

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
    <NoWarn>$(NoWarn);NU5128</NoWarn>
  </PropertyGroup>

  <ItemGroup>
    <Content Include="templates\**\*" Exclude="templates\**\bin\**;templates\**\obj\**" />
    <Compile Remove="**\*" />
  </ItemGroup>

</Project>
```

<span data-ttu-id="9a110-138">`<PropertyGroup>`YUKARıDAKI XML 'deki ayarlar üç gruba bölünmüştür.</span><span class="sxs-lookup"><span data-stu-id="9a110-138">The `<PropertyGroup>` settings in the XML above is broken into three groups.</span></span> <span data-ttu-id="9a110-139">İlk grup, bir NuGet paketi için gereken özelliklerle ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="9a110-139">The first group deals with properties required for a NuGet package.</span></span> <span data-ttu-id="9a110-140">Bu üç `<Package*>` ayar, bir NuGet akışında paketinizi tanımlamak Için NuGet paket özellikleriyle birlikte olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9a110-140">The three `<Package*>` settings have to do with the NuGet package properties to identify your package on a NuGet feed.</span></span> <span data-ttu-id="9a110-141">Özellikle `<PackageId>` değer, şablon paketini dizin yolu yerine tek bir adla kaldırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9a110-141">Specifically the `<PackageId>` value is used to uninstall the template pack with a single name instead of a directory path.</span></span> <span data-ttu-id="9a110-142">Ayrıca, bir NuGet akışından şablon paketini yüklemek için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9a110-142">It can also be used to install the template pack from a NuGet feed.</span></span> <span data-ttu-id="9a110-143">Ve gibi geri kalan ayarlar `<Title>` , `<PackageTags>` NuGet akışında görüntülenecek meta verilerle birlikte olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9a110-143">The remaining settings such as `<Title>` and `<PackageTags>` have to do with metadata displayed on the NuGet feed.</span></span> <span data-ttu-id="9a110-144">NuGet ayarları hakkında daha fazla bilgi için bkz. [NuGet ve MSBuild özellikleri](/nuget/reference/msbuild-targets).</span><span class="sxs-lookup"><span data-stu-id="9a110-144">For more information about NuGet settings, see [NuGet and MSBuild properties](/nuget/reference/msbuild-targets).</span></span>

<span data-ttu-id="9a110-145">`<TargetFramework>`Projeyi derlemek ve paketetmek için paket komutunu çalıştırdığınızda MSBuild 'in düzgün çalışması için ayar ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9a110-145">The `<TargetFramework>` setting must be set so that MSBuild will run properly when you run the pack command to compile and pack the project.</span></span>

<span data-ttu-id="9a110-146">Sonraki üç ayar, projeyi, oluşturulduğu zaman NuGet paketindeki uygun klasöre dahil etmek için doğru şekilde yapılandırmaya yönelik olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9a110-146">The next three settings have to do with configuring the project correctly to include the templates in the appropriate folder in the NuGet pack when it's created.</span></span>

<span data-ttu-id="9a110-147">Son ayar, şablon paketi projelerine uygulanan bir uyarı iletisini bastırır.</span><span class="sxs-lookup"><span data-stu-id="9a110-147">The last setting suppresses a warning message that doesn't apply to template pack projects.</span></span>

<span data-ttu-id="9a110-148">`<ItemGroup>`İki ayar içerir.</span><span class="sxs-lookup"><span data-stu-id="9a110-148">The `<ItemGroup>` contains two settings.</span></span> <span data-ttu-id="9a110-149">İlk olarak, `<Content>` ayar _Şablonlar_ klasöründeki her şeyi içerik olarak içerir.</span><span class="sxs-lookup"><span data-stu-id="9a110-149">First, the `<Content>` setting includes everything in the _templates_ folder as content.</span></span> <span data-ttu-id="9a110-150">Ayrıca, derlenmiş kodların (şablonlarınızı test etmeniz ve derlediğiniz) dahil edilmesini engellemek için herhangi bir _bin_ klasörünü veya _obj_ klasörünü dışarıda bırakmak üzere ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="9a110-150">It's also set to exclude any _bin_ folder or _obj_ folder to prevent any compiled code (if you tested and compiled your templates) from being included.</span></span> <span data-ttu-id="9a110-151">İkincisi, `<Compile>` ayar tüm kod dosyalarını nerede bulunduklarında bağımsız olarak derlemeden dışlar.</span><span class="sxs-lookup"><span data-stu-id="9a110-151">Second, the `<Compile>` setting excludes all code files from compiling no matter where they're located.</span></span> <span data-ttu-id="9a110-152">Bu ayar, şablon paketi oluşturmak için kullanılan projenin _Şablonlar_ klasörü hiyerarşisindeki kodu derlemeye çalışmamasını engeller.</span><span class="sxs-lookup"><span data-stu-id="9a110-152">This setting prevents the project being used to create a template pack from trying to compile the code in the _templates_ folder hierarchy.</span></span>

## <a name="build-and-install"></a><span data-ttu-id="9a110-153">Oluşturma ve yüklemeyi</span><span class="sxs-lookup"><span data-stu-id="9a110-153">Build and install</span></span>

<span data-ttu-id="9a110-154">Bu dosyayı kaydedin ve ardından paket komutunu çalıştırın</span><span class="sxs-lookup"><span data-stu-id="9a110-154">Save this file and then run the pack command</span></span>

```dotnetcli
dotnet pack
```

<span data-ttu-id="9a110-155">Bu komut, projenizi derler ve bu, bir NuGet paketi oluşturmak için _Working\bin\debug_ klasörü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9a110-155">This command will build your project and create a NuGet package in This should be the _working\bin\Debug_ folder.</span></span>

```dotnetcli
dotnet pack
```

```console
Microsoft (R) Build Engine version 16.8.0+126527ff1 for .NET
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 123.86 ms for C:\working\templatepack.csproj.

  templatepack -> C:\working\bin\Debug\netstandard2.0\templatepack.dll
  Successfully created package 'C:\working\bin\Debug\AdatumCorporation.Utility.Templates.1.0.0.nupkg'.
```

<span data-ttu-id="9a110-156">Sonra, komutuyla şablon paketi dosyasını yükler `dotnet new -i PATH_TO_NUPKG_FILE` .</span><span class="sxs-lookup"><span data-stu-id="9a110-156">Next, install the template pack file with the `dotnet new -i PATH_TO_NUPKG_FILE` command.</span></span>

```console
C:\working> dotnet new -i C:\working\bin\Debug\AdatumCorporation.Utility.Templates.1.0.0.nupkg
Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.

... cut to save space ...

Templates                                         Short Name               Language          Tags
--------------------------------------------      -------------------      ------------      ----------------------
Example templates: string extensions              stringext                [C#]              Common/Code
Console Application                               console                  [C#], F#, VB      Common/Console
Example templates: async project                  consoleasync             [C#]              Common/Console/C#9
Class library                                     classlib                 [C#], F#, VB      Common/Library
```

<span data-ttu-id="9a110-157">NuGet paketini bir NuGet akışına yüklediyseniz, `dotnet new -i PACKAGEID` `PACKAGEID` `<PackageId>` _. csproj_ dosyasındaki ayarla aynı olan komutunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a110-157">If you uploaded the NuGet package to a NuGet feed, you can use the `dotnet new -i PACKAGEID` command where `PACKAGEID` is the same as the `<PackageId>` setting from the _.csproj_ file.</span></span> <span data-ttu-id="9a110-158">Bu paket KIMLIĞI, NuGet paket tanımlayıcısı ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="9a110-158">This package ID is the same as the NuGet package identifier.</span></span>

## <a name="uninstall-the-template-pack"></a><span data-ttu-id="9a110-159">Şablon paketini kaldırma</span><span class="sxs-lookup"><span data-stu-id="9a110-159">Uninstall the template pack</span></span>

<span data-ttu-id="9a110-160">Şablon paketini, _. nupkg_ dosyasıyla doğrudan veya NuGet akışı ile nasıl yükletiğinize bakılmaksızın, bir şablon paketinin kaldırılması aynı olur.</span><span class="sxs-lookup"><span data-stu-id="9a110-160">No matter how you installed the template pack, either with the _.nupkg_ file directly or by NuGet feed, removing a template pack is the same.</span></span> <span data-ttu-id="9a110-161">Kaldırmak istediğiniz `<PackageId>` şablonun öğesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="9a110-161">Use the `<PackageId>` of the template you want to uninstall.</span></span> <span data-ttu-id="9a110-162">Komutunu çalıştırarak yüklenen şablonların bir listesini alabilirsiniz `dotnet new -u` .</span><span class="sxs-lookup"><span data-stu-id="9a110-162">You can get a list of templates that are installed by running the `dotnet new -u` command.</span></span>

```dotnetcli
dotnet new -u
```

```console
Template Instantiation Commands for .NET Core CLI

Currently installed items:
  Microsoft.DotNet.Common.ProjectTemplates.2.2
    Details:
      NuGetPackageId: Microsoft.DotNet.Common.ProjectTemplates.2.2
      Version: 1.0.2-beta4
      Author: Microsoft
    Templates:
      Class library (classlib) C#
      Class library (classlib) F#
      Class library (classlib) VB
      Console Application (console) C#
      Console Application (console) F#
      Console Application (console) VB
    Uninstall Command:
      dotnet new -u Microsoft.DotNet.Common.ProjectTemplates.2.2

... cut to save space ...

  AdatumCorporation.Utility.Templates
    Details:
      NuGetPackageId: AdatumCorporation.Utility.Templates
      Version: 1.0.0
      Author: Me
    Templates:
      Example templates: async project (consoleasync) C#
      Example templates: string extensions (stringext) C#
    Uninstall Command:
      dotnet new -u AdatumCorporation.Utility.Templates
```

<span data-ttu-id="9a110-163">`dotnet new -u AdatumCorporation.Utility.Templates`Şablonu kaldırmak için ' i çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9a110-163">Run `dotnet new -u AdatumCorporation.Utility.Templates` to uninstall the template.</span></span> <span data-ttu-id="9a110-164">`dotnet new`Komutu, daha önce yüklediğiniz şablonları atlamanızı gerektiren yardım bilgilerini çıktı olarak alırsınız.</span><span class="sxs-lookup"><span data-stu-id="9a110-164">The `dotnet new` command will output help information that should omit the templates you previously installed.</span></span>

<span data-ttu-id="9a110-165">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="9a110-165">Congratulations!</span></span> <span data-ttu-id="9a110-166">bir şablon paketi yüklediniz ve kaldırdık.</span><span class="sxs-lookup"><span data-stu-id="9a110-166">you've installed and uninstalled a template pack.</span></span>

## <a name="next-steps"></a><span data-ttu-id="9a110-167">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="9a110-167">Next steps</span></span>

<span data-ttu-id="9a110-168">Zaten öğrendiğiniz şablonlar hakkında daha fazla bilgi edinmek için, [DotNet yeni makale Için özel şablonlar](../tools/custom-templates.md) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="9a110-168">To learn more about templates, most of which you've already learned, see the [Custom templates for dotnet new](../tools/custom-templates.md) article.</span></span>

* [<span data-ttu-id="9a110-169">DotNet/şablon oluşturma GitHub deposu wiki</span><span class="sxs-lookup"><span data-stu-id="9a110-169">dotnet/templating GitHub repo Wiki</span></span>](https://github.com/dotnet/templating/wiki)
* [<span data-ttu-id="9a110-170">DotNet/DotNet-şablon-örnek GitHub deposu</span><span class="sxs-lookup"><span data-stu-id="9a110-170">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
* [<span data-ttu-id="9a110-171">JSON Şema deposundaki şemada *template.js*</span><span class="sxs-lookup"><span data-stu-id="9a110-171">*template.json* schema at the JSON Schema Store</span></span>](http://json.schemastore.org/template)
