---
ms.openlocfilehash: 1687b1b9a1a6861f9569a0e29426de7f32ffc32b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804480"
---
### <a name="il-ret-not-allowed-in-a-try-region"></a><span data-ttu-id="e5569-101">IL ret bir deneme bölgesinde izin verilmez</span><span class="sxs-lookup"><span data-stu-id="e5569-101">IL ret not allowed in a try region</span></span>

|   |   |
|---|---|
|<span data-ttu-id="e5569-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="e5569-102">Details</span></span>|<span data-ttu-id="e5569-103">JIT64 tam zamanında derleyicinin aksine, RyuJIT (.NET Framework 4.6'da kullanılır) deneme bölgesinde IL ret yönergesi kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="e5569-103">Unlike the JIT64 just-in-time compiler, RyuJIT (used in .NET Framework 4.6) does not allow an IL ret instruction in a try region.</span></span> <span data-ttu-id="e5569-104">Bir deneme bölgesinden dönüş, ECMA-335 belirtimi tarafından izin verilmez ve bilinen hiçbir yönetilen derleyici böyle bir IL üretmez.</span><span class="sxs-lookup"><span data-stu-id="e5569-104">Returning from a try region is disallowed by the ECMA-335 specification, and no known managed compiler generates such IL.</span></span> <span data-ttu-id="e5569-105">Ancak, JIT64 derleyicisi yansıma yayan kullanılarak oluşturulursa bu TÜR IL yürütür.</span><span class="sxs-lookup"><span data-stu-id="e5569-105">However, the JIT64 compiler will execute such IL if it is generated using reflection emit.</span></span>|
|<span data-ttu-id="e5569-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="e5569-106">Suggestion</span></span>|<span data-ttu-id="e5569-107">Bir uygulama deneme bölgesinde ret opcode içeren IL oluşturuyorsa, uygulama eski JIT'yi kullanmak ve bu kopuşu önlemek için .NET Framework 4.5'i hedefleyebilir.</span><span class="sxs-lookup"><span data-stu-id="e5569-107">If an app is generating IL that includes a ret opcode in a try region, the app may target .NET Framework 4.5 to use the old JIT and avoid this break.</span></span> <span data-ttu-id="e5569-108">Alternatif olarak, oluşturulan IL deneme bölgesinden sonra dönmek için güncelleştirilmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="e5569-108">Alternatively, the generated IL may be updated to return after the try region.</span></span>|
|<span data-ttu-id="e5569-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="e5569-109">Scope</span></span>|<span data-ttu-id="e5569-110">Edge</span><span class="sxs-lookup"><span data-stu-id="e5569-110">Edge</span></span>|
|<span data-ttu-id="e5569-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="e5569-111">Version</span></span>|<span data-ttu-id="e5569-112">4.6</span><span class="sxs-lookup"><span data-stu-id="e5569-112">4.6</span></span>|
|<span data-ttu-id="e5569-113">Tür</span><span class="sxs-lookup"><span data-stu-id="e5569-113">Type</span></span>|<span data-ttu-id="e5569-114">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="e5569-114">Retargeting</span></span>|
