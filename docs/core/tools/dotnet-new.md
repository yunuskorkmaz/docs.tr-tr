---
title: DotNet yeni komut
description: DotNet New komutu, belirtilen şablona göre yeni .NET Core projeleri oluşturur.
no-loc:
- Blazor
- WebAssembly
ms.date: 04/10/2020
ms.openlocfilehash: ec41b3b79ed5eded7c9124d3e4d95c658ee39580
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173126"
---
# <a name="dotnet-new"></a><span data-ttu-id="bc5c1-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="bc5c1-103">dotnet new</span></span>

<span data-ttu-id="bc5c1-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,0 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="bc5c1-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="bc5c1-105">Ad</span><span class="sxs-lookup"><span data-stu-id="bc5c1-105">Name</span></span>

<span data-ttu-id="bc5c1-106">`dotnet new`-Belirtilen şablonu temel alan yeni bir proje, yapılandırma dosyası veya çözüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="bc5c1-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="bc5c1-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install {PATH|NUGET_ID}]
    [-lang|--language {"C#"|"F#"|VB}] [-n|--name <OUTPUT_NAME>]
    [--nuget-source <SOURCE>] [-o|--output <OUTPUT_DIRECTORY>]
    [-u|--uninstall] [--update-apply] [--update-check] [Template options]

dotnet new <TEMPLATE> [-l|--list] [--type <TYPE>]

