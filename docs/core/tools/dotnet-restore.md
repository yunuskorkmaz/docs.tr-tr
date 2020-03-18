---
title: dotnet geri yükleme komutu
description: Dotnet geri yükleme komutuyla bağımlılıkları ve projeye özgü araçları nasıl geri yükleyebileceğinizi öğrenin.
ms.date: 02/27/2020
ms.openlocfilehash: e74027ba70ddf6905a12f9691caeb0a406428ad6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78157030"
---
# <a name="dotnet-restore"></a><span data-ttu-id="350dd-103">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="350dd-103">dotnet restore</span></span>

<span data-ttu-id="350dd-104">**Bu makale şu şekilde dir:** ✔️ .NET Core 2.1 SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="350dd-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="350dd-105">Adı</span><span class="sxs-lookup"><span data-stu-id="350dd-105">Name</span></span>

<span data-ttu-id="350dd-106">`dotnet restore`- Projenin bağımlılıklarını ve araçlarını geri yükler.</span><span class="sxs-lookup"><span data-stu-id="350dd-106">`dotnet restore` - Restores the dependencies and tools of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="350dd-107">Özet</span><span class="sxs-lookup"><span data-stu-id="350dd-107">Synopsis</span></span>

```dotnetcli
dotnet restore [<ROOT>] [--configfile] [--disable-parallel]
    [--force] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime]
    [-s|--source] [-v|--verbosity] [--interactive]

dotnet restore [-h|--help]
```

## <a name="description"></a><span data-ttu-id="350dd-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="350dd-108">Description</span></span>

<span data-ttu-id="350dd-109">Komut, `dotnet restore` proje dosyasında belirtilen projeye özgü araçların yanı sıra bağımlılıkları geri yüklemek için NuGet'i kullanır.</span><span class="sxs-lookup"><span data-stu-id="350dd-109">The `dotnet restore` command uses NuGet to restore dependencies as well as project-specific tools that are specified in the project file.</span></span> <span data-ttu-id="350dd-110">Varsayılan olarak, bağımlılıkların ve araçların geri yükleme paralel olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="350dd-110">By default, the restoration of dependencies and tools are executed in parallel.</span></span>

<span data-ttu-id="350dd-111">Bağımlılıkları geri yüklemek için NuGet'in paketlerin bulunduğu akışlara ihtiyacı vardır.</span><span class="sxs-lookup"><span data-stu-id="350dd-111">To restore the dependencies, NuGet needs the feeds where the packages are located.</span></span> <span data-ttu-id="350dd-112">Özet akışları genellikle *nuget.config* yapılandırma dosyası üzerinden sağlanır.</span><span class="sxs-lookup"><span data-stu-id="350dd-112">Feeds are usually provided via the *nuget.config* configuration file.</span></span> <span data-ttu-id="350dd-113">.NET Core SDK yüklendiğinde varsayılan yapılandırma dosyası sağlanır.</span><span class="sxs-lookup"><span data-stu-id="350dd-113">A default configuration file is provided when the .NET Core SDK is installed.</span></span> <span data-ttu-id="350dd-114">Proje dizininde kendi *nuget.config* dosyanızı oluşturarak ek akışlar belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="350dd-114">You specify additional feeds by creating your own *nuget.config* file in the project directory.</span></span> <span data-ttu-id="350dd-115">*Nuget.config* beslemelerini - `-s` seçeneği ile geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="350dd-115">You can override the *nuget.config* feeds with the - `-s` option.</span></span>

<span data-ttu-id="350dd-116">Bağımlılıklar için, bağımsız değişkeni kullanarak geri yükleme işlemi `--packages` sırasında geri yüklenen paketlerin nereye yerleştirildiğini belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="350dd-116">For dependencies, you specify where the restored packages are placed during the restore operation using the `--packages` argument.</span></span> <span data-ttu-id="350dd-117">Belirtilmemişse, varsayılan NuGet paket önbelleği kullanılır `.nuget/packages` ve bu da tüm işletim sistemlerinde kullanıcının ev dizininde bulunan dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="350dd-117">If not specified, the default NuGet package cache is used, which is found in the `.nuget/packages` directory in the user's home directory on all operating systems.</span></span> <span data-ttu-id="350dd-118">Örneğin, *Linux'ta /home/user1* veya Windows'da *C:\Users\user1.*</span><span class="sxs-lookup"><span data-stu-id="350dd-118">For example, */home/user1* on Linux or *C:\Users\user1* on Windows.</span></span>

