---
title: XML Belgeleri
description: Açıklamalardan belge oluşturmak F# için içindeki destek hakkında bilgi edinin.
ms.date: 05/16/2016
ms.openlocfilehash: 0a87915c361fc88f0c05264e1c17278fd656a167
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344686"
---
# <a name="xml-documentation"></a>XML Belgeleri

İçindeki F#Üçlü eğik çizgi (///) kod açıklamalarından belge oluşturabilirsiniz. XML açıklamaları, kod dosyaları (. FS) veya imza (. fsi) dosyalarındaki bildirimlerden önce olabilir.

## <a name="generating-documentation-from-comments"></a>Açıklamalardan belge oluşturma

Açıklamalardan belge F# oluşturmak için içindeki destek, diğer .NET Framework dilleridir. Diğer .NET Framework dillerde olduğu gibi, [-doc derleyici seçeneği](https://msdn.microsoft.com/library/434394ae-0d4a-459c-a684-bffede519a04) , [Docfx](https://dotnet.github.io/docfx/) veya [sandrole](https://github.com/EWSoftware/SHFB)gibi bir araç kullanarak belgelere dönüştürebileceğiniz bilgiler içeren bir XML dosyası üretmenizi sağlar. Diğer .NET Framework dillerde yazılmış derlemelerle birlikte kullanılmak üzere tasarlanan araçlar kullanılarak oluşturulan belgeler, genellikle derlenen F# yapı biçimine dayalı API 'lerin bir görünümünü oluşturur. Araçların özellikle desteği F#yoksa, bu araçlar tarafından oluşturulan belgeler bir API F# görünümüyle eşleşmez.

XML 'den belge oluşturma hakkında daha fazla bilgi için bkz. [XML belge açıklamaları &#40;&#35; C Programlama Kılavuzu&#41;](https://msdn.microsoft.com/library/b2s063f7).

## <a name="recommended-tags"></a>Önerilen Etiketler

XML belgesi açıklamalarını yazmanın iki yolu vardır. Bunlardan biri, XML etiketleri kullanmadan doğrudan Üçlü eğik çizgi açıklamasında belge yazmak olacaktır. Bunu yaparsanız, tüm açıklama metni hemen izleyen kod yapısına ait Özet belgeler olarak alınır. Her yapı için yalnızca kısa bir özet yazmak istediğinizde bu yöntemi kullanın. Diğer yöntem, daha fazla yapılandırılmış belge sağlamak için XML etiketlerini kullanmaktır. İkinci yöntem, kısa bir Özet, ek açıklamalar, her bir parametre ve tür parametresi ve oluşturulan özel durumlar için belgeler ve dönüş değerinin bir açıklaması için ayrı notlar belirlemenizi sağlar. Aşağıdaki tabloda F# XML kodu açıklamalarında tanınan XML etiketleri açıklanmaktadır.

|Etiket sözdizimi|Açıklama|
|----------|-----------|
|**\<c\>** _text_ **\</c\>**|*Metnin* kod olduğunu belirtir. Bu etiket, kod için uygun bir yazı tipinde metin göstermek üzere belge üreticileri tarafından kullanılabilir.|
|**\<özet\>** _metin_ **\</Summary\>**|*Metnin* program öğesinin kısa bir açıklaması olduğunu belirtir. Açıklama genellikle bir veya iki cümle olur.|
|**\<açıklamalar\>** _metin_ **\</açıklamalar\>**|*Metnin* program öğesiyle ilgili ek bilgileri içerdiğini belirtir.|
|**\<param Name = "** _ad_ **"\>** _Description_ **\</param\>**|Bir işlev veya yöntem parametresi için ad ve açıklama belirtir.|
|**\<typeparam Name = "** _ad_ **"\>** _Description_ **\</typeparam\>**|Bir tür parametresi için ad ve açıklama belirtir.|
|**\<\>** _metin_ döndürür **\</dönüşler\>**|*Metnin* bir işlevin veya yöntemin dönüş değerini açıklamakta olduğunu belirtir.|
|**\<Exception cref = "** _tür_ **"\>** _Description_ **\</Exception\>**|Üretilene özel durum türünü ve bunun altında oluşturulduğu koşulları belirtir.|
|**\<bkz. cref = "** _Reference_ **"\>** _metin_ **\</See\>**|Başka bir program öğesinin satır içi bağlantısını belirtir. *Başvuru* , XML belge dosyasında göründüğü şekliyle addır. *Metin* , bağlantıda gösterilen metindir.|
|**\<seede cref = "** _başvuru_ **"/\>**|Ayrıca bkz. başka bir tür için belgelere bağlantı bağlantısı. *Başvuru* , XML belge dosyasında göründüğü şekliyle addır. Ayrıca bkz. bağlantılar genellikle belge sayfasının alt kısmında görünür.|
|**\<paragraf\>** _metin_ **\</para\>**|Metnin paragrafını belirtir. Bu, **açıklamalar** etiketinin içindeki metni ayırmak için kullanılır.|

## <a name="example"></a>Örnek

### <a name="description"></a>Açıklama

Aşağıda, bir imza dosyasındaki tipik bir XML belgesi yorumu verilmiştir.

### <a name="code"></a>Kod

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7101.fs)]

## <a name="example"></a>Örnek

### <a name="description"></a>Açıklama

Aşağıdaki örnek, XML etiketleri olmadan alternatif yöntemi gösterir. Bu örnekte, açıklama içindeki metnin tamamı bir Özet olarak değerlendirilir. Açıkça bir Özet etiketi belirtmemelisiniz **param** veya etiket **döndüren** Etiketler gibi başka Etiketler belirtmemelisiniz.

### <a name="code"></a>Kod

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7102.fs)]

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
- [Derleyici Seçenekleri](compiler-options.md)
