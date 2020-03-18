---
title: Dotnet yeni için özel şablonlar
description: Her tür .NET projesi veya dosyası için özel şablonlar hakkında bilgi edinin.
author: thraka
ms.date: 06/14/2019
ms.openlocfilehash: 8e1ac4ca21a8a90ad0f7c9bd3dd11281eb4a6e02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73420877"
---
# <a name="custom-templates-for-dotnet-new"></a><span data-ttu-id="edd3c-103">Dotnet yeni için özel şablonlar</span><span class="sxs-lookup"><span data-stu-id="edd3c-103">Custom templates for dotnet new</span></span>

<span data-ttu-id="edd3c-104">[.NET Core SDK,](https://dotnet.microsoft.com/download) zaten yüklenmiş ve kullanmaya hazır birçok şablonla birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="edd3c-104">The [.NET Core SDK](https://dotnet.microsoft.com/download) comes with many templates already installed and ready for you to use.</span></span> <span data-ttu-id="edd3c-105">[ `dotnet new` Komut](dotnet-new.md) yalnızca şablon kullanmanın değil, şablonların nasıl yüklenir ve kaldırılabilen yoludur.</span><span class="sxs-lookup"><span data-stu-id="edd3c-105">The [`dotnet new` command](dotnet-new.md) isn't only the way to use a template, but also how to install and uninstall templates.</span></span> <span data-ttu-id="edd3c-106">.NET Core 2.0 ile başlayarak, uygulama, hizmet, araç veya sınıf kitaplığı gibi her tür proje için kendi özel şablonlarınızı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="edd3c-106">Starting with .NET Core 2.0, you can create your own custom templates for any type of project, such as an app, service, tool, or class library.</span></span> <span data-ttu-id="edd3c-107">Yapılandırma dosyası gibi bir veya daha fazla bağımsız dosyayı çıktılayan bir şablon bile oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="edd3c-107">You can even create a template that outputs one or more independent files, such as a configuration file.</span></span>

<span data-ttu-id="edd3c-108">NuGet paketinden özel şablonlar yükleyebilirsiniz, herhangi bir NuGet akışına doğrudan nuget *.nupkg* dosyasına başvurarak veya şablonu içeren bir dosya sistemi dizini belirterek.</span><span class="sxs-lookup"><span data-stu-id="edd3c-108">You can install custom templates from a NuGet package on any NuGet feed, by referencing a NuGet *.nupkg* file directly, or by specifying a file system directory that contains the template.</span></span> <span data-ttu-id="edd3c-109">Şablon altyapısı, değerleri değiştirmenize, dosyaları eklemenize ve hariç tutmanıza ve şablonuniz kullanıldığında özel işleme işlemlerini yürütmenize olanak tanıyan özellikler sunar.</span><span class="sxs-lookup"><span data-stu-id="edd3c-109">The template engine offers features that allow you to replace values, include and exclude files, and execute custom processing operations when your template is used.</span></span>

<span data-ttu-id="edd3c-110">Şablon motoru açık kaynak koddur ve çevrimiçi kod deposu GitHub'da [dotnet/templating'dedir.](https://github.com/dotnet/templating/)</span><span class="sxs-lookup"><span data-stu-id="edd3c-110">The template engine is open source, and the online code repository is at [dotnet/templating](https://github.com/dotnet/templating/) on GitHub.</span></span> <span data-ttu-id="edd3c-111">Şablon örnekleri için [dotnet/dotnet şablon-örnekleri](https://github.com/dotnet/dotnet-template-samples) repo'yu ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="edd3c-111">Visit the [dotnet/dotnet-template-samples](https://github.com/dotnet/dotnet-template-samples) repo for samples of templates.</span></span> <span data-ttu-id="edd3c-112">Üçüncü taraflardan gelen şablonlar da dahil olmak üzere daha fazla şablon, GitHub'da [yeni dotnet için Kullanılabilir şablonlarda](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new) bulunur.</span><span class="sxs-lookup"><span data-stu-id="edd3c-112">More templates, including templates from third parties, are found at [Available templates for dotnet new](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new) on GitHub.</span></span> <span data-ttu-id="edd3c-113">Özel şablonlar oluşturma ve kullanma hakkında daha fazla bilgi için dotnet yeni ve [dotnet/templating GitHub repo Wiki](https://github.com/dotnet/templating/wiki) [için kendi şablonlarınızı nasıl oluşturabilirsiniz'](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/) a bakın.</span><span class="sxs-lookup"><span data-stu-id="edd3c-113">For more information about creating and using custom templates, see [How to create your own templates for dotnet new](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/) and the [dotnet/templating GitHub repo Wiki](https://github.com/dotnet/templating/wiki).</span></span>

<span data-ttu-id="edd3c-114">Bir iz buzunu takip etmek ve şablon oluşturmak [için, dotnet yeni öğreticisi için özel bir şablon oluştur'a](../tutorials/cli-templates-create-item-template.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="edd3c-114">To follow a walkthrough and create a template, see the [Create a custom template for dotnet new](../tutorials/cli-templates-create-item-template.md) tutorial.</span></span>

### <a name="net-default-templates"></a><span data-ttu-id="edd3c-115">.NET varsayılan şablonları</span><span class="sxs-lookup"><span data-stu-id="edd3c-115">.NET default templates</span></span>

<span data-ttu-id="edd3c-116">[.NET Core SDK'yı](https://dotnet.microsoft.com/download)yüklediğinizde, konsol uygulamaları, sınıf kitaplıkları, birim test projeleri, ASP.NET Core uygulamaları [(Açısal](https://angular.io/) ve [Tepki](https://facebook.github.io/react/) projeleri dahil) ve yapılandırma dosyaları dahil olmak üzere proje ve dosya oluşturmak için bir düzineden fazla yerleşik şablon alırsınız.</span><span class="sxs-lookup"><span data-stu-id="edd3c-116">When you install the [.NET Core SDK](https://dotnet.microsoft.com/download), you receive over a dozen built-in templates for creating projects and files, including console apps, class libraries, unit test projects, ASP.NET Core apps (including [Angular](https://angular.io/) and [React](https://facebook.github.io/react/) projects), and configuration files.</span></span> <span data-ttu-id="edd3c-117">Yerleşik şablonları listelemek için komutu `dotnet new` `-l|--list` seçeneğiyle çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="edd3c-117">To list the built-in templates, run the `dotnet new` command with the `-l|--list` option:</span></span>

```dotnetcli
dotnet new --list
```

## <a name="configuration"></a><span data-ttu-id="edd3c-118">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="edd3c-118">Configuration</span></span>

<span data-ttu-id="edd3c-119">Şablon aşağıdaki bölümlerden oluşur:</span><span class="sxs-lookup"><span data-stu-id="edd3c-119">A template is composed of the following parts:</span></span>

- <span data-ttu-id="edd3c-120">Kaynak dosyaları ve klasörleri.</span><span class="sxs-lookup"><span data-stu-id="edd3c-120">Source files and folders.</span></span>
- <span data-ttu-id="edd3c-121">Yapılandırma dosyası (*template.json*).</span><span class="sxs-lookup"><span data-stu-id="edd3c-121">A configuration file (*template.json*).</span></span>

### <a name="source-files-and-folders"></a><span data-ttu-id="edd3c-122">Kaynak dosya ve klasörler</span><span class="sxs-lookup"><span data-stu-id="edd3c-122">Source files and folders</span></span>

<span data-ttu-id="edd3c-123">Kaynak dosya ve `dotnet new <TEMPLATE>` klasörler, komut çalıştırıldığında şablon altyapısının kullanmasını istediğiniz dosya ve klasörleri içerir.</span><span class="sxs-lookup"><span data-stu-id="edd3c-123">The source files and folders include whatever files and folders you want the template engine to use when the `dotnet new <TEMPLATE>` command is run.</span></span> <span data-ttu-id="edd3c-124">Şablon altyapısı, proje üretmek için *çalıştırılabilir projeleri* kaynak kodu olarak kullanmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="edd3c-124">The template engine is designed to use *runnable projects* as source code to produce projects.</span></span> <span data-ttu-id="edd3c-125">Bunun birkaç faydası vardır:</span><span class="sxs-lookup"><span data-stu-id="edd3c-125">This has several benefits:</span></span>

- <span data-ttu-id="edd3c-126">Şablon altyapısı, projenizin kaynak koduna özel belirteçler enjekte etmenizi gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="edd3c-126">The template engine doesn't require you to inject special tokens into your project's source code.</span></span>
- <span data-ttu-id="edd3c-127">Kod dosyaları özel dosyalar değildir veya şablon altyapısıyla çalışmak için herhangi bir şekilde değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="edd3c-127">The code files aren't special files or modified in any way to work with the template engine.</span></span> <span data-ttu-id="edd3c-128">Bu nedenle, projelerle çalışırken normalde kullandığınız araçlar şablon içeriğiyle de çalışır.</span><span class="sxs-lookup"><span data-stu-id="edd3c-128">So, the tools you normally use when working with projects also work with template content.</span></span>
- <span data-ttu-id="edd3c-129">Şablon projelerinizi, diğer projeleriniz için yaptığınız gibi oluşturur, çalıştırın ve hata ayıklarsınız.</span><span class="sxs-lookup"><span data-stu-id="edd3c-129">You build, run, and debug your template projects just like you do for any of your other projects.</span></span>
- <span data-ttu-id="edd3c-130">Projeye bir *./.template.config/template.json* yapılandırma dosyası ekleyerek varolan bir projeden hızlı bir şekilde şablon oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="edd3c-130">You can quickly create a template from an existing project just by adding a *./.template.config/template.json* configuration file to the project.</span></span>

<span data-ttu-id="edd3c-131">Şablonda depolanan dosya ve klasörler resmi .NET proje türleri ile sınırlı değildir.</span><span class="sxs-lookup"><span data-stu-id="edd3c-131">Files and folders stored in the template aren't limited to formal .NET project types.</span></span> <span data-ttu-id="edd3c-132">Kaynak dosyaları ve klasörleri, şablon altyapısı çıktıolarak yalnızca bir dosya oluştursa bile, şablon kullanıldığında oluşturmak istediğiniz içerikten oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="edd3c-132">Source files and folders may consist of any content that you wish to create when the template is used, even if the template engine produces just one file as its output.</span></span>

<span data-ttu-id="edd3c-133">Şablon tarafından oluşturulan dosyalar, *template.json* yapılandırma dosyasında sağladığınız mantık ve ayarlara göre değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="edd3c-133">Files generated by the template can be modified based on logic and settings you've provided in the *template.json* configuration file.</span></span> <span data-ttu-id="edd3c-134">Kullanıcı, seçenekleri `dotnet new <TEMPLATE>` komuta geçirerek bu ayarları geçersiz kılabilir.</span><span class="sxs-lookup"><span data-stu-id="edd3c-134">The user can override these settings by passing options to the `dotnet new <TEMPLATE>` command.</span></span> <span data-ttu-id="edd3c-135">Özel mantığın yaygın bir örneği, şablon tarafından dağıtılan kod dosyasındaki bir sınıf veya değişken için ad sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="edd3c-135">A common example of custom logic is providing a name for a class or variable in the code file that's deployed by a template.</span></span>

### <a name="templatejson"></a><span data-ttu-id="edd3c-136">template.json</span><span class="sxs-lookup"><span data-stu-id="edd3c-136">template.json</span></span>

<span data-ttu-id="edd3c-137">*template.json* dosyası şablonun kök dizininde bir *.template.config* klasörüne yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="edd3c-137">The *template.json* file is placed in a *.template.config* folder in the root directory of the template.</span></span> <span data-ttu-id="edd3c-138">Dosya şablon motoruna yapılandırma bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="edd3c-138">The file provides configuration information to the template engine.</span></span> <span data-ttu-id="edd3c-139">Minimum yapılandırma, işlevsel bir şablon oluşturmak için yeterli olan aşağıdaki tabloda gösterilen üyeleri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="edd3c-139">The minimum configuration requires the members shown in the following table, which is sufficient to create a functional template.</span></span>

| <span data-ttu-id="edd3c-140">Üye</span><span class="sxs-lookup"><span data-stu-id="edd3c-140">Member</span></span>            | <span data-ttu-id="edd3c-141">Tür</span><span class="sxs-lookup"><span data-stu-id="edd3c-141">Type</span></span>          | <span data-ttu-id="edd3c-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="edd3c-142">Description</span></span> |
| ----------------- | ------------- | ----------- |
| `$schema`         | <span data-ttu-id="edd3c-143">URI</span><span class="sxs-lookup"><span data-stu-id="edd3c-143">URI</span></span>           | <span data-ttu-id="edd3c-144">*template.json* dosyası için JSON şeması.</span><span class="sxs-lookup"><span data-stu-id="edd3c-144">The JSON schema for the *template.json* file.</span></span> <span data-ttu-id="edd3c-145">JSON şemalarını destekleyen editörler şema belirtildiğinde JSON düzenleme özelliklerini etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="edd3c-145">Editors that support JSON schemas enable JSON-editing features when the schema is specified.</span></span> <span data-ttu-id="edd3c-146">Örneğin, [Visual Studio Code](https://code.visualstudio.com/) intelliSense etkinleştirmek için bu üye gerektirir.</span><span class="sxs-lookup"><span data-stu-id="edd3c-146">For example, [Visual Studio Code](https://code.visualstudio.com/) requires this member to enable IntelliSense.</span></span> <span data-ttu-id="edd3c-147">`http://json.schemastore.org/template`Bir değer kullanın.</span><span class="sxs-lookup"><span data-stu-id="edd3c-147">Use a value of `http://json.schemastore.org/template`.</span></span> |
| `author`          | <span data-ttu-id="edd3c-148">string</span><span class="sxs-lookup"><span data-stu-id="edd3c-148">string</span></span>        | <span data-ttu-id="edd3c-149">Şablonun yazarı.</span><span class="sxs-lookup"><span data-stu-id="edd3c-149">The author of the template.</span></span> |
| `classifications` | <span data-ttu-id="edd3c-150">dizi(string)</span><span class="sxs-lookup"><span data-stu-id="edd3c-150">array(string)</span></span> | <span data-ttu-id="edd3c-151">Şablonu ararken bir kullanıcının şablonu bulmak için kullanabileceği sıfır veya daha fazla özellik.</span><span class="sxs-lookup"><span data-stu-id="edd3c-151">Zero or more characteristics of the template that a user might use to find the template when searching for it.</span></span> <span data-ttu-id="edd3c-152">Sınıflandırmalar, komutu kullanarak üretilen şablonlar listesinde göründüğünde *Etiketler* sütununda `dotnet new -l|--list` da görünür.</span><span class="sxs-lookup"><span data-stu-id="edd3c-152">The classifications also appear in the *Tags* column when it appears in a list of templates produced by using the `dotnet new -l|--list` command.</span></span> |
| `identity`        | <span data-ttu-id="edd3c-153">string</span><span class="sxs-lookup"><span data-stu-id="edd3c-153">string</span></span>        | <span data-ttu-id="edd3c-154">Bu şablon için benzersiz bir ad.</span><span class="sxs-lookup"><span data-stu-id="edd3c-154">A unique name for this template.</span></span> |
| `name`            | <span data-ttu-id="edd3c-155">string</span><span class="sxs-lookup"><span data-stu-id="edd3c-155">string</span></span>        | <span data-ttu-id="edd3c-156">Kullanıcıların görmesi gereken şablonun adı.</span><span class="sxs-lookup"><span data-stu-id="edd3c-156">The name for the template that users should see.</span></span> |
| `shortName`       | <span data-ttu-id="edd3c-157">string</span><span class="sxs-lookup"><span data-stu-id="edd3c-157">string</span></span>        | <span data-ttu-id="edd3c-158">Şablon adının gui üzerinden seçilmeden kullanıcı tarafından belirtildiği ortamlara uygulanan şablonu seçmek için varsayılan kısaltma adı.</span><span class="sxs-lookup"><span data-stu-id="edd3c-158">A default shorthand name for selecting the template that applies to environments where the template name is specified by the user, not selected via a GUI.</span></span> <span data-ttu-id="edd3c-159">Örneğin, cli komutları ile bir komut istemi şablonları kullanırken kısa ad yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="edd3c-159">For example, the short name is useful when using templates from a command prompt with CLI commands.</span></span> |

<span data-ttu-id="edd3c-160">*template.json* dosyası için tam şema [JSON Schema Store'da](http://json.schemastore.org/template)bulunur.</span><span class="sxs-lookup"><span data-stu-id="edd3c-160">The full schema for the *template.json* file is found at the [JSON Schema Store](http://json.schemastore.org/template).</span></span> <span data-ttu-id="edd3c-161">*template.json* dosyası hakkında daha fazla bilgi [için, dotnet templating wiki](https://github.com/dotnet/templating/wiki)bakın.</span><span class="sxs-lookup"><span data-stu-id="edd3c-161">For more information about the *template.json* file, see the [dotnet templating wiki](https://github.com/dotnet/templating/wiki).</span></span>

#### <a name="example"></a><span data-ttu-id="edd3c-162">Örnek</span><span class="sxs-lookup"><span data-stu-id="edd3c-162">Example</span></span>

<span data-ttu-id="edd3c-163">Örneğin, burada iki içerik dosyası içeren bir şablon klasörü var: *console.cs* ve *readme.txt*.</span><span class="sxs-lookup"><span data-stu-id="edd3c-163">For example, here is a template folder that contains two content files: *console.cs* and *readme.txt*.</span></span> <span data-ttu-id="edd3c-164">*Template.json* dosyasını içeren *.template.config* adlı gerekli klasör olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="edd3c-164">Take notice that there is the required folder named *.template.config* that contains the *template.json* file.</span></span>

```text
└───mytemplate
    │   console.cs
    │   readme.txt
    │
    └───.template.config
            template.json
```

<span data-ttu-id="edd3c-165">*template.json* dosyası aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="edd3c-165">The *template.json* file looks like the following:</span></span>

```json
{
  "$schema": "http://json.schemastore.org/template",
  "author": "Travis Chau",
  "classifications": [ "Common", "Console" ],
  "identity": "AdatumCorporation.ConsoleTemplate.CSharp",
  "name": "Adatum Corporation Console Application",
  "shortName": "adatumconsole"
}
```

<span data-ttu-id="edd3c-166">*Mytemplate* klasörü yüklenebilir bir şablon paketidir.</span><span class="sxs-lookup"><span data-stu-id="edd3c-166">The *mytemplate* folder is an installable template pack.</span></span> <span data-ttu-id="edd3c-167">Paket yüklendikten sonra `shortName` `dotnet new` komutu ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="edd3c-167">Once the pack is installed, the `shortName` can be used with the `dotnet new` command.</span></span> <span data-ttu-id="edd3c-168">Örneğin, `dotnet new adatumconsole` geçerli `console.cs` klasöre `readme.txt` ve dosyaları çıktı olur.</span><span class="sxs-lookup"><span data-stu-id="edd3c-168">For example, `dotnet new adatumconsole` would output the `console.cs` and `readme.txt` files to the current folder.</span></span>

## <a name="packing-a-template-into-a-nuget-package-nupkg-file"></a><span data-ttu-id="edd3c-169">Şablonu NuGet paketine paketleme (nupkg dosyası)</span><span class="sxs-lookup"><span data-stu-id="edd3c-169">Packing a template into a NuGet package (nupkg file)</span></span>

<span data-ttu-id="edd3c-170">Özel bir [şablon, dotnet paketi](dotnet-pack.md) komutu ve *.csproj* dosyasıyla birlikte paketlenir.</span><span class="sxs-lookup"><span data-stu-id="edd3c-170">A custom template is packed with the [dotnet pack](dotnet-pack.md) command and a *.csproj* file.</span></span> <span data-ttu-id="edd3c-171">Alternatif olarak, [NuGet](https://docs.microsoft.com/nuget/tools/nuget-exe-cli-reference) [nuget paketi](https://docs.microsoft.com/nuget/tools/cli-ref-pack) komutu ile birlikte bir *.nuspec* dosyası ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="edd3c-171">Alternatively, [NuGet](https://docs.microsoft.com/nuget/tools/nuget-exe-cli-reference) can be used with the [nuget pack](https://docs.microsoft.com/nuget/tools/cli-ref-pack) command along with a *.nuspec* file.</span></span> <span data-ttu-id="edd3c-172">Ancak, NuGet Linux ve MacOS'ta Windows ve [Mono'da](https://www.mono-project.com/) .NET Framework gerektirir.</span><span class="sxs-lookup"><span data-stu-id="edd3c-172">However, NuGet requires the .NET Framework on Windows and [Mono](https://www.mono-project.com/) on Linux and MacOS.</span></span>

<span data-ttu-id="edd3c-173">*.csproj* dosyası geleneksel kod-project *.csproj* dosyasından biraz farklıdır.</span><span class="sxs-lookup"><span data-stu-id="edd3c-173">The *.csproj* file is slightly different from a traditional code-project *.csproj* file.</span></span> <span data-ttu-id="edd3c-174">Aşağıdaki ayarlara dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="edd3c-174">Note the following settings:</span></span>

01. <span data-ttu-id="edd3c-175">Ayar `<PackageType>` eklenir ve '' olarak `Template`ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="edd3c-175">The `<PackageType>` setting is added and set to `Template`.</span></span>
01. <span data-ttu-id="edd3c-176">Ayar `<PackageVersion>` eklenir ve geçerli bir [NuGet sürüm numarasına](/nuget/reference/package-versioning)ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="edd3c-176">The `<PackageVersion>` setting is added and set to a valid [NuGet version number](/nuget/reference/package-versioning).</span></span>
01. <span data-ttu-id="edd3c-177">Ayar `<PackageId>` eklenir ve benzersiz bir tanımlayıcıya ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="edd3c-177">The `<PackageId>` setting is added and set to a unique identifier.</span></span> <span data-ttu-id="edd3c-178">Bu tanımlayıcı şablon paketini kaldırmak için kullanılır ve şablon paketinizi kaydetmek için NuGet akışları tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="edd3c-178">This identifier is used to uninstall the template pack and is used by NuGet feeds to register your template pack.</span></span>
01. <span data-ttu-id="edd3c-179">Genel meta veri ayarları `<Title>`ayarlanmalıdır: , `<Authors>`, `<Description>`, ve `<PackageTags>`.</span><span class="sxs-lookup"><span data-stu-id="edd3c-179">Generic metadata settings should be set: `<Title>`, `<Authors>`, `<Description>`, and `<PackageTags>`.</span></span>
01. <span data-ttu-id="edd3c-180">Şablon `<TargetFramework>` işlemi tarafından üretilen ikili kullanılmasa bile ayar ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="edd3c-180">The `<TargetFramework>` setting must be set, even though the binary produced by the template process isn't used.</span></span> <span data-ttu-id="edd3c-181">Aşağıdaki örnekte ' olarak `netstandard2.0`ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="edd3c-181">In the example below it's set to `netstandard2.0`.</span></span>

<span data-ttu-id="edd3c-182">*.nupkg* NuGet paketi biçimindeki şablon paketi, tüm şablonların paket içindeki *içerik* klasöründe depolansın.</span><span class="sxs-lookup"><span data-stu-id="edd3c-182">A template pack, in the form of a *.nupkg* NuGet package, requires that all templates be stored in the *content* folder within the package.</span></span> <span data-ttu-id="edd3c-183">Oluşturulan *.nupkg'ın* şablon paketi olarak yüklenebilmesi için *.csproj* dosyasına eklenecek birkaç ayar daha vardır:</span><span class="sxs-lookup"><span data-stu-id="edd3c-183">There are a few more settings to add to a *.csproj* file to ensure that the generated *.nupkg* can be installed as a template pack:</span></span>

01. <span data-ttu-id="edd3c-184">Ayar, `<IncludeContentInPack>` projenin `true` NuGet paketinde **içerik** olarak ayarlattığı herhangi bir dosyayı içerecek şekilde ayarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="edd3c-184">The `<IncludeContentInPack>` setting is set to `true` to include any file the project sets as **content** in the NuGet package.</span></span>
01. <span data-ttu-id="edd3c-185">Ayar, `<IncludeBuildOutput>` derleyici `false` tarafından oluşturulan tüm ikilileri NuGet paketinden hariç tutmak üzere ayarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="edd3c-185">The `<IncludeBuildOutput>` setting is set to `false` to exclude all binaries generated by the compiler from the NuGet package.</span></span>
01. <span data-ttu-id="edd3c-186">Ayar' `<ContentTargetFolders>` ı `content`' na göre ayarlar.</span><span class="sxs-lookup"><span data-stu-id="edd3c-186">The `<ContentTargetFolders>` setting is set to `content`.</span></span> <span data-ttu-id="edd3c-187">Bu, **içerik** olarak ayarlanan dosyaların NuGet paketindeki *içerik* klasöründe depolandırılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="edd3c-187">This makes sure that the files set as **content** are stored in the *content* folder in the NuGet package.</span></span> <span data-ttu-id="edd3c-188">NuGet paketindeki bu klasör, dotnet şablon sistemi tarafından ayrıştırılır.</span><span class="sxs-lookup"><span data-stu-id="edd3c-188">This folder in the NuGet package is parsed by the dotnet template system.</span></span>

<span data-ttu-id="edd3c-189">Tüm kod dosyalarının şablon projeniz tarafından derlenmesini hariç `<Compile Remove="**\*" />` tutmanın kolay bir yolu, proje dosyanızdaki öğeyi bir `<ItemGroup>` öğenin içinde kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="edd3c-189">An easy way to exclude all code files from being compiled by your template project is by using the `<Compile Remove="**\*" />` item in your project file, inside an `<ItemGroup>` element.</span></span>

<span data-ttu-id="edd3c-190">Şablon paketinizi yapılandırmanın kolay bir yolu, tüm şablonları tek tek klasörlere, sonra da her şablon klasörünü *.csproj* dosyanızla aynı dizinde bulunan *şablonlar* klasörünün içine koymaktır.</span><span class="sxs-lookup"><span data-stu-id="edd3c-190">An easy way to structure your template pack is to put all templates in individual folders, and then each template folder inside of a *templates* folder that is located in the same directory as your *.csproj* file.</span></span> <span data-ttu-id="edd3c-191">Bu şekilde, şablonlara tüm dosya ve *klasörleri* **içerik**olarak eklemek için tek bir proje öğesi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="edd3c-191">This way, you can use a single project item to include all files and folders in the *templates* as **content**.</span></span> <span data-ttu-id="edd3c-192">Bir `<ItemGroup>` öğenin içinde `<Content Include="templates\**\*" Exclude="templates\**\bin\**;templates\**\obj\**" />` bir öğe oluşturun.</span><span class="sxs-lookup"><span data-stu-id="edd3c-192">Inside of an `<ItemGroup>` element, create a `<Content Include="templates\**\*" Exclude="templates\**\bin\**;templates\**\obj\**" />` item.</span></span>

<span data-ttu-id="edd3c-193">Aşağıda, yukarıdaki tüm yönergeleri izleyen bir örnek *.csproj* dosyası verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="edd3c-193">Here is an example *.csproj* file that follows all of the guidelines above.</span></span> <span data-ttu-id="edd3c-194">*Şablonlar* alt klasörünü *içerik* paketi klasörüne paketler ve herhangi bir kod dosyasının derlenmesini hariç tutar.</span><span class="sxs-lookup"><span data-stu-id="edd3c-194">It packs the *templates* child folder to the *content* package folder and excludes any code file from being compiled.</span></span>

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

<span data-ttu-id="edd3c-195">Aşağıdaki örnekte, şablon paketi oluşturmak için *.csproj* kullanmanın dosya ve klasör yapısı gösterin.</span><span class="sxs-lookup"><span data-stu-id="edd3c-195">The example below demonstrates the file and folder structure of using a *.csproj* to create a template pack.</span></span> <span data-ttu-id="edd3c-196">*MyDotnetTemplates.csproj* dosyası ve *şablonlar* klasörü her ikisi de *project_folder*adlı bir dizinin kökünde yer alır.</span><span class="sxs-lookup"><span data-stu-id="edd3c-196">The *MyDotnetTemplates.csproj* file and *templates* folder are both located at the root of a directory named *project_folder*.</span></span> <span data-ttu-id="edd3c-197">*Şablonlar* klasörü iki şablon, *mytemplate1* ve *mytemplate2*içerir.</span><span class="sxs-lookup"><span data-stu-id="edd3c-197">The *templates* folder contains two templates, *mytemplate1* and *mytemplate2*.</span></span> <span data-ttu-id="edd3c-198">Her şablonda içerik dosyaları ve *template.json* config dosyası içeren bir *.template.config* klasörü bulunur.</span><span class="sxs-lookup"><span data-stu-id="edd3c-198">Each template has content files and a *.template.config* folder with a *template.json* config file.</span></span>

```text
project_folder
│   MyDotnetTemplates.csproj
│
└───templates
    ├───mytemplate1
    │   │   console.cs
    │   │   readme.txt
    │   │
    │   └───.template.config
    │           template.json
    │
    └───mytemplate2
        │   otherfile.cs
        │
        └───.template.config
                template.json
```

## <a name="installing-a-template"></a><span data-ttu-id="edd3c-199">Şablon yükleme</span><span class="sxs-lookup"><span data-stu-id="edd3c-199">Installing a template</span></span>

<span data-ttu-id="edd3c-200">Bir paket yüklemek için [dotnet yeni -i|--install](dotnet-new.md) komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="edd3c-200">Use the [dotnet new -i|--install](dotnet-new.md) command to install a package.</span></span>

### <a name="to-install-a-template-from-a-nuget-package-stored-at-nugetorg"></a><span data-ttu-id="edd3c-201">nuget.org'de depolanan bir NuGet paketinden şablon yüklemek için</span><span class="sxs-lookup"><span data-stu-id="edd3c-201">To install a template from a NuGet package stored at nuget.org</span></span>

<span data-ttu-id="edd3c-202">Şablon paketi yüklemek için NuGet paket tanımlayıcısını kullanın.</span><span class="sxs-lookup"><span data-stu-id="edd3c-202">Use the NuGet package identifier to install a template package.</span></span>

```dotnetcli
dotnet new -i <NUGET_PACKAGE_ID>
```

### <a name="to-install-a-template-from-a-local-nupkg-file"></a><span data-ttu-id="edd3c-203">Yerel bir nupkg dosyasından şablon yüklemek için</span><span class="sxs-lookup"><span data-stu-id="edd3c-203">To install a template from a local nupkg file</span></span>

<span data-ttu-id="edd3c-204">*.nupkg* NuGet paket dosyasına giden yolu sağlayın.</span><span class="sxs-lookup"><span data-stu-id="edd3c-204">Provide the path to a *.nupkg* NuGet package file.</span></span>

```dotnetcli
dotnet new -i <PATH_TO_NUPKG_FILE>
```

### <a name="to-install-a-template-from-a-file-system-directory"></a><span data-ttu-id="edd3c-205">Dosya sistemi dizininden şablon yüklemek için</span><span class="sxs-lookup"><span data-stu-id="edd3c-205">To install a template from a file system directory</span></span>

<span data-ttu-id="edd3c-206">Şablonlar yukarıdaki örnekten *mytemplate1* klasörü gibi bir şablon klasöründen yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="edd3c-206">Templates can be installed from a template folder, such as the *mytemplate1* folder from the example above.</span></span> <span data-ttu-id="edd3c-207">*.template.config* klasörünün klasör yolunu belirtin.</span><span class="sxs-lookup"><span data-stu-id="edd3c-207">Specify the folder path of the *.template.config* folder.</span></span> <span data-ttu-id="edd3c-208">Şablon dizinine giden yolun mutlak olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="edd3c-208">The path to the template directory does not need to be absolute.</span></span> <span data-ttu-id="edd3c-209">Ancak, bir klasörden yüklenen bir şablonu kaldırmak için mutlak bir yol gereklidir.</span><span class="sxs-lookup"><span data-stu-id="edd3c-209">However, an absolute path is required to uninstall a template that is installed from a folder.</span></span>

```dotnetcli
dotnet new -i <FILE_SYSTEM_DIRECTORY>
```

## <a name="get-a-list-of-installed-templates"></a><span data-ttu-id="edd3c-210">Yüklü şablonların listesini alma</span><span class="sxs-lookup"><span data-stu-id="edd3c-210">Get a list of installed templates</span></span>

<span data-ttu-id="edd3c-211">Diğer parametreler olmadan kaldır komutu, yüklenen tüm şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="edd3c-211">The uninstall command, without any other parameters, will list all installed templates.</span></span>

```dotnetcli
dotnet new -u
```

<span data-ttu-id="edd3c-212">Bu komut aşağıdaki çıktıya benzer bir şey döndürür:</span><span class="sxs-lookup"><span data-stu-id="edd3c-212">That command returns something similar to the following output:</span></span>

```console
Template Instantiation Commands for .NET Core CLI

Currently installed items:
  Microsoft.DotNet.Common.ItemTemplates
    Templates:
      global.json file (globaljson)
      NuGet Config (nugetconfig)
      Solution File (sln)
      Dotnet local tool manifest file (tool-manifest)
      Web Config (webconfig)
  Microsoft.DotNet.Common.ProjectTemplates.3.0
    Templates:
      Class library (classlib) C#
      Class library (classlib) F#
      Class library (classlib) VB
      Console Application (console) C#
      Console Application (console) F#
      Console Application (console) VB
...
```

<span data-ttu-id="edd3c-213">Sonra öğelerin ilk `Currently installed items:` düzeyi, şablonu kaldırmada kullanılan tanımlayıcılardır.</span><span class="sxs-lookup"><span data-stu-id="edd3c-213">The first level of items after `Currently installed items:` are the identifiers used in uninstalling a template.</span></span> <span data-ttu-id="edd3c-214">Ve yukarıdaki `Microsoft.DotNet.Common.ItemTemplates` örnekte, `Microsoft.DotNet.Common.ProjectTemplates.3.0` ve listelenir.</span><span class="sxs-lookup"><span data-stu-id="edd3c-214">And in the example above, `Microsoft.DotNet.Common.ItemTemplates` and `Microsoft.DotNet.Common.ProjectTemplates.3.0` are listed.</span></span> <span data-ttu-id="edd3c-215">Şablon bir dosya sistemi yolu kullanılarak yüklenmişse, bu tanımlayıcı *.template.config* klasörünün klasör yolu olacaktır.</span><span class="sxs-lookup"><span data-stu-id="edd3c-215">If the template was installed by using a file system path, this identifier will the folder path of the *.template.config* folder.</span></span>

## <a name="uninstalling-a-template"></a><span data-ttu-id="edd3c-216">Şablonu kaldırma</span><span class="sxs-lookup"><span data-stu-id="edd3c-216">Uninstalling a template</span></span>

<span data-ttu-id="edd3c-217">Paketi kaldırmak için [dotnet yeni -u|--kaldır](dotnet-new.md) komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="edd3c-217">Use the [dotnet new -u|--uninstall](dotnet-new.md) command to uninstall a package.</span></span>

<span data-ttu-id="edd3c-218">Paket nuget beslemesi veya *doğrudan .nupkg* dosyası tarafından yüklenmişse, tanımlayıcıyı sağlayın.</span><span class="sxs-lookup"><span data-stu-id="edd3c-218">If the package was installed by either a NuGet feed or by a *.nupkg* file directly, provide the identifier.</span></span>

```dotnetcli
dotnet new -u <NUGET_PACKAGE_ID>
```

<span data-ttu-id="edd3c-219">Paket *.template.config* klasörüne bir yol belirterek yüklendiyse, paketi kaldırmak için bu **mutlak** yolu kullanın.</span><span class="sxs-lookup"><span data-stu-id="edd3c-219">If the package was installed by specifying a path to the *.template.config* folder, use that **absolute** path to uninstall the package.</span></span> <span data-ttu-id="edd3c-220">`dotnet new -u` Komut tarafından sağlanan çıktıda şablonun mutlak yolunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="edd3c-220">You can see the absolute path of the template in the output provided by the `dotnet new -u` command.</span></span> <span data-ttu-id="edd3c-221">Daha fazla bilgi için yukarıdaki [yüklü şablonların listesini alın](#get-a-list-of-installed-templates) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="edd3c-221">For more information, see the [Get a list of installed templates](#get-a-list-of-installed-templates) section above.</span></span>

```dotnetcli
dotnet new -u <ABSOLUTE_FILE_SYSTEM_DIRECTORY>
```

## <a name="create-a-project-using-a-custom-template"></a><span data-ttu-id="edd3c-222">Özel bir şablon kullanarak proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="edd3c-222">Create a project using a custom template</span></span>

<span data-ttu-id="edd3c-223">Şablon yüklendikten sonra, önceden yüklenmiş başka `dotnet new <TEMPLATE>` bir şablonda olduğu gibi komutu çalıştırarak şablonu kullanın.</span><span class="sxs-lookup"><span data-stu-id="edd3c-223">After a template is installed, use the template by executing the `dotnet new <TEMPLATE>` command as you would with any other pre-installed template.</span></span> <span data-ttu-id="edd3c-224">Şablon ayarlarında [options](dotnet-new.md#options) yapılandırdığınız şablona özgü seçenekler de dahil olmak `dotnet new` üzere, komuta seçenekler de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="edd3c-224">You can also specify [options](dotnet-new.md#options) to the `dotnet new` command, including template-specific options you configured in the template settings.</span></span> <span data-ttu-id="edd3c-225">Şablonun kısa adını doğrudan komuta ver:</span><span class="sxs-lookup"><span data-stu-id="edd3c-225">Supply the template's short name directly to the command:</span></span>

```dotnetcli
dotnet new <TEMPLATE>
```

## <a name="see-also"></a><span data-ttu-id="edd3c-226">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="edd3c-226">See also</span></span>

- [<span data-ttu-id="edd3c-227">dotnet yeni (öğretici) için özel bir şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="edd3c-227">Create a custom template for dotnet new (tutorial)</span></span>](../tutorials/cli-templates-create-item-template.md)
- [<span data-ttu-id="edd3c-228">dotnet/templating GitHub repo Wiki</span><span class="sxs-lookup"><span data-stu-id="edd3c-228">dotnet/templating GitHub repo Wiki</span></span>](https://github.com/dotnet/templating/wiki)
- [<span data-ttu-id="edd3c-229">dotnet/dotnet-şablon-örnekleri GitHub repo</span><span class="sxs-lookup"><span data-stu-id="edd3c-229">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="edd3c-230">Dotnet yeni için kendi şablonlarınızı oluşturma</span><span class="sxs-lookup"><span data-stu-id="edd3c-230">How to create your own templates for dotnet new</span></span>](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/)
- [<span data-ttu-id="edd3c-231">json Schema Mağazası'nda *template.json* şema</span><span class="sxs-lookup"><span data-stu-id="edd3c-231">*template.json* schema at the JSON Schema Store</span></span>](http://json.schemastore.org/template)
