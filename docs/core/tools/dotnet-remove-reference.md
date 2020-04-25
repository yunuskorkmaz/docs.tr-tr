---
title: DotNet Remove başvuru komutu
description: DotNet Remove Reference komutu, projeyi Proje başvurularına kaldırmak için kullanışlı bir seçenek sağlar.
ms.date: 02/14/2020
ms.openlocfilehash: a45153376d7d6eb764c1d2c6b473d04a273a2de1
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158339"
---
# <a name="dotnet-remove-reference"></a><span data-ttu-id="83a71-103">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="83a71-103">dotnet remove reference</span></span>

<span data-ttu-id="83a71-104">**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 2. x SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="83a71-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="83a71-105">Adı</span><span class="sxs-lookup"><span data-stu-id="83a71-105">Name</span></span>

<span data-ttu-id="83a71-106">`dotnet remove reference`-Projeden projeye (P2P) başvurularını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="83a71-106">`dotnet remove reference` - Removes project-to-project (P2P) references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="83a71-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="83a71-107">Synopsis</span></span>

```dotnetcli
dotnet remove [<PROJECT>] reference [-f|--framework <FRAMEWORK>]
     <PROJECT_REFERENCES>

dotnet remove reference -h|--help
```

## <a name="description"></a><span data-ttu-id="83a71-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="83a71-108">Description</span></span>

<span data-ttu-id="83a71-109">Komut `dotnet remove reference` , bir projeden proje başvurularını kaldırmak için kullanışlı bir seçenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="83a71-109">The `dotnet remove reference` command provides a convenient option to remove project references from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="83a71-110">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="83a71-110">Arguments</span></span>

`PROJECT`

<span data-ttu-id="83a71-111">Hedef proje dosyası.</span><span class="sxs-lookup"><span data-stu-id="83a71-111">Target project file.</span></span> <span data-ttu-id="83a71-112">Belirtilmemişse, komut geçerli dizinde bir arama yapar.</span><span class="sxs-lookup"><span data-stu-id="83a71-112">If not specified, the command searches the current directory for one.</span></span>

`PROJECT_REFERENCES`

<span data-ttu-id="83a71-113">Kaldırılacak projeden projeye (P2P) başvuruları.</span><span class="sxs-lookup"><span data-stu-id="83a71-113">Project-to-project (P2P) references to remove.</span></span> <span data-ttu-id="83a71-114">Bir veya daha fazla proje belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="83a71-114">You can specify one or multiple projects.</span></span> <span data-ttu-id="83a71-115">[Glob desenleri](https://en.wikipedia.org/wiki/Glob_(programming)) UNIX/Linux tabanlı terminallerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="83a71-115">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

## <a name="options"></a><span data-ttu-id="83a71-116">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="83a71-116">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="83a71-117">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="83a71-117">Prints out a short help for the command.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="83a71-118">Başvuruyu yalnızca, tfd biçimini kullanarak belirli bir [çerçeveyi](../../standard/frameworks.md) hedeflerken kaldırır.</span><span class="sxs-lookup"><span data-stu-id="83a71-118">Removes the reference only when targeting a specific [framework](../../standard/frameworks.md) using the TFM format.</span></span>

## <a name="examples"></a><span data-ttu-id="83a71-119">Örnekler</span><span class="sxs-lookup"><span data-stu-id="83a71-119">Examples</span></span>

- <span data-ttu-id="83a71-120">Belirtilen projeden bir proje başvurusunu kaldır:</span><span class="sxs-lookup"><span data-stu-id="83a71-120">Remove a project reference from the specified project:</span></span>

  ```dotnetcli
  dotnet remove app/app.csproj reference lib/lib.csproj
  ```

- <span data-ttu-id="83a71-121">Geçerli dizindeki projeden birden çok proje başvurusu kaldır:</span><span class="sxs-lookup"><span data-stu-id="83a71-121">Remove multiple project references from the project in the current directory:</span></span>

  ```dotnetcli
  dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj
  ```

- <span data-ttu-id="83a71-122">UNIX/Linux 'ta glob modelini kullanarak birden çok proje başvurusu kaldırma:</span><span class="sxs-lookup"><span data-stu-id="83a71-122">Remove multiple project references using a glob pattern on Unix/Linux:</span></span>

  ```dotnetcli
  dotnet remove app/app.csproj reference **/*.csproj`
  ```
