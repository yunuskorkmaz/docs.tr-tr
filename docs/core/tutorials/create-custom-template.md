---
title: Dotnet için özel bir şablon yeni oluştur
description: Bu eğlenceli dotnet yeni komutu için özel bir şablon oluşturmayı öğrenin öğretici.
author: guardrex
ms.author: mairaw
ms.date: 08/12/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 9ff58634daa6d51c10df9a3c9a1af0fd6420c69c
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="create-a-custom-template-for-dotnet-new"></a><span data-ttu-id="1da42-103">Dotnet için özel bir şablon yeni oluştur</span><span class="sxs-lookup"><span data-stu-id="1da42-103">Create a custom template for dotnet new</span></span>

<span data-ttu-id="1da42-104">Bu öğretici şunların nasıl yapıldığını gösterir için:</span><span class="sxs-lookup"><span data-stu-id="1da42-104">This tutorial shows you how to:</span></span>

- <span data-ttu-id="1da42-105">Temel şablonunu var olan bir proje veya yeni bir konsol uygulama projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1da42-105">Create a basic template from an existing project or a new console app project.</span></span>
- <span data-ttu-id="1da42-106">Nuget.org veya yerel bir dağıtım şablonu paketi *nupkg* dosya.</span><span class="sxs-lookup"><span data-stu-id="1da42-106">Pack the template for distribution at nuget.org or from a local *nupkg* file.</span></span>
- <span data-ttu-id="1da42-107">Yerel nuget.org şablon yükleme *nupkg* dosya ya da yerel dosya sistemi.</span><span class="sxs-lookup"><span data-stu-id="1da42-107">Install the template from nuget.org, a local *nupkg* file, or the local file system.</span></span>
- <span data-ttu-id="1da42-108">Şablon kaldırın.</span><span class="sxs-lookup"><span data-stu-id="1da42-108">Uninstall the template.</span></span>

