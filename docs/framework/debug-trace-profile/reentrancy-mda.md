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
# <a name="reentrancy-mda"></a>yeniden giriş MDA'sı
`reentrancy` Yönetilen hata ayıklama yardımcısı (MDA), yönetilen koddan yerel koda önceki bir geçişin düzenli bir geçiş yoluyla gerçekleştirilemediği durumlarda yerel koddan yönetilen koda geçiş girişiminde bulunulduğunda etkinleştirilir.  
  
## <a name="symptoms"></a>Belirtiler  
 Nesne yığını bozuk veya diğer ciddi hatalar yerel koddan yönetilen koda geçiş yaparken oluşur.  
  
 Her iki yönde yerel ve yönetilen kod arasında geçiş yapan iş parçacıkları düzenli bir geçiş gerçekleştirmelidir. Ancak, vektörel özel durum işleyicisi gibi işletim sistemindeki belirli düşük düzeyli genişletilebilirlik noktaları, düzenli bir geçiş gerçekleştirmeden yönetilen koddan yerel koda geçişlere izin verir.  Bu anahtarlar, ortak dil çalışma süresi (CLR) denetimi yerine işletim sistemi denetimi altındadır.  Bu genişletilebilirlik noktaları içinde yürüten herhangi bir yerel kod yönetilen koda geri arama kaçınmalısınız.  
  
## <a name="cause"></a>Nedeni  
 Yönetilen kodu yürütürken, vektörel özel durum işleyicisi gibi düşük düzeyli bir işletim sistemi genişletilebilirlik noktası etkinleştirildi.  Bu genişletilebilirlik noktası üzerinden çağrılan uygulama kodu yönetilen koda geri çağırmak için çalışıyor.  
  
 Bu sorun her zaman uygulama kodu ndan kaynaklanır.  
  
## <a name="resolution"></a>Çözüm  
 Bu MDA'yı etkinleştiren iş parçacığı için yığın izini inceleyin.  İş parçacığı, yönetilen koda yasa dışı olarak çağrı yapmaya çalışıyor.  Yığın izleme bu genişletilebilirlik noktası, bu genişletilebilirlik noktası sağlayan işletim sistemi kodu ve genişletilebilirlik noktası tarafından kesintiye yönetilen kod kullanarak uygulama kodu göstermelidir.  
  
 Örneğin, MDA'nın, yönetilen kodu vektörel bir özel durum işleyicisinin içinden çağırma girişiminde etkinleştirildiğini görürsünüz.  Yığında işletim sistemi özel durum işleme kodu ve bazı yönetilen kod gibi <xref:System.DivideByZeroException> bir <xref:System.AccessViolationException>özel durum tetikleyen göreceksiniz .  
  
 Bu örnekte, doğru çözüm, vektörel özel durum işleyicisini tamamen yönetilmeyen kodda uygulamaktır.  
  
## <a name="effect-on-the-runtime"></a>Çalışma Süresi üzerindeki etkisi  
 Bu MDA'nın CLR üzerinde hiçbir etkisi yoktur.  
  
## <a name="output"></a>Çıktı  
 MDA yasadışı canlandırma girişiminde bulunulmakta olduğunu bildiriyor.  Bunun neden olduğunu ve sorunu nasıl düzelttiğini belirlemek için iş parçacığının yığınını inceleyin. Aşağıda örnek çıktıs› ve  
  
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
 Aşağıdaki kod örneği <xref:System.AccessViolationException> bir atılmasını neden olur.  Windows'un vektörel özel durum işlemeyi destekleyen sürümlerinde, yönetilen vektörel özel durum işleyicisinin çağrılmasını sağlar.  `reentrancy` MDA etkinse, MDA, işletim sisteminin vektörel özel durum işleme destek `MyHandler` kodundan yapılan arama denemesi sırasında etkinleştirilir.  
  
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
