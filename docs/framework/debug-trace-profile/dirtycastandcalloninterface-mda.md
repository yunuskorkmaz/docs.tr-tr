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
ms.openlocfilehash: 5a28820479ca15ad72475ae9a7754bbbf99ce5c5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59108595"
---
# <a name="dirtycastandcalloninterface-mda"></a><span data-ttu-id="e814b-102">dirtyCastAndCallOnInterface MDA</span><span class="sxs-lookup"><span data-stu-id="e814b-102">dirtyCastAndCallOnInterface MDA</span></span>
<span data-ttu-id="e814b-103">`dirtyCastAndCallOnInterface` Yönetilen hata ayıklama Yardımcısı (MDA) bir erken bağlanan çağrı bir vtable aracılığıyla geç bağlama yalnızca işaretlenmiş bir sınıf arabirimi çalışırken etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e814b-103">The `dirtyCastAndCallOnInterface` managed debugging assistant (MDA) is activated when an early-bound call through a vtable is attempted on a class interface that has been marked late-bound only.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="e814b-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="e814b-104">Symptoms</span></span>  
 <span data-ttu-id="e814b-105">Bir uygulama bir erişim ihlali oluşturur ya da sahip bir erken bağlanan çağrı yoluyla COM CLR yerleştirirken beklenmeyen davranış.</span><span class="sxs-lookup"><span data-stu-id="e814b-105">An application throws an access violation or has unexpected behavior when placing an early-bound call via COM into the CLR.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="e814b-106">Sebep</span><span class="sxs-lookup"><span data-stu-id="e814b-106">Cause</span></span>  
 <span data-ttu-id="e814b-107">Kod bir erken bağlanan çağrı bir vtable geç bağlama yalnızca bir sınıf arabirimi üzerinden aracılığıyla çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="e814b-107">Code is attempting an early-bound call through a vtable via a class interface that is late-bound only.</span></span> <span data-ttu-id="e814b-108">Geç yalnızca bağlama olarak arabirimler varsayılan sınıf tarafından tanımlanan unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e814b-108">Note that by default class interfaces are identified as being late-bound only.</span></span> <span data-ttu-id="e814b-109">Bunlar gibi geç bağlama ile tanımlanabilir <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> özniteliğini bir <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch> değeri (`[ClassInterface(ClassInterfaceType.AutoDispatch)]`).</span><span class="sxs-lookup"><span data-stu-id="e814b-109">They can also be identified as late-bound with the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute with an <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch> value (`[ClassInterface(ClassInterfaceType.AutoDispatch)]`).</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="e814b-110">Çözüm</span><span class="sxs-lookup"><span data-stu-id="e814b-110">Resolution</span></span>  
 <span data-ttu-id="e814b-111">Önerilen çözüm, COM tarafından kullanılması için açık bir arabirim tanımlayın ve otomatik olarak oluşturulan sınıf arabirimi üzerinden yerine bu arabirimi aracılığıyla COM istemcileri çağrısı sahip olmaktır.</span><span class="sxs-lookup"><span data-stu-id="e814b-111">The recommended resolution is to define an explicit interface for use by COM and have the COM clients call through this interface instead of through the automatically generated class interface.</span></span> <span data-ttu-id="e814b-112">Geç bağlama çağrısıyla COM çağrısından alternatif olarak, dönüştürülebilir `IDispatch`.</span><span class="sxs-lookup"><span data-stu-id="e814b-112">Alternatively, the call from COM can be transformed into a late-bound call via `IDispatch`.</span></span>  
  
 <span data-ttu-id="e814b-113">Son olarak, sınıf olarak tanımlamak olası <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> (`[ClassInterface(ClassInterfaceType.AutoDual)]`); COM'dan yerleştirilecek erken bağlama çağrıları izin verecek şekilde ancak kullanarak <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> açıklanan sürüm oluşturma sınırlamaları nedeniyle önerilmez <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>.</span><span class="sxs-lookup"><span data-stu-id="e814b-113">Finally, it is possible to identify the class as <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> (`[ClassInterface(ClassInterfaceType.AutoDual)]`) to allow early bound calls to be placed from COM; however, using <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> is strongly discouraged because of the versioning limitations described in <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="e814b-114">Çalışma zamanı üzerindeki etkisi</span><span class="sxs-lookup"><span data-stu-id="e814b-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="e814b-115">Bu mda'nın CLR üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="e814b-115">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="e814b-116">Geç bağlama arabirimleri üzerinde erken bağlanan çağrılar hakkında veri yalnızca raporlar.</span><span class="sxs-lookup"><span data-stu-id="e814b-116">It only reports data about early-bound calls on late-bound interfaces.</span></span>  
  
## <a name="output"></a><span data-ttu-id="e814b-117">Çıkış</span><span class="sxs-lookup"><span data-stu-id="e814b-117">Output</span></span>  
 <span data-ttu-id="e814b-118">Yöntem veya erken bağlanan erişilen alan adı adı.</span><span class="sxs-lookup"><span data-stu-id="e814b-118">The name of the method or name of the field being accessed early-bound.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="e814b-119">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e814b-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dirtyCastAndCallOnInterface />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e814b-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e814b-120">See also</span></span>

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>
- [<span data-ttu-id="e814b-121">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="e814b-121">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
