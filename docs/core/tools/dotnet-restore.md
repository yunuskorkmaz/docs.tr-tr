---
title: dotnet restore komutu
description: Dotnet restore komutuyla bağımlılıkları ve projeye özel araçları nasıl geri yükleyeceğinizi öğrenin.
ms.date: 05/29/2018
ms.openlocfilehash: 56d99a4edd69246632560065c415a3f41ac3e1b5
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202812"
---
# <a name="dotnet-restore"></a><span data-ttu-id="c2ca1-103">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="c2ca1-103">dotnet restore</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="c2ca1-104">Ad</span><span class="sxs-lookup"><span data-stu-id="c2ca1-104">Name</span></span>

<span data-ttu-id="c2ca1-105">`dotnet restore`-Bir projenin bağımlılıklarını ve araçlarını geri yükler.</span><span class="sxs-lookup"><span data-stu-id="c2ca1-105">`dotnet restore` - Restores the dependencies and tools of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c2ca1-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="c2ca1-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="c2ca1-107">.NET Core 2. x</span><span class="sxs-lookup"><span data-stu-id="c2ca1-107">.NET Core 2.x</span></span>](#tab/netcore2x)

```console
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--force] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity] [--interactive]
dotnet restore [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="c2ca1-108">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="c2ca1-108">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="c2ca1-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c2ca1-109">Description</span></span>

<span data-ttu-id="c2ca1-110">Bu `dotnet restore` komut, bağımlılıkları geri yüklemek için NuGet kullanır ve proje dosyasında belirtilen projeye özgü araçlardır.</span><span class="sxs-lookup"><span data-stu-id="c2ca1-110">The `dotnet restore` command uses NuGet to restore dependencies as well as project-specific tools that are specified in the project file.</span></span> <span data-ttu-id="c2ca1-111">Varsayılan olarak, bağımlılıklar ve araçların geri yüklenmesi paralel olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="c2ca1-111">By default, the restoration of dependencies and tools are executed in parallel.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="c2ca1-112">Bağımlılıkları geri yüklemek için, NuGet paketlerin bulunduğu akışlara ihtiyaç duyuyor.</span><span class="sxs-lookup"><span data-stu-id="c2ca1-112">To restore the dependencies, NuGet needs the feeds where the packages are located.</span></span> <span data-ttu-id="c2ca1-113">Akışlar genellikle *NuGet. config* yapılandırma dosyası aracılığıyla sağlanır.</span><span class="sxs-lookup"><span data-stu-id="c2ca1-113">Feeds are usually provided via the *nuget.config* configuration file.</span></span> <span data-ttu-id="c2ca1-114">CLı araçları yüklendiğinde varsayılan bir yapılandırma dosyası sağlanır.</span><span class="sxs-lookup"><span data-stu-id="c2ca1-114">A default configuration file is provided when the CLI tools are installed.</span></span> <span data-ttu-id="c2ca1-115">Proje dizininde kendi *NuGet. config* dosyanızı oluşturarak ek akışlar belirlersiniz.</span><span class="sxs-lookup"><span data-stu-id="c2ca1-115">You specify additional feeds by creating your own *nuget.config* file in the project directory.</span></span> <span data-ttu-id="c2ca1-116">Komut isteminde her çağrı için ek akışlar da belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c2ca1-116">You also specify additional feeds per invocation at a command prompt.</span></span>

<span data-ttu-id="c2ca1-117">Bağımlılıklar için, geri yükleme işlemi sırasında `--packages` bağımsız değişkeni kullanarak geri yüklenen paketlerin nereye yerleştirileceğini belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c2ca1-117">For dependencies, you specify where the restored packages are placed during the restore operation using the `--packages` argument.</span></span> <span data-ttu-id="c2ca1-118">Belirtilmezse, varsayılan NuGet paketi önbelleği kullanılır ve bu, tüm işletim sistemlerindeki kullanıcının giriş dizinindeki `.nuget/packages` dizininde bulunur.</span><span class="sxs-lookup"><span data-stu-id="c2ca1-118">If not specified, the default NuGet package cache is used, which is found in the `.nuget/packages` directory in the user's home directory on all operating systems.</span></span> <span data-ttu-id="c2ca1-119">Örneğin, Linux üzerinde */home/user1* veya Windows üzerinde *c:\Users\User1* .</span><span class="sxs-lookup"><span data-stu-id="c2ca1-119">For example, */home/user1* on Linux or *C:\Users\user1* on Windows.</span></span>

<span data-ttu-id="c2ca1-120">Projeye özgü araçlar için, `dotnet restore` önce aracın paketlenmesi gereken paketi geri yükler ve ardından, araç bağımlılıklarını proje dosyasında belirtilen şekilde geri yüklemeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="c2ca1-120">For project-specific tooling, `dotnet restore` first restores the package in which the tool is packed, and then proceeds to restore the tool's dependencies as specified in its project file.</span></span>

### <a name="nugetconfig-differences"></a><span data-ttu-id="c2ca1-121">NuGet. config farklılıkları</span><span class="sxs-lookup"><span data-stu-id="c2ca1-121">nuget.config differences</span></span>

<span data-ttu-id="c2ca1-122">`dotnet restore` Komutun davranışı, varsa *NuGet. config* dosyasındaki ayarlardan etkilenir.</span><span class="sxs-lookup"><span data-stu-id="c2ca1-122">The behavior of the `dotnet restore` command is affected by the settings in the *nuget.config* file, if present.</span></span> <span data-ttu-id="c2ca1-123">Örneğin, `globalPackagesFolder` *NuGet. config* içindeki ayarı, geri yüklenen NuGet paketlerini belirtilen klasöre koyar.</span><span class="sxs-lookup"><span data-stu-id="c2ca1-123">For example, setting the `globalPackagesFolder` in *nuget.config* places the restored NuGet packages in the specified folder.</span></span> <span data-ttu-id="c2ca1-124">Bu `--packages` seçenek, `dotnet restore` komutunda seçeneğini belirtmeye yönelik bir alternatiftir.</span><span class="sxs-lookup"><span data-stu-id="c2ca1-124">This is an alternative to specifying the `--packages` option on the `dotnet restore` command.</span></span> <span data-ttu-id="c2ca1-125">Daha fazla bilgi için bkz. [NuGet. config başvurusu](/nuget/schema/nuget-config-file).</span><span class="sxs-lookup"><span data-stu-id="c2ca1-125">For more information, see the [nuget.config reference](/nuget/schema/nuget-config-file).</span></span>

<span data-ttu-id="c2ca1-126">Yok sayan `dotnet restore` üç özel ayar vardır:</span><span class="sxs-lookup"><span data-stu-id="c2ca1-126">There are three specific settings that `dotnet restore` ignores:</span></span>

- [<span data-ttu-id="c2ca1-127">Bindingyönlendirmeler</span><span class="sxs-lookup"><span data-stu-id="c2ca1-127">bindingRedirects</span></span>](/nuget/schema/nuget-config-file#bindingredirects-section)

  <span data-ttu-id="c2ca1-128">Bağlama yeniden yönlendirmeleri `<PackageReference>` öğelerle çalışmaz ve .NET Core yalnızca NuGet paketleri `<PackageReference>` için öğeleri destekler.</span><span class="sxs-lookup"><span data-stu-id="c2ca1-128">Binding redirects don't work with `<PackageReference>` elements and .NET Core only supports `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="c2ca1-129">çözümden</span><span class="sxs-lookup"><span data-stu-id="c2ca1-129">solution</span></span>](/nuget/schema/nuget-config-file#solution-section)

  <span data-ttu-id="c2ca1-130">Bu ayar Visual Studio 'ya özeldir ve .NET Core için uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="c2ca1-130">This setting is Visual Studio specific and doesn't apply to .NET Core.</span></span> <span data-ttu-id="c2ca1-131">.NET Core bir `packages.config` dosya kullanmaz ve bunun yerine NuGet `<PackageReference>` paketleri için öğeleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="c2ca1-131">.NET Core doesn't use a `packages.config` file and instead uses `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="c2ca1-132">trustedSigners</span><span class="sxs-lookup"><span data-stu-id="c2ca1-132">trustedSigners</span></span>](/nuget/schema/nuget-config-file#trustedsigners-section)

  <span data-ttu-id="c2ca1-133">NuGet, güvenilen paketlerin [platformlar arası doğrulanmasını henüz desteklemediğinden](https://github.com/NuGet/Home/issues/7939) , bu ayar geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="c2ca1-133">This setting isn't applicable as [NuGet doesn't yet support cross-platform verification](https://github.com/NuGet/Home/issues/7939) of trusted packages.</span></span>

## <a name="implicit-dotnet-restore"></a><span data-ttu-id="c2ca1-134">İndirgen`dotnet restore`</span><span class="sxs-lookup"><span data-stu-id="c2ca1-134">Implicit `dotnet restore`</span></span>

<span data-ttu-id="c2ca1-135">.NET Core 2,0 ' den itibaren `dotnet restore` , aşağıdaki komutları verdiğinizde, gerekirse örtülü olarak çalıştırılır:</span><span class="sxs-lookup"><span data-stu-id="c2ca1-135">Starting with .NET Core 2.0, `dotnet restore` is run implicitly if necessary when you issue the following commands:</span></span>

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

<span data-ttu-id="c2ca1-136">Çoğu durumda, artık `dotnet restore` komutunu açıkça kullanmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="c2ca1-136">In most cases, you no longer need to explicitly use the `dotnet restore` command.</span></span>

<span data-ttu-id="c2ca1-137">Bazen, örtülü olarak çalıştırılması `dotnet restore` uygun olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="c2ca1-137">Sometimes, it might be inconvenient to run `dotnet restore` implicitly.</span></span> <span data-ttu-id="c2ca1-138">Örneğin, derleme sistemleri gibi bazı otomatikleştirilmiş sistemlerin, ağ kullanımını denetleyebilmeleri için geri `dotnet restore` yüklemenin ne zaman gerçekleşeceğini denetlemek için açıkça çağrılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c2ca1-138">For example, some automated systems, such as build systems, need to call `dotnet restore` explicitly to control when the restore occurs so that they can control network usage.</span></span> <span data-ttu-id="c2ca1-139">Örtülü geri yüklemeyi devre dışı bırakmak için bu komutlardan herhangi `--no-restore` biriyle bayrağı kullanabilirsiniz. `dotnet restore`</span><span class="sxs-lookup"><span data-stu-id="c2ca1-139">To prevent `dotnet restore` from running implicitly, you can use the `--no-restore` flag with any of these commands to disable implicit restore.</span></span>

## <a name="arguments"></a><span data-ttu-id="c2ca1-140">Arguments</span><span class="sxs-lookup"><span data-stu-id="c2ca1-140">Arguments</span></span>

`ROOT`

<span data-ttu-id="c2ca1-141">Geri yüklenecek proje dosyasının isteğe bağlı yolu.</span><span class="sxs-lookup"><span data-stu-id="c2ca1-141">Optional path to the project file to restore.</span></span>

## <a name="options"></a><span data-ttu-id="c2ca1-142">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="c2ca1-142">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="c2ca1-143">.NET Core 2. x</span><span class="sxs-lookup"><span data-stu-id="c2ca1-143">.NET Core 2.x</span></span>](#tab/netcore2x)

`--configfile <FILE>`

<span data-ttu-id="c2ca1-144">Geri yükleme işlemi için kullanılacak NuGet yapılandırma dosyası (*NuGet. config*).</span><span class="sxs-lookup"><span data-stu-id="c2ca1-144">The NuGet configuration file (*nuget.config*) to use for the restore operation.</span></span>

`--disable-parallel`

<span data-ttu-id="c2ca1-145">Paralel olarak birden çok projenin geri yüklenmesini devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="c2ca1-145">Disables restoring multiple projects in parallel.</span></span>

`--force`

<span data-ttu-id="c2ca1-146">Son geri yükleme başarılı olsa bile tüm bağımlılıkların çözülmesini zorlar.</span><span class="sxs-lookup"><span data-stu-id="c2ca1-146">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="c2ca1-147">Bu bayrağın belirtilmesi, *Project. varlıklar. JSON* dosyasını silme ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="c2ca1-147">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="c2ca1-148">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="c2ca1-148">Prints out a short help for the command.</span></span>

`--ignore-failed-sources`

<span data-ttu-id="c2ca1-149">Yalnızca sürüm gereksinimini karşılayan paketler varsa başarısız kaynaklar hakkında uyar.</span><span class="sxs-lookup"><span data-stu-id="c2ca1-149">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

`--no-cache`

<span data-ttu-id="c2ca1-150">Paketlerin ve HTTP isteklerinin önbelleğe alınamadı belirtir.</span><span class="sxs-lookup"><span data-stu-id="c2ca1-150">Specifies to not cache packages and HTTP requests.</span></span>

`--no-dependencies`

<span data-ttu-id="c2ca1-151">Projeden projeye (P2P) başvuruları olan bir projeyi geri yüklerken, başvuruları değil kök projeyi geri yükler.</span><span class="sxs-lookup"><span data-stu-id="c2ca1-151">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--packages <PACKAGES_DIRECTORY>`

<span data-ttu-id="c2ca1-152">Geri yüklenen paketlerin dizinini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c2ca1-152">Specifies the directory for restored packages.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="c2ca1-153">Paket geri yüklemesi için bir çalışma zamanı belirtir.</span><span class="sxs-lookup"><span data-stu-id="c2ca1-153">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="c2ca1-154">Bu, `<RuntimeIdentifiers>` *. csproj* dosyasındaki etiketinde açıkça listelenmeyen çalışma zamanları paketlerini geri yüklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c2ca1-154">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="c2ca1-155">Çalışma zamanı tanımlayıcıları (RID 'Ler) listesi için bkz. [RID kataloğu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="c2ca1-155">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="c2ca1-156">Bu seçeneği birden çok kez belirterek birden çok grup belirtin.</span><span class="sxs-lookup"><span data-stu-id="c2ca1-156">Provide multiple RIDs by specifying this option multiple times.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="c2ca1-157">Geri yükleme işlemi sırasında kullanılacak bir NuGet paket kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c2ca1-157">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="c2ca1-158">Bu ayar *NuGet. config* dosyalarında belirtilen tüm kaynakları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="c2ca1-158">This setting overrides all of the sources specified in the *nuget.config* files.</span></span> <span data-ttu-id="c2ca1-159">Bu seçenek birden çok kez belirtilerek birden çok kaynak sağlanarak sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c2ca1-159">Multiple sources can be provided by specifying this option multiple times.</span></span>

`--verbosity <LEVEL>`

<span data-ttu-id="c2ca1-160">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c2ca1-160">Sets the verbosity level of the command.</span></span> <span data-ttu-id="c2ca1-161">İzin verilen değerler `q[uiet]` `m[inimal]` ,`n[ormal]`,, ve .`diag[nostic]` `d[etailed]`</span><span class="sxs-lookup"><span data-stu-id="c2ca1-161">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--interactive`

<span data-ttu-id="c2ca1-162">Komutun Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir (örneğin, kimlik doğrulamasını tamamlamaya).</span><span class="sxs-lookup"><span data-stu-id="c2ca1-162">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span> <span data-ttu-id="c2ca1-163">.NET Core 2.1.400 'dan beri.</span><span class="sxs-lookup"><span data-stu-id="c2ca1-163">Since .NET Core 2.1.400.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="c2ca1-164">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="c2ca1-164">.NET Core 1.x</span></span>](#tab/netcore1x)

`--configfile <FILE>`

<span data-ttu-id="c2ca1-165">Geri yükleme işlemi için kullanılacak NuGet yapılandırma dosyası (*NuGet. config*).</span><span class="sxs-lookup"><span data-stu-id="c2ca1-165">The NuGet configuration file (*nuget.config*) to use for the restore operation.</span></span>

`--disable-parallel`

<span data-ttu-id="c2ca1-166">Paralel olarak birden çok projenin geri yüklenmesini devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="c2ca1-166">Disables restoring multiple projects in parallel.</span></span>

`-h|--help`

<span data-ttu-id="c2ca1-167">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="c2ca1-167">Prints out a short help for the command.</span></span>

`--ignore-failed-sources`

<span data-ttu-id="c2ca1-168">Yalnızca sürüm gereksinimini karşılayan paketler varsa başarısız kaynaklar hakkında uyar.</span><span class="sxs-lookup"><span data-stu-id="c2ca1-168">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

`--no-cache`

<span data-ttu-id="c2ca1-169">Paketlerin ve HTTP isteklerinin önbelleğe alınamadı belirtir.</span><span class="sxs-lookup"><span data-stu-id="c2ca1-169">Specifies to not cache packages and HTTP requests.</span></span>

`--no-dependencies`

<span data-ttu-id="c2ca1-170">Projeden projeye (P2P) başvuruları olan bir projeyi geri yüklerken, başvuruları değil kök projeyi geri yükler.</span><span class="sxs-lookup"><span data-stu-id="c2ca1-170">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--packages <PACKAGES_DIRECTORY>`

<span data-ttu-id="c2ca1-171">Geri yüklenen paketlerin dizinini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c2ca1-171">Specifies the directory for restored packages.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="c2ca1-172">Paket geri yüklemesi için bir çalışma zamanı belirtir.</span><span class="sxs-lookup"><span data-stu-id="c2ca1-172">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="c2ca1-173">Bu, `<RuntimeIdentifiers>` *. csproj* dosyasındaki etiketinde açıkça listelenmeyen çalışma zamanları paketlerini geri yüklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c2ca1-173">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="c2ca1-174">Çalışma zamanı tanımlayıcıları (RID 'Ler) listesi için bkz. [RID kataloğu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="c2ca1-174">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="c2ca1-175">Bu seçeneği birden çok kez belirterek birden çok grup belirtin.</span><span class="sxs-lookup"><span data-stu-id="c2ca1-175">Provide multiple RIDs by specifying this option multiple times.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="c2ca1-176">Geri yükleme işlemi sırasında kullanılacak bir NuGet paket kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c2ca1-176">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="c2ca1-177">Bu, *NuGet. config* dosyalarında belirtilen tüm kaynakları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="c2ca1-177">This overrides all of the sources specified in the *nuget.config* files.</span></span> <span data-ttu-id="c2ca1-178">Bu seçenek birden çok kez belirtilerek birden çok kaynak sağlanarak sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c2ca1-178">Multiple sources can be provided by specifying this option multiple times.</span></span>

`--verbosity <LEVEL>`

<span data-ttu-id="c2ca1-179">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c2ca1-179">Sets the verbosity level of the command.</span></span> <span data-ttu-id="c2ca1-180">İzin verilen değerler `q[uiet]` `m[inimal]` ,`n[ormal]`,, ve .`diag[nostic]` `d[etailed]`</span><span class="sxs-lookup"><span data-stu-id="c2ca1-180">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="c2ca1-181">Örnekler</span><span class="sxs-lookup"><span data-stu-id="c2ca1-181">Examples</span></span>

<span data-ttu-id="c2ca1-182">Geçerli dizindeki proje için bağımlılıkları ve araçları geri yükle:</span><span class="sxs-lookup"><span data-stu-id="c2ca1-182">Restore dependencies and tools for the project in the current directory:</span></span>

`dotnet restore`

<span data-ttu-id="c2ca1-183">Verilen yolda bulunan `app1` projenin bağımlılıklarını ve araçlarını geri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="c2ca1-183">Restore dependencies and tools for the `app1` project found in the given path:</span></span>

`dotnet restore ~/projects/app1/app1.csproj`

<span data-ttu-id="c2ca1-184">Kaynak olarak belirtilen dosya yolunu kullanarak geçerli dizindeki proje için bağımlılıkları ve araçları geri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="c2ca1-184">Restore the dependencies and tools for the project in the current directory using the file path provided as the source:</span></span>

`dotnet restore -s c:\packages\mypackages`

<span data-ttu-id="c2ca1-185">Kaynak olarak girilen iki dosya yolunu kullanarak geçerli dizindeki proje için bağımlılıkları ve araçları geri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="c2ca1-185">Restore the dependencies and tools for the project in the current directory using the two file paths provided as sources:</span></span>

`dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages`

<span data-ttu-id="c2ca1-186">Geçerli dizindeki proje için bağımlılıkları ve araçları geri yükleyin ve yalnızca en az çıktıyı gösterir:</span><span class="sxs-lookup"><span data-stu-id="c2ca1-186">Restore dependencies and tools for the project in the current directory and shows only minimal output:</span></span>

`dotnet restore --verbosity minimal`
