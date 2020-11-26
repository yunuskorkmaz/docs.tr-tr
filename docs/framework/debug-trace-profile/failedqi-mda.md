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
ms.openlocfilehash: bbd8d5644f8620444d80845b9920b925b6891176
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96244333"
---
# <a name="failedqi-mda"></a><span data-ttu-id="e31ab-103">failedQI MDA</span><span class="sxs-lookup"><span data-stu-id="e31ab-103">failedQI MDA</span></span>

<span data-ttu-id="e31ab-104">`failedQI`Yönetilen hata ayıklama Yardımcısı (MDA), çalışma zamanı `QueryInterface` çağrılabilir bir sarmalayıcı (RCW) ADıNA bir com arabirimi işaretçisine çağrı yaptığında etkinleştirilir ve `QueryInterface` çağrı başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="e31ab-104">The `failedQI` managed debugging assistant (MDA) is activated when the runtime calls `QueryInterface` on a COM interface pointer on behalf of a runtime callable wrapper (RCW), and the `QueryInterface` call fails.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="e31ab-105">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="e31ab-105">Symptoms</span></span>  

 <span data-ttu-id="e31ab-106">RCW üzerinde bir dönüştürme başarısız olur veya bir RCW 'dan COM çağrısı beklenmedik şekilde başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="e31ab-106">A cast on an RCW fails, or a call to COM from an RCW fails unexpectedly.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="e31ab-107">Nedeni</span><span class="sxs-lookup"><span data-stu-id="e31ab-107">Cause</span></span>  
  
- <span data-ttu-id="e31ab-108">Çağrı yanlış bağlamdan yapılır.</span><span class="sxs-lookup"><span data-stu-id="e31ab-108">The call is made from the wrong context.</span></span>  
  
- <span data-ttu-id="e31ab-109">Çağrı yanlış bağlamda denendiği için, kayıtlı ara sunucu çağrıyı başarısız oluyor `QueryInterface` .</span><span class="sxs-lookup"><span data-stu-id="e31ab-109">The registered proxy is failing the `QueryInterface` call because the call was attempted in the wrong context.</span></span>  
  
- <span data-ttu-id="e31ab-110">OLE 'e ait bir ara sunucu HRESULT hatası döndürdü.</span><span class="sxs-lookup"><span data-stu-id="e31ab-110">An OLE-owned proxy returned a failure HRESULT.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="e31ab-111">Çözüm</span><span class="sxs-lookup"><span data-stu-id="e31ab-111">Resolution</span></span>  

 <span data-ttu-id="e31ab-112">COM kuralları hakkında MSDN belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="e31ab-112">See the MSDN documentation on COM rules.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="e31ab-113">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="e31ab-113">Effect on the Runtime</span></span>  

 <span data-ttu-id="e31ab-114">Bir `QueryInterface` çağrı başarısız olursa bağlam çağrılır ve `QueryInterface` yanlış bir bağlamın hata olup olmadığını görmek için çağrı yeniden denenir.</span><span class="sxs-lookup"><span data-stu-id="e31ab-114">If a `QueryInterface` call fails, the context is switched and the `QueryInterface` call is attempted again to see if an incorrect context was at fault.</span></span>  
  
## <a name="output"></a><span data-ttu-id="e31ab-115">Çıkış</span><span class="sxs-lookup"><span data-stu-id="e31ab-115">Output</span></span>  

 <span data-ttu-id="e31ab-116">Arabirimin yönetilen adı, arabirimin GUID 'si ve hatanın HRESULT değeri.</span><span class="sxs-lookup"><span data-stu-id="e31ab-116">The managed name of the interface, the GUID of the interface, and the HRESULT of the failure.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="e31ab-117">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e31ab-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <failedQI/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e31ab-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e31ab-118">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="e31ab-119">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="e31ab-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="e31ab-120">Birlikte Çalışma Hazırlama</span><span class="sxs-lookup"><span data-stu-id="e31ab-120">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
