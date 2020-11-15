---
title: DotNet yeni komut
description: DotNet New komutu, belirtilen şablona göre yeni .NET projeleri oluşturur.
no-loc:
- ':::no-loc(Blazor):::'
- ':::no-loc(WebAssembly):::'
ms.date: 09/04/2020
ms.openlocfilehash: 3ee644f05ea5929ffc7b11054ef1d974b811f418
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634461"
---
# <a name="dotnet-new"></a><span data-ttu-id="aba42-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="aba42-103">dotnet new</span></span>

<span data-ttu-id="aba42-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,0 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="aba42-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="aba42-105">Name</span><span class="sxs-lookup"><span data-stu-id="aba42-105">Name</span></span>

<span data-ttu-id="aba42-106">`dotnet new` -Belirtilen şablonu temel alan yeni bir proje, yapılandırma dosyası veya çözüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="aba42-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="aba42-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="aba42-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install {PATH|NUGET_ID}]
    [-lang|--language {"C#"|"F#"|VB}] [-n|--name <OUTPUT_NAME>]
    [--nuget-source <SOURCE>] [-o|--output <OUTPUT_DIRECTORY>]
    [-u|--uninstall] [--update-apply] [--update-check] [Template options]

dotnet new <TEMPLATE> [-l|--list] [--type <TYPE>]

