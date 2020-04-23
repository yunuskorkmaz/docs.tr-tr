---
title: XAML'de Boşluk İşleme
ms.date: 03/30/2017
helpviewer_keywords:
- East Asian characters [XAML Services]
- XAML [XAML Services], white-space processing
- white-space processing in XAML [XAML Services]
- characters [XAML Services], East Asian
ms.assetid: cc9cc377-7544-4fd0-b65b-117b90bb0b23
ms.openlocfilehash: 05f28c9115326424164b92e1b704c52bba31cf35
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071607"
---
# <a name="white-space-processing-in-xaml"></a>XAML'de Boşluk İşleme

XAML için dil kuralları önemli beyaz alan bir [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] işlemci uygulaması tarafından işlenmesi gerektiğini belirtir. Bu makalede, bu XAML dil kuralları belgeler. Ayrıca, XAML işlemcive serileştirme [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] için XAML yazıcısının uygulanmasıyla tanımlanan ek boşluk işleme yi de belgeler.

## <a name="white-space-definition"></a>Beyaz boşluk tanımı

XML ile tutarlı, beyaz boşluk [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] karakterleri boşluk, satır beslemesi ve sekmesi vardır. Bunlar sırasıyla 0020, 000A ve 0009 Unicode değerlerine karşılık gelir.

## <a name="white-space-normalization"></a>Beyaz boşluk normalleştirme

Varsayılan olarak, bir [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] işlemci bir [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] dosyayı işlediğinde aşağıdaki beyaz boşluk normalleştirmesi oluşur:

1. Doğu Asya karakterleri arasındaki satır akışı karakterleri kaldırılır. Bu terimin tanımı için bu konunun daha sonra "Doğu Asya Karakterleri" bölümüne bakın.

2. Tüm boşluk karakterleri (boşluk, satır besleme, sekme) boşluklara dönüştürülür.

3. Ardışık tüm boşluklar silinir ve tek bir boşlukla değiştirilir.

4. Başlangıç etiketini hemen izleyen bir boşluk silinir.

5. Bitiş etiketi silinmeden hemen önce bir boşluk.

"Varsayılan" [xml:space](xml-space-handling.md) özniteliğinin varsayılan değeriyle gösterilen duruma karşılık gelir.

## <a name="white-space-in-inner-text-and-string-primitives"></a>İç metinde beyaz boşluk ve dize ilkel

Önceki normalleştirme kuralları XAML öğeleri içinde bulunan iç metin için geçerlidir. Normalleştirmeden sonra, Bir XAML işlemci aşağıdaki gibi uygun bir tür içine herhangi bir iç metin dönüştürür:

- Özelliğin türü bir koleksiyon değilse ancak doğrudan <xref:System.Object> bir tür değilse, XAML işlemci türü dönüştürücüsünü kullanarak bu türe dönüştürmeye çalışır. Burada başarısız bir dönüşüm derleme zamanı hatasına neden olur.

- Özelliğin türü bir koleksiyon ve iç metin bitişik (hiçbir müdahale öğesi etiketleri), iç metin tek <xref:System.String>bir . Koleksiyon türü kabul <xref:System.String>edemiyorsa, bu da derleme zamanı hatasına neden olur.

- Özelliğin türü ise, <xref:System.Object>iç metin tek <xref:System.String>olarak ayrıştırılır. Araya giren öğe etiketleri varsa, bu tür tek bir <xref:System.Object> nesneyi (veya<xref:System.String> başka bir şekilde) ima ettiği için derleme zamanı hatasına neden olur.

- Özelliğin türü bir koleksiyon ise ve iç metin bitişik değilse, ilk alt dize <xref:System.String> bir a dönüştürülür ve bir koleksiyon öğesi olarak eklenir, ara veren öğe bir koleksiyon öğesi olarak eklenir ve son <xref:System.String> olarak son olarak son olarak alt dize (varsa) üçüncü bir öğe olarak koleksiyona eklenir.

## <a name="preserving-white-space"></a>Beyaz boşluğu koruma

İşlemci beyaz alan normalleştirme etkilenmez [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] nihai sunu için kaynak beyaz alanı korumak için çeşitli teknikler vardır. [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]

**xml:space="preserve"**: Bu özniteliği, beyaz boşluk korumanın istendiği öğe düzeyinde belirtin. Bu, kod düzenleme uygulamaları tarafından "oldukça yazdırma" öğelerini görsel olarak sezgisel bir iç içe işlem olarak hizalamak için eklenebilir boşlukları içeren tüm beyaz alanı korur. Ancak, bu boşlukların işlenip işlenmediği, içerdiği öğenin içerik modeli tarafından belirlenir. Çoğu nesne `xml:space="preserve"` modeli özniteliği nasıl ayarlarsanız kümelediğinize bakılmaksızın beyaz alanı önemli olarak kabul etmediğinden kök düzeyinde belirtmekten kaçının. Genel `xml:space` olarak ayar, bazı uygulamalarda XAML işleme (özellikle serileştirme) üzerinde performans sonuçları doğurabilir. Özniteliği yalnızca dizeler içinde beyaz boşluk oluşturan veya beyaz boşluk oluşturan öğeler düzeyinde ayarlamak daha iyi bir uygulamadır.

