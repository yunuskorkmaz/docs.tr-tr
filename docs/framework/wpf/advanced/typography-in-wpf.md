---
title: WPF'de Tipografi
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], about typography
ms.assetid: 06cbf17b-6eff-4fe5-949d-2dd533e4e1f4
ms.openlocfilehash: ffbd59cb398d417a36d75ff0ef9ef4ef143c30c0
ms.sourcegitcommit: 4b9c2d893b45d47048c6598b4182ba87759b1b59
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68484642"
---
# <a name="typography-in-wpf"></a>WPF'de Tipografi
Bu konuda, uygulamasının [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]önemli tipografik özellikleri tanıtılmaktadır. Bu özellikler, metin işleme, [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] tipografi desteği, gelişmiş uluslararası metin, gelişmiş yazı tipi desteği ve yeni metin uygulama programlama arabirimleri (API 'ler) için geliştirilmiş kalite ve performans içerir.  
  
<a name="Improved_Quality_and_Performance_of_Text"></a>   
## <a name="improved-quality-and-performance-of-text"></a>Metnin geliştirilmiş kalitesi ve performansı  
 İçindeki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] metin, metnin açıklık [!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)]ve okunabilirliğini artıran kullanılarak işlenir. ClearType, dizüstü ekranları, Pocket PC [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] ekranları ve düz panel izleyicileri gibi mevcut LCD 'lerde (sıvı kristal ekranlar) metnin okunabilirliğini artıran, tarafından geliştirilen bir yazılım teknolojisidir. ClearType, bir pikselin kesirli bölümünde karakterler hizalanarak metnin gerçek şeklinin daha büyük bir uygunluğa eşit bir şekilde görüntülenmesine olanak sağlayan alt piksel işleme kullanır. Ek çözüm, metin görüntüleme içindeki küçük ayrıntıların keskinliğini artırarak uzun süreleri okumayı çok daha kolay hale getirir. ' Deki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] başka bir ClearType geliştirmesi, metin karakterlerine yönelik yüzeysel eğrilerinin ve altları düzgüneden, y yönü düzgünleştirmedir. ClearType özellikleri hakkında daha fazla bilgi için bkz. [ClearType Genel Bakış](cleartype-overview.md).  
  
 ![ClearType y yönü düzgünleştirmesini içeren metin](./media/typography-in-wpf/text-y-direction-antialiasing.gif)  
