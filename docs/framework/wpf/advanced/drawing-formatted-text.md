---
title: "Biçimlendirilmiş Metin Çizme"
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
- text [WPF]
- typography [WPF], drawing formatted text
- formatted text [WPF]
- drawing [WPF], formatted text
ms.assetid: b1d851c1-331c-4814-9964-6fe769db6f1f
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d1d85e85079504e28a5b0ae78dc8be3a4b928ea3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="drawing-formatted-text"></a>Biçimlendirilmiş Metin Çizme
Bu konuda özelliklerini genel bakış sağlar <xref:System.Windows.Media.FormattedText> nesnesi. Bu nesne, metin çizim için alt düzey denetim sağlar. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamalar.  
  
  
## <a name="technology-overview"></a>Teknoloji genel bakış  
 <xref:System.Windows.Media.FormattedText> Nesnesi, metindeki her karakter ayrı ayrı biçimlendirilebilir çok satırlı metin Çiz olanak tanır. Aşağıdaki örnek, çeşitli biçimlerde uygulanmış olan metin gösterir.  
  
 ![FormattedText nesnesi kullanılarak görüntülenen metin](../../../../docs/framework/wpf/advanced/media/formattedtext01.jpg "FormattedText01")  
FormattedText metodu kullanılarak görüntülenen metin  
  
