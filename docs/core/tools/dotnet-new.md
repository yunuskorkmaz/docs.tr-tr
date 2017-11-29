---
title: DotNet yeni komutu - .NET Core CLI
description: "Dotnet yeni komut belirtilen şablona dayalı yeni .NET Core projelerini oluşturur."
keywords: DotNet yeni, CLI, CLI komutu, .NET Core
author: mairaw
ms.author: mairaw
ms.date: 08/13/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: fcc3ed2e-9265-4d50-b59e-dc2e5c190b34
ms.openlocfilehash: d64881380febee08414f57a36ed92079e8d69ed6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-new"></a><span data-ttu-id="ed1e2-104">DotNet yeni</span><span class="sxs-lookup"><span data-stu-id="ed1e2-104">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="ed1e2-105">Ad</span><span class="sxs-lookup"><span data-stu-id="ed1e2-105">Name</span></span>

<span data-ttu-id="ed1e2-106">`dotnet new`-Yeni Proje, yapılandırma dosyası veya belirtilen şablona dayalı çözüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="ed1e2-107">Özet</span><span class="sxs-lookup"><span data-stu-id="ed1e2-107">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="ed1e2-108">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="ed1e2-108">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="ed1e2-109">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="ed1e2-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="ed1e2-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ed1e2-110">Description</span></span>

<span data-ttu-id="ed1e2-111">`dotnet new` Komutu geçerli bir .NET Core projeyi başlatmak için kolay bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span> 

