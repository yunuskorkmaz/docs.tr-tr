---
title: "yeniden giriş MDA'sı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a305658068e6d59f27957879c053b18742ea642f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="reentrancy-mda"></a><span data-ttu-id="a33e6-102">yeniden giriş MDA'sı</span><span class="sxs-lookup"><span data-stu-id="a33e6-102">reentrancy MDA</span></span>
<span data-ttu-id="a33e6-103">`reentrancy` Yönetilen hata ayıklama Yardımcısı (MDA) girişiminde durumlarda burada yerel için yönetilen kod önceki anahtardan gerçekleştirilmediği düzenli geçiş yönetilen kod Yerelden geçiş yapılırken etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="a33e6-103">The `reentrancy` managed debugging assistant (MDA) is activated when an attempt is made to transition from native to managed code in cases where a prior switch from managed to native code was not performed through an orderly transition.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="a33e6-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="a33e6-104">Symptoms</span></span>  
 <span data-ttu-id="a33e6-105">Nesne yığın bozulmuş veya diğer ciddi hatalar yönetilen kod Yerelden geçiş olduğunda ortaya çıkan.</span><span class="sxs-lookup"><span data-stu-id="a33e6-105">The object heap is corrupted or other serious errors are occurring when transitioning from native to managed code.</span></span>  
  
 <span data-ttu-id="a33e6-106">Her iki yönde yerel ve yönetilen kod arasında geçiş iş parçacığı düzenli geçiş gerçekleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a33e6-106">Threads that switch between native and managed code in either direction must perform an orderly transition.</span></span> <span data-ttu-id="a33e6-107">Ancak, belirli alt düzey genişletilebilirlik noktaları Vektörlü özel durum işleyici gibi işletim sistemi yerel koda düzenli geçiş yapmadan yönetilen anahtarlardan izin verir.</span><span class="sxs-lookup"><span data-stu-id="a33e6-107">However, certain low-level extensibility points in the operating system, such as the vectored exception handler, allow switches from managed to native code without performing an orderly transition.</span></span>  <span data-ttu-id="a33e6-108">Bu anahtarlar, işletim sistemi denetimindeki yerine, ortak dil çalışma zamanı (CLR) denetimi altında şunlardır.</span><span class="sxs-lookup"><span data-stu-id="a33e6-108">These switches are under operating system control, rather than under common language runtime (CLR) control.</span></span>  <span data-ttu-id="a33e6-109">Bu genişletilebilirlik noktaları içinde yürüten yerel kod yönetilen kodu geri çağırma kaçınmalısınız.</span><span class="sxs-lookup"><span data-stu-id="a33e6-109">Any native code that executes inside these extensibility points must avoid calling back into managed code.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="a33e6-110">Sebep</span><span class="sxs-lookup"><span data-stu-id="a33e6-110">Cause</span></span>  
 <span data-ttu-id="a33e6-111">Yönetilen kod yürütülürken Vektörlü özel durum işleyici gibi bir alt düzey işletim sistemi genişletilebilirlik noktası etkinleştirdi.</span><span class="sxs-lookup"><span data-stu-id="a33e6-111">A low-level operating system extensibility point, such as the vectored exception handler, has activated while executing managed code.</span></span>  <span data-ttu-id="a33e6-112">Bu genişletilebilirlik noktası aracılığıyla çağrılır uygulama kodu geri yönetilen koda çağrı çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="a33e6-112">The application code that is invoked through that extensibility point is attempting to call back into managed code.</span></span>  
  
 <span data-ttu-id="a33e6-113">Bu sorun uygulama kodu tarafından her zaman kaynaklanır.</span><span class="sxs-lookup"><span data-stu-id="a33e6-113">This problem is always caused by application code.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="a33e6-114">Çözüm</span><span class="sxs-lookup"><span data-stu-id="a33e6-114">Resolution</span></span>  
 <span data-ttu-id="a33e6-115">Bu MDA etkinleştirdi iş parçacığı için yığın izlemesi inceleyin.</span><span class="sxs-lookup"><span data-stu-id="a33e6-115">Examine the stack trace for the thread that has activated this MDA.</span></span>  <span data-ttu-id="a33e6-116">İş parçacığı yasadışı yönetilen koda çağrı çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="a33e6-116">The thread is attempting to illegally call into managed code.</span></span>  <span data-ttu-id="a33e6-117">Yığın izleme, bu genişletilebilirlik noktasını kullanarak uygulama kodu, bu genişletilebilirlik noktasıdır işletim sistemi kodu ve genişletilebilirlik noktası tarafından kesildi yönetilen kod ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="a33e6-117">The stack trace should reveal the application code using this extensibility point, the operating system code that provides this extensibility point, and the managed code that was interrupted by the extensibility point.</span></span>  
  
 <span data-ttu-id="a33e6-118">Örneğin, yönetilen koddan Vektörlü özel durum işleyicisi içine çağrı girişimi etkinleştirilmiş MDA görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="a33e6-118">For example, you will see the MDA activated in an attempt to call managed code from inside a vectored exception handler.</span></span>  <span data-ttu-id="a33e6-119">İşletim sistemi özel durum kodu ve bir özel durum harekete gibi bazı yönetilen kod işleme göreceğiniz yığında bir <xref:System.DivideByZeroException> veya bir <xref:System.AccessViolationException>.</span><span class="sxs-lookup"><span data-stu-id="a33e6-119">On the stack you will see the operating system exception handling code and some managed code triggering an exception such as a <xref:System.DivideByZeroException> or an <xref:System.AccessViolationException>.</span></span>  
  
 <span data-ttu-id="a33e6-120">Bu örnekte, doğru çözünürlüğü Vektörlü özel durum işleyici tamamen yönetilmeyen kodunda uygulamaktır.</span><span class="sxs-lookup"><span data-stu-id="a33e6-120">In this example, the correct resolution is to implement the vectored exception handler completely in unmanaged code.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="a33e6-121">Çalışma zamanı etkisi</span><span class="sxs-lookup"><span data-stu-id="a33e6-121">Effect on the Runtime</span></span>  
 <span data-ttu-id="a33e6-122">Bu MDA CLR üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="a33e6-122">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="a33e6-123">Çıkış</span><span class="sxs-lookup"><span data-stu-id="a33e6-123">Output</span></span>  
 <span data-ttu-id="a33e6-124">Geçersiz yeniden giriş yapılmaya çalışılan MDA bildirir.</span><span class="sxs-lookup"><span data-stu-id="a33e6-124">The MDA reports that illegal reentrancy is being attempted.</span></span>  <span data-ttu-id="a33e6-125">Bu neden olmuyor ve sorunun nasıl giderileceği belirlemek için iş parçacığının yığın inceleyin.</span><span class="sxs-lookup"><span data-stu-id="a33e6-125">Examine the thread's stack to determine why this is happening and how to correct the problem.</span></span> <span data-ttu-id="a33e6-126">Örnek çıktı verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a33e6-126">The following is sample output.</span></span>  
  
