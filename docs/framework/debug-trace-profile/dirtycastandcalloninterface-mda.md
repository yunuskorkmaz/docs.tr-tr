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
ms.openlocfilehash: b5c54b8c2600dca1c7b24ac663a6ed506ca8ef24
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33390516"
---
# <a name="dirtycastandcalloninterface-mda"></a><span data-ttu-id="76a3a-102">dirtyCastAndCallOnInterface MDA</span><span class="sxs-lookup"><span data-stu-id="76a3a-102">dirtyCastAndCallOnInterface MDA</span></span>
<span data-ttu-id="76a3a-103">`dirtyCastAndCallOnInterface` Yönetilen hata ayıklama Yardımcısı (MDA) bir vtable erken bağlama çağrısıyla geç bağlama yalnızca işaretlenmiş bir sınıf arabiriminde çalışırken etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="76a3a-103">The `dirtyCastAndCallOnInterface` managed debugging assistant (MDA) is activated when an early-bound call through a vtable is attempted on a class interface that has been marked late-bound only.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="76a3a-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="76a3a-104">Symptoms</span></span>  
 <span data-ttu-id="76a3a-105">Bir uygulama bir erişim ihlali oluşturur veya sahip COM erken bağlama çağrısıyla CLR yerleştirme sırasında beklenmeyen bir davranış.</span><span class="sxs-lookup"><span data-stu-id="76a3a-105">An application throws an access violation or has unexpected behavior when placing an early-bound call via COM into the CLR.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="76a3a-106">Sebep</span><span class="sxs-lookup"><span data-stu-id="76a3a-106">Cause</span></span>  
 <span data-ttu-id="76a3a-107">Kod vtable geç bağlama yalnızca bir sınıf arabirimi aracılığıyla erken bağlama çağrısıyla deniyor.</span><span class="sxs-lookup"><span data-stu-id="76a3a-107">Code is attempting an early-bound call through a vtable via a class interface that is late-bound only.</span></span> <span data-ttu-id="76a3a-108">Geç yalnızca bağlı olarak arabirimler varsayılan sınıf tarafından tanımlanan unutmayın.</span><span class="sxs-lookup"><span data-stu-id="76a3a-108">Note that by default class interfaces are identified as being late-bound only.</span></span> <span data-ttu-id="76a3a-109">Olarak geç bağlama ile de tanımlanabilir <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> ile öznitelik bir <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch> değeri (`[ClassInterface(ClassInterfaceType.AutoDispatch)]`).</span><span class="sxs-lookup"><span data-stu-id="76a3a-109">They can also be identified as late-bound with the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute with an <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch> value (`[ClassInterface(ClassInterfaceType.AutoDispatch)]`).</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="76a3a-110">Çözüm</span><span class="sxs-lookup"><span data-stu-id="76a3a-110">Resolution</span></span>  
 <span data-ttu-id="76a3a-111">Önerilen çözüm COM tarafından kullanım için açık bir arabirim tanımlayın ve otomatik olarak oluşturulan sınıf arabirimi aracılığıyla yerine bu arabiriminden COM istemcileri çağrısı sahip olmaktır.</span><span class="sxs-lookup"><span data-stu-id="76a3a-111">The recommended resolution is to define an explicit interface for use by COM and have the COM clients call through this interface instead of through the automatically generated class interface.</span></span> <span data-ttu-id="76a3a-112">Geç bağlama çağrısıyla COM çağrısından alternatif olarak, dönüştürülebilir `IDispatch`.</span><span class="sxs-lookup"><span data-stu-id="76a3a-112">Alternatively, the call from COM can be transformed into a late-bound call via `IDispatch`.</span></span>  
  
 <span data-ttu-id="76a3a-113">Son olarak, bu sınıf olarak tanımlamak mümkündür <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> (`[ClassInterface(ClassInterfaceType.AutoDual)]`) COM; yerleştirilecek erken bağlama çağrıları izin vermek için ancak kullanarak <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> açıklanan sürüm oluşturma sınırlamaları nedeniyle kesinlikle önerilmez <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>.</span><span class="sxs-lookup"><span data-stu-id="76a3a-113">Finally, it is possible to identify the class as <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> (`[ClassInterface(ClassInterfaceType.AutoDual)]`) to allow early bound calls to be placed from COM; however, using <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> is strongly discouraged because of the versioning limitations described in <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="76a3a-114">Çalışma zamanı etkisi</span><span class="sxs-lookup"><span data-stu-id="76a3a-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="76a3a-115">Bu MDA CLR üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="76a3a-115">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="76a3a-116">Erken bağlama çağrıları geç bağlama arabirimlerinde hakkında veri yalnızca raporlar.</span><span class="sxs-lookup"><span data-stu-id="76a3a-116">It only reports data about early-bound calls on late-bound interfaces.</span></span>  
  
## <a name="output"></a><span data-ttu-id="76a3a-117">Çıkış</span><span class="sxs-lookup"><span data-stu-id="76a3a-117">Output</span></span>  
 <span data-ttu-id="76a3a-118">Erken bağlama erişilen alanının adı ve yöntemi adı.</span><span class="sxs-lookup"><span data-stu-id="76a3a-118">The name of the method or name of the field being accessed early-bound.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="76a3a-119">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="76a3a-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dirtyCastAndCallOnInterface />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="76a3a-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="76a3a-120">See Also</span></span>  
 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>  
 [<span data-ttu-id="76a3a-121">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="76a3a-121">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
