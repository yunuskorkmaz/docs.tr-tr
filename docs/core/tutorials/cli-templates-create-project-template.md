---
title: dotnet yeni için bir proje şablonu oluşturma
description: dotnet yeni komutu için proje şablonu oluşturmayı öğrenin.
author: thraka
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: f53f4037f832265a35f65bf2e5096c7e5a37bcf1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503527"
---
# <a name="tutorial-create-a-project-template"></a><span data-ttu-id="48a13-103">Öğretici: Proje şablonu oluşturma</span><span class="sxs-lookup"><span data-stu-id="48a13-103">Tutorial: Create a project template</span></span>

<span data-ttu-id="48a13-104">.NET Core ile, projeler, dosyalar ve hatta kaynaklar oluşturan şablonlar oluşturabilir ve dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48a13-104">With .NET Core, you can create and deploy templates that generate projects, files, even resources.</span></span> <span data-ttu-id="48a13-105">Bu öğretici, `dotnet new` komutla birlikte kullanılmak üzere şablonoluşturma, yükleme ve kaldırma yı öğreten bir serinin ikinci bölümüdür.</span><span class="sxs-lookup"><span data-stu-id="48a13-105">This tutorial is part two of a series that teaches you how to create, install, and uninstall, templates for use with the `dotnet new` command.</span></span>

<span data-ttu-id="48a13-106">Serinin bu bölümünde nasıl öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="48a13-106">In this part of the series you'll learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="48a13-107">Proje şablonunun kaynaklarını oluşturma</span><span class="sxs-lookup"><span data-stu-id="48a13-107">Create the resources of a project template</span></span>
> * <span data-ttu-id="48a13-108">Şablon config klasörünü ve dosyasını oluşturma</span><span class="sxs-lookup"><span data-stu-id="48a13-108">Create the template config folder and file</span></span>
> * <span data-ttu-id="48a13-109">Dosya yolundan şablon yükleme</span><span class="sxs-lookup"><span data-stu-id="48a13-109">Install a template from a file path</span></span>
> * <span data-ttu-id="48a13-110">Öğe şablonu test edin</span><span class="sxs-lookup"><span data-stu-id="48a13-110">Test an item template</span></span>
> * <span data-ttu-id="48a13-111">Öğe şablonu kaldırma</span><span class="sxs-lookup"><span data-stu-id="48a13-111">Uninstall an item template</span></span>

## <a name="prerequisites"></a><span data-ttu-id="48a13-112">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="48a13-112">Prerequisites</span></span>

* <span data-ttu-id="48a13-113">Bu öğretici serisinin tam [bölüm 1.](cli-templates-create-item-template.md)</span><span class="sxs-lookup"><span data-stu-id="48a13-113">Complete [part 1](cli-templates-create-item-template.md) of this tutorial series.</span></span>
* <span data-ttu-id="48a13-114">Bir terminal açın ve _çalışma\şablonlar_ klasörüne gidin.</span><span class="sxs-lookup"><span data-stu-id="48a13-114">Open a terminal and navigate to the _working\templates_ folder.</span></span>

## <a name="create-a-project-template"></a><span data-ttu-id="48a13-115">Proje şablonu oluşturma</span><span class="sxs-lookup"><span data-stu-id="48a13-115">Create a project template</span></span>

<span data-ttu-id="48a13-116">Proje şablonları, kullanıcıların çalışan bir kod kümesiyle başlamasını kolaylaştıran çalışmaya hazır projeler üretir.</span><span class="sxs-lookup"><span data-stu-id="48a13-116">Project templates produce ready-to-run projects that make it easy for users to start with a working set of code.</span></span> <span data-ttu-id="48a13-117">.NET Core, konsol uygulaması veya sınıf kitaplığı gibi birkaç proje şablonu içerir.</span><span class="sxs-lookup"><span data-stu-id="48a13-117">.NET Core includes a few project templates such as a console application or a class library.</span></span> <span data-ttu-id="48a13-118">Bu örnekte, C# 8.0'ı etkinleştiren ve bir giriş `async main` noktası üreten yeni bir konsol projesi oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="48a13-118">In this example, you'll create a new console project that enables C# 8.0 and produces an `async main` entry point.</span></span>

