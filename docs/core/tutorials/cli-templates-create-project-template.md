---
title: DotNet New için bir proje şablonu oluşturun
description: DotNet New komutu için bir proje şablonu oluşturmayı öğrenin.
author: adegeo
ms.date: 12/11/2020
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: ed40cfd303c70c7b8f198a0f5b593bf1e1ebeaf8
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97513139"
---
# <a name="tutorial-create-a-project-template"></a><span data-ttu-id="40e60-103">Öğretici: proje şablonu oluşturma</span><span class="sxs-lookup"><span data-stu-id="40e60-103">Tutorial: Create a project template</span></span>

<span data-ttu-id="40e60-104">.NET ile, projeler, dosyalar ve hatta kaynaklar üreten şablonlar oluşturabilir ve dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="40e60-104">With .NET, you can create and deploy templates that generate projects, files, even resources.</span></span> <span data-ttu-id="40e60-105">Bu öğretici, komutuyla kullanılmak üzere şablonlar oluşturmayı, yüklemeyi ve kaldırmayı öğretir `dotnet new` .</span><span class="sxs-lookup"><span data-stu-id="40e60-105">This tutorial is part two of a series that teaches you how to create, install, and uninstall, templates for use with the `dotnet new` command.</span></span>

<span data-ttu-id="40e60-106">Serinin bu bölümünde şunları nasıl yapacağınızı öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="40e60-106">In this part of the series you'll learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="40e60-107">Proje şablonunun kaynaklarını oluşturma</span><span class="sxs-lookup"><span data-stu-id="40e60-107">Create the resources of a project template</span></span>
> * <span data-ttu-id="40e60-108">Şablon yapılandırma klasörünü ve dosyasını oluşturma</span><span class="sxs-lookup"><span data-stu-id="40e60-108">Create the template config folder and file</span></span>
> * <span data-ttu-id="40e60-109">Dosya yolundan şablon yükler</span><span class="sxs-lookup"><span data-stu-id="40e60-109">Install a template from a file path</span></span>
> * <span data-ttu-id="40e60-110">Bir öğe şablonunu test etme</span><span class="sxs-lookup"><span data-stu-id="40e60-110">Test an item template</span></span>
> * <span data-ttu-id="40e60-111">Öğe şablonunu kaldırma</span><span class="sxs-lookup"><span data-stu-id="40e60-111">Uninstall an item template</span></span>

## <a name="prerequisites"></a><span data-ttu-id="40e60-112">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="40e60-112">Prerequisites</span></span>

* <span data-ttu-id="40e60-113">Bu öğretici serisinin [1. bölümünü](cli-templates-create-item-template.md) doldurun.</span><span class="sxs-lookup"><span data-stu-id="40e60-113">Complete [part 1](cli-templates-create-item-template.md) of this tutorial series.</span></span>
* <span data-ttu-id="40e60-114">Bir Terminal açın ve _working\templates_ klasörüne gidin.</span><span class="sxs-lookup"><span data-stu-id="40e60-114">Open a terminal and navigate to the _working\templates_ folder.</span></span>

## <a name="create-a-project-template"></a><span data-ttu-id="40e60-115">Proje şablonu oluşturma</span><span class="sxs-lookup"><span data-stu-id="40e60-115">Create a project template</span></span>

<span data-ttu-id="40e60-116">Proje şablonları, kullanıcıların çalışan bir kod kümesiyle başlamasını kolaylaştıran, çalıştırmaya yönelik olarak çalışan projeler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="40e60-116">Project templates produce ready-to-run projects that make it easy for users to start with a working set of code.</span></span> <span data-ttu-id="40e60-117">.NET, konsol uygulaması veya sınıf kitaplığı gibi bazı proje şablonları içerir.</span><span class="sxs-lookup"><span data-stu-id="40e60-117">.NET includes a few project templates such as a console application or a class library.</span></span> <span data-ttu-id="40e60-118">Bu örnekte, C# 9,0 ' i sağlayan ve bir giriş noktası üreten yeni bir konsol projesi oluşturacaksınız `async main` .</span><span class="sxs-lookup"><span data-stu-id="40e60-118">In this example, you'll create a new console project that enables C# 9.0 and produces an `async main` entry point.</span></span>

