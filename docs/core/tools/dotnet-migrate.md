---
title: DotNet geçiş komutu
description: DotNet Migrate komutu bir projeyi ve tüm bağımlılıklarını geçirir.
ms.date: 08/08/2019
ms.openlocfilehash: afc16161761d151e743e53a8572a6564add43517
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117696"
---
# <a name="dotnet-migrate"></a><span data-ttu-id="8de70-103">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="8de70-103">dotnet migrate</span></span>

<span data-ttu-id="8de70-104">**Bu makale şu şekilde geçerlidir: ✓** .NET Core 1. x SDK **✓** .NET Core 2. x SDK</span><span class="sxs-lookup"><span data-stu-id="8de70-104">**This article applies to: ✓** .NET Core 1.x SDK **✓** .NET Core 2.x SDK</span></span>

## <a name="name"></a><span data-ttu-id="8de70-105">Ad</span><span class="sxs-lookup"><span data-stu-id="8de70-105">Name</span></span>

<span data-ttu-id="8de70-106">`dotnet migrate`-Preview 2 .NET Core projesini .NET Core SDK stilinde bir projeye geçirir.</span><span class="sxs-lookup"><span data-stu-id="8de70-106">`dotnet migrate` - Migrates a Preview 2 .NET Core project to a .NET Core SDK-style project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="8de70-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="8de70-107">Synopsis</span></span>

```dotnetcli
dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [--format-report-file-json] [-r|--report-file] [-s|--skip-project-references] [--skip-backup] [-t|--template-file] [-v|--sdk-package-version] [-x|--xproj-file]
dotnet migrate [-h|--help]
```

## <a name="description"></a><span data-ttu-id="8de70-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8de70-108">Description</span></span>

<span data-ttu-id="8de70-109">Komutu geçerli bir Preview 2 *Project. JSON*tabanlı projeyi geçerli bir .NET Core SDK stili csproj projesine geçirir. `dotnet migrate`</span><span class="sxs-lookup"><span data-stu-id="8de70-109">The `dotnet migrate` command migrates a valid Preview 2 *project.json*-based project to a valid .NET Core SDK-style *csproj* project.</span></span>

<span data-ttu-id="8de70-110">Varsayılan olarak, komut kök projeyi ve kök projenin içerdiği tüm proje başvurularını geçirir.</span><span class="sxs-lookup"><span data-stu-id="8de70-110">By default, the command migrates the root project and any project references that the root project contains.</span></span> <span data-ttu-id="8de70-111">Bu davranış, `--skip-project-references` çalışma zamanında seçeneği kullanılarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="8de70-111">This behavior is disabled using the `--skip-project-references` option at runtime.</span></span>

<span data-ttu-id="8de70-112">Aşağıdaki varlıklarda geçiş yapılabilir:</span><span class="sxs-lookup"><span data-stu-id="8de70-112">Migration can be performed on the following assets:</span></span>

* <span data-ttu-id="8de70-113">Geçirilecek *Project. JSON* dosyasını belirterek tek bir proje.</span><span class="sxs-lookup"><span data-stu-id="8de70-113">A single project by specifying the *project.json* file to migrate.</span></span>
* <span data-ttu-id="8de70-114">Global. *json dosyasında bir* yolu geçirerek *Global. JSON* dosyasında belirtilen tüm dizinler.</span><span class="sxs-lookup"><span data-stu-id="8de70-114">All of the directories specified in the *global.json* file by passing in a path to the *global.json* file.</span></span>
* <span data-ttu-id="8de70-115">Çözümde başvurulan projeleri geçirirken *çözüm. sln* dosyası.</span><span class="sxs-lookup"><span data-stu-id="8de70-115">A *solution.sln* file, where it migrates the projects referenced in the solution.</span></span>
* <span data-ttu-id="8de70-116">Verilen dizinin tüm alt dizinlerinde özyinelemeli olarak.</span><span class="sxs-lookup"><span data-stu-id="8de70-116">On all subdirectories of the given directory recursively.</span></span>

