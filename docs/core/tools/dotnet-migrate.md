---
title: DotNet komut geçirme
description: Dotnet geçirme komutu, bir projeyi ve tüm bağımlılıklarını geçirir.
ms.date: 06/26/2019
ms.openlocfilehash: 3304f666d15d9188cdae76a401747d91791f817f
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539394"
---
# <a name="dotnet-migrate"></a><span data-ttu-id="d19d9-103">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="d19d9-103">dotnet migrate</span></span>

<span data-ttu-id="d19d9-104">**Bu konu için geçerlidir: ✓** .NET Core SDK'sı 1.x ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="d19d9-104">**This topic applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="d19d9-105">Ad</span><span class="sxs-lookup"><span data-stu-id="d19d9-105">Name</span></span>

<span data-ttu-id="d19d9-106">`dotnet migrate` -Önizleme 2 .NET Core projesi bir .NET Core SDK stilinde projesine geçirir.</span><span class="sxs-lookup"><span data-stu-id="d19d9-106">`dotnet migrate` - Migrates a Preview 2 .NET Core project to a .NET Core SDK-style project.</span></span>

> [!NOTE]
> <span data-ttu-id="d19d9-107">`dotnet migrate` .NET Core 3.0 SDK sonraki Önizleme sürümünde kaldırılacak.</span><span class="sxs-lookup"><span data-stu-id="d19d9-107">`dotnet migrate` will be removed from the .NET Core 3.0 SDK in the next preview release.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d19d9-108">Synopsis</span><span class="sxs-lookup"><span data-stu-id="d19d9-108">Synopsis</span></span>

```
dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [--format-report-file-json] [-r|--report-file] [-s|--skip-project-references] [--skip-backup] [-t|--template-file] [-v|--sdk-package-version] [-x|--xproj-file]
dotnet migrate [-h|--help]
```

## <a name="description"></a><span data-ttu-id="d19d9-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d19d9-109">Description</span></span>

<span data-ttu-id="d19d9-110">`dotnet migrate` Komutu geçerli bir önizleme 2 geçirir *project.json*-geçerli bir .NET Core SDK'sı-stili projeye dayalı *csproj* proje.</span><span class="sxs-lookup"><span data-stu-id="d19d9-110">The `dotnet migrate` command migrates a valid Preview 2 *project.json*-based project to a valid .NET Core SDK-style *csproj* project.</span></span>

<span data-ttu-id="d19d9-111">Kök proje ve kök projesini içeren tüm proje başvuruları, varsayılan olarak, komut geçirir.</span><span class="sxs-lookup"><span data-stu-id="d19d9-111">By default, the command migrates the root project and any project references that the root project contains.</span></span> <span data-ttu-id="d19d9-112">Kullanarak bu davranışı devre dışı `--skip-project-references` zamanında seçeneği.</span><span class="sxs-lookup"><span data-stu-id="d19d9-112">This behavior is disabled using the `--skip-project-references` option at runtime.</span></span>

<span data-ttu-id="d19d9-113">Geçiş aşağıdaki varlıklar üzerinde gerçekleştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="d19d9-113">Migration can be performed on the following assets:</span></span>

* <span data-ttu-id="d19d9-114">Tek bir projeye belirterek *project.json* geçirmek için dosya.</span><span class="sxs-lookup"><span data-stu-id="d19d9-114">A single project by specifying the *project.json* file to migrate.</span></span>
* <span data-ttu-id="d19d9-115">Tüm belirtilen dizinlerin *global.json* dosya yolunu geçirerek *global.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="d19d9-115">All of the directories specified in the *global.json* file by passing in a path to the *global.json* file.</span></span>
* <span data-ttu-id="d19d9-116">A *solution.sln* geçirildikten burada çözümde başvurulan proje dosyası.</span><span class="sxs-lookup"><span data-stu-id="d19d9-116">A *solution.sln* file, where it migrates the projects referenced in the solution.</span></span>
* <span data-ttu-id="d19d9-117">Belirtilen dizini yinelemeli olarak tüm alt üzerinde.</span><span class="sxs-lookup"><span data-stu-id="d19d9-117">On all subdirectories of the given directory recursively.</span></span>

