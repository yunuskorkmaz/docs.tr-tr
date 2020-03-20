---
title: callbackOnCollectedDelegate MDA
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- MDAs (managed debugging assistants), garbage collection
- managed debugging assistants (MDAs), callback on collected delegates
- MDAs (managed debugging assistants), callback on collected delegates
- callback on delegate after garbage collection
- callbackOnCollectedDelegate MDA
- managed debugging assistants (MDAs), garbage collection
- call back collected delegates
- garbage collection, run-time errors
- delegates [.NET Framework], garbage collection
ms.assetid: 398b0ce0-5cc9-4518-978d-b8263aa21e5b
ms.openlocfilehash: d4ca777fa5b41433eec227762fe315f22ab33cf6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174231"
---
# <a name="callbackoncollecteddelegate-mda"></a><span data-ttu-id="6d257-102">callbackOnCollectedDelegate MDA</span><span class="sxs-lookup"><span data-stu-id="6d257-102">callbackOnCollectedDelegate MDA</span></span>
<span data-ttu-id="6d257-103">Yönetilen `callbackOnCollectedDelegate` hata ayıklama yardımcısı (MDA), bir temsilci yönetilen koddan işlev işaretçisi olarak denetlenirse etkinleştirilir ve temsilci çöp toplandıktan sonra bu işlev işaretçisine bir geri arama yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="6d257-103">The `callbackOnCollectedDelegate` managed debugging assistant (MDA) is activated if a delegate is marshaled from managed to unmanaged code as a function pointer and a callback is placed on that function pointer after the delegate has been garbage collected.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="6d257-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="6d257-104">Symptoms</span></span>  
 <span data-ttu-id="6d257-105">Erişim ihlalleri, yönetilen temsilcilerden alınan işlev işaretçileri aracılığıyla yönetilen koda çağrı yapmaya çalışırken oluşur.</span><span class="sxs-lookup"><span data-stu-id="6d257-105">Access violations occur when attempting to call into managed code through function pointers that were obtained from managed delegates.</span></span> <span data-ttu-id="6d257-106">Bu hatalar, yaygın dil çalışma zamanı (CLR) hataları olmasa da, erişim ihlali CLR kodunda oluştuğundan öyle görünebilir.</span><span class="sxs-lookup"><span data-stu-id="6d257-106">These failures, while not common language runtime (CLR) bugs, may appear to be so because the access violation occurs in the CLR code.</span></span>  
  
 <span data-ttu-id="6d257-107">Hata tutarlı değildir; bazen işlev işaretçisi üzerindeki çağrı başarılı olur ve bazen başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="6d257-107">The failure is not consistent; sometimes the call on the function pointer succeeds and sometimes it fails.</span></span> <span data-ttu-id="6d257-108">Hata yalnızca ağır yük altında veya rasgele sayıda denemede oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="6d257-108">The failure might occur only under heavy load or on a random number of attempts.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="6d257-109">Nedeni</span><span class="sxs-lookup"><span data-stu-id="6d257-109">Cause</span></span>  
 <span data-ttu-id="6d257-110">İşlev işaretçisinin oluşturulduğu ve yönetilmeyen koda maruz kalan temsilci çöp toplandı.</span><span class="sxs-lookup"><span data-stu-id="6d257-110">The delegate from which the function pointer was created and exposed to unmanaged code was garbage collected.</span></span> <span data-ttu-id="6d257-111">Yönetilmeyen bileşen işlev işaretçisini çağırmaya çalıştığında, bir erişim ihlali oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6d257-111">When the unmanaged component tries to call on the function pointer, it generates an access violation.</span></span>  
  
 <span data-ttu-id="6d257-112">Çöp toplamanın ne zaman oluştuğuna bağlı olduğundan hata rasgele görünür.</span><span class="sxs-lookup"><span data-stu-id="6d257-112">The failure appears random because it depends on when garbage collection occurs.</span></span> <span data-ttu-id="6d257-113">Bir temsilci toplama için uygunsa, geri arama dan sonra çöp toplama oluşabilir ve arama başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="6d257-113">If a delegate is eligible for collection, the garbage collection can occur after the callback and the call succeeds.</span></span> <span data-ttu-id="6d257-114">Diğer zamanlarda, çöp toplama geri arama önce oluşur, geri arama bir erişim ihlali oluşturur ve program durur.</span><span class="sxs-lookup"><span data-stu-id="6d257-114">At other times, the garbage collection occurs before the callback, the callback generates an access violation, and the program stops.</span></span>  
  
 <span data-ttu-id="6d257-115">Hata olasılığı, temsilciyi mareşalleme ile işlev işaretçisindeki geri arama arasındaki süreye ve çöp koleksiyonlarının sıklığına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="6d257-115">The probability of the failure depends on the time between marshaling the delegate and the callback on the function pointer as well as the frequency of garbage collections.</span></span> <span data-ttu-id="6d257-116">Temsilci yimareme ile takip eden geri arama arasındaki süre kısaysa, başarısızlık düzensizdir.</span><span class="sxs-lookup"><span data-stu-id="6d257-116">The failure is sporadic if the time between marshaling the delegate and the ensuing callback is short.</span></span> <span data-ttu-id="6d257-117">İşlev işaretçisini alan yönetilmeyen yöntem işlev işaretçisini daha sonra kullanmak üzere kaydetmez, bunun yerine işlev işaretçisini geri çağırıp dönmeden önce işlemini tamamlamak için hemen geri çağırırsa, genellikle durum böyledir.</span><span class="sxs-lookup"><span data-stu-id="6d257-117">This is usually the case if the unmanaged method receiving the function pointer does not save the function pointer for later use but instead calls back on the function pointer immediately to complete its operation before returning.</span></span> <span data-ttu-id="6d257-118">Benzer şekilde, bir sistem ağır yük altında yken daha fazla çöp toplama oluşur, bu da geri çağırmadan önce bir çöp toplamanın oluşma olasılığını arttırır.</span><span class="sxs-lookup"><span data-stu-id="6d257-118">Similarly, more garbage collections occur when a system is under heavy load, which makes it more likely that a garbage collection will occur before the callback.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="6d257-119">Çözüm</span><span class="sxs-lookup"><span data-stu-id="6d257-119">Resolution</span></span>  
 <span data-ttu-id="6d257-120">Bir temsilci yönetilmeyen bir işlev işaretçisi olarak sıralandıktan sonra, çöp toplayıcı ömrünü izleyemez.</span><span class="sxs-lookup"><span data-stu-id="6d257-120">Once a delegate has been marshaled out as an unmanaged function pointer, the garbage collector cannot track its lifetime.</span></span> <span data-ttu-id="6d257-121">Bunun yerine, kodunuz yönetilmeyen işlev işaretçisinin ömrü boyunca temsilciye bir başvuru tutmalı.</span><span class="sxs-lookup"><span data-stu-id="6d257-121">Instead, your code must keep a reference to the delegate for the lifetime of the unmanaged function pointer.</span></span> <span data-ttu-id="6d257-122">Ancak bunu yapmadan önce hangi temsilcinin toplandığını belirlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6d257-122">But before you can do that, you first must identify which delegate was collected.</span></span> <span data-ttu-id="6d257-123">MDA etkinleştirildiğinde, temsilcinin tür adını sağlar.</span><span class="sxs-lookup"><span data-stu-id="6d257-123">When the MDA is activated, it provides the type name of the delegate.</span></span> <span data-ttu-id="6d257-124">Bu temsilciyi yönetilmeyen koda aktaran platform çağrısı veya COM imzaları için kodunuzu aramak için bu adı kullanın.</span><span class="sxs-lookup"><span data-stu-id="6d257-124">Use this name to search your code for platform invoke or COM signatures that pass that delegate out to unmanaged code.</span></span> <span data-ttu-id="6d257-125">Kusurlu temsilci bu çağrı sitelerinden biri üzerinden dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="6d257-125">The offending delegate is passed out through one of these call sites.</span></span> <span data-ttu-id="6d257-126">Ayrıca, MDA'nın `gcUnmanagedToManaged` her geri aramadan önce bir çöp toplamayı çalıştırma süresine zorlanmasını da sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6d257-126">You can also enable the `gcUnmanagedToManaged` MDA to force a garbage collection before every callback into the runtime.</span></span> <span data-ttu-id="6d257-127">Bu, çöp toplamanın her zaman geri aramadan önce oluşmasını sağlayarak çöp toplama tarafından ortaya çıkan belirsizliği ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="6d257-127">This will remove the uncertainty introduced by the garbage collection by ensuring that a garbage collection always occurs before the callback.</span></span> <span data-ttu-id="6d257-128">Hangi temsilcinin toplandığını bildiğinizde, mareşal olarak yönetilmeyen işlev işaretçisinin ömrü boyunca yönetilen taraftaki temsilciye bir başvuru tutmak için kodunuzu değiştirin.</span><span class="sxs-lookup"><span data-stu-id="6d257-128">Once you know what delegate was collected, change your code to keep a reference to that delegate on the managed side for the lifetime of the marshaled unmanaged function pointer.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="6d257-129">Çalışma Süresi üzerindeki etkisi</span><span class="sxs-lookup"><span data-stu-id="6d257-129">Effect on the Runtime</span></span>  
 <span data-ttu-id="6d257-130">Temsilciler işlev işaretçisi olarak marshaled olduğunda, çalışma zamanı yönetilmeyen den yönetilen geçiş yapan bir thunk ayırır.</span><span class="sxs-lookup"><span data-stu-id="6d257-130">When delegates are marshaled as function pointers, the runtime allocates a thunk that does the transition from unmanaged to managed.</span></span> <span data-ttu-id="6d257-131">Bu thunk, yönetilen temsilci sonunda çağrılmadan önce yönetilmeyen kodun gerçekte çağırdığı şeydir.</span><span class="sxs-lookup"><span data-stu-id="6d257-131">This thunk is what the unmanaged code actually calls before the managed delegate is finally invoked.</span></span> <span data-ttu-id="6d257-132">`callbackOnCollectedDelegate` MDA etkin olmadan, temsilci toplandığında yönetilmeyen mareşal kodu silinir.</span><span class="sxs-lookup"><span data-stu-id="6d257-132">Without the `callbackOnCollectedDelegate` MDA enabled, the unmanaged marshaling code is deleted when the delegate is collected.</span></span> <span data-ttu-id="6d257-133">`callbackOnCollectedDelegate` MDA etkinleştirildiğinde, yönetilmeyen mareşalkodu temsilci toplandığında hemen silinmez.</span><span class="sxs-lookup"><span data-stu-id="6d257-133">With the `callbackOnCollectedDelegate` MDA enabled, the unmanaged marshaling code is not immediately deleted when the delegate is collected.</span></span> <span data-ttu-id="6d257-134">Bunun yerine, son 1.000 örnek varsayılan olarak canlı tutulur ve çağrıldığında MDA etkinleştirmek için değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="6d257-134">Instead, the last 1,000 instances are kept alive by default and changed to activate the MDA when called.</span></span> <span data-ttu-id="6d257-135">Thunk, 1.001 mareşal delege daha toplandıktan sonra silinir.</span><span class="sxs-lookup"><span data-stu-id="6d257-135">The thunk is eventually deleted after 1,001 more marshaled delegates are collected.</span></span>  
  
