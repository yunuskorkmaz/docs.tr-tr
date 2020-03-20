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
ms.openlocfilehash: 745d20e0bd4f877f9d4559f9fc7829b56689d35c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185937"
---
# <a name="advanced-text-formatting"></a>Gelişmiş Metin Biçimlendirme
Windows Sunu Temeli (WPF), uygulamanıza metin dahil etmek için sağlam bir API kümesi sağlar. Düzen [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] ve API'ler, örneğin, <xref:System.Windows.Controls.TextBlock>metin sunusu için en yaygın ve genel kullanım öğelerini sağlar. Çizim API'leri, <xref:System.Windows.Media.FormattedText>örneğin, <xref:System.Windows.Media.GlyphRunDrawing> çizimlere biçimlendirilmiş metin dahil etmek için bir araç sağlar. En gelişmiş düzeyde, WPF metin deposu yönetimi, metin çalıştırma biçimlendirme yönetimi ve katıştırılmış nesne yönetimi gibi metin sunumunun her yönünü denetlemek için genişletilebilir bir metin biçimlendirme altyapısı sağlar.  
  
 Bu konu WPF metin biçimlendirmesine giriş sağlar. Bu istemci uygulama ve WPF metin biçimlendirme motorunun kullanımı üzerinde duruluyor.  
  
