---
title: DotNet restore komutu
description: Bağımlılıklar ve projeye özgü araçları dotnet restore komutu ile geri yüklemeyi öğreneceksiniz.
ms.date: 05/29/2018
ms.openlocfilehash: 6f54671fcd1c17d2466d5a38027e02da5e7494e9
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170788"
---
# <a name="dotnet-restore"></a><span data-ttu-id="948db-103">DotNet restore</span><span class="sxs-lookup"><span data-stu-id="948db-103">dotnet restore</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="948db-104">Ad</span><span class="sxs-lookup"><span data-stu-id="948db-104">Name</span></span>

<span data-ttu-id="948db-105">`dotnet restore` -Bir projenin Araçlar ve bağımlılıkları yükler.</span><span class="sxs-lookup"><span data-stu-id="948db-105">`dotnet restore` - Restores the dependencies and tools of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="948db-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="948db-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="948db-107">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="948db-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--force] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity] [--interactive]
dotnet restore [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="948db-108">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="948db-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="948db-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="948db-109">Description</span></span>

<span data-ttu-id="948db-110">`dotnet restore` Komutu, proje dosyasında belirtilen projeye özgü araçları yanı sıra bağımlılıkları geri yüklemek için NuGet kullanır.</span><span class="sxs-lookup"><span data-stu-id="948db-110">The `dotnet restore` command uses NuGet to restore dependencies as well as project-specific tools that are specified in the project file.</span></span> <span data-ttu-id="948db-111">Varsayılan olarak, Araçlar ile bağımlılıkları ve geri yükleme işlemi paralel olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="948db-111">By default, the restoration of dependencies and tools are executed in parallel.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="948db-112">Bağımlılıkları geri yüklemek için NuGet paketlerinin yer aldığı akışları gerekir.</span><span class="sxs-lookup"><span data-stu-id="948db-112">To restore the dependencies, NuGet needs the feeds where the packages are located.</span></span> <span data-ttu-id="948db-113">Akışları aracılığıyla genellikle sağlanan *NuGet.config* yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="948db-113">Feeds are usually provided via the *NuGet.config* configuration file.</span></span> <span data-ttu-id="948db-114">CLI araçları yüklü olduğunda varsayılan yapılandırma dosyası sağlanır.</span><span class="sxs-lookup"><span data-stu-id="948db-114">A default configuration file is provided when the CLI tools are installed.</span></span> <span data-ttu-id="948db-115">Kendi oluşturarak ek akışları belirttiğiniz *NuGet.config* dosya proje dizininde.</span><span class="sxs-lookup"><span data-stu-id="948db-115">You specify additional feeds by creating your own *NuGet.config* file in the project directory.</span></span> <span data-ttu-id="948db-116">Bir komut isteminde çağrı başına ek akışları de belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="948db-116">You also specify additional feeds per invocation at a command prompt.</span></span>

<span data-ttu-id="948db-117">Bağımlılıklar için geri yüklenen paketler geri yükleme kullanarak işlemi sırasında yerleştirildiği belirtin `--packages` bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="948db-117">For dependencies, you specify where the restored packages are placed during the restore operation using the `--packages` argument.</span></span> <span data-ttu-id="948db-118">Belirtilmezse, varsayılan NuGet paket önbelleğini, içinde geçtiği yerin kullanılıp kullanılmadığını `.nuget/packages` dizini ile tüm işletim sistemlerinde kullanıcının ana dizini.</span><span class="sxs-lookup"><span data-stu-id="948db-118">If not specified, the default NuGet package cache is used, which is found in the `.nuget/packages` directory in the user's home directory on all operating systems.</span></span> <span data-ttu-id="948db-119">Örneğin, */home/user1* Linux üzerinde veya *C:\Users\user1* Windows üzerinde.</span><span class="sxs-lookup"><span data-stu-id="948db-119">For example, */home/user1* on Linux or *C:\Users\user1* on Windows.</span></span>

<span data-ttu-id="948db-120">Projeye özgü araçları için `dotnet restore` öncelikle hangi aracın iyileştirmesiyle doludur ve kendi proje dosyasında belirtilen Aracı'nın bağımlılıkları geri yüklemek için devam eder paket geri yükler.</span><span class="sxs-lookup"><span data-stu-id="948db-120">For project-specific tooling, `dotnet restore` first restores the package in which the tool is packed, and then proceeds to restore the tool's dependencies as specified in its project file.</span></span>

<span data-ttu-id="948db-121">Davranışını `dotnet restore` komut bazı ayarlar tarafından etkilendi *Nuget.Config* varsa, dosya.</span><span class="sxs-lookup"><span data-stu-id="948db-121">The behavior of the `dotnet restore` command is affected by some of the settings in the *Nuget.Config* file, if present.</span></span> <span data-ttu-id="948db-122">Örneğin, ayarlamak `globalPackagesFolder` içinde *NuGet.Config* belirtilen klasörde NuGet paketlerini geri yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="948db-122">For example, setting the `globalPackagesFolder` in *NuGet.Config* places the restored NuGet packages in the specified folder.</span></span> <span data-ttu-id="948db-123">Bu belirten bir alternatifidir `--packages` seçeneğini `dotnet restore` komutu.</span><span class="sxs-lookup"><span data-stu-id="948db-123">This is an alternative to specifying the `--packages` option on the `dotnet restore` command.</span></span> <span data-ttu-id="948db-124">Daha fazla bilgi için [NuGet.Config başvuru](/nuget/schema/nuget-config-file).</span><span class="sxs-lookup"><span data-stu-id="948db-124">For more information, see the [NuGet.Config reference](/nuget/schema/nuget-config-file).</span></span>

## <a name="implicit-dotnet-restore"></a><span data-ttu-id="948db-125">Örtük `dotnet restore`</span><span class="sxs-lookup"><span data-stu-id="948db-125">Implicit `dotnet restore`</span></span>

<span data-ttu-id="948db-126">.NET Core 2.0 ile başlayarak `dotnet restore` aşağıdaki komutları gönderdiğinizde gerekirse örtük olarak çalıştırılan:</span><span class="sxs-lookup"><span data-stu-id="948db-126">Starting with .NET Core 2.0, `dotnet restore` is run implicitly if necessary when you issue the following commands:</span></span>

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

<span data-ttu-id="948db-127">Çoğu durumda, artık açıkça kullanmanız gerekir `dotnet restore` komutu.</span><span class="sxs-lookup"><span data-stu-id="948db-127">In most cases, you no longer need to explicitly use the `dotnet restore` command.</span></span>

<span data-ttu-id="948db-128">Bazı durumlarda, çalıştırılacak kullanışsız olabilir `dotnet restore` örtük olarak.</span><span class="sxs-lookup"><span data-stu-id="948db-128">Sometimes, it might be inconvenient to run `dotnet restore` implicitly.</span></span> <span data-ttu-id="948db-129">Örneğin, yapı sistemi gibi bazı otomatik sistemler çağırmanız gerekir `dotnet restore` açıkça ağ kullanımını kontrol edebilir, böylece geri yükleme ne zaman gerçekleştiğini denetlemek için.</span><span class="sxs-lookup"><span data-stu-id="948db-129">For example, some automated systems, such as build systems, need to call `dotnet restore` explicitly to control when the restore occurs so that they can control network usage.</span></span> <span data-ttu-id="948db-130">Önlemek için `dotnet restore` kullanabileceğiniz örtük olarak çalıştırılmasının `--no-restore` örtük geri yükleme devre dışı bırakmak için aşağıdaki komutlardan birini bayrağıyla.</span><span class="sxs-lookup"><span data-stu-id="948db-130">To prevent `dotnet restore` from running implicitly, you can use the `--no-restore` flag with any of these commands to disable implicit restore.</span></span>

## <a name="arguments"></a><span data-ttu-id="948db-131">Arguments</span><span class="sxs-lookup"><span data-stu-id="948db-131">Arguments</span></span>

`ROOT`

<span data-ttu-id="948db-132">İsteğe bağlı geri yüklemek için proje dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="948db-132">Optional path to the project file to restore.</span></span>

## <a name="options"></a><span data-ttu-id="948db-133">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="948db-133">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="948db-134">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="948db-134">.NET Core 2.x</span></span>](#tab/netcore2x)

`--configfile <FILE>`

<span data-ttu-id="948db-135">NuGet yapılandırma dosyası (*NuGet.config*) geri yükleme işlemi için kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="948db-135">The NuGet configuration file (*NuGet.config*) to use for the restore operation.</span></span>

`--disable-parallel`

<span data-ttu-id="948db-136">Paralel olarak birden çok proje geri yükleme devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="948db-136">Disables restoring multiple projects in parallel.</span></span>

`--force`

<span data-ttu-id="948db-137">Son geri yükleme başarılı olduysa bile çözülmesi için tüm bağımlılıkların zorlar.</span><span class="sxs-lookup"><span data-stu-id="948db-137">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="948db-138">Bu bayrak belirten aynıdır silme *project.assets.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="948db-138">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="948db-139">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="948db-139">Prints out a short help for the command.</span></span>

`--ignore-failed-sources`

<span data-ttu-id="948db-140">Yalnızca sürüm gereksinimi Karşılama paketleri varsa başarısız kaynakları hakkında uyar.</span><span class="sxs-lookup"><span data-stu-id="948db-140">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

`--no-cache`

<span data-ttu-id="948db-141">Paketler ve HTTP isteklerini önbelleğe belirtir.</span><span class="sxs-lookup"><span data-stu-id="948db-141">Specifies to not cache packages and HTTP requests.</span></span>

`--no-dependencies`

<span data-ttu-id="948db-142">Projeden projeye (P2P) başvurular içeren bir proje geri yüklerken, kök proje ve başvuruları geri yükler.</span><span class="sxs-lookup"><span data-stu-id="948db-142">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--packages <PACKAGES_DIRECTORY>`

<span data-ttu-id="948db-143">Geri yüklenen paketler için dizini belirtir.</span><span class="sxs-lookup"><span data-stu-id="948db-143">Specifies the directory for restored packages.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="948db-144">Paket geri yükleme için bir çalışma zamanı belirtir.</span><span class="sxs-lookup"><span data-stu-id="948db-144">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="948db-145">Bu açıkça listelenen çalışma zamanları için paketler geri yüklemek için kullanılan `<RuntimeIdentifiers>` içindeki *.csproj* dosya.</span><span class="sxs-lookup"><span data-stu-id="948db-145">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="948db-146">Çalışma zamanı tanımlayıcılarının (RID'ler) bir listesi için bkz. [RID Kataloğu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="948db-146">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="948db-147">Bu seçeneği birden çok kez belirterek, birden fazla RID sağlar.</span><span class="sxs-lookup"><span data-stu-id="948db-147">Provide multiple RIDs by specifying this option multiple times.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="948db-148">Geri yükleme işlemi sırasında kullanılacak bir NuGet paket kaynağı belirtir.</span><span class="sxs-lookup"><span data-stu-id="948db-148">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="948db-149">Bu ayar tüm kaynakları belirtilen geçersiz kılmaları *NuGet.config* dosyaları.</span><span class="sxs-lookup"><span data-stu-id="948db-149">This setting overrides all of the sources specified in the *NuGet.config* files.</span></span> <span data-ttu-id="948db-150">Bu seçeneği birden çok kez belirterek, birden çok kaynaktan sağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="948db-150">Multiple sources can be provided by specifying this option multiple times.</span></span>

`--verbosity <LEVEL>`

<span data-ttu-id="948db-151">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="948db-151">Sets the verbosity level of the command.</span></span> <span data-ttu-id="948db-152">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="948db-152">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--interactive`

<span data-ttu-id="948db-153">Durdurmak ve kullanıcı girişi veya eylem (örneğin kimlik doğrulamasını tamamlamak için) için beklemek için komutu sağlar.</span><span class="sxs-lookup"><span data-stu-id="948db-153">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span> <span data-ttu-id="948db-154">.NET Core 2.1.400 itibaren.</span><span class="sxs-lookup"><span data-stu-id="948db-154">Since .NET Core 2.1.400.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="948db-155">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="948db-155">.NET Core 1.x</span></span>](#tab/netcore1x)

`--configfile <FILE>`

<span data-ttu-id="948db-156">NuGet yapılandırma dosyası (*NuGet.config*) geri yükleme işlemi için kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="948db-156">The NuGet configuration file (*NuGet.config*) to use for the restore operation.</span></span>

`--disable-parallel`

<span data-ttu-id="948db-157">Paralel olarak birden çok proje geri yükleme devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="948db-157">Disables restoring multiple projects in parallel.</span></span>

`-h|--help`

<span data-ttu-id="948db-158">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="948db-158">Prints out a short help for the command.</span></span>

`--ignore-failed-sources`

<span data-ttu-id="948db-159">Yalnızca sürüm gereksinimi Karşılama paketleri varsa başarısız kaynakları hakkında uyar.</span><span class="sxs-lookup"><span data-stu-id="948db-159">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

`--no-cache`

<span data-ttu-id="948db-160">Paketler ve HTTP isteklerini önbelleğe belirtir.</span><span class="sxs-lookup"><span data-stu-id="948db-160">Specifies to not cache packages and HTTP requests.</span></span>

`--no-dependencies`

<span data-ttu-id="948db-161">Projeden projeye (P2P) başvurular içeren bir proje geri yüklerken, kök proje ve başvuruları geri yükler.</span><span class="sxs-lookup"><span data-stu-id="948db-161">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--packages <PACKAGES_DIRECTORY>`

<span data-ttu-id="948db-162">Geri yüklenen paketler için dizini belirtir.</span><span class="sxs-lookup"><span data-stu-id="948db-162">Specifies the directory for restored packages.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="948db-163">Paket geri yükleme için bir çalışma zamanı belirtir.</span><span class="sxs-lookup"><span data-stu-id="948db-163">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="948db-164">Bu açıkça listelenen çalışma zamanları için paketler geri yüklemek için kullanılan `<RuntimeIdentifiers>` içindeki *.csproj* dosya.</span><span class="sxs-lookup"><span data-stu-id="948db-164">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="948db-165">Çalışma zamanı tanımlayıcılarının (RID'ler) bir listesi için bkz. [RID Kataloğu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="948db-165">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="948db-166">Bu seçeneği birden çok kez belirterek, birden fazla RID sağlar.</span><span class="sxs-lookup"><span data-stu-id="948db-166">Provide multiple RIDs by specifying this option multiple times.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="948db-167">Geri yükleme işlemi sırasında kullanılacak bir NuGet paket kaynağı belirtir.</span><span class="sxs-lookup"><span data-stu-id="948db-167">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="948db-168">Bu kaynakları belirtilen tüm geçersiz kılmaları *NuGet.config* dosyaları.</span><span class="sxs-lookup"><span data-stu-id="948db-168">This overrides all of the sources specified in the *NuGet.config* files.</span></span> <span data-ttu-id="948db-169">Bu seçeneği birden çok kez belirterek, birden çok kaynaktan sağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="948db-169">Multiple sources can be provided by specifying this option multiple times.</span></span>

`--verbosity <LEVEL>`

<span data-ttu-id="948db-170">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="948db-170">Sets the verbosity level of the command.</span></span> <span data-ttu-id="948db-171">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="948db-171">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="948db-172">Örnekler</span><span class="sxs-lookup"><span data-stu-id="948db-172">Examples</span></span>

<span data-ttu-id="948db-173">Bağımlılıklar ve geçerli dizinde proje için araçları geri yükleme:</span><span class="sxs-lookup"><span data-stu-id="948db-173">Restore dependencies and tools for the project in the current directory:</span></span>

`dotnet restore`

<span data-ttu-id="948db-174">Bağımlılıklar ve araçlar için geri `app1` proje verilen yolda bulunamadı:</span><span class="sxs-lookup"><span data-stu-id="948db-174">Restore dependencies and tools for the `app1` project found in the given path:</span></span>

`dotnet restore ~/projects/app1/app1.csproj`

<span data-ttu-id="948db-175">Kaynak olarak sağlanan dosya yolunu kullanarak geçerli dizinde proje için Araçlar ve bağımlılıklar geri yükleme:</span><span class="sxs-lookup"><span data-stu-id="948db-175">Restore the dependencies and tools for the project in the current directory using the file path provided as the source:</span></span>

`dotnet restore -s c:\packages\mypackages`

<span data-ttu-id="948db-176">Kaynakları olarak sağlanan iki dosya yolları kullanarak geçerli dizinde proje için Araçlar ve bağımlılıklar geri yükleme:</span><span class="sxs-lookup"><span data-stu-id="948db-176">Restore the dependencies and tools for the project in the current directory using the two file paths provided as sources:</span></span>

`dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages`

<span data-ttu-id="948db-177">Bağımlılıklar ve araçlar için geçerli dizin ve programlarını yalnızca en az çıktı projede geri yükleme:</span><span class="sxs-lookup"><span data-stu-id="948db-177">Restore dependencies and tools for the project in the current directory and shows only minimal output:</span></span>

`dotnet restore --verbosity minimal`
