---
title: invalidApartmentStateChange MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid apartment state
- managed debugging assistants (MDAs), invalid apartment state
- InvalidApartmentStateChange MDA
- invalid apartment state changes
- threading [.NET Framework], apartment states
- apartment states
- threading [.NET Framework], managed debugging assistants
- COM apartment states
ms.assetid: e56fb9df-5286-4be7-b313-540c4d876cd7
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6a7be97ef3184c6836cd67e47b4e9383214f1b5f
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629401"
---
# <a name="invalidapartmentstatechange-mda"></a><span data-ttu-id="a28d1-102">invalidApartmentStateChange MDA</span><span class="sxs-lookup"><span data-stu-id="a28d1-102">invalidApartmentStateChange MDA</span></span>
<span data-ttu-id="a28d1-103">`invalidApartmentStateChange` Yönetilen hata ayıklama Yardımcısı (MDS) iki sorunlardan biri tarafından etkinleştirilir:</span><span class="sxs-lookup"><span data-stu-id="a28d1-103">The `invalidApartmentStateChange` managed debugging assistant (MDS) is activated by either of two problems:</span></span>  
  
- <span data-ttu-id="a28d1-104">COM tarafından zaten başlatılmış olan bir iş parçacığının COM grup durumunu farklı bir grup durumuna değiştirme girişiminde bulunuldu.</span><span class="sxs-lookup"><span data-stu-id="a28d1-104">An attempt is made to change the COM apartment state of a thread that has already been initialized by COM to a different apartment state.</span></span>  
  
- <span data-ttu-id="a28d1-105">Bir iş parçacığının COM apartman durumu beklenmedik şekilde değişir.</span><span class="sxs-lookup"><span data-stu-id="a28d1-105">The COM apartment state of a thread changes unexpectedly.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="a28d1-106">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="a28d1-106">Symptoms</span></span>  
  
- <span data-ttu-id="a28d1-107">Bir iş parçacığının COM grubu durumu istenen değildir.</span><span class="sxs-lookup"><span data-stu-id="a28d1-107">A thread's COM apartment state is not what was requested.</span></span> <span data-ttu-id="a28d1-108">Bu durum, mevcut bir iş parçacığı modeline sahip COM bileşenleri için proxy 'lerin kullanılmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="a28d1-108">This may cause proxies to be used for COM components that have a threading model different from the current one.</span></span> <span data-ttu-id="a28d1-109">Bu sırayla, com nesnesi çapraz <xref:System.InvalidCastException> grup sıralaması için ayarlanmamış arabirimler aracılığıyla çağrılırken bir oluşturulmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="a28d1-109">This in turn may cause an <xref:System.InvalidCastException> to be thrown when calling the COM object through interfaces that are not set up for cross-apartment marshaling.</span></span>  
  
- <span data-ttu-id="a28d1-110">İş parçacığının COM apartman durumu beklenenden farklı.</span><span class="sxs-lookup"><span data-stu-id="a28d1-110">The COM apartment state of the thread is different than expected.</span></span> <span data-ttu-id="a28d1-111">Bu, bir [çalışma zamanı çağrılabilir sarmalayıcı](../../../docs/standard/native-interop/runtime-callable-wrapper.md) (RCW) üzerinde çağrılar <xref:System.InvalidCastException> yaparken bir HRESULT ile birlikte bir <xref:System.Runtime.InteropServices.COMException> RPC_E_WRONG_THREAD ve bir ile oluşmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="a28d1-111">This can cause a <xref:System.Runtime.InteropServices.COMException> with an HRESULT of RPC_E_WRONG_THREAD as well as a <xref:System.InvalidCastException> when making calls on a [Runtime Callable Wrapper](../../../docs/standard/native-interop/runtime-callable-wrapper.md) (RCW).</span></span> <span data-ttu-id="a28d1-112">Bu Ayrıca, bazı tek iş parçacıklı COM bileşenlerine aynı anda birden çok iş parçacığı tarafından erişilmesine neden olabilir, bu da bozulmaya veya veri kaybına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="a28d1-112">This can also cause some single-threaded COM components to be accessed by multiple threads at the same time, which can lead to corruption or data loss.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="a28d1-113">Sebep</span><span class="sxs-lookup"><span data-stu-id="a28d1-113">Cause</span></span>  
  
