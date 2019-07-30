---
title: Tür Çıkarma
description: F# Derleyicinin değer, değişken, parametre ve dönüş değeri türlerini nasıl kullandığını öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: 4b18c1a67a8b7ddadb4fb334ea4736e9fd29feb0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630186"
---
# <a name="type-inference"></a>Tür Çıkarma

Bu konu, F# derleyicinin değer, değişken, parametre ve dönüş değeri türlerini nasıl kullandığını açıklar.

## <a name="type-inference-in-general"></a>Genel olarak tür çıkarımı

Tür çıkarımı, derleyicinin türü yaratacağı ne zaman bir F# değer çıkarmadığını hariç, yapı türlerini belirtmeniz gerekmez. Açık tür bilgilerinin atlanması, dinamik olarak yazılmış F# bir dil olan veya ' deki F# değerlerin zayıf olarak yazıldığı anlamına gelmez. F#statik olarak yazılmış bir dildir, bu, derleyicinin derleme sırasında her bir yapı için tam bir tür olarak kesintiler anlamına gelir. Derleyicinin her bir yapının türünü vermesini sağlamak için yeterli bilgi yoksa, genellikle kodda bir yere açık tür ek açıklamaları ekleyerek ek tür bilgileri sağlamanız gerekir.

## <a name="inference-of-parameter-and-return-types"></a>Parametre ve dönüş türlerinin çıkarımı

Bir parametre listesinde, her parametrenin türünü belirtmeniz gerekmez. Ancak, F# statik olarak yazılmış bir dildir ve bu nedenle her değer ve ifadede derleme zamanında kesin bir tür vardır. Açıkça belirtmedikleri türler için, derleyici bu türü bağlama göre alır. Tür başka bir şekilde belirtilmemişse, genel olarak algılanır. Kod, bir değeri tutarsız bir şekilde kullanıyorsa, bir değerin tüm kullanımlarını karşılayan tek bir Çıkarsanan tür yoksa, derleyici bir hata bildirir.

İşlevin dönüş türü, işlevdeki son ifadenin türüne göre belirlenir.

Örneğin, aşağıdaki kodda, parametre türleri `a` ve `b` ve dönüş türü, değişmez değer `100` türünde `int`olduğu için `int` hepsi olarak algılanır.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet301.fs)]

Sabit değerleri değiştirerek tür çıkarımı etkileyebilir. `100` `uint32` `uint32` `b`Son Eki`u`ekleyerek bir yaparsanız,,, ve dönüş değerinin türü olarakalgılanır.`a`

Tür çıkarımı, yalnızca belirli bir türle çalışan işlevler ve yöntemler gibi tür kısıtlamalarını belirten diğer yapıları kullanarak da etkileyebilir.

Ayrıca, aşağıdaki örneklerde gösterildiği gibi, işlev veya yöntem parametrelerine ya da deyimlerdeki değişkenlere açık tür ek açıklamaları uygulayabilirsiniz. Hatalar, farklı kısıtlamalar arasında çakışmalar oluşursa oluşur.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet302.fs)]

Ayrıca, tüm parametrelerden sonra bir tür ek açıklaması sağlayarak bir işlevin dönüş değerini açıkça belirtebilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet303.fs)]

Bir parametre üzerinde yararlı bir tür ek açıklamanın, parametrenin nesne türü olması ve bir üyeyi kullanmak istediğinizde olduğu yaygın bir durumdur.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet304.fs)]

## <a name="automatic-generalization"></a>Otomatik Genelleştirme

İşlev kodu bir parametre türüne bağımlı değilse, derleyici parametreyi genel olacak şekilde değerlendirir. Buna *Otomatik Genelleştirme*denir ve karmaşıklık arttırmadan genel kod yazmak için güçlü bir yardım olabilir.

Örneğin, aşağıdaki işlev herhangi bir türdeki iki parametreyi bir tanımlama grubu içinde birleştirir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet305.fs)]

Tür şu şekilde algılanır

```fsharp
'a -> 'b -> 'a * 'b
```

## <a name="additional-information"></a>Ek Bilgiler

Tür çıkarımı, F# dil belirtiminde daha ayrıntılı olarak açıklanmıştır.

## <a name="see-also"></a>Ayrıca bkz.

- [Otomatik Genelleştirme](./generics/automatic-generalization.md)
