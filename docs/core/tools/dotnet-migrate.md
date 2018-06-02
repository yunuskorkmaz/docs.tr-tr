---
title: DotNet command - .NET Core CLI geçirme
description: Dotnet geçirmek komutu bir proje ve tüm bağımlılıkları geçirir.
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: 67a845f7604dededd00746fa6b74a320b3e134fa
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34697111"
---
# <a name="dotnet-migrate"></a><span data-ttu-id="b75d7-103">DotNet geçirme</span><span class="sxs-lookup"><span data-stu-id="b75d7-103">dotnet migrate</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="b75d7-104">Ad</span><span class="sxs-lookup"><span data-stu-id="b75d7-104">Name</span></span>

<span data-ttu-id="b75d7-105">`dotnet migrate` -Önizleme 2 .NET Core proje .NET Core SDK 1.0 projeye taşır.</span><span class="sxs-lookup"><span data-stu-id="b75d7-105">`dotnet migrate` - Migrates a Preview 2 .NET Core project to a .NET Core SDK 1.0 project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b75d7-106">Özet</span><span class="sxs-lookup"><span data-stu-id="b75d7-106">Synopsis</span></span>

```
dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [--format-report-file-json] [-r|--report-file] [-s|--skip-project-references] [--skip-backup] [-t|--template-file] [-v|--sdk-package-version] [-x|--xproj-file]
dotnet migrate [-h|--help]
```

## <a name="description"></a><span data-ttu-id="b75d7-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b75d7-107">Description</span></span>

<span data-ttu-id="b75d7-108">`dotnet migrate` Komutu geçerli bir önizleme 2 geçirir *project.json*-geçerli bir .NET Core SDK 1.0 projesine temel *csproj* projesi.</span><span class="sxs-lookup"><span data-stu-id="b75d7-108">The `dotnet migrate` command migrates a valid Preview 2 *project.json*-based project to a valid .NET Core SDK 1.0 *csproj* project.</span></span>

<span data-ttu-id="b75d7-109">Varsayılan olarak, kök proje ve kök projeyi içeren tüm proje başvuruları komutu geçirir.</span><span class="sxs-lookup"><span data-stu-id="b75d7-109">By default, the command migrates the root project and any project references that the root project contains.</span></span> <span data-ttu-id="b75d7-110">Bu davranış kullanarak devre dışı `--skip-project-references` çalışma zamanında seçeneği.</span><span class="sxs-lookup"><span data-stu-id="b75d7-110">This behavior is disabled using the `--skip-project-references` option at runtime.</span></span>

<span data-ttu-id="b75d7-111">Geçiş aşağıdaki varlıklar üzerinde gerçekleştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="b75d7-111">Migration can be performed on the following assets:</span></span>

* <span data-ttu-id="b75d7-112">Belirterek tek bir proje *project.json* geçirmek için dosya.</span><span class="sxs-lookup"><span data-stu-id="b75d7-112">A single project by specifying the *project.json* file to migrate.</span></span>
* <span data-ttu-id="b75d7-113">Tüm belirtilen dizinlerin *global.json* dosya yolunu geçirerek *global.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="b75d7-113">All of the directories specified in the *global.json* file by passing in a path to the *global.json* file.</span></span>
* <span data-ttu-id="b75d7-114">A *solution.sln* geçirildikten burada çözümde başvurulan projeleri dosya.</span><span class="sxs-lookup"><span data-stu-id="b75d7-114">A *solution.sln* file, where it migrates the projects referenced in the solution.</span></span>
* <span data-ttu-id="b75d7-115">Belirtilen dizin yinelemeli olarak tüm Altdizinler üzerinde.</span><span class="sxs-lookup"><span data-stu-id="b75d7-115">On all subdirectories of the given directory recursively.</span></span>

<span data-ttu-id="b75d7-116">`dotnet migrate` Komutu tutar geçirilen *project.json* içindeki dosya bir `backup` dizin yoksa, onu oluşturan dizin.</span><span class="sxs-lookup"><span data-stu-id="b75d7-116">The `dotnet migrate` command keeps the migrated *project.json* file inside a `backup` directory, which it creates if the directory doesn't exist.</span></span> <span data-ttu-id="b75d7-117">Kullanılarak bu davranışı geçersiz `--skip-backup` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="b75d7-117">This behavior is overridden using the `--skip-backup` option.</span></span>

