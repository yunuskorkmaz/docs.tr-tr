---
title: DotNet yeni komutu
description: Belirtilen şablonu temel alan yeni .NET Core projeleri dotnet yeni bir komut oluşturur.
ms.date: 10/24/2018
ms.openlocfilehash: 5177c920fee6fa946d2bf5d96644f26309ed0a99
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54516154"
---
# <a name="dotnet-new"></a><span data-ttu-id="37afa-103">DotNet yeni</span><span class="sxs-lookup"><span data-stu-id="37afa-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="37afa-104">Ad</span><span class="sxs-lookup"><span data-stu-id="37afa-104">Name</span></span>

<span data-ttu-id="37afa-105">`dotnet new` -Yeni Proje, yapılandırma dosyası veya belirtilen şablonu temel alan bir çözüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="37afa-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="37afa-106">Synopsis</span><span class="sxs-lookup"><span data-stu-id="37afa-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="37afa-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="37afa-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output]
    [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="37afa-108">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="37afa-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="37afa-109">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="37afa-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="37afa-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="37afa-110">Description</span></span>

<span data-ttu-id="37afa-111">`dotnet new` Komutu geçerli bir .NET Core projesi başlatmak için kolay bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="37afa-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="37afa-112">Komut çağrıları [şablon altyapısı](https://github.com/dotnet/templating) yapıları belirtilen şablonu ve seçenekleri bağlı disk oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="37afa-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="37afa-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="37afa-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="37afa-114">Komut çağrıldığında örneği oluşturmak için şablon.</span><span class="sxs-lookup"><span data-stu-id="37afa-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="37afa-115">Her şablon geçirebilirsiniz belirli seçenekler olabilir.</span><span class="sxs-lookup"><span data-stu-id="37afa-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="37afa-116">Daha fazla bilgi için [şablon seçeneklerini](#template-options).</span><span class="sxs-lookup"><span data-stu-id="37afa-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="37afa-117">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="37afa-117">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="37afa-118">Komutu, şablonları, varsayılan listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="37afa-118">The command contains a default list of templates.</span></span> <span data-ttu-id="37afa-119">Kullanım `dotnet new -l` kullanılabilir şablonların listesini alamadı.</span><span class="sxs-lookup"><span data-stu-id="37afa-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="37afa-120">Aşağıdaki tablo, .NET Core SDK 2.1.300 önceden yüklenmiş olarak gelen şablonları gösterir.</span><span class="sxs-lookup"><span data-stu-id="37afa-120">The following table shows the templates that come pre-installed with the .NET Core SDK 2.1.300.</span></span> <span data-ttu-id="37afa-121">Şablonunuz için varsayılan dili köşeli ayraçlar içinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="37afa-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="37afa-122">Şablon açıklaması</span><span class="sxs-lookup"><span data-stu-id="37afa-122">Template description</span></span>                          | <span data-ttu-id="37afa-123">Şablon adı</span><span class="sxs-lookup"><span data-stu-id="37afa-123">Template name</span></span>    | <span data-ttu-id="37afa-124">Diller</span><span class="sxs-lookup"><span data-stu-id="37afa-124">Languages</span></span>     |
|----------------------------------------------|------------------|---------------|
| <span data-ttu-id="37afa-125">Konsol uygulaması</span><span class="sxs-lookup"><span data-stu-id="37afa-125">Console application</span></span>                          | `console`        | <span data-ttu-id="37afa-126">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="37afa-126">[C#], F#, VB</span></span>  |
| <span data-ttu-id="37afa-127">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="37afa-127">Class library</span></span>                                | `classlib`       | <span data-ttu-id="37afa-128">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="37afa-128">[C#], F#, VB</span></span>  |
| <span data-ttu-id="37afa-129">Birim testi projesi</span><span class="sxs-lookup"><span data-stu-id="37afa-129">Unit test project</span></span>                            | `mstest`         | <span data-ttu-id="37afa-130">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="37afa-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="37afa-131">xUnit test projesi</span><span class="sxs-lookup"><span data-stu-id="37afa-131">xUnit test project</span></span>                           | `xunit`          | <span data-ttu-id="37afa-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="37afa-132">[C#], F#, VB</span></span>  |
| <span data-ttu-id="37afa-133">NUnit test projesi</span><span class="sxs-lookup"><span data-stu-id="37afa-133">NUnit test project</span></span>                           | `nunit`          | <span data-ttu-id="37afa-134">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="37afa-134">[C#], F#, VB</span></span>  |
| <span data-ttu-id="37afa-135">Razor sayfası</span><span class="sxs-lookup"><span data-stu-id="37afa-135">Razor page</span></span>                                   | `page`           | <span data-ttu-id="37afa-136">[C#]</span><span class="sxs-lookup"><span data-stu-id="37afa-136">[C#]</span></span>          |
| <span data-ttu-id="37afa-137">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="37afa-137">MVC ViewImports</span></span>                              | `viewimports`    | <span data-ttu-id="37afa-138">[C#]</span><span class="sxs-lookup"><span data-stu-id="37afa-138">[C#]</span></span>          |
| <span data-ttu-id="37afa-139">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="37afa-139">MVC ViewStart</span></span>                                | `viewstart`      | <span data-ttu-id="37afa-140">[C#]</span><span class="sxs-lookup"><span data-stu-id="37afa-140">[C#]</span></span>          |
| <span data-ttu-id="37afa-141">ASP.NET Core boş</span><span class="sxs-lookup"><span data-stu-id="37afa-141">ASP.NET Core empty</span></span>                           | `web`            | <span data-ttu-id="37afa-142">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="37afa-142">[C#], F#</span></span>      |
| <span data-ttu-id="37afa-143">ASP.NET Core Web uygulaması (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="37afa-143">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`            | <span data-ttu-id="37afa-144">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="37afa-144">[C#], F#</span></span>      |
| <span data-ttu-id="37afa-145">ASP.NET Core Web uygulaması</span><span class="sxs-lookup"><span data-stu-id="37afa-145">ASP.NET Core Web App</span></span>                         | <span data-ttu-id="37afa-146">`razor`, `webapp`</span><span class="sxs-lookup"><span data-stu-id="37afa-146">`razor`, `webapp`</span></span>| <span data-ttu-id="37afa-147">[C#]</span><span class="sxs-lookup"><span data-stu-id="37afa-147">[C#]</span></span>          |
| <span data-ttu-id="37afa-148">Angular ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="37afa-148">ASP.NET Core with Angular</span></span>                    | `angular`        | <span data-ttu-id="37afa-149">[C#]</span><span class="sxs-lookup"><span data-stu-id="37afa-149">[C#]</span></span>          |
| <span data-ttu-id="37afa-150">React.js ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="37afa-150">ASP.NET Core with React.js</span></span>                   | `react`          | <span data-ttu-id="37afa-151">[C#]</span><span class="sxs-lookup"><span data-stu-id="37afa-151">[C#]</span></span>          |
| <span data-ttu-id="37afa-152">ASP.NET Core React.js ve Redux</span><span class="sxs-lookup"><span data-stu-id="37afa-152">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`     | <span data-ttu-id="37afa-153">[C#]</span><span class="sxs-lookup"><span data-stu-id="37afa-153">[C#]</span></span>          |
| <span data-ttu-id="37afa-154">ASP.NET Core Web API'si</span><span class="sxs-lookup"><span data-stu-id="37afa-154">ASP.NET Core Web API</span></span>                         | `webapi`         | <span data-ttu-id="37afa-155">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="37afa-155">[C#], F#</span></span>      |
| <span data-ttu-id="37afa-156">Razor sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="37afa-156">Razor class library</span></span>                          | `razorclasslib`  | <span data-ttu-id="37afa-157">[C#]</span><span class="sxs-lookup"><span data-stu-id="37afa-157">[C#]</span></span>          |
| <span data-ttu-id="37afa-158">Global.JSON dosyasını</span><span class="sxs-lookup"><span data-stu-id="37afa-158">global.json file</span></span>                             | `globaljson`     |               |
| <span data-ttu-id="37afa-159">NuGet yapılandırma</span><span class="sxs-lookup"><span data-stu-id="37afa-159">NuGet config</span></span>                                 | `nugetconfig`    |               |
| <span data-ttu-id="37afa-160">Web yapılandırması</span><span class="sxs-lookup"><span data-stu-id="37afa-160">Web config</span></span>                                   | `webconfig`      |               |
| <span data-ttu-id="37afa-161">Çözüm dosyası</span><span class="sxs-lookup"><span data-stu-id="37afa-161">Solution file</span></span>                                | `sln`            |               |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="37afa-162">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="37afa-162">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="37afa-163">Komutu, şablonları, varsayılan listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="37afa-163">The command contains a default list of templates.</span></span> <span data-ttu-id="37afa-164">Kullanım `dotnet new -l` kullanılabilir şablonların listesini alamadı.</span><span class="sxs-lookup"><span data-stu-id="37afa-164">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="37afa-165">Aşağıdaki tablo, .NET Core SDK 2.0 ile önceden yüklenmiş olarak gelen şablonları gösterir.</span><span class="sxs-lookup"><span data-stu-id="37afa-165">The following table shows the templates that come pre-installed with the .NET Core SDK 2.0.</span></span> <span data-ttu-id="37afa-166">Şablonunuz için varsayılan dili köşeli ayraçlar içinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="37afa-166">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="37afa-167">Şablon açıklaması</span><span class="sxs-lookup"><span data-stu-id="37afa-167">Template description</span></span>                          | <span data-ttu-id="37afa-168">Şablon adı</span><span class="sxs-lookup"><span data-stu-id="37afa-168">Template name</span></span> | <span data-ttu-id="37afa-169">Diller</span><span class="sxs-lookup"><span data-stu-id="37afa-169">Languages</span></span>     |
|----------------------------------------------|---------------|---------------|
| <span data-ttu-id="37afa-170">Konsol uygulaması</span><span class="sxs-lookup"><span data-stu-id="37afa-170">Console application</span></span>                          | `console`     | <span data-ttu-id="37afa-171">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="37afa-171">[C#], F#, VB</span></span>  |
| <span data-ttu-id="37afa-172">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="37afa-172">Class library</span></span>                                | `classlib`    | <span data-ttu-id="37afa-173">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="37afa-173">[C#], F#, VB</span></span>  |
| <span data-ttu-id="37afa-174">Birim testi projesi</span><span class="sxs-lookup"><span data-stu-id="37afa-174">Unit test project</span></span>                            | `mstest`      | <span data-ttu-id="37afa-175">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="37afa-175">[C#], F#, VB</span></span>  |
| <span data-ttu-id="37afa-176">xUnit test projesi</span><span class="sxs-lookup"><span data-stu-id="37afa-176">xUnit test project</span></span>                           | `xunit`       | <span data-ttu-id="37afa-177">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="37afa-177">[C#], F#, VB</span></span>  |
| <span data-ttu-id="37afa-178">ASP.NET Core boş</span><span class="sxs-lookup"><span data-stu-id="37afa-178">ASP.NET Core empty</span></span>                           | `web`         | <span data-ttu-id="37afa-179">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="37afa-179">[C#], F#</span></span>      |
| <span data-ttu-id="37afa-180">ASP.NET Core Web uygulaması (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="37afa-180">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="37afa-181">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="37afa-181">[C#], F#</span></span>      |
| <span data-ttu-id="37afa-182">ASP.NET Core Web uygulaması</span><span class="sxs-lookup"><span data-stu-id="37afa-182">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="37afa-183">[C#]</span><span class="sxs-lookup"><span data-stu-id="37afa-183">[C#]</span></span>          |
| <span data-ttu-id="37afa-184">Angular ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="37afa-184">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="37afa-185">[C#]</span><span class="sxs-lookup"><span data-stu-id="37afa-185">[C#]</span></span>          |
| <span data-ttu-id="37afa-186">React.js ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="37afa-186">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="37afa-187">[C#]</span><span class="sxs-lookup"><span data-stu-id="37afa-187">[C#]</span></span>          |
| <span data-ttu-id="37afa-188">ASP.NET Core React.js ve Redux</span><span class="sxs-lookup"><span data-stu-id="37afa-188">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="37afa-189">[C#]</span><span class="sxs-lookup"><span data-stu-id="37afa-189">[C#]</span></span>          |
| <span data-ttu-id="37afa-190">ASP.NET Core Web API'si</span><span class="sxs-lookup"><span data-stu-id="37afa-190">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="37afa-191">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="37afa-191">[C#], F#</span></span>      |
| <span data-ttu-id="37afa-192">Global.JSON dosyasını</span><span class="sxs-lookup"><span data-stu-id="37afa-192">global.json file</span></span>                             | `globaljson`  |               |
| <span data-ttu-id="37afa-193">NuGet yapılandırma</span><span class="sxs-lookup"><span data-stu-id="37afa-193">NuGet config</span></span>                                 | `nugetconfig` |               |
| <span data-ttu-id="37afa-194">Web yapılandırması</span><span class="sxs-lookup"><span data-stu-id="37afa-194">Web config</span></span>                                   | `webconfig`   |               |
| <span data-ttu-id="37afa-195">Çözüm dosyası</span><span class="sxs-lookup"><span data-stu-id="37afa-195">Solution file</span></span>                                | `sln`         |               |
| <span data-ttu-id="37afa-196">Razor sayfası</span><span class="sxs-lookup"><span data-stu-id="37afa-196">Razor page</span></span>                                   | `page`        |               |
| <span data-ttu-id="37afa-197">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="37afa-197">MVC ViewImports</span></span>                              | `viewimports` |               |
| <span data-ttu-id="37afa-198">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="37afa-198">MVC ViewStart</span></span>                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="37afa-199">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="37afa-199">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="37afa-200">Komutu, şablonları, varsayılan listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="37afa-200">The command contains a default list of templates.</span></span> <span data-ttu-id="37afa-201">Kullanım `dotnet new -all` kullanılabilir şablonların listesini alamadı.</span><span class="sxs-lookup"><span data-stu-id="37afa-201">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="37afa-202">.NET Core SDK'sı ile önceden yüklenmiş olarak gelen şablonları aşağıdaki tabloda gösterilmektedir 1.x.</span><span class="sxs-lookup"><span data-stu-id="37afa-202">The following table shows the templates that come pre-installed with the .NET Core SDK 1.x.</span></span> <span data-ttu-id="37afa-203">Şablonunuz için varsayılan dili köşeli ayraçlar içinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="37afa-203">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="37afa-204">Şablon açıklaması</span><span class="sxs-lookup"><span data-stu-id="37afa-204">Template description</span></span>  | <span data-ttu-id="37afa-205">Şablon adı</span><span class="sxs-lookup"><span data-stu-id="37afa-205">Template name</span></span> | <span data-ttu-id="37afa-206">Diller</span><span class="sxs-lookup"><span data-stu-id="37afa-206">Languages</span></span> |
|----------------------|---------------|-----------|
| <span data-ttu-id="37afa-207">Konsol uygulaması</span><span class="sxs-lookup"><span data-stu-id="37afa-207">Console application</span></span>  | `console`     | <span data-ttu-id="37afa-208">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="37afa-208">[C#], F#</span></span>  |
| <span data-ttu-id="37afa-209">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="37afa-209">Class library</span></span>        | `classlib`    | <span data-ttu-id="37afa-210">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="37afa-210">[C#], F#</span></span>  |
| <span data-ttu-id="37afa-211">Birim testi projesi</span><span class="sxs-lookup"><span data-stu-id="37afa-211">Unit test project</span></span>    | `mstest`      | <span data-ttu-id="37afa-212">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="37afa-212">[C#], F#</span></span>  |
| <span data-ttu-id="37afa-213">xUnit test projesi</span><span class="sxs-lookup"><span data-stu-id="37afa-213">xUnit test project</span></span>   | `xunit`       | <span data-ttu-id="37afa-214">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="37afa-214">[C#], F#</span></span>  |
| <span data-ttu-id="37afa-215">ASP.NET Core boş</span><span class="sxs-lookup"><span data-stu-id="37afa-215">ASP.NET Core empty</span></span>   | `web`         | <span data-ttu-id="37afa-216">[C#]</span><span class="sxs-lookup"><span data-stu-id="37afa-216">[C#]</span></span>      |
| <span data-ttu-id="37afa-217">ASP.NET Core Web uygulaması</span><span class="sxs-lookup"><span data-stu-id="37afa-217">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="37afa-218">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="37afa-218">[C#], F#</span></span>  |
| <span data-ttu-id="37afa-219">ASP.NET Core Web API'si</span><span class="sxs-lookup"><span data-stu-id="37afa-219">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="37afa-220">[C#]</span><span class="sxs-lookup"><span data-stu-id="37afa-220">[C#]</span></span>      |
| <span data-ttu-id="37afa-221">NuGet yapılandırma</span><span class="sxs-lookup"><span data-stu-id="37afa-221">NuGet config</span></span>         | `nugetconfig` |           |
| <span data-ttu-id="37afa-222">Web yapılandırması</span><span class="sxs-lookup"><span data-stu-id="37afa-222">Web config</span></span>           | `webconfig`   |           |
| <span data-ttu-id="37afa-223">Çözüm dosyası</span><span class="sxs-lookup"><span data-stu-id="37afa-223">Solution file</span></span>        | `sln`         |           |

---

## <a name="options"></a><span data-ttu-id="37afa-224">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="37afa-224">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="37afa-225">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="37afa-225">.NET Core 2.1</span></span>](#tab/netcore21)

`--force`

<span data-ttu-id="37afa-226">Mevcut dosyaları değiştirmek olsa bile oluşturulması gereken içeriği zorlar.</span><span class="sxs-lookup"><span data-stu-id="37afa-226">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="37afa-227">Bir proje çıkış dizinine içerdiğinde, bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="37afa-227">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="37afa-228">Komut için Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="37afa-228">Prints out help for the command.</span></span> <span data-ttu-id="37afa-229">İçin çağrılabilir `dotnet new` kendisini komutu veya herhangi bir şablon gibi `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="37afa-229">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="37afa-230">Bir kaynak veya şablon paketinden yükler `PATH` veya `NUGET_ID` sağlanan.</span><span class="sxs-lookup"><span data-stu-id="37afa-230">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="37afa-231">Bir şablon Paketi yayım öncesi bir sürümü yüklemek istediğiniz sürümü biçiminde belirtmek gerekirse `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="37afa-231">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="37afa-232">Varsayılan olarak, `dotnet new` geçirir \* sürümünü temsil eden en son kararlı Paket sürümü.</span><span class="sxs-lookup"><span data-stu-id="37afa-232">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="37afa-233">Bir örneğe bakın [örnekler](#examples) bölümü.</span><span class="sxs-lookup"><span data-stu-id="37afa-233">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="37afa-234">Özel şablonlar oluşturma hakkında daha fazla bilgi için bkz. [yeni dotnet için özel şablonları](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="37afa-234">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="37afa-235">Belirtilen ad içeren şablonlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="37afa-235">Lists templates containing the specified name.</span></span> <span data-ttu-id="37afa-236">İçin çağırdıysanız `dotnet new` komut, belirtilen dizinde kullanılabilir olası şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="37afa-236">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="37afa-237">Örnek dizin zaten bir proje içeriyorsa, tüm proje şablonları listesinde değil.</span><span class="sxs-lookup"><span data-stu-id="37afa-237">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="37afa-238">Oluşturmak için şablon dili.</span><span class="sxs-lookup"><span data-stu-id="37afa-238">The language of the template to create.</span></span> <span data-ttu-id="37afa-239">Dil kabul şablon tarafından farklılık gösterir (varsayılan ayarlarında bkz [bağımsız değişkenleri](#arguments) bölümü).</span><span class="sxs-lookup"><span data-stu-id="37afa-239">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="37afa-240">Bazı şablonlar için geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="37afa-240">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="37afa-241">Bazı Kabukları yorumlama `#` olarak bir özel karakter.</span><span class="sxs-lookup"><span data-stu-id="37afa-241">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="37afa-242">Bu gibi durumlarda, dil parametre değeri, aşağıdaki gibi alın gerek `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="37afa-242">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="37afa-243">Oluşturulan çıktı adı.</span><span class="sxs-lookup"><span data-stu-id="37afa-243">The name for the created output.</span></span> <span data-ttu-id="37afa-244">Hiçbir ad belirtilmediği takdirde, geçerli dizin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="37afa-244">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="37afa-245">Yükleme sırasında kullanılacak bir NuGet kaynağı belirtir.</span><span class="sxs-lookup"><span data-stu-id="37afa-245">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="37afa-246">Oluşturulan çıktı yerleştirileceği konumu.</span><span class="sxs-lookup"><span data-stu-id="37afa-246">Location to place the generated output.</span></span> <span data-ttu-id="37afa-247">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="37afa-247">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="37afa-248">Şablonları kullanılabilir türlerine göre filtreler.</span><span class="sxs-lookup"><span data-stu-id="37afa-248">Filters templates based on available types.</span></span> <span data-ttu-id="37afa-249">Önceden tanımlanmış değerler şunlardır: "proje", "Item" veya "diğer".</span><span class="sxs-lookup"><span data-stu-id="37afa-249">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="37afa-250">Bir kaynak veya şablon paketini kaldırır `PATH` veya `NUGET_ID` sağlanan.</span><span class="sxs-lookup"><span data-stu-id="37afa-250">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="37afa-251">Bir şablon kullanarak kaldırmak için bir `PATH`, yol tam olarak nitelemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="37afa-251">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="37afa-252">Örneğin, *C:/Users/\<kullanıcı > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* çalışır, ancak *./GarciaSoftware.ConsoleTemplate.CSharp* içeren gelen Klasör erişemez.</span><span class="sxs-lookup"><span data-stu-id="37afa-252">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="37afa-253">Ayrıca, şablonu yoldaki son Sonlandırıcı directory eğik çizgi içermez.</span><span class="sxs-lookup"><span data-stu-id="37afa-253">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="37afa-254">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="37afa-254">.NET Core 2.0</span></span>](#tab/netcore20)

`--force`

<span data-ttu-id="37afa-255">Mevcut dosyaları değiştirmek olsa bile oluşturulması gereken içeriği zorlar.</span><span class="sxs-lookup"><span data-stu-id="37afa-255">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="37afa-256">Bir proje çıkış dizinine içerdiğinde, bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="37afa-256">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="37afa-257">Komut için Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="37afa-257">Prints out help for the command.</span></span> <span data-ttu-id="37afa-258">İçin çağrılabilir `dotnet new` kendisini komutu veya herhangi bir şablon gibi `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="37afa-258">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="37afa-259">Bir kaynak veya şablon paketinden yükler `PATH` veya `NUGET_ID` sağlanan.</span><span class="sxs-lookup"><span data-stu-id="37afa-259">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="37afa-260">Bir şablon Paketi yayım öncesi bir sürümü yüklemek istediğiniz sürümü biçiminde belirtmek gerekirse `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="37afa-260">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="37afa-261">Varsayılan olarak, `dotnet new` geçirir \* sürümünü temsil eden en son kararlı Paket sürümü.</span><span class="sxs-lookup"><span data-stu-id="37afa-261">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="37afa-262">Bir örneğe bakın [örnekler](#examples) bölümü.</span><span class="sxs-lookup"><span data-stu-id="37afa-262">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="37afa-263">Özel şablonlar oluşturma hakkında daha fazla bilgi için bkz. [yeni dotnet için özel şablonları](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="37afa-263">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="37afa-264">Belirtilen ad içeren şablonlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="37afa-264">Lists templates containing the specified name.</span></span> <span data-ttu-id="37afa-265">İçin çağırdıysanız `dotnet new` komut, belirtilen dizinde kullanılabilir olası şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="37afa-265">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="37afa-266">Örnek dizin zaten bir proje içeriyorsa, tüm proje şablonları listesinde değil.</span><span class="sxs-lookup"><span data-stu-id="37afa-266">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="37afa-267">Oluşturmak için şablon dili.</span><span class="sxs-lookup"><span data-stu-id="37afa-267">The language of the template to create.</span></span> <span data-ttu-id="37afa-268">Dil kabul şablon tarafından farklılık gösterir (varsayılan ayarlarında bkz [bağımsız değişkenleri](#arguments) bölümü).</span><span class="sxs-lookup"><span data-stu-id="37afa-268">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="37afa-269">Bazı şablonlar için geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="37afa-269">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="37afa-270">Bazı Kabukları yorumlama `#` olarak bir özel karakter.</span><span class="sxs-lookup"><span data-stu-id="37afa-270">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="37afa-271">Bu gibi durumlarda, dil parametre değeri, aşağıdaki gibi alın gerek `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="37afa-271">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="37afa-272">Oluşturulan çıktı adı.</span><span class="sxs-lookup"><span data-stu-id="37afa-272">The name for the created output.</span></span> <span data-ttu-id="37afa-273">Hiçbir ad belirtilmediği takdirde, geçerli dizin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="37afa-273">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="37afa-274">Oluşturulan çıktı yerleştirileceği konumu.</span><span class="sxs-lookup"><span data-stu-id="37afa-274">Location to place the generated output.</span></span> <span data-ttu-id="37afa-275">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="37afa-275">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="37afa-276">Şablonları kullanılabilir türlerine göre filtreler.</span><span class="sxs-lookup"><span data-stu-id="37afa-276">Filters templates based on available types.</span></span> <span data-ttu-id="37afa-277">Önceden tanımlanmış değerler şunlardır: "proje", "Item" veya "diğer".</span><span class="sxs-lookup"><span data-stu-id="37afa-277">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="37afa-278">Bir kaynak veya şablon paketini kaldırır `PATH` veya `NUGET_ID` sağlanan.</span><span class="sxs-lookup"><span data-stu-id="37afa-278">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="37afa-279">Bir kaynağı kullanan bir şablonu kaldırmak için `PATH`, yol tam olarak nitelemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="37afa-279">To uninstall a template using a source `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="37afa-280">Örneğin, *C:/Users/\<kullanıcı > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* çalışır, ancak *./GarciaSoftware.ConsoleTemplate.CSharp* içeren gelen Klasör erişemez.</span><span class="sxs-lookup"><span data-stu-id="37afa-280">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span> <span data-ttu-id="37afa-281">Ayrıca, şablonu yoldaki son Sonlandırıcı directory eğik çizgi içermez.</span><span class="sxs-lookup"><span data-stu-id="37afa-281">Additionally, do not include a final terminating directory slash on your template path.</span></span>
> 
> <span data-ttu-id="37afa-282">Belirlemek erişemiyorsanız `PATH` veya `NUGET_ID` çalıştıran, bir şablonu kaldırmak için gerekli bağımsız değişken `dotnet new --uninstall` bağımsız değişken yüklü tüm şablonları ve bunları kaldırmak için gerekli bağımsız değişken listesi olmayan.</span><span class="sxs-lookup"><span data-stu-id="37afa-282">If you are unable to determine the `PATH` or `NUGET_ID` argument needed to uninstall a template, running `dotnet new --uninstall` without an argument will list all installed templates and the argument required to uninstall them.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="37afa-283">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="37afa-283">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="37afa-284">Belirli türde bir proje için tüm şablonları'nı bağlamında çalıştırılırken gösterir `dotnet new` tek başına komutu.</span><span class="sxs-lookup"><span data-stu-id="37afa-284">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="37afa-285">Belirli bir şablon bağlamında gibi çalıştırırken `dotnet new web -all`, `-all` zorla oluşturma bayrak olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="37afa-285">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="37afa-286">Bir proje çıkış dizinine içerdiğinde, bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="37afa-286">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="37afa-287">Komut için Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="37afa-287">Prints out help for the command.</span></span> <span data-ttu-id="37afa-288">İçin çağrılabilir `dotnet new` kendisini komutu veya herhangi bir şablon gibi `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="37afa-288">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="37afa-289">Belirtilen ad içeren şablonlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="37afa-289">Lists templates containing the specified name.</span></span> <span data-ttu-id="37afa-290">İçin çağırdıysanız `dotnet new` komut, belirtilen dizinde kullanılabilir olası şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="37afa-290">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="37afa-291">Örnek dizin zaten bir proje içeriyorsa, tüm proje şablonları listesinde değil.</span><span class="sxs-lookup"><span data-stu-id="37afa-291">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="37afa-292">Oluşturmak için şablon dili.</span><span class="sxs-lookup"><span data-stu-id="37afa-292">The language of the template to create.</span></span> <span data-ttu-id="37afa-293">Dil kabul şablon tarafından farklılık gösterir (varsayılan ayarlarında bkz [bağımsız değişkenleri](#arguments) bölümü).</span><span class="sxs-lookup"><span data-stu-id="37afa-293">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="37afa-294">Bazı şablonlar için geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="37afa-294">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="37afa-295">Bazı Kabukları yorumlama `#` olarak bir özel karakter.</span><span class="sxs-lookup"><span data-stu-id="37afa-295">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="37afa-296">Bu gibi durumlarda, dil parametre değeri, aşağıdaki gibi alın gerek `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="37afa-296">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="37afa-297">Oluşturulan çıktı adı.</span><span class="sxs-lookup"><span data-stu-id="37afa-297">The name for the created output.</span></span> <span data-ttu-id="37afa-298">Hiçbir ad belirtilmediği takdirde, geçerli dizin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="37afa-298">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="37afa-299">Oluşturulan çıktı yerleştirileceği konumu.</span><span class="sxs-lookup"><span data-stu-id="37afa-299">Location to place the generated output.</span></span> <span data-ttu-id="37afa-300">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="37afa-300">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="37afa-301">Şablon seçenekleri</span><span class="sxs-lookup"><span data-stu-id="37afa-301">Template options</span></span>

<span data-ttu-id="37afa-302">Her proje şablonu, ek seçenekler kullanılabilir olabilir.</span><span class="sxs-lookup"><span data-stu-id="37afa-302">Each project template may have additional options available.</span></span> <span data-ttu-id="37afa-303">Çekirdek şablonları aşağıdaki ek seçeneklere sahip olursunuz:</span><span class="sxs-lookup"><span data-stu-id="37afa-303">The core templates have the following additional options:</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="37afa-304">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="37afa-304">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="37afa-305">**konsolunda, angular, react, açarken kilitlenmesi, razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="37afa-305">**console, angular, react, reactredux, razorclasslib**</span></span>

  <span data-ttu-id="37afa-306">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="37afa-306">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="37afa-307">**classlib**</span><span class="sxs-lookup"><span data-stu-id="37afa-307">**classlib**</span></span>

<span data-ttu-id="37afa-308">`-f|--framework <FRAMEWORK>` -Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="37afa-308">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="37afa-309">Değerler: `netcoreapp2.0` bir .NET Core sınıf kitaplığı oluşturmak için veya `netstandard2.0` .NET standart sınıf kitaplığı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="37afa-309">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="37afa-310">Varsayılan değer `netstandard2.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="37afa-310">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="37afa-311">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="37afa-311">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="37afa-312">**MSTest, xunit**</span><span class="sxs-lookup"><span data-stu-id="37afa-312">**mstest, xunit**</span></span>

<span data-ttu-id="37afa-313">`-p|--enable-pack` -Etkinleştirir kullanarak projeyi için paketleme [dotnet paketi](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="37afa-313">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="37afa-314">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="37afa-314">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="37afa-315">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="37afa-315">**globaljson**</span></span>

<span data-ttu-id="37afa-316">`--sdk-version <VERSION_NUMBER>` -Kullanmak için .NET Core SDK'sı sürümünü belirtir *global.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="37afa-316">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="37afa-317">**Web**</span><span class="sxs-lookup"><span data-stu-id="37afa-317">**web**</span></span>

<span data-ttu-id="37afa-318">`--exclude-launch-settings` -Hariç *launchSettings.json* oluşturulan şablonundan.</span><span class="sxs-lookup"><span data-stu-id="37afa-318">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="37afa-319">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="37afa-319">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="37afa-320">`--no-https` -Proje HTTPS'yi gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="37afa-320">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="37afa-321">Bu seçenek yalnızca geçerlidir `IndividualAuth` veya `OrganizationalAuth` kullanılmayan.</span><span class="sxs-lookup"><span data-stu-id="37afa-321">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="37afa-322">**webapı**</span><span class="sxs-lookup"><span data-stu-id="37afa-322">**webapi**</span></span>

<span data-ttu-id="37afa-323">`-au|--auth <AUTHENTICATION_TYPE>` -Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="37afa-323">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="37afa-324">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="37afa-324">The possible values are:</span></span>

- <span data-ttu-id="37afa-325">`None` -Kimlik doğrulama yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="37afa-325">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="37afa-326">`IndividualB2C` -Azure AD B2C ile kimlik doğrulaması tek tek.</span><span class="sxs-lookup"><span data-stu-id="37afa-326">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="37afa-327">`SingleOrg` -Kuruluş kimlik doğrulaması için tek bir kiracı.</span><span class="sxs-lookup"><span data-stu-id="37afa-327">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="37afa-328">`Windows` -Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="37afa-328">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="37afa-329">`--aad-b2c-instance <INSTANCE>` -Bağlanmak için Azure Active Directory B2C örnek.</span><span class="sxs-lookup"><span data-stu-id="37afa-329">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="37afa-330">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="37afa-330">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="37afa-331">Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="37afa-331">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="37afa-332">`-ssp|--susi-policy-id <ID>` -Bu proje için oturum açma ve kaydolma ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="37afa-332">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="37afa-333">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="37afa-333">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="37afa-334">`--aad-instance <INSTANCE>` -Bağlanmak için Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="37afa-334">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="37afa-335">İle kullanma `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="37afa-335">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="37afa-336">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="37afa-336">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="37afa-337">`--client-id <ID>` -Bu proje için istemci kimliği.</span><span class="sxs-lookup"><span data-stu-id="37afa-337">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="37afa-338">İle kullanma `IndividualB2C` veya `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="37afa-338">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="37afa-339">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="37afa-339">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="37afa-340">`--domain <DOMAIN>` -Dizin kiracısı için etki alanı.</span><span class="sxs-lookup"><span data-stu-id="37afa-340">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="37afa-341">İle kullanma `SingleOrg` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="37afa-341">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="37afa-342">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="37afa-342">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="37afa-343">`--tenant-id <ID>` -Tenantıd bağlanmak için kimliği dizini.</span><span class="sxs-lookup"><span data-stu-id="37afa-343">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="37afa-344">İle kullanma `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="37afa-344">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="37afa-345">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="37afa-345">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="37afa-346">`-r|--org-read-access` -Bu uygulamanın dizine okuma erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="37afa-346">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="37afa-347">Yalnızca uygulandığı `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="37afa-347">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="37afa-348">`--exclude-launch-settings` -Hariç *launchSettings.json* oluşturulan şablonundan.</span><span class="sxs-lookup"><span data-stu-id="37afa-348">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="37afa-349">`-uld|--use-local-db` -LocalDB yerine SQLite kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="37afa-349">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="37afa-350">Yalnızca uygulandığı `Individual` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="37afa-350">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="37afa-351">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="37afa-351">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="37afa-352">`--no-https` -Proje HTTPS'yi gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="37afa-352">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="37afa-353">`app.UseHsts` ve `app.UseHttpsRedirection` için eklenmez `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="37afa-353">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="37afa-354">Bu seçenek yalnızca geçerlidir `Individual`, `IndividualB2C`, `SingleOrg`, veya `MultiOrg` kullanılmayan.</span><span class="sxs-lookup"><span data-stu-id="37afa-354">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="37afa-355">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="37afa-355">**mvc, razor**</span></span>

<span data-ttu-id="37afa-356">`-au|--auth <AUTHENTICATION_TYPE>` -Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="37afa-356">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="37afa-357">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="37afa-357">The possible values are:</span></span>

- <span data-ttu-id="37afa-358">`None` -Kimlik doğrulama yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="37afa-358">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="37afa-359">`Individual` -Tek tek kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="37afa-359">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="37afa-360">`IndividualB2C` -Azure AD B2C ile kimlik doğrulaması tek tek.</span><span class="sxs-lookup"><span data-stu-id="37afa-360">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="37afa-361">`SingleOrg` -Kuruluş kimlik doğrulaması için tek bir kiracı.</span><span class="sxs-lookup"><span data-stu-id="37afa-361">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="37afa-362">`MultiOrg` -Birden fazla Kiracı için Kurumsal kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="37afa-362">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="37afa-363">`Windows` -Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="37afa-363">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="37afa-364">`--aad-b2c-instance <INSTANCE>` -Bağlanmak için Azure Active Directory B2C örnek.</span><span class="sxs-lookup"><span data-stu-id="37afa-364">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="37afa-365">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="37afa-365">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="37afa-366">Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="37afa-366">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="37afa-367">`-ssp|--susi-policy-id <ID>` -Bu proje için oturum açma ve kaydolma ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="37afa-367">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="37afa-368">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="37afa-368">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="37afa-369">`-rp|--reset-password-policy-id <ID>` -Bu proje için reset parola ilkesi kimliği.</span><span class="sxs-lookup"><span data-stu-id="37afa-369">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="37afa-370">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="37afa-370">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="37afa-371">`-ep|--edit-profile-policy-id <ID>` -Bu proje için düzenleme profili ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="37afa-371">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="37afa-372">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="37afa-372">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="37afa-373">`--aad-instance <INSTANCE>` -Bağlanmak için Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="37afa-373">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="37afa-374">İle kullanma `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="37afa-374">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="37afa-375">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="37afa-375">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="37afa-376">`--client-id <ID>` -Bu proje için istemci kimliği.</span><span class="sxs-lookup"><span data-stu-id="37afa-376">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="37afa-377">İle kullanma `IndividualB2C`, `SingleOrg`, veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="37afa-377">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="37afa-378">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="37afa-378">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="37afa-379">`--domain <DOMAIN>` -Dizin kiracısı için etki alanı.</span><span class="sxs-lookup"><span data-stu-id="37afa-379">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="37afa-380">İle kullanma `SingleOrg` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="37afa-380">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="37afa-381">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="37afa-381">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="37afa-382">`--tenant-id <ID>` -Tenantıd bağlanmak için kimliği dizini.</span><span class="sxs-lookup"><span data-stu-id="37afa-382">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="37afa-383">İle kullanma `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="37afa-383">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="37afa-384">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="37afa-384">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="37afa-385">`--callback-path <PATH>` -Yeniden yönlendirme URI'si uygulamanın taban yolu içindeki istek yolu.</span><span class="sxs-lookup"><span data-stu-id="37afa-385">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="37afa-386">İle kullanma `SingleOrg` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="37afa-386">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="37afa-387">Varsayılan değer `/signin-oidc` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="37afa-387">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="37afa-388">`-r|--org-read-access` -Bu uygulamanın dizine okuma erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="37afa-388">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="37afa-389">Yalnızca uygulandığı `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="37afa-389">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="37afa-390">`--exclude-launch-settings` -Hariç *launchSettings.json* oluşturulan şablonundan.</span><span class="sxs-lookup"><span data-stu-id="37afa-390">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="37afa-391">`--use-browserlink` -BrowserLink projede içerir.</span><span class="sxs-lookup"><span data-stu-id="37afa-391">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="37afa-392">`-uld|--use-local-db` -LocalDB yerine SQLite kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="37afa-392">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="37afa-393">Yalnızca uygulandığı `Individual` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="37afa-393">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="37afa-394">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="37afa-394">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="37afa-395">`--no-https` -Proje HTTPS'yi gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="37afa-395">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="37afa-396">`app.UseHsts` ve `app.UseHttpsRedirection` için eklenmez `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="37afa-396">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="37afa-397">Bu seçenek yalnızca geçerlidir `Individual`, `IndividualB2C`, `SingleOrg`, veya `MultiOrg` kullanılmayan.</span><span class="sxs-lookup"><span data-stu-id="37afa-397">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="37afa-398">**Sayfa**</span><span class="sxs-lookup"><span data-stu-id="37afa-398">**page**</span></span>

<span data-ttu-id="37afa-399">`-na|--namespace <NAMESPACE_NAME>`-Namespace üretilen kod için.</span><span class="sxs-lookup"><span data-stu-id="37afa-399">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="37afa-400">Varsayılan değer `MyApp.Namespace` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="37afa-400">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="37afa-401">`-np|--no-pagemodel` -Bir PageModel olmadan sayfası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="37afa-401">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="37afa-402">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="37afa-402">**viewimports**</span></span>

<span data-ttu-id="37afa-403">`-na|--namespace <NAMESPACE_NAME>`-Namespace üretilen kod için.</span><span class="sxs-lookup"><span data-stu-id="37afa-403">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="37afa-404">Varsayılan değer `MyApp.Namespace` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="37afa-404">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="37afa-405">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="37afa-405">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="37afa-406">**konsolunda, angular, react, açarken kilitlenmesi**</span><span class="sxs-lookup"><span data-stu-id="37afa-406">**console, angular, react, reactredux**</span></span>

  <span data-ttu-id="37afa-407">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="37afa-407">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="37afa-408">**classlib**</span><span class="sxs-lookup"><span data-stu-id="37afa-408">**classlib**</span></span>

<span data-ttu-id="37afa-409">`-f|--framework <FRAMEWORK>` -Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="37afa-409">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="37afa-410">Değerler: `netcoreapp2.0` bir .NET Core sınıf kitaplığı oluşturmak için veya `netstandard2.0` .NET standart sınıf kitaplığı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="37afa-410">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="37afa-411">Varsayılan değer `netstandard2.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="37afa-411">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="37afa-412">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="37afa-412">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="37afa-413">**MSTest, xunit**</span><span class="sxs-lookup"><span data-stu-id="37afa-413">**mstest, xunit**</span></span>

<span data-ttu-id="37afa-414">`-p|--enable-pack` -Etkinleştirir kullanarak projeyi için paketleme [dotnet paketi](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="37afa-414">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="37afa-415">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="37afa-415">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="37afa-416">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="37afa-416">**globaljson**</span></span>

<span data-ttu-id="37afa-417">`--sdk-version <VERSION_NUMBER>` -Kullanmak için .NET Core SDK'sı sürümünü belirtir *global.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="37afa-417">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="37afa-418">**Web**</span><span class="sxs-lookup"><span data-stu-id="37afa-418">**web**</span></span>

<span data-ttu-id="37afa-419">`--use-launch-settings` -İçeren *launchSettings.json* oluşturulan şablon çıktı.</span><span class="sxs-lookup"><span data-stu-id="37afa-419">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="37afa-420">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="37afa-420">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="37afa-421">**webapı**</span><span class="sxs-lookup"><span data-stu-id="37afa-421">**webapi**</span></span>

<span data-ttu-id="37afa-422">`-au|--auth <AUTHENTICATION_TYPE>` -Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="37afa-422">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="37afa-423">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="37afa-423">The possible values are:</span></span>

- <span data-ttu-id="37afa-424">`None` -Kimlik doğrulama yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="37afa-424">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="37afa-425">`IndividualB2C` -Azure AD B2C ile kimlik doğrulaması tek tek.</span><span class="sxs-lookup"><span data-stu-id="37afa-425">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="37afa-426">`SingleOrg` -Kuruluş kimlik doğrulaması için tek bir kiracı.</span><span class="sxs-lookup"><span data-stu-id="37afa-426">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="37afa-427">`Windows` -Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="37afa-427">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="37afa-428">`--aad-b2c-instance <INSTANCE>` -Bağlanmak için Azure Active Directory B2C örnek.</span><span class="sxs-lookup"><span data-stu-id="37afa-428">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="37afa-429">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="37afa-429">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="37afa-430">Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="37afa-430">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="37afa-431">`-ssp|--susi-policy-id <ID>` -Bu proje için oturum açma ve kaydolma ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="37afa-431">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="37afa-432">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="37afa-432">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="37afa-433">`--aad-instance <INSTANCE>` -Bağlanmak için Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="37afa-433">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="37afa-434">İle kullanma `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="37afa-434">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="37afa-435">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="37afa-435">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="37afa-436">`--client-id <ID>` -Bu proje için istemci kimliği.</span><span class="sxs-lookup"><span data-stu-id="37afa-436">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="37afa-437">İle kullanma `IndividualB2C` veya `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="37afa-437">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="37afa-438">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="37afa-438">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="37afa-439">`--domain <DOMAIN>` -Dizin kiracısı için etki alanı.</span><span class="sxs-lookup"><span data-stu-id="37afa-439">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="37afa-440">İle kullanma `SingleOrg` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="37afa-440">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="37afa-441">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="37afa-441">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="37afa-442">`--tenant-id <ID>` -Tenantıd bağlanmak için kimliği dizini.</span><span class="sxs-lookup"><span data-stu-id="37afa-442">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="37afa-443">İle kullanma `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="37afa-443">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="37afa-444">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="37afa-444">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="37afa-445">`-r|--org-read-access` -Bu uygulamanın dizine okuma erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="37afa-445">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="37afa-446">Yalnızca uygulandığı `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="37afa-446">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="37afa-447">`--use-launch-settings` -İçeren *launchSettings.json* oluşturulan şablon çıktı.</span><span class="sxs-lookup"><span data-stu-id="37afa-447">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="37afa-448">`-uld|--use-local-db` -LocalDB yerine SQLite kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="37afa-448">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="37afa-449">Yalnızca uygulandığı `Individual` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="37afa-449">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="37afa-450">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="37afa-450">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="37afa-451">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="37afa-451">**mvc, razor**</span></span>

<span data-ttu-id="37afa-452">`-au|--auth <AUTHENTICATION_TYPE>` -Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="37afa-452">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="37afa-453">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="37afa-453">The possible values are:</span></span>

- <span data-ttu-id="37afa-454">`None` -Kimlik doğrulama yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="37afa-454">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="37afa-455">`Individual` -Tek tek kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="37afa-455">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="37afa-456">`IndividualB2C` -Azure AD B2C ile kimlik doğrulaması tek tek.</span><span class="sxs-lookup"><span data-stu-id="37afa-456">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="37afa-457">`SingleOrg` -Kuruluş kimlik doğrulaması için tek bir kiracı.</span><span class="sxs-lookup"><span data-stu-id="37afa-457">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="37afa-458">`MultiOrg` -Birden fazla Kiracı için Kurumsal kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="37afa-458">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="37afa-459">`Windows` -Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="37afa-459">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="37afa-460">`--aad-b2c-instance <INSTANCE>` -Bağlanmak için Azure Active Directory B2C örnek.</span><span class="sxs-lookup"><span data-stu-id="37afa-460">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="37afa-461">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="37afa-461">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="37afa-462">Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="37afa-462">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="37afa-463">`-ssp|--susi-policy-id <ID>` -Bu proje için oturum açma ve kaydolma ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="37afa-463">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="37afa-464">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="37afa-464">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="37afa-465">`-rp|--reset-password-policy-id <ID>` -Bu proje için reset parola ilkesi kimliği.</span><span class="sxs-lookup"><span data-stu-id="37afa-465">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="37afa-466">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="37afa-466">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="37afa-467">`-ep|--edit-profile-policy-id <ID>` -Bu proje için düzenleme profili ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="37afa-467">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="37afa-468">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="37afa-468">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="37afa-469">`--aad-instance <INSTANCE>` -Bağlanmak için Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="37afa-469">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="37afa-470">İle kullanma `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="37afa-470">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="37afa-471">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="37afa-471">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="37afa-472">`--client-id <ID>` -Bu proje için istemci kimliği.</span><span class="sxs-lookup"><span data-stu-id="37afa-472">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="37afa-473">İle kullanma `IndividualB2C`, `SingleOrg`, veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="37afa-473">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="37afa-474">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="37afa-474">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="37afa-475">`--domain <DOMAIN>` -Dizin kiracısı için etki alanı.</span><span class="sxs-lookup"><span data-stu-id="37afa-475">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="37afa-476">İle kullanma `SingleOrg` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="37afa-476">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="37afa-477">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="37afa-477">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="37afa-478">`--tenant-id <ID>` -Tenantıd bağlanmak için kimliği dizini.</span><span class="sxs-lookup"><span data-stu-id="37afa-478">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="37afa-479">İle kullanma `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="37afa-479">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="37afa-480">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="37afa-480">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="37afa-481">`--callback-path <PATH>` -Yeniden yönlendirme URI'si uygulamanın taban yolu içindeki istek yolu.</span><span class="sxs-lookup"><span data-stu-id="37afa-481">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="37afa-482">İle kullanma `SingleOrg` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="37afa-482">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="37afa-483">Varsayılan değer `/signin-oidc` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="37afa-483">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="37afa-484">`-r|--org-read-access` -Bu uygulamanın dizine okuma erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="37afa-484">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="37afa-485">Yalnızca uygulandığı `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="37afa-485">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="37afa-486">`--use-launch-settings` -İçeren *launchSettings.json* oluşturulan şablon çıktı.</span><span class="sxs-lookup"><span data-stu-id="37afa-486">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="37afa-487">`--use-browserlink` -BrowserLink projede içerir.</span><span class="sxs-lookup"><span data-stu-id="37afa-487">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="37afa-488">`-uld|--use-local-db` -LocalDB yerine SQLite kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="37afa-488">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="37afa-489">Yalnızca uygulandığı `Individual` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="37afa-489">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="37afa-490">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="37afa-490">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="37afa-491">**Sayfa**</span><span class="sxs-lookup"><span data-stu-id="37afa-491">**page**</span></span>

<span data-ttu-id="37afa-492">`-na|--namespace <NAMESPACE_NAME>`-Namespace üretilen kod için.</span><span class="sxs-lookup"><span data-stu-id="37afa-492">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="37afa-493">Varsayılan değer `MyApp.Namespace` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="37afa-493">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="37afa-494">`-np|--no-pagemodel` -Bir PageModel olmadan sayfası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="37afa-494">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="37afa-495">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="37afa-495">**viewimports**</span></span>

<span data-ttu-id="37afa-496">`-na|--namespace <NAMESPACE_NAME>`-Namespace üretilen kod için.</span><span class="sxs-lookup"><span data-stu-id="37afa-496">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="37afa-497">Varsayılan değer `MyApp.Namespace` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="37afa-497">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="37afa-498">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="37afa-498">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="37afa-499">**Konsolu, xunit, mstest, web, webapı**</span><span class="sxs-lookup"><span data-stu-id="37afa-499">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="37afa-500">`-f|--framework` -Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="37afa-500">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="37afa-501">Değerler: `netcoreapp1.0` veya `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="37afa-501">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="37afa-502">Varsayılan değer `netcoreapp1.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="37afa-502">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="37afa-503">**classlib**</span><span class="sxs-lookup"><span data-stu-id="37afa-503">**classlib**</span></span>

<span data-ttu-id="37afa-504">`-f|--framework` -Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="37afa-504">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="37afa-505">Değerler: `netcoreapp1.0`, `netcoreapp1.1`, veya `netstandard1.0` için `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="37afa-505">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="37afa-506">Varsayılan değer `netstandard1.4` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="37afa-506">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="37afa-507">**mvc**</span><span class="sxs-lookup"><span data-stu-id="37afa-507">**mvc**</span></span>

<span data-ttu-id="37afa-508">`-f|--framework` -Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="37afa-508">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="37afa-509">Değerler: `netcoreapp1.0` veya `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="37afa-509">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="37afa-510">Varsayılan değer `netcoreapp1.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="37afa-510">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="37afa-511">`-au|--auth` -Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="37afa-511">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="37afa-512">Değerler: `None` veya `Individual`.</span><span class="sxs-lookup"><span data-stu-id="37afa-512">Values: `None` or `Individual`.</span></span> <span data-ttu-id="37afa-513">Varsayılan değer `None` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="37afa-513">The default value is `None`.</span></span>

<span data-ttu-id="37afa-514">`-uld|--use-local-db` -LocalDB yerine SQLite kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="37afa-514">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="37afa-515">Değerler: `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="37afa-515">Values: `true` or `false`.</span></span> <span data-ttu-id="37afa-516">Varsayılan değer `false` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="37afa-516">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="37afa-517">Örnekler</span><span class="sxs-lookup"><span data-stu-id="37afa-517">Examples</span></span>

<span data-ttu-id="37afa-518">Oluşturma bir F# konsol uygulama projesi geçerli dizin:</span><span class="sxs-lookup"><span data-stu-id="37afa-518">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="37afa-519">Belirtilen dizin (yalnızca .NET Core SDK 2.0 veya sonraki sürümler ile kullanılabilir) bir .NET Standard sınıf kitaplığı projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="37afa-519">Create a .NET Standard class library project in the specified directory (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="37afa-520">Kimlik doğrulaması olmayan geçerli dizinde yeni bir ASP.NET Core C# MVC uygulaması projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="37afa-520">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication:</span></span>

`dotnet new mvc -au None`

<span data-ttu-id="37afa-521">Yeni bir xUnit uygulama oluşturun:</span><span class="sxs-lookup"><span data-stu-id="37afa-521">Create a new xUnit application:</span></span>

`dotnet new xunit`

<span data-ttu-id="37afa-522">MVC için tüm şablonları listeler:</span><span class="sxs-lookup"><span data-stu-id="37afa-522">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="37afa-523">ASP.NET Core (komut seçeneği kullanılabilir .NET Core SDK 1.1 ve yalnızca sonraki sürümleri için) için tek sayfalı uygulama şablonları 2.0 sürümünü yükleyin:</span><span class="sxs-lookup"><span data-stu-id="37afa-523">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

<span data-ttu-id="37afa-524">Oluşturma bir *global.json* SDK'sı sürüm 2.0.0 (yalnızca .NET Core SDK 2.0 veya sonraki sürümler ile kullanılabilir) ayarı geçerli dizin:</span><span class="sxs-lookup"><span data-stu-id="37afa-524">Create a *global.json* in the current directory setting the SDK version to 2.0.0 (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="37afa-525">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="37afa-525">See also</span></span>

- [<span data-ttu-id="37afa-526">Yeni dotnet için özel şablonlar</span><span class="sxs-lookup"><span data-stu-id="37afa-526">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="37afa-527">Dotnet new için özel şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="37afa-527">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)
- [<span data-ttu-id="37afa-528">DotNet/dotnet-şablonu-örnekleri GitHub deposu</span><span class="sxs-lookup"><span data-stu-id="37afa-528">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="37afa-529">Yeni dotnet şablonları</span><span class="sxs-lookup"><span data-stu-id="37afa-529">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
