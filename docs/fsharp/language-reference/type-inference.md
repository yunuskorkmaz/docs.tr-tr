---
title: Tür Çıkarma
description: Bilgi nasıl F# derleyici değerleri, değişkenleri, parametreler ve dönüş değerleri türlerini algılar.
ms.date: 05/16/2016
ms.openlocfilehash: 3e61d5c81fde0a48af66a47745123a842dc04cb1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61666241"
---
# <a name="type-inference"></a>Tür Çıkarma

Bu konu açıklar nasıl F# derleyici değerleri, değişkenleri, parametreler ve dönüş değerleri türlerini algılar.

## <a name="type-inference-in-general"></a>Genel tür çıkarımı

Türlerini belirtmek gerekmez tür çıkarımı fikirdir F# yapıları hariç, derleyicinin türü yaratacağı çıkarılamıyor. Açık tür bilgileri atlama gelmez, F# dinamik olarak yazılmış bir dildir veya bu değerleri F# zayıf sahipli olan türü belirtilmiş. F#Derleyici, derleme sırasında her yapı için tam bir tür çıkarır anlamına gelen bir statik olarak belirlenmiş, dilidir. Her yapı türlerini kullanarak derleyicinin için yeterli bilgi değilse açık tür ek açıklamaları yere kod ekleyerek ek tür bilgileri, genellikle sağlamalısınız.

## <a name="inference-of-parameter-and-return-types"></a>Çıkarım parametre ve dönüş türleri

Bir parametre listesinde her parametresinin türünü belirtmeniz gerekmez. Ve henüz F# statik olarak yazılmış bir dildir ve bu nedenle her değer ve ifade derleme zamanında kesin bir türe sahip. Türlerine her zaman açık belirtmeyin bağlamına dayalı türü derleyicinin çıkarır. Belirtilen tür Aksi durumda değilse, genel olarak algılanır. Kod bir değer tutarsız kullanıyorsa, şekilde olduğunu Hayır tek bir değerin tüm kullanımları derleyici bir hata bildiriyor karşılayan türün gösterilmesi.

Bir işlevin dönüş türü işlevdeki son ifadenin türü tarafından belirlenir.

Örneğin, aşağıdaki kodda, parametre türleri `a` ve `b` ve dönüş türü tüm çıkarılan olmasını `int` çünkü değişmez değer `100` türünde `int`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet301.fs)]

Tür çıkarımı değişmez değerleri değiştirerek etkileyebilir. Siz `100` bir `uint32` soneki ekleyerek `u`, türlerini `a`, `b`, ve dönüş değeri olarak ortaya çıkan `uint32`.

Ayrıca etkileyebilir çıkarımı işlevleri ve yalnızca belirli bir tür ile çalışan yöntemleri gibi tür kısıtlamalar yaptığından diğer yapıları kullanarak yazın.

Ayrıca, açık bir tür ek açıklamaları, ifadelerdeki değişkenler veya işlev veya metot parametreleri aşağıdaki örneklerde gösterildiği gibi uygulayabilirsiniz. Farklı kısıtlamaları arasında çakışma olursa, hatalara neden.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet302.fs)]

Ayrıca, bir tür ek açıklamasına tüm parametreleri sağlayarak bir işlevin dönüş değeri de açıkça belirtebilirsiniz.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet303.fs)]

Bir tür ek açıklamasına parametre üzerinde kullanışlı olduğu bir yaygın parametresi bir nesne türü ve üye kullanmak istediğiniz bir durumdur.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet304.fs)]

## <a name="automatic-generalization"></a>Otomatik Genelleştirme

İşlev kodu bir parametre türüne bağımlı değilse, derleyici genel parametre olarak değerlendirir. Bu adlandırılır *otomatik Genelleştirme*, ve genel kod karmaşıklığı artırmadan yazma için güçlü bir yardımcı olabilir.

Örneğin, aşağıdaki işlev bir demet içinde herhangi bir türde iki parametre birleştirir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet305.fs)]

Türün olacak şekilde gösterilmesi

```fsharp
'a -> 'b -> 'a * 'b
```

## <a name="additional-information"></a>Ek Bilgiler

Tür çıkarımı daha ayrıntılı olarak açıklanan F# dil belirtimi.

## <a name="see-also"></a>Ayrıca bkz.

- [Otomatik Genelleştirme](generics/automatic-generalization.md)