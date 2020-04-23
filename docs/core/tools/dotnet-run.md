---
title: dotnet çalıştır komutu
description: Dotnet çalıştır komutu, uygulamanızı kaynak kodundan çalıştırmak için kullanışlı bir seçenek sağlar.
ms.date: 02/19/2020
ms.openlocfilehash: 77282fd8615ef01b7867c1bf0f741c834b6ddb30
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102780"
---
# <a name="dotnet-run"></a><span data-ttu-id="51576-103">dotnet run</span><span class="sxs-lookup"><span data-stu-id="51576-103">dotnet run</span></span>

<span data-ttu-id="51576-104">**Bu makale şu şekilde dir:** ✔️ .NET Core 2.x SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="51576-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="51576-105">Adı</span><span class="sxs-lookup"><span data-stu-id="51576-105">Name</span></span>

<span data-ttu-id="51576-106">`dotnet run`- Kaynak kodunu açık bir derleme veya başlatma komutları olmadan çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="51576-106">`dotnet run` - Runs source code without any explicit compile or launch commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="51576-107">Özet</span><span class="sxs-lookup"><span data-stu-id="51576-107">Synopsis</span></span>

```dotnetcli
dotnet run [-c|--configuration <CONFIGURATION>] [-f|--framework <FRAMEWORK>]
    [--force] [--interactive] [--launch-profile <NAME>] [--no-build]
    [--no-dependencies] [--no-launch-profile] [--no-restore]
    [-p|--project <PATH>] [-r|--runtime <RUNTIME_IDENTIFIER>]
    [-v|--verbosity <LEVEL>] [[--] [application arguments]]

dotnet run -h|--help
```

## <a name="description"></a><span data-ttu-id="51576-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="51576-108">Description</span></span>

<span data-ttu-id="51576-109">Komut, `dotnet run` uygulamanızı kaynak koddan tek bir komutla çalıştırmak için kullanışlı bir seçenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="51576-109">The `dotnet run` command provides a convenient option to run your application from the source code with one command.</span></span> <span data-ttu-id="51576-110">Komut satırından hızlı yinelemeli geliştirme için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="51576-110">It's useful for fast iterative development from the command line.</span></span> <span data-ttu-id="51576-111">Komut, kodu oluşturmak [`dotnet build`](dotnet-build.md) için komuta bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="51576-111">The command depends on the [`dotnet build`](dotnet-build.md) command to build the code.</span></span> <span data-ttu-id="51576-112">Yapı için, projenin önce geri yükedilmesi gibi tüm gereksinimler `dotnet run` de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="51576-112">Any requirements for the build, such as that the project must be restored first, apply to `dotnet run` as well.</span></span>

<span data-ttu-id="51576-113">Çıktı dosyaları varsayılan konuma yazılır, `bin/<configuration>/<target>`yani.</span><span class="sxs-lookup"><span data-stu-id="51576-113">Output files are written into the default location, which is `bin/<configuration>/<target>`.</span></span> <span data-ttu-id="51576-114">Örneğin bir `netcoreapp2.1` uygulamanız varsa ve `dotnet run`çalıştırın, çıktı `bin/Debug/netcoreapp2.1`.</span><span class="sxs-lookup"><span data-stu-id="51576-114">For example if you have a `netcoreapp2.1` application and you run `dotnet run`, the output is placed in `bin/Debug/netcoreapp2.1`.</span></span> <span data-ttu-id="51576-115">Dosyalar gerektiği gibi üzerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="51576-115">Files are overwritten as needed.</span></span> <span data-ttu-id="51576-116">Geçici dosyalar dizine `obj` yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="51576-116">Temporary files are placed in the `obj` directory.</span></span>

<span data-ttu-id="51576-117">Proje birden çok çerçeve belirtirse, `dotnet run` çerçeveyi belirtmek `-f|--framework <FRAMEWORK>` için seçenek kullanılmadığı sürece bir hatayla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="51576-117">If the project specifies multiple frameworks, executing `dotnet run` results in an error unless the `-f|--framework <FRAMEWORK>` option is used to specify the framework.</span></span>

