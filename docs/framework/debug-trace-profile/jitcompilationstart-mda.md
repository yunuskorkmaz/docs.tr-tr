---
title: Jıtcompilationstart yönetilen hata ayıklama Yardımcısı (MDA)
description: Tam zamanında (JıT) derleyici bir .NET işlevini derlemeye başladığında, Jıtcompilationstart yönetilen hata ayıklama Yardımcısı (MDA) raporları.
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compilation
- MDAs (managed debugging assistants), JIT compilation
- JitCompilationStart MDA
- managed debugging assistants (MDAs), JIT compilation
ms.assetid: 5ffd2857-d0ba-4342-9824-9ffe04ec135d
ms.openlocfilehash: 13e20c1a940b7bfa777245ba35f3cc1b003d15b2
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325527"
---
# <a name="jitcompilationstart-mda"></a>jitCompilationStart MDA

`jitCompilationStart`Yönetilen hata ayıklama Yardımcısı (MDA), Just-In-Time (JIT) derleyicisi bir işlevi derlemeye başladığında raporlamak için etkinleştirilir.  
  
## <a name="symptoms"></a>Belirtiler  
 Çalışma kümesi boyutu, zaten yerel görüntü biçiminde olan bir program için artar, çünkü mscorjit.dll işleme yüklenir.  
  
## <a name="cause"></a>Nedeni  
Programın bağımlı olduğu tüm derlemeler yerel biçimde üretilmez veya bir derleme doğru şekilde kaydedilmemiş.  

## <a name="resolution"></a>Çözüm  
 Bu MDA ' ın etkinleştirilmesi, hangi işlevin JıT olarak derlendiğini tanımlamanızı sağlar. İşlevi içeren derlemenin yerel biçimde oluşturulduğundan ve doğru şekilde kaydedildiğinden emin olun.
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bu MDA, bir yöntem JıT derlenmeden hemen önce bir ileti günlüğe kaydedilir, bu nedenle bu MDA 'ın etkinleştirilmesi performansı önemli ölçüde etkiler. Bir yöntem satır içi ise, bu MDA ayrı bir ileti oluşturmaz.  
  
## <a name="output"></a>Çıkış  
 Aşağıdaki kod örneği, örnek çıktıyı gösterir. Bu durumda, çıkış, derleme testinde, "ns2.CO" sınıfındaki "d" yönteminin JıT olarak derlendiğini gösterir.  
  
```output
method name="Test!ns2.C0::m"  
```  
  
## <a name="configuration"></a>Yapılandırma  
 Aşağıdaki yapılandırma dosyasında, ilk JıT derlenmiş olduğunda hangi yöntemlerin raporlanacağı filtreleneceği için kullanılabilecek çeşitli filtreler gösterilmektedir. Ad özniteliğinin değerini olarak ayarlayarak tüm yöntemlerin rapor olduğunu belirtebilirsiniz \* .  
  
```xml  
<mdaConfig>  
  <assistants>  
    <jitCompilationStart>  
      <methods>  
        <match name="C0::m" />  
        <match name="MyMethod" />  
        <match name="C2::*" />  
        <match name="ns0::*" />  
        <match name="ns1.C0::*" />  
        <match name="ns2.C0::m" />  
        <match name="ns2.C0+N0::m" />  
      </methods>  
    </jitCompilationStart >  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, önceki yapılandırma dosyası ile kullanılmak üzere tasarlanmıştır.  
  
```csharp
using System;  
using System.Reflection;  
using System.Runtime.CompilerServices;  
using System.Runtime.InteropServices;  
  
public class Entry  
{  
    public static void Main(string[] args)  
    {  
        C0.m();  
        C1.MyMethod();  
        C2.m();  
  
        ns0.C0.m();  
        ns0.C0.N0.m();  
        ns0.C1.m();  
  
        ns1.C0.m();  
        ns1.C0.N0.m();  
  
        ns2.C0.m();  
        ns2.C0.N0.m();  
    }  
}  
  
public class C0  
{  
    [MethodImpl(MethodImplOptions.NoInlining)]  
    public static void m() { }  
}  
  
public class C1  
{  
    [MethodImpl(MethodImplOptions.NoInlining)]  
    public static void MyMethod() { }  
}  
  
public class C2  
{  
    [MethodImpl(MethodImplOptions.NoInlining)]  
    public static void m() { }  
}  
  
namespace ns0  
{  
    public class C0  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
  
        public class N0  
        {  
            [MethodImpl(MethodImplOptions.NoInlining)]  
            public static void m() { }  
        }  
    }  
  
    public class C1  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
    }  
}  
  
namespace ns1  
{  
    public class C0  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
        public class N0  
        {  
            [MethodImpl(MethodImplOptions.NoInlining)]  
            public static void m() { }  
        }  
    }  
}  
  
namespace ns2  
{  
    public class C0  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
  
        public class N0  
        {  
            [MethodImpl(MethodImplOptions.NoInlining)]  
            public static void m() { }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](diagnosing-errors-with-managed-debugging-assistants.md)
- [Birlikte Çalışma Hazırlama](../interop/interop-marshaling.md)
