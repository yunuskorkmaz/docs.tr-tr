---
title: dotnet kaldırma başvuru komutu
description: Dotnet kaldırma başvuru komutu proje başvurularını kaldırmak için uygun bir seçenek sağlar.
ms.date: 02/14/2020
ms.openlocfilehash: 92d36bbbde64d806abc8f223c5f08e3f3d79ce9d
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463438"
---
# <a name="dotnet-remove-reference"></a><span data-ttu-id="e9b2d-103">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="e9b2d-103">dotnet remove reference</span></span>

<span data-ttu-id="e9b2d-104">**Bu makale şu şekilde dir:** ✔️ .NET Core 2.x SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="e9b2d-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="e9b2d-105">Adı</span><span class="sxs-lookup"><span data-stu-id="e9b2d-105">Name</span></span>

<span data-ttu-id="e9b2d-106">`dotnet remove reference`- Projeden projeye başvuruları kaldırır.</span><span class="sxs-lookup"><span data-stu-id="e9b2d-106">`dotnet remove reference` - Removes project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="e9b2d-107">Özet</span><span class="sxs-lookup"><span data-stu-id="e9b2d-107">Synopsis</span></span>

```dotnetcli
dotnet remove [<PROJECT>] reference [-f|--framework <FRAMEWORK>] <PROJECT_REFERENCES>

dotnet remove reference -h|--help
```

## <a name="description"></a><span data-ttu-id="e9b2d-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e9b2d-108">Description</span></span>

<span data-ttu-id="e9b2d-109">Komut, `dotnet remove reference` proje başvurularını projeden kaldırmak için kullanışlı bir seçenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="e9b2d-109">The `dotnet remove reference` command provides a convenient option to remove project references from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="e9b2d-110">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="e9b2d-110">Arguments</span></span>

`PROJECT`

<span data-ttu-id="e9b2d-111">Hedef proje dosyası.</span><span class="sxs-lookup"><span data-stu-id="e9b2d-111">Target project file.</span></span> <span data-ttu-id="e9b2d-112">Belirtilmemişse, komut geçerli dizini arar.</span><span class="sxs-lookup"><span data-stu-id="e9b2d-112">If not specified, the command searches the current directory for one.</span></span>

`PROJECT_REFERENCES`

<span data-ttu-id="e9b2d-113">Kaldırılacak proje-proje (P2P) başvuruları.</span><span class="sxs-lookup"><span data-stu-id="e9b2d-113">Project-to-project (P2P) references to remove.</span></span> <span data-ttu-id="e9b2d-114">Bir veya birden çok proje belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e9b2d-114">You can specify one or multiple projects.</span></span> <span data-ttu-id="e9b2d-115">[Glob desenleri](https://en.wikipedia.org/wiki/Glob_(programming)) Unix/Linux tabanlı terminallerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e9b2d-115">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

## <a name="options"></a><span data-ttu-id="e9b2d-116">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="e9b2d-116">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="e9b2d-117">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="e9b2d-117">Prints out a short help for the command.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="e9b2d-118">Başvuruyu yalnızca belirli bir [çerçeveyi](../../standard/frameworks.md)hedefalırken kaldırır.</span><span class="sxs-lookup"><span data-stu-id="e9b2d-118">Removes the reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

## <a name="examples"></a><span data-ttu-id="e9b2d-119">Örnekler</span><span class="sxs-lookup"><span data-stu-id="e9b2d-119">Examples</span></span>

- <span data-ttu-id="e9b2d-120">Proje başvurularını belirtilen projeden kaldırma:</span><span class="sxs-lookup"><span data-stu-id="e9b2d-120">Remove a project reference from the specified project:</span></span>

  ```dotnetcli
  dotnet remove app/app.csproj reference lib/lib.csproj
  ```

- <span data-ttu-id="e9b2d-121">Geçerli dizinde projeden birden çok proje öncesini kaldırın:</span><span class="sxs-lookup"><span data-stu-id="e9b2d-121">Remove multiple project references from the project in the current directory:</span></span>

  ```dotnetcli
  dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj
  ```

- <span data-ttu-id="e9b2d-122">Unix/Linux'ta glob deseni kullanarak birden çok proje referansı kaldırın:</span><span class="sxs-lookup"><span data-stu-id="e9b2d-122">Remove multiple project references using a glob pattern on Unix/Linux:</span></span>

  ```dotnetcli
  dotnet remove app/app.csproj reference **/*.csproj`
  ```
