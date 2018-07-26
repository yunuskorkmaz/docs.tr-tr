---
title: DotNet restore komutu - .NET Core CLI
description: Bağımlılıklar ve projeye özgü araçları dotnet restore komutu ile geri yüklemeyi öğreneceksiniz.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 0eaab1aa1bc52bd5b3c51a6ed2dd7a59c35a4aa5
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37960602"
---
# <a name="dotnet-restore"></a><span data-ttu-id="b9ae2-103">DotNet restore</span><span class="sxs-lookup"><span data-stu-id="b9ae2-103">dotnet restore</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="b9ae2-104">Ad</span><span class="sxs-lookup"><span data-stu-id="b9ae2-104">Name</span></span>

<span data-ttu-id="b9ae2-105">`dotnet restore` -Bir projenin Araçlar ve bağımlılıkları yükler.</span><span class="sxs-lookup"><span data-stu-id="b9ae2-105">`dotnet restore` - Restores the dependencies and tools of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b9ae2-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="b9ae2-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="b9ae2-107">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="b9ae2-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--force] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="b9ae2-108">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="b9ae2-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="b9ae2-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b9ae2-109">Description</span></span>

<span data-ttu-id="b9ae2-110">`dotnet restore` Komutu, proje dosyasında belirtilen projeye özgü araçları yanı sıra bağımlılıkları geri yüklemek için NuGet kullanır.</span><span class="sxs-lookup"><span data-stu-id="b9ae2-110">The `dotnet restore` command uses NuGet to restore dependencies as well as project-specific tools that are specified in the project file.</span></span> <span data-ttu-id="b9ae2-111">Varsayılan olarak, Araçlar ile bağımlılıkları ve geri yükleme işlemi paralel olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="b9ae2-111">By default, the restoration of dependencies and tools are executed in parallel.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="b9ae2-112">Bağımlılıkları geri yüklemek için NuGet paketlerinin yer aldığı akışları gerekir.</span><span class="sxs-lookup"><span data-stu-id="b9ae2-112">To restore the dependencies, NuGet needs the feeds where the packages are located.</span></span> <span data-ttu-id="b9ae2-113">Akışları aracılığıyla genellikle sağlanan *NuGet.config* yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="b9ae2-113">Feeds are usually provided via the *NuGet.config* configuration file.</span></span> <span data-ttu-id="b9ae2-114">CLI araçları yüklü olduğunda varsayılan yapılandırma dosyası sağlanır.</span><span class="sxs-lookup"><span data-stu-id="b9ae2-114">A default configuration file is provided when the CLI tools are installed.</span></span> <span data-ttu-id="b9ae2-115">Kendi oluşturarak ek akışları belirttiğiniz *NuGet.config* dosya proje dizininde.</span><span class="sxs-lookup"><span data-stu-id="b9ae2-115">You specify additional feeds by creating your own *NuGet.config* file in the project directory.</span></span> <span data-ttu-id="b9ae2-116">Bir komut isteminde çağrı başına ek akışları de belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b9ae2-116">You also specify additional feeds per invocation at a command prompt.</span></span>

<span data-ttu-id="b9ae2-117">Bağımlılıklar için geri yüklenen paketler geri yükleme kullanarak işlemi sırasında yerleştirildiği belirtin `--packages` bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="b9ae2-117">For dependencies, you specify where the restored packages are placed during the restore operation using the `--packages` argument.</span></span> <span data-ttu-id="b9ae2-118">Belirtilmezse, varsayılan NuGet paket önbelleğini, içinde geçtiği yerin kullanılıp kullanılmadığını `.nuget/packages` dizini ile tüm işletim sistemlerinde kullanıcının ana dizini.</span><span class="sxs-lookup"><span data-stu-id="b9ae2-118">If not specified, the default NuGet package cache is used, which is found in the `.nuget/packages` directory in the user's home directory on all operating systems.</span></span> <span data-ttu-id="b9ae2-119">Örneğin, */home/user1* Linux üzerinde veya *C:\Users\user1* Windows üzerinde.</span><span class="sxs-lookup"><span data-stu-id="b9ae2-119">For example, */home/user1* on Linux or *C:\Users\user1* on Windows.</span></span>

<span data-ttu-id="b9ae2-120">Projeye özgü araçları için `dotnet restore` öncelikle hangi aracın iyileştirmesiyle doludur ve kendi proje dosyasında belirtilen Aracı'nın bağımlılıkları geri yüklemek için devam eder paket geri yükler.</span><span class="sxs-lookup"><span data-stu-id="b9ae2-120">For project-specific tooling, `dotnet restore` first restores the package in which the tool is packed, and then proceeds to restore the tool's dependencies as specified in its project file.</span></span>