```  
Additional Information: Attempting to call into managed code without   
transitioning out first.  Do not attempt to run managed code inside   
low-level native extensibility points. Managed Debugging Assistant   
'Reentrancy' has detected a problem in 'D:\ConsoleApplication1\  
ConsoleApplication1\bin\Debug\ConsoleApplication1.vshost.exe'.  
```  
  
## <a name="configuration"></a><span data-ttu-id="a33e6-127">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a33e6-127">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reentrancy />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="a33e6-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="a33e6-128">Example</span></span>  
 <span data-ttu-id="a33e6-129">Aşağıdaki kod örneği neden bir <xref:System.AccessViolationException> oluşturulmasına.</span><span class="sxs-lookup"><span data-stu-id="a33e6-129">The following code example causes an <xref:System.AccessViolationException> to be thrown.</span></span>  <span data-ttu-id="a33e6-130">Vektörlü özel durum işleme destekleyen Windows sürümlerinde bu çağrılacak yönetilen Vektörlü özel durum işleyici neden olur.</span><span class="sxs-lookup"><span data-stu-id="a33e6-130">On versions of Windows that support vectored exception handling, this will cause the managed vectored exception handler to be called.</span></span>  <span data-ttu-id="a33e6-131">Varsa `reentrancy` MDA etkinleştirildiğinde, MDA denenen çağrı sırasında etkinleşir `MyHandler` destek kod işleme işletim sisteminin Vektörlü özel durum.</span><span class="sxs-lookup"><span data-stu-id="a33e6-131">If the `reentrancy` MDA is enabled, the MDA will activate during the attempted call to `MyHandler` from the operating system's vectored exception handling support code.</span></span>  
  
```  
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
  
## <a name="see-also"></a><span data-ttu-id="a33e6-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a33e6-132">See Also</span></span>  
 [<span data-ttu-id="a33e6-133">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="a33e6-133">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
