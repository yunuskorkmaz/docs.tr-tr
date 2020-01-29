---
title: Windows Forms ve WPF Özelliğini Eşleme
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- property mapping [WPF interoperability]
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- WindowsFormsHost element property mapping [WPF]
ms.assetid: 999d8298-9c04-467d-a453-86e41002057d
ms.openlocfilehash: 07e58f87d886212426e25be83f988037549ab642
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735241"
---
# <a name="windows-forms-and-wpf-property-mapping"></a>Windows Forms ve WPF Özelliğini Eşleme
[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] teknolojilerinin iki benzer ancak farklı özellik modeli vardır. *Özellik eşleme* iki mimaride birlikte çalışabilirliği destekler ve aşağıdaki özellikleri sağlar:  
  
- Konak ortamındaki ilgili özellik değişikliklerinin barındırılan denetim veya öğeye eşleşmesini kolaylaştırır.  
  
- En yaygın kullanılan özellikleri eşlemek için varsayılan işleme sağlar.  
  
- Varsayılan özelliklerin kolayca kaldırılmasına, geçersiz kılınmasını veya genişletilmesini sağlar.  
  
- Konaktaki Özellik değeri değişikliklerinin otomatik olarak algılanıp barındırılan denetime veya öğeye çevrilmesini sağlar.  
  
> [!NOTE]
> Özellik değiştirme olayları, barındırma denetimi veya öğe hiyerarşisinin yayılmaz. Özelliğin yerel değeri, doğrudan ayar, stiller, devralma, veri bağlama veya özelliğin değerini değiştiren diğer mekanizmalar nedeniyle değişmezse özellik çevirisi yapılmaz.  
  
 Özellik eşlemesine erişmek için <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesindeki <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> özelliğini ve <xref:System.Windows.Forms.Integration.ElementHost> denetimindeki <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> özelliğini kullanın.  
  
## <a name="property-mapping-with-the-windowsformshost-element"></a>WindowsFormsHost öğesiyle Özellik eşlemesi  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi, aşağıdaki çeviri tablosunu kullanarak varsayılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özelliklerini [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] eşdeğerlerine çevirir.  
  