<span data-ttu-id="51576-118">Komut, `dotnet run` derlemeler değil, projeler bağlamında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="51576-118">The `dotnet run` command is used in the context of projects, not built assemblies.</span></span> <span data-ttu-id="51576-119">Bunun yerine çerçeveye bağımlı bir uygulama olan DLL'yi çalıştırmaya çalışıyorsanız, komut olmadan [dotnet](dotnet.md) kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="51576-119">If you're trying to run a framework-dependent application DLL instead, you must use [dotnet](dotnet.md) without a command.</span></span> <span data-ttu-id="51576-120">Örneğin, çalıştırmak `myapp.dll`için, kullanmak:</span><span class="sxs-lookup"><span data-stu-id="51576-120">For example, to run `myapp.dll`, use:</span></span>

```dotnetcli
dotnet myapp.dll
```

<span data-ttu-id="51576-121">Sürücü hakkında daha `dotnet` fazla bilgi için [.NET Core Komut Satırı Araçları (CLI)](index.md) konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="51576-121">For more information on the `dotnet` driver, see the [.NET Core Command Line Tools (CLI)](index.md) topic.</span></span>

<span data-ttu-id="51576-122">Uygulamayı çalıştırmak için `dotnet run` komut, NuGet önbelleğinden paylaşılan çalışma süresinin dışında olan uygulamanın bağımlılıklarını giderir.</span><span class="sxs-lookup"><span data-stu-id="51576-122">To run the application, the `dotnet run` command resolves the dependencies of the application that are outside of the shared runtime from the NuGet cache.</span></span> <span data-ttu-id="51576-123">Önbelleğe alınmış bağımlılıklar kullandığından, üretimdeki `dotnet run` uygulamaları çalıştırmak için kullanılması önerilmez.</span><span class="sxs-lookup"><span data-stu-id="51576-123">Because it uses cached dependencies, it's not recommended to use `dotnet run` to run applications in production.</span></span> <span data-ttu-id="51576-124">Bunun [create a deployment](../deploying/index.md) yerine, komutu [`dotnet publish`](dotnet-publish.md) kullanarak bir dağıtım oluşturun ve yayımlanmış çıktıyı dağıtın.</span><span class="sxs-lookup"><span data-stu-id="51576-124">Instead, [create a deployment](../deploying/index.md) using the [`dotnet publish`](dotnet-publish.md) command and deploy the published output.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="51576-125">Örtük geri yükleme</span><span class="sxs-lookup"><span data-stu-id="51576-125">Implicit restore</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a><span data-ttu-id="51576-126">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="51576-126">Options</span></span>

- **`--`**

  <span data-ttu-id="51576-127">Çalıştırılmakta `dotnet run` olan uygulama için bağımsız değişkenleri sınırlandırın.</span><span class="sxs-lookup"><span data-stu-id="51576-127">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="51576-128">Bu delimiter sonra tüm bağımsız değişkenler uygulama çalışmasına geçirilir.</span><span class="sxs-lookup"><span data-stu-id="51576-128">All arguments after this delimiter are passed to the application run.</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="51576-129">Yapı yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="51576-129">Defines the build configuration.</span></span> <span data-ttu-id="51576-130">Çoğu proje için `Debug`varsayılan değer, ancak projenizdeki yapı yapılandırma ayarlarını geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51576-130">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="51576-131">Belirtilen [çerçeveyi](../../standard/frameworks.md)kullanarak uygulamayı oluşturur ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="51576-131">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="51576-132">Çerçeve proje dosyasında belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="51576-132">The framework must be specified in the project file.</span></span>

- **`--force`**

  <span data-ttu-id="51576-133">Son geri yükleme başarılı olsa bile tüm bağımlılıkları çözüme kavuşturmaya zorlar.</span><span class="sxs-lookup"><span data-stu-id="51576-133">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="51576-134">Bu bayrağı *belirtmek, project.assets.json* dosyasını silmekle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="51576-134">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="51576-135">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="51576-135">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="51576-136">Komutun durmasına ve kullanıcı girişinin veya eylemini beklemesine (örneğin, kimlik doğrulamasını tamamlamak için) izin verir.</span><span class="sxs-lookup"><span data-stu-id="51576-136">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="51576-137">.NET Core 3.0 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="51576-137">Available since .NET Core 3.0 SDK.</span></span>

