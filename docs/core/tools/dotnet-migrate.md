---
title: DotNet geçiş komutu
description: DotNet Migrate komutu bir projeyi ve tüm bağımlılıklarını geçirir.
ms.date: 01/07/2020
ms.openlocfilehash: b81669d3e4cffeaf10bea39639410d5f06579d84
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734146"
---
# <a name="dotnet-migrate"></a><span data-ttu-id="1fb57-103">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="1fb57-103">dotnet migrate</span></span>

<span data-ttu-id="1fb57-104">**Bu makale için geçerlidir:** .NET Core 1. x SDK ✔️ .NET Core 2. x SDK ✔️</span><span class="sxs-lookup"><span data-stu-id="1fb57-104">**This article applies to:** ✔️ .NET Core 1.x SDK ✔️ .NET Core 2.x SDK</span></span>

## <a name="name"></a><span data-ttu-id="1fb57-105">Name</span><span class="sxs-lookup"><span data-stu-id="1fb57-105">Name</span></span>

<span data-ttu-id="1fb57-106">`dotnet migrate`-Preview 2 .NET Core projesini .NET Core SDK stili bir projeye geçirir.</span><span class="sxs-lookup"><span data-stu-id="1fb57-106">`dotnet migrate` - Migrates a Preview 2 .NET Core project to a .NET Core SDK-style project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="1fb57-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="1fb57-107">Synopsis</span></span>

```dotnetcli
dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [--format-report-file-json] [-r|--report-file] [-s|--skip-project-references] [--skip-backup] [-t|--template-file] [-v|--sdk-package-version] [-x|--xproj-file]
dotnet migrate [-h|--help]
```

## <a name="description"></a><span data-ttu-id="1fb57-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1fb57-108">Description</span></span>

<span data-ttu-id="1fb57-109">Bu komut kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="1fb57-109">This command is deprecated.</span></span> <span data-ttu-id="1fb57-110">`dotnet migrate` komutu artık .NET Core 3,0 SDK ile başlayarak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="1fb57-110">The `dotnet migrate` command is no longer available starting with .NET Core 3.0 SDK.</span></span> <span data-ttu-id="1fb57-111">Yalnızca bir Preview 2 .NET Core projesini, desteklenmeyen bir 1. x .NET Core projesine geçirebilirler.</span><span class="sxs-lookup"><span data-stu-id="1fb57-111">It can only migrate a Preview 2 .NET Core project to a 1.x .NET Core project, which is out of support.</span></span>

<span data-ttu-id="1fb57-112">Varsayılan olarak, komut kök projeyi ve kök projenin içerdiği tüm proje başvurularını geçirir.</span><span class="sxs-lookup"><span data-stu-id="1fb57-112">By default, the command migrates the root project and any project references that the root project contains.</span></span> <span data-ttu-id="1fb57-113">Bu davranış, çalışma zamanında `--skip-project-references` seçeneği kullanılarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="1fb57-113">This behavior is disabled using the `--skip-project-references` option at runtime.</span></span>

<span data-ttu-id="1fb57-114">Aşağıdaki varlıklarda geçiş yapılabilir:</span><span class="sxs-lookup"><span data-stu-id="1fb57-114">Migration can be performed on the following assets:</span></span>

* <span data-ttu-id="1fb57-115">Geçirilecek *Project. JSON* dosyasını belirterek tek bir proje.</span><span class="sxs-lookup"><span data-stu-id="1fb57-115">A single project by specifying the *project.json* file to migrate.</span></span>
* <span data-ttu-id="1fb57-116">Global. *json dosyasında bir* yolu geçirerek *Global. JSON* dosyasında belirtilen tüm dizinler.</span><span class="sxs-lookup"><span data-stu-id="1fb57-116">All of the directories specified in the *global.json* file by passing in a path to the *global.json* file.</span></span>
* <span data-ttu-id="1fb57-117">Çözümde başvurulan projeleri geçirirken *çözüm. sln* dosyası.</span><span class="sxs-lookup"><span data-stu-id="1fb57-117">A *solution.sln* file, where it migrates the projects referenced in the solution.</span></span>
* <span data-ttu-id="1fb57-118">Verilen dizinin tüm alt dizinlerinde özyinelemeli olarak.</span><span class="sxs-lookup"><span data-stu-id="1fb57-118">On all subdirectories of the given directory recursively.</span></span>