<span data-ttu-id="b75d7-118">Varsayılan olarak, geçiş işlemi için standart çıkış (STDOUT) geçiş işleminin durumunu çıkarır.</span><span class="sxs-lookup"><span data-stu-id="b75d7-118">By default, the migration operation outputs the state of the migration process to standard output (STDOUT).</span></span> <span data-ttu-id="b75d7-119">Kullanırsanız `--report-file <REPORT_FILE>` seçeneği, çıktı dosyasına kaydedilir belirtin.</span><span class="sxs-lookup"><span data-stu-id="b75d7-119">If you use the `--report-file <REPORT_FILE>` option, the output is saved to the file specify.</span></span>

<span data-ttu-id="b75d7-120">`dotnet migrate` Komutu yalnızca geçerli Önizleme 2 destekler *project.json*-tabanlı projelerine.</span><span class="sxs-lookup"><span data-stu-id="b75d7-120">The `dotnet migrate` command only supports valid Preview 2 *project.json*-based projects.</span></span> <span data-ttu-id="b75d7-121">Bunu DNX veya Preview 1 geçirmek için kullanamazsınız, yani *project.json*-tabanlı projelerine MSBuild/csproj projelerine doğrudan.</span><span class="sxs-lookup"><span data-stu-id="b75d7-121">This means that you cannot use it to migrate DNX or Preview 1 *project.json*-based projects directly to MSBuild/csproj projects.</span></span> <span data-ttu-id="b75d7-122">İlk proje Önizleme 2'ye el ile geçiş yapmanız *project.json*-tabanlı proje ve ardından `dotnet migrate` proje geçirmek için komutu.</span><span class="sxs-lookup"><span data-stu-id="b75d7-122">You first need to manually migrate the project to a Preview 2 *project.json*-based project and then use the `dotnet migrate` command to migrate the project.</span></span>

## <a name="arguments"></a><span data-ttu-id="b75d7-123">Arguments</span><span class="sxs-lookup"><span data-stu-id="b75d7-123">Arguments</span></span>

`PROJECT_JSON/GLOBAL_JSON/SOLUTION_FILE/PROJECT_DIR`

<span data-ttu-id="b75d7-124">Yolu şunlardan biri:</span><span class="sxs-lookup"><span data-stu-id="b75d7-124">The path to one of the following:</span></span>

* <span data-ttu-id="b75d7-125">bir *project.json* geçirmek için dosya.</span><span class="sxs-lookup"><span data-stu-id="b75d7-125">a *project.json* file to migrate.</span></span>
* <span data-ttu-id="b75d7-126">bir *global.json* dosya: Belirtilen klasörleri *global.json* geçirilir.</span><span class="sxs-lookup"><span data-stu-id="b75d7-126">a *global.json* file: the folders specified in *global.json* are migrated.</span></span>
* <span data-ttu-id="b75d7-127">bir *solution.sln* dosya: çözümde başvurulan projeleri geçirilir.</span><span class="sxs-lookup"><span data-stu-id="b75d7-127">a *solution.sln* file: the projects referenced in the solution are migrated.</span></span>
* <span data-ttu-id="b75d7-128">geçirmek için bir dizin: özyinelemeli olarak arar *project.json* dosyaları içinde belirtilen dizin geçirmek için.</span><span class="sxs-lookup"><span data-stu-id="b75d7-128">a directory to migrate: recursively searches for *project.json* files to migrate inside the specified directory.</span></span>

<span data-ttu-id="b75d7-129">Varsayılan olarak hiçbir şey belirtilmişse, geçerli dizin.</span><span class="sxs-lookup"><span data-stu-id="b75d7-129">Defaults to current directory if nothing is specified.</span></span>

## <a name="options"></a><span data-ttu-id="b75d7-130">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="b75d7-130">Options</span></span>

`--format-report-file-json <REPORT_FILE>`

<span data-ttu-id="b75d7-131">Geçiş rapor çıktı dosyası kullanıcı yerine JSON iletileri olarak.</span><span class="sxs-lookup"><span data-stu-id="b75d7-131">Output migration report file as JSON rather than user messages.</span></span>

