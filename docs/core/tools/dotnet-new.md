---
title: Yeni komut dotnet - .NET Core CLI
description: Belirtilen şablonu temel alan yeni .NET Core projeleri dotnet yeni bir komut oluşturur.
author: mairaw
ms.author: mairaw
ms.date: 10/24/2018
ms.openlocfilehash: 56d76f1dd54097f9cf20129d74057235290c273c
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188214"
---
# <a name="dotnet-new"></a><span data-ttu-id="c3cc0-103">DotNet yeni</span><span class="sxs-lookup"><span data-stu-id="c3cc0-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="c3cc0-104">Ad</span><span class="sxs-lookup"><span data-stu-id="c3cc0-104">Name</span></span>

<span data-ttu-id="c3cc0-105">`dotnet new` -Yeni Proje, yapılandırma dosyası veya belirtilen şablonu temel alan bir çözüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c3cc0-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="c3cc0-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="c3cc0-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="c3cc0-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output]
    [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="c3cc0-108">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="c3cc0-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="c3cc0-109">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="c3cc0-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="c3cc0-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c3cc0-110">Description</span></span>

<span data-ttu-id="c3cc0-111">`dotnet new` Komutu geçerli bir .NET Core projesi başlatmak için kolay bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="c3cc0-112">Komut çağrıları [şablon altyapısı](https://github.com/dotnet/templating) yapıları belirtilen şablonu ve seçenekleri bağlı disk oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="c3cc0-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="c3cc0-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="c3cc0-114">Komut çağrıldığında örneği oluşturmak için şablon.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="c3cc0-115">Her şablon geçirebilirsiniz belirli seçenekler olabilir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="c3cc0-116">Daha fazla bilgi için [şablon seçeneklerini](#template-options).</span><span class="sxs-lookup"><span data-stu-id="c3cc0-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="c3cc0-117">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="c3cc0-117">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="c3cc0-118">Komutu, şablonları, varsayılan listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-118">The command contains a default list of templates.</span></span> <span data-ttu-id="c3cc0-119">Kullanım `dotnet new -l` kullanılabilir şablonların listesini alamadı.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="c3cc0-120">Aşağıdaki tablo, .NET Core SDK 2.1.300 önceden yüklenmiş olarak gelen şablonları gösterir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-120">The following table shows the templates that come pre-installed with the .NET Core SDK 2.1.300.</span></span> <span data-ttu-id="c3cc0-121">Şablonunuz için varsayılan dili köşeli ayraçlar içinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="c3cc0-122">Şablon açıklaması</span><span class="sxs-lookup"><span data-stu-id="c3cc0-122">Template description</span></span>                          | <span data-ttu-id="c3cc0-123">Şablon adı</span><span class="sxs-lookup"><span data-stu-id="c3cc0-123">Template name</span></span>    | <span data-ttu-id="c3cc0-124">Diller</span><span class="sxs-lookup"><span data-stu-id="c3cc0-124">Languages</span></span>     |
|----------------------------------------------|------------------|---------------|
| <span data-ttu-id="c3cc0-125">Konsol uygulaması</span><span class="sxs-lookup"><span data-stu-id="c3cc0-125">Console application</span></span>                          | `console`        | <span data-ttu-id="c3cc0-126">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c3cc0-126">[C#], F#, VB</span></span>  |
| <span data-ttu-id="c3cc0-127">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="c3cc0-127">Class library</span></span>                                | `classlib`       | <span data-ttu-id="c3cc0-128">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c3cc0-128">[C#], F#, VB</span></span>  |
| <span data-ttu-id="c3cc0-129">Birim testi projesi</span><span class="sxs-lookup"><span data-stu-id="c3cc0-129">Unit test project</span></span>                            | `mstest`         | <span data-ttu-id="c3cc0-130">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c3cc0-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="c3cc0-131">xUnit test projesi</span><span class="sxs-lookup"><span data-stu-id="c3cc0-131">xUnit test project</span></span>                           | `xunit`          | <span data-ttu-id="c3cc0-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c3cc0-132">[C#], F#, VB</span></span>  |
| <span data-ttu-id="c3cc0-133">Razor sayfası</span><span class="sxs-lookup"><span data-stu-id="c3cc0-133">Razor page</span></span>                                   | `page`           | <span data-ttu-id="c3cc0-134">[C#]</span><span class="sxs-lookup"><span data-stu-id="c3cc0-134">[C#]</span></span>          |
| <span data-ttu-id="c3cc0-135">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="c3cc0-135">MVC ViewImports</span></span>                              | `viewimports`    | <span data-ttu-id="c3cc0-136">[C#]</span><span class="sxs-lookup"><span data-stu-id="c3cc0-136">[C#]</span></span>          |
| <span data-ttu-id="c3cc0-137">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="c3cc0-137">MVC ViewStart</span></span>                                | `viewstart`      | <span data-ttu-id="c3cc0-138">[C#]</span><span class="sxs-lookup"><span data-stu-id="c3cc0-138">[C#]</span></span>          |
| <span data-ttu-id="c3cc0-139">ASP.NET Core boş</span><span class="sxs-lookup"><span data-stu-id="c3cc0-139">ASP.NET Core empty</span></span>                           | `web`            | <span data-ttu-id="c3cc0-140">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="c3cc0-140">[C#], F#</span></span>      |
| <span data-ttu-id="c3cc0-141">ASP.NET Core Web uygulaması (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="c3cc0-141">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`            | <span data-ttu-id="c3cc0-142">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="c3cc0-142">[C#], F#</span></span>      |
| <span data-ttu-id="c3cc0-143">ASP.NET Core Web uygulaması</span><span class="sxs-lookup"><span data-stu-id="c3cc0-143">ASP.NET Core Web App</span></span>                         | <span data-ttu-id="c3cc0-144">`razor`, `webapp`</span><span class="sxs-lookup"><span data-stu-id="c3cc0-144">`razor`, `webapp`</span></span>| <span data-ttu-id="c3cc0-145">[C#]</span><span class="sxs-lookup"><span data-stu-id="c3cc0-145">[C#]</span></span>          |
| <span data-ttu-id="c3cc0-146">Angular ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c3cc0-146">ASP.NET Core with Angular</span></span>                    | `angular`        | <span data-ttu-id="c3cc0-147">[C#]</span><span class="sxs-lookup"><span data-stu-id="c3cc0-147">[C#]</span></span>          |
| <span data-ttu-id="c3cc0-148">React.js ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c3cc0-148">ASP.NET Core with React.js</span></span>                   | `react`          | <span data-ttu-id="c3cc0-149">[C#]</span><span class="sxs-lookup"><span data-stu-id="c3cc0-149">[C#]</span></span>          |
| <span data-ttu-id="c3cc0-150">ASP.NET Core React.js ve Redux</span><span class="sxs-lookup"><span data-stu-id="c3cc0-150">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`     | <span data-ttu-id="c3cc0-151">[C#]</span><span class="sxs-lookup"><span data-stu-id="c3cc0-151">[C#]</span></span>          |
| <span data-ttu-id="c3cc0-152">ASP.NET Core Web API'si</span><span class="sxs-lookup"><span data-stu-id="c3cc0-152">ASP.NET Core Web API</span></span>                         | `webapi`         | <span data-ttu-id="c3cc0-153">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="c3cc0-153">[C#], F#</span></span>      |
| <span data-ttu-id="c3cc0-154">Razor sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="c3cc0-154">Razor class library</span></span>                          | `razorclasslib`  | <span data-ttu-id="c3cc0-155">[C#]</span><span class="sxs-lookup"><span data-stu-id="c3cc0-155">[C#]</span></span>          |
| <span data-ttu-id="c3cc0-156">Global.JSON dosyasını</span><span class="sxs-lookup"><span data-stu-id="c3cc0-156">global.json file</span></span>                             | `globaljson`     |               |
| <span data-ttu-id="c3cc0-157">NuGet yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c3cc0-157">NuGet config</span></span>                                 | `nugetconfig`    |               |
| <span data-ttu-id="c3cc0-158">Web yapılandırması</span><span class="sxs-lookup"><span data-stu-id="c3cc0-158">Web config</span></span>                                   | `webconfig`      |               |
| <span data-ttu-id="c3cc0-159">Çözüm dosyası</span><span class="sxs-lookup"><span data-stu-id="c3cc0-159">Solution file</span></span>                                | `sln`            |               |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="c3cc0-160">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="c3cc0-160">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="c3cc0-161">Komutu, şablonları, varsayılan listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-161">The command contains a default list of templates.</span></span> <span data-ttu-id="c3cc0-162">Kullanım `dotnet new -l` kullanılabilir şablonların listesini alamadı.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-162">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="c3cc0-163">Aşağıdaki tablo, .NET Core SDK 2.0 ile önceden yüklenmiş olarak gelen şablonları gösterir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-163">The following table shows the templates that come pre-installed with the .NET Core SDK 2.0.</span></span> <span data-ttu-id="c3cc0-164">Şablonunuz için varsayılan dili köşeli ayraçlar içinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-164">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="c3cc0-165">Şablon açıklaması</span><span class="sxs-lookup"><span data-stu-id="c3cc0-165">Template description</span></span>                          | <span data-ttu-id="c3cc0-166">Şablon adı</span><span class="sxs-lookup"><span data-stu-id="c3cc0-166">Template name</span></span> | <span data-ttu-id="c3cc0-167">Diller</span><span class="sxs-lookup"><span data-stu-id="c3cc0-167">Languages</span></span>     |
|----------------------------------------------|---------------|---------------|
| <span data-ttu-id="c3cc0-168">Konsol uygulaması</span><span class="sxs-lookup"><span data-stu-id="c3cc0-168">Console application</span></span>                          | `console`     | <span data-ttu-id="c3cc0-169">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c3cc0-169">[C#], F#, VB</span></span>  |
| <span data-ttu-id="c3cc0-170">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="c3cc0-170">Class library</span></span>                                | `classlib`    | <span data-ttu-id="c3cc0-171">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c3cc0-171">[C#], F#, VB</span></span>  |
| <span data-ttu-id="c3cc0-172">Birim testi projesi</span><span class="sxs-lookup"><span data-stu-id="c3cc0-172">Unit test project</span></span>                            | `mstest`      | <span data-ttu-id="c3cc0-173">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c3cc0-173">[C#], F#, VB</span></span>  |
| <span data-ttu-id="c3cc0-174">xUnit test projesi</span><span class="sxs-lookup"><span data-stu-id="c3cc0-174">xUnit test project</span></span>                           | `xunit`       | <span data-ttu-id="c3cc0-175">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c3cc0-175">[C#], F#, VB</span></span>  |
| <span data-ttu-id="c3cc0-176">ASP.NET Core boş</span><span class="sxs-lookup"><span data-stu-id="c3cc0-176">ASP.NET Core empty</span></span>                           | `web`         | <span data-ttu-id="c3cc0-177">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="c3cc0-177">[C#], F#</span></span>      |
| <span data-ttu-id="c3cc0-178">ASP.NET Core Web uygulaması (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="c3cc0-178">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="c3cc0-179">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="c3cc0-179">[C#], F#</span></span>      |
| <span data-ttu-id="c3cc0-180">ASP.NET Core Web uygulaması</span><span class="sxs-lookup"><span data-stu-id="c3cc0-180">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="c3cc0-181">[C#]</span><span class="sxs-lookup"><span data-stu-id="c3cc0-181">[C#]</span></span>          |
| <span data-ttu-id="c3cc0-182">Angular ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c3cc0-182">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="c3cc0-183">[C#]</span><span class="sxs-lookup"><span data-stu-id="c3cc0-183">[C#]</span></span>          |
| <span data-ttu-id="c3cc0-184">React.js ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c3cc0-184">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="c3cc0-185">[C#]</span><span class="sxs-lookup"><span data-stu-id="c3cc0-185">[C#]</span></span>          |
| <span data-ttu-id="c3cc0-186">ASP.NET Core React.js ve Redux</span><span class="sxs-lookup"><span data-stu-id="c3cc0-186">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="c3cc0-187">[C#]</span><span class="sxs-lookup"><span data-stu-id="c3cc0-187">[C#]</span></span>          |
| <span data-ttu-id="c3cc0-188">ASP.NET Core Web API'si</span><span class="sxs-lookup"><span data-stu-id="c3cc0-188">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="c3cc0-189">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="c3cc0-189">[C#], F#</span></span>      |
| <span data-ttu-id="c3cc0-190">Global.JSON dosyasını</span><span class="sxs-lookup"><span data-stu-id="c3cc0-190">global.json file</span></span>                             | `globaljson`  |               |
| <span data-ttu-id="c3cc0-191">NuGet yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c3cc0-191">NuGet config</span></span>                                 | `nugetconfig` |               |
| <span data-ttu-id="c3cc0-192">Web yapılandırması</span><span class="sxs-lookup"><span data-stu-id="c3cc0-192">Web config</span></span>                                   | `webconfig`   |               |
| <span data-ttu-id="c3cc0-193">Çözüm dosyası</span><span class="sxs-lookup"><span data-stu-id="c3cc0-193">Solution file</span></span>                                | `sln`         |               |
| <span data-ttu-id="c3cc0-194">Razor sayfası</span><span class="sxs-lookup"><span data-stu-id="c3cc0-194">Razor page</span></span>                                   | `page`        |               |
| <span data-ttu-id="c3cc0-195">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="c3cc0-195">MVC ViewImports</span></span>                              | `viewimports` |               |
| <span data-ttu-id="c3cc0-196">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="c3cc0-196">MVC ViewStart</span></span>                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="c3cc0-197">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="c3cc0-197">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="c3cc0-198">Komutu, şablonları, varsayılan listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-198">The command contains a default list of templates.</span></span> <span data-ttu-id="c3cc0-199">Kullanım `dotnet new -all` kullanılabilir şablonların listesini alamadı.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-199">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="c3cc0-200">.NET Core SDK'sı ile önceden yüklenmiş olarak gelen şablonları aşağıdaki tabloda gösterilmektedir 1.x.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-200">The following table shows the templates that come pre-installed with the .NET Core SDK 1.x.</span></span> <span data-ttu-id="c3cc0-201">Şablonunuz için varsayılan dili köşeli ayraçlar içinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-201">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="c3cc0-202">Şablon açıklaması</span><span class="sxs-lookup"><span data-stu-id="c3cc0-202">Template description</span></span>  | <span data-ttu-id="c3cc0-203">Şablon adı</span><span class="sxs-lookup"><span data-stu-id="c3cc0-203">Template name</span></span> | <span data-ttu-id="c3cc0-204">Diller</span><span class="sxs-lookup"><span data-stu-id="c3cc0-204">Languages</span></span> |
|----------------------|---------------|-----------|
| <span data-ttu-id="c3cc0-205">Konsol uygulaması</span><span class="sxs-lookup"><span data-stu-id="c3cc0-205">Console application</span></span>  | `console`     | <span data-ttu-id="c3cc0-206">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="c3cc0-206">[C#], F#</span></span>  |
| <span data-ttu-id="c3cc0-207">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="c3cc0-207">Class library</span></span>        | `classlib`    | <span data-ttu-id="c3cc0-208">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="c3cc0-208">[C#], F#</span></span>  |
| <span data-ttu-id="c3cc0-209">Birim testi projesi</span><span class="sxs-lookup"><span data-stu-id="c3cc0-209">Unit test project</span></span>    | `mstest`      | <span data-ttu-id="c3cc0-210">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="c3cc0-210">[C#], F#</span></span>  |
| <span data-ttu-id="c3cc0-211">xUnit test projesi</span><span class="sxs-lookup"><span data-stu-id="c3cc0-211">xUnit test project</span></span>   | `xunit`       | <span data-ttu-id="c3cc0-212">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="c3cc0-212">[C#], F#</span></span>  |
| <span data-ttu-id="c3cc0-213">ASP.NET Core boş</span><span class="sxs-lookup"><span data-stu-id="c3cc0-213">ASP.NET Core empty</span></span>   | `web`         | <span data-ttu-id="c3cc0-214">[C#]</span><span class="sxs-lookup"><span data-stu-id="c3cc0-214">[C#]</span></span>      |
| <span data-ttu-id="c3cc0-215">ASP.NET Core Web uygulaması</span><span class="sxs-lookup"><span data-stu-id="c3cc0-215">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="c3cc0-216">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="c3cc0-216">[C#], F#</span></span>  |
| <span data-ttu-id="c3cc0-217">ASP.NET Core Web API'si</span><span class="sxs-lookup"><span data-stu-id="c3cc0-217">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="c3cc0-218">[C#]</span><span class="sxs-lookup"><span data-stu-id="c3cc0-218">[C#]</span></span>      |
| <span data-ttu-id="c3cc0-219">NuGet yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c3cc0-219">NuGet config</span></span>         | `nugetconfig` |           |
| <span data-ttu-id="c3cc0-220">Web yapılandırması</span><span class="sxs-lookup"><span data-stu-id="c3cc0-220">Web config</span></span>           | `webconfig`   |           |
| <span data-ttu-id="c3cc0-221">Çözüm dosyası</span><span class="sxs-lookup"><span data-stu-id="c3cc0-221">Solution file</span></span>        | `sln`         |           |

---

## <a name="options"></a><span data-ttu-id="c3cc0-222">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="c3cc0-222">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="c3cc0-223">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="c3cc0-223">.NET Core 2.1</span></span>](#tab/netcore21)

`--force`

<span data-ttu-id="c3cc0-224">Mevcut dosyaları değiştirmek olsa bile oluşturulması gereken içeriği zorlar.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-224">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="c3cc0-225">Bir proje çıkış dizinine içerdiğinde, bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-225">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="c3cc0-226">Komut için Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-226">Prints out help for the command.</span></span> <span data-ttu-id="c3cc0-227">İçin çağrılabilir `dotnet new` kendisini komutu veya herhangi bir şablon gibi `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-227">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="c3cc0-228">Bir kaynak veya şablon paketinden yükler `PATH` veya `NUGET_ID` sağlanan.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-228">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="c3cc0-229">Bir şablon Paketi yayım öncesi bir sürümü yüklemek istediğiniz sürümü biçiminde belirtmek gerekirse `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-229">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="c3cc0-230">Varsayılan olarak, `dotnet new` geçirir \* sürümünü temsil eden en son kararlı Paket sürümü.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-230">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="c3cc0-231">Bir örneğe bakın [örnekler](#examples) bölümü.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-231">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="c3cc0-232">Özel şablonlar oluşturma hakkında daha fazla bilgi için bkz. [yeni dotnet için özel şablonları](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="c3cc0-232">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="c3cc0-233">Belirtilen ad içeren şablonlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-233">Lists templates containing the specified name.</span></span> <span data-ttu-id="c3cc0-234">İçin çağırdıysanız `dotnet new` komut, belirtilen dizinde kullanılabilir olası şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-234">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="c3cc0-235">Örnek dizin zaten bir proje içeriyorsa, tüm proje şablonları listesinde değil.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-235">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="c3cc0-236">Oluşturmak için şablon dili.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-236">The language of the template to create.</span></span> <span data-ttu-id="c3cc0-237">Dil kabul şablon tarafından farklılık gösterir (varsayılan ayarlarında bkz [bağımsız değişkenleri](#arguments) bölümü).</span><span class="sxs-lookup"><span data-stu-id="c3cc0-237">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="c3cc0-238">Bazı şablonlar için geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-238">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="c3cc0-239">Bazı Kabukları yorumlama `#` olarak bir özel karakter.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-239">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="c3cc0-240">Bu gibi durumlarda, dil parametre değeri, aşağıdaki gibi alın gerek `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-240">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="c3cc0-241">Oluşturulan çıktı adı.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-241">The name for the created output.</span></span> <span data-ttu-id="c3cc0-242">Hiçbir ad belirtilmediği takdirde, geçerli dizin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-242">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="c3cc0-243">Yükleme sırasında kullanılacak bir NuGet kaynağı belirtir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-243">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="c3cc0-244">Oluşturulan çıktı yerleştirileceği konumu.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-244">Location to place the generated output.</span></span> <span data-ttu-id="c3cc0-245">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-245">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="c3cc0-246">Şablonları kullanılabilir türlerine göre filtreler.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-246">Filters templates based on available types.</span></span> <span data-ttu-id="c3cc0-247">Önceden tanımlanmış değerler şunlardır: "proje", "Item" veya "diğer".</span><span class="sxs-lookup"><span data-stu-id="c3cc0-247">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="c3cc0-248">Bir kaynak veya şablon paketini kaldırır `PATH` veya `NUGET_ID` sağlanan.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-248">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="c3cc0-249">Bir şablon kullanarak kaldırmak için bir `PATH`, yol tam olarak nitelemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-249">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="c3cc0-250">Örneğin, *C:/Users/\<kullanıcı > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* çalışır, ancak *./GarciaSoftware.ConsoleTemplate.CSharp* içeren gelen Klasör erişemez.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-250">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="c3cc0-251">Ayrıca, şablonu yoldaki son Sonlandırıcı directory eğik çizgi içermez.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-251">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="c3cc0-252">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="c3cc0-252">.NET Core 2.0</span></span>](#tab/netcore20)

`--force`

<span data-ttu-id="c3cc0-253">Mevcut dosyaları değiştirmek olsa bile oluşturulması gereken içeriği zorlar.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-253">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="c3cc0-254">Bir proje çıkış dizinine içerdiğinde, bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-254">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="c3cc0-255">Komut için Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-255">Prints out help for the command.</span></span> <span data-ttu-id="c3cc0-256">İçin çağrılabilir `dotnet new` kendisini komutu veya herhangi bir şablon gibi `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-256">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="c3cc0-257">Bir kaynak veya şablon paketinden yükler `PATH` veya `NUGET_ID` sağlanan.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-257">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="c3cc0-258">Bir şablon Paketi yayım öncesi bir sürümü yüklemek istediğiniz sürümü biçiminde belirtmek gerekirse `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-258">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="c3cc0-259">Varsayılan olarak, `dotnet new` geçirir \* sürümünü temsil eden en son kararlı Paket sürümü.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-259">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="c3cc0-260">Bir örneğe bakın [örnekler](#examples) bölümü.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-260">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="c3cc0-261">Özel şablonlar oluşturma hakkında daha fazla bilgi için bkz. [yeni dotnet için özel şablonları](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="c3cc0-261">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="c3cc0-262">Belirtilen ad içeren şablonlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-262">Lists templates containing the specified name.</span></span> <span data-ttu-id="c3cc0-263">İçin çağırdıysanız `dotnet new` komut, belirtilen dizinde kullanılabilir olası şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-263">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="c3cc0-264">Örnek dizin zaten bir proje içeriyorsa, tüm proje şablonları listesinde değil.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-264">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="c3cc0-265">Oluşturmak için şablon dili.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-265">The language of the template to create.</span></span> <span data-ttu-id="c3cc0-266">Dil kabul şablon tarafından farklılık gösterir (varsayılan ayarlarında bkz [bağımsız değişkenleri](#arguments) bölümü).</span><span class="sxs-lookup"><span data-stu-id="c3cc0-266">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="c3cc0-267">Bazı şablonlar için geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-267">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="c3cc0-268">Bazı Kabukları yorumlama `#` olarak bir özel karakter.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-268">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="c3cc0-269">Bu gibi durumlarda, dil parametre değeri, aşağıdaki gibi alın gerek `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-269">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="c3cc0-270">Oluşturulan çıktı adı.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-270">The name for the created output.</span></span> <span data-ttu-id="c3cc0-271">Hiçbir ad belirtilmediği takdirde, geçerli dizin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-271">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="c3cc0-272">Oluşturulan çıktı yerleştirileceği konumu.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-272">Location to place the generated output.</span></span> <span data-ttu-id="c3cc0-273">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-273">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="c3cc0-274">Şablonları kullanılabilir türlerine göre filtreler.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-274">Filters templates based on available types.</span></span> <span data-ttu-id="c3cc0-275">Önceden tanımlanmış değerler şunlardır: "proje", "Item" veya "diğer".</span><span class="sxs-lookup"><span data-stu-id="c3cc0-275">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="c3cc0-276">Bir kaynak veya şablon paketini kaldırır `PATH` veya `NUGET_ID` sağlanan.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-276">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="c3cc0-277">Bir kaynağı kullanan bir şablonu kaldırmak için `PATH`, yol tam olarak nitelemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-277">To uninstall a template using a source `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="c3cc0-278">Örneğin, *C:/Users/\<kullanıcı > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* çalışır, ancak *./GarciaSoftware.ConsoleTemplate.CSharp* içeren gelen Klasör erişemez.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-278">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span> <span data-ttu-id="c3cc0-279">Ayrıca, şablonu yoldaki son Sonlandırıcı directory eğik çizgi içermez.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-279">Additionally, do not include a final terminating directory slash on your template path.</span></span>
> 
> <span data-ttu-id="c3cc0-280">Belirlemek erişemiyorsanız `PATH` veya `NUGET_ID` çalıştıran, bir şablonu kaldırmak için gerekli bağımsız değişken `dotnet new --uninstall` bağımsız değişken yüklü tüm şablonları ve bunları kaldırmak için gerekli bağımsız değişken listesi olmayan.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-280">If you are unable to determine the `PATH` or `NUGET_ID` argument needed to uninstall a template, running `dotnet new --uninstall` without an argument will list all installed templates and the argument required to uninstall them.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="c3cc0-281">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="c3cc0-281">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="c3cc0-282">Belirli türde bir proje için tüm şablonları'nı bağlamında çalıştırılırken gösterir `dotnet new` tek başına komutu.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-282">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="c3cc0-283">Belirli bir şablon bağlamında gibi çalıştırırken `dotnet new web -all`, `-all` zorla oluşturma bayrak olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-283">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="c3cc0-284">Bir proje çıkış dizinine içerdiğinde, bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-284">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="c3cc0-285">Komut için Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-285">Prints out help for the command.</span></span> <span data-ttu-id="c3cc0-286">İçin çağrılabilir `dotnet new` kendisini komutu veya herhangi bir şablon gibi `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-286">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="c3cc0-287">Belirtilen ad içeren şablonlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-287">Lists templates containing the specified name.</span></span> <span data-ttu-id="c3cc0-288">İçin çağırdıysanız `dotnet new` komut, belirtilen dizinde kullanılabilir olası şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-288">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="c3cc0-289">Örnek dizin zaten bir proje içeriyorsa, tüm proje şablonları listesinde değil.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-289">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="c3cc0-290">Oluşturmak için şablon dili.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-290">The language of the template to create.</span></span> <span data-ttu-id="c3cc0-291">Dil kabul şablon tarafından farklılık gösterir (varsayılan ayarlarında bkz [bağımsız değişkenleri](#arguments) bölümü).</span><span class="sxs-lookup"><span data-stu-id="c3cc0-291">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="c3cc0-292">Bazı şablonlar için geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-292">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="c3cc0-293">Bazı Kabukları yorumlama `#` olarak bir özel karakter.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-293">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="c3cc0-294">Bu gibi durumlarda, dil parametre değeri, aşağıdaki gibi alın gerek `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-294">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="c3cc0-295">Oluşturulan çıktı adı.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-295">The name for the created output.</span></span> <span data-ttu-id="c3cc0-296">Hiçbir ad belirtilmediği takdirde, geçerli dizin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-296">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="c3cc0-297">Oluşturulan çıktı yerleştirileceği konumu.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-297">Location to place the generated output.</span></span> <span data-ttu-id="c3cc0-298">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-298">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="c3cc0-299">Şablon seçenekleri</span><span class="sxs-lookup"><span data-stu-id="c3cc0-299">Template options</span></span>

<span data-ttu-id="c3cc0-300">Her proje şablonu, ek seçenekler kullanılabilir olabilir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-300">Each project template may have additional options available.</span></span> <span data-ttu-id="c3cc0-301">Çekirdek şablonları aşağıdaki ek seçeneklere sahip olursunuz:</span><span class="sxs-lookup"><span data-stu-id="c3cc0-301">The core templates have the following additional options:</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="c3cc0-302">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="c3cc0-302">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="c3cc0-303">**konsolunda, angular, react, açarken kilitlenmesi, razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="c3cc0-303">**console, angular, react, reactredux, razorclasslib**</span></span>

  <span data-ttu-id="c3cc0-304">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-304">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c3cc0-305">**ClassLib**</span><span class="sxs-lookup"><span data-stu-id="c3cc0-305">**classlib**</span></span>

<span data-ttu-id="c3cc0-306">`-f|--framework <FRAMEWORK>` -Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-306">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c3cc0-307">Değerler: `netcoreapp2.0` bir .NET Core sınıf kitaplığı oluşturmak için veya `netstandard2.0` .NET standart sınıf kitaplığı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-307">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="c3cc0-308">Varsayılan değer `netstandard2.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-308">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="c3cc0-309">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-309">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c3cc0-310">**MSTest, xunit**</span><span class="sxs-lookup"><span data-stu-id="c3cc0-310">**mstest, xunit**</span></span>

<span data-ttu-id="c3cc0-311">`-p|--enable-pack` -Etkinleştirir kullanarak projeyi için paketleme [dotnet paketi](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="c3cc0-311">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="c3cc0-312">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-312">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c3cc0-313">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="c3cc0-313">**globaljson**</span></span>

<span data-ttu-id="c3cc0-314">`--sdk-version <VERSION_NUMBER>` -Kullanmak için .NET Core SDK'sı sürümünü belirtir *global.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-314">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="c3cc0-315">**Web**</span><span class="sxs-lookup"><span data-stu-id="c3cc0-315">**web**</span></span>

<span data-ttu-id="c3cc0-316">`--exclude-launch-settings` -Hariç *launchSettings.json* oluşturulan şablonundan.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-316">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="c3cc0-317">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-317">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c3cc0-318">`--no-https` -Proje HTTPS'yi gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-318">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="c3cc0-319">Bu seçenek yalnızca geçerlidir `IndividualAuth` veya `OrganizationalAuth` kullanılmayan.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-319">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="c3cc0-320">**webapı**</span><span class="sxs-lookup"><span data-stu-id="c3cc0-320">**webapi**</span></span>

<span data-ttu-id="c3cc0-321">`-au|--auth <AUTHENTICATION_TYPE>` -Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-321">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="c3cc0-322">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="c3cc0-322">The possible values are:</span></span>

- <span data-ttu-id="c3cc0-323">`None` -Kimlik doğrulama yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="c3cc0-323">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="c3cc0-324">`IndividualB2C` -Azure AD B2C ile kimlik doğrulaması tek tek.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-324">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="c3cc0-325">`SingleOrg` -Kuruluş kimlik doğrulaması için tek bir kiracı.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-325">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="c3cc0-326">`Windows` -Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-326">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="c3cc0-327">`--aad-b2c-instance <INSTANCE>` -Bağlanmak için Azure Active Directory B2C örnek.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-327">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="c3cc0-328">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-328">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="c3cc0-329">Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-329">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="c3cc0-330">`-ssp|--susi-policy-id <ID>` -Bu proje için oturum açma ve kaydolma ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-330">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="c3cc0-331">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-331">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c3cc0-332">`--aad-instance <INSTANCE>` -Bağlanmak için Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-332">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="c3cc0-333">İle kullanma `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-333">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="c3cc0-334">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-334">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="c3cc0-335">`--client-id <ID>` -Bu proje için istemci kimliği.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-335">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="c3cc0-336">İle kullanma `IndividualB2C` veya `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-336">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="c3cc0-337">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-337">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="c3cc0-338">`--domain <DOMAIN>` -Dizin kiracısı için etki alanı.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-338">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="c3cc0-339">İle kullanma `SingleOrg` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-339">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c3cc0-340">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-340">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="c3cc0-341">`--tenant-id <ID>` -Tenantıd bağlanmak için kimliği dizini.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-341">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="c3cc0-342">İle kullanma `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-342">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="c3cc0-343">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-343">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="c3cc0-344">`-r|--org-read-access` -Bu uygulamanın dizine okuma erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-344">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="c3cc0-345">Yalnızca uygulandığı `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-345">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="c3cc0-346">`--exclude-launch-settings` -Hariç *launchSettings.json* oluşturulan şablonundan.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-346">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="c3cc0-347">`-uld|--use-local-db` -LocalDB yerine SQLite kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-347">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="c3cc0-348">Yalnızca uygulandığı `Individual` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-348">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c3cc0-349">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-349">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c3cc0-350">`--no-https` -Proje HTTPS'yi gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-350">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="c3cc0-351">`app.UseHsts` ve `app.UseHttpsRedirection` için eklenmez `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-351">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="c3cc0-352">Bu seçenek yalnızca geçerlidir `Individual`, `IndividualB2C`, `SingleOrg`, veya `MultiOrg` kullanılmayan.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-352">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="c3cc0-353">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="c3cc0-353">**mvc, razor**</span></span>

<span data-ttu-id="c3cc0-354">`-au|--auth <AUTHENTICATION_TYPE>` -Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-354">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="c3cc0-355">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="c3cc0-355">The possible values are:</span></span>

- <span data-ttu-id="c3cc0-356">`None` -Kimlik doğrulama yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="c3cc0-356">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="c3cc0-357">`Individual` -Tek tek kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-357">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="c3cc0-358">`IndividualB2C` -Azure AD B2C ile kimlik doğrulaması tek tek.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-358">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="c3cc0-359">`SingleOrg` -Kuruluş kimlik doğrulaması için tek bir kiracı.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-359">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="c3cc0-360">`MultiOrg` -Birden fazla Kiracı için Kurumsal kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-360">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="c3cc0-361">`Windows` -Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-361">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="c3cc0-362">`--aad-b2c-instance <INSTANCE>` -Bağlanmak için Azure Active Directory B2C örnek.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-362">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="c3cc0-363">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-363">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="c3cc0-364">Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-364">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="c3cc0-365">`-ssp|--susi-policy-id <ID>` -Bu proje için oturum açma ve kaydolma ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-365">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="c3cc0-366">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-366">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c3cc0-367">`-rp|--reset-password-policy-id <ID>` -Bu proje için reset parola ilkesi kimliği.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-367">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="c3cc0-368">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-368">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c3cc0-369">`-ep|--edit-profile-policy-id <ID>` -Bu proje için düzenleme profili ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-369">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="c3cc0-370">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-370">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c3cc0-371">`--aad-instance <INSTANCE>` -Bağlanmak için Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-371">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="c3cc0-372">İle kullanma `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-372">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="c3cc0-373">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-373">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="c3cc0-374">`--client-id <ID>` -Bu proje için istemci kimliği.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-374">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="c3cc0-375">İle kullanma `IndividualB2C`, `SingleOrg`, veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-375">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="c3cc0-376">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-376">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="c3cc0-377">`--domain <DOMAIN>` -Dizin kiracısı için etki alanı.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-377">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="c3cc0-378">İle kullanma `SingleOrg` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-378">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c3cc0-379">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-379">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="c3cc0-380">`--tenant-id <ID>` -Tenantıd bağlanmak için kimliği dizini.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-380">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="c3cc0-381">İle kullanma `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-381">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="c3cc0-382">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-382">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="c3cc0-383">`--callback-path <PATH>` -Yeniden yönlendirme URI'si uygulamanın taban yolu içindeki istek yolu.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-383">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="c3cc0-384">İle kullanma `SingleOrg` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-384">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c3cc0-385">Varsayılan değer `/signin-oidc` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-385">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="c3cc0-386">`-r|--org-read-access` -Bu uygulamanın dizine okuma erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-386">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="c3cc0-387">Yalnızca uygulandığı `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-387">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="c3cc0-388">`--exclude-launch-settings` -Hariç *launchSettings.json* oluşturulan şablonundan.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-388">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="c3cc0-389">`--use-browserlink` -BrowserLink projede içerir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-389">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="c3cc0-390">`-uld|--use-local-db` -LocalDB yerine SQLite kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-390">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="c3cc0-391">Yalnızca uygulandığı `Individual` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-391">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c3cc0-392">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-392">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c3cc0-393">`--no-https` -Proje HTTPS'yi gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-393">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="c3cc0-394">`app.UseHsts` ve `app.UseHttpsRedirection` için eklenmez `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-394">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="c3cc0-395">Bu seçenek yalnızca geçerlidir `Individual`, `IndividualB2C`, `SingleOrg`, veya `MultiOrg` kullanılmayan.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-395">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="c3cc0-396">**Sayfa**</span><span class="sxs-lookup"><span data-stu-id="c3cc0-396">**page**</span></span>

<span data-ttu-id="c3cc0-397">`-na|--namespace <NAMESPACE_NAME>`-Namespace üretilen kod için.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-397">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="c3cc0-398">Varsayılan değer `MyApp.Namespace` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-398">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="c3cc0-399">`-np|--no-pagemodel` -Bir PageModel olmadan sayfası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-399">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="c3cc0-400">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="c3cc0-400">**viewimports**</span></span>

<span data-ttu-id="c3cc0-401">`-na|--namespace <NAMESPACE_NAME>`-Namespace üretilen kod için.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-401">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="c3cc0-402">Varsayılan değer `MyApp.Namespace` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-402">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="c3cc0-403">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="c3cc0-403">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="c3cc0-404">**konsolunda, angular, react, açarken kilitlenmesi**</span><span class="sxs-lookup"><span data-stu-id="c3cc0-404">**console, angular, react, reactredux**</span></span>

  <span data-ttu-id="c3cc0-405">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-405">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c3cc0-406">**ClassLib**</span><span class="sxs-lookup"><span data-stu-id="c3cc0-406">**classlib**</span></span>

<span data-ttu-id="c3cc0-407">`-f|--framework <FRAMEWORK>` -Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-407">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c3cc0-408">Değerler: `netcoreapp2.0` bir .NET Core sınıf kitaplığı oluşturmak için veya `netstandard2.0` .NET standart sınıf kitaplığı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-408">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="c3cc0-409">Varsayılan değer `netstandard2.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-409">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="c3cc0-410">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-410">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c3cc0-411">**MSTest, xunit**</span><span class="sxs-lookup"><span data-stu-id="c3cc0-411">**mstest, xunit**</span></span>

<span data-ttu-id="c3cc0-412">`-p|--enable-pack` -Etkinleştirir kullanarak projeyi için paketleme [dotnet paketi](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="c3cc0-412">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="c3cc0-413">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-413">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c3cc0-414">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="c3cc0-414">**globaljson**</span></span>

<span data-ttu-id="c3cc0-415">`--sdk-version <VERSION_NUMBER>` -Kullanmak için .NET Core SDK'sı sürümünü belirtir *global.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-415">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="c3cc0-416">**Web**</span><span class="sxs-lookup"><span data-stu-id="c3cc0-416">**web**</span></span>

<span data-ttu-id="c3cc0-417">`--use-launch-settings` -İçeren *launchSettings.json* oluşturulan şablon çıktı.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-417">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="c3cc0-418">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-418">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c3cc0-419">**webapı**</span><span class="sxs-lookup"><span data-stu-id="c3cc0-419">**webapi**</span></span>

<span data-ttu-id="c3cc0-420">`-au|--auth <AUTHENTICATION_TYPE>` -Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-420">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="c3cc0-421">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="c3cc0-421">The possible values are:</span></span>

- <span data-ttu-id="c3cc0-422">`None` -Kimlik doğrulama yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="c3cc0-422">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="c3cc0-423">`IndividualB2C` -Azure AD B2C ile kimlik doğrulaması tek tek.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-423">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="c3cc0-424">`SingleOrg` -Kuruluş kimlik doğrulaması için tek bir kiracı.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-424">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="c3cc0-425">`Windows` -Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-425">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="c3cc0-426">`--aad-b2c-instance <INSTANCE>` -Bağlanmak için Azure Active Directory B2C örnek.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-426">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="c3cc0-427">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-427">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="c3cc0-428">Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-428">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="c3cc0-429">`-ssp|--susi-policy-id <ID>` -Bu proje için oturum açma ve kaydolma ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-429">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="c3cc0-430">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-430">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c3cc0-431">`--aad-instance <INSTANCE>` -Bağlanmak için Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-431">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="c3cc0-432">İle kullanma `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-432">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="c3cc0-433">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-433">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="c3cc0-434">`--client-id <ID>` -Bu proje için istemci kimliği.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-434">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="c3cc0-435">İle kullanma `IndividualB2C` veya `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-435">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="c3cc0-436">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-436">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="c3cc0-437">`--domain <DOMAIN>` -Dizin kiracısı için etki alanı.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-437">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="c3cc0-438">İle kullanma `SingleOrg` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-438">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c3cc0-439">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-439">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="c3cc0-440">`--tenant-id <ID>` -Tenantıd bağlanmak için kimliği dizini.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-440">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="c3cc0-441">İle kullanma `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-441">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="c3cc0-442">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-442">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="c3cc0-443">`-r|--org-read-access` -Bu uygulamanın dizine okuma erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-443">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="c3cc0-444">Yalnızca uygulandığı `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-444">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="c3cc0-445">`--use-launch-settings` -İçeren *launchSettings.json* oluşturulan şablon çıktı.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-445">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="c3cc0-446">`-uld|--use-local-db` -LocalDB yerine SQLite kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-446">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="c3cc0-447">Yalnızca uygulandığı `Individual` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-447">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c3cc0-448">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-448">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c3cc0-449">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="c3cc0-449">**mvc, razor**</span></span>

<span data-ttu-id="c3cc0-450">`-au|--auth <AUTHENTICATION_TYPE>` -Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-450">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="c3cc0-451">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="c3cc0-451">The possible values are:</span></span>

- <span data-ttu-id="c3cc0-452">`None` -Kimlik doğrulama yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="c3cc0-452">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="c3cc0-453">`Individual` -Tek tek kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-453">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="c3cc0-454">`IndividualB2C` -Azure AD B2C ile kimlik doğrulaması tek tek.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-454">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="c3cc0-455">`SingleOrg` -Kuruluş kimlik doğrulaması için tek bir kiracı.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-455">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="c3cc0-456">`MultiOrg` -Birden fazla Kiracı için Kurumsal kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-456">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="c3cc0-457">`Windows` -Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-457">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="c3cc0-458">`--aad-b2c-instance <INSTANCE>` -Bağlanmak için Azure Active Directory B2C örnek.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-458">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="c3cc0-459">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-459">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="c3cc0-460">Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-460">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="c3cc0-461">`-ssp|--susi-policy-id <ID>` -Bu proje için oturum açma ve kaydolma ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-461">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="c3cc0-462">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-462">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c3cc0-463">`-rp|--reset-password-policy-id <ID>` -Bu proje için reset parola ilkesi kimliği.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-463">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="c3cc0-464">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-464">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c3cc0-465">`-ep|--edit-profile-policy-id <ID>` -Bu proje için düzenleme profili ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-465">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="c3cc0-466">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-466">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c3cc0-467">`--aad-instance <INSTANCE>` -Bağlanmak için Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-467">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="c3cc0-468">İle kullanma `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-468">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="c3cc0-469">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-469">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="c3cc0-470">`--client-id <ID>` -Bu proje için istemci kimliği.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-470">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="c3cc0-471">İle kullanma `IndividualB2C`, `SingleOrg`, veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-471">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="c3cc0-472">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-472">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="c3cc0-473">`--domain <DOMAIN>` -Dizin kiracısı için etki alanı.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-473">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="c3cc0-474">İle kullanma `SingleOrg` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-474">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c3cc0-475">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-475">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="c3cc0-476">`--tenant-id <ID>` -Tenantıd bağlanmak için kimliği dizini.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-476">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="c3cc0-477">İle kullanma `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-477">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="c3cc0-478">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-478">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="c3cc0-479">`--callback-path <PATH>` -Yeniden yönlendirme URI'si uygulamanın taban yolu içindeki istek yolu.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-479">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="c3cc0-480">İle kullanma `SingleOrg` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-480">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c3cc0-481">Varsayılan değer `/signin-oidc` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-481">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="c3cc0-482">`-r|--org-read-access` -Bu uygulamanın dizine okuma erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-482">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="c3cc0-483">Yalnızca uygulandığı `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-483">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="c3cc0-484">`--use-launch-settings` -İçeren *launchSettings.json* oluşturulan şablon çıktı.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-484">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="c3cc0-485">`--use-browserlink` -BrowserLink projede içerir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-485">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="c3cc0-486">`-uld|--use-local-db` -LocalDB yerine SQLite kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-486">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="c3cc0-487">Yalnızca uygulandığı `Individual` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-487">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c3cc0-488">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-488">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c3cc0-489">**Sayfa**</span><span class="sxs-lookup"><span data-stu-id="c3cc0-489">**page**</span></span>

<span data-ttu-id="c3cc0-490">`-na|--namespace <NAMESPACE_NAME>`-Namespace üretilen kod için.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-490">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="c3cc0-491">Varsayılan değer `MyApp.Namespace` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-491">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="c3cc0-492">`-np|--no-pagemodel` -Bir PageModel olmadan sayfası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-492">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="c3cc0-493">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="c3cc0-493">**viewimports**</span></span>

<span data-ttu-id="c3cc0-494">`-na|--namespace <NAMESPACE_NAME>`-Namespace üretilen kod için.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-494">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="c3cc0-495">Varsayılan değer `MyApp.Namespace` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-495">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="c3cc0-496">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="c3cc0-496">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="c3cc0-497">**Konsolu, xunit, mstest, web, webapı**</span><span class="sxs-lookup"><span data-stu-id="c3cc0-497">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="c3cc0-498">`-f|--framework` -Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-498">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c3cc0-499">Değerler: `netcoreapp1.0` veya `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-499">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="c3cc0-500">Varsayılan değer `netcoreapp1.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-500">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="c3cc0-501">**ClassLib**</span><span class="sxs-lookup"><span data-stu-id="c3cc0-501">**classlib**</span></span>

<span data-ttu-id="c3cc0-502">`-f|--framework` -Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-502">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c3cc0-503">Değerler: `netcoreapp1.0`, `netcoreapp1.1`, veya `netstandard1.0` için `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-503">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="c3cc0-504">Varsayılan değer `netstandard1.4` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-504">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="c3cc0-505">**mvc**</span><span class="sxs-lookup"><span data-stu-id="c3cc0-505">**mvc**</span></span>

<span data-ttu-id="c3cc0-506">`-f|--framework` -Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-506">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c3cc0-507">Değerler: `netcoreapp1.0` veya `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-507">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="c3cc0-508">Varsayılan değer `netcoreapp1.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-508">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="c3cc0-509">`-au|--auth` -Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-509">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="c3cc0-510">Değerler: `None` veya `Individual`.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-510">Values: `None` or `Individual`.</span></span> <span data-ttu-id="c3cc0-511">Varsayılan değer `None` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-511">The default value is `None`.</span></span>

<span data-ttu-id="c3cc0-512">`-uld|--use-local-db` -LocalDB yerine SQLite kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-512">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="c3cc0-513">Değerler: `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-513">Values: `true` or `false`.</span></span> <span data-ttu-id="c3cc0-514">Varsayılan değer `false` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-514">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="c3cc0-515">Örnekler</span><span class="sxs-lookup"><span data-stu-id="c3cc0-515">Examples</span></span>

<span data-ttu-id="c3cc0-516">Geçerli dizinde bir F # konsol uygulaması projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="c3cc0-516">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="c3cc0-517">Belirtilen dizin (yalnızca .NET Core SDK 2.0 veya sonraki sürümler ile kullanılabilir) bir .NET Standard sınıf kitaplığı projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="c3cc0-517">Create a .NET Standard class library project in the specified directory (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="c3cc0-518">Kimlik doğrulaması olmayan geçerli dizinde yeni bir ASP.NET Core C# MVC uygulaması projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="c3cc0-518">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication:</span></span>

`dotnet new mvc -au None`

<span data-ttu-id="c3cc0-519">Yeni bir xUnit uygulama oluşturun:</span><span class="sxs-lookup"><span data-stu-id="c3cc0-519">Create a new xUnit application:</span></span>

`dotnet new xunit`

<span data-ttu-id="c3cc0-520">MVC için tüm şablonları listeler:</span><span class="sxs-lookup"><span data-stu-id="c3cc0-520">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="c3cc0-521">ASP.NET Core (komut seçeneği kullanılabilir .NET Core SDK 1.1 ve yalnızca sonraki sürümleri için) için tek sayfalı uygulama şablonları 2.0 sürümünü yükleyin:</span><span class="sxs-lookup"><span data-stu-id="c3cc0-521">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

<span data-ttu-id="c3cc0-522">Oluşturma bir *global.json* SDK'sı sürüm 2.0.0 (yalnızca .NET Core SDK 2.0 veya sonraki sürümler ile kullanılabilir) ayarı geçerli dizin:</span><span class="sxs-lookup"><span data-stu-id="c3cc0-522">Create a *global.json* in the current directory setting the SDK version to 2.0.0 (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="c3cc0-523">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c3cc0-523">See also</span></span>

* [<span data-ttu-id="c3cc0-524">Yeni dotnet için özel şablonlar</span><span class="sxs-lookup"><span data-stu-id="c3cc0-524">Custom templates for dotnet new</span></span>](custom-templates.md)  
* [<span data-ttu-id="c3cc0-525">Dotnet new için özel şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="c3cc0-525">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)  
* [<span data-ttu-id="c3cc0-526">DotNet/dotnet-şablonu-örnekleri GitHub deposu</span><span class="sxs-lookup"><span data-stu-id="c3cc0-526">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)  
* [<span data-ttu-id="c3cc0-527">Yeni dotnet şablonları</span><span class="sxs-lookup"><span data-stu-id="c3cc0-527">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