- <span data-ttu-id="a28d1-114">İş parçacığı daha önce farklı bir COM grubu durumuna başlatılmıştı.</span><span class="sxs-lookup"><span data-stu-id="a28d1-114">The thread was previously initialized to a different COM apartment state.</span></span> <span data-ttu-id="a28d1-115">Bir iş parçacığının Grup durumunun açık veya örtük olarak ayarlankullanılamayacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a28d1-115">Note that the apartment state of a thread can be set either explicitly or implicitly.</span></span> <span data-ttu-id="a28d1-116">Açık işlemler, <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> özelliğini <xref:System.Threading.Thread.SetApartmentState%2A> ve ve <xref:System.Threading.Thread.TrySetApartmentState%2A> yöntemlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="a28d1-116">The explicit operations include the <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> property and the <xref:System.Threading.Thread.SetApartmentState%2A> and <xref:System.Threading.Thread.TrySetApartmentState%2A> methods.</span></span> <span data-ttu-id="a28d1-117"><xref:System.Threading.Thread.Start%2A> Yöntemi kullanılarak oluşturulan bir iş parçacığı, iş parçacığı başlatılmadan <xref:System.Threading.ApartmentState.MTA> önce <xref:System.Threading.Thread.SetApartmentState%2A> çağrılmadığı için örtük olarak olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="a28d1-117">A thread created using the <xref:System.Threading.Thread.Start%2A> method is implicitly set to <xref:System.Threading.ApartmentState.MTA> unless <xref:System.Threading.Thread.SetApartmentState%2A> is called before the thread is started.</span></span> <span data-ttu-id="a28d1-118">Uygulamanın ana iş parçacığı, <xref:System.Threading.ApartmentState.MTA> <xref:System.STAThreadAttribute> özniteliği Main yönteminde belirtilmediği takdirde olarak olarak da başlatılır.</span><span class="sxs-lookup"><span data-stu-id="a28d1-118">The main thread of the application is also implicitly initialized to <xref:System.Threading.ApartmentState.MTA> unless the <xref:System.STAThreadAttribute> attribute is specified on the main method.</span></span>  
  
- <span data-ttu-id="a28d1-119">Farklı bir eşzamanlılık modeliyle `CoInitializeEx` Yöntemi(veyayöntemi)işparçacığındaçağırılır.`CoUninitialize`</span><span class="sxs-lookup"><span data-stu-id="a28d1-119">The `CoUninitialize` method (or the `CoInitializeEx` method) with a different concurrency model is called on the thread.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="a28d1-120">Çözüm</span><span class="sxs-lookup"><span data-stu-id="a28d1-120">Resolution</span></span>  
 <span data-ttu-id="a28d1-121">Yürütmeye başlamadan önce iş parçacığının Grup durumunu ayarlayın veya <xref:System.STAThreadAttribute> özniteliğini <xref:System.MTAThreadAttribute> ya da özniteliğini uygulamanın Main yöntemine uygulayın.</span><span class="sxs-lookup"><span data-stu-id="a28d1-121">Set the apartment state of the thread before it begins executing, or apply either the <xref:System.STAThreadAttribute> attribute or the <xref:System.MTAThreadAttribute> attribute to the main method of the application.</span></span>  
  
 <span data-ttu-id="a28d1-122">İkinci nedenle, en ideal olarak, `CoUninitialize` yöntemi çağıran kod, iş parçacığı sonlandırılmaya ve bir RCWs olmadığından ve temel alınan com bileşenleri iş parçacığı tarafından hala kullanımda olana kadar çağrıyı geciktirmek için değiştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="a28d1-122">For the second cause, ideally, the code that calls the `CoUninitialize` method should be modified to delay the call until the thread is about to terminate and there are no RCWs and their underlying COM components still in use by the thread.</span></span> <span data-ttu-id="a28d1-123">Ancak, `CoUninitialize` yöntemi çağıran kodu değiştirmek mümkün değilse, bu şekilde başlatılmamış iş parçacıklarında hiçbir RCWs kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="a28d1-123">However, if it is not possible to modify the code that calls the `CoUninitialize` method, then no RCWs should be used from threads that are uninitialized in this way.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="a28d1-124">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="a28d1-124">Effect on the Runtime</span></span>  
 <span data-ttu-id="a28d1-125">Bu MDA, CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="a28d1-125">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="a28d1-126">Çıkış</span><span class="sxs-lookup"><span data-stu-id="a28d1-126">Output</span></span>  
 <span data-ttu-id="a28d1-127">Geçerli iş parçacığının COM grubu durumu ve kodun uygulanmaya çalışılması gereken durum.</span><span class="sxs-lookup"><span data-stu-id="a28d1-127">The COM apartment state of the current thread, and the state that the code was attempting to apply.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="a28d1-128">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a28d1-128">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidApartmentStateChange />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="a28d1-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="a28d1-129">Example</span></span>  
 <span data-ttu-id="a28d1-130">Aşağıdaki kod örneğinde, bu MDA ' i etkinleştirebilecek bir durum gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a28d1-130">The following code example demonstrates a situation that can activate this MDA.</span></span>  
  
```csharp
using System.Threading;  
namespace ApartmentStateMDA  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            Thread.CurrentThread.SetApartmentState(ApartmentState.STA);  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="a28d1-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a28d1-131">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="a28d1-132">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="a28d1-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="a28d1-133">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="a28d1-133">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
