---
title: DotNet command - .NET Core CLI yayımlama
description: Dotnet yayımlama komutu, .NET Core projesi bir dizine yayımlar.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: a60777d613573076f41fba3e5ed610b236884063
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43416928"
---
# <a name="dotnet-publish"></a><span data-ttu-id="986d7-103">DotNet yayımlama</span><span class="sxs-lookup"><span data-stu-id="986d7-103">dotnet publish</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="986d7-104">Ad</span><span class="sxs-lookup"><span data-stu-id="986d7-104">Name</span></span>

<span data-ttu-id="986d7-105">`dotnet publish` -Bir klasöre dağıtım barındıran sistemde için uygulama ve onun bağımlılıklarını paketleri.</span><span class="sxs-lookup"><span data-stu-id="986d7-105">`dotnet publish` - Packs the application and its dependencies into a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="986d7-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="986d7-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="986d7-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="986d7-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-build] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="986d7-108">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="986d7-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="986d7-109">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="986d7-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
    [--version-suffix]
dotnet publish [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="986d7-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="986d7-110">Description</span></span>

<span data-ttu-id="986d7-111">`dotnet publish` uygulamayı derler, bağımlılıkları proje dosyasında belirtilen aracılığıyla okur ve bir dizine dosya sonuç kümesini yayımlar.</span><span class="sxs-lookup"><span data-stu-id="986d7-111">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="986d7-112">Çıktı aşağıdaki varlıklar içerir:</span><span class="sxs-lookup"><span data-stu-id="986d7-112">The output includes the following assets:</span></span>

* <span data-ttu-id="986d7-113">Ara dil (IL) kodu ile bir derlemede bir *dll* uzantısı.</span><span class="sxs-lookup"><span data-stu-id="986d7-113">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
* <span data-ttu-id="986d7-114">*. deps.json* tüm proje bağımlılıklarını içeren dosya.</span><span class="sxs-lookup"><span data-stu-id="986d7-114">*.deps.json* file that includes all of the dependencies of the project.</span></span>
* <span data-ttu-id="986d7-115">*. runtime.config.json* dosyası çalışma zamanı (örneğin, çöp toplama türü) için diğer yapılandırma seçenekleri yanı sıra uygulamanın beklediği paylaşılan çalışma zamanı belirtir.</span><span class="sxs-lookup"><span data-stu-id="986d7-115">*.runtime.config.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
* <span data-ttu-id="986d7-116">Uygulama bağımlılıklarınızın NuGet önbellekten çıktı klasörüne kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="986d7-116">The application's dependencies, which are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="986d7-117">`dotnet publish` Komut çıkışında, bir barındırma sistemine dağıtımı için hazır (örneğin, bir sunucu, PC, Mac, dizüstü) yürütme için.</span><span class="sxs-lookup"><span data-stu-id="986d7-117">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution.</span></span> <span data-ttu-id="986d7-118">Bu uygulama dağıtım için hazırlamak için yalnızca resmi olarak desteklenen yoludur.</span><span class="sxs-lookup"><span data-stu-id="986d7-118">It's the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="986d7-119">Proje belirten bir dağıtım türü, bağlı olarak .NET Core çalışma zamanı yüklü paylaşılmayan sahip veya ana bilgisayar sistemi olabilir.</span><span class="sxs-lookup"><span data-stu-id="986d7-119">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span> <span data-ttu-id="986d7-120">Daha fazla bilgi için [.NET Core uygulaması dağıtımını](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="986d7-120">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span> <span data-ttu-id="986d7-121">Yayımlanmış bir uygulamanın dizin yapısı için bkz. [dizin yapısı](/aspnet/core/hosting/directory-structure).</span><span class="sxs-lookup"><span data-stu-id="986d7-121">For the directory structure of a published application, see [Directory structure](/aspnet/core/hosting/directory-structure).</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="986d7-122">Arguments</span><span class="sxs-lookup"><span data-stu-id="986d7-122">Arguments</span></span>

`PROJECT`

<span data-ttu-id="986d7-123">Yayımlanacak projeyi.</span><span class="sxs-lookup"><span data-stu-id="986d7-123">The project to publish.</span></span> <span data-ttu-id="986d7-124">Belirtilmezse, geçerli dizin için varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="986d7-124">If not specified, it defaults to the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="986d7-125">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="986d7-125">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="986d7-126">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="986d7-126">.NET Core 2.1</span></span>](#tab/netcore21)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="986d7-127">Derleme yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="986d7-127">Defines the build configuration.</span></span> <span data-ttu-id="986d7-128">Varsayılan değer `Debug` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="986d7-128">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="986d7-129">Belirtilen uygulamanın yayınlar [hedef Framework'ü](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="986d7-129">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="986d7-130">Hedef Çerçeve proje dosyasında belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="986d7-130">You must specify the target framework in the project file.</span></span>

`--force`

<span data-ttu-id="986d7-131">Son geri yükleme başarılı olduysa bile çözülmesi için tüm bağımlılıkların zorlar.</span><span class="sxs-lookup"><span data-stu-id="986d7-131">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="986d7-132">Bu bayrak belirten aynıdır silme *project.assets.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="986d7-132">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="986d7-133">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="986d7-133">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="986d7-134">Bir veya birkaç belirtir [hedef bildirimleri](../deploying/runtime-store.md) uygulamayla birlikte yayımlanan paketleri kümesini kırpmak için kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="986d7-134">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="986d7-135">Bildirim dosyası çıktısını bir parçasıdır [ `dotnet store` komut](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="986d7-135">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="986d7-136">Birden çok bildirimleri belirtmek için bir `--manifest` her bildirimi seçeneği.</span><span class="sxs-lookup"><span data-stu-id="986d7-136">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="986d7-137">Bu seçenek, .NET Core 2.0 SDK'sı ile başlayan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="986d7-137">This option is available starting with .NET Core 2.0 SDK.</span></span>

`--no-build`

<span data-ttu-id="986d7-138">Yayımlamadan önce projenizi değil.</span><span class="sxs-lookup"><span data-stu-id="986d7-138">Doesn't build the project before publishing.</span></span> <span data-ttu-id="986d7-139">Ayrıca örtülü olarak ayarlar `--no-restore` bayrağı.</span><span class="sxs-lookup"><span data-stu-id="986d7-139">It also implicitly sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="986d7-140">Projeden projeye başvurular yoksayar ve yalnızca kök proje geri yükler.</span><span class="sxs-lookup"><span data-stu-id="986d7-140">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="986d7-141">Örtük bir geri yükleme komutu çalıştırırken yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="986d7-141">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="986d7-142">Çıktı dizini yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="986d7-142">Specifies the path for the output directory.</span></span> <span data-ttu-id="986d7-143">Belirtilmezse, varsayılan *./bin/[configuration]/[framework]/publish/* framework bağımlı dağıtım veya *./bin/[configuration]/[framework]/[runtime]/publish/* için bir kendi başına dağıtım.</span><span class="sxs-lookup"><span data-stu-id="986d7-143">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="986d7-144">Yolun göreli olduğuna, proje dosyasının konumunu değil geçerli çalışma dizinine göre oluşturulan çıktı dizini olur.</span><span class="sxs-lookup"><span data-stu-id="986d7-144">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`--self-contained`

<span data-ttu-id="986d7-145">Çalışma zamanı hedef makinede yüklü olması gerekmez .NET Core çalışma zamanı, uygulamanız ile yayımlar.</span><span class="sxs-lookup"><span data-stu-id="986d7-145">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="986d7-146">Bir çalışma zamanı tanımlayıcısı belirtilmezse, varsayılan değerdir `true`.</span><span class="sxs-lookup"><span data-stu-id="986d7-146">If a runtime identifier is specified, its default value is `true`.</span></span> <span data-ttu-id="986d7-147">Farklı dağıtım türleri hakkında daha fazla bilgi için bkz. [.NET Core uygulama dağıtımı](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="986d7-147">For more information about the different deployment types, see [.NET Core application deployment](../deploying/index.md).</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="986d7-148">Belirli bir çalışma zamanı için uygulamanın yayınlar.</span><span class="sxs-lookup"><span data-stu-id="986d7-148">Publishes the application for a given runtime.</span></span> <span data-ttu-id="986d7-149">Bu oluştururken kullanılan bir [müstakil dağıtım (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="986d7-149">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="986d7-150">Çalışma zamanı tanımlayıcılarının (RID'ler) bir listesi için bkz. [RID Kataloğu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="986d7-150">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="986d7-151">Varsayılan değer yayımlamak için bir [framework bağımlı dağıtım (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="986d7-151">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="986d7-152">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="986d7-152">Sets the verbosity level of the command.</span></span> <span data-ttu-id="986d7-153">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="986d7-153">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="986d7-154">Yıldız işareti değiştirmek için Sürüm soneki tanımlar (`*`) proje dosyasının sürümü alanında.</span><span class="sxs-lookup"><span data-stu-id="986d7-154">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="986d7-155">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="986d7-155">.NET Core 2.0</span></span>](#tab/netcore20)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="986d7-156">Derleme yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="986d7-156">Defines the build configuration.</span></span> <span data-ttu-id="986d7-157">Varsayılan değer `Debug` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="986d7-157">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="986d7-158">Belirtilen uygulamanın yayınlar [hedef Framework'ü](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="986d7-158">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="986d7-159">Hedef Çerçeve proje dosyasında belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="986d7-159">You must specify the target framework in the project file.</span></span>

`--force`

<span data-ttu-id="986d7-160">Son geri yükleme başarılı olduysa bile çözülmesi için tüm bağımlılıkların zorlar.</span><span class="sxs-lookup"><span data-stu-id="986d7-160">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="986d7-161">Bu bayrak belirten aynıdır silme *project.assets.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="986d7-161">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="986d7-162">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="986d7-162">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="986d7-163">Bir veya birkaç belirtir [hedef bildirimleri](../deploying/runtime-store.md) uygulamayla birlikte yayımlanan paketleri kümesini kırpmak için kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="986d7-163">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="986d7-164">Bildirim dosyası çıktısını bir parçasıdır [ `dotnet store` komut](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="986d7-164">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="986d7-165">Birden çok bildirimleri belirtmek için bir `--manifest` her bildirimi seçeneği.</span><span class="sxs-lookup"><span data-stu-id="986d7-165">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="986d7-166">Bu seçenek, .NET Core 2.0 SDK'sı ile başlayan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="986d7-166">This option is available starting with .NET Core 2.0 SDK.</span></span>

`--no-dependencies`

<span data-ttu-id="986d7-167">Projeden projeye başvurular yoksayar ve yalnızca kök proje geri yükler.</span><span class="sxs-lookup"><span data-stu-id="986d7-167">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="986d7-168">Örtük bir geri yükleme komutu çalıştırırken yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="986d7-168">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="986d7-169">Çıktı dizini yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="986d7-169">Specifies the path for the output directory.</span></span> <span data-ttu-id="986d7-170">Belirtilmezse, varsayılan *./bin/[configuration]/[framework]/publish/* framework bağımlı dağıtım veya *./bin/[configuration]/[framework]/[runtime]/publish/* için bir kendi başına dağıtım.</span><span class="sxs-lookup"><span data-stu-id="986d7-170">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="986d7-171">Yolun göreli olduğuna, proje dosyasının konumunu değil geçerli çalışma dizinine göre oluşturulan çıktı dizini olur.</span><span class="sxs-lookup"><span data-stu-id="986d7-171">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`--self-contained`

<span data-ttu-id="986d7-172">Çalışma zamanı hedef makinede yüklü olması gerekmez .NET Core çalışma zamanı, uygulamanız ile yayımlar.</span><span class="sxs-lookup"><span data-stu-id="986d7-172">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="986d7-173">Bir çalışma zamanı tanımlayıcısı belirtilmezse, varsayılan değerdir `true`.</span><span class="sxs-lookup"><span data-stu-id="986d7-173">If a runtime identifier is specified, its default value is `true`.</span></span> <span data-ttu-id="986d7-174">Farklı dağıtım türleri hakkında daha fazla bilgi için bkz. [.NET Core uygulama dağıtımı](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="986d7-174">For more information about the different deployment types, see [.NET Core application deployment](../deploying/index.md).</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="986d7-175">Belirli bir çalışma zamanı için uygulamanın yayınlar.</span><span class="sxs-lookup"><span data-stu-id="986d7-175">Publishes the application for a given runtime.</span></span> <span data-ttu-id="986d7-176">Bu oluştururken kullanılan bir [müstakil dağıtım (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="986d7-176">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="986d7-177">Çalışma zamanı tanımlayıcılarının (RID'ler) bir listesi için bkz. [RID Kataloğu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="986d7-177">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="986d7-178">Varsayılan değer yayımlamak için bir [framework bağımlı dağıtım (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="986d7-178">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="986d7-179">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="986d7-179">Sets the verbosity level of the command.</span></span> <span data-ttu-id="986d7-180">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="986d7-180">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="986d7-181">Yıldız işareti değiştirmek için Sürüm soneki tanımlar (`*`) proje dosyasının sürümü alanında.</span><span class="sxs-lookup"><span data-stu-id="986d7-181">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="986d7-182">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="986d7-182">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="986d7-183">Derleme yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="986d7-183">Defines the build configuration.</span></span> <span data-ttu-id="986d7-184">Varsayılan değer `Debug` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="986d7-184">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="986d7-185">Belirtilen uygulamanın yayınlar [hedef Framework'ü](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="986d7-185">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="986d7-186">Hedef Çerçeve proje dosyasında belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="986d7-186">You must specify the target framework in the project file.</span></span>

`-h|--help`

<span data-ttu-id="986d7-187">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="986d7-187">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="986d7-188">Bir veya birkaç belirtir [hedef bildirimleri](../deploying/runtime-store.md) uygulamayla birlikte yayımlanan paketleri kümesini kırpmak için kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="986d7-188">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="986d7-189">Bildirim dosyası çıktısını bir parçasıdır [ `dotnet store` komut](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="986d7-189">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="986d7-190">Birden çok bildirimleri belirtmek için bir `--manifest` her bildirimi seçeneği.</span><span class="sxs-lookup"><span data-stu-id="986d7-190">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="986d7-191">Bu seçenek, .NET Core 2.0 SDK'sı ile başlayan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="986d7-191">This option is available starting with .NET Core 2.0 SDK.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="986d7-192">Çıktı dizini yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="986d7-192">Specifies the path for the output directory.</span></span> <span data-ttu-id="986d7-193">Belirtilmezse, varsayılan *./bin/[configuration]/[framework]/publish/* framework bağımlı dağıtım veya *./bin/[configuration]/[framework]/[runtime]/publish/* için bir kendi başına dağıtım.</span><span class="sxs-lookup"><span data-stu-id="986d7-193">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="986d7-194">Yolun göreli olduğuna, proje dosyasının konumunu değil geçerli çalışma dizinine göre oluşturulan çıktı dizini olur.</span><span class="sxs-lookup"><span data-stu-id="986d7-194">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="986d7-195">Belirli bir çalışma zamanı için uygulamanın yayınlar.</span><span class="sxs-lookup"><span data-stu-id="986d7-195">Publishes the application for a given runtime.</span></span> <span data-ttu-id="986d7-196">Bu oluştururken kullanılan bir [müstakil dağıtım (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="986d7-196">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="986d7-197">Çalışma zamanı tanımlayıcılarının (RID'ler) bir listesi için bkz. [RID Kataloğu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="986d7-197">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="986d7-198">Varsayılan değer yayımlamak için bir [framework bağımlı dağıtım (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="986d7-198">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="986d7-199">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="986d7-199">Sets the verbosity level of the command.</span></span> <span data-ttu-id="986d7-200">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="986d7-200">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="986d7-201">Yıldız işareti değiştirmek için Sürüm soneki tanımlar (`*`) proje dosyasının sürümü alanında.</span><span class="sxs-lookup"><span data-stu-id="986d7-201">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

---

## <a name="examples"></a><span data-ttu-id="986d7-202">Örnekler</span><span class="sxs-lookup"><span data-stu-id="986d7-202">Examples</span></span>

<span data-ttu-id="986d7-203">Projenin geçerli dizinde yayımlama:</span><span class="sxs-lookup"><span data-stu-id="986d7-203">Publish the project in the current directory:</span></span>

`dotnet publish`

<span data-ttu-id="986d7-204">Belirtilen proje dosyasını kullanarak uygulama yayımlama:</span><span class="sxs-lookup"><span data-stu-id="986d7-204">Publish the application using the specified project file:</span></span>

`dotnet publish ~/projects/app1/app1.csproj`

<span data-ttu-id="986d7-205">Projenin geçerli kullanarak dizin yayımlama `netcoreapp1.1` framework:</span><span class="sxs-lookup"><span data-stu-id="986d7-205">Publish the project in the current directory using the `netcoreapp1.1` framework:</span></span>

`dotnet publish --framework netcoreapp1.1`

<span data-ttu-id="986d7-206">Geçerli kullanarak uygulama yayımlama `netcoreapp1.1` çerçevesi ve çalışma zamanı için `OS X 10.10` (proje dosyasında bu RID listelemesi gerekir).</span><span class="sxs-lookup"><span data-stu-id="986d7-206">Publish the current application using the `netcoreapp1.1` framework and the runtime for `OS X 10.10` (you must list this RID in the project file).</span></span>

`dotnet publish --framework netcoreapp1.1 --runtime osx.10.11-x64`

<span data-ttu-id="986d7-207">Geçerli uygulama yayımlama ancak projeden projeye (P2P) başvurular, yalnızca kök projesi (.NET Core SDK 2.0 ve sonraki sürümler) geri yükleme işlemi sırasında geri yükleme:</span><span class="sxs-lookup"><span data-stu-id="986d7-207">Publish the current application but don't restore project-to-project (P2P) references, just the root project during the restore operation (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet publish --no-dependencies`

## <a name="see-also"></a><span data-ttu-id="986d7-208">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="986d7-208">See also</span></span>

* [<span data-ttu-id="986d7-209">Hedef çerçeveler</span><span class="sxs-lookup"><span data-stu-id="986d7-209">Target frameworks</span></span>](../../standard/frameworks.md)
* [<span data-ttu-id="986d7-210">Çalışma zamanı tanımlayıcı (RID) Kataloğu</span><span class="sxs-lookup"><span data-stu-id="986d7-210">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
