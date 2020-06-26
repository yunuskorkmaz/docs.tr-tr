---
title: callbackOnCollectedDelegate MDA
description: .NET 'teki callbackOnCollectedDelegate yönetilen hata ayıklama Yardımcısı 'nı (MDA) inceleyerek, temsilci atık toplandıktan sonra bir geri çağırma gerçekleşiyorsa çağrılır.
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
ms.openlocfilehash: 32f02a4e65455f11f3bfa9260caae8b4e48f494e
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416037"
---
# <a name="callbackoncollecteddelegate-mda"></a><span data-ttu-id="83b83-103">callbackOnCollectedDelegate MDA</span><span class="sxs-lookup"><span data-stu-id="83b83-103">callbackOnCollectedDelegate MDA</span></span>
<span data-ttu-id="83b83-104">`callbackOnCollectedDelegate`Yönetilen hata ayıklama Yardımcısı (MDA), bir temsilci yönetilen 'den yönetilmeyen koda bir işlev işaretçisi olarak sıralanırsa ve temsilci atık toplandıktan sonra bu işlev işaretçisine bir geri çağırma yerleştirildiğinde etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="83b83-104">The `callbackOnCollectedDelegate` managed debugging assistant (MDA) is activated if a delegate is marshaled from managed to unmanaged code as a function pointer and a callback is placed on that function pointer after the delegate has been garbage collected.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="83b83-105">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="83b83-105">Symptoms</span></span>  
 <span data-ttu-id="83b83-106">Yönetilen temsilcilerden alınan işlev işaretçileri aracılığıyla yönetilen koda çağrı yapmaya çalışırken erişim ihlalleri oluşur.</span><span class="sxs-lookup"><span data-stu-id="83b83-106">Access violations occur when attempting to call into managed code through function pointers that were obtained from managed delegates.</span></span> <span data-ttu-id="83b83-107">Bu hatalar, ortak dil çalışma zamanı (CLR) hataları olmadığı sürece, erişim ihlali CLR kodunda gerçekleştiği için gibi görünebilir.</span><span class="sxs-lookup"><span data-stu-id="83b83-107">These failures, while not common language runtime (CLR) bugs, may appear to be so because the access violation occurs in the CLR code.</span></span>  
  
 <span data-ttu-id="83b83-108">Hata tutarlı değil; Bazen işlev işaretçisindeki çağrı başarılı olur ve bazen başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="83b83-108">The failure is not consistent; sometimes the call on the function pointer succeeds and sometimes it fails.</span></span> <span data-ttu-id="83b83-109">Hata yalnızca ağır yük altında ya da rastgele sayıda girişimde bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="83b83-109">The failure might occur only under heavy load or on a random number of attempts.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="83b83-110">Nedeni</span><span class="sxs-lookup"><span data-stu-id="83b83-110">Cause</span></span>  
 <span data-ttu-id="83b83-111">İşlev işaretçisinin oluşturulduğu ve yönetilmeyen koda açık olan temsilci atık olarak toplandı.</span><span class="sxs-lookup"><span data-stu-id="83b83-111">The delegate from which the function pointer was created and exposed to unmanaged code was garbage collected.</span></span> <span data-ttu-id="83b83-112">Yönetilmeyen bileşen işlev işaretçisi üzerinde çağırmayı denediğinde, bir erişim ihlali oluşturur.</span><span class="sxs-lookup"><span data-stu-id="83b83-112">When the unmanaged component tries to call on the function pointer, it generates an access violation.</span></span>  
  
 <span data-ttu-id="83b83-113">Çöp toplamanın ne zaman gerçekleşeceğini bağlı olduğundan hata rastgele görünür.</span><span class="sxs-lookup"><span data-stu-id="83b83-113">The failure appears random because it depends on when garbage collection occurs.</span></span> <span data-ttu-id="83b83-114">Bir temsilci koleksiyon için uygun ise, çöp toplama işlemi geri aramadan sonra gerçekleşebilir ve çağrı başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="83b83-114">If a delegate is eligible for collection, the garbage collection can occur after the callback and the call succeeds.</span></span> <span data-ttu-id="83b83-115">Diğer zamanlarda çöp toplama işlemi geri aramadan önce oluşur, geri arama bir erişim ihlali oluşturur ve program durur.</span><span class="sxs-lookup"><span data-stu-id="83b83-115">At other times, the garbage collection occurs before the callback, the callback generates an access violation, and the program stops.</span></span>  
  
 <span data-ttu-id="83b83-116">Hatanın olasılığı, işlev işaretçisindeki ve geri çağırma işleminin yanı sıra çöp koleksiyonları sıklığının sıralaması arasındaki zamana bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="83b83-116">The probability of the failure depends on the time between marshaling the delegate and the callback on the function pointer as well as the frequency of garbage collections.</span></span> <span data-ttu-id="83b83-117">Temsilciyi hazırlama ve geri çağırma işlemi arasında geçen süre kısaysa hata tek tek olur.</span><span class="sxs-lookup"><span data-stu-id="83b83-117">The failure is sporadic if the time between marshaling the delegate and the ensuing callback is short.</span></span> <span data-ttu-id="83b83-118">Bu genellikle, işlev işaretçisini alan yönetilmeyen yöntemin, daha sonra kullanmak üzere işlev işaretçisini kaydetmediğini, ancak döndürmeden önce işlemini tamamlaması için hemen işlev işaretçisine geri çağırması durumunda oluşur.</span><span class="sxs-lookup"><span data-stu-id="83b83-118">This is usually the case if the unmanaged method receiving the function pointer does not save the function pointer for later use but instead calls back on the function pointer immediately to complete its operation before returning.</span></span> <span data-ttu-id="83b83-119">Benzer şekilde, bir sistem ağır yük altındayken daha fazla çöp toplama meydana gelir. Bu, geri aramadan önce çöp toplamanın gerçekleşmesinin daha büyük olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="83b83-119">Similarly, more garbage collections occur when a system is under heavy load, which makes it more likely that a garbage collection will occur before the callback.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="83b83-120">Çözüm</span><span class="sxs-lookup"><span data-stu-id="83b83-120">Resolution</span></span>  
 <span data-ttu-id="83b83-121">Bir temsilci yönetilmeyen bir işlev işaretçisi olarak sıralandıktan sonra çöp toplayıcı ömrünü izleyemez.</span><span class="sxs-lookup"><span data-stu-id="83b83-121">Once a delegate has been marshaled out as an unmanaged function pointer, the garbage collector cannot track its lifetime.</span></span> <span data-ttu-id="83b83-122">Bunun yerine, yönetilmeyen işlev işaretçisinin ömrü boyunca kodunuzun temsilciye bir başvuru tutması gerekir.</span><span class="sxs-lookup"><span data-stu-id="83b83-122">Instead, your code must keep a reference to the delegate for the lifetime of the unmanaged function pointer.</span></span> <span data-ttu-id="83b83-123">Ancak bunu yapabilmeniz için önce hangi temsilcinin toplandığını belirlemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="83b83-123">But before you can do that, you first must identify which delegate was collected.</span></span> <span data-ttu-id="83b83-124">MDA etkinleştirildiğinde, temsilcinin tür adını sağlar.</span><span class="sxs-lookup"><span data-stu-id="83b83-124">When the MDA is activated, it provides the type name of the delegate.</span></span> <span data-ttu-id="83b83-125">Bu temsilciyi, bu temsilciyi yönetilmeyen koda geçiren platform çağrısı veya COM imzaları için aramak üzere kullanın.</span><span class="sxs-lookup"><span data-stu-id="83b83-125">Use this name to search your code for platform invoke or COM signatures that pass that delegate out to unmanaged code.</span></span> <span data-ttu-id="83b83-126">Sorunlu temsilci bu çağrı sitelerinden biri aracılığıyla geçirilir.</span><span class="sxs-lookup"><span data-stu-id="83b83-126">The offending delegate is passed out through one of these call sites.</span></span> <span data-ttu-id="83b83-127">Ayrıca, `gcUnmanagedToManaged` çalışma zamanına her geri çağırmadan önce bir çöp toplamayı zorlamak için mda ' i etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="83b83-127">You can also enable the `gcUnmanagedToManaged` MDA to force a garbage collection before every callback into the runtime.</span></span> <span data-ttu-id="83b83-128">Bu, çöp toplamanın geri aramadan önce her zaman gerçekleşmesini sağlayarak çöp toplama tarafından sunulan belirsizlik kaldırır.</span><span class="sxs-lookup"><span data-stu-id="83b83-128">This will remove the uncertainty introduced by the garbage collection by ensuring that a garbage collection always occurs before the callback.</span></span> <span data-ttu-id="83b83-129">Hangi temsilcinin toplandığını öğrendikten sonra, sıralanmış yönetilmeyen işlev işaretçisinin ömrü boyunca yönetilen tarafta bu temsilciye bir başvuru tutmak için kodunuzu değiştirin.</span><span class="sxs-lookup"><span data-stu-id="83b83-129">Once you know what delegate was collected, change your code to keep a reference to that delegate on the managed side for the lifetime of the marshaled unmanaged function pointer.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="83b83-130">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="83b83-130">Effect on the Runtime</span></span>  
 <span data-ttu-id="83b83-131">Temsilciler işlev işaretçileri olarak sıralandığında, çalışma zamanı Yönetilmeyenden yönetilene geçişi yapan bir dönüştürücü ayırır.</span><span class="sxs-lookup"><span data-stu-id="83b83-131">When delegates are marshaled as function pointers, the runtime allocates a thunk that does the transition from unmanaged to managed.</span></span> <span data-ttu-id="83b83-132">Bu dönüştürücü, yönetilmeyen kodun yönetilen temsilci son olarak çağrılmadan önce ne kadar çağırıldığı şeydir.</span><span class="sxs-lookup"><span data-stu-id="83b83-132">This thunk is what the unmanaged code actually calls before the managed delegate is finally invoked.</span></span> <span data-ttu-id="83b83-133">`callbackOnCollectedDelegate`MDA etkin olmadan, yönetilmeyen sıralama kodu, temsilci toplandığında silinir.</span><span class="sxs-lookup"><span data-stu-id="83b83-133">Without the `callbackOnCollectedDelegate` MDA enabled, the unmanaged marshaling code is deleted when the delegate is collected.</span></span> <span data-ttu-id="83b83-134">`callbackOnCollectedDelegate`MDA etkinleştirildikten sonra, temsilci toplandığında yönetilmeyen sıralama kodu hemen silinmez.</span><span class="sxs-lookup"><span data-stu-id="83b83-134">With the `callbackOnCollectedDelegate` MDA enabled, the unmanaged marshaling code is not immediately deleted when the delegate is collected.</span></span> <span data-ttu-id="83b83-135">Bunun yerine, son 1.000 örnek varsayılan olarak etkin tutulur ve çağrıldığında MDA öğesini etkinleştirmek için değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="83b83-135">Instead, the last 1,000 instances are kept alive by default and changed to activate the MDA when called.</span></span> <span data-ttu-id="83b83-136">Dönüştürücü, 1.001 daha fazla sıralanmış temsilci toplandıktan sonra silinir.</span><span class="sxs-lookup"><span data-stu-id="83b83-136">The thunk is eventually deleted after 1,001 more marshaled delegates are collected.</span></span>  
  
