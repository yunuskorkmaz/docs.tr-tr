---
title: dotnet restore komutu
description: Dotnet restore komutuyla bağımlılıkları ve projeye özel araçları nasıl geri yükleyeceğinizi öğrenin.
ms.date: 05/29/2018
ms.openlocfilehash: dc73b7b2482d25872be922e68103fb86067146f7
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920557"
---
# <a name="dotnet-restore"></a><span data-ttu-id="1cc8d-103">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="1cc8d-103">dotnet restore</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="1cc8d-104">Name</span><span class="sxs-lookup"><span data-stu-id="1cc8d-104">Name</span></span>

<span data-ttu-id="1cc8d-105">`dotnet restore`-bir projenin bağımlılıklarını ve araçlarını geri yükler.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-105">`dotnet restore` - Restores the dependencies and tools of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="1cc8d-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="1cc8d-106">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="1cc8d-107">.NET Core 2. x</span><span class="sxs-lookup"><span data-stu-id="1cc8d-107">.NET Core 2.x</span></span>](#tab/netcore2x)

```dotnetcli
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--force] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity] [--interactive]
dotnet restore [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="1cc8d-108">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="1cc8d-108">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="1cc8d-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1cc8d-109">Description</span></span>

<span data-ttu-id="1cc8d-110">`dotnet restore` komutu,, bağımlılıkları geri yüklemek için NuGet kullanır ve proje dosyasında belirtilen projeye özgü araçlardır.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-110">The `dotnet restore` command uses NuGet to restore dependencies as well as project-specific tools that are specified in the project file.</span></span> <span data-ttu-id="1cc8d-111">Varsayılan olarak, bağımlılıklar ve araçların geri yüklenmesi paralel olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-111">By default, the restoration of dependencies and tools are executed in parallel.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="1cc8d-112">Bağımlılıkları geri yüklemek için, NuGet paketlerin bulunduğu akışlara ihtiyaç duyuyor.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-112">To restore the dependencies, NuGet needs the feeds where the packages are located.</span></span> <span data-ttu-id="1cc8d-113">Akışlar genellikle *NuGet. config* yapılandırma dosyası aracılığıyla sağlanır.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-113">Feeds are usually provided via the *nuget.config* configuration file.</span></span> <span data-ttu-id="1cc8d-114">.NET Core SDK yüklendiğinde varsayılan bir yapılandırma dosyası sağlanır.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-114">A default configuration file is provided when the .NET Core SDK is installed.</span></span> <span data-ttu-id="1cc8d-115">Proje dizininde kendi *NuGet. config* dosyanızı oluşturarak ek akışlar belirlersiniz.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-115">You specify additional feeds by creating your own *nuget.config* file in the project directory.</span></span> <span data-ttu-id="1cc8d-116">*NuGet. config* akışlarını `-s` seçeneği ile geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-116">You can override the *nuget.config* feeds with the `-s` option.</span></span>

<span data-ttu-id="1cc8d-117">Bağımlılıklar için, geri yükleme işlemi sırasında `--packages` bağımsız değişkenini kullanarak geri yüklenen paketlerin nereye yerleştirileceğini belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-117">For dependencies, you specify where the restored packages are placed during the restore operation using the `--packages` argument.</span></span> <span data-ttu-id="1cc8d-118">Belirtilmezse, varsayılan NuGet paketi önbelleği kullanılır ve bu, kullanıcının tüm işletim sistemlerindeki giriş dizinindeki `.nuget/packages` dizininde bulunur.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-118">If not specified, the default NuGet package cache is used, which is found in the `.nuget/packages` directory in the user's home directory on all operating systems.</span></span> <span data-ttu-id="1cc8d-119">Örneğin, Linux üzerinde */home/user1* veya Windows üzerinde *c:\Users\User1* .</span><span class="sxs-lookup"><span data-stu-id="1cc8d-119">For example, */home/user1* on Linux or *C:\Users\user1* on Windows.</span></span>

<span data-ttu-id="1cc8d-120">Projeye özgü araçlar için `dotnet restore` önce aracın paketlenmesi gereken paketi geri yükler, sonra da araç bağımlılıklarını proje dosyasında belirtilen şekilde geri yüklemeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-120">For project-specific tooling, `dotnet restore` first restores the package in which the tool is packed, and then proceeds to restore the tool's dependencies as specified in its project file.</span></span>

### <a name="nugetconfig-differences"></a><span data-ttu-id="1cc8d-121">NuGet. config farklılıkları</span><span class="sxs-lookup"><span data-stu-id="1cc8d-121">nuget.config differences</span></span>

<span data-ttu-id="1cc8d-122">`dotnet restore` komutunun davranışı, varsa *NuGet. config* dosyasındaki ayarlardan etkilenir.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-122">The behavior of the `dotnet restore` command is affected by the settings in the *nuget.config* file, if present.</span></span> <span data-ttu-id="1cc8d-123">Örneğin, *NuGet. config* dosyasındaki `globalPackagesFolder` ayarlamak, geri yüklenen NuGet paketlerini belirtilen klasöre koyar.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-123">For example, setting the `globalPackagesFolder` in *nuget.config* places the restored NuGet packages in the specified folder.</span></span> <span data-ttu-id="1cc8d-124">Bu, `dotnet restore` komutunda `--packages` seçeneğinin belirtilmesine alternatiftir.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-124">This is an alternative to specifying the `--packages` option on the `dotnet restore` command.</span></span> <span data-ttu-id="1cc8d-125">Daha fazla bilgi için bkz. [NuGet. config başvurusu](/nuget/schema/nuget-config-file).</span><span class="sxs-lookup"><span data-stu-id="1cc8d-125">For more information, see the [nuget.config reference](/nuget/schema/nuget-config-file).</span></span>

<span data-ttu-id="1cc8d-126">`dotnet restore` göz ardı eden üç özel ayar vardır:</span><span class="sxs-lookup"><span data-stu-id="1cc8d-126">There are three specific settings that `dotnet restore` ignores:</span></span>

- [<span data-ttu-id="1cc8d-127">Bindingyönlendirmeler</span><span class="sxs-lookup"><span data-stu-id="1cc8d-127">bindingRedirects</span></span>](/nuget/schema/nuget-config-file#bindingredirects-section)

  <span data-ttu-id="1cc8d-128">Bağlama yeniden yönlendirmeleri `<PackageReference>` öğeleriyle çalışmaz ve .NET Core yalnızca NuGet paketleri için `<PackageReference>` öğelerini destekler.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-128">Binding redirects don't work with `<PackageReference>` elements and .NET Core only supports `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="1cc8d-129">çözümden</span><span class="sxs-lookup"><span data-stu-id="1cc8d-129">solution</span></span>](/nuget/schema/nuget-config-file#solution-section)

  <span data-ttu-id="1cc8d-130">Bu ayar Visual Studio 'ya özeldir ve .NET Core için uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-130">This setting is Visual Studio specific and doesn't apply to .NET Core.</span></span> <span data-ttu-id="1cc8d-131">.NET Core bir `packages.config` dosyası kullanmaz ve bunun yerine NuGet paketleri için `<PackageReference>` öğeleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-131">.NET Core doesn't use a `packages.config` file and instead uses `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="1cc8d-132">trustedSigners</span><span class="sxs-lookup"><span data-stu-id="1cc8d-132">trustedSigners</span></span>](/nuget/schema/nuget-config-file#trustedsigners-section)

  <span data-ttu-id="1cc8d-133">NuGet, güvenilen paketlerin [platformlar arası doğrulanmasını henüz desteklemediğinden](https://github.com/NuGet/Home/issues/7939) , bu ayar geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-133">This setting isn't applicable as [NuGet doesn't yet support cross-platform verification](https://github.com/NuGet/Home/issues/7939) of trusted packages.</span></span>

## <a name="implicit-dotnet-restore"></a><span data-ttu-id="1cc8d-134">Örtük `dotnet restore`</span><span class="sxs-lookup"><span data-stu-id="1cc8d-134">Implicit `dotnet restore`</span></span>

<span data-ttu-id="1cc8d-135">.NET Core 2,0 ' den itibaren, aşağıdaki komutları verdiğinizde `dotnet restore`, gerekli olduğunda örtük olarak çalıştırılır:</span><span class="sxs-lookup"><span data-stu-id="1cc8d-135">Starting with .NET Core 2.0, `dotnet restore` is run implicitly if necessary when you issue the following commands:</span></span>

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

<span data-ttu-id="1cc8d-136">Çoğu durumda, artık `dotnet restore` komutunu açıkça kullanmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-136">In most cases, you no longer need to explicitly use the `dotnet restore` command.</span></span>

<span data-ttu-id="1cc8d-137">Bazen `dotnet restore`, örtük olarak çalıştırmak kullanışlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-137">Sometimes, it might be inconvenient to run `dotnet restore` implicitly.</span></span> <span data-ttu-id="1cc8d-138">Örneğin, derleme sistemleri gibi bazı otomatikleştirilmiş sistemlerin, ağ kullanımını denetleyebilmeleri için geri yükleme işleminin ne zaman gerçekleşeceğini denetlemek üzere `dotnet restore` çağrısı yapması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-138">For example, some automated systems, such as build systems, need to call `dotnet restore` explicitly to control when the restore occurs so that they can control network usage.</span></span> <span data-ttu-id="1cc8d-139">`dotnet restore` örtük olarak çalışmasını engellemek için, örtük geri yüklemeyi devre dışı bırakmak üzere bu komutlardan herhangi biriyle `--no-restore` bayrağını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-139">To prevent `dotnet restore` from running implicitly, you can use the `--no-restore` flag with any of these commands to disable implicit restore.</span></span>

## <a name="arguments"></a><span data-ttu-id="1cc8d-140">Arguments</span><span class="sxs-lookup"><span data-stu-id="1cc8d-140">Arguments</span></span>

`ROOT`

<span data-ttu-id="1cc8d-141">Geri yüklenecek proje dosyasının isteğe bağlı yolu.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-141">Optional path to the project file to restore.</span></span>

## <a name="options"></a><span data-ttu-id="1cc8d-142">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="1cc8d-142">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="1cc8d-143">.NET Core 2. x</span><span class="sxs-lookup"><span data-stu-id="1cc8d-143">.NET Core 2.x</span></span>](#tab/netcore2x)

`--configfile <FILE>`

<span data-ttu-id="1cc8d-144">Geri yükleme işlemi için kullanılacak NuGet yapılandırma dosyası (*NuGet. config*).</span><span class="sxs-lookup"><span data-stu-id="1cc8d-144">The NuGet configuration file (*nuget.config*) to use for the restore operation.</span></span>

`--disable-parallel`

<span data-ttu-id="1cc8d-145">Paralel olarak birden çok projenin geri yüklenmesini devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-145">Disables restoring multiple projects in parallel.</span></span>

`--force`

<span data-ttu-id="1cc8d-146">Son geri yükleme başarılı olsa bile tüm bağımlılıkların çözülmesini zorlar.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-146">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="1cc8d-147">Bu bayrağın belirtilmesi, *Project. varlıklar. JSON* dosyasını silme ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-147">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="1cc8d-148">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-148">Prints out a short help for the command.</span></span>

`--ignore-failed-sources`

<span data-ttu-id="1cc8d-149">Yalnızca sürüm gereksinimini karşılayan paketler varsa başarısız kaynaklar hakkında uyar.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-149">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

`--no-cache`

<span data-ttu-id="1cc8d-150">Paketlerin ve HTTP isteklerinin önbelleğe alınamadı belirtir.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-150">Specifies to not cache packages and HTTP requests.</span></span>

`--no-dependencies`

<span data-ttu-id="1cc8d-151">Projeden projeye (P2P) başvuruları olan bir projeyi geri yüklerken, başvuruları değil kök projeyi geri yükler.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-151">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--packages <PACKAGES_DIRECTORY>`

<span data-ttu-id="1cc8d-152">Geri yüklenen paketlerin dizinini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-152">Specifies the directory for restored packages.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="1cc8d-153">Paket geri yüklemesi için bir çalışma zamanı belirtir.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-153">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="1cc8d-154">Bu, *. csproj* dosyasındaki `<RuntimeIdentifiers>` etiketinde açıkça listelenmeyen çalışma zamanları paketlerini geri yüklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-154">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="1cc8d-155">Çalışma zamanı tanımlayıcıları (RID 'Ler) listesi için bkz. [RID kataloğu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="1cc8d-155">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="1cc8d-156">Bu seçeneği birden çok kez belirterek birden çok grup belirtin.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-156">Provide multiple RIDs by specifying this option multiple times.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="1cc8d-157">Geri yükleme işlemi sırasında kullanılacak bir NuGet paket kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-157">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="1cc8d-158">Bu ayar *NuGet. config* dosyalarında belirtilen tüm kaynakları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-158">This setting overrides all of the sources specified in the *nuget.config* files.</span></span> <span data-ttu-id="1cc8d-159">Bu seçenek birden çok kez belirtilerek birden çok kaynak sağlanarak sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-159">Multiple sources can be provided by specifying this option multiple times.</span></span>

`--verbosity <LEVEL>`

<span data-ttu-id="1cc8d-160">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-160">Sets the verbosity level of the command.</span></span> <span data-ttu-id="1cc8d-161">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-161">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="1cc8d-162">Varsayılan değer `minimal`.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-162">Default value is `minimal`.</span></span>

`--interactive`

<span data-ttu-id="1cc8d-163">Komutun Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir (örneğin, kimlik doğrulamasını tamamlamaya).</span><span class="sxs-lookup"><span data-stu-id="1cc8d-163">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span> <span data-ttu-id="1cc8d-164">.NET Core 2.1.400 'dan beri.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-164">Since .NET Core 2.1.400.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="1cc8d-165">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="1cc8d-165">.NET Core 1.x</span></span>](#tab/netcore1x)

`--configfile <FILE>`

<span data-ttu-id="1cc8d-166">Geri yükleme işlemi için kullanılacak NuGet yapılandırma dosyası (*NuGet. config*).</span><span class="sxs-lookup"><span data-stu-id="1cc8d-166">The NuGet configuration file (*nuget.config*) to use for the restore operation.</span></span>

`--disable-parallel`

<span data-ttu-id="1cc8d-167">Paralel olarak birden çok projenin geri yüklenmesini devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-167">Disables restoring multiple projects in parallel.</span></span>

`-h|--help`

<span data-ttu-id="1cc8d-168">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-168">Prints out a short help for the command.</span></span>

`--ignore-failed-sources`

<span data-ttu-id="1cc8d-169">Yalnızca sürüm gereksinimini karşılayan paketler varsa başarısız kaynaklar hakkında uyar.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-169">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

`--no-cache`

<span data-ttu-id="1cc8d-170">Paketlerin ve HTTP isteklerinin önbelleğe alınamadı belirtir.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-170">Specifies to not cache packages and HTTP requests.</span></span>

`--no-dependencies`

<span data-ttu-id="1cc8d-171">Projeden projeye (P2P) başvuruları olan bir projeyi geri yüklerken, başvuruları değil kök projeyi geri yükler.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-171">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--packages <PACKAGES_DIRECTORY>`

<span data-ttu-id="1cc8d-172">Geri yüklenen paketlerin dizinini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-172">Specifies the directory for restored packages.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="1cc8d-173">Paket geri yüklemesi için bir çalışma zamanı belirtir.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-173">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="1cc8d-174">Bu, *. csproj* dosyasındaki `<RuntimeIdentifiers>` etiketinde açıkça listelenmeyen çalışma zamanları paketlerini geri yüklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-174">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="1cc8d-175">Çalışma zamanı tanımlayıcıları (RID 'Ler) listesi için bkz. [RID kataloğu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="1cc8d-175">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="1cc8d-176">Bu seçeneği birden çok kez belirterek birden çok grup belirtin.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-176">Provide multiple RIDs by specifying this option multiple times.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="1cc8d-177">Geri yükleme işlemi sırasında kullanılacak bir NuGet paket kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-177">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="1cc8d-178">Bu, NuGet *. config dosyasında* belirtilen tüm kaynakları geçersiz kılar; `<packageSource>` öğesi orada olmadığı gibi *NuGet. config* dosyasını etkin şekilde okur.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-178">This overrides all of the sources specified in the *nuget.config* files, effectively reading the *nuget.config* file as if the `<packageSource>` element was not there.</span></span> <span data-ttu-id="1cc8d-179">Bu seçenek birden çok kez belirtilerek birden çok kaynak sağlanarak sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-179">Multiple sources can be provided by specifying this option multiple times.</span></span>

`--verbosity <LEVEL>`

<span data-ttu-id="1cc8d-180">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-180">Sets the verbosity level of the command.</span></span> <span data-ttu-id="1cc8d-181">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-181">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="1cc8d-182">Varsayılan, `minimal` değeridir.</span><span class="sxs-lookup"><span data-stu-id="1cc8d-182">The default is `minimal`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="1cc8d-183">Örnekler</span><span class="sxs-lookup"><span data-stu-id="1cc8d-183">Examples</span></span>

<span data-ttu-id="1cc8d-184">Geçerli dizindeki proje için bağımlılıkları ve araçları geri yükle:</span><span class="sxs-lookup"><span data-stu-id="1cc8d-184">Restore dependencies and tools for the project in the current directory:</span></span>

`dotnet restore`

<span data-ttu-id="1cc8d-185">Verilen yolda bulunan `app1` projesi için bağımlılıkları ve araçları geri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="1cc8d-185">Restore dependencies and tools for the `app1` project found in the given path:</span></span>

`dotnet restore ~/projects/app1/app1.csproj`

<span data-ttu-id="1cc8d-186">Kaynak olarak belirtilen dosya yolunu kullanarak geçerli dizindeki proje için bağımlılıkları ve araçları geri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="1cc8d-186">Restore the dependencies and tools for the project in the current directory using the file path provided as the source:</span></span>

`dotnet restore -s c:\packages\mypackages`

<span data-ttu-id="1cc8d-187">Kaynak olarak girilen iki dosya yolunu kullanarak geçerli dizindeki proje için bağımlılıkları ve araçları geri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="1cc8d-187">Restore the dependencies and tools for the project in the current directory using the two file paths provided as sources:</span></span>

`dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages`

<span data-ttu-id="1cc8d-188">Geçerli dizindeki proje için bağımlılıkları ve araçları ayrıntılı çıktıyı gösteren geri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="1cc8d-188">Restore dependencies and tools for the project in the current directory showing detailed output:</span></span>

`dotnet restore --verbosity detailed`
