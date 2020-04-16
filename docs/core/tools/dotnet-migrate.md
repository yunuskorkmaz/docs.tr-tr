---
title: dotnet geçiş komutu
description: Dotnet geçir komutu bir projeyi ve tüm bağımlılıklarını geçirmektedir.
ms.date: 02/14/2020
ms.openlocfilehash: 71f587c1bfadd445aca818448bdd5f136f009fe0
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463632"
---
# <a name="dotnet-migrate"></a><span data-ttu-id="60370-103">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="60370-103">dotnet migrate</span></span>

<span data-ttu-id="60370-104">**Bu makale şu şekilde dir:** ✔️ .NET Core 2.x SDK</span><span class="sxs-lookup"><span data-stu-id="60370-104">**This article applies to:** ✔️ .NET Core 2.x SDK</span></span>

## <a name="name"></a><span data-ttu-id="60370-105">Adı</span><span class="sxs-lookup"><span data-stu-id="60370-105">Name</span></span>

<span data-ttu-id="60370-106">`dotnet migrate`- Önizleme 2 .NET Core projesini .NET Core SDK tarzı bir projeye geçirin.</span><span class="sxs-lookup"><span data-stu-id="60370-106">`dotnet migrate` - Migrates a Preview 2 .NET Core project to a .NET Core SDK-style project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="60370-107">Özet</span><span class="sxs-lookup"><span data-stu-id="60370-107">Synopsis</span></span>

```dotnetcli
dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [--format-report-file-json <REPORT_FILE>]
    [-r|--report-file <REPORT_FILE>] [-s|--skip-project-references [Debug|Release]]
    [--skip-backup] [-t|--template-file <TEMPLATE_FILE>] [-v|--sdk-package-version]
    [-x|--xproj-file]

dotnet migrate -h|--help
```

## <a name="description"></a><span data-ttu-id="60370-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="60370-108">Description</span></span>

<span data-ttu-id="60370-109">Bu komut küçümsüyor.</span><span class="sxs-lookup"><span data-stu-id="60370-109">This command is deprecated.</span></span> <span data-ttu-id="60370-110">Komut `dotnet migrate` artık .NET Core 3.0 SDK ile başlayarak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="60370-110">The `dotnet migrate` command is no longer available starting with .NET Core 3.0 SDK.</span></span> <span data-ttu-id="60370-111">Yalnızca Önizleme 2 .NET Core projesini destek dışı olan 1.x .NET Core projesine geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60370-111">It can only migrate a Preview 2 .NET Core project to a 1.x .NET Core project, which is out of support.</span></span>

<span data-ttu-id="60370-112">Varsayılan olarak, komut kök projeyi ve kök projenin içerdiği proje başvurularını geçirmektedir.</span><span class="sxs-lookup"><span data-stu-id="60370-112">By default, the command migrates the root project and any project references that the root project contains.</span></span> <span data-ttu-id="60370-113">Bu davranış, çalışma `--skip-project-references` zamanında seçeneği kullanılarak devre dışı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="60370-113">This behavior is disabled using the `--skip-project-references` option at runtime.</span></span>

<span data-ttu-id="60370-114">Geçiş aşağıdaki varlıklar üzerinde gerçekleştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="60370-114">Migration can be performed on the following assets:</span></span>

* <span data-ttu-id="60370-115">Tek bir proje *project.json* dosyasını belirterek geçirin.</span><span class="sxs-lookup"><span data-stu-id="60370-115">A single project by specifying the *project.json* file to migrate.</span></span>
* <span data-ttu-id="60370-116">Global.json dosyasında belirtilen tüm dizinler *global.json* dosyasına giden bir yoldan geçerek. *global.json*</span><span class="sxs-lookup"><span data-stu-id="60370-116">All of the directories specified in the *global.json* file by passing in a path to the *global.json* file.</span></span>
* <span data-ttu-id="60370-117">Çözümde başvurulan projeleri geçirdiği bir *solution.sln* dosyası.</span><span class="sxs-lookup"><span data-stu-id="60370-117">A *solution.sln* file, where it migrates the projects referenced in the solution.</span></span>
* <span data-ttu-id="60370-118">Verilen dizinin tüm alt dizilişlerinde özyinelemeli olarak.</span><span class="sxs-lookup"><span data-stu-id="60370-118">On all subdirectories of the given directory recursively.</span></span>