<span data-ttu-id="b9ae2-121">Davranışını `dotnet restore` komut bazı ayarlar tarafından etkilendi *Nuget.Config* varsa, dosya.</span><span class="sxs-lookup"><span data-stu-id="b9ae2-121">The behavior of the `dotnet restore` command is affected by some of the settings in the *Nuget.Config* file, if present.</span></span> <span data-ttu-id="b9ae2-122">Örneğin, ayarlamak `globalPackagesFolder` içinde *NuGet.Config* belirtilen klasörde NuGet paketlerini geri yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="b9ae2-122">For example, setting the `globalPackagesFolder` in *NuGet.Config* places the restored NuGet packages in the specified folder.</span></span> <span data-ttu-id="b9ae2-123">Bu belirten bir alternatifidir `--packages` seçeneğini `dotnet restore` komutu.</span><span class="sxs-lookup"><span data-stu-id="b9ae2-123">This is an alternative to specifying the `--packages` option on the `dotnet restore` command.</span></span> <span data-ttu-id="b9ae2-124">Daha fazla bilgi için [NuGet.Config başvuru](/nuget/schema/nuget-config-file).</span><span class="sxs-lookup"><span data-stu-id="b9ae2-124">For more information, see the [NuGet.Config reference](/nuget/schema/nuget-config-file).</span></span>

## <a name="implicit-dotnet-restore"></a><span data-ttu-id="b9ae2-125">Örtük `dotnet restore`</span><span class="sxs-lookup"><span data-stu-id="b9ae2-125">Implicit `dotnet restore`</span></span>

<span data-ttu-id="b9ae2-126">.NET Core 2.0 ile başlayarak `dotnet restore` aşağıdaki komutları gönderdiğinizde gerekirse örtük olarak çalıştırılan:</span><span class="sxs-lookup"><span data-stu-id="b9ae2-126">Starting with .NET Core 2.0, `dotnet restore` is run implicitly if necessary when you issue the following commands:</span></span>

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

<span data-ttu-id="b9ae2-127">Çoğu durumda, artık açıkça kullanmanız gerekir `dotnet restore` komutu.</span><span class="sxs-lookup"><span data-stu-id="b9ae2-127">In most cases, you no longer need to explicitly use the `dotnet restore` command.</span></span>

<span data-ttu-id="b9ae2-128">Bazı durumlarda, çalıştırılacak kullanışsız olabilir `dotnet restore` örtük olarak.</span><span class="sxs-lookup"><span data-stu-id="b9ae2-128">Sometimes, it might be inconvenient to run `dotnet restore` implicitly.</span></span> <span data-ttu-id="b9ae2-129">Örneğin, yapı sistemi gibi bazı otomatik sistemler çağırmanız gerekir `dotnet restore` açıkça ağ kullanımını kontrol edebilir, böylece geri yükleme ne zaman gerçekleştiğini denetlemek için.</span><span class="sxs-lookup"><span data-stu-id="b9ae2-129">For example, some automated systems, such as build systems, need to call `dotnet restore` explicitly to control when the restore occurs so that they can control network usage.</span></span> <span data-ttu-id="b9ae2-130">Önlemek için `dotnet restore` kullanabileceğiniz örtük olarak çalıştırılmasının `--no-restore` örtük geri yükleme devre dışı bırakmak için aşağıdaki komutlardan birini bayrağıyla.</span><span class="sxs-lookup"><span data-stu-id="b9ae2-130">To prevent `dotnet restore` from running implicitly, you can use the `--no-restore` flag with any of these commands to disable implicit restore.</span></span>

## <a name="arguments"></a><span data-ttu-id="b9ae2-131">Arguments</span><span class="sxs-lookup"><span data-stu-id="b9ae2-131">Arguments</span></span>

`ROOT`

<span data-ttu-id="b9ae2-132">İsteğe bağlı geri yüklemek için proje dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="b9ae2-132">Optional path to the project file to restore.</span></span>

## <a name="options"></a><span data-ttu-id="b9ae2-133">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="b9ae2-133">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="b9ae2-134">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="b9ae2-134">.NET Core 2.x</span></span>](#tab/netcore2x)

`--configfile <FILE>`