<span data-ttu-id="40e60-119">Terminalinizde, _working\templates_ klasörüne gidin ve _consoleasync_ adlı yeni bir alt klasör oluşturun.</span><span class="sxs-lookup"><span data-stu-id="40e60-119">In your terminal, navigate to the _working\templates_ folder and create a new subfolder named _consoleasync_.</span></span> <span data-ttu-id="40e60-120">`dotnet new console`Standart konsol uygulamasını oluşturmak için alt klasörü girin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="40e60-120">Enter the subfolder and run `dotnet new console` to generate the standard console application.</span></span> <span data-ttu-id="40e60-121">Bu şablon tarafından oluşturulan dosyaları düzenleyerek yeni bir şablon oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="40e60-121">You'll be editing the files produced by this template to create a new template.</span></span>

```console
working
└───templates
    └───consoleasync
            consoleasync.csproj
            Program.cs
```

## <a name="modify-programcs"></a><span data-ttu-id="40e60-122">Program.cs Değiştir</span><span class="sxs-lookup"><span data-stu-id="40e60-122">Modify Program.cs</span></span>

<span data-ttu-id="40e60-123">_Program.cs_ dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="40e60-123">Open up the _program.cs_ file.</span></span> <span data-ttu-id="40e60-124">Konsol projesi zaman uyumsuz bir giriş noktası kullanmaz, bu nedenle bunu ekleyelim.</span><span class="sxs-lookup"><span data-stu-id="40e60-124">The console project doesn't use an asynchronous entry point, so let's add that.</span></span> <span data-ttu-id="40e60-125">Kodunuzu aşağıdaki şekilde değiştirin ve dosyayı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="40e60-125">Change your code to the following and save the file.</span></span>

```csharp
using System;
using System.Threading.Tasks;

namespace consoleasync
{
    class Program
    {
        static async Task Main(string[] args)
        {
            await Console.Out.WriteAsync("Hello World with C# 9.0!");
        }
    }
}
```

## <a name="modify-consoleasynccsproj"></a><span data-ttu-id="40e60-126">Consoleasync. csproj öğesini Değiştir</span><span class="sxs-lookup"><span data-stu-id="40e60-126">Modify consoleasync.csproj</span></span>

<span data-ttu-id="40e60-127">Projenin 9,0 sürümüne kullandığı C# dil sürümünü güncelleştirelim.</span><span class="sxs-lookup"><span data-stu-id="40e60-127">Let's update the C# language version the project uses to version 9.0.</span></span> <span data-ttu-id="40e60-128">_Consoleasync. csproj_ dosyasını düzenleyin ve `<LangVersion>` ayarı bir `<PropertyGroup>` düğüme ekleyin.</span><span class="sxs-lookup"><span data-stu-id="40e60-128">Edit the _consoleasync.csproj_ file and add the `<LangVersion>` setting to a `<PropertyGroup>` node.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net5.0</TargetFramework>

    <LangVersion>9.0</LangVersion>

  </PropertyGroup>
  