> [!NOTE]
> Bu belgedeki tüm kod örnekleri [Gelişmiş Metin Biçimlendirme Örneği'nde](https://github.com/Microsoft/WPF-Samples/tree/master/PerMonitorDPI/TextFormatting)bulunabilir.  

<a name="prereq"></a>
## <a name="prerequisites"></a>Önkoşullar  
 Bu konu, metin sunusu için kullanılan daha yüksek düzey API'leri bildiğinizi varsayar. Çoğu kullanıcı senaryosu, bu konuda tartışılan gelişmiş metin biçimlendirme API'lerini gerektirmez. Farklı metin API'lerine giriş yapmak için [WPF'deki Belgeler'e](documents-in-wpf.md)bakın.  
  
<a name="section1"></a>
## <a name="advanced-text-formatting"></a>Gelişmiş Metin Biçimlendirme  
 WPF'deki [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] metin düzeni ve denetimleri, uygulamanıza biçimlendirilmiş metni kolayca eklemenize olanak tanıyan biçimlendirme özellikleri sağlar. Bu denetimler, yazı tipini, boyutunu ve rengini içeren metnin sunusunu işlemek için bir dizi özellik ortaya çıkarır. Normal koşullar altında, bu denetimler uygulamanızdaki metin sunumunun çoğunu işleyebilir. Ancak, bazı gelişmiş senaryolar metin depolamanın yanı sıra metin sunusunun denetimini de gerektirir. WPF bu amaç için genişletilebilir bir metin biçimlendirme altyapısı sağlar.  
  
 WPF'de bulunan gelişmiş metin biçimlendirme özellikleri bir metin biçimlendirme altyapısı, metin deposu, metin çalışır ve biçimlendirme özelliklerinden oluşur. Metin biçimlendirme altyapısı, <xref:System.Windows.Media.TextFormatting.TextFormatter>sunu için kullanılacak metin satırları oluşturur. Bu, satır biçimlendirme işlemini başlatarak ve metnin <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A>formatter'ın kini çağırarak elde edilir. Metin formatter, mağazanın <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> yöntemini arayarak metin deponuzdan metin çalışır alır. Nesneler <xref:System.Windows.Media.TextFormatting.TextRun> daha sonra madde <xref:System.Windows.Media.TextFormatting.TextLine> metni tarafından nesneler halinde oluşturulur ve inceleme veya görüntüleme için uygulamanıza verilir.  
  
<a name="section2"></a>
## <a name="using-the-text-formatter"></a>Formatter Metnini Kullanma  
 <xref:System.Windows.Media.TextFormatting.TextFormatter>WPF metin biçimlendirme motorudur ve metin satırlarını biçimlendirme ve kesme hizmetleri sağlar. Madde metni farklı metin karakter biçimlerini ve paragraf stillerini işleyebilir ve uluslararası metin düzeni için destek içerir.  
  
 Geleneksel metin API'sinin <xref:System.Windows.Media.TextFormatting.TextFormatter> aksine, bir dizi geri arama yöntemi yle metin düzeni istemcisi ile etkileşim kurar. Bu <xref:System.Windows.Media.TextFormatting.TextSource> sınıfın bir uygulamada bu yöntemleri sağlamak için istemci gerektirir. Aşağıdaki diyagram, istemci uygulaması ve <xref:System.Windows.Media.TextFormatting.TextFormatter>.  
  
 ![Metin düzeni istemcisi ve TextFormatter diyagramı](./media/advanced-text-formatting/text-layout-textformatter-interaction.png)  
  
 Madde metni, metin deposundan biçimlendirilmiş metin satırlarını almak için <xref:System.Windows.Media.TextFormatting.TextSource>kullanılır. Bu, önce <xref:System.Windows.Media.TextFormatting.TextFormatter.Create%2A> metnin bir örneğini yöntem kullanılarak oluşturularak yapılır. Bu yöntem, metnin bir örneğini oluşturur ve en büyük çizgi yüksekliği ve genişlik değerlerini ayarlar. Metin için bir örnek oluşturulur oluşturulmaz, satır oluşturma işlemi <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A> yöntemi çağırarak başlatılır. <xref:System.Windows.Media.TextFormatting.TextFormatter>bir satır oluşturan metnin çalıştırmaları için metin ve biçimlendirme parametrelerini almak için metin kaynağına geri çağırır.  
  
 Aşağıdaki örnekte, bir metin deposu biçimlendirme işlemi gösterilir. Nesne <xref:System.Windows.Media.TextFormatting.TextFormatter> metin deposundan metin satırları almak ve sonra ' içine çizim <xref:System.Windows.Media.DrawingContext>için metin satırı biçimlendirmek için kullanılır.  
  
 [!code-csharp[TextFormatterExample#100](~/samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[TextFormatterExample#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/Window1.xaml.vb#100)]  
  
<a name="section3"></a>
## <a name="implementing-the-client-text-store"></a>İstemci Metin Mağazası'nın Uygulanması  
 Metin biçimlendirme altyapısını uzattığınızda, metin deposunun tüm yönlerini uygulamanız ve yönetmeniz gerekir. Bu önemsiz bir görev değil. Metin deposu metin çalıştırma özelliklerini, paragraf özelliklerini, katıştırılmış nesneleri ve diğer benzer içeriği izlemekten sorumludur. Ayrıca, madde için metnin <xref:System.Windows.Media.TextFormatting.TextRun> nesneleri oluşturmak <xref:System.Windows.Media.TextFormatting.TextLine> için kullandığı tek tek nesnelerle metin sağlar.  
  
 Metin deposunun sanallaştırmasını işlemek için metin deposundan <xref:System.Windows.Media.TextFormatting.TextSource>türetilmiş olması gerekir. <xref:System.Windows.Media.TextFormatting.TextSource>metin deposundan metin almak için metin için kullandığı yöntemi tanımlar. <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A>satır biçimlendirmede kullanılan metin çalıştırmalarını almak için metin maddesi tarafından kullanılan yöntemdir. Çağrı, <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> aşağıdaki koşullardan biri ortaya çıkana kadar metin tarafından tekrar tekrar yapılır:  
  
- A <xref:System.Windows.Media.TextFormatting.TextEndOfLine> veya bir alt sınıf döndürülür.  
  
- Metnin birikmiş genişliği, madde metnini oluşturmak için çağrıda belirtilen maksimum satır genişliğini veya maddenin metnin <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A> metnin metnin ekimet ini aşar.  
  
- "CF", "LF" veya "CRLF" gibi bir Unicode yeni satır sırası döndürülür.  
  
<a name="section4"></a>
## <a name="providing-text-runs"></a>Metin Çalıştırmaları Sağlama  
 Metin biçimlendirme işleminin temeli, metin maddesi ile metin deposu arasındaki etkileşimdir. Uygulamanız, <xref:System.Windows.Media.TextFormatting.TextSource> metni nesnelerle <xref:System.Windows.Media.TextFormatting.TextRun> ve metni biçimlendirmek için hangi özelliklerle birlikte sağlar. Bu etkileşim, metin <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> formatter tarafından çağrılan yöntem tarafından ele alınır.  
  
 Aşağıdaki tablo, önceden tanımlanmış <xref:System.Windows.Media.TextFormatting.TextRun> bazı nesneleri gösterir.  
  
|TextRun Türü|Kullanım|  
|------------------|-----------|  
|<xref:System.Windows.Media.TextFormatting.TextCharacters>|Karakter gliflerinin temsilini metne aktarmak için kullanılan özel leştirilmiş metin çalışması.|  
|<xref:System.Windows.Media.TextFormatting.TextEmbeddedObject>|Ölçme, çarpma testi ve çizimin metin içindeki bir düğme veya görüntü gibi bütün olarak yapıldığı içeriği sağlamak için kullanılan özelleştirilmiş metin çalıştırMası.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfLine>|Özelleştirilmiş metin çalışması, satırın sonunu işaretlemek için kullanılır.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>|Paragrafın sonunu işaretlemek için kullanılan özel metin çalıştırı.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfSegment>|Bir önceki <xref:System.Windows.Media.TextFormatting.TextModifier> çalıştırmadan etkilenen kapsamı sona erdirmek gibi bir kesimin sonunu işaretlemek için kullanılan özelleştirilmiş metin çalıştırı.|  
|<xref:System.Windows.Media.TextFormatting.TextHidden>|Gizli karakter aralığını işaretlemek için kullanılan özelleştirilmiş metin çalıştırı.|  
|<xref:System.Windows.Media.TextFormatting.TextModifier>|Metnin özelliklerini değiştirmek için kullanılan özelleştirilmiş metin çalıştırımı, kapsamı içinde çalışır. Kapsam, bir sonraki eşleşen <xref:System.Windows.Media.TextFormatting.TextEndOfSegment> metin çalışmasına <xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>veya sonrakine kadar uzanır.|  
  
 Önceden tanımlanmış <xref:System.Windows.Media.TextFormatting.TextRun> nesnelerden herhangi biri alt sınıflanabilir. Bu, metin kaynağınızın özel veriler içeren metin çalıştırmalarıyla metin matter'ı sağlamasına olanak tanır.  
  
 Aşağıdaki örnekte bir <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> yöntem göster.. Bu metin <xref:System.Windows.Media.TextFormatting.TextRun> deposu nesneleri işlenmek üzere metne döndürür.  
  
 [!code-csharp[TextFormatterExample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/CustomTextSource.cs#101)]
 [!code-vb[TextFormatterExample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/CustomTextSource.vb#101)]  
  
> [!NOTE]
> Bu örnekte, metin deposu tüm metne aynı metin özelliklerini sağlar. Gelişmiş metin depolarının, tek tek karakterlerin farklı özelliklere sahip olması için kendi yayılma yönetimini uygulamaları gerekir.  
  
<a name="section5"></a>
## <a name="specifying-formatting-properties"></a>Biçimlendirme Özelliklerini Belirtme  
 <xref:System.Windows.Media.TextFormatting.TextRun>nesneler metin deposu tarafından sağlanan özellikler kullanılarak biçimlendirilir. Bu özellikler iki türde gelir <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> ve <xref:System.Windows.Media.TextFormatting.TextRunProperties>. <xref:System.Windows.Media.TextFormatting.TextParagraphProperties>gibi paragraf dahil <xref:System.Windows.TextAlignment> özellikleri <xref:System.Windows.FlowDirection>işlemek ve . <xref:System.Windows.Media.TextFormatting.TextRunProperties>ön plan fırçası <xref:System.Windows.Media.Typeface>ve yazı tipi boyutu gibi bir paragraf içinde çalışan her metin için farklı olabilecek özelliklerdir. Özel paragraf ve özel metin çalıştırma özellik türlerini uygulamak için, <xref:System.Windows.Media.TextFormatting.TextRunProperties> uygulamanızın sırasıyla ve bundan türemiş <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> sınıflar oluşturması gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WPF'de Tipografi](typography-in-wpf.md)
- [WPF'deki Belgeler](documents-in-wpf.md)
