---
title: DotNet geçiş komutu
description: DotNet Migrate komutu bir projeyi ve tüm bağımlılıklarını geçirir.
ms.date: 06/26/2019
ms.openlocfilehash: 86f11592e774da12b010886aaa1e30cee063fea6
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202539"
---
# <a name="dotnet-migrate"></a><span data-ttu-id="7d30a-103">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="7d30a-103">dotnet migrate</span></span>

<span data-ttu-id="7d30a-104">**Bu konu şu şekilde geçerlidir: ✓** .NET Core 1. x SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="7d30a-104">**This topic applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="7d30a-105">Ad</span><span class="sxs-lookup"><span data-stu-id="7d30a-105">Name</span></span>

<span data-ttu-id="7d30a-106">`dotnet migrate`-Preview 2 .NET Core projesini .NET Core SDK stilinde bir projeye geçirir.</span><span class="sxs-lookup"><span data-stu-id="7d30a-106">`dotnet migrate` - Migrates a Preview 2 .NET Core project to a .NET Core SDK-style project.</span></span>

> [!NOTE]
> <span data-ttu-id="7d30a-107">`dotnet migrate`, sonraki önizleme sürümündeki .NET Core 3,0 SDK 'dan kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="7d30a-107">`dotnet migrate` will be removed from the .NET Core 3.0 SDK in the next preview release.</span></span>

## <a name="synopsis"></a><span data-ttu-id="7d30a-108">Özeti</span><span class="sxs-lookup"><span data-stu-id="7d30a-108">Synopsis</span></span>

```console
dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [--format-report-file-json] [-r|--report-file] [-s|--skip-project-references] [--skip-backup] [-t|--template-file] [-v|--sdk-package-version] [-x|--xproj-file]
dotnet migrate [-h|--help]
```

## <a name="description"></a><span data-ttu-id="7d30a-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7d30a-109">Description</span></span>

<span data-ttu-id="7d30a-110">Komutu geçerli bir Preview 2 *Project. JSON*tabanlı projeyi geçerli bir .NET Core SDK stili csproj projesine geçirir. `dotnet migrate`</span><span class="sxs-lookup"><span data-stu-id="7d30a-110">The `dotnet migrate` command migrates a valid Preview 2 *project.json*-based project to a valid .NET Core SDK-style *csproj* project.</span></span>

<span data-ttu-id="7d30a-111">Varsayılan olarak, komut kök projeyi ve kök projenin içerdiği tüm proje başvurularını geçirir.</span><span class="sxs-lookup"><span data-stu-id="7d30a-111">By default, the command migrates the root project and any project references that the root project contains.</span></span> <span data-ttu-id="7d30a-112">Bu davranış, `--skip-project-references` çalışma zamanında seçeneği kullanılarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="7d30a-112">This behavior is disabled using the `--skip-project-references` option at runtime.</span></span>

<span data-ttu-id="7d30a-113">Aşağıdaki varlıklarda geçiş yapılabilir:</span><span class="sxs-lookup"><span data-stu-id="7d30a-113">Migration can be performed on the following assets:</span></span>

* <span data-ttu-id="7d30a-114">Geçirilecek *Project. JSON* dosyasını belirterek tek bir proje.</span><span class="sxs-lookup"><span data-stu-id="7d30a-114">A single project by specifying the *project.json* file to migrate.</span></span>
* <span data-ttu-id="7d30a-115">Global. json dosyasında bir yolu geçirerek *Global. JSON* dosyasında belirtilen tüm dizinler.</span><span class="sxs-lookup"><span data-stu-id="7d30a-115">All of the directories specified in the *global.json* file by passing in a path to the *global.json* file.</span></span>
* <span data-ttu-id="7d30a-116">Çözümde başvurulan projeleri geçirirken *çözüm. sln* dosyası.</span><span class="sxs-lookup"><span data-stu-id="7d30a-116">A *solution.sln* file, where it migrates the projects referenced in the solution.</span></span>
* <span data-ttu-id="7d30a-117">Verilen dizinin tüm alt dizinlerinde özyinelemeli olarak.</span><span class="sxs-lookup"><span data-stu-id="7d30a-117">On all subdirectories of the given directory recursively.</span></span>