</Project>
```

## <a name="build-the-project"></a><span data-ttu-id="40e60-129">Projeyi derleme</span><span class="sxs-lookup"><span data-stu-id="40e60-129">Build the project</span></span>

<span data-ttu-id="40e60-130">Bir proje şablonunu tamamlamadan önce, derlendiğinden ve düzgün çalıştığından emin olmak için test etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="40e60-130">Before you complete a project template, you should test it to make sure it compiles and runs correctly.</span></span>

<span data-ttu-id="40e60-131">Terminalinizde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="40e60-131">In your terminal, run the following command.</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="40e60-132">Aşağıdaki çıktıyı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="40e60-132">You get the following output.</span></span>

```console
Hello World with C# 9.0!
```

<span data-ttu-id="40e60-133">Kullanılarak oluşturulan _obj_ ve _bin_ klasörlerini silebilirsiniz `dotnet run` .</span><span class="sxs-lookup"><span data-stu-id="40e60-133">You can delete the _obj_ and _bin_ folders created by using `dotnet run`.</span></span> <span data-ttu-id="40e60-134">Bu dosyaların silinmesi, şablonunuzun yalnızca şablonlarınız ile ilgili dosyaları ve bir yapı eyleminden kaynaklanan hiçbir dosyayı içerdiğini sağlar.</span><span class="sxs-lookup"><span data-stu-id="40e60-134">Deleting these files ensures your template only includes the files related to your template and not any files that result from a build action.</span></span>

<span data-ttu-id="40e60-135">Artık oluşturulan şablonun içeriğine sahip olduğunuza göre, şablonun kök klasöründe şablon yapılandırmasını oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="40e60-135">Now that you have the content of the template created, you need to create the template config at the root folder of the template.</span></span>

## <a name="create-the-template-config"></a><span data-ttu-id="40e60-136">Şablon yapılandırması oluşturma</span><span class="sxs-lookup"><span data-stu-id="40e60-136">Create the template config</span></span>

<span data-ttu-id="40e60-137">Şablonlar, .NET 'te şablonunuzun kökünde bulunan özel bir klasör ve yapılandırma dosyası tarafından tanınır.</span><span class="sxs-lookup"><span data-stu-id="40e60-137">Templates are recognized in .NET by a special folder and config file that exist at the root of your template.</span></span> <span data-ttu-id="40e60-138">Bu öğreticide, şablon klasörünüz _working\templates\consoleasync_ adresinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="40e60-138">In this tutorial, your template folder is located at _working\templates\consoleasync_.</span></span>

<span data-ttu-id="40e60-139">Bir şablon oluşturduğunuzda, şablon klasöründeki tüm dosyalar ve klasörler, özel yapılandırma klasörü hariç, şablonun bir parçası olarak dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="40e60-139">When you create a template, all files and folders in the template folder are included as part of the template except for the special config folder.</span></span> <span data-ttu-id="40e60-140">Bu yapılandırma klasörü _.template.config_ olarak adlandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="40e60-140">This config folder is named _.template.config_.</span></span>

<span data-ttu-id="40e60-141">İlk olarak, _.template.config_ adlı yeni bir alt klasör oluşturun, girin.</span><span class="sxs-lookup"><span data-stu-id="40e60-141">First, create a new subfolder named _.template.config_, enter it.</span></span> <span data-ttu-id="40e60-142">Ardından, _üzerindetemplate.js_ adlı yeni bir dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="40e60-142">Then, create a new file named _template.json_.</span></span> <span data-ttu-id="40e60-143">Klasör yapınız şöyle görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="40e60-143">Your folder structure should look like this.</span></span>

```console
working
└───templates
    └───consoleasync
        └───.template.config
                template.json
