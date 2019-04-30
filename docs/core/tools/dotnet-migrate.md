---
title: DotNet komut geçirme
description: Dotnet geçirme komutu, bir projeyi ve tüm bağımlılıklarını geçirir.
ms.date: 05/25/2018
ms.openlocfilehash: 73e0169e64be4b55e10127ecca0101885061767e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665032"
---
# <a name="dotnet-migrate"></a><span data-ttu-id="369eb-103">DotNet geçirme</span><span class="sxs-lookup"><span data-stu-id="369eb-103">dotnet migrate</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="369eb-104">Ad</span><span class="sxs-lookup"><span data-stu-id="369eb-104">Name</span></span>

<span data-ttu-id="369eb-105">`dotnet migrate` -Önizleme 2 .NET Core projesi bir .NET Core SDK'sı 1.0 projesine geçirir.</span><span class="sxs-lookup"><span data-stu-id="369eb-105">`dotnet migrate` - Migrates a Preview 2 .NET Core project to a .NET Core SDK 1.0 project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="369eb-106">Synopsis</span><span class="sxs-lookup"><span data-stu-id="369eb-106">Synopsis</span></span>

```
dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [--format-report-file-json] [-r|--report-file] [-s|--skip-project-references] [--skip-backup] [-t|--template-file] [-v|--sdk-package-version] [-x|--xproj-file]
dotnet migrate [-h|--help]
```

## <a name="description"></a><span data-ttu-id="369eb-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="369eb-107">Description</span></span>

<span data-ttu-id="369eb-108">`dotnet migrate` Komutu geçerli bir önizleme 2 geçirir *project.json*-geçerli bir .NET Core SDK'sı 1.0 projeye dayalı *csproj* proje.</span><span class="sxs-lookup"><span data-stu-id="369eb-108">The `dotnet migrate` command migrates a valid Preview 2 *project.json*-based project to a valid .NET Core SDK 1.0 *csproj* project.</span></span>

<span data-ttu-id="369eb-109">Kök proje ve kök projesini içeren tüm proje başvuruları, varsayılan olarak, komut geçirir.</span><span class="sxs-lookup"><span data-stu-id="369eb-109">By default, the command migrates the root project and any project references that the root project contains.</span></span> <span data-ttu-id="369eb-110">Kullanarak bu davranışı devre dışı `--skip-project-references` zamanında seçeneği.</span><span class="sxs-lookup"><span data-stu-id="369eb-110">This behavior is disabled using the `--skip-project-references` option at runtime.</span></span>

<span data-ttu-id="369eb-111">Geçiş aşağıdaki varlıklar üzerinde gerçekleştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="369eb-111">Migration can be performed on the following assets:</span></span>

* <span data-ttu-id="369eb-112">Tek bir projeye belirterek *project.json* geçirmek için dosya.</span><span class="sxs-lookup"><span data-stu-id="369eb-112">A single project by specifying the *project.json* file to migrate.</span></span>
* <span data-ttu-id="369eb-113">Tüm belirtilen dizinlerin *global.json* dosya yolunu geçirerek *global.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="369eb-113">All of the directories specified in the *global.json* file by passing in a path to the *global.json* file.</span></span>
* <span data-ttu-id="369eb-114">A *solution.sln* geçirildikten burada çözümde başvurulan proje dosyası.</span><span class="sxs-lookup"><span data-stu-id="369eb-114">A *solution.sln* file, where it migrates the projects referenced in the solution.</span></span>
* <span data-ttu-id="369eb-115">Belirtilen dizini yinelemeli olarak tüm alt üzerinde.</span><span class="sxs-lookup"><span data-stu-id="369eb-115">On all subdirectories of the given directory recursively.</span></span>

<span data-ttu-id="369eb-116">`dotnet migrate` Komut tutar geçirilen *project.json* içindeki dosya bir `backup` dizin yoksa, oluşturduğu dizin.</span><span class="sxs-lookup"><span data-stu-id="369eb-116">The `dotnet migrate` command keeps the migrated *project.json* file inside a `backup` directory, which it creates if the directory doesn't exist.</span></span> <span data-ttu-id="369eb-117">Kullanarak bu davranışı geçersiz `--skip-backup` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="369eb-117">This behavior is overridden using the `--skip-backup` option.</span></span>

