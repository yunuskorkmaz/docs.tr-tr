---
title: Yerel işlevler- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 06/14/2017
helpviewer_keywords:
- local functions [C#]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f572f683511fe90951f841c80eae448a9cb6054b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785083"
---
# <a name="local-functions-c-programming-guide"></a>Yerel işlevler (C# Programlama Kılavuzu)

7,0 ile C# başlayarak C# *Yerel işlevleri*destekler. Yerel işlevler, başka bir üyede iç içe yerleştirilmiş bir türün özel yöntemleridir. Yalnızca kendi kapsayıcı üyelerinden çağrılabilir. Yerel işlevler içinde bildirilebilecek ve şuradan çağrılabilir:

- Yöntemler, özellikle Yineleyici yöntemleri ve zaman uyumsuz yöntemler
- Oluşturucular
- Özellik erişimcileri
- Olay erişimcileri
- Anonim yöntemler
- Lambda ifadeleri
- Sonlandırıcılar
- Diğer yerel işlevler

Ancak, yerel işlevler ifade-Bodied üyesi içinde bildirilemez.

> [!NOTE]
> Bazı durumlarda, bir yerel işlev tarafından desteklenen işlevselliği uygulamak için bir lambda ifadesi kullanabilirsiniz. Bir karşılaştırma için bkz. [Yerel Işlevler lambda ifadelerine kıyasla](../../local-functions-vs-lambdas.md).

Yerel işlevler, kodunuzun amacını açık hale getirir. Kodunuzu okuyan herkes, yöntemin kapsayan Yöntem dışında çağrılabilir olmadığını görebilir. Ekip projeleri için, başka bir geliştiricinin yöntemi doğrudan sınıf veya yapı içinde başka bir yerde çağırmak olanaksız hale getirir.
 
## <a name="local-function-syntax"></a>Yerel işlev sözdizimi

Yerel bir işlev, kapsayan bir üye içinde iç içe geçmiş bir yöntem olarak tanımlanır. Tanımı aşağıdaki sözdizimine sahiptir:

```txt
<modifiers: async | unsafe> <return-type> <method-name> <parameter-list>
```

Yerel işlevler, [zaman uyumsuz](../../language-reference/keywords/async.md) ve [güvenli olmayan](../../language-reference/keywords/unsafe.md) değiştiriciler kullanabilir. 

Kendi Yöntem parametreleri de dahil olmak üzere, kapsayan üyede tanımlanan tüm yerel değişkenlerin yerel işlevde erişilebilir olduğunu unutmayın. 

Bir yöntem tanımının aksine, yerel bir işlev tanımı aşağıdaki öğeleri içeremez:

- Üye erişim değiştiricisi. Tüm yerel işlevler özel olduğundan, `private` anahtar sözcüğü gibi bir erişim değiştiricisi de dahil olmak üzere, "özel ' değiştiricisi Bu öğe için geçerli değil."
 
- [Static](../../language-reference/keywords/static.md) anahtar sözcüğü. "Static ' değiştiricisi Bu öğe için geçerli değil, anahtarsözcüğünüCS0106derleyicihatasıoluşturuyor."`static`

Ayrıca, öznitelikler yerel işleve veya parametrelerine ve parametre türüne uygulanamaz. 
 
Aşağıdaki örnek adlı bir yerel işlevi `AppendPathSeparator` `GetText`tanımlar:
   
[!code-csharp[LocalFunctionExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions1.cs)]  
   
## <a name="local-functions-and-exceptions"></a>Yerel işlevler ve özel durumlar

Yerel işlevlerin yararlı özelliklerinden biri, özel durumların hemen yüzeyine izin verebilir. Yöntem yineleyiciler için, özel durumlar yalnızca döndürülen dizi numaralandırıldıktan sonra, yineleyici alındığında değil, ortaya çıkacak. Zaman uyumsuz metotlar için, bir zaman uyumsuz yöntemde oluşturulan özel durumlar, döndürülen görev beklendiğinde gözlemlenir. 

Aşağıdaki örnek, belirtilen bir `OddSequence` Aralık arasındaki tek sayıları numaralandırır bir yöntemi tanımlar. `OddSequence` Numaralandırıcı yöntemine 100 ' den büyük bir sayı geçirdiğinden, yöntemi bir <xref:System.ArgumentOutOfRangeException>oluşturur. Örneğin çıkışının gösterdiği gibi, özel durum yalnızca sayıları tekrarladığı zaman, numaralandırıcıyı alırken değil, yüzeyleri.

[!code-csharp[LocalFunctionIterator1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator1.cs)] 

Bunun yerine, aşağıdaki örnekte gösterildiği gibi, bir yerel işlevden Yineleyici döndürerek, doğrulama gerçekleştirirken ve yineleyici almadan önce bir özel durum oluşturabilirsiniz.

[!code-csharp[LocalFunctionIterator2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator2.cs)]

Yerel işlevler, zaman uyumsuz işlem dışındaki özel durumları işlemek için benzer bir şekilde kullanılabilir. Genellikle, zaman uyumsuz yöntemde oluşturulan özel durumlar, öğesinin <xref:System.AggregateException>iç özel durumlarını incelemenizi gerektirir. Yerel işlevler, kodunuzun hızlı bir şekilde başarısız olmasına olanak tanır ve özel durumun hem zaman uyumlu olarak hem de aynı şekilde gözlemlenip

Aşağıdaki örnek, belirtilen saniye sayısını duraklatmak için `GetMultipleAsync` adlı zaman uyumsuz bir yöntem kullanır ve bu sayıda saniyeden oluşan rastgele bir değer döndürür. En fazla gecikme 5 saniyedir; değer <xref:System.ArgumentOutOfRangeException> 5 ' ten büyükse bir sonuç elde edilir. Aşağıdaki örnekte gösterildiği gibi, `GetMultipleAsync` yöntemine 6 değeri geçirildiğinde oluşturulan özel durum, `GetMultipleAsync` Yöntem yürütmeye başladıktan sonra bir <xref:System.AggregateException> öğesine kaydırılır.

[!code-csharp[LocalFunctionAsync`](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async1.cs)] 

Yöntem yineleyicisi ile yaptığımız gibi, zaman uyumsuz metodu çağırmadan önce doğrulamayı gerçekleştirmek için bu örnekteki kodu yeniden düzenleyebilirsiniz. Aşağıdaki örnekteki Çıktının gösterdiği gibi, ' <xref:System.ArgumentOutOfRangeException> a <xref:System.AggregateException>sarmalanmaz.

[!code-csharp[LocalFunctionAsync`](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async2.cs)] 

## <a name="see-also"></a>Ayrıca bkz.

- [Yöntemler](methods.md)
