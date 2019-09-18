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
ms.openlocfilehash: c34f160b643a0431168097d3832357b4ac6e4557
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052568"
---
# <a name="invalidvariant-mda"></a><span data-ttu-id="a7bf1-102">invalidVariant MDA</span><span class="sxs-lookup"><span data-stu-id="a7bf1-102">invalidVariant MDA</span></span>
<span data-ttu-id="a7bf1-103">Yönetilen `invalidVariant` hata ayıklama Yardımcısı (MDA), yerel veya yönetilmeyen koddan `VARIANT` yönetilen koda yapılan bir çağrı sırasında geçersiz bir yapıyla karşılaşıldığında etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="a7bf1-103">The `invalidVariant` managed debugging assistant (MDA) is activated when an invalid `VARIANT` structure is encountered during a call from native or unmanaged code to managed code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="a7bf1-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="a7bf1-104">Symptoms</span></span>  
 <span data-ttu-id="a7bf1-105">Bir nesnenin bir `VARIANT` nesneye sıralamasını içeren yerel ve yönetilen kod arasındaki geçiş sırasında beklenmeyen davranış.</span><span class="sxs-lookup"><span data-stu-id="a7bf1-105">Unexpected behavior during a transition between native and managed code involving the marshaling of a `VARIANT` to an object.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="a7bf1-106">Sebep</span><span class="sxs-lookup"><span data-stu-id="a7bf1-106">Cause</span></span>  
 <span data-ttu-id="a7bf1-107">Yerel kod, yönetilen koda hatalı `VARIANT` biçimlendirilmiş bir yapı geçirmektedir.</span><span class="sxs-lookup"><span data-stu-id="a7bf1-107">Native code is passing a malformed `VARIANT` structure to managed code.</span></span>  <span data-ttu-id="a7bf1-108">Çalışma zamanı bunu `VARIANT` bir nesne için sıralama girişiminde bulunur ve geçerli değilse MDA `VARIANT` öğesini etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="a7bf1-108">The runtime attempts to marshal this `VARIANT` to an object and activates the MDA if the `VARIANT` is not valid.</span></span> <span data-ttu-id="a7bf1-109">`VARIANT`Geçersiz S örnekleri, `VARIANT` `VARTYPE` VT_EMPTY &#124; VT_BYREF veya`VARIANT` withVT_VARIANT`VARTYPE` içeren bir içerir.</span><span class="sxs-lookup"><span data-stu-id="a7bf1-109">Examples of invalid `VARIANT`S include a `VARIANT` with `VARTYPE` VT_EMPTY &#124; VT_BYREF or a `VARIANT` with `VARTYPE` VT_VARIANT.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="a7bf1-110">Çözüm</span><span class="sxs-lookup"><span data-stu-id="a7bf1-110">Resolution</span></span>  
 <span data-ttu-id="a7bf1-111">' İ geçirerek `VARIANT` yerel veya yönetilmeyen kod, `VARIANT` doğru şekilde oluşturulmuş ve başlatılmış olduğundan emin olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a7bf1-111">The native or unmanaged code passing the `VARIANT` must ensure that the `VARIANT` is correctly formed and initialized.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="a7bf1-112">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="a7bf1-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="a7bf1-113">MDA çalışma zamanının davranışı üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="a7bf1-113">The MDA has no effect on the runtime's behavior.</span></span>  
  
## <a name="output"></a><span data-ttu-id="a7bf1-114">Çıkış</span><span class="sxs-lookup"><span data-stu-id="a7bf1-114">Output</span></span>  
 <span data-ttu-id="a7bf1-115">Çalışma zamanının yönetilmeyen bir modül tarafından yönetilen koda geçersiz `VARIANT` şekilde geçtiğini belirten bir MDA iletisi.</span><span class="sxs-lookup"><span data-stu-id="a7bf1-115">An MDA message indicating that the runtime detected an invalid `VARIANT` passed to managed code by an unmanaged module.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="a7bf1-116">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a7bf1-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidVariant />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a7bf1-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7bf1-117">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="a7bf1-118">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="a7bf1-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="a7bf1-119">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="a7bf1-119">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
