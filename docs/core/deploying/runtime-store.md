---
title: "Çalışma zamanı Paket Deposu"
description: "Bu konuda çalışma zamanı paket deposu ve hedef bildirimleri .NET Core tarafından kullanılan açıklanmaktadır."
keywords: ".NET, .NET core dotnet deposu, çalışma zamanı Paket Deposu"
author: bleroy
ms.author: mairaw
ms.date: 08/12/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 9521d8b4-25fc-412b-a65b-4c975ebf6bfd
ms.workload: dotnetcore
ms.openlocfilehash: de1aa4d29abae6bc6c26c0686bafe9bd9cc10ee1
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="runtime-package-store"></a><span data-ttu-id="4bb89-104">Çalışma zamanı Paket Deposu</span><span class="sxs-lookup"><span data-stu-id="4bb89-104">Runtime package store</span></span>

<span data-ttu-id="4bb89-105">.NET Core 2.0 ile başlayarak, paket ve hedef ortamda mevcut paketleri bilinen bir dizi uygulamaları dağıtmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="4bb89-105">Starting with .NET Core 2.0, it's possible to package and deploy apps against a known set of packages that exist in the target environment.</span></span> <span data-ttu-id="4bb89-106">Daha hızlı dağıtımlar, daha düşük disk alanı kullanımını ve bazı durumlarda geliştirilmiş başlangıç performans yararlar şunlardır.</span><span class="sxs-lookup"><span data-stu-id="4bb89-106">The benefits are faster deployments, lower disk space use, and improved startup performance in some cases.</span></span>

