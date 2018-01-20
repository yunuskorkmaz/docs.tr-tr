---
title: DotNet yeni komutu - .NET Core CLI
description: "Dotnet yeni komut belirtilen şablona dayalı yeni .NET Core projelerini oluşturur."
keywords: dotnet-new, CLI, CLI command, .NET Core
author: mairaw
ms.author: mairaw
ms.date: 08/13/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: fcc3ed2e-9265-4d50-b59e-dc2e5c190b34
ms.workload: dotnetcore
ms.openlocfilehash: cf65dc80f135badcb1580726a12a9ae9d94ae3d7
ms.sourcegitcommit: 8bde7a3432f30fc771079744955c75c58c4eb393
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/20/2018
---
# <a name="dotnet-new"></a><span data-ttu-id="26d51-104">DotNet yeni</span><span class="sxs-lookup"><span data-stu-id="26d51-104">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="26d51-105">Ad</span><span class="sxs-lookup"><span data-stu-id="26d51-105">Name</span></span>

<span data-ttu-id="26d51-106">`dotnet new`-Yeni Proje, yapılandırma dosyası veya belirtilen şablona dayalı çözüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="26d51-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="26d51-107">Özet</span><span class="sxs-lookup"><span data-stu-id="26d51-107">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="26d51-108">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="26d51-108">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="26d51-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="26d51-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="26d51-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="26d51-110">Description</span></span>

<span data-ttu-id="26d51-111">`dotnet new` Komutu geçerli bir .NET Core projeyi başlatmak için kolay bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="26d51-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span> 

