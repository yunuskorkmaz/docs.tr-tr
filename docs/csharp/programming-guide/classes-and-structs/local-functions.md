---
title: Yerel işlevler (C# programlama Kılavuzu)
ms.date: 06/14/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- local functions [C#]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ac18aa57f443f28f55779ff9c92a5349b9b39fd7
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="local-functions-c-programming-guide"></a>Yerel işlevler (C# programlama Kılavuzu)

C# 7.0, C# destekler'ile başlayan *yerel işlevler*. Başka bir üye iç içe geçmiş özel bir tür yöntemlerinin yerel işlevlerdir. Kendi içeren üyeden yalnızca çağrılabilir. Yerel işlevler içinde bildirilen ve çağrılır:

- Yöntemleri, özellikle Yineleyici ve zaman uyumsuz yöntemleri
- Oluşturucular
- Özellik erişimcisi
- Olay erişimcileri
- Anonim yöntemler
- Lambda ifadeleri
- Sonlandırıcılar
- Diğer yerel işlevler

Ancak, yerel işlevler bir ifade bodied üye iç bildirilemez.

> [!NOTE]
> Bazı durumlarda, ayrıca yerel bir işlev tarafından desteklenen işlevleri uygulamak için bir lambda ifadesi kullanabilirsiniz. Bir karşılaştırması için bkz: [Lambda ifadeleri karşılaştırma yerel işlevler](../../local-functions-vs-lambdas.md).

Yerel işlevler kodunuzu Temizle amacı olun. Herkes okuma yöntemi içeren yöntemi tarafından çağrılabilir dışında değil, kodunu görebilirsiniz. Takım projeleri için de, yanlışlıkla doğrudan başka bir yerden yöntemini çağırmak başka bir geliştirici mümkün yaptıkları sınıfı ya da stuct.
 
## <a name="local-function-syntax"></a>Yerel işlev sözdizimi

Yerel bir işlev içeren bir üye içinde iç içe geçmiş bir yöntem olarak tanımlanır. Tanımına sözdizimi aşağıdaki gibidir:

```txt
<modifiers: async | unsafe> <return-type> <method-name> <parameter-list>
```

Yerel işlevler kullanabileceğiniz [zaman uyumsuz](../../language-reference/keywords/async.md) ve [güvensiz](../../language-reference/keywords/unsafe.md) değiştiricileri. 

Kendi yöntem parametreleri de dahil olmak üzere içeren üye içinde tanımlanan tüm yerel değişkenler yerel işlevde erişilebilir olduğunu unutmayın. 

Bir yöntemin tanımı yerel işlev tanımı aşağıdaki öğeleri içeremez:

- Üye erişim değiştiricisi. Tüm yerel işlevler özel olduğundan, bir erişim değiştiricisi gibi dahil `private` anahtar sözcüğü oluşturur Derleyici Hatası CS0106, "'özel' değiştiricisi bu öğe için geçerli değil."
 
- [Statik](../../language-reference/keywords/static.md) anahtar sözcüğü. Dahil olmak üzere `static` anahtar sözcüğü Derleyici Hatası CS0106 oluşturur, "'static' değiştiricisi bu öğe için geçerli değil."

Ayrıca, öznitelikler yerel işlevi veya parametrelerini uygulanamaz ve parametreleri yazın. 
 
Aşağıdaki örnek adlı bir yerel işlevi tanımlar `AppendPathSeparator` adlı bir yönteme özel olan `GetText`:
   
[!code-csharp[LocalFunctionExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions1.cs)]  
   
## <a name="local-functions-and-exceptions"></a>Yerel işlevler ve özel durumlar

Yerel işlevler yararlı özelliklerini hemen yüzey için özel durumlar izin verebilir biridir. Yöntemi yineleyiciler için özel durumlar, yalnızca döndürülen dizi numaralandırıldığı zaman ve değil yineleyici alındığında çıkmış. Döndürülen görev beklemenin zaman zaman uyumsuz yöntemleri için bir zaman uyumsuz yöntem karşılaşılan özel durumlar gözetilir. 

Aşağıdaki örnek tanımlayan bir `OddSequence` belirli bir aralık arasında tek sayıları numaralandırır yöntemi. Bir sayı 100'den büyük atladığı için `OddSequence` yöntemi Numaralandırıcı yöntemi atar bir <xref:System.ArgumentOutOfRangeException>. Örneğin çıktısını gösterildiği gibi özel durum yalnızca sayıları yinelemek ve Numaralandırıcı almama zamanı ortaya çıkarır.

[!code-csharp[LocalFunctionIterator1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator1.cs)] 

Bunun yerine, doğrulama yapılırken bir özel durum ve yerel bir işleve yineleyici döndürerek yineleyici almadan önce aşağıdaki örnekte görüldüğü gibi.

[!code-csharp[LocalFunctionIterator2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator2.cs)]

Yerel İşlevler, zaman uyumsuz işlemi dışında özel durumları işlemek için benzer bir şekilde kullanılabilir. Normalde, iç özel durumları inceleyin async yöntemi içinde oluşturulan özel durumları gerektiren bir <xref:System.AggregateException>. Yerel işlevler hızlı başarısız ve hem oluşturulur ve zaman uyumlu olarak gözlenen özel izin vermek kodunuzu izin verir.

Aşağıdaki örnek adlı zaman uyumsuz bir yöntem kullanır `GetMultipleAsync` belirtilen sayıda saniye için Duraklat ve o saniye sayısını rastgele birden fazla olan bir değer döndürür. En büyük gecikme 5 saniyedir; bir <xref:System.ArgumentOutOfRangeException> değer 5'ten büyük olduğunda oluşur. Aşağıdaki örnekte gösterildiği gibi bir değer 6'ın zaman oluşturulur özel durum sınıfına `GetMultipleAsync` yöntemi kaydırılır bir <xref:System.AggregateException> sonra `GetMultipleAsync` yöntemi yürütülmesine başlar.

[!code-csharp[LocalFunctionAsync`](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async1.cs)] 

İle yöntemi yineleyici yaptığımız gibi biz zaman uyumsuz bir yöntemini çağırmadan önce doğrulama gerçekleştirmek için bu örnek kodu yeniden. Aşağıdaki örnekte gösterildiği çıktısı olarak <xref:System.ArgumentOutOfRangeException> < x:System.AggregateException > içinde sarmalanmamış.

[!code-csharp[LocalFunctionAsync`](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async2.cs)] 

## <a name="see-also"></a>Ayrıca bkz.
[Yöntemler](methods.md)
