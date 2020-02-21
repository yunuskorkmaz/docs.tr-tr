---
title: DotNet sln komutu
description: DotNet-sln komutu bir çözüm dosyasındaki projeleri eklemek, kaldırmak ve listelemek için kullanışlı bir seçenek sağlar.
ms.date: 02/14/2020
ms.openlocfilehash: b2455c04a46b2a10b8142d8ddc2d8129f2154b27
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543488"
---
# <a name="dotnet-sln"></a><span data-ttu-id="d0851-103">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="d0851-103">dotnet sln</span></span>

<span data-ttu-id="d0851-104">**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 2. x SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="d0851-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="d0851-105">Adı</span><span class="sxs-lookup"><span data-stu-id="d0851-105">Name</span></span>

<span data-ttu-id="d0851-106">`dotnet sln`-bir .NET Core çözüm dosyasındaki projeleri listeler veya değiştirir.</span><span class="sxs-lookup"><span data-stu-id="d0851-106">`dotnet sln` - Lists or modifies the projects in a .NET Core solution file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d0851-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="d0851-107">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] [command] [-h|--help]
```

## <a name="description"></a><span data-ttu-id="d0851-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0851-108">Description</span></span>

<span data-ttu-id="d0851-109">`dotnet sln` komutu bir çözüm dosyasındaki projeleri listelemek ve değiştirmek için kullanışlı bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="d0851-109">The `dotnet sln` command provides a convenient way to list and modify projects in a solution file.</span></span>

<span data-ttu-id="d0851-110">`dotnet sln` komutunu kullanmak için, çözüm dosyası zaten var olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d0851-110">To use the `dotnet sln` command, the solution file must already exist.</span></span> <span data-ttu-id="d0851-111">Bir tane oluşturmanız gerekiyorsa, aşağıdaki örnekte olduğu gibi [DotNet New](dotnet-new.md) komutunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="d0851-111">If you need to create one, use the [dotnet new](dotnet-new.md) command, as in the following example:</span></span>

```dotnetcli
dotnet new sln
```

## <a name="arguments"></a><span data-ttu-id="d0851-112">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="d0851-112">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="d0851-113">Kullanılacak çözüm dosyası.</span><span class="sxs-lookup"><span data-stu-id="d0851-113">The solution file to use.</span></span> <span data-ttu-id="d0851-114">Bu bağımsız değişken atlanırsa, komut geçerli dizinde bir arar.</span><span class="sxs-lookup"><span data-stu-id="d0851-114">If this argument is omitted, the command searches the current directory for one.</span></span> <span data-ttu-id="d0851-115">Çözüm dosyası veya birden çok çözüm dosyası bulursa, komut başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="d0851-115">If it finds no solution file or multiple solution files, the command fails.</span></span>

## <a name="options"></a><span data-ttu-id="d0851-116">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="d0851-116">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="d0851-117">Komutunun nasıl kullanılacağına ilişkin bir açıklama yazdırır.</span><span class="sxs-lookup"><span data-stu-id="d0851-117">Prints out a description of how to use the command.</span></span>

## <a name="commands"></a><span data-ttu-id="d0851-118">Komutlar</span><span class="sxs-lookup"><span data-stu-id="d0851-118">Commands</span></span>

### `list`

<span data-ttu-id="d0851-119">Bir çözüm dosyasındaki tüm projeleri listeler.</span><span class="sxs-lookup"><span data-stu-id="d0851-119">Lists all projects in a solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="d0851-120">Özeti</span><span class="sxs-lookup"><span data-stu-id="d0851-120">Synopsis</span></span>

```dotnetcli
dotnet sln list [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="d0851-121">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="d0851-121">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="d0851-122">Kullanılacak çözüm dosyası.</span><span class="sxs-lookup"><span data-stu-id="d0851-122">The solution file to use.</span></span> <span data-ttu-id="d0851-123">Bu bağımsız değişken atlanırsa, komut geçerli dizinde bir arar.</span><span class="sxs-lookup"><span data-stu-id="d0851-123">If this argument is omitted, the command searches the current directory for one.</span></span> <span data-ttu-id="d0851-124">Çözüm dosyası veya birden çok çözüm dosyası bulursa, komut başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="d0851-124">If it finds no solution file or multiple solution files, the command fails.</span></span>

#### <a name="options"></a><span data-ttu-id="d0851-125">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="d0851-125">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="d0851-126">Komutunun nasıl kullanılacağına ilişkin bir açıklama yazdırır.</span><span class="sxs-lookup"><span data-stu-id="d0851-126">Prints out a description of how to use the command.</span></span>
  
### `add`

<span data-ttu-id="d0851-127">Çözüm dosyasına bir veya daha fazla proje ekler.</span><span class="sxs-lookup"><span data-stu-id="d0851-127">Adds one or more projects to the solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="d0851-128">Özeti</span><span class="sxs-lookup"><span data-stu-id="d0851-128">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] add [--in-root] [-s|--solution-folder] <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln add [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="d0851-129">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="d0851-129">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="d0851-130">Kullanılacak çözüm dosyası.</span><span class="sxs-lookup"><span data-stu-id="d0851-130">The solution file to use.</span></span> <span data-ttu-id="d0851-131">Belirtilmemişse, komut geçerli dizinde bir arar ve birden çok çözüm dosyası varsa başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="d0851-131">If it is unspecified, the command searches the current directory for one and fails if there are multiple solution files.</span></span>

- **`PROJECT_PATH`**

  <span data-ttu-id="d0851-132">Çözüme eklenecek projenin veya projelerin yolu.</span><span class="sxs-lookup"><span data-stu-id="d0851-132">The path to the project or projects to add to the solution.</span></span> <span data-ttu-id="d0851-133">UNIX/Linux kabuğu [Glob model](https://en.wikipedia.org/wiki/Glob_(programming)) genişletmeleri `dotnet sln` komutu tarafından doğru şekilde işlenir.</span><span class="sxs-lookup"><span data-stu-id="d0851-133">Unix/Linux shell [globbing pattern](https://en.wikipedia.org/wiki/Glob_(programming)) expansions are processed correctly by the `dotnet sln` command.</span></span>

#### <a name="options"></a><span data-ttu-id="d0851-134">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="d0851-134">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="d0851-135">Komutunun nasıl kullanılacağına ilişkin bir açıklama yazdırır.</span><span class="sxs-lookup"><span data-stu-id="d0851-135">Prints out a description of how to use the command.</span></span>

- **`--in-root`**

  <span data-ttu-id="d0851-136">Bir çözüm klasörü oluşturmak yerine, projeleri çözümün köküne koyar.</span><span class="sxs-lookup"><span data-stu-id="d0851-136">Places the projects in the root of the solution, rather than creating a solution folder.</span></span> <span data-ttu-id="d0851-137">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d0851-137">Available since .NET Core 3.0 SDK.</span></span>

- **`-s|--solution-folder`**

  <span data-ttu-id="d0851-138">Projelerin ekleneceği hedef çözüm klasörünün yolu.</span><span class="sxs-lookup"><span data-stu-id="d0851-138">The destination solution folder path to add the projects to.</span></span> <span data-ttu-id="d0851-139">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d0851-139">Available since .NET Core 3.0 SDK.</span></span>

### `remove`

<span data-ttu-id="d0851-140">Çözüm dosyasından bir projeyi veya birden çok projeyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="d0851-140">Removes a project or multiple projects from the solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="d0851-141">Özeti</span><span class="sxs-lookup"><span data-stu-id="d0851-141">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] remove <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln [<SOLUTION_FILE>] remove [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="d0851-142">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="d0851-142">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="d0851-143">Kullanılacak çözüm dosyası.</span><span class="sxs-lookup"><span data-stu-id="d0851-143">The solution file to use.</span></span> <span data-ttu-id="d0851-144">Belirtilmemişse, komut geçerli dizinde bir arar ve birden çok çözüm dosyası varsa başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="d0851-144">If is left unspecified, the command searches the current directory for one and fails if there are multiple solution files.</span></span>

- **`PROJECT_PATH`**

  <span data-ttu-id="d0851-145">Çözüme eklenecek projenin veya projelerin yolu.</span><span class="sxs-lookup"><span data-stu-id="d0851-145">The path to the project or projects to add to the solution.</span></span> <span data-ttu-id="d0851-146">UNIX/Linux kabuğu [Glob model](https://en.wikipedia.org/wiki/Glob_(programming)) genişletmeleri `dotnet sln` komutu tarafından doğru şekilde işlenir.</span><span class="sxs-lookup"><span data-stu-id="d0851-146">Unix/Linux shell [globbing pattern](https://en.wikipedia.org/wiki/Glob_(programming)) expansions are processed correctly by the `dotnet sln` command.</span></span>

#### <a name="options"></a><span data-ttu-id="d0851-147">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="d0851-147">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="d0851-148">Komutunun nasıl kullanılacağına ilişkin bir açıklama yazdırır.</span><span class="sxs-lookup"><span data-stu-id="d0851-148">Prints out a description of how to use the command.</span></span>

## <a name="examples"></a><span data-ttu-id="d0851-149">Örnekler</span><span class="sxs-lookup"><span data-stu-id="d0851-149">Examples</span></span>

- <span data-ttu-id="d0851-150">Bir çözümdeki projeleri listeleyin:</span><span class="sxs-lookup"><span data-stu-id="d0851-150">List the projects in a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln list
  ```

- <span data-ttu-id="d0851-151">Bir çözüme C# proje ekleme:</span><span class="sxs-lookup"><span data-stu-id="d0851-151">Add a C# project to a solution:</span></span>

  ```dotnetcli
  dotnet sln add todo-app/todo-app.csproj
  ```

- <span data-ttu-id="d0851-152">Bir C# projeyi çözümden kaldırma:</span><span class="sxs-lookup"><span data-stu-id="d0851-152">Remove a C# project from a solution:</span></span>

  ```dotnetcli
  dotnet sln remove todo-app/todo-app.csproj
  ```

- <span data-ttu-id="d0851-153">Bir çözümün C# köküne birden çok proje ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d0851-153">Add multiple C# projects to the root of a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj --in-root
  ```

- <span data-ttu-id="d0851-154">Bir çözüme C# birden çok proje ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d0851-154">Add multiple C# projects to a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- <span data-ttu-id="d0851-155">Bir çözümden C# birden çok proje kaldırma:</span><span class="sxs-lookup"><span data-stu-id="d0851-155">Remove multiple C# projects from a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- <span data-ttu-id="d0851-156">Bir glob C# kalıbı kullanarak bir çözüme birden çok proje ekleme (yalnızca Unix/Linux):</span><span class="sxs-lookup"><span data-stu-id="d0851-156">Add multiple C# projects to a solution using a globbing pattern (Unix/Linux only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln add **/*.csproj
  ```

- <span data-ttu-id="d0851-157">Bir glob C# kalıbı kullanarak birden çok projeyi çözümden kaldırma (yalnızca Unix/Linux):</span><span class="sxs-lookup"><span data-stu-id="d0851-157">Remove multiple C# projects from a solution using a globbing pattern (Unix/Linux only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove **/*.csproj
  ```