<span data-ttu-id="7d30a-118">Komut, geçirilen *Project. JSON* dosyasını dizin yoksa oluşturduğu bir `backup` dizin içinde tutar. `dotnet migrate`</span><span class="sxs-lookup"><span data-stu-id="7d30a-118">The `dotnet migrate` command keeps the migrated *project.json* file inside a `backup` directory, which it creates if the directory doesn't exist.</span></span> <span data-ttu-id="7d30a-119">Bu davranış `--skip-backup` seçeneği kullanılarak geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="7d30a-119">This behavior is overridden using the `--skip-backup` option.</span></span>

<span data-ttu-id="7d30a-120">Varsayılan olarak, geçiş işlemi geçiş işleminin durumunu standart çıktıya (STDOUT) verir.</span><span class="sxs-lookup"><span data-stu-id="7d30a-120">By default, the migration operation outputs the state of the migration process to standard output (STDOUT).</span></span> <span data-ttu-id="7d30a-121">`--report-file <REPORT_FILE>` Seçeneğini kullanırsanız, çıkış dosyaya kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="7d30a-121">If you use the `--report-file <REPORT_FILE>` option, the output is saved to the file specify.</span></span>

<span data-ttu-id="7d30a-122">Komutu yalnızca geçerli Preview 2 *Project. JSON*tabanlı projeleri destekler. `dotnet migrate`</span><span class="sxs-lookup"><span data-stu-id="7d30a-122">The `dotnet migrate` command only supports valid Preview 2 *project.json*-based projects.</span></span> <span data-ttu-id="7d30a-123">Bu, DNX veya Preview 1 *Project. JSON*tabanlı projeleri doğrudan MSBuild/csproj projelerine geçirebileceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="7d30a-123">This means that you cannot use it to migrate DNX or Preview 1 *project.json*-based projects directly to MSBuild/csproj projects.</span></span> <span data-ttu-id="7d30a-124">Önce projeyi bir Preview 2 *Project. JSON*tabanlı projeye el ile geçirmeniz ve ardından projeyi geçirmek için `dotnet migrate` komutunu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7d30a-124">You first need to manually migrate the project to a Preview 2 *project.json*-based project and then use the `dotnet migrate` command to migrate the project.</span></span>

## <a name="arguments"></a><span data-ttu-id="7d30a-125">Arguments</span><span class="sxs-lookup"><span data-stu-id="7d30a-125">Arguments</span></span>

`PROJECT_JSON/GLOBAL_JSON/SOLUTION_FILE/PROJECT_DIR`

<span data-ttu-id="7d30a-126">Aşağıdakilerden birinin yolu:</span><span class="sxs-lookup"><span data-stu-id="7d30a-126">The path to one of the following:</span></span>

* <span data-ttu-id="7d30a-127">geçirilecek bir *Project. JSON* dosyası.</span><span class="sxs-lookup"><span data-stu-id="7d30a-127">a *project.json* file to migrate.</span></span>
* <span data-ttu-id="7d30a-128">*Global. JSON* dosyası: *Global. JSON* içinde belirtilen klasörler geçirilir.</span><span class="sxs-lookup"><span data-stu-id="7d30a-128">a *global.json* file: the folders specified in *global.json* are migrated.</span></span>
* <span data-ttu-id="7d30a-129">bir *çözüm. sln* dosyası: çözümde başvurulan projeler geçirilir.</span><span class="sxs-lookup"><span data-stu-id="7d30a-129">a *solution.sln* file: the projects referenced in the solution are migrated.</span></span>
* <span data-ttu-id="7d30a-130">geçirilecek Dizin: özyinelemeli olarak *Project. JSON* dosyalarını belirtilen dizin içinde geçirilecek şekilde arar.</span><span class="sxs-lookup"><span data-stu-id="7d30a-130">a directory to migrate: recursively searches for *project.json* files to migrate inside the specified directory.</span></span>

<span data-ttu-id="7d30a-131">Hiçbir şey belirtilmemişse, varsayılan olarak geçerli dizine ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="7d30a-131">Defaults to current directory if nothing is specified.</span></span>

## <a name="options"></a><span data-ttu-id="7d30a-132">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="7d30a-132">Options</span></span>

`--format-report-file-json <REPORT_FILE>`

