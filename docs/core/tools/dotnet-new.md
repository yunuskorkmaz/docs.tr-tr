---
title: DotNet yeni komut
description: DotNet New komutu, belirtilen şablona göre yeni .NET Core projeleri oluşturur.
ms.date: 04/10/2020
ms.openlocfilehash: 1544f519f2a5f6a1a6e042c1db720eff45f5d98c
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442247"
---
# <a name="dotnet-new"></a><span data-ttu-id="649ff-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="649ff-103">dotnet new</span></span>

<span data-ttu-id="649ff-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,0 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="649ff-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="649ff-105">Name</span><span class="sxs-lookup"><span data-stu-id="649ff-105">Name</span></span>

<span data-ttu-id="649ff-106">`dotnet new`-Belirtilen şablonu temel alan yeni bir proje, yapılandırma dosyası veya çözüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="649ff-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="649ff-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="649ff-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install {PATH|NUGET_ID}]
    [-lang|--language {"C#"|"F#"|VB}] [-n|--name <OUTPUT_NAME>]
    [--nuget-source <SOURCE>] [-o|--output <OUTPUT_DIRECTORY>]
    [-u|--uninstall] [--update-apply] [--update-check] [Template options]

dotnet new <TEMPLATE> [-l|--list] [--type <TYPE>]

