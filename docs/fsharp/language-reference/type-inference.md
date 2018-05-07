---
title: Tür Çıkarma (F#)
description: 'F # derleyici değerleri, değişkenleri, parametreler ve dönüş değerleri türlerini nasıl oluşturur öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: 93e1568ebe71436ad8f7119ac9d9628cdf58012a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="type-inference"></a>Tür Çıkarma

Bu konu, F # derleyici değerleri, değişkenleri, parametreler ve dönüş değerleri türlerini nasıl oluşturur açıklar.

## <a name="type-inference-in-general"></a>Genel tür çıkarımı
Tür çıkarımı fikri zaman derleyici conclusively türünü türetme edilemez dışında F # yapılarını türlerini belirtmek gerekmez değildir. Açık tür bilgileri atlama F # dinamik olarak yazılan bir dil olan veya değerleri F # zayıf yazılmış anlamına gelmez. F # derleyici derleme sırasında her bir yapı için tam bir türe deduces anlamına gelen bir statik olarak belirtilmiş, dilidir. Her yapı türleri türetme derleyici için yeterli bilgi değilse açık tür ek açıklama herhangi bir yerde kodda ekleyerek ek tür bilgileri, genellikle sağlamalısınız.


## <a name="inference-of-parameter-and-return-types"></a>Çıkarım parametre ve dönüş türleri
Bir parametre listesinde her parametresinin türü belirtmeniz gerekmez. Henüz, F # bir statik olarak yazılmış bir dildir ve bu nedenle her değer ve ifade derleme zamanında kesin bir türe sahip. Açıkça belirtmeyin türleri için derleyici bağlamına dayalı türü oluşturur. Belirtilen tür Aksi durumda değilse, genel olarak algılanır. Kod bir değer tutarsız kullanıyorsa, bir şekilde olduğunu Hayır tek bir değer tüm kullanımlarını derleyici bir hata bildirir karşılayan türü sonuçlandı.

Bir işlevin dönüş türü, işlev son ifade türü tarafından belirlenir.

Örneğin, aşağıdaki kodda, parametre türleri `a` ve `b` ve dönüş türü tüm çıkarımı yapılan olmasını `int` çünkü sabit `100` türü `int`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet301.fs)]

Tür çıkarımı değişmez değerleri değiştirerek etkileyebilir. Yaptığınız `100` bir `uint32` soneki ekleyerek `u`, türlerini `a`, `b`, ve dönüş değeri olarak olayla `uint32`.

Ayrıca etkileyebilir çıkarım işlevleri ve yalnızca belirli bir türü ile çalışmayı yöntemleri gibi türü kısıtlamalar kapsıyor diğer yapıları kullanarak yazın.

Ayrıca, açık tür ek açıklamaları işlev veya yöntem parametrelerini veya değişkenlerini ifadelerde, aşağıdaki örneklerde gösterildiği gibi uygulayabilirsiniz. Farklı kısıtlamaları arasında çakışma meydana gelirse hatalar neden.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet302.fs)]

Bir işlevin dönüş değeri türü ek açıklama tüm parametreleri sağlayarak açıkça belirtebilirsiniz.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet303.fs)]

Türü ek açıklama bir parametresini yararlı olduğu ortak bir nesne türü parametresi olduğunda ve bir üye kullanmak istediğiniz durumdur.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet304.fs)]
    
## <a name="automatic-generalization"></a>Otomatik Genelleştirme
İşlev kodu bağımlı bir parametrenin türü üzerinde değilse, genel olarak parametresi derleyici göz önünde bulundurur. Bu adlı *otomatik Genelleştirme*, ve karmaşıklık artırmadan genel kod yazma için güçlü bir yardımcı olabilir.

Örneğin, aşağıdaki işlev iki parametre tanımlama grubu içine herhangi bir türde birleştirir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet305.fs)]

Tür çıkarımı yapılan olmalıdır

```fsharp
'a -> 'b -> 'a * 'b
```

## <a name="additional-information"></a>Ek Bilgiler
Tür çıkarımı F # dil belirtimi bölümlerinde daha ayrıntılı açıklanmıştır.


## <a name="see-also"></a>Ayrıca Bkz.
[Otomatik Genelleştirme](generics/automatic-generalization.md)
