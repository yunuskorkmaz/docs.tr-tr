---
title: dotnet sln komutu
description: dotnet-sln komutu, çözüm dosyasındaki projeleri eklemek, kaldırmak ve listelemek için kullanışlı bir seçenek sağlar.
ms.date: 02/14/2020
ms.openlocfilehash: b2455c04a46b2a10b8142d8ddc2d8129f2154b27
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77543488"
---
# <a name="dotnet-sln"></a><span data-ttu-id="561c0-103">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="561c0-103">dotnet sln</span></span>

<span data-ttu-id="561c0-104">**Bu makale şu şekilde dir:** ✔️ .NET Core 2.x SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="561c0-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="561c0-105">Adı</span><span class="sxs-lookup"><span data-stu-id="561c0-105">Name</span></span>

<span data-ttu-id="561c0-106">`dotnet sln`- Projeleri .NET Core çözüm dosyasında listeler veya değiştirir.</span><span class="sxs-lookup"><span data-stu-id="561c0-106">`dotnet sln` - Lists or modifies the projects in a .NET Core solution file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="561c0-107">Özet</span><span class="sxs-lookup"><span data-stu-id="561c0-107">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] [command] [-h|--help]
```

## <a name="description"></a><span data-ttu-id="561c0-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="561c0-108">Description</span></span>

<span data-ttu-id="561c0-109">Komut, `dotnet sln` bir çözüm dosyasındaki projeleri listelemek ve değiştirmek için kullanışlı bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="561c0-109">The `dotnet sln` command provides a convenient way to list and modify projects in a solution file.</span></span>

<span data-ttu-id="561c0-110">Komutu `dotnet sln` kullanmak için çözüm dosyasının zaten var olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="561c0-110">To use the `dotnet sln` command, the solution file must already exist.</span></span> <span data-ttu-id="561c0-111">Bir tane oluşturmanız gerekiyorsa, aşağıdaki örnekte olduğu gibi [dotnet yeni](dotnet-new.md) komutunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="561c0-111">If you need to create one, use the [dotnet new](dotnet-new.md) command, as in the following example:</span></span>

```dotnetcli
dotnet new sln
```

## <a name="arguments"></a><span data-ttu-id="561c0-112">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="561c0-112">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="561c0-113">Kullanılacak çözüm dosyası.</span><span class="sxs-lookup"><span data-stu-id="561c0-113">The solution file to use.</span></span> <span data-ttu-id="561c0-114">Bu bağımsız değişken atlanırsa, komut geçerli dizini arar.</span><span class="sxs-lookup"><span data-stu-id="561c0-114">If this argument is omitted, the command searches the current directory for one.</span></span> <span data-ttu-id="561c0-115">Çözüm dosyası veya birden çok çözüm dosyası bulamazsa, komut başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="561c0-115">If it finds no solution file or multiple solution files, the command fails.</span></span>

## <a name="options"></a><span data-ttu-id="561c0-116">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="561c0-116">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="561c0-117">Komutun nasıl kullanılacağına ilişkin bir açıklama sızıntılır.</span><span class="sxs-lookup"><span data-stu-id="561c0-117">Prints out a description of how to use the command.</span></span>

## <a name="commands"></a><span data-ttu-id="561c0-118">Komutlar</span><span class="sxs-lookup"><span data-stu-id="561c0-118">Commands</span></span>

### `list`

<span data-ttu-id="561c0-119">Çözüm dosyasındaki tüm projeleri listeler.</span><span class="sxs-lookup"><span data-stu-id="561c0-119">Lists all projects in a solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="561c0-120">Özet</span><span class="sxs-lookup"><span data-stu-id="561c0-120">Synopsis</span></span>

```dotnetcli
dotnet sln list [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="561c0-121">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="561c0-121">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="561c0-122">Kullanılacak çözüm dosyası.</span><span class="sxs-lookup"><span data-stu-id="561c0-122">The solution file to use.</span></span> <span data-ttu-id="561c0-123">Bu bağımsız değişken atlanırsa, komut geçerli dizini arar.</span><span class="sxs-lookup"><span data-stu-id="561c0-123">If this argument is omitted, the command searches the current directory for one.</span></span> <span data-ttu-id="561c0-124">Çözüm dosyası veya birden çok çözüm dosyası bulamazsa, komut başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="561c0-124">If it finds no solution file or multiple solution files, the command fails.</span></span>

#### <a name="options"></a><span data-ttu-id="561c0-125">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="561c0-125">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="561c0-126">Komutun nasıl kullanılacağına ilişkin bir açıklama sızıntılır.</span><span class="sxs-lookup"><span data-stu-id="561c0-126">Prints out a description of how to use the command.</span></span>
  
### `add`

<span data-ttu-id="561c0-127">Çözüm dosyasına bir veya daha fazla proje ekler.</span><span class="sxs-lookup"><span data-stu-id="561c0-127">Adds one or more projects to the solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="561c0-128">Özet</span><span class="sxs-lookup"><span data-stu-id="561c0-128">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] add [--in-root] [-s|--solution-folder] <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln add [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="561c0-129">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="561c0-129">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="561c0-130">Kullanılacak çözüm dosyası.</span><span class="sxs-lookup"><span data-stu-id="561c0-130">The solution file to use.</span></span> <span data-ttu-id="561c0-131">Belirtilmemişse, komut geçerli dizini arar ve birden çok çözüm dosyası varsa başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="561c0-131">If it is unspecified, the command searches the current directory for one and fails if there are multiple solution files.</span></span>

- **`PROJECT_PATH`**

  <span data-ttu-id="561c0-132">Çözüme eklenecek proje veya projelere giden yol.</span><span class="sxs-lookup"><span data-stu-id="561c0-132">The path to the project or projects to add to the solution.</span></span> <span data-ttu-id="561c0-133">Unix/Linux kabuk [globbing desen](https://en.wikipedia.org/wiki/Glob_(programming)) genişletmeleri `dotnet sln` komut u tarafından doğru bir şekilde işlenir.</span><span class="sxs-lookup"><span data-stu-id="561c0-133">Unix/Linux shell [globbing pattern](https://en.wikipedia.org/wiki/Glob_(programming)) expansions are processed correctly by the `dotnet sln` command.</span></span>

#### <a name="options"></a><span data-ttu-id="561c0-134">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="561c0-134">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="561c0-135">Komutun nasıl kullanılacağına ilişkin bir açıklama sızıntılır.</span><span class="sxs-lookup"><span data-stu-id="561c0-135">Prints out a description of how to use the command.</span></span>

- **`--in-root`**

  <span data-ttu-id="561c0-136">Projeleri çözüm klasörü oluşturmak yerine çözümün köküne yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="561c0-136">Places the projects in the root of the solution, rather than creating a solution folder.</span></span> <span data-ttu-id="561c0-137">.NET Core 3.0 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="561c0-137">Available since .NET Core 3.0 SDK.</span></span>

- **`-s|--solution-folder`**

  <span data-ttu-id="561c0-138">Projeleri eklemek için hedef çözüm klasörü yolu.</span><span class="sxs-lookup"><span data-stu-id="561c0-138">The destination solution folder path to add the projects to.</span></span> <span data-ttu-id="561c0-139">.NET Core 3.0 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="561c0-139">Available since .NET Core 3.0 SDK.</span></span>

### `remove`

<span data-ttu-id="561c0-140">Bir projeyi veya birden çok projeyi çözüm dosyasından kaldırır.</span><span class="sxs-lookup"><span data-stu-id="561c0-140">Removes a project or multiple projects from the solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="561c0-141">Özet</span><span class="sxs-lookup"><span data-stu-id="561c0-141">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] remove <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln [<SOLUTION_FILE>] remove [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="561c0-142">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="561c0-142">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="561c0-143">Kullanılacak çözüm dosyası.</span><span class="sxs-lookup"><span data-stu-id="561c0-143">The solution file to use.</span></span> <span data-ttu-id="561c0-144">Belirtilmemiş bırakılırsa, komut geçerli dizini arar ve birden çok çözüm dosyası varsa başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="561c0-144">If is left unspecified, the command searches the current directory for one and fails if there are multiple solution files.</span></span>

- **`PROJECT_PATH`**

  <span data-ttu-id="561c0-145">Çözüme eklenecek proje veya projelere giden yol.</span><span class="sxs-lookup"><span data-stu-id="561c0-145">The path to the project or projects to add to the solution.</span></span> <span data-ttu-id="561c0-146">Unix/Linux kabuk [globbing desen](https://en.wikipedia.org/wiki/Glob_(programming)) genişletmeleri `dotnet sln` komut u tarafından doğru bir şekilde işlenir.</span><span class="sxs-lookup"><span data-stu-id="561c0-146">Unix/Linux shell [globbing pattern](https://en.wikipedia.org/wiki/Glob_(programming)) expansions are processed correctly by the `dotnet sln` command.</span></span>

#### <a name="options"></a><span data-ttu-id="561c0-147">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="561c0-147">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="561c0-148">Komutun nasıl kullanılacağına ilişkin bir açıklama sızıntılır.</span><span class="sxs-lookup"><span data-stu-id="561c0-148">Prints out a description of how to use the command.</span></span>

## <a name="examples"></a><span data-ttu-id="561c0-149">Örnekler</span><span class="sxs-lookup"><span data-stu-id="561c0-149">Examples</span></span>

- <span data-ttu-id="561c0-150">Projeleri bir çözümde listele:</span><span class="sxs-lookup"><span data-stu-id="561c0-150">List the projects in a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln list
  ```

- <span data-ttu-id="561c0-151">Çözüme C# projesi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="561c0-151">Add a C# project to a solution:</span></span>

  ```dotnetcli
  dotnet sln add todo-app/todo-app.csproj
  ```

- <span data-ttu-id="561c0-152">Bir C# projesini çözümden kaldırın:</span><span class="sxs-lookup"><span data-stu-id="561c0-152">Remove a C# project from a solution:</span></span>

  ```dotnetcli
  dotnet sln remove todo-app/todo-app.csproj
  ```

- <span data-ttu-id="561c0-153">Bir çözümün köküne birden çok C# projesi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="561c0-153">Add multiple C# projects to the root of a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj --in-root
  ```

- <span data-ttu-id="561c0-154">Bir çözüme birden çok C# projesi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="561c0-154">Add multiple C# projects to a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- <span data-ttu-id="561c0-155">Birden çok C# projesinin çözümden kaldırılması:</span><span class="sxs-lookup"><span data-stu-id="561c0-155">Remove multiple C# projects from a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- <span data-ttu-id="561c0-156">Globbing deseni (yalnızca Unix/Linux) kullanarak bir çözüme birden fazla C# projesi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="561c0-156">Add multiple C# projects to a solution using a globbing pattern (Unix/Linux only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln add **/*.csproj
  ```

- <span data-ttu-id="561c0-157">Birden fazla C# projesinin bir çözümden globbing deseni (yalnızca Unix/Linux) kullanarak çıkarılması:</span><span class="sxs-lookup"><span data-stu-id="561c0-157">Remove multiple C# projects from a solution using a globbing pattern (Unix/Linux only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove **/*.csproj
  ```
