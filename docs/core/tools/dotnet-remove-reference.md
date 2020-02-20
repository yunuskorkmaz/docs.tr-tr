---
title: DotNet Remove başvuru komutu
description: DotNet Remove Reference komutu, projeyi Proje başvurularına kaldırmak için kullanışlı bir seçenek sağlar.
ms.date: 02/14/2020
ms.openlocfilehash: fcadf677faaf9281fb019c3c4bb16efc906b1aa1
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503623"
---
# <a name="dotnet-remove-reference"></a><span data-ttu-id="78c81-103">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="78c81-103">dotnet remove reference</span></span>

<span data-ttu-id="78c81-104">**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 2. x SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="78c81-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="78c81-105">Adı</span><span class="sxs-lookup"><span data-stu-id="78c81-105">Name</span></span>

<span data-ttu-id="78c81-106">`dotnet remove reference`-projeden projeye başvuruları kaldırır.</span><span class="sxs-lookup"><span data-stu-id="78c81-106">`dotnet remove reference` - Removes project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="78c81-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="78c81-107">Synopsis</span></span>

```dotnetcli
dotnet remove [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]
```

## <a name="description"></a><span data-ttu-id="78c81-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="78c81-108">Description</span></span>

<span data-ttu-id="78c81-109">`dotnet remove reference` komutu bir projeden proje başvurularını kaldırmak için kullanışlı bir seçenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="78c81-109">The `dotnet remove reference` command provides a convenient option to remove project references from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="78c81-110">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="78c81-110">Arguments</span></span>

`PROJECT`

<span data-ttu-id="78c81-111">Hedef proje dosyası.</span><span class="sxs-lookup"><span data-stu-id="78c81-111">Target project file.</span></span> <span data-ttu-id="78c81-112">Belirtilmemişse, komut geçerli dizinde bir arama yapar.</span><span class="sxs-lookup"><span data-stu-id="78c81-112">If not specified, the command searches the current directory for one.</span></span>

`PROJECT_REFERENCES`

<span data-ttu-id="78c81-113">Kaldırılacak projeden projeye (P2P) başvuruları.</span><span class="sxs-lookup"><span data-stu-id="78c81-113">Project-to-project (P2P) references to remove.</span></span> <span data-ttu-id="78c81-114">Bir veya daha fazla proje belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78c81-114">You can specify one or multiple projects.</span></span> <span data-ttu-id="78c81-115">[Glob desenleri](https://en.wikipedia.org/wiki/Glob_(programming)) UNIX/Linux tabanlı terminallerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="78c81-115">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

## <a name="options"></a><span data-ttu-id="78c81-116">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="78c81-116">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="78c81-117">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="78c81-117">Prints out a short help for the command.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="78c81-118">Yalnızca belirli bir [çerçeveyi](../../standard/frameworks.md)hedeflerken başvuruyu kaldırır.</span><span class="sxs-lookup"><span data-stu-id="78c81-118">Removes the reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

## <a name="examples"></a><span data-ttu-id="78c81-119">Örnekler</span><span class="sxs-lookup"><span data-stu-id="78c81-119">Examples</span></span>

- <span data-ttu-id="78c81-120">Belirtilen projeden bir proje başvurusunu kaldır:</span><span class="sxs-lookup"><span data-stu-id="78c81-120">Remove a project reference from the specified project:</span></span>

  ```dotnetcli
  dotnet remove app/app.csproj reference lib/lib.csproj
  ```

- <span data-ttu-id="78c81-121">Geçerli dizindeki projeden birden çok proje başvurusu kaldır:</span><span class="sxs-lookup"><span data-stu-id="78c81-121">Remove multiple project references from the project in the current directory:</span></span>

  ```dotnetcli
  dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj
  ```

- <span data-ttu-id="78c81-122">UNIX/Linux 'ta glob modelini kullanarak birden çok proje başvurusu kaldırma:</span><span class="sxs-lookup"><span data-stu-id="78c81-122">Remove multiple project references using a glob pattern on Unix/Linux:</span></span>

  ```dotnetcli
  dotnet remove app/app.csproj reference **/*.csproj`
  ```
