---
title: Tipografi
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], about typography
ms.assetid: 06cbf17b-6eff-4fe5-949d-2dd533e4e1f4
ms.openlocfilehash: 501a4221c99d405484a2fb908641d27d1f38f266
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187346"
---
# <a name="typography-in-wpf"></a>WPF'de Tipografi
Bu konu, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]'nin ana tipografik özelliklerini tanır. Bu özellikler arasında metin oluşturmanın geliştirilmiş kalitesi ve performansı, OpenType tipografi desteği, geliştirilmiş uluslararası metin, geliştirilmiş yazı tipi desteği ve yeni metin uygulama programlama arabirimleri (API'ler) bulunmaktadır.  
  
<a name="Improved_Quality_and_Performance_of_Text"></a>
## <a name="improved-quality-and-performance-of-text"></a>Metnin Kalitesini ve Performansını Artırdı  
 Metin, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] metnin netliğini ve okunabilirliğini artıran Microsoft ClearType kullanılarak işlenir. ClearType, Microsoft tarafından geliştirilen ve dizüstü bilgisayar ekranları, Pocket PC ekranları ve düz panel monitörler gibi mevcut CD'lerde (Liquid Crystal Displays) metnin okunabilirliğini artıran bir yazılım teknolojisidir. ClearType, bir pikselin kesirli bir bölümünde karakterleri hizalayarak metnin gerçek şekline daha fazla doğrulukla görüntülenmesini sağlayan alt piksel oluşturma özelliğini kullanır. Ekstra çözünürlük, metin ekranındaki küçük ayrıntıların netliğini artırarak uzun süreler boyunca okunmasını çok daha kolay hale getirir. ClearType'ın bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] diğer özelliği de metin karakterlerindeki sığ eğrilerin üstve altkısımlarını düzelten y yönü anti-takma addır. ClearType özellikleri hakkında daha fazla bilgi için [ClearType Genel Bakış'a](cleartype-overview.md)bakın.  
  
 ![ClearType y yönü anti-takma ad içeren metin](./media/typography-in-wpf/text-y-direction-antialiasing.gif)  
ClearType y yönü antialiasing ile metin  
  
 Makinenizin gereken minimum donanım düzeyini karşılaması [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] koşuluyla, tüm metin işleme ardışık alanı donanım hızlandırılabilir. Donanım kullanılarak gerçekleştirilemeyen işleme, yazılım işlemeye geri döner. Donanım hızlandırma, tek tek gliflerin depolanması, gliflerin gliflerin biraraya getirilmesi, efektlerin uygulanması ve ClearType karıştırma algoritmasının son görüntülenen çıktıya uygulanmasına kadar metin oluşturma ardışık hattının tüm aşamalarını etkiler. Donanım hızlandırma hakkında daha fazla bilgi için [Grafik Oluşturma Katmanları'na](graphics-rendering-tiers.md)bakın.  
  
 ![Metin oluşturma ardışık lığı diyagramı](./media/typography-in-wpf/text-rendering-pipeline.png)  
  
 Buna ek olarak, animasyonlu metin, karakter veya glyph tarafından etkin [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]grafik donanım yeteneği tam olarak yararlanır. Bu, düzgün metin animasyonu yla sonuçlanır.  
  
<a name="Rich_Typography"></a>
## <a name="rich-typography"></a>Zengin Tipografi  
 OpenType yazı tipi biçimi TrueType® font biçiminin bir uzantısıdır. OpenType yazı tipi biçimi Microsoft ve Adobe tarafından ortaklaşa geliştirilmiştir ve zengin bir gelişmiş tipografik özellik yelpazesine sahiptir. Nesne, <xref:System.Windows.Documents.Typography> stil alternatifleri ve swashes gibi OpenType yazı tiplerinin gelişmiş özelliklerinin çoğunu ortaya çıkarır. Windows SDK, Perikles ve Pescadero yazı tipleri gibi zengin özelliklere sahip bir dizi örnek OpenType yazı tipi sağlar. Daha fazla bilgi için [Örnek OpenType Yazı Tipi Paketi'ne](sample-opentype-font-pack.md)bakın.  
  
 Pericles OpenType yazı tipi, standart glifler kümesine stil alternatifleri sağlayan ek glifler içerir. Aşağıdaki metin de stilistik alternatif glifleri görüntüler.  
  
 ![OpenType stilistik alternatif glifleri kullanarak metin](./media/typography-in-wpf/opentype-stylistic-alternate-glyphs.gif "OpenType stilistik alternatif glifleri kullanarak metin")  
  
 Swashes genellikle kaligrafi ile ilişkili ayrıntılı süsleme kullanan dekoratif glifler vardır. Aşağıdaki metin Pescadero yazı tipi için standart ve swash glifleri görüntüler.  
  
 ![OpenType standardı ve swash glifleri kullanan metin](./media/typography-in-wpf/opentype-standard-swash-glyphs.gif "OpenType standardı ve swash glifleri kullanan metin")  
  
 OpenType özellikleri hakkında daha fazla bilgi için [OpenType Font Özellikleri'ne](opentype-font-features.md)bakın.  
  
<a name="Enhanced_International_Text_Support"></a>
## <a name="enhanced-international-text-support"></a>Geliştirilmiş Uluslararası Metin Desteği  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]aşağıdaki özellikleri sağlayarak gelişmiş uluslararası metin desteği sağlar:  
  
- Tüm yazma sistemlerinde, uyarlanabilir ölçüm kullanarak otomatik satır aralığı.  
  
- Uluslararası metin için geniş destek. Daha fazla bilgi [için WPF için Küreselleşme'ye](globalization-for-wpf.md)bakın.  
  
- Dil kılavuzlu satır kesme, heceleme ve yaslama.  
  
<a name="Enhanced_Font_Support"></a>
## <a name="enhanced-font-support"></a>Geliştirilmiş Font Desteği  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]aşağıdaki özellikleri sağlayarak gelişmiş yazı tipi desteği sağlar:  
  
- Tüm metinler için unicode. Yazı tipi davranışı ve seçimi artık charset veya codepage gerektirmez.  
  
- Sistem yerel ayarları gibi genel ayarlardan bağımsız yazı tipi davranışı.  
  
- Ayrı <xref:System.Windows.FontWeight> <xref:System.Windows.FontStretch>, <xref:System.Windows.FontStyle> ve bir <xref:System.Windows.Media.FontFamily>tanımlamak için türleri . Bu, boolean italik ve kalın birleşimlerinin bir yazı tipi ailesini tanımlamak için kullanıldığı Win32 programlamasına göre daha fazla esneklik sağlar.  
  
- Yazı tipi adından bağımsız olarak işlenen yazı yönü (yatay karşı dikey) işlenir.  
  
- Bileşik yazı tipi teknolojisini kullanarak taşınabilir bir XML dosyasında yazı tipi bağlama ve yazı tipi geri dönüş. Bileşik yazı tipleri, tam kapsamlı çok dilli yazı tiplerinin yapımına olanak sağlar. Bileşik yazı tipleri de eksik gliflerin görüntülenmesini önleyen bir mekanizma sağlar. Daha fazla bilgi için sınıftaki açıklamalara <xref:System.Windows.Media.FontFamily> bakın.  
  
- Tek dilli yazı tipleri grubu kullanarak bileşik yazı tiplerinden oluşturulmuş uluslararası yazı tipleri. Bu, birden çok dil için yazı tipleri geliştirirken kaynak maliyetlerinde tasarruf sağlar.  
  
- Belgeye katıştılmış bileşik yazı tipleri, belge taşınabilirliği sağlar. Daha fazla bilgi için sınıftaki açıklamalara <xref:System.Windows.Media.FontFamily> bakın.  
  
<a name="New_Text_APIs"></a>
## <a name="new-text-application-programming-interfaces-apis"></a>Yeni Metin Uygulama Programlama Arayüzleri (API'ler)  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]geliştiricilerin uygulamalarına metin dahil ederken kullanmaları için çeşitli metin API'leri sağlar. Bu API'ler üç kategoriye ayrılır:  
  
- **Düzen ve kullanıcı arabirimi.** Grafik kullanıcı arabirimi (GUI) için ortak metin denetimleri.  
  
- **Hafif metin çizimi.** Metni doğrudan nesnelere çizmenizi sağlar.  
  
- **Gelişmiş metin biçimlendirme.** Özel bir metin altyapısı uygulamanızı sağlar.  
  
### <a name="layout-and-user-interface"></a>Düzen ve Kullanıcı Arabirimi  
 En [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] üst düzeyde işlevsellik, metin API'leri <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.TextBlock>, <xref:System.Windows.Controls.TextBox>ve . Bu denetimler [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] bir uygulama içindeki temel öğeleri sağlar ve metin sunmak ve metinle etkileşimde bulunmanın kolay bir yolunu sunar. Daha gelişmiş <xref:System.Windows.Controls.RichTextBox> <xref:System.Windows.Controls.PasswordBox> veya özel metin işleme gibi denetimler ve etkinleştirme. Ve , <xref:System.Windows.Documents.TextRange>, <xref:System.Windows.Documents.TextSelection>gibi <xref:System.Windows.Documents.TextPointer> sınıflar ve yararlı metin işleme sağlar. Bu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] denetimler, <xref:System.Windows.Controls.Control.FontFamily%2A>metni <xref:System.Windows.Controls.Control.FontSize%2A>işlemek <xref:System.Windows.Controls.Control.FontStyle%2A>için kullanılan yazı tipini denetlemenizi sağlayan , , ve , gibi özellikler sağlar.  
  
#### <a name="using-bitmap-effects-transforms-and-text-effects"></a>Bitmap Efektlerini, Dönüşümleri ve Metin Efektlerini Kullanma  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]bitmap efektleri, dönüşümler ve metin efektleri gibi özellikleri kullanarak metnin görsel olarak ilginç kullanımlarını oluşturmanıza olanak tanır. Aşağıdaki örnek, metne uygulanan tipik bir açılır gölge efekti türünü gösterir.  
  
 ![Yumuşaklıklı metin gölgesi 0,25 &#61;](./media/typography-in-wpf/drop-shadow-text-effect.jpg)
  
 Aşağıdaki örnekte, metne uygulanan bir damla gölge efekti ve gürültü gösterilmektedir.  
  
 ![Gürültüiçeren metin gölgesi](./media/typography-in-wpf/drop-shadow-noise-text.jpg)
  
 Aşağıdaki örnekte, metne uygulanan bir dış parlaklık efekti gösterilmektedir.  
  
 ![OuterGlowBitmapEffect kullanarak metin gölgesi](./media/typography-in-wpf/text-shadow-glow-effect.jpg)
  
 Aşağıdaki örnekte metne uygulanan bulanıklık efekti gösterilmektedir.  
  
 ![BlurBitmapEffect kullanarak metin gölgesi](./media/typography-in-wpf/text-shadow-blur-effect.jpg)  

 Aşağıdaki örnek, x ekseni boyunca %150 ölçeklendirilen ikinci metin satırını ve y ekseni boyunca %150 ölçeklendirilen üçüncü metin satırını gösterir.  
  
 ![Bir ScaleTransform kullanılarak ölçeklendirilen metin](./media/typography-in-wpf/scaled-text-scaletransform.jpg)
  
 Aşağıdaki örnek, x ekseni boyunca eğriltilen metni gösterir.  
  
 ![SkewTransform kullanılarak eğriltilen metin](./media/typography-in-wpf/skewed-transformed-text.jpg)
  
 <xref:System.Windows.Media.TextEffect> Nesne, metin dizesinde bir veya daha fazla karakter grubu olarak metni ele alabildiğiniz yardımcı nesnedir. Aşağıdaki örnekte, döndürülen tek bir karakter gösterilmektedir. Her karakter 1 saniyelik aralıklarla bağımsız olarak döndürülür.  
  
 ![Metin efekti dönen metin ekran görüntüsü](./media/typography-in-wpf/rotating-text-effect.jpg)
  
#### <a name="using-flow-documents"></a>Akış Belgelerini Kullanma  
 Ortak [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] denetimlere ek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olarak, metin sunumu için <xref:System.Windows.Documents.FlowDocument> bir düzen denetimi sunar- öğe. Öğe, <xref:System.Windows.Documents.FlowDocument> <xref:System.Windows.Controls.DocumentViewer> öğeyle birlikte, değişen düzen gereksinimlerine sahip büyük miktarda metin için bir denetim sağlar. Düzen <xref:System.Windows.Documents.Typography> denetimleri, nesne ve yazı tipi ile ilgili diğer [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] denetimlerin özellikleri aracılığıyla gelişmiş tipografiye erişim sağlar.  
  
 Aşağıdaki örnek, arama, gezinme, pagination ve içerik ölçekleme desteği sağlayan bir <xref:System.Windows.Controls.FlowDocumentReader>, barındırılan metin içeriğini gösterir.  
  
 ![OpenType yazı tiplerini gösteren ekran görüntüsü.](./media/typography-in-wpf/typography-text-flowdocumentreader.png)
  
 Daha fazla bilgi için [WPF'deki Belgeler'e](documents-in-wpf.md)bakın.  
  
### <a name="lightweight-text-drawing"></a>Hafif Metin Çizimi  
 Nesnenin yöntemini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Media.DrawingContext.DrawText%2A> kullanarak doğrudan nesnelere metin çizebilirsiniz. <xref:System.Windows.Media.DrawingContext> Bu yöntemi kullanmak için <xref:System.Windows.Media.FormattedText> bir nesne oluşturursunuz. Bu nesne, metindeki her karakterin ayrı ayrı biçimlendirilebildiği çok satırlı metin çizmenize olanak tanır. <xref:System.Windows.Media.FormattedText> Nesnenin işlevselliği, Windows API'daki DrawText bayraklarının işlevselliğinin çoğunu içerir. Ayrıca, <xref:System.Windows.Media.FormattedText> nesne, metin sınırlarını aştığında bir elipsin görüntülendiği elips desteği gibi işlevler içerir. Aşağıdaki örnekte, ikinci ve üçüncü sözcüklerde doğrusal bir degrade de dahil olmak üzere çeşitli biçimler uygulanmış metin gösterilmektedir.  
  
 ![BiçimlendirilmişMetin nesnesi kullanılarak görüntülenen metin](./media/typography-in-wpf/text-formatted-linear-gradient.jpg)
  
 Biçimlendirilmiş metni nesnelere <xref:System.Windows.Media.Geometry> dönüştürerek görsel olarak ilginç başka metin türleri oluşturabilirsiniz. Örneğin, bir metin <xref:System.Windows.Media.Geometry> dizesinin anahatlarını temel alan bir nesne oluşturabilirsiniz.  
  
 ![Doğrusal degrade fırçası kullanarak metin anahattı](./media/typography-in-wpf/text-outline-linear-gradient.jpg)  
  
 Aşağıdaki örnekler, dönüştürülen metnin konturunu, dolgusunu ve vurgusunu değiştirerek ilginç görsel efektler oluşturmanın çeşitli yollarını göstermektedir.  
  
 ![Dolgu ve kontur için farklı renklere sahip metin](./media/typography-in-wpf/fill-stroke-text-effect.jpg)  
  
 ![Kontura uygulanan görüntü fırçası ile metin](./media/typography-in-wpf/image-brush-application.jpg)
  
 ![Kontur ve vurgulamaya uygulanan görüntü fırçası ile metin](./media/typography-in-wpf/image-brush-text-application.jpg)
  
 <xref:System.Windows.Media.FormattedText> Nesne hakkında daha fazla bilgi için, Çizim [Biçimlendirilmiş Metin'e](drawing-formatted-text.md)bakın.  
  
### <a name="advanced-text-formatting"></a>Gelişmiş Metin Biçimlendirme  
 Metin API'lerinin en gelişmiş [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzeyinde, <xref:System.Windows.Media.TextFormatting.TextFormatter> <xref:System.Windows.Media.TextFormatting> ad alanındaki nesneyi ve diğer türleri kullanarak özel metin düzeni oluşturma olanağı sunar. <xref:System.Windows.Media.TextFormatting.TextFormatter> Ve ilişkili sınıflar, karakter biçimleri, paragraf stilleri, satır kesme kuralları ve uluslararası metin için diğer düzen özelliklerini kendi tanımınızı destekleyen özel metin düzeni uygulamanıza olanak sağlar. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Metin düzeni desteğinin varsayılan uygulamasını geçersiz kılmak istediğiniz çok az servis vardır. Ancak, metin düzenleme denetimi veya uygulaması oluşturuyorsanız, varsayılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamadan farklı bir uygulama isteyebilirsiniz.  
  
 Geleneksel metin API'sinin <xref:System.Windows.Media.TextFormatting.TextFormatter> aksine, bir dizi geri arama yöntemi yle metin düzeni istemcisi ile etkileşim kurar. Bu <xref:System.Windows.Media.TextFormatting.TextSource> sınıfın bir uygulamada bu yöntemleri sağlamak için istemci gerektirir. Aşağıdaki diyagram, istemci uygulaması ve <xref:System.Windows.Media.TextFormatting.TextFormatter>.  
  
 ![Metin düzeni istemcisi ve TextFormatter diyagramı](./media/typography-in-wpf/text-layout-text-formatter-interaction.png)  
  
 Özel metin düzeni oluşturma hakkında daha fazla bilgi için [Gelişmiş Metin Biçimlendirme'ye](advanced-text-formatting.md)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.FormattedText>
- <xref:System.Windows.Media.TextFormatting.TextFormatter>
- [ClearType Genel Bakışı](cleartype-overview.md)
- [OpenType Yazı Tipi Özellikleri](opentype-font-features.md)
- [Biçimlendirilmiş Metin Çizme](drawing-formatted-text.md)
- [Gelişmiş Metin Biçimlendirme](advanced-text-formatting.md)
- [Metin](optimizing-performance-text.md)
- [Microsoft Tipografi](https://docs.microsoft.com/typography/)
