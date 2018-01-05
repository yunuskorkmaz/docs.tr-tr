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
ms.workload: dotnetcore
ms.openlocfilehash: f5815e1ad2a36a8ef3279f6ff83465dba9ec5d50
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-new"></a><span data-ttu-id="b5d40-104">DotNet yeni</span><span class="sxs-lookup"><span data-stu-id="b5d40-104">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="b5d40-105">Ad</span><span class="sxs-lookup"><span data-stu-id="b5d40-105">Name</span></span>

<span data-ttu-id="b5d40-106">`dotnet new`-Yeni Proje, yapılandırma dosyası veya belirtilen şablona dayalı çözüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b5d40-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b5d40-107">Özet</span><span class="sxs-lookup"><span data-stu-id="b5d40-107">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="b5d40-108">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="b5d40-108">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="b5d40-109">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="b5d40-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="b5d40-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b5d40-110">Description</span></span>

<span data-ttu-id="b5d40-111">`dotnet new` Komutu geçerli bir .NET Core projeyi başlatmak için kolay bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="b5d40-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span> 

<span data-ttu-id="b5d40-112">Komut çağrıları [şablon motoru](https://github.com/dotnet/templating) yapıları belirtilen şablonu ve seçenekleri bağlı disk oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="b5d40-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="b5d40-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="b5d40-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="b5d40-114">Komutu çağrıldığında örneği oluşturmak için şablon.</span><span class="sxs-lookup"><span data-stu-id="b5d40-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="b5d40-115">Her bir şablon geçirebilirsiniz belirli seçenekleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="b5d40-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="b5d40-116">Daha fazla bilgi için bkz: [şablon seçenekleri](#template-options).</span><span class="sxs-lookup"><span data-stu-id="b5d40-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="b5d40-117">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="b5d40-117">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="b5d40-118">Komut şablonlarının varsayılan listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="b5d40-118">The command contains a default list of templates.</span></span> <span data-ttu-id="b5d40-119">Kullanım `dotnet new -l` kullanılabilir şablonların listesini elde edilir.</span><span class="sxs-lookup"><span data-stu-id="b5d40-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="b5d40-120">Aşağıdaki tabloda .NET Core 2.0 SDK ile birlikte önceden yüklenmiş olarak gelen şablonları gösterir.</span><span class="sxs-lookup"><span data-stu-id="b5d40-120">The following table shows the templates that come pre-installed with the .NET Core 2.0 SDK.</span></span> <span data-ttu-id="b5d40-121">Şablon için varsayılan dili köşeli ayraçlar içinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b5d40-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="b5d40-122">Şablon açıklaması</span><span class="sxs-lookup"><span data-stu-id="b5d40-122">Template description</span></span>                          | <span data-ttu-id="b5d40-123">Şablon adı</span><span class="sxs-lookup"><span data-stu-id="b5d40-123">Template name</span></span>  | <span data-ttu-id="b5d40-124">Diller</span><span class="sxs-lookup"><span data-stu-id="b5d40-124">Languages</span></span>     |
|----------------------------------------------|----------------|---------------|
| <span data-ttu-id="b5d40-125">Konsol uygulaması</span><span class="sxs-lookup"><span data-stu-id="b5d40-125">Console application</span></span>                          | <span data-ttu-id="b5d40-126">konsolu</span><span class="sxs-lookup"><span data-stu-id="b5d40-126">console</span></span>        | <span data-ttu-id="b5d40-127">[C#] F #, VB</span><span class="sxs-lookup"><span data-stu-id="b5d40-127">[C#], F#, VB</span></span>  |
| <span data-ttu-id="b5d40-128">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="b5d40-128">Class library</span></span>                                | <span data-ttu-id="b5d40-129">ClassLib</span><span class="sxs-lookup"><span data-stu-id="b5d40-129">classlib</span></span>       | <span data-ttu-id="b5d40-130">[C#] F #, VB</span><span class="sxs-lookup"><span data-stu-id="b5d40-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="b5d40-131">Birim testi projesi</span><span class="sxs-lookup"><span data-stu-id="b5d40-131">Unit test project</span></span>                            | <span data-ttu-id="b5d40-132">mstest'i</span><span class="sxs-lookup"><span data-stu-id="b5d40-132">mstest</span></span>         | <span data-ttu-id="b5d40-133">[C#] F #, VB</span><span class="sxs-lookup"><span data-stu-id="b5d40-133">[C#], F#, VB</span></span>  |
| <span data-ttu-id="b5d40-134">xUnit test projesi</span><span class="sxs-lookup"><span data-stu-id="b5d40-134">xUnit test project</span></span>                           | <span data-ttu-id="b5d40-135">xunit</span><span class="sxs-lookup"><span data-stu-id="b5d40-135">xunit</span></span>          | <span data-ttu-id="b5d40-136">[C#] F #, VB</span><span class="sxs-lookup"><span data-stu-id="b5d40-136">[C#], F#, VB</span></span>  |
| <span data-ttu-id="b5d40-137">ASP.NET Core boş</span><span class="sxs-lookup"><span data-stu-id="b5d40-137">ASP.NET Core empty</span></span>                           | <span data-ttu-id="b5d40-138">Web</span><span class="sxs-lookup"><span data-stu-id="b5d40-138">web</span></span>            | <span data-ttu-id="b5d40-139">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="b5d40-139">[C#], F#</span></span>      |
| <span data-ttu-id="b5d40-140">ASP.NET Core Web uygulaması (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="b5d40-140">ASP.NET Core Web App (Model-View-Controller)</span></span> | <span data-ttu-id="b5d40-141">MVC</span><span class="sxs-lookup"><span data-stu-id="b5d40-141">mvc</span></span>            | <span data-ttu-id="b5d40-142">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="b5d40-142">[C#], F#</span></span>      |
| <span data-ttu-id="b5d40-143">ASP.NET Core Web uygulaması</span><span class="sxs-lookup"><span data-stu-id="b5d40-143">ASP.NET Core Web App</span></span>                         | <span data-ttu-id="b5d40-144">Razor</span><span class="sxs-lookup"><span data-stu-id="b5d40-144">razor</span></span>          | <span data-ttu-id="b5d40-145">[C#]</span><span class="sxs-lookup"><span data-stu-id="b5d40-145">[C#]</span></span>          |
| <span data-ttu-id="b5d40-146">ASP.NET Core Açısal ile</span><span class="sxs-lookup"><span data-stu-id="b5d40-146">ASP.NET Core with Angular</span></span>                    | <span data-ttu-id="b5d40-147">Açısal</span><span class="sxs-lookup"><span data-stu-id="b5d40-147">angular</span></span>        | <span data-ttu-id="b5d40-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="b5d40-148">[C#]</span></span>          |
| <span data-ttu-id="b5d40-149">ASP.NET Core React.js ile</span><span class="sxs-lookup"><span data-stu-id="b5d40-149">ASP.NET Core with React.js</span></span>                   | <span data-ttu-id="b5d40-150">tepki</span><span class="sxs-lookup"><span data-stu-id="b5d40-150">react</span></span>          | <span data-ttu-id="b5d40-151">[C#]</span><span class="sxs-lookup"><span data-stu-id="b5d40-151">[C#]</span></span>          |
| <span data-ttu-id="b5d40-152">ASP.NET Core React.js ve Redux</span><span class="sxs-lookup"><span data-stu-id="b5d40-152">ASP.NET Core with React.js and Redux</span></span>         | <span data-ttu-id="b5d40-153">reactredux</span><span class="sxs-lookup"><span data-stu-id="b5d40-153">reactredux</span></span>     | <span data-ttu-id="b5d40-154">[C#]</span><span class="sxs-lookup"><span data-stu-id="b5d40-154">[C#]</span></span>          |
| <span data-ttu-id="b5d40-155">ASP.NET Core Web API'si</span><span class="sxs-lookup"><span data-stu-id="b5d40-155">ASP.NET Core Web API</span></span>                         | <span data-ttu-id="b5d40-156">webapı</span><span class="sxs-lookup"><span data-stu-id="b5d40-156">webapi</span></span>         | <span data-ttu-id="b5d40-157">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="b5d40-157">[C#], F#</span></span>      |
| <span data-ttu-id="b5d40-158">Global.JSON dosyası</span><span class="sxs-lookup"><span data-stu-id="b5d40-158">global.json file</span></span>                             | <span data-ttu-id="b5d40-159">globaljson</span><span class="sxs-lookup"><span data-stu-id="b5d40-159">globaljson</span></span>     |               |
| <span data-ttu-id="b5d40-160">Nuget yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b5d40-160">Nuget config</span></span>                                 | <span data-ttu-id="b5d40-161">nugetconfig</span><span class="sxs-lookup"><span data-stu-id="b5d40-161">nugetconfig</span></span>    |               |
| <span data-ttu-id="b5d40-162">Web yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b5d40-162">Web config</span></span>                                   | <span data-ttu-id="b5d40-163">webconfig</span><span class="sxs-lookup"><span data-stu-id="b5d40-163">webconfig</span></span>      |               |
| <span data-ttu-id="b5d40-164">Çözüm dosyası</span><span class="sxs-lookup"><span data-stu-id="b5d40-164">Solution file</span></span>                                | <span data-ttu-id="b5d40-165">sln</span><span class="sxs-lookup"><span data-stu-id="b5d40-165">sln</span></span>            |               |
| <span data-ttu-id="b5d40-166">Razor sayfası</span><span class="sxs-lookup"><span data-stu-id="b5d40-166">Razor page</span></span>                                   | <span data-ttu-id="b5d40-167">sayfa</span><span class="sxs-lookup"><span data-stu-id="b5d40-167">page</span></span>           |               |
| <span data-ttu-id="b5d40-168">MVC/ViewImports</span><span class="sxs-lookup"><span data-stu-id="b5d40-168">MVC/ViewImports</span></span>                              | <span data-ttu-id="b5d40-169">viewimports</span><span class="sxs-lookup"><span data-stu-id="b5d40-169">viewimports</span></span>    |               |
| <span data-ttu-id="b5d40-170">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="b5d40-170">MVC ViewStart</span></span>                                | <span data-ttu-id="b5d40-171">viewstart</span><span class="sxs-lookup"><span data-stu-id="b5d40-171">viewstart</span></span>      |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="b5d40-172">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="b5d40-172">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="b5d40-173">Komut şablonlarının varsayılan listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="b5d40-173">The command contains a default list of templates.</span></span> <span data-ttu-id="b5d40-174">Kullanım `dotnet new -all` kullanılabilir şablonların listesini elde edilir.</span><span class="sxs-lookup"><span data-stu-id="b5d40-174">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="b5d40-175">.NET Core ile önceden yüklenmiş olarak gelen şablonları aşağıdaki tabloda gösterilmektedir 1.x SDK.</span><span class="sxs-lookup"><span data-stu-id="b5d40-175">The following table shows the templates that come pre-installed with the .NET Core 1.x SDK.</span></span> <span data-ttu-id="b5d40-176">Şablon için varsayılan dili köşeli ayraçlar içinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b5d40-176">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="b5d40-177">Şablon açıklaması</span><span class="sxs-lookup"><span data-stu-id="b5d40-177">Template description</span></span>  | <span data-ttu-id="b5d40-178">Şablon adı</span><span class="sxs-lookup"><span data-stu-id="b5d40-178">Template name</span></span>  | <span data-ttu-id="b5d40-179">Diller</span><span class="sxs-lookup"><span data-stu-id="b5d40-179">Languages</span></span> |
|----------------------|----------------|-----------|
| <span data-ttu-id="b5d40-180">Konsol uygulaması</span><span class="sxs-lookup"><span data-stu-id="b5d40-180">Console application</span></span>  | <span data-ttu-id="b5d40-181">konsolu</span><span class="sxs-lookup"><span data-stu-id="b5d40-181">console</span></span>        | <span data-ttu-id="b5d40-182">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="b5d40-182">[C#], F#</span></span>  |
| <span data-ttu-id="b5d40-183">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="b5d40-183">Class library</span></span>        | <span data-ttu-id="b5d40-184">ClassLib</span><span class="sxs-lookup"><span data-stu-id="b5d40-184">classlib</span></span>       | <span data-ttu-id="b5d40-185">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="b5d40-185">[C#], F#</span></span>  |
| <span data-ttu-id="b5d40-186">Birim testi projesi</span><span class="sxs-lookup"><span data-stu-id="b5d40-186">Unit test project</span></span>    | <span data-ttu-id="b5d40-187">mstest'i</span><span class="sxs-lookup"><span data-stu-id="b5d40-187">mstest</span></span>         | <span data-ttu-id="b5d40-188">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="b5d40-188">[C#], F#</span></span>  |
| <span data-ttu-id="b5d40-189">xUnit test projesi</span><span class="sxs-lookup"><span data-stu-id="b5d40-189">xUnit test project</span></span>   | <span data-ttu-id="b5d40-190">xunit</span><span class="sxs-lookup"><span data-stu-id="b5d40-190">xunit</span></span>          | <span data-ttu-id="b5d40-191">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="b5d40-191">[C#], F#</span></span>  |
| <span data-ttu-id="b5d40-192">ASP.NET Core boş</span><span class="sxs-lookup"><span data-stu-id="b5d40-192">ASP.NET Core empty</span></span>   | <span data-ttu-id="b5d40-193">Web</span><span class="sxs-lookup"><span data-stu-id="b5d40-193">web</span></span>            | <span data-ttu-id="b5d40-194">[C#]</span><span class="sxs-lookup"><span data-stu-id="b5d40-194">[C#]</span></span>      |
| <span data-ttu-id="b5d40-195">ASP.NET Core Web uygulaması</span><span class="sxs-lookup"><span data-stu-id="b5d40-195">ASP.NET Core Web App</span></span> | <span data-ttu-id="b5d40-196">MVC</span><span class="sxs-lookup"><span data-stu-id="b5d40-196">mvc</span></span>            | <span data-ttu-id="b5d40-197">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="b5d40-197">[C#], F#</span></span>  |
| <span data-ttu-id="b5d40-198">ASP.NET Core Web API'si</span><span class="sxs-lookup"><span data-stu-id="b5d40-198">ASP.NET Core Web API</span></span> | <span data-ttu-id="b5d40-199">webapı</span><span class="sxs-lookup"><span data-stu-id="b5d40-199">webapi</span></span>         | <span data-ttu-id="b5d40-200">[C#]</span><span class="sxs-lookup"><span data-stu-id="b5d40-200">[C#]</span></span>      |
| <span data-ttu-id="b5d40-201">Nuget yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b5d40-201">Nuget config</span></span>         | <span data-ttu-id="b5d40-202">nugetconfig</span><span class="sxs-lookup"><span data-stu-id="b5d40-202">nugetconfig</span></span>    |           |
| <span data-ttu-id="b5d40-203">Web yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b5d40-203">Web config</span></span>           | <span data-ttu-id="b5d40-204">webconfig</span><span class="sxs-lookup"><span data-stu-id="b5d40-204">webconfig</span></span>      |           |
| <span data-ttu-id="b5d40-205">Çözüm dosyası</span><span class="sxs-lookup"><span data-stu-id="b5d40-205">Solution file</span></span>        | <span data-ttu-id="b5d40-206">sln</span><span class="sxs-lookup"><span data-stu-id="b5d40-206">sln</span></span>            |           |

---

## <a name="options"></a><span data-ttu-id="b5d40-207">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="b5d40-207">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="b5d40-208">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="b5d40-208">.NET Core 2.x</span></span>](#tab/netcore2x)

`--force`

<span data-ttu-id="b5d40-209">Var olan dosyaları değişeceğinden olsa bile oluşturulacak içeriği zorlar.</span><span class="sxs-lookup"><span data-stu-id="b5d40-209">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="b5d40-210">Çıktı dizini bir proje zaten içeriyor, bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b5d40-210">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="b5d40-211">Komut için Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="b5d40-211">Prints out help for the command.</span></span> <span data-ttu-id="b5d40-212">İçin çağrılabilir `dotnet new` kendisini komut veya herhangi bir şablonu gibi `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="b5d40-212">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="b5d40-213">Bir kaynak veya şablon paketinden yükler `PATH` veya `NUGET_ID` sağlanan.</span><span class="sxs-lookup"><span data-stu-id="b5d40-213">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="b5d40-214">Özel şablonlar oluşturma hakkında daha fazla bilgi için bkz: [yeni dotnet için özel şablonlar](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="b5d40-214">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="b5d40-215">Belirtilen ad içeren şablonlarını listeler.</span><span class="sxs-lookup"><span data-stu-id="b5d40-215">Lists templates containing the specified name.</span></span> <span data-ttu-id="b5d40-216">İçin başlatılırsa `dotnet new` komutu için belirtilen dizin kullanılabilir olası şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="b5d40-216">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="b5d40-217">Örneğin dizini zaten bir proje içeriyorsa, tüm proje şablonları listesinde değil.</span><span class="sxs-lookup"><span data-stu-id="b5d40-217">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="b5d40-218">Oluşturmak için şablon dili.</span><span class="sxs-lookup"><span data-stu-id="b5d40-218">The language of the template to create.</span></span> <span data-ttu-id="b5d40-219">Dil kabul değişir şablon tarafından (varsayılan ayarlarında bkz [bağımsız değişkenleri](#arguments) bölümü).</span><span class="sxs-lookup"><span data-stu-id="b5d40-219">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="b5d40-220">Bazı şablonlar için geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="b5d40-220">Not valid for some templates.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="b5d40-221">Oluşturulan çıktı adı.</span><span class="sxs-lookup"><span data-stu-id="b5d40-221">The name for the created output.</span></span> <span data-ttu-id="b5d40-222">Ad belirtilmezse, geçerli dizin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b5d40-222">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="b5d40-223">Oluşturulan çıktı yerleştirileceği konum.</span><span class="sxs-lookup"><span data-stu-id="b5d40-223">Location to place the generated output.</span></span> <span data-ttu-id="b5d40-224">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="b5d40-224">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="b5d40-225">Şablonlar kullanılabilir türlerine göre filtreler.</span><span class="sxs-lookup"><span data-stu-id="b5d40-225">Filters templates based on available types.</span></span> <span data-ttu-id="b5d40-226">Önceden tanımlanmış değerler "proje", "öğesi" veya "diğer" olabilir.</span><span class="sxs-lookup"><span data-stu-id="b5d40-226">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="b5d40-227">Bir kaynak veya şablon paketini kaldırır `PATH` veya `NUGET_ID` sağlanan.</span><span class="sxs-lookup"><span data-stu-id="b5d40-227">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="b5d40-228">Bir şablon kullanarak kaldırmak için bir `PATH`, yolun tam olarak nitelemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="b5d40-228">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="b5d40-229">Örneğin, *C:/Users/\<kullanıcı > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* çalışır, ancak *./GarciaSoftware.ConsoleTemplate.CSharp* içeren gelen Klasör almayacak.</span><span class="sxs-lookup"><span data-stu-id="b5d40-229">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="b5d40-230">Ayrıca, şablonu yoldaki son sonlandırma dizin eğik çizgi eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="b5d40-230">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="b5d40-231">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="b5d40-231">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="b5d40-232">Belirli bir proje türü için tüm şablonları bağlamında çalışırken gösterir `dotnet new` tek başına komutu.</span><span class="sxs-lookup"><span data-stu-id="b5d40-232">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="b5d40-233">Belirli bir şablon bağlamda gibi çalıştırırken `dotnet new web -all`, `-all` zorla oluşturma bayrak olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="b5d40-233">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="b5d40-234">Çıktı dizini bir proje zaten içeriyor, bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b5d40-234">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="b5d40-235">Komut için Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="b5d40-235">Prints out help for the command.</span></span> <span data-ttu-id="b5d40-236">İçin çağrılabilir `dotnet new` kendisini komut veya herhangi bir şablonu gibi `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="b5d40-236">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="b5d40-237">Belirtilen ad içeren şablonlarını listeler.</span><span class="sxs-lookup"><span data-stu-id="b5d40-237">Lists templates containing the specified name.</span></span> <span data-ttu-id="b5d40-238">İçin başlatılırsa `dotnet new` komutu için belirtilen dizin kullanılabilir olası şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="b5d40-238">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="b5d40-239">Örneğin dizini zaten bir proje içeriyorsa, tüm proje şablonları listesinde değil.</span><span class="sxs-lookup"><span data-stu-id="b5d40-239">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="b5d40-240">Oluşturmak için şablon dili.</span><span class="sxs-lookup"><span data-stu-id="b5d40-240">The language of the template to create.</span></span> <span data-ttu-id="b5d40-241">Dil kabul değişir şablon tarafından (varsayılan ayarlarında bkz [bağımsız değişkenleri](#arguments) bölümü).</span><span class="sxs-lookup"><span data-stu-id="b5d40-241">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="b5d40-242">Bazı şablonlar için geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="b5d40-242">Not valid for some templates.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="b5d40-243">Oluşturulan çıktı adı.</span><span class="sxs-lookup"><span data-stu-id="b5d40-243">The name for the created output.</span></span> <span data-ttu-id="b5d40-244">Ad belirtilmezse, geçerli dizin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b5d40-244">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="b5d40-245">Oluşturulan çıktı yerleştirileceği konum.</span><span class="sxs-lookup"><span data-stu-id="b5d40-245">Location to place the generated output.</span></span> <span data-ttu-id="b5d40-246">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="b5d40-246">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="b5d40-247">Şablon seçenekleri</span><span class="sxs-lookup"><span data-stu-id="b5d40-247">Template options</span></span>

<span data-ttu-id="b5d40-248">Her proje şablonu ek seçenekleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="b5d40-248">Each project template may have additional options available.</span></span> <span data-ttu-id="b5d40-249">Çekirdek şablonları aşağıdaki ek seçeneklere sahip olursunuz:</span><span class="sxs-lookup"><span data-stu-id="b5d40-249">The core templates have the following additional options:</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="b5d40-250">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="b5d40-250">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="b5d40-251">**konsolunda, Açısal, tepki, reactredux**</span><span class="sxs-lookup"><span data-stu-id="b5d40-251">**console, angular, react, reactredux**</span></span>

<span data-ttu-id="b5d40-252">`--no-restore`-Proje oluşturma sırasında örtük bir geri yükleme yapın değil.</span><span class="sxs-lookup"><span data-stu-id="b5d40-252">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="b5d40-253">**ClassLib**</span><span class="sxs-lookup"><span data-stu-id="b5d40-253">**classlib**</span></span>

<span data-ttu-id="b5d40-254">`-f|--framework <FRAMEWORK>`-Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="b5d40-254">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="b5d40-255">Değerler: `netcoreapp2.0` .NET çekirdek sınıf kitaplığı oluşturmak için veya `netstandard2.0` .NET standart sınıf kitaplığı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="b5d40-255">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="b5d40-256">Varsayılan değer `netstandard2.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b5d40-256">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="b5d40-257">`--no-restore`-Proje oluşturma sırasında örtük bir geri yükleme yapın değil.</span><span class="sxs-lookup"><span data-stu-id="b5d40-257">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="b5d40-258">**mstest'i, xunit**</span><span class="sxs-lookup"><span data-stu-id="b5d40-258">**mstest, xunit**</span></span>

<span data-ttu-id="b5d40-259">`-p|--enable-pack`-Proje kullanma paketleme sağlar [dotnet paketi](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="b5d40-259">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="b5d40-260">`--no-restore`-Proje oluşturma sırasında örtük bir geri yükleme yapın değil.</span><span class="sxs-lookup"><span data-stu-id="b5d40-260">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="b5d40-261">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="b5d40-261">**globaljson**</span></span>

<span data-ttu-id="b5d40-262">`--sdk-version <VERSION_NUMBER>`-Kullanmak için .NET Core SDK sürümünü belirtir *global.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="b5d40-262">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="b5d40-263">**Web**</span><span class="sxs-lookup"><span data-stu-id="b5d40-263">**web**</span></span>

<span data-ttu-id="b5d40-264">`--use-launch-settings`-İçeren *launchSettings.json* oluşturulan şablon çıkışı.</span><span class="sxs-lookup"><span data-stu-id="b5d40-264">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="b5d40-265">`--no-restore`-Proje oluşturma sırasında örtük bir geri yükleme yapın değil.</span><span class="sxs-lookup"><span data-stu-id="b5d40-265">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="b5d40-266">**webapı**</span><span class="sxs-lookup"><span data-stu-id="b5d40-266">**webapi**</span></span>

<span data-ttu-id="b5d40-267">`-au|--auth <AUTHENTICATION_TYPE>`-Kullanılacak kimlik doğrulama türü.</span><span class="sxs-lookup"><span data-stu-id="b5d40-267">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="b5d40-268">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b5d40-268">The possible values are:</span></span>

- <span data-ttu-id="b5d40-269">`None`-Kimlik doğrulama yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="b5d40-269">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="b5d40-270">`IndividualB2C`-Azure AD B2C ile tek tek kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="b5d40-270">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="b5d40-271">`SingleOrg`-Tek bir kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="b5d40-271">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="b5d40-272">`Windows`-Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="b5d40-272">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="b5d40-273">`--aad-b2c-instance <INSTANCE>`-Bağlanmak için Azure Active Directory B2C örnek.</span><span class="sxs-lookup"><span data-stu-id="b5d40-273">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="b5d40-274">İle kullandığınız `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="b5d40-274">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="b5d40-275">Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b5d40-275">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="b5d40-276">`-ssp|--susi-policy-id <ID>`-Bu proje için oturum açma ve kaydolma ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="b5d40-276">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="b5d40-277">İle kullandığınız `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="b5d40-277">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b5d40-278">`--aad-instance <INSTANCE>`-Bağlanmak için Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="b5d40-278">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="b5d40-279">İle kullandığınız `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="b5d40-279">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="b5d40-280">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b5d40-280">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="b5d40-281">`--client-id <ID>`-Bu proje için istemci kimliği.</span><span class="sxs-lookup"><span data-stu-id="b5d40-281">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="b5d40-282">İle kullandığınız `IndividualB2C` veya `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="b5d40-282">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="b5d40-283">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b5d40-283">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="b5d40-284">`--domain <DOMAIN>`-Etki alanı için dizin Kiracı.</span><span class="sxs-lookup"><span data-stu-id="b5d40-284">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="b5d40-285">İle kullandığınız `SingleOrg` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="b5d40-285">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="b5d40-286">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b5d40-286">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="b5d40-287">`--tenant-id <ID>`-Tenantıd bağlanmak için kimliği dizini.</span><span class="sxs-lookup"><span data-stu-id="b5d40-287">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="b5d40-288">İle kullandığınız `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="b5d40-288">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="b5d40-289">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b5d40-289">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="b5d40-290">`-r|--org-read-access`-Bu uygulamanın dizine okuma erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b5d40-290">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="b5d40-291">Yalnızca uygular `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="b5d40-291">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="b5d40-292">`--use-launch-settings`-İçeren *launchSettings.json* oluşturulan şablon çıkışı.</span><span class="sxs-lookup"><span data-stu-id="b5d40-292">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="b5d40-293">`-uld|--use-local-db`-Yerel veritabanı yerine SQLite kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b5d40-293">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="b5d40-294">Yalnızca uygular `Individual` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="b5d40-294">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b5d40-295">`--no-restore`-Proje oluşturma sırasında örtük bir geri yükleme yapın değil.</span><span class="sxs-lookup"><span data-stu-id="b5d40-295">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="b5d40-296">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="b5d40-296">**mvc, razor**</span></span>

<span data-ttu-id="b5d40-297">`-au|--auth <AUTHENTICATION_TYPE>`-Kullanılacak kimlik doğrulama türü.</span><span class="sxs-lookup"><span data-stu-id="b5d40-297">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="b5d40-298">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b5d40-298">The possible values are:</span></span>

- <span data-ttu-id="b5d40-299">`None`-Kimlik doğrulama yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="b5d40-299">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="b5d40-300">`Individual`-Tek tek kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="b5d40-300">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="b5d40-301">`IndividualB2C`-Azure AD B2C ile tek tek kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="b5d40-301">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="b5d40-302">`SingleOrg`-Tek bir kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="b5d40-302">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="b5d40-303">`MultiOrg`-Birden çok Kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="b5d40-303">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="b5d40-304">`Windows`-Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="b5d40-304">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="b5d40-305">`--aad-b2c-instance <INSTANCE>`-Bağlanmak için Azure Active Directory B2C örnek.</span><span class="sxs-lookup"><span data-stu-id="b5d40-305">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="b5d40-306">İle kullandığınız `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="b5d40-306">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="b5d40-307">Varsayılan değer `https://login.microsoftonline.com/tfp/` .</span><span class="sxs-lookup"><span data-stu-id="b5d40-307">The default value is `https://login.microsoftonline.com/tfp/` .</span></span>

<span data-ttu-id="b5d40-308">`-ssp|--susi-policy-id <ID>`-Bu proje için oturum açma ve kaydolma ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="b5d40-308">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="b5d40-309">İle kullandığınız `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="b5d40-309">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b5d40-310">`-rp|--reset-password-policy-id <ID>`-Bu proje için reset parola ilkesi kimliği.</span><span class="sxs-lookup"><span data-stu-id="b5d40-310">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="b5d40-311">İle kullandığınız `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="b5d40-311">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b5d40-312">`-ep|--edit-profile-policy-id <ID>`-Bu proje için Düzenle profili ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="b5d40-312">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="b5d40-313">İle kullandığınız `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="b5d40-313">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b5d40-314">`--aad-instance <INSTANCE>`-Bağlanmak için Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="b5d40-314">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="b5d40-315">İle kullandığınız `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="b5d40-315">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="b5d40-316">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b5d40-316">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="b5d40-317">`--client-id <ID>`-Bu proje için istemci kimliği.</span><span class="sxs-lookup"><span data-stu-id="b5d40-317">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="b5d40-318">İle kullandığınız `IndividualB2C`, `SingleOrg`, veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="b5d40-318">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="b5d40-319">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b5d40-319">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="b5d40-320">`--domain <DOMAIN>`-Etki alanı için dizin Kiracı.</span><span class="sxs-lookup"><span data-stu-id="b5d40-320">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="b5d40-321">İle kullandığınız `SingleOrg` veya `IndividualB2C` kimlik doğrulaması...</span><span class="sxs-lookup"><span data-stu-id="b5d40-321">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="b5d40-322">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b5d40-322">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="b5d40-323">`--tenant-id <ID>`-Tenantıd bağlanmak için kimliği dizini.</span><span class="sxs-lookup"><span data-stu-id="b5d40-323">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="b5d40-324">İle kullandığınız `SingleOrg` kimlik doğrulaması...</span><span class="sxs-lookup"><span data-stu-id="b5d40-324">Use with `SingleOrg` authentication..</span></span> <span data-ttu-id="b5d40-325">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b5d40-325">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="b5d40-326">`--callback-path <PATH>`-Yeniden yönlendirme URI'si, uygulamanın taban yolu içindeki istek yolu.</span><span class="sxs-lookup"><span data-stu-id="b5d40-326">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="b5d40-327">İle kullandığınız `SingleOrg` veya `IndividualB2C` kimlik doğrulaması...</span><span class="sxs-lookup"><span data-stu-id="b5d40-327">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="b5d40-328">Varsayılan değer `/signin-oidc` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b5d40-328">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="b5d40-329">`-r|--org-read-access`-Bu uygulamanın dizine okuma erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b5d40-329">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="b5d40-330">Yalnızca uygular `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="b5d40-330">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="b5d40-331">`--use-launch-settings`-İçeren *launchSettings.json* oluşturulan şablon çıkışı.</span><span class="sxs-lookup"><span data-stu-id="b5d40-331">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="b5d40-332">`--use-browserlink`-BrowserLink projede içerir.</span><span class="sxs-lookup"><span data-stu-id="b5d40-332">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="b5d40-333">`-uld|--use-local-db`-Yerel veritabanı yerine SQLite kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b5d40-333">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="b5d40-334">Yalnızca uygular `Individual` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="b5d40-334">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b5d40-335">`--no-restore`-Proje oluşturma sırasında örtük bir geri yükleme yapın değil.</span><span class="sxs-lookup"><span data-stu-id="b5d40-335">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="b5d40-336">**Sayfa**</span><span class="sxs-lookup"><span data-stu-id="b5d40-336">**page**</span></span>

<span data-ttu-id="b5d40-337">`-na|--namespace <NAMESPACE_NAME>`-Namespace üretilen kod için.</span><span class="sxs-lookup"><span data-stu-id="b5d40-337">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="b5d40-338">Varsayılan değer `MyApp.Namespace` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b5d40-338">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="b5d40-339">`-np|--no-pagemodel`-Bir PageModel olmadan sayfası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b5d40-339">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="b5d40-340">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="b5d40-340">**viewimports**</span></span>

<span data-ttu-id="b5d40-341">`-na|--namespace <NAMESPACE_NAME>`-Namespace üretilen kod için.</span><span class="sxs-lookup"><span data-stu-id="b5d40-341">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="b5d40-342">Varsayılan değer `MyApp.Namespace` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b5d40-342">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="b5d40-343">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="b5d40-343">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="b5d40-344">**Konsolu, xunit, mstest'i, web, webapı**</span><span class="sxs-lookup"><span data-stu-id="b5d40-344">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="b5d40-345">`-f|--framework`-Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="b5d40-345">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="b5d40-346">Değerler: `netcoreapp1.0` veya `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="b5d40-346">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="b5d40-347">Varsayılan değer `netcoreapp1.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b5d40-347">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="b5d40-348">**ClassLib**</span><span class="sxs-lookup"><span data-stu-id="b5d40-348">**classlib**</span></span>

<span data-ttu-id="b5d40-349">`-f|--framework`-Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="b5d40-349">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="b5d40-350">Değerler: `netcoreapp1.0`, `netcoreapp1.1`, veya `netstandard1.0` için `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="b5d40-350">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="b5d40-351">Varsayılan değer `netstandard1.4` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b5d40-351">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="b5d40-352">**MVC**</span><span class="sxs-lookup"><span data-stu-id="b5d40-352">**mvc**</span></span>

<span data-ttu-id="b5d40-353">`-f|--framework`-Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="b5d40-353">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="b5d40-354">Değerler: `netcoreapp1.0` veya `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="b5d40-354">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="b5d40-355">Varsayılan değer `netcoreapp1.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b5d40-355">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="b5d40-356">`-au|--auth`-Kullanılacak kimlik doğrulama türü.</span><span class="sxs-lookup"><span data-stu-id="b5d40-356">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="b5d40-357">Değerler: `None` veya `Individual`.</span><span class="sxs-lookup"><span data-stu-id="b5d40-357">Values: `None` or `Individual`.</span></span> <span data-ttu-id="b5d40-358">Varsayılan değer `None` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b5d40-358">The default value is `None`.</span></span>

<span data-ttu-id="b5d40-359">`-uld|--use-local-db`-Yerel veritabanı yerine SQLite kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b5d40-359">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="b5d40-360">Değerler: `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="b5d40-360">Values: `true` or `false`.</span></span> <span data-ttu-id="b5d40-361">Varsayılan değer `false` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b5d40-361">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="b5d40-362">Örnekler</span><span class="sxs-lookup"><span data-stu-id="b5d40-362">Examples</span></span>

<span data-ttu-id="b5d40-363">Geçerli dizinde bir F # konsol uygulama projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="b5d40-363">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang f#`

<span data-ttu-id="b5d40-364">(Yalnızca .NET çekirdeği 2.0 SDK veya sonraki sürümleriyle kullanılabilir) belirtilen dizindeki .NET standart bir sınıf kitaplığı projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="b5d40-364">Create a .NET Standard class library project in the specified directory (available only with .NET Core 2.0 SDK or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="b5d40-365">Yeni bir ASP.NET Core C# MVC uygulama projesi geçerli dizinde kimlik doğrulamasız .NET Core 2.0 hedefleme oluşturun:</span><span class="sxs-lookup"><span data-stu-id="b5d40-365">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication targeting .NET Core 2.0:</span></span>

`dotnet new mvc -au None -f netcoreapp2.0`

<span data-ttu-id="b5d40-366">.NET Core 2.0 hedefleme yeni bir xUnit uygulaması oluşturun:</span><span class="sxs-lookup"><span data-stu-id="b5d40-366">Create a new xUnit application targeting .NET Core 2.0:</span></span>

`dotnet new xunit --framework netcoreapp2.0`

<span data-ttu-id="b5d40-367">MVC için kullanılabilir tüm şablonları listeler:</span><span class="sxs-lookup"><span data-stu-id="b5d40-367">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

## <a name="see-also"></a><span data-ttu-id="b5d40-368">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b5d40-368">See also</span></span>

[<span data-ttu-id="b5d40-369">Yeni dotnet için özel şablonlar</span><span class="sxs-lookup"><span data-stu-id="b5d40-369">Custom templates for dotnet new</span></span>](custom-templates.md)  
[<span data-ttu-id="b5d40-370">Dotnet new için özel şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="b5d40-370">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)  
[<span data-ttu-id="b5d40-371">DotNet/dotnet-şablonu-samples GitHub depo</span><span class="sxs-lookup"><span data-stu-id="b5d40-371">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)  
[<span data-ttu-id="b5d40-372">Yeni dotnet için kullanılabilir şablonlar</span><span class="sxs-lookup"><span data-stu-id="b5d40-372">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
