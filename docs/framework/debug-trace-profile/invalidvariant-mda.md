---
title: invalidVariant MDA
description: Yerel/yönetilmeyen öğesinden yönetilen koddan gelen bir çağrıda geçersiz bir VARYANTA karşılaşılırsa çağrılan ınvalidvariant yönetilen hata ayıklama Yardımcısı ' nı gözden geçirin.
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid variant
- VARIANT type errors
- InvalidVariant MDA
- invalid VARIANT types
- managed debugging assistants (MDAs), invalid variant
ms.assetid: d273e070-d1b1-4a53-a9c7-7af837b04a3d
ms.openlocfilehash: ab1233d9faa86ef1508fa8fe2b5af46cb37bd523
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: tr-TR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051642"
---
# <a name="invalidvariant-mda"></a><span data-ttu-id="d06d7-103">invalidVariant MDA</span><span class="sxs-lookup"><span data-stu-id="d06d7-103">invalidVariant MDA</span></span>
<span data-ttu-id="d06d7-104">`invalidVariant`Yönetilen hata ayıklama Yardımcısı (MDA), `VARIANT` yerel veya yönetilmeyen koddan yönetilen koda yapılan bir çağrı sırasında geçersiz bir yapıyla karşılaşıldığında etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="d06d7-104">The `invalidVariant` managed debugging assistant (MDA) is activated when an invalid `VARIANT` structure is encountered during a call from native or unmanaged code to managed code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="d06d7-105">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="d06d7-105">Symptoms</span></span>  
 <span data-ttu-id="d06d7-106">Bir nesnenin bir nesneye sıralamasını içeren yerel ve yönetilen kod arasındaki geçiş sırasında beklenmeyen davranış `VARIANT` .</span><span class="sxs-lookup"><span data-stu-id="d06d7-106">Unexpected behavior during a transition between native and managed code involving the marshaling of a `VARIANT` to an object.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="d06d7-107">Nedeni</span><span class="sxs-lookup"><span data-stu-id="d06d7-107">Cause</span></span>  
 <span data-ttu-id="d06d7-108">Yerel kod, yönetilen koda hatalı biçimlendirilmiş bir yapı geçirmektedir `VARIANT` .</span><span class="sxs-lookup"><span data-stu-id="d06d7-108">Native code is passing a malformed `VARIANT` structure to managed code.</span></span>  <span data-ttu-id="d06d7-109">Çalışma zamanı bunu `VARIANT` bir nesne için sıralama girişiminde bulunur ve geçerli DEĞILSE MDA öğesini etkinleştirir `VARIANT` .</span><span class="sxs-lookup"><span data-stu-id="d06d7-109">The runtime attempts to marshal this `VARIANT` to an object and activates the MDA if the `VARIANT` is not valid.</span></span> <span data-ttu-id="d06d7-110">`VARIANT` `VARIANT` `VARTYPE` VT_EMPTY &#124; VT_BYREF ya da VT_VARIANT ile geçersiz bir örnek içerir `VARIANT` `VARTYPE` .</span><span class="sxs-lookup"><span data-stu-id="d06d7-110">Examples of invalid `VARIANT`S include a `VARIANT` with `VARTYPE` VT_EMPTY &#124; VT_BYREF or a `VARIANT` with `VARTYPE` VT_VARIANT.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="d06d7-111">Çözüm</span><span class="sxs-lookup"><span data-stu-id="d06d7-111">Resolution</span></span>  
 <span data-ttu-id="d06d7-112">' İ geçirerek yerel veya yönetilmeyen kod `VARIANT` , `VARIANT` doğru şekilde oluşturulmuş ve başlatılmış olduğundan emin olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d06d7-112">The native or unmanaged code passing the `VARIANT` must ensure that the `VARIANT` is correctly formed and initialized.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="d06d7-113">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="d06d7-113">Effect on the Runtime</span></span>  
 <span data-ttu-id="d06d7-114">MDA çalışma zamanının davranışı üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="d06d7-114">The MDA has no effect on the runtime's behavior.</span></span>  
  
## <a name="output"></a><span data-ttu-id="d06d7-115">Çıktı</span><span class="sxs-lookup"><span data-stu-id="d06d7-115">Output</span></span>  
 <span data-ttu-id="d06d7-116">Çalışma zamanının `VARIANT` yönetilmeyen bir modül tarafından yönetilen koda geçersiz şekilde geçtiğini belirten BIR MDA iletisi.</span><span class="sxs-lookup"><span data-stu-id="d06d7-116">An MDA message indicating that the runtime detected an invalid `VARIANT` passed to managed code by an unmanaged module.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="d06d7-117">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d06d7-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidVariant />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d06d7-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d06d7-118">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="d06d7-119">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="d06d7-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="d06d7-120">Birlikte Çalışma Hazırlama</span><span class="sxs-lookup"><span data-stu-id="d06d7-120">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