## <a name="output"></a><span data-ttu-id="83b83-137">Çıktı</span><span class="sxs-lookup"><span data-stu-id="83b83-137">Output</span></span>  
 <span data-ttu-id="83b83-138">MDA, yönetilmeyen işlev işaretçisi üzerinde bir geri çağırma yapılmadan önce toplanan temsilcinin tür adını bildirir.</span><span class="sxs-lookup"><span data-stu-id="83b83-138">The MDA reports the type name of the delegate that was collected before a callback was attempted on its unmanaged function pointer.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="83b83-139">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="83b83-139">Configuration</span></span>  
 <span data-ttu-id="83b83-140">Aşağıdaki örnek, uygulama yapılandırma seçeneklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="83b83-140">The following example shows the application configuration options.</span></span> <span data-ttu-id="83b83-141">MDA 'ın 1.500 olarak etkin kalmasını sağlar dönüştürücüler sayısını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="83b83-141">It sets the number of thunks the MDA keeps alive to 1,500.</span></span> <span data-ttu-id="83b83-142">Varsayılan `listSize` değer 1.000, en az 50, en fazla ise 2.000.</span><span class="sxs-lookup"><span data-stu-id="83b83-142">The default `listSize` value is 1,000, the minimum is 50, and the maximum is 2,000.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <callbackOnCollectedDelegate listSize="1500" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="83b83-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="83b83-143">Example</span></span>  
 <span data-ttu-id="83b83-144">Aşağıdaki örnekte, bu MDA ' i etkinleştirebilecek bir durum gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="83b83-144">The following example demonstrates a situation that can activate this MDA:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="83b83-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="83b83-145">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="83b83-146">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="83b83-146">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="83b83-147">Birlikte Çalışma Hazırlama</span><span class="sxs-lookup"><span data-stu-id="83b83-147">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
- [<span data-ttu-id="83b83-148">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="83b83-148">gcUnmanagedToManaged</span></span>](gcunmanagedtomanaged-mda.md)
