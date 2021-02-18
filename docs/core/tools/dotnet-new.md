---
title: DotNet yeni komut
description: DotNet New komutu, belirtilen şablona göre yeni .NET projeleri oluşturur.
no-loc:
- Blazor
- WebAssembly
ms.date: 09/04/2020
ms.openlocfilehash: acaaf025555c46f720452b8c9d4f875b8656125a
ms.sourcegitcommit: b924ade6426cf61a4604c4e2ee54cb3592c29317
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/18/2021
ms.locfileid: "101096816"
---
# <a name="dotnet-new"></a><span data-ttu-id="19bcf-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="19bcf-103">dotnet new</span></span>

<span data-ttu-id="19bcf-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,0 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="19bcf-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="19bcf-105">Name</span><span class="sxs-lookup"><span data-stu-id="19bcf-105">Name</span></span>

<span data-ttu-id="19bcf-106">`dotnet new` -Belirtilen şablonu temel alan yeni bir proje, yapılandırma dosyası veya çözüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="19bcf-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="19bcf-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="19bcf-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install {PATH|NUGET_ID}]
    [-lang|--language {"C#"|"F#"|VB}] [-n|--name <OUTPUT_NAME>]
    [--nuget-source <SOURCE>] [-o|--output <OUTPUT_DIRECTORY>]
    [-u|--uninstall] [--update-apply] [--update-check] [Template options]

dotnet new <TEMPLATE> [-l|--list] [--type <TYPE>]

