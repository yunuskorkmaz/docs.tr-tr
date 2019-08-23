---
title: Windows Forms ve WPF Özelliğini Eşleme
ms.date: 03/30/2017
helpviewer_keywords:
- property mapping [WPF interoperability]
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- WindowsFormsHost element property mapping [WPF]
ms.assetid: 999d8298-9c04-467d-a453-86e41002057d
ms.openlocfilehash: ae4a97bc96a4f9e93942b4995f488c427fda3134
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917509"
---
# <a name="windows-forms-and-wpf-property-mapping"></a>Windows Forms ve WPF Özelliğini Eşleme
[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Ve[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] teknolojilerinin iki benzer ancak farklı özellik modeli vardır. *Özellik eşleme* iki mimaride birlikte çalışabilirliği destekler ve aşağıdaki özellikleri sağlar:  
  
- Konak ortamındaki ilgili özellik değişikliklerinin barındırılan denetim veya öğeye eşleşmesini kolaylaştırır.  
  
- En yaygın kullanılan özellikleri eşlemek için varsayılan işleme sağlar.  
  
- Varsayılan özelliklerin kolayca kaldırılmasına, geçersiz kılınmasını veya genişletilmesini sağlar.  
  
- Konaktaki Özellik değeri değişikliklerinin otomatik olarak algılanıp barındırılan denetime veya öğeye çevrilmesini sağlar.  
  
> [!NOTE]
> Özellik değiştirme olayları, barındırma denetimi veya öğe hiyerarşisinin yayılmaz. Özelliğin yerel değeri, doğrudan ayar, stiller, devralma, veri bağlama veya özelliğin değerini değiştiren diğer mekanizmalar nedeniyle değişmezse özellik çevirisi yapılmaz.  
  
 Özellik eşlemesine erişmek için, <xref:System.Windows.Forms.Integration.WindowsFormsHost> <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> öğesindeki özelliğini ve denetimindeki özelliğini kullanın. <xref:System.Windows.Forms.Integration.ElementHost> <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>  
  
## <a name="property-mapping-with-the-windowsformshost-element"></a>WindowsFormsHost öğesiyle Özellik eşlemesi  
 Öğesi <xref:System.Windows.Forms.Integration.WindowsFormsHost> , aşağıdaki çeviri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tablosunu kullanarak varsayılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] özellikleri eşdeğerlerine dönüştürür.  
  