dotnet new -h|--help
```

## <a name="description"></a><span data-ttu-id="aba42-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aba42-108">Description</span></span>

<span data-ttu-id="aba42-109">`dotnet new`Komut bir şablonu temel alan bir .NET projesi veya başka yapılar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="aba42-109">The `dotnet new` command creates a .NET project or other artifacts based on a template.</span></span>

<span data-ttu-id="aba42-110">Komutu, belirtilen şablon ve seçeneklere göre diskteki yapıtları oluşturmak için [şablon altyapısını](https://github.com/dotnet/templating) çağırır.</span><span class="sxs-lookup"><span data-stu-id="aba42-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="aba42-111">Örtük geri yükleme</span><span class="sxs-lookup"><span data-stu-id="aba42-111">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="aba42-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="aba42-112">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="aba42-113">Komut çağrıldığında örnek oluşturulacak şablon.</span><span class="sxs-lookup"><span data-stu-id="aba42-113">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="aba42-114">Her şablonun geçirebilmeniz için özel seçenekleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="aba42-114">Each template might have specific options you can pass.</span></span> <span data-ttu-id="aba42-115">Daha fazla bilgi için bkz. [şablon seçenekleri](#template-options).</span><span class="sxs-lookup"><span data-stu-id="aba42-115">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="aba42-116">`dotnet new --list` `dotnet new -l` Tüm yüklü şablonların listesini görmek için veya çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aba42-116">You can run `dotnet new --list` or `dotnet new -l` to see a list of all installed templates.</span></span> <span data-ttu-id="aba42-117">Değer, `TEMPLATE` döndürülen tablodaki **Şablonlar** veya **kısa ad** sütunundaki metinde tam eşleşme değilse, bu iki sütunda bir alt dize eşleşmesi gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="aba42-117">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="aba42-118">.NET Core 3,0 SDK ile başlayarak, aşağıdaki koşullarda komutu çağırdığınızda CLı NuGet.org içindeki şablonları arar `dotnet new` :</span><span class="sxs-lookup"><span data-stu-id="aba42-118">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="aba42-119">CLı çağrılırken bir şablon eşleşmesi bulamazsa `dotnet new` , bu da kısmi değildir.</span><span class="sxs-lookup"><span data-stu-id="aba42-119">If the CLI can't find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="aba42-120">Şablonun daha yeni bir sürümü kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="aba42-120">If there's a newer version of the template available.</span></span> <span data-ttu-id="aba42-121">Bu durumda, proje veya yapıt oluşturulur ancak CLı, şablonun güncelleştirilmiş bir sürümü hakkında sizi uyarır.</span><span class="sxs-lookup"><span data-stu-id="aba42-121">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="aba42-122">Aşağıdaki tabloda .NET SDK ile önceden yüklenmiş olarak gelen şablonlar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="aba42-122">The following table shows the templates that come pre-installed with the .NET SDK.</span></span> <span data-ttu-id="aba42-123">Şablon için varsayılan dil, köşeli ayraçlar içinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="aba42-123">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="aba42-124">Özel şablon seçeneklerini görmek için kısa ad bağlantısına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="aba42-124">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="aba42-125">Şablonlar</span><span class="sxs-lookup"><span data-stu-id="aba42-125">Templates</span></span>                                    | <span data-ttu-id="aba42-126">Kısa ad</span><span class="sxs-lookup"><span data-stu-id="aba42-126">Short name</span></span>                      | <span data-ttu-id="aba42-127">Dil</span><span class="sxs-lookup"><span data-stu-id="aba42-127">Language</span></span>     | <span data-ttu-id="aba42-128">Etiketler</span><span class="sxs-lookup"><span data-stu-id="aba42-128">Tags</span></span>                                  | <span data-ttu-id="aba42-129">Sunulan özellikler</span><span class="sxs-lookup"><span data-stu-id="aba42-129">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="aba42-130">Konsol Uygulaması</span><span class="sxs-lookup"><span data-stu-id="aba42-130">Console Application</span></span>                          | [<span data-ttu-id="aba42-131">konsola</span><span class="sxs-lookup"><span data-stu-id="aba42-131">console</span></span>](#console)             | <span data-ttu-id="aba42-132">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="aba42-132">[C#], F#, VB</span></span> | <span data-ttu-id="aba42-133">Ortak/konsol</span><span class="sxs-lookup"><span data-stu-id="aba42-133">Common/Console</span></span>                        | <span data-ttu-id="aba42-134">1,0</span><span class="sxs-lookup"><span data-stu-id="aba42-134">1.0</span></span>        |
| <span data-ttu-id="aba42-135">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="aba42-135">Class library</span></span>                                | [<span data-ttu-id="aba42-136">projesinin</span><span class="sxs-lookup"><span data-stu-id="aba42-136">classlib</span></span>](#classlib)           | <span data-ttu-id="aba42-137">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="aba42-137">[C#], F#, VB</span></span> | <span data-ttu-id="aba42-138">Ortak/Kitaplık</span><span class="sxs-lookup"><span data-stu-id="aba42-138">Common/Library</span></span>                        | <span data-ttu-id="aba42-139">1,0</span><span class="sxs-lookup"><span data-stu-id="aba42-139">1.0</span></span>        |
| <span data-ttu-id="aba42-140">WPF uygulaması</span><span class="sxs-lookup"><span data-stu-id="aba42-140">WPF Application</span></span>                              | [<span data-ttu-id="aba42-141">WPF</span><span class="sxs-lookup"><span data-stu-id="aba42-141">wpf</span></span>](#wpf)                     | <span data-ttu-id="aba42-142">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="aba42-142">[C#], VB</span></span>     | <span data-ttu-id="aba42-143">Ortak/WPF</span><span class="sxs-lookup"><span data-stu-id="aba42-143">Common/WPF</span></span>                            | <span data-ttu-id="aba42-144">3,0 (VB için 5,0)</span><span class="sxs-lookup"><span data-stu-id="aba42-144">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="aba42-145">WPF sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="aba42-145">WPF Class library</span></span>                            | [<span data-ttu-id="aba42-146">wpflib</span><span class="sxs-lookup"><span data-stu-id="aba42-146">wpflib</span></span>](#wpf)                  | <span data-ttu-id="aba42-147">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="aba42-147">[C#], VB</span></span>     | <span data-ttu-id="aba42-148">Ortak/WPF</span><span class="sxs-lookup"><span data-stu-id="aba42-148">Common/WPF</span></span>                            | <span data-ttu-id="aba42-149">3,0 (VB için 5,0)</span><span class="sxs-lookup"><span data-stu-id="aba42-149">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="aba42-150">WPF Özel Denetim Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="aba42-150">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="aba42-151">wpfcustomcontrollib</span><span class="sxs-lookup"><span data-stu-id="aba42-151">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="aba42-152">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="aba42-152">[C#], VB</span></span>     | <span data-ttu-id="aba42-153">Ortak/WPF</span><span class="sxs-lookup"><span data-stu-id="aba42-153">Common/WPF</span></span>                            | <span data-ttu-id="aba42-154">3,0 (VB için 5,0)</span><span class="sxs-lookup"><span data-stu-id="aba42-154">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="aba42-155">WPF Kullanıcı denetimi kitaplığı</span><span class="sxs-lookup"><span data-stu-id="aba42-155">WPF User Control Library</span></span>                     | [<span data-ttu-id="aba42-156">wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="aba42-156">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="aba42-157">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="aba42-157">[C#], VB</span></span>     | <span data-ttu-id="aba42-158">Ortak/WPF</span><span class="sxs-lookup"><span data-stu-id="aba42-158">Common/WPF</span></span>                            | <span data-ttu-id="aba42-159">3,0 (VB için 5,0)</span><span class="sxs-lookup"><span data-stu-id="aba42-159">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="aba42-160">Windows Forms (WinForms) uygulaması</span><span class="sxs-lookup"><span data-stu-id="aba42-160">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="aba42-161">WinForms</span><span class="sxs-lookup"><span data-stu-id="aba42-161">winforms</span></span>](#winforms)           | <span data-ttu-id="aba42-162">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="aba42-162">[C#], VB</span></span>     | <span data-ttu-id="aba42-163">Ortak/WinForms</span><span class="sxs-lookup"><span data-stu-id="aba42-163">Common/WinForms</span></span>                       | <span data-ttu-id="aba42-164">3,0 (VB için 5,0)</span><span class="sxs-lookup"><span data-stu-id="aba42-164">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="aba42-165">Windows Forms (WinForms) sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="aba42-165">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="aba42-166">winformslib</span><span class="sxs-lookup"><span data-stu-id="aba42-166">winformslib</span></span>](#winforms)        | <span data-ttu-id="aba42-167">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="aba42-167">[C#], VB</span></span>     | <span data-ttu-id="aba42-168">Ortak/WinForms</span><span class="sxs-lookup"><span data-stu-id="aba42-168">Common/WinForms</span></span>                       | <span data-ttu-id="aba42-169">3,0 (VB için 5,0)</span><span class="sxs-lookup"><span data-stu-id="aba42-169">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="aba42-170">Çalışan hizmeti</span><span class="sxs-lookup"><span data-stu-id="aba42-170">Worker Service</span></span>                               | [<span data-ttu-id="aba42-171">ından</span><span class="sxs-lookup"><span data-stu-id="aba42-171">worker</span></span>](#web-others)           | <span data-ttu-id="aba42-172">Þ</span><span class="sxs-lookup"><span data-stu-id="aba42-172">[C#]</span></span>         | <span data-ttu-id="aba42-173">Ortak/çalışan/Web</span><span class="sxs-lookup"><span data-stu-id="aba42-173">Common/Worker/Web</span></span>                     | <span data-ttu-id="aba42-174">3,0</span><span class="sxs-lookup"><span data-stu-id="aba42-174">3.0</span></span>        |
| <span data-ttu-id="aba42-175">Birim testi projesi</span><span class="sxs-lookup"><span data-stu-id="aba42-175">Unit Test Project</span></span>                            | [<span data-ttu-id="aba42-176">'i</span><span class="sxs-lookup"><span data-stu-id="aba42-176">mstest</span></span>](#test)                 | <span data-ttu-id="aba42-177">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="aba42-177">[C#], F#, VB</span></span> | <span data-ttu-id="aba42-178">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="aba42-178">Test/MSTest</span></span>                           | <span data-ttu-id="aba42-179">1,0</span><span class="sxs-lookup"><span data-stu-id="aba42-179">1.0</span></span>        |
| <span data-ttu-id="aba42-180">NUnit 3 test projesi</span><span class="sxs-lookup"><span data-stu-id="aba42-180">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="aba42-181">NUnit</span><span class="sxs-lookup"><span data-stu-id="aba42-181">nunit</span></span>](#nunit)                 | <span data-ttu-id="aba42-182">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="aba42-182">[C#], F#, VB</span></span> | <span data-ttu-id="aba42-183">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="aba42-183">Test/NUnit</span></span>                            | <span data-ttu-id="aba42-184">2.1.400</span><span class="sxs-lookup"><span data-stu-id="aba42-184">2.1.400</span></span>    |
| <span data-ttu-id="aba42-185">NUnit 3 test öğesi</span><span class="sxs-lookup"><span data-stu-id="aba42-185">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="aba42-186">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="aba42-186">[C#], F#, VB</span></span> | <span data-ttu-id="aba42-187">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="aba42-187">Test/NUnit</span></span>                            | <span data-ttu-id="aba42-188">2.2</span><span class="sxs-lookup"><span data-stu-id="aba42-188">2.2</span></span>        |
| <span data-ttu-id="aba42-189">xUnit test projesi</span><span class="sxs-lookup"><span data-stu-id="aba42-189">xUnit Test Project</span></span>                           | [<span data-ttu-id="aba42-190">xUnit</span><span class="sxs-lookup"><span data-stu-id="aba42-190">xunit</span></span>](#test)                  | <span data-ttu-id="aba42-191">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="aba42-191">[C#], F#, VB</span></span> | <span data-ttu-id="aba42-192">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="aba42-192">Test/xUnit</span></span>                            | <span data-ttu-id="aba42-193">1,0</span><span class="sxs-lookup"><span data-stu-id="aba42-193">1.0</span></span>        |
| <span data-ttu-id="aba42-194">Razor bileşeni</span><span class="sxs-lookup"><span data-stu-id="aba42-194">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="aba42-195">Þ</span><span class="sxs-lookup"><span data-stu-id="aba42-195">[C#]</span></span>         | <span data-ttu-id="aba42-196">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="aba42-196">Web/ASP.NET</span></span>                           | <span data-ttu-id="aba42-197">3,0</span><span class="sxs-lookup"><span data-stu-id="aba42-197">3.0</span></span>        |
| <span data-ttu-id="aba42-198">Razor sayfası</span><span class="sxs-lookup"><span data-stu-id="aba42-198">Razor Page</span></span>                                   | <span data-ttu-id="aba42-199">[page (sayfa)](#page) </span><span class="sxs-lookup"><span data-stu-id="aba42-199">[page](#page)</span></span>                   | <span data-ttu-id="aba42-200">Þ</span><span class="sxs-lookup"><span data-stu-id="aba42-200">[C#]</span></span>         | <span data-ttu-id="aba42-201">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="aba42-201">Web/ASP.NET</span></span>                           | <span data-ttu-id="aba42-202">2,0</span><span class="sxs-lookup"><span data-stu-id="aba42-202">2.0</span></span>        |
| <span data-ttu-id="aba42-203">MVC Viewıtemts</span><span class="sxs-lookup"><span data-stu-id="aba42-203">MVC ViewImports</span></span>                              | [<span data-ttu-id="aba42-204">viewıtems 'lar</span><span class="sxs-lookup"><span data-stu-id="aba42-204">viewimports</span></span>](#namespace)       | <span data-ttu-id="aba42-205">Þ</span><span class="sxs-lookup"><span data-stu-id="aba42-205">[C#]</span></span>         | <span data-ttu-id="aba42-206">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="aba42-206">Web/ASP.NET</span></span>                           | <span data-ttu-id="aba42-207">2,0</span><span class="sxs-lookup"><span data-stu-id="aba42-207">2.0</span></span>        |
| <span data-ttu-id="aba42-208">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="aba42-208">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="aba42-209">Þ</span><span class="sxs-lookup"><span data-stu-id="aba42-209">[C#]</span></span>         | <span data-ttu-id="aba42-210">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="aba42-210">Web/ASP.NET</span></span>                           | <span data-ttu-id="aba42-211">2,0</span><span class="sxs-lookup"><span data-stu-id="aba42-211">2.0</span></span>        |
| <span data-ttu-id="aba42-212">:::no-loc(Blazor)::: Sunucu uygulaması</span><span class="sxs-lookup"><span data-stu-id="aba42-212">:::no-loc(Blazor)::: Server App</span></span>                            | [<span data-ttu-id="aba42-213">blazorserver</span><span class="sxs-lookup"><span data-stu-id="aba42-213">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="aba42-214">Þ</span><span class="sxs-lookup"><span data-stu-id="aba42-214">[C#]</span></span>         | <span data-ttu-id="aba42-215">Web:::no-loc(Blazor):::</span><span class="sxs-lookup"><span data-stu-id="aba42-215">Web/:::no-loc(Blazor):::</span></span>                            | <span data-ttu-id="aba42-216">3,0</span><span class="sxs-lookup"><span data-stu-id="aba42-216">3.0</span></span>        |
| <span data-ttu-id="aba42-217">:::no-loc(Blazor)::::::no-loc(WebAssembly):::Uygulama</span><span class="sxs-lookup"><span data-stu-id="aba42-217">:::no-loc(Blazor)::: :::no-loc(WebAssembly)::: App</span></span>                       | [<span data-ttu-id="aba42-218">blazorwasm</span><span class="sxs-lookup"><span data-stu-id="aba42-218">blazorwasm</span></span>](#blazorwasm)       | <span data-ttu-id="aba42-219">Þ</span><span class="sxs-lookup"><span data-stu-id="aba42-219">[C#]</span></span>         | <span data-ttu-id="aba42-220">Web:::no-loc(Blazor):::/:::no-loc(WebAssembly):::</span><span class="sxs-lookup"><span data-stu-id="aba42-220">Web/:::no-loc(Blazor):::/:::no-loc(WebAssembly):::</span></span>                | <span data-ttu-id="aba42-221">3.1.300</span><span class="sxs-lookup"><span data-stu-id="aba42-221">3.1.300</span></span>    |
| <span data-ttu-id="aba42-222">ASP.NET Core boş</span><span class="sxs-lookup"><span data-stu-id="aba42-222">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="aba42-223">Web</span><span class="sxs-lookup"><span data-stu-id="aba42-223">web</span></span>](#web)                     | <span data-ttu-id="aba42-224">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="aba42-224">[C#], F#</span></span>     | <span data-ttu-id="aba42-225">Web/boş</span><span class="sxs-lookup"><span data-stu-id="aba42-225">Web/Empty</span></span>                             | <span data-ttu-id="aba42-226">1,0</span><span class="sxs-lookup"><span data-stu-id="aba42-226">1.0</span></span>        |
| <span data-ttu-id="aba42-227">ASP.NET Core Web uygulaması (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="aba42-227">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="aba42-228">MVC</span><span class="sxs-lookup"><span data-stu-id="aba42-228">mvc</span></span>](#web-options)             | <span data-ttu-id="aba42-229">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="aba42-229">[C#], F#</span></span>     | <span data-ttu-id="aba42-230">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="aba42-230">Web/MVC</span></span>                               | <span data-ttu-id="aba42-231">1,0</span><span class="sxs-lookup"><span data-stu-id="aba42-231">1.0</span></span>        |
| <span data-ttu-id="aba42-232">ASP.NET Core Web uygulaması</span><span class="sxs-lookup"><span data-stu-id="aba42-232">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="aba42-233">WEBAPP, Razor</span><span class="sxs-lookup"><span data-stu-id="aba42-233">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="aba42-234">Þ</span><span class="sxs-lookup"><span data-stu-id="aba42-234">[C#]</span></span>         | <span data-ttu-id="aba42-235">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="aba42-235">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="aba42-236">2,2, 2,0</span><span class="sxs-lookup"><span data-stu-id="aba42-236">2.2, 2.0</span></span>   |
| <span data-ttu-id="aba42-237">Angular ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="aba42-237">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="aba42-238">Angular</span><span class="sxs-lookup"><span data-stu-id="aba42-238">angular</span></span>](#spa)                 | <span data-ttu-id="aba42-239">Þ</span><span class="sxs-lookup"><span data-stu-id="aba42-239">[C#]</span></span>         | <span data-ttu-id="aba42-240">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="aba42-240">Web/MVC/SPA</span></span>                           | <span data-ttu-id="aba42-241">2,0</span><span class="sxs-lookup"><span data-stu-id="aba42-241">2.0</span></span>        |
| <span data-ttu-id="aba42-242">React.js ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="aba42-242">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="aba42-243">tıkla</span><span class="sxs-lookup"><span data-stu-id="aba42-243">react</span></span>](#spa)                   | <span data-ttu-id="aba42-244">Þ</span><span class="sxs-lookup"><span data-stu-id="aba42-244">[C#]</span></span>         | <span data-ttu-id="aba42-245">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="aba42-245">Web/MVC/SPA</span></span>                           | <span data-ttu-id="aba42-246">2,0</span><span class="sxs-lookup"><span data-stu-id="aba42-246">2.0</span></span>        |
| <span data-ttu-id="aba42-247">React.js ve Redux ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="aba42-247">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="aba42-248">reactredux</span><span class="sxs-lookup"><span data-stu-id="aba42-248">reactredux</span></span>](#reactredux)       | <span data-ttu-id="aba42-249">Þ</span><span class="sxs-lookup"><span data-stu-id="aba42-249">[C#]</span></span>         | <span data-ttu-id="aba42-250">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="aba42-250">Web/MVC/SPA</span></span>                           | <span data-ttu-id="aba42-251">2,0</span><span class="sxs-lookup"><span data-stu-id="aba42-251">2.0</span></span>        |
| <span data-ttu-id="aba42-252">Razor sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="aba42-252">Razor Class Library</span></span>                          | [<span data-ttu-id="aba42-253">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="aba42-253">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="aba42-254">Þ</span><span class="sxs-lookup"><span data-stu-id="aba42-254">[C#]</span></span>         | <span data-ttu-id="aba42-255">Web/Razor/kitaplık/Razor sınıfı kitaplığı</span><span class="sxs-lookup"><span data-stu-id="aba42-255">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="aba42-256">2.1</span><span class="sxs-lookup"><span data-stu-id="aba42-256">2.1</span></span>        |
| <span data-ttu-id="aba42-257">ASP.NET Core Web API'si</span><span class="sxs-lookup"><span data-stu-id="aba42-257">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="aba42-258">WebApi</span><span class="sxs-lookup"><span data-stu-id="aba42-258">webapi</span></span>](#webapi)               | <span data-ttu-id="aba42-259">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="aba42-259">[C#], F#</span></span>     | <span data-ttu-id="aba42-260">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="aba42-260">Web/WebAPI</span></span>                            | <span data-ttu-id="aba42-261">1,0</span><span class="sxs-lookup"><span data-stu-id="aba42-261">1.0</span></span>        |
| <span data-ttu-id="aba42-262">ASP.NET Core gRPC hizmeti</span><span class="sxs-lookup"><span data-stu-id="aba42-262">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="aba42-263">GRPC</span><span class="sxs-lookup"><span data-stu-id="aba42-263">grpc</span></span>](#web-others)             | <span data-ttu-id="aba42-264">Þ</span><span class="sxs-lookup"><span data-stu-id="aba42-264">[C#]</span></span>         | <span data-ttu-id="aba42-265">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="aba42-265">Web/gRPC</span></span>                              | <span data-ttu-id="aba42-266">3,0</span><span class="sxs-lookup"><span data-stu-id="aba42-266">3.0</span></span>        |
| <span data-ttu-id="aba42-267">DotNet gitignore dosyası</span><span class="sxs-lookup"><span data-stu-id="aba42-267">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="aba42-268">Config</span><span class="sxs-lookup"><span data-stu-id="aba42-268">Config</span></span>                                | <span data-ttu-id="aba42-269">3,0</span><span class="sxs-lookup"><span data-stu-id="aba42-269">3.0</span></span>        |
| <span data-ttu-id="aba42-270">Dosya üzerinde global.js</span><span class="sxs-lookup"><span data-stu-id="aba42-270">global.json file</span></span>                             | [<span data-ttu-id="aba42-271">globaljson</span><span class="sxs-lookup"><span data-stu-id="aba42-271">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="aba42-272">Config</span><span class="sxs-lookup"><span data-stu-id="aba42-272">Config</span></span>                                | <span data-ttu-id="aba42-273">2,0</span><span class="sxs-lookup"><span data-stu-id="aba42-273">2.0</span></span>        |
| <span data-ttu-id="aba42-274">NuGet yapılandırması</span><span class="sxs-lookup"><span data-stu-id="aba42-274">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="aba42-275">Config</span><span class="sxs-lookup"><span data-stu-id="aba42-275">Config</span></span>                                | <span data-ttu-id="aba42-276">1,0</span><span class="sxs-lookup"><span data-stu-id="aba42-276">1.0</span></span>        |
| <span data-ttu-id="aba42-277">DotNet yerel araç bildirim dosyası</span><span class="sxs-lookup"><span data-stu-id="aba42-277">Dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="aba42-278">Config</span><span class="sxs-lookup"><span data-stu-id="aba42-278">Config</span></span>                                | <span data-ttu-id="aba42-279">3,0</span><span class="sxs-lookup"><span data-stu-id="aba42-279">3.0</span></span>        |
| <span data-ttu-id="aba42-280">Web yapılandırması</span><span class="sxs-lookup"><span data-stu-id="aba42-280">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="aba42-281">Config</span><span class="sxs-lookup"><span data-stu-id="aba42-281">Config</span></span>                                | <span data-ttu-id="aba42-282">1,0</span><span class="sxs-lookup"><span data-stu-id="aba42-282">1.0</span></span>        |
| <span data-ttu-id="aba42-283">Çözüm dosyası</span><span class="sxs-lookup"><span data-stu-id="aba42-283">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="aba42-284">Çözüm</span><span class="sxs-lookup"><span data-stu-id="aba42-284">Solution</span></span>                              | <span data-ttu-id="aba42-285">1,0</span><span class="sxs-lookup"><span data-stu-id="aba42-285">1.0</span></span>        |
| <span data-ttu-id="aba42-286">Protokol arabelleği dosyası</span><span class="sxs-lookup"><span data-stu-id="aba42-286">Protocol Buffer File</span></span>                         | [<span data-ttu-id="aba42-287">Proto</span><span class="sxs-lookup"><span data-stu-id="aba42-287">proto</span></span>](#namespace)             |              | <span data-ttu-id="aba42-288">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="aba42-288">Web/gRPC</span></span>                              | <span data-ttu-id="aba42-289">3,0</span><span class="sxs-lookup"><span data-stu-id="aba42-289">3.0</span></span>        |

## <a name="options"></a><span data-ttu-id="aba42-290">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="aba42-290">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="aba42-291">Bir şablon oluşturulmasına neden olacaksa, verilen komutun çalıştırılması durumunda ne olacağını gösteren bir Özet görüntüler.</span><span class="sxs-lookup"><span data-stu-id="aba42-291">Displays a summary of what would happen if the given command were run if it would result in a template creation.</span></span> <span data-ttu-id="aba42-292">.NET Core 2,2 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="aba42-292">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="aba42-293">Var olan dosyaları değiştirebilse bile içeriğin oluşturulmasını zorlar.</span><span class="sxs-lookup"><span data-stu-id="aba42-293">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="aba42-294">Seçilen şablon çıkış dizinindeki mevcut dosyaları geçersiz kılacağından bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="aba42-294">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="aba42-295">Komut için yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="aba42-295">Prints out help for the command.</span></span> <span data-ttu-id="aba42-296">`dotnet new`Komutun kendisi veya herhangi bir şablon için çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="aba42-296">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="aba42-297">Örneğin, `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="aba42-297">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="aba42-298">Veya tarafından belirtilen bir şablon paketini `PATH` kurar `NUGET_ID` .</span><span class="sxs-lookup"><span data-stu-id="aba42-298">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="aba42-299">Şablon paketinin bir ön sürümü sürümünü yüklemek istiyorsanız, sürümü biçiminde belirtmeniz gerekir `<package-name>::<package-version>` .</span><span class="sxs-lookup"><span data-stu-id="aba42-299">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="aba42-300">Varsayılan olarak, `dotnet new` \* en son kararlı paket sürümünü temsil eden sürüm için geçirir.</span><span class="sxs-lookup"><span data-stu-id="aba42-300">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="aba42-301">[Örnekler](#examples) bölümündeki bir örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="aba42-301">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="aba42-302">Bu komutu çalıştırdığınızda şablonun bir sürümü zaten yüklüyse, şablon belirtilen sürüme veya sürüm belirtilmemişse en son kararlı sürüme güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="aba42-302">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="aba42-303">Özel şablonlar oluşturma hakkında daha fazla bilgi için bkz. [DotNet New Için özel şablonlar](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="aba42-303">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="aba42-304">Belirtilen adı içeren şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="aba42-304">Lists templates containing the specified name.</span></span> <span data-ttu-id="aba42-305">Ad belirtilmemişse, tüm şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="aba42-305">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="aba42-306">Oluşturulacak şablonun dili.</span><span class="sxs-lookup"><span data-stu-id="aba42-306">The language of the template to create.</span></span> <span data-ttu-id="aba42-307">Kabul edilen dil şablona göre değişir (bkz. [arguments](#arguments) bölümünde Varsayılanlar).</span><span class="sxs-lookup"><span data-stu-id="aba42-307">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="aba42-308">Bazı şablonlar için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="aba42-308">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="aba42-309">Bazı kabuklar `#` özel bir karakter olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="aba42-309">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="aba42-310">Bu durumlarda, dil parametre değerini tırnak içine alın.</span><span class="sxs-lookup"><span data-stu-id="aba42-310">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="aba42-311">Örneğin, `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="aba42-311">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="aba42-312">Oluşturulan çıkışın adı.</span><span class="sxs-lookup"><span data-stu-id="aba42-312">The name for the created output.</span></span> <span data-ttu-id="aba42-313">Ad belirtilmemişse, geçerli dizinin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="aba42-313">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source <SOURCE>`**

  <span data-ttu-id="aba42-314">Yüklemesi sırasında kullanılacak bir NuGet kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="aba42-314">Specifies a NuGet source to use during install.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="aba42-315">Oluşturulan çıkışın yerleştirileceği konum.</span><span class="sxs-lookup"><span data-stu-id="aba42-315">Location to place the generated output.</span></span> <span data-ttu-id="aba42-316">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="aba42-316">The default is the current directory.</span></span>

- **`--type <TYPE>`**

  <span data-ttu-id="aba42-317">Şablonları kullanılabilir türlerine göre filtreler.</span><span class="sxs-lookup"><span data-stu-id="aba42-317">Filters templates based on available types.</span></span> <span data-ttu-id="aba42-318">Önceden tanımlanmış değerler `project` ve ' dir `item` .</span><span class="sxs-lookup"><span data-stu-id="aba42-318">Predefined values are `project` and `item`.</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="aba42-319">Veya belirtilen bir şablon paketini kaldırır `PATH` `NUGET_ID` .</span><span class="sxs-lookup"><span data-stu-id="aba42-319">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="aba42-320">`<PATH|NUGET_ID>`Değer belirtilmediğinde, yüklü olan tüm şablon paketleri ve bunlarla ilişkili şablonlar görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="aba42-320">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="aba42-321">Belirtirken `NUGET_ID` , sürüm numarasını eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="aba42-321">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="aba42-322">Bu seçeneğe bir parametre belirtmezseniz, komut, yüklü şablonları ve bunlarla ilgili ayrıntıları listeler.</span><span class="sxs-lookup"><span data-stu-id="aba42-322">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="aba42-323">Bir şablonu kullanarak kaldırmak için `PATH` , yolu tam olarak nitelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="aba42-323">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="aba42-324">Örneğin, *C:/Users/ \<USER> /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* çalışır, ancak içeren klasörden *./GarciaSoftware.ConsoleTemplate.CSharp* olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="aba42-324">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="aba42-325">Şablon yolunuzda son Sonlandırıcı Dizin eğik çizgisi eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="aba42-325">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="aba42-326">Şu anda yüklü olan şablon paketleri için kullanılabilir güncelleştirmelerin olup olmadığını denetler ve bunları kurar.</span><span class="sxs-lookup"><span data-stu-id="aba42-326">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="aba42-327">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="aba42-327">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="aba42-328">Şu anda yüklü olan şablon paketleri için kullanılabilir güncelleştirmeler olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="aba42-328">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="aba42-329">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="aba42-329">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="aba42-330">Şablon seçenekleri</span><span class="sxs-lookup"><span data-stu-id="aba42-330">Template options</span></span>

<span data-ttu-id="aba42-331">Her proje şablonunda ek seçenekler bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="aba42-331">Each project template may have additional options available.</span></span> <span data-ttu-id="aba42-332">Çekirdek şablonlar aşağıdaki ek seçeneklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="aba42-332">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="aba42-333">console</span><span class="sxs-lookup"><span data-stu-id="aba42-333">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="aba42-334">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="aba42-334">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="aba42-335">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="aba42-335">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="aba42-336">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="aba42-336">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="aba42-337">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="aba42-337">SDK version</span></span> | <span data-ttu-id="aba42-338">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="aba42-338">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="aba42-339">5.0</span><span class="sxs-lookup"><span data-stu-id="aba42-339">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="aba42-340">3,1</span><span class="sxs-lookup"><span data-stu-id="aba42-340">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="aba42-341">3,0</span><span class="sxs-lookup"><span data-stu-id="aba42-341">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="aba42-342">`LangVersion`Oluşturulan proje dosyasındaki özelliği ayarlar.</span><span class="sxs-lookup"><span data-stu-id="aba42-342">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="aba42-343">Örneğin, `--langVersion 7.3` C# 7,3 kullanmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="aba42-343">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="aba42-344">F # için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="aba42-344">Not supported for F#.</span></span> <span data-ttu-id="aba42-345">.NET Core 2,2 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="aba42-345">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="aba42-346">Varsayılan C# sürümlerinin listesi için bkz. [Varsayılanlar](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="aba42-346">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="aba42-347">Belirtilmişse, proje oluşturma sırasında örtük geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="aba42-347">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="aba42-348">.NET Core 2,2 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="aba42-348">Available since .NET Core 2.2 SDK.</span></span>

<span data-ttu-id="aba42-349">\*\*_</span><span class="sxs-lookup"><span data-stu-id="aba42-349">\*\*_</span></span>

### <a name="classlib"></a><span data-ttu-id="aba42-350">projesinin</span><span class="sxs-lookup"><span data-stu-id="aba42-350">classlib</span></span>

- <span data-ttu-id="aba42-351">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="aba42-351">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="aba42-352">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="aba42-352">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="aba42-353">Değerler: `net5.0` veya bir `netcoreapp<version>` .NET sınıf kitaplığı oluşturmak veya `netstandard<version>` bir .NET Standard sınıf kitaplığı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="aba42-353">Values: `net5.0` or `netcoreapp<version>` to create a .NET Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="aba42-354">.NET 5,0 SDK için varsayılan değer `net5.0` .</span><span class="sxs-lookup"><span data-stu-id="aba42-354">The default value for .NET 5.0 SDK is `net5.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="aba42-355">`LangVersion`Oluşturulan proje dosyasındaki özelliği ayarlar.</span><span class="sxs-lookup"><span data-stu-id="aba42-355">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="aba42-356">Örneğin, `--langVersion 7.3` C# 7,3 kullanmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="aba42-356">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="aba42-357">F # için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="aba42-357">Not supported for F#.</span></span> <span data-ttu-id="aba42-358">.NET Core 2,2 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="aba42-358">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="aba42-359">Varsayılan C# sürümlerinin listesi için bkz. [Varsayılanlar](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="aba42-359">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="aba42-360">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="aba42-360">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="aba42-361">\*\*_</span><span class="sxs-lookup"><span data-stu-id="aba42-361">\*\*_</span></span>

### <a name="wpf-wpflib-wpfcustomcontrollib-wpfusercontrollib"></a><a name="wpf"></a> <span data-ttu-id="aba42-362">WPF, wpflib, wpfcustomcontrollib, wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="aba42-362">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- <span data-ttu-id="aba42-363">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="aba42-363">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="aba42-364">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="aba42-364">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="aba42-365">`net5.0` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="aba42-365">The default value is `net5.0`.</span></span> <span data-ttu-id="aba42-366">.NET Core 3,1 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="aba42-366">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="aba42-367">`LangVersion`Oluşturulan proje dosyasındaki özelliği ayarlar.</span><span class="sxs-lookup"><span data-stu-id="aba42-367">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="aba42-368">Örneğin, `--langVersion 7.3` C# 7,3 kullanmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="aba42-368">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="aba42-369">Varsayılan C# sürümlerinin listesi için bkz. [Varsayılanlar](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="aba42-369">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="aba42-370">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="aba42-370">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="aba42-371">\*\*_</span><span class="sxs-lookup"><span data-stu-id="aba42-371">\*\*_</span></span>

### <a name="winforms-winformslib"></a><a name="winforms"></a> <span data-ttu-id="aba42-372">WinForms, winformslib</span><span class="sxs-lookup"><span data-stu-id="aba42-372">winforms, winformslib</span></span>

- <span data-ttu-id="aba42-373">_ *`--langVersion <VERSION_NUMBER>`*\*</span><span class="sxs-lookup"><span data-stu-id="aba42-373">_ *`--langVersion <VERSION_NUMBER>`*\*</span></span>

  <span data-ttu-id="aba42-374">`LangVersion`Oluşturulan proje dosyasındaki özelliği ayarlar.</span><span class="sxs-lookup"><span data-stu-id="aba42-374">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="aba42-375">Örneğin, `--langVersion 7.3` C# 7,3 kullanmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="aba42-375">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="aba42-376">Varsayılan C# sürümlerinin listesi için bkz. [Varsayılanlar](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="aba42-376">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="aba42-377">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="aba42-377">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="aba42-378">\*\*_</span><span class="sxs-lookup"><span data-stu-id="aba42-378">\*\*_</span></span>

### <a name="worker-grpc"></a><a name="web-others"></a> <span data-ttu-id="aba42-379">çalışan, GRPC</span><span class="sxs-lookup"><span data-stu-id="aba42-379">worker, grpc</span></span>

- <span data-ttu-id="aba42-380">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="aba42-380">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="aba42-381">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="aba42-381">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="aba42-382">`netcoreapp3.1` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="aba42-382">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="aba42-383">.NET Core 3,1 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="aba42-383">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="aba42-384">Oluşturulan şablondan *launchSettings.js* dışlar.</span><span class="sxs-lookup"><span data-stu-id="aba42-384">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="aba42-385">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="aba42-385">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="aba42-386">\*\*_</span><span class="sxs-lookup"><span data-stu-id="aba42-386">\*\*_</span></span>

### <a name="mstest-xunit"></a><a name="test"></a> <span data-ttu-id="aba42-387">MSTest, xUnit</span><span class="sxs-lookup"><span data-stu-id="aba42-387">mstest, xunit</span></span>

- <span data-ttu-id="aba42-388">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="aba42-388">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="aba42-389">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="aba42-389">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="aba42-390">.NET Core 3,0 SDK 'dan beri kullanılabilir seçeneği.</span><span class="sxs-lookup"><span data-stu-id="aba42-390">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="aba42-391">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="aba42-391">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="aba42-392">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="aba42-392">SDK version</span></span> | <span data-ttu-id="aba42-393">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="aba42-393">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="aba42-394">5.0</span><span class="sxs-lookup"><span data-stu-id="aba42-394">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="aba42-395">3,1</span><span class="sxs-lookup"><span data-stu-id="aba42-395">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="aba42-396">3,0</span><span class="sxs-lookup"><span data-stu-id="aba42-396">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="aba42-397">[DotNet Pack](dotnet-pack.md)kullanarak proje için paketleme imkanı sunar.</span><span class="sxs-lookup"><span data-stu-id="aba42-397">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="aba42-398">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="aba42-398">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="aba42-399">\*\*_</span><span class="sxs-lookup"><span data-stu-id="aba42-399">\*\*_</span></span>

### <a name="nunit"></a><span data-ttu-id="aba42-400">NUnit</span><span class="sxs-lookup"><span data-stu-id="aba42-400">nunit</span></span>

- <span data-ttu-id="aba42-401">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="aba42-401">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="aba42-402">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="aba42-402">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="aba42-403">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="aba42-403">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="aba42-404">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="aba42-404">SDK version</span></span> | <span data-ttu-id="aba42-405">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="aba42-405">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="aba42-406">5.0</span><span class="sxs-lookup"><span data-stu-id="aba42-406">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="aba42-407">3,1</span><span class="sxs-lookup"><span data-stu-id="aba42-407">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="aba42-408">3,0</span><span class="sxs-lookup"><span data-stu-id="aba42-408">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="aba42-409">2.2</span><span class="sxs-lookup"><span data-stu-id="aba42-409">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="aba42-410">2.1</span><span class="sxs-lookup"><span data-stu-id="aba42-410">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="aba42-411">[DotNet Pack](dotnet-pack.md)kullanarak proje için paketleme imkanı sunar.</span><span class="sxs-lookup"><span data-stu-id="aba42-411">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="aba42-412">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="aba42-412">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="aba42-413">\*\*_</span><span class="sxs-lookup"><span data-stu-id="aba42-413">\*\*_</span></span>

### <a name="page"></a><span data-ttu-id="aba42-414">page (sayfa)</span><span class="sxs-lookup"><span data-stu-id="aba42-414">page</span></span>

- <span data-ttu-id="aba42-415">_ *`-na|--namespace <NAMESPACE_NAME>`*\*</span><span class="sxs-lookup"><span data-stu-id="aba42-415">_ *`-na|--namespace <NAMESPACE_NAME>`*\*</span></span>

  <span data-ttu-id="aba42-416">Oluşturulan kod için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="aba42-416">Namespace for the generated code.</span></span> <span data-ttu-id="aba42-417">`MyApp.Namespace` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="aba42-417">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="aba42-418">PageModel olmadan sayfayı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="aba42-418">Creates the page without a PageModel.</span></span>

<span data-ttu-id="aba42-419">\*\*_</span><span class="sxs-lookup"><span data-stu-id="aba42-419">\*\*_</span></span>

### <a name="viewimports-proto"></a><a name="namespace"></a> <span data-ttu-id="aba42-420">viewıtemler, Proto</span><span class="sxs-lookup"><span data-stu-id="aba42-420">viewimports, proto</span></span>

- <span data-ttu-id="aba42-421">_ *`-na|--namespace <NAMESPACE_NAME>`*\*</span><span class="sxs-lookup"><span data-stu-id="aba42-421">_ *`-na|--namespace <NAMESPACE_NAME>`*\*</span></span>

  <span data-ttu-id="aba42-422">Oluşturulan kod için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="aba42-422">Namespace for the generated code.</span></span> <span data-ttu-id="aba42-423">`MyApp.Namespace` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="aba42-423">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="aba42-424">\*\*_</span><span class="sxs-lookup"><span data-stu-id="aba42-424">\*\*_</span></span>

### <a name="blazorserver"></a><span data-ttu-id="aba42-425">blazorserver</span><span class="sxs-lookup"><span data-stu-id="aba42-425">blazorserver</span></span>

- <span data-ttu-id="aba42-426">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="aba42-426">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="aba42-427">Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="aba42-427">The type of authentication to use.</span></span> <span data-ttu-id="aba42-428">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="aba42-428">The possible values are:</span></span>

  - <span data-ttu-id="aba42-429">`None` -Kimlik doğrulaması yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="aba42-429">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="aba42-430">`Individual` -Bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="aba42-430">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="aba42-431">`IndividualB2C` -Azure AD B2C ile bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="aba42-431">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="aba42-432">`SingleOrg` -Tek bir kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="aba42-432">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="aba42-433">`MultiOrg` -Birden çok kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="aba42-433">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="aba42-434">`Windows` -Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="aba42-434">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="aba42-435">Bağlanılacak Azure Active Directory B2C örneği.</span><span class="sxs-lookup"><span data-stu-id="aba42-435">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="aba42-436">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="aba42-436">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="aba42-437">`https://login.microsoftonline.com/tfp/` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="aba42-437">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="aba42-438">Bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="aba42-438">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="aba42-439">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="aba42-439">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="aba42-440">Bu proje için parola sıfırlama ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="aba42-440">The reset password policy ID for this project.</span></span> <span data-ttu-id="aba42-441">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="aba42-441">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="aba42-442">Bu proje için profil ilke KIMLIĞINI Düzenle.</span><span class="sxs-lookup"><span data-stu-id="aba42-442">The edit profile policy ID for this project.</span></span> <span data-ttu-id="aba42-443">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="aba42-443">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="aba42-444">Bağlanılacak Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="aba42-444">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="aba42-445">`SingleOrg`Veya `MultiOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="aba42-445">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="aba42-446">`https://login.microsoftonline.com/` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="aba42-446">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="aba42-447">Bu projenin Istemci KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="aba42-447">The Client ID for this project.</span></span> <span data-ttu-id="aba42-448">`IndividualB2C`, `SingleOrg` Veya `MultiOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="aba42-448">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="aba42-449">`11111111-1111-1111-11111111111111111` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="aba42-449">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="aba42-450">Dizin kiracının etki alanı.</span><span class="sxs-lookup"><span data-stu-id="aba42-450">The domain for the directory tenant.</span></span> <span data-ttu-id="aba42-451">`SingleOrg`Veya `IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="aba42-451">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="aba42-452">`qualified.domain.name` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="aba42-452">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="aba42-453">Bağlanılacak dizinin Tenantıd KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="aba42-453">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="aba42-454">`SingleOrg`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="aba42-454">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="aba42-455">`22222222-2222-2222-2222-222222222222` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="aba42-455">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="aba42-456">Uygulamanın yeniden yönlendirme URI 'sinin temel yolundaki istek yolu.</span><span class="sxs-lookup"><span data-stu-id="aba42-456">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="aba42-457">`SingleOrg`Veya `IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="aba42-457">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="aba42-458">`/signin-oidc` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="aba42-458">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="aba42-459">Bu uygulamanın dizine okuma erişimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="aba42-459">Allows this application read-access to the directory.</span></span> <span data-ttu-id="aba42-460">Yalnızca `SingleOrg` veya `MultiOrg` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="aba42-460">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="aba42-461">Oluşturulan şablondan *launchSettings.js* dışlar.</span><span class="sxs-lookup"><span data-stu-id="aba42-461">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="aba42-462">HTTPS 'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="aba42-462">Turns off HTTPS.</span></span> <span data-ttu-id="aba42-463">Bu seçenek yalnızca,, `Individual` , `IndividualB2C` `SingleOrg` veya için kullanılmıyorsa geçerlidir `MultiOrg` `--auth` .</span><span class="sxs-lookup"><span data-stu-id="aba42-463">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="aba42-464">SQLite yerine LocalDB kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="aba42-464">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="aba42-465">Yalnızca `Individual` veya `IndividualB2C` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="aba42-465">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="aba42-466">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="aba42-466">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="aba42-467">\*\*_</span><span class="sxs-lookup"><span data-stu-id="aba42-467">\*\*_</span></span>

### <a name="blazorwasm"></a><span data-ttu-id="aba42-468">blazorwasm</span><span class="sxs-lookup"><span data-stu-id="aba42-468">blazorwasm</span></span>

- <span data-ttu-id="aba42-469">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="aba42-469">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="aba42-470">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="aba42-470">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="aba42-471">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="aba42-471">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="aba42-472">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="aba42-472">SDK version</span></span> | <span data-ttu-id="aba42-473">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="aba42-473">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="aba42-474">5.0</span><span class="sxs-lookup"><span data-stu-id="aba42-474">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="aba42-475">3,1</span><span class="sxs-lookup"><span data-stu-id="aba42-475">3.1</span></span>         | `netcoreapp3.1` |

- **`--no-restore`**

  <span data-ttu-id="aba42-476">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="aba42-476">Doesn't execute an implicit restore during project creation.</span></span>

- **`-ho|--hosted`**

  <span data-ttu-id="aba42-477">Uygulama için bir ASP.NET Core Konağı içerir :::no-loc(Blazor)::: :::no-loc(WebAssembly)::: .</span><span class="sxs-lookup"><span data-stu-id="aba42-477">Includes an ASP.NET Core host for the :::no-loc(Blazor)::: :::no-loc(WebAssembly)::: app.</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="aba42-478">Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="aba42-478">The type of authentication to use.</span></span> <span data-ttu-id="aba42-479">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="aba42-479">The possible values are:</span></span>

  - <span data-ttu-id="aba42-480">`None` -Kimlik doğrulaması yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="aba42-480">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="aba42-481">`Individual` -Bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="aba42-481">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="aba42-482">`IndividualB2C` -Azure AD B2C ile bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="aba42-482">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="aba42-483">`SingleOrg` -Tek bir kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="aba42-483">`SingleOrg` - Organizational authentication for a single tenant.</span></span>

- **`--authority <AUTHORITY>`**

  <span data-ttu-id="aba42-484">OıDC sağlayıcısı yetkilisi.</span><span class="sxs-lookup"><span data-stu-id="aba42-484">The authority of the OIDC provider.</span></span> <span data-ttu-id="aba42-485">`Individual`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="aba42-485">Use with `Individual` authentication.</span></span> <span data-ttu-id="aba42-486">`https://login.microsoftonline.com/` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="aba42-486">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="aba42-487">Bağlanılacak Azure Active Directory B2C örneği.</span><span class="sxs-lookup"><span data-stu-id="aba42-487">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="aba42-488">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="aba42-488">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="aba42-489">`https://aadB2CInstance.b2clogin.com/` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="aba42-489">The default value is `https://aadB2CInstance.b2clogin.com/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="aba42-490">Bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="aba42-490">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="aba42-491">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="aba42-491">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="aba42-492">Bağlanılacak Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="aba42-492">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="aba42-493">`SingleOrg`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="aba42-493">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="aba42-494">`https://login.microsoftonline.com/` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="aba42-494">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="aba42-495">Bu projenin Istemci KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="aba42-495">The Client ID for this project.</span></span> <span data-ttu-id="aba42-496">`IndividualB2C` `SingleOrg` `Individual` Tek başına senaryolarda, veya ile kimlik doğrulaması kullanın.</span><span class="sxs-lookup"><span data-stu-id="aba42-496">Use with `IndividualB2C`, `SingleOrg`, or `Individual` authentication in standalone scenarios.</span></span> <span data-ttu-id="aba42-497">`33333333-3333-3333-33333333333333333` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="aba42-497">The default value is `33333333-3333-3333-33333333333333333`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="aba42-498">Dizin kiracının etki alanı.</span><span class="sxs-lookup"><span data-stu-id="aba42-498">The domain for the directory tenant.</span></span> <span data-ttu-id="aba42-499">`SingleOrg`Veya `IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="aba42-499">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="aba42-500">`qualified.domain.name` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="aba42-500">The default value is `qualified.domain.name`.</span></span>

- **`--app-id-uri <URI>`**

  <span data-ttu-id="aba42-501">Çağırmak istediğiniz sunucu API 'SI için uygulama KIMLIĞI URI 'Si.</span><span class="sxs-lookup"><span data-stu-id="aba42-501">The App ID Uri for the server API you want to call.</span></span> <span data-ttu-id="aba42-502">`SingleOrg`Veya `IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="aba42-502">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="aba42-503">`api.id.uri` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="aba42-503">The default value is `api.id.uri`.</span></span>

- **`--api-client-id <ID>`**

  <span data-ttu-id="aba42-504">Sunucunun barındırdığı API 'nin Istemci KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="aba42-504">The Client ID for the API that the server hosts.</span></span> <span data-ttu-id="aba42-505">`SingleOrg`Veya `IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="aba42-505">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="aba42-506">`11111111-1111-1111-11111111111111111` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="aba42-506">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`-s|--default-scope <SCOPE>`**

  <span data-ttu-id="aba42-507">İstemcinin bir erişim belirteci sağlamasını istemesi gereken API kapsamı.</span><span class="sxs-lookup"><span data-stu-id="aba42-507">The API scope the client needs to request to provision an access token.</span></span> <span data-ttu-id="aba42-508">`SingleOrg`Veya `IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="aba42-508">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="aba42-509">`user_impersonation` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="aba42-509">The default value is `user_impersonation`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="aba42-510">Bağlanılacak dizinin Tenantıd KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="aba42-510">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="aba42-511">`SingleOrg`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="aba42-511">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="aba42-512">`22222222-2222-2222-2222-222222222222` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="aba42-512">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="aba42-513">Bu uygulamanın dizine okuma erişimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="aba42-513">Allows this application read-access to the directory.</span></span> <span data-ttu-id="aba42-514">Yalnızca `SingleOrg` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="aba42-514">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="aba42-515">Oluşturulan şablondan *launchSettings.js* dışlar.</span><span class="sxs-lookup"><span data-stu-id="aba42-515">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-p|--pwa`**

  <span data-ttu-id="aba42-516">yüklemeyi ve çevrimdışı kullanımı destekleyen bir aşamalı Web uygulaması (PWA) üretir.</span><span class="sxs-lookup"><span data-stu-id="aba42-516">produces a Progressive Web Application (PWA) supporting installation and offline use.</span></span>

- **`--no-https`**

  <span data-ttu-id="aba42-517">HTTPS 'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="aba42-517">Turns off HTTPS.</span></span> <span data-ttu-id="aba42-518">Bu seçenek yalnızca,, `Individual` `IndividualB2C` veya için kullanılmıyorsa geçerlidir `SingleOrg` `--auth` .</span><span class="sxs-lookup"><span data-stu-id="aba42-518">This option only applies if `Individual`, `IndividualB2C`, or `SingleOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="aba42-519">SQLite yerine LocalDB kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="aba42-519">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="aba42-520">Yalnızca `Individual` veya `IndividualB2C` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="aba42-520">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--called-api-url <URL>`**

  <span data-ttu-id="aba42-521">Web uygulamasından çağrılacak API 'nin URL 'SI.</span><span class="sxs-lookup"><span data-stu-id="aba42-521">URL of the API to call from the web app.</span></span> <span data-ttu-id="aba42-522">Yalnızca `SingleOrg` `IndividualB2C` ASP.NET Core bir ana bilgisayar olmadan veya kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="aba42-522">Only applies to `SingleOrg` or `IndividualB2C` authentication without an ASP.NET Core host specified.</span></span> <span data-ttu-id="aba42-523">`https://graph.microsoft.com/v1.0/me` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="aba42-523">The default value is `https://graph.microsoft.com/v1.0/me`.</span></span>

- **`--calls-graph`**

  <span data-ttu-id="aba42-524">Web uygulamasının Microsoft Graph çağırıyorsa belirtir.</span><span class="sxs-lookup"><span data-stu-id="aba42-524">Specifies if the web app calls Microsoft Graph.</span></span> <span data-ttu-id="aba42-525">Yalnızca `SingleOrg` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="aba42-525">Only applies to `SingleOrg` authentication.</span></span>

- **`--called-api-scopes <SCOPES>`**

  <span data-ttu-id="aba42-526">Web uygulamasından API 'yi çağırmak için istenen kapsamlar.</span><span class="sxs-lookup"><span data-stu-id="aba42-526">Scopes to request to call the API from the web app.</span></span> <span data-ttu-id="aba42-527">Yalnızca `SingleOrg` `IndividualB2C` ASP.NET Core bir ana bilgisayar olmadan veya kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="aba42-527">Only applies to `SingleOrg` or `IndividualB2C` authentication without an ASP.NET Core host specified.</span></span> <span data-ttu-id="aba42-528">Varsayılan değer: `user.read`.</span><span class="sxs-lookup"><span data-stu-id="aba42-528">The default is `user.read`.</span></span>

<span data-ttu-id="aba42-529">\*\*_</span><span class="sxs-lookup"><span data-stu-id="aba42-529">\*\*_</span></span>

### <a name="web"></a><span data-ttu-id="aba42-530">web</span><span class="sxs-lookup"><span data-stu-id="aba42-530">web</span></span>

- <span data-ttu-id="aba42-531">_ *`--exclude-launch-settings`*\*</span><span class="sxs-lookup"><span data-stu-id="aba42-531">_ *`--exclude-launch-settings`*\*</span></span>

  <span data-ttu-id="aba42-532">Oluşturulan şablondan *launchSettings.js* dışlar.</span><span class="sxs-lookup"><span data-stu-id="aba42-532">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="aba42-533">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="aba42-533">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="aba42-534">Seçenek .NET Core 2,2 SDK sürümünde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="aba42-534">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="aba42-535">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="aba42-535">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="aba42-536">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="aba42-536">SDK version</span></span> | <span data-ttu-id="aba42-537">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="aba42-537">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="aba42-538">5.0</span><span class="sxs-lookup"><span data-stu-id="aba42-538">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="aba42-539">3,1</span><span class="sxs-lookup"><span data-stu-id="aba42-539">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="aba42-540">3,0</span><span class="sxs-lookup"><span data-stu-id="aba42-540">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="aba42-541">2.1</span><span class="sxs-lookup"><span data-stu-id="aba42-541">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="aba42-542">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="aba42-542">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="aba42-543">HTTPS 'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="aba42-543">Turns off HTTPS.</span></span>

<span data-ttu-id="aba42-544">\*\*_</span><span class="sxs-lookup"><span data-stu-id="aba42-544">\*\*_</span></span>

### <a name="mvc-webapp"></a><a name="web-options"></a> <span data-ttu-id="aba42-545">MVC, WebApp</span><span class="sxs-lookup"><span data-stu-id="aba42-545">mvc, webapp</span></span>

- <span data-ttu-id="aba42-546">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="aba42-546">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="aba42-547">Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="aba42-547">The type of authentication to use.</span></span> <span data-ttu-id="aba42-548">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="aba42-548">The possible values are:</span></span>

  - <span data-ttu-id="aba42-549">`None` -Kimlik doğrulaması yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="aba42-549">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="aba42-550">`Individual` -Bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="aba42-550">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="aba42-551">`IndividualB2C` -Azure AD B2C ile bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="aba42-551">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="aba42-552">`SingleOrg` -Tek bir kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="aba42-552">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="aba42-553">`MultiOrg` -Birden çok kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="aba42-553">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="aba42-554">`Windows` -Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="aba42-554">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="aba42-555">Bağlanılacak Azure Active Directory B2C örneği.</span><span class="sxs-lookup"><span data-stu-id="aba42-555">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="aba42-556">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="aba42-556">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="aba42-557">`https://login.microsoftonline.com/tfp/` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="aba42-557">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="aba42-558">Bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="aba42-558">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="aba42-559">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="aba42-559">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="aba42-560">Bu proje için parola sıfırlama ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="aba42-560">The reset password policy ID for this project.</span></span> <span data-ttu-id="aba42-561">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="aba42-561">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="aba42-562">Bu proje için profil ilke KIMLIĞINI Düzenle.</span><span class="sxs-lookup"><span data-stu-id="aba42-562">The edit profile policy ID for this project.</span></span> <span data-ttu-id="aba42-563">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="aba42-563">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="aba42-564">Bağlanılacak Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="aba42-564">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="aba42-565">`SingleOrg`Veya `MultiOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="aba42-565">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="aba42-566">`https://login.microsoftonline.com/` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="aba42-566">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="aba42-567">Bu projenin Istemci KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="aba42-567">The Client ID for this project.</span></span> <span data-ttu-id="aba42-568">`IndividualB2C`, `SingleOrg` Veya `MultiOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="aba42-568">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="aba42-569">`11111111-1111-1111-11111111111111111` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="aba42-569">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="aba42-570">Dizin kiracının etki alanı.</span><span class="sxs-lookup"><span data-stu-id="aba42-570">The domain for the directory tenant.</span></span> <span data-ttu-id="aba42-571">`SingleOrg`Veya `IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="aba42-571">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="aba42-572">`qualified.domain.name` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="aba42-572">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="aba42-573">Bağlanılacak dizinin Tenantıd KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="aba42-573">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="aba42-574">`SingleOrg`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="aba42-574">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="aba42-575">`22222222-2222-2222-2222-222222222222` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="aba42-575">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="aba42-576">Uygulamanın yeniden yönlendirme URI 'sinin temel yolundaki istek yolu.</span><span class="sxs-lookup"><span data-stu-id="aba42-576">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="aba42-577">`SingleOrg`Veya `IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="aba42-577">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="aba42-578">`/signin-oidc` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="aba42-578">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="aba42-579">Bu uygulamanın dizine okuma erişimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="aba42-579">Allows this application read-access to the directory.</span></span> <span data-ttu-id="aba42-580">Yalnızca `SingleOrg` veya `MultiOrg` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="aba42-580">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="aba42-581">Oluşturulan şablondan *launchSettings.js* dışlar.</span><span class="sxs-lookup"><span data-stu-id="aba42-581">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="aba42-582">HTTPS 'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="aba42-582">Turns off HTTPS.</span></span> <span data-ttu-id="aba42-583">Bu seçenek yalnızca,,, veya kullanılmıyorsa geçerlidir `Individual` `IndividualB2C` `SingleOrg` `MultiOrg` .</span><span class="sxs-lookup"><span data-stu-id="aba42-583">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="aba42-584">SQLite yerine LocalDB kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="aba42-584">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="aba42-585">Yalnızca `Individual` veya `IndividualB2C` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="aba42-585">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="aba42-586">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="aba42-586">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="aba42-587">.NET Core 3,0 SDK 'dan beri kullanılabilir seçeneği.</span><span class="sxs-lookup"><span data-stu-id="aba42-587">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="aba42-588">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="aba42-588">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="aba42-589">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="aba42-589">SDK version</span></span> | <span data-ttu-id="aba42-590">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="aba42-590">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="aba42-591">5.0</span><span class="sxs-lookup"><span data-stu-id="aba42-591">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="aba42-592">3,1</span><span class="sxs-lookup"><span data-stu-id="aba42-592">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="aba42-593">3,0</span><span class="sxs-lookup"><span data-stu-id="aba42-593">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="aba42-594">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="aba42-594">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="aba42-595">Projedeki BrowserLink öğesini içerir.</span><span class="sxs-lookup"><span data-stu-id="aba42-595">Includes BrowserLink in the project.</span></span> <span data-ttu-id="aba42-596">Seçenek .NET Core 2,2 ve 3,1 SDK sürümünde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="aba42-596">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

- **`-rrc|--razor-runtime-compilation`**

  <span data-ttu-id="aba42-597">Projenin hata ayıklama yapılarında [Razor çalışma zamanı derlemesini](/aspnet/core/mvc/views/view-compilation#runtime-compilation) kullanmak üzere yapılandırılıp yapılandırılmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="aba42-597">Determines if the project is configured to use [Razor runtime compilation](/aspnet/core/mvc/views/view-compilation#runtime-compilation) in Debug builds.</span></span> <span data-ttu-id="aba42-598">.NET Core 3.1.201 SDK 'dan beri kullanılabilir seçeneği.</span><span class="sxs-lookup"><span data-stu-id="aba42-598">Option available since .NET Core 3.1.201 SDK.</span></span>

<span data-ttu-id="aba42-599">\*\*_</span><span class="sxs-lookup"><span data-stu-id="aba42-599">\*\*_</span></span>

### <a name="angular-react"></a><a name="spa"></a> <span data-ttu-id="aba42-600">Angular, tepki verme</span><span class="sxs-lookup"><span data-stu-id="aba42-600">angular, react</span></span>

- <span data-ttu-id="aba42-601">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="aba42-601">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="aba42-602">Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="aba42-602">The type of authentication to use.</span></span> <span data-ttu-id="aba42-603">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="aba42-603">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="aba42-604">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="aba42-604">The possible values are:</span></span>

  - <span data-ttu-id="aba42-605">`None` -Kimlik doğrulaması yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="aba42-605">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="aba42-606">`Individual` -Bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="aba42-606">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="aba42-607">Oluşturulan şablondan *launchSettings.js* dışlar.</span><span class="sxs-lookup"><span data-stu-id="aba42-607">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="aba42-608">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="aba42-608">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="aba42-609">HTTPS 'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="aba42-609">Turns off HTTPS.</span></span> <span data-ttu-id="aba42-610">Bu seçenek yalnızca kimlik doğrulaması ise geçerlidir `None` .</span><span class="sxs-lookup"><span data-stu-id="aba42-610">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="aba42-611">SQLite yerine LocalDB kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="aba42-611">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="aba42-612">Yalnızca `Individual` veya `IndividualB2C` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="aba42-612">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="aba42-613">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="aba42-613">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="aba42-614">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="aba42-614">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="aba42-615">Seçenek .NET Core 2,2 SDK sürümünde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="aba42-615">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="aba42-616">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="aba42-616">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="aba42-617">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="aba42-617">SDK version</span></span> | <span data-ttu-id="aba42-618">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="aba42-618">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="aba42-619">5.0</span><span class="sxs-lookup"><span data-stu-id="aba42-619">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="aba42-620">3,1</span><span class="sxs-lookup"><span data-stu-id="aba42-620">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="aba42-621">3,0</span><span class="sxs-lookup"><span data-stu-id="aba42-621">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="aba42-622">2.1</span><span class="sxs-lookup"><span data-stu-id="aba42-622">2.1</span></span>         | `netcoreapp2.0` |

<span data-ttu-id="aba42-623">\*\*_</span><span class="sxs-lookup"><span data-stu-id="aba42-623">\*\*_</span></span>

### <a name="reactredux"></a><span data-ttu-id="aba42-624">reactredux</span><span class="sxs-lookup"><span data-stu-id="aba42-624">reactredux</span></span>

- <span data-ttu-id="aba42-625">_ *`--exclude-launch-settings`*\*</span><span class="sxs-lookup"><span data-stu-id="aba42-625">_ *`--exclude-launch-settings`*\*</span></span>

  <span data-ttu-id="aba42-626">Oluşturulan şablondan *launchSettings.js* dışlar.</span><span class="sxs-lookup"><span data-stu-id="aba42-626">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="aba42-627">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="aba42-627">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="aba42-628">Seçenek .NET Core 2,2 SDK sürümünde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="aba42-628">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="aba42-629">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="aba42-629">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="aba42-630">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="aba42-630">SDK version</span></span> | <span data-ttu-id="aba42-631">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="aba42-631">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="aba42-632">5.0</span><span class="sxs-lookup"><span data-stu-id="aba42-632">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="aba42-633">3,1</span><span class="sxs-lookup"><span data-stu-id="aba42-633">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="aba42-634">3,0</span><span class="sxs-lookup"><span data-stu-id="aba42-634">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="aba42-635">2.1</span><span class="sxs-lookup"><span data-stu-id="aba42-635">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="aba42-636">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="aba42-636">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="aba42-637">HTTPS 'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="aba42-637">Turns off HTTPS.</span></span>

<span data-ttu-id="aba42-638">\*\*_</span><span class="sxs-lookup"><span data-stu-id="aba42-638">\*\*_</span></span>

### <a name="razorclasslib"></a><span data-ttu-id="aba42-639">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="aba42-639">razorclasslib</span></span>

- <span data-ttu-id="aba42-640">_ *`--no-restore`*\*</span><span class="sxs-lookup"><span data-stu-id="aba42-640">_ *`--no-restore`*\*</span></span>

  <span data-ttu-id="aba42-641">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="aba42-641">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="aba42-642">, Bu kitaplığa bileşenlere ek olarak geleneksel Razor sayfaları ve görünümleri eklenmesini destekler.</span><span class="sxs-lookup"><span data-stu-id="aba42-642">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="aba42-643">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="aba42-643">Available since .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="aba42-644">\*\*_</span><span class="sxs-lookup"><span data-stu-id="aba42-644">\*\*_</span></span>
  
### <a name="webapi"></a><span data-ttu-id="aba42-645">WebApi</span><span class="sxs-lookup"><span data-stu-id="aba42-645">webapi</span></span>

- <span data-ttu-id="aba42-646">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="aba42-646">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="aba42-647">Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="aba42-647">The type of authentication to use.</span></span> <span data-ttu-id="aba42-648">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="aba42-648">The possible values are:</span></span>

  - <span data-ttu-id="aba42-649">`None` -Kimlik doğrulaması yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="aba42-649">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="aba42-650">`IndividualB2C` -Azure AD B2C ile bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="aba42-650">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="aba42-651">`SingleOrg` -Tek bir kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="aba42-651">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="aba42-652">`Windows` -Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="aba42-652">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="aba42-653">Bağlanılacak Azure Active Directory B2C örneği.</span><span class="sxs-lookup"><span data-stu-id="aba42-653">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="aba42-654">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="aba42-654">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="aba42-655">`https://login.microsoftonline.com/tfp/` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="aba42-655">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="aba42-656">Bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="aba42-656">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="aba42-657">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="aba42-657">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="aba42-658">Bağlanılacak Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="aba42-658">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="aba42-659">`SingleOrg`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="aba42-659">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="aba42-660">`https://login.microsoftonline.com/` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="aba42-660">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="aba42-661">Bu projenin Istemci KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="aba42-661">The Client ID for this project.</span></span> <span data-ttu-id="aba42-662">`IndividualB2C`Veya `SingleOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="aba42-662">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="aba42-663">`11111111-1111-1111-11111111111111111` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="aba42-663">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="aba42-664">Dizin kiracının etki alanı.</span><span class="sxs-lookup"><span data-stu-id="aba42-664">The domain for the directory tenant.</span></span> <span data-ttu-id="aba42-665">`IndividualB2C`Veya `SingleOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="aba42-665">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="aba42-666">`qualified.domain.name` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="aba42-666">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="aba42-667">Bağlanılacak dizinin Tenantıd KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="aba42-667">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="aba42-668">`SingleOrg`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="aba42-668">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="aba42-669">`22222222-2222-2222-2222-222222222222` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="aba42-669">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="aba42-670">Bu uygulamanın dizine okuma erişimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="aba42-670">Allows this application read-access to the directory.</span></span> <span data-ttu-id="aba42-671">Yalnızca `SingleOrg` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="aba42-671">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="aba42-672">Oluşturulan şablondan *launchSettings.js* dışlar.</span><span class="sxs-lookup"><span data-stu-id="aba42-672">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="aba42-673">HTTPS 'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="aba42-673">Turns off HTTPS.</span></span> <span data-ttu-id="aba42-674">`app.UseHsts` ve `app.UseHttpsRedirection` öğesine eklenmez `Startup.Configure` .</span><span class="sxs-lookup"><span data-stu-id="aba42-674">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="aba42-675">Bu seçenek yalnızca `IndividualB2C` `SingleOrg` kimlik doğrulaması için kullanılmıyorsa geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="aba42-675">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="aba42-676">SQLite yerine LocalDB kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="aba42-676">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="aba42-677">Yalnızca `IndividualB2C` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="aba42-677">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="aba42-678">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="aba42-678">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="aba42-679">Seçenek .NET Core 2,2 SDK sürümünde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="aba42-679">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="aba42-680">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="aba42-680">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="aba42-681">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="aba42-681">SDK version</span></span> | <span data-ttu-id="aba42-682">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="aba42-682">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="aba42-683">5.0</span><span class="sxs-lookup"><span data-stu-id="aba42-683">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="aba42-684">3,1</span><span class="sxs-lookup"><span data-stu-id="aba42-684">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="aba42-685">3,0</span><span class="sxs-lookup"><span data-stu-id="aba42-685">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="aba42-686">2.1</span><span class="sxs-lookup"><span data-stu-id="aba42-686">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="aba42-687">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="aba42-687">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="aba42-688">\*\*_</span><span class="sxs-lookup"><span data-stu-id="aba42-688">\*\*_</span></span>

### <a name="globaljson"></a><span data-ttu-id="aba42-689">globaljson</span><span class="sxs-lookup"><span data-stu-id="aba42-689">globaljson</span></span>

- <span data-ttu-id="aba42-690">_ *`--sdk-version <VERSION_NUMBER>`*\*</span><span class="sxs-lookup"><span data-stu-id="aba42-690">_ *`--sdk-version <VERSION_NUMBER>`*\*</span></span>

  <span data-ttu-id="aba42-691">Dosyasında *global.js* kullanılacak .NET SDK sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="aba42-691">Specifies the version of the .NET SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="aba42-692">Örnekler</span><span class="sxs-lookup"><span data-stu-id="aba42-692">Examples</span></span>

- <span data-ttu-id="aba42-693">Şablon adını belirterek bir C# konsol uygulaması projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="aba42-693">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="aba42-694">Geçerli dizinde bir F # konsol uygulaması projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="aba42-694">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang "F#"
  ```

- <span data-ttu-id="aba42-695">Belirtilen dizinde bir .NET Standard sınıf kitaplığı projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="aba42-695">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="aba42-696">Geçerli dizinde kimlik doğrulaması olmadan yeni bir ASP.NET Core C# MVC projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="aba42-696">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="aba42-697">Yeni bir xUnit projesi oluştur:</span><span class="sxs-lookup"><span data-stu-id="aba42-697">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="aba42-698">Tek sayfalı uygulama (SPA) şablonları için kullanılabilen tüm şablonları listeleyin:</span><span class="sxs-lookup"><span data-stu-id="aba42-698">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="aba42-699">*We* alt dizeniz ile eşleşen tüm şablonları listeleyin.</span><span class="sxs-lookup"><span data-stu-id="aba42-699">List all templates matching the *we* substring.</span></span> <span data-ttu-id="aba42-700">Tam eşleşme bulunamadı, bu nedenle alt dize eşleştirmesi hem kısa ad hem de ad sütunlarında çalışır.</span><span class="sxs-lookup"><span data-stu-id="aba42-700">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="aba42-701">Şablonla *eşleşen şablonu* çağırma girişimi.</span><span class="sxs-lookup"><span data-stu-id="aba42-701">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="aba42-702">Tek bir eşleşme belirlenemiyorsa kısmi eşleşen şablonları listeleyin.</span><span class="sxs-lookup"><span data-stu-id="aba42-702">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="aba42-703">ASP.NET Core için SPA şablonlarının 2,0 sürümünü yükler:</span><span class="sxs-lookup"><span data-stu-id="aba42-703">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="aba42-704">Yüklü şablonları ve bunlarla ilgili ayrıntıları, bunları kaldırma dahil olmak üzere listeleyin:</span><span class="sxs-lookup"><span data-stu-id="aba42-704">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="aba42-705">SDK sürümünü 3.1.101 olarak ayarlamak için geçerli dizinde bir *global.js* oluşturun:</span><span class="sxs-lookup"><span data-stu-id="aba42-705">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="aba42-706">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aba42-706">See also</span></span>

- [<span data-ttu-id="aba42-707">DotNet New için özel şablonlar</span><span class="sxs-lookup"><span data-stu-id="aba42-707">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="aba42-708">Dotnet new için özel şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="aba42-708">Create a custom template for dotnet new</span></span>](../tutorials/cli-templates-create-item-template.md)
- [<span data-ttu-id="aba42-709">DotNet/DotNet-şablon-örnek GitHub deposu</span><span class="sxs-lookup"><span data-stu-id="aba42-709">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="aba42-710">DotNet New için kullanılabilir şablonlar</span><span class="sxs-lookup"><span data-stu-id="aba42-710">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