<span data-ttu-id="8de70-117">Komut, geçirilen *Project. JSON* dosyasını dizin yoksa oluşturduğu bir `backup` dizin içinde tutar. `dotnet migrate`</span><span class="sxs-lookup"><span data-stu-id="8de70-117">The `dotnet migrate` command keeps the migrated *project.json* file inside a `backup` directory, which it creates if the directory doesn't exist.</span></span> <span data-ttu-id="8de70-118">Bu davranış `--skip-backup` seçeneği kullanılarak geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="8de70-118">This behavior is overridden using the `--skip-backup` option.</span></span>

<span data-ttu-id="8de70-119">Varsayılan olarak, geçiş işlemi geçiş işleminin durumunu standart çıktıya (STDOUT) verir.</span><span class="sxs-lookup"><span data-stu-id="8de70-119">By default, the migration operation outputs the state of the migration process to standard output (STDOUT).</span></span> <span data-ttu-id="8de70-120">`--report-file <REPORT_FILE>` Seçeneğini kullanırsanız, çıkış dosyaya kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="8de70-120">If you use the `--report-file <REPORT_FILE>` option, the output is saved to the file specify.</span></span>

<span data-ttu-id="8de70-121">Komutu yalnızca geçerli Preview 2 *Project. JSON*tabanlı projeleri destekler. `dotnet migrate`</span><span class="sxs-lookup"><span data-stu-id="8de70-121">The `dotnet migrate` command only supports valid Preview 2 *project.json*-based projects.</span></span> <span data-ttu-id="8de70-122">Bu, DNX veya Preview 1 *Project. JSON*tabanlı projeleri doğrudan MSBuild/csproj projelerine geçirebileceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="8de70-122">This means that you cannot use it to migrate DNX or Preview 1 *project.json*-based projects directly to MSBuild/csproj projects.</span></span> <span data-ttu-id="8de70-123">Önce projeyi bir Preview 2 *Project. JSON*tabanlı projeye el ile geçirmeniz ve ardından projeyi geçirmek için `dotnet migrate` komutunu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8de70-123">You first need to manually migrate the project to a Preview 2 *project.json*-based project and then use the `dotnet migrate` command to migrate the project.</span></span>

<span data-ttu-id="8de70-124">`dotnet migrate` Komut artık .NET Core 3,0 SDK ile başlayarak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="8de70-124">The `dotnet migrate` command is no longer available starting with .NET Core 3.0 SDK.</span></span>

## <a name="arguments"></a><span data-ttu-id="8de70-125">Arguments</span><span class="sxs-lookup"><span data-stu-id="8de70-125">Arguments</span></span>

`PROJECT_JSON/GLOBAL_JSON/SOLUTION_FILE/PROJECT_DIR`

<span data-ttu-id="8de70-126">Aşağıdakilerden birinin yolu:</span><span class="sxs-lookup"><span data-stu-id="8de70-126">The path to one of the following:</span></span>

* <span data-ttu-id="8de70-127">geçirilecek bir *Project. JSON* dosyası.</span><span class="sxs-lookup"><span data-stu-id="8de70-127">a *project.json* file to migrate.</span></span>
* <span data-ttu-id="8de70-128">*Global. JSON* dosyası: *Global. JSON* içinde belirtilen klasörler geçirilir.</span><span class="sxs-lookup"><span data-stu-id="8de70-128">a *global.json* file: the folders specified in *global.json* are migrated.</span></span>
* <span data-ttu-id="8de70-129">bir *çözüm. sln* dosyası: çözümde başvurulan projeler geçirilir.</span><span class="sxs-lookup"><span data-stu-id="8de70-129">a *solution.sln* file: the projects referenced in the solution are migrated.</span></span>
* <span data-ttu-id="8de70-130">geçirilecek Dizin: özyinelemeli olarak *Project. JSON* dosyalarını belirtilen dizin içinde geçirilecek şekilde arar.</span><span class="sxs-lookup"><span data-stu-id="8de70-130">a directory to migrate: recursively searches for *project.json* files to migrate inside the specified directory.</span></span>

<span data-ttu-id="8de70-131">Hiçbir şey belirtilmemişse, varsayılan olarak geçerli dizine ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="8de70-131">Defaults to current directory if nothing is specified.</span></span>

## <a name="options"></a><span data-ttu-id="8de70-132">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="8de70-132">Options</span></span>

`--format-report-file-json <REPORT_FILE>`

