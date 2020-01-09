---
title: DotNet New için bir proje şablonu oluşturun
description: DotNet New komutu için bir proje şablonu oluşturmayı öğrenin.
author: thraka
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: 64b029f87135c3424d01a6833619f0aec3833883
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75340359"
---
# <a name="tutorial-create-a-project-template"></a><span data-ttu-id="317e5-103">Öğretici: proje şablonu oluşturma</span><span class="sxs-lookup"><span data-stu-id="317e5-103">Tutorial: Create a project template</span></span>

<span data-ttu-id="317e5-104">.NET Core ile projeler, dosyalar, hatta kaynaklar üreten şablonlar oluşturabilir ve dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="317e5-104">With .NET Core, you can create and deploy templates that generate projects, files, even resources.</span></span> <span data-ttu-id="317e5-105">Bu öğretici, `dotnet new` komutuyla kullanılmak üzere şablonlar oluşturmayı, yüklemeyi ve kaldırmayı öğretir.</span><span class="sxs-lookup"><span data-stu-id="317e5-105">This tutorial is part two of a series that teaches you how to create, install, and uninstall, templates for use with the `dotnet new` command.</span></span>

<span data-ttu-id="317e5-106">Serinin bu bölümünde şunları nasıl yapacağınızı öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="317e5-106">In this part of the series you'll learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="317e5-107">Proje şablonunun kaynaklarını oluşturma</span><span class="sxs-lookup"><span data-stu-id="317e5-107">Create the resources of a project template</span></span>
> * <span data-ttu-id="317e5-108">Şablon yapılandırma klasörünü ve dosyasını oluşturma</span><span class="sxs-lookup"><span data-stu-id="317e5-108">Create the template config folder and file</span></span>
> * <span data-ttu-id="317e5-109">Dosya yolundan şablon yükler</span><span class="sxs-lookup"><span data-stu-id="317e5-109">Install a template from a file path</span></span>
> * <span data-ttu-id="317e5-110">Bir öğe şablonunu test etme</span><span class="sxs-lookup"><span data-stu-id="317e5-110">Test an item template</span></span>
> * <span data-ttu-id="317e5-111">Öğe şablonunu kaldırma</span><span class="sxs-lookup"><span data-stu-id="317e5-111">Uninstall an item template</span></span>

## <a name="prerequisites"></a><span data-ttu-id="317e5-112">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="317e5-112">Prerequisites</span></span>

* <span data-ttu-id="317e5-113">Bu öğretici serisinin [1. bölümünü](cli-templates-create-item-template.md) doldurun.</span><span class="sxs-lookup"><span data-stu-id="317e5-113">Complete [part 1](cli-templates-create-item-template.md) of this tutorial series.</span></span>
* <span data-ttu-id="317e5-114">Bir Terminal açın ve _working\templates_ klasörüne gidin.</span><span class="sxs-lookup"><span data-stu-id="317e5-114">Open a terminal and navigate to the _working\templates_ folder.</span></span>

## <a name="create-a-project-template"></a><span data-ttu-id="317e5-115">Proje şablonu oluşturma</span><span class="sxs-lookup"><span data-stu-id="317e5-115">Create a project template</span></span>

<span data-ttu-id="317e5-116">Proje şablonları, kullanıcıların çalışan bir kod kümesiyle başlamasını kolaylaştıran, çalıştırmaya yönelik olarak çalışan projeler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="317e5-116">Project templates produce ready-to-run projects that make it easy for users to start with a working set of code.</span></span> <span data-ttu-id="317e5-117">.NET Core, konsol uygulaması veya sınıf kitaplığı gibi bazı proje şablonları içerir.</span><span class="sxs-lookup"><span data-stu-id="317e5-117">.NET Core includes a few project templates such as a console application or a class library.</span></span> <span data-ttu-id="317e5-118">Bu örnekte, 8,0 sağlayan C# ve bir `async main` giriş noktası üreten yeni bir konsol projesi oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="317e5-118">In this example, you'll create a new console project that enables C# 8.0 and produces an `async main` entry point.</span></span>

