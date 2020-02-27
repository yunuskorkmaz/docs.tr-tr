---
title: dotnet restore komutu
description: Dotnet restore komutuyla bağımlılıkları ve projeye özel araçları nasıl geri yükleyeceğinizi öğrenin.
ms.date: 05/29/2018
ms.openlocfilehash: c221e8a34e844d0ad0482d2bb4aa6e1c795555ca
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626066"
---
# <a name="dotnet-restore"></a><span data-ttu-id="9aecc-103">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="9aecc-103">dotnet restore</span></span>

<span data-ttu-id="9aecc-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="9aecc-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="9aecc-105">Adı</span><span class="sxs-lookup"><span data-stu-id="9aecc-105">Name</span></span>

<span data-ttu-id="9aecc-106">`dotnet restore`-bir projenin bağımlılıklarını ve araçlarını geri yükler.</span><span class="sxs-lookup"><span data-stu-id="9aecc-106">`dotnet restore` - Restores the dependencies and tools of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="9aecc-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="9aecc-107">Synopsis</span></span>

```dotnetcli
dotnet restore [<ROOT>] [--configfile] [--disable-parallel]
    [--force] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime]
    [-s|--source] [-v|--verbosity] [--interactive]

dotnet restore [-h|--help]
```

## <a name="description"></a><span data-ttu-id="9aecc-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9aecc-108">Description</span></span>

<span data-ttu-id="9aecc-109">`dotnet restore` komutu,, bağımlılıkları geri yüklemek için NuGet kullanır ve proje dosyasında belirtilen projeye özgü araçlardır.</span><span class="sxs-lookup"><span data-stu-id="9aecc-109">The `dotnet restore` command uses NuGet to restore dependencies as well as project-specific tools that are specified in the project file.</span></span> <span data-ttu-id="9aecc-110">Varsayılan olarak, bağımlılıklar ve araçların geri yüklenmesi paralel olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="9aecc-110">By default, the restoration of dependencies and tools are executed in parallel.</span></span>

<span data-ttu-id="9aecc-111">Bağımlılıkları geri yüklemek için, NuGet paketlerin bulunduğu akışlara ihtiyaç duyuyor.</span><span class="sxs-lookup"><span data-stu-id="9aecc-111">To restore the dependencies, NuGet needs the feeds where the packages are located.</span></span> <span data-ttu-id="9aecc-112">Akışlar genellikle *NuGet. config* yapılandırma dosyası aracılığıyla sağlanır.</span><span class="sxs-lookup"><span data-stu-id="9aecc-112">Feeds are usually provided via the *nuget.config* configuration file.</span></span> <span data-ttu-id="9aecc-113">.NET Core SDK yüklendiğinde varsayılan bir yapılandırma dosyası sağlanır.</span><span class="sxs-lookup"><span data-stu-id="9aecc-113">A default configuration file is provided when the .NET Core SDK is installed.</span></span> <span data-ttu-id="9aecc-114">Proje dizininde kendi *NuGet. config* dosyanızı oluşturarak ek akışlar belirlersiniz.</span><span class="sxs-lookup"><span data-stu-id="9aecc-114">You specify additional feeds by creating your own *nuget.config* file in the project directory.</span></span> <span data-ttu-id="9aecc-115">*NuGet. config* akışlarını-`-s` seçeneğiyle geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9aecc-115">You can override the *nuget.config* feeds with the - `-s` option.</span></span>

<span data-ttu-id="9aecc-116">Bağımlılıklar için, geri yükleme işlemi sırasında `--packages` bağımsız değişkenini kullanarak geri yüklenen paketlerin nereye yerleştirileceğini belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9aecc-116">For dependencies, you specify where the restored packages are placed during the restore operation using the `--packages` argument.</span></span> <span data-ttu-id="9aecc-117">Belirtilmezse, varsayılan NuGet paketi önbelleği kullanılır ve bu, kullanıcının tüm işletim sistemlerindeki giriş dizinindeki `.nuget/packages` dizininde bulunur.</span><span class="sxs-lookup"><span data-stu-id="9aecc-117">If not specified, the default NuGet package cache is used, which is found in the `.nuget/packages` directory in the user's home directory on all operating systems.</span></span> <span data-ttu-id="9aecc-118">Örneğin, Linux üzerinde */home/user1* veya Windows üzerinde *c:\Users\User1* .</span><span class="sxs-lookup"><span data-stu-id="9aecc-118">For example, */home/user1* on Linux or *C:\Users\user1* on Windows.</span></span>

