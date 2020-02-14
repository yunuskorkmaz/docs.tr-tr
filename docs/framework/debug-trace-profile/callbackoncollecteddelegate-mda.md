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
ms.openlocfilehash: eb14e0df5396d92eb223dde2e562684c4c318295
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217576"
---
# <a name="callbackoncollecteddelegate-mda"></a><span data-ttu-id="06aca-102">callbackOnCollectedDelegate MDA</span><span class="sxs-lookup"><span data-stu-id="06aca-102">callbackOnCollectedDelegate MDA</span></span>
<span data-ttu-id="06aca-103">`callbackOnCollectedDelegate` yönetilen hata ayıklama Yardımcısı (MDA), bir temsilci yönetilen 'den yönetilmeyen koda bir işlev işaretçisi olarak sıralanırsa ve temsilci atık toplandıktan sonra bu işlev işaretçisine bir geri çağırma yerleştirildiğinde etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="06aca-103">The `callbackOnCollectedDelegate` managed debugging assistant (MDA) is activated if a delegate is marshaled from managed to unmanaged code as a function pointer and a callback is placed on that function pointer after the delegate has been garbage collected.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="06aca-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="06aca-104">Symptoms</span></span>  
 <span data-ttu-id="06aca-105">Yönetilen temsilcilerden alınan işlev işaretçileri aracılığıyla yönetilen koda çağrı yapmaya çalışırken erişim ihlalleri oluşur.</span><span class="sxs-lookup"><span data-stu-id="06aca-105">Access violations occur when attempting to call into managed code through function pointers that were obtained from managed delegates.</span></span> <span data-ttu-id="06aca-106">Bu hatalar, ortak dil çalışma zamanı (CLR) hataları olmadığı sürece, erişim ihlali CLR kodunda gerçekleştiği için gibi görünebilir.</span><span class="sxs-lookup"><span data-stu-id="06aca-106">These failures, while not common language runtime (CLR) bugs, may appear to be so because the access violation occurs in the CLR code.</span></span>  
  
 <span data-ttu-id="06aca-107">Hata tutarlı değil; Bazen işlev işaretçisindeki çağrı başarılı olur ve bazen başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="06aca-107">The failure is not consistent; sometimes the call on the function pointer succeeds and sometimes it fails.</span></span> <span data-ttu-id="06aca-108">Hata yalnızca ağır yük altında ya da rastgele sayıda girişimde bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="06aca-108">The failure might occur only under heavy load or on a random number of attempts.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="06aca-109">Nedeni</span><span class="sxs-lookup"><span data-stu-id="06aca-109">Cause</span></span>  
 <span data-ttu-id="06aca-110">İşlev işaretçisinin oluşturulduğu ve yönetilmeyen koda açık olan temsilci atık olarak toplandı.</span><span class="sxs-lookup"><span data-stu-id="06aca-110">The delegate from which the function pointer was created and exposed to unmanaged code was garbage collected.</span></span> <span data-ttu-id="06aca-111">Yönetilmeyen bileşen işlev işaretçisi üzerinde çağırmayı denediğinde, bir erişim ihlali oluşturur.</span><span class="sxs-lookup"><span data-stu-id="06aca-111">When the unmanaged component tries to call on the function pointer, it generates an access violation.</span></span>  
  
 <span data-ttu-id="06aca-112">Çöp toplamanın ne zaman gerçekleşeceğini bağlı olduğundan hata rastgele görünür.</span><span class="sxs-lookup"><span data-stu-id="06aca-112">The failure appears random because it depends on when garbage collection occurs.</span></span> <span data-ttu-id="06aca-113">Bir temsilci koleksiyon için uygun ise, çöp toplama işlemi geri aramadan sonra gerçekleşebilir ve çağrı başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="06aca-113">If a delegate is eligible for collection, the garbage collection can occur after the callback and the call succeeds.</span></span> <span data-ttu-id="06aca-114">Diğer zamanlarda çöp toplama işlemi geri aramadan önce oluşur, geri arama bir erişim ihlali oluşturur ve program durur.</span><span class="sxs-lookup"><span data-stu-id="06aca-114">At other times, the garbage collection occurs before the callback, the callback generates an access violation, and the program stops.</span></span>  
  
 <span data-ttu-id="06aca-115">Hatanın olasılığı, işlev işaretçisindeki ve geri çağırma işleminin yanı sıra çöp koleksiyonları sıklığının sıralaması arasındaki zamana bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="06aca-115">The probability of the failure depends on the time between marshaling the delegate and the callback on the function pointer as well as the frequency of garbage collections.</span></span> <span data-ttu-id="06aca-116">Temsilciyi hazırlama ve geri çağırma işlemi arasında geçen süre kısaysa hata tek tek olur.</span><span class="sxs-lookup"><span data-stu-id="06aca-116">The failure is sporadic if the time between marshaling the delegate and the ensuing callback is short.</span></span> <span data-ttu-id="06aca-117">Bu genellikle, işlev işaretçisini alan yönetilmeyen yöntemin, daha sonra kullanmak üzere işlev işaretçisini kaydetmediğini, ancak döndürmeden önce işlemini tamamlaması için hemen işlev işaretçisine geri çağırması durumunda oluşur.</span><span class="sxs-lookup"><span data-stu-id="06aca-117">This is usually the case if the unmanaged method receiving the function pointer does not save the function pointer for later use but instead calls back on the function pointer immediately to complete its operation before returning.</span></span> <span data-ttu-id="06aca-118">Benzer şekilde, bir sistem ağır yük altındayken daha fazla çöp toplama meydana gelir. Bu, geri aramadan önce çöp toplamanın gerçekleşmesinin daha büyük olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="06aca-118">Similarly, more garbage collections occur when a system is under heavy load, which makes it more likely that a garbage collection will occur before the callback.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="06aca-119">Çözüm</span><span class="sxs-lookup"><span data-stu-id="06aca-119">Resolution</span></span>  
 <span data-ttu-id="06aca-120">Bir temsilci yönetilmeyen bir işlev işaretçisi olarak sıralandıktan sonra çöp toplayıcı ömrünü izleyemez.</span><span class="sxs-lookup"><span data-stu-id="06aca-120">Once a delegate has been marshaled out as an unmanaged function pointer, the garbage collector cannot track its lifetime.</span></span> <span data-ttu-id="06aca-121">Bunun yerine, yönetilmeyen işlev işaretçisinin ömrü boyunca kodunuzun temsilciye bir başvuru tutması gerekir.</span><span class="sxs-lookup"><span data-stu-id="06aca-121">Instead, your code must keep a reference to the delegate for the lifetime of the unmanaged function pointer.</span></span> <span data-ttu-id="06aca-122">Ancak bunu yapabilmeniz için önce hangi temsilcinin toplandığını belirlemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="06aca-122">But before you can do that, you first must identify which delegate was collected.</span></span> <span data-ttu-id="06aca-123">MDA etkinleştirildiğinde, temsilcinin tür adını sağlar.</span><span class="sxs-lookup"><span data-stu-id="06aca-123">When the MDA is activated, it provides the type name of the delegate.</span></span> <span data-ttu-id="06aca-124">Bu temsilciyi, bu temsilciyi yönetilmeyen koda geçiren platform çağrısı veya COM imzaları için aramak üzere kullanın.</span><span class="sxs-lookup"><span data-stu-id="06aca-124">Use this name to search your code for platform invoke or COM signatures that pass that delegate out to unmanaged code.</span></span> <span data-ttu-id="06aca-125">Sorunlu temsilci bu çağrı sitelerinden biri aracılığıyla geçirilir.</span><span class="sxs-lookup"><span data-stu-id="06aca-125">The offending delegate is passed out through one of these call sites.</span></span> <span data-ttu-id="06aca-126">Çalışma zamanına her geri aramadan önce çöp toplamayı zorlamak için `gcUnmanagedToManaged` MDA ' i de etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="06aca-126">You can also enable the `gcUnmanagedToManaged` MDA to force a garbage collection before every callback into the runtime.</span></span> <span data-ttu-id="06aca-127">Bu, çöp toplamanın geri aramadan önce her zaman gerçekleşmesini sağlayarak çöp toplama tarafından sunulan belirsizlik kaldırır.</span><span class="sxs-lookup"><span data-stu-id="06aca-127">This will remove the uncertainty introduced by the garbage collection by ensuring that a garbage collection always occurs before the callback.</span></span> <span data-ttu-id="06aca-128">Hangi temsilcinin toplandığını öğrendikten sonra, sıralanmış yönetilmeyen işlev işaretçisinin ömrü boyunca yönetilen tarafta bu temsilciye bir başvuru tutmak için kodunuzu değiştirin.</span><span class="sxs-lookup"><span data-stu-id="06aca-128">Once you know what delegate was collected, change your code to keep a reference to that delegate on the managed side for the lifetime of the marshaled unmanaged function pointer.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="06aca-129">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="06aca-129">Effect on the Runtime</span></span>  
 <span data-ttu-id="06aca-130">Temsilciler işlev işaretçileri olarak sıralandığında, çalışma zamanı Yönetilmeyenden yönetilene geçişi yapan bir dönüştürücü ayırır.</span><span class="sxs-lookup"><span data-stu-id="06aca-130">When delegates are marshaled as function pointers, the runtime allocates a thunk that does the transition from unmanaged to managed.</span></span> <span data-ttu-id="06aca-131">Bu dönüştürücü, yönetilmeyen kodun yönetilen temsilci son olarak çağrılmadan önce ne kadar çağırıldığı şeydir.</span><span class="sxs-lookup"><span data-stu-id="06aca-131">This thunk is what the unmanaged code actually calls before the managed delegate is finally invoked.</span></span> <span data-ttu-id="06aca-132">`callbackOnCollectedDelegate` MDA etkin olmadan, temsilci toplandığında yönetilmeyen sıralama kodu silinir.</span><span class="sxs-lookup"><span data-stu-id="06aca-132">Without the `callbackOnCollectedDelegate` MDA enabled, the unmanaged marshaling code is deleted when the delegate is collected.</span></span> <span data-ttu-id="06aca-133">`callbackOnCollectedDelegate` MDA etkinken, temsilci toplandığında yönetilmeyen sıralama kodu hemen silinmez.</span><span class="sxs-lookup"><span data-stu-id="06aca-133">With the `callbackOnCollectedDelegate` MDA enabled, the unmanaged marshaling code is not immediately deleted when the delegate is collected.</span></span> <span data-ttu-id="06aca-134">Bunun yerine, son 1.000 örnek varsayılan olarak etkin tutulur ve çağrıldığında MDA öğesini etkinleştirmek için değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="06aca-134">Instead, the last 1,000 instances are kept alive by default and changed to activate the MDA when called.</span></span> <span data-ttu-id="06aca-135">Dönüştürücü, 1.001 daha fazla sıralanmış temsilci toplandıktan sonra silinir.</span><span class="sxs-lookup"><span data-stu-id="06aca-135">The thunk is eventually deleted after 1,001 more marshaled delegates are collected.</span></span>  
  
