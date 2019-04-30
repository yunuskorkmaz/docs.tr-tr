---
title: invalidVariant MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid variant
- VARIANT type errors
- InvalidVariant MDA
- invalid VARIANT types
- managed debugging assistants (MDAs), invalid variant
ms.assetid: d273e070-d1b1-4a53-a9c7-7af837b04a3d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 64f5a4425d70974bae8c4f7bec28041e687fe95f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61754329"
---
# <a name="invalidvariant-mda"></a><span data-ttu-id="c0b20-102">invalidVariant MDA</span><span class="sxs-lookup"><span data-stu-id="c0b20-102">invalidVariant MDA</span></span>
<span data-ttu-id="c0b20-103">`invalidVariant` Yönetilen hata ayıklama Yardımcısı (MDA) geçersiz olduğunda etkinleştirilir `VARIANT` yapısı, yerel veya yönetilmeyen koddan yönetilen koda çağrı sırasında karşılaşıldığında.</span><span class="sxs-lookup"><span data-stu-id="c0b20-103">The `invalidVariant` managed debugging assistant (MDA) is activated when an invalid `VARIANT` structure is encountered during a call from native or unmanaged code to managed code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="c0b20-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="c0b20-104">Symptoms</span></span>  
 <span data-ttu-id="c0b20-105">Beklenmeyen davranışı, hazırlama içeren yerel ve yönetilen kod arasında geçiş sırasında bir `VARIANT` bir nesne.</span><span class="sxs-lookup"><span data-stu-id="c0b20-105">Unexpected behavior during a transition between native and managed code involving the marshaling of a `VARIANT` to an object.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="c0b20-106">Sebep</span><span class="sxs-lookup"><span data-stu-id="c0b20-106">Cause</span></span>  
 <span data-ttu-id="c0b20-107">Yerel kod geçirme hatalı biçimlendirilmiş `VARIANT` yönetilen koda yapısı.</span><span class="sxs-lookup"><span data-stu-id="c0b20-107">Native code is passing a malformed `VARIANT` structure to managed code.</span></span>  <span data-ttu-id="c0b20-108">Çalışma zamanı bu sıralama dener `VARIANT` nesneye ve varsa MDA etkinleştirir `VARIANT` geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="c0b20-108">The runtime attempts to marshal this `VARIANT` to an object and activates the MDA if the `VARIANT` is not valid.</span></span> <span data-ttu-id="c0b20-109">Geçersiz örnekleri `VARIANT`S dahil bir `VARIANT` ile `VARTYPE` VT_EMPTY &#124; VT_BYREF veya `VARIANT` ile `VARTYPE` vt_varıant bekleniyordu.</span><span class="sxs-lookup"><span data-stu-id="c0b20-109">Examples of invalid `VARIANT`S include a `VARIANT` with `VARTYPE` VT_EMPTY &#124; VT_BYREF or a `VARIANT` with `VARTYPE` VT_VARIANT.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="c0b20-110">Çözüm</span><span class="sxs-lookup"><span data-stu-id="c0b20-110">Resolution</span></span>  
 <span data-ttu-id="c0b20-111">Yerel veya yönetilmeyen koda geçirme `VARIANT` emin olmanız gerekir `VARIANT` doğru biçimlendirilmiş ve başlatılır.</span><span class="sxs-lookup"><span data-stu-id="c0b20-111">The native or unmanaged code passing the `VARIANT` must ensure that the `VARIANT` is correctly formed and initialized.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="c0b20-112">Çalışma zamanı üzerindeki etkisi</span><span class="sxs-lookup"><span data-stu-id="c0b20-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="c0b20-113">MDA çalışma zamanı davranışı üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="c0b20-113">The MDA has no effect on the runtime's behavior.</span></span>  
  
## <a name="output"></a><span data-ttu-id="c0b20-114">Çıkış</span><span class="sxs-lookup"><span data-stu-id="c0b20-114">Output</span></span>  
 <span data-ttu-id="c0b20-115">Çalışma zamanı geçersiz algılandığını belirten bir MDA ileti `VARIANT` yönetilen kodu için yönetilmeyen bir modül tarafından geçirilen.</span><span class="sxs-lookup"><span data-stu-id="c0b20-115">An MDA message indicating that the runtime detected an invalid `VARIANT` passed to managed code by an unmanaged module.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="c0b20-116">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c0b20-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidVariant />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c0b20-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c0b20-117">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="c0b20-118">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="c0b20-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="c0b20-119">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="c0b20-119">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
