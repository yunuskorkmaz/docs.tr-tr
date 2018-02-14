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
ms.workload:
- dotnetcore
ms.openlocfilehash: ea94c875ae6fe82d0e5d35ba8ca3fd47971fbbe6
ms.sourcegitcommit: e2bf8e6bc365bd9a0e86fe81eeae7d14f85f48c1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/13/2018
---
# <a name="dotnet-new"></a><span data-ttu-id="89509-104">DotNet yeni</span><span class="sxs-lookup"><span data-stu-id="89509-104">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="89509-105">Ad</span><span class="sxs-lookup"><span data-stu-id="89509-105">Name</span></span>

<span data-ttu-id="89509-106">`dotnet new` -Yeni Proje, yapılandırma dosyası veya belirtilen şablona dayalı çözüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="89509-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="89509-107">Özet</span><span class="sxs-lookup"><span data-stu-id="89509-107">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="89509-108">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="89509-108">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="89509-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="89509-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="89509-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="89509-110">Description</span></span>

<span data-ttu-id="89509-111">`dotnet new` Komutu geçerli bir .NET Core projeyi başlatmak için kolay bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="89509-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span> 

<span data-ttu-id="89509-112">Komut çağrıları [şablon motoru](https://github.com/dotnet/templating) yapıları belirtilen şablonu ve seçenekleri bağlı disk oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="89509-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="89509-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="89509-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="89509-114">Komutu çağrıldığında örneği oluşturmak için şablon.</span><span class="sxs-lookup"><span data-stu-id="89509-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="89509-115">Her bir şablon geçirebilirsiniz belirli seçenekleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="89509-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="89509-116">Daha fazla bilgi için bkz: [şablon seçenekleri](#template-options).</span><span class="sxs-lookup"><span data-stu-id="89509-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="89509-117">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="89509-117">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="89509-118">Komut şablonlarının varsayılan listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="89509-118">The command contains a default list of templates.</span></span> <span data-ttu-id="89509-119">Kullanım `dotnet new -l` kullanılabilir şablonların listesini elde edilir.</span><span class="sxs-lookup"><span data-stu-id="89509-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="89509-120">Aşağıdaki tabloda .NET Core 2.0 SDK ile birlikte önceden yüklenmiş olarak gelen şablonları gösterir.</span><span class="sxs-lookup"><span data-stu-id="89509-120">The following table shows the templates that come pre-installed with the .NET Core 2.0 SDK.</span></span> <span data-ttu-id="89509-121">Şablon için varsayılan dili köşeli ayraçlar içinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="89509-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="89509-122">Şablon açıklaması</span><span class="sxs-lookup"><span data-stu-id="89509-122">Template description</span></span>                          | <span data-ttu-id="89509-123">Şablon adı</span><span class="sxs-lookup"><span data-stu-id="89509-123">Template name</span></span> | <span data-ttu-id="89509-124">Diller</span><span class="sxs-lookup"><span data-stu-id="89509-124">Languages</span></span>     |
|----------------------------------------------|---------------|---------------|
| <span data-ttu-id="89509-125">Konsol uygulaması</span><span class="sxs-lookup"><span data-stu-id="89509-125">Console application</span></span>                          | `console`     | <span data-ttu-id="89509-126">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="89509-126">[C#], F#, VB</span></span>  |
| <span data-ttu-id="89509-127">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="89509-127">Class library</span></span>                                | `classlib`    | <span data-ttu-id="89509-128">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="89509-128">[C#], F#, VB</span></span>  |
| <span data-ttu-id="89509-129">Birim testi projesi</span><span class="sxs-lookup"><span data-stu-id="89509-129">Unit test project</span></span>                            | `mstest`      | <span data-ttu-id="89509-130">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="89509-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="89509-131">xUnit test project</span><span class="sxs-lookup"><span data-stu-id="89509-131">xUnit test project</span></span>                           | `xunit`       | <span data-ttu-id="89509-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="89509-132">[C#], F#, VB</span></span>  |
| <span data-ttu-id="89509-133">ASP.NET Core boş</span><span class="sxs-lookup"><span data-stu-id="89509-133">ASP.NET Core empty</span></span>                           | `web`         | <span data-ttu-id="89509-134">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="89509-134">[C#], F#</span></span>      |
| <span data-ttu-id="89509-135">ASP.NET Core Web uygulaması (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="89509-135">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="89509-136">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="89509-136">[C#], F#</span></span>      |
| <span data-ttu-id="89509-137">ASP.NET Core Web uygulaması</span><span class="sxs-lookup"><span data-stu-id="89509-137">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="89509-138">[C#]</span><span class="sxs-lookup"><span data-stu-id="89509-138">[C#]</span></span>          |
| <span data-ttu-id="89509-139">ASP.NET Core Açısal ile</span><span class="sxs-lookup"><span data-stu-id="89509-139">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="89509-140">[C#]</span><span class="sxs-lookup"><span data-stu-id="89509-140">[C#]</span></span>          |
| <span data-ttu-id="89509-141">ASP.NET Core React.js ile</span><span class="sxs-lookup"><span data-stu-id="89509-141">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="89509-142">[C#]</span><span class="sxs-lookup"><span data-stu-id="89509-142">[C#]</span></span>          |
| <span data-ttu-id="89509-143">ASP.NET Core React.js ve Redux</span><span class="sxs-lookup"><span data-stu-id="89509-143">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="89509-144">[C#]</span><span class="sxs-lookup"><span data-stu-id="89509-144">[C#]</span></span>          |
| <span data-ttu-id="89509-145">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="89509-145">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="89509-146">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="89509-146">[C#], F#</span></span>      |
| <span data-ttu-id="89509-147">global.json file</span><span class="sxs-lookup"><span data-stu-id="89509-147">global.json file</span></span>                             | `globaljson`  |               |
| <span data-ttu-id="89509-148">Nuget yapılandırma</span><span class="sxs-lookup"><span data-stu-id="89509-148">Nuget config</span></span>                                 | `nugetconfig` |               |
| <span data-ttu-id="89509-149">Web yapılandırma</span><span class="sxs-lookup"><span data-stu-id="89509-149">Web config</span></span>                                   | `webconfig`   |               |
| <span data-ttu-id="89509-150">Çözüm dosyası</span><span class="sxs-lookup"><span data-stu-id="89509-150">Solution file</span></span>                                | `sln`         |               |
| <span data-ttu-id="89509-151">Razor sayfası</span><span class="sxs-lookup"><span data-stu-id="89509-151">Razor page</span></span>                                   | `page`        |               |
| <span data-ttu-id="89509-152">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="89509-152">MVC ViewImports</span></span>                              | `viewimports` |               |
| <span data-ttu-id="89509-153">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="89509-153">MVC ViewStart</span></span>                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="89509-154">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="89509-154">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="89509-155">Komut şablonlarının varsayılan listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="89509-155">The command contains a default list of templates.</span></span> <span data-ttu-id="89509-156">Kullanım `dotnet new -all` kullanılabilir şablonların listesini elde edilir.</span><span class="sxs-lookup"><span data-stu-id="89509-156">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="89509-157">.NET Core ile önceden yüklenmiş olarak gelen şablonları aşağıdaki tabloda gösterilmektedir 1.x SDK.</span><span class="sxs-lookup"><span data-stu-id="89509-157">The following table shows the templates that come pre-installed with the .NET Core 1.x SDK.</span></span> <span data-ttu-id="89509-158">Şablon için varsayılan dili köşeli ayraçlar içinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="89509-158">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="89509-159">Şablon açıklaması</span><span class="sxs-lookup"><span data-stu-id="89509-159">Template description</span></span>  | <span data-ttu-id="89509-160">Şablon adı</span><span class="sxs-lookup"><span data-stu-id="89509-160">Template name</span></span> | <span data-ttu-id="89509-161">Diller</span><span class="sxs-lookup"><span data-stu-id="89509-161">Languages</span></span> |
|----------------------|---------------|-----------|
| <span data-ttu-id="89509-162">Konsol uygulaması</span><span class="sxs-lookup"><span data-stu-id="89509-162">Console application</span></span>  | `console`     | <span data-ttu-id="89509-163">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="89509-163">[C#], F#</span></span>  |
| <span data-ttu-id="89509-164">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="89509-164">Class library</span></span>        | `classlib`    | <span data-ttu-id="89509-165">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="89509-165">[C#], F#</span></span>  |
| <span data-ttu-id="89509-166">Birim testi projesi</span><span class="sxs-lookup"><span data-stu-id="89509-166">Unit test project</span></span>    | `mstest`      | <span data-ttu-id="89509-167">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="89509-167">[C#], F#</span></span>  |
| <span data-ttu-id="89509-168">xUnit test project</span><span class="sxs-lookup"><span data-stu-id="89509-168">xUnit test project</span></span>   | `xunit`       | <span data-ttu-id="89509-169">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="89509-169">[C#], F#</span></span>  |
| <span data-ttu-id="89509-170">ASP.NET Core boş</span><span class="sxs-lookup"><span data-stu-id="89509-170">ASP.NET Core empty</span></span>   | `web`         | <span data-ttu-id="89509-171">[C#]</span><span class="sxs-lookup"><span data-stu-id="89509-171">[C#]</span></span>      |
| <span data-ttu-id="89509-172">ASP.NET Core Web uygulaması</span><span class="sxs-lookup"><span data-stu-id="89509-172">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="89509-173">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="89509-173">[C#], F#</span></span>  |
| <span data-ttu-id="89509-174">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="89509-174">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="89509-175">[C#]</span><span class="sxs-lookup"><span data-stu-id="89509-175">[C#]</span></span>      |
| <span data-ttu-id="89509-176">Nuget yapılandırma</span><span class="sxs-lookup"><span data-stu-id="89509-176">Nuget config</span></span>         | `nugetconfig` |           |
| <span data-ttu-id="89509-177">Web yapılandırma</span><span class="sxs-lookup"><span data-stu-id="89509-177">Web config</span></span>           | `webconfig`   |           |
| <span data-ttu-id="89509-178">Çözüm dosyası</span><span class="sxs-lookup"><span data-stu-id="89509-178">Solution file</span></span>        | `sln`         |           |

---

## <a name="options"></a><span data-ttu-id="89509-179">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="89509-179">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="89509-180">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="89509-180">.NET Core 2.x</span></span>](#tab/netcore2x)

`--force`

<span data-ttu-id="89509-181">Var olan dosyaları değişeceğinden olsa bile oluşturulacak içeriği zorlar.</span><span class="sxs-lookup"><span data-stu-id="89509-181">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="89509-182">Çıktı dizini bir proje zaten içeriyor, bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="89509-182">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="89509-183">Komut için Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="89509-183">Prints out help for the command.</span></span> <span data-ttu-id="89509-184">İçin çağrılabilir `dotnet new` kendisini komut veya herhangi bir şablonu gibi `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="89509-184">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="89509-185">Bir kaynak veya şablon paketinden yükler `PATH` veya `NUGET_ID` sağlanan.</span><span class="sxs-lookup"><span data-stu-id="89509-185">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="89509-186">Özel şablonlar oluşturma hakkında daha fazla bilgi için bkz: [yeni dotnet için özel şablonlar](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="89509-186">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="89509-187">Belirtilen ad içeren şablonlarını listeler.</span><span class="sxs-lookup"><span data-stu-id="89509-187">Lists templates containing the specified name.</span></span> <span data-ttu-id="89509-188">İçin başlatılırsa `dotnet new` komutu için belirtilen dizin kullanılabilir olası şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="89509-188">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="89509-189">Örneğin dizini zaten bir proje içeriyorsa, tüm proje şablonları listesinde değil.</span><span class="sxs-lookup"><span data-stu-id="89509-189">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="89509-190">Oluşturmak için şablon dili.</span><span class="sxs-lookup"><span data-stu-id="89509-190">The language of the template to create.</span></span> <span data-ttu-id="89509-191">Dil kabul değişir şablon tarafından (varsayılan ayarlarında bkz [bağımsız değişkenleri](#arguments) bölümü).</span><span class="sxs-lookup"><span data-stu-id="89509-191">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="89509-192">Bazı şablonlar için geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="89509-192">Not valid for some templates.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="89509-193">Oluşturulan çıktı adı.</span><span class="sxs-lookup"><span data-stu-id="89509-193">The name for the created output.</span></span> <span data-ttu-id="89509-194">Ad belirtilmezse, geçerli dizin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="89509-194">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="89509-195">Oluşturulan çıktı yerleştirileceği konum.</span><span class="sxs-lookup"><span data-stu-id="89509-195">Location to place the generated output.</span></span> <span data-ttu-id="89509-196">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="89509-196">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="89509-197">Şablonlar kullanılabilir türlerine göre filtreler.</span><span class="sxs-lookup"><span data-stu-id="89509-197">Filters templates based on available types.</span></span> <span data-ttu-id="89509-198">Önceden tanımlanmış değerler "proje", "öğesi" veya "diğer" olabilir.</span><span class="sxs-lookup"><span data-stu-id="89509-198">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="89509-199">Bir kaynak veya şablon paketini kaldırır `PATH` veya `NUGET_ID` sağlanan.</span><span class="sxs-lookup"><span data-stu-id="89509-199">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="89509-200">Bir şablon kullanarak kaldırmak için bir `PATH`, yolun tam olarak nitelemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="89509-200">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="89509-201">Örneğin, *C:/Users/\<kullanıcı > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* çalışır, ancak *./GarciaSoftware.ConsoleTemplate.CSharp* içeren gelen Klasör almayacak.</span><span class="sxs-lookup"><span data-stu-id="89509-201">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="89509-202">Ayrıca, şablonu yoldaki son sonlandırma dizin eğik çizgi eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="89509-202">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="89509-203">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="89509-203">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="89509-204">Belirli bir proje türü için tüm şablonları bağlamında çalışırken gösterir `dotnet new` tek başına komutu.</span><span class="sxs-lookup"><span data-stu-id="89509-204">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="89509-205">Belirli bir şablon bağlamda gibi çalıştırırken `dotnet new web -all`, `-all` zorla oluşturma bayrak olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="89509-205">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="89509-206">Çıktı dizini bir proje zaten içeriyor, bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="89509-206">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="89509-207">Komut için Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="89509-207">Prints out help for the command.</span></span> <span data-ttu-id="89509-208">İçin çağrılabilir `dotnet new` kendisini komut veya herhangi bir şablonu gibi `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="89509-208">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="89509-209">Belirtilen ad içeren şablonlarını listeler.</span><span class="sxs-lookup"><span data-stu-id="89509-209">Lists templates containing the specified name.</span></span> <span data-ttu-id="89509-210">İçin başlatılırsa `dotnet new` komutu için belirtilen dizin kullanılabilir olası şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="89509-210">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="89509-211">Örneğin dizini zaten bir proje içeriyorsa, tüm proje şablonları listesinde değil.</span><span class="sxs-lookup"><span data-stu-id="89509-211">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="89509-212">Oluşturmak için şablon dili.</span><span class="sxs-lookup"><span data-stu-id="89509-212">The language of the template to create.</span></span> <span data-ttu-id="89509-213">Dil kabul değişir şablon tarafından (varsayılan ayarlarında bkz [bağımsız değişkenleri](#arguments) bölümü).</span><span class="sxs-lookup"><span data-stu-id="89509-213">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="89509-214">Bazı şablonlar için geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="89509-214">Not valid for some templates.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="89509-215">Oluşturulan çıktı adı.</span><span class="sxs-lookup"><span data-stu-id="89509-215">The name for the created output.</span></span> <span data-ttu-id="89509-216">Ad belirtilmezse, geçerli dizin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="89509-216">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="89509-217">Oluşturulan çıktı yerleştirileceği konum.</span><span class="sxs-lookup"><span data-stu-id="89509-217">Location to place the generated output.</span></span> <span data-ttu-id="89509-218">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="89509-218">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="89509-219">Şablon seçenekleri</span><span class="sxs-lookup"><span data-stu-id="89509-219">Template options</span></span>

<span data-ttu-id="89509-220">Her proje şablonu ek seçenekleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="89509-220">Each project template may have additional options available.</span></span> <span data-ttu-id="89509-221">Çekirdek şablonları aşağıdaki ek seçeneklere sahip olursunuz:</span><span class="sxs-lookup"><span data-stu-id="89509-221">The core templates have the following additional options:</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="89509-222">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="89509-222">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="89509-223">**konsolunda, Açısal, tepki, reactredux**</span><span class="sxs-lookup"><span data-stu-id="89509-223">**console, angular, react, reactredux**</span></span>

<span data-ttu-id="89509-224">`--no-restore` -Proje oluşturma sırasında örtük bir geri yükleme yapın değil.</span><span class="sxs-lookup"><span data-stu-id="89509-224">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="89509-225">**classlib**</span><span class="sxs-lookup"><span data-stu-id="89509-225">**classlib**</span></span>

<span data-ttu-id="89509-226">`-f|--framework <FRAMEWORK>` -Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="89509-226">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="89509-227">Değerler: `netcoreapp2.0` .NET çekirdek sınıf kitaplığı oluşturmak için veya `netstandard2.0` .NET standart sınıf kitaplığı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="89509-227">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="89509-228">Varsayılan değer `netstandard2.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="89509-228">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="89509-229">`--no-restore` -Proje oluşturma sırasında örtük bir geri yükleme yapın değil.</span><span class="sxs-lookup"><span data-stu-id="89509-229">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="89509-230">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="89509-230">**mstest, xunit**</span></span>

<span data-ttu-id="89509-231">`-p|--enable-pack` -Proje kullanma paketleme sağlar [dotnet paketi](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="89509-231">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="89509-232">`--no-restore` -Proje oluşturma sırasında örtük bir geri yükleme yapın değil.</span><span class="sxs-lookup"><span data-stu-id="89509-232">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="89509-233">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="89509-233">**globaljson**</span></span>

<span data-ttu-id="89509-234">`--sdk-version <VERSION_NUMBER>` -Kullanmak için .NET Core SDK sürümünü belirtir *global.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="89509-234">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="89509-235">**web**</span><span class="sxs-lookup"><span data-stu-id="89509-235">**web**</span></span>

<span data-ttu-id="89509-236">`--use-launch-settings` -İçeren *launchSettings.json* oluşturulan şablon çıkışı.</span><span class="sxs-lookup"><span data-stu-id="89509-236">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="89509-237">`--no-restore` -Proje oluşturma sırasında örtük bir geri yükleme yapın değil.</span><span class="sxs-lookup"><span data-stu-id="89509-237">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="89509-238">**webapi**</span><span class="sxs-lookup"><span data-stu-id="89509-238">**webapi**</span></span>

<span data-ttu-id="89509-239">`-au|--auth <AUTHENTICATION_TYPE>` -Kullanılacak kimlik doğrulama türü.</span><span class="sxs-lookup"><span data-stu-id="89509-239">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="89509-240">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="89509-240">The possible values are:</span></span>

- <span data-ttu-id="89509-241">`None` -Kimlik doğrulama yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="89509-241">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="89509-242">`IndividualB2C` -Azure AD B2C ile tek tek kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="89509-242">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="89509-243">`SingleOrg` -Tek bir kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="89509-243">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="89509-244">`Windows` -Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="89509-244">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="89509-245">`--aad-b2c-instance <INSTANCE>` -Bağlanmak için Azure Active Directory B2C örnek.</span><span class="sxs-lookup"><span data-stu-id="89509-245">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="89509-246">İle kullandığınız `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="89509-246">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="89509-247">Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="89509-247">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="89509-248">`-ssp|--susi-policy-id <ID>` -Bu proje için oturum açma ve kaydolma ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="89509-248">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="89509-249">İle kullandığınız `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="89509-249">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="89509-250">`--aad-instance <INSTANCE>` -Bağlanmak için Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="89509-250">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="89509-251">İle kullandığınız `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="89509-251">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="89509-252">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="89509-252">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="89509-253">`--client-id <ID>` -Bu proje için istemci kimliği.</span><span class="sxs-lookup"><span data-stu-id="89509-253">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="89509-254">İle kullandığınız `IndividualB2C` veya `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="89509-254">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="89509-255">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="89509-255">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="89509-256">`--domain <DOMAIN>` -Etki alanı için dizin Kiracı.</span><span class="sxs-lookup"><span data-stu-id="89509-256">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="89509-257">İle kullandığınız `SingleOrg` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="89509-257">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="89509-258">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="89509-258">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="89509-259">`--tenant-id <ID>` -Tenantıd bağlanmak için kimliği dizini.</span><span class="sxs-lookup"><span data-stu-id="89509-259">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="89509-260">İle kullandığınız `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="89509-260">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="89509-261">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="89509-261">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="89509-262">`-r|--org-read-access` -Bu uygulamanın dizine okuma erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="89509-262">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="89509-263">Yalnızca uygular `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="89509-263">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="89509-264">`--use-launch-settings` -İçeren *launchSettings.json* oluşturulan şablon çıkışı.</span><span class="sxs-lookup"><span data-stu-id="89509-264">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="89509-265">`-uld|--use-local-db` -Yerel veritabanı yerine SQLite kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="89509-265">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="89509-266">Yalnızca uygular `Individual` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="89509-266">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="89509-267">`--no-restore` -Proje oluşturma sırasında örtük bir geri yükleme yapın değil.</span><span class="sxs-lookup"><span data-stu-id="89509-267">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="89509-268">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="89509-268">**mvc, razor**</span></span>

<span data-ttu-id="89509-269">`-au|--auth <AUTHENTICATION_TYPE>` -Kullanılacak kimlik doğrulama türü.</span><span class="sxs-lookup"><span data-stu-id="89509-269">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="89509-270">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="89509-270">The possible values are:</span></span>

- <span data-ttu-id="89509-271">`None` -Kimlik doğrulama yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="89509-271">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="89509-272">`Individual` -Tek tek kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="89509-272">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="89509-273">`IndividualB2C` -Azure AD B2C ile tek tek kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="89509-273">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="89509-274">`SingleOrg` -Tek bir kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="89509-274">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="89509-275">`MultiOrg` -Birden çok Kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="89509-275">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="89509-276">`Windows` -Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="89509-276">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="89509-277">`--aad-b2c-instance <INSTANCE>` -Bağlanmak için Azure Active Directory B2C örnek.</span><span class="sxs-lookup"><span data-stu-id="89509-277">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="89509-278">İle kullandığınız `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="89509-278">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="89509-279">Varsayılan değer `https://login.microsoftonline.com/tfp/` .</span><span class="sxs-lookup"><span data-stu-id="89509-279">The default value is `https://login.microsoftonline.com/tfp/` .</span></span>

<span data-ttu-id="89509-280">`-ssp|--susi-policy-id <ID>` -Bu proje için oturum açma ve kaydolma ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="89509-280">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="89509-281">İle kullandığınız `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="89509-281">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="89509-282">`-rp|--reset-password-policy-id <ID>` -Bu proje için reset parola ilkesi kimliği.</span><span class="sxs-lookup"><span data-stu-id="89509-282">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="89509-283">İle kullandığınız `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="89509-283">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="89509-284">`-ep|--edit-profile-policy-id <ID>` -Bu proje için Düzenle profili ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="89509-284">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="89509-285">İle kullandığınız `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="89509-285">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="89509-286">`--aad-instance <INSTANCE>` -Bağlanmak için Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="89509-286">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="89509-287">İle kullandığınız `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="89509-287">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="89509-288">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="89509-288">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="89509-289">`--client-id <ID>` -Bu proje için istemci kimliği.</span><span class="sxs-lookup"><span data-stu-id="89509-289">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="89509-290">İle kullandığınız `IndividualB2C`, `SingleOrg`, veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="89509-290">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="89509-291">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="89509-291">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="89509-292">`--domain <DOMAIN>` -Etki alanı için dizin Kiracı.</span><span class="sxs-lookup"><span data-stu-id="89509-292">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="89509-293">İle kullandığınız `SingleOrg` veya `IndividualB2C` kimlik doğrulaması...</span><span class="sxs-lookup"><span data-stu-id="89509-293">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="89509-294">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="89509-294">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="89509-295">`--tenant-id <ID>` -Tenantıd bağlanmak için kimliği dizini.</span><span class="sxs-lookup"><span data-stu-id="89509-295">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="89509-296">İle kullandığınız `SingleOrg` kimlik doğrulaması...</span><span class="sxs-lookup"><span data-stu-id="89509-296">Use with `SingleOrg` authentication..</span></span> <span data-ttu-id="89509-297">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="89509-297">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="89509-298">`--callback-path <PATH>` -Yeniden yönlendirme URI'si, uygulamanın taban yolu içindeki istek yolu.</span><span class="sxs-lookup"><span data-stu-id="89509-298">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="89509-299">İle kullandığınız `SingleOrg` veya `IndividualB2C` kimlik doğrulaması...</span><span class="sxs-lookup"><span data-stu-id="89509-299">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="89509-300">Varsayılan değer `/signin-oidc` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="89509-300">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="89509-301">`-r|--org-read-access` -Bu uygulamanın dizine okuma erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="89509-301">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="89509-302">Yalnızca uygular `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="89509-302">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="89509-303">`--use-launch-settings` -İçeren *launchSettings.json* oluşturulan şablon çıkışı.</span><span class="sxs-lookup"><span data-stu-id="89509-303">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="89509-304">`--use-browserlink` -BrowserLink projede içerir.</span><span class="sxs-lookup"><span data-stu-id="89509-304">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="89509-305">`-uld|--use-local-db` -Yerel veritabanı yerine SQLite kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="89509-305">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="89509-306">Yalnızca uygular `Individual` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="89509-306">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="89509-307">`--no-restore` -Proje oluşturma sırasında örtük bir geri yükleme yapın değil.</span><span class="sxs-lookup"><span data-stu-id="89509-307">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="89509-308">**Sayfa**</span><span class="sxs-lookup"><span data-stu-id="89509-308">**page**</span></span>

<span data-ttu-id="89509-309">`-na|--namespace <NAMESPACE_NAME>`-Namespace üretilen kod için.</span><span class="sxs-lookup"><span data-stu-id="89509-309">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="89509-310">Varsayılan değer `MyApp.Namespace` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="89509-310">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="89509-311">`-np|--no-pagemodel` -Bir PageModel olmadan sayfası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="89509-311">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="89509-312">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="89509-312">**viewimports**</span></span>

<span data-ttu-id="89509-313">`-na|--namespace <NAMESPACE_NAME>`-Namespace üretilen kod için.</span><span class="sxs-lookup"><span data-stu-id="89509-313">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="89509-314">Varsayılan değer `MyApp.Namespace` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="89509-314">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="89509-315">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="89509-315">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="89509-316">**Konsolu, xunit, mstest'i, web, webapı**</span><span class="sxs-lookup"><span data-stu-id="89509-316">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="89509-317">`-f|--framework` -Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="89509-317">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="89509-318">Değerler: `netcoreapp1.0` veya `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="89509-318">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="89509-319">Varsayılan değer `netcoreapp1.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="89509-319">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="89509-320">**classlib**</span><span class="sxs-lookup"><span data-stu-id="89509-320">**classlib**</span></span>

<span data-ttu-id="89509-321">`-f|--framework` -Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="89509-321">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="89509-322">Değerler: `netcoreapp1.0`, `netcoreapp1.1`, veya `netstandard1.0` için `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="89509-322">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="89509-323">Varsayılan değer `netstandard1.4` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="89509-323">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="89509-324">**mvc**</span><span class="sxs-lookup"><span data-stu-id="89509-324">**mvc**</span></span>

<span data-ttu-id="89509-325">`-f|--framework` -Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="89509-325">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="89509-326">Değerler: `netcoreapp1.0` veya `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="89509-326">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="89509-327">Varsayılan değer `netcoreapp1.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="89509-327">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="89509-328">`-au|--auth` -Kullanılacak kimlik doğrulama türü.</span><span class="sxs-lookup"><span data-stu-id="89509-328">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="89509-329">Değerler: `None` veya `Individual`.</span><span class="sxs-lookup"><span data-stu-id="89509-329">Values: `None` or `Individual`.</span></span> <span data-ttu-id="89509-330">Varsayılan değer `None` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="89509-330">The default value is `None`.</span></span>

<span data-ttu-id="89509-331">`-uld|--use-local-db` -Yerel veritabanı yerine SQLite kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="89509-331">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="89509-332">Değerler: `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="89509-332">Values: `true` or `false`.</span></span> <span data-ttu-id="89509-333">Varsayılan değer `false` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="89509-333">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="89509-334">Örnekler</span><span class="sxs-lookup"><span data-stu-id="89509-334">Examples</span></span>

<span data-ttu-id="89509-335">Geçerli dizinde bir F # konsol uygulama projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="89509-335">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang f#`

<span data-ttu-id="89509-336">(Yalnızca .NET çekirdeği 2.0 SDK veya sonraki sürümleriyle kullanılabilir) belirtilen dizindeki .NET standart bir sınıf kitaplığı projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="89509-336">Create a .NET Standard class library project in the specified directory (available only with .NET Core 2.0 SDK or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="89509-337">Yeni bir ASP.NET Core C# MVC uygulama projesi geçerli dizinde kimlik doğrulamasız .NET Core 2.0 hedefleme oluşturun:</span><span class="sxs-lookup"><span data-stu-id="89509-337">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication targeting .NET Core 2.0:</span></span>

`dotnet new mvc -au None -f netcoreapp2.0`

<span data-ttu-id="89509-338">.NET Core 2.0 hedefleme yeni bir xUnit uygulaması oluşturun:</span><span class="sxs-lookup"><span data-stu-id="89509-338">Create a new xUnit application targeting .NET Core 2.0:</span></span>

`dotnet new xunit --framework netcoreapp2.0`

<span data-ttu-id="89509-339">MVC için kullanılabilir tüm şablonları listeler:</span><span class="sxs-lookup"><span data-stu-id="89509-339">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

## <a name="see-also"></a><span data-ttu-id="89509-340">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="89509-340">See also</span></span>

[<span data-ttu-id="89509-341">Yeni dotnet için özel şablonlar</span><span class="sxs-lookup"><span data-stu-id="89509-341">Custom templates for dotnet new</span></span>](custom-templates.md)  
[<span data-ttu-id="89509-342">Dotnet new için özel şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="89509-342">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)  
[<span data-ttu-id="89509-343">DotNet/dotnet-şablonu-samples GitHub depo</span><span class="sxs-lookup"><span data-stu-id="89509-343">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)  
[<span data-ttu-id="89509-344">Yeni dotnet için kullanılabilir şablonlar</span><span class="sxs-lookup"><span data-stu-id="89509-344">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
