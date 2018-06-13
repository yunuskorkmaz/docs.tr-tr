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
ms.openlocfilehash: 0aa9ecd357a192eba64cc14f8940b264461b5e74
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33356363"
---
# <a name="callbackoncollecteddelegate-mda"></a><span data-ttu-id="f4362-102">callbackOnCollectedDelegate MDA</span><span class="sxs-lookup"><span data-stu-id="f4362-102">callbackOnCollectedDelegate MDA</span></span>
<span data-ttu-id="f4362-103">`callbackOnCollectedDelegate` Yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilmiş bir temsilci gelen bir işlev işaretçisi olarak yönetilmeyen kod için yönetilen sıralanmış olduğundan ve temsilci toplanacak sağlandıktan sonra bir geri çağırma bu işlev işaretçisi yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="f4362-103">The `callbackOnCollectedDelegate` managed debugging assistant (MDA) is activated if a delegate is marshaled from managed to unmanaged code as a function pointer and a callback is placed on that function pointer after the delegate has been garbage collected.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="f4362-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="f4362-104">Symptoms</span></span>  
 <span data-ttu-id="f4362-105">Yönetilen temsilciler koleksiyonundan edinilen işlev işaretçileri aracılığıyla yönetilen koda çağrı girişimi erişim ihlalleri oluşur.</span><span class="sxs-lookup"><span data-stu-id="f4362-105">Access violations occur when attempting to call into managed code through function pointers that were obtained from managed delegates.</span></span> <span data-ttu-id="f4362-106">Olmayan ortak dil çalışma zamanı (CLR) hataları sırasında bu hataları, erişim ihlali CLR kodunda oluştuğundan bunu görünebilir.</span><span class="sxs-lookup"><span data-stu-id="f4362-106">These failures, while not common language runtime (CLR) bugs, may appear to be so because the access violation occurs in the CLR code.</span></span>  
  
 <span data-ttu-id="f4362-107">Hata tutarlı değil; Bazen işlev işaretçisi çağrıda başarılı ve bazen başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="f4362-107">The failure is not consistent; sometimes the call on the function pointer succeeds and sometimes it fails.</span></span> <span data-ttu-id="f4362-108">Hata, ağır yük altında yalnızca veya rastgele bir deneme sayısı ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="f4362-108">The failure might occur only under heavy load or on a random number of attempts.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="f4362-109">Sebep</span><span class="sxs-lookup"><span data-stu-id="f4362-109">Cause</span></span>  
 <span data-ttu-id="f4362-110">Hangi işlev işaretçisi oluşturuldu ve yönetilmeyen kodundaki temsilci toplanacak oluştu.</span><span class="sxs-lookup"><span data-stu-id="f4362-110">The delegate from which the function pointer was created and exposed to unmanaged code was garbage collected.</span></span> <span data-ttu-id="f4362-111">İşlev işaretçisi çağırmak yönetilmeyen bileşen çalıştığında, erişim ihlali oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f4362-111">When the unmanaged component tries to call on the function pointer, it generates an access violation.</span></span>  
  
 <span data-ttu-id="f4362-112">Çöp toplama oluştuğunda bağımlı olduğundan dolayı başarısız rastgele görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f4362-112">The failure appears random because it depends on when garbage collection occurs.</span></span> <span data-ttu-id="f4362-113">Koleksiyon için bir temsilci uygunsa, çağrı başarılı ve atık toplama sonra geri çağırma oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="f4362-113">If a delegate is eligible for collection, the garbage collection can occur after the callback and the call succeeds.</span></span> <span data-ttu-id="f4362-114">Diğer saatlerde atık toplama önce geri çağırma işlemi gerçekleştiğinde, erişim ihlali geri çağırma oluşturur ve programı durdurur.</span><span class="sxs-lookup"><span data-stu-id="f4362-114">At other times, the garbage collection occurs before the callback, the callback generates an access violation, and the program stops.</span></span>  
  
 <span data-ttu-id="f4362-115">Temsilci ile geri çağırma işlevi işaretçisi yanı sıra çöp koleksiyonları sıklığını hazırlama arasında geçen zamanı hata olasılığını bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="f4362-115">The probability of the failure depends on the time between marshaling the delegate and the callback on the function pointer as well as the frequency of garbage collections.</span></span> <span data-ttu-id="f4362-116">Temsilci ve olmadığını geri çağırma hazırlama arasında geçen zamanı kısaysa durumlarıyla hatasıdır.</span><span class="sxs-lookup"><span data-stu-id="f4362-116">The failure is sporadic if the time between marshaling the delegate and the ensuing callback is short.</span></span> <span data-ttu-id="f4362-117">Bu genellikle işlev işaretçisi alma yönetilmeyen yöntemi, daha sonra kullanmak için işlev işaretçisi kaydetmez ancak bunun yerine geri dönmeden önce bu işlemi hemen tamamlamak için işlev işaretçisi çağırır karşılaşılan bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="f4362-117">This is usually the case if the unmanaged method receiving the function pointer does not save the function pointer for later use but instead calls back on the function pointer immediately to complete its operation before returning.</span></span> <span data-ttu-id="f4362-118">Bir sistem büyük olasılıkla çöp toplama önce geri dönüş meydana gelmez kolaylaştırır ağır yük altında benzer şekilde, daha fazla çöp koleksiyonlarının meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="f4362-118">Similarly, more garbage collections occur when a system is under heavy load, which makes it more likely that a garbage collection will occur before the callback.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="f4362-119">Çözüm</span><span class="sxs-lookup"><span data-stu-id="f4362-119">Resolution</span></span>  
 <span data-ttu-id="f4362-120">Bir temsilci çıkışı bir yönetilmeyen işlev işaretçisi sıralanmış sonra atık toplayıcı yaşam izleyemez.</span><span class="sxs-lookup"><span data-stu-id="f4362-120">Once a delegate has been marshaled out as an unmanaged function pointer, the garbage collector cannot track its lifetime.</span></span> <span data-ttu-id="f4362-121">Bunun yerine, kodunuzu temsilci başvuru yönetilmeyen işlev işaretçisi ömrü boyunca tutmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f4362-121">Instead, your code must keep a reference to the delegate for the lifetime of the unmanaged function pointer.</span></span> <span data-ttu-id="f4362-122">Ancak bunu yapmadan önce ilk olarak hangi temsilci toplanan belirlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f4362-122">But before you can do that, you first must identify which delegate was collected.</span></span> <span data-ttu-id="f4362-123">MDA etkinleştirildiğinde temsilci türü adını sağlar.</span><span class="sxs-lookup"><span data-stu-id="f4362-123">When the MDA is activated, it provides the type name of the delegate.</span></span> <span data-ttu-id="f4362-124">Kodunuz için platform çağırma arama ya da bu temsilciyi yönetilmeyen koda geçirme COM imzaları bu adı kullanın.</span><span class="sxs-lookup"><span data-stu-id="f4362-124">Use this name to search your code for platform invoke or COM signatures that pass that delegate out to unmanaged code.</span></span> <span data-ttu-id="f4362-125">Sorunlu temsilci bunlardan birini geçirilen çağırma siteleri.</span><span class="sxs-lookup"><span data-stu-id="f4362-125">The offending delegate is passed out through one of these call sites.</span></span> <span data-ttu-id="f4362-126">Etkinleştirebilirsiniz `gcUnmanagedToManaged` MDA her geri çağırma önce çöp toplama çalışma zamanı içine zorla.</span><span class="sxs-lookup"><span data-stu-id="f4362-126">You can also enable the `gcUnmanagedToManaged` MDA to force a garbage collection before every callback into the runtime.</span></span> <span data-ttu-id="f4362-127">Bu geri çağırma önce her zaman bir atık toplama oluşan sağlayarak atık toplama tarafından sunulan belirsizlik kaldırır.</span><span class="sxs-lookup"><span data-stu-id="f4362-127">This will remove the uncertainty introduced by the garbage collection by ensuring that a garbage collection always occurs before the callback.</span></span> <span data-ttu-id="f4362-128">Hangi temsilci toplanan öğrendikten sonra bu temsilciyi başvuru yönetilen tarafında sıralanmış yönetilmeyen işlev işaretçisi ömrü boyunca tutmak için kodunuzu değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f4362-128">Once you know what delegate was collected, change your code to keep a reference to that delegate on the managed side for the lifetime of the marshaled unmanaged function pointer.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="f4362-129">Çalışma zamanı etkisi</span><span class="sxs-lookup"><span data-stu-id="f4362-129">Effect on the Runtime</span></span>  
 <span data-ttu-id="f4362-130">Temsilciler işlev işaretçileri sıralanmış, çalışma zamanı yönetilmeyenden yönetilene geçiş yapan bir dönüştürücü ayırır.</span><span class="sxs-lookup"><span data-stu-id="f4362-130">When delegates are marshaled as function pointers, the runtime allocates a thunk that does the transition from unmanaged to managed.</span></span> <span data-ttu-id="f4362-131">Bu dönüştürücü ne yönetilmeyen kod gerçekte yönetilen önce çağırır olan temsilci son olarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="f4362-131">This thunk is what the unmanaged code actually calls before the managed delegate is finally invoked.</span></span> <span data-ttu-id="f4362-132">Olmadan `callbackOnCollectedDelegate` MDA etkin, temsilci toplanan olduğunda yönetilmeyen hazırlama kod silinir.</span><span class="sxs-lookup"><span data-stu-id="f4362-132">Without the `callbackOnCollectedDelegate` MDA enabled, the unmanaged marshaling code is deleted when the delegate is collected.</span></span> <span data-ttu-id="f4362-133">İle `callbackOnCollectedDelegate` MDA etkin, temsilci toplanan olduğunda yönetilmeyen hazırlama kod hemen silinmez.</span><span class="sxs-lookup"><span data-stu-id="f4362-133">With the `callbackOnCollectedDelegate` MDA enabled, the unmanaged marshaling code is not immediately deleted when the delegate is collected.</span></span> <span data-ttu-id="f4362-134">Bunun yerine, en son 1.000 örnekleri varsayılan olarak Canlı tutulur ve çağrıldığında MDA etkinleştirmek için değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="f4362-134">Instead, the last 1,000 instances are kept alive by default and changed to activate the MDA when called.</span></span> <span data-ttu-id="f4362-135">1,001 daha sıralanmış temsilciler toplanan sonra dönüştürücü sonunda silinir.</span><span class="sxs-lookup"><span data-stu-id="f4362-135">The thunk is eventually deleted after 1,001 more marshaled delegates are collected.</span></span>  
  
