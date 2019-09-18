---
title: failedQI MDA
ms.date: 03/30/2017
helpviewer_keywords:
- failed QueryInterface
- FailedQI MDA
- QueryInterface call failures
- MDAs (managed debugging assistants), failed QueryInterface
- managed debugging assistants (MDAs), failed QueryInterface
ms.assetid: 902dc863-34b3-477c-b433-b8a6bb6133c6
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fec1bfb402f3b394ceb36590c3a880f82c5cb101
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052790"
---
# <a name="failedqi-mda"></a><span data-ttu-id="c87ed-102">failedQI MDA</span><span class="sxs-lookup"><span data-stu-id="c87ed-102">failedQI MDA</span></span>
<span data-ttu-id="c87ed-103">Yönetilen hata ayıklama Yardımcısı (MDA), çalışma zamanı çağrılabilir bir sarmalayıcı `QueryInterface` ( `QueryInterface` RCW) adına bir com arabirimi işaretçisine çağrı yaptığında etkinleştirilir ve çağrı başarısız olur. `failedQI`</span><span class="sxs-lookup"><span data-stu-id="c87ed-103">The `failedQI` managed debugging assistant (MDA) is activated when the runtime calls `QueryInterface` on a COM interface pointer on behalf of a runtime callable wrapper (RCW), and the `QueryInterface` call fails.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="c87ed-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="c87ed-104">Symptoms</span></span>  
 <span data-ttu-id="c87ed-105">RCW üzerinde bir dönüştürme başarısız olur veya bir RCW 'dan COM çağrısı beklenmedik şekilde başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="c87ed-105">A cast on an RCW fails, or a call to COM from an RCW fails unexpectedly.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="c87ed-106">Sebep</span><span class="sxs-lookup"><span data-stu-id="c87ed-106">Cause</span></span>  
  
- <span data-ttu-id="c87ed-107">Çağrı yanlış bağlamdan yapılır.</span><span class="sxs-lookup"><span data-stu-id="c87ed-107">The call is made from the wrong context.</span></span>  
  
- <span data-ttu-id="c87ed-108">Çağrı yanlış bağlamda denendiği için `QueryInterface` , kayıtlı ara sunucu çağrıyı başarısız oluyor.</span><span class="sxs-lookup"><span data-stu-id="c87ed-108">The registered proxy is failing the `QueryInterface` call because the call was attempted in the wrong context.</span></span>  
  
- <span data-ttu-id="c87ed-109">OLE 'e ait bir ara sunucu HRESULT hatası döndürdü.</span><span class="sxs-lookup"><span data-stu-id="c87ed-109">An OLE-owned proxy returned a failure HRESULT.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="c87ed-110">Çözüm</span><span class="sxs-lookup"><span data-stu-id="c87ed-110">Resolution</span></span>  
 <span data-ttu-id="c87ed-111">COM kuralları hakkında MSDN belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="c87ed-111">See the MSDN documentation on COM rules.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="c87ed-112">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="c87ed-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="c87ed-113">Bir `QueryInterface` çağrı başarısız olursa bağlam çağrılır `QueryInterface` ve yanlış bir bağlamın hata olup olmadığını görmek için çağrı yeniden denenir.</span><span class="sxs-lookup"><span data-stu-id="c87ed-113">If a `QueryInterface` call fails, the context is switched and the `QueryInterface` call is attempted again to see if an incorrect context was at fault.</span></span>  
  
## <a name="output"></a><span data-ttu-id="c87ed-114">Çıkış</span><span class="sxs-lookup"><span data-stu-id="c87ed-114">Output</span></span>  
 <span data-ttu-id="c87ed-115">Arabirimin yönetilen adı, arabirimin GUID 'si ve hatanın HRESULT değeri.</span><span class="sxs-lookup"><span data-stu-id="c87ed-115">The managed name of the interface, the GUID of the interface, and the HRESULT of the failure.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="c87ed-116">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c87ed-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <failedQI/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c87ed-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c87ed-117">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="c87ed-118">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="c87ed-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="c87ed-119">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="c87ed-119">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