<span data-ttu-id="48a13-119">Terminalinizde, _çalışma\şablonlar_ klasörüne gidin ve _consoleasync_adında yeni bir alt klasör oluşturun.</span><span class="sxs-lookup"><span data-stu-id="48a13-119">In your terminal, navigate to the _working\templates_ folder and create a new subfolder named _consoleasync_.</span></span> <span data-ttu-id="48a13-120">Alt klasörü girin `dotnet new console` ve standart konsol uygulamasını oluşturmak için çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="48a13-120">Enter the subfolder and run `dotnet new console` to generate the standard console application.</span></span> <span data-ttu-id="48a13-121">Yeni bir şablon oluşturmak için bu şablon tarafından üretilen dosyaları düzenlersiniz.</span><span class="sxs-lookup"><span data-stu-id="48a13-121">You'll be editing the files produced by this template to create a new template.</span></span>

```console
working
└───templates
    └───consoleasync
            consoleasync.csproj
            Program.cs
```

## <a name="modify-programcs"></a><span data-ttu-id="48a13-122">Program.cs değiştirin</span><span class="sxs-lookup"><span data-stu-id="48a13-122">Modify Program.cs</span></span>

<span data-ttu-id="48a13-123">_program.cs_ dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="48a13-123">Open up the _program.cs_ file.</span></span> <span data-ttu-id="48a13-124">Konsol projesi nde eşzamanlı giriş noktası yok, o yüzden bunu ekleyelim.</span><span class="sxs-lookup"><span data-stu-id="48a13-124">The console project doesn't use an asynchronous entry point, so let's add that.</span></span> <span data-ttu-id="48a13-125">Kodunuzu aşağıdakiyle değiştirin ve dosyayı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="48a13-125">Change your code to the following and save the file.</span></span>

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

## <a name="modify-consoleasynccsproj"></a><span data-ttu-id="48a13-126">consoleasync.csproj değiştir</span><span class="sxs-lookup"><span data-stu-id="48a13-126">Modify consoleasync.csproj</span></span>

<span data-ttu-id="48a13-127">Projenin kullandığı C# dil sürümünü sürüm 8.0 olarak güncelleyelim.</span><span class="sxs-lookup"><span data-stu-id="48a13-127">Let's update the C# language version the project uses to version 8.0.</span></span> <span data-ttu-id="48a13-128">_Consoleasync.csproj_ dosyasını edin `<LangVersion>` ve ayarı bir `<PropertyGroup>` düğüme ekleyin.</span><span class="sxs-lookup"><span data-stu-id="48a13-128">Edit the _consoleasync.csproj_ file and add the `<LangVersion>` setting to a `<PropertyGroup>` node.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.2</TargetFramework>

    <LangVersion>8.0</LangVersion>

  </PropertyGroup>
  
