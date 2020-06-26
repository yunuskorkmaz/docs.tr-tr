---
title: failedQI MDA
description: .NET 'teki Failedqmanaged hata ayıklama Yardımcısı 'nı (MDA) gözden geçirin. Bu, çalışma zamanı çağrılabilir sarmalayıcı (RCW) üzerinden bir dönüştürme veya COM çağrısı başarısız olduğunda etkinleştirilebilir.
ms.date: 03/30/2017
helpviewer_keywords:
- failed QueryInterface
- FailedQI MDA
- QueryInterface call failures
- MDAs (managed debugging assistants), failed QueryInterface
- managed debugging assistants (MDAs), failed QueryInterface
ms.assetid: 902dc863-34b3-477c-b433-b8a6bb6133c6
ms.openlocfilehash: 2d7f14c67d47e58bcb88eab4621df63d7c598a7a
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415946"
---
# <a name="failedqi-mda"></a><span data-ttu-id="e45f6-103">failedQI MDA</span><span class="sxs-lookup"><span data-stu-id="e45f6-103">failedQI MDA</span></span>
<span data-ttu-id="e45f6-104">`failedQI`Yönetilen hata ayıklama Yardımcısı (MDA), çalışma zamanı `QueryInterface` çağrılabilir bir sarmalayıcı (RCW) ADıNA bir com arabirimi işaretçisine çağrı yaptığında etkinleştirilir ve `QueryInterface` çağrı başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="e45f6-104">The `failedQI` managed debugging assistant (MDA) is activated when the runtime calls `QueryInterface` on a COM interface pointer on behalf of a runtime callable wrapper (RCW), and the `QueryInterface` call fails.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="e45f6-105">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="e45f6-105">Symptoms</span></span>  
 <span data-ttu-id="e45f6-106">RCW üzerinde bir dönüştürme başarısız olur veya bir RCW 'dan COM çağrısı beklenmedik şekilde başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="e45f6-106">A cast on an RCW fails, or a call to COM from an RCW fails unexpectedly.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="e45f6-107">Nedeni</span><span class="sxs-lookup"><span data-stu-id="e45f6-107">Cause</span></span>  
  
- <span data-ttu-id="e45f6-108">Çağrı yanlış bağlamdan yapılır.</span><span class="sxs-lookup"><span data-stu-id="e45f6-108">The call is made from the wrong context.</span></span>  
  
- <span data-ttu-id="e45f6-109">Çağrı yanlış bağlamda denendiği için, kayıtlı ara sunucu çağrıyı başarısız oluyor `QueryInterface` .</span><span class="sxs-lookup"><span data-stu-id="e45f6-109">The registered proxy is failing the `QueryInterface` call because the call was attempted in the wrong context.</span></span>  
  
- <span data-ttu-id="e45f6-110">OLE 'e ait bir ara sunucu HRESULT hatası döndürdü.</span><span class="sxs-lookup"><span data-stu-id="e45f6-110">An OLE-owned proxy returned a failure HRESULT.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="e45f6-111">Çözüm</span><span class="sxs-lookup"><span data-stu-id="e45f6-111">Resolution</span></span>  
 <span data-ttu-id="e45f6-112">COM kuralları hakkında MSDN belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="e45f6-112">See the MSDN documentation on COM rules.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="e45f6-113">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="e45f6-113">Effect on the Runtime</span></span>  
 <span data-ttu-id="e45f6-114">Bir `QueryInterface` çağrı başarısız olursa bağlam çağrılır ve `QueryInterface` yanlış bir bağlamın hata olup olmadığını görmek için çağrı yeniden denenir.</span><span class="sxs-lookup"><span data-stu-id="e45f6-114">If a `QueryInterface` call fails, the context is switched and the `QueryInterface` call is attempted again to see if an incorrect context was at fault.</span></span>  
  
## <a name="output"></a><span data-ttu-id="e45f6-115">Çıktı</span><span class="sxs-lookup"><span data-stu-id="e45f6-115">Output</span></span>  
 <span data-ttu-id="e45f6-116">Arabirimin yönetilen adı, arabirimin GUID 'si ve hatanın HRESULT değeri.</span><span class="sxs-lookup"><span data-stu-id="e45f6-116">The managed name of the interface, the GUID of the interface, and the HRESULT of the failure.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="e45f6-117">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e45f6-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <failedQI/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e45f6-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e45f6-118">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="e45f6-119">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="e45f6-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="e45f6-120">Birlikte Çalışma Hazırlama</span><span class="sxs-lookup"><span data-stu-id="e45f6-120">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
