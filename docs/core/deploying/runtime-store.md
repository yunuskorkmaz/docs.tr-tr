---
title: Çalışma zamanı paket deposu
description: .NET Core tarafından kullanılan bildirimleri hedeflemek için çalışma zamanı paket deposunu nasıl kullanacağınızı öğrenin.
ms.date: 08/12/2017
ms.openlocfilehash: 4395370c3bb2d97511d549a63813022fb8cac4b7
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158300"
---
# <a name="runtime-package-store"></a><span data-ttu-id="5201e-103">Çalışma zamanı paket deposu</span><span class="sxs-lookup"><span data-stu-id="5201e-103">Runtime package store</span></span>

<span data-ttu-id="5201e-104">.NET Core 2,0 ' den itibaren, uygulamaları paketleyebilir ve hedef ortamda mevcut olan bilinen bir paket kümesine dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5201e-104">Starting with .NET Core 2.0, it's possible to package and deploy apps against a known set of packages that exist in the target environment.</span></span> <span data-ttu-id="5201e-105">Avantajlar, bazı durumlarda daha hızlı dağıtımlar, daha düşük disk alanı kullanımı ve geliştirilmiş başlangıç performanslarıdır.</span><span class="sxs-lookup"><span data-stu-id="5201e-105">The benefits are faster deployments, lower disk space usage, and improved startup performance in some cases.</span></span>