<span data-ttu-id="b9ae2-135">NuGet yapılandırma dosyası (*NuGet.config*) geri yükleme işlemi için kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="b9ae2-135">The NuGet configuration file (*NuGet.config*) to use for the restore operation.</span></span>

`--disable-parallel`

<span data-ttu-id="b9ae2-136">Paralel olarak birden çok proje geri yükleme devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="b9ae2-136">Disables restoring multiple projects in parallel.</span></span>

`--force`

<span data-ttu-id="b9ae2-137">Son geri yükleme başarılı olduysa bile çözülmesi için tüm bağımlılıkların zorlar.</span><span class="sxs-lookup"><span data-stu-id="b9ae2-137">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="b9ae2-138">Bu bayrak belirten aynıdır silme *project.assets.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="b9ae2-138">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="b9ae2-139">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="b9ae2-139">Prints out a short help for the command.</span></span>

`--ignore-failed-sources`

<span data-ttu-id="b9ae2-140">Yalnızca sürüm gereksinimi Karşılama paketleri varsa başarısız kaynakları hakkında uyar.</span><span class="sxs-lookup"><span data-stu-id="b9ae2-140">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

`--no-cache`

<span data-ttu-id="b9ae2-141">Paketler ve HTTP isteklerini önbelleğe belirtir.</span><span class="sxs-lookup"><span data-stu-id="b9ae2-141">Specifies to not cache packages and HTTP requests.</span></span>

`--no-dependencies`

<span data-ttu-id="b9ae2-142">Projeden projeye (P2P) başvurular içeren bir proje geri yüklerken, kök proje ve başvuruları geri yükler.</span><span class="sxs-lookup"><span data-stu-id="b9ae2-142">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--packages <PACKAGES_DIRECTORY>`

<span data-ttu-id="b9ae2-143">Geri yüklenen paketler için dizini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b9ae2-143">Specifies the directory for restored packages.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="b9ae2-144">Paket geri yükleme için bir çalışma zamanı belirtir.</span><span class="sxs-lookup"><span data-stu-id="b9ae2-144">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="b9ae2-145">Bu açıkça listelenen çalışma zamanları için paketler geri yüklemek için kullanılan `<RuntimeIdentifiers>` içindeki *.csproj* dosya.</span><span class="sxs-lookup"><span data-stu-id="b9ae2-145">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="b9ae2-146">Çalışma zamanı tanımlayıcılarının (RID'ler) bir listesi için bkz. [RID Kataloğu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="b9ae2-146">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="b9ae2-147">Bu seçeneği birden çok kez belirterek, birden fazla RID sağlar.</span><span class="sxs-lookup"><span data-stu-id="b9ae2-147">Provide multiple RIDs by specifying this option multiple times.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="b9ae2-148">Geri yükleme işlemi sırasında kullanılacak bir NuGet paket kaynağı belirtir.</span><span class="sxs-lookup"><span data-stu-id="b9ae2-148">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="b9ae2-149">Bu ayar tüm kaynakları belirtilen geçersiz kılmaları *NuGet.config* dosyaları.</span><span class="sxs-lookup"><span data-stu-id="b9ae2-149">This setting overrides all of the sources specified in the *NuGet.config* files.</span></span> <span data-ttu-id="b9ae2-150">Bu seçeneği birden çok kez belirterek, birden çok kaynaktan sağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="b9ae2-150">Multiple sources can be provided by specifying this option multiple times.</span></span>

`--verbosity <LEVEL>`

<span data-ttu-id="b9ae2-151">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b9ae2-151">Sets the verbosity level of the command.</span></span> <span data-ttu-id="b9ae2-152">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="b9ae2-152">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="b9ae2-153">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="b9ae2-153">.NET Core 1.x</span></span>](#tab/netcore1x)

`--configfile <FILE>`

<span data-ttu-id="b9ae2-154">NuGet yapılandırma dosyası (*NuGet.config*) geri yükleme işlemi için kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="b9ae2-154">The NuGet configuration file (*NuGet.config*) to use for the restore operation.</span></span>

`--disable-parallel`

<span data-ttu-id="b9ae2-155">Paralel olarak birden çok proje geri yükleme devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="b9ae2-155">Disables restoring multiple projects in parallel.</span></span>

`-h|--help`

<span data-ttu-id="b9ae2-156">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="b9ae2-156">Prints out a short help for the command.</span></span>

`--ignore-failed-sources`

<span data-ttu-id="b9ae2-157">Yalnızca sürüm gereksinimi Karşılama paketleri varsa başarısız kaynakları hakkında uyar.</span><span class="sxs-lookup"><span data-stu-id="b9ae2-157">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

`--no-cache`

<span data-ttu-id="b9ae2-158">Paketler ve HTTP isteklerini önbelleğe belirtir.</span><span class="sxs-lookup"><span data-stu-id="b9ae2-158">Specifies to not cache packages and HTTP requests.</span></span>

`--no-dependencies`

<span data-ttu-id="b9ae2-159">Projeden projeye (P2P) başvurular içeren bir proje geri yüklerken, kök proje ve başvuruları geri yükler.</span><span class="sxs-lookup"><span data-stu-id="b9ae2-159">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--packages <PACKAGES_DIRECTORY>`

