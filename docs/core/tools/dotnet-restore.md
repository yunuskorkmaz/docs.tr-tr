---
title: DotNet restore komutu - .NET Core CLI
description: "Bağımlılıklar ve projeye özgü araçları dotnet restore komutu ile geri yüklemeyi öğrenin."
keywords: dotnet-restore, CLI, CLI command, .NET Core
author: mairaw
ms.author: mairaw
ms.date: 11/30/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 50e8d5c335386c41e36a490263a4f4ebd2bd39ba
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2018
---
# <a name="dotnet-restore"></a><span data-ttu-id="9997b-104">DotNet geri yükleme</span><span class="sxs-lookup"><span data-stu-id="9997b-104">dotnet restore</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="9997b-105">Ad</span><span class="sxs-lookup"><span data-stu-id="9997b-105">Name</span></span>

<span data-ttu-id="9997b-106">`dotnet restore` -Bir projenin araçları ve bağımlılıklar geri yükler.</span><span class="sxs-lookup"><span data-stu-id="9997b-106">`dotnet restore` - Restores the dependencies and tools of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="9997b-107">Özet</span><span class="sxs-lookup"><span data-stu-id="9997b-107">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="9997b-108">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="9997b-108">.NET Core 2.x</span></span>](#tab/netcore2x)

```
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--force] [--ignore-failed-sources] [--no-cache] [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="9997b-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="9997b-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--ignore-failed-sources] [--no-cache] [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="9997b-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9997b-110">Description</span></span>

<span data-ttu-id="9997b-111">`dotnet restore` Komutu proje dosyasında belirtilen projeye özel araçlar yanı sıra bağımlılıkları geri yüklemek için NuGet kullanır.</span><span class="sxs-lookup"><span data-stu-id="9997b-111">The `dotnet restore` command uses NuGet to restore dependencies as well as project-specific tools that are specified in the project file.</span></span> <span data-ttu-id="9997b-112">Varsayılan olarak, bağımlılıklar ve araçları geri paralel olarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="9997b-112">By default, the restoration of dependencies and tools are performed in parallel.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="9997b-113">Bağımlılıkları geri yüklemek için NuGet paketleri bulunduğu akışları gerekir.</span><span class="sxs-lookup"><span data-stu-id="9997b-113">In order to restore the dependencies, NuGet needs the feeds where the packages are located.</span></span> <span data-ttu-id="9997b-114">Akışları aracılığıyla genellikle sağlanan *NuGet.config* yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="9997b-114">Feeds are usually provided via the *NuGet.config* configuration file.</span></span> <span data-ttu-id="9997b-115">CLI araçlarını yüklendiğinde varsayılan yapılandırma dosyası sağlanır.</span><span class="sxs-lookup"><span data-stu-id="9997b-115">A default configuration file is provided when the CLI tools are installed.</span></span> <span data-ttu-id="9997b-116">Kendi oluşturarak ek akışları belirttiğiniz *NuGet.config* proje dizininde dosya.</span><span class="sxs-lookup"><span data-stu-id="9997b-116">You specify additional feeds by creating your own *NuGet.config* file in the project directory.</span></span> <span data-ttu-id="9997b-117">Ayrıca, bir komut isteminde çağrı başına ek akışları belirtin.</span><span class="sxs-lookup"><span data-stu-id="9997b-117">You also specify additional feeds per invocation at a command prompt.</span></span>

<span data-ttu-id="9997b-118">Bağımlılıklar için geri yüklenen paketler geri yükleme işlemini kullanarak sırasında yerleştirildiği belirtin `--packages` bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="9997b-118">For dependencies, you specify where the restored packages are placed during the restore operation using the `--packages` argument.</span></span> <span data-ttu-id="9997b-119">Belirtilmezse, varsayılan NuGet paketi önbelleği, içinde bulunan kullanılıp kullanılmadığını `.nuget/packages` tüm işletim sistemlerinde kullanıcının giriş dizini, dizin (örneğin, */home/kullanıcı1* Linux'ta veya *C:\Users\user1*  Windows'da).</span><span class="sxs-lookup"><span data-stu-id="9997b-119">If not specified, the default NuGet package cache is used, which is found in the `.nuget/packages` directory in the user's home directory on all operating systems (for example, */home/user1* on Linux or *C:\Users\user1* on Windows).</span></span>

<span data-ttu-id="9997b-120">Projeye özgü araçları için `dotnet restore` önce aracı paketlenmiştir ve proje dosyasında belirtildiği gibi aracın bağımlılıkları geri sürdürüleceği paketini yükler.</span><span class="sxs-lookup"><span data-stu-id="9997b-120">For project-specific tooling, `dotnet restore` first restores the package in which the tool is packed, and then proceeds to restore the tool's dependencies as specified in its project file.</span></span>

<span data-ttu-id="9997b-121">Davranışını `dotnet restore` komut ayarlarında bazıları tarafından etkilenir *Nuget.Config* varsa dosya.</span><span class="sxs-lookup"><span data-stu-id="9997b-121">The behavior of the `dotnet restore` command is affected by some of the settings in the *Nuget.Config* file, if present.</span></span> <span data-ttu-id="9997b-122">Örneğin, ayarlama `globalPackagesFolder` içinde *NuGet.Config* belirtilen klasörde geri yüklenen NuGet paketleri yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="9997b-122">For example, setting the `globalPackagesFolder` in *NuGet.Config* places the restored NuGet packages in the specified folder.</span></span> <span data-ttu-id="9997b-123">Bu belirtme alternatiftir `--packages` seçeneği `dotnet restore` komutu.</span><span class="sxs-lookup"><span data-stu-id="9997b-123">This is an alternative to specifying the `--packages` option on the `dotnet restore` command.</span></span> <span data-ttu-id="9997b-124">Daha fazla bilgi için bkz: [NuGet.Config başvuru](/nuget/schema/nuget-config-file).</span><span class="sxs-lookup"><span data-stu-id="9997b-124">For more information, see the [NuGet.Config reference](/nuget/schema/nuget-config-file).</span></span>

## <a name="implicit-dotnet-restore"></a><span data-ttu-id="9997b-125">Örtük `dotnet restore`</span><span class="sxs-lookup"><span data-stu-id="9997b-125">Implicit `dotnet restore`</span></span>

<span data-ttu-id="9997b-126">.NET Core 2. 0 ile başlayan `dotnet restore` aşağıdaki komutları kesilirken gerekirse örtük olarak çalıştırılır:</span><span class="sxs-lookup"><span data-stu-id="9997b-126">Starting with .NET Core 2.0, `dotnet restore` is run implicitly if necessary when you issue the following commands:</span></span>

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

<span data-ttu-id="9997b-127">Çoğu durumda, artık açıkça kullanmanız gerekebilir `dotnet restore` komutu.</span><span class="sxs-lookup"><span data-stu-id="9997b-127">In most cases, you no longer need to explicitly use the `dotnet restore` command.</span></span> 

<span data-ttu-id="9997b-128">Bazı durumlarda, kullanışsız için `dotnet restore` örtük olarak çalıştırmak için.</span><span class="sxs-lookup"><span data-stu-id="9997b-128">In some cases, it is inconvenient for `dotnet restore` to run implicitly.</span></span> <span data-ttu-id="9997b-129">Örneğin, yapı sistemleri gibi bazı otomatik sistemleri çağırmanız gerekir `dotnet restore` açıkça ağ kullanımını kontrol edebilirsiniz böylece geri yükleme meydana geldiğinde denetlemek için.</span><span class="sxs-lookup"><span data-stu-id="9997b-129">For example, some automated systems, such as build systems, need to call `dotnet restore` explicitly to control when the restore occurs so that they can control network usage.</span></span> <span data-ttu-id="9997b-130">Önlemek için `dotnet restore` kullanabileceğiniz örtük olarak çalıştırılmasını `--no-restore` örtük geri yükleme devre dışı bırakmak için aşağıdaki komutlardan birini anahtarıyla.</span><span class="sxs-lookup"><span data-stu-id="9997b-130">To prevent `dotnet restore` from running implicitly, you can use the `--no-restore` switch with any of these commands to disable implicit restore.</span></span>

## <a name="arguments"></a><span data-ttu-id="9997b-131">Arguments</span><span class="sxs-lookup"><span data-stu-id="9997b-131">Arguments</span></span>

`ROOT`

<span data-ttu-id="9997b-132">Proje dosyasını geri yüklemek için isteğe bağlı bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="9997b-132">Optional path to the project file to restore.</span></span>

## <a name="options"></a><span data-ttu-id="9997b-133">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="9997b-133">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="9997b-134">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="9997b-134">.NET Core 2.x</span></span>](#tab/netcore2x)

`--configfile <FILE>`

<span data-ttu-id="9997b-135">NuGet yapılandırma dosyası (*NuGet.config*) geri yükleme işlemi için kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="9997b-135">The NuGet configuration file (*NuGet.config*) to use for the restore operation.</span></span>

`--disable-parallel`

<span data-ttu-id="9997b-136">Paralel olarak birden çok proje geri yükleme devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="9997b-136">Disables restoring multiple projects in parallel.</span></span>

`--force`

<span data-ttu-id="9997b-137">Son geri yükleme başarılı olsa bile çözümlenmesi için tüm bağımlılıkları zorlar.</span><span class="sxs-lookup"><span data-stu-id="9997b-137">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="9997b-138">Bu silme ile eşdeğerdir *project.assets.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="9997b-138">This is equivalent to deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="9997b-139">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="9997b-139">Prints out a short help for the command.</span></span>

`--ignore-failed-sources`

<span data-ttu-id="9997b-140">Paket sürümü gereksinimini toplantı varsa yalnızca başarısız kaynakları hakkında uyarır.</span><span class="sxs-lookup"><span data-stu-id="9997b-140">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

`--no-cache`

<span data-ttu-id="9997b-141">Paketler ve HTTP isteklerini önbelleğe almaz belirtir.</span><span class="sxs-lookup"><span data-stu-id="9997b-141">Specifies to not cache packages and HTTP requests.</span></span>

`--no-dependencies`

<span data-ttu-id="9997b-142">Proje Proje (P2P) başvuruları içeren bir proje geri yüklerken, kök proje ve başvuru geri yükler.</span><span class="sxs-lookup"><span data-stu-id="9997b-142">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--packages <PACKAGES_DIRECTORY>`

<span data-ttu-id="9997b-143">Geri yüklenen paketler dizinini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9997b-143">Specifies the directory for restored packages.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="9997b-144">Paket geri yüklemesi için bir çalışma zamanı belirtir.</span><span class="sxs-lookup"><span data-stu-id="9997b-144">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="9997b-145">Bu çalışma zamanları açıkça listelenen paketlerini geri yüklemek için kullanılan `<RuntimeIdentifiers>` içinde etiketi *.csproj* dosya.</span><span class="sxs-lookup"><span data-stu-id="9997b-145">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="9997b-146">Çalışma zamanı tanımlayıcıları (RID) bir listesi için bkz: [RID katalog](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="9997b-146">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="9997b-147">Bu seçeneği birden çok kez belirterek birden fazla RID sağlar.</span><span class="sxs-lookup"><span data-stu-id="9997b-147">Provide multiple RIDs by specifying this option multiple times.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="9997b-148">Geri yükleme işlemi sırasında kullanmak için NuGet paket kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9997b-148">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="9997b-149">Bu belirtilen kaynakları tüm geçersiz kılmaları *NuGet.config* dosyaları.</span><span class="sxs-lookup"><span data-stu-id="9997b-149">This overrides all of the sources specified in the *NuGet.config* files.</span></span> <span data-ttu-id="9997b-150">Bu seçeneği birden çok kez belirterek birden çok kaynak sağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="9997b-150">Multiple sources can be provided by specifying this option multiple times.</span></span>

`--verbosity <LEVEL>`

<span data-ttu-id="9997b-151">Komutun ayrıntı düzeyi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9997b-151">Sets the verbosity level of the command.</span></span> <span data-ttu-id="9997b-152">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="9997b-152">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="9997b-153">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="9997b-153">.NET Core 1.x</span></span>](#tab/netcore1x)

`--configfile <FILE>`

<span data-ttu-id="9997b-154">NuGet yapılandırma dosyası (*NuGet.config*) geri yükleme işlemi için kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="9997b-154">The NuGet configuration file (*NuGet.config*) to use for the restore operation.</span></span>

`--disable-parallel`

<span data-ttu-id="9997b-155">Paralel olarak birden çok proje geri yükleme devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="9997b-155">Disables restoring multiple projects in parallel.</span></span>

`-h|--help`

<span data-ttu-id="9997b-156">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="9997b-156">Prints out a short help for the command.</span></span>

`--ignore-failed-sources`

<span data-ttu-id="9997b-157">Paket sürümü gereksinimini toplantı varsa yalnızca başarısız kaynakları hakkında uyarır.</span><span class="sxs-lookup"><span data-stu-id="9997b-157">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

`--no-cache`

<span data-ttu-id="9997b-158">Paketler ve HTTP isteklerini önbelleğe almaz belirtir.</span><span class="sxs-lookup"><span data-stu-id="9997b-158">Specifies to not cache packages and HTTP requests.</span></span>

`--no-dependencies`

<span data-ttu-id="9997b-159">Proje Proje (P2P) başvuruları içeren bir proje geri yüklerken, kök proje ve başvuru geri yükler.</span><span class="sxs-lookup"><span data-stu-id="9997b-159">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--packages <PACKAGES_DIRECTORY>`

<span data-ttu-id="9997b-160">Geri yüklenen paketler dizinini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9997b-160">Specifies the directory for restored packages.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="9997b-161">Paket geri yüklemesi için bir çalışma zamanı belirtir.</span><span class="sxs-lookup"><span data-stu-id="9997b-161">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="9997b-162">Bu çalışma zamanları açıkça listelenen paketlerini geri yüklemek için kullanılan `<RuntimeIdentifiers>` içinde etiketi *.csproj* dosya.</span><span class="sxs-lookup"><span data-stu-id="9997b-162">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="9997b-163">Çalışma zamanı tanımlayıcıları (RID) bir listesi için bkz: [RID katalog](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="9997b-163">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="9997b-164">Bu seçeneği birden çok kez belirterek birden fazla RID sağlar.</span><span class="sxs-lookup"><span data-stu-id="9997b-164">Provide multiple RIDs by specifying this option multiple times.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="9997b-165">Geri yükleme işlemi sırasında kullanmak için NuGet paket kaynağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9997b-165">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="9997b-166">Bu belirtilen kaynakları tüm geçersiz kılmaları *NuGet.config* dosyaları.</span><span class="sxs-lookup"><span data-stu-id="9997b-166">This overrides all of the sources specified in the *NuGet.config* files.</span></span> <span data-ttu-id="9997b-167">Bu seçeneği birden çok kez belirterek birden çok kaynak sağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="9997b-167">Multiple sources can be provided by specifying this option multiple times.</span></span>

`--verbosity <LEVEL>`

<span data-ttu-id="9997b-168">Komutun ayrıntı düzeyi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9997b-168">Sets the verbosity level of the command.</span></span> <span data-ttu-id="9997b-169">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="9997b-169">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="9997b-170">Örnekler</span><span class="sxs-lookup"><span data-stu-id="9997b-170">Examples</span></span>

<span data-ttu-id="9997b-171">Bağımlılıklar ve geçerli dizinde proje için araçları geri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="9997b-171">Restore dependencies and tools for the project in the current directory:</span></span>

`dotnet restore`

<span data-ttu-id="9997b-172">Bağımlılıklar ve araçları için geri `app1` proje verilen yolda bulunamadı:</span><span class="sxs-lookup"><span data-stu-id="9997b-172">Restore dependencies and tools for the `app1` project found in the given path:</span></span>

`dotnet restore ~/projects/app1/app1.csproj`

<span data-ttu-id="9997b-173">Kaynak olarak sağlanan dosya yolunu kullanarak geçerli dizinde projesi için Araçlar ve bağımlılıklar geri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="9997b-173">Restore the dependencies and tools for the project in the current directory using the file path provided as the source:</span></span>

`dotnet restore -s c:\packages\mypackages`

<span data-ttu-id="9997b-174">Kaynakları olarak sağlanan iki dosya yolları kullanarak geçerli dizinde projesi için Araçlar ve bağımlılıklar geri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="9997b-174">Restore the dependencies and tools for the project in the current directory using the two file paths provided as sources:</span></span>

`dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages`

<span data-ttu-id="9997b-175">Bağımlılıklar ve geçerli dizin ve programlarını yalnızca en az çıkış projede için araçları geri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="9997b-175">Restore dependencies and tools for the project in the current directory and shows only minimal output:</span></span>

`dotnet restore --verbosity minimal`