## <a name="output"></a><span data-ttu-id="06aca-136">Çıktı</span><span class="sxs-lookup"><span data-stu-id="06aca-136">Output</span></span>  
 <span data-ttu-id="06aca-137">MDA, yönetilmeyen işlev işaretçisi üzerinde bir geri çağırma yapılmadan önce toplanan temsilcinin tür adını bildirir.</span><span class="sxs-lookup"><span data-stu-id="06aca-137">The MDA reports the type name of the delegate that was collected before a callback was attempted on its unmanaged function pointer.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="06aca-138">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="06aca-138">Configuration</span></span>  
 <span data-ttu-id="06aca-139">Aşağıdaki örnek, uygulama yapılandırma seçeneklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="06aca-139">The following example shows the application configuration options.</span></span> <span data-ttu-id="06aca-140">MDA 'ın 1.500 olarak etkin kalmasını sağlar dönüştürücüler sayısını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="06aca-140">It sets the number of thunks the MDA keeps alive to 1,500.</span></span> <span data-ttu-id="06aca-141">Varsayılan `listSize` değeri 1.000, en az 50, en yüksek değer ise 2.000.</span><span class="sxs-lookup"><span data-stu-id="06aca-141">The default `listSize` value is 1,000, the minimum is 50, and the maximum is 2,000.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <callbackOnCollectedDelegate listSize="1500" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="06aca-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="06aca-142">Example</span></span>  
 <span data-ttu-id="06aca-143">Aşağıdaki örnekte, bu MDA ' i etkinleştirebilecek bir durum gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="06aca-143">The following example demonstrates a situation that can activate this MDA:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="06aca-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="06aca-144">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="06aca-145">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="06aca-145">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="06aca-146">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="06aca-146">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
- [<span data-ttu-id="06aca-147">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="06aca-147">gcUnmanagedToManaged</span></span>](gcunmanagedtomanaged-mda.md)
