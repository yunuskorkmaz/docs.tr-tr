---
title: dotnet yeni komut
description: Dotnet yeni komutu, belirtilen şablonu temel alan yeni .NET Core projeleri oluşturur.
ms.date: 04/10/2020
ms.openlocfilehash: 1979f98a6005a414acc64c5eaa086a88aca9f033
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102833"
---
# <a name="dotnet-new"></a><span data-ttu-id="5cb5d-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="5cb5d-103">dotnet new</span></span>

<span data-ttu-id="5cb5d-104">**Bu makale şu şekilde dir:** ✔️ .NET Core 2.0 SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="5cb5d-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="5cb5d-105">Adı</span><span class="sxs-lookup"><span data-stu-id="5cb5d-105">Name</span></span>

<span data-ttu-id="5cb5d-106">`dotnet new`- Belirtilen şablonu temel alan yeni bir proje, yapılandırma dosyası veya çözüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5cb5d-107">Özet</span><span class="sxs-lookup"><span data-stu-id="5cb5d-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install {PATH|NUGET_ID}]
    [-lang|--language {C#|F#|VB}] [-n|--name <OUTPUT_NAME>]
    [--nuget-source <SOURCE>] [-o|--output <OUTPUT_DIRECTORY>]
    [-u|--uninstall] [--update-apply] [--update-check] [Template options]

dotnet new <TEMPLATE> [-l|--list] [--type <TYPE>]

dotnet new -h|--help
```

## <a name="description"></a><span data-ttu-id="5cb5d-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5cb5d-108">Description</span></span>

<span data-ttu-id="5cb5d-109">Komut, `dotnet new` şablona dayalı bir .NET Core projesi veya diğer yapılar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-109">The `dotnet new` command creates a .NET Core project or other artifacts based on a template.</span></span>

<span data-ttu-id="5cb5d-110">Komut, belirtilen şablon ve seçenekleri temel alan disküzerinde yapıları oluşturmak için [şablon altyapısını](https://github.com/dotnet/templating) çağırır.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="5cb5d-111">Örtük geri yükleme</span><span class="sxs-lookup"><span data-stu-id="5cb5d-111">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="5cb5d-112">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="5cb5d-112">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="5cb5d-113">Komut çağrıldığında anında başlatılabilmek için şablon.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-113">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="5cb5d-114">Her şablonun geçirebileceğiniz belirli seçenekleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-114">Each template might have specific options you can pass.</span></span> <span data-ttu-id="5cb5d-115">Daha fazla bilgi için [Şablon seçeneklerine](#template-options)bakın.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-115">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="5cb5d-116">Yüklenen tüm `dotnet new --list` şablonların listesini görmek için çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-116">You can run `dotnet new --list` to see a list of all installed templates.</span></span> <span data-ttu-id="5cb5d-117">Döndürülen `TEMPLATE` tablodaki **Şablonlar** veya **Kısa Ad** sütunundaki metindeki değer tam eşleşme değilse, bu iki sütunda bir alt dize eşleşmesi gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-117">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="5cb5d-118">.NET Core 3.0 SDK ile başlayarak, cli aşağıdaki koşullarda `dotnet new` komutu çağırdığınızda NuGet.org şablonları arar:</span><span class="sxs-lookup"><span data-stu-id="5cb5d-118">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="5cb5d-119">CLI, çağrıştırırken bir şablon eşleşmesi `dotnet new`bulamazsa, kısmi bile değildir.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-119">If the CLI can't find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="5cb5d-120">Şablonun daha yeni bir sürümü varsa.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-120">If there's a newer version of the template available.</span></span> <span data-ttu-id="5cb5d-121">Bu durumda, proje veya yapı oluşturulur, ancak CLI şablonun güncelleştirilmiş bir sürümü hakkında sizi uyarır.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-121">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="5cb5d-122">Komut varsayılan şablonlar listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-122">The command contains a default list of templates.</span></span> <span data-ttu-id="5cb5d-123">Kullanılabilir `dotnet new -l` şablonların listesini almak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-123">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="5cb5d-124">Aşağıdaki tabloda .NET Core SDK ile önceden yüklenmiş gelen şablonlar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-124">The following table shows the templates that come pre-installed with the .NET Core SDK.</span></span> <span data-ttu-id="5cb5d-125">Şabloniçin varsayılan dil parantez içinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-125">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="5cb5d-126">Belirli şablon seçeneklerini görmek için kısa ad bağlantısını tıklatın.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-126">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="5cb5d-127">Şablonlar</span><span class="sxs-lookup"><span data-stu-id="5cb5d-127">Templates</span></span>                                    | <span data-ttu-id="5cb5d-128">Kısa ad</span><span class="sxs-lookup"><span data-stu-id="5cb5d-128">Short name</span></span>                      | <span data-ttu-id="5cb5d-129">Dil</span><span class="sxs-lookup"><span data-stu-id="5cb5d-129">Language</span></span>     | <span data-ttu-id="5cb5d-130">Etiketler</span><span class="sxs-lookup"><span data-stu-id="5cb5d-130">Tags</span></span>                                  | <span data-ttu-id="5cb5d-131">Tanıttı</span><span class="sxs-lookup"><span data-stu-id="5cb5d-131">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="5cb5d-132">Konsol Uygulaması</span><span class="sxs-lookup"><span data-stu-id="5cb5d-132">Console Application</span></span>                          | [<span data-ttu-id="5cb5d-133">Konsol</span><span class="sxs-lookup"><span data-stu-id="5cb5d-133">console</span></span>](#console)             | <span data-ttu-id="5cb5d-134">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="5cb5d-134">[C#], F#, VB</span></span> | <span data-ttu-id="5cb5d-135">Ortak/Konsol</span><span class="sxs-lookup"><span data-stu-id="5cb5d-135">Common/Console</span></span>                        | <span data-ttu-id="5cb5d-136">1.0</span><span class="sxs-lookup"><span data-stu-id="5cb5d-136">1.0</span></span>        |
| <span data-ttu-id="5cb5d-137">Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="5cb5d-137">Class library</span></span>                                | [<span data-ttu-id="5cb5d-138">classlib</span><span class="sxs-lookup"><span data-stu-id="5cb5d-138">classlib</span></span>](#classlib)           | <span data-ttu-id="5cb5d-139">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="5cb5d-139">[C#], F#, VB</span></span> | <span data-ttu-id="5cb5d-140">Ortak / Kütüphane</span><span class="sxs-lookup"><span data-stu-id="5cb5d-140">Common/Library</span></span>                        | <span data-ttu-id="5cb5d-141">1.0</span><span class="sxs-lookup"><span data-stu-id="5cb5d-141">1.0</span></span>        |
| <span data-ttu-id="5cb5d-142">WPF Uygulaması</span><span class="sxs-lookup"><span data-stu-id="5cb5d-142">WPF Application</span></span>                              | [<span data-ttu-id="5cb5d-143">Wpf</span><span class="sxs-lookup"><span data-stu-id="5cb5d-143">wpf</span></span>](#wpf)                     | <span data-ttu-id="5cb5d-144">[C#]</span><span class="sxs-lookup"><span data-stu-id="5cb5d-144">[C#]</span></span>         | <span data-ttu-id="5cb5d-145">Ortak/WPF</span><span class="sxs-lookup"><span data-stu-id="5cb5d-145">Common/WPF</span></span>                            | <span data-ttu-id="5cb5d-146">3,0</span><span class="sxs-lookup"><span data-stu-id="5cb5d-146">3.0</span></span>        |
| <span data-ttu-id="5cb5d-147">WPF Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="5cb5d-147">WPF Class library</span></span>                            | [<span data-ttu-id="5cb5d-148">wpflib</span><span class="sxs-lookup"><span data-stu-id="5cb5d-148">wpflib</span></span>](#wpf)                  | <span data-ttu-id="5cb5d-149">[C#]</span><span class="sxs-lookup"><span data-stu-id="5cb5d-149">[C#]</span></span>         | <span data-ttu-id="5cb5d-150">Ortak/WPF</span><span class="sxs-lookup"><span data-stu-id="5cb5d-150">Common/WPF</span></span>                            | <span data-ttu-id="5cb5d-151">3,0</span><span class="sxs-lookup"><span data-stu-id="5cb5d-151">3.0</span></span>        |
| <span data-ttu-id="5cb5d-152">WPF Özel Denetim Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="5cb5d-152">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="5cb5d-153">wpfcustomcontrollib</span><span class="sxs-lookup"><span data-stu-id="5cb5d-153">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="5cb5d-154">[C#]</span><span class="sxs-lookup"><span data-stu-id="5cb5d-154">[C#]</span></span>         | <span data-ttu-id="5cb5d-155">Ortak/WPF</span><span class="sxs-lookup"><span data-stu-id="5cb5d-155">Common/WPF</span></span>                            | <span data-ttu-id="5cb5d-156">3,0</span><span class="sxs-lookup"><span data-stu-id="5cb5d-156">3.0</span></span>        |
| <span data-ttu-id="5cb5d-157">WPF Kullanıcı Kontrol Kütüphanesi</span><span class="sxs-lookup"><span data-stu-id="5cb5d-157">WPF User Control Library</span></span>                     | [<span data-ttu-id="5cb5d-158">wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="5cb5d-158">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="5cb5d-159">[C#]</span><span class="sxs-lookup"><span data-stu-id="5cb5d-159">[C#]</span></span>         | <span data-ttu-id="5cb5d-160">Ortak/WPF</span><span class="sxs-lookup"><span data-stu-id="5cb5d-160">Common/WPF</span></span>                            | <span data-ttu-id="5cb5d-161">3,0</span><span class="sxs-lookup"><span data-stu-id="5cb5d-161">3.0</span></span>        |
| <span data-ttu-id="5cb5d-162">Windows Formları (WinForms) Uygulaması</span><span class="sxs-lookup"><span data-stu-id="5cb5d-162">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="5cb5d-163">Winforms</span><span class="sxs-lookup"><span data-stu-id="5cb5d-163">winforms</span></span>](#winforms)           | <span data-ttu-id="5cb5d-164">[C#]</span><span class="sxs-lookup"><span data-stu-id="5cb5d-164">[C#]</span></span>         | <span data-ttu-id="5cb5d-165">Ortak/WinForm'lar</span><span class="sxs-lookup"><span data-stu-id="5cb5d-165">Common/WinForms</span></span>                       | <span data-ttu-id="5cb5d-166">3,0</span><span class="sxs-lookup"><span data-stu-id="5cb5d-166">3.0</span></span>        |
| <span data-ttu-id="5cb5d-167">Windows Formları (WinForms) Sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="5cb5d-167">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="5cb5d-168">winformslib</span><span class="sxs-lookup"><span data-stu-id="5cb5d-168">winformslib</span></span>](#winforms)        | <span data-ttu-id="5cb5d-169">[C#]</span><span class="sxs-lookup"><span data-stu-id="5cb5d-169">[C#]</span></span>         | <span data-ttu-id="5cb5d-170">Ortak/WinForm'lar</span><span class="sxs-lookup"><span data-stu-id="5cb5d-170">Common/WinForms</span></span>                       | <span data-ttu-id="5cb5d-171">3,0</span><span class="sxs-lookup"><span data-stu-id="5cb5d-171">3.0</span></span>        |
| <span data-ttu-id="5cb5d-172">İşçi Hizmeti</span><span class="sxs-lookup"><span data-stu-id="5cb5d-172">Worker Service</span></span>                               | [<span data-ttu-id="5cb5d-173">Işçi</span><span class="sxs-lookup"><span data-stu-id="5cb5d-173">worker</span></span>](#web-others)           | <span data-ttu-id="5cb5d-174">[C#]</span><span class="sxs-lookup"><span data-stu-id="5cb5d-174">[C#]</span></span>         | <span data-ttu-id="5cb5d-175">Ortak/Çalışan/Web</span><span class="sxs-lookup"><span data-stu-id="5cb5d-175">Common/Worker/Web</span></span>                     | <span data-ttu-id="5cb5d-176">3,0</span><span class="sxs-lookup"><span data-stu-id="5cb5d-176">3.0</span></span>        |
| <span data-ttu-id="5cb5d-177">Ünite Test Projesi</span><span class="sxs-lookup"><span data-stu-id="5cb5d-177">Unit Test Project</span></span>                            | [<span data-ttu-id="5cb5d-178">Mstest</span><span class="sxs-lookup"><span data-stu-id="5cb5d-178">mstest</span></span>](#test)                 | <span data-ttu-id="5cb5d-179">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="5cb5d-179">[C#], F#, VB</span></span> | <span data-ttu-id="5cb5d-180">Test /MSTest</span><span class="sxs-lookup"><span data-stu-id="5cb5d-180">Test/MSTest</span></span>                           | <span data-ttu-id="5cb5d-181">1.0</span><span class="sxs-lookup"><span data-stu-id="5cb5d-181">1.0</span></span>        |
| <span data-ttu-id="5cb5d-182">NUnit 3 Test Projesi</span><span class="sxs-lookup"><span data-stu-id="5cb5d-182">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="5cb5d-183">nunit</span><span class="sxs-lookup"><span data-stu-id="5cb5d-183">nunit</span></span>](#nunit)                  | <span data-ttu-id="5cb5d-184">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="5cb5d-184">[C#], F#, VB</span></span> | <span data-ttu-id="5cb5d-185">Test /NUnit</span><span class="sxs-lookup"><span data-stu-id="5cb5d-185">Test/NUnit</span></span>                            | <span data-ttu-id="5cb5d-186">2.1.400</span><span class="sxs-lookup"><span data-stu-id="5cb5d-186">2.1.400</span></span>    |
| <span data-ttu-id="5cb5d-187">NUnit 3 Test Öğesi</span><span class="sxs-lookup"><span data-stu-id="5cb5d-187">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="5cb5d-188">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="5cb5d-188">[C#], F#, VB</span></span> | <span data-ttu-id="5cb5d-189">Test /NUnit</span><span class="sxs-lookup"><span data-stu-id="5cb5d-189">Test/NUnit</span></span>                            | <span data-ttu-id="5cb5d-190">2,2</span><span class="sxs-lookup"><span data-stu-id="5cb5d-190">2.2</span></span>        |
| <span data-ttu-id="5cb5d-191">xUnit Test Projesi</span><span class="sxs-lookup"><span data-stu-id="5cb5d-191">xUnit Test Project</span></span>                           | [<span data-ttu-id="5cb5d-192">xunit</span><span class="sxs-lookup"><span data-stu-id="5cb5d-192">xunit</span></span>](#test)                  | <span data-ttu-id="5cb5d-193">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="5cb5d-193">[C#], F#, VB</span></span> | <span data-ttu-id="5cb5d-194">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="5cb5d-194">Test/xUnit</span></span>                            | <span data-ttu-id="5cb5d-195">1.0</span><span class="sxs-lookup"><span data-stu-id="5cb5d-195">1.0</span></span>        |
| <span data-ttu-id="5cb5d-196">Jilet Bileşeni</span><span class="sxs-lookup"><span data-stu-id="5cb5d-196">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="5cb5d-197">[C#]</span><span class="sxs-lookup"><span data-stu-id="5cb5d-197">[C#]</span></span>         | <span data-ttu-id="5cb5d-198">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5cb5d-198">Web/ASP.NET</span></span>                           | <span data-ttu-id="5cb5d-199">3,0</span><span class="sxs-lookup"><span data-stu-id="5cb5d-199">3.0</span></span>        |
| <span data-ttu-id="5cb5d-200">Jilet Sayfası</span><span class="sxs-lookup"><span data-stu-id="5cb5d-200">Razor Page</span></span>                                   | [<span data-ttu-id="5cb5d-201">Sayfası</span><span class="sxs-lookup"><span data-stu-id="5cb5d-201">page</span></span>](#page)                   | <span data-ttu-id="5cb5d-202">[C#]</span><span class="sxs-lookup"><span data-stu-id="5cb5d-202">[C#]</span></span>         | <span data-ttu-id="5cb5d-203">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5cb5d-203">Web/ASP.NET</span></span>                           | <span data-ttu-id="5cb5d-204">2,0</span><span class="sxs-lookup"><span data-stu-id="5cb5d-204">2.0</span></span>        |
| <span data-ttu-id="5cb5d-205">MVC Görünümİthalat</span><span class="sxs-lookup"><span data-stu-id="5cb5d-205">MVC ViewImports</span></span>                              | [<span data-ttu-id="5cb5d-206">içe görme</span><span class="sxs-lookup"><span data-stu-id="5cb5d-206">viewimports</span></span>](#namespace)       | <span data-ttu-id="5cb5d-207">[C#]</span><span class="sxs-lookup"><span data-stu-id="5cb5d-207">[C#]</span></span>         | <span data-ttu-id="5cb5d-208">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5cb5d-208">Web/ASP.NET</span></span>                           | <span data-ttu-id="5cb5d-209">2,0</span><span class="sxs-lookup"><span data-stu-id="5cb5d-209">2.0</span></span>        |
| <span data-ttu-id="5cb5d-210">MVC Görünüm Başlat</span><span class="sxs-lookup"><span data-stu-id="5cb5d-210">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="5cb5d-211">[C#]</span><span class="sxs-lookup"><span data-stu-id="5cb5d-211">[C#]</span></span>         | <span data-ttu-id="5cb5d-212">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5cb5d-212">Web/ASP.NET</span></span>                           | <span data-ttu-id="5cb5d-213">2,0</span><span class="sxs-lookup"><span data-stu-id="5cb5d-213">2.0</span></span>        |
| <span data-ttu-id="5cb5d-214">Blazor Server Uygulaması</span><span class="sxs-lookup"><span data-stu-id="5cb5d-214">Blazor Server App</span></span>                            | [<span data-ttu-id="5cb5d-215">blazorserver</span><span class="sxs-lookup"><span data-stu-id="5cb5d-215">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="5cb5d-216">[C#]</span><span class="sxs-lookup"><span data-stu-id="5cb5d-216">[C#]</span></span>         | <span data-ttu-id="5cb5d-217">Web/Blazor</span><span class="sxs-lookup"><span data-stu-id="5cb5d-217">Web/Blazor</span></span>                            | <span data-ttu-id="5cb5d-218">3,0</span><span class="sxs-lookup"><span data-stu-id="5cb5d-218">3.0</span></span>        |
| <span data-ttu-id="5cb5d-219">ASP.NET Çekirdek Boş</span><span class="sxs-lookup"><span data-stu-id="5cb5d-219">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="5cb5d-220">Web</span><span class="sxs-lookup"><span data-stu-id="5cb5d-220">web</span></span>](#web)                     | <span data-ttu-id="5cb5d-221">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="5cb5d-221">[C#], F#</span></span>     | <span data-ttu-id="5cb5d-222">Web/Boş</span><span class="sxs-lookup"><span data-stu-id="5cb5d-222">Web/Empty</span></span>                             | <span data-ttu-id="5cb5d-223">1.0</span><span class="sxs-lookup"><span data-stu-id="5cb5d-223">1.0</span></span>        |
| <span data-ttu-id="5cb5d-224">ASP.NET Çekirdek Web Uygulaması (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="5cb5d-224">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="5cb5d-225">Mvc</span><span class="sxs-lookup"><span data-stu-id="5cb5d-225">mvc</span></span>](#web-options)             | <span data-ttu-id="5cb5d-226">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="5cb5d-226">[C#], F#</span></span>     | <span data-ttu-id="5cb5d-227">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="5cb5d-227">Web/MVC</span></span>                               | <span data-ttu-id="5cb5d-228">1.0</span><span class="sxs-lookup"><span data-stu-id="5cb5d-228">1.0</span></span>        |
| <span data-ttu-id="5cb5d-229">ASP.NET Çekirdek Web Uygulaması</span><span class="sxs-lookup"><span data-stu-id="5cb5d-229">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="5cb5d-230">webapp, jilet</span><span class="sxs-lookup"><span data-stu-id="5cb5d-230">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="5cb5d-231">[C#]</span><span class="sxs-lookup"><span data-stu-id="5cb5d-231">[C#]</span></span>         | <span data-ttu-id="5cb5d-232">Web/MVC/Razor Sayfaları</span><span class="sxs-lookup"><span data-stu-id="5cb5d-232">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="5cb5d-233">2.2, 2.0</span><span class="sxs-lookup"><span data-stu-id="5cb5d-233">2.2, 2.0</span></span>   |
| <span data-ttu-id="5cb5d-234">ASP.NET Çekirdek li Açısal</span><span class="sxs-lookup"><span data-stu-id="5cb5d-234">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="5cb5d-235">Açısal</span><span class="sxs-lookup"><span data-stu-id="5cb5d-235">angular</span></span>](#spa)                 | <span data-ttu-id="5cb5d-236">[C#]</span><span class="sxs-lookup"><span data-stu-id="5cb5d-236">[C#]</span></span>         | <span data-ttu-id="5cb5d-237">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="5cb5d-237">Web/MVC/SPA</span></span>                           | <span data-ttu-id="5cb5d-238">2,0</span><span class="sxs-lookup"><span data-stu-id="5cb5d-238">2.0</span></span>        |
| <span data-ttu-id="5cb5d-239">React.js ile ASP.NET Çekirdek</span><span class="sxs-lookup"><span data-stu-id="5cb5d-239">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="5cb5d-240">Tepki</span><span class="sxs-lookup"><span data-stu-id="5cb5d-240">react</span></span>](#spa)                   | <span data-ttu-id="5cb5d-241">[C#]</span><span class="sxs-lookup"><span data-stu-id="5cb5d-241">[C#]</span></span>         | <span data-ttu-id="5cb5d-242">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="5cb5d-242">Web/MVC/SPA</span></span>                           | <span data-ttu-id="5cb5d-243">2,0</span><span class="sxs-lookup"><span data-stu-id="5cb5d-243">2.0</span></span>        |
| <span data-ttu-id="5cb5d-244">React.js ve Redux ile ASP.NET Çekirdek</span><span class="sxs-lookup"><span data-stu-id="5cb5d-244">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="5cb5d-245">reactredux</span><span class="sxs-lookup"><span data-stu-id="5cb5d-245">reactredux</span></span>](#reactredux)       | <span data-ttu-id="5cb5d-246">[C#]</span><span class="sxs-lookup"><span data-stu-id="5cb5d-246">[C#]</span></span>         | <span data-ttu-id="5cb5d-247">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="5cb5d-247">Web/MVC/SPA</span></span>                           | <span data-ttu-id="5cb5d-248">2,0</span><span class="sxs-lookup"><span data-stu-id="5cb5d-248">2.0</span></span>        |
| <span data-ttu-id="5cb5d-249">Razor Sınıf Kütüphanesi</span><span class="sxs-lookup"><span data-stu-id="5cb5d-249">Razor Class Library</span></span>                          | [<span data-ttu-id="5cb5d-250">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="5cb5d-250">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="5cb5d-251">[C#]</span><span class="sxs-lookup"><span data-stu-id="5cb5d-251">[C#]</span></span>         | <span data-ttu-id="5cb5d-252">Web/Razor/Kütüphane/Razor Sınıf Kütüphanesi</span><span class="sxs-lookup"><span data-stu-id="5cb5d-252">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="5cb5d-253">2.1</span><span class="sxs-lookup"><span data-stu-id="5cb5d-253">2.1</span></span>        |
| <span data-ttu-id="5cb5d-254">ASP.NET Core Web API'si</span><span class="sxs-lookup"><span data-stu-id="5cb5d-254">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="5cb5d-255">webapi</span><span class="sxs-lookup"><span data-stu-id="5cb5d-255">webapi</span></span>](#webapi)               | <span data-ttu-id="5cb5d-256">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="5cb5d-256">[C#], F#</span></span>     | <span data-ttu-id="5cb5d-257">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="5cb5d-257">Web/WebAPI</span></span>                            | <span data-ttu-id="5cb5d-258">1.0</span><span class="sxs-lookup"><span data-stu-id="5cb5d-258">1.0</span></span>        |
| <span data-ttu-id="5cb5d-259">ASP.NET Çekirdek gRPC Hizmeti</span><span class="sxs-lookup"><span data-stu-id="5cb5d-259">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="5cb5d-260">grpc</span><span class="sxs-lookup"><span data-stu-id="5cb5d-260">grpc</span></span>](#web-others)             | <span data-ttu-id="5cb5d-261">[C#]</span><span class="sxs-lookup"><span data-stu-id="5cb5d-261">[C#]</span></span>         | <span data-ttu-id="5cb5d-262">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="5cb5d-262">Web/gRPC</span></span>                              | <span data-ttu-id="5cb5d-263">3,0</span><span class="sxs-lookup"><span data-stu-id="5cb5d-263">3.0</span></span>        |
| <span data-ttu-id="5cb5d-264">Protokol Arabellek Dosyası</span><span class="sxs-lookup"><span data-stu-id="5cb5d-264">Protocol Buffer File</span></span>                         | [<span data-ttu-id="5cb5d-265">Proto</span><span class="sxs-lookup"><span data-stu-id="5cb5d-265">proto</span></span>](#namespace)             |              | <span data-ttu-id="5cb5d-266">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="5cb5d-266">Web/gRPC</span></span>                              | <span data-ttu-id="5cb5d-267">3,0</span><span class="sxs-lookup"><span data-stu-id="5cb5d-267">3.0</span></span>        |
| <span data-ttu-id="5cb5d-268">dotnet gitignore dosyası</span><span class="sxs-lookup"><span data-stu-id="5cb5d-268">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="5cb5d-269">Config</span><span class="sxs-lookup"><span data-stu-id="5cb5d-269">Config</span></span>                                | <span data-ttu-id="5cb5d-270">3,0</span><span class="sxs-lookup"><span data-stu-id="5cb5d-270">3.0</span></span>        |
| <span data-ttu-id="5cb5d-271">global.json dosyası</span><span class="sxs-lookup"><span data-stu-id="5cb5d-271">global.json file</span></span>                             | [<span data-ttu-id="5cb5d-272">globaljson</span><span class="sxs-lookup"><span data-stu-id="5cb5d-272">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="5cb5d-273">Config</span><span class="sxs-lookup"><span data-stu-id="5cb5d-273">Config</span></span>                                | <span data-ttu-id="5cb5d-274">2,0</span><span class="sxs-lookup"><span data-stu-id="5cb5d-274">2.0</span></span>        |
| <span data-ttu-id="5cb5d-275">NuGet Config</span><span class="sxs-lookup"><span data-stu-id="5cb5d-275">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="5cb5d-276">Config</span><span class="sxs-lookup"><span data-stu-id="5cb5d-276">Config</span></span>                                | <span data-ttu-id="5cb5d-277">1.0</span><span class="sxs-lookup"><span data-stu-id="5cb5d-277">1.0</span></span>        |
| <span data-ttu-id="5cb5d-278">dotnet yerel araç bildirimi dosyası</span><span class="sxs-lookup"><span data-stu-id="5cb5d-278">dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="5cb5d-279">Config</span><span class="sxs-lookup"><span data-stu-id="5cb5d-279">Config</span></span>                                | <span data-ttu-id="5cb5d-280">3,0</span><span class="sxs-lookup"><span data-stu-id="5cb5d-280">3.0</span></span>        |
| <span data-ttu-id="5cb5d-281">Web Config</span><span class="sxs-lookup"><span data-stu-id="5cb5d-281">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="5cb5d-282">Config</span><span class="sxs-lookup"><span data-stu-id="5cb5d-282">Config</span></span>                                | <span data-ttu-id="5cb5d-283">1.0</span><span class="sxs-lookup"><span data-stu-id="5cb5d-283">1.0</span></span>        |
| <span data-ttu-id="5cb5d-284">Çözüm Dosyası</span><span class="sxs-lookup"><span data-stu-id="5cb5d-284">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="5cb5d-285">Çözüm</span><span class="sxs-lookup"><span data-stu-id="5cb5d-285">Solution</span></span>                              | <span data-ttu-id="5cb5d-286">1.0</span><span class="sxs-lookup"><span data-stu-id="5cb5d-286">1.0</span></span>        |

## <a name="options"></a><span data-ttu-id="5cb5d-287">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="5cb5d-287">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="5cb5d-288">Verilen komut çalıştırılırsa ne olacağının bir özetini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-288">Displays a summary of what would happen if the given command were run.</span></span> <span data-ttu-id="5cb5d-289">.NET Core 2.2 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-289">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="5cb5d-290">Varolan dosyaları değiştirse bile içeriği oluşturulmaya zorlar.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-290">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="5cb5d-291">Bu, seçilen şablon çıktı dizinindeki varolan dosyaları geçersiz kılacaksa gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-291">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="5cb5d-292">Komut için yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-292">Prints out help for the command.</span></span> <span data-ttu-id="5cb5d-293">Komutun `dotnet new` kendisi veya herhangi bir şablon için çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-293">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="5cb5d-294">Örneğin, `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-294">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="5cb5d-295">Bir şablon paketi yükler `PATH` `NUGET_ID` veya sağlanan.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-295">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="5cb5d-296">Bir şablon paketinin ön sürüm sürümünü yüklemek istiyorsanız, sürümü ' nin `<package-name>::<package-version>`biçiminde belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-296">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="5cb5d-297">Varsayılan `dotnet new` olarak, \* en son kararlı paket sürümünü temsil eden sürüm için geçer.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-297">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="5cb5d-298">[Örnekler](#examples) bölümündeki bir örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-298">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="5cb5d-299">Bu komutu çalıştırdığınızda şablonun bir sürümü zaten yüklenmişse, sürüm belirtilmemişse şablon belirtilen sürüme veya en son kararlı sürüme güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-299">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="5cb5d-300">Özel şablonlar oluşturma hakkında bilgi [için, nokta yeni için Özel şablonlara](custom-templates.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-300">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="5cb5d-301">Belirtilen adı içeren şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-301">Lists templates containing the specified name.</span></span> <span data-ttu-id="5cb5d-302">Ad belirtilmemişse, tüm şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-302">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="5cb5d-303">Oluşturulacak şablonun dili.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-303">The language of the template to create.</span></span> <span data-ttu-id="5cb5d-304">Kabul edilen dil şablona göre değişir [(bağımsız değişkenler](#arguments) bölümündeki varsayılanlara bakın).</span><span class="sxs-lookup"><span data-stu-id="5cb5d-304">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="5cb5d-305">Bazı şablonlar için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-305">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="5cb5d-306">Bazı kabuklar `#` özel bir karakter olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-306">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="5cb5d-307">Bu gibi durumlarda, dil parametre değerini tırnak içinde içine atl..</span><span class="sxs-lookup"><span data-stu-id="5cb5d-307">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="5cb5d-308">Örneğin, `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-308">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="5cb5d-309">Oluşturulan çıktının adı.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-309">The name for the created output.</span></span> <span data-ttu-id="5cb5d-310">Ad belirtilmemişse, geçerli dizinin adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-310">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source <SOURCE>`**

  <span data-ttu-id="5cb5d-311">Yükleme sırasında kullanılacak bir NuGet kaynağı belirtir.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-311">Specifies a NuGet source to use during install.</span></span> <span data-ttu-id="5cb5d-312">.NET Core 2.1 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-312">Available since .NET Core 2.1 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="5cb5d-313">Oluşturulan çıktıyı yerleştirmek için yer.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-313">Location to place the generated output.</span></span> <span data-ttu-id="5cb5d-314">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-314">The default is the current directory.</span></span>

- **`--type <TYPE>`**

  <span data-ttu-id="5cb5d-315">Kullanılabilir türleri temel alan şablonları filtreler.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-315">Filters templates based on available types.</span></span> <span data-ttu-id="5cb5d-316">Önceden tanımlanmış `project`değerler `item`, `other`, veya .</span><span class="sxs-lookup"><span data-stu-id="5cb5d-316">Predefined values are `project`, `item`, or `other`.</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="5cb5d-317">Bir şablon paketini `PATH` kaldırın `NUGET_ID` veya sağlanan.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-317">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="5cb5d-318">`<PATH|NUGET_ID>` Değer belirtilmediği zaman, şu anda yüklü olan tüm şablon paketleri ve ilişkili şablonları görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-318">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="5cb5d-319">`NUGET_ID`Belirtirken, sürüm numarasını eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-319">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="5cb5d-320">Bu seçenek için bir parametre belirtmezseniz, komut yüklenen şablonları ve bunlarla ilgili ayrıntıları listeler.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-320">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="5cb5d-321">Bir şablonu kaldırmak `PATH`için , yolu tam olarak nitelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-321">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="5cb5d-322">Örneğin, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* çalışır, ancak içeren klasörden *./GarciaSoftware.ConsoleTemplate.CSharp* çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-322">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="5cb5d-323">Şablon yolunuza sonlandırma dizini kesimieklemeyi eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-323">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="5cb5d-324">Şu anda yüklü olan ve bunları yükleyen şablon paketleri için güncelleştirmeolup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-324">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="5cb5d-325">.NET Core 3.0 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-325">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="5cb5d-326">Şu anda yüklü olan şablon paketleri için güncelleştirme olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-326">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="5cb5d-327">.NET Core 3.0 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-327">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="5cb5d-328">Şablon seçenekleri</span><span class="sxs-lookup"><span data-stu-id="5cb5d-328">Template options</span></span>

<span data-ttu-id="5cb5d-329">Her proje şablonunda ek seçenekler olabilir.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-329">Each project template may have additional options available.</span></span> <span data-ttu-id="5cb5d-330">Çekirdek şablonları aşağıdaki ek seçeneklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="5cb5d-330">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="5cb5d-331">console</span><span class="sxs-lookup"><span data-stu-id="5cb5d-331">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="5cb5d-332">Hedef için [çerçeve](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-332">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="5cb5d-333">.NET Core 3.0 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-333">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="5cb5d-334">Aşağıdaki tablo, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerleri listeler:</span><span class="sxs-lookup"><span data-stu-id="5cb5d-334">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="5cb5d-335">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="5cb5d-335">SDK version</span></span> | <span data-ttu-id="5cb5d-336">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="5cb5d-336">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="5cb5d-337">3.1</span><span class="sxs-lookup"><span data-stu-id="5cb5d-337">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="5cb5d-338">3,0</span><span class="sxs-lookup"><span data-stu-id="5cb5d-338">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="5cb5d-339">Oluşturulan `LangVersion` proje dosyasındaki özelliği ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-339">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="5cb5d-340">Örneğin, C# 7.3'u kullanmak için kullanın. `--langVersion 7.3`</span><span class="sxs-lookup"><span data-stu-id="5cb5d-340">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="5cb5d-341">F# için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-341">Not supported for F#.</span></span> <span data-ttu-id="5cb5d-342">.NET Core 2.2 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-342">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="5cb5d-343">Varsayılan C# sürümlerinin listesi için [Varsayılanlar'a](../../csharp/language-reference/configure-language-version.md#defaults)bakın.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-343">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="5cb5d-344">Belirtilirse, proje oluşturma sırasında örtülü bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-344">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="5cb5d-345">.NET Core 2.2 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-345">Available since .NET Core 2.2 SDK.</span></span>

***

### <a name="classlib"></a><span data-ttu-id="5cb5d-346">classlib</span><span class="sxs-lookup"><span data-stu-id="5cb5d-346">classlib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="5cb5d-347">Hedef için [çerçeve](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-347">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="5cb5d-348">Değerler: `netcoreapp<version>` .NET Çekirdek Sınıf Kitaplığı oluşturmak veya `netstandard<version>` .NET Standart Sınıf Kitaplığı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-348">Values: `netcoreapp<version>` to create a .NET Core Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="5cb5d-349">Varsayılan değer: `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-349">The default value is `netstandard2.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="5cb5d-350">Oluşturulan `LangVersion` proje dosyasındaki özelliği ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-350">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="5cb5d-351">Örneğin, C# 7.3'u kullanmak için kullanın. `--langVersion 7.3`</span><span class="sxs-lookup"><span data-stu-id="5cb5d-351">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="5cb5d-352">F# için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-352">Not supported for F#.</span></span> <span data-ttu-id="5cb5d-353">.NET Core 2.2 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-353">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="5cb5d-354">Varsayılan C# sürümlerinin listesi için [Varsayılanlar'a](../../csharp/language-reference/configure-language-version.md#defaults)bakın.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-354">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="5cb5d-355">Proje oluşturma sırasında örtülü bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-355">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="wpf-wpflib-wpfcustomcontrollib-wpfusercontrollib"></a><a name="wpf"></a><span data-ttu-id="5cb5d-356">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="5cb5d-356">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="5cb5d-357">Hedef için [çerçeve](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-357">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="5cb5d-358">Varsayılan değer: `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-358">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="5cb5d-359">.NET Core 3.1 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-359">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="5cb5d-360">Oluşturulan `LangVersion` proje dosyasındaki özelliği ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-360">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="5cb5d-361">Örneğin, C# 7.3'u kullanmak için kullanın. `--langVersion 7.3`</span><span class="sxs-lookup"><span data-stu-id="5cb5d-361">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="5cb5d-362">Varsayılan C# sürümlerinin listesi için [Varsayılanlar'a](../../csharp/language-reference/configure-language-version.md#defaults)bakın.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-362">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="5cb5d-363">Proje oluşturma sırasında örtülü bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-363">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="winforms-winformslib"></a><a name="winforms"></a><span data-ttu-id="5cb5d-364">winforms, winformslib</span><span class="sxs-lookup"><span data-stu-id="5cb5d-364">winforms, winformslib</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="5cb5d-365">Oluşturulan `LangVersion` proje dosyasındaki özelliği ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-365">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="5cb5d-366">Örneğin, C# 7.3'u kullanmak için kullanın. `--langVersion 7.3`</span><span class="sxs-lookup"><span data-stu-id="5cb5d-366">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="5cb5d-367">Varsayılan C# sürümlerinin listesi için [Varsayılanlar'a](../../csharp/language-reference/configure-language-version.md#defaults)bakın.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-367">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="5cb5d-368">Proje oluşturma sırasında örtülü bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-368">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="worker-grpc"></a><a name="web-others"></a><span data-ttu-id="5cb5d-369">işçi, grpc</span><span class="sxs-lookup"><span data-stu-id="5cb5d-369">worker, grpc</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="5cb5d-370">Hedef için [çerçeve](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-370">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="5cb5d-371">Varsayılan değer: `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-371">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="5cb5d-372">.NET Core 3.1 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-372">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="5cb5d-373">oluşturulan şablondan *launchSettings.json* hariç tutar.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-373">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="5cb5d-374">Proje oluşturma sırasında örtülü bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-374">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="mstest-xunit"></a><a name="test"></a><span data-ttu-id="5cb5d-375">mstest, xunit</span><span class="sxs-lookup"><span data-stu-id="5cb5d-375">mstest, xunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="5cb5d-376">Hedef için [çerçeve](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-376">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="5cb5d-377">Seçenek .NET Core 3.0 SDK beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-377">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="5cb5d-378">Aşağıdaki tablo, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerleri listeler:</span><span class="sxs-lookup"><span data-stu-id="5cb5d-378">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="5cb5d-379">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="5cb5d-379">SDK version</span></span> | <span data-ttu-id="5cb5d-380">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="5cb5d-380">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="5cb5d-381">3.1</span><span class="sxs-lookup"><span data-stu-id="5cb5d-381">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="5cb5d-382">3,0</span><span class="sxs-lookup"><span data-stu-id="5cb5d-382">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="5cb5d-383">[Dotnet paketi](dotnet-pack.md)kullanarak proje için paketleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-383">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="5cb5d-384">Proje oluşturma sırasında örtülü bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-384">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="nunit"></a><span data-ttu-id="5cb5d-385">nunit</span><span class="sxs-lookup"><span data-stu-id="5cb5d-385">nunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="5cb5d-386">Hedef için [çerçeve](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-386">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="5cb5d-387">Aşağıdaki tablo, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerleri listeler:</span><span class="sxs-lookup"><span data-stu-id="5cb5d-387">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="5cb5d-388">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="5cb5d-388">SDK version</span></span> | <span data-ttu-id="5cb5d-389">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="5cb5d-389">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="5cb5d-390">3.1</span><span class="sxs-lookup"><span data-stu-id="5cb5d-390">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="5cb5d-391">3,0</span><span class="sxs-lookup"><span data-stu-id="5cb5d-391">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="5cb5d-392">2,2</span><span class="sxs-lookup"><span data-stu-id="5cb5d-392">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="5cb5d-393">2.1</span><span class="sxs-lookup"><span data-stu-id="5cb5d-393">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="5cb5d-394">[Dotnet paketi](dotnet-pack.md)kullanarak proje için paketleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-394">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="5cb5d-395">Proje oluşturma sırasında örtülü bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-395">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="page"></a><span data-ttu-id="5cb5d-396">Sayfası</span><span class="sxs-lookup"><span data-stu-id="5cb5d-396">page</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="5cb5d-397">Oluşturulan kod için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-397">Namespace for the generated code.</span></span> <span data-ttu-id="5cb5d-398">Varsayılan değer: `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-398">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="5cb5d-399">Sayfayı PageModel olmadan oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-399">Creates the page without a PageModel.</span></span>

***

### <a name="viewimports-proto"></a><a name="namespace"></a><span data-ttu-id="5cb5d-400">viewimports, proto</span><span class="sxs-lookup"><span data-stu-id="5cb5d-400">viewimports, proto</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="5cb5d-401">Oluşturulan kod için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-401">Namespace for the generated code.</span></span> <span data-ttu-id="5cb5d-402">Varsayılan değer: `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-402">The default value is `MyApp.Namespace`.</span></span>

***

### <a name="blazorserver"></a><span data-ttu-id="5cb5d-403">blazorserver</span><span class="sxs-lookup"><span data-stu-id="5cb5d-403">blazorserver</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="5cb5d-404">Kullanılacak kimlik doğrulama türü.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-404">The type of authentication to use.</span></span> <span data-ttu-id="5cb5d-405">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="5cb5d-405">The possible values are:</span></span>

  - <span data-ttu-id="5cb5d-406">`None`- Kimlik doğrulaması yok (Varsayılan).</span><span class="sxs-lookup"><span data-stu-id="5cb5d-406">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="5cb5d-407">`Individual`- Bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-407">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="5cb5d-408">`IndividualB2C`- Azure AD B2C ile bireysel kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-408">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="5cb5d-409">`SingleOrg`- Tek bir kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-409">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="5cb5d-410">`MultiOrg`- Birden çok kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-410">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="5cb5d-411">`Windows`- Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-411">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="5cb5d-412">Bağlanmak için Azure Active Directory B2C örneği.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-412">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="5cb5d-413">Kimlik `IndividualB2C` doğrulaması ile kullanın.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-413">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="5cb5d-414">Varsayılan değer: `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-414">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="5cb5d-415">Bu proje için oturum açma ve kaydolma ilkesi kimliği.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-415">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="5cb5d-416">Kimlik `IndividualB2C` doğrulaması ile kullanın.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-416">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="5cb5d-417">Bu proje için sıfırlama parola ilkesi kimliği.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-417">The reset password policy ID for this project.</span></span> <span data-ttu-id="5cb5d-418">Kimlik `IndividualB2C` doğrulaması ile kullanın.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-418">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="5cb5d-419">Bu projenin profil ilke kimliğini edin.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-419">The edit profile policy ID for this project.</span></span> <span data-ttu-id="5cb5d-420">Kimlik `IndividualB2C` doğrulaması ile kullanın.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-420">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="5cb5d-421">Bağlanmak için Azure Etkin Dizin örneği.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-421">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="5cb5d-422">Kimlik `SingleOrg` doğrulaması ile kullanın. `MultiOrg`</span><span class="sxs-lookup"><span data-stu-id="5cb5d-422">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="5cb5d-423">Varsayılan değer: `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-423">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="5cb5d-424">Bu projenin Istemci Kimliği.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-424">The Client ID for this project.</span></span> <span data-ttu-id="5cb5d-425">"Kimlik `IndividualB2C` `SingleOrg`doğrulama" `MultiOrg` ile kullanın.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-425">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="5cb5d-426">Varsayılan değer: `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-426">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="5cb5d-427">Dizin kiracı için etki alanı.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-427">The domain for the directory tenant.</span></span> <span data-ttu-id="5cb5d-428">Kimlik `SingleOrg` doğrulaması ile kullanın. `IndividualB2C`</span><span class="sxs-lookup"><span data-stu-id="5cb5d-428">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="5cb5d-429">Varsayılan değer: `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-429">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="5cb5d-430">Bağlanacak dizinin Kiracı Kimliği.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-430">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="5cb5d-431">Kimlik `SingleOrg` doğrulaması ile kullanın.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-431">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="5cb5d-432">Varsayılan değer: `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-432">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="5cb5d-433">Yeniden yönlendirme URI uygulamanın temel yolu içinde istek yolu.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-433">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="5cb5d-434">Kimlik `SingleOrg` doğrulaması ile kullanın. `IndividualB2C`</span><span class="sxs-lookup"><span data-stu-id="5cb5d-434">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="5cb5d-435">Varsayılan değer: `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-435">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="5cb5d-436">Bu uygulamanın dizine okuma erişimine izin verir.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-436">Allows this application read-access to the directory.</span></span> <span data-ttu-id="5cb5d-437">Yalnızca kimlik `SingleOrg` doğrulama `MultiOrg` veya kimlik doğrulama için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-437">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="5cb5d-438">oluşturulan şablondan *launchSettings.json* hariç tutar.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-438">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="5cb5d-439">HTTPS'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-439">Turns off HTTPS.</span></span> <span data-ttu-id="5cb5d-440">Bu seçenek yalnızca `Individual`, `IndividualB2C` `SingleOrg`, `MultiOrg` , , `--auth`için kullanılıyorsa veya kullanılmazsa geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-440">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="5cb5d-441">SQLite yerine LocalDB'nin kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-441">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="5cb5d-442">Yalnızca kimlik `Individual` doğrulama `IndividualB2C` veya kimlik doğrulama için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-442">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="5cb5d-443">Proje oluşturma sırasında örtülü bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-443">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web"></a><span data-ttu-id="5cb5d-444">web</span><span class="sxs-lookup"><span data-stu-id="5cb5d-444">web</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="5cb5d-445">oluşturulan şablondan *launchSettings.json* hariç tutar.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-445">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="5cb5d-446">Hedef için [çerçeve](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-446">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="5cb5d-447">Seçenek .NET Core 2.2 SDK'da kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-447">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="5cb5d-448">Aşağıdaki tablo, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerleri listeler:</span><span class="sxs-lookup"><span data-stu-id="5cb5d-448">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="5cb5d-449">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="5cb5d-449">SDK version</span></span> | <span data-ttu-id="5cb5d-450">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="5cb5d-450">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="5cb5d-451">3.1</span><span class="sxs-lookup"><span data-stu-id="5cb5d-451">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="5cb5d-452">3,0</span><span class="sxs-lookup"><span data-stu-id="5cb5d-452">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="5cb5d-453">2.1</span><span class="sxs-lookup"><span data-stu-id="5cb5d-453">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="5cb5d-454">Proje oluşturma sırasında örtülü bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-454">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="5cb5d-455">HTTPS'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-455">Turns off HTTPS.</span></span>

***

### <a name="mvc-webapp"></a><a name="web-options"></a><span data-ttu-id="5cb5d-456">mvc, webapp</span><span class="sxs-lookup"><span data-stu-id="5cb5d-456">mvc, webapp</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="5cb5d-457">Kullanılacak kimlik doğrulama türü.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-457">The type of authentication to use.</span></span> <span data-ttu-id="5cb5d-458">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="5cb5d-458">The possible values are:</span></span>

  - <span data-ttu-id="5cb5d-459">`None`- Kimlik doğrulaması yok (Varsayılan).</span><span class="sxs-lookup"><span data-stu-id="5cb5d-459">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="5cb5d-460">`Individual`- Bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-460">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="5cb5d-461">`IndividualB2C`- Azure AD B2C ile bireysel kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-461">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="5cb5d-462">`SingleOrg`- Tek bir kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-462">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="5cb5d-463">`MultiOrg`- Birden çok kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-463">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="5cb5d-464">`Windows`- Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-464">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="5cb5d-465">Bağlanmak için Azure Active Directory B2C örneği.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-465">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="5cb5d-466">Kimlik `IndividualB2C` doğrulaması ile kullanın.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-466">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="5cb5d-467">Varsayılan değer: `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-467">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="5cb5d-468">Bu proje için oturum açma ve kaydolma ilkesi kimliği.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-468">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="5cb5d-469">Kimlik `IndividualB2C` doğrulaması ile kullanın.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-469">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="5cb5d-470">Bu proje için sıfırlama parola ilkesi kimliği.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-470">The reset password policy ID for this project.</span></span> <span data-ttu-id="5cb5d-471">Kimlik `IndividualB2C` doğrulaması ile kullanın.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-471">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="5cb5d-472">Bu projenin profil ilke kimliğini edin.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-472">The edit profile policy ID for this project.</span></span> <span data-ttu-id="5cb5d-473">Kimlik `IndividualB2C` doğrulaması ile kullanın.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-473">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="5cb5d-474">Bağlanmak için Azure Etkin Dizin örneği.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-474">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="5cb5d-475">Kimlik `SingleOrg` doğrulaması ile kullanın. `MultiOrg`</span><span class="sxs-lookup"><span data-stu-id="5cb5d-475">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="5cb5d-476">Varsayılan değer: `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-476">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="5cb5d-477">Bu projenin Istemci Kimliği.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-477">The Client ID for this project.</span></span> <span data-ttu-id="5cb5d-478">"Kimlik `IndividualB2C` `SingleOrg`doğrulama" `MultiOrg` ile kullanın.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-478">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="5cb5d-479">Varsayılan değer: `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-479">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="5cb5d-480">Dizin kiracı için etki alanı.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-480">The domain for the directory tenant.</span></span> <span data-ttu-id="5cb5d-481">Kimlik `SingleOrg` doğrulaması ile kullanın. `IndividualB2C`</span><span class="sxs-lookup"><span data-stu-id="5cb5d-481">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="5cb5d-482">Varsayılan değer: `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-482">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="5cb5d-483">Bağlanacak dizinin Kiracı Kimliği.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-483">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="5cb5d-484">Kimlik `SingleOrg` doğrulaması ile kullanın.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-484">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="5cb5d-485">Varsayılan değer: `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-485">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="5cb5d-486">Yeniden yönlendirme URI uygulamanın temel yolu içinde istek yolu.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-486">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="5cb5d-487">Kimlik `SingleOrg` doğrulaması ile kullanın. `IndividualB2C`</span><span class="sxs-lookup"><span data-stu-id="5cb5d-487">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="5cb5d-488">Varsayılan değer: `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-488">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="5cb5d-489">Bu uygulamanın dizine okuma erişimine izin verir.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-489">Allows this application read-access to the directory.</span></span> <span data-ttu-id="5cb5d-490">Yalnızca kimlik `SingleOrg` doğrulama `MultiOrg` veya kimlik doğrulama için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-490">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="5cb5d-491">oluşturulan şablondan *launchSettings.json* hariç tutar.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-491">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="5cb5d-492">HTTPS'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-492">Turns off HTTPS.</span></span> <span data-ttu-id="5cb5d-493">Bu seçenek yalnızca `Individual`, `IndividualB2C` `SingleOrg`, `MultiOrg` , , , veya kullanılmazsa geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-493">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="5cb5d-494">SQLite yerine LocalDB'nin kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-494">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="5cb5d-495">Yalnızca kimlik `Individual` doğrulama `IndividualB2C` veya kimlik doğrulama için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-495">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="5cb5d-496">Hedef için [çerçeve](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-496">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="5cb5d-497">Seçenek .NET Core 3.0 SDK beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-497">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="5cb5d-498">Aşağıdaki tablo, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerleri listeler:</span><span class="sxs-lookup"><span data-stu-id="5cb5d-498">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="5cb5d-499">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="5cb5d-499">SDK version</span></span> | <span data-ttu-id="5cb5d-500">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="5cb5d-500">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="5cb5d-501">3.1</span><span class="sxs-lookup"><span data-stu-id="5cb5d-501">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="5cb5d-502">3,0</span><span class="sxs-lookup"><span data-stu-id="5cb5d-502">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="5cb5d-503">Proje oluşturma sırasında örtülü bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-503">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="5cb5d-504">Projeye BrowserLink'i içerir.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-504">Includes BrowserLink in the project.</span></span> <span data-ttu-id="5cb5d-505">Seçenek .NET Core 2.2 ve 3.1 SDK'da kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-505">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

- **`-rrc|--razor-runtime-compilation`**

  <span data-ttu-id="5cb5d-506">Hata Ayıklama yapılarında [ustura çalışma zamanı derlemesi](/aspnet/core/mvc/views/view-compilation#runtime-compilation) kullanacak şekilde yapılandırıp yapılandırılmamasını belirler.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-506">Determines if the project is configured to use [Razor runtime compilation](/aspnet/core/mvc/views/view-compilation#runtime-compilation) in Debug builds.</span></span> <span data-ttu-id="5cb5d-507">Seçenek .NET Core 3.1 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-507">Option available since .NET Core 3.1 SDK.</span></span>

***

### <a name="angular-react"></a><a name="spa"></a><span data-ttu-id="5cb5d-508">açısal, tepki</span><span class="sxs-lookup"><span data-stu-id="5cb5d-508">angular, react</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="5cb5d-509">Kullanılacak kimlik doğrulama türü.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-509">The type of authentication to use.</span></span> <span data-ttu-id="5cb5d-510">.NET Core 3.0 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-510">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="5cb5d-511">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="5cb5d-511">The possible values are:</span></span>

  - <span data-ttu-id="5cb5d-512">`None`- Kimlik doğrulaması yok (Varsayılan).</span><span class="sxs-lookup"><span data-stu-id="5cb5d-512">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="5cb5d-513">`Individual`- Bireysel kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-513">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="5cb5d-514">oluşturulan şablondan *launchSettings.json* hariç tutar.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-514">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="5cb5d-515">Proje oluşturma sırasında örtülü bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-515">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="5cb5d-516">HTTPS'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-516">Turns off HTTPS.</span></span> <span data-ttu-id="5cb5d-517">Bu seçenek yalnızca kimlik `None`doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-517">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="5cb5d-518">SQLite yerine LocalDB'nin kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-518">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="5cb5d-519">Yalnızca kimlik `Individual` doğrulama `IndividualB2C` veya kimlik doğrulama için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-519">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="5cb5d-520">.NET Core 3.0 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-520">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="5cb5d-521">Hedef için [çerçeve](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-521">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="5cb5d-522">Seçenek .NET Core 2.2 SDK'da kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-522">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="5cb5d-523">Aşağıdaki tablo, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerleri listeler:</span><span class="sxs-lookup"><span data-stu-id="5cb5d-523">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="5cb5d-524">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="5cb5d-524">SDK version</span></span> | <span data-ttu-id="5cb5d-525">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="5cb5d-525">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="5cb5d-526">3.1</span><span class="sxs-lookup"><span data-stu-id="5cb5d-526">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="5cb5d-527">3,0</span><span class="sxs-lookup"><span data-stu-id="5cb5d-527">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="5cb5d-528">2.1</span><span class="sxs-lookup"><span data-stu-id="5cb5d-528">2.1</span></span>         | `netcoreapp2.0` |

***

### <a name="reactredux"></a><span data-ttu-id="5cb5d-529">reactredux</span><span class="sxs-lookup"><span data-stu-id="5cb5d-529">reactredux</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="5cb5d-530">oluşturulan şablondan *launchSettings.json* hariç tutar.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-530">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="5cb5d-531">Hedef için [çerçeve](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-531">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="5cb5d-532">Seçenek .NET Core 2.2 SDK'da kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-532">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="5cb5d-533">Aşağıdaki tablo, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerleri listeler:</span><span class="sxs-lookup"><span data-stu-id="5cb5d-533">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="5cb5d-534">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="5cb5d-534">SDK version</span></span> | <span data-ttu-id="5cb5d-535">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="5cb5d-535">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="5cb5d-536">3.1</span><span class="sxs-lookup"><span data-stu-id="5cb5d-536">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="5cb5d-537">3,0</span><span class="sxs-lookup"><span data-stu-id="5cb5d-537">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="5cb5d-538">2.1</span><span class="sxs-lookup"><span data-stu-id="5cb5d-538">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="5cb5d-539">Proje oluşturma sırasında örtülü bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-539">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="5cb5d-540">HTTPS'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-540">Turns off HTTPS.</span></span>

***

### <a name="razorclasslib"></a><span data-ttu-id="5cb5d-541">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="5cb5d-541">razorclasslib</span></span>

- **`--no-restore`**

  <span data-ttu-id="5cb5d-542">Proje oluşturma sırasında örtülü bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-542">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="5cb5d-543">Bu kitaplığa bileşenlere ek olarak geleneksel Razor sayfaları ve Görünümler eklemeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-543">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="5cb5d-544">.NET Core 3.0 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-544">Available since .NET Core 3.0 SDK.</span></span>

***
  
### <a name="webapi"></a><span data-ttu-id="5cb5d-545">webapi</span><span class="sxs-lookup"><span data-stu-id="5cb5d-545">webapi</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="5cb5d-546">Kullanılacak kimlik doğrulama türü.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-546">The type of authentication to use.</span></span> <span data-ttu-id="5cb5d-547">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="5cb5d-547">The possible values are:</span></span>

  - <span data-ttu-id="5cb5d-548">`None`- Kimlik doğrulaması yok (Varsayılan).</span><span class="sxs-lookup"><span data-stu-id="5cb5d-548">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="5cb5d-549">`IndividualB2C`- Azure AD B2C ile bireysel kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-549">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="5cb5d-550">`SingleOrg`- Tek bir kiracı için kuruluş kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-550">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="5cb5d-551">`Windows`- Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-551">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="5cb5d-552">Bağlanmak için Azure Active Directory B2C örneği.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-552">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="5cb5d-553">Kimlik `IndividualB2C` doğrulaması ile kullanın.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-553">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="5cb5d-554">Varsayılan değer: `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-554">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="5cb5d-555">Bu proje için oturum açma ve kaydolma ilkesi kimliği.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-555">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="5cb5d-556">Kimlik `IndividualB2C` doğrulaması ile kullanın.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-556">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="5cb5d-557">Bağlanmak için Azure Etkin Dizin örneği.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-557">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="5cb5d-558">Kimlik `SingleOrg` doğrulaması ile kullanın.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-558">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="5cb5d-559">Varsayılan değer: `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-559">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="5cb5d-560">Bu projenin Istemci Kimliği.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-560">The Client ID for this project.</span></span> <span data-ttu-id="5cb5d-561">Kimlik `IndividualB2C` doğrulaması ile kullanın. `SingleOrg`</span><span class="sxs-lookup"><span data-stu-id="5cb5d-561">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="5cb5d-562">Varsayılan değer: `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-562">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="5cb5d-563">Dizin kiracı için etki alanı.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-563">The domain for the directory tenant.</span></span> <span data-ttu-id="5cb5d-564">Kimlik `IndividualB2C` doğrulaması ile kullanın. `SingleOrg`</span><span class="sxs-lookup"><span data-stu-id="5cb5d-564">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="5cb5d-565">Varsayılan değer: `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-565">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="5cb5d-566">Bağlanacak dizinin Kiracı Kimliği.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-566">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="5cb5d-567">Kimlik `SingleOrg` doğrulaması ile kullanın.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-567">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="5cb5d-568">Varsayılan değer: `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-568">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="5cb5d-569">Bu uygulamanın dizine okuma erişimine izin verir.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-569">Allows this application read-access to the directory.</span></span> <span data-ttu-id="5cb5d-570">Yalnızca kimlik `SingleOrg` doğrulama için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-570">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="5cb5d-571">oluşturulan şablondan *launchSettings.json* hariç tutar.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-571">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="5cb5d-572">HTTPS'yi kapatır.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-572">Turns off HTTPS.</span></span> <span data-ttu-id="5cb5d-573">`app.UseHsts`ve `app.UseHttpsRedirection` `Startup.Configure`eklenmez.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-573">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="5cb5d-574">Bu seçenek yalnızca `IndividualB2C` kimlik `SingleOrg` doğrulaması için kullanılıyorsa veya kullanılmamışsa geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-574">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="5cb5d-575">SQLite yerine LocalDB'nin kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-575">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="5cb5d-576">Yalnızca kimlik `IndividualB2C` doğrulama için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-576">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="5cb5d-577">Hedef için [çerçeve](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-577">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="5cb5d-578">Seçenek .NET Core 2.2 SDK'da kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-578">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="5cb5d-579">Aşağıdaki tablo, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerleri listeler:</span><span class="sxs-lookup"><span data-stu-id="5cb5d-579">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="5cb5d-580">SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="5cb5d-580">SDK version</span></span> | <span data-ttu-id="5cb5d-581">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="5cb5d-581">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="5cb5d-582">3.1</span><span class="sxs-lookup"><span data-stu-id="5cb5d-582">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="5cb5d-583">3,0</span><span class="sxs-lookup"><span data-stu-id="5cb5d-583">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="5cb5d-584">2.1</span><span class="sxs-lookup"><span data-stu-id="5cb5d-584">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="5cb5d-585">Proje oluşturma sırasında örtülü bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-585">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="globaljson"></a><span data-ttu-id="5cb5d-586">globaljson</span><span class="sxs-lookup"><span data-stu-id="5cb5d-586">globaljson</span></span>

- **`--sdk-version <VERSION_NUMBER>`**

  <span data-ttu-id="5cb5d-587">.NET Core SDK sürümünü *global.json* dosyasında kullanmak üzere belirtir.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-587">Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="5cb5d-588">Örnekler</span><span class="sxs-lookup"><span data-stu-id="5cb5d-588">Examples</span></span>

- <span data-ttu-id="5cb5d-589">Şablon adını belirterek c# konsolu uygulama projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="5cb5d-589">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="5cb5d-590">Geçerli dizinde bir F# konsolu uygulama projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="5cb5d-590">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang F#
  ```

- <span data-ttu-id="5cb5d-591">Belirtilen dizinde bir .NET Standart sınıf kitaplığı projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="5cb5d-591">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="5cb5d-592">Geçerli dizinde kimlik doğrulaması olmadan yeni bir ASP.NET Core C# MVC projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="5cb5d-592">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="5cb5d-593">Yeni bir xUnit projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="5cb5d-593">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="5cb5d-594">Tek Sayfa Uygulaması (SPA) şablonları için kullanılabilen tüm şablonları listeleyin:</span><span class="sxs-lookup"><span data-stu-id="5cb5d-594">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="5cb5d-595">*Biz* alt dize ile eşleşen tüm şablonları listeleyin.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-595">List all templates matching the *we* substring.</span></span> <span data-ttu-id="5cb5d-596">Tam eşleşme bulunamadı, bu nedenle alt dize eşleştirme hem kısa ad hem de ad sütunlarına karşı çalışır.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-596">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="5cb5d-597">Ng eşleşen şablonu çağırmak için girişimi *.*</span><span class="sxs-lookup"><span data-stu-id="5cb5d-597">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="5cb5d-598">Tek bir eşleşme belirlenemezse, kısmi eşleşmeolan şablonları listeleyin.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-598">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="5cb5d-599">ASP.NET Core için SPA şablonlarının 2.0 sürümünü yükleyin:</span><span class="sxs-lookup"><span data-stu-id="5cb5d-599">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="5cb5d-600">Yüklenen şablonları ve bunlarla ilgili ayrıntıları ve bunları nasıl kaldırılabildiğini listeleyin:</span><span class="sxs-lookup"><span data-stu-id="5cb5d-600">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="5cb5d-601">Geçerli dizinde SDK sürümünü 3.1.101 olarak ayarlayarak *global.json* oluşturun:</span><span class="sxs-lookup"><span data-stu-id="5cb5d-601">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="5cb5d-602">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5cb5d-602">See also</span></span>

- [<span data-ttu-id="5cb5d-603">Dotnet yeni için özel şablonlar</span><span class="sxs-lookup"><span data-stu-id="5cb5d-603">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="5cb5d-604">Dotnet new için özel şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="5cb5d-604">Create a custom template for dotnet new</span></span>](../tutorials/cli-templates-create-item-template.md)
- [<span data-ttu-id="5cb5d-605">dotnet/dotnet-şablon-örnekleri GitHub repo</span><span class="sxs-lookup"><span data-stu-id="5cb5d-605">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="5cb5d-606">dotnet yeni için kullanılabilir şablonlar</span><span class="sxs-lookup"><span data-stu-id="5cb5d-606">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