|Windows Presentation Foundation barındırma|Windows Forms|Birlikte çalışabilirlik davranışı|  
|---------------------------------------------|-------------------|-----------------------------|  
|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.BackColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi barındırılan denetimin <xref:System.Windows.Forms.Control.BackColor%2A> özelliğini ve barındırılan denetimin <xref:System.Windows.Forms.Control.BackgroundImage%2A> özelliğini ayarlar. Eşleme, aşağıdaki kurallar kullanılarak gerçekleştirilir:<br /><br /> -<xref:System.Windows.Controls.Control.Background%2A> düz bir renkse, bu, dönüştürülür ve barındırılan denetimin <xref:System.Windows.Forms.Control.BackColor%2A> özelliğini ayarlamak için kullanılır. Barındırılan denetim <xref:System.Windows.Forms.Control.BackColor%2A> özelliğinin değerini devraldığı için, <xref:System.Windows.Forms.Control.BackColor%2A> özelliği barındırılan denetimde ayarlı değildir. **Note:**  Barındırılan denetim saydamlığı desteklemiyor. <xref:System.Windows.Forms.Control.BackColor%2A> atanan renk, bir alfa değeri 0xFF olan tam opak olmalıdır. <br /><br /> -<xref:System.Windows.Controls.Control.Background%2A> düz bir renk değilse, <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimi <xref:System.Windows.Controls.Control.Background%2A> özelliğinden bir bit eşlem oluşturur. <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimi bu bit eşlemi barındırılan denetimin <xref:System.Windows.Forms.Control.BackgroundImage%2A> özelliğine atar. Bu, saydamlığa benzeyen bir efekt sağlar. **Note:**  Bu davranışı geçersiz kılabilir veya <xref:System.Windows.Controls.Control.Background%2A> Özellik eşlemesini kaldırabilirsiniz.|  
|<xref:System.Windows.FrameworkElement.Cursor%2A>|<xref:System.Windows.Forms.Control.Cursor%2A>|Varsayılan eşleme yeniden atanmadığından, <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimi, <xref:System.Windows.FrameworkElement.Cursor%2A> özelliği ayarlanmış bir üst öğe bulana kadar üst hiyerarşisinde gezir. Bu değer, en yakın karşılık gelen [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] imlecine çevrilir.<br /><br /> <xref:System.Windows.FrameworkElement.ForceCursor%2A> özelliği için varsayılan eşleme yeniden atanmadığından, geçiş işlemi, <xref:System.Windows.FrameworkElement.ForceCursor%2A> `true`olarak ayarlanan ilk üst öğede duraklar.|  
|<xref:System.Windows.FrameworkElement.FlowDirection%2A><br /><br /> (<xref:System.Windows.FlowDirection?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.RightToLeft%2A><br /><br /> (<xref:System.Windows.Forms.RightToLeft?displayProperty=nameWithType>)|<xref:System.Windows.Forms.RightToLeft.No>eşlenir <xref:System.Windows.FlowDirection.LeftToRight>.<br /><br /> <xref:System.Windows.Forms.RightToLeft.Yes>eşlenir <xref:System.Windows.FlowDirection.RightToLeft>.<br /><br /> <xref:System.Windows.Forms.RightToLeft.Inherit> eşlenmedi.<br /><br /> <xref:System.Windows.Forms.RightToLeft.Yes?displayProperty=nameWithType>eşlenir <xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType>.|  
|<xref:System.Windows.Controls.Control.FontStyle%2A>|barındırılan denetimin <xref:System.Drawing.Font?displayProperty=nameWithType> <xref:System.Drawing.Font.Style%2A>|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özellikler kümesi, karşılık gelen bir <xref:System.Drawing.Font>çevrilir. Bu özelliklerden biri değiştiğinde yeni bir <xref:System.Drawing.Font> oluşturulur. <xref:System.Windows.FontStyles.Normal%2A>için: <xref:System.Drawing.FontStyle.Italic> devre dışı bırakıldı. <xref:System.Windows.FontStyles.Italic%2A> veya <xref:System.Windows.FontStyles.Oblique%2A>için: <xref:System.Drawing.FontStyle.Italic> etkindir.|  
|<xref:System.Windows.Controls.Control.FontWeight%2A>|barındırılan denetimin <xref:System.Drawing.Font?displayProperty=nameWithType> <xref:System.Drawing.Font.Style%2A>|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özellikler kümesi, karşılık gelen bir <xref:System.Drawing.Font>çevrilir. Bu özelliklerden biri değiştiğinde yeni bir <xref:System.Drawing.Font> oluşturulur. <xref:System.Windows.FontWeights.Black%2A>, <xref:System.Windows.FontWeights.Bold%2A>, <xref:System.Windows.FontWeights.DemiBold%2A>, <xref:System.Windows.FontWeights.ExtraBold%2A>, <xref:System.Windows.FontWeights.Heavy%2A>, <xref:System.Windows.FontWeights.Medium%2A>, <xref:System.Windows.FontWeights.SemiBold%2A>veya <xref:System.Windows.FontWeights.UltraBold%2A>: <xref:System.Drawing.FontStyle.Bold> etkindir. <xref:System.Windows.FontWeights.ExtraLight%2A>, <xref:System.Windows.FontWeights.Light%2A>, <xref:System.Windows.FontWeights.Normal%2A>, <xref:System.Windows.FontWeights.Regular%2A>, <xref:System.Windows.FontWeights.Thin%2A>veya <xref:System.Windows.FontWeights.UltraLight%2A>: <xref:System.Drawing.FontStyle.Bold> devre dışı bırakıldı.|  
|<xref:System.Windows.Controls.Control.FontFamily%2A><br /><br /> <xref:System.Windows.Controls.Control.FontSize%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStretch%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStyle%2A><br /><br /> <xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Windows.Forms.Control.Font%2A><br /><br /> (<xref:System.Drawing.Font?displayProperty=nameWithType>)|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özellikler kümesi, karşılık gelen bir <xref:System.Drawing.Font>çevrilir. Bu özelliklerden biri değiştiğinde yeni bir <xref:System.Drawing.Font> oluşturulur. Barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi, yazı tipi boyutuna göre yeniden boyutlandırır.<br /><br /> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yazı tipi boyutu, inç bir dokun altılık olarak ifade edilir ve bir inç 'in bir adet on saniye olarak [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]. Karşılık gelen dönüştürme:<br /><br /> [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] yazı tipi boyutu = [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yazı tipi boyutu * 72,0/96,0.|  
|<xref:System.Windows.Controls.Control.Foreground%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.ForeColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Foreground%2A> özelliği eşleştirmesi aşağıdaki kurallar kullanılarak gerçekleştirilir:<br /><br /> -<xref:System.Windows.Controls.Control.Foreground%2A> bir <xref:System.Windows.Media.SolidColorBrush>, <xref:System.Windows.Forms.Control.ForeColor%2A>için <xref:System.Windows.Media.SolidColorBrush.Color%2A> kullanın.<br />-<xref:System.Windows.Controls.Control.Foreground%2A> bir <xref:System.Windows.Media.GradientBrush>, <xref:System.Windows.Forms.Control.ForeColor%2A>için en düşük fark değeri ile <xref:System.Windows.Media.GradientStop> rengini kullanın.<br />-Diğer <xref:System.Windows.Media.Brush> türleri için, <xref:System.Windows.Forms.Control.ForeColor%2A> değiştirmeden bırakın. Bu, varsayılan olarak kullanılan anlamına gelir.|  
|<xref:System.Windows.UIElement.IsEnabled%2A>|<xref:System.Windows.Forms.Control.Enabled%2A>|<xref:System.Windows.UIElement.IsEnabled%2A> ayarlandığında, <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi barındırılan denetimdeki <xref:System.Windows.Forms.Control.Enabled%2A> özelliğini ayarlar.|  
|<xref:System.Windows.Controls.Control.Padding%2A>|<xref:System.Windows.Forms.Control.Padding%2A>|Barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimindeki <xref:System.Windows.Forms.Control.Padding%2A> özelliğinin tüm dört değeri aynı <xref:System.Windows.Thickness> değerine ayarlanır.<br /><br /> -<xref:System.Int32.MaxValue> ' den büyük değerler <xref:System.Int32.MaxValue>olarak ayarlanır.<br />-<xref:System.Int32.MinValue> değerden küçük değerler <xref:System.Int32.MinValue>olarak ayarlanır.|  
|<xref:System.Windows.UIElement.Visibility%2A>|<xref:System.Windows.Forms.Control.Visible%2A>|-   <xref:System.Windows.Visibility.Visible> <xref:System.Windows.Forms.Control.Visible%2A> = `true`eşlenir. Barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi görünür. Barındırılan denetimdeki <xref:System.Windows.Forms.Control.Visible%2A> özelliğinin `false` olarak ayarlanması önerilmez.<br />-   <xref:System.Windows.Visibility.Collapsed> <xref:System.Windows.Forms.Control.Visible%2A> = `true` veya `false`eşlenir. Barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi çizilmez ve alanı daraltılmıştır.<br />-   <xref:System.Windows.Visibility.Hidden>: barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi düzendeki alanı kaplar, ancak görünür değildir. Bu durumda <xref:System.Windows.Forms.Control.Visible%2A> özelliği `true`olarak ayarlanır. Barındırılan denetimdeki <xref:System.Windows.Forms.Control.Visible%2A> özelliğinin `false` olarak ayarlanması önerilmez.|  
  
 Kapsayıcı öğelerinde Ekli Özellikler <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi tarafından tam olarak desteklenir.  
  
 Daha fazla bilgi için bkz. [Izlenecek yol: WindowsFormsHost öğesi kullanarak özellikleri eşleme](walkthrough-mapping-properties-using-the-windowsformshost-element.md).  
  
## <a name="updates-to-parent-properties"></a>Üst özelliklerde güncelleştirmeler  
 Çoğu üst özelliklerde yapılan değişiklikler barındırılan alt denetime yönelik bildirimlere neden olur. Aşağıdaki listede, değerleri değiştiğinde bildirimlere neden olmayan özellikler açıklanmaktadır.  
  
- <xref:System.Windows.Controls.Control.Background%2A>  
  
- <xref:System.Windows.FrameworkElement.Cursor%2A>  
  
- <xref:System.Windows.FrameworkElement.ForceCursor%2A>  
  
- <xref:System.Windows.UIElement.Visibility%2A>  
  
 Örneğin, <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesinin <xref:System.Windows.Controls.Control.Background%2A> özelliğinin değerini değiştirirseniz, barındırılan denetimin <xref:System.Windows.Forms.Control.BackColor%2A> özelliği değişmez.  
  
## <a name="property-mapping-with-the-elementhost-control"></a>ElementHost denetimiyle Özellik eşleme  
 Aşağıdaki özellikler yerleşik değişiklik bildirimi sağlar. Bu özellikleri eşlerken <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> yöntemini çağırmayın:  
  
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
  
- Üst  
  
- Bölge  
  
- RightToLeft  
  
- Boyut  
  
- Atan  
  
- Sekme durağı  
  
- Metin  
  
- Görünür  
  
 <xref:System.Windows.Forms.Integration.ElementHost> denetimi, aşağıdaki çeviri tablosunu kullanarak varsayılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] özelliklerini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] eşdeğerlerine dönüştürür.  
  
 Daha fazla bilgi için bkz. [Walkthrough: ElementHost denetimini kullanarak özellikleri eşleme](walkthrough-mapping-properties-using-the-elementhost-control.md).  
  