<span data-ttu-id="ed1e2-112">Komut çağrıları [şablon motoru](https://github.com/dotnet/templating) yapıları belirtilen şablonu ve seçenekleri bağlı disk oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="ed1e2-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="ed1e2-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="ed1e2-114">Komutu çağrıldığında örneği oluşturmak için şablon.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="ed1e2-115">Her bir şablon geçirebilirsiniz belirli seçenekleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="ed1e2-116">Daha fazla bilgi için bkz: [şablon seçenekleri](#template-options).</span><span class="sxs-lookup"><span data-stu-id="ed1e2-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="ed1e2-117">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="ed1e2-117">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="ed1e2-118">Komut şablonlarının varsayılan listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-118">The command contains a default list of templates.</span></span> <span data-ttu-id="ed1e2-119">Kullanım `dotnet new -l` kullanılabilir şablonların listesini elde edilir.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="ed1e2-120">Aşağıdaki tabloda .NET Core 2.0 SDK ile birlikte önceden yüklenmiş olarak gelen şablonları gösterir.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-120">The following table shows the templates that come pre-installed with the .NET Core 2.0 SDK.</span></span> <span data-ttu-id="ed1e2-121">Şablon için varsayılan dili köşeli ayraçlar içinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="ed1e2-122">Şablon açıklaması</span><span class="sxs-lookup"><span data-stu-id="ed1e2-122">Template description</span></span>                          | <span data-ttu-id="ed1e2-123">Şablon adı</span><span class="sxs-lookup"><span data-stu-id="ed1e2-123">Template name</span></span>  | <span data-ttu-id="ed1e2-124">Diller</span><span class="sxs-lookup"><span data-stu-id="ed1e2-124">Languages</span></span>     |
|----------------------------------------------|----------------|---------------|
| <span data-ttu-id="ed1e2-125">Konsol uygulaması</span><span class="sxs-lookup"><span data-stu-id="ed1e2-125">Console application</span></span>                          | <span data-ttu-id="ed1e2-126">konsolu</span><span class="sxs-lookup"><span data-stu-id="ed1e2-126">console</span></span>        | <span data-ttu-id="ed1e2-127">[C#] F #, VB</span><span class="sxs-lookup"><span data-stu-id="ed1e2-127">[C#], F#, VB</span></span>  |
| <span data-ttu-id="ed1e2-128">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="ed1e2-128">Class library</span></span>                                | <span data-ttu-id="ed1e2-129">ClassLib</span><span class="sxs-lookup"><span data-stu-id="ed1e2-129">classlib</span></span>       | <span data-ttu-id="ed1e2-130">[C#] F #, VB</span><span class="sxs-lookup"><span data-stu-id="ed1e2-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="ed1e2-131">Birim testi projesi</span><span class="sxs-lookup"><span data-stu-id="ed1e2-131">Unit test project</span></span>                            | <span data-ttu-id="ed1e2-132">mstest'i</span><span class="sxs-lookup"><span data-stu-id="ed1e2-132">mstest</span></span>         | <span data-ttu-id="ed1e2-133">[C#] F #, VB</span><span class="sxs-lookup"><span data-stu-id="ed1e2-133">[C#], F#, VB</span></span>  |
| <span data-ttu-id="ed1e2-134">xUnit test projesi</span><span class="sxs-lookup"><span data-stu-id="ed1e2-134">xUnit test project</span></span>                           | <span data-ttu-id="ed1e2-135">xunit</span><span class="sxs-lookup"><span data-stu-id="ed1e2-135">xunit</span></span>          | <span data-ttu-id="ed1e2-136">[C#] F #, VB</span><span class="sxs-lookup"><span data-stu-id="ed1e2-136">[C#], F#, VB</span></span>  |
| <span data-ttu-id="ed1e2-137">ASP.NET Core boş</span><span class="sxs-lookup"><span data-stu-id="ed1e2-137">ASP.NET Core empty</span></span>                           | <span data-ttu-id="ed1e2-138">Web</span><span class="sxs-lookup"><span data-stu-id="ed1e2-138">web</span></span>            | <span data-ttu-id="ed1e2-139">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="ed1e2-139">[C#], F#</span></span>      |
| <span data-ttu-id="ed1e2-140">ASP.NET Core Web uygulaması (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="ed1e2-140">ASP.NET Core Web App (Model-View-Controller)</span></span> | <span data-ttu-id="ed1e2-141">MVC</span><span class="sxs-lookup"><span data-stu-id="ed1e2-141">mvc</span></span>            | <span data-ttu-id="ed1e2-142">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="ed1e2-142">[C#], F#</span></span>      |
| <span data-ttu-id="ed1e2-143">ASP.NET Core Web uygulaması</span><span class="sxs-lookup"><span data-stu-id="ed1e2-143">ASP.NET Core Web App</span></span>                         | <span data-ttu-id="ed1e2-144">Razor</span><span class="sxs-lookup"><span data-stu-id="ed1e2-144">razor</span></span>          | <span data-ttu-id="ed1e2-145">[C#]</span><span class="sxs-lookup"><span data-stu-id="ed1e2-145">[C#]</span></span>          |
| <span data-ttu-id="ed1e2-146">ASP.NET Core Açısal ile</span><span class="sxs-lookup"><span data-stu-id="ed1e2-146">ASP.NET Core with Angular</span></span>                    | <span data-ttu-id="ed1e2-147">Açısal</span><span class="sxs-lookup"><span data-stu-id="ed1e2-147">angular</span></span>        | <span data-ttu-id="ed1e2-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="ed1e2-148">[C#]</span></span>          |
| <span data-ttu-id="ed1e2-149">ASP.NET Core React.js ile</span><span class="sxs-lookup"><span data-stu-id="ed1e2-149">ASP.NET Core with React.js</span></span>                   | <span data-ttu-id="ed1e2-150">tepki</span><span class="sxs-lookup"><span data-stu-id="ed1e2-150">react</span></span>          | <span data-ttu-id="ed1e2-151">[C#]</span><span class="sxs-lookup"><span data-stu-id="ed1e2-151">[C#]</span></span>          |
| <span data-ttu-id="ed1e2-152">ASP.NET Core React.js ve Redux</span><span class="sxs-lookup"><span data-stu-id="ed1e2-152">ASP.NET Core with React.js and Redux</span></span>         | <span data-ttu-id="ed1e2-153">reactredux</span><span class="sxs-lookup"><span data-stu-id="ed1e2-153">reactredux</span></span>     | <span data-ttu-id="ed1e2-154">[C#]</span><span class="sxs-lookup"><span data-stu-id="ed1e2-154">[C#]</span></span>          |
| <span data-ttu-id="ed1e2-155">ASP.NET Core Web API'si</span><span class="sxs-lookup"><span data-stu-id="ed1e2-155">ASP.NET Core Web API</span></span>                         | <span data-ttu-id="ed1e2-156">webapı</span><span class="sxs-lookup"><span data-stu-id="ed1e2-156">webapi</span></span>         | <span data-ttu-id="ed1e2-157">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="ed1e2-157">[C#], F#</span></span>      |
| <span data-ttu-id="ed1e2-158">Global.JSON dosyası</span><span class="sxs-lookup"><span data-stu-id="ed1e2-158">global.json file</span></span>                             | <span data-ttu-id="ed1e2-159">globaljson</span><span class="sxs-lookup"><span data-stu-id="ed1e2-159">globaljson</span></span>     |               |
| <span data-ttu-id="ed1e2-160">Nuget yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ed1e2-160">Nuget config</span></span>                                 | <span data-ttu-id="ed1e2-161">nugetconfig</span><span class="sxs-lookup"><span data-stu-id="ed1e2-161">nugetconfig</span></span>    |               |
| <span data-ttu-id="ed1e2-162">Web yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ed1e2-162">Web config</span></span>                                   | <span data-ttu-id="ed1e2-163">webconfig</span><span class="sxs-lookup"><span data-stu-id="ed1e2-163">webconfig</span></span>      |               |
| <span data-ttu-id="ed1e2-164">Çözüm dosyası</span><span class="sxs-lookup"><span data-stu-id="ed1e2-164">Solution file</span></span>                                | <span data-ttu-id="ed1e2-165">sln</span><span class="sxs-lookup"><span data-stu-id="ed1e2-165">sln</span></span>            |               |
| <span data-ttu-id="ed1e2-166">Razor sayfası</span><span class="sxs-lookup"><span data-stu-id="ed1e2-166">Razor page</span></span>                                   | <span data-ttu-id="ed1e2-167">sayfa</span><span class="sxs-lookup"><span data-stu-id="ed1e2-167">page</span></span>           |               |
| <span data-ttu-id="ed1e2-168">MVC/ViewImports</span><span class="sxs-lookup"><span data-stu-id="ed1e2-168">MVC/ViewImports</span></span>                              | <span data-ttu-id="ed1e2-169">viewimports</span><span class="sxs-lookup"><span data-stu-id="ed1e2-169">viewimports</span></span>    |               |
| <span data-ttu-id="ed1e2-170">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="ed1e2-170">MVC ViewStart</span></span>                                | <span data-ttu-id="ed1e2-171">viewstart</span><span class="sxs-lookup"><span data-stu-id="ed1e2-171">viewstart</span></span>      |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="ed1e2-172">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="ed1e2-172">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="ed1e2-173">Komut şablonlarının varsayılan listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-173">The command contains a default list of templates.</span></span> <span data-ttu-id="ed1e2-174">Kullanım `dotnet new -all` kullanılabilir şablonların listesini elde edilir.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-174">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="ed1e2-175">.NET Core ile önceden yüklenmiş olarak gelen şablonları aşağıdaki tabloda gösterilmektedir 1.x SDK.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-175">The following table shows the templates that come pre-installed with the .NET Core 1.x SDK.</span></span> <span data-ttu-id="ed1e2-176">Şablon için varsayılan dili köşeli ayraçlar içinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-176">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="ed1e2-177">Şablon açıklaması</span><span class="sxs-lookup"><span data-stu-id="ed1e2-177">Template description</span></span>  | <span data-ttu-id="ed1e2-178">Şablon adı</span><span class="sxs-lookup"><span data-stu-id="ed1e2-178">Template name</span></span>  | <span data-ttu-id="ed1e2-179">Diller</span><span class="sxs-lookup"><span data-stu-id="ed1e2-179">Languages</span></span> |
|----------------------|----------------|-----------|
| <span data-ttu-id="ed1e2-180">Konsol uygulaması</span><span class="sxs-lookup"><span data-stu-id="ed1e2-180">Console application</span></span>  | <span data-ttu-id="ed1e2-181">konsolu</span><span class="sxs-lookup"><span data-stu-id="ed1e2-181">console</span></span>        | <span data-ttu-id="ed1e2-182">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="ed1e2-182">[C#], F#</span></span>  |
| <span data-ttu-id="ed1e2-183">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="ed1e2-183">Class library</span></span>        | <span data-ttu-id="ed1e2-184">ClassLib</span><span class="sxs-lookup"><span data-stu-id="ed1e2-184">classlib</span></span>       | <span data-ttu-id="ed1e2-185">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="ed1e2-185">[C#], F#</span></span>  |
| <span data-ttu-id="ed1e2-186">Birim testi projesi</span><span class="sxs-lookup"><span data-stu-id="ed1e2-186">Unit test project</span></span>    | <span data-ttu-id="ed1e2-187">mstest'i</span><span class="sxs-lookup"><span data-stu-id="ed1e2-187">mstest</span></span>         | <span data-ttu-id="ed1e2-188">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="ed1e2-188">[C#], F#</span></span>  |
| <span data-ttu-id="ed1e2-189">xUnit test projesi</span><span class="sxs-lookup"><span data-stu-id="ed1e2-189">xUnit test project</span></span>   | <span data-ttu-id="ed1e2-190">xunit</span><span class="sxs-lookup"><span data-stu-id="ed1e2-190">xunit</span></span>          | <span data-ttu-id="ed1e2-191">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="ed1e2-191">[C#], F#</span></span>  |
| <span data-ttu-id="ed1e2-192">ASP.NET Core boş</span><span class="sxs-lookup"><span data-stu-id="ed1e2-192">ASP.NET Core empty</span></span>   | <span data-ttu-id="ed1e2-193">Web</span><span class="sxs-lookup"><span data-stu-id="ed1e2-193">web</span></span>            | <span data-ttu-id="ed1e2-194">[C#]</span><span class="sxs-lookup"><span data-stu-id="ed1e2-194">[C#]</span></span>      |
| <span data-ttu-id="ed1e2-195">ASP.NET Core Web uygulaması</span><span class="sxs-lookup"><span data-stu-id="ed1e2-195">ASP.NET Core Web App</span></span> | <span data-ttu-id="ed1e2-196">MVC</span><span class="sxs-lookup"><span data-stu-id="ed1e2-196">mvc</span></span>            | <span data-ttu-id="ed1e2-197">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="ed1e2-197">[C#], F#</span></span>  |
| <span data-ttu-id="ed1e2-198">ASP.NET Core Web API'si</span><span class="sxs-lookup"><span data-stu-id="ed1e2-198">ASP.NET Core Web API</span></span> | <span data-ttu-id="ed1e2-199">webapı</span><span class="sxs-lookup"><span data-stu-id="ed1e2-199">webapi</span></span>         | <span data-ttu-id="ed1e2-200">[C#]</span><span class="sxs-lookup"><span data-stu-id="ed1e2-200">[C#]</span></span>      |
| <span data-ttu-id="ed1e2-201">Nuget yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ed1e2-201">Nuget config</span></span>         | <span data-ttu-id="ed1e2-202">nugetconfig</span><span class="sxs-lookup"><span data-stu-id="ed1e2-202">nugetconfig</span></span>    |           |
| <span data-ttu-id="ed1e2-203">Web yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ed1e2-203">Web config</span></span>           | <span data-ttu-id="ed1e2-204">webconfig</span><span class="sxs-lookup"><span data-stu-id="ed1e2-204">webconfig</span></span>      |           |
| <span data-ttu-id="ed1e2-205">Çözüm dosyası</span><span class="sxs-lookup"><span data-stu-id="ed1e2-205">Solution file</span></span>        | <span data-ttu-id="ed1e2-206">sln</span><span class="sxs-lookup"><span data-stu-id="ed1e2-206">sln</span></span>            |           |

---

## <a name="options"></a><span data-ttu-id="ed1e2-207">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="ed1e2-207">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="ed1e2-208">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="ed1e2-208">.NET Core 2.x</span></span>](#tab/netcore2x)

`--force`

<span data-ttu-id="ed1e2-209">Var olan dosyaları değişeceğinden olsa bile oluşturulacak içeriği zorlar.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-209">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="ed1e2-210">Çıktı dizini bir proje zaten içeriyor, bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-210">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="ed1e2-211">Komut için Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-211">Prints out help for the command.</span></span> <span data-ttu-id="ed1e2-212">İçin çağrılabilir `dotnet new` kendisini komut veya herhangi bir şablonu gibi `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-212">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="ed1e2-213">Bir kaynak veya şablon paketinden yükler `PATH` veya `NUGET_ID` sağlanan.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-213">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="ed1e2-214">Özel şablonlar oluşturma hakkında daha fazla bilgi için bkz: [yeni dotnet için özel şablonlar](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="ed1e2-214">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="ed1e2-215">Belirtilen ad içeren şablonlarını listeler.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-215">Lists templates containing the specified name.</span></span> <span data-ttu-id="ed1e2-216">İçin başlatılırsa `dotnet new` komutu için belirtilen dizin kullanılabilir olası şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-216">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="ed1e2-217">Örneğin dizini zaten bir proje içeriyorsa, tüm proje şablonları listesinde değil.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-217">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="ed1e2-218">Oluşturmak için şablon dili.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-218">The language of the template to create.</span></span> <span data-ttu-id="ed1e2-219">Dil kabul değişir şablon tarafından (varsayılan ayarlarında bkz [bağımsız değişkenleri](#arguments) bölümü).</span><span class="sxs-lookup"><span data-stu-id="ed1e2-219">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="ed1e2-220">Bazı şablonlar için geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-220">Not valid for some templates.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="ed1e2-221">Oluşturulan çıktı adı.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-221">The name for the created output.</span></span> <span data-ttu-id="ed1e2-222">Ad belirtilmezse, geçerli dizin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-222">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="ed1e2-223">Oluşturulan çıktı yerleştirileceği konum.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-223">Location to place the generated output.</span></span> <span data-ttu-id="ed1e2-224">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-224">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="ed1e2-225">Şablonlar kullanılabilir türlerine göre filtreler.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-225">Filters templates based on available types.</span></span> <span data-ttu-id="ed1e2-226">Önceden tanımlanmış değerler "proje", "öğesi" veya "diğer" olabilir.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-226">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="ed1e2-227">Bir kaynak veya şablon paketini kaldırır `PATH` veya `NUGET_ID` sağlanan.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-227">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="ed1e2-228">Bir şablon kullanarak kaldırmak için bir `PATH`, yolun tam olarak nitelemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-228">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="ed1e2-229">Örneğin, *C:/Users/\<kullanıcı > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* çalışır, ancak *./GarciaSoftware.ConsoleTemplate.CSharp* içeren gelen Klasör almayacak.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-229">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="ed1e2-230">Ayrıca, şablonu yoldaki son sonlandırma dizin eğik çizgi eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-230">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="ed1e2-231">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="ed1e2-231">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="ed1e2-232">Belirli bir proje türü için tüm şablonları bağlamında çalışırken gösterir `dotnet new` tek başına komutu.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-232">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="ed1e2-233">Belirli bir şablon bağlamda gibi çalıştırırken `dotnet new web -all`, `-all` zorla oluşturma bayrak olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-233">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="ed1e2-234">Çıktı dizini bir proje zaten içeriyor, bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-234">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="ed1e2-235">Komut için Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-235">Prints out help for the command.</span></span> <span data-ttu-id="ed1e2-236">İçin çağrılabilir `dotnet new` kendisini komut veya herhangi bir şablonu gibi `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-236">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="ed1e2-237">Belirtilen ad içeren şablonlarını listeler.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-237">Lists templates containing the specified name.</span></span> <span data-ttu-id="ed1e2-238">İçin başlatılırsa `dotnet new` komutu için belirtilen dizin kullanılabilir olası şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-238">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="ed1e2-239">Örneğin dizini zaten bir proje içeriyorsa, tüm proje şablonları listesinde değil.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-239">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="ed1e2-240">Oluşturmak için şablon dili.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-240">The language of the template to create.</span></span> <span data-ttu-id="ed1e2-241">Dil kabul değişir şablon tarafından (varsayılan ayarlarında bkz [bağımsız değişkenleri](#arguments) bölümü).</span><span class="sxs-lookup"><span data-stu-id="ed1e2-241">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="ed1e2-242">Bazı şablonlar için geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-242">Not valid for some templates.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="ed1e2-243">Oluşturulan çıktı adı.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-243">The name for the created output.</span></span> <span data-ttu-id="ed1e2-244">Ad belirtilmezse, geçerli dizin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-244">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="ed1e2-245">Oluşturulan çıktı yerleştirileceği konum.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-245">Location to place the generated output.</span></span> <span data-ttu-id="ed1e2-246">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-246">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="ed1e2-247">Şablon seçenekleri</span><span class="sxs-lookup"><span data-stu-id="ed1e2-247">Template options</span></span>

<span data-ttu-id="ed1e2-248">Her proje şablonu ek seçenekleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-248">Each project template may have additional options available.</span></span> <span data-ttu-id="ed1e2-249">Çekirdek şablonları aşağıdaki ek seçeneklere sahip olursunuz:</span><span class="sxs-lookup"><span data-stu-id="ed1e2-249">The core templates have the following additional options:</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="ed1e2-250">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="ed1e2-250">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="ed1e2-251">**konsolunda, Açısal, tepki, reactredux**</span><span class="sxs-lookup"><span data-stu-id="ed1e2-251">**console, angular, react, reactredux**</span></span>

<span data-ttu-id="ed1e2-252">`--no-restore`-Proje oluşturma sırasında örtük bir geri yükleme yapın değil.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-252">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="ed1e2-253">**ClassLib**</span><span class="sxs-lookup"><span data-stu-id="ed1e2-253">**classlib**</span></span>

<span data-ttu-id="ed1e2-254">`-f|--framework <FRAMEWORK>`-Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-254">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ed1e2-255">Değerler: `netcoreapp2.0` .NET çekirdek sınıf kitaplığı oluşturmak için veya `netstandard2.0` .NET standart sınıf kitaplığı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-255">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="ed1e2-256">Varsayılan değer `netstandard2.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-256">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="ed1e2-257">`--no-restore`-Proje oluşturma sırasında örtük bir geri yükleme yapın değil.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-257">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="ed1e2-258">**mstest'i, xunit**</span><span class="sxs-lookup"><span data-stu-id="ed1e2-258">**mstest, xunit**</span></span>

<span data-ttu-id="ed1e2-259">`-p|--enable-pack`-Proje kullanma paketleme sağlar [dotnet paketi](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="ed1e2-259">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="ed1e2-260">`--no-restore`-Proje oluşturma sırasında örtük bir geri yükleme yapın değil.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-260">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="ed1e2-261">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="ed1e2-261">**globaljson**</span></span>

<span data-ttu-id="ed1e2-262">`--sdk-version <VERSION_NUMBER>`-Kullanmak için .NET Core SDK sürümünü belirtir *global.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-262">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="ed1e2-263">**Web**</span><span class="sxs-lookup"><span data-stu-id="ed1e2-263">**web**</span></span>

<span data-ttu-id="ed1e2-264">`--use-launch-settings`-İçeren *launchSettings.json* oluşturulan şablon çıkışı.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-264">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="ed1e2-265">`--no-restore`-Proje oluşturma sırasında örtük bir geri yükleme yapın değil.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-265">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="ed1e2-266">**webapı**</span><span class="sxs-lookup"><span data-stu-id="ed1e2-266">**webapi**</span></span>

<span data-ttu-id="ed1e2-267">`-au|--auth <AUTHENTICATION_TYPE>`-Kullanılacak kimlik doğrulama türü.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-267">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="ed1e2-268">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="ed1e2-268">The possible values are:</span></span>

- <span data-ttu-id="ed1e2-269">`None`-Kimlik doğrulama yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="ed1e2-269">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="ed1e2-270">`IndividualB2C`-Azure AD B2C ile tek tek kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-270">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="ed1e2-271">`SingleOrg`-Tek bir kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-271">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="ed1e2-272">`Windows`-Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-272">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="ed1e2-273">`--aad-b2c-instance <INSTANCE>`-Bağlanmak için Azure Active Directory B2C örnek.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-273">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="ed1e2-274">İle kullandığınız `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-274">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="ed1e2-275">Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-275">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="ed1e2-276">`-ssp|--susi-policy-id <ID>`-Bu proje için oturum açma ve kaydolma ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-276">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="ed1e2-277">İle kullandığınız `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-277">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ed1e2-278">`--aad-instance <INSTANCE>`-Bağlanmak için Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-278">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="ed1e2-279">İle kullandığınız `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-279">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ed1e2-280">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-280">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="ed1e2-281">`--client-id <ID>`-Bu proje için istemci kimliği.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-281">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="ed1e2-282">İle kullandığınız `IndividualB2C` veya `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-282">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="ed1e2-283">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-283">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="ed1e2-284">`--domain <DOMAIN>`-Etki alanı için dizin Kiracı.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-284">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="ed1e2-285">İle kullandığınız `SingleOrg` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-285">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ed1e2-286">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-286">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="ed1e2-287">`--tenant-id <ID>`-Tenantıd bağlanmak için kimliği dizini.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-287">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="ed1e2-288">İle kullandığınız `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-288">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ed1e2-289">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-289">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="ed1e2-290">`-r|--org-read-access`-Bu uygulamanın dizine okuma erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-290">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="ed1e2-291">Yalnızca uygular `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-291">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="ed1e2-292">`--use-launch-settings`-İçeren *launchSettings.json* oluşturulan şablon çıkışı.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-292">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="ed1e2-293">`-uld|--use-local-db`-Yerel veritabanı yerine SQLite kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-293">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="ed1e2-294">Yalnızca uygular `Individual` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-294">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ed1e2-295">`--no-restore`-Proje oluşturma sırasında örtük bir geri yükleme yapın değil.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-295">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="ed1e2-296">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="ed1e2-296">**mvc, razor**</span></span>

<span data-ttu-id="ed1e2-297">`-au|--auth <AUTHENTICATION_TYPE>`-Kullanılacak kimlik doğrulama türü.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-297">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="ed1e2-298">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="ed1e2-298">The possible values are:</span></span>

- <span data-ttu-id="ed1e2-299">`None`-Kimlik doğrulama yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="ed1e2-299">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="ed1e2-300">`Individual`-Tek tek kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-300">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="ed1e2-301">`IndividualB2C`-Azure AD B2C ile tek tek kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-301">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="ed1e2-302">`SingleOrg`-Tek bir kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-302">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="ed1e2-303">`MultiOrg`-Birden çok Kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-303">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="ed1e2-304">`Windows`-Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-304">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="ed1e2-305">`--aad-b2c-instance <INSTANCE>`-Bağlanmak için Azure Active Directory B2C örnek.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-305">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="ed1e2-306">İle kullandığınız `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-306">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="ed1e2-307">Varsayılan değer `https://login.microsoftonline.com/tfp/` .</span><span class="sxs-lookup"><span data-stu-id="ed1e2-307">The default value is `https://login.microsoftonline.com/tfp/` .</span></span>

<span data-ttu-id="ed1e2-308">`-ssp|--susi-policy-id <ID>`-Bu proje için oturum açma ve kaydolma ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-308">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="ed1e2-309">İle kullandığınız `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-309">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ed1e2-310">`-rp|--reset-password-policy-id <ID>`-Bu proje için reset parola ilkesi kimliği.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-310">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="ed1e2-311">İle kullandığınız `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-311">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ed1e2-312">`-ep|--edit-profile-policy-id <ID>`-Bu proje için Düzenle profili ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-312">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="ed1e2-313">İle kullandığınız `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-313">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ed1e2-314">`--aad-instance <INSTANCE>`-Bağlanmak için Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-314">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="ed1e2-315">İle kullandığınız `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-315">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="ed1e2-316">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-316">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="ed1e2-317">`--client-id <ID>`-Bu proje için istemci kimliği.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-317">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="ed1e2-318">İle kullandığınız `IndividualB2C`, `SingleOrg`, veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-318">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="ed1e2-319">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-319">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="ed1e2-320">`--domain <DOMAIN>`-Etki alanı için dizin Kiracı.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-320">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="ed1e2-321">İle kullandığınız `SingleOrg` veya `IndividualB2C` kimlik doğrulaması...</span><span class="sxs-lookup"><span data-stu-id="ed1e2-321">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="ed1e2-322">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-322">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="ed1e2-323">`--tenant-id <ID>`-Tenantıd bağlanmak için kimliği dizini.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-323">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="ed1e2-324">İle kullandığınız `SingleOrg` kimlik doğrulaması...</span><span class="sxs-lookup"><span data-stu-id="ed1e2-324">Use with `SingleOrg` authentication..</span></span> <span data-ttu-id="ed1e2-325">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-325">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="ed1e2-326">`--callback-path <PATH>`-Yeniden yönlendirme URI'si, uygulamanın taban yolu içindeki istek yolu.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-326">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="ed1e2-327">İle kullandığınız `SingleOrg` veya `IndividualB2C` kimlik doğrulaması...</span><span class="sxs-lookup"><span data-stu-id="ed1e2-327">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="ed1e2-328">Varsayılan değer `/signin-oidc` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-328">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="ed1e2-329">`-r|--org-read-access`-Bu uygulamanın dizine okuma erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-329">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="ed1e2-330">Yalnızca uygular `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-330">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="ed1e2-331">`--use-launch-settings`-İçeren *launchSettings.json* oluşturulan şablon çıkışı.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-331">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="ed1e2-332">`--use-browserlink`-BrowserLink projede içerir.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-332">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="ed1e2-333">`-uld|--use-local-db`-Yerel veritabanı yerine SQLite kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-333">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="ed1e2-334">Yalnızca uygular `Individual` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-334">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ed1e2-335">`--no-restore`-Proje oluşturma sırasında örtük bir geri yükleme yapın değil.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-335">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="ed1e2-336">**Sayfa**</span><span class="sxs-lookup"><span data-stu-id="ed1e2-336">**page**</span></span>

<span data-ttu-id="ed1e2-337">`-na|--namespace <NAMESPACE_NAME>`-Namespace üretilen kod için.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-337">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="ed1e2-338">Varsayılan değer `MyApp.Namespace` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-338">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="ed1e2-339">`-np|--no-pagemodel`-Bir PageModel olmadan sayfası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-339">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="ed1e2-340">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="ed1e2-340">**viewimports**</span></span>

<span data-ttu-id="ed1e2-341">`-na|--namespace <NAMESPACE_NAME>`-Namespace üretilen kod için.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-341">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="ed1e2-342">Varsayılan değer `MyApp.Namespace` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-342">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="ed1e2-343">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="ed1e2-343">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="ed1e2-344">**Konsolu, xunit, mstest'i, web, webapı**</span><span class="sxs-lookup"><span data-stu-id="ed1e2-344">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="ed1e2-345">`-f|--framework`-Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-345">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ed1e2-346">Değerler: `netcoreapp1.0` veya `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-346">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="ed1e2-347">Varsayılan değer `netcoreapp1.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-347">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="ed1e2-348">**ClassLib**</span><span class="sxs-lookup"><span data-stu-id="ed1e2-348">**classlib**</span></span>

<span data-ttu-id="ed1e2-349">`-f|--framework`-Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-349">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ed1e2-350">Değerler: `netcoreapp1.0`, `netcoreapp1.1`, veya `netstandard1.0` için `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-350">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="ed1e2-351">Varsayılan değer `netstandard1.4` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-351">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="ed1e2-352">**MVC**</span><span class="sxs-lookup"><span data-stu-id="ed1e2-352">**mvc**</span></span>

<span data-ttu-id="ed1e2-353">`-f|--framework`-Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-353">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ed1e2-354">Değerler: `netcoreapp1.0` veya `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-354">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="ed1e2-355">Varsayılan değer `netcoreapp1.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-355">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="ed1e2-356">`-au|--auth`-Kullanılacak kimlik doğrulama türü.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-356">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="ed1e2-357">Değerler: `None` veya `Individual`.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-357">Values: `None` or `Individual`.</span></span> <span data-ttu-id="ed1e2-358">Varsayılan değer `None` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-358">The default value is `None`.</span></span>

<span data-ttu-id="ed1e2-359">`-uld|--use-local-db`-Yerel veritabanı yerine SQLite kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-359">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="ed1e2-360">Değerler: `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-360">Values: `true` or `false`.</span></span> <span data-ttu-id="ed1e2-361">Varsayılan değer `false` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-361">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="ed1e2-362">Örnekler</span><span class="sxs-lookup"><span data-stu-id="ed1e2-362">Examples</span></span>

<span data-ttu-id="ed1e2-363">Geçerli dizinde bir F # konsol uygulama projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="ed1e2-363">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang f#`

<span data-ttu-id="ed1e2-364">(Yalnızca .NET çekirdeği 2.0 SDK veya sonraki sürümleriyle kullanılabilir) belirtilen dizindeki .NET standart bir sınıf kitaplığı projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="ed1e2-364">Create a .NET Standard class library project in the specified directory (available only with .NET Core 2.0 SDK or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="ed1e2-365">Yeni bir ASP.NET Core C# MVC uygulama projesi geçerli dizinde kimlik doğrulamasız .NET Core 2.0 hedefleme oluşturun:</span><span class="sxs-lookup"><span data-stu-id="ed1e2-365">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication targeting .NET Core 2.0:</span></span>

`dotnet new mvc -au None -f netcoreapp2.0`

<span data-ttu-id="ed1e2-366">.NET Core 2.0 hedefleme yeni bir xUnit uygulaması oluşturun:</span><span class="sxs-lookup"><span data-stu-id="ed1e2-366">Create a new xUnit application targeting .NET Core 2.0:</span></span>

`dotnet new xunit --framework netcoreapp2.0`

<span data-ttu-id="ed1e2-367">MVC için kullanılabilir tüm şablonları listeler:</span><span class="sxs-lookup"><span data-stu-id="ed1e2-367">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

## <a name="see-also"></a><span data-ttu-id="ed1e2-368">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed1e2-368">See also</span></span>

[<span data-ttu-id="ed1e2-369">Yeni dotnet için özel şablonlar</span><span class="sxs-lookup"><span data-stu-id="ed1e2-369">Custom templates for dotnet new</span></span>](custom-templates.md)  
[<span data-ttu-id="ed1e2-370">Dotnet için özel bir şablon yeni oluştur</span><span class="sxs-lookup"><span data-stu-id="ed1e2-370">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)  
[<span data-ttu-id="ed1e2-371">DotNet/dotnet-şablonu-samples GitHub depo</span><span class="sxs-lookup"><span data-stu-id="ed1e2-371">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)  
[<span data-ttu-id="ed1e2-372">Yeni dotnet için kullanılabilir şablonlar</span><span class="sxs-lookup"><span data-stu-id="ed1e2-372">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
