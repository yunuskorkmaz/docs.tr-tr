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
ms.openlocfilehash: c201ab51c1af8a86fc1c2c4f80738007152b3bd9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59122856"
---
# <a name="invalidapartmentstatechange-mda"></a><span data-ttu-id="de967-102">invalidApartmentStateChange MDA</span><span class="sxs-lookup"><span data-stu-id="de967-102">invalidApartmentStateChange MDA</span></span>
<span data-ttu-id="de967-103">`invalidApartmentStateChange` Yönetilen hata ayıklama Yardımcısı (MDS) ya da iki sorunları tarafından etkinleştirilir:</span><span class="sxs-lookup"><span data-stu-id="de967-103">The `invalidApartmentStateChange` managed debugging assistant (MDS) is activated by either of two problems:</span></span>  
  
-   <span data-ttu-id="de967-104">Farklı grup durumuna COM tarafından başlatılmış bir iş parçacığı COM grubu durumunu değiştirmek için bir deneme yapılır.</span><span class="sxs-lookup"><span data-stu-id="de967-104">An attempt is made to change the COM apartment state of a thread that has already been initialized by COM to a different apartment state.</span></span>  
  
-   <span data-ttu-id="de967-105">İş parçacığı COM Grup durumu beklenmedik bir şekilde değiştirir.</span><span class="sxs-lookup"><span data-stu-id="de967-105">The COM apartment state of a thread changes unexpectedly.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="de967-106">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="de967-106">Symptoms</span></span>  
  
-   <span data-ttu-id="de967-107">Bir iş parçacığının COM Grup durumu ne istenmediğinden ' dir.</span><span class="sxs-lookup"><span data-stu-id="de967-107">A thread's COM apartment state is not what was requested.</span></span> <span data-ttu-id="de967-108">Bu, geçerli olandan farklı bir iş parçacığı modeline sahip bir COM bileşenleri için kullanılacak proxy neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="de967-108">This may cause proxies to be used for COM components that have a threading model different from the current one.</span></span> <span data-ttu-id="de967-109">Bu sırayla neden olabilir bir <xref:System.InvalidCastException> COM nesnesi çapraz-grup sıralama için ayarlanmadınız arabirimler üzerinden çağırırken durum.</span><span class="sxs-lookup"><span data-stu-id="de967-109">This in turn may cause an <xref:System.InvalidCastException> to be thrown when calling the COM object through interfaces that are not set up for cross-apartment marshaling.</span></span>  
  
-   <span data-ttu-id="de967-110">İş parçacığının COM Grup durumu, beklenenden daha farklıdır.</span><span class="sxs-lookup"><span data-stu-id="de967-110">The COM apartment state of the thread is different than expected.</span></span> <span data-ttu-id="de967-111">Bu neden olabilir bir <xref:System.Runtime.InteropServices.COMException> ile bir HRESULT RPC_E_WRONG_THREAD yanı <xref:System.InvalidCastException> yapma çağırdığında üzerinde bir [çalışma zamanı çağrılabilir sarmalayıcı](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW).</span><span class="sxs-lookup"><span data-stu-id="de967-111">This can cause a <xref:System.Runtime.InteropServices.COMException> with an HRESULT of RPC_E_WRONG_THREAD as well as a <xref:System.InvalidCastException> when making calls on a [Runtime Callable Wrapper](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW).</span></span> <span data-ttu-id="de967-112">Bu da bazı tek iş parçacıklı COM bileşenleri Bozulması veya veri kaybına yol açabilir aynı anda birden çok iş parçacığı tarafından erişilecek neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="de967-112">This can also cause some single-threaded COM components to be accessed by multiple threads at the same time, which can lead to corruption or data loss.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="de967-113">Sebep</span><span class="sxs-lookup"><span data-stu-id="de967-113">Cause</span></span>  
  
