---
title: Yeni dotnet için proje şablonu oluşturma
description: Dotnet yeni bir komut için bir proje şablonu oluşturmayı öğrenin.
author: thraka
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: 31a6189c0126d6dff000bb84978c1527dbe4e2ae
ms.sourcegitcommit: 6472349821dbe202d01182bc2cfe9d7176eaaa6c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67877182"
---
# <a name="tutorial-create-a-project-template"></a><span data-ttu-id="e7991-103">Öğretici: Bir proje şablonu oluşturma</span><span class="sxs-lookup"><span data-stu-id="e7991-103">Tutorial: Create a project template</span></span>

<span data-ttu-id="e7991-104">.NET Core ile oluşturabilir ve projeleri, dosyaları, kaynaklar oluşturmak şablonlar dağıtın.</span><span class="sxs-lookup"><span data-stu-id="e7991-104">With .NET Core, you can create and deploy templates that generate projects, files, even resources.</span></span> <span data-ttu-id="e7991-105">Bu öğreticide iki oluşturmak, yüklemek ve kaldırmak, şablonları ile kullanılmak öğretir serinin bir parçasıdır `dotnet new` komutu.</span><span class="sxs-lookup"><span data-stu-id="e7991-105">This tutorial is part two of a series that teaches you how to create, install, and uninstall, templates for use with the `dotnet new` command.</span></span>

<span data-ttu-id="e7991-106">Serisinin bu bölümünde şunları öğrenirsiniz nasıl yapılır:</span><span class="sxs-lookup"><span data-stu-id="e7991-106">In this part of the series you'll learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="e7991-107">Kaynak bir proje şablonu oluşturma</span><span class="sxs-lookup"><span data-stu-id="e7991-107">Create the resources of a project template</span></span>
> * <span data-ttu-id="e7991-108">Şablon yapılandırma klasör ve dosya oluşturma</span><span class="sxs-lookup"><span data-stu-id="e7991-108">Create the template config folder and file</span></span>
> * <span data-ttu-id="e7991-109">Bir şablon bir dosya yolundan yükle</span><span class="sxs-lookup"><span data-stu-id="e7991-109">Install a template from a file path</span></span>
> * <span data-ttu-id="e7991-110">Öğe şablonu test</span><span class="sxs-lookup"><span data-stu-id="e7991-110">Test an item template</span></span>
> * <span data-ttu-id="e7991-111">Öğe şablonu Kaldır</span><span class="sxs-lookup"><span data-stu-id="e7991-111">Uninstall an item template</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e7991-112">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="e7991-112">Prerequisites</span></span>

* <span data-ttu-id="e7991-113">Tam [bölüm 1](cli-templates-create-item-template.md) Bu öğretici serisinin.</span><span class="sxs-lookup"><span data-stu-id="e7991-113">Complete [part 1](cli-templates-create-item-template.md) of this tutorial series.</span></span>
* <span data-ttu-id="e7991-114">Bir terminal açın ve gidin _working\templates\\_  klasör.</span><span class="sxs-lookup"><span data-stu-id="e7991-114">Open a terminal and navigate to the _working\templates\\_ folder.</span></span>

## <a name="create-a-project-template"></a><span data-ttu-id="e7991-115">Bir proje şablonu oluşturma</span><span class="sxs-lookup"><span data-stu-id="e7991-115">Create a project template</span></span>

<span data-ttu-id="e7991-116">Kullanıcılar için başlamak kolaylaştırır proje şablonları üretim çalıştırılmaya hazır projeleri çalışan kodu ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e7991-116">Project templates produce ready-to-run projects that make it easy for users to start with a working set of code.</span></span> <span data-ttu-id="e7991-117">.NET core konsol uygulaması veya bir sınıf kitaplığı gibi birkaç proje şablonlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="e7991-117">.NET Core includes a few project templates such as a console application or a class library.</span></span> <span data-ttu-id="e7991-118">Bu örnekte, sağlayan yeni bir konsol projesi oluşturacaksınız C# 8.0 ve oluşturan bir `async main` giriş noktası.</span><span class="sxs-lookup"><span data-stu-id="e7991-118">In this example, you'll create a new console project that enables C# 8.0 and produces an `async main` entry point.</span></span>

