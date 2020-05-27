---
title: dotnet restore komutu
description: Dotnet restore komutuyla bağımlılıkları ve projeye özel araçları nasıl geri yükleyeceğinizi öğrenin.
ms.date: 02/27/2020
ms.openlocfilehash: 276fad896a6a8a647ed05a9de8c582d463d9ab8f
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005329"
---
# <a name="dotnet-restore"></a><span data-ttu-id="73c50-103">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="73c50-103">dotnet restore</span></span>

<span data-ttu-id="73c50-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="73c50-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="73c50-105">Name</span><span class="sxs-lookup"><span data-stu-id="73c50-105">Name</span></span>

<span data-ttu-id="73c50-106">`dotnet restore`-Bir projenin bağımlılıklarını ve araçlarını geri yükler.</span><span class="sxs-lookup"><span data-stu-id="73c50-106">`dotnet restore` - Restores the dependencies and tools of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="73c50-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="73c50-107">Synopsis</span></span>

```dotnetcli
dotnet restore [<ROOT>] [--configfile <FILE>] [--disable-parallel]
    [-f|--force] [--force-evaluate] [--ignore-failed-sources]
    [--interactive] [--lock-file-path <LOCK_FILE_PATH>] [--locked-mode]
    [--no-cache] [--no-dependencies] [--packages <PACKAGES_DIRECTORY>]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [-s|--source <SOURCE>]
    [--use-lock-file] [-v|--verbosity <LEVEL>]

dotnet restore -h|--help
```

## <a name="description"></a><span data-ttu-id="73c50-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="73c50-108">Description</span></span>

<span data-ttu-id="73c50-109">Bu `dotnet restore` komut, bağımlılıkları geri yüklemek Için NuGet kullanır ve proje dosyasında belirtilen projeye özgü araçlardır.</span><span class="sxs-lookup"><span data-stu-id="73c50-109">The `dotnet restore` command uses NuGet to restore dependencies as well as project-specific tools that are specified in the project file.</span></span>  <span data-ttu-id="73c50-110">Çoğu durumda, `dotnet restore` aşağıdaki komutları çalıştırdığınızda bir NuGet geri yüklemesi gerektiğinde örtük olarak çalıştırıldığı için komutunu açıkça kullanmanız gerekmez:</span><span class="sxs-lookup"><span data-stu-id="73c50-110">In most cases, you don't need to explicitly use the `dotnet restore` command, since a NuGet restore is run implicitly if necessary when you run the following commands:</span></span>

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

<span data-ttu-id="73c50-111">Bazen, bu komutlarla örtük NuGet geri yüklemesini çalıştırmak kullanışlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="73c50-111">Sometimes, it might be inconvenient to run the implicit NuGet restore with these commands.</span></span> <span data-ttu-id="73c50-112">Örneğin, derleme sistemleri gibi bazı otomatikleştirilmiş sistemlerin, `dotnet restore` ağ kullanımını denetleyebilmeleri için geri yüklemenin ne zaman gerçekleşeceğini denetlemek için açıkça çağrılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="73c50-112">For example, some automated systems, such as build systems, need to call `dotnet restore` explicitly to control when the restore occurs so that they can control network usage.</span></span> <span data-ttu-id="73c50-113">Örtük NuGet geri yüklemesini engellemek için, `--no-restore` bayrağı, örtük geri yüklemeyi devre dışı bırakmak için bu komutlardan herhangi biriyle kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73c50-113">To prevent the implicit NuGet restore, you can use the `--no-restore` flag with any of these commands to disable implicit restore.</span></span>

### <a name="specify-feeds"></a><span data-ttu-id="73c50-114">Akışları belirt</span><span class="sxs-lookup"><span data-stu-id="73c50-114">Specify feeds</span></span>

