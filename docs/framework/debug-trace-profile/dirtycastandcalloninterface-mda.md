---
title: dirtyCastAndCallOnInterface MDA
description: Erken bağlı vtable çağrıları yalnızca geç bağlı sınıf arabirimlerinde yapıldığında çağrılan Dirtycastandcallonınterface yönetilen hata ayıklama Yardımcısı ' nı gözden geçirin.
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
ms.openlocfilehash: 49a2930d91e76856436480512360e8b9f9fd3d7a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273587"
---
# <a name="dirtycastandcalloninterface-mda"></a><span data-ttu-id="46da8-103">dirtyCastAndCallOnInterface MDA</span><span class="sxs-lookup"><span data-stu-id="46da8-103">dirtyCastAndCallOnInterface MDA</span></span>

<span data-ttu-id="46da8-104">`dirtyCastAndCallOnInterface`Yönetilen hata ayıklama Yardımcısı (MDA), bir vtable üzerinden erken bağlanan bir çağrı yalnızca geç bağlanan olarak işaretlenmiş bir sınıf arabiriminde denendiğinde etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="46da8-104">The `dirtyCastAndCallOnInterface` managed debugging assistant (MDA) is activated when an early-bound call through a vtable is attempted on a class interface that has been marked late-bound only.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="46da8-105">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="46da8-105">Symptoms</span></span>  

 <span data-ttu-id="46da8-106">Bir uygulama bir erişim ihlali oluşturur veya COM ile CLR 'ye erken bağlantılı bir çağrı yerleştirirken beklenmedik davranışlara sahiptir.</span><span class="sxs-lookup"><span data-stu-id="46da8-106">An application throws an access violation or has unexpected behavior when placing an early-bound call via COM into the CLR.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="46da8-107">Nedeni</span><span class="sxs-lookup"><span data-stu-id="46da8-107">Cause</span></span>  

 <span data-ttu-id="46da8-108">Kod, bir vtable aracılığıyla yalnızca geç bağlanan bir sınıf arabirimi aracılığıyla erken bağlanan bir çağrı deniyor.</span><span class="sxs-lookup"><span data-stu-id="46da8-108">Code is attempting an early-bound call through a vtable via a class interface that is late-bound only.</span></span> <span data-ttu-id="46da8-109">Varsayılan sınıf arabirimlerinin yalnızca geç bağlanmakta olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="46da8-109">Note that by default class interfaces are identified as being late-bound only.</span></span> <span data-ttu-id="46da8-110">Ayrıca, <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> bir <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch> değeri () olan özniteliğiyle geç bağlantılı olarak da tanımlanabilir `[ClassInterface(ClassInterfaceType.AutoDispatch)]` .</span><span class="sxs-lookup"><span data-stu-id="46da8-110">They can also be identified as late-bound with the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute with an <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch> value (`[ClassInterface(ClassInterfaceType.AutoDispatch)]`).</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="46da8-111">Çözüm</span><span class="sxs-lookup"><span data-stu-id="46da8-111">Resolution</span></span>  

 <span data-ttu-id="46da8-112">Önerilen çözüm, COM tarafından kullanılmak üzere bir açık arabirim tanımlamaktır ve COM istemcilerinin, otomatik olarak oluşturulan sınıf arabirimi yerine bu arabirim aracılığıyla çağırmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="46da8-112">The recommended resolution is to define an explicit interface for use by COM and have the COM clients call through this interface instead of through the automatically generated class interface.</span></span> <span data-ttu-id="46da8-113">Alternatif olarak, COM 'dan yapılan çağrı aracılığıyla geç bağlı çağrıya dönüştürülebilir `IDispatch` .</span><span class="sxs-lookup"><span data-stu-id="46da8-113">Alternatively, the call from COM can be transformed into a late-bound call via `IDispatch`.</span></span>  
  
 <span data-ttu-id="46da8-114">Son olarak, <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> () sınıfını, `[ClassInterface(ClassInterfaceType.AutoDual)]` erken bağlantılı çağrıların com 'dan yerleştirilmesine izin verecek şekilde belirlemek mümkündür; ancak, <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> içinde açıklanan sürüm oluşturma sınırlamaları nedeniyle kullanılması önemle önerilmez <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> .</span><span class="sxs-lookup"><span data-stu-id="46da8-114">Finally, it is possible to identify the class as <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> (`[ClassInterface(ClassInterfaceType.AutoDual)]`) to allow early bound calls to be placed from COM; however, using <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> is strongly discouraged because of the versioning limitations described in <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="46da8-115">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="46da8-115">Effect on the Runtime</span></span>  

 <span data-ttu-id="46da8-116">Bu MDA, CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="46da8-116">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="46da8-117">Yalnızca, Gecikmeli bağlantılı arabirimlerde erken bağlantılı çağrılar hakkındaki verileri raporlar.</span><span class="sxs-lookup"><span data-stu-id="46da8-117">It only reports data about early-bound calls on late-bound interfaces.</span></span>  
  
## <a name="output"></a><span data-ttu-id="46da8-118">Çıkış</span><span class="sxs-lookup"><span data-stu-id="46da8-118">Output</span></span>  

 <span data-ttu-id="46da8-119">Erken bağlanılmakta olan alanın veya metodun adı.</span><span class="sxs-lookup"><span data-stu-id="46da8-119">The name of the method or name of the field being accessed early-bound.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="46da8-120">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="46da8-120">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dirtyCastAndCallOnInterface />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="46da8-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46da8-121">See also</span></span>

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>
- [<span data-ttu-id="46da8-122">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="46da8-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
