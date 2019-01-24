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
ms.openlocfilehash: 9a3338595e8b541fcda93b091eeddf17919a483c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54614399"
---
# <a name="failedqi-mda"></a><span data-ttu-id="e009e-102">failedQI MDA</span><span class="sxs-lookup"><span data-stu-id="e009e-102">failedQI MDA</span></span>
<span data-ttu-id="e009e-103">`failedQI` Yönetilen hata ayıklama Yardımcısı (MDA), çalışma zamanı çağırdığında etkinleştirilirse `QueryInterface` üzerinde bir COM arabirimi işaretçisini bir çalışma zamanı çağrılabilir sarmalayıcı (RCW) adına ve `QueryInterface` çağrısı başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="e009e-103">The `failedQI` managed debugging assistant (MDA) is activated when the runtime calls `QueryInterface` on a COM interface pointer on behalf of a runtime callable wrapper (RCW), and the `QueryInterface` call fails.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="e009e-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="e009e-104">Symptoms</span></span>  
 <span data-ttu-id="e009e-105">Bir yayın üzerinde bir RCW başarısız olursa veya COM çağrısı bir RCW gelen beklenmedik biçimde başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="e009e-105">A cast on an RCW fails, or a call to COM from an RCW fails unexpectedly.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="e009e-106">Sebep</span><span class="sxs-lookup"><span data-stu-id="e009e-106">Cause</span></span>  
  
-   <span data-ttu-id="e009e-107">Çağrı yanlış bağlamında yapılır.</span><span class="sxs-lookup"><span data-stu-id="e009e-107">The call is made from the wrong context.</span></span>  
  
-   <span data-ttu-id="e009e-108">Kayıtlı proxy başarısız `QueryInterface` çağrı yanlış bağlamda yapıldığı çağırın.</span><span class="sxs-lookup"><span data-stu-id="e009e-108">The registered proxy is failing the `QueryInterface` call because the call was attempted in the wrong context.</span></span>  
  
-   <span data-ttu-id="e009e-109">OLE ait bir ara sunucu bir hata HRESULT döndürdü.</span><span class="sxs-lookup"><span data-stu-id="e009e-109">An OLE-owned proxy returned a failure HRESULT.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="e009e-110">Çözüm</span><span class="sxs-lookup"><span data-stu-id="e009e-110">Resolution</span></span>  
 <span data-ttu-id="e009e-111">COM kuralları'nda MSDN belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="e009e-111">See the MSDN documentation on COM rules.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="e009e-112">Çalışma zamanı üzerindeki etkisi</span><span class="sxs-lookup"><span data-stu-id="e009e-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="e009e-113">Varsa bir `QueryInterface` çağrısı başarısız oldu, bağlam geçti ve `QueryInterface` çağrı denenir yeniden hatalı bir bağlam hatalı olup olmadığını görmek için.</span><span class="sxs-lookup"><span data-stu-id="e009e-113">If a `QueryInterface` call fails, the context is switched and the `QueryInterface` call is attempted again to see if an incorrect context was at fault.</span></span>  
  
## <a name="output"></a><span data-ttu-id="e009e-114">Çıkış</span><span class="sxs-lookup"><span data-stu-id="e009e-114">Output</span></span>  
 <span data-ttu-id="e009e-115">Arabirim, arabirimin GUID ve hatanın HRESULT yönetilen adı.</span><span class="sxs-lookup"><span data-stu-id="e009e-115">The managed name of the interface, the GUID of the interface, and the HRESULT of the failure.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="e009e-116">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e009e-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <failedQI/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e009e-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e009e-117">See also</span></span>
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="e009e-118">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="e009e-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="e009e-119">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="e009e-119">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
