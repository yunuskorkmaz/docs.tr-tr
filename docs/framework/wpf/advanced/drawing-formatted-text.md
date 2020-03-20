---
title: Biçimlendirilmiş Metin Çizme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [WPF]
- typography [WPF], drawing formatted text
- formatted text [WPF]
- drawing [WPF], formatted text
ms.assetid: b1d851c1-331c-4814-9964-6fe769db6f1f
ms.openlocfilehash: 1e82795afbdd5b1b0a05f95600ebdb92fc134b7d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186563"
---
# <a name="drawing-formatted-text"></a>Biçimlendirilmiş Metin Çizme
Bu konu <xref:System.Windows.Media.FormattedText> nesnenin özelliklerine genel bir bakış sağlar. Bu nesne, uygulamalarda [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] metin çizmek için düşük düzeyli denetim sağlar.  

## <a name="technology-overview"></a>Teknolojiye Genel Bakış  
 Nesne, <xref:System.Windows.Media.FormattedText> metindeki her karakterin ayrı ayrı biçimlendirilebildiği çok satırlı metin çizmenize olanak tanır. Aşağıdaki örnekte, çeşitli biçimleri uygulanan metin gösterilmektedir.  
  
 ![BiçimlendirilmişMetin nesnesi kullanılarak görüntülenen metin](./media/typography-in-wpf/text-formatted-linear-gradient.jpg)  
  
> [!NOTE]
> Win32 API'sinden göç eden geliştiriciler için [Win32 Geçiş](#win32_migration) bölümündeki tabloda Win32 DrawText [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]bayrakları ve yaklaşık eşdeğeri listelenmiştir.  
  
### <a name="reasons-for-using-formatted-text"></a>Biçimlendirilmiş Metni Kullanma Nedenleri  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ekrana metin çizmek için birden çok denetim içerir. Her denetim farklı bir senaryoyu hedeflemektedir ve kendi özellik ve sınırlamalar listesi vardır. Genel olarak, <xref:System.Windows.Controls.TextBlock> öğe sınırlı metin desteği gerektiğinde kullanılmalıdır( örneğin bir [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. <xref:System.Windows.Controls.Label>en az metin desteği gerektiğinde kullanılabilir. Daha fazla bilgi için [WPF'deki Belgeler'e](documents-in-wpf.md)bakın.  
  
 Nesne <xref:System.Windows.Media.FormattedText> metin denetimlerine göre [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] daha fazla metin biçimlendirme özellikleri sağlar ve metni dekoratif öğe olarak kullanmak istediğiniz durumlarda yararlı olabilir. Daha fazla bilgi için aşağıdaki bölüme bakın [Biçimlendirilmiş Metni Geometriye Dönüştürün.](#converting_formatted_text)  
  
 Buna ek <xref:System.Windows.Media.FormattedText> olarak, nesne metin yönelimli <xref:System.Windows.Media.DrawingVisual>türetilmiş nesneler oluşturmak için yararlıdır. <xref:System.Windows.Media.DrawingVisual>şekilleri, görüntüleri veya metni işlemek için kullanılan hafif bir çizim sınıfıdır. Daha fazla bilgi için [DrawingVisuals Örnek Kullanarak Test Hit](https://github.com/Microsoft/WPF-Samples/tree/master/Visual%20Layer/DrawingVisual)bakın.  
  
## <a name="using-the-formattedtext-object"></a>Biçimlendirilmiş Metin Nesnesini Kullanma  
 Biçimlendirilmiş metin oluşturmak için, bir <xref:System.Windows.Media.FormattedText.%23ctor%2A> <xref:System.Windows.Media.FormattedText> nesne oluşturmak için oluşturucuyu çağırın. İlk biçimlendirilmiş metin dizesini oluşturduktan sonra, bir dizi biçimlendirme stili uygulayabilirsiniz.  
  
 Metni <xref:System.Windows.Media.FormattedText.MaxTextWidth%2A> belirli bir genişliğe kısıtlamak için özelliği kullanın. Metin, belirtilen genişliği aşmamak için otomatik olarak kaydırır. Metni <xref:System.Windows.Media.FormattedText.MaxTextHeight%2A> belirli bir yüksekliğe kısıtlamak için özelliği kullanın. Metin bir elips görüntüler, "..." belirtilen yüksekliği aşan metin için.  
  
 ![Wordwrap ve elipsile görüntülenen metin.](./media/drawing-formatted-text/formatted-text-wordwrap-ellipsis.png)
  
 Birden çok biçimlendirme stilini bir veya daha fazla karaktere uygulayabilirsiniz. Örneğin, metindeki <xref:System.Windows.Media.FormattedText.SetFontSize%2A> ilk beş <xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A> karakterin biçimlendirmesini değiştirmek için hem yöntemleri hem de yöntemleri arayabilirsiniz.  
  
 Aşağıdaki kod örneği bir <xref:System.Windows.Media.FormattedText> nesne oluşturur ve sonra metne birkaç biçimlendirme stili uygular.  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]  
  
### <a name="font-size-unit-of-measure"></a>Ölçünün Yazı Tipi Boyut Birimi  
 Uygulamalardaki diğer metin [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] nesnelerinde olduğu <xref:System.Windows.Media.FormattedText> gibi, nesne ölçü birimi olarak aygıttan bağımsız pikseller kullanır. Ancak, çoğu Win32 uygulaması ölçü birimi olarak noktaları kullanır. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Uygulamalardaki nokta birimlerinde görüntü metni kullanmak istiyorsanız, aygıttan bağımsız birimleri (birim başına 1/96th inç) noktalara dönüştürmeniz gerekir. Aşağıdaki kod örneği, bu dönüşümün nasıl gerçekleştirilini gösterir.  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets2)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets2)]  
  
