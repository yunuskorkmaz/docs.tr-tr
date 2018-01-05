---
title: "Gelişmiş Metin Biçimlendirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- formatting [WPF]
- text [WPF]
- typography [WPF], text formatting
ms.assetid: f0a7986e-f5b2-485c-a27d-f8e922022212
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9bb2664b267301fdf1e3a67e385595a5d28212bc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="advanced-text-formatting"></a>Gelişmiş Metin Biçimlendirme
[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] Sağlam bir dizi sağlar [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] uygulamanızda metin dahil etmek için. Düzen ve [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], gibi <xref:System.Windows.Controls.TextBlock>, en yaygın sağlamak ve genel öğeleri metin sunumu için kullanın. Çizim [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], gibi <xref:System.Windows.Media.GlyphRunDrawing> ve <xref:System.Windows.Media.FormattedText>, biçimlendirilmiş metin çizimlerini dahil etmek için bir yol sağlar. En gelişmiş düzeyde [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] genişletilebilir bir metin metin Depolama Yönetimi, çalıştırmak metin biçimlendirme yönetimi ve katıştırılmış nesne yönetimi gibi metin sunu her yönüyle denetlemek için altyapısı biçimlendirme sağlar.  
  
 Bu konuda tanıtılmaktadır [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] metni biçimlendirme. İstemci uygulaması ve kullanımını odaklanan [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] metin altyapısı biçimlendirme.  
  
> [!NOTE]
>  Bu belgedeki tüm kod örnekleri bulunabilir [Gelişmiş metin biçimlendirme örneği](http://go.microsoft.com/fwlink/?LinkID=159965).  
  

  
<a name="prereq"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konu, daha üst düzey ile bildiğinizi varsayar [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] metin sunumu için kullanılır. Çoğu kullanıcı senaryoları Gelişmiş metin biçimlendirmesini gerektirmez [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] bu konuda tartışılan. Giriş farklı bir metin için [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], bkz: [WPF belgelerde](../../../../docs/framework/wpf/advanced/documents-in-wpf.md).  
  
<a name="section1"></a>   
## <a name="advanced-text-formatting"></a>Gelişmiş Metin Biçimlendirme  
 Metin düzenini ve [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] denetimlerini [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] biçimlendirilmiş metin uygulamanıza kolayca dahil izin biçimlendirme özellikleri sağlar. Bu denetimler, yazı tipi, boyut ve renk içeren metin sunumu işlemek için bir dizi kullanıma sunar. Normal koşullar altında bu denetimler, uygulamanızda metin sunu çoğunluğu işleyebilir. Ancak, bazı gelişmiş senaryoları, metin sunu yanı sıra metin depolama denetimi gerektirir. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]Genişletilebilir bir metin altyapısı bu amaç için biçimlendirme sağlar.  
  
 Biçimlendirme özellikleri Gelişmiş metin bulunan [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] biçimlendirme altyapısı, bir metin deposu, metin çalıştırır ve biçimlendirme özelliklerini bir metinden oluşur. Metin altyapısı biçimlendirme <xref:System.Windows.Media.TextFormatting.TextFormatter>, sunu için kullanılacak metin satırı oluşturur. Bu satırı biçimlendirme işlemini başlatma ve metin Biçimlendiricinin çağırma elde <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A>. Metin biçimlendirici metin çalışıyor deponun çağrılarak metin deponuzdan alır <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> yöntemi. <xref:System.Windows.Media.TextFormatting.TextRun> Nesneleri sonra içine biçimlendirilmiş <xref:System.Windows.Media.TextFormatting.TextLine> nesneleri metin biçimlendirici tarafından ve uygulamanıza denetleme veya görüntü için belirtilen.  
  