<span data-ttu-id="d19d9-118">`dotnet migrate` Komut tutar geçirilen *project.json* içindeki dosya bir `backup` dizin yoksa, oluşturduğu dizin.</span><span class="sxs-lookup"><span data-stu-id="d19d9-118">The `dotnet migrate` command keeps the migrated *project.json* file inside a `backup` directory, which it creates if the directory doesn't exist.</span></span> <span data-ttu-id="d19d9-119">Kullanarak bu davranışı geçersiz `--skip-backup` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="d19d9-119">This behavior is overridden using the `--skip-backup` option.</span></span>

<span data-ttu-id="d19d9-120">Varsayılan olarak, geçiş işlemi için standart çıktı (STDOUT) geçiş işleminin durumunu çıkarır.</span><span class="sxs-lookup"><span data-stu-id="d19d9-120">By default, the migration operation outputs the state of the migration process to standard output (STDOUT).</span></span> <span data-ttu-id="d19d9-121">Kullanırsanız `--report-file <REPORT_FILE>` seçeneği, çıkışı bir dosyaya kaydedilir belirtin.</span><span class="sxs-lookup"><span data-stu-id="d19d9-121">If you use the `--report-file <REPORT_FILE>` option, the output is saved to the file specify.</span></span>

<span data-ttu-id="d19d9-122">`dotnet migrate` Komutu, yalnızca geçerli Önizleme 2 destekler *project.json*-tabanlı projelerine.</span><span class="sxs-lookup"><span data-stu-id="d19d9-122">The `dotnet migrate` command only supports valid Preview 2 *project.json*-based projects.</span></span> <span data-ttu-id="d19d9-123">Bunu DNX veya Preview 1'e geçirmek için kullanamazsınız, yani *project.json*-tabanlı projelerine MSBuild/csproj projelerine doğrudan.</span><span class="sxs-lookup"><span data-stu-id="d19d9-123">This means that you cannot use it to migrate DNX or Preview 1 *project.json*-based projects directly to MSBuild/csproj projects.</span></span> <span data-ttu-id="d19d9-124">Önce el ile projeyi Önizleme 2'ye geçirmek gereken *project.json*-tabanlı proje ve ardından `dotnet migrate` projeyi geçirmek için komutu.</span><span class="sxs-lookup"><span data-stu-id="d19d9-124">You first need to manually migrate the project to a Preview 2 *project.json*-based project and then use the `dotnet migrate` command to migrate the project.</span></span>

## <a name="arguments"></a><span data-ttu-id="d19d9-125">Arguments</span><span class="sxs-lookup"><span data-stu-id="d19d9-125">Arguments</span></span>

`PROJECT_JSON/GLOBAL_JSON/SOLUTION_FILE/PROJECT_DIR`

<span data-ttu-id="d19d9-126">Aşağıdakilerden birine yolu:</span><span class="sxs-lookup"><span data-stu-id="d19d9-126">The path to one of the following:</span></span>

* <span data-ttu-id="d19d9-127">bir *project.json* geçirmek için dosya.</span><span class="sxs-lookup"><span data-stu-id="d19d9-127">a *project.json* file to migrate.</span></span>
* <span data-ttu-id="d19d9-128">bir *global.json* dosya: Belirtilen klasörleri *global.json* geçirilir.</span><span class="sxs-lookup"><span data-stu-id="d19d9-128">a *global.json* file: the folders specified in *global.json* are migrated.</span></span>
* <span data-ttu-id="d19d9-129">bir *solution.sln* dosya: çözümde başvurulan projeler geçirilir.</span><span class="sxs-lookup"><span data-stu-id="d19d9-129">a *solution.sln* file: the projects referenced in the solution are migrated.</span></span>
* <span data-ttu-id="d19d9-130">geçiş için bir dizin: yinelemeli olarak arar *project.json* belirtilen dizinin içinde geçirmek için dosyaları.</span><span class="sxs-lookup"><span data-stu-id="d19d9-130">a directory to migrate: recursively searches for *project.json* files to migrate inside the specified directory.</span></span>

<span data-ttu-id="d19d9-131">Varsayılan olarak hiçbir şey belirtilmezse, geçerli dizin.</span><span class="sxs-lookup"><span data-stu-id="d19d9-131">Defaults to current directory if nothing is specified.</span></span>

## <a name="options"></a><span data-ttu-id="d19d9-132">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="d19d9-132">Options</span></span>

`--format-report-file-json <REPORT_FILE>`

