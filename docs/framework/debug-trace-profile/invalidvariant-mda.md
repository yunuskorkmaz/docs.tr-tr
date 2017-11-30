---
title: invalidVariant MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid variant
- VARIANT type errors
- InvalidVariant MDA
- invalid VARIANT types
- managed debugging assistants (MDAs), invalid variant
ms.assetid: d273e070-d1b1-4a53-a9c7-7af837b04a3d
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ee537dcb03dc76968b829f827c73542c07922a3b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="invalidvariant-mda"></a><span data-ttu-id="8b03a-102">invalidVariant MDA</span><span class="sxs-lookup"><span data-stu-id="8b03a-102">invalidVariant MDA</span></span>
<span data-ttu-id="8b03a-103">`invalidVariant` Yönetilen hata ayıklama Yardımcısı (MDA) geçersiz bir zaman etkinleştirilirse `VARIANT` yerel veya yönetilmeyen koddan yönetilen koda çağrı sırasında yapısı karşılaştı.</span><span class="sxs-lookup"><span data-stu-id="8b03a-103">The `invalidVariant` managed debugging assistant (MDA) is activated when an invalid `VARIANT` structure is encountered during a call from native or unmanaged code to managed code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="8b03a-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="8b03a-104">Symptoms</span></span>  
 <span data-ttu-id="8b03a-105">Beklenmeyen bir davranış, hazırlama içeren yerel ve yönetilen kod arasında geçiş sırasında bir `VARIANT` nesneye.</span><span class="sxs-lookup"><span data-stu-id="8b03a-105">Unexpected behavior during a transition between native and managed code involving the marshaling of a `VARIANT` to an object.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="8b03a-106">Sebep</span><span class="sxs-lookup"><span data-stu-id="8b03a-106">Cause</span></span>  
 <span data-ttu-id="8b03a-107">Yerel kod geçirme hatalı biçimlendirilmiş `VARIANT` yönetilen kod yapısına.</span><span class="sxs-lookup"><span data-stu-id="8b03a-107">Native code is passing a malformed `VARIANT` structure to managed code.</span></span>  <span data-ttu-id="8b03a-108">Çalışma zamanı bu sıralama girişiminde `VARIANT` nesneye ve varsa MDA'ı etkinleştirir `VARIANT` geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="8b03a-108">The runtime attempts to marshal this `VARIANT` to an object and activates the MDA if the `VARIANT` is not valid.</span></span> <span data-ttu-id="8b03a-109">Geçersiz örnekleri `VARIANT`S içeren bir `VARIANT` ile `VARTYPE` VT_EMPTY &#124; VT_BYREF veya `VARIANT` ile `VARTYPE` VT_VARIANT.</span><span class="sxs-lookup"><span data-stu-id="8b03a-109">Examples of invalid `VARIANT`S include a `VARIANT` with `VARTYPE` VT_EMPTY &#124; VT_BYREF or a `VARIANT` with `VARTYPE` VT_VARIANT.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="8b03a-110">Çözüm</span><span class="sxs-lookup"><span data-stu-id="8b03a-110">Resolution</span></span>  
 <span data-ttu-id="8b03a-111">Geçirme yerel veya yönetilmeyen kod `VARIANT` emin olmanız gerekir `VARIANT` doğru biçimlendirilmiş ve başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="8b03a-111">The native or unmanaged code passing the `VARIANT` must ensure that the `VARIANT` is correctly formed and initialized.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="8b03a-112">Çalışma zamanı etkisi</span><span class="sxs-lookup"><span data-stu-id="8b03a-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="8b03a-113">MDA çalışma zamanı davranışı üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="8b03a-113">The MDA has no effect on the runtime's behavior.</span></span>  
  
## <a name="output"></a><span data-ttu-id="8b03a-114">Çıkış</span><span class="sxs-lookup"><span data-stu-id="8b03a-114">Output</span></span>  
 <span data-ttu-id="8b03a-115">Çalışma zamanı geçersiz algılanan belirten bir MDA ileti `VARIANT` yönetilmeyen bir modül tarafından yönetilen koda geçirildi.</span><span class="sxs-lookup"><span data-stu-id="8b03a-115">An MDA message indicating that the runtime detected an invalid `VARIANT` passed to managed code by an unmanaged module.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="8b03a-116">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="8b03a-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidVariant />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8b03a-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8b03a-117">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="8b03a-118">Yönetilen hata ayıklama Yardımcıları ile hataları tanılama</span><span class="sxs-lookup"><span data-stu-id="8b03a-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="8b03a-119">Birlikte çalışma hazırlama</span><span class="sxs-lookup"><span data-stu-id="8b03a-119">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
