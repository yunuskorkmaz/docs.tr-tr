---
title: DotNet sln command - .NET Core CLI
description: "Dotnet sln komutu eklemek, kaldırmak ve bir çözüm dosyasını projelerinde listelemek için uygun bir seçenek sağlar."
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: deb66ff52074630616c7be47f1a9751246db501d
ms.sourcegitcommit: 70dcc89737127e4d5f20500242409b687e51b07e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/11/2018
---
# <a name="dotnet-sln"></a><span data-ttu-id="a1eb0-103">DotNet sln</span><span class="sxs-lookup"><span data-stu-id="a1eb0-103">dotnet sln</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="a1eb0-104">Ad</span><span class="sxs-lookup"><span data-stu-id="a1eb0-104">Name</span></span>

<span data-ttu-id="a1eb0-105">`dotnet sln`-Bir .NET Core çözüm dosyasını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="a1eb0-105">`dotnet sln` - Modifies a .NET Core solution file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a1eb0-106">Özet</span><span class="sxs-lookup"><span data-stu-id="a1eb0-106">Synopsis</span></span>

```
dotnet sln [<SOLUTION_NAME>] add <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] add <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] remove <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] remove <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] list
dotnet sln [-h|--help]
```

## <a name="description"></a><span data-ttu-id="a1eb0-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a1eb0-107">Description</span></span>

<span data-ttu-id="a1eb0-108">`dotnet sln` Komut eklemek, kaldırmak ve bir çözüm dosyasını projelerinde listelemek için kullanışlı bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="a1eb0-108">The `dotnet sln` command provides a convenient way to add, remove, and list projects in a solution file.</span></span>

## <a name="commands"></a><span data-ttu-id="a1eb0-109">Komutlar</span><span class="sxs-lookup"><span data-stu-id="a1eb0-109">Commands</span></span>

`add <PROJECT> ...`

`add <GLOBBING_PATTERN>`

<span data-ttu-id="a1eb0-110">Bir proje veya birden çok proje çözümü dosyasına ekler.</span><span class="sxs-lookup"><span data-stu-id="a1eb0-110">Adds a project or multiple projects to the solution file.</span></span> <span data-ttu-id="a1eb0-111">[Genelleme desenleri](https://en.wikipedia.org/wiki/Glob_(programming)) UNIX/Linux tabanlı Terminal üzerinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="a1eb0-111">[Globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

`remove <PROJECT> ...`

`remove <GLOBBING_PATTERN>`

<span data-ttu-id="a1eb0-112">Bir proje veya birden çok proje çözümü dosyasından kaldırır.</span><span class="sxs-lookup"><span data-stu-id="a1eb0-112">Removes a project or multiple projects from the solution file.</span></span> <span data-ttu-id="a1eb0-113">[Genelleme desenleri](https://en.wikipedia.org/wiki/Glob_(programming)) UNIX/Linux tabanlı Terminal üzerinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="a1eb0-113">[Globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

`list`

<span data-ttu-id="a1eb0-114">Bir çözüm dosyasındaki tüm projeleri listeler.</span><span class="sxs-lookup"><span data-stu-id="a1eb0-114">Lists all projects in a solution file.</span></span>

## <a name="arguments"></a><span data-ttu-id="a1eb0-115">Arguments</span><span class="sxs-lookup"><span data-stu-id="a1eb0-115">Arguments</span></span>

`SOLUTION_NAME`

<span data-ttu-id="a1eb0-116">Çözüm dosyası kullanın.</span><span class="sxs-lookup"><span data-stu-id="a1eb0-116">Solution file to use.</span></span> <span data-ttu-id="a1eb0-117">Belirtilmezse, komut için geçerli dizin arar.</span><span class="sxs-lookup"><span data-stu-id="a1eb0-117">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="a1eb0-118">Dizinde birden çok çözüm dosyalarını varsa belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="a1eb0-118">If there are multiple solution files in the directory, one must be specified.</span></span>

## <a name="options"></a><span data-ttu-id="a1eb0-119">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="a1eb0-119">Options</span></span>

`-h|--help`

<span data-ttu-id="a1eb0-120">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="a1eb0-120">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="a1eb0-121">Örnekler</span><span class="sxs-lookup"><span data-stu-id="a1eb0-121">Examples</span></span>

<span data-ttu-id="a1eb0-122">Bir C# projesi bir çözüme ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a1eb0-122">Add a C# project to a solution:</span></span>

`dotnet sln todo.sln add todo-app/todo-app.csproj`

<span data-ttu-id="a1eb0-123">Bir C# projesi bir çözümden kaldırın:</span><span class="sxs-lookup"><span data-stu-id="a1eb0-123">Remove a C# project from a solution:</span></span>

`dotnet sln todo.sln remove todo-app/todo-app.csproj`

<span data-ttu-id="a1eb0-124">Birden çok C# projeleri bir çözüme ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a1eb0-124">Add multiple C# projects to a solution:</span></span>

`dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj`

<span data-ttu-id="a1eb0-125">Birden çok C# projeleri bir çözümden kaldırın:</span><span class="sxs-lookup"><span data-stu-id="a1eb0-125">Remove multiple C# projects from a solution:</span></span>

`dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj`

<span data-ttu-id="a1eb0-126">Birden çok C# projeleri genelleme desen kullanan bir çözüme ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a1eb0-126">Add multiple C# projects to a solution using a globbing pattern:</span></span>

`dotnet sln todo.sln add **/*.csproj`

<span data-ttu-id="a1eb0-127">Birden çok C# projeleri genelleme desen kullanan bir çözüm kaldırın:</span><span class="sxs-lookup"><span data-stu-id="a1eb0-127">Remove multiple C# projects from a solution using a globbing pattern:</span></span>

`dotnet sln todo.sln remove **/*.csproj`