<span data-ttu-id="b9ae2-160">Geri yüklenen paketler için dizini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b9ae2-160">Specifies the directory for restored packages.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="b9ae2-161">Paket geri yükleme için bir çalışma zamanı belirtir.</span><span class="sxs-lookup"><span data-stu-id="b9ae2-161">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="b9ae2-162">Bu açıkça listelenen çalışma zamanları için paketler geri yüklemek için kullanılan `<RuntimeIdentifiers>` içindeki *.csproj* dosya.</span><span class="sxs-lookup"><span data-stu-id="b9ae2-162">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="b9ae2-163">Çalışma zamanı tanımlayıcılarının (RID'ler) bir listesi için bkz. [RID Kataloğu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="b9ae2-163">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="b9ae2-164">Bu seçeneği birden çok kez belirterek, birden fazla RID sağlar.</span><span class="sxs-lookup"><span data-stu-id="b9ae2-164">Provide multiple RIDs by specifying this option multiple times.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="b9ae2-165">Geri yükleme işlemi sırasında kullanılacak bir NuGet paket kaynağı belirtir.</span><span class="sxs-lookup"><span data-stu-id="b9ae2-165">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="b9ae2-166">Bu kaynakları belirtilen tüm geçersiz kılmaları *NuGet.config* dosyaları.</span><span class="sxs-lookup"><span data-stu-id="b9ae2-166">This overrides all of the sources specified in the *NuGet.config* files.</span></span> <span data-ttu-id="b9ae2-167">Bu seçeneği birden çok kez belirterek, birden çok kaynaktan sağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="b9ae2-167">Multiple sources can be provided by specifying this option multiple times.</span></span>

`--verbosity <LEVEL>`

<span data-ttu-id="b9ae2-168">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b9ae2-168">Sets the verbosity level of the command.</span></span> <span data-ttu-id="b9ae2-169">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="b9ae2-169">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="b9ae2-170">Örnekler</span><span class="sxs-lookup"><span data-stu-id="b9ae2-170">Examples</span></span>

<span data-ttu-id="b9ae2-171">Bağımlılıklar ve geçerli dizinde proje için araçları geri yükleme:</span><span class="sxs-lookup"><span data-stu-id="b9ae2-171">Restore dependencies and tools for the project in the current directory:</span></span>

`dotnet restore`

<span data-ttu-id="b9ae2-172">Bağımlılıklar ve araçlar için geri `app1` proje verilen yolda bulunamadı:</span><span class="sxs-lookup"><span data-stu-id="b9ae2-172">Restore dependencies and tools for the `app1` project found in the given path:</span></span>

`dotnet restore ~/projects/app1/app1.csproj`

<span data-ttu-id="b9ae2-173">Kaynak olarak sağlanan dosya yolunu kullanarak geçerli dizinde proje için Araçlar ve bağımlılıklar geri yükleme:</span><span class="sxs-lookup"><span data-stu-id="b9ae2-173">Restore the dependencies and tools for the project in the current directory using the file path provided as the source:</span></span>

`dotnet restore -s c:\packages\mypackages`

<span data-ttu-id="b9ae2-174">Kaynakları olarak sağlanan iki dosya yolları kullanarak geçerli dizinde proje için Araçlar ve bağımlılıklar geri yükleme:</span><span class="sxs-lookup"><span data-stu-id="b9ae2-174">Restore the dependencies and tools for the project in the current directory using the two file paths provided as sources:</span></span>

`dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages`

<span data-ttu-id="b9ae2-175">Bağımlılıklar ve araçlar için geçerli dizin ve programlarını yalnızca en az çıktı projede geri yükleme:</span><span class="sxs-lookup"><span data-stu-id="b9ae2-175">Restore dependencies and tools for the project in the current directory and shows only minimal output:</span></span>

`dotnet restore --verbosity minimal`
