---
title: nonComVisibleBaseClass MDA
description: COR_E_INVALIDOPERATION ile başarısız olan yerel koddan QueryInterface çağrılarında çağrılan nonComVisibleBaseClass yönetilen hata ayıklama Yardımcısı ' na (MDA) bakın.
ms.date: 03/30/2017
helpviewer_keywords:
- visible classes
- managed debugging assistants (MDAs), COM visible classes
- nonComVisibleBaseClass MDA
- COM visible classes
- QueryInterface call failures
- MDAs (managed debugging assistants), COM visible classes
ms.assetid: 9ec1af27-604b-477e-9ee2-e833eb10d3ce
ms.openlocfilehash: 9f32b2c57f50fcd900b1fd78f4f8df1ec656a6db
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803930"
---
# <a name="noncomvisiblebaseclass-mda"></a><span data-ttu-id="772b8-103">nonComVisibleBaseClass MDA</span><span class="sxs-lookup"><span data-stu-id="772b8-103">nonComVisibleBaseClass MDA</span></span>
<span data-ttu-id="772b8-104">`nonComVisibleBaseClass`Yönetilen hata ayıklama Yardımcısı (MDA), com `QueryInterface` görünebilir olmayan bir taban sınıftan türetilen com görünebilir bir YÖNETILEN sınıfın com çağrılabilir SARMALAYıCı (CCW) üzerinde yerel veya yönetilmeyen kod tarafından bir çağrı yapıldığında etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="772b8-104">The `nonComVisibleBaseClass` managed debugging assistant (MDA) is activated when a `QueryInterface` call is made by native or unmanaged code on the COM callable wrapper (CCW) of a COM-visible managed class that derives from a base class that is not COM visible.</span></span>  <span data-ttu-id="772b8-105">Bu `QueryInterface` çağrı, MDA öğesinin yalnızca çağrının sınıf arabirimini veya `IDispatch` com görünebilir yönetilen sınıfın varsayılanını istemesi durumunda etkinleştirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="772b8-105">The `QueryInterface` call causes the MDA to activate only in cases where call requests the class interface or default `IDispatch` of the COM-visible managed class.</span></span>  <span data-ttu-id="772b8-106">, `QueryInterface` <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> Özniteliği uygulanmış ve com görünebilir sınıfı tarafından açıkça uygulanan bir açık arabirim için olduğunda, MDA etkinleştirilmez.</span><span class="sxs-lookup"><span data-stu-id="772b8-106">The MDA is not activated when the `QueryInterface` is for an explicit interface that has the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute applied and is explicitly implemented by the COM-visible class.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="772b8-107">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="772b8-107">Symptoms</span></span>  
 <span data-ttu-id="772b8-108">`QueryInterface`BIR HRESULT COR_E_INVALIDOPERATION başarısız olan yerel koddan yapılan bir çağrı.</span><span class="sxs-lookup"><span data-stu-id="772b8-108">A `QueryInterface` call made from native code that is failing with a COR_E_INVALIDOPERATION HRESULT.</span></span>  <span data-ttu-id="772b8-109">HRESULT, `QueryInterface` Bu mda ' ın etkinleştirilmesine neden olabilecek çalışma zamanı izin vermez çağrılardan kaynaklanıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="772b8-109">The HRESULT might be due to the runtime disallowing `QueryInterface` calls that would cause the activation of this MDA.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="772b8-110">Nedeni</span><span class="sxs-lookup"><span data-stu-id="772b8-110">Cause</span></span>  
 <span data-ttu-id="772b8-111">Çalışma zamanı, `QueryInterface` `IDispatch` olası sürüm oluşturma sorunları nedeniyle com görünebilir olmayan bir SıNıFTAN türetilen com görünebilir bir sınıfın sınıf arabirimi veya varsayılan arabirimine yönelik çağrılara izin vermez.</span><span class="sxs-lookup"><span data-stu-id="772b8-111">The runtime cannot allow `QueryInterface` calls for the class interface or default `IDispatch` interface of a COM-visible class that derives from a class that is not COM-visible because of potential versioning problems.</span></span>  <span data-ttu-id="772b8-112">Örneğin, hiçbir ortak üye, COM görünmeyen temel sınıfa eklendiyse, türetilmiş sınıfı kullanan mevcut COM istemcileri, temel sınıf üyelerini içeren bir bu tür değişikliğe göre değiştirilebilecek olan türetilmiş sınıfın vtable 'ı kesintiye neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="772b8-112">For example, if any public members were added to the base class that is not COM-visible, existing COM clients using the derived class could potentially break because the vtable of the derived class, which contains the base class members, would be altered by such a change.</span></span>  <span data-ttu-id="772b8-113">COM 'a sunulan açık arabirimler, vtable 'daki arabirimlerin temel üyelerini içermediği için bu soruna sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="772b8-113">Explicit interfaces exposed to COM do not have this problem because they do not include the base members of interfaces in the vtable.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="772b8-114">Çözüm</span><span class="sxs-lookup"><span data-stu-id="772b8-114">Resolution</span></span>  
 <span data-ttu-id="772b8-115">Sınıf arabirimini kullanıma sunma.</span><span class="sxs-lookup"><span data-stu-id="772b8-115">Do not expose the class interface.</span></span> <span data-ttu-id="772b8-116">Açık bir arabirim tanımlayın ve <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> özniteliği buna uygulayın.</span><span class="sxs-lookup"><span data-stu-id="772b8-116">Define an explicit interface and apply the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute to it.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="772b8-117">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="772b8-117">Effect on the Runtime</span></span>  
 <span data-ttu-id="772b8-118">Bu MDA, CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="772b8-118">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="772b8-119">Çıktı</span><span class="sxs-lookup"><span data-stu-id="772b8-119">Output</span></span>  
 <span data-ttu-id="772b8-120">Aşağıda, `QueryInterface` `Derived` com görünebilir olmayan bir SıNıFTAN türetilen com görünebilir bir sınıftaki çağrı için örnek bir ileti verilmiştir `Base` .</span><span class="sxs-lookup"><span data-stu-id="772b8-120">The following is an example message for a `QueryInterface` call on a COM-visible class `Derived` that derives from a non-COM-visible class `Base`.</span></span>  
  
```output
A QueryInterface call was made requesting the class interface of COM
visible managed class 'Derived'. However since this class derives from
non COM visible class 'Base', the QueryInterface call will fail. This
is done to prevent the non COM visible base class from being
constrained by the COM versioning rules.
```  
  
## <a name="configuration"></a><span data-ttu-id="772b8-121">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="772b8-121">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <nonComVisibleBaseClass />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="772b8-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="772b8-122">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="772b8-123">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="772b8-123">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="772b8-124">Birlikte Çalışma Hazırlama</span><span class="sxs-lookup"><span data-stu-id="772b8-124">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
