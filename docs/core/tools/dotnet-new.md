---
title: DotNet yeni komutu - .NET Core CLI
description: Dotnet yeni komut belirtilen şablona dayalı yeni .NET Core projelerini oluşturur.
author: mairaw
ms.author: mairaw
ms.date: 06/12/2018
ms.openlocfilehash: f0ef91361dfbc2c2ba5532fbd607786289e98c69
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208327"
---
# <a name="dotnet-new"></a><span data-ttu-id="e548b-103">DotNet yeni</span><span class="sxs-lookup"><span data-stu-id="e548b-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="e548b-104">Ad</span><span class="sxs-lookup"><span data-stu-id="e548b-104">Name</span></span>

<span data-ttu-id="e548b-105">`dotnet new` -Yeni Proje, yapılandırma dosyası veya belirtilen şablona dayalı çözüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e548b-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="e548b-106">Özet</span><span class="sxs-lookup"><span data-stu-id="e548b-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="e548b-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="e548b-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output]
    [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="e548b-108">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="e548b-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="e548b-109">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="e548b-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="e548b-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e548b-110">Description</span></span>

<span data-ttu-id="e548b-111">`dotnet new` Komutu geçerli bir .NET Core projeyi başlatmak için kolay bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="e548b-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="e548b-112">Komut çağrıları [şablon motoru](https://github.com/dotnet/templating) yapıları belirtilen şablonu ve seçenekleri bağlı disk oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="e548b-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="e548b-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="e548b-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="e548b-114">Komutu çağrıldığında örneği oluşturmak için şablon.</span><span class="sxs-lookup"><span data-stu-id="e548b-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="e548b-115">Her bir şablon geçirebilirsiniz belirli seçenekleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="e548b-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="e548b-116">Daha fazla bilgi için bkz: [şablon seçenekleri](#template-options).</span><span class="sxs-lookup"><span data-stu-id="e548b-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="e548b-117">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="e548b-117">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="e548b-118">Komut şablonlarının varsayılan listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="e548b-118">The command contains a default list of templates.</span></span> <span data-ttu-id="e548b-119">Kullanım `dotnet new -l` kullanılabilir şablonların listesini elde edilir.</span><span class="sxs-lookup"><span data-stu-id="e548b-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="e548b-120">Aşağıdaki tabloda, .NET Core SDK 2.1.300 önceden yüklenmiş olarak gelen şablonları gösterir.</span><span class="sxs-lookup"><span data-stu-id="e548b-120">The following table shows the templates that come pre-installed with the .NET Core SDK 2.1.300.</span></span> <span data-ttu-id="e548b-121">Şablon için varsayılan dili köşeli ayraçlar içinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e548b-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="e548b-122">Şablon açıklaması</span><span class="sxs-lookup"><span data-stu-id="e548b-122">Template description</span></span>                          | <span data-ttu-id="e548b-123">Şablon adı</span><span class="sxs-lookup"><span data-stu-id="e548b-123">Template name</span></span>   | <span data-ttu-id="e548b-124">Diller</span><span class="sxs-lookup"><span data-stu-id="e548b-124">Languages</span></span>     |
|----------------------------------------------|-----------------|---------------|
| <span data-ttu-id="e548b-125">Konsol uygulaması</span><span class="sxs-lookup"><span data-stu-id="e548b-125">Console application</span></span>                          | `console`       | <span data-ttu-id="e548b-126">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="e548b-126">[C#], F#, VB</span></span>  |
| <span data-ttu-id="e548b-127">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="e548b-127">Class library</span></span>                                | `classlib`      | <span data-ttu-id="e548b-128">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="e548b-128">[C#], F#, VB</span></span>  |
| <span data-ttu-id="e548b-129">Birim testi projesi</span><span class="sxs-lookup"><span data-stu-id="e548b-129">Unit test project</span></span>                            | `mstest`        | <span data-ttu-id="e548b-130">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="e548b-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="e548b-131">xUnit test projesi</span><span class="sxs-lookup"><span data-stu-id="e548b-131">xUnit test project</span></span>                           | `xunit`         | <span data-ttu-id="e548b-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="e548b-132">[C#], F#, VB</span></span>  |
| <span data-ttu-id="e548b-133">Razor sayfası</span><span class="sxs-lookup"><span data-stu-id="e548b-133">Razor page</span></span>                                   | `page`          | <span data-ttu-id="e548b-134">[C#]</span><span class="sxs-lookup"><span data-stu-id="e548b-134">[C#]</span></span>          |
| <span data-ttu-id="e548b-135">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="e548b-135">MVC ViewImports</span></span>                              | `viewimports`   | <span data-ttu-id="e548b-136">[C#]</span><span class="sxs-lookup"><span data-stu-id="e548b-136">[C#]</span></span>          |
| <span data-ttu-id="e548b-137">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="e548b-137">MVC ViewStart</span></span>                                | `viewstart`     | <span data-ttu-id="e548b-138">[C#]</span><span class="sxs-lookup"><span data-stu-id="e548b-138">[C#]</span></span>          |
| <span data-ttu-id="e548b-139">ASP.NET Core boş</span><span class="sxs-lookup"><span data-stu-id="e548b-139">ASP.NET Core empty</span></span>                           | `web`           | <span data-ttu-id="e548b-140">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="e548b-140">[C#], F#</span></span>      |
| <span data-ttu-id="e548b-141">ASP.NET Core Web uygulaması (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="e548b-141">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`           | <span data-ttu-id="e548b-142">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="e548b-142">[C#], F#</span></span>      |
| <span data-ttu-id="e548b-143">ASP.NET Core Web uygulaması</span><span class="sxs-lookup"><span data-stu-id="e548b-143">ASP.NET Core Web App</span></span>                         | `razor`         | <span data-ttu-id="e548b-144">[C#]</span><span class="sxs-lookup"><span data-stu-id="e548b-144">[C#]</span></span>          |
| <span data-ttu-id="e548b-145">ASP.NET Core Açısal ile</span><span class="sxs-lookup"><span data-stu-id="e548b-145">ASP.NET Core with Angular</span></span>                    | `angular`       | <span data-ttu-id="e548b-146">[C#]</span><span class="sxs-lookup"><span data-stu-id="e548b-146">[C#]</span></span>          |
| <span data-ttu-id="e548b-147">ASP.NET Core React.js ile</span><span class="sxs-lookup"><span data-stu-id="e548b-147">ASP.NET Core with React.js</span></span>                   | `react`         | <span data-ttu-id="e548b-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="e548b-148">[C#]</span></span>          |
| <span data-ttu-id="e548b-149">ASP.NET Core React.js ve Redux</span><span class="sxs-lookup"><span data-stu-id="e548b-149">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`    | <span data-ttu-id="e548b-150">[C#]</span><span class="sxs-lookup"><span data-stu-id="e548b-150">[C#]</span></span>          |
| <span data-ttu-id="e548b-151">ASP.NET Core Web API'si</span><span class="sxs-lookup"><span data-stu-id="e548b-151">ASP.NET Core Web API</span></span>                         | `webapi`        | <span data-ttu-id="e548b-152">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="e548b-152">[C#], F#</span></span>      |
| <span data-ttu-id="e548b-153">Razor sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="e548b-153">Razor class library</span></span>                          | `razorclasslib` | <span data-ttu-id="e548b-154">[C#]</span><span class="sxs-lookup"><span data-stu-id="e548b-154">[C#]</span></span>          |
| <span data-ttu-id="e548b-155">Global.JSON dosyası</span><span class="sxs-lookup"><span data-stu-id="e548b-155">global.json file</span></span>                             | `globaljson`    |               |
| <span data-ttu-id="e548b-156">NuGet yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e548b-156">NuGet config</span></span>                                 | `nugetconfig`   |               |
| <span data-ttu-id="e548b-157">Web yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e548b-157">Web config</span></span>                                   | `webconfig`     |               |
| <span data-ttu-id="e548b-158">Çözüm dosyası</span><span class="sxs-lookup"><span data-stu-id="e548b-158">Solution file</span></span>                                | `sln`           |               |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="e548b-159">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="e548b-159">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="e548b-160">Komut şablonlarının varsayılan listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="e548b-160">The command contains a default list of templates.</span></span> <span data-ttu-id="e548b-161">Kullanım `dotnet new -l` kullanılabilir şablonların listesini elde edilir.</span><span class="sxs-lookup"><span data-stu-id="e548b-161">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="e548b-162">Aşağıdaki tabloda, .NET Core SDK 2.0 ile önceden yüklenmiş olarak gelen şablonları gösterir.</span><span class="sxs-lookup"><span data-stu-id="e548b-162">The following table shows the templates that come pre-installed with the .NET Core SDK 2.0.</span></span> <span data-ttu-id="e548b-163">Şablon için varsayılan dili köşeli ayraçlar içinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e548b-163">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="e548b-164">Şablon açıklaması</span><span class="sxs-lookup"><span data-stu-id="e548b-164">Template description</span></span>                          | <span data-ttu-id="e548b-165">Şablon adı</span><span class="sxs-lookup"><span data-stu-id="e548b-165">Template name</span></span> | <span data-ttu-id="e548b-166">Diller</span><span class="sxs-lookup"><span data-stu-id="e548b-166">Languages</span></span>     |
|----------------------------------------------|---------------|---------------|
| <span data-ttu-id="e548b-167">Konsol uygulaması</span><span class="sxs-lookup"><span data-stu-id="e548b-167">Console application</span></span>                          | `console`     | <span data-ttu-id="e548b-168">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="e548b-168">[C#], F#, VB</span></span>  |
| <span data-ttu-id="e548b-169">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="e548b-169">Class library</span></span>                                | `classlib`    | <span data-ttu-id="e548b-170">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="e548b-170">[C#], F#, VB</span></span>  |
| <span data-ttu-id="e548b-171">Birim testi projesi</span><span class="sxs-lookup"><span data-stu-id="e548b-171">Unit test project</span></span>                            | `mstest`      | <span data-ttu-id="e548b-172">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="e548b-172">[C#], F#, VB</span></span>  |
| <span data-ttu-id="e548b-173">xUnit test projesi</span><span class="sxs-lookup"><span data-stu-id="e548b-173">xUnit test project</span></span>                           | `xunit`       | <span data-ttu-id="e548b-174">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="e548b-174">[C#], F#, VB</span></span>  |
| <span data-ttu-id="e548b-175">ASP.NET Core boş</span><span class="sxs-lookup"><span data-stu-id="e548b-175">ASP.NET Core empty</span></span>                           | `web`         | <span data-ttu-id="e548b-176">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="e548b-176">[C#], F#</span></span>      |
| <span data-ttu-id="e548b-177">ASP.NET Core Web uygulaması (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="e548b-177">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="e548b-178">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="e548b-178">[C#], F#</span></span>      |
| <span data-ttu-id="e548b-179">ASP.NET Core Web uygulaması</span><span class="sxs-lookup"><span data-stu-id="e548b-179">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="e548b-180">[C#]</span><span class="sxs-lookup"><span data-stu-id="e548b-180">[C#]</span></span>          |
| <span data-ttu-id="e548b-181">ASP.NET Core Açısal ile</span><span class="sxs-lookup"><span data-stu-id="e548b-181">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="e548b-182">[C#]</span><span class="sxs-lookup"><span data-stu-id="e548b-182">[C#]</span></span>          |
| <span data-ttu-id="e548b-183">ASP.NET Core React.js ile</span><span class="sxs-lookup"><span data-stu-id="e548b-183">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="e548b-184">[C#]</span><span class="sxs-lookup"><span data-stu-id="e548b-184">[C#]</span></span>          |
| <span data-ttu-id="e548b-185">ASP.NET Core React.js ve Redux</span><span class="sxs-lookup"><span data-stu-id="e548b-185">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="e548b-186">[C#]</span><span class="sxs-lookup"><span data-stu-id="e548b-186">[C#]</span></span>          |
| <span data-ttu-id="e548b-187">ASP.NET Core Web API'si</span><span class="sxs-lookup"><span data-stu-id="e548b-187">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="e548b-188">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="e548b-188">[C#], F#</span></span>      |
| <span data-ttu-id="e548b-189">Global.JSON dosyası</span><span class="sxs-lookup"><span data-stu-id="e548b-189">global.json file</span></span>                             | `globaljson`  |               |
| <span data-ttu-id="e548b-190">NuGet yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e548b-190">NuGet config</span></span>                                 | `nugetconfig` |               |
| <span data-ttu-id="e548b-191">Web yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e548b-191">Web config</span></span>                                   | `webconfig`   |               |
| <span data-ttu-id="e548b-192">Çözüm dosyası</span><span class="sxs-lookup"><span data-stu-id="e548b-192">Solution file</span></span>                                | `sln`         |               |
| <span data-ttu-id="e548b-193">Razor sayfası</span><span class="sxs-lookup"><span data-stu-id="e548b-193">Razor page</span></span>                                   | `page`        |               |
| <span data-ttu-id="e548b-194">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="e548b-194">MVC ViewImports</span></span>                              | `viewimports` |               |
| <span data-ttu-id="e548b-195">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="e548b-195">MVC ViewStart</span></span>                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="e548b-196">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="e548b-196">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="e548b-197">Komut şablonlarının varsayılan listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="e548b-197">The command contains a default list of templates.</span></span> <span data-ttu-id="e548b-198">Kullanım `dotnet new -all` kullanılabilir şablonların listesini elde edilir.</span><span class="sxs-lookup"><span data-stu-id="e548b-198">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="e548b-199">.NET Core SDK'sı ile önceden yüklenmiş olarak gelen şablonları aşağıdaki tabloda gösterilmektedir 1.x.</span><span class="sxs-lookup"><span data-stu-id="e548b-199">The following table shows the templates that come pre-installed with the .NET Core SDK 1.x.</span></span> <span data-ttu-id="e548b-200">Şablon için varsayılan dili köşeli ayraçlar içinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e548b-200">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="e548b-201">Şablon açıklaması</span><span class="sxs-lookup"><span data-stu-id="e548b-201">Template description</span></span>  | <span data-ttu-id="e548b-202">Şablon adı</span><span class="sxs-lookup"><span data-stu-id="e548b-202">Template name</span></span> | <span data-ttu-id="e548b-203">Diller</span><span class="sxs-lookup"><span data-stu-id="e548b-203">Languages</span></span> |
|----------------------|---------------|-----------|
| <span data-ttu-id="e548b-204">Konsol uygulaması</span><span class="sxs-lookup"><span data-stu-id="e548b-204">Console application</span></span>  | `console`     | <span data-ttu-id="e548b-205">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="e548b-205">[C#], F#</span></span>  |
| <span data-ttu-id="e548b-206">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="e548b-206">Class library</span></span>        | `classlib`    | <span data-ttu-id="e548b-207">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="e548b-207">[C#], F#</span></span>  |
| <span data-ttu-id="e548b-208">Birim testi projesi</span><span class="sxs-lookup"><span data-stu-id="e548b-208">Unit test project</span></span>    | `mstest`      | <span data-ttu-id="e548b-209">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="e548b-209">[C#], F#</span></span>  |
| <span data-ttu-id="e548b-210">xUnit test projesi</span><span class="sxs-lookup"><span data-stu-id="e548b-210">xUnit test project</span></span>   | `xunit`       | <span data-ttu-id="e548b-211">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="e548b-211">[C#], F#</span></span>  |
| <span data-ttu-id="e548b-212">ASP.NET Core boş</span><span class="sxs-lookup"><span data-stu-id="e548b-212">ASP.NET Core empty</span></span>   | `web`         | <span data-ttu-id="e548b-213">[C#]</span><span class="sxs-lookup"><span data-stu-id="e548b-213">[C#]</span></span>      |
| <span data-ttu-id="e548b-214">ASP.NET Core Web uygulaması</span><span class="sxs-lookup"><span data-stu-id="e548b-214">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="e548b-215">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="e548b-215">[C#], F#</span></span>  |
| <span data-ttu-id="e548b-216">ASP.NET Core Web API'si</span><span class="sxs-lookup"><span data-stu-id="e548b-216">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="e548b-217">[C#]</span><span class="sxs-lookup"><span data-stu-id="e548b-217">[C#]</span></span>      |
| <span data-ttu-id="e548b-218">NuGet yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e548b-218">NuGet config</span></span>         | `nugetconfig` |           |
| <span data-ttu-id="e548b-219">Web yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e548b-219">Web config</span></span>           | `webconfig`   |           |
| <span data-ttu-id="e548b-220">Çözüm dosyası</span><span class="sxs-lookup"><span data-stu-id="e548b-220">Solution file</span></span>        | `sln`         |           |

---

## <a name="options"></a><span data-ttu-id="e548b-221">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="e548b-221">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="e548b-222">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="e548b-222">.NET Core 2.1</span></span>](#tab/netcore21)

`--force`

<span data-ttu-id="e548b-223">Var olan dosyaları değişeceğinden olsa bile oluşturulacak içeriği zorlar.</span><span class="sxs-lookup"><span data-stu-id="e548b-223">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="e548b-224">Çıktı dizini bir proje zaten içeriyor, bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e548b-224">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="e548b-225">Komut için Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="e548b-225">Prints out help for the command.</span></span> <span data-ttu-id="e548b-226">İçin çağrılabilir `dotnet new` kendisini komut veya herhangi bir şablonu gibi `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="e548b-226">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="e548b-227">Bir kaynak veya şablon paketinden yükler `PATH` veya `NUGET_ID` sağlanan.</span><span class="sxs-lookup"><span data-stu-id="e548b-227">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="e548b-228">Bir şablon paketini bir ön sürümünü yüklemek istiyorsanız, sürüm biçiminde belirtmeniz gerekir `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="e548b-228">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="e548b-229">Varsayılan olarak, `dotnet new` geçirir \* sürümü için temsil eden en son kararlı Paket sürümü.</span><span class="sxs-lookup"><span data-stu-id="e548b-229">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="e548b-230">Bir örneğe bakın [örnekler](#examples) bölümü.</span><span class="sxs-lookup"><span data-stu-id="e548b-230">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="e548b-231">Özel şablonlar oluşturma hakkında daha fazla bilgi için bkz: [yeni dotnet için özel şablonlar](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="e548b-231">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="e548b-232">Belirtilen ad içeren şablonlarını listeler.</span><span class="sxs-lookup"><span data-stu-id="e548b-232">Lists templates containing the specified name.</span></span> <span data-ttu-id="e548b-233">İçin başlatılırsa `dotnet new` komutu için belirtilen dizin kullanılabilir olası şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="e548b-233">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="e548b-234">Örneğin dizini zaten bir proje içeriyorsa, tüm proje şablonları listesinde değil.</span><span class="sxs-lookup"><span data-stu-id="e548b-234">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="e548b-235">Oluşturmak için şablon dili.</span><span class="sxs-lookup"><span data-stu-id="e548b-235">The language of the template to create.</span></span> <span data-ttu-id="e548b-236">Dil kabul değişir şablon tarafından (varsayılan ayarlarında bkz [bağımsız değişkenleri](#arguments) bölümü).</span><span class="sxs-lookup"><span data-stu-id="e548b-236">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="e548b-237">Bazı şablonlar için geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="e548b-237">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="e548b-238">Bazı Kabukları yorumlama `#` bir özel karakter olarak.</span><span class="sxs-lookup"><span data-stu-id="e548b-238">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="e548b-239">Bu gibi durumlarda dil parametre değeri, aşağıdaki gibi alın gerek `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="e548b-239">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="e548b-240">Oluşturulan çıktı adı.</span><span class="sxs-lookup"><span data-stu-id="e548b-240">The name for the created output.</span></span> <span data-ttu-id="e548b-241">Ad belirtilmezse, geçerli dizin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e548b-241">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="e548b-242">Yükleme sırasında kullanılacak bir NuGet kaynağı belirtir.</span><span class="sxs-lookup"><span data-stu-id="e548b-242">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="e548b-243">Oluşturulan çıktı yerleştirileceği konum.</span><span class="sxs-lookup"><span data-stu-id="e548b-243">Location to place the generated output.</span></span> <span data-ttu-id="e548b-244">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="e548b-244">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="e548b-245">Şablonlar kullanılabilir türlerine göre filtreler.</span><span class="sxs-lookup"><span data-stu-id="e548b-245">Filters templates based on available types.</span></span> <span data-ttu-id="e548b-246">Önceden tanımlanmış değerler "proje", "öğesi" veya "diğer" olabilir.</span><span class="sxs-lookup"><span data-stu-id="e548b-246">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="e548b-247">Bir kaynak veya şablon paketini kaldırır `PATH` veya `NUGET_ID` sağlanan.</span><span class="sxs-lookup"><span data-stu-id="e548b-247">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="e548b-248">Bir şablon kullanarak kaldırmak için bir `PATH`, yolun tam olarak nitelemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="e548b-248">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="e548b-249">Örneğin, *C:/Users/\<kullanıcı > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* çalışır, ancak *./GarciaSoftware.ConsoleTemplate.CSharp* içeren gelen Klasör almayacak.</span><span class="sxs-lookup"><span data-stu-id="e548b-249">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="e548b-250">Ayrıca, şablonu yoldaki son sonlandırma dizin eğik çizgi eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="e548b-250">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="e548b-251">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="e548b-251">.NET Core 2.0</span></span>](#tab/netcore20)

`--force`

<span data-ttu-id="e548b-252">Var olan dosyaları değişeceğinden olsa bile oluşturulacak içeriği zorlar.</span><span class="sxs-lookup"><span data-stu-id="e548b-252">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="e548b-253">Çıktı dizini bir proje zaten içeriyor, bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e548b-253">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="e548b-254">Komut için Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="e548b-254">Prints out help for the command.</span></span> <span data-ttu-id="e548b-255">İçin çağrılabilir `dotnet new` kendisini komut veya herhangi bir şablonu gibi `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="e548b-255">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="e548b-256">Bir kaynak veya şablon paketinden yükler `PATH` veya `NUGET_ID` sağlanan.</span><span class="sxs-lookup"><span data-stu-id="e548b-256">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="e548b-257">Bir şablon paketini bir ön sürümünü yüklemek istiyorsanız, sürüm biçiminde belirtmeniz gerekir `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="e548b-257">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="e548b-258">Varsayılan olarak, `dotnet new` geçirir \* sürümü için temsil eden en son kararlı Paket sürümü.</span><span class="sxs-lookup"><span data-stu-id="e548b-258">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="e548b-259">Bir örneğe bakın [örnekler](#examples) bölümü.</span><span class="sxs-lookup"><span data-stu-id="e548b-259">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="e548b-260">Özel şablonlar oluşturma hakkında daha fazla bilgi için bkz: [yeni dotnet için özel şablonlar](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="e548b-260">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="e548b-261">Belirtilen ad içeren şablonlarını listeler.</span><span class="sxs-lookup"><span data-stu-id="e548b-261">Lists templates containing the specified name.</span></span> <span data-ttu-id="e548b-262">İçin başlatılırsa `dotnet new` komutu için belirtilen dizin kullanılabilir olası şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="e548b-262">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="e548b-263">Örneğin dizini zaten bir proje içeriyorsa, tüm proje şablonları listesinde değil.</span><span class="sxs-lookup"><span data-stu-id="e548b-263">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="e548b-264">Oluşturmak için şablon dili.</span><span class="sxs-lookup"><span data-stu-id="e548b-264">The language of the template to create.</span></span> <span data-ttu-id="e548b-265">Dil kabul değişir şablon tarafından (varsayılan ayarlarında bkz [bağımsız değişkenleri](#arguments) bölümü).</span><span class="sxs-lookup"><span data-stu-id="e548b-265">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="e548b-266">Bazı şablonlar için geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="e548b-266">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="e548b-267">Bazı Kabukları yorumlama `#` bir özel karakter olarak.</span><span class="sxs-lookup"><span data-stu-id="e548b-267">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="e548b-268">Bu gibi durumlarda dil parametre değeri, aşağıdaki gibi alın gerek `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="e548b-268">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="e548b-269">Oluşturulan çıktı adı.</span><span class="sxs-lookup"><span data-stu-id="e548b-269">The name for the created output.</span></span> <span data-ttu-id="e548b-270">Ad belirtilmezse, geçerli dizin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e548b-270">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="e548b-271">Oluşturulan çıktı yerleştirileceği konum.</span><span class="sxs-lookup"><span data-stu-id="e548b-271">Location to place the generated output.</span></span> <span data-ttu-id="e548b-272">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="e548b-272">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="e548b-273">Şablonlar kullanılabilir türlerine göre filtreler.</span><span class="sxs-lookup"><span data-stu-id="e548b-273">Filters templates based on available types.</span></span> <span data-ttu-id="e548b-274">Önceden tanımlanmış değerler "proje", "öğesi" veya "diğer" olabilir.</span><span class="sxs-lookup"><span data-stu-id="e548b-274">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="e548b-275">Bir kaynak veya şablon paketini kaldırır `PATH` veya `NUGET_ID` sağlanan.</span><span class="sxs-lookup"><span data-stu-id="e548b-275">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="e548b-276">Bir şablon kullanarak kaldırmak için bir `PATH`, yolun tam olarak nitelemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="e548b-276">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="e548b-277">Örneğin, *C:/Users/\<kullanıcı > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* çalışır, ancak *./GarciaSoftware.ConsoleTemplate.CSharp* içeren gelen Klasör almayacak.</span><span class="sxs-lookup"><span data-stu-id="e548b-277">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="e548b-278">Ayrıca, şablonu yoldaki son sonlandırma dizin eğik çizgi eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="e548b-278">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="e548b-279">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="e548b-279">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="e548b-280">Belirli bir proje türü için tüm şablonları bağlamında çalışırken gösterir `dotnet new` tek başına komutu.</span><span class="sxs-lookup"><span data-stu-id="e548b-280">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="e548b-281">Belirli bir şablon bağlamda gibi çalıştırırken `dotnet new web -all`, `-all` zorla oluşturma bayrak olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="e548b-281">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="e548b-282">Çıktı dizini bir proje zaten içeriyor, bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e548b-282">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="e548b-283">Komut için Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="e548b-283">Prints out help for the command.</span></span> <span data-ttu-id="e548b-284">İçin çağrılabilir `dotnet new` kendisini komut veya herhangi bir şablonu gibi `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="e548b-284">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="e548b-285">Belirtilen ad içeren şablonlarını listeler.</span><span class="sxs-lookup"><span data-stu-id="e548b-285">Lists templates containing the specified name.</span></span> <span data-ttu-id="e548b-286">İçin başlatılırsa `dotnet new` komutu için belirtilen dizin kullanılabilir olası şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="e548b-286">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="e548b-287">Örneğin dizini zaten bir proje içeriyorsa, tüm proje şablonları listesinde değil.</span><span class="sxs-lookup"><span data-stu-id="e548b-287">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="e548b-288">Oluşturmak için şablon dili.</span><span class="sxs-lookup"><span data-stu-id="e548b-288">The language of the template to create.</span></span> <span data-ttu-id="e548b-289">Dil kabul değişir şablon tarafından (varsayılan ayarlarında bkz [bağımsız değişkenleri](#arguments) bölümü).</span><span class="sxs-lookup"><span data-stu-id="e548b-289">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="e548b-290">Bazı şablonlar için geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="e548b-290">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="e548b-291">Bazı Kabukları yorumlama `#` bir özel karakter olarak.</span><span class="sxs-lookup"><span data-stu-id="e548b-291">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="e548b-292">Bu gibi durumlarda dil parametre değeri, aşağıdaki gibi alın gerek `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="e548b-292">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="e548b-293">Oluşturulan çıktı adı.</span><span class="sxs-lookup"><span data-stu-id="e548b-293">The name for the created output.</span></span> <span data-ttu-id="e548b-294">Ad belirtilmezse, geçerli dizin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e548b-294">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="e548b-295">Oluşturulan çıktı yerleştirileceği konum.</span><span class="sxs-lookup"><span data-stu-id="e548b-295">Location to place the generated output.</span></span> <span data-ttu-id="e548b-296">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="e548b-296">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="e548b-297">Şablon seçenekleri</span><span class="sxs-lookup"><span data-stu-id="e548b-297">Template options</span></span>

<span data-ttu-id="e548b-298">Her proje şablonu ek seçenekleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="e548b-298">Each project template may have additional options available.</span></span> <span data-ttu-id="e548b-299">Çekirdek şablonları aşağıdaki ek seçeneklere sahip olursunuz:</span><span class="sxs-lookup"><span data-stu-id="e548b-299">The core templates have the following additional options:</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="e548b-300">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="e548b-300">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="e548b-301">**konsolunda, Açısal tepki, reactredux, razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="e548b-301">**console, angular, react, reactredux, razorclasslib**</span></span>

  <span data-ttu-id="e548b-302">`--no-restore` -Proje oluşturma sırasında örtük bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="e548b-302">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="e548b-303">**ClassLib**</span><span class="sxs-lookup"><span data-stu-id="e548b-303">**classlib**</span></span>

<span data-ttu-id="e548b-304">`-f|--framework <FRAMEWORK>` -Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="e548b-304">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="e548b-305">Değerler: `netcoreapp2.0` .NET çekirdek sınıf kitaplığı oluşturmak için veya `netstandard2.0` .NET standart sınıf kitaplığı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="e548b-305">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="e548b-306">Varsayılan değer `netstandard2.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="e548b-306">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="e548b-307">`--no-restore` -Proje oluşturma sırasında örtük bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="e548b-307">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="e548b-308">**mstest'i, xunit**</span><span class="sxs-lookup"><span data-stu-id="e548b-308">**mstest, xunit**</span></span>

<span data-ttu-id="e548b-309">`-p|--enable-pack` -Proje kullanma paketleme sağlar [dotnet paketi](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="e548b-309">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="e548b-310">`--no-restore` -Proje oluşturma sırasında örtük bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="e548b-310">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="e548b-311">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="e548b-311">**globaljson**</span></span>

<span data-ttu-id="e548b-312">`--sdk-version <VERSION_NUMBER>` -Kullanmak için .NET Core SDK sürümünü belirtir *global.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="e548b-312">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="e548b-313">**Web**</span><span class="sxs-lookup"><span data-stu-id="e548b-313">**web**</span></span>

<span data-ttu-id="e548b-314">`--use-launch-settings` -İçeren *launchSettings.json* oluşturulan şablon çıkışı.</span><span class="sxs-lookup"><span data-stu-id="e548b-314">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="e548b-315">`--no-restore` -Proje oluşturma sırasında örtük bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="e548b-315">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="e548b-316">**webapı**</span><span class="sxs-lookup"><span data-stu-id="e548b-316">**webapi**</span></span>

<span data-ttu-id="e548b-317">`-au|--auth <AUTHENTICATION_TYPE>` -Kullanılacak kimlik doğrulama türü.</span><span class="sxs-lookup"><span data-stu-id="e548b-317">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="e548b-318">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e548b-318">The possible values are:</span></span>

- <span data-ttu-id="e548b-319">`None` -Kimlik doğrulama yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="e548b-319">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="e548b-320">`IndividualB2C` -Azure AD B2C ile tek tek kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e548b-320">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="e548b-321">`SingleOrg` -Tek bir kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e548b-321">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="e548b-322">`Windows` -Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e548b-322">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="e548b-323">`--aad-b2c-instance <INSTANCE>` -Bağlanmak için Azure Active Directory B2C örnek.</span><span class="sxs-lookup"><span data-stu-id="e548b-323">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="e548b-324">İle kullandığınız `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e548b-324">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="e548b-325">Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="e548b-325">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="e548b-326">`-ssp|--susi-policy-id <ID>` -Bu proje için oturum açma ve kaydolma ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="e548b-326">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="e548b-327">İle kullandığınız `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e548b-327">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="e548b-328">`--aad-instance <INSTANCE>` -Bağlanmak için Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="e548b-328">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="e548b-329">İle kullandığınız `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e548b-329">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="e548b-330">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="e548b-330">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="e548b-331">`--client-id <ID>` -Bu proje için istemci kimliği.</span><span class="sxs-lookup"><span data-stu-id="e548b-331">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="e548b-332">İle kullandığınız `IndividualB2C` veya `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e548b-332">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="e548b-333">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="e548b-333">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="e548b-334">`--domain <DOMAIN>` -Etki alanı için dizin Kiracı.</span><span class="sxs-lookup"><span data-stu-id="e548b-334">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="e548b-335">İle kullandığınız `SingleOrg` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e548b-335">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="e548b-336">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="e548b-336">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="e548b-337">`--tenant-id <ID>` -Tenantıd bağlanmak için kimliği dizini.</span><span class="sxs-lookup"><span data-stu-id="e548b-337">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="e548b-338">İle kullandığınız `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e548b-338">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="e548b-339">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="e548b-339">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="e548b-340">`-r|--org-read-access` -Bu uygulamanın dizine okuma erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e548b-340">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="e548b-341">Yalnızca uygular `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e548b-341">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="e548b-342">`--use-launch-settings` -İçeren *launchSettings.json* oluşturulan şablon çıkışı.</span><span class="sxs-lookup"><span data-stu-id="e548b-342">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="e548b-343">`-uld|--use-local-db` -Yerel veritabanı yerine SQLite kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e548b-343">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="e548b-344">Yalnızca uygular `Individual` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e548b-344">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="e548b-345">`--no-restore` -Proje oluşturma sırasında örtük bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="e548b-345">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="e548b-346">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="e548b-346">**mvc, razor**</span></span>

<span data-ttu-id="e548b-347">`-au|--auth <AUTHENTICATION_TYPE>` -Kullanılacak kimlik doğrulama türü.</span><span class="sxs-lookup"><span data-stu-id="e548b-347">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="e548b-348">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e548b-348">The possible values are:</span></span>

- <span data-ttu-id="e548b-349">`None` -Kimlik doğrulama yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="e548b-349">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="e548b-350">`Individual` -Tek tek kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e548b-350">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="e548b-351">`IndividualB2C` -Azure AD B2C ile tek tek kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e548b-351">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="e548b-352">`SingleOrg` -Tek bir kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e548b-352">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="e548b-353">`MultiOrg` -Birden çok Kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e548b-353">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="e548b-354">`Windows` -Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e548b-354">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="e548b-355">`--aad-b2c-instance <INSTANCE>` -Bağlanmak için Azure Active Directory B2C örnek.</span><span class="sxs-lookup"><span data-stu-id="e548b-355">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="e548b-356">İle kullandığınız `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e548b-356">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="e548b-357">Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="e548b-357">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="e548b-358">`-ssp|--susi-policy-id <ID>` -Bu proje için oturum açma ve kaydolma ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="e548b-358">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="e548b-359">İle kullandığınız `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e548b-359">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="e548b-360">`-rp|--reset-password-policy-id <ID>` -Bu proje için reset parola ilkesi kimliği.</span><span class="sxs-lookup"><span data-stu-id="e548b-360">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="e548b-361">İle kullandığınız `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e548b-361">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="e548b-362">`-ep|--edit-profile-policy-id <ID>` -Bu proje için Düzenle profili ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="e548b-362">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="e548b-363">İle kullandığınız `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e548b-363">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="e548b-364">`--aad-instance <INSTANCE>` -Bağlanmak için Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="e548b-364">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="e548b-365">İle kullandığınız `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e548b-365">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="e548b-366">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="e548b-366">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="e548b-367">`--client-id <ID>` -Bu proje için istemci kimliği.</span><span class="sxs-lookup"><span data-stu-id="e548b-367">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="e548b-368">İle kullandığınız `IndividualB2C`, `SingleOrg`, veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e548b-368">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="e548b-369">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="e548b-369">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="e548b-370">`--domain <DOMAIN>` -Etki alanı için dizin Kiracı.</span><span class="sxs-lookup"><span data-stu-id="e548b-370">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="e548b-371">İle kullandığınız `SingleOrg` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e548b-371">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="e548b-372">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="e548b-372">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="e548b-373">`--tenant-id <ID>` -Tenantıd bağlanmak için kimliği dizini.</span><span class="sxs-lookup"><span data-stu-id="e548b-373">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="e548b-374">İle kullandığınız `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e548b-374">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="e548b-375">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="e548b-375">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="e548b-376">`--callback-path <PATH>` -Yeniden yönlendirme URI'si, uygulamanın taban yolu içindeki istek yolu.</span><span class="sxs-lookup"><span data-stu-id="e548b-376">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="e548b-377">İle kullandığınız `SingleOrg` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e548b-377">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="e548b-378">Varsayılan değer `/signin-oidc` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="e548b-378">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="e548b-379">`-r|--org-read-access` -Bu uygulamanın dizine okuma erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e548b-379">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="e548b-380">Yalnızca uygular `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e548b-380">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="e548b-381">`--use-launch-settings` -İçeren *launchSettings.json* oluşturulan şablon çıkışı.</span><span class="sxs-lookup"><span data-stu-id="e548b-381">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="e548b-382">`--use-browserlink` -BrowserLink projede içerir.</span><span class="sxs-lookup"><span data-stu-id="e548b-382">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="e548b-383">`-uld|--use-local-db` -Yerel veritabanı yerine SQLite kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e548b-383">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="e548b-384">Yalnızca uygular `Individual` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e548b-384">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="e548b-385">`--no-restore` -Proje oluşturma sırasında örtük bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="e548b-385">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="e548b-386">**Sayfa**</span><span class="sxs-lookup"><span data-stu-id="e548b-386">**page**</span></span>

<span data-ttu-id="e548b-387">`-na|--namespace <NAMESPACE_NAME>`-Namespace üretilen kod için.</span><span class="sxs-lookup"><span data-stu-id="e548b-387">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="e548b-388">Varsayılan değer `MyApp.Namespace` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="e548b-388">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="e548b-389">`-np|--no-pagemodel` -Bir PageModel olmadan sayfası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e548b-389">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="e548b-390">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="e548b-390">**viewimports**</span></span>

<span data-ttu-id="e548b-391">`-na|--namespace <NAMESPACE_NAME>`-Namespace üretilen kod için.</span><span class="sxs-lookup"><span data-stu-id="e548b-391">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="e548b-392">Varsayılan değer `MyApp.Namespace` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="e548b-392">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="e548b-393">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="e548b-393">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="e548b-394">**konsolunda, Açısal, tepki, reactredux**</span><span class="sxs-lookup"><span data-stu-id="e548b-394">**console, angular, react, reactredux**</span></span>

  <span data-ttu-id="e548b-395">`--no-restore` -Proje oluşturma sırasında örtük bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="e548b-395">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="e548b-396">**ClassLib**</span><span class="sxs-lookup"><span data-stu-id="e548b-396">**classlib**</span></span>

<span data-ttu-id="e548b-397">`-f|--framework <FRAMEWORK>` -Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="e548b-397">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="e548b-398">Değerler: `netcoreapp2.0` .NET çekirdek sınıf kitaplığı oluşturmak için veya `netstandard2.0` .NET standart sınıf kitaplığı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="e548b-398">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="e548b-399">Varsayılan değer `netstandard2.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="e548b-399">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="e548b-400">`--no-restore` -Proje oluşturma sırasında örtük bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="e548b-400">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="e548b-401">**mstest'i, xunit**</span><span class="sxs-lookup"><span data-stu-id="e548b-401">**mstest, xunit**</span></span>

<span data-ttu-id="e548b-402">`-p|--enable-pack` -Proje kullanma paketleme sağlar [dotnet paketi](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="e548b-402">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="e548b-403">`--no-restore` -Proje oluşturma sırasında örtük bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="e548b-403">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="e548b-404">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="e548b-404">**globaljson**</span></span>

<span data-ttu-id="e548b-405">`--sdk-version <VERSION_NUMBER>` -Kullanmak için .NET Core SDK sürümünü belirtir *global.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="e548b-405">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="e548b-406">**Web**</span><span class="sxs-lookup"><span data-stu-id="e548b-406">**web**</span></span>

<span data-ttu-id="e548b-407">`--use-launch-settings` -İçeren *launchSettings.json* oluşturulan şablon çıkışı.</span><span class="sxs-lookup"><span data-stu-id="e548b-407">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="e548b-408">`--no-restore` -Proje oluşturma sırasında örtük bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="e548b-408">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="e548b-409">**webapı**</span><span class="sxs-lookup"><span data-stu-id="e548b-409">**webapi**</span></span>

<span data-ttu-id="e548b-410">`-au|--auth <AUTHENTICATION_TYPE>` -Kullanılacak kimlik doğrulama türü.</span><span class="sxs-lookup"><span data-stu-id="e548b-410">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="e548b-411">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e548b-411">The possible values are:</span></span>

- <span data-ttu-id="e548b-412">`None` -Kimlik doğrulama yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="e548b-412">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="e548b-413">`IndividualB2C` -Azure AD B2C ile tek tek kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e548b-413">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="e548b-414">`SingleOrg` -Tek bir kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e548b-414">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="e548b-415">`Windows` -Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e548b-415">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="e548b-416">`--aad-b2c-instance <INSTANCE>` -Bağlanmak için Azure Active Directory B2C örnek.</span><span class="sxs-lookup"><span data-stu-id="e548b-416">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="e548b-417">İle kullandığınız `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e548b-417">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="e548b-418">Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="e548b-418">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="e548b-419">`-ssp|--susi-policy-id <ID>` -Bu proje için oturum açma ve kaydolma ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="e548b-419">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="e548b-420">İle kullandığınız `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e548b-420">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="e548b-421">`--aad-instance <INSTANCE>` -Bağlanmak için Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="e548b-421">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="e548b-422">İle kullandığınız `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e548b-422">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="e548b-423">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="e548b-423">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="e548b-424">`--client-id <ID>` -Bu proje için istemci kimliği.</span><span class="sxs-lookup"><span data-stu-id="e548b-424">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="e548b-425">İle kullandığınız `IndividualB2C` veya `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e548b-425">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="e548b-426">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="e548b-426">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="e548b-427">`--domain <DOMAIN>` -Etki alanı için dizin Kiracı.</span><span class="sxs-lookup"><span data-stu-id="e548b-427">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="e548b-428">İle kullandığınız `SingleOrg` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e548b-428">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="e548b-429">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="e548b-429">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="e548b-430">`--tenant-id <ID>` -Tenantıd bağlanmak için kimliği dizini.</span><span class="sxs-lookup"><span data-stu-id="e548b-430">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="e548b-431">İle kullandığınız `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e548b-431">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="e548b-432">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="e548b-432">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="e548b-433">`-r|--org-read-access` -Bu uygulamanın dizine okuma erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e548b-433">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="e548b-434">Yalnızca uygular `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e548b-434">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="e548b-435">`--use-launch-settings` -İçeren *launchSettings.json* oluşturulan şablon çıkışı.</span><span class="sxs-lookup"><span data-stu-id="e548b-435">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="e548b-436">`-uld|--use-local-db` -Yerel veritabanı yerine SQLite kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e548b-436">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="e548b-437">Yalnızca uygular `Individual` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e548b-437">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="e548b-438">`--no-restore` -Proje oluşturma sırasında örtük bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="e548b-438">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="e548b-439">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="e548b-439">**mvc, razor**</span></span>

<span data-ttu-id="e548b-440">`-au|--auth <AUTHENTICATION_TYPE>` -Kullanılacak kimlik doğrulama türü.</span><span class="sxs-lookup"><span data-stu-id="e548b-440">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="e548b-441">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e548b-441">The possible values are:</span></span>

- <span data-ttu-id="e548b-442">`None` -Kimlik doğrulama yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="e548b-442">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="e548b-443">`Individual` -Tek tek kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e548b-443">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="e548b-444">`IndividualB2C` -Azure AD B2C ile tek tek kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e548b-444">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="e548b-445">`SingleOrg` -Tek bir kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e548b-445">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="e548b-446">`MultiOrg` -Birden çok Kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e548b-446">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="e548b-447">`Windows` -Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e548b-447">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="e548b-448">`--aad-b2c-instance <INSTANCE>` -Bağlanmak için Azure Active Directory B2C örnek.</span><span class="sxs-lookup"><span data-stu-id="e548b-448">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="e548b-449">İle kullandığınız `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e548b-449">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="e548b-450">Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="e548b-450">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="e548b-451">`-ssp|--susi-policy-id <ID>` -Bu proje için oturum açma ve kaydolma ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="e548b-451">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="e548b-452">İle kullandığınız `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e548b-452">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="e548b-453">`-rp|--reset-password-policy-id <ID>` -Bu proje için reset parola ilkesi kimliği.</span><span class="sxs-lookup"><span data-stu-id="e548b-453">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="e548b-454">İle kullandığınız `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e548b-454">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="e548b-455">`-ep|--edit-profile-policy-id <ID>` -Bu proje için Düzenle profili ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="e548b-455">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="e548b-456">İle kullandığınız `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e548b-456">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="e548b-457">`--aad-instance <INSTANCE>` -Bağlanmak için Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="e548b-457">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="e548b-458">İle kullandığınız `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e548b-458">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="e548b-459">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="e548b-459">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="e548b-460">`--client-id <ID>` -Bu proje için istemci kimliği.</span><span class="sxs-lookup"><span data-stu-id="e548b-460">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="e548b-461">İle kullandığınız `IndividualB2C`, `SingleOrg`, veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e548b-461">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="e548b-462">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="e548b-462">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="e548b-463">`--domain <DOMAIN>` -Etki alanı için dizin Kiracı.</span><span class="sxs-lookup"><span data-stu-id="e548b-463">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="e548b-464">İle kullandığınız `SingleOrg` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e548b-464">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="e548b-465">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="e548b-465">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="e548b-466">`--tenant-id <ID>` -Tenantıd bağlanmak için kimliği dizini.</span><span class="sxs-lookup"><span data-stu-id="e548b-466">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="e548b-467">İle kullandığınız `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e548b-467">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="e548b-468">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="e548b-468">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="e548b-469">`--callback-path <PATH>` -Yeniden yönlendirme URI'si, uygulamanın taban yolu içindeki istek yolu.</span><span class="sxs-lookup"><span data-stu-id="e548b-469">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="e548b-470">İle kullandığınız `SingleOrg` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e548b-470">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="e548b-471">Varsayılan değer `/signin-oidc` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="e548b-471">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="e548b-472">`-r|--org-read-access` -Bu uygulamanın dizine okuma erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e548b-472">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="e548b-473">Yalnızca uygular `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e548b-473">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="e548b-474">`--use-launch-settings` -İçeren *launchSettings.json* oluşturulan şablon çıkışı.</span><span class="sxs-lookup"><span data-stu-id="e548b-474">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="e548b-475">`--use-browserlink` -BrowserLink projede içerir.</span><span class="sxs-lookup"><span data-stu-id="e548b-475">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="e548b-476">`-uld|--use-local-db` -Yerel veritabanı yerine SQLite kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e548b-476">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="e548b-477">Yalnızca uygular `Individual` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e548b-477">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="e548b-478">`--no-restore` -Proje oluşturma sırasında örtük bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="e548b-478">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="e548b-479">**Sayfa**</span><span class="sxs-lookup"><span data-stu-id="e548b-479">**page**</span></span>

<span data-ttu-id="e548b-480">`-na|--namespace <NAMESPACE_NAME>`-Namespace üretilen kod için.</span><span class="sxs-lookup"><span data-stu-id="e548b-480">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="e548b-481">Varsayılan değer `MyApp.Namespace` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="e548b-481">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="e548b-482">`-np|--no-pagemodel` -Bir PageModel olmadan sayfası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e548b-482">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="e548b-483">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="e548b-483">**viewimports**</span></span>

<span data-ttu-id="e548b-484">`-na|--namespace <NAMESPACE_NAME>`-Namespace üretilen kod için.</span><span class="sxs-lookup"><span data-stu-id="e548b-484">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="e548b-485">Varsayılan değer `MyApp.Namespace` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="e548b-485">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="e548b-486">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="e548b-486">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="e548b-487">**Konsolu, xunit, mstest'i, web, webapı**</span><span class="sxs-lookup"><span data-stu-id="e548b-487">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="e548b-488">`-f|--framework` -Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="e548b-488">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="e548b-489">Değerler: `netcoreapp1.0` veya `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="e548b-489">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="e548b-490">Varsayılan değer `netcoreapp1.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="e548b-490">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="e548b-491">**ClassLib**</span><span class="sxs-lookup"><span data-stu-id="e548b-491">**classlib**</span></span>

<span data-ttu-id="e548b-492">`-f|--framework` -Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="e548b-492">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="e548b-493">Değerler: `netcoreapp1.0`, `netcoreapp1.1`, veya `netstandard1.0` için `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="e548b-493">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="e548b-494">Varsayılan değer `netstandard1.4` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="e548b-494">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="e548b-495">**mvc**</span><span class="sxs-lookup"><span data-stu-id="e548b-495">**mvc**</span></span>

<span data-ttu-id="e548b-496">`-f|--framework` -Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="e548b-496">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="e548b-497">Değerler: `netcoreapp1.0` veya `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="e548b-497">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="e548b-498">Varsayılan değer `netcoreapp1.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="e548b-498">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="e548b-499">`-au|--auth` -Kullanılacak kimlik doğrulama türü.</span><span class="sxs-lookup"><span data-stu-id="e548b-499">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="e548b-500">Değerler: `None` veya `Individual`.</span><span class="sxs-lookup"><span data-stu-id="e548b-500">Values: `None` or `Individual`.</span></span> <span data-ttu-id="e548b-501">Varsayılan değer `None` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="e548b-501">The default value is `None`.</span></span>

<span data-ttu-id="e548b-502">`-uld|--use-local-db` -Yerel veritabanı yerine SQLite kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e548b-502">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="e548b-503">Değerler: `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="e548b-503">Values: `true` or `false`.</span></span> <span data-ttu-id="e548b-504">Varsayılan değer `false` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="e548b-504">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="e548b-505">Örnekler</span><span class="sxs-lookup"><span data-stu-id="e548b-505">Examples</span></span>

<span data-ttu-id="e548b-506">Geçerli dizinde bir F # konsol uygulama projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="e548b-506">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="e548b-507">(Yalnızca .NET Core SDK 2.0 veya sonraki sürümleriyle kullanılabilir) belirtilen dizindeki .NET standart bir sınıf kitaplığı projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="e548b-507">Create a .NET Standard class library project in the specified directory (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="e548b-508">Geçerli dizinde hiçbir kimlik doğrulama ile yeni bir ASP.NET Core C# MVC uygulama projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="e548b-508">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication:</span></span>

`dotnet new mvc -au None`

<span data-ttu-id="e548b-509">Yeni bir xUnit uygulaması oluşturun:</span><span class="sxs-lookup"><span data-stu-id="e548b-509">Create a new xUnit application:</span></span>

`dotnet new xunit`

<span data-ttu-id="e548b-510">MVC için kullanılabilir tüm şablonları listeler:</span><span class="sxs-lookup"><span data-stu-id="e548b-510">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="e548b-511">ASP.NET Core (komut seçeneği kullanılabilir .NET Core SDK 1.1 ve sonraki sürümler için) için tek sayfa uygulaması şablonlarının 2.0 sürümünü yükleyin:</span><span class="sxs-lookup"><span data-stu-id="e548b-511">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

<span data-ttu-id="e548b-512">Oluşturma bir *global.json* SDK sürümü 2.0.0 (yalnızca .NET Core SDK 2.0 veya sonraki sürümleriyle kullanılabilir) ayarı geçerli dizinde:</span><span class="sxs-lookup"><span data-stu-id="e548b-512">Create a *global.json* in the current directory setting the SDK version to 2.0.0 (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="e548b-513">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e548b-513">See also</span></span>

[<span data-ttu-id="e548b-514">Yeni dotnet için özel şablonlar</span><span class="sxs-lookup"><span data-stu-id="e548b-514">Custom templates for dotnet new</span></span>](custom-templates.md)  
[<span data-ttu-id="e548b-515">Dotnet new için özel şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="e548b-515">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)  
[<span data-ttu-id="e548b-516">DotNet/dotnet-şablonu-samples GitHub depo</span><span class="sxs-lookup"><span data-stu-id="e548b-516">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)  
[<span data-ttu-id="e548b-517">Yeni dotnet için kullanılabilir şablonlar</span><span class="sxs-lookup"><span data-stu-id="e548b-517">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
