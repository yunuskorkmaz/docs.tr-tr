---
title: XAML'de Boşluk İşleme
ms.date: 03/30/2017
helpviewer_keywords:
- East Asian characters [XAML Services]
- XAML [XAML Services], white-space processing
- white-space processing in XAML [XAML Services]
- characters [XAML Services], East Asian
ms.assetid: cc9cc377-7544-4fd0-b65b-117b90bb0b23
ms.openlocfilehash: 930e8a0013dd601aaafcd81340b3b9b8b69f8fdd
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458498"
---
# <a name="white-space-processing-in-xaml"></a>XAML'de Boşluk İşleme
XAML durumunun, önemli boşluk olan bir [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] işlemci uygulamasıyla işlenmesi gereken için dil kuralları. Bu konu, bu XAML dil kurallarını belgeler. Ayrıca XAML işlemcisinin [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] uygulamasının ve serileştirme için XAML yazıcısının tanımladığı ek boşluk işlemeyi da belgelemektedir.  
  
<a name="whitespace_definition"></a>   
## <a name="white-space-definition"></a>Boşluk tanımı  
 [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)]ile tutarlı, [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] boşluk karakterleri, linefeed ve sekme. Bunlar sırasıyla 0020, 000A ve 0009 Unicode değerlerine karşılık gelir.  
  
<a name="whitespace_normalization"></a>   
## <a name="white-space-normalization"></a>Boşluk normalleştirme  
 Varsayılan olarak, bir [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] işlemcisi bir [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] dosyasını işlediğinde aşağıdaki beyaz boşluk normalleştirmesi oluşur:  
  
1. Doğu Asya karakterleri arasında linefeed karakterleri kaldırılır. Bu terimin bir tanımı için bu konunun devamındaki "Doğu Asya karakterleri" bölümüne bakın.  
  
2. Tüm beyaz boşluk karakterleri (boşluk, linefeed, sekme) boşluklara dönüştürülür.  
  
3. Tüm ardışık Boşluklar silinir ve bir boşluk ile değiştirilmiştir.  
  
4. Başlangıç etiketinden hemen sonraki bir boşluk silinir.  
  
5. Bitiş etiketi silinmeden hemen önce bir boşluk.  
  
 "Default", [XML: Space](xml-space-handling-in-xaml.md) özniteliğinin varsayılan değeri tarafından belirtilen duruma karşılık gelir.  
  
<a name="whitespace_in_inner_text_and_string_primitives"></a>   
## <a name="white-space-in-inner-text-and-string-primitives"></a>İç metinde boşluk ve dize temelleri  
 Önceki normalleştirme kuralları XAML öğeleri içinde bulunan iç metin için geçerlidir. Normalleştirme sonrasında bir XAML işlemcisi, herhangi bir iç metni aşağıdaki gibi uygun bir türe dönüştürür:  
  
- Özelliğin türü bir koleksiyon değilse ancak doğrudan bir <xref:System.Object> türü değilse, XAML işlemcisi tür dönüştürücüsünü kullanarak bu türe dönüştürmeye çalışır. Başarısız bir dönüştürme, derleme zamanı hatasına neden olur.  
  
- Özelliğin türü bir koleksiyon ise ve iç metin bitişik ise (aradaki öğe etiketi yoksa), iç metin tek bir <xref:System.String> olarak ayrıştırılır. Koleksiyon türü <xref:System.String> kabul edemez, bu da derleme zamanı hatasına neden olur.  
  
- Özelliğin türü <xref:System.Object> ise, iç metin tek bir <xref:System.String> olarak ayrıştırılır. Aradaki öğe etiketleri varsa, <xref:System.Object> türü tek bir nesne (<xref:System.String> veya aksi) gösterdiği için bu bir derleme zamanı hatasına neden olur.  
  
- Özelliğin türü bir koleksiyon ise ve iç metin bitişik değilse, ilk alt dize <xref:System.String> ' a dönüştürülür ve koleksiyon öğesi olarak eklenir, aradaki öğe bir koleksiyon öğesi olarak eklenir ve son alt dize (varsa) eklenirse üçüncü <xref:System.String> öğe olarak koleksiyona.  
  
