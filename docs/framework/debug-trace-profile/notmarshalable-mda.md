---
title: notMarshalable MDA
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c52f104228db0b9e7f664ee7c1de393aa696c71a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33386736"
---
# <a name="notmarshalable-mda"></a><span data-ttu-id="0bde5-102">notMarshalable MDA</span><span class="sxs-lookup"><span data-stu-id="0bde5-102">notMarshalable MDA</span></span>
<span data-ttu-id="0bde5-103">`notMarshalable` Yönetilen hata ayıklama Yardımcısı (MDA), ortak dil çalışma zamanı (CLR) bir geçerli kayıtlı proxy/stub veya yanlış bir olmadan COM arabirimi işaretçisi karşılaştığında etkinleştirilirse `IMarshal` arabirim çalışılırken uygulaması Arabirim bağlamlarında sıralama.</span><span class="sxs-lookup"><span data-stu-id="0bde5-103">The `notMarshalable` managed debugging assistant (MDA) is activated when the common language runtime (CLR) encounters a COM interface pointer without a valid registered proxy/stub or an incorrect `IMarshal` interface implementation while attempting to marshal the interface across contexts.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="0bde5-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="0bde5-104">Symptoms</span></span>  
 <span data-ttu-id="0bde5-105">Çağrıları değil sunulur veya COM arabirim işaretçileri için yanlış bağlamda çağrıları gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="0bde5-105">Calls are not serviced, or calls occur in the wrong context for COM interface pointers.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="0bde5-106">Sebep</span><span class="sxs-lookup"><span data-stu-id="0bde5-106">Cause</span></span>  
 <span data-ttu-id="0bde5-107">Hiçbir geçerli kayıtlı proxy/stub veya yanlış bir `IMarshal` bağlamlarında arabirimi sıralamakta çalışırken.</span><span class="sxs-lookup"><span data-stu-id="0bde5-107">No valid registered proxy/stub or an incorrect `IMarshal` while attempting to marshal the interface across contexts.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="0bde5-108">Çözüm</span><span class="sxs-lookup"><span data-stu-id="0bde5-108">Resolution</span></span>  
 <span data-ttu-id="0bde5-109">Kayıtlı bir proxy saplama ve bu olduğundan emin olun `IMarshal` uygulama geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="0bde5-109">Make sure you have a proxy stub registered and that the `IMarshal` implementation is valid.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="0bde5-110">Çalışma zamanı etkisi</span><span class="sxs-lookup"><span data-stu-id="0bde5-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="0bde5-111">Bu MDA çalışma zamanı üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="0bde5-111">This MDA has no effect on the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="0bde5-112">Çıkış</span><span class="sxs-lookup"><span data-stu-id="0bde5-112">Output</span></span>  
 <span data-ttu-id="0bde5-113">Sorunu açıklayan bir ileti.</span><span class="sxs-lookup"><span data-stu-id="0bde5-113">A message describing the problem.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="0bde5-114">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="0bde5-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <notMarshalable/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0bde5-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0bde5-115">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="0bde5-116">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="0bde5-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="0bde5-117">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="0bde5-117">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