- **`--launch-profile <NAME>`**

  <span data-ttu-id="51576-138">Uygulamayı başlatırken kullanılacak başlatma profilinin adı (varsa).</span><span class="sxs-lookup"><span data-stu-id="51576-138">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="51576-139">Başlatma profilleri *launchSettings.json* dosyasında tanımlanır ve genellikle `Development` `Staging`, `Production`, ve .</span><span class="sxs-lookup"><span data-stu-id="51576-139">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="51576-140">Daha fazla bilgi için bkz: [Birden çok ortamla çalışma.](/aspnet/core/fundamentals/environments)</span><span class="sxs-lookup"><span data-stu-id="51576-140">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

- **`--no-build`**

  <span data-ttu-id="51576-141">Çalıştırmadan önce projeyi oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="51576-141">Doesn't build the project before running.</span></span> <span data-ttu-id="51576-142">Ayrıca örtük `--no-restore` bayrağı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="51576-142">It also implicit sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="51576-143">Projeden projeye (P2P) başvurularla projeyi geri yüklediğinizde, başvuruları değil, kök projeyi geri yükler.</span><span class="sxs-lookup"><span data-stu-id="51576-143">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

- **`--no-launch-profile`**

  <span data-ttu-id="51576-144">Uygulamayı yapılandırmak için *launchSettings.json* kullanmaya çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="51576-144">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

- **`--no-restore`**

  <span data-ttu-id="51576-145">Komutu çalıştırırken örtük bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="51576-145">Doesn't execute an implicit restore when running the command.</span></span>

- **`-p|--project <PATH>`**

  <span data-ttu-id="51576-146">Proje dosyasının çalışma yolunu (klasör adı veya tam yol) belirtir.</span><span class="sxs-lookup"><span data-stu-id="51576-146">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="51576-147">Belirtilmemişse, varsayılan olarak geçerli dizine göre olur.</span><span class="sxs-lookup"><span data-stu-id="51576-147">If not specified, it defaults to the current directory.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="51576-148">Paketleri geri yüklemek için hedef çalışma süresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="51576-148">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="51576-149">Runtime Tanımlayıcıları (RID'ler) listesi için RID [kataloğuna](../rid-catalog.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="51576-149">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="51576-150">`-r`.NET Core 3.0 SDK'dan beri kısa seçenek mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="51576-150">`-r` short option available since .NET Core 3.0 SDK.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="51576-151">Komutun ayrıntılı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="51576-151">Sets the verbosity level of the command.</span></span> <span data-ttu-id="51576-152">İzin verilen `q[uiet]` `m[inimal]`değerler `n[ormal]` `d[etailed]`, `diag[nostic]`, , , ve .</span><span class="sxs-lookup"><span data-stu-id="51576-152">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="51576-153">Varsayılan değer: `m`.</span><span class="sxs-lookup"><span data-stu-id="51576-153">The default value is `m`.</span></span> <span data-ttu-id="51576-154">.NET Core 2.1 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="51576-154">Available since .NET Core 2.1 SDK.</span></span>

## <a name="examples"></a><span data-ttu-id="51576-155">Örnekler</span><span class="sxs-lookup"><span data-stu-id="51576-155">Examples</span></span>

- <span data-ttu-id="51576-156">Projeyi geçerli dizinde çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="51576-156">Run the project in the current directory:</span></span>

  ```dotnetcli
  dotnet run
  ```

- <span data-ttu-id="51576-157">Belirtilen projeyi çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="51576-157">Run the specified project:</span></span>

  ```dotnetcli
  dotnet run --project ./projects/proj1/proj1.csproj
  ```

- <span data-ttu-id="51576-158">Projeyi geçerli dizinde çalıştırın `--help` (boş `--` seçenek kullanıldığından, bu örnekteki bağımsız değişken uygulamaya geçirilir):</span><span class="sxs-lookup"><span data-stu-id="51576-158">Run the project in the current directory (the `--help` argument in this example is passed to the application, since the blank `--` option is used):</span></span>

  ```dotnetcli
  dotnet run --configuration Release -- --help
  ```

- <span data-ttu-id="51576-159">Geçerli dizinde proje için bağımlılıkları ve araçları yalnızca en az çıktıyı gösteren geri yüklenir ve projeyi çalıştırın: (.NET Core SDK 2.0 ve sonraki sürümler):</span><span class="sxs-lookup"><span data-stu-id="51576-159">Restore dependencies and tools for the project in the current directory only showing minimal output and then run the project: (.NET Core SDK 2.0 and later versions):</span></span>

  ```dotnetcli
  dotnet run --verbosity m
  ```
