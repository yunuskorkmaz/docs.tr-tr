---
title: DotNet Run komutu
description: DotNet Run komutu, uygulamanızı kaynak koddan çalıştırmak için uygun bir seçenek sağlar.
ms.date: 10/31/2019
ms.openlocfilehash: 5920f0d1f04204b286fdf6f51f5fd13644846390
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734108"
---
# <a name="dotnet-run"></a><span data-ttu-id="acebc-103">dotnet run</span><span class="sxs-lookup"><span data-stu-id="acebc-103">dotnet run</span></span>

<span data-ttu-id="acebc-104">**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 1. x SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="acebc-104">**This article applies to:** ✔️ .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="acebc-105">Ad</span><span class="sxs-lookup"><span data-stu-id="acebc-105">Name</span></span>

<span data-ttu-id="acebc-106">`dotnet run`-herhangi bir açık derleme veya başlatma komutu olmadan kaynak kodu çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="acebc-106">`dotnet run` - Runs source code without any explicit compile or launch commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="acebc-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="acebc-107">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="acebc-108">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="acebc-108">.NET Core 3.0</span></span>](#tab/netcore30)

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [--force] [--interactive] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [-r|--runtime] [-v|--verbosity] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="acebc-109">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="acebc-109">.NET Core 2.1</span></span>](#tab/netcore21)

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [-v|--verbosity] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="acebc-110">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="acebc-110">.NET Core 2.0</span></span>](#tab/netcore20)

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="acebc-111">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="acebc-111">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [-p|--project] [[--] [application arguments]]
dotnet run [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="acebc-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="acebc-112">Description</span></span>

<span data-ttu-id="acebc-113">`dotnet run` komutu, uygulamanızı kaynak koddan tek bir komutla çalıştırmak için uygun bir seçenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="acebc-113">The `dotnet run` command provides a convenient option to run your application from the source code with one command.</span></span> <span data-ttu-id="acebc-114">Komut satırından hızlı yinelemeli geliştirme için faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="acebc-114">It's useful for fast iterative development from the command line.</span></span> <span data-ttu-id="acebc-115">Komut, kodu derlemek için [`dotnet build`](dotnet-build.md) komutuna bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="acebc-115">The command depends on the [`dotnet build`](dotnet-build.md) command to build the code.</span></span> <span data-ttu-id="acebc-116">Projenin önce geri yüklenmesi gerektiği gibi, derleme için tüm gereksinimler, `dotnet run` için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="acebc-116">Any requirements for the build, such as that the project must be restored first, apply to `dotnet run` as well.</span></span>

<span data-ttu-id="acebc-117">Çıktı dosyaları varsayılan konuma yazılır, bu `bin/<configuration>/<target>`.</span><span class="sxs-lookup"><span data-stu-id="acebc-117">Output files are written into the default location, which is `bin/<configuration>/<target>`.</span></span> <span data-ttu-id="acebc-118">Örneğin, bir `netcoreapp2.1` uygulamanız varsa ve `dotnet run`çalıştırırsanız, çıktı `bin/Debug/netcoreapp2.1`yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="acebc-118">For example if you have a `netcoreapp2.1` application and you run `dotnet run`, the output is placed in `bin/Debug/netcoreapp2.1`.</span></span> <span data-ttu-id="acebc-119">Dosyalar gerektiği gibi üzerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="acebc-119">Files are overwritten as needed.</span></span> <span data-ttu-id="acebc-120">Geçici dosyalar `obj` dizinine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="acebc-120">Temporary files are placed in the `obj` directory.</span></span>

<span data-ttu-id="acebc-121">Proje birden çok çerçeve belirtiyorsa, Framework 'ü belirtmek için `-f|--framework <FRAMEWORK>` seçeneği kullanılmadığı müddetçe `dotnet run` yürütülerek hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="acebc-121">If the project specifies multiple frameworks, executing `dotnet run` results in an error unless the `-f|--framework <FRAMEWORK>` option is used to specify the framework.</span></span>

<span data-ttu-id="acebc-122">`dotnet run` komutu, oluşturulan derlemeler değil, proje bağlamında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="acebc-122">The `dotnet run` command is used in the context of projects, not built assemblies.</span></span> <span data-ttu-id="acebc-123">Bunun yerine Framework 'e bağımlı bir uygulama DLL 'sini çalıştırmaya çalışıyorsanız, bir komut olmadan [DotNet](dotnet.md) kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="acebc-123">If you're trying to run a framework-dependent application DLL instead, you must use [dotnet](dotnet.md) without a command.</span></span> <span data-ttu-id="acebc-124">Örneğin, `myapp.dll`çalıştırmak için şunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="acebc-124">For example, to run `myapp.dll`, use:</span></span>

```dotnetcli
dotnet myapp.dll
```

<span data-ttu-id="acebc-125">`dotnet` sürücüsü hakkında daha fazla bilgi için bkz. [.NET Core komut satırı araçları (CLI)](index.md) konusu.</span><span class="sxs-lookup"><span data-stu-id="acebc-125">For more information on the `dotnet` driver, see the [.NET Core Command Line Tools (CLI)](index.md) topic.</span></span>

<span data-ttu-id="acebc-126">Uygulamayı çalıştırmak için `dotnet run` komutu, paylaşılan çalışma zamanının dışındaki uygulamanın tüm bağımlılıklarını NuGet önbelleğinden çözer.</span><span class="sxs-lookup"><span data-stu-id="acebc-126">To run the application, the `dotnet run` command resolves the dependencies of the application that are outside of the shared runtime from the NuGet cache.</span></span> <span data-ttu-id="acebc-127">Önbelleğe alınmış bağımlılıkları kullandığından, üretimde uygulamaları çalıştırmak için `dotnet run` kullanılması önerilmez.</span><span class="sxs-lookup"><span data-stu-id="acebc-127">Because it uses cached dependencies, it's not recommended to use `dotnet run` to run applications in production.</span></span> <span data-ttu-id="acebc-128">Bunun yerine, [`dotnet publish`](dotnet-publish.md) komutunu kullanarak [bir dağıtım oluşturun](../deploying/index.md) ve yayımlanan çıktıyı dağıtın.</span><span class="sxs-lookup"><span data-stu-id="acebc-128">Instead, [create a deployment](../deploying/index.md) using the [`dotnet publish`](dotnet-publish.md) command and deploy the published output.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a><span data-ttu-id="acebc-129">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="acebc-129">Options</span></span>

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="acebc-130">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="acebc-130">.NET Core 3.0</span></span>](#tab/netcore30)

`--`

<span data-ttu-id="acebc-131">Çalıştırılmakta olan uygulamanın bağımsız değişkenlerinden `dotnet run` için bağımsız değişkenleri ayırır.</span><span class="sxs-lookup"><span data-stu-id="acebc-131">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="acebc-132">Bu sınırlayıcıdan sonraki tüm bağımsız değişkenler uygulama çalıştırmasına geçirilir.</span><span class="sxs-lookup"><span data-stu-id="acebc-132">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="acebc-133">Yapı yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="acebc-133">Defines the build configuration.</span></span> <span data-ttu-id="acebc-134">Çoğu projenin varsayılan değeri `Debug`.</span><span class="sxs-lookup"><span data-stu-id="acebc-134">The default value for most projects is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="acebc-135">Belirtilen [Framework 'ü](../../standard/frameworks.md)kullanarak uygulamayı oluşturur ve çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="acebc-135">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="acebc-136">Çerçeve proje dosyasında belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="acebc-136">The framework must be specified in the project file.</span></span>

`--force`

<span data-ttu-id="acebc-137">Son geri yükleme başarılı olsa bile tüm bağımlılıkların çözülmesini zorlar.</span><span class="sxs-lookup"><span data-stu-id="acebc-137">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="acebc-138">Bu bayrağın belirtilmesi, *Project. varlıklar. JSON* dosyasını silme ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="acebc-138">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="acebc-139">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="acebc-139">Prints out a short help for the command.</span></span>

`--interactive`

<span data-ttu-id="acebc-140">Komutun, Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir (örneğin, kimlik doğrulamasını tamamlamaya yönelik).</span><span class="sxs-lookup"><span data-stu-id="acebc-140">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span>

`--launch-profile <NAME>`

<span data-ttu-id="acebc-141">Uygulamayı başlatırken kullanılacak başlatma profilinin adı (varsa).</span><span class="sxs-lookup"><span data-stu-id="acebc-141">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="acebc-142">Başlatma profilleri, *Launchsettings. JSON* dosyasında tanımlanır ve genellikle `Development`, `Staging`ve `Production`olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="acebc-142">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="acebc-143">Daha fazla bilgi için bkz. [birden çok ortamla çalışma](/aspnet/core/fundamentals/environments).</span><span class="sxs-lookup"><span data-stu-id="acebc-143">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

`--no-build`

<span data-ttu-id="acebc-144">Çalıştırmadan önce projeyi oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="acebc-144">Doesn't build the project before running.</span></span> <span data-ttu-id="acebc-145">Ayrıca `--no-restore` bayrağını örtülü olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="acebc-145">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="acebc-146">Projeden projeye (P2P) başvuruları olan bir projeyi geri yüklerken, başvuruları değil kök projeyi geri yükler.</span><span class="sxs-lookup"><span data-stu-id="acebc-146">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--no-launch-profile`

<span data-ttu-id="acebc-147">Uygulamayı yapılandırmak için *Launchsettings. JSON* kullanmaya çalışmayın.</span><span class="sxs-lookup"><span data-stu-id="acebc-147">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

`--no-restore`

<span data-ttu-id="acebc-148">Komutu çalıştırılırken örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="acebc-148">Doesn't execute an implicit restore when running the command.</span></span>

`-p|--project <PATH>`

<span data-ttu-id="acebc-149">Çalıştırılacak proje dosyasının yolunu belirtir (klasör adı veya tam yol).</span><span class="sxs-lookup"><span data-stu-id="acebc-149">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="acebc-150">Belirtilmezse, varsayılan olarak geçerli dizini alır.</span><span class="sxs-lookup"><span data-stu-id="acebc-150">If not specified, it defaults to the current directory.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="acebc-151">Paketlerinin geri yükleneceği hedef çalışma zamanını belirtir.</span><span class="sxs-lookup"><span data-stu-id="acebc-151">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="acebc-152">Çalışma zamanı tanımlayıcıları (RID 'Ler) listesi için bkz. [RID kataloğu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="acebc-152">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="acebc-153">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="acebc-153">Sets the verbosity level of the command.</span></span> <span data-ttu-id="acebc-154">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="acebc-154">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="acebc-155">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="acebc-155">.NET Core 2.1</span></span>](#tab/netcore21)

`--`

<span data-ttu-id="acebc-156">Çalıştırılmakta olan uygulamanın bağımsız değişkenlerinden `dotnet run` için bağımsız değişkenleri ayırır.</span><span class="sxs-lookup"><span data-stu-id="acebc-156">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="acebc-157">Bu sınırlayıcıdan sonraki tüm bağımsız değişkenler uygulama çalıştırmasına geçirilir.</span><span class="sxs-lookup"><span data-stu-id="acebc-157">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="acebc-158">Yapı yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="acebc-158">Defines the build configuration.</span></span> <span data-ttu-id="acebc-159">Çoğu projenin varsayılan değeri `Debug`.</span><span class="sxs-lookup"><span data-stu-id="acebc-159">The default value for most projects is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="acebc-160">Belirtilen [Framework 'ü](../../standard/frameworks.md)kullanarak uygulamayı oluşturur ve çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="acebc-160">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="acebc-161">Çerçeve proje dosyasında belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="acebc-161">The framework must be specified in the project file.</span></span>

`--force`

<span data-ttu-id="acebc-162">Son geri yükleme başarılı olsa bile tüm bağımlılıkların çözülmesini zorlar.</span><span class="sxs-lookup"><span data-stu-id="acebc-162">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="acebc-163">Bu bayrağın belirtilmesi, *Project. varlıklar. JSON* dosyasını silme ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="acebc-163">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="acebc-164">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="acebc-164">Prints out a short help for the command.</span></span>

`--launch-profile <NAME>`

<span data-ttu-id="acebc-165">Uygulamayı başlatırken kullanılacak başlatma profilinin adı (varsa).</span><span class="sxs-lookup"><span data-stu-id="acebc-165">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="acebc-166">Başlatma profilleri, *Launchsettings. JSON* dosyasında tanımlanır ve genellikle `Development`, `Staging`ve `Production`olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="acebc-166">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="acebc-167">Daha fazla bilgi için bkz. [birden çok ortamla çalışma](/aspnet/core/fundamentals/environments).</span><span class="sxs-lookup"><span data-stu-id="acebc-167">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

`--no-build`

<span data-ttu-id="acebc-168">Çalıştırmadan önce projeyi oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="acebc-168">Doesn't build the project before running.</span></span> <span data-ttu-id="acebc-169">Ayrıca `--no-restore` bayrağını örtülü olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="acebc-169">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="acebc-170">Projeden projeye (P2P) başvuruları olan bir projeyi geri yüklerken, başvuruları değil kök projeyi geri yükler.</span><span class="sxs-lookup"><span data-stu-id="acebc-170">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--no-launch-profile`

<span data-ttu-id="acebc-171">Uygulamayı yapılandırmak için *Launchsettings. JSON* kullanmaya çalışmayın.</span><span class="sxs-lookup"><span data-stu-id="acebc-171">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

`--no-restore`

<span data-ttu-id="acebc-172">Komutu çalıştırılırken örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="acebc-172">Doesn't execute an implicit restore when running the command.</span></span>

`-p|--project <PATH>`

<span data-ttu-id="acebc-173">Çalıştırılacak proje dosyasının yolunu belirtir (klasör adı veya tam yol).</span><span class="sxs-lookup"><span data-stu-id="acebc-173">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="acebc-174">Belirtilmezse, varsayılan olarak geçerli dizini alır.</span><span class="sxs-lookup"><span data-stu-id="acebc-174">If not specified, it defaults to the current directory.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="acebc-175">Paketlerinin geri yükleneceği hedef çalışma zamanını belirtir.</span><span class="sxs-lookup"><span data-stu-id="acebc-175">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="acebc-176">Çalışma zamanı tanımlayıcıları (RID 'Ler) listesi için bkz. [RID kataloğu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="acebc-176">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="acebc-177">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="acebc-177">Sets the verbosity level of the command.</span></span> <span data-ttu-id="acebc-178">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="acebc-178">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="acebc-179">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="acebc-179">.NET Core 2.0</span></span>](#tab/netcore20)

`--`

<span data-ttu-id="acebc-180">Çalıştırılmakta olan uygulamanın bağımsız değişkenlerinden `dotnet run` için bağımsız değişkenleri ayırır.</span><span class="sxs-lookup"><span data-stu-id="acebc-180">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="acebc-181">Bu sınırlayıcıdan sonraki tüm bağımsız değişkenler uygulama çalıştırmasına geçirilir.</span><span class="sxs-lookup"><span data-stu-id="acebc-181">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="acebc-182">Yapı yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="acebc-182">Defines the build configuration.</span></span> <span data-ttu-id="acebc-183">Çoğu proje değeri için varsayılan değer `Debug`.</span><span class="sxs-lookup"><span data-stu-id="acebc-183">The default for most projects value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="acebc-184">Belirtilen [Framework 'ü](../../standard/frameworks.md)kullanarak uygulamayı oluşturur ve çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="acebc-184">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="acebc-185">Çerçeve proje dosyasında belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="acebc-185">The framework must be specified in the project file.</span></span>

`--force`

<span data-ttu-id="acebc-186">Son geri yükleme başarılı olsa bile tüm bağımlılıkların çözülmesini zorlar.</span><span class="sxs-lookup"><span data-stu-id="acebc-186">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="acebc-187">Bu bayrağın belirtilmesi, *Project. varlıklar. JSON* dosyasını silme ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="acebc-187">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="acebc-188">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="acebc-188">Prints out a short help for the command.</span></span>

`--launch-profile <NAME>`

<span data-ttu-id="acebc-189">Uygulamayı başlatırken kullanılacak başlatma profilinin adı (varsa).</span><span class="sxs-lookup"><span data-stu-id="acebc-189">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="acebc-190">Başlatma profilleri, *Launchsettings. JSON* dosyasında tanımlanır ve genellikle `Development`, `Staging`ve `Production`olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="acebc-190">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="acebc-191">Daha fazla bilgi için bkz. [birden çok ortamla çalışma](/aspnet/core/fundamentals/environments).</span><span class="sxs-lookup"><span data-stu-id="acebc-191">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

`--no-build`

<span data-ttu-id="acebc-192">Çalıştırmadan önce projeyi oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="acebc-192">Doesn't build the project before running.</span></span> <span data-ttu-id="acebc-193">Ayrıca `--no-restore` bayrağını örtülü olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="acebc-193">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="acebc-194">Projeden projeye (P2P) başvuruları olan bir projeyi geri yüklerken, başvuruları değil kök projeyi geri yükler.</span><span class="sxs-lookup"><span data-stu-id="acebc-194">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--no-launch-profile`

<span data-ttu-id="acebc-195">Uygulamayı yapılandırmak için *Launchsettings. JSON* kullanmaya çalışmayın.</span><span class="sxs-lookup"><span data-stu-id="acebc-195">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

`--no-restore`

<span data-ttu-id="acebc-196">Komutu çalıştırılırken örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="acebc-196">Doesn't execute an implicit restore when running the command.</span></span>

`-p|--project <PATH>`

<span data-ttu-id="acebc-197">Çalıştırılacak proje dosyasının yolunu belirtir (klasör adı veya tam yol).</span><span class="sxs-lookup"><span data-stu-id="acebc-197">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="acebc-198">Belirtilmezse, varsayılan olarak geçerli dizini alır.</span><span class="sxs-lookup"><span data-stu-id="acebc-198">If not specified, it defaults to the current directory.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="acebc-199">Paketlerinin geri yükleneceği hedef çalışma zamanını belirtir.</span><span class="sxs-lookup"><span data-stu-id="acebc-199">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="acebc-200">Çalışma zamanı tanımlayıcıları (RID 'Ler) listesi için bkz. [RID kataloğu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="acebc-200">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="acebc-201">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="acebc-201">.NET Core 1.x</span></span>](#tab/netcore1x)

`--`

<span data-ttu-id="acebc-202">Çalıştırılmakta olan uygulamanın bağımsız değişkenlerinden `dotnet run` için bağımsız değişkenleri ayırır.</span><span class="sxs-lookup"><span data-stu-id="acebc-202">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="acebc-203">Bu sınırlayıcıdan sonraki tüm bağımsız değişkenler uygulama çalıştırmasına geçirilir.</span><span class="sxs-lookup"><span data-stu-id="acebc-203">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="acebc-204">Yapı yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="acebc-204">Defines the build configuration.</span></span> <span data-ttu-id="acebc-205">Çoğu projenin varsayılan değeri `Debug`.</span><span class="sxs-lookup"><span data-stu-id="acebc-205">The default value for most projects is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="acebc-206">Belirtilen [Framework 'ü](../../standard/frameworks.md)kullanarak uygulamayı oluşturur ve çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="acebc-206">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="acebc-207">Çerçeve proje dosyasında belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="acebc-207">The framework must be specified in the project file.</span></span>

`-h|--help`

<span data-ttu-id="acebc-208">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="acebc-208">Prints out a short help for the command.</span></span>

`-p|--project <PATH/PROJECT.csproj>`

<span data-ttu-id="acebc-209">Proje dosyasının yolunu ve adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="acebc-209">Specifies the path and name of the project file.</span></span> <span data-ttu-id="acebc-210">(Nota bakın.) Belirtilmezse, varsayılan olarak geçerli dizini alır.</span><span class="sxs-lookup"><span data-stu-id="acebc-210">(See the NOTE.) If not specified, it defaults to the current directory.</span></span>

> [!NOTE]
> <span data-ttu-id="acebc-211">`-p|--project` seçeneğiyle proje dosyasının yolunu ve adını kullanın.</span><span class="sxs-lookup"><span data-stu-id="acebc-211">Use the path and name of the project file with the `-p|--project` option.</span></span> <span data-ttu-id="acebc-212">CLı 'deki bir gerileme, .NET Core SDK 1. x ile bir klasör yolu sağlamaya engel olur.</span><span class="sxs-lookup"><span data-stu-id="acebc-212">A regression in the CLI prevents providing a folder path with .NET Core SDK 1.x.</span></span> <span data-ttu-id="acebc-213">Bu sorun hakkında daha fazla bilgi için bkz. [DotNet Run-p, bir proje başlatılamadı (DotNet/clı #5992)](https://github.com/dotnet/cli/issues/5992).</span><span class="sxs-lookup"><span data-stu-id="acebc-213">For more information about this issue, see [dotnet run -p, can not start a project (dotnet/cli #5992)](https://github.com/dotnet/cli/issues/5992).</span></span>

---

## <a name="examples"></a><span data-ttu-id="acebc-214">Örnekler</span><span class="sxs-lookup"><span data-stu-id="acebc-214">Examples</span></span>

<span data-ttu-id="acebc-215">Projeyi geçerli dizinde Çalıştır:</span><span class="sxs-lookup"><span data-stu-id="acebc-215">Run the project in the current directory:</span></span>

`dotnet run`

<span data-ttu-id="acebc-216">Belirtilen projeyi Çalıştır:</span><span class="sxs-lookup"><span data-stu-id="acebc-216">Run the specified project:</span></span>

`dotnet run --project ./projects/proj1/proj1.csproj`

<span data-ttu-id="acebc-217">Projeyi geçerli dizinde çalıştırın (boş `--` seçeneği kullanıldığından bu örnekteki `--help` bağımsız değişkeni uygulamaya geçirilir):</span><span class="sxs-lookup"><span data-stu-id="acebc-217">Run the project in the current directory (the `--help` argument in this example is passed to the application, since the blank `--` option is used):</span></span>

`dotnet run --configuration Release -- --help`

<span data-ttu-id="acebc-218">Geçerli dizindeki proje için bağımlılıkları ve araçları geri yükleme yalnızca minimum çıktıyı gösterir ve ardından projeyi (.NET Core SDK 2,0 ve sonraki sürümleri) çalıştırır:</span><span class="sxs-lookup"><span data-stu-id="acebc-218">Restore dependencies and tools for the project in the current directory only showing minimal output and then run the project: (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet run --verbosity m`
