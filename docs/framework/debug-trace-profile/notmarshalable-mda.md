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
ms.openlocfilehash: 30db07ddf935b5ce13b1fe4212f7f6a40270ae93
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61753705"
---
# <a name="notmarshalable-mda"></a><span data-ttu-id="004b9-102">notMarshalable MDA</span><span class="sxs-lookup"><span data-stu-id="004b9-102">notMarshalable MDA</span></span>
<span data-ttu-id="004b9-103">`notMarshalable` Yönetilen hata ayıklama Yardımcısı (MDA), ortak dil çalışma zamanı (CLR) bir COM arabirimi işaretçisini geçerli kayıtlı proxy/saplama veya yanlış bir olmadan karşılaştığında etkinleştirilirse `IMarshal` arabirim çalışılırken uygulaması Arabirim bağlamlarında hazırlama.</span><span class="sxs-lookup"><span data-stu-id="004b9-103">The `notMarshalable` managed debugging assistant (MDA) is activated when the common language runtime (CLR) encounters a COM interface pointer without a valid registered proxy/stub or an incorrect `IMarshal` interface implementation while attempting to marshal the interface across contexts.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="004b9-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="004b9-104">Symptoms</span></span>  
 <span data-ttu-id="004b9-105">Çağrıları değil sunulur veya çağrı yanlış bağlamda COM arabirim işaretçileri için oluşur.</span><span class="sxs-lookup"><span data-stu-id="004b9-105">Calls are not serviced, or calls occur in the wrong context for COM interface pointers.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="004b9-106">Sebep</span><span class="sxs-lookup"><span data-stu-id="004b9-106">Cause</span></span>  
 <span data-ttu-id="004b9-107">Hiçbir geçerli kayıtlı proxy/saplama veya yanlış bir `IMarshal` bağlamlarında arabirimi sıralamakta çalışırken.</span><span class="sxs-lookup"><span data-stu-id="004b9-107">No valid registered proxy/stub or an incorrect `IMarshal` while attempting to marshal the interface across contexts.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="004b9-108">Çözüm</span><span class="sxs-lookup"><span data-stu-id="004b9-108">Resolution</span></span>  
 <span data-ttu-id="004b9-109">Kayıtlı bir proxy saplama ve bu olduğundan emin olun `IMarshal` uygulama geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="004b9-109">Make sure you have a proxy stub registered and that the `IMarshal` implementation is valid.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="004b9-110">Çalışma zamanı üzerindeki etkisi</span><span class="sxs-lookup"><span data-stu-id="004b9-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="004b9-111">Bu mda'nın çalışma zamanı üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="004b9-111">This MDA has no effect on the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="004b9-112">Çıkış</span><span class="sxs-lookup"><span data-stu-id="004b9-112">Output</span></span>  
 <span data-ttu-id="004b9-113">Sorunu açıklayan bir ileti.</span><span class="sxs-lookup"><span data-stu-id="004b9-113">A message describing the problem.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="004b9-114">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="004b9-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <notMarshalable/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="004b9-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="004b9-115">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="004b9-116">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="004b9-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="004b9-117">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="004b9-117">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