<span data-ttu-id="317e5-119">Terminalinizde, _working\templates_ klasörüne gidin ve _consoleasync_adlı yeni bir alt klasör oluşturun.</span><span class="sxs-lookup"><span data-stu-id="317e5-119">In your terminal, navigate to the _working\templates_ folder and create a new subfolder named _consoleasync_.</span></span> <span data-ttu-id="317e5-120">Standart konsol uygulamasını oluşturmak için alt klasörü girin ve `dotnet new console` çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="317e5-120">Enter the subfolder and run `dotnet new console` to generate the standard console application.</span></span> <span data-ttu-id="317e5-121">Bu şablon tarafından oluşturulan dosyaları düzenleyerek yeni bir şablon oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="317e5-121">You'll be editing the files produced by this template to create a new template.</span></span>

```console
working
└───templates
    └───consoleasync
            consoleasync.csproj
            Program.cs
```

## <a name="modify-programcs"></a><span data-ttu-id="317e5-122">Program.cs Değiştir</span><span class="sxs-lookup"><span data-stu-id="317e5-122">Modify Program.cs</span></span>

<span data-ttu-id="317e5-123">_Program.cs_ dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="317e5-123">Open up the _program.cs_ file.</span></span> <span data-ttu-id="317e5-124">Konsol projesi zaman uyumsuz bir giriş noktası kullanmaz, bu nedenle bunu ekleyelim.</span><span class="sxs-lookup"><span data-stu-id="317e5-124">The console project doesn't use an asynchronous entry point, so let's add that.</span></span> <span data-ttu-id="317e5-125">Kodunuzu aşağıdaki şekilde değiştirin ve dosyayı kaydedin:</span><span class="sxs-lookup"><span data-stu-id="317e5-125">Change your code to the following and save the file:</span></span>

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

## <a name="modify-consoleasynccsproj"></a><span data-ttu-id="317e5-126">Consoleasync. csproj öğesini Değiştir</span><span class="sxs-lookup"><span data-stu-id="317e5-126">Modify consoleasync.csproj</span></span>

<span data-ttu-id="317e5-127">Projenin 8,0 sürümünü kullandığı C# dil sürümünü güncelleştirelim.</span><span class="sxs-lookup"><span data-stu-id="317e5-127">Let's update the C# language version the project uses to version 8.0.</span></span> <span data-ttu-id="317e5-128">_Consoleasync. csproj_ dosyasını düzenleyin ve `<PropertyGroup>` düğümüne `<LangVersion>` ayarını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="317e5-128">Edit the _consoleasync.csproj_ file and add the `<LangVersion>` setting to a `<PropertyGroup>` node.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.2</TargetFramework>

    <LangVersion>8.0</LangVersion>

  </PropertyGroup>
  
