---
title: NuGet ve .NET kitaplıkları
description: En iyi yöntem önerileri paketleme için NuGet ile .NET kitaplıkları.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 845af3b34827e1f284bb52e040f9de09f22baf37
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/11/2018
ms.locfileid: "49087871"
---
# <a name="nuget"></a><span data-ttu-id="19788-103">NuGet</span><span class="sxs-lookup"><span data-stu-id="19788-103">NuGet</span></span>

<span data-ttu-id="19788-104">NuGet, .NET ekonomik sistem için bir paket yöneticisidir ve birincil yolu geliştiriciler keşfedin ve .NET açık kaynak kitaplıkları Al.</span><span class="sxs-lookup"><span data-stu-id="19788-104">NuGet is a package manager for the .NET eco-system and is the primary way developers discover and acquire .NET open-source libraries.</span></span> <span data-ttu-id="19788-105">Birincil ana bilgisayar için genel NuGet paketleri NuGet.org, NuGet paketlerini barındırmak için Microsoft tarafından sağlanan ücretsiz bir hizmet olan ancak MyGet ve Azure DevOps gibi özel NuGet hizmetlerine yayımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="19788-105">NuGet.org, a free service provided by Microsoft for hosting NuGet packages, is the primary host for public NuGet packages but you can publish to custom NuGet services like MyGet and Azure DevOps.</span></span>

<span data-ttu-id="19788-106">![NuGet](./media/nuget/nuget-logo.png "NuGet")</span><span class="sxs-lookup"><span data-stu-id="19788-106">![NuGet](./media/nuget/nuget-logo.png "NuGet")</span></span>

## <a name="create-a-nuget-package"></a><span data-ttu-id="19788-107">Bir NuGet paketi oluşturma</span><span class="sxs-lookup"><span data-stu-id="19788-107">Create a NuGet package</span></span>

<span data-ttu-id="19788-108">Bir NuGet paketi (`*.nupkg`) .NET derlemelerini ve ilişkili meta verileri içeren bir zip dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="19788-108">A NuGet package (`*.nupkg`) is a zip file that contains .NET assemblies and associated metadata.</span></span>

<span data-ttu-id="19788-109">Bir NuGet paketi oluşturmak için iki ana yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="19788-109">There are two main ways to create a NuGet package.</span></span> <span data-ttu-id="19788-110">Yeni ve önerilen bir SDK stilinde projeden bir paketi oluşturmak için yoludur (proje dosyasının içeriği ile başlayan `<Project Sdk="Microsoft.NET.Sdk">`).</span><span class="sxs-lookup"><span data-stu-id="19788-110">The newer and recommended way is to create a package from a SDK-style project (project file the content starts with `<Project Sdk="Microsoft.NET.Sdk">`).</span></span> <span data-ttu-id="19788-111">Derlemeler ve hedefleri paketi otomatik olarak eklenir ve meta verileri kalan paket adı ve sürüm numarası gibi MSBuild dosyasına eklenir.</span><span class="sxs-lookup"><span data-stu-id="19788-111">Assemblies and targets are automatically added to the package and remaining metadata is added to the MSBuild file, like package name and version number.</span></span> <span data-ttu-id="19788-112">İle derlerken [ `dotnet pack` ](../../core/tools/dotnet-pack.md) çıktılar komut bir `*.nupkg` derlemeler yerine dosya.</span><span class="sxs-lookup"><span data-stu-id="19788-112">Compiling with the [`dotnet pack`](../../core/tools/dotnet-pack.md) command outputs a `*.nupkg` file instead of assemblies.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
    <AssemblyName>Contoso.Api</AssemblyName>
    <PackageVersion>1.1.0</PackageVersion>
    <Authors>John Doe</Authors>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="19788-113">Bir NuGet paketi oluşturma eski yöntem, bir `*.nuspec` dosya ve `nuget.exe` komut satırı aracı.</span><span class="sxs-lookup"><span data-stu-id="19788-113">The older way of creating a NuGet package is with a `*.nuspec` file and the `nuget.exe` command-line tool.</span></span> <span data-ttu-id="19788-114">Soubor nuspec çok denetimi verir ancak hangi derlemelerin ve hedefleri son NuGet paket içerisine dâhil etmek dikkatli bir şekilde belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="19788-114">A nuspec file gives you great control but you must carefully specify what assemblies and targets to include in the final NuGet package.</span></span> <span data-ttu-id="19788-115">Bir hata yapmak kolaydır veya birinin değişiklikler yaparken nuspec güncelleştirilecek unutmayın.</span><span class="sxs-lookup"><span data-stu-id="19788-115">It's easy to make a mistake or for someone to forget to update the nuspec when making changes.</span></span> <span data-ttu-id="19788-116">Kullanabilirsiniz bir nuspec avantajlarındandır henüz bir SDK stilinde proje dosyası desteklemeyen çerçeveler için NuGet paketleri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="19788-116">The advantage of a nuspec is you can use it create NuGet packages for frameworks that don't yet support an SDK-style project file.</span></span>