> [!NOTE]
>  Geçiş bu geliştiriciler için [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] API, tabloda [Win32 geçiş](#win32_migration) bölümünde listeleri [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DrawText bayrakları ve içindeki yaklaşık eşdeğerleri [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
### <a name="reasons-for-using-formatted-text"></a>Biçimlendirilmiş metin kullanma nedenleri  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ekrana metin çizme için birden çok denetim içerir. Her denetim için farklı bir senaryo hedeflenen ve kendi listesi özellikleri ve sınırlamaları vardır. Genel olarak, <xref:System.Windows.Controls.TextBlock> öğesi sınırlı metin desteği içindeki kısa tümce gibi gerekli olduğunda kullanılmalıdır bir [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. <xref:System.Windows.Controls.Label>en az metin desteği gerekli olduğunda kullanılabilir. Daha fazla bilgi için bkz: [WPF belgelerde](../../../../docs/framework/wpf/advanced/documents-in-wpf.md).  
  
 <xref:System.Windows.Media.FormattedText> Nesnesi sağlar biçimlendirme özellikleri daha büyük metin [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] metin denetimleri ve metin dekoratif bir öğe olarak kullanmak istediğiniz durumlarda yararlı olabilir. Daha fazla bilgi için aşağıdaki bölüme bakın [biçimlendirilmiş metni geometriye dönüştürme](#converting_formatted_text).  
  
 Ayrıca, <xref:System.Windows.Media.FormattedText> nesnesidir metin odaklı oluşturmak için yararlı <xref:System.Windows.Media.DrawingVisual>-türetilmiş nesneleri. <xref:System.Windows.Media.DrawingVisual>Şekil, görüntü veya metin işlemek için kullanılan bir basit çizim sınıfıdır. Daha fazla bilgi için bkz: [Test kullanarak isabet sınaması örneği isabet](http://go.microsoft.com/fwlink/?LinkID=159994).  
  
## <a name="using-the-formattedtext-object"></a>BiçimlendirilmişMetin nesnesi kullanma  
 Biçimlendirilmiş metin oluşturmak için arama <xref:System.Windows.Media.FormattedText.%23ctor%2A> Oluşturucusu oluşturmak için bir <xref:System.Windows.Media.FormattedText> nesnesi. İlk biçimlendirilmiş metin dizesi oluşturduktan sonra bir aralık stilleri biçimlendirme uygulayabilirsiniz.  
  
 Kullanım <xref:System.Windows.Media.FormattedText.MaxTextWidth%2A> metni belirli bir genişliğe sınırlamak için özellik. Metnin belirtilen genişliği aşmasını önlemek için otomatik olarak kaydırılır. Kullanım <xref:System.Windows.Media.FormattedText.MaxTextHeight%2A> belirli bir yükseklikte metni kısıtlamak için özelliği. Metni "..." belirtilen yüksekliği aştığı metin için üç nokta görüntüler.  
  
 ![FormattedText nesnesi kullanılarak görüntülenen metin](../../../../docs/framework/wpf/advanced/media/formattedtext02.png "FormattedText02")  
Sözcük kaydırma ve üç nokta gösteren metin  
  
 Bir veya daha fazla karakterle birden çok biçimlendirme stilleri uygulayabilirsiniz. Örneğin, her ikisini çağırabilirsiniz <xref:System.Windows.Media.FormattedText.SetFontSize%2A> ve <xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A> metindeki ilk beş karakter biçimlendirme değiştirmek için yöntemleri.  
  
 Aşağıdaki kod örneği oluşturur bir <xref:System.Windows.Media.FormattedText> nesne ve birkaç biçimlendirme stili metne uygular.  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]  
  
### <a name="font-size-unit-of-measure"></a>Yazı tipi boyutu ölçü  
 Diğer metin nesneleri ile [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamaları <xref:System.Windows.Media.FormattedText> nesnesi aygıttan bağımsız piksel ölçü birimi kullanır. Bununla birlikte, çoğu [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] uygulamaları noktaları ölçü birimi kullanır. Puan birimlerindeki görüntüleme metni kullanmak isteyip istemediğinizi [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamaları dönüştürmek için ihtiyacınız [!INCLUDE[TLA#tla_dipixel#plural](../../../../includes/tlasharptla-dipixelsharpplural-md.md)] noktalarına. Aşağıdaki kod örneği, bu dönüştürme gerçekleştirmek gösterilmiştir.  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets2)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets2)]  
  
<a name="converting_formatted_text"></a>   
### <a name="converting-formatted-text-to-a-geometry"></a>Biçimlendirilmiş metin geometriye dönüştürme  
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
  
 Ne zaman metin dönüştürülür için bir <xref:System.Windows.Media.Geometry> nesne olduğu artık karakterler koleksiyonu — metin dizesindeki karakterleri değiştiremezsiniz. Ancak, vuruş ve dolgu özelliklerini değiştirerek Dönüştürülen metin görünümünü etkileyebilir. Vuruşun Dönüştürülen metin anahattına gösterir; Dolgu alanının içini Dönüştürülen metin anahat ifade eder. Daha fazla bilgi için bkz: [özetlenen metin Oluştur](../../../../docs/framework/wpf/advanced/how-to-create-outlined-text.md).  
  
 Biçimlendirilmiş metin da dönüştürebilirsiniz bir <xref:System.Windows.Media.PathGeometry> nesne ve nesneyi metni vurgulamak için kullanabilirsiniz. Örneğin, bir animasyon uygulayabilir <xref:System.Windows.Media.PathGeometry> böylece animasyon biçimlendirilmiş metin anahat izleyen nesne.  
  
 Dönüştürülen biçimlendirilmiş metin aşağıdaki örnekte bir <xref:System.Windows.Media.PathGeometry> nesnesi. Animasyonlu bir elips işlenmiş metin vuruşları yol izler.  
  
 ![Metnin yol geometri izleyen küre](../../../../docs/framework/wpf/advanced/media/textpathgeometry01.gif "TextPathGeometry01")  
Metnin yol geometri izleyen küre  
  
 Daha fazla bilgi için bkz: [nasıl yapılır: metin için PathGeometry animasyon oluşturmak](http://msdn.microsoft.com/en-us/29f8051e-798a-463f-a926-a099a99e9c67).  
  
 İçin dönüştürüldükten sonra biçimlendirilmiş metin ilginç başka amaçlarla oluşturabileceğiniz bir <xref:System.Windows.Media.PathGeometry> nesnesi. Örneğin, içinde görüntülemek için video bölebilirsiniz.  
  
 ![Metnin yol geometri video görüntüleme](../../../../docs/framework/wpf/advanced/media/videotextdemo01.png "VideoTextDemo01")  
Metnin yol geometri video görüntüleme  
  
<a name="win32_migration"></a>   
## <a name="win32-migration"></a>Win32 geçiş  
 Özelliklerini <xref:System.Windows.Media.FormattedText> metin çizim özelliklerine benzer [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DrawText işlevi. Geçiş bu geliştiriciler için [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] API, aşağıdaki tabloda [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DrawText bayrakları ve içindeki yaklaşık eşdeğerleri [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
|DrawText bayrağı|WPF eşdeğer|Notlar|  
|-------------------|--------------------|-----------|  
|DT_BOTTOM|<xref:System.Windows.Media.FormattedText.Height%2A>|Kullanım <xref:System.Windows.Media.FormattedText.Height%2A> uygun bir işlem için özellik [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DrawText 'y' konumu.|  
|DT_CALCRECT|<xref:System.Windows.Media.FormattedText.Height%2A>, <xref:System.Windows.Media.FormattedText.Width%2A>|Kullanım <xref:System.Windows.Media.FormattedText.Height%2A> ve <xref:System.Windows.Media.FormattedText.Width%2A> çıktı dikdörtgeni hesaplamak için özellikler.|  
|DT_CENTER|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Kullanım <xref:System.Windows.Media.FormattedText.TextAlignment%2A> ayarlamak değere sahip özelliği <xref:System.Windows.TextAlignment.Center>.|  
|DT_EDITCONTROL|Yok.|Gerekli değildir. Alanı genişlik ve son çizgi işleme framework ile aynı düzenleme denetimindeki ile aynıdır.|  
|F:SYSTEM.WİNDOWS.TEXTTRİMMİNG.WORDELLİPSİS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|Kullanım <xref:System.Windows.Media.FormattedText.Trimming%2A> değere sahip özelliği <xref:System.Windows.TextTrimming.CharacterEllipsis>.<br /><br /> Kullanım <xref:System.Windows.TextTrimming.WordEllipsis> almak için [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] f:System.Windows.TextTrimming.WordEllipsis DT_WORD_ELIPSIS ile son üç nokta — bu durumda, üç nokta karakteri yalnızca tek bir satırda sığmayacak sözcükler ortaya çıkar.|  
|DT_EXPAND_TABS|Yok.|Gerekli değildir. Sekmeleri otomatik olarak durdurur için her 4 ems yaklaşık 8 dilden bağımsız karakter genişliğini olduğu genişletilir.|  
|DT_EXTERNALLEADING|Yok.|Gerekli değildir. Dış başında her zaman satır aralığına dahil edilir. Kullanım <xref:System.Windows.Media.FormattedText.LineHeight%2A> kullanıcı tanımlı satır aralığı oluşturmak için özellik.|  
|DT_HIDEPREFIX|Yok.|Desteklenmez. '&' Dize oluşturmadan önce Kaldır <xref:System.Windows.Media.FormattedText> nesnesi.|  
|DT_LEFT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Varsayılan metin hizalamasını budur. Kullanım <xref:System.Windows.Media.FormattedText.TextAlignment%2A> ayarlamak değere sahip özelliği <xref:System.Windows.TextAlignment.Left>. (Yalnızca WPF)|  
|DT_MODIFYSTRING|Yok.|Desteklenmez.|  
|DT_NOCLIP|<xref:System.Windows.Media.Visual.VisualClip%2A>|Kırpma otomatik olarak gerçekleştirilmez. Küçük metin istiyorsanız kullanın <xref:System.Windows.Media.Visual.VisualClip%2A> özelliği.|  
|DT_NOFULLWIDTHCHARBREAK|Yok.|Desteklenmez.|  
|DT_NOPREFIX|Yok.|Gerekli değildir. Dizelerde '&' karakteri her zaman normal karakter olarak kabul edilir.|  
|DT_PATHELLIPSIS|Yok.|Kullanım <xref:System.Windows.Media.FormattedText.Trimming%2A> değere sahip özelliği <xref:System.Windows.TextTrimming.WordEllipsis>.|  
|DT_PREFIX|Yok.|Desteklenmez. Bir kısayol tuşu veya bağlantı gibi bir metin için alt çizgi kullanmak istiyorsanız kullanın <xref:System.Windows.Media.FormattedText.SetTextDecorations%2A> yöntemi.|  
|DT_PREFIXONLY|Yok.|Desteklenmez.|  
|DT_RIGHT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Kullanım <xref:System.Windows.Media.FormattedText.TextAlignment%2A> ayarlamak değere sahip özelliği <xref:System.Windows.TextAlignment.Right>. (Yalnızca WPF)|  
|DT_RTLREADING|<xref:System.Windows.Media.FormattedText.FlowDirection%2A>|Ayarlama <xref:System.Windows.Media.FormattedText.FlowDirection%2A> özelliğine <xref:System.Windows.FlowDirection.RightToLeft>.|  
|DT_SINGLELINE|Yok.|Gerekli değildir. <xref:System.Windows.Media.FormattedText>nesneleri sürece tek satır denetimi gibi davranır ya da <xref:System.Windows.Media.FormattedText.MaxTextWidth%2A> özelliği ayarlanmış veya satır başı/satır besleme (CR/LF) metni içerir.|  
|DT_TABSTOP|Yok.|Kullanıcı tanımlı sekme Dur konumlar için destek yok.|  
|DT_TOP|<xref:System.Windows.Media.FormattedText.Height%2A>|Gerekli değildir. Üst gerekçe varsayılandır. Diğer dikey konumlandırma değerleri kullanılarak tanımlanabilir <xref:System.Windows.Media.FormattedText.Height%2A> uygun bir işlem için özellik [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DrawText 'y' konumu.|  
|DT_VCENTER|<xref:System.Windows.Media.FormattedText.Height%2A>|Kullanım <xref:System.Windows.Media.FormattedText.Height%2A> uygun bir işlem için özellik [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DrawText 'y' konumu.|  
|DT_WORDBREAK|Yok.|Gerekli değildir. Sözcük bölünmesi ile otomatik olarak gerçekleşir <xref:System.Windows.Media.FormattedText> nesneleri. Bunu devre dışı bırakamaz.|  
|DT_WORD_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|Kullanım <xref:System.Windows.Media.FormattedText.Trimming%2A> değere sahip özelliği <xref:System.Windows.TextTrimming.WordEllipsis>.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.FormattedText>  
 [WPF'deki Belgeler](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [WPF'de Tipografi](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)  
 [Anahatları Belirlenmiş Metin Oluşturma](../../../../docs/framework/wpf/advanced/how-to-create-outlined-text.md)  
 [Nasıl yapılır: metin için PathGeometry Animasyonu oluşturma](http://msdn.microsoft.com/en-us/29f8051e-798a-463f-a926-a099a99e9c67)