</Project>
```

## <a name="build-the-project"></a><span data-ttu-id="48a13-129">Projeyi derleme</span><span class="sxs-lookup"><span data-stu-id="48a13-129">Build the project</span></span>

<span data-ttu-id="48a13-130">Proje şablonu tamamlanmadan önce, doğru çalıştığından ve çalıştığından emin olmak için bu şablonu sınamalısınız.</span><span class="sxs-lookup"><span data-stu-id="48a13-130">Before you complete a project template, you should test it to make sure it compiles and runs correctly.</span></span>

<span data-ttu-id="48a13-131">Terminalinizde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="48a13-131">In your terminal, run the following command.</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="48a13-132">Aşağıdaki çıktıyı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="48a13-132">You get the following output.</span></span>

```console
Hello World with C# 8.0!
```

<span data-ttu-id="48a13-133">Kullanarak oluşturulan _obj_ ve _bin_ klasörlerini `dotnet run`silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48a13-133">You can delete the _obj_ and _bin_ folders created by using `dotnet run`.</span></span> <span data-ttu-id="48a13-134">Bu dosyaları silerken, şablonunuzun yalnızca şablonunuzla ilgili dosyaları içermesini ve bir yapı eyleminin sonucu olan dosyaları içermemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="48a13-134">Deleting these files ensures your template only includes the files related to your template and not any files that result of a build action.</span></span>

<span data-ttu-id="48a13-135">Oluşturulan şablonun içeriğine sahip olduğunuza göre, şablonun kök klasöründe şablon config'ini oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="48a13-135">Now that you have the content of the template created, you need to create the template config at the root folder of the template.</span></span>

## <a name="create-the-template-config"></a><span data-ttu-id="48a13-136">Şablon config oluşturma</span><span class="sxs-lookup"><span data-stu-id="48a13-136">Create the template config</span></span>

<span data-ttu-id="48a13-137">Şablonlar .NET Core'da şablonunuzun kökünde bulunan özel bir klasör ve config dosyası tarafından tanınır.</span><span class="sxs-lookup"><span data-stu-id="48a13-137">Templates are recognized in .NET Core by a special folder and config file that exist at the root of your template.</span></span> <span data-ttu-id="48a13-138">Bu öğreticide, şablon klasörünüz _çalışma\templates\consoleasync_adresinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="48a13-138">In this tutorial, your template folder is located at _working\templates\consoleasync_.</span></span>

<span data-ttu-id="48a13-139">Bir şablon oluşturduğunuzda, şablon klasöründeki tüm dosya ve klasörler özel config klasörü dışında şablonun bir parçası olarak dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="48a13-139">When you create a template, all files and folders in the template folder are included as part of the template except for the special config folder.</span></span> <span data-ttu-id="48a13-140">Bu config klasörü _.template.config_olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="48a13-140">This config folder is named _.template.config_.</span></span>

<span data-ttu-id="48a13-141">İlk olarak, _.template.config_adlı yeni bir alt klasör oluşturun, girin.</span><span class="sxs-lookup"><span data-stu-id="48a13-141">First, create a new subfolder named _.template.config_, enter it.</span></span> <span data-ttu-id="48a13-142">Ardından, _template.json_adında yeni bir dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="48a13-142">Then, create a new file named _template.json_.</span></span> <span data-ttu-id="48a13-143">Klasör yapınız şu şekilde görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="48a13-143">Your folder structure should look like this.</span></span>

```console
working
└───templates
    └───consoleasync
        └───.template.config
                template.json
