---
title: Yeni dotnet için özel şablonlar
description: Herhangi bir türde .NET proje veya dosya için özel şablonlar hakkında bilgi edinin.
author: mairaw
ms.date: 08/11/2017
ms.openlocfilehash: 19211d1ac45bbd2e5838c5ee30e380d7d10c3f1c
ms.sourcegitcommit: 5e05f983e63d5bbd8c0b246d02c6e4f23d2fc1db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2019
ms.locfileid: "67151946"
---
# <a name="custom-templates-for-dotnet-new"></a><span data-ttu-id="bcaec-103">Yeni dotnet için özel şablonlar</span><span class="sxs-lookup"><span data-stu-id="bcaec-103">Custom templates for dotnet new</span></span>

<span data-ttu-id="bcaec-104">[.NET Core SDK'sı](https://www.microsoft.com/net/download/core) birçok zaten yüklü şablonlar ve kullanımınıza hazır birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="bcaec-104">The [.NET Core SDK](https://www.microsoft.com/net/download/core) comes with many templates already installed and ready for you to use.</span></span> <span data-ttu-id="bcaec-105">[ `dotnet new` Komut](dotnet-new.md) yalnızca şablon aynı zamanda yüklemek ve şablonları kaldırmak nasıl kullanılacağını yolu değildir.</span><span class="sxs-lookup"><span data-stu-id="bcaec-105">The [`dotnet new` command](dotnet-new.md) isn't only the way to use a template, but also how to install and uninstall templates.</span></span> <span data-ttu-id="bcaec-106">.NET Core 2.0 ile başlayarak, herhangi bir türde gibi bir uygulama, hizmet, aracı veya sınıf kitaplığı projesi için kendi özel şablonlarınızı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bcaec-106">Starting with .NET Core 2.0, you can create your own custom templates for any type of project, such as an app, service, tool, or class library.</span></span> <span data-ttu-id="bcaec-107">Hatta çıkaran bir veya daha fazla bağımsız dosyaları, bir yapılandırma dosyası gibi bir şablon oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bcaec-107">You can even create a template that outputs one or more independent files, such as a configuration file.</span></span>

<span data-ttu-id="bcaec-108">Özel şablonlar akış, bir NuGet başvurarak herhangi bir NuGet üzerindeki bir NuGet paketini yükleyebilirsiniz *.nupkg* doğrudan veya şablon içeren bir dosya sistemi dizin belirterek dosya.</span><span class="sxs-lookup"><span data-stu-id="bcaec-108">You can install custom templates from a NuGet package on any NuGet feed, by referencing a NuGet *.nupkg* file directly, or by specifying a file system directory that contains the template.</span></span> <span data-ttu-id="bcaec-109">Şablon altyapısı, değerleri değiştirebilir, içerir ve dosyaları dışarıda bırak olanak tanır ve şablonunuzu kullanıldığında özel işlemleri yürüten özellikleri sunar.</span><span class="sxs-lookup"><span data-stu-id="bcaec-109">The template engine offers features that allow you to replace values, include and exclude files, and execute custom processing operations when your template is used.</span></span>

<span data-ttu-id="bcaec-110">Şablon altyapısı açık kaynaklıdır ve çevrimiçi kod deposundaki altındadır [dotnet/şablon](https://github.com/dotnet/templating/) GitHub üzerinde.</span><span class="sxs-lookup"><span data-stu-id="bcaec-110">The template engine is open source, and the online code repository is at [dotnet/templating](https://github.com/dotnet/templating/) on GitHub.</span></span> <span data-ttu-id="bcaec-111">Ziyaret [dotnet/dotnet-şablonu-samples](https://github.com/dotnet/dotnet-template-samples) şablonları örnekleri için depo.</span><span class="sxs-lookup"><span data-stu-id="bcaec-111">Visit the [dotnet/dotnet-template-samples](https://github.com/dotnet/dotnet-template-samples) repo for samples of templates.</span></span> <span data-ttu-id="bcaec-112">Üçüncü taraf şablonları dahil olmak üzere daha fazla şablon adresten [yeni dotnet şablonları](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new) GitHub üzerinde.</span><span class="sxs-lookup"><span data-stu-id="bcaec-112">More templates, including templates from third parties, are found at [Available templates for dotnet new](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new) on GitHub.</span></span> <span data-ttu-id="bcaec-113">Özel şablon oluşturma ve kullanma hakkında daha fazla bilgi için bkz. [yeni dotnet için kendi şablonlarınızı oluşturmak nasıl](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/) ve [dotnet/şablon GitHub deposunu Wiki](https://github.com/dotnet/templating/wiki).</span><span class="sxs-lookup"><span data-stu-id="bcaec-113">For more information about creating and using custom templates, see [How to create your own templates for dotnet new](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/) and the [dotnet/templating GitHub repo Wiki](https://github.com/dotnet/templating/wiki).</span></span>

<span data-ttu-id="bcaec-114">Bir kılavuz uygulayın ve bir şablon oluşturmak için bkz: [yeni dotnet için özel bir şablon oluşturma](~/docs/core/tutorials/create-custom-template.md) öğretici.</span><span class="sxs-lookup"><span data-stu-id="bcaec-114">To follow a walkthrough and create a template, see the [Create a custom template for dotnet new](~/docs/core/tutorials/create-custom-template.md) tutorial.</span></span>

### <a name="net-default-templates"></a><span data-ttu-id="bcaec-115">.NET varsayılan şablonları</span><span class="sxs-lookup"><span data-stu-id="bcaec-115">.NET default templates</span></span>

<span data-ttu-id="bcaec-116">Yüklediğinizde [.NET Core SDK'sı](https://www.microsoft.com/net/download/core)projeleri oluşturmak için yerleşik şablonlar üzerinde bir düzine Al ve dosyaları, dahil konsol uygulamaları, sınıf kitaplıkları, birim test projeleri, ASP.NET Core uygulamaları (dahil olmak üzere [Angular](https://angular.io/) ve [React](https://facebook.github.io/react/) projeler) ve yapılandırma dosyaları.</span><span class="sxs-lookup"><span data-stu-id="bcaec-116">When you install the [.NET Core SDK](https://www.microsoft.com/net/download/core), you receive over a dozen built-in templates for creating projects and files, including console apps, class libraries, unit test projects, ASP.NET Core apps (including [Angular](https://angular.io/) and [React](https://facebook.github.io/react/) projects), and configuration files.</span></span> <span data-ttu-id="bcaec-117">Yerleşik şablonlar listelemek için çalıştırma `dotnet new` komutunu `-l|--list` seçeneği:</span><span class="sxs-lookup"><span data-stu-id="bcaec-117">To list the built-in templates, run the `dotnet new` command with the `-l|--list` option:</span></span>

```console
dotnet new --list
```

## <a name="configuration"></a><span data-ttu-id="bcaec-118">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="bcaec-118">Configuration</span></span>

<span data-ttu-id="bcaec-119">Şablon aşağıdaki bölümlerden oluşur:</span><span class="sxs-lookup"><span data-stu-id="bcaec-119">A template is composed of the following parts:</span></span>

- <span data-ttu-id="bcaec-120">Kaynak dosya ve klasörler.</span><span class="sxs-lookup"><span data-stu-id="bcaec-120">Source files and folders.</span></span>
- <span data-ttu-id="bcaec-121">Bir yapılandırma dosyası (*template.json*).</span><span class="sxs-lookup"><span data-stu-id="bcaec-121">A configuration file (*template.json*).</span></span>

### <a name="source-files-and-folders"></a><span data-ttu-id="bcaec-122">Kaynak dosyalar ve klasörler</span><span class="sxs-lookup"><span data-stu-id="bcaec-122">Source files and folders</span></span>

<span data-ttu-id="bcaec-123">Kaynak dosyaları ve klasörleri kullanmak üzere hangi dosya ve klasörleri, istediğiniz şablon altyapısı dahil `dotnet new <TEMPLATE>` komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="bcaec-123">The source files and folders include whatever files and folders you want the template engine to use when the `dotnet new <TEMPLATE>` command is run.</span></span> <span data-ttu-id="bcaec-124">Şablon altyapısı kullanmak üzere tasarlanmış *çalıştırılabilir projeleri* gibi kaynak kod projeleri oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="bcaec-124">The template engine is designed to use *runnable projects* as source code to produce projects.</span></span> <span data-ttu-id="bcaec-125">Bu, birçok faydası vardır:</span><span class="sxs-lookup"><span data-stu-id="bcaec-125">This has several benefits:</span></span>

- <span data-ttu-id="bcaec-126">Şablon motoru özel belirteçler projenizin kaynak koda eklemesine gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="bcaec-126">The template engine doesn't require you to inject special tokens into your project's source code.</span></span>
- <span data-ttu-id="bcaec-127">Kod dosyaları, özel dosyaları değil veya şablon altyapısı ile çalışmak üzere herhangi bir şekilde değiştirdi.</span><span class="sxs-lookup"><span data-stu-id="bcaec-127">The code files aren't special files or modified in any way to work with the template engine.</span></span> <span data-ttu-id="bcaec-128">Bu nedenle, normalde projeleriyle çalışırken kullandığınız araçları da şablon içeriği ile çalışır.</span><span class="sxs-lookup"><span data-stu-id="bcaec-128">So, the tools you normally use when working with projects also work with template content.</span></span>
- <span data-ttu-id="bcaec-129">Oluşturun, çalıştırın ve herhangi diğer projeleriniz için yaptığınız gibi şablon projelerini hata ayıklama.</span><span class="sxs-lookup"><span data-stu-id="bcaec-129">You build, run, and debug your template projects just like you do for any of your other projects.</span></span>
- <span data-ttu-id="bcaec-130">Yalnızca ekleyerek bir şablonu var olan bir projeden hızlı bir şekilde oluşturabilirsiniz bir *./.template.config/template.json* projeye yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="bcaec-130">You can quickly create a template from an existing project just by adding a *./.template.config/template.json* configuration file to the project.</span></span>

<span data-ttu-id="bcaec-131">Şablonda depolanan dosya ve klasörleri resmi .NET proje türleri için sınırlı değildir.</span><span class="sxs-lookup"><span data-stu-id="bcaec-131">Files and folders stored in the template aren't limited to formal .NET project types.</span></span> <span data-ttu-id="bcaec-132">Kaynak dosyalar ve klasörler, şablon kullanıldığında, şablon altyapısı çıktısını olarak yalnızca bir dosya üretse oluşturmak istediğiniz tüm içeriklerin oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="bcaec-132">Source files and folders may consist of any content that you wish to create when the template is used, even if the template engine produces just one file as its output.</span></span>

<span data-ttu-id="bcaec-133">Şablon tarafından oluşturulan dosyaları içinde sağladığınız ayarları ve mantıksal dayalı değiştirilebilir *template.json* yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="bcaec-133">Files generated by the template can be modified based on logic and settings you've provided in the *template.json* configuration file.</span></span> <span data-ttu-id="bcaec-134">Seçenekleri geçirme, kullanıcı bu ayarları geçersiz kılabilirsiniz `dotnet new <TEMPLATE>` komutu.</span><span class="sxs-lookup"><span data-stu-id="bcaec-134">The user can override these settings by passing options to the `dotnet new <TEMPLATE>` command.</span></span> <span data-ttu-id="bcaec-135">Yaygın olarak karşılaşılan örneklerden özel mantığı bir sınıfı veya şablon tarafından dağıtılan kod dosyasında değişken için bir ad sağlar.</span><span class="sxs-lookup"><span data-stu-id="bcaec-135">A common example of custom logic is providing a name for a class or variable in the code file that's deployed by a template.</span></span>

### <a name="templatejson"></a><span data-ttu-id="bcaec-136">Template.JSON</span><span class="sxs-lookup"><span data-stu-id="bcaec-136">template.json</span></span>

<span data-ttu-id="bcaec-137">*Template.json* dosya yerleştirilir bir *. template.config* şablonunun kök dizininde klasör.</span><span class="sxs-lookup"><span data-stu-id="bcaec-137">The *template.json* file is placed in a *.template.config* folder in the root directory of the template.</span></span> <span data-ttu-id="bcaec-138">Dosya, şablon altyapısı yapılandırma bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="bcaec-138">The file provides configuration information to the template engine.</span></span> <span data-ttu-id="bcaec-139">Bir işlev şablonu oluşturmak yeterli olan aşağıdaki tabloda gösterilen üyeleri en az yapılandırma gerektirir.</span><span class="sxs-lookup"><span data-stu-id="bcaec-139">The minimum configuration requires the members shown in the following table, which is sufficient to create a functional template.</span></span>

| <span data-ttu-id="bcaec-140">Üye</span><span class="sxs-lookup"><span data-stu-id="bcaec-140">Member</span></span>            | <span data-ttu-id="bcaec-141">Tür</span><span class="sxs-lookup"><span data-stu-id="bcaec-141">Type</span></span>          | <span data-ttu-id="bcaec-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bcaec-142">Description</span></span> |
| ----------------- | ------------- | ----------- |
| `$schema`         | <span data-ttu-id="bcaec-143">URI</span><span class="sxs-lookup"><span data-stu-id="bcaec-143">URI</span></span>           | <span data-ttu-id="bcaec-144">JSON şemasını *template.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="bcaec-144">The JSON schema for the *template.json* file.</span></span> <span data-ttu-id="bcaec-145">Şema belirtildiğinde JSON şema desteği düzenleyicileri JSON düzenleme özelliklerini etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="bcaec-145">Editors that support JSON schemas enable JSON-editing features when the schema is specified.</span></span> <span data-ttu-id="bcaec-146">Örneğin, [Visual Studio Code](https://code.visualstudio.com/) IntelliSense'i etkinleştirmek bu üye gerektirir.</span><span class="sxs-lookup"><span data-stu-id="bcaec-146">For example, [Visual Studio Code](https://code.visualstudio.com/) requires this member to enable IntelliSense.</span></span> <span data-ttu-id="bcaec-147">Değeri kullanın `http://json.schemastore.org/template`.</span><span class="sxs-lookup"><span data-stu-id="bcaec-147">Use a value of `http://json.schemastore.org/template`.</span></span> |
| `author`          | <span data-ttu-id="bcaec-148">dize</span><span class="sxs-lookup"><span data-stu-id="bcaec-148">string</span></span>        | <span data-ttu-id="bcaec-149">Şablon yazarı.</span><span class="sxs-lookup"><span data-stu-id="bcaec-149">The author of the template.</span></span> |
| `classifications` | <span data-ttu-id="bcaec-150">Array(String)</span><span class="sxs-lookup"><span data-stu-id="bcaec-150">array(string)</span></span> | <span data-ttu-id="bcaec-151">Sıfır veya daha fazla kullanıcı için arama yaparken şablonu bulmak için kullanıyor olabileceğiniz şablonun özelliklerini.</span><span class="sxs-lookup"><span data-stu-id="bcaec-151">Zero or more characteristics of the template that a user might use to find the template when searching for it.</span></span> <span data-ttu-id="bcaec-152">Sınıflandırmalar da görünür *etiketleri* şablonları listesinde göründüğünde sütun üretilen kullanarak `dotnet new -l|--list` komutu.</span><span class="sxs-lookup"><span data-stu-id="bcaec-152">The classifications also appear in the *Tags* column when it appears in a list of templates produced by using the `dotnet new -l|--list` command.</span></span> |
| `identity`        | <span data-ttu-id="bcaec-153">dize</span><span class="sxs-lookup"><span data-stu-id="bcaec-153">string</span></span>        | <span data-ttu-id="bcaec-154">Bu şablon için benzersiz bir ad.</span><span class="sxs-lookup"><span data-stu-id="bcaec-154">A unique name for this template.</span></span> |
| `name`            | <span data-ttu-id="bcaec-155">dize</span><span class="sxs-lookup"><span data-stu-id="bcaec-155">string</span></span>        | <span data-ttu-id="bcaec-156">Kullanıcılar görmelisiniz şablonunun adı.</span><span class="sxs-lookup"><span data-stu-id="bcaec-156">The name for the template that users should see.</span></span> |
| `shortName`       | <span data-ttu-id="bcaec-157">dize</span><span class="sxs-lookup"><span data-stu-id="bcaec-157">string</span></span>        | <span data-ttu-id="bcaec-158">Şablon adı GUI seçili olmayan bir kullanıcı tarafından burada belirtilen ortam için geçerli şablonu seçmek için bir varsayılan toplu özellik adı.</span><span class="sxs-lookup"><span data-stu-id="bcaec-158">A default shorthand name for selecting the template that applies to environments where the template name is specified by the user, not selected via a GUI.</span></span> <span data-ttu-id="bcaec-159">Örneğin, kısa ad şablonları bir komut isteminden CLI komutları ile kullanıldığında yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="bcaec-159">For example, the short name is useful when using templates from a command prompt with CLI commands.</span></span> |

<span data-ttu-id="bcaec-160">İçin tam şema *template.json* dosya konumunda bulundu [JSON şema Store](http://json.schemastore.org/template).</span><span class="sxs-lookup"><span data-stu-id="bcaec-160">The full schema for the *template.json* file is found at the [JSON Schema Store](http://json.schemastore.org/template).</span></span> <span data-ttu-id="bcaec-161">Hakkında daha fazla bilgi için *template.json* bkz [dotnet şablon wiki](https://github.com/dotnet/templating/wiki).</span><span class="sxs-lookup"><span data-stu-id="bcaec-161">For more information about the *template.json* file, see the [dotnet templating wiki](https://github.com/dotnet/templating/wiki).</span></span>

#### <a name="example"></a><span data-ttu-id="bcaec-162">Örnek</span><span class="sxs-lookup"><span data-stu-id="bcaec-162">Example</span></span>

<span data-ttu-id="bcaec-163">Örneğin, iki içerik dosyalarını içeren bir şablon klasörü şöyledir: *console.cs* ve *readme.txt*.</span><span class="sxs-lookup"><span data-stu-id="bcaec-163">For example, here is a template folder that contains two content files: *console.cs* and *readme.txt*.</span></span> <span data-ttu-id="bcaec-164">Adında gereken klasör var olduğuna dikkat edin ele *. template.config* içeren *template.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="bcaec-164">Take notice that there is the required folder named *.template.config* that contains the *template.json* file.</span></span>

```text
└───mytemplate
    │   console.cs
    │   readme.txt
    │
    └───.template.config
            template.json
```

<span data-ttu-id="bcaec-165">*Template.json* dosyasını aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="bcaec-165">The *template.json* file looks like the following:</span></span>

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

<span data-ttu-id="bcaec-166">*Şablonum* yüklenebilir bir şablon paketi bir klasördür.</span><span class="sxs-lookup"><span data-stu-id="bcaec-166">The *mytemplate* folder is an installable template pack.</span></span> <span data-ttu-id="bcaec-167">Paketi yüklendikten sonra `shortName` kullanılabilir `dotnet new` komutu.</span><span class="sxs-lookup"><span data-stu-id="bcaec-167">Once the pack is installed, the `shortName` can be used with the `dotnet new` command.</span></span> <span data-ttu-id="bcaec-168">Örneğin, `dotnet new adatumconsole` çıkış `console.cs` ve `readme.txt` geçerli klasörle dosyaları.</span><span class="sxs-lookup"><span data-stu-id="bcaec-168">For example, `dotnet new adatumconsole` would output the `console.cs` and `readme.txt` files to the current folder.</span></span>

## <a name="packing-a-template-into-a-nuget-package-nupkg-file"></a><span data-ttu-id="bcaec-169">Bir NuGet paketine (nupkg dosyası) bir şablon paketleme</span><span class="sxs-lookup"><span data-stu-id="bcaec-169">Packing a template into a NuGet package (nupkg file)</span></span>

<span data-ttu-id="bcaec-170">Özel bir şablon ile paketlenmiştir [dotnet paketi](dotnet-pack.md) komut ve *.csproj* dosya.</span><span class="sxs-lookup"><span data-stu-id="bcaec-170">A custom template is packed with the [dotnet pack](dotnet-pack.md) command and a *.csproj* file.</span></span> <span data-ttu-id="bcaec-171">Alternatif olarak, [NuGet](https://docs.microsoft.com/nuget/tools/nuget-exe-cli-reference) kullanılabilir [nuget paketi](https://docs.microsoft.com/nuget/tools/cli-ref-pack) komutu ile birlikte bir *.nuspec* dosya.</span><span class="sxs-lookup"><span data-stu-id="bcaec-171">Alternatively, [NuGet](https://docs.microsoft.com/nuget/tools/nuget-exe-cli-reference) can be used with the [nuget pack](https://docs.microsoft.com/nuget/tools/cli-ref-pack) command along with a *.nuspec* file.</span></span> <span data-ttu-id="bcaec-172">Ancak, Windows üzerinde .NET Framework NuGet gerektirir ve [Mono](https://www.mono-project.com/) Linux ve Macos'ta.</span><span class="sxs-lookup"><span data-stu-id="bcaec-172">However, NuGet requires the .NET Framework on Windows and [Mono](https://www.mono-project.com/) on Linux and MacOS.</span></span>

<span data-ttu-id="bcaec-173">*.Csproj* dosyasıdır geleneksel bir kod-projeden biraz farklı *.csproj* dosya.</span><span class="sxs-lookup"><span data-stu-id="bcaec-173">The *.csproj* file is slightly different from a traditional code-project *.csproj* file.</span></span> <span data-ttu-id="bcaec-174">Şunlara dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="bcaec-174">Note the following settings:</span></span>

01. <span data-ttu-id="bcaec-175">`<PackageType>` Ayarı eklenir ve kümesine `Template`.</span><span class="sxs-lookup"><span data-stu-id="bcaec-175">The `<PackageType>` setting is added and set to `Template`.</span></span>
01. <span data-ttu-id="bcaec-176">`<PackageVersion>` Ayarı eklenir ve geçerli bir kümesi [NuGet sürüm numarası](/nuget/reference/package-versioning).</span><span class="sxs-lookup"><span data-stu-id="bcaec-176">The `<PackageVersion>` setting is added and set to a valid [NuGet version number](/nuget/reference/package-versioning).</span></span>
01. <span data-ttu-id="bcaec-177">`<PackageId>` Ayarı eklenir ve benzersiz bir tanımlayıcı ile ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="bcaec-177">The `<PackageId>` setting is added and set to a unique identifier.</span></span> <span data-ttu-id="bcaec-178">Bu tanımlayıcı, şablon paketi kaldırmak için kullanılır ve NuGet tarafından kullanılır, şablon paketi kaydetmek için akışları.</span><span class="sxs-lookup"><span data-stu-id="bcaec-178">This identifier is used to uninstall the template pack and is used by NuGet feeds to register your template pack.</span></span>
01. <span data-ttu-id="bcaec-179">Genel meta veri ayarları ayarlanmalıdır: `<Title>`, `<Authors>`, `<Description>`, ve `<Tags>`.</span><span class="sxs-lookup"><span data-stu-id="bcaec-179">Generic metadata settings should be set: `<Title>`, `<Authors>`, `<Description>`, and `<Tags>`.</span></span>
01. <span data-ttu-id="bcaec-180">`<TargetFramework>` Ayarı ayarlanmalıdır, halde şablonunun işlem tarafından üretilen ikili kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="bcaec-180">The `<TargetFramework>` setting must be set, even though the binary produced by the template process isn't used.</span></span> <span data-ttu-id="bcaec-181">Aşağıdaki örnekte ayarlanmış `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="bcaec-181">In the example below it's set to `netstandard2.0`.</span></span>

<span data-ttu-id="bcaec-182">Biçiminde bir şablon paketi bir *.nupkg* NuGet paketini gerektiren tüm şablonları depolanması *içeriği* paket içindeki klasör.</span><span class="sxs-lookup"><span data-stu-id="bcaec-182">A template pack, in the form of a *.nupkg* NuGet package, requires that all templates be stored in the *content* folder within the package.</span></span> <span data-ttu-id="bcaec-183">Birkaç daha fazla ayar eklemek için bir *.csproj* oluşturulan emin olmak için dosya *.nupkg* bir şablon paketi yüklenebilir:</span><span class="sxs-lookup"><span data-stu-id="bcaec-183">There are a few more settings to add to a *.csproj* file to ensure that the generated *.nupkg* can be installed as a template pack:</span></span>

01. <span data-ttu-id="bcaec-184">`<IncludeContentInPack>` Ayarı `true` proje ayarlar olarak herhangi bir dosya eklemek için **içeriği** NuGet paketi olarak.</span><span class="sxs-lookup"><span data-stu-id="bcaec-184">The `<IncludeContentInPack>` setting is set to `true` to include any file the project sets as **content** in the NuGet package.</span></span>
01. <span data-ttu-id="bcaec-185">`<IncludeBuildOutput>` Ayarı `false` NuGet paketinden derleyici tarafından oluşturulan tüm ikili dosyaları hariç tutmak için.</span><span class="sxs-lookup"><span data-stu-id="bcaec-185">The `<IncludeBuildOutput>` setting is set to `false` to exclude all binaries generated by the compiler from the NuGet package.</span></span>
01. <span data-ttu-id="bcaec-186">`<ContentTargetFolders>` Ayarı `content`.</span><span class="sxs-lookup"><span data-stu-id="bcaec-186">The `<ContentTargetFolders>` setting is set to `content`.</span></span> <span data-ttu-id="bcaec-187">Bu dosyalar olarak ayarlayın xenapp'i **içeriği** depolanır *içeriği* NuGet paketi klasörüne.</span><span class="sxs-lookup"><span data-stu-id="bcaec-187">This makes sure that the files set as **content** are stored in the *content* folder in the NuGet package.</span></span> <span data-ttu-id="bcaec-188">NuGet paketi bu klasöre dotnet şablon sistem tarafından ayrıştırılır.</span><span class="sxs-lookup"><span data-stu-id="bcaec-188">This folder in the NuGet package is parsed by the dotnet template system.</span></span>

<span data-ttu-id="bcaec-189">Şablon projeniz tarafından derlenen tüm kod dosyaları hariç tutmak için kolay bir yol kullanmaktır `<Compile Remove="**\*" />` proje dosyanızın içine öğesi bir `<ItemGroup>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="bcaec-189">An easy way to exclude all code files from being compiled by your template project is by using the `<Compile Remove="**\*" />` item in your project file, inside an `<ItemGroup>` element.</span></span>

<span data-ttu-id="bcaec-190">Tüm Şablonları ayrı bir klasör ve ardından her şablon klasörü içine koymak için şablon paketi yapısı için kolay bir yol olan bir *şablonları* aynı dizinde klasörünün, *.csproj* dosya.</span><span class="sxs-lookup"><span data-stu-id="bcaec-190">An easy way to structure your template pack is to put all templates in individual folders, and then each template folder inside of a *templates* folder that is located in the same directory as your *.csproj* file.</span></span> <span data-ttu-id="bcaec-191">Bu şekilde tüm dosya ve klasörleri eklemek için bir tek proje öğesi kullanabilir *şablonları* olarak **içerik**.</span><span class="sxs-lookup"><span data-stu-id="bcaec-191">This way, you can use a single project item to include all files and folders in the *templates* as **content**.</span></span> <span data-ttu-id="bcaec-192">İçinde bir `<ItemGroup>` öğesi oluşturmak bir `<Content Include="templates\**\*" Exclude="templates\**\bin\**;templates\**\obj\**" />` öğesi.</span><span class="sxs-lookup"><span data-stu-id="bcaec-192">Inside of an `<ItemGroup>` element, create a `<Content Include="templates\**\*" Exclude="templates\**\bin\**;templates\**\obj\**" />` item.</span></span>

<span data-ttu-id="bcaec-193">İşte bir örnek *.csproj* tüm yukarıdaki yönergeleri izleyen dosya.</span><span class="sxs-lookup"><span data-stu-id="bcaec-193">Here is an example *.csproj* file that follows all of the guidelines above.</span></span> <span data-ttu-id="bcaec-194">Bu paketleri *şablonları* alt klasöre *içeriği* paketi klasörü ve Eylemi'ni her kod dosyasını hariç tutar.</span><span class="sxs-lookup"><span data-stu-id="bcaec-194">It packs the *templates* child folder to the *content* package folder and excludes any code file from being compiled.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <PackageType>Template</PackageType>
    <PackageVersion>1.0</PackageVersion>
    <PackageId>AdatumCorporation.Utility.Templates</PackageId>
    <Title>AdatumCorporation Templates</Title>
    <Authors>Me</Authors>
    <Description>Templates to use when creating an application for Adatum Corporation.</Description>
    <Tags>dotnet-new;templates;contoso</Tags>
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

<span data-ttu-id="bcaec-195">Aşağıdaki örneği kullanarak dosya ve klasör yapısını gösterir. bir *.csproj* bir şablon paketi oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="bcaec-195">The example below demonstrates the file and folder structure of using a *.csproj* to create a template pack.</span></span> <span data-ttu-id="bcaec-196">*MyDotnetTemplates.csproj* dosya ve *şablonları* klasör adında bir dizin kökünde bulunan *project_folder*.</span><span class="sxs-lookup"><span data-stu-id="bcaec-196">The *MyDotnetTemplates.csproj* file and *templates* folder are both located at the root of a directory named *project_folder*.</span></span> <span data-ttu-id="bcaec-197">*Şablonları* klasörünü içeren iki şablon *mytemplate1* ve *mytemplate2*.</span><span class="sxs-lookup"><span data-stu-id="bcaec-197">The *templates* folder contains two templates, *mytemplate1* and *mytemplate2*.</span></span> <span data-ttu-id="bcaec-198">Her şablon içerik dosyalarına sahip ve bir *. template.config* klasörüyle bir *template.json* yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="bcaec-198">Each template has content files and a *.template.config* folder with a *template.json* config file.</span></span>

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

## <a name="installing-a-template"></a><span data-ttu-id="bcaec-199">Bir şablon yüklenirken</span><span class="sxs-lookup"><span data-stu-id="bcaec-199">Installing a template</span></span>

<span data-ttu-id="bcaec-200">Kullanım [yeni dotnet -i |--yükleme](dotnet-new.md) bir paketini yüklemek için komutu.</span><span class="sxs-lookup"><span data-stu-id="bcaec-200">Use the [dotnet new -i|--install](dotnet-new.md) command to install a package.</span></span>

### <a name="to-install-a-template-from-a-nuget-package-stored-at-nugetorg"></a><span data-ttu-id="bcaec-201">Bir şablon nuget.org depolanan bir NuGet paketini yüklemek için</span><span class="sxs-lookup"><span data-stu-id="bcaec-201">To install a template from a NuGet package stored at nuget.org</span></span>

<span data-ttu-id="bcaec-202">Bir şablon paketi yüklemek için NuGet paket tanımlayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="bcaec-202">Use the NuGet package identifier to install a template package.</span></span>

```console
dotnet new -i <NUGET_PACKAGE_ID>
```

### <a name="to-install-a-template-from-a-local-nupkg-file"></a><span data-ttu-id="bcaec-203">Bir şablon nupkg yerel dosyadan yüklemek için</span><span class="sxs-lookup"><span data-stu-id="bcaec-203">To install a template from a local nupkg file</span></span>

<span data-ttu-id="bcaec-204">Yolu sağlayan bir *.nupkg* NuGet paket dosyası.</span><span class="sxs-lookup"><span data-stu-id="bcaec-204">Provide the path to a *.nupkg* NuGet package file.</span></span>

```console
dotnet new -i <PATH_TO_NUPKG_FILE>
```

### <a name="to-install-a-template-from-a-file-system-directory"></a><span data-ttu-id="bcaec-205">Bir şablon bir dosya sistemi dizinden yüklemek için</span><span class="sxs-lookup"><span data-stu-id="bcaec-205">To install a template from a file system directory</span></span>

<span data-ttu-id="bcaec-206">Şablonları yüklenebilir bir şablon klasöründen gibi *mytemplate1* Yukarıdaki örnekteki klasör.</span><span class="sxs-lookup"><span data-stu-id="bcaec-206">Templates can be installed from a template folder, such as the *mytemplate1* folder from the example above.</span></span> <span data-ttu-id="bcaec-207">Klasör yolunu belirtin *. template.config* klasör.</span><span class="sxs-lookup"><span data-stu-id="bcaec-207">Specify the folder path of the *.template.config* folder.</span></span> <span data-ttu-id="bcaec-208">Şablon dizini yolu mutlak olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="bcaec-208">The path to the template directory does not need to be absolute.</span></span> <span data-ttu-id="bcaec-209">Ancak, bir klasörden yüklü olan bir şablonu kaldırmak için bir mutlak yol gereklidir.</span><span class="sxs-lookup"><span data-stu-id="bcaec-209">However, an absolute path is required to uninstall a template that is installed from a folder.</span></span>

```console
dotnet new -i <FILE_SYSTEM_DIRECTORY>
```

## <a name="get-a-list-of-installed-templates"></a><span data-ttu-id="bcaec-210">Yüklü şablonlar listesinden Al</span><span class="sxs-lookup"><span data-stu-id="bcaec-210">Get a list of installed templates</span></span>

<span data-ttu-id="bcaec-211">Kaldırma komutu hiçbir parametre olmadan, yüklü tüm şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="bcaec-211">The uninstall command, without any other parameters, will list all installed templates.</span></span>

```console
dotnet new -u
```

<span data-ttu-id="bcaec-212">Bu komut aşağıdaki çıktıya benzer bir şey döndürür:</span><span class="sxs-lookup"><span data-stu-id="bcaec-212">That command returns something similar to the following output:</span></span>

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

<span data-ttu-id="bcaec-213">Öğelerden sonra ilk düzeyini `Currently installed items:` olan bir şablonu kaldırma içinde kullanılan tanımlayıcıları.</span><span class="sxs-lookup"><span data-stu-id="bcaec-213">The first level of items after `Currently installed items:` are the identifiers used in uninstalling a template.</span></span> <span data-ttu-id="bcaec-214">Ve yukarıdaki örnekte, `Microsoft.DotNet.Common.ItemTemplates` ve `Microsoft.DotNet.Common.ProjectTemplates.3.0` listelenir.</span><span class="sxs-lookup"><span data-stu-id="bcaec-214">And in the example above, `Microsoft.DotNet.Common.ItemTemplates` and `Microsoft.DotNet.Common.ProjectTemplates.3.0` are listed.</span></span> <span data-ttu-id="bcaec-215">Bu tanımlayıcı bir dosya sistemi yolu kullanarak şablonu yüklenmişse, klasör yolunu, olur *. template.config* klasör.</span><span class="sxs-lookup"><span data-stu-id="bcaec-215">If the template was installed by using a file system path, this identifier will the folder path of the *.template.config* folder.</span></span>

## <a name="uninstalling-a-template"></a><span data-ttu-id="bcaec-216">Bir şablon kaldırma</span><span class="sxs-lookup"><span data-stu-id="bcaec-216">Uninstalling a template</span></span>

<span data-ttu-id="bcaec-217">Kullanım [yeni dotnet -u |--kaldırma](dotnet-new.md) paketi kaldırmak için komutu.</span><span class="sxs-lookup"><span data-stu-id="bcaec-217">Use the [dotnet new -u|--uninstall](dotnet-new.md) command to uninstall a package.</span></span>

<span data-ttu-id="bcaec-218">Paket bir NuGet akışı tarafından ya da yüklenmişse bir *.nupkg* doğrudan dosya, tanımlayıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="bcaec-218">If the package was installed by either a NuGet feed or by a *.nupkg* file directly, provide the identifier.</span></span>

```console
dotnet new -u <NUGET_PACKAGE_ID>
```

<span data-ttu-id="bcaec-219">Paket bir yolunu belirterek yüklendiyse *. template.config* klasöründe kullanan **mutlak** paketi kaldırma yolu.</span><span class="sxs-lookup"><span data-stu-id="bcaec-219">If the package was installed by specifying a path to the *.template.config* folder, use that **absolute** path to uninstall the package.</span></span> <span data-ttu-id="bcaec-220">Şablon tarafından sağlanan çıkış mutlak yolu gördüğünüz `dotnet new -u` komutu.</span><span class="sxs-lookup"><span data-stu-id="bcaec-220">You can see the absolute path of the template in the output provided by the `dotnet new -u` command.</span></span> <span data-ttu-id="bcaec-221">Daha fazla bilgi için [yüklü şablonlar listesinden alma](#get-a-list-of-installed-templates) yukarıdaki bölümde.</span><span class="sxs-lookup"><span data-stu-id="bcaec-221">For more information, see the [Get a list of installed templates](#get-a-list-of-installed-templates) section above.</span></span>

```console
dotnet new -u <ABSOLUTE_FILE_SYSTEM_DIRECTORY>
```

## <a name="create-a-project-using-a-custom-template"></a><span data-ttu-id="bcaec-222">Özel bir şablon kullanarak bir proje oluşturun</span><span class="sxs-lookup"><span data-stu-id="bcaec-222">Create a project using a custom template</span></span>

<span data-ttu-id="bcaec-223">Şablon yüklendikten sonra şablonu yürüterek kullanmak `dotnet new <TEMPLATE>` diğer önceden yüklenmiş şablonu olduğu gibi komutu.</span><span class="sxs-lookup"><span data-stu-id="bcaec-223">After a template is installed, use the template by executing the `dotnet new <TEMPLATE>` command as you would with any other pre-installed template.</span></span> <span data-ttu-id="bcaec-224">Belirtebilirsiniz [seçenekleri](dotnet-new.md#options) için `dotnet new` şablon ayarlarında yapılandırdığınız şablon özgü seçenekleri dahil olmak üzere komutu.</span><span class="sxs-lookup"><span data-stu-id="bcaec-224">You can also specify [options](dotnet-new.md#options) to the `dotnet new` command, including template-specific options you configured in the template settings.</span></span> <span data-ttu-id="bcaec-225">Şablonun doğrudan komutuna kısa ad belirtin:</span><span class="sxs-lookup"><span data-stu-id="bcaec-225">Supply the template's short name directly to the command:</span></span>

```console
dotnet new <TEMPLATE>
```

## <a name="see-also"></a><span data-ttu-id="bcaec-226">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bcaec-226">See also</span></span>

- [<span data-ttu-id="bcaec-227">Yeni dotnet (eğitim) için özel bir şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="bcaec-227">Create a custom template for dotnet new (tutorial)</span></span>](../tutorials/create-custom-template.md)
- [<span data-ttu-id="bcaec-228">DotNet/şablon GitHub deposunu Wiki</span><span class="sxs-lookup"><span data-stu-id="bcaec-228">dotnet/templating GitHub repo Wiki</span></span>](https://github.com/dotnet/templating/wiki)
- [<span data-ttu-id="bcaec-229">DotNet/dotnet-şablonu-örnekleri GitHub deposu</span><span class="sxs-lookup"><span data-stu-id="bcaec-229">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="bcaec-230">Dotnet için kendi şablonlarınızı yeni oluşturma</span><span class="sxs-lookup"><span data-stu-id="bcaec-230">How to create your own templates for dotnet new</span></span>](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/)
- [<span data-ttu-id="bcaec-231">*Template.JSON* JSON şema Store şema</span><span class="sxs-lookup"><span data-stu-id="bcaec-231">*template.json* schema at the JSON Schema Store</span></span>](http://json.schemastore.org/template)
