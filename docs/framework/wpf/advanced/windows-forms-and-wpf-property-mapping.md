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
ms.openlocfilehash: 67d1d1f2cb712c0c8ffec3972fd83bc46a66d65c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650796"
---
# <a name="windows-forms-and-wpf-property-mapping"></a>Windows Forms ve WPF Özelliğini Eşleme
[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] teknolojileri sahip iki özelliği, benzer ancak farklı modeli. *Özellik eşleme* iki mimariler arasında birlikte çalışabilirliği destekler ve aşağıdaki özellikleri sağlar:  
  
- Barındırılan denetim veya öğeyle ilgili özellik değişiklikleri konak ortamında eşleştirmeyi kolaylaştırır.  
  
- Kullanılan en yaygın olarak eşlemek için varsayılan işleme özellikleri sunar.  
  
- Geçersiz kılma veya varsayılan özelliklerini genişletme kolayca kaldırılmasını sağlar.  
  
- Özellik değeri değiştiğinde konak üzerinde otomatik olarak algılandı ve barındırılan denetim veya öğe için çevrilmiş olduğunu sağlar.  
  
> [!NOTE]
>  Özellik değiştirme olayları barındırma denetimi veya öğe hiyerarşisine yayılmaz. Yerel bir özelliğin değerini doğrudan ayarı, stiller, devralma, veri bağlama veya özelliğin değerini değiştiren başka mekanizmalar nedeniyle değişmezse özellik çevirisi yapılmaz.  
  
 Kullanım <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> özelliği <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi ve <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> özelliği <xref:System.Windows.Forms.Integration.ElementHost> özellik eşlemesi erişim denetimi.  
  
## <a name="property-mapping-with-the-windowsformshost-element"></a>WindowsFormsHost öğe özelliği eşleme  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi varsayılan çevirir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özelliklerine kendi [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] eşdeğerleri aşağıdaki çeviri tablosunu kullanarak.  
  
