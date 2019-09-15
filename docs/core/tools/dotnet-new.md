---
title: DotNet yeni komut
description: DotNet New komutu, belirtilen şablona göre yeni .NET Core projeleri oluşturur.
ms.date: 05/06/2019
ms.openlocfilehash: 57b198d13984fb4585e1df6303afe481e7e0552d
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70969746"
---
# <a name="dotnet-new"></a><span data-ttu-id="b7005-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="b7005-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="b7005-104">Ad</span><span class="sxs-lookup"><span data-stu-id="b7005-104">Name</span></span>

<span data-ttu-id="b7005-105">`dotnet new`-Belirtilen şablonu temel alan yeni bir proje, yapılandırma dosyası veya çözüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b7005-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b7005-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="b7005-106">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="b7005-107">.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="b7005-107">.NET Core 2.2</span></span>](#tab/netcore22)

```console
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="b7005-108">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="b7005-108">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="b7005-109">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="b7005-109">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="b7005-110">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="b7005-110">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="b7005-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b7005-111">Description</span></span>

<span data-ttu-id="b7005-112">Komut `dotnet new` , geçerli bir .NET Core projesi başlatmak için kullanışlı bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="b7005-112">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="b7005-113">Komutu, belirtilen şablon ve seçeneklere göre diskteki yapıtları oluşturmak için [şablon altyapısını](https://github.com/dotnet/templating) çağırır.</span><span class="sxs-lookup"><span data-stu-id="b7005-113">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="b7005-114">Arguments</span><span class="sxs-lookup"><span data-stu-id="b7005-114">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="b7005-115">Komut çağrıldığında örnek oluşturulacak şablon.</span><span class="sxs-lookup"><span data-stu-id="b7005-115">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="b7005-116">Her şablonun geçirebilmeniz için özel seçenekleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="b7005-116">Each template might have specific options you can pass.</span></span> <span data-ttu-id="b7005-117">Daha fazla bilgi için bkz. [şablon seçenekleri](#template-options).</span><span class="sxs-lookup"><span data-stu-id="b7005-117">For more information, see [Template options](#template-options).</span></span>

<span data-ttu-id="b7005-118">Değer, şablonlar veya **kısa ad** sütunundaki metin üzerinde tam eşleşme değilse, bu iki sütunda bir alt dize eşleşmesi gerçekleştirilir. `TEMPLATE`</span><span class="sxs-lookup"><span data-stu-id="b7005-118">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column, a substring match is performed on those two columns.</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="b7005-119">.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="b7005-119">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="b7005-120">Komut, şablonların varsayılan bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="b7005-120">The command contains a default list of templates.</span></span> <span data-ttu-id="b7005-121">Kullanılabilir `dotnet new -l` şablonların bir listesini almak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7005-121">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="b7005-122">Aşağıdaki tabloda, .NET Core SDK 2.2.100 ile önceden yüklenmiş olarak gelen şablonlar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b7005-122">The following table shows the templates that come pre-installed with the .NET Core SDK 2.2.100.</span></span> <span data-ttu-id="b7005-123">Şablon için varsayılan dil, köşeli ayraçlar içinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="b7005-123">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="b7005-124">Şablonlar</span><span class="sxs-lookup"><span data-stu-id="b7005-124">Templates</span></span>                                    | <span data-ttu-id="b7005-125">Kısa Ad</span><span class="sxs-lookup"><span data-stu-id="b7005-125">Short Name</span></span>        | <span data-ttu-id="b7005-126">Dil</span><span class="sxs-lookup"><span data-stu-id="b7005-126">Language</span></span>     | <span data-ttu-id="b7005-127">Etiketler</span><span class="sxs-lookup"><span data-stu-id="b7005-127">Tags</span></span>                                  |
|----------------------------------------------|-------------------|--------------|---------------------------------------|
| <span data-ttu-id="b7005-128">Konsol Uygulaması</span><span class="sxs-lookup"><span data-stu-id="b7005-128">Console Application</span></span>                          | `console`         | <span data-ttu-id="b7005-129">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="b7005-129">[C#], F#, VB</span></span> | <span data-ttu-id="b7005-130">Ortak/konsol</span><span class="sxs-lookup"><span data-stu-id="b7005-130">Common/Console</span></span>                        |
| <span data-ttu-id="b7005-131">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="b7005-131">Class library</span></span>                                | `classlib`        | <span data-ttu-id="b7005-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="b7005-132">[C#], F#, VB</span></span> | <span data-ttu-id="b7005-133">Ortak/Kitaplık</span><span class="sxs-lookup"><span data-stu-id="b7005-133">Common/Library</span></span>                        |
| <span data-ttu-id="b7005-134">Birim testi projesi</span><span class="sxs-lookup"><span data-stu-id="b7005-134">Unit Test Project</span></span>                            | `mstest`          | <span data-ttu-id="b7005-135">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="b7005-135">[C#], F#, VB</span></span> | <span data-ttu-id="b7005-136">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="b7005-136">Test/MSTest</span></span>                           |
| <span data-ttu-id="b7005-137">NUnit 3 test projesi</span><span class="sxs-lookup"><span data-stu-id="b7005-137">NUnit 3 Test Project</span></span>                         | `nunit`           | <span data-ttu-id="b7005-138">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="b7005-138">[C#], F#, VB</span></span> | <span data-ttu-id="b7005-139">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="b7005-139">Test/NUnit</span></span>                            |
| <span data-ttu-id="b7005-140">NUnit 3 test öğesi</span><span class="sxs-lookup"><span data-stu-id="b7005-140">NUnit 3 Test Item</span></span>                            | `nunit-test`      | <span data-ttu-id="b7005-141">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="b7005-141">[C#], F#, VB</span></span> | <span data-ttu-id="b7005-142">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="b7005-142">Test/NUnit</span></span>                            |
| <span data-ttu-id="b7005-143">xUnit test projesi</span><span class="sxs-lookup"><span data-stu-id="b7005-143">xUnit Test Project</span></span>                           | `xunit`           | <span data-ttu-id="b7005-144">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="b7005-144">[C#], F#, VB</span></span> | <span data-ttu-id="b7005-145">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="b7005-145">Test/xUnit</span></span>                            |
| <span data-ttu-id="b7005-146">Razor sayfası</span><span class="sxs-lookup"><span data-stu-id="b7005-146">Razor Page</span></span>                                   | `page`            | <span data-ttu-id="b7005-147">[C#]</span><span class="sxs-lookup"><span data-stu-id="b7005-147">[C#]</span></span>         | <span data-ttu-id="b7005-148">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="b7005-148">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="b7005-149">MVC Viewıtemts</span><span class="sxs-lookup"><span data-stu-id="b7005-149">MVC ViewImports</span></span>                              | `viewimports`     | <span data-ttu-id="b7005-150">[C#]</span><span class="sxs-lookup"><span data-stu-id="b7005-150">[C#]</span></span>         | <span data-ttu-id="b7005-151">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="b7005-151">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="b7005-152">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="b7005-152">MVC ViewStart</span></span>                                | `viewstart`       | <span data-ttu-id="b7005-153">[C#]</span><span class="sxs-lookup"><span data-stu-id="b7005-153">[C#]</span></span>         | <span data-ttu-id="b7005-154">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="b7005-154">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="b7005-155">ASP.NET Core boş</span><span class="sxs-lookup"><span data-stu-id="b7005-155">ASP.NET Core Empty</span></span>                           | `web`             | <span data-ttu-id="b7005-156">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="b7005-156">[C#], F#</span></span>     | <span data-ttu-id="b7005-157">Web/boş</span><span class="sxs-lookup"><span data-stu-id="b7005-157">Web/Empty</span></span>                             |
| <span data-ttu-id="b7005-158">ASP.NET Core Web uygulaması (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="b7005-158">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`             | <span data-ttu-id="b7005-159">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="b7005-159">[C#], F#</span></span>     | <span data-ttu-id="b7005-160">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="b7005-160">Web/MVC</span></span>                               |
| <span data-ttu-id="b7005-161">ASP.NET Core Web uygulaması</span><span class="sxs-lookup"><span data-stu-id="b7005-161">ASP.NET Core Web App</span></span>                         | <span data-ttu-id="b7005-162">`webapp`, `razor`</span><span class="sxs-lookup"><span data-stu-id="b7005-162">`webapp`, `razor`</span></span> | <span data-ttu-id="b7005-163">[C#]</span><span class="sxs-lookup"><span data-stu-id="b7005-163">[C#]</span></span>         | <span data-ttu-id="b7005-164">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="b7005-164">Web/MVC/Razor Pages</span></span>                   |
| <span data-ttu-id="b7005-165">Angular ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b7005-165">ASP.NET Core with Angular</span></span>                    | `angular`         | <span data-ttu-id="b7005-166">[C#]</span><span class="sxs-lookup"><span data-stu-id="b7005-166">[C#]</span></span>         | <span data-ttu-id="b7005-167">MVC/Web/SPA</span><span class="sxs-lookup"><span data-stu-id="b7005-167">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="b7005-168">Tepki verme. js ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b7005-168">ASP.NET Core with React.js</span></span>                   | `react`           | <span data-ttu-id="b7005-169">[C#]</span><span class="sxs-lookup"><span data-stu-id="b7005-169">[C#]</span></span>         | <span data-ttu-id="b7005-170">MVC/Web/SPA</span><span class="sxs-lookup"><span data-stu-id="b7005-170">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="b7005-171">Yanıt verir. js ve Redux ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b7005-171">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`      | <span data-ttu-id="b7005-172">[C#]</span><span class="sxs-lookup"><span data-stu-id="b7005-172">[C#]</span></span>         | <span data-ttu-id="b7005-173">MVC/Web/SPA</span><span class="sxs-lookup"><span data-stu-id="b7005-173">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="b7005-174">Razor sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="b7005-174">Razor Class Library</span></span>                          | `razorclasslib`   | <span data-ttu-id="b7005-175">[C#]</span><span class="sxs-lookup"><span data-stu-id="b7005-175">[C#]</span></span>         | <span data-ttu-id="b7005-176">Web/Razor/kitaplık/Razor sınıfı kitaplığı</span><span class="sxs-lookup"><span data-stu-id="b7005-176">Web/Razor/Library/Razor Class Library</span></span> |
| <span data-ttu-id="b7005-177">ASP.NET Core Web API 'SI</span><span class="sxs-lookup"><span data-stu-id="b7005-177">ASP.NET Core Web API</span></span>                         | `webapi`          | <span data-ttu-id="b7005-178">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="b7005-178">[C#], F#</span></span>     | <span data-ttu-id="b7005-179">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="b7005-179">Web/WebAPI</span></span>                            |
| <span data-ttu-id="b7005-180">Global. JSON dosyası</span><span class="sxs-lookup"><span data-stu-id="b7005-180">global.json file</span></span>                             | `globaljson`      |              | <span data-ttu-id="b7005-181">Config</span><span class="sxs-lookup"><span data-stu-id="b7005-181">Config</span></span>                                |
| <span data-ttu-id="b7005-182">NuGet yapılandırması</span><span class="sxs-lookup"><span data-stu-id="b7005-182">NuGet Config</span></span>                                 | `nugetconfig`     |              | <span data-ttu-id="b7005-183">Config</span><span class="sxs-lookup"><span data-stu-id="b7005-183">Config</span></span>                                |
| <span data-ttu-id="b7005-184">Web yapılandırması</span><span class="sxs-lookup"><span data-stu-id="b7005-184">Web Config</span></span>                                   | `webconfig`       |              | <span data-ttu-id="b7005-185">Config</span><span class="sxs-lookup"><span data-stu-id="b7005-185">Config</span></span>                                |
| <span data-ttu-id="b7005-186">Çözüm dosyası</span><span class="sxs-lookup"><span data-stu-id="b7005-186">Solution File</span></span>                                | `sln`             |              | <span data-ttu-id="b7005-187">Çözüm</span><span class="sxs-lookup"><span data-stu-id="b7005-187">Solution</span></span>                              |

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="b7005-188">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="b7005-188">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="b7005-189">Komut, şablonların varsayılan bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="b7005-189">The command contains a default list of templates.</span></span> <span data-ttu-id="b7005-190">Kullanılabilir `dotnet new -l` şablonların bir listesini almak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7005-190">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="b7005-191">Aşağıdaki tabloda, .NET Core SDK 2.1.300 ile önceden yüklenmiş olarak gelen şablonlar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b7005-191">The following table shows the templates that come pre-installed with the .NET Core SDK 2.1.300.</span></span> <span data-ttu-id="b7005-192">Şablon için varsayılan dil, köşeli ayraçlar içinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="b7005-192">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="b7005-193">Şablonlar</span><span class="sxs-lookup"><span data-stu-id="b7005-193">Templates</span></span>                                    | <span data-ttu-id="b7005-194">Kısa Ad</span><span class="sxs-lookup"><span data-stu-id="b7005-194">Short Name</span></span>      | <span data-ttu-id="b7005-195">Dil</span><span class="sxs-lookup"><span data-stu-id="b7005-195">Language</span></span>     | <span data-ttu-id="b7005-196">Etiketler</span><span class="sxs-lookup"><span data-stu-id="b7005-196">Tags</span></span>                                  |
|----------------------------------------------|-----------------|--------------|---------------------------------------|
| <span data-ttu-id="b7005-197">Konsol Uygulaması</span><span class="sxs-lookup"><span data-stu-id="b7005-197">Console Application</span></span>                          | `console`       | <span data-ttu-id="b7005-198">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="b7005-198">[C#], F#, VB</span></span> | <span data-ttu-id="b7005-199">Ortak/konsol</span><span class="sxs-lookup"><span data-stu-id="b7005-199">Common/Console</span></span>                        |
| <span data-ttu-id="b7005-200">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="b7005-200">Class library</span></span>                                | `classlib`      | <span data-ttu-id="b7005-201">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="b7005-201">[C#], F#, VB</span></span> | <span data-ttu-id="b7005-202">Ortak/Kitaplık</span><span class="sxs-lookup"><span data-stu-id="b7005-202">Common/Library</span></span>                        |
| <span data-ttu-id="b7005-203">Birim testi projesi</span><span class="sxs-lookup"><span data-stu-id="b7005-203">Unit Test Project</span></span>                            | `mstest`        | <span data-ttu-id="b7005-204">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="b7005-204">[C#], F#, VB</span></span> | <span data-ttu-id="b7005-205">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="b7005-205">Test/MSTest</span></span>                           |
| <span data-ttu-id="b7005-206">xUnit test projesi</span><span class="sxs-lookup"><span data-stu-id="b7005-206">xUnit Test Project</span></span>                           | `xunit`         | <span data-ttu-id="b7005-207">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="b7005-207">[C#], F#, VB</span></span> | <span data-ttu-id="b7005-208">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="b7005-208">Test/xUnit</span></span>                            |
| <span data-ttu-id="b7005-209">Razor sayfası</span><span class="sxs-lookup"><span data-stu-id="b7005-209">Razor Page</span></span>                                   | `page`          | <span data-ttu-id="b7005-210">[C#]</span><span class="sxs-lookup"><span data-stu-id="b7005-210">[C#]</span></span>         | <span data-ttu-id="b7005-211">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="b7005-211">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="b7005-212">MVC Viewıtemts</span><span class="sxs-lookup"><span data-stu-id="b7005-212">MVC ViewImports</span></span>                              | `viewimports`   | <span data-ttu-id="b7005-213">[C#]</span><span class="sxs-lookup"><span data-stu-id="b7005-213">[C#]</span></span>         | <span data-ttu-id="b7005-214">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="b7005-214">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="b7005-215">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="b7005-215">MVC ViewStart</span></span>                                | `viewstart`     | <span data-ttu-id="b7005-216">[C#]</span><span class="sxs-lookup"><span data-stu-id="b7005-216">[C#]</span></span>         | <span data-ttu-id="b7005-217">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="b7005-217">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="b7005-218">ASP.NET Core boş</span><span class="sxs-lookup"><span data-stu-id="b7005-218">ASP.NET Core Empty</span></span>                           | `web`           | <span data-ttu-id="b7005-219">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="b7005-219">[C#], F#</span></span>     | <span data-ttu-id="b7005-220">Web/boş</span><span class="sxs-lookup"><span data-stu-id="b7005-220">Web/Empty</span></span>                             |
| <span data-ttu-id="b7005-221">ASP.NET Core Web uygulaması (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="b7005-221">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`           | <span data-ttu-id="b7005-222">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="b7005-222">[C#], F#</span></span>     | <span data-ttu-id="b7005-223">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="b7005-223">Web/MVC</span></span>                               |
| <span data-ttu-id="b7005-224">ASP.NET Core Web uygulaması</span><span class="sxs-lookup"><span data-stu-id="b7005-224">ASP.NET Core Web App</span></span>                         | `razor`         | <span data-ttu-id="b7005-225">[C#]</span><span class="sxs-lookup"><span data-stu-id="b7005-225">[C#]</span></span>         | <span data-ttu-id="b7005-226">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="b7005-226">Web/MVC/Razor Pages</span></span>                   |
| <span data-ttu-id="b7005-227">Angular ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b7005-227">ASP.NET Core with Angular</span></span>                    | `angular`       | <span data-ttu-id="b7005-228">[C#]</span><span class="sxs-lookup"><span data-stu-id="b7005-228">[C#]</span></span>         | <span data-ttu-id="b7005-229">MVC/Web/SPA</span><span class="sxs-lookup"><span data-stu-id="b7005-229">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="b7005-230">Tepki verme. js ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b7005-230">ASP.NET Core with React.js</span></span>                   | `react`         | <span data-ttu-id="b7005-231">[C#]</span><span class="sxs-lookup"><span data-stu-id="b7005-231">[C#]</span></span>         | <span data-ttu-id="b7005-232">MVC/Web/SPA</span><span class="sxs-lookup"><span data-stu-id="b7005-232">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="b7005-233">Yanıt verir. js ve Redux ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b7005-233">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`    | <span data-ttu-id="b7005-234">[C#]</span><span class="sxs-lookup"><span data-stu-id="b7005-234">[C#]</span></span>         | <span data-ttu-id="b7005-235">MVC/Web/SPA</span><span class="sxs-lookup"><span data-stu-id="b7005-235">Web/MVC/SPA</span></span>                           | 
| <span data-ttu-id="b7005-236">Razor sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="b7005-236">Razor Class Library</span></span>                          | `razorclasslib` | <span data-ttu-id="b7005-237">[C#]</span><span class="sxs-lookup"><span data-stu-id="b7005-237">[C#]</span></span>         | <span data-ttu-id="b7005-238">Web/Razor/kitaplık/Razor sınıfı kitaplığı</span><span class="sxs-lookup"><span data-stu-id="b7005-238">Web/Razor/Library/Razor Class Library</span></span> |
| <span data-ttu-id="b7005-239">ASP.NET Core Web API 'SI</span><span class="sxs-lookup"><span data-stu-id="b7005-239">ASP.NET Core Web API</span></span>                         | `webapi`        | <span data-ttu-id="b7005-240">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="b7005-240">[C#], F#</span></span>     | <span data-ttu-id="b7005-241">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="b7005-241">Web/WebAPI</span></span>                            |
| <span data-ttu-id="b7005-242">Global. JSON dosyası</span><span class="sxs-lookup"><span data-stu-id="b7005-242">global.json file</span></span>                             | `globaljson`    |              | <span data-ttu-id="b7005-243">Config</span><span class="sxs-lookup"><span data-stu-id="b7005-243">Config</span></span>                                |
| <span data-ttu-id="b7005-244">NuGet yapılandırması</span><span class="sxs-lookup"><span data-stu-id="b7005-244">NuGet Config</span></span>                                 | `nugetconfig`   |              | <span data-ttu-id="b7005-245">Config</span><span class="sxs-lookup"><span data-stu-id="b7005-245">Config</span></span>                                |
| <span data-ttu-id="b7005-246">Web yapılandırması</span><span class="sxs-lookup"><span data-stu-id="b7005-246">Web Config</span></span>                                   | `webconfig`     |              | <span data-ttu-id="b7005-247">Config</span><span class="sxs-lookup"><span data-stu-id="b7005-247">Config</span></span>                                |
| <span data-ttu-id="b7005-248">Çözüm dosyası</span><span class="sxs-lookup"><span data-stu-id="b7005-248">Solution File</span></span>                                | `sln`           |              | <span data-ttu-id="b7005-249">Çözüm</span><span class="sxs-lookup"><span data-stu-id="b7005-249">Solution</span></span>                              |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="b7005-250">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="b7005-250">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="b7005-251">Komut, şablonların varsayılan bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="b7005-251">The command contains a default list of templates.</span></span> <span data-ttu-id="b7005-252">Kullanılabilir `dotnet new -l` şablonların bir listesini almak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7005-252">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="b7005-253">Aşağıdaki tabloda, .NET Core SDK 2.0.0 ile önceden yüklenmiş olarak gelen şablonlar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b7005-253">The following table shows the templates that come pre-installed with the .NET Core SDK 2.0.0.</span></span> <span data-ttu-id="b7005-254">Şablon için varsayılan dil, köşeli ayraçlar içinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="b7005-254">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="b7005-255">Şablonlar</span><span class="sxs-lookup"><span data-stu-id="b7005-255">Templates</span></span>                                    | <span data-ttu-id="b7005-256">Kısa Ad</span><span class="sxs-lookup"><span data-stu-id="b7005-256">Short Name</span></span>    | <span data-ttu-id="b7005-257">Dil</span><span class="sxs-lookup"><span data-stu-id="b7005-257">Language</span></span>     | <span data-ttu-id="b7005-258">Etiketler</span><span class="sxs-lookup"><span data-stu-id="b7005-258">Tags</span></span>                |
|----------------------------------------------|---------------|--------------|---------------------|
| <span data-ttu-id="b7005-259">Konsol Uygulaması</span><span class="sxs-lookup"><span data-stu-id="b7005-259">Console Application</span></span>                          | `console`     | <span data-ttu-id="b7005-260">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="b7005-260">[C#], F#, VB</span></span> | <span data-ttu-id="b7005-261">Ortak/konsol</span><span class="sxs-lookup"><span data-stu-id="b7005-261">Common/Console</span></span>      |
| <span data-ttu-id="b7005-262">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="b7005-262">Class library</span></span>                                | `classlib`    | <span data-ttu-id="b7005-263">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="b7005-263">[C#], F#, VB</span></span> | <span data-ttu-id="b7005-264">Ortak/Kitaplık</span><span class="sxs-lookup"><span data-stu-id="b7005-264">Common/Library</span></span>      |
| <span data-ttu-id="b7005-265">Birim testi projesi</span><span class="sxs-lookup"><span data-stu-id="b7005-265">Unit Test Project</span></span>                            | `mstest`      | <span data-ttu-id="b7005-266">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="b7005-266">[C#], F#, VB</span></span> | <span data-ttu-id="b7005-267">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="b7005-267">Test/MSTest</span></span>         |
| <span data-ttu-id="b7005-268">xUnit test projesi</span><span class="sxs-lookup"><span data-stu-id="b7005-268">xUnit Test Project</span></span>                           | `xunit`       | <span data-ttu-id="b7005-269">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="b7005-269">[C#], F#, VB</span></span> | <span data-ttu-id="b7005-270">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="b7005-270">Test/xUnit</span></span>          |
| <span data-ttu-id="b7005-271">ASP.NET Core boş</span><span class="sxs-lookup"><span data-stu-id="b7005-271">ASP.NET Core Empty</span></span>                           | `web`         | <span data-ttu-id="b7005-272">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="b7005-272">[C#], F#</span></span>     | <span data-ttu-id="b7005-273">Web/boş</span><span class="sxs-lookup"><span data-stu-id="b7005-273">Web/Empty</span></span>           |
| <span data-ttu-id="b7005-274">ASP.NET Core Web uygulaması (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="b7005-274">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="b7005-275">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="b7005-275">[C#], F#</span></span>     | <span data-ttu-id="b7005-276">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="b7005-276">Web/MVC</span></span>             |
| <span data-ttu-id="b7005-277">ASP.NET Core Web uygulaması</span><span class="sxs-lookup"><span data-stu-id="b7005-277">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="b7005-278">[C#]</span><span class="sxs-lookup"><span data-stu-id="b7005-278">[C#]</span></span>         | <span data-ttu-id="b7005-279">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="b7005-279">Web/MVC/Razor Pages</span></span> |
| <span data-ttu-id="b7005-280">Angular ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b7005-280">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="b7005-281">[C#]</span><span class="sxs-lookup"><span data-stu-id="b7005-281">[C#]</span></span>         | <span data-ttu-id="b7005-282">MVC/Web/SPA</span><span class="sxs-lookup"><span data-stu-id="b7005-282">Web/MVC/SPA</span></span>         |
| <span data-ttu-id="b7005-283">Tepki verme. js ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b7005-283">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="b7005-284">[C#]</span><span class="sxs-lookup"><span data-stu-id="b7005-284">[C#]</span></span>         | <span data-ttu-id="b7005-285">MVC/Web/SPA</span><span class="sxs-lookup"><span data-stu-id="b7005-285">Web/MVC/SPA</span></span>         |
| <span data-ttu-id="b7005-286">Yanıt verir. js ve Redux ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b7005-286">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="b7005-287">[C#]</span><span class="sxs-lookup"><span data-stu-id="b7005-287">[C#]</span></span>         | <span data-ttu-id="b7005-288">MVC/Web/SPA</span><span class="sxs-lookup"><span data-stu-id="b7005-288">Web/MVC/SPA</span></span>         |
| <span data-ttu-id="b7005-289">ASP.NET Core Web API 'SI</span><span class="sxs-lookup"><span data-stu-id="b7005-289">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="b7005-290">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="b7005-290">[C#], F#</span></span>     | <span data-ttu-id="b7005-291">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="b7005-291">Web/WebAPI</span></span>          |
| <span data-ttu-id="b7005-292">Global. JSON dosyası</span><span class="sxs-lookup"><span data-stu-id="b7005-292">global.json file</span></span>                             | `globaljson`  |              | <span data-ttu-id="b7005-293">Config</span><span class="sxs-lookup"><span data-stu-id="b7005-293">Config</span></span>              |
| <span data-ttu-id="b7005-294">NuGet yapılandırması</span><span class="sxs-lookup"><span data-stu-id="b7005-294">Nuget Config</span></span>                                 | `nugetconfig` |              | <span data-ttu-id="b7005-295">Config</span><span class="sxs-lookup"><span data-stu-id="b7005-295">Config</span></span>              |
| <span data-ttu-id="b7005-296">Web yapılandırması</span><span class="sxs-lookup"><span data-stu-id="b7005-296">Web Config</span></span>                                   | `webconfig`   |              | <span data-ttu-id="b7005-297">Config</span><span class="sxs-lookup"><span data-stu-id="b7005-297">Config</span></span>              |
| <span data-ttu-id="b7005-298">Çözüm dosyası</span><span class="sxs-lookup"><span data-stu-id="b7005-298">Solution File</span></span>                                | `sln`         |              | <span data-ttu-id="b7005-299">Çözüm</span><span class="sxs-lookup"><span data-stu-id="b7005-299">Solution</span></span>            |
| <span data-ttu-id="b7005-300">Razor sayfası</span><span class="sxs-lookup"><span data-stu-id="b7005-300">Razor Page</span></span>                                   | `page`        |              | <span data-ttu-id="b7005-301">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="b7005-301">Web/ASP.NET</span></span>         |
| <span data-ttu-id="b7005-302">MVC Viewıtemts</span><span class="sxs-lookup"><span data-stu-id="b7005-302">MVC ViewImports</span></span>                              | `viewimports` |              | <span data-ttu-id="b7005-303">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="b7005-303">Web/ASP.NET</span></span>         |
| <span data-ttu-id="b7005-304">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="b7005-304">MVC ViewStart</span></span>                                | `viewstart`   |              | <span data-ttu-id="b7005-305">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="b7005-305">Web/ASP.NET</span></span>         |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="b7005-306">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="b7005-306">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="b7005-307">Komut, şablonların varsayılan bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="b7005-307">The command contains a default list of templates.</span></span> <span data-ttu-id="b7005-308">Kullanılabilir `dotnet new -all` şablonların bir listesini almak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7005-308">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="b7005-309">Aşağıdaki tabloda, .NET Core SDK 1.0.1 ile önceden yüklenmiş olarak gelen şablonlar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b7005-309">The following table shows the templates that come pre-installed with the .NET Core SDK 1.0.1.</span></span> <span data-ttu-id="b7005-310">Şablon için varsayılan dil, köşeli ayraçlar içinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="b7005-310">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="b7005-311">Şablonlar</span><span class="sxs-lookup"><span data-stu-id="b7005-311">Templates</span></span>            | <span data-ttu-id="b7005-312">Kısa Ad</span><span class="sxs-lookup"><span data-stu-id="b7005-312">Short Name</span></span>    | <span data-ttu-id="b7005-313">Dil</span><span class="sxs-lookup"><span data-stu-id="b7005-313">Language</span></span> | <span data-ttu-id="b7005-314">Etiketler</span><span class="sxs-lookup"><span data-stu-id="b7005-314">Tags</span></span>           |
|----------------------|---------------|----------|----------------|
| <span data-ttu-id="b7005-315">Konsol Uygulaması</span><span class="sxs-lookup"><span data-stu-id="b7005-315">Console Application</span></span>  | `console`     | <span data-ttu-id="b7005-316">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="b7005-316">[C#], F#</span></span> | <span data-ttu-id="b7005-317">Ortak/konsol</span><span class="sxs-lookup"><span data-stu-id="b7005-317">Common/Console</span></span> |
| <span data-ttu-id="b7005-318">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="b7005-318">Class library</span></span>        | `classlib`    | <span data-ttu-id="b7005-319">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="b7005-319">[C#], F#</span></span> | <span data-ttu-id="b7005-320">Ortak/Kitaplık</span><span class="sxs-lookup"><span data-stu-id="b7005-320">Common/Library</span></span> |
| <span data-ttu-id="b7005-321">Birim testi projesi</span><span class="sxs-lookup"><span data-stu-id="b7005-321">Unit Test Project</span></span>    | `mstest`      | <span data-ttu-id="b7005-322">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="b7005-322">[C#], F#</span></span> | <span data-ttu-id="b7005-323">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="b7005-323">Test/MSTest</span></span>    |
| <span data-ttu-id="b7005-324">xUnit test projesi</span><span class="sxs-lookup"><span data-stu-id="b7005-324">xUnit Test Project</span></span>   | `xunit`       | <span data-ttu-id="b7005-325">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="b7005-325">[C#], F#</span></span> | <span data-ttu-id="b7005-326">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="b7005-326">Test/xUnit</span></span>     |
| <span data-ttu-id="b7005-327">ASP.NET Core boş</span><span class="sxs-lookup"><span data-stu-id="b7005-327">ASP.NET Core Empty</span></span>   | `web`         | <span data-ttu-id="b7005-328">[C#]</span><span class="sxs-lookup"><span data-stu-id="b7005-328">[C#]</span></span>     | <span data-ttu-id="b7005-329">Web/boş</span><span class="sxs-lookup"><span data-stu-id="b7005-329">Web/Empty</span></span>      |
| <span data-ttu-id="b7005-330">ASP.NET Core Web uygulaması</span><span class="sxs-lookup"><span data-stu-id="b7005-330">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="b7005-331">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="b7005-331">[C#], F#</span></span> | <span data-ttu-id="b7005-332">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="b7005-332">Web/MVC</span></span>        |
| <span data-ttu-id="b7005-333">ASP.NET Core Web API 'SI</span><span class="sxs-lookup"><span data-stu-id="b7005-333">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="b7005-334">[C#]</span><span class="sxs-lookup"><span data-stu-id="b7005-334">[C#]</span></span>     | <span data-ttu-id="b7005-335">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="b7005-335">Web/WebAPI</span></span>     |
| <span data-ttu-id="b7005-336">NuGet yapılandırması</span><span class="sxs-lookup"><span data-stu-id="b7005-336">Nuget Config</span></span>         | `nugetconfig` |          | <span data-ttu-id="b7005-337">Config</span><span class="sxs-lookup"><span data-stu-id="b7005-337">Config</span></span>         |
| <span data-ttu-id="b7005-338">Web yapılandırması</span><span class="sxs-lookup"><span data-stu-id="b7005-338">Web Config</span></span>           | `webconfig`   |          | <span data-ttu-id="b7005-339">Config</span><span class="sxs-lookup"><span data-stu-id="b7005-339">Config</span></span>         |
| <span data-ttu-id="b7005-340">Çözüm dosyası</span><span class="sxs-lookup"><span data-stu-id="b7005-340">Solution File</span></span>        | `sln`         |          | <span data-ttu-id="b7005-341">Çözüm</span><span class="sxs-lookup"><span data-stu-id="b7005-341">Solution</span></span>       |

---

## <a name="options"></a><span data-ttu-id="b7005-342">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="b7005-342">Options</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="b7005-343">.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="b7005-343">.NET Core 2.2</span></span>](#tab/netcore22)

`--dry-run`

<span data-ttu-id="b7005-344">Bir şablon oluşturulmasına neden olacaksa, verilen komutun çalıştırılması durumunda ne olacağını gösteren bir Özet görüntüler.</span><span class="sxs-lookup"><span data-stu-id="b7005-344">Displays a summary of what would happen if the given command were run if it would result in a template creation.</span></span>

`--force`

<span data-ttu-id="b7005-345">Var olan dosyaları değiştirebilse bile içeriğin oluşturulmasını zorlar.</span><span class="sxs-lookup"><span data-stu-id="b7005-345">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="b7005-346">Çıkış dizini zaten bir proje içerdiğinde bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b7005-346">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="b7005-347">Komut için yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="b7005-347">Prints out help for the command.</span></span> <span data-ttu-id="b7005-348">`dotnet new` Komutun kendisi veya gibi herhangi bir şablon `dotnet new mvc --help`için çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="b7005-348">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="b7005-349">`PATH` Veya`NUGET_ID` tarafından sağlanmış bir kaynak veya şablon paketi kurar.</span><span class="sxs-lookup"><span data-stu-id="b7005-349">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="b7005-350">Şablon paketinin bir ön sürümü sürümünü yüklemek istiyorsanız, sürümü biçiminde `<package-name>::<package-version>`belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b7005-350">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="b7005-351">Varsayılan olarak, `dotnet new` en \* son kararlı paket sürümünü temsil eden sürüm için geçirir.</span><span class="sxs-lookup"><span data-stu-id="b7005-351">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="b7005-352">[Örnekler](#examples) bölümündeki bir örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="b7005-352">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="b7005-353">Özel şablonlar oluşturma hakkında daha fazla bilgi için bkz. [DotNet New Için özel şablonlar](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="b7005-353">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="b7005-354">Belirtilen adı içeren şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="b7005-354">Lists templates containing the specified name.</span></span> <span data-ttu-id="b7005-355">`dotnet new` Komut için çağrılırsa, belirtilen dizin için kullanılabilir olabilecek şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="b7005-355">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="b7005-356">Örneğin, dizin zaten bir proje içeriyorsa, tüm proje şablonlarını listeetmez.</span><span class="sxs-lookup"><span data-stu-id="b7005-356">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="b7005-357">Oluşturulacak şablonun dili.</span><span class="sxs-lookup"><span data-stu-id="b7005-357">The language of the template to create.</span></span> <span data-ttu-id="b7005-358">Kabul edilen dil şablona göre değişir (bkz. [arguments](#arguments) bölümünde Varsayılanlar).</span><span class="sxs-lookup"><span data-stu-id="b7005-358">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="b7005-359">Bazı şablonlar için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="b7005-359">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="b7005-360">Bazı kabuklar `#` özel bir karakter olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="b7005-360">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="b7005-361">Bu durumlarda, gibi dil parametre değerini `dotnet new console -lang "F#"`almalısınız.</span><span class="sxs-lookup"><span data-stu-id="b7005-361">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="b7005-362">Oluşturulan çıkışın adı.</span><span class="sxs-lookup"><span data-stu-id="b7005-362">The name for the created output.</span></span> <span data-ttu-id="b7005-363">Ad belirtilmemişse, geçerli dizinin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b7005-363">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="b7005-364">Yüklemesi sırasında kullanılacak bir NuGet kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b7005-364">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="b7005-365">Oluşturulan çıkışın yerleştirileceği konum.</span><span class="sxs-lookup"><span data-stu-id="b7005-365">Location to place the generated output.</span></span> <span data-ttu-id="b7005-366">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="b7005-366">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="b7005-367">Şablonları kullanılabilir türlerine göre filtreler.</span><span class="sxs-lookup"><span data-stu-id="b7005-367">Filters templates based on available types.</span></span> <span data-ttu-id="b7005-368">Önceden tanımlanmış değerler şunlardır "proje", "öğe" veya "diğer".</span><span class="sxs-lookup"><span data-stu-id="b7005-368">Predefined values are "project", "item", or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="b7005-369">`PATH` Veya`NUGET_ID` belirtilen bir kaynak veya şablon paketini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="b7005-369">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="b7005-370">`<PATH|NUGET_ID>` Değer hariç tutularak, yüklü olan tüm şablon paketleri ve bunlarla ilişkili şablonlar görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b7005-370">When excluding the `<PATH|NUGET_ID>` value, all currently installed template packs and their associated templates are displayed.</span></span>

> [!NOTE]
> <span data-ttu-id="b7005-371">Bir `PATH`şablonu kullanarak kaldırmak için, yolu tam olarak nitelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b7005-371">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="b7005-372">Örneğin, *C:/kullanıcıları/\<Kullanıcı >/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* çalışır, ancak içeren klasörden *./GarciaSoftware.ConsoleTemplate.CSharp* olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="b7005-372">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="b7005-373">Ayrıca, şablon yolunuza son Sonlandırıcı Dizin eğik çizgi eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="b7005-373">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="b7005-374">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="b7005-374">.NET Core 2.1</span></span>](#tab/netcore21)

`--force`

<span data-ttu-id="b7005-375">Var olan dosyaları değiştirebilse bile içeriğin oluşturulmasını zorlar.</span><span class="sxs-lookup"><span data-stu-id="b7005-375">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="b7005-376">Çıkış dizini zaten bir proje içerdiğinde bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b7005-376">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="b7005-377">Komut için yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="b7005-377">Prints out help for the command.</span></span> <span data-ttu-id="b7005-378">`dotnet new` Komutun kendisi veya gibi herhangi bir şablon `dotnet new mvc --help`için çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="b7005-378">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="b7005-379">`PATH` Veya`NUGET_ID` tarafından sağlanmış bir kaynak veya şablon paketi kurar.</span><span class="sxs-lookup"><span data-stu-id="b7005-379">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="b7005-380">Şablon paketinin bir ön sürümü sürümünü yüklemek istiyorsanız, sürümü biçiminde `<package-name>::<package-version>`belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b7005-380">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="b7005-381">Varsayılan olarak, `dotnet new` en \* son kararlı paket sürümünü temsil eden sürüm için geçirir.</span><span class="sxs-lookup"><span data-stu-id="b7005-381">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="b7005-382">[Örnekler](#examples) bölümündeki bir örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="b7005-382">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="b7005-383">Özel şablonlar oluşturma hakkında daha fazla bilgi için bkz. [DotNet New Için özel şablonlar](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="b7005-383">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="b7005-384">Belirtilen adı içeren şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="b7005-384">Lists templates containing the specified name.</span></span> <span data-ttu-id="b7005-385">`dotnet new` Komut için çağrılırsa, belirtilen dizin için kullanılabilir olabilecek şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="b7005-385">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="b7005-386">Örneğin, dizin zaten bir proje içeriyorsa, tüm proje şablonlarını listeetmez.</span><span class="sxs-lookup"><span data-stu-id="b7005-386">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="b7005-387">Oluşturulacak şablonun dili.</span><span class="sxs-lookup"><span data-stu-id="b7005-387">The language of the template to create.</span></span> <span data-ttu-id="b7005-388">Kabul edilen dil şablona göre değişir (bkz. [arguments](#arguments) bölümünde Varsayılanlar).</span><span class="sxs-lookup"><span data-stu-id="b7005-388">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="b7005-389">Bazı şablonlar için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="b7005-389">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="b7005-390">Bazı kabuklar `#` özel bir karakter olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="b7005-390">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="b7005-391">Bu durumlarda, gibi dil parametre değerini `dotnet new console -lang "F#"`almalısınız.</span><span class="sxs-lookup"><span data-stu-id="b7005-391">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="b7005-392">Oluşturulan çıkışın adı.</span><span class="sxs-lookup"><span data-stu-id="b7005-392">The name for the created output.</span></span> <span data-ttu-id="b7005-393">Ad belirtilmemişse, geçerli dizinin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b7005-393">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="b7005-394">Yüklemesi sırasında kullanılacak bir NuGet kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b7005-394">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="b7005-395">Oluşturulan çıkışın yerleştirileceği konum.</span><span class="sxs-lookup"><span data-stu-id="b7005-395">Location to place the generated output.</span></span> <span data-ttu-id="b7005-396">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="b7005-396">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="b7005-397">Şablonları kullanılabilir türlerine göre filtreler.</span><span class="sxs-lookup"><span data-stu-id="b7005-397">Filters templates based on available types.</span></span> <span data-ttu-id="b7005-398">Önceden tanımlanmış değerler şunlardır "proje", "öğe" veya "diğer".</span><span class="sxs-lookup"><span data-stu-id="b7005-398">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="b7005-399">`PATH` Veya`NUGET_ID` belirtilen bir kaynak veya şablon paketini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="b7005-399">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="b7005-400">Bir `PATH`şablonu kullanarak kaldırmak için, yolu tam olarak nitelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b7005-400">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="b7005-401">Örneğin, *C:/kullanıcıları/\<Kullanıcı >/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* çalışır, ancak içeren klasörden *./GarciaSoftware.ConsoleTemplate.CSharp* olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="b7005-401">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="b7005-402">Ayrıca, şablon yolunuza son Sonlandırıcı Dizin eğik çizgi eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="b7005-402">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="b7005-403">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="b7005-403">.NET Core 2.0</span></span>](#tab/netcore20)

`--force`

<span data-ttu-id="b7005-404">Var olan dosyaları değiştirebilse bile içeriğin oluşturulmasını zorlar.</span><span class="sxs-lookup"><span data-stu-id="b7005-404">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="b7005-405">Çıkış dizini zaten bir proje içerdiğinde bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b7005-405">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="b7005-406">Komut için yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="b7005-406">Prints out help for the command.</span></span> <span data-ttu-id="b7005-407">`dotnet new` Komutun kendisi veya gibi herhangi bir şablon `dotnet new mvc --help`için çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="b7005-407">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="b7005-408">`PATH` Veya`NUGET_ID` tarafından sağlanmış bir kaynak veya şablon paketi kurar.</span><span class="sxs-lookup"><span data-stu-id="b7005-408">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="b7005-409">Şablon paketinin bir ön sürümü sürümünü yüklemek istiyorsanız, sürümü biçiminde `<package-name>::<package-version>`belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b7005-409">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="b7005-410">Varsayılan olarak, `dotnet new` en \* son kararlı paket sürümünü temsil eden sürüm için geçirir.</span><span class="sxs-lookup"><span data-stu-id="b7005-410">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="b7005-411">[Örnekler](#examples) bölümündeki bir örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="b7005-411">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="b7005-412">Özel şablonlar oluşturma hakkında daha fazla bilgi için bkz. [DotNet New Için özel şablonlar](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="b7005-412">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="b7005-413">Belirtilen adı içeren şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="b7005-413">Lists templates containing the specified name.</span></span> <span data-ttu-id="b7005-414">`dotnet new` Komut için çağrılırsa, belirtilen dizin için kullanılabilir olabilecek şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="b7005-414">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="b7005-415">Örneğin, dizin zaten bir proje içeriyorsa, tüm proje şablonlarını listeetmez.</span><span class="sxs-lookup"><span data-stu-id="b7005-415">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="b7005-416">Oluşturulacak şablonun dili.</span><span class="sxs-lookup"><span data-stu-id="b7005-416">The language of the template to create.</span></span> <span data-ttu-id="b7005-417">Kabul edilen dil şablona göre değişir (bkz. [arguments](#arguments) bölümünde Varsayılanlar).</span><span class="sxs-lookup"><span data-stu-id="b7005-417">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="b7005-418">Bazı şablonlar için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="b7005-418">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="b7005-419">Bazı kabuklar `#` özel bir karakter olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="b7005-419">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="b7005-420">Bu durumlarda, gibi dil parametre değerini `dotnet new console -lang "F#"`almalısınız.</span><span class="sxs-lookup"><span data-stu-id="b7005-420">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="b7005-421">Oluşturulan çıkışın adı.</span><span class="sxs-lookup"><span data-stu-id="b7005-421">The name for the created output.</span></span> <span data-ttu-id="b7005-422">Ad belirtilmemişse, geçerli dizinin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b7005-422">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="b7005-423">Oluşturulan çıkışın yerleştirileceği konum.</span><span class="sxs-lookup"><span data-stu-id="b7005-423">Location to place the generated output.</span></span> <span data-ttu-id="b7005-424">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="b7005-424">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="b7005-425">Şablonları kullanılabilir türlerine göre filtreler.</span><span class="sxs-lookup"><span data-stu-id="b7005-425">Filters templates based on available types.</span></span> <span data-ttu-id="b7005-426">Önceden tanımlanmış değerler şunlardır "proje", "öğe" veya "diğer".</span><span class="sxs-lookup"><span data-stu-id="b7005-426">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="b7005-427">`PATH` Veya`NUGET_ID` belirtilen bir kaynak veya şablon paketini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="b7005-427">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="b7005-428">Bir kaynağı `PATH`kullanarak bir şablonu kaldırmak için yolu tam olarak nitelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b7005-428">To uninstall a template using a source `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="b7005-429">Örneğin, *C:/kullanıcıları/\<Kullanıcı >/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* çalışır, ancak içeren klasörden *./GarciaSoftware.ConsoleTemplate.CSharp* olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="b7005-429">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span> <span data-ttu-id="b7005-430">Ayrıca, şablon yolunuza son Sonlandırıcı Dizin eğik çizgi eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="b7005-430">Additionally, do not include a final terminating directory slash on your template path.</span></span>
> 
> <span data-ttu-id="b7005-431">Bir şablonu kaldırmak için gereken `PATH` veya `NUGET_ID` bağımsız değişkeni belirleyemıyorsanız, bağımsız değişken olmadan çalıştırıldığında `dotnet new --uninstall` , tüm yüklü şablonlar ve bunları kaldırmak için gereken bağımsız değişken listelenir.</span><span class="sxs-lookup"><span data-stu-id="b7005-431">If you are unable to determine the `PATH` or `NUGET_ID` argument needed to uninstall a template, running `dotnet new --uninstall` without an argument will list all installed templates and the argument required to uninstall them.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="b7005-432">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="b7005-432">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="b7005-433">Yalnızca `dotnet new` komutun bağlamında çalışırken belirli bir proje türü için tüm şablonları gösterir.</span><span class="sxs-lookup"><span data-stu-id="b7005-433">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="b7005-434">Gibi belirli bir şablon `dotnet new web -all`bağlamında çalıştırılırken, `-all` zorla oluşturma bayrağı olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="b7005-434">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="b7005-435">Çıkış dizini zaten bir proje içerdiğinde bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b7005-435">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="b7005-436">Komut için yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="b7005-436">Prints out help for the command.</span></span> <span data-ttu-id="b7005-437">`dotnet new` Komutun kendisi veya gibi herhangi bir şablon `dotnet new mvc --help`için çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="b7005-437">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="b7005-438">Belirtilen adı içeren şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="b7005-438">Lists templates containing the specified name.</span></span> <span data-ttu-id="b7005-439">`dotnet new` Komut için çağrılırsa, belirtilen dizin için kullanılabilir olabilecek şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="b7005-439">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="b7005-440">Örneğin, dizin zaten bir proje içeriyorsa, tüm proje şablonlarını listeetmez.</span><span class="sxs-lookup"><span data-stu-id="b7005-440">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="b7005-441">Oluşturulacak şablonun dili.</span><span class="sxs-lookup"><span data-stu-id="b7005-441">The language of the template to create.</span></span> <span data-ttu-id="b7005-442">Kabul edilen dil şablona göre değişir (bkz. [arguments](#arguments) bölümünde Varsayılanlar).</span><span class="sxs-lookup"><span data-stu-id="b7005-442">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="b7005-443">Bazı şablonlar için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="b7005-443">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="b7005-444">Bazı kabuklar `#` özel bir karakter olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="b7005-444">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="b7005-445">Bu durumlarda, gibi dil parametre değerini `dotnet new console -lang "F#"`almalısınız.</span><span class="sxs-lookup"><span data-stu-id="b7005-445">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="b7005-446">Oluşturulan çıkışın adı.</span><span class="sxs-lookup"><span data-stu-id="b7005-446">The name for the created output.</span></span> <span data-ttu-id="b7005-447">Ad belirtilmemişse, geçerli dizinin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b7005-447">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="b7005-448">Oluşturulan çıkışın yerleştirileceği konum.</span><span class="sxs-lookup"><span data-stu-id="b7005-448">Location to place the generated output.</span></span> <span data-ttu-id="b7005-449">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="b7005-449">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="b7005-450">Şablon seçenekleri</span><span class="sxs-lookup"><span data-stu-id="b7005-450">Template options</span></span>

<span data-ttu-id="b7005-451">Her proje şablonunda ek seçenekler bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="b7005-451">Each project template may have additional options available.</span></span> <span data-ttu-id="b7005-452">Çekirdek şablonlar aşağıdaki ek seçeneklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="b7005-452">The core templates have the following additional options:</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="b7005-453">.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="b7005-453">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="b7005-454">**konsola**</span><span class="sxs-lookup"><span data-stu-id="b7005-454">**console**</span></span>

<span data-ttu-id="b7005-455">`--langVersion <VERSION_NUMBER>`-Oluşturulan proje `LangVersion` dosyasındaki özelliği ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b7005-455">`--langVersion <VERSION_NUMBER>` - Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="b7005-456">Örneğin, 7,3 kullanmak `--langVersion 7.3` C# için kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7005-456">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="b7005-457">İçin F#desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="b7005-457">Not supported for F#.</span></span>

<span data-ttu-id="b7005-458">`--no-restore`-Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="b7005-458">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b7005-459">**Angular, tepki, reactredux**</span><span class="sxs-lookup"><span data-stu-id="b7005-459">**angular, react, reactredux**</span></span>

<span data-ttu-id="b7005-460">`--exclude-launch-settings`- *Launchsettings. JSON* öğesini oluşturulan şablondan hariç tutun.</span><span class="sxs-lookup"><span data-stu-id="b7005-460">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="b7005-461">`--no-restore`-Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="b7005-461">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b7005-462">`--no-https`-Proje HTTPS gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="b7005-462">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="b7005-463">Bu seçenek yalnızca `IndividualAuth` veya `OrganizationalAuth` kullanılmıyorsa geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b7005-463">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="b7005-464">**razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="b7005-464">**razorclasslib**</span></span>

<span data-ttu-id="b7005-465">`--no-restore`-Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="b7005-465">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b7005-466">**projesinin**</span><span class="sxs-lookup"><span data-stu-id="b7005-466">**classlib**</span></span>

<span data-ttu-id="b7005-467">`-f|--framework <FRAMEWORK>`-Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="b7005-467">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="b7005-468">Değerler: `netcoreapp2.2` bir .NET Core sınıf kitaplığı oluşturmak veya `netstandard2.0` bir .NET Standard sınıf kitaplığı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="b7005-468">Values: `netcoreapp2.2` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="b7005-469">Varsayılan değer `netstandard2.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b7005-469">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="b7005-470">`--langVersion <VERSION_NUMBER>`-Oluşturulan proje `LangVersion` dosyasındaki özelliği ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b7005-470">`--langVersion <VERSION_NUMBER>` - Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="b7005-471">Örneğin, 7,3 kullanmak `--langVersion 7.3` C# için kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7005-471">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="b7005-472">İçin F#desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="b7005-472">Not supported for F#.</span></span>

<span data-ttu-id="b7005-473">`--no-restore`-Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="b7005-473">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b7005-474">**MSTest, xUnit**</span><span class="sxs-lookup"><span data-stu-id="b7005-474">**mstest, xunit**</span></span>

<span data-ttu-id="b7005-475">`-p|--enable-pack`- [DotNet Pack](dotnet-pack.md)kullanarak proje için paketlemeyi etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="b7005-475">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="b7005-476">`--no-restore`-Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="b7005-476">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b7005-477">**NUnit**</span><span class="sxs-lookup"><span data-stu-id="b7005-477">**nunit**</span></span>

<span data-ttu-id="b7005-478">`-f|--framework <FRAMEWORK>`-Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="b7005-478">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="b7005-479">Varsayılan değer `netcoreapp2.1` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b7005-479">The default value is `netcoreapp2.1`.</span></span>

<span data-ttu-id="b7005-480">`-p|--enable-pack`- [DotNet Pack](dotnet-pack.md)kullanarak proje için paketlemeyi etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="b7005-480">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="b7005-481">`--no-restore`-Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="b7005-481">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b7005-482">**sayfasında**</span><span class="sxs-lookup"><span data-stu-id="b7005-482">**page**</span></span>

<span data-ttu-id="b7005-483">`-na|--namespace <NAMESPACE_NAME>`-Oluşturulan kod için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="b7005-483">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="b7005-484">Varsayılan değer `MyApp.Namespace` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b7005-484">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="b7005-485">`-np|--no-pagemodel`-Sayfayı PageModel olmadan oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b7005-485">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="b7005-486">**viewıtems 'lar**</span><span class="sxs-lookup"><span data-stu-id="b7005-486">**viewimports**</span></span>

<span data-ttu-id="b7005-487">`-na|--namespace <NAMESPACE_NAME>`-Oluşturulan kod için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="b7005-487">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="b7005-488">Varsayılan değer `MyApp.Namespace` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b7005-488">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="b7005-489">**Web**</span><span class="sxs-lookup"><span data-stu-id="b7005-489">**web**</span></span>

<span data-ttu-id="b7005-490">`--exclude-launch-settings`- *Launchsettings. JSON* öğesini oluşturulan şablondan hariç tutun.</span><span class="sxs-lookup"><span data-stu-id="b7005-490">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="b7005-491">`--no-restore`-Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="b7005-491">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b7005-492">`--no-https`-Proje HTTPS gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="b7005-492">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="b7005-493">Bu seçenek yalnızca `IndividualAuth` veya `OrganizationalAuth` kullanılmıyorsa geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b7005-493">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="b7005-494">**MVC, WebApp**</span><span class="sxs-lookup"><span data-stu-id="b7005-494">**mvc, webapp**</span></span>

<span data-ttu-id="b7005-495">`-au|--auth <AUTHENTICATION_TYPE>`-Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="b7005-495">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="b7005-496">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b7005-496">The possible values are:</span></span>

- <span data-ttu-id="b7005-497">`None`-Kimlik doğrulaması yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="b7005-497">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="b7005-498">`Individual`-Bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="b7005-498">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="b7005-499">`IndividualB2C`-Azure AD B2C ile bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="b7005-499">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="b7005-500">`SingleOrg`-Tek bir kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="b7005-500">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="b7005-501">`MultiOrg`-Birden çok kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="b7005-501">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="b7005-502">`Windows`-Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="b7005-502">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="b7005-503">`--aad-b2c-instance <INSTANCE>`-Bağlanılacak Azure Active Directory B2C örneği.</span><span class="sxs-lookup"><span data-stu-id="b7005-503">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="b7005-504">`IndividualB2C` Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7005-504">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="b7005-505">Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b7005-505">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="b7005-506">`-ssp|--susi-policy-id <ID>`-Bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="b7005-506">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="b7005-507">`IndividualB2C` Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7005-507">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b7005-508">`-rp|--reset-password-policy-id <ID>`-Bu proje için parola sıfırlama ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="b7005-508">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="b7005-509">`IndividualB2C` Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7005-509">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b7005-510">`-ep|--edit-profile-policy-id <ID>`-Bu proje için profil ilkesi KIMLIĞINI Düzenle.</span><span class="sxs-lookup"><span data-stu-id="b7005-510">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="b7005-511">`IndividualB2C` Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7005-511">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b7005-512">`--aad-instance <INSTANCE>`-Bağlanılacak Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="b7005-512">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="b7005-513">`SingleOrg` Veya`MultiOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7005-513">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="b7005-514">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b7005-514">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="b7005-515">`--client-id <ID>`-Bu projenin Istemci KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="b7005-515">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="b7005-516">`IndividualB2C`, Veyakimlik`MultiOrg`doğrulamasıylakullanın. `SingleOrg`</span><span class="sxs-lookup"><span data-stu-id="b7005-516">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="b7005-517">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b7005-517">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="b7005-518">`--domain <DOMAIN>`-Dizin kiracının etki alanı.</span><span class="sxs-lookup"><span data-stu-id="b7005-518">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="b7005-519">`SingleOrg` Veya`IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7005-519">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="b7005-520">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b7005-520">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="b7005-521">`--tenant-id <ID>`-Bağlanılacak dizinin Tenantıd KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="b7005-521">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="b7005-522">`SingleOrg` Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7005-522">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="b7005-523">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b7005-523">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="b7005-524">`--callback-path <PATH>`-Uygulamanın yeniden yönlendirme URI 'sinin temel yolu içindeki istek yolu.</span><span class="sxs-lookup"><span data-stu-id="b7005-524">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="b7005-525">`SingleOrg` Veya`IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7005-525">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="b7005-526">Varsayılan değer `/signin-oidc` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b7005-526">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="b7005-527">`-r|--org-read-access`-Bu uygulamanın dizine okuma erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b7005-527">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="b7005-528">Yalnızca veya `SingleOrg` `MultiOrg` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b7005-528">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="b7005-529">`--exclude-launch-settings`- *Launchsettings. JSON* öğesini oluşturulan şablondan hariç tutun.</span><span class="sxs-lookup"><span data-stu-id="b7005-529">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="b7005-530">`--no-https`-Proje HTTPS gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="b7005-530">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="b7005-531">`app.UseHsts`ve `app.UseHttpsRedirection` öğesine`Startup.Configure`eklenmez.</span><span class="sxs-lookup"><span data-stu-id="b7005-531">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="b7005-532">Bu `Individual`seçenek yalnızca `IndividualB2C` `MultiOrg` , ,,veyakullanılmıyorsageçerlidir.`SingleOrg`</span><span class="sxs-lookup"><span data-stu-id="b7005-532">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="b7005-533">`-uld|--use-local-db`-SQLite yerine LocalDB kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b7005-533">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="b7005-534">Yalnızca veya `Individual` `IndividualB2C` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b7005-534">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b7005-535">`--no-restore`-Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="b7005-535">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b7005-536">**WebApi**</span><span class="sxs-lookup"><span data-stu-id="b7005-536">**webapi**</span></span>

<span data-ttu-id="b7005-537">`-au|--auth <AUTHENTICATION_TYPE>`-Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="b7005-537">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="b7005-538">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b7005-538">The possible values are:</span></span>

- <span data-ttu-id="b7005-539">`None`-Kimlik doğrulaması yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="b7005-539">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="b7005-540">`IndividualB2C`-Azure AD B2C ile bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="b7005-540">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="b7005-541">`SingleOrg`-Tek bir kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="b7005-541">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="b7005-542">`Windows`-Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="b7005-542">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="b7005-543">`--aad-b2c-instance <INSTANCE>`-Bağlanılacak Azure Active Directory B2C örneği.</span><span class="sxs-lookup"><span data-stu-id="b7005-543">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="b7005-544">`IndividualB2C` Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7005-544">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="b7005-545">Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b7005-545">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="b7005-546">`-ssp|--susi-policy-id <ID>`-Bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="b7005-546">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="b7005-547">`IndividualB2C` Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7005-547">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b7005-548">`--aad-instance <INSTANCE>`-Bağlanılacak Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="b7005-548">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="b7005-549">`SingleOrg` Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7005-549">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="b7005-550">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b7005-550">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="b7005-551">`--client-id <ID>`-Bu projenin Istemci KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="b7005-551">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="b7005-552">`IndividualB2C` Veya`SingleOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7005-552">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="b7005-553">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b7005-553">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="b7005-554">`--domain <DOMAIN>`-Dizin kiracının etki alanı.</span><span class="sxs-lookup"><span data-stu-id="b7005-554">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="b7005-555">`SingleOrg` Veya`IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7005-555">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="b7005-556">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b7005-556">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="b7005-557">`--tenant-id <ID>`-Bağlanılacak dizinin Tenantıd KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="b7005-557">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="b7005-558">`SingleOrg` Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7005-558">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="b7005-559">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b7005-559">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="b7005-560">`-r|--org-read-access`-Bu uygulamanın dizine okuma erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b7005-560">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="b7005-561">Yalnızca veya `SingleOrg` `MultiOrg` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b7005-561">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="b7005-562">`--exclude-launch-settings`- *Launchsettings. JSON* öğesini oluşturulan şablondan hariç tutun.</span><span class="sxs-lookup"><span data-stu-id="b7005-562">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="b7005-563">`--no-https`-Proje HTTPS gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="b7005-563">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="b7005-564">`app.UseHsts`ve `app.UseHttpsRedirection` öğesine`Startup.Configure`eklenmez.</span><span class="sxs-lookup"><span data-stu-id="b7005-564">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="b7005-565">Bu `Individual`seçenek yalnızca `IndividualB2C` `MultiOrg` , ,,veyakullanılmıyorsageçerlidir.`SingleOrg`</span><span class="sxs-lookup"><span data-stu-id="b7005-565">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="b7005-566">`-uld|--use-local-db`-SQLite yerine LocalDB kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b7005-566">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="b7005-567">Yalnızca veya `Individual` `IndividualB2C` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b7005-567">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b7005-568">`--no-restore`-Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="b7005-568">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b7005-569">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="b7005-569">**globaljson**</span></span>

<span data-ttu-id="b7005-570">`--sdk-version <VERSION_NUMBER>`- *Global. JSON* dosyasında kullanılacak .NET Core SDK sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="b7005-570">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="b7005-571">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="b7005-571">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="b7005-572">**konsol, angular, tepki, reactredux, razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="b7005-572">**console, angular, react, reactredux, razorclasslib**</span></span>

<span data-ttu-id="b7005-573">`--no-restore`-Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="b7005-573">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b7005-574">**projesinin**</span><span class="sxs-lookup"><span data-stu-id="b7005-574">**classlib**</span></span>

<span data-ttu-id="b7005-575">`-f|--framework <FRAMEWORK>`-Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="b7005-575">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="b7005-576">Değerler: `netcoreapp2.1` bir .NET Core sınıf kitaplığı oluşturmak veya `netstandard2.0` bir .NET Standard sınıf kitaplığı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="b7005-576">Values: `netcoreapp2.1` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="b7005-577">Varsayılan değer `netstandard2.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b7005-577">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="b7005-578">`--no-restore`-Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="b7005-578">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b7005-579">**MSTest, xUnit**</span><span class="sxs-lookup"><span data-stu-id="b7005-579">**mstest, xunit**</span></span>

<span data-ttu-id="b7005-580">`-p|--enable-pack`- [DotNet Pack](dotnet-pack.md)kullanarak proje için paketlemeyi etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="b7005-580">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="b7005-581">`--no-restore`-Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="b7005-581">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b7005-582">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="b7005-582">**globaljson**</span></span>

<span data-ttu-id="b7005-583">`--sdk-version <VERSION_NUMBER>`- *Global. JSON* dosyasında kullanılacak .NET Core SDK sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="b7005-583">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="b7005-584">**Web**</span><span class="sxs-lookup"><span data-stu-id="b7005-584">**web**</span></span>

<span data-ttu-id="b7005-585">`--exclude-launch-settings`- *Launchsettings. JSON* öğesini oluşturulan şablondan hariç tutun.</span><span class="sxs-lookup"><span data-stu-id="b7005-585">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="b7005-586">`--no-restore`-Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="b7005-586">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b7005-587">`--no-https`-Proje HTTPS gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="b7005-587">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="b7005-588">Bu seçenek yalnızca `IndividualAuth` veya `OrganizationalAuth` kullanılmıyorsa geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b7005-588">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="b7005-589">**WebApi**</span><span class="sxs-lookup"><span data-stu-id="b7005-589">**webapi**</span></span>

<span data-ttu-id="b7005-590">`-au|--auth <AUTHENTICATION_TYPE>`-Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="b7005-590">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="b7005-591">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b7005-591">The possible values are:</span></span>

- <span data-ttu-id="b7005-592">`None`-Kimlik doğrulaması yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="b7005-592">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="b7005-593">`IndividualB2C`-Azure AD B2C ile bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="b7005-593">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="b7005-594">`SingleOrg`-Tek bir kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="b7005-594">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="b7005-595">`Windows`-Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="b7005-595">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="b7005-596">`--aad-b2c-instance <INSTANCE>`-Bağlanılacak Azure Active Directory B2C örneği.</span><span class="sxs-lookup"><span data-stu-id="b7005-596">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="b7005-597">`IndividualB2C` Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7005-597">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="b7005-598">Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b7005-598">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="b7005-599">`-ssp|--susi-policy-id <ID>`-Bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="b7005-599">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="b7005-600">`IndividualB2C` Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7005-600">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b7005-601">`--aad-instance <INSTANCE>`-Bağlanılacak Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="b7005-601">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="b7005-602">`SingleOrg` Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7005-602">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="b7005-603">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b7005-603">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="b7005-604">`--client-id <ID>`-Bu projenin Istemci KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="b7005-604">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="b7005-605">`IndividualB2C` Veya`SingleOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7005-605">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="b7005-606">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b7005-606">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="b7005-607">`--domain <DOMAIN>`-Dizin kiracının etki alanı.</span><span class="sxs-lookup"><span data-stu-id="b7005-607">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="b7005-608">`SingleOrg` Veya`IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7005-608">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="b7005-609">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b7005-609">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="b7005-610">`--tenant-id <ID>`-Bağlanılacak dizinin Tenantıd KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="b7005-610">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="b7005-611">`SingleOrg` Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7005-611">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="b7005-612">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b7005-612">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="b7005-613">`-r|--org-read-access`-Bu uygulamanın dizine okuma erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b7005-613">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="b7005-614">Yalnızca veya `SingleOrg` `MultiOrg` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b7005-614">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="b7005-615">`--exclude-launch-settings`- *Launchsettings. JSON* öğesini oluşturulan şablondan hariç tutun.</span><span class="sxs-lookup"><span data-stu-id="b7005-615">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="b7005-616">`-uld|--use-local-db`-SQLite yerine LocalDB kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b7005-616">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="b7005-617">Yalnızca veya `Individual` `IndividualB2C` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b7005-617">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b7005-618">`--no-restore`-Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="b7005-618">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b7005-619">`--no-https`-Proje HTTPS gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="b7005-619">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="b7005-620">`app.UseHsts`ve `app.UseHttpsRedirection` öğesine`Startup.Configure`eklenmez.</span><span class="sxs-lookup"><span data-stu-id="b7005-620">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="b7005-621">Bu `Individual`seçenek yalnızca `IndividualB2C` `MultiOrg` , ,,veyakullanılmıyorsageçerlidir.`SingleOrg`</span><span class="sxs-lookup"><span data-stu-id="b7005-621">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="b7005-622">**MVC, Razor**</span><span class="sxs-lookup"><span data-stu-id="b7005-622">**mvc, razor**</span></span>

<span data-ttu-id="b7005-623">`-au|--auth <AUTHENTICATION_TYPE>`-Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="b7005-623">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="b7005-624">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b7005-624">The possible values are:</span></span>

- <span data-ttu-id="b7005-625">`None`-Kimlik doğrulaması yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="b7005-625">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="b7005-626">`Individual`-Bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="b7005-626">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="b7005-627">`IndividualB2C`-Azure AD B2C ile bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="b7005-627">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="b7005-628">`SingleOrg`-Tek bir kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="b7005-628">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="b7005-629">`MultiOrg`-Birden çok kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="b7005-629">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="b7005-630">`Windows`-Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="b7005-630">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="b7005-631">`--aad-b2c-instance <INSTANCE>`-Bağlanılacak Azure Active Directory B2C örneği.</span><span class="sxs-lookup"><span data-stu-id="b7005-631">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="b7005-632">`IndividualB2C` Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7005-632">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="b7005-633">Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b7005-633">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="b7005-634">`-ssp|--susi-policy-id <ID>`-Bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="b7005-634">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="b7005-635">`IndividualB2C` Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7005-635">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b7005-636">`-rp|--reset-password-policy-id <ID>`-Bu proje için parola sıfırlama ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="b7005-636">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="b7005-637">`IndividualB2C` Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7005-637">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b7005-638">`-ep|--edit-profile-policy-id <ID>`-Bu proje için profil ilkesi KIMLIĞINI Düzenle.</span><span class="sxs-lookup"><span data-stu-id="b7005-638">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="b7005-639">`IndividualB2C` Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7005-639">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b7005-640">`--aad-instance <INSTANCE>`-Bağlanılacak Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="b7005-640">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="b7005-641">`SingleOrg` Veya`MultiOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7005-641">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="b7005-642">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b7005-642">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="b7005-643">`--client-id <ID>`-Bu projenin Istemci KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="b7005-643">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="b7005-644">`IndividualB2C`, Veyakimlik`MultiOrg`doğrulamasıylakullanın. `SingleOrg`</span><span class="sxs-lookup"><span data-stu-id="b7005-644">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="b7005-645">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b7005-645">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="b7005-646">`--domain <DOMAIN>`-Dizin kiracının etki alanı.</span><span class="sxs-lookup"><span data-stu-id="b7005-646">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="b7005-647">`SingleOrg` Veya`IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7005-647">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="b7005-648">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b7005-648">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="b7005-649">`--tenant-id <ID>`-Bağlanılacak dizinin Tenantıd KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="b7005-649">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="b7005-650">`SingleOrg` Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7005-650">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="b7005-651">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b7005-651">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="b7005-652">`--callback-path <PATH>`-Uygulamanın yeniden yönlendirme URI 'sinin temel yolu içindeki istek yolu.</span><span class="sxs-lookup"><span data-stu-id="b7005-652">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="b7005-653">`SingleOrg` Veya`IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7005-653">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="b7005-654">Varsayılan değer `/signin-oidc` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b7005-654">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="b7005-655">`-r|--org-read-access`-Bu uygulamanın dizine okuma erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b7005-655">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="b7005-656">Yalnızca veya `SingleOrg` `MultiOrg` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b7005-656">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="b7005-657">`--exclude-launch-settings`- *Launchsettings. JSON* öğesini oluşturulan şablondan hariç tutun.</span><span class="sxs-lookup"><span data-stu-id="b7005-657">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="b7005-658">`--use-browserlink`-Projedeki BrowserLink öğesini içerir.</span><span class="sxs-lookup"><span data-stu-id="b7005-658">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="b7005-659">`-uld|--use-local-db`-SQLite yerine LocalDB kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b7005-659">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="b7005-660">Yalnızca veya `Individual` `IndividualB2C` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b7005-660">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b7005-661">`--no-restore`-Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="b7005-661">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b7005-662">`--no-https`-Proje HTTPS gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="b7005-662">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="b7005-663">`app.UseHsts`ve `app.UseHttpsRedirection` öğesine`Startup.Configure`eklenmez.</span><span class="sxs-lookup"><span data-stu-id="b7005-663">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="b7005-664">Bu `Individual`seçenek yalnızca `IndividualB2C` `MultiOrg` , ,,veyakullanılmıyorsageçerlidir.`SingleOrg`</span><span class="sxs-lookup"><span data-stu-id="b7005-664">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="b7005-665">**sayfasında**</span><span class="sxs-lookup"><span data-stu-id="b7005-665">**page**</span></span>

<span data-ttu-id="b7005-666">`-na|--namespace <NAMESPACE_NAME>`-Oluşturulan kod için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="b7005-666">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="b7005-667">Varsayılan değer `MyApp.Namespace` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b7005-667">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="b7005-668">`-np|--no-pagemodel`-Sayfayı PageModel olmadan oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b7005-668">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="b7005-669">**viewıtems 'lar**</span><span class="sxs-lookup"><span data-stu-id="b7005-669">**viewimports**</span></span>

<span data-ttu-id="b7005-670">`-na|--namespace <NAMESPACE_NAME>`-Oluşturulan kod için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="b7005-670">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="b7005-671">Varsayılan değer `MyApp.Namespace` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b7005-671">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="b7005-672">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="b7005-672">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="b7005-673">**konsol, angular, tepki, reactredux**</span><span class="sxs-lookup"><span data-stu-id="b7005-673">**console, angular, react, reactredux**</span></span>

<span data-ttu-id="b7005-674">`--no-restore`-Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="b7005-674">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b7005-675">**projesinin**</span><span class="sxs-lookup"><span data-stu-id="b7005-675">**classlib**</span></span>

<span data-ttu-id="b7005-676">`-f|--framework <FRAMEWORK>`-Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="b7005-676">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="b7005-677">Değerler: `netcoreapp2.0` bir .NET Core sınıf kitaplığı oluşturmak veya `netstandard2.0` bir .NET Standard sınıf kitaplığı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="b7005-677">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="b7005-678">Varsayılan değer `netstandard2.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b7005-678">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="b7005-679">`--no-restore`-Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="b7005-679">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b7005-680">**MSTest, xUnit**</span><span class="sxs-lookup"><span data-stu-id="b7005-680">**mstest, xunit**</span></span>

<span data-ttu-id="b7005-681">`-p|--enable-pack`- [DotNet Pack](dotnet-pack.md)kullanarak proje için paketlemeyi etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="b7005-681">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="b7005-682">`--no-restore`-Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="b7005-682">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b7005-683">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="b7005-683">**globaljson**</span></span>

<span data-ttu-id="b7005-684">`--sdk-version <VERSION_NUMBER>`- *Global. JSON* dosyasında kullanılacak .NET Core SDK sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="b7005-684">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="b7005-685">**Web**</span><span class="sxs-lookup"><span data-stu-id="b7005-685">**web**</span></span>

<span data-ttu-id="b7005-686">`--use-launch-settings`-Oluşturulan şablon çıkışında *Launchsettings. JSON* öğesini içerir.</span><span class="sxs-lookup"><span data-stu-id="b7005-686">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="b7005-687">`--no-restore`-Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="b7005-687">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b7005-688">**WebApi**</span><span class="sxs-lookup"><span data-stu-id="b7005-688">**webapi**</span></span>

<span data-ttu-id="b7005-689">`-au|--auth <AUTHENTICATION_TYPE>`-Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="b7005-689">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="b7005-690">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b7005-690">The possible values are:</span></span>

- <span data-ttu-id="b7005-691">`None`-Kimlik doğrulaması yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="b7005-691">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="b7005-692">`IndividualB2C`-Azure AD B2C ile bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="b7005-692">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="b7005-693">`SingleOrg`-Tek bir kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="b7005-693">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="b7005-694">`Windows`-Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="b7005-694">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="b7005-695">`--aad-b2c-instance <INSTANCE>`-Bağlanılacak Azure Active Directory B2C örneği.</span><span class="sxs-lookup"><span data-stu-id="b7005-695">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="b7005-696">`IndividualB2C` Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7005-696">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="b7005-697">Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b7005-697">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="b7005-698">`-ssp|--susi-policy-id <ID>`-Bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="b7005-698">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="b7005-699">`IndividualB2C` Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7005-699">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b7005-700">`--aad-instance <INSTANCE>`-Bağlanılacak Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="b7005-700">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="b7005-701">`SingleOrg` Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7005-701">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="b7005-702">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b7005-702">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="b7005-703">`--client-id <ID>`-Bu projenin Istemci KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="b7005-703">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="b7005-704">`IndividualB2C` Veya`SingleOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7005-704">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="b7005-705">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b7005-705">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="b7005-706">`--domain <DOMAIN>`-Dizin kiracının etki alanı.</span><span class="sxs-lookup"><span data-stu-id="b7005-706">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="b7005-707">`SingleOrg` Veya`IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7005-707">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="b7005-708">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b7005-708">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="b7005-709">`--tenant-id <ID>`-Bağlanılacak dizinin Tenantıd KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="b7005-709">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="b7005-710">`SingleOrg` Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7005-710">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="b7005-711">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b7005-711">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="b7005-712">`-r|--org-read-access`-Bu uygulamanın dizine okuma erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b7005-712">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="b7005-713">Yalnızca veya `SingleOrg` `MultiOrg` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b7005-713">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="b7005-714">`--use-launch-settings`-Oluşturulan şablon çıkışında *Launchsettings. JSON* öğesini içerir.</span><span class="sxs-lookup"><span data-stu-id="b7005-714">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="b7005-715">`-uld|--use-local-db`-SQLite yerine LocalDB kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b7005-715">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="b7005-716">Yalnızca veya `Individual` `IndividualB2C` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b7005-716">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b7005-717">`--no-restore`-Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="b7005-717">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b7005-718">**MVC, Razor**</span><span class="sxs-lookup"><span data-stu-id="b7005-718">**mvc, razor**</span></span>

<span data-ttu-id="b7005-719">`-au|--auth <AUTHENTICATION_TYPE>`-Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="b7005-719">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="b7005-720">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b7005-720">The possible values are:</span></span>

- <span data-ttu-id="b7005-721">`None`-Kimlik doğrulaması yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="b7005-721">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="b7005-722">`Individual`-Bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="b7005-722">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="b7005-723">`IndividualB2C`-Azure AD B2C ile bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="b7005-723">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="b7005-724">`SingleOrg`-Tek bir kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="b7005-724">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="b7005-725">`MultiOrg`-Birden çok kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="b7005-725">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="b7005-726">`Windows`-Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="b7005-726">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="b7005-727">`--aad-b2c-instance <INSTANCE>`-Bağlanılacak Azure Active Directory B2C örneği.</span><span class="sxs-lookup"><span data-stu-id="b7005-727">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="b7005-728">`IndividualB2C` Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7005-728">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="b7005-729">Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b7005-729">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="b7005-730">`-ssp|--susi-policy-id <ID>`-Bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="b7005-730">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="b7005-731">`IndividualB2C` Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7005-731">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b7005-732">`-rp|--reset-password-policy-id <ID>`-Bu proje için parola sıfırlama ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="b7005-732">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="b7005-733">`IndividualB2C` Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7005-733">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b7005-734">`-ep|--edit-profile-policy-id <ID>`-Bu proje için profil ilkesi KIMLIĞINI Düzenle.</span><span class="sxs-lookup"><span data-stu-id="b7005-734">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="b7005-735">`IndividualB2C` Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7005-735">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b7005-736">`--aad-instance <INSTANCE>`-Bağlanılacak Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="b7005-736">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="b7005-737">`SingleOrg` Veya`MultiOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7005-737">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="b7005-738">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b7005-738">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="b7005-739">`--client-id <ID>`-Bu projenin Istemci KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="b7005-739">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="b7005-740">`IndividualB2C`, Veyakimlik`MultiOrg`doğrulamasıylakullanın. `SingleOrg`</span><span class="sxs-lookup"><span data-stu-id="b7005-740">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="b7005-741">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b7005-741">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="b7005-742">`--domain <DOMAIN>`-Dizin kiracının etki alanı.</span><span class="sxs-lookup"><span data-stu-id="b7005-742">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="b7005-743">`SingleOrg` Veya`IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7005-743">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="b7005-744">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b7005-744">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="b7005-745">`--tenant-id <ID>`-Bağlanılacak dizinin Tenantıd KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="b7005-745">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="b7005-746">`SingleOrg` Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7005-746">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="b7005-747">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b7005-747">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="b7005-748">`--callback-path <PATH>`-Uygulamanın yeniden yönlendirme URI 'sinin temel yolu içindeki istek yolu.</span><span class="sxs-lookup"><span data-stu-id="b7005-748">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="b7005-749">`SingleOrg` Veya`IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7005-749">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="b7005-750">Varsayılan değer `/signin-oidc` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b7005-750">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="b7005-751">`-r|--org-read-access`-Bu uygulamanın dizine okuma erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b7005-751">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="b7005-752">Yalnızca veya `SingleOrg` `MultiOrg` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b7005-752">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="b7005-753">`--use-launch-settings`-Oluşturulan şablon çıkışında *Launchsettings. JSON* öğesini içerir.</span><span class="sxs-lookup"><span data-stu-id="b7005-753">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="b7005-754">`--use-browserlink`-Projedeki BrowserLink öğesini içerir.</span><span class="sxs-lookup"><span data-stu-id="b7005-754">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="b7005-755">`-uld|--use-local-db`-SQLite yerine LocalDB kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b7005-755">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="b7005-756">Yalnızca veya `Individual` `IndividualB2C` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b7005-756">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b7005-757">`--no-restore`-Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="b7005-757">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b7005-758">**sayfasında**</span><span class="sxs-lookup"><span data-stu-id="b7005-758">**page**</span></span>

<span data-ttu-id="b7005-759">`-na|--namespace <NAMESPACE_NAME>`-Oluşturulan kod için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="b7005-759">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="b7005-760">Varsayılan değer `MyApp.Namespace` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b7005-760">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="b7005-761">`-np|--no-pagemodel`-Sayfayı PageModel olmadan oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b7005-761">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="b7005-762">**viewıtems 'lar**</span><span class="sxs-lookup"><span data-stu-id="b7005-762">**viewimports**</span></span>

<span data-ttu-id="b7005-763">`-na|--namespace <NAMESPACE_NAME>`-Oluşturulan kod için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="b7005-763">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="b7005-764">Varsayılan değer `MyApp.Namespace` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b7005-764">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="b7005-765">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="b7005-765">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="b7005-766">**konsol, xUnit, MSTest, Web, WebApi**</span><span class="sxs-lookup"><span data-stu-id="b7005-766">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="b7005-767">`-f|--framework <FRAMEWORK>`-Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="b7005-767">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="b7005-768">Değerler: `netcoreapp1.0` veya `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="b7005-768">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="b7005-769">Varsayılan değer `netcoreapp1.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b7005-769">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="b7005-770">**projesinin**</span><span class="sxs-lookup"><span data-stu-id="b7005-770">**classlib**</span></span>

<span data-ttu-id="b7005-771">`-f|--framework <FRAMEWORK>`-Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="b7005-771">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="b7005-772">Değerler: `netcoreapp1.0`, `netcoreapp1.1`, veya `netstandard1.0` .`netstandard1.6`</span><span class="sxs-lookup"><span data-stu-id="b7005-772">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="b7005-773">Varsayılan değer `netstandard1.4` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b7005-773">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="b7005-774">**mvc**</span><span class="sxs-lookup"><span data-stu-id="b7005-774">**mvc**</span></span>

<span data-ttu-id="b7005-775">`-f|--framework <FRAMEWORK>`-Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="b7005-775">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="b7005-776">Değerler: `netcoreapp1.0` veya `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="b7005-776">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="b7005-777">Varsayılan değer `netcoreapp1.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b7005-777">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="b7005-778">`-au|--auth <AUTHENTICATION_TYPE>`-Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="b7005-778">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="b7005-779">Değerler: `None` veya `Individual`.</span><span class="sxs-lookup"><span data-stu-id="b7005-779">Values: `None` or `Individual`.</span></span> <span data-ttu-id="b7005-780">Varsayılan değer `None` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b7005-780">The default value is `None`.</span></span>

<span data-ttu-id="b7005-781">`-uld|--use-local-db`-SQLite yerine LocalDB kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b7005-781">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="b7005-782">Değerler: `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="b7005-782">Values: `true` or `false`.</span></span> <span data-ttu-id="b7005-783">Varsayılan değer `false` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b7005-783">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="b7005-784">Örnekler</span><span class="sxs-lookup"><span data-stu-id="b7005-784">Examples</span></span>

<span data-ttu-id="b7005-785">Şablon adını C# belirterek bir konsol uygulaması projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="b7005-785">Create a C# console application project by specifying the template name:</span></span>

`dotnet new "Console Application"`

<span data-ttu-id="b7005-786">Geçerli dizinde F# bir konsol uygulaması projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="b7005-786">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="b7005-787">Belirtilen dizinde bir .NET Standard sınıf kitaplığı projesi oluşturun (yalnızca .NET Core SDK 2,0 veya sonraki sürümlerle kullanılabilir):</span><span class="sxs-lookup"><span data-stu-id="b7005-787">Create a .NET Standard class library project in the specified directory (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="b7005-788">Geçerli dizinde kimlik doğrulaması C# olmadan yeni bir ASP.NET Core MVC projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="b7005-788">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

`dotnet new mvc -au None`

<span data-ttu-id="b7005-789">Yeni bir xUnit projesi oluştur:</span><span class="sxs-lookup"><span data-stu-id="b7005-789">Create a new xUnit project:</span></span>

`dotnet new xunit`

<span data-ttu-id="b7005-790">MVC için kullanılabilen tüm şablonları listeleyin:</span><span class="sxs-lookup"><span data-stu-id="b7005-790">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="b7005-791">*We* alt dizeniz ile eşleşen tüm şablonları listeleyin.</span><span class="sxs-lookup"><span data-stu-id="b7005-791">List all templates matching the *we* substring.</span></span> <span data-ttu-id="b7005-792">Tam eşleşme bulunamadı, bu nedenle alt dize eşleştirmesi hem kısa ad hem de ad sütunlarında çalışır.</span><span class="sxs-lookup"><span data-stu-id="b7005-792">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

`dotnet new we -l`

<span data-ttu-id="b7005-793">Şablonla *eşleşen şablonu*çağırma girişimi.</span><span class="sxs-lookup"><span data-stu-id="b7005-793">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="b7005-794">Tek bir eşleşme belirlenemiyorsa kısmi eşleşen şablonları listeleyin.</span><span class="sxs-lookup"><span data-stu-id="b7005-794">If a single match can't be determined, list the templates that are partial matches.</span></span>

`dotnet new ng`

<span data-ttu-id="b7005-795">ASP.NET Core için tek sayfalı uygulama şablonlarının 2,0 sürümünü (yalnızca .NET Core SDK 1,1 ve sonraki sürümler için kullanılabilir) (komut seçeneği) yükler:</span><span class="sxs-lookup"><span data-stu-id="b7005-795">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

<span data-ttu-id="b7005-796">SDK sürümü 2.0.0 (yalnızca .NET Core SDK 2,0 veya üzeri sürümlerle kullanılabilir) ayarı geçerli dizinde *Global. JSON* oluşturun:</span><span class="sxs-lookup"><span data-stu-id="b7005-796">Create a *global.json* in the current directory setting the SDK version to 2.0.0 (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="b7005-797">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b7005-797">See also</span></span>

- [<span data-ttu-id="b7005-798">DotNet New için özel şablonlar</span><span class="sxs-lookup"><span data-stu-id="b7005-798">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="b7005-799">Dotnet new için özel şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="b7005-799">Create a custom template for dotnet new</span></span>](../tutorials/create-custom-template.md)
- [<span data-ttu-id="b7005-800">DotNet/DotNet-şablon-örnek GitHub deposu</span><span class="sxs-lookup"><span data-stu-id="b7005-800">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="b7005-801">DotNet New için kullanılabilir şablonlar</span><span class="sxs-lookup"><span data-stu-id="b7005-801">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