## <a name="output"></a><span data-ttu-id="f4362-136">Çıkış</span><span class="sxs-lookup"><span data-stu-id="f4362-136">Output</span></span>  
 <span data-ttu-id="f4362-137">MDA bir geri çağırma denendi önce kendi yönetilmeyen işlev işaretçisi toplanan temsilci tür adını bildirir.</span><span class="sxs-lookup"><span data-stu-id="f4362-137">The MDA reports the type name of the delegate that was collected before a callback was attempted on its unmanaged function pointer.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="f4362-138">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f4362-138">Configuration</span></span>  
 <span data-ttu-id="f4362-139">Aşağıdaki örnek uygulama yapılandırma seçeneklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4362-139">The following example shows the application configuration options.</span></span> <span data-ttu-id="f4362-140">MDA 1.500 için etkin tutar dönüştürücüler sayısını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f4362-140">It sets the number of thunks the MDA keeps alive to 1,500.</span></span> <span data-ttu-id="f4362-141">Varsayılan `listSize` değerdir 1.000, en az 50'dir ve 2.000 en yüksek değer.</span><span class="sxs-lookup"><span data-stu-id="f4362-141">The default `listSize` value is 1,000, the minimum is 50, and the maximum is 2,000.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <callbackOnCollectedDelegate listSize="1500" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="f4362-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="f4362-142">Example</span></span>  
 <span data-ttu-id="f4362-143">Aşağıdaki örnek, bu MDA etkinleştirebilirsiniz bir durumu gösterir:</span><span class="sxs-lookup"><span data-stu-id="f4362-143">The following example demonstrates a situation that can activate this MDA:</span></span>  
  
```  
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
// ---------------------------------------------------  
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
  
## <a name="see-also"></a><span data-ttu-id="f4362-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f4362-144">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="f4362-145">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="f4362-145">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="f4362-146">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="f4362-146">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)  
 [<span data-ttu-id="f4362-147">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="f4362-147">gcUnmanagedToManaged</span></span>](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)