<span data-ttu-id="9aecc-119">Projeye özgü araçlar için `dotnet restore` önce aracın paketlenmesi gereken paketi geri yükler, sonra da araç bağımlılıklarını proje dosyasında belirtilen şekilde geri yüklemeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="9aecc-119">For project-specific tooling, `dotnet restore` first restores the package in which the tool is packed, and then proceeds to restore the tool's dependencies as specified in its project file.</span></span>

### <a name="nugetconfig-differences"></a><span data-ttu-id="9aecc-120">NuGet. config farklılıkları</span><span class="sxs-lookup"><span data-stu-id="9aecc-120">nuget.config differences</span></span>

<span data-ttu-id="9aecc-121">`dotnet restore` komutunun davranışı, varsa *NuGet. config* dosyasındaki ayarlardan etkilenir.</span><span class="sxs-lookup"><span data-stu-id="9aecc-121">The behavior of the `dotnet restore` command is affected by the settings in the *nuget.config* file, if present.</span></span> <span data-ttu-id="9aecc-122">Örneğin, *NuGet. config* dosyasındaki `globalPackagesFolder` ayarlamak, geri yüklenen NuGet paketlerini belirtilen klasöre koyar.</span><span class="sxs-lookup"><span data-stu-id="9aecc-122">For example, setting the `globalPackagesFolder` in *nuget.config* places the restored NuGet packages in the specified folder.</span></span> <span data-ttu-id="9aecc-123">Bu, `dotnet restore` komutunda `--packages` seçeneğinin belirtilmesine alternatiftir.</span><span class="sxs-lookup"><span data-stu-id="9aecc-123">This is an alternative to specifying the `--packages` option on the `dotnet restore` command.</span></span> <span data-ttu-id="9aecc-124">Daha fazla bilgi için bkz. [NuGet. config başvurusu](/nuget/schema/nuget-config-file).</span><span class="sxs-lookup"><span data-stu-id="9aecc-124">For more information, see the [nuget.config reference](/nuget/schema/nuget-config-file).</span></span>

<span data-ttu-id="9aecc-125">`dotnet restore` göz ardı eden üç özel ayar vardır:</span><span class="sxs-lookup"><span data-stu-id="9aecc-125">There are three specific settings that `dotnet restore` ignores:</span></span>

