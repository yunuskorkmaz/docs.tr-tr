---
title: XML Belgeleri (F#)
description: Açıklamalardan belge oluşturmak F# için içindeki destek hakkında bilgi edinin.
ms.date: 05/16/2016
ms.openlocfilehash: b89ab4117f4dd71126f8e203f4a5271ab3c30021
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630826"
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
|**cmetni\>/c \<** **\<\>**|*Metnin* kod olduğunu belirtir. Bu etiket, kod için uygun bir yazı tipinde metin göstermek üzere belge üreticileri tarafından kullanılabilir.|
| **Özet\<metni\>** **/Özet\<\>**|*Metnin* program öğesinin kısa bir açıklaması olduğunu belirtir. Açıklama genellikle bir veya iki cümle olur.|
| **açıklamalar\<metni\>** **/açıklamalar\<\>**|*Metnin* program öğesiyle ilgili ek bilgileri içerdiğini belirtir.|
|**\>** **paramName\> = "ad"Açıklama\</param**  **\<**|Bir işlev veya yöntem parametresi için ad ve açıklama belirtir.|
|**\>** **\> typeparamName\<** = "ad" Açıklama/typeparam  **\<**|Bir tür parametresi için ad ve açıklama belirtir.|
|**/döndürüyormetnini\> döndürür\<**  **\<\>**|*Metnin* bir işlevin veya yöntemin dönüş değerini açıklamakta olduğunu belirtir.|
|**\>** **\> Exception cref=\<** "tür" açıklama/özel durum  **\<**|Üretilene özel durum türünü ve bunun altında oluşturulduğu koşulları belirtir.|
|**\>** **\<bkz.cref\>**  = "başvuru" metni/See  **\<**|Başka bir program öğesinin satır içi bağlantısını belirtir. *Başvuru* , XML belge dosyasında göründüğü şekliyle addır. *Metin* , bağlantıda gösterilen metindir.|
|**\>**   **\<SeeAlso cref = "** başvuru"/|Ayrıca bkz. başka bir tür için belgelere bağlantı bağlantısı. *Başvuru* , XML belge dosyasında göründüğü şekliyle addır. Ayrıca bkz. bağlantılar genellikle belge sayfasının alt kısmında görünür.|
| **paragraf\<metni\>** **/para\<\>**|Metnin paragrafını belirtir. Bu, **açıklamalar** etiketinin içindeki metni ayırmak için kullanılır.|

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