|Windows Presentation Foundation barındırma|Windows Forms|Birlikte çalışabilirlik davranışı|  
|---------------------------------------------|-------------------|-----------------------------|  
|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.BackColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|Öğesi barındırılan denetimin <xref:System.Windows.Forms.Control.BackColor%2A> özelliğini ve <xref:System.Windows.Forms.Control.BackgroundImage%2A> barındırılan denetimin özelliğini ayarlar. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Eşleme, aşağıdaki kurallar kullanılarak gerçekleştirilir:<br /><br /> -Düz bir renkse, bu, dönüştürülür ve barındırılan denetimin <xref:System.Windows.Forms.Control.BackColor%2A> özelliğini ayarlamak için kullanılır. <xref:System.Windows.Controls.Control.Background%2A> Barındırılan denetim <xref:System.Windows.Forms.Control.BackColor%2A> özelliğin değerini devraldığı için, özelliğibarındırılandenetimdeayarlıdeğildir.<xref:System.Windows.Forms.Control.BackColor%2A> **Not:**  Barındırılan denetim saydamlığı desteklemiyor. Öğesine <xref:System.Windows.Forms.Control.BackColor%2A> atanan renk, bir alfa değeri 0xFF olan tamamen opak olmalıdır. <br /><br /> -Düz bir renk değilse <xref:System.Windows.Forms.Integration.WindowsFormsHost> , Denetim <xref:System.Windows.Controls.Control.Background%2A> özelliğinden bir bit eşlem oluşturur. <xref:System.Windows.Controls.Control.Background%2A> Denetim <xref:System.Windows.Forms.Integration.WindowsFormsHost> , bu bit eşlemi <xref:System.Windows.Forms.Control.BackgroundImage%2A> barındırılan denetimin özelliğine atar. Bu, saydamlığa benzeyen bir efekt sağlar. **Not:**  Bu davranışı geçersiz kılabilir veya <xref:System.Windows.Controls.Control.Background%2A> Özellik eşlemesini kaldırabilirsiniz.|  
|<xref:System.Windows.FrameworkElement.Cursor%2A>|<xref:System.Windows.Forms.Control.Cursor%2A>|Varsayılan eşleme yeniden atanmayan denetim, <xref:System.Windows.Forms.Integration.WindowsFormsHost> <xref:System.Windows.FrameworkElement.Cursor%2A> özelliği ayarlanmış bir üst öğe bulana kadar üst hiyerarşisinde gezir. Bu değer, en yakın karşılık gelen [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] imlece çevrilir.<br /><br /> <xref:System.Windows.FrameworkElement.ForceCursor%2A> Özelliği için varsayılan eşleme yeniden atanmadığından, geçiş işlemi olarak <xref:System.Windows.FrameworkElement.ForceCursor%2A> `true`ayarlanan ilk üst öğede duraklar.|  
|<xref:System.Windows.FrameworkElement.FlowDirection%2A><br /><br /> (<xref:System.Windows.FlowDirection?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.RightToLeft%2A><br /><br /> (<xref:System.Windows.Forms.RightToLeft?displayProperty=nameWithType>)|<xref:System.Windows.FlowDirection.LeftToRight>ile <xref:System.Windows.Forms.RightToLeft.No>eşlenir.<br /><br /> <xref:System.Windows.FlowDirection.RightToLeft>ile <xref:System.Windows.Forms.RightToLeft.Yes>eşlenir.<br /><br /> <xref:System.Windows.Forms.RightToLeft.Inherit>eşlenmedi.<br /><br /> <xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType>ile <xref:System.Windows.Forms.RightToLeft.Yes?displayProperty=nameWithType>eşlenir.|  
|<xref:System.Windows.Controls.Control.FontStyle%2A>|<xref:System.Drawing.Font.Style%2A>barındırılan denetimin<xref:System.Drawing.Font?displayProperty=nameWithType>|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Özellikler kümesi karşılık gelen <xref:System.Drawing.Font>öğesine çevrilir. Bu özelliklerden biri değiştiğinde yeni <xref:System.Drawing.Font> bir oluşturulur. İçin <xref:System.Windows.FontStyles.Normal%2A> :<xref:System.Drawing.FontStyle.Italic> devre dışı. Veya <xref:System.Windows.FontStyles.Italic%2A> için<xref:System.Windows.FontStyles.Oblique%2A> :<xref:System.Drawing.FontStyle.Italic> etkin.|  
|<xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Drawing.Font.Style%2A>barındırılan denetimin<xref:System.Drawing.Font?displayProperty=nameWithType>|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Özellikler kümesi karşılık gelen <xref:System.Drawing.Font>öğesine çevrilir. Bu özelliklerden biri değiştiğinde yeni <xref:System.Drawing.Font> bir oluşturulur. <xref:System.Windows.FontWeights.Black%2A> ,<xref:System.Windows.FontWeights.Heavy%2A> ,,<xref:System.Drawing.FontStyle.Bold> ,,, ,Veya<xref:System.Windows.FontWeights.UltraBold%2A>: için etkindir. <xref:System.Windows.FontWeights.SemiBold%2A> <xref:System.Windows.FontWeights.Bold%2A> <xref:System.Windows.FontWeights.DemiBold%2A> <xref:System.Windows.FontWeights.ExtraBold%2A> <xref:System.Windows.FontWeights.Medium%2A> <xref:System.Windows.FontWeights.ExtraLight%2A> ,<xref:System.Windows.FontWeights.Light%2A> ,,<xref:System.Windows.FontWeights.UltraLight%2A>,, Veya :<xref:System.Drawing.FontStyle.Bold> için devre dışı. <xref:System.Windows.FontWeights.Normal%2A> <xref:System.Windows.FontWeights.Regular%2A> <xref:System.Windows.FontWeights.Thin%2A>|  
|<xref:System.Windows.Controls.Control.FontFamily%2A><br /><br /> <xref:System.Windows.Controls.Control.FontSize%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStretch%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStyle%2A><br /><br /> <xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Windows.Forms.Control.Font%2A><br /><br /> (<xref:System.Drawing.Font?displayProperty=nameWithType>)|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Özellikler kümesi karşılık gelen <xref:System.Drawing.Font>öğesine çevrilir. Bu özelliklerden biri değiştiğinde yeni <xref:System.Drawing.Font> bir oluşturulur. Barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetim, yazı tipi boyutuna göre yeniden boyutlandırır.<br /><br /> İçindeki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yazı tipi boyutu, inç bir dokun altılık [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ve inç olarak bir inç olarak ifade edilir. Karşılık gelen dönüştürme:<br /><br /> [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]yazı tipi boyutu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] = yazı tipi boyutu * 72,0/96,0.|  
|<xref:System.Windows.Controls.Control.Foreground%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.ForeColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Foreground%2A> Özellik eşlemesi aşağıdaki kurallar kullanılarak gerçekleştirilir:<br /><br /> -İse ,için<xref:System.Windows.Forms.Control.ForeColor%2A>kullanın <xref:System.Windows.Media.SolidColorBrush.Color%2A>. <xref:System.Windows.Media.SolidColorBrush> <xref:System.Windows.Controls.Control.Foreground%2A><br />-İse <xref:System.Windows.Media.GradientStop> , için en<xref:System.Windows.Forms.Control.ForeColor%2A>düşük fark değeri ile rengini kullanın. <xref:System.Windows.Controls.Control.Foreground%2A> <xref:System.Windows.Media.GradientBrush><br />-Diğer <xref:System.Windows.Media.Brush> herhangi bir tür için değiştirilmeden <xref:System.Windows.Forms.Control.ForeColor%2A> bırakın. Bu, varsayılan olarak kullanılan anlamına gelir.|  
|<xref:System.Windows.UIElement.IsEnabled%2A>|<xref:System.Windows.Forms.Control.Enabled%2A>|Ayarlandığında, <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi barındırılan denetimdeki <xref:System.Windows.Forms.Control.Enabled%2A> özelliği ayarlar. <xref:System.Windows.UIElement.IsEnabled%2A>|  
|<xref:System.Windows.Controls.Control.Padding%2A>|<xref:System.Windows.Forms.Control.Padding%2A>|<xref:System.Windows.Thickness> Barındırılan <xref:System.Windows.Forms.Control.Padding%2A> denetimdekiözelliğin[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] tüm dört değeri aynı değere ayarlanır.<br /><br /> -Değerinden <xref:System.Int32.MaxValue> büyük değerler olarak <xref:System.Int32.MaxValue>ayarlanır.<br />-Değerinden küçük <xref:System.Int32.MinValue> değerler olarak <xref:System.Int32.MinValue>ayarlanır.|  
|<xref:System.Windows.UIElement.Visibility%2A>|<xref:System.Windows.Forms.Control.Visible%2A>|-   <xref:System.Windows.Visibility.Visible>ile <xref:System.Windows.Forms.Control.Visible%2A>  = eşlenir. `true` Barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetim görünür durumda. <xref:System.Windows.Forms.Control.Visible%2A> Barındırılan`false` denetimdeki özelliği açıkça ayarlamak önerilmez.<br />-   <xref:System.Windows.Visibility.Collapsed>veya <xref:System.Windows.Forms.Control.Visible%2A> ile`true` eşlenir.  =  `false` Barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetim çizilmez ve alanı daraltılmıştır.<br />-   <xref:System.Windows.Visibility.Hidden>: Barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetim mizanpajda boşluk kaplar, ancak görünür değildir. Bu durumda, <xref:System.Windows.Forms.Control.Visible%2A> özelliği olarak `true`ayarlanır. <xref:System.Windows.Forms.Control.Visible%2A> Barındırılan`false` denetimdeki özelliği açıkça ayarlamak önerilmez.|  
  
 Kapsayıcı öğelerinde Ekli Özellikler <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi tarafından tamamen desteklenir.  
  
 Daha fazla bilgi için bkz [. İzlenecek yol: WindowsFormsHost öğesi](walkthrough-mapping-properties-using-the-windowsformshost-element.md)kullanarak özellikleri eşleme.  
  
## <a name="updates-to-parent-properties"></a>Üst özelliklerde güncelleştirmeler  
 Çoğu üst özelliklerde yapılan değişiklikler barındırılan alt denetime yönelik bildirimlere neden olur. Aşağıdaki listede, değerleri değiştiğinde bildirimlere neden olmayan özellikler açıklanmaktadır.  
  
- <xref:System.Windows.Controls.Control.Background%2A>  
  
- <xref:System.Windows.FrameworkElement.Cursor%2A>  
  
- <xref:System.Windows.FrameworkElement.ForceCursor%2A>  
  
- <xref:System.Windows.UIElement.Visibility%2A>  
  
 Örneğin, <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesinin özelliğinin değerini değiştirirseniz, <xref:System.Windows.Forms.Control.BackColor%2A> barındırılan denetimin özelliği değişmez.  
  
## <a name="property-mapping-with-the-elementhost-control"></a>ElementHost denetimiyle Özellik eşleme  
 Aşağıdaki özellikler yerleşik değişiklik bildirimi sağlar. Bu özellikleri eşlerken <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> yöntemi çağırmayın:  
  
- AutoSize  
  
- Rengi  
  
- BackgroundImage  
  
- BackgroundImageLayout  
  
- Denetimin  
  
- Denetimin  
  
- ContextMenu  
  
- ContextMenuStrip  
  
- Oraya  
  
- Dock  
  
- Etkin  
  
- Yazý  
  
- ForeColor  
  
- Konum  
  
- Margin  
  
- Doldurmayı  
  
- Üst öğe  
  
- Bölge  
  
- RightToLeft  
  
- Boyut  
  
- Atan  
  
- Sekme durağı  
  
- Metin  
  
- Görünür  
  
 Denetim <xref:System.Windows.Forms.Integration.ElementHost> , aşağıdaki çeviri [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] tablosunu kullanarak varsayılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özellikleri eşdeğerlerine dönüştürür.  
  
 Daha fazla bilgi için bkz [. İzlenecek yol: ElementHost denetimini](walkthrough-mapping-properties-using-the-elementhost-control.md)kullanarak özellikleri eşleme.  
  
|Windows Forms barındırma|Windows Presentation Foundation|Birlikte çalışabilirlik davranışı|  
|---------------------------|-------------------------------------|-----------------------------|  
|<xref:System.Windows.Forms.Control.BackColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> <xref:System.Windows.Media.Brush?displayProperty=nameWithType>barındırılan öğede|Bu özelliği ayarlamak bir yeniden çizmeyi bir <xref:System.Windows.Media.ImageBrush>ile zorlar. <xref:System.Windows.Forms.Control.BackColor%2A> <xref:System.Windows.Media.ImageBrush> <xref:System.Windows.Forms.Integration.ElementHost> <xref:System.Windows.Forms.Control.BackgroundImageLayout%2A> <xref:System.Windows.Forms.Control.BackgroundImage%2A>Özelliği olarak `false` ayarlandıysa (varsayılan değer), bu,, özellikleri ve ekli boyama dahil olmak üzere denetimin görünümüne dayalıdır <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> ileridir.<br /><br /> Özelliğiolarak`true` ayarlandıysa,<xref:System.Windows.Forms.Control.BackColor%2A>üst öğenin,özelliklerininve<xref:System.Windows.Forms.Integration.ElementHost>ekli boyamadahilolmaküzeredenetiminüstününgörünümünedayalıdır<xref:System.Windows.Forms.Control.BackgroundImageLayout%2A> <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> <xref:System.Windows.Media.ImageBrush> <xref:System.Windows.Forms.Control.BackgroundImage%2A> ileridir.|  
|<xref:System.Windows.Forms.Control.BackgroundImage%2A><br /><br /> (<xref:System.Drawing.Image?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> <xref:System.Windows.Media.Brush?displayProperty=nameWithType>barındırılan öğede|Bu özelliğin ayarlanması, <xref:System.Windows.Forms.Control.BackColor%2A> eşleme için açıklanan davranışa neden olur.|  
|<xref:System.Windows.Forms.Control.BackgroundImageLayout%2A>|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> <xref:System.Windows.Media.Brush?displayProperty=nameWithType>barındırılan öğede|Bu özelliğin ayarlanması, <xref:System.Windows.Forms.Control.BackColor%2A> eşleme için açıklanan davranışa neden olur.|  
|<xref:System.Windows.Forms.Control.Cursor%2A><br /><br /> (<xref:System.Windows.Forms.Cursor?displayProperty=nameWithType>)|<xref:System.Windows.FrameworkElement.Cursor%2A><br /><br /> (<xref:System.Windows.Input.Cursor?displayProperty=nameWithType>)|Standart imleç, ilgili [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] standart imlece çevrilir. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Standart bir imleç değilse, varsayılan olarak atanır.|  
|<xref:System.Windows.Forms.Control.Enabled%2A>|<xref:System.Windows.UIElement.IsEnabled%2A>|Ayarlandığında, denetim barındırılan öğedeki <xref:System.Windows.UIElement.IsEnabled%2A> özelliğini ayarlar. <xref:System.Windows.Forms.Integration.ElementHost> <xref:System.Windows.Forms.Control.Enabled%2A>|  
|<xref:System.Windows.Forms.Control.Font%2A><br /><br /> (<xref:System.Drawing.Font?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.FontFamily%2A><br /><br /> <xref:System.Windows.Controls.Control.FontSize%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStretch%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStyle%2A><br /><br /> <xref:System.Windows.Controls.Control.FontWeight%2A>|Değer <xref:System.Windows.Forms.Control.Font%2A> , karşılık gelen bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yazı tipi özellikleri kümesine çevrilir.|  
|<xref:System.Drawing.Font.Bold%2A>|<xref:System.Windows.Controls.Control.FontWeight%2A>barındırılan öğede|<xref:System.Drawing.Font.Bold%2A> İse`true` ,<xref:System.Windows.FontWeights.Bold%2A>olarak ayarlanır<xref:System.Windows.Controls.Control.FontWeight%2A> .<br /><br /> <xref:System.Drawing.Font.Bold%2A> İse`false` ,<xref:System.Windows.FontWeights.Normal%2A>olarak ayarlanır<xref:System.Windows.Controls.Control.FontWeight%2A> .|  
|<xref:System.Drawing.Font.Italic%2A>|<xref:System.Windows.Controls.Control.FontStyle%2A>barındırılan öğede|<xref:System.Drawing.Font.Italic%2A> İse`true` ,<xref:System.Windows.FontStyles.Italic%2A>olarak ayarlanır<xref:System.Windows.Controls.Control.FontStyle%2A> .<br /><br /> <xref:System.Drawing.Font.Italic%2A> İse`false` ,<xref:System.Windows.FontStyles.Normal%2A>olarak ayarlanır<xref:System.Windows.Controls.Control.FontStyle%2A> .|  
|<xref:System.Drawing.Font.Strikeout%2A>|<xref:System.Windows.TextDecorations>barındırılan öğede|Yalnızca bir <xref:System.Windows.Controls.TextBlock> denetim barındırırken geçerlidir.|  
|<xref:System.Drawing.Font.Underline%2A>|<xref:System.Windows.TextDecorations>barındırılan öğede|Yalnızca bir <xref:System.Windows.Controls.TextBlock> denetim barındırırken geçerlidir.|  
|<xref:System.Windows.Forms.Control.RightToLeft%2A><br /><br /> (<xref:System.Windows.Forms.RightToLeft?displayProperty=nameWithType>)|<xref:System.Windows.FrameworkElement.FlowDirection%2A><br /><br /> (<xref:System.Windows.FlowDirection>)|<xref:System.Windows.Forms.RightToLeft.No>ile <xref:System.Windows.FlowDirection.LeftToRight>eşlenir.<br /><br /> <xref:System.Windows.Forms.RightToLeft.Yes>ile <xref:System.Windows.FlowDirection.RightToLeft>eşlenir.|  
|<xref:System.Windows.Forms.Control.Visible%2A>|<xref:System.Windows.UIElement.Visibility%2A>|Denetim, barındırılan öğedeki <xref:System.Windows.UIElement.Visibility%2A> özelliği aşağıdaki kuralları kullanarak ayarlar: <xref:System.Windows.Forms.Integration.ElementHost><br /><br /> -   <xref:System.Windows.Forms.Control.Visible%2A> = `true`ile <xref:System.Windows.Visibility.Visible>eşlenir.<br />-   <xref:System.Windows.Forms.Control.Visible%2A> = `false`ile <xref:System.Windows.Visibility.Hidden>eşlenir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [WPF ve Win32 Birlikte Çalışması](wpf-and-win32-interoperation.md)
- [WPF ve Windows Forms Birlikte Çalışması](wpf-and-windows-forms-interoperation.md)
- [İzlenecek yol: WindowsFormsHost öğesi kullanarak özellikleri eşleme](walkthrough-mapping-properties-using-the-windowsformshost-element.md)
- [İzlenecek yol: ElementHost denetimini kullanarak özellikleri eşleme](walkthrough-mapping-properties-using-the-elementhost-control.md)
