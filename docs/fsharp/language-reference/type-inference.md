---
title: Tür Çıkarma (F#)
description: 'F # derleyicisi değerleri, değişkenleri, parametreler ve dönüş değerlerinin türleri nasıl çıkarsar öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: fd826ac48fb9a70aa6f4ff746599c11b7e21a02e
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "43865702"
---
# <a name="type-inference"></a>Tür Çıkarma

Bu konu, F # derleyicisi değerleri, değişkenleri, parametreler ve dönüş değerlerinin türleri nasıl çıkarsar açıklar.

## <a name="type-inference-in-general"></a>Genel tür çıkarımı

Tür çıkarımı, ne zaman derleyici türü yaratacağı çıkarılamıyor dışında F # yapılarını türlerini belirtmek gerekmez olur. Açık tür bilgileri atlama F # bir dinamik olarak belirlenmiş dildir veya F # değerleri zayıf olduğu anlamına gelmez. F # derleyici, derleme sırasında her yapı için tam bir tür çıkarır anlamına gelen bir statik olarak belirlenmiş, dilidir. Her yapı türlerini kullanarak derleyicinin için yeterli bilgi değilse açık tür ek açıklamaları yere kod ekleyerek ek tür bilgileri, genellikle sağlamalısınız.

## <a name="inference-of-parameter-and-return-types"></a>Çıkarım parametre ve dönüş türleri

Bir parametre listesinde her parametresinin türünü belirtmeniz gerekmez. Henüz, F # bir statik olarak yazılmış bir dildir ve bu nedenle her değer ve ifade derleme zamanında kesin bir türe sahip. Türlerine her zaman açık belirtmeyin bağlamına dayalı türü derleyicinin çıkarır. Belirtilen tür Aksi durumda değilse, genel olarak algılanır. Kod bir değer tutarsız kullanıyorsa, şekilde olduğunu Hayır tek bir değerin tüm kullanımları derleyici bir hata bildiriyor karşılayan türün gösterilmesi.

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

Tür çıkarımı, F # dil belirtiminde daha ayrıntılı açıklanmıştır.

## <a name="see-also"></a>Ayrıca bkz.

- [Otomatik Genelleştirme](generics/automatic-generalization.md)
