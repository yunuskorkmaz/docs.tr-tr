---
title: DotNet yeni komut
description: DotNet New komutu, belirtilen şablona göre yeni .NET Core projeleri oluşturur.
no-loc:
- Blazor
- WebAssembly
ms.date: 09/01/2020
ms.openlocfilehash: 70297cfe15732716b9ceacae091abe3c8957fb61
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89495479"
---
# <a name="dotnet-new"></a><span data-ttu-id="d2f4c-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="d2f4c-103">dotnet new</span></span>

<span data-ttu-id="d2f4c-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,0 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="d2f4c-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="d2f4c-105">Name</span><span class="sxs-lookup"><span data-stu-id="d2f4c-105">Name</span></span>

<span data-ttu-id="d2f4c-106">`dotnet new` -Belirtilen şablonu temel alan yeni bir proje, yapılandırma dosyası veya çözüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d2f4c-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="d2f4c-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install {PATH|NUGET_ID}]
    [-lang|--language {"C#"|"F#"|VB}] [-n|--name <OUTPUT_NAME>]
    [--nuget-source <SOURCE>] [-o|--output <OUTPUT_DIRECTORY>]
    [-u|--uninstall] [--update-apply] [--update-check] [Template options]

dotnet new <TEMPLATE> [-l|--list] [--type <TYPE>]

