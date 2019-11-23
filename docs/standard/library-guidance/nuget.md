---
title: NuGet ve .NET kitaplıkları
description: .NET kitaplıkları için NuGet ile paketleme için en iyi yöntem önerileri.
author: jamesnk
ms.author: mairaw
ms.date: 01/15/2019
ms.openlocfilehash: 9288bf440692302c3a0b1954236540af6363f367
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775307"
---
# <a name="nuget"></a><span data-ttu-id="1fb84-103">NuGet</span><span class="sxs-lookup"><span data-stu-id="1fb84-103">NuGet</span></span>

<span data-ttu-id="1fb84-104">NuGet, .NET ekosistemi için bir paket yöneticisidir ve geliştiricilerin .NET açık kaynaklı kitaplıklarını bulmasına ve almasına yönelik birincil yoldur.</span><span class="sxs-lookup"><span data-stu-id="1fb84-104">NuGet is a package manager for the .NET ecosystem and is the primary way developers discover and acquire .NET open-source libraries.</span></span> <span data-ttu-id="1fb84-105">NuGet paketlerini barındırmak için Microsoft tarafından sunulan ücretsiz bir hizmet olan [NuGet.org](https://www.nuget.org/), genel NuGet paketlerine yönelik birincil ana makinedir, ancak [myget](https://www.myget.org/) ve [Azure Artifacts](https://azure.microsoft.com/services/devops/artifacts/)gibi özel NuGet hizmetlerine yayımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1fb84-105">[NuGet.org](https://www.nuget.org/), a free service provided by Microsoft for hosting NuGet packages, is the primary host for public NuGet packages, but you can publish to custom NuGet services like [MyGet](https://www.myget.org/) and [Azure Artifacts](https://azure.microsoft.com/services/devops/artifacts/).</span></span>

<span data-ttu-id="1fb84-106">![NuGet](./media/nuget/nuget-logo.png "NuGet")</span><span class="sxs-lookup"><span data-stu-id="1fb84-106">![NuGet](./media/nuget/nuget-logo.png "NuGet")</span></span>

## <a name="create-a-nuget-package"></a><span data-ttu-id="1fb84-107">NuGet paketi oluşturma</span><span class="sxs-lookup"><span data-stu-id="1fb84-107">Create a NuGet package</span></span>

<span data-ttu-id="1fb84-108">Bir NuGet paketi (`*.nupkg`), .NET derlemelerini ve ilişkili meta verileri içeren bir zip dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="1fb84-108">A NuGet package (`*.nupkg`) is a zip file that contains .NET assemblies and associated metadata.</span></span>

<span data-ttu-id="1fb84-109">Bir NuGet paketi oluşturmanın iki ana yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="1fb84-109">There are two main ways to create a NuGet package.</span></span> <span data-ttu-id="1fb84-110">Daha yeni ve önerilen yol, bir SDK stili projeden paket oluşturmaktır (içeriği `<Project Sdk="Microsoft.NET.Sdk">`ile başlayan proje dosyası).</span><span class="sxs-lookup"><span data-stu-id="1fb84-110">The newer and recommended way is to create a package from a SDK-style project (project file whose content starts with `<Project Sdk="Microsoft.NET.Sdk">`).</span></span> <span data-ttu-id="1fb84-111">Derlemeler ve hedefler pakete otomatik olarak eklenir ve geri kalan meta veriler, paket adı ve sürüm numarası gibi MSBuild dosyasına eklenir.</span><span class="sxs-lookup"><span data-stu-id="1fb84-111">Assemblies and targets are automatically added to the package and remaining metadata is added to the MSBuild file, like package name and version number.</span></span> <span data-ttu-id="1fb84-112">[`dotnet pack`](../../core/tools/dotnet-pack.md) komutuyla derlemek, derlemeler yerine bir `*.nupkg` dosyası çıkışı verir.</span><span class="sxs-lookup"><span data-stu-id="1fb84-112">Compiling with the [`dotnet pack`](../../core/tools/dotnet-pack.md) command outputs a `*.nupkg` file instead of assemblies.</span></span>

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

<span data-ttu-id="1fb84-113">NuGet paketi oluşturmanın daha eski yolu, bir `*.nuspec` dosyası ve `nuget.exe` komut satırı aracıdır.</span><span class="sxs-lookup"><span data-stu-id="1fb84-113">The older way of creating a NuGet package is with a `*.nuspec` file and the `nuget.exe` command-line tool.</span></span> <span data-ttu-id="1fb84-114">Bir nuspec dosyası harika denetim sağlar ancak son NuGet paketine hangi derlemeleri ve hedefleri dahil edileceğini dikkatle belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1fb84-114">A nuspec file gives you great control but you must carefully specify what assemblies and targets to include in the final NuGet package.</span></span> <span data-ttu-id="1fb84-115">Bir hata yapmak veya birisinin değişiklik yaparken nuspec 'i güncelleştirmeyi unutmaları çok kolay.</span><span class="sxs-lookup"><span data-stu-id="1fb84-115">It's easy to make a mistake or for someone to forget to update the nuspec when making changes.</span></span> <span data-ttu-id="1fb84-116">Bir nuspec 'in avantajı, henüz bir SDK stili proje dosyasını desteklemeyen çerçeveler için NuGet paketleri oluşturmayı kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="1fb84-116">The advantage of a nuspec is you can use it create NuGet packages for frameworks that don't yet support an SDK-style project file.</span></span>

<span data-ttu-id="1fb84-117">**✔️** NuGet paketini oluşturmak için SDK stili bir proje dosyası kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="1fb84-117">**✔️ CONSIDER** using an SDK-style project file to create the NuGet package.</span></span>

## <a name="package-dependencies"></a><span data-ttu-id="1fb84-118">Paket bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="1fb84-118">Package dependencies</span></span>

<span data-ttu-id="1fb84-119">NuGet paketi bağımlılıkları, [Bağımlılıklar](./dependencies.md) makalesinde ayrıntılı olarak ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="1fb84-119">NuGet package dependencies are covered in detail in the [Dependencies](./dependencies.md) article.</span></span>

## <a name="important-nuget-package-metadata"></a><span data-ttu-id="1fb84-120">Önemli NuGet paketi meta verileri</span><span class="sxs-lookup"><span data-stu-id="1fb84-120">Important NuGet package metadata</span></span>

<span data-ttu-id="1fb84-121">Bir NuGet paketi birçok [meta veri özelliğini](/nuget/reference/nuspec)destekler.</span><span class="sxs-lookup"><span data-stu-id="1fb84-121">A NuGet package supports many [metadata properties](/nuget/reference/nuspec).</span></span> <span data-ttu-id="1fb84-122">Aşağıdaki tabloda, NuGet.org üzerindeki her paketin sağlaması gereken çekirdek meta veriler yer almaktadır:</span><span class="sxs-lookup"><span data-stu-id="1fb84-122">The following table contains the core metadata that every package on NuGet.org should provide:</span></span>

| <span data-ttu-id="1fb84-123">MSBuild özellik adı</span><span class="sxs-lookup"><span data-stu-id="1fb84-123">MSBuild Property name</span></span>              | <span data-ttu-id="1fb84-124">Nuspec adı</span><span class="sxs-lookup"><span data-stu-id="1fb84-124">Nuspec name</span></span>              | <span data-ttu-id="1fb84-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1fb84-125">Description</span></span>  |
| ---------------------------------- | ------------------------ | ------------ |
| `PackageId`                        | `id`                       | <span data-ttu-id="1fb84-126">Paket tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="1fb84-126">The package identifier.</span></span> <span data-ttu-id="1fb84-127">Tanımlayıcıdan bir önek, [ölçütlere](/nuget/reference/id-prefix-reservation)uyuyorsa ayrılabilir.</span><span class="sxs-lookup"><span data-stu-id="1fb84-127">A prefix from the identifier can be reserved if it meets the [criteria](/nuget/reference/id-prefix-reservation).</span></span> |
| `PackageVersion`                   | `version`                  | <span data-ttu-id="1fb84-128">NuGet paket sürümü.</span><span class="sxs-lookup"><span data-stu-id="1fb84-128">NuGet package version.</span></span> <span data-ttu-id="1fb84-129">Daha fazla bilgi için bkz. [NuGet paket sürümü](./versioning.md#nuget-package-version).</span><span class="sxs-lookup"><span data-stu-id="1fb84-129">For more information, see [NuGet package version](./versioning.md#nuget-package-version).</span></span>             |
| `Title`                            | `title`                    | <span data-ttu-id="1fb84-130">Paketin insan dostu bir başlığı.</span><span class="sxs-lookup"><span data-stu-id="1fb84-130">A human-friendly title of the package.</span></span> <span data-ttu-id="1fb84-131">Varsayılan olarak `PackageId`.</span><span class="sxs-lookup"><span data-stu-id="1fb84-131">It defaults to the `PackageId`.</span></span>             |
| `Description`                      | `description`              | <span data-ttu-id="1fb84-132">Kullanıcı arabiriminde görüntülenmekte olan paketin uzun açıklaması.</span><span class="sxs-lookup"><span data-stu-id="1fb84-132">A long description of the package displayed in UI.</span></span>             |
| `Authors`                          | `authors`                  | <span data-ttu-id="1fb84-133">Nuget.org üzerindeki profil adlarıyla eşleşen paket yazarları için virgülle ayrılmış bir liste.</span><span class="sxs-lookup"><span data-stu-id="1fb84-133">A comma-separated list of package authors, matching the profile names on nuget.org.</span></span>             |
| `PackageTags`                      | `tags`                     | <span data-ttu-id="1fb84-134">Paketi tanımlayan etiketlerin ve anahtar sözcüklerin boşlukla ayrılmış bir listesi.</span><span class="sxs-lookup"><span data-stu-id="1fb84-134">A space-delimited list of tags and keywords that describe the package.</span></span> <span data-ttu-id="1fb84-135">Etiketler, paketler aranırken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1fb84-135">Tags are used when searching for packages.</span></span>             |
| `PackageIconUrl`                   | `iconUrl`                  | <span data-ttu-id="1fb84-136">Paket için simge olarak kullanılacak bir görüntünün URL 'SI.</span><span class="sxs-lookup"><span data-stu-id="1fb84-136">A URL for an image to use as the icon for the package.</span></span> <span data-ttu-id="1fb84-137">URL HTTPS olmalıdır ve görüntü 64x64 olmalı ve saydam bir arka plana sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1fb84-137">URL should be HTTPS and the image should be 64x64 and have a transparent background.</span></span>             |
| `PackageProjectUrl`                | `projectUrl`               | <span data-ttu-id="1fb84-138">Proje giriş sayfası veya Kaynak deposu için bir URL.</span><span class="sxs-lookup"><span data-stu-id="1fb84-138">A URL for the project homepage or source repository.</span></span>             |
| `PackageLicenseExpression`         | `license`                  | <span data-ttu-id="1fb84-139">Proje lisansının [Spdx tanımlayıcısı](https://spdx.org/licenses/).</span><span class="sxs-lookup"><span data-stu-id="1fb84-139">The project license's [SPDX identifier](https://spdx.org/licenses/).</span></span> <span data-ttu-id="1fb84-140">Yalnızca OSı ve FSF onaylı lisanslar bir tanımlayıcı kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="1fb84-140">Only OSI and FSF approved licenses can use an identifier.</span></span> <span data-ttu-id="1fb84-141">Diğer lisanslar `PackageLicenseFile`kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1fb84-141">Other licenses should use `PackageLicenseFile`.</span></span> <span data-ttu-id="1fb84-142">[`license` meta verileri](/nuget/reference/nuspec#license)hakkında daha fazla bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="1fb84-142">Read more about [`license` metadata](/nuget/reference/nuspec#license).</span></span> |

> [!IMPORTANT]
> <span data-ttu-id="1fb84-143">Lisansı olmayan bir proje, özel bir [telif hakkı](https://choosealicense.com/no-permission/)için varsayılan olarak, diğer kişilerin kullanması mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="1fb84-143">A project without a license defaults to [exclusive copyright](https://choosealicense.com/no-permission/), making it legally impossible for other people to use.</span></span>

<span data-ttu-id="1fb84-144">**✔️** NuGet 'in önek ayırma [ölçütlerine](/nuget/reference/id-prefix-reservation)uyan bir ön ek içeren bir NuGet paketi adı seçmeyi düşünün.</span><span class="sxs-lookup"><span data-stu-id="1fb84-144">**✔️ CONSIDER** choosing a NuGet package name with a prefix that meets NuGet's prefix reservation [criteria](/nuget/reference/id-prefix-reservation).</span></span>

<span data-ttu-id="1fb84-145">**✔️** paket SIMGENIZIN https href 'i kullanır.</span><span class="sxs-lookup"><span data-stu-id="1fb84-145">**✔️ DO** use an HTTPS href to your package icon.</span></span>

> <span data-ttu-id="1fb84-146">HTTPS ile NuGet.org Run ve HTTPS olmayan bir görüntü görüntüleme gibi siteler, karışık bir içerik uyarısı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1fb84-146">Sites like NuGet.org run with HTTPS enabled and displaying a non-HTTPS image will create a mixed content warning.</span></span>

<span data-ttu-id="1fb84-147">**✔️** , 64x64 olan ve sonuçların en iyi şekilde görüntülenmesi için saydam bir arka plana sahip olan bir paket simge görüntüsünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="1fb84-147">**✔️ DO** use a package icon image that is 64x64 and has a transparent background for best viewing results.</span></span>

<span data-ttu-id="1fb84-148">**✔️** derlemelerinize ve NuGet paketinize kaynak denetimi meta verileri eklemek Için [kaynak bağlantısı](./sourcelink.md) kurmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="1fb84-148">**✔️ CONSIDER** setting up [Source Link](./sourcelink.md) to add source control metadata to your assemblies and NuGet package.</span></span>

> <span data-ttu-id="1fb84-149">Kaynak bağlantısı, NuGet paketine `RepositoryUrl` ve `RepositoryType` meta verileri otomatik olarak ekler.</span><span class="sxs-lookup"><span data-stu-id="1fb84-149">Source Link automatically adds `RepositoryUrl` and `RepositoryType` metadata to the NuGet package.</span></span> <span data-ttu-id="1fb84-150">Kaynak bağlantısı, paketin oluşturulduğu tam kaynak kodu hakkında bilgi de ekler.</span><span class="sxs-lookup"><span data-stu-id="1fb84-150">Source Link also adds information about the exact source code the package was built from.</span></span> <span data-ttu-id="1fb84-151">Örneğin, bir git deposundan oluşturulan bir pakette, işlem karması meta veriler olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="1fb84-151">For example, a package created from a Git repository will have the commit hash added as metadata.</span></span>

## <a name="pre-release-packages"></a><span data-ttu-id="1fb84-152">Yayın öncesi paketler</span><span class="sxs-lookup"><span data-stu-id="1fb84-152">Pre-release packages</span></span>

<span data-ttu-id="1fb84-153">Sürüm sonekine sahip NuGet paketleri [yayın öncesi](/nuget/create-packages/prerelease-packages)olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="1fb84-153">NuGet packages with a version suffix are considered [pre-release](/nuget/create-packages/prerelease-packages).</span></span> <span data-ttu-id="1fb84-154">Varsayılan olarak, NuGet Paket Yöneticisi kullanıcı ARABIRIMI, bir Kullanıcı paketleri ön serbest bırakma paketleri, sınırlı Kullanıcı testi için ideal hale getirmediği takdirde kararlı yayınlar gösterir.</span><span class="sxs-lookup"><span data-stu-id="1fb84-154">By default, the NuGet Package Manager UI shows stable releases unless a user opts-in to pre-release packages, making pre-release packages ideal for limited user testing.</span></span>

```xml
<PackageVersion>1.0.1-beta1</PackageVersion>
```

> [!NOTE]
> <span data-ttu-id="1fb84-155">Kararlı bir paket, yayın öncesi paketine bağımlı olamaz.</span><span class="sxs-lookup"><span data-stu-id="1fb84-155">A stable package cannot depend on a pre-release package.</span></span> <span data-ttu-id="1fb84-156">Kendi paketinizi yayın öncesi yapmanız veya daha eski bir kararlı sürüme bağlı olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1fb84-156">You must either make your own package pre-release or depend on an older stable version.</span></span>

<span data-ttu-id="1fb84-157">![NuGet yayın öncesi paket bağımlılığı](./media/nuget/nuget-prerelease-package.png "NuGet yayın öncesi paket bağımlılığı")</span><span class="sxs-lookup"><span data-stu-id="1fb84-157">![NuGet pre-release package dependency](./media/nuget/nuget-prerelease-package.png "NuGet pre-release package dependency")</span></span>

<span data-ttu-id="1fb84-158">**✔️** , test etme, önizleme veya deneme yaparken yayın öncesi paketi yayımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="1fb84-158">**✔️ DO** publish a pre-release package when testing, previewing, or experimenting.</span></span>

<span data-ttu-id="1fb84-159">**✔️** , diğer kararlı paketlerin buna başvurabilmesi için kararlı bir paket yayımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="1fb84-159">**✔️ DO** publish a stable package when its ready so other stable packages can reference it.</span></span>

## <a name="symbol-packages"></a><span data-ttu-id="1fb84-160">Sembol paketleri</span><span class="sxs-lookup"><span data-stu-id="1fb84-160">Symbol packages</span></span>

<span data-ttu-id="1fb84-161">Sembol dosyaları (`*.pdb`) derlemelerle birlikte .NET derleyicisi tarafından üretilir.</span><span class="sxs-lookup"><span data-stu-id="1fb84-161">Symbol files (`*.pdb`) are produced by the .NET compiler alongside assemblies.</span></span> <span data-ttu-id="1fb84-162">Sembol dosyaları, yürütme konumlarını özgün kaynak koduna eşler, böylece bir hata ayıklayıcı kullanarak çalışırken kaynak kodu adım adım ilerleyebilir.</span><span class="sxs-lookup"><span data-stu-id="1fb84-162">Symbol files map execution locations to the original source code so you can step through source code as it is running using a debugger.</span></span> <span data-ttu-id="1fb84-163">NuGet, .NET derlemeleri içeren ana paketin yanı sıra sembol dosyalarını içeren [ayrı bir sembol paketi (`*.snupkg`) oluşturmayı](/nuget/create-packages/symbol-packages-snupkg) destekler.</span><span class="sxs-lookup"><span data-stu-id="1fb84-163">NuGet supports [generating a separate symbol package (`*.snupkg`)](/nuget/create-packages/symbol-packages-snupkg) containing symbol files alongside the main package containing .NET assemblies.</span></span> <span data-ttu-id="1fb84-164">Sembol paketlerinin fikri, bir sembol sunucusunda barındırıldığından ve yalnızca isteğe bağlı Visual Studio gibi bir araç tarafından indirilir.</span><span class="sxs-lookup"><span data-stu-id="1fb84-164">The idea of symbol packages is they're hosted on a symbol server and are only downloaded by a tool like Visual Studio on demand.</span></span>

<span data-ttu-id="1fb84-165">NuGet.org kendi [sembolleri sunucu deposunu](/nuget/create-packages/symbol-packages-snupkg#nugetorg-symbol-server)barındırır.</span><span class="sxs-lookup"><span data-stu-id="1fb84-165">NuGet.org hosts its own [symbols server repository](/nuget/create-packages/symbol-packages-snupkg#nugetorg-symbol-server).</span></span> <span data-ttu-id="1fb84-166">Geliştiriciler, [Visual Studio 'daki sembol kaynaklarına](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger)`https://symbols.nuget.org/download/symbols` ekleyerek NuGet.org symbol sunucusunda yayınlanan sembolleri kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="1fb84-166">Developers can use the symbols published to the NuGet.org symbol server by adding `https://symbols.nuget.org/download/symbols` to their [symbol sources in Visual Studio](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1fb84-167">NuGet.org symbol sunucusu yalnızca SDK stili projeler tarafından oluşturulan yeni [Taşınabilir sembol dosyalarını](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md) (`*.pdb`) destekler.</span><span class="sxs-lookup"><span data-stu-id="1fb84-167">The NuGet.org symbol server only supports the new [portable symbol files](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md) (`*.pdb`) created by SDK-style projects.</span></span>
>
> <span data-ttu-id="1fb84-168">.NET kitaplığı 'nda hata ayıklarken NuGet.org symbol sunucusunu kullanmak için, geliştiriciler Visual Studio 2017 sürüm 15,9 veya üzeri bir sürüme sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1fb84-168">To use the NuGet.org symbol server when debugging a .NET library, developers must have Visual Studio 2017 version 15.9 or later.</span></span>

<span data-ttu-id="1fb84-169">Sembol paketi oluşturmanın bir alternatifi, sembol dosyalarını ana NuGet paketine katıştırmaya yönelik bir alternatiftir.</span><span class="sxs-lookup"><span data-stu-id="1fb84-169">An alternative to creating a symbol package is embedding symbol files in the main NuGet package.</span></span> <span data-ttu-id="1fb84-170">Ana NuGet paketi daha büyük olacaktır, ancak katıştırılmış sembol dosyaları, geliştiricilerin NuGet.org symbol sunucusunu yapılandırmasına gerek duymayacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="1fb84-170">The main NuGet package will be larger, but the embedded symbol files means developers don't need to configure the NuGet.org symbol server.</span></span> <span data-ttu-id="1fb84-171">NuGet paketinizi bir SDK stili proje kullanarak oluşturuyorsanız, `AllowedOutputExtensionsInPackageBuildOutputFolder` özelliğini ayarlayarak sembol dosyalarını ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1fb84-171">If you're building your NuGet package using an SDK-style project, then you can embed symbol files by setting the `AllowedOutputExtensionsInPackageBuildOutputFolder` property:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
 <PropertyGroup>
    <!-- Include symbol files (*.pdb) in the built .nupkg -->
    <AllowedOutputExtensionsInPackageBuildOutputFolder>$(AllowedOutputExtensionsInPackageBuildOutputFolder);.pdb</AllowedOutputExtensionsInPackageBuildOutputFolder>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="1fb84-172">Sembol dosyalarını gömmenin dezavantajı, SDK stilindeki projeler kullanılarak derlenen .NET kitaplıkları için paket boyutunu %30 oranında artırdı.</span><span class="sxs-lookup"><span data-stu-id="1fb84-172">The downside of embedding symbol files is that they increase the package size by about 30% for .NET libraries compiled using SDK-style projects.</span></span> <span data-ttu-id="1fb84-173">Paket boyutu bir sorun oluşturacaksa, sembolleri bir sembol paketinde yayımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1fb84-173">If package size is a concern, you should publish symbols in a symbol package instead.</span></span>

<span data-ttu-id="1fb84-174">**✔️** sembolleri bir sembol paketi olarak yayımlamayı düşünün (`*.snupkg`) NuGet.org</span><span class="sxs-lookup"><span data-stu-id="1fb84-174">**✔️ CONSIDER** publishing symbols as a symbol package (`*.snupkg`) to NuGet.org</span></span>

> <span data-ttu-id="1fb84-175">Sembol paketleri (`*.snupkg`), geliştiricilere ana paket boyutunu ayıklamadan ve NuGet paketinde hata ayıklamaya yönelik geri yükleme performansını etkilemeden iyi bir istek üzerine hata ayıklama deneyimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="1fb84-175">Symbol packages (`*.snupkg`) provide developers a good on-demand debugging experience without bloating the main package size and impacting restore performance for those who don't intend to debug the NuGet package.</span></span>
>
> <span data-ttu-id="1fb84-176">Desteklenmediği uyarısıyla, kullanıcıların sembol dosyalarını almak için IDE (tek seferlik kurulum olarak) içinde NuGet sembol sunucusunu bulması ve yapılandırması gerekebilecek bir işlem olabilir.</span><span class="sxs-lookup"><span data-stu-id="1fb84-176">The caveat is that users may need to find and configure the NuGet symbol server in their IDE (as a one-time setup) to get symbol files.</span></span> <span data-ttu-id="1fb84-177">Visual Studio 2019 sürüm 16,1 varsayılan sembol sunucuları listesine NuGet. org 'ın sembol sunucusunu ekledi.</span><span class="sxs-lookup"><span data-stu-id="1fb84-177">Visual Studio 2019 version 16.1 added NuGet.org's symbol server to the list of default symbol servers.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="1fb84-178">[Önceki](strong-naming.md)
>[İleri](dependencies.md)</span><span class="sxs-lookup"><span data-stu-id="1fb84-178">[Previous](strong-naming.md)
[Next](dependencies.md)</span></span>
