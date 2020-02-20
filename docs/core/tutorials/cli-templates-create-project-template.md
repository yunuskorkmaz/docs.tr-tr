---
title: DotNet New için bir proje şablonu oluşturun
description: DotNet New komutu için bir proje şablonu oluşturmayı öğrenin.
author: thraka
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: f53f4037f832265a35f65bf2e5096c7e5a37bcf1
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503527"
---
# <a name="tutorial-create-a-project-template"></a><span data-ttu-id="3403b-103">Öğretici: proje şablonu oluşturma</span><span class="sxs-lookup"><span data-stu-id="3403b-103">Tutorial: Create a project template</span></span>

<span data-ttu-id="3403b-104">.NET Core ile projeler, dosyalar, hatta kaynaklar üreten şablonlar oluşturabilir ve dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3403b-104">With .NET Core, you can create and deploy templates that generate projects, files, even resources.</span></span> <span data-ttu-id="3403b-105">Bu öğretici, `dotnet new` komutuyla kullanılmak üzere şablonlar oluşturmayı, yüklemeyi ve kaldırmayı öğretir.</span><span class="sxs-lookup"><span data-stu-id="3403b-105">This tutorial is part two of a series that teaches you how to create, install, and uninstall, templates for use with the `dotnet new` command.</span></span>

<span data-ttu-id="3403b-106">Serinin bu bölümünde şunları nasıl yapacağınızı öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="3403b-106">In this part of the series you'll learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="3403b-107">Proje şablonunun kaynaklarını oluşturma</span><span class="sxs-lookup"><span data-stu-id="3403b-107">Create the resources of a project template</span></span>
> * <span data-ttu-id="3403b-108">Şablon yapılandırma klasörünü ve dosyasını oluşturma</span><span class="sxs-lookup"><span data-stu-id="3403b-108">Create the template config folder and file</span></span>
> * <span data-ttu-id="3403b-109">Dosya yolundan şablon yükler</span><span class="sxs-lookup"><span data-stu-id="3403b-109">Install a template from a file path</span></span>
> * <span data-ttu-id="3403b-110">Bir öğe şablonunu test etme</span><span class="sxs-lookup"><span data-stu-id="3403b-110">Test an item template</span></span>
> * <span data-ttu-id="3403b-111">Öğe şablonunu kaldırma</span><span class="sxs-lookup"><span data-stu-id="3403b-111">Uninstall an item template</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3403b-112">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="3403b-112">Prerequisites</span></span>

* <span data-ttu-id="3403b-113">Bu öğretici serisinin [1. bölümünü](cli-templates-create-item-template.md) doldurun.</span><span class="sxs-lookup"><span data-stu-id="3403b-113">Complete [part 1](cli-templates-create-item-template.md) of this tutorial series.</span></span>
* <span data-ttu-id="3403b-114">Bir Terminal açın ve _working\templates_ klasörüne gidin.</span><span class="sxs-lookup"><span data-stu-id="3403b-114">Open a terminal and navigate to the _working\templates_ folder.</span></span>

## <a name="create-a-project-template"></a><span data-ttu-id="3403b-115">Proje şablonu oluşturma</span><span class="sxs-lookup"><span data-stu-id="3403b-115">Create a project template</span></span>

<span data-ttu-id="3403b-116">Proje şablonları, kullanıcıların çalışan bir kod kümesiyle başlamasını kolaylaştıran, çalıştırmaya yönelik olarak çalışan projeler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3403b-116">Project templates produce ready-to-run projects that make it easy for users to start with a working set of code.</span></span> <span data-ttu-id="3403b-117">.NET Core, konsol uygulaması veya sınıf kitaplığı gibi bazı proje şablonları içerir.</span><span class="sxs-lookup"><span data-stu-id="3403b-117">.NET Core includes a few project templates such as a console application or a class library.</span></span> <span data-ttu-id="3403b-118">Bu örnekte, 8,0 sağlayan C# ve bir `async main` giriş noktası üreten yeni bir konsol projesi oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="3403b-118">In this example, you'll create a new console project that enables C# 8.0 and produces an `async main` entry point.</span></span>