dotnet new -h|--help
```

## <a name="description"></a><span data-ttu-id="d2f4c-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d2f4c-108">Description</span></span>

<span data-ttu-id="d2f4c-109">`dotnet new`Komut bir şablonu temel alan bir .NET Core projesi veya diğer yapılar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-109">The `dotnet new` command creates a .NET Core project or other artifacts based on a template.</span></span>

<span data-ttu-id="d2f4c-110">Komutu, belirtilen şablon ve seçeneklere göre diskteki yapıtları oluşturmak için [şablon altyapısını](https://github.com/dotnet/templating) çağırır.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="d2f4c-111">Örtük geri yükleme</span><span class="sxs-lookup"><span data-stu-id="d2f4c-111">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="d2f4c-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="d2f4c-112">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="d2f4c-113">Komut çağrıldığında örnek oluşturulacak şablon.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-113">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="d2f4c-114">Her şablonun geçirebilmeniz için özel seçenekleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-114">Each template might have specific options you can pass.</span></span> <span data-ttu-id="d2f4c-115">Daha fazla bilgi için bkz. [şablon seçenekleri](#template-options).</span><span class="sxs-lookup"><span data-stu-id="d2f4c-115">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="d2f4c-116">`dotnet new --list` `dotnet new -l` Tüm yüklü şablonların listesini görmek için veya çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-116">You can run `dotnet new --list` or `dotnet new -l` to see a list of all installed templates.</span></span> <span data-ttu-id="d2f4c-117">Değer, `TEMPLATE` döndürülen tablodaki **Şablonlar** veya **kısa ad** sütunundaki metinde tam eşleşme değilse, bu iki sütunda bir alt dize eşleşmesi gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-117">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="d2f4c-118">.NET Core 3,0 SDK ile başlayarak, aşağıdaki koşullarda komutu çağırdığınızda CLı NuGet.org içindeki şablonları arar `dotnet new` :</span><span class="sxs-lookup"><span data-stu-id="d2f4c-118">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="d2f4c-119">CLı çağrılırken bir şablon eşleşmesi bulamazsa `dotnet new` , bu da kısmi değildir.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-119">If the CLI can't find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="d2f4c-120">Şablonun daha yeni bir sürümü kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-120">If there's a newer version of the template available.</span></span> <span data-ttu-id="d2f4c-121">Bu durumda, proje veya yapıt oluşturulur ancak CLı, şablonun güncelleştirilmiş bir sürümü hakkında sizi uyarır.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-121">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="d2f4c-122">Aşağıdaki tabloda, .NET Core SDK ile önceden yüklenmiş olan şablonlar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-122">The following table shows the templates that come pre-installed with the .NET Core SDK.</span></span> <span data-ttu-id="d2f4c-123">Şablon için varsayılan dil, köşeli ayraçlar içinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-123">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="d2f4c-124">Özel şablon seçeneklerini görmek için kısa ad bağlantısına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-124">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="d2f4c-125">Şablonlar</span><span class="sxs-lookup"><span data-stu-id="d2f4c-125">Templates</span></span>                                    | <span data-ttu-id="d2f4c-126">Kısa ad</span><span class="sxs-lookup"><span data-stu-id="d2f4c-126">Short name</span></span>                      | <span data-ttu-id="d2f4c-127">Dil</span><span class="sxs-lookup"><span data-stu-id="d2f4c-127">Language</span></span>     | <span data-ttu-id="d2f4c-128">Etiketler</span><span class="sxs-lookup"><span data-stu-id="d2f4c-128">Tags</span></span>                                  | <span data-ttu-id="d2f4c-129">Dağıtıla</span><span class="sxs-lookup"><span data-stu-id="d2f4c-129">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="d2f4c-130">Konsol Uygulaması</span><span class="sxs-lookup"><span data-stu-id="d2f4c-130">Console Application</span></span>                          | [<span data-ttu-id="d2f4c-131">konsola</span><span class="sxs-lookup"><span data-stu-id="d2f4c-131">console</span></span>](#console)             | <span data-ttu-id="d2f4c-132">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="d2f4c-132">[C#], F#, VB</span></span> | <span data-ttu-id="d2f4c-133">Ortak/konsol</span><span class="sxs-lookup"><span data-stu-id="d2f4c-133">Common/Console</span></span>                        | <span data-ttu-id="d2f4c-134">1.0</span><span class="sxs-lookup"><span data-stu-id="d2f4c-134">1.0</span></span>        |
| <span data-ttu-id="d2f4c-135">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="d2f4c-135">Class library</span></span>                                | [<span data-ttu-id="d2f4c-136">projesinin</span><span class="sxs-lookup"><span data-stu-id="d2f4c-136">classlib</span></span>](#classlib)           | <span data-ttu-id="d2f4c-137">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="d2f4c-137">[C#], F#, VB</span></span> | <span data-ttu-id="d2f4c-138">Ortak/Kitaplık</span><span class="sxs-lookup"><span data-stu-id="d2f4c-138">Common/Library</span></span>                        | <span data-ttu-id="d2f4c-139">1.0</span><span class="sxs-lookup"><span data-stu-id="d2f4c-139">1.0</span></span>        |
| <span data-ttu-id="d2f4c-140">WPF uygulaması</span><span class="sxs-lookup"><span data-stu-id="d2f4c-140">WPF Application</span></span>                              | [<span data-ttu-id="d2f4c-141">WPF</span><span class="sxs-lookup"><span data-stu-id="d2f4c-141">wpf</span></span>](#wpf)                     | <span data-ttu-id="d2f4c-142">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="d2f4c-142">[C#], VB</span></span>     | <span data-ttu-id="d2f4c-143">Ortak/WPF</span><span class="sxs-lookup"><span data-stu-id="d2f4c-143">Common/WPF</span></span>                            | <span data-ttu-id="d2f4c-144">3,0 (VB için 5,0)</span><span class="sxs-lookup"><span data-stu-id="d2f4c-144">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="d2f4c-145">WPF sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="d2f4c-145">WPF Class library</span></span>                            | [<span data-ttu-id="d2f4c-146">wpflib</span><span class="sxs-lookup"><span data-stu-id="d2f4c-146">wpflib</span></span>](#wpf)                  | <span data-ttu-id="d2f4c-147">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="d2f4c-147">[C#], VB</span></span>     | <span data-ttu-id="d2f4c-148">Ortak/WPF</span><span class="sxs-lookup"><span data-stu-id="d2f4c-148">Common/WPF</span></span>                            | <span data-ttu-id="d2f4c-149">3,0 (VB için 5,0)</span><span class="sxs-lookup"><span data-stu-id="d2f4c-149">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="d2f4c-150">WPF Özel Denetim Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="d2f4c-150">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="d2f4c-151">wpfcustomcontrollib</span><span class="sxs-lookup"><span data-stu-id="d2f4c-151">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="d2f4c-152">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="d2f4c-152">[C#], VB</span></span>     | <span data-ttu-id="d2f4c-153">Ortak/WPF</span><span class="sxs-lookup"><span data-stu-id="d2f4c-153">Common/WPF</span></span>                            | <span data-ttu-id="d2f4c-154">3,0 (VB için 5,0)</span><span class="sxs-lookup"><span data-stu-id="d2f4c-154">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="d2f4c-155">WPF Kullanıcı denetimi kitaplığı</span><span class="sxs-lookup"><span data-stu-id="d2f4c-155">WPF User Control Library</span></span>                     | [<span data-ttu-id="d2f4c-156">wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="d2f4c-156">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="d2f4c-157">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="d2f4c-157">[C#], VB</span></span>     | <span data-ttu-id="d2f4c-158">Ortak/WPF</span><span class="sxs-lookup"><span data-stu-id="d2f4c-158">Common/WPF</span></span>                            | <span data-ttu-id="d2f4c-159">3,0 (VB için 5,0)</span><span class="sxs-lookup"><span data-stu-id="d2f4c-159">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="d2f4c-160">Windows Forms (WinForms) uygulaması</span><span class="sxs-lookup"><span data-stu-id="d2f4c-160">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="d2f4c-161">WinForms</span><span class="sxs-lookup"><span data-stu-id="d2f4c-161">winforms</span></span>](#winforms)           | <span data-ttu-id="d2f4c-162">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="d2f4c-162">[C#], VB</span></span>     | <span data-ttu-id="d2f4c-163">Ortak/WinForms</span><span class="sxs-lookup"><span data-stu-id="d2f4c-163">Common/WinForms</span></span>                       | <span data-ttu-id="d2f4c-164">3,0 (VB için 5,0)</span><span class="sxs-lookup"><span data-stu-id="d2f4c-164">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="d2f4c-165">Windows Forms (WinForms) sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="d2f4c-165">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="d2f4c-166">winformslib</span><span class="sxs-lookup"><span data-stu-id="d2f4c-166">winformslib</span></span>](#winforms)        | <span data-ttu-id="d2f4c-167">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="d2f4c-167">[C#], VB</span></span>     | <span data-ttu-id="d2f4c-168">Ortak/WinForms</span><span class="sxs-lookup"><span data-stu-id="d2f4c-168">Common/WinForms</span></span>                       | <span data-ttu-id="d2f4c-169">3,0 (VB için 5,0)</span><span class="sxs-lookup"><span data-stu-id="d2f4c-169">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="d2f4c-170">Çalışan hizmeti</span><span class="sxs-lookup"><span data-stu-id="d2f4c-170">Worker Service</span></span>                               | [<span data-ttu-id="d2f4c-171">ından</span><span class="sxs-lookup"><span data-stu-id="d2f4c-171">worker</span></span>](#web-others)           | <span data-ttu-id="d2f4c-172">Þ</span><span class="sxs-lookup"><span data-stu-id="d2f4c-172">[C#]</span></span>         | <span data-ttu-id="d2f4c-173">Ortak/çalışan/Web</span><span class="sxs-lookup"><span data-stu-id="d2f4c-173">Common/Worker/Web</span></span>                     | <span data-ttu-id="d2f4c-174">3.0</span><span class="sxs-lookup"><span data-stu-id="d2f4c-174">3.0</span></span>        |
| <span data-ttu-id="d2f4c-175">Birim testi projesi</span><span class="sxs-lookup"><span data-stu-id="d2f4c-175">Unit Test Project</span></span>                            | [<span data-ttu-id="d2f4c-176">'i</span><span class="sxs-lookup"><span data-stu-id="d2f4c-176">mstest</span></span>](#test)                 | <span data-ttu-id="d2f4c-177">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="d2f4c-177">[C#], F#, VB</span></span> | <span data-ttu-id="d2f4c-178">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="d2f4c-178">Test/MSTest</span></span>                           | <span data-ttu-id="d2f4c-179">1.0</span><span class="sxs-lookup"><span data-stu-id="d2f4c-179">1.0</span></span>        |
| <span data-ttu-id="d2f4c-180">NUnit 3 test projesi</span><span class="sxs-lookup"><span data-stu-id="d2f4c-180">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="d2f4c-181">NUnit</span><span class="sxs-lookup"><span data-stu-id="d2f4c-181">nunit</span></span>](#nunit)                 | <span data-ttu-id="d2f4c-182">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="d2f4c-182">[C#], F#, VB</span></span> | <span data-ttu-id="d2f4c-183">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="d2f4c-183">Test/NUnit</span></span>                            | <span data-ttu-id="d2f4c-184">2.1.400</span><span class="sxs-lookup"><span data-stu-id="d2f4c-184">2.1.400</span></span>    |
| <span data-ttu-id="d2f4c-185">NUnit 3 test öğesi</span><span class="sxs-lookup"><span data-stu-id="d2f4c-185">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="d2f4c-186">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="d2f4c-186">[C#], F#, VB</span></span> | <span data-ttu-id="d2f4c-187">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="d2f4c-187">Test/NUnit</span></span>                            | <span data-ttu-id="d2f4c-188">2.2</span><span class="sxs-lookup"><span data-stu-id="d2f4c-188">2.2</span></span>        |
| <span data-ttu-id="d2f4c-189">xUnit test projesi</span><span class="sxs-lookup"><span data-stu-id="d2f4c-189">xUnit Test Project</span></span>                           | [<span data-ttu-id="d2f4c-190">xUnit</span><span class="sxs-lookup"><span data-stu-id="d2f4c-190">xunit</span></span>](#test)                  | <span data-ttu-id="d2f4c-191">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="d2f4c-191">[C#], F#, VB</span></span> | <span data-ttu-id="d2f4c-192">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="d2f4c-192">Test/xUnit</span></span>                            | <span data-ttu-id="d2f4c-193">1.0</span><span class="sxs-lookup"><span data-stu-id="d2f4c-193">1.0</span></span>        |
| <span data-ttu-id="d2f4c-194">Razor bileşeni</span><span class="sxs-lookup"><span data-stu-id="d2f4c-194">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="d2f4c-195">Þ</span><span class="sxs-lookup"><span data-stu-id="d2f4c-195">[C#]</span></span>         | <span data-ttu-id="d2f4c-196">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="d2f4c-196">Web/ASP.NET</span></span>                           | <span data-ttu-id="d2f4c-197">3.0</span><span class="sxs-lookup"><span data-stu-id="d2f4c-197">3.0</span></span>        |
| <span data-ttu-id="d2f4c-198">Razor sayfası</span><span class="sxs-lookup"><span data-stu-id="d2f4c-198">Razor Page</span></span>                                   | [<span data-ttu-id="d2f4c-199">sayfasında</span><span class="sxs-lookup"><span data-stu-id="d2f4c-199">page</span></span>](#page)                   | <span data-ttu-id="d2f4c-200">Þ</span><span class="sxs-lookup"><span data-stu-id="d2f4c-200">[C#]</span></span>         | <span data-ttu-id="d2f4c-201">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="d2f4c-201">Web/ASP.NET</span></span>                           | <span data-ttu-id="d2f4c-202">2.0</span><span class="sxs-lookup"><span data-stu-id="d2f4c-202">2.0</span></span>        |
| <span data-ttu-id="d2f4c-203">MVC Viewıtemts</span><span class="sxs-lookup"><span data-stu-id="d2f4c-203">MVC ViewImports</span></span>                              | [<span data-ttu-id="d2f4c-204">viewıtems 'lar</span><span class="sxs-lookup"><span data-stu-id="d2f4c-204">viewimports</span></span>](#namespace)       | <span data-ttu-id="d2f4c-205">Þ</span><span class="sxs-lookup"><span data-stu-id="d2f4c-205">[C#]</span></span>         | <span data-ttu-id="d2f4c-206">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="d2f4c-206">Web/ASP.NET</span></span>                           | <span data-ttu-id="d2f4c-207">2.0</span><span class="sxs-lookup"><span data-stu-id="d2f4c-207">2.0</span></span>        |
| <span data-ttu-id="d2f4c-208">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="d2f4c-208">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="d2f4c-209">Þ</span><span class="sxs-lookup"><span data-stu-id="d2f4c-209">[C#]</span></span>         | <span data-ttu-id="d2f4c-210">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="d2f4c-210">Web/ASP.NET</span></span>                           | <span data-ttu-id="d2f4c-211">2.0</span><span class="sxs-lookup"><span data-stu-id="d2f4c-211">2.0</span></span>        |
| <span data-ttu-id="d2f4c-212">Blazor Sunucu uygulaması</span><span class="sxs-lookup"><span data-stu-id="d2f4c-212">Blazor Server App</span></span>                            | [<span data-ttu-id="d2f4c-213">blazorserver</span><span class="sxs-lookup"><span data-stu-id="d2f4c-213">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="d2f4c-214">Þ</span><span class="sxs-lookup"><span data-stu-id="d2f4c-214">[C#]</span></span>         | <span data-ttu-id="d2f4c-215">WebBlazor</span><span class="sxs-lookup"><span data-stu-id="d2f4c-215">Web/Blazor</span></span>                            | <span data-ttu-id="d2f4c-216">3.0</span><span class="sxs-lookup"><span data-stu-id="d2f4c-216">3.0</span></span>        |
| <span data-ttu-id="d2f4c-217">BlazorWebAssemblyUygulama</span><span class="sxs-lookup"><span data-stu-id="d2f4c-217">Blazor WebAssembly App</span></span>                       | `blazorwasm`                    | <span data-ttu-id="d2f4c-218">Þ</span><span class="sxs-lookup"><span data-stu-id="d2f4c-218">[C#]</span></span>         | <span data-ttu-id="d2f4c-219">WebBlazor/WebAssembly</span><span class="sxs-lookup"><span data-stu-id="d2f4c-219">Web/Blazor/WebAssembly</span></span>                | <span data-ttu-id="d2f4c-220">3.1.300</span><span class="sxs-lookup"><span data-stu-id="d2f4c-220">3.1.300</span></span>    |
| <span data-ttu-id="d2f4c-221">ASP.NET Core boş</span><span class="sxs-lookup"><span data-stu-id="d2f4c-221">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="d2f4c-222">Web</span><span class="sxs-lookup"><span data-stu-id="d2f4c-222">web</span></span>](#web)                     | <span data-ttu-id="d2f4c-223">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="d2f4c-223">[C#], F#</span></span>     | <span data-ttu-id="d2f4c-224">Web/boş</span><span class="sxs-lookup"><span data-stu-id="d2f4c-224">Web/Empty</span></span>                             | <span data-ttu-id="d2f4c-225">1.0</span><span class="sxs-lookup"><span data-stu-id="d2f4c-225">1.0</span></span>        |
| <span data-ttu-id="d2f4c-226">ASP.NET Core Web uygulaması (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="d2f4c-226">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="d2f4c-227">MVC</span><span class="sxs-lookup"><span data-stu-id="d2f4c-227">mvc</span></span>](#web-options)             | <span data-ttu-id="d2f4c-228">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="d2f4c-228">[C#], F#</span></span>     | <span data-ttu-id="d2f4c-229">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="d2f4c-229">Web/MVC</span></span>                               | <span data-ttu-id="d2f4c-230">1.0</span><span class="sxs-lookup"><span data-stu-id="d2f4c-230">1.0</span></span>        |
| <span data-ttu-id="d2f4c-231">ASP.NET Core Web uygulaması</span><span class="sxs-lookup"><span data-stu-id="d2f4c-231">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="d2f4c-232">WEBAPP, Razor</span><span class="sxs-lookup"><span data-stu-id="d2f4c-232">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="d2f4c-233">Þ</span><span class="sxs-lookup"><span data-stu-id="d2f4c-233">[C#]</span></span>         | <span data-ttu-id="d2f4c-234">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="d2f4c-234">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="d2f4c-235">2,2, 2,0</span><span class="sxs-lookup"><span data-stu-id="d2f4c-235">2.2, 2.0</span></span>   |
| <span data-ttu-id="d2f4c-236">Angular ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d2f4c-236">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="d2f4c-237">Angular</span><span class="sxs-lookup"><span data-stu-id="d2f4c-237">angular</span></span>](#spa)                 | <span data-ttu-id="d2f4c-238">Þ</span><span class="sxs-lookup"><span data-stu-id="d2f4c-238">[C#]</span></span>         | <span data-ttu-id="d2f4c-239">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="d2f4c-239">Web/MVC/SPA</span></span>                           | <span data-ttu-id="d2f4c-240">2.0</span><span class="sxs-lookup"><span data-stu-id="d2f4c-240">2.0</span></span>        |
| <span data-ttu-id="d2f4c-241">React.js ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d2f4c-241">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="d2f4c-242">tıkla</span><span class="sxs-lookup"><span data-stu-id="d2f4c-242">react</span></span>](#spa)                   | <span data-ttu-id="d2f4c-243">Þ</span><span class="sxs-lookup"><span data-stu-id="d2f4c-243">[C#]</span></span>         | <span data-ttu-id="d2f4c-244">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="d2f4c-244">Web/MVC/SPA</span></span>                           | <span data-ttu-id="d2f4c-245">2.0</span><span class="sxs-lookup"><span data-stu-id="d2f4c-245">2.0</span></span>        |
| <span data-ttu-id="d2f4c-246">React.js ve Redux ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d2f4c-246">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="d2f4c-247">reactredux</span><span class="sxs-lookup"><span data-stu-id="d2f4c-247">reactredux</span></span>](#reactredux)       | <span data-ttu-id="d2f4c-248">Þ</span><span class="sxs-lookup"><span data-stu-id="d2f4c-248">[C#]</span></span>         | <span data-ttu-id="d2f4c-249">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="d2f4c-249">Web/MVC/SPA</span></span>                           | <span data-ttu-id="d2f4c-250">2.0</span><span class="sxs-lookup"><span data-stu-id="d2f4c-250">2.0</span></span>        |
| <span data-ttu-id="d2f4c-251">Razor sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="d2f4c-251">Razor Class Library</span></span>                          | [<span data-ttu-id="d2f4c-252">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="d2f4c-252">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="d2f4c-253">Þ</span><span class="sxs-lookup"><span data-stu-id="d2f4c-253">[C#]</span></span>         | <span data-ttu-id="d2f4c-254">Web/Razor/kitaplık/Razor sınıfı kitaplığı</span><span class="sxs-lookup"><span data-stu-id="d2f4c-254">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="d2f4c-255">2.1</span><span class="sxs-lookup"><span data-stu-id="d2f4c-255">2.1</span></span>        |
| <span data-ttu-id="d2f4c-256">ASP.NET Core Web API'si</span><span class="sxs-lookup"><span data-stu-id="d2f4c-256">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="d2f4c-257">WebApi</span><span class="sxs-lookup"><span data-stu-id="d2f4c-257">webapi</span></span>](#webapi)               | <span data-ttu-id="d2f4c-258">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="d2f4c-258">[C#], F#</span></span>     | <span data-ttu-id="d2f4c-259">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="d2f4c-259">Web/WebAPI</span></span>                            | <span data-ttu-id="d2f4c-260">1.0</span><span class="sxs-lookup"><span data-stu-id="d2f4c-260">1.0</span></span>        |
| <span data-ttu-id="d2f4c-261">ASP.NET Core gRPC hizmeti</span><span class="sxs-lookup"><span data-stu-id="d2f4c-261">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="d2f4c-262">GRPC</span><span class="sxs-lookup"><span data-stu-id="d2f4c-262">grpc</span></span>](#web-others)             | <span data-ttu-id="d2f4c-263">Þ</span><span class="sxs-lookup"><span data-stu-id="d2f4c-263">[C#]</span></span>         | <span data-ttu-id="d2f4c-264">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="d2f4c-264">Web/gRPC</span></span>                              | <span data-ttu-id="d2f4c-265">3.0</span><span class="sxs-lookup"><span data-stu-id="d2f4c-265">3.0</span></span>        |
| <span data-ttu-id="d2f4c-266">DotNet gitignore dosyası</span><span class="sxs-lookup"><span data-stu-id="d2f4c-266">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="d2f4c-267">Config</span><span class="sxs-lookup"><span data-stu-id="d2f4c-267">Config</span></span>                                | <span data-ttu-id="d2f4c-268">3.0</span><span class="sxs-lookup"><span data-stu-id="d2f4c-268">3.0</span></span>        |
| <span data-ttu-id="d2f4c-269">Dosya üzerinde global.js</span><span class="sxs-lookup"><span data-stu-id="d2f4c-269">global.json file</span></span>                             | [<span data-ttu-id="d2f4c-270">globaljson</span><span class="sxs-lookup"><span data-stu-id="d2f4c-270">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="d2f4c-271">Config</span><span class="sxs-lookup"><span data-stu-id="d2f4c-271">Config</span></span>                                | <span data-ttu-id="d2f4c-272">2.0</span><span class="sxs-lookup"><span data-stu-id="d2f4c-272">2.0</span></span>        |
| <span data-ttu-id="d2f4c-273">NuGet yapılandırması</span><span class="sxs-lookup"><span data-stu-id="d2f4c-273">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="d2f4c-274">Config</span><span class="sxs-lookup"><span data-stu-id="d2f4c-274">Config</span></span>                                | <span data-ttu-id="d2f4c-275">1.0</span><span class="sxs-lookup"><span data-stu-id="d2f4c-275">1.0</span></span>        |
| <span data-ttu-id="d2f4c-276">DotNet yerel araç bildirim dosyası</span><span class="sxs-lookup"><span data-stu-id="d2f4c-276">Dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="d2f4c-277">Config</span><span class="sxs-lookup"><span data-stu-id="d2f4c-277">Config</span></span>                                | <span data-ttu-id="d2f4c-278">3.0</span><span class="sxs-lookup"><span data-stu-id="d2f4c-278">3.0</span></span>        |
| <span data-ttu-id="d2f4c-279">Web yapılandırması</span><span class="sxs-lookup"><span data-stu-id="d2f4c-279">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="d2f4c-280">Config</span><span class="sxs-lookup"><span data-stu-id="d2f4c-280">Config</span></span>                                | <span data-ttu-id="d2f4c-281">1.0</span><span class="sxs-lookup"><span data-stu-id="d2f4c-281">1.0</span></span>        |
| <span data-ttu-id="d2f4c-282">Çözüm dosyası</span><span class="sxs-lookup"><span data-stu-id="d2f4c-282">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="d2f4c-283">Çözüm</span><span class="sxs-lookup"><span data-stu-id="d2f4c-283">Solution</span></span>                              | <span data-ttu-id="d2f4c-284">1.0</span><span class="sxs-lookup"><span data-stu-id="d2f4c-284">1.0</span></span>        |
| <span data-ttu-id="d2f4c-285">Protokol arabelleği dosyası</span><span class="sxs-lookup"><span data-stu-id="d2f4c-285">Protocol Buffer File</span></span>                         | [<span data-ttu-id="d2f4c-286">Proto</span><span class="sxs-lookup"><span data-stu-id="d2f4c-286">proto</span></span>](#namespace)             |              | <span data-ttu-id="d2f4c-287">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="d2f4c-287">Web/gRPC</span></span>                              | <span data-ttu-id="d2f4c-288">3.0</span><span class="sxs-lookup"><span data-stu-id="d2f4c-288">3.0</span></span>        |

## <a name="options"></a><span data-ttu-id="d2f4c-289">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="d2f4c-289">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="d2f4c-290">Bir şablon oluşturulmasına neden olacaksa, verilen komutun çalıştırılması durumunda ne olacağını gösteren bir Özet görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-290">Displays a summary of what would happen if the given command were run if it would result in a template creation.</span></span> <span data-ttu-id="d2f4c-291">.NET Core 2,2 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-291">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="d2f4c-292">Var olan dosyaları değiştirebilse bile içeriğin oluşturulmasını zorlar.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-292">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="d2f4c-293">Seçilen şablon çıkış dizinindeki mevcut dosyaları geçersiz kılacağından bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-293">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="d2f4c-294">Komut için yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-294">Prints out help for the command.</span></span> <span data-ttu-id="d2f4c-295">`dotnet new`Komutun kendisi veya herhangi bir şablon için çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-295">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="d2f4c-296">Örneğin, `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-296">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="d2f4c-297">Veya tarafından belirtilen bir şablon paketini `PATH` kurar `NUGET_ID` .</span><span class="sxs-lookup"><span data-stu-id="d2f4c-297">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="d2f4c-298">Şablon paketinin bir ön sürümü sürümünü yüklemek istiyorsanız, sürümü biçiminde belirtmeniz gerekir `<package-name>::<package-version>` .</span><span class="sxs-lookup"><span data-stu-id="d2f4c-298">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="d2f4c-299">Varsayılan olarak, `dotnet new` \* en son kararlı paket sürümünü temsil eden sürüm için geçirir.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-299">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="d2f4c-300">[Örnekler](#examples) bölümündeki bir örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-300">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="d2f4c-301">Bu komutu çalıştırdığınızda şablonun bir sürümü zaten yüklüyse, şablon belirtilen sürüme veya sürüm belirtilmemişse en son kararlı sürüme güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-301">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="d2f4c-302">Özel şablonlar oluşturma hakkında daha fazla bilgi için bkz. [DotNet New Için özel şablonlar](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="d2f4c-302">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="d2f4c-303">Belirtilen adı içeren şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-303">Lists templates containing the specified name.</span></span> <span data-ttu-id="d2f4c-304">Ad belirtilmemişse, tüm şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-304">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="d2f4c-305">Oluşturulacak şablonun dili.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-305">The language of the template to create.</span></span> <span data-ttu-id="d2f4c-306">Kabul edilen dil şablona göre değişir (bkz. [arguments](#arguments) bölümünde Varsayılanlar).</span><span class="sxs-lookup"><span data-stu-id="d2f4c-306">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="d2f4c-307">Bazı şablonlar için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-307">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="d2f4c-308">Bazı kabuklar `#` özel bir karakter olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-308">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="d2f4c-309">Bu durumlarda, dil parametre değerini tırnak içine alın.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-309">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="d2f4c-310">Örneğin, `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-310">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="d2f4c-311">Oluşturulan çıkışın adı.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-311">The name for the created output.</span></span> <span data-ttu-id="d2f4c-312">Ad belirtilmemişse, geçerli dizinin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-312">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source <SOURCE>`**

  <span data-ttu-id="d2f4c-313">Yüklemesi sırasında kullanılacak bir NuGet kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-313">Specifies a NuGet source to use during install.</span></span> <span data-ttu-id="d2f4c-314">.NET Core 2,1 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-314">Available since .NET Core 2.1 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="d2f4c-315">Oluşturulan çıkışın yerleştirileceği konum.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-315">Location to place the generated output.</span></span> <span data-ttu-id="d2f4c-316">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-316">The default is the current directory.</span></span>

- **`--type <TYPE>`**

  <span data-ttu-id="d2f4c-317">Şablonları kullanılabilir türlerine göre filtreler.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-317">Filters templates based on available types.</span></span> <span data-ttu-id="d2f4c-318">Önceden tanımlanmış değerler `project` , `item` , ve `other` .</span><span class="sxs-lookup"><span data-stu-id="d2f4c-318">Predefined values are `project`, `item`, and `other`.</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="d2f4c-319">Veya belirtilen bir şablon paketini kaldırır `PATH` `NUGET_ID` .</span><span class="sxs-lookup"><span data-stu-id="d2f4c-319">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="d2f4c-320">`<PATH|NUGET_ID>`Değer belirtilmediğinde, yüklü olan tüm şablon paketleri ve bunlarla ilişkili şablonlar görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-320">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="d2f4c-321">Belirtirken `NUGET_ID` , sürüm numarasını eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-321">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="d2f4c-322">Bu seçeneğe bir parametre belirtmezseniz, komut, yüklü şablonları ve bunlarla ilgili ayrıntıları listeler.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-322">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="d2f4c-323">Bir şablonu kullanarak kaldırmak için `PATH` , yolu tam olarak nitelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-323">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="d2f4c-324">Örneğin, *C:/Users/ \<USER> /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* çalışır, ancak içeren klasörden *./GarciaSoftware.ConsoleTemplate.CSharp* olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-324">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="d2f4c-325">Şablon yolunuzda son Sonlandırıcı Dizin eğik çizgisi eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-325">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="d2f4c-326">Şu anda yüklü olan şablon paketleri için kullanılabilir güncelleştirmelerin olup olmadığını denetler ve bunları kurar.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-326">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="d2f4c-327">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-327">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="d2f4c-328">Şu anda yüklü olan şablon paketleri için kullanılabilir güncelleştirmeler olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-328">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="d2f4c-329">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-329">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="d2f4c-330">Şablon seçenekleri</span><span class="sxs-lookup"><span data-stu-id="d2f4c-330">Template options</span></span>

<span data-ttu-id="d2f4c-331">Her proje şablonunda ek seçenekler bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-331">Each project template may have additional options available.</span></span> <span data-ttu-id="d2f4c-332">Çekirdek şablonlar aşağıdaki ek seçeneklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="d2f4c-332">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="d2f4c-333">console</span><span class="sxs-lookup"><span data-stu-id="d2f4c-333">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="d2f4c-334">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-334">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="d2f4c-335">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-335">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="d2f4c-336">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="d2f4c-336">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="d2f4c-337">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="d2f4c-337">SDK version</span></span> | <span data-ttu-id="d2f4c-338">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="d2f4c-338">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="d2f4c-339">3,1</span><span class="sxs-lookup"><span data-stu-id="d2f4c-339">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="d2f4c-340">3.0</span><span class="sxs-lookup"><span data-stu-id="d2f4c-340">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="d2f4c-341">`LangVersion`Oluşturulan proje dosyasındaki özelliği ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-341">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="d2f4c-342">Örneğin, `--langVersion 7.3` C# 7,3 kullanmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-342">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="d2f4c-343">F # için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-343">Not supported for F#.</span></span> <span data-ttu-id="d2f4c-344">.NET Core 2,2 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-344">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="d2f4c-345">Varsayılan C# sürümlerinin listesi için bkz. [Varsayılanlar](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="d2f4c-345">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="d2f4c-346">Belirtilmişse, proje oluşturma sırasında örtük geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-346">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="d2f4c-347">.NET Core 2,2 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-347">Available since .NET Core 2.2 SDK.</span></span>

***

### <a name="classlib"></a><span data-ttu-id="d2f4c-348">projesinin</span><span class="sxs-lookup"><span data-stu-id="d2f4c-348">classlib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="d2f4c-349">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-349">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="d2f4c-350">Değerler: `netcoreapp<version>` bir .NET Core sınıf kitaplığı oluşturmak veya `netstandard<version>` bir .NET Standard sınıf kitaplığı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-350">Values: `netcoreapp<version>` to create a .NET Core Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="d2f4c-351">Varsayılan değer: `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-351">The default value is `netstandard2.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="d2f4c-352">`LangVersion`Oluşturulan proje dosyasındaki özelliği ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-352">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="d2f4c-353">Örneğin, `--langVersion 7.3` C# 7,3 kullanmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-353">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="d2f4c-354">F # için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-354">Not supported for F#.</span></span> <span data-ttu-id="d2f4c-355">.NET Core 2,2 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-355">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="d2f4c-356">Varsayılan C# sürümlerinin listesi için bkz. [Varsayılanlar](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="d2f4c-356">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="d2f4c-357">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-357">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="wpf-wpflib-wpfcustomcontrollib-wpfusercontrollib"></a><a name="wpf"></a> <span data-ttu-id="d2f4c-358">WPF, wpflib, wpfcustomcontrollib, wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="d2f4c-358">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="d2f4c-359">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-359">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="d2f4c-360">Varsayılan değer: `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-360">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="d2f4c-361">.NET Core 3,1 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-361">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="d2f4c-362">`LangVersion`Oluşturulan proje dosyasındaki özelliği ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-362">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="d2f4c-363">Örneğin, `--langVersion 7.3` C# 7,3 kullanmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-363">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="d2f4c-364">Varsayılan C# sürümlerinin listesi için bkz. [Varsayılanlar](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="d2f4c-364">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="d2f4c-365">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-365">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="winforms-winformslib"></a><a name="winforms"></a> <span data-ttu-id="d2f4c-366">WinForms, winformslib</span><span class="sxs-lookup"><span data-stu-id="d2f4c-366">winforms, winformslib</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="d2f4c-367">`LangVersion`Oluşturulan proje dosyasındaki özelliği ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-367">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="d2f4c-368">Örneğin, `--langVersion 7.3` C# 7,3 kullanmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-368">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="d2f4c-369">Varsayılan C# sürümlerinin listesi için bkz. [Varsayılanlar](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="d2f4c-369">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="d2f4c-370">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-370">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="worker-grpc"></a><a name="web-others"></a> <span data-ttu-id="d2f4c-371">çalışan, GRPC</span><span class="sxs-lookup"><span data-stu-id="d2f4c-371">worker, grpc</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="d2f4c-372">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-372">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="d2f4c-373">Varsayılan değer: `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-373">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="d2f4c-374">.NET Core 3,1 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-374">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="d2f4c-375">Oluşturulan şablondan *launchSettings.js* dışlar.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-375">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="d2f4c-376">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-376">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="mstest-xunit"></a><a name="test"></a> <span data-ttu-id="d2f4c-377">MSTest, xUnit</span><span class="sxs-lookup"><span data-stu-id="d2f4c-377">mstest, xunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="d2f4c-378">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-378">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="d2f4c-379">.NET Core 3,0 SDK 'dan beri kullanılabilir seçeneği.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-379">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="d2f4c-380">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="d2f4c-380">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="d2f4c-381">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="d2f4c-381">SDK version</span></span> | <span data-ttu-id="d2f4c-382">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="d2f4c-382">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="d2f4c-383">3,1</span><span class="sxs-lookup"><span data-stu-id="d2f4c-383">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="d2f4c-384">3.0</span><span class="sxs-lookup"><span data-stu-id="d2f4c-384">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="d2f4c-385">[DotNet Pack](dotnet-pack.md)kullanarak proje için paketleme imkanı sunar.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-385">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="d2f4c-386">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-386">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="nunit"></a><span data-ttu-id="d2f4c-387">NUnit</span><span class="sxs-lookup"><span data-stu-id="d2f4c-387">nunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="d2f4c-388">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-388">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="d2f4c-389">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="d2f4c-389">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="d2f4c-390">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="d2f4c-390">SDK version</span></span> | <span data-ttu-id="d2f4c-391">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="d2f4c-391">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="d2f4c-392">3,1</span><span class="sxs-lookup"><span data-stu-id="d2f4c-392">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="d2f4c-393">3.0</span><span class="sxs-lookup"><span data-stu-id="d2f4c-393">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="d2f4c-394">2.2</span><span class="sxs-lookup"><span data-stu-id="d2f4c-394">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="d2f4c-395">2.1</span><span class="sxs-lookup"><span data-stu-id="d2f4c-395">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="d2f4c-396">[DotNet Pack](dotnet-pack.md)kullanarak proje için paketleme imkanı sunar.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-396">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="d2f4c-397">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-397">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="page"></a><span data-ttu-id="d2f4c-398">sayfasında</span><span class="sxs-lookup"><span data-stu-id="d2f4c-398">page</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="d2f4c-399">Oluşturulan kod için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-399">Namespace for the generated code.</span></span> <span data-ttu-id="d2f4c-400">Varsayılan değer: `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-400">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="d2f4c-401">PageModel olmadan sayfayı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-401">Creates the page without a PageModel.</span></span>

***

### <a name="viewimports-proto"></a><a name="namespace"></a> <span data-ttu-id="d2f4c-402">viewıtemler, Proto</span><span class="sxs-lookup"><span data-stu-id="d2f4c-402">viewimports, proto</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="d2f4c-403">Oluşturulan kod için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-403">Namespace for the generated code.</span></span> <span data-ttu-id="d2f4c-404">Varsayılan değer: `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-404">The default value is `MyApp.Namespace`.</span></span>

***

### <a name="blazorserver"></a><span data-ttu-id="d2f4c-405">blazorserver</span><span class="sxs-lookup"><span data-stu-id="d2f4c-405">blazorserver</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="d2f4c-406">Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-406">The type of authentication to use.</span></span> <span data-ttu-id="d2f4c-407">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d2f4c-407">The possible values are:</span></span>

  - <span data-ttu-id="d2f4c-408">`None` -Kimlik doğrulaması yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="d2f4c-408">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="d2f4c-409">`Individual` -Bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-409">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="d2f4c-410">`IndividualB2C` -Azure AD B2C ile bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-410">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="d2f4c-411">`SingleOrg` -Tek bir kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-411">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="d2f4c-412">`MultiOrg` -Birden çok kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-412">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="d2f4c-413">`Windows` -Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-413">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="d2f4c-414">Bağlanılacak Azure Active Directory B2C örneği.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-414">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="d2f4c-415">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-415">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="d2f4c-416">Varsayılan değer: `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-416">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="d2f4c-417">Bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-417">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="d2f4c-418">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-418">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="d2f4c-419">Bu proje için parola sıfırlama ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-419">The reset password policy ID for this project.</span></span> <span data-ttu-id="d2f4c-420">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-420">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="d2f4c-421">Bu proje için profil ilke KIMLIĞINI Düzenle.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-421">The edit profile policy ID for this project.</span></span> <span data-ttu-id="d2f4c-422">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-422">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="d2f4c-423">Bağlanılacak Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-423">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="d2f4c-424">`SingleOrg`Veya `MultiOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-424">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="d2f4c-425">Varsayılan değer: `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-425">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="d2f4c-426">Bu projenin Istemci KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-426">The Client ID for this project.</span></span> <span data-ttu-id="d2f4c-427">`IndividualB2C`, `SingleOrg` Veya `MultiOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-427">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="d2f4c-428">Varsayılan değer: `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-428">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="d2f4c-429">Dizin kiracının etki alanı.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-429">The domain for the directory tenant.</span></span> <span data-ttu-id="d2f4c-430">`SingleOrg`Veya `IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-430">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="d2f4c-431">Varsayılan değer: `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-431">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="d2f4c-432">Bağlanılacak dizinin Tenantıd KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-432">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="d2f4c-433">`SingleOrg`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-433">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="d2f4c-434">Varsayılan değer: `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-434">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="d2f4c-435">Uygulamanın yeniden yönlendirme URI 'sinin temel yolundaki istek yolu.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-435">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="d2f4c-436">`SingleOrg`Veya `IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-436">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="d2f4c-437">Varsayılan değer: `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-437">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="d2f4c-438">Bu uygulamanın dizine okuma erişimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-438">Allows this application read-access to the directory.</span></span> <span data-ttu-id="d2f4c-439">Yalnızca `SingleOrg` veya `MultiOrg` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-439">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="d2f4c-440">Oluşturulan şablondan *launchSettings.js* dışlar.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-440">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="d2f4c-441">HTTPS 'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-441">Turns off HTTPS.</span></span> <span data-ttu-id="d2f4c-442">Bu seçenek yalnızca,, `Individual` , `IndividualB2C` `SingleOrg` veya için kullanılmıyorsa geçerlidir `MultiOrg` `--auth` .</span><span class="sxs-lookup"><span data-stu-id="d2f4c-442">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="d2f4c-443">SQLite yerine LocalDB kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-443">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="d2f4c-444">Yalnızca `Individual` veya `IndividualB2C` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-444">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="d2f4c-445">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-445">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web"></a><span data-ttu-id="d2f4c-446">web</span><span class="sxs-lookup"><span data-stu-id="d2f4c-446">web</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="d2f4c-447">Oluşturulan şablondan *launchSettings.js* dışlar.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-447">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="d2f4c-448">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-448">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="d2f4c-449">Seçenek .NET Core 2,2 SDK sürümünde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-449">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="d2f4c-450">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="d2f4c-450">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="d2f4c-451">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="d2f4c-451">SDK version</span></span> | <span data-ttu-id="d2f4c-452">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="d2f4c-452">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="d2f4c-453">3,1</span><span class="sxs-lookup"><span data-stu-id="d2f4c-453">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="d2f4c-454">3.0</span><span class="sxs-lookup"><span data-stu-id="d2f4c-454">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="d2f4c-455">2.1</span><span class="sxs-lookup"><span data-stu-id="d2f4c-455">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="d2f4c-456">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-456">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="d2f4c-457">HTTPS 'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-457">Turns off HTTPS.</span></span>

***

### <a name="mvc-webapp"></a><a name="web-options"></a> <span data-ttu-id="d2f4c-458">MVC, WebApp</span><span class="sxs-lookup"><span data-stu-id="d2f4c-458">mvc, webapp</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="d2f4c-459">Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-459">The type of authentication to use.</span></span> <span data-ttu-id="d2f4c-460">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d2f4c-460">The possible values are:</span></span>

  - <span data-ttu-id="d2f4c-461">`None` -Kimlik doğrulaması yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="d2f4c-461">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="d2f4c-462">`Individual` -Bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-462">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="d2f4c-463">`IndividualB2C` -Azure AD B2C ile bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-463">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="d2f4c-464">`SingleOrg` -Tek bir kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-464">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="d2f4c-465">`MultiOrg` -Birden çok kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-465">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="d2f4c-466">`Windows` -Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-466">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="d2f4c-467">Bağlanılacak Azure Active Directory B2C örneği.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-467">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="d2f4c-468">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-468">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="d2f4c-469">Varsayılan değer: `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-469">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="d2f4c-470">Bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-470">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="d2f4c-471">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-471">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="d2f4c-472">Bu proje için parola sıfırlama ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-472">The reset password policy ID for this project.</span></span> <span data-ttu-id="d2f4c-473">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-473">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="d2f4c-474">Bu proje için profil ilke KIMLIĞINI Düzenle.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-474">The edit profile policy ID for this project.</span></span> <span data-ttu-id="d2f4c-475">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-475">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="d2f4c-476">Bağlanılacak Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-476">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="d2f4c-477">`SingleOrg`Veya `MultiOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-477">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="d2f4c-478">Varsayılan değer: `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-478">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="d2f4c-479">Bu projenin Istemci KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-479">The Client ID for this project.</span></span> <span data-ttu-id="d2f4c-480">`IndividualB2C`, `SingleOrg` Veya `MultiOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-480">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="d2f4c-481">Varsayılan değer: `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-481">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="d2f4c-482">Dizin kiracının etki alanı.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-482">The domain for the directory tenant.</span></span> <span data-ttu-id="d2f4c-483">`SingleOrg`Veya `IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-483">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="d2f4c-484">Varsayılan değer: `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-484">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="d2f4c-485">Bağlanılacak dizinin Tenantıd KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-485">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="d2f4c-486">`SingleOrg`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-486">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="d2f4c-487">Varsayılan değer: `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-487">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="d2f4c-488">Uygulamanın yeniden yönlendirme URI 'sinin temel yolundaki istek yolu.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-488">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="d2f4c-489">`SingleOrg`Veya `IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-489">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="d2f4c-490">Varsayılan değer: `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-490">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="d2f4c-491">Bu uygulamanın dizine okuma erişimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-491">Allows this application read-access to the directory.</span></span> <span data-ttu-id="d2f4c-492">Yalnızca `SingleOrg` veya `MultiOrg` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-492">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="d2f4c-493">Oluşturulan şablondan *launchSettings.js* dışlar.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-493">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="d2f4c-494">HTTPS 'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-494">Turns off HTTPS.</span></span> <span data-ttu-id="d2f4c-495">Bu seçenek yalnızca,,, veya kullanılmıyorsa geçerlidir `Individual` `IndividualB2C` `SingleOrg` `MultiOrg` .</span><span class="sxs-lookup"><span data-stu-id="d2f4c-495">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="d2f4c-496">SQLite yerine LocalDB kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-496">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="d2f4c-497">Yalnızca `Individual` veya `IndividualB2C` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-497">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="d2f4c-498">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-498">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="d2f4c-499">.NET Core 3,0 SDK 'dan beri kullanılabilir seçeneği.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-499">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="d2f4c-500">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="d2f4c-500">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="d2f4c-501">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="d2f4c-501">SDK version</span></span> | <span data-ttu-id="d2f4c-502">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="d2f4c-502">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="d2f4c-503">3,1</span><span class="sxs-lookup"><span data-stu-id="d2f4c-503">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="d2f4c-504">3.0</span><span class="sxs-lookup"><span data-stu-id="d2f4c-504">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="d2f4c-505">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-505">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="d2f4c-506">Projedeki BrowserLink öğesini içerir.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-506">Includes BrowserLink in the project.</span></span> <span data-ttu-id="d2f4c-507">Seçenek .NET Core 2,2 ve 3,1 SDK sürümünde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-507">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

- **`-rrc|--razor-runtime-compilation`**

  <span data-ttu-id="d2f4c-508">Projenin hata ayıklama yapılarında [Razor çalışma zamanı derlemesini](/aspnet/core/mvc/views/view-compilation#runtime-compilation) kullanmak üzere yapılandırılıp yapılandırılmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-508">Determines if the project is configured to use [Razor runtime compilation](/aspnet/core/mvc/views/view-compilation#runtime-compilation) in Debug builds.</span></span> <span data-ttu-id="d2f4c-509">.NET Core 3.1.201 SDK 'dan beri kullanılabilir seçeneği.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-509">Option available since .NET Core 3.1.201 SDK.</span></span>

***

### <a name="angular-react"></a><a name="spa"></a> <span data-ttu-id="d2f4c-510">Angular, tepki verme</span><span class="sxs-lookup"><span data-stu-id="d2f4c-510">angular, react</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="d2f4c-511">Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-511">The type of authentication to use.</span></span> <span data-ttu-id="d2f4c-512">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-512">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="d2f4c-513">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d2f4c-513">The possible values are:</span></span>

  - <span data-ttu-id="d2f4c-514">`None` -Kimlik doğrulaması yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="d2f4c-514">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="d2f4c-515">`Individual` -Bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-515">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="d2f4c-516">Oluşturulan şablondan *launchSettings.js* dışlar.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-516">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="d2f4c-517">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-517">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="d2f4c-518">HTTPS 'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-518">Turns off HTTPS.</span></span> <span data-ttu-id="d2f4c-519">Bu seçenek yalnızca kimlik doğrulaması ise geçerlidir `None` .</span><span class="sxs-lookup"><span data-stu-id="d2f4c-519">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="d2f4c-520">SQLite yerine LocalDB kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-520">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="d2f4c-521">Yalnızca `Individual` veya `IndividualB2C` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-521">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="d2f4c-522">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-522">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="d2f4c-523">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-523">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="d2f4c-524">Seçenek .NET Core 2,2 SDK sürümünde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-524">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="d2f4c-525">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="d2f4c-525">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="d2f4c-526">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="d2f4c-526">SDK version</span></span> | <span data-ttu-id="d2f4c-527">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="d2f4c-527">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="d2f4c-528">3,1</span><span class="sxs-lookup"><span data-stu-id="d2f4c-528">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="d2f4c-529">3.0</span><span class="sxs-lookup"><span data-stu-id="d2f4c-529">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="d2f4c-530">2.1</span><span class="sxs-lookup"><span data-stu-id="d2f4c-530">2.1</span></span>         | `netcoreapp2.0` |

***

### <a name="reactredux"></a><span data-ttu-id="d2f4c-531">reactredux</span><span class="sxs-lookup"><span data-stu-id="d2f4c-531">reactredux</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="d2f4c-532">Oluşturulan şablondan *launchSettings.js* dışlar.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-532">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="d2f4c-533">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-533">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="d2f4c-534">Seçenek .NET Core 2,2 SDK sürümünde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-534">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="d2f4c-535">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="d2f4c-535">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="d2f4c-536">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="d2f4c-536">SDK version</span></span> | <span data-ttu-id="d2f4c-537">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="d2f4c-537">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="d2f4c-538">3,1</span><span class="sxs-lookup"><span data-stu-id="d2f4c-538">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="d2f4c-539">3.0</span><span class="sxs-lookup"><span data-stu-id="d2f4c-539">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="d2f4c-540">2.1</span><span class="sxs-lookup"><span data-stu-id="d2f4c-540">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="d2f4c-541">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-541">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="d2f4c-542">HTTPS 'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-542">Turns off HTTPS.</span></span>

***

### <a name="razorclasslib"></a><span data-ttu-id="d2f4c-543">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="d2f4c-543">razorclasslib</span></span>

- **`--no-restore`**

  <span data-ttu-id="d2f4c-544">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-544">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="d2f4c-545">, Bu kitaplığa bileşenlere ek olarak geleneksel Razor sayfaları ve görünümleri eklenmesini destekler.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-545">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="d2f4c-546">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-546">Available since .NET Core 3.0 SDK.</span></span>

***
  
### <a name="webapi"></a><span data-ttu-id="d2f4c-547">WebApi</span><span class="sxs-lookup"><span data-stu-id="d2f4c-547">webapi</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="d2f4c-548">Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-548">The type of authentication to use.</span></span> <span data-ttu-id="d2f4c-549">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d2f4c-549">The possible values are:</span></span>

  - <span data-ttu-id="d2f4c-550">`None` -Kimlik doğrulaması yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="d2f4c-550">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="d2f4c-551">`IndividualB2C` -Azure AD B2C ile bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-551">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="d2f4c-552">`SingleOrg` -Tek bir kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-552">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="d2f4c-553">`Windows` -Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-553">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="d2f4c-554">Bağlanılacak Azure Active Directory B2C örneği.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-554">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="d2f4c-555">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-555">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="d2f4c-556">Varsayılan değer: `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-556">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="d2f4c-557">Bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-557">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="d2f4c-558">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-558">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="d2f4c-559">Bağlanılacak Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-559">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="d2f4c-560">`SingleOrg`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-560">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="d2f4c-561">Varsayılan değer: `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-561">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="d2f4c-562">Bu projenin Istemci KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-562">The Client ID for this project.</span></span> <span data-ttu-id="d2f4c-563">`IndividualB2C`Veya `SingleOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-563">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="d2f4c-564">Varsayılan değer: `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-564">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="d2f4c-565">Dizin kiracının etki alanı.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-565">The domain for the directory tenant.</span></span> <span data-ttu-id="d2f4c-566">`IndividualB2C`Veya `SingleOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-566">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="d2f4c-567">Varsayılan değer: `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-567">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="d2f4c-568">Bağlanılacak dizinin Tenantıd KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-568">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="d2f4c-569">`SingleOrg`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-569">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="d2f4c-570">Varsayılan değer: `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-570">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="d2f4c-571">Bu uygulamanın dizine okuma erişimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-571">Allows this application read-access to the directory.</span></span> <span data-ttu-id="d2f4c-572">Yalnızca `SingleOrg` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-572">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="d2f4c-573">Oluşturulan şablondan *launchSettings.js* dışlar.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-573">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="d2f4c-574">HTTPS 'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-574">Turns off HTTPS.</span></span> <span data-ttu-id="d2f4c-575">`app.UseHsts` ve `app.UseHttpsRedirection` öğesine eklenmez `Startup.Configure` .</span><span class="sxs-lookup"><span data-stu-id="d2f4c-575">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="d2f4c-576">Bu seçenek yalnızca `IndividualB2C` `SingleOrg` kimlik doğrulaması için kullanılmıyorsa geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-576">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="d2f4c-577">SQLite yerine LocalDB kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-577">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="d2f4c-578">Yalnızca `IndividualB2C` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-578">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="d2f4c-579">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-579">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="d2f4c-580">Seçenek .NET Core 2,2 SDK sürümünde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-580">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="d2f4c-581">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="d2f4c-581">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="d2f4c-582">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="d2f4c-582">SDK version</span></span> | <span data-ttu-id="d2f4c-583">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="d2f4c-583">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="d2f4c-584">3,1</span><span class="sxs-lookup"><span data-stu-id="d2f4c-584">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="d2f4c-585">3.0</span><span class="sxs-lookup"><span data-stu-id="d2f4c-585">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="d2f4c-586">2.1</span><span class="sxs-lookup"><span data-stu-id="d2f4c-586">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="d2f4c-587">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-587">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="globaljson"></a><span data-ttu-id="d2f4c-588">globaljson</span><span class="sxs-lookup"><span data-stu-id="d2f4c-588">globaljson</span></span>

- **`--sdk-version <VERSION_NUMBER>`**

  <span data-ttu-id="d2f4c-589">*global.json* dosyasında kullanılacak .NET Core SDK sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-589">Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="d2f4c-590">Örnekler</span><span class="sxs-lookup"><span data-stu-id="d2f4c-590">Examples</span></span>

- <span data-ttu-id="d2f4c-591">Şablon adını belirterek bir C# konsol uygulaması projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="d2f4c-591">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="d2f4c-592">Geçerli dizinde bir F # konsol uygulaması projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="d2f4c-592">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang "F#"
  ```

- <span data-ttu-id="d2f4c-593">Belirtilen dizinde bir .NET Standard sınıf kitaplığı projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="d2f4c-593">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="d2f4c-594">Geçerli dizinde kimlik doğrulaması olmadan yeni bir ASP.NET Core C# MVC projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="d2f4c-594">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="d2f4c-595">Yeni bir xUnit projesi oluştur:</span><span class="sxs-lookup"><span data-stu-id="d2f4c-595">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="d2f4c-596">Tek sayfalı uygulama (SPA) şablonları için kullanılabilen tüm şablonları listeleyin:</span><span class="sxs-lookup"><span data-stu-id="d2f4c-596">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="d2f4c-597">*We* alt dizeniz ile eşleşen tüm şablonları listeleyin.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-597">List all templates matching the *we* substring.</span></span> <span data-ttu-id="d2f4c-598">Tam eşleşme bulunamadı, bu nedenle alt dize eşleştirmesi hem kısa ad hem de ad sütunlarında çalışır.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-598">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="d2f4c-599">Şablonla *eşleşen şablonu*çağırma girişimi.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-599">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="d2f4c-600">Tek bir eşleşme belirlenemiyorsa kısmi eşleşen şablonları listeleyin.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-600">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="d2f4c-601">ASP.NET Core için SPA şablonlarının 2,0 sürümünü yükler:</span><span class="sxs-lookup"><span data-stu-id="d2f4c-601">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="d2f4c-602">Yüklü şablonları ve bunlarla ilgili ayrıntıları, bunları kaldırma dahil olmak üzere listeleyin:</span><span class="sxs-lookup"><span data-stu-id="d2f4c-602">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="d2f4c-603">SDK sürümünü 3.1.101 olarak ayarlamak için geçerli dizinde bir *global.js* oluşturun:</span><span class="sxs-lookup"><span data-stu-id="d2f4c-603">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="d2f4c-604">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2f4c-604">See also</span></span>

- [<span data-ttu-id="d2f4c-605">DotNet New için özel şablonlar</span><span class="sxs-lookup"><span data-stu-id="d2f4c-605">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="d2f4c-606">Dotnet new için özel şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="d2f4c-606">Create a custom template for dotnet new</span></span>](../tutorials/cli-templates-create-item-template.md)
- [<span data-ttu-id="d2f4c-607">DotNet/DotNet-şablon-örnek GitHub deposu</span><span class="sxs-lookup"><span data-stu-id="d2f4c-607">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="d2f4c-608">DotNet New için kullanılabilir şablonlar</span><span class="sxs-lookup"><span data-stu-id="d2f4c-608">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