<span data-ttu-id="1da42-109">Bu öğreticiyi tam bir örnek üzerinden geçmek isterseniz, indirme [örnek proje şablonu](https://github.com/dotnet/dotnet-template-samples/tree/master/16-nuget-package).</span><span class="sxs-lookup"><span data-stu-id="1da42-109">If you prefer to proceed through the tutorial with a complete sample, download the [sample project template](https://github.com/dotnet/dotnet-template-samples/tree/master/16-nuget-package).</span></span> <span data-ttu-id="1da42-110">Örnek şablon NuGet dağıtımı için yapılandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="1da42-110">The sample template is configured for NuGet distribution.</span></span>

<span data-ttu-id="1da42-111">İndirilen örnek dosya sistemi dağıtımı ile kullanmak istiyorsanız, aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="1da42-111">If you wish to use the downloaded sample with file system distribution, do the following:</span></span>

- <span data-ttu-id="1da42-112">İçeriğini taşımak *içerik* klasörü örnek bir düzey yukarı *GarciaSoftware.ConsoleTemplate.CSharp* klasör.</span><span class="sxs-lookup"><span data-stu-id="1da42-112">Move the contents of the *content* folder of the sample up one level into the *GarciaSoftware.ConsoleTemplate.CSharp* folder.</span></span>
- <span data-ttu-id="1da42-113">Boş silme *içerik* klasör.</span><span class="sxs-lookup"><span data-stu-id="1da42-113">Delete the empty *content* folder.</span></span>
- <span data-ttu-id="1da42-114">Silme *nuspec* dosya.</span><span class="sxs-lookup"><span data-stu-id="1da42-114">Delete the *nuspec* file.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1da42-115">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="1da42-115">Prerequisites</span></span>

- <span data-ttu-id="1da42-116">Yükleme [.NET Core 2.0 SDK](https://www.microsoft.com/net/core) veya sonraki sürümler.</span><span class="sxs-lookup"><span data-stu-id="1da42-116">Install the [.NET Core 2.0 SDK](https://www.microsoft.com/net/core) or later versions.</span></span>
- <span data-ttu-id="1da42-117">Başvuru konusunu okuyun [yeni dotnet için özel şablonlar](../tools/custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="1da42-117">Read the reference topic [Custom templates for dotnet new](../tools/custom-templates.md).</span></span>

## <a name="create-a-template-from-a-project"></a><span data-ttu-id="1da42-118">Bir şablonu bir proje oluşturun</span><span class="sxs-lookup"><span data-stu-id="1da42-118">Create a template from a project</span></span>

<span data-ttu-id="1da42-119">Kullanım onaylanıp var olan bir proje derler ve çalıştıran veya yeni bir konsol uygulama projesi için sabit diskinizde bir klasör oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1da42-119">Use an existing project that you've confirmed compiles and runs, or create a new console app project in a folder on your hard drive.</span></span> <span data-ttu-id="1da42-120">Bu öğretici proje klasörünün adını olduğunu varsayar *GarciaSoftware.ConsoleTemplate.CSharp* depolandığı *Documents\Templates* kullanıcının profilindeki.</span><span class="sxs-lookup"><span data-stu-id="1da42-120">This tutorial assumes that the name of the project folder is *GarciaSoftware.ConsoleTemplate.CSharp* stored at *Documents\Templates* in the user's profile.</span></span> <span data-ttu-id="1da42-121">Eğitmen proje şablonu adı şu biçimdedir  *\<şirket adı >.\< Şablon türü >. \<Programlama dili >*, ancak proje ve şablonu istediğiniz herhangi bir şey adı boş.</span><span class="sxs-lookup"><span data-stu-id="1da42-121">The tutorial project template name is in the format *\<Company Name>.\<Template Type>.\<Programming Language>*, but you're free to name your project and template anything you wish.</span></span>

1. <span data-ttu-id="1da42-122">Adlı proje kök klasör ekleme *. template.config*.</span><span class="sxs-lookup"><span data-stu-id="1da42-122">Add a folder to the root of the project named *.template.config*.</span></span>
1. <span data-ttu-id="1da42-123">İçinde *. template.config* klasörü oluşturmak bir *template.json* şablonunuzu yapılandırmak için bir dosya.</span><span class="sxs-lookup"><span data-stu-id="1da42-123">Inside the *.template.config* folder, create a *template.json* file to configure your template.</span></span> <span data-ttu-id="1da42-124">Daha fazla bilgi ve üye tanımları için *template.json* dosya için bkz: [yeni dotnet için özel şablonlar](../tools/custom-templates.md#templatejson) konu ve [ *template.json* JSON şeması depolama şema](http://json.schemastore.org/template).</span><span class="sxs-lookup"><span data-stu-id="1da42-124">For more information and member definitions for the *template.json* file, see the [Custom templates for dotnet new](../tools/custom-templates.md#templatejson) topic and the [*template.json* schema at the JSON Schema Store](http://json.schemastore.org/template).</span></span>

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

<span data-ttu-id="1da42-125">Şablon tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="1da42-125">The template is finished.</span></span> <span data-ttu-id="1da42-126">Bu noktada, şablon dağıtımı için iki seçeneğiniz vardır.</span><span class="sxs-lookup"><span data-stu-id="1da42-126">At this point, you have two options for template distribution.</span></span> <span data-ttu-id="1da42-127">Bu öğretici devam etmek için bir yol veya diğer seçin:</span><span class="sxs-lookup"><span data-stu-id="1da42-127">To continue this tutorial, choose one path or the other:</span></span>

1. <span data-ttu-id="1da42-128">[NuGet dağıtım](#use-nuget-distribution): NuGet ya da yerel şablonunu yüklemek *nupkg* dosya ve yüklenmiş bir şablon kullanın.</span><span class="sxs-lookup"><span data-stu-id="1da42-128">[NuGet distribution](#use-nuget-distribution): install the template from NuGet or from the local *nupkg* file, and use the installed template.</span></span>
2. <span data-ttu-id="1da42-129">[Dosya sistemi dağıtım](#use-file-system-distribution).</span><span class="sxs-lookup"><span data-stu-id="1da42-129">[File system distribution](#use-file-system-distribution).</span></span>

## <a name="use-nuget-distribution"></a><span data-ttu-id="1da42-130">NuGet dağıtım kullanın</span><span class="sxs-lookup"><span data-stu-id="1da42-130">Use NuGet Distribution</span></span>

### <a name="pack-the-template-into-a-nuget-package"></a><span data-ttu-id="1da42-131">Şablon bir NuGet paketi</span><span class="sxs-lookup"><span data-stu-id="1da42-131">Pack the template into a NuGet package</span></span>

1. <span data-ttu-id="1da42-132">NuGet paketi için bir klasör oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1da42-132">Create a folder for the NuGet package.</span></span> <span data-ttu-id="1da42-133">Öğretici, klasör adı için *GarciaSoftware.ConsoleTemplate.CSharp* kullanılan ve klasör içinde oluşturulan bir *Documents\NuGetTemplates* kullanıcının profilini klasöründe.</span><span class="sxs-lookup"><span data-stu-id="1da42-133">For the tutorial, the folder name *GarciaSoftware.ConsoleTemplate.CSharp* is used, and the folder is created inside a *Documents\NuGetTemplates* folder in the user's profile.</span></span> <span data-ttu-id="1da42-134">Adlı bir klasör oluşturun *içerik* proje dosyalarını tutmak için yeni şablon klasörünü içinde.</span><span class="sxs-lookup"><span data-stu-id="1da42-134">Create a folder named *content* inside of the new template folder to hold the project files.</span></span>
1. <span data-ttu-id="1da42-135">İle birlikte proje klasörünüzdeki içeriğini kopyalayın, *.template.config/template.json* dosyası içine *içerik* oluşturduğunuz klasör.</span><span class="sxs-lookup"><span data-stu-id="1da42-135">Copy the contents of your project folder, together with its *.template.config/template.json* file, into the *content* folder you created.</span></span>
1. <span data-ttu-id="1da42-136">Yanına *içerik* klasörüne eklemek bir [ *nuspec* dosya](/nuget/create-packages/creating-a-package).</span><span class="sxs-lookup"><span data-stu-id="1da42-136">Next to the *content* folder, add a [*nuspec* file](/nuget/create-packages/creating-a-package).</span></span> <span data-ttu-id="1da42-137">Bir paketin içeriğini açıklayan ve NuGet paketi oluşturma işlemi sürücüleri bir XML bildirim dosyası nuspec dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="1da42-137">The nuspec file is an XML manifest file that describes a package's contents and drives the process of creating the NuGet package.</span></span>
   
   ![NuGet paketi düzenini gösteren dizin yapısı](./media/create-custom-template/nugetdirectorylayout.png)

1. <span data-ttu-id="1da42-139">İçinde bir  **\<packageTypes >** öğesinde *nuspec* içeriyor, dosya bir  **\<packageType >** öğesi ile bir `name` öznitelik değeri `Template`.</span><span class="sxs-lookup"><span data-stu-id="1da42-139">Inside of a **\<packageTypes>** element in the *nuspec* file, include a **\<packageType>** element with a `name` attribute value of `Template`.</span></span> <span data-ttu-id="1da42-140">Her iki *içerik* klasör ve *nuspec* dosya aynı dizinde bulunması.</span><span class="sxs-lookup"><span data-stu-id="1da42-140">Both the *content* folder and the *nuspec* file should reside in the same directory.</span></span> <span data-ttu-id="1da42-141">En düşük tablo gösterir *nuspec* dosya şablon bir NuGet paketi olarak üretmek için gereken öğeler.</span><span class="sxs-lookup"><span data-stu-id="1da42-141">The table shows the minimum *nuspec* file elements required to produce a template as a NuGet package.</span></span>

   | <span data-ttu-id="1da42-142">Öğe</span><span class="sxs-lookup"><span data-stu-id="1da42-142">Element</span></span>            | <span data-ttu-id="1da42-143">Tür</span><span class="sxs-lookup"><span data-stu-id="1da42-143">Type</span></span>   | <span data-ttu-id="1da42-144">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1da42-144">Description</span></span> |
   | ------------------ | ------ | ----------- |
   | <span data-ttu-id="1da42-145">**\<yazarları >**</span><span class="sxs-lookup"><span data-stu-id="1da42-145">**\<authors>**</span></span>     | <span data-ttu-id="1da42-146">dize</span><span class="sxs-lookup"><span data-stu-id="1da42-146">string</span></span> | <span data-ttu-id="1da42-147">Nuget.org profil adları eşleşen paketleri yazarlar, virgülle ayrılmış listesi. Yazarları nuget.org NuGet galerisinde görüntülenir ve paketleri çapraz başvuru yapmak için aynı yazarlar tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1da42-147">A comma-separated list of packages authors, matching the profile names on nuget.org. Authors are displayed in the NuGet Gallery on nuget.org and are used to cross-reference packages by the same authors.</span></span> |
   | <span data-ttu-id="1da42-148">**\<Açıklama >**</span><span class="sxs-lookup"><span data-stu-id="1da42-148">**\<description>**</span></span> | <span data-ttu-id="1da42-149">dize</span><span class="sxs-lookup"><span data-stu-id="1da42-149">string</span></span> | <span data-ttu-id="1da42-150">Paket UI görüntü için uzun bir açıklaması.</span><span class="sxs-lookup"><span data-stu-id="1da42-150">A long description of the package for UI display.</span></span> |
   | <span data-ttu-id="1da42-151">**\<Kimliği >**</span><span class="sxs-lookup"><span data-stu-id="1da42-151">**\<id>**</span></span>          | <span data-ttu-id="1da42-152">dize</span><span class="sxs-lookup"><span data-stu-id="1da42-152">string</span></span> | <span data-ttu-id="1da42-153">Nuget.org ya da ihtiyacınız arasında benzersiz olması büyük küçük harf duyarsız paket tanımlayıcısı galeri paketi içindeki bulunacağı.</span><span class="sxs-lookup"><span data-stu-id="1da42-153">The case-insensitive package identifier, which must be unique across nuget.org or whatever gallery the package will reside in.</span></span> <span data-ttu-id="1da42-154">Kimlikleri boşluk veya bir URL geçerli değil ve genellikle .NET ad alanı kurallarına karakter içerebilir.</span><span class="sxs-lookup"><span data-stu-id="1da42-154">IDs may not contain spaces or characters that are not valid for a URL and generally follow .NET namespace rules.</span></span> <span data-ttu-id="1da42-155">Bkz: [benzersiz paket tanımlayıcısı seçme ve sürüm numarasını ayarlama](/nuget/create-packages/creating-a-package#choosing-a-unique-package-identifier-and-setting-the-version-number) Kılavuzu.</span><span class="sxs-lookup"><span data-stu-id="1da42-155">See [Choosing a unique package identifier and setting the version number](/nuget/create-packages/creating-a-package#choosing-a-unique-package-identifier-and-setting-the-version-number) for guidance.</span></span> |
   | <span data-ttu-id="1da42-156">**\<packageType >**</span><span class="sxs-lookup"><span data-stu-id="1da42-156">**\<packageType>**</span></span> | <span data-ttu-id="1da42-157">dize</span><span class="sxs-lookup"><span data-stu-id="1da42-157">string</span></span> | <span data-ttu-id="1da42-158">Bu öğe içine yerleştirin bir  **\<packageTypes >** öğesi arasında  **\<meta verileri >** öğeleri.</span><span class="sxs-lookup"><span data-stu-id="1da42-158">Place this element inside a **\<packageTypes>** element among the **\<metadata>** elements.</span></span> <span data-ttu-id="1da42-159">Ayarlama `name` özniteliği  **\<packageType >** öğesine `Template`.</span><span class="sxs-lookup"><span data-stu-id="1da42-159">Set the `name` attribute of the **\<packageType>** element to `Template`.</span></span> |
   | <span data-ttu-id="1da42-160">**\<Sürüm >**</span><span class="sxs-lookup"><span data-stu-id="1da42-160">**\<version>**</span></span>     | <span data-ttu-id="1da42-161">dize</span><span class="sxs-lookup"><span data-stu-id="1da42-161">string</span></span> | <span data-ttu-id="1da42-162">Major.minor.patch desen aşağıdaki şekilde paketin sürümü.</span><span class="sxs-lookup"><span data-stu-id="1da42-162">The version of the package, following the major.minor.patch pattern.</span></span> <span data-ttu-id="1da42-163">Sürüm numaraları, yayın öncesi soneki içerebilir, açıklandığı gibi [yayın öncesi sürümleri](/nuget/create-packages/prerelease-packages#semantic-versioning).</span><span class="sxs-lookup"><span data-stu-id="1da42-163">Version numbers may include a pre-release suffix as described in [Pre-release versions](/nuget/create-packages/prerelease-packages#semantic-versioning).</span></span> |

   <span data-ttu-id="1da42-164">Bkz: [.nuspec başvuru](/nuget/schema/nuspec) tam için *nuspec* dosyası şeması.</span><span class="sxs-lookup"><span data-stu-id="1da42-164">See the [.nuspec reference](/nuget/schema/nuspec) for the complete *nuspec* file schema.</span></span>

   <span data-ttu-id="1da42-165">*Nuspec* öğretici adlı için dosya *GarciaSoftware.ConsoleTemplate.CSharp.nuspec* ve aşağıdaki içeriği içerir:</span><span class="sxs-lookup"><span data-stu-id="1da42-165">The *nuspec* file for the tutorial is named *GarciaSoftware.ConsoleTemplate.CSharp.nuspec* and contains the following content:</span></span>

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

1. <span data-ttu-id="1da42-166">[Paket oluşturma](/nuget/create-packages/creating-a-package#creating-the-package) kullanarak `nuget pack <PATH_TO_NUSPEC_FILE>` komutu.</span><span class="sxs-lookup"><span data-stu-id="1da42-166">[Create the package](/nuget/create-packages/creating-a-package#creating-the-package) using the `nuget pack <PATH_TO_NUSPEC_FILE>` command.</span></span> <span data-ttu-id="1da42-167">Aşağıdaki komutu NuGet varlıklar tutan klasör konumunda varsayar *C:\Users\\\<kullanıcı > \Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp*.</span><span class="sxs-lookup"><span data-stu-id="1da42-167">The following command assumes that the folder that holds the NuGet assets is at *C:\Users\\\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp*.</span></span> <span data-ttu-id="1da42-168">Ancak klasörü, sisteminizde yerde yerleştirdiğiniz `nuget pack` komut yolu kabul *nuspec* dosyası:</span><span class="sxs-lookup"><span data-stu-id="1da42-168">But wherever you place the folder on your system, the `nuget pack` command accepts the path to the *nuspec* file:</span></span>

   ```console
   nuget pack C:\Users\<USER>\Documents\NuGetTemplates\GarciaSoftware.ConsoleTemplate.CSharp\GarciaSoftware.ConsoleTemplate.CSharp.nuspec
   ```

### <a name="publishing-the-package-to-nugetorg"></a><span data-ttu-id="1da42-169">Paket için nuget.org yayımlama</span><span class="sxs-lookup"><span data-stu-id="1da42-169">Publishing the package to nuget.org</span></span>

<span data-ttu-id="1da42-170">Bir NuGet paketi yayımlamak için ' ndaki yönergeleri izleyin [oluşturma ve bir paketi yayımlamaya](/nuget/quickstart/create-and-publish-a-package#publish-the-package) konu.</span><span class="sxs-lookup"><span data-stu-id="1da42-170">To publish a NuGet package, follow the instructions in the [Create and publish a package](/nuget/quickstart/create-and-publish-a-package#publish-the-package) topic.</span></span> <span data-ttu-id="1da42-171">Ancak, hiçbir zaman yayımlandıktan sonra yalnızca delisted silinmeden gibi öğretici şablonu için NuGet yayımlama öneririz.</span><span class="sxs-lookup"><span data-stu-id="1da42-171">However, we recommend that you don't publish the tutorial template to NuGet as it can never be deleted once published, only delisted.</span></span> <span data-ttu-id="1da42-172">NuGet paketi biçiminde sahip olduğunuza göre bir *nupkg* dosyası önerdiğimiz doğrudan yerel bilgisayardan şablonunu yüklemek için aşağıdaki yönergeleri izleyin *nupkg* dosya.</span><span class="sxs-lookup"><span data-stu-id="1da42-172">Now that you have the NuGet package in the form of a *nupkg* file, we suggest that you follow the instructions below to install the template directly from the local *nupkg* file.</span></span>

### <a name="install-the-template-from-a-nuget-package"></a><span data-ttu-id="1da42-173">Şablonu bir NuGet paketi yükle</span><span class="sxs-lookup"><span data-stu-id="1da42-173">Install the template from a NuGet package</span></span>

#### <a name="install-the-template-from-the-local-nupkg-file"></a><span data-ttu-id="1da42-174">Yerel bilgisayardan şablonunu yüklemek *nupkg* dosyası</span><span class="sxs-lookup"><span data-stu-id="1da42-174">Install the template from the local *nupkg* file</span></span>

<span data-ttu-id="1da42-175">Şablondan yüklemek için *nupkg* , üretilen, dosya kullanım `dotnet new` komutunu `-i|--install` seçeneği ve yolunu girin *nupkg* dosyası:</span><span class="sxs-lookup"><span data-stu-id="1da42-175">To install the template from the *nupkg* file that you produced, use the `dotnet new` command with the `-i|--install` option and provide the path to the *nupkg* file:</span></span>

```console
dotnet new -i C:\Users\<USER>\GarciaSoftware.ConsoleTemplate.CSharp.1.0.0.nupkg
```

#### <a name="install-the-template-from-a-nuget-package-stored-at-nugetorg"></a><span data-ttu-id="1da42-176">Şablon nuget.org depolanan bir NuGet paketi yükleyin</span><span class="sxs-lookup"><span data-stu-id="1da42-176">Install the template from a NuGet package stored at nuget.org</span></span>

<span data-ttu-id="1da42-177">Bir şablon kullanım nuget.org depolanan bir NuGet paketi yükleyin isterseniz, `dotnet new` komutunu `-i|--install` seçeneği ve NuGet paketinin adını sağlayın:</span><span class="sxs-lookup"><span data-stu-id="1da42-177">If you wish to install a template from a NuGet package stored at nuget.org, use the `dotnet new` command with the `-i|--install` option and supply the name of the NuGet package:</span></span>

```console
dotnet new -i GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> <span data-ttu-id="1da42-178">Örnek, yalnızca tanıtım amacıyla kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1da42-178">The example is for demonstration purposes only.</span></span> <span data-ttu-id="1da42-179">Hiç bir `GarciaSoftware.ConsoleTemplate.CSharp` nuget.org, NuGet paket ve yayımlama ve test şablonlardan NuGet kullanma öneririz yok.</span><span class="sxs-lookup"><span data-stu-id="1da42-179">There isn't a `GarciaSoftware.ConsoleTemplate.CSharp` NuGet package at nuget.org, and we don't recommend that you publish and consume test templates from NuGet.</span></span> <span data-ttu-id="1da42-180">Komutu çalıştırırsanız, herhangi bir şablon yüklenir.</span><span class="sxs-lookup"><span data-stu-id="1da42-180">If you run the command, no template is installed.</span></span> <span data-ttu-id="1da42-181">Ancak, nuget.org için başvurarak yayımlanmadı bir şablon yükleyebilirsiniz *nupkg* önceki bölümde gösterildiği gibi doğrudan yerel dosya sisteminde dosya [yerel nupkg şablonunu yüklemek Dosya](#install-the-template-from-the-local-nupkg-file).</span><span class="sxs-lookup"><span data-stu-id="1da42-181">However, you can install a template that hasn't been published to nuget.org by referencing the *nupkg* file directly on your local file system as shown in the previous section [Install the template from the local nupkg file](#install-the-template-from-the-local-nupkg-file).</span></span>

<span data-ttu-id="1da42-182">Bir şablon nuget.org bir paketin yüklemek nasıl dinamik örneği istiyorsanız kullanabileceğiniz [NUnit 3 şablonu dotnet yeni](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/).</span><span class="sxs-lookup"><span data-stu-id="1da42-182">If you'd like a live example of how to install a template from a package at nuget.org, you can use the [NUnit 3 template for dotnet-new](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/).</span></span> <span data-ttu-id="1da42-183">Bu şablon bir projeyi NUnit birim testi kullanacak şekilde ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1da42-183">This template sets up a project to use NUnit unit testing.</span></span> <span data-ttu-id="1da42-184">Yüklemek için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="1da42-184">Use the following command to install it:</span></span>

```console
dotnet new -i NUnit3.DotNetNew.Template
```

<span data-ttu-id="1da42-185">Liste zaman şablonlarıyla `dotnet new -l`, gördüğünüz *NUnit 3 Test projesi* kısa bir adı ile *nunit* şablon listesinde.</span><span class="sxs-lookup"><span data-stu-id="1da42-185">When you list the templates with `dotnet new -l`, you see the *NUnit 3 Test Project* with a short name of *nunit* in the template list.</span></span> <span data-ttu-id="1da42-186">Sonraki bölümde şablonu kullanmak hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="1da42-186">You're ready to use the template in the next section.</span></span>

![Diğer yüklü şablonlarıyla listelenen NUnit şablonu gösteren konsol penceresi](./media/create-custom-template/nunit1.png)

### <a name="create-a-project-from-the-template"></a><span data-ttu-id="1da42-188">Bir proje şablonu oluşturma</span><span class="sxs-lookup"><span data-stu-id="1da42-188">Create a project from the template</span></span>

<span data-ttu-id="1da42-189">Şablon Nuget'ten yüklendikten sonra şablonu yürüterek kullanmaya `dotnet new <TEMPLATE>` şablon motoru istediğiniz dizinin komutu animasyonun çıktı yerleştirilen (kullanmakta olduğunuz sürece `-o|--output` seçeneği belirli bir dizin belirtin).</span><span class="sxs-lookup"><span data-stu-id="1da42-189">After the template is installed from NuGet, use the template by executing the `dotnet new <TEMPLATE>` command from the directory where you want to the template engine's output placed (unless you're using the `-o|--output` option to specify a specific directory).</span></span> <span data-ttu-id="1da42-190">Daha fazla bilgi için bkz: [ `dotnet new` seçenekleri](~/docs/core/tools/dotnet-new.md#options).</span><span class="sxs-lookup"><span data-stu-id="1da42-190">For more information, see [`dotnet new` Options](~/docs/core/tools/dotnet-new.md#options).</span></span> <span data-ttu-id="1da42-191">Şablonun kısa ad doğrudan tedarik `dotnet new` komutu.</span><span class="sxs-lookup"><span data-stu-id="1da42-191">Supply the template's short name directly to the `dotnet new` command.</span></span> <span data-ttu-id="1da42-192">Bir proje NUnit şablonu oluşturmak için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="1da42-192">To create a project from the NUnit template, run the following command:</span></span>

```console
dotnet new nunit
```

<span data-ttu-id="1da42-193">Konsol projesi oluşturulur ve projenin paketler geri yükleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="1da42-193">The console shows that the project is created and that the project's packages are restored.</span></span> <span data-ttu-id="1da42-194">Komutu çalıştırdıktan sonra proje kullanıma hazırdır.</span><span class="sxs-lookup"><span data-stu-id="1da42-194">After the command is run, the project is ready for use.</span></span>

![NUnit projesi oluşturur ve proje bağımlılıkları yükler gibi dotnet yeni komutunun çıkışını gösteren konsol penceresi](./media/create-custom-template/nunit2.png)

### <a name="to-uninstall-a-template-from-a-nuget-package-stored-at-nugetorg"></a><span data-ttu-id="1da42-196">Nuget.org depolanan NuGet paketinden bir şablonu kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="1da42-196">To uninstall a template from a NuGet package stored at nuget.org</span></span>

```console
dotnet new -u GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> <span data-ttu-id="1da42-197">Örnek, yalnızca tanıtım amacıyla kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1da42-197">The example is for demonstration purposes only.</span></span> <span data-ttu-id="1da42-198">Hiç bir `GarciaSoftware.ConsoleTemplate.CSharp` NuGet paketini nuget.org veya .NET Core SDK ile birlikte yüklenen.</span><span class="sxs-lookup"><span data-stu-id="1da42-198">There isn't a `GarciaSoftware.ConsoleTemplate.CSharp` NuGet package at nuget.org or installed with the .NET Core SDK.</span></span> <span data-ttu-id="1da42-199">Komutu çalıştırırsanız, hiçbir paket/şablon kaldırılır ve şu özel durum alırsınız:</span><span class="sxs-lookup"><span data-stu-id="1da42-199">If you run the command, no package/template is uninstalled and you receive the following exception:</span></span>
> 
> > <span data-ttu-id="1da42-200">Kaldırmak için bir şey 'GarciaSoftware.ConsoleTemplate.CSharp' adlı bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="1da42-200">Could not find something to uninstall called 'GarciaSoftware.ConsoleTemplate.CSharp'.</span></span>

<span data-ttu-id="1da42-201">Yüklediyseniz [NUnit 3 şablonu dotnet yeni](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/) ve istediğiniz kaldırmak için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="1da42-201">If you installed the [NUnit 3 template for dotnet-new](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/) and wish to uninstall it, use the following command:</span></span>

```console
dotnet new -u NUnit3.DotNetNew.Template
```

### <a name="uninstall-the-template-from-a-local-nupkg-file"></a><span data-ttu-id="1da42-202">Şablon yerel nupkg dosyadan kaldırın</span><span class="sxs-lookup"><span data-stu-id="1da42-202">Uninstall the template from a local nupkg file</span></span>

<span data-ttu-id="1da42-203">Şablonu kaldırmak istediğinizde, yolunu kullanma girişimi yok *nupkg* dosya.</span><span class="sxs-lookup"><span data-stu-id="1da42-203">When you wish to uninstall the template, don't attempt to use the path to the *nupkg* file.</span></span> <span data-ttu-id="1da42-204">*Bir şablon kullanarak kaldırma işlemini denemeden `dotnet new -u <PATH_TO_NUPKG_FILE>` başarısız olur.*</span><span class="sxs-lookup"><span data-stu-id="1da42-204">*Attempting to uninstall a template using `dotnet new -u <PATH_TO_NUPKG_FILE>` fails.*</span></span> <span data-ttu-id="1da42-205">Paket tarafından başvuru kendi `id`:</span><span class="sxs-lookup"><span data-stu-id="1da42-205">Reference the package by its `id`:</span></span>

```console
dotnet new -u GarciaSoftware.ConsoleTemplate.CSharp.1.0.0
```

## <a name="use-file-system-distribution"></a><span data-ttu-id="1da42-206">Dosya sistemi dağıtım kullanın</span><span class="sxs-lookup"><span data-stu-id="1da42-206">Use file system distribution</span></span>

<span data-ttu-id="1da42-207">Şablonu dağıtmak için proje şablonu klasörü bir konumda ağınızdaki kullanıcılar için erişilebilir yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="1da42-207">To distribute the template, place the project template folder in a location accessible to users on your network.</span></span> <span data-ttu-id="1da42-208">Kullanım `dotnet new` komutunu `-i|--install` seçeneği ve şablon klasörün yolunu belirtin (projeyi içeren projeyi klasörü ve *. template.config* klasörü).</span><span class="sxs-lookup"><span data-stu-id="1da42-208">Use the `dotnet new` command with the `-i|--install` option and specify the path to the template folder (the project folder containing the project and the *.template.config* folder).</span></span>

<span data-ttu-id="1da42-209">Proje şablonu depolanır öğretici varsayar *belgeler/şablonları* kullanıcının profilini klasörü.</span><span class="sxs-lookup"><span data-stu-id="1da42-209">The tutorial assumes the project template is stored in the *Documents/Templates* folder of the user's profile.</span></span> <span data-ttu-id="1da42-210">Aşağıdaki yerine komutu şablonunu bu konumdan yüklemek \<kullanıcı > kullanıcının profil adı ile:</span><span class="sxs-lookup"><span data-stu-id="1da42-210">From that location, install the template with the following command replacing \<USER> with the user's profile name:</span></span>

```console
dotnet new -i C:\Users\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp
```

### <a name="create-a-project-from-the-template"></a><span data-ttu-id="1da42-211">Bir proje şablonu oluşturma</span><span class="sxs-lookup"><span data-stu-id="1da42-211">Create a project from the template</span></span>

<span data-ttu-id="1da42-212">Şablon dosya sisteminden yüklendikten sonra şablonu yürüterek kullanmaya `dotnet new <TEMPLATE>` şablon motoru istediğiniz dizinin komutu animasyonun çıktı yerleştirilen (kullanmakta olduğunuz sürece `-o|--output` seçeneği belirli bir dizin belirtin).</span><span class="sxs-lookup"><span data-stu-id="1da42-212">After the template is installed from the file system, use the template by executing the `dotnet new <TEMPLATE>` command from the directory where you want to the template engine's output placed (unless you're using the `-o|--output` option to specify a specific directory).</span></span> <span data-ttu-id="1da42-213">Daha fazla bilgi için bkz: [ `dotnet new` seçenekleri](~/docs/core/tools/dotnet-new.md#options).</span><span class="sxs-lookup"><span data-stu-id="1da42-213">For more information, see [`dotnet new` Options](~/docs/core/tools/dotnet-new.md#options).</span></span> <span data-ttu-id="1da42-214">Şablonun kısa ad doğrudan tedarik `dotnet new` komutu.</span><span class="sxs-lookup"><span data-stu-id="1da42-214">Supply the template's short name directly to the `dotnet new` command.</span></span>

<span data-ttu-id="1da42-215">Öğesinde oluşturulan yeni bir proje klasöründeki *C:\Users\\\<kullanıcı > \Documents\Projects\MyConsoleApp*, bir proje oluşturun `garciaconsole` şablonu:</span><span class="sxs-lookup"><span data-stu-id="1da42-215">From a new project folder created at *C:\Users\\\<USER>\Documents\Projects\MyConsoleApp*, create a project from the `garciaconsole` template:</span></span>

```console
dotnet new garciaconsole
```

### <a name="uninstall-the-template"></a><span data-ttu-id="1da42-216">Şablon kaldırma</span><span class="sxs-lookup"><span data-stu-id="1da42-216">Uninstall the template</span></span>

<span data-ttu-id="1da42-217">Yerel dosya sistemine şablon oluşturduysanız *C:\Users\\\<kullanıcı > \Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp*, kendisiyle kaldırmak `-u|--uninstall` anahtar ve yolu Şablon klasör:</span><span class="sxs-lookup"><span data-stu-id="1da42-217">If you created the template on your local file system at *C:\Users\\\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp*, uninstall it with the `-u|--uninstall` switch and the path to the template folder:</span></span>

```console
dotnet new -u C:\Users\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> <span data-ttu-id="1da42-218">Şablon, yerel dosya sisteminden kaldırmak için yol tam olarak nitelemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="1da42-218">To uninstall the template from your local file system, you need to fully qualify the path.</span></span> <span data-ttu-id="1da42-219">Örneğin, *C:\Users\\\<kullanıcı > \Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp* çalışır, ancak *./GarciaSoftware.ConsoleTemplate.CSharp* kapsayan klasörden almayacak.</span><span class="sxs-lookup"><span data-stu-id="1da42-219">For example, *C:\Users\\\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="1da42-220">Ayrıca, şablonu yoldaki son sonlandırma dizin eğik çizgi eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="1da42-220">Additionally, do not include a final terminating directory slash on your template path.</span></span>

## <a name="see-also"></a><span data-ttu-id="1da42-221">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1da42-221">See also</span></span>

[<span data-ttu-id="1da42-222">DotNet/şablon GitHub deposuna Wiki</span><span class="sxs-lookup"><span data-stu-id="1da42-222">dotnet/templating GitHub repo Wiki</span></span>](https://github.com/dotnet/templating/wiki)  
[<span data-ttu-id="1da42-223">DotNet/dotnet-şablonu-samples GitHub depo</span><span class="sxs-lookup"><span data-stu-id="1da42-223">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)  
[<span data-ttu-id="1da42-224">Dotnet için kendi şablonlarınızı yeni oluşturma</span><span class="sxs-lookup"><span data-stu-id="1da42-224">How to create your own templates for dotnet new</span></span>](https://blogs.msdn.microsoft.com/dotnet/2017/04/02/how-to-create-your-own-templates-for-dotnet-new/)  
[<span data-ttu-id="1da42-225">*Template.JSON* JSON şeması depolama şema</span><span class="sxs-lookup"><span data-stu-id="1da42-225">*template.json* schema at the JSON Schema Store</span></span>](http://json.schemastore.org/template)  
