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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 459465064fe9db9f2f0aebb4153a3caea173af4e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59223647"
---
# <a name="callbackoncollecteddelegate-mda"></a><span data-ttu-id="93958-102">callbackOnCollectedDelegate MDA</span><span class="sxs-lookup"><span data-stu-id="93958-102">callbackOnCollectedDelegate MDA</span></span>
<span data-ttu-id="93958-103">`callbackOnCollectedDelegate` Yönetilen hata ayıklama Yardımcısı (MDA) etkin olduğu bir temsilci gelen yönetilen ve yönetilmeyen kodu bir işlev işaretçisi olarak sıralanır ve çöp olarak toplanacak temsilci sonra bir geri çağırma, işlev işaretçisi üzerinde yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="93958-103">The `callbackOnCollectedDelegate` managed debugging assistant (MDA) is activated if a delegate is marshaled from managed to unmanaged code as a function pointer and a callback is placed on that function pointer after the delegate has been garbage collected.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="93958-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="93958-104">Symptoms</span></span>  
 <span data-ttu-id="93958-105">Erişim ihlalleri yönetilen temsilciler edinilen işlev işaretçileri aracılığıyla yönetilen koda çağrı çalışılırken oluşur.</span><span class="sxs-lookup"><span data-stu-id="93958-105">Access violations occur when attempting to call into managed code through function pointers that were obtained from managed delegates.</span></span> <span data-ttu-id="93958-106">Olmayan ortak dil çalışma zamanı (CLR) hataları sırasında bu hatalar, erişim ihlali CLR kodda oluştuğu için bunu gibi görünebilir.</span><span class="sxs-lookup"><span data-stu-id="93958-106">These failures, while not common language runtime (CLR) bugs, may appear to be so because the access violation occurs in the CLR code.</span></span>  
  
 <span data-ttu-id="93958-107">Hata tutarlı değil; Bazen arama işlev işaretçisi üzerinde başarılı olur ve bazen başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="93958-107">The failure is not consistent; sometimes the call on the function pointer succeeds and sometimes it fails.</span></span> <span data-ttu-id="93958-108">Hata, ağır yük altında yalnızca veya rastgele bir deneme sayısı ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="93958-108">The failure might occur only under heavy load or on a random number of attempts.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="93958-109">Sebep</span><span class="sxs-lookup"><span data-stu-id="93958-109">Cause</span></span>  
 <span data-ttu-id="93958-110">Temsilci, işlev işaretçisi oluşturuldu ve yönetilmeyen kod sunulan çöp olarak toplanacak oluştu.</span><span class="sxs-lookup"><span data-stu-id="93958-110">The delegate from which the function pointer was created and exposed to unmanaged code was garbage collected.</span></span> <span data-ttu-id="93958-111">Yönetilmeyen bileşeni çağrı işlev işaretçisi üzerinde çalıştığında, erişim ihlaline neden olur.</span><span class="sxs-lookup"><span data-stu-id="93958-111">When the unmanaged component tries to call on the function pointer, it generates an access violation.</span></span>  
  
 <span data-ttu-id="93958-112">Çöp toplama oluştuğunda bağımlı olduğundan dolayı başarısız rastgele görünür.</span><span class="sxs-lookup"><span data-stu-id="93958-112">The failure appears random because it depends on when garbage collection occurs.</span></span> <span data-ttu-id="93958-113">Koleksiyon için bir temsilci uygunsa, çöp toplama geri çağırma sonra ortaya çıkabilir ve çağrının başarılı.</span><span class="sxs-lookup"><span data-stu-id="93958-113">If a delegate is eligible for collection, the garbage collection can occur after the callback and the call succeeds.</span></span> <span data-ttu-id="93958-114">Diğer zamanlarda, çöp toplama geri çağırma önce oluşur, geri çağırma erişim ihlaline neden olur ve program durdurur.</span><span class="sxs-lookup"><span data-stu-id="93958-114">At other times, the garbage collection occurs before the callback, the callback generates an access violation, and the program stops.</span></span>  
  
 <span data-ttu-id="93958-115">Temsilci ve geri arama işlev işaretçisi yanı sıra atık Toplamaların sıklığını hazırlama arasındaki zaman hata olasılığını bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="93958-115">The probability of the failure depends on the time between marshaling the delegate and the callback on the function pointer as well as the frequency of garbage collections.</span></span> <span data-ttu-id="93958-116">Temsilci ve erişilemez geri çağırma hazırlama arasındaki zaman kısa ise, ara sıra hatasıdır.</span><span class="sxs-lookup"><span data-stu-id="93958-116">The failure is sporadic if the time between marshaling the delegate and the ensuing callback is short.</span></span> <span data-ttu-id="93958-117">Bu genellikle işlev işaretçisi alma yönetilmeyen yöntemi daha sonra kullanmak için işlev işaretçisi kaydettiğinizde değil ancak bunun yerine geri dönmeden önce bu işlemi hemen tamamlanması işlev işaretçisi çağırır karşılaşılan bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="93958-117">This is usually the case if the unmanaged method receiving the function pointer does not save the function pointer for later use but instead calls back on the function pointer immediately to complete its operation before returning.</span></span> <span data-ttu-id="93958-118">Benzer şekilde, bir sistem daha olası bir çöp toplama geri çağırma önce meydana gelir getiren ağır yük altında olduğunda daha fazla çöp koleksiyonlarının meydana geldiği.</span><span class="sxs-lookup"><span data-stu-id="93958-118">Similarly, more garbage collections occur when a system is under heavy load, which makes it more likely that a garbage collection will occur before the callback.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="93958-119">Çözüm</span><span class="sxs-lookup"><span data-stu-id="93958-119">Resolution</span></span>  
 <span data-ttu-id="93958-120">Bir temsilci çıkış bir yönetilmeyen işlev işaretçisi sıralanmış sonra atık toplayıcı ömrü izleyemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="93958-120">Once a delegate has been marshaled out as an unmanaged function pointer, the garbage collector cannot track its lifetime.</span></span> <span data-ttu-id="93958-121">Bunun yerine, kodunuzu temsilci bir başvuru yönetilmeyen işlev işaretçisi ömrü boyunca tutmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="93958-121">Instead, your code must keep a reference to the delegate for the lifetime of the unmanaged function pointer.</span></span> <span data-ttu-id="93958-122">Ancak bunu yapmadan önce öncelikle hangi temsilci toplanan belirlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="93958-122">But before you can do that, you first must identify which delegate was collected.</span></span> <span data-ttu-id="93958-123">MDA etkinleştirildiğinde, temsilci türünün adı sağlar.</span><span class="sxs-lookup"><span data-stu-id="93958-123">When the MDA is activated, it provides the type name of the delegate.</span></span> <span data-ttu-id="93958-124">Kodunuz için platform çağırma arama ya da bu temsilciyi yönetilmeyen koda geçirebilirsiniz COM imzaları bu adı kullanın.</span><span class="sxs-lookup"><span data-stu-id="93958-124">Use this name to search your code for platform invoke or COM signatures that pass that delegate out to unmanaged code.</span></span> <span data-ttu-id="93958-125">Bunlardan biri geçirilir sorunlu temsilci çağrı siteleri.</span><span class="sxs-lookup"><span data-stu-id="93958-125">The offending delegate is passed out through one of these call sites.</span></span> <span data-ttu-id="93958-126">Ayrıca etkinleştirebilirsiniz `gcUnmanagedToManaged` zamanına her geri çağırma önce bir Çöp toplamayı zorlamak için MDA.</span><span class="sxs-lookup"><span data-stu-id="93958-126">You can also enable the `gcUnmanagedToManaged` MDA to force a garbage collection before every callback into the runtime.</span></span> <span data-ttu-id="93958-127">Bu geri çağırma önce her zaman bir çöp toplama oluşan sağlayarak çöp toplama tarafından tanıtılan belirsizlik kaldırır.</span><span class="sxs-lookup"><span data-stu-id="93958-127">This will remove the uncertainty introduced by the garbage collection by ensuring that a garbage collection always occurs before the callback.</span></span> <span data-ttu-id="93958-128">Hangi temsilci toplanan öğrendikten sonra bu temsilci bir başvuru yönetilen tarafında sıralanmış yönetilmeyen işlev işaretçisi ömrü boyunca saklamak için kodunuzu değiştirin.</span><span class="sxs-lookup"><span data-stu-id="93958-128">Once you know what delegate was collected, change your code to keep a reference to that delegate on the managed side for the lifetime of the marshaled unmanaged function pointer.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="93958-129">Çalışma zamanı üzerindeki etkisi</span><span class="sxs-lookup"><span data-stu-id="93958-129">Effect on the Runtime</span></span>  
 <span data-ttu-id="93958-130">İşlev işaretçileri olarak temsilciler başvuruya çalışma zamanı yönetilmeyen yönetilene geçiş yapan bir dönüştürücü ayırır.</span><span class="sxs-lookup"><span data-stu-id="93958-130">When delegates are marshaled as function pointers, the runtime allocates a thunk that does the transition from unmanaged to managed.</span></span> <span data-ttu-id="93958-131">Bu dönüştürücü ne yönetilmeyen kod gerçekten yönetilen önce çağırır olan temsilci son çağrılır.</span><span class="sxs-lookup"><span data-stu-id="93958-131">This thunk is what the unmanaged code actually calls before the managed delegate is finally invoked.</span></span> <span data-ttu-id="93958-132">Olmadan `callbackOnCollectedDelegate` MDA etkin, temsilci toplanan yönetilmeyen sıralama kodu silinir.</span><span class="sxs-lookup"><span data-stu-id="93958-132">Without the `callbackOnCollectedDelegate` MDA enabled, the unmanaged marshaling code is deleted when the delegate is collected.</span></span> <span data-ttu-id="93958-133">İle `callbackOnCollectedDelegate` MDA etkin, temsilci toplanan olduğunda yönetilmeyen sıralama kodu hemen silinmez.</span><span class="sxs-lookup"><span data-stu-id="93958-133">With the `callbackOnCollectedDelegate` MDA enabled, the unmanaged marshaling code is not immediately deleted when the delegate is collected.</span></span> <span data-ttu-id="93958-134">Bunun yerine, en son 1.000 örnekleri varsayılan olarak Canlı tutulur ve çağrıldığında MDA etkinleştirmek için değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="93958-134">Instead, the last 1,000 instances are kept alive by default and changed to activate the MDA when called.</span></span> <span data-ttu-id="93958-135">Dönüştürücü, sonunda 1,001 daha sıralanmış temsilciler toplanan sonra silinir.</span><span class="sxs-lookup"><span data-stu-id="93958-135">The thunk is eventually deleted after 1,001 more marshaled delegates are collected.</span></span>  
  
