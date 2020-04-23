---
title: dotnet geri yükleme komutu
description: Dotnet geri yükleme komutuyla bağımlılıkları ve projeye özgü araçları nasıl geri yükleyebileceğinizi öğrenin.
ms.date: 02/27/2020
ms.openlocfilehash: 3deef68a9bcee389a52291c72e7e1a1019a739fd
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102794"
---
# <a name="dotnet-restore"></a><span data-ttu-id="2751f-103">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="2751f-103">dotnet restore</span></span>

<span data-ttu-id="2751f-104">**Bu makale şu şekilde dir:** ✔️ .NET Core 2.1 SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="2751f-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="2751f-105">Adı</span><span class="sxs-lookup"><span data-stu-id="2751f-105">Name</span></span>

<span data-ttu-id="2751f-106">`dotnet restore`- Projenin bağımlılıklarını ve araçlarını geri yükler.</span><span class="sxs-lookup"><span data-stu-id="2751f-106">`dotnet restore` - Restores the dependencies and tools of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="2751f-107">Özet</span><span class="sxs-lookup"><span data-stu-id="2751f-107">Synopsis</span></span>

```dotnetcli
dotnet restore [<ROOT>] [--configfile <FILE>] [--disable-parallel]
    [-f|--force] [--force-evaluate] [--ignore-failed-sources]
    [--interactive] [--lock-file-path <LOCK_FILE_PATH>] [--locked-mode]
    [--no-cache] [--no-dependencies] [--packages <PACKAGES_DIRECTORY>]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [-s|--source <SOURCE>]
    [--use-lockfile] [-v|--verbosity <LEVEL>]

dotnet restore -h|--help
```

## <a name="description"></a><span data-ttu-id="2751f-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2751f-108">Description</span></span>

<span data-ttu-id="2751f-109">Komut, `dotnet restore` proje dosyasında belirtilen projeye özgü araçların yanı sıra bağımlılıkları geri yüklemek için NuGet'i kullanır.</span><span class="sxs-lookup"><span data-stu-id="2751f-109">The `dotnet restore` command uses NuGet to restore dependencies as well as project-specific tools that are specified in the project file.</span></span> <span data-ttu-id="2751f-110">Varsayılan olarak, bağımlılıkların ve araçların geri yükleme paralel olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="2751f-110">By default, the restoration of dependencies and tools are executed in parallel.</span></span>

### <a name="specify-feeds"></a><span data-ttu-id="2751f-111">Akışları belirtin</span><span class="sxs-lookup"><span data-stu-id="2751f-111">Specify feeds</span></span>

<span data-ttu-id="2751f-112">Bağımlılıkları geri yüklemek için NuGet'in paketlerin bulunduğu akışlara ihtiyacı vardır.</span><span class="sxs-lookup"><span data-stu-id="2751f-112">To restore the dependencies, NuGet needs the feeds where the packages are located.</span></span> <span data-ttu-id="2751f-113">Özet akışları genellikle *nuget.config* yapılandırma dosyası üzerinden sağlanır.</span><span class="sxs-lookup"><span data-stu-id="2751f-113">Feeds are usually provided via the *nuget.config* configuration file.</span></span> <span data-ttu-id="2751f-114">.NET Core SDK yüklendiğinde varsayılan yapılandırma dosyası sağlanır.</span><span class="sxs-lookup"><span data-stu-id="2751f-114">A default configuration file is provided when the .NET Core SDK is installed.</span></span> <span data-ttu-id="2751f-115">Ek akışlar belirtmek için aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="2751f-115">To specify additional feeds, do one of the following:</span></span>

