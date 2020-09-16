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
ms.openlocfilehash: 1ba99cda512bc5e18c646b09f26672a39c1cf53c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90548198"
---
# <a name="xml-character-entities-and-xaml"></a>XML Karakter Varlıkları ve XAML

XAML, XML 'de özel karakterler için tanımlanan karakter varlıklarını kullanır. Bu konuda bazı belirli karakter varlıkları ve XAML 'deki diğer XML kavramları için genel konular açıklanmaktadır.

## <a name="character-entities-and-escaping-issues-that-are-unique-to-xaml"></a>XAML 'e özgü karakter varlıkları ve kaçış sorunları

XAML biçimlendirmesi genellikle XML 'de tanımlanan karakter varlıklarını ve kaçış dizilerini kullanır.

Ana özel durum, parantez içinde ({ve}), parantez içine alınmış bir karakter sırasının bir biçimlendirme uzantısı olarak yorumlanmalıdır. Biçimlendirme uzantıları hakkında daha fazla bilgi için bkz. [xaml Için biçimlendirme uzantıları genel bakış](markup-extensions-overview.md).

Ancak, XML yerine XAML için özel bir kaçış sırası kullanarak, ayraçları sabit karakter olarak görüntülemeye devam edebilirsiniz. Daha fazla bilgi için bkz. [ {} kaçış sırası-işaretleme uzantısı](escape-sequence-markup-extension.md).

Bir ters eğik çizgi ( \\ ) dize olarak işlendiği zaman bir kaçış sırası gerektirmediğini unutmayın.

## <a name="xml-character-entities"></a>XML karakter varlıkları

Daha önce belirtildiği gibi, genellikle XAML işaretlemesini yazmak için kullanılan karakter varlıklarının ve kaçış sıralarının çoğu XML tarafından tanımlanır. Bu konu, bu varlıkların tüm listesini sağlamaz; varlıklar için ayrıntılı bir başvuru, XML belirtimleri gibi dış belgelerde bulunabilir. Ancak kolaylık sağlaması için, bu konuda genellikle XAML biçimlendirmesinde kullanılan belirli XML karakter varlıklarının bazıları listelenmektedir.

|Karakter|Varlık|Notlar|
|---------------|------------|-----------|
|& (ve işareti)|\&amp|Hem öznitelik değerleri hem de bir öğenin içeriği için kullanılmalıdır.|
|> (büyüktür karakteri)|\&>|Bir öznitelik değeri için kullanılmalıdır, ancak > bir öğenin içeriği olarak kabul edilebilir, bu, < önünde olmadığı sürece.|
|< (küçüktür karakteri)|\&itme|Bir öznitelik değeri için kullanılmalıdır, ancak \< is acceptable as the content of an element as long as > bunu takip etmez.|
|"(düz tırnak işareti)|\&quot;|Bir öznitelik değeri için kullanılmalıdır, ancak düz tırnak işareti (") bir öğenin içeriği olarak kabul edilebilir. Öznitelik değerlerinin tek bir düz tırnak işareti (') veya düz tırnak işareti (") ile (")) alınbileceğine unutmayın. önce hangi karakter görünür, öznitelik değeri Kasası tanımlar ve alternatif teklif, değer içinde değişmez değer olarak kullanılabilir.|
|' (tek düz tırnak işareti)|\&apos|Bir öznitelik değeri için kullanılmalıdır, ancak tek bir düz tırnak işareti (') bir öğenin içeriği olarak kabul edilebilir. Öznitelik değerlerinin tek bir düz tırnak işareti (') veya düz tırnak işareti (") ile (")) alınbileceğine unutmayın. önce hangi karakter görünür, öznitelik değeri Kasası tanımlar ve alternatif teklif, değer içinde değişmez değer olarak kullanılabilir.|
|(sayısal karakter eşlemeleri)|&#*[tamsayı]*; veya & # x *[onaltılı]*;|XAML, etkin olan kodlamaya sayısal karakter eşlemelerini destekler.|
|(bölünemez boşluk)|&\#160; (UTF-8 kodlaması varsayılıyor)|Flow belge öğeleri için veya WPF gibi metin alan öğeler için <xref:System.Windows.Controls.TextBox> bile, bölünemez boşluklar biçimlendirme dışında normalleştirilmez `xml:space="default"` . (Daha fazla bilgi için bkz. [xaml 'de beyaz boşluk işleme](white-space-processing.md).)|

## <a name="xml-comment-format"></a>XML açıklama biçimi

XAML, XML açıklama biçimini kullanır: açıklamanın başlangıcı `<!--` , açıklamanın sonu ise `-->,` ve sıra `--` Açıklama içinde gerçekleşmemelidir.

## <a name="xml-processing-instructions"></a>XML Işleme yönergeleri

XAML XML işleme talimatlarını XML belirtimlerine göre işler, bu durum yönergelerin geçirilmesi gereken durumdur. .NET XAML hizmetlerinde XAML işleme hiçbir işlem yönergesi kullanmaz. XAML kullanan diğer mevcut çerçeveler de XAML 'den işleme yönergelerini kullanmaz.

## <a name="see-also"></a>Ayrıca bkz.

- [XAML'ye Genel Bakış (WPF)](../fundamentals/xaml.md)
- [Biçimlendirme Uzantıları ve WPF XAML](/dotnet/desktop/wpf/advanced/markup-extensions-and-wpf-xaml)
- [XamlName Dilbilgisi](xamlname-grammar.md)
- [XAML'de Boşluk İşleme](white-space-processing.md)
