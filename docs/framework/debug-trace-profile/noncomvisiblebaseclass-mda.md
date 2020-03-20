---
title: nonComVisibleBaseClass MDA
ms.date: 03/30/2017
helpviewer_keywords:
- visible classes
- managed debugging assistants (MDAs), COM visible classes
- nonComVisibleBaseClass MDA
- COM visible classes
- QueryInterface call failures
- MDAs (managed debugging assistants), COM visible classes
ms.assetid: 9ec1af27-604b-477e-9ee2-e833eb10d3ce
ms.openlocfilehash: 4c16432df201d19b65c91206ec529d07605e979a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181797"
---
# <a name="noncomvisiblebaseclass-mda"></a><span data-ttu-id="107fa-102">nonComVisibleBaseClass MDA</span><span class="sxs-lookup"><span data-stu-id="107fa-102">nonComVisibleBaseClass MDA</span></span>
<span data-ttu-id="107fa-103">Yönetilen `nonComVisibleBaseClass` hata ayıklama yardımcısı (MDA), COM `QueryInterface` görünür olmayan bir taban sınıftan türetilen COM görünür yönetilen sınıfın COM çağrılabilir sarıcı (CCW) üzerinde yerel veya yönetilmeyen kod tarafından bir çağrı yapıldığında etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="107fa-103">The `nonComVisibleBaseClass` managed debugging assistant (MDA) is activated when a `QueryInterface` call is made by native or unmanaged code on the COM callable wrapper (CCW) of a COM-visible managed class that derives from a base class that is not COM visible.</span></span>  <span data-ttu-id="107fa-104">Arama, `QueryInterface` MDA'nın yalnızca çağrının sınıf arabirimini `IDispatch` veya COM tarafından görünür yönetilen sınıfın varsayılanını talep ettiği durumlarda etkinleştirilmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="107fa-104">The `QueryInterface` call causes the MDA to activate only in cases where call requests the class interface or default `IDispatch` of the COM-visible managed class.</span></span>  <span data-ttu-id="107fa-105">MDA, özniteliğe `QueryInterface` sahip açık bir arabirim <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> için olduğunda etkinleştirilmez ve COM-görünür sınıf tarafından açıkça uygulanır.</span><span class="sxs-lookup"><span data-stu-id="107fa-105">The MDA is not activated when the `QueryInterface` is for an explicit interface that has the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute applied and is explicitly implemented by the COM-visible class.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="107fa-106">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="107fa-106">Symptoms</span></span>  
 <span data-ttu-id="107fa-107">COR_E_INVALIDOPERATION `QueryInterface` HRESULT ile başarısız olan yerel koddan yapılan bir arama.</span><span class="sxs-lookup"><span data-stu-id="107fa-107">A `QueryInterface` call made from native code that is failing with a COR_E_INVALIDOPERATION HRESULT.</span></span>  <span data-ttu-id="107fa-108">HRESULT, bu MDA'nın etkinleştirilmesine `QueryInterface` neden olacak çalışma saatinden izin vermeme çağrılarına bağlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="107fa-108">The HRESULT might be due to the runtime disallowing `QueryInterface` calls that would cause the activation of this MDA.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="107fa-109">Nedeni</span><span class="sxs-lookup"><span data-stu-id="107fa-109">Cause</span></span>  
 <span data-ttu-id="107fa-110">Çalışma süresi, `QueryInterface` olası sürüm sorunları nedeniyle `IDispatch` COM görünür olmayan bir sınıftan türeyen BIR COM görünür sınıfın sınıf arabirimi veya varsayılan arabirimi için çağrılara izin veremez.</span><span class="sxs-lookup"><span data-stu-id="107fa-110">The runtime cannot allow `QueryInterface` calls for the class interface or default `IDispatch` interface of a COM-visible class that derives from a class that is not COM-visible because of potential versioning problems.</span></span>  <span data-ttu-id="107fa-111">Örneğin, com-görünür olmayan taban sınıfa herhangi bir ortak üye eklenirse, türemiş sınıfı kullanan varolan COM istemcileri, taban sınıf üyelerini içeren türemiş sınıfın vtable'ı bu tür bir Değiştirmek.</span><span class="sxs-lookup"><span data-stu-id="107fa-111">For example, if any public members were added to the base class that is not COM-visible, existing COM clients using the derived class could potentially break because the vtable of the derived class, which contains the base class members, would be altered by such a change.</span></span>  <span data-ttu-id="107fa-112">COM'a maruz kalan açık arabirimler, arabirimlerin temel üyelerini vtable'a içermedikleri için bu soruna sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="107fa-112">Explicit interfaces exposed to COM do not have this problem because they do not include the base members of interfaces in the vtable.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="107fa-113">Çözüm</span><span class="sxs-lookup"><span data-stu-id="107fa-113">Resolution</span></span>  
 <span data-ttu-id="107fa-114">Sınıf arabirimini ifşa etmeyin.</span><span class="sxs-lookup"><span data-stu-id="107fa-114">Do not expose the class interface.</span></span> <span data-ttu-id="107fa-115">Açık bir arabirim <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> tanımlayın ve özniteliği uygulayın.</span><span class="sxs-lookup"><span data-stu-id="107fa-115">Define an explicit interface and apply the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute to it.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="107fa-116">Çalışma Süresi üzerindeki etkisi</span><span class="sxs-lookup"><span data-stu-id="107fa-116">Effect on the Runtime</span></span>  
 <span data-ttu-id="107fa-117">Bu MDA'nın CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="107fa-117">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="107fa-118">Çıktı</span><span class="sxs-lookup"><span data-stu-id="107fa-118">Output</span></span>  
 <span data-ttu-id="107fa-119">Aşağıda, COM'da görünmeyen bir sınıftan `QueryInterface` `Derived` `Base`türeyen COM görünür sınıfındaki bir çağrı için örnek bir ileti verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="107fa-119">The following is an example message for a `QueryInterface` call on a COM-visible class `Derived` that derives from a non-COM-visible class `Base`.</span></span>  
  
```output
A QueryInterface call was made requesting the class interface of COM
visible managed class 'Derived'. However since this class derives from
non COM visible class 'Base', the QueryInterface call will fail. This
is done to prevent the non COM visible base class from being
constrained by the COM versioning rules.
```  
  
## <a name="configuration"></a><span data-ttu-id="107fa-120">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="107fa-120">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <nonComVisibleBaseClass />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="107fa-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="107fa-121">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="107fa-122">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="107fa-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="107fa-123">Birlikte Çalışma Hazırlama</span><span class="sxs-lookup"><span data-stu-id="107fa-123">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
