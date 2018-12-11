---
title: Çalışma zamanı Paket Deposu
description: .NET Core tarafından kullanılan hedef bildirimleri için çalışma zamanı Paket Deposu kullanmayı öğrenin.
author: bleroy
ms.date: 08/12/2017
ms.custom: seodec18
ms.openlocfilehash: a190e148715547fde29d3a852183ea4d75065e79
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170359"
---
# <a name="runtime-package-store"></a><span data-ttu-id="4a47c-103">Çalışma zamanı Paket Deposu</span><span class="sxs-lookup"><span data-stu-id="4a47c-103">Runtime package store</span></span>

<span data-ttu-id="4a47c-104">.NET Core 2.0 ile başlayarak, paketleme ve dağıtma hedef ortamda mevcut paketleri bilinen bir dizi karşı uygulamalar mümkündür.</span><span class="sxs-lookup"><span data-stu-id="4a47c-104">Starting with .NET Core 2.0, it's possible to package and deploy apps against a known set of packages that exist in the target environment.</span></span> <span data-ttu-id="4a47c-105">Daha hızlı dağıtımlar, daha düşük disk alanı kullanımı ve bazı durumlarda geliştirilmiş başlangıç performansı yararlar şunlardır.</span><span class="sxs-lookup"><span data-stu-id="4a47c-105">The benefits are faster deployments, lower disk space usage, and improved startup performance in some cases.</span></span>