<span data-ttu-id="19788-117">**✔️ DÜŞÜNÜN** NuGet paketi oluşturmak için bir SDK stilinde proje dosyasını kullanarak.</span><span class="sxs-lookup"><span data-stu-id="19788-117">**✔️ CONSIDER** using an SDK-style project file to create the NuGet package.</span></span>

<span data-ttu-id="19788-118">**✔️ DÜŞÜNÜN** NuGet paketi ve derlemeler için kaynak denetimi meta verilerini eklemek için SourceLink ayarlama.</span><span class="sxs-lookup"><span data-stu-id="19788-118">**✔️ CONSIDER** setting up SourceLink to add source control metadata to your assemblies and NuGet package.</span></span>

## <a name="package-dependencies"></a><span data-ttu-id="19788-119">Paket bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="19788-119">Package dependencies</span></span>

<span data-ttu-id="19788-120">NuGet Paket bağımlılıklarını ayrıntılı olarak ele alınmıştır [bağımlılıkları](./dependencies.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="19788-120">NuGet package dependencies are covered in detail in the [Dependencies](./dependencies.md) article.</span></span>

## <a name="important-nuget-package-metadata"></a><span data-ttu-id="19788-121">Önemli NuGet paketi meta verileri</span><span class="sxs-lookup"><span data-stu-id="19788-121">Important NuGet package metadata</span></span>

<span data-ttu-id="19788-122">Bir NuGet paketi birçok destekler [meta veri özelliklerini](/nuget/reference/nuspec).</span><span class="sxs-lookup"><span data-stu-id="19788-122">A NuGet package supports many [metadata properties](/nuget/reference/nuspec).</span></span> <span data-ttu-id="19788-123">Aşağıdaki tabloda her bir açık kaynak proje sağlamalıdır çekirdek meta veriler içerir:</span><span class="sxs-lookup"><span data-stu-id="19788-123">The following table contains the core metadata that every open-source project should provide:</span></span>

| <span data-ttu-id="19788-124">MSBuild özellik adı</span><span class="sxs-lookup"><span data-stu-id="19788-124">MSBuild Property name</span></span>              | <span data-ttu-id="19788-125">Nuspec adı</span><span class="sxs-lookup"><span data-stu-id="19788-125">Nuspec name</span></span>              | <span data-ttu-id="19788-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="19788-126">Description</span></span>  |
| ---------------------------------- | ------------------------ | ------------ |
| `PackageId`                        | `id`                       | <span data-ttu-id="19788-127">Paket tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="19788-127">The package identifier.</span></span> <span data-ttu-id="19788-128">Bunu karşılıyorsa tanımlayıcı önekten ayrılabileceğini [ölçütleri](/nuget/reference/id-prefix-reservation).</span><span class="sxs-lookup"><span data-stu-id="19788-128">A prefix from the identifier can be reserved if it meets the [criteria](/nuget/reference/id-prefix-reservation).</span></span> |
| `PackageVersion`                   | `version`                  | <span data-ttu-id="19788-129">NuGet Paket sürümü.</span><span class="sxs-lookup"><span data-stu-id="19788-129">NuGet package version.</span></span> <span data-ttu-id="19788-130">Daha fazla bilgi için [NuGet paketi sürüm](./versioning.md#nuget-package-version).</span><span class="sxs-lookup"><span data-stu-id="19788-130">For more information, see [NuGet package version](./versioning.md#nuget-package-version).</span></span>             |
| `Title`                            | `title`                    | <span data-ttu-id="19788-131">Paket bir insan dostu başlığı.</span><span class="sxs-lookup"><span data-stu-id="19788-131">A human-friendly title of the package.</span></span> <span data-ttu-id="19788-132">Varsayılan `PackageId`.</span><span class="sxs-lookup"><span data-stu-id="19788-132">It defaults to the `PackageId`.</span></span>             |
| `Description`                      | `description`              | <span data-ttu-id="19788-133">Kullanıcı Arabiriminde görüntülenen paketinin uzun açıklaması.</span><span class="sxs-lookup"><span data-stu-id="19788-133">A long description of the package displayed in UI.</span></span>             |
| `Authors`                          | `authors`                  | <span data-ttu-id="19788-134">Nuget.org profil adları eşleşen, paket yazarlarının virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="19788-134">A comma-separated list of package authors, matching the profile names on nuget.org.</span></span>             |
| `PackageTags`                      | `tags`                     | <span data-ttu-id="19788-135">Etiketleri ve paket tanımlayan anahtar sözcükleri boşlukla ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="19788-135">A space-delimited list of tags and keywords that describe the package.</span></span> <span data-ttu-id="19788-136">Etiketleri paketler için arama yaparken de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="19788-136">Tags are used when searching for packages.</span></span>             |
| `PackageIconUrl`                   | `iconUrl`                  | <span data-ttu-id="19788-137">Paket için simge olarak kullanılacak bir URL için bir görüntü.</span><span class="sxs-lookup"><span data-stu-id="19788-137">A URL for an image to use as the icon for the package.</span></span> <span data-ttu-id="19788-138">HTTPS URL'si olmalıdır ve görüntü 64 x 64 olmalıdır ve saydam bir arka plana sahip.</span><span class="sxs-lookup"><span data-stu-id="19788-138">URL should be HTTPS and the image should be 64x64 and have a transparent background.</span></span>             |
| `PackageProjectUrl`                | `projectUrl`               | <span data-ttu-id="19788-139">Proje giriş sayfası veya kaynak havuzu için bir URL.</span><span class="sxs-lookup"><span data-stu-id="19788-139">A URL for the project homepage or source repository.</span></span>             |
| `PackageLicenseUrl`                | `licenseUrl`               | <span data-ttu-id="19788-140">Proje lisans URL'si.</span><span class="sxs-lookup"><span data-stu-id="19788-140">A URL to the project license.</span></span> <span data-ttu-id="19788-141">URL için `LICENSE` dosyası kaynak denetiminde.</span><span class="sxs-lookup"><span data-stu-id="19788-141">Can be the URL to the `LICENSE` file in source control.</span></span>             |

<span data-ttu-id="19788-142">**✔️ DÜŞÜNÜN** NuGet'ın ön eki ayırma karşılayan bir önek ile NuGet paket adı seçerek [ölçütleri](/nuget/reference/id-prefix-reservation).</span><span class="sxs-lookup"><span data-stu-id="19788-142">**✔️ CONSIDER** choosing a NuGet package name with a prefix that meets NuGet's prefix reservation [criteria](/nuget/reference/id-prefix-reservation).</span></span>

<span data-ttu-id="19788-143">**✔️ DÜŞÜNÜN** kullanarak `LICENSE` dosya kaynak denetimine eklememelisiniz `LicenseUrl`.</span><span class="sxs-lookup"><span data-stu-id="19788-143">**✔️ CONSIDER** using the `LICENSE` file in source control as the `LicenseUrl`.</span></span> <span data-ttu-id="19788-144">Örneğin, https://github.com/JamesNK/Newtonsoft.Json/blob/master/LICENSE.md</span><span class="sxs-lookup"><span data-stu-id="19788-144">For example, https://github.com/JamesNK/Newtonsoft.Json/blob/master/LICENSE.md</span></span>

> [!IMPORTANT]
> <span data-ttu-id="19788-145">Bir proje için varsayılan olarak bir lisans olmadan [özel telif hakkı](https://choosealicense.com/no-permission/), diğer kişilerin kullanmasına imkansızdır.</span><span class="sxs-lookup"><span data-stu-id="19788-145">A project without a license defaults to [exclusive copyright](https://choosealicense.com/no-permission/), making it impossible for other people to use.</span></span>

<span data-ttu-id="19788-146">**✔️ YAPMAK** paket simge için bir HTTPS href kullanın.</span><span class="sxs-lookup"><span data-stu-id="19788-146">**✔️ DO** use an HTTPS href to your package icon.</span></span>

> <span data-ttu-id="19788-147">İle HTTPS etkin site NuGet.org gibi çalıştırın ve HTTPS olmayan bir resim görüntüleyen bir karışık içerik uyarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="19788-147">Sites like NuGet.org run with HTTPS enabled and displaying a non-HTTPS image will create a mixed content warning.</span></span>

<span data-ttu-id="19788-148">**✔️ YAPMAK** 64 x 64 ve en iyi sonuçları görüntülemek için saydam bir arka plana sahip bir paket simge görüntüsü kullanın.</span><span class="sxs-lookup"><span data-stu-id="19788-148">**✔️ DO** use a package icon image that is 64x64 and has a transparent background for best viewing results.</span></span>

## <a name="pre-release-packages"></a><span data-ttu-id="19788-149">Yayın öncesi paketleri</span><span class="sxs-lookup"><span data-stu-id="19788-149">Pre-release packages</span></span>

<span data-ttu-id="19788-150">NuGet paketlerini sürüm sonekine sahip olarak kabul edilir [yayın öncesi](/nuget/create-packages/prerelease-packages).</span><span class="sxs-lookup"><span data-stu-id="19788-150">NuGet packages with a version suffix are considered [pre-release](/nuget/create-packages/prerelease-packages).</span></span> <span data-ttu-id="19788-151">Bir kullanıcı kabul eder yayın öncesi paketleri, yayın öncesi paketleri sınırlı kullanıcı test için ideal hale açma sürece varsayılan olarak, NuGet Paket Yöneticisi UI kararlı yayınları gösterir.</span><span class="sxs-lookup"><span data-stu-id="19788-151">By default, the NuGet Package Manager UI shows stable releases unless a user opts-in to pre-release packages, making pre-release packages ideal for limited user testing.</span></span>

```xml
<PackageVersion>1.0.1-beta1</PackageVersion>
```

> [!NOTE]
> <span data-ttu-id="19788-152">Bir kararlı paket bir yayın öncesi pakete bağımlı olamaz.</span><span class="sxs-lookup"><span data-stu-id="19788-152">A stable package cannot depend on a pre-release package.</span></span> <span data-ttu-id="19788-153">Yayın öncesi kendi paket yapmak veya eski bir kararlı sürüme bağlı.</span><span class="sxs-lookup"><span data-stu-id="19788-153">You must either make your own package pre-release or depend on an older stable version.</span></span>

<span data-ttu-id="19788-154">![NuGet yayın öncesi paket bağımlılığı](./media/nuget/nuget-prerelease-package.png "NuGet yayın öncesi paket bağımlılığı")</span><span class="sxs-lookup"><span data-stu-id="19788-154">![NuGet pre-release package dependency](./media/nuget/nuget-prerelease-package.png "NuGet pre-release package dependency")</span></span>

<span data-ttu-id="19788-155">**✔️ YAPMAK** test etme, Önizleme veya deneme yayın öncesi paket yayımlama.</span><span class="sxs-lookup"><span data-stu-id="19788-155">**✔️ DO** publish a pre-release package when testing, previewing, or experimenting.</span></span>

<span data-ttu-id="19788-156">**✔️ YAPMAK** , hazır, bu nedenle diğer kararlı paketleri başvuruda bulunduğunuzda bir kararlı paket yayımlama.</span><span class="sxs-lookup"><span data-stu-id="19788-156">**✔️ DO** publish a stable package when its ready so other stable packages can reference it.</span></span>

## <a name="symbol-packages"></a><span data-ttu-id="19788-157">Sembol paketleri</span><span class="sxs-lookup"><span data-stu-id="19788-157">Symbol packages</span></span>

<span data-ttu-id="19788-158">NuGet destekler [ayrı sembol paketi oluşturuluyor](/nuget/create-packages/symbol-packages) içeren hata ayıklama PDB dosyaları .NET derlemelerini içeren ana paket yanı sıra.</span><span class="sxs-lookup"><span data-stu-id="19788-158">NuGet supports [generating a separate symbol package](/nuget/create-packages/symbol-packages) containing debug PDB files alongside the main package containing .NET assemblies.</span></span> <span data-ttu-id="19788-159">Sembol paketleri fikri bir sembol sunucusunda barındırılan ve yalnızca Visual Studio gibi bir araçla isteğe bağlı olarak yüklenen değildir.</span><span class="sxs-lookup"><span data-stu-id="19788-159">The idea of symbol packages is they're hosted on a symbol server and are only downloaded by a tool like Visual Studio on demand.</span></span>

<span data-ttu-id="19788-160">Şu anda genel ana sembolleri - [SymbolSource](http://www.symbolsource.org/) -oluşturulan taşınabilir pdb desteklemiyor tarafından SDK stili projeleri ve sembol paketleri yararlı değildir.</span><span class="sxs-lookup"><span data-stu-id="19788-160">Currently the main public host for symbols - [SymbolSource](http://www.symbolsource.org/) - doesn't support the portable PDBs created by SDK-style projects and symbol packages aren't useful.</span></span>

<span data-ttu-id="19788-161">**✔️ DÜŞÜNÜN** pdb ana NuGet paketini ekleme.</span><span class="sxs-lookup"><span data-stu-id="19788-161">**✔️ CONSIDER** embedding PDBs in the main NuGet package.</span></span>

<span data-ttu-id="19788-162">**❌ KAÇININ** pdb içeren bir sembol paketi oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="19788-162">**❌ AVOID** creating a symbols package containing PDBs.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="19788-163">[Önceki](./strong-naming.md)
[İleri](./dependencies.md)</span><span class="sxs-lookup"><span data-stu-id="19788-163">[Previous](./strong-naming.md)
[Next](./dependencies.md)</span></span>
