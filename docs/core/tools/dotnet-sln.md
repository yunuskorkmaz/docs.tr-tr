---
title: DotNet sln komutu
description: DotNet-sln komutu bir çözüm dosyasındaki projeleri eklemek, kaldırmak ve listelemek için kullanışlı bir seçenek sağlar.
ms.date: 10/29/2019
ms.openlocfilehash: e344deaae0867202a79a3c38df48a2be8d4d7d13
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733076"
---
# <a name="dotnet-sln"></a><span data-ttu-id="5cdf9-103">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="5cdf9-103">dotnet sln</span></span>

<span data-ttu-id="5cdf9-104">**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 1. x SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="5cdf9-104">**This article applies to:** ✔️ .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="5cdf9-105">Name</span><span class="sxs-lookup"><span data-stu-id="5cdf9-105">Name</span></span>

<span data-ttu-id="5cdf9-106">`dotnet sln`-bir .NET Core çözüm dosyasını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="5cdf9-106">`dotnet sln` - Modifies a .NET Core solution file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5cdf9-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="5cdf9-107">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] [command] [-h|--help]
```

## <a name="description"></a><span data-ttu-id="5cdf9-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5cdf9-108">Description</span></span>

<span data-ttu-id="5cdf9-109">`dotnet sln` komutu bir çözüm dosyasındaki projeleri eklemek, kaldırmak ve listelemek için kullanışlı bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="5cdf9-109">The `dotnet sln` command provides a convenient way to add, remove, and list projects in a solution file.</span></span>

<span data-ttu-id="5cdf9-110">`dotnet sln` komutunu kullanmak için, çözüm dosyası zaten var olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5cdf9-110">To use the `dotnet sln` command, the solution file must already exist.</span></span> <span data-ttu-id="5cdf9-111">Bir tane oluşturmanız gerekiyorsa, aşağıdaki örnekte olduğu gibi [DotNet New](dotnet-new.md) komutunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="5cdf9-111">If you need to create one, use the [dotnet new](dotnet-new.md) command, like in the following example:</span></span>

```dotnetcli
dotnet new sln
```

## <a name="arguments"></a><span data-ttu-id="5cdf9-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="5cdf9-112">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="5cdf9-113">Kullanılacak çözüm dosyası.</span><span class="sxs-lookup"><span data-stu-id="5cdf9-113">The solution file to use.</span></span> <span data-ttu-id="5cdf9-114">Belirtilmemişse, komut geçerli dizinde bir arama yapar.</span><span class="sxs-lookup"><span data-stu-id="5cdf9-114">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="5cdf9-115">Dizinde birden çok çözüm dosyası varsa, birinin belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="5cdf9-115">If there are multiple solution files in the directory, one must be specified.</span></span>

## <a name="options"></a><span data-ttu-id="5cdf9-116">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="5cdf9-116">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="5cdf9-117">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="5cdf9-117">Prints out a short help for the command.</span></span>

## <a name="commands"></a><span data-ttu-id="5cdf9-118">Komutlar</span><span class="sxs-lookup"><span data-stu-id="5cdf9-118">Commands</span></span>

### `add`

<span data-ttu-id="5cdf9-119">Çözüm dosyasına bir proje veya birden çok proje ekler.</span><span class="sxs-lookup"><span data-stu-id="5cdf9-119">Adds a project or multiple projects to the solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="5cdf9-120">Özeti</span><span class="sxs-lookup"><span data-stu-id="5cdf9-120">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] add [--in-root] [-s|--solution-folder] <PROJECT_PATH>
dotnet sln add [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="5cdf9-121">Arguments</span><span class="sxs-lookup"><span data-stu-id="5cdf9-121">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="5cdf9-122">Kullanılacak çözüm dosyası.</span><span class="sxs-lookup"><span data-stu-id="5cdf9-122">The solution file to use.</span></span> <span data-ttu-id="5cdf9-123">Belirtilmemişse, komut geçerli dizinde bir arama yapar.</span><span class="sxs-lookup"><span data-stu-id="5cdf9-123">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="5cdf9-124">Dizinde birden çok çözüm dosyası varsa, birinin belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="5cdf9-124">If there are multiple solution files in the directory, one must be specified.</span></span>

- **`PROJECT_PATH`**

  <span data-ttu-id="5cdf9-125">Çözüme eklenecek projenin yolu.</span><span class="sxs-lookup"><span data-stu-id="5cdf9-125">The path to the project to add to the solution.</span></span> <span data-ttu-id="5cdf9-126">Boşluktan daha sonra bir tane ekleyerek birden fazla proje ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5cdf9-126">Add multiple projects by adding one after the other separated by spaces.</span></span> <span data-ttu-id="5cdf9-127">UNIX/Linux kabuğu [Glob model](https://en.wikipedia.org/wiki/Glob_(programming)) genişletmeleri `dotnet sln` komutu tarafından doğru şekilde işlenir.</span><span class="sxs-lookup"><span data-stu-id="5cdf9-127">Unix/Linux shell [globbing pattern](https://en.wikipedia.org/wiki/Glob_(programming)) expansions are processed correctly by the `dotnet sln` command.</span></span>

#### <a name="options"></a><span data-ttu-id="5cdf9-128">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="5cdf9-128">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="5cdf9-129">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="5cdf9-129">Prints out a short help for the command.</span></span>

- **`--in-root`**

  <span data-ttu-id="5cdf9-130">Bir çözüm klasörü oluşturmak yerine, projeleri çözümün köküne koyar.</span><span class="sxs-lookup"><span data-stu-id="5cdf9-130">Places the projects in the root of the solution, rather than creating a solution folder.</span></span> <span data-ttu-id="5cdf9-131">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5cdf9-131">Available since .NET Core 3.0 SDK.</span></span>

- **`-s|--solution-folder`**

  <span data-ttu-id="5cdf9-132">Projelerin ekleneceği hedef çözüm klasörünün yolu.</span><span class="sxs-lookup"><span data-stu-id="5cdf9-132">The destination solution folder path to add the projects to.</span></span> <span data-ttu-id="5cdf9-133">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5cdf9-133">Available since .NET Core 3.0 SDK.</span></span>

### `remove`

<span data-ttu-id="5cdf9-134">Çözüm dosyasından bir projeyi veya birden çok projeyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="5cdf9-134">Removes a project or multiple projects from the solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="5cdf9-135">Özeti</span><span class="sxs-lookup"><span data-stu-id="5cdf9-135">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] remove <PROJECT_PATH>
dotnet sln [<SOLUTION_FILE>] remove [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="5cdf9-136">Arguments</span><span class="sxs-lookup"><span data-stu-id="5cdf9-136">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="5cdf9-137">Kullanılacak çözüm dosyası.</span><span class="sxs-lookup"><span data-stu-id="5cdf9-137">The solution file to use.</span></span> <span data-ttu-id="5cdf9-138">Belirtilmemişse, komut geçerli dizinde bir arama yapar.</span><span class="sxs-lookup"><span data-stu-id="5cdf9-138">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="5cdf9-139">Dizinde birden çok çözüm dosyası varsa, birinin belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="5cdf9-139">If there are multiple solution files in the directory, one must be specified.</span></span>

- **`PROJECT_PATH`**

  <span data-ttu-id="5cdf9-140">Çözümden kaldırılacak projenin yolu.</span><span class="sxs-lookup"><span data-stu-id="5cdf9-140">The path to the project to remove from the solution.</span></span> <span data-ttu-id="5cdf9-141">Boşluktan daha sonra bir tane ekleyerek birden çok projeyi kaldırın.</span><span class="sxs-lookup"><span data-stu-id="5cdf9-141">Remove multiple projects by adding one after the other separated by spaces.</span></span> <span data-ttu-id="5cdf9-142">UNIX/Linux kabuğu [Glob model](https://en.wikipedia.org/wiki/Glob_(programming)) genişletmeleri `dotnet sln` komutu tarafından doğru şekilde işlenir.</span><span class="sxs-lookup"><span data-stu-id="5cdf9-142">Unix/Linux shell [globbing pattern](https://en.wikipedia.org/wiki/Glob_(programming)) expansions are processed correctly by the `dotnet sln` command.</span></span>

#### <a name="options"></a><span data-ttu-id="5cdf9-143">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="5cdf9-143">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="5cdf9-144">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="5cdf9-144">Prints out a short help for the command.</span></span>

### `list`

<span data-ttu-id="5cdf9-145">Bir çözüm dosyasındaki tüm projeleri listeler.</span><span class="sxs-lookup"><span data-stu-id="5cdf9-145">Lists all projects in a solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="5cdf9-146">Özeti</span><span class="sxs-lookup"><span data-stu-id="5cdf9-146">Synopsis</span></span>

```dotnetcli
dotnet sln list [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="5cdf9-147">Arguments</span><span class="sxs-lookup"><span data-stu-id="5cdf9-147">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="5cdf9-148">Kullanılacak çözüm dosyası.</span><span class="sxs-lookup"><span data-stu-id="5cdf9-148">The solution file to use.</span></span> <span data-ttu-id="5cdf9-149">Belirtilmemişse, komut geçerli dizinde bir arama yapar.</span><span class="sxs-lookup"><span data-stu-id="5cdf9-149">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="5cdf9-150">Dizinde birden çok çözüm dosyası varsa, birinin belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="5cdf9-150">If there are multiple solution files in the directory, one must be specified.</span></span>

#### <a name="options"></a><span data-ttu-id="5cdf9-151">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="5cdf9-151">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="5cdf9-152">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="5cdf9-152">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="5cdf9-153">Örnekler</span><span class="sxs-lookup"><span data-stu-id="5cdf9-153">Examples</span></span>

- <span data-ttu-id="5cdf9-154">Bir çözüme C# proje ekleme:</span><span class="sxs-lookup"><span data-stu-id="5cdf9-154">Add a C# project to a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj
  ```

- <span data-ttu-id="5cdf9-155">Bir C# projeyi çözümden kaldırma:</span><span class="sxs-lookup"><span data-stu-id="5cdf9-155">Remove a C# project from a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove todo-app/todo-app.csproj
  ```

- <span data-ttu-id="5cdf9-156">Bir çözüme C# birden çok proje ekleyin:</span><span class="sxs-lookup"><span data-stu-id="5cdf9-156">Add multiple C# projects to a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- <span data-ttu-id="5cdf9-157">Bir çözümden C# birden çok proje kaldırma:</span><span class="sxs-lookup"><span data-stu-id="5cdf9-157">Remove multiple C# projects from a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- <span data-ttu-id="5cdf9-158">Bir glob C# kalıbı kullanarak bir çözüme birden çok proje ekleme (yalnızca Unix/Linux):</span><span class="sxs-lookup"><span data-stu-id="5cdf9-158">Add multiple C# projects to a solution using a globbing pattern (Unix/Linux only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln add **/*.csproj
  ```

- <span data-ttu-id="5cdf9-159">Bir glob C# kalıbı kullanarak birden çok projeyi çözümden kaldırma (yalnızca Unix/Linux):</span><span class="sxs-lookup"><span data-stu-id="5cdf9-159">Remove multiple C# projects from a solution using a globbing pattern (Unix/Linux only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove **/*.csproj
  ```
