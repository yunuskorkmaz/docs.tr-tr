---
title: notMarshalable MDA
description: NotMarshalable yönetilen hata ayıklama Yardımcısı ' nı gözden geçirin. Bu, çağrılar hizmet verilmediğinde veya COM arabirimi işaretçileri için yanlış bağlamda gerçekleşmemişse etkinleştirilebilir.
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
ms.openlocfilehash: 344c275d8645b16de3ecb06517297df06323ced4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96254564"
---
# <a name="notmarshalable-mda"></a><span data-ttu-id="58519-103">notMarshalable MDA</span><span class="sxs-lookup"><span data-stu-id="58519-103">notMarshalable MDA</span></span>

<span data-ttu-id="58519-104">`notMarshalable`Yönetilen hata ayıklama Yardımcısı (MDA), ortak dil çalışma zamanı (CLR) geçerli bir kayıtlı ara sunucu/saplama olmadan BIR com arabirim işaretçisi veya bir `IMarshal` arabirim bağlamı arasında sıralama yapmaya çalışırken yanlış bir arabirim uygulamasıyla karşılaştığında etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="58519-104">The `notMarshalable` managed debugging assistant (MDA) is activated when the common language runtime (CLR) encounters a COM interface pointer without a valid registered proxy/stub or an incorrect `IMarshal` interface implementation while attempting to marshal the interface across contexts.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="58519-105">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="58519-105">Symptoms</span></span>  

 <span data-ttu-id="58519-106">Çağrılara hizmet verilmez veya COM arabirim işaretçileri için yanlış bağlamda çağrılar oluşur.</span><span class="sxs-lookup"><span data-stu-id="58519-106">Calls are not serviced, or calls occur in the wrong context for COM interface pointers.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="58519-107">Nedeni</span><span class="sxs-lookup"><span data-stu-id="58519-107">Cause</span></span>  

 <span data-ttu-id="58519-108">Geçerli kayıtlı ara sunucu/saplama yok ya da `IMarshal` arabirim bağlamlarda hazırlanmaya çalışılırken yanlış.</span><span class="sxs-lookup"><span data-stu-id="58519-108">No valid registered proxy/stub or an incorrect `IMarshal` while attempting to marshal the interface across contexts.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="58519-109">Çözüm</span><span class="sxs-lookup"><span data-stu-id="58519-109">Resolution</span></span>  

 <span data-ttu-id="58519-110">Kayıtlı bir ara sunucu Saplamasının olduğundan ve `IMarshal` uygulamanın geçerli olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="58519-110">Make sure you have a proxy stub registered and that the `IMarshal` implementation is valid.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="58519-111">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="58519-111">Effect on the Runtime</span></span>  

 <span data-ttu-id="58519-112">Bu MDA çalışma zamanı üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="58519-112">This MDA has no effect on the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="58519-113">Çıkış</span><span class="sxs-lookup"><span data-stu-id="58519-113">Output</span></span>  

 <span data-ttu-id="58519-114">Sorunu açıklayan bir ileti.</span><span class="sxs-lookup"><span data-stu-id="58519-114">A message describing the problem.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="58519-115">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="58519-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <notMarshalable/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="58519-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="58519-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="58519-117">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="58519-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="58519-118">Birlikte Çalışma Hazırlama</span><span class="sxs-lookup"><span data-stu-id="58519-118">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