|Windows Forms barındırma|Windows Presentation Foundation|Birlikte çalışabilirlik davranışı|  
|---------------------------|-------------------------------------|-----------------------------|  
|<xref:System.Windows.Forms.Control.BackColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) barındırılan öğede|Bu özelliği ayarlamak bir <xref:System.Windows.Media.ImageBrush>yeniden çizmeyi zorlar. <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> özelliği `false` (varsayılan değer) olarak ayarlandıysa, bu <xref:System.Windows.Media.ImageBrush> <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, <xref:System.Windows.Forms.Control.BackgroundImageLayout%2A> özellikleri ve ekli boyama işleyicileri dahil <xref:System.Windows.Forms.Integration.ElementHost> denetiminin görünümüne dayalıdır.<br /><br /> <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> özelliği `true`olarak ayarlanırsa <xref:System.Windows.Media.ImageBrush>, üst öğenin <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, <xref:System.Windows.Forms.Control.BackgroundImageLayout%2A> özellikleri ve ekli boyama işleyicileri dahil <xref:System.Windows.Forms.Integration.ElementHost> denetimin üstünün görünümüne dayalıdır.|  
|<xref:System.Windows.Forms.Control.BackgroundImage%2A><br /><br /> (<xref:System.Drawing.Image?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) barındırılan öğede|Bu özelliğin ayarlanması <xref:System.Windows.Forms.Control.BackColor%2A> eşlemesi için açıklanan davranışa neden olur.|  
|<xref:System.Windows.Forms.Control.BackgroundImageLayout%2A>|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) barındırılan öğede|Bu özelliğin ayarlanması <xref:System.Windows.Forms.Control.BackColor%2A> eşlemesi için açıklanan davranışa neden olur.|  
|<xref:System.Windows.Forms.Control.Cursor%2A><br /><br /> (<xref:System.Windows.Forms.Cursor?displayProperty=nameWithType>)|<xref:System.Windows.FrameworkElement.Cursor%2A><br /><br /> (<xref:System.Windows.Input.Cursor?displayProperty=nameWithType>)|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Standart imleç, karşılık gelen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] standart imlecine çevrilir. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] standart bir imleç değilse, varsayılan değer atanır.|  
|<xref:System.Windows.Forms.Control.Enabled%2A>|<xref:System.Windows.UIElement.IsEnabled%2A>|<xref:System.Windows.Forms.Control.Enabled%2A> ayarlandığında, <xref:System.Windows.Forms.Integration.ElementHost> denetimi barındırılan öğedeki <xref:System.Windows.UIElement.IsEnabled%2A> özelliğini ayarlar.|  
|<xref:System.Windows.Forms.Control.Font%2A><br /><br /> (<xref:System.Drawing.Font?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.FontFamily%2A><br /><br /> <xref:System.Windows.Controls.Control.FontSize%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStretch%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStyle%2A><br /><br /> <xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Windows.Forms.Control.Font%2A> değeri karşılık gelen bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yazı tipi özellikleri kümesine çevrilir.|  
|<xref:System.Drawing.Font.Bold%2A>|barındırılan öğede <xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Drawing.Font.Bold%2A> `true`, <xref:System.Windows.Controls.Control.FontWeight%2A> <xref:System.Windows.FontWeights.Bold%2A>olarak ayarlanır.<br /><br /> <xref:System.Drawing.Font.Bold%2A> `false`, <xref:System.Windows.Controls.Control.FontWeight%2A> <xref:System.Windows.FontWeights.Normal%2A>olarak ayarlanır.|  
|<xref:System.Drawing.Font.Italic%2A>|barındırılan öğede <xref:System.Windows.Controls.Control.FontStyle%2A>|<xref:System.Drawing.Font.Italic%2A> `true`, <xref:System.Windows.Controls.Control.FontStyle%2A> <xref:System.Windows.FontStyles.Italic%2A>olarak ayarlanır.<br /><br /> <xref:System.Drawing.Font.Italic%2A> `false`, <xref:System.Windows.Controls.Control.FontStyle%2A> <xref:System.Windows.FontStyles.Normal%2A>olarak ayarlanır.|  
|<xref:System.Drawing.Font.Strikeout%2A>|barındırılan öğede <xref:System.Windows.TextDecorations>|Yalnızca bir <xref:System.Windows.Controls.TextBlock> denetimi barındırdığında geçerlidir.|  
|<xref:System.Drawing.Font.Underline%2A>|barındırılan öğede <xref:System.Windows.TextDecorations>|Yalnızca bir <xref:System.Windows.Controls.TextBlock> denetimi barındırdığında geçerlidir.|  
|<xref:System.Windows.Forms.Control.RightToLeft%2A><br /><br /> (<xref:System.Windows.Forms.RightToLeft?displayProperty=nameWithType>)|<xref:System.Windows.FrameworkElement.FlowDirection%2A><br /><br /> (<xref:System.Windows.FlowDirection>)|<xref:System.Windows.FlowDirection.LeftToRight>eşlenir <xref:System.Windows.Forms.RightToLeft.No>.<br /><br /> <xref:System.Windows.FlowDirection.RightToLeft>eşlenir <xref:System.Windows.Forms.RightToLeft.Yes>.|  
|<xref:System.Windows.Forms.Control.Visible%2A>|<xref:System.Windows.UIElement.Visibility%2A>|<xref:System.Windows.Forms.Integration.ElementHost> denetimi aşağıdaki kuralları kullanarak barındırılan öğedeki <xref:System.Windows.UIElement.Visibility%2A> özelliğini ayarlar:<br /><br /> -   <xref:System.Windows.Forms.Control.Visible%2A> = `true` <xref:System.Windows.Visibility.Visible>eşlenir.<br />-   <xref:System.Windows.Forms.Control.Visible%2A> = `false` <xref:System.Windows.Visibility.Hidden>eşlenir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [WPF ve Win32 Birlikte Çalışması](wpf-and-win32-interoperation.md)
- [WPF ve Windows Forms Birlikte Çalışması](wpf-and-windows-forms-interoperation.md)
- [İzlenecek yol: WindowsFormsHost Öğesi Kullanarak Özellikleri Eşleme](walkthrough-mapping-properties-using-the-windowsformshost-element.md)
- [İzlenecek yol: ElementHost Denetimini Kullanarak Özellikleri Eşleme](walkthrough-mapping-properties-using-the-elementhost-control.md)