</Project>
```

## <a name="build-the-project"></a><span data-ttu-id="317e5-129">Proje derleme</span><span class="sxs-lookup"><span data-stu-id="317e5-129">Build the project</span></span>

<span data-ttu-id="317e5-130">Bir proje şablonunu tamamlamadan önce, derlendiğinden ve düzgün çalıştığından emin olmak için test etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="317e5-130">Before you complete a project template, you should test it to make sure it compiles and runs correctly.</span></span> <span data-ttu-id="317e5-131">Terminalinizde `dotnet run` komutunu çalıştırın ve aşağıdaki çıktıyı görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="317e5-131">In your terminal, run the `dotnet run` command and you should see the following output:</span></span>

```console
C:\working\templates\consoleasync> dotnet run
Hello World with C# 8.0!
```

<span data-ttu-id="317e5-132">`dotnet run`kullanarak oluşturulan _obj_ ve _bin_ klasörlerini silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="317e5-132">You can delete the _obj_ and _bin_ folders created by using `dotnet run`.</span></span> <span data-ttu-id="317e5-133">Bu dosyaların silinmesi, şablonunuzun yalnızca şablonlarınız ile ilgili dosyaları ve bir yapı eylemi sonucu olan dosyaları içerip içermemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="317e5-133">Deleting these files ensures your template only includes the files related to your template and not any files that result of a build action.</span></span>

<span data-ttu-id="317e5-134">Artık oluşturulan şablonun içeriğine sahip olduğunuza göre, şablonun kök klasöründe şablon yapılandırmasını oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="317e5-134">Now that you have the content of the template created, you need to create the template config at the root folder of the template.</span></span>

## <a name="create-the-template-config"></a><span data-ttu-id="317e5-135">Şablon yapılandırması oluşturma</span><span class="sxs-lookup"><span data-stu-id="317e5-135">Create the template config</span></span>

<span data-ttu-id="317e5-136">Şablonlar, .NET Core 'da şablonunuzun kökünde bulunan özel bir klasör ve yapılandırma dosyası tarafından tanınır.</span><span class="sxs-lookup"><span data-stu-id="317e5-136">Templates are recognized in .NET Core by a special folder and config file that exist at the root of your template.</span></span> <span data-ttu-id="317e5-137">Bu öğreticide, şablon klasörünüz _working\templates\consoleasync_adresinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="317e5-137">In this tutorial, your template folder is located at _working\templates\consoleasync_.</span></span>

<span data-ttu-id="317e5-138">Bir şablon oluşturduğunuzda, şablon klasöründeki tüm dosyalar ve klasörler, özel yapılandırma klasörü hariç, şablonun bir parçası olarak dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="317e5-138">When you create a template, all files and folders in the template folder are included as part of the template except for the special config folder.</span></span> <span data-ttu-id="317e5-139">Bu yapılandırma klasörü _. Template. config_olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="317e5-139">This config folder is named _.template.config_.</span></span>

<span data-ttu-id="317e5-140">İlk olarak, _. Template. config_adlı yeni bir alt klasör oluşturun, bunu girin.</span><span class="sxs-lookup"><span data-stu-id="317e5-140">First, create a new subfolder named _.template.config_, enter it.</span></span> <span data-ttu-id="317e5-141">Ardından, _Template. JSON_adlı yeni bir dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="317e5-141">Then, create a new file named _template.json_.</span></span> <span data-ttu-id="317e5-142">Klasör yapınız şöyle görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="317e5-142">Your folder structure should look like this:</span></span>

```console
working
└───templates
    └───consoleasync
        └───.template.config
                template.json
