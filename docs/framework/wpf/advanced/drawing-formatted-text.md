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
ms.openlocfilehash: 3b410bcf609aca2cb201042247b8768f243ac93a
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629747"
---
# <a name="drawing-formatted-text"></a>Biçimlendirilmiş Metin Çizme
Bu konu, <xref:System.Windows.Media.FormattedText> nesnesinin özelliklerine genel bir bakış sağlar. Bu nesne, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamalarda metin çizmek için alt düzey denetim sağlar.  

## <a name="technology-overview"></a>Teknolojiye genel bakış  
 <xref:System.Windows.Media.FormattedText> Nesnesi, metin içindeki her karakterin ayrı ayrı biçimlendirilebileceği çok satırlı metin çizmenizi sağlar. Aşağıdaki örnek, birkaç biçimin uygulanmış olduğu metni gösterir.  
  
 ![FormattedText nesnesi kullanılarak görünen metin](./media/typography-in-wpf/text-formatted-linear-gradient.jpg)  
  
> [!NOTE]
>  [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] API 'den geçiş yapan geliştiriciler için, [Win32 geçiş](#win32_migration) bölümündeki tablo, [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DrawText bayraklarını ve içindeki [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]yaklaşık eşdeğerini listeler.  
  
### <a name="reasons-for-using-formatted-text"></a>Biçimli metin kullanma nedenleri  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ekrana metin çizme için birden çok denetim içerir. Her denetim farklı bir senaryoya yöneliktir ve kendi özellik ve kısıtlama listesine sahiptir. Genel <xref:System.Windows.Controls.TextBlock> olarak, öğesinde kısa bir cümle [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]gibi sınırlı metin desteği gerektiğinde öğesi kullanılmalıdır. <xref:System.Windows.Controls.Label>en az metin desteği gerekli olduğunda kullanılabilir. Daha fazla bilgi için bkz. [WPF Içindeki belgeler](documents-in-wpf.md).  
  
 <xref:System.Windows.Media.FormattedText> Nesnesi [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] metin denetimlerinden daha fazla metin biçimlendirme özelliği sağlar ve metni dekoratif bir öğe olarak kullanmak istediğiniz durumlarda yararlı olabilir. Daha fazla bilgi için, [biçimlendirilen metni bir geometriye dönüştürmenin](#converting_formatted_text)aşağıdaki bölümüne bakın.  
  
 Ayrıca, <xref:System.Windows.Media.FormattedText> nesnesi metin odaklı <xref:System.Windows.Media.DrawingVisual>türetilmiş nesneler oluşturmak için faydalıdır. <xref:System.Windows.Media.DrawingVisual>şekilleri, resimleri veya metni işlemek için kullanılan basit bir çizim sınıfıdır. Daha fazla bilgi için bkz. [Drawinggörselleri kullanarak Isabet testi örneği](https://go.microsoft.com/fwlink/?LinkID=159994).  
  
## <a name="using-the-formattedtext-object"></a>FormattedText nesnesini kullanma  
 Biçimlendirilen metin oluşturmak için, bir <xref:System.Windows.Media.FormattedText.%23ctor%2A> <xref:System.Windows.Media.FormattedText> nesnesi oluşturmak için oluşturucuyu çağırın. İlk biçimlendirilmiş metin dizesini oluşturduktan sonra bir dizi biçimlendirme stili uygulayabilirsiniz.  
  
 Metni belirli bir genişliğe kısıtlamak için özelliğinikullanın.<xref:System.Windows.Media.FormattedText.MaxTextWidth%2A> Metin, belirtilen genişliği aşmaktan kaçınmak için otomatik olarak kaydırılır. Metni belirli bir yüksekliğe kısıtlamak için özelliğinikullanın.<xref:System.Windows.Media.FormattedText.MaxTextHeight%2A> Metinde "..." üç nokta görüntülenir belirtilen yüksekliği aşan metin için.  
  
 ![WordWrap ve üç nokta ile görünen metin.](./media/drawing-formatted-text/formatted-text-wordwrap-ellipsis.png)    
  
 Bir veya daha fazla karaktere birden çok biçimlendirme stili uygulayabilirsiniz. Örneğin, metin içindeki ilk beş karakterin biçimlendirmesini <xref:System.Windows.Media.FormattedText.SetFontSize%2A> değiştirmek <xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A> için ve yöntemlerini çağırabilirsiniz.  
  
 Aşağıdaki kod örneği bir <xref:System.Windows.Media.FormattedText> nesnesi oluşturur ve sonra metne birkaç biçimlendirme stili uygular.  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]  
  
### <a name="font-size-unit-of-measure"></a>Yazı tipi boyutu ölçü birimi  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Uygulamalarda diğer metin nesnelerinde olduğu gibi <xref:System.Windows.Media.FormattedText> , nesne, ölçü birimi olarak cihazdan bağımsız pikseller kullanır. Ancak çoğu [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] uygulama, ölçü birimi olarak noktaları kullanır. Görüntüleme metnini [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamalarda punto birimlerinde kullanmak istiyorsanız, cihazdan bağımsız birimleri (birim başına 1/96th) noktalara dönüştürmeniz gerekir. Aşağıdaki kod örneği, bu dönüştürmenin nasıl gerçekleştirileceğini gösterir.  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets2)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets2)]  
  
<a name="converting_formatted_text"></a>   
### <a name="converting-formatted-text-to-a-geometry"></a>Biçimlendirilen metni bir geometriye dönüştürme  
 Biçimlendirilen metni <xref:System.Windows.Media.Geometry> nesnelerine dönüştürebilirsiniz, böylece görsel açıdan ilgi çekici metin türlerini oluşturabilirsiniz. Örneğin, bir metin dizesinin ana hattını <xref:System.Windows.Media.Geometry> temel alan bir nesne oluşturabilirsiniz.  
  
 ![Doğrusal gradyan fırçası kullanan metin ana hattı](./media/typography-in-wpf/text-outline-linear-gradient.jpg)    
  
 Aşağıdaki örneklerde, dönüştürülmüş metnin vuruş, dolgusu ve vurgulanmasını değiştirerek ilginç görsel etkiler oluşturmanın birkaç yolu gösterilmektedir.  
  
 ![Fill ve Stroke için farklı renkler içeren metin](./media/typography-in-wpf/fill-stroke-text-effect.jpg)  
  
 ![Görüntüye resim fırçası uygulanmış metin](./media/typography-in-wpf/image-brush-application.jpg)
  
 ![Kontura ve vurgulamaya uygulanan resim fırçasının bulunduğu metin](./media/typography-in-wpf/image-brush-text-application.jpg)
  
 Metin bir <xref:System.Windows.Media.Geometry> nesneye dönüştürüldüğünde, artık bir karakter koleksiyonu değildir; metin dizesindeki karakterleri değiştiremezsiniz. Ancak, kontur ve Fill özelliklerini değiştirerek dönüştürülen metnin görünümünü etkileyebilirsiniz. Vuruş, dönüştürülen metnin ana hattını ifade eder; Fill, dönüştürülen metnin ana hattının içindeki alanı ifade eder. Daha fazla bilgi için bkz. [anahatları belirlenmiş metin oluşturma](how-to-create-outlined-text.md).  
  
 Ayrıca, biçimlendirilen metni bir <xref:System.Windows.Media.PathGeometry> nesneye dönüştürebilir ve nesneyi metin vurgulamak için kullanabilirsiniz. Örneğin, animasyonun biçimli metnin ana hattını takip edebilmesi için <xref:System.Windows.Media.PathGeometry> nesnesine bir animasyon uygulayabilirsiniz.  
  
 Aşağıdaki örnek, bir <xref:System.Windows.Media.PathGeometry> nesnesine dönüştürülen biçimlendirilmiş metni gösterir. Hareketli bir elips, işlenen metnin vuruşlarının yolunu izler.  
  
 ![Metnin yol geometrisini izleyen Sphere](./media/drawing-formatted-text/sphere-following-geometry-path.gif)  
Metnin yol geometrisini izleyen Sphere  
  
 Daha fazla bilgi için [nasıl yapılır: Metin](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms743610(v=vs.100))Için bir PathGeometry Animasyonu oluşturun.  
  
 Biçimlendirilmiş metin için, bir <xref:System.Windows.Media.PathGeometry> nesnesine dönüştürüldükten sonra başka ilginç kullanımlar oluşturabilirsiniz. Örneğin, video görüntüsünü, içinde görüntülenecek şekilde kırpabilirsiniz.  
  
 ![Metnin yol geometrisi içinde görüntülenen video](./media/drawing-formatted-text/video-displaying-text-path-geometry.png)
  
<a name="win32_migration"></a>   
## <a name="win32-migration"></a>Win32 geçişi  
 Çizim metni <xref:System.Windows.Media.FormattedText> için özellikleri, [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DrawText işlevinin özelliklerine benzerdir. [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] API 'den geçiş yapan geliştiriciler için aşağıdaki tablo, içindeki [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]DrawText bayraklarını ve yaklaşık eşdeğerini listelemektedir.  
  
|DrawText bayrağı|WPF eşdeğeri|Notlar|  
|-------------------|--------------------|-----------|  
|DT_BOTTOM|<xref:System.Windows.Media.FormattedText.Height%2A>|<xref:System.Windows.Media.FormattedText.Height%2A> Uygun[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] bir DrawText ' y ' konumunu hesaplamak için özelliğini kullanın.|  
|DT_CALCRECT|<xref:System.Windows.Media.FormattedText.Height%2A>, <xref:System.Windows.Media.FormattedText.Width%2A>|Çıkış dikdörtgenini hesaplamak <xref:System.Windows.Media.FormattedText.Width%2A> için veözelliklerinikullanın.<xref:System.Windows.Media.FormattedText.Height%2A>|  
|DT_CENTER|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|<xref:System.Windows.Media.FormattedText.TextAlignment%2A> Özelliğini olarak<xref:System.Windows.TextAlignment.Center>ayarlanan değerle kullanın.|  
|DT_EDITCONTROL|Yok.|Gerekli değildir. Boşluk genişliği ve son satır işleme, çerçeve düzenleme denetimindeki ile aynıdır.|  
|DT_END_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|<xref:System.Windows.Media.FormattedText.Trimming%2A> Özelliğini değeriyle<xref:System.Windows.TextTrimming.CharacterEllipsis>kullanın.<br /><br /> DT_WORD_ELIPSIS <xref:System.Windows.TextTrimming.WordEllipsis> End üç [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] nokta ile DT_END_ELLIPSIS almak için kullanın — Bu durumda, karakter üç nokta yalnızca tek bir satıra sığmayan sözcüklerde oluşur.|  
|DT_EXPAND_TABS|Yok.|Gerekli değildir. Sekmeler, 8 dilden bağımsız karakterlerin yaklaşık genişliği olan her 4 EMS 'yi durdurmak üzere otomatik olarak genişletilir.|  
|DT_EXTERNALLEADING|None|Gerekli değildir. Dış lider her zaman satır aralığına dahildir. Kullanıcı tanımlı satır aralığı oluşturmak için özelliğinikullanın.<xref:System.Windows.Media.FormattedText.LineHeight%2A>|  
|DT_HIDEPREFIX|Yok.|Desteklenmez. <xref:System.Windows.Media.FormattedText> Nesneyi oluşturmadan önce dizeden ' & ' öğesini kaldırın.|  
|DT_LEFT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Bu, varsayılan metin hizalamasıdır. <xref:System.Windows.Media.FormattedText.TextAlignment%2A> Özelliğini olarak<xref:System.Windows.TextAlignment.Left>ayarlanan değerle kullanın. (Yalnızca WPF)|  
|DT_MODIFYSTRING|None|Desteklenmez.|  
|DT_NOCLIP|<xref:System.Windows.Media.Visual.VisualClip%2A>|Kırpma otomatik olarak gerçekleşmez. Metni kırpmak istiyorsanız <xref:System.Windows.Media.Visual.VisualClip%2A> özelliğini kullanın.|  
|DT_NOFULLWIDTHCHARBREAK|None|Desteklenmez.|  
|DT_NOPREFIX|Yok.|Gerekli değildir. Dizelerdeki ' & ' karakteri her zaman normal karakter olarak değerlendirilir.|  
|DT_PATHELLIPSIS|None|<xref:System.Windows.Media.FormattedText.Trimming%2A> Özelliğini değeriyle<xref:System.Windows.TextTrimming.WordEllipsis>kullanın.|  
|DT_PREFIX|Yok.|Desteklenmez. Bir Hızlandırıcı tuşu veya bağlantı gibi metin için alt çizgi kullanmak istiyorsanız <xref:System.Windows.Media.FormattedText.SetTextDecorations%2A> yöntemini kullanın.|  
|DT_PREFIXONLY|Yok.|Desteklenmez.|  
|DT_RIGHT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|<xref:System.Windows.Media.FormattedText.TextAlignment%2A> Özelliğini olarak<xref:System.Windows.TextAlignment.Right>ayarlanan değerle kullanın. (Yalnızca WPF)|  
|DT_RTLREADING|<xref:System.Windows.Media.FormattedText.FlowDirection%2A>|Ayarlama <xref:System.Windows.Media.FormattedText.FlowDirection%2A> özelliğini <xref:System.Windows.FlowDirection.RightToLeft>.|  
|DT_SINGLELINE|Yok.|Gerekli değildir. <xref:System.Windows.Media.FormattedText><xref:System.Windows.Media.FormattedText.MaxTextWidth%2A> özellik ayarlanmamışsa ya da metin bir satır başı/satır besleme (CR/LF) içermiyorsa, nesneler tek satırlık bir denetim gibi davranır.|  
|DT_TABSTOP|Yok.|Kullanıcı tanımlı sekme durağı konumları desteği yok.|  
|DT_TOP|<xref:System.Windows.Media.FormattedText.Height%2A>|Gerekli değildir. En üstteki gerekçe varsayılandır. Diğer dikey konumlandırma değerleri, <xref:System.Windows.Media.FormattedText.Height%2A> uygun [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] bir DrawText ' y ' konumunu hesaplamak için özelliği kullanılarak tanımlanabilir.|  
|DT_VCENTER|<xref:System.Windows.Media.FormattedText.Height%2A>|<xref:System.Windows.Media.FormattedText.Height%2A> Uygun[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] bir DrawText ' y ' konumunu hesaplamak için özelliğini kullanın.|  
|DT_WORDBREAK|Yok.|Gerekli değildir. Sözcük bölünmesi, <xref:System.Windows.Media.FormattedText> nesnelerle otomatik olarak gerçekleşir. Devre dışı bırakılamıyor.|  
|DT_WORD_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|<xref:System.Windows.Media.FormattedText.Trimming%2A> Özelliğini değeriyle<xref:System.Windows.TextTrimming.WordEllipsis>kullanın.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.FormattedText>
- [WPF'deki Belgeler](documents-in-wpf.md)
- [WPF'de Tipografi](typography-in-wpf.md)
- [Anahatları Belirlenmiş Metin Oluşturma](how-to-create-outlined-text.md)
- [Nasıl yapılır: Metin için bir PathGeometry Animasyonu oluşturun](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms743610(v=vs.100))