## <a name="output"></a><span data-ttu-id="6d257-136">Çıktı</span><span class="sxs-lookup"><span data-stu-id="6d257-136">Output</span></span>  
 <span data-ttu-id="6d257-137">MDA, yönetilmeyen işlev işaretçisi üzerinde geri arama girişiminde bulunulmadan önce toplanan temsilcinin türünü bildirir.</span><span class="sxs-lookup"><span data-stu-id="6d257-137">The MDA reports the type name of the delegate that was collected before a callback was attempted on its unmanaged function pointer.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="6d257-138">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6d257-138">Configuration</span></span>  
 <span data-ttu-id="6d257-139">Aşağıdaki örnekte uygulama yapılandırma seçenekleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6d257-139">The following example shows the application configuration options.</span></span> <span data-ttu-id="6d257-140">MDA'nın hayatta tuttuğu thunk sayısını 1500'e ayarlıyor.</span><span class="sxs-lookup"><span data-stu-id="6d257-140">It sets the number of thunks the MDA keeps alive to 1,500.</span></span> <span data-ttu-id="6d257-141">Varsayılan `listSize` değer 1.000, en az 50 ve en büyük değer 2.000'dir.</span><span class="sxs-lookup"><span data-stu-id="6d257-141">The default `listSize` value is 1,000, the minimum is 50, and the maximum is 2,000.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <callbackOnCollectedDelegate listSize="1500" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="6d257-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="6d257-142">Example</span></span>  
 <span data-ttu-id="6d257-143">Aşağıdaki örnek, bu MDA'yı etkinleştirebilecek bir durumu gösterir:</span><span class="sxs-lookup"><span data-stu-id="6d257-143">The following example demonstrates a situation that can activate this MDA:</span></span>  
  
