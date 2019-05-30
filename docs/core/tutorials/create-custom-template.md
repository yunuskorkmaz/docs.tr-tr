---
title: Dotnet new için özel şablon oluşturma
description: Bu eğlenceli dotnet yeni komutu için özel bir şablon oluşturmayı öğrenin öğretici.
author: mairaw
ms.date: 08/12/2017
ms.custom: seodec18
ms.openlocfilehash: e47da048584ec31c275ff9c122d157f34556268a
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66299954"
---
# <a name="create-a-custom-template-for-dotnet-new"></a><span data-ttu-id="1982e-103">Dotnet new için özel şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="1982e-103">Create a custom template for dotnet new</span></span>

<span data-ttu-id="1982e-104">Bu öğretici, nasıl gösterir için:</span><span class="sxs-lookup"><span data-stu-id="1982e-104">This tutorial shows you how to:</span></span>

- <span data-ttu-id="1982e-105">Bir temel şablon, var olan bir proje veya yeni bir konsol uygulama projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1982e-105">Create a basic template from an existing project or a new console app project.</span></span>
- <span data-ttu-id="1982e-106">Nuget.org veya yerel bir dağıtım için bir şablon paketi *nupkg* dosya.</span><span class="sxs-lookup"><span data-stu-id="1982e-106">Pack the template for distribution at nuget.org or from a local *nupkg* file.</span></span>
- <span data-ttu-id="1982e-107">Şablon yerel nuget.org adresinden yükleyin *nupkg* dosya ya da yerel dosya sistemi.</span><span class="sxs-lookup"><span data-stu-id="1982e-107">Install the template from nuget.org, a local *nupkg* file, or the local file system.</span></span>
- <span data-ttu-id="1982e-108">Şablon kaldırın.</span><span class="sxs-lookup"><span data-stu-id="1982e-108">Uninstall the template.</span></span>

