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
ms.openlocfilehash: 92bf49ac1ae67fb8d2e268eeaaf63cd72d9f6251
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458805"
---
# <a name="xml-character-entities-and-xaml"></a>XML Karakter Varlıkları ve XAML
XAML, XML 'de özel karakterler için tanımlanan karakter varlıklarını kullanır. Bu konuda bazı belirli karakter varlıkları ve XAML 'deki diğer XML kavramları için genel konular açıklanmaktadır.  
  
<a name="character_entities_and_escaping_issues_that_are_unique_to_xaml"></a>   
## <a name="character-entities-and-escaping-issues-that-are-unique-to-xaml"></a>XAML 'e özgü karakter varlıkları ve kaçış sorunları  
 XAML biçimlendirmesi genellikle XML 'de tanımlanan karakter varlıklarını ve kaçış dizilerini kullanır.  
  
 Ana özel durum, parantez içinde ({ve}), parantez içine alınmış bir karakter sırasının bir biçimlendirme uzantısı olarak yorumlanmalıdır. Biçimlendirme uzantıları hakkında daha fazla bilgi için bkz. [xaml Için biçimlendirme uzantıları genel bakış](markup-extensions-for-xaml-overview.md).  
  
 Ancak, XML yerine XAML için özel bir kaçış sırası kullanarak, ayraçları sabit karakter olarak görüntülemeye devam edebilirsiniz. Daha fazla bilgi için bkz. [{} kaçış sırası-biçimlendirme uzantısı](escape-sequence-markup-extension.md).  
  
 Ters eğik çizgi (\\) bir dize olarak işlendiği zaman bir kaçış sırası gerektirmediğini unutmayın.  
  
<a name="xml_character_entities"></a>   
## <a name="xml-character-entities"></a>XML karakter varlıkları  
 Daha önce belirtildiği gibi, genellikle XAML işaretlemesini yazmak için kullanılan karakter varlıklarının ve kaçış sıralarının çoğu XML tarafından tanımlanır. Bu konu, bu varlıkların tüm listesini sağlamaz; varlıklar için ayrıntılı bir başvuru, XML belirtimleri gibi dış belgelerde bulunabilir. Ancak kolaylık sağlaması için, bu konuda genellikle XAML biçimlendirmesinde kullanılan belirli XML karakter varlıklarının bazıları listelenmektedir.  
  
|Karakter|Varlık|Notlar|  
|---------------|------------|-----------|  
|& (ve işareti)|\&amp;|Hem öznitelik değerleri hem de bir öğenin içeriği için kullanılmalıdır.|  
|> (büyüktür karakteri)|\&gt;|Bir öznitelik değeri için kullanılmalıdır, ancak > bir öğenin içeriği olarak kabul edilebilir, bu, < önünde olmadığı sürece.|  
|< (küçüktür karakteri)|\&lt;|Bir öznitelik değeri için kullanılmalıdır, ancak \<, > takip edimediğinden bir öğenin içeriği olarak kabul edilebilir.|  
|"(düz tırnak işareti)|\&quot;|Bir öznitelik değeri için kullanılmalıdır, ancak düz tırnak işareti (") bir öğenin içeriği olarak kabul edilebilir. Öznitelik değerlerinin tek bir düz tırnak işareti (') veya düz tırnak işareti (") ile (")) alınbileceğine unutmayın. önce hangi karakter görünür, öznitelik değeri Kasası tanımlar ve alternatif teklif, değer içinde değişmez değer olarak kullanılabilir.|  
|' (tek düz tırnak işareti)|\&apos;|Bir öznitelik değeri için kullanılmalıdır, ancak tek bir düz tırnak işareti (') bir öğenin içeriği olarak kabul edilebilir. Öznitelik değerlerinin tek bir düz tırnak işareti (') veya düz tırnak işareti (") ile (")) alınbileceğine unutmayın. önce hangi karakter görünür, öznitelik değeri Kasası tanımlar ve alternatif teklif, değer içinde değişmez değer olarak kullanılabilir.|  
|(sayısal karakter eşlemeleri)|&# *[tamsayı]* ; veya & #x *[onaltılı]* ;|XAML, etkin olan kodlamaya sayısal karakter eşlemelerini destekler.|  
|(bölünemez boşluk)|&\#160; (UTF-8 kodlaması varsayılıyor)|Flow belge öğeleri veya WPF <xref:System.Windows.Controls.TextBox>gibi metinler alan öğeler için, `xml:space="default"`için bile, bölünemez boşluklar işaretlemenin dışında normalleştirilmez. (Daha fazla bilgi için bkz. [xaml 'de beyaz boşluk işleme](whitespace-processing-in-xaml.md).)|  
  
<a name="xml_comment_format"></a>   
## <a name="xml-comment-format"></a>XML açıklama biçimi  
 XAML, XML açıklama biçimini kullanır: açıklamanın başlangıcı `<!--`, açıklama sonu `-->,` ve sıra `--` açıklama içinde gerçekleşmemelidir.  
  
<a name="xml_processing_instructions"></a>   
## <a name="xml-processing-instructions"></a>XML Işleme yönergeleri  
 XAML XML işleme talimatlarını XML belirtimlerine göre işler, bu durum yönergelerin geçirilmesi gereken durumdur. .NET Framework XAML hizmetlerinde XAML işleme hiçbir işlem yönergesi kullanmaz. XAML kullanan diğer mevcut çerçeveler de XAML 'den işleme yönergelerini kullanmaz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XAML'ye Genel Bakış (WPF)](../../desktop-wpf/fundamentals/xaml.md)
- [İşaretleme Uzantıları ve WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
- [XamlName Dilbilgisi](xamlname-grammar.md)
- [XAML 'de boşluk işleme](whitespace-processing-in-xaml.md)
