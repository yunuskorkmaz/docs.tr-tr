---
title: Dotnet için bir öğe şablonunu yeni - .NET Core CLI oluştur
description: Dotnet yeni bir komut için bir öğe şablonu oluşturmayı öğrenin. Öğe şablonları, herhangi bir sayıda dosyaları içerebilir.
author: thraka
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: c50aaf413f08c2e4cbe3f8ce8c057e5841067c92
ms.sourcegitcommit: 6472349821dbe202d01182bc2cfe9d7176eaaa6c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67877179"
---
# <a name="tutorial-create-an-item-template"></a><span data-ttu-id="8efb9-104">Öğretici: Öğe şablonu oluşturma</span><span class="sxs-lookup"><span data-stu-id="8efb9-104">Tutorial: Create an item template</span></span>

<span data-ttu-id="8efb9-105">.NET Core ile oluşturabilir ve projeleri, dosyaları, kaynaklar oluşturmak şablonlar dağıtın.</span><span class="sxs-lookup"><span data-stu-id="8efb9-105">With .NET Core, you can create and deploy templates that generate projects, files, even resources.</span></span> <span data-ttu-id="8efb9-106">Bu öğretici, oluşturmak, yüklemek ve kaldırmak, şablonları ile kullanılmak öğretir bir dizinin birinci bölümüdür `dotnet new` komutu.</span><span class="sxs-lookup"><span data-stu-id="8efb9-106">This tutorial is part one of a series that teaches you how to create, install, and uninstall, templates for use with the `dotnet new` command.</span></span>

<span data-ttu-id="8efb9-107">Serisinin bu bölümünde şunları öğrenirsiniz nasıl yapılır:</span><span class="sxs-lookup"><span data-stu-id="8efb9-107">In this part of the series, you'll learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="8efb9-108">Öğe şablonu için bir sınıf oluşturma</span><span class="sxs-lookup"><span data-stu-id="8efb9-108">Create a class for an item template</span></span>
> * <span data-ttu-id="8efb9-109">Şablon yapılandırma klasör ve dosya oluşturma</span><span class="sxs-lookup"><span data-stu-id="8efb9-109">Create the template config folder and file</span></span>
> * <span data-ttu-id="8efb9-110">Bir şablon bir dosya yolundan yükle</span><span class="sxs-lookup"><span data-stu-id="8efb9-110">Install a template from a file path</span></span>
> * <span data-ttu-id="8efb9-111">Öğe şablonu test</span><span class="sxs-lookup"><span data-stu-id="8efb9-111">Test an item template</span></span>
> * <span data-ttu-id="8efb9-112">Öğe şablonu Kaldır</span><span class="sxs-lookup"><span data-stu-id="8efb9-112">Uninstall an item template</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8efb9-113">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="8efb9-113">Prerequisites</span></span>

