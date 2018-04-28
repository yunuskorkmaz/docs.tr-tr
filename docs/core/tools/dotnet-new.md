---
title: DotNet yeni komutu - .NET Core CLI
description: Dotnet yeni komut belirtilen şablona dayalı yeni .NET Core projelerini oluşturur.
author: mairaw
ms.author: mairaw
ms.date: 03/26/2018
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: ab8d6f779a428aab7bd2739105dcf08b51d14ab9
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-new"></a><span data-ttu-id="21f51-103">DotNet yeni</span><span class="sxs-lookup"><span data-stu-id="21f51-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="21f51-104">Ad</span><span class="sxs-lookup"><span data-stu-id="21f51-104">Name</span></span>

<span data-ttu-id="21f51-105">`dotnet new` -Yeni Proje, yapılandırma dosyası veya belirtilen şablona dayalı çözüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="21f51-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="21f51-106">Özet</span><span class="sxs-lookup"><span data-stu-id="21f51-106">Synopsis</span></span>

# <a name="net-core-20tabnetcore2x"></a>[<span data-ttu-id="21f51-107">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="21f51-107">.NET Core 2.0</span></span>](#tab/netcore2x)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="21f51-108">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="21f51-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="21f51-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="21f51-109">Description</span></span>

<span data-ttu-id="21f51-110">`dotnet new` Komutu geçerli bir .NET Core projeyi başlatmak için kolay bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="21f51-110">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="21f51-111">Komut çağrıları [şablon motoru](https://github.com/dotnet/templating) yapıları belirtilen şablonu ve seçenekleri bağlı disk oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="21f51-111">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="21f51-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="21f51-112">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="21f51-113">Komutu çağrıldığında örneği oluşturmak için şablon.</span><span class="sxs-lookup"><span data-stu-id="21f51-113">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="21f51-114">Her bir şablon geçirebilirsiniz belirli seçenekleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="21f51-114">Each template might have specific options you can pass.</span></span> <span data-ttu-id="21f51-115">Daha fazla bilgi için bkz: [şablon seçenekleri](#template-options).</span><span class="sxs-lookup"><span data-stu-id="21f51-115">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-20tabnetcore2x"></a>[<span data-ttu-id="21f51-116">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="21f51-116">.NET Core 2.0</span></span>](#tab/netcore2x)

<span data-ttu-id="21f51-117">Komut şablonlarının varsayılan listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="21f51-117">The command contains a default list of templates.</span></span> <span data-ttu-id="21f51-118">Kullanım `dotnet new -l` kullanılabilir şablonların listesini elde edilir.</span><span class="sxs-lookup"><span data-stu-id="21f51-118">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="21f51-119">Aşağıdaki tabloda .NET Core 2.0 SDK ile birlikte önceden yüklenmiş olarak gelen şablonları gösterir.</span><span class="sxs-lookup"><span data-stu-id="21f51-119">The following table shows the templates that come pre-installed with the .NET Core 2.0 SDK.</span></span> <span data-ttu-id="21f51-120">Şablon için varsayılan dili köşeli ayraçlar içinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="21f51-120">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="21f51-121">Şablon açıklaması</span><span class="sxs-lookup"><span data-stu-id="21f51-121">Template description</span></span>                          | <span data-ttu-id="21f51-122">Şablon adı</span><span class="sxs-lookup"><span data-stu-id="21f51-122">Template name</span></span> | <span data-ttu-id="21f51-123">Diller</span><span class="sxs-lookup"><span data-stu-id="21f51-123">Languages</span></span>     |
|----------------------------------------------|---------------|---------------|
| <span data-ttu-id="21f51-124">Konsol uygulaması</span><span class="sxs-lookup"><span data-stu-id="21f51-124">Console application</span></span>                          | `console`     | <span data-ttu-id="21f51-125">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="21f51-125">[C#], F#, VB</span></span>  |
| <span data-ttu-id="21f51-126">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="21f51-126">Class library</span></span>                                | `classlib`    | <span data-ttu-id="21f51-127">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="21f51-127">[C#], F#, VB</span></span>  |
| <span data-ttu-id="21f51-128">Birim testi projesi</span><span class="sxs-lookup"><span data-stu-id="21f51-128">Unit test project</span></span>                            | `mstest`      | <span data-ttu-id="21f51-129">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="21f51-129">[C#], F#, VB</span></span>  |
| <span data-ttu-id="21f51-130">xUnit test projesi</span><span class="sxs-lookup"><span data-stu-id="21f51-130">xUnit test project</span></span>                           | `xunit`       | <span data-ttu-id="21f51-131">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="21f51-131">[C#], F#, VB</span></span>  |
| <span data-ttu-id="21f51-132">ASP.NET Core boş</span><span class="sxs-lookup"><span data-stu-id="21f51-132">ASP.NET Core empty</span></span>                           | `web`         | <span data-ttu-id="21f51-133">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="21f51-133">[C#], F#</span></span>      |
| <span data-ttu-id="21f51-134">ASP.NET Core Web uygulaması (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="21f51-134">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="21f51-135">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="21f51-135">[C#], F#</span></span>      |
| <span data-ttu-id="21f51-136">ASP.NET Core Web uygulaması</span><span class="sxs-lookup"><span data-stu-id="21f51-136">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="21f51-137">[C#]</span><span class="sxs-lookup"><span data-stu-id="21f51-137">[C#]</span></span>          |
| <span data-ttu-id="21f51-138">ASP.NET Core Açısal ile</span><span class="sxs-lookup"><span data-stu-id="21f51-138">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="21f51-139">[C#]</span><span class="sxs-lookup"><span data-stu-id="21f51-139">[C#]</span></span>          |
| <span data-ttu-id="21f51-140">ASP.NET Core React.js ile</span><span class="sxs-lookup"><span data-stu-id="21f51-140">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="21f51-141">[C#]</span><span class="sxs-lookup"><span data-stu-id="21f51-141">[C#]</span></span>          |
| <span data-ttu-id="21f51-142">ASP.NET Core React.js ve Redux</span><span class="sxs-lookup"><span data-stu-id="21f51-142">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="21f51-143">[C#]</span><span class="sxs-lookup"><span data-stu-id="21f51-143">[C#]</span></span>          |
| <span data-ttu-id="21f51-144">ASP.NET Core Web API'si</span><span class="sxs-lookup"><span data-stu-id="21f51-144">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="21f51-145">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="21f51-145">[C#], F#</span></span>      |
| <span data-ttu-id="21f51-146">Global.JSON dosyası</span><span class="sxs-lookup"><span data-stu-id="21f51-146">global.json file</span></span>                             | `globaljson`  |               |
| <span data-ttu-id="21f51-147">Nuget yapılandırma</span><span class="sxs-lookup"><span data-stu-id="21f51-147">Nuget config</span></span>                                 | `nugetconfig` |               |
| <span data-ttu-id="21f51-148">Web yapılandırma</span><span class="sxs-lookup"><span data-stu-id="21f51-148">Web config</span></span>                                   | `webconfig`   |               |
| <span data-ttu-id="21f51-149">Çözüm dosyası</span><span class="sxs-lookup"><span data-stu-id="21f51-149">Solution file</span></span>                                | `sln`         |               |
| <span data-ttu-id="21f51-150">Razor sayfası</span><span class="sxs-lookup"><span data-stu-id="21f51-150">Razor page</span></span>                                   | `page`        |               |
| <span data-ttu-id="21f51-151">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="21f51-151">MVC ViewImports</span></span>                              | `viewimports` |               |
| <span data-ttu-id="21f51-152">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="21f51-152">MVC ViewStart</span></span>                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="21f51-153">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="21f51-153">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="21f51-154">Komut şablonlarının varsayılan listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="21f51-154">The command contains a default list of templates.</span></span> <span data-ttu-id="21f51-155">Kullanım `dotnet new -all` kullanılabilir şablonların listesini elde edilir.</span><span class="sxs-lookup"><span data-stu-id="21f51-155">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="21f51-156">.NET Core ile önceden yüklenmiş olarak gelen şablonları aşağıdaki tabloda gösterilmektedir 1.x SDK.</span><span class="sxs-lookup"><span data-stu-id="21f51-156">The following table shows the templates that come pre-installed with the .NET Core 1.x SDK.</span></span> <span data-ttu-id="21f51-157">Şablon için varsayılan dili köşeli ayraçlar içinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="21f51-157">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="21f51-158">Şablon açıklaması</span><span class="sxs-lookup"><span data-stu-id="21f51-158">Template description</span></span>  | <span data-ttu-id="21f51-159">Şablon adı</span><span class="sxs-lookup"><span data-stu-id="21f51-159">Template name</span></span> | <span data-ttu-id="21f51-160">Diller</span><span class="sxs-lookup"><span data-stu-id="21f51-160">Languages</span></span> |
|----------------------|---------------|-----------|
| <span data-ttu-id="21f51-161">Konsol uygulaması</span><span class="sxs-lookup"><span data-stu-id="21f51-161">Console application</span></span>  | `console`     | <span data-ttu-id="21f51-162">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="21f51-162">[C#], F#</span></span>  |
| <span data-ttu-id="21f51-163">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="21f51-163">Class library</span></span>        | `classlib`    | <span data-ttu-id="21f51-164">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="21f51-164">[C#], F#</span></span>  |
| <span data-ttu-id="21f51-165">Birim testi projesi</span><span class="sxs-lookup"><span data-stu-id="21f51-165">Unit test project</span></span>    | `mstest`      | <span data-ttu-id="21f51-166">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="21f51-166">[C#], F#</span></span>  |
| <span data-ttu-id="21f51-167">xUnit test projesi</span><span class="sxs-lookup"><span data-stu-id="21f51-167">xUnit test project</span></span>   | `xunit`       | <span data-ttu-id="21f51-168">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="21f51-168">[C#], F#</span></span>  |
| <span data-ttu-id="21f51-169">ASP.NET Core boş</span><span class="sxs-lookup"><span data-stu-id="21f51-169">ASP.NET Core empty</span></span>   | `web`         | <span data-ttu-id="21f51-170">[C#]</span><span class="sxs-lookup"><span data-stu-id="21f51-170">[C#]</span></span>      |
| <span data-ttu-id="21f51-171">ASP.NET Core Web uygulaması</span><span class="sxs-lookup"><span data-stu-id="21f51-171">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="21f51-172">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="21f51-172">[C#], F#</span></span>  |
| <span data-ttu-id="21f51-173">ASP.NET Core Web API'si</span><span class="sxs-lookup"><span data-stu-id="21f51-173">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="21f51-174">[C#]</span><span class="sxs-lookup"><span data-stu-id="21f51-174">[C#]</span></span>      |
| <span data-ttu-id="21f51-175">Nuget yapılandırma</span><span class="sxs-lookup"><span data-stu-id="21f51-175">Nuget config</span></span>         | `nugetconfig` |           |
| <span data-ttu-id="21f51-176">Web yapılandırma</span><span class="sxs-lookup"><span data-stu-id="21f51-176">Web config</span></span>           | `webconfig`   |           |
| <span data-ttu-id="21f51-177">Çözüm dosyası</span><span class="sxs-lookup"><span data-stu-id="21f51-177">Solution file</span></span>        | `sln`         |           |

---

## <a name="options"></a><span data-ttu-id="21f51-178">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="21f51-178">Options</span></span>

# <a name="net-core-20tabnetcore2x"></a>[<span data-ttu-id="21f51-179">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="21f51-179">.NET Core 2.0</span></span>](#tab/netcore2x)

`--force`

<span data-ttu-id="21f51-180">Var olan dosyaları değişeceğinden olsa bile oluşturulacak içeriği zorlar.</span><span class="sxs-lookup"><span data-stu-id="21f51-180">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="21f51-181">Çıktı dizini bir proje zaten içeriyor, bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="21f51-181">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="21f51-182">Komut için Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="21f51-182">Prints out help for the command.</span></span> <span data-ttu-id="21f51-183">İçin çağrılabilir `dotnet new` kendisini komut veya herhangi bir şablonu gibi `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="21f51-183">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="21f51-184">Bir kaynak veya şablon paketinden yükler `PATH` veya `NUGET_ID` sağlanan.</span><span class="sxs-lookup"><span data-stu-id="21f51-184">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="21f51-185">Bir şablon paketini bir ön sürümünü yüklemek istiyorsanız, sürüm biçiminde belirtmeniz gerekir `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="21f51-185">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="21f51-186">Varsayılan olarak, `dotnet new` geçirir \* sürümü için temsil eden en son kararlı Paket sürümü.</span><span class="sxs-lookup"><span data-stu-id="21f51-186">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="21f51-187">Bir örneğe bakın [örnekler](#examples) bölümü.</span><span class="sxs-lookup"><span data-stu-id="21f51-187">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="21f51-188">Özel şablonlar oluşturma hakkında daha fazla bilgi için bkz: [yeni dotnet için özel şablonlar](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="21f51-188">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="21f51-189">Belirtilen ad içeren şablonlarını listeler.</span><span class="sxs-lookup"><span data-stu-id="21f51-189">Lists templates containing the specified name.</span></span> <span data-ttu-id="21f51-190">İçin başlatılırsa `dotnet new` komutu için belirtilen dizin kullanılabilir olası şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="21f51-190">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="21f51-191">Örneğin dizini zaten bir proje içeriyorsa, tüm proje şablonları listesinde değil.</span><span class="sxs-lookup"><span data-stu-id="21f51-191">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="21f51-192">Oluşturmak için şablon dili.</span><span class="sxs-lookup"><span data-stu-id="21f51-192">The language of the template to create.</span></span> <span data-ttu-id="21f51-193">Dil kabul değişir şablon tarafından (varsayılan ayarlarında bkz [bağımsız değişkenleri](#arguments) bölümü).</span><span class="sxs-lookup"><span data-stu-id="21f51-193">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="21f51-194">Bazı şablonlar için geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="21f51-194">Not valid for some templates.</span></span>

    > [!NOTE]
    > Some shells interpret `#` as a special character. In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="21f51-195">Oluşturulan çıktı adı.</span><span class="sxs-lookup"><span data-stu-id="21f51-195">The name for the created output.</span></span> <span data-ttu-id="21f51-196">Ad belirtilmezse, geçerli dizin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="21f51-196">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="21f51-197">Oluşturulan çıktı yerleştirileceği konum.</span><span class="sxs-lookup"><span data-stu-id="21f51-197">Location to place the generated output.</span></span> <span data-ttu-id="21f51-198">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="21f51-198">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="21f51-199">Şablonlar kullanılabilir türlerine göre filtreler.</span><span class="sxs-lookup"><span data-stu-id="21f51-199">Filters templates based on available types.</span></span> <span data-ttu-id="21f51-200">Önceden tanımlanmış değerler "proje", "öğesi" veya "diğer" olabilir.</span><span class="sxs-lookup"><span data-stu-id="21f51-200">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="21f51-201">Bir kaynak veya şablon paketini kaldırır `PATH` veya `NUGET_ID` sağlanan.</span><span class="sxs-lookup"><span data-stu-id="21f51-201">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="21f51-202">Bir şablon kullanarak kaldırmak için bir `PATH`, yolun tam olarak nitelemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="21f51-202">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="21f51-203">Örneğin, *C:/Users/\<kullanıcı > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* çalışır, ancak *./GarciaSoftware.ConsoleTemplate.CSharp* içeren gelen Klasör almayacak.</span><span class="sxs-lookup"><span data-stu-id="21f51-203">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="21f51-204">Ayrıca, şablonu yoldaki son sonlandırma dizin eğik çizgi eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="21f51-204">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="21f51-205">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="21f51-205">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="21f51-206">Belirli bir proje türü için tüm şablonları bağlamında çalışırken gösterir `dotnet new` tek başına komutu.</span><span class="sxs-lookup"><span data-stu-id="21f51-206">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="21f51-207">Belirli bir şablon bağlamda gibi çalıştırırken `dotnet new web -all`, `-all` zorla oluşturma bayrak olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="21f51-207">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="21f51-208">Çıktı dizini bir proje zaten içeriyor, bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="21f51-208">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="21f51-209">Komut için Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="21f51-209">Prints out help for the command.</span></span> <span data-ttu-id="21f51-210">İçin çağrılabilir `dotnet new` kendisini komut veya herhangi bir şablonu gibi `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="21f51-210">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="21f51-211">Belirtilen ad içeren şablonlarını listeler.</span><span class="sxs-lookup"><span data-stu-id="21f51-211">Lists templates containing the specified name.</span></span> <span data-ttu-id="21f51-212">İçin başlatılırsa `dotnet new` komutu için belirtilen dizin kullanılabilir olası şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="21f51-212">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="21f51-213">Örneğin dizini zaten bir proje içeriyorsa, tüm proje şablonları listesinde değil.</span><span class="sxs-lookup"><span data-stu-id="21f51-213">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="21f51-214">Oluşturmak için şablon dili.</span><span class="sxs-lookup"><span data-stu-id="21f51-214">The language of the template to create.</span></span> <span data-ttu-id="21f51-215">Dil kabul değişir şablon tarafından (varsayılan ayarlarında bkz [bağımsız değişkenleri](#arguments) bölümü).</span><span class="sxs-lookup"><span data-stu-id="21f51-215">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="21f51-216">Bazı şablonlar için geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="21f51-216">Not valid for some templates.</span></span>

    > [!NOTE]
    > Some shells interpret `#` as a special character. In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="21f51-217">Oluşturulan çıktı adı.</span><span class="sxs-lookup"><span data-stu-id="21f51-217">The name for the created output.</span></span> <span data-ttu-id="21f51-218">Ad belirtilmezse, geçerli dizin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="21f51-218">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="21f51-219">Oluşturulan çıktı yerleştirileceği konum.</span><span class="sxs-lookup"><span data-stu-id="21f51-219">Location to place the generated output.</span></span> <span data-ttu-id="21f51-220">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="21f51-220">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="21f51-221">Şablon seçenekleri</span><span class="sxs-lookup"><span data-stu-id="21f51-221">Template options</span></span>

<span data-ttu-id="21f51-222">Her proje şablonu ek seçenekleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="21f51-222">Each project template may have additional options available.</span></span> <span data-ttu-id="21f51-223">Çekirdek şablonları aşağıdaki ek seçeneklere sahip olursunuz:</span><span class="sxs-lookup"><span data-stu-id="21f51-223">The core templates have the following additional options:</span></span>

# <a name="net-core-20tabnetcore2x"></a>[<span data-ttu-id="21f51-224">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="21f51-224">.NET Core 2.0</span></span>](#tab/netcore2x)

<span data-ttu-id="21f51-225">**konsolunda, Açısal, tepki, reactredux**</span><span class="sxs-lookup"><span data-stu-id="21f51-225">**console, angular, react, reactredux**</span></span>

  <span data-ttu-id="21f51-226">`--no-restore` -Proje oluşturma sırasında örtük bir geri yükleme yapın değil.</span><span class="sxs-lookup"><span data-stu-id="21f51-226">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="21f51-227">**ClassLib**</span><span class="sxs-lookup"><span data-stu-id="21f51-227">**classlib**</span></span>

<span data-ttu-id="21f51-228">`-f|--framework <FRAMEWORK>` -Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="21f51-228">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="21f51-229">Değerler: `netcoreapp2.0` .NET çekirdek sınıf kitaplığı oluşturmak için veya `netstandard2.0` .NET standart sınıf kitaplığı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="21f51-229">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="21f51-230">Varsayılan değer `netstandard2.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="21f51-230">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="21f51-231">`--no-restore` -Proje oluşturma sırasında örtük bir geri yükleme yapın değil.</span><span class="sxs-lookup"><span data-stu-id="21f51-231">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="21f51-232">**mstest'i, xunit**</span><span class="sxs-lookup"><span data-stu-id="21f51-232">**mstest, xunit**</span></span>

<span data-ttu-id="21f51-233">`-p|--enable-pack` -Proje kullanma paketleme sağlar [dotnet paketi](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="21f51-233">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="21f51-234">`--no-restore` -Proje oluşturma sırasında örtük bir geri yükleme yapın değil.</span><span class="sxs-lookup"><span data-stu-id="21f51-234">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="21f51-235">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="21f51-235">**globaljson**</span></span>

<span data-ttu-id="21f51-236">`--sdk-version <VERSION_NUMBER>` -Kullanmak için .NET Core SDK sürümünü belirtir *global.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="21f51-236">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="21f51-237">**Web**</span><span class="sxs-lookup"><span data-stu-id="21f51-237">**web**</span></span>

<span data-ttu-id="21f51-238">`--use-launch-settings` -İçeren *launchSettings.json* oluşturulan şablon çıkışı.</span><span class="sxs-lookup"><span data-stu-id="21f51-238">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="21f51-239">`--no-restore` -Proje oluşturma sırasında örtük bir geri yükleme yapın değil.</span><span class="sxs-lookup"><span data-stu-id="21f51-239">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="21f51-240">**webapı**</span><span class="sxs-lookup"><span data-stu-id="21f51-240">**webapi**</span></span>

<span data-ttu-id="21f51-241">`-au|--auth <AUTHENTICATION_TYPE>` -Kullanılacak kimlik doğrulama türü.</span><span class="sxs-lookup"><span data-stu-id="21f51-241">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="21f51-242">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="21f51-242">The possible values are:</span></span>

- <span data-ttu-id="21f51-243">`None` -Kimlik doğrulama yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="21f51-243">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="21f51-244">`IndividualB2C` -Azure AD B2C ile tek tek kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="21f51-244">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="21f51-245">`SingleOrg` -Tek bir kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="21f51-245">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="21f51-246">`Windows` -Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="21f51-246">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="21f51-247">`--aad-b2c-instance <INSTANCE>` -Bağlanmak için Azure Active Directory B2C örnek.</span><span class="sxs-lookup"><span data-stu-id="21f51-247">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="21f51-248">İle kullandığınız `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="21f51-248">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="21f51-249">Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="21f51-249">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="21f51-250">`-ssp|--susi-policy-id <ID>` -Bu proje için oturum açma ve kaydolma ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="21f51-250">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="21f51-251">İle kullandığınız `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="21f51-251">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="21f51-252">`--aad-instance <INSTANCE>` -Bağlanmak için Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="21f51-252">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="21f51-253">İle kullandığınız `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="21f51-253">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="21f51-254">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="21f51-254">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="21f51-255">`--client-id <ID>` -Bu proje için istemci kimliği.</span><span class="sxs-lookup"><span data-stu-id="21f51-255">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="21f51-256">İle kullandığınız `IndividualB2C` veya `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="21f51-256">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="21f51-257">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="21f51-257">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="21f51-258">`--domain <DOMAIN>` -Etki alanı için dizin Kiracı.</span><span class="sxs-lookup"><span data-stu-id="21f51-258">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="21f51-259">İle kullandığınız `SingleOrg` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="21f51-259">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="21f51-260">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="21f51-260">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="21f51-261">`--tenant-id <ID>` -Tenantıd bağlanmak için kimliği dizini.</span><span class="sxs-lookup"><span data-stu-id="21f51-261">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="21f51-262">İle kullandığınız `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="21f51-262">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="21f51-263">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="21f51-263">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="21f51-264">`-r|--org-read-access` -Bu uygulamanın dizine okuma erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="21f51-264">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="21f51-265">Yalnızca uygular `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="21f51-265">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="21f51-266">`--use-launch-settings` -İçeren *launchSettings.json* oluşturulan şablon çıkışı.</span><span class="sxs-lookup"><span data-stu-id="21f51-266">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="21f51-267">`-uld|--use-local-db` -Yerel veritabanı yerine SQLite kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="21f51-267">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="21f51-268">Yalnızca uygular `Individual` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="21f51-268">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="21f51-269">`--no-restore` -Proje oluşturma sırasında örtük bir geri yükleme yapın değil.</span><span class="sxs-lookup"><span data-stu-id="21f51-269">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="21f51-270">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="21f51-270">**mvc, razor**</span></span>

<span data-ttu-id="21f51-271">`-au|--auth <AUTHENTICATION_TYPE>` -Kullanılacak kimlik doğrulama türü.</span><span class="sxs-lookup"><span data-stu-id="21f51-271">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="21f51-272">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="21f51-272">The possible values are:</span></span>

- <span data-ttu-id="21f51-273">`None` -Kimlik doğrulama yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="21f51-273">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="21f51-274">`Individual` -Tek tek kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="21f51-274">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="21f51-275">`IndividualB2C` -Azure AD B2C ile tek tek kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="21f51-275">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="21f51-276">`SingleOrg` -Tek bir kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="21f51-276">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="21f51-277">`MultiOrg` -Birden çok Kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="21f51-277">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="21f51-278">`Windows` -Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="21f51-278">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="21f51-279">`--aad-b2c-instance <INSTANCE>` -Bağlanmak için Azure Active Directory B2C örnek.</span><span class="sxs-lookup"><span data-stu-id="21f51-279">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="21f51-280">İle kullandığınız `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="21f51-280">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="21f51-281">Varsayılan değer `https://login.microsoftonline.com/tfp/` .</span><span class="sxs-lookup"><span data-stu-id="21f51-281">The default value is `https://login.microsoftonline.com/tfp/` .</span></span>

<span data-ttu-id="21f51-282">`-ssp|--susi-policy-id <ID>` -Bu proje için oturum açma ve kaydolma ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="21f51-282">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="21f51-283">İle kullandığınız `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="21f51-283">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="21f51-284">`-rp|--reset-password-policy-id <ID>` -Bu proje için reset parola ilkesi kimliği.</span><span class="sxs-lookup"><span data-stu-id="21f51-284">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="21f51-285">İle kullandığınız `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="21f51-285">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="21f51-286">`-ep|--edit-profile-policy-id <ID>` -Bu proje için Düzenle profili ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="21f51-286">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="21f51-287">İle kullandığınız `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="21f51-287">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="21f51-288">`--aad-instance <INSTANCE>` -Bağlanmak için Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="21f51-288">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="21f51-289">İle kullandığınız `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="21f51-289">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="21f51-290">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="21f51-290">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="21f51-291">`--client-id <ID>` -Bu proje için istemci kimliği.</span><span class="sxs-lookup"><span data-stu-id="21f51-291">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="21f51-292">İle kullandığınız `IndividualB2C`, `SingleOrg`, veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="21f51-292">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="21f51-293">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="21f51-293">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="21f51-294">`--domain <DOMAIN>` -Etki alanı için dizin Kiracı.</span><span class="sxs-lookup"><span data-stu-id="21f51-294">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="21f51-295">İle kullandığınız `SingleOrg` veya `IndividualB2C` kimlik doğrulaması...</span><span class="sxs-lookup"><span data-stu-id="21f51-295">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="21f51-296">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="21f51-296">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="21f51-297">`--tenant-id <ID>` -Tenantıd bağlanmak için kimliği dizini.</span><span class="sxs-lookup"><span data-stu-id="21f51-297">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="21f51-298">İle kullandığınız `SingleOrg` kimlik doğrulaması...</span><span class="sxs-lookup"><span data-stu-id="21f51-298">Use with `SingleOrg` authentication..</span></span> <span data-ttu-id="21f51-299">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="21f51-299">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="21f51-300">`--callback-path <PATH>` -Yeniden yönlendirme URI'si, uygulamanın taban yolu içindeki istek yolu.</span><span class="sxs-lookup"><span data-stu-id="21f51-300">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="21f51-301">İle kullandığınız `SingleOrg` veya `IndividualB2C` kimlik doğrulaması...</span><span class="sxs-lookup"><span data-stu-id="21f51-301">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="21f51-302">Varsayılan değer `/signin-oidc` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="21f51-302">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="21f51-303">`-r|--org-read-access` -Bu uygulamanın dizine okuma erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="21f51-303">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="21f51-304">Yalnızca uygular `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="21f51-304">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="21f51-305">`--use-launch-settings` -İçeren *launchSettings.json* oluşturulan şablon çıkışı.</span><span class="sxs-lookup"><span data-stu-id="21f51-305">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="21f51-306">`--use-browserlink` -BrowserLink projede içerir.</span><span class="sxs-lookup"><span data-stu-id="21f51-306">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="21f51-307">`-uld|--use-local-db` -Yerel veritabanı yerine SQLite kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="21f51-307">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="21f51-308">Yalnızca uygular `Individual` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="21f51-308">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="21f51-309">`--no-restore` -Proje oluşturma sırasında örtük bir geri yükleme yapın değil.</span><span class="sxs-lookup"><span data-stu-id="21f51-309">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="21f51-310">**Sayfa**</span><span class="sxs-lookup"><span data-stu-id="21f51-310">**page**</span></span>

<span data-ttu-id="21f51-311">`-na|--namespace <NAMESPACE_NAME>`-Namespace üretilen kod için.</span><span class="sxs-lookup"><span data-stu-id="21f51-311">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="21f51-312">Varsayılan değer `MyApp.Namespace` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="21f51-312">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="21f51-313">`-np|--no-pagemodel` -Bir PageModel olmadan sayfası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="21f51-313">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="21f51-314">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="21f51-314">**viewimports**</span></span>

<span data-ttu-id="21f51-315">`-na|--namespace <NAMESPACE_NAME>`-Namespace üretilen kod için.</span><span class="sxs-lookup"><span data-stu-id="21f51-315">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="21f51-316">Varsayılan değer `MyApp.Namespace` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="21f51-316">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="21f51-317">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="21f51-317">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="21f51-318">**Konsolu, xunit, mstest'i, web, webapı**</span><span class="sxs-lookup"><span data-stu-id="21f51-318">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="21f51-319">`-f|--framework` -Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="21f51-319">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="21f51-320">Değerler: `netcoreapp1.0` veya `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="21f51-320">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="21f51-321">Varsayılan değer `netcoreapp1.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="21f51-321">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="21f51-322">**ClassLib**</span><span class="sxs-lookup"><span data-stu-id="21f51-322">**classlib**</span></span>

<span data-ttu-id="21f51-323">`-f|--framework` -Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="21f51-323">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="21f51-324">Değerler: `netcoreapp1.0`, `netcoreapp1.1`, veya `netstandard1.0` için `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="21f51-324">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="21f51-325">Varsayılan değer `netstandard1.4` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="21f51-325">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="21f51-326">**mvc**</span><span class="sxs-lookup"><span data-stu-id="21f51-326">**mvc**</span></span>

<span data-ttu-id="21f51-327">`-f|--framework` -Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="21f51-327">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="21f51-328">Değerler: `netcoreapp1.0` veya `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="21f51-328">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="21f51-329">Varsayılan değer `netcoreapp1.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="21f51-329">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="21f51-330">`-au|--auth` -Kullanılacak kimlik doğrulama türü.</span><span class="sxs-lookup"><span data-stu-id="21f51-330">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="21f51-331">Değerler: `None` veya `Individual`.</span><span class="sxs-lookup"><span data-stu-id="21f51-331">Values: `None` or `Individual`.</span></span> <span data-ttu-id="21f51-332">Varsayılan değer `None` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="21f51-332">The default value is `None`.</span></span>

<span data-ttu-id="21f51-333">`-uld|--use-local-db` -Yerel veritabanı yerine SQLite kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="21f51-333">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="21f51-334">Değerler: `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="21f51-334">Values: `true` or `false`.</span></span> <span data-ttu-id="21f51-335">Varsayılan değer `false` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="21f51-335">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="21f51-336">Örnekler</span><span class="sxs-lookup"><span data-stu-id="21f51-336">Examples</span></span>

<span data-ttu-id="21f51-337">Geçerli dizinde bir F # konsol uygulama projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="21f51-337">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="21f51-338">(Yalnızca .NET çekirdeği 2.0 SDK veya sonraki sürümleriyle kullanılabilir) belirtilen dizindeki .NET standart bir sınıf kitaplığı projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="21f51-338">Create a .NET Standard class library project in the specified directory (available only with .NET Core 2.0 SDK or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="21f51-339">Yeni bir ASP.NET Core C# MVC uygulama projesi geçerli dizinde kimlik doğrulamasız .NET Core 2.0 hedefleme oluşturun:</span><span class="sxs-lookup"><span data-stu-id="21f51-339">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication targeting .NET Core 2.0:</span></span>

`dotnet new mvc -au None -f netcoreapp2.0`

<span data-ttu-id="21f51-340">.NET Core 2.0 hedefleme yeni bir xUnit uygulaması oluşturun:</span><span class="sxs-lookup"><span data-stu-id="21f51-340">Create a new xUnit application targeting .NET Core 2.0:</span></span>

`dotnet new xunit --framework netcoreapp2.0`

<span data-ttu-id="21f51-341">MVC için kullanılabilir tüm şablonları listeler:</span><span class="sxs-lookup"><span data-stu-id="21f51-341">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="21f51-342">ASP.NET Core (komut seçeneği kullanılabilir .NET Core SDK 1.1 ve sonraki sürümler için) için tek sayfa uygulaması şablonlarının 2.0 sürümünü yükleyin:</span><span class="sxs-lookup"><span data-stu-id="21f51-342">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

## <a name="see-also"></a><span data-ttu-id="21f51-343">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21f51-343">See also</span></span>

[<span data-ttu-id="21f51-344">Yeni dotnet için özel şablonlar</span><span class="sxs-lookup"><span data-stu-id="21f51-344">Custom templates for dotnet new</span></span>](custom-templates.md)  
[<span data-ttu-id="21f51-345">Dotnet new için özel şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="21f51-345">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)  
[<span data-ttu-id="21f51-346">DotNet/dotnet-şablonu-samples GitHub depo</span><span class="sxs-lookup"><span data-stu-id="21f51-346">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)  
[<span data-ttu-id="21f51-347">Yeni dotnet için kullanılabilir şablonlar</span><span class="sxs-lookup"><span data-stu-id="21f51-347">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
