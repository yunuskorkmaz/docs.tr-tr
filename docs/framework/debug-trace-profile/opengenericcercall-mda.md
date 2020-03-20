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
ms.openlocfilehash: 7492a4c0547680a6ace85a5f7c98567770f5575a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181774"
---
# <a name="opengenericcercall-mda"></a>openGenericCERCall MDA

Yönetilen `openGenericCERCall` hata ayıklama yardımcısı, kök yönteminde genel tür değişkenleri içeren kısıtlanmış bir yürütme bölgesi (CER) grafiğinin JIT derlemeveya yerel görüntü oluşturma zamanında işlendiğini ve genel tür değişkenlerinden en az birinin nesne başvuru türü olduğu konusunda uyarmak için etkinleştirilir.

## <a name="symptoms"></a>Belirtiler

Cer kodu, iş parçacığı iptal edildiğinde veya uygulama etki alanı boşaltıldığında çalışmaz.

## <a name="cause"></a>Nedeni

JIT derleme zamanında, bir nesne başvuru türü içeren bir anlık ileti yalnızca, elde edilen kod paylaşıldı ve nesne başvuru türü değişkenlerinin her biri herhangi bir nesne başvuru türü olabilir. Bu, bazı çalışma zamanı kaynaklarının önceden hazırlanmasını engelleyebilir.

Özellikle, genel tür değişkenleri ile yöntemler tembel arka planda kaynakları tahsis edebilirsiniz. Bunlara genel sözlük girişleri denir. Örneğin, genel bir `List<T> list = new List<T>();` `T` tür değişkeninin olduğu deyim için çalışma zamanı yukarı bakmalı ve muhtemelen çalışma `List<Object>, List<String>`zamanında tam anlık oluşturmayı, örneğin, ve saire. Bu, geliştiricinin denetimi dışında bellek tükenen çeşitli nedenlerle başarısız olabilir.

Bu MDA sadece JIT derleme zamanında etkinleştirilmelidir, tam bir anlık olduğunda değil.

Bu MDA etkinleştirildiğinde, olası belirtiler CEO'ların kötü anlık algılamalar için işlevsel olmadığıdır. Aslında, çalışma süresi MDA'nın etkinleştirilmesine neden olan koşullar altında bir CER uygulamaya çalışmamıştır. Bu nedenle, geliştirici CER'in paylaşılan bir anlık iletisini kullanırsa, JIT derleme hataları, genel yazı yükleme hataları veya amaçlanan CER bölgesindeki iş parçacığı iptalleri yakalanmaz.

## <a name="resolution"></a>Çözüm

CER içerebilecek yöntemler için nesne başvuru türüne ait genel tür değişkenleri kullanmayın.

## <a name="effect-on-the-runtime"></a>Çalışma Süresi üzerindeki etkisi

Bu MDA'nın CLR üzerinde hiçbir etkisi yoktur.

## <a name="output"></a>Çıktı

Bu MDA çıktısının bir örneği aşağıda veda edilebistir:
  
 ```output
 Method 'GenericMethodWithCer', which contains at least one constrained execution region, cannot be prepared automatically since it has one or more unbound generic type parameters.
 The caller must ensure this method is prepared explicitly at run time prior to execution.
 method name="GenericMethodWithCer"
 declaringType name="OpenGenericCERCall"
 ```

## <a name="configuration"></a>Yapılandırma

```xml
<mdaConfig>
  <assistants>
    <openGenericCERCall/>
  </assistants>
</mdaConfig>
```  

## <a name="example"></a>Örnek

CER kodu yürütülmez.

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
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](diagnosing-errors-with-managed-debugging-assistants.md)
