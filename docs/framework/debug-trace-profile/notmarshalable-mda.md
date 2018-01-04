---
title: notMarshalable MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed debugging assistants (MDAs), interface pointer not marshalable
- interface pointer not marshalable MDA
- MDAs (managed debugging assistants), interface pointer not marshalable
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- marshalable interface pointers
- MDAs (managed debugging assistants), marshaling
- notMarshalable MDA
ms.assetid: 96e7b2c1-843f-4d64-b519-740c3a18b50a
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 489f0e2ff4dc1eeaa9721ec6cf59faad0bee2ca8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="notmarshalable-mda"></a><span data-ttu-id="0d659-102">notMarshalable MDA</span><span class="sxs-lookup"><span data-stu-id="0d659-102">notMarshalable MDA</span></span>
<span data-ttu-id="0d659-103">`notMarshalable` Yönetilen hata ayıklama Yardımcısı (MDA), ortak dil çalışma zamanı (CLR) bir geçerli kayıtlı proxy/stub veya yanlış bir olmadan COM arabirimi işaretçisi karşılaştığında etkinleştirilirse `IMarshal` arabirim çalışılırken uygulaması Arabirim bağlamlarında sıralama.</span><span class="sxs-lookup"><span data-stu-id="0d659-103">The `notMarshalable` managed debugging assistant (MDA) is activated when the common language runtime (CLR) encounters a COM interface pointer without a valid registered proxy/stub or an incorrect `IMarshal` interface implementation while attempting to marshal the interface across contexts.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="0d659-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="0d659-104">Symptoms</span></span>  
 <span data-ttu-id="0d659-105">Çağrıları değil sunulur veya COM arabirim işaretçileri için yanlış bağlamda çağrıları gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="0d659-105">Calls are not serviced, or calls occur in the wrong context for COM interface pointers.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="0d659-106">Sebep</span><span class="sxs-lookup"><span data-stu-id="0d659-106">Cause</span></span>  
 <span data-ttu-id="0d659-107">Hiçbir geçerli kayıtlı proxy/stub veya yanlış bir `IMarshal` bağlamlarında arabirimi sıralamakta çalışırken.</span><span class="sxs-lookup"><span data-stu-id="0d659-107">No valid registered proxy/stub or an incorrect `IMarshal` while attempting to marshal the interface across contexts.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="0d659-108">Çözüm</span><span class="sxs-lookup"><span data-stu-id="0d659-108">Resolution</span></span>  
 <span data-ttu-id="0d659-109">Kayıtlı bir proxy saplama ve bu olduğundan emin olun `IMarshal` uygulama geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="0d659-109">Make sure you have a proxy stub registered and that the `IMarshal` implementation is valid.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="0d659-110">Çalışma zamanı etkisi</span><span class="sxs-lookup"><span data-stu-id="0d659-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="0d659-111">Bu MDA çalışma zamanı üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="0d659-111">This MDA has no effect on the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="0d659-112">Çıkış</span><span class="sxs-lookup"><span data-stu-id="0d659-112">Output</span></span>  
 <span data-ttu-id="0d659-113">Sorunu açıklayan bir ileti.</span><span class="sxs-lookup"><span data-stu-id="0d659-113">A message describing the problem.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="0d659-114">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="0d659-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <notMarshalable/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0d659-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0d659-115">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="0d659-116">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="0d659-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="0d659-117">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="0d659-117">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
