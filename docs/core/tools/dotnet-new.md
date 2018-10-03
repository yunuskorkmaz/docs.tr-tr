---
title: Yeni komut dotnet - .NET Core CLI
description: Belirtilen şablonu temel alan yeni .NET Core projeleri dotnet yeni bir komut oluşturur.
author: mairaw
ms.author: mairaw
ms.date: 07/31/2018
ms.openlocfilehash: 396c4ddf09854fa4582226bdb1422f8c929e459b
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48036136"
---
# <a name="dotnet-new"></a><span data-ttu-id="75160-103">DotNet yeni</span><span class="sxs-lookup"><span data-stu-id="75160-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="75160-104">Ad</span><span class="sxs-lookup"><span data-stu-id="75160-104">Name</span></span>

<span data-ttu-id="75160-105">`dotnet new` -Yeni Proje, yapılandırma dosyası veya belirtilen şablonu temel alan bir çözüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="75160-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="75160-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="75160-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="75160-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="75160-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output]
    [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="75160-108">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="75160-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="75160-109">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="75160-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="75160-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="75160-110">Description</span></span>

<span data-ttu-id="75160-111">`dotnet new` Komutu geçerli bir .NET Core projesi başlatmak için kolay bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="75160-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="75160-112">Komut çağrıları [şablon altyapısı](https://github.com/dotnet/templating) yapıları belirtilen şablonu ve seçenekleri bağlı disk oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="75160-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="75160-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="75160-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="75160-114">Komut çağrıldığında örneği oluşturmak için şablon.</span><span class="sxs-lookup"><span data-stu-id="75160-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="75160-115">Her şablon geçirebilirsiniz belirli seçenekler olabilir.</span><span class="sxs-lookup"><span data-stu-id="75160-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="75160-116">Daha fazla bilgi için [şablon seçeneklerini](#template-options).</span><span class="sxs-lookup"><span data-stu-id="75160-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="75160-117">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="75160-117">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="75160-118">Komutu, şablonları, varsayılan listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="75160-118">The command contains a default list of templates.</span></span> <span data-ttu-id="75160-119">Kullanım `dotnet new -l` kullanılabilir şablonların listesini alamadı.</span><span class="sxs-lookup"><span data-stu-id="75160-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="75160-120">Aşağıdaki tablo, .NET Core SDK 2.1.300 önceden yüklenmiş olarak gelen şablonları gösterir.</span><span class="sxs-lookup"><span data-stu-id="75160-120">The following table shows the templates that come pre-installed with the .NET Core SDK 2.1.300.</span></span> <span data-ttu-id="75160-121">Şablonunuz için varsayılan dili köşeli ayraçlar içinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="75160-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="75160-122">Şablon açıklaması</span><span class="sxs-lookup"><span data-stu-id="75160-122">Template description</span></span>                          | <span data-ttu-id="75160-123">Şablon adı</span><span class="sxs-lookup"><span data-stu-id="75160-123">Template name</span></span>   | <span data-ttu-id="75160-124">Diller</span><span class="sxs-lookup"><span data-stu-id="75160-124">Languages</span></span>     |
|----------------------------------------------|-----------------|---------------|
| <span data-ttu-id="75160-125">Konsol uygulaması</span><span class="sxs-lookup"><span data-stu-id="75160-125">Console application</span></span>                          | `console`       | <span data-ttu-id="75160-126">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="75160-126">[C#], F#, VB</span></span>  |
| <span data-ttu-id="75160-127">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="75160-127">Class library</span></span>                                | `classlib`      | <span data-ttu-id="75160-128">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="75160-128">[C#], F#, VB</span></span>  |
| <span data-ttu-id="75160-129">Birim testi projesi</span><span class="sxs-lookup"><span data-stu-id="75160-129">Unit test project</span></span>                            | `mstest`        | <span data-ttu-id="75160-130">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="75160-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="75160-131">xUnit test projesi</span><span class="sxs-lookup"><span data-stu-id="75160-131">xUnit test project</span></span>                           | `xunit`         | <span data-ttu-id="75160-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="75160-132">[C#], F#, VB</span></span>  |
| <span data-ttu-id="75160-133">Razor sayfası</span><span class="sxs-lookup"><span data-stu-id="75160-133">Razor page</span></span>                                   | `page`          | <span data-ttu-id="75160-134">[C#]</span><span class="sxs-lookup"><span data-stu-id="75160-134">[C#]</span></span>          |
| <span data-ttu-id="75160-135">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="75160-135">MVC ViewImports</span></span>                              | `viewimports`   | <span data-ttu-id="75160-136">[C#]</span><span class="sxs-lookup"><span data-stu-id="75160-136">[C#]</span></span>          |
| <span data-ttu-id="75160-137">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="75160-137">MVC ViewStart</span></span>                                | `viewstart`     | <span data-ttu-id="75160-138">[C#]</span><span class="sxs-lookup"><span data-stu-id="75160-138">[C#]</span></span>          |
| <span data-ttu-id="75160-139">ASP.NET Core boş</span><span class="sxs-lookup"><span data-stu-id="75160-139">ASP.NET Core empty</span></span>                           | `web`           | <span data-ttu-id="75160-140">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="75160-140">[C#], F#</span></span>      |
| <span data-ttu-id="75160-141">ASP.NET Core Web uygulaması (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="75160-141">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`           | <span data-ttu-id="75160-142">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="75160-142">[C#], F#</span></span>      |
| <span data-ttu-id="75160-143">ASP.NET Core Web uygulaması</span><span class="sxs-lookup"><span data-stu-id="75160-143">ASP.NET Core Web App</span></span>                         | `razor`         | <span data-ttu-id="75160-144">[C#]</span><span class="sxs-lookup"><span data-stu-id="75160-144">[C#]</span></span>          |
| <span data-ttu-id="75160-145">Angular ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="75160-145">ASP.NET Core with Angular</span></span>                    | `angular`       | <span data-ttu-id="75160-146">[C#]</span><span class="sxs-lookup"><span data-stu-id="75160-146">[C#]</span></span>          |
| <span data-ttu-id="75160-147">React.js ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="75160-147">ASP.NET Core with React.js</span></span>                   | `react`         | <span data-ttu-id="75160-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="75160-148">[C#]</span></span>          |
| <span data-ttu-id="75160-149">ASP.NET Core React.js ve Redux</span><span class="sxs-lookup"><span data-stu-id="75160-149">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`    | <span data-ttu-id="75160-150">[C#]</span><span class="sxs-lookup"><span data-stu-id="75160-150">[C#]</span></span>          |
| <span data-ttu-id="75160-151">ASP.NET Core Web API'si</span><span class="sxs-lookup"><span data-stu-id="75160-151">ASP.NET Core Web API</span></span>                         | `webapi`        | <span data-ttu-id="75160-152">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="75160-152">[C#], F#</span></span>      |
| <span data-ttu-id="75160-153">Razor sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="75160-153">Razor class library</span></span>                          | `razorclasslib` | <span data-ttu-id="75160-154">[C#]</span><span class="sxs-lookup"><span data-stu-id="75160-154">[C#]</span></span>          |
| <span data-ttu-id="75160-155">Global.JSON dosyasını</span><span class="sxs-lookup"><span data-stu-id="75160-155">global.json file</span></span>                             | `globaljson`    |               |
| <span data-ttu-id="75160-156">NuGet yapılandırma</span><span class="sxs-lookup"><span data-stu-id="75160-156">NuGet config</span></span>                                 | `nugetconfig`   |               |
| <span data-ttu-id="75160-157">Web yapılandırması</span><span class="sxs-lookup"><span data-stu-id="75160-157">Web config</span></span>                                   | `webconfig`     |               |
| <span data-ttu-id="75160-158">Çözüm dosyası</span><span class="sxs-lookup"><span data-stu-id="75160-158">Solution file</span></span>                                | `sln`           |               |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="75160-159">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="75160-159">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="75160-160">Komutu, şablonları, varsayılan listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="75160-160">The command contains a default list of templates.</span></span> <span data-ttu-id="75160-161">Kullanım `dotnet new -l` kullanılabilir şablonların listesini alamadı.</span><span class="sxs-lookup"><span data-stu-id="75160-161">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="75160-162">Aşağıdaki tablo, .NET Core SDK 2.0 ile önceden yüklenmiş olarak gelen şablonları gösterir.</span><span class="sxs-lookup"><span data-stu-id="75160-162">The following table shows the templates that come pre-installed with the .NET Core SDK 2.0.</span></span> <span data-ttu-id="75160-163">Şablonunuz için varsayılan dili köşeli ayraçlar içinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="75160-163">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="75160-164">Şablon açıklaması</span><span class="sxs-lookup"><span data-stu-id="75160-164">Template description</span></span>                          | <span data-ttu-id="75160-165">Şablon adı</span><span class="sxs-lookup"><span data-stu-id="75160-165">Template name</span></span> | <span data-ttu-id="75160-166">Diller</span><span class="sxs-lookup"><span data-stu-id="75160-166">Languages</span></span>     |
|----------------------------------------------|---------------|---------------|
| <span data-ttu-id="75160-167">Konsol uygulaması</span><span class="sxs-lookup"><span data-stu-id="75160-167">Console application</span></span>                          | `console`     | <span data-ttu-id="75160-168">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="75160-168">[C#], F#, VB</span></span>  |
| <span data-ttu-id="75160-169">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="75160-169">Class library</span></span>                                | `classlib`    | <span data-ttu-id="75160-170">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="75160-170">[C#], F#, VB</span></span>  |
| <span data-ttu-id="75160-171">Birim testi projesi</span><span class="sxs-lookup"><span data-stu-id="75160-171">Unit test project</span></span>                            | `mstest`      | <span data-ttu-id="75160-172">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="75160-172">[C#], F#, VB</span></span>  |
| <span data-ttu-id="75160-173">xUnit test projesi</span><span class="sxs-lookup"><span data-stu-id="75160-173">xUnit test project</span></span>                           | `xunit`       | <span data-ttu-id="75160-174">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="75160-174">[C#], F#, VB</span></span>  |
| <span data-ttu-id="75160-175">ASP.NET Core boş</span><span class="sxs-lookup"><span data-stu-id="75160-175">ASP.NET Core empty</span></span>                           | `web`         | <span data-ttu-id="75160-176">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="75160-176">[C#], F#</span></span>      |
| <span data-ttu-id="75160-177">ASP.NET Core Web uygulaması (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="75160-177">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="75160-178">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="75160-178">[C#], F#</span></span>      |
| <span data-ttu-id="75160-179">ASP.NET Core Web uygulaması</span><span class="sxs-lookup"><span data-stu-id="75160-179">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="75160-180">[C#]</span><span class="sxs-lookup"><span data-stu-id="75160-180">[C#]</span></span>          |
| <span data-ttu-id="75160-181">Angular ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="75160-181">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="75160-182">[C#]</span><span class="sxs-lookup"><span data-stu-id="75160-182">[C#]</span></span>          |
| <span data-ttu-id="75160-183">React.js ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="75160-183">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="75160-184">[C#]</span><span class="sxs-lookup"><span data-stu-id="75160-184">[C#]</span></span>          |
| <span data-ttu-id="75160-185">ASP.NET Core React.js ve Redux</span><span class="sxs-lookup"><span data-stu-id="75160-185">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="75160-186">[C#]</span><span class="sxs-lookup"><span data-stu-id="75160-186">[C#]</span></span>          |
| <span data-ttu-id="75160-187">ASP.NET Core Web API'si</span><span class="sxs-lookup"><span data-stu-id="75160-187">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="75160-188">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="75160-188">[C#], F#</span></span>      |
| <span data-ttu-id="75160-189">Global.JSON dosyasını</span><span class="sxs-lookup"><span data-stu-id="75160-189">global.json file</span></span>                             | `globaljson`  |               |
| <span data-ttu-id="75160-190">NuGet yapılandırma</span><span class="sxs-lookup"><span data-stu-id="75160-190">NuGet config</span></span>                                 | `nugetconfig` |               |
| <span data-ttu-id="75160-191">Web yapılandırması</span><span class="sxs-lookup"><span data-stu-id="75160-191">Web config</span></span>                                   | `webconfig`   |               |
| <span data-ttu-id="75160-192">Çözüm dosyası</span><span class="sxs-lookup"><span data-stu-id="75160-192">Solution file</span></span>                                | `sln`         |               |
| <span data-ttu-id="75160-193">Razor sayfası</span><span class="sxs-lookup"><span data-stu-id="75160-193">Razor page</span></span>                                   | `page`        |               |
| <span data-ttu-id="75160-194">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="75160-194">MVC ViewImports</span></span>                              | `viewimports` |               |
| <span data-ttu-id="75160-195">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="75160-195">MVC ViewStart</span></span>                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="75160-196">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="75160-196">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="75160-197">Komutu, şablonları, varsayılan listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="75160-197">The command contains a default list of templates.</span></span> <span data-ttu-id="75160-198">Kullanım `dotnet new -all` kullanılabilir şablonların listesini alamadı.</span><span class="sxs-lookup"><span data-stu-id="75160-198">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="75160-199">.NET Core SDK'sı ile önceden yüklenmiş olarak gelen şablonları aşağıdaki tabloda gösterilmektedir 1.x.</span><span class="sxs-lookup"><span data-stu-id="75160-199">The following table shows the templates that come pre-installed with the .NET Core SDK 1.x.</span></span> <span data-ttu-id="75160-200">Şablonunuz için varsayılan dili köşeli ayraçlar içinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="75160-200">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="75160-201">Şablon açıklaması</span><span class="sxs-lookup"><span data-stu-id="75160-201">Template description</span></span>  | <span data-ttu-id="75160-202">Şablon adı</span><span class="sxs-lookup"><span data-stu-id="75160-202">Template name</span></span> | <span data-ttu-id="75160-203">Diller</span><span class="sxs-lookup"><span data-stu-id="75160-203">Languages</span></span> |
|----------------------|---------------|-----------|
| <span data-ttu-id="75160-204">Konsol uygulaması</span><span class="sxs-lookup"><span data-stu-id="75160-204">Console application</span></span>  | `console`     | <span data-ttu-id="75160-205">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="75160-205">[C#], F#</span></span>  |
| <span data-ttu-id="75160-206">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="75160-206">Class library</span></span>        | `classlib`    | <span data-ttu-id="75160-207">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="75160-207">[C#], F#</span></span>  |
| <span data-ttu-id="75160-208">Birim testi projesi</span><span class="sxs-lookup"><span data-stu-id="75160-208">Unit test project</span></span>    | `mstest`      | <span data-ttu-id="75160-209">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="75160-209">[C#], F#</span></span>  |
| <span data-ttu-id="75160-210">xUnit test projesi</span><span class="sxs-lookup"><span data-stu-id="75160-210">xUnit test project</span></span>   | `xunit`       | <span data-ttu-id="75160-211">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="75160-211">[C#], F#</span></span>  |
| <span data-ttu-id="75160-212">ASP.NET Core boş</span><span class="sxs-lookup"><span data-stu-id="75160-212">ASP.NET Core empty</span></span>   | `web`         | <span data-ttu-id="75160-213">[C#]</span><span class="sxs-lookup"><span data-stu-id="75160-213">[C#]</span></span>      |
| <span data-ttu-id="75160-214">ASP.NET Core Web uygulaması</span><span class="sxs-lookup"><span data-stu-id="75160-214">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="75160-215">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="75160-215">[C#], F#</span></span>  |
| <span data-ttu-id="75160-216">ASP.NET Core Web API'si</span><span class="sxs-lookup"><span data-stu-id="75160-216">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="75160-217">[C#]</span><span class="sxs-lookup"><span data-stu-id="75160-217">[C#]</span></span>      |
| <span data-ttu-id="75160-218">NuGet yapılandırma</span><span class="sxs-lookup"><span data-stu-id="75160-218">NuGet config</span></span>         | `nugetconfig` |           |
| <span data-ttu-id="75160-219">Web yapılandırması</span><span class="sxs-lookup"><span data-stu-id="75160-219">Web config</span></span>           | `webconfig`   |           |
| <span data-ttu-id="75160-220">Çözüm dosyası</span><span class="sxs-lookup"><span data-stu-id="75160-220">Solution file</span></span>        | `sln`         |           |

---

## <a name="options"></a><span data-ttu-id="75160-221">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="75160-221">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="75160-222">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="75160-222">.NET Core 2.1</span></span>](#tab/netcore21)

`--force`

<span data-ttu-id="75160-223">Mevcut dosyaları değiştirmek olsa bile oluşturulması gereken içeriği zorlar.</span><span class="sxs-lookup"><span data-stu-id="75160-223">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="75160-224">Bir proje çıkış dizinine içerdiğinde, bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="75160-224">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="75160-225">Komut için Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="75160-225">Prints out help for the command.</span></span> <span data-ttu-id="75160-226">İçin çağrılabilir `dotnet new` kendisini komutu veya herhangi bir şablon gibi `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="75160-226">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="75160-227">Bir kaynak veya şablon paketinden yükler `PATH` veya `NUGET_ID` sağlanan.</span><span class="sxs-lookup"><span data-stu-id="75160-227">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="75160-228">Bir şablon Paketi yayım öncesi bir sürümü yüklemek istediğiniz sürümü biçiminde belirtmek gerekirse `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="75160-228">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="75160-229">Varsayılan olarak, `dotnet new` geçirir \* sürümünü temsil eden en son kararlı Paket sürümü.</span><span class="sxs-lookup"><span data-stu-id="75160-229">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="75160-230">Bir örneğe bakın [örnekler](#examples) bölümü.</span><span class="sxs-lookup"><span data-stu-id="75160-230">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="75160-231">Özel şablonlar oluşturma hakkında daha fazla bilgi için bkz. [yeni dotnet için özel şablonları](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="75160-231">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="75160-232">Belirtilen ad içeren şablonlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="75160-232">Lists templates containing the specified name.</span></span> <span data-ttu-id="75160-233">İçin çağırdıysanız `dotnet new` komut, belirtilen dizinde kullanılabilir olası şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="75160-233">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="75160-234">Örnek dizin zaten bir proje içeriyorsa, tüm proje şablonları listesinde değil.</span><span class="sxs-lookup"><span data-stu-id="75160-234">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="75160-235">Oluşturmak için şablon dili.</span><span class="sxs-lookup"><span data-stu-id="75160-235">The language of the template to create.</span></span> <span data-ttu-id="75160-236">Dil kabul şablon tarafından farklılık gösterir (varsayılan ayarlarında bkz [bağımsız değişkenleri](#arguments) bölümü).</span><span class="sxs-lookup"><span data-stu-id="75160-236">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="75160-237">Bazı şablonlar için geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="75160-237">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="75160-238">Bazı Kabukları yorumlama `#` olarak bir özel karakter.</span><span class="sxs-lookup"><span data-stu-id="75160-238">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="75160-239">Bu gibi durumlarda, dil parametre değeri, aşağıdaki gibi alın gerek `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="75160-239">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="75160-240">Oluşturulan çıktı adı.</span><span class="sxs-lookup"><span data-stu-id="75160-240">The name for the created output.</span></span> <span data-ttu-id="75160-241">Hiçbir ad belirtilmediği takdirde, geçerli dizin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="75160-241">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="75160-242">Yükleme sırasında kullanılacak bir NuGet kaynağı belirtir.</span><span class="sxs-lookup"><span data-stu-id="75160-242">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="75160-243">Oluşturulan çıktı yerleştirileceği konumu.</span><span class="sxs-lookup"><span data-stu-id="75160-243">Location to place the generated output.</span></span> <span data-ttu-id="75160-244">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="75160-244">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="75160-245">Şablonları kullanılabilir türlerine göre filtreler.</span><span class="sxs-lookup"><span data-stu-id="75160-245">Filters templates based on available types.</span></span> <span data-ttu-id="75160-246">Önceden tanımlanmış değerler şunlardır: "proje", "Item" veya "diğer".</span><span class="sxs-lookup"><span data-stu-id="75160-246">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="75160-247">Bir kaynak veya şablon paketini kaldırır `PATH` veya `NUGET_ID` sağlanan.</span><span class="sxs-lookup"><span data-stu-id="75160-247">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="75160-248">Bir şablon kullanarak kaldırmak için bir `PATH`, yol tam olarak nitelemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="75160-248">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="75160-249">Örneğin, *C:/Users/\<kullanıcı > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* çalışır, ancak *./GarciaSoftware.ConsoleTemplate.CSharp* içeren gelen Klasör erişemez.</span><span class="sxs-lookup"><span data-stu-id="75160-249">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="75160-250">Ayrıca, şablonu yoldaki son Sonlandırıcı directory eğik çizgi içermez.</span><span class="sxs-lookup"><span data-stu-id="75160-250">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="75160-251">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="75160-251">.NET Core 2.0</span></span>](#tab/netcore20)

`--force`

<span data-ttu-id="75160-252">Mevcut dosyaları değiştirmek olsa bile oluşturulması gereken içeriği zorlar.</span><span class="sxs-lookup"><span data-stu-id="75160-252">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="75160-253">Bir proje çıkış dizinine içerdiğinde, bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="75160-253">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="75160-254">Komut için Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="75160-254">Prints out help for the command.</span></span> <span data-ttu-id="75160-255">İçin çağrılabilir `dotnet new` kendisini komutu veya herhangi bir şablon gibi `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="75160-255">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="75160-256">Bir kaynak veya şablon paketinden yükler `PATH` veya `NUGET_ID` sağlanan.</span><span class="sxs-lookup"><span data-stu-id="75160-256">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="75160-257">Bir şablon Paketi yayım öncesi bir sürümü yüklemek istediğiniz sürümü biçiminde belirtmek gerekirse `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="75160-257">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="75160-258">Varsayılan olarak, `dotnet new` geçirir \* sürümünü temsil eden en son kararlı Paket sürümü.</span><span class="sxs-lookup"><span data-stu-id="75160-258">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="75160-259">Bir örneğe bakın [örnekler](#examples) bölümü.</span><span class="sxs-lookup"><span data-stu-id="75160-259">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="75160-260">Özel şablonlar oluşturma hakkında daha fazla bilgi için bkz. [yeni dotnet için özel şablonları](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="75160-260">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="75160-261">Belirtilen ad içeren şablonlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="75160-261">Lists templates containing the specified name.</span></span> <span data-ttu-id="75160-262">İçin çağırdıysanız `dotnet new` komut, belirtilen dizinde kullanılabilir olası şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="75160-262">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="75160-263">Örnek dizin zaten bir proje içeriyorsa, tüm proje şablonları listesinde değil.</span><span class="sxs-lookup"><span data-stu-id="75160-263">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="75160-264">Oluşturmak için şablon dili.</span><span class="sxs-lookup"><span data-stu-id="75160-264">The language of the template to create.</span></span> <span data-ttu-id="75160-265">Dil kabul şablon tarafından farklılık gösterir (varsayılan ayarlarında bkz [bağımsız değişkenleri](#arguments) bölümü).</span><span class="sxs-lookup"><span data-stu-id="75160-265">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="75160-266">Bazı şablonlar için geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="75160-266">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="75160-267">Bazı Kabukları yorumlama `#` olarak bir özel karakter.</span><span class="sxs-lookup"><span data-stu-id="75160-267">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="75160-268">Bu gibi durumlarda, dil parametre değeri, aşağıdaki gibi alın gerek `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="75160-268">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="75160-269">Oluşturulan çıktı adı.</span><span class="sxs-lookup"><span data-stu-id="75160-269">The name for the created output.</span></span> <span data-ttu-id="75160-270">Hiçbir ad belirtilmediği takdirde, geçerli dizin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="75160-270">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="75160-271">Oluşturulan çıktı yerleştirileceği konumu.</span><span class="sxs-lookup"><span data-stu-id="75160-271">Location to place the generated output.</span></span> <span data-ttu-id="75160-272">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="75160-272">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="75160-273">Şablonları kullanılabilir türlerine göre filtreler.</span><span class="sxs-lookup"><span data-stu-id="75160-273">Filters templates based on available types.</span></span> <span data-ttu-id="75160-274">Önceden tanımlanmış değerler şunlardır: "proje", "Item" veya "diğer".</span><span class="sxs-lookup"><span data-stu-id="75160-274">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="75160-275">Bir kaynak veya şablon paketini kaldırır `PATH` veya `NUGET_ID` sağlanan.</span><span class="sxs-lookup"><span data-stu-id="75160-275">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="75160-276">Bir kaynağı kullanan bir şablonu kaldırmak için `PATH`, yol tam olarak nitelemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="75160-276">To uninstall a template using a source `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="75160-277">Örneğin, *C:/Users/\<kullanıcı > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* çalışır, ancak *./GarciaSoftware.ConsoleTemplate.CSharp* içeren gelen Klasör erişemez.</span><span class="sxs-lookup"><span data-stu-id="75160-277">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span> <span data-ttu-id="75160-278">Ayrıca, şablonu yoldaki son Sonlandırıcı directory eğik çizgi içermez.</span><span class="sxs-lookup"><span data-stu-id="75160-278">Additionally, do not include a final terminating directory slash on your template path.</span></span>
> 
> <span data-ttu-id="75160-279">Belirlemek erişemiyorsanız `PATH` veya `NUGET_ID` çalıştıran, bir şablonu kaldırmak için gerekli bağımsız değişken `dotnet new --uninstall` bağımsız değişken yüklü tüm şablonları ve bunları kaldırmak için gerekli bağımsız değişken listesi olmayan.</span><span class="sxs-lookup"><span data-stu-id="75160-279">If you are unable to determine the `PATH` or `NUGET_ID` argument needed to uninstall a template, running `dotnet new --uninstall` without an argument will list all installed templates and the argument required to uninstall them.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="75160-280">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="75160-280">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="75160-281">Belirli türde bir proje için tüm şablonları'nı bağlamında çalıştırılırken gösterir `dotnet new` tek başına komutu.</span><span class="sxs-lookup"><span data-stu-id="75160-281">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="75160-282">Belirli bir şablon bağlamında gibi çalıştırırken `dotnet new web -all`, `-all` zorla oluşturma bayrak olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="75160-282">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="75160-283">Bir proje çıkış dizinine içerdiğinde, bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="75160-283">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="75160-284">Komut için Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="75160-284">Prints out help for the command.</span></span> <span data-ttu-id="75160-285">İçin çağrılabilir `dotnet new` kendisini komutu veya herhangi bir şablon gibi `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="75160-285">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="75160-286">Belirtilen ad içeren şablonlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="75160-286">Lists templates containing the specified name.</span></span> <span data-ttu-id="75160-287">İçin çağırdıysanız `dotnet new` komut, belirtilen dizinde kullanılabilir olası şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="75160-287">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="75160-288">Örnek dizin zaten bir proje içeriyorsa, tüm proje şablonları listesinde değil.</span><span class="sxs-lookup"><span data-stu-id="75160-288">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="75160-289">Oluşturmak için şablon dili.</span><span class="sxs-lookup"><span data-stu-id="75160-289">The language of the template to create.</span></span> <span data-ttu-id="75160-290">Dil kabul şablon tarafından farklılık gösterir (varsayılan ayarlarında bkz [bağımsız değişkenleri](#arguments) bölümü).</span><span class="sxs-lookup"><span data-stu-id="75160-290">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="75160-291">Bazı şablonlar için geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="75160-291">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="75160-292">Bazı Kabukları yorumlama `#` olarak bir özel karakter.</span><span class="sxs-lookup"><span data-stu-id="75160-292">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="75160-293">Bu gibi durumlarda, dil parametre değeri, aşağıdaki gibi alın gerek `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="75160-293">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="75160-294">Oluşturulan çıktı adı.</span><span class="sxs-lookup"><span data-stu-id="75160-294">The name for the created output.</span></span> <span data-ttu-id="75160-295">Hiçbir ad belirtilmediği takdirde, geçerli dizin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="75160-295">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="75160-296">Oluşturulan çıktı yerleştirileceği konumu.</span><span class="sxs-lookup"><span data-stu-id="75160-296">Location to place the generated output.</span></span> <span data-ttu-id="75160-297">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="75160-297">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="75160-298">Şablon seçenekleri</span><span class="sxs-lookup"><span data-stu-id="75160-298">Template options</span></span>

<span data-ttu-id="75160-299">Her proje şablonu, ek seçenekler kullanılabilir olabilir.</span><span class="sxs-lookup"><span data-stu-id="75160-299">Each project template may have additional options available.</span></span> <span data-ttu-id="75160-300">Çekirdek şablonları aşağıdaki ek seçeneklere sahip olursunuz:</span><span class="sxs-lookup"><span data-stu-id="75160-300">The core templates have the following additional options:</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="75160-301">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="75160-301">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="75160-302">**konsolunda, angular, react, açarken kilitlenmesi, razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="75160-302">**console, angular, react, reactredux, razorclasslib**</span></span>

  <span data-ttu-id="75160-303">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="75160-303">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="75160-304">**ClassLib**</span><span class="sxs-lookup"><span data-stu-id="75160-304">**classlib**</span></span>

<span data-ttu-id="75160-305">`-f|--framework <FRAMEWORK>` -Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="75160-305">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="75160-306">Değerler: `netcoreapp2.0` bir .NET Core sınıf kitaplığı oluşturmak için veya `netstandard2.0` .NET standart sınıf kitaplığı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="75160-306">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="75160-307">Varsayılan değer `netstandard2.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="75160-307">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="75160-308">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="75160-308">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="75160-309">**MSTest, xunit**</span><span class="sxs-lookup"><span data-stu-id="75160-309">**mstest, xunit**</span></span>

<span data-ttu-id="75160-310">`-p|--enable-pack` -Etkinleştirir kullanarak projeyi için paketleme [dotnet paketi](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="75160-310">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="75160-311">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="75160-311">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="75160-312">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="75160-312">**globaljson**</span></span>

<span data-ttu-id="75160-313">`--sdk-version <VERSION_NUMBER>` -Kullanmak için .NET Core SDK'sı sürümünü belirtir *global.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="75160-313">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="75160-314">**Web**</span><span class="sxs-lookup"><span data-stu-id="75160-314">**web**</span></span>

<span data-ttu-id="75160-315">`--exclude-launch-settings` -Hariç *launchSettings.json* oluşturulan şablonundan.</span><span class="sxs-lookup"><span data-stu-id="75160-315">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="75160-316">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="75160-316">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="75160-317">`--no-https` -Proje HTTPS'yi gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="75160-317">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="75160-318">Bu seçenek yalnızca geçerlidir `IndividualAuth` veya `OrganizationalAuth` kullanılmayan.</span><span class="sxs-lookup"><span data-stu-id="75160-318">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="75160-319">**webapı**</span><span class="sxs-lookup"><span data-stu-id="75160-319">**webapi**</span></span>

<span data-ttu-id="75160-320">`-au|--auth <AUTHENTICATION_TYPE>` -Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="75160-320">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="75160-321">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="75160-321">The possible values are:</span></span>

- <span data-ttu-id="75160-322">`None` -Kimlik doğrulama yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="75160-322">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="75160-323">`IndividualB2C` -Azure AD B2C ile kimlik doğrulaması tek tek.</span><span class="sxs-lookup"><span data-stu-id="75160-323">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="75160-324">`SingleOrg` -Kuruluş kimlik doğrulaması için tek bir kiracı.</span><span class="sxs-lookup"><span data-stu-id="75160-324">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="75160-325">`Windows` -Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="75160-325">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="75160-326">`--aad-b2c-instance <INSTANCE>` -Bağlanmak için Azure Active Directory B2C örnek.</span><span class="sxs-lookup"><span data-stu-id="75160-326">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="75160-327">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="75160-327">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="75160-328">Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="75160-328">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="75160-329">`-ssp|--susi-policy-id <ID>` -Bu proje için oturum açma ve kaydolma ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="75160-329">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="75160-330">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="75160-330">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="75160-331">`--aad-instance <INSTANCE>` -Bağlanmak için Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="75160-331">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="75160-332">İle kullanma `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="75160-332">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="75160-333">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="75160-333">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="75160-334">`--client-id <ID>` -Bu proje için istemci kimliği.</span><span class="sxs-lookup"><span data-stu-id="75160-334">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="75160-335">İle kullanma `IndividualB2C` veya `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="75160-335">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="75160-336">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="75160-336">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="75160-337">`--domain <DOMAIN>` -Dizin kiracısı için etki alanı.</span><span class="sxs-lookup"><span data-stu-id="75160-337">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="75160-338">İle kullanma `SingleOrg` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="75160-338">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="75160-339">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="75160-339">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="75160-340">`--tenant-id <ID>` -Tenantıd bağlanmak için kimliği dizini.</span><span class="sxs-lookup"><span data-stu-id="75160-340">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="75160-341">İle kullanma `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="75160-341">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="75160-342">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="75160-342">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="75160-343">`-r|--org-read-access` -Bu uygulamanın dizine okuma erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="75160-343">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="75160-344">Yalnızca uygulandığı `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="75160-344">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="75160-345">`--exclude-launch-settings` -Hariç *launchSettings.json* oluşturulan şablonundan.</span><span class="sxs-lookup"><span data-stu-id="75160-345">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="75160-346">`-uld|--use-local-db` -LocalDB yerine SQLite kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="75160-346">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="75160-347">Yalnızca uygulandığı `Individual` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="75160-347">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="75160-348">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="75160-348">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="75160-349">`--no-https` -Proje HTTPS'yi gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="75160-349">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="75160-350">`app.UseHsts` ve `app.UseHttpsRedirection` için eklenmez `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="75160-350">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="75160-351">Bu seçenek yalnızca geçerlidir `Individual`, `IndividualB2C`, `SingleOrg`, veya `MultiOrg` kullanılmayan.</span><span class="sxs-lookup"><span data-stu-id="75160-351">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="75160-352">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="75160-352">**mvc, razor**</span></span>

<span data-ttu-id="75160-353">`-au|--auth <AUTHENTICATION_TYPE>` -Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="75160-353">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="75160-354">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="75160-354">The possible values are:</span></span>

- <span data-ttu-id="75160-355">`None` -Kimlik doğrulama yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="75160-355">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="75160-356">`Individual` -Tek tek kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="75160-356">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="75160-357">`IndividualB2C` -Azure AD B2C ile kimlik doğrulaması tek tek.</span><span class="sxs-lookup"><span data-stu-id="75160-357">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="75160-358">`SingleOrg` -Kuruluş kimlik doğrulaması için tek bir kiracı.</span><span class="sxs-lookup"><span data-stu-id="75160-358">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="75160-359">`MultiOrg` -Birden fazla Kiracı için Kurumsal kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="75160-359">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="75160-360">`Windows` -Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="75160-360">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="75160-361">`--aad-b2c-instance <INSTANCE>` -Bağlanmak için Azure Active Directory B2C örnek.</span><span class="sxs-lookup"><span data-stu-id="75160-361">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="75160-362">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="75160-362">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="75160-363">Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="75160-363">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="75160-364">`-ssp|--susi-policy-id <ID>` -Bu proje için oturum açma ve kaydolma ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="75160-364">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="75160-365">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="75160-365">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="75160-366">`-rp|--reset-password-policy-id <ID>` -Bu proje için reset parola ilkesi kimliği.</span><span class="sxs-lookup"><span data-stu-id="75160-366">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="75160-367">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="75160-367">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="75160-368">`-ep|--edit-profile-policy-id <ID>` -Bu proje için düzenleme profili ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="75160-368">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="75160-369">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="75160-369">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="75160-370">`--aad-instance <INSTANCE>` -Bağlanmak için Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="75160-370">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="75160-371">İle kullanma `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="75160-371">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="75160-372">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="75160-372">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="75160-373">`--client-id <ID>` -Bu proje için istemci kimliği.</span><span class="sxs-lookup"><span data-stu-id="75160-373">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="75160-374">İle kullanma `IndividualB2C`, `SingleOrg`, veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="75160-374">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="75160-375">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="75160-375">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="75160-376">`--domain <DOMAIN>` -Dizin kiracısı için etki alanı.</span><span class="sxs-lookup"><span data-stu-id="75160-376">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="75160-377">İle kullanma `SingleOrg` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="75160-377">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="75160-378">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="75160-378">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="75160-379">`--tenant-id <ID>` -Tenantıd bağlanmak için kimliği dizini.</span><span class="sxs-lookup"><span data-stu-id="75160-379">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="75160-380">İle kullanma `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="75160-380">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="75160-381">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="75160-381">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="75160-382">`--callback-path <PATH>` -Yeniden yönlendirme URI'si uygulamanın taban yolu içindeki istek yolu.</span><span class="sxs-lookup"><span data-stu-id="75160-382">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="75160-383">İle kullanma `SingleOrg` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="75160-383">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="75160-384">Varsayılan değer `/signin-oidc` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="75160-384">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="75160-385">`-r|--org-read-access` -Bu uygulamanın dizine okuma erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="75160-385">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="75160-386">Yalnızca uygulandığı `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="75160-386">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="75160-387">`--exclude-launch-settings` -Hariç *launchSettings.json* oluşturulan şablonundan.</span><span class="sxs-lookup"><span data-stu-id="75160-387">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="75160-388">`--use-browserlink` -BrowserLink projede içerir.</span><span class="sxs-lookup"><span data-stu-id="75160-388">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="75160-389">`-uld|--use-local-db` -LocalDB yerine SQLite kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="75160-389">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="75160-390">Yalnızca uygulandığı `Individual` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="75160-390">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="75160-391">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="75160-391">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="75160-392">`--no-https` -Proje HTTPS'yi gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="75160-392">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="75160-393">`app.UseHsts` ve `app.UseHttpsRedirection` için eklenmez `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="75160-393">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="75160-394">Bu seçenek yalnızca geçerlidir `Individual`, `IndividualB2C`, `SingleOrg`, veya `MultiOrg` kullanılmayan.</span><span class="sxs-lookup"><span data-stu-id="75160-394">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="75160-395">**Sayfa**</span><span class="sxs-lookup"><span data-stu-id="75160-395">**page**</span></span>

<span data-ttu-id="75160-396">`-na|--namespace <NAMESPACE_NAME>`-Namespace üretilen kod için.</span><span class="sxs-lookup"><span data-stu-id="75160-396">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="75160-397">Varsayılan değer `MyApp.Namespace` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="75160-397">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="75160-398">`-np|--no-pagemodel` -Bir PageModel olmadan sayfası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="75160-398">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="75160-399">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="75160-399">**viewimports**</span></span>

<span data-ttu-id="75160-400">`-na|--namespace <NAMESPACE_NAME>`-Namespace üretilen kod için.</span><span class="sxs-lookup"><span data-stu-id="75160-400">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="75160-401">Varsayılan değer `MyApp.Namespace` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="75160-401">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="75160-402">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="75160-402">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="75160-403">**konsolunda, angular, react, açarken kilitlenmesi**</span><span class="sxs-lookup"><span data-stu-id="75160-403">**console, angular, react, reactredux**</span></span>

  <span data-ttu-id="75160-404">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="75160-404">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="75160-405">**ClassLib**</span><span class="sxs-lookup"><span data-stu-id="75160-405">**classlib**</span></span>

<span data-ttu-id="75160-406">`-f|--framework <FRAMEWORK>` -Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="75160-406">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="75160-407">Değerler: `netcoreapp2.0` bir .NET Core sınıf kitaplığı oluşturmak için veya `netstandard2.0` .NET standart sınıf kitaplığı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="75160-407">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="75160-408">Varsayılan değer `netstandard2.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="75160-408">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="75160-409">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="75160-409">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="75160-410">**MSTest, xunit**</span><span class="sxs-lookup"><span data-stu-id="75160-410">**mstest, xunit**</span></span>

<span data-ttu-id="75160-411">`-p|--enable-pack` -Etkinleştirir kullanarak projeyi için paketleme [dotnet paketi](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="75160-411">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="75160-412">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="75160-412">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="75160-413">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="75160-413">**globaljson**</span></span>

<span data-ttu-id="75160-414">`--sdk-version <VERSION_NUMBER>` -Kullanmak için .NET Core SDK'sı sürümünü belirtir *global.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="75160-414">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="75160-415">**Web**</span><span class="sxs-lookup"><span data-stu-id="75160-415">**web**</span></span>

<span data-ttu-id="75160-416">`--use-launch-settings` -İçeren *launchSettings.json* oluşturulan şablon çıktı.</span><span class="sxs-lookup"><span data-stu-id="75160-416">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="75160-417">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="75160-417">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="75160-418">**webapı**</span><span class="sxs-lookup"><span data-stu-id="75160-418">**webapi**</span></span>

<span data-ttu-id="75160-419">`-au|--auth <AUTHENTICATION_TYPE>` -Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="75160-419">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="75160-420">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="75160-420">The possible values are:</span></span>

- <span data-ttu-id="75160-421">`None` -Kimlik doğrulama yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="75160-421">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="75160-422">`IndividualB2C` -Azure AD B2C ile kimlik doğrulaması tek tek.</span><span class="sxs-lookup"><span data-stu-id="75160-422">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="75160-423">`SingleOrg` -Kuruluş kimlik doğrulaması için tek bir kiracı.</span><span class="sxs-lookup"><span data-stu-id="75160-423">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="75160-424">`Windows` -Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="75160-424">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="75160-425">`--aad-b2c-instance <INSTANCE>` -Bağlanmak için Azure Active Directory B2C örnek.</span><span class="sxs-lookup"><span data-stu-id="75160-425">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="75160-426">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="75160-426">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="75160-427">Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="75160-427">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="75160-428">`-ssp|--susi-policy-id <ID>` -Bu proje için oturum açma ve kaydolma ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="75160-428">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="75160-429">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="75160-429">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="75160-430">`--aad-instance <INSTANCE>` -Bağlanmak için Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="75160-430">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="75160-431">İle kullanma `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="75160-431">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="75160-432">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="75160-432">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="75160-433">`--client-id <ID>` -Bu proje için istemci kimliği.</span><span class="sxs-lookup"><span data-stu-id="75160-433">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="75160-434">İle kullanma `IndividualB2C` veya `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="75160-434">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="75160-435">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="75160-435">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="75160-436">`--domain <DOMAIN>` -Dizin kiracısı için etki alanı.</span><span class="sxs-lookup"><span data-stu-id="75160-436">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="75160-437">İle kullanma `SingleOrg` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="75160-437">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="75160-438">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="75160-438">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="75160-439">`--tenant-id <ID>` -Tenantıd bağlanmak için kimliği dizini.</span><span class="sxs-lookup"><span data-stu-id="75160-439">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="75160-440">İle kullanma `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="75160-440">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="75160-441">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="75160-441">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="75160-442">`-r|--org-read-access` -Bu uygulamanın dizine okuma erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="75160-442">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="75160-443">Yalnızca uygulandığı `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="75160-443">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="75160-444">`--use-launch-settings` -İçeren *launchSettings.json* oluşturulan şablon çıktı.</span><span class="sxs-lookup"><span data-stu-id="75160-444">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="75160-445">`-uld|--use-local-db` -LocalDB yerine SQLite kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="75160-445">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="75160-446">Yalnızca uygulandığı `Individual` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="75160-446">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="75160-447">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="75160-447">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="75160-448">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="75160-448">**mvc, razor**</span></span>

<span data-ttu-id="75160-449">`-au|--auth <AUTHENTICATION_TYPE>` -Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="75160-449">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="75160-450">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="75160-450">The possible values are:</span></span>

- <span data-ttu-id="75160-451">`None` -Kimlik doğrulama yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="75160-451">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="75160-452">`Individual` -Tek tek kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="75160-452">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="75160-453">`IndividualB2C` -Azure AD B2C ile kimlik doğrulaması tek tek.</span><span class="sxs-lookup"><span data-stu-id="75160-453">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="75160-454">`SingleOrg` -Kuruluş kimlik doğrulaması için tek bir kiracı.</span><span class="sxs-lookup"><span data-stu-id="75160-454">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="75160-455">`MultiOrg` -Birden fazla Kiracı için Kurumsal kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="75160-455">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="75160-456">`Windows` -Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="75160-456">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="75160-457">`--aad-b2c-instance <INSTANCE>` -Bağlanmak için Azure Active Directory B2C örnek.</span><span class="sxs-lookup"><span data-stu-id="75160-457">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="75160-458">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="75160-458">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="75160-459">Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="75160-459">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="75160-460">`-ssp|--susi-policy-id <ID>` -Bu proje için oturum açma ve kaydolma ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="75160-460">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="75160-461">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="75160-461">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="75160-462">`-rp|--reset-password-policy-id <ID>` -Bu proje için reset parola ilkesi kimliği.</span><span class="sxs-lookup"><span data-stu-id="75160-462">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="75160-463">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="75160-463">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="75160-464">`-ep|--edit-profile-policy-id <ID>` -Bu proje için düzenleme profili ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="75160-464">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="75160-465">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="75160-465">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="75160-466">`--aad-instance <INSTANCE>` -Bağlanmak için Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="75160-466">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="75160-467">İle kullanma `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="75160-467">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="75160-468">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="75160-468">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="75160-469">`--client-id <ID>` -Bu proje için istemci kimliği.</span><span class="sxs-lookup"><span data-stu-id="75160-469">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="75160-470">İle kullanma `IndividualB2C`, `SingleOrg`, veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="75160-470">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="75160-471">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="75160-471">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="75160-472">`--domain <DOMAIN>` -Dizin kiracısı için etki alanı.</span><span class="sxs-lookup"><span data-stu-id="75160-472">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="75160-473">İle kullanma `SingleOrg` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="75160-473">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="75160-474">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="75160-474">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="75160-475">`--tenant-id <ID>` -Tenantıd bağlanmak için kimliği dizini.</span><span class="sxs-lookup"><span data-stu-id="75160-475">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="75160-476">İle kullanma `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="75160-476">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="75160-477">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="75160-477">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="75160-478">`--callback-path <PATH>` -Yeniden yönlendirme URI'si uygulamanın taban yolu içindeki istek yolu.</span><span class="sxs-lookup"><span data-stu-id="75160-478">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="75160-479">İle kullanma `SingleOrg` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="75160-479">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="75160-480">Varsayılan değer `/signin-oidc` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="75160-480">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="75160-481">`-r|--org-read-access` -Bu uygulamanın dizine okuma erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="75160-481">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="75160-482">Yalnızca uygulandığı `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="75160-482">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="75160-483">`--use-launch-settings` -İçeren *launchSettings.json* oluşturulan şablon çıktı.</span><span class="sxs-lookup"><span data-stu-id="75160-483">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="75160-484">`--use-browserlink` -BrowserLink projede içerir.</span><span class="sxs-lookup"><span data-stu-id="75160-484">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="75160-485">`-uld|--use-local-db` -LocalDB yerine SQLite kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="75160-485">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="75160-486">Yalnızca uygulandığı `Individual` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="75160-486">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="75160-487">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="75160-487">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="75160-488">**Sayfa**</span><span class="sxs-lookup"><span data-stu-id="75160-488">**page**</span></span>

<span data-ttu-id="75160-489">`-na|--namespace <NAMESPACE_NAME>`-Namespace üretilen kod için.</span><span class="sxs-lookup"><span data-stu-id="75160-489">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="75160-490">Varsayılan değer `MyApp.Namespace` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="75160-490">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="75160-491">`-np|--no-pagemodel` -Bir PageModel olmadan sayfası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="75160-491">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="75160-492">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="75160-492">**viewimports**</span></span>

<span data-ttu-id="75160-493">`-na|--namespace <NAMESPACE_NAME>`-Namespace üretilen kod için.</span><span class="sxs-lookup"><span data-stu-id="75160-493">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="75160-494">Varsayılan değer `MyApp.Namespace` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="75160-494">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="75160-495">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="75160-495">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="75160-496">**Konsolu, xunit, mstest, web, webapı**</span><span class="sxs-lookup"><span data-stu-id="75160-496">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="75160-497">`-f|--framework` -Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="75160-497">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="75160-498">Değerler: `netcoreapp1.0` veya `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="75160-498">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="75160-499">Varsayılan değer `netcoreapp1.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="75160-499">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="75160-500">**ClassLib**</span><span class="sxs-lookup"><span data-stu-id="75160-500">**classlib**</span></span>

<span data-ttu-id="75160-501">`-f|--framework` -Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="75160-501">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="75160-502">Değerler: `netcoreapp1.0`, `netcoreapp1.1`, veya `netstandard1.0` için `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="75160-502">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="75160-503">Varsayılan değer `netstandard1.4` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="75160-503">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="75160-504">**mvc**</span><span class="sxs-lookup"><span data-stu-id="75160-504">**mvc**</span></span>

<span data-ttu-id="75160-505">`-f|--framework` -Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="75160-505">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="75160-506">Değerler: `netcoreapp1.0` veya `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="75160-506">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="75160-507">Varsayılan değer `netcoreapp1.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="75160-507">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="75160-508">`-au|--auth` -Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="75160-508">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="75160-509">Değerler: `None` veya `Individual`.</span><span class="sxs-lookup"><span data-stu-id="75160-509">Values: `None` or `Individual`.</span></span> <span data-ttu-id="75160-510">Varsayılan değer `None` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="75160-510">The default value is `None`.</span></span>

<span data-ttu-id="75160-511">`-uld|--use-local-db` -LocalDB yerine SQLite kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="75160-511">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="75160-512">Değerler: `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="75160-512">Values: `true` or `false`.</span></span> <span data-ttu-id="75160-513">Varsayılan değer `false` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="75160-513">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="75160-514">Örnekler</span><span class="sxs-lookup"><span data-stu-id="75160-514">Examples</span></span>

<span data-ttu-id="75160-515">Geçerli dizinde bir F # konsol uygulaması projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="75160-515">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="75160-516">Belirtilen dizin (yalnızca .NET Core SDK 2.0 veya sonraki sürümler ile kullanılabilir) bir .NET Standard sınıf kitaplığı projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="75160-516">Create a .NET Standard class library project in the specified directory (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="75160-517">Kimlik doğrulaması olmayan geçerli dizinde yeni bir ASP.NET Core C# MVC uygulaması projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="75160-517">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication:</span></span>

`dotnet new mvc -au None`

<span data-ttu-id="75160-518">Yeni bir xUnit uygulama oluşturun:</span><span class="sxs-lookup"><span data-stu-id="75160-518">Create a new xUnit application:</span></span>

`dotnet new xunit`

<span data-ttu-id="75160-519">MVC için tüm şablonları listeler:</span><span class="sxs-lookup"><span data-stu-id="75160-519">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="75160-520">ASP.NET Core (komut seçeneği kullanılabilir .NET Core SDK 1.1 ve yalnızca sonraki sürümleri için) için tek sayfalı uygulama şablonları 2.0 sürümünü yükleyin:</span><span class="sxs-lookup"><span data-stu-id="75160-520">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

<span data-ttu-id="75160-521">Oluşturma bir *global.json* SDK'sı sürüm 2.0.0 (yalnızca .NET Core SDK 2.0 veya sonraki sürümler ile kullanılabilir) ayarı geçerli dizin:</span><span class="sxs-lookup"><span data-stu-id="75160-521">Create a *global.json* in the current directory setting the SDK version to 2.0.0 (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="75160-522">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75160-522">See also</span></span>

* [<span data-ttu-id="75160-523">Yeni dotnet için özel şablonlar</span><span class="sxs-lookup"><span data-stu-id="75160-523">Custom templates for dotnet new</span></span>](custom-templates.md)  
* [<span data-ttu-id="75160-524">Dotnet new için özel şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="75160-524">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)  
* [<span data-ttu-id="75160-525">DotNet/dotnet-şablonu-örnekleri GitHub deposu</span><span class="sxs-lookup"><span data-stu-id="75160-525">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)  
* [<span data-ttu-id="75160-526">Yeni dotnet şablonları</span><span class="sxs-lookup"><span data-stu-id="75160-526">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
