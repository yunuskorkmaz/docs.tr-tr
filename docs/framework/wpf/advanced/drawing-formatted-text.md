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
ms.openlocfilehash: c786137a471e0199a8ac60f8d82b4ce440e33b7e
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740403"
---
# <a name="drawing-formatted-text"></a>Biçimlendirilmiş Metin Çizme
Bu konu, <xref:System.Windows.Media.FormattedText> nesnesinin özelliklerine genel bir bakış sağlar. Bu nesne [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamalarında metin çizmek için alt düzey denetim sağlar.  

## <a name="technology-overview"></a>Teknolojiye genel bakış  
 <xref:System.Windows.Media.FormattedText> nesnesi, metin içindeki her karakterin ayrı ayrı biçimlendirilebileceği çok satırlı metin çizmenizi sağlar. Aşağıdaki örnek, birkaç biçimin uygulanmış olduğu metni gösterir.  
  
 ![FormattedText nesnesi kullanılarak görünen metin](./media/typography-in-wpf/text-formatted-linear-gradient.jpg)  
  
> [!NOTE]
> Win32 API geçiş yapan geliştiriciler için, [Win32 geçiş](#win32_migration) bölümündeki tablo, Win32 DrawText bayraklarını ve [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]yaklaşık eşdeğerini listeler.  
  
### <a name="reasons-for-using-formatted-text"></a>Biçimli metin kullanma nedenleri  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], ekrana metin çizme için birden çok denetim içerir. Her denetim farklı bir senaryoya yöneliktir ve kendi özellik ve kısıtlama listesine sahiptir. Genellikle, bir [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]kısa bir cümle gibi sınırlı metin desteği gerektiğinde <xref:System.Windows.Controls.TextBlock> öğesi kullanılmalıdır. <xref:System.Windows.Controls.Label>, en az metin desteği gerekli olduğunda kullanılabilir. Daha fazla bilgi için bkz. [WPF Içindeki belgeler](documents-in-wpf.md).  
  
 <xref:System.Windows.Media.FormattedText> nesnesi, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] metin denetimlerinden daha fazla metin biçimlendirme özelliği sağlar ve metni dekoratif bir öğe olarak kullanmak istediğiniz durumlarda yararlı olabilir. Daha fazla bilgi için, [biçimlendirilen metni bir geometriye dönüştürmenin](#converting_formatted_text)aşağıdaki bölümüne bakın.  
  
 Ayrıca, <xref:System.Windows.Media.FormattedText> nesnesi metin odaklı <xref:System.Windows.Media.DrawingVisual>türetilmiş nesneler oluşturmak için faydalıdır. <xref:System.Windows.Media.DrawingVisual> şekilleri, resimleri veya metinleri işlemek için kullanılan basit bir çizim sınıfıdır. Daha fazla bilgi için bkz. [Drawinggörselleri kullanarak Isabet testi örneği](https://go.microsoft.com/fwlink/?LinkID=159994).  
  
## <a name="using-the-formattedtext-object"></a>FormattedText nesnesini kullanma  
 Biçimli metin oluşturmak için, bir <xref:System.Windows.Media.FormattedText> nesnesi oluşturmak üzere <xref:System.Windows.Media.FormattedText.%23ctor%2A> oluşturucusunu çağırın. İlk biçimlendirilmiş metin dizesini oluşturduktan sonra bir dizi biçimlendirme stili uygulayabilirsiniz.  
  
 Metni belirli bir genişliğe kısıtlamak için <xref:System.Windows.Media.FormattedText.MaxTextWidth%2A> özelliğini kullanın. Metin, belirtilen genişliği aşmaktan kaçınmak için otomatik olarak kaydırılır. Metni belirli bir yüksekliğe kısıtlamak için <xref:System.Windows.Media.FormattedText.MaxTextHeight%2A> özelliğini kullanın. Metinde "..." üç nokta görüntülenir belirtilen yüksekliği aşan metin için.  
  
 ![WordWrap ve üç nokta ile görünen metin.](./media/drawing-formatted-text/formatted-text-wordwrap-ellipsis.png)    
  
 Bir veya daha fazla karaktere birden çok biçimlendirme stili uygulayabilirsiniz. Örneğin, metindeki ilk beş karakterin biçimlendirmesini değiştirmek için hem <xref:System.Windows.Media.FormattedText.SetFontSize%2A> hem de <xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A> yöntemlerini çağırabilirsiniz.  
  
 Aşağıdaki kod örneği bir <xref:System.Windows.Media.FormattedText> nesnesi oluşturur ve sonra metne birkaç biçimlendirme stili uygular.  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]  
  
### <a name="font-size-unit-of-measure"></a>Yazı tipi boyutu ölçü birimi  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamalardaki diğer metin nesnelerinde olduğu gibi, <xref:System.Windows.Media.FormattedText> nesnesi, ölçü birimi olarak cihazdan bağımsız pikseller kullanır. Ancak, çoğu Win32 uygulaması, ölçü birimi olarak noktaları kullanır. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamalarında punto birimlerinde görüntü metni kullanmak istiyorsanız, cihazdan bağımsız birimleri (birim başına 1/96th) noktalara dönüştürmeniz gerekir. Aşağıdaki kod örneği, bu dönüştürmenin nasıl gerçekleştirileceğini gösterir.  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets2)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets2)]  
  
<a name="converting_formatted_text"></a>   
### <a name="converting-formatted-text-to-a-geometry"></a>Biçimlendirilen metni bir geometriye dönüştürme  
 Biçimlendirilen metni <xref:System.Windows.Media.Geometry> nesnelerine dönüştürebilirsiniz, böylece görsel açıdan ilgi çekici metin türlerini oluşturabilirsiniz. Örneğin, bir metin dizesinin ana hattını temel alan bir <xref:System.Windows.Media.Geometry> nesnesi oluşturabilirsiniz.  
  
 ![Doğrusal gradyan fırçası kullanan metin ana hattı](./media/typography-in-wpf/text-outline-linear-gradient.jpg)    
  
 Aşağıdaki örneklerde, dönüştürülmüş metnin vuruş, dolgusu ve vurgulanmasını değiştirerek ilginç görsel etkiler oluşturmanın birkaç yolu gösterilmektedir.  
  
 ![Fill ve Stroke için farklı renkler içeren metin](./media/typography-in-wpf/fill-stroke-text-effect.jpg)  
  
 ![Görüntüye resim fırçası uygulanmış metin](./media/typography-in-wpf/image-brush-application.jpg)
  
 ![Kontura ve vurgulamaya uygulanan resim fırçasının bulunduğu metin](./media/typography-in-wpf/image-brush-text-application.jpg)
  
 Metin bir <xref:System.Windows.Media.Geometry> nesnesine dönüştürüldüğünde, artık bir karakter koleksiyonu değildir; metin dizesindeki karakterleri değiştiremezsiniz. Ancak, kontur ve Fill özelliklerini değiştirerek dönüştürülen metnin görünümünü etkileyebilirsiniz. Vuruş, dönüştürülen metnin ana hattını ifade eder; Fill, dönüştürülen metnin ana hattının içindeki alanı ifade eder. Daha fazla bilgi için bkz. [anahatları belirlenmiş metin oluşturma](how-to-create-outlined-text.md).  
  
 Ayrıca, biçimli metni bir <xref:System.Windows.Media.PathGeometry> nesnesine dönüştürebilir ve nesneyi metin vurgulamak için kullanabilirsiniz. Örneğin, animasyonun biçimli metnin ana hattını takip edebilmesi için <xref:System.Windows.Media.PathGeometry> nesnesine bir animasyon uygulayabilirsiniz.  
  
 Aşağıdaki örnek, <xref:System.Windows.Media.PathGeometry> nesnesine dönüştürülen biçimlendirilmiş metni gösterir. Hareketli bir elips, işlenen metnin vuruşlarının yolunu izler.  
  
 ![Metnin yol geometrisini izleyen Sphere](./media/drawing-formatted-text/sphere-following-geometry-path.gif)  
Metnin yol geometrisini izleyen Sphere  
  
 Daha fazla bilgi için bkz. [nasıl yapılır: metin Için PathGeometry animasyonu oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms743610(v=vs.100)).  
  
 Biçimlendirilmiş metin için, <xref:System.Windows.Media.PathGeometry> nesnesine dönüştürüldükten sonra başka ilginç kullanımlar oluşturabilirsiniz. Örneğin, video görüntüsünü, içinde görüntülenecek şekilde kırpabilirsiniz.  
  
 ![Metnin yol geometrisi içinde görüntülenen video](./media/drawing-formatted-text/video-displaying-text-path-geometry.png)
  
<a name="win32_migration"></a>   
## <a name="win32-migration"></a>Win32 geçişi  
 Çizim metni için <xref:System.Windows.Media.FormattedText> özellikleri Win32 DrawText işlevinin özelliklerine benzerdir. Win32 API geçiş yapan geliştiriciler için aşağıdaki tablo, Win32 DrawText bayraklarını ve [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]yaklaşık eşdeğerini listelemektedir.  
  
|DrawText bayrağı|WPF eşdeğeri|Notlar|  
|-------------------|--------------------|-----------|  
|DT_BOTTOM|<xref:System.Windows.Media.FormattedText.Height%2A>|Uygun bir Win32 DrawText ' y ' konumunu hesaplamak için <xref:System.Windows.Media.FormattedText.Height%2A> özelliğini kullanın.|  
|DT_CALCRECT|<xref:System.Windows.Media.FormattedText.Height%2A>, <xref:System.Windows.Media.FormattedText.Width%2A>|Çıkış dikdörtgenini hesaplamak için <xref:System.Windows.Media.FormattedText.Height%2A> ve <xref:System.Windows.Media.FormattedText.Width%2A> özelliklerini kullanın.|  
|DT_CENTER|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|<xref:System.Windows.Media.FormattedText.TextAlignment%2A> özelliğini <xref:System.Windows.TextAlignment.Center>olarak ayarlanan değerle kullanın.|  
|DT_EDITCONTROL|Yok.|Gerekli değildir. Boşluk genişliği ve son satır işleme, çerçeve düzenleme denetimindeki ile aynıdır.|  
|DT_END_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|<xref:System.Windows.Media.FormattedText.Trimming%2A> özelliğini <xref:System.Windows.TextTrimming.CharacterEllipsis>değeri ile kullanın.<br /><br /> DT_WORD_ELIPSIS uç üç nokta ile Win32 DT_END_ELLIPSIS almak için <xref:System.Windows.TextTrimming.WordEllipsis> kullanın — Bu durumda, karakter üç nokta yalnızca tek bir satıra sığmayan sözcüklerde oluşur.|  
|DT_EXPAND_TABS|Yok.|Gerekli değildir. Sekmeler, 8 dilden bağımsız karakterlerin yaklaşık genişliği olan her 4 EMS 'yi durdurmak üzere otomatik olarak genişletilir.|  
|DT_EXTERNALLEADING|Yok.|Gerekli değildir. Dış lider her zaman satır aralığına dahildir. Kullanıcı tanımlı satır aralığı oluşturmak için <xref:System.Windows.Media.FormattedText.LineHeight%2A> özelliğini kullanın.|  
|DT_HIDEPREFIX|Yok.|Desteklenmez. <xref:System.Windows.Media.FormattedText> nesnesini oluşturmadan önce dizeden ' & ' öğesini kaldırın.|  
|DT_LEFT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Bu, varsayılan metin hizalamasıdır. <xref:System.Windows.Media.FormattedText.TextAlignment%2A> özelliğini <xref:System.Windows.TextAlignment.Left>olarak ayarlanan değerle kullanın. (Yalnızca WPF)|  
|DT_MODIFYSTRING|Yok.|Desteklenmez.|  
|DT_NOCLIP|<xref:System.Windows.Media.Visual.VisualClip%2A>|Kırpma otomatik olarak gerçekleşmez. Metni kırpmak istiyorsanız <xref:System.Windows.Media.Visual.VisualClip%2A> özelliğini kullanın.|  
|DT_NOFULLWIDTHCHARBREAK|Yok.|Desteklenmez.|  
|DT_NOPREFIX|Yok.|Gerekli değildir. Dizelerdeki ' & ' karakteri her zaman normal karakter olarak değerlendirilir.|  
|DT_PATHELLIPSIS|Yok.|<xref:System.Windows.Media.FormattedText.Trimming%2A> özelliğini <xref:System.Windows.TextTrimming.WordEllipsis>değeri ile kullanın.|  
|DT_PREFIX|Yok.|Desteklenmez. Bir Hızlandırıcı tuşu veya bağlantı gibi metin için alt çizgi kullanmak istiyorsanız <xref:System.Windows.Media.FormattedText.SetTextDecorations%2A> yöntemini kullanın.|  
|DT_PREFIXONLY|Yok.|Desteklenmez.|  
|DT_RIGHT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|<xref:System.Windows.Media.FormattedText.TextAlignment%2A> özelliğini <xref:System.Windows.TextAlignment.Right>olarak ayarlanan değerle kullanın. (Yalnızca WPF)|  
|DT_RTLREADING|<xref:System.Windows.Media.FormattedText.FlowDirection%2A>|Ayarlama <xref:System.Windows.Media.FormattedText.FlowDirection%2A> özelliğini <xref:System.Windows.FlowDirection.RightToLeft>.|  
|DT_SINGLELINE|Yok.|Gerekli değildir. <xref:System.Windows.Media.FormattedText> nesneler, <xref:System.Windows.Media.FormattedText.MaxTextWidth%2A> özelliği ayarlanmamışsa veya metin bir satır başı/satır besleme (CR/LF) içermiyorsa, tek satırlık bir denetim gibi davranır.|  
|DT_TABSTOP|Yok.|Kullanıcı tanımlı sekme durağı konumları desteği yok.|  
|DT_TOP|<xref:System.Windows.Media.FormattedText.Height%2A>|Gerekli değildir. En üstteki gerekçe varsayılandır. Diğer dikey konumlandırma değerleri, uygun bir Win32 DrawText ' y ' konumunu hesaplamak için <xref:System.Windows.Media.FormattedText.Height%2A> özelliği kullanılarak tanımlanabilir.|  
|DT_VCENTER|<xref:System.Windows.Media.FormattedText.Height%2A>|Uygun bir Win32 DrawText ' y ' konumunu hesaplamak için <xref:System.Windows.Media.FormattedText.Height%2A> özelliğini kullanın.|  
|DT_WORDBREAK|Yok.|Gerekli değildir. Sözcük bölünmesi <xref:System.Windows.Media.FormattedText> nesneleriyle otomatik olarak gerçekleşir. Devre dışı bırakılamıyor.|  
|DT_WORD_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|<xref:System.Windows.Media.FormattedText.Trimming%2A> özelliğini <xref:System.Windows.TextTrimming.WordEllipsis>değeri ile kullanın.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.FormattedText>
- [WPF'deki Belgeler](documents-in-wpf.md)
- [WPF'de Tipografi](typography-in-wpf.md)
- [Anahatları Belirlenmiş Metin Oluşturma](how-to-create-outlined-text.md)
- [Nasıl yapılır: metin için PathGeometry animasyonu oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms743610(v=vs.100))