<a name="section2"></a>   
## <a name="using-the-text-formatter"></a>Metin biçimlendirici kullanılarak  
 <xref:System.Windows.Media.TextFormatting.TextFormatter>olan [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] metin biçimlendirmesini altyapısı ve biçimlendirme ve metin satırlara ayırma için hizmetler sağlar. Metin biçimlendirici farklı metin karakter biçimlerini ve stilleri işleyebilir ve uluslararası metin düzenini destekler.  
  
 Geleneksel bir metni farklı [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)], <xref:System.Windows.Media.TextFormatting.TextFormatter> kümesi geri arama yöntemleri ile metin düzeni istemcisi ile etkileşim kurar. Bu yöntemler bir uygulanmasını sağlamak için istemcinin gerektirir <xref:System.Windows.Media.TextFormatting.TextSource> sınıfı. Aşağıdaki diyagram, istemci uygulaması arasında metin düzeni etkileşim gösterir ve <xref:System.Windows.Media.TextFormatting.TextFormatter>.  
  
 ![Metin düzeni istemcisi ve TextFormatter diyagramı](../../../../docs/framework/wpf/advanced/media/textformatter01.png "TextFormatter01")  
Uygulama ve TextFormatter arasındaki etkileşimi  
  
 Metin biçimlendirici biçimlendirilmiş metin satırlarını metin Mağazası'ndan almak için kullanılan uygulaması olduğu <xref:System.Windows.Media.TextFormatting.TextSource>. Bu ilk metin biçimlendiricisi örneği kullanarak oluşturarak yapılır <xref:System.Windows.Media.TextFormatting.TextFormatter.Create%2A> yöntemi. Bu yöntem, metin biçimlendiricisi örneği oluşturur ve en fazla satır yüksekliğini ve genişliğini değerlerini ayarlar. Metin biçimlendiricisi örneği oluşturulduktan hemen sonra satır oluşturma işlemi çağrılarak başlatılır <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A> yöntemi. <xref:System.Windows.Media.TextFormatting.TextFormatter>geri metin ve biçimlendirme parametreleri metin çalışmaları için almak için metin kaynağı için bir satır oluşturan çağırır.  
  
 Aşağıdaki örnekte, bir metin deposu biçimlendirme işlemi gösterilir. <xref:System.Windows.Media.TextFormatting.TextFormatter> Nesne metin Mağazası'ndan metin satırlarını almak ve çizim içine metin satırı biçimlendirmek için kullanılan <xref:System.Windows.Media.DrawingContext>.  
  
 [!code-csharp[TextFormatterExample#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[TextFormatterExample#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/Window1.xaml.vb#100)]  
  
<a name="section3"></a>   
## <a name="implementing-the-client-text-store"></a>İstemci metin deposu uygulama  
 Metni Biçimlendirme altyapısı genişlettiğinizde, uygulamak ve metin deposu tüm yönlerini yönetmek için gereklidir. Bu karmaşık bir görev değildir. Metin özellikleri, paragraf özellikleri, katıştırılmış nesneler ve benzer diğer içeriği çalıştıran izlemek için metin deposu sorumludur. Ayrıca kişiyle metin biçimlendirici sağlar <xref:System.Windows.Media.TextFormatting.TextRun> oluşturmak için metin biçimlendirici kullanan nesneleri <xref:System.Windows.Media.TextFormatting.TextLine> nesneleri.  
  
 Metin deposu sanallaştırma işlemek için metin deposu öğesinden türetilmelidir <xref:System.Windows.Media.TextFormatting.TextSource>. <xref:System.Windows.Media.TextFormatting.TextSource>metin biçimlendirici metin çalışıyor metin Mağazası'ndan almak için kullandığı yöntemi tanımlar. <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A>metin biçimlendirici tarafından metni almak için kullanılan yöntem satır biçimlendirmede kullanılan çalıştığı yerdir. Çağrı <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> aşağıdaki koşullardan biri gerçekleşene kadar metin biçimlendirici tarafından art arda yapılan:  
  
-   A <xref:System.Windows.Media.TextFormatting.TextEndOfLine> veya bir alt kümesi döndürdü.  
  
-   Metin biçimlendirici oluşturmak ya da bir arama veya metin Biçimlendiricinin çağrısı belirtilen maksimum çizgi genişliği metin çalışıyor birikmiş genişliğini aşıyor <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A> yöntemi.  
  
-   A [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] "CF", "LF" veya "CRLF" gibi yeni satır sırası döndürülür.  
  
<a name="section4"></a>   
## <a name="providing-text-runs"></a>Metin çalışıyor sağlama  
 Metni biçimlendirme işlemini çekirdek metin biçimlendirici ve metin deposu arasındaki etkileşimi ' dir. Uygulamanıza <xref:System.Windows.Media.TextFormatting.TextSource> ile metin biçimlendirici sağlar <xref:System.Windows.Media.TextFormatting.TextRun> nesneleri ve özellikleri ile biçimlendirmek metin çalıştığı. Bu etkileşimi tarafından işlenen <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> metin biçimlendirici tarafından çağrılan yöntemi.  
  
 Aşağıdaki tabloda bazı önceden tanımlanmış gösterilmektedir <xref:System.Windows.Media.TextFormatting.TextRun> nesneleri.  
  
|TextRun türü|Kullanım|  
|------------------|-----------|  
|<xref:System.Windows.Media.TextFormatting.TextCharacters>|Özel metin gösterimi karakter karakterlerin geri metin biçimlendirici geçirmek için kullanılan çalıştırın.|  
|<xref:System.Windows.Media.TextFormatting.TextEmbeddedObject>|Özel metin hangi ölçme içinde içerik sağlamak için isabet testi kullanılan çalıştırın ve çizim bütün bir düğme veya metin içinde görüntü gibi yapılır.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfLine>|Özel metin bir satır sonu işaretlemek için kullanılan çalıştırın.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>|Özel metin paragraf sonu işaretlemek için kullanılan çalıştırın.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfSegment>|Çalıştırma özelleştirilmiş metin kapsam önceki tarafından etkilenen sonuna gibi bir segmentinin sonunu işaretlemek için kullanılan <xref:System.Windows.Media.TextFormatting.TextModifier> çalıştırın.|  
|<xref:System.Windows.Media.TextFormatting.TextHidden>|Özel metin çalıştırın gizli karakter aralığı işaretlemek için kullanılan.|  
|<xref:System.Windows.Media.TextFormatting.TextModifier>|Metin özelliklerini değiştirmek için kullanılan çalıştırmak özelleştirilmiş metin, kapsamında çalışır. Sonraki eşleşen kapsamını genişletir <xref:System.Windows.Media.TextFormatting.TextEndOfSegment> metin çalıştırın ya da sonraki <xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>.|  
  
 Önceden tanımlanmış hiçbirini <xref:System.Windows.Media.TextFormatting.TextRun> nesneleri sınıflandırma. Bu özel verileri içeren metin içeren metin biçimlendirici çalıştıran sağlamak için metin kaynak sağlar.  
  
 Aşağıdaki örnekte gösterilmiştir bir <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> yöntemi. Bu metin deposu döndürür <xref:System.Windows.Media.TextFormatting.TextRun> işleme için metin biçimlendirici nesnelere.  
  
 [!code-csharp[TextFormatterExample#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/CustomTextSource.cs#101)]
 [!code-vb[TextFormatterExample#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/CustomTextSource.vb#101)]  
  
> [!NOTE]
>  Bu örnekte, aynı metin özellikleri tüm metnin metin deposu sağlar. Span farklı özelliklere sahip tek tek karakterlerine izin vermek için yönetim Gelişmiş metin depoları uygulamak için kendi gerekir.  
  
<a name="section5"></a>   
## <a name="specifying-formatting-properties"></a>Biçimlendirme özelliklerini belirtme  
 <xref:System.Windows.Media.TextFormatting.TextRun>nesneleri metin deposu tarafından sağlanan özellikleri kullanılarak biçimlendirilir. Bu özellikler iki türlerinde gelen <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> ve <xref:System.Windows.Media.TextFormatting.TextRunProperties>. <xref:System.Windows.Media.TextFormatting.TextParagraphProperties>Paragraf dahil özellikler gibi ele <xref:System.Windows.TextAlignment> ve <xref:System.Windows.FlowDirection>. <xref:System.Windows.Media.TextFormatting.TextRunProperties>Her metin ön plan Fırçası gibi bir paragraf içinde çalıştırmak için farklı özellikleri <xref:System.Windows.Media.Typeface>ve yazı tipi boyutu. Özel Paragraf ve özellik türleri çalıştırmak özel metin uygulamak için uygulamanızın öğesinden türetilen sınıflar oluşturmalısınız <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> ve <xref:System.Windows.Media.TextFormatting.TextRunProperties> sırasıyla.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WPF'de Tipografi](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)  
 [WPF'deki Belgeler](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)