```

<span data-ttu-id="317e5-143">En sevdiğiniz metin düzenleyicinizle _Template. JSON_ ' i açın ve aşağıdaki JSON kodunu yapıştırın ve kaydedin:</span><span class="sxs-lookup"><span data-stu-id="317e5-143">Open the _template.json_ with your favorite text editor and paste in the following json code and save it:</span></span>

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

<span data-ttu-id="317e5-144">Bu yapılandırma dosyası şablonunuz için tüm ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="317e5-144">This config file contains all of the settings for your template.</span></span> <span data-ttu-id="317e5-145">`name` ve `shortName` gibi temel ayarları görebilir, ancak `project`olarak ayarlanmış bir `tags/type` değeri de vardır.</span><span class="sxs-lookup"><span data-stu-id="317e5-145">You can see the basic settings such as `name` and `shortName` but also there's a `tags/type` value that's set to `project`.</span></span> <span data-ttu-id="317e5-146">Bu, şablonunuzu bir proje şablonu olarak belirler.</span><span class="sxs-lookup"><span data-stu-id="317e5-146">This designates your template as a project template.</span></span> <span data-ttu-id="317e5-147">Oluşturduğunuz şablon türü üzerinde hiçbir kısıtlama yoktur.</span><span class="sxs-lookup"><span data-stu-id="317e5-147">There's no restriction on the type of template you create.</span></span> <span data-ttu-id="317e5-148">`item` ve `project` değerleri, .NET Core 'un arama yapmakta oldukları şablonun türünü kolayca filtreleyebilmesi için .NET Core 'un önerdiği yaygın adlardır.</span><span class="sxs-lookup"><span data-stu-id="317e5-148">The `item` and `project` values are common names that .NET Core recommends so that users can easily filter the type of template they're searching for.</span></span>

<span data-ttu-id="317e5-149">`classifications` öğesi, `dotnet new` çalıştırdığınız ve şablonların bir listesini alacağınız zaman gördüğünüz **Etiketler** sütununu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="317e5-149">The `classifications` item represents the **tags** column you see when you run `dotnet new` and get a list of templates.</span></span> <span data-ttu-id="317e5-150">Kullanıcılar ayrıca sınıflandırma etiketlerine göre arama yapabilir.</span><span class="sxs-lookup"><span data-stu-id="317e5-150">Users can also search based on classification tags.</span></span> <span data-ttu-id="317e5-151">JSON dosyasındaki `tags` özelliğini `classifications` Etiketler listesiyle karıştırmayın.</span><span class="sxs-lookup"><span data-stu-id="317e5-151">Don't confuse the `tags` property in the json file with the `classifications` tags list.</span></span> <span data-ttu-id="317e5-152">Benzer şekilde adlandırılan iki farklı şey vardır.</span><span class="sxs-lookup"><span data-stu-id="317e5-152">They're two different things unfortunately named similarly.</span></span> <span data-ttu-id="317e5-153">*Template. JSON* dosyasının tam şeması [JSON Şema deposunda](http://json.schemastore.org/template)bulunur.</span><span class="sxs-lookup"><span data-stu-id="317e5-153">The full schema for the *template.json* file is found at the [JSON Schema Store](http://json.schemastore.org/template).</span></span> <span data-ttu-id="317e5-154">*Template. JSON* dosyası hakkında daha fazla bilgi için bkz. [DotNet şablon oluşturma wiki](https://github.com/dotnet/templating/wiki).</span><span class="sxs-lookup"><span data-stu-id="317e5-154">For more information about the *template.json* file, see the [dotnet templating wiki](https://github.com/dotnet/templating/wiki).</span></span>

<span data-ttu-id="317e5-155">Artık geçerli bir _. Template. config/Template. JSON_ dosyanız olduğuna göre, şablonunuz yüklenmeye hazırdır.</span><span class="sxs-lookup"><span data-stu-id="317e5-155">Now that you have a valid _.template.config/template.json_ file, your template is ready to be installed.</span></span> <span data-ttu-id="317e5-156">Şablonu yüklemeden önce, _küme_ veya _obj_ klasörleri gibi şablonunuzda yer almasını istemediğiniz ek dosya klasörlerini ve dosyalarını sildiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="317e5-156">Before you install the template, make sure that you delete any extra files folders and files you don't want included in your template, like the _bin_ or _obj_ folders.</span></span> <span data-ttu-id="317e5-157">Terminalinizde _consoleasync_ klasörüne gidin ve geçerli klasörde bulunan şablonu yüklemek için `dotnet new -i .\` çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="317e5-157">In your terminal, navigate to the _consoleasync_ folder and run `dotnet new -i .\` to install the template located at the current folder.</span></span> <span data-ttu-id="317e5-158">Linux veya MacOS işletim sistemi kullanıyorsanız, eğik çizgi kullanın: `dotnet new -i ./`.</span><span class="sxs-lookup"><span data-stu-id="317e5-158">If you're using a Linux or MacOS operating system, use a forward slash: `dotnet new -i ./`.</span></span>

<span data-ttu-id="317e5-159">Bu komut, yüklenmiş şablonların listesini verir ve bunları içermelidir.</span><span class="sxs-lookup"><span data-stu-id="317e5-159">This command outputs the list of templates installed, which should include yours.</span></span>

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

### <a name="test-the-project-template"></a><span data-ttu-id="317e5-160">Proje şablonunu test etme</span><span class="sxs-lookup"><span data-stu-id="317e5-160">Test the project template</span></span>

<span data-ttu-id="317e5-161">Artık bir öğe şablonu yükleolduğunuza göre, test edin.</span><span class="sxs-lookup"><span data-stu-id="317e5-161">Now that you have an item template installed, test it.</span></span> <span data-ttu-id="317e5-162">_Test_ klasörüne gidin ve `dotnet new consoleasync`yeni bir konsol uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="317e5-162">Navigate to the _test_ folder and create a new console application with `dotnet new consoleasync`.</span></span> <span data-ttu-id="317e5-163">Bu, `dotnet run` komutuyla kolayca test edebileceğiniz bir çalışan proje oluşturur.</span><span class="sxs-lookup"><span data-stu-id="317e5-163">This generates a working project you can easily test with the `dotnet run` command.</span></span>

```console
C:\test> dotnet new consoleasync
The template "Example templates: async project" was created successfully.
```

```console
C:\test> dotnet run
Hello World with C# 8.0!
```

<span data-ttu-id="317e5-164">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="317e5-164">Congratulations!</span></span> <span data-ttu-id="317e5-165">.NET Core ile bir proje şablonu oluşturdunuz ve dağıttıysanız.</span><span class="sxs-lookup"><span data-stu-id="317e5-165">You created and deployed a project template with .NET Core.</span></span> <span data-ttu-id="317e5-166">Bu öğretici serisinin bir sonraki kısmına hazırlanın, oluşturduğunuz şablonu kaldırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="317e5-166">In preparation for the next part of this tutorial series, you must uninstall the template you created.</span></span> <span data-ttu-id="317e5-167">Tüm dosyaları da _Test_ klasöründen sildiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="317e5-167">Make sure to delete all files from the _test_ folder too.</span></span> <span data-ttu-id="317e5-168">Bu, Bu öğreticinin bir sonraki ana kısmına yönelik temiz bir duruma geri dönebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="317e5-168">This will get you back to a clean state ready for the next major section of this tutorial.</span></span>

### <a name="uninstall-the-template"></a><span data-ttu-id="317e5-169">Şablonu kaldırma</span><span class="sxs-lookup"><span data-stu-id="317e5-169">Uninstall the template</span></span>

<span data-ttu-id="317e5-170">Şablonu bir dosya yolu kullanarak yükletiğinden, **mutlak** dosya yoluyla kaldırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="317e5-170">Because you installed the template by using a file path, you must uninstall it with the **absolute** file path.</span></span> <span data-ttu-id="317e5-171">`dotnet new -u` komutunu çalıştırarak, yüklenmiş şablonların listesini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="317e5-171">You can see a list of templates installed by running the `dotnet new -u` command.</span></span> <span data-ttu-id="317e5-172">Şablonunuzun son listelenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="317e5-172">Your template should be listed last.</span></span> <span data-ttu-id="317e5-173">`dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` komutuyla şablonunuzu kaldırmak için listelenen yolu kullanın.</span><span class="sxs-lookup"><span data-stu-id="317e5-173">Use the path listed to uninstall your template with the `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` command.</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="317e5-174">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="317e5-174">Next steps</span></span>

<span data-ttu-id="317e5-175">Bu öğreticide bir proje şablonu oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="317e5-175">In this tutorial, you created a project template.</span></span> <span data-ttu-id="317e5-176">Hem öğe hem de proje şablonlarının kullanımı kolay bir dosyaya nasıl paketleyeceğinizi öğrenmek için, bu öğretici serisine devam edin.</span><span class="sxs-lookup"><span data-stu-id="317e5-176">To learn how to package both the item and project templates into an easy-to-use file, continue this tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="317e5-177">Şablon paketi oluşturma</span><span class="sxs-lookup"><span data-stu-id="317e5-177">Create a template pack</span></span>](cli-templates-create-template-pack.md)
