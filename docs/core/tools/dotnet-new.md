---
title: DotNet yeni komutu - .NET Core CLI
description: Dotnet yeni komut belirtilen şablona dayalı yeni .NET Core projelerini oluşturur.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: ae24c4145cc67ca863c07e4d22af8a1c2c2dd732
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34570469"
---
# <a name="dotnet-new"></a><span data-ttu-id="5a039-103">DotNet yeni</span><span class="sxs-lookup"><span data-stu-id="5a039-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="5a039-104">Ad</span><span class="sxs-lookup"><span data-stu-id="5a039-104">Name</span></span>

<span data-ttu-id="5a039-105">`dotnet new` -Yeni Proje, yapılandırma dosyası veya belirtilen şablona dayalı çözüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5a039-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5a039-106">Özet</span><span class="sxs-lookup"><span data-stu-id="5a039-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="5a039-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="5a039-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output]
    [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="5a039-108">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="5a039-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="5a039-109">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="5a039-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="5a039-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5a039-110">Description</span></span>

<span data-ttu-id="5a039-111">`dotnet new` Komutu geçerli bir .NET Core projeyi başlatmak için kolay bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="5a039-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="5a039-112">Komut çağrıları [şablon motoru](https://github.com/dotnet/templating) yapıları belirtilen şablonu ve seçenekleri bağlı disk oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="5a039-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="5a039-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="5a039-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="5a039-114">Komutu çağrıldığında örneği oluşturmak için şablon.</span><span class="sxs-lookup"><span data-stu-id="5a039-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="5a039-115">Her bir şablon geçirebilirsiniz belirli seçenekleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="5a039-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="5a039-116">Daha fazla bilgi için bkz: [şablon seçenekleri](#template-options).</span><span class="sxs-lookup"><span data-stu-id="5a039-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="5a039-117">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="5a039-117">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="5a039-118">Komut şablonlarının varsayılan listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="5a039-118">The command contains a default list of templates.</span></span> <span data-ttu-id="5a039-119">Kullanım `dotnet new -l` kullanılabilir şablonların listesini elde edilir.</span><span class="sxs-lookup"><span data-stu-id="5a039-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="5a039-120">Aşağıdaki tabloda, .NET Core SDK 2.1.300 önceden yüklenmiş olarak gelen şablonları gösterir.</span><span class="sxs-lookup"><span data-stu-id="5a039-120">The following table shows the templates that come pre-installed with the .NET Core SDK 2.1.300.</span></span> <span data-ttu-id="5a039-121">Şablon için varsayılan dili köşeli ayraçlar içinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5a039-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="5a039-122">Şablon açıklaması</span><span class="sxs-lookup"><span data-stu-id="5a039-122">Template description</span></span>                          | <span data-ttu-id="5a039-123">Şablon adı</span><span class="sxs-lookup"><span data-stu-id="5a039-123">Template name</span></span>   | <span data-ttu-id="5a039-124">Diller</span><span class="sxs-lookup"><span data-stu-id="5a039-124">Languages</span></span>     |
|----------------------------------------------|-----------------|---------------|
| <span data-ttu-id="5a039-125">Konsol uygulaması</span><span class="sxs-lookup"><span data-stu-id="5a039-125">Console application</span></span>                          | `console`       | <span data-ttu-id="5a039-126">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="5a039-126">[C#], F#, VB</span></span>  |
| <span data-ttu-id="5a039-127">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="5a039-127">Class library</span></span>                                | `classlib`      | <span data-ttu-id="5a039-128">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="5a039-128">[C#], F#, VB</span></span>  |
| <span data-ttu-id="5a039-129">Birim testi projesi</span><span class="sxs-lookup"><span data-stu-id="5a039-129">Unit test project</span></span>                            | `mstest`        | <span data-ttu-id="5a039-130">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="5a039-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="5a039-131">xUnit test projesi</span><span class="sxs-lookup"><span data-stu-id="5a039-131">xUnit test project</span></span>                           | `xunit`         | <span data-ttu-id="5a039-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="5a039-132">[C#], F#, VB</span></span>  |
| <span data-ttu-id="5a039-133">Razor sayfası</span><span class="sxs-lookup"><span data-stu-id="5a039-133">Razor page</span></span>                                   | `page`          | <span data-ttu-id="5a039-134">[C#]</span><span class="sxs-lookup"><span data-stu-id="5a039-134">[C#]</span></span>          |
| <span data-ttu-id="5a039-135">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="5a039-135">MVC ViewImports</span></span>                              | `viewimports`   | <span data-ttu-id="5a039-136">[C#]</span><span class="sxs-lookup"><span data-stu-id="5a039-136">[C#]</span></span>          |
| <span data-ttu-id="5a039-137">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="5a039-137">MVC ViewStart</span></span>                                | `viewstart`     | <span data-ttu-id="5a039-138">[C#]</span><span class="sxs-lookup"><span data-stu-id="5a039-138">[C#]</span></span>          |
| <span data-ttu-id="5a039-139">ASP.NET Core boş</span><span class="sxs-lookup"><span data-stu-id="5a039-139">ASP.NET Core empty</span></span>                           | `web`           | <span data-ttu-id="5a039-140">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="5a039-140">[C#], F#</span></span>      |
| <span data-ttu-id="5a039-141">ASP.NET Core Web uygulaması (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="5a039-141">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`           | <span data-ttu-id="5a039-142">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="5a039-142">[C#], F#</span></span>      |
| <span data-ttu-id="5a039-143">ASP.NET Core Web uygulaması</span><span class="sxs-lookup"><span data-stu-id="5a039-143">ASP.NET Core Web App</span></span>                         | `razor`         | <span data-ttu-id="5a039-144">[C#]</span><span class="sxs-lookup"><span data-stu-id="5a039-144">[C#]</span></span>          |
| <span data-ttu-id="5a039-145">ASP.NET Core Açısal ile</span><span class="sxs-lookup"><span data-stu-id="5a039-145">ASP.NET Core with Angular</span></span>                    | `angular`       | <span data-ttu-id="5a039-146">[C#]</span><span class="sxs-lookup"><span data-stu-id="5a039-146">[C#]</span></span>          |
| <span data-ttu-id="5a039-147">ASP.NET Core React.js ile</span><span class="sxs-lookup"><span data-stu-id="5a039-147">ASP.NET Core with React.js</span></span>                   | `react`         | <span data-ttu-id="5a039-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="5a039-148">[C#]</span></span>          |
| <span data-ttu-id="5a039-149">ASP.NET Core React.js ve Redux</span><span class="sxs-lookup"><span data-stu-id="5a039-149">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`    | <span data-ttu-id="5a039-150">[C#]</span><span class="sxs-lookup"><span data-stu-id="5a039-150">[C#]</span></span>          |
| <span data-ttu-id="5a039-151">ASP.NET Core Web API'si</span><span class="sxs-lookup"><span data-stu-id="5a039-151">ASP.NET Core Web API</span></span>                         | `webapi`        | <span data-ttu-id="5a039-152">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="5a039-152">[C#], F#</span></span>      |
| <span data-ttu-id="5a039-153">Razor sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="5a039-153">Razor class library</span></span>                          | `razorclasslib` | <span data-ttu-id="5a039-154">[C#]</span><span class="sxs-lookup"><span data-stu-id="5a039-154">[C#]</span></span>          |
| <span data-ttu-id="5a039-155">Global.JSON dosyası</span><span class="sxs-lookup"><span data-stu-id="5a039-155">global.json file</span></span>                             | `globaljson`    |               |
| <span data-ttu-id="5a039-156">NuGet yapılandırma</span><span class="sxs-lookup"><span data-stu-id="5a039-156">NuGet config</span></span>                                 | `nugetconfig`   |               |
| <span data-ttu-id="5a039-157">Web yapılandırma</span><span class="sxs-lookup"><span data-stu-id="5a039-157">Web config</span></span>                                   | `webconfig`     |               |
| <span data-ttu-id="5a039-158">Çözüm dosyası</span><span class="sxs-lookup"><span data-stu-id="5a039-158">Solution file</span></span>                                | `sln`           |               |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="5a039-159">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="5a039-159">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="5a039-160">Komut şablonlarının varsayılan listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="5a039-160">The command contains a default list of templates.</span></span> <span data-ttu-id="5a039-161">Kullanım `dotnet new -l` kullanılabilir şablonların listesini elde edilir.</span><span class="sxs-lookup"><span data-stu-id="5a039-161">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="5a039-162">Aşağıdaki tabloda, .NET Core SDK 2.0 ile önceden yüklenmiş olarak gelen şablonları gösterir.</span><span class="sxs-lookup"><span data-stu-id="5a039-162">The following table shows the templates that come pre-installed with the .NET Core SDK 2.0.</span></span> <span data-ttu-id="5a039-163">Şablon için varsayılan dili köşeli ayraçlar içinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5a039-163">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="5a039-164">Şablon açıklaması</span><span class="sxs-lookup"><span data-stu-id="5a039-164">Template description</span></span>                          | <span data-ttu-id="5a039-165">Şablon adı</span><span class="sxs-lookup"><span data-stu-id="5a039-165">Template name</span></span> | <span data-ttu-id="5a039-166">Diller</span><span class="sxs-lookup"><span data-stu-id="5a039-166">Languages</span></span>     |
|----------------------------------------------|---------------|---------------|
| <span data-ttu-id="5a039-167">Konsol uygulaması</span><span class="sxs-lookup"><span data-stu-id="5a039-167">Console application</span></span>                          | `console`     | <span data-ttu-id="5a039-168">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="5a039-168">[C#], F#, VB</span></span>  |
| <span data-ttu-id="5a039-169">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="5a039-169">Class library</span></span>                                | `classlib`    | <span data-ttu-id="5a039-170">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="5a039-170">[C#], F#, VB</span></span>  |
| <span data-ttu-id="5a039-171">Birim testi projesi</span><span class="sxs-lookup"><span data-stu-id="5a039-171">Unit test project</span></span>                            | `mstest`      | <span data-ttu-id="5a039-172">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="5a039-172">[C#], F#, VB</span></span>  |
| <span data-ttu-id="5a039-173">xUnit test projesi</span><span class="sxs-lookup"><span data-stu-id="5a039-173">xUnit test project</span></span>                           | `xunit`       | <span data-ttu-id="5a039-174">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="5a039-174">[C#], F#, VB</span></span>  |
| <span data-ttu-id="5a039-175">ASP.NET Core boş</span><span class="sxs-lookup"><span data-stu-id="5a039-175">ASP.NET Core empty</span></span>                           | `web`         | <span data-ttu-id="5a039-176">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="5a039-176">[C#], F#</span></span>      |
| <span data-ttu-id="5a039-177">ASP.NET Core Web uygulaması (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="5a039-177">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="5a039-178">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="5a039-178">[C#], F#</span></span>      |
| <span data-ttu-id="5a039-179">ASP.NET Core Web uygulaması</span><span class="sxs-lookup"><span data-stu-id="5a039-179">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="5a039-180">[C#]</span><span class="sxs-lookup"><span data-stu-id="5a039-180">[C#]</span></span>          |
| <span data-ttu-id="5a039-181">ASP.NET Core Açısal ile</span><span class="sxs-lookup"><span data-stu-id="5a039-181">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="5a039-182">[C#]</span><span class="sxs-lookup"><span data-stu-id="5a039-182">[C#]</span></span>          |
| <span data-ttu-id="5a039-183">ASP.NET Core React.js ile</span><span class="sxs-lookup"><span data-stu-id="5a039-183">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="5a039-184">[C#]</span><span class="sxs-lookup"><span data-stu-id="5a039-184">[C#]</span></span>          |
| <span data-ttu-id="5a039-185">ASP.NET Core React.js ve Redux</span><span class="sxs-lookup"><span data-stu-id="5a039-185">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="5a039-186">[C#]</span><span class="sxs-lookup"><span data-stu-id="5a039-186">[C#]</span></span>          |
| <span data-ttu-id="5a039-187">ASP.NET Core Web API'si</span><span class="sxs-lookup"><span data-stu-id="5a039-187">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="5a039-188">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="5a039-188">[C#], F#</span></span>      |
| <span data-ttu-id="5a039-189">Global.JSON dosyası</span><span class="sxs-lookup"><span data-stu-id="5a039-189">global.json file</span></span>                             | `globaljson`  |               |
| <span data-ttu-id="5a039-190">NuGet yapılandırma</span><span class="sxs-lookup"><span data-stu-id="5a039-190">NuGet config</span></span>                                 | `nugetconfig` |               |
| <span data-ttu-id="5a039-191">Web yapılandırma</span><span class="sxs-lookup"><span data-stu-id="5a039-191">Web config</span></span>                                   | `webconfig`   |               |
| <span data-ttu-id="5a039-192">Çözüm dosyası</span><span class="sxs-lookup"><span data-stu-id="5a039-192">Solution file</span></span>                                | `sln`         |               |
| <span data-ttu-id="5a039-193">Razor sayfası</span><span class="sxs-lookup"><span data-stu-id="5a039-193">Razor page</span></span>                                   | `page`        |               |
| <span data-ttu-id="5a039-194">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="5a039-194">MVC ViewImports</span></span>                              | `viewimports` |               |
| <span data-ttu-id="5a039-195">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="5a039-195">MVC ViewStart</span></span>                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="5a039-196">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="5a039-196">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="5a039-197">Komut şablonlarının varsayılan listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="5a039-197">The command contains a default list of templates.</span></span> <span data-ttu-id="5a039-198">Kullanım `dotnet new -all` kullanılabilir şablonların listesini elde edilir.</span><span class="sxs-lookup"><span data-stu-id="5a039-198">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="5a039-199">.NET Core SDK'sı ile önceden yüklenmiş olarak gelen şablonları aşağıdaki tabloda gösterilmektedir 1.x.</span><span class="sxs-lookup"><span data-stu-id="5a039-199">The following table shows the templates that come pre-installed with the .NET Core SDK 1.x.</span></span> <span data-ttu-id="5a039-200">Şablon için varsayılan dili köşeli ayraçlar içinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5a039-200">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="5a039-201">Şablon açıklaması</span><span class="sxs-lookup"><span data-stu-id="5a039-201">Template description</span></span>  | <span data-ttu-id="5a039-202">Şablon adı</span><span class="sxs-lookup"><span data-stu-id="5a039-202">Template name</span></span> | <span data-ttu-id="5a039-203">Diller</span><span class="sxs-lookup"><span data-stu-id="5a039-203">Languages</span></span> |
|----------------------|---------------|-----------|
| <span data-ttu-id="5a039-204">Konsol uygulaması</span><span class="sxs-lookup"><span data-stu-id="5a039-204">Console application</span></span>  | `console`     | <span data-ttu-id="5a039-205">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="5a039-205">[C#], F#</span></span>  |
| <span data-ttu-id="5a039-206">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="5a039-206">Class library</span></span>        | `classlib`    | <span data-ttu-id="5a039-207">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="5a039-207">[C#], F#</span></span>  |
| <span data-ttu-id="5a039-208">Birim testi projesi</span><span class="sxs-lookup"><span data-stu-id="5a039-208">Unit test project</span></span>    | `mstest`      | <span data-ttu-id="5a039-209">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="5a039-209">[C#], F#</span></span>  |
| <span data-ttu-id="5a039-210">xUnit test projesi</span><span class="sxs-lookup"><span data-stu-id="5a039-210">xUnit test project</span></span>   | `xunit`       | <span data-ttu-id="5a039-211">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="5a039-211">[C#], F#</span></span>  |
| <span data-ttu-id="5a039-212">ASP.NET Core boş</span><span class="sxs-lookup"><span data-stu-id="5a039-212">ASP.NET Core empty</span></span>   | `web`         | <span data-ttu-id="5a039-213">[C#]</span><span class="sxs-lookup"><span data-stu-id="5a039-213">[C#]</span></span>      |
| <span data-ttu-id="5a039-214">ASP.NET Core Web uygulaması</span><span class="sxs-lookup"><span data-stu-id="5a039-214">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="5a039-215">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="5a039-215">[C#], F#</span></span>  |
| <span data-ttu-id="5a039-216">ASP.NET Core Web API'si</span><span class="sxs-lookup"><span data-stu-id="5a039-216">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="5a039-217">[C#]</span><span class="sxs-lookup"><span data-stu-id="5a039-217">[C#]</span></span>      |
| <span data-ttu-id="5a039-218">NuGet yapılandırma</span><span class="sxs-lookup"><span data-stu-id="5a039-218">NuGet config</span></span>         | `nugetconfig` |           |
| <span data-ttu-id="5a039-219">Web yapılandırma</span><span class="sxs-lookup"><span data-stu-id="5a039-219">Web config</span></span>           | `webconfig`   |           |
| <span data-ttu-id="5a039-220">Çözüm dosyası</span><span class="sxs-lookup"><span data-stu-id="5a039-220">Solution file</span></span>        | `sln`         |           |

---

## <a name="options"></a><span data-ttu-id="5a039-221">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="5a039-221">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="5a039-222">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="5a039-222">.NET Core 2.1</span></span>](#tab/netcore21)

`--force`

<span data-ttu-id="5a039-223">Var olan dosyaları değişeceğinden olsa bile oluşturulacak içeriği zorlar.</span><span class="sxs-lookup"><span data-stu-id="5a039-223">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="5a039-224">Çıktı dizini bir proje zaten içeriyor, bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5a039-224">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="5a039-225">Komut için Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="5a039-225">Prints out help for the command.</span></span> <span data-ttu-id="5a039-226">İçin çağrılabilir `dotnet new` kendisini komut veya herhangi bir şablonu gibi `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="5a039-226">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="5a039-227">Bir kaynak veya şablon paketinden yükler `PATH` veya `NUGET_ID` sağlanan.</span><span class="sxs-lookup"><span data-stu-id="5a039-227">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="5a039-228">Bir şablon paketini bir ön sürümünü yüklemek istiyorsanız, sürüm biçiminde belirtmeniz gerekir `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="5a039-228">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="5a039-229">Varsayılan olarak, `dotnet new` geçirir \* sürümü için temsil eden en son kararlı Paket sürümü.</span><span class="sxs-lookup"><span data-stu-id="5a039-229">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="5a039-230">Bir örneğe bakın [örnekler](#examples) bölümü.</span><span class="sxs-lookup"><span data-stu-id="5a039-230">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="5a039-231">Özel şablonlar oluşturma hakkında daha fazla bilgi için bkz: [yeni dotnet için özel şablonlar](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="5a039-231">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="5a039-232">Belirtilen ad içeren şablonlarını listeler.</span><span class="sxs-lookup"><span data-stu-id="5a039-232">Lists templates containing the specified name.</span></span> <span data-ttu-id="5a039-233">İçin başlatılırsa `dotnet new` komutu için belirtilen dizin kullanılabilir olası şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="5a039-233">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="5a039-234">Örneğin dizini zaten bir proje içeriyorsa, tüm proje şablonları listesinde değil.</span><span class="sxs-lookup"><span data-stu-id="5a039-234">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="5a039-235">Oluşturmak için şablon dili.</span><span class="sxs-lookup"><span data-stu-id="5a039-235">The language of the template to create.</span></span> <span data-ttu-id="5a039-236">Dil kabul değişir şablon tarafından (varsayılan ayarlarında bkz [bağımsız değişkenleri](#arguments) bölümü).</span><span class="sxs-lookup"><span data-stu-id="5a039-236">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="5a039-237">Bazı şablonlar için geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="5a039-237">Not valid for some templates.</span></span>

    > [!NOTE]
    > Some shells interpret `#` as a special character. In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="5a039-238">Oluşturulan çıktı adı.</span><span class="sxs-lookup"><span data-stu-id="5a039-238">The name for the created output.</span></span> <span data-ttu-id="5a039-239">Ad belirtilmezse, geçerli dizin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5a039-239">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="5a039-240">Yükleme sırasında kullanılacak bir NuGet kaynağı belirtir.</span><span class="sxs-lookup"><span data-stu-id="5a039-240">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="5a039-241">Oluşturulan çıktı yerleştirileceği konum.</span><span class="sxs-lookup"><span data-stu-id="5a039-241">Location to place the generated output.</span></span> <span data-ttu-id="5a039-242">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="5a039-242">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="5a039-243">Şablonlar kullanılabilir türlerine göre filtreler.</span><span class="sxs-lookup"><span data-stu-id="5a039-243">Filters templates based on available types.</span></span> <span data-ttu-id="5a039-244">Önceden tanımlanmış değerler "proje", "öğesi" veya "diğer" olabilir.</span><span class="sxs-lookup"><span data-stu-id="5a039-244">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="5a039-245">Bir kaynak veya şablon paketini kaldırır `PATH` veya `NUGET_ID` sağlanan.</span><span class="sxs-lookup"><span data-stu-id="5a039-245">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="5a039-246">Bir şablon kullanarak kaldırmak için bir `PATH`, yolun tam olarak nitelemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="5a039-246">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="5a039-247">Örneğin, *C:/Users/\<kullanıcı > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* çalışır, ancak *./GarciaSoftware.ConsoleTemplate.CSharp* içeren gelen Klasör almayacak.</span><span class="sxs-lookup"><span data-stu-id="5a039-247">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="5a039-248">Ayrıca, şablonu yoldaki son sonlandırma dizin eğik çizgi eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="5a039-248">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="5a039-249">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="5a039-249">.NET Core 2.0</span></span>](#tab/netcore20)

`--force`

<span data-ttu-id="5a039-250">Var olan dosyaları değişeceğinden olsa bile oluşturulacak içeriği zorlar.</span><span class="sxs-lookup"><span data-stu-id="5a039-250">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="5a039-251">Çıktı dizini bir proje zaten içeriyor, bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5a039-251">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="5a039-252">Komut için Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="5a039-252">Prints out help for the command.</span></span> <span data-ttu-id="5a039-253">İçin çağrılabilir `dotnet new` kendisini komut veya herhangi bir şablonu gibi `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="5a039-253">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="5a039-254">Bir kaynak veya şablon paketinden yükler `PATH` veya `NUGET_ID` sağlanan.</span><span class="sxs-lookup"><span data-stu-id="5a039-254">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="5a039-255">Bir şablon paketini bir ön sürümünü yüklemek istiyorsanız, sürüm biçiminde belirtmeniz gerekir `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="5a039-255">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="5a039-256">Varsayılan olarak, `dotnet new` geçirir \* sürümü için temsil eden en son kararlı Paket sürümü.</span><span class="sxs-lookup"><span data-stu-id="5a039-256">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="5a039-257">Bir örneğe bakın [örnekler](#examples) bölümü.</span><span class="sxs-lookup"><span data-stu-id="5a039-257">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="5a039-258">Özel şablonlar oluşturma hakkında daha fazla bilgi için bkz: [yeni dotnet için özel şablonlar](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="5a039-258">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="5a039-259">Belirtilen ad içeren şablonlarını listeler.</span><span class="sxs-lookup"><span data-stu-id="5a039-259">Lists templates containing the specified name.</span></span> <span data-ttu-id="5a039-260">İçin başlatılırsa `dotnet new` komutu için belirtilen dizin kullanılabilir olası şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="5a039-260">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="5a039-261">Örneğin dizini zaten bir proje içeriyorsa, tüm proje şablonları listesinde değil.</span><span class="sxs-lookup"><span data-stu-id="5a039-261">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="5a039-262">Oluşturmak için şablon dili.</span><span class="sxs-lookup"><span data-stu-id="5a039-262">The language of the template to create.</span></span> <span data-ttu-id="5a039-263">Dil kabul değişir şablon tarafından (varsayılan ayarlarında bkz [bağımsız değişkenleri](#arguments) bölümü).</span><span class="sxs-lookup"><span data-stu-id="5a039-263">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="5a039-264">Bazı şablonlar için geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="5a039-264">Not valid for some templates.</span></span>

    > [!NOTE]
    > Some shells interpret `#` as a special character. In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="5a039-265">Oluşturulan çıktı adı.</span><span class="sxs-lookup"><span data-stu-id="5a039-265">The name for the created output.</span></span> <span data-ttu-id="5a039-266">Ad belirtilmezse, geçerli dizin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5a039-266">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="5a039-267">Oluşturulan çıktı yerleştirileceği konum.</span><span class="sxs-lookup"><span data-stu-id="5a039-267">Location to place the generated output.</span></span> <span data-ttu-id="5a039-268">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="5a039-268">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="5a039-269">Şablonlar kullanılabilir türlerine göre filtreler.</span><span class="sxs-lookup"><span data-stu-id="5a039-269">Filters templates based on available types.</span></span> <span data-ttu-id="5a039-270">Önceden tanımlanmış değerler "proje", "öğesi" veya "diğer" olabilir.</span><span class="sxs-lookup"><span data-stu-id="5a039-270">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="5a039-271">Bir kaynak veya şablon paketini kaldırır `PATH` veya `NUGET_ID` sağlanan.</span><span class="sxs-lookup"><span data-stu-id="5a039-271">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="5a039-272">Bir şablon kullanarak kaldırmak için bir `PATH`, yolun tam olarak nitelemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="5a039-272">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="5a039-273">Örneğin, *C:/Users/\<kullanıcı > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* çalışır, ancak *./GarciaSoftware.ConsoleTemplate.CSharp* içeren gelen Klasör almayacak.</span><span class="sxs-lookup"><span data-stu-id="5a039-273">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="5a039-274">Ayrıca, şablonu yoldaki son sonlandırma dizin eğik çizgi eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="5a039-274">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="5a039-275">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="5a039-275">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="5a039-276">Belirli bir proje türü için tüm şablonları bağlamında çalışırken gösterir `dotnet new` tek başına komutu.</span><span class="sxs-lookup"><span data-stu-id="5a039-276">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="5a039-277">Belirli bir şablon bağlamda gibi çalıştırırken `dotnet new web -all`, `-all` zorla oluşturma bayrak olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="5a039-277">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="5a039-278">Çıktı dizini bir proje zaten içeriyor, bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5a039-278">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="5a039-279">Komut için Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="5a039-279">Prints out help for the command.</span></span> <span data-ttu-id="5a039-280">İçin çağrılabilir `dotnet new` kendisini komut veya herhangi bir şablonu gibi `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="5a039-280">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="5a039-281">Belirtilen ad içeren şablonlarını listeler.</span><span class="sxs-lookup"><span data-stu-id="5a039-281">Lists templates containing the specified name.</span></span> <span data-ttu-id="5a039-282">İçin başlatılırsa `dotnet new` komutu için belirtilen dizin kullanılabilir olası şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="5a039-282">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="5a039-283">Örneğin dizini zaten bir proje içeriyorsa, tüm proje şablonları listesinde değil.</span><span class="sxs-lookup"><span data-stu-id="5a039-283">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="5a039-284">Oluşturmak için şablon dili.</span><span class="sxs-lookup"><span data-stu-id="5a039-284">The language of the template to create.</span></span> <span data-ttu-id="5a039-285">Dil kabul değişir şablon tarafından (varsayılan ayarlarında bkz [bağımsız değişkenleri](#arguments) bölümü).</span><span class="sxs-lookup"><span data-stu-id="5a039-285">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="5a039-286">Bazı şablonlar için geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="5a039-286">Not valid for some templates.</span></span>

    > [!NOTE]
    > Some shells interpret `#` as a special character. In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="5a039-287">Oluşturulan çıktı adı.</span><span class="sxs-lookup"><span data-stu-id="5a039-287">The name for the created output.</span></span> <span data-ttu-id="5a039-288">Ad belirtilmezse, geçerli dizin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5a039-288">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="5a039-289">Oluşturulan çıktı yerleştirileceği konum.</span><span class="sxs-lookup"><span data-stu-id="5a039-289">Location to place the generated output.</span></span> <span data-ttu-id="5a039-290">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="5a039-290">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="5a039-291">Şablon seçenekleri</span><span class="sxs-lookup"><span data-stu-id="5a039-291">Template options</span></span>

<span data-ttu-id="5a039-292">Her proje şablonu ek seçenekleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="5a039-292">Each project template may have additional options available.</span></span> <span data-ttu-id="5a039-293">Çekirdek şablonları aşağıdaki ek seçeneklere sahip olursunuz:</span><span class="sxs-lookup"><span data-stu-id="5a039-293">The core templates have the following additional options:</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="5a039-294">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="5a039-294">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="5a039-295">**konsolunda, Açısal tepki, reactredux, razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="5a039-295">**console, angular, react, reactredux, razorclasslib**</span></span>

  <span data-ttu-id="5a039-296">`--no-restore` -Proje oluşturma sırasında örtük bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="5a039-296">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="5a039-297">**ClassLib**</span><span class="sxs-lookup"><span data-stu-id="5a039-297">**classlib**</span></span>

<span data-ttu-id="5a039-298">`-f|--framework <FRAMEWORK>` -Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="5a039-298">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="5a039-299">Değerler: `netcoreapp2.0` .NET çekirdek sınıf kitaplığı oluşturmak için veya `netstandard2.0` .NET standart sınıf kitaplığı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="5a039-299">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="5a039-300">Varsayılan değer `netstandard2.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="5a039-300">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="5a039-301">`--no-restore` -Proje oluşturma sırasında örtük bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="5a039-301">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="5a039-302">**mstest'i, xunit**</span><span class="sxs-lookup"><span data-stu-id="5a039-302">**mstest, xunit**</span></span>

<span data-ttu-id="5a039-303">`-p|--enable-pack` -Proje kullanma paketleme sağlar [dotnet paketi](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="5a039-303">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="5a039-304">`--no-restore` -Proje oluşturma sırasında örtük bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="5a039-304">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="5a039-305">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="5a039-305">**globaljson**</span></span>

<span data-ttu-id="5a039-306">`--sdk-version <VERSION_NUMBER>` -Kullanmak için .NET Core SDK sürümünü belirtir *global.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="5a039-306">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="5a039-307">**Web**</span><span class="sxs-lookup"><span data-stu-id="5a039-307">**web**</span></span>

<span data-ttu-id="5a039-308">`--use-launch-settings` -İçeren *launchSettings.json* oluşturulan şablon çıkışı.</span><span class="sxs-lookup"><span data-stu-id="5a039-308">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="5a039-309">`--no-restore` -Proje oluşturma sırasında örtük bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="5a039-309">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="5a039-310">**webapı**</span><span class="sxs-lookup"><span data-stu-id="5a039-310">**webapi**</span></span>

<span data-ttu-id="5a039-311">`-au|--auth <AUTHENTICATION_TYPE>` -Kullanılacak kimlik doğrulama türü.</span><span class="sxs-lookup"><span data-stu-id="5a039-311">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="5a039-312">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="5a039-312">The possible values are:</span></span>

- <span data-ttu-id="5a039-313">`None` -Kimlik doğrulama yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="5a039-313">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="5a039-314">`IndividualB2C` -Azure AD B2C ile tek tek kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5a039-314">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="5a039-315">`SingleOrg` -Tek bir kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5a039-315">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="5a039-316">`Windows` -Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5a039-316">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="5a039-317">`--aad-b2c-instance <INSTANCE>` -Bağlanmak için Azure Active Directory B2C örnek.</span><span class="sxs-lookup"><span data-stu-id="5a039-317">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="5a039-318">İle kullandığınız `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5a039-318">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="5a039-319">Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="5a039-319">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="5a039-320">`-ssp|--susi-policy-id <ID>` -Bu proje için oturum açma ve kaydolma ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="5a039-320">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="5a039-321">İle kullandığınız `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5a039-321">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="5a039-322">`--aad-instance <INSTANCE>` -Bağlanmak için Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="5a039-322">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="5a039-323">İle kullandığınız `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5a039-323">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="5a039-324">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="5a039-324">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="5a039-325">`--client-id <ID>` -Bu proje için istemci kimliği.</span><span class="sxs-lookup"><span data-stu-id="5a039-325">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="5a039-326">İle kullandığınız `IndividualB2C` veya `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5a039-326">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="5a039-327">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="5a039-327">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="5a039-328">`--domain <DOMAIN>` -Etki alanı için dizin Kiracı.</span><span class="sxs-lookup"><span data-stu-id="5a039-328">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="5a039-329">İle kullandığınız `SingleOrg` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5a039-329">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="5a039-330">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="5a039-330">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="5a039-331">`--tenant-id <ID>` -Tenantıd bağlanmak için kimliği dizini.</span><span class="sxs-lookup"><span data-stu-id="5a039-331">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="5a039-332">İle kullandığınız `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5a039-332">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="5a039-333">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="5a039-333">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="5a039-334">`-r|--org-read-access` -Bu uygulamanın dizine okuma erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="5a039-334">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="5a039-335">Yalnızca uygular `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5a039-335">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="5a039-336">`--use-launch-settings` -İçeren *launchSettings.json* oluşturulan şablon çıkışı.</span><span class="sxs-lookup"><span data-stu-id="5a039-336">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="5a039-337">`-uld|--use-local-db` -Yerel veritabanı yerine SQLite kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5a039-337">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="5a039-338">Yalnızca uygular `Individual` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5a039-338">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="5a039-339">`--no-restore` -Proje oluşturma sırasında örtük bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="5a039-339">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="5a039-340">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="5a039-340">**mvc, razor**</span></span>

<span data-ttu-id="5a039-341">`-au|--auth <AUTHENTICATION_TYPE>` -Kullanılacak kimlik doğrulama türü.</span><span class="sxs-lookup"><span data-stu-id="5a039-341">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="5a039-342">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="5a039-342">The possible values are:</span></span>

- <span data-ttu-id="5a039-343">`None` -Kimlik doğrulama yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="5a039-343">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="5a039-344">`Individual` -Tek tek kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5a039-344">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="5a039-345">`IndividualB2C` -Azure AD B2C ile tek tek kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5a039-345">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="5a039-346">`SingleOrg` -Tek bir kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5a039-346">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="5a039-347">`MultiOrg` -Birden çok Kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5a039-347">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="5a039-348">`Windows` -Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5a039-348">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="5a039-349">`--aad-b2c-instance <INSTANCE>` -Bağlanmak için Azure Active Directory B2C örnek.</span><span class="sxs-lookup"><span data-stu-id="5a039-349">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="5a039-350">İle kullandığınız `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5a039-350">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="5a039-351">Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="5a039-351">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="5a039-352">`-ssp|--susi-policy-id <ID>` -Bu proje için oturum açma ve kaydolma ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="5a039-352">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="5a039-353">İle kullandığınız `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5a039-353">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="5a039-354">`-rp|--reset-password-policy-id <ID>` -Bu proje için reset parola ilkesi kimliği.</span><span class="sxs-lookup"><span data-stu-id="5a039-354">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="5a039-355">İle kullandığınız `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5a039-355">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="5a039-356">`-ep|--edit-profile-policy-id <ID>` -Bu proje için Düzenle profili ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="5a039-356">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="5a039-357">İle kullandığınız `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5a039-357">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="5a039-358">`--aad-instance <INSTANCE>` -Bağlanmak için Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="5a039-358">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="5a039-359">İle kullandığınız `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5a039-359">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="5a039-360">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="5a039-360">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="5a039-361">`--client-id <ID>` -Bu proje için istemci kimliği.</span><span class="sxs-lookup"><span data-stu-id="5a039-361">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="5a039-362">İle kullandığınız `IndividualB2C`, `SingleOrg`, veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5a039-362">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="5a039-363">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="5a039-363">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="5a039-364">`--domain <DOMAIN>` -Etki alanı için dizin Kiracı.</span><span class="sxs-lookup"><span data-stu-id="5a039-364">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="5a039-365">İle kullandığınız `SingleOrg` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5a039-365">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="5a039-366">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="5a039-366">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="5a039-367">`--tenant-id <ID>` -Tenantıd bağlanmak için kimliği dizini.</span><span class="sxs-lookup"><span data-stu-id="5a039-367">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="5a039-368">İle kullandığınız `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5a039-368">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="5a039-369">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="5a039-369">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="5a039-370">`--callback-path <PATH>` -Yeniden yönlendirme URI'si, uygulamanın taban yolu içindeki istek yolu.</span><span class="sxs-lookup"><span data-stu-id="5a039-370">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="5a039-371">İle kullandığınız `SingleOrg` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5a039-371">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="5a039-372">Varsayılan değer `/signin-oidc` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="5a039-372">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="5a039-373">`-r|--org-read-access` -Bu uygulamanın dizine okuma erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="5a039-373">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="5a039-374">Yalnızca uygular `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5a039-374">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="5a039-375">`--use-launch-settings` -İçeren *launchSettings.json* oluşturulan şablon çıkışı.</span><span class="sxs-lookup"><span data-stu-id="5a039-375">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="5a039-376">`--use-browserlink` -BrowserLink projede içerir.</span><span class="sxs-lookup"><span data-stu-id="5a039-376">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="5a039-377">`-uld|--use-local-db` -Yerel veritabanı yerine SQLite kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5a039-377">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="5a039-378">Yalnızca uygular `Individual` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5a039-378">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="5a039-379">`--no-restore` -Proje oluşturma sırasında örtük bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="5a039-379">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="5a039-380">**Sayfa**</span><span class="sxs-lookup"><span data-stu-id="5a039-380">**page**</span></span>

<span data-ttu-id="5a039-381">`-na|--namespace <NAMESPACE_NAME>`-Namespace üretilen kod için.</span><span class="sxs-lookup"><span data-stu-id="5a039-381">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="5a039-382">Varsayılan değer `MyApp.Namespace` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="5a039-382">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="5a039-383">`-np|--no-pagemodel` -Bir PageModel olmadan sayfası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5a039-383">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="5a039-384">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="5a039-384">**viewimports**</span></span>

<span data-ttu-id="5a039-385">`-na|--namespace <NAMESPACE_NAME>`-Namespace üretilen kod için.</span><span class="sxs-lookup"><span data-stu-id="5a039-385">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="5a039-386">Varsayılan değer `MyApp.Namespace` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="5a039-386">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="5a039-387">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="5a039-387">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="5a039-388">**konsolunda, Açısal, tepki, reactredux**</span><span class="sxs-lookup"><span data-stu-id="5a039-388">**console, angular, react, reactredux**</span></span>

  <span data-ttu-id="5a039-389">`--no-restore` -Proje oluşturma sırasında örtük bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="5a039-389">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="5a039-390">**ClassLib**</span><span class="sxs-lookup"><span data-stu-id="5a039-390">**classlib**</span></span>

<span data-ttu-id="5a039-391">`-f|--framework <FRAMEWORK>` -Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="5a039-391">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="5a039-392">Değerler: `netcoreapp2.0` .NET çekirdek sınıf kitaplığı oluşturmak için veya `netstandard2.0` .NET standart sınıf kitaplığı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="5a039-392">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="5a039-393">Varsayılan değer `netstandard2.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="5a039-393">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="5a039-394">`--no-restore` -Proje oluşturma sırasında örtük bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="5a039-394">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="5a039-395">**mstest'i, xunit**</span><span class="sxs-lookup"><span data-stu-id="5a039-395">**mstest, xunit**</span></span>

<span data-ttu-id="5a039-396">`-p|--enable-pack` -Proje kullanma paketleme sağlar [dotnet paketi](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="5a039-396">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="5a039-397">`--no-restore` -Proje oluşturma sırasında örtük bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="5a039-397">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="5a039-398">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="5a039-398">**globaljson**</span></span>

<span data-ttu-id="5a039-399">`--sdk-version <VERSION_NUMBER>` -Kullanmak için .NET Core SDK sürümünü belirtir *global.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="5a039-399">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="5a039-400">**Web**</span><span class="sxs-lookup"><span data-stu-id="5a039-400">**web**</span></span>

<span data-ttu-id="5a039-401">`--use-launch-settings` -İçeren *launchSettings.json* oluşturulan şablon çıkışı.</span><span class="sxs-lookup"><span data-stu-id="5a039-401">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="5a039-402">`--no-restore` -Proje oluşturma sırasında örtük bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="5a039-402">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="5a039-403">**webapı**</span><span class="sxs-lookup"><span data-stu-id="5a039-403">**webapi**</span></span>

<span data-ttu-id="5a039-404">`-au|--auth <AUTHENTICATION_TYPE>` -Kullanılacak kimlik doğrulama türü.</span><span class="sxs-lookup"><span data-stu-id="5a039-404">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="5a039-405">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="5a039-405">The possible values are:</span></span>

- <span data-ttu-id="5a039-406">`None` -Kimlik doğrulama yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="5a039-406">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="5a039-407">`IndividualB2C` -Azure AD B2C ile tek tek kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5a039-407">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="5a039-408">`SingleOrg` -Tek bir kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5a039-408">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="5a039-409">`Windows` -Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5a039-409">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="5a039-410">`--aad-b2c-instance <INSTANCE>` -Bağlanmak için Azure Active Directory B2C örnek.</span><span class="sxs-lookup"><span data-stu-id="5a039-410">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="5a039-411">İle kullandığınız `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5a039-411">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="5a039-412">Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="5a039-412">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="5a039-413">`-ssp|--susi-policy-id <ID>` -Bu proje için oturum açma ve kaydolma ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="5a039-413">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="5a039-414">İle kullandığınız `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5a039-414">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="5a039-415">`--aad-instance <INSTANCE>` -Bağlanmak için Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="5a039-415">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="5a039-416">İle kullandığınız `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5a039-416">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="5a039-417">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="5a039-417">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="5a039-418">`--client-id <ID>` -Bu proje için istemci kimliği.</span><span class="sxs-lookup"><span data-stu-id="5a039-418">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="5a039-419">İle kullandığınız `IndividualB2C` veya `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5a039-419">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="5a039-420">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="5a039-420">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="5a039-421">`--domain <DOMAIN>` -Etki alanı için dizin Kiracı.</span><span class="sxs-lookup"><span data-stu-id="5a039-421">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="5a039-422">İle kullandığınız `SingleOrg` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5a039-422">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="5a039-423">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="5a039-423">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="5a039-424">`--tenant-id <ID>` -Tenantıd bağlanmak için kimliği dizini.</span><span class="sxs-lookup"><span data-stu-id="5a039-424">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="5a039-425">İle kullandığınız `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5a039-425">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="5a039-426">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="5a039-426">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="5a039-427">`-r|--org-read-access` -Bu uygulamanın dizine okuma erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="5a039-427">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="5a039-428">Yalnızca uygular `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5a039-428">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="5a039-429">`--use-launch-settings` -İçeren *launchSettings.json* oluşturulan şablon çıkışı.</span><span class="sxs-lookup"><span data-stu-id="5a039-429">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="5a039-430">`-uld|--use-local-db` -Yerel veritabanı yerine SQLite kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5a039-430">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="5a039-431">Yalnızca uygular `Individual` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5a039-431">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="5a039-432">`--no-restore` -Proje oluşturma sırasında örtük bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="5a039-432">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="5a039-433">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="5a039-433">**mvc, razor**</span></span>

<span data-ttu-id="5a039-434">`-au|--auth <AUTHENTICATION_TYPE>` -Kullanılacak kimlik doğrulama türü.</span><span class="sxs-lookup"><span data-stu-id="5a039-434">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="5a039-435">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="5a039-435">The possible values are:</span></span>

- <span data-ttu-id="5a039-436">`None` -Kimlik doğrulama yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="5a039-436">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="5a039-437">`Individual` -Tek tek kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5a039-437">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="5a039-438">`IndividualB2C` -Azure AD B2C ile tek tek kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5a039-438">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="5a039-439">`SingleOrg` -Tek bir kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5a039-439">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="5a039-440">`MultiOrg` -Birden çok Kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5a039-440">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="5a039-441">`Windows` -Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5a039-441">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="5a039-442">`--aad-b2c-instance <INSTANCE>` -Bağlanmak için Azure Active Directory B2C örnek.</span><span class="sxs-lookup"><span data-stu-id="5a039-442">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="5a039-443">İle kullandığınız `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5a039-443">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="5a039-444">Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="5a039-444">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="5a039-445">`-ssp|--susi-policy-id <ID>` -Bu proje için oturum açma ve kaydolma ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="5a039-445">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="5a039-446">İle kullandığınız `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5a039-446">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="5a039-447">`-rp|--reset-password-policy-id <ID>` -Bu proje için reset parola ilkesi kimliği.</span><span class="sxs-lookup"><span data-stu-id="5a039-447">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="5a039-448">İle kullandığınız `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5a039-448">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="5a039-449">`-ep|--edit-profile-policy-id <ID>` -Bu proje için Düzenle profili ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="5a039-449">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="5a039-450">İle kullandığınız `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5a039-450">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="5a039-451">`--aad-instance <INSTANCE>` -Bağlanmak için Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="5a039-451">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="5a039-452">İle kullandığınız `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5a039-452">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="5a039-453">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="5a039-453">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="5a039-454">`--client-id <ID>` -Bu proje için istemci kimliği.</span><span class="sxs-lookup"><span data-stu-id="5a039-454">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="5a039-455">İle kullandığınız `IndividualB2C`, `SingleOrg`, veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5a039-455">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="5a039-456">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="5a039-456">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="5a039-457">`--domain <DOMAIN>` -Etki alanı için dizin Kiracı.</span><span class="sxs-lookup"><span data-stu-id="5a039-457">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="5a039-458">İle kullandığınız `SingleOrg` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5a039-458">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="5a039-459">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="5a039-459">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="5a039-460">`--tenant-id <ID>` -Tenantıd bağlanmak için kimliği dizini.</span><span class="sxs-lookup"><span data-stu-id="5a039-460">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="5a039-461">İle kullandığınız `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5a039-461">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="5a039-462">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="5a039-462">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="5a039-463">`--callback-path <PATH>` -Yeniden yönlendirme URI'si, uygulamanın taban yolu içindeki istek yolu.</span><span class="sxs-lookup"><span data-stu-id="5a039-463">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="5a039-464">İle kullandığınız `SingleOrg` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5a039-464">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="5a039-465">Varsayılan değer `/signin-oidc` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="5a039-465">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="5a039-466">`-r|--org-read-access` -Bu uygulamanın dizine okuma erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="5a039-466">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="5a039-467">Yalnızca uygular `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5a039-467">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="5a039-468">`--use-launch-settings` -İçeren *launchSettings.json* oluşturulan şablon çıkışı.</span><span class="sxs-lookup"><span data-stu-id="5a039-468">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="5a039-469">`--use-browserlink` -BrowserLink projede içerir.</span><span class="sxs-lookup"><span data-stu-id="5a039-469">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="5a039-470">`-uld|--use-local-db` -Yerel veritabanı yerine SQLite kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5a039-470">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="5a039-471">Yalnızca uygular `Individual` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5a039-471">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="5a039-472">`--no-restore` -Proje oluşturma sırasında örtük bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="5a039-472">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="5a039-473">**Sayfa**</span><span class="sxs-lookup"><span data-stu-id="5a039-473">**page**</span></span>

<span data-ttu-id="5a039-474">`-na|--namespace <NAMESPACE_NAME>`-Namespace üretilen kod için.</span><span class="sxs-lookup"><span data-stu-id="5a039-474">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="5a039-475">Varsayılan değer `MyApp.Namespace` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="5a039-475">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="5a039-476">`-np|--no-pagemodel` -Bir PageModel olmadan sayfası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5a039-476">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="5a039-477">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="5a039-477">**viewimports**</span></span>

<span data-ttu-id="5a039-478">`-na|--namespace <NAMESPACE_NAME>`-Namespace üretilen kod için.</span><span class="sxs-lookup"><span data-stu-id="5a039-478">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="5a039-479">Varsayılan değer `MyApp.Namespace` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="5a039-479">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="5a039-480">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="5a039-480">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="5a039-481">**Konsolu, xunit, mstest'i, web, webapı**</span><span class="sxs-lookup"><span data-stu-id="5a039-481">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="5a039-482">`-f|--framework` -Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="5a039-482">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="5a039-483">Değerler: `netcoreapp1.0` veya `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="5a039-483">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="5a039-484">Varsayılan değer `netcoreapp1.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="5a039-484">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="5a039-485">**ClassLib**</span><span class="sxs-lookup"><span data-stu-id="5a039-485">**classlib**</span></span>

<span data-ttu-id="5a039-486">`-f|--framework` -Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="5a039-486">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="5a039-487">Değerler: `netcoreapp1.0`, `netcoreapp1.1`, veya `netstandard1.0` için `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="5a039-487">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="5a039-488">Varsayılan değer `netstandard1.4` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="5a039-488">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="5a039-489">**mvc**</span><span class="sxs-lookup"><span data-stu-id="5a039-489">**mvc**</span></span>

<span data-ttu-id="5a039-490">`-f|--framework` -Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="5a039-490">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="5a039-491">Değerler: `netcoreapp1.0` veya `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="5a039-491">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="5a039-492">Varsayılan değer `netcoreapp1.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="5a039-492">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="5a039-493">`-au|--auth` -Kullanılacak kimlik doğrulama türü.</span><span class="sxs-lookup"><span data-stu-id="5a039-493">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="5a039-494">Değerler: `None` veya `Individual`.</span><span class="sxs-lookup"><span data-stu-id="5a039-494">Values: `None` or `Individual`.</span></span> <span data-ttu-id="5a039-495">Varsayılan değer `None` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="5a039-495">The default value is `None`.</span></span>

<span data-ttu-id="5a039-496">`-uld|--use-local-db` -Yerel veritabanı yerine SQLite kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5a039-496">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="5a039-497">Değerler: `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="5a039-497">Values: `true` or `false`.</span></span> <span data-ttu-id="5a039-498">Varsayılan değer `false` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="5a039-498">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="5a039-499">Örnekler</span><span class="sxs-lookup"><span data-stu-id="5a039-499">Examples</span></span>

<span data-ttu-id="5a039-500">Geçerli dizinde bir F # konsol uygulama projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="5a039-500">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="5a039-501">(Yalnızca .NET Core SDK 2.0 veya sonraki sürümleriyle kullanılabilir) belirtilen dizindeki .NET standart bir sınıf kitaplığı projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="5a039-501">Create a .NET Standard class library project in the specified directory (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="5a039-502">Yeni bir ASP.NET Core C# MVC uygulama projesi geçerli dizinde kimlik doğrulamasız .NET Core 2.0 hedefleme oluşturun:</span><span class="sxs-lookup"><span data-stu-id="5a039-502">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication targeting .NET Core 2.0:</span></span>

`dotnet new mvc -au None -f netcoreapp2.0`

<span data-ttu-id="5a039-503">.NET Core 2.0 hedefleme yeni bir xUnit uygulaması oluşturun:</span><span class="sxs-lookup"><span data-stu-id="5a039-503">Create a new xUnit application targeting .NET Core 2.0:</span></span>

`dotnet new xunit --framework netcoreapp2.0`

<span data-ttu-id="5a039-504">MVC için kullanılabilir tüm şablonları listeler:</span><span class="sxs-lookup"><span data-stu-id="5a039-504">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="5a039-505">ASP.NET Core (komut seçeneği kullanılabilir .NET Core SDK 1.1 ve sonraki sürümler için) için tek sayfa uygulaması şablonlarının 2.0 sürümünü yükleyin:</span><span class="sxs-lookup"><span data-stu-id="5a039-505">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

<span data-ttu-id="5a039-506">Oluşturma bir *global.json* SDK sürümü 2.0.0 (yalnızca .NET Core SDK 2.0 veya sonraki sürümleriyle kullanılabilir) ayarı geçerli dizinde:</span><span class="sxs-lookup"><span data-stu-id="5a039-506">Create a *global.json* in the current directory setting the SDK version to 2.0.0 (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="5a039-507">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5a039-507">See also</span></span>

[<span data-ttu-id="5a039-508">Yeni dotnet için özel şablonlar</span><span class="sxs-lookup"><span data-stu-id="5a039-508">Custom templates for dotnet new</span></span>](custom-templates.md)  
[<span data-ttu-id="5a039-509">Dotnet new için özel şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="5a039-509">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)  
[<span data-ttu-id="5a039-510">DotNet/dotnet-şablonu-samples GitHub depo</span><span class="sxs-lookup"><span data-stu-id="5a039-510">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)  
[<span data-ttu-id="5a039-511">Yeni dotnet için kullanılabilir şablonlar</span><span class="sxs-lookup"><span data-stu-id="5a039-511">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)