```cpp
// Library.cpp : Defines the unmanaged entry point for the DLL application.  
#include "windows.h"  
#include "stdio.h"  
  
void (__stdcall *g_pfTarget)();  
  
void __stdcall Initialize(void __stdcall pfTarget())  
{  
    g_pfTarget = pfTarget;  
}  
  
void __stdcall Callback()  
{  
    g_pfTarget();  
}
```

```csharp
// C# Client  
using System;  
using System.Runtime.InteropServices;  
  
public class Entry  
{  
    public delegate void DCallback();  
  
    public static void Main()  
    {  
        new Entry();  
        Initialize(Target);  
        GC.Collect();  
        GC.WaitForPendingFinalizers();  
        Callback();  
    }  
  
    public static void Target()  
    {
    }  
  
    [DllImport("Library", CallingConvention = CallingConvention.StdCall)]  
    public static extern void Initialize(DCallback pfDelegate);  
  
    [DllImport ("Library", CallingConvention = CallingConvention.StdCall)]  
    public static extern void Callback();  
  
    ~Entry() { Console.Error.WriteLine("Entry Collected"); }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="6d257-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6d257-144">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="6d257-145">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="6d257-145">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="6d257-146">Birlikte Çalışma Hazırlama</span><span class="sxs-lookup"><span data-stu-id="6d257-146">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
- [<span data-ttu-id="6d257-147">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="6d257-147">gcUnmanagedToManaged</span></span>](gcunmanagedtomanaged-mda.md)