-   <span data-ttu-id="de967-114">İş parçacığı için farklı bir COM Grup durumu daha önceden başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="de967-114">The thread was previously initialized to a different COM apartment state.</span></span> <span data-ttu-id="de967-115">Bir iş parçacığı grubu durumunu açık veya örtük olarak ayarlanabilir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="de967-115">Note that the apartment state of a thread can be set either explicitly or implicitly.</span></span> <span data-ttu-id="de967-116">Açık işlemleri <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> özelliği ve <xref:System.Threading.Thread.SetApartmentState%2A> ve <xref:System.Threading.Thread.TrySetApartmentState%2A> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="de967-116">The explicit operations include the <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> property and the <xref:System.Threading.Thread.SetApartmentState%2A> and <xref:System.Threading.Thread.TrySetApartmentState%2A> methods.</span></span> <span data-ttu-id="de967-117">Kullanılarak oluşturulan bir iş parçacığı <xref:System.Threading.Thread.Start%2A> yöntemi örtülü olarak ayarlandığında <xref:System.Threading.ApartmentState.MTA> sürece <xref:System.Threading.Thread.SetApartmentState%2A> iş parçacığı başlatılmadan önce çağrılır.</span><span class="sxs-lookup"><span data-stu-id="de967-117">A thread created using the <xref:System.Threading.Thread.Start%2A> method is implicitly set to <xref:System.Threading.ApartmentState.MTA> unless <xref:System.Threading.Thread.SetApartmentState%2A> is called before the thread is started.</span></span> <span data-ttu-id="de967-118">Uygulamanın ana iş parçacığı ayrıca açık olarak başlatılır <xref:System.Threading.ApartmentState.MTA> sürece <xref:System.STAThreadAttribute> özniteliği ana yöntemi belirtildi.</span><span class="sxs-lookup"><span data-stu-id="de967-118">The main thread of the application is also implicitly initialized to <xref:System.Threading.ApartmentState.MTA> unless the <xref:System.STAThreadAttribute> attribute is specified on the main method.</span></span>  
  
-   <span data-ttu-id="de967-119">`CoUninitialize` Yöntemi (veya `CoInitializeEx` yöntemi) ile farklı bir eşzamanlılık modeli iş parçacığı üzerinde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="de967-119">The `CoUninitialize` method (or the `CoInitializeEx` method) with a different concurrency model is called on the thread.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="de967-120">Çözüm</span><span class="sxs-lookup"><span data-stu-id="de967-120">Resolution</span></span>  
 <span data-ttu-id="de967-121">Yürütme başlamadan önce iş parçacığı grubu durumunu ayarlamak veya ya da uygulama <xref:System.STAThreadAttribute> özniteliği veya <xref:System.MTAThreadAttribute> uygulamanın main yöntemi için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="de967-121">Set the apartment state of the thread before it begins executing, or apply either the <xref:System.STAThreadAttribute> attribute or the <xref:System.MTAThreadAttribute> attribute to the main method of the application.</span></span>  
  
 <span data-ttu-id="de967-122">İkinci nedeni, ideal olarak, kodu çağırır `CoUninitialize` yöntemi çağrısı yaklaşık sonlandırmak için iş parçacığı olan ve hiçbir RCW vardır ve temel alınan COM bileşenleri yine de iş parçacığı tarafından kullanıma kadar gecikme değiştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="de967-122">For the second cause, ideally, the code that calls the `CoUninitialize` method should be modified to delay the call until the thread is about to terminate and there are no RCWs and their underlying COM components still in use by the thread.</span></span> <span data-ttu-id="de967-123">Ancak, çağıran kodu değiştirmek mümkün değilse, `CoUninitialize` bu şekilde başlatılmamış parçacıklarından yöntemi, ardından hiçbir RCW kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="de967-123">However, if it is not possible to modify the code that calls the `CoUninitialize` method, then no RCWs should be used from threads that are uninitialized in this way.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="de967-124">Çalışma zamanı üzerindeki etkisi</span><span class="sxs-lookup"><span data-stu-id="de967-124">Effect on the Runtime</span></span>  
 <span data-ttu-id="de967-125">Bu mda'nın CLR üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="de967-125">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="de967-126">Çıkış</span><span class="sxs-lookup"><span data-stu-id="de967-126">Output</span></span>  
 <span data-ttu-id="de967-127">Geçerli iş parçacığının COM Grup durumu ve kod uygulanmaya çalışılıyor durumu.</span><span class="sxs-lookup"><span data-stu-id="de967-127">The COM apartment state of the current thread, and the state that the code was attempting to apply.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="de967-128">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="de967-128">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidApartmentStateChange />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="de967-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="de967-129">Example</span></span>  
 <span data-ttu-id="de967-130">Aşağıdaki kod örneği, bu mda'nın etkinleştirebilirsiniz bir durumu gösterir.</span><span class="sxs-lookup"><span data-stu-id="de967-130">The following code example demonstrates a situation that can activate this MDA.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="de967-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="de967-131">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="de967-132">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="de967-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="de967-133">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="de967-133">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