<a name="converting_formatted_text"></a>
### <a name="converting-formatted-text-to-a-geometry"></a>Biçimlendirilmiş Metni Geometriye Dönüştürme  
 Biçimlendirilmiş metni nesnelere <xref:System.Windows.Media.Geometry> dönüştürerek görsel olarak ilginç başka metin türleri oluşturabilirsiniz. Örneğin, bir metin <xref:System.Windows.Media.Geometry> dizesinin anahatlarını temel alan bir nesne oluşturabilirsiniz.  
  
 ![Doğrusal degrade fırçası kullanarak metin anahattı](./media/typography-in-wpf/text-outline-linear-gradient.jpg)
  
 Aşağıdaki örnekler, dönüştürülen metnin konturunu, dolgusunu ve vurgusunu değiştirerek ilginç görsel efektler oluşturmanın çeşitli yollarını göstermektedir.  
  
 ![Dolgu ve kontur için farklı renklere sahip metin](./media/typography-in-wpf/fill-stroke-text-effect.jpg)  
  
 ![Kontura uygulanan görüntü fırçası ile metin](./media/typography-in-wpf/image-brush-application.jpg)
  
 ![Kontur ve vurgulamaya uygulanan görüntü fırçası ile metin](./media/typography-in-wpf/image-brush-text-application.jpg)
  
 Metin bir <xref:System.Windows.Media.Geometry> nesneye dönüştürüldüğünde, artık bir karakter topluluğu değildir—metin dizesindeki karakterleri değiştiremezsiniz. Ancak, kontur ve dolgu özelliklerini değiştirerek dönüştürülen metnin görünümünü etkileyebilirsiniz. Kontur, dönüştürülen metnin anahatlarını ifade eder; dolgu, dönüştürülen metnin anahat içindeki alanı ifade eder. Daha fazla bilgi için [bkz.](how-to-create-outlined-text.md)  
  
 Ayrıca biçimlendirilmiş metni bir <xref:System.Windows.Media.PathGeometry> nesneye dönüştürebilir ve metni vurgulamak için nesneyi kullanabilirsiniz. Örneğin, animasyon biçimlendirilmiş metnin <xref:System.Windows.Media.PathGeometry> anahatlarını izlemesi için nesneye animasyon uygulayabilirsiniz.  
  
 Aşağıdaki örnek, bir <xref:System.Windows.Media.PathGeometry> nesneye dönüştürülen biçimlendirilmiş metni gösterir. Animasyonlu bir elips, işlenen metnin konturlarının yolunu izler.  
  
 ![Metnin yol geometrisini izleyen küre](./media/drawing-formatted-text/sphere-following-geometry-path.gif)  
