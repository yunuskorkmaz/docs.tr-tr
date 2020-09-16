---
title: XML Belgeleri
description: "Açıklamalardan belge oluşturmak için F # ' da destek hakkında bilgi edinin."
ms.date: 05/16/2016
ms.openlocfilehash: 03d14cef910d149f0c7a2f3a49c8cf4606ac5305
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556583"
---
# <a name="xml-documentation"></a>XML Belgeleri

F # ' da Üçlü eğik çizgi (///) kod açıklamalarından belgeler oluşturabilirsiniz. XML açıklamaları, kod dosyaları (. FS) veya imza (. fsi) dosyalarındaki bildirimlerden önce olabilir.

## <a name="generating-documentation-from-comments"></a>Açıklamalardan belge oluşturma

Açıklamalardan belge oluşturmak için F # desteği diğer .NET Framework dilleridir. Diğer .NET Framework dillerde olduğu gibi, [-doc derleyici seçeneği](./compiler-options.md) , [Docfx](https://dotnet.github.io/docfx/) veya [sandrole](https://github.com/EWSoftware/SHFB)gibi bir araç kullanarak belgelere dönüştürebileceğiniz bilgiler içeren bir XML dosyası üretmenizi sağlar. Diğer .NET Framework dillerde yazılmış derlemelerle birlikte kullanılmak üzere tasarlanan araçlar kullanılarak oluşturulan belgeler, genellikle F # yapıları derlenmiş biçimini temel alan API 'lerin bir görünümünü oluşturur. Araçlar F # ' ı özellikle desteklemediği takdirde, bu araçlar tarafından oluşturulan belgeler bir API 'nin F # görünümüyle eşleşmez.

XML 'den belge oluşturma hakkında daha fazla bilgi için bkz. [XML belge açıklamaları &#40;C&#35; programlama kılavuzu&#41;](../../csharp/programming-guide/xmldoc/index.md).

## <a name="recommended-tags"></a>Önerilen Etiketler

XML belgesi açıklamalarını yazmanın iki yolu vardır. Bunlardan biri, XML etiketleri kullanmadan doğrudan Üçlü eğik çizgi açıklamasında belge yazmak olacaktır. Bunu yaparsanız, tüm açıklama metni hemen izleyen kod yapısına ait Özet belgeler olarak alınır. Her yapı için yalnızca kısa bir özet yazmak istediğinizde bu yöntemi kullanın. Diğer yöntem, daha fazla yapılandırılmış belge sağlamak için XML etiketlerini kullanmaktır. İkinci yöntem, kısa bir Özet, ek açıklamalar, her bir parametre ve tür parametresi ve oluşturulan özel durumlar için belgeler ve dönüş değerinin bir açıklaması için ayrı notlar belirlemenizi sağlar. Aşağıdaki tabloda, F # XML kod açıklamalarında tanınan XML etiketleri açıklanmaktadır.

|Etiket sözdizimi|Description|
|----------|-----------|
|**\<c\>**_metinleri_**\</c\>**|*Metnin* kod olduğunu belirtir. Bu etiket, kod için uygun bir yazı tipinde metin göstermek üzere belge üreticileri tarafından kullanılabilir.|
|**\<summary\>**_metinleri_**\</summary\>**|*Metnin* program öğesinin kısa bir açıklaması olduğunu belirtir. Açıklama genellikle bir veya iki cümle olur.|
|**\<remarks\>**_metinleri_**\</remarks\>**|*Metnin* program öğesiyle ilgili ek bilgileri içerdiğini belirtir.|
|**\<param name="**_name_**"\>**_açıklaması_**\</param\>**|Bir işlev veya yöntem parametresi için ad ve açıklama belirtir.|
|**\<typeparam name="**_name_**"\>**_açıklaması_**\</typeparam\>**|Bir tür parametresi için ad ve açıklama belirtir.|
|**\<returns\>**_metinleri_**\</returns\>**|*Metnin* bir işlevin veya yöntemin dönüş değerini açıklamakta olduğunu belirtir.|
|**\<exception cref="**_type_**"\>**_açıklaması_**\</exception\>**|Üretilene özel durum türünü ve bunun altında oluşturulduğu koşulları belirtir.|
|**\<see cref="**_reference_**"\>**_metinleri_**\</see\>**|Başka bir program öğesinin satır içi bağlantısını belirtir. *Başvuru* , XML belge dosyasında göründüğü şekliyle addır. *Metin* , bağlantıda gösterilen metindir.|
|**\<seealso cref="**_reference_**"/\>**|Ayrıca bkz. başka bir tür için belgelere bağlantı bağlantısı. *Başvuru* , XML belge dosyasında göründüğü şekliyle addır. Ayrıca bkz. bağlantılar genellikle belge sayfasının alt kısmında görünür.|
|**\<para\>**_metinleri_**\</para\>**|Metnin paragrafını belirtir. Bu, **açıklamalar** etiketinin içindeki metni ayırmak için kullanılır.|

## <a name="example"></a>Örnek

### <a name="description"></a>Description

Aşağıda, bir imza dosyasındaki tipik bir XML belgesi yorumu verilmiştir.

### <a name="code"></a>Kod

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7101.fs)]

## <a name="example"></a>Örnek

### <a name="description"></a>Description

Aşağıdaki örnek, XML etiketleri olmadan alternatif yöntemi gösterir. Bu örnekte, açıklama içindeki metnin tamamı bir Özet olarak değerlendirilir. Açıkça bir Özet etiketi belirtmemelisiniz **param** veya etiket **döndüren** Etiketler gibi başka Etiketler belirtmemelisiniz.

### <a name="code"></a>Kod

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7102.fs)]

## <a name="see-also"></a>Ayrıca bkz.

- [F # dil başvurusu](index.md)
- [Derleyici seçenekleri](compiler-options.md)
