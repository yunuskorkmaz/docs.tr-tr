---
title: DotNet New için özel şablonlar
description: Herhangi bir .NET projesi veya dosya türü için özel şablonlar hakkında bilgi edinin.
author: adegeo
ms.date: 05/20/2020
ms.openlocfilehash: 55091ef9bb9f7a2aa24f585c94aa2a47960b1829
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874719"
---
# <a name="custom-templates-for-dotnet-new"></a><span data-ttu-id="66772-103">DotNet New için özel şablonlar</span><span class="sxs-lookup"><span data-stu-id="66772-103">Custom templates for dotnet new</span></span>

<span data-ttu-id="66772-104">[.NET Core SDK](https://dotnet.microsoft.com/download) , zaten yüklenmiş ve kullanıma hazırmış birçok şablon ile birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="66772-104">The [.NET Core SDK](https://dotnet.microsoft.com/download) comes with many templates already installed and ready for you to use.</span></span> <span data-ttu-id="66772-105">[ `dotnet new` Komut](dotnet-new.md) yalnızca bir şablonu kullanmanın ve ayrıca şablonların nasıl yükleneceğini ve kaldırılacağını gösteren bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="66772-105">The [`dotnet new` command](dotnet-new.md) isn't only the way to use a template, but also how to install and uninstall templates.</span></span> <span data-ttu-id="66772-106">.NET Core 2,0 ile başlayarak, bir uygulama, hizmet, araç veya sınıf kitaplığı gibi herhangi bir proje türü için kendi özel şablonlarınızı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66772-106">Starting with .NET Core 2.0, you can create your own custom templates for any type of project, such as an app, service, tool, or class library.</span></span> <span data-ttu-id="66772-107">Hatta bir yapılandırma dosyası gibi bir veya daha fazla bağımsız dosyayı çıkaran bir şablon oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66772-107">You can even create a template that outputs one or more independent files, such as a configuration file.</span></span>

<span data-ttu-id="66772-108">NuGet *. nupkg* dosyasına doğrudan başvurarak veya şablonu içeren bir dosya sistemi dizini belirterek herhangi bir NuGet akışında bir NuGet paketinden özel şablonlar yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66772-108">You can install custom templates from a NuGet package on any NuGet feed, by referencing a NuGet *.nupkg* file directly, or by specifying a file system directory that contains the template.</span></span> <span data-ttu-id="66772-109">Şablon altyapısı, şablon kullanılırken değerleri değiştirmenizi, dosyaları dahil ve dışlamalarını ve özel işleme işlemlerini yürütmeyi sağlayan özellikler sunar.</span><span class="sxs-lookup"><span data-stu-id="66772-109">The template engine offers features that allow you to replace values, include and exclude files, and execute custom processing operations when your template is used.</span></span>

<span data-ttu-id="66772-110">Şablon altyapısı açık kaynaktır ve çevrimiçi kod deposu GitHub 'da [DotNet/şablon](https://github.com/dotnet/templating/) oluşturma ' dır.</span><span class="sxs-lookup"><span data-stu-id="66772-110">The template engine is open source, and the online code repository is at [dotnet/templating](https://github.com/dotnet/templating/) on GitHub.</span></span> <span data-ttu-id="66772-111">Üçüncü taraflardan şablonlar da dahil olmak üzere diğer şablonlar, GitHub 'da [Yeni DotNet Için kullanılabilir şablonlarda](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new) bulunur.</span><span class="sxs-lookup"><span data-stu-id="66772-111">More templates, including templates from third parties, are found at [Available templates for dotnet new](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new) on GitHub.</span></span> <span data-ttu-id="66772-112">Özel şablonlar oluşturma ve kullanma hakkında daha fazla bilgi için bkz. [DotNet New için kendi şablonlarınızı oluşturma](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/) ve [DotNet/şablon GitHub depo wiki](https://github.com/dotnet/templating/wiki).</span><span class="sxs-lookup"><span data-stu-id="66772-112">For more information about creating and using custom templates, see [How to create your own templates for dotnet new](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/) and the [dotnet/templating GitHub repo Wiki](https://github.com/dotnet/templating/wiki).</span></span>

> [!NOTE]
> <span data-ttu-id="66772-113">Şablon örnekleri [DotNet/DotNet-Template-Samples](https://github.com/dotnet/dotnet-template-samples) GitHub deposunda mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="66772-113">Template examples are available at the [dotnet/dotnet-template-samples](https://github.com/dotnet/dotnet-template-samples) GitHub repository.</span></span> <span data-ttu-id="66772-114">Bununla birlikte, şablonların nasıl çalıştığını öğrenmek için bu örnekler iyi bir kaynaktır, depo arşivlenir ve artık korunmaz.</span><span class="sxs-lookup"><span data-stu-id="66772-114">However, while these examples are good resource for learning how the templates work, the repository is archived and no longer maintained.</span></span> <span data-ttu-id="66772-115">Örnekler güncel olmayabilir ve çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="66772-115">The examples may be out of date and no longer working.</span></span>

<span data-ttu-id="66772-116">Bir yönergeyi izlemek ve şablon oluşturmak için, [DotNet yeni öğretici için özel şablon oluşturma](../tutorials/cli-templates-create-item-template.md) makalesine bakın.</span><span class="sxs-lookup"><span data-stu-id="66772-116">To follow a walkthrough and create a template, see the [Create a custom template for dotnet new](../tutorials/cli-templates-create-item-template.md) tutorial.</span></span>

### <a name="net-default-templates"></a><span data-ttu-id="66772-117">.NET varsayılan şablonları</span><span class="sxs-lookup"><span data-stu-id="66772-117">.NET default templates</span></span>

<span data-ttu-id="66772-118">[.NET Core SDK](https://dotnet.microsoft.com/download)yüklediğinizde, konsol uygulamaları, sınıf kitaplıkları, birim testi projeleri, ASP.NET Core uygulamalar ( [angular](https://angular.io/) ve [tepki](https://facebook.github.io/react/) verme projeleri dahil) ve yapılandırma dosyaları dahil olmak üzere proje ve dosya oluşturmaya yönelik bir düzine yerleşik şablon üzerinden karşılaşırsınız.</span><span class="sxs-lookup"><span data-stu-id="66772-118">When you install the [.NET Core SDK](https://dotnet.microsoft.com/download), you receive over a dozen built-in templates for creating projects and files, including console apps, class libraries, unit test projects, ASP.NET Core apps (including [Angular](https://angular.io/) and [React](https://facebook.github.io/react/) projects), and configuration files.</span></span> <span data-ttu-id="66772-119">Yerleşik şablonları listelemek için `dotnet new` komutunu `-l|--list` seçeneğiyle çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="66772-119">To list the built-in templates, run the `dotnet new` command with the `-l|--list` option:</span></span>

```dotnetcli
dotnet new --list
```

## <a name="configuration"></a><span data-ttu-id="66772-120">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="66772-120">Configuration</span></span>

<span data-ttu-id="66772-121">Şablon, aşağıdaki bölümlerden oluşur:</span><span class="sxs-lookup"><span data-stu-id="66772-121">A template is composed of the following parts:</span></span>

- <span data-ttu-id="66772-122">Kaynak dosya ve klasörler.</span><span class="sxs-lookup"><span data-stu-id="66772-122">Source files and folders.</span></span>
- <span data-ttu-id="66772-123">Bir yapılandırma dosyası (*template.js*).</span><span class="sxs-lookup"><span data-stu-id="66772-123">A configuration file (*template.json*).</span></span>

### <a name="source-files-and-folders"></a><span data-ttu-id="66772-124">Kaynak dosya ve klasörler</span><span class="sxs-lookup"><span data-stu-id="66772-124">Source files and folders</span></span>

<span data-ttu-id="66772-125">Kaynak dosya ve klasörler, şablon altyapısının komut çalıştırıldığında kullanmasını istediğiniz dosya ve klasörleri içerir `dotnet new <TEMPLATE>` .</span><span class="sxs-lookup"><span data-stu-id="66772-125">The source files and folders include whatever files and folders you want the template engine to use when the `dotnet new <TEMPLATE>` command is run.</span></span> <span data-ttu-id="66772-126">Şablon altyapısı, proje üretmek için kaynak kodu olarak *runacitme projelerini* kullanmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="66772-126">The template engine is designed to use *runnable projects* as source code to produce projects.</span></span> <span data-ttu-id="66772-127">Bunun birkaç avantajı vardır:</span><span class="sxs-lookup"><span data-stu-id="66772-127">This has several benefits:</span></span>

- <span data-ttu-id="66772-128">Şablon altyapısı, projenizin kaynak koduna özel belirteçler eklemesine gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="66772-128">The template engine doesn't require you to inject special tokens into your project's source code.</span></span>
- <span data-ttu-id="66772-129">Kod dosyaları özel dosyalar değildir veya şablon altyapısıyla çalışmak için herhangi bir şekilde değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="66772-129">The code files aren't special files or modified in any way to work with the template engine.</span></span> <span data-ttu-id="66772-130">Bu nedenle, genellikle projelerle çalışırken kullandığınız araçlar şablon içeriğiyle de çalışır.</span><span class="sxs-lookup"><span data-stu-id="66772-130">So, the tools you normally use when working with projects also work with template content.</span></span>
- <span data-ttu-id="66772-131">Diğer projelerinizden herhangi biri için yaptığınız gibi şablon projelerinizi oluşturup hata ayıkladınız.</span><span class="sxs-lookup"><span data-stu-id="66772-131">You build, run, and debug your template projects just like you do for any of your other projects.</span></span>
- <span data-ttu-id="66772-132">Proje için yapılandırma dosyasına bir *./.template.config/template.js* ekleyerek, varolan bir projeden hızlıca bir şablon oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66772-132">You can quickly create a template from an existing project just by adding a *./.template.config/template.json* configuration file to the project.</span></span>

<span data-ttu-id="66772-133">Şablonda depolanan dosya ve klasörler, biçimsel .NET proje türleriyle sınırlı değildir.</span><span class="sxs-lookup"><span data-stu-id="66772-133">Files and folders stored in the template aren't limited to formal .NET project types.</span></span> <span data-ttu-id="66772-134">Şablon altyapısı çıkış olarak yalnızca bir dosya üretse bile, kaynak dosyalar ve klasörler, şablon kullanıldığında oluşturmak istediğiniz içerikten oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="66772-134">Source files and folders may consist of any content that you wish to create when the template is used, even if the template engine produces just one file as its output.</span></span>

<span data-ttu-id="66772-135">Şablon tarafından oluşturulan dosyalar, yapılandırma dosyasında *template.js* sağladığınız mantık ve ayarlara göre değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="66772-135">Files generated by the template can be modified based on logic and settings you've provided in the *template.json* configuration file.</span></span> <span data-ttu-id="66772-136">Kullanıcı, seçenekleri komuta geçirerek bu ayarları geçersiz kılabilir `dotnet new <TEMPLATE>` .</span><span class="sxs-lookup"><span data-stu-id="66772-136">The user can override these settings by passing options to the `dotnet new <TEMPLATE>` command.</span></span> <span data-ttu-id="66772-137">Özel mantığın ortak bir örneği, bir şablon tarafından dağıtılan kod dosyasındaki bir sınıf veya değişken için bir ad sağlar.</span><span class="sxs-lookup"><span data-stu-id="66772-137">A common example of custom logic is providing a name for a class or variable in the code file that's deployed by a template.</span></span>

### <a name="templatejson"></a><span data-ttu-id="66772-138">Üzerinde template.js</span><span class="sxs-lookup"><span data-stu-id="66772-138">template.json</span></span>

<span data-ttu-id="66772-139">Dosyadaki *template.js* , şablonun kök dizinindeki bir *.template.config* klasörüne yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="66772-139">The *template.json* file is placed in a *.template.config* folder in the root directory of the template.</span></span> <span data-ttu-id="66772-140">Dosya, şablon altyapısına yapılandırma bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="66772-140">The file provides configuration information to the template engine.</span></span> <span data-ttu-id="66772-141">En düşük yapılandırma, aşağıdaki tabloda gösterilen üyeleri gerektirir ve bu, işlevsel bir şablon oluşturmak için yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="66772-141">The minimum configuration requires the members shown in the following table, which is sufficient to create a functional template.</span></span>

| <span data-ttu-id="66772-142">Üye</span><span class="sxs-lookup"><span data-stu-id="66772-142">Member</span></span>            | <span data-ttu-id="66772-143">Tür</span><span class="sxs-lookup"><span data-stu-id="66772-143">Type</span></span>          | <span data-ttu-id="66772-144">Açıklama</span><span class="sxs-lookup"><span data-stu-id="66772-144">Description</span></span> |
| ----------------- | ------------- | ----------- |
| `$schema`         | <span data-ttu-id="66772-145">URI</span><span class="sxs-lookup"><span data-stu-id="66772-145">URI</span></span>           | <span data-ttu-id="66772-146">Dosyadaki *template.js* JSON şeması.</span><span class="sxs-lookup"><span data-stu-id="66772-146">The JSON schema for the *template.json* file.</span></span> <span data-ttu-id="66772-147">JSON şemalarını destekleyen düzenleyiciler, şema belirtildiğinde JSON düzenlemesi özelliklerini etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="66772-147">Editors that support JSON schemas enable JSON-editing features when the schema is specified.</span></span> <span data-ttu-id="66772-148">Örneğin, [Visual Studio Code](https://code.visualstudio.com/) IntelliSense 'i etkinleştirmek için bu üyeyi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="66772-148">For example, [Visual Studio Code](https://code.visualstudio.com/) requires this member to enable IntelliSense.</span></span> <span data-ttu-id="66772-149">Değerini kullanın `http://json.schemastore.org/template` .</span><span class="sxs-lookup"><span data-stu-id="66772-149">Use a value of `http://json.schemastore.org/template`.</span></span> |
| `author`          | <span data-ttu-id="66772-150">string</span><span class="sxs-lookup"><span data-stu-id="66772-150">string</span></span>        | <span data-ttu-id="66772-151">Şablonun yazarı.</span><span class="sxs-lookup"><span data-stu-id="66772-151">The author of the template.</span></span> |
| `classifications` | <span data-ttu-id="66772-152">dizi (dize)</span><span class="sxs-lookup"><span data-stu-id="66772-152">array(string)</span></span> | <span data-ttu-id="66772-153">Bir kullanıcının, arama yaparken şablonu bulmak için kullanabileceği şablonun sıfır veya daha fazla özelliği.</span><span class="sxs-lookup"><span data-stu-id="66772-153">Zero or more characteristics of the template that a user might use to find the template when searching for it.</span></span> <span data-ttu-id="66772-154">Sınıflandırmalar, komutu kullanılarak oluşturulan şablonlar listesinde göründüğünde *Etiketler* sütununda da görüntülenir `dotnet new -l|--list` .</span><span class="sxs-lookup"><span data-stu-id="66772-154">The classifications also appear in the *Tags* column when it appears in a list of templates produced by using the `dotnet new -l|--list` command.</span></span> |
| `identity`        | <span data-ttu-id="66772-155">string</span><span class="sxs-lookup"><span data-stu-id="66772-155">string</span></span>        | <span data-ttu-id="66772-156">Bu şablon için benzersiz bir ad.</span><span class="sxs-lookup"><span data-stu-id="66772-156">A unique name for this template.</span></span> |
| `name`            | <span data-ttu-id="66772-157">string</span><span class="sxs-lookup"><span data-stu-id="66772-157">string</span></span>        | <span data-ttu-id="66772-158">Kullanıcıların göreceği şablonun adı.</span><span class="sxs-lookup"><span data-stu-id="66772-158">The name for the template that users should see.</span></span> |
| `shortName`       | <span data-ttu-id="66772-159">string</span><span class="sxs-lookup"><span data-stu-id="66772-159">string</span></span>        | <span data-ttu-id="66772-160">Şablon adının Kullanıcı tarafından belirtildiği, GUI aracılığıyla seçilmemiş ortamlar için geçerli olan şablonu seçmek üzere varsayılan bir Özet adı.</span><span class="sxs-lookup"><span data-stu-id="66772-160">A default shorthand name for selecting the template that applies to environments where the template name is specified by the user, not selected via a GUI.</span></span> <span data-ttu-id="66772-161">Örneğin, CLı komutlarıyla bir komut isteminden Şablonlar kullanılırken kısa ad yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="66772-161">For example, the short name is useful when using templates from a command prompt with CLI commands.</span></span> |
| `sourceName`       | <span data-ttu-id="66772-162">string</span><span class="sxs-lookup"><span data-stu-id="66772-162">string</span></span>        | <span data-ttu-id="66772-163">Değiştirilecek kaynak ağaçtaki ad, kullanıcının belirttiği adla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="66772-163">The name in the source tree to replace with the name the user specifies.</span></span> <span data-ttu-id="66772-164">Şablon altyapısı, yapılandırma dosyasında bahsedilen ' ın herhangi bir oluşumunu arayacaktır `sourceName` ve dosya adlarında ve dosya içeriğinde yerini alır.</span><span class="sxs-lookup"><span data-stu-id="66772-164">The template engine will look for any occurrence of the `sourceName` mentioned in the config file and replace it in file names and file contents.</span></span> <span data-ttu-id="66772-165">İle değiştirilmelidir değeri, `-n` `--name` bir şablon çalıştırılırken veya seçenekleri kullanılarak verilebilir.</span><span class="sxs-lookup"><span data-stu-id="66772-165">The value to be replaced with can be given using the `-n` or `--name` options while running a template.</span></span> <span data-ttu-id="66772-166">Ad belirtilmemişse, geçerli dizin kullanılır.</span><span class="sxs-lookup"><span data-stu-id="66772-166">If no name is specified, the current directory is used.</span></span>|
| `preferNameDirectory`       | <span data-ttu-id="66772-167">boolean</span><span class="sxs-lookup"><span data-stu-id="66772-167">boolean</span></span>        | <span data-ttu-id="66772-168">Ad belirtilmişse şablon için bir dizin oluşturulup oluşturulmayacağını belirtir, ancak bir çıkış dizini ayarlanmamışsa (içeriği doğrudan geçerli dizinde oluşturmak yerine).</span><span class="sxs-lookup"><span data-stu-id="66772-168">Indicates whether to create a directory for the template if name is specified but an output directory is not set (instead of creating the content directly in the current directory).</span></span> <span data-ttu-id="66772-169">Varsayılan değer false'tur.</span><span class="sxs-lookup"><span data-stu-id="66772-169">The default value is false.</span></span>|

<span data-ttu-id="66772-170">Dosyadaki *template.js* tam şeması [JSON Şema deposunda](http://json.schemastore.org/template)bulunur.</span><span class="sxs-lookup"><span data-stu-id="66772-170">The full schema for the *template.json* file is found at the [JSON Schema Store](http://json.schemastore.org/template).</span></span> <span data-ttu-id="66772-171">Dosyadaki *template.js* hakkında daha fazla bilgi için bkz. [DotNet şablon oluşturma wiki](https://github.com/dotnet/templating/wiki).</span><span class="sxs-lookup"><span data-stu-id="66772-171">For more information about the *template.json* file, see the [dotnet templating wiki](https://github.com/dotnet/templating/wiki).</span></span>

#### <a name="example"></a><span data-ttu-id="66772-172">Örnek</span><span class="sxs-lookup"><span data-stu-id="66772-172">Example</span></span>

<span data-ttu-id="66772-173">Örneğin, aşağıda iki içerik dosyası içeren bir şablon klasörü verilmiştir: *Console.cs* ve *readme.txt*.</span><span class="sxs-lookup"><span data-stu-id="66772-173">For example, here is a template folder that contains two content files: *console.cs* and *readme.txt*.</span></span> <span data-ttu-id="66772-174">Dosyasında *template.js* içeren *.template.config* adlı gerekli klasör olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="66772-174">Take notice that there is the required folder named *.template.config* that contains the *template.json* file.</span></span>

```text
└───mytemplate
    │   console.cs
    │   readme.txt
    │
    └───.template.config
            template.json
```

<span data-ttu-id="66772-175">*template.js* dosyadaki dosya aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="66772-175">The *template.json* file looks like the following:</span></span>

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

<span data-ttu-id="66772-176">*MyTemplate* klasörü, yüklenebilir bir şablon paketidir.</span><span class="sxs-lookup"><span data-stu-id="66772-176">The *mytemplate* folder is an installable template pack.</span></span> <span data-ttu-id="66772-177">Paket yüklendikten sonra, `shortName` komutu ile kullanılabilir `dotnet new` .</span><span class="sxs-lookup"><span data-stu-id="66772-177">Once the pack is installed, the `shortName` can be used with the `dotnet new` command.</span></span> <span data-ttu-id="66772-178">Örneğin, `dotnet new adatumconsole` `console.cs` ve `readme.txt` dosyalarını geçerli klasöre çıktı.</span><span class="sxs-lookup"><span data-stu-id="66772-178">For example, `dotnet new adatumconsole` would output the `console.cs` and `readme.txt` files to the current folder.</span></span>

## <a name="packing-a-template-into-a-nuget-package-nupkg-file"></a><span data-ttu-id="66772-179">Bir NuGet paketine (nupkg dosyası) şablon paketleme</span><span class="sxs-lookup"><span data-stu-id="66772-179">Packing a template into a NuGet package (nupkg file)</span></span>

<span data-ttu-id="66772-180">Özel bir şablon [DotNet Pack](dotnet-pack.md) komutu ve bir *. csproj* dosyası ile paketlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="66772-180">A custom template is packed with the [dotnet pack](dotnet-pack.md) command and a *.csproj* file.</span></span> <span data-ttu-id="66772-181">Alternatif olarak, [NuGet](/nuget/tools/nuget-exe-cli-reference) , [NuGet Pack](/nuget/tools/cli-ref-pack) komutuyla birlikte bir *. nuspec* dosyası ile birlikte kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="66772-181">Alternatively, [NuGet](/nuget/tools/nuget-exe-cli-reference) can be used with the [nuget pack](/nuget/tools/cli-ref-pack) command along with a *.nuspec* file.</span></span> <span data-ttu-id="66772-182">Ancak NuGet, Linux ve macOS 'ta Windows ve [mono](https://www.mono-project.com/) üzerinde .NET Framework gerektirir.</span><span class="sxs-lookup"><span data-stu-id="66772-182">However, NuGet requires the .NET Framework on Windows and [Mono](https://www.mono-project.com/) on Linux and macOS.</span></span>

<span data-ttu-id="66772-183">*. Csproj* dosyası geleneksel bir Code-Project *. csproj* dosyasından biraz farklıdır.</span><span class="sxs-lookup"><span data-stu-id="66772-183">The *.csproj* file is slightly different from a traditional code-project *.csproj* file.</span></span> <span data-ttu-id="66772-184">Aşağıdaki ayarlara dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="66772-184">Note the following settings:</span></span>

01. <span data-ttu-id="66772-185">`<PackageType>`Ayar eklenir ve olarak ayarlanır `Template` .</span><span class="sxs-lookup"><span data-stu-id="66772-185">The `<PackageType>` setting is added and set to `Template`.</span></span>
01. <span data-ttu-id="66772-186">`<PackageVersion>`Ayar eklenir ve geçerli bir [NuGet sürüm numarasına](/nuget/reference/package-versioning)ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="66772-186">The `<PackageVersion>` setting is added and set to a valid [NuGet version number](/nuget/reference/package-versioning).</span></span>
01. <span data-ttu-id="66772-187">`<PackageId>`Ayar eklenir ve benzersiz bir tanımlayıcıya ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="66772-187">The `<PackageId>` setting is added and set to a unique identifier.</span></span> <span data-ttu-id="66772-188">Bu tanımlayıcı, şablon paketini kaldırmak için kullanılır ve NuGet akışları tarafından şablon paketinizi kaydetmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="66772-188">This identifier is used to uninstall the template pack and is used by NuGet feeds to register your template pack.</span></span>
01. <span data-ttu-id="66772-189">Genel meta veri ayarları ayarlanmalıdır: `<Title>` , `<Authors>` , `<Description>` , ve `<PackageTags>` .</span><span class="sxs-lookup"><span data-stu-id="66772-189">Generic metadata settings should be set: `<Title>`, `<Authors>`, `<Description>`, and `<PackageTags>`.</span></span>
01. <span data-ttu-id="66772-190">`<TargetFramework>`Şablon işlemi tarafından üretilen ikilinin kullanılmasa bile, ayarın ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="66772-190">The `<TargetFramework>` setting must be set, even though the binary produced by the template process isn't used.</span></span> <span data-ttu-id="66772-191">Aşağıdaki örnekte olarak ayarlanır `netstandard2.0` .</span><span class="sxs-lookup"><span data-stu-id="66772-191">In the example below it's set to `netstandard2.0`.</span></span>

<span data-ttu-id="66772-192">*. Nupkg* NuGet paketi biçimindeki bir şablon paketi, tüm şablonların paket içindeki *içerik* klasöründe depolanmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="66772-192">A template pack, in the form of a *.nupkg* NuGet package, requires that all templates be stored in the *content* folder within the package.</span></span> <span data-ttu-id="66772-193">Oluşturulan *. nupkg* 'nin bir şablon paketi olarak yüklenememesini sağlamak için bir *. csproj* dosyasına eklemenin daha fazla ayarı vardır:</span><span class="sxs-lookup"><span data-stu-id="66772-193">There are a few more settings to add to a *.csproj* file to ensure that the generated *.nupkg* can be installed as a template pack:</span></span>

01. <span data-ttu-id="66772-194">`<IncludeContentInPack>`Ayar, `true` projenin, NuGet paketine **içerik** olarak ayarlandığı herhangi bir dosyayı içerecek şekilde ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="66772-194">The `<IncludeContentInPack>` setting is set to `true` to include any file the project sets as **content** in the NuGet package.</span></span>
01. <span data-ttu-id="66772-195">`<IncludeBuildOutput>`Ayar, `false` NuGet paketinden derleyici tarafından oluşturulan tüm ikilileri dışarıda bırakacak şekilde ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="66772-195">The `<IncludeBuildOutput>` setting is set to `false` to exclude all binaries generated by the compiler from the NuGet package.</span></span>
01. <span data-ttu-id="66772-196">`<ContentTargetFolders>`Ayar olarak ayarlanır `content` .</span><span class="sxs-lookup"><span data-stu-id="66772-196">The `<ContentTargetFolders>` setting is set to `content`.</span></span> <span data-ttu-id="66772-197">Bu, **içerik** olarak ayarlanmış dosyaların NuGet paketindeki *içerik* klasörüne depolandığından emin olur.</span><span class="sxs-lookup"><span data-stu-id="66772-197">This makes sure that the files set as **content** are stored in the *content* folder in the NuGet package.</span></span> <span data-ttu-id="66772-198">NuGet paketindeki bu klasör DotNet şablon sistemi tarafından ayrıştırılır.</span><span class="sxs-lookup"><span data-stu-id="66772-198">This folder in the NuGet package is parsed by the dotnet template system.</span></span>

<span data-ttu-id="66772-199">Tüm kod dosyalarının şablon projeniz tarafından derlenmesinden dışlanmasını sağlamanın kolay bir yolu `<Compile Remove="**\*" />` , proje dosyanızdaki öğeyi bir öğe içinde kullanmaktır `<ItemGroup>` .</span><span class="sxs-lookup"><span data-stu-id="66772-199">An easy way to exclude all code files from being compiled by your template project is by using the `<Compile Remove="**\*" />` item in your project file, inside an `<ItemGroup>` element.</span></span>

<span data-ttu-id="66772-200">Şablon paketinizi oluşturmanın kolay bir yolu, tüm şablonları tek tek klasörlere koymak ve ardından, *. csproj* dosyanız ile aynı dizinde bulunan *bir şablon klasörünün içindeki her bir şablon* klasörünü kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="66772-200">An easy way to structure your template pack is to put all templates in individual folders, and then each template folder inside of a *templates* folder that is located in the same directory as your *.csproj* file.</span></span> <span data-ttu-id="66772-201">Bu şekilde, tek bir proje öğesi kullanarak *şablonlarda* tüm dosya ve klasörleri **içerik**olarak ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66772-201">This way, you can use a single project item to include all files and folders in the *templates* as **content**.</span></span> <span data-ttu-id="66772-202">`<ItemGroup>`Öğesinin içinde bir `<Content Include="templates\**\*" Exclude="templates\**\bin\**;templates\**\obj\**" />` öğe oluşturun.</span><span class="sxs-lookup"><span data-stu-id="66772-202">Inside of an `<ItemGroup>` element, create a `<Content Include="templates\**\*" Exclude="templates\**\bin\**;templates\**\obj\**" />` item.</span></span>

<span data-ttu-id="66772-203">Yukarıdaki tüm yönergeleri izleyen örnek bir *. csproj* dosyası aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="66772-203">Here is an example *.csproj* file that follows all of the guidelines above.</span></span> <span data-ttu-id="66772-204">*Şablonlar* alt klasörünü *içerik* paketi klasörüne paketler ve tüm kod dosyalarını derlenmeden dışlar.</span><span class="sxs-lookup"><span data-stu-id="66772-204">It packs the *templates* child folder to the *content* package folder and excludes any code file from being compiled.</span></span>

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

<span data-ttu-id="66772-205">Aşağıdaki örnekte, bir şablon paketi oluşturmak için *. csproj* kullanarak dosya ve klasör yapısı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="66772-205">The example below demonstrates the file and folder structure of using a *.csproj* to create a template pack.</span></span> <span data-ttu-id="66772-206">*MyDotnetTemplates. csproj* dosya ve *şablonlar* klasörü, *project_folder*adlı bir dizinin kökünde bulunur.</span><span class="sxs-lookup"><span data-stu-id="66772-206">The *MyDotnetTemplates.csproj* file and *templates* folder are both located at the root of a directory named *project_folder*.</span></span> <span data-ttu-id="66772-207">*Şablonlar* klasörü, *mytemplate1* ve *mytemplate2*olmak üzere iki şablon içerir.</span><span class="sxs-lookup"><span data-stu-id="66772-207">The *templates* folder contains two templates, *mytemplate1* and *mytemplate2*.</span></span> <span data-ttu-id="66772-208">Her şablonda içerik dosyaları ve *template.js* yapılandırma dosyasında bir *.template.config* klasörü bulunur.</span><span class="sxs-lookup"><span data-stu-id="66772-208">Each template has content files and a *.template.config* folder with a *template.json* config file.</span></span>

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

## <a name="installing-a-template"></a><span data-ttu-id="66772-209">Şablon yükleme</span><span class="sxs-lookup"><span data-stu-id="66772-209">Installing a template</span></span>

<span data-ttu-id="66772-210">Bir paket yüklemek için [DotNet New-i |--Install](dotnet-new.md) komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="66772-210">Use the [dotnet new -i|--install](dotnet-new.md) command to install a package.</span></span>

### <a name="to-install-a-template-from-a-nuget-package-stored-at-nugetorg"></a><span data-ttu-id="66772-211">Nuget.org adresinde depolanan bir NuGet paketinden şablon yüklemek için</span><span class="sxs-lookup"><span data-stu-id="66772-211">To install a template from a NuGet package stored at nuget.org</span></span>

<span data-ttu-id="66772-212">Bir şablon paketini yüklemek için NuGet paket tanımlayıcısını kullanın.</span><span class="sxs-lookup"><span data-stu-id="66772-212">Use the NuGet package identifier to install a template package.</span></span>

```dotnetcli
dotnet new -i <NUGET_PACKAGE_ID>
```

### <a name="to-install-a-template-from-a-local-nupkg-file"></a><span data-ttu-id="66772-213">Yerel nupkg dosyasından bir şablon yüklemek için</span><span class="sxs-lookup"><span data-stu-id="66772-213">To install a template from a local nupkg file</span></span>

<span data-ttu-id="66772-214">*. Nupkg* NuGet paket dosyasının yolunu belirtin.</span><span class="sxs-lookup"><span data-stu-id="66772-214">Provide the path to a *.nupkg* NuGet package file.</span></span>

```dotnetcli
dotnet new -i <PATH_TO_NUPKG_FILE>
```

### <a name="to-install-a-template-from-a-file-system-directory"></a><span data-ttu-id="66772-215">Bir dosya sistemi dizininden şablon yüklemek için</span><span class="sxs-lookup"><span data-stu-id="66772-215">To install a template from a file system directory</span></span>

<span data-ttu-id="66772-216">Şablonlar, yukarıdaki örnekteki *mytemplate1* klasörü gibi bir şablon klasöründen yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="66772-216">Templates can be installed from a template folder, such as the *mytemplate1* folder from the example above.</span></span> <span data-ttu-id="66772-217">*.template.config* klasörünün klasör yolunu belirtin.</span><span class="sxs-lookup"><span data-stu-id="66772-217">Specify the folder path of the *.template.config* folder.</span></span> <span data-ttu-id="66772-218">Şablon dizini yolunun mutlak olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="66772-218">The path to the template directory does not need to be absolute.</span></span> <span data-ttu-id="66772-219">Ancak, bir klasörden yüklenen bir şablonu kaldırmak için mutlak bir yol gereklidir.</span><span class="sxs-lookup"><span data-stu-id="66772-219">However, an absolute path is required to uninstall a template that is installed from a folder.</span></span>

```dotnetcli
dotnet new -i <FILE_SYSTEM_DIRECTORY>
```

## <a name="get-a-list-of-installed-templates"></a><span data-ttu-id="66772-220">Yüklü şablonların bir listesini alın</span><span class="sxs-lookup"><span data-stu-id="66772-220">Get a list of installed templates</span></span>

<span data-ttu-id="66772-221">Kaldırma komutu, başka parametreler olmadan, tüm yüklü şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="66772-221">The uninstall command, without any other parameters, will list all installed templates.</span></span>

```dotnetcli
dotnet new -u
```

<span data-ttu-id="66772-222">Bu komut aşağıdaki çıktıya benzer bir şey döndürür:</span><span class="sxs-lookup"><span data-stu-id="66772-222">That command returns something similar to the following output:</span></span>

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

<span data-ttu-id="66772-223">Sonraki öğelerin ilk düzeyi, `Currently installed items:` bir şablonu kaldırma bölümünde kullanılan tanımlayıcılardır.</span><span class="sxs-lookup"><span data-stu-id="66772-223">The first level of items after `Currently installed items:` are the identifiers used in uninstalling a template.</span></span> <span data-ttu-id="66772-224">Ve yukarıdaki örnekteki `Microsoft.DotNet.Common.ItemTemplates` ve `Microsoft.DotNet.Common.ProjectTemplates.3.0` listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="66772-224">And in the example above, `Microsoft.DotNet.Common.ItemTemplates` and `Microsoft.DotNet.Common.ProjectTemplates.3.0` are listed.</span></span> <span data-ttu-id="66772-225">Şablon bir dosya sistemi yolu kullanılarak yüklendiyse, bu tanımlayıcı *.template.config* klasörünün klasör yolu olacaktır.</span><span class="sxs-lookup"><span data-stu-id="66772-225">If the template was installed by using a file system path, this identifier will the folder path of the *.template.config* folder.</span></span>

## <a name="uninstalling-a-template"></a><span data-ttu-id="66772-226">Bir şablonu kaldırma</span><span class="sxs-lookup"><span data-stu-id="66772-226">Uninstalling a template</span></span>

<span data-ttu-id="66772-227">Bir paketi kaldırmak için [DotNet New-u |--Uninstall](dotnet-new.md) komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="66772-227">Use the [dotnet new -u|--uninstall](dotnet-new.md) command to uninstall a package.</span></span>

<span data-ttu-id="66772-228">Paket, bir NuGet akışı veya doğrudan bir *. nupkg* dosyası tarafından yüklendiyse, tanımlayıcıyı sağlayın.</span><span class="sxs-lookup"><span data-stu-id="66772-228">If the package was installed by either a NuGet feed or by a *.nupkg* file directly, provide the identifier.</span></span>

```dotnetcli
dotnet new -u <NUGET_PACKAGE_ID>
```

<span data-ttu-id="66772-229">Paket, *.template.config* klasörü için bir yol belirtilerek yüklenmişse, paketi kaldırmak için bu **mutlak** yolu kullanın.</span><span class="sxs-lookup"><span data-stu-id="66772-229">If the package was installed by specifying a path to the *.template.config* folder, use that **absolute** path to uninstall the package.</span></span> <span data-ttu-id="66772-230">Şablonun mutlak yolunu komut tarafından belirtilen çıkışta görebilirsiniz `dotnet new -u` .</span><span class="sxs-lookup"><span data-stu-id="66772-230">You can see the absolute path of the template in the output provided by the `dotnet new -u` command.</span></span> <span data-ttu-id="66772-231">Daha fazla bilgi için yukarıdaki [yüklü şablonlar listesini al](#get-a-list-of-installed-templates) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="66772-231">For more information, see the [Get a list of installed templates](#get-a-list-of-installed-templates) section above.</span></span>

```dotnetcli
dotnet new -u <ABSOLUTE_FILE_SYSTEM_DIRECTORY>
```

## <a name="create-a-project-using-a-custom-template"></a><span data-ttu-id="66772-232">Özel şablon kullanarak proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="66772-232">Create a project using a custom template</span></span>

<span data-ttu-id="66772-233">Bir şablon yüklendikten sonra, `dotnet new <TEMPLATE>` başka bir önceden yüklenmiş şablonla yaptığınız gibi komutu yürüterek şablonu kullanın.</span><span class="sxs-lookup"><span data-stu-id="66772-233">After a template is installed, use the template by executing the `dotnet new <TEMPLATE>` command as you would with any other pre-installed template.</span></span> <span data-ttu-id="66772-234">Ayrıca [options](dotnet-new.md#options) `dotnet new` , şablon ayarlarında yapılandırdığınız şablona özgü seçenekler dahil olmak üzere komut için seçenekler de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66772-234">You can also specify [options](dotnet-new.md#options) to the `dotnet new` command, including template-specific options you configured in the template settings.</span></span> <span data-ttu-id="66772-235">Şablonun kısa adını doğrudan komuta sağlayın:</span><span class="sxs-lookup"><span data-stu-id="66772-235">Supply the template's short name directly to the command:</span></span>

```dotnetcli
dotnet new <TEMPLATE>
```

## <a name="see-also"></a><span data-ttu-id="66772-236">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="66772-236">See also</span></span>

- [<span data-ttu-id="66772-237">DotNet New için özel şablon oluşturma (öğretici)</span><span class="sxs-lookup"><span data-stu-id="66772-237">Create a custom template for dotnet new (tutorial)</span></span>](../tutorials/cli-templates-create-item-template.md)
- [<span data-ttu-id="66772-238">DotNet/şablon oluşturma GitHub deposu wiki</span><span class="sxs-lookup"><span data-stu-id="66772-238">dotnet/templating GitHub repo Wiki</span></span>](https://github.com/dotnet/templating/wiki)
- [<span data-ttu-id="66772-239">DotNet/DotNet-şablon-örnek GitHub deposu</span><span class="sxs-lookup"><span data-stu-id="66772-239">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="66772-240">DotNet New için kendi şablonlarınızı oluşturma</span><span class="sxs-lookup"><span data-stu-id="66772-240">How to create your own templates for dotnet new</span></span>](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/)
- [<span data-ttu-id="66772-241">JSON Şema deposundaki şemada *template.js*</span><span class="sxs-lookup"><span data-stu-id="66772-241">*template.json* schema at the JSON Schema Store</span></span>](http://json.schemastore.org/template)
