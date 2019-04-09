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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eb0810a9e0ffce825abecc87eb2698920209d86f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59171814"
---
# <a name="noncomvisiblebaseclass-mda"></a><span data-ttu-id="c8047-102">nonComVisibleBaseClass MDA</span><span class="sxs-lookup"><span data-stu-id="c8047-102">nonComVisibleBaseClass MDA</span></span>
<span data-ttu-id="c8047-103">`nonComVisibleBaseClass` Yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilmiş olduğunda bir `QueryInterface` Çağrının yapıldığı COM çağrılabilir sarmalayıcı (CCW) yerel veya yönetilmeyen kodla COM görünür olmayan bir taban sınıftan türetilen bir COM yönetilen görünür sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c8047-103">The `nonComVisibleBaseClass` managed debugging assistant (MDA) is activated when a `QueryInterface` call is made by native or unmanaged code on the COM callable wrapper (CCW) of a COM-visible managed class that derives from a base class that is not COM visible.</span></span>  <span data-ttu-id="c8047-104">`QueryInterface` Çağrının sebep olur yalnızca çağrı burada istekleri sınıf arabirimi veya varsayılan durumda etkinleştirmek MDA `IDispatch` sınıfı için Yönetilen COM-görünür.</span><span class="sxs-lookup"><span data-stu-id="c8047-104">The `QueryInterface` call causes the MDA to activate only in cases where call requests the class interface or default `IDispatch` of the COM-visible managed class.</span></span>  <span data-ttu-id="c8047-105">MDA değil etkinleştirildiği zaman `QueryInterface` olan açık bir arabirim için <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> özniteliği uygulanan ve açıkça COM görünür bir sınıf tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="c8047-105">The MDA is not activated when the `QueryInterface` is for an explicit interface that has the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute applied and is explicitly implemented by the COM-visible class.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="c8047-106">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="c8047-106">Symptoms</span></span>  
 <span data-ttu-id="c8047-107">A `QueryInterface` yapılan bir COR_E_INVALIDOPERATION HRESULT başarısız olduğu yerel koddan çağrı.</span><span class="sxs-lookup"><span data-stu-id="c8047-107">A `QueryInterface` call made from native code that is failing with a COR_E_INVALIDOPERATION HRESULT.</span></span>  <span data-ttu-id="c8047-108">HRESULT engelleyerek runtime nedeniyle olabilir `QueryInterface` bu mda'nın etkinleştirilmesinden neden çağırır.</span><span class="sxs-lookup"><span data-stu-id="c8047-108">The HRESULT might be due to the runtime disallowing `QueryInterface` calls that would cause the activation of this MDA.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="c8047-109">Sebep</span><span class="sxs-lookup"><span data-stu-id="c8047-109">Cause</span></span>  
 <span data-ttu-id="c8047-110">Çalışma zamanı izin veremez `QueryInterface` çağırır sınıf arabirimi veya varsayılan için `IDispatch` COM-görünür olası sürüm oluşturma sorunları nedeniyle değil bir sınıftan türetilen bir COM görünür bir sınıfın arabirim.</span><span class="sxs-lookup"><span data-stu-id="c8047-110">The runtime cannot allow `QueryInterface` calls for the class interface or default `IDispatch` interface of a COM-visible class that derives from a class that is not COM-visible because of potential versioning problems.</span></span>  <span data-ttu-id="c8047-111">COM görünür olmayan taban sınıfa herhangi bir ortak üye eklendiyse, türetilen sınıfın temel sınıf üyelerini içeren vtable gibi tarafından değiştirilmesi çünkü gibi türetilmiş bir sınıf kullanarak mevcut COM istemcileri olası uğratabilir bir değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c8047-111">For example, if any public members were added to the base class that is not COM-visible, existing COM clients using the derived class could potentially break because the vtable of the derived class, which contains the base class members, would be altered by such a change.</span></span>  <span data-ttu-id="c8047-112">Açık arabirimler com'a vtable içinde arabirimin temel üyelerini içermediği için bu sorun yok.</span><span class="sxs-lookup"><span data-stu-id="c8047-112">Explicit interfaces exposed to COM do not have this problem because they do not include the base members of interfaces in the vtable.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="c8047-113">Çözüm</span><span class="sxs-lookup"><span data-stu-id="c8047-113">Resolution</span></span>  
 <span data-ttu-id="c8047-114">Sınıf arabirimi gösterme.</span><span class="sxs-lookup"><span data-stu-id="c8047-114">Do not expose the class interface.</span></span> <span data-ttu-id="c8047-115">Açık bir arabirim tanımlayın ve uygulayın <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="c8047-115">Define an explicit interface and apply the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute to it.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="c8047-116">Çalışma zamanı üzerindeki etkisi</span><span class="sxs-lookup"><span data-stu-id="c8047-116">Effect on the Runtime</span></span>  
 <span data-ttu-id="c8047-117">Bu mda'nın CLR üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="c8047-117">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="c8047-118">Çıkış</span><span class="sxs-lookup"><span data-stu-id="c8047-118">Output</span></span>  
 <span data-ttu-id="c8047-119">Bir örnek iletisidir aşağıdaki bir `QueryInterface` COM görünür bir sınıf üzerinde çağrı `Derived` COM görünür olmayan bir sınıftan türetilen `Base`.</span><span class="sxs-lookup"><span data-stu-id="c8047-119">The following is an example message for a `QueryInterface` call on a COM-visible class `Derived` that derives from a non-COM-visible class `Base`.</span></span>  
  
```  
A QueryInterface call was made requesting the class interface of COM   
visible managed class 'Derived'. However since this class derives from   
non COM visible class 'Base', the QueryInterface call will fail. This   
is done to prevent the non COM visible base class from being   
constrained by the COM versioning rules.   
```  
  
## <a name="configuration"></a><span data-ttu-id="c8047-120">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c8047-120">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <nonComVisibleBaseClass />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c8047-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c8047-121">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="c8047-122">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="c8047-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="c8047-123">Birlikte Çalışma Hazırlama</span><span class="sxs-lookup"><span data-stu-id="c8047-123">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
