---
title: DotNet Listele başvuru komutu
description: Dotnet listesi başvuru komut listesi projeden projeye başvurular için uygun bir seçenek sağlar.
ms.date: 12/03/2018
ms.openlocfilehash: d22ea27f8e8f6b94d763e44a6d8644f814663797
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665058"
---
# <a name="dotnet-list-reference"></a><span data-ttu-id="d2fe1-103">DotNet listesi başvurusu</span><span class="sxs-lookup"><span data-stu-id="d2fe1-103">dotnet list reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="d2fe1-104">Ad</span><span class="sxs-lookup"><span data-stu-id="d2fe1-104">Name</span></span>

<span data-ttu-id="d2fe1-105">`dotnet list reference` -Projeden projeye başvurular listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="d2fe1-105">`dotnet list reference` - Lists project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d2fe1-106">Synopsis</span><span class="sxs-lookup"><span data-stu-id="d2fe1-106">Synopsis</span></span>

`dotnet list [<PROJECT>] reference [-h|--help]`

## <a name="description"></a><span data-ttu-id="d2fe1-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d2fe1-107">Description</span></span>

<span data-ttu-id="d2fe1-108">`dotnet list reference` Komut listesi proje başvurularını belirtilen proje veya çözüm için uygun bir seçenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="d2fe1-108">The `dotnet list reference` command provides a convenient option to list project references for a given project or solution.</span></span>

## <a name="arguments"></a><span data-ttu-id="d2fe1-109">Arguments</span><span class="sxs-lookup"><span data-stu-id="d2fe1-109">Arguments</span></span>

* **`PROJECT`**

  <span data-ttu-id="d2fe1-110">Başvuruları listelemek için kullanılacak proje dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d2fe1-110">Specifies the project file to use for listing references.</span></span> <span data-ttu-id="d2fe1-111">Belirtilmezse, komut, bir proje dosyasını geçerli dizinde arar.</span><span class="sxs-lookup"><span data-stu-id="d2fe1-111">If not specified, the command searches the current directory for a project file.</span></span>

## <a name="options"></a><span data-ttu-id="d2fe1-112">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="d2fe1-112">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="d2fe1-113">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="d2fe1-113">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="d2fe1-114">Örnekler</span><span class="sxs-lookup"><span data-stu-id="d2fe1-114">Examples</span></span>

* <span data-ttu-id="d2fe1-115">Belirtilen proje için proje başvuruları listeleyin:</span><span class="sxs-lookup"><span data-stu-id="d2fe1-115">List the project references for the specified project:</span></span>

  ```console
  dotnet list app/app.csproj reference
  ```

* <span data-ttu-id="d2fe1-116">Geçerli dizinde proje için proje başvuruları listeleyin:</span><span class="sxs-lookup"><span data-stu-id="d2fe1-116">List the project references for the project in the current directory:</span></span>

  ```console
  dotnet list reference
  ```