<span data-ttu-id="60370-119">Komut, `dotnet migrate` geçirilen *project.json* dosyasını `backup` dizin yoksa oluşturduğu bir dizinin içinde tutar.</span><span class="sxs-lookup"><span data-stu-id="60370-119">The `dotnet migrate` command keeps the migrated *project.json* file inside a `backup` directory, which it creates if the directory doesn't exist.</span></span> <span data-ttu-id="60370-120">Bu davranış `--skip-backup` seçeneği kullanılarak geçersiz kılındı.</span><span class="sxs-lookup"><span data-stu-id="60370-120">This behavior is overridden using the `--skip-backup` option.</span></span>

<span data-ttu-id="60370-121">Varsayılan olarak, geçiş işlemi geçiş işleminin durumunu standart çıktıya (STDOUT) çıkarır.</span><span class="sxs-lookup"><span data-stu-id="60370-121">By default, the migration operation outputs the state of the migration process to standard output (STDOUT).</span></span> <span data-ttu-id="60370-122">`--report-file <REPORT_FILE>` Seçeneği kullanırsanız, çıktı belirtin dosyaya kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="60370-122">If you use the `--report-file <REPORT_FILE>` option, the output is saved to the file specify.</span></span>

<span data-ttu-id="60370-123">Komut `dotnet migrate` yalnızca geçerli Preview 2 *project.json*tabanlı projeleri destekler.</span><span class="sxs-lookup"><span data-stu-id="60370-123">The `dotnet migrate` command only supports valid Preview 2 *project.json*-based projects.</span></span> <span data-ttu-id="60370-124">Bu, DNX veya Preview 1 *project.json*tabanlı projeleri doğrudan MSBuild/csproj projelerine geçirmek için kullanamayacağınız anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="60370-124">This means that you cannot use it to migrate DNX or Preview 1 *project.json*-based projects directly to MSBuild/csproj projects.</span></span> <span data-ttu-id="60370-125">Önce projeyi önizleme 2 *project.json*tabanlı projeye el ile geçirmeniz `dotnet migrate` ve ardından projeyi geçirmek için komutu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="60370-125">You first need to manually migrate the project to a Preview 2 *project.json*-based project and then use the `dotnet migrate` command to migrate the project.</span></span>

## <a name="arguments"></a><span data-ttu-id="60370-126">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="60370-126">Arguments</span></span>

`PROJECT_JSON/GLOBAL_JSON/SOLUTION_FILE/PROJECT_DIR`

<span data-ttu-id="60370-127">Aşağıdakilerden birine giden yol:</span><span class="sxs-lookup"><span data-stu-id="60370-127">The path to one of the following:</span></span>

* <span data-ttu-id="60370-128">bir *project.json* dosyası geçiş için.</span><span class="sxs-lookup"><span data-stu-id="60370-128">a *project.json* file to migrate.</span></span>
* <span data-ttu-id="60370-129">global.json dosyası: *global.json'da* belirtilen klasörler geçirilir. *global.json*</span><span class="sxs-lookup"><span data-stu-id="60370-129">a *global.json* file: the folders specified in *global.json* are migrated.</span></span>
* <span data-ttu-id="60370-130">*solution.sln* dosyası: çözümde başvurulan projeler geçirilir.</span><span class="sxs-lookup"><span data-stu-id="60370-130">a *solution.sln* file: the projects referenced in the solution are migrated.</span></span>
* <span data-ttu-id="60370-131">geçirilen bir dizin: belirtilen dizinin içinde geçiş yapmak için *project.json* dosyalarını özyinelemeli olarak arar.</span><span class="sxs-lookup"><span data-stu-id="60370-131">a directory to migrate: recursively searches for *project.json* files to migrate inside the specified directory.</span></span>

<span data-ttu-id="60370-132">Hiçbir şey belirtilmemişse, varsayılan olarak geçerli dizini alır.</span><span class="sxs-lookup"><span data-stu-id="60370-132">Defaults to current directory if nothing is specified.</span></span>

## <a name="options"></a><span data-ttu-id="60370-133">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="60370-133">Options</span></span>

`--format-report-file-json <REPORT_FILE>`