<span data-ttu-id="e7991-119">Terminalinizde gidin _working\templates\\_  klasör adında yeni bir alt klasör oluşturup _consoleasync_.</span><span class="sxs-lookup"><span data-stu-id="e7991-119">In your terminal, navigate to the _working\templates\\_ folder and create a new subfolder named _consoleasync_.</span></span> <span data-ttu-id="e7991-120">Alt klasörü girin ve çalıştırma `dotnet new console` standart konsol uygulaması oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="e7991-120">Enter the subfolder and run `dotnet new console` to generate the standard console application.</span></span> <span data-ttu-id="e7991-121">Yeni bir şablon oluşturmak için bu şablonu tarafından üretilen dosyaları düzenleme.</span><span class="sxs-lookup"><span data-stu-id="e7991-121">You'll be editing the files produced by this template to create a new template.</span></span>

```console
working
└───templates
    └───consoleasync
            consoleasync.csproj
            Program.cs
```

## <a name="modify-programcs"></a><span data-ttu-id="e7991-122">Program.cs değiştirme</span><span class="sxs-lookup"><span data-stu-id="e7991-122">Modify Program.cs</span></span>

<span data-ttu-id="e7991-123">Açık yukarı _program.cs_ dosya.</span><span class="sxs-lookup"><span data-stu-id="e7991-123">Open up the _program.cs_ file.</span></span> <span data-ttu-id="e7991-124">Konsol projesi değil, bir zaman uyumsuz bir giriş noktası kullanın, bu nedenle şimdi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e7991-124">The console project doesn't use an asynchronous entry point, so let's add that.</span></span> <span data-ttu-id="e7991-125">Kodunuz şu şekilde değiştirin ve dosyayı kaydedin:</span><span class="sxs-lookup"><span data-stu-id="e7991-125">Change your code to the following and save the file:</span></span>

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

## <a name="modify-consoleasynccsproj"></a><span data-ttu-id="e7991-126">Consoleasync.csproj değiştirme</span><span class="sxs-lookup"><span data-stu-id="e7991-126">Modify consoleasync.csproj</span></span>

<span data-ttu-id="e7991-127">Güncelleştirelim C# projenin kullandığı sürüm 8.0 Dil sürümü.</span><span class="sxs-lookup"><span data-stu-id="e7991-127">Let's update the C# language version the project uses to version 8.0.</span></span> <span data-ttu-id="e7991-128">Düzen _consoleasync.csproj_ dosya ve ekleme `<LangVersion>` ayarını bir `<PropertyGroup>` düğümü.</span><span class="sxs-lookup"><span data-stu-id="e7991-128">Edit the _consoleasync.csproj_ file and add the `<LangVersion>` setting to a `<PropertyGroup>` node.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.2</TargetFramework>

    <LangVersion>8.0</LangVersion>

  </PropertyGroup>
  
</Project>
```

## <a name="build-the-project"></a><span data-ttu-id="e7991-129">Proje derleme</span><span class="sxs-lookup"><span data-stu-id="e7991-129">Build the project</span></span>

<span data-ttu-id="e7991-130">Bir proje şablonu tamamlamadan önce bu şekilde sıkışmalı ve emin olmak için sınamalısınız.</span><span class="sxs-lookup"><span data-stu-id="e7991-130">Before you complete a project template, you should test it to make sure it compiles and runs correctly.</span></span> <span data-ttu-id="e7991-131">Terminalinizde çalıştırma `dotnet run` komutunu aşağıdaki çıktıyı görmelisiniz:</span><span class="sxs-lookup"><span data-stu-id="e7991-131">In your terminal, run the `dotnet run` command and you should see the following output:</span></span>

```console
C:\working\templates\consoleasync> dotnet run
Hello World with C# 8.0!
```

<span data-ttu-id="e7991-132">Silebilirsiniz _obj_ ve _bin_ kullanılarak oluşturulan klasörleri `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="e7991-132">You can delete the _obj_ and _bin_ folders created by using `dotnet run`.</span></span> <span data-ttu-id="e7991-133">Bu dosyaların silinmesi, şablonunuzu şablonunuza ilgili dosyaları ve hiçbir dosyaları yalnızca içeren bir derleme eylemi sonucunda ortaya çıkan sağlar.</span><span class="sxs-lookup"><span data-stu-id="e7991-133">Deleting these files ensures your template only includes the files related to your template and not any files that result of a build action.</span></span>