<span data-ttu-id="7d30a-133">Geçiş raporu dosyasını kullanıcı iletileri yerine JSON olarak çıkar.</span><span class="sxs-lookup"><span data-stu-id="7d30a-133">Output migration report file as JSON rather than user messages.</span></span>

`-h|--help`

<span data-ttu-id="7d30a-134">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="7d30a-134">Prints out a short help for the command.</span></span>

`-r|--report-file <REPORT_FILE>`

<span data-ttu-id="7d30a-135">Konsola ek olarak çıkış geçiş raporu.</span><span class="sxs-lookup"><span data-stu-id="7d30a-135">Output migration report to a file in addition to the console.</span></span>

`-s|--skip-project-references [Debug|Release]`

<span data-ttu-id="7d30a-136">Proje başvurularını geçirmeyi atlayın.</span><span class="sxs-lookup"><span data-stu-id="7d30a-136">Skip migrating project references.</span></span> <span data-ttu-id="7d30a-137">Varsayılan olarak, proje başvuruları yinelemeli olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="7d30a-137">By default, project references are migrated recursively.</span></span>

`--skip-backup`

<span data-ttu-id="7d30a-138">Başarılı geçişten sonra *Project. JSON*, *Global. JSON*ve  *\*. xproj* ' ı `backup` bir dizine taşımayı atlayın.</span><span class="sxs-lookup"><span data-stu-id="7d30a-138">Skip moving *project.json*, *global.json*, and *\*.xproj* to a `backup` directory after successful migration.</span></span>

`-t|--template-file <TEMPLATE_FILE>`

<span data-ttu-id="7d30a-139">Geçiş için kullanılacak şablon csproj dosyası.</span><span class="sxs-lookup"><span data-stu-id="7d30a-139">Template csproj file to use for migration.</span></span> <span data-ttu-id="7d30a-140">Varsayılan olarak, tarafından bırakılan ile `dotnet new console` aynı şablon kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7d30a-140">By default, the same template as the one dropped by `dotnet new console` is used.</span></span>

`-v|--sdk-package-version <VERSION>`

<span data-ttu-id="7d30a-141">Geçirilen uygulamada başvurulan SDK paketinin sürümü.</span><span class="sxs-lookup"><span data-stu-id="7d30a-141">The version of the sdk package that's referenced in the migrated app.</span></span> <span data-ttu-id="7d30a-142">Varsayılan, ' deki `dotnet new`SDK sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="7d30a-142">The default is the version of the SDK in `dotnet new`.</span></span>

`-x|--xproj-file <FILE>`

<span data-ttu-id="7d30a-143">Kullanılacak xproj dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="7d30a-143">The path to the xproj file to use.</span></span> <span data-ttu-id="7d30a-144">Proje dizininde birden fazla xproj olduğunda gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7d30a-144">Required when there is more than one xproj in a project directory.</span></span>

## <a name="examples"></a><span data-ttu-id="7d30a-145">Örnekler</span><span class="sxs-lookup"><span data-stu-id="7d30a-145">Examples</span></span>

<span data-ttu-id="7d30a-146">Geçerli dizindeki bir projeyi ve projenin tüm proje bağımlılıklarını geçirin:</span><span class="sxs-lookup"><span data-stu-id="7d30a-146">Migrate a project in the current directory and all of its project-to-project dependencies:</span></span>

`dotnet migrate`

<span data-ttu-id="7d30a-147">*Global. JSON* dosyasının içerdiği tüm projeleri geçirin:</span><span class="sxs-lookup"><span data-stu-id="7d30a-147">Migrate all projects that *global.json* file includes:</span></span>

`dotnet migrate path/to/global.json`

<span data-ttu-id="7d30a-148">Yalnızca geçerli projeyi geçirin ve projeden projeye (P2P) bağımlılıkları yoktur.</span><span class="sxs-lookup"><span data-stu-id="7d30a-148">Migrate only the current project and no project-to-project (P2P) dependencies.</span></span> <span data-ttu-id="7d30a-149">Ayrıca, belirli bir SDK sürümünü kullanın:</span><span class="sxs-lookup"><span data-stu-id="7d30a-149">Also, use a specific SDK version:</span></span>

`dotnet migrate -s -v 1.0.0-preview4`