<span data-ttu-id="369eb-118">Varsayılan olarak, geçiş işlemi için standart çıktı (STDOUT) geçiş işleminin durumunu çıkarır.</span><span class="sxs-lookup"><span data-stu-id="369eb-118">By default, the migration operation outputs the state of the migration process to standard output (STDOUT).</span></span> <span data-ttu-id="369eb-119">Kullanırsanız `--report-file <REPORT_FILE>` seçeneği, çıkışı bir dosyaya kaydedilir belirtin.</span><span class="sxs-lookup"><span data-stu-id="369eb-119">If you use the `--report-file <REPORT_FILE>` option, the output is saved to the file specify.</span></span>

<span data-ttu-id="369eb-120">`dotnet migrate` Komutu, yalnızca geçerli Önizleme 2 destekler *project.json*-tabanlı projelerine.</span><span class="sxs-lookup"><span data-stu-id="369eb-120">The `dotnet migrate` command only supports valid Preview 2 *project.json*-based projects.</span></span> <span data-ttu-id="369eb-121">Bunu DNX veya Preview 1'e geçirmek için kullanamazsınız, yani *project.json*-tabanlı projelerine MSBuild/csproj projelerine doğrudan.</span><span class="sxs-lookup"><span data-stu-id="369eb-121">This means that you cannot use it to migrate DNX or Preview 1 *project.json*-based projects directly to MSBuild/csproj projects.</span></span> <span data-ttu-id="369eb-122">Önce el ile projeyi Önizleme 2'ye geçirmek gereken *project.json*-tabanlı proje ve ardından `dotnet migrate` projeyi geçirmek için komutu.</span><span class="sxs-lookup"><span data-stu-id="369eb-122">You first need to manually migrate the project to a Preview 2 *project.json*-based project and then use the `dotnet migrate` command to migrate the project.</span></span>

## <a name="arguments"></a><span data-ttu-id="369eb-123">Arguments</span><span class="sxs-lookup"><span data-stu-id="369eb-123">Arguments</span></span>

`PROJECT_JSON/GLOBAL_JSON/SOLUTION_FILE/PROJECT_DIR`

<span data-ttu-id="369eb-124">Aşağıdakilerden birine yolu:</span><span class="sxs-lookup"><span data-stu-id="369eb-124">The path to one of the following:</span></span>

* <span data-ttu-id="369eb-125">bir *project.json* geçirmek için dosya.</span><span class="sxs-lookup"><span data-stu-id="369eb-125">a *project.json* file to migrate.</span></span>
* <span data-ttu-id="369eb-126">bir *global.json* dosya: Belirtilen klasörleri *global.json* geçirilir.</span><span class="sxs-lookup"><span data-stu-id="369eb-126">a *global.json* file: the folders specified in *global.json* are migrated.</span></span>
* <span data-ttu-id="369eb-127">bir *solution.sln* dosya: çözümde başvurulan projeler geçirilir.</span><span class="sxs-lookup"><span data-stu-id="369eb-127">a *solution.sln* file: the projects referenced in the solution are migrated.</span></span>
* <span data-ttu-id="369eb-128">geçiş için bir dizin: yinelemeli olarak arar *project.json* belirtilen dizinin içinde geçirmek için dosyaları.</span><span class="sxs-lookup"><span data-stu-id="369eb-128">a directory to migrate: recursively searches for *project.json* files to migrate inside the specified directory.</span></span>

<span data-ttu-id="369eb-129">Varsayılan olarak hiçbir şey belirtilmezse, geçerli dizin.</span><span class="sxs-lookup"><span data-stu-id="369eb-129">Defaults to current directory if nothing is specified.</span></span>

## <a name="options"></a><span data-ttu-id="369eb-130">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="369eb-130">Options</span></span>

`--format-report-file-json <REPORT_FILE>`

<span data-ttu-id="369eb-131">Geçiş raporu dosyasını kullanıcı yerine JSON iletileri olarak çıktı.</span><span class="sxs-lookup"><span data-stu-id="369eb-131">Output migration report file as JSON rather than user messages.</span></span>

