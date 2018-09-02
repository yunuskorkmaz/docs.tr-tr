---
title: Gelişmiş Metin Biçimlendirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- formatting [WPF]
- text [WPF]
- typography [WPF], text formatting
ms.assetid: f0a7986e-f5b2-485c-a27d-f8e922022212
ms.openlocfilehash: e8347f1a82c70f1ce8aa7cc05841bc869abbcc33
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43462512"
---
# <a name="advanced-text-formatting"></a>Gelişmiş Metin Biçimlendirme
Windows Presentation Foundation (WPF) sağlayan bir dizi güçlü [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] uygulamanızda metin dahil etmek için. Düzen ve [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], gibi <xref:System.Windows.Controls.TextBlock>, en yaygın sağlar ve genel metin sunu öğelerini kullanın. Çizim [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], gibi <xref:System.Windows.Media.GlyphRunDrawing> ve <xref:System.Windows.Media.FormattedText>, biçimlendirilmiş metin çizimlerini dahil etmek için bir yol sağlar. En gelişmiş düzeyde [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] bir Genişletilebilir metin biçimlendirme metin sunum, metin Depolama Yönetimi, çalıştırma metin biçimlendirme yönetim ve katıştırılmış nesne yönetimi gibi her yönüyle denetlemek için altyapı sağlar.  
  
 Bu konuda tanıtır [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] metin biçimlendirmesi. İstemci uygulamasını ve kullanımını üzerinde odaklanır [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] altyapısı biçimlendirme metin.  
  