Metnin yol geometrisini izleyen küre  
  
 Daha fazla bilgi için [bkz: Metin için Bir YolGeometri Animasyonu Oluşturun.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms743610(v=vs.100))  
  
 Bir <xref:System.Windows.Media.PathGeometry> nesneye dönüştürüldükten sonra biçimlendirilmiş metin için başka ilginç kullanımlar oluşturabilirsiniz. Örneğin, videonun içinde görüntülemek için klibi kesebilirsiniz.  
  
 ![Metnin yol geometrisinde görüntüleyen video](./media/drawing-formatted-text/video-displaying-text-path-geometry.png)
  
<a name="win32_migration"></a>
## <a name="win32-migration"></a>Win32 Geçiş  
 Çizim metninin <xref:System.Windows.Media.FormattedText> özellikleri Win32 DrawText işlevinin özelliklerine benzer. Win32 API'sinden göç eden geliştiriciler için aşağıdaki tabloda Win32 DrawText [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]bayrakları ve yaklaşık eşdeğeri listelenmiştir.  
  
|DrawText bayrağı|WPF eşdeğeri|Notlar|  
|-------------------|--------------------|-----------|  
|DT_BOTTOM|<xref:System.Windows.Media.FormattedText.Height%2A>|Uygun <xref:System.Windows.Media.FormattedText.Height%2A> bir Win32 DrawText 'y' konumunu hesaplamak için özelliği kullanın.|  
|DT_CALCRECT|<xref:System.Windows.Media.FormattedText.Height%2A>, <xref:System.Windows.Media.FormattedText.Width%2A>|Çıktı <xref:System.Windows.Media.FormattedText.Height%2A> dikdörtgenini hesaplamak için ve <xref:System.Windows.Media.FormattedText.Width%2A> özelliklerini kullanın.|  
|DT_CENTER|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Değeri <xref:System.Windows.Media.FormattedText.TextAlignment%2A> <xref:System.Windows.TextAlignment.Center>'ne ayarlanmış özelliği kullanın.|  
|DT_EDITCONTROL|None|Gerek yok. Alan genişliği ve son satır oluşturma, çerçeve düzendenetimindekiyle aynıdır.|  
|DT_END_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|Değeri <xref:System.Windows.TextTrimming.CharacterEllipsis> <xref:System.Windows.Media.FormattedText.Trimming%2A> ile özelliği kullanın.<br /><br /> Win32'yi DT_WORD_ELIPSIS son elipsile DT_END_ELLIPSIS almak için kullanın—bu <xref:System.Windows.TextTrimming.WordEllipsis> durumda karakter elipsleri yalnızca tek bir satıra sığmayan sözcüklerde oluşur.|  
|DT_EXPAND_TABS|None|Gerek yok. Sekmeler, yaklaşık olarak 8 dilden bağımsız karakter genişliğinde olan her 4 ems'i durduracak şekilde otomatik olarak genişletilir.|  
|DT_EXTERNALLEADING|None|Gerek yok. Dış satır aralığı her zaman satır aralığına dahildir. Kullanıcı <xref:System.Windows.Media.FormattedText.LineHeight%2A> tanımlı satır aralığı oluşturmak için özelliği kullanın.|  
|DT_HIDEPREFIX|None|Desteklenmiyor. Nesneyi oluşturmadan önce dizedeki <xref:System.Windows.Media.FormattedText> '&'ı kaldırın.|  
|DT_LEFT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Bu varsayılan metin hizalamasıdır. Değeri <xref:System.Windows.Media.FormattedText.TextAlignment%2A> <xref:System.Windows.TextAlignment.Left>'ne ayarlanmış özelliği kullanın. (Yalnızca WPF)|  
|DT_MODIFYSTRING|None|Desteklenmiyor.|  
|DT_NOCLIP|<xref:System.Windows.Media.Visual.VisualClip%2A>|Kırpma otomatik olarak gerçekleşmez. Metni klibini kesmek istiyorsanız, <xref:System.Windows.Media.Visual.VisualClip%2A> özelliği kullanın.|  
|DT_NOFULLWIDTHCHARBREAK|None|Desteklenmiyor.|  
|DT_NOPREFIX|None|Gerek yok. Dizelerdeki '&' karakteri her zaman normal bir karakter olarak kabul edilir.|  
|DT_PATHELLIPSIS|None|Değeri <xref:System.Windows.TextTrimming.WordEllipsis> <xref:System.Windows.Media.FormattedText.Trimming%2A> ile özelliği kullanın.|  
|DT_PREFIX|None|Desteklenmiyor. Hızlandırıcı anahtarı veya bağlantı gibi metin için alt çiziler <xref:System.Windows.Media.FormattedText.SetTextDecorations%2A> kullanmak istiyorsanız, yöntemi kullanın.|  
|DT_PREFIXONLY|None|Desteklenmiyor.|  
|DT_RIGHT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Değeri <xref:System.Windows.Media.FormattedText.TextAlignment%2A> <xref:System.Windows.TextAlignment.Right>'ne ayarlanmış özelliği kullanın. (Yalnızca WPF)|  
|DT_RTLREADING|<xref:System.Windows.Media.FormattedText.FlowDirection%2A>|Özelliği <xref:System.Windows.Media.FormattedText.FlowDirection%2A> ' <xref:System.Windows.FlowDirection.RightToLeft>ye ayarlayın.|  
|DT_SINGLELINE|None|Gerek yok. <xref:System.Windows.Media.FormattedText>nesneler, <xref:System.Windows.Media.FormattedText.MaxTextWidth%2A> özellik ayarlanmadıkça veya metin bir satır döndürme/satır beslemesi (CR/LF) içermediği sürece tek satır denetimi olarak değişir.|  
|DT_TABSTOP|None|Kullanıcı tanımlı sekme durdurma pozisyonları için destek yok.|  
|DT_TOP|<xref:System.Windows.Media.FormattedText.Height%2A>|Gerek yok. En üst yaslama varsayılandır. Diğer dikey konumlandırma değerleri, uygun <xref:System.Windows.Media.FormattedText.Height%2A> bir Win32 DrawText 'y' konumunu hesaplamak için özellik kullanılarak tanımlanabilir.|  
|DT_VCENTER|<xref:System.Windows.Media.FormattedText.Height%2A>|Uygun <xref:System.Windows.Media.FormattedText.Height%2A> bir Win32 DrawText 'y' konumunu hesaplamak için özelliği kullanın.|  
|DT_WORDBREAK|None|Gerek yok. Sözcük bölme nesneleri <xref:System.Windows.Media.FormattedText> ile otomatik olarak gerçekleşir. Devre dışı kalamazsınız.|  
|DT_WORD_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|Değeri <xref:System.Windows.TextTrimming.WordEllipsis> <xref:System.Windows.Media.FormattedText.Trimming%2A> ile özelliği kullanın.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.FormattedText>
- [WPF'deki Belgeler](documents-in-wpf.md)
- [WPF'de Tipografi](typography-in-wpf.md)
- [Anahatları Belirlenmiş Metin Oluşturma](how-to-create-outlined-text.md)
- [Nasıl yapilir: Metin için YolGeometri Animasyonu Oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms743610(v=vs.100))
