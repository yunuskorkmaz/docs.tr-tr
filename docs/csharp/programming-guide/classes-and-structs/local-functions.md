---
title: Yerel işlevler- C# Programlama Kılavuzu
ms.date: 06/14/2017
helpviewer_keywords:
- local functions [C#]
ms.openlocfilehash: 2036e576a44aa3e1e7829e2091e5a9243d6b6010
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705528"
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

```csharp
<modifiers: async | unsafe> <return-type> <method-name> <parameter-list>
```

Yerel işlevler, [zaman uyumsuz](../../language-reference/keywords/async.md) ve [güvenli olmayan](../../language-reference/keywords/unsafe.md) değiştiriciler kullanabilir. 

Kendi Yöntem parametreleri de dahil olmak üzere, kapsayan üyede tanımlanan tüm yerel değişkenlerin yerel işlevde erişilebilir olduğunu unutmayın. 

Bir yöntem tanımının aksine, yerel bir işlev tanımı üye erişim değiştiricisini içeremez. Tüm yerel işlevler özel olduğundan, `private` anahtar sözcüğü gibi bir erişim değiştiricisi de dahil olmak üzere, "özel ' değiştiricisi Bu öğe için geçerli değil."

> [!NOTE]
> C# 8,0 ' den önce yerel işlevler `static` değiştiricisini içeremez. `static` anahtar sözcüğünü içeren derleyici hatası CS0106, "' static ' değiştiricisi Bu öğe için geçerli değil."

Ayrıca, öznitelikler yerel işleve veya parametrelerine ve parametre türüne uygulanamaz. 
 
Aşağıdaki örnek, `GetText`adlı bir yönteme özel `AppendPathSeparator` adlı yerel bir işlevi tanımlar:
   
[!code-csharp[LocalFunctionExample](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions1.cs)]  
   
## <a name="local-functions-and-exceptions"></a>Yerel işlevler ve özel durumlar

Yerel işlevlerin yararlı özelliklerinden biri, özel durumların hemen yüzeyine izin verebilir. Yöntem yineleyiciler için, özel durumlar yalnızca döndürülen dizi numaralandırıldıktan sonra, yineleyici alındığında değil, ortaya çıkacak. Zaman uyumsuz metotlar için, bir zaman uyumsuz yöntemde oluşturulan özel durumlar, döndürülen görev beklendiğinde gözlemlenir. 

Aşağıdaki örnek, belirtilen bir Aralık arasındaki tek sayıları numaralandırır `OddSequence` yöntemini tanımlar. `OddSequence` Numaralandırıcı yöntemine 100 ' den büyük bir sayı geçirdiğinden, yöntem bir <xref:System.ArgumentOutOfRangeException>oluşturur. Örneğin çıkışının gösterdiği gibi, özel durum yalnızca sayıları tekrarladığı zaman, numaralandırıcıyı alırken değil, yüzeyleri.

[!code-csharp[LocalFunctionIterator1](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator1.cs)] 

Bunun yerine, aşağıdaki örnekte gösterildiği gibi, bir yerel işlevden Yineleyici döndürerek, doğrulama gerçekleştirirken ve yineleyici almadan önce bir özel durum oluşturabilirsiniz.

[!code-csharp[LocalFunctionIterator2](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator2.cs)]

Yerel işlevler, zaman uyumsuz işlem dışındaki özel durumları işlemek için benzer bir şekilde kullanılabilir. Genellikle, zaman uyumsuz yöntemde oluşturulan özel durumlar, bir <xref:System.AggregateException>iç özel durumlarını incelemenizi gerektirir. Yerel işlevler, kodunuzun hızlı bir şekilde başarısız olmasına olanak tanır ve özel durumun hem zaman uyumlu olarak hem de aynı şekilde gözlemlenip

Aşağıdaki örnek, belirtilen saniye sayısını duraklatmak için `GetMultipleAsync` adlı zaman uyumsuz bir yöntem kullanır ve bu kadar saniye rastgele bir değer döndürür. En fazla gecikme 5 saniyedir; değer 5 ' ten büyükse bir <xref:System.ArgumentOutOfRangeException> sonuç elde edilir. Aşağıdaki örnekte gösterildiği gibi, `GetMultipleAsync` yöntemine 6 değeri geçirildiğinde oluşturulan özel durum, `GetMultipleAsync` yöntemi yürütülmeye başladıktan sonra bir <xref:System.AggregateException> sarmalanır.

[!code-csharp[LocalFunctionAsync](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async1.cs)] 

Yöntem yineleyicisi ile yaptığımız gibi, zaman uyumsuz metodu çağırmadan önce doğrulamayı gerçekleştirmek için bu örnekteki kodu yeniden düzenleyebilirsiniz. Aşağıdaki örnekteki Çıktının gösterdiği gibi, <xref:System.ArgumentOutOfRangeException> bir <xref:System.AggregateException>sarmalanmamış.

[!code-csharp[LocalFunctionAsync](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async2.cs)] 

## <a name="see-also"></a>Ayrıca bkz.

- [Yöntemler](methods.md)