`-h|--help`

<span data-ttu-id="b75d7-132">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="b75d7-132">Prints out a short help for the command.</span></span>

`-r|--report-file <REPORT_FILE>`

<span data-ttu-id="b75d7-133">Çıktı geçiş rapor Konsolu ek olarak bir dosya için.</span><span class="sxs-lookup"><span data-stu-id="b75d7-133">Output migration report to a file in addition to the console.</span></span>

`-s|--skip-project-references [Debug|Release]`

<span data-ttu-id="b75d7-134">Proje geçirme Atla başvurur.</span><span class="sxs-lookup"><span data-stu-id="b75d7-134">Skip migrating project references.</span></span> <span data-ttu-id="b75d7-135">Varsayılan olarak, proje başvuruları geçirilen yinelemeli olarak gelir.</span><span class="sxs-lookup"><span data-stu-id="b75d7-135">By default, project references are migrated recursively.</span></span>

`--skip-backup`

<span data-ttu-id="b75d7-136">Taşıma atla *project.json*, *global.json*, ve  *\*artık.xproj* için bir `backup` başarılı geçişten sonra dizin.</span><span class="sxs-lookup"><span data-stu-id="b75d7-136">Skip moving *project.json*, *global.json*, and *\*.xproj* to a `backup` directory after successful migration.</span></span>

`-t|--template-file <TEMPLATE_FILE>`

<span data-ttu-id="b75d7-137">Geçiş için kullanılacak şablonu csproj dosyası.</span><span class="sxs-lookup"><span data-stu-id="b75d7-137">Template csproj file to use for migration.</span></span> <span data-ttu-id="b75d7-138">Varsayılan olarak, bir aynı şablonu bırakılan `dotnet new console` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b75d7-138">By default, the same template as the one dropped by `dotnet new console` is used.</span></span>

`-v|--sdk-package-version <VERSION>`

<span data-ttu-id="b75d7-139">Geçirilen uygulamada başvurulan sdk paketi sürümü.</span><span class="sxs-lookup"><span data-stu-id="b75d7-139">The version of the sdk package that's referenced in the migrated app.</span></span> <span data-ttu-id="b75d7-140">Varsayılan SDK'ın sürümüdür `dotnet new`.</span><span class="sxs-lookup"><span data-stu-id="b75d7-140">The default is the version of the SDK in `dotnet new`.</span></span>

`-x|--xproj-file <FILE>`

<span data-ttu-id="b75d7-141">Kullanılacak xproj dosya yolu.</span><span class="sxs-lookup"><span data-stu-id="b75d7-141">The path to the xproj file to use.</span></span> <span data-ttu-id="b75d7-142">Proje dizininde birden fazla xproj olduğunda gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b75d7-142">Required when there is more than one xproj in a project directory.</span></span>

## <a name="examples"></a><span data-ttu-id="b75d7-143">Örnekler</span><span class="sxs-lookup"><span data-stu-id="b75d7-143">Examples</span></span>

<span data-ttu-id="b75d7-144">Geçerli dizinde ve tüm proje proje bağımlılıkları projede Geçir:</span><span class="sxs-lookup"><span data-stu-id="b75d7-144">Migrate a project in the current directory and all of its project-to-project dependencies:</span></span>

`dotnet migrate`

<span data-ttu-id="b75d7-145">Geçiş tüm projeleri *global.json* dosya içerir:</span><span class="sxs-lookup"><span data-stu-id="b75d7-145">Migrate all projects that *global.json* file includes:</span></span>

`dotnet migrate path/to/global.json`

<span data-ttu-id="b75d7-146">Yalnızca geçerli proje ve proje proje (P2P) bağımlılık geçirin.</span><span class="sxs-lookup"><span data-stu-id="b75d7-146">Migrate only the current project and no project-to-project (P2P) dependencies.</span></span> <span data-ttu-id="b75d7-147">Ayrıca, belirli bir SDK sürümü kullanın:</span><span class="sxs-lookup"><span data-stu-id="b75d7-147">Also, use a specific SDK version:</span></span>

`dotnet migrate -s -v 1.0.0-preview4`