## <a name="output"></a><span data-ttu-id="93958-136">Çıkış</span><span class="sxs-lookup"><span data-stu-id="93958-136">Output</span></span>  
 <span data-ttu-id="93958-137">MDA, bir geri çağırma girişiminde bulunuldu önce kendi yönetilmeyen işlev işaretçisini toplanan temsilci türü adını bildirir.</span><span class="sxs-lookup"><span data-stu-id="93958-137">The MDA reports the type name of the delegate that was collected before a callback was attempted on its unmanaged function pointer.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="93958-138">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="93958-138">Configuration</span></span>  
 <span data-ttu-id="93958-139">Aşağıdaki örnek, uygulama yapılandırma seçeneklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="93958-139">The following example shows the application configuration options.</span></span> <span data-ttu-id="93958-140">Dönüştürücüler 1,500 için MDA etkin tutar sayısını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="93958-140">It sets the number of thunks the MDA keeps alive to 1,500.</span></span> <span data-ttu-id="93958-141">Varsayılan `listSize` 2.000 en yüksek değer değer 1000'dir ve en az 50'dir.</span><span class="sxs-lookup"><span data-stu-id="93958-141">The default `listSize` value is 1,000, the minimum is 50, and the maximum is 2,000.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <callbackOnCollectedDelegate listSize="1500" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="93958-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="93958-142">Example</span></span>  
 <span data-ttu-id="93958-143">Aşağıdaki örnek, bu mda'nın etkinleştirebilirsiniz bir durumu gösterir:</span><span class="sxs-lookup"><span data-stu-id="93958-143">The following example demonstrates a situation that can activate this MDA:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="93958-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="93958-144">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="93958-145">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="93958-145">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="93958-146">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="93958-146">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
- [<span data-ttu-id="93958-147">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="93958-147">gcUnmanagedToManaged</span></span>](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)