**Varlıklar ve kırılmayan boşluklar:** [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] Herhangi bir Unicode varlığının metin nesnesi modeline yerleştirimi destekler. Kırılmayan alan (160 &; \#UTF-8 kodlaması gibi özel varlıkları kullanabilirsiniz. Kırılmayan alan karakterlerini destekleyen zengin metin denetimlerini de kullanabilirsiniz. Varlıkların çalışma zamanı çıktısı, panellerin ve kenar boşluklarının doğru kullanımı gibi tipik bir düzen sisteminde girinti sonuçları oluşturma yeteneklerinden daha fazla sayıda etkene bağlı olarak değişeceği için, girinti gibi düzen özelliklerini simüle etmek için varlıkları kullanıyorsanız dikkatli olmalısınız. Örneğin, varlıklar yazı tiplerine eşlenir ve kullanıcı yazı tipi seçimine yanıt olarak boyutu değiştirebilir.

## <a name="east-asian-characters"></a>Doğu Asya karakterleri

"Doğu Asya karakterleri" Unicode karakter aralıkları U+20000 ile U+2FFFD ve U+30000 -U+3FFFD arasında bir dizi olarak tanımlanır. Bu alt küme bazen "CJK ideographs" olarak da adlandırılır. Daha fazla bilgi için bkz. <https://www.unicode.org>.

## <a name="white-space-and-text-content-models"></a>Beyaz alan ve metin içeriği modelleri

Uygulamada, beyaz alanı korumak yalnızca olası tüm içerik modellerinin bir alt kümesi için önemlidir. Bu alt küme, bir biçimde tek ton <xref:System.String> türü, özel <xref:System.String> bir koleksiyon veya <xref:System.String> bir <xref:System.Collections.IList> veya <xref:System.Collections.Generic.ICollection%601> koleksiyondaki diğer türlerin bir karışımını alabilen içerik modellerinden oluşur.

### <a name="white-space-and-text-content-models-in-wpf"></a>WPF'de beyaz alan ve metin içeriği modelleri

Çizim amacıyla, bu bölümün geri kalanı WPF tarafından tanımlanan belirli türlerden başvurur. Bu makalede açıklanan beyaz alan işleme özellikleri hem .NET XAML Hizmetleri hem de WPF ile ilgilidir. Bu davranışı iş başında görmek için, bazı WPF XAML biçimlendirmesini deneyebilir, sonuçları bir nesne grafiğinde görüntüleyebilir ve sonra yeniden işaretlemek için seri hale getirebilirsiniz.

Dizeleri alabilen içerik modelleri için bile, bu içerik modelleri içindeki varsayılan davranış, kalan herhangi bir beyaz alanın önemli olarak kabul edilmemesidir. Örneğin, <xref:System.Windows.Controls.ListBox> bir <xref:System.Collections.IList>, ancak beyaz boşluk (her <xref:System.Windows.Controls.ListBoxItem>biri arasındaki satır akışları gibi) korunmuş değildir ve işlenmez. Satır akışlarını öğeler için <xref:System.Windows.Controls.ListBoxItem> dizeleri arasında ayırıcı olarak kullanmaya çalışırsanız, hiç çalışmaz; satır akışları ile ayrılan dizeleri bir dize ve bir öğe olarak kabul edilir.

Beyaz alanı önemli olarak ele alan bu koleksiyonlar genellikle akış belgesi modelinin bir parçasıdır. Beyaz alanı koruma davranışını destekleyen <xref:System.Windows.Documents.InlineCollection>birincil koleksiyon. Bu koleksiyon sınıfı ile <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>bildirilir; Bu öznitelik bulunduğunda, [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] işlemci koleksiyondaki beyaz alanı önemli olarak ele alacaktır. Belirtilen bir `xml:space="preserve"` <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> koleksiyondaki ve beyaz boşluğun birleşimi, tüm beyaz alanın korunmuş ve işlenmiş olmasıdır. Bir ve `xml:space="default"` beyaz <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> uzayın birleşimi daha önce açıklanan ilk beyaz boşluk normalizasyonuna neden olur, bu da belirli konumlarda bir boşluk bırakır ve bu boşluklar korunur ve işlenir. Hangi davranışın arzu edilir size kalmış `xml:space` ve istediğiniz davranışı etkinleştirmek için seçici olarak kullanmalısınız.

Ayrıca, akış belgesi modelinde bir satır sonu ifade eden bazı satır içi öğeler, bir beyaz boşluk önemli koleksiyonunda bile kasıtlı olarak fazladan bir boşluk tanıtmamalıdır. Örneğin, <xref:System.Windows.Documents.LineBreak> öğe NIN HTML'deki \<BR/> etiketiyle aynı amacı vardır ve biçimlendirmede <xref:System.Windows.Documents.LineBreak> okunabilirlik için genellikle a, sonraki herhangi bir metinden yazarlı bir satır akışıyla ayrılır. Bu satır beslemesi sonraki satırda bir satır alanı olmak için normalleştirilmemelidir. Bu davranışı etkinleştirmek için, <xref:System.Windows.Documents.LineBreak> öğenin sınıf <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>tanımı, [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] daha sonra işlemci tarafından çevreleyen beyaz <xref:System.Windows.Documents.LineBreak> boşluğun her zaman kırpıldığı anlamına gelen yorumlanır.

## <a name="see-also"></a>Ayrıca bkz.

- [XAML genel bakış (WPF)](../fundamentals/xaml.md)
- [XML karakter varlıkları ve XAML](xml-character-entities.md)
- [xml:XAML'de boşluk taşıma](xml-space-handling.md)
