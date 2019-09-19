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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d14ba8724659172711da44e7bb249e9d20768dbc
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052336"
---
# <a name="reentrancy-mda"></a><span data-ttu-id="9f3d1-102">yeniden giriş MDA'sı</span><span class="sxs-lookup"><span data-stu-id="9f3d1-102">reentrancy MDA</span></span>
<span data-ttu-id="9f3d1-103">Yönetilen `reentrancy` hata ayıklama Yardımcısı (MDA), yönetilen ve yerel koddan önceki bir geçişin düzenli bir geçiş aracılığıyla gerçekleştirilmediği durumlarda yerelden yönetilen koda geçişe yönelik bir girişim yapıldığında etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="9f3d1-103">The `reentrancy` managed debugging assistant (MDA) is activated when an attempt is made to transition from native to managed code in cases where a prior switch from managed to native code was not performed through an orderly transition.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="9f3d1-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="9f3d1-104">Symptoms</span></span>  
 <span data-ttu-id="9f3d1-105">Nesne yığını bozulmuş ya da yerelden yönetilen koda geçiş yaparken diğer önemli hatalar oluşuyor.</span><span class="sxs-lookup"><span data-stu-id="9f3d1-105">The object heap is corrupted or other serious errors are occurring when transitioning from native to managed code.</span></span>  
  
 <span data-ttu-id="9f3d1-106">Her iki yönde de yerel ve yönetilen kod arasında geçiş yapan iş parçacıklarının düzenli bir geçiş gerçekleştirmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="9f3d1-106">Threads that switch between native and managed code in either direction must perform an orderly transition.</span></span> <span data-ttu-id="9f3d1-107">Ancak, Vektörlü özel durum işleyicisi gibi işletim sisteminde bulunan bazı alt düzey genişletilebilirlik noktaları, düzenli bir geçiş gerçekleştirmeden yerel koda geçiş yapmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="9f3d1-107">However, certain low-level extensibility points in the operating system, such as the vectored exception handler, allow switches from managed to native code without performing an orderly transition.</span></span>  <span data-ttu-id="9f3d1-108">Bu anahtarlar, ortak dil çalışma zamanı (CLR) denetimi altında değil, işletim sistemi denetimi altındadır.</span><span class="sxs-lookup"><span data-stu-id="9f3d1-108">These switches are under operating system control, rather than under common language runtime (CLR) control.</span></span>  <span data-ttu-id="9f3d1-109">Bu genişletilebilirlik noktaları içinde yürütülen herhangi bir yerel kod, yönetilen koda geri çağırma yapmaktan kaçınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9f3d1-109">Any native code that executes inside these extensibility points must avoid calling back into managed code.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="9f3d1-110">Sebep</span><span class="sxs-lookup"><span data-stu-id="9f3d1-110">Cause</span></span>  
 <span data-ttu-id="9f3d1-111">Vektörlü özel durum işleyicisi gibi alt düzey bir işletim sistemi genişletilebilirlik noktası, yönetilen kod yürütülürken etkinleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9f3d1-111">A low-level operating system extensibility point, such as the vectored exception handler, has activated while executing managed code.</span></span>  <span data-ttu-id="9f3d1-112">Bu genişletilebilirlik noktasından çağrılan uygulama kodu, yönetilen koda geri çağırmaya çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="9f3d1-112">The application code that is invoked through that extensibility point is attempting to call back into managed code.</span></span>  
  
 <span data-ttu-id="9f3d1-113">Bu sorun her zaman uygulama kodundan kaynaklanır.</span><span class="sxs-lookup"><span data-stu-id="9f3d1-113">This problem is always caused by application code.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="9f3d1-114">Çözüm</span><span class="sxs-lookup"><span data-stu-id="9f3d1-114">Resolution</span></span>  
 <span data-ttu-id="9f3d1-115">Bu MDA ' i etkinleştiren iş parçacığı için yığın izlemesini inceleyin.</span><span class="sxs-lookup"><span data-stu-id="9f3d1-115">Examine the stack trace for the thread that has activated this MDA.</span></span>  <span data-ttu-id="9f3d1-116">İş parçacığı yönetilen koda geçersiz şekilde çağrı yapmaya çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="9f3d1-116">The thread is attempting to illegally call into managed code.</span></span>  <span data-ttu-id="9f3d1-117">Yığın izlemesi bu genişletilebilirlik noktasını, bu genişletilebilirlik noktasını sağlayan işletim sistemi kodunu ve genişletilebilirlik noktası tarafından kesintiye uğramış yönetilen kodu kullanarak uygulama kodunu açığa çıkarmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9f3d1-117">The stack trace should reveal the application code using this extensibility point, the operating system code that provides this extensibility point, and the managed code that was interrupted by the extensibility point.</span></span>  
  
 <span data-ttu-id="9f3d1-118">Örneğin, bir vektör özel durum işleyicisinin içinden yönetilen kodu çağırma girişiminde, MDA ' nin etkinleştirilmesini görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="9f3d1-118">For example, you will see the MDA activated in an attempt to call managed code from inside a vectored exception handler.</span></span>  <span data-ttu-id="9f3d1-119">Yığında, işletim sistemi özel durum işleme kodunu ve bir <xref:System.DivideByZeroException> <xref:System.AccessViolationException>veya gibi özel durumu tetikleyen bazı yönetilen kodları görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="9f3d1-119">On the stack you will see the operating system exception handling code and some managed code triggering an exception such as a <xref:System.DivideByZeroException> or an <xref:System.AccessViolationException>.</span></span>  
  
 <span data-ttu-id="9f3d1-120">Bu örnekte, doğru çözüm, Vektörlü özel durum işleyicisini yönetilmeyen kodda tamamen uygulamaktır.</span><span class="sxs-lookup"><span data-stu-id="9f3d1-120">In this example, the correct resolution is to implement the vectored exception handler completely in unmanaged code.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="9f3d1-121">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="9f3d1-121">Effect on the Runtime</span></span>  
 <span data-ttu-id="9f3d1-122">Bu MDA, CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="9f3d1-122">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="9f3d1-123">Çıkış</span><span class="sxs-lookup"><span data-stu-id="9f3d1-123">Output</span></span>  
 <span data-ttu-id="9f3d1-124">Geçersiz yeniden giriş yapmaya yönelik MDA raporları denenmekte.</span><span class="sxs-lookup"><span data-stu-id="9f3d1-124">The MDA reports that illegal reentrancy is being attempted.</span></span>  <span data-ttu-id="9f3d1-125">Bunun neden olduğunu ve sorunun nasıl düzeltilacağını öğrenmek için iş parçacığının yığınını inceleyin.</span><span class="sxs-lookup"><span data-stu-id="9f3d1-125">Examine the thread's stack to determine why this is happening and how to correct the problem.</span></span> <span data-ttu-id="9f3d1-126">Örnek çıktı aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9f3d1-126">The following is sample output.</span></span>  
  
