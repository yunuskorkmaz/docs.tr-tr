---
title: dotnet publish komutu
description: Dotnet publish komutu .NET Core projenizi bir dizinde yayımlar.
ms.date: 05/29/2018
ms.openlocfilehash: 88dc53d6c45bc18f630d8a7137704e813ad4f0e3
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626079"
---
# <a name="dotnet-publish"></a><span data-ttu-id="6c16a-103">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="6c16a-103">dotnet publish</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="6c16a-104">Adı</span><span class="sxs-lookup"><span data-stu-id="6c16a-104">Name</span></span>

<span data-ttu-id="6c16a-105">uygulama ve bağımlılıklarını bir barındırma sistemine dağıtım için bir klasöre `dotnet publish` paketler.</span><span class="sxs-lookup"><span data-stu-id="6c16a-105">`dotnet publish` - Packs the application and its dependencies into a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="6c16a-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="6c16a-106">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21"></a>[<span data-ttu-id="6c16a-107">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="6c16a-107">.NET Core 2.1</span></span>](#tab/netcore21)

```dotnetcli
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-build] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

# <a name="net-core-20"></a>[<span data-ttu-id="6c16a-108">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="6c16a-108">.NET Core 2.0</span></span>](#tab/netcore20)

```dotnetcli
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

# <a name="net-core-1x"></a>[<span data-ttu-id="6c16a-109">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="6c16a-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
    [--version-suffix]
dotnet publish [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="6c16a-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6c16a-110">Description</span></span>

<span data-ttu-id="6c16a-111">`dotnet publish` uygulamayı derler, proje dosyasında belirtilen bağımlılıklarını okur ve elde edilen dosya kümesini bir dizine yayınlar.</span><span class="sxs-lookup"><span data-stu-id="6c16a-111">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="6c16a-112">Çıktı aşağıdaki varlıkları içerir:</span><span class="sxs-lookup"><span data-stu-id="6c16a-112">The output includes the following assets:</span></span>

- <span data-ttu-id="6c16a-113">*DLL* uzantılı bir derlemede ara DIL (IL) kodu.</span><span class="sxs-lookup"><span data-stu-id="6c16a-113">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
- <span data-ttu-id="6c16a-114">*. Deps. JSON* dosyası, projenin tüm bağımlılıklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="6c16a-114">*.deps.json* file that includes all of the dependencies of the project.</span></span>
- <span data-ttu-id="6c16a-115">uygulamanın beklediği paylaşılan çalışma zamanını belirten *. runtimeconfig. JSON* dosyası, ayrıca çalışma zamanına yönelik diğer yapılandırma seçenekleri (örneğin, çöp toplama türü).</span><span class="sxs-lookup"><span data-stu-id="6c16a-115">*.runtimeconfig.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
- <span data-ttu-id="6c16a-116">NuGet önbelleğinden çıkış klasörüne kopyalanmış olan uygulamanın bağımlılıkları.</span><span class="sxs-lookup"><span data-stu-id="6c16a-116">The application's dependencies, which are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="6c16a-117">`dotnet publish` komutun çıktısı, yürütme için bir barındırma sistemine (örneğin, bir sunucu, PC, Mac, dizüstü bilgisayar) dağıtıma yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="6c16a-117">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution.</span></span> <span data-ttu-id="6c16a-118">Uygulamayı dağıtıma hazırlamak için tek resmi olarak desteklenen bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="6c16a-118">It's the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="6c16a-119">Projenin belirttiği dağıtımın türüne bağlı olarak, barındırma sisteminde .NET Core paylaşılan çalışma zamanı yüklü olabilir veya olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="6c16a-119">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span> <span data-ttu-id="6c16a-120">Daha fazla bilgi için bkz. [.NET Core uygulama dağıtımı](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="6c16a-120">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span> <span data-ttu-id="6c16a-121">Yayımlanan bir uygulamanın dizin yapısı için bkz. [Dizin yapısı](/aspnet/core/hosting/directory-structure).</span><span class="sxs-lookup"><span data-stu-id="6c16a-121">For the directory structure of a published application, see [Directory structure](/aspnet/core/hosting/directory-structure).</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="6c16a-122">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="6c16a-122">Arguments</span></span>

`PROJECT`

<span data-ttu-id="6c16a-123">Yayımlanacak proje.</span><span class="sxs-lookup"><span data-stu-id="6c16a-123">The project to publish.</span></span> <span data-ttu-id="6c16a-124">Bir [C#](csproj.md), F#veya Visual Basic proje dosyasının yolu ve dosya adı ya da C#, F#ya da Visual Basic proje dosyası içeren bir dizinin yolu.</span><span class="sxs-lookup"><span data-stu-id="6c16a-124">It's either the path and filename of a [C#](csproj.md), F#, or Visual Basic project file, or the path to a directory that contains a C#, F#, or Visual Basic project file.</span></span> <span data-ttu-id="6c16a-125">Belirtilmezse, varsayılan olarak geçerli dizini alır.</span><span class="sxs-lookup"><span data-stu-id="6c16a-125">If not specified, it defaults to the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="6c16a-126">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="6c16a-126">Options</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="6c16a-127">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="6c16a-127">.NET Core 2.1</span></span>](#tab/netcore21)

`-c|--configuration <CONFIGURATION>`

<span data-ttu-id="6c16a-128">Yapı yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6c16a-128">Defines the build configuration.</span></span> <span data-ttu-id="6c16a-129">Çoğu proje için varsayılan değer `Debug`, ancak projenizde derleme yapılandırma ayarlarını geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6c16a-129">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="6c16a-130">Belirtilen [hedef çerçeve](../../standard/frameworks.md)için uygulamayı yayımlar.</span><span class="sxs-lookup"><span data-stu-id="6c16a-130">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="6c16a-131">Hedef çerçeveyi proje dosyasında belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6c16a-131">You must specify the target framework in the project file.</span></span>

`--force`

<span data-ttu-id="6c16a-132">Son geri yükleme başarılı olsa bile tüm bağımlılıkların çözülmesini zorlar.</span><span class="sxs-lookup"><span data-stu-id="6c16a-132">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="6c16a-133">Bu bayrağın belirtilmesi, *Project. varlıklar. JSON* dosyasını silme ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="6c16a-133">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="6c16a-134">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="6c16a-134">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="6c16a-135">Uygulamayla yayımlanmış paket kümesini kırpmak için kullanılacak bir veya birkaç [hedef bildirimi](../deploying/runtime-store.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c16a-135">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="6c16a-136">Bildirim dosyası [`dotnet store` komutunun](dotnet-store.md)çıktısının bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="6c16a-136">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="6c16a-137">Birden çok bildirim belirtmek için her bildirim için bir `--manifest` seçeneği ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6c16a-137">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="6c16a-138">Bu seçenek .NET Core 2,0 SDK ile başlayarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6c16a-138">This option is available starting with .NET Core 2.0 SDK.</span></span>

`--no-build`

<span data-ttu-id="6c16a-139">Yayımlamadan önce projeyi oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="6c16a-139">Doesn't build the project before publishing.</span></span> <span data-ttu-id="6c16a-140">Ayrıca `--no-restore` bayrağını örtülü olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6c16a-140">It also implicitly sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="6c16a-141">Projeden projeye başvuruları yoksayar ve yalnızca kök projeyi geri yükler.</span><span class="sxs-lookup"><span data-stu-id="6c16a-141">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="6c16a-142">Komutu çalıştırılırken örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="6c16a-142">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="6c16a-143">Çıkış dizini için yolu belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c16a-143">Specifies the path for the output directory.</span></span> <span data-ttu-id="6c16a-144">Belirtilmemişse, varsayılan olarak *./bin/[Configuration]/[Framework]/Publish/* , çerçeveye bağlı bir dağıtım için veya *./bin/[yapılandırma]/[Framework]/[Runtime]/Publish/* için otomatik olarak kapsanan bir dağıtım için.</span><span class="sxs-lookup"><span data-stu-id="6c16a-144">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="6c16a-145">Yol göreli ise, oluşturulan çıkış dizini geçerli çalışma dizinine değil, proje dosyası konumuna göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="6c16a-145">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`--self-contained`

<span data-ttu-id="6c16a-146">.NET Core çalışma zamanını uygulamanızla yayımlar, böylece çalışma zamanının hedef makinede yüklü olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="6c16a-146">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="6c16a-147">Bir çalışma zamanı tanımlayıcısı belirtilmişse, varsayılan değeri `true`.</span><span class="sxs-lookup"><span data-stu-id="6c16a-147">If a runtime identifier is specified, its default value is `true`.</span></span> <span data-ttu-id="6c16a-148">Farklı dağıtım türleri hakkında daha fazla bilgi için bkz. [.NET Core uygulama dağıtımı](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="6c16a-148">For more information about the different deployment types, see [.NET Core application deployment](../deploying/index.md).</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="6c16a-149">Uygulamayı belirli bir çalışma zamanı için yayımlar.</span><span class="sxs-lookup"><span data-stu-id="6c16a-149">Publishes the application for a given runtime.</span></span> <span data-ttu-id="6c16a-150">Bu, [kendinden bağımsız bir dağıtım (SCD)](../deploying/index.md#publish-self-contained)oluşturulurken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6c16a-150">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#publish-self-contained).</span></span> <span data-ttu-id="6c16a-151">Çalışma zamanı tanımlayıcıları (RID 'Ler) listesi için bkz. [RID kataloğu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="6c16a-151">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="6c16a-152">Varsayılan, [çerçeveye bağımlı bir dağıtımı (FDD)](../deploying/index.md#publish-runtime-dependent)yayımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="6c16a-152">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#publish-runtime-dependent).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="6c16a-153">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6c16a-153">Sets the verbosity level of the command.</span></span> <span data-ttu-id="6c16a-154">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="6c16a-154">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="6c16a-155">Proje dosyasının sürüm alanındaki yıldız işaretini (`*`) değiştirecek sürüm sonekini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6c16a-155">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

# <a name="net-core-20"></a>[<span data-ttu-id="6c16a-156">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="6c16a-156">.NET Core 2.0</span></span>](#tab/netcore20)

`-c|--configuration <CONFIGURATION>`

<span data-ttu-id="6c16a-157">Yapı yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6c16a-157">Defines the build configuration.</span></span> <span data-ttu-id="6c16a-158">Çoğu proje için varsayılan değer `Debug`, ancak projenizde derleme yapılandırma ayarlarını geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6c16a-158">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="6c16a-159">Belirtilen [hedef çerçeve](../../standard/frameworks.md)için uygulamayı yayımlar.</span><span class="sxs-lookup"><span data-stu-id="6c16a-159">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="6c16a-160">Hedef çerçeveyi proje dosyasında belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6c16a-160">You must specify the target framework in the project file.</span></span>

`--force`

<span data-ttu-id="6c16a-161">Son geri yükleme başarılı olsa bile tüm bağımlılıkların çözülmesini zorlar.</span><span class="sxs-lookup"><span data-stu-id="6c16a-161">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="6c16a-162">Bu bayrağın belirtilmesi, *Project. varlıklar. JSON* dosyasını silme ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="6c16a-162">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="6c16a-163">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="6c16a-163">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="6c16a-164">Uygulamayla yayımlanmış paket kümesini kırpmak için kullanılacak bir veya birkaç [hedef bildirimi](../deploying/runtime-store.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c16a-164">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="6c16a-165">Bildirim dosyası [`dotnet store` komutunun](dotnet-store.md)çıktısının bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="6c16a-165">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="6c16a-166">Birden çok bildirim belirtmek için her bildirim için bir `--manifest` seçeneği ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6c16a-166">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="6c16a-167">Bu seçenek .NET Core 2,0 SDK ile başlayarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6c16a-167">This option is available starting with .NET Core 2.0 SDK.</span></span>

`--no-dependencies`

<span data-ttu-id="6c16a-168">Projeden projeye başvuruları yoksayar ve yalnızca kök projeyi geri yükler.</span><span class="sxs-lookup"><span data-stu-id="6c16a-168">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="6c16a-169">Komutu çalıştırılırken örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="6c16a-169">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="6c16a-170">Çıkış dizini için yolu belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c16a-170">Specifies the path for the output directory.</span></span> <span data-ttu-id="6c16a-171">Belirtilmemişse, varsayılan olarak *./bin/[Configuration]/[Framework]/Publish/* , çerçeveye bağlı bir dağıtım için veya *./bin/[yapılandırma]/[Framework]/[Runtime]/Publish/* için otomatik olarak kapsanan bir dağıtım için.</span><span class="sxs-lookup"><span data-stu-id="6c16a-171">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="6c16a-172">Yol göreli ise, oluşturulan çıkış dizini geçerli çalışma dizinine değil, proje dosyası konumuna göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="6c16a-172">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`--self-contained`

<span data-ttu-id="6c16a-173">.NET Core çalışma zamanını uygulamanızla yayımlar, böylece çalışma zamanının hedef makinede yüklü olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="6c16a-173">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="6c16a-174">Bir çalışma zamanı tanımlayıcısı belirtilmişse, varsayılan değeri `true`.</span><span class="sxs-lookup"><span data-stu-id="6c16a-174">If a runtime identifier is specified, its default value is `true`.</span></span> <span data-ttu-id="6c16a-175">Farklı dağıtım türleri hakkında daha fazla bilgi için bkz. [.NET Core uygulama dağıtımı](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="6c16a-175">For more information about the different deployment types, see [.NET Core application deployment](../deploying/index.md).</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="6c16a-176">Uygulamayı belirli bir çalışma zamanı için yayımlar.</span><span class="sxs-lookup"><span data-stu-id="6c16a-176">Publishes the application for a given runtime.</span></span> <span data-ttu-id="6c16a-177">Bu, [kendinden bağımsız bir dağıtım (SCD)](../deploying/index.md#publish-self-contained)oluşturulurken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6c16a-177">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#publish-self-contained).</span></span> <span data-ttu-id="6c16a-178">Çalışma zamanı tanımlayıcıları (RID 'Ler) listesi için bkz. [RID kataloğu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="6c16a-178">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="6c16a-179">Varsayılan, [çerçeveye bağımlı bir dağıtımı (FDD)](../deploying/index.md#publish-runtime-dependent)yayımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="6c16a-179">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#publish-runtime-dependent).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="6c16a-180">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6c16a-180">Sets the verbosity level of the command.</span></span> <span data-ttu-id="6c16a-181">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="6c16a-181">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="6c16a-182">Proje dosyasının sürüm alanındaki yıldız işaretini (`*`) değiştirecek sürüm sonekini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6c16a-182">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

# <a name="net-core-1x"></a>[<span data-ttu-id="6c16a-183">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="6c16a-183">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration <CONFIGURATION>`

<span data-ttu-id="6c16a-184">Yapı yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6c16a-184">Defines the build configuration.</span></span> <span data-ttu-id="6c16a-185">Çoğu proje için varsayılan değer `Debug`, ancak projenizde derleme yapılandırma ayarlarını geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6c16a-185">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="6c16a-186">Belirtilen [hedef çerçeve](../../standard/frameworks.md)için uygulamayı yayımlar.</span><span class="sxs-lookup"><span data-stu-id="6c16a-186">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="6c16a-187">Hedef çerçeveyi proje dosyasında belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6c16a-187">You must specify the target framework in the project file.</span></span>

`-h|--help`

<span data-ttu-id="6c16a-188">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="6c16a-188">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="6c16a-189">Uygulamayla yayımlanmış paket kümesini kırpmak için kullanılacak bir veya birkaç [hedef bildirimi](../deploying/runtime-store.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c16a-189">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="6c16a-190">Bildirim dosyası [`dotnet store` komutunun](dotnet-store.md)çıktısının bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="6c16a-190">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="6c16a-191">Birden çok bildirim belirtmek için her bildirim için bir `--manifest` seçeneği ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6c16a-191">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="6c16a-192">Bu seçenek .NET Core 2,0 SDK ile başlayarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6c16a-192">This option is available starting with .NET Core 2.0 SDK.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="6c16a-193">Çıkış dizini için yolu belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c16a-193">Specifies the path for the output directory.</span></span> <span data-ttu-id="6c16a-194">Belirtilmemişse, varsayılan olarak *./bin/[Configuration]/[Framework]/Publish/* , çerçeveye bağlı bir dağıtım için veya *./bin/[yapılandırma]/[Framework]/[Runtime]/Publish/* için otomatik olarak kapsanan bir dağıtım için.</span><span class="sxs-lookup"><span data-stu-id="6c16a-194">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="6c16a-195">Yol göreli ise, oluşturulan çıkış dizini geçerli çalışma dizinine değil, proje dosyası konumuna göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="6c16a-195">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="6c16a-196">Uygulamayı belirli bir çalışma zamanı için yayımlar.</span><span class="sxs-lookup"><span data-stu-id="6c16a-196">Publishes the application for a given runtime.</span></span> <span data-ttu-id="6c16a-197">Bu, [kendinden bağımsız bir dağıtım (SCD)](../deploying/index.md#publish-self-contained)oluşturulurken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6c16a-197">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#publish-self-contained).</span></span> <span data-ttu-id="6c16a-198">Çalışma zamanı tanımlayıcıları (RID 'Ler) listesi için bkz. [RID kataloğu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="6c16a-198">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="6c16a-199">Varsayılan, [çerçeveye bağımlı bir dağıtımı (FDD)](../deploying/index.md#publish-runtime-dependent)yayımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="6c16a-199">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#publish-runtime-dependent).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="6c16a-200">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6c16a-200">Sets the verbosity level of the command.</span></span> <span data-ttu-id="6c16a-201">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="6c16a-201">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="6c16a-202">Proje dosyasının sürüm alanındaki yıldız işaretini (`*`) değiştirecek sürüm sonekini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6c16a-202">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

---

## <a name="examples"></a><span data-ttu-id="6c16a-203">Örnekler</span><span class="sxs-lookup"><span data-stu-id="6c16a-203">Examples</span></span>

<span data-ttu-id="6c16a-204">Projeyi geçerli dizinde yayımlayın:</span><span class="sxs-lookup"><span data-stu-id="6c16a-204">Publish the project in the current directory:</span></span>

`dotnet publish`

<span data-ttu-id="6c16a-205">Belirtilen proje dosyasını kullanarak uygulamayı yayımlayın:</span><span class="sxs-lookup"><span data-stu-id="6c16a-205">Publish the application using the specified project file:</span></span>

`dotnet publish ~/projects/app1/app1.csproj`

<span data-ttu-id="6c16a-206">`netcoreapp1.1` çerçevesini kullanarak projeyi geçerli dizinde yayımlayın:</span><span class="sxs-lookup"><span data-stu-id="6c16a-206">Publish the project in the current directory using the `netcoreapp1.1` framework:</span></span>

`dotnet publish --framework netcoreapp1.1`

<span data-ttu-id="6c16a-207">`netcoreapp1.1` çerçevesini ve `OS X 10.10` çalışma zamanını kullanarak geçerli uygulamayı yayımlayın (Bu RID 'yi proje dosyasında listemalısınız).</span><span class="sxs-lookup"><span data-stu-id="6c16a-207">Publish the current application using the `netcoreapp1.1` framework and the runtime for `OS X 10.10` (you must list this RID in the project file).</span></span>

`dotnet publish --framework netcoreapp1.1 --runtime osx.10.11-x64`

<span data-ttu-id="6c16a-208">Geçerli uygulamayı yayımlayın ancak projeden projeye (P2P) başvurularını geri yüklemeyin, ancak geri yükleme işlemi sırasında yalnızca kök proje (.NET Core SDK 2,0 ve üzeri sürümler):</span><span class="sxs-lookup"><span data-stu-id="6c16a-208">Publish the current application but don't restore project-to-project (P2P) references, just the root project during the restore operation (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet publish --no-dependencies`

## <a name="see-also"></a><span data-ttu-id="6c16a-209">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6c16a-209">See also</span></span>

- [<span data-ttu-id="6c16a-210">Hedef çerçeveler</span><span class="sxs-lookup"><span data-stu-id="6c16a-210">Target frameworks</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="6c16a-211">Çalışma zamanı tanımlayıcı (RID) kataloğu</span><span class="sxs-lookup"><span data-stu-id="6c16a-211">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
