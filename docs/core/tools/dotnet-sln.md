---
title: DotNet sln komutu
description: Dotnet sln komutu eklemek, kaldırmak ve bir çözüm dosyası projelerinde listelemek için uygun bir seçenek sağlar.
ms.date: 06/13/2018
ms.openlocfilehash: a88e22c68f639f2a42e59f9a271e431f04e24a2b
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169150"
---
# <a name="dotnet-sln"></a><span data-ttu-id="db029-103">DotNet sln</span><span class="sxs-lookup"><span data-stu-id="db029-103">dotnet sln</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="db029-104">Ad</span><span class="sxs-lookup"><span data-stu-id="db029-104">Name</span></span>

<span data-ttu-id="db029-105">`dotnet sln` -.NET Core çözüm dosyasını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="db029-105">`dotnet sln` - Modifies a .NET Core solution file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="db029-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="db029-106">Synopsis</span></span>

```
dotnet sln [<SOLUTION_NAME>] add <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] add <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] remove <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] remove <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] list
dotnet sln [-h|--help]
```

## <a name="description"></a><span data-ttu-id="db029-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="db029-107">Description</span></span>

<span data-ttu-id="db029-108">`dotnet sln` Komutu eklemek, kaldırmak ve bir çözüm dosyası projelerinde listelemek için kolay bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="db029-108">The `dotnet sln` command provides a convenient way to add, remove, and list projects in a solution file.</span></span>

<span data-ttu-id="db029-109">Kullanılacak `dotnet sln` komutu, çözüm dosyası zaten var olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="db029-109">To use the `dotnet sln` command, the solution file must already exist.</span></span> <span data-ttu-id="db029-110">Oluşturmak ihtiyacınız varsa [yeni dotnet](dotnet-new.md) komutu gibi aşağıdaki örnekte:</span><span class="sxs-lookup"><span data-stu-id="db029-110">If you need to create one, use the [dotnet new](dotnet-new.md) command, like in the following example:</span></span>

```
dotnet new sln
```

## <a name="commands"></a><span data-ttu-id="db029-111">Komutlar</span><span class="sxs-lookup"><span data-stu-id="db029-111">Commands</span></span>

`add <PROJECT> ...`

`add <GLOBBING_PATTERN>`

<span data-ttu-id="db029-112">Bir proje ya da birden çok proje, çözüm dosyasına eklenir.</span><span class="sxs-lookup"><span data-stu-id="db029-112">Adds a project or multiple projects to the solution file.</span></span> <span data-ttu-id="db029-113">[Glob desenlerinin](https://en.wikipedia.org/wiki/Glob_(programming)) UNIX/Linux tabanlı terminaller üzerinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="db029-113">[Globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

`remove <PROJECT> ...`

`remove <GLOBBING_PATTERN>`

<span data-ttu-id="db029-114">Bir proje ya da birden çok proje çözümü dosyasından kaldırır.</span><span class="sxs-lookup"><span data-stu-id="db029-114">Removes a project or multiple projects from the solution file.</span></span> <span data-ttu-id="db029-115">[Glob desenlerinin](https://en.wikipedia.org/wiki/Glob_(programming)) UNIX/Linux tabanlı terminaller üzerinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="db029-115">[Globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

`list`

<span data-ttu-id="db029-116">Bir çözüm dosyasındaki tüm projeleri listeler.</span><span class="sxs-lookup"><span data-stu-id="db029-116">Lists all projects in a solution file.</span></span>

## <a name="arguments"></a><span data-ttu-id="db029-117">Arguments</span><span class="sxs-lookup"><span data-stu-id="db029-117">Arguments</span></span>

`SOLUTION_NAME`

<span data-ttu-id="db029-118">Çözüm dosyası kullanın.</span><span class="sxs-lookup"><span data-stu-id="db029-118">Solution file to use.</span></span> <span data-ttu-id="db029-119">Belirtilmezse, komut için geçerli dizinde arar.</span><span class="sxs-lookup"><span data-stu-id="db029-119">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="db029-120">Dizinde birden fazla çözüm dosyası varsa, biri belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="db029-120">If there are multiple solution files in the directory, one must be specified.</span></span>

## <a name="options"></a><span data-ttu-id="db029-121">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="db029-121">Options</span></span>

`-h|--help`

<span data-ttu-id="db029-122">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="db029-122">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="db029-123">Örnekler</span><span class="sxs-lookup"><span data-stu-id="db029-123">Examples</span></span>

<span data-ttu-id="db029-124">Bir C# projesi çözüme ekleyin:</span><span class="sxs-lookup"><span data-stu-id="db029-124">Add a C# project to a solution:</span></span>

`dotnet sln todo.sln add todo-app/todo-app.csproj`

<span data-ttu-id="db029-125">Bir C# projesi bir çözümden Kaldır:</span><span class="sxs-lookup"><span data-stu-id="db029-125">Remove a C# project from a solution:</span></span>

`dotnet sln todo.sln remove todo-app/todo-app.csproj`

<span data-ttu-id="db029-126">Birden çok C# projeleri çözüme ekleyin:</span><span class="sxs-lookup"><span data-stu-id="db029-126">Add multiple C# projects to a solution:</span></span>

`dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj`

<span data-ttu-id="db029-127">Birden çok C# projelerini bir çözümden Kaldır:</span><span class="sxs-lookup"><span data-stu-id="db029-127">Remove multiple C# projects from a solution:</span></span>

`dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj`

<span data-ttu-id="db029-128">Birden çok C# projelerinde, Glob deseni kullanılarak çözüm ekleyin:</span><span class="sxs-lookup"><span data-stu-id="db029-128">Add multiple C# projects to a solution using a globbing pattern:</span></span>

`dotnet sln todo.sln add **/*.csproj`

<span data-ttu-id="db029-129">Birden çok C# projelerinde, Glob deseni kullanılarak bir çözümden kaldırmak:</span><span class="sxs-lookup"><span data-stu-id="db029-129">Remove multiple C# projects from a solution using a globbing pattern:</span></span>

`dotnet sln todo.sln remove **/*.csproj`

> [!NOTE]
> <span data-ttu-id="db029-130">Genelleştirme CLI özelliği ancak yerine bir komut kabuğu özelliği değil.</span><span class="sxs-lookup"><span data-stu-id="db029-130">Globbing is not a CLI feature but rather a feature of the command shell.</span></span> <span data-ttu-id="db029-131">Dosyalar başarılı bir şekilde genişletmek için genelleştirme destekleyen bir kabuk kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="db029-131">To successfully expand the files, you must use a shell that supports globbing.</span></span> <span data-ttu-id="db029-132">Genelleştirme hakkında daha fazla bilgi için bkz: [Wikipedia](https://en.wikipedia.org/wiki/Glob_(programming)).</span><span class="sxs-lookup"><span data-stu-id="db029-132">For more information about globbing, see [Wikipedia](https://en.wikipedia.org/wiki/Glob_(programming)).</span></span>
