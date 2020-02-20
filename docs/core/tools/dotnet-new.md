---
title: DotNet yeni komut
description: DotNet New komutu, belirtilen şablona göre yeni .NET Core projeleri oluşturur.
ms.date: 02/13/2020
ms.openlocfilehash: f11512acf5a1fdc4bde49b3d1212ccf6335dff8b
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451336"
---
# <a name="dotnet-new"></a><span data-ttu-id="33b05-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="33b05-103">dotnet new</span></span>

<span data-ttu-id="33b05-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,0 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="33b05-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="33b05-105">Name</span><span class="sxs-lookup"><span data-stu-id="33b05-105">Name</span></span>

<span data-ttu-id="33b05-106">`dotnet new`-belirtilen şablona göre yeni bir proje, yapılandırma dosyası veya çözüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="33b05-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="33b05-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="33b05-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install] [-lang|--language] [-n|--name] 
    [--nuget-source] [-o|--output] [-u|--uninstall] [--update-apply] [--update-check] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

## <a name="description"></a><span data-ttu-id="33b05-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="33b05-108">Description</span></span>

<span data-ttu-id="33b05-109">`dotnet new` komutu bir şablonu temel alan bir .NET Core projesi veya diğer yapılar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="33b05-109">The `dotnet new` command creates a .NET Core project or other artifacts based on a template.</span></span>

