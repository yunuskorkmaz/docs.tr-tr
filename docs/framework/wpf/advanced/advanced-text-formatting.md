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
ms.openlocfilehash: 469c62691ff38a8c5a01bec3ddfd7b324bab7eca
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969063"
---
# <a name="advanced-text-formatting"></a>Gelişmiş Metin Biçimlendirme
Windows Presentation Foundation (WPF), uygulamanıza metin dahil etmek için güçlü bir API kümesi sağlar. Gibi Düzen [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]ve API 'ler <xref:System.Windows.Controls.TextBlock>, metin sunumu için en yaygın ve genel kullanım öğeleri sağlar. <xref:System.Windows.Media.GlyphRunDrawing> Ve<xref:System.Windows.Media.FormattedText>gibi çizim API 'leri, çizimlerde biçimlendirilen metin ekleme için bir yol sağlar. En gelişmiş düzeyde, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] metin sunumu yönetimi, metin çalışma biçimlendirme yönetimi ve katıştırılmış nesne yönetimi gibi metin sunumunun her yönüyle denetlemek için Genişletilebilir metin biçimlendirme altyapısı sağlar.  
  
 Bu konu, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] metin biçimlendirmeye giriş sağlar. İstemci uygulamasına odaklanır ve [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] metin biçimlendirme altyapısının kullanımını kullanır.  
  