<span data-ttu-id="26d51-112">Komut çağrıları [şablon motoru](https://github.com/dotnet/templating) yapıları belirtilen şablonu ve seçenekleri bağlı disk oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="26d51-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="26d51-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="26d51-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="26d51-114">Komutu çağrıldığında örneği oluşturmak için şablon.</span><span class="sxs-lookup"><span data-stu-id="26d51-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="26d51-115">Her bir şablon geçirebilirsiniz belirli seçenekleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="26d51-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="26d51-116">Daha fazla bilgi için bkz: [şablon seçenekleri](#template-options).</span><span class="sxs-lookup"><span data-stu-id="26d51-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="26d51-117">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="26d51-117">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="26d51-118">Komut şablonlarının varsayılan listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="26d51-118">The command contains a default list of templates.</span></span> <span data-ttu-id="26d51-119">Kullanım `dotnet new -l` kullanılabilir şablonların listesini elde edilir.</span><span class="sxs-lookup"><span data-stu-id="26d51-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="26d51-120">Aşağıdaki tabloda .NET Core 2.0 SDK ile birlikte önceden yüklenmiş olarak gelen şablonları gösterir.</span><span class="sxs-lookup"><span data-stu-id="26d51-120">The following table shows the templates that come pre-installed with the .NET Core 2.0 SDK.</span></span> <span data-ttu-id="26d51-121">Şablon için varsayılan dili köşeli ayraçlar içinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="26d51-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="26d51-122">Şablon açıklaması</span><span class="sxs-lookup"><span data-stu-id="26d51-122">Template description</span></span>                          | <span data-ttu-id="26d51-123">Şablon adı</span><span class="sxs-lookup"><span data-stu-id="26d51-123">Template name</span></span> | <span data-ttu-id="26d51-124">Diller</span><span class="sxs-lookup"><span data-stu-id="26d51-124">Languages</span></span>     |
|----------------------------------------------|---------------|---------------|
| <span data-ttu-id="26d51-125">Konsol uygulaması</span><span class="sxs-lookup"><span data-stu-id="26d51-125">Console application</span></span>                          | `console`     | <span data-ttu-id="26d51-126">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="26d51-126">[C#], F#, VB</span></span>  |
| <span data-ttu-id="26d51-127">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="26d51-127">Class library</span></span>                                | `classlib`    | <span data-ttu-id="26d51-128">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="26d51-128">[C#], F#, VB</span></span>  |
| <span data-ttu-id="26d51-129">Birim testi projesi</span><span class="sxs-lookup"><span data-stu-id="26d51-129">Unit test project</span></span>                            | `mstest`      | <span data-ttu-id="26d51-130">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="26d51-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="26d51-131">xUnit test project</span><span class="sxs-lookup"><span data-stu-id="26d51-131">xUnit test project</span></span>                           | `xunit`       | <span data-ttu-id="26d51-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="26d51-132">[C#], F#, VB</span></span>  |
| <span data-ttu-id="26d51-133">ASP.NET Core boş</span><span class="sxs-lookup"><span data-stu-id="26d51-133">ASP.NET Core empty</span></span>                           | `web`         | <span data-ttu-id="26d51-134">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="26d51-134">[C#], F#</span></span>      |
| <span data-ttu-id="26d51-135">ASP.NET Core Web uygulaması (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="26d51-135">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="26d51-136">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="26d51-136">[C#], F#</span></span>      |
| <span data-ttu-id="26d51-137">ASP.NET Core Web uygulaması</span><span class="sxs-lookup"><span data-stu-id="26d51-137">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="26d51-138">[C#]</span><span class="sxs-lookup"><span data-stu-id="26d51-138">[C#]</span></span>          |
| <span data-ttu-id="26d51-139">ASP.NET Core Açısal ile</span><span class="sxs-lookup"><span data-stu-id="26d51-139">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="26d51-140">[C#]</span><span class="sxs-lookup"><span data-stu-id="26d51-140">[C#]</span></span>          |
| <span data-ttu-id="26d51-141">ASP.NET Core React.js ile</span><span class="sxs-lookup"><span data-stu-id="26d51-141">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="26d51-142">[C#]</span><span class="sxs-lookup"><span data-stu-id="26d51-142">[C#]</span></span>          |
| <span data-ttu-id="26d51-143">ASP.NET Core React.js ve Redux</span><span class="sxs-lookup"><span data-stu-id="26d51-143">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="26d51-144">[C#]</span><span class="sxs-lookup"><span data-stu-id="26d51-144">[C#]</span></span>          |
| <span data-ttu-id="26d51-145">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="26d51-145">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="26d51-146">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="26d51-146">[C#], F#</span></span>      |
| <span data-ttu-id="26d51-147">global.json file</span><span class="sxs-lookup"><span data-stu-id="26d51-147">global.json file</span></span>                             | `globaljson`  |               |
| <span data-ttu-id="26d51-148">Nuget yapılandırma</span><span class="sxs-lookup"><span data-stu-id="26d51-148">Nuget config</span></span>                                 | `nugetconfig` |               |
| <span data-ttu-id="26d51-149">Web yapılandırma</span><span class="sxs-lookup"><span data-stu-id="26d51-149">Web config</span></span>                                   | `webconfig`   |               |
| <span data-ttu-id="26d51-150">Çözüm dosyası</span><span class="sxs-lookup"><span data-stu-id="26d51-150">Solution file</span></span>                                | `sln`         |               |
| <span data-ttu-id="26d51-151">Razor sayfası</span><span class="sxs-lookup"><span data-stu-id="26d51-151">Razor page</span></span>                                   | `page`        |               |
| <span data-ttu-id="26d51-152">MVC/ViewImports</span><span class="sxs-lookup"><span data-stu-id="26d51-152">MVC/ViewImports</span></span>                              | `viewimports` |               |
| <span data-ttu-id="26d51-153">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="26d51-153">MVC ViewStart</span></span>                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="26d51-154">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="26d51-154">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="26d51-155">Komut şablonlarının varsayılan listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="26d51-155">The command contains a default list of templates.</span></span> <span data-ttu-id="26d51-156">Kullanım `dotnet new -all` kullanılabilir şablonların listesini elde edilir.</span><span class="sxs-lookup"><span data-stu-id="26d51-156">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="26d51-157">.NET Core ile önceden yüklenmiş olarak gelen şablonları aşağıdaki tabloda gösterilmektedir 1.x SDK.</span><span class="sxs-lookup"><span data-stu-id="26d51-157">The following table shows the templates that come pre-installed with the .NET Core 1.x SDK.</span></span> <span data-ttu-id="26d51-158">Şablon için varsayılan dili köşeli ayraçlar içinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="26d51-158">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="26d51-159">Şablon açıklaması</span><span class="sxs-lookup"><span data-stu-id="26d51-159">Template description</span></span>  | <span data-ttu-id="26d51-160">Şablon adı</span><span class="sxs-lookup"><span data-stu-id="26d51-160">Template name</span></span> | <span data-ttu-id="26d51-161">Diller</span><span class="sxs-lookup"><span data-stu-id="26d51-161">Languages</span></span> |
|----------------------|---------------|-----------|
| <span data-ttu-id="26d51-162">Konsol uygulaması</span><span class="sxs-lookup"><span data-stu-id="26d51-162">Console application</span></span>  | `console`     | <span data-ttu-id="26d51-163">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="26d51-163">[C#], F#</span></span>  |
| <span data-ttu-id="26d51-164">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="26d51-164">Class library</span></span>        | `classlib`    | <span data-ttu-id="26d51-165">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="26d51-165">[C#], F#</span></span>  |
| <span data-ttu-id="26d51-166">Birim testi projesi</span><span class="sxs-lookup"><span data-stu-id="26d51-166">Unit test project</span></span>    | `mstest`      | <span data-ttu-id="26d51-167">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="26d51-167">[C#], F#</span></span>  |
| <span data-ttu-id="26d51-168">xUnit test project</span><span class="sxs-lookup"><span data-stu-id="26d51-168">xUnit test project</span></span>   | `xunit`       | <span data-ttu-id="26d51-169">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="26d51-169">[C#], F#</span></span>  |
| <span data-ttu-id="26d51-170">ASP.NET Core boş</span><span class="sxs-lookup"><span data-stu-id="26d51-170">ASP.NET Core empty</span></span>   | `web`         | <span data-ttu-id="26d51-171">[C#]</span><span class="sxs-lookup"><span data-stu-id="26d51-171">[C#]</span></span>      |
| <span data-ttu-id="26d51-172">ASP.NET Core Web uygulaması</span><span class="sxs-lookup"><span data-stu-id="26d51-172">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="26d51-173">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="26d51-173">[C#], F#</span></span>  |
| <span data-ttu-id="26d51-174">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="26d51-174">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="26d51-175">[C#]</span><span class="sxs-lookup"><span data-stu-id="26d51-175">[C#]</span></span>      |
| <span data-ttu-id="26d51-176">Nuget yapılandırma</span><span class="sxs-lookup"><span data-stu-id="26d51-176">Nuget config</span></span>         | `nugetconfig` |           |
| <span data-ttu-id="26d51-177">Web yapılandırma</span><span class="sxs-lookup"><span data-stu-id="26d51-177">Web config</span></span>           | `webconfig`   |           |
| <span data-ttu-id="26d51-178">Çözüm dosyası</span><span class="sxs-lookup"><span data-stu-id="26d51-178">Solution file</span></span>        | `sln`         |           |

---

## <a name="options"></a><span data-ttu-id="26d51-179">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="26d51-179">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="26d51-180">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="26d51-180">.NET Core 2.x</span></span>](#tab/netcore2x)

`--force`

<span data-ttu-id="26d51-181">Var olan dosyaları değişeceğinden olsa bile oluşturulacak içeriği zorlar.</span><span class="sxs-lookup"><span data-stu-id="26d51-181">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="26d51-182">Çıktı dizini bir proje zaten içeriyor, bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="26d51-182">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="26d51-183">Komut için Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="26d51-183">Prints out help for the command.</span></span> <span data-ttu-id="26d51-184">İçin çağrılabilir `dotnet new` kendisini komut veya herhangi bir şablonu gibi `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="26d51-184">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="26d51-185">Bir kaynak veya şablon paketinden yükler `PATH` veya `NUGET_ID` sağlanan.</span><span class="sxs-lookup"><span data-stu-id="26d51-185">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="26d51-186">Özel şablonlar oluşturma hakkında daha fazla bilgi için bkz: [yeni dotnet için özel şablonlar](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="26d51-186">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="26d51-187">Belirtilen ad içeren şablonlarını listeler.</span><span class="sxs-lookup"><span data-stu-id="26d51-187">Lists templates containing the specified name.</span></span> <span data-ttu-id="26d51-188">İçin başlatılırsa `dotnet new` komutu için belirtilen dizin kullanılabilir olası şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="26d51-188">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="26d51-189">Örneğin dizini zaten bir proje içeriyorsa, tüm proje şablonları listesinde değil.</span><span class="sxs-lookup"><span data-stu-id="26d51-189">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="26d51-190">Oluşturmak için şablon dili.</span><span class="sxs-lookup"><span data-stu-id="26d51-190">The language of the template to create.</span></span> <span data-ttu-id="26d51-191">Dil kabul değişir şablon tarafından (varsayılan ayarlarında bkz [bağımsız değişkenleri](#arguments) bölümü).</span><span class="sxs-lookup"><span data-stu-id="26d51-191">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="26d51-192">Bazı şablonlar için geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="26d51-192">Not valid for some templates.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="26d51-193">Oluşturulan çıktı adı.</span><span class="sxs-lookup"><span data-stu-id="26d51-193">The name for the created output.</span></span> <span data-ttu-id="26d51-194">Ad belirtilmezse, geçerli dizin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="26d51-194">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="26d51-195">Oluşturulan çıktı yerleştirileceği konum.</span><span class="sxs-lookup"><span data-stu-id="26d51-195">Location to place the generated output.</span></span> <span data-ttu-id="26d51-196">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="26d51-196">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="26d51-197">Şablonlar kullanılabilir türlerine göre filtreler.</span><span class="sxs-lookup"><span data-stu-id="26d51-197">Filters templates based on available types.</span></span> <span data-ttu-id="26d51-198">Önceden tanımlanmış değerler "proje", "öğesi" veya "diğer" olabilir.</span><span class="sxs-lookup"><span data-stu-id="26d51-198">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="26d51-199">Bir kaynak veya şablon paketini kaldırır `PATH` veya `NUGET_ID` sağlanan.</span><span class="sxs-lookup"><span data-stu-id="26d51-199">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="26d51-200">Bir şablon kullanarak kaldırmak için bir `PATH`, yolun tam olarak nitelemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="26d51-200">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="26d51-201">Örneğin, *C:/Users/\<kullanıcı > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* çalışır, ancak *./GarciaSoftware.ConsoleTemplate.CSharp* içeren gelen Klasör almayacak.</span><span class="sxs-lookup"><span data-stu-id="26d51-201">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="26d51-202">Ayrıca, şablonu yoldaki son sonlandırma dizin eğik çizgi eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="26d51-202">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="26d51-203">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="26d51-203">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="26d51-204">Belirli bir proje türü için tüm şablonları bağlamında çalışırken gösterir `dotnet new` tek başına komutu.</span><span class="sxs-lookup"><span data-stu-id="26d51-204">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="26d51-205">Belirli bir şablon bağlamda gibi çalıştırırken `dotnet new web -all`, `-all` zorla oluşturma bayrak olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="26d51-205">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="26d51-206">Çıktı dizini bir proje zaten içeriyor, bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="26d51-206">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="26d51-207">Komut için Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="26d51-207">Prints out help for the command.</span></span> <span data-ttu-id="26d51-208">İçin çağrılabilir `dotnet new` kendisini komut veya herhangi bir şablonu gibi `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="26d51-208">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="26d51-209">Belirtilen ad içeren şablonlarını listeler.</span><span class="sxs-lookup"><span data-stu-id="26d51-209">Lists templates containing the specified name.</span></span> <span data-ttu-id="26d51-210">İçin başlatılırsa `dotnet new` komutu için belirtilen dizin kullanılabilir olası şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="26d51-210">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="26d51-211">Örneğin dizini zaten bir proje içeriyorsa, tüm proje şablonları listesinde değil.</span><span class="sxs-lookup"><span data-stu-id="26d51-211">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="26d51-212">Oluşturmak için şablon dili.</span><span class="sxs-lookup"><span data-stu-id="26d51-212">The language of the template to create.</span></span> <span data-ttu-id="26d51-213">Dil kabul değişir şablon tarafından (varsayılan ayarlarında bkz [bağımsız değişkenleri](#arguments) bölümü).</span><span class="sxs-lookup"><span data-stu-id="26d51-213">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="26d51-214">Bazı şablonlar için geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="26d51-214">Not valid for some templates.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="26d51-215">Oluşturulan çıktı adı.</span><span class="sxs-lookup"><span data-stu-id="26d51-215">The name for the created output.</span></span> <span data-ttu-id="26d51-216">Ad belirtilmezse, geçerli dizin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="26d51-216">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="26d51-217">Oluşturulan çıktı yerleştirileceği konum.</span><span class="sxs-lookup"><span data-stu-id="26d51-217">Location to place the generated output.</span></span> <span data-ttu-id="26d51-218">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="26d51-218">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="26d51-219">Şablon seçenekleri</span><span class="sxs-lookup"><span data-stu-id="26d51-219">Template options</span></span>

<span data-ttu-id="26d51-220">Her proje şablonu ek seçenekleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="26d51-220">Each project template may have additional options available.</span></span> <span data-ttu-id="26d51-221">Çekirdek şablonları aşağıdaki ek seçeneklere sahip olursunuz:</span><span class="sxs-lookup"><span data-stu-id="26d51-221">The core templates have the following additional options:</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="26d51-222">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="26d51-222">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="26d51-223">**konsolunda, Açısal, tepki, reactredux**</span><span class="sxs-lookup"><span data-stu-id="26d51-223">**console, angular, react, reactredux**</span></span>

<span data-ttu-id="26d51-224">`--no-restore`-Proje oluşturma sırasında örtük bir geri yükleme yapın değil.</span><span class="sxs-lookup"><span data-stu-id="26d51-224">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="26d51-225">**classlib**</span><span class="sxs-lookup"><span data-stu-id="26d51-225">**classlib**</span></span>

<span data-ttu-id="26d51-226">`-f|--framework <FRAMEWORK>`-Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="26d51-226">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="26d51-227">Değerler: `netcoreapp2.0` .NET çekirdek sınıf kitaplığı oluşturmak için veya `netstandard2.0` .NET standart sınıf kitaplığı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="26d51-227">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="26d51-228">Varsayılan değer `netstandard2.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="26d51-228">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="26d51-229">`--no-restore`-Proje oluşturma sırasında örtük bir geri yükleme yapın değil.</span><span class="sxs-lookup"><span data-stu-id="26d51-229">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="26d51-230">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="26d51-230">**mstest, xunit**</span></span>

<span data-ttu-id="26d51-231">`-p|--enable-pack`-Proje kullanma paketleme sağlar [dotnet paketi](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="26d51-231">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="26d51-232">`--no-restore`-Proje oluşturma sırasında örtük bir geri yükleme yapın değil.</span><span class="sxs-lookup"><span data-stu-id="26d51-232">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="26d51-233">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="26d51-233">**globaljson**</span></span>

<span data-ttu-id="26d51-234">`--sdk-version <VERSION_NUMBER>`-Kullanmak için .NET Core SDK sürümünü belirtir *global.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="26d51-234">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="26d51-235">**web**</span><span class="sxs-lookup"><span data-stu-id="26d51-235">**web**</span></span>

<span data-ttu-id="26d51-236">`--use-launch-settings`-İçeren *launchSettings.json* oluşturulan şablon çıkışı.</span><span class="sxs-lookup"><span data-stu-id="26d51-236">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="26d51-237">`--no-restore`-Proje oluşturma sırasında örtük bir geri yükleme yapın değil.</span><span class="sxs-lookup"><span data-stu-id="26d51-237">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="26d51-238">**webapi**</span><span class="sxs-lookup"><span data-stu-id="26d51-238">**webapi**</span></span>

<span data-ttu-id="26d51-239">`-au|--auth <AUTHENTICATION_TYPE>`-Kullanılacak kimlik doğrulama türü.</span><span class="sxs-lookup"><span data-stu-id="26d51-239">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="26d51-240">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="26d51-240">The possible values are:</span></span>

- <span data-ttu-id="26d51-241">`None`-Kimlik doğrulama yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="26d51-241">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="26d51-242">`IndividualB2C`-Azure AD B2C ile tek tek kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="26d51-242">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="26d51-243">`SingleOrg`-Tek bir kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="26d51-243">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="26d51-244">`Windows`-Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="26d51-244">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="26d51-245">`--aad-b2c-instance <INSTANCE>`-Bağlanmak için Azure Active Directory B2C örnek.</span><span class="sxs-lookup"><span data-stu-id="26d51-245">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="26d51-246">İle kullandığınız `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="26d51-246">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="26d51-247">Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="26d51-247">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="26d51-248">`-ssp|--susi-policy-id <ID>`-Bu proje için oturum açma ve kaydolma ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="26d51-248">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="26d51-249">İle kullandığınız `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="26d51-249">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="26d51-250">`--aad-instance <INSTANCE>`-Bağlanmak için Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="26d51-250">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="26d51-251">İle kullandığınız `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="26d51-251">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="26d51-252">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="26d51-252">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="26d51-253">`--client-id <ID>`-Bu proje için istemci kimliği.</span><span class="sxs-lookup"><span data-stu-id="26d51-253">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="26d51-254">İle kullandığınız `IndividualB2C` veya `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="26d51-254">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="26d51-255">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="26d51-255">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="26d51-256">`--domain <DOMAIN>`-Etki alanı için dizin Kiracı.</span><span class="sxs-lookup"><span data-stu-id="26d51-256">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="26d51-257">İle kullandığınız `SingleOrg` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="26d51-257">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="26d51-258">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="26d51-258">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="26d51-259">`--tenant-id <ID>`-Tenantıd bağlanmak için kimliği dizini.</span><span class="sxs-lookup"><span data-stu-id="26d51-259">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="26d51-260">İle kullandığınız `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="26d51-260">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="26d51-261">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="26d51-261">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="26d51-262">`-r|--org-read-access`-Bu uygulamanın dizine okuma erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="26d51-262">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="26d51-263">Yalnızca uygular `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="26d51-263">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="26d51-264">`--use-launch-settings`-İçeren *launchSettings.json* oluşturulan şablon çıkışı.</span><span class="sxs-lookup"><span data-stu-id="26d51-264">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="26d51-265">`-uld|--use-local-db`-Yerel veritabanı yerine SQLite kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="26d51-265">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="26d51-266">Yalnızca uygular `Individual` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="26d51-266">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="26d51-267">`--no-restore`-Proje oluşturma sırasında örtük bir geri yükleme yapın değil.</span><span class="sxs-lookup"><span data-stu-id="26d51-267">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="26d51-268">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="26d51-268">**mvc, razor**</span></span>

<span data-ttu-id="26d51-269">`-au|--auth <AUTHENTICATION_TYPE>`-Kullanılacak kimlik doğrulama türü.</span><span class="sxs-lookup"><span data-stu-id="26d51-269">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="26d51-270">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="26d51-270">The possible values are:</span></span>

- <span data-ttu-id="26d51-271">`None`-Kimlik doğrulama yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="26d51-271">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="26d51-272">`Individual`-Tek tek kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="26d51-272">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="26d51-273">`IndividualB2C`-Azure AD B2C ile tek tek kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="26d51-273">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="26d51-274">`SingleOrg`-Tek bir kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="26d51-274">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="26d51-275">`MultiOrg`-Birden çok Kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="26d51-275">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="26d51-276">`Windows`-Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="26d51-276">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="26d51-277">`--aad-b2c-instance <INSTANCE>`-Bağlanmak için Azure Active Directory B2C örnek.</span><span class="sxs-lookup"><span data-stu-id="26d51-277">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="26d51-278">İle kullandığınız `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="26d51-278">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="26d51-279">Varsayılan değer `https://login.microsoftonline.com/tfp/` .</span><span class="sxs-lookup"><span data-stu-id="26d51-279">The default value is `https://login.microsoftonline.com/tfp/` .</span></span>

<span data-ttu-id="26d51-280">`-ssp|--susi-policy-id <ID>`-Bu proje için oturum açma ve kaydolma ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="26d51-280">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="26d51-281">İle kullandığınız `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="26d51-281">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="26d51-282">`-rp|--reset-password-policy-id <ID>`-Bu proje için reset parola ilkesi kimliği.</span><span class="sxs-lookup"><span data-stu-id="26d51-282">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="26d51-283">İle kullandığınız `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="26d51-283">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="26d51-284">`-ep|--edit-profile-policy-id <ID>`-Bu proje için Düzenle profili ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="26d51-284">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="26d51-285">İle kullandığınız `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="26d51-285">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="26d51-286">`--aad-instance <INSTANCE>`-Bağlanmak için Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="26d51-286">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="26d51-287">İle kullandığınız `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="26d51-287">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="26d51-288">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="26d51-288">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="26d51-289">`--client-id <ID>`-Bu proje için istemci kimliği.</span><span class="sxs-lookup"><span data-stu-id="26d51-289">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="26d51-290">İle kullandığınız `IndividualB2C`, `SingleOrg`, veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="26d51-290">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="26d51-291">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="26d51-291">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="26d51-292">`--domain <DOMAIN>`-Etki alanı için dizin Kiracı.</span><span class="sxs-lookup"><span data-stu-id="26d51-292">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="26d51-293">İle kullandığınız `SingleOrg` veya `IndividualB2C` kimlik doğrulaması...</span><span class="sxs-lookup"><span data-stu-id="26d51-293">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="26d51-294">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="26d51-294">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="26d51-295">`--tenant-id <ID>`-Tenantıd bağlanmak için kimliği dizini.</span><span class="sxs-lookup"><span data-stu-id="26d51-295">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="26d51-296">İle kullandığınız `SingleOrg` kimlik doğrulaması...</span><span class="sxs-lookup"><span data-stu-id="26d51-296">Use with `SingleOrg` authentication..</span></span> <span data-ttu-id="26d51-297">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="26d51-297">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="26d51-298">`--callback-path <PATH>`-Yeniden yönlendirme URI'si, uygulamanın taban yolu içindeki istek yolu.</span><span class="sxs-lookup"><span data-stu-id="26d51-298">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="26d51-299">İle kullandığınız `SingleOrg` veya `IndividualB2C` kimlik doğrulaması...</span><span class="sxs-lookup"><span data-stu-id="26d51-299">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="26d51-300">Varsayılan değer `/signin-oidc` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="26d51-300">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="26d51-301">`-r|--org-read-access`-Bu uygulamanın dizine okuma erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="26d51-301">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="26d51-302">Yalnızca uygular `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="26d51-302">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="26d51-303">`--use-launch-settings`-İçeren *launchSettings.json* oluşturulan şablon çıkışı.</span><span class="sxs-lookup"><span data-stu-id="26d51-303">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="26d51-304">`--use-browserlink`-BrowserLink projede içerir.</span><span class="sxs-lookup"><span data-stu-id="26d51-304">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="26d51-305">`-uld|--use-local-db`-Yerel veritabanı yerine SQLite kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="26d51-305">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="26d51-306">Yalnızca uygular `Individual` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="26d51-306">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="26d51-307">`--no-restore`-Proje oluşturma sırasında örtük bir geri yükleme yapın değil.</span><span class="sxs-lookup"><span data-stu-id="26d51-307">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="26d51-308">**Sayfa**</span><span class="sxs-lookup"><span data-stu-id="26d51-308">**page**</span></span>

<span data-ttu-id="26d51-309">`-na|--namespace <NAMESPACE_NAME>`-Namespace üretilen kod için.</span><span class="sxs-lookup"><span data-stu-id="26d51-309">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="26d51-310">Varsayılan değer `MyApp.Namespace` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="26d51-310">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="26d51-311">`-np|--no-pagemodel`-Bir PageModel olmadan sayfası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="26d51-311">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="26d51-312">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="26d51-312">**viewimports**</span></span>

<span data-ttu-id="26d51-313">`-na|--namespace <NAMESPACE_NAME>`-Namespace üretilen kod için.</span><span class="sxs-lookup"><span data-stu-id="26d51-313">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="26d51-314">Varsayılan değer `MyApp.Namespace` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="26d51-314">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="26d51-315">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="26d51-315">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="26d51-316">**Konsolu, xunit, mstest'i, web, webapı**</span><span class="sxs-lookup"><span data-stu-id="26d51-316">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="26d51-317">`-f|--framework`-Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="26d51-317">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="26d51-318">Değerler: `netcoreapp1.0` veya `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="26d51-318">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="26d51-319">Varsayılan değer `netcoreapp1.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="26d51-319">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="26d51-320">**classlib**</span><span class="sxs-lookup"><span data-stu-id="26d51-320">**classlib**</span></span>

<span data-ttu-id="26d51-321">`-f|--framework`-Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="26d51-321">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="26d51-322">Değerler: `netcoreapp1.0`, `netcoreapp1.1`, veya `netstandard1.0` için `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="26d51-322">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="26d51-323">Varsayılan değer `netstandard1.4` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="26d51-323">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="26d51-324">**mvc**</span><span class="sxs-lookup"><span data-stu-id="26d51-324">**mvc**</span></span>

<span data-ttu-id="26d51-325">`-f|--framework`-Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="26d51-325">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="26d51-326">Değerler: `netcoreapp1.0` veya `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="26d51-326">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="26d51-327">Varsayılan değer `netcoreapp1.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="26d51-327">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="26d51-328">`-au|--auth`-Kullanılacak kimlik doğrulama türü.</span><span class="sxs-lookup"><span data-stu-id="26d51-328">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="26d51-329">Değerler: `None` veya `Individual`.</span><span class="sxs-lookup"><span data-stu-id="26d51-329">Values: `None` or `Individual`.</span></span> <span data-ttu-id="26d51-330">Varsayılan değer `None` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="26d51-330">The default value is `None`.</span></span>

<span data-ttu-id="26d51-331">`-uld|--use-local-db`-Yerel veritabanı yerine SQLite kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="26d51-331">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="26d51-332">Değerler: `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="26d51-332">Values: `true` or `false`.</span></span> <span data-ttu-id="26d51-333">Varsayılan değer `false` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="26d51-333">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="26d51-334">Örnekler</span><span class="sxs-lookup"><span data-stu-id="26d51-334">Examples</span></span>

<span data-ttu-id="26d51-335">Geçerli dizinde bir F # konsol uygulama projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="26d51-335">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang f#`

<span data-ttu-id="26d51-336">(Yalnızca .NET çekirdeği 2.0 SDK veya sonraki sürümleriyle kullanılabilir) belirtilen dizindeki .NET standart bir sınıf kitaplığı projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="26d51-336">Create a .NET Standard class library project in the specified directory (available only with .NET Core 2.0 SDK or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="26d51-337">Yeni bir ASP.NET Core C# MVC uygulama projesi geçerli dizinde kimlik doğrulamasız .NET Core 2.0 hedefleme oluşturun:</span><span class="sxs-lookup"><span data-stu-id="26d51-337">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication targeting .NET Core 2.0:</span></span>

`dotnet new mvc -au None -f netcoreapp2.0`

<span data-ttu-id="26d51-338">.NET Core 2.0 hedefleme yeni bir xUnit uygulaması oluşturun:</span><span class="sxs-lookup"><span data-stu-id="26d51-338">Create a new xUnit application targeting .NET Core 2.0:</span></span>

`dotnet new xunit --framework netcoreapp2.0`

<span data-ttu-id="26d51-339">MVC için kullanılabilir tüm şablonları listeler:</span><span class="sxs-lookup"><span data-stu-id="26d51-339">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

## <a name="see-also"></a><span data-ttu-id="26d51-340">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="26d51-340">See also</span></span>

[<span data-ttu-id="26d51-341">Yeni dotnet için özel şablonlar</span><span class="sxs-lookup"><span data-stu-id="26d51-341">Custom templates for dotnet new</span></span>](custom-templates.md)  
[<span data-ttu-id="26d51-342">Dotnet new için özel şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="26d51-342">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)  
[<span data-ttu-id="26d51-343">DotNet/dotnet-şablonu-samples GitHub depo</span><span class="sxs-lookup"><span data-stu-id="26d51-343">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)  
[<span data-ttu-id="26d51-344">Yeni dotnet için kullanılabilir şablonlar</span><span class="sxs-lookup"><span data-stu-id="26d51-344">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