<span data-ttu-id="350dd-119">Projeye özgü takımlama `dotnet restore` için, önce aracın paketlendiği paketi geri yükler, sonra da proje dosyasında belirtildiği şekilde aracın bağımlılıklarını geri yüklemeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="350dd-119">For project-specific tooling, `dotnet restore` first restores the package in which the tool is packed, and then proceeds to restore the tool's dependencies as specified in its project file.</span></span>

### <a name="nugetconfig-differences"></a><span data-ttu-id="350dd-120">nuget.config farklar</span><span class="sxs-lookup"><span data-stu-id="350dd-120">nuget.config differences</span></span>

<span data-ttu-id="350dd-121">`dotnet restore` Komutun davranışı *nuget.config* dosyasındaki ayarlardan etkilenir, varsa.</span><span class="sxs-lookup"><span data-stu-id="350dd-121">The behavior of the `dotnet restore` command is affected by the settings in the *nuget.config* file, if present.</span></span> <span data-ttu-id="350dd-122">Örneğin, `globalPackagesFolder` *nuget.config'de* ayarla, geri yüklenen NuGet paketlerini belirtilen klasöre yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="350dd-122">For example, setting the `globalPackagesFolder` in *nuget.config* places the restored NuGet packages in the specified folder.</span></span> <span data-ttu-id="350dd-123">Bu, komuttaki `--packages` seçeneği belirtmeye `dotnet restore` alternatiftir.</span><span class="sxs-lookup"><span data-stu-id="350dd-123">This is an alternative to specifying the `--packages` option on the `dotnet restore` command.</span></span> <span data-ttu-id="350dd-124">Daha fazla bilgi için [nuget.config referansına](/nuget/schema/nuget-config-file)bakın.</span><span class="sxs-lookup"><span data-stu-id="350dd-124">For more information, see the [nuget.config reference](/nuget/schema/nuget-config-file).</span></span>

<span data-ttu-id="350dd-125">Yoksayan `dotnet restore` üç özel ayar vardır:</span><span class="sxs-lookup"><span data-stu-id="350dd-125">There are three specific settings that `dotnet restore` ignores:</span></span>