`-h|--help`

<span data-ttu-id="369eb-132">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="369eb-132">Prints out a short help for the command.</span></span>

`-r|--report-file <REPORT_FILE>`

<span data-ttu-id="369eb-133">Bir dosyaya konsol ek olarak geçiş raporu çıktı.</span><span class="sxs-lookup"><span data-stu-id="369eb-133">Output migration report to a file in addition to the console.</span></span>

`-s|--skip-project-references [Debug|Release]`

<span data-ttu-id="369eb-134">Proje geçiş Atla başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="369eb-134">Skip migrating project references.</span></span> <span data-ttu-id="369eb-135">Varsayılan olarak, proje başvurularına geçirilen yinelemeli olarak olur.</span><span class="sxs-lookup"><span data-stu-id="369eb-135">By default, project references are migrated recursively.</span></span>

`--skip-backup`

<span data-ttu-id="369eb-136">Taşıma atla *project.json*, *global.json*, ve  *\*.xproj* için bir `backup` başarılı geçişten sonra dizin.</span><span class="sxs-lookup"><span data-stu-id="369eb-136">Skip moving *project.json*, *global.json*, and *\*.xproj* to a `backup` directory after successful migration.</span></span>

`-t|--template-file <TEMPLATE_FILE>`

<span data-ttu-id="369eb-137">Geçiş için kullanılacak şablonu csproj dosyasını.</span><span class="sxs-lookup"><span data-stu-id="369eb-137">Template csproj file to use for migration.</span></span> <span data-ttu-id="369eb-138">Varsayılan olarak, aynı şablonu bırakılan `dotnet new console` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="369eb-138">By default, the same template as the one dropped by `dotnet new console` is used.</span></span>

`-v|--sdk-package-version <VERSION>`

<span data-ttu-id="369eb-139">Geçirilen uygulamada başvurulan sdk Paket sürümü.</span><span class="sxs-lookup"><span data-stu-id="369eb-139">The version of the sdk package that's referenced in the migrated app.</span></span> <span data-ttu-id="369eb-140">Varsayılan SDK sürümüdür `dotnet new`.</span><span class="sxs-lookup"><span data-stu-id="369eb-140">The default is the version of the SDK in `dotnet new`.</span></span>

`-x|--xproj-file <FILE>`

<span data-ttu-id="369eb-141">Kullanılacak xproj dosyanın yolu.</span><span class="sxs-lookup"><span data-stu-id="369eb-141">The path to the xproj file to use.</span></span> <span data-ttu-id="369eb-142">Proje dizininde birden fazla xproj olduğunda gereklidir.</span><span class="sxs-lookup"><span data-stu-id="369eb-142">Required when there is more than one xproj in a project directory.</span></span>

## <a name="examples"></a><span data-ttu-id="369eb-143">Örnekler</span><span class="sxs-lookup"><span data-stu-id="369eb-143">Examples</span></span>

<span data-ttu-id="369eb-144">Bir projede geçerli dizin ve tüm proje ve proje bağımlılıklarını Geçir:</span><span class="sxs-lookup"><span data-stu-id="369eb-144">Migrate a project in the current directory and all of its project-to-project dependencies:</span></span>

`dotnet migrate`

<span data-ttu-id="369eb-145">Geçiş tüm projeleri *global.json* dosyası içerir:</span><span class="sxs-lookup"><span data-stu-id="369eb-145">Migrate all projects that *global.json* file includes:</span></span>

`dotnet migrate path/to/global.json`

<span data-ttu-id="369eb-146">Yalnızca geçerli proje ve proje proje (P2P) bağımlılık geçirin.</span><span class="sxs-lookup"><span data-stu-id="369eb-146">Migrate only the current project and no project-to-project (P2P) dependencies.</span></span> <span data-ttu-id="369eb-147">Ayrıca, belirli bir SDK'sı sürümünü kullanın:</span><span class="sxs-lookup"><span data-stu-id="369eb-147">Also, use a specific SDK version:</span></span>

`dotnet migrate -s -v 1.0.0-preview4`