<span data-ttu-id="e7991-134">Oluşturduğunuz şablonu içeriğini olduğuna göre şablon yapılandırması şablonunun Kök klasörde oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e7991-134">Now that you have the content of the template created, you need to create the template config at the root folder of the template.</span></span>

## <a name="create-the-template-config"></a><span data-ttu-id="e7991-135">Şablon yapılandırması oluşturma</span><span class="sxs-lookup"><span data-stu-id="e7991-135">Create the template config</span></span>

<span data-ttu-id="e7991-136">Şablonlar, .NET core'da şablonunuzun kök dizininde mevcut özel bir klasör ve yapılandırma dosyasında tarafından tanınır.</span><span class="sxs-lookup"><span data-stu-id="e7991-136">Templates are recognized in .NET Core by a special folder and config file that exist at the root of your template.</span></span> <span data-ttu-id="e7991-137">Bu öğreticide, şu şablonu klasörünüze konumdadır _working\templates\consoleasync\\_ .</span><span class="sxs-lookup"><span data-stu-id="e7991-137">In this tutorial, your template folder is located at _working\templates\consoleasync\\_.</span></span>

<span data-ttu-id="e7991-138">Bir şablonu oluşturduğunuzda, tüm dosya ve klasörlerin şablon klasöründe özel yapılandırma klasörü dışında şablonun parçası olarak dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="e7991-138">When you create a template, all files and folders in the template folder are included as part of the template except for the special config folder.</span></span> <span data-ttu-id="e7991-139">Bu yapılandırma klasörü adlı _. template.config_.</span><span class="sxs-lookup"><span data-stu-id="e7991-139">This config folder is named _.template.config_.</span></span>

<span data-ttu-id="e7991-140">İlk olarak, adlı yeni bir alt klasör oluşturun _. template.config_, girin.</span><span class="sxs-lookup"><span data-stu-id="e7991-140">First, create a new subfolder named _.template.config_, enter it.</span></span> <span data-ttu-id="e7991-141">Adlı yeni bir dosya oluşturup _template.json_.</span><span class="sxs-lookup"><span data-stu-id="e7991-141">Then, create a new file named _template.json_.</span></span> <span data-ttu-id="e7991-142">Klasör yapınız gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="e7991-142">Your folder structure should look like this:</span></span>

```console
working
└───templates
    └───consoleasync
        └───.template.config
                template.json
```

<span data-ttu-id="e7991-143">Açık _template.json_ , sık kullandığınız metin düzenleyicisi ve Yapıştır aşağıdaki JSON kod ve kaydedin:</span><span class="sxs-lookup"><span data-stu-id="e7991-143">Open the _template.json_ with your favorite text editor and paste in the following json code and save it:</span></span>

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

<span data-ttu-id="e7991-144">Bu yapılandırma dosyası, tüm ayarlarını şablonunuz için içerir.</span><span class="sxs-lookup"><span data-stu-id="e7991-144">This config file contains all of the settings for your template.</span></span> <span data-ttu-id="e7991-145">Gördüğünüz gibi temel ayarlar `name` ve `shortName` ayrıca yoktur ancak bir `tags/type` ayarlanan değer `project`.</span><span class="sxs-lookup"><span data-stu-id="e7991-145">You can see the basic settings such as `name` and `shortName` but also there's a `tags/type` value that's set to `project`.</span></span> <span data-ttu-id="e7991-146">Bu şablon proje şablonu olarak belirler.</span><span class="sxs-lookup"><span data-stu-id="e7991-146">This designates your template as a project template.</span></span> <span data-ttu-id="e7991-147">Oluşturduğunuz şablonun türüyle ilgili bir kısıtlama yoktur.</span><span class="sxs-lookup"><span data-stu-id="e7991-147">There's no restriction on the type of template you create.</span></span> <span data-ttu-id="e7991-148">`item` Ve `project` değerler için yaygın olarak kullanılan adları .NET Core önerir ve böylece kullanıcılar bunlar aramakta olduğunuz şablon türü kolayca filtre uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e7991-148">The `item` and `project` values are common names that .NET Core recommends so that users can easily filter the type of template they're searching for.</span></span>

