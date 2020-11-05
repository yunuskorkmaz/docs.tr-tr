---
title: DotNet yeni komut
description: DotNet New komutu, belirtilen şablona göre yeni .NET Core projeleri oluşturur.
no-loc:
- ':::no-loc(Blazor):::'
- ':::no-loc(WebAssembly):::'
ms.date: 09/04/2020
ms.openlocfilehash: 2ee06c37cd950f3b9771db2f30fe353435641d67
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400597"
---
# <a name="dotnet-new"></a><span data-ttu-id="07c3b-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="07c3b-103">dotnet new</span></span>

<span data-ttu-id="07c3b-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,0 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="07c3b-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="07c3b-105">Ad</span><span class="sxs-lookup"><span data-stu-id="07c3b-105">Name</span></span>

<span data-ttu-id="07c3b-106">`dotnet new` -Belirtilen şablonu temel alan yeni bir proje, yapılandırma dosyası veya çözüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="07c3b-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="07c3b-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="07c3b-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install {PATH|NUGET_ID}]
    [-lang|--language {"C#"|"F#"|VB}] [-n|--name <OUTPUT_NAME>]
    [--nuget-source <SOURCE>] [-o|--output <OUTPUT_DIRECTORY>]
    [-u|--uninstall] [--update-apply] [--update-check] [Template options]

dotnet new <TEMPLATE> [-l|--list] [--type <TYPE>]

