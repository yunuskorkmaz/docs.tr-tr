---
title: Çalışma zamanı paket deposu
description: .NET Core tarafından kullanılan bildirimleri hedeflemek için çalışma zamanı paket deposunu nasıl kullanacağınızı öğrenin.
ms.date: 08/12/2017
ms.openlocfilehash: ba3182b682e8a47397ac09ed46afe25190d34e5f
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134270"
---
# <a name="runtime-package-store"></a><span data-ttu-id="8fcd6-103">Çalışma zamanı paket deposu</span><span class="sxs-lookup"><span data-stu-id="8fcd6-103">Runtime package store</span></span>

<span data-ttu-id="8fcd6-104">.NET Core 2.0 ile başlayarak, uygulamaları hedef ortamda bulunan bilinen paketlere karşı paketleyip dağıtmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="8fcd6-104">Starting with .NET Core 2.0, it's possible to package and deploy apps against a known set of packages that exist in the target environment.</span></span> <span data-ttu-id="8fcd6-105">Avantajları daha hızlı dağıtımlar, daha düşük disk alanı kullanımı ve bazı durumlarda geliştirilmiş başlangıç performansıdır.</span><span class="sxs-lookup"><span data-stu-id="8fcd6-105">The benefits are faster deployments, lower disk space usage, and improved startup performance in some cases.</span></span>

