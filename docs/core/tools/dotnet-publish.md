---
title: DotNet command - .NET Core CLI yayımlama
description: Dotnet yayımlama komutu .NET Core projenizi bir dizine yayımlar.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 38224aa8472f99df107e523667e18892384a20b0
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34696666"
---
# <a name="dotnet-publish"></a><span data-ttu-id="2e70f-103">DotNet yayımlama</span><span class="sxs-lookup"><span data-stu-id="2e70f-103">dotnet publish</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="2e70f-104">Ad</span><span class="sxs-lookup"><span data-stu-id="2e70f-104">Name</span></span>

<span data-ttu-id="2e70f-105">`dotnet publish` -Dağıtım barındırma sistem için bir klasöre uygulamayı ve bağımlılıklarını paketler.</span><span class="sxs-lookup"><span data-stu-id="2e70f-105">`dotnet publish` - Packs the application and its dependencies into a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="2e70f-106">Özet</span><span class="sxs-lookup"><span data-stu-id="2e70f-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="2e70f-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="2e70f-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-build] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="2e70f-108">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="2e70f-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="2e70f-109">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="2e70f-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
    [--version-suffix]
dotnet publish [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="2e70f-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2e70f-110">Description</span></span>

<span data-ttu-id="2e70f-111">`dotnet publish` Uygulama derler, proje dosyasında belirtilen bağımlılıklarını aracılığıyla okur ve bir dizine dosyaları sonuç kümesini yayımlar.</span><span class="sxs-lookup"><span data-stu-id="2e70f-111">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="2e70f-112">Çıktı şu varlıkları içerir:</span><span class="sxs-lookup"><span data-stu-id="2e70f-112">The output includes the following assets:</span></span>

* <span data-ttu-id="2e70f-113">Ara dil (IL) ile bir derlemeyi kodda bir *dll* uzantısı.</span><span class="sxs-lookup"><span data-stu-id="2e70f-113">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
* <span data-ttu-id="2e70f-114">*. deps.json* tüm proje bağımlılıklarını içeren dosya.</span><span class="sxs-lookup"><span data-stu-id="2e70f-114">*.deps.json* file that includes all of the dependencies of the project.</span></span>
* <span data-ttu-id="2e70f-115">*. runtime.config.json* çalışma zamanı (örneğin, atık toplama türü) için diğer yapılandırma seçeneklerini yanı sıra uygulama bekler paylaşılan çalışma zamanı belirten dosyası.</span><span class="sxs-lookup"><span data-stu-id="2e70f-115">*.runtime.config.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
* <span data-ttu-id="2e70f-116">Uygulama bağımlılıkları, NuGet önbellekten çıkış klasörüne kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="2e70f-116">The application's dependencies, which are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="2e70f-117">`dotnet publish` Komutunun çıktısını, dağıtım için bir barındırma sistemi hazır (örneğin, bir sunucu, PC, Mac, dizüstü) yürütme için.</span><span class="sxs-lookup"><span data-stu-id="2e70f-117">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution.</span></span> <span data-ttu-id="2e70f-118">Bu uygulama dağıtım için hazırlamak için yalnızca resmi olarak desteklenen yoludur.</span><span class="sxs-lookup"><span data-stu-id="2e70f-118">It's the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="2e70f-119">Projeyi belirtir. Dağıtım türü, bağlı olarak ana bilgisayar sistemi olabilir veya .NET Core üzerinde yüklü çalışma zamanı paylaşılmayan sahip.</span><span class="sxs-lookup"><span data-stu-id="2e70f-119">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span> <span data-ttu-id="2e70f-120">Daha fazla bilgi için bkz: [.NET Core uygulama dağıtımı](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="2e70f-120">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span> <span data-ttu-id="2e70f-121">Yayımlanmış bir uygulama dizin yapısı için bkz: [dizin yapısını](/aspnet/core/hosting/directory-structure).</span><span class="sxs-lookup"><span data-stu-id="2e70f-121">For the directory structure of a published application, see [Directory structure](/aspnet/core/hosting/directory-structure).</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="2e70f-122">Arguments</span><span class="sxs-lookup"><span data-stu-id="2e70f-122">Arguments</span></span>

`PROJECT`

<span data-ttu-id="2e70f-123">Yayımlanacak projeyi.</span><span class="sxs-lookup"><span data-stu-id="2e70f-123">The project to publish.</span></span> <span data-ttu-id="2e70f-124">Belirtilmezse, geçerli dizine varsayılan olur.</span><span class="sxs-lookup"><span data-stu-id="2e70f-124">If not specified, it defaults to the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="2e70f-125">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="2e70f-125">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="2e70f-126">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="2e70f-126">.NET Core 2.1</span></span>](#tab/netcore21)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="2e70f-127">Derleme yapılandırması tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2e70f-127">Defines the build configuration.</span></span> <span data-ttu-id="2e70f-128">Varsayılan değer `Debug` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="2e70f-128">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="2e70f-129">Uygulama için belirtilen yayımlar [hedef framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="2e70f-129">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="2e70f-130">Proje dosyasında hedef Framework'ü belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2e70f-130">You must specify the target framework in the project file.</span></span>

`--force`

<span data-ttu-id="2e70f-131">Son geri yükleme başarılı olsa bile çözümlenmesi için tüm bağımlılıkları zorlar.</span><span class="sxs-lookup"><span data-stu-id="2e70f-131">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="2e70f-132">Bu bayrak belirten aynıdır silme *project.assets.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="2e70f-132">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="2e70f-133">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="2e70f-133">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="2e70f-134">Bir veya birkaç belirtir [hedef bildirimleri](../deploying/runtime-store.md) uygulamayla yayımlanan paket kümesini kırpma için kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="2e70f-134">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="2e70f-135">Bildirim dosyası çıkışını bir parçasıdır [ `dotnet store` komutu](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="2e70f-135">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="2e70f-136">Birden çok bildirimleri belirtmek için ekleyin bir `--manifest` her bildirimi için seçeneği.</span><span class="sxs-lookup"><span data-stu-id="2e70f-136">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="2e70f-137">Bu seçenek, .NET Core 2.0 SDK'sı ile başlayarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2e70f-137">This option is available starting with .NET Core 2.0 SDK.</span></span>

`--no-build`

<span data-ttu-id="2e70f-138">Yayımlamadan önce projeyi derlemek değil.</span><span class="sxs-lookup"><span data-stu-id="2e70f-138">Doesn't build the project before publishing.</span></span> <span data-ttu-id="2e70f-139">Ayrıca örtük ayarlar `--no-restore` bayrağı.</span><span class="sxs-lookup"><span data-stu-id="2e70f-139">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="2e70f-140">Proje Proje başvuruları yoksayar ve yalnızca kök proje geri yükler.</span><span class="sxs-lookup"><span data-stu-id="2e70f-140">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="2e70f-141">Örtük bir geri yükleme komutu çalıştırırken yürütmez.</span><span class="sxs-lookup"><span data-stu-id="2e70f-141">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="2e70f-142">Çıktı dizini yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="2e70f-142">Specifies the path for the output directory.</span></span> <span data-ttu-id="2e70f-143">Belirtilmezse, varsayılan olarak *./bin/[configuration]/[framework]/publish/* framework bağımlı dağıtım için veya *./bin/[configuration]/[framework]/[runtime]/publish/* için bir kendi içinde bulunan dağıtım.</span><span class="sxs-lookup"><span data-stu-id="2e70f-143">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="2e70f-144">Göreli yol ise, oluşturulan çıktı dizini proje dosya konumu, geçerli çalışma dizini için görelidir.</span><span class="sxs-lookup"><span data-stu-id="2e70f-144">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`--self-contained`

<span data-ttu-id="2e70f-145">Çalışma zamanı hedef makinede yüklü olması gerekmez için uygulamanızın ile .NET çekirdeği çalışma zamanı yayımlar.</span><span class="sxs-lookup"><span data-stu-id="2e70f-145">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="2e70f-146">Bir çalışma zamanı tanıtıcı belirtilirse, varsayılan değeri olduğu `true`.</span><span class="sxs-lookup"><span data-stu-id="2e70f-146">If a runtime identifier is specified, its default value is `true`.</span></span> <span data-ttu-id="2e70f-147">Farklı dağıtım türleri hakkında daha fazla bilgi için bkz: [.NET Core uygulama dağıtımı](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="2e70f-147">For more information about the different deployment types, see [.NET Core application deployment](../deploying/index.md).</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="2e70f-148">Uygulama için belirli bir çalışma zamanı yayımlar.</span><span class="sxs-lookup"><span data-stu-id="2e70f-148">Publishes the application for a given runtime.</span></span> <span data-ttu-id="2e70f-149">Bu oluşturulurken kullanılan bir [müstakil dağıtım (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="2e70f-149">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="2e70f-150">Çalışma zamanı tanımlayıcıları (RID) bir listesi için bkz: [RID katalog](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="2e70f-150">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="2e70f-151">Varsayılan değer yayımlamak için bir [framework bağımlı dağıtım (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="2e70f-151">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="2e70f-152">Komutun ayrıntı düzeyi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2e70f-152">Sets the verbosity level of the command.</span></span> <span data-ttu-id="2e70f-153">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="2e70f-153">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="2e70f-154">Yıldız işareti değiştirmek için Sürüm soneki tanımlar (`*`) proje dosyasının sürüm alanında.</span><span class="sxs-lookup"><span data-stu-id="2e70f-154">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="2e70f-155">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="2e70f-155">.NET Core 2.0</span></span>](#tab/netcore20)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="2e70f-156">Derleme yapılandırması tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2e70f-156">Defines the build configuration.</span></span> <span data-ttu-id="2e70f-157">Varsayılan değer `Debug` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="2e70f-157">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="2e70f-158">Uygulama için belirtilen yayımlar [hedef framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="2e70f-158">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="2e70f-159">Proje dosyasında hedef Framework'ü belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2e70f-159">You must specify the target framework in the project file.</span></span>

`--force`

<span data-ttu-id="2e70f-160">Son geri yükleme başarılı olsa bile çözümlenmesi için tüm bağımlılıkları zorlar.</span><span class="sxs-lookup"><span data-stu-id="2e70f-160">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="2e70f-161">Bu bayrak belirten aynıdır silme *project.assets.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="2e70f-161">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="2e70f-162">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="2e70f-162">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="2e70f-163">Bir veya birkaç belirtir [hedef bildirimleri](../deploying/runtime-store.md) uygulamayla yayımlanan paket kümesini kırpma için kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="2e70f-163">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="2e70f-164">Bildirim dosyası çıkışını bir parçasıdır [ `dotnet store` komutu](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="2e70f-164">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="2e70f-165">Birden çok bildirimleri belirtmek için ekleyin bir `--manifest` her bildirimi için seçeneği.</span><span class="sxs-lookup"><span data-stu-id="2e70f-165">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="2e70f-166">Bu seçenek, .NET Core 2.0 SDK'sı ile başlayarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2e70f-166">This option is available starting with .NET Core 2.0 SDK.</span></span>

`--no-dependencies`

<span data-ttu-id="2e70f-167">Proje Proje başvuruları yoksayar ve yalnızca kök proje geri yükler.</span><span class="sxs-lookup"><span data-stu-id="2e70f-167">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="2e70f-168">Örtük bir geri yükleme komutu çalıştırırken yürütmez.</span><span class="sxs-lookup"><span data-stu-id="2e70f-168">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="2e70f-169">Çıktı dizini yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="2e70f-169">Specifies the path for the output directory.</span></span> <span data-ttu-id="2e70f-170">Belirtilmezse, varsayılan olarak *./bin/[configuration]/[framework]/publish/* framework bağımlı dağıtım için veya *./bin/[configuration]/[framework]/[runtime]/publish/* için bir kendi içinde bulunan dağıtım.</span><span class="sxs-lookup"><span data-stu-id="2e70f-170">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="2e70f-171">Göreli yol ise, oluşturulan çıktı dizini proje dosya konumu, geçerli çalışma dizini için görelidir.</span><span class="sxs-lookup"><span data-stu-id="2e70f-171">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`--self-contained`

<span data-ttu-id="2e70f-172">Çalışma zamanı hedef makinede yüklü olması gerekmez için uygulamanızın ile .NET çekirdeği çalışma zamanı yayımlar.</span><span class="sxs-lookup"><span data-stu-id="2e70f-172">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="2e70f-173">Bir çalışma zamanı tanıtıcı belirtilirse, varsayılan değeri olduğu `true`.</span><span class="sxs-lookup"><span data-stu-id="2e70f-173">If a runtime identifier is specified, its default value is `true`.</span></span> <span data-ttu-id="2e70f-174">Farklı dağıtım türleri hakkında daha fazla bilgi için bkz: [.NET Core uygulama dağıtımı](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="2e70f-174">For more information about the different deployment types, see [.NET Core application deployment](../deploying/index.md).</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="2e70f-175">Uygulama için belirli bir çalışma zamanı yayımlar.</span><span class="sxs-lookup"><span data-stu-id="2e70f-175">Publishes the application for a given runtime.</span></span> <span data-ttu-id="2e70f-176">Bu oluşturulurken kullanılan bir [müstakil dağıtım (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="2e70f-176">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="2e70f-177">Çalışma zamanı tanımlayıcıları (RID) bir listesi için bkz: [RID katalog](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="2e70f-177">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="2e70f-178">Varsayılan değer yayımlamak için bir [framework bağımlı dağıtım (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="2e70f-178">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="2e70f-179">Komutun ayrıntı düzeyi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2e70f-179">Sets the verbosity level of the command.</span></span> <span data-ttu-id="2e70f-180">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="2e70f-180">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="2e70f-181">Yıldız işareti değiştirmek için Sürüm soneki tanımlar (`*`) proje dosyasının sürüm alanında.</span><span class="sxs-lookup"><span data-stu-id="2e70f-181">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="2e70f-182">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="2e70f-182">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="2e70f-183">Derleme yapılandırması tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2e70f-183">Defines the build configuration.</span></span> <span data-ttu-id="2e70f-184">Varsayılan değer `Debug` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="2e70f-184">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="2e70f-185">Uygulama için belirtilen yayımlar [hedef framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="2e70f-185">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="2e70f-186">Proje dosyasında hedef Framework'ü belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2e70f-186">You must specify the target framework in the project file.</span></span>

`-h|--help`

<span data-ttu-id="2e70f-187">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="2e70f-187">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="2e70f-188">Bir veya birkaç belirtir [hedef bildirimleri](../deploying/runtime-store.md) uygulamayla yayımlanan paket kümesini kırpma için kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="2e70f-188">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="2e70f-189">Bildirim dosyası çıkışını bir parçasıdır [ `dotnet store` komutu](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="2e70f-189">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="2e70f-190">Birden çok bildirimleri belirtmek için ekleyin bir `--manifest` her bildirimi için seçeneği.</span><span class="sxs-lookup"><span data-stu-id="2e70f-190">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="2e70f-191">Bu seçenek, .NET Core 2.0 SDK'sı ile başlayarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2e70f-191">This option is available starting with .NET Core 2.0 SDK.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="2e70f-192">Çıktı dizini yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="2e70f-192">Specifies the path for the output directory.</span></span> <span data-ttu-id="2e70f-193">Belirtilmezse, varsayılan olarak *./bin/[configuration]/[framework]/publish/* framework bağımlı dağıtım için veya *./bin/[configuration]/[framework]/[runtime]/publish/* için bir kendi içinde bulunan dağıtım.</span><span class="sxs-lookup"><span data-stu-id="2e70f-193">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="2e70f-194">Göreli yol ise, oluşturulan çıktı dizini proje dosya konumu, geçerli çalışma dizini için görelidir.</span><span class="sxs-lookup"><span data-stu-id="2e70f-194">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="2e70f-195">Uygulama için belirli bir çalışma zamanı yayımlar.</span><span class="sxs-lookup"><span data-stu-id="2e70f-195">Publishes the application for a given runtime.</span></span> <span data-ttu-id="2e70f-196">Bu oluşturulurken kullanılan bir [müstakil dağıtım (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="2e70f-196">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="2e70f-197">Çalışma zamanı tanımlayıcıları (RID) bir listesi için bkz: [RID katalog](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="2e70f-197">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="2e70f-198">Varsayılan değer yayımlamak için bir [framework bağımlı dağıtım (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="2e70f-198">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="2e70f-199">Komutun ayrıntı düzeyi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2e70f-199">Sets the verbosity level of the command.</span></span> <span data-ttu-id="2e70f-200">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="2e70f-200">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="2e70f-201">Yıldız işareti değiştirmek için Sürüm soneki tanımlar (`*`) proje dosyasının sürüm alanında.</span><span class="sxs-lookup"><span data-stu-id="2e70f-201">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

---

## <a name="examples"></a><span data-ttu-id="2e70f-202">Örnekler</span><span class="sxs-lookup"><span data-stu-id="2e70f-202">Examples</span></span>

<span data-ttu-id="2e70f-203">Proje geçerli dizinde yayımlayın:</span><span class="sxs-lookup"><span data-stu-id="2e70f-203">Publish the project in the current directory:</span></span>

`dotnet publish`

<span data-ttu-id="2e70f-204">Belirtilen proje dosyası kullanarak uygulama yayımlama:</span><span class="sxs-lookup"><span data-stu-id="2e70f-204">Publish the application using the specified project file:</span></span>

`dotnet publish ~/projects/app1/app1.csproj`

<span data-ttu-id="2e70f-205">Geçerli bir dizin içinde proje yayımlama `netcoreapp1.1` framework:</span><span class="sxs-lookup"><span data-stu-id="2e70f-205">Publish the project in the current directory using the `netcoreapp1.1` framework:</span></span>

`dotnet publish --framework netcoreapp1.1`

<span data-ttu-id="2e70f-206">Geçerli kullanarak uygulamayı yayımlamak `netcoreapp1.1` framework ve Çalışma Zamanı Modülü `OS X 10.10` (proje dosyasında bu RID listelemeniz gerekir).</span><span class="sxs-lookup"><span data-stu-id="2e70f-206">Publish the current application using the `netcoreapp1.1` framework and the runtime for `OS X 10.10` (you must list this RID in the project file).</span></span>

`dotnet publish --framework netcoreapp1.1 --runtime osx.10.11-x64`

<span data-ttu-id="2e70f-207">Geçerli uygulamayı yayımlamak, ancak proje proje (P2P) başvuruları, yalnızca kök proje (.NET Core SDK 2.0 ve sonraki sürümler) geri yükleme işlemi sırasında geri yüklemeyin:</span><span class="sxs-lookup"><span data-stu-id="2e70f-207">Publish the current application but don't restore project-to-project (P2P) references, just the root project during the restore operation (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet publish --no-dependencies`

## <a name="see-also"></a><span data-ttu-id="2e70f-208">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e70f-208">See also</span></span>

* [<span data-ttu-id="2e70f-209">Hedef çerçeveler</span><span class="sxs-lookup"><span data-stu-id="2e70f-209">Target frameworks</span></span>](../../standard/frameworks.md)
* [<span data-ttu-id="2e70f-210">Çalışma zamanı tanımlayıcı (RID) Kataloğu</span><span class="sxs-lookup"><span data-stu-id="2e70f-210">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
