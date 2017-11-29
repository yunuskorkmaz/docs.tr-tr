---
title: nonComVisibleBaseClass MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- visible classes
- managed debugging assistants (MDAs), COM visible classes
- nonComVisibleBaseClass MDA
- COM visible classes
- QueryInterface call failures
- MDAs (managed debugging assistants), COM visible classes
ms.assetid: 9ec1af27-604b-477e-9ee2-e833eb10d3ce
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b43ad5c039be3ad1c4e57bad12304927a76fb6c2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="noncomvisiblebaseclass-mda"></a><span data-ttu-id="76d80-102">nonComVisibleBaseClass MDA</span><span class="sxs-lookup"><span data-stu-id="76d80-102">nonComVisibleBaseClass MDA</span></span>
<span data-ttu-id="76d80-103">`nonComVisibleBaseClass` Yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilmiş olduğunda bir `QueryInterface` çağrısı yapıldığında COM aranabilir sarmalayıcısı (saat) yerel veya yönetilmeyen kodla COM görünür olmayan bir taban sınıftan türeyen bir COM-yönetilen görünür sınıfının.</span><span class="sxs-lookup"><span data-stu-id="76d80-103">The `nonComVisibleBaseClass` managed debugging assistant (MDA) is activated when a `QueryInterface` call is made by native or unmanaged code on the COM callable wrapper (CCW) of a COM-visible managed class that derives from a base class that is not COM visible.</span></span>  <span data-ttu-id="76d80-104">`QueryInterface` Çağrısı neden yalnızca çağrı burada istekleri sınıf arabirimi veya varsayılan durumlarda etkinleştirmeyi MDA `IDispatch` COM görünür yönetilen sınıf.</span><span class="sxs-lookup"><span data-stu-id="76d80-104">The `QueryInterface` call causes the MDA to activate only in cases where call requests the class interface or default `IDispatch` of the COM-visible managed class.</span></span>  <span data-ttu-id="76d80-105">MDA değil ne zaman etkin `QueryInterface` olan açık bir arabirim için <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> özniteliği uygulanan ve COM görünür sınıfı tarafından açıkça uygulanır.</span><span class="sxs-lookup"><span data-stu-id="76d80-105">The MDA is not activated when the `QueryInterface` is for an explicit interface that has the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute applied and is explicitly implemented by the COM-visible class.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="76d80-106">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="76d80-106">Symptoms</span></span>  
 <span data-ttu-id="76d80-107">A `QueryInterface` COR_E_INVALIDOPERATION HRESULT başarısız olduğu yerel koddan yapılan çağrı.</span><span class="sxs-lookup"><span data-stu-id="76d80-107">A `QueryInterface` call made from native code that is failing with a COR_E_INVALIDOPERATION HRESULT.</span></span>  <span data-ttu-id="76d80-108">Çalışma zamanı vermemek nedeniyle HRESULT olabilir `QueryInterface` çağrıları bu MDA etkinleştirme neden olur.</span><span class="sxs-lookup"><span data-stu-id="76d80-108">The HRESULT might be due to the runtime disallowing `QueryInterface` calls that would cause the activation of this MDA.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="76d80-109">Sebep</span><span class="sxs-lookup"><span data-stu-id="76d80-109">Cause</span></span>  
 <span data-ttu-id="76d80-110">Çalışma zamanı izin veremez `QueryInterface` çağırır ve sınıf arabirimi veya varsayılan için `IDispatch` COM görünür olası sürüm oluşturma sorunları nedeniyle olmayan bir sınıftan türeyen bir COM görünür sınıf arabirimi.</span><span class="sxs-lookup"><span data-stu-id="76d80-110">The runtime cannot allow `QueryInterface` calls for the class interface or default `IDispatch` interface of a COM-visible class that derives from a class that is not COM-visible because of potential versioning problems.</span></span>  <span data-ttu-id="76d80-111">COM görünür değil taban sınıfı için herhangi bir ortak üye eklendiyse, taban sınıfı üyeleri içeren, türetilmiş sınıf vtable gibi tarafından değiştirilmesi çünkü Örneğin, türetilmiş sınıf kullanarak var olan COM istemcileri olası uğratabilir bir değiştirin.</span><span class="sxs-lookup"><span data-stu-id="76d80-111">For example, if any public members were added to the base class that is not COM-visible, existing COM clients using the derived class could potentially break because the vtable of the derived class, which contains the base class members, would be altered by such a change.</span></span>  <span data-ttu-id="76d80-112">Vtable arabirimleri temel üyeleri içermediği için açık arabirimler com'a Bu sorun yok.</span><span class="sxs-lookup"><span data-stu-id="76d80-112">Explicit interfaces exposed to COM do not have this problem because they do not include the base members of interfaces in the vtable.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="76d80-113">Çözüm</span><span class="sxs-lookup"><span data-stu-id="76d80-113">Resolution</span></span>  
 <span data-ttu-id="76d80-114">Sınıf arabirimi gösterme.</span><span class="sxs-lookup"><span data-stu-id="76d80-114">Do not expose the class interface.</span></span> <span data-ttu-id="76d80-115">Açık bir arabirim tanımlayın ve uygulayın <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> özniteliği için.</span><span class="sxs-lookup"><span data-stu-id="76d80-115">Define an explicit interface and apply the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute to it.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="76d80-116">Çalışma zamanı etkisi</span><span class="sxs-lookup"><span data-stu-id="76d80-116">Effect on the Runtime</span></span>  
 <span data-ttu-id="76d80-117">Bu MDA CLR üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="76d80-117">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="76d80-118">Çıkış</span><span class="sxs-lookup"><span data-stu-id="76d80-118">Output</span></span>  
 <span data-ttu-id="76d80-119">Bir örnek iletisidir aşağıdaki bir `QueryInterface` çağrısı COM görünür bir sınıf üzerinde `Derived` COM görünür olmayan bir sınıftan türetilen `Base`.</span><span class="sxs-lookup"><span data-stu-id="76d80-119">The following is an example message for a `QueryInterface` call on a COM-visible class `Derived` that derives from a non-COM-visible class `Base`.</span></span>  
  
```  
A QueryInterface call was made requesting the class interface of COM   
visible managed class 'Derived'. However since this class derives from   
non COM visible class 'Base', the QueryInterface call will fail. This   
is done to prevent the non COM visible base class from being   
constrained by the COM versioning rules.   
```  
  
## <a name="configuration"></a><span data-ttu-id="76d80-120">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="76d80-120">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <nonComVisibleBaseClass />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="76d80-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="76d80-121">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="76d80-122">Yönetilen hata ayıklama Yardımcıları ile hataları tanılama</span><span class="sxs-lookup"><span data-stu-id="76d80-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="76d80-123">Birlikte çalışma hazırlama</span><span class="sxs-lookup"><span data-stu-id="76d80-123">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