<span data-ttu-id="8fcd6-106">Bu özellik, paketlerin depolandığı diskteki bir dizin olan *çalışma zamanı paket deposu*olarak uygulanır (genellikle macOS/Linux ve *C:/Program Files/dotnet/store* on Windows'da */usr/local/share/dotnet/store* adresinde).</span><span class="sxs-lookup"><span data-stu-id="8fcd6-106">This feature is implemented as a *runtime package store*, which is a directory on disk where packages are stored (typically at */usr/local/share/dotnet/store* on macOS/Linux and *C:/Program Files/dotnet/store* on Windows).</span></span> <span data-ttu-id="8fcd6-107">Bu dizin altında, mimariler ve [hedef çerçeveler](../../standard/frameworks.md)için alt dizinler vardır.</span><span class="sxs-lookup"><span data-stu-id="8fcd6-107">Under this directory, there are subdirectories for architectures and [target frameworks](../../standard/frameworks.md).</span></span> <span data-ttu-id="8fcd6-108">Dosya [düzeni, NuGet varlıklarının diskte düzenlenmesine](/nuget/create-packages/supporting-multiple-target-frameworks#framework-version-folder-structure)benzer:</span><span class="sxs-lookup"><span data-stu-id="8fcd6-108">The file layout is similar to the way that [NuGet assets are laid out on disk](/nuget/create-packages/supporting-multiple-target-frameworks#framework-version-folder-structure):</span></span>

```
\dotnet
    \store
        \x64
            \netcoreapp2.0
                \microsoft.applicationinsights
                \microsoft.aspnetcore
                ...
        \x86
            \netcoreapp2.0
                \microsoft.applicationinsights
                \microsoft.aspnetcore
                ...
```

<span data-ttu-id="8fcd6-109">*Hedef bildirim* dosyası, çalışma zamanı paket deposundaki paketleri listeler.</span><span class="sxs-lookup"><span data-stu-id="8fcd6-109">A *target manifest* file lists the packages in the runtime package store.</span></span> <span data-ttu-id="8fcd6-110">Geliştiriciler uygulamalarını yayınlarken bu bildirimi hedefleyebilirler.</span><span class="sxs-lookup"><span data-stu-id="8fcd6-110">Developers can target this manifest when publishing their app.</span></span> <span data-ttu-id="8fcd6-111">Hedef bildirim genellikle hedeflenen üretim ortamının sahibi tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="8fcd6-111">The target manifest is typically provided by the owner of the targeted production environment.</span></span>

## <a name="preparing-a-runtime-environment"></a><span data-ttu-id="8fcd6-112">Çalışma zamanı ortamı hazırlama</span><span class="sxs-lookup"><span data-stu-id="8fcd6-112">Preparing a runtime environment</span></span>

<span data-ttu-id="8fcd6-113">Çalışma zamanı ortamının yöneticisi, bir çalışma zamanı paket deposu ve ilgili hedef bildirimi oluşturarak uygulamaları daha hızlı dağıtımlar ve daha düşük disk alanı kullanımı için optimize edebilir.</span><span class="sxs-lookup"><span data-stu-id="8fcd6-113">The administrator of a runtime environment can optimize apps for faster deployments and lower disk space use by building a runtime package store and the corresponding target manifest.</span></span>

<span data-ttu-id="8fcd6-114">İlk adım, çalışma zamanı paket deposunu oluşturan paketleri listeleyen bir *paket deposu bildirimi* oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="8fcd6-114">The first step is to create a *package store manifest* that lists the packages that compose the runtime package store.</span></span> <span data-ttu-id="8fcd6-115">Bu dosya biçimi proje dosya biçimi *(csproj)* ile uyumludur.</span><span class="sxs-lookup"><span data-stu-id="8fcd6-115">This file format is compatible with the project file format (*csproj*).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="NUGET_PACKAGE" Version="VERSION" />
    <!-- Include additional packages here -->
  </ItemGroup>
</Project>
```

<span data-ttu-id="8fcd6-116">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="8fcd6-116">**Example**</span></span>

<span data-ttu-id="8fcd6-117">Aşağıdaki örnek paket deposu bildirimi *(packages.csproj)* [`Newtonsoft.Json`](https://www.nuget.org/packages/Newtonsoft.Json/) [`Moq`](https://www.nuget.org/packages/moq/) eklemek ve bir çalışma zamanı paket deposuna kullanılır:</span><span class="sxs-lookup"><span data-stu-id="8fcd6-117">The following example package store manifest (*packages.csproj*) is used to add [`Newtonsoft.Json`](https://www.nuget.org/packages/Newtonsoft.Json/) and [`Moq`](https://www.nuget.org/packages/moq/) to a runtime package store:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.3" />
    <PackageReference Include="Moq" Version="4.7.63" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="8fcd6-118">Paket deposu bildirimi, çalışma `dotnet store` zamanı ve çerçeve ile yürütülerek çalışma zamanı paket deposunu sağlama:</span><span class="sxs-lookup"><span data-stu-id="8fcd6-118">Provision the runtime package store by executing `dotnet store` with the package store manifest, runtime, and framework:</span></span>

```dotnetcli
dotnet store --manifest <PATH_TO_MANIFEST_FILE> --runtime <RUNTIME_IDENTIFIER> --framework <FRAMEWORK>
```

<span data-ttu-id="8fcd6-119">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="8fcd6-119">**Example**</span></span>

```dotnetcli
dotnet store --manifest packages.csproj --runtime win10-x64 --framework netcoreapp2.0 --framework-version 2.0.0
```

<span data-ttu-id="8fcd6-120">Komuttaki seçeneği ve yolu yineleyerek [`dotnet store`](../tools/dotnet-store.md) birden çok hedef paket deposu bildirim yolunu tek bir komuta geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8fcd6-120">You can pass multiple target package store manifest paths to a single [`dotnet store`](../tools/dotnet-store.md) command by repeating the option and path in the command.</span></span>

<span data-ttu-id="8fcd6-121">Varsayılan olarak, komutun çıktısı kullanıcıprofilinin *.dotnet/store* alt dizini altında bir paket deposudur.</span><span class="sxs-lookup"><span data-stu-id="8fcd6-121">By default, the output of the command is a package store under the *.dotnet/store* subdirectory of the user's profile.</span></span> <span data-ttu-id="8fcd6-122">`--output <OUTPUT_DIRECTORY>` Seçeneği kullanarak farklı bir konum belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8fcd6-122">You can specify a different location using the `--output <OUTPUT_DIRECTORY>` option.</span></span> <span data-ttu-id="8fcd6-123">Mağazanın kök dizini bir hedef bildirimi *artifakı.xml* dosyası içerir.</span><span class="sxs-lookup"><span data-stu-id="8fcd6-123">The root directory of the store contains a target manifest *artifact.xml* file.</span></span> <span data-ttu-id="8fcd6-124">Bu dosya indirilebilmek için kullanılabilir hale getirilebilir ve yayımlarken bu mağazayı hedeflemek isteyen uygulama yazarları tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8fcd6-124">This file can be made available for download and be used by app authors who want to target this store when publishing.</span></span>

<span data-ttu-id="8fcd6-125">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="8fcd6-125">**Example**</span></span>

<span data-ttu-id="8fcd6-126">Aşağıdaki *artifact.xml* dosyası önceki örnek çalıştırdıktan sonra üretilir.</span><span class="sxs-lookup"><span data-stu-id="8fcd6-126">The following *artifact.xml* file is produced after running the previous example.</span></span> <span data-ttu-id="8fcd6-127">Bu [`Castle.Core`](https://www.nuget.org/packages/Castle.Core/) bir bağımlılık olduğunu `Moq`unutmayın , bu yüzden otomatik olarak dahil ve *artifakı.xml* bildirim dosyasında görünür.</span><span class="sxs-lookup"><span data-stu-id="8fcd6-127">Note that [`Castle.Core`](https://www.nuget.org/packages/Castle.Core/) is a dependency of `Moq`, so it's included automatically and appears in the *artifacts.xml* manifest file.</span></span>

```xml
<StoreArtifacts>
  <Package Id="Newtonsoft.Json" Version="10.0.3" />
  <Package Id="Castle.Core" Version="4.1.0" />
  <Package Id="Moq" Version="4.7.63" />
</StoreArtifacts>
```

## <a name="publishing-an-app-against-a-target-manifest"></a><span data-ttu-id="8fcd6-128">Bir uygulamayı hedef bildirime karşı yayımlama</span><span class="sxs-lookup"><span data-stu-id="8fcd6-128">Publishing an app against a target manifest</span></span>

<span data-ttu-id="8fcd6-129">Diskte bir hedef bildirim dosyanız varsa, uygulamanızı [`dotnet publish`](../tools/dotnet-publish.md) komutla yayınlarken dosyaya giden yolu belirtirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8fcd6-129">If you have a target manifest file on disk, you specify the path to the file when publishing your app with the [`dotnet publish`](../tools/dotnet-publish.md) command:</span></span>

```dotnetcli
dotnet publish --manifest <PATH_TO_MANIFEST_FILE>
```

<span data-ttu-id="8fcd6-130">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="8fcd6-130">**Example**</span></span>

```dotnetcli
dotnet publish --manifest manifest.xml
```

<span data-ttu-id="8fcd6-131">Ortaya çıkan yayınlanmış uygulamayı, hedef bildirimde açıklanan paketlerin olduğu bir ortama dağıtırsınız.</span><span class="sxs-lookup"><span data-stu-id="8fcd6-131">You deploy the resulting published app to an environment that has the packages described in the target manifest.</span></span> <span data-ttu-id="8fcd6-132">Bunu yapamamak, uygulamanın başlayamamasına neden oluyor.</span><span class="sxs-lookup"><span data-stu-id="8fcd6-132">Failing to do so results in the app failing to start.</span></span>

<span data-ttu-id="8fcd6-133">Seçeneği ve yolu yineleyerek bir uygulamayı yayınlarken birden çok `--manifest manifest1.xml --manifest manifest2.xml`hedef bildirimi belirtin (örneğin, ).</span><span class="sxs-lookup"><span data-stu-id="8fcd6-133">Specify multiple target manifests when publishing an app by repeating the option and path (for example, `--manifest manifest1.xml --manifest manifest2.xml`).</span></span> <span data-ttu-id="8fcd6-134">Bunu yaptığınızda, uygulama komuta sağlanan hedef bildirim dosyalarında belirtilen paketlerin birleşimi için kırpılır.</span><span class="sxs-lookup"><span data-stu-id="8fcd6-134">When you do so, the app is trimmed for the union of packages specified in the target manifest files provided to the command.</span></span>

## <a name="specifying-target-manifests-in-the-project-file"></a><span data-ttu-id="8fcd6-135">Proje dosyasında hedef bildirimlerinin belirtilmesi</span><span class="sxs-lookup"><span data-stu-id="8fcd6-135">Specifying target manifests in the project file</span></span>

<span data-ttu-id="8fcd6-136">Komutla hedef bildirimleri belirtmenin [`dotnet publish`](../tools/dotnet-publish.md) alternatifi, bunları proje dosyasında \*\* \<TargetManifestFiles>\*\* etiketi altında yarı sütunlu ayrılmış bir yol listesi olarak belirtmektir.</span><span class="sxs-lookup"><span data-stu-id="8fcd6-136">An alternative to specifying target manifests with the [`dotnet publish`](../tools/dotnet-publish.md) command is to specify them in the project file as a semicolon-separated list of paths under a **\<TargetManifestFiles>** tag.</span></span>

```xml
<PropertyGroup>
  <TargetManifestFiles>manifest1.xml;manifest2.xml</TargetManifestFiles>
</PropertyGroup>
```

<span data-ttu-id="8fcd6-137">Proje dosyasındaki hedef bildirimlerini yalnızca uygulamanın hedef ortamı .NET Core projeleri gibi iyi bilindiğinde belirtin.</span><span class="sxs-lookup"><span data-stu-id="8fcd6-137">Specify the target manifests in the project file only when the target environment for the app is well-known, such as for .NET Core projects.</span></span> <span data-ttu-id="8fcd6-138">Bu açık kaynak projeleri için durum böyle değildir.</span><span class="sxs-lookup"><span data-stu-id="8fcd6-138">This isn't the case for open-source projects.</span></span> <span data-ttu-id="8fcd6-139">Açık kaynak proje kullanıcıları genellikle farklı üretim ortamlarına dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="8fcd6-139">The users of an open-source project typically deploy it to different production environments.</span></span> <span data-ttu-id="8fcd6-140">Bu üretim ortamları genellikle önceden yüklenmiş farklı paket kümeleri vardır.</span><span class="sxs-lookup"><span data-stu-id="8fcd6-140">These production environments generally have different sets of packages pre-installed.</span></span> <span data-ttu-id="8fcd6-141">Bu tür ortamlarda hedef bildirimi hakkında varsayımlarda bulunamazsınız, `--manifest` bu [`dotnet publish`](../tools/dotnet-publish.md)nedenle .</span><span class="sxs-lookup"><span data-stu-id="8fcd6-141">You can't make assumptions about the target manifest in such environments, so you should use the `--manifest` option of [`dotnet publish`](../tools/dotnet-publish.md).</span></span>

## <a name="aspnet-core-implicit-store"></a><span data-ttu-id="8fcd6-142">ASP.NET Çekirdek örtük mağaza</span><span class="sxs-lookup"><span data-stu-id="8fcd6-142">ASP.NET Core implicit store</span></span>

<span data-ttu-id="8fcd6-143">ASP.NET Core örtülü deposu yalnızca core 2.0 ASP.NET için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="8fcd6-143">The ASP.NET Core implicit store applies only to ASP.NET Core 2.0.</span></span> <span data-ttu-id="8fcd6-144">Uygulamaların core 2.1 ve sonrası ASP.NET kullanmalarını şiddetle öneririz, bu da örtük depoyu **kullanmaz.**</span><span class="sxs-lookup"><span data-stu-id="8fcd6-144">We strongly recommend applications use ASP.NET Core 2.1 and later, which does **not** use the implicit store.</span></span> <span data-ttu-id="8fcd6-145">ASP.NET Core 2.1 ve daha sonra paylaşılan çerçeveyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="8fcd6-145">ASP.NET Core 2.1 and later use the shared framework.</span></span>

<span data-ttu-id="8fcd6-146">Çalışma zamanı paket deposu özelliği, uygulama [çerçeveye bağımlı dağıtım (FDD)](index.md#publish-runtime-dependent) uygulaması olarak dağıtıldığında, ASP.NET Core uygulaması tarafından örtülü olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8fcd6-146">The runtime package store feature is used implicitly by an ASP.NET Core app when the app is deployed as a [framework-dependent deployment (FDD)](index.md#publish-runtime-dependent) app.</span></span> <span data-ttu-id="8fcd6-147">Hedefler, [`Microsoft.NET.Sdk.Web`](https://github.com/aspnet/websdk) hedef sistemdeki örtülü paket deposuna atıfta bulunan bildirimleri içerir.</span><span class="sxs-lookup"><span data-stu-id="8fcd6-147">The targets in [`Microsoft.NET.Sdk.Web`](https://github.com/aspnet/websdk) include manifests referencing the implicit package store on the target system.</span></span> <span data-ttu-id="8fcd6-148">Ayrıca, `Microsoft.AspNetCore.All` paket sonuçlarına bağlı olan herhangi bir FDD uygulaması, meta pakette listelenen paketleri değil, `Microsoft.AspNetCore.All` yalnızca uygulamayı ve varlıklarını içeren yayınlanmış bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="8fcd6-148">Additionally, any FDD app that depends on the `Microsoft.AspNetCore.All` package results in a published app that contains only the app and its assets and not the packages listed in the `Microsoft.AspNetCore.All` metapackage.</span></span> <span data-ttu-id="8fcd6-149">Bu paketlerin hedef sistemde olduğu varsayılıyor.</span><span class="sxs-lookup"><span data-stu-id="8fcd6-149">It's assumed that those packages are present on the target system.</span></span>

<span data-ttu-id="8fcd6-150">.NET Core SDK yüklendiğinde çalışma zamanı paket deposu ana bilgisayara yüklenir.</span><span class="sxs-lookup"><span data-stu-id="8fcd6-150">The runtime package store is installed on the host when the .NET Core SDK is installed.</span></span> <span data-ttu-id="8fcd6-151">Diğer yükleyiciler,.NET Core SDK, Red Hat Yum, `apt-get`.NET Core Windows Server Hosting paketi ve manuel çalışma zamanı paket mağaza yüklemeleri zip/tarball yüklemeleri de dahil olmak üzere çalışma zamanı paket deposu sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="8fcd6-151">Other installers may provide the runtime package store, including Zip/tarball installations of the .NET Core SDK, `apt-get`, Red Hat Yum, the .NET Core Windows Server Hosting bundle, and manual runtime package store installations.</span></span>

<span data-ttu-id="8fcd6-152">Çerçeveye bağımlı bir [dağıtım (FDD)](index.md#publish-runtime-dependent) uygulaması dağıtırken, hedef ortamın .NET Core SDK yüklü olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="8fcd6-152">When deploying a [framework-dependent deployment (FDD)](index.md#publish-runtime-dependent) app, make sure that the target environment has the .NET Core SDK installed.</span></span> <span data-ttu-id="8fcd6-153">Uygulama ASP.NET Core içermeyen bir ortama dağıtılırsa, aşağıdaki örnekte olduğu gibi proje `false` dosyasında>\*\* \<PublishWithAspNetCoreTargetManifest'i\*\* belirterek örtülü mağazayı devre dışı bırakabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8fcd6-153">If the app is deployed to an environment that doesn't include ASP.NET Core, you can opt out of the implicit store by specifying  **\<PublishWithAspNetCoreTargetManifest>** set to `false` in the project file as in the following example:</span></span>

```xml
<PropertyGroup>
  <PublishWithAspNetCoreTargetManifest>false</PublishWithAspNetCoreTargetManifest>
</PropertyGroup>
```

> [!NOTE]
> <span data-ttu-id="8fcd6-154">[Bağımsız dağıtım (SCD)](index.md#publish-self-contained) uygulamaları için, hedef sistemin gerekli bildirim paketlerini içermediği varsayılır.</span><span class="sxs-lookup"><span data-stu-id="8fcd6-154">For [self-contained deployment (SCD)](index.md#publish-self-contained) apps, it's assumed that the target system doesn't necessarily contain the required manifest packages.</span></span> <span data-ttu-id="8fcd6-155">Bu nedenle, \*\* \<PublishWithAspNetCoreTargetManifest\*\*>`true` bir SCD uygulaması için ayarlanamaz.</span><span class="sxs-lookup"><span data-stu-id="8fcd6-155">Therefore, **\<PublishWithAspNetCoreTargetManifest>** cannot be set to `true` for an SCD app.</span></span>

<span data-ttu-id="8fcd6-156">Dağıtımda bulunan bir bildirim bağımlılığı olan bir uygulama dağıtırsanız (derleme *çöp kutusu* klasöründe bulunur), çalışma zamanı paket deposu bu derlemeiçin ana bilgisayarda *kullanılmaz.*</span><span class="sxs-lookup"><span data-stu-id="8fcd6-156">If you deploy an application with a manifest dependency that's present in the deployment (the assembly is present in the *bin* folder), the runtime package store *isn't used* on the host for that assembly.</span></span> <span data-ttu-id="8fcd6-157">*Depo kutusu* klasörü derlemesi, ana bilgisayardaki çalışma zamanı paket deposundaki varlığından bağımsız olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8fcd6-157">The *bin* folder assembly is used regardless of its presence in the runtime package store on the host.</span></span>

<span data-ttu-id="8fcd6-158">Bildirimde belirtilen bağımlılığın sürümü, çalışma zamanı paket deposundaki bağımlılığın sürümüyle eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="8fcd6-158">The version of the dependency indicated in the manifest must match the version of the dependency in the runtime package store.</span></span> <span data-ttu-id="8fcd6-159">Hedef bildirimdeki bağımlılık ile çalışma zamanı paket deposunda bulunan sürüm arasında bir sürüm uyuşmazlığı varsa ve uygulama dağıtımında paketin gerekli sürümünü içermiyorsa, uygulama başlatılamıyorsa.</span><span class="sxs-lookup"><span data-stu-id="8fcd6-159">If you have a version mismatch between the dependency in the target manifest and the version that exists in the runtime package store and the app doesn't include the required version of the package in its deployment, the app fails to start.</span></span> <span data-ttu-id="8fcd6-160">Özel durum, çalışma zamanı paket deposu montajını çağıran hedef bildiriminin adını içerir ve bu da uyuşmazlığı gidermenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="8fcd6-160">The exception includes the name of the target manifest that called for the runtime package store assembly, which helps you troubleshoot the mismatch.</span></span>

<span data-ttu-id="8fcd6-161">Dağıtım yayımlamada *kırpıldığında,* yalnızca belirttiğiniz bildirim paketlerinin belirli sürümleri yayımlanmış çıktıdan uzak tutulur.</span><span class="sxs-lookup"><span data-stu-id="8fcd6-161">When the deployment is *trimmed* on publish, only the specific versions of the manifest packages you indicate are withheld from the published output.</span></span> <span data-ttu-id="8fcd6-162">Uygulamanın başlatabilmesi için belirtilen sürümlerde paketler inanılması için ana bilgisayarda bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8fcd6-162">The packages at the versions indicated must be present on the host for the app to start.</span></span>

## <a name="see-also"></a><span data-ttu-id="8fcd6-163">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8fcd6-163">See also</span></span>

- [<span data-ttu-id="8fcd6-164">dotnet-yayımla</span><span class="sxs-lookup"><span data-stu-id="8fcd6-164">dotnet-publish</span></span>](../tools/dotnet-publish.md)
- [<span data-ttu-id="8fcd6-165">dotnet mağaza</span><span class="sxs-lookup"><span data-stu-id="8fcd6-165">dotnet-store</span></span>](../tools/dotnet-store.md)
