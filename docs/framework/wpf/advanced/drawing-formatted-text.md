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
ms.openlocfilehash: 4cbf2a9ec9b742af3895f7c30b1a4dbbdbf5a635
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43804951"
---
# <a name="drawing-formatted-text"></a>Biçimlendirilmiş Metin Çizme
Bu konu, özelliklerine genel bir bakış sağlar. <xref:System.Windows.Media.FormattedText> nesne. Bu nesne, metin çizim için alt düzey denetim sağlar. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamalar.  
  
  
## <a name="technology-overview"></a>Teknoloji genel bakış  
 <xref:System.Windows.Media.FormattedText> Nesne, metindeki her karakter ayrı ayrı biçimlendirilebilir, çok satırlı metin çizme olanak tanır. Aşağıdaki örnek, çeşitli biçimlerde uygulanmış olan metni gösterir.  
  
 ![FormattedText nesnesi kullanılarak görüntülenen metin](../../../../docs/framework/wpf/advanced/media/formattedtext01.jpg "FormattedText01")  
FormattedText yöntemi kullanılarak görüntülenen metin  
  
> [!NOTE]
>  Geçiş bu geliştiriciler için [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] API'si, tabloda [Win32 geçiş](#win32_migration) bölümünde listeleri [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DrawText bayraklar ve yaklaşık eşdeğeri [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
### <a name="reasons-for-using-formatted-text"></a>Biçimlendirilmiş metin kullanma nedenleri  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ekrana metnin çizmek için birden fazla denetim içerir. Her denetim için farklı bir senaryo hedeflenen ve kendi listesi özellikler ve sınırlamalar vardır. Genel olarak, <xref:System.Windows.Controls.TextBlock> öğesi sınırlı metin desteği kısa bir cümle gibi gerekli olduğunda kullanılmalıdır bir [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. <xref:System.Windows.Controls.Label> en az metin desteği gerekli olduğunda kullanılabilir. Daha fazla bilgi için [WPF'deki Belgeler](../../../../docs/framework/wpf/advanced/documents-in-wpf.md).  
  
 <xref:System.Windows.Media.FormattedText> Nesne sağlayan biçimlendirme özellikleri daha büyük metin [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] metin denetimlerini ve metin dekoratif bir öğe olarak kullanmak istediğiniz durumlarda yararlı olabilir. Daha fazla bilgi için bkz. aşağıdaki bölümde [geometriye biçimlendirilmiş metin dönüştürme](#converting_formatted_text).  
  
 Ayrıca, <xref:System.Windows.Media.FormattedText> nesne, metin tabanlı oluşturmak için kullanışlıdır <xref:System.Windows.Media.DrawingVisual>-türetilmiş nesneler. <xref:System.Windows.Media.DrawingVisual> şekiller, görüntü veya metin işlemek için kullanılan bir basit çizim sınıfıdır. Daha fazla bilgi için [isabet sınaması örneği kullanarak Test isabet](https://go.microsoft.com/fwlink/?LinkID=159994).  
  
## <a name="using-the-formattedtext-object"></a>BiçimlendirilmişMetin nesnesi kullanma  
 Biçimlendirilmiş metin oluşturmak için arama <xref:System.Windows.Media.FormattedText.%23ctor%2A> oluşturmak için bir <xref:System.Windows.Media.FormattedText> nesne. İlk biçimlendirilmiş metin dizesi oluşturduktan sonra bir aralık stilleri biçimlendirme uygulayabilirsiniz.  
  
 Kullanım <xref:System.Windows.Media.FormattedText.MaxTextWidth%2A> metni belirli bir genişlikte kısıtlamak için özellik. Metnin belirtilen genişlik aşmamak için otomatik olarak kaydırılır. Kullanım <xref:System.Windows.Media.FormattedText.MaxTextHeight%2A> metni belirli bir yükseklikte kısıtlamak için özellik. "..." Belirtilen yüksekliğini aşıyor metin için üç nokta metni görüntüler.  
  
 ![FormattedText nesnesi kullanılarak görüntülenen metin](../../../../docs/framework/wpf/advanced/media/formattedtext02.png "FormattedText02")  
Sözcük kaydırma ve üç nokta gösteren metin  
  
 Bir veya daha fazla karakterle birden çok biçimlendirme stil uygulayabilirsiniz. Örneğin, her ikisi de çağırabilirsiniz <xref:System.Windows.Media.FormattedText.SetFontSize%2A> ve <xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A> ilk beş karakterlerini biçimini değiştirmek için yöntem.  
  
 Aşağıdaki kod örneği oluşturur bir <xref:System.Windows.Media.FormattedText> nesne ve sonra birkaç biçimlendirme stili metinler için geçerlidir.  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]  
  
### <a name="font-size-unit-of-measure"></a>Yazı tipi boyutu ölçü birimi  
 Diğer metin nesneleri ile [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamaları <xref:System.Windows.Media.FormattedText> nesne CİHAZDAN bağımsız piksel ölçü birimi olarak kullanır. Ancak, çoğu [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] uygulamaları ölçü birimi olarak noktalarını kullanır. Görüntü metni noktaları birimi kullanmak isterseniz [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamaları dönüştürmek için ihtiyacınız [!INCLUDE[TLA#tla_dipixel#plural](../../../../includes/tlasharptla-dipixelsharpplural-md.md)] noktalarına. Aşağıdaki kod örneği, bu dönüştürmeyi gerçekleştirecek gösterilmektedir.  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets2)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets2)]  
  
<a name="converting_formatted_text"></a>   
### <a name="converting-formatted-text-to-a-geometry"></a>Biçimlendirilmiş metin geometriye dönüştürme  
 Biçimlendirilmiş metin dönüştürebilirsiniz <xref:System.Windows.Media.Geometry> görsel metin ilginç diğer tür oluşturmanızı sağlayan nesneler. Örneğin, aşağıdakileri oluşturabilirsiniz bir <xref:System.Windows.Media.Geometry> nesne tabanlı bir metin dizesinin çerçevesinde.  
  
 ![Doğrusal gradyan fırçası kullanma metin anahat](../../../../docs/framework/wpf/advanced/media/outlinedtext02.jpg "OutlinedText02")  
Metin anahat doğrusal gradyan fırçası kullanma  
  
 Aşağıdaki örnekler, ilgi çekici görsel efektler vuruş dolgu ve dönüştürülen metin vurgulama değiştirerek oluşturmanın birkaç yolu gösterilmektedir.  
  
 ![Metin doldurup için farklı renklerde](../../../../docs/framework/wpf/advanced/media/outlinedtext03.jpg "OutlinedText03")  
Fırça darbesi ve dolgu farklı renkleri ayarlama örneği  
  
 ![Resim fırçası uygulandığı metinle](../../../../docs/framework/wpf/advanced/media/outlinedtext04.jpg "OutlinedText04")  
Bir resim fırçası uygulandığı örneği  
  
 ![Resim fırçası uygulandığı metinle](../../../../docs/framework/wpf/advanced/media/outlinedtext05.jpg "OutlinedText05")  
Fırça darbesi ve vurgulamaya uygulanan bir resim fırçası örneği  
  
 Ne zaman metin dönüştürülür bir <xref:System.Windows.Media.Geometry> nesnesi, artık bir derlemesidir karakter — metin dizesindeki karakterlerin değiştiremezsiniz. Ancak, çizme ve İşaretleme dolgu özelliklerini değiştirerek Dönüştürülen metin görünümünü etkileyebilir. Fırça darbesi Dönüştürülen metin anahattına gösterir. Dolgu Dönüştürülen metin özetini içindeki alan ifade eder. Daha fazla bilgi için [özetlenen metin oluşturma](../../../../docs/framework/wpf/advanced/how-to-create-outlined-text.md).  
  
 Biçimlendirilmiş metin de dönüştürebilirsiniz bir <xref:System.Windows.Media.PathGeometry> nesnesini ve nesne metni vurgulamak için kullanabilirsiniz. Örneğin, bir animasyonu uygulayabilirsiniz <xref:System.Windows.Media.PathGeometry> animasyon ana hat biçimlendirilmiş metnin izleyen nesnesi.  
  
 Aşağıdaki örnek, dönüştürülen biçimlendirilmiş metni gösterir. bir <xref:System.Windows.Media.PathGeometry> nesne. Animasyonlu bir elips işlenen metin vuruşlarının yolu izler.  
  
 ![Metin yolu geometri izleyen küre](../../../../docs/framework/wpf/advanced/media/textpathgeometry01.gif "TextPathGeometry01")  
Metin yolu geometri izleyen küre  
  
 Daha fazla bilgi için [nasıl yapılır: bir PathGeometry animasyon metin oluşturmak](https://msdn.microsoft.com/library/29f8051e-798a-463f-a926-a099a99e9c67).  
  
 Biçimlendirilmiş metin için ilgi çekici diğer kullanımlar için dönüştürüldükten sonra oluşturabilirsiniz bir <xref:System.Windows.Media.PathGeometry> nesne. Örneğin, içinde görüntülemek için video bölebilirsiniz.  
  
 ![Video görüntüleme metnin yol geometrisini](../../../../docs/framework/wpf/advanced/media/videotextdemo01.png "VideoTextDemo01")  
Metnin yolu geometrisini video görüntüleme  
  
<a name="win32_migration"></a>   
## <a name="win32-migration"></a>Win32 geçiş  
 Özelliklerinin <xref:System.Windows.Media.FormattedText> metin çizim özelliklerine benzer [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DrawText işlevi. Geçiş bu geliştiriciler için [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] API, aşağıdaki tabloda [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DrawText bayraklar ve yaklaşık eşdeğeri [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
|DrawText bayrağı|WPF eşdeğeri|Notlar|  
|-------------------|--------------------|-----------|  
|DT_BOTTOM|<xref:System.Windows.Media.FormattedText.Height%2A>|Kullanım <xref:System.Windows.Media.FormattedText.Height%2A> uygun bir işlem için özellik [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DrawText 'y' konumu.|  
|DT_CALCRECT|<xref:System.Windows.Media.FormattedText.Height%2A>, <xref:System.Windows.Media.FormattedText.Width%2A>|Kullanım <xref:System.Windows.Media.FormattedText.Height%2A> ve <xref:System.Windows.Media.FormattedText.Width%2A> çıktı dikdörtgeni hesaplamak için özellikler.|  
|DT_CENTER|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Kullanım <xref:System.Windows.Media.FormattedText.TextAlignment%2A> özelliği ayarlanan değer ile <xref:System.Windows.TextAlignment.Center>.|  
|DT_EDITCONTROL|Yok.|Gerekli değildir. Alan genişliği ve son satırı işleme framework olduğu gibi aynı Denetim Düzenle ' dir.|  
|DT_END_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|Kullanım <xref:System.Windows.Media.FormattedText.Trimming%2A> özellik değeriyle <xref:System.Windows.TextTrimming.CharacterEllipsis>.<br /><br /> Kullanım <xref:System.Windows.TextTrimming.WordEllipsis> almak için [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DT_END_ELLIPSIS DT_WORD_ELIPSIS ile son üç nokta — bu durumda, üç nokta karakteri yalnızca tek bir satıra sığmayacak sözcükler ortaya çıkar.|  
|DT_EXPAND_TABS|Yok.|Gerekli değildir. Sekmeleri otomatik olarak durdurur her 4 ems yaklaşık 8 dilden bağımsız karakter genişliği olduğu genişletilir.|  
|DT_EXTERNALLEADING|Yok.|Gerekli değildir. Başlıca dış her zaman satır aralığı içinde bulunur. Kullanım <xref:System.Windows.Media.FormattedText.LineHeight%2A> kullanıcı tanımlı satır aralığı oluşturmak için özellik.|  
|DT_HIDEPREFIX|Yok.|Desteklenmez. '&' Dizesinden oluşturmadan önce Kaldır <xref:System.Windows.Media.FormattedText> nesne.|  
|DT_LEFT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Varsayılan metin hizalamasını budur. Kullanım <xref:System.Windows.Media.FormattedText.TextAlignment%2A> özelliği ayarlanan değer ile <xref:System.Windows.TextAlignment.Left>. (Yalnızca WPF)|  
|DT_MODIFYSTRING|Yok.|Desteklenmez.|  
|DT_NOCLIP|<xref:System.Windows.Media.Visual.VisualClip%2A>|Kırpma otomatik olarak gerçekleştirilmez. Metni kırpmak isterseniz kullanın <xref:System.Windows.Media.Visual.VisualClip%2A> özelliği.|  
|DT_NOFULLWIDTHCHARBREAK|Yok.|Desteklenmez.|  
|DT_NOPREFIX|Yok.|Gerekli değildir. Dizelerdeki '&' karakteri, her zaman normal bir karakter olarak kabul edilir.|  
|DT_PATHELLIPSIS|Yok.|Kullanım <xref:System.Windows.Media.FormattedText.Trimming%2A> özellik değeriyle <xref:System.Windows.TextTrimming.WordEllipsis>.|  
|DT_PREFIX|Yok.|Desteklenmez. Bir kısayol tuşu ya da bağlantı gibi metin için alt çizgi kullanmak istiyorsanız kullanın <xref:System.Windows.Media.FormattedText.SetTextDecorations%2A> yöntemi.|  
|DT_PREFIXONLY|Yok.|Desteklenmez.|  
|DT_RIGHT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Kullanım <xref:System.Windows.Media.FormattedText.TextAlignment%2A> özelliği ayarlanan değer ile <xref:System.Windows.TextAlignment.Right>. (Yalnızca WPF)|  
|DT_RTLREADING|<xref:System.Windows.Media.FormattedText.FlowDirection%2A>|Ayarlama <xref:System.Windows.Media.FormattedText.FlowDirection%2A> özelliğini <xref:System.Windows.FlowDirection.RightToLeft>.|  
|DT_SINGLELINE|Yok.|Gerekli değildir. <xref:System.Windows.Media.FormattedText> nesneleri sürece bir tek satır denetimi gibi davranırlar ya da <xref:System.Windows.Media.FormattedText.MaxTextWidth%2A> özelliği veya satır başı/satır besleme (CR/LF) metin içeriyor.|  
|DT_TABSTOP|Yok.|Kullanıcı tanımlı sekme durağı pozisyonlar için destek yok.|  
|DT_TOP|<xref:System.Windows.Media.FormattedText.Height%2A>|Gerekli değildir. Üst gerekçe varsayılandır. Diğer dikey konumlandırma değerleri kullanılarak tanımlanabilir <xref:System.Windows.Media.FormattedText.Height%2A> uygun bir işlem için özellik [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DrawText 'y' konumu.|  
|DT_VCENTER|<xref:System.Windows.Media.FormattedText.Height%2A>|Kullanım <xref:System.Windows.Media.FormattedText.Height%2A> uygun bir işlem için özellik [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DrawText 'y' konumu.|  
|DT_WORDBREAK|Yok.|Gerekli değildir. Sözcük bölme ile otomatik olarak gerçekleşir <xref:System.Windows.Media.FormattedText> nesneleri. Bunu devre dışı bırakamaz.|  
|DT_WORD_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|Kullanım <xref:System.Windows.Media.FormattedText.Trimming%2A> özellik değeriyle <xref:System.Windows.TextTrimming.WordEllipsis>.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.FormattedText>  
 [WPF'deki Belgeler](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [WPF'de Tipografi](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)  
 [Anahatları Belirlenmiş Metin Oluşturma](../../../../docs/framework/wpf/advanced/how-to-create-outlined-text.md)  
 [Nasıl yapılır: PathGeometry animasyon metnini oluşturma](https://msdn.microsoft.com/library/29f8051e-798a-463f-a926-a099a99e9c67)
