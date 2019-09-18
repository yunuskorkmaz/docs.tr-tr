---
title: dirtyCastAndCallOnInterface MDA
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), early bound calls AutoDispatch
- dispatch-only mode
- dirtyCastAndCallOnInterface
- early-bound managed classes
- early bound calls on AutoDispatch
- MDAs (managed debugging assistants), early bound calls AutoDispatch
- EarlyBoundCallOnAutorDispatchClassInteface MDA
ms.assetid: aa388ed3-7e3d-48ea-a0b5-c47ae19cec38
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6ac43f6b92198fec03e722b6cf5e12b86df6f4b8
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052872"
---
# <a name="dirtycastandcalloninterface-mda"></a><span data-ttu-id="e7531-102">dirtyCastAndCallOnInterface MDA</span><span class="sxs-lookup"><span data-stu-id="e7531-102">dirtyCastAndCallOnInterface MDA</span></span>
<span data-ttu-id="e7531-103">Yönetilen `dirtyCastAndCallOnInterface` hata ayıklama Yardımcısı (MDA), bir vtable üzerinden erken bağlanan bir çağrı yalnızca geç bağlanan olarak işaretlenmiş bir sınıf arabiriminde denendiğinde etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e7531-103">The `dirtyCastAndCallOnInterface` managed debugging assistant (MDA) is activated when an early-bound call through a vtable is attempted on a class interface that has been marked late-bound only.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="e7531-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="e7531-104">Symptoms</span></span>  
 <span data-ttu-id="e7531-105">Bir uygulama bir erişim ihlali oluşturur veya COM ile CLR 'ye erken bağlantılı bir çağrı yerleştirirken beklenmedik davranışlara sahiptir.</span><span class="sxs-lookup"><span data-stu-id="e7531-105">An application throws an access violation or has unexpected behavior when placing an early-bound call via COM into the CLR.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="e7531-106">Sebep</span><span class="sxs-lookup"><span data-stu-id="e7531-106">Cause</span></span>  
 <span data-ttu-id="e7531-107">Kod, bir vtable aracılığıyla yalnızca geç bağlanan bir sınıf arabirimi aracılığıyla erken bağlanan bir çağrı deniyor.</span><span class="sxs-lookup"><span data-stu-id="e7531-107">Code is attempting an early-bound call through a vtable via a class interface that is late-bound only.</span></span> <span data-ttu-id="e7531-108">Varsayılan sınıf arabirimlerinin yalnızca geç bağlanmakta olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e7531-108">Note that by default class interfaces are identified as being late-bound only.</span></span> <span data-ttu-id="e7531-109">Ayrıca, <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> bir <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch> değeri (`[ClassInterface(ClassInterfaceType.AutoDispatch)]`) olan özniteliğiyle geç bağlantılı olarak da tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="e7531-109">They can also be identified as late-bound with the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute with an <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch> value (`[ClassInterface(ClassInterfaceType.AutoDispatch)]`).</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="e7531-110">Çözüm</span><span class="sxs-lookup"><span data-stu-id="e7531-110">Resolution</span></span>  
 <span data-ttu-id="e7531-111">Önerilen çözüm, COM tarafından kullanılmak üzere bir açık arabirim tanımlamaktır ve COM istemcilerinin, otomatik olarak oluşturulan sınıf arabirimi yerine bu arabirim aracılığıyla çağırmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="e7531-111">The recommended resolution is to define an explicit interface for use by COM and have the COM clients call through this interface instead of through the automatically generated class interface.</span></span> <span data-ttu-id="e7531-112">Alternatif olarak, COM 'dan yapılan çağrı aracılığıyla `IDispatch`geç bağlı çağrıya dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="e7531-112">Alternatively, the call from COM can be transformed into a late-bound call via `IDispatch`.</span></span>  
  
 <span data-ttu-id="e7531-113">Son olarak, <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> (`[ClassInterface(ClassInterfaceType.AutoDual)]`) sınıfını, erken bağlantılı çağrıların com 'dan yerleştirilmesine izin verecek şekilde belirlemek mümkündür; ancak, içinde <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>açıklanan sürüm oluşturma sınırlamaları <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> nedeniyle kullanılması önemle önerilmez.</span><span class="sxs-lookup"><span data-stu-id="e7531-113">Finally, it is possible to identify the class as <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> (`[ClassInterface(ClassInterfaceType.AutoDual)]`) to allow early bound calls to be placed from COM; however, using <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> is strongly discouraged because of the versioning limitations described in <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="e7531-114">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="e7531-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="e7531-115">Bu MDA, CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="e7531-115">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="e7531-116">Yalnızca, Gecikmeli bağlantılı arabirimlerde erken bağlantılı çağrılar hakkındaki verileri raporlar.</span><span class="sxs-lookup"><span data-stu-id="e7531-116">It only reports data about early-bound calls on late-bound interfaces.</span></span>  
  
## <a name="output"></a><span data-ttu-id="e7531-117">Çıkış</span><span class="sxs-lookup"><span data-stu-id="e7531-117">Output</span></span>  
 <span data-ttu-id="e7531-118">Erken bağlanılmakta olan alanın veya metodun adı.</span><span class="sxs-lookup"><span data-stu-id="e7531-118">The name of the method or name of the field being accessed early-bound.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="e7531-119">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e7531-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dirtyCastAndCallOnInterface />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e7531-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e7531-120">See also</span></span>

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>
- [<span data-ttu-id="e7531-121">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="e7531-121">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
