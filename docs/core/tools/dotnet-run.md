---
title: DotNet Run komutu
description: DotNet Run komutu, uygulamanızı kaynak koddan çalıştırmak için uygun bir seçenek sağlar.
ms.date: 02/19/2020
ms.openlocfilehash: c80f290c75e3bac65ae73fe8edada53db4ce86f8
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634422"
---
# <a name="dotnet-run"></a><span data-ttu-id="0e64b-103">dotnet run</span><span class="sxs-lookup"><span data-stu-id="0e64b-103">dotnet run</span></span>

<span data-ttu-id="0e64b-104">**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 2. x SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="0e64b-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="0e64b-105">Name</span><span class="sxs-lookup"><span data-stu-id="0e64b-105">Name</span></span>

<span data-ttu-id="0e64b-106">`dotnet run` -Açık derleme veya başlatma komutları olmadan kaynak kodu çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="0e64b-106">`dotnet run` - Runs source code without any explicit compile or launch commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="0e64b-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="0e64b-107">Synopsis</span></span>

```dotnetcli
dotnet run [-c|--configuration <CONFIGURATION>] [-f|--framework <FRAMEWORK>]
    [--force] [--interactive] [--launch-profile <NAME>] [--no-build]
    [--no-dependencies] [--no-launch-profile] [--no-restore]
    [-p|--project <PATH>] [-r|--runtime <RUNTIME_IDENTIFIER>]
    [-v|--verbosity <LEVEL>] [[--] [application arguments]]

dotnet run -h|--help
```

## <a name="description"></a><span data-ttu-id="0e64b-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0e64b-108">Description</span></span>

<span data-ttu-id="0e64b-109">`dotnet run`Komut, uygulamanızı kaynak koddan tek bir komutla çalıştırmak için uygun bir seçenek sunar.</span><span class="sxs-lookup"><span data-stu-id="0e64b-109">The `dotnet run` command provides a convenient option to run your application from the source code with one command.</span></span> <span data-ttu-id="0e64b-110">Komut satırından hızlı yinelemeli geliştirme için faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="0e64b-110">It's useful for fast iterative development from the command line.</span></span> <span data-ttu-id="0e64b-111">Komut, [`dotnet build`](dotnet-build.md) kodu oluşturmak için komutuna bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="0e64b-111">The command depends on the [`dotnet build`](dotnet-build.md) command to build the code.</span></span> <span data-ttu-id="0e64b-112">Projenin önce geri yüklenmesi gerektiği gibi, derleme için tüm gereksinimler, için `dotnet run` de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="0e64b-112">Any requirements for the build, such as that the project must be restored first, apply to `dotnet run` as well.</span></span>

<span data-ttu-id="0e64b-113">Çıktı dosyaları varsayılan konuma yazılır, yani `bin/<configuration>/<target>` .</span><span class="sxs-lookup"><span data-stu-id="0e64b-113">Output files are written into the default location, which is `bin/<configuration>/<target>`.</span></span> <span data-ttu-id="0e64b-114">Örneğin `netcoreapp2.1` , bir uygulamanız varsa ve çalıştırırsanız çıkış ' a `dotnet run` yerleştirilir `bin/Debug/netcoreapp2.1` .</span><span class="sxs-lookup"><span data-stu-id="0e64b-114">For example if you have a `netcoreapp2.1` application and you run `dotnet run`, the output is placed in `bin/Debug/netcoreapp2.1`.</span></span> <span data-ttu-id="0e64b-115">Dosyalar gerektiği gibi üzerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="0e64b-115">Files are overwritten as needed.</span></span> <span data-ttu-id="0e64b-116">Geçici dosyalar `obj` dizine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="0e64b-116">Temporary files are placed in the `obj` directory.</span></span>

<span data-ttu-id="0e64b-117">Proje birden çok çerçeve belirtiyorsa, `dotnet run` `-f|--framework <FRAMEWORK>` çerçeveyi belirtmek için seçeneği kullanılmadığı müddetçe sonuçları bir hata halinde yürütüyordur.</span><span class="sxs-lookup"><span data-stu-id="0e64b-117">If the project specifies multiple frameworks, executing `dotnet run` results in an error unless the `-f|--framework <FRAMEWORK>` option is used to specify the framework.</span></span>

