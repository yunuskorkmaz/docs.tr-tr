---
title: dotnet yeni komut
description: Dotnet yeni komutu, belirtilen şablonu temel alan yeni .NET Core projeleri oluşturur.
ms.date: 04/10/2020
ms.openlocfilehash: 4ad0d7e54f93582237ed9457b562957018916d36
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463605"
---
# <a name="dotnet-new"></a><span data-ttu-id="88ab4-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="88ab4-103">dotnet new</span></span>

<span data-ttu-id="88ab4-104">**Bu makale şu şekilde dir:** ✔️ .NET Core 2.0 SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="88ab4-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="88ab4-105">Adı</span><span class="sxs-lookup"><span data-stu-id="88ab4-105">Name</span></span>

<span data-ttu-id="88ab4-106">`dotnet new`- Belirtilen şablonu temel alan yeni bir proje, yapılandırma dosyası veya çözüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="88ab4-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="88ab4-107">Özet</span><span class="sxs-lookup"><span data-stu-id="88ab4-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install {PATH|NUGET_ID}]
    [-lang|--language {C#|F#|VB}] [-n|--name <OUTPUT_NAME>]
    [--nuget-source <SOURCE>] [-o|--output <OUTPUT_DIRECTORY>]
    [-u|--uninstall] [--update-apply] [--update-check] [Template options]

dotnet new <TEMPLATE> [-l|--list] [--type <TYPE>]

dotnet new -h|--help
```

## <a name="description"></a><span data-ttu-id="88ab4-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="88ab4-108">Description</span></span>

<span data-ttu-id="88ab4-109">Komut, `dotnet new` şablona dayalı bir .NET Core projesi veya diğer yapılar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="88ab4-109">The `dotnet new` command creates a .NET Core project or other artifacts based on a template.</span></span>

<span data-ttu-id="88ab4-110">Komut, belirtilen şablon ve seçenekleri temel alan disküzerinde yapıları oluşturmak için [şablon altyapısını](https://github.com/dotnet/templating) çağırır.</span><span class="sxs-lookup"><span data-stu-id="88ab4-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="88ab4-111">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="88ab4-111">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="88ab4-112">Komut çağrıldığında anında başlatılabilmek için şablon.</span><span class="sxs-lookup"><span data-stu-id="88ab4-112">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="88ab4-113">Her şablonun geçirebileceğiniz belirli seçenekleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="88ab4-113">Each template might have specific options you can pass.</span></span> <span data-ttu-id="88ab4-114">Daha fazla bilgi için [Şablon seçeneklerine](#template-options)bakın.</span><span class="sxs-lookup"><span data-stu-id="88ab4-114">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="88ab4-115">Yüklenen tüm `dotnet new --list` şablonların listesini görmek için çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="88ab4-115">You can run `dotnet new --list` to see a list of all installed templates.</span></span> <span data-ttu-id="88ab4-116">Döndürülen `TEMPLATE` tablodaki **Şablonlar** veya **Kısa Ad** sütunundaki metindeki değer tam eşleşme değilse, bu iki sütunda bir alt dize eşleşmesi gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="88ab4-116">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="88ab4-117">.NET Core 3.0 SDK ile başlayarak, cli aşağıdaki koşullarda `dotnet new` komutu çağırdığınızda NuGet.org şablonları arar:</span><span class="sxs-lookup"><span data-stu-id="88ab4-117">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="88ab4-118">CLI, çağrıştırırken bir şablon eşleşmesi `dotnet new`bulamazsa, kısmi bile değildir.</span><span class="sxs-lookup"><span data-stu-id="88ab4-118">If the CLI can't find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="88ab4-119">Şablonun daha yeni bir sürümü varsa.</span><span class="sxs-lookup"><span data-stu-id="88ab4-119">If there's a newer version of the template available.</span></span> <span data-ttu-id="88ab4-120">Bu durumda, proje veya yapı oluşturulur, ancak CLI şablonun güncelleştirilmiş bir sürümü hakkında sizi uyarır.</span><span class="sxs-lookup"><span data-stu-id="88ab4-120">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="88ab4-121">Komut varsayılan şablonlar listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="88ab4-121">The command contains a default list of templates.</span></span> <span data-ttu-id="88ab4-122">Kullanılabilir `dotnet new -l` şablonların listesini almak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="88ab4-122">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="88ab4-123">Aşağıdaki tabloda .NET Core SDK ile önceden yüklenmiş gelen şablonlar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="88ab4-123">The following table shows the templates that come pre-installed with the .NET Core SDK.</span></span> <span data-ttu-id="88ab4-124">Şabloniçin varsayılan dil parantez içinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="88ab4-124">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="88ab4-125">Belirli şablon seçeneklerini görmek için kısa ad bağlantısını tıklatın.</span><span class="sxs-lookup"><span data-stu-id="88ab4-125">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="88ab4-126">Şablonlar</span><span class="sxs-lookup"><span data-stu-id="88ab4-126">Templates</span></span>                                    | <span data-ttu-id="88ab4-127">Kısa ad</span><span class="sxs-lookup"><span data-stu-id="88ab4-127">Short name</span></span>                      | <span data-ttu-id="88ab4-128">Dil</span><span class="sxs-lookup"><span data-stu-id="88ab4-128">Language</span></span>     | <span data-ttu-id="88ab4-129">Etiketler</span><span class="sxs-lookup"><span data-stu-id="88ab4-129">Tags</span></span>                                  | <span data-ttu-id="88ab4-130">Tanıttı</span><span class="sxs-lookup"><span data-stu-id="88ab4-130">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="88ab4-131">Konsol Uygulaması</span><span class="sxs-lookup"><span data-stu-id="88ab4-131">Console Application</span></span>                          | [<span data-ttu-id="88ab4-132">Konsol</span><span class="sxs-lookup"><span data-stu-id="88ab4-132">console</span></span>](#console)             | <span data-ttu-id="88ab4-133">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="88ab4-133">[C#], F#, VB</span></span> | <span data-ttu-id="88ab4-134">Ortak/Konsol</span><span class="sxs-lookup"><span data-stu-id="88ab4-134">Common/Console</span></span>                        | <span data-ttu-id="88ab4-135">1.0</span><span class="sxs-lookup"><span data-stu-id="88ab4-135">1.0</span></span>        |
| <span data-ttu-id="88ab4-136">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="88ab4-136">Class library</span></span>                                | [<span data-ttu-id="88ab4-137">classlib</span><span class="sxs-lookup"><span data-stu-id="88ab4-137">classlib</span></span>](#classlib)           | <span data-ttu-id="88ab4-138">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="88ab4-138">[C#], F#, VB</span></span> | <span data-ttu-id="88ab4-139">Ortak / Kütüphane</span><span class="sxs-lookup"><span data-stu-id="88ab4-139">Common/Library</span></span>                        | <span data-ttu-id="88ab4-140">1.0</span><span class="sxs-lookup"><span data-stu-id="88ab4-140">1.0</span></span>        |
| <span data-ttu-id="88ab4-141">WPF Uygulaması</span><span class="sxs-lookup"><span data-stu-id="88ab4-141">WPF Application</span></span>                              | [<span data-ttu-id="88ab4-142">Wpf</span><span class="sxs-lookup"><span data-stu-id="88ab4-142">wpf</span></span>](#wpf)                     | <span data-ttu-id="88ab4-143">[C#]</span><span class="sxs-lookup"><span data-stu-id="88ab4-143">[C#]</span></span>         | <span data-ttu-id="88ab4-144">Ortak/WPF</span><span class="sxs-lookup"><span data-stu-id="88ab4-144">Common/WPF</span></span>                            | <span data-ttu-id="88ab4-145">3,0</span><span class="sxs-lookup"><span data-stu-id="88ab4-145">3.0</span></span>        |
| <span data-ttu-id="88ab4-146">WPF Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="88ab4-146">WPF Class library</span></span>                            | [<span data-ttu-id="88ab4-147">wpflib</span><span class="sxs-lookup"><span data-stu-id="88ab4-147">wpflib</span></span>](#wpf)                  | <span data-ttu-id="88ab4-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="88ab4-148">[C#]</span></span>         | <span data-ttu-id="88ab4-149">Ortak/WPF</span><span class="sxs-lookup"><span data-stu-id="88ab4-149">Common/WPF</span></span>                            | <span data-ttu-id="88ab4-150">3,0</span><span class="sxs-lookup"><span data-stu-id="88ab4-150">3.0</span></span>        |
| <span data-ttu-id="88ab4-151">WPF Özel Denetim Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="88ab4-151">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="88ab4-152">wpfcustomcontrollib</span><span class="sxs-lookup"><span data-stu-id="88ab4-152">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="88ab4-153">[C#]</span><span class="sxs-lookup"><span data-stu-id="88ab4-153">[C#]</span></span>         | <span data-ttu-id="88ab4-154">Ortak/WPF</span><span class="sxs-lookup"><span data-stu-id="88ab4-154">Common/WPF</span></span>                            | <span data-ttu-id="88ab4-155">3,0</span><span class="sxs-lookup"><span data-stu-id="88ab4-155">3.0</span></span>        |
| <span data-ttu-id="88ab4-156">WPF Kullanıcı Kontrol Kütüphanesi</span><span class="sxs-lookup"><span data-stu-id="88ab4-156">WPF User Control Library</span></span>                     | [<span data-ttu-id="88ab4-157">wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="88ab4-157">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="88ab4-158">[C#]</span><span class="sxs-lookup"><span data-stu-id="88ab4-158">[C#]</span></span>         | <span data-ttu-id="88ab4-159">Ortak/WPF</span><span class="sxs-lookup"><span data-stu-id="88ab4-159">Common/WPF</span></span>                            | <span data-ttu-id="88ab4-160">3,0</span><span class="sxs-lookup"><span data-stu-id="88ab4-160">3.0</span></span>        |
| <span data-ttu-id="88ab4-161">Windows Formları (WinForms) Uygulaması</span><span class="sxs-lookup"><span data-stu-id="88ab4-161">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="88ab4-162">Winforms</span><span class="sxs-lookup"><span data-stu-id="88ab4-162">winforms</span></span>](#winforms)           | <span data-ttu-id="88ab4-163">[C#]</span><span class="sxs-lookup"><span data-stu-id="88ab4-163">[C#]</span></span>         | <span data-ttu-id="88ab4-164">Ortak/WinForm'lar</span><span class="sxs-lookup"><span data-stu-id="88ab4-164">Common/WinForms</span></span>                       | <span data-ttu-id="88ab4-165">3,0</span><span class="sxs-lookup"><span data-stu-id="88ab4-165">3.0</span></span>        |
| <span data-ttu-id="88ab4-166">Windows Formları (WinForms) Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="88ab4-166">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="88ab4-167">winformslib</span><span class="sxs-lookup"><span data-stu-id="88ab4-167">winformslib</span></span>](#winforms)        | <span data-ttu-id="88ab4-168">[C#]</span><span class="sxs-lookup"><span data-stu-id="88ab4-168">[C#]</span></span>         | <span data-ttu-id="88ab4-169">Ortak/WinForm'lar</span><span class="sxs-lookup"><span data-stu-id="88ab4-169">Common/WinForms</span></span>                       | <span data-ttu-id="88ab4-170">3,0</span><span class="sxs-lookup"><span data-stu-id="88ab4-170">3.0</span></span>        |
| <span data-ttu-id="88ab4-171">İşçi Hizmeti</span><span class="sxs-lookup"><span data-stu-id="88ab4-171">Worker Service</span></span>                               | [<span data-ttu-id="88ab4-172">Işçi</span><span class="sxs-lookup"><span data-stu-id="88ab4-172">worker</span></span>](#web-others)           | <span data-ttu-id="88ab4-173">[C#]</span><span class="sxs-lookup"><span data-stu-id="88ab4-173">[C#]</span></span>         | <span data-ttu-id="88ab4-174">Ortak/Çalışan/Web</span><span class="sxs-lookup"><span data-stu-id="88ab4-174">Common/Worker/Web</span></span>                     | <span data-ttu-id="88ab4-175">3,0</span><span class="sxs-lookup"><span data-stu-id="88ab4-175">3.0</span></span>        |
| <span data-ttu-id="88ab4-176">Ünite Test Projesi</span><span class="sxs-lookup"><span data-stu-id="88ab4-176">Unit Test Project</span></span>                            | [<span data-ttu-id="88ab4-177">Mstest</span><span class="sxs-lookup"><span data-stu-id="88ab4-177">mstest</span></span>](#test)                 | <span data-ttu-id="88ab4-178">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="88ab4-178">[C#], F#, VB</span></span> | <span data-ttu-id="88ab4-179">Test /MSTest</span><span class="sxs-lookup"><span data-stu-id="88ab4-179">Test/MSTest</span></span>                           | <span data-ttu-id="88ab4-180">1.0</span><span class="sxs-lookup"><span data-stu-id="88ab4-180">1.0</span></span>        |
| <span data-ttu-id="88ab4-181">NUnit 3 Test Projesi</span><span class="sxs-lookup"><span data-stu-id="88ab4-181">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="88ab4-182">nunit</span><span class="sxs-lookup"><span data-stu-id="88ab4-182">nunit</span></span>](#nunit)                  | <span data-ttu-id="88ab4-183">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="88ab4-183">[C#], F#, VB</span></span> | <span data-ttu-id="88ab4-184">Test /NUnit</span><span class="sxs-lookup"><span data-stu-id="88ab4-184">Test/NUnit</span></span>                            | <span data-ttu-id="88ab4-185">2.1.400</span><span class="sxs-lookup"><span data-stu-id="88ab4-185">2.1.400</span></span>    |
| <span data-ttu-id="88ab4-186">NUnit 3 Test Öğesi</span><span class="sxs-lookup"><span data-stu-id="88ab4-186">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="88ab4-187">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="88ab4-187">[C#], F#, VB</span></span> | <span data-ttu-id="88ab4-188">Test /NUnit</span><span class="sxs-lookup"><span data-stu-id="88ab4-188">Test/NUnit</span></span>                            | <span data-ttu-id="88ab4-189">2,2</span><span class="sxs-lookup"><span data-stu-id="88ab4-189">2.2</span></span>        |
| <span data-ttu-id="88ab4-190">xUnit Test Projesi</span><span class="sxs-lookup"><span data-stu-id="88ab4-190">xUnit Test Project</span></span>                           | [<span data-ttu-id="88ab4-191">xunit</span><span class="sxs-lookup"><span data-stu-id="88ab4-191">xunit</span></span>](#test)                  | <span data-ttu-id="88ab4-192">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="88ab4-192">[C#], F#, VB</span></span> | <span data-ttu-id="88ab4-193">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="88ab4-193">Test/xUnit</span></span>                            | <span data-ttu-id="88ab4-194">1.0</span><span class="sxs-lookup"><span data-stu-id="88ab4-194">1.0</span></span>        |
| <span data-ttu-id="88ab4-195">Jilet Bileşeni</span><span class="sxs-lookup"><span data-stu-id="88ab4-195">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="88ab4-196">[C#]</span><span class="sxs-lookup"><span data-stu-id="88ab4-196">[C#]</span></span>         | <span data-ttu-id="88ab4-197">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="88ab4-197">Web/ASP.NET</span></span>                           | <span data-ttu-id="88ab4-198">3,0</span><span class="sxs-lookup"><span data-stu-id="88ab4-198">3.0</span></span>        |
| <span data-ttu-id="88ab4-199">Jilet Sayfası</span><span class="sxs-lookup"><span data-stu-id="88ab4-199">Razor Page</span></span>                                   | [<span data-ttu-id="88ab4-200">Sayfası</span><span class="sxs-lookup"><span data-stu-id="88ab4-200">page</span></span>](#page)                   | <span data-ttu-id="88ab4-201">[C#]</span><span class="sxs-lookup"><span data-stu-id="88ab4-201">[C#]</span></span>         | <span data-ttu-id="88ab4-202">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="88ab4-202">Web/ASP.NET</span></span>                           | <span data-ttu-id="88ab4-203">2,0</span><span class="sxs-lookup"><span data-stu-id="88ab4-203">2.0</span></span>        |
| <span data-ttu-id="88ab4-204">MVC Görünümİthalat</span><span class="sxs-lookup"><span data-stu-id="88ab4-204">MVC ViewImports</span></span>                              | [<span data-ttu-id="88ab4-205">içe görme</span><span class="sxs-lookup"><span data-stu-id="88ab4-205">viewimports</span></span>](#namespace)       | <span data-ttu-id="88ab4-206">[C#]</span><span class="sxs-lookup"><span data-stu-id="88ab4-206">[C#]</span></span>         | <span data-ttu-id="88ab4-207">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="88ab4-207">Web/ASP.NET</span></span>                           | <span data-ttu-id="88ab4-208">2,0</span><span class="sxs-lookup"><span data-stu-id="88ab4-208">2.0</span></span>        |
| <span data-ttu-id="88ab4-209">MVC Görünüm Başlat</span><span class="sxs-lookup"><span data-stu-id="88ab4-209">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="88ab4-210">[C#]</span><span class="sxs-lookup"><span data-stu-id="88ab4-210">[C#]</span></span>         | <span data-ttu-id="88ab4-211">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="88ab4-211">Web/ASP.NET</span></span>                           | <span data-ttu-id="88ab4-212">2,0</span><span class="sxs-lookup"><span data-stu-id="88ab4-212">2.0</span></span>        |
| <span data-ttu-id="88ab4-213">Blazor Server Uygulaması</span><span class="sxs-lookup"><span data-stu-id="88ab4-213">Blazor Server App</span></span>                            | [<span data-ttu-id="88ab4-214">blazorserver</span><span class="sxs-lookup"><span data-stu-id="88ab4-214">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="88ab4-215">[C#]</span><span class="sxs-lookup"><span data-stu-id="88ab4-215">[C#]</span></span>         | <span data-ttu-id="88ab4-216">Web/Blazor</span><span class="sxs-lookup"><span data-stu-id="88ab4-216">Web/Blazor</span></span>                            | <span data-ttu-id="88ab4-217">3,0</span><span class="sxs-lookup"><span data-stu-id="88ab4-217">3.0</span></span>        |
| <span data-ttu-id="88ab4-218">ASP.NET Çekirdek Boş</span><span class="sxs-lookup"><span data-stu-id="88ab4-218">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="88ab4-219">Web</span><span class="sxs-lookup"><span data-stu-id="88ab4-219">web</span></span>](#web)                     | <span data-ttu-id="88ab4-220">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="88ab4-220">[C#], F#</span></span>     | <span data-ttu-id="88ab4-221">Web/Boş</span><span class="sxs-lookup"><span data-stu-id="88ab4-221">Web/Empty</span></span>                             | <span data-ttu-id="88ab4-222">1.0</span><span class="sxs-lookup"><span data-stu-id="88ab4-222">1.0</span></span>        |
| <span data-ttu-id="88ab4-223">ASP.NET Çekirdek Web Uygulaması (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="88ab4-223">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="88ab4-224">Mvc</span><span class="sxs-lookup"><span data-stu-id="88ab4-224">mvc</span></span>](#web-options)             | <span data-ttu-id="88ab4-225">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="88ab4-225">[C#], F#</span></span>     | <span data-ttu-id="88ab4-226">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="88ab4-226">Web/MVC</span></span>                               | <span data-ttu-id="88ab4-227">1.0</span><span class="sxs-lookup"><span data-stu-id="88ab4-227">1.0</span></span>        |
| <span data-ttu-id="88ab4-228">ASP.NET Çekirdek Web Uygulaması</span><span class="sxs-lookup"><span data-stu-id="88ab4-228">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="88ab4-229">webapp, jilet</span><span class="sxs-lookup"><span data-stu-id="88ab4-229">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="88ab4-230">[C#]</span><span class="sxs-lookup"><span data-stu-id="88ab4-230">[C#]</span></span>         | <span data-ttu-id="88ab4-231">Web/MVC/Razor Sayfaları</span><span class="sxs-lookup"><span data-stu-id="88ab4-231">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="88ab4-232">2.2, 2.0</span><span class="sxs-lookup"><span data-stu-id="88ab4-232">2.2, 2.0</span></span>   |
| <span data-ttu-id="88ab4-233">ASP.NET Çekirdek li Açısal</span><span class="sxs-lookup"><span data-stu-id="88ab4-233">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="88ab4-234">Açısal</span><span class="sxs-lookup"><span data-stu-id="88ab4-234">angular</span></span>](#spa)                 | <span data-ttu-id="88ab4-235">[C#]</span><span class="sxs-lookup"><span data-stu-id="88ab4-235">[C#]</span></span>         | <span data-ttu-id="88ab4-236">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="88ab4-236">Web/MVC/SPA</span></span>                           | <span data-ttu-id="88ab4-237">2,0</span><span class="sxs-lookup"><span data-stu-id="88ab4-237">2.0</span></span>        |
| <span data-ttu-id="88ab4-238">React.js ile ASP.NET Çekirdek</span><span class="sxs-lookup"><span data-stu-id="88ab4-238">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="88ab4-239">Tepki</span><span class="sxs-lookup"><span data-stu-id="88ab4-239">react</span></span>](#spa)                   | <span data-ttu-id="88ab4-240">[C#]</span><span class="sxs-lookup"><span data-stu-id="88ab4-240">[C#]</span></span>         | <span data-ttu-id="88ab4-241">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="88ab4-241">Web/MVC/SPA</span></span>                           | <span data-ttu-id="88ab4-242">2,0</span><span class="sxs-lookup"><span data-stu-id="88ab4-242">2.0</span></span>        |
| <span data-ttu-id="88ab4-243">React.js ve Redux ile ASP.NET Çekirdek</span><span class="sxs-lookup"><span data-stu-id="88ab4-243">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="88ab4-244">reactredux</span><span class="sxs-lookup"><span data-stu-id="88ab4-244">reactredux</span></span>](#reactredux)       | <span data-ttu-id="88ab4-245">[C#]</span><span class="sxs-lookup"><span data-stu-id="88ab4-245">[C#]</span></span>         | <span data-ttu-id="88ab4-246">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="88ab4-246">Web/MVC/SPA</span></span>                           | <span data-ttu-id="88ab4-247">2,0</span><span class="sxs-lookup"><span data-stu-id="88ab4-247">2.0</span></span>        |
| <span data-ttu-id="88ab4-248">Razor Sınıf Kütüphanesi</span><span class="sxs-lookup"><span data-stu-id="88ab4-248">Razor Class Library</span></span>                          | [<span data-ttu-id="88ab4-249">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="88ab4-249">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="88ab4-250">[C#]</span><span class="sxs-lookup"><span data-stu-id="88ab4-250">[C#]</span></span>         | <span data-ttu-id="88ab4-251">Web/Razor/Kütüphane/Razor Sınıf Kütüphanesi</span><span class="sxs-lookup"><span data-stu-id="88ab4-251">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="88ab4-252">2.1</span><span class="sxs-lookup"><span data-stu-id="88ab4-252">2.1</span></span>        |
| <span data-ttu-id="88ab4-253">ASP.NET Core Web API'si</span><span class="sxs-lookup"><span data-stu-id="88ab4-253">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="88ab4-254">webapi</span><span class="sxs-lookup"><span data-stu-id="88ab4-254">webapi</span></span>](#webapi)               | <span data-ttu-id="88ab4-255">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="88ab4-255">[C#], F#</span></span>     | <span data-ttu-id="88ab4-256">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="88ab4-256">Web/WebAPI</span></span>                            | <span data-ttu-id="88ab4-257">1.0</span><span class="sxs-lookup"><span data-stu-id="88ab4-257">1.0</span></span>        |
| <span data-ttu-id="88ab4-258">ASP.NET Çekirdek gRPC Hizmeti</span><span class="sxs-lookup"><span data-stu-id="88ab4-258">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="88ab4-259">grpc</span><span class="sxs-lookup"><span data-stu-id="88ab4-259">grpc</span></span>](#web-others)             | <span data-ttu-id="88ab4-260">[C#]</span><span class="sxs-lookup"><span data-stu-id="88ab4-260">[C#]</span></span>         | <span data-ttu-id="88ab4-261">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="88ab4-261">Web/gRPC</span></span>                              | <span data-ttu-id="88ab4-262">3,0</span><span class="sxs-lookup"><span data-stu-id="88ab4-262">3.0</span></span>        |
| <span data-ttu-id="88ab4-263">Protokol Arabellek Dosyası</span><span class="sxs-lookup"><span data-stu-id="88ab4-263">Protocol Buffer File</span></span>                         | [<span data-ttu-id="88ab4-264">Proto</span><span class="sxs-lookup"><span data-stu-id="88ab4-264">proto</span></span>](#namespace)             |              | <span data-ttu-id="88ab4-265">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="88ab4-265">Web/gRPC</span></span>                              | <span data-ttu-id="88ab4-266">3,0</span><span class="sxs-lookup"><span data-stu-id="88ab4-266">3.0</span></span>        |
| <span data-ttu-id="88ab4-267">dotnet gitignore dosyası</span><span class="sxs-lookup"><span data-stu-id="88ab4-267">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="88ab4-268">Config</span><span class="sxs-lookup"><span data-stu-id="88ab4-268">Config</span></span>                                | <span data-ttu-id="88ab4-269">3,0</span><span class="sxs-lookup"><span data-stu-id="88ab4-269">3.0</span></span>        |
| <span data-ttu-id="88ab4-270">global.json dosyası</span><span class="sxs-lookup"><span data-stu-id="88ab4-270">global.json file</span></span>                             | [<span data-ttu-id="88ab4-271">globaljson</span><span class="sxs-lookup"><span data-stu-id="88ab4-271">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="88ab4-272">Config</span><span class="sxs-lookup"><span data-stu-id="88ab4-272">Config</span></span>                                | <span data-ttu-id="88ab4-273">2,0</span><span class="sxs-lookup"><span data-stu-id="88ab4-273">2.0</span></span>        |
| <span data-ttu-id="88ab4-274">NuGet Config</span><span class="sxs-lookup"><span data-stu-id="88ab4-274">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="88ab4-275">Config</span><span class="sxs-lookup"><span data-stu-id="88ab4-275">Config</span></span>                                | <span data-ttu-id="88ab4-276">1.0</span><span class="sxs-lookup"><span data-stu-id="88ab4-276">1.0</span></span>        |
| <span data-ttu-id="88ab4-277">dotnet yerel araç bildirimi dosyası</span><span class="sxs-lookup"><span data-stu-id="88ab4-277">dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="88ab4-278">Config</span><span class="sxs-lookup"><span data-stu-id="88ab4-278">Config</span></span>                                | <span data-ttu-id="88ab4-279">3,0</span><span class="sxs-lookup"><span data-stu-id="88ab4-279">3.0</span></span>        |
| <span data-ttu-id="88ab4-280">Web Config</span><span class="sxs-lookup"><span data-stu-id="88ab4-280">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="88ab4-281">Config</span><span class="sxs-lookup"><span data-stu-id="88ab4-281">Config</span></span>                                | <span data-ttu-id="88ab4-282">1.0</span><span class="sxs-lookup"><span data-stu-id="88ab4-282">1.0</span></span>        |
| <span data-ttu-id="88ab4-283">Çözüm Dosyası</span><span class="sxs-lookup"><span data-stu-id="88ab4-283">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="88ab4-284">Çözüm</span><span class="sxs-lookup"><span data-stu-id="88ab4-284">Solution</span></span>                              | <span data-ttu-id="88ab4-285">1.0</span><span class="sxs-lookup"><span data-stu-id="88ab4-285">1.0</span></span>        |

## <a name="options"></a><span data-ttu-id="88ab4-286">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="88ab4-286">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="88ab4-287">Verilen komut çalıştırılırsa ne olacağının bir özetini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="88ab4-287">Displays a summary of what would happen if the given command were run.</span></span> <span data-ttu-id="88ab4-288">.NET Core 2.2 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="88ab4-288">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="88ab4-289">Varolan dosyaları değiştirse bile içeriği oluşturulmaya zorlar.</span><span class="sxs-lookup"><span data-stu-id="88ab4-289">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="88ab4-290">Bu, seçilen şablon çıktı dizinindeki varolan dosyaları geçersiz kılacaksa gereklidir.</span><span class="sxs-lookup"><span data-stu-id="88ab4-290">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="88ab4-291">Komut için yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="88ab4-291">Prints out help for the command.</span></span> <span data-ttu-id="88ab4-292">Komutun `dotnet new` kendisi veya herhangi bir şablon için çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="88ab4-292">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="88ab4-293">Örneğin, `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="88ab4-293">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="88ab4-294">Bir şablon paketi yükler `PATH` `NUGET_ID` veya sağlanan.</span><span class="sxs-lookup"><span data-stu-id="88ab4-294">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="88ab4-295">Bir şablon paketinin ön sürüm sürümünü yüklemek istiyorsanız, sürümü ' nin `<package-name>::<package-version>`biçiminde belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="88ab4-295">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="88ab4-296">Varsayılan `dotnet new` olarak, \* en son kararlı paket sürümünü temsil eden sürüm için geçer.</span><span class="sxs-lookup"><span data-stu-id="88ab4-296">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="88ab4-297">[Örnekler](#examples) bölümündeki bir örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="88ab4-297">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="88ab4-298">Bu komutu çalıştırdığınızda şablonun bir sürümü zaten yüklenmişse, sürüm belirtilmemişse şablon belirtilen sürüme veya en son kararlı sürüme güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="88ab4-298">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="88ab4-299">Özel şablonlar oluşturma hakkında bilgi [için, nokta yeni için Özel şablonlara](custom-templates.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="88ab4-299">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="88ab4-300">Belirtilen adı içeren şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="88ab4-300">Lists templates containing the specified name.</span></span> <span data-ttu-id="88ab4-301">Ad belirtilmemişse, tüm şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="88ab4-301">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="88ab4-302">Oluşturulacak şablonun dili.</span><span class="sxs-lookup"><span data-stu-id="88ab4-302">The language of the template to create.</span></span> <span data-ttu-id="88ab4-303">Kabul edilen dil şablona göre değişir [(bağımsız değişkenler](#arguments) bölümündeki varsayılanlara bakın).</span><span class="sxs-lookup"><span data-stu-id="88ab4-303">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="88ab4-304">Bazı şablonlar için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="88ab4-304">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="88ab4-305">Bazı kabuklar `#` özel bir karakter olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="88ab4-305">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="88ab4-306">Bu gibi durumlarda, dil parametre değerini tırnak içinde içine atl..</span><span class="sxs-lookup"><span data-stu-id="88ab4-306">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="88ab4-307">Örneğin, `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="88ab4-307">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="88ab4-308">Oluşturulan çıktının adı.</span><span class="sxs-lookup"><span data-stu-id="88ab4-308">The name for the created output.</span></span> <span data-ttu-id="88ab4-309">Ad belirtilmemişse, geçerli dizinin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="88ab4-309">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source <SOURCE>`**

  <span data-ttu-id="88ab4-310">Yükleme sırasında kullanılacak bir NuGet kaynağı belirtir.</span><span class="sxs-lookup"><span data-stu-id="88ab4-310">Specifies a NuGet source to use during install.</span></span> <span data-ttu-id="88ab4-311">.NET Core 2.1 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="88ab4-311">Available since .NET Core 2.1 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="88ab4-312">Oluşturulan çıktıyı yerleştirmek için yer.</span><span class="sxs-lookup"><span data-stu-id="88ab4-312">Location to place the generated output.</span></span> <span data-ttu-id="88ab4-313">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="88ab4-313">The default is the current directory.</span></span>

- **`--type <TYPE>`**

  <span data-ttu-id="88ab4-314">Kullanılabilir türleri temel alan şablonları filtreler.</span><span class="sxs-lookup"><span data-stu-id="88ab4-314">Filters templates based on available types.</span></span> <span data-ttu-id="88ab4-315">Önceden tanımlanmış `project`değerler `item`, `other`, veya .</span><span class="sxs-lookup"><span data-stu-id="88ab4-315">Predefined values are `project`, `item`, or `other`.</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="88ab4-316">Bir şablon paketini `PATH` kaldırın `NUGET_ID` veya sağlanan.</span><span class="sxs-lookup"><span data-stu-id="88ab4-316">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="88ab4-317">`<PATH|NUGET_ID>` Değer belirtilmediği zaman, şu anda yüklü olan tüm şablon paketleri ve ilişkili şablonları görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="88ab4-317">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="88ab4-318">`NUGET_ID`Belirtirken, sürüm numarasını eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="88ab4-318">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="88ab4-319">Bu seçenek için bir parametre belirtmezseniz, komut yüklenen şablonları ve bunlarla ilgili ayrıntıları listeler.</span><span class="sxs-lookup"><span data-stu-id="88ab4-319">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="88ab4-320">Bir şablonu kaldırmak `PATH`için , yolu tam olarak nitelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="88ab4-320">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="88ab4-321">Örneğin, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* çalışır, ancak içeren klasörden *./GarciaSoftware.ConsoleTemplate.CSharp* çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="88ab4-321">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="88ab4-322">Şablon yolunuza sonlandırma dizini kesimieklemeyi eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="88ab4-322">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="88ab4-323">Şu anda yüklü olan ve bunları yükleyen şablon paketleri için güncelleştirmeolup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="88ab4-323">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="88ab4-324">.NET Core 3.0 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="88ab4-324">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="88ab4-325">Şu anda yüklü olan şablon paketleri için güncelleştirme olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="88ab4-325">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="88ab4-326">.NET Core 3.0 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="88ab4-326">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="88ab4-327">Şablon seçenekleri</span><span class="sxs-lookup"><span data-stu-id="88ab4-327">Template options</span></span>

<span data-ttu-id="88ab4-328">Her proje şablonunda ek seçenekler olabilir.</span><span class="sxs-lookup"><span data-stu-id="88ab4-328">Each project template may have additional options available.</span></span> <span data-ttu-id="88ab4-329">Çekirdek şablonları aşağıdaki ek seçeneklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="88ab4-329">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="88ab4-330">console</span><span class="sxs-lookup"><span data-stu-id="88ab4-330">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="88ab4-331">Hedef için [çerçeve](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="88ab4-331">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="88ab4-332">.NET Core 3.0 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="88ab4-332">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="88ab4-333">Aşağıdaki tablo, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerleri listeler:</span><span class="sxs-lookup"><span data-stu-id="88ab4-333">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="88ab4-334">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="88ab4-334">SDK version</span></span> | <span data-ttu-id="88ab4-335">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="88ab4-335">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="88ab4-336">3.1</span><span class="sxs-lookup"><span data-stu-id="88ab4-336">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="88ab4-337">3,0</span><span class="sxs-lookup"><span data-stu-id="88ab4-337">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="88ab4-338">Oluşturulan `LangVersion` proje dosyasındaki özelliği ayarlar.</span><span class="sxs-lookup"><span data-stu-id="88ab4-338">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="88ab4-339">Örneğin, C# 7.3'u kullanmak için kullanın. `--langVersion 7.3`</span><span class="sxs-lookup"><span data-stu-id="88ab4-339">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="88ab4-340">F# için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="88ab4-340">Not supported for F#.</span></span> <span data-ttu-id="88ab4-341">.NET Core 2.2 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="88ab4-341">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="88ab4-342">Varsayılan C# sürümlerinin listesi için [Varsayılanlar'a](../../csharp/language-reference/configure-language-version.md#defaults)bakın.</span><span class="sxs-lookup"><span data-stu-id="88ab4-342">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="88ab4-343">Belirtilirse, proje oluşturma sırasında örtülü bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="88ab4-343">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="88ab4-344">.NET Core 2.2 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="88ab4-344">Available since .NET Core 2.2 SDK.</span></span>

***

### <a name="classlib"></a><span data-ttu-id="88ab4-345">classlib</span><span class="sxs-lookup"><span data-stu-id="88ab4-345">classlib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="88ab4-346">Hedef için [çerçeve](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="88ab4-346">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="88ab4-347">Değerler: `netcoreapp<version>` .NET Çekirdek Sınıf Kitaplığı oluşturmak veya `netstandard<version>` .NET Standart Sınıf Kitaplığı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="88ab4-347">Values: `netcoreapp<version>` to create a .NET Core Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="88ab4-348">Varsayılan değer: `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="88ab4-348">The default value is `netstandard2.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="88ab4-349">Oluşturulan `LangVersion` proje dosyasındaki özelliği ayarlar.</span><span class="sxs-lookup"><span data-stu-id="88ab4-349">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="88ab4-350">Örneğin, C# 7.3'u kullanmak için kullanın. `--langVersion 7.3`</span><span class="sxs-lookup"><span data-stu-id="88ab4-350">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="88ab4-351">F# için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="88ab4-351">Not supported for F#.</span></span> <span data-ttu-id="88ab4-352">.NET Core 2.2 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="88ab4-352">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="88ab4-353">Varsayılan C# sürümlerinin listesi için [Varsayılanlar'a](../../csharp/language-reference/configure-language-version.md#defaults)bakın.</span><span class="sxs-lookup"><span data-stu-id="88ab4-353">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="88ab4-354">Proje oluşturma sırasında örtülü bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="88ab4-354">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="wpf-wpflib-wpfcustomcontrollib-wpfusercontrollib"></a><a name="wpf"></a><span data-ttu-id="88ab4-355">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="88ab4-355">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="88ab4-356">Hedef için [çerçeve](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="88ab4-356">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="88ab4-357">Varsayılan değer: `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="88ab4-357">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="88ab4-358">.NET Core 3.1 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="88ab4-358">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="88ab4-359">Oluşturulan `LangVersion` proje dosyasındaki özelliği ayarlar.</span><span class="sxs-lookup"><span data-stu-id="88ab4-359">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="88ab4-360">Örneğin, C# 7.3'u kullanmak için kullanın. `--langVersion 7.3`</span><span class="sxs-lookup"><span data-stu-id="88ab4-360">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="88ab4-361">Varsayılan C# sürümlerinin listesi için [Varsayılanlar'a](../../csharp/language-reference/configure-language-version.md#defaults)bakın.</span><span class="sxs-lookup"><span data-stu-id="88ab4-361">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="88ab4-362">Proje oluşturma sırasında örtülü bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="88ab4-362">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="winforms-winformslib"></a><a name="winforms"></a><span data-ttu-id="88ab4-363">winforms, winformslib</span><span class="sxs-lookup"><span data-stu-id="88ab4-363">winforms, winformslib</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="88ab4-364">Oluşturulan `LangVersion` proje dosyasındaki özelliği ayarlar.</span><span class="sxs-lookup"><span data-stu-id="88ab4-364">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="88ab4-365">Örneğin, C# 7.3'u kullanmak için kullanın. `--langVersion 7.3`</span><span class="sxs-lookup"><span data-stu-id="88ab4-365">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="88ab4-366">Varsayılan C# sürümlerinin listesi için [Varsayılanlar'a](../../csharp/language-reference/configure-language-version.md#defaults)bakın.</span><span class="sxs-lookup"><span data-stu-id="88ab4-366">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="88ab4-367">Proje oluşturma sırasında örtülü bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="88ab4-367">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="worker-grpc"></a><a name="web-others"></a><span data-ttu-id="88ab4-368">işçi, grpc</span><span class="sxs-lookup"><span data-stu-id="88ab4-368">worker, grpc</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="88ab4-369">Hedef için [çerçeve](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="88ab4-369">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="88ab4-370">Varsayılan değer: `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="88ab4-370">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="88ab4-371">.NET Core 3.1 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="88ab4-371">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="88ab4-372">oluşturulan şablondan *launchSettings.json* hariç tutar.</span><span class="sxs-lookup"><span data-stu-id="88ab4-372">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="88ab4-373">Proje oluşturma sırasında örtülü bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="88ab4-373">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="mstest-xunit"></a><a name="test"></a><span data-ttu-id="88ab4-374">mstest, xunit</span><span class="sxs-lookup"><span data-stu-id="88ab4-374">mstest, xunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="88ab4-375">Hedef için [çerçeve](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="88ab4-375">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="88ab4-376">Seçenek .NET Core 3.0 SDK beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="88ab4-376">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="88ab4-377">Aşağıdaki tablo, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerleri listeler:</span><span class="sxs-lookup"><span data-stu-id="88ab4-377">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="88ab4-378">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="88ab4-378">SDK version</span></span> | <span data-ttu-id="88ab4-379">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="88ab4-379">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="88ab4-380">3.1</span><span class="sxs-lookup"><span data-stu-id="88ab4-380">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="88ab4-381">3,0</span><span class="sxs-lookup"><span data-stu-id="88ab4-381">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="88ab4-382">[Dotnet paketi](dotnet-pack.md)kullanarak proje için paketleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="88ab4-382">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="88ab4-383">Proje oluşturma sırasında örtülü bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="88ab4-383">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="nunit"></a><span data-ttu-id="88ab4-384">nunit</span><span class="sxs-lookup"><span data-stu-id="88ab4-384">nunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="88ab4-385">Hedef için [çerçeve](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="88ab4-385">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="88ab4-386">Aşağıdaki tablo, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerleri listeler:</span><span class="sxs-lookup"><span data-stu-id="88ab4-386">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="88ab4-387">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="88ab4-387">SDK version</span></span> | <span data-ttu-id="88ab4-388">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="88ab4-388">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="88ab4-389">3.1</span><span class="sxs-lookup"><span data-stu-id="88ab4-389">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="88ab4-390">3,0</span><span class="sxs-lookup"><span data-stu-id="88ab4-390">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="88ab4-391">2,2</span><span class="sxs-lookup"><span data-stu-id="88ab4-391">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="88ab4-392">2.1</span><span class="sxs-lookup"><span data-stu-id="88ab4-392">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="88ab4-393">[Dotnet paketi](dotnet-pack.md)kullanarak proje için paketleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="88ab4-393">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="88ab4-394">Proje oluşturma sırasında örtülü bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="88ab4-394">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="page"></a><span data-ttu-id="88ab4-395">Sayfası</span><span class="sxs-lookup"><span data-stu-id="88ab4-395">page</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="88ab4-396">Oluşturulan kod için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="88ab4-396">Namespace for the generated code.</span></span> <span data-ttu-id="88ab4-397">Varsayılan değer: `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="88ab4-397">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="88ab4-398">Sayfayı PageModel olmadan oluşturur.</span><span class="sxs-lookup"><span data-stu-id="88ab4-398">Creates the page without a PageModel.</span></span>

***

### <a name="viewimports-proto"></a><a name="namespace"></a><span data-ttu-id="88ab4-399">viewimports, proto</span><span class="sxs-lookup"><span data-stu-id="88ab4-399">viewimports, proto</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="88ab4-400">Oluşturulan kod için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="88ab4-400">Namespace for the generated code.</span></span> <span data-ttu-id="88ab4-401">Varsayılan değer: `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="88ab4-401">The default value is `MyApp.Namespace`.</span></span>

***

### <a name="blazorserver"></a><span data-ttu-id="88ab4-402">blazorserver</span><span class="sxs-lookup"><span data-stu-id="88ab4-402">blazorserver</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="88ab4-403">Kullanılacak kimlik doğrulama türü.</span><span class="sxs-lookup"><span data-stu-id="88ab4-403">The type of authentication to use.</span></span> <span data-ttu-id="88ab4-404">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="88ab4-404">The possible values are:</span></span>

  - <span data-ttu-id="88ab4-405">`None`- Kimlik doğrulaması yok (Varsayılan).</span><span class="sxs-lookup"><span data-stu-id="88ab4-405">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="88ab4-406">`Individual`- Bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="88ab4-406">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="88ab4-407">`IndividualB2C`- Azure AD B2C ile bireysel kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="88ab4-407">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="88ab4-408">`SingleOrg`- Tek bir kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="88ab4-408">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="88ab4-409">`MultiOrg`- Birden çok kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="88ab4-409">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="88ab4-410">`Windows`- Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="88ab4-410">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="88ab4-411">Bağlanmak için Azure Active Directory B2C örneği.</span><span class="sxs-lookup"><span data-stu-id="88ab4-411">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="88ab4-412">Kimlik `IndividualB2C` doğrulaması ile kullanın.</span><span class="sxs-lookup"><span data-stu-id="88ab4-412">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="88ab4-413">Varsayılan değer: `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="88ab4-413">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="88ab4-414">Bu proje için oturum açma ve kaydolma ilkesi kimliği.</span><span class="sxs-lookup"><span data-stu-id="88ab4-414">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="88ab4-415">Kimlik `IndividualB2C` doğrulaması ile kullanın.</span><span class="sxs-lookup"><span data-stu-id="88ab4-415">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="88ab4-416">Bu proje için sıfırlama parola ilkesi kimliği.</span><span class="sxs-lookup"><span data-stu-id="88ab4-416">The reset password policy ID for this project.</span></span> <span data-ttu-id="88ab4-417">Kimlik `IndividualB2C` doğrulaması ile kullanın.</span><span class="sxs-lookup"><span data-stu-id="88ab4-417">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="88ab4-418">Bu projenin profil ilke kimliğini edin.</span><span class="sxs-lookup"><span data-stu-id="88ab4-418">The edit profile policy ID for this project.</span></span> <span data-ttu-id="88ab4-419">Kimlik `IndividualB2C` doğrulaması ile kullanın.</span><span class="sxs-lookup"><span data-stu-id="88ab4-419">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="88ab4-420">Bağlanmak için Azure Etkin Dizin örneği.</span><span class="sxs-lookup"><span data-stu-id="88ab4-420">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="88ab4-421">Kimlik `SingleOrg` doğrulaması ile kullanın. `MultiOrg`</span><span class="sxs-lookup"><span data-stu-id="88ab4-421">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="88ab4-422">Varsayılan değer: `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="88ab4-422">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="88ab4-423">Bu projenin Istemci Kimliği.</span><span class="sxs-lookup"><span data-stu-id="88ab4-423">The Client ID for this project.</span></span> <span data-ttu-id="88ab4-424">"Kimlik `IndividualB2C` `SingleOrg`doğrulama" `MultiOrg` ile kullanın.</span><span class="sxs-lookup"><span data-stu-id="88ab4-424">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="88ab4-425">Varsayılan değer: `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="88ab4-425">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="88ab4-426">Dizin kiracı için etki alanı.</span><span class="sxs-lookup"><span data-stu-id="88ab4-426">The domain for the directory tenant.</span></span> <span data-ttu-id="88ab4-427">Kimlik `SingleOrg` doğrulaması ile kullanın. `IndividualB2C`</span><span class="sxs-lookup"><span data-stu-id="88ab4-427">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="88ab4-428">Varsayılan değer: `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="88ab4-428">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="88ab4-429">Bağlanacak dizinin Kiracı Kimliği.</span><span class="sxs-lookup"><span data-stu-id="88ab4-429">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="88ab4-430">Kimlik `SingleOrg` doğrulaması ile kullanın.</span><span class="sxs-lookup"><span data-stu-id="88ab4-430">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="88ab4-431">Varsayılan değer: `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="88ab4-431">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="88ab4-432">Yeniden yönlendirme URI uygulamanın temel yolu içinde istek yolu.</span><span class="sxs-lookup"><span data-stu-id="88ab4-432">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="88ab4-433">Kimlik `SingleOrg` doğrulaması ile kullanın. `IndividualB2C`</span><span class="sxs-lookup"><span data-stu-id="88ab4-433">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="88ab4-434">Varsayılan değer: `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="88ab4-434">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="88ab4-435">Bu uygulamanın dizine okuma erişimine izin verir.</span><span class="sxs-lookup"><span data-stu-id="88ab4-435">Allows this application read-access to the directory.</span></span> <span data-ttu-id="88ab4-436">Yalnızca kimlik `SingleOrg` doğrulama `MultiOrg` veya kimlik doğrulama için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="88ab4-436">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="88ab4-437">oluşturulan şablondan *launchSettings.json* hariç tutar.</span><span class="sxs-lookup"><span data-stu-id="88ab4-437">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="88ab4-438">HTTPS'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="88ab4-438">Turns off HTTPS.</span></span> <span data-ttu-id="88ab4-439">Bu seçenek yalnızca `Individual`, `IndividualB2C` `SingleOrg`, `MultiOrg` , , `--auth`için kullanılıyorsa veya kullanılmazsa geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="88ab4-439">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="88ab4-440">SQLite yerine LocalDB'nin kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="88ab4-440">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="88ab4-441">Yalnızca kimlik `Individual` doğrulama `IndividualB2C` veya kimlik doğrulama için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="88ab4-441">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="88ab4-442">Proje oluşturma sırasında örtülü bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="88ab4-442">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web"></a><span data-ttu-id="88ab4-443">web</span><span class="sxs-lookup"><span data-stu-id="88ab4-443">web</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="88ab4-444">oluşturulan şablondan *launchSettings.json* hariç tutar.</span><span class="sxs-lookup"><span data-stu-id="88ab4-444">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="88ab4-445">Hedef için [çerçeve](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="88ab4-445">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="88ab4-446">Seçenek .NET Core 2.2 SDK'da kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="88ab4-446">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="88ab4-447">Aşağıdaki tablo, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerleri listeler:</span><span class="sxs-lookup"><span data-stu-id="88ab4-447">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="88ab4-448">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="88ab4-448">SDK version</span></span> | <span data-ttu-id="88ab4-449">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="88ab4-449">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="88ab4-450">3.1</span><span class="sxs-lookup"><span data-stu-id="88ab4-450">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="88ab4-451">3,0</span><span class="sxs-lookup"><span data-stu-id="88ab4-451">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="88ab4-452">2.1</span><span class="sxs-lookup"><span data-stu-id="88ab4-452">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="88ab4-453">Proje oluşturma sırasında örtülü bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="88ab4-453">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="88ab4-454">HTTPS'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="88ab4-454">Turns off HTTPS.</span></span>

***

### <a name="mvc-webapp"></a><a name="web-options"></a><span data-ttu-id="88ab4-455">mvc, webapp</span><span class="sxs-lookup"><span data-stu-id="88ab4-455">mvc, webapp</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="88ab4-456">Kullanılacak kimlik doğrulama türü.</span><span class="sxs-lookup"><span data-stu-id="88ab4-456">The type of authentication to use.</span></span> <span data-ttu-id="88ab4-457">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="88ab4-457">The possible values are:</span></span>

  - <span data-ttu-id="88ab4-458">`None`- Kimlik doğrulaması yok (Varsayılan).</span><span class="sxs-lookup"><span data-stu-id="88ab4-458">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="88ab4-459">`Individual`- Bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="88ab4-459">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="88ab4-460">`IndividualB2C`- Azure AD B2C ile bireysel kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="88ab4-460">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="88ab4-461">`SingleOrg`- Tek bir kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="88ab4-461">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="88ab4-462">`MultiOrg`- Birden çok kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="88ab4-462">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="88ab4-463">`Windows`- Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="88ab4-463">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="88ab4-464">Bağlanmak için Azure Active Directory B2C örneği.</span><span class="sxs-lookup"><span data-stu-id="88ab4-464">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="88ab4-465">Kimlik `IndividualB2C` doğrulaması ile kullanın.</span><span class="sxs-lookup"><span data-stu-id="88ab4-465">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="88ab4-466">Varsayılan değer: `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="88ab4-466">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="88ab4-467">Bu proje için oturum açma ve kaydolma ilkesi kimliği.</span><span class="sxs-lookup"><span data-stu-id="88ab4-467">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="88ab4-468">Kimlik `IndividualB2C` doğrulaması ile kullanın.</span><span class="sxs-lookup"><span data-stu-id="88ab4-468">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="88ab4-469">Bu proje için sıfırlama parola ilkesi kimliği.</span><span class="sxs-lookup"><span data-stu-id="88ab4-469">The reset password policy ID for this project.</span></span> <span data-ttu-id="88ab4-470">Kimlik `IndividualB2C` doğrulaması ile kullanın.</span><span class="sxs-lookup"><span data-stu-id="88ab4-470">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="88ab4-471">Bu projenin profil ilke kimliğini edin.</span><span class="sxs-lookup"><span data-stu-id="88ab4-471">The edit profile policy ID for this project.</span></span> <span data-ttu-id="88ab4-472">Kimlik `IndividualB2C` doğrulaması ile kullanın.</span><span class="sxs-lookup"><span data-stu-id="88ab4-472">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="88ab4-473">Bağlanmak için Azure Etkin Dizin örneği.</span><span class="sxs-lookup"><span data-stu-id="88ab4-473">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="88ab4-474">Kimlik `SingleOrg` doğrulaması ile kullanın. `MultiOrg`</span><span class="sxs-lookup"><span data-stu-id="88ab4-474">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="88ab4-475">Varsayılan değer: `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="88ab4-475">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="88ab4-476">Bu projenin Istemci Kimliği.</span><span class="sxs-lookup"><span data-stu-id="88ab4-476">The Client ID for this project.</span></span> <span data-ttu-id="88ab4-477">"Kimlik `IndividualB2C` `SingleOrg`doğrulama" `MultiOrg` ile kullanın.</span><span class="sxs-lookup"><span data-stu-id="88ab4-477">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="88ab4-478">Varsayılan değer: `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="88ab4-478">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="88ab4-479">Dizin kiracı için etki alanı.</span><span class="sxs-lookup"><span data-stu-id="88ab4-479">The domain for the directory tenant.</span></span> <span data-ttu-id="88ab4-480">Kimlik `SingleOrg` doğrulaması ile kullanın. `IndividualB2C`</span><span class="sxs-lookup"><span data-stu-id="88ab4-480">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="88ab4-481">Varsayılan değer: `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="88ab4-481">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="88ab4-482">Bağlanacak dizinin Kiracı Kimliği.</span><span class="sxs-lookup"><span data-stu-id="88ab4-482">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="88ab4-483">Kimlik `SingleOrg` doğrulaması ile kullanın.</span><span class="sxs-lookup"><span data-stu-id="88ab4-483">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="88ab4-484">Varsayılan değer: `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="88ab4-484">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="88ab4-485">Yeniden yönlendirme URI uygulamanın temel yolu içinde istek yolu.</span><span class="sxs-lookup"><span data-stu-id="88ab4-485">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="88ab4-486">Kimlik `SingleOrg` doğrulaması ile kullanın. `IndividualB2C`</span><span class="sxs-lookup"><span data-stu-id="88ab4-486">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="88ab4-487">Varsayılan değer: `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="88ab4-487">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="88ab4-488">Bu uygulamanın dizine okuma erişimine izin verir.</span><span class="sxs-lookup"><span data-stu-id="88ab4-488">Allows this application read-access to the directory.</span></span> <span data-ttu-id="88ab4-489">Yalnızca kimlik `SingleOrg` doğrulama `MultiOrg` veya kimlik doğrulama için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="88ab4-489">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="88ab4-490">oluşturulan şablondan *launchSettings.json* hariç tutar.</span><span class="sxs-lookup"><span data-stu-id="88ab4-490">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="88ab4-491">HTTPS'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="88ab4-491">Turns off HTTPS.</span></span> <span data-ttu-id="88ab4-492">Bu seçenek yalnızca `Individual`, `IndividualB2C` `SingleOrg`, `MultiOrg` , , , veya kullanılmazsa geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="88ab4-492">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="88ab4-493">SQLite yerine LocalDB'nin kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="88ab4-493">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="88ab4-494">Yalnızca kimlik `Individual` doğrulama `IndividualB2C` veya kimlik doğrulama için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="88ab4-494">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="88ab4-495">Hedef için [çerçeve](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="88ab4-495">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="88ab4-496">Seçenek .NET Core 3.0 SDK beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="88ab4-496">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="88ab4-497">Aşağıdaki tablo, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerleri listeler:</span><span class="sxs-lookup"><span data-stu-id="88ab4-497">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="88ab4-498">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="88ab4-498">SDK version</span></span> | <span data-ttu-id="88ab4-499">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="88ab4-499">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="88ab4-500">3.1</span><span class="sxs-lookup"><span data-stu-id="88ab4-500">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="88ab4-501">3,0</span><span class="sxs-lookup"><span data-stu-id="88ab4-501">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="88ab4-502">Proje oluşturma sırasında örtülü bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="88ab4-502">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="88ab4-503">Projeye BrowserLink'i içerir.</span><span class="sxs-lookup"><span data-stu-id="88ab4-503">Includes BrowserLink in the project.</span></span> <span data-ttu-id="88ab4-504">Seçenek .NET Core 2.2 ve 3.1 SDK'da kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="88ab4-504">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

- **`-rrc|--razor-runtime-compilation`**

  <span data-ttu-id="88ab4-505">Hata Ayıklama yapılarında [ustura çalışma zamanı derlemesi](/aspnet/core/mvc/views/view-compilation#runtime-compilation) kullanacak şekilde yapılandırıp yapılandırılmamasını belirler.</span><span class="sxs-lookup"><span data-stu-id="88ab4-505">Determines if the project is configured to use [Razor runtime compilation](/aspnet/core/mvc/views/view-compilation#runtime-compilation) in Debug builds.</span></span> <span data-ttu-id="88ab4-506">Seçenek .NET Core 3.1 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="88ab4-506">Option available since .NET Core 3.1 SDK.</span></span>

***

### <a name="angular-react"></a><a name="spa"></a><span data-ttu-id="88ab4-507">açısal, tepki</span><span class="sxs-lookup"><span data-stu-id="88ab4-507">angular, react</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="88ab4-508">Kullanılacak kimlik doğrulama türü.</span><span class="sxs-lookup"><span data-stu-id="88ab4-508">The type of authentication to use.</span></span> <span data-ttu-id="88ab4-509">.NET Core 3.0 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="88ab4-509">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="88ab4-510">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="88ab4-510">The possible values are:</span></span>

  - <span data-ttu-id="88ab4-511">`None`- Kimlik doğrulaması yok (Varsayılan).</span><span class="sxs-lookup"><span data-stu-id="88ab4-511">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="88ab4-512">`Individual`- Bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="88ab4-512">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="88ab4-513">oluşturulan şablondan *launchSettings.json* hariç tutar.</span><span class="sxs-lookup"><span data-stu-id="88ab4-513">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="88ab4-514">Proje oluşturma sırasında örtülü bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="88ab4-514">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="88ab4-515">HTTPS'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="88ab4-515">Turns off HTTPS.</span></span> <span data-ttu-id="88ab4-516">Bu seçenek yalnızca kimlik `None`doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="88ab4-516">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="88ab4-517">SQLite yerine LocalDB'nin kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="88ab4-517">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="88ab4-518">Yalnızca kimlik `Individual` doğrulama `IndividualB2C` veya kimlik doğrulama için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="88ab4-518">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="88ab4-519">.NET Core 3.0 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="88ab4-519">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="88ab4-520">Hedef için [çerçeve](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="88ab4-520">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="88ab4-521">Seçenek .NET Core 2.2 SDK'da kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="88ab4-521">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="88ab4-522">Aşağıdaki tablo, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerleri listeler:</span><span class="sxs-lookup"><span data-stu-id="88ab4-522">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="88ab4-523">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="88ab4-523">SDK version</span></span> | <span data-ttu-id="88ab4-524">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="88ab4-524">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="88ab4-525">3.1</span><span class="sxs-lookup"><span data-stu-id="88ab4-525">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="88ab4-526">3,0</span><span class="sxs-lookup"><span data-stu-id="88ab4-526">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="88ab4-527">2.1</span><span class="sxs-lookup"><span data-stu-id="88ab4-527">2.1</span></span>         | `netcoreapp2.0` |

***

### <a name="reactredux"></a><span data-ttu-id="88ab4-528">reactredux</span><span class="sxs-lookup"><span data-stu-id="88ab4-528">reactredux</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="88ab4-529">oluşturulan şablondan *launchSettings.json* hariç tutar.</span><span class="sxs-lookup"><span data-stu-id="88ab4-529">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="88ab4-530">Hedef için [çerçeve](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="88ab4-530">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="88ab4-531">Seçenek .NET Core 2.2 SDK'da kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="88ab4-531">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="88ab4-532">Aşağıdaki tablo, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerleri listeler:</span><span class="sxs-lookup"><span data-stu-id="88ab4-532">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="88ab4-533">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="88ab4-533">SDK version</span></span> | <span data-ttu-id="88ab4-534">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="88ab4-534">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="88ab4-535">3.1</span><span class="sxs-lookup"><span data-stu-id="88ab4-535">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="88ab4-536">3,0</span><span class="sxs-lookup"><span data-stu-id="88ab4-536">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="88ab4-537">2.1</span><span class="sxs-lookup"><span data-stu-id="88ab4-537">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="88ab4-538">Proje oluşturma sırasında örtülü bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="88ab4-538">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="88ab4-539">HTTPS'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="88ab4-539">Turns off HTTPS.</span></span>

***

### <a name="razorclasslib"></a><span data-ttu-id="88ab4-540">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="88ab4-540">razorclasslib</span></span>

- **`--no-restore`**

  <span data-ttu-id="88ab4-541">Proje oluşturma sırasında örtülü bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="88ab4-541">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="88ab4-542">Bu kitaplığa bileşenlere ek olarak geleneksel Razor sayfaları ve Görünümler eklemeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="88ab4-542">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="88ab4-543">.NET Core 3.0 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="88ab4-543">Available since .NET Core 3.0 SDK.</span></span>

***
  
### <a name="webapi"></a><span data-ttu-id="88ab4-544">webapi</span><span class="sxs-lookup"><span data-stu-id="88ab4-544">webapi</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="88ab4-545">Kullanılacak kimlik doğrulama türü.</span><span class="sxs-lookup"><span data-stu-id="88ab4-545">The type of authentication to use.</span></span> <span data-ttu-id="88ab4-546">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="88ab4-546">The possible values are:</span></span>

  - <span data-ttu-id="88ab4-547">`None`- Kimlik doğrulaması yok (Varsayılan).</span><span class="sxs-lookup"><span data-stu-id="88ab4-547">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="88ab4-548">`IndividualB2C`- Azure AD B2C ile bireysel kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="88ab4-548">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="88ab4-549">`SingleOrg`- Tek bir kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="88ab4-549">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="88ab4-550">`Windows`- Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="88ab4-550">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="88ab4-551">Bağlanmak için Azure Active Directory B2C örneği.</span><span class="sxs-lookup"><span data-stu-id="88ab4-551">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="88ab4-552">Kimlik `IndividualB2C` doğrulaması ile kullanın.</span><span class="sxs-lookup"><span data-stu-id="88ab4-552">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="88ab4-553">Varsayılan değer: `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="88ab4-553">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="88ab4-554">Bu proje için oturum açma ve kaydolma ilkesi kimliği.</span><span class="sxs-lookup"><span data-stu-id="88ab4-554">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="88ab4-555">Kimlik `IndividualB2C` doğrulaması ile kullanın.</span><span class="sxs-lookup"><span data-stu-id="88ab4-555">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="88ab4-556">Bağlanmak için Azure Etkin Dizin örneği.</span><span class="sxs-lookup"><span data-stu-id="88ab4-556">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="88ab4-557">Kimlik `SingleOrg` doğrulaması ile kullanın.</span><span class="sxs-lookup"><span data-stu-id="88ab4-557">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="88ab4-558">Varsayılan değer: `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="88ab4-558">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="88ab4-559">Bu projenin Istemci Kimliği.</span><span class="sxs-lookup"><span data-stu-id="88ab4-559">The Client ID for this project.</span></span> <span data-ttu-id="88ab4-560">Kimlik `IndividualB2C` doğrulaması ile kullanın. `SingleOrg`</span><span class="sxs-lookup"><span data-stu-id="88ab4-560">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="88ab4-561">Varsayılan değer: `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="88ab4-561">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="88ab4-562">Dizin kiracı için etki alanı.</span><span class="sxs-lookup"><span data-stu-id="88ab4-562">The domain for the directory tenant.</span></span> <span data-ttu-id="88ab4-563">Kimlik `IndividualB2C` doğrulaması ile kullanın. `SingleOrg`</span><span class="sxs-lookup"><span data-stu-id="88ab4-563">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="88ab4-564">Varsayılan değer: `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="88ab4-564">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="88ab4-565">Bağlanacak dizinin Kiracı Kimliği.</span><span class="sxs-lookup"><span data-stu-id="88ab4-565">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="88ab4-566">Kimlik `SingleOrg` doğrulaması ile kullanın.</span><span class="sxs-lookup"><span data-stu-id="88ab4-566">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="88ab4-567">Varsayılan değer: `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="88ab4-567">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="88ab4-568">Bu uygulamanın dizine okuma erişimine izin verir.</span><span class="sxs-lookup"><span data-stu-id="88ab4-568">Allows this application read-access to the directory.</span></span> <span data-ttu-id="88ab4-569">Yalnızca kimlik `SingleOrg` doğrulama için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="88ab4-569">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="88ab4-570">oluşturulan şablondan *launchSettings.json* hariç tutar.</span><span class="sxs-lookup"><span data-stu-id="88ab4-570">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="88ab4-571">HTTPS'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="88ab4-571">Turns off HTTPS.</span></span> <span data-ttu-id="88ab4-572">`app.UseHsts`ve `app.UseHttpsRedirection` `Startup.Configure`eklenmez.</span><span class="sxs-lookup"><span data-stu-id="88ab4-572">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="88ab4-573">Bu seçenek yalnızca `IndividualB2C` kimlik `SingleOrg` doğrulaması için kullanılıyorsa veya kullanılmamışsa geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="88ab4-573">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="88ab4-574">SQLite yerine LocalDB'nin kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="88ab4-574">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="88ab4-575">Yalnızca kimlik `IndividualB2C` doğrulama için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="88ab4-575">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="88ab4-576">Hedef için [çerçeve](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="88ab4-576">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="88ab4-577">Seçenek .NET Core 2.2 SDK'da kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="88ab4-577">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="88ab4-578">Aşağıdaki tablo, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerleri listeler:</span><span class="sxs-lookup"><span data-stu-id="88ab4-578">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="88ab4-579">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="88ab4-579">SDK version</span></span> | <span data-ttu-id="88ab4-580">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="88ab4-580">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="88ab4-581">3.1</span><span class="sxs-lookup"><span data-stu-id="88ab4-581">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="88ab4-582">3,0</span><span class="sxs-lookup"><span data-stu-id="88ab4-582">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="88ab4-583">2.1</span><span class="sxs-lookup"><span data-stu-id="88ab4-583">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="88ab4-584">Proje oluşturma sırasında örtülü bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="88ab4-584">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="globaljson"></a><span data-ttu-id="88ab4-585">globaljson</span><span class="sxs-lookup"><span data-stu-id="88ab4-585">globaljson</span></span>

- **`--sdk-version <VERSION_NUMBER>`**

  <span data-ttu-id="88ab4-586">.NET Core SDK sürümünü *global.json* dosyasında kullanmak üzere belirtir.</span><span class="sxs-lookup"><span data-stu-id="88ab4-586">Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="88ab4-587">Örnekler</span><span class="sxs-lookup"><span data-stu-id="88ab4-587">Examples</span></span>

- <span data-ttu-id="88ab4-588">Şablon adını belirterek c# konsolu uygulama projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="88ab4-588">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="88ab4-589">Geçerli dizinde bir F# konsolu uygulama projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="88ab4-589">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang F#
  ```

- <span data-ttu-id="88ab4-590">Belirtilen dizinde bir .NET Standart sınıf kitaplığı projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="88ab4-590">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="88ab4-591">Geçerli dizinde kimlik doğrulaması olmadan yeni bir ASP.NET Core C# MVC projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="88ab4-591">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="88ab4-592">Yeni bir xUnit projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="88ab4-592">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="88ab4-593">Tek Sayfa Uygulaması (SPA) şablonları için kullanılabilen tüm şablonları listeleyin:</span><span class="sxs-lookup"><span data-stu-id="88ab4-593">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="88ab4-594">*Biz* alt dize ile eşleşen tüm şablonları listeleyin.</span><span class="sxs-lookup"><span data-stu-id="88ab4-594">List all templates matching the *we* substring.</span></span> <span data-ttu-id="88ab4-595">Tam eşleşme bulunamadı, bu nedenle alt dize eşleştirme hem kısa ad hem de ad sütunlarına karşı çalışır.</span><span class="sxs-lookup"><span data-stu-id="88ab4-595">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="88ab4-596">Ng eşleşen şablonu çağırmak için girişimi *.*</span><span class="sxs-lookup"><span data-stu-id="88ab4-596">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="88ab4-597">Tek bir eşleşme belirlenemezse, kısmi eşleşmeolan şablonları listeleyin.</span><span class="sxs-lookup"><span data-stu-id="88ab4-597">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="88ab4-598">ASP.NET Core için SPA şablonlarının 2.0 sürümünü yükleyin:</span><span class="sxs-lookup"><span data-stu-id="88ab4-598">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="88ab4-599">Yüklenen şablonları ve bunlarla ilgili ayrıntıları ve bunları nasıl kaldırılabildiğini listeleyin:</span><span class="sxs-lookup"><span data-stu-id="88ab4-599">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="88ab4-600">Geçerli dizinde SDK sürümünü 3.1.101 olarak ayarlayarak *global.json* oluşturun:</span><span class="sxs-lookup"><span data-stu-id="88ab4-600">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="88ab4-601">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="88ab4-601">See also</span></span>

- [<span data-ttu-id="88ab4-602">Dotnet yeni için özel şablonlar</span><span class="sxs-lookup"><span data-stu-id="88ab4-602">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="88ab4-603">Dotnet new için özel şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="88ab4-603">Create a custom template for dotnet new</span></span>](../tutorials/cli-templates-create-item-template.md)
- [<span data-ttu-id="88ab4-604">dotnet/dotnet-şablon-örnekleri GitHub repo</span><span class="sxs-lookup"><span data-stu-id="88ab4-604">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="88ab4-605">dotnet yeni için kullanılabilir şablonlar</span><span class="sxs-lookup"><span data-stu-id="88ab4-605">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
