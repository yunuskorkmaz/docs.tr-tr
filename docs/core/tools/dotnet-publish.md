---
title: dotnet publish komutu
description: Dotnet publish komutu .NET Core projenizi bir dizinde yayımlar.
ms.date: 05/29/2018
ms.openlocfilehash: 4612c8cd1f63550905ef7c6d94af050892b1620c
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117607"
---
# <a name="dotnet-publish"></a><span data-ttu-id="9caed-103">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="9caed-103">dotnet publish</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="9caed-104">Ad</span><span class="sxs-lookup"><span data-stu-id="9caed-104">Name</span></span>

<span data-ttu-id="9caed-105">`dotnet publish`-Uygulamayı ve bağımlılıklarını bir barındırma sistemine dağıtım için bir klasöre paketler.</span><span class="sxs-lookup"><span data-stu-id="9caed-105">`dotnet publish` - Packs the application and its dependencies into a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="9caed-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="9caed-106">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="9caed-107">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="9caed-107">.NET Core 2.1</span></span>](#tab/netcore21)

```dotnetcli
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-build] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="9caed-108">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="9caed-108">.NET Core 2.0</span></span>](#tab/netcore20)

```dotnetcli
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="9caed-109">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="9caed-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
    [--version-suffix]
dotnet publish [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="9caed-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9caed-110">Description</span></span>

<span data-ttu-id="9caed-111">`dotnet publish`uygulamayı derler, proje dosyasında belirtilen bağımlılıklarını okur ve elde edilen dosya kümesini bir dizine yayınlar.</span><span class="sxs-lookup"><span data-stu-id="9caed-111">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="9caed-112">Çıktı aşağıdaki varlıkları içerir:</span><span class="sxs-lookup"><span data-stu-id="9caed-112">The output includes the following assets:</span></span>

- <span data-ttu-id="9caed-113">*DLL* uzantılı bir derlemede ara DIL (IL) kodu.</span><span class="sxs-lookup"><span data-stu-id="9caed-113">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
- <span data-ttu-id="9caed-114">*. Deps. JSON* dosyası, projenin tüm bağımlılıklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="9caed-114">*.deps.json* file that includes all of the dependencies of the project.</span></span>
- <span data-ttu-id="9caed-115">uygulamanın beklediği paylaşılan çalışma zamanını belirten *. runtimeconfig. JSON* dosyası, ayrıca çalışma zamanına yönelik diğer yapılandırma seçenekleri (örneğin, çöp toplama türü).</span><span class="sxs-lookup"><span data-stu-id="9caed-115">*.runtimeconfig.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
- <span data-ttu-id="9caed-116">NuGet önbelleğinden çıkış klasörüne kopyalanmış olan uygulamanın bağımlılıkları.</span><span class="sxs-lookup"><span data-stu-id="9caed-116">The application's dependencies, which are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="9caed-117">`dotnet publish` Komutun çıktısı, yürütme için bir barındırma sistemine (örneğin, bir sunucu, PC, Mac, dizüstü bilgisayar) dağıtıma yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="9caed-117">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution.</span></span> <span data-ttu-id="9caed-118">Uygulamayı dağıtıma hazırlamak için tek resmi olarak desteklenen bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="9caed-118">It's the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="9caed-119">Projenin belirttiği dağıtımın türüne bağlı olarak, barındırma sisteminde .NET Core paylaşılan çalışma zamanı yüklü olabilir veya olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="9caed-119">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span> <span data-ttu-id="9caed-120">Daha fazla bilgi için bkz. [.NET Core uygulama dağıtımı](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="9caed-120">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span> <span data-ttu-id="9caed-121">Yayımlanan bir uygulamanın dizin yapısı için bkz. [Dizin yapısı](/aspnet/core/hosting/directory-structure).</span><span class="sxs-lookup"><span data-stu-id="9caed-121">For the directory structure of a published application, see [Directory structure](/aspnet/core/hosting/directory-structure).</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="9caed-122">Arguments</span><span class="sxs-lookup"><span data-stu-id="9caed-122">Arguments</span></span>

`PROJECT`

<span data-ttu-id="9caed-123">Yayımlanacak proje.</span><span class="sxs-lookup"><span data-stu-id="9caed-123">The project to publish.</span></span> <span data-ttu-id="9caed-124">Bir [C#](csproj.md), F#veya Visual Basic proje dosyasının yolu ve dosya adı ya da C#, F#ya da Visual Basic proje dosyası içeren bir dizinin yolu.</span><span class="sxs-lookup"><span data-stu-id="9caed-124">It's either the path and filename of a [C#](csproj.md), F#, or Visual Basic project file, or the path to a directory that contains a C#, F#, or Visual Basic project file.</span></span> <span data-ttu-id="9caed-125">Belirtilmezse, varsayılan olarak geçerli dizini alır.</span><span class="sxs-lookup"><span data-stu-id="9caed-125">If not specified, it defaults to the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="9caed-126">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="9caed-126">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="9caed-127">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="9caed-127">.NET Core 2.1</span></span>](#tab/netcore21)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="9caed-128">Yapı yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9caed-128">Defines the build configuration.</span></span> <span data-ttu-id="9caed-129">Varsayılan değer `Debug` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="9caed-129">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="9caed-130">Belirtilen [hedef çerçeve](../../standard/frameworks.md)için uygulamayı yayımlar.</span><span class="sxs-lookup"><span data-stu-id="9caed-130">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="9caed-131">Hedef çerçeveyi proje dosyasında belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9caed-131">You must specify the target framework in the project file.</span></span>

`--force`

<span data-ttu-id="9caed-132">Son geri yükleme başarılı olsa bile tüm bağımlılıkların çözülmesini zorlar.</span><span class="sxs-lookup"><span data-stu-id="9caed-132">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="9caed-133">Bu bayrağın belirtilmesi, *Project. varlıklar. JSON* dosyasını silme ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="9caed-133">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="9caed-134">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="9caed-134">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="9caed-135">Uygulamayla yayımlanmış paket kümesini kırpmak için kullanılacak bir veya birkaç [hedef bildirimi](../deploying/runtime-store.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="9caed-135">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="9caed-136">Bildirim dosyası, [ `dotnet store` komutun](dotnet-store.md)çıktısının bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="9caed-136">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="9caed-137">Birden çok bildirim belirtmek için her bildirim `--manifest` için bir seçenek ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9caed-137">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="9caed-138">Bu seçenek .NET Core 2,0 SDK ile başlayarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9caed-138">This option is available starting with .NET Core 2.0 SDK.</span></span>

`--no-build`

<span data-ttu-id="9caed-139">Yayımlamadan önce projeyi oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="9caed-139">Doesn't build the project before publishing.</span></span> <span data-ttu-id="9caed-140">Ayrıca `--no-restore` bayrağı örtülü olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9caed-140">It also implicitly sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="9caed-141">Projeden projeye başvuruları yoksayar ve yalnızca kök projeyi geri yükler.</span><span class="sxs-lookup"><span data-stu-id="9caed-141">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="9caed-142">Komutu çalıştırılırken örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="9caed-142">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="9caed-143">Çıkış dizini için yolu belirtir.</span><span class="sxs-lookup"><span data-stu-id="9caed-143">Specifies the path for the output directory.</span></span> <span data-ttu-id="9caed-144">Belirtilmemişse, varsayılan olarak *./bin/[Configuration]/[Framework]/Publish/* , çerçeveye bağlı bir dağıtım için veya *./bin/[yapılandırma]/[Framework]/[Runtime]/Publish/* için otomatik olarak kapsanan bir dağıtım için.</span><span class="sxs-lookup"><span data-stu-id="9caed-144">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="9caed-145">Yol göreli ise, oluşturulan çıkış dizini geçerli çalışma dizinine değil, proje dosyası konumuna göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="9caed-145">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`--self-contained`

<span data-ttu-id="9caed-146">.NET Core çalışma zamanını uygulamanızla yayımlar, böylece çalışma zamanının hedef makinede yüklü olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="9caed-146">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="9caed-147">Bir çalışma zamanı tanımlayıcısı belirtilmişse, varsayılan değeri olur `true`.</span><span class="sxs-lookup"><span data-stu-id="9caed-147">If a runtime identifier is specified, its default value is `true`.</span></span> <span data-ttu-id="9caed-148">Farklı dağıtım türleri hakkında daha fazla bilgi için bkz. [.NET Core uygulama dağıtımı](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="9caed-148">For more information about the different deployment types, see [.NET Core application deployment](../deploying/index.md).</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="9caed-149">Uygulamayı belirli bir çalışma zamanı için yayımlar.</span><span class="sxs-lookup"><span data-stu-id="9caed-149">Publishes the application for a given runtime.</span></span> <span data-ttu-id="9caed-150">Bu, [kendinden bağımsız bir dağıtım (SCD)](../deploying/index.md#self-contained-deployments-scd)oluşturulurken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9caed-150">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="9caed-151">Çalışma zamanı tanımlayıcıları (RID 'Ler) listesi için bkz. [RID kataloğu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="9caed-151">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="9caed-152">Varsayılan, [çerçeveye bağımlı bir dağıtımı (FDD)](../deploying/index.md#framework-dependent-deployments-fdd)yayımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="9caed-152">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="9caed-153">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9caed-153">Sets the verbosity level of the command.</span></span> <span data-ttu-id="9caed-154">İzin verilen değerler `q[uiet]` `m[inimal]` ,`n[ormal]`,, ve .`diag[nostic]` `d[etailed]`</span><span class="sxs-lookup"><span data-stu-id="9caed-154">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="9caed-155">Proje dosyasının sürüm alanındaki yıldız işaretini (`*`) değiştirecek olan sürüm sonekini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9caed-155">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="9caed-156">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="9caed-156">.NET Core 2.0</span></span>](#tab/netcore20)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="9caed-157">Yapı yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9caed-157">Defines the build configuration.</span></span> <span data-ttu-id="9caed-158">Varsayılan değer `Debug` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="9caed-158">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="9caed-159">Belirtilen [hedef çerçeve](../../standard/frameworks.md)için uygulamayı yayımlar.</span><span class="sxs-lookup"><span data-stu-id="9caed-159">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="9caed-160">Hedef çerçeveyi proje dosyasında belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9caed-160">You must specify the target framework in the project file.</span></span>

`--force`

<span data-ttu-id="9caed-161">Son geri yükleme başarılı olsa bile tüm bağımlılıkların çözülmesini zorlar.</span><span class="sxs-lookup"><span data-stu-id="9caed-161">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="9caed-162">Bu bayrağın belirtilmesi, *Project. varlıklar. JSON* dosyasını silme ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="9caed-162">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="9caed-163">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="9caed-163">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="9caed-164">Uygulamayla yayımlanmış paket kümesini kırpmak için kullanılacak bir veya birkaç [hedef bildirimi](../deploying/runtime-store.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="9caed-164">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="9caed-165">Bildirim dosyası, [ `dotnet store` komutun](dotnet-store.md)çıktısının bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="9caed-165">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="9caed-166">Birden çok bildirim belirtmek için her bildirim `--manifest` için bir seçenek ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9caed-166">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="9caed-167">Bu seçenek .NET Core 2,0 SDK ile başlayarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9caed-167">This option is available starting with .NET Core 2.0 SDK.</span></span>

`--no-dependencies`

<span data-ttu-id="9caed-168">Projeden projeye başvuruları yoksayar ve yalnızca kök projeyi geri yükler.</span><span class="sxs-lookup"><span data-stu-id="9caed-168">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="9caed-169">Komutu çalıştırılırken örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="9caed-169">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="9caed-170">Çıkış dizini için yolu belirtir.</span><span class="sxs-lookup"><span data-stu-id="9caed-170">Specifies the path for the output directory.</span></span> <span data-ttu-id="9caed-171">Belirtilmemişse, varsayılan olarak *./bin/[Configuration]/[Framework]/Publish/* , çerçeveye bağlı bir dağıtım için veya *./bin/[yapılandırma]/[Framework]/[Runtime]/Publish/* için otomatik olarak kapsanan bir dağıtım için.</span><span class="sxs-lookup"><span data-stu-id="9caed-171">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="9caed-172">Yol göreli ise, oluşturulan çıkış dizini geçerli çalışma dizinine değil, proje dosyası konumuna göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="9caed-172">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`--self-contained`

<span data-ttu-id="9caed-173">.NET Core çalışma zamanını uygulamanızla yayımlar, böylece çalışma zamanının hedef makinede yüklü olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="9caed-173">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="9caed-174">Bir çalışma zamanı tanımlayıcısı belirtilmişse, varsayılan değeri olur `true`.</span><span class="sxs-lookup"><span data-stu-id="9caed-174">If a runtime identifier is specified, its default value is `true`.</span></span> <span data-ttu-id="9caed-175">Farklı dağıtım türleri hakkında daha fazla bilgi için bkz. [.NET Core uygulama dağıtımı](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="9caed-175">For more information about the different deployment types, see [.NET Core application deployment](../deploying/index.md).</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="9caed-176">Uygulamayı belirli bir çalışma zamanı için yayımlar.</span><span class="sxs-lookup"><span data-stu-id="9caed-176">Publishes the application for a given runtime.</span></span> <span data-ttu-id="9caed-177">Bu, [kendinden bağımsız bir dağıtım (SCD)](../deploying/index.md#self-contained-deployments-scd)oluşturulurken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9caed-177">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="9caed-178">Çalışma zamanı tanımlayıcıları (RID 'Ler) listesi için bkz. [RID kataloğu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="9caed-178">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="9caed-179">Varsayılan, [çerçeveye bağımlı bir dağıtımı (FDD)](../deploying/index.md#framework-dependent-deployments-fdd)yayımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="9caed-179">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="9caed-180">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9caed-180">Sets the verbosity level of the command.</span></span> <span data-ttu-id="9caed-181">İzin verilen değerler `q[uiet]` `m[inimal]` ,`n[ormal]`,, ve .`diag[nostic]` `d[etailed]`</span><span class="sxs-lookup"><span data-stu-id="9caed-181">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="9caed-182">Proje dosyasının sürüm alanındaki yıldız işaretini (`*`) değiştirecek olan sürüm sonekini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9caed-182">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="9caed-183">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="9caed-183">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="9caed-184">Yapı yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9caed-184">Defines the build configuration.</span></span> <span data-ttu-id="9caed-185">Varsayılan değer `Debug` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="9caed-185">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="9caed-186">Belirtilen [hedef çerçeve](../../standard/frameworks.md)için uygulamayı yayımlar.</span><span class="sxs-lookup"><span data-stu-id="9caed-186">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="9caed-187">Hedef çerçeveyi proje dosyasında belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9caed-187">You must specify the target framework in the project file.</span></span>

`-h|--help`

<span data-ttu-id="9caed-188">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="9caed-188">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="9caed-189">Uygulamayla yayımlanmış paket kümesini kırpmak için kullanılacak bir veya birkaç [hedef bildirimi](../deploying/runtime-store.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="9caed-189">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="9caed-190">Bildirim dosyası, [ `dotnet store` komutun](dotnet-store.md)çıktısının bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="9caed-190">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="9caed-191">Birden çok bildirim belirtmek için her bildirim `--manifest` için bir seçenek ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9caed-191">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="9caed-192">Bu seçenek .NET Core 2,0 SDK ile başlayarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9caed-192">This option is available starting with .NET Core 2.0 SDK.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="9caed-193">Çıkış dizini için yolu belirtir.</span><span class="sxs-lookup"><span data-stu-id="9caed-193">Specifies the path for the output directory.</span></span> <span data-ttu-id="9caed-194">Belirtilmemişse, varsayılan olarak *./bin/[Configuration]/[Framework]/Publish/* , çerçeveye bağlı bir dağıtım için veya *./bin/[yapılandırma]/[Framework]/[Runtime]/Publish/* için otomatik olarak kapsanan bir dağıtım için.</span><span class="sxs-lookup"><span data-stu-id="9caed-194">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="9caed-195">Yol göreli ise, oluşturulan çıkış dizini geçerli çalışma dizinine değil, proje dosyası konumuna göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="9caed-195">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="9caed-196">Uygulamayı belirli bir çalışma zamanı için yayımlar.</span><span class="sxs-lookup"><span data-stu-id="9caed-196">Publishes the application for a given runtime.</span></span> <span data-ttu-id="9caed-197">Bu, [kendinden bağımsız bir dağıtım (SCD)](../deploying/index.md#self-contained-deployments-scd)oluşturulurken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9caed-197">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="9caed-198">Çalışma zamanı tanımlayıcıları (RID 'Ler) listesi için bkz. [RID kataloğu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="9caed-198">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="9caed-199">Varsayılan, [çerçeveye bağımlı bir dağıtımı (FDD)](../deploying/index.md#framework-dependent-deployments-fdd)yayımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="9caed-199">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="9caed-200">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9caed-200">Sets the verbosity level of the command.</span></span> <span data-ttu-id="9caed-201">İzin verilen değerler `q[uiet]` `m[inimal]` ,`n[ormal]`,, ve .`diag[nostic]` `d[etailed]`</span><span class="sxs-lookup"><span data-stu-id="9caed-201">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="9caed-202">Proje dosyasının sürüm alanındaki yıldız işaretini (`*`) değiştirecek olan sürüm sonekini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9caed-202">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

---

## <a name="examples"></a><span data-ttu-id="9caed-203">Örnekler</span><span class="sxs-lookup"><span data-stu-id="9caed-203">Examples</span></span>

<span data-ttu-id="9caed-204">Projeyi geçerli dizinde yayımlayın:</span><span class="sxs-lookup"><span data-stu-id="9caed-204">Publish the project in the current directory:</span></span>

`dotnet publish`

<span data-ttu-id="9caed-205">Belirtilen proje dosyasını kullanarak uygulamayı yayımlayın:</span><span class="sxs-lookup"><span data-stu-id="9caed-205">Publish the application using the specified project file:</span></span>

`dotnet publish ~/projects/app1/app1.csproj`

<span data-ttu-id="9caed-206">Şu `netcoreapp1.1` Framework 'ü kullanarak projeyi geçerli dizinde yayımlayın:</span><span class="sxs-lookup"><span data-stu-id="9caed-206">Publish the project in the current directory using the `netcoreapp1.1` framework:</span></span>

`dotnet publish --framework netcoreapp1.1`

<span data-ttu-id="9caed-207">`netcoreapp1.1` Çerçevesini ve`OS X 10.10` çalışma zamanını kullanarak geçerli uygulamayı yayımlayın (Bu RID 'yi proje dosyasında listemalısınız).</span><span class="sxs-lookup"><span data-stu-id="9caed-207">Publish the current application using the `netcoreapp1.1` framework and the runtime for `OS X 10.10` (you must list this RID in the project file).</span></span>

`dotnet publish --framework netcoreapp1.1 --runtime osx.10.11-x64`

<span data-ttu-id="9caed-208">Geçerli uygulamayı yayımlayın ancak projeden projeye (P2P) başvurularını geri yüklemeyin, ancak geri yükleme işlemi sırasında yalnızca kök proje (.NET Core SDK 2,0 ve üzeri sürümler):</span><span class="sxs-lookup"><span data-stu-id="9caed-208">Publish the current application but don't restore project-to-project (P2P) references, just the root project during the restore operation (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet publish --no-dependencies`

## <a name="see-also"></a><span data-ttu-id="9caed-209">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9caed-209">See also</span></span>

- [<span data-ttu-id="9caed-210">Hedef çerçeveler</span><span class="sxs-lookup"><span data-stu-id="9caed-210">Target frameworks</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="9caed-211">Çalışma zamanı tanımlayıcı (RID) kataloğu</span><span class="sxs-lookup"><span data-stu-id="9caed-211">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