<span data-ttu-id="0e64b-118">`dotnet run`Komut, oluşturulan derlemeler değil, proje bağlamında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0e64b-118">The `dotnet run` command is used in the context of projects, not built assemblies.</span></span> <span data-ttu-id="0e64b-119">Bunun yerine Framework 'e bağımlı bir uygulama DLL 'sini çalıştırmaya çalışıyorsanız, bir komut olmadan [DotNet](dotnet.md) kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0e64b-119">If you're trying to run a framework-dependent application DLL instead, you must use [dotnet](dotnet.md) without a command.</span></span> <span data-ttu-id="0e64b-120">Örneğin, çalıştırmak için `myapp.dll` şunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="0e64b-120">For example, to run `myapp.dll`, use:</span></span>

```dotnetcli
dotnet myapp.dll
```

<span data-ttu-id="0e64b-121">Sürücü hakkında daha fazla bilgi için `dotnet` bkz. [.NET komut satırı araçları (CLI)](index.md) konusu.</span><span class="sxs-lookup"><span data-stu-id="0e64b-121">For more information on the `dotnet` driver, see the [.NET Command Line Tools (CLI)](index.md) topic.</span></span>

<span data-ttu-id="0e64b-122">Uygulamayı çalıştırmak için `dotnet run` komut, paylaşılan çalışma zamanının dışındaki uygulamanın tüm bağımlılıklarını NuGet önbelleğinden çözer.</span><span class="sxs-lookup"><span data-stu-id="0e64b-122">To run the application, the `dotnet run` command resolves the dependencies of the application that are outside of the shared runtime from the NuGet cache.</span></span> <span data-ttu-id="0e64b-123">Önbelleğe alınmış bağımlılıkları kullandığından, `dotnet run` Üretim ortamında uygulamaları çalıştırmak için kullanılması önerilmez.</span><span class="sxs-lookup"><span data-stu-id="0e64b-123">Because it uses cached dependencies, it's not recommended to use `dotnet run` to run applications in production.</span></span> <span data-ttu-id="0e64b-124">Bunun yerine, komutunu kullanarak [bir dağıtım oluşturun](../deploying/index.md) [`dotnet publish`](dotnet-publish.md) ve yayımlanan çıktıyı dağıtın.</span><span class="sxs-lookup"><span data-stu-id="0e64b-124">Instead, [create a deployment](../deploying/index.md) using the [`dotnet publish`](dotnet-publish.md) command and deploy the published output.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="0e64b-125">Örtük geri yükleme</span><span class="sxs-lookup"><span data-stu-id="0e64b-125">Implicit restore</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a><span data-ttu-id="0e64b-126">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="0e64b-126">Options</span></span>