dotnet new -h|--help
```

## <a name="description"></a><span data-ttu-id="07c3b-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="07c3b-108">Description</span></span>

<span data-ttu-id="07c3b-109">`dotnet new`Komut bir şablonu temel alan bir .NET Core projesi veya diğer yapılar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="07c3b-109">The `dotnet new` command creates a .NET Core project or other artifacts based on a template.</span></span>

<span data-ttu-id="07c3b-110">Komutu, belirtilen şablon ve seçeneklere göre diskteki yapıtları oluşturmak için [şablon altyapısını](https://github.com/dotnet/templating) çağırır.</span><span class="sxs-lookup"><span data-stu-id="07c3b-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="07c3b-111">Örtük geri yükleme</span><span class="sxs-lookup"><span data-stu-id="07c3b-111">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="07c3b-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="07c3b-112">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="07c3b-113">Komut çağrıldığında örnek oluşturulacak şablon.</span><span class="sxs-lookup"><span data-stu-id="07c3b-113">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="07c3b-114">Her şablonun geçirebilmeniz için özel seçenekleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-114">Each template might have specific options you can pass.</span></span> <span data-ttu-id="07c3b-115">Daha fazla bilgi için bkz. [şablon seçenekleri](#template-options).</span><span class="sxs-lookup"><span data-stu-id="07c3b-115">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="07c3b-116">`dotnet new --list` `dotnet new -l` Tüm yüklü şablonların listesini görmek için veya çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07c3b-116">You can run `dotnet new --list` or `dotnet new -l` to see a list of all installed templates.</span></span> <span data-ttu-id="07c3b-117">Değer, `TEMPLATE` döndürülen tablodaki **Şablonlar** veya **kısa ad** sütunundaki metinde tam eşleşme değilse, bu iki sütunda bir alt dize eşleşmesi gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-117">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="07c3b-118">.NET Core 3,0 SDK ile başlayarak, aşağıdaki koşullarda komutu çağırdığınızda CLı NuGet.org içindeki şablonları arar `dotnet new` :</span><span class="sxs-lookup"><span data-stu-id="07c3b-118">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="07c3b-119">CLı çağrılırken bir şablon eşleşmesi bulamazsa `dotnet new` , bu da kısmi değildir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-119">If the CLI can't find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="07c3b-120">Şablonun daha yeni bir sürümü kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-120">If there's a newer version of the template available.</span></span> <span data-ttu-id="07c3b-121">Bu durumda, proje veya yapıt oluşturulur ancak CLı, şablonun güncelleştirilmiş bir sürümü hakkında sizi uyarır.</span><span class="sxs-lookup"><span data-stu-id="07c3b-121">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="07c3b-122">Aşağıdaki tabloda, .NET Core SDK ile önceden yüklenmiş olan şablonlar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-122">The following table shows the templates that come pre-installed with the .NET Core SDK.</span></span> <span data-ttu-id="07c3b-123">Şablon için varsayılan dil, köşeli ayraçlar içinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-123">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="07c3b-124">Özel şablon seçeneklerini görmek için kısa ad bağlantısına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="07c3b-124">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="07c3b-125">Şablonlar</span><span class="sxs-lookup"><span data-stu-id="07c3b-125">Templates</span></span>                                    | <span data-ttu-id="07c3b-126">Kısa ad</span><span class="sxs-lookup"><span data-stu-id="07c3b-126">Short name</span></span>                      | <span data-ttu-id="07c3b-127">Dil</span><span class="sxs-lookup"><span data-stu-id="07c3b-127">Language</span></span>     | <span data-ttu-id="07c3b-128">Etiketler</span><span class="sxs-lookup"><span data-stu-id="07c3b-128">Tags</span></span>                                  | <span data-ttu-id="07c3b-129">Sunulan özellikler</span><span class="sxs-lookup"><span data-stu-id="07c3b-129">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="07c3b-130">Konsol Uygulaması</span><span class="sxs-lookup"><span data-stu-id="07c3b-130">Console Application</span></span>                          | [<span data-ttu-id="07c3b-131">konsola</span><span class="sxs-lookup"><span data-stu-id="07c3b-131">console</span></span>](#console)             | <span data-ttu-id="07c3b-132">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="07c3b-132">[C#], F#, VB</span></span> | <span data-ttu-id="07c3b-133">Ortak/konsol</span><span class="sxs-lookup"><span data-stu-id="07c3b-133">Common/Console</span></span>                        | <span data-ttu-id="07c3b-134">1,0</span><span class="sxs-lookup"><span data-stu-id="07c3b-134">1.0</span></span>        |
| <span data-ttu-id="07c3b-135">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="07c3b-135">Class library</span></span>                                | [<span data-ttu-id="07c3b-136">projesinin</span><span class="sxs-lookup"><span data-stu-id="07c3b-136">classlib</span></span>](#classlib)           | <span data-ttu-id="07c3b-137">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="07c3b-137">[C#], F#, VB</span></span> | <span data-ttu-id="07c3b-138">Ortak/Kitaplık</span><span class="sxs-lookup"><span data-stu-id="07c3b-138">Common/Library</span></span>                        | <span data-ttu-id="07c3b-139">1,0</span><span class="sxs-lookup"><span data-stu-id="07c3b-139">1.0</span></span>        |
| <span data-ttu-id="07c3b-140">WPF uygulaması</span><span class="sxs-lookup"><span data-stu-id="07c3b-140">WPF Application</span></span>                              | [<span data-ttu-id="07c3b-141">WPF</span><span class="sxs-lookup"><span data-stu-id="07c3b-141">wpf</span></span>](#wpf)                     | <span data-ttu-id="07c3b-142">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="07c3b-142">[C#], VB</span></span>     | <span data-ttu-id="07c3b-143">Ortak/WPF</span><span class="sxs-lookup"><span data-stu-id="07c3b-143">Common/WPF</span></span>                            | <span data-ttu-id="07c3b-144">3,0 (VB için 5,0)</span><span class="sxs-lookup"><span data-stu-id="07c3b-144">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="07c3b-145">WPF sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="07c3b-145">WPF Class library</span></span>                            | [<span data-ttu-id="07c3b-146">wpflib</span><span class="sxs-lookup"><span data-stu-id="07c3b-146">wpflib</span></span>](#wpf)                  | <span data-ttu-id="07c3b-147">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="07c3b-147">[C#], VB</span></span>     | <span data-ttu-id="07c3b-148">Ortak/WPF</span><span class="sxs-lookup"><span data-stu-id="07c3b-148">Common/WPF</span></span>                            | <span data-ttu-id="07c3b-149">3,0 (VB için 5,0)</span><span class="sxs-lookup"><span data-stu-id="07c3b-149">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="07c3b-150">WPF Özel Denetim Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="07c3b-150">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="07c3b-151">wpfcustomcontrollib</span><span class="sxs-lookup"><span data-stu-id="07c3b-151">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="07c3b-152">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="07c3b-152">[C#], VB</span></span>     | <span data-ttu-id="07c3b-153">Ortak/WPF</span><span class="sxs-lookup"><span data-stu-id="07c3b-153">Common/WPF</span></span>                            | <span data-ttu-id="07c3b-154">3,0 (VB için 5,0)</span><span class="sxs-lookup"><span data-stu-id="07c3b-154">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="07c3b-155">WPF Kullanıcı denetimi kitaplığı</span><span class="sxs-lookup"><span data-stu-id="07c3b-155">WPF User Control Library</span></span>                     | [<span data-ttu-id="07c3b-156">wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="07c3b-156">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="07c3b-157">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="07c3b-157">[C#], VB</span></span>     | <span data-ttu-id="07c3b-158">Ortak/WPF</span><span class="sxs-lookup"><span data-stu-id="07c3b-158">Common/WPF</span></span>                            | <span data-ttu-id="07c3b-159">3,0 (VB için 5,0)</span><span class="sxs-lookup"><span data-stu-id="07c3b-159">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="07c3b-160">Windows Forms (WinForms) uygulaması</span><span class="sxs-lookup"><span data-stu-id="07c3b-160">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="07c3b-161">WinForms</span><span class="sxs-lookup"><span data-stu-id="07c3b-161">winforms</span></span>](#winforms)           | <span data-ttu-id="07c3b-162">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="07c3b-162">[C#], VB</span></span>     | <span data-ttu-id="07c3b-163">Ortak/WinForms</span><span class="sxs-lookup"><span data-stu-id="07c3b-163">Common/WinForms</span></span>                       | <span data-ttu-id="07c3b-164">3,0 (VB için 5,0)</span><span class="sxs-lookup"><span data-stu-id="07c3b-164">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="07c3b-165">Windows Forms (WinForms) sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="07c3b-165">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="07c3b-166">winformslib</span><span class="sxs-lookup"><span data-stu-id="07c3b-166">winformslib</span></span>](#winforms)        | <span data-ttu-id="07c3b-167">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="07c3b-167">[C#], VB</span></span>     | <span data-ttu-id="07c3b-168">Ortak/WinForms</span><span class="sxs-lookup"><span data-stu-id="07c3b-168">Common/WinForms</span></span>                       | <span data-ttu-id="07c3b-169">3,0 (VB için 5,0)</span><span class="sxs-lookup"><span data-stu-id="07c3b-169">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="07c3b-170">Çalışan hizmeti</span><span class="sxs-lookup"><span data-stu-id="07c3b-170">Worker Service</span></span>                               | [<span data-ttu-id="07c3b-171">ından</span><span class="sxs-lookup"><span data-stu-id="07c3b-171">worker</span></span>](#web-others)           | <span data-ttu-id="07c3b-172">Þ</span><span class="sxs-lookup"><span data-stu-id="07c3b-172">[C#]</span></span>         | <span data-ttu-id="07c3b-173">Ortak/çalışan/Web</span><span class="sxs-lookup"><span data-stu-id="07c3b-173">Common/Worker/Web</span></span>                     | <span data-ttu-id="07c3b-174">3,0</span><span class="sxs-lookup"><span data-stu-id="07c3b-174">3.0</span></span>        |
| <span data-ttu-id="07c3b-175">Birim testi projesi</span><span class="sxs-lookup"><span data-stu-id="07c3b-175">Unit Test Project</span></span>                            | [<span data-ttu-id="07c3b-176">'i</span><span class="sxs-lookup"><span data-stu-id="07c3b-176">mstest</span></span>](#test)                 | <span data-ttu-id="07c3b-177">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="07c3b-177">[C#], F#, VB</span></span> | <span data-ttu-id="07c3b-178">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="07c3b-178">Test/MSTest</span></span>                           | <span data-ttu-id="07c3b-179">1,0</span><span class="sxs-lookup"><span data-stu-id="07c3b-179">1.0</span></span>        |
| <span data-ttu-id="07c3b-180">NUnit 3 test projesi</span><span class="sxs-lookup"><span data-stu-id="07c3b-180">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="07c3b-181">NUnit</span><span class="sxs-lookup"><span data-stu-id="07c3b-181">nunit</span></span>](#nunit)                 | <span data-ttu-id="07c3b-182">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="07c3b-182">[C#], F#, VB</span></span> | <span data-ttu-id="07c3b-183">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="07c3b-183">Test/NUnit</span></span>                            | <span data-ttu-id="07c3b-184">2.1.400</span><span class="sxs-lookup"><span data-stu-id="07c3b-184">2.1.400</span></span>    |
| <span data-ttu-id="07c3b-185">NUnit 3 test öğesi</span><span class="sxs-lookup"><span data-stu-id="07c3b-185">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="07c3b-186">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="07c3b-186">[C#], F#, VB</span></span> | <span data-ttu-id="07c3b-187">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="07c3b-187">Test/NUnit</span></span>                            | <span data-ttu-id="07c3b-188">2.2</span><span class="sxs-lookup"><span data-stu-id="07c3b-188">2.2</span></span>        |
| <span data-ttu-id="07c3b-189">xUnit test projesi</span><span class="sxs-lookup"><span data-stu-id="07c3b-189">xUnit Test Project</span></span>                           | [<span data-ttu-id="07c3b-190">xUnit</span><span class="sxs-lookup"><span data-stu-id="07c3b-190">xunit</span></span>](#test)                  | <span data-ttu-id="07c3b-191">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="07c3b-191">[C#], F#, VB</span></span> | <span data-ttu-id="07c3b-192">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="07c3b-192">Test/xUnit</span></span>                            | <span data-ttu-id="07c3b-193">1,0</span><span class="sxs-lookup"><span data-stu-id="07c3b-193">1.0</span></span>        |
| <span data-ttu-id="07c3b-194">Razor bileşeni</span><span class="sxs-lookup"><span data-stu-id="07c3b-194">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="07c3b-195">Þ</span><span class="sxs-lookup"><span data-stu-id="07c3b-195">[C#]</span></span>         | <span data-ttu-id="07c3b-196">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="07c3b-196">Web/ASP.NET</span></span>                           | <span data-ttu-id="07c3b-197">3,0</span><span class="sxs-lookup"><span data-stu-id="07c3b-197">3.0</span></span>        |
| <span data-ttu-id="07c3b-198">Razor sayfası</span><span class="sxs-lookup"><span data-stu-id="07c3b-198">Razor Page</span></span>                                   | [<span data-ttu-id="07c3b-199">sayfasında</span><span class="sxs-lookup"><span data-stu-id="07c3b-199">page</span></span>](#page)                   | <span data-ttu-id="07c3b-200">Þ</span><span class="sxs-lookup"><span data-stu-id="07c3b-200">[C#]</span></span>         | <span data-ttu-id="07c3b-201">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="07c3b-201">Web/ASP.NET</span></span>                           | <span data-ttu-id="07c3b-202">2,0</span><span class="sxs-lookup"><span data-stu-id="07c3b-202">2.0</span></span>        |
| <span data-ttu-id="07c3b-203">MVC Viewıtemts</span><span class="sxs-lookup"><span data-stu-id="07c3b-203">MVC ViewImports</span></span>                              | [<span data-ttu-id="07c3b-204">viewıtems 'lar</span><span class="sxs-lookup"><span data-stu-id="07c3b-204">viewimports</span></span>](#namespace)       | <span data-ttu-id="07c3b-205">Þ</span><span class="sxs-lookup"><span data-stu-id="07c3b-205">[C#]</span></span>         | <span data-ttu-id="07c3b-206">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="07c3b-206">Web/ASP.NET</span></span>                           | <span data-ttu-id="07c3b-207">2,0</span><span class="sxs-lookup"><span data-stu-id="07c3b-207">2.0</span></span>        |
| <span data-ttu-id="07c3b-208">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="07c3b-208">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="07c3b-209">Þ</span><span class="sxs-lookup"><span data-stu-id="07c3b-209">[C#]</span></span>         | <span data-ttu-id="07c3b-210">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="07c3b-210">Web/ASP.NET</span></span>                           | <span data-ttu-id="07c3b-211">2,0</span><span class="sxs-lookup"><span data-stu-id="07c3b-211">2.0</span></span>        |
| <span data-ttu-id="07c3b-212">:::no-loc(Blazor)::: Sunucu uygulaması</span><span class="sxs-lookup"><span data-stu-id="07c3b-212">:::no-loc(Blazor)::: Server App</span></span>                            | [<span data-ttu-id="07c3b-213">blazorserver</span><span class="sxs-lookup"><span data-stu-id="07c3b-213">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="07c3b-214">Þ</span><span class="sxs-lookup"><span data-stu-id="07c3b-214">[C#]</span></span>         | <span data-ttu-id="07c3b-215">Web:::no-loc(Blazor):::</span><span class="sxs-lookup"><span data-stu-id="07c3b-215">Web/:::no-loc(Blazor):::</span></span>                            | <span data-ttu-id="07c3b-216">3,0</span><span class="sxs-lookup"><span data-stu-id="07c3b-216">3.0</span></span>        |
| <span data-ttu-id="07c3b-217">:::no-loc(Blazor)::::::no-loc(WebAssembly):::Uygulama</span><span class="sxs-lookup"><span data-stu-id="07c3b-217">:::no-loc(Blazor)::: :::no-loc(WebAssembly)::: App</span></span>                       | [<span data-ttu-id="07c3b-218">blazorwasm</span><span class="sxs-lookup"><span data-stu-id="07c3b-218">blazorwasm</span></span>](#blazorwasm)       | <span data-ttu-id="07c3b-219">Þ</span><span class="sxs-lookup"><span data-stu-id="07c3b-219">[C#]</span></span>         | <span data-ttu-id="07c3b-220">Web:::no-loc(Blazor):::/:::no-loc(WebAssembly):::</span><span class="sxs-lookup"><span data-stu-id="07c3b-220">Web/:::no-loc(Blazor):::/:::no-loc(WebAssembly):::</span></span>                | <span data-ttu-id="07c3b-221">3.1.300</span><span class="sxs-lookup"><span data-stu-id="07c3b-221">3.1.300</span></span>    |
| <span data-ttu-id="07c3b-222">ASP.NET Core boş</span><span class="sxs-lookup"><span data-stu-id="07c3b-222">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="07c3b-223">Web</span><span class="sxs-lookup"><span data-stu-id="07c3b-223">web</span></span>](#web)                     | <span data-ttu-id="07c3b-224">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="07c3b-224">[C#], F#</span></span>     | <span data-ttu-id="07c3b-225">Web/boş</span><span class="sxs-lookup"><span data-stu-id="07c3b-225">Web/Empty</span></span>                             | <span data-ttu-id="07c3b-226">1,0</span><span class="sxs-lookup"><span data-stu-id="07c3b-226">1.0</span></span>        |
| <span data-ttu-id="07c3b-227">ASP.NET Core Web uygulaması (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="07c3b-227">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="07c3b-228">MVC</span><span class="sxs-lookup"><span data-stu-id="07c3b-228">mvc</span></span>](#web-options)             | <span data-ttu-id="07c3b-229">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="07c3b-229">[C#], F#</span></span>     | <span data-ttu-id="07c3b-230">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="07c3b-230">Web/MVC</span></span>                               | <span data-ttu-id="07c3b-231">1,0</span><span class="sxs-lookup"><span data-stu-id="07c3b-231">1.0</span></span>        |
| <span data-ttu-id="07c3b-232">ASP.NET Core Web uygulaması</span><span class="sxs-lookup"><span data-stu-id="07c3b-232">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="07c3b-233">WEBAPP, Razor</span><span class="sxs-lookup"><span data-stu-id="07c3b-233">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="07c3b-234">Þ</span><span class="sxs-lookup"><span data-stu-id="07c3b-234">[C#]</span></span>         | <span data-ttu-id="07c3b-235">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="07c3b-235">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="07c3b-236">2,2, 2,0</span><span class="sxs-lookup"><span data-stu-id="07c3b-236">2.2, 2.0</span></span>   |
| <span data-ttu-id="07c3b-237">Angular ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="07c3b-237">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="07c3b-238">Angular</span><span class="sxs-lookup"><span data-stu-id="07c3b-238">angular</span></span>](#spa)                 | <span data-ttu-id="07c3b-239">Þ</span><span class="sxs-lookup"><span data-stu-id="07c3b-239">[C#]</span></span>         | <span data-ttu-id="07c3b-240">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="07c3b-240">Web/MVC/SPA</span></span>                           | <span data-ttu-id="07c3b-241">2,0</span><span class="sxs-lookup"><span data-stu-id="07c3b-241">2.0</span></span>        |
| <span data-ttu-id="07c3b-242">React.js ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="07c3b-242">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="07c3b-243">tıkla</span><span class="sxs-lookup"><span data-stu-id="07c3b-243">react</span></span>](#spa)                   | <span data-ttu-id="07c3b-244">Þ</span><span class="sxs-lookup"><span data-stu-id="07c3b-244">[C#]</span></span>         | <span data-ttu-id="07c3b-245">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="07c3b-245">Web/MVC/SPA</span></span>                           | <span data-ttu-id="07c3b-246">2,0</span><span class="sxs-lookup"><span data-stu-id="07c3b-246">2.0</span></span>        |
| <span data-ttu-id="07c3b-247">React.js ve Redux ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="07c3b-247">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="07c3b-248">reactredux</span><span class="sxs-lookup"><span data-stu-id="07c3b-248">reactredux</span></span>](#reactredux)       | <span data-ttu-id="07c3b-249">Þ</span><span class="sxs-lookup"><span data-stu-id="07c3b-249">[C#]</span></span>         | <span data-ttu-id="07c3b-250">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="07c3b-250">Web/MVC/SPA</span></span>                           | <span data-ttu-id="07c3b-251">2,0</span><span class="sxs-lookup"><span data-stu-id="07c3b-251">2.0</span></span>        |
| <span data-ttu-id="07c3b-252">Razor sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="07c3b-252">Razor Class Library</span></span>                          | [<span data-ttu-id="07c3b-253">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="07c3b-253">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="07c3b-254">Þ</span><span class="sxs-lookup"><span data-stu-id="07c3b-254">[C#]</span></span>         | <span data-ttu-id="07c3b-255">Web/Razor/kitaplık/Razor sınıfı kitaplığı</span><span class="sxs-lookup"><span data-stu-id="07c3b-255">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="07c3b-256">2.1</span><span class="sxs-lookup"><span data-stu-id="07c3b-256">2.1</span></span>        |
| <span data-ttu-id="07c3b-257">ASP.NET Core Web API'si</span><span class="sxs-lookup"><span data-stu-id="07c3b-257">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="07c3b-258">WebApi</span><span class="sxs-lookup"><span data-stu-id="07c3b-258">webapi</span></span>](#webapi)               | <span data-ttu-id="07c3b-259">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="07c3b-259">[C#], F#</span></span>     | <span data-ttu-id="07c3b-260">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="07c3b-260">Web/WebAPI</span></span>                            | <span data-ttu-id="07c3b-261">1,0</span><span class="sxs-lookup"><span data-stu-id="07c3b-261">1.0</span></span>        |
| <span data-ttu-id="07c3b-262">ASP.NET Core gRPC hizmeti</span><span class="sxs-lookup"><span data-stu-id="07c3b-262">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="07c3b-263">GRPC</span><span class="sxs-lookup"><span data-stu-id="07c3b-263">grpc</span></span>](#web-others)             | <span data-ttu-id="07c3b-264">Þ</span><span class="sxs-lookup"><span data-stu-id="07c3b-264">[C#]</span></span>         | <span data-ttu-id="07c3b-265">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="07c3b-265">Web/gRPC</span></span>                              | <span data-ttu-id="07c3b-266">3,0</span><span class="sxs-lookup"><span data-stu-id="07c3b-266">3.0</span></span>        |
| <span data-ttu-id="07c3b-267">DotNet gitignore dosyası</span><span class="sxs-lookup"><span data-stu-id="07c3b-267">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="07c3b-268">Config</span><span class="sxs-lookup"><span data-stu-id="07c3b-268">Config</span></span>                                | <span data-ttu-id="07c3b-269">3,0</span><span class="sxs-lookup"><span data-stu-id="07c3b-269">3.0</span></span>        |
| <span data-ttu-id="07c3b-270">Dosya üzerinde global.js</span><span class="sxs-lookup"><span data-stu-id="07c3b-270">global.json file</span></span>                             | [<span data-ttu-id="07c3b-271">globaljson</span><span class="sxs-lookup"><span data-stu-id="07c3b-271">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="07c3b-272">Config</span><span class="sxs-lookup"><span data-stu-id="07c3b-272">Config</span></span>                                | <span data-ttu-id="07c3b-273">2,0</span><span class="sxs-lookup"><span data-stu-id="07c3b-273">2.0</span></span>        |
| <span data-ttu-id="07c3b-274">NuGet yapılandırması</span><span class="sxs-lookup"><span data-stu-id="07c3b-274">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="07c3b-275">Config</span><span class="sxs-lookup"><span data-stu-id="07c3b-275">Config</span></span>                                | <span data-ttu-id="07c3b-276">1,0</span><span class="sxs-lookup"><span data-stu-id="07c3b-276">1.0</span></span>        |
| <span data-ttu-id="07c3b-277">DotNet yerel araç bildirim dosyası</span><span class="sxs-lookup"><span data-stu-id="07c3b-277">Dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="07c3b-278">Config</span><span class="sxs-lookup"><span data-stu-id="07c3b-278">Config</span></span>                                | <span data-ttu-id="07c3b-279">3,0</span><span class="sxs-lookup"><span data-stu-id="07c3b-279">3.0</span></span>        |
| <span data-ttu-id="07c3b-280">Web yapılandırması</span><span class="sxs-lookup"><span data-stu-id="07c3b-280">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="07c3b-281">Config</span><span class="sxs-lookup"><span data-stu-id="07c3b-281">Config</span></span>                                | <span data-ttu-id="07c3b-282">1,0</span><span class="sxs-lookup"><span data-stu-id="07c3b-282">1.0</span></span>        |
| <span data-ttu-id="07c3b-283">Çözüm dosyası</span><span class="sxs-lookup"><span data-stu-id="07c3b-283">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="07c3b-284">Çözüm</span><span class="sxs-lookup"><span data-stu-id="07c3b-284">Solution</span></span>                              | <span data-ttu-id="07c3b-285">1,0</span><span class="sxs-lookup"><span data-stu-id="07c3b-285">1.0</span></span>        |
| <span data-ttu-id="07c3b-286">Protokol arabelleği dosyası</span><span class="sxs-lookup"><span data-stu-id="07c3b-286">Protocol Buffer File</span></span>                         | [<span data-ttu-id="07c3b-287">Proto</span><span class="sxs-lookup"><span data-stu-id="07c3b-287">proto</span></span>](#namespace)             |              | <span data-ttu-id="07c3b-288">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="07c3b-288">Web/gRPC</span></span>                              | <span data-ttu-id="07c3b-289">3,0</span><span class="sxs-lookup"><span data-stu-id="07c3b-289">3.0</span></span>        |

## <a name="options"></a><span data-ttu-id="07c3b-290">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="07c3b-290">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="07c3b-291">Bir şablon oluşturulmasına neden olacaksa, verilen komutun çalıştırılması durumunda ne olacağını gösteren bir Özet görüntüler.</span><span class="sxs-lookup"><span data-stu-id="07c3b-291">Displays a summary of what would happen if the given command were run if it would result in a template creation.</span></span> <span data-ttu-id="07c3b-292">.NET Core 2,2 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-292">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="07c3b-293">Var olan dosyaları değiştirebilse bile içeriğin oluşturulmasını zorlar.</span><span class="sxs-lookup"><span data-stu-id="07c3b-293">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="07c3b-294">Seçilen şablon çıkış dizinindeki mevcut dosyaları geçersiz kılacağından bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-294">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="07c3b-295">Komut için yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="07c3b-295">Prints out help for the command.</span></span> <span data-ttu-id="07c3b-296">`dotnet new`Komutun kendisi veya herhangi bir şablon için çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-296">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="07c3b-297">Örneğin, `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="07c3b-297">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="07c3b-298">Veya tarafından belirtilen bir şablon paketini `PATH` kurar `NUGET_ID` .</span><span class="sxs-lookup"><span data-stu-id="07c3b-298">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="07c3b-299">Şablon paketinin bir ön sürümü sürümünü yüklemek istiyorsanız, sürümü biçiminde belirtmeniz gerekir `<package-name>::<package-version>` .</span><span class="sxs-lookup"><span data-stu-id="07c3b-299">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="07c3b-300">Varsayılan olarak, `dotnet new` \* en son kararlı paket sürümünü temsil eden sürüm için geçirir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-300">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="07c3b-301">[Örnekler](#examples) bölümündeki bir örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="07c3b-301">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="07c3b-302">Bu komutu çalıştırdığınızda şablonun bir sürümü zaten yüklüyse, şablon belirtilen sürüme veya sürüm belirtilmemişse en son kararlı sürüme güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-302">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="07c3b-303">Özel şablonlar oluşturma hakkında daha fazla bilgi için bkz. [DotNet New Için özel şablonlar](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="07c3b-303">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="07c3b-304">Belirtilen adı içeren şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="07c3b-304">Lists templates containing the specified name.</span></span> <span data-ttu-id="07c3b-305">Ad belirtilmemişse, tüm şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="07c3b-305">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="07c3b-306">Oluşturulacak şablonun dili.</span><span class="sxs-lookup"><span data-stu-id="07c3b-306">The language of the template to create.</span></span> <span data-ttu-id="07c3b-307">Kabul edilen dil şablona göre değişir (bkz. [arguments](#arguments) bölümünde Varsayılanlar).</span><span class="sxs-lookup"><span data-stu-id="07c3b-307">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="07c3b-308">Bazı şablonlar için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-308">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="07c3b-309">Bazı kabuklar `#` özel bir karakter olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="07c3b-309">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="07c3b-310">Bu durumlarda, dil parametre değerini tırnak içine alın.</span><span class="sxs-lookup"><span data-stu-id="07c3b-310">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="07c3b-311">Örneğin, `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="07c3b-311">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="07c3b-312">Oluşturulan çıkışın adı.</span><span class="sxs-lookup"><span data-stu-id="07c3b-312">The name for the created output.</span></span> <span data-ttu-id="07c3b-313">Ad belirtilmemişse, geçerli dizinin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="07c3b-313">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source <SOURCE>`**

  <span data-ttu-id="07c3b-314">Yüklemesi sırasında kullanılacak bir NuGet kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-314">Specifies a NuGet source to use during install.</span></span> <span data-ttu-id="07c3b-315">.NET Core 2,1 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-315">Available since .NET Core 2.1 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="07c3b-316">Oluşturulan çıkışın yerleştirileceği konum.</span><span class="sxs-lookup"><span data-stu-id="07c3b-316">Location to place the generated output.</span></span> <span data-ttu-id="07c3b-317">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="07c3b-317">The default is the current directory.</span></span>

- **`--type <TYPE>`**

  <span data-ttu-id="07c3b-318">Şablonları kullanılabilir türlerine göre filtreler.</span><span class="sxs-lookup"><span data-stu-id="07c3b-318">Filters templates based on available types.</span></span> <span data-ttu-id="07c3b-319">Önceden tanımlanmış değerler `project` ve ' dir `item` .</span><span class="sxs-lookup"><span data-stu-id="07c3b-319">Predefined values are `project` and `item`.</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="07c3b-320">Veya belirtilen bir şablon paketini kaldırır `PATH` `NUGET_ID` .</span><span class="sxs-lookup"><span data-stu-id="07c3b-320">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="07c3b-321">`<PATH|NUGET_ID>`Değer belirtilmediğinde, yüklü olan tüm şablon paketleri ve bunlarla ilişkili şablonlar görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-321">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="07c3b-322">Belirtirken `NUGET_ID` , sürüm numarasını eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="07c3b-322">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="07c3b-323">Bu seçeneğe bir parametre belirtmezseniz, komut, yüklü şablonları ve bunlarla ilgili ayrıntıları listeler.</span><span class="sxs-lookup"><span data-stu-id="07c3b-323">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="07c3b-324">Bir şablonu kullanarak kaldırmak için `PATH` , yolu tam olarak nitelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-324">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="07c3b-325">Örneğin, *C:/Users/ \<USER> /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* çalışır, ancak içeren klasörden *./GarciaSoftware.ConsoleTemplate.CSharp* olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="07c3b-325">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="07c3b-326">Şablon yolunuzda son Sonlandırıcı Dizin eğik çizgisi eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="07c3b-326">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="07c3b-327">Şu anda yüklü olan şablon paketleri için kullanılabilir güncelleştirmelerin olup olmadığını denetler ve bunları kurar.</span><span class="sxs-lookup"><span data-stu-id="07c3b-327">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="07c3b-328">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-328">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="07c3b-329">Şu anda yüklü olan şablon paketleri için kullanılabilir güncelleştirmeler olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="07c3b-329">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="07c3b-330">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-330">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="07c3b-331">Şablon seçenekleri</span><span class="sxs-lookup"><span data-stu-id="07c3b-331">Template options</span></span>

<span data-ttu-id="07c3b-332">Her proje şablonunda ek seçenekler bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-332">Each project template may have additional options available.</span></span> <span data-ttu-id="07c3b-333">Çekirdek şablonlar aşağıdaki ek seçeneklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="07c3b-333">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="07c3b-334">console</span><span class="sxs-lookup"><span data-stu-id="07c3b-334">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="07c3b-335">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-335">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="07c3b-336">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-336">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="07c3b-337">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="07c3b-337">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="07c3b-338">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="07c3b-338">SDK version</span></span> | <span data-ttu-id="07c3b-339">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="07c3b-339">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="07c3b-340">3,1</span><span class="sxs-lookup"><span data-stu-id="07c3b-340">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="07c3b-341">3,0</span><span class="sxs-lookup"><span data-stu-id="07c3b-341">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="07c3b-342">`LangVersion`Oluşturulan proje dosyasındaki özelliği ayarlar.</span><span class="sxs-lookup"><span data-stu-id="07c3b-342">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="07c3b-343">Örneğin, `--langVersion 7.3` C# 7,3 kullanmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="07c3b-343">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="07c3b-344">F # için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="07c3b-344">Not supported for F#.</span></span> <span data-ttu-id="07c3b-345">.NET Core 2,2 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-345">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="07c3b-346">Varsayılan C# sürümlerinin listesi için bkz. [Varsayılanlar](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="07c3b-346">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="07c3b-347">Belirtilmişse, proje oluşturma sırasında örtük geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="07c3b-347">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="07c3b-348">.NET Core 2,2 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-348">Available since .NET Core 2.2 SDK.</span></span>

<span data-ttu-id="07c3b-349">\*\*_</span><span class="sxs-lookup"><span data-stu-id="07c3b-349">\*\*_</span></span>

### <a name="classlib"></a><span data-ttu-id="07c3b-350">projesinin</span><span class="sxs-lookup"><span data-stu-id="07c3b-350">classlib</span></span>

- <span data-ttu-id="07c3b-351">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="07c3b-351">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="07c3b-352">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-352">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="07c3b-353">Değerler: `netcoreapp<version>` bir .NET Core sınıf kitaplığı oluşturmak veya `netstandard<version>` bir .NET Standard sınıf kitaplığı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="07c3b-353">Values: `netcoreapp<version>` to create a .NET Core Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="07c3b-354">`netstandard2.0` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-354">The default value is `netstandard2.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="07c3b-355">`LangVersion`Oluşturulan proje dosyasındaki özelliği ayarlar.</span><span class="sxs-lookup"><span data-stu-id="07c3b-355">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="07c3b-356">Örneğin, `--langVersion 7.3` C# 7,3 kullanmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="07c3b-356">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="07c3b-357">F # için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="07c3b-357">Not supported for F#.</span></span> <span data-ttu-id="07c3b-358">.NET Core 2,2 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-358">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="07c3b-359">Varsayılan C# sürümlerinin listesi için bkz. [Varsayılanlar](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="07c3b-359">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="07c3b-360">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="07c3b-360">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="07c3b-361">\*\*_</span><span class="sxs-lookup"><span data-stu-id="07c3b-361">\*\*_</span></span>

### <a name="wpf-wpflib-wpfcustomcontrollib-wpfusercontrollib"></a><a name="wpf"></a> <span data-ttu-id="07c3b-362">WPF, wpflib, wpfcustomcontrollib, wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="07c3b-362">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- <span data-ttu-id="07c3b-363">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="07c3b-363">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="07c3b-364">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-364">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="07c3b-365">`netcoreapp3.1` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-365">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="07c3b-366">.NET Core 3,1 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-366">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="07c3b-367">`LangVersion`Oluşturulan proje dosyasındaki özelliği ayarlar.</span><span class="sxs-lookup"><span data-stu-id="07c3b-367">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="07c3b-368">Örneğin, `--langVersion 7.3` C# 7,3 kullanmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="07c3b-368">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="07c3b-369">Varsayılan C# sürümlerinin listesi için bkz. [Varsayılanlar](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="07c3b-369">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="07c3b-370">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="07c3b-370">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="07c3b-371">\*\*_</span><span class="sxs-lookup"><span data-stu-id="07c3b-371">\*\*_</span></span>

### <a name="winforms-winformslib"></a><a name="winforms"></a> <span data-ttu-id="07c3b-372">WinForms, winformslib</span><span class="sxs-lookup"><span data-stu-id="07c3b-372">winforms, winformslib</span></span>

- <span data-ttu-id="07c3b-373">_ *`--langVersion <VERSION_NUMBER>`*\*</span><span class="sxs-lookup"><span data-stu-id="07c3b-373">_ *`--langVersion <VERSION_NUMBER>`*\*</span></span>

  <span data-ttu-id="07c3b-374">`LangVersion`Oluşturulan proje dosyasındaki özelliği ayarlar.</span><span class="sxs-lookup"><span data-stu-id="07c3b-374">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="07c3b-375">Örneğin, `--langVersion 7.3` C# 7,3 kullanmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="07c3b-375">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="07c3b-376">Varsayılan C# sürümlerinin listesi için bkz. [Varsayılanlar](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="07c3b-376">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="07c3b-377">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="07c3b-377">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="07c3b-378">\*\*_</span><span class="sxs-lookup"><span data-stu-id="07c3b-378">\*\*_</span></span>

### <a name="worker-grpc"></a><a name="web-others"></a> <span data-ttu-id="07c3b-379">çalışan, GRPC</span><span class="sxs-lookup"><span data-stu-id="07c3b-379">worker, grpc</span></span>

- <span data-ttu-id="07c3b-380">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="07c3b-380">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="07c3b-381">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-381">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="07c3b-382">`netcoreapp3.1` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-382">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="07c3b-383">.NET Core 3,1 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-383">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="07c3b-384">Oluşturulan şablondan *launchSettings.js* dışlar.</span><span class="sxs-lookup"><span data-stu-id="07c3b-384">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="07c3b-385">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="07c3b-385">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="07c3b-386">\*\*_</span><span class="sxs-lookup"><span data-stu-id="07c3b-386">\*\*_</span></span>

### <a name="mstest-xunit"></a><a name="test"></a> <span data-ttu-id="07c3b-387">MSTest, xUnit</span><span class="sxs-lookup"><span data-stu-id="07c3b-387">mstest, xunit</span></span>

- <span data-ttu-id="07c3b-388">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="07c3b-388">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="07c3b-389">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-389">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="07c3b-390">.NET Core 3,0 SDK 'dan beri kullanılabilir seçeneği.</span><span class="sxs-lookup"><span data-stu-id="07c3b-390">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="07c3b-391">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="07c3b-391">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="07c3b-392">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="07c3b-392">SDK version</span></span> | <span data-ttu-id="07c3b-393">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="07c3b-393">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="07c3b-394">3,1</span><span class="sxs-lookup"><span data-stu-id="07c3b-394">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="07c3b-395">3,0</span><span class="sxs-lookup"><span data-stu-id="07c3b-395">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="07c3b-396">[DotNet Pack](dotnet-pack.md)kullanarak proje için paketleme imkanı sunar.</span><span class="sxs-lookup"><span data-stu-id="07c3b-396">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="07c3b-397">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="07c3b-397">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="07c3b-398">\*\*_</span><span class="sxs-lookup"><span data-stu-id="07c3b-398">\*\*_</span></span>

### <a name="nunit"></a><span data-ttu-id="07c3b-399">NUnit</span><span class="sxs-lookup"><span data-stu-id="07c3b-399">nunit</span></span>

- <span data-ttu-id="07c3b-400">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="07c3b-400">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="07c3b-401">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-401">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="07c3b-402">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="07c3b-402">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="07c3b-403">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="07c3b-403">SDK version</span></span> | <span data-ttu-id="07c3b-404">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="07c3b-404">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="07c3b-405">3,1</span><span class="sxs-lookup"><span data-stu-id="07c3b-405">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="07c3b-406">3,0</span><span class="sxs-lookup"><span data-stu-id="07c3b-406">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="07c3b-407">2.2</span><span class="sxs-lookup"><span data-stu-id="07c3b-407">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="07c3b-408">2.1</span><span class="sxs-lookup"><span data-stu-id="07c3b-408">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="07c3b-409">[DotNet Pack](dotnet-pack.md)kullanarak proje için paketleme imkanı sunar.</span><span class="sxs-lookup"><span data-stu-id="07c3b-409">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="07c3b-410">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="07c3b-410">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="07c3b-411">\*\*_</span><span class="sxs-lookup"><span data-stu-id="07c3b-411">\*\*_</span></span>

### <a name="page"></a><span data-ttu-id="07c3b-412">sayfasında</span><span class="sxs-lookup"><span data-stu-id="07c3b-412">page</span></span>

- <span data-ttu-id="07c3b-413">_ *`-na|--namespace <NAMESPACE_NAME>`*\*</span><span class="sxs-lookup"><span data-stu-id="07c3b-413">_ *`-na|--namespace <NAMESPACE_NAME>`*\*</span></span>

  <span data-ttu-id="07c3b-414">Oluşturulan kod için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="07c3b-414">Namespace for the generated code.</span></span> <span data-ttu-id="07c3b-415">`MyApp.Namespace` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-415">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="07c3b-416">PageModel olmadan sayfayı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="07c3b-416">Creates the page without a PageModel.</span></span>

<span data-ttu-id="07c3b-417">\*\*_</span><span class="sxs-lookup"><span data-stu-id="07c3b-417">\*\*_</span></span>

### <a name="viewimports-proto"></a><a name="namespace"></a> <span data-ttu-id="07c3b-418">viewıtemler, Proto</span><span class="sxs-lookup"><span data-stu-id="07c3b-418">viewimports, proto</span></span>

- <span data-ttu-id="07c3b-419">_ *`-na|--namespace <NAMESPACE_NAME>`*\*</span><span class="sxs-lookup"><span data-stu-id="07c3b-419">_ *`-na|--namespace <NAMESPACE_NAME>`*\*</span></span>

  <span data-ttu-id="07c3b-420">Oluşturulan kod için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="07c3b-420">Namespace for the generated code.</span></span> <span data-ttu-id="07c3b-421">`MyApp.Namespace` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-421">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="07c3b-422">\*\*_</span><span class="sxs-lookup"><span data-stu-id="07c3b-422">\*\*_</span></span>

### <a name="blazorserver"></a><span data-ttu-id="07c3b-423">blazorserver</span><span class="sxs-lookup"><span data-stu-id="07c3b-423">blazorserver</span></span>

- <span data-ttu-id="07c3b-424">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="07c3b-424">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="07c3b-425">Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="07c3b-425">The type of authentication to use.</span></span> <span data-ttu-id="07c3b-426">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="07c3b-426">The possible values are:</span></span>

  - <span data-ttu-id="07c3b-427">`None` -Kimlik doğrulaması yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="07c3b-427">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="07c3b-428">`Individual` -Bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="07c3b-428">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="07c3b-429">`IndividualB2C` -Azure AD B2C ile bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="07c3b-429">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="07c3b-430">`SingleOrg` -Tek bir kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="07c3b-430">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="07c3b-431">`MultiOrg` -Birden çok kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="07c3b-431">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="07c3b-432">`Windows` -Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="07c3b-432">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="07c3b-433">Bağlanılacak Azure Active Directory B2C örneği.</span><span class="sxs-lookup"><span data-stu-id="07c3b-433">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="07c3b-434">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="07c3b-434">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="07c3b-435">`https://login.microsoftonline.com/tfp/` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-435">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="07c3b-436">Bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="07c3b-436">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="07c3b-437">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="07c3b-437">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="07c3b-438">Bu proje için parola sıfırlama ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="07c3b-438">The reset password policy ID for this project.</span></span> <span data-ttu-id="07c3b-439">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="07c3b-439">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="07c3b-440">Bu proje için profil ilke KIMLIĞINI Düzenle.</span><span class="sxs-lookup"><span data-stu-id="07c3b-440">The edit profile policy ID for this project.</span></span> <span data-ttu-id="07c3b-441">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="07c3b-441">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="07c3b-442">Bağlanılacak Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="07c3b-442">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="07c3b-443">`SingleOrg`Veya `MultiOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="07c3b-443">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="07c3b-444">`https://login.microsoftonline.com/` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-444">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="07c3b-445">Bu projenin Istemci KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="07c3b-445">The Client ID for this project.</span></span> <span data-ttu-id="07c3b-446">`IndividualB2C`, `SingleOrg` Veya `MultiOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="07c3b-446">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="07c3b-447">`11111111-1111-1111-11111111111111111` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-447">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="07c3b-448">Dizin kiracının etki alanı.</span><span class="sxs-lookup"><span data-stu-id="07c3b-448">The domain for the directory tenant.</span></span> <span data-ttu-id="07c3b-449">`SingleOrg`Veya `IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="07c3b-449">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="07c3b-450">`qualified.domain.name` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-450">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="07c3b-451">Bağlanılacak dizinin Tenantıd KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="07c3b-451">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="07c3b-452">`SingleOrg`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="07c3b-452">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="07c3b-453">`22222222-2222-2222-2222-222222222222` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-453">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="07c3b-454">Uygulamanın yeniden yönlendirme URI 'sinin temel yolundaki istek yolu.</span><span class="sxs-lookup"><span data-stu-id="07c3b-454">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="07c3b-455">`SingleOrg`Veya `IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="07c3b-455">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="07c3b-456">`/signin-oidc` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-456">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="07c3b-457">Bu uygulamanın dizine okuma erişimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="07c3b-457">Allows this application read-access to the directory.</span></span> <span data-ttu-id="07c3b-458">Yalnızca `SingleOrg` veya `MultiOrg` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-458">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="07c3b-459">Oluşturulan şablondan *launchSettings.js* dışlar.</span><span class="sxs-lookup"><span data-stu-id="07c3b-459">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="07c3b-460">HTTPS 'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="07c3b-460">Turns off HTTPS.</span></span> <span data-ttu-id="07c3b-461">Bu seçenek yalnızca,, `Individual` , `IndividualB2C` `SingleOrg` veya için kullanılmıyorsa geçerlidir `MultiOrg` `--auth` .</span><span class="sxs-lookup"><span data-stu-id="07c3b-461">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="07c3b-462">SQLite yerine LocalDB kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-462">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="07c3b-463">Yalnızca `Individual` veya `IndividualB2C` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-463">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="07c3b-464">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="07c3b-464">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="07c3b-465">\*\*_</span><span class="sxs-lookup"><span data-stu-id="07c3b-465">\*\*_</span></span>

### <a name="blazorwasm"></a><span data-ttu-id="07c3b-466">blazorwasm</span><span class="sxs-lookup"><span data-stu-id="07c3b-466">blazorwasm</span></span>

- <span data-ttu-id="07c3b-467">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="07c3b-467">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="07c3b-468">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-468">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="07c3b-469">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="07c3b-469">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="07c3b-470">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="07c3b-470">SDK version</span></span> | <span data-ttu-id="07c3b-471">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="07c3b-471">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="07c3b-472">5.0</span><span class="sxs-lookup"><span data-stu-id="07c3b-472">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="07c3b-473">3,1</span><span class="sxs-lookup"><span data-stu-id="07c3b-473">3.1</span></span>         | `netcoreapp3.1` |

- **`--no-restore`**

  <span data-ttu-id="07c3b-474">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="07c3b-474">Doesn't execute an implicit restore during project creation.</span></span>

- **`-ho|--hosted`**

  <span data-ttu-id="07c3b-475">Uygulama için bir ASP.NET Core Konağı içerir :::no-loc(Blazor)::: :::no-loc(WebAssembly)::: .</span><span class="sxs-lookup"><span data-stu-id="07c3b-475">Includes an ASP.NET Core host for the :::no-loc(Blazor)::: :::no-loc(WebAssembly)::: app.</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="07c3b-476">Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="07c3b-476">The type of authentication to use.</span></span> <span data-ttu-id="07c3b-477">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="07c3b-477">The possible values are:</span></span>

  - <span data-ttu-id="07c3b-478">`None` -Kimlik doğrulaması yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="07c3b-478">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="07c3b-479">`Individual` -Bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="07c3b-479">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="07c3b-480">`IndividualB2C` -Azure AD B2C ile bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="07c3b-480">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="07c3b-481">`SingleOrg` -Tek bir kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="07c3b-481">`SingleOrg` - Organizational authentication for a single tenant.</span></span>

- **`--authority <AUTHORITY>`**

  <span data-ttu-id="07c3b-482">OıDC sağlayıcısı yetkilisi.</span><span class="sxs-lookup"><span data-stu-id="07c3b-482">The authority of the OIDC provider.</span></span> <span data-ttu-id="07c3b-483">`Individual`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="07c3b-483">Use with `Individual` authentication.</span></span> <span data-ttu-id="07c3b-484">`https://login.microsoftonline.com/` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-484">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="07c3b-485">Bağlanılacak Azure Active Directory B2C örneği.</span><span class="sxs-lookup"><span data-stu-id="07c3b-485">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="07c3b-486">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="07c3b-486">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="07c3b-487">`https://aadB2CInstance.b2clogin.com/` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-487">The default value is `https://aadB2CInstance.b2clogin.com/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="07c3b-488">Bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="07c3b-488">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="07c3b-489">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="07c3b-489">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="07c3b-490">Bağlanılacak Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="07c3b-490">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="07c3b-491">`SingleOrg`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="07c3b-491">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="07c3b-492">`https://login.microsoftonline.com/` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-492">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="07c3b-493">Bu projenin Istemci KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="07c3b-493">The Client ID for this project.</span></span> <span data-ttu-id="07c3b-494">`IndividualB2C` `SingleOrg` `Individual` Tek başına senaryolarda, veya ile kimlik doğrulaması kullanın.</span><span class="sxs-lookup"><span data-stu-id="07c3b-494">Use with `IndividualB2C`, `SingleOrg`, or `Individual` authentication in standalone scenarios.</span></span> <span data-ttu-id="07c3b-495">`33333333-3333-3333-33333333333333333` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-495">The default value is `33333333-3333-3333-33333333333333333`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="07c3b-496">Dizin kiracının etki alanı.</span><span class="sxs-lookup"><span data-stu-id="07c3b-496">The domain for the directory tenant.</span></span> <span data-ttu-id="07c3b-497">`SingleOrg`Veya `IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="07c3b-497">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="07c3b-498">`qualified.domain.name` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-498">The default value is `qualified.domain.name`.</span></span>

- **`--app-id-uri <URI>`**

  <span data-ttu-id="07c3b-499">Çağırmak istediğiniz sunucu API 'SI için uygulama KIMLIĞI URI 'Si.</span><span class="sxs-lookup"><span data-stu-id="07c3b-499">The App ID Uri for the server API you want to call.</span></span> <span data-ttu-id="07c3b-500">`SingleOrg`Veya `IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="07c3b-500">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="07c3b-501">`api.id.uri` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-501">The default value is `api.id.uri`.</span></span>

- **`--api-client-id <ID>`**

  <span data-ttu-id="07c3b-502">Sunucunun barındırdığı API 'nin Istemci KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="07c3b-502">The Client ID for the API that the server hosts.</span></span> <span data-ttu-id="07c3b-503">`SingleOrg`Veya `IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="07c3b-503">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="07c3b-504">`11111111-1111-1111-11111111111111111` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-504">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`-s|--default-scope <SCOPE>`**

  <span data-ttu-id="07c3b-505">İstemcinin bir erişim belirteci sağlamasını istemesi gereken API kapsamı.</span><span class="sxs-lookup"><span data-stu-id="07c3b-505">The API scope the client needs to request to provision an access token.</span></span> <span data-ttu-id="07c3b-506">`SingleOrg`Veya `IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="07c3b-506">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="07c3b-507">`user_impersonation` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-507">The default value is `user_impersonation`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="07c3b-508">Bağlanılacak dizinin Tenantıd KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="07c3b-508">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="07c3b-509">`SingleOrg`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="07c3b-509">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="07c3b-510">`22222222-2222-2222-2222-222222222222` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-510">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="07c3b-511">Bu uygulamanın dizine okuma erişimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="07c3b-511">Allows this application read-access to the directory.</span></span> <span data-ttu-id="07c3b-512">Yalnızca `SingleOrg` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-512">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="07c3b-513">Oluşturulan şablondan *launchSettings.js* dışlar.</span><span class="sxs-lookup"><span data-stu-id="07c3b-513">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-p|--pwa`**

  <span data-ttu-id="07c3b-514">yüklemeyi ve çevrimdışı kullanımı destekleyen bir aşamalı Web uygulaması (PWA) üretir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-514">produces a Progressive Web Application (PWA) supporting installation and offline use.</span></span>

- **`--no-https`**

  <span data-ttu-id="07c3b-515">HTTPS 'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="07c3b-515">Turns off HTTPS.</span></span> <span data-ttu-id="07c3b-516">Bu seçenek yalnızca,, `Individual` `IndividualB2C` veya için kullanılmıyorsa geçerlidir `SingleOrg` `--auth` .</span><span class="sxs-lookup"><span data-stu-id="07c3b-516">This option only applies if `Individual`, `IndividualB2C`, or `SingleOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="07c3b-517">SQLite yerine LocalDB kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-517">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="07c3b-518">Yalnızca `Individual` veya `IndividualB2C` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-518">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--called-api-url <URL>`**

  <span data-ttu-id="07c3b-519">Web uygulamasından çağrılacak API 'nin URL 'SI.</span><span class="sxs-lookup"><span data-stu-id="07c3b-519">URL of the API to call from the web app.</span></span> <span data-ttu-id="07c3b-520">Yalnızca `SingleOrg` `IndividualB2C` ASP.NET Core bir ana bilgisayar olmadan veya kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-520">Only applies to `SingleOrg` or `IndividualB2C` authentication without an ASP.NET Core host specified.</span></span> <span data-ttu-id="07c3b-521">`https://graph.microsoft.com/v1.0/me` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-521">The default value is `https://graph.microsoft.com/v1.0/me`.</span></span>

- **`--calls-graph`**

  <span data-ttu-id="07c3b-522">Web uygulamasının Microsoft Graph çağırıyorsa belirtir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-522">Specifies if the web app calls Microsoft Graph.</span></span> <span data-ttu-id="07c3b-523">Yalnızca `SingleOrg` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-523">Only applies to `SingleOrg` authentication.</span></span>

- **`--called-api-scopes <SCOPES>`**

  <span data-ttu-id="07c3b-524">Web uygulamasından API 'yi çağırmak için istenen kapsamlar.</span><span class="sxs-lookup"><span data-stu-id="07c3b-524">Scopes to request to call the API from the web app.</span></span> <span data-ttu-id="07c3b-525">Yalnızca `SingleOrg` `IndividualB2C` ASP.NET Core bir ana bilgisayar olmadan veya kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-525">Only applies to `SingleOrg` or `IndividualB2C` authentication without an ASP.NET Core host specified.</span></span> <span data-ttu-id="07c3b-526">Varsayılan değer: `user.read`.</span><span class="sxs-lookup"><span data-stu-id="07c3b-526">The default is `user.read`.</span></span>

<span data-ttu-id="07c3b-527">\*\*_</span><span class="sxs-lookup"><span data-stu-id="07c3b-527">\*\*_</span></span>

### <a name="web"></a><span data-ttu-id="07c3b-528">web</span><span class="sxs-lookup"><span data-stu-id="07c3b-528">web</span></span>

- <span data-ttu-id="07c3b-529">_ *`--exclude-launch-settings`*\*</span><span class="sxs-lookup"><span data-stu-id="07c3b-529">_ *`--exclude-launch-settings`*\*</span></span>

  <span data-ttu-id="07c3b-530">Oluşturulan şablondan *launchSettings.js* dışlar.</span><span class="sxs-lookup"><span data-stu-id="07c3b-530">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="07c3b-531">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-531">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="07c3b-532">Seçenek .NET Core 2,2 SDK sürümünde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="07c3b-532">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="07c3b-533">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="07c3b-533">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="07c3b-534">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="07c3b-534">SDK version</span></span> | <span data-ttu-id="07c3b-535">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="07c3b-535">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="07c3b-536">3,1</span><span class="sxs-lookup"><span data-stu-id="07c3b-536">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="07c3b-537">3,0</span><span class="sxs-lookup"><span data-stu-id="07c3b-537">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="07c3b-538">2.1</span><span class="sxs-lookup"><span data-stu-id="07c3b-538">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="07c3b-539">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="07c3b-539">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="07c3b-540">HTTPS 'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="07c3b-540">Turns off HTTPS.</span></span>

<span data-ttu-id="07c3b-541">\*\*_</span><span class="sxs-lookup"><span data-stu-id="07c3b-541">\*\*_</span></span>

### <a name="mvc-webapp"></a><a name="web-options"></a> <span data-ttu-id="07c3b-542">MVC, WebApp</span><span class="sxs-lookup"><span data-stu-id="07c3b-542">mvc, webapp</span></span>

- <span data-ttu-id="07c3b-543">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="07c3b-543">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="07c3b-544">Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="07c3b-544">The type of authentication to use.</span></span> <span data-ttu-id="07c3b-545">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="07c3b-545">The possible values are:</span></span>

  - <span data-ttu-id="07c3b-546">`None` -Kimlik doğrulaması yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="07c3b-546">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="07c3b-547">`Individual` -Bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="07c3b-547">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="07c3b-548">`IndividualB2C` -Azure AD B2C ile bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="07c3b-548">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="07c3b-549">`SingleOrg` -Tek bir kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="07c3b-549">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="07c3b-550">`MultiOrg` -Birden çok kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="07c3b-550">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="07c3b-551">`Windows` -Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="07c3b-551">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="07c3b-552">Bağlanılacak Azure Active Directory B2C örneği.</span><span class="sxs-lookup"><span data-stu-id="07c3b-552">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="07c3b-553">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="07c3b-553">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="07c3b-554">`https://login.microsoftonline.com/tfp/` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-554">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="07c3b-555">Bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="07c3b-555">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="07c3b-556">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="07c3b-556">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="07c3b-557">Bu proje için parola sıfırlama ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="07c3b-557">The reset password policy ID for this project.</span></span> <span data-ttu-id="07c3b-558">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="07c3b-558">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="07c3b-559">Bu proje için profil ilke KIMLIĞINI Düzenle.</span><span class="sxs-lookup"><span data-stu-id="07c3b-559">The edit profile policy ID for this project.</span></span> <span data-ttu-id="07c3b-560">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="07c3b-560">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="07c3b-561">Bağlanılacak Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="07c3b-561">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="07c3b-562">`SingleOrg`Veya `MultiOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="07c3b-562">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="07c3b-563">`https://login.microsoftonline.com/` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-563">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="07c3b-564">Bu projenin Istemci KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="07c3b-564">The Client ID for this project.</span></span> <span data-ttu-id="07c3b-565">`IndividualB2C`, `SingleOrg` Veya `MultiOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="07c3b-565">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="07c3b-566">`11111111-1111-1111-11111111111111111` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-566">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="07c3b-567">Dizin kiracının etki alanı.</span><span class="sxs-lookup"><span data-stu-id="07c3b-567">The domain for the directory tenant.</span></span> <span data-ttu-id="07c3b-568">`SingleOrg`Veya `IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="07c3b-568">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="07c3b-569">`qualified.domain.name` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-569">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="07c3b-570">Bağlanılacak dizinin Tenantıd KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="07c3b-570">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="07c3b-571">`SingleOrg`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="07c3b-571">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="07c3b-572">`22222222-2222-2222-2222-222222222222` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-572">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="07c3b-573">Uygulamanın yeniden yönlendirme URI 'sinin temel yolundaki istek yolu.</span><span class="sxs-lookup"><span data-stu-id="07c3b-573">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="07c3b-574">`SingleOrg`Veya `IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="07c3b-574">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="07c3b-575">`/signin-oidc` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-575">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="07c3b-576">Bu uygulamanın dizine okuma erişimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="07c3b-576">Allows this application read-access to the directory.</span></span> <span data-ttu-id="07c3b-577">Yalnızca `SingleOrg` veya `MultiOrg` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-577">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="07c3b-578">Oluşturulan şablondan *launchSettings.js* dışlar.</span><span class="sxs-lookup"><span data-stu-id="07c3b-578">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="07c3b-579">HTTPS 'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="07c3b-579">Turns off HTTPS.</span></span> <span data-ttu-id="07c3b-580">Bu seçenek yalnızca,,, veya kullanılmıyorsa geçerlidir `Individual` `IndividualB2C` `SingleOrg` `MultiOrg` .</span><span class="sxs-lookup"><span data-stu-id="07c3b-580">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="07c3b-581">SQLite yerine LocalDB kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-581">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="07c3b-582">Yalnızca `Individual` veya `IndividualB2C` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-582">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="07c3b-583">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-583">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="07c3b-584">.NET Core 3,0 SDK 'dan beri kullanılabilir seçeneği.</span><span class="sxs-lookup"><span data-stu-id="07c3b-584">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="07c3b-585">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="07c3b-585">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="07c3b-586">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="07c3b-586">SDK version</span></span> | <span data-ttu-id="07c3b-587">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="07c3b-587">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="07c3b-588">3,1</span><span class="sxs-lookup"><span data-stu-id="07c3b-588">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="07c3b-589">3,0</span><span class="sxs-lookup"><span data-stu-id="07c3b-589">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="07c3b-590">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="07c3b-590">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="07c3b-591">Projedeki BrowserLink öğesini içerir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-591">Includes BrowserLink in the project.</span></span> <span data-ttu-id="07c3b-592">Seçenek .NET Core 2,2 ve 3,1 SDK sürümünde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="07c3b-592">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

- **`-rrc|--razor-runtime-compilation`**

  <span data-ttu-id="07c3b-593">Projenin hata ayıklama yapılarında [Razor çalışma zamanı derlemesini](/aspnet/core/mvc/views/view-compilation#runtime-compilation) kullanmak üzere yapılandırılıp yapılandırılmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="07c3b-593">Determines if the project is configured to use [Razor runtime compilation](/aspnet/core/mvc/views/view-compilation#runtime-compilation) in Debug builds.</span></span> <span data-ttu-id="07c3b-594">.NET Core 3.1.201 SDK 'dan beri kullanılabilir seçeneği.</span><span class="sxs-lookup"><span data-stu-id="07c3b-594">Option available since .NET Core 3.1.201 SDK.</span></span>

<span data-ttu-id="07c3b-595">\*\*_</span><span class="sxs-lookup"><span data-stu-id="07c3b-595">\*\*_</span></span>

### <a name="angular-react"></a><a name="spa"></a> <span data-ttu-id="07c3b-596">Angular, tepki verme</span><span class="sxs-lookup"><span data-stu-id="07c3b-596">angular, react</span></span>

- <span data-ttu-id="07c3b-597">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="07c3b-597">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="07c3b-598">Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="07c3b-598">The type of authentication to use.</span></span> <span data-ttu-id="07c3b-599">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-599">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="07c3b-600">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="07c3b-600">The possible values are:</span></span>

  - <span data-ttu-id="07c3b-601">`None` -Kimlik doğrulaması yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="07c3b-601">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="07c3b-602">`Individual` -Bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="07c3b-602">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="07c3b-603">Oluşturulan şablondan *launchSettings.js* dışlar.</span><span class="sxs-lookup"><span data-stu-id="07c3b-603">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="07c3b-604">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="07c3b-604">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="07c3b-605">HTTPS 'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="07c3b-605">Turns off HTTPS.</span></span> <span data-ttu-id="07c3b-606">Bu seçenek yalnızca kimlik doğrulaması ise geçerlidir `None` .</span><span class="sxs-lookup"><span data-stu-id="07c3b-606">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="07c3b-607">SQLite yerine LocalDB kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-607">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="07c3b-608">Yalnızca `Individual` veya `IndividualB2C` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-608">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="07c3b-609">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-609">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="07c3b-610">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-610">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="07c3b-611">Seçenek .NET Core 2,2 SDK sürümünde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="07c3b-611">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="07c3b-612">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="07c3b-612">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="07c3b-613">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="07c3b-613">SDK version</span></span> | <span data-ttu-id="07c3b-614">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="07c3b-614">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="07c3b-615">3,1</span><span class="sxs-lookup"><span data-stu-id="07c3b-615">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="07c3b-616">3,0</span><span class="sxs-lookup"><span data-stu-id="07c3b-616">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="07c3b-617">2.1</span><span class="sxs-lookup"><span data-stu-id="07c3b-617">2.1</span></span>         | `netcoreapp2.0` |

<span data-ttu-id="07c3b-618">\*\*_</span><span class="sxs-lookup"><span data-stu-id="07c3b-618">\*\*_</span></span>

### <a name="reactredux"></a><span data-ttu-id="07c3b-619">reactredux</span><span class="sxs-lookup"><span data-stu-id="07c3b-619">reactredux</span></span>

- <span data-ttu-id="07c3b-620">_ *`--exclude-launch-settings`*\*</span><span class="sxs-lookup"><span data-stu-id="07c3b-620">_ *`--exclude-launch-settings`*\*</span></span>

  <span data-ttu-id="07c3b-621">Oluşturulan şablondan *launchSettings.js* dışlar.</span><span class="sxs-lookup"><span data-stu-id="07c3b-621">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="07c3b-622">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-622">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="07c3b-623">Seçenek .NET Core 2,2 SDK sürümünde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="07c3b-623">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="07c3b-624">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="07c3b-624">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="07c3b-625">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="07c3b-625">SDK version</span></span> | <span data-ttu-id="07c3b-626">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="07c3b-626">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="07c3b-627">3,1</span><span class="sxs-lookup"><span data-stu-id="07c3b-627">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="07c3b-628">3,0</span><span class="sxs-lookup"><span data-stu-id="07c3b-628">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="07c3b-629">2.1</span><span class="sxs-lookup"><span data-stu-id="07c3b-629">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="07c3b-630">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="07c3b-630">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="07c3b-631">HTTPS 'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="07c3b-631">Turns off HTTPS.</span></span>

<span data-ttu-id="07c3b-632">\*\*_</span><span class="sxs-lookup"><span data-stu-id="07c3b-632">\*\*_</span></span>

### <a name="razorclasslib"></a><span data-ttu-id="07c3b-633">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="07c3b-633">razorclasslib</span></span>

- <span data-ttu-id="07c3b-634">_ *`--no-restore`*\*</span><span class="sxs-lookup"><span data-stu-id="07c3b-634">_ *`--no-restore`*\*</span></span>

  <span data-ttu-id="07c3b-635">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="07c3b-635">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="07c3b-636">, Bu kitaplığa bileşenlere ek olarak geleneksel Razor sayfaları ve görünümleri eklenmesini destekler.</span><span class="sxs-lookup"><span data-stu-id="07c3b-636">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="07c3b-637">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-637">Available since .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="07c3b-638">\*\*_</span><span class="sxs-lookup"><span data-stu-id="07c3b-638">\*\*_</span></span>
  
### <a name="webapi"></a><span data-ttu-id="07c3b-639">WebApi</span><span class="sxs-lookup"><span data-stu-id="07c3b-639">webapi</span></span>

- <span data-ttu-id="07c3b-640">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="07c3b-640">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="07c3b-641">Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="07c3b-641">The type of authentication to use.</span></span> <span data-ttu-id="07c3b-642">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="07c3b-642">The possible values are:</span></span>

  - <span data-ttu-id="07c3b-643">`None` -Kimlik doğrulaması yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="07c3b-643">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="07c3b-644">`IndividualB2C` -Azure AD B2C ile bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="07c3b-644">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="07c3b-645">`SingleOrg` -Tek bir kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="07c3b-645">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="07c3b-646">`Windows` -Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="07c3b-646">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="07c3b-647">Bağlanılacak Azure Active Directory B2C örneği.</span><span class="sxs-lookup"><span data-stu-id="07c3b-647">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="07c3b-648">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="07c3b-648">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="07c3b-649">`https://login.microsoftonline.com/tfp/` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-649">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="07c3b-650">Bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="07c3b-650">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="07c3b-651">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="07c3b-651">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="07c3b-652">Bağlanılacak Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="07c3b-652">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="07c3b-653">`SingleOrg`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="07c3b-653">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="07c3b-654">`https://login.microsoftonline.com/` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-654">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="07c3b-655">Bu projenin Istemci KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="07c3b-655">The Client ID for this project.</span></span> <span data-ttu-id="07c3b-656">`IndividualB2C`Veya `SingleOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="07c3b-656">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="07c3b-657">`11111111-1111-1111-11111111111111111` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-657">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="07c3b-658">Dizin kiracının etki alanı.</span><span class="sxs-lookup"><span data-stu-id="07c3b-658">The domain for the directory tenant.</span></span> <span data-ttu-id="07c3b-659">`IndividualB2C`Veya `SingleOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="07c3b-659">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="07c3b-660">`qualified.domain.name` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-660">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="07c3b-661">Bağlanılacak dizinin Tenantıd KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="07c3b-661">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="07c3b-662">`SingleOrg`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="07c3b-662">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="07c3b-663">`22222222-2222-2222-2222-222222222222` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-663">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="07c3b-664">Bu uygulamanın dizine okuma erişimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="07c3b-664">Allows this application read-access to the directory.</span></span> <span data-ttu-id="07c3b-665">Yalnızca `SingleOrg` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-665">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="07c3b-666">Oluşturulan şablondan *launchSettings.js* dışlar.</span><span class="sxs-lookup"><span data-stu-id="07c3b-666">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="07c3b-667">HTTPS 'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="07c3b-667">Turns off HTTPS.</span></span> <span data-ttu-id="07c3b-668">`app.UseHsts` ve `app.UseHttpsRedirection` öğesine eklenmez `Startup.Configure` .</span><span class="sxs-lookup"><span data-stu-id="07c3b-668">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="07c3b-669">Bu seçenek yalnızca `IndividualB2C` `SingleOrg` kimlik doğrulaması için kullanılmıyorsa geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-669">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="07c3b-670">SQLite yerine LocalDB kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-670">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="07c3b-671">Yalnızca `IndividualB2C` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-671">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="07c3b-672">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-672">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="07c3b-673">Seçenek .NET Core 2,2 SDK sürümünde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="07c3b-673">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="07c3b-674">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="07c3b-674">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="07c3b-675">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="07c3b-675">SDK version</span></span> | <span data-ttu-id="07c3b-676">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="07c3b-676">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="07c3b-677">3,1</span><span class="sxs-lookup"><span data-stu-id="07c3b-677">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="07c3b-678">3,0</span><span class="sxs-lookup"><span data-stu-id="07c3b-678">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="07c3b-679">2.1</span><span class="sxs-lookup"><span data-stu-id="07c3b-679">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="07c3b-680">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="07c3b-680">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="07c3b-681">\*\*_</span><span class="sxs-lookup"><span data-stu-id="07c3b-681">\*\*_</span></span>

### <a name="globaljson"></a><span data-ttu-id="07c3b-682">globaljson</span><span class="sxs-lookup"><span data-stu-id="07c3b-682">globaljson</span></span>

- <span data-ttu-id="07c3b-683">_ *`--sdk-version <VERSION_NUMBER>`*\*</span><span class="sxs-lookup"><span data-stu-id="07c3b-683">_ *`--sdk-version <VERSION_NUMBER>`*\*</span></span>

  <span data-ttu-id="07c3b-684">*global.json* dosyasında kullanılacak .NET Core SDK sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="07c3b-684">Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="07c3b-685">Örnekler</span><span class="sxs-lookup"><span data-stu-id="07c3b-685">Examples</span></span>

- <span data-ttu-id="07c3b-686">Şablon adını belirterek bir C# konsol uygulaması projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="07c3b-686">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="07c3b-687">Geçerli dizinde bir F # konsol uygulaması projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="07c3b-687">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang "F#"
  ```

- <span data-ttu-id="07c3b-688">Belirtilen dizinde bir .NET Standard sınıf kitaplığı projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="07c3b-688">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="07c3b-689">Geçerli dizinde kimlik doğrulaması olmadan yeni bir ASP.NET Core C# MVC projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="07c3b-689">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="07c3b-690">Yeni bir xUnit projesi oluştur:</span><span class="sxs-lookup"><span data-stu-id="07c3b-690">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="07c3b-691">Tek sayfalı uygulama (SPA) şablonları için kullanılabilen tüm şablonları listeleyin:</span><span class="sxs-lookup"><span data-stu-id="07c3b-691">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="07c3b-692">*We* alt dizeniz ile eşleşen tüm şablonları listeleyin.</span><span class="sxs-lookup"><span data-stu-id="07c3b-692">List all templates matching the *we* substring.</span></span> <span data-ttu-id="07c3b-693">Tam eşleşme bulunamadı, bu nedenle alt dize eşleştirmesi hem kısa ad hem de ad sütunlarında çalışır.</span><span class="sxs-lookup"><span data-stu-id="07c3b-693">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="07c3b-694">Şablonla *eşleşen şablonu* çağırma girişimi.</span><span class="sxs-lookup"><span data-stu-id="07c3b-694">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="07c3b-695">Tek bir eşleşme belirlenemiyorsa kısmi eşleşen şablonları listeleyin.</span><span class="sxs-lookup"><span data-stu-id="07c3b-695">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="07c3b-696">ASP.NET Core için SPA şablonlarının 2,0 sürümünü yükler:</span><span class="sxs-lookup"><span data-stu-id="07c3b-696">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="07c3b-697">Yüklü şablonları ve bunlarla ilgili ayrıntıları, bunları kaldırma dahil olmak üzere listeleyin:</span><span class="sxs-lookup"><span data-stu-id="07c3b-697">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="07c3b-698">SDK sürümünü 3.1.101 olarak ayarlamak için geçerli dizinde bir *global.js* oluşturun:</span><span class="sxs-lookup"><span data-stu-id="07c3b-698">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="07c3b-699">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07c3b-699">See also</span></span>

- [<span data-ttu-id="07c3b-700">DotNet New için özel şablonlar</span><span class="sxs-lookup"><span data-stu-id="07c3b-700">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="07c3b-701">Dotnet new için özel şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="07c3b-701">Create a custom template for dotnet new</span></span>](../tutorials/cli-templates-create-item-template.md)
- [<span data-ttu-id="07c3b-702">DotNet/DotNet-şablon-örnek GitHub deposu</span><span class="sxs-lookup"><span data-stu-id="07c3b-702">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="07c3b-703">DotNet New için kullanılabilir şablonlar</span><span class="sxs-lookup"><span data-stu-id="07c3b-703">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