<span data-ttu-id="1fb57-119">`dotnet migrate` komutu geçirilmiş *proje. JSON* dosyasını, dizin yoksa oluşturduğu `backup` bir dizin içinde tutar.</span><span class="sxs-lookup"><span data-stu-id="1fb57-119">The `dotnet migrate` command keeps the migrated *project.json* file inside a `backup` directory, which it creates if the directory doesn't exist.</span></span> <span data-ttu-id="1fb57-120">Bu davranış, `--skip-backup` seçeneği kullanılarak geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="1fb57-120">This behavior is overridden using the `--skip-backup` option.</span></span>

<span data-ttu-id="1fb57-121">Varsayılan olarak, geçiş işlemi geçiş işleminin durumunu standart çıktıya (STDOUT) verir.</span><span class="sxs-lookup"><span data-stu-id="1fb57-121">By default, the migration operation outputs the state of the migration process to standard output (STDOUT).</span></span> <span data-ttu-id="1fb57-122">`--report-file <REPORT_FILE>` seçeneğini kullanırsanız, çıkış dosyaya kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="1fb57-122">If you use the `--report-file <REPORT_FILE>` option, the output is saved to the file specify.</span></span>

<span data-ttu-id="1fb57-123">`dotnet migrate` komutu yalnızca geçerli Preview 2 *Project. JSON*tabanlı projeleri destekler.</span><span class="sxs-lookup"><span data-stu-id="1fb57-123">The `dotnet migrate` command only supports valid Preview 2 *project.json*-based projects.</span></span> <span data-ttu-id="1fb57-124">Bu, DNX veya Preview 1 *Project. JSON*tabanlı projeleri doğrudan MSBuild/csproj projelerine geçirebileceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="1fb57-124">This means that you cannot use it to migrate DNX or Preview 1 *project.json*-based projects directly to MSBuild/csproj projects.</span></span> <span data-ttu-id="1fb57-125">Önce projeyi bir Preview 2 *Project. JSON*tabanlı projeye el ile geçirmeniz ve sonra `dotnet migrate` komutunu kullanarak projeyi geçirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1fb57-125">You first need to manually migrate the project to a Preview 2 *project.json*-based project and then use the `dotnet migrate` command to migrate the project.</span></span>

## <a name="arguments"></a><span data-ttu-id="1fb57-126">Arguments</span><span class="sxs-lookup"><span data-stu-id="1fb57-126">Arguments</span></span>

`PROJECT_JSON/GLOBAL_JSON/SOLUTION_FILE/PROJECT_DIR`

<span data-ttu-id="1fb57-127">Aşağıdakilerden birinin yolu:</span><span class="sxs-lookup"><span data-stu-id="1fb57-127">The path to one of the following:</span></span>

* <span data-ttu-id="1fb57-128">geçirilecek bir *Project. JSON* dosyası.</span><span class="sxs-lookup"><span data-stu-id="1fb57-128">a *project.json* file to migrate.</span></span>
* <span data-ttu-id="1fb57-129">*Global. JSON* dosyası: *Global. JSON* içinde belirtilen klasörler geçirilir.</span><span class="sxs-lookup"><span data-stu-id="1fb57-129">a *global.json* file: the folders specified in *global.json* are migrated.</span></span>
* <span data-ttu-id="1fb57-130">bir *çözüm. sln* dosyası: çözümde başvurulan projeler geçirilir.</span><span class="sxs-lookup"><span data-stu-id="1fb57-130">a *solution.sln* file: the projects referenced in the solution are migrated.</span></span>
* <span data-ttu-id="1fb57-131">geçirilecek Dizin: özyinelemeli olarak *Project. JSON* dosyalarını belirtilen dizin içinde geçirilecek şekilde arar.</span><span class="sxs-lookup"><span data-stu-id="1fb57-131">a directory to migrate: recursively searches for *project.json* files to migrate inside the specified directory.</span></span>

<span data-ttu-id="1fb57-132">Hiçbir şey belirtilmemişse, varsayılan olarak geçerli dizine ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="1fb57-132">Defaults to current directory if nothing is specified.</span></span>

## <a name="options"></a><span data-ttu-id="1fb57-133">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="1fb57-133">Options</span></span>