<span data-ttu-id="e7991-149">`classifications` Öğesini temsil eder **etiketleri** gördüğünüz çalıştırdığınızda sütun `dotnet new` ve şablon listesini alın.</span><span class="sxs-lookup"><span data-stu-id="e7991-149">The `classifications` item represents the **tags** column you see when you run `dotnet new` and get a list of templates.</span></span> <span data-ttu-id="e7991-150">Kullanıcılar ayrıca arayabilirler tabanlı sınıflandırma etiketleri.</span><span class="sxs-lookup"><span data-stu-id="e7991-150">Users can also search based on classification tags.</span></span> <span data-ttu-id="e7991-151">Karıştırmayın `tags` özelliği ile json dosyasındaki `classifications` Etiketler listesi.</span><span class="sxs-lookup"><span data-stu-id="e7991-151">Don't confuse the `tags` property in the json file with the `classifications` tags list.</span></span> <span data-ttu-id="e7991-152">Ne yazık ki benzer şekilde adlı iki terimin farklı anlamlara oldukları.</span><span class="sxs-lookup"><span data-stu-id="e7991-152">They're two different things unfortunately named similarly.</span></span> <span data-ttu-id="e7991-153">İçin tam şema *template.json* dosya konumunda bulundu [JSON şema Store](http://json.schemastore.org/template).</span><span class="sxs-lookup"><span data-stu-id="e7991-153">The full schema for the *template.json* file is found at the [JSON Schema Store](http://json.schemastore.org/template).</span></span> <span data-ttu-id="e7991-154">Hakkında daha fazla bilgi için *template.json* bkz [dotnet şablon wiki](https://github.com/dotnet/templating/wiki).</span><span class="sxs-lookup"><span data-stu-id="e7991-154">For more information about the *template.json* file, see the [dotnet templating wiki](https://github.com/dotnet/templating/wiki).</span></span>

<span data-ttu-id="e7991-155">Geçerli bir sahip olduğunuza göre _.template.config/template.json_ dosya, şablonunuzu yüklenmeye hazır.</span><span class="sxs-lookup"><span data-stu-id="e7991-155">Now that you have a valid _.template.config/template.json_ file, your template is ready to be installed.</span></span> <span data-ttu-id="e7991-156">Şablon yüklemeden önce herhangi bir ek dosya, klasör ve istemediğiniz dosyaları gibi şablonunuzda dahil sildiğinizden emin olun _bin_ veya _obj_ klasörleri.</span><span class="sxs-lookup"><span data-stu-id="e7991-156">Before you install the template, make sure that you delete any extra files folders and files you don't want included in your template, like the _bin_ or _obj_ folders.</span></span> <span data-ttu-id="e7991-157">Terminalinizde gidin _consoleasync_ klasör ve çalışma `dotnet new -i .\` geçerli klasöründe şablonunu yüklemek için.</span><span class="sxs-lookup"><span data-stu-id="e7991-157">In your terminal, navigate to the _consoleasync_ folder and run `dotnet new -i .\` to install the template located at the current folder.</span></span> <span data-ttu-id="e7991-158">Bir Linux veya Mac OS x işletim sistemi kullanıyorsanız, eğik çizgi kullanın: `dotnet new -i ./`.</span><span class="sxs-lookup"><span data-stu-id="e7991-158">If you're using a Linux or MacOS operating system, use a forward slash: `dotnet new -i ./`.</span></span>

<span data-ttu-id="e7991-159">Bu komut sizin kapsamalıdır yüklü şablonlar listesinden çıkarır.</span><span class="sxs-lookup"><span data-stu-id="e7991-159">This command outputs the list of templates installed, which should include yours.</span></span>

```console
C:\working\templates\consoleasync> dotnet new -i .\
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

### <a name="test-the-project-template"></a><span data-ttu-id="e7991-160">Test projesi şablonu</span><span class="sxs-lookup"><span data-stu-id="e7991-160">Test the project template</span></span>

<span data-ttu-id="e7991-161">Yüklü bir öğe şablonunu olduğuna göre test edin.</span><span class="sxs-lookup"><span data-stu-id="e7991-161">Now that you have an item template installed, test it.</span></span> <span data-ttu-id="e7991-162">Gidin _test_ klasörü ile yeni bir konsol uygulaması oluşturup `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="e7991-162">Navigate to the _test_ folder and create a new console application with `dotnet new console`.</span></span> <span data-ttu-id="e7991-163">Bu, kolayca test ile bir çalışma projenin oluşturduğu `dotnet run` komutu.</span><span class="sxs-lookup"><span data-stu-id="e7991-163">This generates a working project you can easily test with the `dotnet run` command.</span></span>

```console
C:\test> dotnet new consoleasync
The template "Example templates: async project" was created successfully.
```

```console
C:\test> dotnet run
Hello World with C# 8.0!
```

<span data-ttu-id="e7991-164">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="e7991-164">Congratulations!</span></span> <span data-ttu-id="e7991-165">Oluşturduğunuz ve .NET Core proje şablonu dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="e7991-165">You created and deployed a project template with .NET Core.</span></span> <span data-ttu-id="e7991-166">Bu öğretici serisinin bir sonraki bölümü için hazırlanırken oluşturduğunuz şablonu kaldırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e7991-166">In preparation for the next part of this tutorial series, you must uninstall the template you created.</span></span> <span data-ttu-id="e7991-167">Tüm dosyaları silmek istediğinizden emin olun _test_ klasörü çok.</span><span class="sxs-lookup"><span data-stu-id="e7991-167">Make sure to delete all files from the _test_ folder too.</span></span> <span data-ttu-id="e7991-168">Bununla geri temiz bir duruma hazır için bu öğreticinin sonraki ana bölüme sahip olursunuz.</span><span class="sxs-lookup"><span data-stu-id="e7991-168">This will get you back to a clean state ready for the next major section of this tutorial.</span></span>

### <a name="uninstall-the-template"></a><span data-ttu-id="e7991-169">Şablonu Kaldır</span><span class="sxs-lookup"><span data-stu-id="e7991-169">Uninstall the template</span></span>

<span data-ttu-id="e7991-170">Bir dosya yolu kullanarak şablon yüklü olduğundan, birlikte kaldırmalısınız **mutlak** dosya yolu.</span><span class="sxs-lookup"><span data-stu-id="e7991-170">Because you installed the template by using a file path, you must uninstall it with the **absolute** file path.</span></span> <span data-ttu-id="e7991-171">Çalıştırarak yüklü şablonlar listesi gördüğünüz `dotnet new -u` komutu.</span><span class="sxs-lookup"><span data-stu-id="e7991-171">You can see a list of templates installed by running the `dotnet new -u` command.</span></span> <span data-ttu-id="e7991-172">Şablonunuzu son listelenmelidir.</span><span class="sxs-lookup"><span data-stu-id="e7991-172">Your template should be listed last.</span></span> <span data-ttu-id="e7991-173">Yolun listelenen şablonunuzla birlikte kaldırmak için kullanımı `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` komutu.</span><span class="sxs-lookup"><span data-stu-id="e7991-173">Use the path listed to uninstall your template with the `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` command.</span></span>

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
  C:\working\templates\consoleasync
    Templates:
      Example templates: async project (consoleasync) C#
```

```console
C:\working> dotnet new -u C:\working\templates\consoleasync
```

## <a name="next-steps"></a><span data-ttu-id="e7991-174">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="e7991-174">Next steps</span></span>

<span data-ttu-id="e7991-175">Bu öğreticide, bir proje şablonu oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="e7991-175">In this tutorial, you created a project template.</span></span> <span data-ttu-id="e7991-176">Öğe ve proje şablonlarının bir kolayca kullanıma dosyasına paketini öğrenmek için Bu öğretici serisine devam edin.</span><span class="sxs-lookup"><span data-stu-id="e7991-176">To learn how to package both the item and project templates into an easy-to-use file, continue this tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e7991-177">Bir şablon paketi oluşturma</span><span class="sxs-lookup"><span data-stu-id="e7991-177">Create a template pack</span></span>](cli-templates-create-template-pack.md)