<span data-ttu-id="73c50-115">Bağımlılıkları geri yüklemek için, NuGet paketlerin bulunduğu akışlara ihtiyaç duyuyor.</span><span class="sxs-lookup"><span data-stu-id="73c50-115">To restore the dependencies, NuGet needs the feeds where the packages are located.</span></span> <span data-ttu-id="73c50-116">Akışlar genellikle *NuGet. config* yapılandırma dosyası aracılığıyla sağlanır.</span><span class="sxs-lookup"><span data-stu-id="73c50-116">Feeds are usually provided via the *nuget.config* configuration file.</span></span> <span data-ttu-id="73c50-117">.NET Core SDK yüklendiğinde varsayılan bir yapılandırma dosyası sağlanır.</span><span class="sxs-lookup"><span data-stu-id="73c50-117">A default configuration file is provided when the .NET Core SDK is installed.</span></span> <span data-ttu-id="73c50-118">Ek akışlar belirtmek için aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="73c50-118">To specify additional feeds, do one of the following:</span></span>

- <span data-ttu-id="73c50-119">Proje dizininde kendi *NuGet. config* dosyanızı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="73c50-119">Create your own *nuget.config* file in the project directory.</span></span> <span data-ttu-id="73c50-120">Daha fazla bilgi için bu makalenin ilerleyen kısımlarında [yaygın NuGet yapılandırmalarını](/nuget/consume-packages/configuring-nuget-behavior) ve [NuGet. config farklılıklarını](#nugetconfig-differences) inceleyin.</span><span class="sxs-lookup"><span data-stu-id="73c50-120">For more information, see [Common NuGet configurations](/nuget/consume-packages/configuring-nuget-behavior) and [nuget.config differences](#nugetconfig-differences) later in this article.</span></span>
- <span data-ttu-id="73c50-121">Gibi `dotnet nuget` komutları kullanın [`dotnet nuget add source`](dotnet-nuget-add-source.md) .</span><span class="sxs-lookup"><span data-stu-id="73c50-121">Use `dotnet nuget` commands such as [`dotnet nuget add source`](dotnet-nuget-add-source.md).</span></span>

<span data-ttu-id="73c50-122">*NuGet. config* akışlarını seçeneğiyle geçersiz kılabilirsiniz `-s` .</span><span class="sxs-lookup"><span data-stu-id="73c50-122">You can override the *nuget.config* feeds with the `-s` option.</span></span>

<span data-ttu-id="73c50-123">Kimliği doğrulanmış akışların nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [kimliği doğrulanmış akışlardan paketleri](/nuget/consume-packages/consuming-packages-authenticated-feeds)kullanma.</span><span class="sxs-lookup"><span data-stu-id="73c50-123">For information about how to use authenticated feeds, see [Consuming packages from authenticated feeds](/nuget/consume-packages/consuming-packages-authenticated-feeds).</span></span>

### <a name="global-packages-folder"></a><span data-ttu-id="73c50-124">Genel paketler klasörü</span><span class="sxs-lookup"><span data-stu-id="73c50-124">Global packages folder</span></span>

<span data-ttu-id="73c50-125">Bağımlılıklar için, geri yükleme işlemi sırasında bağımsız değişkeni kullanarak geri yüklenen paketlerin nerede yerleştirileceğini belirtebilirsiniz `--packages` .</span><span class="sxs-lookup"><span data-stu-id="73c50-125">For dependencies, you can specify where the restored packages are placed during the restore operation using the `--packages` argument.</span></span> <span data-ttu-id="73c50-126">Belirtilmezse, varsayılan NuGet paketi önbelleği kullanılır ve bu, `.nuget/packages` tüm işletim sistemlerindeki kullanıcının giriş dizinindeki dizininde bulunur.</span><span class="sxs-lookup"><span data-stu-id="73c50-126">If not specified, the default NuGet package cache is used, which is found in the `.nuget/packages` directory in the user's home directory on all operating systems.</span></span> <span data-ttu-id="73c50-127">Örneğin, Linux üzerinde */home/user1* veya Windows üzerinde *c:\Users\User1* .</span><span class="sxs-lookup"><span data-stu-id="73c50-127">For example, */home/user1* on Linux or *C:\Users\user1* on Windows.</span></span>

### <a name="project-specific-tooling"></a><span data-ttu-id="73c50-128">Projeye özgü araç</span><span class="sxs-lookup"><span data-stu-id="73c50-128">Project-specific tooling</span></span>

<span data-ttu-id="73c50-129">Projeye özgü araçlar için, `dotnet restore` önce aracın paketlenmesi gereken paketi geri yükler ve ardından, araç bağımlılıklarını proje dosyasında belirtilen şekilde geri yüklemeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="73c50-129">For project-specific tooling, `dotnet restore` first restores the package in which the tool is packed, and then proceeds to restore the tool's dependencies as specified in its project file.</span></span>

### <a name="nugetconfig-differences"></a><span data-ttu-id="73c50-130">NuGet. config farklılıkları</span><span class="sxs-lookup"><span data-stu-id="73c50-130">nuget.config differences</span></span>

<span data-ttu-id="73c50-131">Komutun davranışı, varsa `dotnet restore` *NuGet. config* dosyasındaki ayarlardan etkilenir.</span><span class="sxs-lookup"><span data-stu-id="73c50-131">The behavior of the `dotnet restore` command is affected by the settings in the *nuget.config* file, if present.</span></span> <span data-ttu-id="73c50-132">Örneğin, `globalPackagesFolder` *NuGet. config* içindeki ayarı, geri yüklenen NuGet paketlerini belirtilen klasöre koyar.</span><span class="sxs-lookup"><span data-stu-id="73c50-132">For example, setting the `globalPackagesFolder` in *nuget.config* places the restored NuGet packages in the specified folder.</span></span> <span data-ttu-id="73c50-133">Bu seçenek, komutunda seçeneğini belirtmeye yönelik bir alternatiftir `--packages` `dotnet restore` .</span><span class="sxs-lookup"><span data-stu-id="73c50-133">This is an alternative to specifying the `--packages` option on the `dotnet restore` command.</span></span> <span data-ttu-id="73c50-134">Daha fazla bilgi için bkz. [NuGet. config başvurusu](/nuget/schema/nuget-config-file).</span><span class="sxs-lookup"><span data-stu-id="73c50-134">For more information, see the [nuget.config reference](/nuget/schema/nuget-config-file).</span></span>

<span data-ttu-id="73c50-135">Yok sayan üç özel ayar vardır `dotnet restore` :</span><span class="sxs-lookup"><span data-stu-id="73c50-135">There are three specific settings that `dotnet restore` ignores:</span></span>

- [<span data-ttu-id="73c50-136">Bindingyönlendirmeler</span><span class="sxs-lookup"><span data-stu-id="73c50-136">bindingRedirects</span></span>](/nuget/schema/nuget-config-file#bindingredirects-section)

  <span data-ttu-id="73c50-137">Bağlama yeniden yönlendirmeleri öğelerle çalışmaz `<PackageReference>` ve .NET Core yalnızca `<PackageReference>` NuGet paketleri için öğeleri destekler.</span><span class="sxs-lookup"><span data-stu-id="73c50-137">Binding redirects don't work with `<PackageReference>` elements and .NET Core only supports `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="73c50-138">çözümden</span><span class="sxs-lookup"><span data-stu-id="73c50-138">solution</span></span>](/nuget/schema/nuget-config-file#solution-section)

  <span data-ttu-id="73c50-139">Bu ayar Visual Studio 'ya özeldir ve .NET Core için uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="73c50-139">This setting is Visual Studio specific and doesn't apply to .NET Core.</span></span> <span data-ttu-id="73c50-140">.NET Core bir dosya kullanmaz `packages.config` ve bunun yerine `<PackageReference>` NuGet paketleri için öğeleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="73c50-140">.NET Core doesn't use a `packages.config` file and instead uses `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="73c50-141">trustedSigners</span><span class="sxs-lookup"><span data-stu-id="73c50-141">trustedSigners</span></span>](/nuget/schema/nuget-config-file#trustedsigners-section)

  <span data-ttu-id="73c50-142">NuGet, güvenilen paketlerin [platformlar arası doğrulanmasını henüz desteklemediğinden](https://github.com/NuGet/Home/issues/7939) , bu ayar geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="73c50-142">This setting isn't applicable as [NuGet doesn't yet support cross-platform verification](https://github.com/NuGet/Home/issues/7939) of trusted packages.</span></span>

## <a name="arguments"></a><span data-ttu-id="73c50-143">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="73c50-143">Arguments</span></span>

- **`ROOT`**

  <span data-ttu-id="73c50-144">Geri yüklenecek proje dosyasının isteğe bağlı yolu.</span><span class="sxs-lookup"><span data-stu-id="73c50-144">Optional path to the project file to restore.</span></span>

## <a name="options"></a><span data-ttu-id="73c50-145">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="73c50-145">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="73c50-146">Geri yükleme işlemi için kullanılacak NuGet yapılandırma dosyası (*NuGet. config*).</span><span class="sxs-lookup"><span data-stu-id="73c50-146">The NuGet configuration file (*nuget.config*) to use for the restore operation.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="73c50-147">Paralel olarak birden çok projenin geri yüklenmesini devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="73c50-147">Disables restoring multiple projects in parallel.</span></span>

- **`--force`**

  <span data-ttu-id="73c50-148">Son geri yükleme başarılı olsa bile tüm bağımlılıkların çözülmesini zorlar.</span><span class="sxs-lookup"><span data-stu-id="73c50-148">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="73c50-149">Bu bayrağın belirtilmesi, *Project. varlıklar. JSON* dosyasını silme ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="73c50-149">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`--force-evaluate`**

  <span data-ttu-id="73c50-150">Bir kilit dosyası zaten mevcut olsa bile, geri yüklemeyi tüm bağımlılıklara yeniden değerlendirmeye zorlar.</span><span class="sxs-lookup"><span data-stu-id="73c50-150">Forces restore to reevaluate all dependencies even if a lock file already exists.</span></span>

- **`-h|--help`**

  <span data-ttu-id="73c50-151">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="73c50-151">Prints out a short help for the command.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="73c50-152">Yalnızca sürüm gereksinimini karşılayan paketler varsa başarısız kaynaklar hakkında uyar.</span><span class="sxs-lookup"><span data-stu-id="73c50-152">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

- **`--interactive`**

  <span data-ttu-id="73c50-153">Komutun Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir (örneğin, kimlik doğrulamasını tamamlamaya).</span><span class="sxs-lookup"><span data-stu-id="73c50-153">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span> <span data-ttu-id="73c50-154">.NET Core 2.1.400 'dan beri.</span><span class="sxs-lookup"><span data-stu-id="73c50-154">Since .NET Core 2.1.400.</span></span>

- **`--lock-file-path <LOCK_FILE_PATH>`**

  <span data-ttu-id="73c50-155">Proje kilit dosyasının yazıldığı çıkış konumu.</span><span class="sxs-lookup"><span data-stu-id="73c50-155">Output location where project lock file is written.</span></span> <span data-ttu-id="73c50-156">Bu, varsayılan olarak *PROJECT_ROOT \packages.Lock.JSON*.</span><span class="sxs-lookup"><span data-stu-id="73c50-156">By default, this is *PROJECT_ROOT\packages.lock.json*.</span></span>

- **`--locked-mode`**

  <span data-ttu-id="73c50-157">Proje kilit dosyası güncelleştirilmeye izin verme.</span><span class="sxs-lookup"><span data-stu-id="73c50-157">Don't allow updating project lock file.</span></span>

- **`--no-cache`**

  <span data-ttu-id="73c50-158">HTTP isteklerinin önbelleğe alınamadı belirtir.</span><span class="sxs-lookup"><span data-stu-id="73c50-158">Specifies to not cache HTTP requests.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="73c50-159">Projeden projeye (P2P) başvuruları olan bir projeyi geri yüklerken, başvuruları değil kök projeyi geri yükler.</span><span class="sxs-lookup"><span data-stu-id="73c50-159">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

- **`--packages <PACKAGES_DIRECTORY>`**

  <span data-ttu-id="73c50-160">Geri yüklenen paketlerin dizinini belirtir.</span><span class="sxs-lookup"><span data-stu-id="73c50-160">Specifies the directory for restored packages.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="73c50-161">Paket geri yüklemesi için bir çalışma zamanı belirtir.</span><span class="sxs-lookup"><span data-stu-id="73c50-161">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="73c50-162">Bu, `<RuntimeIdentifiers>` *. csproj* dosyasındaki etiketinde açıkça listelenmeyen çalışma zamanları paketlerini geri yüklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="73c50-162">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="73c50-163">Çalışma zamanı tanımlayıcıları (RID 'Ler) listesi için bkz. [RID kataloğu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="73c50-163">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="73c50-164">Bu seçeneği birden çok kez belirterek birden çok grup belirtin.</span><span class="sxs-lookup"><span data-stu-id="73c50-164">Provide multiple RIDs by specifying this option multiple times.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="73c50-165">Geri yükleme işlemi sırasında kullanılacak NuGet paket kaynağının URI 'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="73c50-165">Specifies the URI of the NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="73c50-166">Bu ayar *NuGet. config* dosyalarında belirtilen tüm kaynakları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="73c50-166">This setting overrides all of the sources specified in the *nuget.config* files.</span></span> <span data-ttu-id="73c50-167">Bu seçenek birden çok kez belirtilerek birden çok kaynak sağlanarak sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73c50-167">Multiple sources can be provided by specifying this option multiple times.</span></span>

- **`--use-lock-file`**

  <span data-ttu-id="73c50-168">Proje kilitleme dosyasının oluşturulup geri yükleme ile kullanılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="73c50-168">Enables project lock file to be generated and used with restore.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="73c50-169">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="73c50-169">Sets the verbosity level of the command.</span></span> <span data-ttu-id="73c50-170">İzin verilen değerler,,, `q[uiet]` `m[inimal]` `n[ormal]` `d[etailed]` ve `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="73c50-170">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="73c50-171">Varsayılan değer `minimal` .</span><span class="sxs-lookup"><span data-stu-id="73c50-171">Default value is `minimal`.</span></span>

## <a name="examples"></a><span data-ttu-id="73c50-172">Örnekler</span><span class="sxs-lookup"><span data-stu-id="73c50-172">Examples</span></span>

- <span data-ttu-id="73c50-173">Geçerli dizindeki proje için bağımlılıkları ve araçları geri yükle:</span><span class="sxs-lookup"><span data-stu-id="73c50-173">Restore dependencies and tools for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet restore
  ```

- <span data-ttu-id="73c50-174">Verilen yolda bulunan projenin bağımlılıklarını ve araçlarını geri yükleyin `app1` :</span><span class="sxs-lookup"><span data-stu-id="73c50-174">Restore dependencies and tools for the `app1` project found in the   given path:</span></span>

  ```dotnetcli
  dotnet restore ~/projects/app1/app1.csproj
  ```

- <span data-ttu-id="73c50-175">Kaynak olarak belirtilen dosya yolunu kullanarak geçerli dizindeki proje için bağımlılıkları ve araçları geri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="73c50-175">Restore the dependencies and tools for the project in the current   directory using the file path provided as the source:</span></span>

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages
  ```

- <span data-ttu-id="73c50-176">Kaynak olarak girilen iki dosya yolunu kullanarak geçerli dizindeki proje için bağımlılıkları ve araçları geri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="73c50-176">Restore the dependencies and tools for the project in the current   directory using the two file paths provided as sources:</span></span>

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages
  ```

- <span data-ttu-id="73c50-177">Geçerli dizindeki proje için bağımlılıkları ve araçları ayrıntılı çıktıyı gösteren geri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="73c50-177">Restore dependencies and tools for the project in the current directory   showing detailed output:</span></span>

  ```dotnetcli
  dotnet restore --verbosity detailed
  ```
