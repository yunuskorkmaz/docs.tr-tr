---
title: yeniden giriş MDA'sı
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged code, debugging
- transitioning threads unmanaged to managed code
- reentrancy MDA
- reentrancy without an orderly transition
- managed debugging assistants (MDAs), reentrancy
- illegal reentrancy
- MDAs (managed debugging assistants), reentrancy
- threading [.NET Framework], managed debugging assistants
- managed code, debugging
- native debugging, MDAs
ms.assetid: 7240c3f3-7df8-4b03-bbf1-17cdce142d45
ms.openlocfilehash: 5cbe8e843ad72785010240f3db30b1d344c80650
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181760"
---
# <a name="reentrancy-mda"></a><span data-ttu-id="ced69-102">yeniden giriş MDA'sı</span><span class="sxs-lookup"><span data-stu-id="ced69-102">reentrancy MDA</span></span>
<span data-ttu-id="ced69-103">`reentrancy` Yönetilen hata ayıklama yardımcısı (MDA), yönetilen koddan yerel koda önceki bir geçişin düzenli bir geçiş yoluyla gerçekleştirilemediği durumlarda yerel koddan yönetilen koda geçiş girişiminde bulunulduğunda etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="ced69-103">The `reentrancy` managed debugging assistant (MDA) is activated when an attempt is made to transition from native to managed code in cases where a prior switch from managed to native code was not performed through an orderly transition.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="ced69-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="ced69-104">Symptoms</span></span>  
 <span data-ttu-id="ced69-105">Nesne yığını bozuk veya diğer ciddi hatalar yerel koddan yönetilen koda geçiş yaparken oluşur.</span><span class="sxs-lookup"><span data-stu-id="ced69-105">The object heap is corrupted or other serious errors are occurring when transitioning from native to managed code.</span></span>  
  
 <span data-ttu-id="ced69-106">Her iki yönde yerel ve yönetilen kod arasında geçiş yapan iş parçacıkları düzenli bir geçiş gerçekleştirmelidir.</span><span class="sxs-lookup"><span data-stu-id="ced69-106">Threads that switch between native and managed code in either direction must perform an orderly transition.</span></span> <span data-ttu-id="ced69-107">Ancak, vektörel özel durum işleyicisi gibi işletim sistemindeki belirli düşük düzeyli genişletilebilirlik noktaları, düzenli bir geçiş gerçekleştirmeden yönetilen koddan yerel koda geçişlere izin verir.</span><span class="sxs-lookup"><span data-stu-id="ced69-107">However, certain low-level extensibility points in the operating system, such as the vectored exception handler, allow switches from managed to native code without performing an orderly transition.</span></span>  <span data-ttu-id="ced69-108">Bu anahtarlar, ortak dil çalışma süresi (CLR) denetimi yerine işletim sistemi denetimi altındadır.</span><span class="sxs-lookup"><span data-stu-id="ced69-108">These switches are under operating system control, rather than under common language runtime (CLR) control.</span></span>  <span data-ttu-id="ced69-109">Bu genişletilebilirlik noktaları içinde yürüten herhangi bir yerel kod yönetilen koda geri arama kaçınmalısınız.</span><span class="sxs-lookup"><span data-stu-id="ced69-109">Any native code that executes inside these extensibility points must avoid calling back into managed code.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="ced69-110">Nedeni</span><span class="sxs-lookup"><span data-stu-id="ced69-110">Cause</span></span>  
 <span data-ttu-id="ced69-111">Yönetilen kodu yürütürken, vektörel özel durum işleyicisi gibi düşük düzeyli bir işletim sistemi genişletilebilirlik noktası etkinleştirildi.</span><span class="sxs-lookup"><span data-stu-id="ced69-111">A low-level operating system extensibility point, such as the vectored exception handler, has activated while executing managed code.</span></span>  <span data-ttu-id="ced69-112">Bu genişletilebilirlik noktası üzerinden çağrılan uygulama kodu yönetilen koda geri çağırmak için çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="ced69-112">The application code that is invoked through that extensibility point is attempting to call back into managed code.</span></span>  
  
 <span data-ttu-id="ced69-113">Bu sorun her zaman uygulama kodu ndan kaynaklanır.</span><span class="sxs-lookup"><span data-stu-id="ced69-113">This problem is always caused by application code.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="ced69-114">Çözüm</span><span class="sxs-lookup"><span data-stu-id="ced69-114">Resolution</span></span>  
 <span data-ttu-id="ced69-115">Bu MDA'yı etkinleştiren iş parçacığı için yığın izini inceleyin.</span><span class="sxs-lookup"><span data-stu-id="ced69-115">Examine the stack trace for the thread that has activated this MDA.</span></span>  <span data-ttu-id="ced69-116">İş parçacığı, yönetilen koda yasa dışı olarak çağrı yapmaya çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="ced69-116">The thread is attempting to illegally call into managed code.</span></span>  <span data-ttu-id="ced69-117">Yığın izleme bu genişletilebilirlik noktası, bu genişletilebilirlik noktası sağlayan işletim sistemi kodu ve genişletilebilirlik noktası tarafından kesintiye yönetilen kod kullanarak uygulama kodu göstermelidir.</span><span class="sxs-lookup"><span data-stu-id="ced69-117">The stack trace should reveal the application code using this extensibility point, the operating system code that provides this extensibility point, and the managed code that was interrupted by the extensibility point.</span></span>  
  
 <span data-ttu-id="ced69-118">Örneğin, MDA'nın, yönetilen kodu vektörel bir özel durum işleyicisinin içinden çağırma girişiminde etkinleştirildiğini görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="ced69-118">For example, you will see the MDA activated in an attempt to call managed code from inside a vectored exception handler.</span></span>  <span data-ttu-id="ced69-119">Yığında işletim sistemi özel durum işleme kodu ve bazı yönetilen kod gibi <xref:System.DivideByZeroException> bir <xref:System.AccessViolationException>özel durum tetikleyen göreceksiniz .</span><span class="sxs-lookup"><span data-stu-id="ced69-119">On the stack you will see the operating system exception handling code and some managed code triggering an exception such as a <xref:System.DivideByZeroException> or an <xref:System.AccessViolationException>.</span></span>  
  
 <span data-ttu-id="ced69-120">Bu örnekte, doğru çözüm, vektörel özel durum işleyicisini tamamen yönetilmeyen kodda uygulamaktır.</span><span class="sxs-lookup"><span data-stu-id="ced69-120">In this example, the correct resolution is to implement the vectored exception handler completely in unmanaged code.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="ced69-121">Çalışma Süresi üzerindeki etkisi</span><span class="sxs-lookup"><span data-stu-id="ced69-121">Effect on the Runtime</span></span>  
 <span data-ttu-id="ced69-122">Bu MDA'nın CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="ced69-122">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="ced69-123">Çıktı</span><span class="sxs-lookup"><span data-stu-id="ced69-123">Output</span></span>  
 <span data-ttu-id="ced69-124">MDA yasadışı canlandırma girişiminde bulunulmakta olduğunu bildiriyor.</span><span class="sxs-lookup"><span data-stu-id="ced69-124">The MDA reports that illegal reentrancy is being attempted.</span></span>  <span data-ttu-id="ced69-125">Bunun neden olduğunu ve sorunu nasıl düzelttiğini belirlemek için iş parçacığının yığınını inceleyin.</span><span class="sxs-lookup"><span data-stu-id="ced69-125">Examine the thread's stack to determine why this is happening and how to correct the problem.</span></span> <span data-ttu-id="ced69-126">Aşağıda örnek çıktıs› ve</span><span class="sxs-lookup"><span data-stu-id="ced69-126">The following is sample output.</span></span>  
  
