---
title: jitCompilationStart MDA
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compilation
- MDAs (managed debugging assistants), JIT compilation
- JitCompilationStart MDA
- managed debugging assistants (MDAs), JIT compilation
ms.assetid: 5ffd2857-d0ba-4342-9824-9ffe04ec135d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d73c299231a588a5ae0b252dd2b5a0a834685f2d
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53150673"
---
# <a name="jitcompilationstart-mda"></a>jitCompilationStart MDA
`jitCompilationStart` Yönetilen hata ayıklama Yardımcısı (MDA), rapora etkinleştirilirse, just-in-time (JIT) derleyici bir işlevi derlemeye yürütülmeye başladığı zaman.  
  
## <a name="symptoms"></a>Belirtiler  
 Çalışan boyutu arttıkça mscorjit.dll işlem içine yüklenmiş olduğundan, yerel görüntü biçiminde olan bir program için ayarlayın.  
  
## <a name="cause"></a>Sebep  
 Programa bağımlı tüm bütünleştirilmiş kodları yerel biçiminde oluşturulmuş veya sahip doğru şekilde kaydedilmemiş.  
  
## <a name="resolution"></a>Çözüm  
 Bu MDA etkinleştirme JIT olarak derlenmiş hangi işlevi belirlemenize olanak sağlar. İşlevi içeren bütünleştirilmiş kodun yerel biçiminde oluşturulur ve düzgün şekilde kayıtlı olup olmadığını belirler.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı üzerindeki etkisi  
 Bu MDA, bu MDA etkinleştirme performansı üzerinde önemli bir etkisi yoktur, dolayısıyla yalnızca bir yöntem JIT olarak derlenmiş, önce bir ileti kaydeder. Satır içi bir yöntem ise bu mda'nın ayrı bir ileti oluşturmaz unutmayın.  
  
## <a name="output"></a>Çıkış  
 Aşağıdaki kod örneği, örnek çıktı gösterilmektedir. Bu durumda, "ns2.CO" sınıfı "m" metodunda Test derlemesindeki çıkışın gösterdiği JIT olarak derlenmiş.  
  
```  
method name="Test!ns2.C0::m"  
```  
  
## <a name="configuration"></a>Yapılandırma  
 Aşağıdaki yapılandırma dosyası, hangi yöntemlerin JIT olarak derlenmiş olsalar ilk raporlanır filtrelemek üzere kullanılan filtreler çeşitli gösterir. Tüm yöntemleri ad özniteliğini ayarlayarak bildirilmesini belirtebilirsiniz \*.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Birlikte Çalışma için Hazırlama](../../../docs/framework/interop/interop-marshaling.md)
