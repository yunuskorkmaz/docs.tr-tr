---
title: XAML'de Boşluk İşleme
ms.date: 03/30/2017
helpviewer_keywords:
- East Asian characters [XAML Services]
- XAML [XAML Services], whitespace processing
- whitespace processing in XAML [XAML Services]
- characters [XAML Services], East Asian
ms.assetid: cc9cc377-7544-4fd0-b65b-117b90bb0b23
ms.openlocfilehash: 9f7d7ca900955b8899322533f9d69338042d88ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="whitespace-processing-in-xaml"></a>XAML'de Boşluk İşleme
Bu önemli boşluk işlenen, tarafından XAML dil kuralları durum bir [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] işlemci uygulama. Bu bölümde, XAML dili kurallar listelenmiştir. Ayrıca tarafından tanımlanan ek boşluk işleme belgeleri [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] XAML işlemci ve seri hale getirme için XAML yazıcı uygulamasıdır.  
  
<a name="whitespace_definition"></a>   
## <a name="whitespace-definition"></a>Boşluk tanımı  
 İle tutarlı [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)], boşluk karakterleri [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] alan, satır besleme ve sekmesi. Bunlar karşılık [!INCLUDE[TLA#tla_unicode](../../../includes/tlasharptla-unicode-md.md)] değerleri 0020, 000A ve 0009 sırasıyla.  
  
<a name="whitespace_normalization"></a>   
## <a name="whitespace-normalization"></a>Boşluk normalleştirme  
 Varsayılan olarak aşağıdaki boşluk normalleştirme gerçekleşir olduğunda bir [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] işlemci işlemleri bir [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] dosyası:  
  
1.  Doğu Asya karakterler arasında satır besleme karakterleri kaldırılır. Bu terim tanımı için bu konunun devamındaki "Doğu Asya karakterler" bölümüne bakın.  
  
2.  Tüm boşluk karakterleri (alan, satır besleme, sekmesi) alanları dönüştürülür.  
  
3.  Tüm ardışık boşluk silinir ve bir boşlukla değiştirildi.  
  
4.  Başlangıç etiketi hemen ardından bir boşluk silinir.  
  
5.  Bitiş etiketi hemen önce bir boşluk silinir.  
  
 "Varsayılan" karşılık gelen varsayılan değeri tarafından belirtilen durumuna [XML: Space](../../../docs/framework/xaml-services/xml-space-handling-in-xaml.md) özniteliği.  
  
<a name="whitespace_in_inner_text_and_string_primitives"></a>   
## <a name="whitespace-in-inner-text-and-string-primitives"></a>Boşluk iç metin ve dize temelleri  
 XAML öğeleri içinde bulunan iç metne önceki normalleştirme kurallarını uygulayabilir. Normalleştirme sonra XAML işlemci herhangi bir iç metin uygun bir türe şu şekilde dönüştürür:  
  
-   Özellik türü bir toplama değildir, ancak doğrudan değil bir <xref:System.Object> türü, XAML işlemci türü dönüştürücü kullanarak bu türüne dönüştürmek çalışır. Burada başarısız dönüştürme bir derleme zamanı hatasına neden olur.  
  
-   Özellik türü bir koleksiyon ve iç metni bitişik ise (hiçbir müdahalede bulunan öğe etiketleri), iç metni tek bir ayrıştırılır <xref:System.String>. Koleksiyon türünü kabul edemez, <xref:System.String>, bu da bir derleme zamanı hatasına neden olur.  
  
-   Özelliğin türü ise <xref:System.Object>, iç metni tek bir ayrıştırılır <xref:System.String>. Öğe etiketleri var olan müdahale cihazlarınız varsa, bu bir derleme zamanı hatası neden olur <xref:System.Object> türü tek bir nesne anlamına gelir (<xref:System.String> veya aksi halde).  
  
-   Özelliğin türü koleksiyonudur ve iç metni bitişik değil, ilk alt dizeyi dönüştürülen bir <xref:System.String> ve bir koleksiyon öğesi olarak eklenen, müdahalede bulunan öğe bir koleksiyon öğesi olarak eklenir, son olarak sonunda alt dizeyi (varsa) üçüncü bir olarak koleksiyonuna eklenen <xref:System.String> öğesi.  
  
<a name="preserving_whitespace"></a>   
## <a name="preserving-whitespace"></a>Boşluk koruma  
 Kaynak boşluk koruma için bazı teknikler vardır [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] etkilenmez nihai sunum [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] işlemci boşluk normalleştirme.  
  
 **XML: space = "preserve"**: Bu öznitelik boşluk korunması istenen burada öğe düzeyinde belirtin. Tüm "pretty-Yazdır" kod düzenleme uygulamalar tarafından eklenebilir alanları içeren, boşluk bu korur öğeleri görsel olarak sezgisel bir iç içe geçme olarak hizalayın. Ancak, bu alanları olup işlemek içeren öğe için içerik modeli belirlenir. Belirtmekten kaçının `xml:space="preserve"` çoğu nesne modelleri boşluk bağımsız olarak, önemli olarak dikkate almaz çünkü kök düzeyinde nasıl, öznitelik ayarlayın. Ayarı `xml:space` genel performans sonuçları bazı uygulamalarda (özellikle seri hale getirme) işleme XAML sahip olabilir. Yalnızca öznitelik özellikle boşluk dizeler içindeki oluşturmak ya da boşluk önemli koleksiyonlarıdır öğeleri düzeyinde ayarlamak için daha iyi bir uygulamadır.  
  
 **Varlıklar ve olmayan sonu alanları**: [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] herhangi bir yerleştirme destekleyen [!INCLUDE[TLA#tla_unicode](../../../includes/tlasharptla-unicode-md.md)] metin nesne modeli içindeki varlık. Ayrılmış varlıklar gibi bölünemez boşluk kullanabilirsiniz (&\#160; UTF-8 kodlaması). Bölünemez boşluk karakterleri destekleyen zengin metin denetimleri de kullanabilirsiniz. Tipik bir girintileme sonuçlarında üretme yetenekleri olduğundan varlıkları çalışma zamanı çıktısını büyük bir dizi etkene göre değişir olduğundan girintileme gibi yerleşim özellikleri benzetimini yapmak için varlıklar kullanıyorsanız, siz dikkatli olmanız gerekir paneller ve kenar boşlukları doğru kullanımı gibi düzen sistemi. Örneği için varlıklar yazı tiplerini eşlenir ve yanıt olarak kullanıcı yazı tipi seçimi boyutunu değiştirebilirsiniz.  
  
<a name="east_asian_characters"></a>   
## <a name="east-asian-characters"></a>Doğu Asya karakterler  
 "Doğu Asya karakterler" bir dizi tanımlanmış [!INCLUDE[TLA2#tla_unicode](../../../includes/tla2sharptla-unicode-md.md)] U + U + 2FFFD 20000 ve U + U + 3FFFD 30000 karakter aralığı. Bu alt bazen "CJK İdeogramlar" adlandırılır. Daha fazla bilgi için bkz. [http://www.unicode.org](http://www.unicode.org/).  
  
<a name="whitespace_and_text_content_models"></a>   
## <a name="whitespace-and-text-content-models"></a>Boşluk ve metin içerik modelleri  
 İçinde boşluk koruma yalnızca bir alt kümesini tüm olası içerik modelleri kaygısı, uygulamadır. Bu alt tek yapabileceği içerik modellerinin oluşan <xref:System.String> bazı formunda, ayrılmış bir türü <xref:System.String> koleksiyonu veya bir karışımını <xref:System.String> ve diğer türleri bir <xref:System.Collections.IList> veya <xref:System.Collections.Generic.ICollection%601> koleksiyonu.  
  
### <a name="whitespace-and-text-content-models-in-wpf"></a>WPF'de boşluk ve metin içerik modelleri  
 Gösterim amacıyla, bu bölümde kalanı WPF tarafından tanımlanan belirli türleri başvuruda bulunuyor. Bu konuda açıklanan boşluk işleme .NET Framework XAML hizmetlerinde ve WPF için genellikle ilgili özellikleridir. Uygulamada bu davranışı görmek için olan bazı WPF XAML biçimlendirme denemeler, bir nesne grafiğinin sonuçları görüntüleyin ve geri biçimlendirme yeniden seri.  
  
 Bile, içerik modelleri için dizeleri alabilir, bu içerik modelleri içinde varsayılan davranışı kalır boşluk gibi önemli işlenmez. Örneğin, <xref:System.Windows.Controls.ListBox> geçen bir <xref:System.Collections.IList>, ancak boşluk (her arasında satır beslemeleri gibi <xref:System.Windows.Controls.ListBoxItem>) korunmaz ve işlenmez. Dizeler için arasında ayırıcılar olarak satır beslemeleri kullanmayı dener <xref:System.Windows.Controls.ListBoxItem> öğeleri, hiç çalışmaz; satır beslemeleri tarafından ayrılmış dizeleri bir dize ve bir öğe kabul edilir.  
  
 Boşluk önemli olarak davran bu koleksiyonları genellikle akış belge modeli bir parçasıdır. Boşluk korunması davranışını destekler birincil koleksiyonu <xref:System.Windows.Documents.InlineCollection>. Bu koleksiyon sınıfı ile bildirilmiş <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>; bu öznitelik bulunduğunda, [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] işlemci kabul koleksiyonundaki boşluk olarak önemli. Birleşimi `xml:space="preserve"` ve boşluk içinde bir <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> koleksiyonudur tüm boşluk korunur ve işlenen gösterilir. Birleşimi `xml:space="default"` ve boşluk içinde bir <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> belirli konumlarda bir boşluk ve bu alanları bırakır ilk boşluk normalleştirme daha önce açıklanan nedenler korunur ve çizilir. Hangi davranışın tercih edilir size bağlıdır ve kullanması gereken `xml:space` seçmeli olarak istediğiniz davranışı etkinleştirmek üzere.  
  
 Ayrıca, bir akış belge modeldeki linebreak connote belirli satır içi öğeleri bile koleksiyonundaki bir boşluk önemli bir boşluk eklemeniz gerekir kasıtlı olarak değil. Örneğin, <xref:System.Windows.Documents.LineBreak> öğeye sahip aynı amaca \<BR / > içinde etiketi [!INCLUDE[TLA2#tla_html](../../../includes/tla2sharptla-html-md.md)]ve biçimlendirme içinde okunabilirlik için genellikle bir <xref:System.Windows.Documents.LineBreak> sonraki tüm metinden tarafından yazılan bir satır besleme ayrılır. Bu satır besleme sonraki satırın başında boşluk olmasını normalleştirilmiş değil. Sınıf tanımı bu davranışı etkinleştirmek için <xref:System.Windows.Documents.LineBreak> öğesine uygular <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>, hangi sonra yorumlanır tarafından [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] bu boşluk çevresindeki ortalama İşlemci <xref:System.Windows.Documents.LineBreak> her zaman kırpılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XAML'ye Genel Bakış (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [XML Karakter Varlıkları ve XAML](../../../docs/framework/xaml-services/xml-character-entities-and-xaml.md)  
 [XAML'de xml:space İşleme](../../../docs/framework/xaml-services/xml-space-handling-in-xaml.md)
