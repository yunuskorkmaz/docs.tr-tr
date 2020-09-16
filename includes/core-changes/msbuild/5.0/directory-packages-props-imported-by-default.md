---
ms.openlocfilehash: 4a916a4178535763712ebd58fde1a81e456da0d1
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538831"
---
### <a name="directorypackagesprops-files-is-imported-by-default"></a><span data-ttu-id="78d52-101">Directory. Packages. props dosyaları varsayılan olarak içeri aktarılır</span><span class="sxs-lookup"><span data-stu-id="78d52-101">Directory.Packages.props files is imported by default</span></span>

<span data-ttu-id="78d52-102">NuGet *. props* dosyaları, proje klasöründe veya üst öğelerinden birinde bulunursa, *Directory. Packages. props* adlı bir dosyayı otomatik olarak içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="78d52-102">NuGet's *.props* files automatically import a file named *Directory.Packages.props* if it's found in the project folder or any of its ancestors.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="78d52-103">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="78d52-103">Version introduced</span></span>

<span data-ttu-id="78d52-104">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="78d52-104">5.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="78d52-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="78d52-105">Change description</span></span>

<span data-ttu-id="78d52-106">Önceki .NET sürümlerinde, proje dosyanızda *Directory. Packages. props* adlı bir dosyanız olabilir ve derleme zamanında NuGet *. props* dosyası tarafından otomatik olarak içeri aktarılmaz.</span><span class="sxs-lookup"><span data-stu-id="78d52-106">In previous .NET versions, you could have a file named *Directory.Packages.props* in your project file and it wouldn't be automatically imported by NuGet's *.props* file at build time.</span></span>

<span data-ttu-id="78d52-107">.NET 5,0 ' den başlayarak, bu tür bir dosya proje klasöründe veya üst öğelerinden herhangi biri *varsa otomatik olarak içeri aktarılır.*</span><span class="sxs-lookup"><span data-stu-id="78d52-107">Starting in .NET 5.0, such a file *is* automatically imported if it exists in the project folder or any of its ancestors.</span></span> <span data-ttu-id="78d52-108">Proje klasörünüzde bu adı taşıyan bir dosyanız varsa, bu otomatik içeri aktarma yapı davranışını değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="78d52-108">If you have a file with this name in your project folder, this automatic import could change behavior of the build.</span></span> <span data-ttu-id="78d52-109">Örneğin, dosya içeri aktarılır, ancak daha önce değil veya içe aktarıldıysanız içeri aktarma sırası değişebilir.</span><span class="sxs-lookup"><span data-stu-id="78d52-109">For example, the file will be imported but it wasn't before, or the order of when it's imported could change if you specifically import it.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="78d52-110">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="78d52-110">Reason for change</span></span>

<span data-ttu-id="78d52-111">Bu değişiklik, NuGet için [Merkezi paket sürümü oluşturmayı](https://github.com/NuGet/Home/wiki/Centrally-managing-NuGet-package-versions) desteklemek üzere yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="78d52-111">This change was made in order to support [central package versioning](https://github.com/NuGet/Home/wiki/Centrally-managing-NuGet-package-versions) for NuGet.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="78d52-112">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="78d52-112">Recommended action</span></span>

<span data-ttu-id="78d52-113">Otomatik olarak içeri aktarılmaması gerekiyorsa, var olan *Dizin. Packages. props* dosyasını yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="78d52-113">Rename the existing *Directory.Packages.props* file if it should not be imported automatically.</span></span>

#### <a name="category"></a><span data-ttu-id="78d52-114">Kategori</span><span class="sxs-lookup"><span data-stu-id="78d52-114">Category</span></span>

<span data-ttu-id="78d52-115">MSBuild</span><span class="sxs-lookup"><span data-stu-id="78d52-115">MSBuild</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="78d52-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="78d52-116">Affected APIs</span></span>

<span data-ttu-id="78d52-117">Yok</span><span class="sxs-lookup"><span data-stu-id="78d52-117">N/A</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
