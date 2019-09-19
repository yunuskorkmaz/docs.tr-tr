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
# <a name="reentrancy-mda"></a>yeniden giriş MDA'sı
Yönetilen `reentrancy` hata ayıklama Yardımcısı (MDA), yönetilen ve yerel koddan önceki bir geçişin düzenli bir geçiş aracılığıyla gerçekleştirilmediği durumlarda yerelden yönetilen koda geçişe yönelik bir girişim yapıldığında etkinleştirilir.  
  
## <a name="symptoms"></a>Belirtiler  
 Nesne yığını bozulmuş ya da yerelden yönetilen koda geçiş yaparken diğer önemli hatalar oluşuyor.  
  
 Her iki yönde de yerel ve yönetilen kod arasında geçiş yapan iş parçacıklarının düzenli bir geçiş gerçekleştirmesi gerekir. Ancak, Vektörlü özel durum işleyicisi gibi işletim sisteminde bulunan bazı alt düzey genişletilebilirlik noktaları, düzenli bir geçiş gerçekleştirmeden yerel koda geçiş yapmasına izin verir.  Bu anahtarlar, ortak dil çalışma zamanı (CLR) denetimi altında değil, işletim sistemi denetimi altındadır.  Bu genişletilebilirlik noktaları içinde yürütülen herhangi bir yerel kod, yönetilen koda geri çağırma yapmaktan kaçınmalıdır.  
  
## <a name="cause"></a>Sebep  
 Vektörlü özel durum işleyicisi gibi alt düzey bir işletim sistemi genişletilebilirlik noktası, yönetilen kod yürütülürken etkinleştirilmiştir.  Bu genişletilebilirlik noktasından çağrılan uygulama kodu, yönetilen koda geri çağırmaya çalışıyor.  
  
 Bu sorun her zaman uygulama kodundan kaynaklanır.  
  
## <a name="resolution"></a>Çözüm  
 Bu MDA ' i etkinleştiren iş parçacığı için yığın izlemesini inceleyin.  İş parçacığı yönetilen koda geçersiz şekilde çağrı yapmaya çalışıyor.  Yığın izlemesi bu genişletilebilirlik noktasını, bu genişletilebilirlik noktasını sağlayan işletim sistemi kodunu ve genişletilebilirlik noktası tarafından kesintiye uğramış yönetilen kodu kullanarak uygulama kodunu açığa çıkarmalıdır.  
  
 Örneğin, bir vektör özel durum işleyicisinin içinden yönetilen kodu çağırma girişiminde, MDA ' nin etkinleştirilmesini görürsünüz.  Yığında, işletim sistemi özel durum işleme kodunu ve bir <xref:System.DivideByZeroException> <xref:System.AccessViolationException>veya gibi özel durumu tetikleyen bazı yönetilen kodları görürsünüz.  
  
 Bu örnekte, doğru çözüm, Vektörlü özel durum işleyicisini yönetilmeyen kodda tamamen uygulamaktır.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bu MDA, CLR üzerinde hiçbir etkisi yoktur.  
  
## <a name="output"></a>Çıkış  
 Geçersiz yeniden giriş yapmaya yönelik MDA raporları denenmekte.  Bunun neden olduğunu ve sorunun nasıl düzeltilacağını öğrenmek için iş parçacığının yığınını inceleyin. Örnek çıktı aşağıda verilmiştir.  
  
```output
Additional Information: Attempting to call into managed code without   
transitioning out first.  Do not attempt to run managed code inside   
low-level native extensibility points. Managed Debugging Assistant   
'Reentrancy' has detected a problem in 'D:\ConsoleApplication1\  
ConsoleApplication1\bin\Debug\ConsoleApplication1.vshost.exe'.  
```  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reentrancy />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği bir <xref:System.AccessViolationException> oluşturulmasına neden olur.  Vektörlü özel durum işlemeyi destekleyen Windows sürümlerinde, bu, yönetilen Vektörlü özel durum işleyicisinin çağrılmasına neden olur.  Mda etkin ise, işletim sisteminin Vektörlü özel durum işleme desteği kodundan ' a `MyHandler` yapılan çağrı sırasında MDA etkinleştirilir. `reentrancy`  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](diagnosing-errors-with-managed-debugging-assistants.md)
