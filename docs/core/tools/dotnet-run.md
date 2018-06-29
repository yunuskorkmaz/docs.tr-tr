---
title: dotnet .NET Core CLI komutu çalıştırın
description: Komutu çalıştırın dotnet uygulamanızın kaynak kodunu çalıştırmak için uygun bir seçenek sağlar.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 609ac27f21e6801992b9e10c7d465a805492859e
ms.sourcegitcommit: 9e18e4a18284ae9e54c515e30d019c0bbff9cd37
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37071766"
---
# <a name="dotnet-run"></a><span data-ttu-id="49a68-103">dotnet çalıştırın</span><span class="sxs-lookup"><span data-stu-id="49a68-103">dotnet run</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="49a68-104">Ad</span><span class="sxs-lookup"><span data-stu-id="49a68-104">Name</span></span>

<span data-ttu-id="49a68-105">`dotnet run` -Kaynak kodu herhangi bir açık derleme veya başlatma komutları olmadan çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="49a68-105">`dotnet run` - Runs source code without any explicit compile or launch commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="49a68-106">Özet</span><span class="sxs-lookup"><span data-stu-id="49a68-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="49a68-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="49a68-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [-v|--verbosity] [[--] [application arguments]]
dotnet run [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="49a68-108">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="49a68-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [[--] [application arguments]]
dotnet run [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="49a68-109">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="49a68-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet run [-c|--configuration] [-f|--framework] [-p|--project] [[--] [application arguments]]
dotnet run [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="49a68-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="49a68-110">Description</span></span>

<span data-ttu-id="49a68-111">`dotnet run` Komutu bir komut ile kaynak koddan uygulamanızı çalıştırmak için uygun bir seçenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="49a68-111">The `dotnet run` command provides a convenient option to run your application from the source code with one command.</span></span> <span data-ttu-id="49a68-112">Komut satırından hızlı yinelemeli geliştirme için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="49a68-112">It's useful for fast iterative development from the command line.</span></span> <span data-ttu-id="49a68-113">Komut bağlıdır [ `dotnet build` ](dotnet-build.md) kodu oluşturmak için komutu.</span><span class="sxs-lookup"><span data-stu-id="49a68-113">The command depends on the [`dotnet build`](dotnet-build.md) command to build the code.</span></span> <span data-ttu-id="49a68-114">Derleme için tüm gereksinimleri, gibi proje geri yüklenmelidir ilk olarak, geçerli `dotnet run` de.</span><span class="sxs-lookup"><span data-stu-id="49a68-114">Any requirements for the build, such as that the project must be restored first, apply to `dotnet run` as well.</span></span>

<span data-ttu-id="49a68-115">Çıkış dosyaları olan varsayılan konumuna yazılır `bin/<configuration>/<target>`.</span><span class="sxs-lookup"><span data-stu-id="49a68-115">Output files are written into the default location, which is `bin/<configuration>/<target>`.</span></span> <span data-ttu-id="49a68-116">Örneğin, varsa bir `netcoreapp1.0` uygulama ve Çalıştır `dotnet run`, çıktı yerleştirilir `bin/Debug/netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="49a68-116">For example if you have a `netcoreapp1.0` application and you run `dotnet run`, the output is placed in `bin/Debug/netcoreapp1.0`.</span></span> <span data-ttu-id="49a68-117">Gerektiğinde dosyalarının üzerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="49a68-117">Files are overwritten as needed.</span></span> <span data-ttu-id="49a68-118">Geçici dosyalar yerleştirilir `obj` dizin.</span><span class="sxs-lookup"><span data-stu-id="49a68-118">Temporary files are placed in the `obj` directory.</span></span>

<span data-ttu-id="49a68-119">Projenin birden çok çerçeveyi belirtiyorsa, yürütme `dotnet run` sürece hatayla sonuçlanır `-f|--framework <FRAMEWORK>` seçeneği framework belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="49a68-119">If the project specifies multiple frameworks, executing `dotnet run` results in an error unless the `-f|--framework <FRAMEWORK>` option is used to specify the framework.</span></span>

<span data-ttu-id="49a68-120">`dotnet run` Komutu derlemeler oluşturulan değil projeler bağlamında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="49a68-120">The `dotnet run` command is used in the context of projects, not built assemblies.</span></span> <span data-ttu-id="49a68-121">Bunun yerine bir framework bağımlı uygulamayı DLL çalıştırmak çalışıyorsanız, kullanmalısınız [dotnet](dotnet.md) olmadan bir komutu.</span><span class="sxs-lookup"><span data-stu-id="49a68-121">If you're trying to run a framework-dependent application DLL instead, you must use [dotnet](dotnet.md) without a command.</span></span> <span data-ttu-id="49a68-122">Örneğin, çalıştırmak için `myapp.dll`, kullanın:</span><span class="sxs-lookup"><span data-stu-id="49a68-122">For example, to run `myapp.dll`, use:</span></span>

```console
dotnet myapp.dll
```

<span data-ttu-id="49a68-123">Daha fazla bilgi için `dotnet` sürücüsü bkz [.NET Core komut satırı araçları (CLI)](index.md) konu.</span><span class="sxs-lookup"><span data-stu-id="49a68-123">For more information on the `dotnet` driver, see the [.NET Core Command Line Tools (CLI)](index.md) topic.</span></span>

<span data-ttu-id="49a68-124">Uygulamayı çalıştırmak için `dotnet run` komutu NuGet önbelleğinden paylaşılan çalışma zamanı dışında Uygulama bağımlılıklarını giderir.</span><span class="sxs-lookup"><span data-stu-id="49a68-124">To run the application, the `dotnet run` command resolves the dependencies of the application that are outside of the shared runtime from the NuGet cache.</span></span> <span data-ttu-id="49a68-125">Önbelleğe alınan bağımlılıkları kullandığından, onu kullanmak önerilmez `dotnet run` üretimde uygulamaları çalıştırmak için.</span><span class="sxs-lookup"><span data-stu-id="49a68-125">Because it uses cached dependencies, it's not recommended to use `dotnet run` to run applications in production.</span></span> <span data-ttu-id="49a68-126">Bunun yerine, [bir dağıtım oluşturmak](../deploying/index.md) kullanarak [ `dotnet publish` ](dotnet-publish.md) komut ve yayımlanan çıkış dağıtın.</span><span class="sxs-lookup"><span data-stu-id="49a68-126">Instead, [create a deployment](../deploying/index.md) using the [`dotnet publish`](dotnet-publish.md) command and deploy the published output.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a><span data-ttu-id="49a68-127">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="49a68-127">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="49a68-128">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="49a68-128">.NET Core 2.1</span></span>](#tab/netcore21)

`--`

<span data-ttu-id="49a68-129">Bağımsız değişkenleri sınırlandırır `dotnet run` gelen çalıştırılan uygulama için bağımsız değişkenler.</span><span class="sxs-lookup"><span data-stu-id="49a68-129">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="49a68-130">Tüm bağımsız değişkenler bu sınırlayıcı sonra Çalıştırma uygulaması geçirilir.</span><span class="sxs-lookup"><span data-stu-id="49a68-130">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="49a68-131">Derleme yapılandırması tanımlar.</span><span class="sxs-lookup"><span data-stu-id="49a68-131">Defines the build configuration.</span></span> <span data-ttu-id="49a68-132">Varsayılan değer `Debug` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="49a68-132">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="49a68-133">Derlemeler ve belirtilen kullanarak uygulamayı çalıştıran [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="49a68-133">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="49a68-134">Proje dosyasında framework belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="49a68-134">The framework must be specified in the project file.</span></span>

`--force`

<span data-ttu-id="49a68-135">Son geri yükleme başarılı olsa bile çözümlenmesi için tüm bağımlılıkları zorlar.</span><span class="sxs-lookup"><span data-stu-id="49a68-135">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="49a68-136">Bu bayrak belirten aynıdır silme *project.assets.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="49a68-136">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="49a68-137">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="49a68-137">Prints out a short help for the command.</span></span>

`--launch-profile <NAME>`

<span data-ttu-id="49a68-138">Başlatma adını profil (varsa) uygulama başlatılırken kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="49a68-138">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="49a68-139">Başlatma profilleri tanımlanmış *launchSettings.json* dosya ve genellikle adlı `Development`, `Staging`, ve `Production`.</span><span class="sxs-lookup"><span data-stu-id="49a68-139">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="49a68-140">Daha fazla bilgi için bkz: [birden çok ortamlarıyla çalışma](/aspnet/core/fundamentals/environments).</span><span class="sxs-lookup"><span data-stu-id="49a68-140">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

`--no-build`

<span data-ttu-id="49a68-141">Çalıştırmadan önce projeyi derlemek değil.</span><span class="sxs-lookup"><span data-stu-id="49a68-141">Doesn't build the project before running.</span></span> <span data-ttu-id="49a68-142">Ayrıca örtük ayarlar `--no-restore` bayrağı.</span><span class="sxs-lookup"><span data-stu-id="49a68-142">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="49a68-143">Proje Proje (P2P) başvuruları içeren bir proje geri yüklerken, kök proje ve başvuru geri yükler.</span><span class="sxs-lookup"><span data-stu-id="49a68-143">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--no-launch-profile`

<span data-ttu-id="49a68-144">Kullanmaya çalıştığınızda değil *launchSettings.json* uygulamayı yapılandırmak için.</span><span class="sxs-lookup"><span data-stu-id="49a68-144">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

`--no-restore`

<span data-ttu-id="49a68-145">Örtük bir geri yükleme komutu çalıştırırken yürütmez.</span><span class="sxs-lookup"><span data-stu-id="49a68-145">Doesn't execute an implicit restore when running the command.</span></span>

`-p|--project <PATH>`

<span data-ttu-id="49a68-146">(Klasör adı veya tam yolu) çalıştırmak için proje dosyasının yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="49a68-146">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="49a68-147">Belirtilmezse, geçerli dizine varsayılan olur.</span><span class="sxs-lookup"><span data-stu-id="49a68-147">If not specified, it defaults to the current directory.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="49a68-148">Paketler için geri yüklemek için hedef çalışma zamanı belirtir.</span><span class="sxs-lookup"><span data-stu-id="49a68-148">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="49a68-149">Çalışma zamanı tanımlayıcıları (RID) bir listesi için bkz: [RID katalog](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="49a68-149">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="49a68-150">Komutun ayrıntı düzeyi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="49a68-150">Sets the verbosity level of the command.</span></span> <span data-ttu-id="49a68-151">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="49a68-151">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="49a68-152">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="49a68-152">.NET Core 2.0</span></span>](#tab/netcore20)

`--`

<span data-ttu-id="49a68-153">Bağımsız değişkenleri sınırlandırır `dotnet run` gelen çalıştırılan uygulama için bağımsız değişkenler.</span><span class="sxs-lookup"><span data-stu-id="49a68-153">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="49a68-154">Tüm bağımsız değişkenler bu sınırlayıcı sonra Çalıştırma uygulaması geçirilir.</span><span class="sxs-lookup"><span data-stu-id="49a68-154">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="49a68-155">Derleme yapılandırması tanımlar.</span><span class="sxs-lookup"><span data-stu-id="49a68-155">Defines the build configuration.</span></span> <span data-ttu-id="49a68-156">Varsayılan değer `Debug` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="49a68-156">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="49a68-157">Derlemeler ve belirtilen kullanarak uygulamayı çalıştıran [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="49a68-157">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="49a68-158">Proje dosyasında framework belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="49a68-158">The framework must be specified in the project file.</span></span>

`--force`

<span data-ttu-id="49a68-159">Son geri yükleme başarılı olsa bile çözümlenmesi için tüm bağımlılıkları zorlar.</span><span class="sxs-lookup"><span data-stu-id="49a68-159">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="49a68-160">Bu bayrak belirten aynıdır silme *project.assets.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="49a68-160">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="49a68-161">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="49a68-161">Prints out a short help for the command.</span></span>

`--launch-profile <NAME>`

<span data-ttu-id="49a68-162">Başlatma adını profil (varsa) uygulama başlatılırken kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="49a68-162">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="49a68-163">Başlatma profilleri tanımlanmış *launchSettings.json* dosya ve genellikle adlı `Development`, `Staging`, ve `Production`.</span><span class="sxs-lookup"><span data-stu-id="49a68-163">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="49a68-164">Daha fazla bilgi için bkz: [birden çok ortamlarıyla çalışma](/aspnet/core/fundamentals/environments).</span><span class="sxs-lookup"><span data-stu-id="49a68-164">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

`--no-build`

<span data-ttu-id="49a68-165">Çalıştırmadan önce projeyi derlemek değil.</span><span class="sxs-lookup"><span data-stu-id="49a68-165">Doesn't build the project before running.</span></span> <span data-ttu-id="49a68-166">Ayrıca örtük ayarlar `--no-restore` bayrağı.</span><span class="sxs-lookup"><span data-stu-id="49a68-166">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="49a68-167">Proje Proje (P2P) başvuruları içeren bir proje geri yüklerken, kök proje ve başvuru geri yükler.</span><span class="sxs-lookup"><span data-stu-id="49a68-167">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--no-launch-profile`

<span data-ttu-id="49a68-168">Kullanmaya çalıştığınızda değil *launchSettings.json* uygulamayı yapılandırmak için.</span><span class="sxs-lookup"><span data-stu-id="49a68-168">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

`--no-restore`

<span data-ttu-id="49a68-169">Örtük bir geri yükleme komutu çalıştırırken yürütmez.</span><span class="sxs-lookup"><span data-stu-id="49a68-169">Doesn't execute an implicit restore when running the command.</span></span>

`-p|--project <PATH>`

<span data-ttu-id="49a68-170">(Klasör adı veya tam yolu) çalıştırmak için proje dosyasının yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="49a68-170">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="49a68-171">Belirtilmezse, geçerli dizine varsayılan olur.</span><span class="sxs-lookup"><span data-stu-id="49a68-171">If not specified, it defaults to the current directory.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="49a68-172">Paketler için geri yüklemek için hedef çalışma zamanı belirtir.</span><span class="sxs-lookup"><span data-stu-id="49a68-172">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="49a68-173">Çalışma zamanı tanımlayıcıları (RID) bir listesi için bkz: [RID katalog](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="49a68-173">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="49a68-174">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="49a68-174">.NET Core 1.x</span></span>](#tab/netcore1x)

`--`

<span data-ttu-id="49a68-175">Bağımsız değişkenleri sınırlandırır `dotnet run` gelen çalıştırılan uygulama için bağımsız değişkenler.</span><span class="sxs-lookup"><span data-stu-id="49a68-175">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="49a68-176">Tüm bağımsız değişkenler bu sınırlayıcı sonra Çalıştırma uygulaması geçirilir.</span><span class="sxs-lookup"><span data-stu-id="49a68-176">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="49a68-177">Derleme yapılandırması tanımlar.</span><span class="sxs-lookup"><span data-stu-id="49a68-177">Defines the build configuration.</span></span> <span data-ttu-id="49a68-178">Varsayılan değer `Debug` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="49a68-178">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="49a68-179">Derlemeler ve belirtilen kullanarak uygulamayı çalıştıran [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="49a68-179">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="49a68-180">Proje dosyasında framework belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="49a68-180">The framework must be specified in the project file.</span></span>

`-h|--help`

<span data-ttu-id="49a68-181">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="49a68-181">Prints out a short help for the command.</span></span>

`-p|--project <PATH/PROJECT.csproj>`

<span data-ttu-id="49a68-182">Proje dosyasının adını ve yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="49a68-182">Specifies the path and name of the project file.</span></span> <span data-ttu-id="49a68-183">(NOTA bakın.) Belirtilmezse, geçerli dizine varsayılan olur.</span><span class="sxs-lookup"><span data-stu-id="49a68-183">(See the NOTE.) If not specified, it defaults to the current directory.</span></span>

> [!NOTE]
> <span data-ttu-id="49a68-184">Proje dosyası ile adını ve yolunu kullanın `-p|--project` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="49a68-184">Use the path and name of the project file with the `-p|--project` option.</span></span> <span data-ttu-id="49a68-185">.NET Core SDK ile bir klasör yolu sağlayan CLI'teki bir gerileme engeller 1.x.</span><span class="sxs-lookup"><span data-stu-id="49a68-185">A regression in the CLI prevents providing a folder path with .NET Core SDK 1.x.</span></span> <span data-ttu-id="49a68-186">Bu sorun hakkında daha fazla bilgi için bkz: [-p, çalıştırmak dotnet değil (dotnet/CLI #5992) proje Başlat](https://github.com/dotnet/cli/issues/5992).</span><span class="sxs-lookup"><span data-stu-id="49a68-186">For more information about this issue, see [dotnet run -p, can not start a project (dotnet/cli #5992)](https://github.com/dotnet/cli/issues/5992).</span></span>

---

## <a name="examples"></a><span data-ttu-id="49a68-187">Örnekler</span><span class="sxs-lookup"><span data-stu-id="49a68-187">Examples</span></span>

<span data-ttu-id="49a68-188">Proje geçerli dizinde çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="49a68-188">Run the project in the current directory:</span></span>

`dotnet run`

<span data-ttu-id="49a68-189">Belirtilen proje çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="49a68-189">Run the specified project:</span></span>

`dotnet run --project ./projects/proj1/proj1.csproj`

<span data-ttu-id="49a68-190">Geçerli dizinde projeyi çalıştırın ( `--help` Bu örnekte bağımsız değişkeni boş bu yana uygulama geçirilir `--` seçeneği kullanıldığında):</span><span class="sxs-lookup"><span data-stu-id="49a68-190">Run the project in the current directory (the `--help` argument in this example is passed to the application, since the blank `--` option is used):</span></span>

`dotnet run --configuration Release -- --help`

<span data-ttu-id="49a68-191">Bağımlılıklar ve geçerli dizinde proje için araçları çıkış ve projeyi çalıştırın en az gösteren yalnızca geri yükleme: (.NET Core SDK 2.0 ve sonraki sürümler):</span><span class="sxs-lookup"><span data-stu-id="49a68-191">Restore dependencies and tools for the project in the current directory only showing minimal output and then run the project: (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet run --verbosity m`