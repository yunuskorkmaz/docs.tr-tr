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
ms.openlocfilehash: 0ac478644561d2aab13d10811987d8d02c8d7608
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59217633"
---
# <a name="failedqi-mda"></a><span data-ttu-id="63717-102">failedQI MDA</span><span class="sxs-lookup"><span data-stu-id="63717-102">failedQI MDA</span></span>
<span data-ttu-id="63717-103">`failedQI` Yönetilen hata ayıklama Yardımcısı (MDA), çalışma zamanı çağırdığında etkinleştirilirse `QueryInterface` üzerinde bir COM arabirimi işaretçisini bir çalışma zamanı çağrılabilir sarmalayıcı (RCW) adına ve `QueryInterface` çağrısı başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="63717-103">The `failedQI` managed debugging assistant (MDA) is activated when the runtime calls `QueryInterface` on a COM interface pointer on behalf of a runtime callable wrapper (RCW), and the `QueryInterface` call fails.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="63717-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="63717-104">Symptoms</span></span>  
 <span data-ttu-id="63717-105">Bir yayın üzerinde bir RCW başarısız olursa veya COM çağrısı bir RCW gelen beklenmedik biçimde başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="63717-105">A cast on an RCW fails, or a call to COM from an RCW fails unexpectedly.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="63717-106">Sebep</span><span class="sxs-lookup"><span data-stu-id="63717-106">Cause</span></span>  
  
-   <span data-ttu-id="63717-107">Çağrı yanlış bağlamında yapılır.</span><span class="sxs-lookup"><span data-stu-id="63717-107">The call is made from the wrong context.</span></span>  
  
-   <span data-ttu-id="63717-108">Kayıtlı proxy başarısız `QueryInterface` çağrı yanlış bağlamda yapıldığı çağırın.</span><span class="sxs-lookup"><span data-stu-id="63717-108">The registered proxy is failing the `QueryInterface` call because the call was attempted in the wrong context.</span></span>  
  
-   <span data-ttu-id="63717-109">OLE ait bir ara sunucu bir hata HRESULT döndürdü.</span><span class="sxs-lookup"><span data-stu-id="63717-109">An OLE-owned proxy returned a failure HRESULT.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="63717-110">Çözüm</span><span class="sxs-lookup"><span data-stu-id="63717-110">Resolution</span></span>  
 <span data-ttu-id="63717-111">COM kuralları'nda MSDN belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="63717-111">See the MSDN documentation on COM rules.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="63717-112">Çalışma zamanı üzerindeki etkisi</span><span class="sxs-lookup"><span data-stu-id="63717-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="63717-113">Varsa bir `QueryInterface` çağrısı başarısız oldu, bağlam geçti ve `QueryInterface` çağrı denenir yeniden hatalı bir bağlam hatalı olup olmadığını görmek için.</span><span class="sxs-lookup"><span data-stu-id="63717-113">If a `QueryInterface` call fails, the context is switched and the `QueryInterface` call is attempted again to see if an incorrect context was at fault.</span></span>  
  
## <a name="output"></a><span data-ttu-id="63717-114">Çıkış</span><span class="sxs-lookup"><span data-stu-id="63717-114">Output</span></span>  
 <span data-ttu-id="63717-115">Arabirim, arabirimin GUID ve hatanın HRESULT yönetilen adı.</span><span class="sxs-lookup"><span data-stu-id="63717-115">The managed name of the interface, the GUID of the interface, and the HRESULT of the failure.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="63717-116">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="63717-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <failedQI/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="63717-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="63717-117">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="63717-118">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="63717-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="63717-119">Birlikte Çalışma Hazırlama</span><span class="sxs-lookup"><span data-stu-id="63717-119">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