* <span data-ttu-id="8efb9-114">[.NET core 2.2 SDK](https://www.microsoft.com/net/core) veya sonraki sürümler.</span><span class="sxs-lookup"><span data-stu-id="8efb9-114">[.NET Core 2.2 SDK](https://www.microsoft.com/net/core) or later versions.</span></span>
* <span data-ttu-id="8efb9-115">Başvuru makaleyi okuyun [yeni dotnet için özel şablonları](../tools/custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="8efb9-115">Read the reference article [Custom templates for dotnet new](../tools/custom-templates.md).</span></span>

  <span data-ttu-id="8efb9-116">Başvurusu makalesinde, şablonlar ve nasıl bunlar bir araya hakkında temel bilgileri açıklar.</span><span class="sxs-lookup"><span data-stu-id="8efb9-116">The reference article explains the basics about templates and how they're put together.</span></span> <span data-ttu-id="8efb9-117">Bu bilgilerin bazıları burada reiterated.</span><span class="sxs-lookup"><span data-stu-id="8efb9-117">Some of this information will be reiterated here.</span></span>

* <span data-ttu-id="8efb9-118">Bir terminal açın ve gidin _working\templates\\_  klasör.</span><span class="sxs-lookup"><span data-stu-id="8efb9-118">Open a terminal and navigate to the _working\templates\\_ folder.</span></span>

## <a name="create-the-required-folders"></a><span data-ttu-id="8efb9-119">Gerekli klasörleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="8efb9-119">Create the required folders</span></span>

<span data-ttu-id="8efb9-120">Bu seri, "şablonu kaynak bulunduğu bir çalışma klasörü" ve "şablonlarınızı test etmek için kullanılan bir sınama klasör" kullanır.</span><span class="sxs-lookup"><span data-stu-id="8efb9-120">This series uses a "working folder" where your template source is contained and a "testing folder" used to test your templates.</span></span> <span data-ttu-id="8efb9-121">Çalışma klasörü ve test klasörü aynı üst klasör altında olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8efb9-121">The working folder and testing folder should be under the same parent folder.</span></span>

<span data-ttu-id="8efb9-122">İlk olarak, üst klasörü oluşturun, adı önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="8efb9-122">First, create the parent folder, the name does not matter.</span></span> <span data-ttu-id="8efb9-123">Adlı bir alt klasör oluşturup _çalışma_.</span><span class="sxs-lookup"><span data-stu-id="8efb9-123">Then, create a subfolder named _working_.</span></span> <span data-ttu-id="8efb9-124">İçine _çalışma_ klasöründe adlı bir alt klasör oluşturun _şablonları_.</span><span class="sxs-lookup"><span data-stu-id="8efb9-124">Inside of the _working_ folder, create a subfolder named _templates_.</span></span>

<span data-ttu-id="8efb9-125">Ardından, adlı üst klasör altında bir klasör oluşturun _test_.</span><span class="sxs-lookup"><span data-stu-id="8efb9-125">Next, create a folder under the parent folder named _test_.</span></span> <span data-ttu-id="8efb9-126">Klasör yapısı aşağıdaki gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="8efb9-126">The folder structure should look like the following:</span></span>

```console
parent_folder
├───test
└───working
    └───templates
```

## <a name="create-an-item-template"></a><span data-ttu-id="8efb9-127">Öğe şablonu oluşturma</span><span class="sxs-lookup"><span data-stu-id="8efb9-127">Create an item template</span></span>

<span data-ttu-id="8efb9-128">Öğe şablonu, bir veya daha fazla dosya içeren şablon belirli bir türdür.</span><span class="sxs-lookup"><span data-stu-id="8efb9-128">An item template is a specific type of template that contains one or more files.</span></span> <span data-ttu-id="8efb9-129">Bu tür şablon yapılandırma, kod veya çözüm dosyası gibi bir şey oluşturmak istediğinizde kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="8efb9-129">These types of templates are useful when you want to generate something like a config, code, or solution file.</span></span> <span data-ttu-id="8efb9-130">Bu örnekte, dize türü için bir uzantı yöntemini ekleyen bir sınıf oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="8efb9-130">In this example, you'll create a class that adds an extension method to the string type.</span></span>

<span data-ttu-id="8efb9-131">Terminalinizde gidin _working\templates\\_  klasör adında yeni bir alt klasör oluşturup _uzantıları_.</span><span class="sxs-lookup"><span data-stu-id="8efb9-131">In your terminal, navigate to the _working\templates\\_ folder and create a new subfolder named _extensions_.</span></span> <span data-ttu-id="8efb9-132">Klasörü girin.</span><span class="sxs-lookup"><span data-stu-id="8efb9-132">Enter the folder.</span></span>

```console
working
└───templates
    └───extensions
```

<span data-ttu-id="8efb9-133">Adlı yeni bir dosya oluşturun _CommonExtensions.cs_ ve sevdiğiniz bir metin düzenleyici ile açın.</span><span class="sxs-lookup"><span data-stu-id="8efb9-133">Create a new file named _CommonExtensions.cs_ and open it with your favorite text editor.</span></span> <span data-ttu-id="8efb9-134">Bu sınıf adlı bir genişletme yöntemi sağlayacak `Reverse` , bir dizenin içeriklerini tersine çevirir.</span><span class="sxs-lookup"><span data-stu-id="8efb9-134">This class will provide an extension method named `Reverse` that reverses the contents of a string.</span></span> <span data-ttu-id="8efb9-135">Aşağıdaki kodu yapıştırın ve dosyayı kaydedin:</span><span class="sxs-lookup"><span data-stu-id="8efb9-135">Paste in the following code and save the file:</span></span>

```csharp
using System;

namespace System
{
    public static class StringExtensions
    {
        public static string Reverse(this string value)
        {
            var tempArray = value.ToCharArray();
            Array.Reverse(tempArray);
            return new string(tempArray);
        }
    }
}
```

<span data-ttu-id="8efb9-136">Oluşturduğunuz şablonu içeriğini olduğuna göre şablon yapılandırması şablonunun Kök klasörde oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8efb9-136">Now that you have the content of the template created, you need to create the template config at the root folder of the template.</span></span>

## <a name="create-the-template-config"></a><span data-ttu-id="8efb9-137">Şablon yapılandırması oluşturma</span><span class="sxs-lookup"><span data-stu-id="8efb9-137">Create the template config</span></span>

<span data-ttu-id="8efb9-138">Şablonlar, .NET core'da şablonunuzun kök dizininde mevcut özel bir klasör ve yapılandırma dosyasında tarafından tanınır.</span><span class="sxs-lookup"><span data-stu-id="8efb9-138">Templates are recognized in .NET Core by a special folder and config file that exist at the root of your template.</span></span> <span data-ttu-id="8efb9-139">Bu öğreticide, şu şablonu klasörünüze konumdadır _working\templates\extensions\\_ .</span><span class="sxs-lookup"><span data-stu-id="8efb9-139">In this tutorial, your template folder is located at _working\templates\extensions\\_.</span></span>

<span data-ttu-id="8efb9-140">Bir şablonu oluşturduğunuzda, tüm dosya ve klasörlerin şablon klasöründe özel yapılandırma klasörü dışında şablonun parçası olarak dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="8efb9-140">When you create a template, all files and folders in the template folder are included as part of the template except for the special config folder.</span></span> <span data-ttu-id="8efb9-141">Bu yapılandırma klasörü adlı _. template.config_.</span><span class="sxs-lookup"><span data-stu-id="8efb9-141">This config folder is named _.template.config_.</span></span>

<span data-ttu-id="8efb9-142">İlk olarak, adlı yeni bir alt klasör oluşturun _. template.config_, girin.</span><span class="sxs-lookup"><span data-stu-id="8efb9-142">First, create a new subfolder named _.template.config_, enter it.</span></span> <span data-ttu-id="8efb9-143">Adlı yeni bir dosya oluşturup _template.json_.</span><span class="sxs-lookup"><span data-stu-id="8efb9-143">Then, create a new file named _template.json_.</span></span> <span data-ttu-id="8efb9-144">Klasör yapınız gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="8efb9-144">Your folder structure should look like this:</span></span>

```console
working
└───templates
    └───extensions
        └───.template.config
                template.json
```

<span data-ttu-id="8efb9-145">Açık _template.json_ , sık kullandığınız metin düzenleyicisi ve Yapıştır aşağıdaki JSON kod ve kaydedin:</span><span class="sxs-lookup"><span data-stu-id="8efb9-145">Open the _template.json_ with your favorite text editor and paste in the following JSON code and save it:</span></span>

```json
{
  "$schema": "http://json.schemastore.org/template",
  "author": "Me",
  "classifications": [ "Common", "Code" ],
  "identity": "ExampleTemplate.StringExtensions",
  "name": "Example templates: string extensions",
  "shortName": "stringext",
  "tags": {
    "language": "C#",
    "type": "item"
  }
}
```

<span data-ttu-id="8efb9-146">Bu yapılandırma dosyası şablonunuz için tüm ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="8efb9-146">This config file contains all the settings for your template.</span></span> <span data-ttu-id="8efb9-147">Temel ayarlar gibi görebilirsiniz `name` ve `shortName`, ancak aynı zamanda bir `tags/type` ayarlanan değer `item`.</span><span class="sxs-lookup"><span data-stu-id="8efb9-147">You can see the basic settings, such as `name` and `shortName`, but there's also a `tags/type` value that is set to `item`.</span></span> <span data-ttu-id="8efb9-148">Bu şablon bir öğe şablonu kategorilere ayırır.</span><span class="sxs-lookup"><span data-stu-id="8efb9-148">This categorizes your template as an item template.</span></span> <span data-ttu-id="8efb9-149">Oluşturduğunuz şablonun türüyle ilgili bir kısıtlama yoktur.</span><span class="sxs-lookup"><span data-stu-id="8efb9-149">There's no restriction on the type of template you create.</span></span> <span data-ttu-id="8efb9-150">`item` Ve `project` değerler için yaygın olarak kullanılan adları .NET Core önerir ve böylece kullanıcılar bunlar aramakta olduğunuz şablon türü kolayca filtre uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8efb9-150">The `item` and `project` values are common names that .NET Core recommends so that users can easily filter the type of template they're searching for.</span></span>

<span data-ttu-id="8efb9-151">`classifications` Öğesini temsil eder **etiketleri** gördüğünüz çalıştırdığınızda sütun `dotnet new` ve şablon listesini alın.</span><span class="sxs-lookup"><span data-stu-id="8efb9-151">The `classifications` item represents the **tags** column you see when you run `dotnet new` and get a list of templates.</span></span> <span data-ttu-id="8efb9-152">Kullanıcılar ayrıca arayabilirler tabanlı sınıflandırma etiketleri.</span><span class="sxs-lookup"><span data-stu-id="8efb9-152">Users can also search based on classification tags.</span></span> <span data-ttu-id="8efb9-153">Karıştırmayın `tags` özelliğinde \*.json dosyasını `classifications` Etiketler listesi.</span><span class="sxs-lookup"><span data-stu-id="8efb9-153">Don't confuse the `tags` property in the \*.json file with the `classifications` tags list.</span></span> <span data-ttu-id="8efb9-154">Ne yazık ki benzer şekilde adlı iki terimin farklı anlamlara oldukları.</span><span class="sxs-lookup"><span data-stu-id="8efb9-154">They're two different things unfortunately named similarly.</span></span> <span data-ttu-id="8efb9-155">İçin tam şema *template.json* dosya konumunda bulundu [JSON şema Store](http://json.schemastore.org/template).</span><span class="sxs-lookup"><span data-stu-id="8efb9-155">The full schema for the *template.json* file is found at the [JSON Schema Store](http://json.schemastore.org/template).</span></span> <span data-ttu-id="8efb9-156">Hakkında daha fazla bilgi için *template.json* bkz [dotnet şablon wiki](https://github.com/dotnet/templating/wiki).</span><span class="sxs-lookup"><span data-stu-id="8efb9-156">For more information about the *template.json* file, see the [dotnet templating wiki](https://github.com/dotnet/templating/wiki).</span></span>

<span data-ttu-id="8efb9-157">Geçerli bir sahip olduğunuza göre _.template.config/template.json_ dosya, şablonunuzu yüklenmeye hazır.</span><span class="sxs-lookup"><span data-stu-id="8efb9-157">Now that you have a valid _.template.config/template.json_ file, your template is ready to be installed.</span></span> <span data-ttu-id="8efb9-158">Terminalinizde gidin _uzantıları_ klasör ve şablon yüklemek için aşağıdaki komutu, geçerli klasörde bulunan çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="8efb9-158">In your terminal, navigate to the  _extensions_ folder and run the following command to install the template located at the current folder:</span></span>

* <span data-ttu-id="8efb9-159">**Windows üzerinde**: `dotnet new -i .\`</span><span class="sxs-lookup"><span data-stu-id="8efb9-159">**On Windows**: `dotnet new -i .\`</span></span>
* <span data-ttu-id="8efb9-160">**Linux veya macOS üzerinde**: `dotnet new -i ./`</span><span class="sxs-lookup"><span data-stu-id="8efb9-160">**On Linux or macOS**: `dotnet new -i ./`</span></span>

<span data-ttu-id="8efb9-161">Bu komut sizin kapsamalıdır yüklü şablonlar listesinden çıkarır.</span><span class="sxs-lookup"><span data-stu-id="8efb9-161">This command outputs the list of templates installed, which should include yours.</span></span>

```console
C:\working\templates\extensions> dotnet new -i .\
Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.

... cut to save space ...

Templates                                         Short Name            Language          Tags
-------------------------------------------------------------------------------------------------------------------------------
Example templates: string extensions              stringext             [C#]              Common/Code
Console Application                               console               [C#], F#, VB      Common/Console
Class library                                     classlib              [C#], F#, VB      Common/Library
WPF Application                                   wpf                   [C#], VB          Common/WPF
Windows Forms (WinForms) Application              winforms              [C#], VB          Common/WinForms
Worker Service                                    worker                [C#]              Common/Worker/Web
```

## <a name="test-the-item-template"></a><span data-ttu-id="8efb9-162">Öğe şablonunda test</span><span class="sxs-lookup"><span data-stu-id="8efb9-162">Test the item template</span></span>

<span data-ttu-id="8efb9-163">Yüklü bir öğe şablonunu olduğuna göre test edin.</span><span class="sxs-lookup"><span data-stu-id="8efb9-163">Now that you have an item template installed, test it.</span></span> <span data-ttu-id="8efb9-164">Gidin _test /_ klasörü ile yeni bir konsol uygulaması oluşturup `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="8efb9-164">Navigate to the _test/_ folder and create a new console application with `dotnet new console`.</span></span> <span data-ttu-id="8efb9-165">Bu, kolayca test ile bir çalışma projenin oluşturduğu `dotnet run` komutu.</span><span class="sxs-lookup"><span data-stu-id="8efb9-165">This generates a working project you can easily test with the `dotnet run` command.</span></span>

```console
C:\test> dotnet new console
The template "Console Application" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on C:\test\test.csproj...
  Restore completed in 54.82 ms for C:\test\test.csproj.

Restore succeeded.
```

```console
C:\test> dotnet run
Hello World!
```

<span data-ttu-id="8efb9-166">Ardından, çalıştırma `dotnet new stringext` oluşturulacak _CommonExtensions.cs_ şablonundan.</span><span class="sxs-lookup"><span data-stu-id="8efb9-166">Next, run `dotnet new stringext` to generate the _CommonExtensions.cs_ from the template.</span></span>

```console
C:\test> dotnet new stringext
The template "Example templates: string extensions" was created successfully.
```

<span data-ttu-id="8efb9-167">Kodda değişiklik _Program.cs_ tersine çevirmek için `"Hello World"` şablon tarafından sağlanan genişletme yöntemi ile dize.</span><span class="sxs-lookup"><span data-stu-id="8efb9-167">Change the code in _Program.cs_ to reverse the `"Hello World"` string with the extension method provided by the template.</span></span>

```csharp
Console.WriteLine("Hello World!".Reverse());
```

<span data-ttu-id="8efb9-168">Programı yeniden çalıştırın ve sonuç ters çevrilir görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="8efb9-168">Run the program again and you'll see that the result is reversed.</span></span>

```console
C:\test> dotnet run
!dlroW olleH
```

<span data-ttu-id="8efb9-169">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="8efb9-169">Congratulations!</span></span> <span data-ttu-id="8efb9-170">Oluşturduğunuz ve .NET Core ile bir öğe şablonunu dağıtılmış.</span><span class="sxs-lookup"><span data-stu-id="8efb9-170">You created and deployed an item template with .NET Core.</span></span> <span data-ttu-id="8efb9-171">Bu öğretici serisinin bir sonraki bölümü için hazırlanırken oluşturduğunuz şablonu kaldırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8efb9-171">In preparation for the next part of this tutorial series, you must uninstall the template you created.</span></span> <span data-ttu-id="8efb9-172">Tüm dosyaları silmek istediğinizden emin olun _test_ klasörü çok.</span><span class="sxs-lookup"><span data-stu-id="8efb9-172">Make sure to delete all files from the _test_ folder too.</span></span> <span data-ttu-id="8efb9-173">Bununla geri temiz bir duruma hazır için bu öğreticinin sonraki ana bölüme sahip olursunuz.</span><span class="sxs-lookup"><span data-stu-id="8efb9-173">This will get you back to a clean state ready for the next major section of this tutorial.</span></span>

## <a name="uninstall-the-template"></a><span data-ttu-id="8efb9-174">Şablonu Kaldır</span><span class="sxs-lookup"><span data-stu-id="8efb9-174">Uninstall the template</span></span>

<span data-ttu-id="8efb9-175">Şablon dosyası yolu tarafından yüklü olduğundan, birlikte kaldırmalısınız **mutlak** dosya yolu.</span><span class="sxs-lookup"><span data-stu-id="8efb9-175">Because you installed the template by file path, you must uninstall it with the **absolute** file path.</span></span> <span data-ttu-id="8efb9-176">Çalıştırarak yüklü şablonlar listesi gördüğünüz `dotnet new -u` komutu.</span><span class="sxs-lookup"><span data-stu-id="8efb9-176">You can see a list of templates installed by running the `dotnet new -u` command.</span></span> <span data-ttu-id="8efb9-177">Şablonunuzu son listelenmelidir.</span><span class="sxs-lookup"><span data-stu-id="8efb9-177">Your template should be listed last.</span></span> <span data-ttu-id="8efb9-178">Yolun listelenen şablonunuzla birlikte kaldırmak için kullanımı `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` komutu.</span><span class="sxs-lookup"><span data-stu-id="8efb9-178">Use the path listed to uninstall your template with the `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` command.</span></span>

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
  C:\working\templates\extensions
    Templates:
      Example templates: string extensions (stringext) C#
```

```console
C:\working> dotnet new -u C:\working\templates\extensions
```

## <a name="next-steps"></a><span data-ttu-id="8efb9-179">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="8efb9-179">Next steps</span></span>

<span data-ttu-id="8efb9-180">Bu öğreticide, bir öğe şablonu oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="8efb9-180">In this tutorial, you created an item template.</span></span> <span data-ttu-id="8efb9-181">Bu öğretici serisinin devam proje şablonu oluşturmayı öğrenin.</span><span class="sxs-lookup"><span data-stu-id="8efb9-181">To learn how to create a project template, continue this tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8efb9-182">Bir proje şablonu oluşturma</span><span class="sxs-lookup"><span data-stu-id="8efb9-182">Create a project template</span></span>](cli-templates-create-project-template.md)
