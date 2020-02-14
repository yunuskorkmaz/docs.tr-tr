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
ms.openlocfilehash: 45db0e70b2446fa6e3175409bcc3844042f0acc0
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217279"
---
# <a name="notmarshalable-mda"></a><span data-ttu-id="fe723-102">notMarshalable MDA</span><span class="sxs-lookup"><span data-stu-id="fe723-102">notMarshalable MDA</span></span>
<span data-ttu-id="fe723-103">`notMarshalable` yönetilen hata ayıklama Yardımcısı (MDA), ortak dil çalışma zamanı (CLR), geçerli bir kayıtlı ara sunucu/saplama olmadan bir COM arabirim işaretçisi veya bağlamı arasında arabirim sıralaması denenirken yanlış bir `IMarshal` arabirim uygulamasıyla karşılaştığında etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="fe723-103">The `notMarshalable` managed debugging assistant (MDA) is activated when the common language runtime (CLR) encounters a COM interface pointer without a valid registered proxy/stub or an incorrect `IMarshal` interface implementation while attempting to marshal the interface across contexts.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="fe723-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="fe723-104">Symptoms</span></span>  
 <span data-ttu-id="fe723-105">Çağrılara hizmet verilmez veya COM arabirim işaretçileri için yanlış bağlamda çağrılar oluşur.</span><span class="sxs-lookup"><span data-stu-id="fe723-105">Calls are not serviced, or calls occur in the wrong context for COM interface pointers.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="fe723-106">Nedeni</span><span class="sxs-lookup"><span data-stu-id="fe723-106">Cause</span></span>  
 <span data-ttu-id="fe723-107">Arabirim bağlamlarda hazırlanmaya çalışılırken geçerli kayıtlı ara sunucu/saplama yok ya da yanlış `IMarshal`.</span><span class="sxs-lookup"><span data-stu-id="fe723-107">No valid registered proxy/stub or an incorrect `IMarshal` while attempting to marshal the interface across contexts.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="fe723-108">Çözüm</span><span class="sxs-lookup"><span data-stu-id="fe723-108">Resolution</span></span>  
 <span data-ttu-id="fe723-109">Kayıtlı bir ara sunucu Saplamasının olduğundan ve `IMarshal` uygulamasının geçerli olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="fe723-109">Make sure you have a proxy stub registered and that the `IMarshal` implementation is valid.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="fe723-110">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="fe723-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="fe723-111">Bu MDA çalışma zamanı üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="fe723-111">This MDA has no effect on the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="fe723-112">Çıktı</span><span class="sxs-lookup"><span data-stu-id="fe723-112">Output</span></span>  
 <span data-ttu-id="fe723-113">Sorunu açıklayan bir ileti.</span><span class="sxs-lookup"><span data-stu-id="fe723-113">A message describing the problem.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="fe723-114">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="fe723-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <notMarshalable/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fe723-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe723-115">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="fe723-116">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="fe723-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="fe723-117">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="fe723-117">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
