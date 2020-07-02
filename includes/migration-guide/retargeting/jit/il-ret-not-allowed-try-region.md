---
ms.openlocfilehash: 4a65e721e5639f12445a9a44f46baa0d26898a88
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615752"
---
### <a name="il-ret-not-allowed-in-a-try-region"></a><span data-ttu-id="ca9d8-101">Bir TRY bölgesinde Il ret 'ye izin verilmiyor</span><span class="sxs-lookup"><span data-stu-id="ca9d8-101">IL ret not allowed in a try region</span></span>

#### <a name="details"></a><span data-ttu-id="ca9d8-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="ca9d8-102">Details</span></span>

<span data-ttu-id="ca9d8-103">JıT64 Just-In-Time derleyicisinden farklı olarak, RyuJIT (.NET Framework 4,6 ' de kullanılır), bir TRY bölgesinde Il ret yönergesine izin vermez.</span><span class="sxs-lookup"><span data-stu-id="ca9d8-103">Unlike the JIT64 just-in-time compiler, RyuJIT (used in .NET Framework 4.6) does not allow an IL ret instruction in a try region.</span></span> <span data-ttu-id="ca9d8-104">Bir TRY bölgesinden dönerek ECMA-335 belirtimine izin verilmez ve bilinen yönetilen derleyici böyle bir Il oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="ca9d8-104">Returning from a try region is disallowed by the ECMA-335 specification, and no known managed compiler generates such IL.</span></span> <span data-ttu-id="ca9d8-105">Ancak, JıT64 derleyicisi, yansıma yayma kullanılarak oluşturulduysa bu Il 'yi yürütür.</span><span class="sxs-lookup"><span data-stu-id="ca9d8-105">However, the JIT64 compiler will execute such IL if it is generated using reflection emit.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ca9d8-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="ca9d8-106">Suggestion</span></span>

<span data-ttu-id="ca9d8-107">Bir uygulama bir TRY bölgesinde ret Opcode içeren Il oluşturuyorsa, uygulama eski JıT 'i kullanmak için .NET Framework 4,5 ' i hedefleyebilir ve bu kesmeyi önleyin.</span><span class="sxs-lookup"><span data-stu-id="ca9d8-107">If an app is generating IL that includes a ret opcode in a try region, the app may target .NET Framework 4.5 to use the old JIT and avoid this break.</span></span> <span data-ttu-id="ca9d8-108">Alternatif olarak, üretilen IL, TRY bölgesinden sonra döndürülecek şekilde güncelleştirilebilen olabilir.</span><span class="sxs-lookup"><span data-stu-id="ca9d8-108">Alternatively, the generated IL may be updated to return after the try region.</span></span>

| <span data-ttu-id="ca9d8-109">Name</span><span class="sxs-lookup"><span data-stu-id="ca9d8-109">Name</span></span>    | <span data-ttu-id="ca9d8-110">Değer</span><span class="sxs-lookup"><span data-stu-id="ca9d8-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ca9d8-111">Kapsam</span><span class="sxs-lookup"><span data-stu-id="ca9d8-111">Scope</span></span>   | <span data-ttu-id="ca9d8-112">Edge</span><span class="sxs-lookup"><span data-stu-id="ca9d8-112">Edge</span></span>        |
| <span data-ttu-id="ca9d8-113">Sürüm</span><span class="sxs-lookup"><span data-stu-id="ca9d8-113">Version</span></span> | <span data-ttu-id="ca9d8-114">4.6</span><span class="sxs-lookup"><span data-stu-id="ca9d8-114">4.6</span></span>         |
| <span data-ttu-id="ca9d8-115">Tür</span><span class="sxs-lookup"><span data-stu-id="ca9d8-115">Type</span></span>    | <span data-ttu-id="ca9d8-116">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="ca9d8-116">Retargeting</span></span> |
