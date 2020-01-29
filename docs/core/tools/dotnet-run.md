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
# <a name="dotnet-run"></a><span data-ttu-id="39cd6-103">dotnet run</span><span class="sxs-lookup"><span data-stu-id="39cd6-103">dotnet run</span></span>

<span data-ttu-id="39cd6-104">**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 1. x SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="39cd6-104">**This article applies to:** ✔️ .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="39cd6-105">Name</span><span class="sxs-lookup"><span data-stu-id="39cd6-105">Name</span></span>

<span data-ttu-id="39cd6-106">`dotnet run`-herhangi bir açık derleme veya başlatma komutu olmadan kaynak kodu çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="39cd6-106">`dotnet run` - Runs source code without any explicit compile or launch commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="39cd6-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="39cd6-107">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="39cd6-108">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="39cd6-108">.NET Core 3.0</span></span>](#tab/netcore30)

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [--force] [--interactive] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [-r|--runtime] [-v|--verbosity] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="39cd6-109">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="39cd6-109">.NET Core 2.1</span></span>](#tab/netcore21)

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [-v|--verbosity] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="39cd6-110">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="39cd6-110">.NET Core 2.0</span></span>](#tab/netcore20)

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="39cd6-111">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="39cd6-111">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [-p|--project] [[--] [application arguments]]
dotnet run [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="39cd6-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="39cd6-112">Description</span></span>

<span data-ttu-id="39cd6-113">`dotnet run` komutu, uygulamanızı kaynak koddan tek bir komutla çalıştırmak için uygun bir seçenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="39cd6-113">The `dotnet run` command provides a convenient option to run your application from the source code with one command.</span></span> <span data-ttu-id="39cd6-114">Komut satırından hızlı yinelemeli geliştirme için faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="39cd6-114">It's useful for fast iterative development from the command line.</span></span> <span data-ttu-id="39cd6-115">Komut, kodu derlemek için [`dotnet build`](dotnet-build.md) komutuna bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="39cd6-115">The command depends on the [`dotnet build`](dotnet-build.md) command to build the code.</span></span> <span data-ttu-id="39cd6-116">Projenin önce geri yüklenmesi gerektiği gibi, derleme için tüm gereksinimler, `dotnet run` için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="39cd6-116">Any requirements for the build, such as that the project must be restored first, apply to `dotnet run` as well.</span></span>

<span data-ttu-id="39cd6-117">Çıktı dosyaları varsayılan konuma yazılır, bu `bin/<configuration>/<target>`.</span><span class="sxs-lookup"><span data-stu-id="39cd6-117">Output files are written into the default location, which is `bin/<configuration>/<target>`.</span></span> <span data-ttu-id="39cd6-118">Örneğin, bir `netcoreapp2.1` uygulamanız varsa ve `dotnet run`çalıştırırsanız, çıktı `bin/Debug/netcoreapp2.1`yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="39cd6-118">For example if you have a `netcoreapp2.1` application and you run `dotnet run`, the output is placed in `bin/Debug/netcoreapp2.1`.</span></span> <span data-ttu-id="39cd6-119">Dosyalar gerektiği gibi üzerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="39cd6-119">Files are overwritten as needed.</span></span> <span data-ttu-id="39cd6-120">Geçici dosyalar `obj` dizinine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="39cd6-120">Temporary files are placed in the `obj` directory.</span></span>

<span data-ttu-id="39cd6-121">Proje birden çok çerçeve belirtiyorsa, Framework 'ü belirtmek için `-f|--framework <FRAMEWORK>` seçeneği kullanılmadığı müddetçe `dotnet run` yürütülerek hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="39cd6-121">If the project specifies multiple frameworks, executing `dotnet run` results in an error unless the `-f|--framework <FRAMEWORK>` option is used to specify the framework.</span></span>

<span data-ttu-id="39cd6-122">`dotnet run` komutu, oluşturulan derlemeler değil, proje bağlamında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="39cd6-122">The `dotnet run` command is used in the context of projects, not built assemblies.</span></span> <span data-ttu-id="39cd6-123">Bunun yerine Framework 'e bağımlı bir uygulama DLL 'sini çalıştırmaya çalışıyorsanız, bir komut olmadan [DotNet](dotnet.md) kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="39cd6-123">If you're trying to run a framework-dependent application DLL instead, you must use [dotnet](dotnet.md) without a command.</span></span> <span data-ttu-id="39cd6-124">Örneğin, `myapp.dll`çalıştırmak için şunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="39cd6-124">For example, to run `myapp.dll`, use:</span></span>

```dotnetcli
dotnet myapp.dll
```

<span data-ttu-id="39cd6-125">`dotnet` sürücüsü hakkında daha fazla bilgi için bkz. [.NET Core komut satırı araçları (CLI)](index.md) konusu.</span><span class="sxs-lookup"><span data-stu-id="39cd6-125">For more information on the `dotnet` driver, see the [.NET Core Command Line Tools (CLI)](index.md) topic.</span></span>

<span data-ttu-id="39cd6-126">Uygulamayı çalıştırmak için `dotnet run` komutu, paylaşılan çalışma zamanının dışındaki uygulamanın tüm bağımlılıklarını NuGet önbelleğinden çözer.</span><span class="sxs-lookup"><span data-stu-id="39cd6-126">To run the application, the `dotnet run` command resolves the dependencies of the application that are outside of the shared runtime from the NuGet cache.</span></span> <span data-ttu-id="39cd6-127">Önbelleğe alınmış bağımlılıkları kullandığından, üretimde uygulamaları çalıştırmak için `dotnet run` kullanılması önerilmez.</span><span class="sxs-lookup"><span data-stu-id="39cd6-127">Because it uses cached dependencies, it's not recommended to use `dotnet run` to run applications in production.</span></span> <span data-ttu-id="39cd6-128">Bunun yerine, [`dotnet publish`](dotnet-publish.md) komutunu kullanarak [bir dağıtım oluşturun](../deploying/index.md) ve yayımlanan çıktıyı dağıtın.</span><span class="sxs-lookup"><span data-stu-id="39cd6-128">Instead, [create a deployment](../deploying/index.md) using the [`dotnet publish`](dotnet-publish.md) command and deploy the published output.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a><span data-ttu-id="39cd6-129">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="39cd6-129">Options</span></span>

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="39cd6-130">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="39cd6-130">.NET Core 3.0</span></span>](#tab/netcore30)

`--`

<span data-ttu-id="39cd6-131">Çalıştırılmakta olan uygulamanın bağımsız değişkenlerinden `dotnet run` için bağımsız değişkenleri ayırır.</span><span class="sxs-lookup"><span data-stu-id="39cd6-131">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="39cd6-132">Bu sınırlayıcıdan sonraki tüm bağımsız değişkenler uygulama çalıştırmasına geçirilir.</span><span class="sxs-lookup"><span data-stu-id="39cd6-132">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="39cd6-133">Yapı yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="39cd6-133">Defines the build configuration.</span></span> <span data-ttu-id="39cd6-134">Çoğu projenin varsayılan değeri `Debug`.</span><span class="sxs-lookup"><span data-stu-id="39cd6-134">The default value for most projects is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="39cd6-135">Belirtilen [Framework 'ü](../../standard/frameworks.md)kullanarak uygulamayı oluşturur ve çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="39cd6-135">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="39cd6-136">Çerçeve proje dosyasında belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="39cd6-136">The framework must be specified in the project file.</span></span>

`--force`

<span data-ttu-id="39cd6-137">Son geri yükleme başarılı olsa bile tüm bağımlılıkların çözülmesini zorlar.</span><span class="sxs-lookup"><span data-stu-id="39cd6-137">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="39cd6-138">Bu bayrağın belirtilmesi, *Project. varlıklar. JSON* dosyasını silme ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="39cd6-138">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="39cd6-139">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="39cd6-139">Prints out a short help for the command.</span></span>

`--interactive`

<span data-ttu-id="39cd6-140">Komutun, Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir (örneğin, kimlik doğrulamasını tamamlamaya yönelik).</span><span class="sxs-lookup"><span data-stu-id="39cd6-140">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span>

`--launch-profile <NAME>`

<span data-ttu-id="39cd6-141">Uygulamayı başlatırken kullanılacak başlatma profilinin adı (varsa).</span><span class="sxs-lookup"><span data-stu-id="39cd6-141">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="39cd6-142">Başlatma profilleri, *Launchsettings. JSON* dosyasında tanımlanır ve genellikle `Development`, `Staging`ve `Production`olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="39cd6-142">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="39cd6-143">Daha fazla bilgi için bkz. [birden çok ortamla çalışma](/aspnet/core/fundamentals/environments).</span><span class="sxs-lookup"><span data-stu-id="39cd6-143">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

`--no-build`

<span data-ttu-id="39cd6-144">Çalıştırmadan önce projeyi oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="39cd6-144">Doesn't build the project before running.</span></span> <span data-ttu-id="39cd6-145">Ayrıca `--no-restore` bayrağını örtülü olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="39cd6-145">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="39cd6-146">Projeden projeye (P2P) başvuruları olan bir projeyi geri yüklerken, başvuruları değil kök projeyi geri yükler.</span><span class="sxs-lookup"><span data-stu-id="39cd6-146">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--no-launch-profile`

<span data-ttu-id="39cd6-147">Uygulamayı yapılandırmak için *Launchsettings. JSON* kullanmaya çalışmayın.</span><span class="sxs-lookup"><span data-stu-id="39cd6-147">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

`--no-restore`

<span data-ttu-id="39cd6-148">Komutu çalıştırılırken örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="39cd6-148">Doesn't execute an implicit restore when running the command.</span></span>

`-p|--project <PATH>`

<span data-ttu-id="39cd6-149">Çalıştırılacak proje dosyasının yolunu belirtir (klasör adı veya tam yol).</span><span class="sxs-lookup"><span data-stu-id="39cd6-149">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="39cd6-150">Belirtilmezse, varsayılan olarak geçerli dizini alır.</span><span class="sxs-lookup"><span data-stu-id="39cd6-150">If not specified, it defaults to the current directory.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="39cd6-151">Paketlerinin geri yükleneceği hedef çalışma zamanını belirtir.</span><span class="sxs-lookup"><span data-stu-id="39cd6-151">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="39cd6-152">Çalışma zamanı tanımlayıcıları (RID 'Ler) listesi için bkz. [RID kataloğu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="39cd6-152">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="39cd6-153">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="39cd6-153">Sets the verbosity level of the command.</span></span> <span data-ttu-id="39cd6-154">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="39cd6-154">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="39cd6-155">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="39cd6-155">.NET Core 2.1</span></span>](#tab/netcore21)

`--`

<span data-ttu-id="39cd6-156">Çalıştırılmakta olan uygulamanın bağımsız değişkenlerinden `dotnet run` için bağımsız değişkenleri ayırır.</span><span class="sxs-lookup"><span data-stu-id="39cd6-156">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="39cd6-157">Bu sınırlayıcıdan sonraki tüm bağımsız değişkenler uygulama çalıştırmasına geçirilir.</span><span class="sxs-lookup"><span data-stu-id="39cd6-157">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="39cd6-158">Yapı yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="39cd6-158">Defines the build configuration.</span></span> <span data-ttu-id="39cd6-159">Çoğu projenin varsayılan değeri `Debug`.</span><span class="sxs-lookup"><span data-stu-id="39cd6-159">The default value for most projects is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="39cd6-160">Belirtilen [Framework 'ü](../../standard/frameworks.md)kullanarak uygulamayı oluşturur ve çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="39cd6-160">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="39cd6-161">Çerçeve proje dosyasında belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="39cd6-161">The framework must be specified in the project file.</span></span>

`--force`

<span data-ttu-id="39cd6-162">Son geri yükleme başarılı olsa bile tüm bağımlılıkların çözülmesini zorlar.</span><span class="sxs-lookup"><span data-stu-id="39cd6-162">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="39cd6-163">Bu bayrağın belirtilmesi, *Project. varlıklar. JSON* dosyasını silme ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="39cd6-163">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="39cd6-164">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="39cd6-164">Prints out a short help for the command.</span></span>

`--launch-profile <NAME>`

<span data-ttu-id="39cd6-165">Uygulamayı başlatırken kullanılacak başlatma profilinin adı (varsa).</span><span class="sxs-lookup"><span data-stu-id="39cd6-165">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="39cd6-166">Başlatma profilleri, *Launchsettings. JSON* dosyasında tanımlanır ve genellikle `Development`, `Staging`ve `Production`olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="39cd6-166">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="39cd6-167">Daha fazla bilgi için bkz. [birden çok ortamla çalışma](/aspnet/core/fundamentals/environments).</span><span class="sxs-lookup"><span data-stu-id="39cd6-167">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

`--no-build`

<span data-ttu-id="39cd6-168">Çalıştırmadan önce projeyi oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="39cd6-168">Doesn't build the project before running.</span></span> <span data-ttu-id="39cd6-169">Ayrıca `--no-restore` bayrağını örtülü olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="39cd6-169">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="39cd6-170">Projeden projeye (P2P) başvuruları olan bir projeyi geri yüklerken, başvuruları değil kök projeyi geri yükler.</span><span class="sxs-lookup"><span data-stu-id="39cd6-170">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--no-launch-profile`

<span data-ttu-id="39cd6-171">Uygulamayı yapılandırmak için *Launchsettings. JSON* kullanmaya çalışmayın.</span><span class="sxs-lookup"><span data-stu-id="39cd6-171">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

`--no-restore`

<span data-ttu-id="39cd6-172">Komutu çalıştırılırken örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="39cd6-172">Doesn't execute an implicit restore when running the command.</span></span>

`-p|--project <PATH>`

<span data-ttu-id="39cd6-173">Çalıştırılacak proje dosyasının yolunu belirtir (klasör adı veya tam yol).</span><span class="sxs-lookup"><span data-stu-id="39cd6-173">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="39cd6-174">Belirtilmezse, varsayılan olarak geçerli dizini alır.</span><span class="sxs-lookup"><span data-stu-id="39cd6-174">If not specified, it defaults to the current directory.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="39cd6-175">Paketlerinin geri yükleneceği hedef çalışma zamanını belirtir.</span><span class="sxs-lookup"><span data-stu-id="39cd6-175">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="39cd6-176">Çalışma zamanı tanımlayıcıları (RID 'Ler) listesi için bkz. [RID kataloğu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="39cd6-176">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="39cd6-177">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="39cd6-177">Sets the verbosity level of the command.</span></span> <span data-ttu-id="39cd6-178">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="39cd6-178">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="39cd6-179">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="39cd6-179">.NET Core 2.0</span></span>](#tab/netcore20)

`--`

<span data-ttu-id="39cd6-180">Çalıştırılmakta olan uygulamanın bağımsız değişkenlerinden `dotnet run` için bağımsız değişkenleri ayırır.</span><span class="sxs-lookup"><span data-stu-id="39cd6-180">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="39cd6-181">Bu sınırlayıcıdan sonraki tüm bağımsız değişkenler uygulama çalıştırmasına geçirilir.</span><span class="sxs-lookup"><span data-stu-id="39cd6-181">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="39cd6-182">Yapı yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="39cd6-182">Defines the build configuration.</span></span> <span data-ttu-id="39cd6-183">Çoğu proje değeri için varsayılan değer `Debug`.</span><span class="sxs-lookup"><span data-stu-id="39cd6-183">The default for most projects value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="39cd6-184">Belirtilen [Framework 'ü](../../standard/frameworks.md)kullanarak uygulamayı oluşturur ve çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="39cd6-184">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="39cd6-185">Çerçeve proje dosyasında belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="39cd6-185">The framework must be specified in the project file.</span></span>

`--force`

<span data-ttu-id="39cd6-186">Son geri yükleme başarılı olsa bile tüm bağımlılıkların çözülmesini zorlar.</span><span class="sxs-lookup"><span data-stu-id="39cd6-186">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="39cd6-187">Bu bayrağın belirtilmesi, *Project. varlıklar. JSON* dosyasını silme ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="39cd6-187">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="39cd6-188">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="39cd6-188">Prints out a short help for the command.</span></span>

`--launch-profile <NAME>`

<span data-ttu-id="39cd6-189">Uygulamayı başlatırken kullanılacak başlatma profilinin adı (varsa).</span><span class="sxs-lookup"><span data-stu-id="39cd6-189">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="39cd6-190">Başlatma profilleri, *Launchsettings. JSON* dosyasında tanımlanır ve genellikle `Development`, `Staging`ve `Production`olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="39cd6-190">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="39cd6-191">Daha fazla bilgi için bkz. [birden çok ortamla çalışma](/aspnet/core/fundamentals/environments).</span><span class="sxs-lookup"><span data-stu-id="39cd6-191">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

`--no-build`

<span data-ttu-id="39cd6-192">Çalıştırmadan önce projeyi oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="39cd6-192">Doesn't build the project before running.</span></span> <span data-ttu-id="39cd6-193">Ayrıca `--no-restore` bayrağını örtülü olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="39cd6-193">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="39cd6-194">Projeden projeye (P2P) başvuruları olan bir projeyi geri yüklerken, başvuruları değil kök projeyi geri yükler.</span><span class="sxs-lookup"><span data-stu-id="39cd6-194">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--no-launch-profile`

<span data-ttu-id="39cd6-195">Uygulamayı yapılandırmak için *Launchsettings. JSON* kullanmaya çalışmayın.</span><span class="sxs-lookup"><span data-stu-id="39cd6-195">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

`--no-restore`

<span data-ttu-id="39cd6-196">Komutu çalıştırılırken örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="39cd6-196">Doesn't execute an implicit restore when running the command.</span></span>

`-p|--project <PATH>`

<span data-ttu-id="39cd6-197">Çalıştırılacak proje dosyasının yolunu belirtir (klasör adı veya tam yol).</span><span class="sxs-lookup"><span data-stu-id="39cd6-197">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="39cd6-198">Belirtilmezse, varsayılan olarak geçerli dizini alır.</span><span class="sxs-lookup"><span data-stu-id="39cd6-198">If not specified, it defaults to the current directory.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="39cd6-199">Paketlerinin geri yükleneceği hedef çalışma zamanını belirtir.</span><span class="sxs-lookup"><span data-stu-id="39cd6-199">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="39cd6-200">Çalışma zamanı tanımlayıcıları (RID 'Ler) listesi için bkz. [RID kataloğu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="39cd6-200">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="39cd6-201">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="39cd6-201">.NET Core 1.x</span></span>](#tab/netcore1x)

`--`

<span data-ttu-id="39cd6-202">Çalıştırılmakta olan uygulamanın bağımsız değişkenlerinden `dotnet run` için bağımsız değişkenleri ayırır.</span><span class="sxs-lookup"><span data-stu-id="39cd6-202">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="39cd6-203">Bu sınırlayıcıdan sonraki tüm bağımsız değişkenler uygulama çalıştırmasına geçirilir.</span><span class="sxs-lookup"><span data-stu-id="39cd6-203">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="39cd6-204">Yapı yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="39cd6-204">Defines the build configuration.</span></span> <span data-ttu-id="39cd6-205">Çoğu projenin varsayılan değeri `Debug`.</span><span class="sxs-lookup"><span data-stu-id="39cd6-205">The default value for most projects is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="39cd6-206">Belirtilen [Framework 'ü](../../standard/frameworks.md)kullanarak uygulamayı oluşturur ve çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="39cd6-206">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="39cd6-207">Çerçeve proje dosyasında belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="39cd6-207">The framework must be specified in the project file.</span></span>

`-h|--help`

<span data-ttu-id="39cd6-208">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="39cd6-208">Prints out a short help for the command.</span></span>

`-p|--project <PATH/PROJECT.csproj>`

<span data-ttu-id="39cd6-209">Proje dosyasının yolunu ve adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="39cd6-209">Specifies the path and name of the project file.</span></span> <span data-ttu-id="39cd6-210">(Nota bakın.) Belirtilmezse, varsayılan olarak geçerli dizini alır.</span><span class="sxs-lookup"><span data-stu-id="39cd6-210">(See the NOTE.) If not specified, it defaults to the current directory.</span></span>

> [!NOTE]
> <span data-ttu-id="39cd6-211">`-p|--project` seçeneğiyle proje dosyasının yolunu ve adını kullanın.</span><span class="sxs-lookup"><span data-stu-id="39cd6-211">Use the path and name of the project file with the `-p|--project` option.</span></span> <span data-ttu-id="39cd6-212">CLı 'deki bir gerileme, .NET Core SDK 1. x ile bir klasör yolu sağlamaya engel olur.</span><span class="sxs-lookup"><span data-stu-id="39cd6-212">A regression in the CLI prevents providing a folder path with .NET Core SDK 1.x.</span></span> <span data-ttu-id="39cd6-213">Bu sorun hakkında daha fazla bilgi için bkz. [DotNet Run-p, bir proje başlatılamadı (DotNet/clı #5992)](https://github.com/dotnet/cli/issues/5992).</span><span class="sxs-lookup"><span data-stu-id="39cd6-213">For more information about this issue, see [dotnet run -p, can not start a project (dotnet/cli #5992)](https://github.com/dotnet/cli/issues/5992).</span></span>

---

## <a name="examples"></a><span data-ttu-id="39cd6-214">Örnekler</span><span class="sxs-lookup"><span data-stu-id="39cd6-214">Examples</span></span>

<span data-ttu-id="39cd6-215">Projeyi geçerli dizinde Çalıştır:</span><span class="sxs-lookup"><span data-stu-id="39cd6-215">Run the project in the current directory:</span></span>

`dotnet run`

<span data-ttu-id="39cd6-216">Belirtilen projeyi Çalıştır:</span><span class="sxs-lookup"><span data-stu-id="39cd6-216">Run the specified project:</span></span>

`dotnet run --project ./projects/proj1/proj1.csproj`

<span data-ttu-id="39cd6-217">Projeyi geçerli dizinde çalıştırın (boş `--` seçeneği kullanıldığından bu örnekteki `--help` bağımsız değişkeni uygulamaya geçirilir):</span><span class="sxs-lookup"><span data-stu-id="39cd6-217">Run the project in the current directory (the `--help` argument in this example is passed to the application, since the blank `--` option is used):</span></span>

`dotnet run --configuration Release -- --help`

<span data-ttu-id="39cd6-218">Geçerli dizindeki proje için bağımlılıkları ve araçları geri yükleme yalnızca minimum çıktıyı gösterir ve ardından projeyi (.NET Core SDK 2,0 ve sonraki sürümleri) çalıştırır:</span><span class="sxs-lookup"><span data-stu-id="39cd6-218">Restore dependencies and tools for the project in the current directory only showing minimal output and then run the project: (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet run --verbosity m`
