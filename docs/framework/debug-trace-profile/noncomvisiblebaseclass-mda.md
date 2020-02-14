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
ms.openlocfilehash: b46d5c6ffbf12efbae113a95bbfccd5742ec9ec9
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217297"
---
# <a name="noncomvisiblebaseclass-mda"></a><span data-ttu-id="ffbcf-102">nonComVisibleBaseClass MDA</span><span class="sxs-lookup"><span data-stu-id="ffbcf-102">nonComVisibleBaseClass MDA</span></span>
<span data-ttu-id="ffbcf-103">`nonComVisibleBaseClass` yönetilen hata ayıklama Yardımcısı (MDA), com görünebilir olmayan bir taban sınıftan türetilen com görünebilir bir yönetilen sınıfın COM çağrılabilir sarmalayıcı (CCW) üzerinde yerel veya yönetilmeyen kod tarafından bir `QueryInterface` çağrısı yapıldığında etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="ffbcf-103">The `nonComVisibleBaseClass` managed debugging assistant (MDA) is activated when a `QueryInterface` call is made by native or unmanaged code on the COM callable wrapper (CCW) of a COM-visible managed class that derives from a base class that is not COM visible.</span></span>  <span data-ttu-id="ffbcf-104">`QueryInterface` çağrısı, MDA öğesinin yalnızca çağrının sınıf arabirimini veya COM görünebilir yönetilen sınıfın varsayılan `IDispatch` bir çağrı istemesi durumunda etkinleştirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="ffbcf-104">The `QueryInterface` call causes the MDA to activate only in cases where call requests the class interface or default `IDispatch` of the COM-visible managed class.</span></span>  <span data-ttu-id="ffbcf-105">`QueryInterface`, <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> özniteliği uygulanan ve COM görünebilir sınıfı tarafından açıkça uygulanan bir açık arabirim için olduğunda, MDA etkinleştirilmez.</span><span class="sxs-lookup"><span data-stu-id="ffbcf-105">The MDA is not activated when the `QueryInterface` is for an explicit interface that has the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute applied and is explicitly implemented by the COM-visible class.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="ffbcf-106">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="ffbcf-106">Symptoms</span></span>  
 <span data-ttu-id="ffbcf-107">COR_E_INVALIDOPERATION HRESULT ile başarısız olan yerel koddan yapılan `QueryInterface` çağrısı.</span><span class="sxs-lookup"><span data-stu-id="ffbcf-107">A `QueryInterface` call made from native code that is failing with a COR_E_INVALIDOPERATION HRESULT.</span></span>  <span data-ttu-id="ffbcf-108">HRESULT, bu MDA ' ın etkinleştirilmesine neden olacak çağrılardan `QueryInterface`, çalışma zamanının nedeni olabilir.</span><span class="sxs-lookup"><span data-stu-id="ffbcf-108">The HRESULT might be due to the runtime disallowing `QueryInterface` calls that would cause the activation of this MDA.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="ffbcf-109">Nedeni</span><span class="sxs-lookup"><span data-stu-id="ffbcf-109">Cause</span></span>  
 <span data-ttu-id="ffbcf-110">Çalışma zamanı, olası sürüm sorunları nedeniyle COM tarafından görülemeyen bir sınıftan türetilmiş bir COM görünebilir sınıfın sınıf arabirimi veya varsayılan `IDispatch` arabirimi için `QueryInterface` çağrılarına izin vermez.</span><span class="sxs-lookup"><span data-stu-id="ffbcf-110">The runtime cannot allow `QueryInterface` calls for the class interface or default `IDispatch` interface of a COM-visible class that derives from a class that is not COM-visible because of potential versioning problems.</span></span>  <span data-ttu-id="ffbcf-111">Örneğin, hiçbir ortak üye, COM görünmeyen temel sınıfa eklendiyse, türetilmiş sınıfı kullanan mevcut COM istemcileri, temel sınıf üyelerini içeren bir sınıf olan vtable, bu tür bir değişebilir.</span><span class="sxs-lookup"><span data-stu-id="ffbcf-111">For example, if any public members were added to the base class that is not COM-visible, existing COM clients using the derived class could potentially break because the vtable of the derived class, which contains the base class members, would be altered by such a change.</span></span>  <span data-ttu-id="ffbcf-112">COM 'a sunulan açık arabirimler, vtable 'daki arabirimlerin temel üyelerini içermediği için bu soruna sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="ffbcf-112">Explicit interfaces exposed to COM do not have this problem because they do not include the base members of interfaces in the vtable.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="ffbcf-113">Çözüm</span><span class="sxs-lookup"><span data-stu-id="ffbcf-113">Resolution</span></span>  
 <span data-ttu-id="ffbcf-114">Sınıf arabirimini kullanıma sunma.</span><span class="sxs-lookup"><span data-stu-id="ffbcf-114">Do not expose the class interface.</span></span> <span data-ttu-id="ffbcf-115">Açık bir arabirim tanımlayın ve <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> özniteliği buna uygulayın.</span><span class="sxs-lookup"><span data-stu-id="ffbcf-115">Define an explicit interface and apply the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute to it.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="ffbcf-116">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="ffbcf-116">Effect on the Runtime</span></span>  
 <span data-ttu-id="ffbcf-117">Bu MDA, CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="ffbcf-117">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="ffbcf-118">Çıktı</span><span class="sxs-lookup"><span data-stu-id="ffbcf-118">Output</span></span>  
 <span data-ttu-id="ffbcf-119">Aşağıda, COM görünebilir olmayan bir sınıftan `Base``Derived` bir COM görünebilir sınıf `QueryInterface` çağrısı için örnek bir ileti verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ffbcf-119">The following is an example message for a `QueryInterface` call on a COM-visible class `Derived` that derives from a non-COM-visible class `Base`.</span></span>  
  
```output
A QueryInterface call was made requesting the class interface of COM   
visible managed class 'Derived'. However since this class derives from   
non COM visible class 'Base', the QueryInterface call will fail. This   
is done to prevent the non COM visible base class from being   
constrained by the COM versioning rules.   
```  
  
## <a name="configuration"></a><span data-ttu-id="ffbcf-120">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ffbcf-120">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <nonComVisibleBaseClass />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ffbcf-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ffbcf-121">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="ffbcf-122">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="ffbcf-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="ffbcf-123">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="ffbcf-123">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
