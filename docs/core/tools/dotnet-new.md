---
title: DotNet yeni komutu
description: Belirtilen şablonu temel alan yeni .NET Core projeleri dotnet yeni bir komut oluşturur.
ms.date: 05/06/2019
ms.openlocfilehash: f8bc8cb59ae6e421f4e9bd05925376399939056d
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65878311"
---
# <a name="dotnet-new"></a><span data-ttu-id="6c7a4-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="6c7a4-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="6c7a4-104">Ad</span><span class="sxs-lookup"><span data-stu-id="6c7a4-104">Name</span></span>

<span data-ttu-id="6c7a4-105">`dotnet new` -Yeni Proje, yapılandırma dosyası veya belirtilen şablonu temel alan bir çözüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="6c7a4-106">Synopsis</span><span class="sxs-lookup"><span data-stu-id="6c7a4-106">Synopsis</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="6c7a4-107">.NET core 2.2</span><span class="sxs-lookup"><span data-stu-id="6c7a4-107">.NET Core 2.2</span></span>](#tab/netcore22)

```console
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="6c7a4-108">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="6c7a4-108">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="6c7a4-109">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="6c7a4-109">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="6c7a4-110">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="6c7a4-110">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="6c7a4-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6c7a4-111">Description</span></span>

<span data-ttu-id="6c7a4-112">`dotnet new` Komutu geçerli bir .NET Core projesi başlatmak için kolay bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-112">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="6c7a4-113">Komut çağrıları [şablon altyapısı](https://github.com/dotnet/templating) yapıları belirtilen şablonu ve seçenekleri bağlı disk oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-113">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="6c7a4-114">Arguments</span><span class="sxs-lookup"><span data-stu-id="6c7a4-114">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="6c7a4-115">Komut çağrıldığında örneği oluşturmak için şablon.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-115">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="6c7a4-116">Her şablon geçirebilirsiniz belirli seçenekler olabilir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-116">Each template might have specific options you can pass.</span></span> <span data-ttu-id="6c7a4-117">Daha fazla bilgi için [şablon seçeneklerini](#template-options).</span><span class="sxs-lookup"><span data-stu-id="6c7a4-117">For more information, see [Template options](#template-options).</span></span>

<span data-ttu-id="6c7a4-118">Varsa `TEMPLATE` değeri değil metinde tam eşleşme **şablonları** veya **kısa ad** sütun, bir alt dize eşleşmesinin, bu iki sütun üzerinde gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-118">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column, a substring match is performed on those two columns.</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="6c7a4-119">.NET core 2.2</span><span class="sxs-lookup"><span data-stu-id="6c7a4-119">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="6c7a4-120">Komutu, şablonları, varsayılan listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-120">The command contains a default list of templates.</span></span> <span data-ttu-id="6c7a4-121">Kullanım `dotnet new -l` kullanılabilir şablonların listesini alamadı.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-121">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="6c7a4-122">Aşağıdaki tablo, .NET Core SDK 2.2.100 önceden yüklenmiş olarak gelen şablonları gösterir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-122">The following table shows the templates that come pre-installed with the .NET Core SDK 2.2.100.</span></span> <span data-ttu-id="6c7a4-123">Şablonunuz için varsayılan dili köşeli ayraçlar içinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-123">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="6c7a4-124">Şablonlar</span><span class="sxs-lookup"><span data-stu-id="6c7a4-124">Templates</span></span>                                    | <span data-ttu-id="6c7a4-125">Kısa Ad</span><span class="sxs-lookup"><span data-stu-id="6c7a4-125">Short Name</span></span>        | <span data-ttu-id="6c7a4-126">Dil</span><span class="sxs-lookup"><span data-stu-id="6c7a4-126">Language</span></span>     | <span data-ttu-id="6c7a4-127">Etiketler</span><span class="sxs-lookup"><span data-stu-id="6c7a4-127">Tags</span></span>                                  |
|----------------------------------------------|-------------------|--------------|---------------------------------------|
| <span data-ttu-id="6c7a4-128">Konsol Uygulaması</span><span class="sxs-lookup"><span data-stu-id="6c7a4-128">Console Application</span></span>                          | `console`         | <span data-ttu-id="6c7a4-129">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="6c7a4-129">[C#], F#, VB</span></span> | <span data-ttu-id="6c7a4-130">Ortak/Konsolu</span><span class="sxs-lookup"><span data-stu-id="6c7a4-130">Common/Console</span></span>                        |
| <span data-ttu-id="6c7a4-131">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="6c7a4-131">Class library</span></span>                                | `classlib`        | <span data-ttu-id="6c7a4-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="6c7a4-132">[C#], F#, VB</span></span> | <span data-ttu-id="6c7a4-133">Ortak/Kitaplık</span><span class="sxs-lookup"><span data-stu-id="6c7a4-133">Common/Library</span></span>                        |
| <span data-ttu-id="6c7a4-134">Unit Test Project</span><span class="sxs-lookup"><span data-stu-id="6c7a4-134">Unit Test Project</span></span>                            | `mstest`          | <span data-ttu-id="6c7a4-135">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="6c7a4-135">[C#], F#, VB</span></span> | <span data-ttu-id="6c7a4-136">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="6c7a4-136">Test/MSTest</span></span>                           |
| <span data-ttu-id="6c7a4-137">NUnit 3 Test projesi</span><span class="sxs-lookup"><span data-stu-id="6c7a4-137">NUnit 3 Test Project</span></span>                         | `nunit`           | <span data-ttu-id="6c7a4-138">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="6c7a4-138">[C#], F#, VB</span></span> | <span data-ttu-id="6c7a4-139">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="6c7a4-139">Test/NUnit</span></span>                            |
| <span data-ttu-id="6c7a4-140">NUnit 3 Test öğesi</span><span class="sxs-lookup"><span data-stu-id="6c7a4-140">NUnit 3 Test Item</span></span>                            | `nunit-test`      | <span data-ttu-id="6c7a4-141">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="6c7a4-141">[C#], F#, VB</span></span> | <span data-ttu-id="6c7a4-142">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="6c7a4-142">Test/NUnit</span></span>                            |
| <span data-ttu-id="6c7a4-143">xUnit Test projesi</span><span class="sxs-lookup"><span data-stu-id="6c7a4-143">xUnit Test Project</span></span>                           | `xunit`           | <span data-ttu-id="6c7a4-144">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="6c7a4-144">[C#], F#, VB</span></span> | <span data-ttu-id="6c7a4-145">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="6c7a4-145">Test/xUnit</span></span>                            |
| <span data-ttu-id="6c7a4-146">Razor sayfası</span><span class="sxs-lookup"><span data-stu-id="6c7a4-146">Razor Page</span></span>                                   | `page`            | <span data-ttu-id="6c7a4-147">[C#]</span><span class="sxs-lookup"><span data-stu-id="6c7a4-147">[C#]</span></span>         | <span data-ttu-id="6c7a4-148">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="6c7a4-148">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="6c7a4-149">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="6c7a4-149">MVC ViewImports</span></span>                              | `viewimports`     | <span data-ttu-id="6c7a4-150">[C#]</span><span class="sxs-lookup"><span data-stu-id="6c7a4-150">[C#]</span></span>         | <span data-ttu-id="6c7a4-151">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="6c7a4-151">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="6c7a4-152">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="6c7a4-152">MVC ViewStart</span></span>                                | `viewstart`       | <span data-ttu-id="6c7a4-153">[C#]</span><span class="sxs-lookup"><span data-stu-id="6c7a4-153">[C#]</span></span>         | <span data-ttu-id="6c7a4-154">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="6c7a4-154">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="6c7a4-155">ASP.NET Core boş</span><span class="sxs-lookup"><span data-stu-id="6c7a4-155">ASP.NET Core Empty</span></span>                           | `web`             | <span data-ttu-id="6c7a4-156">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="6c7a4-156">[C#], F#</span></span>     | <span data-ttu-id="6c7a4-157">Web veya boş</span><span class="sxs-lookup"><span data-stu-id="6c7a4-157">Web/Empty</span></span>                             |
| <span data-ttu-id="6c7a4-158">ASP.NET Core Web uygulaması (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="6c7a4-158">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`             | <span data-ttu-id="6c7a4-159">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="6c7a4-159">[C#], F#</span></span>     | <span data-ttu-id="6c7a4-160">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="6c7a4-160">Web/MVC</span></span>                               |
| <span data-ttu-id="6c7a4-161">ASP.NET Core Web uygulaması</span><span class="sxs-lookup"><span data-stu-id="6c7a4-161">ASP.NET Core Web App</span></span>                         | <span data-ttu-id="6c7a4-162">`webapp`, `razor`</span><span class="sxs-lookup"><span data-stu-id="6c7a4-162">`webapp`, `razor`</span></span> | <span data-ttu-id="6c7a4-163">[C#]</span><span class="sxs-lookup"><span data-stu-id="6c7a4-163">[C#]</span></span>         | <span data-ttu-id="6c7a4-164">MVC/Web/Razor sayfaları</span><span class="sxs-lookup"><span data-stu-id="6c7a4-164">Web/MVC/Razor Pages</span></span>                   |
| <span data-ttu-id="6c7a4-165">Angular ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6c7a4-165">ASP.NET Core with Angular</span></span>                    | `angular`         | <span data-ttu-id="6c7a4-166">[C#]</span><span class="sxs-lookup"><span data-stu-id="6c7a4-166">[C#]</span></span>         | <span data-ttu-id="6c7a4-167">MVC/Web/SPA</span><span class="sxs-lookup"><span data-stu-id="6c7a4-167">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="6c7a4-168">React.js ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6c7a4-168">ASP.NET Core with React.js</span></span>                   | `react`           | <span data-ttu-id="6c7a4-169">[C#]</span><span class="sxs-lookup"><span data-stu-id="6c7a4-169">[C#]</span></span>         | <span data-ttu-id="6c7a4-170">MVC/Web/SPA</span><span class="sxs-lookup"><span data-stu-id="6c7a4-170">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="6c7a4-171">ASP.NET Core React.js ve Redux</span><span class="sxs-lookup"><span data-stu-id="6c7a4-171">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`      | <span data-ttu-id="6c7a4-172">[C#]</span><span class="sxs-lookup"><span data-stu-id="6c7a4-172">[C#]</span></span>         | <span data-ttu-id="6c7a4-173">MVC/Web/SPA</span><span class="sxs-lookup"><span data-stu-id="6c7a4-173">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="6c7a4-174">Razor sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="6c7a4-174">Razor Class Library</span></span>                          | `razorclasslib`   | <span data-ttu-id="6c7a4-175">[C#]</span><span class="sxs-lookup"><span data-stu-id="6c7a4-175">[C#]</span></span>         | <span data-ttu-id="6c7a4-176">Web/Razor/kitaplık/Razor sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="6c7a4-176">Web/Razor/Library/Razor Class Library</span></span> |
| <span data-ttu-id="6c7a4-177">ASP.NET Core Web API'si</span><span class="sxs-lookup"><span data-stu-id="6c7a4-177">ASP.NET Core Web API</span></span>                         | `webapi`          | <span data-ttu-id="6c7a4-178">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="6c7a4-178">[C#], F#</span></span>     | <span data-ttu-id="6c7a4-179">Web/Webapı</span><span class="sxs-lookup"><span data-stu-id="6c7a4-179">Web/WebAPI</span></span>                            |
| <span data-ttu-id="6c7a4-180">Global.JSON dosyasını</span><span class="sxs-lookup"><span data-stu-id="6c7a4-180">global.json file</span></span>                             | `globaljson`      |              | <span data-ttu-id="6c7a4-181">Config</span><span class="sxs-lookup"><span data-stu-id="6c7a4-181">Config</span></span>                                |
| <span data-ttu-id="6c7a4-182">NuGet Config</span><span class="sxs-lookup"><span data-stu-id="6c7a4-182">NuGet Config</span></span>                                 | `nugetconfig`     |              | <span data-ttu-id="6c7a4-183">Config</span><span class="sxs-lookup"><span data-stu-id="6c7a4-183">Config</span></span>                                |
| <span data-ttu-id="6c7a4-184">Web yapılandırması</span><span class="sxs-lookup"><span data-stu-id="6c7a4-184">Web Config</span></span>                                   | `webconfig`       |              | <span data-ttu-id="6c7a4-185">Config</span><span class="sxs-lookup"><span data-stu-id="6c7a4-185">Config</span></span>                                |
| <span data-ttu-id="6c7a4-186">Çözüm dosyası</span><span class="sxs-lookup"><span data-stu-id="6c7a4-186">Solution File</span></span>                                | `sln`             |              | <span data-ttu-id="6c7a4-187">Çözüm</span><span class="sxs-lookup"><span data-stu-id="6c7a4-187">Solution</span></span>                              |

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="6c7a4-188">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="6c7a4-188">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="6c7a4-189">Komutu, şablonları, varsayılan listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-189">The command contains a default list of templates.</span></span> <span data-ttu-id="6c7a4-190">Kullanım `dotnet new -l` kullanılabilir şablonların listesini alamadı.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-190">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="6c7a4-191">Aşağıdaki tablo, .NET Core SDK 2.1.300 önceden yüklenmiş olarak gelen şablonları gösterir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-191">The following table shows the templates that come pre-installed with the .NET Core SDK 2.1.300.</span></span> <span data-ttu-id="6c7a4-192">Şablonunuz için varsayılan dili köşeli ayraçlar içinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-192">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="6c7a4-193">Şablonlar</span><span class="sxs-lookup"><span data-stu-id="6c7a4-193">Templates</span></span>                                    | <span data-ttu-id="6c7a4-194">Kısa Ad</span><span class="sxs-lookup"><span data-stu-id="6c7a4-194">Short Name</span></span>      | <span data-ttu-id="6c7a4-195">Dil</span><span class="sxs-lookup"><span data-stu-id="6c7a4-195">Language</span></span>     | <span data-ttu-id="6c7a4-196">Etiketler</span><span class="sxs-lookup"><span data-stu-id="6c7a4-196">Tags</span></span>                                  |
|----------------------------------------------|-----------------|--------------|---------------------------------------|
| <span data-ttu-id="6c7a4-197">Konsol Uygulaması</span><span class="sxs-lookup"><span data-stu-id="6c7a4-197">Console Application</span></span>                          | `console`       | <span data-ttu-id="6c7a4-198">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="6c7a4-198">[C#], F#, VB</span></span> | <span data-ttu-id="6c7a4-199">Ortak/Konsolu</span><span class="sxs-lookup"><span data-stu-id="6c7a4-199">Common/Console</span></span>                        |
| <span data-ttu-id="6c7a4-200">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="6c7a4-200">Class library</span></span>                                | `classlib`      | <span data-ttu-id="6c7a4-201">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="6c7a4-201">[C#], F#, VB</span></span> | <span data-ttu-id="6c7a4-202">Ortak/Kitaplık</span><span class="sxs-lookup"><span data-stu-id="6c7a4-202">Common/Library</span></span>                        |
| <span data-ttu-id="6c7a4-203">Unit Test Project</span><span class="sxs-lookup"><span data-stu-id="6c7a4-203">Unit Test Project</span></span>                            | `mstest`        | <span data-ttu-id="6c7a4-204">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="6c7a4-204">[C#], F#, VB</span></span> | <span data-ttu-id="6c7a4-205">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="6c7a4-205">Test/MSTest</span></span>                           |
| <span data-ttu-id="6c7a4-206">xUnit Test projesi</span><span class="sxs-lookup"><span data-stu-id="6c7a4-206">xUnit Test Project</span></span>                           | `xunit`         | <span data-ttu-id="6c7a4-207">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="6c7a4-207">[C#], F#, VB</span></span> | <span data-ttu-id="6c7a4-208">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="6c7a4-208">Test/xUnit</span></span>                            |
| <span data-ttu-id="6c7a4-209">Razor sayfası</span><span class="sxs-lookup"><span data-stu-id="6c7a4-209">Razor Page</span></span>                                   | `page`          | <span data-ttu-id="6c7a4-210">[C#]</span><span class="sxs-lookup"><span data-stu-id="6c7a4-210">[C#]</span></span>         | <span data-ttu-id="6c7a4-211">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="6c7a4-211">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="6c7a4-212">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="6c7a4-212">MVC ViewImports</span></span>                              | `viewimports`   | <span data-ttu-id="6c7a4-213">[C#]</span><span class="sxs-lookup"><span data-stu-id="6c7a4-213">[C#]</span></span>         | <span data-ttu-id="6c7a4-214">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="6c7a4-214">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="6c7a4-215">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="6c7a4-215">MVC ViewStart</span></span>                                | `viewstart`     | <span data-ttu-id="6c7a4-216">[C#]</span><span class="sxs-lookup"><span data-stu-id="6c7a4-216">[C#]</span></span>         | <span data-ttu-id="6c7a4-217">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="6c7a4-217">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="6c7a4-218">ASP.NET Core boş</span><span class="sxs-lookup"><span data-stu-id="6c7a4-218">ASP.NET Core Empty</span></span>                           | `web`           | <span data-ttu-id="6c7a4-219">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="6c7a4-219">[C#], F#</span></span>     | <span data-ttu-id="6c7a4-220">Web veya boş</span><span class="sxs-lookup"><span data-stu-id="6c7a4-220">Web/Empty</span></span>                             |
| <span data-ttu-id="6c7a4-221">ASP.NET Core Web uygulaması (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="6c7a4-221">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`           | <span data-ttu-id="6c7a4-222">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="6c7a4-222">[C#], F#</span></span>     | <span data-ttu-id="6c7a4-223">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="6c7a4-223">Web/MVC</span></span>                               |
| <span data-ttu-id="6c7a4-224">ASP.NET Core Web uygulaması</span><span class="sxs-lookup"><span data-stu-id="6c7a4-224">ASP.NET Core Web App</span></span>                         | `razor`         | <span data-ttu-id="6c7a4-225">[C#]</span><span class="sxs-lookup"><span data-stu-id="6c7a4-225">[C#]</span></span>         | <span data-ttu-id="6c7a4-226">MVC/Web/Razor sayfaları</span><span class="sxs-lookup"><span data-stu-id="6c7a4-226">Web/MVC/Razor Pages</span></span>                   |
| <span data-ttu-id="6c7a4-227">Angular ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6c7a4-227">ASP.NET Core with Angular</span></span>                    | `angular`       | <span data-ttu-id="6c7a4-228">[C#]</span><span class="sxs-lookup"><span data-stu-id="6c7a4-228">[C#]</span></span>         | <span data-ttu-id="6c7a4-229">MVC/Web/SPA</span><span class="sxs-lookup"><span data-stu-id="6c7a4-229">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="6c7a4-230">React.js ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6c7a4-230">ASP.NET Core with React.js</span></span>                   | `react`         | <span data-ttu-id="6c7a4-231">[C#]</span><span class="sxs-lookup"><span data-stu-id="6c7a4-231">[C#]</span></span>         | <span data-ttu-id="6c7a4-232">MVC/Web/SPA</span><span class="sxs-lookup"><span data-stu-id="6c7a4-232">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="6c7a4-233">ASP.NET Core React.js ve Redux</span><span class="sxs-lookup"><span data-stu-id="6c7a4-233">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`    | <span data-ttu-id="6c7a4-234">[C#]</span><span class="sxs-lookup"><span data-stu-id="6c7a4-234">[C#]</span></span>         | <span data-ttu-id="6c7a4-235">MVC/Web/SPA</span><span class="sxs-lookup"><span data-stu-id="6c7a4-235">Web/MVC/SPA</span></span>                           | 
| <span data-ttu-id="6c7a4-236">Razor sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="6c7a4-236">Razor Class Library</span></span>                          | `razorclasslib` | <span data-ttu-id="6c7a4-237">[C#]</span><span class="sxs-lookup"><span data-stu-id="6c7a4-237">[C#]</span></span>         | <span data-ttu-id="6c7a4-238">Web/Razor/kitaplık/Razor sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="6c7a4-238">Web/Razor/Library/Razor Class Library</span></span> |
| <span data-ttu-id="6c7a4-239">ASP.NET Core Web API'si</span><span class="sxs-lookup"><span data-stu-id="6c7a4-239">ASP.NET Core Web API</span></span>                         | `webapi`        | <span data-ttu-id="6c7a4-240">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="6c7a4-240">[C#], F#</span></span>     | <span data-ttu-id="6c7a4-241">Web/Webapı</span><span class="sxs-lookup"><span data-stu-id="6c7a4-241">Web/WebAPI</span></span>                            |
| <span data-ttu-id="6c7a4-242">Global.JSON dosyasını</span><span class="sxs-lookup"><span data-stu-id="6c7a4-242">global.json file</span></span>                             | `globaljson`    |              | <span data-ttu-id="6c7a4-243">Config</span><span class="sxs-lookup"><span data-stu-id="6c7a4-243">Config</span></span>                                |
| <span data-ttu-id="6c7a4-244">NuGet Config</span><span class="sxs-lookup"><span data-stu-id="6c7a4-244">NuGet Config</span></span>                                 | `nugetconfig`   |              | <span data-ttu-id="6c7a4-245">Config</span><span class="sxs-lookup"><span data-stu-id="6c7a4-245">Config</span></span>                                |
| <span data-ttu-id="6c7a4-246">Web yapılandırması</span><span class="sxs-lookup"><span data-stu-id="6c7a4-246">Web Config</span></span>                                   | `webconfig`     |              | <span data-ttu-id="6c7a4-247">Config</span><span class="sxs-lookup"><span data-stu-id="6c7a4-247">Config</span></span>                                |
| <span data-ttu-id="6c7a4-248">Çözüm dosyası</span><span class="sxs-lookup"><span data-stu-id="6c7a4-248">Solution File</span></span>                                | `sln`           |              | <span data-ttu-id="6c7a4-249">Çözüm</span><span class="sxs-lookup"><span data-stu-id="6c7a4-249">Solution</span></span>                              |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="6c7a4-250">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="6c7a4-250">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="6c7a4-251">Komutu, şablonları, varsayılan listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-251">The command contains a default list of templates.</span></span> <span data-ttu-id="6c7a4-252">Kullanım `dotnet new -l` kullanılabilir şablonların listesini alamadı.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-252">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="6c7a4-253">Aşağıdaki tablo, .NET Core SDK 2.0.0 ile önceden yüklenmiş olarak gelen şablonları gösterir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-253">The following table shows the templates that come pre-installed with the .NET Core SDK 2.0.0.</span></span> <span data-ttu-id="6c7a4-254">Şablonunuz için varsayılan dili köşeli ayraçlar içinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-254">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="6c7a4-255">Şablonlar</span><span class="sxs-lookup"><span data-stu-id="6c7a4-255">Templates</span></span>                                    | <span data-ttu-id="6c7a4-256">Kısa Ad</span><span class="sxs-lookup"><span data-stu-id="6c7a4-256">Short Name</span></span>    | <span data-ttu-id="6c7a4-257">Dil</span><span class="sxs-lookup"><span data-stu-id="6c7a4-257">Language</span></span>     | <span data-ttu-id="6c7a4-258">Etiketler</span><span class="sxs-lookup"><span data-stu-id="6c7a4-258">Tags</span></span>                |
|----------------------------------------------|---------------|--------------|---------------------|
| <span data-ttu-id="6c7a4-259">Konsol Uygulaması</span><span class="sxs-lookup"><span data-stu-id="6c7a4-259">Console Application</span></span>                          | `console`     | <span data-ttu-id="6c7a4-260">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="6c7a4-260">[C#], F#, VB</span></span> | <span data-ttu-id="6c7a4-261">Ortak/Konsolu</span><span class="sxs-lookup"><span data-stu-id="6c7a4-261">Common/Console</span></span>      |
| <span data-ttu-id="6c7a4-262">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="6c7a4-262">Class library</span></span>                                | `classlib`    | <span data-ttu-id="6c7a4-263">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="6c7a4-263">[C#], F#, VB</span></span> | <span data-ttu-id="6c7a4-264">Ortak/Kitaplık</span><span class="sxs-lookup"><span data-stu-id="6c7a4-264">Common/Library</span></span>      |
| <span data-ttu-id="6c7a4-265">Unit Test Project</span><span class="sxs-lookup"><span data-stu-id="6c7a4-265">Unit Test Project</span></span>                            | `mstest`      | <span data-ttu-id="6c7a4-266">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="6c7a4-266">[C#], F#, VB</span></span> | <span data-ttu-id="6c7a4-267">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="6c7a4-267">Test/MSTest</span></span>         |
| <span data-ttu-id="6c7a4-268">xUnit Test projesi</span><span class="sxs-lookup"><span data-stu-id="6c7a4-268">xUnit Test Project</span></span>                           | `xunit`       | <span data-ttu-id="6c7a4-269">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="6c7a4-269">[C#], F#, VB</span></span> | <span data-ttu-id="6c7a4-270">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="6c7a4-270">Test/xUnit</span></span>          |
| <span data-ttu-id="6c7a4-271">ASP.NET Core boş</span><span class="sxs-lookup"><span data-stu-id="6c7a4-271">ASP.NET Core Empty</span></span>                           | `web`         | <span data-ttu-id="6c7a4-272">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="6c7a4-272">[C#], F#</span></span>     | <span data-ttu-id="6c7a4-273">Web veya boş</span><span class="sxs-lookup"><span data-stu-id="6c7a4-273">Web/Empty</span></span>           |
| <span data-ttu-id="6c7a4-274">ASP.NET Core Web uygulaması (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="6c7a4-274">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="6c7a4-275">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="6c7a4-275">[C#], F#</span></span>     | <span data-ttu-id="6c7a4-276">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="6c7a4-276">Web/MVC</span></span>             |
| <span data-ttu-id="6c7a4-277">ASP.NET Core Web uygulaması</span><span class="sxs-lookup"><span data-stu-id="6c7a4-277">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="6c7a4-278">[C#]</span><span class="sxs-lookup"><span data-stu-id="6c7a4-278">[C#]</span></span>         | <span data-ttu-id="6c7a4-279">MVC/Web/Razor sayfaları</span><span class="sxs-lookup"><span data-stu-id="6c7a4-279">Web/MVC/Razor Pages</span></span> |
| <span data-ttu-id="6c7a4-280">Angular ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6c7a4-280">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="6c7a4-281">[C#]</span><span class="sxs-lookup"><span data-stu-id="6c7a4-281">[C#]</span></span>         | <span data-ttu-id="6c7a4-282">MVC/Web/SPA</span><span class="sxs-lookup"><span data-stu-id="6c7a4-282">Web/MVC/SPA</span></span>         |
| <span data-ttu-id="6c7a4-283">React.js ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6c7a4-283">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="6c7a4-284">[C#]</span><span class="sxs-lookup"><span data-stu-id="6c7a4-284">[C#]</span></span>         | <span data-ttu-id="6c7a4-285">MVC/Web/SPA</span><span class="sxs-lookup"><span data-stu-id="6c7a4-285">Web/MVC/SPA</span></span>         |
| <span data-ttu-id="6c7a4-286">ASP.NET Core React.js ve Redux</span><span class="sxs-lookup"><span data-stu-id="6c7a4-286">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="6c7a4-287">[C#]</span><span class="sxs-lookup"><span data-stu-id="6c7a4-287">[C#]</span></span>         | <span data-ttu-id="6c7a4-288">MVC/Web/SPA</span><span class="sxs-lookup"><span data-stu-id="6c7a4-288">Web/MVC/SPA</span></span>         |
| <span data-ttu-id="6c7a4-289">ASP.NET Core Web API'si</span><span class="sxs-lookup"><span data-stu-id="6c7a4-289">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="6c7a4-290">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="6c7a4-290">[C#], F#</span></span>     | <span data-ttu-id="6c7a4-291">Web/Webapı</span><span class="sxs-lookup"><span data-stu-id="6c7a4-291">Web/WebAPI</span></span>          |
| <span data-ttu-id="6c7a4-292">Global.JSON dosyasını</span><span class="sxs-lookup"><span data-stu-id="6c7a4-292">global.json file</span></span>                             | `globaljson`  |              | <span data-ttu-id="6c7a4-293">Config</span><span class="sxs-lookup"><span data-stu-id="6c7a4-293">Config</span></span>              |
| <span data-ttu-id="6c7a4-294">Nuget yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6c7a4-294">Nuget Config</span></span>                                 | `nugetconfig` |              | <span data-ttu-id="6c7a4-295">Config</span><span class="sxs-lookup"><span data-stu-id="6c7a4-295">Config</span></span>              |
| <span data-ttu-id="6c7a4-296">Web yapılandırması</span><span class="sxs-lookup"><span data-stu-id="6c7a4-296">Web Config</span></span>                                   | `webconfig`   |              | <span data-ttu-id="6c7a4-297">Config</span><span class="sxs-lookup"><span data-stu-id="6c7a4-297">Config</span></span>              |
| <span data-ttu-id="6c7a4-298">Çözüm dosyası</span><span class="sxs-lookup"><span data-stu-id="6c7a4-298">Solution File</span></span>                                | `sln`         |              | <span data-ttu-id="6c7a4-299">Çözüm</span><span class="sxs-lookup"><span data-stu-id="6c7a4-299">Solution</span></span>            |
| <span data-ttu-id="6c7a4-300">Razor sayfası</span><span class="sxs-lookup"><span data-stu-id="6c7a4-300">Razor Page</span></span>                                   | `page`        |              | <span data-ttu-id="6c7a4-301">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="6c7a4-301">Web/ASP.NET</span></span>         |
| <span data-ttu-id="6c7a4-302">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="6c7a4-302">MVC ViewImports</span></span>                              | `viewimports` |              | <span data-ttu-id="6c7a4-303">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="6c7a4-303">Web/ASP.NET</span></span>         |
| <span data-ttu-id="6c7a4-304">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="6c7a4-304">MVC ViewStart</span></span>                                | `viewstart`   |              | <span data-ttu-id="6c7a4-305">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="6c7a4-305">Web/ASP.NET</span></span>         |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="6c7a4-306">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="6c7a4-306">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="6c7a4-307">Komutu, şablonları, varsayılan listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-307">The command contains a default list of templates.</span></span> <span data-ttu-id="6c7a4-308">Kullanım `dotnet new -all` kullanılabilir şablonların listesini alamadı.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-308">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="6c7a4-309">Aşağıdaki tablo, .NET Core SDK 1.0.1 önceden yüklenmiş olarak gelen şablonları gösterir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-309">The following table shows the templates that come pre-installed with the .NET Core SDK 1.0.1.</span></span> <span data-ttu-id="6c7a4-310">Şablonunuz için varsayılan dili köşeli ayraçlar içinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-310">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="6c7a4-311">Şablonlar</span><span class="sxs-lookup"><span data-stu-id="6c7a4-311">Templates</span></span>            | <span data-ttu-id="6c7a4-312">Kısa Ad</span><span class="sxs-lookup"><span data-stu-id="6c7a4-312">Short Name</span></span>    | <span data-ttu-id="6c7a4-313">Dil</span><span class="sxs-lookup"><span data-stu-id="6c7a4-313">Language</span></span> | <span data-ttu-id="6c7a4-314">Etiketler</span><span class="sxs-lookup"><span data-stu-id="6c7a4-314">Tags</span></span>           |
|----------------------|---------------|----------|----------------|
| <span data-ttu-id="6c7a4-315">Konsol Uygulaması</span><span class="sxs-lookup"><span data-stu-id="6c7a4-315">Console Application</span></span>  | `console`     | <span data-ttu-id="6c7a4-316">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="6c7a4-316">[C#], F#</span></span> | <span data-ttu-id="6c7a4-317">Ortak/Konsolu</span><span class="sxs-lookup"><span data-stu-id="6c7a4-317">Common/Console</span></span> |
| <span data-ttu-id="6c7a4-318">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="6c7a4-318">Class library</span></span>        | `classlib`    | <span data-ttu-id="6c7a4-319">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="6c7a4-319">[C#], F#</span></span> | <span data-ttu-id="6c7a4-320">Ortak/Kitaplık</span><span class="sxs-lookup"><span data-stu-id="6c7a4-320">Common/Library</span></span> |
| <span data-ttu-id="6c7a4-321">Unit Test Project</span><span class="sxs-lookup"><span data-stu-id="6c7a4-321">Unit Test Project</span></span>    | `mstest`      | <span data-ttu-id="6c7a4-322">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="6c7a4-322">[C#], F#</span></span> | <span data-ttu-id="6c7a4-323">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="6c7a4-323">Test/MSTest</span></span>    |
| <span data-ttu-id="6c7a4-324">xUnit Test projesi</span><span class="sxs-lookup"><span data-stu-id="6c7a4-324">xUnit Test Project</span></span>   | `xunit`       | <span data-ttu-id="6c7a4-325">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="6c7a4-325">[C#], F#</span></span> | <span data-ttu-id="6c7a4-326">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="6c7a4-326">Test/xUnit</span></span>     |
| <span data-ttu-id="6c7a4-327">ASP.NET Core boş</span><span class="sxs-lookup"><span data-stu-id="6c7a4-327">ASP.NET Core Empty</span></span>   | `web`         | <span data-ttu-id="6c7a4-328">[C#]</span><span class="sxs-lookup"><span data-stu-id="6c7a4-328">[C#]</span></span>     | <span data-ttu-id="6c7a4-329">Web veya boş</span><span class="sxs-lookup"><span data-stu-id="6c7a4-329">Web/Empty</span></span>      |
| <span data-ttu-id="6c7a4-330">ASP.NET Core Web uygulaması</span><span class="sxs-lookup"><span data-stu-id="6c7a4-330">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="6c7a4-331">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="6c7a4-331">[C#], F#</span></span> | <span data-ttu-id="6c7a4-332">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="6c7a4-332">Web/MVC</span></span>        |
| <span data-ttu-id="6c7a4-333">ASP.NET Core Web API'si</span><span class="sxs-lookup"><span data-stu-id="6c7a4-333">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="6c7a4-334">[C#]</span><span class="sxs-lookup"><span data-stu-id="6c7a4-334">[C#]</span></span>     | <span data-ttu-id="6c7a4-335">Web/Webapı</span><span class="sxs-lookup"><span data-stu-id="6c7a4-335">Web/WebAPI</span></span>     |
| <span data-ttu-id="6c7a4-336">Nuget yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6c7a4-336">Nuget Config</span></span>         | `nugetconfig` |          | <span data-ttu-id="6c7a4-337">Config</span><span class="sxs-lookup"><span data-stu-id="6c7a4-337">Config</span></span>         |
| <span data-ttu-id="6c7a4-338">Web yapılandırması</span><span class="sxs-lookup"><span data-stu-id="6c7a4-338">Web Config</span></span>           | `webconfig`   |          | <span data-ttu-id="6c7a4-339">Config</span><span class="sxs-lookup"><span data-stu-id="6c7a4-339">Config</span></span>         |
| <span data-ttu-id="6c7a4-340">Çözüm dosyası</span><span class="sxs-lookup"><span data-stu-id="6c7a4-340">Solution File</span></span>        | `sln`         |          | <span data-ttu-id="6c7a4-341">Çözüm</span><span class="sxs-lookup"><span data-stu-id="6c7a4-341">Solution</span></span>       |

---

## <a name="options"></a><span data-ttu-id="6c7a4-342">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="6c7a4-342">Options</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="6c7a4-343">.NET core 2.2</span><span class="sxs-lookup"><span data-stu-id="6c7a4-343">.NET Core 2.2</span></span>](#tab/netcore22)

`--dry-run`

<span data-ttu-id="6c7a4-344">Verilen komutu bir şablonu oluşturmaya neden olacaksa çalıştırırsanız ne olacağını bir özeti görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-344">Displays a summary of what would happen if the given command were run if it would result in a template creation.</span></span>

`--force`

<span data-ttu-id="6c7a4-345">Mevcut dosyaları değiştirmek olsa bile oluşturulması gereken içeriği zorlar.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-345">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="6c7a4-346">Bir proje çıkış dizinine içerdiğinde, bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-346">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="6c7a4-347">Komut için Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-347">Prints out help for the command.</span></span> <span data-ttu-id="6c7a4-348">İçin çağrılabilir `dotnet new` kendisini komutu veya herhangi bir şablon gibi `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-348">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="6c7a4-349">Bir kaynak veya şablon paketinden yükler `PATH` veya `NUGET_ID` sağlanan.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-349">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="6c7a4-350">Bir şablon Paketi yayım öncesi bir sürümü yüklemek istediğiniz sürümü biçiminde belirtmek gerekirse `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-350">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="6c7a4-351">Varsayılan olarak, `dotnet new` geçirir \* sürümünü temsil eden en son kararlı Paket sürümü.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-351">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="6c7a4-352">Bir örneğe bakın [örnekler](#examples) bölümü.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-352">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="6c7a4-353">Özel şablonlar oluşturma hakkında daha fazla bilgi için bkz. [yeni dotnet için özel şablonları](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="6c7a4-353">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="6c7a4-354">Belirtilen ad içeren şablonlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-354">Lists templates containing the specified name.</span></span> <span data-ttu-id="6c7a4-355">İçin çağırdıysanız `dotnet new` komut, belirtilen dizinde kullanılabilir olası şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-355">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="6c7a4-356">Örnek dizin zaten bir proje içeriyorsa, tüm proje şablonları listesinde değil.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-356">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="6c7a4-357">Oluşturmak için şablon dili.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-357">The language of the template to create.</span></span> <span data-ttu-id="6c7a4-358">Dil kabul şablon tarafından farklılık gösterir (varsayılan ayarlarında bkz [bağımsız değişkenleri](#arguments) bölümü).</span><span class="sxs-lookup"><span data-stu-id="6c7a4-358">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="6c7a4-359">Bazı şablonlar için geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-359">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="6c7a4-360">Bazı Kabukları yorumlama `#` olarak bir özel karakter.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-360">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="6c7a4-361">Bu gibi durumlarda, dil parametre değeri, aşağıdaki gibi alın gerek `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-361">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="6c7a4-362">Oluşturulan çıktı adı.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-362">The name for the created output.</span></span> <span data-ttu-id="6c7a4-363">Hiçbir ad belirtilmediği takdirde, geçerli dizin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-363">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="6c7a4-364">Yükleme sırasında kullanılacak bir NuGet kaynağı belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-364">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="6c7a4-365">Oluşturulan çıktı yerleştirileceği konumu.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-365">Location to place the generated output.</span></span> <span data-ttu-id="6c7a4-366">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-366">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="6c7a4-367">Şablonları kullanılabilir türlerine göre filtreler.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-367">Filters templates based on available types.</span></span> <span data-ttu-id="6c7a4-368">Önceden tanımlanmış değerler şunlardır: "proje", "Item" veya "diğer".</span><span class="sxs-lookup"><span data-stu-id="6c7a4-368">Predefined values are "project", "item", or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="6c7a4-369">Bir kaynak veya şablon paketini kaldırır `PATH` veya `NUGET_ID` sağlanan.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-369">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="6c7a4-370">Dışlarken `<PATH|NUGET_ID>` değer, tüm yüklü şablon paketleri ve bunların ilişkili şablonları görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-370">When excluding the `<PATH|NUGET_ID>` value, all currently installed template packs and their associated templates are displayed.</span></span>

> [!NOTE]
> <span data-ttu-id="6c7a4-371">Bir şablon kullanarak kaldırmak için bir `PATH`, yol tam olarak nitelemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-371">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="6c7a4-372">Örneğin, *C:/Users/\<kullanıcı > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* çalışır, ancak *./GarciaSoftware.ConsoleTemplate.CSharp* içeren gelen Klasör erişemez.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-372">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="6c7a4-373">Ayrıca, şablonu yoldaki son Sonlandırıcı directory eğik çizgi içermez.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-373">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="6c7a4-374">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="6c7a4-374">.NET Core 2.1</span></span>](#tab/netcore21)

`--force`

<span data-ttu-id="6c7a4-375">Mevcut dosyaları değiştirmek olsa bile oluşturulması gereken içeriği zorlar.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-375">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="6c7a4-376">Bir proje çıkış dizinine içerdiğinde, bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-376">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="6c7a4-377">Komut için Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-377">Prints out help for the command.</span></span> <span data-ttu-id="6c7a4-378">İçin çağrılabilir `dotnet new` kendisini komutu veya herhangi bir şablon gibi `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-378">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="6c7a4-379">Bir kaynak veya şablon paketinden yükler `PATH` veya `NUGET_ID` sağlanan.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-379">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="6c7a4-380">Bir şablon Paketi yayım öncesi bir sürümü yüklemek istediğiniz sürümü biçiminde belirtmek gerekirse `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-380">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="6c7a4-381">Varsayılan olarak, `dotnet new` geçirir \* sürümünü temsil eden en son kararlı Paket sürümü.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-381">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="6c7a4-382">Bir örneğe bakın [örnekler](#examples) bölümü.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-382">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="6c7a4-383">Özel şablonlar oluşturma hakkında daha fazla bilgi için bkz. [yeni dotnet için özel şablonları](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="6c7a4-383">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="6c7a4-384">Belirtilen ad içeren şablonlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-384">Lists templates containing the specified name.</span></span> <span data-ttu-id="6c7a4-385">İçin çağırdıysanız `dotnet new` komut, belirtilen dizinde kullanılabilir olası şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-385">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="6c7a4-386">Örnek dizin zaten bir proje içeriyorsa, tüm proje şablonları listesinde değil.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-386">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="6c7a4-387">Oluşturmak için şablon dili.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-387">The language of the template to create.</span></span> <span data-ttu-id="6c7a4-388">Dil kabul şablon tarafından farklılık gösterir (varsayılan ayarlarında bkz [bağımsız değişkenleri](#arguments) bölümü).</span><span class="sxs-lookup"><span data-stu-id="6c7a4-388">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="6c7a4-389">Bazı şablonlar için geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-389">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="6c7a4-390">Bazı Kabukları yorumlama `#` olarak bir özel karakter.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-390">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="6c7a4-391">Bu gibi durumlarda, dil parametre değeri, aşağıdaki gibi alın gerek `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-391">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="6c7a4-392">Oluşturulan çıktı adı.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-392">The name for the created output.</span></span> <span data-ttu-id="6c7a4-393">Hiçbir ad belirtilmediği takdirde, geçerli dizin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-393">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="6c7a4-394">Yükleme sırasında kullanılacak bir NuGet kaynağı belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-394">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="6c7a4-395">Oluşturulan çıktı yerleştirileceği konumu.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-395">Location to place the generated output.</span></span> <span data-ttu-id="6c7a4-396">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-396">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="6c7a4-397">Şablonları kullanılabilir türlerine göre filtreler.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-397">Filters templates based on available types.</span></span> <span data-ttu-id="6c7a4-398">Önceden tanımlanmış değerler şunlardır: "proje", "Item" veya "diğer".</span><span class="sxs-lookup"><span data-stu-id="6c7a4-398">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="6c7a4-399">Bir kaynak veya şablon paketini kaldırır `PATH` veya `NUGET_ID` sağlanan.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-399">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="6c7a4-400">Bir şablon kullanarak kaldırmak için bir `PATH`, yol tam olarak nitelemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-400">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="6c7a4-401">Örneğin, *C:/Users/\<kullanıcı > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* çalışır, ancak *./GarciaSoftware.ConsoleTemplate.CSharp* içeren gelen Klasör erişemez.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-401">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="6c7a4-402">Ayrıca, şablonu yoldaki son Sonlandırıcı directory eğik çizgi içermez.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-402">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="6c7a4-403">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="6c7a4-403">.NET Core 2.0</span></span>](#tab/netcore20)

`--force`

<span data-ttu-id="6c7a4-404">Mevcut dosyaları değiştirmek olsa bile oluşturulması gereken içeriği zorlar.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-404">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="6c7a4-405">Bir proje çıkış dizinine içerdiğinde, bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-405">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="6c7a4-406">Komut için Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-406">Prints out help for the command.</span></span> <span data-ttu-id="6c7a4-407">İçin çağrılabilir `dotnet new` kendisini komutu veya herhangi bir şablon gibi `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-407">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="6c7a4-408">Bir kaynak veya şablon paketinden yükler `PATH` veya `NUGET_ID` sağlanan.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-408">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="6c7a4-409">Bir şablon Paketi yayım öncesi bir sürümü yüklemek istediğiniz sürümü biçiminde belirtmek gerekirse `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-409">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="6c7a4-410">Varsayılan olarak, `dotnet new` geçirir \* sürümünü temsil eden en son kararlı Paket sürümü.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-410">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="6c7a4-411">Bir örneğe bakın [örnekler](#examples) bölümü.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-411">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="6c7a4-412">Özel şablonlar oluşturma hakkında daha fazla bilgi için bkz. [yeni dotnet için özel şablonları](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="6c7a4-412">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="6c7a4-413">Belirtilen ad içeren şablonlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-413">Lists templates containing the specified name.</span></span> <span data-ttu-id="6c7a4-414">İçin çağırdıysanız `dotnet new` komut, belirtilen dizinde kullanılabilir olası şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-414">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="6c7a4-415">Örnek dizin zaten bir proje içeriyorsa, tüm proje şablonları listesinde değil.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-415">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="6c7a4-416">Oluşturmak için şablon dili.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-416">The language of the template to create.</span></span> <span data-ttu-id="6c7a4-417">Dil kabul şablon tarafından farklılık gösterir (varsayılan ayarlarında bkz [bağımsız değişkenleri](#arguments) bölümü).</span><span class="sxs-lookup"><span data-stu-id="6c7a4-417">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="6c7a4-418">Bazı şablonlar için geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-418">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="6c7a4-419">Bazı Kabukları yorumlama `#` olarak bir özel karakter.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-419">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="6c7a4-420">Bu gibi durumlarda, dil parametre değeri, aşağıdaki gibi alın gerek `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-420">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="6c7a4-421">Oluşturulan çıktı adı.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-421">The name for the created output.</span></span> <span data-ttu-id="6c7a4-422">Hiçbir ad belirtilmediği takdirde, geçerli dizin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-422">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="6c7a4-423">Oluşturulan çıktı yerleştirileceği konumu.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-423">Location to place the generated output.</span></span> <span data-ttu-id="6c7a4-424">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-424">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="6c7a4-425">Şablonları kullanılabilir türlerine göre filtreler.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-425">Filters templates based on available types.</span></span> <span data-ttu-id="6c7a4-426">Önceden tanımlanmış değerler şunlardır: "proje", "Item" veya "diğer".</span><span class="sxs-lookup"><span data-stu-id="6c7a4-426">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="6c7a4-427">Bir kaynak veya şablon paketini kaldırır `PATH` veya `NUGET_ID` sağlanan.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-427">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="6c7a4-428">Bir kaynağı kullanan bir şablonu kaldırmak için `PATH`, yol tam olarak nitelemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-428">To uninstall a template using a source `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="6c7a4-429">Örneğin, *C:/Users/\<kullanıcı > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* çalışır, ancak *./GarciaSoftware.ConsoleTemplate.CSharp* içeren gelen Klasör erişemez.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-429">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span> <span data-ttu-id="6c7a4-430">Ayrıca, şablonu yoldaki son Sonlandırıcı directory eğik çizgi içermez.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-430">Additionally, do not include a final terminating directory slash on your template path.</span></span>
> 
> <span data-ttu-id="6c7a4-431">Belirlemek erişemiyorsanız `PATH` veya `NUGET_ID` çalıştıran, bir şablonu kaldırmak için gerekli bağımsız değişken `dotnet new --uninstall` bağımsız değişken yüklü tüm şablonları ve bunları kaldırmak için gerekli bağımsız değişken listesi olmayan.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-431">If you are unable to determine the `PATH` or `NUGET_ID` argument needed to uninstall a template, running `dotnet new --uninstall` without an argument will list all installed templates and the argument required to uninstall them.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="6c7a4-432">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="6c7a4-432">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="6c7a4-433">Belirli türde bir proje için tüm şablonları'nı bağlamında çalıştırılırken gösterir `dotnet new` tek başına komutu.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-433">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="6c7a4-434">Belirli bir şablon bağlamında gibi çalıştırırken `dotnet new web -all`, `-all` zorla oluşturma bayrak olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-434">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="6c7a4-435">Bir proje çıkış dizinine içerdiğinde, bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-435">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="6c7a4-436">Komut için Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-436">Prints out help for the command.</span></span> <span data-ttu-id="6c7a4-437">İçin çağrılabilir `dotnet new` kendisini komutu veya herhangi bir şablon gibi `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-437">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="6c7a4-438">Belirtilen ad içeren şablonlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-438">Lists templates containing the specified name.</span></span> <span data-ttu-id="6c7a4-439">İçin çağırdıysanız `dotnet new` komut, belirtilen dizinde kullanılabilir olası şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-439">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="6c7a4-440">Örnek dizin zaten bir proje içeriyorsa, tüm proje şablonları listesinde değil.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-440">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="6c7a4-441">Oluşturmak için şablon dili.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-441">The language of the template to create.</span></span> <span data-ttu-id="6c7a4-442">Dil kabul şablon tarafından farklılık gösterir (varsayılan ayarlarında bkz [bağımsız değişkenleri](#arguments) bölümü).</span><span class="sxs-lookup"><span data-stu-id="6c7a4-442">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="6c7a4-443">Bazı şablonlar için geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-443">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="6c7a4-444">Bazı Kabukları yorumlama `#` olarak bir özel karakter.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-444">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="6c7a4-445">Bu gibi durumlarda, dil parametre değeri, aşağıdaki gibi alın gerek `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-445">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="6c7a4-446">Oluşturulan çıktı adı.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-446">The name for the created output.</span></span> <span data-ttu-id="6c7a4-447">Hiçbir ad belirtilmediği takdirde, geçerli dizin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-447">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="6c7a4-448">Oluşturulan çıktı yerleştirileceği konumu.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-448">Location to place the generated output.</span></span> <span data-ttu-id="6c7a4-449">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-449">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="6c7a4-450">Şablon seçenekleri</span><span class="sxs-lookup"><span data-stu-id="6c7a4-450">Template options</span></span>

<span data-ttu-id="6c7a4-451">Her proje şablonu, ek seçenekler kullanılabilir olabilir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-451">Each project template may have additional options available.</span></span> <span data-ttu-id="6c7a4-452">Çekirdek şablonları aşağıdaki ek seçeneklere sahip olursunuz:</span><span class="sxs-lookup"><span data-stu-id="6c7a4-452">The core templates have the following additional options:</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="6c7a4-453">.NET core 2.2</span><span class="sxs-lookup"><span data-stu-id="6c7a4-453">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="6c7a4-454">**Konsolu**</span><span class="sxs-lookup"><span data-stu-id="6c7a4-454">**console**</span></span>

<span data-ttu-id="6c7a4-455">`--langVersion <VERSION_NUMBER>` -Ayarlar `LangVersion` oluşturulan proje dosyasındaki özellik.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-455">`--langVersion <VERSION_NUMBER>` - Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="6c7a4-456">Örneğin, `--langVersion 7.3` kullanılacak C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-456">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="6c7a4-457">Desteklenen değil F#.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-457">Not supported for F#.</span></span>

<span data-ttu-id="6c7a4-458">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-458">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6c7a4-459">**angular, react, açarken kilitlenmesi**</span><span class="sxs-lookup"><span data-stu-id="6c7a4-459">**angular, react, reactredux**</span></span>

<span data-ttu-id="6c7a4-460">`--exclude-launch-settings` -Hariç *launchSettings.json* oluşturulan şablonundan.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-460">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="6c7a4-461">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-461">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6c7a4-462">`--no-https` -Proje HTTPS'yi gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-462">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="6c7a4-463">Bu seçenek yalnızca geçerlidir `IndividualAuth` veya `OrganizationalAuth` kullanılmayan.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-463">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="6c7a4-464">**razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="6c7a4-464">**razorclasslib**</span></span>

<span data-ttu-id="6c7a4-465">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-465">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6c7a4-466">**classlib**</span><span class="sxs-lookup"><span data-stu-id="6c7a4-466">**classlib**</span></span>

<span data-ttu-id="6c7a4-467">`-f|--framework <FRAMEWORK>` -Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-467">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="6c7a4-468">Değerler: `netcoreapp2.2` bir .NET Core sınıf kitaplığı oluşturmak için veya `netstandard2.0` .NET standart sınıf kitaplığı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-468">Values: `netcoreapp2.2` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="6c7a4-469">Varsayılan değer `netstandard2.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-469">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="6c7a4-470">`--langVersion <VERSION_NUMBER>` -Ayarlar `LangVersion` oluşturulan proje dosyasındaki özellik.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-470">`--langVersion <VERSION_NUMBER>` - Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="6c7a4-471">Örneğin, `--langVersion 7.3` kullanılacak C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-471">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="6c7a4-472">Desteklenen değil F#.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-472">Not supported for F#.</span></span>

<span data-ttu-id="6c7a4-473">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-473">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6c7a4-474">**MSTest, xunit**</span><span class="sxs-lookup"><span data-stu-id="6c7a4-474">**mstest, xunit**</span></span>

<span data-ttu-id="6c7a4-475">`-p|--enable-pack` -Etkinleştirir kullanarak projeyi için paketleme [dotnet paketi](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="6c7a4-475">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="6c7a4-476">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-476">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6c7a4-477">**nunit**</span><span class="sxs-lookup"><span data-stu-id="6c7a4-477">**nunit**</span></span>

<span data-ttu-id="6c7a4-478">`-f|--framework <FRAMEWORK>` -Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-478">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="6c7a4-479">Varsayılan değer `netcoreapp2.1` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-479">The default value is `netcoreapp2.1`.</span></span>

<span data-ttu-id="6c7a4-480">`-p|--enable-pack` -Etkinleştirir kullanarak projeyi için paketleme [dotnet paketi](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="6c7a4-480">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="6c7a4-481">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-481">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6c7a4-482">**Sayfa**</span><span class="sxs-lookup"><span data-stu-id="6c7a4-482">**page**</span></span>

<span data-ttu-id="6c7a4-483">`-na|--namespace <NAMESPACE_NAME>` -Namespace üretilen kod için.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-483">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="6c7a4-484">Varsayılan değer `MyApp.Namespace` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-484">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="6c7a4-485">`-np|--no-pagemodel` -Bir PageModel olmadan sayfası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-485">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="6c7a4-486">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="6c7a4-486">**viewimports**</span></span>

<span data-ttu-id="6c7a4-487">`-na|--namespace <NAMESPACE_NAME>` -Namespace üretilen kod için.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-487">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="6c7a4-488">Varsayılan değer `MyApp.Namespace` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-488">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="6c7a4-489">**Web**</span><span class="sxs-lookup"><span data-stu-id="6c7a4-489">**web**</span></span>

<span data-ttu-id="6c7a4-490">`--exclude-launch-settings` -Hariç *launchSettings.json* oluşturulan şablonundan.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-490">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="6c7a4-491">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-491">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6c7a4-492">`--no-https` -Proje HTTPS'yi gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-492">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="6c7a4-493">Bu seçenek yalnızca geçerlidir `IndividualAuth` veya `OrganizationalAuth` kullanılmayan.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-493">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="6c7a4-494">**MVC, webapp**</span><span class="sxs-lookup"><span data-stu-id="6c7a4-494">**mvc, webapp**</span></span>

<span data-ttu-id="6c7a4-495">`-au|--auth <AUTHENTICATION_TYPE>` -Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-495">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="6c7a4-496">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="6c7a4-496">The possible values are:</span></span>

- <span data-ttu-id="6c7a4-497">`None` -Kimlik doğrulama yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="6c7a4-497">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="6c7a4-498">`Individual` -Tek tek kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-498">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="6c7a4-499">`IndividualB2C` -Azure AD B2C ile kimlik doğrulaması tek tek.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-499">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="6c7a4-500">`SingleOrg` -Kuruluş kimlik doğrulaması için tek bir kiracı.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-500">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="6c7a4-501">`MultiOrg` -Birden fazla Kiracı için Kurumsal kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-501">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="6c7a4-502">`Windows` -Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-502">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="6c7a4-503">`--aad-b2c-instance <INSTANCE>` -Bağlanmak için Azure Active Directory B2C örnek.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-503">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="6c7a4-504">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-504">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="6c7a4-505">Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-505">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="6c7a4-506">`-ssp|--susi-policy-id <ID>` -Bu proje için oturum açma ve kaydolma ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-506">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="6c7a4-507">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-507">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6c7a4-508">`-rp|--reset-password-policy-id <ID>` -Bu proje için reset parola ilkesi kimliği.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-508">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="6c7a4-509">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-509">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6c7a4-510">`-ep|--edit-profile-policy-id <ID>` -Bu proje için düzenleme profili ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-510">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="6c7a4-511">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-511">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6c7a4-512">`--aad-instance <INSTANCE>` -Bağlanmak için Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-512">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="6c7a4-513">İle kullanma `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-513">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="6c7a4-514">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-514">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="6c7a4-515">`--client-id <ID>` -Bu proje için istemci kimliği.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-515">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="6c7a4-516">İle kullanma `IndividualB2C`, `SingleOrg`, veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-516">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="6c7a4-517">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-517">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="6c7a4-518">`--domain <DOMAIN>` -Dizin kiracısı için etki alanı.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-518">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="6c7a4-519">İle kullanma `SingleOrg` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-519">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="6c7a4-520">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-520">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="6c7a4-521">`--tenant-id <ID>` -Tenantıd bağlanmak için kimliği dizini.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-521">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="6c7a4-522">İle kullanma `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-522">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="6c7a4-523">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-523">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="6c7a4-524">`--callback-path <PATH>` -Yeniden yönlendirme URI'si uygulamanın taban yolu içindeki istek yolu.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-524">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="6c7a4-525">İle kullanma `SingleOrg` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-525">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="6c7a4-526">Varsayılan değer `/signin-oidc` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-526">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="6c7a4-527">`-r|--org-read-access` -Bu uygulamanın dizine okuma erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-527">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="6c7a4-528">Yalnızca uygulandığı `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-528">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="6c7a4-529">`--exclude-launch-settings` -Hariç *launchSettings.json* oluşturulan şablonundan.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-529">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="6c7a4-530">`--no-https` -Proje HTTPS'yi gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-530">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="6c7a4-531">`app.UseHsts` ve `app.UseHttpsRedirection` için eklenmez `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-531">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="6c7a4-532">Bu seçenek yalnızca geçerlidir `Individual`, `IndividualB2C`, `SingleOrg`, veya `MultiOrg` kullanılmayan.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-532">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="6c7a4-533">`-uld|--use-local-db` -LocalDB yerine SQLite kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-533">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="6c7a4-534">Yalnızca uygulandığı `Individual` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-534">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6c7a4-535">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-535">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6c7a4-536">**webapı**</span><span class="sxs-lookup"><span data-stu-id="6c7a4-536">**webapi**</span></span>

<span data-ttu-id="6c7a4-537">`-au|--auth <AUTHENTICATION_TYPE>` -Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-537">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="6c7a4-538">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="6c7a4-538">The possible values are:</span></span>

- <span data-ttu-id="6c7a4-539">`None` -Kimlik doğrulama yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="6c7a4-539">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="6c7a4-540">`IndividualB2C` -Azure AD B2C ile kimlik doğrulaması tek tek.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-540">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="6c7a4-541">`SingleOrg` -Kuruluş kimlik doğrulaması için tek bir kiracı.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-541">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="6c7a4-542">`Windows` -Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-542">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="6c7a4-543">`--aad-b2c-instance <INSTANCE>` -Bağlanmak için Azure Active Directory B2C örnek.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-543">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="6c7a4-544">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-544">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="6c7a4-545">Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-545">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="6c7a4-546">`-ssp|--susi-policy-id <ID>` -Bu proje için oturum açma ve kaydolma ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-546">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="6c7a4-547">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-547">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6c7a4-548">`--aad-instance <INSTANCE>` -Bağlanmak için Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-548">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="6c7a4-549">İle kullanma `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-549">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="6c7a4-550">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-550">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="6c7a4-551">`--client-id <ID>` -Bu proje için istemci kimliği.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-551">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="6c7a4-552">İle kullanma `IndividualB2C` veya `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-552">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="6c7a4-553">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-553">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="6c7a4-554">`--domain <DOMAIN>` -Dizin kiracısı için etki alanı.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-554">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="6c7a4-555">İle kullanma `SingleOrg` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-555">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="6c7a4-556">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-556">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="6c7a4-557">`--tenant-id <ID>` -Tenantıd bağlanmak için kimliği dizini.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-557">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="6c7a4-558">İle kullanma `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-558">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="6c7a4-559">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-559">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="6c7a4-560">`-r|--org-read-access` -Bu uygulamanın dizine okuma erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-560">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="6c7a4-561">Yalnızca uygulandığı `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-561">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="6c7a4-562">`--exclude-launch-settings` -Hariç *launchSettings.json* oluşturulan şablonundan.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-562">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="6c7a4-563">`--no-https` -Proje HTTPS'yi gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-563">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="6c7a4-564">`app.UseHsts` ve `app.UseHttpsRedirection` için eklenmez `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-564">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="6c7a4-565">Bu seçenek yalnızca geçerlidir `Individual`, `IndividualB2C`, `SingleOrg`, veya `MultiOrg` kullanılmayan.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-565">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="6c7a4-566">`-uld|--use-local-db` -LocalDB yerine SQLite kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-566">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="6c7a4-567">Yalnızca uygulandığı `Individual` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-567">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6c7a4-568">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-568">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6c7a4-569">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="6c7a4-569">**globaljson**</span></span>

<span data-ttu-id="6c7a4-570">`--sdk-version <VERSION_NUMBER>` -Kullanmak için .NET Core SDK'sı sürümünü belirtir *global.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-570">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="6c7a4-571">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="6c7a4-571">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="6c7a4-572">**konsolunda, angular, react, açarken kilitlenmesi, razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="6c7a4-572">**console, angular, react, reactredux, razorclasslib**</span></span>

<span data-ttu-id="6c7a4-573">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-573">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6c7a4-574">**classlib**</span><span class="sxs-lookup"><span data-stu-id="6c7a4-574">**classlib**</span></span>

<span data-ttu-id="6c7a4-575">`-f|--framework <FRAMEWORK>` -Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-575">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="6c7a4-576">Değerler: `netcoreapp2.1` bir .NET Core sınıf kitaplığı oluşturmak için veya `netstandard2.0` .NET standart sınıf kitaplığı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-576">Values: `netcoreapp2.1` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="6c7a4-577">Varsayılan değer `netstandard2.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-577">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="6c7a4-578">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-578">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6c7a4-579">**MSTest, xunit**</span><span class="sxs-lookup"><span data-stu-id="6c7a4-579">**mstest, xunit**</span></span>

<span data-ttu-id="6c7a4-580">`-p|--enable-pack` -Etkinleştirir kullanarak projeyi için paketleme [dotnet paketi](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="6c7a4-580">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="6c7a4-581">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-581">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6c7a4-582">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="6c7a4-582">**globaljson**</span></span>

<span data-ttu-id="6c7a4-583">`--sdk-version <VERSION_NUMBER>` -Kullanmak için .NET Core SDK'sı sürümünü belirtir *global.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-583">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="6c7a4-584">**Web**</span><span class="sxs-lookup"><span data-stu-id="6c7a4-584">**web**</span></span>

<span data-ttu-id="6c7a4-585">`--exclude-launch-settings` -Hariç *launchSettings.json* oluşturulan şablonundan.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-585">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="6c7a4-586">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-586">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6c7a4-587">`--no-https` -Proje HTTPS'yi gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-587">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="6c7a4-588">Bu seçenek yalnızca geçerlidir `IndividualAuth` veya `OrganizationalAuth` kullanılmayan.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-588">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="6c7a4-589">**webapı**</span><span class="sxs-lookup"><span data-stu-id="6c7a4-589">**webapi**</span></span>

<span data-ttu-id="6c7a4-590">`-au|--auth <AUTHENTICATION_TYPE>` -Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-590">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="6c7a4-591">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="6c7a4-591">The possible values are:</span></span>

- <span data-ttu-id="6c7a4-592">`None` -Kimlik doğrulama yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="6c7a4-592">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="6c7a4-593">`IndividualB2C` -Azure AD B2C ile kimlik doğrulaması tek tek.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-593">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="6c7a4-594">`SingleOrg` -Kuruluş kimlik doğrulaması için tek bir kiracı.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-594">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="6c7a4-595">`Windows` -Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-595">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="6c7a4-596">`--aad-b2c-instance <INSTANCE>` -Bağlanmak için Azure Active Directory B2C örnek.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-596">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="6c7a4-597">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-597">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="6c7a4-598">Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-598">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="6c7a4-599">`-ssp|--susi-policy-id <ID>` -Bu proje için oturum açma ve kaydolma ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-599">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="6c7a4-600">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-600">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6c7a4-601">`--aad-instance <INSTANCE>` -Bağlanmak için Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-601">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="6c7a4-602">İle kullanma `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-602">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="6c7a4-603">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-603">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="6c7a4-604">`--client-id <ID>` -Bu proje için istemci kimliği.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-604">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="6c7a4-605">İle kullanma `IndividualB2C` veya `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-605">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="6c7a4-606">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-606">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="6c7a4-607">`--domain <DOMAIN>` -Dizin kiracısı için etki alanı.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-607">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="6c7a4-608">İle kullanma `SingleOrg` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-608">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="6c7a4-609">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-609">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="6c7a4-610">`--tenant-id <ID>` -Tenantıd bağlanmak için kimliği dizini.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-610">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="6c7a4-611">İle kullanma `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-611">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="6c7a4-612">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-612">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="6c7a4-613">`-r|--org-read-access` -Bu uygulamanın dizine okuma erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-613">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="6c7a4-614">Yalnızca uygulandığı `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-614">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="6c7a4-615">`--exclude-launch-settings` -Hariç *launchSettings.json* oluşturulan şablonundan.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-615">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="6c7a4-616">`-uld|--use-local-db` -LocalDB yerine SQLite kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-616">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="6c7a4-617">Yalnızca uygulandığı `Individual` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-617">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6c7a4-618">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-618">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6c7a4-619">`--no-https` -Proje HTTPS'yi gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-619">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="6c7a4-620">`app.UseHsts` ve `app.UseHttpsRedirection` için eklenmez `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-620">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="6c7a4-621">Bu seçenek yalnızca geçerlidir `Individual`, `IndividualB2C`, `SingleOrg`, veya `MultiOrg` kullanılmayan.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-621">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="6c7a4-622">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="6c7a4-622">**mvc, razor**</span></span>

<span data-ttu-id="6c7a4-623">`-au|--auth <AUTHENTICATION_TYPE>` -Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-623">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="6c7a4-624">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="6c7a4-624">The possible values are:</span></span>

- <span data-ttu-id="6c7a4-625">`None` -Kimlik doğrulama yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="6c7a4-625">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="6c7a4-626">`Individual` -Tek tek kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-626">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="6c7a4-627">`IndividualB2C` -Azure AD B2C ile kimlik doğrulaması tek tek.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-627">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="6c7a4-628">`SingleOrg` -Kuruluş kimlik doğrulaması için tek bir kiracı.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-628">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="6c7a4-629">`MultiOrg` -Birden fazla Kiracı için Kurumsal kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-629">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="6c7a4-630">`Windows` -Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-630">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="6c7a4-631">`--aad-b2c-instance <INSTANCE>` -Bağlanmak için Azure Active Directory B2C örnek.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-631">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="6c7a4-632">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-632">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="6c7a4-633">Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-633">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="6c7a4-634">`-ssp|--susi-policy-id <ID>` -Bu proje için oturum açma ve kaydolma ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-634">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="6c7a4-635">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-635">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6c7a4-636">`-rp|--reset-password-policy-id <ID>` -Bu proje için reset parola ilkesi kimliği.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-636">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="6c7a4-637">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-637">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6c7a4-638">`-ep|--edit-profile-policy-id <ID>` -Bu proje için düzenleme profili ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-638">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="6c7a4-639">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-639">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6c7a4-640">`--aad-instance <INSTANCE>` -Bağlanmak için Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-640">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="6c7a4-641">İle kullanma `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-641">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="6c7a4-642">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-642">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="6c7a4-643">`--client-id <ID>` -Bu proje için istemci kimliği.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-643">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="6c7a4-644">İle kullanma `IndividualB2C`, `SingleOrg`, veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-644">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="6c7a4-645">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-645">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="6c7a4-646">`--domain <DOMAIN>` -Dizin kiracısı için etki alanı.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-646">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="6c7a4-647">İle kullanma `SingleOrg` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-647">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="6c7a4-648">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-648">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="6c7a4-649">`--tenant-id <ID>` -Tenantıd bağlanmak için kimliği dizini.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-649">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="6c7a4-650">İle kullanma `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-650">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="6c7a4-651">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-651">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="6c7a4-652">`--callback-path <PATH>` -Yeniden yönlendirme URI'si uygulamanın taban yolu içindeki istek yolu.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-652">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="6c7a4-653">İle kullanma `SingleOrg` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-653">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="6c7a4-654">Varsayılan değer `/signin-oidc` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-654">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="6c7a4-655">`-r|--org-read-access` -Bu uygulamanın dizine okuma erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-655">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="6c7a4-656">Yalnızca uygulandığı `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-656">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="6c7a4-657">`--exclude-launch-settings` -Hariç *launchSettings.json* oluşturulan şablonundan.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-657">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="6c7a4-658">`--use-browserlink` -BrowserLink projede içerir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-658">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="6c7a4-659">`-uld|--use-local-db` -LocalDB yerine SQLite kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-659">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="6c7a4-660">Yalnızca uygulandığı `Individual` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-660">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6c7a4-661">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-661">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6c7a4-662">`--no-https` -Proje HTTPS'yi gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-662">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="6c7a4-663">`app.UseHsts` ve `app.UseHttpsRedirection` için eklenmez `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-663">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="6c7a4-664">Bu seçenek yalnızca geçerlidir `Individual`, `IndividualB2C`, `SingleOrg`, veya `MultiOrg` kullanılmayan.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-664">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="6c7a4-665">**Sayfa**</span><span class="sxs-lookup"><span data-stu-id="6c7a4-665">**page**</span></span>

<span data-ttu-id="6c7a4-666">`-na|--namespace <NAMESPACE_NAME>` -Namespace üretilen kod için.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-666">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="6c7a4-667">Varsayılan değer `MyApp.Namespace` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-667">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="6c7a4-668">`-np|--no-pagemodel` -Bir PageModel olmadan sayfası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-668">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="6c7a4-669">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="6c7a4-669">**viewimports**</span></span>

<span data-ttu-id="6c7a4-670">`-na|--namespace <NAMESPACE_NAME>` -Namespace üretilen kod için.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-670">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="6c7a4-671">Varsayılan değer `MyApp.Namespace` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-671">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="6c7a4-672">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="6c7a4-672">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="6c7a4-673">**konsolunda, angular, react, açarken kilitlenmesi**</span><span class="sxs-lookup"><span data-stu-id="6c7a4-673">**console, angular, react, reactredux**</span></span>

<span data-ttu-id="6c7a4-674">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-674">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6c7a4-675">**classlib**</span><span class="sxs-lookup"><span data-stu-id="6c7a4-675">**classlib**</span></span>

<span data-ttu-id="6c7a4-676">`-f|--framework <FRAMEWORK>` -Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-676">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="6c7a4-677">Değerler: `netcoreapp2.0` bir .NET Core sınıf kitaplığı oluşturmak için veya `netstandard2.0` .NET standart sınıf kitaplığı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-677">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="6c7a4-678">Varsayılan değer `netstandard2.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-678">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="6c7a4-679">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-679">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6c7a4-680">**MSTest, xunit**</span><span class="sxs-lookup"><span data-stu-id="6c7a4-680">**mstest, xunit**</span></span>

<span data-ttu-id="6c7a4-681">`-p|--enable-pack` -Etkinleştirir kullanarak projeyi için paketleme [dotnet paketi](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="6c7a4-681">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="6c7a4-682">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-682">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6c7a4-683">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="6c7a4-683">**globaljson**</span></span>

<span data-ttu-id="6c7a4-684">`--sdk-version <VERSION_NUMBER>` -Kullanmak için .NET Core SDK'sı sürümünü belirtir *global.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-684">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="6c7a4-685">**Web**</span><span class="sxs-lookup"><span data-stu-id="6c7a4-685">**web**</span></span>

<span data-ttu-id="6c7a4-686">`--use-launch-settings` -İçeren *launchSettings.json* oluşturulan şablon çıktı.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-686">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="6c7a4-687">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-687">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6c7a4-688">**webapı**</span><span class="sxs-lookup"><span data-stu-id="6c7a4-688">**webapi**</span></span>

<span data-ttu-id="6c7a4-689">`-au|--auth <AUTHENTICATION_TYPE>` -Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-689">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="6c7a4-690">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="6c7a4-690">The possible values are:</span></span>

- <span data-ttu-id="6c7a4-691">`None` -Kimlik doğrulama yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="6c7a4-691">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="6c7a4-692">`IndividualB2C` -Azure AD B2C ile kimlik doğrulaması tek tek.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-692">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="6c7a4-693">`SingleOrg` -Kuruluş kimlik doğrulaması için tek bir kiracı.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-693">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="6c7a4-694">`Windows` -Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-694">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="6c7a4-695">`--aad-b2c-instance <INSTANCE>` -Bağlanmak için Azure Active Directory B2C örnek.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-695">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="6c7a4-696">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-696">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="6c7a4-697">Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-697">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="6c7a4-698">`-ssp|--susi-policy-id <ID>` -Bu proje için oturum açma ve kaydolma ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-698">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="6c7a4-699">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-699">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6c7a4-700">`--aad-instance <INSTANCE>` -Bağlanmak için Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-700">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="6c7a4-701">İle kullanma `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-701">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="6c7a4-702">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-702">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="6c7a4-703">`--client-id <ID>` -Bu proje için istemci kimliği.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-703">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="6c7a4-704">İle kullanma `IndividualB2C` veya `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-704">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="6c7a4-705">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-705">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="6c7a4-706">`--domain <DOMAIN>` -Dizin kiracısı için etki alanı.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-706">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="6c7a4-707">İle kullanma `SingleOrg` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-707">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="6c7a4-708">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-708">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="6c7a4-709">`--tenant-id <ID>` -Tenantıd bağlanmak için kimliği dizini.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-709">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="6c7a4-710">İle kullanma `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-710">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="6c7a4-711">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-711">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="6c7a4-712">`-r|--org-read-access` -Bu uygulamanın dizine okuma erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-712">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="6c7a4-713">Yalnızca uygulandığı `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-713">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="6c7a4-714">`--use-launch-settings` -İçeren *launchSettings.json* oluşturulan şablon çıktı.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-714">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="6c7a4-715">`-uld|--use-local-db` -LocalDB yerine SQLite kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-715">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="6c7a4-716">Yalnızca uygulandığı `Individual` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-716">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6c7a4-717">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-717">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6c7a4-718">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="6c7a4-718">**mvc, razor**</span></span>

<span data-ttu-id="6c7a4-719">`-au|--auth <AUTHENTICATION_TYPE>` -Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-719">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="6c7a4-720">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="6c7a4-720">The possible values are:</span></span>

- <span data-ttu-id="6c7a4-721">`None` -Kimlik doğrulama yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="6c7a4-721">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="6c7a4-722">`Individual` -Tek tek kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-722">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="6c7a4-723">`IndividualB2C` -Azure AD B2C ile kimlik doğrulaması tek tek.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-723">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="6c7a4-724">`SingleOrg` -Kuruluş kimlik doğrulaması için tek bir kiracı.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-724">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="6c7a4-725">`MultiOrg` -Birden fazla Kiracı için Kurumsal kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-725">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="6c7a4-726">`Windows` -Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-726">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="6c7a4-727">`--aad-b2c-instance <INSTANCE>` -Bağlanmak için Azure Active Directory B2C örnek.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-727">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="6c7a4-728">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-728">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="6c7a4-729">Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-729">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="6c7a4-730">`-ssp|--susi-policy-id <ID>` -Bu proje için oturum açma ve kaydolma ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-730">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="6c7a4-731">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-731">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6c7a4-732">`-rp|--reset-password-policy-id <ID>` -Bu proje için reset parola ilkesi kimliği.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-732">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="6c7a4-733">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-733">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6c7a4-734">`-ep|--edit-profile-policy-id <ID>` -Bu proje için düzenleme profili ilke kimliği.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-734">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="6c7a4-735">İle kullanma `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-735">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6c7a4-736">`--aad-instance <INSTANCE>` -Bağlanmak için Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-736">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="6c7a4-737">İle kullanma `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-737">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="6c7a4-738">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-738">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="6c7a4-739">`--client-id <ID>` -Bu proje için istemci kimliği.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-739">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="6c7a4-740">İle kullanma `IndividualB2C`, `SingleOrg`, veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-740">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="6c7a4-741">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-741">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="6c7a4-742">`--domain <DOMAIN>` -Dizin kiracısı için etki alanı.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-742">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="6c7a4-743">İle kullanma `SingleOrg` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-743">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="6c7a4-744">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-744">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="6c7a4-745">`--tenant-id <ID>` -Tenantıd bağlanmak için kimliği dizini.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-745">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="6c7a4-746">İle kullanma `SingleOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-746">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="6c7a4-747">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-747">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="6c7a4-748">`--callback-path <PATH>` -Yeniden yönlendirme URI'si uygulamanın taban yolu içindeki istek yolu.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-748">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="6c7a4-749">İle kullanma `SingleOrg` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-749">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="6c7a4-750">Varsayılan değer `/signin-oidc` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-750">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="6c7a4-751">`-r|--org-read-access` -Bu uygulamanın dizine okuma erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-751">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="6c7a4-752">Yalnızca uygulandığı `SingleOrg` veya `MultiOrg` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-752">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="6c7a4-753">`--use-launch-settings` -İçeren *launchSettings.json* oluşturulan şablon çıktı.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-753">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="6c7a4-754">`--use-browserlink` -BrowserLink projede içerir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-754">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="6c7a4-755">`-uld|--use-local-db` -LocalDB yerine SQLite kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-755">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="6c7a4-756">Yalnızca uygulandığı `Individual` veya `IndividualB2C` kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-756">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6c7a4-757">`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-757">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6c7a4-758">**Sayfa**</span><span class="sxs-lookup"><span data-stu-id="6c7a4-758">**page**</span></span>

<span data-ttu-id="6c7a4-759">`-na|--namespace <NAMESPACE_NAME>`-Namespace üretilen kod için.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-759">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="6c7a4-760">Varsayılan değer `MyApp.Namespace` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-760">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="6c7a4-761">`-np|--no-pagemodel` -Bir PageModel olmadan sayfası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-761">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="6c7a4-762">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="6c7a4-762">**viewimports**</span></span>

<span data-ttu-id="6c7a4-763">`-na|--namespace <NAMESPACE_NAME>`-Namespace üretilen kod için.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-763">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="6c7a4-764">Varsayılan değer `MyApp.Namespace` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-764">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="6c7a4-765">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="6c7a4-765">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="6c7a4-766">**Konsolu, xunit, mstest, web, webapı**</span><span class="sxs-lookup"><span data-stu-id="6c7a4-766">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="6c7a4-767">`-f|--framework <FRAMEWORK>` -Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-767">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="6c7a4-768">Değerler: `netcoreapp1.0` veya `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-768">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="6c7a4-769">Varsayılan değer `netcoreapp1.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-769">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="6c7a4-770">**classlib**</span><span class="sxs-lookup"><span data-stu-id="6c7a4-770">**classlib**</span></span>

<span data-ttu-id="6c7a4-771">`-f|--framework <FRAMEWORK>` -Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-771">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="6c7a4-772">Değerler: `netcoreapp1.0`, `netcoreapp1.1`, veya `netstandard1.0` için `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-772">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="6c7a4-773">Varsayılan değer `netstandard1.4` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-773">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="6c7a4-774">**mvc**</span><span class="sxs-lookup"><span data-stu-id="6c7a4-774">**mvc**</span></span>

<span data-ttu-id="6c7a4-775">`-f|--framework <FRAMEWORK>` -Belirtir [framework](../../standard/frameworks.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-775">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="6c7a4-776">Değerler: `netcoreapp1.0` veya `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-776">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="6c7a4-777">Varsayılan değer `netcoreapp1.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-777">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="6c7a4-778">`-au|--auth <AUTHENTICATION_TYPE>` -Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-778">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="6c7a4-779">Değerler: `None` veya `Individual`.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-779">Values: `None` or `Individual`.</span></span> <span data-ttu-id="6c7a4-780">Varsayılan değer `None` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-780">The default value is `None`.</span></span>

<span data-ttu-id="6c7a4-781">`-uld|--use-local-db` -LocalDB yerine SQLite kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-781">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="6c7a4-782">Değerler: `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-782">Values: `true` or `false`.</span></span> <span data-ttu-id="6c7a4-783">Varsayılan değer `false` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-783">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="6c7a4-784">Örnekler</span><span class="sxs-lookup"><span data-stu-id="6c7a4-784">Examples</span></span>

<span data-ttu-id="6c7a4-785">Oluşturma bir C# şablon adı belirterek konsol uygulama projesi:</span><span class="sxs-lookup"><span data-stu-id="6c7a4-785">Create a C# console application project by specifying the template name:</span></span>

`dotnet new "Console Application"`

<span data-ttu-id="6c7a4-786">Oluşturma bir F# konsol uygulama projesi geçerli dizin:</span><span class="sxs-lookup"><span data-stu-id="6c7a4-786">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="6c7a4-787">Belirtilen dizin (yalnızca .NET Core SDK 2.0 veya sonraki sürümler ile kullanılabilir) bir .NET Standard sınıf kitaplığı projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="6c7a4-787">Create a .NET Standard class library project in the specified directory (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="6c7a4-788">Yeni bir ASP.NET Core oluşturma C# MVC projesi kimlik doğrulaması olmayan geçerli dizin:</span><span class="sxs-lookup"><span data-stu-id="6c7a4-788">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

`dotnet new mvc -au None`

<span data-ttu-id="6c7a4-789">Yeni bir xUnit projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="6c7a4-789">Create a new xUnit project:</span></span>

`dotnet new xunit`

<span data-ttu-id="6c7a4-790">MVC için tüm şablonları listeler:</span><span class="sxs-lookup"><span data-stu-id="6c7a4-790">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="6c7a4-791">Eşleşen tüm şablonları listesinde *biz* alt dize.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-791">List all templates matching the *we* substring.</span></span> <span data-ttu-id="6c7a4-792">Tam eşleşme bulunamazsa, bu nedenle kısa bir ad ve ad sütunu karşı altdizgi eşleştirme çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-792">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

`dotnet new we -l`

<span data-ttu-id="6c7a4-793">Eşleşen şablon çağırma girişiminde *ng*.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-793">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="6c7a4-794">Tek bir eşleştirme belirlenemiyorsa, kısmi eşleşmeler şablonları listesi.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-794">If a single match can't be determined, list the templates that are partial matches.</span></span>

`dotnet new ng`

<span data-ttu-id="6c7a4-795">ASP.NET Core (komut seçeneği kullanılabilir .NET Core SDK 1.1 ve yalnızca sonraki sürümleri için) için tek sayfalı uygulama şablonları 2.0 sürümünü yükleyin:</span><span class="sxs-lookup"><span data-stu-id="6c7a4-795">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

<span data-ttu-id="6c7a4-796">Oluşturma bir *global.json* SDK'sı sürüm 2.0.0 (yalnızca .NET Core SDK 2.0 veya sonraki sürümler ile kullanılabilir) ayarı geçerli dizin:</span><span class="sxs-lookup"><span data-stu-id="6c7a4-796">Create a *global.json* in the current directory setting the SDK version to 2.0.0 (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="6c7a4-797">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6c7a4-797">See also</span></span>

- [<span data-ttu-id="6c7a4-798">Yeni dotnet için özel şablonlar</span><span class="sxs-lookup"><span data-stu-id="6c7a4-798">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="6c7a4-799">Dotnet new için özel şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="6c7a4-799">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)
- [<span data-ttu-id="6c7a4-800">DotNet/dotnet-şablonu-örnekleri GitHub deposu</span><span class="sxs-lookup"><span data-stu-id="6c7a4-800">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="6c7a4-801">Yeni dotnet şablonları</span><span class="sxs-lookup"><span data-stu-id="6c7a4-801">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