<span data-ttu-id="4a47c-106">Bu özellik olarak uygulanan bir *çalışma zamanı Paket Deposu*, disk paketleri depolandığı bir dizin olan (genellikle en */usr/local/share/dotnet/store* macOS/Linux'ta ve *C: / Program dosyaları/dotnet/deposu* Windows üzerinde).</span><span class="sxs-lookup"><span data-stu-id="4a47c-106">This feature is implemented as a *runtime package store*, which is a directory on disk where packages are stored (typically at */usr/local/share/dotnet/store* on macOS/Linux and *C:/Program Files/dotnet/store* on Windows).</span></span> <span data-ttu-id="4a47c-107">Bu dizin altında mimarileri için alt vardır ve [hedef çerçeveyi](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="4a47c-107">Under this directory, there are subdirectories for architectures and [target frameworks](../../standard/frameworks.md).</span></span> <span data-ttu-id="4a47c-108">Dosya düzeni benzer şekilde, [NuGet varlıklar düzenlenir diskte](/nuget/create-packages/supporting-multiple-target-frameworks#framework-version-folder-structure):</span><span class="sxs-lookup"><span data-stu-id="4a47c-108">The file layout is similar to the way that [NuGet assets are laid out on disk](/nuget/create-packages/supporting-multiple-target-frameworks#framework-version-folder-structure):</span></span>

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

<span data-ttu-id="4a47c-109">A *hedef bildirimi* dosyası çalışma zamanı Paket Deposu paketleri listeler.</span><span class="sxs-lookup"><span data-stu-id="4a47c-109">A *target manifest* file lists the packages in the runtime package store.</span></span> <span data-ttu-id="4a47c-110">Geliştiriciler, uygulamaları yayımlarken bu bildirimi hedefleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4a47c-110">Developers can target this manifest when publishing their app.</span></span> <span data-ttu-id="4a47c-111">Hedef bildirimi genellikle hedeflenen üretim ortamına sahibi tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="4a47c-111">The target manifest is typically provided by the owner of the targeted production environment.</span></span>

## <a name="preparing-a-runtime-environment"></a><span data-ttu-id="4a47c-112">Bir çalışma zamanı ortamı hazırlama</span><span class="sxs-lookup"><span data-stu-id="4a47c-112">Preparing a runtime environment</span></span>

<span data-ttu-id="4a47c-113">Bir çalışma zamanı ortam Yöneticisi, bir çalışma zamanı paket deposu ve karşılık gelen hedef bildirim oluşturarak uygulamaları daha hızlı dağıtım ve daha düşük disk alanı kullanımı için iyileştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4a47c-113">The administrator of a runtime environment can optimize apps for faster deployments and lower disk space use by building a runtime package store and the corresponding target manifest.</span></span>

<span data-ttu-id="4a47c-114">İlk adım oluşturmaktır bir *Paket Deposu bildirimi* çalışma zamanı paket deposu oluşturma paketlerini listeler.</span><span class="sxs-lookup"><span data-stu-id="4a47c-114">The first step is to create a *package store manifest* that lists the packages that compose the runtime package store.</span></span> <span data-ttu-id="4a47c-115">Bu dosya biçimi, proje dosyası biçimi ile uyumlu (*csproj*).</span><span class="sxs-lookup"><span data-stu-id="4a47c-115">This file format is compatible with the project file format (*csproj*).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="<NUGET_PACKAGE>" Version="<VERSION>" />
    <!-- Include additional packages here -->
  </ItemGroup>
</Project>
```

<span data-ttu-id="4a47c-116">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="4a47c-116">**Example**</span></span>

<span data-ttu-id="4a47c-117">Aşağıdaki örnek Paket Deposu bildirimi (*packages.csproj*) eklemek için kullanılan [ `Newtonsoft.Json` ](https://www.nuget.org/packages/Newtonsoft.Json/) ve [ `Moq` ](https://www.nuget.org/packages/moq/) çalışma zamanı paket deposu için:</span><span class="sxs-lookup"><span data-stu-id="4a47c-117">The following example package store manifest (*packages.csproj*) is used to add [`Newtonsoft.Json`](https://www.nuget.org/packages/Newtonsoft.Json/) and [`Moq`](https://www.nuget.org/packages/moq/) to a runtime package store:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.3" />
    <PackageReference Include="Moq" Version="4.7.63" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="4a47c-118">Çalışma zamanı Paket Deposu yürüterek sağlama `dotnet store` Paket Deposu bildirimi, çalışma zamanı ve framework ile:</span><span class="sxs-lookup"><span data-stu-id="4a47c-118">Provision the runtime package store by executing `dotnet store` with the package store manifest, runtime, and framework:</span></span>

```console
dotnet store --manifest <PATH_TO_MANIFEST_FILE> --runtime <RUNTIME_IDENTIFIER> --framework <FRAMEWORK>
```

<span data-ttu-id="4a47c-119">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="4a47c-119">**Example**</span></span>

```console
dotnet store --manifest packages.csproj --runtime win10-x64 --framework netcoreapp2.0 --framework-version 2.0.0
```

<span data-ttu-id="4a47c-120">Tek bir birden çok hedef Paket Deposu bildirim yolları geçirebilirsiniz [ `dotnet store` ](../tools/dotnet-store.md) seçeneği ve Komut yolunda yineleyerek komutu.</span><span class="sxs-lookup"><span data-stu-id="4a47c-120">You can pass multiple target package store manifest paths to a single [`dotnet store`](../tools/dotnet-store.md) command by repeating the option and path in the command.</span></span>

<span data-ttu-id="4a47c-121">Varsayılan olarak, komut çıktısı bir paket altında deposudur *.dotnet depolama* kullanıcının profilini alt dizinidir.</span><span class="sxs-lookup"><span data-stu-id="4a47c-121">By default, the output of the command is a package store under the *.dotnet/store* subdirectory of the user's profile.</span></span> <span data-ttu-id="4a47c-122">Kullanarak farklı bir konum belirtebilirsiniz `--output <OUTPUT_DIRECTORY>` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="4a47c-122">You can specify a different location using the `--output <OUTPUT_DIRECTORY>` option.</span></span> <span data-ttu-id="4a47c-123">Depo kök dizininde içeren bir hedef bildirime *artifact.xml* dosya.</span><span class="sxs-lookup"><span data-stu-id="4a47c-123">The root directory of the store contains a target manifest *artifact.xml* file.</span></span> <span data-ttu-id="4a47c-124">Bu dosya indirme için kullanılabilir hale getirilebilir ve yayımlarken bu depo hedeflemek istediğiniz uygulama yazarları tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4a47c-124">This file can be made available for download and be used by app authors who want to target this store when publishing.</span></span>

<span data-ttu-id="4a47c-125">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="4a47c-125">**Example**</span></span>

<span data-ttu-id="4a47c-126">Aşağıdaki *artifact.xml* dosya önceki örnekteki çalıştırdıktan sonra oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="4a47c-126">The following *artifact.xml* file is produced after running the previous example.</span></span> <span data-ttu-id="4a47c-127">Unutmayın [ `Castle.Core` ](https://www.nuget.org/packages/Castle.Core/) bir bağımlılığı olduğundan `Moq`, otomatik olarak eklemiştir ve görünür *artifacts.xml* bildirim dosyası.</span><span class="sxs-lookup"><span data-stu-id="4a47c-127">Note that [`Castle.Core`](https://www.nuget.org/packages/Castle.Core/) is a dependency of `Moq`, so it's included automatically and appears in the *artifacts.xml* manifest file.</span></span>

```xml
<StoreArtifacts>
  <Package Id="Newtonsoft.Json" Version="10.0.3" />
  <Package Id="Castle.Core" Version="4.1.0" />
  <Package Id="Moq" Version="4.7.63" />
</StoreArtifacts>
```

## <a name="publishing-an-app-against-a-target-manifest"></a><span data-ttu-id="4a47c-128">Bir hedef bildirim karşı bir uygulamayı yayımlama</span><span class="sxs-lookup"><span data-stu-id="4a47c-128">Publishing an app against a target manifest</span></span>

<span data-ttu-id="4a47c-129">Diskte hedef bir bildirim dosyası varsa, dosya yolunu uygulamanızla yayımlama sırasında belirttiğiniz [ `dotnet publish` ](../tools/dotnet-publish.md) komutu:</span><span class="sxs-lookup"><span data-stu-id="4a47c-129">If you have a target manifest file on disk, you specify the path to the file when publishing your app with the [`dotnet publish`](../tools/dotnet-publish.md) command:</span></span>

```console
dotnet publish --manifest <PATH_TO_MANIFEST_FILE>
```

<span data-ttu-id="4a47c-130">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="4a47c-130">**Example**</span></span>

```console
dotnet publish --manifest manifest.xml
```

<span data-ttu-id="4a47c-131">Hedef bildiriminde açıklanan paketleri olan bir ortam elde edilen yayımlanan uygulamayı dağıtın.</span><span class="sxs-lookup"><span data-stu-id="4a47c-131">You deploy the resulting published app to an environment that has the packages described in the target manifest.</span></span> <span data-ttu-id="4a47c-132">Bunu yapmazsanız, uygulamanın başlatılması başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="4a47c-132">Failing to do so results in the app failing to start.</span></span>

<span data-ttu-id="4a47c-133">Bir uygulamayı yayımlarken seçeneği ve yolu tekrarlayarak birden fazla hedef bildirimleri belirtin (örneğin, `--manifest manifest1.xml --manifest manifest2.xml`).</span><span class="sxs-lookup"><span data-stu-id="4a47c-133">Specify multiple target manifests when publishing an app by repeating the option and path (for example, `--manifest manifest1.xml --manifest manifest2.xml`).</span></span> <span data-ttu-id="4a47c-134">Bunu yaptığınızda, uygulama paketleri komutu sağlanan hedef bildirim dosyaları belirtilen birleşimi için kırpılır.</span><span class="sxs-lookup"><span data-stu-id="4a47c-134">When you do so, the app is trimmed for the union of packages specified in the target manifest files provided to the command.</span></span>

## <a name="specifying-target-manifests-in-the-project-file"></a><span data-ttu-id="4a47c-135">Proje dosyasındaki belirten hedef bildirimleri</span><span class="sxs-lookup"><span data-stu-id="4a47c-135">Specifying target manifests in the project file</span></span>

<span data-ttu-id="4a47c-136">Hedef belirtmek için alternatif bildirimleri ile [ `dotnet publish` ](../tools/dotnet-publish.md) komutu, proje dosyasında bunları yollarda noktalı virgülle ayrılmış bir listesi olarak belirtmek için bir  **\<TargetManifestFiles >** etiketi.</span><span class="sxs-lookup"><span data-stu-id="4a47c-136">An alternative to specifying target manifests with the [`dotnet publish`](../tools/dotnet-publish.md) command is to specify them in the project file as a semicolon-separated list of paths under a **\<TargetManifestFiles>** tag.</span></span>

```xml
<PropertyGroup>
  <TargetManifestFiles>manifest1.xml;manifest2.xml</TargetManifestFiles>
</PropertyGroup>
```

<span data-ttu-id="4a47c-137">Yalnızca uygulama için hedef ortam .NET Core projeleri için iyi bilinen, gibi olduğunda proje dosyasında hedef bildirimleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="4a47c-137">Specify the target manifests in the project file only when the target environment for the app is well-known, such as for .NET Core projects.</span></span> <span data-ttu-id="4a47c-138">Bu, açık kaynak projeleri için durum geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="4a47c-138">This isn't the case for open-source projects.</span></span> <span data-ttu-id="4a47c-139">Bir açık kaynak projesi kullanıcıları genellikle farklı üretim ortamlarına dağıtın.</span><span class="sxs-lookup"><span data-stu-id="4a47c-139">The users of an open-source project typically deploy it to different production environments.</span></span> <span data-ttu-id="4a47c-140">Bu üretim ortamları genellikle farklı önceden yüklenmiş paketler vardır.</span><span class="sxs-lookup"><span data-stu-id="4a47c-140">These production environments generally have different sets of packages pre-installed.</span></span> <span data-ttu-id="4a47c-141">Kullanmanız gerekir bu tür ortamlarda, hedef bildirimi hakkında varsayımlar yapamazsınız `--manifest` seçeneği [ `dotnet publish` ](../tools/dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="4a47c-141">You can't make assumptions about the target manifest in such environments, so you should use the `--manifest` option of [`dotnet publish`](../tools/dotnet-publish.md).</span></span>

## <a name="aspnet-core-implicit-store"></a><span data-ttu-id="4a47c-142">ASP.NET Core örtük deposu</span><span class="sxs-lookup"><span data-stu-id="4a47c-142">ASP.NET Core implicit store</span></span>

<span data-ttu-id="4a47c-143">ASP.NET Core örtük deposu yalnızca ASP.NET Core 2.0 için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4a47c-143">The ASP.NET Core implicit store applies only to ASP.NET Core 2.0.</span></span> <span data-ttu-id="4a47c-144">Uygulamaları kullanan mu, ASP.NET Core 2.1 ve üzeri, öneririz **değil** örtük deposu kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a47c-144">We strongly recommend applications use ASP.NET Core 2.1 and later, which does **not** use the implicit store.</span></span> <span data-ttu-id="4a47c-145">ASP.NET Core 2.1 ve üzeri, paylaşılan çerçeve kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a47c-145">ASP.NET Core 2.1 and later use the shared framework.</span></span>

<span data-ttu-id="4a47c-146">Uygulama olarak dağıtıldığında çalışma zamanı Paket Deposu özelliği örtük olarak bir ASP.NET Core uygulaması tarafından kullanılan bir [framework bağımlı dağıtım (FDD)](index.md#framework-dependent-deployments-fdd) uygulama.</span><span class="sxs-lookup"><span data-stu-id="4a47c-146">The runtime package store feature is used implicitly by an ASP.NET Core app when the app is deployed as a [framework-dependent deployment (FDD)](index.md#framework-dependent-deployments-fdd) app.</span></span> <span data-ttu-id="4a47c-147">Hedeflerin [ `Microsoft.NET.Sdk.Web` ](https://github.com/aspnet/websdk) örtük Paket Deposu hedef sistemde başvuran bildirimleri içerir.</span><span class="sxs-lookup"><span data-stu-id="4a47c-147">The targets in [`Microsoft.NET.Sdk.Web`](https://github.com/aspnet/websdk) include manifests referencing the implicit package store on the target system.</span></span> <span data-ttu-id="4a47c-148">Ayrıca, bağlı olduğu tüm FDD uygulama `Microsoft.AspNetCore.All` paket uygulama ve varlıklarını ve listelenen paketleri içeren bir yayımlanan uygulama sonuçları `Microsoft.AspNetCore.All` metapackage.</span><span class="sxs-lookup"><span data-stu-id="4a47c-148">Additionally, any FDD app that depends on the `Microsoft.AspNetCore.All` package results in a published app that contains only the app and its assets and not the packages listed in the `Microsoft.AspNetCore.All` metapackage.</span></span> <span data-ttu-id="4a47c-149">Bu paketleri hedef sistemde mevcut olduğundan emin varsayılır.</span><span class="sxs-lookup"><span data-stu-id="4a47c-149">It's assumed that those packages are present on the target system.</span></span>

<span data-ttu-id="4a47c-150">.NET Core SDK'sı yüklü çalışma zamanı Paket Deposu konakta yüklenir.</span><span class="sxs-lookup"><span data-stu-id="4a47c-150">The runtime package store is installed on the host when the .NET Core SDK is installed.</span></span> <span data-ttu-id="4a47c-151">Diğer yükleyiciler .NET Core SDK'ın Zip/tarball yüklemeleri dahil olmak üzere çalışma zamanı Paket Deposu sağlayabilir `apt-get`, Red Hat Yum paket .NET Core Windows Server barındırma ve el ile çalışma zamanı Paket Deposu yüklemeleri.</span><span class="sxs-lookup"><span data-stu-id="4a47c-151">Other installers may provide the runtime package store, including Zip/tarball installations of the .NET Core SDK, `apt-get`, Red Hat Yum, the .NET Core Windows Server Hosting bundle, and manual runtime package store installations.</span></span>

<span data-ttu-id="4a47c-152">Dağıtım yaparken bir [framework bağımlı dağıtım (FDD)](index.md#framework-dependent-deployments-fdd) uygulama, hedef ortam .NET Core SDK yüklü olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="4a47c-152">When deploying a [framework-dependent deployment (FDD)](index.md#framework-dependent-deployments-fdd) app, make sure that the target environment has the .NET Core SDK installed.</span></span> <span data-ttu-id="4a47c-153">Uygulama ASP.NET Core içermeyen bir ortama dağıtılırsa belirterek örtük deponun dışında seçebilirsiniz  **\<PublishWithAspNetCoreTargetManifest >** kümesine `false` olarak proje dosyasındaki Aşağıdaki örnekte:</span><span class="sxs-lookup"><span data-stu-id="4a47c-153">If the app is deployed to an environment that doesn't include ASP.NET Core, you can opt out of the implicit store by specifying  **\<PublishWithAspNetCoreTargetManifest>** set to `false` in the project file as in the following example:</span></span>

```xml
<PropertyGroup>
  <PublishWithAspNetCoreTargetManifest>false</PublishWithAspNetCoreTargetManifest>
</PropertyGroup>
```

> [!NOTE]
> <span data-ttu-id="4a47c-154">İçin [müstakil dağıtım (SCD)](index.md#self-contained-deployments-scd) uygulamaları, hedef sistem bildirim gerekli paketleri mutlaka içermiyor varsayılır.</span><span class="sxs-lookup"><span data-stu-id="4a47c-154">For [self-contained deployment (SCD)](index.md#self-contained-deployments-scd) apps, it's assumed that the target system doesn't necessarily contain the required manifest packages.</span></span> <span data-ttu-id="4a47c-155">Bu nedenle,  **\<PublishWithAspNetCoreTargetManifest >** ayarlanamıyor `true` SCD uygulama.</span><span class="sxs-lookup"><span data-stu-id="4a47c-155">Therefore, **\<PublishWithAspNetCoreTargetManifest>** cannot be set to `true` for an SCD app.</span></span>

<span data-ttu-id="4a47c-156">Uygulamanın dağıtımda mevcut olan bildirim bağımlılığı dağıtırsanız (mevcut bir derlemedir *bin* klasör), çalışma zamanı Paket Deposu *kullanılmayan* o derleme için ana bilgisayarda.</span><span class="sxs-lookup"><span data-stu-id="4a47c-156">If you deploy an application with a manifest dependency that's present in the deployment (the assembly is present in the *bin* folder), the runtime package store *isn't used* on the host for that assembly.</span></span> <span data-ttu-id="4a47c-157">*Bin* klasör derleme bakılmaksızın, konaktaki çalışma zamanı Paket Deposu bulunması kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4a47c-157">The *bin* folder assembly is used regardless of its presence in the runtime package store on the host.</span></span>

<span data-ttu-id="4a47c-158">Bildirimde belirtilen bağımlılık sürümü, çalışma zamanı Paket Deposu bağımlılığı sürümünü eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="4a47c-158">The version of the dependency indicated in the manifest must match the version of the dependency in the runtime package store.</span></span> <span data-ttu-id="4a47c-159">Hedef bildirimde bağımlılık arasında sürüm uyuşmazlığı varsa ve çalışma zamanı paket deposu ve uygulama içinde bulunan sürüm gerekli Paket sürümü, dağıtımda içermez, uygulamayı başlatmak başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="4a47c-159">If you have a version mismatch between the dependency in the target manifest and the version that exists in the runtime package store and the app doesn't include the required version of the package in its deployment, the app fails to start.</span></span> <span data-ttu-id="4a47c-160">Özel durum uyuşmazlığı gidermenize yardımcı olur çalışma zamanı Paket Deposu derleme için adlı hedef bildirim adını içerir.</span><span class="sxs-lookup"><span data-stu-id="4a47c-160">The exception includes the name of the target manifest that called for the runtime package store assembly, which helps you troubleshoot the mismatch.</span></span>

<span data-ttu-id="4a47c-161">Bir dağıtım olduğunda *kırpılmış* yayımlama sırasında belirttiğiniz bildirim paketler yalnızca belirli sürümlerini yayımlanmış çıktısı uğratılan.</span><span class="sxs-lookup"><span data-stu-id="4a47c-161">When the deployment is *trimmed* on publish, only the specific versions of the manifest packages you indicate are withheld from the published output.</span></span> <span data-ttu-id="4a47c-162">Belirtilen sürümleri, paketleri başlatmak için uygulama için ana bilgisayarda bulunması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4a47c-162">The packages at the versions indicated must be present on the host for the app to start.</span></span>

## <a name="see-also"></a><span data-ttu-id="4a47c-163">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4a47c-163">See also</span></span>

* [<span data-ttu-id="4a47c-164">DotNet-yayımlama</span><span class="sxs-lookup"><span data-stu-id="4a47c-164">dotnet-publish</span></span>](../tools/dotnet-publish.md)  
* [<span data-ttu-id="4a47c-165">DotNet-store</span><span class="sxs-lookup"><span data-stu-id="4a47c-165">dotnet-store</span></span>](../tools/dotnet-store.md)  
