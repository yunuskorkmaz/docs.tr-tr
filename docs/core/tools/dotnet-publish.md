---
title: dotnet publish komutu
description: Dotnet publish komutu .NET Core projenizi bir dizinde yayımlar.
ms.date: 05/29/2018
ms.openlocfilehash: 0653a7b1e1abd6d7ffd3d21a0410279235b43a28
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451298"
---
# <a name="dotnet-publish"></a><span data-ttu-id="2833f-103">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="2833f-103">dotnet publish</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="2833f-104">Name</span><span class="sxs-lookup"><span data-stu-id="2833f-104">Name</span></span>

<span data-ttu-id="2833f-105">uygulama ve bağımlılıklarını bir barındırma sistemine dağıtım için bir klasöre `dotnet publish` paketler.</span><span class="sxs-lookup"><span data-stu-id="2833f-105">`dotnet publish` - Packs the application and its dependencies into a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="2833f-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="2833f-106">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21"></a>[<span data-ttu-id="2833f-107">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="2833f-107">.NET Core 2.1</span></span>](#tab/netcore21)

```dotnetcli
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-build] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

# <a name="net-core-20"></a>[<span data-ttu-id="2833f-108">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="2833f-108">.NET Core 2.0</span></span>](#tab/netcore20)

```dotnetcli
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

# <a name="net-core-1x"></a>[<span data-ttu-id="2833f-109">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="2833f-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
    [--version-suffix]
dotnet publish [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="2833f-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2833f-110">Description</span></span>

<span data-ttu-id="2833f-111">`dotnet publish` uygulamayı derler, proje dosyasında belirtilen bağımlılıklarını okur ve elde edilen dosya kümesini bir dizine yayınlar.</span><span class="sxs-lookup"><span data-stu-id="2833f-111">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="2833f-112">Çıktı aşağıdaki varlıkları içerir:</span><span class="sxs-lookup"><span data-stu-id="2833f-112">The output includes the following assets:</span></span>

- <span data-ttu-id="2833f-113">*DLL* uzantılı bir derlemede ara DIL (IL) kodu.</span><span class="sxs-lookup"><span data-stu-id="2833f-113">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
- <span data-ttu-id="2833f-114">*. Deps. JSON* dosyası, projenin tüm bağımlılıklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="2833f-114">*.deps.json* file that includes all of the dependencies of the project.</span></span>
- <span data-ttu-id="2833f-115">uygulamanın beklediği paylaşılan çalışma zamanını belirten *. runtimeconfig. JSON* dosyası, ayrıca çalışma zamanına yönelik diğer yapılandırma seçenekleri (örneğin, çöp toplama türü).</span><span class="sxs-lookup"><span data-stu-id="2833f-115">*.runtimeconfig.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
- <span data-ttu-id="2833f-116">NuGet önbelleğinden çıkış klasörüne kopyalanmış olan uygulamanın bağımlılıkları.</span><span class="sxs-lookup"><span data-stu-id="2833f-116">The application's dependencies, which are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="2833f-117">`dotnet publish` komutun çıktısı, yürütme için bir barındırma sistemine (örneğin, bir sunucu, PC, Mac, dizüstü bilgisayar) dağıtıma yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="2833f-117">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution.</span></span> <span data-ttu-id="2833f-118">Uygulamayı dağıtıma hazırlamak için tek resmi olarak desteklenen bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="2833f-118">It's the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="2833f-119">Projenin belirttiği dağıtımın türüne bağlı olarak, barındırma sisteminde .NET Core paylaşılan çalışma zamanı yüklü olabilir veya olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="2833f-119">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span> <span data-ttu-id="2833f-120">Daha fazla bilgi için bkz. [.NET Core uygulama dağıtımı](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="2833f-120">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span> <span data-ttu-id="2833f-121">Yayımlanan bir uygulamanın dizin yapısı için bkz. [Dizin yapısı](/aspnet/core/hosting/directory-structure).</span><span class="sxs-lookup"><span data-stu-id="2833f-121">For the directory structure of a published application, see [Directory structure](/aspnet/core/hosting/directory-structure).</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="2833f-122">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="2833f-122">Arguments</span></span>

`PROJECT`

<span data-ttu-id="2833f-123">Yayımlanacak proje.</span><span class="sxs-lookup"><span data-stu-id="2833f-123">The project to publish.</span></span> <span data-ttu-id="2833f-124">Bir [C#](csproj.md), F#veya Visual Basic proje dosyasının yolu ve dosya adı ya da C#, F#ya da Visual Basic proje dosyası içeren bir dizinin yolu.</span><span class="sxs-lookup"><span data-stu-id="2833f-124">It's either the path and filename of a [C#](csproj.md), F#, or Visual Basic project file, or the path to a directory that contains a C#, F#, or Visual Basic project file.</span></span> <span data-ttu-id="2833f-125">Belirtilmezse, varsayılan olarak geçerli dizini alır.</span><span class="sxs-lookup"><span data-stu-id="2833f-125">If not specified, it defaults to the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="2833f-126">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="2833f-126">Options</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="2833f-127">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="2833f-127">.NET Core 2.1</span></span>](#tab/netcore21)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="2833f-128">Yapı yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2833f-128">Defines the build configuration.</span></span> <span data-ttu-id="2833f-129">Varsayılan değer `Debug` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="2833f-129">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="2833f-130">Belirtilen [hedef çerçeve](../../standard/frameworks.md)için uygulamayı yayımlar.</span><span class="sxs-lookup"><span data-stu-id="2833f-130">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="2833f-131">Hedef çerçeveyi proje dosyasında belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2833f-131">You must specify the target framework in the project file.</span></span>

`--force`

<span data-ttu-id="2833f-132">Son geri yükleme başarılı olsa bile tüm bağımlılıkların çözülmesini zorlar.</span><span class="sxs-lookup"><span data-stu-id="2833f-132">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="2833f-133">Bu bayrağın belirtilmesi, *Project. varlıklar. JSON* dosyasını silme ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="2833f-133">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="2833f-134">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="2833f-134">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="2833f-135">Uygulamayla yayımlanmış paket kümesini kırpmak için kullanılacak bir veya birkaç [hedef bildirimi](../deploying/runtime-store.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="2833f-135">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="2833f-136">Bildirim dosyası [`dotnet store` komutunun](dotnet-store.md)çıktısının bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="2833f-136">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="2833f-137">Birden çok bildirim belirtmek için her bildirim için bir `--manifest` seçeneği ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2833f-137">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="2833f-138">Bu seçenek .NET Core 2,0 SDK ile başlayarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2833f-138">This option is available starting with .NET Core 2.0 SDK.</span></span>

`--no-build`

<span data-ttu-id="2833f-139">Yayımlamadan önce projeyi oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="2833f-139">Doesn't build the project before publishing.</span></span> <span data-ttu-id="2833f-140">Ayrıca `--no-restore` bayrağını örtülü olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2833f-140">It also implicitly sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="2833f-141">Projeden projeye başvuruları yoksayar ve yalnızca kök projeyi geri yükler.</span><span class="sxs-lookup"><span data-stu-id="2833f-141">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="2833f-142">Komutu çalıştırılırken örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="2833f-142">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="2833f-143">Çıkış dizini için yolu belirtir.</span><span class="sxs-lookup"><span data-stu-id="2833f-143">Specifies the path for the output directory.</span></span> <span data-ttu-id="2833f-144">Belirtilmemişse, varsayılan olarak *./bin/[Configuration]/[Framework]/Publish/* , çerçeveye bağlı bir dağıtım için veya *./bin/[yapılandırma]/[Framework]/[Runtime]/Publish/* için otomatik olarak kapsanan bir dağıtım için.</span><span class="sxs-lookup"><span data-stu-id="2833f-144">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="2833f-145">Yol göreli ise, oluşturulan çıkış dizini geçerli çalışma dizinine değil, proje dosyası konumuna göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="2833f-145">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`--self-contained`

<span data-ttu-id="2833f-146">.NET Core çalışma zamanını uygulamanızla yayımlar, böylece çalışma zamanının hedef makinede yüklü olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="2833f-146">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="2833f-147">Bir çalışma zamanı tanımlayıcısı belirtilmişse, varsayılan değeri `true`.</span><span class="sxs-lookup"><span data-stu-id="2833f-147">If a runtime identifier is specified, its default value is `true`.</span></span> <span data-ttu-id="2833f-148">Farklı dağıtım türleri hakkında daha fazla bilgi için bkz. [.NET Core uygulama dağıtımı](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="2833f-148">For more information about the different deployment types, see [.NET Core application deployment](../deploying/index.md).</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="2833f-149">Uygulamayı belirli bir çalışma zamanı için yayımlar.</span><span class="sxs-lookup"><span data-stu-id="2833f-149">Publishes the application for a given runtime.</span></span> <span data-ttu-id="2833f-150">Bu, [kendinden bağımsız bir dağıtım (SCD)](../deploying/index.md#publish-self-contained)oluşturulurken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2833f-150">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#publish-self-contained).</span></span> <span data-ttu-id="2833f-151">Çalışma zamanı tanımlayıcıları (RID 'Ler) listesi için bkz. [RID kataloğu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="2833f-151">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="2833f-152">Varsayılan, [çerçeveye bağımlı bir dağıtımı (FDD)](../deploying/index.md#publish-runtime-dependent)yayımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="2833f-152">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#publish-runtime-dependent).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="2833f-153">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2833f-153">Sets the verbosity level of the command.</span></span> <span data-ttu-id="2833f-154">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="2833f-154">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="2833f-155">Proje dosyasının sürüm alanındaki yıldız işaretini (`*`) değiştirecek sürüm sonekini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2833f-155">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

# <a name="net-core-20"></a>[<span data-ttu-id="2833f-156">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="2833f-156">.NET Core 2.0</span></span>](#tab/netcore20)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="2833f-157">Yapı yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2833f-157">Defines the build configuration.</span></span> <span data-ttu-id="2833f-158">Varsayılan değer `Debug` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="2833f-158">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="2833f-159">Belirtilen [hedef çerçeve](../../standard/frameworks.md)için uygulamayı yayımlar.</span><span class="sxs-lookup"><span data-stu-id="2833f-159">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="2833f-160">Hedef çerçeveyi proje dosyasında belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2833f-160">You must specify the target framework in the project file.</span></span>

`--force`

<span data-ttu-id="2833f-161">Son geri yükleme başarılı olsa bile tüm bağımlılıkların çözülmesini zorlar.</span><span class="sxs-lookup"><span data-stu-id="2833f-161">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="2833f-162">Bu bayrağın belirtilmesi, *Project. varlıklar. JSON* dosyasını silme ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="2833f-162">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="2833f-163">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="2833f-163">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="2833f-164">Uygulamayla yayımlanmış paket kümesini kırpmak için kullanılacak bir veya birkaç [hedef bildirimi](../deploying/runtime-store.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="2833f-164">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="2833f-165">Bildirim dosyası [`dotnet store` komutunun](dotnet-store.md)çıktısının bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="2833f-165">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="2833f-166">Birden çok bildirim belirtmek için her bildirim için bir `--manifest` seçeneği ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2833f-166">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="2833f-167">Bu seçenek .NET Core 2,0 SDK ile başlayarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2833f-167">This option is available starting with .NET Core 2.0 SDK.</span></span>

`--no-dependencies`

<span data-ttu-id="2833f-168">Projeden projeye başvuruları yoksayar ve yalnızca kök projeyi geri yükler.</span><span class="sxs-lookup"><span data-stu-id="2833f-168">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="2833f-169">Komutu çalıştırılırken örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="2833f-169">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="2833f-170">Çıkış dizini için yolu belirtir.</span><span class="sxs-lookup"><span data-stu-id="2833f-170">Specifies the path for the output directory.</span></span> <span data-ttu-id="2833f-171">Belirtilmemişse, varsayılan olarak *./bin/[Configuration]/[Framework]/Publish/* , çerçeveye bağlı bir dağıtım için veya *./bin/[yapılandırma]/[Framework]/[Runtime]/Publish/* için otomatik olarak kapsanan bir dağıtım için.</span><span class="sxs-lookup"><span data-stu-id="2833f-171">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="2833f-172">Yol göreli ise, oluşturulan çıkış dizini geçerli çalışma dizinine değil, proje dosyası konumuna göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="2833f-172">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`--self-contained`

<span data-ttu-id="2833f-173">.NET Core çalışma zamanını uygulamanızla yayımlar, böylece çalışma zamanının hedef makinede yüklü olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="2833f-173">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="2833f-174">Bir çalışma zamanı tanımlayıcısı belirtilmişse, varsayılan değeri `true`.</span><span class="sxs-lookup"><span data-stu-id="2833f-174">If a runtime identifier is specified, its default value is `true`.</span></span> <span data-ttu-id="2833f-175">Farklı dağıtım türleri hakkında daha fazla bilgi için bkz. [.NET Core uygulama dağıtımı](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="2833f-175">For more information about the different deployment types, see [.NET Core application deployment](../deploying/index.md).</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="2833f-176">Uygulamayı belirli bir çalışma zamanı için yayımlar.</span><span class="sxs-lookup"><span data-stu-id="2833f-176">Publishes the application for a given runtime.</span></span> <span data-ttu-id="2833f-177">Bu, [kendinden bağımsız bir dağıtım (SCD)](../deploying/index.md#publish-self-contained)oluşturulurken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2833f-177">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#publish-self-contained).</span></span> <span data-ttu-id="2833f-178">Çalışma zamanı tanımlayıcıları (RID 'Ler) listesi için bkz. [RID kataloğu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="2833f-178">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="2833f-179">Varsayılan, [çerçeveye bağımlı bir dağıtımı (FDD)](../deploying/index.md#publish-runtime-dependent)yayımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="2833f-179">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#publish-runtime-dependent).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="2833f-180">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2833f-180">Sets the verbosity level of the command.</span></span> <span data-ttu-id="2833f-181">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="2833f-181">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="2833f-182">Proje dosyasının sürüm alanındaki yıldız işaretini (`*`) değiştirecek sürüm sonekini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2833f-182">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

# <a name="net-core-1x"></a>[<span data-ttu-id="2833f-183">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="2833f-183">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="2833f-184">Yapı yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2833f-184">Defines the build configuration.</span></span> <span data-ttu-id="2833f-185">Varsayılan değer `Debug` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="2833f-185">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="2833f-186">Belirtilen [hedef çerçeve](../../standard/frameworks.md)için uygulamayı yayımlar.</span><span class="sxs-lookup"><span data-stu-id="2833f-186">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="2833f-187">Hedef çerçeveyi proje dosyasında belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2833f-187">You must specify the target framework in the project file.</span></span>

`-h|--help`

<span data-ttu-id="2833f-188">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="2833f-188">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="2833f-189">Uygulamayla yayımlanmış paket kümesini kırpmak için kullanılacak bir veya birkaç [hedef bildirimi](../deploying/runtime-store.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="2833f-189">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="2833f-190">Bildirim dosyası [`dotnet store` komutunun](dotnet-store.md)çıktısının bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="2833f-190">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="2833f-191">Birden çok bildirim belirtmek için her bildirim için bir `--manifest` seçeneği ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2833f-191">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="2833f-192">Bu seçenek .NET Core 2,0 SDK ile başlayarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2833f-192">This option is available starting with .NET Core 2.0 SDK.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="2833f-193">Çıkış dizini için yolu belirtir.</span><span class="sxs-lookup"><span data-stu-id="2833f-193">Specifies the path for the output directory.</span></span> <span data-ttu-id="2833f-194">Belirtilmemişse, varsayılan olarak *./bin/[Configuration]/[Framework]/Publish/* , çerçeveye bağlı bir dağıtım için veya *./bin/[yapılandırma]/[Framework]/[Runtime]/Publish/* için otomatik olarak kapsanan bir dağıtım için.</span><span class="sxs-lookup"><span data-stu-id="2833f-194">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="2833f-195">Yol göreli ise, oluşturulan çıkış dizini geçerli çalışma dizinine değil, proje dosyası konumuna göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="2833f-195">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="2833f-196">Uygulamayı belirli bir çalışma zamanı için yayımlar.</span><span class="sxs-lookup"><span data-stu-id="2833f-196">Publishes the application for a given runtime.</span></span> <span data-ttu-id="2833f-197">Bu, [kendinden bağımsız bir dağıtım (SCD)](../deploying/index.md#publish-self-contained)oluşturulurken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2833f-197">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#publish-self-contained).</span></span> <span data-ttu-id="2833f-198">Çalışma zamanı tanımlayıcıları (RID 'Ler) listesi için bkz. [RID kataloğu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="2833f-198">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="2833f-199">Varsayılan, [çerçeveye bağımlı bir dağıtımı (FDD)](../deploying/index.md#publish-runtime-dependent)yayımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="2833f-199">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#publish-runtime-dependent).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="2833f-200">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2833f-200">Sets the verbosity level of the command.</span></span> <span data-ttu-id="2833f-201">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="2833f-201">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="2833f-202">Proje dosyasının sürüm alanındaki yıldız işaretini (`*`) değiştirecek sürüm sonekini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2833f-202">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

---

## <a name="examples"></a><span data-ttu-id="2833f-203">Örnekler</span><span class="sxs-lookup"><span data-stu-id="2833f-203">Examples</span></span>

<span data-ttu-id="2833f-204">Projeyi geçerli dizinde yayımlayın:</span><span class="sxs-lookup"><span data-stu-id="2833f-204">Publish the project in the current directory:</span></span>

`dotnet publish`

<span data-ttu-id="2833f-205">Belirtilen proje dosyasını kullanarak uygulamayı yayımlayın:</span><span class="sxs-lookup"><span data-stu-id="2833f-205">Publish the application using the specified project file:</span></span>

`dotnet publish ~/projects/app1/app1.csproj`

<span data-ttu-id="2833f-206">`netcoreapp1.1` çerçevesini kullanarak projeyi geçerli dizinde yayımlayın:</span><span class="sxs-lookup"><span data-stu-id="2833f-206">Publish the project in the current directory using the `netcoreapp1.1` framework:</span></span>

`dotnet publish --framework netcoreapp1.1`

<span data-ttu-id="2833f-207">`netcoreapp1.1` çerçevesini ve `OS X 10.10` çalışma zamanını kullanarak geçerli uygulamayı yayımlayın (Bu RID 'yi proje dosyasında listemalısınız).</span><span class="sxs-lookup"><span data-stu-id="2833f-207">Publish the current application using the `netcoreapp1.1` framework and the runtime for `OS X 10.10` (you must list this RID in the project file).</span></span>

`dotnet publish --framework netcoreapp1.1 --runtime osx.10.11-x64`

<span data-ttu-id="2833f-208">Geçerli uygulamayı yayımlayın ancak projeden projeye (P2P) başvurularını geri yüklemeyin, ancak geri yükleme işlemi sırasında yalnızca kök proje (.NET Core SDK 2,0 ve üzeri sürümler):</span><span class="sxs-lookup"><span data-stu-id="2833f-208">Publish the current application but don't restore project-to-project (P2P) references, just the root project during the restore operation (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet publish --no-dependencies`

## <a name="see-also"></a><span data-ttu-id="2833f-209">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2833f-209">See also</span></span>

- [<span data-ttu-id="2833f-210">Hedef çerçeveler</span><span class="sxs-lookup"><span data-stu-id="2833f-210">Target frameworks</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="2833f-211">Çalışma zamanı tanımlayıcı (RID) kataloğu</span><span class="sxs-lookup"><span data-stu-id="2833f-211">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