|Windows Presentation Foundation barındırma|Windows Forms|Birlikte çalışabilirlik davranışı|  
|---------------------------------------------|-------------------|-----------------------------|  
|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.BackColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğe kümeleri <xref:System.Windows.Forms.Control.BackColor%2A> barındırılan denetim özelliğini ve <xref:System.Windows.Forms.Control.BackgroundImage%2A> barındırılan denetim özelliği. Eşleme, aşağıdaki kurallar kullanılarak gerçekleştirilir:<br /><br /> -Eğer <xref:System.Windows.Controls.Control.Background%2A> düz bir renk dönüştürülür ve ayarlamak için kullanılan <xref:System.Windows.Forms.Control.BackColor%2A> barındırılan denetim özelliği. <xref:System.Windows.Forms.Control.BackColor%2A> Özelliği ayarlı değil barındırılan denetiminde barındırılan denetim değerini devralabileceğinden <xref:System.Windows.Forms.Control.BackColor%2A> özelliği. **Not:**  Barındırılan denetim saydamlık desteklemez. Atanan herhangi bir renk <xref:System.Windows.Forms.Control.BackColor%2A> 0xFF alfa değeri ile tam opak olması gerekir. <br /><br /> -Eğer <xref:System.Windows.Controls.Control.Background%2A> düz bir renk değil <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimi oluşturur eşlemden <xref:System.Windows.Controls.Control.Background%2A> özelliği. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Denetimi bu bit eşlemi atayan <xref:System.Windows.Forms.Control.BackgroundImage%2A> barındırılan denetim özelliği. Bu, saydamlığa benzeyen bir efekti sağlar. **Not:**  Bu davranışı geçersiz kılmak veya kaldırabilirsiniz <xref:System.Windows.Controls.Control.Background%2A> özellik eşlemesi.|  
|<xref:System.Windows.FrameworkElement.Cursor%2A>|<xref:System.Windows.Forms.Control.Cursor%2A>|Varsayılan eşleme atandı değil, <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimi erişir, üst hiyerarşisi olan bir üst bulana kadar kendi <xref:System.Windows.FrameworkElement.Cursor%2A> özellik kümesi. Bu değer en yakın ilgili çevrilir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] imleç.<br /><br /> Varsayılan eşlemesini <xref:System.Windows.FrameworkElement.ForceCursor%2A> özelliği yok atadı, geçişi durdurur olan ilk üst <xref:System.Windows.FrameworkElement.ForceCursor%2A> kümesine `true`.|  
|<xref:System.Windows.FrameworkElement.FlowDirection%2A><br /><br /> (<xref:System.Windows.FlowDirection?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.RightToLeft%2A><br /><br /> (<xref:System.Windows.Forms.RightToLeft?displayProperty=nameWithType>)|<xref:System.Windows.FlowDirection.LeftToRight> eşlendiği <xref:System.Windows.Forms.RightToLeft.No>.<br /><br /> <xref:System.Windows.FlowDirection.RightToLeft> eşlendiği <xref:System.Windows.Forms.RightToLeft.Yes>.<br /><br /> <xref:System.Windows.Forms.RightToLeft.Inherit> eşlenmemiş.<br /><br /> <xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType> eşlendiği <xref:System.Windows.Forms.RightToLeft.Yes?displayProperty=nameWithType>.|  
|<xref:System.Windows.Controls.Control.FontStyle%2A>|<xref:System.Drawing.Font.Style%2A> barındırılan denetim üzerinde <xref:System.Drawing.Font?displayProperty=nameWithType>|Dizi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özellikleri, karşılık gelen içine çevrilir <xref:System.Drawing.Font>. Bu özelliklerden biri değiştiğinde yeni bir <xref:System.Drawing.Font> oluşturulur. İçin <xref:System.Windows.FontStyles.Normal%2A>: <xref:System.Drawing.FontStyle.Italic> devre dışı bırakıldı. İçin <xref:System.Windows.FontStyles.Italic%2A> veya <xref:System.Windows.FontStyles.Oblique%2A>: <xref:System.Drawing.FontStyle.Italic> etkinleştirilir.|  
|<xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Drawing.Font.Style%2A> barındırılan denetim üzerinde <xref:System.Drawing.Font?displayProperty=nameWithType>|Dizi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özellikleri, karşılık gelen içine çevrilir <xref:System.Drawing.Font>. Bu özelliklerden biri değiştiğinde yeni bir <xref:System.Drawing.Font> oluşturulur. İçin <xref:System.Windows.FontWeights.Black%2A>, <xref:System.Windows.FontWeights.Bold%2A>, <xref:System.Windows.FontWeights.DemiBold%2A>, <xref:System.Windows.FontWeights.ExtraBold%2A>, <xref:System.Windows.FontWeights.Heavy%2A>, <xref:System.Windows.FontWeights.Medium%2A>, <xref:System.Windows.FontWeights.SemiBold%2A>, veya <xref:System.Windows.FontWeights.UltraBold%2A>: <xref:System.Drawing.FontStyle.Bold> etkinleştirilir. İçin <xref:System.Windows.FontWeights.ExtraLight%2A>, <xref:System.Windows.FontWeights.Light%2A>, <xref:System.Windows.FontWeights.Normal%2A>, <xref:System.Windows.FontWeights.Regular%2A>, <xref:System.Windows.FontWeights.Thin%2A>, veya <xref:System.Windows.FontWeights.UltraLight%2A>: <xref:System.Drawing.FontStyle.Bold> devre dışı bırakıldı.|  
|<xref:System.Windows.Controls.Control.FontFamily%2A><br /><br /> <xref:System.Windows.Controls.Control.FontSize%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStretch%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStyle%2A><br /><br /> <xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Windows.Forms.Control.Font%2A><br /><br /> (<xref:System.Drawing.Font?displayProperty=nameWithType>)|Dizi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özellikleri, karşılık gelen içine çevrilir <xref:System.Drawing.Font>. Bu özelliklerden biri değiştiğinde yeni bir <xref:System.Drawing.Font> oluşturulur. Barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi yazı tipi boyutuna göre yeniden boyutlandırır.<br /><br /> Yazı tipi boyutunu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir doksan altıda ve inç olarak ifade edilen [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] inç bir yetmiş saniye olarak. Karşılık gelen dönüştürmedir:<br /><br /> [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] yazı tipi boyutu = [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yazı tipi boyutu * 72.0 / 96.0.|  
|<xref:System.Windows.Controls.Control.Foreground%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.ForeColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Foreground%2A> Özellik eşlemesi, aşağıdaki kurallar kullanılarak gerçekleştirilir:<br /><br /> -Eğer <xref:System.Windows.Controls.Control.Foreground%2A> olduğu bir <xref:System.Windows.Media.SolidColorBrush>, kullanın <xref:System.Windows.Media.SolidColorBrush.Color%2A> için <xref:System.Windows.Forms.Control.ForeColor%2A>.<br />-Eğer <xref:System.Windows.Controls.Control.Foreground%2A> olduğu bir <xref:System.Windows.Media.GradientBrush>, rengi kullanma <xref:System.Windows.Media.GradientStop> için en düşük bir uzaklık değeri ile <xref:System.Windows.Forms.Control.ForeColor%2A>.<br />-İçin diğer <xref:System.Windows.Media.Brush> yazın, bırakın <xref:System.Windows.Forms.Control.ForeColor%2A> değişmez. Başka bir deyişle varsayılan değer kullanılır.|  
|<xref:System.Windows.UIElement.IsEnabled%2A>|<xref:System.Windows.Forms.Control.Enabled%2A>|Zaman <xref:System.Windows.UIElement.IsEnabled%2A> ayarlanan <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğe kümeleri <xref:System.Windows.Forms.Control.Enabled%2A> barındırılan denetim özelliği.|  
|<xref:System.Windows.Controls.Control.Padding%2A>|<xref:System.Windows.Forms.Control.Padding%2A>|Tüm dört değerden <xref:System.Windows.Forms.Control.Padding%2A> barındırılan özelliği [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi aynı ayarlanır <xref:System.Windows.Thickness> değeri.<br /><br /> -Değerleri büyük <xref:System.Int32.MaxValue> ayarlandığından <xref:System.Int32.MaxValue>.<br />-Değerleri küçüktür <xref:System.Int32.MinValue> ayarlandığından <xref:System.Int32.MinValue>.|  
|<xref:System.Windows.UIElement.Visibility%2A>|<xref:System.Windows.Forms.Control.Visible%2A>|-   <xref:System.Windows.Visibility.Visible> eşlendiği <xref:System.Windows.Forms.Control.Visible%2A>  =  `true`. Barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi görünür. Açık olarak ayarlama <xref:System.Windows.Forms.Control.Visible%2A> özelliği için barındırılan denetimde `false` önerilmez.<br />-   <xref:System.Windows.Visibility.Collapsed> eşlendiği <xref:System.Windows.Forms.Control.Visible%2A>  =  `true` veya `false`. Barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi çizilmez ve alanı daraltılır.<br />-   <xref:System.Windows.Visibility.Hidden> : Barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi düzende yer kaplayan, ancak görünür değil. Bu durumda, <xref:System.Windows.Forms.Control.Visible%2A> özelliği `true`. Açık olarak ayarlama <xref:System.Windows.Forms.Control.Visible%2A> özelliği için barındırılan denetimde `false` önerilmez.|  
  
 Kapsayıcı öğeler üzerinde iliştirilmiş özellikler tarafından tam olarak desteklenmektedir <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi.  
  
 Daha fazla bilgi için [izlenecek yol: WindowsFormsHost Öğesi kullanarak özellikleri eşleme](walkthrough-mapping-properties-using-the-windowsformshost-element.md).  
  
## <a name="updates-to-parent-properties"></a>Üst özellikleri için güncelleştirmeler  
 Çoğu üst özelliklerde yapılan değişiklikler, barındırılan alt denetimin bildirimleri neden. Aşağıdaki liste değerleri değiştiğinde bildirim neden olmaz özellikleri açıklar.  
  
- <xref:System.Windows.Controls.Control.Background%2A>  
  
- <xref:System.Windows.FrameworkElement.Cursor%2A>  
  
- <xref:System.Windows.FrameworkElement.ForceCursor%2A>  
  
- <xref:System.Windows.UIElement.Visibility%2A>  
  
 Örneğin değerini değiştirirseniz, <xref:System.Windows.Controls.Control.Background%2A> özelliği <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi <xref:System.Windows.Forms.Control.BackColor%2A> barındırılan denetim özelliği değiştirmez.  
  
## <a name="property-mapping-with-the-elementhost-control"></a>ElementHost Denetimi ile özellik eşlemesi  
 Yerleşik değişiklik bildirimi aşağıdaki özellikleri sağlar. Çağırmayın <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> bu özellikleri eşlerken yöntemi:  
  
- AutoSize  
  
- Arka plan rengi  
  
- BackgroundImage  
  
- BackgroundImageLayout  
  
- BindingContext  
  
- CausesValidation  
  
- ContextMenu  
  
- ContextMenuStrip  
  
- İmleç  
  
- Dock  
  
- Etkin  
  
- Yazı tipi  
  
- ForeColor  
  
- Konum  
  
- Kenar boşluğu  
  
- Doldurma  
  
- Üst öğe  
  
- Bölge  
  
- RightToLeft  
  
- Boyut  
  
- TabIndex  
  
- Sekme durağı  
  
- Metin  
  
- Görünür  
  
 <xref:System.Windows.Forms.Integration.ElementHost> Denetimi varsayılan çevirir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] özelliklerine kendi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] eşdeğerleri aşağıdaki çeviri tablosunu kullanarak.  
  
 Daha fazla bilgi için [izlenecek yol: ElementHost denetimini kullanarak özellikleri eşleme](walkthrough-mapping-properties-using-the-elementhost-control.md).  
  
|Windows Forms barındırma|Windows Presentation Foundation|Birlikte çalışabilirlik davranışı|  
|---------------------------|-------------------------------------|-----------------------------|  
|<xref:System.Windows.Forms.Control.BackColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) barındırılan öğenin|Bu özellik ayarı ile yeniden çizmeyi zorlar bir <xref:System.Windows.Media.ImageBrush>. Varsa <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> özelliği `false` (varsayılan değer) bu <xref:System.Windows.Media.ImageBrush> görüntüsünü temel <xref:System.Windows.Forms.Integration.ElementHost> dahil olmak üzere, denetimi kendi <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, <xref:System.Windows.Forms.Control.BackgroundImageLayout%2A> özellikleri ve ekli Boya işleyicileri.<br /><br /> Varsa <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> özelliği `true`, <xref:System.Windows.Media.ImageBrush> görüntüsünü temel <xref:System.Windows.Forms.Integration.ElementHost> üst öğenin dahil olmak üzere, denetimin üst <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, <xref:System.Windows.Forms.Control.BackgroundImageLayout%2A> özellikleri ve ekli Boya işleyicileri.|  
|<xref:System.Windows.Forms.Control.BackgroundImage%2A><br /><br /> (<xref:System.Drawing.Image?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) barındırılan öğenin|Bu özelliği ayarlamak için açıklanan aynı davranışa neden <xref:System.Windows.Forms.Control.BackColor%2A> eşleme.|  
|<xref:System.Windows.Forms.Control.BackgroundImageLayout%2A>|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) barındırılan öğenin|Bu özelliği ayarlamak için açıklanan aynı davranışa neden <xref:System.Windows.Forms.Control.BackColor%2A> eşleme.|  
|<xref:System.Windows.Forms.Control.Cursor%2A><br /><br /> (<xref:System.Windows.Forms.Cursor?displayProperty=nameWithType>)|<xref:System.Windows.FrameworkElement.Cursor%2A><br /><br /> (<xref:System.Windows.Input.Cursor?displayProperty=nameWithType>)|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Karşılık gelen standart imleç çevrilir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] standart imleç. Varsa [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] standart bir imleç değil varsayılan atanır.|  
|<xref:System.Windows.Forms.Control.Enabled%2A>|<xref:System.Windows.UIElement.IsEnabled%2A>|Zaman <xref:System.Windows.Forms.Control.Enabled%2A> ayarlanan <xref:System.Windows.Forms.Integration.ElementHost> denetim kümeleri <xref:System.Windows.UIElement.IsEnabled%2A> barındırılan özelliği.|  
|<xref:System.Windows.Forms.Control.Font%2A><br /><br /> (<xref:System.Drawing.Font?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.FontFamily%2A><br /><br /> <xref:System.Windows.Controls.Control.FontSize%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStretch%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStyle%2A><br /><br /> <xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Windows.Forms.Control.Font%2A> Değerine karşılık gelen bir kümesi olarak çevrilir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yazı tipi özellikleri.|  
|<xref:System.Drawing.Font.Bold%2A>|<xref:System.Windows.Controls.Control.FontWeight%2A> barındırılan|Varsa <xref:System.Drawing.Font.Bold%2A> olduğu `true`, <xref:System.Windows.Controls.Control.FontWeight%2A> ayarlanır <xref:System.Windows.FontWeights.Bold%2A>.<br /><br /> Varsa <xref:System.Drawing.Font.Bold%2A> olduğu `false`, <xref:System.Windows.Controls.Control.FontWeight%2A> ayarlanır <xref:System.Windows.FontWeights.Normal%2A>.|  
|<xref:System.Drawing.Font.Italic%2A>|<xref:System.Windows.Controls.Control.FontStyle%2A> barındırılan|Varsa <xref:System.Drawing.Font.Italic%2A> olduğu `true`, <xref:System.Windows.Controls.Control.FontStyle%2A> ayarlanır <xref:System.Windows.FontStyles.Italic%2A>.<br /><br /> Varsa <xref:System.Drawing.Font.Italic%2A> olduğu `false`, <xref:System.Windows.Controls.Control.FontStyle%2A> ayarlanır <xref:System.Windows.FontStyles.Normal%2A>.|  
|<xref:System.Drawing.Font.Strikeout%2A>|<xref:System.Windows.TextDecorations> barındırılan|Yalnızca barındırırken geçerli bir <xref:System.Windows.Controls.TextBlock> denetimi.|  
|<xref:System.Drawing.Font.Underline%2A>|<xref:System.Windows.TextDecorations> barındırılan|Yalnızca barındırırken geçerli bir <xref:System.Windows.Controls.TextBlock> denetimi.|  
|<xref:System.Windows.Forms.Control.RightToLeft%2A><br /><br /> (<xref:System.Windows.Forms.RightToLeft?displayProperty=nameWithType>)|<xref:System.Windows.FrameworkElement.FlowDirection%2A><br /><br /> (<xref:System.Windows.FlowDirection>)|<xref:System.Windows.Forms.RightToLeft.No> eşlendiği <xref:System.Windows.FlowDirection.LeftToRight>.<br /><br /> <xref:System.Windows.Forms.RightToLeft.Yes> eşlendiği <xref:System.Windows.FlowDirection.RightToLeft>.|  
|<xref:System.Windows.Forms.Control.Visible%2A>|<xref:System.Windows.UIElement.Visibility%2A>|<xref:System.Windows.Forms.Integration.ElementHost> Denetim kümeleri <xref:System.Windows.UIElement.Visibility%2A> aşağıdaki kuralları kullanarak barındırılan öğesindeki özelliği:<br /><br /> -   <xref:System.Windows.Forms.Control.Visible%2A> = `true` eşlendiği <xref:System.Windows.Visibility.Visible>.<br />-   <xref:System.Windows.Forms.Control.Visible%2A> = `false` eşlendiği <xref:System.Windows.Visibility.Hidden>.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [WPF ve Win32 Birlikte Çalışması](wpf-and-win32-interoperation.md)
- [WPF ve Windows Forms Birlikte Çalışması](wpf-and-windows-forms-interoperation.md)
- [İzlenecek yol: WindowsFormsHost Öğesi kullanarak özellikleri eşleme](walkthrough-mapping-properties-using-the-windowsformshost-element.md)
- [İzlenecek yol: ElementHost denetimini kullanarak özellikleri eşleme](walkthrough-mapping-properties-using-the-elementhost-control.md)
