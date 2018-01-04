---
title: "XML Karakter Varlıkları ve XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "23"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6b325c931579606f6d1d90eb821766a4110acfd5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="xml-character-entities-and-xaml"></a>XML Karakter Varlıkları ve XAML
XAML için özel karakterler XML dosyasında tanımlanan karakter varlıkları kullanır. Bu konuda, bazı belirli karakter varlıkları ve XAML diğer XML kavramlarına genel konular açıklanmaktadır.  
  
<a name="character_entities_and_escaping_issues_that_are_unique_to_xaml"></a>   
## <a name="character-entities-and-escaping-issues-that-are-unique-to-xaml"></a>Karakter varlıkları ve XAML için benzersiz kaçış sorunları  
 XAML biçimlendirme genellikle aynı karakter varlıkları ve XML içinde tanımlanan çıkış sıraları kullanır.  
  
 Ana istisnadır, küme ayraçları ({ve}) tarafından ayraçlar bir karakter dizisi işaretleme uzantısı anlaşılması gereken XAML işlemci bu karakterleri bildirmek için XAML'de önemi yoktur. Biçimlendirme uzantıları hakkında daha fazla bilgi için bkz: [işaretleme uzantılarına genel bakış XAML](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md).  
  
 Ancak, yine küme ayraçları değişmez değer karakter olarak XAML XML yerine belirli bir kaçış dizisi kullanarak görüntüleyebilirsiniz. Daha fazla bilgi için bkz: [{} kaçış sırası - biçimlendirme uzantısı](escape-sequence-markup-extension.md).  
  
 Unutmayın bir ters eğik çizgi (\\) bir dize olarak işlendiğinde bir kaçış sırası gerektirmez.  
  
<a name="xml_character_entities"></a>   
## <a name="xml-character-entities"></a>XML karakter varlıkları  
 Daha önce belirtildiği gibi çoğu karakter varlıkları ve XAML işaretleme yazmak için genellikle kullanılan kaçış sıraları XML tarafından tanımlanır. Bu konu, bu varlıkları tam listesi sağlamaz; varlıklar için ayrıntılı başvuru dış belgelerinde gibi XML belirtimleri bulunabilir. Ancak, kolaylık olması için bu konuda bazı XAML biçimlendirme genelde kullanılan belirli XML karakter varlıkları listelenir.  
  
|Karakter|Varlık|Notlar|  
|---------------|------------|-----------|  
|& (ve işareti)|\&amp;|Öznitelik değeri hem bir öğenin içeriğini kullanılması gerekir.|  
|> (büyük-karakter daha)|\&gt;|Bir öznitelik değeri için kullanılması gereken ancak > sürece bir öğenin içeriğini olarak kabul edilebilir < önce gelmez.|  
|< (daha az-karakter daha)|\&lt;|Bir öznitelik değeri için kullanılması gereken ancak \< sürece bir öğenin içeriğini olarak kabul edilebilir > bunu izlemez.|  
|"(düz tırnak işareti)|\&quot;|Bir öznitelik değeri için kullanılması gereken ancak düz tırnak işareti (") öğenin içerik kabul edilebilir. Öznitelik değerleri düz tek tırnak işareti (') veya ("); düz tırnak işareti içine olduğunu unutmayın hangi karakter ilk olarak görünür öznitelik değeri muhafaza tanımlar ve alternatif teklif ardından değeri içinde bir hazır değer olarak kullanılabilir.|  
|' (düz tek tırnak işareti)|\&apos;|Bir öznitelik değeri için kullanılması gereken ancak düz tek tırnak işareti (') öğenin içerik kabul edilebilir. Öznitelik değerleri düz tek tırnak işareti (') veya ("); düz tırnak işareti içine olduğunu unutmayın hangi karakter ilk olarak görünür öznitelik değeri muhafaza tanımlar ve alternatif teklif ardından değeri içinde bir hazır değer olarak kullanılabilir.|  
|(sayısal karakter eşlemeleri)|&#*[tamsayı]* ; veya & #x*[onaltılık]*;|XAML etkin olan kodlama içine sayısal karakter eşlemeleri destekler.|  
|(bölünemez boşluk)|&\#160; (UTF-8 kodlaması varsayılarak)|Akış belge öğeleri ya da metin WPF gibi ele öğeleri için <xref:System.Windows.Controls.TextBox>, bölünemez boşluklar Normalleştirilmemiş biçimlendirme dışında için bile `xml:space="default"`. (Daha fazla bilgi için bkz: [XAML'de boşluk işleme](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).)|  
  
<a name="xml_comment_format"></a>   
## <a name="xml-comment-format"></a>XML açıklama biçimi  
 XAML XML açıklama biçimi kullanır: açıklama başlangıç `<!--`, yorum sonudur `-->,` ve sıra `--` içinde yorum oluşamaz.  
  
<a name="xml_processing_instructions"></a>   
## <a name="xml-processing-instructions"></a>XML işleme yönergeleri  
 XAML XML işleme yönergelerini yönergeleri aracılığıyla geçirilmelidir state XML belirtimlerine uygun işler. .NET Framework XAML hizmetlerinde işleme XAML işleme yönergeleri kullanmaz. XAML kullanmak varolan diğer çerçeveler XAML işleme yönergeleri de kullanmayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XAML'ye Genel Bakış (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [İşaretleme Uzantıları ve WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [XamlName Dilbilgisi](../../../docs/framework/xaml-services/xamlname-grammar.md)  
 [XAML'de Boşluk İşleme](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)
