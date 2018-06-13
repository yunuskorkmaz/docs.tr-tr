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
ms.openlocfilehash: 864367e71f3ed05af87931b2a87f576df42dcbf5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33390698"
---
# <a name="invalidapartmentstatechange-mda"></a><span data-ttu-id="a6538-102">invalidApartmentStateChange MDA</span><span class="sxs-lookup"><span data-stu-id="a6538-102">invalidApartmentStateChange MDA</span></span>
<span data-ttu-id="a6538-103">`invalidApartmentStateChange` Yönetilen hata ayıklama Yardımcısı (MDS) ya da iki sorunları etkinleştirildi:</span><span class="sxs-lookup"><span data-stu-id="a6538-103">The `invalidApartmentStateChange` managed debugging assistant (MDS) is activated by either of two problems:</span></span>  
  
-   <span data-ttu-id="a6538-104">COM tarafından farklı grup durumu için zaten başlatılmış olan bir iş parçacığı COM grup durumunu değiştirmek için bir deneme yapılır.</span><span class="sxs-lookup"><span data-stu-id="a6538-104">An attempt is made to change the COM apartment state of a thread that has already been initialized by COM to a different apartment state.</span></span>  
  
-   <span data-ttu-id="a6538-105">İş parçacığı COM Grup durumu beklenmedik bir şekilde değiştirir.</span><span class="sxs-lookup"><span data-stu-id="a6538-105">The COM apartment state of a thread changes unexpectedly.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="a6538-106">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="a6538-106">Symptoms</span></span>  
  
-   <span data-ttu-id="a6538-107">Bir iş parçacığının COM Grup durumu ne değil istendi ' dir.</span><span class="sxs-lookup"><span data-stu-id="a6538-107">A thread's COM apartment state is not what was requested.</span></span> <span data-ttu-id="a6538-108">Bu, geçerli olandan farklı bir iş parçacığı modeline sahip COM bileşenleri için kullanılacak proxy neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="a6538-108">This may cause proxies to be used for COM components that have a threading model different from the current one.</span></span> <span data-ttu-id="a6538-109">Bu sırayla neden bir <xref:System.InvalidCastException> COM nesnesi arası grup hazırlama için ayarlanmayan arabirimleri aracılığıyla çağrılırken durum için.</span><span class="sxs-lookup"><span data-stu-id="a6538-109">This in turn may cause an <xref:System.InvalidCastException> to be thrown when calling the COM object through interfaces that are not set up for cross-apartment marshaling.</span></span>  
  
-   <span data-ttu-id="a6538-110">COM Grup iş parçacığı beklenenden farklı bir durumda.</span><span class="sxs-lookup"><span data-stu-id="a6538-110">The COM apartment state of the thread is different than expected.</span></span> <span data-ttu-id="a6538-111">Bu neden bir <xref:System.Runtime.InteropServices.COMException> , bir HRESULT RPC_E_WRONG_THREAD ile yanı sıra bir <xref:System.InvalidCastException> yapma çağırdığında üzerinde bir [çalışma zamanı aranabilir sarmalayıcısı](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW).</span><span class="sxs-lookup"><span data-stu-id="a6538-111">This can cause a <xref:System.Runtime.InteropServices.COMException> with an HRESULT of RPC_E_WRONG_THREAD as well as a <xref:System.InvalidCastException> when making calls on a [Runtime Callable Wrapper](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW).</span></span> <span data-ttu-id="a6538-112">Bu da bazı tek iş parçacıklı COM bileşenleri bozulmaya veya veri kaybına yol açabilir aynı anda birden çok iş parçacığı tarafından erişilecek neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="a6538-112">This can also cause some single-threaded COM components to be accessed by multiple threads at the same time, which can lead to corruption or data loss.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="a6538-113">Sebep</span><span class="sxs-lookup"><span data-stu-id="a6538-113">Cause</span></span>  
  