- [<span data-ttu-id="9aecc-126">Bindingyönlendirmeler</span><span class="sxs-lookup"><span data-stu-id="9aecc-126">bindingRedirects</span></span>](/nuget/schema/nuget-config-file#bindingredirects-section)

  <span data-ttu-id="9aecc-127">Bağlama yeniden yönlendirmeleri `<PackageReference>` öğeleriyle çalışmaz ve .NET Core yalnızca NuGet paketleri için `<PackageReference>` öğelerini destekler.</span><span class="sxs-lookup"><span data-stu-id="9aecc-127">Binding redirects don't work with `<PackageReference>` elements and .NET Core only supports `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="9aecc-128">çözümden</span><span class="sxs-lookup"><span data-stu-id="9aecc-128">solution</span></span>](/nuget/schema/nuget-config-file#solution-section)

  <span data-ttu-id="9aecc-129">Bu ayar Visual Studio 'ya özeldir ve .NET Core için uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="9aecc-129">This setting is Visual Studio specific and doesn't apply to .NET Core.</span></span> <span data-ttu-id="9aecc-130">.NET Core bir `packages.config` dosyası kullanmaz ve bunun yerine NuGet paketleri için `<PackageReference>` öğeleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="9aecc-130">.NET Core doesn't use a `packages.config` file and instead uses `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="9aecc-131">trustedSigners</span><span class="sxs-lookup"><span data-stu-id="9aecc-131">trustedSigners</span></span>](/nuget/schema/nuget-config-file#trustedsigners-section)

  <span data-ttu-id="9aecc-132">NuGet, güvenilen paketlerin [platformlar arası doğrulanmasını henüz desteklemediğinden](https://github.com/NuGet/Home/issues/7939) , bu ayar geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="9aecc-132">This setting isn't applicable as [NuGet doesn't yet support cross-platform verification](https://github.com/NuGet/Home/issues/7939) of trusted packages.</span></span>

## <a name="implicit-restore"></a><span data-ttu-id="9aecc-133">Örtük geri yükleme</span><span class="sxs-lookup"><span data-stu-id="9aecc-133">Implicit restore</span></span>

<span data-ttu-id="9aecc-134">Aşağıdaki komutları çalıştırdığınızda, gerekirse `dotnet restore` komutu örtülü olarak çalıştırılır:</span><span class="sxs-lookup"><span data-stu-id="9aecc-134">The `dotnet restore` command is run implicitly if necessary when you run the following commands:</span></span>

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

<span data-ttu-id="9aecc-135">Çoğu durumda, `dotnet restore` komutunu açıkça kullanmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="9aecc-135">In most cases, you don't need to explicitly use the `dotnet restore` command.</span></span>

<span data-ttu-id="9aecc-136">Bazen `dotnet restore`, örtük olarak çalıştırmak kullanışlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="9aecc-136">Sometimes, it might be inconvenient to run `dotnet restore` implicitly.</span></span> <span data-ttu-id="9aecc-137">Örneğin, derleme sistemleri gibi bazı otomatikleştirilmiş sistemlerin, ağ kullanımını denetleyebilmeleri için geri yükleme işleminin ne zaman gerçekleşeceğini denetlemek üzere `dotnet restore` çağrısı yapması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9aecc-137">For example, some automated systems, such as build systems, need to call `dotnet restore` explicitly to control when the restore occurs so that they can control network usage.</span></span> <span data-ttu-id="9aecc-138">`dotnet restore` örtük olarak çalışmasını engellemek için, örtük geri yüklemeyi devre dışı bırakmak üzere bu komutlardan herhangi biriyle `--no-restore` bayrağını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9aecc-138">To prevent `dotnet restore` from running implicitly, you can use the `--no-restore` flag with any of these commands to disable implicit restore.</span></span>

## <a name="arguments"></a><span data-ttu-id="9aecc-139">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="9aecc-139">Arguments</span></span>

- **`ROOT`**

  <span data-ttu-id="9aecc-140">Geri yüklenecek proje dosyasının isteğe bağlı yolu.</span><span class="sxs-lookup"><span data-stu-id="9aecc-140">Optional path to the project file to restore.</span></span>

## <a name="options"></a><span data-ttu-id="9aecc-141">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="9aecc-141">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="9aecc-142">Geri yükleme işlemi için kullanılacak NuGet yapılandırma dosyası (*NuGet. config*).</span><span class="sxs-lookup"><span data-stu-id="9aecc-142">The NuGet configuration file (*nuget.config*) to use for the restore operation.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="9aecc-143">Paralel olarak birden çok projenin geri yüklenmesini devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="9aecc-143">Disables restoring multiple projects in parallel.</span></span>

- **`--force`**

  <span data-ttu-id="9aecc-144">Son geri yükleme başarılı olsa bile tüm bağımlılıkların çözülmesini zorlar.</span><span class="sxs-lookup"><span data-stu-id="9aecc-144">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="9aecc-145">Bu bayrağın belirtilmesi, *Project. varlıklar. JSON* dosyasını silme ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="9aecc-145">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="9aecc-146">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="9aecc-146">Prints out a short help for the command.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="9aecc-147">Yalnızca sürüm gereksinimini karşılayan paketler varsa başarısız kaynaklar hakkında uyar.</span><span class="sxs-lookup"><span data-stu-id="9aecc-147">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

- **`--no-cache`**

  <span data-ttu-id="9aecc-148">Paketlerin ve HTTP isteklerinin önbelleğe alınamadı belirtir.</span><span class="sxs-lookup"><span data-stu-id="9aecc-148">Specifies to not cache packages and HTTP requests.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="9aecc-149">Projeden projeye (P2P) başvuruları olan bir projeyi geri yüklerken, başvuruları değil kök projeyi geri yükler.</span><span class="sxs-lookup"><span data-stu-id="9aecc-149">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

- **`--packages <PACKAGES_DIRECTORY>`**

  <span data-ttu-id="9aecc-150">Geri yüklenen paketlerin dizinini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9aecc-150">Specifies the directory for restored packages.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="9aecc-151">Paket geri yüklemesi için bir çalışma zamanı belirtir.</span><span class="sxs-lookup"><span data-stu-id="9aecc-151">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="9aecc-152">Bu, *. csproj* dosyasındaki `<RuntimeIdentifiers>` etiketinde açıkça listelenmeyen çalışma zamanları paketlerini geri yüklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9aecc-152">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="9aecc-153">Çalışma zamanı tanımlayıcıları (RID 'Ler) listesi için bkz. [RID kataloğu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="9aecc-153">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="9aecc-154">Bu seçeneği birden çok kez belirterek birden çok grup belirtin.</span><span class="sxs-lookup"><span data-stu-id="9aecc-154">Provide multiple RIDs by specifying this option multiple times.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="9aecc-155">Geri yükleme işlemi sırasında kullanılacak bir NuGet paket kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9aecc-155">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="9aecc-156">Bu ayar *NuGet. config* dosyalarında belirtilen tüm kaynakları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="9aecc-156">This setting overrides all of the sources specified in the *nuget.config* files.</span></span> <span data-ttu-id="9aecc-157">Bu seçenek birden çok kez belirtilerek birden çok kaynak sağlanarak sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9aecc-157">Multiple sources can be provided by specifying this option multiple times.</span></span>

- **`--verbosity <LEVEL>`**

  <span data-ttu-id="9aecc-158">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9aecc-158">Sets the verbosity level of the command.</span></span> <span data-ttu-id="9aecc-159">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="9aecc-159">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="9aecc-160">Varsayılan değer `minimal`.</span><span class="sxs-lookup"><span data-stu-id="9aecc-160">Default value is `minimal`.</span></span>

- **`--interactive`**

  <span data-ttu-id="9aecc-161">Komutun Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir (örneğin, kimlik doğrulamasını tamamlamaya).</span><span class="sxs-lookup"><span data-stu-id="9aecc-161">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span> <span data-ttu-id="9aecc-162">.NET Core 2.1.400 'dan beri.</span><span class="sxs-lookup"><span data-stu-id="9aecc-162">Since .NET Core 2.1.400.</span></span>

## <a name="examples"></a><span data-ttu-id="9aecc-163">Örnekler</span><span class="sxs-lookup"><span data-stu-id="9aecc-163">Examples</span></span>

- <span data-ttu-id="9aecc-164">Geçerli dizindeki proje için bağımlılıkları ve araçları geri yükle:</span><span class="sxs-lookup"><span data-stu-id="9aecc-164">Restore dependencies and tools for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet restore
  ```

- <span data-ttu-id="9aecc-165">Verilen yolda bulunan `app1` projesi için bağımlılıkları ve araçları geri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="9aecc-165">Restore dependencies and tools for the `app1` project found in the   given path:</span></span>

  ```dotnetcli
  dotnet restore ~/projects/app1/app1.csproj
  ```

- <span data-ttu-id="9aecc-166">Kaynak olarak belirtilen dosya yolunu kullanarak geçerli dizindeki proje için bağımlılıkları ve araçları geri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="9aecc-166">Restore the dependencies and tools for the project in the current   directory using the file path provided as the source:</span></span>

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages
  ```

- <span data-ttu-id="9aecc-167">Kaynak olarak girilen iki dosya yolunu kullanarak geçerli dizindeki proje için bağımlılıkları ve araçları geri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="9aecc-167">Restore the dependencies and tools for the project in the current   directory using the two file paths provided as sources:</span></span>

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages
  ```

- <span data-ttu-id="9aecc-168">Geçerli dizindeki proje için bağımlılıkları ve araçları ayrıntılı çıktıyı gösteren geri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="9aecc-168">Restore dependencies and tools for the project in the current directory   showing detailed output:</span></span>

  ```dotnetcli
  dotnet restore --verbosity detailed
  ```