<span data-ttu-id="4bb89-107">Bu özellik olarak uygulanan bir *çalışma zamanı Paket Deposu*, paketleri depolandığı disk üzerindeki bir dizin olduğu (genellikle en */usr/local/share/dotnet/store* macOS/Linux üzerinde ve *C: / Program dosyaları/dotnet/deposu* Windows'da).</span><span class="sxs-lookup"><span data-stu-id="4bb89-107">This feature is implemented as a *runtime package store*, which is a directory on disk where packages are stored (typically at */usr/local/share/dotnet/store* on macOS/Linux and *C:/Program Files/dotnet/store* on Windows).</span></span> <span data-ttu-id="4bb89-108">Bu dizin altında mimarileri için alt dizinler vardır ve [hedef çerçeveler](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="4bb89-108">Under this directory, there are subdirectories for architectures and [target frameworks](../../standard/frameworks.md).</span></span> <span data-ttu-id="4bb89-109">Dosya düzeni benzer şekilde, [NuGet varlıklar düzenlenir diskte](/nuget/create-packages/supporting-multiple-target-frameworks#framework-version-folder-structure):</span><span class="sxs-lookup"><span data-stu-id="4bb89-109">The file layout is similar to the way that [NuGet assets are laid out on disk](/nuget/create-packages/supporting-multiple-target-frameworks#framework-version-folder-structure):</span></span>

<span data-ttu-id="4bb89-110">\dotnet</span><span class="sxs-lookup"><span data-stu-id="4bb89-110">\dotnet</span></span>   
<span data-ttu-id="4bb89-111">&nbsp;&nbsp;\store</span><span class="sxs-lookup"><span data-stu-id="4bb89-111">&nbsp;&nbsp;\store</span></span>   
<span data-ttu-id="4bb89-112">&nbsp;&nbsp;&nbsp;&nbsp;\x64</span><span class="sxs-lookup"><span data-stu-id="4bb89-112">&nbsp;&nbsp;&nbsp;&nbsp;\x64</span></span>   
<span data-ttu-id="4bb89-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\netcoreapp2.0</span><span class="sxs-lookup"><span data-stu-id="4bb89-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\netcoreapp2.0</span></span>   
<span data-ttu-id="4bb89-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\Microsoft.applicationinsights</span><span class="sxs-lookup"><span data-stu-id="4bb89-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\microsoft.applicationinsights</span></span>   
<span data-ttu-id="4bb89-115">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\Microsoft.aspnetcore</span><span class="sxs-lookup"><span data-stu-id="4bb89-115">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\microsoft.aspnetcore</span></span>   
<span data-ttu-id="4bb89-116">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;...</span><span class="sxs-lookup"><span data-stu-id="4bb89-116">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;...</span></span>   
<span data-ttu-id="4bb89-117">&nbsp;&nbsp;&nbsp;&nbsp;\x86</span><span class="sxs-lookup"><span data-stu-id="4bb89-117">&nbsp;&nbsp;&nbsp;&nbsp;\x86</span></span>   
<span data-ttu-id="4bb89-118">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\netcoreapp2.0</span><span class="sxs-lookup"><span data-stu-id="4bb89-118">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\netcoreapp2.0</span></span>   
<span data-ttu-id="4bb89-119">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\Microsoft.applicationinsights</span><span class="sxs-lookup"><span data-stu-id="4bb89-119">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\microsoft.applicationinsights</span></span>   
<span data-ttu-id="4bb89-120">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\Microsoft.aspnetcore</span><span class="sxs-lookup"><span data-stu-id="4bb89-120">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\microsoft.aspnetcore</span></span>   
<span data-ttu-id="4bb89-121">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;...</span><span class="sxs-lookup"><span data-stu-id="4bb89-121">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;...</span></span>   

<span data-ttu-id="4bb89-122">A *hedef bildirimi* dosya çalışma zamanı paketi deposundaki paketlerini listeler.</span><span class="sxs-lookup"><span data-stu-id="4bb89-122">A *target manifest* file lists the packages in the runtime package store.</span></span> <span data-ttu-id="4bb89-123">Geliştiriciler, kendi uygulama yayımlarken bu bildirimi hedefleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4bb89-123">Developers can target this manifest when publishing their app.</span></span> <span data-ttu-id="4bb89-124">Hedef bildirimi genellikle hedeflenen üretim ortamına sahibi tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="4bb89-124">The target manifest is typically provided by the owner of the targeted production environment.</span></span>

## <a name="preparing-a-runtime-environment"></a><span data-ttu-id="4bb89-125">Çalışma zamanı ortamı hazırlama</span><span class="sxs-lookup"><span data-stu-id="4bb89-125">Preparing a runtime environment</span></span>

<span data-ttu-id="4bb89-126">Çalışma zamanı ortamı yönetici uygulamaları daha hızlı dağıtımları ve daha düşük disk alanı kullanımı için bir çalışma zamanı paket deposu ve karşılık gelen hedef bildirimi oluşturarak en iyi duruma getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4bb89-126">The administrator of a runtime environment can optimize apps for faster deployments and lower disk space use by building a runtime package store and the corresponding target manifest.</span></span>

<span data-ttu-id="4bb89-127">İlk adım oluşturmaktır bir *Paket Deposu bildirimi* çalışma zamanı paket deposu oluşturma paketlerini listeler.</span><span class="sxs-lookup"><span data-stu-id="4bb89-127">The first step is to create a *package store manifest* that lists the packages that compose the runtime package store.</span></span> <span data-ttu-id="4bb89-128">Bu dosya biçimi proje dosyası biçimiyle uyumlu değil (*csproj*).</span><span class="sxs-lookup"><span data-stu-id="4bb89-128">This file format is compatible with the project file format (*csproj*).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="<NUGET_PACKAGE>" Version="<VERSION>" />
    <!-- Include additional packages here -->
  </ItemGroup>
</Project>
```

<span data-ttu-id="4bb89-129">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="4bb89-129">**Example**</span></span>

<span data-ttu-id="4bb89-130">Aşağıdaki örnek Paket Deposu bildirimi (*packages.csproj*) eklemek için kullanılan [ `Newtonsoft.Json` ](https://www.nuget.org/packages/Newtonsoft.Json/) ve [ `Moq` ](https://www.nuget.org/packages/moq/) bir çalışma zamanı paket deposu için:</span><span class="sxs-lookup"><span data-stu-id="4bb89-130">The following example package store manifest (*packages.csproj*) is used to add [`Newtonsoft.Json`](https://www.nuget.org/packages/Newtonsoft.Json/) and [`Moq`](https://www.nuget.org/packages/moq/) to a runtime package store:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.3" />
    <PackageReference Include="Moq" Version="4.7.63" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="4bb89-131">Çalışma zamanı Paket Deposu yürüterek sağlamak `dotnet store` Paket Deposu bildirimi, çalışma zamanı ve framework ile:</span><span class="sxs-lookup"><span data-stu-id="4bb89-131">Provision the runtime package store by executing `dotnet store` with the package store manifest, runtime, and framework:</span></span>

```console
dotnet store --manifest <PATH_TO_MANIFEST_FILE> --runtime <RUNTIME_IDENTIFIER> --framework <FRAMEWORK>
```

<span data-ttu-id="4bb89-132">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="4bb89-132">**Example**</span></span>

```console
dotnet store --manifest packages.csproj --runtime win10-x64 --framework netcoreapp2.0 --framework-version 2.0.0
```

<span data-ttu-id="4bb89-133">Tek bir birden çok hedef Paket Deposu bildirim yollarını geçirebilirsiniz [ `dotnet store` ](../tools/dotnet-store.md) yinelenen seçeneği ve Komut yolunda tarafından komutu.</span><span class="sxs-lookup"><span data-stu-id="4bb89-133">You can pass multiple target package store manifest paths to a single [`dotnet store`](../tools/dotnet-store.md) command by repeating the option and path in the command.</span></span>

<span data-ttu-id="4bb89-134">Varsayılan olarak, komut çıktısı bir paket altında deposudur *.dotnet/deposu* kullanıcının profilini alt.</span><span class="sxs-lookup"><span data-stu-id="4bb89-134">By default, the output of the command is a package store under the *.dotnet/store* subdirectory of the user's profile.</span></span> <span data-ttu-id="4bb89-135">Kullanarak farklı bir konum belirtebilirsiniz `--output <OUTPUT_DIRECTORY>` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="4bb89-135">You can specify a different location using the `--output <OUTPUT_DIRECTORY>` option.</span></span> <span data-ttu-id="4bb89-136">Depo kök dizininde içeren bir hedef bildirime *artifact.xml* dosya.</span><span class="sxs-lookup"><span data-stu-id="4bb89-136">The root directory of the store contains a target manifest *artifact.xml* file.</span></span> <span data-ttu-id="4bb89-137">Bu dosya indirme için kullanılabilir hale getirilebilir ve bu depo yayımlarken hedeflemek istediğiniz uygulama yazarlar tarafından kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="4bb89-137">This file can be made available for download and be used by app authors who want to target this store when publishing.</span></span>

<span data-ttu-id="4bb89-138">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="4bb89-138">**Example**</span></span>

<span data-ttu-id="4bb89-139">Aşağıdaki *artifact.xml* dosyası, önceki örnekte çalıştırdıktan sonra oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="4bb89-139">The following *artifact.xml* file is produced after running the previous example.</span></span> <span data-ttu-id="4bb89-140">Unutmayın [ `Castle.Core` ](https://www.nuget.org/packages/Castle.Core/) bir bağımlılığıdır `Moq`, böylece otomatik olarak eklenen ve görünür *artifacts.xml* bildirim dosyası.</span><span class="sxs-lookup"><span data-stu-id="4bb89-140">Note that [`Castle.Core`](https://www.nuget.org/packages/Castle.Core/) is a dependency of `Moq`, so it's included automatically and appears in the *artifacts.xml* manifest file.</span></span>

```xml
<StoreArtifacts>
  <Package Id="Newtonsoft.Json" Version="10.0.3" />
  <Package Id="Castle.Core" Version="4.1.0" />
  <Package Id="Moq" Version="4.7.63" />
</StoreArtifacts>
```

## <a name="publishing-an-app-against-a-target-manifest"></a><span data-ttu-id="4bb89-141">Bir hedef bildirimi karşı bir uygulama yayımlama</span><span class="sxs-lookup"><span data-stu-id="4bb89-141">Publishing an app against a target manifest</span></span>

<span data-ttu-id="4bb89-142">Diskte hedef bildirim dosyası varsa, dosyanın yolu ile uygulamanızı yayımlama sırasında belirttiğiniz [ `dotnet publish` ](../tools/dotnet-publish.md) komutu:</span><span class="sxs-lookup"><span data-stu-id="4bb89-142">If you have a target manifest file on disk, you specify the path to the file when publishing your app with the [`dotnet publish`](../tools/dotnet-publish.md) command:</span></span>

```console
dotnet publish --manifest <PATH_TO_MANIFEST_FILE>
```

<span data-ttu-id="4bb89-143">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="4bb89-143">**Example**</span></span>

```console
dotnet publish --manifest manifest.xml
```

<span data-ttu-id="4bb89-144">Hedef bildiriminde açıklanan paketleri bir ortam için sonuçta elde edilen yayımlanan uygulamayı dağıtın.</span><span class="sxs-lookup"><span data-stu-id="4bb89-144">You deploy the resulting published app to an environment that has the packages described in the target manifest.</span></span> <span data-ttu-id="4bb89-145">Bunu yapmazsanız başlatılamamasına uygulamada sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="4bb89-145">Failing to do so results in the app failing to start.</span></span>

<span data-ttu-id="4bb89-146">Bir uygulama seçeneği ve yolu tekrarlayarak yayımlarken birden çok hedef bildirimleri belirtin (örneğin, `--manifest manifest1.xml --manifest manifest2.xml`).</span><span class="sxs-lookup"><span data-stu-id="4bb89-146">Specify multiple target manifests when publishing an app by repeating the option and path (for example, `--manifest manifest1.xml --manifest manifest2.xml`).</span></span> <span data-ttu-id="4bb89-147">Bunu yaptığınızda, uygulama paketleri komutu sağlanan hedef bildirim dosyaları belirtilen birleşimi için kırpılır.</span><span class="sxs-lookup"><span data-stu-id="4bb89-147">When you do so, the app is trimmed for the union of packages specified in the target manifest files provided to the command.</span></span>

## <a name="specifying-target-manifests-in-the-project-file"></a><span data-ttu-id="4bb89-148">Proje dosyasında belirten hedef bildirimleri</span><span class="sxs-lookup"><span data-stu-id="4bb89-148">Specifying target manifests in the project file</span></span>

<span data-ttu-id="4bb89-149">Hedef belirtme alternatif bildirimleri ile [ `dotnet publish` ](../tools/dotnet-publish.md) komuttur bunları yollarının altında noktalı virgülle ayrılmış liste olarak proje dosyasında belirtmek için bir  **\<TargetManifestFiles >** etiketi.</span><span class="sxs-lookup"><span data-stu-id="4bb89-149">An alternative to specifying target manifests with the [`dotnet publish`](../tools/dotnet-publish.md) command is to specify them in the project file as a semicolon-separated list of paths under a **\<TargetManifestFiles>** tag.</span></span>

```xml
<PropertyGroup>
  <TargetManifestFiles>manifest1.xml;manifest2.xml</TargetManifestFiles>
</PropertyGroup>
```

<span data-ttu-id="4bb89-150">Yalnızca hedef ortam uygulama için .NET Core projeleri için iyi bilinen, gibi olduğunda hedef bildirimleri proje dosyası belirtin.</span><span class="sxs-lookup"><span data-stu-id="4bb89-150">Specify the target manifests in the project file only when the target environment for the app is well-known, such as for .NET Core projects.</span></span> <span data-ttu-id="4bb89-151">Bu, açık kaynaklı proje söz konusu değildir.</span><span class="sxs-lookup"><span data-stu-id="4bb89-151">This isn't the case for open-source projects.</span></span> <span data-ttu-id="4bb89-152">Bir açık kaynak projesi kullanıcıları genellikle farklı üretim ortamlarına dağıtın.</span><span class="sxs-lookup"><span data-stu-id="4bb89-152">The users of an open-source project typically deploy it to different production environments.</span></span> <span data-ttu-id="4bb89-153">Bu üretim ortamlarında genellikle önceden yüklenen paketler farklı kümelerini sahiptir.</span><span class="sxs-lookup"><span data-stu-id="4bb89-153">These production environments generally have different sets of packages pre-installed.</span></span> <span data-ttu-id="4bb89-154">Kullanmanız gereken şekilde bu tür ortamlarda varsayımlar hedef bildirimi hakkında yapamazsınız `--manifest` seçeneği [ `dotnet publish` ](../tools/dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="4bb89-154">You can't make assumptions about the target manifest in such environments, so you should use the `--manifest` option of [`dotnet publish`](../tools/dotnet-publish.md).</span></span>

## <a name="aspnet-core-implicit-store"></a><span data-ttu-id="4bb89-155">ASP.NET Core örtük deposu</span><span class="sxs-lookup"><span data-stu-id="4bb89-155">ASP.NET Core implicit store</span></span>

<span data-ttu-id="4bb89-156">Uygulama olarak dağıtıldığında çalışma zamanı paketi depolama özelliğini örtük olarak ASP.NET Core uygulama tarafından kullanılan bir [framework bağımlı dağıtım (FDD)](index.md#framework-dependent-deployments-fdd) uygulama.</span><span class="sxs-lookup"><span data-stu-id="4bb89-156">The runtime package store feature is used implicitly by an ASP.NET Core app when the app is deployed as a [framework-dependent deployment (FDD)](index.md#framework-dependent-deployments-fdd) app.</span></span> <span data-ttu-id="4bb89-157">Hedeflerin [ `Microsoft.NET.Sdk.Web` ](https://github.com/aspnet/websdk) hedef sistemde örtük Paket Deposu başvuran bildirimlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="4bb89-157">The targets in [`Microsoft.NET.Sdk.Web`](https://github.com/aspnet/websdk) include manifests referencing the implicit package store on the target system.</span></span> <span data-ttu-id="4bb89-158">Ayrıca, bağımlı herhangi FDD uygulama `Microsoft.AspNetCore.All` paketini yalnızca uygulama ve varlıklarını ve değil listelenen paketler içeren yayımlanan bir uygulamanın sonuçlarında `Microsoft.AspNetCore.All` metapackage.</span><span class="sxs-lookup"><span data-stu-id="4bb89-158">Additionally, any FDD app that depends on the `Microsoft.AspNetCore.All` package results in a published app that contains only the app and its assets and not the packages listed in the `Microsoft.AspNetCore.All` metapackage.</span></span> <span data-ttu-id="4bb89-159">Bu paketleri hedef sistemde mevcut olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="4bb89-159">It's assumed that those packages are present on the target system.</span></span>

<span data-ttu-id="4bb89-160">.NET Core SDK yüklendiğinde çalışma zamanı Paket Deposu ana bilgisayarda yüklü.</span><span class="sxs-lookup"><span data-stu-id="4bb89-160">The runtime package store is installed on the host when the .NET Core SDK is installed.</span></span> <span data-ttu-id="4bb89-161">Diğer yükleyicileri .NET Core SDK Zip/tarball yüklemeleri dahil olmak üzere çalışma zamanı Paket Deposu sağlayabilir `apt-get`, Red Hat Yum, .NET Core Windows Server barındırma paket ve el ile çalışma zamanı Paket Deposu yüklemeleri.</span><span class="sxs-lookup"><span data-stu-id="4bb89-161">Other installers may provide the runtime package store, including Zip/tarball installations of the .NET Core SDK, `apt-get`, Red Hat Yum, the .NET Core Windows Server Hosting bundle, and manual runtime package store installations.</span></span>

<span data-ttu-id="4bb89-162">Dağıtırken bir [framework bağımlı dağıtım (FDD)](index.md#framework-dependent-deployments-fdd) uygulama, hedef ortam .NET Core SDK yüklü olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="4bb89-162">When deploying a [framework-dependent deployment (FDD)](index.md#framework-dependent-deployments-fdd) app, make sure that the target environment has the .NET Core SDK installed.</span></span> <span data-ttu-id="4bb89-163">Uygulama ASP.NET Core içermeyen bir ortama dağıtılırsa belirterek dışında örtük deposu seçebilirsiniz  **\<PublishWithAspNetCoreTargetManifest >** kümesine `false` proje dosyasında olarak Aşağıdaki örnek:</span><span class="sxs-lookup"><span data-stu-id="4bb89-163">If the app is deployed to an environment that doesn't include ASP.NET Core, you can opt out of the implicit store by specifying  **\<PublishWithAspNetCoreTargetManifest>** set to `false` in the project file as in the following example:</span></span>

```xml
<PropertyGroup>
  <PublishWithAspNetCoreTargetManifest>false</PublishWithAspNetCoreTargetManifest>
</PropertyGroup>
```

> [!NOTE] 
> <span data-ttu-id="4bb89-164">İçin [müstakil dağıtım (SCD)](index.md#self-contained-deployments-scd) uygulamaları varsayılır hedef sistem gerekli bildirim paketlerini mutlaka içermiyor.</span><span class="sxs-lookup"><span data-stu-id="4bb89-164">For [self-contained deployment (SCD)](index.md#self-contained-deployments-scd) apps, it's assumed that the target system doesn't necessarily contain the required manifest packages.</span></span> <span data-ttu-id="4bb89-165">Bu nedenle,  **\<PublishWithAspNetCoreTargetManifest >** ayarlanamıyor `true` SCD uygulama.</span><span class="sxs-lookup"><span data-stu-id="4bb89-165">Therefore, **\<PublishWithAspNetCoreTargetManifest>** cannot be set to `true` for an SCD app.</span></span>

<span data-ttu-id="4bb89-166">Dağıtımda mevcut bir bildirim bağımlılık uygulamayla dağıtırsanız (derleme mevcut *bin* klasör), çalışma zamanı Paket Deposu *kullanılmaz* bu derleme için konakta.</span><span class="sxs-lookup"><span data-stu-id="4bb89-166">If you deploy an application with a manifest dependency that's present in the deployment (the assembly is present in the *bin* folder), the runtime package store *isn't used* on the host for that assembly.</span></span> <span data-ttu-id="4bb89-167">*Bin* klasörü derleme ana bilgisayarda çalışma zamanı paketi deposundaki varlığını bağımsız olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4bb89-167">The *bin* folder assembly is used regardless of its presence in the runtime package store on the host.</span></span>

<span data-ttu-id="4bb89-168">Bildiriminde belirtilen bağımlılık sürümü çalışma zamanı paketi deposundaki bağımlılık sürümü aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4bb89-168">The version of the dependency indicated in the manifest must match the version of the dependency in the runtime package store.</span></span> <span data-ttu-id="4bb89-169">Hedef bildiriminde bağımlılık arasında sürüm uyuşmazlığı varsa ve çalışma zamanı paket deposu ve uygulama mevcut sürümü, dağıtım paketi gerekli sürümü içermez, uygulamayı başlatmak başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="4bb89-169">If you have a version mismatch between the dependency in the target manifest and the version that exists in the runtime package store and the app doesn't include the required version of the package in its deployment, the app fails to start.</span></span> <span data-ttu-id="4bb89-170">Özel durum uyuşmazlığı gidermenize yardımcı çalışma zamanı Paket Deposu derleme için adlı hedef bildirim adını içerir.</span><span class="sxs-lookup"><span data-stu-id="4bb89-170">The exception includes the name of the target manifest that called for the runtime package store assembly, which helps you troubleshoot the mismatch.</span></span>

<span data-ttu-id="4bb89-171">Dağıtım olduğunda *kırpılmış* şunu yayımlanan çıkışı gösterdiğiniz bildirim paketler yalnızca belirli sürümlerini geri çekildi.</span><span class="sxs-lookup"><span data-stu-id="4bb89-171">When the deployment is *trimmed* on publish, only the specific versions of the manifest packages you indicate are withheld from the published output.</span></span> <span data-ttu-id="4bb89-172">Belirtilen sürümleri adresindeki paketleri başlatmak için uygulama için ana bilgisayarda mevcut olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4bb89-172">The packages at the versions indicated must be present on the host for the app to start.</span></span>

## <a name="see-also"></a><span data-ttu-id="4bb89-173">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4bb89-173">See also</span></span>
 [<span data-ttu-id="4bb89-174">DotNet-yayımlama</span><span class="sxs-lookup"><span data-stu-id="4bb89-174">dotnet-publish</span></span>](../tools/dotnet-publish.md)  
 [<span data-ttu-id="4bb89-175">DotNet deposu</span><span class="sxs-lookup"><span data-stu-id="4bb89-175">dotnet-store</span></span>](../tools/dotnet-store.md)  