```output
Additional Information: Attempting to call into managed code without   
transitioning out first.  Do not attempt to run managed code inside   
low-level native extensibility points. Managed Debugging Assistant   
'Reentrancy' has detected a problem in 'D:\ConsoleApplication1\  
ConsoleApplication1\bin\Debug\ConsoleApplication1.vshost.exe'.  
```  
  
## <a name="configuration"></a><span data-ttu-id="9f3d1-127">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="9f3d1-127">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reentrancy />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="9f3d1-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="9f3d1-128">Example</span></span>  
 <span data-ttu-id="9f3d1-129">Aşağıdaki kod örneği bir <xref:System.AccessViolationException> oluşturulmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="9f3d1-129">The following code example causes an <xref:System.AccessViolationException> to be thrown.</span></span>  <span data-ttu-id="9f3d1-130">Vektörlü özel durum işlemeyi destekleyen Windows sürümlerinde, bu, yönetilen Vektörlü özel durum işleyicisinin çağrılmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="9f3d1-130">On versions of Windows that support vectored exception handling, this will cause the managed vectored exception handler to be called.</span></span>  <span data-ttu-id="9f3d1-131">Mda etkin ise, işletim sisteminin Vektörlü özel durum işleme desteği kodundan ' a `MyHandler` yapılan çağrı sırasında MDA etkinleştirilir. `reentrancy`</span><span class="sxs-lookup"><span data-stu-id="9f3d1-131">If the `reentrancy` MDA is enabled, the MDA will activate during the attempted call to `MyHandler` from the operating system's vectored exception handling support code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9f3d1-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f3d1-132">See also</span></span>

- [<span data-ttu-id="9f3d1-133">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="9f3d1-133">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