dotnet new -h|--help
```

## <a name="description"></a><span data-ttu-id="649ff-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="649ff-108">Description</span></span>

<span data-ttu-id="649ff-109">`dotnet new`Komut bir şablonu temel alan bir .NET Core projesi veya diğer yapılar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="649ff-109">The `dotnet new` command creates a .NET Core project or other artifacts based on a template.</span></span>

<span data-ttu-id="649ff-110">Komutu, belirtilen şablon ve seçeneklere göre diskteki yapıtları oluşturmak için [şablon altyapısını](https://github.com/dotnet/templating) çağırır.</span><span class="sxs-lookup"><span data-stu-id="649ff-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="649ff-111">Örtük geri yükleme</span><span class="sxs-lookup"><span data-stu-id="649ff-111">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="649ff-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="649ff-112">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="649ff-113">Komut çağrıldığında örnek oluşturulacak şablon.</span><span class="sxs-lookup"><span data-stu-id="649ff-113">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="649ff-114">Her şablonun geçirebilmeniz için özel seçenekleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="649ff-114">Each template might have specific options you can pass.</span></span> <span data-ttu-id="649ff-115">Daha fazla bilgi için bkz. [şablon seçenekleri](#template-options).</span><span class="sxs-lookup"><span data-stu-id="649ff-115">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="649ff-116">`dotnet new --list` `dotnet new -l` Tüm yüklü şablonların listesini görmek için veya çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="649ff-116">You can run `dotnet new --list` or `dotnet new -l` to see a list of all installed templates.</span></span> <span data-ttu-id="649ff-117">Değer, `TEMPLATE` döndürülen tablodaki **Şablonlar** veya **kısa ad** sütunundaki metinde tam eşleşme değilse, bu iki sütunda bir alt dize eşleşmesi gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="649ff-117">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="649ff-118">.NET Core 3,0 SDK ile başlayarak, aşağıdaki koşullarda komutu çağırdığınızda CLı NuGet.org içindeki şablonları arar `dotnet new` :</span><span class="sxs-lookup"><span data-stu-id="649ff-118">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="649ff-119">CLı çağrılırken bir şablon eşleşmesi bulamazsa `dotnet new` , bu da kısmi değildir.</span><span class="sxs-lookup"><span data-stu-id="649ff-119">If the CLI can't find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="649ff-120">Şablonun daha yeni bir sürümü kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="649ff-120">If there's a newer version of the template available.</span></span> <span data-ttu-id="649ff-121">Bu durumda, proje veya yapıt oluşturulur ancak CLı, şablonun güncelleştirilmiş bir sürümü hakkında sizi uyarır.</span><span class="sxs-lookup"><span data-stu-id="649ff-121">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="649ff-122">Aşağıdaki tabloda, .NET Core SDK ile önceden yüklenmiş olan şablonlar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="649ff-122">The following table shows the templates that come pre-installed with the .NET Core SDK.</span></span> <span data-ttu-id="649ff-123">Şablon için varsayılan dil, köşeli ayraçlar içinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="649ff-123">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="649ff-124">Özel şablon seçeneklerini görmek için kısa ad bağlantısına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="649ff-124">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="649ff-125">Şablonlar</span><span class="sxs-lookup"><span data-stu-id="649ff-125">Templates</span></span>                                    | <span data-ttu-id="649ff-126">Kısa ad</span><span class="sxs-lookup"><span data-stu-id="649ff-126">Short name</span></span>                      | <span data-ttu-id="649ff-127">Dil</span><span class="sxs-lookup"><span data-stu-id="649ff-127">Language</span></span>     | <span data-ttu-id="649ff-128">Etiketler</span><span class="sxs-lookup"><span data-stu-id="649ff-128">Tags</span></span>                                  | <span data-ttu-id="649ff-129">Dağıtıla</span><span class="sxs-lookup"><span data-stu-id="649ff-129">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="649ff-130">Konsol Uygulaması</span><span class="sxs-lookup"><span data-stu-id="649ff-130">Console Application</span></span>                          | [<span data-ttu-id="649ff-131">konsola</span><span class="sxs-lookup"><span data-stu-id="649ff-131">console</span></span>](#console)             | <span data-ttu-id="649ff-132">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="649ff-132">[C#], F#, VB</span></span> | <span data-ttu-id="649ff-133">Ortak/konsol</span><span class="sxs-lookup"><span data-stu-id="649ff-133">Common/Console</span></span>                        | <span data-ttu-id="649ff-134">1.0</span><span class="sxs-lookup"><span data-stu-id="649ff-134">1.0</span></span>        |
| <span data-ttu-id="649ff-135">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="649ff-135">Class library</span></span>                                | [<span data-ttu-id="649ff-136">projesinin</span><span class="sxs-lookup"><span data-stu-id="649ff-136">classlib</span></span>](#classlib)           | <span data-ttu-id="649ff-137">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="649ff-137">[C#], F#, VB</span></span> | <span data-ttu-id="649ff-138">Ortak/Kitaplık</span><span class="sxs-lookup"><span data-stu-id="649ff-138">Common/Library</span></span>                        | <span data-ttu-id="649ff-139">1.0</span><span class="sxs-lookup"><span data-stu-id="649ff-139">1.0</span></span>        |
| <span data-ttu-id="649ff-140">WPF uygulaması</span><span class="sxs-lookup"><span data-stu-id="649ff-140">WPF Application</span></span>                              | [<span data-ttu-id="649ff-141">WPF</span><span class="sxs-lookup"><span data-stu-id="649ff-141">wpf</span></span>](#wpf)                     | <span data-ttu-id="649ff-142">Þ</span><span class="sxs-lookup"><span data-stu-id="649ff-142">[C#]</span></span>         | <span data-ttu-id="649ff-143">Ortak/WPF</span><span class="sxs-lookup"><span data-stu-id="649ff-143">Common/WPF</span></span>                            | <span data-ttu-id="649ff-144">3.0</span><span class="sxs-lookup"><span data-stu-id="649ff-144">3.0</span></span>        |
| <span data-ttu-id="649ff-145">WPF sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="649ff-145">WPF Class library</span></span>                            | [<span data-ttu-id="649ff-146">wpflib</span><span class="sxs-lookup"><span data-stu-id="649ff-146">wpflib</span></span>](#wpf)                  | <span data-ttu-id="649ff-147">Þ</span><span class="sxs-lookup"><span data-stu-id="649ff-147">[C#]</span></span>         | <span data-ttu-id="649ff-148">Ortak/WPF</span><span class="sxs-lookup"><span data-stu-id="649ff-148">Common/WPF</span></span>                            | <span data-ttu-id="649ff-149">3.0</span><span class="sxs-lookup"><span data-stu-id="649ff-149">3.0</span></span>        |
| <span data-ttu-id="649ff-150">WPF Özel Denetim Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="649ff-150">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="649ff-151">wpfcustomcontrollib</span><span class="sxs-lookup"><span data-stu-id="649ff-151">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="649ff-152">Þ</span><span class="sxs-lookup"><span data-stu-id="649ff-152">[C#]</span></span>         | <span data-ttu-id="649ff-153">Ortak/WPF</span><span class="sxs-lookup"><span data-stu-id="649ff-153">Common/WPF</span></span>                            | <span data-ttu-id="649ff-154">3.0</span><span class="sxs-lookup"><span data-stu-id="649ff-154">3.0</span></span>        |
| <span data-ttu-id="649ff-155">WPF Kullanıcı denetimi kitaplığı</span><span class="sxs-lookup"><span data-stu-id="649ff-155">WPF User Control Library</span></span>                     | [<span data-ttu-id="649ff-156">wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="649ff-156">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="649ff-157">Þ</span><span class="sxs-lookup"><span data-stu-id="649ff-157">[C#]</span></span>         | <span data-ttu-id="649ff-158">Ortak/WPF</span><span class="sxs-lookup"><span data-stu-id="649ff-158">Common/WPF</span></span>                            | <span data-ttu-id="649ff-159">3.0</span><span class="sxs-lookup"><span data-stu-id="649ff-159">3.0</span></span>        |
| <span data-ttu-id="649ff-160">Windows Forms (WinForms) uygulaması</span><span class="sxs-lookup"><span data-stu-id="649ff-160">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="649ff-161">WinForms</span><span class="sxs-lookup"><span data-stu-id="649ff-161">winforms</span></span>](#winforms)           | <span data-ttu-id="649ff-162">Þ</span><span class="sxs-lookup"><span data-stu-id="649ff-162">[C#]</span></span>         | <span data-ttu-id="649ff-163">Ortak/WinForms</span><span class="sxs-lookup"><span data-stu-id="649ff-163">Common/WinForms</span></span>                       | <span data-ttu-id="649ff-164">3.0</span><span class="sxs-lookup"><span data-stu-id="649ff-164">3.0</span></span>        |
| <span data-ttu-id="649ff-165">Windows Forms (WinForms) sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="649ff-165">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="649ff-166">winformslib</span><span class="sxs-lookup"><span data-stu-id="649ff-166">winformslib</span></span>](#winforms)        | <span data-ttu-id="649ff-167">Þ</span><span class="sxs-lookup"><span data-stu-id="649ff-167">[C#]</span></span>         | <span data-ttu-id="649ff-168">Ortak/WinForms</span><span class="sxs-lookup"><span data-stu-id="649ff-168">Common/WinForms</span></span>                       | <span data-ttu-id="649ff-169">3.0</span><span class="sxs-lookup"><span data-stu-id="649ff-169">3.0</span></span>        |
| <span data-ttu-id="649ff-170">Çalışan hizmeti</span><span class="sxs-lookup"><span data-stu-id="649ff-170">Worker Service</span></span>                               | [<span data-ttu-id="649ff-171">ından</span><span class="sxs-lookup"><span data-stu-id="649ff-171">worker</span></span>](#web-others)           | <span data-ttu-id="649ff-172">Þ</span><span class="sxs-lookup"><span data-stu-id="649ff-172">[C#]</span></span>         | <span data-ttu-id="649ff-173">Ortak/çalışan/Web</span><span class="sxs-lookup"><span data-stu-id="649ff-173">Common/Worker/Web</span></span>                     | <span data-ttu-id="649ff-174">3.0</span><span class="sxs-lookup"><span data-stu-id="649ff-174">3.0</span></span>        |
| <span data-ttu-id="649ff-175">Birim testi projesi</span><span class="sxs-lookup"><span data-stu-id="649ff-175">Unit Test Project</span></span>                            | [<span data-ttu-id="649ff-176">'i</span><span class="sxs-lookup"><span data-stu-id="649ff-176">mstest</span></span>](#test)                 | <span data-ttu-id="649ff-177">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="649ff-177">[C#], F#, VB</span></span> | <span data-ttu-id="649ff-178">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="649ff-178">Test/MSTest</span></span>                           | <span data-ttu-id="649ff-179">1.0</span><span class="sxs-lookup"><span data-stu-id="649ff-179">1.0</span></span>        |
| <span data-ttu-id="649ff-180">NUnit 3 test projesi</span><span class="sxs-lookup"><span data-stu-id="649ff-180">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="649ff-181">NUnit</span><span class="sxs-lookup"><span data-stu-id="649ff-181">nunit</span></span>](#nunit)                  | <span data-ttu-id="649ff-182">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="649ff-182">[C#], F#, VB</span></span> | <span data-ttu-id="649ff-183">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="649ff-183">Test/NUnit</span></span>                            | <span data-ttu-id="649ff-184">2.1.400</span><span class="sxs-lookup"><span data-stu-id="649ff-184">2.1.400</span></span>    |
| <span data-ttu-id="649ff-185">NUnit 3 test öğesi</span><span class="sxs-lookup"><span data-stu-id="649ff-185">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="649ff-186">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="649ff-186">[C#], F#, VB</span></span> | <span data-ttu-id="649ff-187">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="649ff-187">Test/NUnit</span></span>                            | <span data-ttu-id="649ff-188">2,2</span><span class="sxs-lookup"><span data-stu-id="649ff-188">2.2</span></span>        |
| <span data-ttu-id="649ff-189">xUnit test projesi</span><span class="sxs-lookup"><span data-stu-id="649ff-189">xUnit Test Project</span></span>                           | [<span data-ttu-id="649ff-190">xUnit</span><span class="sxs-lookup"><span data-stu-id="649ff-190">xunit</span></span>](#test)                  | <span data-ttu-id="649ff-191">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="649ff-191">[C#], F#, VB</span></span> | <span data-ttu-id="649ff-192">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="649ff-192">Test/xUnit</span></span>                            | <span data-ttu-id="649ff-193">1.0</span><span class="sxs-lookup"><span data-stu-id="649ff-193">1.0</span></span>        |
| <span data-ttu-id="649ff-194">Razor bileşeni</span><span class="sxs-lookup"><span data-stu-id="649ff-194">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="649ff-195">Þ</span><span class="sxs-lookup"><span data-stu-id="649ff-195">[C#]</span></span>         | <span data-ttu-id="649ff-196">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="649ff-196">Web/ASP.NET</span></span>                           | <span data-ttu-id="649ff-197">3.0</span><span class="sxs-lookup"><span data-stu-id="649ff-197">3.0</span></span>        |
| <span data-ttu-id="649ff-198">Razor sayfası</span><span class="sxs-lookup"><span data-stu-id="649ff-198">Razor Page</span></span>                                   | [<span data-ttu-id="649ff-199">sayfasında</span><span class="sxs-lookup"><span data-stu-id="649ff-199">page</span></span>](#page)                   | <span data-ttu-id="649ff-200">Þ</span><span class="sxs-lookup"><span data-stu-id="649ff-200">[C#]</span></span>         | <span data-ttu-id="649ff-201">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="649ff-201">Web/ASP.NET</span></span>                           | <span data-ttu-id="649ff-202">2.0</span><span class="sxs-lookup"><span data-stu-id="649ff-202">2.0</span></span>        |
| <span data-ttu-id="649ff-203">MVC Viewıtemts</span><span class="sxs-lookup"><span data-stu-id="649ff-203">MVC ViewImports</span></span>                              | [<span data-ttu-id="649ff-204">viewıtems 'lar</span><span class="sxs-lookup"><span data-stu-id="649ff-204">viewimports</span></span>](#namespace)       | <span data-ttu-id="649ff-205">Þ</span><span class="sxs-lookup"><span data-stu-id="649ff-205">[C#]</span></span>         | <span data-ttu-id="649ff-206">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="649ff-206">Web/ASP.NET</span></span>                           | <span data-ttu-id="649ff-207">2.0</span><span class="sxs-lookup"><span data-stu-id="649ff-207">2.0</span></span>        |
| <span data-ttu-id="649ff-208">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="649ff-208">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="649ff-209">Þ</span><span class="sxs-lookup"><span data-stu-id="649ff-209">[C#]</span></span>         | <span data-ttu-id="649ff-210">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="649ff-210">Web/ASP.NET</span></span>                           | <span data-ttu-id="649ff-211">2.0</span><span class="sxs-lookup"><span data-stu-id="649ff-211">2.0</span></span>        |
| <span data-ttu-id="649ff-212">Blazor sunucusu uygulaması</span><span class="sxs-lookup"><span data-stu-id="649ff-212">Blazor Server App</span></span>                            | [<span data-ttu-id="649ff-213">blazorserver</span><span class="sxs-lookup"><span data-stu-id="649ff-213">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="649ff-214">Þ</span><span class="sxs-lookup"><span data-stu-id="649ff-214">[C#]</span></span>         | <span data-ttu-id="649ff-215">Web/Blazor</span><span class="sxs-lookup"><span data-stu-id="649ff-215">Web/Blazor</span></span>                            | <span data-ttu-id="649ff-216">3.0</span><span class="sxs-lookup"><span data-stu-id="649ff-216">3.0</span></span>        |
| <span data-ttu-id="649ff-217">ASP.NET Core boş</span><span class="sxs-lookup"><span data-stu-id="649ff-217">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="649ff-218">Web</span><span class="sxs-lookup"><span data-stu-id="649ff-218">web</span></span>](#web)                     | <span data-ttu-id="649ff-219">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="649ff-219">[C#], F#</span></span>     | <span data-ttu-id="649ff-220">Web/boş</span><span class="sxs-lookup"><span data-stu-id="649ff-220">Web/Empty</span></span>                             | <span data-ttu-id="649ff-221">1.0</span><span class="sxs-lookup"><span data-stu-id="649ff-221">1.0</span></span>        |
| <span data-ttu-id="649ff-222">ASP.NET Core Web uygulaması (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="649ff-222">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="649ff-223">MVC</span><span class="sxs-lookup"><span data-stu-id="649ff-223">mvc</span></span>](#web-options)             | <span data-ttu-id="649ff-224">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="649ff-224">[C#], F#</span></span>     | <span data-ttu-id="649ff-225">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="649ff-225">Web/MVC</span></span>                               | <span data-ttu-id="649ff-226">1.0</span><span class="sxs-lookup"><span data-stu-id="649ff-226">1.0</span></span>        |
| <span data-ttu-id="649ff-227">ASP.NET Core Web uygulaması</span><span class="sxs-lookup"><span data-stu-id="649ff-227">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="649ff-228">WEBAPP, Razor</span><span class="sxs-lookup"><span data-stu-id="649ff-228">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="649ff-229">Þ</span><span class="sxs-lookup"><span data-stu-id="649ff-229">[C#]</span></span>         | <span data-ttu-id="649ff-230">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="649ff-230">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="649ff-231">2,2, 2,0</span><span class="sxs-lookup"><span data-stu-id="649ff-231">2.2, 2.0</span></span>   |
| <span data-ttu-id="649ff-232">Angular ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="649ff-232">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="649ff-233">Angular</span><span class="sxs-lookup"><span data-stu-id="649ff-233">angular</span></span>](#spa)                 | <span data-ttu-id="649ff-234">Þ</span><span class="sxs-lookup"><span data-stu-id="649ff-234">[C#]</span></span>         | <span data-ttu-id="649ff-235">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="649ff-235">Web/MVC/SPA</span></span>                           | <span data-ttu-id="649ff-236">2.0</span><span class="sxs-lookup"><span data-stu-id="649ff-236">2.0</span></span>        |
| <span data-ttu-id="649ff-237">Tepki verme. js ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="649ff-237">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="649ff-238">tıkla</span><span class="sxs-lookup"><span data-stu-id="649ff-238">react</span></span>](#spa)                   | <span data-ttu-id="649ff-239">Þ</span><span class="sxs-lookup"><span data-stu-id="649ff-239">[C#]</span></span>         | <span data-ttu-id="649ff-240">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="649ff-240">Web/MVC/SPA</span></span>                           | <span data-ttu-id="649ff-241">2.0</span><span class="sxs-lookup"><span data-stu-id="649ff-241">2.0</span></span>        |
| <span data-ttu-id="649ff-242">Yanıt verir. js ve Redux ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="649ff-242">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="649ff-243">reactredux</span><span class="sxs-lookup"><span data-stu-id="649ff-243">reactredux</span></span>](#reactredux)       | <span data-ttu-id="649ff-244">Þ</span><span class="sxs-lookup"><span data-stu-id="649ff-244">[C#]</span></span>         | <span data-ttu-id="649ff-245">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="649ff-245">Web/MVC/SPA</span></span>                           | <span data-ttu-id="649ff-246">2.0</span><span class="sxs-lookup"><span data-stu-id="649ff-246">2.0</span></span>        |
| <span data-ttu-id="649ff-247">Razor sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="649ff-247">Razor Class Library</span></span>                          | [<span data-ttu-id="649ff-248">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="649ff-248">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="649ff-249">Þ</span><span class="sxs-lookup"><span data-stu-id="649ff-249">[C#]</span></span>         | <span data-ttu-id="649ff-250">Web/Razor/kitaplık/Razor sınıfı kitaplığı</span><span class="sxs-lookup"><span data-stu-id="649ff-250">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="649ff-251">2.1</span><span class="sxs-lookup"><span data-stu-id="649ff-251">2.1</span></span>        |
| <span data-ttu-id="649ff-252">ASP.NET Core Web API'si</span><span class="sxs-lookup"><span data-stu-id="649ff-252">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="649ff-253">WebApi</span><span class="sxs-lookup"><span data-stu-id="649ff-253">webapi</span></span>](#webapi)               | <span data-ttu-id="649ff-254">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="649ff-254">[C#], F#</span></span>     | <span data-ttu-id="649ff-255">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="649ff-255">Web/WebAPI</span></span>                            | <span data-ttu-id="649ff-256">1.0</span><span class="sxs-lookup"><span data-stu-id="649ff-256">1.0</span></span>        |
| <span data-ttu-id="649ff-257">ASP.NET Core gRPC hizmeti</span><span class="sxs-lookup"><span data-stu-id="649ff-257">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="649ff-258">GRPC</span><span class="sxs-lookup"><span data-stu-id="649ff-258">grpc</span></span>](#web-others)             | <span data-ttu-id="649ff-259">Þ</span><span class="sxs-lookup"><span data-stu-id="649ff-259">[C#]</span></span>         | <span data-ttu-id="649ff-260">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="649ff-260">Web/gRPC</span></span>                              | <span data-ttu-id="649ff-261">3.0</span><span class="sxs-lookup"><span data-stu-id="649ff-261">3.0</span></span>        |
| <span data-ttu-id="649ff-262">DotNet gitignore dosyası</span><span class="sxs-lookup"><span data-stu-id="649ff-262">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="649ff-263">Config</span><span class="sxs-lookup"><span data-stu-id="649ff-263">Config</span></span>                                | <span data-ttu-id="649ff-264">3.0</span><span class="sxs-lookup"><span data-stu-id="649ff-264">3.0</span></span>        |
| <span data-ttu-id="649ff-265">Global. JSON dosyası</span><span class="sxs-lookup"><span data-stu-id="649ff-265">global.json file</span></span>                             | [<span data-ttu-id="649ff-266">globaljson</span><span class="sxs-lookup"><span data-stu-id="649ff-266">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="649ff-267">Config</span><span class="sxs-lookup"><span data-stu-id="649ff-267">Config</span></span>                                | <span data-ttu-id="649ff-268">2.0</span><span class="sxs-lookup"><span data-stu-id="649ff-268">2.0</span></span>        |
| <span data-ttu-id="649ff-269">NuGet yapılandırması</span><span class="sxs-lookup"><span data-stu-id="649ff-269">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="649ff-270">Config</span><span class="sxs-lookup"><span data-stu-id="649ff-270">Config</span></span>                                | <span data-ttu-id="649ff-271">1.0</span><span class="sxs-lookup"><span data-stu-id="649ff-271">1.0</span></span>        |
| <span data-ttu-id="649ff-272">DotNet yerel araç bildirim dosyası</span><span class="sxs-lookup"><span data-stu-id="649ff-272">Dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="649ff-273">Config</span><span class="sxs-lookup"><span data-stu-id="649ff-273">Config</span></span>                                | <span data-ttu-id="649ff-274">3.0</span><span class="sxs-lookup"><span data-stu-id="649ff-274">3.0</span></span>        |
| <span data-ttu-id="649ff-275">Web yapılandırması</span><span class="sxs-lookup"><span data-stu-id="649ff-275">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="649ff-276">Config</span><span class="sxs-lookup"><span data-stu-id="649ff-276">Config</span></span>                                | <span data-ttu-id="649ff-277">1.0</span><span class="sxs-lookup"><span data-stu-id="649ff-277">1.0</span></span>        |
| <span data-ttu-id="649ff-278">Çözüm dosyası</span><span class="sxs-lookup"><span data-stu-id="649ff-278">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="649ff-279">Çözüm</span><span class="sxs-lookup"><span data-stu-id="649ff-279">Solution</span></span>                              | <span data-ttu-id="649ff-280">1.0</span><span class="sxs-lookup"><span data-stu-id="649ff-280">1.0</span></span>        |
| <span data-ttu-id="649ff-281">Protokol arabelleği dosyası</span><span class="sxs-lookup"><span data-stu-id="649ff-281">Protocol Buffer File</span></span>                         | [<span data-ttu-id="649ff-282">proto</span><span class="sxs-lookup"><span data-stu-id="649ff-282">proto</span></span>](#namespace)             |              | <span data-ttu-id="649ff-283">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="649ff-283">Web/gRPC</span></span>                              | <span data-ttu-id="649ff-284">3.0</span><span class="sxs-lookup"><span data-stu-id="649ff-284">3.0</span></span>        |

## <a name="options"></a><span data-ttu-id="649ff-285">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="649ff-285">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="649ff-286">Bir şablon oluşturulmasına neden olacaksa, verilen komutun çalıştırılması durumunda ne olacağını gösteren bir Özet görüntüler.</span><span class="sxs-lookup"><span data-stu-id="649ff-286">Displays a summary of what would happen if the given command were run if it would result in a template creation.</span></span> <span data-ttu-id="649ff-287">.NET Core 2,2 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="649ff-287">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="649ff-288">Var olan dosyaları değiştirebilse bile içeriğin oluşturulmasını zorlar.</span><span class="sxs-lookup"><span data-stu-id="649ff-288">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="649ff-289">Seçilen şablon çıkış dizinindeki mevcut dosyaları geçersiz kılacağından bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="649ff-289">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="649ff-290">Komut için yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="649ff-290">Prints out help for the command.</span></span> <span data-ttu-id="649ff-291">`dotnet new`Komutun kendisi veya herhangi bir şablon için çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="649ff-291">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="649ff-292">Örneğin, `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="649ff-292">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="649ff-293">Veya tarafından belirtilen bir şablon paketini `PATH` kurar `NUGET_ID` .</span><span class="sxs-lookup"><span data-stu-id="649ff-293">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="649ff-294">Şablon paketinin bir ön sürümü sürümünü yüklemek istiyorsanız, sürümü biçiminde belirtmeniz gerekir `<package-name>::<package-version>` .</span><span class="sxs-lookup"><span data-stu-id="649ff-294">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="649ff-295">Varsayılan olarak, `dotnet new` \* en son kararlı paket sürümünü temsil eden sürüm için geçirir.</span><span class="sxs-lookup"><span data-stu-id="649ff-295">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="649ff-296">[Örnekler](#examples) bölümündeki bir örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="649ff-296">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="649ff-297">Bu komutu çalıştırdığınızda şablonun bir sürümü zaten yüklüyse, şablon belirtilen sürüme veya sürüm belirtilmemişse en son kararlı sürüme güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="649ff-297">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="649ff-298">Özel şablonlar oluşturma hakkında daha fazla bilgi için bkz. [DotNet New Için özel şablonlar](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="649ff-298">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="649ff-299">Belirtilen adı içeren şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="649ff-299">Lists templates containing the specified name.</span></span> <span data-ttu-id="649ff-300">Ad belirtilmemişse, tüm şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="649ff-300">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="649ff-301">Oluşturulacak şablonun dili.</span><span class="sxs-lookup"><span data-stu-id="649ff-301">The language of the template to create.</span></span> <span data-ttu-id="649ff-302">Kabul edilen dil şablona göre değişir (bkz. [arguments](#arguments) bölümünde Varsayılanlar).</span><span class="sxs-lookup"><span data-stu-id="649ff-302">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="649ff-303">Bazı şablonlar için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="649ff-303">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="649ff-304">Bazı kabuklar `#` özel bir karakter olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="649ff-304">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="649ff-305">Bu durumlarda, dil parametre değerini tırnak içine alın.</span><span class="sxs-lookup"><span data-stu-id="649ff-305">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="649ff-306">Örneğin, `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="649ff-306">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="649ff-307">Oluşturulan çıkışın adı.</span><span class="sxs-lookup"><span data-stu-id="649ff-307">The name for the created output.</span></span> <span data-ttu-id="649ff-308">Ad belirtilmemişse, geçerli dizinin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="649ff-308">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source <SOURCE>`**

  <span data-ttu-id="649ff-309">Yüklemesi sırasında kullanılacak bir NuGet kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="649ff-309">Specifies a NuGet source to use during install.</span></span> <span data-ttu-id="649ff-310">.NET Core 2,1 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="649ff-310">Available since .NET Core 2.1 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="649ff-311">Oluşturulan çıkışın yerleştirileceği konum.</span><span class="sxs-lookup"><span data-stu-id="649ff-311">Location to place the generated output.</span></span> <span data-ttu-id="649ff-312">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="649ff-312">The default is the current directory.</span></span>

- **`--type <TYPE>`**

  <span data-ttu-id="649ff-313">Şablonları kullanılabilir türlerine göre filtreler.</span><span class="sxs-lookup"><span data-stu-id="649ff-313">Filters templates based on available types.</span></span> <span data-ttu-id="649ff-314">Önceden tanımlanmış değerler `project` , `item` , ve `other` .</span><span class="sxs-lookup"><span data-stu-id="649ff-314">Predefined values are `project`, `item`, and `other`.</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="649ff-315">Veya belirtilen bir şablon paketini kaldırır `PATH` `NUGET_ID` .</span><span class="sxs-lookup"><span data-stu-id="649ff-315">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="649ff-316">`<PATH|NUGET_ID>`Değer belirtilmediğinde, yüklü olan tüm şablon paketleri ve bunlarla ilişkili şablonlar görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="649ff-316">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="649ff-317">Belirtirken `NUGET_ID` , sürüm numarasını eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="649ff-317">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="649ff-318">Bu seçeneğe bir parametre belirtmezseniz, komut, yüklü şablonları ve bunlarla ilgili ayrıntıları listeler.</span><span class="sxs-lookup"><span data-stu-id="649ff-318">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="649ff-319">Bir şablonu kullanarak kaldırmak için `PATH` , yolu tam olarak nitelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="649ff-319">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="649ff-320">Örneğin, *C:/kullanıcıları/ \< Kullanıcı>/Documents/Templates/garciasoftware.consoletemplate.CSharp* çalışır, ancak içeren klasörden *./GarciaSoftware.ConsoleTemplate.CSharp* olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="649ff-320">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="649ff-321">Şablon yolunuzda son Sonlandırıcı Dizin eğik çizgisi eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="649ff-321">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="649ff-322">Şu anda yüklü olan şablon paketleri için kullanılabilir güncelleştirmelerin olup olmadığını denetler ve bunları kurar.</span><span class="sxs-lookup"><span data-stu-id="649ff-322">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="649ff-323">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="649ff-323">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="649ff-324">Şu anda yüklü olan şablon paketleri için kullanılabilir güncelleştirmeler olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="649ff-324">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="649ff-325">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="649ff-325">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="649ff-326">Şablon seçenekleri</span><span class="sxs-lookup"><span data-stu-id="649ff-326">Template options</span></span>

<span data-ttu-id="649ff-327">Her proje şablonunda ek seçenekler bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="649ff-327">Each project template may have additional options available.</span></span> <span data-ttu-id="649ff-328">Çekirdek şablonlar aşağıdaki ek seçeneklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="649ff-328">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="649ff-329">console</span><span class="sxs-lookup"><span data-stu-id="649ff-329">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="649ff-330">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="649ff-330">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="649ff-331">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="649ff-331">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="649ff-332">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="649ff-332">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="649ff-333">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="649ff-333">SDK version</span></span> | <span data-ttu-id="649ff-334">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="649ff-334">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="649ff-335">3,1</span><span class="sxs-lookup"><span data-stu-id="649ff-335">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="649ff-336">3.0</span><span class="sxs-lookup"><span data-stu-id="649ff-336">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="649ff-337">`LangVersion`Oluşturulan proje dosyasındaki özelliği ayarlar.</span><span class="sxs-lookup"><span data-stu-id="649ff-337">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="649ff-338">Örneğin, `--langVersion 7.3` C# 7,3 kullanmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="649ff-338">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="649ff-339">F # için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="649ff-339">Not supported for F#.</span></span> <span data-ttu-id="649ff-340">.NET Core 2,2 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="649ff-340">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="649ff-341">Varsayılan C# sürümlerinin listesi için bkz. [Varsayılanlar](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="649ff-341">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="649ff-342">Belirtilmişse, proje oluşturma sırasında örtük geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="649ff-342">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="649ff-343">.NET Core 2,2 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="649ff-343">Available since .NET Core 2.2 SDK.</span></span>

***

### <a name="classlib"></a><span data-ttu-id="649ff-344">projesinin</span><span class="sxs-lookup"><span data-stu-id="649ff-344">classlib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="649ff-345">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="649ff-345">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="649ff-346">Değerler: `netcoreapp<version>` bir .NET Core sınıf kitaplığı oluşturmak veya `netstandard<version>` bir .NET Standard sınıf kitaplığı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="649ff-346">Values: `netcoreapp<version>` to create a .NET Core Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="649ff-347">Varsayılan değer: `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="649ff-347">The default value is `netstandard2.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="649ff-348">`LangVersion`Oluşturulan proje dosyasındaki özelliği ayarlar.</span><span class="sxs-lookup"><span data-stu-id="649ff-348">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="649ff-349">Örneğin, `--langVersion 7.3` C# 7,3 kullanmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="649ff-349">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="649ff-350">F # için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="649ff-350">Not supported for F#.</span></span> <span data-ttu-id="649ff-351">.NET Core 2,2 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="649ff-351">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="649ff-352">Varsayılan C# sürümlerinin listesi için bkz. [Varsayılanlar](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="649ff-352">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="649ff-353">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="649ff-353">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="wpf-wpflib-wpfcustomcontrollib-wpfusercontrollib"></a><a name="wpf"></a><span data-ttu-id="649ff-354">WPF, wpflib, wpfcustomcontrollib, wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="649ff-354">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="649ff-355">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="649ff-355">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="649ff-356">Varsayılan değer: `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="649ff-356">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="649ff-357">.NET Core 3,1 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="649ff-357">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="649ff-358">`LangVersion`Oluşturulan proje dosyasındaki özelliği ayarlar.</span><span class="sxs-lookup"><span data-stu-id="649ff-358">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="649ff-359">Örneğin, `--langVersion 7.3` C# 7,3 kullanmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="649ff-359">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="649ff-360">Varsayılan C# sürümlerinin listesi için bkz. [Varsayılanlar](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="649ff-360">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="649ff-361">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="649ff-361">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="winforms-winformslib"></a><a name="winforms"></a><span data-ttu-id="649ff-362">WinForms, winformslib</span><span class="sxs-lookup"><span data-stu-id="649ff-362">winforms, winformslib</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="649ff-363">`LangVersion`Oluşturulan proje dosyasındaki özelliği ayarlar.</span><span class="sxs-lookup"><span data-stu-id="649ff-363">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="649ff-364">Örneğin, `--langVersion 7.3` C# 7,3 kullanmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="649ff-364">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="649ff-365">Varsayılan C# sürümlerinin listesi için bkz. [Varsayılanlar](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="649ff-365">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="649ff-366">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="649ff-366">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="worker-grpc"></a><a name="web-others"></a><span data-ttu-id="649ff-367">çalışan, GRPC</span><span class="sxs-lookup"><span data-stu-id="649ff-367">worker, grpc</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="649ff-368">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="649ff-368">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="649ff-369">Varsayılan değer: `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="649ff-369">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="649ff-370">.NET Core 3,1 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="649ff-370">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="649ff-371">Oluşturulan şablondan *Launchsettings. JSON* öğesini dışlar.</span><span class="sxs-lookup"><span data-stu-id="649ff-371">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="649ff-372">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="649ff-372">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="mstest-xunit"></a><a name="test"></a><span data-ttu-id="649ff-373">MSTest, xUnit</span><span class="sxs-lookup"><span data-stu-id="649ff-373">mstest, xunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="649ff-374">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="649ff-374">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="649ff-375">.NET Core 3,0 SDK 'dan beri kullanılabilir seçeneği.</span><span class="sxs-lookup"><span data-stu-id="649ff-375">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="649ff-376">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="649ff-376">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="649ff-377">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="649ff-377">SDK version</span></span> | <span data-ttu-id="649ff-378">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="649ff-378">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="649ff-379">3,1</span><span class="sxs-lookup"><span data-stu-id="649ff-379">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="649ff-380">3.0</span><span class="sxs-lookup"><span data-stu-id="649ff-380">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="649ff-381">[DotNet Pack](dotnet-pack.md)kullanarak proje için paketleme imkanı sunar.</span><span class="sxs-lookup"><span data-stu-id="649ff-381">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="649ff-382">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="649ff-382">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="nunit"></a><span data-ttu-id="649ff-383">NUnit</span><span class="sxs-lookup"><span data-stu-id="649ff-383">nunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="649ff-384">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="649ff-384">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="649ff-385">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="649ff-385">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="649ff-386">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="649ff-386">SDK version</span></span> | <span data-ttu-id="649ff-387">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="649ff-387">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="649ff-388">3,1</span><span class="sxs-lookup"><span data-stu-id="649ff-388">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="649ff-389">3.0</span><span class="sxs-lookup"><span data-stu-id="649ff-389">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="649ff-390">2,2</span><span class="sxs-lookup"><span data-stu-id="649ff-390">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="649ff-391">2.1</span><span class="sxs-lookup"><span data-stu-id="649ff-391">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="649ff-392">[DotNet Pack](dotnet-pack.md)kullanarak proje için paketleme imkanı sunar.</span><span class="sxs-lookup"><span data-stu-id="649ff-392">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="649ff-393">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="649ff-393">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="page"></a><span data-ttu-id="649ff-394">sayfasında</span><span class="sxs-lookup"><span data-stu-id="649ff-394">page</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="649ff-395">Oluşturulan kod için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="649ff-395">Namespace for the generated code.</span></span> <span data-ttu-id="649ff-396">Varsayılan değer: `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="649ff-396">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="649ff-397">PageModel olmadan sayfayı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="649ff-397">Creates the page without a PageModel.</span></span>

***

### <a name="viewimports-proto"></a><a name="namespace"></a><span data-ttu-id="649ff-398">viewıtemler, Proto</span><span class="sxs-lookup"><span data-stu-id="649ff-398">viewimports, proto</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="649ff-399">Oluşturulan kod için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="649ff-399">Namespace for the generated code.</span></span> <span data-ttu-id="649ff-400">Varsayılan değer: `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="649ff-400">The default value is `MyApp.Namespace`.</span></span>

***

### <a name="blazorserver"></a><span data-ttu-id="649ff-401">blazorserver</span><span class="sxs-lookup"><span data-stu-id="649ff-401">blazorserver</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="649ff-402">Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="649ff-402">The type of authentication to use.</span></span> <span data-ttu-id="649ff-403">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="649ff-403">The possible values are:</span></span>

  - <span data-ttu-id="649ff-404">`None`-Kimlik doğrulaması yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="649ff-404">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="649ff-405">`Individual`-Bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="649ff-405">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="649ff-406">`IndividualB2C`-Azure AD B2C ile bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="649ff-406">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="649ff-407">`SingleOrg`-Tek bir kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="649ff-407">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="649ff-408">`MultiOrg`-Birden çok kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="649ff-408">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="649ff-409">`Windows`-Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="649ff-409">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="649ff-410">Bağlanılacak Azure Active Directory B2C örneği.</span><span class="sxs-lookup"><span data-stu-id="649ff-410">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="649ff-411">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="649ff-411">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="649ff-412">Varsayılan değer: `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="649ff-412">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="649ff-413">Bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="649ff-413">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="649ff-414">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="649ff-414">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="649ff-415">Bu proje için parola sıfırlama ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="649ff-415">The reset password policy ID for this project.</span></span> <span data-ttu-id="649ff-416">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="649ff-416">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="649ff-417">Bu proje için profil ilke KIMLIĞINI Düzenle.</span><span class="sxs-lookup"><span data-stu-id="649ff-417">The edit profile policy ID for this project.</span></span> <span data-ttu-id="649ff-418">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="649ff-418">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="649ff-419">Bağlanılacak Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="649ff-419">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="649ff-420">`SingleOrg`Veya `MultiOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="649ff-420">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="649ff-421">Varsayılan değer: `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="649ff-421">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="649ff-422">Bu projenin Istemci KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="649ff-422">The Client ID for this project.</span></span> <span data-ttu-id="649ff-423">`IndividualB2C`, `SingleOrg` Veya `MultiOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="649ff-423">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="649ff-424">Varsayılan değer: `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="649ff-424">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="649ff-425">Dizin kiracının etki alanı.</span><span class="sxs-lookup"><span data-stu-id="649ff-425">The domain for the directory tenant.</span></span> <span data-ttu-id="649ff-426">`SingleOrg`Veya `IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="649ff-426">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="649ff-427">Varsayılan değer: `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="649ff-427">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="649ff-428">Bağlanılacak dizinin Tenantıd KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="649ff-428">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="649ff-429">`SingleOrg`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="649ff-429">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="649ff-430">Varsayılan değer: `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="649ff-430">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="649ff-431">Uygulamanın yeniden yönlendirme URI 'sinin temel yolundaki istek yolu.</span><span class="sxs-lookup"><span data-stu-id="649ff-431">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="649ff-432">`SingleOrg`Veya `IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="649ff-432">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="649ff-433">Varsayılan değer: `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="649ff-433">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="649ff-434">Bu uygulamanın dizine okuma erişimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="649ff-434">Allows this application read-access to the directory.</span></span> <span data-ttu-id="649ff-435">Yalnızca `SingleOrg` veya `MultiOrg` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="649ff-435">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="649ff-436">Oluşturulan şablondan *Launchsettings. JSON* öğesini dışlar.</span><span class="sxs-lookup"><span data-stu-id="649ff-436">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="649ff-437">HTTPS 'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="649ff-437">Turns off HTTPS.</span></span> <span data-ttu-id="649ff-438">Bu seçenek yalnızca,, `Individual` , `IndividualB2C` `SingleOrg` veya için kullanılmıyorsa geçerlidir `MultiOrg` `--auth` .</span><span class="sxs-lookup"><span data-stu-id="649ff-438">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="649ff-439">SQLite yerine LocalDB kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="649ff-439">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="649ff-440">Yalnızca `Individual` veya `IndividualB2C` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="649ff-440">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="649ff-441">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="649ff-441">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web"></a><span data-ttu-id="649ff-442">web</span><span class="sxs-lookup"><span data-stu-id="649ff-442">web</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="649ff-443">Oluşturulan şablondan *Launchsettings. JSON* öğesini dışlar.</span><span class="sxs-lookup"><span data-stu-id="649ff-443">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="649ff-444">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="649ff-444">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="649ff-445">Seçenek .NET Core 2,2 SDK sürümünde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="649ff-445">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="649ff-446">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="649ff-446">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="649ff-447">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="649ff-447">SDK version</span></span> | <span data-ttu-id="649ff-448">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="649ff-448">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="649ff-449">3,1</span><span class="sxs-lookup"><span data-stu-id="649ff-449">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="649ff-450">3.0</span><span class="sxs-lookup"><span data-stu-id="649ff-450">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="649ff-451">2.1</span><span class="sxs-lookup"><span data-stu-id="649ff-451">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="649ff-452">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="649ff-452">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="649ff-453">HTTPS 'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="649ff-453">Turns off HTTPS.</span></span>

***

### <a name="mvc-webapp"></a><a name="web-options"></a><span data-ttu-id="649ff-454">MVC, WebApp</span><span class="sxs-lookup"><span data-stu-id="649ff-454">mvc, webapp</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="649ff-455">Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="649ff-455">The type of authentication to use.</span></span> <span data-ttu-id="649ff-456">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="649ff-456">The possible values are:</span></span>

  - <span data-ttu-id="649ff-457">`None`-Kimlik doğrulaması yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="649ff-457">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="649ff-458">`Individual`-Bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="649ff-458">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="649ff-459">`IndividualB2C`-Azure AD B2C ile bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="649ff-459">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="649ff-460">`SingleOrg`-Tek bir kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="649ff-460">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="649ff-461">`MultiOrg`-Birden çok kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="649ff-461">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="649ff-462">`Windows`-Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="649ff-462">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="649ff-463">Bağlanılacak Azure Active Directory B2C örneği.</span><span class="sxs-lookup"><span data-stu-id="649ff-463">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="649ff-464">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="649ff-464">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="649ff-465">Varsayılan değer: `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="649ff-465">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="649ff-466">Bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="649ff-466">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="649ff-467">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="649ff-467">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="649ff-468">Bu proje için parola sıfırlama ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="649ff-468">The reset password policy ID for this project.</span></span> <span data-ttu-id="649ff-469">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="649ff-469">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="649ff-470">Bu proje için profil ilke KIMLIĞINI Düzenle.</span><span class="sxs-lookup"><span data-stu-id="649ff-470">The edit profile policy ID for this project.</span></span> <span data-ttu-id="649ff-471">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="649ff-471">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="649ff-472">Bağlanılacak Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="649ff-472">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="649ff-473">`SingleOrg`Veya `MultiOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="649ff-473">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="649ff-474">Varsayılan değer: `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="649ff-474">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="649ff-475">Bu projenin Istemci KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="649ff-475">The Client ID for this project.</span></span> <span data-ttu-id="649ff-476">`IndividualB2C`, `SingleOrg` Veya `MultiOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="649ff-476">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="649ff-477">Varsayılan değer: `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="649ff-477">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="649ff-478">Dizin kiracının etki alanı.</span><span class="sxs-lookup"><span data-stu-id="649ff-478">The domain for the directory tenant.</span></span> <span data-ttu-id="649ff-479">`SingleOrg`Veya `IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="649ff-479">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="649ff-480">Varsayılan değer: `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="649ff-480">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="649ff-481">Bağlanılacak dizinin Tenantıd KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="649ff-481">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="649ff-482">`SingleOrg`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="649ff-482">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="649ff-483">Varsayılan değer: `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="649ff-483">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="649ff-484">Uygulamanın yeniden yönlendirme URI 'sinin temel yolundaki istek yolu.</span><span class="sxs-lookup"><span data-stu-id="649ff-484">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="649ff-485">`SingleOrg`Veya `IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="649ff-485">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="649ff-486">Varsayılan değer: `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="649ff-486">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="649ff-487">Bu uygulamanın dizine okuma erişimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="649ff-487">Allows this application read-access to the directory.</span></span> <span data-ttu-id="649ff-488">Yalnızca `SingleOrg` veya `MultiOrg` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="649ff-488">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="649ff-489">Oluşturulan şablondan *Launchsettings. JSON* öğesini dışlar.</span><span class="sxs-lookup"><span data-stu-id="649ff-489">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="649ff-490">HTTPS 'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="649ff-490">Turns off HTTPS.</span></span> <span data-ttu-id="649ff-491">Bu seçenek yalnızca,,, veya kullanılmıyorsa geçerlidir `Individual` `IndividualB2C` `SingleOrg` `MultiOrg` .</span><span class="sxs-lookup"><span data-stu-id="649ff-491">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="649ff-492">SQLite yerine LocalDB kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="649ff-492">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="649ff-493">Yalnızca `Individual` veya `IndividualB2C` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="649ff-493">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="649ff-494">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="649ff-494">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="649ff-495">.NET Core 3,0 SDK 'dan beri kullanılabilir seçeneği.</span><span class="sxs-lookup"><span data-stu-id="649ff-495">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="649ff-496">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="649ff-496">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="649ff-497">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="649ff-497">SDK version</span></span> | <span data-ttu-id="649ff-498">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="649ff-498">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="649ff-499">3,1</span><span class="sxs-lookup"><span data-stu-id="649ff-499">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="649ff-500">3.0</span><span class="sxs-lookup"><span data-stu-id="649ff-500">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="649ff-501">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="649ff-501">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="649ff-502">Projedeki BrowserLink öğesini içerir.</span><span class="sxs-lookup"><span data-stu-id="649ff-502">Includes BrowserLink in the project.</span></span> <span data-ttu-id="649ff-503">Seçenek .NET Core 2,2 ve 3,1 SDK sürümünde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="649ff-503">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

- **`-rrc|--razor-runtime-compilation`**

  <span data-ttu-id="649ff-504">Projenin hata ayıklama yapılarında [Razor çalışma zamanı derlemesini](/aspnet/core/mvc/views/view-compilation#runtime-compilation) kullanmak üzere yapılandırılıp yapılandırılmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="649ff-504">Determines if the project is configured to use [Razor runtime compilation](/aspnet/core/mvc/views/view-compilation#runtime-compilation) in Debug builds.</span></span> <span data-ttu-id="649ff-505">.NET Core 3.1.201 SDK 'dan beri kullanılabilir seçeneği.</span><span class="sxs-lookup"><span data-stu-id="649ff-505">Option available since .NET Core 3.1.201 SDK.</span></span>

***

### <a name="angular-react"></a><a name="spa"></a><span data-ttu-id="649ff-506">Angular, tepki verme</span><span class="sxs-lookup"><span data-stu-id="649ff-506">angular, react</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="649ff-507">Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="649ff-507">The type of authentication to use.</span></span> <span data-ttu-id="649ff-508">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="649ff-508">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="649ff-509">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="649ff-509">The possible values are:</span></span>

  - <span data-ttu-id="649ff-510">`None`-Kimlik doğrulaması yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="649ff-510">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="649ff-511">`Individual`-Bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="649ff-511">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="649ff-512">Oluşturulan şablondan *Launchsettings. JSON* öğesini dışlar.</span><span class="sxs-lookup"><span data-stu-id="649ff-512">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="649ff-513">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="649ff-513">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="649ff-514">HTTPS 'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="649ff-514">Turns off HTTPS.</span></span> <span data-ttu-id="649ff-515">Bu seçenek yalnızca kimlik doğrulaması ise geçerlidir `None` .</span><span class="sxs-lookup"><span data-stu-id="649ff-515">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="649ff-516">SQLite yerine LocalDB kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="649ff-516">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="649ff-517">Yalnızca `Individual` veya `IndividualB2C` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="649ff-517">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="649ff-518">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="649ff-518">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="649ff-519">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="649ff-519">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="649ff-520">Seçenek .NET Core 2,2 SDK sürümünde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="649ff-520">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="649ff-521">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="649ff-521">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="649ff-522">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="649ff-522">SDK version</span></span> | <span data-ttu-id="649ff-523">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="649ff-523">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="649ff-524">3,1</span><span class="sxs-lookup"><span data-stu-id="649ff-524">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="649ff-525">3.0</span><span class="sxs-lookup"><span data-stu-id="649ff-525">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="649ff-526">2.1</span><span class="sxs-lookup"><span data-stu-id="649ff-526">2.1</span></span>         | `netcoreapp2.0` |

***

### <a name="reactredux"></a><span data-ttu-id="649ff-527">reactredux</span><span class="sxs-lookup"><span data-stu-id="649ff-527">reactredux</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="649ff-528">Oluşturulan şablondan *Launchsettings. JSON* öğesini dışlar.</span><span class="sxs-lookup"><span data-stu-id="649ff-528">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="649ff-529">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="649ff-529">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="649ff-530">Seçenek .NET Core 2,2 SDK sürümünde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="649ff-530">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="649ff-531">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="649ff-531">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="649ff-532">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="649ff-532">SDK version</span></span> | <span data-ttu-id="649ff-533">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="649ff-533">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="649ff-534">3,1</span><span class="sxs-lookup"><span data-stu-id="649ff-534">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="649ff-535">3.0</span><span class="sxs-lookup"><span data-stu-id="649ff-535">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="649ff-536">2.1</span><span class="sxs-lookup"><span data-stu-id="649ff-536">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="649ff-537">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="649ff-537">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="649ff-538">HTTPS 'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="649ff-538">Turns off HTTPS.</span></span>

***

### <a name="razorclasslib"></a><span data-ttu-id="649ff-539">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="649ff-539">razorclasslib</span></span>

- **`--no-restore`**

  <span data-ttu-id="649ff-540">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="649ff-540">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="649ff-541">, Bu kitaplığa bileşenlere ek olarak geleneksel Razor sayfaları ve görünümleri eklenmesini destekler.</span><span class="sxs-lookup"><span data-stu-id="649ff-541">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="649ff-542">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="649ff-542">Available since .NET Core 3.0 SDK.</span></span>

***
  
### <a name="webapi"></a><span data-ttu-id="649ff-543">WebApi</span><span class="sxs-lookup"><span data-stu-id="649ff-543">webapi</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="649ff-544">Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="649ff-544">The type of authentication to use.</span></span> <span data-ttu-id="649ff-545">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="649ff-545">The possible values are:</span></span>

  - <span data-ttu-id="649ff-546">`None`-Kimlik doğrulaması yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="649ff-546">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="649ff-547">`IndividualB2C`-Azure AD B2C ile bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="649ff-547">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="649ff-548">`SingleOrg`-Tek bir kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="649ff-548">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="649ff-549">`Windows`-Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="649ff-549">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="649ff-550">Bağlanılacak Azure Active Directory B2C örneği.</span><span class="sxs-lookup"><span data-stu-id="649ff-550">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="649ff-551">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="649ff-551">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="649ff-552">Varsayılan değer: `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="649ff-552">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="649ff-553">Bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="649ff-553">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="649ff-554">`IndividualB2C`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="649ff-554">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="649ff-555">Bağlanılacak Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="649ff-555">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="649ff-556">`SingleOrg`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="649ff-556">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="649ff-557">Varsayılan değer: `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="649ff-557">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="649ff-558">Bu projenin Istemci KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="649ff-558">The Client ID for this project.</span></span> <span data-ttu-id="649ff-559">`IndividualB2C`Veya `SingleOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="649ff-559">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="649ff-560">Varsayılan değer: `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="649ff-560">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="649ff-561">Dizin kiracının etki alanı.</span><span class="sxs-lookup"><span data-stu-id="649ff-561">The domain for the directory tenant.</span></span> <span data-ttu-id="649ff-562">`IndividualB2C`Veya `SingleOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="649ff-562">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="649ff-563">Varsayılan değer: `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="649ff-563">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="649ff-564">Bağlanılacak dizinin Tenantıd KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="649ff-564">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="649ff-565">`SingleOrg`Kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="649ff-565">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="649ff-566">Varsayılan değer: `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="649ff-566">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="649ff-567">Bu uygulamanın dizine okuma erişimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="649ff-567">Allows this application read-access to the directory.</span></span> <span data-ttu-id="649ff-568">Yalnızca `SingleOrg` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="649ff-568">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="649ff-569">Oluşturulan şablondan *Launchsettings. JSON* öğesini dışlar.</span><span class="sxs-lookup"><span data-stu-id="649ff-569">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="649ff-570">HTTPS 'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="649ff-570">Turns off HTTPS.</span></span> <span data-ttu-id="649ff-571">`app.UseHsts`ve `app.UseHttpsRedirection` öğesine eklenmez `Startup.Configure` .</span><span class="sxs-lookup"><span data-stu-id="649ff-571">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="649ff-572">Bu seçenek yalnızca `IndividualB2C` `SingleOrg` kimlik doğrulaması için kullanılmıyorsa geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="649ff-572">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="649ff-573">SQLite yerine LocalDB kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="649ff-573">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="649ff-574">Yalnızca `IndividualB2C` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="649ff-574">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="649ff-575">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="649ff-575">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="649ff-576">Seçenek .NET Core 2,2 SDK sürümünde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="649ff-576">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="649ff-577">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="649ff-577">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="649ff-578">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="649ff-578">SDK version</span></span> | <span data-ttu-id="649ff-579">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="649ff-579">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="649ff-580">3,1</span><span class="sxs-lookup"><span data-stu-id="649ff-580">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="649ff-581">3.0</span><span class="sxs-lookup"><span data-stu-id="649ff-581">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="649ff-582">2.1</span><span class="sxs-lookup"><span data-stu-id="649ff-582">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="649ff-583">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="649ff-583">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="globaljson"></a><span data-ttu-id="649ff-584">globaljson</span><span class="sxs-lookup"><span data-stu-id="649ff-584">globaljson</span></span>

- **`--sdk-version <VERSION_NUMBER>`**

  <span data-ttu-id="649ff-585">*Global. JSON* dosyasında kullanılacak .NET Core SDK sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="649ff-585">Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="649ff-586">Örnekler</span><span class="sxs-lookup"><span data-stu-id="649ff-586">Examples</span></span>

- <span data-ttu-id="649ff-587">Şablon adını belirterek bir C# konsol uygulaması projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="649ff-587">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="649ff-588">Geçerli dizinde bir F # konsol uygulaması projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="649ff-588">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang "F#"
  ```

- <span data-ttu-id="649ff-589">Belirtilen dizinde bir .NET Standard sınıf kitaplığı projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="649ff-589">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="649ff-590">Geçerli dizinde kimlik doğrulaması olmadan yeni bir ASP.NET Core C# MVC projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="649ff-590">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="649ff-591">Yeni bir xUnit projesi oluştur:</span><span class="sxs-lookup"><span data-stu-id="649ff-591">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="649ff-592">Tek sayfalı uygulama (SPA) şablonları için kullanılabilen tüm şablonları listeleyin:</span><span class="sxs-lookup"><span data-stu-id="649ff-592">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="649ff-593">*We* alt dizeniz ile eşleşen tüm şablonları listeleyin.</span><span class="sxs-lookup"><span data-stu-id="649ff-593">List all templates matching the *we* substring.</span></span> <span data-ttu-id="649ff-594">Tam eşleşme bulunamadı, bu nedenle alt dize eşleştirmesi hem kısa ad hem de ad sütunlarında çalışır.</span><span class="sxs-lookup"><span data-stu-id="649ff-594">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="649ff-595">Şablonla *eşleşen şablonu*çağırma girişimi.</span><span class="sxs-lookup"><span data-stu-id="649ff-595">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="649ff-596">Tek bir eşleşme belirlenemiyorsa kısmi eşleşen şablonları listeleyin.</span><span class="sxs-lookup"><span data-stu-id="649ff-596">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="649ff-597">ASP.NET Core için SPA şablonlarının 2,0 sürümünü yükler:</span><span class="sxs-lookup"><span data-stu-id="649ff-597">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="649ff-598">Yüklü şablonları ve bunlarla ilgili ayrıntıları, bunları kaldırma dahil olmak üzere listeleyin:</span><span class="sxs-lookup"><span data-stu-id="649ff-598">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="649ff-599">SDK sürümünü 3.1.101 olarak ayarlamak için geçerli dizinde *Global. JSON* oluşturun:</span><span class="sxs-lookup"><span data-stu-id="649ff-599">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="649ff-600">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="649ff-600">See also</span></span>

- [<span data-ttu-id="649ff-601">DotNet New için özel şablonlar</span><span class="sxs-lookup"><span data-stu-id="649ff-601">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="649ff-602">Dotnet new için özel şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="649ff-602">Create a custom template for dotnet new</span></span>](../tutorials/cli-templates-create-item-template.md)
- [<span data-ttu-id="649ff-603">DotNet/DotNet-şablon-örnek GitHub deposu</span><span class="sxs-lookup"><span data-stu-id="649ff-603">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="649ff-604">DotNet New için kullanılabilir şablonlar</span><span class="sxs-lookup"><span data-stu-id="649ff-604">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