`--format-report-file-json <REPORT_FILE>`

<span data-ttu-id="1fb57-134">Geçiş raporu dosyasını kullanıcı iletileri yerine JSON olarak çıkar.</span><span class="sxs-lookup"><span data-stu-id="1fb57-134">Output migration report file as JSON rather than user messages.</span></span>

`-h|--help`

<span data-ttu-id="1fb57-135">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="1fb57-135">Prints out a short help for the command.</span></span>

`-r|--report-file <REPORT_FILE>`

<span data-ttu-id="1fb57-136">Konsola ek olarak çıkış geçiş raporu.</span><span class="sxs-lookup"><span data-stu-id="1fb57-136">Output migration report to a file in addition to the console.</span></span>

`-s|--skip-project-references [Debug|Release]`

<span data-ttu-id="1fb57-137">Proje başvurularını geçirmeyi atlayın.</span><span class="sxs-lookup"><span data-stu-id="1fb57-137">Skip migrating project references.</span></span> <span data-ttu-id="1fb57-138">Varsayılan olarak, proje başvuruları yinelemeli olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="1fb57-138">By default, project references are migrated recursively.</span></span>

`--skip-backup`

<span data-ttu-id="1fb57-139">Başarılı geçişten sonra *Project. JSON*, *Global. JSON*ve *\*. xproj* ' ı bir `backup` dizinine taşımayı atlayın.</span><span class="sxs-lookup"><span data-stu-id="1fb57-139">Skip moving *project.json*, *global.json*, and *\*.xproj* to a `backup` directory after successful migration.</span></span>

`-t|--template-file <TEMPLATE_FILE>`

<span data-ttu-id="1fb57-140">Geçiş için kullanılacak şablon csproj dosyası.</span><span class="sxs-lookup"><span data-stu-id="1fb57-140">Template csproj file to use for migration.</span></span> <span data-ttu-id="1fb57-141">Varsayılan olarak, `dotnet new console` tarafından bırakılan şablonla aynı şablon kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1fb57-141">By default, the same template as the one dropped by `dotnet new console` is used.</span></span>

`-v|--sdk-package-version <VERSION>`

<span data-ttu-id="1fb57-142">Geçirilen uygulamada başvurulan SDK paketinin sürümü.</span><span class="sxs-lookup"><span data-stu-id="1fb57-142">The version of the sdk package that's referenced in the migrated app.</span></span> <span data-ttu-id="1fb57-143">Varsayılan değer `dotnet new`SDK 'nın sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="1fb57-143">The default is the version of the SDK in `dotnet new`.</span></span>

`-x|--xproj-file <FILE>`

<span data-ttu-id="1fb57-144">Kullanılacak xproj dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="1fb57-144">The path to the xproj file to use.</span></span> <span data-ttu-id="1fb57-145">Proje dizininde birden fazla xproj olduğunda gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1fb57-145">Required when there is more than one xproj in a project directory.</span></span>

## <a name="examples"></a><span data-ttu-id="1fb57-146">Örnekler</span><span class="sxs-lookup"><span data-stu-id="1fb57-146">Examples</span></span>

<span data-ttu-id="1fb57-147">Geçerli dizindeki bir projeyi ve projenin tüm proje bağımlılıklarını geçirin:</span><span class="sxs-lookup"><span data-stu-id="1fb57-147">Migrate a project in the current directory and all of its project-to-project dependencies:</span></span>

`dotnet migrate`

<span data-ttu-id="1fb57-148">*Global. JSON* dosyasının içerdiği tüm projeleri geçirin:</span><span class="sxs-lookup"><span data-stu-id="1fb57-148">Migrate all projects that *global.json* file includes:</span></span>

`dotnet migrate path/to/global.json`

<span data-ttu-id="1fb57-149">Yalnızca geçerli projeyi geçirin ve projeden projeye (P2P) bağımlılıkları yoktur.</span><span class="sxs-lookup"><span data-stu-id="1fb57-149">Migrate only the current project and no project-to-project (P2P) dependencies.</span></span> <span data-ttu-id="1fb57-150">Ayrıca, belirli bir SDK sürümünü kullanın:</span><span class="sxs-lookup"><span data-stu-id="1fb57-150">Also, use a specific SDK version:</span></span>

`dotnet migrate -s -v 1.0.0-preview4`