```

<span data-ttu-id="48a13-144">En sevdiğiniz metin düzenleyicisi ile _template.json'u_ açın ve aşağıdaki json koduna yapıştırın ve kaydedin.</span><span class="sxs-lookup"><span data-stu-id="48a13-144">Open the _template.json_ with your favorite text editor and paste in the following json code and save it.</span></span>

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

<span data-ttu-id="48a13-145">Bu config dosyası, şablonunuzun tüm ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="48a13-145">This config file contains all of the settings for your template.</span></span> <span data-ttu-id="48a13-146">Temel ayarları görebilirsiniz `name` ve `shortName` aynı zamanda `tags/type` `project`'' için ayarlanmış bir değer de vardır.</span><span class="sxs-lookup"><span data-stu-id="48a13-146">You can see the basic settings such as `name` and `shortName` but also there's a `tags/type` value that's set to `project`.</span></span> <span data-ttu-id="48a13-147">Bu, şablonunuzu proje şablonu olarak belirtir.</span><span class="sxs-lookup"><span data-stu-id="48a13-147">This designates your template as a project template.</span></span> <span data-ttu-id="48a13-148">Oluşturduğunuz şablon türünde herhangi bir kısıtlama yoktur.</span><span class="sxs-lookup"><span data-stu-id="48a13-148">There's no restriction on the type of template you create.</span></span> <span data-ttu-id="48a13-149">Ve `item` `project` değerler, kullanıcıların aradıkları şablon türünü kolayca filtreleyebilmeleri için .NET Core'un önerdiği ortak adlardır.</span><span class="sxs-lookup"><span data-stu-id="48a13-149">The `item` and `project` values are common names that .NET Core recommends so that users can easily filter the type of template they're searching for.</span></span>

<span data-ttu-id="48a13-150">Öğe, `classifications` çalıştırdığınızda `dotnet new` ve şablonların listesini aldığınızda gördüğünüz **etiketler** sütununa temsil eder.</span><span class="sxs-lookup"><span data-stu-id="48a13-150">The `classifications` item represents the **tags** column you see when you run `dotnet new` and get a list of templates.</span></span> <span data-ttu-id="48a13-151">Kullanıcılar sınıflandırma etiketlerine göre de arama yapabilir.</span><span class="sxs-lookup"><span data-stu-id="48a13-151">Users can also search based on classification tags.</span></span> <span data-ttu-id="48a13-152">Json dosyasındaki `tags` özelliği `classifications` etiket listesiyle karıştırmayın.</span><span class="sxs-lookup"><span data-stu-id="48a13-152">Don't confuse the `tags` property in the json file with the `classifications` tags list.</span></span> <span data-ttu-id="48a13-153">Ne yazık ki benzer adlı iki farklı şey konum.</span><span class="sxs-lookup"><span data-stu-id="48a13-153">They're two different things unfortunately named similarly.</span></span> <span data-ttu-id="48a13-154">*template.json* dosyası için tam şema [JSON Schema Store'da](http://json.schemastore.org/template)bulunur.</span><span class="sxs-lookup"><span data-stu-id="48a13-154">The full schema for the *template.json* file is found at the [JSON Schema Store](http://json.schemastore.org/template).</span></span> <span data-ttu-id="48a13-155">*template.json* dosyası hakkında daha fazla bilgi [için, dotnet templating wiki](https://github.com/dotnet/templating/wiki)bakın.</span><span class="sxs-lookup"><span data-stu-id="48a13-155">For more information about the *template.json* file, see the [dotnet templating wiki](https://github.com/dotnet/templating/wiki).</span></span>

<span data-ttu-id="48a13-156">Artık geçerli bir _.template.config/template.json_ dosyanız olduğuna göre, şablonunuz yüklenmeye hazırdır.</span><span class="sxs-lookup"><span data-stu-id="48a13-156">Now that you have a valid _.template.config/template.json_ file, your template is ready to be installed.</span></span> <span data-ttu-id="48a13-157">Şablonu yüklemeden önce, şablonunuza dahil olmasını istemediğiniz ek dosya klasörlerini ve dosyalarını _(depo gözü_ veya _obj_ klasörleri) sildiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="48a13-157">Before you install the template, make sure that you delete any extra files folders and files you don't want included in your template, like the _bin_ or _obj_ folders.</span></span> <span data-ttu-id="48a13-158">Terminalinizde, _consoleasync_ klasörüne gidin `dotnet new -i .\` ve geçerli klasörde bulunan şablonu yüklemek için çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="48a13-158">In your terminal, navigate to the _consoleasync_ folder and run `dotnet new -i .\` to install the template located at the current folder.</span></span> <span data-ttu-id="48a13-159">Linux veya macOS işletim sistemi kullanıyorsanız, ileri eğik `dotnet new -i ./`çizgi kullanın: .</span><span class="sxs-lookup"><span data-stu-id="48a13-159">If you're using a Linux or macOS operating system, use a forward slash: `dotnet new -i ./`.</span></span>

<span data-ttu-id="48a13-160">Bu komut, sizinkini içermesi gereken yüklü şablonlar listesini çıkartır.</span><span class="sxs-lookup"><span data-stu-id="48a13-160">This command outputs the list of templates installed, which should include yours.</span></span>

```dotnetcli
dotnet new -i .\
```

<span data-ttu-id="48a13-161">Aşağıdakine benzer çıktı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="48a13-161">You get output similar to the following.</span></span>

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

### <a name="test-the-project-template"></a><span data-ttu-id="48a13-162">Proje şablonu test edin</span><span class="sxs-lookup"><span data-stu-id="48a13-162">Test the project template</span></span>

<span data-ttu-id="48a13-163">Artık yüklü bir öğe şablonu var, test edin.</span><span class="sxs-lookup"><span data-stu-id="48a13-163">Now that you have an item template installed, test it.</span></span>

1. <span data-ttu-id="48a13-164">_Test_ klasörüne gidin</span><span class="sxs-lookup"><span data-stu-id="48a13-164">Navigate to the _test_ folder</span></span>

1. <span data-ttu-id="48a13-165">Komutu ile kolayca test edebilirsiniz çalışan bir proje oluşturur aşağıdaki `dotnet run` komutu ile yeni bir konsol uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="48a13-165">Create a new console application with the following command which generates a working project you can easily test with the `dotnet run` command.</span></span>

    ```dotnetcli
    dotnet new consoleasync
    ```

    <span data-ttu-id="48a13-166">Aşağıdaki çıktıyı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="48a13-166">You get the following output.</span></span>

    ```console
    The template "Example templates: async project" was created successfully.
    ```

1. <span data-ttu-id="48a13-167">Aşağıdaki komutu kullanarak projeyi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="48a13-167">Run the project using the following command.</span></span>

    ```dotnetcli
    dotnet run
    ```

    <span data-ttu-id="48a13-168">Aşağıdaki çıktıyı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="48a13-168">You get the following output.</span></span>

    ```console
    Hello World with C# 8.0!
    ```

<span data-ttu-id="48a13-169">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="48a13-169">Congratulations!</span></span> <span data-ttu-id="48a13-170">.NET Core ile bir proje şablonu oluşturdunuz ve dağıttınız.</span><span class="sxs-lookup"><span data-stu-id="48a13-170">You created and deployed a project template with .NET Core.</span></span> <span data-ttu-id="48a13-171">Bu öğretici serinin bir sonraki bölümüne hazırlık olarak, oluşturduğunuz şablonu kaldırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="48a13-171">In preparation for the next part of this tutorial series, you must uninstall the template you created.</span></span> <span data-ttu-id="48a13-172">Test klasöründeki tüm _test_ dosyaları da sildiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="48a13-172">Make sure to delete all files from the _test_ folder too.</span></span> <span data-ttu-id="48a13-173">Bu, bu öğreticinin bir sonraki ana bölümü için hazır temiz bir duruma geri dönecektir.</span><span class="sxs-lookup"><span data-stu-id="48a13-173">This will get you back to a clean state ready for the next major section of this tutorial.</span></span>

### <a name="uninstall-the-template"></a><span data-ttu-id="48a13-174">Şablonu kaldırma</span><span class="sxs-lookup"><span data-stu-id="48a13-174">Uninstall the template</span></span>

<span data-ttu-id="48a13-175">Şablonu bir dosya yolu kullanarak yüklediğiniz için, şablonu **mutlak** dosya yolu ile kaldırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="48a13-175">Because you installed the template by using a file path, you must uninstall it with the **absolute** file path.</span></span> <span data-ttu-id="48a13-176">`dotnet new -u` Komutu çalıştırarak yüklenen şablonların listesini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48a13-176">You can see a list of templates installed by running the `dotnet new -u` command.</span></span> <span data-ttu-id="48a13-177">Şablonunuzun en son listelenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="48a13-177">Your template should be listed last.</span></span> <span data-ttu-id="48a13-178">Komutla `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` şablonunuzu kaldırmak için listelenen yolu kullanın.</span><span class="sxs-lookup"><span data-stu-id="48a13-178">Use the path listed to uninstall your template with the `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` command.</span></span>

```dotnetcli
dotnet new -u
```

<span data-ttu-id="48a13-179">Aşağıdakine benzer çıktı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="48a13-179">You get output similar to the following.</span></span>

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

<span data-ttu-id="48a13-180">Şablonu kaldırmak için aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="48a13-180">To uninstall a template, run the following command.</span></span>

```dotnetcli
dotnet new -u C:\working\templates\consoleasync
```

## <a name="next-steps"></a><span data-ttu-id="48a13-181">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="48a13-181">Next steps</span></span>

<span data-ttu-id="48a13-182">Bu öğreticide, bir proje şablonu oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="48a13-182">In this tutorial, you created a project template.</span></span> <span data-ttu-id="48a13-183">Hem öğeyi hem de proje şablonlarını kullanımı kolay bir dosyaya nasıl paketlendireceklerini öğrenmek için bu öğretici seriye devam edin.</span><span class="sxs-lookup"><span data-stu-id="48a13-183">To learn how to package both the item and project templates into an easy-to-use file, continue this tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="48a13-184">Şablon paketi oluşturma</span><span class="sxs-lookup"><span data-stu-id="48a13-184">Create a template pack</span></span>](cli-templates-create-template-pack.md)