<span data-ttu-id="60370-134">Kullanıcı iletileri yerine JSON olarak çıktı geçiş raporu dosyası.</span><span class="sxs-lookup"><span data-stu-id="60370-134">Output migration report file as JSON rather than user messages.</span></span>

`-h|--help`

<span data-ttu-id="60370-135">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="60370-135">Prints out a short help for the command.</span></span>

`-r|--report-file <REPORT_FILE>`

<span data-ttu-id="60370-136">Konsola ek olarak bir dosyaya geçiş raporu çıktı.</span><span class="sxs-lookup"><span data-stu-id="60370-136">Output migration report to a file in addition to the console.</span></span>

`-s|--skip-project-references [Debug|Release]`

<span data-ttu-id="60370-137">Geçiş proje başvurularını atlayın.</span><span class="sxs-lookup"><span data-stu-id="60370-137">Skip migrating project references.</span></span> <span data-ttu-id="60370-138">Varsayılan olarak, proje başvuruları özyinelemeli olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="60370-138">By default, project references are migrated recursively.</span></span>

`--skip-backup`

<span data-ttu-id="60370-139">Başarılı *geçişten sonra project.json,* *global.json*ve `backup` \* \*.xproj'u\* bir dizine taşıyın.</span><span class="sxs-lookup"><span data-stu-id="60370-139">Skip moving *project.json*, *global.json*, and *\*.xproj* to a `backup` directory after successful migration.</span></span>

`-t|--template-file <TEMPLATE_FILE>`

<span data-ttu-id="60370-140">Geçiş için kullanılacak csproj dosyasını şablonleyin.</span><span class="sxs-lookup"><span data-stu-id="60370-140">Template csproj file to use for migration.</span></span> <span data-ttu-id="60370-141">Varsayılan olarak, bırakılan `dotnet new console` şablonla aynı şablon kullanılır.</span><span class="sxs-lookup"><span data-stu-id="60370-141">By default, the same template as the one dropped by `dotnet new console` is used.</span></span>

`-v|--sdk-package-version <VERSION>`

<span data-ttu-id="60370-142">Geçirilen uygulamada başvurulan sdk paketinin sürümü.</span><span class="sxs-lookup"><span data-stu-id="60370-142">The version of the sdk package that's referenced in the migrated app.</span></span> <span data-ttu-id="60370-143">Varsayılan sdk `dotnet new`sürümü.</span><span class="sxs-lookup"><span data-stu-id="60370-143">The default is the version of the SDK in `dotnet new`.</span></span>

`-x|--xproj-file <FILE>`

<span data-ttu-id="60370-144">Xproj dosyasına giden yol.</span><span class="sxs-lookup"><span data-stu-id="60370-144">The path to the xproj file to use.</span></span> <span data-ttu-id="60370-145">Bir proje dizininde birden fazla xproj olduğunda gereklidir.</span><span class="sxs-lookup"><span data-stu-id="60370-145">Required when there is more than one xproj in a project directory.</span></span>

## <a name="examples"></a><span data-ttu-id="60370-146">Örnekler</span><span class="sxs-lookup"><span data-stu-id="60370-146">Examples</span></span>

<span data-ttu-id="60370-147">Bir projeyi geçerli dizinde ve projeden projeye tüm bağımlılıklarında geçirin:</span><span class="sxs-lookup"><span data-stu-id="60370-147">Migrate a project in the current directory and all of its project-to-project dependencies:</span></span>

`dotnet migrate`

<span data-ttu-id="60370-148">*global.json* dosyasının içerdiği tüm projeleri geçirin:</span><span class="sxs-lookup"><span data-stu-id="60370-148">Migrate all projects that *global.json* file includes:</span></span>

`dotnet migrate path/to/global.json`

<span data-ttu-id="60370-149">Yalnızca geçerli projeyi geçirin ve projeden projeye (P2P) bağımlılıklar yapmayın.</span><span class="sxs-lookup"><span data-stu-id="60370-149">Migrate only the current project and no project-to-project (P2P) dependencies.</span></span> <span data-ttu-id="60370-150">Ayrıca, belirli bir SDK sürümünü kullanın:</span><span class="sxs-lookup"><span data-stu-id="60370-150">Also, use a specific SDK version:</span></span>

`dotnet migrate -s -v 1.0.0-preview4`
