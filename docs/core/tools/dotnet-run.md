---
title: dotnet .NET Core CLI komutu çalıştırın
description: Komutu çalıştırın dotnet uygulamanızın kaynak kodunu çalıştırmak için uygun bir seçenek sağlar.
author: mairaw
ms.author: mairaw
ms.date: 03/10/2018
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 18ceb395ed025fa562f295fc2facd00c67a75536
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-run"></a><span data-ttu-id="cf969-103">dotnet çalıştırın</span><span class="sxs-lookup"><span data-stu-id="cf969-103">dotnet run</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="cf969-104">Ad</span><span class="sxs-lookup"><span data-stu-id="cf969-104">Name</span></span>

<span data-ttu-id="cf969-105">`dotnet run` -Kaynak kodu herhangi bir açık derleme veya başlatma komutları olmadan çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="cf969-105">`dotnet run` - Runs source code without any explicit compile or launch commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="cf969-106">Özet</span><span class="sxs-lookup"><span data-stu-id="cf969-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="cf969-107">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="cf969-107">.NET Core 2.x</span></span>](#tab/netcore2x)

```
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies] [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="cf969-108">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="cf969-108">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet run [-c|--configuration] [-f|--framework] [-p|--project] [[--] [application arguments]]
dotnet run [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="cf969-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cf969-109">Description</span></span>

<span data-ttu-id="cf969-110">`dotnet run` Komutu bir komut ile kaynak koddan uygulamanızı çalıştırmak için uygun bir seçenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="cf969-110">The `dotnet run` command provides a convenient option to run your application from the source code with one command.</span></span> <span data-ttu-id="cf969-111">Komut satırından hızlı yinelemeli geliştirme için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="cf969-111">It's useful for fast iterative development from the command line.</span></span> <span data-ttu-id="cf969-112">Komut bağlıdır [ `dotnet build` ](dotnet-build.md) kodu oluşturmak için komutu.</span><span class="sxs-lookup"><span data-stu-id="cf969-112">The command depends on the [`dotnet build`](dotnet-build.md) command to build the code.</span></span> <span data-ttu-id="cf969-113">Derleme için tüm gereksinimleri, gibi proje geri yüklenmelidir ilk olarak, geçerli `dotnet run` de.</span><span class="sxs-lookup"><span data-stu-id="cf969-113">Any requirements for the build, such as that the project must be restored first, apply to `dotnet run` as well.</span></span>

<span data-ttu-id="cf969-114">Çıkış dosyaları olan varsayılan konumuna yazılır `bin/<configuration>/<target>`.</span><span class="sxs-lookup"><span data-stu-id="cf969-114">Output files are written into the default location, which is `bin/<configuration>/<target>`.</span></span> <span data-ttu-id="cf969-115">Örneğin, varsa bir `netcoreapp1.0` uygulama ve Çalıştır `dotnet run`, çıktı yerleştirilir `bin/Debug/netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="cf969-115">For example if you have a `netcoreapp1.0` application and you run `dotnet run`, the output is placed in `bin/Debug/netcoreapp1.0`.</span></span> <span data-ttu-id="cf969-116">Gerektiğinde dosyalarının üzerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="cf969-116">Files are overwritten as needed.</span></span> <span data-ttu-id="cf969-117">Geçici dosyalar yerleştirilir `obj` dizin.</span><span class="sxs-lookup"><span data-stu-id="cf969-117">Temporary files are placed in the `obj` directory.</span></span>

<span data-ttu-id="cf969-118">Projenin birden çok çerçeveyi belirtiyorsa, yürütme `dotnet run` sürece hatayla sonuçlanır `-f|--framework <FRAMEWORK>` seçeneği framework belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cf969-118">If the project specifies multiple frameworks, executing `dotnet run` results in an error unless the `-f|--framework <FRAMEWORK>` option is used to specify the framework.</span></span>

<span data-ttu-id="cf969-119">`dotnet run` Komutu derlemeler oluşturulan değil projeler bağlamında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cf969-119">The `dotnet run` command is used in the context of projects, not built assemblies.</span></span> <span data-ttu-id="cf969-120">Bunun yerine bir framework bağımlı uygulamayı DLL çalıştırmak çalışıyorsanız, kullanmalısınız [dotnet](dotnet.md) olmadan bir komutu.</span><span class="sxs-lookup"><span data-stu-id="cf969-120">If you're trying to run a framework-dependent application DLL instead, you must use [dotnet](dotnet.md) without a command.</span></span> <span data-ttu-id="cf969-121">Örneğin, çalıştırmak için `myapp.dll`, kullanın:</span><span class="sxs-lookup"><span data-stu-id="cf969-121">For example, to run `myapp.dll`, use:</span></span>

```
dotnet myapp.dll
```