- <span data-ttu-id="2751f-116">Proje dizininde kendi *nuget.config* dosyanızı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2751f-116">Create your own *nuget.config* file in the project directory.</span></span> <span data-ttu-id="2751f-117">Daha fazla bilgi için, bu makalenin ilerleyen saatlerinde [Ortak NuGet yapılandırmaları](/nuget/consume-packages/configuring-nuget-behavior) ve [nuget.config farklılıklarına](#nugetconfig-differences) bakın.</span><span class="sxs-lookup"><span data-stu-id="2751f-117">For more information, see [Common NuGet configurations](/nuget/consume-packages/configuring-nuget-behavior) and [nuget.config differences](#nugetconfig-differences) later in this article.</span></span>
- <span data-ttu-id="2751f-118">Gibi komutları kullanın. `dotnet nuget` [`dotnet nuget add source`](dotnet-nuget-add-source.md)</span><span class="sxs-lookup"><span data-stu-id="2751f-118">Use `dotnet nuget` commands such as [`dotnet nuget add source`](dotnet-nuget-add-source.md).</span></span>

<span data-ttu-id="2751f-119">*Nuget.config* beslemelerini `-s` seçeneği ile geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2751f-119">You can override the *nuget.config* feeds with the `-s` option.</span></span>

<span data-ttu-id="2751f-120">Kimlik doğrulamalı akışların nasıl kullanılacağı hakkında bilgi için [bkz.](/nuget/consume-packages/consuming-packages-authenticated-feeds)</span><span class="sxs-lookup"><span data-stu-id="2751f-120">For information about how to use authenticated feeds, see [Consuming packages from authenticated feeds](/nuget/consume-packages/consuming-packages-authenticated-feeds).</span></span>

### <a name="package-cache"></a><span data-ttu-id="2751f-121">Paket önbelleği</span><span class="sxs-lookup"><span data-stu-id="2751f-121">Package cache</span></span>

<span data-ttu-id="2751f-122">Bağımlılıklar için, bağımsız değişkeni kullanarak geri yükleme işlemi `--packages` sırasında geri yüklenen paketlerin nereye yerleştirildiğini belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2751f-122">For dependencies, you specify where the restored packages are placed during the restore operation using the `--packages` argument.</span></span> <span data-ttu-id="2751f-123">Belirtilmemişse, varsayılan NuGet paket önbelleği kullanılır `.nuget/packages` ve bu da tüm işletim sistemlerinde kullanıcının ev dizininde bulunan dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="2751f-123">If not specified, the default NuGet package cache is used, which is found in the `.nuget/packages` directory in the user's home directory on all operating systems.</span></span> <span data-ttu-id="2751f-124">Örneğin, *Linux'ta /home/user1* veya Windows'da *C:\Users\user1.*</span><span class="sxs-lookup"><span data-stu-id="2751f-124">For example, */home/user1* on Linux or *C:\Users\user1* on Windows.</span></span>

### <a name="project-specific-tooling"></a><span data-ttu-id="2751f-125">Projeye özel takımlama</span><span class="sxs-lookup"><span data-stu-id="2751f-125">Project-specific tooling</span></span>

<span data-ttu-id="2751f-126">Projeye özgü takımlama `dotnet restore` için, önce aracın paketlendiği paketi geri yükler, sonra da proje dosyasında belirtildiği şekilde aracın bağımlılıklarını geri yüklemeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="2751f-126">For project-specific tooling, `dotnet restore` first restores the package in which the tool is packed, and then proceeds to restore the tool's dependencies as specified in its project file.</span></span>

### <a name="nugetconfig-differences"></a><span data-ttu-id="2751f-127">nuget.config farklar</span><span class="sxs-lookup"><span data-stu-id="2751f-127">nuget.config differences</span></span>

<span data-ttu-id="2751f-128">`dotnet restore` Komutun davranışı *nuget.config* dosyasındaki ayarlardan etkilenir, varsa.</span><span class="sxs-lookup"><span data-stu-id="2751f-128">The behavior of the `dotnet restore` command is affected by the settings in the *nuget.config* file, if present.</span></span> <span data-ttu-id="2751f-129">Örneğin, `globalPackagesFolder` *nuget.config'de* ayarla, geri yüklenen NuGet paketlerini belirtilen klasöre yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="2751f-129">For example, setting the `globalPackagesFolder` in *nuget.config* places the restored NuGet packages in the specified folder.</span></span> <span data-ttu-id="2751f-130">Bu, komuttaki `--packages` seçeneği belirtmeye `dotnet restore` alternatiftir.</span><span class="sxs-lookup"><span data-stu-id="2751f-130">This is an alternative to specifying the `--packages` option on the `dotnet restore` command.</span></span> <span data-ttu-id="2751f-131">Daha fazla bilgi için [nuget.config referansına](/nuget/schema/nuget-config-file)bakın.</span><span class="sxs-lookup"><span data-stu-id="2751f-131">For more information, see the [nuget.config reference](/nuget/schema/nuget-config-file).</span></span>

