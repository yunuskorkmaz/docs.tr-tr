---
ms.openlocfilehash: 77e04333ed2b9a5ca8b900c1355fb5b12957772d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774442"
---
### <a name="machinekeyencode-and-machinekeydecode-methods-are-now-obsolete"></a><span data-ttu-id="69017-101">MachineKey.Encode ve MachineKey.Decode yöntemleri artık kullanılmamaktadır</span><span class="sxs-lookup"><span data-stu-id="69017-101">MachineKey.Encode and MachineKey.Decode methods are now obsolete</span></span>

|   |   |
|---|---|
|<span data-ttu-id="69017-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="69017-102">Details</span></span>|<span data-ttu-id="69017-103">Bu yöntemler artık kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="69017-103">These methods are now obsolete.</span></span> <span data-ttu-id="69017-104">Bu yöntemleri çağıran kodun derlemesi bir derleyici uyarısı meydana getirir.</span><span class="sxs-lookup"><span data-stu-id="69017-104">Compilation of code that calls these methods produces a compiler warning.</span></span>|
|<span data-ttu-id="69017-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="69017-105">Suggestion</span></span>|<span data-ttu-id="69017-106">Önerilen alternatifler, <xref:System.Web.Security.MachineKey.Protect(System.Byte[],System.String[])> ve <xref:System.Web.Security.MachineKey.Unprotect(System.Byte[],System.String[])>.</span><span class="sxs-lookup"><span data-stu-id="69017-106">The recommended alternatives are <xref:System.Web.Security.MachineKey.Protect(System.Byte[],System.String[])> and <xref:System.Web.Security.MachineKey.Unprotect(System.Byte[],System.String[])>.</span></span> <span data-ttu-id="69017-107">Alternatif olarak, derleme uyarıları gizlenebilir ya da daha eski bir derleyici kullanılarak önlenebilir.</span><span class="sxs-lookup"><span data-stu-id="69017-107">Alternatively, the build warnings can be suppressed, or they can be avoided by using an older compiler.</span></span> <span data-ttu-id="69017-108">API'leri hala desteklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="69017-108">The APIs are still supported.</span></span>|
|<span data-ttu-id="69017-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="69017-109">Scope</span></span>|<span data-ttu-id="69017-110">İkincil</span><span class="sxs-lookup"><span data-stu-id="69017-110">Minor</span></span>|
|<span data-ttu-id="69017-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="69017-111">Version</span></span>|<span data-ttu-id="69017-112">4,5</span><span class="sxs-lookup"><span data-stu-id="69017-112">4.5</span></span>|
|<span data-ttu-id="69017-113">Tür</span><span class="sxs-lookup"><span data-stu-id="69017-113">Type</span></span>|<span data-ttu-id="69017-114">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="69017-114">Retargeting</span></span>|
|<span data-ttu-id="69017-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="69017-115">Affected APIs</span></span>|<ul><li><xref:System.Web.Security.MachineKey.Encode(System.Byte[],System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType></li><li><xref:System.Web.Security.MachineKey.Decode(System.String,System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType></li></ul>|