-   <span data-ttu-id="a6538-114">İş parçacığı için farklı bir COM Grup durumu daha önce başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="a6538-114">The thread was previously initialized to a different COM apartment state.</span></span> <span data-ttu-id="a6538-115">İş parçacığı Grup durumu açıkça veya örtük ayarlanabilir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a6538-115">Note that the apartment state of a thread can be set either explicitly or implicitly.</span></span> <span data-ttu-id="a6538-116">Açık işlemleri içeren <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> özelliği ve <xref:System.Threading.Thread.SetApartmentState%2A> ve <xref:System.Threading.Thread.TrySetApartmentState%2A> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="a6538-116">The explicit operations include the <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> property and the <xref:System.Threading.Thread.SetApartmentState%2A> and <xref:System.Threading.Thread.TrySetApartmentState%2A> methods.</span></span> <span data-ttu-id="a6538-117">Kullanılarak oluşturulan bir iş parçacığı <xref:System.Threading.Thread.Start%2A> yöntemi örtük olarak ayarlandığında <xref:System.Threading.ApartmentState.MTA> sürece <xref:System.Threading.Thread.SetApartmentState%2A> iş parçacığı başlatılmadan önce çağrılır.</span><span class="sxs-lookup"><span data-stu-id="a6538-117">A thread created using the <xref:System.Threading.Thread.Start%2A> method is implicitly set to <xref:System.Threading.ApartmentState.MTA> unless <xref:System.Threading.Thread.SetApartmentState%2A> is called before the thread is started.</span></span> <span data-ttu-id="a6538-118">Uygulamanın ana iş parçacığına da örtük olarak başlatılıp başlatılmadığı <xref:System.Threading.ApartmentState.MTA> sürece <xref:System.STAThreadAttribute> özniteliği ana yöntemi belirtilen.</span><span class="sxs-lookup"><span data-stu-id="a6538-118">The main thread of the application is also implicitly initialized to <xref:System.Threading.ApartmentState.MTA> unless the <xref:System.STAThreadAttribute> attribute is specified on the main method.</span></span>  
  
-   <span data-ttu-id="a6538-119">`CoUninitialize` Yöntemi (veya `CoInitializeEx` yöntemi) ile farklı bir eşzamanlılık modeli iş parçacığı üzerinde olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="a6538-119">The `CoUninitialize` method (or the `CoInitializeEx` method) with a different concurrency model is called on the thread.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="a6538-120">Çözüm</span><span class="sxs-lookup"><span data-stu-id="a6538-120">Resolution</span></span>  
 <span data-ttu-id="a6538-121">Yürütme başlamadan önce iş parçacığının grup durumu ayarlamak veya ya da geçerli <xref:System.STAThreadAttribute> özniteliği veya <xref:System.MTAThreadAttribute> özniteliği uygulamanın ana yöntem.</span><span class="sxs-lookup"><span data-stu-id="a6538-121">Set the apartment state of the thread before it begins executing, or apply either the <xref:System.STAThreadAttribute> attribute or the <xref:System.MTAThreadAttribute> attribute to the main method of the application.</span></span>  
  
 <span data-ttu-id="a6538-122">İkinci nedeni için ideal olarak, kod, çağıran `CoUninitialize` yöntemi, iş parçacığının yaklaşık sonlandırmak için ve hiçbir RCWs vardır ve temel alınan COM bileşenleri yine iş parçacığı tarafından kullanımda kadar çağrı gecikme değiştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="a6538-122">For the second cause, ideally, the code that calls the `CoUninitialize` method should be modified to delay the call until the thread is about to terminate and there are no RCWs and their underlying COM components still in use by the thread.</span></span> <span data-ttu-id="a6538-123">Ancak, çağıran kodu değiştirmek mümkün değilse, `CoUninitialize` bu şekilde başlatılmadı parçacıklarından yöntemi sonra hiçbir RCWs kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a6538-123">However, if it is not possible to modify the code that calls the `CoUninitialize` method, then no RCWs should be used from threads that are uninitialized in this way.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="a6538-124">Çalışma zamanı etkisi</span><span class="sxs-lookup"><span data-stu-id="a6538-124">Effect on the Runtime</span></span>  
 <span data-ttu-id="a6538-125">Bu MDA CLR üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="a6538-125">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="a6538-126">Çıkış</span><span class="sxs-lookup"><span data-stu-id="a6538-126">Output</span></span>  
 <span data-ttu-id="a6538-127">Geçerli iş parçacığının COM Grup durumu ve kod uygulamak için çalışıyordu durumu.</span><span class="sxs-lookup"><span data-stu-id="a6538-127">The COM apartment state of the current thread, and the state that the code was attempting to apply.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="a6538-128">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a6538-128">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidApartmentStateChange />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="a6538-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="a6538-129">Example</span></span>  
 <span data-ttu-id="a6538-130">Aşağıdaki kod örneği, bu MDA etkinleştirebilirsiniz bir durumu gösterir.</span><span class="sxs-lookup"><span data-stu-id="a6538-130">The following code example demonstrates a situation that can activate this MDA.</span></span>  
  
```  
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
  
## <a name="see-also"></a><span data-ttu-id="a6538-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a6538-131">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="a6538-132">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="a6538-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="a6538-133">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="a6538-133">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