dotnet new -h|--help
```

## <a name="description"></a><span data-ttu-id="19bcf-108">Description</span><span class="sxs-lookup"><span data-stu-id="19bcf-108">Description</span></span>

<span data-ttu-id="19bcf-109">`dotnet new`Komut bir şablonu temel alan bir .NET projesi veya başka yapılar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="19bcf-109">The `dotnet new` command creates a .NET project or other artifacts based on a template.</span></span>

<span data-ttu-id="19bcf-110">Komutu, belirtilen şablon ve seçeneklere göre diskteki yapıtları oluşturmak için [şablon altyapısını](https://github.com/dotnet/templating) çağırır.</span><span class="sxs-lookup"><span data-stu-id="19bcf-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="19bcf-111">Örtük geri yükleme</span><span class="sxs-lookup"><span data-stu-id="19bcf-111">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="19bcf-112">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="19bcf-112">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="19bcf-113">Komut çağrıldığında örnek oluşturulacak şablon.</span><span class="sxs-lookup"><span data-stu-id="19bcf-113">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="19bcf-114">Her şablonun geçirebilmeniz için özel seçenekleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-114">Each template might have specific options you can pass.</span></span> <span data-ttu-id="19bcf-115">Daha fazla bilgi için bkz. [şablon seçenekleri](#template-options).</span><span class="sxs-lookup"><span data-stu-id="19bcf-115">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="19bcf-116">`dotnet new --list` `dotnet new -l` Tüm yüklü şablonların listesini görmek için veya çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="19bcf-116">You can run `dotnet new --list` or `dotnet new -l` to see a list of all installed templates.</span></span> <span data-ttu-id="19bcf-117">Değer, `TEMPLATE` döndürülen tablodaki **Şablonlar** veya **kısa ad** sütunundaki metinde tam eşleşme değilse, bu iki sütunda bir alt dize eşleşmesi gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-117">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="19bcf-118">.NET Core 3,0 SDK ile başlayarak, aşağıdaki koşullarda komutu çağırdığınızda CLı NuGet.org içindeki şablonları arar `dotnet new` :</span><span class="sxs-lookup"><span data-stu-id="19bcf-118">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="19bcf-119">CLı çağrılırken bir şablon eşleşmesi bulamazsa `dotnet new` , bu da kısmi değildir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-119">If the CLI can't find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="19bcf-120">Şablonun daha yeni bir sürümü kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-120">If there's a newer version of the template available.</span></span> <span data-ttu-id="19bcf-121">Bu durumda, proje veya yapıt oluşturulur ancak CLı, şablonun güncelleştirilmiş bir sürümü hakkında sizi uyarır.</span><span class="sxs-lookup"><span data-stu-id="19bcf-121">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="19bcf-122">Aşağıdaki tabloda .NET SDK ile önceden yüklenmiş olarak gelen şablonlar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-122">The following table shows the templates that come pre-installed with the .NET SDK.</span></span> <span data-ttu-id="19bcf-123">Şablon için varsayılan dil, köşeli ayraçlar içinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-123">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="19bcf-124">Özel şablon seçeneklerini görmek için kısa ad bağlantısına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="19bcf-124">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="19bcf-125">Şablonlar</span><span class="sxs-lookup"><span data-stu-id="19bcf-125">Templates</span></span>                                    | <span data-ttu-id="19bcf-126">Kısa ad</span><span class="sxs-lookup"><span data-stu-id="19bcf-126">Short name</span></span>                        | <span data-ttu-id="19bcf-127">Dil</span><span class="sxs-lookup"><span data-stu-id="19bcf-127">Language</span></span>     | <span data-ttu-id="19bcf-128">Etiketler</span><span class="sxs-lookup"><span data-stu-id="19bcf-128">Tags</span></span>                                  | <span data-ttu-id="19bcf-129">Sunulan özellikler</span><span class="sxs-lookup"><span data-stu-id="19bcf-129">Introduced</span></span> |
|----------------------------------------------|-----------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="19bcf-130">Konsol Uygulaması</span><span class="sxs-lookup"><span data-stu-id="19bcf-130">Console Application</span></span>                          | [`console`](#console)             | <span data-ttu-id="19bcf-131">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="19bcf-131">[C#], F#, VB</span></span> | <span data-ttu-id="19bcf-132">Ortak/konsol</span><span class="sxs-lookup"><span data-stu-id="19bcf-132">Common/Console</span></span>                        | <span data-ttu-id="19bcf-133">1.0</span><span class="sxs-lookup"><span data-stu-id="19bcf-133">1.0</span></span>        |
| <span data-ttu-id="19bcf-134">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="19bcf-134">Class library</span></span>                                | [`classlib`](#classlib)           | <span data-ttu-id="19bcf-135">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="19bcf-135">[C#], F#, VB</span></span> | <span data-ttu-id="19bcf-136">Ortak/Kitaplık</span><span class="sxs-lookup"><span data-stu-id="19bcf-136">Common/Library</span></span>                        | <span data-ttu-id="19bcf-137">1.0</span><span class="sxs-lookup"><span data-stu-id="19bcf-137">1.0</span></span>        |
| <span data-ttu-id="19bcf-138">WPF uygulaması</span><span class="sxs-lookup"><span data-stu-id="19bcf-138">WPF Application</span></span>                              | [`wpf`](#wpf)                     | <span data-ttu-id="19bcf-139">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="19bcf-139">[C#], VB</span></span>     | <span data-ttu-id="19bcf-140">Ortak/WPF</span><span class="sxs-lookup"><span data-stu-id="19bcf-140">Common/WPF</span></span>                            | <span data-ttu-id="19bcf-141">3,0 (VB için 5,0)</span><span class="sxs-lookup"><span data-stu-id="19bcf-141">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="19bcf-142">WPF sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="19bcf-142">WPF Class library</span></span>                            | [`wpflib`](#wpf)                  | <span data-ttu-id="19bcf-143">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="19bcf-143">[C#], VB</span></span>     | <span data-ttu-id="19bcf-144">Ortak/WPF</span><span class="sxs-lookup"><span data-stu-id="19bcf-144">Common/WPF</span></span>                            | <span data-ttu-id="19bcf-145">3,0 (VB için 5,0)</span><span class="sxs-lookup"><span data-stu-id="19bcf-145">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="19bcf-146">WPF Özel Denetim Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="19bcf-146">WPF Custom Control Library</span></span>                   | [`wpfcustomcontrollib`](#wpf)     | <span data-ttu-id="19bcf-147">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="19bcf-147">[C#], VB</span></span>     | <span data-ttu-id="19bcf-148">Ortak/WPF</span><span class="sxs-lookup"><span data-stu-id="19bcf-148">Common/WPF</span></span>                            | <span data-ttu-id="19bcf-149">3,0 (VB için 5,0)</span><span class="sxs-lookup"><span data-stu-id="19bcf-149">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="19bcf-150">WPF Kullanıcı denetimi kitaplığı</span><span class="sxs-lookup"><span data-stu-id="19bcf-150">WPF User Control Library</span></span>                     | [`wpfusercontrollib`](#wpf)       | <span data-ttu-id="19bcf-151">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="19bcf-151">[C#], VB</span></span>     | <span data-ttu-id="19bcf-152">Ortak/WPF</span><span class="sxs-lookup"><span data-stu-id="19bcf-152">Common/WPF</span></span>                            | <span data-ttu-id="19bcf-153">3,0 (VB için 5,0)</span><span class="sxs-lookup"><span data-stu-id="19bcf-153">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="19bcf-154">Windows Forms (WinForms) uygulaması</span><span class="sxs-lookup"><span data-stu-id="19bcf-154">Windows Forms (WinForms) Application</span></span>         | [`winforms`](#winforms)           | <span data-ttu-id="19bcf-155">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="19bcf-155">[C#], VB</span></span>     | <span data-ttu-id="19bcf-156">Ortak/WinForms</span><span class="sxs-lookup"><span data-stu-id="19bcf-156">Common/WinForms</span></span>                       | <span data-ttu-id="19bcf-157">3,0 (VB için 5,0)</span><span class="sxs-lookup"><span data-stu-id="19bcf-157">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="19bcf-158">Windows Forms (WinForms) sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="19bcf-158">Windows Forms (WinForms) Class library</span></span>       | [`winformslib`](#winforms)        | <span data-ttu-id="19bcf-159">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="19bcf-159">[C#], VB</span></span>     | <span data-ttu-id="19bcf-160">Ortak/WinForms</span><span class="sxs-lookup"><span data-stu-id="19bcf-160">Common/WinForms</span></span>                       | <span data-ttu-id="19bcf-161">3,0 (VB için 5,0)</span><span class="sxs-lookup"><span data-stu-id="19bcf-161">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="19bcf-162">Çalışan hizmeti</span><span class="sxs-lookup"><span data-stu-id="19bcf-162">Worker Service</span></span>                               | [`worker`](#web-others)           | <span data-ttu-id="19bcf-163">Þ</span><span class="sxs-lookup"><span data-stu-id="19bcf-163">[C#]</span></span>         | <span data-ttu-id="19bcf-164">Ortak/çalışan/Web</span><span class="sxs-lookup"><span data-stu-id="19bcf-164">Common/Worker/Web</span></span>                     | <span data-ttu-id="19bcf-165">3.0</span><span class="sxs-lookup"><span data-stu-id="19bcf-165">3.0</span></span>        |
| <span data-ttu-id="19bcf-166">Birim testi projesi</span><span class="sxs-lookup"><span data-stu-id="19bcf-166">Unit Test Project</span></span>                            | [`mstest`](#test)                 | <span data-ttu-id="19bcf-167">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="19bcf-167">[C#], F#, VB</span></span> | <span data-ttu-id="19bcf-168">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="19bcf-168">Test/MSTest</span></span>                           | <span data-ttu-id="19bcf-169">1.0</span><span class="sxs-lookup"><span data-stu-id="19bcf-169">1.0</span></span>        |
| <span data-ttu-id="19bcf-170">NUnit 3 test projesi</span><span class="sxs-lookup"><span data-stu-id="19bcf-170">NUnit 3 Test Project</span></span>                         | [`nunit`](#nunit)                 | <span data-ttu-id="19bcf-171">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="19bcf-171">[C#], F#, VB</span></span> | <span data-ttu-id="19bcf-172">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="19bcf-172">Test/NUnit</span></span>                            | <span data-ttu-id="19bcf-173">2.1.400</span><span class="sxs-lookup"><span data-stu-id="19bcf-173">2.1.400</span></span>    |
| <span data-ttu-id="19bcf-174">NUnit 3 test öğesi</span><span class="sxs-lookup"><span data-stu-id="19bcf-174">NUnit 3 Test Item</span></span>                            | `nunit-test`                      | <span data-ttu-id="19bcf-175">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="19bcf-175">[C#], F#, VB</span></span> | <span data-ttu-id="19bcf-176">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="19bcf-176">Test/NUnit</span></span>                            | <span data-ttu-id="19bcf-177">2,2</span><span class="sxs-lookup"><span data-stu-id="19bcf-177">2.2</span></span>        |
| <span data-ttu-id="19bcf-178">xUnit test projesi</span><span class="sxs-lookup"><span data-stu-id="19bcf-178">xUnit Test Project</span></span>                           | [`xunit`](#test)                  | <span data-ttu-id="19bcf-179">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="19bcf-179">[C#], F#, VB</span></span> | <span data-ttu-id="19bcf-180">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="19bcf-180">Test/xUnit</span></span>                            | <span data-ttu-id="19bcf-181">1.0</span><span class="sxs-lookup"><span data-stu-id="19bcf-181">1.0</span></span>        |
| <span data-ttu-id="19bcf-182">Razor bileşeni</span><span class="sxs-lookup"><span data-stu-id="19bcf-182">Razor Component</span></span>                              | `razorcomponent`                  | <span data-ttu-id="19bcf-183">Þ</span><span class="sxs-lookup"><span data-stu-id="19bcf-183">[C#]</span></span>         | <span data-ttu-id="19bcf-184">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="19bcf-184">Web/ASP.NET</span></span>                           | <span data-ttu-id="19bcf-185">3.0</span><span class="sxs-lookup"><span data-stu-id="19bcf-185">3.0</span></span>        |
| <span data-ttu-id="19bcf-186">Razor sayfası</span><span class="sxs-lookup"><span data-stu-id="19bcf-186">Razor Page</span></span>                                   | [`page`](#page)                   | <span data-ttu-id="19bcf-187">Þ</span><span class="sxs-lookup"><span data-stu-id="19bcf-187">[C#]</span></span>         | <span data-ttu-id="19bcf-188">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="19bcf-188">Web/ASP.NET</span></span>                           | <span data-ttu-id="19bcf-189">2.0</span><span class="sxs-lookup"><span data-stu-id="19bcf-189">2.0</span></span>        |
| <span data-ttu-id="19bcf-190">MVC Viewıtemts</span><span class="sxs-lookup"><span data-stu-id="19bcf-190">MVC ViewImports</span></span>                              | [`viewimports`](#namespace)       | <span data-ttu-id="19bcf-191">Þ</span><span class="sxs-lookup"><span data-stu-id="19bcf-191">[C#]</span></span>         | <span data-ttu-id="19bcf-192">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="19bcf-192">Web/ASP.NET</span></span>                           | <span data-ttu-id="19bcf-193">2.0</span><span class="sxs-lookup"><span data-stu-id="19bcf-193">2.0</span></span>        |
| <span data-ttu-id="19bcf-194">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="19bcf-194">MVC ViewStart</span></span>                                | `viewstart`                       | <span data-ttu-id="19bcf-195">Þ</span><span class="sxs-lookup"><span data-stu-id="19bcf-195">[C#]</span></span>         | <span data-ttu-id="19bcf-196">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="19bcf-196">Web/ASP.NET</span></span>                           | <span data-ttu-id="19bcf-197">2.0</span><span class="sxs-lookup"><span data-stu-id="19bcf-197">2.0</span></span>        |
| <span data-ttu-id="19bcf-198">Blazor Sunucu uygulaması</span><span class="sxs-lookup"><span data-stu-id="19bcf-198">Blazor Server App</span></span>                            | [`blazorserver`](#blazorserver)   | <span data-ttu-id="19bcf-199">Þ</span><span class="sxs-lookup"><span data-stu-id="19bcf-199">[C#]</span></span>         | <span data-ttu-id="19bcf-200">WebBlazor</span><span class="sxs-lookup"><span data-stu-id="19bcf-200">Web/Blazor</span></span>                            | <span data-ttu-id="19bcf-201">3.0</span><span class="sxs-lookup"><span data-stu-id="19bcf-201">3.0</span></span>        |
| <span data-ttu-id="19bcf-202">BlazorWebAssemblyUygulama</span><span class="sxs-lookup"><span data-stu-id="19bcf-202">Blazor WebAssembly App</span></span>                       | [`blazorwasm`](#blazorwasm)       | <span data-ttu-id="19bcf-203">Þ</span><span class="sxs-lookup"><span data-stu-id="19bcf-203">[C#]</span></span>         | <span data-ttu-id="19bcf-204">WebBlazor/WebAssembly</span><span class="sxs-lookup"><span data-stu-id="19bcf-204">Web/Blazor/WebAssembly</span></span>                | <span data-ttu-id="19bcf-205">3.1.300</span><span class="sxs-lookup"><span data-stu-id="19bcf-205">3.1.300</span></span>    |
| <span data-ttu-id="19bcf-206">ASP.NET Core boş</span><span class="sxs-lookup"><span data-stu-id="19bcf-206">ASP.NET Core Empty</span></span>                           | [`web`](#web)                     | <span data-ttu-id="19bcf-207">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="19bcf-207">[C#], F#</span></span>     | <span data-ttu-id="19bcf-208">Web/boş</span><span class="sxs-lookup"><span data-stu-id="19bcf-208">Web/Empty</span></span>                             | <span data-ttu-id="19bcf-209">1.0</span><span class="sxs-lookup"><span data-stu-id="19bcf-209">1.0</span></span>        |
| <span data-ttu-id="19bcf-210">ASP.NET Core Web uygulaması (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="19bcf-210">ASP.NET Core Web App (Model-View-Controller)</span></span> | [`mvc`](#web-options)             | <span data-ttu-id="19bcf-211">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="19bcf-211">[C#], F#</span></span>     | <span data-ttu-id="19bcf-212">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="19bcf-212">Web/MVC</span></span>                               | <span data-ttu-id="19bcf-213">1.0</span><span class="sxs-lookup"><span data-stu-id="19bcf-213">1.0</span></span>        |
| <span data-ttu-id="19bcf-214">ASP.NET Core Web uygulaması</span><span class="sxs-lookup"><span data-stu-id="19bcf-214">ASP.NET Core Web App</span></span>                         | [`webapp, razor`](#web-options)   | <span data-ttu-id="19bcf-215">Þ</span><span class="sxs-lookup"><span data-stu-id="19bcf-215">[C#]</span></span>         | <span data-ttu-id="19bcf-216">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="19bcf-216">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="19bcf-217">2,2, 2,0</span><span class="sxs-lookup"><span data-stu-id="19bcf-217">2.2, 2.0</span></span>   |
| <span data-ttu-id="19bcf-218">Angular ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="19bcf-218">ASP.NET Core with Angular</span></span>                    | [`angular`](#spa)                 | <span data-ttu-id="19bcf-219">Þ</span><span class="sxs-lookup"><span data-stu-id="19bcf-219">[C#]</span></span>         | <span data-ttu-id="19bcf-220">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="19bcf-220">Web/MVC/SPA</span></span>                           | <span data-ttu-id="19bcf-221">2.0</span><span class="sxs-lookup"><span data-stu-id="19bcf-221">2.0</span></span>        |
| <span data-ttu-id="19bcf-222">React.js ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="19bcf-222">ASP.NET Core with React.js</span></span>                   | [`react`](#spa)                   | <span data-ttu-id="19bcf-223">Þ</span><span class="sxs-lookup"><span data-stu-id="19bcf-223">[C#]</span></span>         | <span data-ttu-id="19bcf-224">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="19bcf-224">Web/MVC/SPA</span></span>                           | <span data-ttu-id="19bcf-225">2.0</span><span class="sxs-lookup"><span data-stu-id="19bcf-225">2.0</span></span>        |
| <span data-ttu-id="19bcf-226">React.js ve Redux ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="19bcf-226">ASP.NET Core with React.js and Redux</span></span>         | [`reactredux`](#reactredux)       | <span data-ttu-id="19bcf-227">Þ</span><span class="sxs-lookup"><span data-stu-id="19bcf-227">[C#]</span></span>         | <span data-ttu-id="19bcf-228">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="19bcf-228">Web/MVC/SPA</span></span>                           | <span data-ttu-id="19bcf-229">2.0</span><span class="sxs-lookup"><span data-stu-id="19bcf-229">2.0</span></span>        |
| <span data-ttu-id="19bcf-230">Razor sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="19bcf-230">Razor Class Library</span></span>                          | [`razorclasslib`](#razorclasslib) | <span data-ttu-id="19bcf-231">Þ</span><span class="sxs-lookup"><span data-stu-id="19bcf-231">[C#]</span></span>         | <span data-ttu-id="19bcf-232">Web/Razor/kitaplık/Razor sınıfı kitaplığı</span><span class="sxs-lookup"><span data-stu-id="19bcf-232">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="19bcf-233">2.1</span><span class="sxs-lookup"><span data-stu-id="19bcf-233">2.1</span></span>        |
| <span data-ttu-id="19bcf-234">ASP.NET Core Web API'si</span><span class="sxs-lookup"><span data-stu-id="19bcf-234">ASP.NET Core Web API</span></span>                         | [`webapi`](#webapi)               | <span data-ttu-id="19bcf-235">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="19bcf-235">[C#], F#</span></span>     | <span data-ttu-id="19bcf-236">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="19bcf-236">Web/WebAPI</span></span>                            | <span data-ttu-id="19bcf-237">1.0</span><span class="sxs-lookup"><span data-stu-id="19bcf-237">1.0</span></span>        |
| <span data-ttu-id="19bcf-238">ASP.NET Core gRPC hizmeti</span><span class="sxs-lookup"><span data-stu-id="19bcf-238">ASP.NET Core gRPC Service</span></span>                    | [`grpc`](#web-others)             | <span data-ttu-id="19bcf-239">Þ</span><span class="sxs-lookup"><span data-stu-id="19bcf-239">[C#]</span></span>         | <span data-ttu-id="19bcf-240">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="19bcf-240">Web/gRPC</span></span>                              | <span data-ttu-id="19bcf-241">3.0</span><span class="sxs-lookup"><span data-stu-id="19bcf-241">3.0</span></span>        |
| <span data-ttu-id="19bcf-242">DotNet gitignore dosyası</span><span class="sxs-lookup"><span data-stu-id="19bcf-242">dotnet gitignore file</span></span>                        | `gitignore`                       |              | <span data-ttu-id="19bcf-243">Config</span><span class="sxs-lookup"><span data-stu-id="19bcf-243">Config</span></span>                                | <span data-ttu-id="19bcf-244">3.0</span><span class="sxs-lookup"><span data-stu-id="19bcf-244">3.0</span></span>        |
| <span data-ttu-id="19bcf-245">Dosya üzerinde global.js</span><span class="sxs-lookup"><span data-stu-id="19bcf-245">global.json file</span></span>                             | [`globaljson`](#globaljson)       |              | <span data-ttu-id="19bcf-246">Config</span><span class="sxs-lookup"><span data-stu-id="19bcf-246">Config</span></span>                                | <span data-ttu-id="19bcf-247">2.0</span><span class="sxs-lookup"><span data-stu-id="19bcf-247">2.0</span></span>        |
| <span data-ttu-id="19bcf-248">NuGet yapılandırması</span><span class="sxs-lookup"><span data-stu-id="19bcf-248">NuGet Config</span></span>                                 | `nugetconfig`                     |              | <span data-ttu-id="19bcf-249">Config</span><span class="sxs-lookup"><span data-stu-id="19bcf-249">Config</span></span>                                | <span data-ttu-id="19bcf-250">1.0</span><span class="sxs-lookup"><span data-stu-id="19bcf-250">1.0</span></span>        |
| <span data-ttu-id="19bcf-251">DotNet yerel araç bildirim dosyası</span><span class="sxs-lookup"><span data-stu-id="19bcf-251">Dotnet local tool manifest file</span></span>              | `tool-manifest`                   |              | <span data-ttu-id="19bcf-252">Config</span><span class="sxs-lookup"><span data-stu-id="19bcf-252">Config</span></span>                                | <span data-ttu-id="19bcf-253">3.0</span><span class="sxs-lookup"><span data-stu-id="19bcf-253">3.0</span></span>        |
| <span data-ttu-id="19bcf-254">Web yapılandırması</span><span class="sxs-lookup"><span data-stu-id="19bcf-254">Web Config</span></span>                                   | `webconfig`                       |              | <span data-ttu-id="19bcf-255">Config</span><span class="sxs-lookup"><span data-stu-id="19bcf-255">Config</span></span>                                | <span data-ttu-id="19bcf-256">1.0</span><span class="sxs-lookup"><span data-stu-id="19bcf-256">1.0</span></span>        |
| <span data-ttu-id="19bcf-257">Çözüm dosyası</span><span class="sxs-lookup"><span data-stu-id="19bcf-257">Solution File</span></span>                                | `sln`                             |              | <span data-ttu-id="19bcf-258">Çözüm</span><span class="sxs-lookup"><span data-stu-id="19bcf-258">Solution</span></span>                              | <span data-ttu-id="19bcf-259">1.0</span><span class="sxs-lookup"><span data-stu-id="19bcf-259">1.0</span></span>        |
| <span data-ttu-id="19bcf-260">Protokol arabelleği dosyası</span><span class="sxs-lookup"><span data-stu-id="19bcf-260">Protocol Buffer File</span></span>                         | [`proto`](#namespace)             |              | <span data-ttu-id="19bcf-261">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="19bcf-261">Web/gRPC</span></span>                              | <span data-ttu-id="19bcf-262">3.0</span><span class="sxs-lookup"><span data-stu-id="19bcf-262">3.0</span></span>        |

## <a name="options"></a><span data-ttu-id="19bcf-263">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="19bcf-263">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="19bcf-264">Bir şablon oluşturulmasına neden olacaksa, verilen komutun çalıştırılması durumunda ne olacağını gösteren bir Özet görüntüler.</span><span class="sxs-lookup"><span data-stu-id="19bcf-264">Displays a summary of what would happen if the given command were run if it would result in a template creation.</span></span> <span data-ttu-id="19bcf-265">.NET Core 2,2 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-265">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="19bcf-266">Var olan dosyaları değiştirebilse bile içeriğin oluşturulmasını zorlar.</span><span class="sxs-lookup"><span data-stu-id="19bcf-266">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="19bcf-267">Seçilen şablon çıkış dizinindeki mevcut dosyaları geçersiz kılacağından bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-267">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="19bcf-268">Komut için yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="19bcf-268">Prints out help for the command.</span></span> <span data-ttu-id="19bcf-269">`dotnet new`Komutun kendisi veya herhangi bir şablon için çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-269">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="19bcf-270">Örneğin, `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="19bcf-270">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="19bcf-271">Veya tarafından belirtilen bir şablon paketini `PATH` kurar `NUGET_ID` .</span><span class="sxs-lookup"><span data-stu-id="19bcf-271">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="19bcf-272">Şablon paketinin bir ön sürümü sürümünü yüklemek istiyorsanız, sürümü biçiminde belirtmeniz gerekir `<package-name>::<package-version>` .</span><span class="sxs-lookup"><span data-stu-id="19bcf-272">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="19bcf-273">Varsayılan olarak, `dotnet new` \* en son kararlı paket sürümünü temsil eden sürüm için geçirir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-273">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="19bcf-274">[Örnekler](#examples) bölümündeki bir örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="19bcf-274">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="19bcf-275">Bu komutu çalıştırdığınızda şablonun bir sürümü zaten yüklüyse, şablon belirtilen sürüme veya sürüm belirtilmemişse en son kararlı sürüme güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-275">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="19bcf-276">Özel şablonlar oluşturma hakkında daha fazla bilgi için bkz. [DotNet New Için özel şablonlar](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="19bcf-276">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="19bcf-277">Belirtilen adı içeren şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="19bcf-277">Lists templates containing the specified name.</span></span> <span data-ttu-id="19bcf-278">Ad belirtilmemişse, tüm şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="19bcf-278">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="19bcf-279">Oluşturulacak şablonun dili.</span><span class="sxs-lookup"><span data-stu-id="19bcf-279">The language of the template to create.</span></span> <span data-ttu-id="19bcf-280">Kabul edilen dil şablona göre değişir (bkz. [arguments](#arguments) bölümünde Varsayılanlar).</span><span class="sxs-lookup"><span data-stu-id="19bcf-280">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="19bcf-281">Bazı şablonlar için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-281">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="19bcf-282">Bazı kabuklar `#` özel bir karakter olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="19bcf-282">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="19bcf-283">Bu durumlarda, dil parametre değerini tırnak içine alın.</span><span class="sxs-lookup"><span data-stu-id="19bcf-283">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="19bcf-284">Örneğin, `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="19bcf-284">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="19bcf-285">Oluşturulan çıkışın adı.</span><span class="sxs-lookup"><span data-stu-id="19bcf-285">The name for the created output.</span></span> <span data-ttu-id="19bcf-286">Ad belirtilmemişse, geçerli dizinin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="19bcf-286">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source <SOURCE>`**

  <span data-ttu-id="19bcf-287">Yüklemesi sırasında kullanılacak bir NuGet kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-287">Specifies a NuGet source to use during install.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="19bcf-288">Oluşturulan çıkışın yerleştirileceği konum.</span><span class="sxs-lookup"><span data-stu-id="19bcf-288">Location to place the generated output.</span></span> <span data-ttu-id="19bcf-289">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="19bcf-289">The default is the current directory.</span></span>

- **`--type <TYPE>`**

  <span data-ttu-id="19bcf-290">Şablonları kullanılabilir türlerine göre filtreler.</span><span class="sxs-lookup"><span data-stu-id="19bcf-290">Filters templates based on available types.</span></span> <span data-ttu-id="19bcf-291">Önceden tanımlanmış değerler `project` ve ' dir `item` .</span><span class="sxs-lookup"><span data-stu-id="19bcf-291">Predefined values are `project` and `item`.</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="19bcf-292">Veya belirtilen bir şablon paketini kaldırır `PATH` `NUGET_ID` .</span><span class="sxs-lookup"><span data-stu-id="19bcf-292">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="19bcf-293">`<PATH|NUGET_ID>`Değer belirtilmediğinde, yüklü olan tüm şablon paketleri ve bunlarla ilişkili şablonlar görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-293">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="19bcf-294">Belirtirken `NUGET_ID` , sürüm numarasını eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="19bcf-294">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="19bcf-295">Bu seçeneğe bir parametre belirtmezseniz, komut, yüklü şablonları ve bunlarla ilgili ayrıntıları listeler.</span><span class="sxs-lookup"><span data-stu-id="19bcf-295">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="19bcf-296">Bir şablonu kullanarak kaldırmak için `PATH` , yolu tam olarak nitelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-296">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="19bcf-297">Örneğin, *C:/Users/ \<USER> /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* çalışır, ancak içeren klasörden *./GarciaSoftware.ConsoleTemplate.CSharp* olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="19bcf-297">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="19bcf-298">Şablon yolunuzda son Sonlandırıcı Dizin eğik çizgisi eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="19bcf-298">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="19bcf-299">Şu anda yüklü olan şablon paketleri için kullanılabilir güncelleştirmelerin olup olmadığını denetler ve bunları kurar.</span><span class="sxs-lookup"><span data-stu-id="19bcf-299">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="19bcf-300">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-300">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="19bcf-301">Şu anda yüklü olan şablon paketleri için kullanılabilir güncelleştirmeler olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="19bcf-301">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="19bcf-302">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-302">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="19bcf-303">Şablon seçenekleri</span><span class="sxs-lookup"><span data-stu-id="19bcf-303">Template options</span></span>

<span data-ttu-id="19bcf-304">Her proje şablonunda ek seçenekler bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-304">Each project template may have additional options available.</span></span> <span data-ttu-id="19bcf-305">Çekirdek şablonlar aşağıdaki ek seçeneklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="19bcf-305">The core templates have the following additional options:</span></span>

### `console`

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="19bcf-306">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-306">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="19bcf-307">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-307">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="19bcf-308">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="19bcf-308">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="19bcf-309">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="19bcf-309">SDK version</span></span> | <span data-ttu-id="19bcf-310">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="19bcf-310">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="19bcf-311">5.0</span><span class="sxs-lookup"><span data-stu-id="19bcf-311">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="19bcf-312">3,1</span><span class="sxs-lookup"><span data-stu-id="19bcf-312">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="19bcf-313">3.0</span><span class="sxs-lookup"><span data-stu-id="19bcf-313">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="19bcf-314">`LangVersion`Oluşturulan proje dosyasındaki özelliği ayarlar.</span><span class="sxs-lookup"><span data-stu-id="19bcf-314">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="19bcf-315">Örneğin, `--langVersion 7.3` C# 7,3 kullanmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="19bcf-315">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="19bcf-316">F # için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="19bcf-316">Not supported for F#.</span></span> <span data-ttu-id="19bcf-317">.NET Core 2,2 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-317">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="19bcf-318">Varsayılan C# sürümlerinin listesi için bkz. [Varsayılanlar](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="19bcf-318">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="19bcf-319">Belirtilmişse, proje oluşturma sırasında örtük geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="19bcf-319">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="19bcf-320">.NET Core 2,2 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-320">Available since .NET Core 2.2 SDK.</span></span>

***

### `classlib`

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="19bcf-321">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-321">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="19bcf-322">Değerler: `net5.0` veya bir `netcoreapp<version>` .NET sınıf kitaplığı oluşturmak veya `netstandard<version>` bir .NET Standard sınıf kitaplığı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="19bcf-322">Values: `net5.0` or `netcoreapp<version>` to create a .NET Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="19bcf-323">.NET 5,0 SDK için varsayılan değer `net5.0` .</span><span class="sxs-lookup"><span data-stu-id="19bcf-323">The default value for .NET 5.0 SDK is `net5.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="19bcf-324">`LangVersion`Oluşturulan proje dosyasındaki özelliği ayarlar.</span><span class="sxs-lookup"><span data-stu-id="19bcf-324">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="19bcf-325">Örneğin, `--langVersion 7.3` C# 7,3 kullanmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="19bcf-325">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="19bcf-326">F # için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="19bcf-326">Not supported for F#.</span></span> <span data-ttu-id="19bcf-327">.NET Core 2,2 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-327">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="19bcf-328">Varsayılan C# sürümlerinin listesi için bkz. [Varsayılanlar](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="19bcf-328">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="19bcf-329">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="19bcf-329">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="wpf-wpflib-wpfcustomcontrollib-wpfusercontrollib"></a><a name="wpf"></a> <span data-ttu-id="19bcf-330">`wpf`, `wpflib`, `wpfcustomcontrollib`, `wpfusercontrollib`</span><span class="sxs-lookup"><span data-stu-id="19bcf-330">`wpf`, `wpflib`, `wpfcustomcontrollib`, `wpfusercontrollib`</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="19bcf-331">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-331">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="19bcf-332">`net5.0` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-332">The default value is `net5.0`.</span></span> <span data-ttu-id="19bcf-333">.NET Core 3,1 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-333">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="19bcf-334">`LangVersion`Oluşturulan proje dosyasındaki özelliği ayarlar.</span><span class="sxs-lookup"><span data-stu-id="19bcf-334">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="19bcf-335">Örneğin, `--langVersion 7.3` C# 7,3 kullanmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="19bcf-335">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="19bcf-336">Varsayılan C# sürümlerinin listesi için bkz. [Varsayılanlar](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="19bcf-336">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="19bcf-337">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="19bcf-337">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="winforms-winformslib"></a><a name="winforms"></a> <span data-ttu-id="19bcf-338">`winforms`, `winformslib`</span><span class="sxs-lookup"><span data-stu-id="19bcf-338">`winforms`, `winformslib`</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="19bcf-339">`LangVersion`Oluşturulan proje dosyasındaki özelliği ayarlar.</span><span class="sxs-lookup"><span data-stu-id="19bcf-339">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="19bcf-340">Örneğin, `--langVersion 7.3` C# 7,3 kullanmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="19bcf-340">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="19bcf-341">Varsayılan C# sürümlerinin listesi için bkz. [Varsayılanlar](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="19bcf-341">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="19bcf-342">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="19bcf-342">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="worker-grpc"></a><a name="web-others"></a> <span data-ttu-id="19bcf-343">`worker`, `grpc`</span><span class="sxs-lookup"><span data-stu-id="19bcf-343">`worker`, `grpc`</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="19bcf-344">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-344">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="19bcf-345">`netcoreapp3.1` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-345">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="19bcf-346">.NET Core 3,1 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-346">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="19bcf-347">Oluşturulan şablondan *launchSettings.js* dışlar.</span><span class="sxs-lookup"><span data-stu-id="19bcf-347">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="19bcf-348">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="19bcf-348">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="mstest-xunit"></a><a name="test"></a> <span data-ttu-id="19bcf-349">`mstest`, `xunit`</span><span class="sxs-lookup"><span data-stu-id="19bcf-349">`mstest`, `xunit`</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="19bcf-350">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-350">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="19bcf-351">.NET Core 3,0 SDK 'dan beri kullanılabilir seçeneği.</span><span class="sxs-lookup"><span data-stu-id="19bcf-351">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="19bcf-352">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="19bcf-352">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="19bcf-353">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="19bcf-353">SDK version</span></span> | <span data-ttu-id="19bcf-354">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="19bcf-354">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="19bcf-355">5.0</span><span class="sxs-lookup"><span data-stu-id="19bcf-355">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="19bcf-356">3,1</span><span class="sxs-lookup"><span data-stu-id="19bcf-356">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="19bcf-357">3.0</span><span class="sxs-lookup"><span data-stu-id="19bcf-357">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="19bcf-358">[DotNet Pack](dotnet-pack.md)kullanarak proje için paketleme imkanı sunar.</span><span class="sxs-lookup"><span data-stu-id="19bcf-358">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="19bcf-359">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="19bcf-359">Doesn't execute an implicit restore during project creation.</span></span>

***

### `nunit`

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="19bcf-360">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-360">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="19bcf-361">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="19bcf-361">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="19bcf-362">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="19bcf-362">SDK version</span></span> | <span data-ttu-id="19bcf-363">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="19bcf-363">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="19bcf-364">5.0</span><span class="sxs-lookup"><span data-stu-id="19bcf-364">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="19bcf-365">3,1</span><span class="sxs-lookup"><span data-stu-id="19bcf-365">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="19bcf-366">3.0</span><span class="sxs-lookup"><span data-stu-id="19bcf-366">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="19bcf-367">2,2</span><span class="sxs-lookup"><span data-stu-id="19bcf-367">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="19bcf-368">2.1</span><span class="sxs-lookup"><span data-stu-id="19bcf-368">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="19bcf-369">[DotNet Pack](dotnet-pack.md)kullanarak proje için paketleme imkanı sunar.</span><span class="sxs-lookup"><span data-stu-id="19bcf-369">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="19bcf-370">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="19bcf-370">Doesn't execute an implicit restore during project creation.</span></span>

***

### `page`

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="19bcf-371">Oluşturulan kod için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="19bcf-371">Namespace for the generated code.</span></span> <span data-ttu-id="19bcf-372">`MyApp.Namespace` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-372">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="19bcf-373">PageModel olmadan sayfayı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="19bcf-373">Creates the page without a PageModel.</span></span>

***

### <a name="viewimports-proto"></a><a name="namespace"></a> <span data-ttu-id="19bcf-374">`viewimports`, `proto`</span><span class="sxs-lookup"><span data-stu-id="19bcf-374">`viewimports`, `proto`</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="19bcf-375">Oluşturulan kod için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="19bcf-375">Namespace for the generated code.</span></span> <span data-ttu-id="19bcf-376">`MyApp.Namespace` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-376">The default value is `MyApp.Namespace`.</span></span>

***

### `blazorserver`

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="19bcf-377">Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="19bcf-377">The type of authentication to use.</span></span> <span data-ttu-id="19bcf-378">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="19bcf-378">The possible values are:</span></span>

  - <span data-ttu-id="19bcf-379">`None` -Kimlik doğrulaması yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="19bcf-379">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="19bcf-380">`Individual` -Bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="19bcf-380">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="19bcf-381">`IndividualB2C` -Azure AD B2C ile bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="19bcf-381">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="19bcf-382">`SingleOrg` -Tek bir kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="19bcf-382">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="19bcf-383">`MultiOrg` -Birden çok kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="19bcf-383">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="19bcf-384">`Windows` -Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="19bcf-384">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="19bcf-385">Bağlanılacak Azure Active Directory B2C örneği.</span><span class="sxs-lookup"><span data-stu-id="19bcf-385">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="19bcf-386">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="19bcf-386">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="19bcf-387">`https://login.microsoftonline.com/tfp/` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-387">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="19bcf-388">Bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="19bcf-388">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="19bcf-389">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="19bcf-389">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="19bcf-390">Bu proje için parola sıfırlama ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="19bcf-390">The reset password policy ID for this project.</span></span> <span data-ttu-id="19bcf-391">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="19bcf-391">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="19bcf-392">Bu proje için profil ilke KIMLIĞINI Düzenle.</span><span class="sxs-lookup"><span data-stu-id="19bcf-392">The edit profile policy ID for this project.</span></span> <span data-ttu-id="19bcf-393">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="19bcf-393">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="19bcf-394">Bağlanılacak Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="19bcf-394">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="19bcf-395">`SingleOrg`Veya `MultiOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="19bcf-395">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="19bcf-396">`https://login.microsoftonline.com/` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-396">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="19bcf-397">Bu projenin Istemci KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="19bcf-397">The Client ID for this project.</span></span> <span data-ttu-id="19bcf-398">`IndividualB2C`, `SingleOrg` Veya `MultiOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="19bcf-398">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="19bcf-399">`11111111-1111-1111-11111111111111111` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-399">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="19bcf-400">Dizin kiracının etki alanı.</span><span class="sxs-lookup"><span data-stu-id="19bcf-400">The domain for the directory tenant.</span></span> <span data-ttu-id="19bcf-401">`SingleOrg`Veya `IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="19bcf-401">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="19bcf-402">`qualified.domain.name` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-402">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="19bcf-403">Bağlanılacak dizinin Tenantıd KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="19bcf-403">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="19bcf-404">`SingleOrg`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="19bcf-404">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="19bcf-405">`22222222-2222-2222-2222-222222222222` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-405">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="19bcf-406">Uygulamanın yeniden yönlendirme URI 'sinin temel yolundaki istek yolu.</span><span class="sxs-lookup"><span data-stu-id="19bcf-406">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="19bcf-407">`SingleOrg`Veya `IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="19bcf-407">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="19bcf-408">`/signin-oidc` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-408">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="19bcf-409">Bu uygulamanın dizine okuma erişimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="19bcf-409">Allows this application read-access to the directory.</span></span> <span data-ttu-id="19bcf-410">Yalnızca `SingleOrg` veya `MultiOrg` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-410">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="19bcf-411">Oluşturulan şablondan *launchSettings.js* dışlar.</span><span class="sxs-lookup"><span data-stu-id="19bcf-411">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="19bcf-412">HTTPS 'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="19bcf-412">Turns off HTTPS.</span></span> <span data-ttu-id="19bcf-413">Bu seçenek yalnızca,, `Individual` , `IndividualB2C` `SingleOrg` veya için kullanılmıyorsa geçerlidir `MultiOrg` `--auth` .</span><span class="sxs-lookup"><span data-stu-id="19bcf-413">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="19bcf-414">SQLite yerine LocalDB kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-414">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="19bcf-415">Yalnızca `Individual` veya `IndividualB2C` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-415">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="19bcf-416">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="19bcf-416">Doesn't execute an implicit restore during project creation.</span></span>

***

### `blazorwasm`

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="19bcf-417">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-417">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="19bcf-418">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="19bcf-418">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="19bcf-419">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="19bcf-419">SDK version</span></span> | <span data-ttu-id="19bcf-420">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="19bcf-420">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="19bcf-421">5.0</span><span class="sxs-lookup"><span data-stu-id="19bcf-421">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="19bcf-422">3,1</span><span class="sxs-lookup"><span data-stu-id="19bcf-422">3.1</span></span>         | `netcoreapp3.1` |

- **`--no-restore`**

  <span data-ttu-id="19bcf-423">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="19bcf-423">Doesn't execute an implicit restore during project creation.</span></span>

- **`-ho|--hosted`**

  <span data-ttu-id="19bcf-424">Uygulama için bir ASP.NET Core Konağı içerir Blazor WebAssembly .</span><span class="sxs-lookup"><span data-stu-id="19bcf-424">Includes an ASP.NET Core host for the Blazor WebAssembly app.</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="19bcf-425">Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="19bcf-425">The type of authentication to use.</span></span> <span data-ttu-id="19bcf-426">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="19bcf-426">The possible values are:</span></span>

  - <span data-ttu-id="19bcf-427">`None` -Kimlik doğrulaması yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="19bcf-427">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="19bcf-428">`Individual` -Bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="19bcf-428">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="19bcf-429">`IndividualB2C` -Azure AD B2C ile bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="19bcf-429">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="19bcf-430">`SingleOrg` -Tek bir kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="19bcf-430">`SingleOrg` - Organizational authentication for a single tenant.</span></span>

- **`--authority <AUTHORITY>`**

  <span data-ttu-id="19bcf-431">OıDC sağlayıcısı yetkilisi.</span><span class="sxs-lookup"><span data-stu-id="19bcf-431">The authority of the OIDC provider.</span></span> <span data-ttu-id="19bcf-432">`Individual`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="19bcf-432">Use with `Individual` authentication.</span></span> <span data-ttu-id="19bcf-433">`https://login.microsoftonline.com/` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-433">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="19bcf-434">Bağlanılacak Azure Active Directory B2C örneği.</span><span class="sxs-lookup"><span data-stu-id="19bcf-434">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="19bcf-435">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="19bcf-435">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="19bcf-436">`https://aadB2CInstance.b2clogin.com/` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-436">The default value is `https://aadB2CInstance.b2clogin.com/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="19bcf-437">Bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="19bcf-437">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="19bcf-438">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="19bcf-438">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="19bcf-439">Bağlanılacak Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="19bcf-439">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="19bcf-440">`SingleOrg`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="19bcf-440">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="19bcf-441">`https://login.microsoftonline.com/` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-441">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="19bcf-442">Bu projenin Istemci KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="19bcf-442">The Client ID for this project.</span></span> <span data-ttu-id="19bcf-443">`IndividualB2C` `SingleOrg` `Individual` Tek başına senaryolarda, veya ile kimlik doğrulaması kullanın.</span><span class="sxs-lookup"><span data-stu-id="19bcf-443">Use with `IndividualB2C`, `SingleOrg`, or `Individual` authentication in standalone scenarios.</span></span> <span data-ttu-id="19bcf-444">`33333333-3333-3333-33333333333333333` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-444">The default value is `33333333-3333-3333-33333333333333333`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="19bcf-445">Dizin kiracının etki alanı.</span><span class="sxs-lookup"><span data-stu-id="19bcf-445">The domain for the directory tenant.</span></span> <span data-ttu-id="19bcf-446">`SingleOrg`Veya `IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="19bcf-446">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="19bcf-447">`qualified.domain.name` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-447">The default value is `qualified.domain.name`.</span></span>

- **`--app-id-uri <URI>`**

  <span data-ttu-id="19bcf-448">Çağırmak istediğiniz sunucu API 'SI için uygulama KIMLIĞI URI 'Si.</span><span class="sxs-lookup"><span data-stu-id="19bcf-448">The App ID Uri for the server API you want to call.</span></span> <span data-ttu-id="19bcf-449">`SingleOrg`Veya `IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="19bcf-449">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="19bcf-450">`api.id.uri` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-450">The default value is `api.id.uri`.</span></span>

- **`--api-client-id <ID>`**

  <span data-ttu-id="19bcf-451">Sunucunun barındırdığı API 'nin Istemci KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="19bcf-451">The Client ID for the API that the server hosts.</span></span> <span data-ttu-id="19bcf-452">`SingleOrg`Veya `IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="19bcf-452">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="19bcf-453">`11111111-1111-1111-11111111111111111` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-453">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`-s|--default-scope <SCOPE>`**

  <span data-ttu-id="19bcf-454">İstemcinin bir erişim belirteci sağlamasını istemesi gereken API kapsamı.</span><span class="sxs-lookup"><span data-stu-id="19bcf-454">The API scope the client needs to request to provision an access token.</span></span> <span data-ttu-id="19bcf-455">`SingleOrg`Veya `IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="19bcf-455">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="19bcf-456">`user_impersonation` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-456">The default value is `user_impersonation`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="19bcf-457">Bağlanılacak dizinin Tenantıd KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="19bcf-457">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="19bcf-458">`SingleOrg`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="19bcf-458">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="19bcf-459">`22222222-2222-2222-2222-222222222222` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-459">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="19bcf-460">Bu uygulamanın dizine okuma erişimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="19bcf-460">Allows this application read-access to the directory.</span></span> <span data-ttu-id="19bcf-461">Yalnızca `SingleOrg` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-461">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="19bcf-462">Oluşturulan şablondan *launchSettings.js* dışlar.</span><span class="sxs-lookup"><span data-stu-id="19bcf-462">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-p|--pwa`**

  <span data-ttu-id="19bcf-463">yüklemeyi ve çevrimdışı kullanımı destekleyen bir aşamalı Web uygulaması (PWA) üretir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-463">produces a Progressive Web Application (PWA) supporting installation and offline use.</span></span>

- **`--no-https`**

  <span data-ttu-id="19bcf-464">HTTPS 'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="19bcf-464">Turns off HTTPS.</span></span> <span data-ttu-id="19bcf-465">Bu seçenek yalnızca,, `Individual` `IndividualB2C` veya için kullanılmıyorsa geçerlidir `SingleOrg` `--auth` .</span><span class="sxs-lookup"><span data-stu-id="19bcf-465">This option only applies if `Individual`, `IndividualB2C`, or `SingleOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="19bcf-466">SQLite yerine LocalDB kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-466">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="19bcf-467">Yalnızca `Individual` veya `IndividualB2C` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-467">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--called-api-url <URL>`**

  <span data-ttu-id="19bcf-468">Web uygulamasından çağrılacak API 'nin URL 'SI.</span><span class="sxs-lookup"><span data-stu-id="19bcf-468">URL of the API to call from the web app.</span></span> <span data-ttu-id="19bcf-469">Yalnızca `SingleOrg` `IndividualB2C` ASP.NET Core bir ana bilgisayar olmadan veya kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-469">Only applies to `SingleOrg` or `IndividualB2C` authentication without an ASP.NET Core host specified.</span></span> <span data-ttu-id="19bcf-470">`https://graph.microsoft.com/v1.0/me` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-470">The default value is `https://graph.microsoft.com/v1.0/me`.</span></span>

- **`--calls-graph`**

  <span data-ttu-id="19bcf-471">Web uygulamasının Microsoft Graph çağırıyorsa belirtir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-471">Specifies if the web app calls Microsoft Graph.</span></span> <span data-ttu-id="19bcf-472">Yalnızca `SingleOrg` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-472">Only applies to `SingleOrg` authentication.</span></span>

- **`--called-api-scopes <SCOPES>`**

  <span data-ttu-id="19bcf-473">Web uygulamasından API 'yi çağırmak için istenen kapsamlar.</span><span class="sxs-lookup"><span data-stu-id="19bcf-473">Scopes to request to call the API from the web app.</span></span> <span data-ttu-id="19bcf-474">Yalnızca `SingleOrg` `IndividualB2C` ASP.NET Core bir ana bilgisayar olmadan veya kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-474">Only applies to `SingleOrg` or `IndividualB2C` authentication without an ASP.NET Core host specified.</span></span> <span data-ttu-id="19bcf-475">Varsayılan değer: `user.read`.</span><span class="sxs-lookup"><span data-stu-id="19bcf-475">The default is `user.read`.</span></span>

***

### `web`

- **`--exclude-launch-settings`**

  <span data-ttu-id="19bcf-476">Oluşturulan şablondan *launchSettings.js* dışlar.</span><span class="sxs-lookup"><span data-stu-id="19bcf-476">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="19bcf-477">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-477">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="19bcf-478">Seçenek .NET Core 2,2 SDK sürümünde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="19bcf-478">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="19bcf-479">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="19bcf-479">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="19bcf-480">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="19bcf-480">SDK version</span></span> | <span data-ttu-id="19bcf-481">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="19bcf-481">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="19bcf-482">5.0</span><span class="sxs-lookup"><span data-stu-id="19bcf-482">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="19bcf-483">3,1</span><span class="sxs-lookup"><span data-stu-id="19bcf-483">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="19bcf-484">3.0</span><span class="sxs-lookup"><span data-stu-id="19bcf-484">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="19bcf-485">2.1</span><span class="sxs-lookup"><span data-stu-id="19bcf-485">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="19bcf-486">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="19bcf-486">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="19bcf-487">HTTPS 'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="19bcf-487">Turns off HTTPS.</span></span>

***

### <a name="mvc-webapp"></a><a name="web-options"></a> <span data-ttu-id="19bcf-488">`mvc`, `webapp`</span><span class="sxs-lookup"><span data-stu-id="19bcf-488">`mvc`, `webapp`</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="19bcf-489">Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="19bcf-489">The type of authentication to use.</span></span> <span data-ttu-id="19bcf-490">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="19bcf-490">The possible values are:</span></span>

  - <span data-ttu-id="19bcf-491">`None` -Kimlik doğrulaması yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="19bcf-491">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="19bcf-492">`Individual` -Bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="19bcf-492">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="19bcf-493">`IndividualB2C` -Azure AD B2C ile bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="19bcf-493">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="19bcf-494">`SingleOrg` -Tek bir kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="19bcf-494">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="19bcf-495">`MultiOrg` -Birden çok kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="19bcf-495">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="19bcf-496">`Windows` -Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="19bcf-496">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="19bcf-497">Bağlanılacak Azure Active Directory B2C örneği.</span><span class="sxs-lookup"><span data-stu-id="19bcf-497">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="19bcf-498">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="19bcf-498">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="19bcf-499">`https://login.microsoftonline.com/tfp/` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-499">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="19bcf-500">Bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="19bcf-500">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="19bcf-501">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="19bcf-501">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="19bcf-502">Bu proje için parola sıfırlama ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="19bcf-502">The reset password policy ID for this project.</span></span> <span data-ttu-id="19bcf-503">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="19bcf-503">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="19bcf-504">Bu proje için profil ilke KIMLIĞINI Düzenle.</span><span class="sxs-lookup"><span data-stu-id="19bcf-504">The edit profile policy ID for this project.</span></span> <span data-ttu-id="19bcf-505">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="19bcf-505">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="19bcf-506">Bağlanılacak Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="19bcf-506">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="19bcf-507">`SingleOrg`Veya `MultiOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="19bcf-507">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="19bcf-508">`https://login.microsoftonline.com/` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-508">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="19bcf-509">Bu projenin Istemci KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="19bcf-509">The Client ID for this project.</span></span> <span data-ttu-id="19bcf-510">`IndividualB2C`, `SingleOrg` Veya `MultiOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="19bcf-510">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="19bcf-511">`11111111-1111-1111-11111111111111111` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-511">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="19bcf-512">Dizin kiracının etki alanı.</span><span class="sxs-lookup"><span data-stu-id="19bcf-512">The domain for the directory tenant.</span></span> <span data-ttu-id="19bcf-513">`SingleOrg`Veya `IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="19bcf-513">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="19bcf-514">`qualified.domain.name` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-514">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="19bcf-515">Bağlanılacak dizinin Tenantıd KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="19bcf-515">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="19bcf-516">`SingleOrg`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="19bcf-516">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="19bcf-517">`22222222-2222-2222-2222-222222222222` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-517">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="19bcf-518">Uygulamanın yeniden yönlendirme URI 'sinin temel yolundaki istek yolu.</span><span class="sxs-lookup"><span data-stu-id="19bcf-518">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="19bcf-519">`SingleOrg`Veya `IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="19bcf-519">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="19bcf-520">`/signin-oidc` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-520">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="19bcf-521">Bu uygulamanın dizine okuma erişimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="19bcf-521">Allows this application read-access to the directory.</span></span> <span data-ttu-id="19bcf-522">Yalnızca `SingleOrg` veya `MultiOrg` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-522">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="19bcf-523">Oluşturulan şablondan *launchSettings.js* dışlar.</span><span class="sxs-lookup"><span data-stu-id="19bcf-523">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="19bcf-524">HTTPS 'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="19bcf-524">Turns off HTTPS.</span></span> <span data-ttu-id="19bcf-525">Bu seçenek yalnızca,,, veya kullanılmıyorsa geçerlidir `Individual` `IndividualB2C` `SingleOrg` `MultiOrg` .</span><span class="sxs-lookup"><span data-stu-id="19bcf-525">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="19bcf-526">SQLite yerine LocalDB kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-526">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="19bcf-527">Yalnızca `Individual` veya `IndividualB2C` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-527">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="19bcf-528">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-528">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="19bcf-529">.NET Core 3,0 SDK 'dan beri kullanılabilir seçeneği.</span><span class="sxs-lookup"><span data-stu-id="19bcf-529">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="19bcf-530">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="19bcf-530">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="19bcf-531">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="19bcf-531">SDK version</span></span> | <span data-ttu-id="19bcf-532">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="19bcf-532">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="19bcf-533">5.0</span><span class="sxs-lookup"><span data-stu-id="19bcf-533">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="19bcf-534">3,1</span><span class="sxs-lookup"><span data-stu-id="19bcf-534">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="19bcf-535">3.0</span><span class="sxs-lookup"><span data-stu-id="19bcf-535">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="19bcf-536">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="19bcf-536">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="19bcf-537">Projedeki BrowserLink öğesini içerir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-537">Includes BrowserLink in the project.</span></span> <span data-ttu-id="19bcf-538">Seçenek .NET Core 2,2 ve 3,1 SDK sürümünde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="19bcf-538">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

- **`-rrc|--razor-runtime-compilation`**

  <span data-ttu-id="19bcf-539">Projenin hata ayıklama yapılarında [Razor çalışma zamanı derlemesini](/aspnet/core/mvc/views/view-compilation#runtime-compilation) kullanmak üzere yapılandırılıp yapılandırılmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="19bcf-539">Determines if the project is configured to use [Razor runtime compilation](/aspnet/core/mvc/views/view-compilation#runtime-compilation) in Debug builds.</span></span> <span data-ttu-id="19bcf-540">.NET Core 3.1.201 SDK 'dan beri kullanılabilir seçeneği.</span><span class="sxs-lookup"><span data-stu-id="19bcf-540">Option available since .NET Core 3.1.201 SDK.</span></span>

***

### <a name="angular-react"></a><a name="spa"></a> <span data-ttu-id="19bcf-541">`angular`, `react`</span><span class="sxs-lookup"><span data-stu-id="19bcf-541">`angular`, `react`</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="19bcf-542">Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="19bcf-542">The type of authentication to use.</span></span> <span data-ttu-id="19bcf-543">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-543">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="19bcf-544">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="19bcf-544">The possible values are:</span></span>

  - <span data-ttu-id="19bcf-545">`None` -Kimlik doğrulaması yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="19bcf-545">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="19bcf-546">`Individual` -Bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="19bcf-546">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="19bcf-547">Oluşturulan şablondan *launchSettings.js* dışlar.</span><span class="sxs-lookup"><span data-stu-id="19bcf-547">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="19bcf-548">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="19bcf-548">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="19bcf-549">HTTPS 'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="19bcf-549">Turns off HTTPS.</span></span> <span data-ttu-id="19bcf-550">Bu seçenek yalnızca kimlik doğrulaması ise geçerlidir `None` .</span><span class="sxs-lookup"><span data-stu-id="19bcf-550">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="19bcf-551">SQLite yerine LocalDB kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-551">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="19bcf-552">Yalnızca `Individual` veya `IndividualB2C` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-552">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="19bcf-553">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-553">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="19bcf-554">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-554">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="19bcf-555">Seçenek .NET Core 2,2 SDK sürümünde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="19bcf-555">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="19bcf-556">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="19bcf-556">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="19bcf-557">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="19bcf-557">SDK version</span></span> | <span data-ttu-id="19bcf-558">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="19bcf-558">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="19bcf-559">5.0</span><span class="sxs-lookup"><span data-stu-id="19bcf-559">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="19bcf-560">3,1</span><span class="sxs-lookup"><span data-stu-id="19bcf-560">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="19bcf-561">3.0</span><span class="sxs-lookup"><span data-stu-id="19bcf-561">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="19bcf-562">2.1</span><span class="sxs-lookup"><span data-stu-id="19bcf-562">2.1</span></span>         | `netcoreapp2.0` |

***

### `reactredux`

- **`--exclude-launch-settings`**

  <span data-ttu-id="19bcf-563">Oluşturulan şablondan *launchSettings.js* dışlar.</span><span class="sxs-lookup"><span data-stu-id="19bcf-563">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="19bcf-564">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-564">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="19bcf-565">Seçenek .NET Core 2,2 SDK sürümünde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="19bcf-565">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="19bcf-566">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="19bcf-566">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="19bcf-567">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="19bcf-567">SDK version</span></span> | <span data-ttu-id="19bcf-568">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="19bcf-568">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="19bcf-569">5.0</span><span class="sxs-lookup"><span data-stu-id="19bcf-569">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="19bcf-570">3,1</span><span class="sxs-lookup"><span data-stu-id="19bcf-570">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="19bcf-571">3.0</span><span class="sxs-lookup"><span data-stu-id="19bcf-571">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="19bcf-572">2.1</span><span class="sxs-lookup"><span data-stu-id="19bcf-572">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="19bcf-573">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="19bcf-573">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="19bcf-574">HTTPS 'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="19bcf-574">Turns off HTTPS.</span></span>

***

### `razorclasslib`

- **`--no-restore`**

  <span data-ttu-id="19bcf-575">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="19bcf-575">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="19bcf-576">, Bu kitaplığa bileşenlere ek olarak geleneksel Razor sayfaları ve görünümleri eklenmesini destekler.</span><span class="sxs-lookup"><span data-stu-id="19bcf-576">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="19bcf-577">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-577">Available since .NET Core 3.0 SDK.</span></span>

***
  
### `webapi`

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="19bcf-578">Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="19bcf-578">The type of authentication to use.</span></span> <span data-ttu-id="19bcf-579">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="19bcf-579">The possible values are:</span></span>

  - <span data-ttu-id="19bcf-580">`None` -Kimlik doğrulaması yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="19bcf-580">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="19bcf-581">`IndividualB2C` -Azure AD B2C ile bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="19bcf-581">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="19bcf-582">`SingleOrg` -Tek bir kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="19bcf-582">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="19bcf-583">`Windows` -Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="19bcf-583">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="19bcf-584">Bağlanılacak Azure Active Directory B2C örneği.</span><span class="sxs-lookup"><span data-stu-id="19bcf-584">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="19bcf-585">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="19bcf-585">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="19bcf-586">`https://login.microsoftonline.com/tfp/` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-586">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="19bcf-587">Bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="19bcf-587">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="19bcf-588">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="19bcf-588">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="19bcf-589">Bağlanılacak Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="19bcf-589">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="19bcf-590">`SingleOrg`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="19bcf-590">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="19bcf-591">`https://login.microsoftonline.com/` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-591">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="19bcf-592">Bu projenin Istemci KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="19bcf-592">The Client ID for this project.</span></span> <span data-ttu-id="19bcf-593">`IndividualB2C`Veya `SingleOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="19bcf-593">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="19bcf-594">`11111111-1111-1111-11111111111111111` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-594">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="19bcf-595">Dizin kiracının etki alanı.</span><span class="sxs-lookup"><span data-stu-id="19bcf-595">The domain for the directory tenant.</span></span> <span data-ttu-id="19bcf-596">`IndividualB2C`Veya `SingleOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="19bcf-596">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="19bcf-597">`qualified.domain.name` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-597">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="19bcf-598">Bağlanılacak dizinin Tenantıd KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="19bcf-598">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="19bcf-599">`SingleOrg`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="19bcf-599">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="19bcf-600">`22222222-2222-2222-2222-222222222222` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-600">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="19bcf-601">Bu uygulamanın dizine okuma erişimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="19bcf-601">Allows this application read-access to the directory.</span></span> <span data-ttu-id="19bcf-602">Yalnızca `SingleOrg` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-602">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="19bcf-603">Oluşturulan şablondan *launchSettings.js* dışlar.</span><span class="sxs-lookup"><span data-stu-id="19bcf-603">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="19bcf-604">HTTPS 'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="19bcf-604">Turns off HTTPS.</span></span> <span data-ttu-id="19bcf-605">`app.UseHsts` ve `app.UseHttpsRedirection` öğesine eklenmez `Startup.Configure` .</span><span class="sxs-lookup"><span data-stu-id="19bcf-605">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="19bcf-606">Bu seçenek yalnızca `IndividualB2C` `SingleOrg` kimlik doğrulaması için kullanılmıyorsa geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-606">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="19bcf-607">SQLite yerine LocalDB kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-607">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="19bcf-608">Yalnızca `IndividualB2C` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-608">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="19bcf-609">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-609">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="19bcf-610">Seçenek .NET Core 2,2 SDK sürümünde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="19bcf-610">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="19bcf-611">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="19bcf-611">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="19bcf-612">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="19bcf-612">SDK version</span></span> | <span data-ttu-id="19bcf-613">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="19bcf-613">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="19bcf-614">5.0</span><span class="sxs-lookup"><span data-stu-id="19bcf-614">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="19bcf-615">3,1</span><span class="sxs-lookup"><span data-stu-id="19bcf-615">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="19bcf-616">3.0</span><span class="sxs-lookup"><span data-stu-id="19bcf-616">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="19bcf-617">2.1</span><span class="sxs-lookup"><span data-stu-id="19bcf-617">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="19bcf-618">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="19bcf-618">Doesn't execute an implicit restore during project creation.</span></span>

***

### `globaljson`

- **`--sdk-version <VERSION_NUMBER>`**

  <span data-ttu-id="19bcf-619">Dosyasında *global.js* kullanılacak .NET SDK sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="19bcf-619">Specifies the version of the .NET SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="19bcf-620">Örnekler</span><span class="sxs-lookup"><span data-stu-id="19bcf-620">Examples</span></span>

- <span data-ttu-id="19bcf-621">Şablon adını belirterek bir C# konsol uygulaması projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="19bcf-621">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="19bcf-622">Geçerli dizinde bir F # konsol uygulaması projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="19bcf-622">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang "F#"
  ```

- <span data-ttu-id="19bcf-623">Belirtilen dizinde bir .NET Standard sınıf kitaplığı projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="19bcf-623">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="19bcf-624">Geçerli dizinde kimlik doğrulaması olmadan yeni bir ASP.NET Core C# MVC projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="19bcf-624">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="19bcf-625">Yeni bir xUnit projesi oluştur:</span><span class="sxs-lookup"><span data-stu-id="19bcf-625">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="19bcf-626">Tek sayfalı uygulama (SPA) şablonları için kullanılabilen tüm şablonları listeleyin:</span><span class="sxs-lookup"><span data-stu-id="19bcf-626">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="19bcf-627">*We* alt dizeniz ile eşleşen tüm şablonları listeleyin.</span><span class="sxs-lookup"><span data-stu-id="19bcf-627">List all templates matching the *we* substring.</span></span> <span data-ttu-id="19bcf-628">Tam eşleşme bulunamadı, bu nedenle alt dize eşleştirmesi hem kısa ad hem de ad sütunlarında çalışır.</span><span class="sxs-lookup"><span data-stu-id="19bcf-628">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="19bcf-629">Şablonla *eşleşen şablonu* çağırma girişimi.</span><span class="sxs-lookup"><span data-stu-id="19bcf-629">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="19bcf-630">Tek bir eşleşme belirlenemiyorsa kısmi eşleşen şablonları listeleyin.</span><span class="sxs-lookup"><span data-stu-id="19bcf-630">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="19bcf-631">ASP.NET Core için SPA şablonlarının 2,0 sürümünü yükler:</span><span class="sxs-lookup"><span data-stu-id="19bcf-631">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="19bcf-632">Yüklü şablonları ve bunlarla ilgili ayrıntıları, bunları kaldırma dahil olmak üzere listeleyin:</span><span class="sxs-lookup"><span data-stu-id="19bcf-632">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="19bcf-633">SDK sürümünü 3.1.101 olarak ayarlamak için geçerli dizinde bir *global.js* oluşturun:</span><span class="sxs-lookup"><span data-stu-id="19bcf-633">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="19bcf-634">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="19bcf-634">See also</span></span>

- [<span data-ttu-id="19bcf-635">DotNet New için özel şablonlar</span><span class="sxs-lookup"><span data-stu-id="19bcf-635">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="19bcf-636">Dotnet new için özel şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="19bcf-636">Create a custom template for dotnet new</span></span>](../tutorials/cli-templates-create-item-template.md)
- [<span data-ttu-id="19bcf-637">DotNet/DotNet-şablon-örnek GitHub deposu</span><span class="sxs-lookup"><span data-stu-id="19bcf-637">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="19bcf-638">DotNet New için kullanılabilir şablonlar</span><span class="sxs-lookup"><span data-stu-id="19bcf-638">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