<a name="preserving_whitespace"></a>   
## <a name="preserving-white-space"></a>Boşluk koruma  
 [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] işlemci beyaz alan normalleştirmesi tarafından etkilenmeyen son sunum için kaynak [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)], boş alan korumak için çeşitli teknikler vardır.  
  
 **XML: Space = "koru"** : Bu özniteliği, boşluk saklama işleminin istendiği öğe düzeyinde belirtin. Bu, kod düzenlemesi uygulamaları tarafından görsel açıdan sezgisel bir iç içe geçme olarak öğeleri "düzgün yazdırma" olarak hizalamak için eklenen boşlukları içeren tüm boşluğu korur. Ancak, bu alanlar işleme, kapsayan öğe için içerik modeli tarafından belirlenir. Kök düzeyinde `xml:space="preserve"` belirtmekten kaçının çünkü çoğu nesne modeli, özniteliği nasıl ayarlamaktan bağımsız olarak boşluğu önemli ölçüde düşünmez. `xml:space` küresel olarak ayarlamanın bazı uygulamalarda XAML işlemede (özellikle serileştirme) performans sonuçları olabilir. Özniteliği yalnızca dizeler içinde boşluk işleyen ya da boşluk açısından önemli koleksiyonlardaki öğe düzeyinde ayarlamak daha iyi bir uygulamadır.  
  
 **Varlıklar ve bölme olmayan boşluklar**: [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)], bir metin nesne modeli içinde herhangi bir Unicode varlığının yerleştirilmesini destekler. Bölünemez boşluk gibi adanmış varlıkları (& \#160; UTF-8 kodlaması) kullanabilirsiniz. Bölünemez boşluk karakterlerini destekleyen zengin metin denetimleri de kullanabilirsiniz. Ölçü gibi düzen özelliklerinin benzetimini yapmak için varlıklar kullanıyorsanız, varlıkların bir süre içinde girintileme sonuçları oluşturma olanaklarından daha fazla sayıda faktöre göre farklılık gösterdiğinden, bu tür bir işlem yapılması gerekir. Pano ve kenar boşluklarının uygun kullanımı gibi düzen sistemi. Örneğin, varlıklar yazı tiplerine eşlenir ve Kullanıcı yazı tipi seçimine yanıt olarak boyutu değiştirebilir.  
  
<a name="east_asian_characters"></a>   
## <a name="east-asian-characters"></a>Doğu Asya karakterleri  
 "Doğu Asya karakterleri", u + 20000-u + 2FFFD ve u + 30000 ile u + 3FFFD arasında bir Unicode karakter aralığı kümesi olarak tanımlanır. Bu alt küme bazen "CJK Kavram Resimleri" olarak da adlandırılır. Daha fazla bilgi için bkz. <https://www.unicode.org>.  
  
<a name="whitespace_and_text_content_models"></a>   
## <a name="white-space-and-text-content-models"></a>Boşluk ve metin içeriği modelleri  
 Uygulamada, boşluk korumak, yalnızca tüm olası içerik modellerinin bir alt kümesiyle ilgili kaygıdır. Bu alt küme, bazı biçimde <xref:System.String>, bir <xref:System.Collections.IList> veya <xref:System.Collections.Generic.ICollection%601> koleksiyonundaki <xref:System.String> ve diğer türlerin bir dizi <xref:System.String> türü alan içerik modellerinden oluşur.  
  
### <a name="white-space-and-text-content-models-in-wpf"></a>WPF 'de boşluk ve metin içeriği modelleri  
 Çizim amaçlarıyla, bu bölümün geri kalanı WPF tarafından tanımlanan belirli türlere başvurur. Bu konuda açıklanan boşluk işleme özellikleri, genellikle .NET Framework XAML Hizmetleri ve WPF için de kullanılır. Bu davranışı eylemde görmek için, bazı WPF XAML işaretlemelerini deneyebilir, sonuçları bir nesne grafiğinde görüntüleyebilir ve sonra yeniden biçimlendirmeye tekrar serileştirmenize olanak sağlayabilirsiniz.  
  
 Dizeleri alan içerik modelleri bile, bu içerik modelleriyle ilgili varsayılan davranış, kalan tüm boşluklar önemli kabul edilmez. Örneğin, <xref:System.Windows.Controls.ListBox> <xref:System.Collections.IList> alır, ancak boşluk (her <xref:System.Windows.Controls.ListBoxItem> arasındaki satır beslemeleri gibi) korunmaz ve işlenmez. Satır akışlarını <xref:System.Windows.Controls.ListBoxItem> öğelerinin dizeleri arasında ayırıcılar olarak kullanmaya çalışırsanız, hiç çalışmaz; lineakışlarıyla ayrılmış dizeler tek bir dize ve bir öğe olarak değerlendirilir.  
  
 Boşlukları önemli olarak ele alan koleksiyonlar genellikle akış belge modelinin bir parçasıdır. Beyaz alan koruma davranışını destekleyen birincil koleksiyon <xref:System.Windows.Documents.InlineCollection> ' dır. Bu koleksiyon sınıfı <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>ile bildirilmiştir; Bu öznitelik bulunduğunda [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] işlemcisi, koleksiyon içindeki boşlukları önemli ölçüde değerlendirir. `xml:space="preserve"` ve boşluk birleşimi <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> belirtilen bir koleksiyon içinde, tüm boşluklar korunur ve işlenir. Bir <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> içindeki `xml:space="default"` ve boşluk birleşimi, daha önce açıklanan ilk beyaz boşluk normalleştirmesine neden olur ve belirli konumlarda bir boşluk bırakır ve bu boşluklar korunur ve işlenir. Size istenen davranış size bağlı ve istediğiniz davranışı etkinleştirmek için `xml:space` ' ı seçmeniz gerekir.  
  
 Ayrıca, akış belge modelinde bir satır sonu sağlayan belirli satır içi öğeler, bir boşluk açısından önemli bir koleksiyonda bile ek bir boşluk sunmaz. Örneğin, <xref:System.Windows.Documents.LineBreak> öğesi, HTML 'deki \<BR/> etiketiyle aynı amaca sahiptir ve biçimlendirmede okunabilirlik için, genellikle bir <xref:System.Windows.Documents.LineBreak> yazılmış bir linefeed tarafından sonraki metinden ayrılır. Bu satır besleme sonraki satırda önde gelen bir boşluk olacak şekilde normalleştirilmemelidir. Bu davranışı etkinleştirmek için, <xref:System.Windows.Documents.LineBreak> öğesi için sınıf tanımı <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>uygular ve bu, [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] işlemcisi tarafından, <xref:System.Windows.Documents.LineBreak> çevresindeki beyaz alanın her zaman kırpıldıkları anlamına gelir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XAML 'ye Genel Bakış (WPF)](../../desktop-wpf/fundamentals/xaml.md)
- [XML karakter varlıkları ve XAML](xml-character-entities-and-xaml.md)
- [XML: XAML 'de alan işleme](xml-space-handling-in-xaml.md)
