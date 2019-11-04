---
title: DotNet yeni komut
description: DotNet New komutu, belirtilen şablona göre yeni .NET Core projeleri oluşturur.
ms.date: 05/06/2019
ms.openlocfilehash: c9529e135f48c80f445c91038294a3e7266486f1
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73420472"
---
# <a name="dotnet-new"></a><span data-ttu-id="4a225-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="4a225-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="4a225-104">Name</span><span class="sxs-lookup"><span data-stu-id="4a225-104">Name</span></span>

<span data-ttu-id="4a225-105">`dotnet new`-belirtilen şablona göre yeni bir proje, yapılandırma dosyası veya çözüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4a225-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="4a225-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="4a225-106">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="4a225-107">.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="4a225-107">.NET Core 2.2</span></span>](#tab/netcore22)

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="4a225-108">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="4a225-108">.NET Core 2.1</span></span>](#tab/netcore21)

```dotnetcli
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="4a225-109">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="4a225-109">.NET Core 2.0</span></span>](#tab/netcore20)

```dotnetcli
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="4a225-110">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="4a225-110">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="4a225-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4a225-111">Description</span></span>

<span data-ttu-id="4a225-112">`dotnet new` komutu, geçerli bir .NET Core projesi başlatmak için kullanışlı bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="4a225-112">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="4a225-113">Komutu, belirtilen şablon ve seçeneklere göre diskteki yapıtları oluşturmak için [şablon altyapısını](https://github.com/dotnet/templating) çağırır.</span><span class="sxs-lookup"><span data-stu-id="4a225-113">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="4a225-114">Arguments</span><span class="sxs-lookup"><span data-stu-id="4a225-114">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="4a225-115">Komut çağrıldığında örnek oluşturulacak şablon.</span><span class="sxs-lookup"><span data-stu-id="4a225-115">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="4a225-116">Her şablonun geçirebilmeniz için özel seçenekleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="4a225-116">Each template might have specific options you can pass.</span></span> <span data-ttu-id="4a225-117">Daha fazla bilgi için bkz. [şablon seçenekleri](#template-options).</span><span class="sxs-lookup"><span data-stu-id="4a225-117">For more information, see [Template options](#template-options).</span></span>

<span data-ttu-id="4a225-118">`TEMPLATE` değeri **Şablonlar** veya **kısa ad** sütunundaki metin üzerinde tam eşleşme değilse, bu iki sütunda bir alt dize eşleşmesi gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="4a225-118">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column, a substring match is performed on those two columns.</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="4a225-119">.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="4a225-119">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="4a225-120">Komut, şablonların varsayılan bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="4a225-120">The command contains a default list of templates.</span></span> <span data-ttu-id="4a225-121">Kullanılabilir şablonların bir listesini almak için `dotnet new -l` kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a225-121">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="4a225-122">Aşağıdaki tabloda, .NET Core SDK 2.2.100 ile önceden yüklenmiş olarak gelen şablonlar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4a225-122">The following table shows the templates that come pre-installed with the .NET Core SDK 2.2.100.</span></span> <span data-ttu-id="4a225-123">Şablon için varsayılan dil, köşeli ayraçlar içinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="4a225-123">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="4a225-124">Şablonlar</span><span class="sxs-lookup"><span data-stu-id="4a225-124">Templates</span></span>                                    | <span data-ttu-id="4a225-125">Kısa Ad</span><span class="sxs-lookup"><span data-stu-id="4a225-125">Short Name</span></span>        | <span data-ttu-id="4a225-126">Dil</span><span class="sxs-lookup"><span data-stu-id="4a225-126">Language</span></span>     | <span data-ttu-id="4a225-127">Etiketler</span><span class="sxs-lookup"><span data-stu-id="4a225-127">Tags</span></span>                                  |
|----------------------------------------------|-------------------|--------------|---------------------------------------|
| <span data-ttu-id="4a225-128">Konsol Uygulaması</span><span class="sxs-lookup"><span data-stu-id="4a225-128">Console Application</span></span>                          | `console`         | <span data-ttu-id="4a225-129">[C#], F#Vb.</span><span class="sxs-lookup"><span data-stu-id="4a225-129">[C#], F#, VB</span></span> | <span data-ttu-id="4a225-130">Ortak/konsol</span><span class="sxs-lookup"><span data-stu-id="4a225-130">Common/Console</span></span>                        |
| <span data-ttu-id="4a225-131">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="4a225-131">Class library</span></span>                                | `classlib`        | <span data-ttu-id="4a225-132">[C#], F#Vb.</span><span class="sxs-lookup"><span data-stu-id="4a225-132">[C#], F#, VB</span></span> | <span data-ttu-id="4a225-133">Ortak/Kitaplık</span><span class="sxs-lookup"><span data-stu-id="4a225-133">Common/Library</span></span>                        |
| <span data-ttu-id="4a225-134">Birim testi projesi</span><span class="sxs-lookup"><span data-stu-id="4a225-134">Unit Test Project</span></span>                            | `mstest`          | <span data-ttu-id="4a225-135">[C#], F#Vb.</span><span class="sxs-lookup"><span data-stu-id="4a225-135">[C#], F#, VB</span></span> | <span data-ttu-id="4a225-136">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="4a225-136">Test/MSTest</span></span>                           |
| <span data-ttu-id="4a225-137">NUnit 3 test projesi</span><span class="sxs-lookup"><span data-stu-id="4a225-137">NUnit 3 Test Project</span></span>                         | `nunit`           | <span data-ttu-id="4a225-138">[C#], F#Vb.</span><span class="sxs-lookup"><span data-stu-id="4a225-138">[C#], F#, VB</span></span> | <span data-ttu-id="4a225-139">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="4a225-139">Test/NUnit</span></span>                            |
| <span data-ttu-id="4a225-140">NUnit 3 test öğesi</span><span class="sxs-lookup"><span data-stu-id="4a225-140">NUnit 3 Test Item</span></span>                            | `nunit-test`      | <span data-ttu-id="4a225-141">[C#], F#Vb.</span><span class="sxs-lookup"><span data-stu-id="4a225-141">[C#], F#, VB</span></span> | <span data-ttu-id="4a225-142">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="4a225-142">Test/NUnit</span></span>                            |
| <span data-ttu-id="4a225-143">xUnit test projesi</span><span class="sxs-lookup"><span data-stu-id="4a225-143">xUnit Test Project</span></span>                           | `xunit`           | <span data-ttu-id="4a225-144">[C#], F#Vb.</span><span class="sxs-lookup"><span data-stu-id="4a225-144">[C#], F#, VB</span></span> | <span data-ttu-id="4a225-145">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="4a225-145">Test/xUnit</span></span>                            |
| <span data-ttu-id="4a225-146">Razor sayfası</span><span class="sxs-lookup"><span data-stu-id="4a225-146">Razor Page</span></span>                                   | `page`            | <span data-ttu-id="4a225-147">[C#]</span><span class="sxs-lookup"><span data-stu-id="4a225-147">[C#]</span></span>         | <span data-ttu-id="4a225-148">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="4a225-148">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="4a225-149">MVC Viewıtemts</span><span class="sxs-lookup"><span data-stu-id="4a225-149">MVC ViewImports</span></span>                              | `viewimports`     | <span data-ttu-id="4a225-150">[C#]</span><span class="sxs-lookup"><span data-stu-id="4a225-150">[C#]</span></span>         | <span data-ttu-id="4a225-151">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="4a225-151">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="4a225-152">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="4a225-152">MVC ViewStart</span></span>                                | `viewstart`       | <span data-ttu-id="4a225-153">[C#]</span><span class="sxs-lookup"><span data-stu-id="4a225-153">[C#]</span></span>         | <span data-ttu-id="4a225-154">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="4a225-154">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="4a225-155">ASP.NET Core boş</span><span class="sxs-lookup"><span data-stu-id="4a225-155">ASP.NET Core Empty</span></span>                           | `web`             | <span data-ttu-id="4a225-156">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="4a225-156">[C#], F#</span></span>     | <span data-ttu-id="4a225-157">Web/boş</span><span class="sxs-lookup"><span data-stu-id="4a225-157">Web/Empty</span></span>                             |
| <span data-ttu-id="4a225-158">ASP.NET Core Web uygulaması (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="4a225-158">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`             | <span data-ttu-id="4a225-159">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="4a225-159">[C#], F#</span></span>     | <span data-ttu-id="4a225-160">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="4a225-160">Web/MVC</span></span>                               |
| <span data-ttu-id="4a225-161">ASP.NET Core Web uygulaması</span><span class="sxs-lookup"><span data-stu-id="4a225-161">ASP.NET Core Web App</span></span>                         | <span data-ttu-id="4a225-162">`webapp`, `razor`</span><span class="sxs-lookup"><span data-stu-id="4a225-162">`webapp`, `razor`</span></span> | <span data-ttu-id="4a225-163">[C#]</span><span class="sxs-lookup"><span data-stu-id="4a225-163">[C#]</span></span>         | <span data-ttu-id="4a225-164">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="4a225-164">Web/MVC/Razor Pages</span></span>                   |
| <span data-ttu-id="4a225-165">Angular ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4a225-165">ASP.NET Core with Angular</span></span>                    | `angular`         | <span data-ttu-id="4a225-166">[C#]</span><span class="sxs-lookup"><span data-stu-id="4a225-166">[C#]</span></span>         | <span data-ttu-id="4a225-167">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="4a225-167">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="4a225-168">Tepki verme. js ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4a225-168">ASP.NET Core with React.js</span></span>                   | `react`           | <span data-ttu-id="4a225-169">[C#]</span><span class="sxs-lookup"><span data-stu-id="4a225-169">[C#]</span></span>         | <span data-ttu-id="4a225-170">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="4a225-170">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="4a225-171">Yanıt verir. js ve Redux ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4a225-171">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`      | <span data-ttu-id="4a225-172">[C#]</span><span class="sxs-lookup"><span data-stu-id="4a225-172">[C#]</span></span>         | <span data-ttu-id="4a225-173">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="4a225-173">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="4a225-174">Razor sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="4a225-174">Razor Class Library</span></span>                          | `razorclasslib`   | <span data-ttu-id="4a225-175">[C#]</span><span class="sxs-lookup"><span data-stu-id="4a225-175">[C#]</span></span>         | <span data-ttu-id="4a225-176">Web/Razor/kitaplık/Razor sınıfı kitaplığı</span><span class="sxs-lookup"><span data-stu-id="4a225-176">Web/Razor/Library/Razor Class Library</span></span> |
| <span data-ttu-id="4a225-177">ASP.NET Core Web API 'SI</span><span class="sxs-lookup"><span data-stu-id="4a225-177">ASP.NET Core Web API</span></span>                         | `webapi`          | <span data-ttu-id="4a225-178">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="4a225-178">[C#], F#</span></span>     | <span data-ttu-id="4a225-179">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="4a225-179">Web/WebAPI</span></span>                            |
| <span data-ttu-id="4a225-180">Global. JSON dosyası</span><span class="sxs-lookup"><span data-stu-id="4a225-180">global.json file</span></span>                             | `globaljson`      |              | <span data-ttu-id="4a225-181">Config</span><span class="sxs-lookup"><span data-stu-id="4a225-181">Config</span></span>                                |
| <span data-ttu-id="4a225-182">NuGet yapılandırması</span><span class="sxs-lookup"><span data-stu-id="4a225-182">NuGet Config</span></span>                                 | `nugetconfig`     |              | <span data-ttu-id="4a225-183">Config</span><span class="sxs-lookup"><span data-stu-id="4a225-183">Config</span></span>                                |
| <span data-ttu-id="4a225-184">Web yapılandırması</span><span class="sxs-lookup"><span data-stu-id="4a225-184">Web Config</span></span>                                   | `webconfig`       |              | <span data-ttu-id="4a225-185">Config</span><span class="sxs-lookup"><span data-stu-id="4a225-185">Config</span></span>                                |
| <span data-ttu-id="4a225-186">Çözüm dosyası</span><span class="sxs-lookup"><span data-stu-id="4a225-186">Solution File</span></span>                                | `sln`             |              | <span data-ttu-id="4a225-187">Çözüm</span><span class="sxs-lookup"><span data-stu-id="4a225-187">Solution</span></span>                              |

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="4a225-188">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="4a225-188">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="4a225-189">Komut, şablonların varsayılan bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="4a225-189">The command contains a default list of templates.</span></span> <span data-ttu-id="4a225-190">Kullanılabilir şablonların bir listesini almak için `dotnet new -l` kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a225-190">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="4a225-191">Aşağıdaki tabloda, .NET Core SDK 2.1.300 ile önceden yüklenmiş olarak gelen şablonlar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4a225-191">The following table shows the templates that come pre-installed with the .NET Core SDK 2.1.300.</span></span> <span data-ttu-id="4a225-192">Şablon için varsayılan dil, köşeli ayraçlar içinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="4a225-192">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="4a225-193">Şablonlar</span><span class="sxs-lookup"><span data-stu-id="4a225-193">Templates</span></span>                                    | <span data-ttu-id="4a225-194">Kısa Ad</span><span class="sxs-lookup"><span data-stu-id="4a225-194">Short Name</span></span>      | <span data-ttu-id="4a225-195">Dil</span><span class="sxs-lookup"><span data-stu-id="4a225-195">Language</span></span>     | <span data-ttu-id="4a225-196">Etiketler</span><span class="sxs-lookup"><span data-stu-id="4a225-196">Tags</span></span>                                  |
|----------------------------------------------|-----------------|--------------|---------------------------------------|
| <span data-ttu-id="4a225-197">Konsol Uygulaması</span><span class="sxs-lookup"><span data-stu-id="4a225-197">Console Application</span></span>                          | `console`       | <span data-ttu-id="4a225-198">[C#], F#Vb.</span><span class="sxs-lookup"><span data-stu-id="4a225-198">[C#], F#, VB</span></span> | <span data-ttu-id="4a225-199">Ortak/konsol</span><span class="sxs-lookup"><span data-stu-id="4a225-199">Common/Console</span></span>                        |
| <span data-ttu-id="4a225-200">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="4a225-200">Class library</span></span>                                | `classlib`      | <span data-ttu-id="4a225-201">[C#], F#Vb.</span><span class="sxs-lookup"><span data-stu-id="4a225-201">[C#], F#, VB</span></span> | <span data-ttu-id="4a225-202">Ortak/Kitaplık</span><span class="sxs-lookup"><span data-stu-id="4a225-202">Common/Library</span></span>                        |
| <span data-ttu-id="4a225-203">Birim testi projesi</span><span class="sxs-lookup"><span data-stu-id="4a225-203">Unit Test Project</span></span>                            | `mstest`        | <span data-ttu-id="4a225-204">[C#], F#Vb.</span><span class="sxs-lookup"><span data-stu-id="4a225-204">[C#], F#, VB</span></span> | <span data-ttu-id="4a225-205">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="4a225-205">Test/MSTest</span></span>                           |
| <span data-ttu-id="4a225-206">xUnit test projesi</span><span class="sxs-lookup"><span data-stu-id="4a225-206">xUnit Test Project</span></span>                           | `xunit`         | <span data-ttu-id="4a225-207">[C#], F#Vb.</span><span class="sxs-lookup"><span data-stu-id="4a225-207">[C#], F#, VB</span></span> | <span data-ttu-id="4a225-208">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="4a225-208">Test/xUnit</span></span>                            |
| <span data-ttu-id="4a225-209">Razor sayfası</span><span class="sxs-lookup"><span data-stu-id="4a225-209">Razor Page</span></span>                                   | `page`          | <span data-ttu-id="4a225-210">[C#]</span><span class="sxs-lookup"><span data-stu-id="4a225-210">[C#]</span></span>         | <span data-ttu-id="4a225-211">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="4a225-211">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="4a225-212">MVC Viewıtemts</span><span class="sxs-lookup"><span data-stu-id="4a225-212">MVC ViewImports</span></span>                              | `viewimports`   | <span data-ttu-id="4a225-213">[C#]</span><span class="sxs-lookup"><span data-stu-id="4a225-213">[C#]</span></span>         | <span data-ttu-id="4a225-214">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="4a225-214">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="4a225-215">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="4a225-215">MVC ViewStart</span></span>                                | `viewstart`     | <span data-ttu-id="4a225-216">[C#]</span><span class="sxs-lookup"><span data-stu-id="4a225-216">[C#]</span></span>         | <span data-ttu-id="4a225-217">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="4a225-217">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="4a225-218">ASP.NET Core boş</span><span class="sxs-lookup"><span data-stu-id="4a225-218">ASP.NET Core Empty</span></span>                           | `web`           | <span data-ttu-id="4a225-219">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="4a225-219">[C#], F#</span></span>     | <span data-ttu-id="4a225-220">Web/boş</span><span class="sxs-lookup"><span data-stu-id="4a225-220">Web/Empty</span></span>                             |
| <span data-ttu-id="4a225-221">ASP.NET Core Web uygulaması (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="4a225-221">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`           | <span data-ttu-id="4a225-222">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="4a225-222">[C#], F#</span></span>     | <span data-ttu-id="4a225-223">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="4a225-223">Web/MVC</span></span>                               |
| <span data-ttu-id="4a225-224">ASP.NET Core Web uygulaması</span><span class="sxs-lookup"><span data-stu-id="4a225-224">ASP.NET Core Web App</span></span>                         | `razor`         | <span data-ttu-id="4a225-225">[C#]</span><span class="sxs-lookup"><span data-stu-id="4a225-225">[C#]</span></span>         | <span data-ttu-id="4a225-226">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="4a225-226">Web/MVC/Razor Pages</span></span>                   |
| <span data-ttu-id="4a225-227">Angular ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4a225-227">ASP.NET Core with Angular</span></span>                    | `angular`       | <span data-ttu-id="4a225-228">[C#]</span><span class="sxs-lookup"><span data-stu-id="4a225-228">[C#]</span></span>         | <span data-ttu-id="4a225-229">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="4a225-229">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="4a225-230">Tepki verme. js ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4a225-230">ASP.NET Core with React.js</span></span>                   | `react`         | <span data-ttu-id="4a225-231">[C#]</span><span class="sxs-lookup"><span data-stu-id="4a225-231">[C#]</span></span>         | <span data-ttu-id="4a225-232">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="4a225-232">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="4a225-233">Yanıt verir. js ve Redux ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4a225-233">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`    | <span data-ttu-id="4a225-234">[C#]</span><span class="sxs-lookup"><span data-stu-id="4a225-234">[C#]</span></span>         | <span data-ttu-id="4a225-235">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="4a225-235">Web/MVC/SPA</span></span>                           | 
| <span data-ttu-id="4a225-236">Razor sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="4a225-236">Razor Class Library</span></span>                          | `razorclasslib` | <span data-ttu-id="4a225-237">[C#]</span><span class="sxs-lookup"><span data-stu-id="4a225-237">[C#]</span></span>         | <span data-ttu-id="4a225-238">Web/Razor/kitaplık/Razor sınıfı kitaplığı</span><span class="sxs-lookup"><span data-stu-id="4a225-238">Web/Razor/Library/Razor Class Library</span></span> |
| <span data-ttu-id="4a225-239">ASP.NET Core Web API 'SI</span><span class="sxs-lookup"><span data-stu-id="4a225-239">ASP.NET Core Web API</span></span>                         | `webapi`        | <span data-ttu-id="4a225-240">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="4a225-240">[C#], F#</span></span>     | <span data-ttu-id="4a225-241">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="4a225-241">Web/WebAPI</span></span>                            |
| <span data-ttu-id="4a225-242">Global. JSON dosyası</span><span class="sxs-lookup"><span data-stu-id="4a225-242">global.json file</span></span>                             | `globaljson`    |              | <span data-ttu-id="4a225-243">Config</span><span class="sxs-lookup"><span data-stu-id="4a225-243">Config</span></span>                                |
| <span data-ttu-id="4a225-244">NuGet yapılandırması</span><span class="sxs-lookup"><span data-stu-id="4a225-244">NuGet Config</span></span>                                 | `nugetconfig`   |              | <span data-ttu-id="4a225-245">Config</span><span class="sxs-lookup"><span data-stu-id="4a225-245">Config</span></span>                                |
| <span data-ttu-id="4a225-246">Web yapılandırması</span><span class="sxs-lookup"><span data-stu-id="4a225-246">Web Config</span></span>                                   | `webconfig`     |              | <span data-ttu-id="4a225-247">Config</span><span class="sxs-lookup"><span data-stu-id="4a225-247">Config</span></span>                                |
| <span data-ttu-id="4a225-248">Çözüm dosyası</span><span class="sxs-lookup"><span data-stu-id="4a225-248">Solution File</span></span>                                | `sln`           |              | <span data-ttu-id="4a225-249">Çözüm</span><span class="sxs-lookup"><span data-stu-id="4a225-249">Solution</span></span>                              |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="4a225-250">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="4a225-250">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="4a225-251">Komut, şablonların varsayılan bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="4a225-251">The command contains a default list of templates.</span></span> <span data-ttu-id="4a225-252">Kullanılabilir şablonların bir listesini almak için `dotnet new -l` kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a225-252">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="4a225-253">Aşağıdaki tabloda, .NET Core SDK 2.0.0 ile önceden yüklenmiş olarak gelen şablonlar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4a225-253">The following table shows the templates that come pre-installed with the .NET Core SDK 2.0.0.</span></span> <span data-ttu-id="4a225-254">Şablon için varsayılan dil, köşeli ayraçlar içinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="4a225-254">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="4a225-255">Şablonlar</span><span class="sxs-lookup"><span data-stu-id="4a225-255">Templates</span></span>                                    | <span data-ttu-id="4a225-256">Kısa Ad</span><span class="sxs-lookup"><span data-stu-id="4a225-256">Short Name</span></span>    | <span data-ttu-id="4a225-257">Dil</span><span class="sxs-lookup"><span data-stu-id="4a225-257">Language</span></span>     | <span data-ttu-id="4a225-258">Etiketler</span><span class="sxs-lookup"><span data-stu-id="4a225-258">Tags</span></span>                |
|----------------------------------------------|---------------|--------------|---------------------|
| <span data-ttu-id="4a225-259">Konsol Uygulaması</span><span class="sxs-lookup"><span data-stu-id="4a225-259">Console Application</span></span>                          | `console`     | <span data-ttu-id="4a225-260">[C#], F#Vb.</span><span class="sxs-lookup"><span data-stu-id="4a225-260">[C#], F#, VB</span></span> | <span data-ttu-id="4a225-261">Ortak/konsol</span><span class="sxs-lookup"><span data-stu-id="4a225-261">Common/Console</span></span>      |
| <span data-ttu-id="4a225-262">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="4a225-262">Class library</span></span>                                | `classlib`    | <span data-ttu-id="4a225-263">[C#], F#Vb.</span><span class="sxs-lookup"><span data-stu-id="4a225-263">[C#], F#, VB</span></span> | <span data-ttu-id="4a225-264">Ortak/Kitaplık</span><span class="sxs-lookup"><span data-stu-id="4a225-264">Common/Library</span></span>      |
| <span data-ttu-id="4a225-265">Birim testi projesi</span><span class="sxs-lookup"><span data-stu-id="4a225-265">Unit Test Project</span></span>                            | `mstest`      | <span data-ttu-id="4a225-266">[C#], F#Vb.</span><span class="sxs-lookup"><span data-stu-id="4a225-266">[C#], F#, VB</span></span> | <span data-ttu-id="4a225-267">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="4a225-267">Test/MSTest</span></span>         |
| <span data-ttu-id="4a225-268">xUnit test projesi</span><span class="sxs-lookup"><span data-stu-id="4a225-268">xUnit Test Project</span></span>                           | `xunit`       | <span data-ttu-id="4a225-269">[C#], F#Vb.</span><span class="sxs-lookup"><span data-stu-id="4a225-269">[C#], F#, VB</span></span> | <span data-ttu-id="4a225-270">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="4a225-270">Test/xUnit</span></span>          |
| <span data-ttu-id="4a225-271">ASP.NET Core boş</span><span class="sxs-lookup"><span data-stu-id="4a225-271">ASP.NET Core Empty</span></span>                           | `web`         | <span data-ttu-id="4a225-272">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="4a225-272">[C#], F#</span></span>     | <span data-ttu-id="4a225-273">Web/boş</span><span class="sxs-lookup"><span data-stu-id="4a225-273">Web/Empty</span></span>           |
| <span data-ttu-id="4a225-274">ASP.NET Core Web uygulaması (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="4a225-274">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="4a225-275">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="4a225-275">[C#], F#</span></span>     | <span data-ttu-id="4a225-276">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="4a225-276">Web/MVC</span></span>             |
| <span data-ttu-id="4a225-277">ASP.NET Core Web uygulaması</span><span class="sxs-lookup"><span data-stu-id="4a225-277">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="4a225-278">[C#]</span><span class="sxs-lookup"><span data-stu-id="4a225-278">[C#]</span></span>         | <span data-ttu-id="4a225-279">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="4a225-279">Web/MVC/Razor Pages</span></span> |
| <span data-ttu-id="4a225-280">Angular ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4a225-280">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="4a225-281">[C#]</span><span class="sxs-lookup"><span data-stu-id="4a225-281">[C#]</span></span>         | <span data-ttu-id="4a225-282">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="4a225-282">Web/MVC/SPA</span></span>         |
| <span data-ttu-id="4a225-283">Tepki verme. js ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4a225-283">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="4a225-284">[C#]</span><span class="sxs-lookup"><span data-stu-id="4a225-284">[C#]</span></span>         | <span data-ttu-id="4a225-285">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="4a225-285">Web/MVC/SPA</span></span>         |
| <span data-ttu-id="4a225-286">Yanıt verir. js ve Redux ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4a225-286">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="4a225-287">[C#]</span><span class="sxs-lookup"><span data-stu-id="4a225-287">[C#]</span></span>         | <span data-ttu-id="4a225-288">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="4a225-288">Web/MVC/SPA</span></span>         |
| <span data-ttu-id="4a225-289">ASP.NET Core Web API 'SI</span><span class="sxs-lookup"><span data-stu-id="4a225-289">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="4a225-290">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="4a225-290">[C#], F#</span></span>     | <span data-ttu-id="4a225-291">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="4a225-291">Web/WebAPI</span></span>          |
| <span data-ttu-id="4a225-292">Global. JSON dosyası</span><span class="sxs-lookup"><span data-stu-id="4a225-292">global.json file</span></span>                             | `globaljson`  |              | <span data-ttu-id="4a225-293">Config</span><span class="sxs-lookup"><span data-stu-id="4a225-293">Config</span></span>              |
| <span data-ttu-id="4a225-294">NuGet yapılandırması</span><span class="sxs-lookup"><span data-stu-id="4a225-294">Nuget Config</span></span>                                 | `nugetconfig` |              | <span data-ttu-id="4a225-295">Config</span><span class="sxs-lookup"><span data-stu-id="4a225-295">Config</span></span>              |
| <span data-ttu-id="4a225-296">Web yapılandırması</span><span class="sxs-lookup"><span data-stu-id="4a225-296">Web Config</span></span>                                   | `webconfig`   |              | <span data-ttu-id="4a225-297">Config</span><span class="sxs-lookup"><span data-stu-id="4a225-297">Config</span></span>              |
| <span data-ttu-id="4a225-298">Çözüm dosyası</span><span class="sxs-lookup"><span data-stu-id="4a225-298">Solution File</span></span>                                | `sln`         |              | <span data-ttu-id="4a225-299">Çözüm</span><span class="sxs-lookup"><span data-stu-id="4a225-299">Solution</span></span>            |
| <span data-ttu-id="4a225-300">Razor sayfası</span><span class="sxs-lookup"><span data-stu-id="4a225-300">Razor Page</span></span>                                   | `page`        |              | <span data-ttu-id="4a225-301">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="4a225-301">Web/ASP.NET</span></span>         |
| <span data-ttu-id="4a225-302">MVC Viewıtemts</span><span class="sxs-lookup"><span data-stu-id="4a225-302">MVC ViewImports</span></span>                              | `viewimports` |              | <span data-ttu-id="4a225-303">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="4a225-303">Web/ASP.NET</span></span>         |
| <span data-ttu-id="4a225-304">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="4a225-304">MVC ViewStart</span></span>                                | `viewstart`   |              | <span data-ttu-id="4a225-305">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="4a225-305">Web/ASP.NET</span></span>         |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="4a225-306">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="4a225-306">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="4a225-307">Komut, şablonların varsayılan bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="4a225-307">The command contains a default list of templates.</span></span> <span data-ttu-id="4a225-308">Kullanılabilir şablonların bir listesini almak için `dotnet new -all` kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a225-308">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="4a225-309">Aşağıdaki tabloda, .NET Core SDK 1.0.1 ile önceden yüklenmiş olarak gelen şablonlar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4a225-309">The following table shows the templates that come pre-installed with the .NET Core SDK 1.0.1.</span></span> <span data-ttu-id="4a225-310">Şablon için varsayılan dil, köşeli ayraçlar içinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="4a225-310">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="4a225-311">Şablonlar</span><span class="sxs-lookup"><span data-stu-id="4a225-311">Templates</span></span>            | <span data-ttu-id="4a225-312">Kısa Ad</span><span class="sxs-lookup"><span data-stu-id="4a225-312">Short Name</span></span>    | <span data-ttu-id="4a225-313">Dil</span><span class="sxs-lookup"><span data-stu-id="4a225-313">Language</span></span> | <span data-ttu-id="4a225-314">Etiketler</span><span class="sxs-lookup"><span data-stu-id="4a225-314">Tags</span></span>           |
|----------------------|---------------|----------|----------------|
| <span data-ttu-id="4a225-315">Konsol Uygulaması</span><span class="sxs-lookup"><span data-stu-id="4a225-315">Console Application</span></span>  | `console`     | <span data-ttu-id="4a225-316">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="4a225-316">[C#], F#</span></span> | <span data-ttu-id="4a225-317">Ortak/konsol</span><span class="sxs-lookup"><span data-stu-id="4a225-317">Common/Console</span></span> |
| <span data-ttu-id="4a225-318">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="4a225-318">Class library</span></span>        | `classlib`    | <span data-ttu-id="4a225-319">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="4a225-319">[C#], F#</span></span> | <span data-ttu-id="4a225-320">Ortak/Kitaplık</span><span class="sxs-lookup"><span data-stu-id="4a225-320">Common/Library</span></span> |
| <span data-ttu-id="4a225-321">Birim testi projesi</span><span class="sxs-lookup"><span data-stu-id="4a225-321">Unit Test Project</span></span>    | `mstest`      | <span data-ttu-id="4a225-322">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="4a225-322">[C#], F#</span></span> | <span data-ttu-id="4a225-323">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="4a225-323">Test/MSTest</span></span>    |
| <span data-ttu-id="4a225-324">xUnit test projesi</span><span class="sxs-lookup"><span data-stu-id="4a225-324">xUnit Test Project</span></span>   | `xunit`       | <span data-ttu-id="4a225-325">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="4a225-325">[C#], F#</span></span> | <span data-ttu-id="4a225-326">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="4a225-326">Test/xUnit</span></span>     |
| <span data-ttu-id="4a225-327">ASP.NET Core boş</span><span class="sxs-lookup"><span data-stu-id="4a225-327">ASP.NET Core Empty</span></span>   | `web`         | <span data-ttu-id="4a225-328">[C#]</span><span class="sxs-lookup"><span data-stu-id="4a225-328">[C#]</span></span>     | <span data-ttu-id="4a225-329">Web/boş</span><span class="sxs-lookup"><span data-stu-id="4a225-329">Web/Empty</span></span>      |
| <span data-ttu-id="4a225-330">ASP.NET Core Web uygulaması</span><span class="sxs-lookup"><span data-stu-id="4a225-330">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="4a225-331">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="4a225-331">[C#], F#</span></span> | <span data-ttu-id="4a225-332">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="4a225-332">Web/MVC</span></span>        |
| <span data-ttu-id="4a225-333">ASP.NET Core Web API 'SI</span><span class="sxs-lookup"><span data-stu-id="4a225-333">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="4a225-334">[C#]</span><span class="sxs-lookup"><span data-stu-id="4a225-334">[C#]</span></span>     | <span data-ttu-id="4a225-335">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="4a225-335">Web/WebAPI</span></span>     |
| <span data-ttu-id="4a225-336">NuGet yapılandırması</span><span class="sxs-lookup"><span data-stu-id="4a225-336">Nuget Config</span></span>         | `nugetconfig` |          | <span data-ttu-id="4a225-337">Config</span><span class="sxs-lookup"><span data-stu-id="4a225-337">Config</span></span>         |
| <span data-ttu-id="4a225-338">Web yapılandırması</span><span class="sxs-lookup"><span data-stu-id="4a225-338">Web Config</span></span>           | `webconfig`   |          | <span data-ttu-id="4a225-339">Config</span><span class="sxs-lookup"><span data-stu-id="4a225-339">Config</span></span>         |
| <span data-ttu-id="4a225-340">Çözüm dosyası</span><span class="sxs-lookup"><span data-stu-id="4a225-340">Solution File</span></span>        | `sln`         |          | <span data-ttu-id="4a225-341">Çözüm</span><span class="sxs-lookup"><span data-stu-id="4a225-341">Solution</span></span>       |

---

## <a name="options"></a><span data-ttu-id="4a225-342">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="4a225-342">Options</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="4a225-343">.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="4a225-343">.NET Core 2.2</span></span>](#tab/netcore22)

`--dry-run`

<span data-ttu-id="4a225-344">Bir şablon oluşturulmasına neden olacaksa, verilen komutun çalıştırılması durumunda ne olacağını gösteren bir Özet görüntüler.</span><span class="sxs-lookup"><span data-stu-id="4a225-344">Displays a summary of what would happen if the given command were run if it would result in a template creation.</span></span>

`--force`

<span data-ttu-id="4a225-345">Var olan dosyaları değiştirebilse bile içeriğin oluşturulmasını zorlar.</span><span class="sxs-lookup"><span data-stu-id="4a225-345">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="4a225-346">Çıkış dizini zaten bir proje içerdiğinde bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="4a225-346">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="4a225-347">Komut için yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="4a225-347">Prints out help for the command.</span></span> <span data-ttu-id="4a225-348">`dotnet new` komutun kendisi veya `dotnet new mvc --help`gibi herhangi bir şablon için çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="4a225-348">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="4a225-349">`PATH` veya `NUGET_ID` belirtilen bir kaynak veya şablon paketini kurar.</span><span class="sxs-lookup"><span data-stu-id="4a225-349">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="4a225-350">Şablon paketinin bir ön sürümünü yüklemek istiyorsanız, `<package-name>::<package-version>`biçiminde sürümü belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4a225-350">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="4a225-351">Varsayılan olarak, `dotnet new` en son kararlı paket sürümünü temsil eden sürüm için \* geçirir.</span><span class="sxs-lookup"><span data-stu-id="4a225-351">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="4a225-352">[Örnekler](#examples) bölümündeki bir örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="4a225-352">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="4a225-353">Özel şablonlar oluşturma hakkında daha fazla bilgi için bkz. [DotNet New Için özel şablonlar](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="4a225-353">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="4a225-354">Belirtilen adı içeren şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="4a225-354">Lists templates containing the specified name.</span></span> <span data-ttu-id="4a225-355">`dotnet new` komutu için çağrılırsa, belirtilen dizin için kullanılabilir olabilecek şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="4a225-355">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="4a225-356">Örneğin, dizin zaten bir proje içeriyorsa, tüm proje şablonlarını listeetmez.</span><span class="sxs-lookup"><span data-stu-id="4a225-356">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="4a225-357">Oluşturulacak şablonun dili.</span><span class="sxs-lookup"><span data-stu-id="4a225-357">The language of the template to create.</span></span> <span data-ttu-id="4a225-358">Kabul edilen dil şablona göre değişir (bkz. [arguments](#arguments) bölümünde Varsayılanlar).</span><span class="sxs-lookup"><span data-stu-id="4a225-358">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="4a225-359">Bazı şablonlar için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="4a225-359">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="4a225-360">Bazı kabuklar, `#` özel bir karakter olarak yorumlar.</span><span class="sxs-lookup"><span data-stu-id="4a225-360">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="4a225-361">Bu durumlarda, `dotnet new console -lang "F#"`gibi dil parametre değerini almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4a225-361">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="4a225-362">Oluşturulan çıkışın adı.</span><span class="sxs-lookup"><span data-stu-id="4a225-362">The name for the created output.</span></span> <span data-ttu-id="4a225-363">Ad belirtilmemişse, geçerli dizinin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4a225-363">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="4a225-364">Yüklemesi sırasında kullanılacak bir NuGet kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4a225-364">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="4a225-365">Oluşturulan çıkışın yerleştirileceği konum.</span><span class="sxs-lookup"><span data-stu-id="4a225-365">Location to place the generated output.</span></span> <span data-ttu-id="4a225-366">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="4a225-366">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="4a225-367">Şablonları kullanılabilir türlerine göre filtreler.</span><span class="sxs-lookup"><span data-stu-id="4a225-367">Filters templates based on available types.</span></span> <span data-ttu-id="4a225-368">Önceden tanımlanmış değerler şunlardır "proje", "öğe" veya "diğer".</span><span class="sxs-lookup"><span data-stu-id="4a225-368">Predefined values are "project", "item", or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="4a225-369">`PATH` veya `NUGET_ID` sağlanmış bir kaynak veya şablon paketini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="4a225-369">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="4a225-370">`<PATH|NUGET_ID>` değeri hariç tutularak, yüklü olan tüm şablon paketleri ve bunlarla ilişkili şablonlar görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="4a225-370">When excluding the `<PATH|NUGET_ID>` value, all currently installed template packs and their associated templates are displayed.</span></span>

> [!NOTE]
> <span data-ttu-id="4a225-371">Bir `PATH`kullanarak bir şablonu kaldırmak için, yolu tam olarak nitelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4a225-371">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="4a225-372">Örneğin, *C:/kullanıcılar/\<USER >/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* çalışır, ancak içeren klasörden *./GarciaSoftware.ConsoleTemplate.CSharp* olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="4a225-372">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="4a225-373">Ayrıca, şablon yolunuza son Sonlandırıcı Dizin eğik çizgi eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="4a225-373">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="4a225-374">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="4a225-374">.NET Core 2.1</span></span>](#tab/netcore21)

`--force`

<span data-ttu-id="4a225-375">Var olan dosyaları değiştirebilse bile içeriğin oluşturulmasını zorlar.</span><span class="sxs-lookup"><span data-stu-id="4a225-375">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="4a225-376">Çıkış dizini zaten bir proje içerdiğinde bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="4a225-376">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="4a225-377">Komut için yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="4a225-377">Prints out help for the command.</span></span> <span data-ttu-id="4a225-378">`dotnet new` komutun kendisi veya `dotnet new mvc --help`gibi herhangi bir şablon için çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="4a225-378">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="4a225-379">`PATH` veya `NUGET_ID` belirtilen bir kaynak veya şablon paketini kurar.</span><span class="sxs-lookup"><span data-stu-id="4a225-379">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="4a225-380">Şablon paketinin bir ön sürümünü yüklemek istiyorsanız, `<package-name>::<package-version>`biçiminde sürümü belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4a225-380">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="4a225-381">Varsayılan olarak, `dotnet new` en son kararlı paket sürümünü temsil eden sürüm için \* geçirir.</span><span class="sxs-lookup"><span data-stu-id="4a225-381">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="4a225-382">[Örnekler](#examples) bölümündeki bir örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="4a225-382">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="4a225-383">Özel şablonlar oluşturma hakkında daha fazla bilgi için bkz. [DotNet New Için özel şablonlar](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="4a225-383">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="4a225-384">Belirtilen adı içeren şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="4a225-384">Lists templates containing the specified name.</span></span> <span data-ttu-id="4a225-385">`dotnet new` komutu için çağrılırsa, belirtilen dizin için kullanılabilir olabilecek şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="4a225-385">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="4a225-386">Örneğin, dizin zaten bir proje içeriyorsa, tüm proje şablonlarını listeetmez.</span><span class="sxs-lookup"><span data-stu-id="4a225-386">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="4a225-387">Oluşturulacak şablonun dili.</span><span class="sxs-lookup"><span data-stu-id="4a225-387">The language of the template to create.</span></span> <span data-ttu-id="4a225-388">Kabul edilen dil şablona göre değişir (bkz. [arguments](#arguments) bölümünde Varsayılanlar).</span><span class="sxs-lookup"><span data-stu-id="4a225-388">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="4a225-389">Bazı şablonlar için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="4a225-389">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="4a225-390">Bazı kabuklar, `#` özel bir karakter olarak yorumlar.</span><span class="sxs-lookup"><span data-stu-id="4a225-390">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="4a225-391">Bu durumlarda, `dotnet new console -lang "F#"`gibi dil parametre değerini almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4a225-391">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="4a225-392">Oluşturulan çıkışın adı.</span><span class="sxs-lookup"><span data-stu-id="4a225-392">The name for the created output.</span></span> <span data-ttu-id="4a225-393">Ad belirtilmemişse, geçerli dizinin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4a225-393">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="4a225-394">Yüklemesi sırasında kullanılacak bir NuGet kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4a225-394">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="4a225-395">Oluşturulan çıkışın yerleştirileceği konum.</span><span class="sxs-lookup"><span data-stu-id="4a225-395">Location to place the generated output.</span></span> <span data-ttu-id="4a225-396">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="4a225-396">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="4a225-397">Şablonları kullanılabilir türlerine göre filtreler.</span><span class="sxs-lookup"><span data-stu-id="4a225-397">Filters templates based on available types.</span></span> <span data-ttu-id="4a225-398">Önceden tanımlanmış değerler şunlardır "proje", "öğe" veya "diğer".</span><span class="sxs-lookup"><span data-stu-id="4a225-398">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="4a225-399">`PATH` veya `NUGET_ID` sağlanmış bir kaynak veya şablon paketini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="4a225-399">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="4a225-400">Bir `PATH`kullanarak bir şablonu kaldırmak için, yolu tam olarak nitelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4a225-400">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="4a225-401">Örneğin, *C:/kullanıcılar/\<USER >/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* çalışır, ancak içeren klasörden *./GarciaSoftware.ConsoleTemplate.CSharp* olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="4a225-401">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="4a225-402">Ayrıca, şablon yolunuza son Sonlandırıcı Dizin eğik çizgi eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="4a225-402">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="4a225-403">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="4a225-403">.NET Core 2.0</span></span>](#tab/netcore20)

`--force`

<span data-ttu-id="4a225-404">Var olan dosyaları değiştirebilse bile içeriğin oluşturulmasını zorlar.</span><span class="sxs-lookup"><span data-stu-id="4a225-404">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="4a225-405">Çıkış dizini zaten bir proje içerdiğinde bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="4a225-405">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="4a225-406">Komut için yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="4a225-406">Prints out help for the command.</span></span> <span data-ttu-id="4a225-407">`dotnet new` komutun kendisi veya `dotnet new mvc --help`gibi herhangi bir şablon için çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="4a225-407">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="4a225-408">`PATH` veya `NUGET_ID` belirtilen bir kaynak veya şablon paketini kurar.</span><span class="sxs-lookup"><span data-stu-id="4a225-408">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="4a225-409">Şablon paketinin bir ön sürümünü yüklemek istiyorsanız, `<package-name>::<package-version>`biçiminde sürümü belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4a225-409">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="4a225-410">Varsayılan olarak, `dotnet new` en son kararlı paket sürümünü temsil eden sürüm için \* geçirir.</span><span class="sxs-lookup"><span data-stu-id="4a225-410">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="4a225-411">[Örnekler](#examples) bölümündeki bir örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="4a225-411">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="4a225-412">Özel şablonlar oluşturma hakkında daha fazla bilgi için bkz. [DotNet New Için özel şablonlar](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="4a225-412">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="4a225-413">Belirtilen adı içeren şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="4a225-413">Lists templates containing the specified name.</span></span> <span data-ttu-id="4a225-414">`dotnet new` komutu için çağrılırsa, belirtilen dizin için kullanılabilir olabilecek şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="4a225-414">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="4a225-415">Örneğin, dizin zaten bir proje içeriyorsa, tüm proje şablonlarını listeetmez.</span><span class="sxs-lookup"><span data-stu-id="4a225-415">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="4a225-416">Oluşturulacak şablonun dili.</span><span class="sxs-lookup"><span data-stu-id="4a225-416">The language of the template to create.</span></span> <span data-ttu-id="4a225-417">Kabul edilen dil şablona göre değişir (bkz. [arguments](#arguments) bölümünde Varsayılanlar).</span><span class="sxs-lookup"><span data-stu-id="4a225-417">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="4a225-418">Bazı şablonlar için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="4a225-418">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="4a225-419">Bazı kabuklar, `#` özel bir karakter olarak yorumlar.</span><span class="sxs-lookup"><span data-stu-id="4a225-419">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="4a225-420">Bu durumlarda, `dotnet new console -lang "F#"`gibi dil parametre değerini almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4a225-420">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="4a225-421">Oluşturulan çıkışın adı.</span><span class="sxs-lookup"><span data-stu-id="4a225-421">The name for the created output.</span></span> <span data-ttu-id="4a225-422">Ad belirtilmemişse, geçerli dizinin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4a225-422">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="4a225-423">Oluşturulan çıkışın yerleştirileceği konum.</span><span class="sxs-lookup"><span data-stu-id="4a225-423">Location to place the generated output.</span></span> <span data-ttu-id="4a225-424">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="4a225-424">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="4a225-425">Şablonları kullanılabilir türlerine göre filtreler.</span><span class="sxs-lookup"><span data-stu-id="4a225-425">Filters templates based on available types.</span></span> <span data-ttu-id="4a225-426">Önceden tanımlanmış değerler şunlardır "proje", "öğe" veya "diğer".</span><span class="sxs-lookup"><span data-stu-id="4a225-426">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="4a225-427">`PATH` veya `NUGET_ID` sağlanmış bir kaynak veya şablon paketini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="4a225-427">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="4a225-428">Kaynak `PATH`kullanarak bir şablonu kaldırmak için, yolu tam olarak nitelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4a225-428">To uninstall a template using a source `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="4a225-429">Örneğin, *C:/kullanıcılar/\<USER >/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* çalışır, ancak içeren klasörden *./GarciaSoftware.ConsoleTemplate.CSharp* olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="4a225-429">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span> <span data-ttu-id="4a225-430">Ayrıca, şablon yolunuza son Sonlandırıcı Dizin eğik çizgi eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="4a225-430">Additionally, do not include a final terminating directory slash on your template path.</span></span>
> 
> <span data-ttu-id="4a225-431">Bir şablonu kaldırmak için gereken `PATH` veya `NUGET_ID` bağımsız değişkenini belirleyemıyorsanız, bir bağımsız değişken olmadan `dotnet new --uninstall` çalıştırmak, tüm yüklü şablonları ve bunları kaldırmak için gereken bağımsız değişkeni listeler.</span><span class="sxs-lookup"><span data-stu-id="4a225-431">If you are unable to determine the `PATH` or `NUGET_ID` argument needed to uninstall a template, running `dotnet new --uninstall` without an argument will list all installed templates and the argument required to uninstall them.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="4a225-432">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="4a225-432">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="4a225-433">Yalnızca `dotnet new` komutu bağlamında çalışırken belirli bir proje türü için tüm şablonları gösterir.</span><span class="sxs-lookup"><span data-stu-id="4a225-433">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="4a225-434">`dotnet new web -all`gibi belirli bir şablon bağlamında çalıştırılırken, `-all` bir zorla oluşturma bayrağı olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="4a225-434">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="4a225-435">Çıkış dizini zaten bir proje içerdiğinde bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="4a225-435">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="4a225-436">Komut için yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="4a225-436">Prints out help for the command.</span></span> <span data-ttu-id="4a225-437">`dotnet new` komutun kendisi veya `dotnet new mvc --help`gibi herhangi bir şablon için çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="4a225-437">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="4a225-438">Belirtilen adı içeren şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="4a225-438">Lists templates containing the specified name.</span></span> <span data-ttu-id="4a225-439">`dotnet new` komutu için çağrılırsa, belirtilen dizin için kullanılabilir olabilecek şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="4a225-439">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="4a225-440">Örneğin, dizin zaten bir proje içeriyorsa, tüm proje şablonlarını listeetmez.</span><span class="sxs-lookup"><span data-stu-id="4a225-440">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="4a225-441">Oluşturulacak şablonun dili.</span><span class="sxs-lookup"><span data-stu-id="4a225-441">The language of the template to create.</span></span> <span data-ttu-id="4a225-442">Kabul edilen dil şablona göre değişir (bkz. [arguments](#arguments) bölümünde Varsayılanlar).</span><span class="sxs-lookup"><span data-stu-id="4a225-442">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="4a225-443">Bazı şablonlar için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="4a225-443">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="4a225-444">Bazı kabuklar, `#` özel bir karakter olarak yorumlar.</span><span class="sxs-lookup"><span data-stu-id="4a225-444">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="4a225-445">Bu durumlarda, `dotnet new console -lang "F#"`gibi dil parametre değerini almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4a225-445">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="4a225-446">Oluşturulan çıkışın adı.</span><span class="sxs-lookup"><span data-stu-id="4a225-446">The name for the created output.</span></span> <span data-ttu-id="4a225-447">Ad belirtilmemişse, geçerli dizinin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4a225-447">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="4a225-448">Oluşturulan çıkışın yerleştirileceği konum.</span><span class="sxs-lookup"><span data-stu-id="4a225-448">Location to place the generated output.</span></span> <span data-ttu-id="4a225-449">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="4a225-449">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="4a225-450">Şablon seçenekleri</span><span class="sxs-lookup"><span data-stu-id="4a225-450">Template options</span></span>

<span data-ttu-id="4a225-451">Her proje şablonunda ek seçenekler bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="4a225-451">Each project template may have additional options available.</span></span> <span data-ttu-id="4a225-452">Çekirdek şablonlar aşağıdaki ek seçeneklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="4a225-452">The core templates have the following additional options:</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="4a225-453">.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="4a225-453">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="4a225-454">**konsola**</span><span class="sxs-lookup"><span data-stu-id="4a225-454">**console**</span></span>

<span data-ttu-id="4a225-455">`--langVersion <VERSION_NUMBER>`-oluşturulan proje dosyasındaki `LangVersion` özelliğini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4a225-455">`--langVersion <VERSION_NUMBER>` - Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="4a225-456">Örneğin, 7,3 kullanmak C# için `--langVersion 7.3` kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a225-456">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="4a225-457">İçin F#desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="4a225-457">Not supported for F#.</span></span>

<span data-ttu-id="4a225-458">`--no-restore`-proje oluşturma sırasında örtük geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="4a225-458">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="4a225-459">**Angular, tepki, reactredux**</span><span class="sxs-lookup"><span data-stu-id="4a225-459">**angular, react, reactredux**</span></span>

<span data-ttu-id="4a225-460">`--exclude-launch-settings`-oluşturulan şablondan *Launchsettings. JSON* öğesini hariç tutun.</span><span class="sxs-lookup"><span data-stu-id="4a225-460">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="4a225-461">`--no-restore`-proje oluşturma sırasında örtük geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="4a225-461">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="4a225-462">`--no-https`-proje HTTPS gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="4a225-462">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="4a225-463">Bu seçenek yalnızca `IndividualAuth` veya `OrganizationalAuth` kullanılmıyorsa geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4a225-463">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="4a225-464">**razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="4a225-464">**razorclasslib**</span></span>

<span data-ttu-id="4a225-465">`--no-restore`-proje oluşturma sırasında örtük geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="4a225-465">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="4a225-466">**projesinin**</span><span class="sxs-lookup"><span data-stu-id="4a225-466">**classlib**</span></span>

<span data-ttu-id="4a225-467">`-f|--framework <FRAMEWORK>`-hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="4a225-467">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="4a225-468">Değerler: bir .NET Standard sınıf kitaplığı oluşturmak için bir .NET Core sınıf kitaplığı veya `netstandard2.0` oluşturmak `netcoreapp2.2`.</span><span class="sxs-lookup"><span data-stu-id="4a225-468">Values: `netcoreapp2.2` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="4a225-469">Varsayılan değer `netstandard2.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="4a225-469">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="4a225-470">`--langVersion <VERSION_NUMBER>`-oluşturulan proje dosyasındaki `LangVersion` özelliğini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4a225-470">`--langVersion <VERSION_NUMBER>` - Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="4a225-471">Örneğin, 7,3 kullanmak C# için `--langVersion 7.3` kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a225-471">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="4a225-472">İçin F#desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="4a225-472">Not supported for F#.</span></span>

<span data-ttu-id="4a225-473">`--no-restore`-proje oluşturma sırasında örtük geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="4a225-473">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="4a225-474">**MSTest, xUnit**</span><span class="sxs-lookup"><span data-stu-id="4a225-474">**mstest, xunit**</span></span>

<span data-ttu-id="4a225-475">`-p|--enable-pack`- [DotNet Pack](dotnet-pack.md)kullanarak proje için paketlemeyi etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="4a225-475">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="4a225-476">`--no-restore`-proje oluşturma sırasında örtük geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="4a225-476">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="4a225-477">**NUnit**</span><span class="sxs-lookup"><span data-stu-id="4a225-477">**nunit**</span></span>

<span data-ttu-id="4a225-478">`-f|--framework <FRAMEWORK>`-hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="4a225-478">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="4a225-479">Varsayılan değer `netcoreapp2.1` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="4a225-479">The default value is `netcoreapp2.1`.</span></span>

<span data-ttu-id="4a225-480">`-p|--enable-pack`- [DotNet Pack](dotnet-pack.md)kullanarak proje için paketlemeyi etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="4a225-480">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="4a225-481">`--no-restore`-proje oluşturma sırasında örtük geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="4a225-481">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="4a225-482">**sayfasında**</span><span class="sxs-lookup"><span data-stu-id="4a225-482">**page**</span></span>

<span data-ttu-id="4a225-483">`-na|--namespace <NAMESPACE_NAME>`-oluşturulan kod için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="4a225-483">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="4a225-484">Varsayılan değer `MyApp.Namespace` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="4a225-484">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="4a225-485">`-np|--no-pagemodel`-sayfayı PageModel olmadan oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4a225-485">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="4a225-486">**viewıtems 'lar**</span><span class="sxs-lookup"><span data-stu-id="4a225-486">**viewimports**</span></span>

<span data-ttu-id="4a225-487">`-na|--namespace <NAMESPACE_NAME>`-oluşturulan kod için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="4a225-487">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="4a225-488">Varsayılan değer `MyApp.Namespace` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="4a225-488">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="4a225-489">**Web**</span><span class="sxs-lookup"><span data-stu-id="4a225-489">**web**</span></span>

<span data-ttu-id="4a225-490">`--exclude-launch-settings`-oluşturulan şablondan *Launchsettings. JSON* öğesini hariç tutun.</span><span class="sxs-lookup"><span data-stu-id="4a225-490">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="4a225-491">`--no-restore`-proje oluşturma sırasında örtük geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="4a225-491">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="4a225-492">`--no-https`-proje HTTPS gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="4a225-492">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="4a225-493">Bu seçenek yalnızca `IndividualAuth` veya `OrganizationalAuth` kullanılmıyorsa geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4a225-493">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="4a225-494">**MVC, WebApp**</span><span class="sxs-lookup"><span data-stu-id="4a225-494">**mvc, webapp**</span></span>

<span data-ttu-id="4a225-495">`-au|--auth <AUTHENTICATION_TYPE>`-kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="4a225-495">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="4a225-496">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="4a225-496">The possible values are:</span></span>

- <span data-ttu-id="4a225-497">`None`-kimlik doğrulaması yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="4a225-497">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="4a225-498">`Individual` bireysel kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="4a225-498">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="4a225-499">`IndividualB2C` bireysel kimlik doğrulama Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="4a225-499">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="4a225-500">tek bir kiracı için `SingleOrg` kurumsal kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="4a225-500">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="4a225-501">`MultiOrg`-birden çok kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="4a225-501">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="4a225-502">`Windows`-Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="4a225-502">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="4a225-503">`--aad-b2c-instance <INSTANCE>`-Bağlanılacak Azure Active Directory B2C örneği.</span><span class="sxs-lookup"><span data-stu-id="4a225-503">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="4a225-504">`IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a225-504">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="4a225-505">Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="4a225-505">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="4a225-506">`-ssp|--susi-policy-id <ID>`-bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="4a225-506">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="4a225-507">`IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a225-507">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="4a225-508">`-rp|--reset-password-policy-id <ID>`-bu proje için parola sıfırlama ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="4a225-508">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="4a225-509">`IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a225-509">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="4a225-510">`-ep|--edit-profile-policy-id <ID>`-bu proje için profil ilke KIMLIĞINI Düzenle.</span><span class="sxs-lookup"><span data-stu-id="4a225-510">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="4a225-511">`IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a225-511">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="4a225-512">`--aad-instance <INSTANCE>`-Bağlanılacak Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="4a225-512">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="4a225-513">`SingleOrg` veya `MultiOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a225-513">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="4a225-514">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="4a225-514">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="4a225-515">`--client-id <ID>`-bu projenin Istemci KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="4a225-515">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="4a225-516">`IndividualB2C`, `SingleOrg`veya `MultiOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a225-516">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="4a225-517">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="4a225-517">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="4a225-518">`--domain <DOMAIN>`-Dizin kiracının etki alanı.</span><span class="sxs-lookup"><span data-stu-id="4a225-518">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="4a225-519">`SingleOrg` veya `IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a225-519">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="4a225-520">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="4a225-520">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="4a225-521">`--tenant-id <ID>`-Bağlanılacak dizinin Tenantıd KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="4a225-521">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="4a225-522">`SingleOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a225-522">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="4a225-523">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="4a225-523">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="4a225-524">`--callback-path <PATH>`-uygulamanın yeniden yönlendirme URI 'sinin temel yolu içindeki istek yolu.</span><span class="sxs-lookup"><span data-stu-id="4a225-524">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="4a225-525">`SingleOrg` veya `IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a225-525">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="4a225-526">Varsayılan değer `/signin-oidc` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="4a225-526">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="4a225-527">`-r|--org-read-access`-bu uygulamanın dizine okuma erişimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="4a225-527">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="4a225-528">Yalnızca `SingleOrg` veya `MultiOrg` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4a225-528">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="4a225-529">`--exclude-launch-settings`-oluşturulan şablondan *Launchsettings. JSON* öğesini hariç tutun.</span><span class="sxs-lookup"><span data-stu-id="4a225-529">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="4a225-530">`--no-https`-proje HTTPS gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="4a225-530">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="4a225-531">`app.UseHsts` ve `app.UseHttpsRedirection` `Startup.Configure`eklenmez.</span><span class="sxs-lookup"><span data-stu-id="4a225-531">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="4a225-532">Bu seçenek yalnızca `Individual`, `IndividualB2C`, `SingleOrg`veya `MultiOrg` kullanılmıyorsa geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4a225-532">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="4a225-533">`-uld|--use-local-db`-bir LocalDB 'nin SQLite yerine kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4a225-533">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="4a225-534">Yalnızca `Individual` veya `IndividualB2C` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4a225-534">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="4a225-535">`--no-restore`-proje oluşturma sırasında örtük geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="4a225-535">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="4a225-536">**WebApi**</span><span class="sxs-lookup"><span data-stu-id="4a225-536">**webapi**</span></span>

<span data-ttu-id="4a225-537">`-au|--auth <AUTHENTICATION_TYPE>`-kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="4a225-537">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="4a225-538">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="4a225-538">The possible values are:</span></span>

- <span data-ttu-id="4a225-539">`None`-kimlik doğrulaması yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="4a225-539">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="4a225-540">`IndividualB2C` bireysel kimlik doğrulama Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="4a225-540">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="4a225-541">tek bir kiracı için `SingleOrg` kurumsal kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="4a225-541">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="4a225-542">`Windows`-Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="4a225-542">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="4a225-543">`--aad-b2c-instance <INSTANCE>`-Bağlanılacak Azure Active Directory B2C örneği.</span><span class="sxs-lookup"><span data-stu-id="4a225-543">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="4a225-544">`IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a225-544">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="4a225-545">Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="4a225-545">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="4a225-546">`-ssp|--susi-policy-id <ID>`-bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="4a225-546">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="4a225-547">`IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a225-547">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="4a225-548">`--aad-instance <INSTANCE>`-Bağlanılacak Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="4a225-548">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="4a225-549">`SingleOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a225-549">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="4a225-550">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="4a225-550">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="4a225-551">`--client-id <ID>`-bu projenin Istemci KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="4a225-551">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="4a225-552">`IndividualB2C` veya `SingleOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a225-552">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="4a225-553">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="4a225-553">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="4a225-554">`--domain <DOMAIN>`-Dizin kiracının etki alanı.</span><span class="sxs-lookup"><span data-stu-id="4a225-554">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="4a225-555">`SingleOrg` veya `IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a225-555">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="4a225-556">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="4a225-556">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="4a225-557">`--tenant-id <ID>`-Bağlanılacak dizinin Tenantıd KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="4a225-557">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="4a225-558">`SingleOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a225-558">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="4a225-559">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="4a225-559">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="4a225-560">`-r|--org-read-access`-bu uygulamanın dizine okuma erişimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="4a225-560">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="4a225-561">Yalnızca `SingleOrg` veya `MultiOrg` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4a225-561">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="4a225-562">`--exclude-launch-settings`-oluşturulan şablondan *Launchsettings. JSON* öğesini hariç tutun.</span><span class="sxs-lookup"><span data-stu-id="4a225-562">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="4a225-563">`--no-https`-proje HTTPS gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="4a225-563">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="4a225-564">`app.UseHsts` ve `app.UseHttpsRedirection` `Startup.Configure`eklenmez.</span><span class="sxs-lookup"><span data-stu-id="4a225-564">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="4a225-565">Bu seçenek yalnızca `Individual`, `IndividualB2C`, `SingleOrg`veya `MultiOrg` kullanılmıyorsa geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4a225-565">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="4a225-566">`-uld|--use-local-db`-bir LocalDB 'nin SQLite yerine kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4a225-566">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="4a225-567">Yalnızca `Individual` veya `IndividualB2C` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4a225-567">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="4a225-568">`--no-restore`-proje oluşturma sırasında örtük geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="4a225-568">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="4a225-569">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="4a225-569">**globaljson**</span></span>

<span data-ttu-id="4a225-570">`--sdk-version <VERSION_NUMBER>`- *Global. JSON* dosyasında kullanılacak .NET Core SDK sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="4a225-570">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="4a225-571">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="4a225-571">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="4a225-572">**konsol, angular, tepki, reactredux, razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="4a225-572">**console, angular, react, reactredux, razorclasslib**</span></span>

<span data-ttu-id="4a225-573">`--no-restore`-proje oluşturma sırasında örtük geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="4a225-573">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="4a225-574">**projesinin**</span><span class="sxs-lookup"><span data-stu-id="4a225-574">**classlib**</span></span>

<span data-ttu-id="4a225-575">`-f|--framework <FRAMEWORK>`-hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="4a225-575">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="4a225-576">Değerler: bir .NET Standard sınıf kitaplığı oluşturmak için bir .NET Core sınıf kitaplığı veya `netstandard2.0` oluşturmak `netcoreapp2.1`.</span><span class="sxs-lookup"><span data-stu-id="4a225-576">Values: `netcoreapp2.1` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="4a225-577">Varsayılan değer `netstandard2.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="4a225-577">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="4a225-578">`--no-restore`-proje oluşturma sırasında örtük geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="4a225-578">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="4a225-579">**MSTest, xUnit**</span><span class="sxs-lookup"><span data-stu-id="4a225-579">**mstest, xunit**</span></span>

<span data-ttu-id="4a225-580">`-p|--enable-pack`- [DotNet Pack](dotnet-pack.md)kullanarak proje için paketlemeyi etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="4a225-580">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="4a225-581">`--no-restore`-proje oluşturma sırasında örtük geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="4a225-581">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="4a225-582">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="4a225-582">**globaljson**</span></span>

<span data-ttu-id="4a225-583">`--sdk-version <VERSION_NUMBER>`- *Global. JSON* dosyasında kullanılacak .NET Core SDK sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="4a225-583">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="4a225-584">**Web**</span><span class="sxs-lookup"><span data-stu-id="4a225-584">**web**</span></span>

<span data-ttu-id="4a225-585">`--exclude-launch-settings`-oluşturulan şablondan *Launchsettings. JSON* öğesini hariç tutun.</span><span class="sxs-lookup"><span data-stu-id="4a225-585">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="4a225-586">`--no-restore`-proje oluşturma sırasında örtük geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="4a225-586">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="4a225-587">`--no-https`-proje HTTPS gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="4a225-587">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="4a225-588">Bu seçenek yalnızca `IndividualAuth` veya `OrganizationalAuth` kullanılmıyorsa geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4a225-588">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="4a225-589">**WebApi**</span><span class="sxs-lookup"><span data-stu-id="4a225-589">**webapi**</span></span>

<span data-ttu-id="4a225-590">`-au|--auth <AUTHENTICATION_TYPE>`-kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="4a225-590">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="4a225-591">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="4a225-591">The possible values are:</span></span>

- <span data-ttu-id="4a225-592">`None`-kimlik doğrulaması yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="4a225-592">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="4a225-593">`IndividualB2C` bireysel kimlik doğrulama Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="4a225-593">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="4a225-594">tek bir kiracı için `SingleOrg` kurumsal kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="4a225-594">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="4a225-595">`Windows`-Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="4a225-595">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="4a225-596">`--aad-b2c-instance <INSTANCE>`-Bağlanılacak Azure Active Directory B2C örneği.</span><span class="sxs-lookup"><span data-stu-id="4a225-596">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="4a225-597">`IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a225-597">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="4a225-598">Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="4a225-598">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="4a225-599">`-ssp|--susi-policy-id <ID>`-bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="4a225-599">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="4a225-600">`IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a225-600">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="4a225-601">`--aad-instance <INSTANCE>`-Bağlanılacak Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="4a225-601">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="4a225-602">`SingleOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a225-602">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="4a225-603">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="4a225-603">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="4a225-604">`--client-id <ID>`-bu projenin Istemci KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="4a225-604">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="4a225-605">`IndividualB2C` veya `SingleOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a225-605">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="4a225-606">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="4a225-606">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="4a225-607">`--domain <DOMAIN>`-Dizin kiracının etki alanı.</span><span class="sxs-lookup"><span data-stu-id="4a225-607">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="4a225-608">`SingleOrg` veya `IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a225-608">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="4a225-609">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="4a225-609">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="4a225-610">`--tenant-id <ID>`-Bağlanılacak dizinin Tenantıd KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="4a225-610">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="4a225-611">`SingleOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a225-611">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="4a225-612">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="4a225-612">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="4a225-613">`-r|--org-read-access`-bu uygulamanın dizine okuma erişimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="4a225-613">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="4a225-614">Yalnızca `SingleOrg` veya `MultiOrg` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4a225-614">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="4a225-615">`--exclude-launch-settings`-oluşturulan şablondan *Launchsettings. JSON* öğesini hariç tutun.</span><span class="sxs-lookup"><span data-stu-id="4a225-615">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="4a225-616">`-uld|--use-local-db`-bir LocalDB 'nin SQLite yerine kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4a225-616">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="4a225-617">Yalnızca `Individual` veya `IndividualB2C` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4a225-617">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="4a225-618">`--no-restore`-proje oluşturma sırasında örtük geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="4a225-618">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="4a225-619">`--no-https`-proje HTTPS gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="4a225-619">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="4a225-620">`app.UseHsts` ve `app.UseHttpsRedirection` `Startup.Configure`eklenmez.</span><span class="sxs-lookup"><span data-stu-id="4a225-620">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="4a225-621">Bu seçenek yalnızca `Individual`, `IndividualB2C`, `SingleOrg`veya `MultiOrg` kullanılmıyorsa geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4a225-621">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="4a225-622">**MVC, Razor**</span><span class="sxs-lookup"><span data-stu-id="4a225-622">**mvc, razor**</span></span>

<span data-ttu-id="4a225-623">`-au|--auth <AUTHENTICATION_TYPE>`-kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="4a225-623">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="4a225-624">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="4a225-624">The possible values are:</span></span>

- <span data-ttu-id="4a225-625">`None`-kimlik doğrulaması yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="4a225-625">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="4a225-626">`Individual` bireysel kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="4a225-626">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="4a225-627">`IndividualB2C` bireysel kimlik doğrulama Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="4a225-627">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="4a225-628">tek bir kiracı için `SingleOrg` kurumsal kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="4a225-628">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="4a225-629">`MultiOrg`-birden çok kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="4a225-629">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="4a225-630">`Windows`-Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="4a225-630">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="4a225-631">`--aad-b2c-instance <INSTANCE>`-Bağlanılacak Azure Active Directory B2C örneği.</span><span class="sxs-lookup"><span data-stu-id="4a225-631">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="4a225-632">`IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a225-632">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="4a225-633">Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="4a225-633">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="4a225-634">`-ssp|--susi-policy-id <ID>`-bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="4a225-634">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="4a225-635">`IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a225-635">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="4a225-636">`-rp|--reset-password-policy-id <ID>`-bu proje için parola sıfırlama ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="4a225-636">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="4a225-637">`IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a225-637">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="4a225-638">`-ep|--edit-profile-policy-id <ID>`-bu proje için profil ilke KIMLIĞINI Düzenle.</span><span class="sxs-lookup"><span data-stu-id="4a225-638">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="4a225-639">`IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a225-639">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="4a225-640">`--aad-instance <INSTANCE>`-Bağlanılacak Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="4a225-640">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="4a225-641">`SingleOrg` veya `MultiOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a225-641">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="4a225-642">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="4a225-642">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="4a225-643">`--client-id <ID>`-bu projenin Istemci KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="4a225-643">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="4a225-644">`IndividualB2C`, `SingleOrg`veya `MultiOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a225-644">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="4a225-645">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="4a225-645">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="4a225-646">`--domain <DOMAIN>`-Dizin kiracının etki alanı.</span><span class="sxs-lookup"><span data-stu-id="4a225-646">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="4a225-647">`SingleOrg` veya `IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a225-647">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="4a225-648">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="4a225-648">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="4a225-649">`--tenant-id <ID>`-Bağlanılacak dizinin Tenantıd KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="4a225-649">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="4a225-650">`SingleOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a225-650">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="4a225-651">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="4a225-651">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="4a225-652">`--callback-path <PATH>`-uygulamanın yeniden yönlendirme URI 'sinin temel yolu içindeki istek yolu.</span><span class="sxs-lookup"><span data-stu-id="4a225-652">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="4a225-653">`SingleOrg` veya `IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a225-653">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="4a225-654">Varsayılan değer `/signin-oidc` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="4a225-654">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="4a225-655">`-r|--org-read-access`-bu uygulamanın dizine okuma erişimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="4a225-655">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="4a225-656">Yalnızca `SingleOrg` veya `MultiOrg` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4a225-656">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="4a225-657">`--exclude-launch-settings`-oluşturulan şablondan *Launchsettings. JSON* öğesini hariç tutun.</span><span class="sxs-lookup"><span data-stu-id="4a225-657">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="4a225-658">`--use-browserlink`-projede BrowserLink 'i Içerir.</span><span class="sxs-lookup"><span data-stu-id="4a225-658">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="4a225-659">`-uld|--use-local-db`-bir LocalDB 'nin SQLite yerine kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4a225-659">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="4a225-660">Yalnızca `Individual` veya `IndividualB2C` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4a225-660">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="4a225-661">`--no-restore`-proje oluşturma sırasında örtük geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="4a225-661">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="4a225-662">`--no-https`-proje HTTPS gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="4a225-662">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="4a225-663">`app.UseHsts` ve `app.UseHttpsRedirection` `Startup.Configure`eklenmez.</span><span class="sxs-lookup"><span data-stu-id="4a225-663">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="4a225-664">Bu seçenek yalnızca `Individual`, `IndividualB2C`, `SingleOrg`veya `MultiOrg` kullanılmıyorsa geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4a225-664">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="4a225-665">**sayfasında**</span><span class="sxs-lookup"><span data-stu-id="4a225-665">**page**</span></span>

<span data-ttu-id="4a225-666">`-na|--namespace <NAMESPACE_NAME>`-oluşturulan kod için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="4a225-666">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="4a225-667">Varsayılan değer `MyApp.Namespace` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="4a225-667">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="4a225-668">`-np|--no-pagemodel`-sayfayı PageModel olmadan oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4a225-668">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="4a225-669">**viewıtems 'lar**</span><span class="sxs-lookup"><span data-stu-id="4a225-669">**viewimports**</span></span>

<span data-ttu-id="4a225-670">`-na|--namespace <NAMESPACE_NAME>`-oluşturulan kod için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="4a225-670">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="4a225-671">Varsayılan değer `MyApp.Namespace` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="4a225-671">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="4a225-672">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="4a225-672">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="4a225-673">**konsol, angular, tepki, reactredux**</span><span class="sxs-lookup"><span data-stu-id="4a225-673">**console, angular, react, reactredux**</span></span>

<span data-ttu-id="4a225-674">`--no-restore`-proje oluşturma sırasında örtük geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="4a225-674">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="4a225-675">**projesinin**</span><span class="sxs-lookup"><span data-stu-id="4a225-675">**classlib**</span></span>

<span data-ttu-id="4a225-676">`-f|--framework <FRAMEWORK>`-hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="4a225-676">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="4a225-677">Değerler: bir .NET Standard sınıf kitaplığı oluşturmak için bir .NET Core sınıf kitaplığı veya `netstandard2.0` oluşturmak `netcoreapp2.0`.</span><span class="sxs-lookup"><span data-stu-id="4a225-677">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="4a225-678">Varsayılan değer `netstandard2.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="4a225-678">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="4a225-679">`--no-restore`-proje oluşturma sırasında örtük geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="4a225-679">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="4a225-680">**MSTest, xUnit**</span><span class="sxs-lookup"><span data-stu-id="4a225-680">**mstest, xunit**</span></span>

<span data-ttu-id="4a225-681">`-p|--enable-pack`- [DotNet Pack](dotnet-pack.md)kullanarak proje için paketlemeyi etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="4a225-681">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="4a225-682">`--no-restore`-proje oluşturma sırasında örtük geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="4a225-682">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="4a225-683">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="4a225-683">**globaljson**</span></span>

<span data-ttu-id="4a225-684">`--sdk-version <VERSION_NUMBER>`- *Global. JSON* dosyasında kullanılacak .NET Core SDK sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="4a225-684">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="4a225-685">**Web**</span><span class="sxs-lookup"><span data-stu-id="4a225-685">**web**</span></span>

<span data-ttu-id="4a225-686">`--use-launch-settings`-oluşturulan şablon çıkışında *Launchsettings. JSON* öğesini içerir.</span><span class="sxs-lookup"><span data-stu-id="4a225-686">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="4a225-687">`--no-restore`-proje oluşturma sırasında örtük geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="4a225-687">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="4a225-688">**WebApi**</span><span class="sxs-lookup"><span data-stu-id="4a225-688">**webapi**</span></span>

<span data-ttu-id="4a225-689">`-au|--auth <AUTHENTICATION_TYPE>`-kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="4a225-689">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="4a225-690">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="4a225-690">The possible values are:</span></span>

- <span data-ttu-id="4a225-691">`None`-kimlik doğrulaması yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="4a225-691">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="4a225-692">`IndividualB2C` bireysel kimlik doğrulama Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="4a225-692">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="4a225-693">tek bir kiracı için `SingleOrg` kurumsal kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="4a225-693">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="4a225-694">`Windows`-Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="4a225-694">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="4a225-695">`--aad-b2c-instance <INSTANCE>`-Bağlanılacak Azure Active Directory B2C örneği.</span><span class="sxs-lookup"><span data-stu-id="4a225-695">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="4a225-696">`IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a225-696">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="4a225-697">Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="4a225-697">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="4a225-698">`-ssp|--susi-policy-id <ID>`-bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="4a225-698">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="4a225-699">`IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a225-699">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="4a225-700">`--aad-instance <INSTANCE>`-Bağlanılacak Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="4a225-700">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="4a225-701">`SingleOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a225-701">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="4a225-702">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="4a225-702">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="4a225-703">`--client-id <ID>`-bu projenin Istemci KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="4a225-703">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="4a225-704">`IndividualB2C` veya `SingleOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a225-704">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="4a225-705">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="4a225-705">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="4a225-706">`--domain <DOMAIN>`-Dizin kiracının etki alanı.</span><span class="sxs-lookup"><span data-stu-id="4a225-706">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="4a225-707">`SingleOrg` veya `IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a225-707">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="4a225-708">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="4a225-708">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="4a225-709">`--tenant-id <ID>`-Bağlanılacak dizinin Tenantıd KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="4a225-709">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="4a225-710">`SingleOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a225-710">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="4a225-711">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="4a225-711">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="4a225-712">`-r|--org-read-access`-bu uygulamanın dizine okuma erişimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="4a225-712">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="4a225-713">Yalnızca `SingleOrg` veya `MultiOrg` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4a225-713">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="4a225-714">`--use-launch-settings`-oluşturulan şablon çıkışında *Launchsettings. JSON* öğesini içerir.</span><span class="sxs-lookup"><span data-stu-id="4a225-714">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="4a225-715">`-uld|--use-local-db`-bir LocalDB 'nin SQLite yerine kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4a225-715">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="4a225-716">Yalnızca `Individual` veya `IndividualB2C` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4a225-716">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="4a225-717">`--no-restore`-proje oluşturma sırasında örtük geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="4a225-717">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="4a225-718">**MVC, Razor**</span><span class="sxs-lookup"><span data-stu-id="4a225-718">**mvc, razor**</span></span>

<span data-ttu-id="4a225-719">`-au|--auth <AUTHENTICATION_TYPE>`-kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="4a225-719">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="4a225-720">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="4a225-720">The possible values are:</span></span>

- <span data-ttu-id="4a225-721">`None`-kimlik doğrulaması yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="4a225-721">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="4a225-722">`Individual` bireysel kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="4a225-722">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="4a225-723">`IndividualB2C` bireysel kimlik doğrulama Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="4a225-723">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="4a225-724">tek bir kiracı için `SingleOrg` kurumsal kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="4a225-724">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="4a225-725">`MultiOrg`-birden çok kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="4a225-725">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="4a225-726">`Windows`-Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="4a225-726">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="4a225-727">`--aad-b2c-instance <INSTANCE>`-Bağlanılacak Azure Active Directory B2C örneği.</span><span class="sxs-lookup"><span data-stu-id="4a225-727">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="4a225-728">`IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a225-728">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="4a225-729">Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="4a225-729">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="4a225-730">`-ssp|--susi-policy-id <ID>`-bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="4a225-730">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="4a225-731">`IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a225-731">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="4a225-732">`-rp|--reset-password-policy-id <ID>`-bu proje için parola sıfırlama ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="4a225-732">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="4a225-733">`IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a225-733">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="4a225-734">`-ep|--edit-profile-policy-id <ID>`-bu proje için profil ilke KIMLIĞINI Düzenle.</span><span class="sxs-lookup"><span data-stu-id="4a225-734">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="4a225-735">`IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a225-735">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="4a225-736">`--aad-instance <INSTANCE>`-Bağlanılacak Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="4a225-736">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="4a225-737">`SingleOrg` veya `MultiOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a225-737">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="4a225-738">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="4a225-738">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="4a225-739">`--client-id <ID>`-bu projenin Istemci KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="4a225-739">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="4a225-740">`IndividualB2C`, `SingleOrg`veya `MultiOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a225-740">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="4a225-741">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="4a225-741">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="4a225-742">`--domain <DOMAIN>`-Dizin kiracının etki alanı.</span><span class="sxs-lookup"><span data-stu-id="4a225-742">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="4a225-743">`SingleOrg` veya `IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a225-743">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="4a225-744">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="4a225-744">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="4a225-745">`--tenant-id <ID>`-Bağlanılacak dizinin Tenantıd KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="4a225-745">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="4a225-746">`SingleOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a225-746">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="4a225-747">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="4a225-747">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="4a225-748">`--callback-path <PATH>`-uygulamanın yeniden yönlendirme URI 'sinin temel yolu içindeki istek yolu.</span><span class="sxs-lookup"><span data-stu-id="4a225-748">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="4a225-749">`SingleOrg` veya `IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a225-749">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="4a225-750">Varsayılan değer `/signin-oidc` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="4a225-750">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="4a225-751">`-r|--org-read-access`-bu uygulamanın dizine okuma erişimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="4a225-751">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="4a225-752">Yalnızca `SingleOrg` veya `MultiOrg` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4a225-752">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="4a225-753">`--use-launch-settings`-oluşturulan şablon çıkışında *Launchsettings. JSON* öğesini içerir.</span><span class="sxs-lookup"><span data-stu-id="4a225-753">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="4a225-754">`--use-browserlink`-projede BrowserLink 'i Içerir.</span><span class="sxs-lookup"><span data-stu-id="4a225-754">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="4a225-755">`-uld|--use-local-db`-bir LocalDB 'nin SQLite yerine kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4a225-755">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="4a225-756">Yalnızca `Individual` veya `IndividualB2C` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4a225-756">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="4a225-757">`--no-restore`-proje oluşturma sırasında örtük geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="4a225-757">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="4a225-758">**sayfasında**</span><span class="sxs-lookup"><span data-stu-id="4a225-758">**page**</span></span>

<span data-ttu-id="4a225-759">`-na|--namespace <NAMESPACE_NAME>`-oluşturulan kod için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="4a225-759">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="4a225-760">Varsayılan değer `MyApp.Namespace` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="4a225-760">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="4a225-761">`-np|--no-pagemodel`-sayfayı PageModel olmadan oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4a225-761">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="4a225-762">**viewıtems 'lar**</span><span class="sxs-lookup"><span data-stu-id="4a225-762">**viewimports**</span></span>

<span data-ttu-id="4a225-763">`-na|--namespace <NAMESPACE_NAME>`-oluşturulan kod için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="4a225-763">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="4a225-764">Varsayılan değer `MyApp.Namespace` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="4a225-764">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="4a225-765">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="4a225-765">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="4a225-766">**konsol, xUnit, MSTest, Web, WebApi**</span><span class="sxs-lookup"><span data-stu-id="4a225-766">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="4a225-767">`-f|--framework <FRAMEWORK>`-hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="4a225-767">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="4a225-768">Değerler: `netcoreapp1.0` veya `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="4a225-768">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="4a225-769">Varsayılan değer `netcoreapp1.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="4a225-769">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="4a225-770">**projesinin**</span><span class="sxs-lookup"><span data-stu-id="4a225-770">**classlib**</span></span>

<span data-ttu-id="4a225-771">`-f|--framework <FRAMEWORK>`-hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="4a225-771">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="4a225-772">Değerler: `netstandard1.6`için `netcoreapp1.0`, `netcoreapp1.1`veya `netstandard1.0`.</span><span class="sxs-lookup"><span data-stu-id="4a225-772">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="4a225-773">Varsayılan değer `netstandard1.4` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="4a225-773">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="4a225-774">**MVC**</span><span class="sxs-lookup"><span data-stu-id="4a225-774">**mvc**</span></span>

<span data-ttu-id="4a225-775">`-f|--framework <FRAMEWORK>`-hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="4a225-775">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="4a225-776">Değerler: `netcoreapp1.0` veya `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="4a225-776">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="4a225-777">Varsayılan değer `netcoreapp1.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="4a225-777">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="4a225-778">`-au|--auth <AUTHENTICATION_TYPE>`-kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="4a225-778">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="4a225-779">Değerler: `None` veya `Individual`.</span><span class="sxs-lookup"><span data-stu-id="4a225-779">Values: `None` or `Individual`.</span></span> <span data-ttu-id="4a225-780">Varsayılan değer `None` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="4a225-780">The default value is `None`.</span></span>

<span data-ttu-id="4a225-781">`-uld|--use-local-db`-, SQLite yerine LocalDB kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4a225-781">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="4a225-782">Değerler: `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="4a225-782">Values: `true` or `false`.</span></span> <span data-ttu-id="4a225-783">Varsayılan değer `false` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="4a225-783">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="4a225-784">Örnekler</span><span class="sxs-lookup"><span data-stu-id="4a225-784">Examples</span></span>

<span data-ttu-id="4a225-785">Şablon adını C# belirterek bir konsol uygulaması projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="4a225-785">Create a C# console application project by specifying the template name:</span></span>

`dotnet new "Console Application"`

<span data-ttu-id="4a225-786">Geçerli dizinde F# bir konsol uygulaması projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="4a225-786">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="4a225-787">Belirtilen dizinde bir .NET Standard sınıf kitaplığı projesi oluşturun (yalnızca .NET Core SDK 2,0 veya sonraki sürümlerle kullanılabilir):</span><span class="sxs-lookup"><span data-stu-id="4a225-787">Create a .NET Standard class library project in the specified directory (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="4a225-788">Geçerli dizinde kimlik doğrulaması C# olmadan yeni bir ASP.NET Core MVC projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="4a225-788">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

`dotnet new mvc -au None`

<span data-ttu-id="4a225-789">Yeni bir xUnit projesi oluştur:</span><span class="sxs-lookup"><span data-stu-id="4a225-789">Create a new xUnit project:</span></span>

`dotnet new xunit`

<span data-ttu-id="4a225-790">MVC için kullanılabilen tüm şablonları listeleyin:</span><span class="sxs-lookup"><span data-stu-id="4a225-790">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="4a225-791">*We* alt dizeniz ile eşleşen tüm şablonları listeleyin.</span><span class="sxs-lookup"><span data-stu-id="4a225-791">List all templates matching the *we* substring.</span></span> <span data-ttu-id="4a225-792">Tam eşleşme bulunamadı, bu nedenle alt dize eşleştirmesi hem kısa ad hem de ad sütunlarında çalışır.</span><span class="sxs-lookup"><span data-stu-id="4a225-792">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

`dotnet new we -l`

<span data-ttu-id="4a225-793">Şablonla *eşleşen şablonu*çağırma girişimi.</span><span class="sxs-lookup"><span data-stu-id="4a225-793">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="4a225-794">Tek bir eşleşme belirlenemiyorsa kısmi eşleşen şablonları listeleyin.</span><span class="sxs-lookup"><span data-stu-id="4a225-794">If a single match can't be determined, list the templates that are partial matches.</span></span>

`dotnet new ng`

<span data-ttu-id="4a225-795">ASP.NET Core için tek sayfalı uygulama şablonlarının 2,0 sürümünü (yalnızca .NET Core SDK 1,1 ve sonraki sürümler için kullanılabilir) (komut seçeneği) yükler:</span><span class="sxs-lookup"><span data-stu-id="4a225-795">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

<span data-ttu-id="4a225-796">SDK sürümü 2.0.0 (yalnızca .NET Core SDK 2,0 veya üzeri sürümlerle kullanılabilir) ayarı geçerli dizinde *Global. JSON* oluşturun:</span><span class="sxs-lookup"><span data-stu-id="4a225-796">Create a *global.json* in the current directory setting the SDK version to 2.0.0 (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="4a225-797">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4a225-797">See also</span></span>

- [<span data-ttu-id="4a225-798">DotNet New için özel şablonlar</span><span class="sxs-lookup"><span data-stu-id="4a225-798">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="4a225-799">Dotnet new için özel şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="4a225-799">Create a custom template for dotnet new</span></span>](../tutorials/cli-templates-create-item-template.md)
- [<span data-ttu-id="4a225-800">DotNet/DotNet-şablon-örnek GitHub deposu</span><span class="sxs-lookup"><span data-stu-id="4a225-800">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="4a225-801">DotNet New için kullanılabilir şablonlar</span><span class="sxs-lookup"><span data-stu-id="4a225-801">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