<span data-ttu-id="cf969-122">Daha fazla bilgi için `dotnet` sürücüsü bkz [.NET Core komut satırı araçları (CLI)](index.md) konu.</span><span class="sxs-lookup"><span data-stu-id="cf969-122">For more information on the `dotnet` driver, see the [.NET Core Command Line Tools (CLI)](index.md) topic.</span></span>

<span data-ttu-id="cf969-123">Uygulamayı çalıştırmak için `dotnet run` komutu NuGet önbelleğinden paylaşılan çalışma zamanı dışında Uygulama bağımlılıklarını giderir.</span><span class="sxs-lookup"><span data-stu-id="cf969-123">In order to run the application, the `dotnet run` command resolves the dependencies of the application that are outside of the shared runtime from the NuGet cache.</span></span> <span data-ttu-id="cf969-124">Önbelleğe alınan bağımlılıkları kullandığından, onu kullanmak önerilmez `dotnet run` üretimde uygulamaları çalıştırmak için.</span><span class="sxs-lookup"><span data-stu-id="cf969-124">Because it uses cached dependencies, it's not recommended to use `dotnet run` to run applications in production.</span></span> <span data-ttu-id="cf969-125">Bunun yerine, [bir dağıtım oluşturmak](../deploying/index.md) kullanarak [ `dotnet publish` ](dotnet-publish.md) komut ve yayımlanan çıkış dağıtın.</span><span class="sxs-lookup"><span data-stu-id="cf969-125">Instead, [create a deployment](../deploying/index.md) using the [`dotnet publish`](dotnet-publish.md) command and deploy the published output.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a><span data-ttu-id="cf969-126">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="cf969-126">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="cf969-127">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="cf969-127">.NET Core 2.x</span></span>](#tab/netcore2x)

`--`

<span data-ttu-id="cf969-128">Bağımsız değişkenleri sınırlandırır `dotnet run` gelen çalıştırılan uygulama için bağımsız değişkenler.</span><span class="sxs-lookup"><span data-stu-id="cf969-128">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="cf969-129">Bu bir sonra tüm bağımsız değişkenler Çalıştırma uygulaması geçirilir.</span><span class="sxs-lookup"><span data-stu-id="cf969-129">All arguments after this one are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="cf969-130">Derleme yapılandırması tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cf969-130">Defines the build configuration.</span></span> <span data-ttu-id="cf969-131">Varsayılan değer `Debug` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="cf969-131">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="cf969-132">Derlemeler ve belirtilen kullanarak uygulamayı çalıştıran [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="cf969-132">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="cf969-133">Proje dosyasında framework belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="cf969-133">The framework must be specified in the project file.</span></span>

`--force`

<span data-ttu-id="cf969-134">Son geri yükleme başarılı olsa bile çözümlenmesi için tüm bağımlılıkları zorlar.</span><span class="sxs-lookup"><span data-stu-id="cf969-134">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="cf969-135">Bu silme ile eşdeğerdir *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="cf969-135">This is equivalent to deleting *project.assets.json*.</span></span>

`-h|--help`

<span data-ttu-id="cf969-136">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="cf969-136">Prints out a short help for the command.</span></span>

`--launch-profile <NAME>`

<span data-ttu-id="cf969-137">Başlatma adını profil (varsa) uygulama başlatılırken kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="cf969-137">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="cf969-138">Başlatma profilleri tanımlanmış *launchSettings.json* dosya ve genellikle adlı `Development`, `Staging` ve `Production`.</span><span class="sxs-lookup"><span data-stu-id="cf969-138">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging` and `Production`.</span></span> <span data-ttu-id="cf969-139">Daha fazla bilgi için bkz: [birden çok ortamlarıyla çalışma](/aspnet/core/fundamentals/environments).</span><span class="sxs-lookup"><span data-stu-id="cf969-139">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

`--no-build`

<span data-ttu-id="cf969-140">Çalıştırmadan önce projeyi derlemek değil.</span><span class="sxs-lookup"><span data-stu-id="cf969-140">Doesn't build the project before running.</span></span>

`--no-dependencies`

<span data-ttu-id="cf969-141">Proje Proje (P2P) başvuruları içeren bir proje geri yüklerken, kök proje ve başvuru geri yükler.</span><span class="sxs-lookup"><span data-stu-id="cf969-141">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--no-launch-profile`

<span data-ttu-id="cf969-142">Kullanma girişimi değil *launchSettings.json* uygulamayı yapılandırmak için.</span><span class="sxs-lookup"><span data-stu-id="cf969-142">Doesn't attempt to use *launchSettings.json* to configure the application.</span></span>

`--no-restore`

<span data-ttu-id="cf969-143">Örtük bir geri yükleme komutu çalıştırırken gerçekleştirmez.</span><span class="sxs-lookup"><span data-stu-id="cf969-143">Doesn't perform an implicit restore when running the command.</span></span>

