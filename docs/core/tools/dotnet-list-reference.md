---
title: DotNet liste başvurusu komutu
description: DotNet liste başvurusu komutu, projeyi Proje başvurularına göre listelemek için kullanışlı bir seçenek sağlar.
ms.date: 02/14/2020
ms.openlocfilehash: 43c4dbc94b33e717c6ba0a1c1c5317ac006f5bba
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503710"
---
# <a name="dotnet-list-reference"></a><span data-ttu-id="1f1ed-103">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="1f1ed-103">dotnet list reference</span></span>

<span data-ttu-id="1f1ed-104">**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 2. x SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="1f1ed-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="1f1ed-105">Adı</span><span class="sxs-lookup"><span data-stu-id="1f1ed-105">Name</span></span>

<span data-ttu-id="1f1ed-106">`dotnet list reference`-projeden projeye başvuruları listeler.</span><span class="sxs-lookup"><span data-stu-id="1f1ed-106">`dotnet list reference` - Lists project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="1f1ed-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="1f1ed-107">Synopsis</span></span>

`dotnet list [<PROJECT>|<SOLUTION>] reference [-h|--help]`

## <a name="description"></a><span data-ttu-id="1f1ed-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f1ed-108">Description</span></span>

<span data-ttu-id="1f1ed-109">`dotnet list reference` komutu, belirli bir proje veya çözümün proje başvurularını listelemek için uygun bir seçenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="1f1ed-109">The `dotnet list reference` command provides a convenient option to list project references for a given project or solution.</span></span>

## <a name="arguments"></a><span data-ttu-id="1f1ed-110">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="1f1ed-110">Arguments</span></span>

* **`PROJECT | SOLUTION`**

  <span data-ttu-id="1f1ed-111">Başvuruları listelemek için kullanılacak proje veya çözüm dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1f1ed-111">Specifies the project or solution file to use for listing references.</span></span> <span data-ttu-id="1f1ed-112">Belirtilmemişse, komut geçerli dizinde bir proje dosyası arar.</span><span class="sxs-lookup"><span data-stu-id="1f1ed-112">If not specified, the command searches the current directory for a project file.</span></span>

## <a name="options"></a><span data-ttu-id="1f1ed-113">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="1f1ed-113">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="1f1ed-114">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="1f1ed-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="1f1ed-115">Örnekler</span><span class="sxs-lookup"><span data-stu-id="1f1ed-115">Examples</span></span>

* <span data-ttu-id="1f1ed-116">Belirtilen proje için proje başvurularını listeleyin:</span><span class="sxs-lookup"><span data-stu-id="1f1ed-116">List the project references for the specified project:</span></span>

  ```dotnetcli
  dotnet list app/app.csproj reference
  ```

* <span data-ttu-id="1f1ed-117">Geçerli dizindeki projenin proje başvurularını listeleyin:</span><span class="sxs-lookup"><span data-stu-id="1f1ed-117">List the project references for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet list reference
  ```
