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
ms.openlocfilehash: 8d686621ae4aa087e1b4f4bea9df7fc3de758d40
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216269"
---
# <a name="invalidvariant-mda"></a><span data-ttu-id="7c584-102">invalidVariant MDA</span><span class="sxs-lookup"><span data-stu-id="7c584-102">invalidVariant MDA</span></span>
<span data-ttu-id="7c584-103">`invalidVariant` yönetilen hata ayıklama Yardımcısı (MDA), yerel veya yönetilmeyen koddan yönetilen koda yapılan bir çağrı sırasında geçersiz bir `VARIANT` yapısına rastlana kadar etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="7c584-103">The `invalidVariant` managed debugging assistant (MDA) is activated when an invalid `VARIANT` structure is encountered during a call from native or unmanaged code to managed code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="7c584-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="7c584-104">Symptoms</span></span>  
 <span data-ttu-id="7c584-105">Bir nesneye `VARIANT` sıralamasını içeren yerel ve yönetilen kod arasındaki geçiş sırasında beklenmeyen davranış.</span><span class="sxs-lookup"><span data-stu-id="7c584-105">Unexpected behavior during a transition between native and managed code involving the marshaling of a `VARIANT` to an object.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="7c584-106">Nedeni</span><span class="sxs-lookup"><span data-stu-id="7c584-106">Cause</span></span>  
 <span data-ttu-id="7c584-107">Yerel kod, yönetilen koda hatalı biçimlendirilmiş `VARIANT` yapısını geçiyor.</span><span class="sxs-lookup"><span data-stu-id="7c584-107">Native code is passing a malformed `VARIANT` structure to managed code.</span></span>  <span data-ttu-id="7c584-108">Çalışma zamanı bu `VARIANT` bir nesneye sıralama girişiminde bulunur ve `VARIANT` geçerli değilse MDA 'ı etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="7c584-108">The runtime attempts to marshal this `VARIANT` to an object and activates the MDA if the `VARIANT` is not valid.</span></span> <span data-ttu-id="7c584-109">Geçersiz `VARIANT`örnekleri, `VARTYPE` VT_EMPTY &#124; VT_BYREF veya `VARIANT` `VARTYPE` bir VT_VARIANT içeren bir `VARIANT` içerir.</span><span class="sxs-lookup"><span data-stu-id="7c584-109">Examples of invalid `VARIANT`S include a `VARIANT` with `VARTYPE` VT_EMPTY &#124; VT_BYREF or a `VARIANT` with `VARTYPE` VT_VARIANT.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="7c584-110">Çözüm</span><span class="sxs-lookup"><span data-stu-id="7c584-110">Resolution</span></span>  
 <span data-ttu-id="7c584-111">`VARIANT` geçirerek yerel veya yönetilmeyen kod, `VARIANT` doğru şekilde oluşturulmuş ve başlatılmış olduğundan emin olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7c584-111">The native or unmanaged code passing the `VARIANT` must ensure that the `VARIANT` is correctly formed and initialized.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="7c584-112">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="7c584-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="7c584-113">MDA çalışma zamanının davranışı üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="7c584-113">The MDA has no effect on the runtime's behavior.</span></span>  
  
## <a name="output"></a><span data-ttu-id="7c584-114">Çıktı</span><span class="sxs-lookup"><span data-stu-id="7c584-114">Output</span></span>  
 <span data-ttu-id="7c584-115">Çalışma zamanının yönetilmeyen bir modül tarafından yönetilen koda geçirilen geçersiz bir `VARIANT` algıladığını belirten bir MDA iletisi.</span><span class="sxs-lookup"><span data-stu-id="7c584-115">An MDA message indicating that the runtime detected an invalid `VARIANT` passed to managed code by an unmanaged module.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="7c584-116">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="7c584-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidVariant />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7c584-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7c584-117">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="7c584-118">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="7c584-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="7c584-119">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="7c584-119">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
