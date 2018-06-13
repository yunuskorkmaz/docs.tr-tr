---
title: openGenericCERCall MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), CER calls
- open generic CER calls
- constrained execution regions
- openGenericCERCall MDA
- CER calls
- managed debugging assistants (MDAs), CER calls
- generics [.NET Framework], open generic CER calls
ms.assetid: da3e4ff3-2e67-4668-9720-fa776c97407e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 486c3c44b69c69a472b7405b6c14f9d27a29d756
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33387526"
---
# <a name="opengenericcercall-mda"></a>openGenericCERCall MDA
`openGenericCERCall` Yönetilen hata ayıklama Yardımcısı JIT derleme veya yerel görüntü oluşturma zamanı ve en az bir genel kısıtlı yürütme bölge (CER) grafiğe kök yöntemi en genel tür değişkenlerle birlikte işleniyor uyarmak için etkinleştirildi türü değişkenleri olan bir nesne başvurusu türü.  
  
## <a name="symptoms"></a>Belirtiler  
 CER kod, bir iş parçacığı iptal edildiğinde veya uygulama etki alanı kaldırıldığında çalışmaz.  
  
## <a name="cause"></a>Sebep  
 JIT derleme zamanında bir nesne başvurusu türü içeren bir örnek oluşturma yalnızca Sonuç kodu paylaşılan ve her nesne başvurusu türü değişkenleri herhangi bir nesne başvurusu türünün olabilir çünkü temsilcisidir. Bu, bazı çalışma zamanı kaynaklar önceden hazırlanması engelleyebilir.  
  
 Özellikle, genel tür değişken içeren yöntemlerin gevşek arka planda kaynakları tahsis edebilirsiniz. Bunlar, genel bir sözlük girişleri olarak adlandırılır. Örneğin, deyim için `List<T> list = new List<T>();` nerede `T` çalışma zamanı aramak ve büyük olasılıkla tam örnek oluşturma zamanında, örneğin, oluşturma genel tür değişken `List<Object>, List<String>`, vb. Bu, çeşitli nedenlerle çalışan yetersiz bellek gibi geliştirici denetim ötesinde için başarısız olabilir.  
  
 Bu MDA JIT derleme zamanında, tam bir örnek oluşturma olduğunda değil yalnızca etkinleştirilmesi.  
  
 Bu MDA etkinleştirildiğinde, büyük olasılıkla Belirtiler CERs için hatalı örneklemesi işlevsel olduğundan emin olan. Aslında, çalışma zamanı CER etkinleştirilecek MDA neden olduğu durumlarda uygulamak çalıştı değil. Bu nedenle paylaşılan örneklemesi sonra JIT derleme CER, geliştirici kullanıyorsa, genel türler yükleme hataları yazın veya hedeflenen CER bölge içinde iş parçacığı iptalleri yakalanan değil.  
  
## <a name="resolution"></a>Çözüm  
 Nesne başvurusu türü bir CER içerebilir yöntemleri için genel tür değişkenler kullanmayın.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı etkisi  
 Bu MDA CLR üzerinde etkisi yoktur.  
  
## <a name="output"></a>Çıkış  
 Bu MDA çıktısı bir örnek verilmiştir.  
  
 `Method 'GenericMethodWithCer', which contains at least one constrained execution region, cannot be prepared automatically since it has one or more unbound generic type parameters.`  
  
 `The caller must ensure this method is prepared explicitly at run time prior to execution.`  
  
 `method name="GenericMethodWithCer"`  
  
 `declaringType name="OpenGenericCERCall"`  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <openGenericCERCall/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Örnek  
 CER kod yürütülmedi.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Runtime.CompilerServices;  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        CallGenericMethods();  
    }  
    static void CallGenericMethods()  
    {  
        // This call is correct. The instantiation of the method  
        // contains only nonreference types.  
        MyClass.GenericMethodWithCer<int>();  
  
        // This call is incorrect. A shared version of the method that  
        // cannot be completely analyzed will be JIT-compiled. The   
        // MDA will be activated at JIT-compile time, not at run time.  
        MyClass.GenericMethodWithCer<String>();  
    }  
}  
  
    class MyClass  
{  
    public static void GenericMethodWithCer<T>()  
    {  
        RuntimeHelpers.PrepareConstrainedRegions();  
        try  
        {  
  
        }  
        finally  
        {  
            // This is the start of the CER.  
            Console.WriteLine("In finally block.");  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>  
 <xref:System.Runtime.ConstrainedExecution>  
 [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
