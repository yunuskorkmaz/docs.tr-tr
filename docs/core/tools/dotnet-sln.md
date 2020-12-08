---
title: DotNet sln komutu
description: DotNet-sln komutu bir çözüm dosyasındaki projeleri eklemek, kaldırmak ve listelemek için kullanışlı bir seçenek sağlar.
ms.date: 12/07/2020
ms.openlocfilehash: 480634550f6fa1983bb46f51b439dc8a686ead3c
ms.sourcegitcommit: 45c7148f2483db2501c1aa696ab6ed2ed8cb71b2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96851710"
---
# <a name="dotnet-sln"></a><span data-ttu-id="be399-103">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="be399-103">dotnet sln</span></span>

<span data-ttu-id="be399-104">**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 2. x SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="be399-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="be399-105">Name</span><span class="sxs-lookup"><span data-stu-id="be399-105">Name</span></span>

<span data-ttu-id="be399-106">`dotnet sln` -Bir .NET çözüm dosyasındaki projeleri listeler veya değiştirir.</span><span class="sxs-lookup"><span data-stu-id="be399-106">`dotnet sln` - Lists or modifies the projects in a .NET solution file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="be399-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="be399-107">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] [command]

dotnet sln [command] -h|--help
```

## <a name="description"></a><span data-ttu-id="be399-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="be399-108">Description</span></span>

<span data-ttu-id="be399-109">`dotnet sln`Komut, bir çözüm dosyasındaki projeleri listelemek ve değiştirmek için kullanışlı bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="be399-109">The `dotnet sln` command provides a convenient way to list and modify projects in a solution file.</span></span>

<span data-ttu-id="be399-110">Komutunu kullanmak için `dotnet sln` , çözüm dosyası zaten var olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="be399-110">To use the `dotnet sln` command, the solution file must already exist.</span></span> <span data-ttu-id="be399-111">Bir tane oluşturmanız gerekiyorsa, aşağıdaki örnekte olduğu gibi [DotNet New](dotnet-new.md) komutunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="be399-111">If you need to create one, use the [dotnet new](dotnet-new.md) command, as in the following example:</span></span>

```dotnetcli
dotnet new sln
```

## <a name="arguments"></a><span data-ttu-id="be399-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="be399-112">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="be399-113">Kullanılacak çözüm dosyası.</span><span class="sxs-lookup"><span data-stu-id="be399-113">The solution file to use.</span></span> <span data-ttu-id="be399-114">Bu bağımsız değişken atlanırsa, komut geçerli dizinde bir arar.</span><span class="sxs-lookup"><span data-stu-id="be399-114">If this argument is omitted, the command searches the current directory for one.</span></span> <span data-ttu-id="be399-115">Çözüm dosyası veya birden çok çözüm dosyası bulursa, komut başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="be399-115">If it finds no solution file or multiple solution files, the command fails.</span></span>

## <a name="options"></a><span data-ttu-id="be399-116">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="be399-116">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="be399-117">Komutunun nasıl kullanılacağına ilişkin bir açıklama yazdırır.</span><span class="sxs-lookup"><span data-stu-id="be399-117">Prints out a description of how to use the command.</span></span>

## <a name="commands"></a><span data-ttu-id="be399-118">Komutlar</span><span class="sxs-lookup"><span data-stu-id="be399-118">Commands</span></span>

### `list`

<span data-ttu-id="be399-119">Bir çözüm dosyasındaki tüm projeleri listeler.</span><span class="sxs-lookup"><span data-stu-id="be399-119">Lists all projects in a solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="be399-120">Özeti</span><span class="sxs-lookup"><span data-stu-id="be399-120">Synopsis</span></span>

```dotnetcli
dotnet sln list [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="be399-121">Arguments</span><span class="sxs-lookup"><span data-stu-id="be399-121">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="be399-122">Kullanılacak çözüm dosyası.</span><span class="sxs-lookup"><span data-stu-id="be399-122">The solution file to use.</span></span> <span data-ttu-id="be399-123">Bu bağımsız değişken atlanırsa, komut geçerli dizinde bir arar.</span><span class="sxs-lookup"><span data-stu-id="be399-123">If this argument is omitted, the command searches the current directory for one.</span></span> <span data-ttu-id="be399-124">Çözüm dosyası veya birden çok çözüm dosyası bulursa, komut başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="be399-124">If it finds no solution file or multiple solution files, the command fails.</span></span>

#### <a name="options"></a><span data-ttu-id="be399-125">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="be399-125">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="be399-126">Komutunun nasıl kullanılacağına ilişkin bir açıklama yazdırır.</span><span class="sxs-lookup"><span data-stu-id="be399-126">Prints out a description of how to use the command.</span></span>
  
### `add`

<span data-ttu-id="be399-127">Çözüm dosyasına bir veya daha fazla proje ekler.</span><span class="sxs-lookup"><span data-stu-id="be399-127">Adds one or more projects to the solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="be399-128">Özeti</span><span class="sxs-lookup"><span data-stu-id="be399-128">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] add [--in-root] [-s|--solution-folder <PATH>] <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln add [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="be399-129">Arguments</span><span class="sxs-lookup"><span data-stu-id="be399-129">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="be399-130">Kullanılacak çözüm dosyası.</span><span class="sxs-lookup"><span data-stu-id="be399-130">The solution file to use.</span></span> <span data-ttu-id="be399-131">Belirtilmemişse, komut geçerli dizinde bir arar ve birden çok çözüm dosyası varsa başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="be399-131">If it is unspecified, the command searches the current directory for one and fails if there are multiple solution files.</span></span>

- **`PROJECT_PATH`**

  <span data-ttu-id="be399-132">Çözüme eklenecek projenin veya projelerin yolu.</span><span class="sxs-lookup"><span data-stu-id="be399-132">The path to the project or projects to add to the solution.</span></span> <span data-ttu-id="be399-133">UNIX/Linux kabuğu [Glob model](https://en.wikipedia.org/wiki/Glob_(programming)) genişletmeleri, komut tarafından doğru şekilde işlenir `dotnet sln` .</span><span class="sxs-lookup"><span data-stu-id="be399-133">Unix/Linux shell [globbing pattern](https://en.wikipedia.org/wiki/Glob_(programming)) expansions are processed correctly by the `dotnet sln` command.</span></span>

#### <a name="options"></a><span data-ttu-id="be399-134">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="be399-134">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="be399-135">Komutunun nasıl kullanılacağına ilişkin bir açıklama yazdırır.</span><span class="sxs-lookup"><span data-stu-id="be399-135">Prints out a description of how to use the command.</span></span>

- **`--in-root`**

  <span data-ttu-id="be399-136">Bir çözüm klasörü oluşturmak yerine, projeleri çözümün köküne koyar.</span><span class="sxs-lookup"><span data-stu-id="be399-136">Places the projects in the root of the solution, rather than creating a solution folder.</span></span> <span data-ttu-id="be399-137">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="be399-137">Available since .NET Core 3.0 SDK.</span></span>

- **`-s|--solution-folder <PATH>`**

  <span data-ttu-id="be399-138">Projelerin ekleneceği hedef çözüm klasörünün yolu.</span><span class="sxs-lookup"><span data-stu-id="be399-138">The destination solution folder path to add the projects to.</span></span> <span data-ttu-id="be399-139">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="be399-139">Available since .NET Core 3.0 SDK.</span></span>

### `remove`

<span data-ttu-id="be399-140">Çözüm dosyasından bir projeyi veya birden çok projeyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="be399-140">Removes a project or multiple projects from the solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="be399-141">Özeti</span><span class="sxs-lookup"><span data-stu-id="be399-141">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] remove <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln [<SOLUTION_FILE>] remove [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="be399-142">Arguments</span><span class="sxs-lookup"><span data-stu-id="be399-142">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="be399-143">Kullanılacak çözüm dosyası.</span><span class="sxs-lookup"><span data-stu-id="be399-143">The solution file to use.</span></span> <span data-ttu-id="be399-144">Belirtilmemişse, komut geçerli dizinde bir arar ve birden çok çözüm dosyası varsa başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="be399-144">If is left unspecified, the command searches the current directory for one and fails if there are multiple solution files.</span></span>

- **`PROJECT_PATH`**

  <span data-ttu-id="be399-145">Çözüme eklenecek projenin veya projelerin yolu.</span><span class="sxs-lookup"><span data-stu-id="be399-145">The path to the project or projects to add to the solution.</span></span> <span data-ttu-id="be399-146">UNIX/Linux kabuğu [Glob model](https://en.wikipedia.org/wiki/Glob_(programming)) genişletmeleri, komut tarafından doğru şekilde işlenir `dotnet sln` .</span><span class="sxs-lookup"><span data-stu-id="be399-146">Unix/Linux shell [globbing pattern](https://en.wikipedia.org/wiki/Glob_(programming)) expansions are processed correctly by the `dotnet sln` command.</span></span>

#### <a name="options"></a><span data-ttu-id="be399-147">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="be399-147">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="be399-148">Komutunun nasıl kullanılacağına ilişkin bir açıklama yazdırır.</span><span class="sxs-lookup"><span data-stu-id="be399-148">Prints out a description of how to use the command.</span></span>

## <a name="examples"></a><span data-ttu-id="be399-149">Örnekler</span><span class="sxs-lookup"><span data-stu-id="be399-149">Examples</span></span>

- <span data-ttu-id="be399-150">Bir çözümdeki projeleri listeleyin:</span><span class="sxs-lookup"><span data-stu-id="be399-150">List the projects in a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln list
  ```

- <span data-ttu-id="be399-151">Bir çözüme C# projesi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="be399-151">Add a C# project to a solution:</span></span>

  ```dotnetcli
  dotnet sln add todo-app/todo-app.csproj
  ```

- <span data-ttu-id="be399-152">Bir C# projesini çözümden kaldırma:</span><span class="sxs-lookup"><span data-stu-id="be399-152">Remove a C# project from a solution:</span></span>

  ```dotnetcli
  dotnet sln remove todo-app/todo-app.csproj
  ```

- <span data-ttu-id="be399-153">Bir çözümün köküne birden çok C# projesi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="be399-153">Add multiple C# projects to the root of a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj --in-root
  ```

- <span data-ttu-id="be399-154">Bir çözüme birden çok C# projesi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="be399-154">Add multiple C# projects to a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- <span data-ttu-id="be399-155">Bir çözümden birden çok C# projesini kaldırma:</span><span class="sxs-lookup"><span data-stu-id="be399-155">Remove multiple C# projects from a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- <span data-ttu-id="be399-156">Bir glob deseninin (yalnızca Unix/Linux) kullanıldığı bir çözüme birden çok C# projesi ekleme:</span><span class="sxs-lookup"><span data-stu-id="be399-156">Add multiple C# projects to a solution using a globbing pattern (Unix/Linux only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln add **/*.csproj
  ```

- <span data-ttu-id="be399-157">Glob deseninin kullanıldığı bir çözüme birden çok C# projesi ekleme (yalnızca Windows PowerShell):</span><span class="sxs-lookup"><span data-stu-id="be399-157">Add multiple C# projects to a solution using a globbing pattern (Windows PowerShell only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln add (ls -r **/*.csproj)
  ```

- <span data-ttu-id="be399-158">Bir glob deseninin (yalnızca Unix/Linux) kullanıldığı bir çözümden birden çok C# projesini kaldırma:</span><span class="sxs-lookup"><span data-stu-id="be399-158">Remove multiple C# projects from a solution using a globbing pattern (Unix/Linux only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove **/*.csproj
  ```

- <span data-ttu-id="be399-159">Glob deseninin kullanıldığı bir çözümden birden çok C# projesini kaldırma (yalnızca Windows PowerShell):</span><span class="sxs-lookup"><span data-stu-id="be399-159">Remove multiple C# projects from a solution using a globbing pattern (Windows PowerShell only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove (ls -r **/*.csproj)
  ```

- <span data-ttu-id="be399-160">Bir çözüm, konsol uygulaması ve iki sınıf kitaplığı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="be399-160">Create a solution, a console app, and two class libraries.</span></span> <span data-ttu-id="be399-161">Projeleri çözüme ekleyin ve ' `--solution-folder` nin seçeneğini kullanarak `dotnet sln` sınıf kitaplıklarını bir çözüm klasörü olarak düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="be399-161">Add the projects to the solution, and use the `--solution-folder` option of `dotnet sln` to organize the class libraries into a solution folder.</span></span>

  ```dotnetcli
  dotnet new sln -n mysolution
  dotnet new console -o myapp
  dotnet new classlib -o mylib1
  dotnet new classlib -o mylib2
  dotnet sln mysolution.sln add myapp\myapp.csproj
  dotnet sln mysolution.sln add mylib1\mylib1.csproj --solution-folder mylibs
  dotnet sln mysolution.sln add mylib2\mylib2.csproj --solution-folder mylibs
  ```

  <span data-ttu-id="be399-162">Aşağıdaki ekran görüntüsünde, Visual Studio 2019 **Çözüm Gezgini** sonucu gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="be399-162">The following screenshot shows the result in Visual Studio 2019 **Solution Explorer**:</span></span>

  :::image type="content" source="media/dotnet-sln/dotnet-sln-solution-folder.png" alt-text="Bir çözüm klasöründe gruplanmış sınıf kitaplığı projelerini gösteren Çözüm Gezgini.":::