- **`--`**

  <span data-ttu-id="0e64b-127">`dotnet run`Çalıştırılmakta olan uygulama için bağımsız değişkenlerin bağımsız değişkenlerini sınırlandırın.</span><span class="sxs-lookup"><span data-stu-id="0e64b-127">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="0e64b-128">Bu sınırlayıcıdan sonraki tüm bağımsız değişkenler uygulama çalıştırmasına geçirilir.</span><span class="sxs-lookup"><span data-stu-id="0e64b-128">All arguments after this delimiter are passed to the application run.</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="0e64b-129">Yapı yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0e64b-129">Defines the build configuration.</span></span> <span data-ttu-id="0e64b-130">Çoğu proje için varsayılandır `Debug` , ancak projenizde derleme yapılandırma ayarlarını geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e64b-130">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="0e64b-131">Belirtilen [Framework 'ü](../../standard/frameworks.md)kullanarak uygulamayı oluşturur ve çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="0e64b-131">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="0e64b-132">Çerçeve proje dosyasında belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="0e64b-132">The framework must be specified in the project file.</span></span>

- **`--force`**

  <span data-ttu-id="0e64b-133">Son geri yükleme başarılı olsa bile tüm bağımlılıkların çözülmesini zorlar.</span><span class="sxs-lookup"><span data-stu-id="0e64b-133">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="0e64b-134">Bu bayrağın belirtilmesi, dosyadaki *project.assets.js* silme ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="0e64b-134">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="0e64b-135">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="0e64b-135">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="0e64b-136">Komutun, Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir (örneğin, kimlik doğrulamasını tamamlamaya yönelik).</span><span class="sxs-lookup"><span data-stu-id="0e64b-136">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="0e64b-137">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0e64b-137">Available since .NET Core 3.0 SDK.</span></span>

- **`--launch-profile <NAME>`**

  <span data-ttu-id="0e64b-138">Uygulamayı başlatırken kullanılacak başlatma profilinin adı (varsa).</span><span class="sxs-lookup"><span data-stu-id="0e64b-138">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="0e64b-139">Başlatma profilleri dosyasında *launchSettings.js* tanımlanmıştır ve genellikle `Development` , ve olarak adlandırılır `Staging` `Production` .</span><span class="sxs-lookup"><span data-stu-id="0e64b-139">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="0e64b-140">Daha fazla bilgi için bkz. [birden çok ortamla çalışma](/aspnet/core/fundamentals/environments).</span><span class="sxs-lookup"><span data-stu-id="0e64b-140">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

- **`--no-build`**

  <span data-ttu-id="0e64b-141">Çalıştırmadan önce projeyi oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="0e64b-141">Doesn't build the project before running.</span></span> <span data-ttu-id="0e64b-142">Bayrak de örtülü olarak ayarlanır `--no-restore` .</span><span class="sxs-lookup"><span data-stu-id="0e64b-142">It also implicit sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="0e64b-143">Projeden projeye (P2P) başvuruları olan bir projeyi geri yüklerken, başvuruları değil kök projeyi geri yükler.</span><span class="sxs-lookup"><span data-stu-id="0e64b-143">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

- **`--no-launch-profile`**

  <span data-ttu-id="0e64b-144">, Uygulamayı yapılandırmak için *üzerindelaunchSettings.js* kullanmaya çalışmayın.</span><span class="sxs-lookup"><span data-stu-id="0e64b-144">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

- **`--no-restore`**

  <span data-ttu-id="0e64b-145">Komutu çalıştırılırken örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="0e64b-145">Doesn't execute an implicit restore when running the command.</span></span>

- **`-p|--project <PATH>`**

  <span data-ttu-id="0e64b-146">Çalıştırılacak proje dosyasının yolunu belirtir (klasör adı veya tam yol).</span><span class="sxs-lookup"><span data-stu-id="0e64b-146">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="0e64b-147">Belirtilmezse, varsayılan olarak geçerli dizini alır.</span><span class="sxs-lookup"><span data-stu-id="0e64b-147">If not specified, it defaults to the current directory.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="0e64b-148">Paketlerinin geri yükleneceği hedef çalışma zamanını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0e64b-148">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="0e64b-149">Çalışma zamanı tanımlayıcıları (RID 'Ler) listesi için bkz. [RID kataloğu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="0e64b-149">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="0e64b-150">`-r` .NET Core 3,0 SDK 'dan bu yana sunulan kısa seçenek.</span><span class="sxs-lookup"><span data-stu-id="0e64b-150">`-r` short option available since .NET Core 3.0 SDK.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="0e64b-151">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0e64b-151">Sets the verbosity level of the command.</span></span> <span data-ttu-id="0e64b-152">İzin verilen değerler,,, `q[uiet]` `m[inimal]` `n[ormal]` `d[etailed]` ve `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="0e64b-152">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="0e64b-153">`m` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="0e64b-153">The default value is `m`.</span></span> <span data-ttu-id="0e64b-154">.NET Core 2,1 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0e64b-154">Available since .NET Core 2.1 SDK.</span></span>

## <a name="examples"></a><span data-ttu-id="0e64b-155">Örnekler</span><span class="sxs-lookup"><span data-stu-id="0e64b-155">Examples</span></span>

- <span data-ttu-id="0e64b-156">Projeyi geçerli dizinde Çalıştır:</span><span class="sxs-lookup"><span data-stu-id="0e64b-156">Run the project in the current directory:</span></span>

  ```dotnetcli
  dotnet run
  ```

- <span data-ttu-id="0e64b-157">Belirtilen projeyi Çalıştır:</span><span class="sxs-lookup"><span data-stu-id="0e64b-157">Run the specified project:</span></span>

  ```dotnetcli
  dotnet run --project ./projects/proj1/proj1.csproj
  ```

- <span data-ttu-id="0e64b-158">Projeyi geçerli dizinde çalıştırın ( `--help` boş seçenek kullanıldığından bu örnekteki bağımsız değişken uygulamaya geçirilir `--` ):</span><span class="sxs-lookup"><span data-stu-id="0e64b-158">Run the project in the current directory (the `--help` argument in this example is passed to the application, since the blank `--` option is used):</span></span>

  ```dotnetcli
  dotnet run --configuration Release -- --help
  ```

- <span data-ttu-id="0e64b-159">Geçerli dizindeki proje için bağımlılıkları ve araçları geri yükleme yalnızca minimum çıktıyı gösterir ve ardından projeyi çalıştırır:</span><span class="sxs-lookup"><span data-stu-id="0e64b-159">Restore dependencies and tools for the project in the current directory only showing minimal output and then run the project:</span></span>

  ```dotnetcli
  dotnet run --verbosity m
  ```