> [!NOTE]
> Bu belgedeki tüm kod örnekleri, [Gelişmiş metin biçimlendirme örneğinde](https://go.microsoft.com/fwlink/?LinkID=159965)bulunabilir.  

<a name="prereq"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konu başlığı altında, metin sunumu için kullanılan yüksek düzey API 'lerle ilgili bilgi sahibi olduğunuz varsayılır. Çoğu Kullanıcı senaryosunda, bu konuda ele alınan Gelişmiş metin biçimlendirme API 'Leri gerekli değildir. Farklı metin API 'Lerine giriş için bkz. [WPF Içindeki belgeler](documents-in-wpf.md).  
  
<a name="section1"></a>   
## <a name="advanced-text-formatting"></a>Gelişmiş Metin Biçimlendirme  
 ' Deki [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] metin düzeni ve denetimleri, uygulamanıza biçimlendirilmiş metni kolayca eklemenize olanak tanıyan biçimlendirme özellikleri sağlar. Bu denetimler, yazı biçimini, boyutunu ve rengini içeren metin sunumunu işlemek için bir dizi özellik sunar. Normal koşullarda, bu denetimler uygulamanızdaki metin sunumunun çoğunu işleyebilir. Ancak, bazı gelişmiş senaryolar metin depolamanın ve metin sunumunun denetimini gerektirir. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]Bu amaçla bir Genişletilebilir metin biçimlendirme altyapısı sağlar.  
  
 İçinde [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] bulunan Gelişmiş metin biçimlendirme özellikleri, metin biçimlendirme motoru, metin deposu, metin çalıştırmaları ve biçimlendirme özelliklerinden oluşur. Metin biçimlendirme altyapısı <xref:System.Windows.Media.TextFormatting.TextFormatter>, sunum için kullanılacak metin satırları oluşturur. Bu, satır biçimlendirme işlemini başlatarak ve metin biçimlendirici 'nin <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A>çağrılmasıyla elde edilir. Metin biçimlendiricisi, mağaza <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> yöntemini çağırarak Metin deponuzdan metin çalıştırmalarını alır. Nesneler daha sonra metin biçimlendirici tarafından <xref:System.Windows.Media.TextFormatting.TextLine> nesneler halinde oluşturulur ve İnceleme veya görüntüleme için uygulamanıza verilir. <xref:System.Windows.Media.TextFormatting.TextRun>  
  
<a name="section2"></a>   
## <a name="using-the-text-formatter"></a>Metin biçimlendirici 'yi kullanma  
 <xref:System.Windows.Media.TextFormatting.TextFormatter>[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] metin biçimlendirme altyapısıdır ve metin çizgilerini biçimlendirmek ve bölmek için hizmetler sağlar. Metin biçimlendiricisi farklı metin karakter biçimlerini ve paragraf stillerini işleyebilir ve uluslararası metin düzeni için destek içerir.  
  
 Geleneksel bir metin API 'sinin <xref:System.Windows.Media.TextFormatting.TextFormatter> aksine, bir dizi geri arama yöntemi aracılığıyla metin düzeni istemcisiyle etkileşime girer. İstemcinin bu yöntemleri <xref:System.Windows.Media.TextFormatting.TextSource> sınıfının bir uygulamasında sağlamasını gerektirir. Aşağıdaki diyagramda, istemci uygulaması ve <xref:System.Windows.Media.TextFormatting.TextFormatter>arasındaki metin düzeni etkileşimi gösterilmektedir.  
  
 ![Metin düzeni istemcisi ve TextFormatter diyagramı](./media/advanced-text-formatting/text-layout-textformatter-interaction.png)  
  
 Metin biçimlendiricisi, uygulamasının bir uygulamasına ait <xref:System.Windows.Media.TextFormatting.TextSource>metin deposundan biçimli metin satırları almak için kullanılır. Bu, ilk olarak <xref:System.Windows.Media.TextFormatting.TextFormatter.Create%2A> yöntemi kullanılarak metin biçimlendirici bir örneği oluşturularak yapılır. Bu yöntem, metin biçimlendiricisi örneğini oluşturur ve maksimum çizgi yüksekliği ve genişlik değerlerini ayarlar. Metin biçimlendiricisi 'nin bir örneği oluşturulduktan hemen sonra, hat oluşturma işlemi <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A> yöntemi çağırarak başlatılır. <xref:System.Windows.Media.TextFormatting.TextFormatter>metin kaynağına geri çağrı yapar ve bir satırı oluşturan metin çalıştırmaları için metin ve biçimlendirme parametrelerini alır.  
  
 Aşağıdaki örnekte, bir metin deposunu biçimlendirme işlemi gösterilmektedir. Nesnesi metin deposundan metin satırları almak ve sonra çizim <xref:System.Windows.Media.DrawingContext>için metin satırını biçimlendirmek için kullanılır. <xref:System.Windows.Media.TextFormatting.TextFormatter>  
  
 [!code-csharp[TextFormatterExample#100](~/samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[TextFormatterExample#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/Window1.xaml.vb#100)]  
  
<a name="section3"></a>   
## <a name="implementing-the-client-text-store"></a>Istemci metin deposunu uygulama  
 Metin biçimlendirme altyapısını genişlettiğinizde, metin deposunun tüm yönlerini uygulamanız ve yönetmeniz gerekir. Bu, önemsiz bir görev değildir. Metin deposu, metin çalıştırma özelliklerinin, paragraf özelliklerinin, katıştırılmış nesnelerin ve diğer benzer içeriklerin izlenmesinden sorumludur. Ayrıca metin biçimlendirici tarafından nesne oluşturmak <xref:System.Windows.Media.TextFormatting.TextRun> <xref:System.Windows.Media.TextFormatting.TextLine> için kullanılan tek tek nesneleriyle metin biçimlendirici de sağlar.  
  
 Metin deposunun sanallaştırılmasını işlemek için metin deposunun öğesinden <xref:System.Windows.Media.TextFormatting.TextSource>türetilmesi gerekir. <xref:System.Windows.Media.TextFormatting.TextSource>metin deposundaki metin çalıştırmalarını almak için metin biçimlendirici tarafından kullanılan yöntemi tanımlar. <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A>, satır biçimlendirmesinde kullanılan metin çalıştırmalarını almak için metin biçimlendirici tarafından kullanılan yöntemdir. Çağrısı <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> , aşağıdaki koşullardan biri gerçekleşene kadar metin biçimlendiricisi tarafından tekrar tekrar yapılır:  
  
- Bir <xref:System.Windows.Media.TextFormatting.TextEndOfLine> veya alt sınıf döndürülür.  
  
- Metnin birikmiş genişliği, metin biçimlendirici veya metin biçimlendirici <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A> yöntemine yapılan çağrıyı oluşturmak için yapılan çağrıda belirtilen en büyük çizgi genişliğini aşıyor.  
  
- " [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] CF", "LF" veya "crlf" gibi bir yeni satır dizisi döndürülür.  
  
<a name="section4"></a>   
## <a name="providing-text-runs"></a>Metin çalıştırmaları sağlama  
 Metin biçimlendirme işleminin çekirdeği, metin biçimlendiricisi ve metin deposu arasındaki etkileşimdir. Uygulamanız <xref:System.Windows.Media.TextFormatting.TextSource> , <xref:System.Windows.Media.TextFormatting.TextRun> nesne ve metin çalıştırmalarının biçimlendirilecek özelliklerle metin biçimlendirici sağlar. Bu etkileşim, metin biçimlendiricisi tarafından <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> çağrılan yöntemi tarafından işlenir.  
  
 Aşağıdaki tabloda önceden tanımlanmış <xref:System.Windows.Media.TextFormatting.TextRun> bazı nesneler gösterilmektedir.  
  
|TextRun türü|Kullanım|  
|------------------|-----------|  
|<xref:System.Windows.Media.TextFormatting.TextCharacters>|Karakter karakterlerinin gösterimini metin biçimlendiricine geçirmek için kullanılan özel metin çalıştırması.|  
|<xref:System.Windows.Media.TextFormatting.TextEmbeddedObject>|Ölçüm, isabet testi ve çizim gibi metin içindeki bir düğme veya görüntü gibi tüm içerikleri sağlamak için kullanılan özel metin çalıştırması.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfLine>|Bir satırın sonunu işaretlemek için kullanılan özel metin çalıştırması.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>|Bir paragrafın sonunu işaretlemek için kullanılan özel metin çalıştırması.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfSegment>|Bir segmentin sonunu işaretlemek için kullanılan özel metin çalıştırması (örneğin, önceki <xref:System.Windows.Media.TextFormatting.TextModifier> bir çalıştırmanın etkilediği kapsamı bitirmek için).|  
|<xref:System.Windows.Media.TextFormatting.TextHidden>|Gizli bir karakter aralığını işaretlemek için kullanılan özelleştirilmiş metin.|  
|<xref:System.Windows.Media.TextFormatting.TextModifier>|Metin içinde metinlerin özelliklerini değiştirmek için kullanılan özelleştirilmiş metin çalıştırması. Kapsam bir sonraki eşleşen <xref:System.Windows.Media.TextFormatting.TextEndOfSegment> metin çalıştırmasına veya bir sonraki <xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>öğesine genişletilir.|  
  
 Önceden tanımlanmış <xref:System.Windows.Media.TextFormatting.TextRun> nesnelerden herhangi biri alt sınıflı olabilir. Bu, metin kaynağınızın özel verileri içeren metin çalıştırmaları ile metin biçimlendirici sağlamasına izin verir.  
  
 Aşağıdaki örnekte bir <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> yöntemi gösterilmektedir. Bu metin deposu işleme <xref:System.Windows.Media.TextFormatting.TextRun> için nesneleri metin biçimlendirici öğesine döndürür.  
  
 [!code-csharp[TextFormatterExample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/CustomTextSource.cs#101)]
 [!code-vb[TextFormatterExample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/CustomTextSource.vb#101)]  
  
> [!NOTE]
> Bu örnekte, metin deposu metnin tümüne aynı metin özelliklerini sağlar. Gelişmiş metin mağazaların tek tek karakterlerin farklı özelliklere sahip olmasını sağlamak için kendi yayma yönetimini uygulaması gerekir.  
  
<a name="section5"></a>   
## <a name="specifying-formatting-properties"></a>Biçimlendirme özelliklerini belirtme  
 <xref:System.Windows.Media.TextFormatting.TextRun>nesneler, metin deposunun sunduğu özellikler kullanılarak biçimlendirilir. Bu özellikler iki tür <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> olarak gelir ve. <xref:System.Windows.Media.TextFormatting.TextRunProperties> <xref:System.Windows.Media.TextFormatting.TextParagraphProperties><xref:System.Windows.TextAlignment> ve<xref:System.Windows.FlowDirection>gibi paragraf kapsamlı özellikleri işleyin. <xref:System.Windows.Media.TextFormatting.TextRunProperties>, ön plan Fırçası, <xref:System.Windows.Media.Typeface>ve yazı tipi boyutu gibi bir paragraf içinde çalıştırılan her metin için farklı olabilecek özelliklerdir. Özel paragraf ve özel metin çalışma özelliği türlerini uygulamak için uygulamanızın, <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> ve <xref:System.Windows.Media.TextFormatting.TextRunProperties> sırasıyla türetilen sınıflar oluşturması gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WPF'de Tipografi](typography-in-wpf.md)
- [WPF'deki Belgeler](documents-in-wpf.md)
