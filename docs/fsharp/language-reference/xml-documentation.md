---
title: XML Belgeleri (F#)
description: Desteği hakkında bilgi edinin F# açıklamalardan belgeleri oluşturmak için.
ms.date: 05/16/2016
ms.openlocfilehash: c5305dea8832112644710b2863269ef00feddd10
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61902180"
---
# <a name="xml-documentation"></a>XML Belgeleri

Üç eğik çizgi (/ / /) belgelerinden oluşturabilecek kod açıklamaları F#. XML açıklamaları, kod dosyaları (.fs) veya imza (.fsi) dosyalarını bildirimlerinde koyabilirsiniz.

## <a name="generating-documentation-from-comments"></a>Belge açıklamaları oluşturma

Destek F# açıklamalardan belgeleri oluşturmak aynı diğer .NET Framework dillerinde, için. Diğer .NET Framework dillerde olduğu gibi [-doc derleyici seçeneği](https://msdn.microsoft.com/library/434394ae-0d4a-459c-a684-bffede519a04) gibi bir araç kullanarak belgeleme dönüştürebilirsiniz bilgilerini içeren bir XML dosyası üretebilir sayesinde [DocFX](https://dotnet.github.io/docfx/) veya [ Sandcastle](https://github.com/EWSoftware/SHFB). Diğer .NET Framework dillerinde genel olarak yazılır derlemeleri ile kullanılmak üzere tasarlanmış araçları kullanılarak oluşturulan belgeleri üzerinde derlenmiş formuna dayalı API'leri bir görünümünü oluşturmak F# oluşturur. Özellikle Destek Araçları sürece F#, bu araçları tarafından oluşturulan belgeleri eşleşmiyor F# görünümünü bir API.

XML'den belgeleri oluştur hakkında daha fazla bilgi için bkz: [XML belgeleri yorumları &#40;C&#35; Programming Guide&#41;](https://msdn.microsoft.com/library/b2s063f7).

## <a name="recommended-tags"></a>Önerilen etiketler

XML belgeleri yorumları yazmak için iki yolu vardır. Yalnızca XML etiketleri kullanmadan belgeleri doğrudan bir üç eğik çizgi açıklama yazmak için biridir. Bunu yaparsanız, tüm açıklama metni hemen izleyen kod yapısı için Özet belgeleri olarak alınır. Her yapı için yalnızca kısa bir özeti yazmak istediğinizde bu yöntemi kullanın. Diğer yöntem, yapılandırılmış belgeleri daha fazla bilgi sağlamak için XML etiketleri kullanmaktır. İkinci yöntem kısa bir özeti, ek açıklamalar, her bir parametre ve tür parametresi ve oluşturulan özel durumlar için belgeler ve dönüş değeri bir açıklaması için ayrı bir not belirtmenize olanak sağlar. Aşağıdaki tabloda, tanınan bir XML etiketleri açıklanmaktadır F# XML kodu açıklamalarını.

|Etiket sözdizimi|Açıklama|
|----------|-----------|
|**\<c\>**_metin_**\</c\>**|Belirten *metin* kodudur. Bu etiket, metin, kod için uygun bir yazı tipi görüntülemek için belgeleri Oluşturucuları tarafından kullanılabilir.|
|**\<Özet\>**_metin_ **\< /summary\>**|Belirten *metin* program öğesinin kısa açıklamasıdır. Genellikle bir veya iki cümle açıklamasıdır.|
|**\<Açıklamalar\>**_metin_ **\< /açıklamalar\>**|Belirten *metin* bir program öğesi hakkında ek bilgiler içerir.|
|**\<param name = "**_adı_**"\>**_açıklama_**\</param\>**|Bir işlev veya metot parametresi için bir açıklama ve adını belirtir.|
|**\<typeparam name = "**_adı_**"\>**_açıklama_**\</typeparam\>**|Bir tür parametresi için bir açıklama ve adını belirtir.|
|**\<döndürür\>**_metin_ **\< /döndürür\>**|Belirten *metin* dönüş değeri bir işlev veya metot açıklar.|
|**\<exception cref="**_type_**"\>**_description_**\</exception\>**|Oluşturulabilecek özel durum ve durum durumlarda türünü belirtir.|
|**\<see cref = "**_başvuru_**"\>**_metin_ **\< /bakın\>**|Başka bir program öğesi için satır içi bağlantı belirtir. *Başvuru* XML belge dosyası içinde görünen addır. *Metin* bağlantıya gösterilen metin.|
|**\<seealso cref="**_reference_**"/\>**|Başka bir türe yönelik belgelere ayrıca bağlantı belirtir. *Başvuru* XML belge dosyası içinde görünen addır. Ayrıca bkz: bağlantılar genellikle belgeleri sayfasının en altında görünür.|
|**\<para\>**_metin_**\</para\>**|Paragraf metni belirtir. Bu metin içinde ayırmak için kullanılan **açıklamalar** etiketi.|

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
