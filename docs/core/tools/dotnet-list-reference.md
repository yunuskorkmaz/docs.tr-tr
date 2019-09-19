---
title: DotNet liste başvurusu komutu
description: DotNet liste başvurusu komutu, projeyi Proje başvurularına göre listelemek için kullanışlı bir seçenek sağlar.
ms.date: 06/26/2019
ms.openlocfilehash: b4b82ca1e7aeb2b73d9f99aff1c97452b2166770
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117670"
---
# <a name="dotnet-list-reference"></a><span data-ttu-id="f1755-103">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="f1755-103">dotnet list reference</span></span>

<span data-ttu-id="f1755-104">**Bu konu şu şekilde geçerlidir: ✓** .NET Core 1. x SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="f1755-104">**This topic applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="f1755-105">Ad</span><span class="sxs-lookup"><span data-stu-id="f1755-105">Name</span></span>

<span data-ttu-id="f1755-106">`dotnet list reference`-Projeden projeye başvuruları listeler.</span><span class="sxs-lookup"><span data-stu-id="f1755-106">`dotnet list reference` - Lists project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f1755-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="f1755-107">Synopsis</span></span>

`dotnet list [<PROJECT>|<SOLUTION>] reference [-h|--help]`

## <a name="description"></a><span data-ttu-id="f1755-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f1755-108">Description</span></span>

<span data-ttu-id="f1755-109">Komut `dotnet list reference` , belirli bir proje veya çözümün proje başvurularını listelemek için uygun bir seçenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="f1755-109">The `dotnet list reference` command provides a convenient option to list project references for a given project or solution.</span></span>

## <a name="arguments"></a><span data-ttu-id="f1755-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="f1755-110">Arguments</span></span>

* **`PROJECT | SOLUTION`**

  <span data-ttu-id="f1755-111">Başvuruları listelemek için kullanılacak proje veya çözüm dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f1755-111">Specifies the project or solution file to use for listing references.</span></span> <span data-ttu-id="f1755-112">Belirtilmemişse, komut geçerli dizinde bir proje dosyası arar.</span><span class="sxs-lookup"><span data-stu-id="f1755-112">If not specified, the command searches the current directory for a project file.</span></span>

## <a name="options"></a><span data-ttu-id="f1755-113">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="f1755-113">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="f1755-114">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="f1755-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="f1755-115">Örnekler</span><span class="sxs-lookup"><span data-stu-id="f1755-115">Examples</span></span>

* <span data-ttu-id="f1755-116">Belirtilen proje için proje başvurularını listeleyin:</span><span class="sxs-lookup"><span data-stu-id="f1755-116">List the project references for the specified project:</span></span>

  ```dotnetcli
  dotnet list app/app.csproj reference
  ```

* <span data-ttu-id="f1755-117">Geçerli dizindeki projenin proje başvurularını listeleyin:</span><span class="sxs-lookup"><span data-stu-id="f1755-117">List the project references for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet list reference
  ```
