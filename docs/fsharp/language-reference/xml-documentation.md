---
title: XML Belgeleri (F#)
description: 'F # desteği hakkında daha fazla belge açıklamalarını oluşturmak için öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: 1a4cb132e65b630821e5eb2b39276c1de99aff80
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44360800"
---
# <a name="xml-documentation"></a>XML Belgeleri

Üç eğik çizgi (/ / /) belgelerinden oluşturabilecek kod yorumlarında F #. XML açıklamaları, kod dosyaları (.fs) veya imza (.fsi) dosyalarını bildirimlerinde koyabilirsiniz.

## <a name="generating-documentation-from-comments"></a>Belge açıklamaları oluşturma

Belge açıklamaları oluşturma desteği F # diğer .NET Framework dillerinde aynıdır. Diğer .NET Framework dillerde olduğu gibi [-doc derleyici seçeneği](https://msdn.microsoft.com/library/434394ae-0d4a-459c-a684-bffede519a04) Sandcastle gibi bir araç kullanarak belgeleme dönüştürebilirsiniz bilgilerini içeren bir XML dosyası üretebilir sağlar. Diğer .NET Framework dillerinde genel olarak yazılır derlemeleri ile kullanılmak üzere tasarlanmış araçları kullanılarak oluşturulan belgeleri derlenmiş F # yapılarını formdaki dayalı API'leri bir görünümünü oluşturur. Özellikle F # Destek Araçları sürece, bu araçları tarafından oluşturulan belgeleri F # görünümü bir API'nin eşleşmiyor.

XML'den belgeleri oluştur hakkında daha fazla bilgi için bkz: [XML belgeleri yorumları &#40;C&#35; Programming Guide&#41;](https://msdn.microsoft.com/library/b2s063f7).

## <a name="recommended-tags"></a>Önerilen etiketler

XML belgeleri yorumları yazmak için iki yolu vardır. Yalnızca XML etiketleri kullanmadan belgeleri doğrudan bir üç eğik çizgi açıklama yazmak için biridir. Bunu yaparsanız, tüm açıklama metni hemen izleyen kod yapısı için Özet belgeleri olarak alınır. Her yapı için yalnızca kısa bir özeti yazmak istediğinizde bu yöntemi kullanın. Diğer yöntem, yapılandırılmış belgeleri daha fazla bilgi sağlamak için XML etiketleri kullanmaktır. İkinci yöntem kısa bir özeti, ek açıklamalar, her bir parametre ve tür parametresi ve oluşturulan özel durumlar için belgeler ve dönüş değeri bir açıklaması için ayrı bir not belirtmenize olanak sağlar. Aşağıdaki tabloda, F # XML kodu açıklamalarını içinde tanınan XML etiketleri açıklanmaktadır.

|Etiket sözdizimi|Açıklama|
|----------|-----------|
|**&lt;c&gt;***metin***&lt;/c&gt;**|Belirten *metin* kodudur. Bu etiket, metin, kod için uygun bir yazı tipi görüntülemek için belgeleri Oluşturucuları tarafından kullanılabilir.|
|**&lt;Özet&gt;***metin*** &lt; /summary&gt;**|Belirten *metin* program öğesinin kısa açıklamasıdır. Genellikle bir veya iki cümle açıklamasıdır.|
|**&lt;Açıklamalar&gt;***metin*** &lt; /açıklamalar&gt;**|Belirten *metin* bir program öğesi hakkında ek bilgiler içerir.|
|**&lt;param name = "***adı***"&gt;***açıklama***&lt;/param&gt;**|Bir işlev veya metot parametresi için bir açıklama ve adını belirtir.|
|**&lt;typeparam name = "***adı***"&gt;***açıklama***&lt;/typeparam&gt;**|Bir tür parametresi için bir açıklama ve adını belirtir.|
|**&lt;döndürür&gt;***metin*** &lt; /döndürür&gt;**|Belirten *metin* dönüş değeri bir işlev veya metot açıklar.|
|**&lt;özel durum cref = "***türü***"&gt;***açıklama***&lt;/exception&gt;**|Oluşturulabilecek özel durum ve durum durumlarda türünü belirtir.|
|**&lt;see cref = "***başvuru***"&gt;***metin*** &lt; /bakın&gt;**|Başka bir program öğesi için satır içi bağlantı belirtir. *Başvuru* XML belge dosyası içinde görünen addır. *Metin* bağlantıya gösterilen metin.|
|**&lt;SeeAlso cref = "***başvuru***" /&gt;**|Başka bir türe yönelik belgelere ayrıca bağlantı belirtir. *Başvuru* XML belge dosyası içinde görünen addır. Ayrıca bkz: bağlantılar genellikle belgeleri sayfasının en altında görünür.|
|**&lt;para&gt;***metin***&lt;/para&gt;**|Paragraf metni belirtir. Bu metin içinde ayırmak için kullanılan **açıklamalar** etiketi.|

## <a name="example"></a>Örnek

### <a name="description"></a>Açıklama

Bir imza dosyası tipik bir XML belgesi açıklamasında verilmiştir.

### <a name="code"></a>Kod

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7101.fs)]

## <a name="example"></a>Örnek

### <a name="description"></a>Açıklama

Aşağıdaki örnek XML etiketi olmayan alternatif bir yöntemi gösterir. Bu örnekte, tüm metin açıklamasında bir Özet olarak kabul edilir. Açıkça Özet bir etiket belirtmezseniz, diğer etiketler gibi belirtmeniz gerekir değil, Not **param** veya **döndürür** etiketler.

### <a name="code"></a>Kod

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7102.fs)]

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
- [Derleyici Seçenekleri](compiler-options.md)