`-p|--project <PATH>`

<span data-ttu-id="cf969-144">(Klasör adı veya tam yolu) çalıştırmak için proje dosyasının yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="cf969-144">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="cf969-145">Belirtilmezse, geçerli dizine varsayar.</span><span class="sxs-lookup"><span data-stu-id="cf969-145">It defaults to the current directory if not specified.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="cf969-146">Paketler için geri yüklemek için hedef çalışma zamanı belirtir.</span><span class="sxs-lookup"><span data-stu-id="cf969-146">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="cf969-147">Çalışma zamanı tanımlayıcıları (RID) bir listesi için bkz: [RID katalog](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="cf969-147">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="cf969-148">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="cf969-148">.NET Core 1.x</span></span>](#tab/netcore1x)

`--`

<span data-ttu-id="cf969-149">Bağımsız değişkenleri sınırlandırır `dotnet run` gelen çalıştırılan uygulama için bağımsız değişkenler.</span><span class="sxs-lookup"><span data-stu-id="cf969-149">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="cf969-150">Bu bir sonra tüm bağımsız değişkenler Çalıştırma uygulaması geçirilir.</span><span class="sxs-lookup"><span data-stu-id="cf969-150">All arguments after this one are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="cf969-151">Derleme yapılandırması tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cf969-151">Defines the build configuration.</span></span> <span data-ttu-id="cf969-152">Varsayılan değer `Debug` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="cf969-152">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="cf969-153">Derlemeler ve belirtilen kullanarak uygulamayı çalıştıran [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="cf969-153">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="cf969-154">Proje dosyasında framework belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="cf969-154">The framework must be specified in the project file.</span></span>

`-h|--help`

<span data-ttu-id="cf969-155">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="cf969-155">Prints out a short help for the command.</span></span>

`-p|--project <PATH/PROJECT.csproj>`

<span data-ttu-id="cf969-156">Proje dosyasının adını ve yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="cf969-156">Specifies the path and name of the project file.</span></span> <span data-ttu-id="cf969-157">(NOTA bakın.) Belirtilmezse, geçerli dizine varsayar.</span><span class="sxs-lookup"><span data-stu-id="cf969-157">(See the NOTE.) It defaults to the current directory if not specified.</span></span>

> [!NOTE]
> <span data-ttu-id="cf969-158">Proje dosyası ile adını ve yolunu kullanın `-p|--project` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="cf969-158">Use the path and name of the project file with the `-p|--project` option.</span></span> <span data-ttu-id="cf969-159">.NET Core SDK ile bir klasör yolu sağlayan CLI'teki bir gerileme engeller 1.x.</span><span class="sxs-lookup"><span data-stu-id="cf969-159">A regression in the CLI prevents providing a folder path with .NET Core SDK 1.x.</span></span> <span data-ttu-id="cf969-160">Bu sorun hakkında daha fazla bilgi için bkz: [-p, çalıştırmak dotnet değil (dotnet/CLI #5992) proje Başlat](https://github.com/dotnet/cli/issues/5992).</span><span class="sxs-lookup"><span data-stu-id="cf969-160">For more information about this issue, see [dotnet run -p, can not start a project (dotnet/cli #5992)](https://github.com/dotnet/cli/issues/5992).</span></span>

---

## <a name="examples"></a><span data-ttu-id="cf969-161">Örnekler</span><span class="sxs-lookup"><span data-stu-id="cf969-161">Examples</span></span>

<span data-ttu-id="cf969-162">Proje geçerli dizinde çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="cf969-162">Run the project in the current directory:</span></span>

`dotnet run`

<span data-ttu-id="cf969-163">Belirtilen proje çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="cf969-163">Run the specified project:</span></span>

`dotnet run --project /projects/proj1/proj1.csproj`

<span data-ttu-id="cf969-164">Geçerli dizinde projeyi çalıştırın ( `--help` bağımsız değişkeni Bu örnekte geçirilir uygulamaya beri `--` bağımsız değişkeninin değeri kullanılır):</span><span class="sxs-lookup"><span data-stu-id="cf969-164">Run the project in the current directory (the `--help` argument in this example is passed to the application, since the `--` argument is used):</span></span>

`dotnet run --configuration Release -- --help`

<span data-ttu-id="cf969-165">Bağımlılıklar ve geçerli dizinde proje için araçları çıkış ve projeyi çalıştırın en az gösteren yalnızca geri yükleme: (.NET Core SDK 2.0 ve sonraki sürümler):</span><span class="sxs-lookup"><span data-stu-id="cf969-165">Restore dependencies and tools for the project in the current directory only showing minimal output and then run the project: (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet run --verbosity m`