ClearType y yönünde düzgünleştirme içeren metin  
  
 Tüm metin işleme işlem hattı, makinenizde gereken en düşük donanım [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzeyini karşılaması şartıyla donanım hızlandırılır. Donanım kullanılarak gerçekleştirilemediği işleme, yazılım işlemeye geri döner. Donanım hızlandırma, metin işleme işlem hattının tüm aşamalarını etkiler. tek glifleri depolamadan, glifleri karakter çalıştırmalarıyla birleştirme, etkileri uygulama, son görünen çıktıya ClearType karıştırma algoritmasını uygulama. Donanım hızlandırma hakkında daha fazla bilgi için bkz. [grafik Işleme katmanları](graphics-rendering-tiers.md).  
  
 ![Metin işleme işlem hattının diyagramı](./media/typography-in-wpf/text-rendering-pipeline.png)  
  
 Buna ek olarak, karakter veya karakter olarak hareketli metin, tarafından [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]etkinleştirilen grafik donanım yeteneğinin tam avantajlarından yararlanır. Bu, düz metin animasyonuna neden olur.  
  
<a name="Rich_Typography"></a>   
## <a name="rich-typography"></a>Zengin tipografi  
 Yazı tipi biçimi, [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)] yazı tipi biçiminin bir uzantısıdır. [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] Yazı tipi biçimi, ve Adobe tarafından [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] ortaklaşa geliştirilmiştir ve zengin bir gelişmiş tipografik özellikler sunar. [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] Nesnesi, [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] yazı tiplerinin stil alternatifleri ve süslemeler gibi gelişmiş özelliklerinin çoğunu gösterir. <xref:System.Windows.Documents.Typography> , [!INCLUDE[TLA2#tla_lhsdk](../../../../includes/tla2sharptla-lhsdk-md.md)] Pericles ve Pescadero fontları gibi zengin özelliklerle tasarlanan bir örnek [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] yazı tipi kümesi sağlar. Daha fazla bilgi için bkz. [örnek OpenType yazı tipi paketi](sample-opentype-font-pack.md).  
  
 Pericles [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] yazı tipi, standart glif kümesine stil alternatifleri sağlayan ek glifler içerir. Aşağıdaki metin, biçimsel alternatif glifleri görüntüler.  
  
 ![OpenType biçimsel alternatif glifleri kullanan metin](./media/typography-in-wpf/opentype-stylistic-alternate-glyphs.gif "OpenType biçimsel alternatif glifleri kullanan metin")  
  
 Süslemeler, kaligrafi ile sık kullanılan süslemeler ile ilişkili olan dekoratif karakterlerdir. Aşağıdaki metin Pescadero yazı tipi için standart ve dalgalı glifleri görüntüler.  
  
 ![OpenType standart ve dalgalı glifleri kullanan metin](./media/typography-in-wpf/opentype-standard-swash-glyphs.gif "OpenType standart ve dalgalı glifleri kullanan metin")  
  
 Özellikler hakkında [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] daha fazla bilgi için bkz. [OpenType yazı tipi özellikleri](opentype-font-features.md).  
  
<a name="Enhanced_International_Text_Support"></a>   
## <a name="enhanced-international-text-support"></a>Gelişmiş uluslararası metin desteği  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]aşağıdaki özellikleri sağlayarak gelişmiş uluslararası metin desteği sağlar:  
  
- Uyarlamalı ölçüm kullanarak tüm yazma sistemlerinde otomatik satır aralığı.  
  
- Uluslararası metin için geniş destek. Daha fazla bilgi için bkz. [WPF Için Genelleştirme](globalization-for-wpf.md).  
  
- Dil temelli satır sonu, heceleme ve gerekçe.  
  
<a name="Enhanced_Font_Support"></a>   
## <a name="enhanced-font-support"></a>Gelişmiş yazı tipi desteği  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]aşağıdaki özellikleri sağlayarak gelişmiş yazı tipi desteği sağlar:  
  
- Tüm metinler için Unicode. Yazı tipi davranışı ve seçimi artık karakter kümesi veya kod sayfası gerektirmez.  
  
- Sistem yerel ayarı gibi genel ayarlardan bağımsız yazı tipi davranışı.  
  
- Tanımlama <xref:System.Windows.FontWeight>için <xref:System.Windows.FontStretch>ayrı, <xref:System.Windows.FontStyle>vetürleri. <xref:System.Windows.Media.FontFamily> Bu, bir yazı tipi ailesini [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] tanımlamak için italik ve kalın olan Boole birleşimlerinin kullanıldığı, programlamadan daha fazla esneklik sağlar.  
  
- Yazma yönü (yatay veya dikey), yazı tipi adından bağımsız olarak işlenir.  
  
- Bileşik yazı tipi teknolojisini kullanarak taşınabilir [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] bir dosyaya yazı tipi bağlama ve yazı tipi düşürme. Bileşik yazı tipleri, tam aralıklı çok dilli yazı tiplerinin oluşturulmasını sağlar. Bileşik yazı tipleri ayrıca eksik karakterlerin görüntülenmesini önleyen bir mekanizma sağlar. Daha fazla bilgi için, <xref:System.Windows.Media.FontFamily> sınıfındaki açıklamalara bakın.  
  
- Tek dildeki bir yazı tipi grubu kullanılarak bileşik yazı tiplerinden oluşturulan uluslararası yazı tipleri. Bu, birden çok dil için yazı tipi geliştirirken kaynak maliyetlerine kaydedilir.  
  
- Belge taşınabilirliği sağlayan bileşik yazı tipleri bir belgeye katıştırılır. Daha fazla bilgi için, <xref:System.Windows.Media.FontFamily> sınıfındaki açıklamalara bakın.  
  
<a name="New_Text_APIs"></a>   
## <a name="new-text-application-programming-interfaces-apis"></a>Yeni metin uygulama programlama arabirimleri (API 'Ler)  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]geliştiricilerin uygulamalarına metin eklerken kullanacağı birkaç metin API 'si sağlar. Bu API 'Ler üç kategoride gruplandırılır:  
  
- **Düzen ve Kullanıcı arabirimi**. İçin ortak metin denetimleri [!INCLUDE[TLA#tla_gui](../../../../includes/tlasharptla-gui-md.md)].  
  
- **Hafif metin çizme**. Doğrudan nesnelere metin çizmenizi sağlar.  
  
- **Gelişmiş metin biçimlendirme**. Özel bir metin altyapısı uygulamanıza olanak tanır.  
  
### <a name="layout-and-user-interface"></a>Düzen ve Kullanıcı arabirimi  
 En yüksek düzeyde işlevsellik, metin API 'leri, [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] , ve <xref:System.Windows.Controls.TextBox>gibi ortak denetimleri <xref:System.Windows.Controls.Label> <xref:System.Windows.Controls.TextBlock>sağlar. Bu denetimler bir uygulama içindeki [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] temel öğeleri sağlar ve metin sunmak ve bunlarla etkileşim kurmak için kolay bir yol sunar. Ve gibi denetimler, <xref:System.Windows.Controls.PasswordBox> daha gelişmiş veya özelleştirilmiş metin işleme sağlar. <xref:System.Windows.Controls.RichTextBox> Ve <xref:System.Windows.Documents.TextRange>, <xref:System.Windows.Documents.TextSelection>, ve<xref:System.Windows.Documents.TextPointer> gibi sınıflar yararlı metin işlemesini etkinleştirir. Bu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] <xref:System.Windows.Controls.Control.FontFamily%2A>denetimler, ,<xref:System.Windows.Controls.Control.FontSize%2A>ve gibiözelliklerisağlar,budametniişlemekiçinkullanılanyazı<xref:System.Windows.Controls.Control.FontStyle%2A>tipini denetlemenizi sağlar.  
  
#### <a name="using-bitmap-effects-transforms-and-text-effects"></a>Bit eşlem efektleri, dönüşümler ve metin efektlerini kullanma  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]bit eşlem efektleri, dönüşümler ve metin etkileri gibi özellikleri kullanarak metnin görsel açıdan ilgi çekici kullanımlarını oluşturmanızı sağlar. Aşağıdaki örnek, metin için uygulanan tipik bir gölge etkisi türünü gösterir.  
  
 ![Soflük &#61; 0,25 ile metin gölgesi](./media/typography-in-wpf/drop-shadow-text-effect.jpg) 
  
 Aşağıdaki örnekte, bir gölge efekti ve metne uygulanan gürültü gösterilmektedir.  
  
 ![Gürültü içeren metin gölgesi](./media/typography-in-wpf/drop-shadow-noise-text.jpg) 
  
 Aşağıdaki örnek, metne uygulanan bir dış ışıma efektini gösterir.  
  
 ![OuterGlowBitmapEffect kullanarak metin gölgesi](./media/typography-in-wpf/text-shadow-glow-effect.jpg)
  
 Aşağıdaki örnek, metne uygulanan bir bulanıklaştırma efektini gösterir.  
  
 ![Bir BlurBitmapEffect kullanarak metin gölgesi](./media/typography-in-wpf/text-shadow-blur-effect.jpg)  

 Aşağıdaki örnek, x ekseni ve y ekseni üzerinde% 150 ile ölçeklenmiş üçüncü metin satırındaki 150 metnin ikinci satırını gösterir.  
  
 ![ScaleTransform kullanılarak Ölçeklendirilmiş metin](./media/typography-in-wpf/scaled-text-scaletransform.jpg) 
  
 Aşağıdaki örnek, x ekseni üzerinde eğilmiş metni gösterir.  
  
 ![SkewTransform kullanarak eğilmiş metin](./media/typography-in-wpf/skewed-transformed-text.jpg)
  
 Bir <xref:System.Windows.Media.TextEffect> nesne, metni bir metin dizesinde bir veya daha fazla karakter grubu olarak değerlendirme olanağı sağlayan bir yardımcı nesnedir. Aşağıdaki örnek, döndürülmekte olan ayrı bir karakteri gösterir. Her karakter, 1 saniyelik aralıklarla bağımsız olarak döndürülür.  
  
 ![Metin döndürme metin efektinin ekran görüntüsü](./media/typography-in-wpf/rotating-text-effect.jpg) 
  
#### <a name="using-flow-documents"></a>Flow belgelerini kullanma  
 Ortak [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] denetimlere ek olarak, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] metin sunumu <xref:System.Windows.Documents.FlowDocument> için bir düzen denetimi sağlar — öğesi. <xref:System.Windows.Documents.FlowDocument> Öğesi<xref:System.Windows.Controls.DocumentViewer> ile birlikte, farklı düzen gereksinimlerine sahip büyük miktarda metin için bir denetim sağlar. Düzen denetimleri, diğer <xref:System.Windows.Documents.Typography> [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] denetimlerin, nesne ve yazı tipi ile ilgili özellikler aracılığıyla Gelişmiş tipografi erişimi sağlar.  
  
 Aşağıdaki örnek, içinde <xref:System.Windows.Controls.FlowDocumentReader>barındırılan, arama, gezinme, sayfalandırma ve içerik ölçekleme desteği sağlayan metin içeriğini gösterir.  
  
 ![OpenType yazı tiplerini gösteren ekran görüntüsü.](./media/typography-in-wpf/typography-text-flowdocumentreader.png)
  
 Daha fazla bilgi için bkz. [WPF Içindeki belgeler](documents-in-wpf.md).  
  
### <a name="lightweight-text-drawing"></a>Hafif metin çizme  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Nesnenin yöntemini<xref:System.Windows.Media.DrawingContext.DrawText%2A> kullanarak doğrudan nesnelere metin çizebilirsiniz. <xref:System.Windows.Media.DrawingContext> Bu yöntemi kullanmak için bir <xref:System.Windows.Media.FormattedText> nesnesi oluşturun. Bu nesne, metin içindeki her karakterin tek tek biçimlendirilebileceği çok satırlı metin çizmenizi sağlar. <xref:System.Windows.Media.FormattedText> Nesnesinin işlevselliği, Windows API 'sindeki DrawText bayraklarının işlevlerinin çoğunu içerir. Ayrıca, <xref:System.Windows.Media.FormattedText> nesnesi, metin sınırlarını aştığında üç nokta da gösterildiği üç nokta desteği gibi işlevler içerir. Aşağıdaki örnek, ikinci ve üçüncü sözcüklere doğrusal bir gradyan dahil olmak üzere birkaç biçim uygulanmış olan metni gösterir.  
  
 ![FormattedText nesnesi kullanılarak görünen metin](./media/typography-in-wpf/text-formatted-linear-gradient.jpg) 
  
 Biçimlendirilen metni <xref:System.Windows.Media.Geometry> nesnelerine dönüştürebilirsiniz, böylece görsel açıdan ilgi çekici metin türlerini oluşturabilirsiniz. Örneğin, bir metin dizesinin ana hattını <xref:System.Windows.Media.Geometry> temel alan bir nesne oluşturabilirsiniz.  
  
 ![Doğrusal gradyan fırçası kullanan metin ana hattı](./media/typography-in-wpf/text-outline-linear-gradient.jpg)  
  
 Aşağıdaki örneklerde, dönüştürülmüş metnin vuruş, dolgusu ve vurgulanmasını değiştirerek ilginç görsel etkiler oluşturmanın birkaç yolu gösterilmektedir.  
  
 ![Fill ve Stroke için farklı renkler içeren metin](./media/typography-in-wpf/fill-stroke-text-effect.jpg)  
  
 ![Görüntüye resim fırçası uygulanmış metin](./media/typography-in-wpf/image-brush-application.jpg)
  
 ![Kontura ve vurgulamaya uygulanan resim fırçasının bulunduğu metin](./media/typography-in-wpf/image-brush-text-application.jpg)
  
 <xref:System.Windows.Media.FormattedText> Nesnesi hakkında daha fazla bilgi için bkz. [biçimli metin çizme](drawing-formatted-text.md).  
  
### <a name="advanced-text-formatting"></a>Gelişmiş Metin Biçimlendirme  
 Metin API 'lerinin en gelişmiş düzeyinde, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Media.TextFormatting.TextFormatter> nesne <xref:System.Windows.Media.TextFormatting> ve ad alanındaki diğer türler kullanılarak özel metin düzeni oluşturma olanağı sunar. <xref:System.Windows.Media.TextFormatting.TextFormatter> Ve ilişkili sınıflar, kendi karakter formatları, paragraf stilleri, satır sonu kuralları ve uluslararası metin için diğer düzen özellikleri tanımlarını destekleyen özel metin düzeni uygulamanıza olanak tanır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Metin düzeni desteğinin varsayılan uygulamasını geçersiz kılmak isteyebileceğiniz çok az durum vardır. Ancak, bir metin düzenlemesi denetimi veya uygulaması oluşturuyorsanız, varsayılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamadan farklı bir uygulama gerekebilir.  
  
 Geleneksel bir metin API 'sinin <xref:System.Windows.Media.TextFormatting.TextFormatter> aksine, bir dizi geri arama yöntemi aracılığıyla metin düzeni istemcisiyle etkileşime girer. İstemcinin bu yöntemleri <xref:System.Windows.Media.TextFormatting.TextSource> sınıfının bir uygulamasında sağlamasını gerektirir. Aşağıdaki diyagramda, istemci uygulaması ve <xref:System.Windows.Media.TextFormatting.TextFormatter>arasındaki metin düzeni etkileşimi gösterilmektedir.  
  
 ![Metin düzeni istemcisi ve TextFormatter diyagramı](./media/typography-in-wpf/text-layout-text-formatter-interaction.png)  
  
 Özel metin düzeni oluşturma hakkında daha fazla bilgi için bkz. [Gelişmiş metin biçimlendirme](advanced-text-formatting.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.FormattedText>
- <xref:System.Windows.Media.TextFormatting.TextFormatter>
- [ClearType Genel Bakışı](cleartype-overview.md)
- [OpenType Yazı Tipi Özellikleri](opentype-font-features.md)
- [Biçimlendirilmiş Metin Çizme](drawing-formatted-text.md)
- [Gelişmiş Metin Biçimlendirme](advanced-text-formatting.md)
- [Text](optimizing-performance-text.md)
- [Microsoft Tipografi](https://docs.microsoft.com/typography/)
