---
title: DotNet sln command - .NET Core CLI
description: Dotnet sln komutu eklemek, kaldırmak ve bir çözüm dosyasını projelerinde listelemek için uygun bir seçenek sağlar.
author: mairaw
ms.author: mairaw
ms.date: 06/13/2018
ms.openlocfilehash: 65ae402ef5519863886c8cf833598f5314b4bdad
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208342"
---
# <a name="dotnet-sln"></a><span data-ttu-id="4f71d-103">DotNet sln</span><span class="sxs-lookup"><span data-stu-id="4f71d-103">dotnet sln</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="4f71d-104">Ad</span><span class="sxs-lookup"><span data-stu-id="4f71d-104">Name</span></span>

<span data-ttu-id="4f71d-105">`dotnet sln` -Bir .NET Core çözüm dosyasını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="4f71d-105">`dotnet sln` - Modifies a .NET Core solution file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="4f71d-106">Özet</span><span class="sxs-lookup"><span data-stu-id="4f71d-106">Synopsis</span></span>

```
dotnet sln [<SOLUTION_NAME>] add <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] add <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] remove <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] remove <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] list
dotnet sln [-h|--help]
```

## <a name="description"></a><span data-ttu-id="4f71d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4f71d-107">Description</span></span>

<span data-ttu-id="4f71d-108">`dotnet sln` Komut eklemek, kaldırmak ve bir çözüm dosyasını projelerinde listelemek için kullanışlı bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="4f71d-108">The `dotnet sln` command provides a convenient way to add, remove, and list projects in a solution file.</span></span>

<span data-ttu-id="4f71d-109">Kullanılacak `dotnet sln` komutu, çözüm dosya zaten bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4f71d-109">To use the `dotnet sln` command, the solution file must already exist.</span></span> <span data-ttu-id="4f71d-110">Bir oluşturmanız gerekiyorsa, kullanın [dotnet yeni](dotnet-new.md) komutunu gibi aşağıdaki örnekte:</span><span class="sxs-lookup"><span data-stu-id="4f71d-110">If you need to create one, use the [dotnet new](dotnet-new.md) command, like in the following example:</span></span>

```
dotnet new sln
```

## <a name="commands"></a><span data-ttu-id="4f71d-111">Komutlar</span><span class="sxs-lookup"><span data-stu-id="4f71d-111">Commands</span></span>

`add <PROJECT> ...`

`add <GLOBBING_PATTERN>`

<span data-ttu-id="4f71d-112">Bir proje veya birden çok proje çözümü dosyasına ekler.</span><span class="sxs-lookup"><span data-stu-id="4f71d-112">Adds a project or multiple projects to the solution file.</span></span> <span data-ttu-id="4f71d-113">[Genelleme desenleri](https://en.wikipedia.org/wiki/Glob_(programming)) UNIX/Linux tabanlı Terminal üzerinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="4f71d-113">[Globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

`remove <PROJECT> ...`

`remove <GLOBBING_PATTERN>`

<span data-ttu-id="4f71d-114">Bir proje veya birden çok proje çözümü dosyasından kaldırır.</span><span class="sxs-lookup"><span data-stu-id="4f71d-114">Removes a project or multiple projects from the solution file.</span></span> <span data-ttu-id="4f71d-115">[Genelleme desenleri](https://en.wikipedia.org/wiki/Glob_(programming)) UNIX/Linux tabanlı Terminal üzerinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="4f71d-115">[Globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

`list`

<span data-ttu-id="4f71d-116">Bir çözüm dosyasındaki tüm projeleri listeler.</span><span class="sxs-lookup"><span data-stu-id="4f71d-116">Lists all projects in a solution file.</span></span>

## <a name="arguments"></a><span data-ttu-id="4f71d-117">Arguments</span><span class="sxs-lookup"><span data-stu-id="4f71d-117">Arguments</span></span>

`SOLUTION_NAME`

<span data-ttu-id="4f71d-118">Çözüm dosyası kullanın.</span><span class="sxs-lookup"><span data-stu-id="4f71d-118">Solution file to use.</span></span> <span data-ttu-id="4f71d-119">Belirtilmezse, komut için geçerli dizin arar.</span><span class="sxs-lookup"><span data-stu-id="4f71d-119">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="4f71d-120">Dizinde birden çok çözüm dosyalarını varsa belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="4f71d-120">If there are multiple solution files in the directory, one must be specified.</span></span>

## <a name="options"></a><span data-ttu-id="4f71d-121">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="4f71d-121">Options</span></span>

`-h|--help`

<span data-ttu-id="4f71d-122">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="4f71d-122">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="4f71d-123">Örnekler</span><span class="sxs-lookup"><span data-stu-id="4f71d-123">Examples</span></span>

<span data-ttu-id="4f71d-124">Bir C# projesi bir çözüme ekleyin:</span><span class="sxs-lookup"><span data-stu-id="4f71d-124">Add a C# project to a solution:</span></span>

`dotnet sln todo.sln add todo-app/todo-app.csproj`

<span data-ttu-id="4f71d-125">Bir C# projesi bir çözümden kaldırın:</span><span class="sxs-lookup"><span data-stu-id="4f71d-125">Remove a C# project from a solution:</span></span>

`dotnet sln todo.sln remove todo-app/todo-app.csproj`

<span data-ttu-id="4f71d-126">Birden çok C# projeleri bir çözüme ekleyin:</span><span class="sxs-lookup"><span data-stu-id="4f71d-126">Add multiple C# projects to a solution:</span></span>

`dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj`

<span data-ttu-id="4f71d-127">Birden çok C# projeleri bir çözümden kaldırın:</span><span class="sxs-lookup"><span data-stu-id="4f71d-127">Remove multiple C# projects from a solution:</span></span>

`dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj`

<span data-ttu-id="4f71d-128">Birden çok C# projeleri genelleme desen kullanan bir çözüme ekleyin:</span><span class="sxs-lookup"><span data-stu-id="4f71d-128">Add multiple C# projects to a solution using a globbing pattern:</span></span>

`dotnet sln todo.sln add **/*.csproj`

<span data-ttu-id="4f71d-129">Birden çok C# projeleri genelleme desen kullanan bir çözüm kaldırın:</span><span class="sxs-lookup"><span data-stu-id="4f71d-129">Remove multiple C# projects from a solution using a globbing pattern:</span></span>

`dotnet sln todo.sln remove **/*.csproj`