```

<span data-ttu-id="40e60-144">En sevdiğiniz metin düzenleyicinizle birlikte _template.js_ açın ve aşağıdaki JSON kodunu yapıştırın ve kaydedin.</span><span class="sxs-lookup"><span data-stu-id="40e60-144">Open the _template.json_ with your favorite text editor and paste in the following json code and save it.</span></span>

```json
{
  "$schema": "http://json.schemastore.org/template",
  "author": "Me",
  "classifications": [ "Common", "Console", "C#9" ],
  "identity": "ExampleTemplate.AsyncProject",
  "name": "Example templates: async project",
  "shortName": "consoleasync",
  "tags": {
    "language": "C#",
    "type": "project"
  }
}
```

<span data-ttu-id="40e60-145">Bu yapılandırma dosyası şablonunuz için tüm ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="40e60-145">This config file contains all of the settings for your template.</span></span> <span data-ttu-id="40e60-146">Ve gibi temel ayarları görebilir, ancak olarak `name` `shortName` ayarlanmış bir değer de vardır `tags/type` `project` .</span><span class="sxs-lookup"><span data-stu-id="40e60-146">You can see the basic settings such as `name` and `shortName` but also there's a `tags/type` value that's set to `project`.</span></span> <span data-ttu-id="40e60-147">Bu, şablonunuzu bir proje şablonu olarak belirler.</span><span class="sxs-lookup"><span data-stu-id="40e60-147">This designates your template as a project template.</span></span> <span data-ttu-id="40e60-148">Oluşturduğunuz şablon türü üzerinde hiçbir kısıtlama yoktur.</span><span class="sxs-lookup"><span data-stu-id="40e60-148">There's no restriction on the type of template you create.</span></span> <span data-ttu-id="40e60-149">`item`Ve `project` değerleri, kullanıcıların aradıkları şablonun türünü kolayca filtreleyebilmesi için .NET tarafından önerilen yaygın adlardır.</span><span class="sxs-lookup"><span data-stu-id="40e60-149">The `item` and `project` values are common names that .NET recommends so that users can easily filter the type of template they're searching for.</span></span>

<span data-ttu-id="40e60-150">`classifications`Öğe,  çalıştırdığınız `dotnet new` ve bir şablon listesi alırken gördüğünüz Etiketler sütununu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="40e60-150">The `classifications` item represents the **tags** column you see when you run `dotnet new` and get a list of templates.</span></span> <span data-ttu-id="40e60-151">Kullanıcılar ayrıca sınıflandırma etiketlerine göre arama yapabilir.</span><span class="sxs-lookup"><span data-stu-id="40e60-151">Users can also search based on classification tags.</span></span> <span data-ttu-id="40e60-152">`tags`JSON dosyasındaki özelliği `classifications` Etiketler listesiyle karıştırmayın.</span><span class="sxs-lookup"><span data-stu-id="40e60-152">Don't confuse the `tags` property in the json file with the `classifications` tags list.</span></span> <span data-ttu-id="40e60-153">Benzer şekilde adlandırılan iki farklı şey vardır.</span><span class="sxs-lookup"><span data-stu-id="40e60-153">They're two different things unfortunately named similarly.</span></span> <span data-ttu-id="40e60-154">Dosyadaki *template.js* tam şeması [JSON Şema deposunda](http://json.schemastore.org/template)bulunur.</span><span class="sxs-lookup"><span data-stu-id="40e60-154">The full schema for the *template.json* file is found at the [JSON Schema Store](http://json.schemastore.org/template).</span></span> <span data-ttu-id="40e60-155">Dosyadaki *template.js* hakkında daha fazla bilgi için bkz. [DotNet şablon oluşturma wiki](https://github.com/dotnet/templating/wiki).</span><span class="sxs-lookup"><span data-stu-id="40e60-155">For more information about the *template.json* file, see the [dotnet templating wiki](https://github.com/dotnet/templating/wiki).</span></span>

<span data-ttu-id="40e60-156">Artık dosyada geçerli bir _.template.config/template.jsolduğuna göre_ şablonunuz yüklenmeye hazırdır.</span><span class="sxs-lookup"><span data-stu-id="40e60-156">Now that you have a valid _.template.config/template.json_ file, your template is ready to be installed.</span></span> <span data-ttu-id="40e60-157">Şablonu yüklemeden önce, _küme_ veya _obj_ klasörleri gibi şablonunuzda yer almasını istemediğiniz ek dosya klasörlerini ve dosyalarını sildiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="40e60-157">Before you install the template, make sure that you delete any extra files folders and files you don't want included in your template, like the _bin_ or _obj_ folders.</span></span> <span data-ttu-id="40e60-158">Terminalinizde _consoleasync_ klasörüne gidin ve `dotnet new -i .\` geçerli klasörde bulunan şablonu yüklemek için öğesini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="40e60-158">In your terminal, navigate to the _consoleasync_ folder and run `dotnet new -i .\` to install the template located at the current folder.</span></span> <span data-ttu-id="40e60-159">Linux veya macOS işletim sistemi kullanıyorsanız, eğik çizgi kullanın: `dotnet new -i ./` .</span><span class="sxs-lookup"><span data-stu-id="40e60-159">If you're using a Linux or macOS operating system, use a forward slash: `dotnet new -i ./`.</span></span>

<span data-ttu-id="40e60-160">Bu komut, yüklenmiş şablonların listesini verir ve bunları içermelidir.</span><span class="sxs-lookup"><span data-stu-id="40e60-160">This command outputs the list of templates installed, which should include yours.</span></span>

```dotnetcli
dotnet new -i .\
```

<span data-ttu-id="40e60-161">Aşağıdakine benzer bir çıktı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="40e60-161">You get output similar to the following.</span></span>

```console
Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.

... cut to save space ...