<span data-ttu-id="1982e-109">Bu öğreticide eksiksiz bir örnek ile devam etmek isterseniz, indirme [örnek proje şablonu](https://github.com/dotnet/dotnet-template-samples/tree/master/16-nuget-package).</span><span class="sxs-lookup"><span data-stu-id="1982e-109">If you prefer to proceed through the tutorial with a complete sample, download the [sample project template](https://github.com/dotnet/dotnet-template-samples/tree/master/16-nuget-package).</span></span> <span data-ttu-id="1982e-110">Örnek şablonu, NuGet dağıtımı için yapılandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="1982e-110">The sample template is configured for NuGet distribution.</span></span>

<span data-ttu-id="1982e-111">Dosya sistemi dağıtımı ile indirilen örnek kullanmak istiyorsanız, aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="1982e-111">If you wish to use the downloaded sample with file system distribution, do the following:</span></span>

- <span data-ttu-id="1982e-112">İçeriği Taşı *içeriği* klasörü örnek bir düzey yukarı *GarciaSoftware.ConsoleTemplate.CSharp* klasör.</span><span class="sxs-lookup"><span data-stu-id="1982e-112">Move the contents of the *content* folder of the sample up one level into the *GarciaSoftware.ConsoleTemplate.CSharp* folder.</span></span>
- <span data-ttu-id="1982e-113">Boş Sil *içeriği* klasör.</span><span class="sxs-lookup"><span data-stu-id="1982e-113">Delete the empty *content* folder.</span></span>
- <span data-ttu-id="1982e-114">Silme *nuspec* dosya.</span><span class="sxs-lookup"><span data-stu-id="1982e-114">Delete the *nuspec* file.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1982e-115">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="1982e-115">Prerequisites</span></span>

- <span data-ttu-id="1982e-116">Yükleme [.NET Core 2.0 SDK'sını](https://www.microsoft.com/net/core) veya sonraki sürümler.</span><span class="sxs-lookup"><span data-stu-id="1982e-116">Install the [.NET Core 2.0 SDK](https://www.microsoft.com/net/core) or later versions.</span></span>
- <span data-ttu-id="1982e-117">Başvuru konusu okuma [yeni dotnet için özel şablonları](../tools/custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="1982e-117">Read the reference topic [Custom templates for dotnet new](../tools/custom-templates.md).</span></span>

## <a name="create-a-template-from-a-project"></a><span data-ttu-id="1982e-118">Bir projeden bir şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="1982e-118">Create a template from a project</span></span>

<span data-ttu-id="1982e-119">Kullanımı, onayladıktan varolan bir projeyi derler ve çalıştırır veya sabit sürücünüzdeki bir klasöre yeni bir konsol uygulama projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1982e-119">Use an existing project that you've confirmed compiles and runs, or create a new console app project in a folder on your hard drive.</span></span> <span data-ttu-id="1982e-120">Bu öğreticide, proje klasörünün adı olduğunu varsayar *GarciaSoftware.ConsoleTemplate.CSharp* depolandığı *Documents\Templates* kullanıcının profilinde.</span><span class="sxs-lookup"><span data-stu-id="1982e-120">This tutorial assumes that the name of the project folder is *GarciaSoftware.ConsoleTemplate.CSharp* stored at *Documents\Templates* in the user's profile.</span></span> <span data-ttu-id="1982e-121">Öğretici projesinin şablon adı şu biçimdedir  *\<şirket adı >.\< Şablon türü >. \<Programlama dili >* , ancak projenizi ve şablon istediğiniz herhangi bir şey adı boş.</span><span class="sxs-lookup"><span data-stu-id="1982e-121">The tutorial project template name is in the format *\<Company Name>.\<Template Type>.\<Programming Language>*, but you're free to name your project and template anything you wish.</span></span>

1. <span data-ttu-id="1982e-122">Adlı proje kök dizinine bir klasör eklemek *. template.config*.</span><span class="sxs-lookup"><span data-stu-id="1982e-122">Add a folder to the root of the project named *.template.config*.</span></span>
1. <span data-ttu-id="1982e-123">İçinde *. template.config* klasör oluşturma bir *template.json* şablonunuzu yapılandırmak için bir dosya.</span><span class="sxs-lookup"><span data-stu-id="1982e-123">Inside the *.template.config* folder, create a *template.json* file to configure your template.</span></span> <span data-ttu-id="1982e-124">Daha fazla bilgi ve üye tanımları için *template.json* bkz [yeni dotnet için özel şablonları](../tools/custom-templates.md#templatejson) konu ve [ *template.json* JSON şema Store şema](http://json.schemastore.org/template).</span><span class="sxs-lookup"><span data-stu-id="1982e-124">For more information and member definitions for the *template.json* file, see the [Custom templates for dotnet new](../tools/custom-templates.md#templatejson) topic and the [*template.json* schema at the JSON Schema Store](http://json.schemastore.org/template).</span></span>

```json
{
    "$schema": "http://json.schemastore.org/template",
    "author": "Catalina Garcia",
    "classifications": [ "Common", "Console" ],
    "identity": "GarciaSoftware.ConsoleTemplate.CSharp",
    "name": "Garcia Software Console Application",
    "shortName": "garciaconsole"
}
```

<span data-ttu-id="1982e-125">Şablonu tamamladınız.</span><span class="sxs-lookup"><span data-stu-id="1982e-125">The template is finished.</span></span> <span data-ttu-id="1982e-126">Bu noktada, şablon dağıtımı için iki seçeneğiniz vardır.</span><span class="sxs-lookup"><span data-stu-id="1982e-126">At this point, you have two options for template distribution.</span></span> <span data-ttu-id="1982e-127">Bu öğreticiye devam etmek için bir yol ya da diğerini seçin:</span><span class="sxs-lookup"><span data-stu-id="1982e-127">To continue this tutorial, choose one path or the other:</span></span>

1. <span data-ttu-id="1982e-128">[NuGet dağıtım](#use-nuget-distribution): NuGet veya yerel şablonunu yüklemek *nupkg* dosya ve yüklü şablonu kullanın.</span><span class="sxs-lookup"><span data-stu-id="1982e-128">[NuGet distribution](#use-nuget-distribution): install the template from NuGet or from the local *nupkg* file, and use the installed template.</span></span>
2. <span data-ttu-id="1982e-129">[Dosya sistemi dağıtım](#use-file-system-distribution).</span><span class="sxs-lookup"><span data-stu-id="1982e-129">[File system distribution](#use-file-system-distribution).</span></span>

## <a name="use-nuget-distribution"></a><span data-ttu-id="1982e-130">NuGet dağıtım kullan</span><span class="sxs-lookup"><span data-stu-id="1982e-130">Use NuGet Distribution</span></span>

### <a name="pack-the-template-into-a-nuget-package"></a><span data-ttu-id="1982e-131">Şablon bir NuGet paketi</span><span class="sxs-lookup"><span data-stu-id="1982e-131">Pack the template into a NuGet package</span></span>

1. <span data-ttu-id="1982e-132">NuGet paketi için bir klasör oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1982e-132">Create a folder for the NuGet package.</span></span> <span data-ttu-id="1982e-133">Öğretici, klasör adı için *GarciaSoftware.ConsoleTemplate.CSharp* kullanılır, ve klasörü içinde oluşturulur bir *Documents\NuGetTemplates* kullanıcı profili klasöründe.</span><span class="sxs-lookup"><span data-stu-id="1982e-133">For the tutorial, the folder name *GarciaSoftware.ConsoleTemplate.CSharp* is used, and the folder is created inside a *Documents\NuGetTemplates* folder in the user's profile.</span></span> <span data-ttu-id="1982e-134">Adlı bir klasör oluşturun *içeriği* proje dosyalarını tutmak için yeni şablon klasörü içinde.</span><span class="sxs-lookup"><span data-stu-id="1982e-134">Create a folder named *content* inside of the new template folder to hold the project files.</span></span>
1. <span data-ttu-id="1982e-135">İle birlikte proje klasörünüzün içeriğini kopyalayın, *.template.config/template.json* dosyası içine *içeriği* oluşturduğunuz klasör.</span><span class="sxs-lookup"><span data-stu-id="1982e-135">Copy the contents of your project folder, together with its *.template.config/template.json* file, into the *content* folder you created.</span></span>
1. <span data-ttu-id="1982e-136">Yanındaki *içeriği* klasör ekleme bir [ *nuspec* dosya](/nuget/create-packages/creating-a-package).</span><span class="sxs-lookup"><span data-stu-id="1982e-136">Next to the *content* folder, add a [*nuspec* file](/nuget/create-packages/creating-a-package).</span></span> <span data-ttu-id="1982e-137">Soubor nuspec bir paket içeriğini açıklayan ve NuGet paketi oluşturma işlemlerini yöneten bir XML bildirimi dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="1982e-137">The nuspec file is an XML manifest file that describes a package's contents and drives the process of creating the NuGet package.</span></span>

   ![NuGet paketinin düzenini gösteren dizin yapısı](./media/create-custom-template/nuget-directory-layout.png)

1. <span data-ttu-id="1982e-139">İçinde bir  **\<packageTypes >** öğesinde *nuspec* dosya, içeren bir  **\<packageType >** öğesi ile bir `name` öznitelik değerini `Template`.</span><span class="sxs-lookup"><span data-stu-id="1982e-139">Inside of a **\<packageTypes>** element in the *nuspec* file, include a **\<packageType>** element with a `name` attribute value of `Template`.</span></span> <span data-ttu-id="1982e-140">Her iki *içeriği* klasörü ve *nuspec* dosya aynı dizinde bulunması.</span><span class="sxs-lookup"><span data-stu-id="1982e-140">Both the *content* folder and the *nuspec* file should reside in the same directory.</span></span> <span data-ttu-id="1982e-141">Tabloda, en düşük gösterilmiştir *nuspec* dosya şablon bir NuGet paketi olarak üretmek için gerekli öğeler.</span><span class="sxs-lookup"><span data-stu-id="1982e-141">The table shows the minimum *nuspec* file elements required to produce a template as a NuGet package.</span></span>

   | <span data-ttu-id="1982e-142">Öğe</span><span class="sxs-lookup"><span data-stu-id="1982e-142">Element</span></span>            | <span data-ttu-id="1982e-143">Tür</span><span class="sxs-lookup"><span data-stu-id="1982e-143">Type</span></span>   | <span data-ttu-id="1982e-144">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1982e-144">Description</span></span> |
   | ------------------ | ------ | ----------- |
   | <span data-ttu-id="1982e-145">**\<Yazarlar >**</span><span class="sxs-lookup"><span data-stu-id="1982e-145">**\<authors>**</span></span>     | <span data-ttu-id="1982e-146">dize</span><span class="sxs-lookup"><span data-stu-id="1982e-146">string</span></span> | <span data-ttu-id="1982e-147">Nuget.org profil adları eşleşen paketleri yazar, virgülle ayrılmış listesi. Yazarlar nuget.org NuGet galerisinde görüntülenir ve paketleri çapraz başvuru için aynı yazarları tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1982e-147">A comma-separated list of packages authors, matching the profile names on nuget.org. Authors are displayed in the NuGet Gallery on nuget.org and are used to cross-reference packages by the same authors.</span></span> |
   | <span data-ttu-id="1982e-148">**\<Açıklama >**</span><span class="sxs-lookup"><span data-stu-id="1982e-148">**\<description>**</span></span> | <span data-ttu-id="1982e-149">dize</span><span class="sxs-lookup"><span data-stu-id="1982e-149">string</span></span> | <span data-ttu-id="1982e-150">Kullanıcı Arabirimi ekranı için paketinin uzun açıklaması.</span><span class="sxs-lookup"><span data-stu-id="1982e-150">A long description of the package for UI display.</span></span> |
   | <span data-ttu-id="1982e-151">**\<Kimliği >**</span><span class="sxs-lookup"><span data-stu-id="1982e-151">**\<id>**</span></span>          | <span data-ttu-id="1982e-152">dize</span><span class="sxs-lookup"><span data-stu-id="1982e-152">string</span></span> | <span data-ttu-id="1982e-153">Nuget.org veya ne olursa olsun arasında benzersiz olması gereken büyük küçük harf duyarsız paket tanımlayıcısı galeri paketi bulunacağı.</span><span class="sxs-lookup"><span data-stu-id="1982e-153">The case-insensitive package identifier, which must be unique across nuget.org or whatever gallery the package will reside in.</span></span> <span data-ttu-id="1982e-154">Kimlikleri, boşluk veya bir URL için geçerli olmayan ve genellikle .NET ad alanı kurallarına karakterler içeremez.</span><span class="sxs-lookup"><span data-stu-id="1982e-154">IDs may not contain spaces or characters that are not valid for a URL and generally follow .NET namespace rules.</span></span> <span data-ttu-id="1982e-155">Bkz: [benzersiz paket tanımlayıcısı seçme ve sürüm numarasını ayarlama](/nuget/create-packages/creating-a-package#choosing-a-unique-package-identifier-and-setting-the-version-number) Kılavuzu.</span><span class="sxs-lookup"><span data-stu-id="1982e-155">See [Choosing a unique package identifier and setting the version number](/nuget/create-packages/creating-a-package#choosing-a-unique-package-identifier-and-setting-the-version-number) for guidance.</span></span> |
   | <span data-ttu-id="1982e-156">**\<packageType >**</span><span class="sxs-lookup"><span data-stu-id="1982e-156">**\<packageType>**</span></span> | <span data-ttu-id="1982e-157">dize</span><span class="sxs-lookup"><span data-stu-id="1982e-157">string</span></span> | <span data-ttu-id="1982e-158">Bu öğe içinde yerleştirileceği bir  **\<packageTypes >** öğesi arasında  **\<meta veri >** öğeleri.</span><span class="sxs-lookup"><span data-stu-id="1982e-158">Place this element inside a **\<packageTypes>** element among the **\<metadata>** elements.</span></span> <span data-ttu-id="1982e-159">Ayarlama `name` özniteliği  **\<packageType >** öğesine `Template`.</span><span class="sxs-lookup"><span data-stu-id="1982e-159">Set the `name` attribute of the **\<packageType>** element to `Template`.</span></span> |
   | <span data-ttu-id="1982e-160">**\<Sürüm >**</span><span class="sxs-lookup"><span data-stu-id="1982e-160">**\<version>**</span></span>     | <span data-ttu-id="1982e-161">dize</span><span class="sxs-lookup"><span data-stu-id="1982e-161">string</span></span> | <span data-ttu-id="1982e-162">Ana.İkincil.yama aşağıdaki Paket sürümü.</span><span class="sxs-lookup"><span data-stu-id="1982e-162">The version of the package, following the major.minor.patch pattern.</span></span> <span data-ttu-id="1982e-163">Sürüm numaraları, yayın öncesi son içerebilir, açıklandığı [yayın öncesi sürümleri](/nuget/create-packages/prerelease-packages#semantic-versioning).</span><span class="sxs-lookup"><span data-stu-id="1982e-163">Version numbers may include a pre-release suffix as described in [Pre-release versions](/nuget/create-packages/prerelease-packages#semantic-versioning).</span></span> |

   <span data-ttu-id="1982e-164">Bkz: [.nuspec başvuru](/nuget/schema/nuspec) tamamlanmış *nuspec* dosya şeması.</span><span class="sxs-lookup"><span data-stu-id="1982e-164">See the [.nuspec reference](/nuget/schema/nuspec) for the complete *nuspec* file schema.</span></span>

   <span data-ttu-id="1982e-165">*Nuspec* öğretici adlı dosya *GarciaSoftware.ConsoleTemplate.CSharp.nuspec* ve aşağıdaki içeriği içerir:</span><span class="sxs-lookup"><span data-stu-id="1982e-165">The *nuspec* file for the tutorial is named *GarciaSoftware.ConsoleTemplate.CSharp.nuspec* and contains the following content:</span></span>

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <package xmlns="http://schemas.microsoft.com/packaging/2012/06/nuspec.xsd">
     <metadata>
       <id>GarciaSoftware.ConsoleTemplate.CSharp</id>
       <version>1.0.0</version>
       <description>
         Creates the Garcia Software console app.
       </description>
       <authors>Catalina Garcia</authors>
       <packageTypes>
         <packageType name="Template" />
       </packageTypes>
     </metadata>
   </package>
   ```

1. <span data-ttu-id="1982e-166">[Paket oluşturma](/nuget/create-packages/creating-a-package#creating-the-package) kullanarak `nuget pack <PATH_TO_NUSPEC_FILE>` komutu.</span><span class="sxs-lookup"><span data-stu-id="1982e-166">[Create the package](/nuget/create-packages/creating-a-package#creating-the-package) using the `nuget pack <PATH_TO_NUSPEC_FILE>` command.</span></span> <span data-ttu-id="1982e-167">Aşağıdaki komutu NuGet varlıkları bulunduğu klasöre, olduğunu varsayar *C:\Users\\\<kullanıcı > \Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp*.</span><span class="sxs-lookup"><span data-stu-id="1982e-167">The following command assumes that the folder that holds the NuGet assets is at *C:\Users\\\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp*.</span></span> <span data-ttu-id="1982e-168">Ancak her yerde, sisteminizde klasörü yerleştirmek `nuget pack` komut yolu kabul *nuspec* dosyası:</span><span class="sxs-lookup"><span data-stu-id="1982e-168">But wherever you place the folder on your system, the `nuget pack` command accepts the path to the *nuspec* file:</span></span>

   ```console
   nuget pack C:\Users\<USER>\Documents\NuGetTemplates\GarciaSoftware.ConsoleTemplate.CSharp\GarciaSoftware.ConsoleTemplate.CSharp.nuspec
   ```

### <a name="publishing-the-package-to-nugetorg"></a><span data-ttu-id="1982e-169">Nuget.org için paket yayımlama</span><span class="sxs-lookup"><span data-stu-id="1982e-169">Publishing the package to nuget.org</span></span>

<span data-ttu-id="1982e-170">Bir NuGet paketi yayımlamak için yönergeleri izleyin. [oluşturun ve paket yayımlama](/nuget/quickstart/create-and-publish-a-package#publish-the-package) konu.</span><span class="sxs-lookup"><span data-stu-id="1982e-170">To publish a NuGet package, follow the instructions in the [Create and publish a package](/nuget/quickstart/create-and-publish-a-package#publish-the-package) topic.</span></span> <span data-ttu-id="1982e-171">Ancak, hiçbir zaman yayımlandıktan sonra yalnızca delisted silinebilir gibi öğretici şablonu için NuGet yayımlama öneririz.</span><span class="sxs-lookup"><span data-stu-id="1982e-171">However, we recommend that you don't publish the tutorial template to NuGet as it can never be deleted once published, only delisted.</span></span> <span data-ttu-id="1982e-172">NuGet paketi biçiminde olduğuna göre bir *nupkg* dosyası öneririz şablonu doğrudan yerel konumdan yüklemek için aşağıdaki yönergeleri izleyin *nupkg* dosya.</span><span class="sxs-lookup"><span data-stu-id="1982e-172">Now that you have the NuGet package in the form of a *nupkg* file, we suggest that you follow the instructions below to install the template directly from the local *nupkg* file.</span></span>

### <a name="install-the-template-from-a-nuget-package"></a><span data-ttu-id="1982e-173">Bir NuGet paketi şablonu yükleyin</span><span class="sxs-lookup"><span data-stu-id="1982e-173">Install the template from a NuGet package</span></span>

#### <a name="install-the-template-from-the-local-nupkg-file"></a><span data-ttu-id="1982e-174">Yerel konumdan şablonunu yüklemek *nupkg* dosyası</span><span class="sxs-lookup"><span data-stu-id="1982e-174">Install the template from the local *nupkg* file</span></span>

<span data-ttu-id="1982e-175">Şablondan yüklemek için *nupkg* , üretilen, dosya kullanım `dotnet new` komutunu `-i|--install` seçenek ve yolunu belirtin *nupkg* dosyası:</span><span class="sxs-lookup"><span data-stu-id="1982e-175">To install the template from the *nupkg* file that you produced, use the `dotnet new` command with the `-i|--install` option and provide the path to the *nupkg* file:</span></span>

```console
dotnet new -i C:\Users\<USER>\GarciaSoftware.ConsoleTemplate.CSharp.1.0.0.nupkg
```

#### <a name="install-the-template-from-a-nuget-package-stored-at-nugetorg"></a><span data-ttu-id="1982e-176">Nuget.org depolanan bir NuGet paketi şablonu yükleyin</span><span class="sxs-lookup"><span data-stu-id="1982e-176">Install the template from a NuGet package stored at nuget.org</span></span>

<span data-ttu-id="1982e-177">Bir şablon kullanım nuget.org depolanan bir NuGet paketinden yüklemek istiyorsanız `dotnet new` komutunu `-i|--install` seçeneği ve NuGet paketinin adını sağlayın:</span><span class="sxs-lookup"><span data-stu-id="1982e-177">If you wish to install a template from a NuGet package stored at nuget.org, use the `dotnet new` command with the `-i|--install` option and supply the name of the NuGet package:</span></span>

```console
dotnet new -i GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> <span data-ttu-id="1982e-178">Örnek yalnızca gösterim amaçlıdır.</span><span class="sxs-lookup"><span data-stu-id="1982e-178">The example is for demonstration purposes only.</span></span> <span data-ttu-id="1982e-179">Hiç bir `GarciaSoftware.ConsoleTemplate.CSharp` nuget.org, NuGet paketini ve yayımlama ve test şablonlardan NuGet kullanma önermemekteyiz.</span><span class="sxs-lookup"><span data-stu-id="1982e-179">There isn't a `GarciaSoftware.ConsoleTemplate.CSharp` NuGet package at nuget.org, and we don't recommend that you publish and consume test templates from NuGet.</span></span> <span data-ttu-id="1982e-180">Komutunu çalıştırın, hiçbir şablon yüklenir.</span><span class="sxs-lookup"><span data-stu-id="1982e-180">If you run the command, no template is installed.</span></span> <span data-ttu-id="1982e-181">Nuget.org için başvurarak yayımlanmadı bir şablon yükleyebilirsiniz ancak *nupkg* önceki bölümde gösterildiği gibi yerel dosya sisteminizde doğrudan dosya [yerel nupkg şablonu yükleme Dosya](#install-the-template-from-the-local-nupkg-file).</span><span class="sxs-lookup"><span data-stu-id="1982e-181">However, you can install a template that hasn't been published to nuget.org by referencing the *nupkg* file directly on your local file system as shown in the previous section [Install the template from the local nupkg file](#install-the-template-from-the-local-nupkg-file).</span></span>

<span data-ttu-id="1982e-182">Bir şablon nuget.org adresindeki paketinden yüklemek canlı bir örneği isterseniz kullanabileceğiniz [NUnit 3 şablonu için yeni dotnet](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/).</span><span class="sxs-lookup"><span data-stu-id="1982e-182">If you'd like a live example of how to install a template from a package at nuget.org, you can use the [NUnit 3 template for dotnet-new](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/).</span></span> <span data-ttu-id="1982e-183">Bu şablon bir projeyi NUnit birim testi kullanılacak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1982e-183">This template sets up a project to use NUnit unit testing.</span></span> <span data-ttu-id="1982e-184">Yüklemek için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="1982e-184">Use the following command to install it:</span></span>

```console
dotnet new -i NUnit3.DotNetNew.Template
```

<span data-ttu-id="1982e-185">Liste zaman şablonlarıyla `dotnet new -l`, gördüğünüz *NUnit 3 Test projesi* kısa adı ile *nunit* şablon listesinde.</span><span class="sxs-lookup"><span data-stu-id="1982e-185">When you list the templates with `dotnet new -l`, you see the *NUnit 3 Test Project* with a short name of *nunit* in the template list.</span></span> <span data-ttu-id="1982e-186">Sonraki bölümde şablonu kullanmaya hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="1982e-186">You're ready to use the template in the next section.</span></span>

![Diğer şablonları NUnit şablonla gösteren konsol penceresi](./media/create-custom-template/nunit-template-console-window.png)

### <a name="create-a-project-from-the-template"></a><span data-ttu-id="1982e-188">Bir şablondan bir proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="1982e-188">Create a project from the template</span></span>

<span data-ttu-id="1982e-189">Şablon Nuget'ten yüklendikten sonra şablonu yürüterek kullanmak `dotnet new <TEMPLATE>` şablon Altyapısı'na istediğiniz dizine komuttan çıkış yerleştirilen (kullanmakta olduğunuz sürece `-o|--output` belirli bir dizini belirtmek için seçeneği).</span><span class="sxs-lookup"><span data-stu-id="1982e-189">After the template is installed from NuGet, use the template by executing the `dotnet new <TEMPLATE>` command from the directory where you want to the template engine's output placed (unless you're using the `-o|--output` option to specify a specific directory).</span></span> <span data-ttu-id="1982e-190">Daha fazla bilgi için [ `dotnet new` seçenekleri](~/docs/core/tools/dotnet-new.md#options).</span><span class="sxs-lookup"><span data-stu-id="1982e-190">For more information, see [`dotnet new` Options](~/docs/core/tools/dotnet-new.md#options).</span></span> <span data-ttu-id="1982e-191">Şablonun kısa ad doğrudan tedarik `dotnet new` komutu.</span><span class="sxs-lookup"><span data-stu-id="1982e-191">Supply the template's short name directly to the `dotnet new` command.</span></span> <span data-ttu-id="1982e-192">NUnit şablondan bir proje oluşturmak için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="1982e-192">To create a project from the NUnit template, run the following command:</span></span>

```console
dotnet new nunit
```

<span data-ttu-id="1982e-193">Konsol projesi oluşturulur ve projenin paketleri geri olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="1982e-193">The console shows that the project is created and that the project's packages are restored.</span></span> <span data-ttu-id="1982e-194">Komutu çalıştırdıktan sonra projeyi kullanıma hazırdır.</span><span class="sxs-lookup"><span data-stu-id="1982e-194">After the command is run, the project is ready for use.</span></span>

![Konsol penceresinde proje bağımlılıklarını geri yükleme dahil olmak üzere yeni dotnet nunit çıktısını gösterir](./media/create-custom-template/dotnet-new-nunit-console-output.png)

### <a name="to-uninstall-a-template-from-a-nuget-package-stored-at-nugetorg"></a><span data-ttu-id="1982e-196">Nuget.org depolanan bir NuGet paketinden bir şablonu kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="1982e-196">To uninstall a template from a NuGet package stored at nuget.org</span></span>

```console
dotnet new -u GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> <span data-ttu-id="1982e-197">Örnek yalnızca gösterim amaçlıdır.</span><span class="sxs-lookup"><span data-stu-id="1982e-197">The example is for demonstration purposes only.</span></span> <span data-ttu-id="1982e-198">Hiç bir `GarciaSoftware.ConsoleTemplate.CSharp` NuGet paketini nuget.org veya .NET Core SDK'sı ile yüklü.</span><span class="sxs-lookup"><span data-stu-id="1982e-198">There isn't a `GarciaSoftware.ConsoleTemplate.CSharp` NuGet package at nuget.org or installed with the .NET Core SDK.</span></span> <span data-ttu-id="1982e-199">Komutu çalıştırırsanız, hiçbir paket/şablon kaldırılır ve şu özel durum alırsınız:</span><span class="sxs-lookup"><span data-stu-id="1982e-199">If you run the command, no package/template is uninstalled and you receive the following exception:</span></span>
>
> > <span data-ttu-id="1982e-200">Bir şeyi kaldırmak için 'GarciaSoftware.ConsoleTemplate.CSharp' adlı nebyla nalezena.</span><span class="sxs-lookup"><span data-stu-id="1982e-200">Could not find something to uninstall called 'GarciaSoftware.ConsoleTemplate.CSharp'.</span></span>

<span data-ttu-id="1982e-201">Yüklediyseniz [NUnit 3 şablonu için yeni dotnet](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/) isterseniz bunu kaldırın, aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="1982e-201">If you installed the [NUnit 3 template for dotnet-new](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/) and wish to uninstall it, use the following command:</span></span>

```console
dotnet new -u NUnit3.DotNetNew.Template
```

### <a name="uninstall-the-template-from-a-local-nupkg-file"></a><span data-ttu-id="1982e-202">Şablon yerel nupkg dosyasından kaldırın.</span><span class="sxs-lookup"><span data-stu-id="1982e-202">Uninstall the template from a local nupkg file</span></span>

<span data-ttu-id="1982e-203">Şablonu kaldırmak istiyorsanız, yolu kullanmaya çalışmayın *nupkg* dosya.</span><span class="sxs-lookup"><span data-stu-id="1982e-203">When you wish to uninstall the template, don't attempt to use the path to the *nupkg* file.</span></span> <span data-ttu-id="1982e-204">*Bir şablon kullanarak kaldırma girişimi `dotnet new -u <PATH_TO_NUPKG_FILE>` başarısız olur.*</span><span class="sxs-lookup"><span data-stu-id="1982e-204">*Attempting to uninstall a template using `dotnet new -u <PATH_TO_NUPKG_FILE>` fails.*</span></span> <span data-ttu-id="1982e-205">Başvuru paketi tarafından kendi `id`:</span><span class="sxs-lookup"><span data-stu-id="1982e-205">Reference the package by its `id`:</span></span>

```console
dotnet new -u GarciaSoftware.ConsoleTemplate.CSharp.1.0.0
```

## <a name="use-file-system-distribution"></a><span data-ttu-id="1982e-206">Dosya sistemi dağıtım kullanın</span><span class="sxs-lookup"><span data-stu-id="1982e-206">Use file system distribution</span></span>

<span data-ttu-id="1982e-207">Şablonu dağıtmak için proje şablonu klasörüne bir konumda ağınızdaki kullanıcılar için erişilebilir yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="1982e-207">To distribute the template, place the project template folder in a location accessible to users on your network.</span></span> <span data-ttu-id="1982e-208">Kullanım `dotnet new` komutunu `-i|--install` seçenek ve şablon klasörü yolunu belirtin (projeyi içeren proje klasörü ve *. template.config* klasörü).</span><span class="sxs-lookup"><span data-stu-id="1982e-208">Use the `dotnet new` command with the `-i|--install` option and specify the path to the template folder (the project folder containing the project and the *.template.config* folder).</span></span>

<span data-ttu-id="1982e-209">Bu öğretici proje şablonu depolanır varsayar *belgeleri/şablonları* kullanıcının profilin klasörü.</span><span class="sxs-lookup"><span data-stu-id="1982e-209">The tutorial assumes the project template is stored in the *Documents/Templates* folder of the user's profile.</span></span> <span data-ttu-id="1982e-210">Aşağıdaki komut değiştirme ile şablon o konumdan yüklemek \<kullanıcı > ile kullanıcının profil adı:</span><span class="sxs-lookup"><span data-stu-id="1982e-210">From that location, install the template with the following command replacing \<USER> with the user's profile name:</span></span>

```console
dotnet new -i C:\Users\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp
```

### <a name="create-a-project-from-the-template"></a><span data-ttu-id="1982e-211">Bir şablondan bir proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="1982e-211">Create a project from the template</span></span>

<span data-ttu-id="1982e-212">Şablon dosya sisteminden yüklendikten sonra şablonu yürüterek kullanmak `dotnet new <TEMPLATE>` şablon Altyapısı'na istediğiniz dizine komuttan çıkış yerleştirilen (kullanmakta olduğunuz sürece `-o|--output` belirli bir dizini belirtmek için seçeneği).</span><span class="sxs-lookup"><span data-stu-id="1982e-212">After the template is installed from the file system, use the template by executing the `dotnet new <TEMPLATE>` command from the directory where you want to the template engine's output placed (unless you're using the `-o|--output` option to specify a specific directory).</span></span> <span data-ttu-id="1982e-213">Daha fazla bilgi için [ `dotnet new` seçenekleri](~/docs/core/tools/dotnet-new.md#options).</span><span class="sxs-lookup"><span data-stu-id="1982e-213">For more information, see [`dotnet new` Options](~/docs/core/tools/dotnet-new.md#options).</span></span> <span data-ttu-id="1982e-214">Şablonun kısa ad doğrudan tedarik `dotnet new` komutu.</span><span class="sxs-lookup"><span data-stu-id="1982e-214">Supply the template's short name directly to the `dotnet new` command.</span></span>

<span data-ttu-id="1982e-215">Oluşturulma yeni bir proje klasöründeki *C:\Users\\\<kullanıcı > \Documents\Projects\MyConsoleApp*, bir proje oluşturma `garciaconsole` şablonu:</span><span class="sxs-lookup"><span data-stu-id="1982e-215">From a new project folder created at *C:\Users\\\<USER>\Documents\Projects\MyConsoleApp*, create a project from the `garciaconsole` template:</span></span>

```console
dotnet new garciaconsole
```

### <a name="uninstall-the-template"></a><span data-ttu-id="1982e-216">Şablonu Kaldır</span><span class="sxs-lookup"><span data-stu-id="1982e-216">Uninstall the template</span></span>

<span data-ttu-id="1982e-217">Yerel dosya sisteminize şablon oluşturduysanız *C:\Users\\\<kullanıcı > \Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp*, kendisiyle kaldırma `-u|--uninstall` anahtar ve yolu Şablon klasör:</span><span class="sxs-lookup"><span data-stu-id="1982e-217">If you created the template on your local file system at *C:\Users\\\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp*, uninstall it with the `-u|--uninstall` switch and the path to the template folder:</span></span>

```console
dotnet new -u C:\Users\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> <span data-ttu-id="1982e-218">Yerel dosya sisteminizden şablonu kaldırmak için yol tam olarak nitelemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="1982e-218">To uninstall the template from your local file system, you need to fully qualify the path.</span></span> <span data-ttu-id="1982e-219">Örneğin, *C:\Users\\\<kullanıcı > \Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp* çalışır, ancak *./GarciaSoftware.ConsoleTemplate.CSharp* içeren klasörden erişemez.</span><span class="sxs-lookup"><span data-stu-id="1982e-219">For example, *C:\Users\\\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="1982e-220">Ayrıca, şablonu yoldaki son Sonlandırıcı directory eğik çizgi içermez.</span><span class="sxs-lookup"><span data-stu-id="1982e-220">Additionally, do not include a final terminating directory slash on your template path.</span></span>

## <a name="see-also"></a><span data-ttu-id="1982e-221">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1982e-221">See also</span></span>

- [<span data-ttu-id="1982e-222">DotNet/şablon GitHub deposunu Wiki</span><span class="sxs-lookup"><span data-stu-id="1982e-222">dotnet/templating GitHub repo Wiki</span></span>](https://github.com/dotnet/templating/wiki)
- [<span data-ttu-id="1982e-223">DotNet/dotnet-şablonu-örnekleri GitHub deposu</span><span class="sxs-lookup"><span data-stu-id="1982e-223">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="1982e-224">Dotnet için kendi şablonlarınızı yeni oluşturma</span><span class="sxs-lookup"><span data-stu-id="1982e-224">How to create your own templates for dotnet new</span></span>](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/)
- [<span data-ttu-id="1982e-225">*Template.JSON* JSON şema Store şema</span><span class="sxs-lookup"><span data-stu-id="1982e-225">*template.json* schema at the JSON Schema Store</span></span>](http://json.schemastore.org/template)
