---
title: dotnet kaldırma başvuru komutu
description: Dotnet kaldırma başvuru komutu proje başvurularını kaldırmak için uygun bir seçenek sağlar.
ms.date: 02/14/2020
ms.openlocfilehash: fcadf677faaf9281fb019c3c4bb16efc906b1aa1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503623"
---
# <a name="dotnet-remove-reference"></a><span data-ttu-id="a66f0-103">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="a66f0-103">dotnet remove reference</span></span>

<span data-ttu-id="a66f0-104">**Bu makale şu şekilde dir:** ✔️ .NET Core 2.x SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="a66f0-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="a66f0-105">Adı</span><span class="sxs-lookup"><span data-stu-id="a66f0-105">Name</span></span>

<span data-ttu-id="a66f0-106">`dotnet remove reference`- Projeden projeye başvuruları kaldırır.</span><span class="sxs-lookup"><span data-stu-id="a66f0-106">`dotnet remove reference` - Removes project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a66f0-107">Özet</span><span class="sxs-lookup"><span data-stu-id="a66f0-107">Synopsis</span></span>

```dotnetcli
dotnet remove [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]
```

## <a name="description"></a><span data-ttu-id="a66f0-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a66f0-108">Description</span></span>

<span data-ttu-id="a66f0-109">Komut, `dotnet remove reference` proje başvurularını projeden kaldırmak için kullanışlı bir seçenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="a66f0-109">The `dotnet remove reference` command provides a convenient option to remove project references from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="a66f0-110">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="a66f0-110">Arguments</span></span>

`PROJECT`

<span data-ttu-id="a66f0-111">Hedef proje dosyası.</span><span class="sxs-lookup"><span data-stu-id="a66f0-111">Target project file.</span></span> <span data-ttu-id="a66f0-112">Belirtilmemişse, komut geçerli dizini arar.</span><span class="sxs-lookup"><span data-stu-id="a66f0-112">If not specified, the command searches the current directory for one.</span></span>

`PROJECT_REFERENCES`

<span data-ttu-id="a66f0-113">Kaldırılacak proje-proje (P2P) başvuruları.</span><span class="sxs-lookup"><span data-stu-id="a66f0-113">Project-to-project (P2P) references to remove.</span></span> <span data-ttu-id="a66f0-114">Bir veya birden çok proje belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a66f0-114">You can specify one or multiple projects.</span></span> <span data-ttu-id="a66f0-115">[Glob desenleri](https://en.wikipedia.org/wiki/Glob_(programming)) Unix/Linux tabanlı terminallerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="a66f0-115">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

## <a name="options"></a><span data-ttu-id="a66f0-116">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="a66f0-116">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="a66f0-117">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="a66f0-117">Prints out a short help for the command.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="a66f0-118">Başvuruyu yalnızca belirli bir [çerçeveyi](../../standard/frameworks.md)hedefalırken kaldırır.</span><span class="sxs-lookup"><span data-stu-id="a66f0-118">Removes the reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

## <a name="examples"></a><span data-ttu-id="a66f0-119">Örnekler</span><span class="sxs-lookup"><span data-stu-id="a66f0-119">Examples</span></span>

- <span data-ttu-id="a66f0-120">Proje başvurularını belirtilen projeden kaldırma:</span><span class="sxs-lookup"><span data-stu-id="a66f0-120">Remove a project reference from the specified project:</span></span>

  ```dotnetcli
  dotnet remove app/app.csproj reference lib/lib.csproj
  ```

- <span data-ttu-id="a66f0-121">Geçerli dizinde projeden birden çok proje öncesini kaldırın:</span><span class="sxs-lookup"><span data-stu-id="a66f0-121">Remove multiple project references from the project in the current directory:</span></span>

  ```dotnetcli
  dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj
  ```

- <span data-ttu-id="a66f0-122">Unix/Linux'ta glob deseni kullanarak birden çok proje referansı kaldırın:</span><span class="sxs-lookup"><span data-stu-id="a66f0-122">Remove multiple project references using a glob pattern on Unix/Linux:</span></span>

  ```dotnetcli
  dotnet remove app/app.csproj reference **/*.csproj`
  ```