dotnet new -h|--help
```

## <a name="description"></a><span data-ttu-id="bc5c1-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bc5c1-108">Description</span></span>

<span data-ttu-id="bc5c1-109">`dotnet new`Komut bir şablonu temel alan bir .NET Core projesi veya diğer yapılar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-109">The `dotnet new` command creates a .NET Core project or other artifacts based on a template.</span></span>

<span data-ttu-id="bc5c1-110">Komutu, belirtilen şablon ve seçeneklere göre diskteki yapıtları oluşturmak için [şablon altyapısını](https://github.com/dotnet/templating) çağırır.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="bc5c1-111">Örtük geri yükleme</span><span class="sxs-lookup"><span data-stu-id="bc5c1-111">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="bc5c1-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="bc5c1-112">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="bc5c1-113">Komut çağrıldığında örnek oluşturulacak şablon.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-113">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="bc5c1-114">Her şablonun geçirebilmeniz için özel seçenekleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-114">Each template might have specific options you can pass.</span></span> <span data-ttu-id="bc5c1-115">Daha fazla bilgi için bkz. [şablon seçenekleri](#template-options).</span><span class="sxs-lookup"><span data-stu-id="bc5c1-115">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="bc5c1-116">`dotnet new --list` `dotnet new -l` Tüm yüklü şablonların listesini görmek için veya çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-116">You can run `dotnet new --list` or `dotnet new -l` to see a list of all installed templates.</span></span> <span data-ttu-id="bc5c1-117">Değer, `TEMPLATE` döndürülen tablodaki **Şablonlar** veya **kısa ad** sütunundaki metinde tam eşleşme değilse, bu iki sütunda bir alt dize eşleşmesi gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-117">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="bc5c1-118">.NET Core 3,0 SDK ile başlayarak, aşağıdaki koşullarda komutu çağırdığınızda CLı NuGet.org içindeki şablonları arar `dotnet new` :</span><span class="sxs-lookup"><span data-stu-id="bc5c1-118">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="bc5c1-119">CLı çağrılırken bir şablon eşleşmesi bulamazsa `dotnet new` , bu da kısmi değildir.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-119">If the CLI can't find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="bc5c1-120">Şablonun daha yeni bir sürümü kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-120">If there's a newer version of the template available.</span></span> <span data-ttu-id="bc5c1-121">Bu durumda, proje veya yapıt oluşturulur ancak CLı, şablonun güncelleştirilmiş bir sürümü hakkında sizi uyarır.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-121">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="bc5c1-122">Aşağıdaki tabloda, .NET Core SDK ile önceden yüklenmiş olan şablonlar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-122">The following table shows the templates that come pre-installed with the .NET Core SDK.</span></span> <span data-ttu-id="bc5c1-123">Şablon için varsayılan dil, köşeli ayraçlar içinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-123">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="bc5c1-124">Özel şablon seçeneklerini görmek için kısa ad bağlantısına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-124">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="bc5c1-125">Şablonlar</span><span class="sxs-lookup"><span data-stu-id="bc5c1-125">Templates</span></span>                                    | <span data-ttu-id="bc5c1-126">Kısa ad</span><span class="sxs-lookup"><span data-stu-id="bc5c1-126">Short name</span></span>                      | <span data-ttu-id="bc5c1-127">Dil</span><span class="sxs-lookup"><span data-stu-id="bc5c1-127">Language</span></span>     | <span data-ttu-id="bc5c1-128">Etiketler</span><span class="sxs-lookup"><span data-stu-id="bc5c1-128">Tags</span></span>                                  | <span data-ttu-id="bc5c1-129">Dağıtıla</span><span class="sxs-lookup"><span data-stu-id="bc5c1-129">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="bc5c1-130">Konsol Uygulaması</span><span class="sxs-lookup"><span data-stu-id="bc5c1-130">Console Application</span></span>                          | [<span data-ttu-id="bc5c1-131">konsola</span><span class="sxs-lookup"><span data-stu-id="bc5c1-131">console</span></span>](#console)             | <span data-ttu-id="bc5c1-132">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="bc5c1-132">[C#], F#, VB</span></span> | <span data-ttu-id="bc5c1-133">Ortak/konsol</span><span class="sxs-lookup"><span data-stu-id="bc5c1-133">Common/Console</span></span>                        | <span data-ttu-id="bc5c1-134">1.0</span><span class="sxs-lookup"><span data-stu-id="bc5c1-134">1.0</span></span>        |
| <span data-ttu-id="bc5c1-135">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="bc5c1-135">Class library</span></span>                                | [<span data-ttu-id="bc5c1-136">projesinin</span><span class="sxs-lookup"><span data-stu-id="bc5c1-136">classlib</span></span>](#classlib)           | <span data-ttu-id="bc5c1-137">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="bc5c1-137">[C#], F#, VB</span></span> | <span data-ttu-id="bc5c1-138">Ortak/Kitaplık</span><span class="sxs-lookup"><span data-stu-id="bc5c1-138">Common/Library</span></span>                        | <span data-ttu-id="bc5c1-139">1.0</span><span class="sxs-lookup"><span data-stu-id="bc5c1-139">1.0</span></span>        |
| <span data-ttu-id="bc5c1-140">WPF uygulaması</span><span class="sxs-lookup"><span data-stu-id="bc5c1-140">WPF Application</span></span>                              | [<span data-ttu-id="bc5c1-141">WPF</span><span class="sxs-lookup"><span data-stu-id="bc5c1-141">wpf</span></span>](#wpf)                     | <span data-ttu-id="bc5c1-142">Þ</span><span class="sxs-lookup"><span data-stu-id="bc5c1-142">[C#]</span></span>         | <span data-ttu-id="bc5c1-143">Ortak/WPF</span><span class="sxs-lookup"><span data-stu-id="bc5c1-143">Common/WPF</span></span>                            | <span data-ttu-id="bc5c1-144">3.0</span><span class="sxs-lookup"><span data-stu-id="bc5c1-144">3.0</span></span>        |
| <span data-ttu-id="bc5c1-145">WPF sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="bc5c1-145">WPF Class library</span></span>                            | [<span data-ttu-id="bc5c1-146">wpflib</span><span class="sxs-lookup"><span data-stu-id="bc5c1-146">wpflib</span></span>](#wpf)                  | <span data-ttu-id="bc5c1-147">Þ</span><span class="sxs-lookup"><span data-stu-id="bc5c1-147">[C#]</span></span>         | <span data-ttu-id="bc5c1-148">Ortak/WPF</span><span class="sxs-lookup"><span data-stu-id="bc5c1-148">Common/WPF</span></span>                            | <span data-ttu-id="bc5c1-149">3.0</span><span class="sxs-lookup"><span data-stu-id="bc5c1-149">3.0</span></span>        |
| <span data-ttu-id="bc5c1-150">WPF Özel Denetim Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="bc5c1-150">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="bc5c1-151">wpfcustomcontrollib</span><span class="sxs-lookup"><span data-stu-id="bc5c1-151">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="bc5c1-152">Þ</span><span class="sxs-lookup"><span data-stu-id="bc5c1-152">[C#]</span></span>         | <span data-ttu-id="bc5c1-153">Ortak/WPF</span><span class="sxs-lookup"><span data-stu-id="bc5c1-153">Common/WPF</span></span>                            | <span data-ttu-id="bc5c1-154">3.0</span><span class="sxs-lookup"><span data-stu-id="bc5c1-154">3.0</span></span>        |
| <span data-ttu-id="bc5c1-155">WPF Kullanıcı denetimi kitaplığı</span><span class="sxs-lookup"><span data-stu-id="bc5c1-155">WPF User Control Library</span></span>                     | [<span data-ttu-id="bc5c1-156">wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="bc5c1-156">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="bc5c1-157">Þ</span><span class="sxs-lookup"><span data-stu-id="bc5c1-157">[C#]</span></span>         | <span data-ttu-id="bc5c1-158">Ortak/WPF</span><span class="sxs-lookup"><span data-stu-id="bc5c1-158">Common/WPF</span></span>                            | <span data-ttu-id="bc5c1-159">3.0</span><span class="sxs-lookup"><span data-stu-id="bc5c1-159">3.0</span></span>        |
| <span data-ttu-id="bc5c1-160">Windows Forms (WinForms) uygulaması</span><span class="sxs-lookup"><span data-stu-id="bc5c1-160">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="bc5c1-161">WinForms</span><span class="sxs-lookup"><span data-stu-id="bc5c1-161">winforms</span></span>](#winforms)           | <span data-ttu-id="bc5c1-162">Þ</span><span class="sxs-lookup"><span data-stu-id="bc5c1-162">[C#]</span></span>         | <span data-ttu-id="bc5c1-163">Ortak/WinForms</span><span class="sxs-lookup"><span data-stu-id="bc5c1-163">Common/WinForms</span></span>                       | <span data-ttu-id="bc5c1-164">3.0</span><span class="sxs-lookup"><span data-stu-id="bc5c1-164">3.0</span></span>        |
| <span data-ttu-id="bc5c1-165">Windows Forms (WinForms) sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="bc5c1-165">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="bc5c1-166">winformslib</span><span class="sxs-lookup"><span data-stu-id="bc5c1-166">winformslib</span></span>](#winforms)        | <span data-ttu-id="bc5c1-167">Þ</span><span class="sxs-lookup"><span data-stu-id="bc5c1-167">[C#]</span></span>         | <span data-ttu-id="bc5c1-168">Ortak/WinForms</span><span class="sxs-lookup"><span data-stu-id="bc5c1-168">Common/WinForms</span></span>                       | <span data-ttu-id="bc5c1-169">3.0</span><span class="sxs-lookup"><span data-stu-id="bc5c1-169">3.0</span></span>        |
| <span data-ttu-id="bc5c1-170">Çalışan hizmeti</span><span class="sxs-lookup"><span data-stu-id="bc5c1-170">Worker Service</span></span>                               | [<span data-ttu-id="bc5c1-171">ından</span><span class="sxs-lookup"><span data-stu-id="bc5c1-171">worker</span></span>](#web-others)           | <span data-ttu-id="bc5c1-172">Þ</span><span class="sxs-lookup"><span data-stu-id="bc5c1-172">[C#]</span></span>         | <span data-ttu-id="bc5c1-173">Ortak/çalışan/Web</span><span class="sxs-lookup"><span data-stu-id="bc5c1-173">Common/Worker/Web</span></span>                     | <span data-ttu-id="bc5c1-174">3.0</span><span class="sxs-lookup"><span data-stu-id="bc5c1-174">3.0</span></span>        |
| <span data-ttu-id="bc5c1-175">Birim testi projesi</span><span class="sxs-lookup"><span data-stu-id="bc5c1-175">Unit Test Project</span></span>                            | [<span data-ttu-id="bc5c1-176">'i</span><span class="sxs-lookup"><span data-stu-id="bc5c1-176">mstest</span></span>](#test)                 | <span data-ttu-id="bc5c1-177">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="bc5c1-177">[C#], F#, VB</span></span> | <span data-ttu-id="bc5c1-178">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="bc5c1-178">Test/MSTest</span></span>                           | <span data-ttu-id="bc5c1-179">1.0</span><span class="sxs-lookup"><span data-stu-id="bc5c1-179">1.0</span></span>        |
| <span data-ttu-id="bc5c1-180">NUnit 3 test projesi</span><span class="sxs-lookup"><span data-stu-id="bc5c1-180">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="bc5c1-181">NUnit</span><span class="sxs-lookup"><span data-stu-id="bc5c1-181">nunit</span></span>](#nunit)                  | <span data-ttu-id="bc5c1-182">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="bc5c1-182">[C#], F#, VB</span></span> | <span data-ttu-id="bc5c1-183">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="bc5c1-183">Test/NUnit</span></span>                            | <span data-ttu-id="bc5c1-184">2.1.400</span><span class="sxs-lookup"><span data-stu-id="bc5c1-184">2.1.400</span></span>    |
| <span data-ttu-id="bc5c1-185">NUnit 3 test öğesi</span><span class="sxs-lookup"><span data-stu-id="bc5c1-185">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="bc5c1-186">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="bc5c1-186">[C#], F#, VB</span></span> | <span data-ttu-id="bc5c1-187">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="bc5c1-187">Test/NUnit</span></span>                            | <span data-ttu-id="bc5c1-188">2,2</span><span class="sxs-lookup"><span data-stu-id="bc5c1-188">2.2</span></span>        |
| <span data-ttu-id="bc5c1-189">xUnit test projesi</span><span class="sxs-lookup"><span data-stu-id="bc5c1-189">xUnit Test Project</span></span>                           | [<span data-ttu-id="bc5c1-190">xUnit</span><span class="sxs-lookup"><span data-stu-id="bc5c1-190">xunit</span></span>](#test)                  | <span data-ttu-id="bc5c1-191">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="bc5c1-191">[C#], F#, VB</span></span> | <span data-ttu-id="bc5c1-192">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="bc5c1-192">Test/xUnit</span></span>                            | <span data-ttu-id="bc5c1-193">1.0</span><span class="sxs-lookup"><span data-stu-id="bc5c1-193">1.0</span></span>        |
| <span data-ttu-id="bc5c1-194">Razor bileşeni</span><span class="sxs-lookup"><span data-stu-id="bc5c1-194">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="bc5c1-195">Þ</span><span class="sxs-lookup"><span data-stu-id="bc5c1-195">[C#]</span></span>         | <span data-ttu-id="bc5c1-196">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="bc5c1-196">Web/ASP.NET</span></span>                           | <span data-ttu-id="bc5c1-197">3.0</span><span class="sxs-lookup"><span data-stu-id="bc5c1-197">3.0</span></span>        |
| <span data-ttu-id="bc5c1-198">Razor sayfası</span><span class="sxs-lookup"><span data-stu-id="bc5c1-198">Razor Page</span></span>                                   | [<span data-ttu-id="bc5c1-199">sayfasında</span><span class="sxs-lookup"><span data-stu-id="bc5c1-199">page</span></span>](#page)                   | <span data-ttu-id="bc5c1-200">Þ</span><span class="sxs-lookup"><span data-stu-id="bc5c1-200">[C#]</span></span>         | <span data-ttu-id="bc5c1-201">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="bc5c1-201">Web/ASP.NET</span></span>                           | <span data-ttu-id="bc5c1-202">2.0</span><span class="sxs-lookup"><span data-stu-id="bc5c1-202">2.0</span></span>        |
| <span data-ttu-id="bc5c1-203">MVC Viewıtemts</span><span class="sxs-lookup"><span data-stu-id="bc5c1-203">MVC ViewImports</span></span>                              | [<span data-ttu-id="bc5c1-204">viewıtems 'lar</span><span class="sxs-lookup"><span data-stu-id="bc5c1-204">viewimports</span></span>](#namespace)       | <span data-ttu-id="bc5c1-205">Þ</span><span class="sxs-lookup"><span data-stu-id="bc5c1-205">[C#]</span></span>         | <span data-ttu-id="bc5c1-206">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="bc5c1-206">Web/ASP.NET</span></span>                           | <span data-ttu-id="bc5c1-207">2.0</span><span class="sxs-lookup"><span data-stu-id="bc5c1-207">2.0</span></span>        |
| <span data-ttu-id="bc5c1-208">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="bc5c1-208">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="bc5c1-209">Þ</span><span class="sxs-lookup"><span data-stu-id="bc5c1-209">[C#]</span></span>         | <span data-ttu-id="bc5c1-210">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="bc5c1-210">Web/ASP.NET</span></span>                           | <span data-ttu-id="bc5c1-211">2.0</span><span class="sxs-lookup"><span data-stu-id="bc5c1-211">2.0</span></span>        |
| Blazor<span data-ttu-id="bc5c1-212">Sunucu uygulaması</span><span class="sxs-lookup"><span data-stu-id="bc5c1-212"> Server App</span></span>                            | [<span data-ttu-id="bc5c1-213">blazorserver</span><span class="sxs-lookup"><span data-stu-id="bc5c1-213">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="bc5c1-214">Þ</span><span class="sxs-lookup"><span data-stu-id="bc5c1-214">[C#]</span></span>         | <span data-ttu-id="bc5c1-215">WebBlazor</span><span class="sxs-lookup"><span data-stu-id="bc5c1-215">Web/Blazor</span></span>                            | <span data-ttu-id="bc5c1-216">3.0</span><span class="sxs-lookup"><span data-stu-id="bc5c1-216">3.0</span></span>        |
| Blazor<span data-ttu-id="bc5c1-217">WebAssemblyUygulama</span><span class="sxs-lookup"><span data-stu-id="bc5c1-217"> WebAssembly App</span></span>                       | `blazorwasm`                    | <span data-ttu-id="bc5c1-218">Þ</span><span class="sxs-lookup"><span data-stu-id="bc5c1-218">[C#]</span></span>         | <span data-ttu-id="bc5c1-219">WebBlazor/WebAssembly</span><span class="sxs-lookup"><span data-stu-id="bc5c1-219">Web/Blazor/WebAssembly</span></span>                            | <span data-ttu-id="bc5c1-220">3.1.300</span><span class="sxs-lookup"><span data-stu-id="bc5c1-220">3.1.300</span></span>    |
| <span data-ttu-id="bc5c1-221">ASP.NET Core boş</span><span class="sxs-lookup"><span data-stu-id="bc5c1-221">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="bc5c1-222">Web</span><span class="sxs-lookup"><span data-stu-id="bc5c1-222">web</span></span>](#web)                     | <span data-ttu-id="bc5c1-223">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="bc5c1-223">[C#], F#</span></span>     | <span data-ttu-id="bc5c1-224">Web/boş</span><span class="sxs-lookup"><span data-stu-id="bc5c1-224">Web/Empty</span></span>                             | <span data-ttu-id="bc5c1-225">1.0</span><span class="sxs-lookup"><span data-stu-id="bc5c1-225">1.0</span></span>        |
| <span data-ttu-id="bc5c1-226">ASP.NET Core Web uygulaması (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="bc5c1-226">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="bc5c1-227">MVC</span><span class="sxs-lookup"><span data-stu-id="bc5c1-227">mvc</span></span>](#web-options)             | <span data-ttu-id="bc5c1-228">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="bc5c1-228">[C#], F#</span></span>     | <span data-ttu-id="bc5c1-229">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="bc5c1-229">Web/MVC</span></span>                               | <span data-ttu-id="bc5c1-230">1.0</span><span class="sxs-lookup"><span data-stu-id="bc5c1-230">1.0</span></span>        |
| <span data-ttu-id="bc5c1-231">ASP.NET Core Web uygulaması</span><span class="sxs-lookup"><span data-stu-id="bc5c1-231">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="bc5c1-232">WEBAPP, Razor</span><span class="sxs-lookup"><span data-stu-id="bc5c1-232">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="bc5c1-233">Þ</span><span class="sxs-lookup"><span data-stu-id="bc5c1-233">[C#]</span></span>         | <span data-ttu-id="bc5c1-234">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="bc5c1-234">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="bc5c1-235">2,2, 2,0</span><span class="sxs-lookup"><span data-stu-id="bc5c1-235">2.2, 2.0</span></span>   |
| <span data-ttu-id="bc5c1-236">Angular ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="bc5c1-236">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="bc5c1-237">Angular</span><span class="sxs-lookup"><span data-stu-id="bc5c1-237">angular</span></span>](#spa)                 | <span data-ttu-id="bc5c1-238">Þ</span><span class="sxs-lookup"><span data-stu-id="bc5c1-238">[C#]</span></span>         | <span data-ttu-id="bc5c1-239">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="bc5c1-239">Web/MVC/SPA</span></span>                           | <span data-ttu-id="bc5c1-240">2.0</span><span class="sxs-lookup"><span data-stu-id="bc5c1-240">2.0</span></span>        |
| <span data-ttu-id="bc5c1-241">React.js ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="bc5c1-241">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="bc5c1-242">tıkla</span><span class="sxs-lookup"><span data-stu-id="bc5c1-242">react</span></span>](#spa)                   | <span data-ttu-id="bc5c1-243">Þ</span><span class="sxs-lookup"><span data-stu-id="bc5c1-243">[C#]</span></span>         | <span data-ttu-id="bc5c1-244">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="bc5c1-244">Web/MVC/SPA</span></span>                           | <span data-ttu-id="bc5c1-245">2.0</span><span class="sxs-lookup"><span data-stu-id="bc5c1-245">2.0</span></span>        |
| <span data-ttu-id="bc5c1-246">React.js ve Redux ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="bc5c1-246">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="bc5c1-247">reactredux</span><span class="sxs-lookup"><span data-stu-id="bc5c1-247">reactredux</span></span>](#reactredux)       | <span data-ttu-id="bc5c1-248">Þ</span><span class="sxs-lookup"><span data-stu-id="bc5c1-248">[C#]</span></span>         | <span data-ttu-id="bc5c1-249">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="bc5c1-249">Web/MVC/SPA</span></span>                           | <span data-ttu-id="bc5c1-250">2.0</span><span class="sxs-lookup"><span data-stu-id="bc5c1-250">2.0</span></span>        |
| <span data-ttu-id="bc5c1-251">Razor sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="bc5c1-251">Razor Class Library</span></span>                          | [<span data-ttu-id="bc5c1-252">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="bc5c1-252">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="bc5c1-253">Þ</span><span class="sxs-lookup"><span data-stu-id="bc5c1-253">[C#]</span></span>         | <span data-ttu-id="bc5c1-254">Web/Razor/kitaplık/Razor sınıfı kitaplığı</span><span class="sxs-lookup"><span data-stu-id="bc5c1-254">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="bc5c1-255">2.1</span><span class="sxs-lookup"><span data-stu-id="bc5c1-255">2.1</span></span>        |
| <span data-ttu-id="bc5c1-256">ASP.NET Core Web API'si</span><span class="sxs-lookup"><span data-stu-id="bc5c1-256">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="bc5c1-257">WebApi</span><span class="sxs-lookup"><span data-stu-id="bc5c1-257">webapi</span></span>](#webapi)               | <span data-ttu-id="bc5c1-258">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="bc5c1-258">[C#], F#</span></span>     | <span data-ttu-id="bc5c1-259">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="bc5c1-259">Web/WebAPI</span></span>                            | <span data-ttu-id="bc5c1-260">1.0</span><span class="sxs-lookup"><span data-stu-id="bc5c1-260">1.0</span></span>        |
| <span data-ttu-id="bc5c1-261">ASP.NET Core gRPC hizmeti</span><span class="sxs-lookup"><span data-stu-id="bc5c1-261">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="bc5c1-262">GRPC</span><span class="sxs-lookup"><span data-stu-id="bc5c1-262">grpc</span></span>](#web-others)             | <span data-ttu-id="bc5c1-263">Þ</span><span class="sxs-lookup"><span data-stu-id="bc5c1-263">[C#]</span></span>         | <span data-ttu-id="bc5c1-264">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="bc5c1-264">Web/gRPC</span></span>                              | <span data-ttu-id="bc5c1-265">3.0</span><span class="sxs-lookup"><span data-stu-id="bc5c1-265">3.0</span></span>        |
| <span data-ttu-id="bc5c1-266">DotNet gitignore dosyası</span><span class="sxs-lookup"><span data-stu-id="bc5c1-266">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="bc5c1-267">Config</span><span class="sxs-lookup"><span data-stu-id="bc5c1-267">Config</span></span>                                | <span data-ttu-id="bc5c1-268">3.0</span><span class="sxs-lookup"><span data-stu-id="bc5c1-268">3.0</span></span>        |
| <span data-ttu-id="bc5c1-269">Dosya üzerinde global.js</span><span class="sxs-lookup"><span data-stu-id="bc5c1-269">global.json file</span></span>                             | [<span data-ttu-id="bc5c1-270">globaljson</span><span class="sxs-lookup"><span data-stu-id="bc5c1-270">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="bc5c1-271">Config</span><span class="sxs-lookup"><span data-stu-id="bc5c1-271">Config</span></span>                                | <span data-ttu-id="bc5c1-272">2.0</span><span class="sxs-lookup"><span data-stu-id="bc5c1-272">2.0</span></span>        |
| <span data-ttu-id="bc5c1-273">NuGet yapılandırması</span><span class="sxs-lookup"><span data-stu-id="bc5c1-273">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="bc5c1-274">Config</span><span class="sxs-lookup"><span data-stu-id="bc5c1-274">Config</span></span>                                | <span data-ttu-id="bc5c1-275">1.0</span><span class="sxs-lookup"><span data-stu-id="bc5c1-275">1.0</span></span>        |
| <span data-ttu-id="bc5c1-276">DotNet yerel araç bildirim dosyası</span><span class="sxs-lookup"><span data-stu-id="bc5c1-276">Dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="bc5c1-277">Config</span><span class="sxs-lookup"><span data-stu-id="bc5c1-277">Config</span></span>                                | <span data-ttu-id="bc5c1-278">3.0</span><span class="sxs-lookup"><span data-stu-id="bc5c1-278">3.0</span></span>        |
| <span data-ttu-id="bc5c1-279">Web yapılandırması</span><span class="sxs-lookup"><span data-stu-id="bc5c1-279">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="bc5c1-280">Config</span><span class="sxs-lookup"><span data-stu-id="bc5c1-280">Config</span></span>                                | <span data-ttu-id="bc5c1-281">1.0</span><span class="sxs-lookup"><span data-stu-id="bc5c1-281">1.0</span></span>        |
| <span data-ttu-id="bc5c1-282">Çözüm dosyası</span><span class="sxs-lookup"><span data-stu-id="bc5c1-282">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="bc5c1-283">Çözüm</span><span class="sxs-lookup"><span data-stu-id="bc5c1-283">Solution</span></span>                              | <span data-ttu-id="bc5c1-284">1.0</span><span class="sxs-lookup"><span data-stu-id="bc5c1-284">1.0</span></span>        |
| <span data-ttu-id="bc5c1-285">Protokol arabelleği dosyası</span><span class="sxs-lookup"><span data-stu-id="bc5c1-285">Protocol Buffer File</span></span>                         | [<span data-ttu-id="bc5c1-286">Proto</span><span class="sxs-lookup"><span data-stu-id="bc5c1-286">proto</span></span>](#namespace)             |              | <span data-ttu-id="bc5c1-287">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="bc5c1-287">Web/gRPC</span></span>                              | <span data-ttu-id="bc5c1-288">3.0</span><span class="sxs-lookup"><span data-stu-id="bc5c1-288">3.0</span></span>        |

## <a name="options"></a><span data-ttu-id="bc5c1-289">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="bc5c1-289">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="bc5c1-290">Bir şablon oluşturulmasına neden olacaksa, verilen komutun çalıştırılması durumunda ne olacağını gösteren bir Özet görüntüler.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-290">Displays a summary of what would happen if the given command were run if it would result in a template creation.</span></span> <span data-ttu-id="bc5c1-291">.NET Core 2,2 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-291">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="bc5c1-292">Var olan dosyaları değiştirebilse bile içeriğin oluşturulmasını zorlar.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-292">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="bc5c1-293">Seçilen şablon çıkış dizinindeki mevcut dosyaları geçersiz kılacağından bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-293">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="bc5c1-294">Komut için yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-294">Prints out help for the command.</span></span> <span data-ttu-id="bc5c1-295">`dotnet new`Komutun kendisi veya herhangi bir şablon için çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-295">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="bc5c1-296">Örneğin, `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-296">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="bc5c1-297">Veya tarafından belirtilen bir şablon paketini `PATH` kurar `NUGET_ID` .</span><span class="sxs-lookup"><span data-stu-id="bc5c1-297">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="bc5c1-298">Şablon paketinin bir ön sürümü sürümünü yüklemek istiyorsanız, sürümü biçiminde belirtmeniz gerekir `<package-name>::<package-version>` .</span><span class="sxs-lookup"><span data-stu-id="bc5c1-298">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="bc5c1-299">Varsayılan olarak, `dotnet new` \* en son kararlı paket sürümünü temsil eden sürüm için geçirir.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-299">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="bc5c1-300">[Örnekler](#examples) bölümündeki bir örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-300">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="bc5c1-301">Bu komutu çalıştırdığınızda şablonun bir sürümü zaten yüklüyse, şablon belirtilen sürüme veya sürüm belirtilmemişse en son kararlı sürüme güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-301">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="bc5c1-302">Özel şablonlar oluşturma hakkında daha fazla bilgi için bkz. [DotNet New Için özel şablonlar](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="bc5c1-302">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="bc5c1-303">Belirtilen adı içeren şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-303">Lists templates containing the specified name.</span></span> <span data-ttu-id="bc5c1-304">Ad belirtilmemişse, tüm şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-304">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="bc5c1-305">Oluşturulacak şablonun dili.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-305">The language of the template to create.</span></span> <span data-ttu-id="bc5c1-306">Kabul edilen dil şablona göre değişir (bkz. [arguments](#arguments) bölümünde Varsayılanlar).</span><span class="sxs-lookup"><span data-stu-id="bc5c1-306">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="bc5c1-307">Bazı şablonlar için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-307">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="bc5c1-308">Bazı kabuklar `#` özel bir karakter olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-308">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="bc5c1-309">Bu durumlarda, dil parametre değerini tırnak içine alın.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-309">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="bc5c1-310">Örneğin, `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-310">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="bc5c1-311">Oluşturulan çıkışın adı.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-311">The name for the created output.</span></span> <span data-ttu-id="bc5c1-312">Ad belirtilmemişse, geçerli dizinin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-312">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source <SOURCE>`**

  <span data-ttu-id="bc5c1-313">Yüklemesi sırasında kullanılacak bir NuGet kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-313">Specifies a NuGet source to use during install.</span></span> <span data-ttu-id="bc5c1-314">.NET Core 2,1 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-314">Available since .NET Core 2.1 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="bc5c1-315">Oluşturulan çıkışın yerleştirileceği konum.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-315">Location to place the generated output.</span></span> <span data-ttu-id="bc5c1-316">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-316">The default is the current directory.</span></span>

- **`--type <TYPE>`**

  <span data-ttu-id="bc5c1-317">Şablonları kullanılabilir türlerine göre filtreler.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-317">Filters templates based on available types.</span></span> <span data-ttu-id="bc5c1-318">Önceden tanımlanmış değerler `project` , `item` , ve `other` .</span><span class="sxs-lookup"><span data-stu-id="bc5c1-318">Predefined values are `project`, `item`, and `other`.</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="bc5c1-319">Veya belirtilen bir şablon paketini kaldırır `PATH` `NUGET_ID` .</span><span class="sxs-lookup"><span data-stu-id="bc5c1-319">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="bc5c1-320">`<PATH|NUGET_ID>`Değer belirtilmediğinde, yüklü olan tüm şablon paketleri ve bunlarla ilişkili şablonlar görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-320">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="bc5c1-321">Belirtirken `NUGET_ID` , sürüm numarasını eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-321">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="bc5c1-322">Bu seçeneğe bir parametre belirtmezseniz, komut, yüklü şablonları ve bunlarla ilgili ayrıntıları listeler.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-322">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="bc5c1-323">Bir şablonu kullanarak kaldırmak için `PATH` , yolu tam olarak nitelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-323">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="bc5c1-324">Örneğin, *C:/Users/ \<USER> /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* çalışır, ancak içeren klasörden *./GarciaSoftware.ConsoleTemplate.CSharp* olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-324">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="bc5c1-325">Şablon yolunuzda son Sonlandırıcı Dizin eğik çizgisi eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-325">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="bc5c1-326">Şu anda yüklü olan şablon paketleri için kullanılabilir güncelleştirmelerin olup olmadığını denetler ve bunları kurar.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-326">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="bc5c1-327">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-327">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="bc5c1-328">Şu anda yüklü olan şablon paketleri için kullanılabilir güncelleştirmeler olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-328">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="bc5c1-329">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-329">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="bc5c1-330">Şablon seçenekleri</span><span class="sxs-lookup"><span data-stu-id="bc5c1-330">Template options</span></span>

<span data-ttu-id="bc5c1-331">Her proje şablonunda ek seçenekler bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-331">Each project template may have additional options available.</span></span> <span data-ttu-id="bc5c1-332">Çekirdek şablonlar aşağıdaki ek seçeneklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="bc5c1-332">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="bc5c1-333">console</span><span class="sxs-lookup"><span data-stu-id="bc5c1-333">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="bc5c1-334">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-334">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="bc5c1-335">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-335">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="bc5c1-336">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="bc5c1-336">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="bc5c1-337">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="bc5c1-337">SDK version</span></span> | <span data-ttu-id="bc5c1-338">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="bc5c1-338">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="bc5c1-339">3,1</span><span class="sxs-lookup"><span data-stu-id="bc5c1-339">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="bc5c1-340">3.0</span><span class="sxs-lookup"><span data-stu-id="bc5c1-340">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="bc5c1-341">`LangVersion`Oluşturulan proje dosyasındaki özelliği ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-341">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="bc5c1-342">Örneğin, `--langVersion 7.3` C# 7,3 kullanmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-342">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="bc5c1-343">F # için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-343">Not supported for F#.</span></span> <span data-ttu-id="bc5c1-344">.NET Core 2,2 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-344">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="bc5c1-345">Varsayılan C# sürümlerinin listesi için bkz. [Varsayılanlar](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="bc5c1-345">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="bc5c1-346">Belirtilmişse, proje oluşturma sırasında örtük geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-346">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="bc5c1-347">.NET Core 2,2 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-347">Available since .NET Core 2.2 SDK.</span></span>

***

### <a name="classlib"></a><span data-ttu-id="bc5c1-348">projesinin</span><span class="sxs-lookup"><span data-stu-id="bc5c1-348">classlib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="bc5c1-349">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-349">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="bc5c1-350">Değerler: `netcoreapp<version>` bir .NET Core sınıf kitaplığı oluşturmak veya `netstandard<version>` bir .NET Standard sınıf kitaplığı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-350">Values: `netcoreapp<version>` to create a .NET Core Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="bc5c1-351">Varsayılan değer: `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-351">The default value is `netstandard2.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="bc5c1-352">`LangVersion`Oluşturulan proje dosyasındaki özelliği ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-352">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="bc5c1-353">Örneğin, `--langVersion 7.3` C# 7,3 kullanmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-353">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="bc5c1-354">F # için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-354">Not supported for F#.</span></span> <span data-ttu-id="bc5c1-355">.NET Core 2,2 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-355">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="bc5c1-356">Varsayılan C# sürümlerinin listesi için bkz. [Varsayılanlar](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="bc5c1-356">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="bc5c1-357">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-357">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="wpf-wpflib-wpfcustomcontrollib-wpfusercontrollib"></a><a name="wpf"></a><span data-ttu-id="bc5c1-358">WPF, wpflib, wpfcustomcontrollib, wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="bc5c1-358">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="bc5c1-359">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-359">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="bc5c1-360">Varsayılan değer: `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-360">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="bc5c1-361">.NET Core 3,1 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-361">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="bc5c1-362">`LangVersion`Oluşturulan proje dosyasındaki özelliği ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-362">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="bc5c1-363">Örneğin, `--langVersion 7.3` C# 7,3 kullanmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-363">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="bc5c1-364">Varsayılan C# sürümlerinin listesi için bkz. [Varsayılanlar](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="bc5c1-364">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="bc5c1-365">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-365">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="winforms-winformslib"></a><a name="winforms"></a><span data-ttu-id="bc5c1-366">WinForms, winformslib</span><span class="sxs-lookup"><span data-stu-id="bc5c1-366">winforms, winformslib</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="bc5c1-367">`LangVersion`Oluşturulan proje dosyasındaki özelliği ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-367">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="bc5c1-368">Örneğin, `--langVersion 7.3` C# 7,3 kullanmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-368">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="bc5c1-369">Varsayılan C# sürümlerinin listesi için bkz. [Varsayılanlar](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="bc5c1-369">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="bc5c1-370">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-370">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="worker-grpc"></a><a name="web-others"></a><span data-ttu-id="bc5c1-371">çalışan, GRPC</span><span class="sxs-lookup"><span data-stu-id="bc5c1-371">worker, grpc</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="bc5c1-372">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-372">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="bc5c1-373">Varsayılan değer: `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-373">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="bc5c1-374">.NET Core 3,1 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-374">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="bc5c1-375">Oluşturulan şablondan *launchSettings.js* dışlar.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-375">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="bc5c1-376">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-376">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="mstest-xunit"></a><a name="test"></a><span data-ttu-id="bc5c1-377">MSTest, xUnit</span><span class="sxs-lookup"><span data-stu-id="bc5c1-377">mstest, xunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="bc5c1-378">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-378">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="bc5c1-379">.NET Core 3,0 SDK 'dan beri kullanılabilir seçeneği.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-379">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="bc5c1-380">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="bc5c1-380">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="bc5c1-381">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="bc5c1-381">SDK version</span></span> | <span data-ttu-id="bc5c1-382">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="bc5c1-382">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="bc5c1-383">3,1</span><span class="sxs-lookup"><span data-stu-id="bc5c1-383">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="bc5c1-384">3.0</span><span class="sxs-lookup"><span data-stu-id="bc5c1-384">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="bc5c1-385">[DotNet Pack](dotnet-pack.md)kullanarak proje için paketleme imkanı sunar.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-385">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="bc5c1-386">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-386">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="nunit"></a><span data-ttu-id="bc5c1-387">NUnit</span><span class="sxs-lookup"><span data-stu-id="bc5c1-387">nunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="bc5c1-388">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-388">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="bc5c1-389">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="bc5c1-389">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="bc5c1-390">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="bc5c1-390">SDK version</span></span> | <span data-ttu-id="bc5c1-391">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="bc5c1-391">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="bc5c1-392">3,1</span><span class="sxs-lookup"><span data-stu-id="bc5c1-392">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="bc5c1-393">3.0</span><span class="sxs-lookup"><span data-stu-id="bc5c1-393">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="bc5c1-394">2,2</span><span class="sxs-lookup"><span data-stu-id="bc5c1-394">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="bc5c1-395">2.1</span><span class="sxs-lookup"><span data-stu-id="bc5c1-395">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="bc5c1-396">[DotNet Pack](dotnet-pack.md)kullanarak proje için paketleme imkanı sunar.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-396">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="bc5c1-397">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-397">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="page"></a><span data-ttu-id="bc5c1-398">sayfasında</span><span class="sxs-lookup"><span data-stu-id="bc5c1-398">page</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="bc5c1-399">Oluşturulan kod için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-399">Namespace for the generated code.</span></span> <span data-ttu-id="bc5c1-400">Varsayılan değer: `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-400">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="bc5c1-401">PageModel olmadan sayfayı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-401">Creates the page without a PageModel.</span></span>

***

### <a name="viewimports-proto"></a><a name="namespace"></a><span data-ttu-id="bc5c1-402">viewıtemler, Proto</span><span class="sxs-lookup"><span data-stu-id="bc5c1-402">viewimports, proto</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="bc5c1-403">Oluşturulan kod için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-403">Namespace for the generated code.</span></span> <span data-ttu-id="bc5c1-404">Varsayılan değer: `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-404">The default value is `MyApp.Namespace`.</span></span>

***

### <a name="blazorserver"></a><span data-ttu-id="bc5c1-405">blazorserver</span><span class="sxs-lookup"><span data-stu-id="bc5c1-405">blazorserver</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="bc5c1-406">Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-406">The type of authentication to use.</span></span> <span data-ttu-id="bc5c1-407">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="bc5c1-407">The possible values are:</span></span>

  - <span data-ttu-id="bc5c1-408">`None`-Kimlik doğrulaması yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="bc5c1-408">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="bc5c1-409">`Individual`-Bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-409">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="bc5c1-410">`IndividualB2C`-Azure AD B2C ile bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-410">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="bc5c1-411">`SingleOrg`-Tek bir kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-411">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="bc5c1-412">`MultiOrg`-Birden çok kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-412">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="bc5c1-413">`Windows`-Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-413">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="bc5c1-414">Bağlanılacak Azure Active Directory B2C örneği.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-414">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="bc5c1-415">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-415">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="bc5c1-416">Varsayılan değer: `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-416">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="bc5c1-417">Bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-417">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="bc5c1-418">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-418">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="bc5c1-419">Bu proje için parola sıfırlama ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-419">The reset password policy ID for this project.</span></span> <span data-ttu-id="bc5c1-420">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-420">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="bc5c1-421">Bu proje için profil ilke KIMLIĞINI Düzenle.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-421">The edit profile policy ID for this project.</span></span> <span data-ttu-id="bc5c1-422">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-422">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="bc5c1-423">Bağlanılacak Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-423">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="bc5c1-424">`SingleOrg`Veya `MultiOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-424">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="bc5c1-425">Varsayılan değer: `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-425">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="bc5c1-426">Bu projenin Istemci KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-426">The Client ID for this project.</span></span> <span data-ttu-id="bc5c1-427">`IndividualB2C`, `SingleOrg` Veya `MultiOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-427">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="bc5c1-428">Varsayılan değer: `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-428">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="bc5c1-429">Dizin kiracının etki alanı.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-429">The domain for the directory tenant.</span></span> <span data-ttu-id="bc5c1-430">`SingleOrg`Veya `IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-430">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="bc5c1-431">Varsayılan değer: `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-431">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="bc5c1-432">Bağlanılacak dizinin Tenantıd KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-432">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="bc5c1-433">`SingleOrg`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-433">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="bc5c1-434">Varsayılan değer: `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-434">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="bc5c1-435">Uygulamanın yeniden yönlendirme URI 'sinin temel yolundaki istek yolu.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-435">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="bc5c1-436">`SingleOrg`Veya `IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-436">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="bc5c1-437">Varsayılan değer: `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-437">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="bc5c1-438">Bu uygulamanın dizine okuma erişimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-438">Allows this application read-access to the directory.</span></span> <span data-ttu-id="bc5c1-439">Yalnızca `SingleOrg` veya `MultiOrg` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-439">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="bc5c1-440">Oluşturulan şablondan *launchSettings.js* dışlar.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-440">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="bc5c1-441">HTTPS 'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-441">Turns off HTTPS.</span></span> <span data-ttu-id="bc5c1-442">Bu seçenek yalnızca,, `Individual` , `IndividualB2C` `SingleOrg` veya için kullanılmıyorsa geçerlidir `MultiOrg` `--auth` .</span><span class="sxs-lookup"><span data-stu-id="bc5c1-442">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="bc5c1-443">SQLite yerine LocalDB kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-443">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="bc5c1-444">Yalnızca `Individual` veya `IndividualB2C` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-444">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="bc5c1-445">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-445">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web"></a><span data-ttu-id="bc5c1-446">web</span><span class="sxs-lookup"><span data-stu-id="bc5c1-446">web</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="bc5c1-447">Oluşturulan şablondan *launchSettings.js* dışlar.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-447">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="bc5c1-448">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-448">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="bc5c1-449">Seçenek .NET Core 2,2 SDK sürümünde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-449">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="bc5c1-450">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="bc5c1-450">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="bc5c1-451">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="bc5c1-451">SDK version</span></span> | <span data-ttu-id="bc5c1-452">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="bc5c1-452">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="bc5c1-453">3,1</span><span class="sxs-lookup"><span data-stu-id="bc5c1-453">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="bc5c1-454">3.0</span><span class="sxs-lookup"><span data-stu-id="bc5c1-454">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="bc5c1-455">2.1</span><span class="sxs-lookup"><span data-stu-id="bc5c1-455">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="bc5c1-456">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-456">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="bc5c1-457">HTTPS 'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-457">Turns off HTTPS.</span></span>

***

### <a name="mvc-webapp"></a><a name="web-options"></a><span data-ttu-id="bc5c1-458">MVC, WebApp</span><span class="sxs-lookup"><span data-stu-id="bc5c1-458">mvc, webapp</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="bc5c1-459">Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-459">The type of authentication to use.</span></span> <span data-ttu-id="bc5c1-460">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="bc5c1-460">The possible values are:</span></span>

  - <span data-ttu-id="bc5c1-461">`None`-Kimlik doğrulaması yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="bc5c1-461">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="bc5c1-462">`Individual`-Bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-462">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="bc5c1-463">`IndividualB2C`-Azure AD B2C ile bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-463">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="bc5c1-464">`SingleOrg`-Tek bir kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-464">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="bc5c1-465">`MultiOrg`-Birden çok kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-465">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="bc5c1-466">`Windows`-Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-466">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="bc5c1-467">Bağlanılacak Azure Active Directory B2C örneği.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-467">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="bc5c1-468">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-468">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="bc5c1-469">Varsayılan değer: `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-469">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="bc5c1-470">Bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-470">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="bc5c1-471">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-471">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="bc5c1-472">Bu proje için parola sıfırlama ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-472">The reset password policy ID for this project.</span></span> <span data-ttu-id="bc5c1-473">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-473">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="bc5c1-474">Bu proje için profil ilke KIMLIĞINI Düzenle.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-474">The edit profile policy ID for this project.</span></span> <span data-ttu-id="bc5c1-475">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-475">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="bc5c1-476">Bağlanılacak Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-476">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="bc5c1-477">`SingleOrg`Veya `MultiOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-477">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="bc5c1-478">Varsayılan değer: `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-478">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="bc5c1-479">Bu projenin Istemci KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-479">The Client ID for this project.</span></span> <span data-ttu-id="bc5c1-480">`IndividualB2C`, `SingleOrg` Veya `MultiOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-480">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="bc5c1-481">Varsayılan değer: `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-481">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="bc5c1-482">Dizin kiracının etki alanı.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-482">The domain for the directory tenant.</span></span> <span data-ttu-id="bc5c1-483">`SingleOrg`Veya `IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-483">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="bc5c1-484">Varsayılan değer: `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-484">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="bc5c1-485">Bağlanılacak dizinin Tenantıd KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-485">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="bc5c1-486">`SingleOrg`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-486">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="bc5c1-487">Varsayılan değer: `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-487">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="bc5c1-488">Uygulamanın yeniden yönlendirme URI 'sinin temel yolundaki istek yolu.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-488">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="bc5c1-489">`SingleOrg`Veya `IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-489">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="bc5c1-490">Varsayılan değer: `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-490">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="bc5c1-491">Bu uygulamanın dizine okuma erişimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-491">Allows this application read-access to the directory.</span></span> <span data-ttu-id="bc5c1-492">Yalnızca `SingleOrg` veya `MultiOrg` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-492">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="bc5c1-493">Oluşturulan şablondan *launchSettings.js* dışlar.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-493">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="bc5c1-494">HTTPS 'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-494">Turns off HTTPS.</span></span> <span data-ttu-id="bc5c1-495">Bu seçenek yalnızca,,, veya kullanılmıyorsa geçerlidir `Individual` `IndividualB2C` `SingleOrg` `MultiOrg` .</span><span class="sxs-lookup"><span data-stu-id="bc5c1-495">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="bc5c1-496">SQLite yerine LocalDB kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-496">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="bc5c1-497">Yalnızca `Individual` veya `IndividualB2C` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-497">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="bc5c1-498">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-498">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="bc5c1-499">.NET Core 3,0 SDK 'dan beri kullanılabilir seçeneği.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-499">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="bc5c1-500">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="bc5c1-500">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="bc5c1-501">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="bc5c1-501">SDK version</span></span> | <span data-ttu-id="bc5c1-502">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="bc5c1-502">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="bc5c1-503">3,1</span><span class="sxs-lookup"><span data-stu-id="bc5c1-503">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="bc5c1-504">3.0</span><span class="sxs-lookup"><span data-stu-id="bc5c1-504">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="bc5c1-505">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-505">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="bc5c1-506">Projedeki BrowserLink öğesini içerir.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-506">Includes BrowserLink in the project.</span></span> <span data-ttu-id="bc5c1-507">Seçenek .NET Core 2,2 ve 3,1 SDK sürümünde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-507">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

- **`-rrc|--razor-runtime-compilation`**

  <span data-ttu-id="bc5c1-508">Projenin hata ayıklama yapılarında [Razor çalışma zamanı derlemesini](/aspnet/core/mvc/views/view-compilation#runtime-compilation) kullanmak üzere yapılandırılıp yapılandırılmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-508">Determines if the project is configured to use [Razor runtime compilation](/aspnet/core/mvc/views/view-compilation#runtime-compilation) in Debug builds.</span></span> <span data-ttu-id="bc5c1-509">.NET Core 3.1.201 SDK 'dan beri kullanılabilir seçeneği.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-509">Option available since .NET Core 3.1.201 SDK.</span></span>

***

### <a name="angular-react"></a><a name="spa"></a><span data-ttu-id="bc5c1-510">Angular, tepki verme</span><span class="sxs-lookup"><span data-stu-id="bc5c1-510">angular, react</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="bc5c1-511">Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-511">The type of authentication to use.</span></span> <span data-ttu-id="bc5c1-512">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-512">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="bc5c1-513">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="bc5c1-513">The possible values are:</span></span>

  - <span data-ttu-id="bc5c1-514">`None`-Kimlik doğrulaması yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="bc5c1-514">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="bc5c1-515">`Individual`-Bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-515">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="bc5c1-516">Oluşturulan şablondan *launchSettings.js* dışlar.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-516">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="bc5c1-517">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-517">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="bc5c1-518">HTTPS 'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-518">Turns off HTTPS.</span></span> <span data-ttu-id="bc5c1-519">Bu seçenek yalnızca kimlik doğrulaması ise geçerlidir `None` .</span><span class="sxs-lookup"><span data-stu-id="bc5c1-519">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="bc5c1-520">SQLite yerine LocalDB kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-520">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="bc5c1-521">Yalnızca `Individual` veya `IndividualB2C` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-521">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="bc5c1-522">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-522">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="bc5c1-523">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-523">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="bc5c1-524">Seçenek .NET Core 2,2 SDK sürümünde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-524">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="bc5c1-525">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="bc5c1-525">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="bc5c1-526">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="bc5c1-526">SDK version</span></span> | <span data-ttu-id="bc5c1-527">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="bc5c1-527">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="bc5c1-528">3,1</span><span class="sxs-lookup"><span data-stu-id="bc5c1-528">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="bc5c1-529">3.0</span><span class="sxs-lookup"><span data-stu-id="bc5c1-529">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="bc5c1-530">2.1</span><span class="sxs-lookup"><span data-stu-id="bc5c1-530">2.1</span></span>         | `netcoreapp2.0` |

***

### <a name="reactredux"></a><span data-ttu-id="bc5c1-531">reactredux</span><span class="sxs-lookup"><span data-stu-id="bc5c1-531">reactredux</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="bc5c1-532">Oluşturulan şablondan *launchSettings.js* dışlar.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-532">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="bc5c1-533">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-533">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="bc5c1-534">Seçenek .NET Core 2,2 SDK sürümünde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-534">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="bc5c1-535">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="bc5c1-535">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="bc5c1-536">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="bc5c1-536">SDK version</span></span> | <span data-ttu-id="bc5c1-537">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="bc5c1-537">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="bc5c1-538">3,1</span><span class="sxs-lookup"><span data-stu-id="bc5c1-538">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="bc5c1-539">3.0</span><span class="sxs-lookup"><span data-stu-id="bc5c1-539">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="bc5c1-540">2.1</span><span class="sxs-lookup"><span data-stu-id="bc5c1-540">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="bc5c1-541">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-541">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="bc5c1-542">HTTPS 'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-542">Turns off HTTPS.</span></span>

***

### <a name="razorclasslib"></a><span data-ttu-id="bc5c1-543">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="bc5c1-543">razorclasslib</span></span>

- **`--no-restore`**

  <span data-ttu-id="bc5c1-544">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-544">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="bc5c1-545">, Bu kitaplığa bileşenlere ek olarak geleneksel Razor sayfaları ve görünümleri eklenmesini destekler.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-545">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="bc5c1-546">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-546">Available since .NET Core 3.0 SDK.</span></span>

***
  
### <a name="webapi"></a><span data-ttu-id="bc5c1-547">WebApi</span><span class="sxs-lookup"><span data-stu-id="bc5c1-547">webapi</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="bc5c1-548">Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-548">The type of authentication to use.</span></span> <span data-ttu-id="bc5c1-549">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="bc5c1-549">The possible values are:</span></span>

  - <span data-ttu-id="bc5c1-550">`None`-Kimlik doğrulaması yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="bc5c1-550">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="bc5c1-551">`IndividualB2C`-Azure AD B2C ile bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-551">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="bc5c1-552">`SingleOrg`-Tek bir kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-552">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="bc5c1-553">`Windows`-Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-553">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="bc5c1-554">Bağlanılacak Azure Active Directory B2C örneği.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-554">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="bc5c1-555">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-555">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="bc5c1-556">Varsayılan değer: `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-556">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="bc5c1-557">Bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-557">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="bc5c1-558">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-558">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="bc5c1-559">Bağlanılacak Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-559">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="bc5c1-560">`SingleOrg`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-560">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="bc5c1-561">Varsayılan değer: `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-561">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="bc5c1-562">Bu projenin Istemci KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-562">The Client ID for this project.</span></span> <span data-ttu-id="bc5c1-563">`IndividualB2C`Veya `SingleOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-563">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="bc5c1-564">Varsayılan değer: `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-564">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="bc5c1-565">Dizin kiracının etki alanı.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-565">The domain for the directory tenant.</span></span> <span data-ttu-id="bc5c1-566">`IndividualB2C`Veya `SingleOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-566">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="bc5c1-567">Varsayılan değer: `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-567">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="bc5c1-568">Bağlanılacak dizinin Tenantıd KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-568">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="bc5c1-569">`SingleOrg`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-569">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="bc5c1-570">Varsayılan değer: `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-570">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="bc5c1-571">Bu uygulamanın dizine okuma erişimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-571">Allows this application read-access to the directory.</span></span> <span data-ttu-id="bc5c1-572">Yalnızca `SingleOrg` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-572">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="bc5c1-573">Oluşturulan şablondan *launchSettings.js* dışlar.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-573">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="bc5c1-574">HTTPS 'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-574">Turns off HTTPS.</span></span> <span data-ttu-id="bc5c1-575">`app.UseHsts`ve `app.UseHttpsRedirection` öğesine eklenmez `Startup.Configure` .</span><span class="sxs-lookup"><span data-stu-id="bc5c1-575">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="bc5c1-576">Bu seçenek yalnızca `IndividualB2C` `SingleOrg` kimlik doğrulaması için kullanılmıyorsa geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-576">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="bc5c1-577">SQLite yerine LocalDB kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-577">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="bc5c1-578">Yalnızca `IndividualB2C` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-578">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="bc5c1-579">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-579">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="bc5c1-580">Seçenek .NET Core 2,2 SDK sürümünde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-580">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="bc5c1-581">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="bc5c1-581">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="bc5c1-582">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="bc5c1-582">SDK version</span></span> | <span data-ttu-id="bc5c1-583">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="bc5c1-583">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="bc5c1-584">3,1</span><span class="sxs-lookup"><span data-stu-id="bc5c1-584">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="bc5c1-585">3.0</span><span class="sxs-lookup"><span data-stu-id="bc5c1-585">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="bc5c1-586">2.1</span><span class="sxs-lookup"><span data-stu-id="bc5c1-586">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="bc5c1-587">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-587">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="globaljson"></a><span data-ttu-id="bc5c1-588">globaljson</span><span class="sxs-lookup"><span data-stu-id="bc5c1-588">globaljson</span></span>

- **`--sdk-version <VERSION_NUMBER>`**

  <span data-ttu-id="bc5c1-589">*global.json* dosyasında kullanılacak .NET Core SDK sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-589">Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="bc5c1-590">Örnekler</span><span class="sxs-lookup"><span data-stu-id="bc5c1-590">Examples</span></span>

- <span data-ttu-id="bc5c1-591">Şablon adını belirterek bir C# konsol uygulaması projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="bc5c1-591">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="bc5c1-592">Geçerli dizinde bir F # konsol uygulaması projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="bc5c1-592">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang "F#"
  ```

- <span data-ttu-id="bc5c1-593">Belirtilen dizinde bir .NET Standard sınıf kitaplığı projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="bc5c1-593">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="bc5c1-594">Geçerli dizinde kimlik doğrulaması olmadan yeni bir ASP.NET Core C# MVC projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="bc5c1-594">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="bc5c1-595">Yeni bir xUnit projesi oluştur:</span><span class="sxs-lookup"><span data-stu-id="bc5c1-595">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="bc5c1-596">Tek sayfalı uygulama (SPA) şablonları için kullanılabilen tüm şablonları listeleyin:</span><span class="sxs-lookup"><span data-stu-id="bc5c1-596">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="bc5c1-597">*We* alt dizeniz ile eşleşen tüm şablonları listeleyin.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-597">List all templates matching the *we* substring.</span></span> <span data-ttu-id="bc5c1-598">Tam eşleşme bulunamadı, bu nedenle alt dize eşleştirmesi hem kısa ad hem de ad sütunlarında çalışır.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-598">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="bc5c1-599">Şablonla *eşleşen şablonu*çağırma girişimi.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-599">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="bc5c1-600">Tek bir eşleşme belirlenemiyorsa kısmi eşleşen şablonları listeleyin.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-600">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="bc5c1-601">ASP.NET Core için SPA şablonlarının 2,0 sürümünü yükler:</span><span class="sxs-lookup"><span data-stu-id="bc5c1-601">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="bc5c1-602">Yüklü şablonları ve bunlarla ilgili ayrıntıları, bunları kaldırma dahil olmak üzere listeleyin:</span><span class="sxs-lookup"><span data-stu-id="bc5c1-602">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="bc5c1-603">SDK sürümünü 3.1.101 olarak ayarlamak için geçerli dizinde bir *global.js* oluşturun:</span><span class="sxs-lookup"><span data-stu-id="bc5c1-603">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="bc5c1-604">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc5c1-604">See also</span></span>

- [<span data-ttu-id="bc5c1-605">DotNet New için özel şablonlar</span><span class="sxs-lookup"><span data-stu-id="bc5c1-605">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="bc5c1-606">Dotnet new için özel şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="bc5c1-606">Create a custom template for dotnet new</span></span>](../tutorials/cli-templates-create-item-template.md)
- [<span data-ttu-id="bc5c1-607">DotNet/DotNet-şablon-örnek GitHub deposu</span><span class="sxs-lookup"><span data-stu-id="bc5c1-607">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="bc5c1-608">DotNet New için kullanılabilir şablonlar</span><span class="sxs-lookup"><span data-stu-id="bc5c1-608">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