> [!NOTE]
>  Bu belgedeki tüm kod örnekleri bulunabilir [Gelişmiş metin biçimlendirme örnek](https://go.microsoft.com/fwlink/?LinkID=159965).  
  

  
<a name="prereq"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konuda, daha yüksek düzeyiyle ilgili bilgi sahibi olduğunuz varsayılır [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] metin sunu için kullanılır. Çoğu kullanıcı senaryoları Gelişmiş metin biçimlendirme gerektirmez [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] bu konuda tartışılan. Giriş için farklı bir metin [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], bkz: [WPF'deki Belgeler](../../../../docs/framework/wpf/advanced/documents-in-wpf.md).  
  
<a name="section1"></a>   
## <a name="advanced-text-formatting"></a>Gelişmiş Metin Biçimlendirme  
 Metin düzenini ve [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] denetimlerini [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] biçimlendirilmiş metnin uygulamanızda kolayca dahil etmenize imkan tanır biçimlendirme özellikleri sağlar. Bu denetimler, özellikler, yazı tipi, boyutu ve rengi içeren metin sunumunu işlemek için bir dizi kullanıma sunar. Normal koşullar altında bu denetimleri, uygulamanızda metin sunu çoğunu başa çıkabilir. Ancak, bazı gelişmiş senaryoları denetim metin sunu yanı sıra, metin depolama gerektirir. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Bu amaçla altyapısı biçimlendirme genişletilebilir bir metin sağlar.  
  
 Gelişmiş metin biçimlendirme özellikleri bulunan [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] biçimlendirme altyapısı, bir metin depolama, metin çalıştırır ve biçimlendirme özellikleri bir metinden oluşur. Metin biçimlendirme altyapısı <xref:System.Windows.Media.TextFormatting.TextFormatter>, sunu için kullanılacak metin satırı oluşturur. Bu satır biçimlendirme işlemini başlatan ve metin Biçimlendiricinin çağırarak sağlanır <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A>. Metin biçimlendirici metin çalışıyor mağazanın çağırarak metin Mağazası'ndan alır <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> yöntemi. <xref:System.Windows.Media.TextFormatting.TextRun> Nesneleri ardından içinde oluşturulmuş <xref:System.Windows.Media.TextFormatting.TextLine> metin biçimlendirici tarafından nesneleri ve uygulamanıza inceleme veya görüntü için belirtilen.  
  
<a name="section2"></a>   
## <a name="using-the-text-formatter"></a>Metin biçimlendirici kullanılarak  
 <xref:System.Windows.Media.TextFormatting.TextFormatter> olan [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] metin biçimlendirme altyapısını ve biçimlendirme ve metin satırlarını yeni hizmetler sağlar. Metin biçimlendirici farklı metin karakter biçimlerini ve stilleri işleyebilir ve uluslararası metin düzeni için destek içerir.  
  
 Geleneksel bir metin aksine [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)], <xref:System.Windows.Media.TextFormatting.TextFormatter> metin düzeni istemcisi kümesi geri çağırma yöntemleri ile etkileşime geçer. Bu yöntemleri uygulaması sağlamak için istemcinin gerektirir <xref:System.Windows.Media.TextFormatting.TextSource> sınıfı. Aşağıdaki diyagram, istemci uygulama arasındaki metin düzeni etkileşimi gösterir ve <xref:System.Windows.Media.TextFormatting.TextFormatter>.  
  
 ![Metin düzeni istemcisi ve TextFormatter diyagramı](../../../../docs/framework/wpf/advanced/media/textformatter01.png "TextFormatter01")  
Uygulama TextFormatter arasındaki etkileşimi  
  
 Biçimlendirilmiş metin satırlarını metin Mağazası'ndan almak için kullanılan metin biçimlendirici uygulaması olduğu <xref:System.Windows.Media.TextFormatting.TextSource>. Bu ilk metin biçimlendirici örneğini kullanarak oluşturarak yapılır <xref:System.Windows.Media.TextFormatting.TextFormatter.Create%2A> yöntemi. Bu yöntem, metin biçimlendirici örneği oluşturur ve maksimum satır yüksekliğini ve genişliğini değerlerini ayarlar. Metin biçimlendirici örneği oluşturulduktan hemen sonra satır oluşturma işlemini çağırarak başlatıldığında <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A> yöntemi. <xref:System.Windows.Media.TextFormatting.TextFormatter> geri metin ve biçimlendirme metin sıralarında parametrelerini almak için metin kaynağına oluşturan bir satır çağırır.  
  
 Aşağıdaki örnekte, bir metin deposu biçimlendirme işlemi gösterilmektedir. <xref:System.Windows.Media.TextFormatting.TextFormatter> Metin satırlarını metin Mağazası'ndan almak ve sonra metin satırı halinde çizim biçimlendirmek için kullanılan nesne <xref:System.Windows.Media.DrawingContext>.  
  
 [!code-csharp[TextFormatterExample#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[TextFormatterExample#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/Window1.xaml.vb#100)]  
  
<a name="section3"></a>   
## <a name="implementing-the-client-text-store"></a>İstemci metin Store uygulama  
 Metin biçimlendirme motoru genişlettiğinizde, uygulamak ve metin deponun tüm yönlerini yönetmek için gereklidir. Bu basit bir görev değildir. İzleme özellikleri, paragraf özellikleri, katıştırılmış nesneleri ve diğer benzer içeriği çalıştırma metni için metin deposu sorumludur. Metin biçimlendirici ile tek tek de sağlar <xref:System.Windows.Media.TextFormatting.TextRun> oluşturmak için metin biçimlendirici kullanan nesneler <xref:System.Windows.Media.TextFormatting.TextLine> nesneleri.  
  
 Metin depolama sanallaştırma işlemek için metin deposu nesnesinden türetilmesi <xref:System.Windows.Media.TextFormatting.TextSource>. <xref:System.Windows.Media.TextFormatting.TextSource> metin biçimlendirici metin çalıştırmaları metin Mağazası'ndan almak için kullandığı yöntem tanımlar. <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> metin biçimlendirici tarafından metnini almak için kullanılan yöntem satırı biçimlendirmede kullanılan çalıştığı yerdir. Çağrı <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> metin biçimlendirici tarafından aşağıdaki koşullardan biri gerçekleşene kadar sürekli olarak gerçekleştirilir:  
  
-   A <xref:System.Windows.Media.TextFormatting.TextEndOfLine> veya bir alt döndürülür.  
  
-   Metin çalıştırmaları birikmiş genişliğini aşıyor veya metin Biçimlendiricinin için yapılan metin biçimlendirici oluşturmak için bir çağrı ya da belirtilen en fazla çizgi genişliği <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A> yöntemi.  
  
-   A [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] "CF", "LF" veya "CRLF" gibi yeni satır sırası döndürülür.  
  
<a name="section4"></a>   
## <a name="providing-text-runs"></a>Metin çalıştırmaları sağlama  
 Metin biçimlendirme işleminin çekirdeği metin biçimlendirici metin deposu arasındaki etkileşimi olur. Uygulamanıza <xref:System.Windows.Media.TextFormatting.TextSource> metin biçimlendirici ile sağlar <xref:System.Windows.Media.TextFormatting.TextRun> nesneleri ve özellikleri ile biçimlendirmek metin çalıştığı. Bu etkileşimi tarafından işlenen <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> metin biçimlendirici tarafından çağrılan yöntem.  
  
 Aşağıdaki tabloda önceden tanımlanmış bazıları gösterilmektedir <xref:System.Windows.Media.TextFormatting.TextRun> nesneleri.  
  
|TextRun türü|Kullanım|  
|------------------|-----------|  
|<xref:System.Windows.Media.TextFormatting.TextCharacters>|Özel metin karakterleri karakter gösterimi geri metin biçimlendirici için geçirmek için kullanılan çalıştırın.|  
|<xref:System.Windows.Media.TextFormatting.TextEmbeddedObject>|Özel metin hangi ölçme, içerik sağlamak, tıklama testi için kullanılan çalıştırın ve çizim gibi bir düğme veya görüntü metni içindeki bütün gerçekleştirilir.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfLine>|Özel metin bir satır sonu işaretlemek için kullanılan çalıştırın.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>|Özel metin paragrafı sonunu işaretlemek için kullanılan çalıştırın.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfSegment>|Çalıştırma özelleştirilmiş metin kapsam önceki tarafından etkilenen sonuna gibi bir segment sonu işaretlemek için kullanılan <xref:System.Windows.Media.TextFormatting.TextModifier> çalıştırın.|  
|<xref:System.Windows.Media.TextFormatting.TextHidden>|Özel metin gizli karakter aralığı işaretlemek için kullanılan çalıştırın.|  
|<xref:System.Windows.Media.TextFormatting.TextModifier>|Metin özelliklerini değiştirmek için kullanılan çalıştırma özelleştirilmiş metin kapsamında çalıştırır. Sonraki eşleşen kapsamını genişletir <xref:System.Windows.Media.TextFormatting.TextEndOfSegment> metin çalıştırın ya da sonraki <xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>.|  
  
 Önceden tanımlanmış tüm <xref:System.Windows.Media.TextFormatting.TextRun> nesneleri sınıflandırma. Bu, özel veri içeren metin biçimlendirici metinle çalışır sağlamak metin kaynak sağlar.  
  
 Aşağıdaki örnek, gösterir bir <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> yöntemi. Bu metin deposu döndürür <xref:System.Windows.Media.TextFormatting.TextRun> metin biçimlendirici işleme nesneleri.  
  
 [!code-csharp[TextFormatterExample#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/CustomTextSource.cs#101)]
 [!code-vb[TextFormatterExample#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/CustomTextSource.vb#101)]  
  
> [!NOTE]
>  Bu örnekte, aynı metin özellikleri tüm metnin metin deposu sağlar. Gelişmiş metin depoları uygulamak için kendi gerekir, farklı özelliklere sahip karakterlerin tek tek izin vermek için yönetim yayılır.  
  
<a name="section5"></a>   
## <a name="specifying-formatting-properties"></a>Biçimlendirme özellikleri belirtme  
 <xref:System.Windows.Media.TextFormatting.TextRun> metin mağaza tarafından sağlanan özellikleri kullanarak nesneleri biçimlendirilir. İki tür içinde bu özellikleri gelen <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> ve <xref:System.Windows.Media.TextFormatting.TextRunProperties>. <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> Paragraf kapsamlı özellikler gibi işleme <xref:System.Windows.TextAlignment> ve <xref:System.Windows.FlowDirection>. <xref:System.Windows.Media.TextFormatting.TextRunProperties> Her metin ön plan fırça gibi bir paragraf içinde çalıştırmak için farklı özellikleri <xref:System.Windows.Media.Typeface>ve yazı tipi boyutu. Özel Paragraf ve özel metin özelliği türler uygulamak için uygulamanızı öğesinden türetilen sınıflar oluşturma <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> ve <xref:System.Windows.Media.TextFormatting.TextRunProperties> sırasıyla.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WPF'de Tipografi](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)  
 [WPF'deki Belgeler](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)
