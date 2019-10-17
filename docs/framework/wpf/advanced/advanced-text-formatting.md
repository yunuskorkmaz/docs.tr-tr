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
ms.openlocfilehash: 2c120c6d71cb22bc38909f980b2f6faf2b5c3663
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395212"
---
# <a name="advanced-text-formatting"></a>Gelişmiş Metin Biçimlendirme
Windows Presentation Foundation (WPF), uygulamanıza metin dahil etmek için güçlü bir API kümesi sağlar. @No__t-1 gibi düzen ve [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]Apı 'Leri, metin sunumu için en yaygın ve genel kullanım öğelerini sağlar. @No__t-0 ve <xref:System.Windows.Media.FormattedText> gibi çizim API 'Leri, çizimlerde biçimlendirilen metin ekleme için bir yol sağlar. @No__t-0, en gelişmiş düzeyde metin sunusunun, metin çalışma biçimlendirme yönetimi ve katıştırılmış nesne yönetimi gibi her yönüyle denetim için bir Genişletilebilir metin biçimlendirme altyapısı sağlar.  
  
 Bu konu, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] metin biçimlendirmeye giriş sağlar. İstemci uygulamasına odaklanır ve [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] metin biçimlendirme motorunu kullanır.  
  
> [!NOTE]
> Bu belgedeki tüm kod örnekleri, [Gelişmiş metin biçimlendirme örneğinde](https://go.microsoft.com/fwlink/?LinkID=159965)bulunabilir.  

<a name="prereq"></a>   
## <a name="prerequisites"></a>Prerequisites  
 Bu konu başlığı altında, metin sunumu için kullanılan yüksek düzey API 'lerle ilgili bilgi sahibi olduğunuz varsayılır. Çoğu Kullanıcı senaryosunda, bu konuda ele alınan Gelişmiş metin biçimlendirme API 'Leri gerekli değildir. Farklı metin API 'Lerine giriş için bkz. [WPF Içindeki belgeler](documents-in-wpf.md).  
  
<a name="section1"></a>   
## <a name="advanced-text-formatting"></a>Gelişmiş Metin Biçimlendirme  
 @No__t-1 ' deki metin düzeni ve [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] denetimleri, uygulamanıza biçimlendirilmiş metni kolayca eklemenize olanak tanıyan biçimlendirme özellikleri sağlar. Bu denetimler, yazı biçimini, boyutunu ve rengini içeren metin sunumunu işlemek için bir dizi özellik sunar. Normal koşullarda, bu denetimler uygulamanızdaki metin sunumunun çoğunu işleyebilir. Ancak, bazı gelişmiş senaryolar metin depolamanın ve metin sunumunun denetimini gerektirir. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], bu amaçla bir Genişletilebilir metin biçimlendirme altyapısı sağlar.  
  
 @No__t-0 ' da bulunan Gelişmiş metin biçimlendirme özellikleri metin biçimlendirme motoru, metin deposu, metin çalıştırmaları ve biçimlendirme özelliklerinden oluşur. @No__t-0 metin biçimlendirme altyapısı, sunum için kullanılacak metin satırları oluşturur. Bu, satır biçimlendirme işlemini başlatarak ve metin biçimlendiricisi <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A> ' a çağırarak elde edilir. Metin biçimlendiricisi, mağazanın <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> yöntemini çağırarak metin mağazalarından metin çalıştırmalarını alır. @No__t-0 nesneleri daha sonra metin biçimlendiricisi tarafından <xref:System.Windows.Media.TextFormatting.TextLine> nesneleriyle oluşturulur ve İnceleme veya görüntüleme için uygulamanıza verilir.  
  
<a name="section2"></a>   
## <a name="using-the-text-formatter"></a>Metin biçimlendirici 'yi kullanma  
 <xref:System.Windows.Media.TextFormatting.TextFormatter>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] metin biçimlendirme altyapısıdır ve metin satırları biçimlendirme ve ayırma hizmetleri sağlar. Metin biçimlendiricisi farklı metin karakter biçimlerini ve paragraf stillerini işleyebilir ve uluslararası metin düzeni için destek içerir.  
  
 Geleneksel bir metin API 'sinin aksine, <xref:System.Windows.Media.TextFormatting.TextFormatter>, bir geri arama yöntemi kümesi aracılığıyla metin düzeni istemcisiyle etkileşime girer. İstemcinin bu yöntemleri <xref:System.Windows.Media.TextFormatting.TextSource> sınıfının bir uygulamasında sağlamasını gerektirir. Aşağıdaki diyagramda, istemci uygulaması ile <xref:System.Windows.Media.TextFormatting.TextFormatter> arasındaki metin düzeni etkileşimi gösterilmektedir.  
  
 ![Metin düzeni istemcisi ve TextFormatter diyagramı](./media/advanced-text-formatting/text-layout-textformatter-interaction.png)  
  
 Metin biçimlendiricisi, <xref:System.Windows.Media.TextFormatting.TextSource> ' ın uygulanması olan metin deposundan biçimli metin satırları almak için kullanılır. Bu, ilk olarak <xref:System.Windows.Media.TextFormatting.TextFormatter.Create%2A> yöntemi kullanılarak metin biçimlendiricisi örneği oluşturularak yapılır. Bu yöntem, metin biçimlendiricisi örneğini oluşturur ve maksimum çizgi yüksekliği ve genişlik değerlerini ayarlar. Metin biçimlendiricisi 'nin bir örneği oluşturulduktan hemen sonra, satır oluşturma işlemi <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A> yöntemi çağırarak başlatılır. <xref:System.Windows.Media.TextFormatting.TextFormatter> metin kaynağına geri çağrı yapar ve bir satırı oluşturan metin çalıştırmaları için metin ve biçimlendirme parametrelerini alır.  
  
 Aşağıdaki örnekte, bir metin deposunu biçimlendirme işlemi gösterilmektedir. @No__t-0 nesnesi metin deposundan metin satırları almak ve sonra çizim için metin satırını <xref:System.Windows.Media.DrawingContext> ' e biçimlendirmek için kullanılır.  
  
 [!code-csharp[TextFormatterExample#100](~/samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[TextFormatterExample#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/Window1.xaml.vb#100)]  
  
<a name="section3"></a>   
## <a name="implementing-the-client-text-store"></a>Istemci metin deposunu uygulama  
 Metin biçimlendirme altyapısını genişlettiğinizde, metin deposunun tüm yönlerini uygulamanız ve yönetmeniz gerekir. Bu, önemsiz bir görev değildir. Metin deposu, metin çalıştırma özelliklerinin, paragraf özelliklerinin, katıştırılmış nesnelerin ve diğer benzer içeriklerin izlenmesinden sorumludur. Ayrıca, metin biçimlendirici tarafından <xref:System.Windows.Media.TextFormatting.TextLine> nesneleri oluşturmak için kullanılan tek <xref:System.Windows.Media.TextFormatting.TextRun> nesneleriyle metin biçimlendirici de sağlar.  
  
 Metin deposunun sanallaştırılmasını işlemek için, metin deposunun <xref:System.Windows.Media.TextFormatting.TextSource> ' dan türetilmesi gerekir. <xref:System.Windows.Media.TextFormatting.TextSource> metin deposundan metin çalıştırmalarını almak için metin biçimlendirici tarafından kullanılan yöntemi tanımlar. <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A>, metin biçimlendiricisi tarafından satır biçimlendirmesinde kullanılan metin çalıştırmalarını almak için kullanılan yöntemdir. @No__t-0 ' a yapılan çağrı, aşağıdaki koşullardan biri gerçekleşene kadar metin biçimlendiricisi tarafından tekrar tekrar yapılır:  
  
- @No__t-0 veya bir alt sınıf döndürülür.  
  
- Metnin birikmiş genişliği, metin biçimlendirici veya metin biçimlendirici <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A> metoduna yapılan çağrı içinde belirtilen en büyük çizgi genişliğini aşıyor.  
  
- "CF", "LF" veya "CRLF" gibi bir Unicode yeni satır dizisi döndürülür.  
  
<a name="section4"></a>   
## <a name="providing-text-runs"></a>Metin çalıştırmaları sağlama  
 Metin biçimlendirme işleminin çekirdeği, metin biçimlendiricisi ve metin deposu arasındaki etkileşimdir. @No__t-0 uygulamanız, <xref:System.Windows.Media.TextFormatting.TextRun> nesneleriyle metin biçimlendiricisi ve metin çalıştırmalarının formatlamasıdır özellikleri sağlar. Bu etkileşim, metin biçimlendiricisi tarafından çağrılan <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> yöntemi tarafından işlenir.  
  
 Aşağıdaki tabloda önceden tanımlanmış <xref:System.Windows.Media.TextFormatting.TextRun> nesnelerinden bazıları gösterilmektedir.  
  
|TextRun türü|Kullanım|  
|------------------|-----------|  
|<xref:System.Windows.Media.TextFormatting.TextCharacters>|Karakter karakterlerinin gösterimini metin biçimlendiricine geçirmek için kullanılan özel metin çalıştırması.|  
|<xref:System.Windows.Media.TextFormatting.TextEmbeddedObject>|Ölçüm, isabet testi ve çizim gibi metin içindeki bir düğme veya görüntü gibi tüm içerikleri sağlamak için kullanılan özel metin çalıştırması.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfLine>|Bir satırın sonunu işaretlemek için kullanılan özel metin çalıştırması.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>|Bir paragrafın sonunu işaretlemek için kullanılan özel metin çalıştırması.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfSegment>|Bir segmentin sonunu işaretlemek için kullanılan özel metin çalıştırması (örneğin, önceki bir <xref:System.Windows.Media.TextFormatting.TextModifier> çalıştırucunun etkilediği kapsamı sonlandırmak için).|  
|<xref:System.Windows.Media.TextFormatting.TextHidden>|Gizli bir karakter aralığını işaretlemek için kullanılan özelleştirilmiş metin.|  
|<xref:System.Windows.Media.TextFormatting.TextModifier>|Metin içinde metinlerin özelliklerini değiştirmek için kullanılan özelleştirilmiş metin çalıştırması. Kapsam bir sonraki eşleşen <xref:System.Windows.Media.TextFormatting.TextEndOfSegment> metin çalıştırmasına veya bir sonraki <xref:System.Windows.Media.TextFormatting.TextEndOfParagraph> ' i genişletir.|  
  
 Önceden tanımlanmış <xref:System.Windows.Media.TextFormatting.TextRun> nesnelerinden herhangi biri alt sınıflı olabilir. Bu, metin kaynağınızın özel verileri içeren metin çalıştırmaları ile metin biçimlendirici sağlamasına izin verir.  
  
 Aşağıdaki örnek bir <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> yöntemini gösterir. Bu metin deposu işleme için metin biçimlendirici öğesine <xref:System.Windows.Media.TextFormatting.TextRun> nesneleri döndürüyor.  
  
 [!code-csharp[TextFormatterExample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/CustomTextSource.cs#101)]
 [!code-vb[TextFormatterExample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/CustomTextSource.vb#101)]  
  
> [!NOTE]
> Bu örnekte, metin deposu metnin tümüne aynı metin özelliklerini sağlar. Gelişmiş metin mağazaların tek tek karakterlerin farklı özelliklere sahip olmasını sağlamak için kendi yayma yönetimini uygulaması gerekir.  
  
<a name="section5"></a>   
## <a name="specifying-formatting-properties"></a>Biçimlendirme özelliklerini belirtme  
 <xref:System.Windows.Media.TextFormatting.TextRun> nesneleri metin deposunun sunduğu özellikler kullanılarak biçimlendirilir. Bu özellikler iki tür gelir <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> ve <xref:System.Windows.Media.TextFormatting.TextRunProperties>. <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> <xref:System.Windows.TextAlignment> ve <xref:System.Windows.FlowDirection> gibi paragraf kapsamlı özellikleri işleyin. <xref:System.Windows.Media.TextFormatting.TextRunProperties>, bir paragraftaki, ön plan Fırçası, <xref:System.Windows.Media.Typeface> ve yazı tipi boyutu gibi her metin için farklı olabilecek özelliklerdir. Özel paragraf ve özel metin çalıştırma özelliği türlerini uygulamak için, uygulamanız sırasıyla <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> ve <xref:System.Windows.Media.TextFormatting.TextRunProperties> ' den türetilen sınıflar oluşturmalı.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WPF'de Tipografi](typography-in-wpf.md)
- [WPF'deki Belgeler](documents-in-wpf.md)