<span data-ttu-id="d19d9-133">Geçiş raporu dosyasını kullanıcı yerine JSON iletileri olarak çıktı.</span><span class="sxs-lookup"><span data-stu-id="d19d9-133">Output migration report file as JSON rather than user messages.</span></span>

`-h|--help`

<span data-ttu-id="d19d9-134">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="d19d9-134">Prints out a short help for the command.</span></span>

`-r|--report-file <REPORT_FILE>`

<span data-ttu-id="d19d9-135">Bir dosyaya konsol ek olarak geçiş raporu çıktı.</span><span class="sxs-lookup"><span data-stu-id="d19d9-135">Output migration report to a file in addition to the console.</span></span>

`-s|--skip-project-references [Debug|Release]`

<span data-ttu-id="d19d9-136">Proje geçiş Atla başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="d19d9-136">Skip migrating project references.</span></span> <span data-ttu-id="d19d9-137">Varsayılan olarak, proje başvurularına geçirilen yinelemeli olarak olur.</span><span class="sxs-lookup"><span data-stu-id="d19d9-137">By default, project references are migrated recursively.</span></span>

`--skip-backup`

<span data-ttu-id="d19d9-138">Taşıma atla *project.json*, *global.json*, ve  *\*.xproj* için bir `backup` başarılı geçişten sonra dizin.</span><span class="sxs-lookup"><span data-stu-id="d19d9-138">Skip moving *project.json*, *global.json*, and *\*.xproj* to a `backup` directory after successful migration.</span></span>

`-t|--template-file <TEMPLATE_FILE>`

<span data-ttu-id="d19d9-139">Geçiş için kullanılacak şablonu csproj dosyasını.</span><span class="sxs-lookup"><span data-stu-id="d19d9-139">Template csproj file to use for migration.</span></span> <span data-ttu-id="d19d9-140">Varsayılan olarak, aynı şablonu bırakılan `dotnet new console` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d19d9-140">By default, the same template as the one dropped by `dotnet new console` is used.</span></span>

`-v|--sdk-package-version <VERSION>`

<span data-ttu-id="d19d9-141">Geçirilen uygulamada başvurulan sdk Paket sürümü.</span><span class="sxs-lookup"><span data-stu-id="d19d9-141">The version of the sdk package that's referenced in the migrated app.</span></span> <span data-ttu-id="d19d9-142">Varsayılan SDK sürümüdür `dotnet new`.</span><span class="sxs-lookup"><span data-stu-id="d19d9-142">The default is the version of the SDK in `dotnet new`.</span></span>

`-x|--xproj-file <FILE>`

<span data-ttu-id="d19d9-143">Kullanılacak xproj dosyanın yolu.</span><span class="sxs-lookup"><span data-stu-id="d19d9-143">The path to the xproj file to use.</span></span> <span data-ttu-id="d19d9-144">Proje dizininde birden fazla xproj olduğunda gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d19d9-144">Required when there is more than one xproj in a project directory.</span></span>

## <a name="examples"></a><span data-ttu-id="d19d9-145">Örnekler</span><span class="sxs-lookup"><span data-stu-id="d19d9-145">Examples</span></span>

<span data-ttu-id="d19d9-146">Bir projede geçerli dizin ve tüm proje ve proje bağımlılıklarını Geçir:</span><span class="sxs-lookup"><span data-stu-id="d19d9-146">Migrate a project in the current directory and all of its project-to-project dependencies:</span></span>

`dotnet migrate`

<span data-ttu-id="d19d9-147">Geçiş tüm projeleri *global.json* dosyası içerir:</span><span class="sxs-lookup"><span data-stu-id="d19d9-147">Migrate all projects that *global.json* file includes:</span></span>

`dotnet migrate path/to/global.json`

<span data-ttu-id="d19d9-148">Yalnızca geçerli proje ve proje proje (P2P) bağımlılık geçirin.</span><span class="sxs-lookup"><span data-stu-id="d19d9-148">Migrate only the current project and no project-to-project (P2P) dependencies.</span></span> <span data-ttu-id="d19d9-149">Ayrıca, belirli bir SDK'sı sürümünü kullanın:</span><span class="sxs-lookup"><span data-stu-id="d19d9-149">Also, use a specific SDK version:</span></span>

`dotnet migrate -s -v 1.0.0-preview4`