<span data-ttu-id="2751f-132">Yoksayan `dotnet restore` üç özel ayar vardır:</span><span class="sxs-lookup"><span data-stu-id="2751f-132">There are three specific settings that `dotnet restore` ignores:</span></span>

- [<span data-ttu-id="2751f-133">bindingYönlendirmeler</span><span class="sxs-lookup"><span data-stu-id="2751f-133">bindingRedirects</span></span>](/nuget/schema/nuget-config-file#bindingredirects-section)

  <span data-ttu-id="2751f-134">Bağlama yönlendirmeleri öğelerle `<PackageReference>` çalışmaz ve .NET `<PackageReference>` Core yalnızca NuGet paketleri için öğeleri destekler.</span><span class="sxs-lookup"><span data-stu-id="2751f-134">Binding redirects don't work with `<PackageReference>` elements and .NET Core only supports `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="2751f-135">Çözüm</span><span class="sxs-lookup"><span data-stu-id="2751f-135">solution</span></span>](/nuget/schema/nuget-config-file#solution-section)

  <span data-ttu-id="2751f-136">Bu ayar Visual Studio'ya özgüdür ve .NET Core için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="2751f-136">This setting is Visual Studio specific and doesn't apply to .NET Core.</span></span> <span data-ttu-id="2751f-137">.NET Core bir `packages.config` dosya kullanmaz `<PackageReference>` ve bunun yerine NuGet paketleri için öğeleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="2751f-137">.NET Core doesn't use a `packages.config` file and instead uses `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="2751f-138">güvenilir Signers</span><span class="sxs-lookup"><span data-stu-id="2751f-138">trustedSigners</span></span>](/nuget/schema/nuget-config-file#trustedsigners-section)

  <span data-ttu-id="2751f-139">NuGet henüz güvenilir paketlerin [platformlar arası doğrulanmasını desteklemediği](https://github.com/NuGet/Home/issues/7939) için bu ayar geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="2751f-139">This setting isn't applicable as [NuGet doesn't yet support cross-platform verification](https://github.com/NuGet/Home/issues/7939) of trusted packages.</span></span>

## <a name="implicit-restore"></a><span data-ttu-id="2751f-140">Örtük geri yükleme</span><span class="sxs-lookup"><span data-stu-id="2751f-140">Implicit restore</span></span>

<span data-ttu-id="2751f-141">Aşağıdaki `dotnet restore` komutları çalıştırdığınızda gerekirse komut örtülü olarak çalıştırılır:</span><span class="sxs-lookup"><span data-stu-id="2751f-141">The `dotnet restore` command is run implicitly if necessary when you run the following commands:</span></span>

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

<span data-ttu-id="2751f-142">Çoğu durumda, komutu `dotnet restore` açıkça kullanmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="2751f-142">In most cases, you don't need to explicitly use the `dotnet restore` command.</span></span>

<span data-ttu-id="2751f-143">Bazen, dolaylı olarak çalıştırmak `dotnet restore` rahatsız edici olabilir.</span><span class="sxs-lookup"><span data-stu-id="2751f-143">Sometimes, it might be inconvenient to run `dotnet restore` implicitly.</span></span> <span data-ttu-id="2751f-144">Örneğin, yapı sistemleri gibi bazı otomatik sistemlerin, `dotnet restore` ağ kullanımını denetleyebilmeleri için geri yüklemenin ne zaman gerçekleşebileceğini denetlemek için açıkça aramaları gerekir.</span><span class="sxs-lookup"><span data-stu-id="2751f-144">For example, some automated systems, such as build systems, need to call `dotnet restore` explicitly to control when the restore occurs so that they can control network usage.</span></span> <span data-ttu-id="2751f-145">Örtülü `dotnet restore` olarak çalışmasını önlemek için, `--no-restore` örtük geri yüklemeyi devre dışı bırakmada bu komutlardan herhangi biriyle bayrağı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2751f-145">To prevent `dotnet restore` from running implicitly, you can use the `--no-restore` flag with any of these commands to disable implicit restore.</span></span>

## <a name="arguments"></a><span data-ttu-id="2751f-146">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="2751f-146">Arguments</span></span>

- **`ROOT`**

  <span data-ttu-id="2751f-147">Geri yükleme için proje dosyasına isteğe bağlı yol.</span><span class="sxs-lookup"><span data-stu-id="2751f-147">Optional path to the project file to restore.</span></span>

## <a name="options"></a><span data-ttu-id="2751f-148">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="2751f-148">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="2751f-149">NuGet yapılandırma dosyası (*nuget.config*) geri yükleme işlemi için kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="2751f-149">The NuGet configuration file (*nuget.config*) to use for the restore operation.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="2751f-150">Birden çok projeyi paralel olarak geri devre dışı kılabilir.</span><span class="sxs-lookup"><span data-stu-id="2751f-150">Disables restoring multiple projects in parallel.</span></span>

- **`--force`**

  <span data-ttu-id="2751f-151">Son geri yükleme başarılı olsa bile tüm bağımlılıkları çözüme kavuşturmaya zorlar.</span><span class="sxs-lookup"><span data-stu-id="2751f-151">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="2751f-152">Bu bayrağı *belirtmek, project.assets.json* dosyasını silmekle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="2751f-152">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`--force-evaluate`**

  <span data-ttu-id="2751f-153">Bir kilit dosyası zaten olsa bile tüm bağımlılıkları yeniden değerlendirmek için geri yükleme zorlar.</span><span class="sxs-lookup"><span data-stu-id="2751f-153">Forces restore to reevaluate all dependencies even if a lock file already exists.</span></span>

- **`-h|--help`**

  <span data-ttu-id="2751f-154">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="2751f-154">Prints out a short help for the command.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="2751f-155">Yalnızca sürüm gereksinimini karşılayan paketler varsa, başarısız kaynaklar hakkında uyarıda bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="2751f-155">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

- **`--interactive`**

  <span data-ttu-id="2751f-156">Komutun durmasına ve kullanıcı girişinin veya eylemini beklemesine izin verir (örneğin kimlik doğrulamasını tamamlamak için).</span><span class="sxs-lookup"><span data-stu-id="2751f-156">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span> <span data-ttu-id="2751f-157">.NET Core 2.1.400'den beri.</span><span class="sxs-lookup"><span data-stu-id="2751f-157">Since .NET Core 2.1.400.</span></span>

- **`--lock-file-path <LOCK_FILE_PATH>`**

  <span data-ttu-id="2751f-158">Proje kilidi dosyasının yazıldığı çıktı konumu.</span><span class="sxs-lookup"><span data-stu-id="2751f-158">Output location where project lock file is written.</span></span> <span data-ttu-id="2751f-159">Varsayılan olarak, bu *PROJECT_ROOT\packages.lock.json*olduğunu.</span><span class="sxs-lookup"><span data-stu-id="2751f-159">By default, this is *PROJECT_ROOT\packages.lock.json*.</span></span>

- **`--locked-mode`**

  <span data-ttu-id="2751f-160">Proje kilidi dosyasının güncelleştirilmesine izin verme.</span><span class="sxs-lookup"><span data-stu-id="2751f-160">Don't allow updating project lock file.</span></span>

- **`--no-cache`**

  <span data-ttu-id="2751f-161">HTTP isteklerini önbelleğe almaya karar verebisin.</span><span class="sxs-lookup"><span data-stu-id="2751f-161">Specifies to not cache HTTP requests.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="2751f-162">Projeden projeye (P2P) başvurularla projeyi geri yüklediğinizde, başvuruları değil, kök projeyi geri yükler.</span><span class="sxs-lookup"><span data-stu-id="2751f-162">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

- **`--packages <PACKAGES_DIRECTORY>`**

  <span data-ttu-id="2751f-163">Geri yüklenen paketler için dizini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2751f-163">Specifies the directory for restored packages.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="2751f-164">Paket geri yüklemesi için bir çalışma zamanı belirtir.</span><span class="sxs-lookup"><span data-stu-id="2751f-164">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="2751f-165">Bu, `<RuntimeIdentifiers>` *.csproj* dosyasındaki etikette açıkça belirtilmeyen çalışma süreleri için paketleri geri yüklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2751f-165">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="2751f-166">Runtime Tanımlayıcıları (RID'ler) listesi için RID [kataloğuna](../rid-catalog.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="2751f-166">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="2751f-167">Bu seçeneği birden çok kez belirterek birden çok RID sağlayın.</span><span class="sxs-lookup"><span data-stu-id="2751f-167">Provide multiple RIDs by specifying this option multiple times.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="2751f-168">Geri yükleme işlemi sırasında kullanılacak bir NuGet paket kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2751f-168">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="2751f-169">Bu ayar *nuget.config* dosyalarında belirtilen tüm kaynakları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="2751f-169">This setting overrides all of the sources specified in the *nuget.config* files.</span></span> <span data-ttu-id="2751f-170">Bu seçeneği birden çok kez belirterek birden çok kaynak sağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="2751f-170">Multiple sources can be provided by specifying this option multiple times.</span></span>

- **`--use-lockfile`**

  <span data-ttu-id="2751f-171">Proje kilit dosyasının oluşturulmasını ve geri yükleme ile kullanılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="2751f-171">Enables project lock file to be generated and used with restore.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="2751f-172">Komutun ayrıntılı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2751f-172">Sets the verbosity level of the command.</span></span> <span data-ttu-id="2751f-173">İzin verilen `q[uiet]` `m[inimal]`değerler `n[ormal]` `d[etailed]`, `diag[nostic]`, , , ve .</span><span class="sxs-lookup"><span data-stu-id="2751f-173">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="2751f-174">Varsayılan değer. `minimal`</span><span class="sxs-lookup"><span data-stu-id="2751f-174">Default value is `minimal`.</span></span>

## <a name="examples"></a><span data-ttu-id="2751f-175">Örnekler</span><span class="sxs-lookup"><span data-stu-id="2751f-175">Examples</span></span>

- <span data-ttu-id="2751f-176">Geçerli dizindeki proje için bağımlılıkları ve araçları geri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="2751f-176">Restore dependencies and tools for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet restore
  ```

- <span data-ttu-id="2751f-177">Verilen yolda bulunan `app1` proje için bağımlılıkları ve araçları geri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="2751f-177">Restore dependencies and tools for the `app1` project found in the   given path:</span></span>

  ```dotnetcli
  dotnet restore ~/projects/app1/app1.csproj
  ```

- <span data-ttu-id="2751f-178">Kaynak olarak sağlanan dosya yolunu kullanarak geçerli dizindeki projeye ilişkin bağımlılıkları ve araçları geri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="2751f-178">Restore the dependencies and tools for the project in the current   directory using the file path provided as the source:</span></span>

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages
  ```

- <span data-ttu-id="2751f-179">Kaynak olarak sağlanan iki dosya yolunu kullanarak geçerli dizindeki proje ye bağımlılıkları ve araçları geri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="2751f-179">Restore the dependencies and tools for the project in the current   directory using the two file paths provided as sources:</span></span>

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages
  ```

- <span data-ttu-id="2751f-180">Ayrıntılı çıktıyı gösteren geçerli dizinde proje için bağımlılıkları ve araçları geri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="2751f-180">Restore dependencies and tools for the project in the current directory   showing detailed output:</span></span>

  ```dotnetcli
  dotnet restore --verbosity detailed
  ```
