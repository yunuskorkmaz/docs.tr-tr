---
title: DotNet yeni komut
description: DotNet New komutu, belirtilen şablona göre yeni .NET Core projeleri oluşturur.
no-loc:
- Blazor
- WebAssembly
ms.date: 09/01/2020
ms.openlocfilehash: 4a4c8e2806fee663b5f6aa255a6f24250a072a85
ms.sourcegitcommit: 532b03d5bbab764d63356193b04cd2281bc01239
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/26/2020
ms.locfileid: "92526614"
---
# <a name="dotnet-new"></a><span data-ttu-id="dd5ea-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="dd5ea-103">dotnet new</span></span>

<span data-ttu-id="dd5ea-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,0 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="dd5ea-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="dd5ea-105">Name</span><span class="sxs-lookup"><span data-stu-id="dd5ea-105">Name</span></span>

<span data-ttu-id="dd5ea-106">`dotnet new` -Belirtilen şablonu temel alan yeni bir proje, yapılandırma dosyası veya çözüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="dd5ea-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="dd5ea-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install {PATH|NUGET_ID}]
    [-lang|--language {"C#"|"F#"|VB}] [-n|--name <OUTPUT_NAME>]
    [--nuget-source <SOURCE>] [-o|--output <OUTPUT_DIRECTORY>]
    [-u|--uninstall] [--update-apply] [--update-check] [Template options]

dotnet new <TEMPLATE> [-l|--list] [--type <TYPE>]