Templates                                         Short Name               Language          Tags
--------------------------------------------      -------------------      ------------      ----------------------
Console Application                               console                  [C#], F#, VB      Common/Console
Example templates: async project                  consoleasync             [C#]              Common/Console/C#9
Class library                                     classlib                 [C#], F#, VB      Common/Library
WPF Application                                   wpf                      [C#], VB          Common/WPF
```

### <a name="test-the-project-template"></a><span data-ttu-id="40e60-162">Proje şablonunu test etme</span><span class="sxs-lookup"><span data-stu-id="40e60-162">Test the project template</span></span>

<span data-ttu-id="40e60-163">Artık yüklü bir proje şablonunuz olduğuna göre, test edin.</span><span class="sxs-lookup"><span data-stu-id="40e60-163">Now that you have a project template installed, test it.</span></span>

1. <span data-ttu-id="40e60-164">_Test_ klasörüne git</span><span class="sxs-lookup"><span data-stu-id="40e60-164">Navigate to the _test_ folder</span></span>

1. <span data-ttu-id="40e60-165">Komut ile kolayca test edebileceğiniz, çalışan bir proje üreten aşağıdaki komutla yeni bir konsol uygulaması oluşturun `dotnet run` .</span><span class="sxs-lookup"><span data-stu-id="40e60-165">Create a new console application with the following command which generates a working project you can easily test with the `dotnet run` command.</span></span>

    ```dotnetcli
    dotnet new consoleasync
    ```

    <span data-ttu-id="40e60-166">Aşağıdaki çıktıyı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="40e60-166">You get the following output.</span></span>

    ```console
    The template "Example templates: async project" was created successfully.
    ```

1. <span data-ttu-id="40e60-167">Aşağıdaki komutu kullanarak projeyi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="40e60-167">Run the project using the following command.</span></span>

    ```dotnetcli
    dotnet run
    ```

    <span data-ttu-id="40e60-168">Aşağıdaki çıktıyı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="40e60-168">You get the following output.</span></span>

    ```console
    Hello World with C# 9.0!
    ```

<span data-ttu-id="40e60-169">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="40e60-169">Congratulations!</span></span> <span data-ttu-id="40e60-170">.NET ile bir proje şablonu oluşturdunuz ve dağıttıysanız.</span><span class="sxs-lookup"><span data-stu-id="40e60-170">You created and deployed a project template with .NET.</span></span> <span data-ttu-id="40e60-171">Bu öğretici serisinin bir sonraki kısmına hazırlanın, oluşturduğunuz şablonu kaldırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="40e60-171">In preparation for the next part of this tutorial series, you must uninstall the template you created.</span></span> <span data-ttu-id="40e60-172">Tüm dosyaları da _Test_ klasöründen sildiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="40e60-172">Make sure to delete all files from the _test_ folder too.</span></span> <span data-ttu-id="40e60-173">Bu, Bu öğreticinin bir sonraki ana kısmına yönelik temiz bir duruma geri dönebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="40e60-173">This will get you back to a clean state ready for the next major section of this tutorial.</span></span>

### <a name="uninstall-the-template"></a><span data-ttu-id="40e60-174">Şablonu kaldırma</span><span class="sxs-lookup"><span data-stu-id="40e60-174">Uninstall the template</span></span>

<span data-ttu-id="40e60-175">Şablonu bir dosya yolu kullanarak yükletiğinden, **mutlak** dosya yoluyla kaldırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="40e60-175">Because you installed the template by using a file path, you must uninstall it with the **absolute** file path.</span></span> <span data-ttu-id="40e60-176">Komutunu çalıştırarak, yüklenmiş şablonların bir listesini görebilirsiniz `dotnet new -u` .</span><span class="sxs-lookup"><span data-stu-id="40e60-176">You can see a list of templates installed by running the `dotnet new -u` command.</span></span> <span data-ttu-id="40e60-177">Şablonunuzun son listelenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="40e60-177">Your template should be listed last.</span></span> <span data-ttu-id="40e60-178">`Uninstall Command`Şablonunuzu kaldırmak için listelenmiş ' i kullanın.</span><span class="sxs-lookup"><span data-stu-id="40e60-178">Use the `Uninstall Command` listed to uninstall your template.</span></span>

```dotnetcli
dotnet new -u
```

<span data-ttu-id="40e60-179">Aşağıdakine benzer bir çıktı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="40e60-179">You get output similar to the following.</span></span>

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

  C:\Test\templatetutorial\working\templates\consoleasync
    Templates:
      Example templates: async project (consoleasync) C#
    Uninstall Command:
      dotnet new -u C:\working\templates\consoleasync
```

<span data-ttu-id="40e60-180">Oluşturduğunuz şablonu kaldırmak için `Uninstall Command` çıktıda gösterilen öğesini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="40e60-180">To uninstall the template that you created, run the `Uninstall Command` that is shown in the output.</span></span>

```dotnetcli
dotnet new -u C:\working\templates\consoleasync
```

## <a name="next-steps"></a><span data-ttu-id="40e60-181">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="40e60-181">Next steps</span></span>

<span data-ttu-id="40e60-182">Bu öğreticide bir proje şablonu oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="40e60-182">In this tutorial, you created a project template.</span></span> <span data-ttu-id="40e60-183">Hem öğe hem de proje şablonlarının kullanımı kolay bir dosyaya nasıl paketleyeceğinizi öğrenmek için, bu öğretici serisine devam edin.</span><span class="sxs-lookup"><span data-stu-id="40e60-183">To learn how to package both the item and project templates into an easy-to-use file, continue this tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="40e60-184">Şablon paketi oluşturma</span><span class="sxs-lookup"><span data-stu-id="40e60-184">Create a template pack</span></span>](cli-templates-create-template-pack.md)