<span data-ttu-id="8de70-133">Geçiş raporu dosyasını kullanıcı iletileri yerine JSON olarak çıkar.</span><span class="sxs-lookup"><span data-stu-id="8de70-133">Output migration report file as JSON rather than user messages.</span></span>

`-h|--help`

<span data-ttu-id="8de70-134">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="8de70-134">Prints out a short help for the command.</span></span>

`-r|--report-file <REPORT_FILE>`

<span data-ttu-id="8de70-135">Konsola ek olarak çıkış geçiş raporu.</span><span class="sxs-lookup"><span data-stu-id="8de70-135">Output migration report to a file in addition to the console.</span></span>

`-s|--skip-project-references [Debug|Release]`

<span data-ttu-id="8de70-136">Proje başvurularını geçirmeyi atlayın.</span><span class="sxs-lookup"><span data-stu-id="8de70-136">Skip migrating project references.</span></span> <span data-ttu-id="8de70-137">Varsayılan olarak, proje başvuruları yinelemeli olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="8de70-137">By default, project references are migrated recursively.</span></span>

`--skip-backup`

<span data-ttu-id="8de70-138">Başarılı geçişten sonra *Project. JSON*, *Global. JSON*ve  *\*. xproj* ' ı `backup` bir dizine taşımayı atlayın.</span><span class="sxs-lookup"><span data-stu-id="8de70-138">Skip moving *project.json*, *global.json*, and *\*.xproj* to a `backup` directory after successful migration.</span></span>

`-t|--template-file <TEMPLATE_FILE>`

<span data-ttu-id="8de70-139">Geçiş için kullanılacak şablon csproj dosyası.</span><span class="sxs-lookup"><span data-stu-id="8de70-139">Template csproj file to use for migration.</span></span> <span data-ttu-id="8de70-140">Varsayılan olarak, tarafından bırakılan ile `dotnet new console` aynı şablon kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8de70-140">By default, the same template as the one dropped by `dotnet new console` is used.</span></span>

`-v|--sdk-package-version <VERSION>`

<span data-ttu-id="8de70-141">Geçirilen uygulamada başvurulan SDK paketinin sürümü.</span><span class="sxs-lookup"><span data-stu-id="8de70-141">The version of the sdk package that's referenced in the migrated app.</span></span> <span data-ttu-id="8de70-142">Varsayılan, ' deki `dotnet new`SDK sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="8de70-142">The default is the version of the SDK in `dotnet new`.</span></span>

`-x|--xproj-file <FILE>`

<span data-ttu-id="8de70-143">Kullanılacak xproj dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="8de70-143">The path to the xproj file to use.</span></span> <span data-ttu-id="8de70-144">Proje dizininde birden fazla xproj olduğunda gereklidir.</span><span class="sxs-lookup"><span data-stu-id="8de70-144">Required when there is more than one xproj in a project directory.</span></span>

## <a name="examples"></a><span data-ttu-id="8de70-145">Örnekler</span><span class="sxs-lookup"><span data-stu-id="8de70-145">Examples</span></span>

<span data-ttu-id="8de70-146">Geçerli dizindeki bir projeyi ve projenin tüm proje bağımlılıklarını geçirin:</span><span class="sxs-lookup"><span data-stu-id="8de70-146">Migrate a project in the current directory and all of its project-to-project dependencies:</span></span>

`dotnet migrate`

<span data-ttu-id="8de70-147">*Global. JSON* dosyasının içerdiği tüm projeleri geçirin:</span><span class="sxs-lookup"><span data-stu-id="8de70-147">Migrate all projects that *global.json* file includes:</span></span>

`dotnet migrate path/to/global.json`

<span data-ttu-id="8de70-148">Yalnızca geçerli projeyi geçirin ve projeden projeye (P2P) bağımlılıkları yoktur.</span><span class="sxs-lookup"><span data-stu-id="8de70-148">Migrate only the current project and no project-to-project (P2P) dependencies.</span></span> <span data-ttu-id="8de70-149">Ayrıca, belirli bir SDK sürümünü kullanın:</span><span class="sxs-lookup"><span data-stu-id="8de70-149">Also, use a specific SDK version:</span></span>

`dotnet migrate -s -v 1.0.0-preview4`
