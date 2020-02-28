---
title: DotNet Run komutu
description: DotNet Run komutu, uygulamanızı kaynak koddan çalıştırmak için uygun bir seçenek sağlar.
ms.date: 02/19/2020
ms.openlocfilehash: e442ed56d676ffd189ef6d394d840cea671c2dc6
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157082"
---
# <a name="dotnet-run"></a><span data-ttu-id="5522f-103">dotnet run</span><span class="sxs-lookup"><span data-stu-id="5522f-103">dotnet run</span></span>

<span data-ttu-id="5522f-104">**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 2. x SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="5522f-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="5522f-105">Adı</span><span class="sxs-lookup"><span data-stu-id="5522f-105">Name</span></span>

<span data-ttu-id="5522f-106">`dotnet run`-herhangi bir açık derleme veya başlatma komutu olmadan kaynak kodu çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="5522f-106">`dotnet run` - Runs source code without any explicit compile or launch commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5522f-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="5522f-107">Synopsis</span></span>

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [--force] [--interactive] [--launch-profile]
    [--no-build] [--no-dependencies] [--no-launch-profile] [--no-restore] [-p|--project]
    [-r|--runtime] [-v|--verbosity] [[--] [application arguments]]
dotnet run [-h|--help]
```

## <a name="description"></a><span data-ttu-id="5522f-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5522f-108">Description</span></span>

<span data-ttu-id="5522f-109">`dotnet run` komutu, uygulamanızı kaynak koddan tek bir komutla çalıştırmak için uygun bir seçenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="5522f-109">The `dotnet run` command provides a convenient option to run your application from the source code with one command.</span></span> <span data-ttu-id="5522f-110">Komut satırından hızlı yinelemeli geliştirme için faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="5522f-110">It's useful for fast iterative development from the command line.</span></span> <span data-ttu-id="5522f-111">Komut, kodu derlemek için [`dotnet build`](dotnet-build.md) komutuna bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="5522f-111">The command depends on the [`dotnet build`](dotnet-build.md) command to build the code.</span></span> <span data-ttu-id="5522f-112">Projenin önce geri yüklenmesi gerektiği gibi, derleme için tüm gereksinimler, `dotnet run` için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5522f-112">Any requirements for the build, such as that the project must be restored first, apply to `dotnet run` as well.</span></span>

<span data-ttu-id="5522f-113">Çıktı dosyaları varsayılan konuma yazılır, bu `bin/<configuration>/<target>`.</span><span class="sxs-lookup"><span data-stu-id="5522f-113">Output files are written into the default location, which is `bin/<configuration>/<target>`.</span></span> <span data-ttu-id="5522f-114">Örneğin, bir `netcoreapp2.1` uygulamanız varsa ve `dotnet run`çalıştırırsanız, çıktı `bin/Debug/netcoreapp2.1`yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="5522f-114">For example if you have a `netcoreapp2.1` application and you run `dotnet run`, the output is placed in `bin/Debug/netcoreapp2.1`.</span></span> <span data-ttu-id="5522f-115">Dosyalar gerektiği gibi üzerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="5522f-115">Files are overwritten as needed.</span></span> <span data-ttu-id="5522f-116">Geçici dosyalar `obj` dizinine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="5522f-116">Temporary files are placed in the `obj` directory.</span></span>

<span data-ttu-id="5522f-117">Proje birden çok çerçeve belirtiyorsa, Framework 'ü belirtmek için `-f|--framework <FRAMEWORK>` seçeneği kullanılmadığı müddetçe `dotnet run` yürütülerek hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="5522f-117">If the project specifies multiple frameworks, executing `dotnet run` results in an error unless the `-f|--framework <FRAMEWORK>` option is used to specify the framework.</span></span>

<span data-ttu-id="5522f-118">`dotnet run` komutu, oluşturulan derlemeler değil, proje bağlamında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5522f-118">The `dotnet run` command is used in the context of projects, not built assemblies.</span></span> <span data-ttu-id="5522f-119">Bunun yerine Framework 'e bağımlı bir uygulama DLL 'sini çalıştırmaya çalışıyorsanız, bir komut olmadan [DotNet](dotnet.md) kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5522f-119">If you're trying to run a framework-dependent application DLL instead, you must use [dotnet](dotnet.md) without a command.</span></span> <span data-ttu-id="5522f-120">Örneğin, `myapp.dll`çalıştırmak için şunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="5522f-120">For example, to run `myapp.dll`, use:</span></span>

```dotnetcli
dotnet myapp.dll
```

<span data-ttu-id="5522f-121">`dotnet` sürücüsü hakkında daha fazla bilgi için bkz. [.NET Core komut satırı araçları (CLI)](index.md) konusu.</span><span class="sxs-lookup"><span data-stu-id="5522f-121">For more information on the `dotnet` driver, see the [.NET Core Command Line Tools (CLI)](index.md) topic.</span></span>

<span data-ttu-id="5522f-122">Uygulamayı çalıştırmak için `dotnet run` komutu, paylaşılan çalışma zamanının dışındaki uygulamanın tüm bağımlılıklarını NuGet önbelleğinden çözer.</span><span class="sxs-lookup"><span data-stu-id="5522f-122">To run the application, the `dotnet run` command resolves the dependencies of the application that are outside of the shared runtime from the NuGet cache.</span></span> <span data-ttu-id="5522f-123">Önbelleğe alınmış bağımlılıkları kullandığından, üretimde uygulamaları çalıştırmak için `dotnet run` kullanılması önerilmez.</span><span class="sxs-lookup"><span data-stu-id="5522f-123">Because it uses cached dependencies, it's not recommended to use `dotnet run` to run applications in production.</span></span> <span data-ttu-id="5522f-124">Bunun yerine, [`dotnet publish`](dotnet-publish.md) komutunu kullanarak [bir dağıtım oluşturun](../deploying/index.md) ve yayımlanan çıktıyı dağıtın.</span><span class="sxs-lookup"><span data-stu-id="5522f-124">Instead, [create a deployment](../deploying/index.md) using the [`dotnet publish`](dotnet-publish.md) command and deploy the published output.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a><span data-ttu-id="5522f-125">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="5522f-125">Options</span></span>

- **`--`**

  <span data-ttu-id="5522f-126">Çalıştırılmakta olan uygulamanın bağımsız değişkenlerinden `dotnet run` için bağımsız değişkenleri ayırır.</span><span class="sxs-lookup"><span data-stu-id="5522f-126">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="5522f-127">Bu sınırlayıcıdan sonraki tüm bağımsız değişkenler uygulama çalıştırmasına geçirilir.</span><span class="sxs-lookup"><span data-stu-id="5522f-127">All arguments after this delimiter are passed to the application run.</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="5522f-128">Yapı yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5522f-128">Defines the build configuration.</span></span> <span data-ttu-id="5522f-129">Çoğu proje için varsayılan değer `Debug`, ancak projenizde derleme yapılandırma ayarlarını geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5522f-129">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="5522f-130">Belirtilen [Framework 'ü](../../standard/frameworks.md)kullanarak uygulamayı oluşturur ve çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="5522f-130">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="5522f-131">Çerçeve proje dosyasında belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="5522f-131">The framework must be specified in the project file.</span></span>

- **`--force`**

  <span data-ttu-id="5522f-132">Son geri yükleme başarılı olsa bile tüm bağımlılıkların çözülmesini zorlar.</span><span class="sxs-lookup"><span data-stu-id="5522f-132">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="5522f-133">Bu bayrağın belirtilmesi, *Project. varlıklar. JSON* dosyasını silme ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="5522f-133">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="5522f-134">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="5522f-134">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="5522f-135">Komutun, Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir (örneğin, kimlik doğrulamasını tamamlamaya yönelik).</span><span class="sxs-lookup"><span data-stu-id="5522f-135">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="5522f-136">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5522f-136">Available since .NET Core 3.0 SDK.</span></span>

- **`--launch-profile <NAME>`**

  <span data-ttu-id="5522f-137">Uygulamayı başlatırken kullanılacak başlatma profilinin adı (varsa).</span><span class="sxs-lookup"><span data-stu-id="5522f-137">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="5522f-138">Başlatma profilleri, *Launchsettings. JSON* dosyasında tanımlanır ve genellikle `Development`, `Staging`ve `Production`olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="5522f-138">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="5522f-139">Daha fazla bilgi için bkz. [birden çok ortamla çalışma](/aspnet/core/fundamentals/environments).</span><span class="sxs-lookup"><span data-stu-id="5522f-139">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

- **`--no-build`**

  <span data-ttu-id="5522f-140">Çalıştırmadan önce projeyi oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="5522f-140">Doesn't build the project before running.</span></span> <span data-ttu-id="5522f-141">Ayrıca `--no-restore` bayrağını örtülü olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5522f-141">It also implicit sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="5522f-142">Projeden projeye (P2P) başvuruları olan bir projeyi geri yüklerken, başvuruları değil kök projeyi geri yükler.</span><span class="sxs-lookup"><span data-stu-id="5522f-142">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

- **`--no-launch-profile`**

  <span data-ttu-id="5522f-143">Uygulamayı yapılandırmak için *Launchsettings. JSON* kullanmaya çalışmayın.</span><span class="sxs-lookup"><span data-stu-id="5522f-143">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

- **`--no-restore`**

  <span data-ttu-id="5522f-144">Komutu çalıştırılırken örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="5522f-144">Doesn't execute an implicit restore when running the command.</span></span>

- **`-p|--project <PATH>`**

  <span data-ttu-id="5522f-145">Çalıştırılacak proje dosyasının yolunu belirtir (klasör adı veya tam yol).</span><span class="sxs-lookup"><span data-stu-id="5522f-145">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="5522f-146">Belirtilmezse, varsayılan olarak geçerli dizini alır.</span><span class="sxs-lookup"><span data-stu-id="5522f-146">If not specified, it defaults to the current directory.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="5522f-147">Paketlerinin geri yükleneceği hedef çalışma zamanını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5522f-147">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="5522f-148">Çalışma zamanı tanımlayıcıları (RID 'Ler) listesi için bkz. [RID kataloğu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="5522f-148">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="5522f-149">`-r` Short seçeneği .NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5522f-149">`-r` short option available since .NET Core 3.0 SDK.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="5522f-150">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5522f-150">Sets the verbosity level of the command.</span></span> <span data-ttu-id="5522f-151">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="5522f-151">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="5522f-152">Varsayılan değer: `m`.</span><span class="sxs-lookup"><span data-stu-id="5522f-152">The default value is `m`.</span></span> <span data-ttu-id="5522f-153">.NET Core 2,1 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5522f-153">Available since .NET Core 2.1 SDK.</span></span>

## <a name="examples"></a><span data-ttu-id="5522f-154">Örnekler</span><span class="sxs-lookup"><span data-stu-id="5522f-154">Examples</span></span>

- <span data-ttu-id="5522f-155">Projeyi geçerli dizinde Çalıştır:</span><span class="sxs-lookup"><span data-stu-id="5522f-155">Run the project in the current directory:</span></span>

  ```dotnetcli
  dotnet run
  ```

- <span data-ttu-id="5522f-156">Belirtilen projeyi Çalıştır:</span><span class="sxs-lookup"><span data-stu-id="5522f-156">Run the specified project:</span></span>

  ```dotnetcli
  dotnet run --project ./projects/proj1/proj1.csproj
  ```

- <span data-ttu-id="5522f-157">Projeyi geçerli dizinde çalıştırın (boş `--` seçeneği kullanıldığından bu örnekteki `--help` bağımsız değişkeni uygulamaya geçirilir):</span><span class="sxs-lookup"><span data-stu-id="5522f-157">Run the project in the current directory (the `--help` argument in this example is passed to the application, since the blank `--` option is used):</span></span>

  ```dotnetcli
  dotnet run --configuration Release -- --help
  ```

- <span data-ttu-id="5522f-158">Geçerli dizindeki proje için bağımlılıkları ve araçları geri yükleme yalnızca minimum çıktıyı gösterir ve ardından projeyi (.NET Core SDK 2,0 ve sonraki sürümleri) çalıştırır:</span><span class="sxs-lookup"><span data-stu-id="5522f-158">Restore dependencies and tools for the project in the current directory only showing minimal output and then run the project: (.NET Core SDK 2.0 and later versions):</span></span>

  ```dotnetcli
  dotnet run --verbosity m
  ```
