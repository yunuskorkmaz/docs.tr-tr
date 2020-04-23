---
title: XML Karakter Varlıkları ve XAML
ms.date: 03/30/2017
f1_keywords:
- '&'
- '&amp'
- '&gt'
- '&lt'
helpviewer_keywords:
- XAML [XAML Services], special characters
- ampersand (&) [XAML Services]
- special characters [XAML Services]
- apostrophe (') [XAML Services]
- greater-than (>) character [XAML Services]
- XAML [XAML Services], quotation mark (")
- XAML [XAML Services], apostrophe (')
- '& (ampersand) [XAML Services]'
- XAML [XAML Services], & (ampersand)
- XAML [XAML Services], escape sequence
- quotation mark (") [XAML Services]
- less-than (<) character [XAML Services]
ms.assetid: 6896d0ce-74f7-420a-9ab4-de9bbf390e8d
ms.openlocfilehash: aff96c5d0ee6bbf2bbe2f9e3b3ae091caa781f7a
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071460"
---
# <a name="xml-character-entities-and-xaml"></a>XML Karakter Varlıkları ve XAML

XAML, özel karakterler için XML'de tanımlanan karakter varlıklarını kullanır. Bu konu, XAML'deki diğer XML kavramları için bazı özel karakter varlıklarını ve genel hususları açıklar.

## <a name="character-entities-and-escaping-issues-that-are-unique-to-xaml"></a>XAML'ye Özgü Karakter Varlıkları ve Kaçış Sorunları

XAML biçimlendirmesi genellikle XML'de tanımlanan aynı karakter varlıklarını ve kaçış dizilerini kullanır.

Bunun temel istisnası, parantezlerin ({ ve }) XAML'de anlamlı olmasıdır, çünkü bu karakterler bir XAML işlemciye, ayraçlarla çevrili bir karakter dizisinin biçimlendirme uzantısı olarak yorumlanması gerektiğini bildirir. Biçimlendirme uzantıları hakkında daha fazla bilgi için [XAML Genel Bakış için Biçimlendirme Uzantıları'na](markup-extensions-overview.md)bakın.

Ancak, XML yerine XAML'ye özgü bir kaçış dizisi kullanarak ayraçları gerçek karakterler olarak görüntülemeye devam edebilirsiniz. Daha fazla bilgi için [ {} Escape Sequence - Biçimlendirme Uzantısı'na](escape-sequence-markup-extension.md)bakın.

Bir ters eğik\\çizgi ( ) dize olarak işlendiğinde bir kaçış sırası gerektirmediğini unutmayın.

## <a name="xml-character-entities"></a>XML Karakter Varlıkları

Daha önce de belirtildiği gibi, genellikle XAML biçimlendirmesi yazmak için kullanılan çoğu karakter varlıkları ve kaçış dizileri XML tarafından tanımlanır. Bu konu, bu varlıkların tam listesini sağlamaz; varlıklar için ayrıntılı bir başvuru xml belirtimleri gibi dış belgelerde bulunabilir. Ancak, kolaylık sağlamak için, bu konu genellikle XAML biçimlendirmesinde kullanılan belirli XML karakter varlıklarından bazılarını listeler.

|Karakter|Varlık|Notlar|
|---------------|------------|-----------|
|& (ampersand)|\&amp;|Öznitelik değerleri ve bir öğenin içeriği için hem kullanılmalıdır.|
|> (karakterden büyüktür)|\&gt;|Bir öznitelik değeri için kullanılmalıdır, ancak < önce olmadığı sürece bir öğenin içeriği olarak > kabul edilebilir.|
|< (karakterden az)|\&lt;|Bir öznitelik değeri için kullanılmalıdır, ancak \< > takip etmediği sürece bir öğenin içeriği olarak kabul edilebilir.|
|" (düz tırnak işareti)|\&quot;|Bir öznitelik değeri için kullanılmalıdır, ancak düz bir tırnak işareti (") bir öğenin içeriği olarak kabul edilebilir. Öznitelik değerlerinin tek bir düz tırnak işareti (') veya düz bir tırnak işareti (") ile eklenebilir olduğunu unutmayın; hangi karakter görünürse görünün, önce öznitelik değeri muhafazasını tanımlar ve alternatif teklif daha sonra değer içinde gerçek bir değer olarak kullanılabilir.|
|' (tek düz tırnak işareti)|\&apos;|Bir öznitelik değeri için kullanılmalıdır, ancak tek bir düz tırnak işareti (') bir öğenin içeriği olarak kabul edilebilir. Öznitelik değerlerinin tek bir düz tırnak işareti (') veya düz bir tırnak işareti (") ile eklenebilir olduğunu unutmayın; hangi karakter görünürse görünün, önce öznitelik değeri muhafazasını tanımlar ve alternatif teklif daha sonra değer içinde gerçek bir değer olarak kullanılabilir.|
|(sayısal karakter eşlemeleri)|&#*[integer]*; veya &#x *[hex]*;|XAML, etkin olan kodlamaya sayısal karakter eşlemelerini destekler.|
|(kırılmayan boşluk)|&\#160; (UTF-8 kodlama varsayarak)|Akış belge öğeleri veya WPF <xref:System.Windows.Controls.TextBox>gibi metin alan öğeler için, `xml:space="default"`kırılmayan boşluklar biçimlendirme dışında normalleştirilmeyecektir, hatta . (Daha fazla bilgi için [XAML'de Beyaz alan işlemeye](white-space-processing.md)bakın.)|

## <a name="xml-comment-format"></a>XML Yorum Biçimi

XAML XML yorum biçimini kullanır: yorumun `<!--`başlangıcı, yorumun `-->,` sonudur `--` ve dizi yorum içinde oluşmamalıdır.

## <a name="xml-processing-instructions"></a>XML İşleme Talimatları

XAML, XML belirtimlerine göre XML işleme yönergelerini işler ve bu yönergelerin geçirilmesi gerektiğini belirtir. .NET XAML Hizmetleri'nde XAML işleme herhangi bir işlem talimatı kullanmaz. XAML kullanan diğer varolan çerçeveler de XAML'nin işleme yönergelerini kullanmaz.

## <a name="see-also"></a>Ayrıca bkz.

- [XAML'ye Genel Bakış (WPF)](../fundamentals/xaml.md)
- [Biçimlendirme Uzantıları ve WPF XAML](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
- [XamlName Dilbilgisi](xamlname-grammar.md)
- [XAML'de Boşluk İşleme](white-space-processing.md)
