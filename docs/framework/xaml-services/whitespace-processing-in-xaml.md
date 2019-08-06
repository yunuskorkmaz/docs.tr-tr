---
title: XAML'de Boşluk İşleme
ms.date: 03/30/2017
helpviewer_keywords:
- East Asian characters [XAML Services]
- XAML [XAML Services], white-space processing
- white-space processing in XAML [XAML Services]
- characters [XAML Services], East Asian
ms.assetid: cc9cc377-7544-4fd0-b65b-117b90bb0b23
ms.openlocfilehash: 077f19690d204d3b8f682d01c51feee9e9edbfd4
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796816"
---
# <a name="white-space-processing-in-xaml"></a>XAML'de Boşluk İşleme
XAML durumunun, bir [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] işlemci uygulamasıyla ilgili önemli boşluk olması gerektiğini belirten dil kuralları. Bu konu, bu XAML dil kurallarını belgeler. Ayrıca XAML işlemcisinin ve serileştirme için XAML yazıcısının [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] uygulanmasıyla tanımlanan ek boşluk işlemesini belgeler.  
  
<a name="whitespace_definition"></a>   
## <a name="white-space-definition"></a>Boşluk tanımı  
 İle tutarlı [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)], boşluk, linefeed ve [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] Tab içindeki boşluk karakterleri ile tutarlıdır. Bunlar sırasıyla 0020, [!INCLUDE[TLA#tla_unicode](../../../includes/tlasharptla-unicode-md.md)] 000A ve 0009 değerlerine karşılık gelir.  
  
<a name="whitespace_normalization"></a>   
## <a name="white-space-normalization"></a>Boşluk normalleştirme  
 Varsayılan olarak, bir [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] işlemci bir [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] dosyayı işlediğinde aşağıdaki beyaz boşluk normalleştirmesi oluşur:  
  
1. Doğu Asya karakterleri arasında linefeed karakterleri kaldırılır. Bu terimin bir tanımı için bu konunun devamındaki "Doğu Asya karakterleri" bölümüne bakın.  
  
2. Tüm beyaz boşluk karakterleri (boşluk, linefeed, sekme) boşluklara dönüştürülür.  
  
3. Tüm ardışık Boşluklar silinir ve bir boşluk ile değiştirilmiştir.  
  
4. Başlangıç etiketinden hemen sonraki bir boşluk silinir.  
  
5. Bitiş etiketi silinmeden hemen önce bir boşluk.  
  
 "Default", [XML: Space](xml-space-handling-in-xaml.md) özniteliğinin varsayılan değeri tarafından belirtilen duruma karşılık gelir.  
  
<a name="whitespace_in_inner_text_and_string_primitives"></a>   
## <a name="white-space-in-inner-text-and-string-primitives"></a>İç metinde boşluk ve dize temelleri  
 Önceki normalleştirme kuralları XAML öğeleri içinde bulunan iç metin için geçerlidir. Normalleştirme sonrasında bir XAML işlemcisi, herhangi bir iç metni aşağıdaki gibi uygun bir türe dönüştürür:  
  
- Özelliğin türü bir koleksiyon değilse ancak doğrudan bir <xref:System.Object> tür değilse, XAML işlemcisi tür dönüştürücüsünü kullanarak bu türe dönüştürmeye çalışır. Başarısız bir dönüştürme, derleme zamanı hatasına neden olur.  
  
- Özelliğin türü bir koleksiyon ise ve iç metin bitişik ise (aradaki öğe etiketi yoksa), iç metin tek <xref:System.String>bir olarak ayrıştırılır. Koleksiyon türü kabul <xref:System.String>edemez, bu da derleme zamanı hatasına neden olur.  
  
- Özelliğin türü ise <xref:System.Object>, iç metin tek <xref:System.String>bir olarak ayrıştırılır. Aradaki öğe etiketleri varsa, tür tek bir nesne ( <xref:System.Object> <xref:System.String> veya başka bir şekilde) gösterdiği için bu bir derleme zamanı hatasına neden olur.  
  
- Özelliğin türü bir koleksiyon ise ve iç metin bitişik değilse, ilk alt dize öğesine dönüştürülür <xref:System.String> ve koleksiyon öğesi olarak eklenir, aradaki öğe bir koleksiyon öğesi olarak eklenir ve son alt dize (varsa) koleksiyona üçüncü <xref:System.String> öğe olarak eklendi.  
  
<a name="preserving_whitespace"></a>   
## <a name="preserving-white-space"></a>Boşluk koruma  
 Son sunum için, [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] işlemci beyaz alanı normalleştirmeden etkilenmeyen, kaynak üzerinde boşluk korumak için çeşitli teknikler vardır.  
  
 **xml:space="preserve"** : Bu özniteliği, boşluk saklama işleminin istendiği öğe düzeyinde belirtin. Bu, kod düzenlemesi uygulamaları tarafından görsel açıdan sezgisel bir iç içe geçme olarak öğeleri "düzgün yazdırma" olarak hizalamak için eklenen boşlukları içeren tüm boşluğu korur. Ancak, bu alanlar işleme, kapsayan öğe için içerik modeli tarafından belirlenir. Nesne modellerinin `xml:space="preserve"` çoğu özniteliği nasıl ayarlamaktan bağımsız olarak boş değer düşünmediğinden kök düzeyinde belirtmekten kaçının. Küresel `xml:space` ayar, bazı uygulamalarda xaml işlemede (özellikle serileştirme) performans sonuçlarının olması olabilir. Özniteliği yalnızca dizeler içinde boşluk işleyen ya da boşluk açısından önemli koleksiyonlardaki öğe düzeyinde ayarlamak daha iyi bir uygulamadır.  
  
 **Varlıklar ve bölünemez boşluklar**: [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] bir metin nesne modeli [!INCLUDE[TLA#tla_unicode](../../../includes/tlasharptla-unicode-md.md)] içinde herhangi bir varlığın yerleştirilmesini destekler. Bölünemez boşluk gibi adanmış varlıkları (&\#160; UTF-8 kodlaması) kullanabilirsiniz. Bölünemez boşluk karakterlerini destekleyen zengin metin denetimleri de kullanabilirsiniz. Ölçü gibi düzen özelliklerinin benzetimini yapmak için varlıklar kullanıyorsanız, varlıkların bir süre içinde girintileme sonuçları oluşturma olanaklarından daha fazla sayıda faktöre göre farklılık gösterdiğinden, bu tür bir işlem yapılması gerekir. Pano ve kenar boşluklarının uygun kullanımı gibi düzen sistemi. Örneğin, varlıklar yazı tiplerine eşlenir ve Kullanıcı yazı tipi seçimine yanıt olarak boyutu değiştirebilir.  
  
<a name="east_asian_characters"></a>   
## <a name="east-asian-characters"></a>Doğu Asya karakterleri  
 "Doğu Asya karakterleri", u + 20000 [!INCLUDE[TLA2#tla_unicode](../../../includes/tla2sharptla-unicode-md.md)] karakter aralıkları kümesi olarak, u + 2FFFD ve u + 30000 ile u + 3FFFD arasında tanımlanır. Bu alt küme bazen "CJK Kavram Resimleri" olarak da adlandırılır. Daha fazla bilgi için bkz. <https://www.unicode.org>.  
  
<a name="whitespace_and_text_content_models"></a>   
## <a name="white-space-and-text-content-models"></a>Boşluk ve metin içeriği modelleri  
 Uygulamada, boşluk korumak, yalnızca tüm olası içerik modellerinin bir alt kümesiyle ilgili kaygıdır. Bu alt küme, bazı biçimde <xref:System.String> , özel <xref:System.String> bir koleksiyonda <xref:System.String> veya bir ya <xref:System.Collections.Generic.ICollection%601> da bir <xref:System.Collections.IList> koleksiyondaki diğer türler için tek bir tür alan içerik modellerinden oluşur.  
  
### <a name="white-space-and-text-content-models-in-wpf"></a>WPF 'de boşluk ve metin içeriği modelleri  
 Çizim amaçlarıyla, bu bölümün geri kalanı WPF tarafından tanımlanan belirli türlere başvurur. Bu konuda açıklanan boşluk işleme özellikleri, genellikle .NET Framework XAML Hizmetleri ve WPF için de kullanılır. Bu davranışı eylemde görmek için, bazı WPF XAML işaretlemelerini deneyebilir, sonuçları bir nesne grafiğinde görüntüleyebilir ve sonra yeniden biçimlendirmeye tekrar serileştirmenize olanak sağlayabilirsiniz.  
  
 Dizeleri alan içerik modelleri bile, bu içerik modelleriyle ilgili varsayılan davranış, kalan tüm boşluklar önemli kabul edilmez. Örneğin <xref:System.Windows.Controls.ListBox> , bir <xref:System.Collections.IList>alır, ancak boşluk (her biri <xref:System.Windows.Controls.ListBoxItem>arasındaki satır beslemeleri gibi) korunmaz ve işlenmez. Satır akışlarını öğeler için <xref:System.Windows.Controls.ListBoxItem> dizeler arasında ayırıcılar olarak kullanmaya çalışırsanız, hiç çalışmaz; satır akışlarıyla ayrılmış dizeler tek bir dize ve bir öğe olarak değerlendirilir.  
  
 Boşlukları önemli olarak ele alan koleksiyonlar genellikle akış belge modelinin bir parçasıdır. Beyaz alanı koruma davranışını destekleyen birincil koleksiyon, <xref:System.Windows.Documents.InlineCollection>. Bu koleksiyon sınıfı ile <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>bildirilmiştir; bu öznitelik bulunduğunda [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] , işlemci koleksiyon içindeki boşlukları önemli ölçüde değerlendirir. Belirtilen bir `xml:space="preserve"` <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> koleksiyon içindeki ve boşluk birleşimi, tüm boşluklar korunmalı ve işlenir. `xml:space="default"` Bir<xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> içinde ve boşluk birleşimi, daha önce açıklanan ilk beyaz boşluk normalleştirmesine neden olur ve bu da bazı konumlarda bir boşluk bırakır ve bu boşluklar korunur ve işlenir. Hangi davranışın sizin için kullanılması gerektiği ve tercih ettiğiniz davranışı etkinleştirmek için seçime `xml:space` bağlı olarak kullanmanız gerekir.  
  
 Ayrıca, akış belge modelinde bir satır sonu sağlayan belirli satır içi öğeler, bir boşluk açısından önemli bir koleksiyonda bile ek bir boşluk sunmaz. Örneğin, <xref:System.Windows.Documents.LineBreak> öğesi, HTML 'deki \<br/> etiketiyle aynı amaca sahiptir ve biçimlendirmede okunabilirlik için, genellikle bir <xref:System.Windows.Documents.LineBreak> yazılan linefeed tarafından sonraki metinden ayrılır. Bu satır besleme sonraki satırda önde gelen bir boşluk olacak şekilde normalleştirilmemelidir. Bu <xref:System.Windows.Documents.LineBreak> davranışı etkinleştirmek için, öğesi için sınıf tanımı uygular ve <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>ardından, çevreleyen <xref:System.Windows.Documents.LineBreak> beyaz alanın her zaman kırpılmasından dolayı [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] işlemci tarafından yorumlanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XAML 'ye Genel Bakış (WPF)](../wpf/advanced/xaml-overview-wpf.md)
- [XML karakter varlıkları ve XAML](xml-character-entities-and-xaml.md)
- [XML: XAML 'de alan işleme](xml-space-handling-in-xaml.md)
