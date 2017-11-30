---
title: WPF'de Tipografi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: typography [WPF], about typography
ms.assetid: 06cbf17b-6eff-4fe5-949d-2dd533e4e1f4
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 28c51c6208bfdfe068b9fb3ed2cdc58dd0350fdb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="typography-in-wpf"></a>WPF'de Tipografi
Bu konu ana tipografik özelliklerini tanıtır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Geliştirilmiş kalitesini ve metin işleme performansını bu özellikleri [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] Gelişmiş tipografi destek, Gelişmiş uluslararası metin yazı tipi desteği ve yeni metin uygulama programlama arabirimleri (API).  
  

  
<a name="Improved_Quality_and_Performance_of_Text"></a>   
## <a name="improved-quality-and-performance-of-text"></a>Kalitesinin, metin performansı  
 Metin [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kullanılarak oluşturulması [!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)], metnin okunabilirliğini ve netlik geliştirir. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]bir yazılım teknoloji tarafından geliştirilen [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] dizüstü ekranları, Pocket PC ekranları ve düz panel monitörler gibi varolan LCDler (Sıvı Crystal görüntüler) üzerinde metnin okunabilirliğini artırır. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]büyük bir doğruluk, doğru şekilde ile bir piksel kesirli kısmını hizalama karakterleri tarafından görüntülenecek metni veren alt piksel işleme kullanır. Ek çözümleme uzun süreler çok okunmasını kolaylaştırmak metin görüntüsündeki küçük ayrıntıların netlik artırır. Başka bir geliştirilmesini [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] içinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] y yönünde düzgünleştirme, hangi düzgünleştirir dows masaüstleri ve alta metin karakterlerinin yüzeysel eğrilerinin değil. Daha fazla ayrıntı için [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] özellikleri, bkz. [ClearType genel bakış](../../../../docs/framework/wpf/advanced/cleartype-overview.md).  
  
 ![ClearType y &#45; anti yön &#45;metinle; yumuşatma](../../../../docs/framework/wpf/advanced/media/typographyinwpf02.gif "TypographyInWPF02")  
ClearType y yönünde düzgünleştirme metinle  
  
 Tüm metin işleme ardışık olarak donanım hızlandırılmış [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] gerekli donanım en düşük düzeyde makinenizi karşılaması koşuluyla. İşleme, yazılım işleme geri donanım döner kullanarak gerçekleştirilemiyor. Donanım hızlandırma etkiler tüm metin işleme ardışık düzen aşamaları — tek tek karakter, karakter çalıştığında, içine birleştirme karakterlerin depolamasını efektleri, uygulama için uygulama [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] son görüntülenen çıktının algoritmasına karıştırma. Donanım hızlandırma hakkında daha fazla bilgi için bkz: [grafik işleme katmanları](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md).  
  
 ![Metin işleme ardışık düzeni diyagramı](../../../../docs/framework/wpf/advanced/media/typographyinwpf01.png "TypographyInWPF01")  
Metin işleme ardışık düzeni diyagramı  
  
 Buna ek olarak, animasyon metni karakterin veya karakter, grafik donanım özelliğin yararlanır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Bu düz metin animasyonda sonuçlanır.  
  
<a name="Rich_Typography"></a>   
## <a name="rich-typography"></a>Zengin tipografi  
 [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] Yazı tipi biçimi uzantısıdır [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)] yazı tipi biçimi. [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] Yazı tipi biçimi ortaklaşa tarafından geliştirilen [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] ve Adobe ve Gelişmiş tipografik özellikleri zengin bir listesini sağlar. <xref:System.Windows.Documents.Typography> Nesneyi birçok gelişmiş özellikleri kullanıma sunan [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] stil seçeneklerini ve dalgalı karakterler gibi yazı tipi. [!INCLUDE[TLA2#tla_lhsdk](../../../../includes/tla2sharptla-lhsdk-md.md)] Örnek kümesi sağlar [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] Pericles ve Pescadero yazı tipleri gibi zengin özelliklere sahip tasarlanmış yazı tipi. Daha fazla bilgi için bkz: [örnek OpenType yazıtipi paketi](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md).  
  
 Pericles [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] yazı tipi standart kümesine stil seçeneklerini sağlayan ek karakterleri içerir. Aşağıdaki metin diğer biçimsel görüntüler.  
  
 ![OpenType diğer biçimsel kullanarak metin](../../../../docs/framework/wpf/advanced/media/opentypefont02.gif "opentypefont02")  
OpenType diğer biçimsel kullanarak metin  
  
 Dalgalı karakterler genellikle calligraphy ile ilişkili ayrıntılı süsleme kullanan dekoratif karakterlerdir. Aşağıdaki metin Pescadero yazı tipi için standart ve süslü karakterleri görüntüler.  
  
 ![OpenType standart ve süslü karakterleri kullanarak metin](../../../../docs/framework/wpf/advanced/media/opentypefont08.gif "opentypefont08")  
OpenType standart ve süslü karakterleri kullanarak metin  
  
 Daha fazla ayrıntı için [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] özellikleri, bkz. [OpenType yazıtipi özellikleri](../../../../docs/framework/wpf/advanced/opentype-font-features.md).  
  
<a name="Enhanced_International_Text_Support"></a>   
## <a name="enhanced-international-text-support"></a>Gelişmiş uluslararası metin desteği  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Aşağıdaki özellikleri sağlayarak Gelişmiş uluslararası metin desteği sağlar:  
  
-   Otomatik satır aralığını Uyarlamalı ölçüm kullanarak tüm yazı sistemlerinde.  
  
-   Uluslararası metin geniş desteği. Daha fazla bilgi için bkz: [WPF için genelleştirme](../../../../docs/framework/wpf/advanced/globalization-for-wpf.md).  
  
-   Dil destekli satır kesme, heceleme ve düzeltme.  
  
<a name="Enhanced_Font_Support"></a>   
## <a name="enhanced-font-support"></a>Gelişmiş yazı tipi desteği  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Aşağıdaki özellikleri sağlayarak gelişmiş yazı tipi desteği sağlar:  
  
-   Unicode tüm metnin. Yazı tipi davranışı ve artık seçimi charset veya codepage gerektirir.  
  
-   Yazı tipi davranışı sistem yerel ayarı gibi genel ayarları bağımsızdır.  
  
-   Ayrı <xref:System.Windows.FontWeight>, <xref:System.Windows.FontStretch>, ve <xref:System.Windows.FontStyle> türlerini tanımlamak için bir <xref:System.Windows.Media.FontFamily>. Bu daha da büyük esneklik sağlar [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] programlama, hangi Boolean birleşimlerini italik ve kalın yazı tipi ailesi tanımlamak için kullanılır.  
  
-   Yazma yönünü (dikey ve yatay) bağımsız yazı tipi adı olarak işlenir.  
  
-   Bağlama de yazı tipi bir taşınabilir geri dönüş [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] bileşik font teknolojisini kullanarak, dosya. Bileşik yazı tipleri tam kapsamlı bir dilde yazı tipleri yapımı için izin verir. Bileşik yazı tipleri de eksik karakterlerin görüntüleme engelleyen bir mekanizma sağlar. Açıklamalar daha fazla bilgi için bkz: <xref:System.Windows.Media.FontFamily> sınıfı.  
  
-   Bir grup tek dili yazı tipi kullanarak bileşik yazı yerleşik uluslararası yazı tipi. Bu birden çok dil için yazı tipi geliştirirken kaynak giderlerinden tasarruf eder.  
  
-   Bileşik yazı tiplerini, böylece belge taşınabilirliği sağlayan bir belge içine katıştırılmış. Açıklamalar daha fazla bilgi için bkz: <xref:System.Windows.Media.FontFamily> sınıfı.  
  
<a name="New_Text_APIs"></a>   
## <a name="new-text-application-programming-interfaces-apis"></a>Yeni metin uygulama programlama arabirimleri (API)  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]birkaç metin sağlar [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] geliştiricilerin uygulamalarında metin dahil olmak üzere kullanın. Bunlar [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] üç kategoriye ayrılır:  
  
-   **Düzen ve kullanıcı arabirimini**. Genel metin denetimleri için [!INCLUDE[TLA#tla_gui](../../../../includes/tlasharptla-gui-md.md)].  
  
-   **Çizim basit metin**. Doğrudan nesnelere metin Çiz olanak tanır.  
  
-   **Metni Biçimlendirme Gelişmiş**. Özel metin altyapısı uygulama olanak tanır.  
  
### <a name="layout-and-user-interface"></a>Düzen ve kullanıcı arabirimi  
 En üst düzeyde işlevselliği, metin [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] ortak sağlamak [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] gibi denetimler <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.TextBlock>, ve <xref:System.Windows.Controls.TextBox>. Bu denetimler temel sağlamak [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] bir uygulama ve teklif sunmak ve metin ile etkileşim kurmak için kolay bir yol içinde öğelerin. Gibi denetimler <xref:System.Windows.Controls.RichTextBox> ve <xref:System.Windows.Controls.PasswordBox> etkinleştir daha gelişmiş veya metin işleme özelleştirilmiş. Gibi sınıfları <xref:System.Windows.Documents.TextRange>, <xref:System.Windows.Documents.TextSelection>, ve <xref:System.Windows.Documents.TextPointer> yararlı metin düzenleme etkinleştirin. Bunlar [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] denetimleri sağlayan özellikler gibi <xref:System.Windows.Controls.Control.FontFamily%2A>, <xref:System.Windows.Controls.Control.FontSize%2A>, ve <xref:System.Windows.Controls.Control.FontStyle%2A>, metin işlemek için kullanılan yazı tipi kontrol etkinleştirin.  
  
#### <a name="using-bitmap-effects-transforms-and-text-effects"></a>Bit eşlem efektleri, dönüşümler ve metin efektleri kullanma  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]bit eşlem efektleri, dönüşümler ve metin efektleri gibi özellikleri kullanıyor tarafından metnin görsel olarak ilginç kullanımlarını oluşturmanıza olanak sağlar. Aşağıdaki örnek, tipik bir metne uygulanan bir gölge efekti türünü gösterir.  
  
 ![Metin gölgesinin Yumuşaklık &#61; 0,25](../../../../docs/framework/wpf/advanced/media/shadowtext01.jpg "ShadowText01")  
Gölge metinle  
  
 Aşağıdaki örnek, bir gölge efekti ve metne uygulanan gürültü gösterir.  
  
 ![Metin gölgesinin gürültü ile](../../../../docs/framework/wpf/advanced/media/shadowtext04.jpg "ShadowText04")  
Gölge ve gürültü içeren metin  
  
 Aşağıdaki örnek metne uygulanan dış parlama efekti gösterir.  
  
 ![Metin gölgesinin OuterGlowBitmapEffect kullanan](../../../../docs/framework/wpf/advanced/media/shadowtext05.jpg "ShadowText05")  
Dış parlama efekti metinle  
  
 Aşağıdaki örnek metne uygulanan bir bulanıklaştırma efekti gösterir.  
  
 ![Metin gölgesinin BlurBitmapEffect kullanan](../../../../docs/framework/wpf/advanced/media/shadowtext06.jpg "ShadowText06")  
Metin Bulanıklaştırma efekti  
  
 Aşağıdaki örnek, x ekseni boyunca % 150 ölçeklendirilmiş metin satırının ikinci ve üçüncü y ekseni boyunca % 150 ölçeklendirilmiş metin satırının gösterir.  
  
 ![ScaleTransform kullanılarak ölçeklendirilen metin](../../../../docs/framework/wpf/advanced/media/transformedtext02.jpg "TransformedText02")  
ScaleTransform kullanarak metin  
  
 Aşağıdaki örnek eksenindeki eğri metni gösterir.  
  
 ![SkewTransform kullanılarak eğri metin](../../../../docs/framework/wpf/advanced/media/transformedtext03.jpg "TransformedText03")  
SkewTransform kullanarak metin  
  
 A <xref:System.Windows.Media.TextEffect> nesnesidir metin bir veya daha fazla grup, bir metin dizesindeki karakterlerin olarak işlemek izin veren bir yardımcı nesnesi. Aşağıdaki örnek döndürülmüş tek bir karakteri gösterir. Her karakteri 1 saniyelik aralıklarla bağımsız olarak döndürülür.  
  
 ![Metin döndürme metin efektinin ekran](../../../../docs/framework/wpf/advanced/media/texteffect01.jpg "TextEffect01")  
Bir döndürme metin efekti animasyonu örneği  
  
#### <a name="using-flow-documents"></a>Akış belgeleri kullanma  
 Ortak yanı sıra [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] denetimleri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] metin sunu için düzen denetimi sunar — <xref:System.Windows.Documents.FlowDocument> öğesi. <xref:System.Windows.Documents.FlowDocument> Birlikte öğesi <xref:System.Windows.Controls.DocumentViewer> öğesi, büyük miktarlarda düzen gereksinimlerini değişen metni için bir denetim sağlar. Düzen denetimleri Gelişmiş tipografi erişilmesini sağlar <xref:System.Windows.Documents.Typography> nesne ve yazı tipi ile ilgili özellikler, diğer [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] kontrol eder.  
  
 Metin içeriğinin barındırılan aşağıdaki örnekte bir <xref:System.Windows.Controls.FlowDocumentReader>, arama, gezinti, sayfalandırma ve Destek ölçeklendirme içeriği sağlar.  
  
 ![OpenType kullanarak yazı tipleri örnek ekran görüntüsü](../../../../docs/framework/wpf/advanced/media/typographyinwpf-03.png "TypographyInWPF_03")  
Bir FlowDocumentReader barındırılan metin  
  
 Daha fazla bilgi için bkz: [WPF belgelerde](../../../../docs/framework/wpf/advanced/documents-in-wpf.md).  
  
### <a name="lightweight-text-drawing"></a>Basit metin çizme  
 Metin doğrudan çizebilirsiniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kullanarak nesneleri <xref:System.Windows.Media.DrawingContext.DrawText%2A> yöntemi <xref:System.Windows.Media.DrawingContext> nesnesi. Bu yöntemi kullanmak için oluşturduğunuz bir <xref:System.Windows.Media.FormattedText> nesnesi. Bu nesne, tek tek her karakter metindeki biçimlendirilebilir çok satırlı metin Çiz olanak sağlar. İşlevselliğini <xref:System.Windows.Media.FormattedText> nesne Win32 API DrawText bayrakları işlevlerinin çoğunu içerir. Ayrıca, <xref:System.Windows.Media.FormattedText> nesnesi üç nokta görüntülendiği metin sınırlarının aştığında üç nokta destek gibi işlevsellikler içerir. Aşağıdaki örnek, ikinci ve üçüncü sözcükleri doğrusal gradyan dahil olmak üzere uygulanan çeşitli biçimlerde olan metin gösterir.  
  
 ![FormattedText nesnesi kullanılarak görüntülenen metin](../../../../docs/framework/wpf/advanced/media/formattedtext01.jpg "FormattedText01")  
FormattedText nesnesi kullanılarak görüntülenen metin  
  
 Biçimlendirilmiş metin dönüştürebilirsiniz <xref:System.Windows.Media.Geometry> görsel metin ilginç diğer türleri oluşturmanızı sağlayan nesneleri. Örneğin, oluşturabilirsiniz bir <xref:System.Windows.Media.Geometry> nesne tabanlı bir metin dizesinin anahattına.  
  
 ![Doğrusal gradyan fırçası kullanarak metin anahattı](../../../../docs/framework/wpf/advanced/media/outlinedtext02.jpg "OutlinedText02")  
Metin anahattı doğrusal gradyan fırçası kullanma  
  
 Aşağıdaki örneklerde vuruş, dolgu ve dönüştürülen metin Vurgusu değiştirerek ilginç görsel efektler oluşturmanın birkaç yolu gösterilmektedir.  
  
 ![Doldurma ve vuruş yapmak için farklı renkler metinle](../../../../docs/framework/wpf/advanced/media/outlinedtext03.jpg "OutlinedText03")  
Farklı renk vuruş ve dolgu ayarlama örneği  
  
 ![Görüntü fırça uygulandığı metinle](../../../../docs/framework/wpf/advanced/media/outlinedtext04.jpg "OutlinedText04")  
Uygulandığı bir resim fırçası örneği  
  
 ![Görüntü fırça uygulandığı metinle](../../../../docs/framework/wpf/advanced/media/outlinedtext05.jpg "OutlinedText05")  
Vuruş ve vurgulamaya uygulanan resim fırçası örneği  
  
 Daha fazla bilgi için <xref:System.Windows.Media.FormattedText> nesne için bkz: [çizim biçimlendirilmiş metin](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md).  
  
### <a name="advanced-text-formatting"></a>Gelişmiş Metin Biçimlendirme  
 En gelişmiş düzeyde metnin [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kullanarak özel metin düzenini oluşturma olanağı sunan <xref:System.Windows.Media.TextFormatting.TextFormatter> nesne ve diğer türleri <xref:System.Windows.Media.TextFormatting> ad alanı. <xref:System.Windows.Media.TextFormatting.TextFormatter> Ve ilişkili sınıflar, kendi karakter biçimleri, paragraf stil tanımını destekleyen özel metin düzenini uygulamak için satır sonu kuralları ve diğer yerleşim özellikleri için Uluslararası metin izin verir. İstediğiniz varsayılan uygulamasını geçersiz kılmak çok az durumlar vardır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] metin düzeni desteği. Ancak, bir metin denetim ya da uygulama düzenleme oluşturuyorsanız, varsayılandan farklı bir uygulama gerektirebilir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulaması.  
  
 Geleneksel bir metni farklı [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)], <xref:System.Windows.Media.TextFormatting.TextFormatter> kümesi geri arama yöntemleri ile metin düzeni istemcisi ile etkileşim kurar. Bu yöntemler bir uygulanmasını sağlamak için istemcinin gerektirir <xref:System.Windows.Media.TextFormatting.TextSource> sınıfı. Aşağıdaki diyagram, istemci uygulaması arasında metin düzeni etkileşim gösterir ve <xref:System.Windows.Media.TextFormatting.TextFormatter>.  
  
 ![Metin düzeni istemcisi ve TextFormatter diyagramı](../../../../docs/framework/wpf/advanced/media/textformatter01.png "TextFormatter01")  
Uygulama ve TextFormatter arasındaki etkileşimi  
  
 Özel metin düzenini oluşturma hakkında daha fazla ayrıntı için bkz: [Gelişmiş metin biçimlendirme](../../../../docs/framework/wpf/advanced/advanced-text-formatting.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.FormattedText>  
 <xref:System.Windows.Media.TextFormatting.TextFormatter>  
 [ClearType genel bakış](../../../../docs/framework/wpf/advanced/cleartype-overview.md)  
 [OpenType yazıtipi özellikleri](../../../../docs/framework/wpf/advanced/opentype-font-features.md)  
 [Biçimli metin çizme](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)  
 [Gelişmiş metin biçimlendirme](../../../../docs/framework/wpf/advanced/advanced-text-formatting.md)  
 [Metin](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [Microsoft tipografi](http://www.microsoft.com/typography/default.mspx)
