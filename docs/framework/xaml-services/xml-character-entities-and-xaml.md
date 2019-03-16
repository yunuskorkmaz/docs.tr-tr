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
ms.openlocfilehash: 3fefbe9696ba7618dc811c6ac8f600bb6322dad5
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2019
ms.locfileid: "58048052"
---
# <a name="xml-character-entities-and-xaml"></a>XML Karakter Varlıkları ve XAML
XAML, XML'de özel karakterler için tanımlanan karakter varlıkları kullanır. Bu konuda, bazı belirli karakter varlıkları ve XAML içinde diğer XML kavramları yönelik genel konular açıklanmaktadır.  
  
<a name="character_entities_and_escaping_issues_that_are_unique_to_xaml"></a>   
## <a name="character-entities-and-escaping-issues-that-are-unique-to-xaml"></a>Karakter varlıkları ve XAML için benzersiz bir kaçış sorunları  
 XAML işaretleme genellikle aynı karakter varlıkları ve XML içinde tanımlanan çıkış sıraları kullanır.  
  
 Ana istisnadır, küme ayraçları ({ve}) bu karakterler kaşlı ayraç içine alınmış bir karakter dizisi bir işaretleme uzantısı anlaşılması gereken bir XAML işlemci bildirmek için XAML içinde önemi yoktur. Biçimlendirme uzantıları hakkında daha fazla bilgi için bkz: [genel XAML işaretleme uzantılarına](markup-extensions-for-xaml-overview.md).  
  
 Ancak, yine de küme ayraçları değişmez karakterler XAML XML yerine özel bir kaçış dizisi kullanarak görüntüleyebilirsiniz. Daha fazla bilgi için [ {} kaçış sırası - işaretleme uzantısı](escape-sequence-markup-extension.md).  
  
 Unutmayın, ters eğik çizgi (\\) bir dize olarak işlendiğinde bir kaçış dizisi gerektirmez.  
  
<a name="xml_character_entities"></a>   
## <a name="xml-character-entities"></a>XML karakter varlıkları  
 Çoğu karakter varlıkları ve XAML biçimlendirme yazmak için genellikle kullanılan kaçış dizileri, daha önce belirtildiği gibi XML tarafından tanımlanır. Bu konuda, bu varlıkların tam listesi sağlamaz; varlıklar için ayrıntılı bir başvuru dış belgelerinde gibi XML belirtimlerinde bulunabilir. Ancak, kolaylık sağlamak için bu konuda genellikle XAML biçimlendirmede kullanılan belirli bir XML karakter varlıkları bazıları listelenmiştir.  
  
|Karakter|Varlık|Notlar|  
|---------------|------------|-----------|  
|& (ve işareti)|\&amp;|Öznitelik değerleri için hem de bir öğenin içeriğini için kullanılmalıdır.|  
|> (büyük-karakter fazla)|\&gt;|Bir öznitelik değeri için kullanılması gerekir ancak > kabul edilebilir bir öğenin sağlandığı sürece içerik olarak < önce gelmez.|  
|< (az-karakter fazla)|\&lt;|Bir öznitelik değeri için kullanılması gerekir ancak \< öğenin sağlandığı sürece içerik olarak kabul edilebilir > bunu izlemez.|  
|"(düz tırnak işareti)|\&quot;|Bir öznitelik değeri için kullanılmalıdır, ancak bir düz tırnak (") bir öğenin içeriği olarak kabul edilebilir. Öznitelik değerleri tek düz tırnak işareti (') veya (''); düz tırnak işareti içine alınabilir olduğunu unutmayın. öznitelik değeri muhafaza tanımlar hangi karakter ilk olarak görünür ve alternatif teklif sonra bir sabit değer içinde kullanılabilir.|  
|' (tek düz tırnak işareti)|\&apos;|Bir öznitelik değeri için kullanılmalıdır, ancak tek düz tırnak işareti (') bir öğenin içeriği olarak kabul edilebilir. Öznitelik değerleri tek düz tırnak işareti (') veya (''); düz tırnak işareti içine alınabilir olduğunu unutmayın. öznitelik değeri muhafaza tanımlar hangi karakter ilk olarak görünür ve alternatif teklif sonra bir sabit değer içinde kullanılabilir.|  
|(sayısal karakter eşlemelerini)|&#*[tamsayı]* ; veya & #x *[onaltılık]*;|XAML etkin olan kodlama içine sayısal karakter eşlemelerini destekler.|  
|(bölünemez boşluk)|&\#160; (UTF-8 kodlaması varsayılarak)|Akış belge öğeleri veya metin WPF gibi ele öğeleri <xref:System.Windows.Controls.TextBox>, bölünemez boşluklar Normalleştirilmemiş biçimlendirme dışında için bile `xml:space="default"`. (Daha fazla bilgi için [boşluk XAML içinde işleme](whitespace-processing-in-xaml.md).)|  
  
<a name="xml_comment_format"></a>   
## <a name="xml-comment-format"></a>XML açıklama biçimi  
 XAML XML açıklama biçimi kullanır: Başlangıç açıklamanın `<!--`, açıklama sonu `-->,` ve sırasını `--` açıklama içinde gerçekleşmemelidir.  
  
<a name="xml_processing_instructions"></a>   
## <a name="xml-processing-instructions"></a>XML işleme yönergeleri  
 XAML XML işleme yönergeleri yönergeleri ile geçirilmelidir state XML belirtimleri göre işler. XAML içinde .NET Framework XAML hizmetlerinde işleme işleme yönergeleri kullanmaz. XAML kullanan diğer mevcut altyapılarınız, ayrıca XAML işleme yönergeleri kullanmayın.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [XAML'ye Genel Bakış (WPF)](../wpf/advanced/xaml-overview-wpf.md)
- [İşaretleme Uzantıları ve WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
- [XamlName Dilbilgisi](xamlname-grammar.md)
- [Boşluk XAML içinde işleme](whitespace-processing-in-xaml.md)
