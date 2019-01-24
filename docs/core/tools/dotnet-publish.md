---
title: DotNet yayımlama komutu
description: Dotnet yayımlama komutu, .NET Core projesi bir dizine yayımlar.
ms.date: 05/29/2018
ms.openlocfilehash: 40ce31073ee3f6f94e110f3a4e1eeda0c7b2e48d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54559326"
---
# <a name="dotnet-publish"></a><span data-ttu-id="7422a-103">DotNet yayımlama</span><span class="sxs-lookup"><span data-stu-id="7422a-103">dotnet publish</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="7422a-104">Ad</span><span class="sxs-lookup"><span data-stu-id="7422a-104">Name</span></span>

<span data-ttu-id="7422a-105">`dotnet publish` -Bir klasöre dağıtım barındıran sistemde için uygulama ve onun bağımlılıklarını paketleri.</span><span class="sxs-lookup"><span data-stu-id="7422a-105">`dotnet publish` - Packs the application and its dependencies into a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="7422a-106">Synopsis</span><span class="sxs-lookup"><span data-stu-id="7422a-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="7422a-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="7422a-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-build] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="7422a-108">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="7422a-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="7422a-109">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="7422a-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
    [--version-suffix]
dotnet publish [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="7422a-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7422a-110">Description</span></span>

<span data-ttu-id="7422a-111">`dotnet publish` uygulamayı derler, bağımlılıkları proje dosyasında belirtilen aracılığıyla okur ve bir dizine dosya sonuç kümesini yayımlar.</span><span class="sxs-lookup"><span data-stu-id="7422a-111">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="7422a-112">Çıktı aşağıdaki varlıklar içerir:</span><span class="sxs-lookup"><span data-stu-id="7422a-112">The output includes the following assets:</span></span>

* <span data-ttu-id="7422a-113">Ara dil (IL) kodu ile bir derlemede bir *dll* uzantısı.</span><span class="sxs-lookup"><span data-stu-id="7422a-113">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
* <span data-ttu-id="7422a-114">*. deps.json* tüm proje bağımlılıklarını içeren dosya.</span><span class="sxs-lookup"><span data-stu-id="7422a-114">*.deps.json* file that includes all of the dependencies of the project.</span></span>
* <span data-ttu-id="7422a-115">*. runtime.config.json* dosyası çalışma zamanı (örneğin, çöp toplama türü) için diğer yapılandırma seçenekleri yanı sıra uygulamanın beklediği paylaşılan çalışma zamanı belirtir.</span><span class="sxs-lookup"><span data-stu-id="7422a-115">*.runtime.config.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
* <span data-ttu-id="7422a-116">Uygulama bağımlılıklarınızın NuGet önbellekten çıktı klasörüne kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="7422a-116">The application's dependencies, which are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="7422a-117">`dotnet publish` Komut çıkışında, bir barındırma sistemine dağıtımı için hazır (örneğin, bir sunucu, PC, Mac, dizüstü) yürütme için.</span><span class="sxs-lookup"><span data-stu-id="7422a-117">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution.</span></span> <span data-ttu-id="7422a-118">Bu uygulama dağıtım için hazırlamak için yalnızca resmi olarak desteklenen yoludur.</span><span class="sxs-lookup"><span data-stu-id="7422a-118">It's the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="7422a-119">Proje belirten bir dağıtım türü, bağlı olarak .NET Core çalışma zamanı yüklü paylaşılmayan sahip veya ana bilgisayar sistemi olabilir.</span><span class="sxs-lookup"><span data-stu-id="7422a-119">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span> <span data-ttu-id="7422a-120">Daha fazla bilgi için [.NET Core uygulaması dağıtımını](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="7422a-120">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span> <span data-ttu-id="7422a-121">Yayımlanmış bir uygulamanın dizin yapısı için bkz. [dizin yapısı](/aspnet/core/hosting/directory-structure).</span><span class="sxs-lookup"><span data-stu-id="7422a-121">For the directory structure of a published application, see [Directory structure](/aspnet/core/hosting/directory-structure).</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="7422a-122">Arguments</span><span class="sxs-lookup"><span data-stu-id="7422a-122">Arguments</span></span>

`PROJECT`

<span data-ttu-id="7422a-123">Yayımlanacak projeyi.</span><span class="sxs-lookup"><span data-stu-id="7422a-123">The project to publish.</span></span> <span data-ttu-id="7422a-124">Yol ve dosya adı olan bir [ C# ](csproj.md), F#, veya Visual Basic proje dosyası ya da içeren dizinin yolunu bir C#, F#, veya Visual Basic proje dosyası.</span><span class="sxs-lookup"><span data-stu-id="7422a-124">It's either the path and filename of a [C#](csproj.md), F#, or Visual Basic project file, or the path to a directory that contains a C#, F#, or Visual Basic project file.</span></span> <span data-ttu-id="7422a-125">Belirtilmezse, geçerli dizin için varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="7422a-125">If not specified, it defaults to the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="7422a-126">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="7422a-126">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="7422a-127">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="7422a-127">.NET Core 2.1</span></span>](#tab/netcore21)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="7422a-128">Derleme yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7422a-128">Defines the build configuration.</span></span> <span data-ttu-id="7422a-129">Varsayılan değer `Debug` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="7422a-129">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="7422a-130">Belirtilen uygulamanın yayınlar [hedef Framework'ü](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="7422a-130">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="7422a-131">Hedef Çerçeve proje dosyasında belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7422a-131">You must specify the target framework in the project file.</span></span>

`--force`

<span data-ttu-id="7422a-132">Son geri yükleme başarılı olduysa bile çözülmesi için tüm bağımlılıkların zorlar.</span><span class="sxs-lookup"><span data-stu-id="7422a-132">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="7422a-133">Bu bayrak belirten aynıdır silme *project.assets.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="7422a-133">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="7422a-134">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="7422a-134">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="7422a-135">Bir veya birkaç belirtir [hedef bildirimleri](../deploying/runtime-store.md) uygulamayla birlikte yayımlanan paketleri kümesini kırpmak için kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="7422a-135">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="7422a-136">Bildirim dosyası çıktısını bir parçasıdır [ `dotnet store` komut](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="7422a-136">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="7422a-137">Birden çok bildirimleri belirtmek için bir `--manifest` her bildirimi seçeneği.</span><span class="sxs-lookup"><span data-stu-id="7422a-137">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="7422a-138">Bu seçenek, .NET Core 2.0 SDK'sı ile başlayan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7422a-138">This option is available starting with .NET Core 2.0 SDK.</span></span>

`--no-build`

<span data-ttu-id="7422a-139">Yayımlamadan önce projenizi değil.</span><span class="sxs-lookup"><span data-stu-id="7422a-139">Doesn't build the project before publishing.</span></span> <span data-ttu-id="7422a-140">Ayrıca örtülü olarak ayarlar `--no-restore` bayrağı.</span><span class="sxs-lookup"><span data-stu-id="7422a-140">It also implicitly sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="7422a-141">Projeden projeye başvurular yoksayar ve yalnızca kök proje geri yükler.</span><span class="sxs-lookup"><span data-stu-id="7422a-141">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="7422a-142">Örtük bir geri yükleme komutu çalıştırırken yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="7422a-142">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="7422a-143">Çıktı dizini yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="7422a-143">Specifies the path for the output directory.</span></span> <span data-ttu-id="7422a-144">Belirtilmezse, varsayılan *./bin/[configuration]/[framework]/publish/* framework bağımlı dağıtım veya *./bin/[configuration]/[framework]/[runtime]/publish/* için bir kendi başına dağıtım.</span><span class="sxs-lookup"><span data-stu-id="7422a-144">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="7422a-145">Yolun göreli olduğuna, proje dosyasının konumunu değil geçerli çalışma dizinine göre oluşturulan çıktı dizini olur.</span><span class="sxs-lookup"><span data-stu-id="7422a-145">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`--self-contained`

<span data-ttu-id="7422a-146">Çalışma zamanı hedef makinede yüklü olması gerekmez .NET Core çalışma zamanı, uygulamanız ile yayımlar.</span><span class="sxs-lookup"><span data-stu-id="7422a-146">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="7422a-147">Bir çalışma zamanı tanımlayıcısı belirtilmezse, varsayılan değerdir `true`.</span><span class="sxs-lookup"><span data-stu-id="7422a-147">If a runtime identifier is specified, its default value is `true`.</span></span> <span data-ttu-id="7422a-148">Farklı dağıtım türleri hakkında daha fazla bilgi için bkz. [.NET Core uygulama dağıtımı](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="7422a-148">For more information about the different deployment types, see [.NET Core application deployment](../deploying/index.md).</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="7422a-149">Belirli bir çalışma zamanı için uygulamanın yayınlar.</span><span class="sxs-lookup"><span data-stu-id="7422a-149">Publishes the application for a given runtime.</span></span> <span data-ttu-id="7422a-150">Bu oluştururken kullanılan bir [müstakil dağıtım (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="7422a-150">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="7422a-151">Çalışma zamanı tanımlayıcılarının (RID'ler) bir listesi için bkz. [RID Kataloğu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="7422a-151">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="7422a-152">Varsayılan değer yayımlamak için bir [framework bağımlı dağıtım (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="7422a-152">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="7422a-153">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="7422a-153">Sets the verbosity level of the command.</span></span> <span data-ttu-id="7422a-154">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="7422a-154">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="7422a-155">Yıldız işareti değiştirmek için Sürüm soneki tanımlar (`*`) proje dosyasının sürümü alanında.</span><span class="sxs-lookup"><span data-stu-id="7422a-155">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="7422a-156">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="7422a-156">.NET Core 2.0</span></span>](#tab/netcore20)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="7422a-157">Derleme yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7422a-157">Defines the build configuration.</span></span> <span data-ttu-id="7422a-158">Varsayılan değer `Debug` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="7422a-158">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="7422a-159">Belirtilen uygulamanın yayınlar [hedef Framework'ü](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="7422a-159">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="7422a-160">Hedef Çerçeve proje dosyasında belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7422a-160">You must specify the target framework in the project file.</span></span>

`--force`

<span data-ttu-id="7422a-161">Son geri yükleme başarılı olduysa bile çözülmesi için tüm bağımlılıkların zorlar.</span><span class="sxs-lookup"><span data-stu-id="7422a-161">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="7422a-162">Bu bayrak belirten aynıdır silme *project.assets.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="7422a-162">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="7422a-163">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="7422a-163">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="7422a-164">Bir veya birkaç belirtir [hedef bildirimleri](../deploying/runtime-store.md) uygulamayla birlikte yayımlanan paketleri kümesini kırpmak için kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="7422a-164">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="7422a-165">Bildirim dosyası çıktısını bir parçasıdır [ `dotnet store` komut](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="7422a-165">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="7422a-166">Birden çok bildirimleri belirtmek için bir `--manifest` her bildirimi seçeneği.</span><span class="sxs-lookup"><span data-stu-id="7422a-166">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="7422a-167">Bu seçenek, .NET Core 2.0 SDK'sı ile başlayan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7422a-167">This option is available starting with .NET Core 2.0 SDK.</span></span>

`--no-dependencies`

<span data-ttu-id="7422a-168">Projeden projeye başvurular yoksayar ve yalnızca kök proje geri yükler.</span><span class="sxs-lookup"><span data-stu-id="7422a-168">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="7422a-169">Örtük bir geri yükleme komutu çalıştırırken yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="7422a-169">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="7422a-170">Çıktı dizini yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="7422a-170">Specifies the path for the output directory.</span></span> <span data-ttu-id="7422a-171">Belirtilmezse, varsayılan *./bin/[configuration]/[framework]/publish/* framework bağımlı dağıtım veya *./bin/[configuration]/[framework]/[runtime]/publish/* için bir kendi başına dağıtım.</span><span class="sxs-lookup"><span data-stu-id="7422a-171">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="7422a-172">Yolun göreli olduğuna, proje dosyasının konumunu değil geçerli çalışma dizinine göre oluşturulan çıktı dizini olur.</span><span class="sxs-lookup"><span data-stu-id="7422a-172">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`--self-contained`

<span data-ttu-id="7422a-173">Çalışma zamanı hedef makinede yüklü olması gerekmez .NET Core çalışma zamanı, uygulamanız ile yayımlar.</span><span class="sxs-lookup"><span data-stu-id="7422a-173">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="7422a-174">Bir çalışma zamanı tanımlayıcısı belirtilmezse, varsayılan değerdir `true`.</span><span class="sxs-lookup"><span data-stu-id="7422a-174">If a runtime identifier is specified, its default value is `true`.</span></span> <span data-ttu-id="7422a-175">Farklı dağıtım türleri hakkında daha fazla bilgi için bkz. [.NET Core uygulama dağıtımı](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="7422a-175">For more information about the different deployment types, see [.NET Core application deployment](../deploying/index.md).</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="7422a-176">Belirli bir çalışma zamanı için uygulamanın yayınlar.</span><span class="sxs-lookup"><span data-stu-id="7422a-176">Publishes the application for a given runtime.</span></span> <span data-ttu-id="7422a-177">Bu oluştururken kullanılan bir [müstakil dağıtım (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="7422a-177">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="7422a-178">Çalışma zamanı tanımlayıcılarının (RID'ler) bir listesi için bkz. [RID Kataloğu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="7422a-178">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="7422a-179">Varsayılan değer yayımlamak için bir [framework bağımlı dağıtım (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="7422a-179">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="7422a-180">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="7422a-180">Sets the verbosity level of the command.</span></span> <span data-ttu-id="7422a-181">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="7422a-181">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="7422a-182">Yıldız işareti değiştirmek için Sürüm soneki tanımlar (`*`) proje dosyasının sürümü alanında.</span><span class="sxs-lookup"><span data-stu-id="7422a-182">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="7422a-183">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="7422a-183">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="7422a-184">Derleme yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7422a-184">Defines the build configuration.</span></span> <span data-ttu-id="7422a-185">Varsayılan değer `Debug` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="7422a-185">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="7422a-186">Belirtilen uygulamanın yayınlar [hedef Framework'ü](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="7422a-186">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="7422a-187">Hedef Çerçeve proje dosyasında belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7422a-187">You must specify the target framework in the project file.</span></span>

`-h|--help`

<span data-ttu-id="7422a-188">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="7422a-188">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="7422a-189">Bir veya birkaç belirtir [hedef bildirimleri](../deploying/runtime-store.md) uygulamayla birlikte yayımlanan paketleri kümesini kırpmak için kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="7422a-189">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="7422a-190">Bildirim dosyası çıktısını bir parçasıdır [ `dotnet store` komut](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="7422a-190">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="7422a-191">Birden çok bildirimleri belirtmek için bir `--manifest` her bildirimi seçeneği.</span><span class="sxs-lookup"><span data-stu-id="7422a-191">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="7422a-192">Bu seçenek, .NET Core 2.0 SDK'sı ile başlayan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7422a-192">This option is available starting with .NET Core 2.0 SDK.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="7422a-193">Çıktı dizini yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="7422a-193">Specifies the path for the output directory.</span></span> <span data-ttu-id="7422a-194">Belirtilmezse, varsayılan *./bin/[configuration]/[framework]/publish/* framework bağımlı dağıtım veya *./bin/[configuration]/[framework]/[runtime]/publish/* için bir kendi başına dağıtım.</span><span class="sxs-lookup"><span data-stu-id="7422a-194">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="7422a-195">Yolun göreli olduğuna, proje dosyasının konumunu değil geçerli çalışma dizinine göre oluşturulan çıktı dizini olur.</span><span class="sxs-lookup"><span data-stu-id="7422a-195">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="7422a-196">Belirli bir çalışma zamanı için uygulamanın yayınlar.</span><span class="sxs-lookup"><span data-stu-id="7422a-196">Publishes the application for a given runtime.</span></span> <span data-ttu-id="7422a-197">Bu oluştururken kullanılan bir [müstakil dağıtım (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="7422a-197">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="7422a-198">Çalışma zamanı tanımlayıcılarının (RID'ler) bir listesi için bkz. [RID Kataloğu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="7422a-198">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="7422a-199">Varsayılan değer yayımlamak için bir [framework bağımlı dağıtım (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="7422a-199">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="7422a-200">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="7422a-200">Sets the verbosity level of the command.</span></span> <span data-ttu-id="7422a-201">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="7422a-201">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="7422a-202">Yıldız işareti değiştirmek için Sürüm soneki tanımlar (`*`) proje dosyasının sürümü alanında.</span><span class="sxs-lookup"><span data-stu-id="7422a-202">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

---

## <a name="examples"></a><span data-ttu-id="7422a-203">Örnekler</span><span class="sxs-lookup"><span data-stu-id="7422a-203">Examples</span></span>

<span data-ttu-id="7422a-204">Projenin geçerli dizinde yayımlama:</span><span class="sxs-lookup"><span data-stu-id="7422a-204">Publish the project in the current directory:</span></span>

`dotnet publish`

<span data-ttu-id="7422a-205">Belirtilen proje dosyasını kullanarak uygulama yayımlama:</span><span class="sxs-lookup"><span data-stu-id="7422a-205">Publish the application using the specified project file:</span></span>

`dotnet publish ~/projects/app1/app1.csproj`

<span data-ttu-id="7422a-206">Projenin geçerli kullanarak dizin yayımlama `netcoreapp1.1` framework:</span><span class="sxs-lookup"><span data-stu-id="7422a-206">Publish the project in the current directory using the `netcoreapp1.1` framework:</span></span>

`dotnet publish --framework netcoreapp1.1`

<span data-ttu-id="7422a-207">Geçerli kullanarak uygulama yayımlama `netcoreapp1.1` çerçevesi ve çalışma zamanı için `OS X 10.10` (proje dosyasında bu RID listelemesi gerekir).</span><span class="sxs-lookup"><span data-stu-id="7422a-207">Publish the current application using the `netcoreapp1.1` framework and the runtime for `OS X 10.10` (you must list this RID in the project file).</span></span>

`dotnet publish --framework netcoreapp1.1 --runtime osx.10.11-x64`

<span data-ttu-id="7422a-208">Geçerli uygulama yayımlama ancak projeden projeye (P2P) başvurular, yalnızca kök projesi (.NET Core SDK 2.0 ve sonraki sürümler) geri yükleme işlemi sırasında geri yükleme:</span><span class="sxs-lookup"><span data-stu-id="7422a-208">Publish the current application but don't restore project-to-project (P2P) references, just the root project during the restore operation (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet publish --no-dependencies`

## <a name="see-also"></a><span data-ttu-id="7422a-209">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7422a-209">See also</span></span>

- [<span data-ttu-id="7422a-210">Hedef çerçeveler</span><span class="sxs-lookup"><span data-stu-id="7422a-210">Target frameworks</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="7422a-211">Çalışma zamanı tanımlayıcı (RID) Kataloğu</span><span class="sxs-lookup"><span data-stu-id="7422a-211">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