```output
Additional Information: Attempting to call into managed code without
transitioning out first.  Do not attempt to run managed code inside
low-level native extensibility points. Managed Debugging Assistant
'Reentrancy' has detected a problem in 'D:\ConsoleApplication1\  
ConsoleApplication1\bin\Debug\ConsoleApplication1.vshost.exe'.  
```  
  
## <a name="configuration"></a><span data-ttu-id="ced69-127">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ced69-127">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reentrancy />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="ced69-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="ced69-128">Example</span></span>  
 <span data-ttu-id="ced69-129">Aşağıdaki kod örneği <xref:System.AccessViolationException> bir atılmasını neden olur.</span><span class="sxs-lookup"><span data-stu-id="ced69-129">The following code example causes an <xref:System.AccessViolationException> to be thrown.</span></span>  <span data-ttu-id="ced69-130">Windows'un vektörel özel durum işlemeyi destekleyen sürümlerinde, yönetilen vektörel özel durum işleyicisinin çağrılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="ced69-130">On versions of Windows that support vectored exception handling, this will cause the managed vectored exception handler to be called.</span></span>  <span data-ttu-id="ced69-131">`reentrancy` MDA etkinse, MDA, işletim sisteminin vektörel özel durum işleme destek `MyHandler` kodundan yapılan arama denemesi sırasında etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="ced69-131">If the `reentrancy` MDA is enabled, the MDA will activate during the attempted call to `MyHandler` from the operating system's vectored exception handling support code.</span></span>  
  
```csharp
using System;  
public delegate int ExceptionHandler(IntPtr ptrExceptionInfo);  
  
public class Reenter
{  
    public static ExceptionHandler keepAlive;  
  
    [System.Runtime.InteropServices.DllImport("kernel32", ExactSpelling=true,
        CharSet=System.Runtime.InteropServices.CharSet.Auto)]  
    public static extern IntPtr AddVectoredExceptionHandler(int bFirst,
        ExceptionHandler handler);  
  
    static int MyHandler(IntPtr ptrExceptionInfo)
    {  
        // EXCEPTION_CONTINUE_SEARCH  
        return 0;  
    }  
    void Run() {}  
  
    static void Main()
    {  
        keepAlive = new ExceptionHandler(Reenter.MyHandler);  
        IntPtr ret = AddVectoredExceptionHandler(1, keepAlive);  
        try
        {  
            // Dispatch on null should AV.  
            Reenter r = null;
            r.Run();  
        }
        catch { }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="ced69-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ced69-132">See also</span></span>

- [<span data-ttu-id="ced69-133">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="ced69-133">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