- [<span data-ttu-id="350dd-126">bindingYönlendirmeler</span><span class="sxs-lookup"><span data-stu-id="350dd-126">bindingRedirects</span></span>](/nuget/schema/nuget-config-file#bindingredirects-section)

  <span data-ttu-id="350dd-127">Bağlama yönlendirmeleri öğelerle `<PackageReference>` çalışmaz ve .NET `<PackageReference>` Core yalnızca NuGet paketleri için öğeleri destekler.</span><span class="sxs-lookup"><span data-stu-id="350dd-127">Binding redirects don't work with `<PackageReference>` elements and .NET Core only supports `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="350dd-128">Çözüm</span><span class="sxs-lookup"><span data-stu-id="350dd-128">solution</span></span>](/nuget/schema/nuget-config-file#solution-section)

  <span data-ttu-id="350dd-129">Bu ayar Visual Studio'ya özgüdür ve .NET Core için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="350dd-129">This setting is Visual Studio specific and doesn't apply to .NET Core.</span></span> <span data-ttu-id="350dd-130">.NET Core bir `packages.config` dosya kullanmaz `<PackageReference>` ve bunun yerine NuGet paketleri için öğeleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="350dd-130">.NET Core doesn't use a `packages.config` file and instead uses `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="350dd-131">güvenilir Signers</span><span class="sxs-lookup"><span data-stu-id="350dd-131">trustedSigners</span></span>](/nuget/schema/nuget-config-file#trustedsigners-section)

  <span data-ttu-id="350dd-132">NuGet henüz güvenilir paketlerin [platformlar arası doğrulanmasını desteklemediği](https://github.com/NuGet/Home/issues/7939) için bu ayar geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="350dd-132">This setting isn't applicable as [NuGet doesn't yet support cross-platform verification](https://github.com/NuGet/Home/issues/7939) of trusted packages.</span></span>

## <a name="implicit-restore"></a><span data-ttu-id="350dd-133">Örtük geri yükleme</span><span class="sxs-lookup"><span data-stu-id="350dd-133">Implicit restore</span></span>

<span data-ttu-id="350dd-134">Aşağıdaki `dotnet restore` komutları çalıştırdığınızda gerekirse komut örtülü olarak çalıştırılır:</span><span class="sxs-lookup"><span data-stu-id="350dd-134">The `dotnet restore` command is run implicitly if necessary when you run the following commands:</span></span>

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

<span data-ttu-id="350dd-135">Çoğu durumda, komutu `dotnet restore` açıkça kullanmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="350dd-135">In most cases, you don't need to explicitly use the `dotnet restore` command.</span></span>

<span data-ttu-id="350dd-136">Bazen, dolaylı olarak çalıştırmak `dotnet restore` rahatsız edici olabilir.</span><span class="sxs-lookup"><span data-stu-id="350dd-136">Sometimes, it might be inconvenient to run `dotnet restore` implicitly.</span></span> <span data-ttu-id="350dd-137">Örneğin, yapı sistemleri gibi bazı otomatik sistemlerin, `dotnet restore` ağ kullanımını denetleyebilmeleri için geri yüklemenin ne zaman gerçekleşebileceğini denetlemek için açıkça aramaları gerekir.</span><span class="sxs-lookup"><span data-stu-id="350dd-137">For example, some automated systems, such as build systems, need to call `dotnet restore` explicitly to control when the restore occurs so that they can control network usage.</span></span> <span data-ttu-id="350dd-138">Örtülü `dotnet restore` olarak çalışmasını önlemek için, `--no-restore` örtük geri yüklemeyi devre dışı bırakmada bu komutlardan herhangi biriyle bayrağı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="350dd-138">To prevent `dotnet restore` from running implicitly, you can use the `--no-restore` flag with any of these commands to disable implicit restore.</span></span>

## <a name="arguments"></a><span data-ttu-id="350dd-139">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="350dd-139">Arguments</span></span>

- **`ROOT`**

  <span data-ttu-id="350dd-140">Geri yükleme için proje dosyasına isteğe bağlı yol.</span><span class="sxs-lookup"><span data-stu-id="350dd-140">Optional path to the project file to restore.</span></span>

## <a name="options"></a><span data-ttu-id="350dd-141">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="350dd-141">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="350dd-142">NuGet yapılandırma dosyası (*nuget.config*) geri yükleme işlemi için kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="350dd-142">The NuGet configuration file (*nuget.config*) to use for the restore operation.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="350dd-143">Birden çok projeyi paralel olarak geri devre dışı kılabilir.</span><span class="sxs-lookup"><span data-stu-id="350dd-143">Disables restoring multiple projects in parallel.</span></span>

- **`--force`**

  <span data-ttu-id="350dd-144">Son geri yükleme başarılı olsa bile tüm bağımlılıkları çözüme kavuşturmaya zorlar.</span><span class="sxs-lookup"><span data-stu-id="350dd-144">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="350dd-145">Bu bayrağı *belirtmek, project.assets.json* dosyasını silmekle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="350dd-145">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="350dd-146">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="350dd-146">Prints out a short help for the command.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="350dd-147">Yalnızca sürüm gereksinimini karşılayan paketler varsa, başarısız kaynaklar hakkında uyarıda bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="350dd-147">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

- **`--no-cache`**

  <span data-ttu-id="350dd-148">Önbellek paketleri ve HTTP isteklerini belirtim.</span><span class="sxs-lookup"><span data-stu-id="350dd-148">Specifies to not cache packages and HTTP requests.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="350dd-149">Projeden projeye (P2P) başvurularla projeyi geri yüklediğinizde, başvuruları değil, kök projeyi geri yükler.</span><span class="sxs-lookup"><span data-stu-id="350dd-149">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

- **`--packages <PACKAGES_DIRECTORY>`**

  <span data-ttu-id="350dd-150">Geri yüklenen paketler için dizini belirtir.</span><span class="sxs-lookup"><span data-stu-id="350dd-150">Specifies the directory for restored packages.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="350dd-151">Paket geri yüklemesi için bir çalışma zamanı belirtir.</span><span class="sxs-lookup"><span data-stu-id="350dd-151">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="350dd-152">Bu, `<RuntimeIdentifiers>` *.csproj* dosyasındaki etikette açıkça belirtilmeyen çalışma süreleri için paketleri geri yüklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="350dd-152">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="350dd-153">Runtime Tanımlayıcıları (RID'ler) listesi için RID [kataloğuna](../rid-catalog.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="350dd-153">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="350dd-154">Bu seçeneği birden çok kez belirterek birden çok RID sağlayın.</span><span class="sxs-lookup"><span data-stu-id="350dd-154">Provide multiple RIDs by specifying this option multiple times.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="350dd-155">Geri yükleme işlemi sırasında kullanılacak bir NuGet paket kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="350dd-155">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="350dd-156">Bu ayar *nuget.config* dosyalarında belirtilen tüm kaynakları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="350dd-156">This setting overrides all of the sources specified in the *nuget.config* files.</span></span> <span data-ttu-id="350dd-157">Bu seçeneği birden çok kez belirterek birden çok kaynak sağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="350dd-157">Multiple sources can be provided by specifying this option multiple times.</span></span>

- **`--verbosity <LEVEL>`**

  <span data-ttu-id="350dd-158">Komutun ayrıntılı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="350dd-158">Sets the verbosity level of the command.</span></span> <span data-ttu-id="350dd-159">İzin verilen `q[uiet]` `m[inimal]`değerler `n[ormal]` `d[etailed]`, `diag[nostic]`, , , ve .</span><span class="sxs-lookup"><span data-stu-id="350dd-159">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="350dd-160">Varsayılan değer. `minimal`</span><span class="sxs-lookup"><span data-stu-id="350dd-160">Default value is `minimal`.</span></span>

- **`--interactive`**

  <span data-ttu-id="350dd-161">Komutun durmasına ve kullanıcı girişinin veya eylemini beklemesine izin verir (örneğin kimlik doğrulamasını tamamlamak için).</span><span class="sxs-lookup"><span data-stu-id="350dd-161">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span> <span data-ttu-id="350dd-162">.NET Core 2.1.400'den beri.</span><span class="sxs-lookup"><span data-stu-id="350dd-162">Since .NET Core 2.1.400.</span></span>

## <a name="examples"></a><span data-ttu-id="350dd-163">Örnekler</span><span class="sxs-lookup"><span data-stu-id="350dd-163">Examples</span></span>

- <span data-ttu-id="350dd-164">Geçerli dizindeki proje için bağımlılıkları ve araçları geri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="350dd-164">Restore dependencies and tools for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet restore
  ```

- <span data-ttu-id="350dd-165">Verilen yolda bulunan `app1` proje için bağımlılıkları ve araçları geri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="350dd-165">Restore dependencies and tools for the `app1` project found in the   given path:</span></span>

  ```dotnetcli
  dotnet restore ~/projects/app1/app1.csproj
  ```

- <span data-ttu-id="350dd-166">Kaynak olarak sağlanan dosya yolunu kullanarak geçerli dizindeki projeye ilişkin bağımlılıkları ve araçları geri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="350dd-166">Restore the dependencies and tools for the project in the current   directory using the file path provided as the source:</span></span>

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages
  ```

- <span data-ttu-id="350dd-167">Kaynak olarak sağlanan iki dosya yolunu kullanarak geçerli dizindeki proje ye bağımlılıkları ve araçları geri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="350dd-167">Restore the dependencies and tools for the project in the current   directory using the two file paths provided as sources:</span></span>

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages
  ```

- <span data-ttu-id="350dd-168">Ayrıntılı çıktıyı gösteren geçerli dizinde proje için bağımlılıkları ve araçları geri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="350dd-168">Restore dependencies and tools for the project in the current directory   showing detailed output:</span></span>

  ```dotnetcli
  dotnet restore --verbosity detailed
  ```