<span data-ttu-id="33b05-110">Komutu, belirtilen şablon ve seçeneklere göre diskteki yapıtları oluşturmak için [şablon altyapısını](https://github.com/dotnet/templating) çağırır.</span><span class="sxs-lookup"><span data-stu-id="33b05-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="33b05-111">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="33b05-111">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="33b05-112">Komut çağrıldığında örnek oluşturulacak şablon.</span><span class="sxs-lookup"><span data-stu-id="33b05-112">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="33b05-113">Her şablonun geçirebilmeniz için özel seçenekleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="33b05-113">Each template might have specific options you can pass.</span></span> <span data-ttu-id="33b05-114">Daha fazla bilgi için bkz. [şablon seçenekleri](#template-options).</span><span class="sxs-lookup"><span data-stu-id="33b05-114">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="33b05-115">Tüm yüklü şablonların listesini görmek için `dotnet new --list` çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="33b05-115">You can run `dotnet new --list` to see a list of all installed templates.</span></span> <span data-ttu-id="33b05-116">`TEMPLATE` değeri, döndürülen tablodaki **Şablonlar** veya **kısa ad** sütunundaki metinde tam eşleşme değilse, bu iki sütunda bir alt dize eşleşmesi gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="33b05-116">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="33b05-117">.NET Core 3,0 SDK ile başlayarak, CLı, aşağıdaki koşullarda `dotnet new` komutunu çağırdığınızda NuGet.org içindeki şablonları arar:</span><span class="sxs-lookup"><span data-stu-id="33b05-117">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="33b05-118">CLı, `dotnet new`çağrılırken bir şablon eşleşmesi bulamazsa, bu da kısmi değildir.</span><span class="sxs-lookup"><span data-stu-id="33b05-118">If the CLI can’t find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="33b05-119">Şablonun daha yeni bir sürümü kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="33b05-119">If there’s a newer version of the template available.</span></span> <span data-ttu-id="33b05-120">Bu durumda, proje veya yapıt oluşturulur ancak CLı, şablonun güncelleştirilmiş bir sürümü hakkında sizi uyarır.</span><span class="sxs-lookup"><span data-stu-id="33b05-120">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="33b05-121">Komut, şablonların varsayılan bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="33b05-121">The command contains a default list of templates.</span></span> <span data-ttu-id="33b05-122">Kullanılabilir şablonların bir listesini almak için `dotnet new -l` kullanın.</span><span class="sxs-lookup"><span data-stu-id="33b05-122">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="33b05-123">Aşağıdaki tabloda, .NET Core SDK ile önceden yüklenmiş olan şablonlar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="33b05-123">The following table shows the templates that come pre-installed with the .NET Core SDK.</span></span> <span data-ttu-id="33b05-124">Şablon için varsayılan dil, köşeli ayraçlar içinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="33b05-124">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="33b05-125">Özel şablon seçeneklerini görmek için kısa ad bağlantısına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="33b05-125">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="33b05-126">Şablonlar</span><span class="sxs-lookup"><span data-stu-id="33b05-126">Templates</span></span>                                    | <span data-ttu-id="33b05-127">Kısa ad</span><span class="sxs-lookup"><span data-stu-id="33b05-127">Short name</span></span>                      | <span data-ttu-id="33b05-128">Dil</span><span class="sxs-lookup"><span data-stu-id="33b05-128">Language</span></span>     | <span data-ttu-id="33b05-129">Etiketler</span><span class="sxs-lookup"><span data-stu-id="33b05-129">Tags</span></span>                                  | <span data-ttu-id="33b05-130">Dağıtıla</span><span class="sxs-lookup"><span data-stu-id="33b05-130">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="33b05-131">Konsol Uygulaması</span><span class="sxs-lookup"><span data-stu-id="33b05-131">Console Application</span></span>                          | [<span data-ttu-id="33b05-132">konsola</span><span class="sxs-lookup"><span data-stu-id="33b05-132">console</span></span>](#console)             | <span data-ttu-id="33b05-133">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="33b05-133">[C#], F#, VB</span></span> | <span data-ttu-id="33b05-134">Ortak/konsol</span><span class="sxs-lookup"><span data-stu-id="33b05-134">Common/Console</span></span>                        | <span data-ttu-id="33b05-135">1.0</span><span class="sxs-lookup"><span data-stu-id="33b05-135">1.0</span></span>        |
| <span data-ttu-id="33b05-136">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="33b05-136">Class library</span></span>                                | [<span data-ttu-id="33b05-137">projesinin</span><span class="sxs-lookup"><span data-stu-id="33b05-137">classlib</span></span>](#classlib)           | <span data-ttu-id="33b05-138">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="33b05-138">[C#], F#, VB</span></span> | <span data-ttu-id="33b05-139">Ortak/Kitaplık</span><span class="sxs-lookup"><span data-stu-id="33b05-139">Common/Library</span></span>                        | <span data-ttu-id="33b05-140">1.0</span><span class="sxs-lookup"><span data-stu-id="33b05-140">1.0</span></span>        |
| <span data-ttu-id="33b05-141">WPF Uygulaması</span><span class="sxs-lookup"><span data-stu-id="33b05-141">WPF Application</span></span>                              | [<span data-ttu-id="33b05-142">WPF</span><span class="sxs-lookup"><span data-stu-id="33b05-142">wpf</span></span>](#wpf)                     | <span data-ttu-id="33b05-143">[C#]</span><span class="sxs-lookup"><span data-stu-id="33b05-143">[C#]</span></span>         | <span data-ttu-id="33b05-144">Ortak/WPF</span><span class="sxs-lookup"><span data-stu-id="33b05-144">Common/WPF</span></span>                            | <span data-ttu-id="33b05-145">3.0</span><span class="sxs-lookup"><span data-stu-id="33b05-145">3.0</span></span>        |
| <span data-ttu-id="33b05-146">WPF sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="33b05-146">WPF Class library</span></span>                            | [<span data-ttu-id="33b05-147">wpflib</span><span class="sxs-lookup"><span data-stu-id="33b05-147">wpflib</span></span>](#wpf)                  | <span data-ttu-id="33b05-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="33b05-148">[C#]</span></span>         | <span data-ttu-id="33b05-149">Ortak/WPF</span><span class="sxs-lookup"><span data-stu-id="33b05-149">Common/WPF</span></span>                            | <span data-ttu-id="33b05-150">3.0</span><span class="sxs-lookup"><span data-stu-id="33b05-150">3.0</span></span>        |
| <span data-ttu-id="33b05-151">WPF Özel Denetim Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="33b05-151">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="33b05-152">wpfcustomcontrollib</span><span class="sxs-lookup"><span data-stu-id="33b05-152">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="33b05-153">[C#]</span><span class="sxs-lookup"><span data-stu-id="33b05-153">[C#]</span></span>         | <span data-ttu-id="33b05-154">Ortak/WPF</span><span class="sxs-lookup"><span data-stu-id="33b05-154">Common/WPF</span></span>                            | <span data-ttu-id="33b05-155">3.0</span><span class="sxs-lookup"><span data-stu-id="33b05-155">3.0</span></span>        |
| <span data-ttu-id="33b05-156">WPF Kullanıcı Denetimi Kütüphanesi</span><span class="sxs-lookup"><span data-stu-id="33b05-156">WPF User Control Library</span></span>                     | [<span data-ttu-id="33b05-157">wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="33b05-157">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="33b05-158">[C#]</span><span class="sxs-lookup"><span data-stu-id="33b05-158">[C#]</span></span>         | <span data-ttu-id="33b05-159">Ortak/WPF</span><span class="sxs-lookup"><span data-stu-id="33b05-159">Common/WPF</span></span>                            | <span data-ttu-id="33b05-160">3.0</span><span class="sxs-lookup"><span data-stu-id="33b05-160">3.0</span></span>        |
| <span data-ttu-id="33b05-161">Windows Forms (WinForms) uygulaması</span><span class="sxs-lookup"><span data-stu-id="33b05-161">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="33b05-162">WinForms</span><span class="sxs-lookup"><span data-stu-id="33b05-162">winforms</span></span>](#winforms)           | <span data-ttu-id="33b05-163">[C#]</span><span class="sxs-lookup"><span data-stu-id="33b05-163">[C#]</span></span>         | <span data-ttu-id="33b05-164">Ortak/WinForms</span><span class="sxs-lookup"><span data-stu-id="33b05-164">Common/WinForms</span></span>                       | <span data-ttu-id="33b05-165">3.0</span><span class="sxs-lookup"><span data-stu-id="33b05-165">3.0</span></span>        |
| <span data-ttu-id="33b05-166">Windows Forms (WinForms) sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="33b05-166">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="33b05-167">winformslib</span><span class="sxs-lookup"><span data-stu-id="33b05-167">winformslib</span></span>](#winforms)        | <span data-ttu-id="33b05-168">[C#]</span><span class="sxs-lookup"><span data-stu-id="33b05-168">[C#]</span></span>         | <span data-ttu-id="33b05-169">Ortak/WinForms</span><span class="sxs-lookup"><span data-stu-id="33b05-169">Common/WinForms</span></span>                       | <span data-ttu-id="33b05-170">3.0</span><span class="sxs-lookup"><span data-stu-id="33b05-170">3.0</span></span>        |
| <span data-ttu-id="33b05-171">Çalışan hizmeti</span><span class="sxs-lookup"><span data-stu-id="33b05-171">Worker Service</span></span>                               | [<span data-ttu-id="33b05-172">ından</span><span class="sxs-lookup"><span data-stu-id="33b05-172">worker</span></span>](#web-others)           | <span data-ttu-id="33b05-173">[C#]</span><span class="sxs-lookup"><span data-stu-id="33b05-173">[C#]</span></span>         | <span data-ttu-id="33b05-174">Ortak/çalışan/Web</span><span class="sxs-lookup"><span data-stu-id="33b05-174">Common/Worker/Web</span></span>                     | <span data-ttu-id="33b05-175">3.0</span><span class="sxs-lookup"><span data-stu-id="33b05-175">3.0</span></span>        |
| <span data-ttu-id="33b05-176">Birim testi projesi</span><span class="sxs-lookup"><span data-stu-id="33b05-176">Unit Test Project</span></span>                            | [<span data-ttu-id="33b05-177">'i</span><span class="sxs-lookup"><span data-stu-id="33b05-177">mstest</span></span>](#test)                 | <span data-ttu-id="33b05-178">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="33b05-178">[C#], F#, VB</span></span> | <span data-ttu-id="33b05-179">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="33b05-179">Test/MSTest</span></span>                           | <span data-ttu-id="33b05-180">1.0</span><span class="sxs-lookup"><span data-stu-id="33b05-180">1.0</span></span>        |
| <span data-ttu-id="33b05-181">NUnit 3 test projesi</span><span class="sxs-lookup"><span data-stu-id="33b05-181">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="33b05-182">NUnit</span><span class="sxs-lookup"><span data-stu-id="33b05-182">nunit</span></span>](#nunit)                  | <span data-ttu-id="33b05-183">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="33b05-183">[C#], F#, VB</span></span> | <span data-ttu-id="33b05-184">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="33b05-184">Test/NUnit</span></span>                            | <span data-ttu-id="33b05-185">2.1.400</span><span class="sxs-lookup"><span data-stu-id="33b05-185">2.1.400</span></span>    |
| <span data-ttu-id="33b05-186">NUnit 3 test öğesi</span><span class="sxs-lookup"><span data-stu-id="33b05-186">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="33b05-187">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="33b05-187">[C#], F#, VB</span></span> | <span data-ttu-id="33b05-188">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="33b05-188">Test/NUnit</span></span>                            | <span data-ttu-id="33b05-189">2.2</span><span class="sxs-lookup"><span data-stu-id="33b05-189">2.2</span></span>        |
| <span data-ttu-id="33b05-190">xUnit test projesi</span><span class="sxs-lookup"><span data-stu-id="33b05-190">xUnit Test Project</span></span>                           | [<span data-ttu-id="33b05-191">xUnit</span><span class="sxs-lookup"><span data-stu-id="33b05-191">xunit</span></span>](#test)                  | <span data-ttu-id="33b05-192">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="33b05-192">[C#], F#, VB</span></span> | <span data-ttu-id="33b05-193">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="33b05-193">Test/xUnit</span></span>                            | <span data-ttu-id="33b05-194">1.0</span><span class="sxs-lookup"><span data-stu-id="33b05-194">1.0</span></span>        |
| <span data-ttu-id="33b05-195">Razor bileşeni</span><span class="sxs-lookup"><span data-stu-id="33b05-195">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="33b05-196">[C#]</span><span class="sxs-lookup"><span data-stu-id="33b05-196">[C#]</span></span>         | <span data-ttu-id="33b05-197">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="33b05-197">Web/ASP.NET</span></span>                           | <span data-ttu-id="33b05-198">3.0</span><span class="sxs-lookup"><span data-stu-id="33b05-198">3.0</span></span>        |
| <span data-ttu-id="33b05-199">Razor sayfası</span><span class="sxs-lookup"><span data-stu-id="33b05-199">Razor Page</span></span>                                   | [<span data-ttu-id="33b05-200">sayfasında</span><span class="sxs-lookup"><span data-stu-id="33b05-200">page</span></span>](#page)                   | <span data-ttu-id="33b05-201">[C#]</span><span class="sxs-lookup"><span data-stu-id="33b05-201">[C#]</span></span>         | <span data-ttu-id="33b05-202">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="33b05-202">Web/ASP.NET</span></span>                           | <span data-ttu-id="33b05-203">2,0</span><span class="sxs-lookup"><span data-stu-id="33b05-203">2.0</span></span>        |
| <span data-ttu-id="33b05-204">MVC Viewıtemts</span><span class="sxs-lookup"><span data-stu-id="33b05-204">MVC ViewImports</span></span>                              | [<span data-ttu-id="33b05-205">viewıtems 'lar</span><span class="sxs-lookup"><span data-stu-id="33b05-205">viewimports</span></span>](#namespace)       | <span data-ttu-id="33b05-206">[C#]</span><span class="sxs-lookup"><span data-stu-id="33b05-206">[C#]</span></span>         | <span data-ttu-id="33b05-207">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="33b05-207">Web/ASP.NET</span></span>                           | <span data-ttu-id="33b05-208">2,0</span><span class="sxs-lookup"><span data-stu-id="33b05-208">2.0</span></span>        |
| <span data-ttu-id="33b05-209">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="33b05-209">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="33b05-210">[C#]</span><span class="sxs-lookup"><span data-stu-id="33b05-210">[C#]</span></span>         | <span data-ttu-id="33b05-211">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="33b05-211">Web/ASP.NET</span></span>                           | <span data-ttu-id="33b05-212">2,0</span><span class="sxs-lookup"><span data-stu-id="33b05-212">2.0</span></span>        |
| <span data-ttu-id="33b05-213">Blazor sunucusu uygulaması</span><span class="sxs-lookup"><span data-stu-id="33b05-213">Blazor Server App</span></span>                            | [<span data-ttu-id="33b05-214">blazorserver</span><span class="sxs-lookup"><span data-stu-id="33b05-214">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="33b05-215">[C#]</span><span class="sxs-lookup"><span data-stu-id="33b05-215">[C#]</span></span>         | <span data-ttu-id="33b05-216">Web/Blazor</span><span class="sxs-lookup"><span data-stu-id="33b05-216">Web/Blazor</span></span>                            | <span data-ttu-id="33b05-217">3.0</span><span class="sxs-lookup"><span data-stu-id="33b05-217">3.0</span></span>        |
| <span data-ttu-id="33b05-218">ASP.NET Core boş</span><span class="sxs-lookup"><span data-stu-id="33b05-218">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="33b05-219">Web</span><span class="sxs-lookup"><span data-stu-id="33b05-219">web</span></span>](#web)                     | <span data-ttu-id="33b05-220">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="33b05-220">[C#], F#</span></span>     | <span data-ttu-id="33b05-221">Web/boş</span><span class="sxs-lookup"><span data-stu-id="33b05-221">Web/Empty</span></span>                             | <span data-ttu-id="33b05-222">1.0</span><span class="sxs-lookup"><span data-stu-id="33b05-222">1.0</span></span>        |
| <span data-ttu-id="33b05-223">ASP.NET Core Web uygulaması (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="33b05-223">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="33b05-224">MVC</span><span class="sxs-lookup"><span data-stu-id="33b05-224">mvc</span></span>](#web-options)             | <span data-ttu-id="33b05-225">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="33b05-225">[C#], F#</span></span>     | <span data-ttu-id="33b05-226">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="33b05-226">Web/MVC</span></span>                               | <span data-ttu-id="33b05-227">1.0</span><span class="sxs-lookup"><span data-stu-id="33b05-227">1.0</span></span>        |
| <span data-ttu-id="33b05-228">ASP.NET Core Web uygulaması</span><span class="sxs-lookup"><span data-stu-id="33b05-228">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="33b05-229">WEBAPP, Razor</span><span class="sxs-lookup"><span data-stu-id="33b05-229">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="33b05-230">[C#]</span><span class="sxs-lookup"><span data-stu-id="33b05-230">[C#]</span></span>         | <span data-ttu-id="33b05-231">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="33b05-231">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="33b05-232">2,2, 2,0</span><span class="sxs-lookup"><span data-stu-id="33b05-232">2.2, 2.0</span></span>   |
| <span data-ttu-id="33b05-233">Angular ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="33b05-233">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="33b05-234">Angular</span><span class="sxs-lookup"><span data-stu-id="33b05-234">angular</span></span>](#spa)                 | <span data-ttu-id="33b05-235">[C#]</span><span class="sxs-lookup"><span data-stu-id="33b05-235">[C#]</span></span>         | <span data-ttu-id="33b05-236">MVC/Web/SPA</span><span class="sxs-lookup"><span data-stu-id="33b05-236">Web/MVC/SPA</span></span>                           | <span data-ttu-id="33b05-237">2,0</span><span class="sxs-lookup"><span data-stu-id="33b05-237">2.0</span></span>        |
| <span data-ttu-id="33b05-238">Tepki verme. js ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="33b05-238">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="33b05-239">tıkla</span><span class="sxs-lookup"><span data-stu-id="33b05-239">react</span></span>](#spa)                   | <span data-ttu-id="33b05-240">[C#]</span><span class="sxs-lookup"><span data-stu-id="33b05-240">[C#]</span></span>         | <span data-ttu-id="33b05-241">MVC/Web/SPA</span><span class="sxs-lookup"><span data-stu-id="33b05-241">Web/MVC/SPA</span></span>                           | <span data-ttu-id="33b05-242">2,0</span><span class="sxs-lookup"><span data-stu-id="33b05-242">2.0</span></span>        |
| <span data-ttu-id="33b05-243">Yanıt verir. js ve Redux ile ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="33b05-243">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="33b05-244">reactredux</span><span class="sxs-lookup"><span data-stu-id="33b05-244">reactredux</span></span>](#reactredux)       | <span data-ttu-id="33b05-245">[C#]</span><span class="sxs-lookup"><span data-stu-id="33b05-245">[C#]</span></span>         | <span data-ttu-id="33b05-246">MVC/Web/SPA</span><span class="sxs-lookup"><span data-stu-id="33b05-246">Web/MVC/SPA</span></span>                           | <span data-ttu-id="33b05-247">2,0</span><span class="sxs-lookup"><span data-stu-id="33b05-247">2.0</span></span>        |
| <span data-ttu-id="33b05-248">Razor sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="33b05-248">Razor Class Library</span></span>                          | [<span data-ttu-id="33b05-249">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="33b05-249">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="33b05-250">[C#]</span><span class="sxs-lookup"><span data-stu-id="33b05-250">[C#]</span></span>         | <span data-ttu-id="33b05-251">Web/Razor/kitaplık/Razor sınıfı kitaplığı</span><span class="sxs-lookup"><span data-stu-id="33b05-251">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="33b05-252">2.1</span><span class="sxs-lookup"><span data-stu-id="33b05-252">2.1</span></span>        |
| <span data-ttu-id="33b05-253">ASP.NET Core Web API'si</span><span class="sxs-lookup"><span data-stu-id="33b05-253">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="33b05-254">WebApi</span><span class="sxs-lookup"><span data-stu-id="33b05-254">webapi</span></span>](#webapi)               | <span data-ttu-id="33b05-255">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="33b05-255">[C#], F#</span></span>     | <span data-ttu-id="33b05-256">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="33b05-256">Web/WebAPI</span></span>                            | <span data-ttu-id="33b05-257">1.0</span><span class="sxs-lookup"><span data-stu-id="33b05-257">1.0</span></span>        |
| <span data-ttu-id="33b05-258">ASP.NET Core gRPC hizmeti</span><span class="sxs-lookup"><span data-stu-id="33b05-258">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="33b05-259">GRPC</span><span class="sxs-lookup"><span data-stu-id="33b05-259">grpc</span></span>](#web-others)             | <span data-ttu-id="33b05-260">[C#]</span><span class="sxs-lookup"><span data-stu-id="33b05-260">[C#]</span></span>         | <span data-ttu-id="33b05-261">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="33b05-261">Web/gRPC</span></span>                              | <span data-ttu-id="33b05-262">3.0</span><span class="sxs-lookup"><span data-stu-id="33b05-262">3.0</span></span>        |
| <span data-ttu-id="33b05-263">Protokol arabelleği dosyası</span><span class="sxs-lookup"><span data-stu-id="33b05-263">Protocol Buffer File</span></span>                         | [<span data-ttu-id="33b05-264">Proto</span><span class="sxs-lookup"><span data-stu-id="33b05-264">proto</span></span>](#namespace)             |              | <span data-ttu-id="33b05-265">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="33b05-265">Web/gRPC</span></span>                              | <span data-ttu-id="33b05-266">3.0</span><span class="sxs-lookup"><span data-stu-id="33b05-266">3.0</span></span>        |
| <span data-ttu-id="33b05-267">DotNet gitignore dosyası</span><span class="sxs-lookup"><span data-stu-id="33b05-267">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="33b05-268">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="33b05-268">Config</span></span>                                | <span data-ttu-id="33b05-269">3.0</span><span class="sxs-lookup"><span data-stu-id="33b05-269">3.0</span></span>        |
| <span data-ttu-id="33b05-270">Global. JSON dosyası</span><span class="sxs-lookup"><span data-stu-id="33b05-270">global.json file</span></span>                             | [<span data-ttu-id="33b05-271">globaljson</span><span class="sxs-lookup"><span data-stu-id="33b05-271">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="33b05-272">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="33b05-272">Config</span></span>                                | <span data-ttu-id="33b05-273">2,0</span><span class="sxs-lookup"><span data-stu-id="33b05-273">2.0</span></span>        |
| <span data-ttu-id="33b05-274">NuGet yapılandırması</span><span class="sxs-lookup"><span data-stu-id="33b05-274">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="33b05-275">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="33b05-275">Config</span></span>                                | <span data-ttu-id="33b05-276">1.0</span><span class="sxs-lookup"><span data-stu-id="33b05-276">1.0</span></span>        |
| <span data-ttu-id="33b05-277">DotNet yerel araç bildirim dosyası</span><span class="sxs-lookup"><span data-stu-id="33b05-277">dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="33b05-278">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="33b05-278">Config</span></span>                                | <span data-ttu-id="33b05-279">3.0</span><span class="sxs-lookup"><span data-stu-id="33b05-279">3.0</span></span>        |
| <span data-ttu-id="33b05-280">Web yapılandırması</span><span class="sxs-lookup"><span data-stu-id="33b05-280">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="33b05-281">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="33b05-281">Config</span></span>                                | <span data-ttu-id="33b05-282">1.0</span><span class="sxs-lookup"><span data-stu-id="33b05-282">1.0</span></span>        |
| <span data-ttu-id="33b05-283">Çözüm dosyası</span><span class="sxs-lookup"><span data-stu-id="33b05-283">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="33b05-284">Çözüm</span><span class="sxs-lookup"><span data-stu-id="33b05-284">Solution</span></span>                              | <span data-ttu-id="33b05-285">1.0</span><span class="sxs-lookup"><span data-stu-id="33b05-285">1.0</span></span>        |

## <a name="options"></a><span data-ttu-id="33b05-286">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="33b05-286">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="33b05-287">Verilen komutun çalıştırılmasından sonra ne olacağını gösteren bir Özet görüntüler.</span><span class="sxs-lookup"><span data-stu-id="33b05-287">Displays a summary of what would happen if the given command were run.</span></span> <span data-ttu-id="33b05-288">.NET Core 2,2 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="33b05-288">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="33b05-289">Var olan dosyaları değiştirebilse bile içeriğin oluşturulmasını zorlar.</span><span class="sxs-lookup"><span data-stu-id="33b05-289">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="33b05-290">Seçilen şablon çıkış dizinindeki mevcut dosyaları geçersiz kılacağından bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="33b05-290">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="33b05-291">Komut için yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="33b05-291">Prints out help for the command.</span></span> <span data-ttu-id="33b05-292">`dotnet new` komutun kendisi veya herhangi bir şablon için çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="33b05-292">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="33b05-293">Örneğin, `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="33b05-293">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="33b05-294">`PATH` veya sağlanmış `NUGET_ID` bir şablon paketi kurar.</span><span class="sxs-lookup"><span data-stu-id="33b05-294">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="33b05-295">Şablon paketinin bir ön sürümünü yüklemek istiyorsanız, `<package-name>::<package-version>`biçiminde sürümü belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="33b05-295">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="33b05-296">Varsayılan olarak, `dotnet new` en son kararlı paket sürümünü temsil eden sürüm için \* geçirir.</span><span class="sxs-lookup"><span data-stu-id="33b05-296">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="33b05-297">[Örnekler](#examples) bölümündeki bir örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="33b05-297">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="33b05-298">Bu komutu çalıştırdığınızda şablonun bir sürümü zaten yüklüyse, şablon belirtilen sürüme veya sürüm belirtilmemişse en son kararlı sürüme güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="33b05-298">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="33b05-299">Özel şablonlar oluşturma hakkında daha fazla bilgi için bkz. [DotNet New Için özel şablonlar](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="33b05-299">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="33b05-300">Belirtilen adı içeren şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="33b05-300">Lists templates containing the specified name.</span></span> <span data-ttu-id="33b05-301">Ad belirtilmemişse, tüm şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="33b05-301">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="33b05-302">Oluşturulacak şablonun dili.</span><span class="sxs-lookup"><span data-stu-id="33b05-302">The language of the template to create.</span></span> <span data-ttu-id="33b05-303">Kabul edilen dil şablona göre değişir (bkz. [arguments](#arguments) bölümünde Varsayılanlar).</span><span class="sxs-lookup"><span data-stu-id="33b05-303">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="33b05-304">Bazı şablonlar için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="33b05-304">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="33b05-305">Bazı kabuklar, `#` özel bir karakter olarak yorumlar.</span><span class="sxs-lookup"><span data-stu-id="33b05-305">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="33b05-306">Bu durumlarda, dil parametre değerini tırnak içine alın.</span><span class="sxs-lookup"><span data-stu-id="33b05-306">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="33b05-307">Örneğin, `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="33b05-307">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="33b05-308">Oluşturulan çıkışın adı.</span><span class="sxs-lookup"><span data-stu-id="33b05-308">The name for the created output.</span></span> <span data-ttu-id="33b05-309">Ad belirtilmemişse, geçerli dizinin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="33b05-309">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source`**

  <span data-ttu-id="33b05-310">Yüklemesi sırasında kullanılacak bir NuGet kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="33b05-310">Specifies a NuGet source to use during install.</span></span> <span data-ttu-id="33b05-311">.NET Core 2,1 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="33b05-311">Available since .NET Core 2.1 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="33b05-312">Oluşturulan çıkışın yerleştirileceği konum.</span><span class="sxs-lookup"><span data-stu-id="33b05-312">Location to place the generated output.</span></span> <span data-ttu-id="33b05-313">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="33b05-313">The default is the current directory.</span></span>

- **`--type`**

  <span data-ttu-id="33b05-314">Şablonları kullanılabilir türlerine göre filtreler.</span><span class="sxs-lookup"><span data-stu-id="33b05-314">Filters templates based on available types.</span></span> <span data-ttu-id="33b05-315">Önceden tanımlanmış değerler şunlardır "proje", "öğe" veya "diğer".</span><span class="sxs-lookup"><span data-stu-id="33b05-315">Predefined values are "project", "item", or "other".</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="33b05-316">`PATH` veya sağlanmış `NUGET_ID` bir şablon paketini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="33b05-316">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="33b05-317">`<PATH|NUGET_ID>` değeri belirtilmediğinde, yüklü olan tüm şablon paketleri ve bunlarla ilişkili şablonlar görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="33b05-317">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="33b05-318">`NUGET_ID`belirtirken sürüm numarasını eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="33b05-318">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="33b05-319">Bu seçeneğe bir parametre belirtmezseniz, komut, yüklü şablonları ve bunlarla ilgili ayrıntıları listeler.</span><span class="sxs-lookup"><span data-stu-id="33b05-319">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="33b05-320">Bir `PATH`kullanarak bir şablonu kaldırmak için, yolu tam olarak nitelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="33b05-320">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="33b05-321">Örneğin, *C:/kullanıcılar/\<USER >/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* çalışır, ancak içeren klasörden *./GarciaSoftware.ConsoleTemplate.CSharp* olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="33b05-321">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="33b05-322">Şablon yolunuzda son Sonlandırıcı Dizin eğik çizgisi eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="33b05-322">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="33b05-323">Şu anda yüklü olan şablon paketleri için kullanılabilir güncelleştirmelerin olup olmadığını denetler ve bunları kurar.</span><span class="sxs-lookup"><span data-stu-id="33b05-323">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="33b05-324">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="33b05-324">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="33b05-325">Şu anda yüklü olan şablon paketleri için kullanılabilir güncelleştirmeler olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="33b05-325">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="33b05-326">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="33b05-326">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="33b05-327">Şablon seçenekleri</span><span class="sxs-lookup"><span data-stu-id="33b05-327">Template options</span></span>

<span data-ttu-id="33b05-328">Her proje şablonunda ek seçenekler bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="33b05-328">Each project template may have additional options available.</span></span> <span data-ttu-id="33b05-329">Çekirdek şablonlar aşağıdaki ek seçeneklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="33b05-329">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="33b05-330">konsolu</span><span class="sxs-lookup"><span data-stu-id="33b05-330">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="33b05-331">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="33b05-331">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="33b05-332">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="33b05-332">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="33b05-333">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="33b05-333">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="33b05-334">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="33b05-334">SDK version</span></span> | <span data-ttu-id="33b05-335">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="33b05-335">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="33b05-336">3.1</span><span class="sxs-lookup"><span data-stu-id="33b05-336">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="33b05-337">3.0</span><span class="sxs-lookup"><span data-stu-id="33b05-337">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="33b05-338">Oluşturulan proje dosyasındaki `LangVersion` özelliğini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="33b05-338">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="33b05-339">Örneğin, 7,3 kullanmak C# için `--langVersion 7.3` kullanın.</span><span class="sxs-lookup"><span data-stu-id="33b05-339">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="33b05-340">İçin F#desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="33b05-340">Not supported for F#.</span></span> <span data-ttu-id="33b05-341">.NET Core 2,2 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="33b05-341">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="33b05-342">Varsayılan C# sürümlerin bir listesi için bkz. [Varsayılanlar](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="33b05-342">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`** 

  <span data-ttu-id="33b05-343">Belirtilmişse, proje oluşturma sırasında örtük geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="33b05-343">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="33b05-344">.NET Core 2,2 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="33b05-344">Available since .NET Core 2.2 SDK.</span></span>

***

### <a name="classlib"></a><span data-ttu-id="33b05-345">projesinin</span><span class="sxs-lookup"><span data-stu-id="33b05-345">classlib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="33b05-346">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="33b05-346">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="33b05-347">Değerler: bir .NET Standard sınıf kitaplığı oluşturmak için bir .NET Core sınıf kitaplığı veya `netstandard<version>` oluşturmak `netcoreapp<version>`.</span><span class="sxs-lookup"><span data-stu-id="33b05-347">Values: `netcoreapp<version>` to create a .NET Core Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="33b05-348">Varsayılan değer `netstandard2.0` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="33b05-348">The default value is `netstandard2.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="33b05-349">Oluşturulan proje dosyasındaki `LangVersion` özelliğini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="33b05-349">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="33b05-350">Örneğin, 7,3 kullanmak C# için `--langVersion 7.3` kullanın.</span><span class="sxs-lookup"><span data-stu-id="33b05-350">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="33b05-351">İçin F#desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="33b05-351">Not supported for F#.</span></span> <span data-ttu-id="33b05-352">.NET Core 2,2 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="33b05-352">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="33b05-353">Varsayılan C# sürümlerin bir listesi için bkz. [Varsayılanlar](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="33b05-353">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="33b05-354">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="33b05-354">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="wpf"></a><span data-ttu-id="33b05-355">WPF, wpflib, wpfcustomcontrollib, wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="33b05-355">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="33b05-356">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="33b05-356">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="33b05-357">Varsayılan değer `netcoreapp3.1` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="33b05-357">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="33b05-358">.NET Core 3,1 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="33b05-358">Available since .NET Core 3.1 SDK.</span></span> 

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="33b05-359">Oluşturulan proje dosyasındaki `LangVersion` özelliğini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="33b05-359">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="33b05-360">Örneğin, 7,3 kullanmak C# için `--langVersion 7.3` kullanın.</span><span class="sxs-lookup"><span data-stu-id="33b05-360">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="33b05-361">Varsayılan C# sürümlerin bir listesi için bkz. [Varsayılanlar](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="33b05-361">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="33b05-362">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="33b05-362">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="winforms"></a><span data-ttu-id="33b05-363">WinForms, winformslib</span><span class="sxs-lookup"><span data-stu-id="33b05-363">winforms, winformslib</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="33b05-364">Oluşturulan proje dosyasındaki `LangVersion` özelliğini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="33b05-364">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="33b05-365">Örneğin, 7,3 kullanmak C# için `--langVersion 7.3` kullanın.</span><span class="sxs-lookup"><span data-stu-id="33b05-365">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="33b05-366">Varsayılan C# sürümlerin bir listesi için bkz. [Varsayılanlar](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="33b05-366">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="33b05-367">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="33b05-367">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web-others"></a><span data-ttu-id="33b05-368">çalışan, GRPC</span><span class="sxs-lookup"><span data-stu-id="33b05-368">worker, grpc</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="33b05-369">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="33b05-369">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="33b05-370">Varsayılan değer `netcoreapp3.1` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="33b05-370">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="33b05-371">.NET Core 3,1 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="33b05-371">Available since .NET Core 3.1 SDK.</span></span> 

- **`--exclude-launch-settings`**

  <span data-ttu-id="33b05-372">Oluşturulan şablondan *Launchsettings. JSON* öğesini dışlar.</span><span class="sxs-lookup"><span data-stu-id="33b05-372">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="33b05-373">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="33b05-373">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="test"></a><span data-ttu-id="33b05-374">MSTest, xUnit</span><span class="sxs-lookup"><span data-stu-id="33b05-374">mstest, xunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="33b05-375">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="33b05-375">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="33b05-376">.NET Core 3,0 SDK 'dan beri kullanılabilir seçeneği.</span><span class="sxs-lookup"><span data-stu-id="33b05-376">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="33b05-377">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="33b05-377">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="33b05-378">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="33b05-378">SDK version</span></span> | <span data-ttu-id="33b05-379">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="33b05-379">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="33b05-380">3.1</span><span class="sxs-lookup"><span data-stu-id="33b05-380">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="33b05-381">3.0</span><span class="sxs-lookup"><span data-stu-id="33b05-381">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="33b05-382">[DotNet Pack](dotnet-pack.md)kullanarak proje için paketleme imkanı sunar.</span><span class="sxs-lookup"><span data-stu-id="33b05-382">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="33b05-383">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="33b05-383">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="nunit"></a><span data-ttu-id="33b05-384">NUnit</span><span class="sxs-lookup"><span data-stu-id="33b05-384">nunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="33b05-385">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="33b05-385">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="33b05-386">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="33b05-386">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="33b05-387">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="33b05-387">SDK version</span></span> | <span data-ttu-id="33b05-388">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="33b05-388">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="33b05-389">3.1</span><span class="sxs-lookup"><span data-stu-id="33b05-389">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="33b05-390">3.0</span><span class="sxs-lookup"><span data-stu-id="33b05-390">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="33b05-391">2.2</span><span class="sxs-lookup"><span data-stu-id="33b05-391">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="33b05-392">2.1</span><span class="sxs-lookup"><span data-stu-id="33b05-392">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="33b05-393">[DotNet Pack](dotnet-pack.md)kullanarak proje için paketleme imkanı sunar.</span><span class="sxs-lookup"><span data-stu-id="33b05-393">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="33b05-394">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="33b05-394">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="page"></a><span data-ttu-id="33b05-395">sayfa</span><span class="sxs-lookup"><span data-stu-id="33b05-395">page</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="33b05-396">Oluşturulan kod için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="33b05-396">Namespace for the generated code.</span></span> <span data-ttu-id="33b05-397">Varsayılan değer `MyApp.Namespace` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="33b05-397">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="33b05-398">PageModel olmadan sayfayı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="33b05-398">Creates the page without a PageModel.</span></span>

***

### <a name="namespace"></a><span data-ttu-id="33b05-399">viewıtemler, Proto</span><span class="sxs-lookup"><span data-stu-id="33b05-399">viewimports, proto</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="33b05-400">Oluşturulan kod için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="33b05-400">Namespace for the generated code.</span></span> <span data-ttu-id="33b05-401">Varsayılan değer `MyApp.Namespace` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="33b05-401">The default value is `MyApp.Namespace`.</span></span>

***

### <a name="blazorserver"></a><span data-ttu-id="33b05-402">blazorserver</span><span class="sxs-lookup"><span data-stu-id="33b05-402">blazorserver</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="33b05-403">Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="33b05-403">The type of authentication to use.</span></span> <span data-ttu-id="33b05-404">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="33b05-404">The possible values are:</span></span>

  - <span data-ttu-id="33b05-405">`None`-kimlik doğrulaması yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="33b05-405">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="33b05-406">`Individual` bireysel kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="33b05-406">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="33b05-407">`IndividualB2C` bireysel kimlik doğrulama Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="33b05-407">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="33b05-408">tek bir kiracı için `SingleOrg` kurumsal kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="33b05-408">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="33b05-409">`MultiOrg`-birden çok kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="33b05-409">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="33b05-410">`Windows`-Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="33b05-410">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="33b05-411">Bağlanılacak Azure Active Directory B2C örneği.</span><span class="sxs-lookup"><span data-stu-id="33b05-411">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="33b05-412">`IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="33b05-412">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="33b05-413">Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="33b05-413">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="33b05-414">Bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="33b05-414">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="33b05-415">`IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="33b05-415">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="33b05-416">Bu proje için parola sıfırlama ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="33b05-416">The reset password policy ID for this project.</span></span> <span data-ttu-id="33b05-417">`IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="33b05-417">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="33b05-418">Bu proje için profil ilke KIMLIĞINI Düzenle.</span><span class="sxs-lookup"><span data-stu-id="33b05-418">The edit profile policy ID for this project.</span></span> <span data-ttu-id="33b05-419">`IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="33b05-419">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="33b05-420">Bağlanılacak Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="33b05-420">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="33b05-421">`SingleOrg` veya `MultiOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="33b05-421">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="33b05-422">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="33b05-422">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="33b05-423">Bu projenin Istemci KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="33b05-423">The Client ID for this project.</span></span> <span data-ttu-id="33b05-424">`IndividualB2C`, `SingleOrg`veya `MultiOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="33b05-424">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="33b05-425">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="33b05-425">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="33b05-426">Dizin kiracının etki alanı.</span><span class="sxs-lookup"><span data-stu-id="33b05-426">The domain for the directory tenant.</span></span> <span data-ttu-id="33b05-427">`SingleOrg` veya `IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="33b05-427">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="33b05-428">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="33b05-428">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="33b05-429">Bağlanılacak dizinin Tenantıd KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="33b05-429">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="33b05-430">`SingleOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="33b05-430">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="33b05-431">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="33b05-431">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="33b05-432">Uygulamanın yeniden yönlendirme URI 'sinin temel yolundaki istek yolu.</span><span class="sxs-lookup"><span data-stu-id="33b05-432">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="33b05-433">`SingleOrg` veya `IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="33b05-433">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="33b05-434">Varsayılan değer `/signin-oidc` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="33b05-434">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="33b05-435">Bu uygulamanın dizine okuma erişimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="33b05-435">Allows this application read-access to the directory.</span></span> <span data-ttu-id="33b05-436">Yalnızca `SingleOrg` veya `MultiOrg` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="33b05-436">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="33b05-437">Oluşturulan şablondan *Launchsettings. JSON* öğesini dışlar.</span><span class="sxs-lookup"><span data-stu-id="33b05-437">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="33b05-438">HTTPS 'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="33b05-438">Turns off HTTPS.</span></span> <span data-ttu-id="33b05-439">Bu seçenek yalnızca `Individual`, `IndividualB2C`, `SingleOrg`veya `MultiOrg` `--auth`için kullanılmıyorsa geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="33b05-439">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="33b05-440">SQLite yerine LocalDB kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="33b05-440">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="33b05-441">Yalnızca `Individual` veya `IndividualB2C` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="33b05-441">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="33b05-442">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="33b05-442">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web"></a><span data-ttu-id="33b05-443">web</span><span class="sxs-lookup"><span data-stu-id="33b05-443">web</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="33b05-444">Oluşturulan şablondan *Launchsettings. JSON* öğesini dışlar.</span><span class="sxs-lookup"><span data-stu-id="33b05-444">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="33b05-445">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="33b05-445">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="33b05-446">Seçenek .NET Core 2,2 SDK sürümünde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="33b05-446">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="33b05-447">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="33b05-447">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="33b05-448">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="33b05-448">SDK version</span></span> | <span data-ttu-id="33b05-449">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="33b05-449">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="33b05-450">3.1</span><span class="sxs-lookup"><span data-stu-id="33b05-450">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="33b05-451">3.0</span><span class="sxs-lookup"><span data-stu-id="33b05-451">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="33b05-452">2.1</span><span class="sxs-lookup"><span data-stu-id="33b05-452">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="33b05-453">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="33b05-453">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="33b05-454">HTTPS 'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="33b05-454">Turns off HTTPS.</span></span>

***

### <a name="web-options"></a><span data-ttu-id="33b05-455">MVC, WebApp</span><span class="sxs-lookup"><span data-stu-id="33b05-455">mvc, webapp</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="33b05-456">Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="33b05-456">The type of authentication to use.</span></span> <span data-ttu-id="33b05-457">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="33b05-457">The possible values are:</span></span>

  - <span data-ttu-id="33b05-458">`None`-kimlik doğrulaması yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="33b05-458">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="33b05-459">`Individual` bireysel kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="33b05-459">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="33b05-460">`IndividualB2C` bireysel kimlik doğrulama Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="33b05-460">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="33b05-461">tek bir kiracı için `SingleOrg` kurumsal kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="33b05-461">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="33b05-462">`MultiOrg`-birden çok kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="33b05-462">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="33b05-463">`Windows`-Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="33b05-463">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="33b05-464">Bağlanılacak Azure Active Directory B2C örneği.</span><span class="sxs-lookup"><span data-stu-id="33b05-464">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="33b05-465">`IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="33b05-465">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="33b05-466">Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="33b05-466">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="33b05-467">Bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="33b05-467">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="33b05-468">`IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="33b05-468">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="33b05-469">Bu proje için parola sıfırlama ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="33b05-469">The reset password policy ID for this project.</span></span> <span data-ttu-id="33b05-470">`IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="33b05-470">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="33b05-471">Bu proje için profil ilke KIMLIĞINI Düzenle.</span><span class="sxs-lookup"><span data-stu-id="33b05-471">The edit profile policy ID for this project.</span></span> <span data-ttu-id="33b05-472">`IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="33b05-472">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="33b05-473">Bağlanılacak Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="33b05-473">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="33b05-474">`SingleOrg` veya `MultiOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="33b05-474">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="33b05-475">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="33b05-475">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="33b05-476">Bu projenin Istemci KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="33b05-476">The Client ID for this project.</span></span> <span data-ttu-id="33b05-477">`IndividualB2C`, `SingleOrg`veya `MultiOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="33b05-477">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="33b05-478">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="33b05-478">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="33b05-479">Dizin kiracının etki alanı.</span><span class="sxs-lookup"><span data-stu-id="33b05-479">The domain for the directory tenant.</span></span> <span data-ttu-id="33b05-480">`SingleOrg` veya `IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="33b05-480">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="33b05-481">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="33b05-481">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="33b05-482">Bağlanılacak dizinin Tenantıd KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="33b05-482">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="33b05-483">`SingleOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="33b05-483">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="33b05-484">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="33b05-484">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="33b05-485">Uygulamanın yeniden yönlendirme URI 'sinin temel yolundaki istek yolu.</span><span class="sxs-lookup"><span data-stu-id="33b05-485">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="33b05-486">`SingleOrg` veya `IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="33b05-486">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="33b05-487">Varsayılan değer `/signin-oidc` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="33b05-487">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="33b05-488">Bu uygulamanın dizine okuma erişimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="33b05-488">Allows this application read-access to the directory.</span></span> <span data-ttu-id="33b05-489">Yalnızca `SingleOrg` veya `MultiOrg` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="33b05-489">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="33b05-490">Oluşturulan şablondan *Launchsettings. JSON* öğesini dışlar.</span><span class="sxs-lookup"><span data-stu-id="33b05-490">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="33b05-491">HTTPS 'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="33b05-491">Turns off HTTPS.</span></span> <span data-ttu-id="33b05-492">Bu seçenek yalnızca `Individual`, `IndividualB2C`, `SingleOrg`veya `MultiOrg` kullanılmıyorsa geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="33b05-492">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="33b05-493">SQLite yerine LocalDB kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="33b05-493">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="33b05-494">Yalnızca `Individual` veya `IndividualB2C` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="33b05-494">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="33b05-495">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="33b05-495">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="33b05-496">.NET Core 3,0 SDK 'dan beri kullanılabilir seçeneği.</span><span class="sxs-lookup"><span data-stu-id="33b05-496">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="33b05-497">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="33b05-497">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="33b05-498">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="33b05-498">SDK version</span></span> | <span data-ttu-id="33b05-499">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="33b05-499">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="33b05-500">3.1</span><span class="sxs-lookup"><span data-stu-id="33b05-500">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="33b05-501">3.0</span><span class="sxs-lookup"><span data-stu-id="33b05-501">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="33b05-502">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="33b05-502">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="33b05-503">Projedeki BrowserLink öğesini içerir.</span><span class="sxs-lookup"><span data-stu-id="33b05-503">Includes BrowserLink in the project.</span></span> <span data-ttu-id="33b05-504">Seçenek .NET Core 2,2 ve 3,1 SDK sürümünde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="33b05-504">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

***

### <a name="spa"></a><span data-ttu-id="33b05-505">Angular, tepki verme</span><span class="sxs-lookup"><span data-stu-id="33b05-505">angular, react</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="33b05-506">Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="33b05-506">The type of authentication to use.</span></span> <span data-ttu-id="33b05-507">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="33b05-507">Available since .NET Core 3.0 SDK.</span></span> 
  
  <span data-ttu-id="33b05-508">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="33b05-508">The possible values are:</span></span>

  - <span data-ttu-id="33b05-509">`None`-kimlik doğrulaması yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="33b05-509">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="33b05-510">`Individual` bireysel kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="33b05-510">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="33b05-511">Oluşturulan şablondan *Launchsettings. JSON* öğesini dışlar.</span><span class="sxs-lookup"><span data-stu-id="33b05-511">Excludes *launchSettings.json* from the generated template.</span></span> 

- **`--no-restore`**

  <span data-ttu-id="33b05-512">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="33b05-512">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="33b05-513">HTTPS 'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="33b05-513">Turns off HTTPS.</span></span> <span data-ttu-id="33b05-514">Bu seçenek yalnızca kimlik doğrulama `None`geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="33b05-514">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="33b05-515">SQLite yerine LocalDB kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="33b05-515">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="33b05-516">Yalnızca `Individual` veya `IndividualB2C` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="33b05-516">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="33b05-517">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="33b05-517">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="33b05-518">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="33b05-518">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="33b05-519">Seçenek .NET Core 2,2 SDK sürümünde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="33b05-519">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="33b05-520">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="33b05-520">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="33b05-521">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="33b05-521">SDK version</span></span> | <span data-ttu-id="33b05-522">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="33b05-522">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="33b05-523">3.1</span><span class="sxs-lookup"><span data-stu-id="33b05-523">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="33b05-524">3.0</span><span class="sxs-lookup"><span data-stu-id="33b05-524">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="33b05-525">2.1</span><span class="sxs-lookup"><span data-stu-id="33b05-525">2.1</span></span>         | `netcoreapp2.0` |

***

### <a name="reactredux"></a><span data-ttu-id="33b05-526">açarken kilitlenmesi</span><span class="sxs-lookup"><span data-stu-id="33b05-526">reactredux</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="33b05-527">Oluşturulan şablondan *Launchsettings. JSON* öğesini dışlar.</span><span class="sxs-lookup"><span data-stu-id="33b05-527">Excludes *launchSettings.json* from the generated template.</span></span> 

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="33b05-528">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="33b05-528">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="33b05-529">Seçenek .NET Core 2,2 SDK sürümünde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="33b05-529">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="33b05-530">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="33b05-530">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="33b05-531">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="33b05-531">SDK version</span></span> | <span data-ttu-id="33b05-532">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="33b05-532">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="33b05-533">3.1</span><span class="sxs-lookup"><span data-stu-id="33b05-533">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="33b05-534">3.0</span><span class="sxs-lookup"><span data-stu-id="33b05-534">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="33b05-535">2.1</span><span class="sxs-lookup"><span data-stu-id="33b05-535">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="33b05-536">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="33b05-536">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="33b05-537">HTTPS 'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="33b05-537">Turns off HTTPS.</span></span>

***

### <a name="razorclasslib"></a><span data-ttu-id="33b05-538">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="33b05-538">razorclasslib</span></span>

- **`--no-restore`**

  <span data-ttu-id="33b05-539">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="33b05-539">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="33b05-540">, Bu kitaplığa bileşenlere ek olarak geleneksel Razor sayfaları ve görünümleri eklenmesini destekler.</span><span class="sxs-lookup"><span data-stu-id="33b05-540">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="33b05-541">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="33b05-541">Available since .NET Core 3.0 SDK.</span></span>

***
  
### <a name="webapi"></a><span data-ttu-id="33b05-542">WebApi</span><span class="sxs-lookup"><span data-stu-id="33b05-542">webapi</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="33b05-543">Kullanılacak kimlik doğrulaması türü.</span><span class="sxs-lookup"><span data-stu-id="33b05-543">The type of authentication to use.</span></span> <span data-ttu-id="33b05-544">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="33b05-544">The possible values are:</span></span>

  - <span data-ttu-id="33b05-545">`None`-kimlik doğrulaması yok (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="33b05-545">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="33b05-546">`IndividualB2C` bireysel kimlik doğrulama Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="33b05-546">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="33b05-547">tek bir kiracı için `SingleOrg` kurumsal kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="33b05-547">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="33b05-548">`Windows`-Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="33b05-548">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="33b05-549">Bağlanılacak Azure Active Directory B2C örneği.</span><span class="sxs-lookup"><span data-stu-id="33b05-549">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="33b05-550">`IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="33b05-550">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="33b05-551">Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="33b05-551">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="33b05-552">Bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="33b05-552">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="33b05-553">`IndividualB2C` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="33b05-553">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="33b05-554">Bağlanılacak Azure Active Directory örneği.</span><span class="sxs-lookup"><span data-stu-id="33b05-554">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="33b05-555">`SingleOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="33b05-555">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="33b05-556">Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="33b05-556">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="33b05-557">Bu projenin Istemci KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="33b05-557">The Client ID for this project.</span></span> <span data-ttu-id="33b05-558">`IndividualB2C` veya `SingleOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="33b05-558">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="33b05-559">Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="33b05-559">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="33b05-560">Dizin kiracının etki alanı.</span><span class="sxs-lookup"><span data-stu-id="33b05-560">The domain for the directory tenant.</span></span> <span data-ttu-id="33b05-561">`IndividualB2C` veya `SingleOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="33b05-561">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="33b05-562">Varsayılan değer `qualified.domain.name` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="33b05-562">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="33b05-563">Bağlanılacak dizinin Tenantıd KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="33b05-563">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="33b05-564">`SingleOrg` kimlik doğrulamasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="33b05-564">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="33b05-565">Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="33b05-565">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="33b05-566">Bu uygulamanın dizine okuma erişimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="33b05-566">Allows this application read-access to the directory.</span></span> <span data-ttu-id="33b05-567">Yalnızca `SingleOrg` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="33b05-567">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="33b05-568">Oluşturulan şablondan *Launchsettings. JSON* öğesini dışlar.</span><span class="sxs-lookup"><span data-stu-id="33b05-568">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="33b05-569">HTTPS 'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="33b05-569">Turns off HTTPS.</span></span> <span data-ttu-id="33b05-570">`app.UseHsts` ve `app.UseHttpsRedirection` `Startup.Configure`eklenmez.</span><span class="sxs-lookup"><span data-stu-id="33b05-570">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="33b05-571">Bu seçenek yalnızca `IndividualB2C` veya `SingleOrg` kimlik doğrulaması için kullanılmıyorsa geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="33b05-571">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="33b05-572">SQLite yerine LocalDB kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="33b05-572">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="33b05-573">Yalnızca `IndividualB2C` kimlik doğrulaması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="33b05-573">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="33b05-574">Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="33b05-574">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="33b05-575">Seçenek .NET Core 2,2 SDK sürümünde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="33b05-575">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="33b05-576">Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="33b05-576">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="33b05-577">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="33b05-577">SDK version</span></span> | <span data-ttu-id="33b05-578">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="33b05-578">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="33b05-579">3.1</span><span class="sxs-lookup"><span data-stu-id="33b05-579">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="33b05-580">3.0</span><span class="sxs-lookup"><span data-stu-id="33b05-580">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="33b05-581">2.1</span><span class="sxs-lookup"><span data-stu-id="33b05-581">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="33b05-582">Proje oluşturma sırasında örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="33b05-582">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="globaljson"></a><span data-ttu-id="33b05-583">globaljson</span><span class="sxs-lookup"><span data-stu-id="33b05-583">globaljson</span></span>

- **`--sdk-version <VERSION_NUMBER>`**

  <span data-ttu-id="33b05-584">*Global. JSON* dosyasında kullanılacak .NET Core SDK sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="33b05-584">Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="33b05-585">Örnekler</span><span class="sxs-lookup"><span data-stu-id="33b05-585">Examples</span></span>

- <span data-ttu-id="33b05-586">Şablon adını C# belirterek bir konsol uygulaması projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="33b05-586">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="33b05-587">Geçerli dizinde F# bir konsol uygulaması projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="33b05-587">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang F#
  ```

- <span data-ttu-id="33b05-588">Belirtilen dizinde bir .NET Standard sınıf kitaplığı projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="33b05-588">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="33b05-589">Geçerli dizinde kimlik doğrulaması C# olmadan yeni bir ASP.NET Core MVC projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="33b05-589">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="33b05-590">Yeni bir xUnit projesi oluştur:</span><span class="sxs-lookup"><span data-stu-id="33b05-590">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="33b05-591">Tek sayfalı uygulama (SPA) şablonları için kullanılabilen tüm şablonları listeleyin:</span><span class="sxs-lookup"><span data-stu-id="33b05-591">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="33b05-592">*We* alt dizeniz ile eşleşen tüm şablonları listeleyin.</span><span class="sxs-lookup"><span data-stu-id="33b05-592">List all templates matching the *we* substring.</span></span> <span data-ttu-id="33b05-593">Tam eşleşme bulunamadı, bu nedenle alt dize eşleştirmesi hem kısa ad hem de ad sütunlarında çalışır.</span><span class="sxs-lookup"><span data-stu-id="33b05-593">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="33b05-594">Şablonla *eşleşen şablonu*çağırma girişimi.</span><span class="sxs-lookup"><span data-stu-id="33b05-594">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="33b05-595">Tek bir eşleşme belirlenemiyorsa kısmi eşleşen şablonları listeleyin.</span><span class="sxs-lookup"><span data-stu-id="33b05-595">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="33b05-596">ASP.NET Core için SPA şablonlarının 2,0 sürümünü yükler:</span><span class="sxs-lookup"><span data-stu-id="33b05-596">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="33b05-597">Yüklü şablonları ve bunlarla ilgili ayrıntıları, bunları kaldırma dahil olmak üzere listeleyin:</span><span class="sxs-lookup"><span data-stu-id="33b05-597">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="33b05-598">SDK sürümünü 3.1.101 olarak ayarlamak için geçerli dizinde *Global. JSON* oluşturun:</span><span class="sxs-lookup"><span data-stu-id="33b05-598">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="33b05-599">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="33b05-599">See also</span></span>

- [<span data-ttu-id="33b05-600">DotNet New için özel şablonlar</span><span class="sxs-lookup"><span data-stu-id="33b05-600">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="33b05-601">Dotnet new için özel şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="33b05-601">Create a custom template for dotnet new</span></span>](../tutorials/cli-templates-create-item-template.md)
- [<span data-ttu-id="33b05-602">DotNet/DotNet-şablon-örnek GitHub deposu</span><span class="sxs-lookup"><span data-stu-id="33b05-602">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="33b05-603">DotNet New için kullanılabilir şablonlar</span><span class="sxs-lookup"><span data-stu-id="33b05-603">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