<span data-ttu-id="5201e-106">Bu özellik, paketlerin depolandığı disk üzerindeki bir dizin olan bir *çalışma zamanı paket deposu*olarak uygulanır (genellikle MacOS/Linux ve *C:/Program Files/Windows üzerinde/Program Files/DotNet/Store* *üzerinde/*</span><span class="sxs-lookup"><span data-stu-id="5201e-106">This feature is implemented as a *runtime package store*, which is a directory on disk where packages are stored (typically at */usr/local/share/dotnet/store* on macOS/Linux and *C:/Program Files/dotnet/store* on Windows).</span></span> <span data-ttu-id="5201e-107">Bu dizin altında mimariler ve [hedef çerçeveler](../../standard/frameworks.md)için alt dizinler vardır.</span><span class="sxs-lookup"><span data-stu-id="5201e-107">Under this directory, there are subdirectories for architectures and [target frameworks](../../standard/frameworks.md).</span></span> <span data-ttu-id="5201e-108">Dosya düzeni, [NuGet varlıklarının diskte düzenlendiği](/nuget/create-packages/supporting-multiple-target-frameworks#framework-version-folder-structure)yönteme benzer:</span><span class="sxs-lookup"><span data-stu-id="5201e-108">The file layout is similar to the way that [NuGet assets are laid out on disk](/nuget/create-packages/supporting-multiple-target-frameworks#framework-version-folder-structure):</span></span>

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

<span data-ttu-id="5201e-109">Bir *hedef bildirim* dosyası, çalışma zamanı paket deposundaki paketleri listeler.</span><span class="sxs-lookup"><span data-stu-id="5201e-109">A *target manifest* file lists the packages in the runtime package store.</span></span> <span data-ttu-id="5201e-110">Geliştiriciler, uygulamasını yayımlarken bu bildirimi hedefleyebilir.</span><span class="sxs-lookup"><span data-stu-id="5201e-110">Developers can target this manifest when publishing their app.</span></span> <span data-ttu-id="5201e-111">Hedef bildirim genellikle hedeflenen üretim ortamının sahibi tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="5201e-111">The target manifest is typically provided by the owner of the targeted production environment.</span></span>

## <a name="preparing-a-runtime-environment"></a><span data-ttu-id="5201e-112">Çalışma zamanı ortamı hazırlama</span><span class="sxs-lookup"><span data-stu-id="5201e-112">Preparing a runtime environment</span></span>

<span data-ttu-id="5201e-113">Bir çalışma zamanı ortamının Yöneticisi, bir çalışma zamanı paket deposu ve ilgili hedef bildirimi oluşturarak daha hızlı dağıtımlar ve daha düşük disk alanı kullanımı için uygulamaları iyileştirebilirler.</span><span class="sxs-lookup"><span data-stu-id="5201e-113">The administrator of a runtime environment can optimize apps for faster deployments and lower disk space use by building a runtime package store and the corresponding target manifest.</span></span>

<span data-ttu-id="5201e-114">İlk adım, çalışma zamanı paket deposunu oluşturan paketleri listeleyen bir *paket deposu bildirimi* oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="5201e-114">The first step is to create a *package store manifest* that lists the packages that compose the runtime package store.</span></span> <span data-ttu-id="5201e-115">Bu dosya biçimi, proje dosyası biçimi (*csproj*) ile uyumludur.</span><span class="sxs-lookup"><span data-stu-id="5201e-115">This file format is compatible with the project file format (*csproj*).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="NUGET_PACKAGE" Version="VERSION" />
    <!-- Include additional packages here -->
  </ItemGroup>
</Project>
```

<span data-ttu-id="5201e-116">**Örneğinde**</span><span class="sxs-lookup"><span data-stu-id="5201e-116">**Example**</span></span>

<span data-ttu-id="5201e-117">Aşağıdaki örnek paket deposu bildirimi (*Packages. csproj*), bir çalışma zamanı paket [`Newtonsoft.Json`](https://www.nuget.org/packages/Newtonsoft.Json/) deposu [`Moq`](https://www.nuget.org/packages/moq/) eklemek için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="5201e-117">The following example package store manifest (*packages.csproj*) is used to add [`Newtonsoft.Json`](https://www.nuget.org/packages/Newtonsoft.Json/) and [`Moq`](https://www.nuget.org/packages/moq/) to a runtime package store:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.3" />
    <PackageReference Include="Moq" Version="4.7.63" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="5201e-118">Paket deposu bildirimi, çalışma zamanı ve `dotnet store` Framework ile yürüterek çalışma zamanı paket deposunu sağlayın:</span><span class="sxs-lookup"><span data-stu-id="5201e-118">Provision the runtime package store by executing `dotnet store` with the package store manifest, runtime, and framework:</span></span>

```dotnetcli
dotnet store --manifest <PATH_TO_MANIFEST_FILE> --runtime <RUNTIME_IDENTIFIER> --framework <FRAMEWORK>
```

<span data-ttu-id="5201e-119">**Örneğinde**</span><span class="sxs-lookup"><span data-stu-id="5201e-119">**Example**</span></span>

```dotnetcli
dotnet store --manifest packages.csproj --runtime win10-x64 --framework netcoreapp2.0 --framework-version 2.0.0
```

<span data-ttu-id="5201e-120">Komutta seçeneğini ve yolunu yineleyerek tek [`dotnet store`](../tools/dotnet-store.md) bir komuta birden çok hedef paket deposu bildirim yolu geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5201e-120">You can pass multiple target package store manifest paths to a single [`dotnet store`](../tools/dotnet-store.md) command by repeating the option and path in the command.</span></span>

<span data-ttu-id="5201e-121">Varsayılan olarak, komutun çıktısı Kullanıcı profilinin *. DotNet/Store* alt dizininin altında bulunan bir paket deposudur.</span><span class="sxs-lookup"><span data-stu-id="5201e-121">By default, the output of the command is a package store under the *.dotnet/store* subdirectory of the user's profile.</span></span> <span data-ttu-id="5201e-122">`--output <OUTPUT_DIRECTORY>` Seçeneğini kullanarak farklı bir konum belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5201e-122">You can specify a different location using the `--output <OUTPUT_DIRECTORY>` option.</span></span> <span data-ttu-id="5201e-123">Deponun kök dizini bir hedef bildirim *yapıtı. xml* dosyası içeriyor.</span><span class="sxs-lookup"><span data-stu-id="5201e-123">The root directory of the store contains a target manifest *artifact.xml* file.</span></span> <span data-ttu-id="5201e-124">Bu dosya indirilmek üzere kullanılabilir hale getirilebilir ve yayımlarken bu depoyu hedeflemek isteyen uygulama yazarları tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5201e-124">This file can be made available for download and be used by app authors who want to target this store when publishing.</span></span>

<span data-ttu-id="5201e-125">**Örneğinde**</span><span class="sxs-lookup"><span data-stu-id="5201e-125">**Example**</span></span>

<span data-ttu-id="5201e-126">Önceki örnek çalıştırıldıktan sonra aşağıdaki *yapıt. xml* dosyası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5201e-126">The following *artifact.xml* file is produced after running the previous example.</span></span> <span data-ttu-id="5201e-127">Uygulamasının bağımlılığı olduğunu, bu nedenle otomatik olarak dahil edildiğini ve *yapılar. xml* bildirim dosyasında göründüğünü unutmayın. `Moq` [`Castle.Core`](https://www.nuget.org/packages/Castle.Core/)</span><span class="sxs-lookup"><span data-stu-id="5201e-127">Note that [`Castle.Core`](https://www.nuget.org/packages/Castle.Core/) is a dependency of `Moq`, so it's included automatically and appears in the *artifacts.xml* manifest file.</span></span>

```xml
<StoreArtifacts>
  <Package Id="Newtonsoft.Json" Version="10.0.3" />
  <Package Id="Castle.Core" Version="4.1.0" />
  <Package Id="Moq" Version="4.7.63" />
</StoreArtifacts>
```

## <a name="publishing-an-app-against-a-target-manifest"></a><span data-ttu-id="5201e-128">Hedef bildiriminde uygulama yayımlama</span><span class="sxs-lookup"><span data-stu-id="5201e-128">Publishing an app against a target manifest</span></span>

<span data-ttu-id="5201e-129">Diskte bir hedef bildirim dosyanız varsa, şu [`dotnet publish`](../tools/dotnet-publish.md) komutla uygulamanızı yayımlarken dosyanın yolunu belirtirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5201e-129">If you have a target manifest file on disk, you specify the path to the file when publishing your app with the [`dotnet publish`](../tools/dotnet-publish.md) command:</span></span>

```dotnetcli
dotnet publish --manifest <PATH_TO_MANIFEST_FILE>
```

<span data-ttu-id="5201e-130">**Örneğinde**</span><span class="sxs-lookup"><span data-stu-id="5201e-130">**Example**</span></span>

```dotnetcli
dotnet publish --manifest manifest.xml
```

<span data-ttu-id="5201e-131">Ortaya çıkan yayımlanmış uygulamayı, hedef bildiriminde tanımlanan paketlere sahip bir ortama dağıtırsınız.</span><span class="sxs-lookup"><span data-stu-id="5201e-131">You deploy the resulting published app to an environment that has the packages described in the target manifest.</span></span> <span data-ttu-id="5201e-132">Bunun başarısız olması, uygulamanın başlamamasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="5201e-132">Failing to do so results in the app failing to start.</span></span>

<span data-ttu-id="5201e-133">Bir uygulamayı yayımlarken, seçeneğini ve yolunu yineleyerek birden çok hedef bildirimi belirtin (örneğin, `--manifest manifest1.xml --manifest manifest2.xml`).</span><span class="sxs-lookup"><span data-stu-id="5201e-133">Specify multiple target manifests when publishing an app by repeating the option and path (for example, `--manifest manifest1.xml --manifest manifest2.xml`).</span></span> <span data-ttu-id="5201e-134">Bunu yaptığınızda, uygulama, komuta sunulan hedef bildirim dosyalarında belirtilen paketlerin birleşimi için kırpılır.</span><span class="sxs-lookup"><span data-stu-id="5201e-134">When you do so, the app is trimmed for the union of packages specified in the target manifest files provided to the command.</span></span>

<span data-ttu-id="5201e-135">Dağıtımda mevcut olan bir bildirim bağımlılığıyla bir uygulama dağıtırsanız (derleme *bin* klasöründe bulunur), çalışma zamanı paket deposu bu derleme için konakta *kullanılmaz* .</span><span class="sxs-lookup"><span data-stu-id="5201e-135">If you deploy an application with a manifest dependency that's present in the deployment (the assembly is present in the *bin* folder), the runtime package store *isn't used* on the host for that assembly.</span></span> <span data-ttu-id="5201e-136">*Bin* klasörü derlemesi, konaktaki çalışma zamanı paket deposundaki varlığına bakılmaksızın kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5201e-136">The *bin* folder assembly is used regardless of its presence in the runtime package store on the host.</span></span>

<span data-ttu-id="5201e-137">Bildirimde belirtilen bağımlılığın sürümü, çalışma zamanı paket deposundaki bağımlılığın sürümüyle eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="5201e-137">The version of the dependency indicated in the manifest must match the version of the dependency in the runtime package store.</span></span> <span data-ttu-id="5201e-138">Hedef bildirimde bağımlılık ile çalışma zamanı paket deposunda bulunan sürüm arasında bir sürüm uyumsuzluğu varsa ve uygulama, dağıtımda paketin gerekli sürümünü içermiyorsa, uygulama başlatılamaz.</span><span class="sxs-lookup"><span data-stu-id="5201e-138">If you have a version mismatch between the dependency in the target manifest and the version that exists in the runtime package store and the app doesn't include the required version of the package in its deployment, the app fails to start.</span></span> <span data-ttu-id="5201e-139">Özel durum, uyuşmazlığın giderilmesine yardımcı olan çalışma zamanı paket deposu derlemesi için çağıran hedef bildirimin adını içerir.</span><span class="sxs-lookup"><span data-stu-id="5201e-139">The exception includes the name of the target manifest that called for the runtime package store assembly, which helps you troubleshoot the mismatch.</span></span>

<span data-ttu-id="5201e-140">Dağıtım yayımlandığında *kırpıldıysa* , yalnızca belirttiğiniz bildirim paketlerinin belirli sürümleri, yayımlanan çıktıdan alınır.</span><span class="sxs-lookup"><span data-stu-id="5201e-140">When the deployment is *trimmed* on publish, only the specific versions of the manifest packages you indicate are withheld from the published output.</span></span> <span data-ttu-id="5201e-141">Uygulamanın başlaması için belirtilen sürümlerdeki paketlerin konakta mevcut olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5201e-141">The packages at the versions indicated must be present on the host for the app to start.</span></span>

## <a name="specifying-target-manifests-in-the-project-file"></a><span data-ttu-id="5201e-142">Proje dosyasında hedef bildirimleri belirtme</span><span class="sxs-lookup"><span data-stu-id="5201e-142">Specifying target manifests in the project file</span></span>

<span data-ttu-id="5201e-143">[`dotnet publish`](../tools/dotnet-publish.md) Komut ile hedef bildirimleri belirtmenin bir alternatifi, bunları proje dosyasında bir \*\* \<targetmanifestfiles>\*\* etiketi altındaki noktalı virgülle ayrılmış bir yol listesi olarak belirtmektir.</span><span class="sxs-lookup"><span data-stu-id="5201e-143">An alternative to specifying target manifests with the [`dotnet publish`](../tools/dotnet-publish.md) command is to specify them in the project file as a semicolon-separated list of paths under a **\<TargetManifestFiles>** tag.</span></span>

```xml
<PropertyGroup>
  <TargetManifestFiles>manifest1.xml;manifest2.xml</TargetManifestFiles>
</PropertyGroup>
```

<span data-ttu-id="5201e-144">Yalnızca uygulamanın hedef ortamı, .NET Core projeleri için gibi iyi bilindiğinde, hedef bildirimleri proje dosyasında belirtin.</span><span class="sxs-lookup"><span data-stu-id="5201e-144">Specify the target manifests in the project file only when the target environment for the app is well-known, such as for .NET Core projects.</span></span> <span data-ttu-id="5201e-145">Bu, açık kaynaklı projelerde bu durum değildir.</span><span class="sxs-lookup"><span data-stu-id="5201e-145">This isn't the case for open-source projects.</span></span> <span data-ttu-id="5201e-146">Açık kaynaklı bir projenin kullanıcıları genellikle farklı üretim ortamlarına dağıtır.</span><span class="sxs-lookup"><span data-stu-id="5201e-146">The users of an open-source project typically deploy it to different production environments.</span></span> <span data-ttu-id="5201e-147">Bu üretim ortamları genellikle önceden yüklenmiş farklı paket kümelerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="5201e-147">These production environments generally have different sets of packages pre-installed.</span></span> <span data-ttu-id="5201e-148">Bu tür ortamlarda hedef bildirimle ilgili varsayımlar yapamazsınız, bu nedenle `--manifest` seçeneğini kullanmanız gerekir. [`dotnet publish`](../tools/dotnet-publish.md)</span><span class="sxs-lookup"><span data-stu-id="5201e-148">You can't make assumptions about the target manifest in such environments, so you should use the `--manifest` option of [`dotnet publish`](../tools/dotnet-publish.md).</span></span>

## <a name="aspnet-core-implicit-store-net-core-20-only"></a><span data-ttu-id="5201e-149">ASP.NET Core örtük depo (yalnızca .NET Core 2,0)</span><span class="sxs-lookup"><span data-stu-id="5201e-149">ASP.NET Core implicit store (.NET Core 2.0 only)</span></span>

<span data-ttu-id="5201e-150">ASP.NET Core örtük depo yalnızca ASP.NET Core 2,0 için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5201e-150">The ASP.NET Core implicit store applies only to ASP.NET Core 2.0.</span></span> <span data-ttu-id="5201e-151">Uygulamaların, örtük mağazayı kullanmayan ASP.NET Core 2,1 ve **üstünü kullanmasını önemle** öneririz.</span><span class="sxs-lookup"><span data-stu-id="5201e-151">We strongly recommend applications use ASP.NET Core 2.1 and later, which does **not** use the implicit store.</span></span> <span data-ttu-id="5201e-152">ASP.NET Core 2,1 ve üzeri, paylaşılan çerçeveyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="5201e-152">ASP.NET Core 2.1 and later use the shared framework.</span></span>

<span data-ttu-id="5201e-153">.NET Core 2,0 için, uygulama [çalışma zamanına bağımlı bir dağıtım](index.md#publish-runtime-dependent) uygulaması olarak dağıtıldığında, çalışma zamanı paket deposu özelliği örtük olarak bir ASP.NET Core uygulaması tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5201e-153">For .NET Core 2.0, the runtime package store feature is used implicitly by an ASP.NET Core app when the app is deployed as a [runtime-dependent deployment](index.md#publish-runtime-dependent) app.</span></span> <span data-ttu-id="5201e-154">İçindeki [`Microsoft.NET.Sdk.Web`](https://github.com/aspnet/websdk) hedefler, hedef sistemdeki örtük paket deposuna başvuran bildirimleri içerir.</span><span class="sxs-lookup"><span data-stu-id="5201e-154">The targets in [`Microsoft.NET.Sdk.Web`](https://github.com/aspnet/websdk) include manifests referencing the implicit package store on the target system.</span></span> <span data-ttu-id="5201e-155">Ayrıca, `Microsoft.AspNetCore.All` pakete bağlı olan tüm çalışma zamanına bağımlı uygulamalar, `Microsoft.AspNetCore.All` metapackage 'de listelenen paketleri değil, yalnızca uygulamayı ve varlıklarını içeren yayımlanmış bir uygulamayla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="5201e-155">Additionally, any runtime-dependent app that depends on the `Microsoft.AspNetCore.All` package results in a published app that contains only the app and its assets and not the packages listed in the `Microsoft.AspNetCore.All` metapackage.</span></span> <span data-ttu-id="5201e-156">Bu paketlerin hedef sistemde bulunduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="5201e-156">It's assumed that those packages are present on the target system.</span></span>

<span data-ttu-id="5201e-157">Çalışma zamanı paket deposu, .NET Core SDK yüklendiği zaman konağa yüklenir.</span><span class="sxs-lookup"><span data-stu-id="5201e-157">The runtime package store is installed on the host when the .NET Core SDK is installed.</span></span> <span data-ttu-id="5201e-158">Diğer yükleyiciler, .NET Core SDK `apt-get`ZIP/tarbol yüklemeleri, Red Hat yıum, .NET Core Windows Server barındırma paketi ve el ile çalışma zamanı paket deposu yüklemeleri de dahil olmak üzere çalışma zamanı paket deposunu sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="5201e-158">Other installers may provide the runtime package store, including Zip/tarball installations of the .NET Core SDK, `apt-get`, Red Hat Yum, the .NET Core Windows Server Hosting bundle, and manual runtime package store installations.</span></span>

<span data-ttu-id="5201e-159">[Çalışma zamanına bağımlı dağıtım](index.md#publish-runtime-dependent) uygulaması dağıttığınızda, hedef ortamda .NET Core SDK yüklü olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="5201e-159">When deploying a [runtime-dependent deployment](index.md#publish-runtime-dependent) app, make sure that the target environment has the .NET Core SDK installed.</span></span> <span data-ttu-id="5201e-160">Uygulama ASP.NET Core içermeyen bir ortama dağıtılırsa, aşağıdaki örnekte olduğu gibi \*\* \<publishwithaspnetcoretargetmanifest>\*\* öğesini proje dosyasında olarak ayarlanmış şekilde `false` belirterek örtük depoyu devre dışı bırakabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5201e-160">If the app is deployed to an environment that doesn't include ASP.NET Core, you can opt out of the implicit store by specifying  **\<PublishWithAspNetCoreTargetManifest>** set to `false` in the project file as in the following example:</span></span>

```xml
<PropertyGroup>
  <PublishWithAspNetCoreTargetManifest>false</PublishWithAspNetCoreTargetManifest>
</PropertyGroup>
```

> [!NOTE]
> <span data-ttu-id="5201e-161">[Kendi kendine kapsanan dağıtım](index.md#publish-self-contained) uygulamaları için, hedef sistemin gerekli bildirim paketlerini içermesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="5201e-161">For [self-contained deployment](index.md#publish-self-contained) apps, it's assumed that the target system doesn't necessarily contain the required manifest packages.</span></span> <span data-ttu-id="5201e-162">Bu nedenle, \*\* \<publishwithaspnetcoretargetmanifest>\*\* , kendi içinde `true` bulunan bir uygulama için olarak ayarlanamaz.</span><span class="sxs-lookup"><span data-stu-id="5201e-162">Therefore, **\<PublishWithAspNetCoreTargetManifest>** cannot be set to `true` for an self-contained app.</span></span>

## <a name="see-also"></a><span data-ttu-id="5201e-163">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5201e-163">See also</span></span>

- [<span data-ttu-id="5201e-164">DotNet-Yayımla</span><span class="sxs-lookup"><span data-stu-id="5201e-164">dotnet-publish</span></span>](../tools/dotnet-publish.md)
- [<span data-ttu-id="5201e-165">DotNet-mağaza</span><span class="sxs-lookup"><span data-stu-id="5201e-165">dotnet-store</span></span>](../tools/dotnet-store.md)
