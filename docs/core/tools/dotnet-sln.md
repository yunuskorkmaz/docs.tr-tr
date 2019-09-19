---
title: DotNet sln komutu
description: DotNet-sln komutu bir çözüm dosyasındaki projeleri eklemek, kaldırmak ve listelemek için kullanışlı bir seçenek sağlar.
ms.date: 06/13/2018
ms.openlocfilehash: 84508aaefff61b31e2965576ebc2daaae7331951
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117586"
---
# <a name="dotnet-sln"></a><span data-ttu-id="1121d-103">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="1121d-103">dotnet sln</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="1121d-104">Ad</span><span class="sxs-lookup"><span data-stu-id="1121d-104">Name</span></span>

<span data-ttu-id="1121d-105">`dotnet sln`-Bir .NET Core çözüm dosyasını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="1121d-105">`dotnet sln` - Modifies a .NET Core solution file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="1121d-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="1121d-106">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_NAME>] add <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] add <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] remove <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] remove <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] list
dotnet sln [-h|--help]
```

## <a name="description"></a><span data-ttu-id="1121d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1121d-107">Description</span></span>

<span data-ttu-id="1121d-108">`dotnet sln` Komut, bir çözüm dosyasındaki projeleri eklemek, kaldırmak ve listelemek için kullanışlı bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="1121d-108">The `dotnet sln` command provides a convenient way to add, remove, and list projects in a solution file.</span></span>

<span data-ttu-id="1121d-109">`dotnet sln` Komutunu kullanmak için, çözüm dosyası zaten var olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1121d-109">To use the `dotnet sln` command, the solution file must already exist.</span></span> <span data-ttu-id="1121d-110">Bir tane oluşturmanız gerekiyorsa, aşağıdaki örnekte olduğu gibi [DotNet New](dotnet-new.md) komutunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="1121d-110">If you need to create one, use the [dotnet new](dotnet-new.md) command, like in the following example:</span></span>

```dotnetcli
dotnet new sln
```

## <a name="commands"></a><span data-ttu-id="1121d-111">Komutlar</span><span class="sxs-lookup"><span data-stu-id="1121d-111">Commands</span></span>

`add <PROJECT> ...`

`add <GLOBBING_PATTERN>`

<span data-ttu-id="1121d-112">Çözüm dosyasına bir proje veya birden çok proje ekler.</span><span class="sxs-lookup"><span data-stu-id="1121d-112">Adds a project or multiple projects to the solution file.</span></span> <span data-ttu-id="1121d-113">[Glob desenleri](https://en.wikipedia.org/wiki/Glob_(programming)) UNIX/Linux tabanlı terminallerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="1121d-113">[Globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

`remove <PROJECT> ...`

`remove <GLOBBING_PATTERN>`

<span data-ttu-id="1121d-114">Çözüm dosyasından bir projeyi veya birden çok projeyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="1121d-114">Removes a project or multiple projects from the solution file.</span></span> <span data-ttu-id="1121d-115">[Glob desenleri](https://en.wikipedia.org/wiki/Glob_(programming)) UNIX/Linux tabanlı terminallerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="1121d-115">[Globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

`list`

<span data-ttu-id="1121d-116">Bir çözüm dosyasındaki tüm projeleri listeler.</span><span class="sxs-lookup"><span data-stu-id="1121d-116">Lists all projects in a solution file.</span></span>

## <a name="arguments"></a><span data-ttu-id="1121d-117">Arguments</span><span class="sxs-lookup"><span data-stu-id="1121d-117">Arguments</span></span>

`SOLUTION_NAME`

<span data-ttu-id="1121d-118">Kullanılacak çözüm dosyası.</span><span class="sxs-lookup"><span data-stu-id="1121d-118">Solution file to use.</span></span> <span data-ttu-id="1121d-119">Belirtilmemişse, komut geçerli dizinde bir arama yapar.</span><span class="sxs-lookup"><span data-stu-id="1121d-119">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="1121d-120">Dizinde birden çok çözüm dosyası varsa, birinin belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="1121d-120">If there are multiple solution files in the directory, one must be specified.</span></span>

## <a name="options"></a><span data-ttu-id="1121d-121">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="1121d-121">Options</span></span>

`-h|--help`

<span data-ttu-id="1121d-122">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="1121d-122">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="1121d-123">Örnekler</span><span class="sxs-lookup"><span data-stu-id="1121d-123">Examples</span></span>

<span data-ttu-id="1121d-124">Bir çözüme C# proje ekleme:</span><span class="sxs-lookup"><span data-stu-id="1121d-124">Add a C# project to a solution:</span></span>

`dotnet sln todo.sln add todo-app/todo-app.csproj`

<span data-ttu-id="1121d-125">Bir C# projeyi çözümden kaldırma:</span><span class="sxs-lookup"><span data-stu-id="1121d-125">Remove a C# project from a solution:</span></span>

`dotnet sln todo.sln remove todo-app/todo-app.csproj`

<span data-ttu-id="1121d-126">Bir çözüme C# birden çok proje ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1121d-126">Add multiple C# projects to a solution:</span></span>

`dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj`

<span data-ttu-id="1121d-127">Bir çözümden C# birden çok proje kaldırma:</span><span class="sxs-lookup"><span data-stu-id="1121d-127">Remove multiple C# projects from a solution:</span></span>

`dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj`

<span data-ttu-id="1121d-128">Bir glob C# deseninin kullanıldığı bir çözüme birden fazla proje ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1121d-128">Add multiple C# projects to a solution using a globbing pattern:</span></span>

`dotnet sln todo.sln add **/*.csproj`

<span data-ttu-id="1121d-129">Bir glob C# deseninin kullanıldığı bir çözümden birden fazla projeyi kaldırma:</span><span class="sxs-lookup"><span data-stu-id="1121d-129">Remove multiple C# projects from a solution using a globbing pattern:</span></span>

`dotnet sln todo.sln remove **/*.csproj`

> [!NOTE]
> <span data-ttu-id="1121d-130">Glob, bir CLı özelliği değil, bir komut kabuğu özelliği değil.</span><span class="sxs-lookup"><span data-stu-id="1121d-130">Globbing is not a CLI feature but rather a feature of the command shell.</span></span> <span data-ttu-id="1121d-131">Dosyaları başarılı bir şekilde genişletmek için glob destekleyen bir kabuk kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1121d-131">To successfully expand the files, you must use a shell that supports globbing.</span></span> <span data-ttu-id="1121d-132">Glob hakkında daha fazla bilgi için bkz. [Vikipedi](https://en.wikipedia.org/wiki/Glob_(programming)).</span><span class="sxs-lookup"><span data-stu-id="1121d-132">For more information about globbing, see [Wikipedia](https://en.wikipedia.org/wiki/Glob_(programming)).</span></span>
