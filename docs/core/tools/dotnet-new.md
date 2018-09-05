---
title: Yeni komut dotnet - .NET Core CLI
description: Belirtilen şablonu temel alan yeni .NET Core projeleri dotnet yeni bir komut oluşturur.
author: mairaw
ms.author: mairaw
ms.date: 07/31/2018
ms.openlocfilehash: 2c82dda2d93225edb360316637e22964135cd5e4
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43512561"
---
# <a name="dotnet-new"></a><span data-ttu-id="67d43-103">DotNet yeni</span><span class="sxs-lookup"><span data-stu-id="67d43-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="67d43-104">Ad</span><span class="sxs-lookup"><span data-stu-id="67d43-104">Name</span></span>

<span data-ttu-id="67d43-105">`dotnet new` -Yeni Proje, yapılandırma dosyası veya belirtilen şablonu temel alan bir çözüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="67d43-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="67d43-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="67d43-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="67d43-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="67d43-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output]
    [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="67d43-108">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="67d43-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="67d43-109">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="67d43-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="67d43-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="67d43-110">Description</span></span>

<span data-ttu-id="67d43-111">`dotnet new` Komutu geçerli bir .NET Core projesi başlatmak için kolay bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="67d43-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="67d43-112">Komut çağrıları [şablon altyapısı](https://github.com/dotnet/templating) yapıları belirtilen şablonu ve seçenekleri bağlı disk oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="67d43-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="67d43-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="67d43-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="67d43-114">Komut çağrıldığında örneği oluşturmak için şablon.</span><span class="sxs-lookup"><span data-stu-id="67d43-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="67d43-115">Her şablon geçirebilirsiniz belirli seçenekler olabilir.</span><span class="sxs-lookup"><span data-stu-id="67d43-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="67d43-116">Daha fazla bilgi için [şablon seçeneklerini](#template-options).</span><span class="sxs-lookup"><span data-stu-id="67d43-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="67d43-117">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="67d43-117">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="67d43-118">Komutu, şablonları, varsayılan listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="67d43-118">The command contains a default list of templates.</span></span> <span data-ttu-id="67d43-119">Kullanım `dotnet new -l` kullanılabilir şablonların listesini alamadı.</span><span class="sxs-lookup"><span data-stu-id="67d43-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="67d43-120">Aşağıdaki tablo, .NET Core SDK 2.1.300 önceden yüklenmiş olarak gelen şablonları gösterir.</span><span class="sxs-lookup"><span data-stu-id="67d43-120">The following table shows the templates that come pre-installed with the .NET Core SDK 2.1.300.</span></span> <span data-ttu-id="67d43-121">Şablonunuz için varsayılan dili köşeli ayraçlar içinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="67d43-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="67d43-122">Şablon açıklaması</span><span class="sxs-lookup"><span data-stu-id="67d43-122">Template description</span></span>                          | <span data-ttu-id="67d43-123">Şablon adı</span><span class="sxs-lookup"><span data-stu-id="67d43-123">Template name</span></span>   | <span data-ttu-id="67d43-124">Diller</span><span class="sxs-lookup"><span data-stu-id="67d43-124">Languages</span></span>     |
|----------------------------------------------|-----------------|---------------|
| <span data-ttu-id="67d43-125">Konsol uygulaması</span><span class="sxs-lookup"><span data-stu-id="67d43-125">Console application</span></span>                          | `console`       | <span data-ttu-id="67d43-126">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="67d43-126">[C#], F#, VB</span></span>  |
| <span data-ttu-id="67d43-127">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="67d43-127">Class library</span></span>                                | `classlib`      | <span data-ttu-id="67d43-128">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="67d43-128">[C#], F#, VB</span></span>  |
| <span data-ttu-id="67d43-129">Birim testi projesi</span><span class="sxs-lookup"><span data-stu-id="67d43-129">Unit test project</span></span>                            | `mstest`        | <span data-ttu-id="67d43-130">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="67d43-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="67d43-131">xUnit test projesi</span><span class="sxs-lookup"><span data-stu-id="67d43-131">xUnit test project</span></span>                           | `xunit`         | <span data-ttu-id="67d43-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="67d43-132">[C#], F#, VB</span></span>  |
| <span data-ttu-id="67d43-133">Razor sayfası</span><span class="sxs-lookup"><span data-stu-id="67d43-133">Razor page</span></span>                                   | `page`          | <span data-ttu-id="67d43-134">[C#]</span><span class="sxs-lookup"><span data-stu-id="67d43-134">[C#]</span></span>          |
| <span data-ttu-id="67d43-135">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="67d43-135">MVC ViewImports</span></span>                              | `viewimports`   | <span data-ttu-id="67d43-136">[C#]</span><span class="sxs-lookup"><span data-stu-id="67d43-136">[C#]</span></span>          |
| <span data-ttu-id="67d43-137">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="67d43-137">MVC ViewStart</span></span>                                | `viewstart`     | <span data-ttu-id="67d43-138">[C#]</span><span class="sxs-lookup"><span data-stu-id="67d43-138">[C#]</span></span>          |
| <span data-ttu-id="67d43-139">ASP.NET Core boş</span><span class="sxs-lookup"><span data-stu-id="67d43-139">ASP.NET Core empty</span></span>                           | `web`           | <span data-ttu-id="67d43-140">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="67d43-140">[C#], F#</span></span>      |
| <span data-ttu-id="67d43-141">ASP.NET Core Web uygulaması (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="67d43-141">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`           | <span data-ttu-id="67d43-142">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="67d43-142">[C#], F#</span></span>      |
| <span data-ttu-id="67d43-143">ASP.NET Core Web uygulaması</span><span class="sxs-lookup"><span data-stu-id="67d43-143">ASP.NET Core Web App</span></span>                         | `razor`         | <span data-ttu-id="67d43-144">[C#]</span><span class="sxs-lookup"><span data-stu-id="67d43-144">[C#]</span></span>          |
| <span data-ttu-id="67d43-145">Angular ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="67d43-145">ASP.NET Core with Angular</span></span>                    | `angular`       | <span data-ttu-id="67d43-146">[C#]</span><span class="sxs-lookup"><span data-stu-id="67d43-146">[C#]</span></span>          |
| <span data-ttu-id="67d43-147">React.js ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="67d43-147">ASP.NET Core with React.js</span></span>                   | `react`         | <span data-ttu-id="67d43-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="67d43-148">[C#]</span></span>          |
| <span data-ttu-id="67d43-149">ASP.NET Core React.js ve Redux</span><span class="sxs-lookup"><span data-stu-id="67d43-149">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`    | <span data-ttu-id="67d43-150">[C#]</span><span class="sxs-lookup"><span data-stu-id="67d43-150">[C#]</span></span>          |
| <span data-ttu-id="67d43-151">ASP.NET Core Web API'si</span><span class="sxs-lookup"><span data-stu-id="67d43-151">ASP.NET Core Web API</span></span>                         | `webapi`        | <span data-ttu-id="67d43-152">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="67d43-152">[C#], F#</span></span>      |
| <span data-ttu-id="67d43-153">Razor sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="67d43-153">Razor class library</span></span>                          | `razorclasslib` | <span data-ttu-id="67d43-154">[C#]</span><span class="sxs-lookup"><span data-stu-id="67d43-154">[C#]</span></span>          |
| <span data-ttu-id="67d43-155">Global.JSON dosyasını</span><span class="sxs-lookup"><span data-stu-id="67d43-155">global.json file</span></span>                             | `globaljson`    |               |
| <span data-ttu-id="67d43-156">NuGet yapılandırma</span><span class="sxs-lookup"><span data-stu-id="67d43-156">NuGet config</span></span>                                 | `nugetconfig`   |               |
| <span data-ttu-id="67d43-157">Web yapılandırması</span><span class="sxs-lookup"><span data-stu-id="67d43-157">Web config</span></span>                                   | `webconfig`     |               |
| <span data-ttu-id="67d43-158">Çözüm dosyası</span><span class="sxs-lookup"><span data-stu-id="67d43-158">Solution file</span></span>                                | `sln`           |               |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="67d43-159">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="67d43-159">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="67d43-160">Komutu, şablonları, varsayılan listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="67d43-160">The command contains a default list of templates.</span></span> <span data-ttu-id="67d43-161">Kullanım `dotnet new -l` kullanılabilir şablonların listesini alamadı.</span><span class="sxs-lookup"><span data-stu-id="67d43-161">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="67d43-162">Aşağıdaki tablo, .NET Core SDK 2.0 ile önceden yüklenmiş olarak gelen şablonları gösterir.</span><span class="sxs-lookup"><span data-stu-id="67d43-162">The following table shows the templates that come pre-installed with the .NET Core SDK 2.0.</span></span> <span data-ttu-id="67d43-163">Şablonunuz için varsayılan dili köşeli ayraçlar içinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="67d43-163">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="67d43-164">Şablon açıklaması</span><span class="sxs-lookup"><span data-stu-id="67d43-164">Template description</span></span>                          | <span data-ttu-id="67d43-165">Şablon adı</span><span class="sxs-lookup"><span data-stu-id="67d43-165">Template name</span></span> | <span data-ttu-id="67d43-166">Diller</span><span class="sxs-lookup"><span data-stu-id="67d43-166">Languages</span></span>     |
|----------------------------------------------|---------------|---------------|
| <span data-ttu-id="67d43-167">Konsol uygulaması</span><span class="sxs-lookup"><span data-stu-id="67d43-167">Console application</span></span>                          | `console`     | <span data-ttu-id="67d43-168">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="67d43-168">[C#], F#, VB</span></span>  |
| <span data-ttu-id="67d43-169">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="67d43-169">Class library</span></span>                                | `classlib`    | <span data-ttu-id="67d43-170">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="67d43-170">[C#], F#, VB</span></span>  |
| <span data-ttu-id="67d43-171">Birim testi projesi</span><span class="sxs-lookup"><span data-stu-id="67d43-171">Unit test project</span></span>                            | `mstest`      | <span data-ttu-id="67d43-172">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="67d43-172">[C#], F#, VB</span></span>  |
| <span data-ttu-id="67d43-173">xUnit test projesi</span><span class="sxs-lookup"><span data-stu-id="67d43-173">xUnit test project</span></span>                           | `xunit`       | <span data-ttu-id="67d43-174">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="67d43-174">[C#], F#, VB</span></span>  |
| <span data-ttu-id="67d43-175">ASP.NET Core boş</span><span class="sxs-lookup"><span data-stu-id="67d43-175">ASP.NET Core empty</span></span>                           | `web`         | <span data-ttu-id="67d43-176">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="67d43-176">[C#], F#</span></span>      |
| <span data-ttu-id="67d43-177">ASP.NET Core Web uygulaması (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="67d43-177">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="67d43-178">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="67d43-178">[C#], F#</span></span>      |
| <span data-ttu-id="67d43-179">ASP.NET Core Web uygulaması</span><span class="sxs-lookup"><span data-stu-id="67d43-179">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="67d43-180">[C#]</span><span class="sxs-lookup"><span data-stu-id="67d43-180">[C#]</span></span>          |
| <span data-ttu-id="67d43-181">Angular ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="67d43-181">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="67d43-182">[C#]</span><span class="sxs-lookup"><span data-stu-id="67d43-182">[C#]</span></span>          |
| <span data-ttu-id="67d43-183">React.js ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="67d43-183">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="67d43-184">[C#]</span><span class="sxs-lookup"><span data-stu-id="67d43-184">[C#]</span></span>          |
| <span data-ttu-id="67d43-185">ASP.NET Core React.js ve Redux</span><span class="sxs-lookup"><span data-stu-id="67d43-185">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="67d43-186">[C#]</span><span class="sxs-lookup"><span data-stu-id="67d43-186">[C#]</span></span>          |
| <span data-ttu-id="67d43-187">ASP.NET Core Web API'si</span><span class="sxs-lookup"><span data-stu-id="67d43-187">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="67d43-188">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="67d43-188">[C#], F#</span></span>      |
| <span data-ttu-id="67d43-189">Global.JSON dosyasını</span><span class="sxs-lookup"><span data-stu-id="67d43-189">global.json file</span></span>                             | `globaljson`  |               |
| <span data-ttu-id="67d43-190">NuGet yapılandırma</span><span class="sxs-lookup"><span data-stu-id="67d43-190">NuGet config</span></span>                                 | `nugetconfig` |               |
| <span data-ttu-id="67d43-191">Web yapılandırması</span><span class="sxs-lookup"><span data-stu-id="67d43-191">Web config</span></span>                                   | `webconfig`   |               |
| <span data-ttu-id="67d43-192">Çözüm dosyası</span><span class="sxs-lookup"><span data-stu-id="67d43-192">Solution file</span></span>                                | `sln`         |               |
| <span data-ttu-id="67d43-193">Razor sayfası</span><span class="sxs-lookup"><span data-stu-id="67d43-193">Razor page</span></span>                                   | `page`        |               |
| <span data-ttu-id="67d43-194">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="67d43-194">MVC ViewImports</span></span>                              | `viewimports` |               |
| <span data-ttu-id="67d43-195">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="67d43-195">MVC ViewStart</span></span>                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="67d43-196">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="67d43-196">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="67d43-197">Komutu, şablonları, varsayılan listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="67d43-197">The command contains a default list of templates.</span></span> <span data-ttu-id="67d43-198">Kullanım `dotnet new -all` kullanılabilir şablonların listesini alamadı.</span><span class="sxs-lookup"><span data-stu-id="67d43-198">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="67d43-199">.NET Core SDK'sı ile önceden yüklenmiş olarak gelen şablonları aşağıdaki tabloda gösterilmektedir 1.x.</span><span class="sxs-lookup"><span data-stu-id="67d43-199">The following table shows the templates that come pre-installed with the .NET Core SDK 1.x.</span></span> <span data-ttu-id="67d43-200">Şablonunuz için varsayılan dili köşeli ayraçlar içinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="67d43-200">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="67d43-201">Şablon açıklaması</span><span class="sxs-lookup"><span data-stu-id="67d43-201">Template description</span></span>  | <span data-ttu-id="67d43-202">Şablon adı</span><span class="sxs-lookup"><span data-stu-id="67d43-202">Template name</span></span> | <span data-ttu-id="67d43-203">Diller</span><span class="sxs-lookup"><span data-stu-id="67d43-203">Languages</span></span> |
|----------------------|---------------|-----------|
| <span data-ttu-id="67d43-204">Konsol uygulaması</span><span class="sxs-lookup"><span data-stu-id="67d43-204">Console application</span></span>  | `console`     | <span data-ttu-id="67d43-205">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="67d43-205">[C#], F#</span></span>  |
| <span data-ttu-id="67d43-206">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="67d43-206">Class library</span></span>        | `classlib`    | <span data-ttu-id="67d43-207">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="67d43-207">[C#], F#</span></span>  |
| <span data-ttu-id="67d43-208">Birim testi projesi</span><span class="sxs-lookup"><span data-stu-id="67d43-208">Unit test project</span></span>    | `mstest`      | <span data-ttu-id="67d43-209">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="67d43-209">[C#], F#</span></span>  |
| <span data-ttu-id="67d43-210">xUnit test projesi</span><span class="sxs-lookup"><span data-stu-id="67d43-210">xUnit test project</span></span>   | `xunit`       | <span data-ttu-id="67d43-211">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="67d43-211">[C#], F#</span></span>  |
| <span data-ttu-id="67d43-212">ASP.NET Core boş</span><span class="sxs-lookup"><span data-stu-id="67d43-212">ASP.NET Core empty</span></span>   | `web`         | <span data-ttu-id="67d43-213">[C#]</span><span class="sxs-lookup"><span data-stu-id="67d43-213">[C#]</span></span>      |
| <span data-ttu-id="67d43-214">ASP.NET Core Web uygulaması</span><span class="sxs-lookup"><span data-stu-id="67d43-214">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="67d43-215">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="67d43-215">[C#], F#</span></span>  |
| <span data-ttu-id="67d43-216">ASP.NET Core Web API'si</span><span class="sxs-lookup"><span data-stu-id="67d43-216">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="67d43-217">[C#]</span><span class="sxs-lookup"><span data-stu-id="67d43-217">[C#]</span></span>      |
| <span data-ttu-id="67d43-218">NuGet yapılandırma</span><span class="sxs-lookup"><span data-stu-id="67d43-218">NuGet config</span></span>         | `nugetconfig` |           |
| <span data-ttu-id="67d43-219">Web yapılandırması</span><span class="sxs-lookup"><span data-stu-id="67d43-219">Web config</span></span>           | `webconfig`   |           |
| <span data-ttu-id="67d43-220">Çözüm dosyası</span><span class="sxs-lookup"><span data-stu-id="67d43-220">Solution file</span></span>        | `sln`         |           |

---

## <a name="options"></a><span data-ttu-id="67d43-221">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="67d43-221">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="67d43-222">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="67d43-222">.NET Core 2.1</span></span>](#tab/netcore21)

`--force`

<span data-ttu-id="67d43-223">Mevcut dosyaları değiştirmek olsa bile oluşturulması gereken içeriği zorlar.</span><span class="sxs-lookup"><span data-stu-id="67d43-223">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="67d43-224">Bir proje çıkış dizinine içerdiğinde, bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="67d43-224">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="67d43-225">Komut için Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="67d43-225">Prints out help for the command.</span></span> <span data-ttu-id="67d43-226">İçin çağrılabilir `dotnet new` kendisini komutu veya herhangi bir şablon gibi `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="67d43-226">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="67d43-227">Bir kaynak veya şablon paketinden yükler `PATH` veya `NUGET_ID` sağlanan.</span><span class="sxs-lookup"><span data-stu-id="67d43-227">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="67d43-228">Bir şablon Paketi yayım öncesi bir sürümü yüklemek istediğiniz sürümü biçiminde belirtmek gerekirse `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="67d43-228">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="67d43-229">Varsayılan olarak, `dotnet new` geçirir \* sürümünü temsil eden en son kararlı Paket sürümü.</span><span class="sxs-lookup"><span data-stu-id="67d43-229">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="67d43-230">Bir örneğe bakın [örnekler](#examples) bölümü.</span><span class="sxs-lookup"><span data-stu-id="67d43-230">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="67d43-231">Özel şablonlar oluşturma hakkında daha fazla bilgi için bkz. [yeni dotnet için özel şablonları](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="67d43-231">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="67d43-232">Belirtilen ad içeren şablonlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="67d43-232">Lists templates containing the specified name.</span></span> <span data-ttu-id="67d43-233">İçin çağırdıysanız `dotnet new` komut, belirtilen dizinde kullanılabilir olası şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="67d43-233">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="67d43-234">Örnek dizin zaten bir proje içeriyorsa, tüm proje şablonları listesinde değil.</span><span class="sxs-lookup"><span data-stu-id="67d43-234">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="67d43-235">Oluşturmak için şablon dili.</span><span class="sxs-lookup"><span data-stu-id="67d43-235">The language of the template to create.</span></span> <span data-ttu-id="67d43-236">Dil kabul şablon tarafından farklılık gösterir (varsayılan ayarlarında bkz [bağımsız değişkenleri](#arguments) bölümü).</span><span class="sxs-lookup"><span data-stu-id="67d43-236">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="67d43-237">Bazı şablonlar için geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="67d43-237">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="67d43-238">Bazı Kabukları yorumlama `#` olarak bir özel karakter.</span><span class="sxs-lookup"><span data-stu-id="67d43-238">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="67d43-239">Bu gibi durumlarda, dil parametre değeri, aşağıdaki gibi alın gerek `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="67d43-239">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="67d43-240">Oluşturulan çıktı adı.</span><span class="sxs-lookup"><span data-stu-id="67d43-240">The name for the created output.</span></span> <span data-ttu-id="67d43-241">Hiçbir ad belirtilmediği takdirde, geçerli dizin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="67d43-241">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="67d43-242">Yükleme sırasında kullanılacak bir NuGet kaynağı belirtir.</span><span class="sxs-lookup"><span data-stu-id="67d43-242">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="67d43-243">Oluşturulan çıktı yerleştirileceği konumu.</span><span class="sxs-lookup"><span data-stu-id="67d43-243">Location to place the generated output.</span></span> <span data-ttu-id="67d43-244">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="67d43-244">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="67d43-245">Şablonları kullanılabilir türlerine göre filtreler.</span><span class="sxs-lookup"><span data-stu-id="67d43-245">Filters templates based on available types.</span></span> <span data-ttu-id="67d43-246">Önceden tanımlanmış değerler şunlardır: "proje", "Item" veya "diğer".</span><span class="sxs-lookup"><span data-stu-id="67d43-246">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="67d43-247">Bir kaynak veya şablon paketini kaldırır `PATH` veya `NUGET_ID` sağlanan.</span><span class="sxs-lookup"><span data-stu-id="67d43-247">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="67d43-248">Bir şablon kullanarak kaldırmak için bir `PATH`, yol tam olarak nitelemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="67d43-248">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="67d43-249">Örneğin, *C:/Users/\<kullanıcı > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* çalışır, ancak *./GarciaSoftware.ConsoleTemplate.CSharp* içeren gelen Klasör erişemez.</span><span class="sxs-lookup"><span data-stu-id="67d43-249">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="67d43-250">Ayrıca, şablonu yoldaki son Sonlandırıcı directory eğik çizgi içermez.</span><span class="sxs-lookup"><span data-stu-id="67d43-250">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="67d43-251">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="67d43-251">.NET Core 2.0</span></span>](#tab/netcore20)

`--force`

<span data-ttu-id="67d43-252">Mevcut dosyaları değiştirmek olsa bile oluşturulması gereken içeriği zorlar.</span><span class="sxs-lookup"><span data-stu-id="67d43-252">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="67d43-253">Bir proje çıkış dizinine içerdiğinde, bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="67d43-253">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="67d43-254">Komut için Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="67d43-254">Prints out help for the command.</span></span> <span data-ttu-id="67d43-255">İçin çağrılabilir `dotnet new` kendisini komutu veya herhangi bir şablon gibi `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="67d43-255">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="67d43-256">Bir kaynak veya şablon paketinden yükler `PATH` veya `NUGET_ID` sağlanan.</span><span class="sxs-lookup"><span data-stu-id="67d43-256">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="67d43-257">Bir şablon Paketi yayım öncesi bir sürümü yüklemek istediğiniz sürümü biçiminde belirtmek gerekirse `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="67d43-257">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="67d43-258">Varsayılan olarak, `dotnet new` geçirir \* sürümünü temsil eden en son kararlı Paket sürümü.</span><span class="sxs-lookup"><span data-stu-id="67d43-258">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="67d43-259">Bir örneğe bakın [örnekler](#examples) bölümü.</span><span class="sxs-lookup"><span data-stu-id="67d43-259">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="67d43-260">Özel şablonlar oluşturma hakkında daha fazla bilgi için bkz. [yeni dotnet için özel şablonları](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="67d43-260">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="67d43-261">Belirtilen ad içeren şablonlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="67d43-261">Lists templates containing the specified name.</span></span> <span data-ttu-id="67d43-262">İçin çağırdıysanız `dotnet new` komut, belirtilen dizinde kullanılabilir olası şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="67d43-262">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="67d43-263">Örnek dizin zaten bir proje içeriyorsa, tüm proje şablonları listesinde değil.</span><span class="sxs-lookup"><span data-stu-id="67d43-263">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="67d43-264">Oluşturmak için şablon dili.</span><span class="sxs-lookup"><span data-stu-id="67d43-264">The language of the template to create.</span></span> <span data-ttu-id="67d43-265">Dil kabul şablon tarafından farklılık gösterir (varsayılan ayarlarında bkz [bağımsız değişkenleri](#arguments) bölümü).</span><span class="sxs-lookup"><span data-stu-id="67d43-265">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="67d43-266">Bazı şablonlar için geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="67d43-266">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="67d43-267">Bazı Kabukları yorumlama `#` olarak bir özel karakter.</span><span class="sxs-lookup"><span data-stu-id="67d43-267">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="67d43-268">Bu gibi durumlarda, dil parametre değeri, aşağıdaki gibi alın gerek `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="67d43-268">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="67d43-269">Oluşturulan çıktı adı.</span><span class="sxs-lookup"><span data-stu-id="67d43-269">The name for the created output.</span></span> <span data-ttu-id="67d43-270">Hiçbir ad belirtilmediği takdirde, geçerli dizin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="67d43-270">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="67d43-271">Oluşturulan çıktı yerleştirileceği konumu.</span><span class="sxs-lookup"><span data-stu-id="67d43-271">Location to place the generated output.</span></span> <span data-ttu-id="67d43-272">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="67d43-272">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="67d43-273">Şablonları kullanılabilir türlerine göre filtreler.</span><span class="sxs-lookup"><span data-stu-id="67d43-273">Filters templates based on available types.</span></span> <span data-ttu-id="67d43-274">Önceden tanımlanmış değerler şunlardır: "proje", "Item" veya "diğer".</span><span class="sxs-lookup"><span data-stu-id="67d43-274">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="67d43-275">Bir kaynak veya şablon paketini kaldırır `PATH` veya `NUGET_ID` sağlanan.</span><span class="sxs-lookup"><span data-stu-id="67d43-275">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="67d43-276">Bir şablon kullanarak kaldırmak için bir `PATH`, yol tam olarak nitelemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="67d43-276">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="67d43-277">Örneğin, *C:/Users/\<kullanıcı > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* çalışır, ancak *./GarciaSoftware.ConsoleTemplate.CSharp* içeren gelen Klasör erişemez.</span><span class="sxs-lookup"><span data-stu-id="67d43-277">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="67d43-278">Ayrıca, şablonu yoldaki son Sonlandırıcı directory eğik çizgi içermez.</span><span class="sxs-lookup"><span data-stu-id="67d43-278">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="67d43-279">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="67d43-279">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="67d43-280">Belirli türde bir proje için tüm şablonları'nı bağlamında çalıştırılırken gösterir `dotnet new` tek başına komutu.</span><span class="sxs-lookup"><span data-stu-id="67d43-280">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="67d43-281">Belirli bir şablon bağlamında gibi çalıştırırken `dotnet new web -all`, `-all` zorla oluşturma bayrak olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="67d43-281">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="67d43-282">Bir proje çıkış dizinine içerdiğinde, bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="67d43-282">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="67d43-283">Komut için Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="67d43-283">Prints out help for the command.</span></span> <span data-ttu-id="67d43-284">İçin çağrılabilir `dotnet new` kendisini komutu veya herhangi bir şablon gibi `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="67d43-284">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="67d43-285">Belirtilen ad içeren şablonlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="67d43-285">Lists templates containing the specified name.</span></span> <span data-ttu-id="67d43-286">İçin çağırdıysanız `dotnet new` komut, belirtilen dizinde kullanılabilir olası şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="67d43-286">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="67d43-287">Örnek dizin zaten bir proje içeriyorsa, tüm proje şablonları listesinde değil.</span><span class="sxs-lookup"><span data-stu-id="67d43-287">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="67d43-288">Oluşturmak için şablon dili.</span><span class="sxs-lookup"><span data-stu-id="67d43-288">The language of the template to create.</span></span> <span data-ttu-id="67d43-289">Dil kabul şablon tarafından farklılık gösterir (varsayılan ayarlarında bkz [bağımsız değişkenleri](#arguments) bölümü).</span><span class="sxs-lookup"><span data-stu-id="67d43-289">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="67d43-290">Bazı şablonlar için geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="67d43-290">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="67d43-291">Bazı Kabukları yorumlama `#` olarak bir özel karakter.</span><span class="sxs-lookup"><span data-stu-id="67d43-291">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="67d43-292">Bu gibi durumlarda, dil parametre değeri, aşağıdaki gibi alın gerek `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="67d43-292">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="67d43-293">Oluşturulan çıktı adı.</span><span class="sxs-lookup"><span data-stu-id="67d43-293">The name for the created output.</span></span> <span data-ttu-id="67d43-294">Hiçbir ad belirtilmediği takdirde, geçerli dizin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="67d43-294">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="67d43-295">Oluşturulan çıktı yerleştirileceği konumu.</span><span class="sxs-lookup"><span data-stu-id="67d43-295">Location to place the generated output.</span></span> <span data-ttu-id="67d43-296">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="67d43-296">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="67d43-297">Şablon seçenekleri</span><span class="sxs-lookup"><span data-stu-id="67d43-297">Template options</span></span>

<span data-ttu-id="67d43-298">Her proje şablonu, ek seçenekler kullanılabilir olabilir.</span><span class="sxs-lookup"><span data-stu-id="67d43-298">Each project template may have additional options available.</span></span> <span data-ttu-id="67d43-299">Çekirdek şablonları aşağıdaki ek seçeneklere sahip olursunuz:</span><span class="sxs-lookup"><span data-stu-id="67d43-299">The core templates have the following additional options:</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="67d43-300">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="67d43-300">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="67d43-301">**konsolunda, angular, react, açarken kilitlenmesi, razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="67d43-301">**console, angular, react, reactredux, razorclasslib**</span></span>

  <span data-ttu-id="67d43-302">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="67d43-302">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="67d43-303">**ClassLib**</span><span class="sxs-lookup"><span data-stu-id="67d43-303">**classlib**</span></span>

<span data-ttu-id="67d43-304">`-f|--framework <FRAMEWORK>` -Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="67d43-304">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="67d43-305">Değerler: `netcoreapp2.0` bir .NET Core sınıf kitaplığı oluşturmak için veya `netstandard2.0` .NET standart sınıf kitaplığı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="67d43-305">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="67d43-306">Varsayılan değer `netstandard2.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="67d43-306">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="67d43-307">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="67d43-307">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="67d43-308">**MSTest, xunit**</span><span class="sxs-lookup"><span data-stu-id="67d43-308">**mstest, xunit**</span></span>

<span data-ttu-id="67d43-309">`-p|--enable-pack` -Etkinleştirir kullanarak projeyi için paketleme [dotnet paketi](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="67d43-309">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="67d43-310">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="67d43-310">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="67d43-311">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="67d43-311">**globaljson**</span></span>

<span data-ttu-id="67d43-312">`--sdk-version <VERSION_NUMBER>` -Kullanmak için .NET Core SDK'sı sürümünü belirtir *global.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="67d43-312">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="67d43-313">**Web**</span><span class="sxs-lookup"><span data-stu-id="67d43-313">**web**</span></span>

<span data-ttu-id="67d43-314">`--exclude-launch-settings` -Hariç *launchSettings.json* oluşturulan şablonundan.</span><span class="sxs-lookup"><span data-stu-id="67d43-314">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="67d43-315">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="67d43-315">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="67d43-316">`--no-https` -Proje HTTPS'yi gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="67d43-316">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="67d43-317">Bu seçenek yalnızca geçerlidir `IndividualAuth` veya `OrganizationalAuth` kullanılmayan.</span><span class="sxs-lookup"><span data-stu-id="67d43-317">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="67d43-318">**webapı**</span><span class="sxs-lookup"><span data-stu-id="67d43-318">**webapi**</span></span>

<span data-ttu-id="67d43-319">`-au|--auth <AUTHENTICATION_TYPE>` -Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="67d43-319">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="67d43-320">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="67d43-320">The possible values are:</span></span>

- <span data-ttu-id="67d43-321">`None` -Kimlik doğrulama yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="67d43-321">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="67d43-322">`IndividualB2C` -Azure AD B2C ile kimlik doğrulaması tek tek.</span><span class="sxs-lookup"><span data-stu-id="67d43-322">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="67d43-323">`SingleOrg` -Kuruluş kimlik doğrulaması için tek bir kiracı.</span><span class="sxs-lookup"><span data-stu-id="67d43-323">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="67d43-324">`Windows` -Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="67d43-324">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="67d43-325">`--aad-b2c-instance <INSTANCE>` -Bağlanmak için Azure Active Directory B2C örnek.</span><span class="sxs-lookup"><span data-stu-id="67d43-325">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="67d43-326">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="67d43-326">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="67d43-327">Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="67d43-327">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="67d43-328">`-ssp|--susi-policy-id <ID>` -Bu proje için oturum açma ve kaydolma ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="67d43-328">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="67d43-329">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="67d43-329">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="67d43-330">`--aad-instance <INSTANCE>` -Bağlanmak için Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="67d43-330">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="67d43-331">İle kullanma `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="67d43-331">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="67d43-332">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="67d43-332">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="67d43-333">`--client-id <ID>` -Bu proje için istemci kimliği.</span><span class="sxs-lookup"><span data-stu-id="67d43-333">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="67d43-334">İle kullanma `IndividualB2C` veya `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="67d43-334">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="67d43-335">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="67d43-335">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="67d43-336">`--domain <DOMAIN>` -Dizin kiracısı için etki alanı.</span><span class="sxs-lookup"><span data-stu-id="67d43-336">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="67d43-337">İle kullanma `SingleOrg` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="67d43-337">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="67d43-338">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="67d43-338">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="67d43-339">`--tenant-id <ID>` -Tenantıd bağlanmak için kimliği dizini.</span><span class="sxs-lookup"><span data-stu-id="67d43-339">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="67d43-340">İle kullanma `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="67d43-340">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="67d43-341">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="67d43-341">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="67d43-342">`-r|--org-read-access` -Bu uygulamanın dizine okuma erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="67d43-342">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="67d43-343">Yalnızca uygulandığı `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="67d43-343">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="67d43-344">`--exclude-launch-settings` -Hariç *launchSettings.json* oluşturulan şablonundan.</span><span class="sxs-lookup"><span data-stu-id="67d43-344">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="67d43-345">`-uld|--use-local-db` -LocalDB yerine SQLite kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="67d43-345">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="67d43-346">Yalnızca uygulandığı `Individual` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="67d43-346">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="67d43-347">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="67d43-347">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="67d43-348">`--no-https` -Proje HTTPS'yi gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="67d43-348">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="67d43-349">`app.UseHsts` ve `app.UseHttpsRedirection` için eklenmez `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="67d43-349">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="67d43-350">Bu seçenek yalnızca geçerlidir `Individual`, `IndividualB2C`, `SingleOrg`, veya `MultiOrg` kullanılmayan.</span><span class="sxs-lookup"><span data-stu-id="67d43-350">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="67d43-351">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="67d43-351">**mvc, razor**</span></span>

<span data-ttu-id="67d43-352">`-au|--auth <AUTHENTICATION_TYPE>` -Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="67d43-352">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="67d43-353">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="67d43-353">The possible values are:</span></span>

- <span data-ttu-id="67d43-354">`None` -Kimlik doğrulama yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="67d43-354">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="67d43-355">`Individual` -Tek tek kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="67d43-355">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="67d43-356">`IndividualB2C` -Azure AD B2C ile kimlik doğrulaması tek tek.</span><span class="sxs-lookup"><span data-stu-id="67d43-356">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="67d43-357">`SingleOrg` -Kuruluş kimlik doğrulaması için tek bir kiracı.</span><span class="sxs-lookup"><span data-stu-id="67d43-357">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="67d43-358">`MultiOrg` -Birden fazla Kiracı için Kurumsal kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="67d43-358">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="67d43-359">`Windows` -Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="67d43-359">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="67d43-360">`--aad-b2c-instance <INSTANCE>` -Bağlanmak için Azure Active Directory B2C örnek.</span><span class="sxs-lookup"><span data-stu-id="67d43-360">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="67d43-361">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="67d43-361">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="67d43-362">Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="67d43-362">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="67d43-363">`-ssp|--susi-policy-id <ID>` -Bu proje için oturum açma ve kaydolma ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="67d43-363">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="67d43-364">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="67d43-364">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="67d43-365">`-rp|--reset-password-policy-id <ID>` -Bu proje için reset parola ilkesi kimliği.</span><span class="sxs-lookup"><span data-stu-id="67d43-365">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="67d43-366">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="67d43-366">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="67d43-367">`-ep|--edit-profile-policy-id <ID>` -Bu proje için düzenleme profili ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="67d43-367">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="67d43-368">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="67d43-368">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="67d43-369">`--aad-instance <INSTANCE>` -Bağlanmak için Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="67d43-369">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="67d43-370">İle kullanma `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="67d43-370">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="67d43-371">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="67d43-371">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="67d43-372">`--client-id <ID>` -Bu proje için istemci kimliği.</span><span class="sxs-lookup"><span data-stu-id="67d43-372">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="67d43-373">İle kullanma `IndividualB2C`, `SingleOrg`, veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="67d43-373">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="67d43-374">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="67d43-374">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="67d43-375">`--domain <DOMAIN>` -Dizin kiracısı için etki alanı.</span><span class="sxs-lookup"><span data-stu-id="67d43-375">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="67d43-376">İle kullanma `SingleOrg` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="67d43-376">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="67d43-377">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="67d43-377">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="67d43-378">`--tenant-id <ID>` -Tenantıd bağlanmak için kimliği dizini.</span><span class="sxs-lookup"><span data-stu-id="67d43-378">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="67d43-379">İle kullanma `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="67d43-379">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="67d43-380">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="67d43-380">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="67d43-381">`--callback-path <PATH>` -Yeniden yönlendirme URI'si uygulamanın taban yolu içindeki istek yolu.</span><span class="sxs-lookup"><span data-stu-id="67d43-381">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="67d43-382">İle kullanma `SingleOrg` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="67d43-382">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="67d43-383">Varsayılan değer `/signin-oidc` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="67d43-383">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="67d43-384">`-r|--org-read-access` -Bu uygulamanın dizine okuma erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="67d43-384">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="67d43-385">Yalnızca uygulandığı `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="67d43-385">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="67d43-386">`--exclude-launch-settings` -Hariç *launchSettings.json* oluşturulan şablonundan.</span><span class="sxs-lookup"><span data-stu-id="67d43-386">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="67d43-387">`--use-browserlink` -BrowserLink projede içerir.</span><span class="sxs-lookup"><span data-stu-id="67d43-387">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="67d43-388">`-uld|--use-local-db` -LocalDB yerine SQLite kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="67d43-388">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="67d43-389">Yalnızca uygulandığı `Individual` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="67d43-389">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="67d43-390">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="67d43-390">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="67d43-391">`--no-https` -Proje HTTPS'yi gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="67d43-391">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="67d43-392">`app.UseHsts` ve `app.UseHttpsRedirection` için eklenmez `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="67d43-392">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="67d43-393">Bu seçenek yalnızca geçerlidir `Individual`, `IndividualB2C`, `SingleOrg`, veya `MultiOrg` kullanılmayan.</span><span class="sxs-lookup"><span data-stu-id="67d43-393">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="67d43-394">**Sayfa**</span><span class="sxs-lookup"><span data-stu-id="67d43-394">**page**</span></span>

<span data-ttu-id="67d43-395">`-na|--namespace <NAMESPACE_NAME>`-Namespace üretilen kod için.</span><span class="sxs-lookup"><span data-stu-id="67d43-395">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="67d43-396">Varsayılan değer `MyApp.Namespace` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="67d43-396">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="67d43-397">`-np|--no-pagemodel` -Bir PageModel olmadan sayfası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="67d43-397">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="67d43-398">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="67d43-398">**viewimports**</span></span>

<span data-ttu-id="67d43-399">`-na|--namespace <NAMESPACE_NAME>`-Namespace üretilen kod için.</span><span class="sxs-lookup"><span data-stu-id="67d43-399">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="67d43-400">Varsayılan değer `MyApp.Namespace` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="67d43-400">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="67d43-401">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="67d43-401">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="67d43-402">**konsolunda, angular, react, açarken kilitlenmesi**</span><span class="sxs-lookup"><span data-stu-id="67d43-402">**console, angular, react, reactredux**</span></span>

  <span data-ttu-id="67d43-403">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="67d43-403">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="67d43-404">**ClassLib**</span><span class="sxs-lookup"><span data-stu-id="67d43-404">**classlib**</span></span>

<span data-ttu-id="67d43-405">`-f|--framework <FRAMEWORK>` -Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="67d43-405">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="67d43-406">Değerler: `netcoreapp2.0` bir .NET Core sınıf kitaplığı oluşturmak için veya `netstandard2.0` .NET standart sınıf kitaplığı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="67d43-406">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="67d43-407">Varsayılan değer `netstandard2.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="67d43-407">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="67d43-408">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="67d43-408">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="67d43-409">**MSTest, xunit**</span><span class="sxs-lookup"><span data-stu-id="67d43-409">**mstest, xunit**</span></span>

<span data-ttu-id="67d43-410">`-p|--enable-pack` -Etkinleştirir kullanarak projeyi için paketleme [dotnet paketi](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="67d43-410">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="67d43-411">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="67d43-411">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="67d43-412">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="67d43-412">**globaljson**</span></span>

<span data-ttu-id="67d43-413">`--sdk-version <VERSION_NUMBER>` -Kullanmak için .NET Core SDK'sı sürümünü belirtir *global.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="67d43-413">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="67d43-414">**Web**</span><span class="sxs-lookup"><span data-stu-id="67d43-414">**web**</span></span>

<span data-ttu-id="67d43-415">`--use-launch-settings` -İçeren *launchSettings.json* oluşturulan şablon çıktı.</span><span class="sxs-lookup"><span data-stu-id="67d43-415">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="67d43-416">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="67d43-416">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="67d43-417">**webapı**</span><span class="sxs-lookup"><span data-stu-id="67d43-417">**webapi**</span></span>

<span data-ttu-id="67d43-418">`-au|--auth <AUTHENTICATION_TYPE>` -Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="67d43-418">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="67d43-419">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="67d43-419">The possible values are:</span></span>

- <span data-ttu-id="67d43-420">`None` -Kimlik doğrulama yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="67d43-420">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="67d43-421">`IndividualB2C` -Azure AD B2C ile kimlik doğrulaması tek tek.</span><span class="sxs-lookup"><span data-stu-id="67d43-421">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="67d43-422">`SingleOrg` -Kuruluş kimlik doğrulaması için tek bir kiracı.</span><span class="sxs-lookup"><span data-stu-id="67d43-422">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="67d43-423">`Windows` -Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="67d43-423">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="67d43-424">`--aad-b2c-instance <INSTANCE>` -Bağlanmak için Azure Active Directory B2C örnek.</span><span class="sxs-lookup"><span data-stu-id="67d43-424">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="67d43-425">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="67d43-425">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="67d43-426">Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="67d43-426">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="67d43-427">`-ssp|--susi-policy-id <ID>` -Bu proje için oturum açma ve kaydolma ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="67d43-427">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="67d43-428">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="67d43-428">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="67d43-429">`--aad-instance <INSTANCE>` -Bağlanmak için Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="67d43-429">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="67d43-430">İle kullanma `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="67d43-430">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="67d43-431">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="67d43-431">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="67d43-432">`--client-id <ID>` -Bu proje için istemci kimliği.</span><span class="sxs-lookup"><span data-stu-id="67d43-432">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="67d43-433">İle kullanma `IndividualB2C` veya `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="67d43-433">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="67d43-434">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="67d43-434">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="67d43-435">`--domain <DOMAIN>` -Dizin kiracısı için etki alanı.</span><span class="sxs-lookup"><span data-stu-id="67d43-435">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="67d43-436">İle kullanma `SingleOrg` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="67d43-436">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="67d43-437">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="67d43-437">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="67d43-438">`--tenant-id <ID>` -Tenantıd bağlanmak için kimliği dizini.</span><span class="sxs-lookup"><span data-stu-id="67d43-438">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="67d43-439">İle kullanma `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="67d43-439">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="67d43-440">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="67d43-440">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="67d43-441">`-r|--org-read-access` -Bu uygulamanın dizine okuma erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="67d43-441">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="67d43-442">Yalnızca uygulandığı `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="67d43-442">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="67d43-443">`--use-launch-settings` -İçeren *launchSettings.json* oluşturulan şablon çıktı.</span><span class="sxs-lookup"><span data-stu-id="67d43-443">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="67d43-444">`-uld|--use-local-db` -LocalDB yerine SQLite kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="67d43-444">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="67d43-445">Yalnızca uygulandığı `Individual` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="67d43-445">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="67d43-446">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="67d43-446">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="67d43-447">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="67d43-447">**mvc, razor**</span></span>

<span data-ttu-id="67d43-448">`-au|--auth <AUTHENTICATION_TYPE>` -Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="67d43-448">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="67d43-449">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="67d43-449">The possible values are:</span></span>

- <span data-ttu-id="67d43-450">`None` -Kimlik doğrulama yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="67d43-450">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="67d43-451">`Individual` -Tek tek kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="67d43-451">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="67d43-452">`IndividualB2C` -Azure AD B2C ile kimlik doğrulaması tek tek.</span><span class="sxs-lookup"><span data-stu-id="67d43-452">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="67d43-453">`SingleOrg` -Kuruluş kimlik doğrulaması için tek bir kiracı.</span><span class="sxs-lookup"><span data-stu-id="67d43-453">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="67d43-454">`MultiOrg` -Birden fazla Kiracı için Kurumsal kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="67d43-454">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="67d43-455">`Windows` -Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="67d43-455">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="67d43-456">`--aad-b2c-instance <INSTANCE>` -Bağlanmak için Azure Active Directory B2C örnek.</span><span class="sxs-lookup"><span data-stu-id="67d43-456">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="67d43-457">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="67d43-457">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="67d43-458">Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="67d43-458">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="67d43-459">`-ssp|--susi-policy-id <ID>` -Bu proje için oturum açma ve kaydolma ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="67d43-459">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="67d43-460">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="67d43-460">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="67d43-461">`-rp|--reset-password-policy-id <ID>` -Bu proje için reset parola ilkesi kimliği.</span><span class="sxs-lookup"><span data-stu-id="67d43-461">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="67d43-462">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="67d43-462">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="67d43-463">`-ep|--edit-profile-policy-id <ID>` -Bu proje için düzenleme profili ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="67d43-463">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="67d43-464">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="67d43-464">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="67d43-465">`--aad-instance <INSTANCE>` -Bağlanmak için Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="67d43-465">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="67d43-466">İle kullanma `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="67d43-466">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="67d43-467">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="67d43-467">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="67d43-468">`--client-id <ID>` -Bu proje için istemci kimliği.</span><span class="sxs-lookup"><span data-stu-id="67d43-468">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="67d43-469">İle kullanma `IndividualB2C`, `SingleOrg`, veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="67d43-469">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="67d43-470">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="67d43-470">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="67d43-471">`--domain <DOMAIN>` -Dizin kiracısı için etki alanı.</span><span class="sxs-lookup"><span data-stu-id="67d43-471">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="67d43-472">İle kullanma `SingleOrg` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="67d43-472">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="67d43-473">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="67d43-473">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="67d43-474">`--tenant-id <ID>` -Tenantıd bağlanmak için kimliği dizini.</span><span class="sxs-lookup"><span data-stu-id="67d43-474">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="67d43-475">İle kullanma `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="67d43-475">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="67d43-476">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="67d43-476">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="67d43-477">`--callback-path <PATH>` -Yeniden yönlendirme URI'si uygulamanın taban yolu içindeki istek yolu.</span><span class="sxs-lookup"><span data-stu-id="67d43-477">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="67d43-478">İle kullanma `SingleOrg` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="67d43-478">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="67d43-479">Varsayılan değer `/signin-oidc` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="67d43-479">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="67d43-480">`-r|--org-read-access` -Bu uygulamanın dizine okuma erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="67d43-480">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="67d43-481">Yalnızca uygulandığı `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="67d43-481">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="67d43-482">`--use-launch-settings` -İçeren *launchSettings.json* oluşturulan şablon çıktı.</span><span class="sxs-lookup"><span data-stu-id="67d43-482">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="67d43-483">`--use-browserlink` -BrowserLink projede içerir.</span><span class="sxs-lookup"><span data-stu-id="67d43-483">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="67d43-484">`-uld|--use-local-db` -LocalDB yerine SQLite kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="67d43-484">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="67d43-485">Yalnızca uygulandığı `Individual` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="67d43-485">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="67d43-486">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="67d43-486">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="67d43-487">**Sayfa**</span><span class="sxs-lookup"><span data-stu-id="67d43-487">**page**</span></span>

<span data-ttu-id="67d43-488">`-na|--namespace <NAMESPACE_NAME>`-Namespace üretilen kod için.</span><span class="sxs-lookup"><span data-stu-id="67d43-488">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="67d43-489">Varsayılan değer `MyApp.Namespace` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="67d43-489">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="67d43-490">`-np|--no-pagemodel` -Bir PageModel olmadan sayfası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="67d43-490">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="67d43-491">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="67d43-491">**viewimports**</span></span>

<span data-ttu-id="67d43-492">`-na|--namespace <NAMESPACE_NAME>`-Namespace üretilen kod için.</span><span class="sxs-lookup"><span data-stu-id="67d43-492">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="67d43-493">Varsayılan değer `MyApp.Namespace` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="67d43-493">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="67d43-494">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="67d43-494">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="67d43-495">**Konsolu, xunit, mstest, web, webapı**</span><span class="sxs-lookup"><span data-stu-id="67d43-495">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="67d43-496">`-f|--framework` -Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="67d43-496">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="67d43-497">Değerler: `netcoreapp1.0` veya `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="67d43-497">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="67d43-498">Varsayılan değer `netcoreapp1.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="67d43-498">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="67d43-499">**ClassLib**</span><span class="sxs-lookup"><span data-stu-id="67d43-499">**classlib**</span></span>

<span data-ttu-id="67d43-500">`-f|--framework` -Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="67d43-500">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="67d43-501">Değerler: `netcoreapp1.0`, `netcoreapp1.1`, veya `netstandard1.0` için `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="67d43-501">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="67d43-502">Varsayılan değer `netstandard1.4` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="67d43-502">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="67d43-503">**mvc**</span><span class="sxs-lookup"><span data-stu-id="67d43-503">**mvc**</span></span>

<span data-ttu-id="67d43-504">`-f|--framework` -Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="67d43-504">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="67d43-505">Değerler: `netcoreapp1.0` veya `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="67d43-505">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="67d43-506">Varsayılan değer `netcoreapp1.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="67d43-506">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="67d43-507">`-au|--auth` -Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="67d43-507">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="67d43-508">Değerler: `None` veya `Individual`.</span><span class="sxs-lookup"><span data-stu-id="67d43-508">Values: `None` or `Individual`.</span></span> <span data-ttu-id="67d43-509">Varsayılan değer `None` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="67d43-509">The default value is `None`.</span></span>

<span data-ttu-id="67d43-510">`-uld|--use-local-db` -LocalDB yerine SQLite kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="67d43-510">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="67d43-511">Değerler: `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="67d43-511">Values: `true` or `false`.</span></span> <span data-ttu-id="67d43-512">Varsayılan değer `false` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="67d43-512">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="67d43-513">Örnekler</span><span class="sxs-lookup"><span data-stu-id="67d43-513">Examples</span></span>

<span data-ttu-id="67d43-514">Geçerli dizinde bir F # konsol uygulaması projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="67d43-514">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="67d43-515">Belirtilen dizin (yalnızca .NET Core SDK 2.0 veya sonraki sürümler ile kullanılabilir) bir .NET Standard sınıf kitaplığı projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="67d43-515">Create a .NET Standard class library project in the specified directory (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="67d43-516">Kimlik doğrulaması olmayan geçerli dizinde yeni bir ASP.NET Core C# MVC uygulaması projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="67d43-516">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication:</span></span>

`dotnet new mvc -au None`

<span data-ttu-id="67d43-517">Yeni bir xUnit uygulama oluşturun:</span><span class="sxs-lookup"><span data-stu-id="67d43-517">Create a new xUnit application:</span></span>

`dotnet new xunit`

<span data-ttu-id="67d43-518">MVC için tüm şablonları listeler:</span><span class="sxs-lookup"><span data-stu-id="67d43-518">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="67d43-519">ASP.NET Core (komut seçeneği kullanılabilir .NET Core SDK 1.1 ve yalnızca sonraki sürümleri için) için tek sayfalı uygulama şablonları 2.0 sürümünü yükleyin:</span><span class="sxs-lookup"><span data-stu-id="67d43-519">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

<span data-ttu-id="67d43-520">Oluşturma bir *global.json* SDK'sı sürüm 2.0.0 (yalnızca .NET Core SDK 2.0 veya sonraki sürümler ile kullanılabilir) ayarı geçerli dizin:</span><span class="sxs-lookup"><span data-stu-id="67d43-520">Create a *global.json* in the current directory setting the SDK version to 2.0.0 (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="67d43-521">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="67d43-521">See also</span></span>

* [<span data-ttu-id="67d43-522">Yeni dotnet için özel şablonlar</span><span class="sxs-lookup"><span data-stu-id="67d43-522">Custom templates for dotnet new</span></span>](custom-templates.md)  
* [<span data-ttu-id="67d43-523">Dotnet new için özel şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="67d43-523">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)  
* [<span data-ttu-id="67d43-524">DotNet/dotnet-şablonu-örnekleri GitHub deposu</span><span class="sxs-lookup"><span data-stu-id="67d43-524">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)  
* [<span data-ttu-id="67d43-525">Yeni dotnet şablonları</span><span class="sxs-lookup"><span data-stu-id="67d43-525">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
