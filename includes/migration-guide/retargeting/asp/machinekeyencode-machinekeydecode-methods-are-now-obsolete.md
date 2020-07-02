---
ms.openlocfilehash: e9d34465970287ed94c0f0373ee4ae94d55aa1ff
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617267"
---
### <a name="machinekeyencode-and-machinekeydecode-methods-are-now-obsolete"></a><span data-ttu-id="daa59-101">MachineKey. Encode ve MachineKey. kodunu çözme yöntemleri artık kullanılmıyor</span><span class="sxs-lookup"><span data-stu-id="daa59-101">MachineKey.Encode and MachineKey.Decode methods are now obsolete</span></span>

#### <a name="details"></a><span data-ttu-id="daa59-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="daa59-102">Details</span></span>

<span data-ttu-id="daa59-103">Bu yöntemler artık kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="daa59-103">These methods are now obsolete.</span></span> <span data-ttu-id="daa59-104">Bu yöntemleri çağıran kodun derlemesi bir derleyici uyarısı meydana getirir.</span><span class="sxs-lookup"><span data-stu-id="daa59-104">Compilation of code that calls these methods produces a compiler warning.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="daa59-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="daa59-105">Suggestion</span></span>

<span data-ttu-id="daa59-106">Önerilen alternatifler <xref:System.Web.Security.MachineKey.Protect(System.Byte[],System.String[])> ve ' dir <xref:System.Web.Security.MachineKey.Unprotect(System.Byte[],System.String[])> .</span><span class="sxs-lookup"><span data-stu-id="daa59-106">The recommended alternatives are <xref:System.Web.Security.MachineKey.Protect(System.Byte[],System.String[])> and <xref:System.Web.Security.MachineKey.Unprotect(System.Byte[],System.String[])>.</span></span> <span data-ttu-id="daa59-107">Alternatif olarak, derleme uyarıları bastırılabilir veya eski bir derleyici kullanılarak kaçınılabilir.</span><span class="sxs-lookup"><span data-stu-id="daa59-107">Alternatively, the build warnings can be suppressed, or they can be avoided by using an older compiler.</span></span> <span data-ttu-id="daa59-108">API 'Ler hala desteklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="daa59-108">The APIs are still supported.</span></span>

| <span data-ttu-id="daa59-109">Name</span><span class="sxs-lookup"><span data-stu-id="daa59-109">Name</span></span>    | <span data-ttu-id="daa59-110">Değer</span><span class="sxs-lookup"><span data-stu-id="daa59-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="daa59-111">Kapsam</span><span class="sxs-lookup"><span data-stu-id="daa59-111">Scope</span></span>   | <span data-ttu-id="daa59-112">İkincil</span><span class="sxs-lookup"><span data-stu-id="daa59-112">Minor</span></span>       |
| <span data-ttu-id="daa59-113">Sürüm</span><span class="sxs-lookup"><span data-stu-id="daa59-113">Version</span></span> | <span data-ttu-id="daa59-114">4,5</span><span class="sxs-lookup"><span data-stu-id="daa59-114">4.5</span></span>         |
| <span data-ttu-id="daa59-115">Tür</span><span class="sxs-lookup"><span data-stu-id="daa59-115">Type</span></span>    | <span data-ttu-id="daa59-116">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="daa59-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="daa59-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="daa59-117">Affected APIs</span></span>

- <xref:System.Web.Security.MachineKey.Encode(System.Byte[],System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType>
- <xref:System.Web.Security.MachineKey.Decode(System.String,System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType>
