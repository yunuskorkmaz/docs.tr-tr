---
title: NuGet ve .NET kitaplıkları
description: En iyi yöntem önerileri paketleme için NuGet ile .NET kitaplıkları.
author: jamesnk
ms.author: mairaw
ms.date: 01/15/2019
ms.openlocfilehash: 6c3c7feb95f0ebe6b348f42cdd243ce1d14b9c50
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333427"
---
# <a name="nuget"></a><span data-ttu-id="749b3-103">NuGet</span><span class="sxs-lookup"><span data-stu-id="749b3-103">NuGet</span></span>

<span data-ttu-id="749b3-104">NuGet için .NET ekosisteminin bir paket yöneticisidir ve birincil yolu geliştiriciler keşfedin ve .NET açık kaynak kitaplıklarını edinebilir.</span><span class="sxs-lookup"><span data-stu-id="749b3-104">NuGet is a package manager for the .NET ecosystem and is the primary way developers discover and acquire .NET open-source libraries.</span></span> <span data-ttu-id="749b3-105">[NuGet.org](https://www.nuget.org/), NuGet paketlerini barındırmak için Microsoft tarafından sağlanan ücretsiz bir hizmet olduğundan birincil konak genel NuGet paketleri için ancak gibi özel NuGet hizmetlerine yayımlayabilirsiniz [MyGet](https://www.myget.org/) ve [Azure Yapıtları ](https://azure.microsoft.com/services/devops/artifacts/).</span><span class="sxs-lookup"><span data-stu-id="749b3-105">[NuGet.org](https://www.nuget.org/), a free service provided by Microsoft for hosting NuGet packages, is the primary host for public NuGet packages, but you can publish to custom NuGet services like [MyGet](https://www.myget.org/) and [Azure Artifacts](https://azure.microsoft.com/services/devops/artifacts/).</span></span>

<span data-ttu-id="749b3-106">![NuGet](./media/nuget/nuget-logo.png "NuGet")</span><span class="sxs-lookup"><span data-stu-id="749b3-106">![NuGet](./media/nuget/nuget-logo.png "NuGet")</span></span>

## <a name="create-a-nuget-package"></a><span data-ttu-id="749b3-107">Bir NuGet paketi oluşturma</span><span class="sxs-lookup"><span data-stu-id="749b3-107">Create a NuGet package</span></span>

<span data-ttu-id="749b3-108">Bir NuGet paketi (`*.nupkg`) .NET derlemelerini ve ilişkili meta verileri içeren bir zip dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="749b3-108">A NuGet package (`*.nupkg`) is a zip file that contains .NET assemblies and associated metadata.</span></span>

<span data-ttu-id="749b3-109">Bir NuGet paketi oluşturmak için iki ana yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="749b3-109">There are two main ways to create a NuGet package.</span></span> <span data-ttu-id="749b3-110">Yeni ve önerilen bir SDK stilinde projeden bir paketi oluşturmak için yoludur (proje dosyası içerikleri ile başlayan `<Project Sdk="Microsoft.NET.Sdk">`).</span><span class="sxs-lookup"><span data-stu-id="749b3-110">The newer and recommended way is to create a package from a SDK-style project (project file whose content starts with `<Project Sdk="Microsoft.NET.Sdk">`).</span></span> <span data-ttu-id="749b3-111">Derlemeler ve hedefleri paketi otomatik olarak eklenir ve meta verileri kalan paket adı ve sürüm numarası gibi MSBuild dosyasına eklenir.</span><span class="sxs-lookup"><span data-stu-id="749b3-111">Assemblies and targets are automatically added to the package and remaining metadata is added to the MSBuild file, like package name and version number.</span></span> <span data-ttu-id="749b3-112">İle derlerken [ `dotnet pack` ](../../core/tools/dotnet-pack.md) çıktılar komut bir `*.nupkg` derlemeler yerine dosya.</span><span class="sxs-lookup"><span data-stu-id="749b3-112">Compiling with the [`dotnet pack`](../../core/tools/dotnet-pack.md) command outputs a `*.nupkg` file instead of assemblies.</span></span>

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

<span data-ttu-id="749b3-113">Bir NuGet paketi oluşturma eski yöntem, bir `*.nuspec` dosya ve `nuget.exe` komut satırı aracı.</span><span class="sxs-lookup"><span data-stu-id="749b3-113">The older way of creating a NuGet package is with a `*.nuspec` file and the `nuget.exe` command-line tool.</span></span> <span data-ttu-id="749b3-114">Soubor nuspec çok denetimi verir ancak hangi derlemelerin ve hedefleri son NuGet paket içerisine dâhil etmek dikkatli bir şekilde belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="749b3-114">A nuspec file gives you great control but you must carefully specify what assemblies and targets to include in the final NuGet package.</span></span> <span data-ttu-id="749b3-115">Bir hata yapmak kolaydır veya birinin değişiklikler yaparken nuspec güncelleştirilecek unutmayın.</span><span class="sxs-lookup"><span data-stu-id="749b3-115">It's easy to make a mistake or for someone to forget to update the nuspec when making changes.</span></span> <span data-ttu-id="749b3-116">Kullanabilirsiniz bir nuspec avantajlarındandır henüz bir SDK stilinde proje dosyası desteklemeyen çerçeveler için NuGet paketleri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="749b3-116">The advantage of a nuspec is you can use it create NuGet packages for frameworks that don't yet support an SDK-style project file.</span></span>

<span data-ttu-id="749b3-117">**✔️ DÜŞÜNÜN** NuGet paketi oluşturmak için bir SDK stilinde proje dosyasını kullanarak.</span><span class="sxs-lookup"><span data-stu-id="749b3-117">**✔️ CONSIDER** using an SDK-style project file to create the NuGet package.</span></span>

## <a name="package-dependencies"></a><span data-ttu-id="749b3-118">Paket bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="749b3-118">Package dependencies</span></span>

<span data-ttu-id="749b3-119">NuGet Paket bağımlılıklarını ayrıntılı olarak ele alınmıştır [bağımlılıkları](./dependencies.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="749b3-119">NuGet package dependencies are covered in detail in the [Dependencies](./dependencies.md) article.</span></span>

## <a name="important-nuget-package-metadata"></a><span data-ttu-id="749b3-120">Önemli NuGet paketi meta verileri</span><span class="sxs-lookup"><span data-stu-id="749b3-120">Important NuGet package metadata</span></span>

<span data-ttu-id="749b3-121">Bir NuGet paketi birçok destekler [meta veri özelliklerini](/nuget/reference/nuspec).</span><span class="sxs-lookup"><span data-stu-id="749b3-121">A NuGet package supports many [metadata properties](/nuget/reference/nuspec).</span></span> <span data-ttu-id="749b3-122">Aşağıdaki tabloda, her paket nuget.org sağlamalıdır çekirdek meta veriler içerir:</span><span class="sxs-lookup"><span data-stu-id="749b3-122">The following table contains the core metadata that every package on NuGet.org should provide:</span></span>

| <span data-ttu-id="749b3-123">MSBuild özellik adı</span><span class="sxs-lookup"><span data-stu-id="749b3-123">MSBuild Property name</span></span>              | <span data-ttu-id="749b3-124">Nuspec adı</span><span class="sxs-lookup"><span data-stu-id="749b3-124">Nuspec name</span></span>              | <span data-ttu-id="749b3-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="749b3-125">Description</span></span>  |
| ---------------------------------- | ------------------------ | ------------ |
| `PackageId`                        | `id`                       | <span data-ttu-id="749b3-126">Paket tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="749b3-126">The package identifier.</span></span> <span data-ttu-id="749b3-127">Bunu karşılıyorsa tanımlayıcı önekten ayrılabileceğini [ölçütleri](/nuget/reference/id-prefix-reservation).</span><span class="sxs-lookup"><span data-stu-id="749b3-127">A prefix from the identifier can be reserved if it meets the [criteria](/nuget/reference/id-prefix-reservation).</span></span> |
| `PackageVersion`                   | `version`                  | <span data-ttu-id="749b3-128">NuGet Paket sürümü.</span><span class="sxs-lookup"><span data-stu-id="749b3-128">NuGet package version.</span></span> <span data-ttu-id="749b3-129">Daha fazla bilgi için [NuGet paketi sürüm](./versioning.md#nuget-package-version).</span><span class="sxs-lookup"><span data-stu-id="749b3-129">For more information, see [NuGet package version](./versioning.md#nuget-package-version).</span></span>             |
| `Title`                            | `title`                    | <span data-ttu-id="749b3-130">Paket bir insan dostu başlığı.</span><span class="sxs-lookup"><span data-stu-id="749b3-130">A human-friendly title of the package.</span></span> <span data-ttu-id="749b3-131">Varsayılan `PackageId`.</span><span class="sxs-lookup"><span data-stu-id="749b3-131">It defaults to the `PackageId`.</span></span>             |
| `Description`                      | `description`              | <span data-ttu-id="749b3-132">Kullanıcı Arabiriminde görüntülenen paketinin uzun açıklaması.</span><span class="sxs-lookup"><span data-stu-id="749b3-132">A long description of the package displayed in UI.</span></span>             |
| `Authors`                          | `authors`                  | <span data-ttu-id="749b3-133">Nuget.org profil adları eşleşen, paket yazarlarının virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="749b3-133">A comma-separated list of package authors, matching the profile names on nuget.org.</span></span>             |
| `PackageTags`                      | `tags`                     | <span data-ttu-id="749b3-134">Etiketleri ve paket tanımlayan anahtar sözcükleri boşlukla ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="749b3-134">A space-delimited list of tags and keywords that describe the package.</span></span> <span data-ttu-id="749b3-135">Etiketleri paketler için arama yaparken de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="749b3-135">Tags are used when searching for packages.</span></span>             |
| `PackageIconUrl`                   | `iconUrl`                  | <span data-ttu-id="749b3-136">Paket için simge olarak kullanılacak bir URL için bir görüntü.</span><span class="sxs-lookup"><span data-stu-id="749b3-136">A URL for an image to use as the icon for the package.</span></span> <span data-ttu-id="749b3-137">HTTPS URL'si olmalıdır ve görüntü 64 x 64 olmalıdır ve saydam bir arka plana sahip.</span><span class="sxs-lookup"><span data-stu-id="749b3-137">URL should be HTTPS and the image should be 64x64 and have a transparent background.</span></span>             |
| `PackageProjectUrl`                | `projectUrl`               | <span data-ttu-id="749b3-138">Proje giriş sayfası veya kaynak havuzu için bir URL.</span><span class="sxs-lookup"><span data-stu-id="749b3-138">A URL for the project homepage or source repository.</span></span>             |
| `PackageLicenseExpression`         | `license`                  | <span data-ttu-id="749b3-139">Proje Lisans'ın [SPDX tanımlayıcı](https://spdx.org/licenses/).</span><span class="sxs-lookup"><span data-stu-id="749b3-139">The project license's [SPDX identifier](https://spdx.org/licenses/).</span></span> <span data-ttu-id="749b3-140">OSI ve FSF lisansları onaylanan yalnızca bir tanımlayıcıyı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="749b3-140">Only OSI and FSF approved licenses can use an identifier.</span></span> <span data-ttu-id="749b3-141">Diğer lisans kullanması gereken `PackageLicenseFile`.</span><span class="sxs-lookup"><span data-stu-id="749b3-141">Other licenses should use `PackageLicenseFile`.</span></span> <span data-ttu-id="749b3-142">Daha fazla bilgi edinin [ `license` meta verileri](/nuget/reference/nuspec#license).</span><span class="sxs-lookup"><span data-stu-id="749b3-142">Read more about [`license` metadata](/nuget/reference/nuspec#license).</span></span> |

> [!IMPORTANT]
> <span data-ttu-id="749b3-143">Bir proje için varsayılan olarak bir lisans olmadan [özel telif hakkı](https://choosealicense.com/no-permission/), diğer kullanıcıların yasal imkansız hale getirme.</span><span class="sxs-lookup"><span data-stu-id="749b3-143">A project without a license defaults to [exclusive copyright](https://choosealicense.com/no-permission/), making it legally impossible for other people to use.</span></span>

<span data-ttu-id="749b3-144">**✔️ DÜŞÜNÜN** NuGet'ın ön eki ayırma karşılayan bir önek ile NuGet paket adı seçerek [ölçütleri](/nuget/reference/id-prefix-reservation).</span><span class="sxs-lookup"><span data-stu-id="749b3-144">**✔️ CONSIDER** choosing a NuGet package name with a prefix that meets NuGet's prefix reservation [criteria](/nuget/reference/id-prefix-reservation).</span></span>

<span data-ttu-id="749b3-145">**✔️ YAPMAK** paket simge için bir HTTPS href kullanın.</span><span class="sxs-lookup"><span data-stu-id="749b3-145">**✔️ DO** use an HTTPS href to your package icon.</span></span>

> <span data-ttu-id="749b3-146">İle HTTPS etkin site NuGet.org gibi çalıştırın ve HTTPS olmayan bir resim görüntüleyen bir karışık içerik uyarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="749b3-146">Sites like NuGet.org run with HTTPS enabled and displaying a non-HTTPS image will create a mixed content warning.</span></span>

<span data-ttu-id="749b3-147">**✔️ YAPMAK** 64 x 64 ve en iyi sonuçları görüntülemek için saydam bir arka plana sahip bir paket simge görüntüsü kullanın.</span><span class="sxs-lookup"><span data-stu-id="749b3-147">**✔️ DO** use a package icon image that is 64x64 and has a transparent background for best viewing results.</span></span>

<span data-ttu-id="749b3-148">**✔️ DÜŞÜNÜN** ayarlama [SourceLink](./sourcelink.md) NuGet paketi ve derlemeler için kaynak denetimi meta verilerini eklemek için.</span><span class="sxs-lookup"><span data-stu-id="749b3-148">**✔️ CONSIDER** setting up [SourceLink](./sourcelink.md) to add source control metadata to your assemblies and NuGet package.</span></span>

> <span data-ttu-id="749b3-149">SourceLink otomatik olarak ekler `RepositoryUrl` ve `RepositoryType` NuGet paketi meta verileri.</span><span class="sxs-lookup"><span data-stu-id="749b3-149">SourceLink automatically adds `RepositoryUrl` and `RepositoryType` metadata to the NuGet package.</span></span> <span data-ttu-id="749b3-150">SourceLink Ayrıca paket tam kaynak kodu hakkında bilgi oluşturulmuş ekler.</span><span class="sxs-lookup"><span data-stu-id="749b3-150">SourceLink also adds information about the exact source code the package was built from.</span></span> <span data-ttu-id="749b3-151">Örneğin, bir Git deposundan oluşturulan bir paket olarak meta veriler eklenen işleme karması sahip olur.</span><span class="sxs-lookup"><span data-stu-id="749b3-151">For example, a package created from a Git repository will have the commit hash added as metadata.</span></span>

## <a name="pre-release-packages"></a><span data-ttu-id="749b3-152">Yayın öncesi paketleri</span><span class="sxs-lookup"><span data-stu-id="749b3-152">Pre-release packages</span></span>

<span data-ttu-id="749b3-153">NuGet paketlerini sürüm sonekine sahip olarak kabul edilir [yayın öncesi](/nuget/create-packages/prerelease-packages).</span><span class="sxs-lookup"><span data-stu-id="749b3-153">NuGet packages with a version suffix are considered [pre-release](/nuget/create-packages/prerelease-packages).</span></span> <span data-ttu-id="749b3-154">Bir kullanıcı kabul eder yayın öncesi paketleri, yayın öncesi paketleri sınırlı kullanıcı test için ideal hale açma sürece varsayılan olarak, NuGet Paket Yöneticisi UI kararlı yayınları gösterir.</span><span class="sxs-lookup"><span data-stu-id="749b3-154">By default, the NuGet Package Manager UI shows stable releases unless a user opts-in to pre-release packages, making pre-release packages ideal for limited user testing.</span></span>

```xml
<PackageVersion>1.0.1-beta1</PackageVersion>
```

> [!NOTE]
> <span data-ttu-id="749b3-155">Bir kararlı paket bir yayın öncesi pakete bağımlı olamaz.</span><span class="sxs-lookup"><span data-stu-id="749b3-155">A stable package cannot depend on a pre-release package.</span></span> <span data-ttu-id="749b3-156">Yayın öncesi kendi paket yapmak veya eski bir kararlı sürüme bağlı.</span><span class="sxs-lookup"><span data-stu-id="749b3-156">You must either make your own package pre-release or depend on an older stable version.</span></span>

<span data-ttu-id="749b3-157">![NuGet yayın öncesi paket bağımlılığı](./media/nuget/nuget-prerelease-package.png "NuGet yayın öncesi paket bağımlılığı")</span><span class="sxs-lookup"><span data-stu-id="749b3-157">![NuGet pre-release package dependency](./media/nuget/nuget-prerelease-package.png "NuGet pre-release package dependency")</span></span>

<span data-ttu-id="749b3-158">**✔️ YAPMAK** test etme, Önizleme veya deneme yayın öncesi paket yayımlama.</span><span class="sxs-lookup"><span data-stu-id="749b3-158">**✔️ DO** publish a pre-release package when testing, previewing, or experimenting.</span></span>

<span data-ttu-id="749b3-159">**✔️ YAPMAK** , hazır, bu nedenle diğer kararlı paketleri başvuruda bulunduğunuzda bir kararlı paket yayımlama.</span><span class="sxs-lookup"><span data-stu-id="749b3-159">**✔️ DO** publish a stable package when its ready so other stable packages can reference it.</span></span>

## <a name="symbol-packages"></a><span data-ttu-id="749b3-160">Sembol paketleri</span><span class="sxs-lookup"><span data-stu-id="749b3-160">Symbol packages</span></span>

<span data-ttu-id="749b3-161">Sembol dosyaları (`*.pdb`) derlemeleri yanı sıra .NET derleyici tarafından üretilen.</span><span class="sxs-lookup"><span data-stu-id="749b3-161">Symbol files (`*.pdb`) are produced by the .NET compiler alongside assemblies.</span></span> <span data-ttu-id="749b3-162">Sembol dosyaları harita yürütme konumu özgün kaynak kodu, kaynak kodu olarak aracılığıyla girmek için bir hata ayıklayıcıyı kullanarak çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="749b3-162">Symbol files map execution locations to the original source code so you can step through source code as it is running using a debugger.</span></span> <span data-ttu-id="749b3-163">NuGet destekler [ayrı sembol paketi oluşturuluyor (`*.snupkg`)](/nuget/create-packages/symbol-packages-snupkg) .NET derlemelerini içeren ana paket yanı sıra sembol dosyalarını içeren.</span><span class="sxs-lookup"><span data-stu-id="749b3-163">NuGet supports [generating a separate symbol package (`*.snupkg`)](/nuget/create-packages/symbol-packages-snupkg) containing symbol files alongside the main package containing .NET assemblies.</span></span> <span data-ttu-id="749b3-164">Sembol paketleri fikri bir sembol sunucusunda barındırılan ve yalnızca Visual Studio gibi bir araçla isteğe bağlı olarak yüklenen değildir.</span><span class="sxs-lookup"><span data-stu-id="749b3-164">The idea of symbol packages is they're hosted on a symbol server and are only downloaded by a tool like Visual Studio on demand.</span></span>

<span data-ttu-id="749b3-165">NuGet.org barındıran kendi [sembolleri sunucu deposu](/nuget/create-packages/symbol-packages-snupkg#nugetorg-symbol-server).</span><span class="sxs-lookup"><span data-stu-id="749b3-165">NuGet.org hosts its own [symbols server repository](/nuget/create-packages/symbol-packages-snupkg#nugetorg-symbol-server).</span></span> <span data-ttu-id="749b3-166">Geliştiriciler, ekleyerek NuGet.org sembol sunucusuna yayımlanması ve simgeleri kullanabilirsiniz `https://symbols.nuget.org/download/symbols` için kendi [sembol kaynakları Visual Studio'da](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger).</span><span class="sxs-lookup"><span data-stu-id="749b3-166">Developers can use the symbols published to the NuGet.org symbol server by adding `https://symbols.nuget.org/download/symbols` to their [symbol sources in Visual Studio](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="749b3-167">NuGet.org sembol sunucusu yalnızca yeni destekler [taşınabilir sembol dosyalarını](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md) (`*.pdb`) SDK stili projeleri tarafından oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="749b3-167">The NuGet.org symbol server only supports the new [portable symbol files](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md) (`*.pdb`) created by SDK-style projects.</span></span>
>
> <span data-ttu-id="749b3-168">Bir .NET kitaplığı hata ayıklama sırasında NuGet.org sembol sunucusu kullanmak için geliştiricilerin Visual Studio 2017 15.9 olmalıdır veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="749b3-168">To use the NuGet.org symbol server when debugging a .NET library, developers must have Visual Studio 2017 15.9 or later.</span></span>

<span data-ttu-id="749b3-169">Alternatif bir sembol paketi oluşturma seçeneği, ana NuGet paketinin sembol dosyaları ekleme.</span><span class="sxs-lookup"><span data-stu-id="749b3-169">An alternative to creating a symbol package is embedding symbol files in the main NuGet package.</span></span> <span data-ttu-id="749b3-170">Ana NuGet paketini daha büyük olacaktır, ancak katıştırılmış sembol dosyaları geliştiriciler NuGet.org sembol sunucusu yapılandırmanız gerekmez anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="749b3-170">The main NuGet package will be larger, but the embedded symbol files means developers don't need to configure the NuGet.org symbol server.</span></span> <span data-ttu-id="749b3-171">NuGet paketi kullanarak bir SDK stilinde projesi oluştururken ardından sembol dosyalarını ayarlayarak katıştırabilirsiniz `AllowedOutputExtensionsInPackageBuildOutputFolder` özelliği:</span><span class="sxs-lookup"><span data-stu-id="749b3-171">If you're building your NuGet package using an SDK-style project, then you can embed symbol files by setting the `AllowedOutputExtensionsInPackageBuildOutputFolder` property:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
 <PropertyGroup>
    <!-- Include symbol files (*.pdb) in the built .nupkg -->
    <AllowedOutputExtensionsInPackageBuildOutputFolder>$(AllowedOutputExtensionsInPackageBuildOutputFolder);.pdb</AllowedOutputExtensionsInPackageBuildOutputFolder>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="749b3-172">**✔️ DÜŞÜNÜN** sembol dosyaları ana NuGet paketini ekleme.</span><span class="sxs-lookup"><span data-stu-id="749b3-172">**✔️ CONSIDER** embedding symbol files in the main NuGet package.</span></span>

> <span data-ttu-id="749b3-173">Sembol dosyaları ana NuGet paketini ekleme geliştiriciler varsayılan olarak daha iyi hata ayıklama deneyimi sunar.</span><span class="sxs-lookup"><span data-stu-id="749b3-173">Embedding symbol files in the main NuGet package gives developers a better debugging experience by default.</span></span> <span data-ttu-id="749b3-174">Bulup sembol dosyaları almak için kendi IDE'de NuGet sembol sunucusu yapılandırmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="749b3-174">They don't need to find and configure the NuGet symbol server in their IDE to get symbol files.</span></span>
>
> <span data-ttu-id="749b3-175">Katıştırılmış sembol dosyalarını dezavantajı, paket boyutu yaklaşık %30 SDK stili projeleri kullanılarak derlenmiş .NET kitaplıkları için daha fazla olur.</span><span class="sxs-lookup"><span data-stu-id="749b3-175">The downside to embedded symbol files is they increase the package size by about 30% for .NET libraries compiled using SDK-style projects.</span></span> <span data-ttu-id="749b3-176">Paket boyutu önemliyse, sembolleri bir sembol paketi bunun yerine yayımlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="749b3-176">If package size is a concern, you should publish symbols in a symbol package instead.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="749b3-177">[Önceki](strong-naming.md)
>[İleri](dependencies.md)</span><span class="sxs-lookup"><span data-stu-id="749b3-177">[Previous](strong-naming.md)
[Next](dependencies.md)</span></span>
