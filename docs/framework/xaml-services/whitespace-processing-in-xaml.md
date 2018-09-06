---
title: Boşluk XAML içinde işleme
ms.date: 03/30/2017
helpviewer_keywords:
- East Asian characters [XAML Services]
- XAML [XAML Services], white-space processing
- white-space processing in XAML [XAML Services]
- characters [XAML Services], East Asian
ms.assetid: cc9cc377-7544-4fd0-b65b-117b90bb0b23
ms.openlocfilehash: 89f8a4675b3edc23913549bc24f0d9ae16917519
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43802554"
---
# <a name="white-space-processing-in-xaml"></a>Boşluk XAML içinde işleme
XAML dil kuralları önemli boşlukların işlenen, tarafından durum bir [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] işlemci uygulamasında. Bu bölümde, XAML dili kurallar listelenmiştir. Ayrıca tarafından tanımlanan ek boşluk işleme belgeleri [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] XAML işlemci ve seri hale getirme için XAML yazıcı uygulamasıdır.  
  
<a name="whitespace_definition"></a>   
## <a name="white-space-definition"></a>Boşluk tanımı  
 Tutarlı [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)], beyaz alan karakteri olarak [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] boşluk, satır besleme ve sekmesi. Bunlar karşılık [!INCLUDE[TLA#tla_unicode](../../../includes/tlasharptla-unicode-md.md)] değerleri 0020 000A ve 0009 sırasıyla.  
  
<a name="whitespace_normalization"></a>   
## <a name="white-space-normalization"></a>Boşluk normalleştirme  
 Varsayılan olarak, aşağıdaki beyaz boşluk normalleştirme gerçekleşir, bir [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] işlemci işlemleri bir [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] dosyası:  
  
1.  Doğu Asya karakterler arasında satır başı besleme karakterleri kaldırılır. Bu terim tanımı için bu konunun ilerleyen bölümlerindeki "Doğu Asya karakterler" bölümüne bakın.  
  
2.  Tüm beyaz boşluk karakterleri (boşluk, satır besleme, sekme), boşluk dönüştürülür.  
  
3.  Tüm ardışık boşluk silinir ve bir boşlukla değiştirildi.  
  
4.  Başlangıç etiketinin hemen ardından bir boşluk silinir.  
  
5.  Bitiş etiketi hemen önce bir boşluk silinir.  
  
 "Varsayılan" karşılık gelen varsayılan değeri tarafından belirtilen duruma [XML: Space](../../../docs/framework/xaml-services/xml-space-handling-in-xaml.md) özniteliği.  
  
<a name="whitespace_in_inner_text_and_string_primitives"></a>   
## <a name="white-space-in-inner-text-and-string-primitives"></a>Boşluk iç metni ve dize temelleri  
 XAML öğeleri içinde bulunan iç metni önceki normalleştirme kuralları uygulanır. Normalleştirme sonra XAML işlemci herhangi bir iç metin uygun bir türe şu şekilde dönüştürür:  
  
-   Özelliğin türü bir koleksiyon değil, ancak doğrudan değil bir <xref:System.Object> türü, XAML işlemci onun tür dönüştürücü kullanarak bu türe dönüştürmeye çalışır. Burada başarısız bir dönüştürme, bir derleme zamanı hatasına neden olur.  
  
-   Özelliğin türü bir koleksiyon ve iç metni bitişik ise (müdahalede bulunan öğe etiket yok), iç metni tek bir ayrıştırılır <xref:System.String>. Koleksiyon türü alamaz, <xref:System.String>, bu da bir derleme zamanı hatasına neden olur.  
  
-   Özelliğin türü ise <xref:System.Object>, iç metni tek bir ayrıştırılır <xref:System.String>. Var olan müdahale cihazlarınız varsa öğe etiketleri, bu derleme zamanı hatası nedeniyle neden olur <xref:System.Object> türü tek bir nesne anlamına gelir (<xref:System.String> veya başka türlü).  
  
-   Özelliğin türü koleksiyonudur ve iç metni bitişik değil, ilk alt dizeyi dönüştürülür bir <xref:System.String> ve bir koleksiyon öğesi olarak eklenir, müdahalede bulunan öğe, bir koleksiyon öğesi olarak eklenir ve son olarak (varsa) izleyen alt dizedir Üçüncü olarak koleksiyona eklenen <xref:System.String> öğesi.  
  
<a name="preserving_whitespace"></a>   
## <a name="preserving-white-space"></a>Koruma boşluk  
 Kaynak boşluk korunması için çeşitli teknikler vardır [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] etkilenmez nihai sunu [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] işlemci boşluk normalleştirme.  
  
 **XML: space = "preserve"**: Bu öznitelik burada boşluk korunması isteniyorsa öğe düzeyinde belirtin. Tüm "pretty yazdırma" için kod düzenleme uygulamalar tarafından eklenmiş olabilir alanları içeren, boşluk bu korur, olarak görsel olarak sezgisel bir iç içe öğeleri hizalayın. Ancak bu boşlukları olup işlemek için kapsayıcı öğe içerik modeli belirlenir. Belirtmekten kaçının `xml:space="preserve"` çoğu nesne modellerini beyaz dikkate almaz olduğundan kök düzeyinde öznitelik nasıl ayarlanacağını bağımsız olarak gibi önemli boşluk. Ayar `xml:space` genel performans sonuçları XAML (özellikle seri hale getirme) bazı uygulamalarda işleme sahip olabilir. Yalnızca öznitelik özellikle boşluk dizeler içindeki işleme veya boşluk önemli koleksiyon öğeleri düzeyinde ayarlamak için daha iyi bir uygulamadır.  
  
 **Varlıklar ve olmayan son boşluk**: [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] destekleyen herhangi bir yerleştirme [!INCLUDE[TLA#tla_unicode](../../../includes/tlasharptla-unicode-md.md)] metin nesne modeli içindeki varlık. Bölünemez boşluk gibi özel varlık kullanabilirsiniz (&\#160; UTF-8 kodlaması). Bölünemez boşluk karakterleri destekleyen zengin metin denetimleri de kullanabilirsiniz. Tipik bir girintileme sonuçları üreten yetenekleri olduğu kadar temkinli varlıkları çalışma zamanı çıktısı büyük bir dizi etkene göre değişiklik gösterir çünkü girintileme gibi düzen özelliklerini benzetimini yapmak için varlıklar kullanıyorsanız, dikkatli olmalıdır paneller ve kenar boşlukları doğru kullanımı gibi düzen sistemi. Örneğin, varlıkları yazıtipleriyle eşlenir ve yanıt olarak kullanıcı yazı tipi seçimi boyutunu değiştirebilirsiniz.  
  
<a name="east_asian_characters"></a>   
## <a name="east-asian-characters"></a>Doğu Asya karakterlerinin görüntülenmesi  
 "Doğu Asya karakterler" bir dizi tanımlanan [!INCLUDE[TLA2#tla_unicode](../../../includes/tla2sharptla-unicode-md.md)] karakteri, U + U + 2FFFD 20000 ve U + U + 3FFFD 30000 aralıkları. Bu alt küme, bazen "CJK İdeogramlar" da denir. Daha fazla bilgi için bkz. [http://www.unicode.org](http://www.unicode.org/).  
  
<a name="whitespace_and_text_content_models"></a>   
## <a name="white-space-and-text-content-models"></a>Boşluk ve metnin içerik modelleri  
 Uygulamada, beyaz alanı koruma yalnızca önemli bir kısmı tüm olası içerik modelleri için önemlidir. Bu alt tek gerçekleştirebileceğiniz içerik modelleri oluşur <xref:System.String> bazı formunda, ayrılmış bir türü <xref:System.String> koleksiyon veya bir karışımını <xref:System.String> ve diğer türleri bir <xref:System.Collections.IList> veya <xref:System.Collections.Generic.ICollection%601> koleksiyonu.  
  
### <a name="white-space-and-text-content-models-in-wpf"></a>WPF içinde boşluk ve metnin içerik modelleri  
 Gösterim amacıyla, bu bölümün geri kalanında WPF tarafından tanımlanan belirli türlerine başvuruyor. Bu konuda açıklanan boşluk işleme özellikleri genellikle .NET Framework XAML hizmetlerinde hem WPF ilgili. Bu davranışı iş başında görmek için bazı WPF XAML biçimlendirme ile denemeler yapın, bir nesne grafında sonuçlarını görüntülemek ve yeniden geri biçimlendirme için seri hale getirme.  
  
 Bile, içerik modelleri için dizeleri sürebilir, bu içerik modelleri içinde varsayılan davranışı kalan tüm boşluk önemli olarak işlenmez. Örneğin, <xref:System.Windows.Controls.ListBox> alır bir <xref:System.Collections.IList>, ancak boşluk (her arasında karakterlerine gibi <xref:System.Windows.Controls.ListBoxItem>) korunmaz ve işlenmez. Karakterlerine ayırıcıları arasında dizeleri için kullanılacak çalışırsanız <xref:System.Windows.Controls.ListBoxItem> öğeleri hiç çalışmaz; karakterlerine tarafından ayrılmış dizeleri bir dize ve bir öğe kabul edilir.  
  
 Boşluk olarak önemli kabul bu koleksiyonlarla genellikle akışı belge modelin bir parçasıdır. Boşluk korunması davranışı destekleyen birincil koleksiyonu <xref:System.Windows.Documents.InlineCollection>. Bu koleksiyon sınıfı ile bildirilen <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>; bu öznitelik bulunduğunda [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] işlemci işlemek koleksiyon içindeki boşluk önemli olarak. Birleşimi `xml:space="preserve"` ve boşluk içinde bir <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> koleksiyondur tüm boşluk korunur ve işlenen gösterilen. Birleşimi `xml:space="default"` ve boşluk içinde bir <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> belirli konumlarda bir boşluk ve bu boşlukları bırakan ilk boşluk normalleştirme daha önce açıklanan nedenleri korunur ve çizilir. Hangi istenmeyen bir davranıştır size bağlıdır; kullanmalısınız `xml:space` seçmeli olarak istediğiniz davranışı etkinleştirmek için.  
  
 Ayrıca, bir akış belgesi modelinde bir linebreak connote bazı satır içi öğeleri bile bir koleksiyondaki boşluk önemli ek bir alan eklemeniz gerekir kasıtlı olarak değil. Örneğin, <xref:System.Windows.Documents.LineBreak> öğesinin aynı amaca \<BR / > etiketi içinde [!INCLUDE[TLA2#tla_html](../../../includes/tla2sharptla-html-md.md)]ve biçimlendirme içinde okunabilirlik için genellikle bir <xref:System.Windows.Documents.LineBreak> sonraki tüm metni tarafından yazılmış bir satır besleme ayrılır. Bu satır besleme sonraki satırın başında boşluk olacak normalleştirilmeli değil. Bu davranış, sınıf tanımında etkinleştirmek için <xref:System.Windows.Documents.LineBreak> öğesine uygular <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>, hangi ardından yorumlanır tarafından [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] çevresindeki boşluk auto'yu İşlemci <xref:System.Windows.Documents.LineBreak> her zaman kırpılır.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [XAML genel bakış (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [XML karakter varlıkları ve XAML](../../../docs/framework/xaml-services/xml-character-entities-and-xaml.md)  
 [XML: Space XAML içinde işleme](../../../docs/framework/xaml-services/xml-space-handling-in-xaml.md)