<span data-ttu-id="3403b-119">Terminalinizde, _working\templates_ klasörüne gidin ve _consoleasync_adlı yeni bir alt klasör oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3403b-119">In your terminal, navigate to the _working\templates_ folder and create a new subfolder named _consoleasync_.</span></span> <span data-ttu-id="3403b-120">Standart konsol uygulamasını oluşturmak için alt klasörü girin ve `dotnet new console` çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="3403b-120">Enter the subfolder and run `dotnet new console` to generate the standard console application.</span></span> <span data-ttu-id="3403b-121">Bu şablon tarafından oluşturulan dosyaları düzenleyerek yeni bir şablon oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3403b-121">You'll be editing the files produced by this template to create a new template.</span></span>

```console
working
└───templates
    └───consoleasync
            consoleasync.csproj
            Program.cs
```

## <a name="modify-programcs"></a><span data-ttu-id="3403b-122">Program.cs Değiştir</span><span class="sxs-lookup"><span data-stu-id="3403b-122">Modify Program.cs</span></span>

<span data-ttu-id="3403b-123">_Program.cs_ dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="3403b-123">Open up the _program.cs_ file.</span></span> <span data-ttu-id="3403b-124">Konsol projesi zaman uyumsuz bir giriş noktası kullanmaz, bu nedenle bunu ekleyelim.</span><span class="sxs-lookup"><span data-stu-id="3403b-124">The console project doesn't use an asynchronous entry point, so let's add that.</span></span> <span data-ttu-id="3403b-125">Kodunuzu aşağıdaki şekilde değiştirin ve dosyayı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="3403b-125">Change your code to the following and save the file.</span></span>

```csharp
using System;
using System.Threading.Tasks;

namespace consoleasync
{
    class Program
    {
        static async Task Main(string[] args)
        {
            await Console.Out.WriteAsync("Hello World with C# 8.0!");
        }
    }
}
```

## <a name="modify-consoleasynccsproj"></a><span data-ttu-id="3403b-126">Consoleasync. csproj öğesini Değiştir</span><span class="sxs-lookup"><span data-stu-id="3403b-126">Modify consoleasync.csproj</span></span>

<span data-ttu-id="3403b-127">Projenin 8,0 sürümünü kullandığı C# dil sürümünü güncelleştirelim.</span><span class="sxs-lookup"><span data-stu-id="3403b-127">Let's update the C# language version the project uses to version 8.0.</span></span> <span data-ttu-id="3403b-128">_Consoleasync. csproj_ dosyasını düzenleyin ve `<PropertyGroup>` düğümüne `<LangVersion>` ayarını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3403b-128">Edit the _consoleasync.csproj_ file and add the `<LangVersion>` setting to a `<PropertyGroup>` node.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.2</TargetFramework>

    <LangVersion>8.0</LangVersion>

  </PropertyGroup>
  
</Project>
```

## <a name="build-the-project"></a><span data-ttu-id="3403b-129">Projeyi derleme</span><span class="sxs-lookup"><span data-stu-id="3403b-129">Build the project</span></span>

<span data-ttu-id="3403b-130">Bir proje şablonunu tamamlamadan önce, derlendiğinden ve düzgün çalıştığından emin olmak için test etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3403b-130">Before you complete a project template, you should test it to make sure it compiles and runs correctly.</span></span>

<span data-ttu-id="3403b-131">Terminalinizde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="3403b-131">In your terminal, run the following command.</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="3403b-132">Aşağıdaki çıktıyı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="3403b-132">You get the following output.</span></span>

```console
Hello World with C# 8.0!
```

<span data-ttu-id="3403b-133">`dotnet run`kullanarak oluşturulan _obj_ ve _bin_ klasörlerini silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3403b-133">You can delete the _obj_ and _bin_ folders created by using `dotnet run`.</span></span> <span data-ttu-id="3403b-134">Bu dosyaların silinmesi, şablonunuzun yalnızca şablonlarınız ile ilgili dosyaları ve bir yapı eylemi sonucu olan dosyaları içerip içermemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="3403b-134">Deleting these files ensures your template only includes the files related to your template and not any files that result of a build action.</span></span>

<span data-ttu-id="3403b-135">Artık oluşturulan şablonun içeriğine sahip olduğunuza göre, şablonun kök klasöründe şablon yapılandırmasını oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3403b-135">Now that you have the content of the template created, you need to create the template config at the root folder of the template.</span></span>

## <a name="create-the-template-config"></a><span data-ttu-id="3403b-136">Şablon yapılandırması oluşturma</span><span class="sxs-lookup"><span data-stu-id="3403b-136">Create the template config</span></span>

<span data-ttu-id="3403b-137">Şablonlar, .NET Core 'da şablonunuzun kökünde bulunan özel bir klasör ve yapılandırma dosyası tarafından tanınır.</span><span class="sxs-lookup"><span data-stu-id="3403b-137">Templates are recognized in .NET Core by a special folder and config file that exist at the root of your template.</span></span> <span data-ttu-id="3403b-138">Bu öğreticide, şablon klasörünüz _working\templates\consoleasync_adresinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="3403b-138">In this tutorial, your template folder is located at _working\templates\consoleasync_.</span></span>

<span data-ttu-id="3403b-139">Bir şablon oluşturduğunuzda, şablon klasöründeki tüm dosyalar ve klasörler, özel yapılandırma klasörü hariç, şablonun bir parçası olarak dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="3403b-139">When you create a template, all files and folders in the template folder are included as part of the template except for the special config folder.</span></span> <span data-ttu-id="3403b-140">Bu yapılandırma klasörü _. Template. config_olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="3403b-140">This config folder is named _.template.config_.</span></span>

<span data-ttu-id="3403b-141">İlk olarak, _. Template. config_adlı yeni bir alt klasör oluşturun, bunu girin.</span><span class="sxs-lookup"><span data-stu-id="3403b-141">First, create a new subfolder named _.template.config_, enter it.</span></span> <span data-ttu-id="3403b-142">Ardından, _Template. JSON_adlı yeni bir dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3403b-142">Then, create a new file named _template.json_.</span></span> <span data-ttu-id="3403b-143">Klasör yapınız şöyle görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="3403b-143">Your folder structure should look like this.</span></span>

```console
working
└───templates
    └───consoleasync
        └───.template.config
                template.json
