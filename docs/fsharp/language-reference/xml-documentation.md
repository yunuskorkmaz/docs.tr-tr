---
title: XML Belgeleri (F#)
description: "F # destek açıklamalardan belgeleri oluşturmak için öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: d99ab1b6-e170-4ec2-a543-43ea7ab15bb2
ms.openlocfilehash: 20768a7d4ea17c926318043f658691819a3d7d2f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="xml-documentation"></a>XML Belgeleri

Üçlü-eğik çizgi (/ / /) belgelerinden üretebilir kod açıklamalarını F #. XML açıklamaları kod dosyaları (.fs) veya imza (.fsi) dosyalarını bildirimlerden önce.


## <a name="generating-documentation-from-comments"></a>Açıklamalardan belgeleri oluşturma
Belgeleri açıklamalardan oluşturma desteği F # diğer .NET Framework dillerde aynıdır. Diğer .NET Framework diller olduğu gibi [-doc derleyici seçeneği](https://msdn.microsoft.com/library/434394ae-0d4a-459c-a684-bffede519a04) Sandcastle gibi bir araç kullanarak belge dönüştürebilirsiniz bilgilerini içeren bir XML dosyası üretmek sağlar. Diğer .NET Framework dillerde genellikle yazılır derlemeler ile kullanılmak üzere tasarlanmış araçlar kullanılarak oluşturulan belgeleri derlenmiş F # yapılarını formdaki tabanlı API'ler bir görünümünü oluşturur. Özellikle F # Destek Araçları sürece, bu araçları tarafından oluşturulan belgeleri F # görünümünü bir API eşleşmiyor.

XML'den belgeleri oluşturma hakkında daha fazla bilgi için bkz: [XML belgeleri yorumları &#40; C &#35; Programlama Kılavuzu &#41; ](https://msdn.microsoft.com/library/b2s063f7).


## <a name="recommended-tags"></a>Önerilen etiketler
XML belgeleri yorumları yazmak için iki yolu vardır. Bir yalnızca belgeleri doğrudan bir eğik çizgi Üçlü açıklama XML etiketleri kullanmadan yazmaktır. Bunu yaparsanız, tüm açıklama metni hemen izleyen kod yapı Özet belgelerine olarak alınır. Her bir yapı için yalnızca kısa bir özeti yazmak istediğinizde bu yöntemi kullanın. Başka bir yöntem daha yapılandırılmış belgelerine sağlamak için XML etiketleri kullanmaktır. İkinci yöntem, kısa bir özeti, ek açıklamalar, her bir parametre ve tür parametresi ve oluşturulan özel durumları için belgeleri ve dönüş değeri açıklaması için ayrı notları belirtmenize olanak sağlar. Aşağıdaki tabloda, F # XML kodu açıklamaları tanınır XML etiketleri açıklanmaktadır.



|Etiket sözdizimi|Açıklama|
|----------|-----------|
|**&lt;c&gt;***metin***&lt;/c&gt;**|Belirleyen *metin* kodudur. Bu etiket metin kodu için uygun bir yazı tipi görüntülemek için belgelerine oluşturucular tarafından kullanılabilir.|
|**&lt;Özet&gt;***metin* **&lt; /özeti&gt;**|Belirleyen *metin* program öğesinin kısa açıklamasıdır. Genellikle bir veya iki cümle açıklamasıdır.|
|**&lt;Açıklamalar&gt;***metin* **&lt; /açıklamalar&gt;**|Belirleyen *metin* bir program öğesi ilgili ek bilgiler içerir.|
|**&lt;param name = "***adı***"&gt;***açıklama***&lt;/param&gt;**|Bir işlev veya yöntem parametresi için bir açıklama ve adını belirtir.|
|**&lt;typeparam name = "***adı***"&gt;***açıklama***&lt;/typeparam&gt;**|Tür parametresi için bir açıklama ve adını belirtir.|
|**&lt;döndürür&gt;***metin* **&lt; /döndürür&gt;**|Belirleyen *metin* bir işlev veya yöntem dönüş değerini açıklar.|
|**&lt;özel durum cref = "***türü***"&gt;***açıklama***&lt;/exception&gt;**|Oluşturulabilecek özel durumu ve durum durumlarda türünü belirtir.|
|**&lt;see cref = "***başvuru***"&gt;***metin* **&lt; /bakın&gt;**|Başka bir program öğesi için bir satır içi bağlantı belirtir. *Başvuru* XML belge dosyası içinde görünen addır. *Metin* bağlantıyı gösterilen metin.|
|**&lt;SeeAlso cref = "***başvuru***" /&gt;**|Başka bir tür için belgelerine ayrıca bağlantı belirtir. *Başvuru* XML belge dosyası içinde görünen addır. Ayrıca bkz: bağlantılar genellikle bir belge sayfasının alt kısmında görüntülenir.|
|**&lt;para&gt;***metin***&lt;/para&gt;**|Paragraf metni belirtir. Bu metin içinde ayırmak için kullanılan **açıklamalar** etiketi.|

## <a name="example"></a>Örnek

### <a name="description"></a>Açıklama
Bir imza dosyası tipik bir XML belgeleri açıklamada verilmiştir.


### <a name="code"></a>Kod
[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7101.fs)]
    
## <a name="example"></a>Örnek

### <a name="description"></a>Açıklama
Aşağıdaki örnek XML etiketleri olmadan alternatif bir yöntemi gösterir. Bu örnekte, tüm metin açıklamasında bir Özet olarak kabul edilir. Summary etiketi açıkça belirtmezseniz, diğer etiketler gibi belirtilmemelidir olduğunu Not **param** veya **döndürür** etiketler.


### <a name="code"></a>Kod
[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7102.fs)]
    
## <a name="see-also"></a>Ayrıca Bkz.
[F # dili başvurusu](index.md)

[Derleyici Seçenekleri](compiler-options.md)
