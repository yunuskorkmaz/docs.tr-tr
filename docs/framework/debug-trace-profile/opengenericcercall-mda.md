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
ms.openlocfilehash: 92528a2cf2227520327b9be2dca70be4c238ff61
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54564688"
---
# <a name="opengenericcercall-mda"></a>openGenericCERCall MDA
`openGenericCERCall` Yönetilen hata ayıklama Yardımcısı, genel tür değişkenleri kök yöntemi ile kısıtlı yürütme bölge (CER) grafik JIT derleme veya yerel görüntü oluşturma zamanına ve en az bir genel işlenmekte olduğunu uyarmak için etkinleştirildi türü değişkenler olan bir nesne başvuru türü.  
  
## <a name="symptoms"></a>Belirtiler  
 Bir iş parçacığı iptal edildiğinde veya uygulama etki alanı kaldırıldığında CER kod çalıştırmaz.  
  
## <a name="cause"></a>Sebep  
 JIT derleme zamanında örneklemesi içeren bir nesne başvuru türü yalnızca Sonuç kodu paylaşılır ve her nesne başvuru türü değişkenlerin herhangi bir nesne başvuru türü olabilir çünkü temsilcisidir. Bu, bazı çalışma zamanı kaynaklar önceden hazırlanması engelleyebilir.  
  
 Özellikle, genel tür değişkenleri olan yöntemleri gevşek arka planda kaynakları tahsis edebilirsiniz. Bunlar, genel bir sözlük girişleri olarak adlandırılır. Deyim için örneği için `List<T> list = new List<T>();` burada `T` çalışma zamanı aramak ve büyük olasılıkla tam oluşturmada çalışma zamanında, örneğin, oluşturun bir genel tür değişken `List<Object>, List<String>`ve böyle devam eder. Bu, çeşitli nedenlerle yetersiz bellek çalışıyor gibi geliştiricinin kontrolü için başarısız olabilir.  
  
 Bu MDA, JIT derleme zamanında tam örneklemesi olduğunda değil yalnızca etkinleştirilmelidir.  
  
 Bu MDA etkinleştirildiğinde, büyük olasılıkla Belirtiler CERs hatalı örneklemesi için işlevsel olmayan olan. Aslında, çalışma zamanı etkinleştirilecek MDA neden koşullarda bir CER uygulamak çalıştı değil. Bu nedenle Geliştirici sonra JIT derleme CER paylaşılan bir örneğinin kullanıyorsa, genel türler yükleme hataları yazın ya da iş parçacığı iptalleri hedeflenen CER bölge içinde yakalanır değil.  
  
## <a name="resolution"></a>Çözüm  
 Nesne başvuru türü bir CER içerebilir yöntemleri için genel tür değişkenler kullanmayın.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı üzerindeki etkisi  
 Bu mda'nın CLR üzerinde etkisi yoktur.  
  
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
 CER kod yürütülmez.  
  
```csharp
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
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>
- <xref:System.Runtime.ConstrainedExecution>
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