```

<span data-ttu-id="3403b-144">En sevdiğiniz metin düzenleyicinizle _Template. JSON_ ' i açın ve aşağıdaki JSON kodunu yapıştırın ve kaydedin.</span><span class="sxs-lookup"><span data-stu-id="3403b-144">Open the _template.json_ with your favorite text editor and paste in the following json code and save it.</span></span>

```json
{
  "$schema": "http://json.schemastore.org/template",
  "author": "Me",
  "classifications": [ "Common", "Console", "C#8" ],
  "identity": "ExampleTemplate.AsyncProject",
  "name": "Example templates: async project",
  "shortName": "consoleasync",
  "tags": {
    "language": "C#",
    "type": "project"
  }
}
```

<span data-ttu-id="3403b-145">Bu yapılandırma dosyası şablonunuz için tüm ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="3403b-145">This config file contains all of the settings for your template.</span></span> <span data-ttu-id="3403b-146">`name` ve `shortName` gibi temel ayarları görebilir, ancak `project`olarak ayarlanmış bir `tags/type` değeri de vardır.</span><span class="sxs-lookup"><span data-stu-id="3403b-146">You can see the basic settings such as `name` and `shortName` but also there's a `tags/type` value that's set to `project`.</span></span> <span data-ttu-id="3403b-147">Bu, şablonunuzu bir proje şablonu olarak belirler.</span><span class="sxs-lookup"><span data-stu-id="3403b-147">This designates your template as a project template.</span></span> <span data-ttu-id="3403b-148">Oluşturduğunuz şablon türü üzerinde hiçbir kısıtlama yoktur.</span><span class="sxs-lookup"><span data-stu-id="3403b-148">There's no restriction on the type of template you create.</span></span> <span data-ttu-id="3403b-149">`item` ve `project` değerleri, .NET Core 'un arama yapmakta oldukları şablonun türünü kolayca filtreleyebilmesi için .NET Core 'un önerdiği yaygın adlardır.</span><span class="sxs-lookup"><span data-stu-id="3403b-149">The `item` and `project` values are common names that .NET Core recommends so that users can easily filter the type of template they're searching for.</span></span>

<span data-ttu-id="3403b-150">`classifications` öğesi, `dotnet new` çalıştırdığınız ve şablonların bir listesini alacağınız zaman gördüğünüz **Etiketler** sütununu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3403b-150">The `classifications` item represents the **tags** column you see when you run `dotnet new` and get a list of templates.</span></span> <span data-ttu-id="3403b-151">Kullanıcılar ayrıca sınıflandırma etiketlerine göre arama yapabilir.</span><span class="sxs-lookup"><span data-stu-id="3403b-151">Users can also search based on classification tags.</span></span> <span data-ttu-id="3403b-152">JSON dosyasındaki `tags` özelliğini `classifications` Etiketler listesiyle karıştırmayın.</span><span class="sxs-lookup"><span data-stu-id="3403b-152">Don't confuse the `tags` property in the json file with the `classifications` tags list.</span></span> <span data-ttu-id="3403b-153">Benzer şekilde adlandırılan iki farklı şey vardır.</span><span class="sxs-lookup"><span data-stu-id="3403b-153">They're two different things unfortunately named similarly.</span></span> <span data-ttu-id="3403b-154">*Template. JSON* dosyasının tam şeması [JSON Şema deposunda](http://json.schemastore.org/template)bulunur.</span><span class="sxs-lookup"><span data-stu-id="3403b-154">The full schema for the *template.json* file is found at the [JSON Schema Store](http://json.schemastore.org/template).</span></span> <span data-ttu-id="3403b-155">*Template. JSON* dosyası hakkında daha fazla bilgi için bkz. [DotNet şablon oluşturma wiki](https://github.com/dotnet/templating/wiki).</span><span class="sxs-lookup"><span data-stu-id="3403b-155">For more information about the *template.json* file, see the [dotnet templating wiki](https://github.com/dotnet/templating/wiki).</span></span>

<span data-ttu-id="3403b-156">Artık geçerli bir _. Template. config/Template. JSON_ dosyanız olduğuna göre, şablonunuz yüklenmeye hazırdır.</span><span class="sxs-lookup"><span data-stu-id="3403b-156">Now that you have a valid _.template.config/template.json_ file, your template is ready to be installed.</span></span> <span data-ttu-id="3403b-157">Şablonu yüklemeden önce, _küme_ veya _obj_ klasörleri gibi şablonunuzda yer almasını istemediğiniz ek dosya klasörlerini ve dosyalarını sildiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="3403b-157">Before you install the template, make sure that you delete any extra files folders and files you don't want included in your template, like the _bin_ or _obj_ folders.</span></span> <span data-ttu-id="3403b-158">Terminalinizde _consoleasync_ klasörüne gidin ve geçerli klasörde bulunan şablonu yüklemek için `dotnet new -i .\` çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="3403b-158">In your terminal, navigate to the _consoleasync_ folder and run `dotnet new -i .\` to install the template located at the current folder.</span></span> <span data-ttu-id="3403b-159">Linux veya macOS işletim sistemi kullanıyorsanız, eğik çizgi kullanın: `dotnet new -i ./`.</span><span class="sxs-lookup"><span data-stu-id="3403b-159">If you're using a Linux or macOS operating system, use a forward slash: `dotnet new -i ./`.</span></span>

<span data-ttu-id="3403b-160">Bu komut, yüklenmiş şablonların listesini verir ve bunları içermelidir.</span><span class="sxs-lookup"><span data-stu-id="3403b-160">This command outputs the list of templates installed, which should include yours.</span></span>

```dotnetcli
dotnet new -i .\
```

<span data-ttu-id="3403b-161">Aşağıdakine benzer bir çıktı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="3403b-161">You get output similar to the following.</span></span>

```console
Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.

