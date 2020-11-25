---
title: 'Son değişiklik: Directory. Packages. props dosyaları varsayılan olarak içeri aktarılır'
description: NuGet. props dosyalarının, proje klasöründe bulunursa, dizin. Packages. props adlı bir dosyayı otomatik olarak içeri aktardığından, .NET 5,0 ' deki Son değişiklik hakkında bilgi edinin.
ms.date: 09/17/2020
ms.openlocfilehash: ee8a2999b801e81750d96a0bc985e3c8169224a9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761458"
---
# <a name="directorypackagesprops-files-is-imported-by-default"></a><span data-ttu-id="c4b56-103">Directory. Packages. props dosyaları varsayılan olarak içeri aktarılır</span><span class="sxs-lookup"><span data-stu-id="c4b56-103">Directory.Packages.props files is imported by default</span></span>

<span data-ttu-id="c4b56-104">NuGet *. props* dosyaları, proje klasöründe veya üst öğelerinden birinde bulunursa, *Directory. Packages. props* adlı bir dosyayı otomatik olarak içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="c4b56-104">NuGet's *.props* files automatically import a file named *Directory.Packages.props* if it's found in the project folder or any of its ancestors.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="c4b56-105">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="c4b56-105">Version introduced</span></span>

<span data-ttu-id="c4b56-106">5.0</span><span class="sxs-lookup"><span data-stu-id="c4b56-106">5.0</span></span>

## <a name="change-description"></a><span data-ttu-id="c4b56-107">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="c4b56-107">Change description</span></span>

<span data-ttu-id="c4b56-108">Önceki .NET sürümlerinde, proje dosyanızda *Directory. Packages. props* adlı bir dosyanız olabilir ve derleme zamanında NuGet *. props* dosyası tarafından otomatik olarak içeri aktarılmaz.</span><span class="sxs-lookup"><span data-stu-id="c4b56-108">In previous .NET versions, you could have a file named *Directory.Packages.props* in your project file and it wouldn't be automatically imported by NuGet's *.props* file at build time.</span></span>

<span data-ttu-id="c4b56-109">.NET 5,0 ' den başlayarak, bu tür bir dosya proje klasöründe veya üst öğelerinden herhangi biri *varsa otomatik olarak içeri aktarılır.*</span><span class="sxs-lookup"><span data-stu-id="c4b56-109">Starting in .NET 5.0, such a file *is* automatically imported if it exists in the project folder or any of its ancestors.</span></span> <span data-ttu-id="c4b56-110">Proje klasörünüzde bu adı taşıyan bir dosyanız varsa, bu otomatik içeri aktarma yapı davranışını değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="c4b56-110">If you have a file with this name in your project folder, this automatic import could change behavior of the build.</span></span> <span data-ttu-id="c4b56-111">Örneğin, dosya içeri aktarılır, ancak daha önce değil veya içe aktarıldıysanız içeri aktarma sırası değişebilir.</span><span class="sxs-lookup"><span data-stu-id="c4b56-111">For example, the file will be imported but it wasn't before, or the order of when it's imported could change if you specifically import it.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="c4b56-112">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="c4b56-112">Reason for change</span></span>

<span data-ttu-id="c4b56-113">Bu değişiklik, NuGet için [Merkezi paket sürümü oluşturmayı](https://github.com/NuGet/Home/wiki/Centrally-managing-NuGet-package-versions) desteklemek üzere yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="c4b56-113">This change was made in order to support [central package versioning](https://github.com/NuGet/Home/wiki/Centrally-managing-NuGet-package-versions) for NuGet.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="c4b56-114">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="c4b56-114">Recommended action</span></span>

<span data-ttu-id="c4b56-115">Otomatik olarak içeri aktarılmaması gerekiyorsa, var olan *Dizin. Packages. props* dosyasını yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="c4b56-115">Rename the existing *Directory.Packages.props* file if it should not be imported automatically.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="c4b56-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="c4b56-116">Affected APIs</span></span>

<span data-ttu-id="c4b56-117">YOK</span><span class="sxs-lookup"><span data-stu-id="c4b56-117">N/A</span></span>

<!--

### Affected APIs

Not detectable via API analysis.

### Category

MSBuild

-->