dotnet new -h|--help
```

## <a name="description"></a><span data-ttu-id="dd5ea-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dd5ea-108">Description</span></span>

<span data-ttu-id="dd5ea-109">`dotnet new`Komut bir şablonu temel alan bir .NET Core projesi veya diğer yapılar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-109">The `dotnet new` command creates a .NET Core project or other artifacts based on a template.</span></span>

<span data-ttu-id="dd5ea-110">Komutu, belirtilen şablon ve seçeneklere göre diskteki yapıtları oluşturmak için [şablon altyapısını](https://github.com/dotnet/templating) çağırır.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="dd5ea-111">Örtük geri yükleme</span><span class="sxs-lookup"><span data-stu-id="dd5ea-111">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="dd5ea-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="dd5ea-112">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="dd5ea-113">Komut çağrıldığında örnek oluşturulacak şablon.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-113">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="dd5ea-114">Her şablonun geçirebilmeniz için özel seçenekleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-114">Each template might have specific options you can pass.</span></span> <span data-ttu-id="dd5ea-115">Daha fazla bilgi için bkz. [şablon seçenekleri](#template-options).</span><span class="sxs-lookup"><span data-stu-id="dd5ea-115">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="dd5ea-116">`dotnet new --list` `dotnet new -l` Tüm yüklü şablonların listesini görmek için veya çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-116">You can run `dotnet new --list` or `dotnet new -l` to see a list of all installed templates.</span></span> <span data-ttu-id="dd5ea-117">Değer, `TEMPLATE` döndürülen tablodaki **Şablonlar** veya **kısa ad** sütunundaki metinde tam eşleşme değilse, bu iki sütunda bir alt dize eşleşmesi gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-117">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="dd5ea-118">.NET Core 3,0 SDK ile başlayarak, aşağıdaki koşullarda komutu çağırdığınızda CLı NuGet.org içindeki şablonları arar `dotnet new` :</span><span class="sxs-lookup"><span data-stu-id="dd5ea-118">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="dd5ea-119">CLı çağrılırken bir şablon eşleşmesi bulamazsa `dotnet new` , bu da kısmi değildir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-119">If the CLI can't find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="dd5ea-120">Şablonun daha yeni bir sürümü kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-120">If there's a newer version of the template available.</span></span> <span data-ttu-id="dd5ea-121">Bu durumda, proje veya yapıt oluşturulur ancak CLı, şablonun güncelleştirilmiş bir sürümü hakkında sizi uyarır.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-121">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="dd5ea-122">Aşağıdaki tabloda, .NET Core SDK ile önceden yüklenmiş olan şablonlar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-122">The following table shows the templates that come pre-installed with the .NET Core SDK.</span></span> <span data-ttu-id="dd5ea-123">Şablon için varsayılan dil, köşeli ayraçlar içinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-123">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="dd5ea-124">Özel şablon seçeneklerini görmek için kısa ad bağlantısına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-124">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="dd5ea-125">Şablonlar</span><span class="sxs-lookup"><span data-stu-id="dd5ea-125">Templates</span></span>                                    | <span data-ttu-id="dd5ea-126">Kısa ad</span><span class="sxs-lookup"><span data-stu-id="dd5ea-126">Short name</span></span>                      | <span data-ttu-id="dd5ea-127">Dil</span><span class="sxs-lookup"><span data-stu-id="dd5ea-127">Language</span></span>     | <span data-ttu-id="dd5ea-128">Etiketler</span><span class="sxs-lookup"><span data-stu-id="dd5ea-128">Tags</span></span>                                  | <span data-ttu-id="dd5ea-129">Sunulan özellikler</span><span class="sxs-lookup"><span data-stu-id="dd5ea-129">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="dd5ea-130">Konsol Uygulaması</span><span class="sxs-lookup"><span data-stu-id="dd5ea-130">Console Application</span></span>                          | [<span data-ttu-id="dd5ea-131">konsola</span><span class="sxs-lookup"><span data-stu-id="dd5ea-131">console</span></span>](#console)             | <span data-ttu-id="dd5ea-132">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="dd5ea-132">[C#], F#, VB</span></span> | <span data-ttu-id="dd5ea-133">Ortak/konsol</span><span class="sxs-lookup"><span data-stu-id="dd5ea-133">Common/Console</span></span>                        | <span data-ttu-id="dd5ea-134">1.0</span><span class="sxs-lookup"><span data-stu-id="dd5ea-134">1.0</span></span>        |
| <span data-ttu-id="dd5ea-135">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="dd5ea-135">Class library</span></span>                                | [<span data-ttu-id="dd5ea-136">projesinin</span><span class="sxs-lookup"><span data-stu-id="dd5ea-136">classlib</span></span>](#classlib)           | <span data-ttu-id="dd5ea-137">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="dd5ea-137">[C#], F#, VB</span></span> | <span data-ttu-id="dd5ea-138">Ortak/Kitaplık</span><span class="sxs-lookup"><span data-stu-id="dd5ea-138">Common/Library</span></span>                        | <span data-ttu-id="dd5ea-139">1.0</span><span class="sxs-lookup"><span data-stu-id="dd5ea-139">1.0</span></span>        |
| <span data-ttu-id="dd5ea-140">WPF uygulaması</span><span class="sxs-lookup"><span data-stu-id="dd5ea-140">WPF Application</span></span>                              | [<span data-ttu-id="dd5ea-141">WPF</span><span class="sxs-lookup"><span data-stu-id="dd5ea-141">wpf</span></span>](#wpf)                     | <span data-ttu-id="dd5ea-142">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="dd5ea-142">[C#], VB</span></span>     | <span data-ttu-id="dd5ea-143">Ortak/WPF</span><span class="sxs-lookup"><span data-stu-id="dd5ea-143">Common/WPF</span></span>                            | <span data-ttu-id="dd5ea-144">3,0 (VB için 5,0)</span><span class="sxs-lookup"><span data-stu-id="dd5ea-144">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="dd5ea-145">WPF sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="dd5ea-145">WPF Class library</span></span>                            | [<span data-ttu-id="dd5ea-146">wpflib</span><span class="sxs-lookup"><span data-stu-id="dd5ea-146">wpflib</span></span>](#wpf)                  | <span data-ttu-id="dd5ea-147">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="dd5ea-147">[C#], VB</span></span>     | <span data-ttu-id="dd5ea-148">Ortak/WPF</span><span class="sxs-lookup"><span data-stu-id="dd5ea-148">Common/WPF</span></span>                            | <span data-ttu-id="dd5ea-149">3,0 (VB için 5,0)</span><span class="sxs-lookup"><span data-stu-id="dd5ea-149">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="dd5ea-150">WPF Özel Denetim Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="dd5ea-150">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="dd5ea-151">wpfcustomcontrollib</span><span class="sxs-lookup"><span data-stu-id="dd5ea-151">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="dd5ea-152">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="dd5ea-152">[C#], VB</span></span>     | <span data-ttu-id="dd5ea-153">Ortak/WPF</span><span class="sxs-lookup"><span data-stu-id="dd5ea-153">Common/WPF</span></span>                            | <span data-ttu-id="dd5ea-154">3,0 (VB için 5,0)</span><span class="sxs-lookup"><span data-stu-id="dd5ea-154">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="dd5ea-155">WPF Kullanıcı denetimi kitaplığı</span><span class="sxs-lookup"><span data-stu-id="dd5ea-155">WPF User Control Library</span></span>                     | [<span data-ttu-id="dd5ea-156">wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="dd5ea-156">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="dd5ea-157">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="dd5ea-157">[C#], VB</span></span>     | <span data-ttu-id="dd5ea-158">Ortak/WPF</span><span class="sxs-lookup"><span data-stu-id="dd5ea-158">Common/WPF</span></span>                            | <span data-ttu-id="dd5ea-159">3,0 (VB için 5,0)</span><span class="sxs-lookup"><span data-stu-id="dd5ea-159">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="dd5ea-160">Windows Forms (WinForms) uygulaması</span><span class="sxs-lookup"><span data-stu-id="dd5ea-160">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="dd5ea-161">WinForms</span><span class="sxs-lookup"><span data-stu-id="dd5ea-161">winforms</span></span>](#winforms)           | <span data-ttu-id="dd5ea-162">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="dd5ea-162">[C#], VB</span></span>     | <span data-ttu-id="dd5ea-163">Ortak/WinForms</span><span class="sxs-lookup"><span data-stu-id="dd5ea-163">Common/WinForms</span></span>                       | <span data-ttu-id="dd5ea-164">3,0 (VB için 5,0)</span><span class="sxs-lookup"><span data-stu-id="dd5ea-164">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="dd5ea-165">Windows Forms (WinForms) sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="dd5ea-165">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="dd5ea-166">winformslib</span><span class="sxs-lookup"><span data-stu-id="dd5ea-166">winformslib</span></span>](#winforms)        | <span data-ttu-id="dd5ea-167">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="dd5ea-167">[C#], VB</span></span>     | <span data-ttu-id="dd5ea-168">Ortak/WinForms</span><span class="sxs-lookup"><span data-stu-id="dd5ea-168">Common/WinForms</span></span>                       | <span data-ttu-id="dd5ea-169">3,0 (VB için 5,0)</span><span class="sxs-lookup"><span data-stu-id="dd5ea-169">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="dd5ea-170">Çalışan hizmeti</span><span class="sxs-lookup"><span data-stu-id="dd5ea-170">Worker Service</span></span>                               | [<span data-ttu-id="dd5ea-171">ından</span><span class="sxs-lookup"><span data-stu-id="dd5ea-171">worker</span></span>](#web-others)           | <span data-ttu-id="dd5ea-172">Þ</span><span class="sxs-lookup"><span data-stu-id="dd5ea-172">[C#]</span></span>         | <span data-ttu-id="dd5ea-173">Ortak/çalışan/Web</span><span class="sxs-lookup"><span data-stu-id="dd5ea-173">Common/Worker/Web</span></span>                     | <span data-ttu-id="dd5ea-174">3.0</span><span class="sxs-lookup"><span data-stu-id="dd5ea-174">3.0</span></span>        |
| <span data-ttu-id="dd5ea-175">Birim testi projesi</span><span class="sxs-lookup"><span data-stu-id="dd5ea-175">Unit Test Project</span></span>                            | [<span data-ttu-id="dd5ea-176">'i</span><span class="sxs-lookup"><span data-stu-id="dd5ea-176">mstest</span></span>](#test)                 | <span data-ttu-id="dd5ea-177">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="dd5ea-177">[C#], F#, VB</span></span> | <span data-ttu-id="dd5ea-178">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="dd5ea-178">Test/MSTest</span></span>                           | <span data-ttu-id="dd5ea-179">1.0</span><span class="sxs-lookup"><span data-stu-id="dd5ea-179">1.0</span></span>        |
| <span data-ttu-id="dd5ea-180">NUnit 3 test projesi</span><span class="sxs-lookup"><span data-stu-id="dd5ea-180">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="dd5ea-181">NUnit</span><span class="sxs-lookup"><span data-stu-id="dd5ea-181">nunit</span></span>](#nunit)                 | <span data-ttu-id="dd5ea-182">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="dd5ea-182">[C#], F#, VB</span></span> | <span data-ttu-id="dd5ea-183">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="dd5ea-183">Test/NUnit</span></span>                            | <span data-ttu-id="dd5ea-184">2.1.400</span><span class="sxs-lookup"><span data-stu-id="dd5ea-184">2.1.400</span></span>    |
| <span data-ttu-id="dd5ea-185">NUnit 3 test öğesi</span><span class="sxs-lookup"><span data-stu-id="dd5ea-185">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="dd5ea-186">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="dd5ea-186">[C#], F#, VB</span></span> | <span data-ttu-id="dd5ea-187">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="dd5ea-187">Test/NUnit</span></span>                            | <span data-ttu-id="dd5ea-188">2.2</span><span class="sxs-lookup"><span data-stu-id="dd5ea-188">2.2</span></span>        |
| <span data-ttu-id="dd5ea-189">xUnit test projesi</span><span class="sxs-lookup"><span data-stu-id="dd5ea-189">xUnit Test Project</span></span>                           | [<span data-ttu-id="dd5ea-190">xUnit</span><span class="sxs-lookup"><span data-stu-id="dd5ea-190">xunit</span></span>](#test)                  | <span data-ttu-id="dd5ea-191">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="dd5ea-191">[C#], F#, VB</span></span> | <span data-ttu-id="dd5ea-192">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="dd5ea-192">Test/xUnit</span></span>                            | <span data-ttu-id="dd5ea-193">1.0</span><span class="sxs-lookup"><span data-stu-id="dd5ea-193">1.0</span></span>        |
| <span data-ttu-id="dd5ea-194">Razor bileşeni</span><span class="sxs-lookup"><span data-stu-id="dd5ea-194">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="dd5ea-195">Þ</span><span class="sxs-lookup"><span data-stu-id="dd5ea-195">[C#]</span></span>         | <span data-ttu-id="dd5ea-196">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="dd5ea-196">Web/ASP.NET</span></span>                           | <span data-ttu-id="dd5ea-197">3.0</span><span class="sxs-lookup"><span data-stu-id="dd5ea-197">3.0</span></span>        |
| <span data-ttu-id="dd5ea-198">Razor sayfası</span><span class="sxs-lookup"><span data-stu-id="dd5ea-198">Razor Page</span></span>                                   | [<span data-ttu-id="dd5ea-199">sayfasında</span><span class="sxs-lookup"><span data-stu-id="dd5ea-199">page</span></span>](#page)                   | <span data-ttu-id="dd5ea-200">Þ</span><span class="sxs-lookup"><span data-stu-id="dd5ea-200">[C#]</span></span>         | <span data-ttu-id="dd5ea-201">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="dd5ea-201">Web/ASP.NET</span></span>                           | <span data-ttu-id="dd5ea-202">2.0</span><span class="sxs-lookup"><span data-stu-id="dd5ea-202">2.0</span></span>        |
| <span data-ttu-id="dd5ea-203">MVC Viewıtemts</span><span class="sxs-lookup"><span data-stu-id="dd5ea-203">MVC ViewImports</span></span>                              | [<span data-ttu-id="dd5ea-204">viewıtems 'lar</span><span class="sxs-lookup"><span data-stu-id="dd5ea-204">viewimports</span></span>](#namespace)       | <span data-ttu-id="dd5ea-205">Þ</span><span class="sxs-lookup"><span data-stu-id="dd5ea-205">[C#]</span></span>         | <span data-ttu-id="dd5ea-206">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="dd5ea-206">Web/ASP.NET</span></span>                           | <span data-ttu-id="dd5ea-207">2.0</span><span class="sxs-lookup"><span data-stu-id="dd5ea-207">2.0</span></span>        |
| <span data-ttu-id="dd5ea-208">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="dd5ea-208">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="dd5ea-209">Þ</span><span class="sxs-lookup"><span data-stu-id="dd5ea-209">[C#]</span></span>         | <span data-ttu-id="dd5ea-210">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="dd5ea-210">Web/ASP.NET</span></span>                           | <span data-ttu-id="dd5ea-211">2.0</span><span class="sxs-lookup"><span data-stu-id="dd5ea-211">2.0</span></span>        |
| <span data-ttu-id="dd5ea-212">Blazor Sunucu uygulaması</span><span class="sxs-lookup"><span data-stu-id="dd5ea-212">Blazor Server App</span></span>                            | [<span data-ttu-id="dd5ea-213">blazorserver</span><span class="sxs-lookup"><span data-stu-id="dd5ea-213">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="dd5ea-214">Þ</span><span class="sxs-lookup"><span data-stu-id="dd5ea-214">[C#]</span></span>         | <span data-ttu-id="dd5ea-215">WebBlazor</span><span class="sxs-lookup"><span data-stu-id="dd5ea-215">Web/Blazor</span></span>                            | <span data-ttu-id="dd5ea-216">3.0</span><span class="sxs-lookup"><span data-stu-id="dd5ea-216">3.0</span></span>        |
| <span data-ttu-id="dd5ea-217">BlazorWebAssemblyUygulama</span><span class="sxs-lookup"><span data-stu-id="dd5ea-217">Blazor WebAssembly App</span></span>                       | `blazorwasm`                    | <span data-ttu-id="dd5ea-218">Þ</span><span class="sxs-lookup"><span data-stu-id="dd5ea-218">[C#]</span></span>         | <span data-ttu-id="dd5ea-219">WebBlazor/WebAssembly</span><span class="sxs-lookup"><span data-stu-id="dd5ea-219">Web/Blazor/WebAssembly</span></span>                | <span data-ttu-id="dd5ea-220">3.1.300</span><span class="sxs-lookup"><span data-stu-id="dd5ea-220">3.1.300</span></span>    |
| <span data-ttu-id="dd5ea-221">ASP.NET Core boş</span><span class="sxs-lookup"><span data-stu-id="dd5ea-221">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="dd5ea-222">Web</span><span class="sxs-lookup"><span data-stu-id="dd5ea-222">web</span></span>](#web)                     | <span data-ttu-id="dd5ea-223">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="dd5ea-223">[C#], F#</span></span>     | <span data-ttu-id="dd5ea-224">Web/boş</span><span class="sxs-lookup"><span data-stu-id="dd5ea-224">Web/Empty</span></span>                             | <span data-ttu-id="dd5ea-225">1.0</span><span class="sxs-lookup"><span data-stu-id="dd5ea-225">1.0</span></span>        |
| <span data-ttu-id="dd5ea-226">ASP.NET Core Web uygulaması (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="dd5ea-226">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="dd5ea-227">MVC</span><span class="sxs-lookup"><span data-stu-id="dd5ea-227">mvc</span></span>](#web-options)             | <span data-ttu-id="dd5ea-228">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="dd5ea-228">[C#], F#</span></span>     | <span data-ttu-id="dd5ea-229">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="dd5ea-229">Web/MVC</span></span>                               | <span data-ttu-id="dd5ea-230">1.0</span><span class="sxs-lookup"><span data-stu-id="dd5ea-230">1.0</span></span>        |
| <span data-ttu-id="dd5ea-231">ASP.NET Core Web uygulaması</span><span class="sxs-lookup"><span data-stu-id="dd5ea-231">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="dd5ea-232">WEBAPP, Razor</span><span class="sxs-lookup"><span data-stu-id="dd5ea-232">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="dd5ea-233">Þ</span><span class="sxs-lookup"><span data-stu-id="dd5ea-233">[C#]</span></span>         | <span data-ttu-id="dd5ea-234">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="dd5ea-234">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="dd5ea-235">2,2, 2,0</span><span class="sxs-lookup"><span data-stu-id="dd5ea-235">2.2, 2.0</span></span>   |
| <span data-ttu-id="dd5ea-236">Angular ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="dd5ea-236">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="dd5ea-237">Angular</span><span class="sxs-lookup"><span data-stu-id="dd5ea-237">angular</span></span>](#spa)                 | <span data-ttu-id="dd5ea-238">Þ</span><span class="sxs-lookup"><span data-stu-id="dd5ea-238">[C#]</span></span>         | <span data-ttu-id="dd5ea-239">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="dd5ea-239">Web/MVC/SPA</span></span>                           | <span data-ttu-id="dd5ea-240">2.0</span><span class="sxs-lookup"><span data-stu-id="dd5ea-240">2.0</span></span>        |
| <span data-ttu-id="dd5ea-241">React.js ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="dd5ea-241">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="dd5ea-242">tıkla</span><span class="sxs-lookup"><span data-stu-id="dd5ea-242">react</span></span>](#spa)                   | <span data-ttu-id="dd5ea-243">Þ</span><span class="sxs-lookup"><span data-stu-id="dd5ea-243">[C#]</span></span>         | <span data-ttu-id="dd5ea-244">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="dd5ea-244">Web/MVC/SPA</span></span>                           | <span data-ttu-id="dd5ea-245">2.0</span><span class="sxs-lookup"><span data-stu-id="dd5ea-245">2.0</span></span>        |
| <span data-ttu-id="dd5ea-246">React.js ve Redux ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="dd5ea-246">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="dd5ea-247">reactredux</span><span class="sxs-lookup"><span data-stu-id="dd5ea-247">reactredux</span></span>](#reactredux)       | <span data-ttu-id="dd5ea-248">Þ</span><span class="sxs-lookup"><span data-stu-id="dd5ea-248">[C#]</span></span>         | <span data-ttu-id="dd5ea-249">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="dd5ea-249">Web/MVC/SPA</span></span>                           | <span data-ttu-id="dd5ea-250">2.0</span><span class="sxs-lookup"><span data-stu-id="dd5ea-250">2.0</span></span>        |
| <span data-ttu-id="dd5ea-251">Razor sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="dd5ea-251">Razor Class Library</span></span>                          | [<span data-ttu-id="dd5ea-252">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="dd5ea-252">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="dd5ea-253">Þ</span><span class="sxs-lookup"><span data-stu-id="dd5ea-253">[C#]</span></span>         | <span data-ttu-id="dd5ea-254">Web/Razor/kitaplık/Razor sınıfı kitaplığı</span><span class="sxs-lookup"><span data-stu-id="dd5ea-254">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="dd5ea-255">2.1</span><span class="sxs-lookup"><span data-stu-id="dd5ea-255">2.1</span></span>        |
| <span data-ttu-id="dd5ea-256">ASP.NET Core Web API'si</span><span class="sxs-lookup"><span data-stu-id="dd5ea-256">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="dd5ea-257">WebApi</span><span class="sxs-lookup"><span data-stu-id="dd5ea-257">webapi</span></span>](#webapi)               | <span data-ttu-id="dd5ea-258">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="dd5ea-258">[C#], F#</span></span>     | <span data-ttu-id="dd5ea-259">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="dd5ea-259">Web/WebAPI</span></span>                            | <span data-ttu-id="dd5ea-260">1.0</span><span class="sxs-lookup"><span data-stu-id="dd5ea-260">1.0</span></span>        |
| <span data-ttu-id="dd5ea-261">ASP.NET Core gRPC hizmeti</span><span class="sxs-lookup"><span data-stu-id="dd5ea-261">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="dd5ea-262">GRPC</span><span class="sxs-lookup"><span data-stu-id="dd5ea-262">grpc</span></span>](#web-others)             | <span data-ttu-id="dd5ea-263">Þ</span><span class="sxs-lookup"><span data-stu-id="dd5ea-263">[C#]</span></span>         | <span data-ttu-id="dd5ea-264">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="dd5ea-264">Web/gRPC</span></span>                              | <span data-ttu-id="dd5ea-265">3.0</span><span class="sxs-lookup"><span data-stu-id="dd5ea-265">3.0</span></span>        |
| <span data-ttu-id="dd5ea-266">DotNet gitignore dosyası</span><span class="sxs-lookup"><span data-stu-id="dd5ea-266">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="dd5ea-267">Config</span><span class="sxs-lookup"><span data-stu-id="dd5ea-267">Config</span></span>                                | <span data-ttu-id="dd5ea-268">3.0</span><span class="sxs-lookup"><span data-stu-id="dd5ea-268">3.0</span></span>        |
| <span data-ttu-id="dd5ea-269">Dosya üzerinde global.js</span><span class="sxs-lookup"><span data-stu-id="dd5ea-269">global.json file</span></span>                             | [<span data-ttu-id="dd5ea-270">globaljson</span><span class="sxs-lookup"><span data-stu-id="dd5ea-270">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="dd5ea-271">Config</span><span class="sxs-lookup"><span data-stu-id="dd5ea-271">Config</span></span>                                | <span data-ttu-id="dd5ea-272">2.0</span><span class="sxs-lookup"><span data-stu-id="dd5ea-272">2.0</span></span>        |
| <span data-ttu-id="dd5ea-273">NuGet yapılandırması</span><span class="sxs-lookup"><span data-stu-id="dd5ea-273">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="dd5ea-274">Config</span><span class="sxs-lookup"><span data-stu-id="dd5ea-274">Config</span></span>                                | <span data-ttu-id="dd5ea-275">1.0</span><span class="sxs-lookup"><span data-stu-id="dd5ea-275">1.0</span></span>        |
| <span data-ttu-id="dd5ea-276">DotNet yerel araç bildirim dosyası</span><span class="sxs-lookup"><span data-stu-id="dd5ea-276">Dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="dd5ea-277">Config</span><span class="sxs-lookup"><span data-stu-id="dd5ea-277">Config</span></span>                                | <span data-ttu-id="dd5ea-278">3.0</span><span class="sxs-lookup"><span data-stu-id="dd5ea-278">3.0</span></span>        |
| <span data-ttu-id="dd5ea-279">Web yapılandırması</span><span class="sxs-lookup"><span data-stu-id="dd5ea-279">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="dd5ea-280">Config</span><span class="sxs-lookup"><span data-stu-id="dd5ea-280">Config</span></span>                                | <span data-ttu-id="dd5ea-281">1.0</span><span class="sxs-lookup"><span data-stu-id="dd5ea-281">1.0</span></span>        |
| <span data-ttu-id="dd5ea-282">Çözüm dosyası</span><span class="sxs-lookup"><span data-stu-id="dd5ea-282">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="dd5ea-283">Çözüm</span><span class="sxs-lookup"><span data-stu-id="dd5ea-283">Solution</span></span>                              | <span data-ttu-id="dd5ea-284">1.0</span><span class="sxs-lookup"><span data-stu-id="dd5ea-284">1.0</span></span>        |
| <span data-ttu-id="dd5ea-285">Protokol arabelleği dosyası</span><span class="sxs-lookup"><span data-stu-id="dd5ea-285">Protocol Buffer File</span></span>                         | [<span data-ttu-id="dd5ea-286">Proto</span><span class="sxs-lookup"><span data-stu-id="dd5ea-286">proto</span></span>](#namespace)             |              | <span data-ttu-id="dd5ea-287">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="dd5ea-287">Web/gRPC</span></span>                              | <span data-ttu-id="dd5ea-288">3.0</span><span class="sxs-lookup"><span data-stu-id="dd5ea-288">3.0</span></span>        |

## <a name="options"></a><span data-ttu-id="dd5ea-289">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="dd5ea-289">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="dd5ea-290">Bir şablon oluşturulmasına neden olacaksa, verilen komutun çalıştırılması durumunda ne olacağını gösteren bir Özet görüntüler.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-290">Displays a summary of what would happen if the given command were run if it would result in a template creation.</span></span> <span data-ttu-id="dd5ea-291">.NET Core 2,2 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-291">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="dd5ea-292">Var olan dosyaları değiştirebilse bile içeriğin oluşturulmasını zorlar.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-292">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="dd5ea-293">Seçilen şablon çıkış dizinindeki mevcut dosyaları geçersiz kılacağından bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-293">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="dd5ea-294">Komut için yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-294">Prints out help for the command.</span></span> <span data-ttu-id="dd5ea-295">`dotnet new`Komutun kendisi veya herhangi bir şablon için çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-295">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="dd5ea-296">Örneğin, `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-296">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="dd5ea-297">Veya tarafından belirtilen bir şablon paketini `PATH` kurar `NUGET_ID` .</span><span class="sxs-lookup"><span data-stu-id="dd5ea-297">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="dd5ea-298">Şablon paketinin bir ön sürümü sürümünü yüklemek istiyorsanız, sürümü biçiminde belirtmeniz gerekir `<package-name>::<package-version>` .</span><span class="sxs-lookup"><span data-stu-id="dd5ea-298">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="dd5ea-299">Varsayılan olarak, `dotnet new` \* en son kararlı paket sürümünü temsil eden sürüm için geçirir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-299">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="dd5ea-300">[Örnekler](#examples) bölümündeki bir örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-300">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="dd5ea-301">Bu komutu çalıştırdığınızda şablonun bir sürümü zaten yüklüyse, şablon belirtilen sürüme veya sürüm belirtilmemişse en son kararlı sürüme güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-301">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="dd5ea-302">Özel şablonlar oluşturma hakkında daha fazla bilgi için bkz. [DotNet New Için özel şablonlar](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="dd5ea-302">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="dd5ea-303">Belirtilen adı içeren şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-303">Lists templates containing the specified name.</span></span> <span data-ttu-id="dd5ea-304">Ad belirtilmemişse, tüm şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-304">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="dd5ea-305">Oluşturulacak şablonun dili.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-305">The language of the template to create.</span></span> <span data-ttu-id="dd5ea-306">Kabul edilen dil şablona göre değişir (bkz. [arguments](#arguments) bölümünde Varsayılanlar).</span><span class="sxs-lookup"><span data-stu-id="dd5ea-306">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="dd5ea-307">Bazı şablonlar için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-307">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="dd5ea-308">Bazı kabuklar `#` özel bir karakter olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-308">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="dd5ea-309">Bu durumlarda, dil parametre değerini tırnak içine alın.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-309">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="dd5ea-310">Örneğin, `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-310">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="dd5ea-311">Oluşturulan çıkışın adı.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-311">The name for the created output.</span></span> <span data-ttu-id="dd5ea-312">Ad belirtilmemişse, geçerli dizinin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-312">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source <SOURCE>`**

  <span data-ttu-id="dd5ea-313">Yüklemesi sırasında kullanılacak bir NuGet kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-313">Specifies a NuGet source to use during install.</span></span> <span data-ttu-id="dd5ea-314">.NET Core 2,1 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-314">Available since .NET Core 2.1 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="dd5ea-315">Oluşturulan çıkışın yerleştirileceği konum.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-315">Location to place the generated output.</span></span> <span data-ttu-id="dd5ea-316">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-316">The default is the current directory.</span></span>

- **`--type <TYPE>`**

  <span data-ttu-id="dd5ea-317">Şablonları kullanılabilir türlerine göre filtreler.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-317">Filters templates based on available types.</span></span> <span data-ttu-id="dd5ea-318">Önceden tanımlanmış değerler `project` ve ' dir `item` .</span><span class="sxs-lookup"><span data-stu-id="dd5ea-318">Predefined values are `project` and `item`.</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="dd5ea-319">Veya belirtilen bir şablon paketini kaldırır `PATH` `NUGET_ID` .</span><span class="sxs-lookup"><span data-stu-id="dd5ea-319">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="dd5ea-320">`<PATH|NUGET_ID>`Değer belirtilmediğinde, yüklü olan tüm şablon paketleri ve bunlarla ilişkili şablonlar görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-320">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="dd5ea-321">Belirtirken `NUGET_ID` , sürüm numarasını eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-321">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="dd5ea-322">Bu seçeneğe bir parametre belirtmezseniz, komut, yüklü şablonları ve bunlarla ilgili ayrıntıları listeler.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-322">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="dd5ea-323">Bir şablonu kullanarak kaldırmak için `PATH` , yolu tam olarak nitelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-323">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="dd5ea-324">Örneğin, *C:/Users/ \<USER> /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* çalışır, ancak içeren klasörden *./GarciaSoftware.ConsoleTemplate.CSharp* olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-324">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="dd5ea-325">Şablon yolunuzda son Sonlandırıcı Dizin eğik çizgisi eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-325">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="dd5ea-326">Şu anda yüklü olan şablon paketleri için kullanılabilir güncelleştirmelerin olup olmadığını denetler ve bunları kurar.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-326">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="dd5ea-327">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-327">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="dd5ea-328">Şu anda yüklü olan şablon paketleri için kullanılabilir güncelleştirmeler olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-328">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="dd5ea-329">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-329">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="dd5ea-330">Şablon seçenekleri</span><span class="sxs-lookup"><span data-stu-id="dd5ea-330">Template options</span></span>

<span data-ttu-id="dd5ea-331">Her proje şablonunda ek seçenekler bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-331">Each project template may have additional options available.</span></span> <span data-ttu-id="dd5ea-332">Çekirdek şablonlar aşağıdaki ek seçeneklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="dd5ea-332">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="dd5ea-333">console</span><span class="sxs-lookup"><span data-stu-id="dd5ea-333">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="dd5ea-334">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-334">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="dd5ea-335">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-335">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="dd5ea-336">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="dd5ea-336">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="dd5ea-337">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="dd5ea-337">SDK version</span></span> | <span data-ttu-id="dd5ea-338">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="dd5ea-338">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="dd5ea-339">3,1</span><span class="sxs-lookup"><span data-stu-id="dd5ea-339">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="dd5ea-340">3.0</span><span class="sxs-lookup"><span data-stu-id="dd5ea-340">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="dd5ea-341">`LangVersion`Oluşturulan proje dosyasındaki özelliği ayarlar.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-341">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="dd5ea-342">Örneğin, `--langVersion 7.3` C# 7,3 kullanmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-342">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="dd5ea-343">F # için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-343">Not supported for F#.</span></span> <span data-ttu-id="dd5ea-344">.NET Core 2,2 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-344">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="dd5ea-345">Varsayılan C# sürümlerinin listesi için bkz. [Varsayılanlar](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="dd5ea-345">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="dd5ea-346">Belirtilmişse, proje oluşturma sırasında örtük geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-346">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="dd5ea-347">.NET Core 2,2 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-347">Available since .NET Core 2.2 SDK.</span></span>

<span data-ttu-id="dd5ea-348">\*\*_</span><span class="sxs-lookup"><span data-stu-id="dd5ea-348">\*\*_</span></span>

### <a name="classlib"></a><span data-ttu-id="dd5ea-349">projesinin</span><span class="sxs-lookup"><span data-stu-id="dd5ea-349">classlib</span></span>

- <span data-ttu-id="dd5ea-350">_*`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="dd5ea-350">_*`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="dd5ea-351">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-351">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="dd5ea-352">Değerler: `netcoreapp<version>` bir .NET Core sınıf kitaplığı oluşturmak veya `netstandard<version>` bir .NET Standard sınıf kitaplığı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-352">Values: `netcoreapp<version>` to create a .NET Core Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="dd5ea-353">`netstandard2.0` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-353">The default value is `netstandard2.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="dd5ea-354">`LangVersion`Oluşturulan proje dosyasındaki özelliği ayarlar.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-354">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="dd5ea-355">Örneğin, `--langVersion 7.3` C# 7,3 kullanmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-355">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="dd5ea-356">F # için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-356">Not supported for F#.</span></span> <span data-ttu-id="dd5ea-357">.NET Core 2,2 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-357">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="dd5ea-358">Varsayılan C# sürümlerinin listesi için bkz. [Varsayılanlar](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="dd5ea-358">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="dd5ea-359">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-359">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="dd5ea-360">\*\*_</span><span class="sxs-lookup"><span data-stu-id="dd5ea-360">\*\*_</span></span>

### <a name="wpf-wpflib-wpfcustomcontrollib-wpfusercontrollib"></a><a name="wpf"></a> <span data-ttu-id="dd5ea-361">WPF, wpflib, wpfcustomcontrollib, wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="dd5ea-361">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- <span data-ttu-id="dd5ea-362">_*`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="dd5ea-362">_*`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="dd5ea-363">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-363">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="dd5ea-364">`netcoreapp3.1` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-364">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="dd5ea-365">.NET Core 3,1 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-365">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="dd5ea-366">`LangVersion`Oluşturulan proje dosyasındaki özelliği ayarlar.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-366">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="dd5ea-367">Örneğin, `--langVersion 7.3` C# 7,3 kullanmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-367">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="dd5ea-368">Varsayılan C# sürümlerinin listesi için bkz. [Varsayılanlar](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="dd5ea-368">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="dd5ea-369">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-369">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="dd5ea-370">\*\*_</span><span class="sxs-lookup"><span data-stu-id="dd5ea-370">\*\*_</span></span>

### <a name="winforms-winformslib"></a><a name="winforms"></a> <span data-ttu-id="dd5ea-371">WinForms, winformslib</span><span class="sxs-lookup"><span data-stu-id="dd5ea-371">winforms, winformslib</span></span>

- <span data-ttu-id="dd5ea-372">_*`--langVersion <VERSION_NUMBER>`*\*</span><span class="sxs-lookup"><span data-stu-id="dd5ea-372">_*`--langVersion <VERSION_NUMBER>`*\*</span></span>

  <span data-ttu-id="dd5ea-373">`LangVersion`Oluşturulan proje dosyasındaki özelliği ayarlar.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-373">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="dd5ea-374">Örneğin, `--langVersion 7.3` C# 7,3 kullanmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-374">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="dd5ea-375">Varsayılan C# sürümlerinin listesi için bkz. [Varsayılanlar](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="dd5ea-375">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="dd5ea-376">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-376">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="dd5ea-377">\*\*_</span><span class="sxs-lookup"><span data-stu-id="dd5ea-377">\*\*_</span></span>

### <a name="worker-grpc"></a><a name="web-others"></a> <span data-ttu-id="dd5ea-378">çalışan, GRPC</span><span class="sxs-lookup"><span data-stu-id="dd5ea-378">worker, grpc</span></span>

- <span data-ttu-id="dd5ea-379">_*`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="dd5ea-379">_*`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="dd5ea-380">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-380">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="dd5ea-381">`netcoreapp3.1` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-381">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="dd5ea-382">.NET Core 3,1 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-382">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="dd5ea-383">Oluşturulan şablondan *launchSettings.js* dışlar.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-383">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="dd5ea-384">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-384">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="dd5ea-385">\*\*_</span><span class="sxs-lookup"><span data-stu-id="dd5ea-385">\*\*_</span></span>

### <a name="mstest-xunit"></a><a name="test"></a> <span data-ttu-id="dd5ea-386">MSTest, xUnit</span><span class="sxs-lookup"><span data-stu-id="dd5ea-386">mstest, xunit</span></span>

- <span data-ttu-id="dd5ea-387">_*`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="dd5ea-387">_*`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="dd5ea-388">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-388">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="dd5ea-389">.NET Core 3,0 SDK 'dan beri kullanılabilir seçeneği.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-389">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="dd5ea-390">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="dd5ea-390">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="dd5ea-391">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="dd5ea-391">SDK version</span></span> | <span data-ttu-id="dd5ea-392">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="dd5ea-392">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="dd5ea-393">3,1</span><span class="sxs-lookup"><span data-stu-id="dd5ea-393">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="dd5ea-394">3.0</span><span class="sxs-lookup"><span data-stu-id="dd5ea-394">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="dd5ea-395">[DotNet Pack](dotnet-pack.md)kullanarak proje için paketleme imkanı sunar.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-395">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="dd5ea-396">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-396">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="dd5ea-397">\*\*_</span><span class="sxs-lookup"><span data-stu-id="dd5ea-397">\*\*_</span></span>

### <a name="nunit"></a><span data-ttu-id="dd5ea-398">NUnit</span><span class="sxs-lookup"><span data-stu-id="dd5ea-398">nunit</span></span>

- <span data-ttu-id="dd5ea-399">_*`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="dd5ea-399">_*`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="dd5ea-400">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-400">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="dd5ea-401">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="dd5ea-401">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="dd5ea-402">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="dd5ea-402">SDK version</span></span> | <span data-ttu-id="dd5ea-403">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="dd5ea-403">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="dd5ea-404">3,1</span><span class="sxs-lookup"><span data-stu-id="dd5ea-404">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="dd5ea-405">3.0</span><span class="sxs-lookup"><span data-stu-id="dd5ea-405">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="dd5ea-406">2.2</span><span class="sxs-lookup"><span data-stu-id="dd5ea-406">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="dd5ea-407">2.1</span><span class="sxs-lookup"><span data-stu-id="dd5ea-407">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="dd5ea-408">[DotNet Pack](dotnet-pack.md)kullanarak proje için paketleme imkanı sunar.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-408">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="dd5ea-409">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-409">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="dd5ea-410">\*\*_</span><span class="sxs-lookup"><span data-stu-id="dd5ea-410">\*\*_</span></span>

### <a name="page"></a><span data-ttu-id="dd5ea-411">sayfasında</span><span class="sxs-lookup"><span data-stu-id="dd5ea-411">page</span></span>

- <span data-ttu-id="dd5ea-412">_*`-na|--namespace <NAMESPACE_NAME>`*\*</span><span class="sxs-lookup"><span data-stu-id="dd5ea-412">_*`-na|--namespace <NAMESPACE_NAME>`*\*</span></span>

  <span data-ttu-id="dd5ea-413">Oluşturulan kod için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-413">Namespace for the generated code.</span></span> <span data-ttu-id="dd5ea-414">`MyApp.Namespace` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-414">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="dd5ea-415">PageModel olmadan sayfayı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-415">Creates the page without a PageModel.</span></span>

<span data-ttu-id="dd5ea-416">\*\*_</span><span class="sxs-lookup"><span data-stu-id="dd5ea-416">\*\*_</span></span>

### <a name="viewimports-proto"></a><a name="namespace"></a> <span data-ttu-id="dd5ea-417">viewıtemler, Proto</span><span class="sxs-lookup"><span data-stu-id="dd5ea-417">viewimports, proto</span></span>

- <span data-ttu-id="dd5ea-418">_*`-na|--namespace <NAMESPACE_NAME>`*\*</span><span class="sxs-lookup"><span data-stu-id="dd5ea-418">_*`-na|--namespace <NAMESPACE_NAME>`*\*</span></span>

  <span data-ttu-id="dd5ea-419">Oluşturulan kod için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-419">Namespace for the generated code.</span></span> <span data-ttu-id="dd5ea-420">`MyApp.Namespace` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-420">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="dd5ea-421">\*\*_</span><span class="sxs-lookup"><span data-stu-id="dd5ea-421">\*\*_</span></span>

### <a name="blazorserver"></a><span data-ttu-id="dd5ea-422">blazorserver</span><span class="sxs-lookup"><span data-stu-id="dd5ea-422">blazorserver</span></span>

- <span data-ttu-id="dd5ea-423">_*`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="dd5ea-423">_*`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="dd5ea-424">Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-424">The type of authentication to use.</span></span> <span data-ttu-id="dd5ea-425">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="dd5ea-425">The possible values are:</span></span>

  - <span data-ttu-id="dd5ea-426">`None` -Kimlik doğrulaması yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="dd5ea-426">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="dd5ea-427">`Individual` -Bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-427">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="dd5ea-428">`IndividualB2C` -Azure AD B2C ile bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-428">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="dd5ea-429">`SingleOrg` -Tek bir kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-429">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="dd5ea-430">`MultiOrg` -Birden çok kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-430">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="dd5ea-431">`Windows` -Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-431">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="dd5ea-432">Bağlanılacak Azure Active Directory B2C örneği.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-432">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="dd5ea-433">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-433">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="dd5ea-434">`https://login.microsoftonline.com/tfp/` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-434">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="dd5ea-435">Bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-435">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="dd5ea-436">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-436">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="dd5ea-437">Bu proje için parola sıfırlama ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-437">The reset password policy ID for this project.</span></span> <span data-ttu-id="dd5ea-438">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-438">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="dd5ea-439">Bu proje için profil ilke KIMLIĞINI Düzenle.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-439">The edit profile policy ID for this project.</span></span> <span data-ttu-id="dd5ea-440">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-440">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="dd5ea-441">Bağlanılacak Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-441">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="dd5ea-442">`SingleOrg`Veya `MultiOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-442">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="dd5ea-443">`https://login.microsoftonline.com/` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-443">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="dd5ea-444">Bu projenin Istemci KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-444">The Client ID for this project.</span></span> <span data-ttu-id="dd5ea-445">`IndividualB2C`, `SingleOrg` Veya `MultiOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-445">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="dd5ea-446">`11111111-1111-1111-11111111111111111` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-446">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="dd5ea-447">Dizin kiracının etki alanı.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-447">The domain for the directory tenant.</span></span> <span data-ttu-id="dd5ea-448">`SingleOrg`Veya `IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-448">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="dd5ea-449">`qualified.domain.name` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-449">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="dd5ea-450">Bağlanılacak dizinin Tenantıd KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-450">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="dd5ea-451">`SingleOrg`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-451">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="dd5ea-452">`22222222-2222-2222-2222-222222222222` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-452">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="dd5ea-453">Uygulamanın yeniden yönlendirme URI 'sinin temel yolundaki istek yolu.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-453">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="dd5ea-454">`SingleOrg`Veya `IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-454">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="dd5ea-455">`/signin-oidc` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-455">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="dd5ea-456">Bu uygulamanın dizine okuma erişimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-456">Allows this application read-access to the directory.</span></span> <span data-ttu-id="dd5ea-457">Yalnızca `SingleOrg` veya `MultiOrg` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-457">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="dd5ea-458">Oluşturulan şablondan *launchSettings.js* dışlar.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-458">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="dd5ea-459">HTTPS 'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-459">Turns off HTTPS.</span></span> <span data-ttu-id="dd5ea-460">Bu seçenek yalnızca,, `Individual` , `IndividualB2C` `SingleOrg` veya için kullanılmıyorsa geçerlidir `MultiOrg` `--auth` .</span><span class="sxs-lookup"><span data-stu-id="dd5ea-460">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="dd5ea-461">SQLite yerine LocalDB kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-461">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="dd5ea-462">Yalnızca `Individual` veya `IndividualB2C` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-462">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="dd5ea-463">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-463">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="dd5ea-464">\*\*_</span><span class="sxs-lookup"><span data-stu-id="dd5ea-464">\*\*_</span></span>

### <a name="web"></a><span data-ttu-id="dd5ea-465">web</span><span class="sxs-lookup"><span data-stu-id="dd5ea-465">web</span></span>

- <span data-ttu-id="dd5ea-466">_*`--exclude-launch-settings`*\*</span><span class="sxs-lookup"><span data-stu-id="dd5ea-466">_*`--exclude-launch-settings`*\*</span></span>

  <span data-ttu-id="dd5ea-467">Oluşturulan şablondan *launchSettings.js* dışlar.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-467">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="dd5ea-468">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-468">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="dd5ea-469">Seçenek .NET Core 2,2 SDK sürümünde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-469">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="dd5ea-470">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="dd5ea-470">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="dd5ea-471">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="dd5ea-471">SDK version</span></span> | <span data-ttu-id="dd5ea-472">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="dd5ea-472">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="dd5ea-473">3,1</span><span class="sxs-lookup"><span data-stu-id="dd5ea-473">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="dd5ea-474">3.0</span><span class="sxs-lookup"><span data-stu-id="dd5ea-474">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="dd5ea-475">2.1</span><span class="sxs-lookup"><span data-stu-id="dd5ea-475">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="dd5ea-476">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-476">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="dd5ea-477">HTTPS 'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-477">Turns off HTTPS.</span></span>

<span data-ttu-id="dd5ea-478">\*\*_</span><span class="sxs-lookup"><span data-stu-id="dd5ea-478">\*\*_</span></span>

### <a name="mvc-webapp"></a><a name="web-options"></a> <span data-ttu-id="dd5ea-479">MVC, WebApp</span><span class="sxs-lookup"><span data-stu-id="dd5ea-479">mvc, webapp</span></span>

- <span data-ttu-id="dd5ea-480">_*`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="dd5ea-480">_*`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="dd5ea-481">Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-481">The type of authentication to use.</span></span> <span data-ttu-id="dd5ea-482">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="dd5ea-482">The possible values are:</span></span>

  - <span data-ttu-id="dd5ea-483">`None` -Kimlik doğrulaması yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="dd5ea-483">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="dd5ea-484">`Individual` -Bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-484">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="dd5ea-485">`IndividualB2C` -Azure AD B2C ile bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-485">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="dd5ea-486">`SingleOrg` -Tek bir kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-486">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="dd5ea-487">`MultiOrg` -Birden çok kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-487">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="dd5ea-488">`Windows` -Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-488">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="dd5ea-489">Bağlanılacak Azure Active Directory B2C örneği.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-489">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="dd5ea-490">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-490">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="dd5ea-491">`https://login.microsoftonline.com/tfp/` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-491">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="dd5ea-492">Bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-492">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="dd5ea-493">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-493">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="dd5ea-494">Bu proje için parola sıfırlama ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-494">The reset password policy ID for this project.</span></span> <span data-ttu-id="dd5ea-495">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-495">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="dd5ea-496">Bu proje için profil ilke KIMLIĞINI Düzenle.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-496">The edit profile policy ID for this project.</span></span> <span data-ttu-id="dd5ea-497">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-497">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="dd5ea-498">Bağlanılacak Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-498">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="dd5ea-499">`SingleOrg`Veya `MultiOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-499">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="dd5ea-500">`https://login.microsoftonline.com/` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-500">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="dd5ea-501">Bu projenin Istemci KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-501">The Client ID for this project.</span></span> <span data-ttu-id="dd5ea-502">`IndividualB2C`, `SingleOrg` Veya `MultiOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-502">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="dd5ea-503">`11111111-1111-1111-11111111111111111` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-503">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="dd5ea-504">Dizin kiracının etki alanı.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-504">The domain for the directory tenant.</span></span> <span data-ttu-id="dd5ea-505">`SingleOrg`Veya `IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-505">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="dd5ea-506">`qualified.domain.name` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-506">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="dd5ea-507">Bağlanılacak dizinin Tenantıd KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-507">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="dd5ea-508">`SingleOrg`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-508">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="dd5ea-509">`22222222-2222-2222-2222-222222222222` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-509">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="dd5ea-510">Uygulamanın yeniden yönlendirme URI 'sinin temel yolundaki istek yolu.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-510">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="dd5ea-511">`SingleOrg`Veya `IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-511">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="dd5ea-512">`/signin-oidc` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-512">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="dd5ea-513">Bu uygulamanın dizine okuma erişimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-513">Allows this application read-access to the directory.</span></span> <span data-ttu-id="dd5ea-514">Yalnızca `SingleOrg` veya `MultiOrg` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-514">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="dd5ea-515">Oluşturulan şablondan *launchSettings.js* dışlar.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-515">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="dd5ea-516">HTTPS 'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-516">Turns off HTTPS.</span></span> <span data-ttu-id="dd5ea-517">Bu seçenek yalnızca,,, veya kullanılmıyorsa geçerlidir `Individual` `IndividualB2C` `SingleOrg` `MultiOrg` .</span><span class="sxs-lookup"><span data-stu-id="dd5ea-517">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="dd5ea-518">SQLite yerine LocalDB kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-518">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="dd5ea-519">Yalnızca `Individual` veya `IndividualB2C` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-519">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="dd5ea-520">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-520">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="dd5ea-521">.NET Core 3,0 SDK 'dan beri kullanılabilir seçeneği.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-521">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="dd5ea-522">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="dd5ea-522">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="dd5ea-523">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="dd5ea-523">SDK version</span></span> | <span data-ttu-id="dd5ea-524">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="dd5ea-524">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="dd5ea-525">3,1</span><span class="sxs-lookup"><span data-stu-id="dd5ea-525">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="dd5ea-526">3.0</span><span class="sxs-lookup"><span data-stu-id="dd5ea-526">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="dd5ea-527">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-527">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="dd5ea-528">Projedeki BrowserLink öğesini içerir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-528">Includes BrowserLink in the project.</span></span> <span data-ttu-id="dd5ea-529">Seçenek .NET Core 2,2 ve 3,1 SDK sürümünde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-529">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

- **`-rrc|--razor-runtime-compilation`**

  <span data-ttu-id="dd5ea-530">Projenin hata ayıklama yapılarında [Razor çalışma zamanı derlemesini](/aspnet/core/mvc/views/view-compilation#runtime-compilation) kullanmak üzere yapılandırılıp yapılandırılmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-530">Determines if the project is configured to use [Razor runtime compilation](/aspnet/core/mvc/views/view-compilation#runtime-compilation) in Debug builds.</span></span> <span data-ttu-id="dd5ea-531">.NET Core 3.1.201 SDK 'dan beri kullanılabilir seçeneği.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-531">Option available since .NET Core 3.1.201 SDK.</span></span>

<span data-ttu-id="dd5ea-532">\*\*_</span><span class="sxs-lookup"><span data-stu-id="dd5ea-532">\*\*_</span></span>

### <a name="angular-react"></a><a name="spa"></a> <span data-ttu-id="dd5ea-533">Angular, tepki verme</span><span class="sxs-lookup"><span data-stu-id="dd5ea-533">angular, react</span></span>

- <span data-ttu-id="dd5ea-534">_*`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="dd5ea-534">_*`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="dd5ea-535">Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-535">The type of authentication to use.</span></span> <span data-ttu-id="dd5ea-536">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-536">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="dd5ea-537">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="dd5ea-537">The possible values are:</span></span>

  - <span data-ttu-id="dd5ea-538">`None` -Kimlik doğrulaması yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="dd5ea-538">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="dd5ea-539">`Individual` -Bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-539">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="dd5ea-540">Oluşturulan şablondan *launchSettings.js* dışlar.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-540">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="dd5ea-541">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-541">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="dd5ea-542">HTTPS 'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-542">Turns off HTTPS.</span></span> <span data-ttu-id="dd5ea-543">Bu seçenek yalnızca kimlik doğrulaması ise geçerlidir `None` .</span><span class="sxs-lookup"><span data-stu-id="dd5ea-543">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="dd5ea-544">SQLite yerine LocalDB kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-544">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="dd5ea-545">Yalnızca `Individual` veya `IndividualB2C` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-545">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="dd5ea-546">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-546">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="dd5ea-547">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-547">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="dd5ea-548">Seçenek .NET Core 2,2 SDK sürümünde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-548">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="dd5ea-549">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="dd5ea-549">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="dd5ea-550">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="dd5ea-550">SDK version</span></span> | <span data-ttu-id="dd5ea-551">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="dd5ea-551">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="dd5ea-552">3,1</span><span class="sxs-lookup"><span data-stu-id="dd5ea-552">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="dd5ea-553">3.0</span><span class="sxs-lookup"><span data-stu-id="dd5ea-553">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="dd5ea-554">2.1</span><span class="sxs-lookup"><span data-stu-id="dd5ea-554">2.1</span></span>         | `netcoreapp2.0` |

<span data-ttu-id="dd5ea-555">\*\*_</span><span class="sxs-lookup"><span data-stu-id="dd5ea-555">\*\*_</span></span>

### <a name="reactredux"></a><span data-ttu-id="dd5ea-556">reactredux</span><span class="sxs-lookup"><span data-stu-id="dd5ea-556">reactredux</span></span>

- <span data-ttu-id="dd5ea-557">_*`--exclude-launch-settings`*\*</span><span class="sxs-lookup"><span data-stu-id="dd5ea-557">_*`--exclude-launch-settings`*\*</span></span>

  <span data-ttu-id="dd5ea-558">Oluşturulan şablondan *launchSettings.js* dışlar.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-558">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="dd5ea-559">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-559">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="dd5ea-560">Seçenek .NET Core 2,2 SDK sürümünde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-560">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="dd5ea-561">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="dd5ea-561">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="dd5ea-562">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="dd5ea-562">SDK version</span></span> | <span data-ttu-id="dd5ea-563">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="dd5ea-563">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="dd5ea-564">3,1</span><span class="sxs-lookup"><span data-stu-id="dd5ea-564">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="dd5ea-565">3.0</span><span class="sxs-lookup"><span data-stu-id="dd5ea-565">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="dd5ea-566">2.1</span><span class="sxs-lookup"><span data-stu-id="dd5ea-566">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="dd5ea-567">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-567">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="dd5ea-568">HTTPS 'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-568">Turns off HTTPS.</span></span>

<span data-ttu-id="dd5ea-569">\*\*_</span><span class="sxs-lookup"><span data-stu-id="dd5ea-569">\*\*_</span></span>

### <a name="razorclasslib"></a><span data-ttu-id="dd5ea-570">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="dd5ea-570">razorclasslib</span></span>

- <span data-ttu-id="dd5ea-571">_*`--no-restore`*\*</span><span class="sxs-lookup"><span data-stu-id="dd5ea-571">_*`--no-restore`*\*</span></span>

  <span data-ttu-id="dd5ea-572">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-572">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="dd5ea-573">, Bu kitaplığa bileşenlere ek olarak geleneksel Razor sayfaları ve görünümleri eklenmesini destekler.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-573">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="dd5ea-574">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-574">Available since .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="dd5ea-575">\*\*_</span><span class="sxs-lookup"><span data-stu-id="dd5ea-575">\*\*_</span></span>
  
### <a name="webapi"></a><span data-ttu-id="dd5ea-576">WebApi</span><span class="sxs-lookup"><span data-stu-id="dd5ea-576">webapi</span></span>

- <span data-ttu-id="dd5ea-577">_*`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="dd5ea-577">_*`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="dd5ea-578">Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-578">The type of authentication to use.</span></span> <span data-ttu-id="dd5ea-579">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="dd5ea-579">The possible values are:</span></span>

  - <span data-ttu-id="dd5ea-580">`None` -Kimlik doğrulaması yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="dd5ea-580">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="dd5ea-581">`IndividualB2C` -Azure AD B2C ile bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-581">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="dd5ea-582">`SingleOrg` -Tek bir kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-582">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="dd5ea-583">`Windows` -Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-583">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="dd5ea-584">Bağlanılacak Azure Active Directory B2C örneği.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-584">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="dd5ea-585">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-585">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="dd5ea-586">`https://login.microsoftonline.com/tfp/` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-586">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="dd5ea-587">Bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-587">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="dd5ea-588">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-588">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="dd5ea-589">Bağlanılacak Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-589">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="dd5ea-590">`SingleOrg`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-590">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="dd5ea-591">`https://login.microsoftonline.com/` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-591">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="dd5ea-592">Bu projenin Istemci KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-592">The Client ID for this project.</span></span> <span data-ttu-id="dd5ea-593">`IndividualB2C`Veya `SingleOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-593">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="dd5ea-594">`11111111-1111-1111-11111111111111111` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-594">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="dd5ea-595">Dizin kiracının etki alanı.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-595">The domain for the directory tenant.</span></span> <span data-ttu-id="dd5ea-596">`IndividualB2C`Veya `SingleOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-596">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="dd5ea-597">`qualified.domain.name` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-597">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="dd5ea-598">Bağlanılacak dizinin Tenantıd KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-598">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="dd5ea-599">`SingleOrg`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-599">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="dd5ea-600">`22222222-2222-2222-2222-222222222222` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-600">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="dd5ea-601">Bu uygulamanın dizine okuma erişimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-601">Allows this application read-access to the directory.</span></span> <span data-ttu-id="dd5ea-602">Yalnızca `SingleOrg` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-602">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="dd5ea-603">Oluşturulan şablondan *launchSettings.js* dışlar.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-603">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="dd5ea-604">HTTPS 'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-604">Turns off HTTPS.</span></span> <span data-ttu-id="dd5ea-605">`app.UseHsts` ve `app.UseHttpsRedirection` öğesine eklenmez `Startup.Configure` .</span><span class="sxs-lookup"><span data-stu-id="dd5ea-605">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="dd5ea-606">Bu seçenek yalnızca `IndividualB2C` `SingleOrg` kimlik doğrulaması için kullanılmıyorsa geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-606">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="dd5ea-607">SQLite yerine LocalDB kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-607">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="dd5ea-608">Yalnızca `IndividualB2C` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-608">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="dd5ea-609">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-609">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="dd5ea-610">Seçenek .NET Core 2,2 SDK sürümünde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-610">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="dd5ea-611">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="dd5ea-611">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="dd5ea-612">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="dd5ea-612">SDK version</span></span> | <span data-ttu-id="dd5ea-613">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="dd5ea-613">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="dd5ea-614">3,1</span><span class="sxs-lookup"><span data-stu-id="dd5ea-614">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="dd5ea-615">3.0</span><span class="sxs-lookup"><span data-stu-id="dd5ea-615">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="dd5ea-616">2.1</span><span class="sxs-lookup"><span data-stu-id="dd5ea-616">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="dd5ea-617">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-617">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="dd5ea-618">\*\*_</span><span class="sxs-lookup"><span data-stu-id="dd5ea-618">\*\*_</span></span>

### <a name="globaljson"></a><span data-ttu-id="dd5ea-619">globaljson</span><span class="sxs-lookup"><span data-stu-id="dd5ea-619">globaljson</span></span>

- <span data-ttu-id="dd5ea-620">_*`--sdk-version <VERSION_NUMBER>`*\*</span><span class="sxs-lookup"><span data-stu-id="dd5ea-620">_*`--sdk-version <VERSION_NUMBER>`*\*</span></span>

  <span data-ttu-id="dd5ea-621">*global.json* dosyasında kullanılacak .NET Core SDK sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-621">Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="dd5ea-622">Örnekler</span><span class="sxs-lookup"><span data-stu-id="dd5ea-622">Examples</span></span>

- <span data-ttu-id="dd5ea-623">Şablon adını belirterek bir C# konsol uygulaması projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="dd5ea-623">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="dd5ea-624">Geçerli dizinde bir F # konsol uygulaması projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="dd5ea-624">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang "F#"
  ```

- <span data-ttu-id="dd5ea-625">Belirtilen dizinde bir .NET Standard sınıf kitaplığı projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="dd5ea-625">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="dd5ea-626">Geçerli dizinde kimlik doğrulaması olmadan yeni bir ASP.NET Core C# MVC projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="dd5ea-626">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="dd5ea-627">Yeni bir xUnit projesi oluştur:</span><span class="sxs-lookup"><span data-stu-id="dd5ea-627">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="dd5ea-628">Tek sayfalı uygulama (SPA) şablonları için kullanılabilen tüm şablonları listeleyin:</span><span class="sxs-lookup"><span data-stu-id="dd5ea-628">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="dd5ea-629">*We* alt dizeniz ile eşleşen tüm şablonları listeleyin.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-629">List all templates matching the *we* substring.</span></span> <span data-ttu-id="dd5ea-630">Tam eşleşme bulunamadı, bu nedenle alt dize eşleştirmesi hem kısa ad hem de ad sütunlarında çalışır.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-630">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="dd5ea-631">Şablonla *eşleşen şablonu*çağırma girişimi.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-631">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="dd5ea-632">Tek bir eşleşme belirlenemiyorsa kısmi eşleşen şablonları listeleyin.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-632">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="dd5ea-633">ASP.NET Core için SPA şablonlarının 2,0 sürümünü yükler:</span><span class="sxs-lookup"><span data-stu-id="dd5ea-633">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="dd5ea-634">Yüklü şablonları ve bunlarla ilgili ayrıntıları, bunları kaldırma dahil olmak üzere listeleyin:</span><span class="sxs-lookup"><span data-stu-id="dd5ea-634">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="dd5ea-635">SDK sürümünü 3.1.101 olarak ayarlamak için geçerli dizinde bir *global.js* oluşturun:</span><span class="sxs-lookup"><span data-stu-id="dd5ea-635">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="dd5ea-636">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dd5ea-636">See also</span></span>

- [<span data-ttu-id="dd5ea-637">DotNet New için özel şablonlar</span><span class="sxs-lookup"><span data-stu-id="dd5ea-637">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="dd5ea-638">Dotnet new için özel şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="dd5ea-638">Create a custom template for dotnet new</span></span>](../tutorials/cli-templates-create-item-template.md)
- [<span data-ttu-id="dd5ea-639">DotNet/DotNet-şablon-örnek GitHub deposu</span><span class="sxs-lookup"><span data-stu-id="dd5ea-639">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="dd5ea-640">DotNet New için kullanılabilir şablonlar</span><span class="sxs-lookup"><span data-stu-id="dd5ea-640">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