... cut to save space ...

Templates                                         Short Name            Language          Tags
-------------------------------------------------------------------------------------------------------------------------------
Console Application                               console               [C#], F#, VB      Common/Console
Example templates: async project                  consoleasync          [C#]              Common/Console/C#8
Class library                                     classlib              [C#], F#, VB      Common/Library
WPF Application                                   wpf                   [C#], VB          Common/WPF
Windows Forms (WinForms) Application              winforms              [C#], VB          Common/WinForms
Worker Service                                    worker                [C#]              Common/Worker/Web
```

### <a name="test-the-project-template"></a><span data-ttu-id="3403b-162">Proje şablonunu test etme</span><span class="sxs-lookup"><span data-stu-id="3403b-162">Test the project template</span></span>

<span data-ttu-id="3403b-163">Artık bir öğe şablonu yükleolduğunuza göre, test edin.</span><span class="sxs-lookup"><span data-stu-id="3403b-163">Now that you have an item template installed, test it.</span></span>

1. <span data-ttu-id="3403b-164">_Test_ klasörüne git</span><span class="sxs-lookup"><span data-stu-id="3403b-164">Navigate to the _test_ folder</span></span>

1. <span data-ttu-id="3403b-165">`dotnet run` komutuyla kolayca test edebileceğiniz, çalışan bir proje üreten aşağıdaki komutla yeni bir konsol uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3403b-165">Create a new console application with the following command which generates a working project you can easily test with the `dotnet run` command.</span></span>

    ```dotnetcli
    dotnet new consoleasync
    ```

    <span data-ttu-id="3403b-166">Aşağıdaki çıktıyı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="3403b-166">You get the following output.</span></span>

    ```console
    The template "Example templates: async project" was created successfully.
    ```

1. <span data-ttu-id="3403b-167">Aşağıdaki komutu kullanarak projeyi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="3403b-167">Run the project using the following command.</span></span>

    ```dotnetcli
    dotnet run
    ```

    <span data-ttu-id="3403b-168">Aşağıdaki çıktıyı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="3403b-168">You get the following output.</span></span>

    ```console
    Hello World with C# 8.0!
    ```

<span data-ttu-id="3403b-169">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="3403b-169">Congratulations!</span></span> <span data-ttu-id="3403b-170">.NET Core ile bir proje şablonu oluşturdunuz ve dağıttıysanız.</span><span class="sxs-lookup"><span data-stu-id="3403b-170">You created and deployed a project template with .NET Core.</span></span> <span data-ttu-id="3403b-171">Bu öğretici serisinin bir sonraki kısmına hazırlanın, oluşturduğunuz şablonu kaldırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3403b-171">In preparation for the next part of this tutorial series, you must uninstall the template you created.</span></span> <span data-ttu-id="3403b-172">Tüm dosyaları da _Test_ klasöründen sildiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="3403b-172">Make sure to delete all files from the _test_ folder too.</span></span> <span data-ttu-id="3403b-173">Bu, Bu öğreticinin bir sonraki ana kısmına yönelik temiz bir duruma geri dönebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3403b-173">This will get you back to a clean state ready for the next major section of this tutorial.</span></span>

### <a name="uninstall-the-template"></a><span data-ttu-id="3403b-174">Şablonu kaldırma</span><span class="sxs-lookup"><span data-stu-id="3403b-174">Uninstall the template</span></span>

<span data-ttu-id="3403b-175">Şablonu bir dosya yolu kullanarak yükletiğinden, **mutlak** dosya yoluyla kaldırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3403b-175">Because you installed the template by using a file path, you must uninstall it with the **absolute** file path.</span></span> <span data-ttu-id="3403b-176">`dotnet new -u` komutunu çalıştırarak, yüklenmiş şablonların listesini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3403b-176">You can see a list of templates installed by running the `dotnet new -u` command.</span></span> <span data-ttu-id="3403b-177">Şablonunuzun son listelenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="3403b-177">Your template should be listed last.</span></span> <span data-ttu-id="3403b-178">`dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` komutuyla şablonunuzu kaldırmak için listelenen yolu kullanın.</span><span class="sxs-lookup"><span data-stu-id="3403b-178">Use the path listed to uninstall your template with the `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` command.</span></span>

```dotnetcli
dotnet new -u
```

<span data-ttu-id="3403b-179">Aşağıdakine benzer bir çıktı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="3403b-179">You get output similar to the following.</span></span>

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
  C:\working\templates\consoleasync
    Templates:
      Example templates: async project (consoleasync) C#
```

<span data-ttu-id="3403b-180">Bir şablonu kaldırmak için aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="3403b-180">To uninstall a template, run the following command.</span></span>

```dotnetcli
dotnet new -u C:\working\templates\consoleasync
```

## <a name="next-steps"></a><span data-ttu-id="3403b-181">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="3403b-181">Next steps</span></span>

<span data-ttu-id="3403b-182">Bu öğreticide bir proje şablonu oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="3403b-182">In this tutorial, you created a project template.</span></span> <span data-ttu-id="3403b-183">Hem öğe hem de proje şablonlarının kullanımı kolay bir dosyaya nasıl paketleyeceğinizi öğrenmek için, bu öğretici serisine devam edin.</span><span class="sxs-lookup"><span data-stu-id="3403b-183">To learn how to package both the item and project templates into an easy-to-use file, continue this tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3403b-184">Şablon paketi oluşturma</span><span class="sxs-lookup"><span data-stu-id="3403b-184">Create a template pack</span></span>](cli-templates-create-template-pack.md)
