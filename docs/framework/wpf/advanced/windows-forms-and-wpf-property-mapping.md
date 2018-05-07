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
ms.openlocfilehash: f2177c65a8b1a1d5ad2f5bad67591e6d98087539
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="windows-forms-and-wpf-property-mapping"></a>Windows Forms ve WPF Özelliğini Eşleme
[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] teknolojileri iki özelliği, benzer ancak farklı modelleri vardır. *Özellik eşlemesi* iki mimarinin arasında birlikte çalışabilirliği destekler ve aşağıdaki yetenekleri sağlar:  
  
-   Konak ortamında ilgili özellik değişikliklerini barındırılan denetime veya öğeye eşlemek kolaylaştırır.  
  
-   En yaygın olarak eşlemek için varsayılan işleme özelliklerinin kullanılmasını sağlar.  
  
-   Geçersiz kılma veya varsayılan özelliklerini genişletme kolayca kaldırılmasını sağlar.  
  
-   Özellik değeri değişiklikleri ana bilgisayarda otomatik olarak algılanan ve barındırılan denetime veya öğeye çevrilen olduğunu sağlar.  
  
> [!NOTE]
>  Özellik değiştirme olayları barındırılan denetime veya öğe hiyerarşisine yayılmaz. Yerel bir özelliğin değerini doğrudan ayarlama, stiller, devralma, veri bağlama veya özelliğin değerini değiştirmek diğer mekanizmalar nedeniyle değişmezse özellik çevirisi yapılmaz.  
  
 Kullanım <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> özelliği <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi ve <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> özellikte <xref:System.Windows.Forms.Integration.ElementHost> özellik eşlemesi erişmek için denetim.  
  
## <a name="property-mapping-with-the-windowsformshost-element"></a>WindowsFormsHost Öğesi ile özellik eşlemesi  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi çevirir varsayılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özelliklerine kendi [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] aşağıdaki çeviri tablosunu kullanarak eşdeğerleri.  
  
|Windows Presentation Foundation barındırma|Windows Forms|Birlikte çalışabilirlik davranışı|  
|---------------------------------------------|-------------------|-----------------------------|  
|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.BackColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi kümeleri <xref:System.Windows.Forms.Control.BackColor%2A> barındırılan denetim özelliği ve <xref:System.Windows.Forms.Control.BackgroundImage%2A> barındırılan denetimi özelliği. Eşleme aşağıdaki kuralları kullanarak gerçekleştirilir:<br /><br /> -İf <xref:System.Windows.Controls.Control.Background%2A> düz renk dönüştürülür ve ayarlamak için kullanılan <xref:System.Windows.Forms.Control.BackColor%2A> barındırılan denetimi özelliği. <xref:System.Windows.Forms.Control.BackColor%2A> Özelliği ayarlı değil barındırılan denetimde denetimden değerini devrettiği çünkü <xref:System.Windows.Forms.Control.BackColor%2A> özelliği. **Not:** denetimden saydamlığı desteklemez. Atanan herhangi bir renk <xref:System.Windows.Forms.Control.BackColor%2A> 0xFF alfa değeri ile tamamıyla opak olması gerekir. <br /><br /> -İf <xref:System.Windows.Controls.Control.Background%2A> düz renk değil <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimi oluşturur bir bit eşlem <xref:System.Windows.Controls.Control.Background%2A> özelliği. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Denetim atar bu bit eşlemi <xref:System.Windows.Forms.Control.BackgroundImage%2A> barındırılan denetimi özelliği. Saydamlık benzeyen bir efekt sağlar. **Not:** bu davranışı geçersiz kılabilirsiniz veya kaldırabilirsiniz <xref:System.Windows.Controls.Control.Background%2A> özellik eşlemesi.|  
|<xref:System.Windows.FrameworkElement.Cursor%2A>|<xref:System.Windows.Forms.Control.Cursor%2A>|Varsayılan eşleme atandı değil, <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimi erişir, üst hiyerarşisi olan bir üst bulana kadar kendi <xref:System.Windows.FrameworkElement.Cursor%2A> özellik kümesi. Bu değer en yakın ilgili çevrilir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] imleç.<br /><br /> Varsa için varsayılan eşlemeyi <xref:System.Windows.FrameworkElement.ForceCursor%2A> özelliğine değil yeniden atandığında, geçişi durdurur olan ilk üst <xref:System.Windows.FrameworkElement.ForceCursor%2A> kümesine `true`.|  
|<xref:System.Windows.FrameworkElement.FlowDirection%2A><br /><br /> (<xref:System.Windows.FlowDirection?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.RightToLeft%2A><br /><br /> (<xref:System.Windows.Forms.RightToLeft?displayProperty=nameWithType>)|<xref:System.Windows.FlowDirection.LeftToRight> eşlendiği <xref:System.Windows.Forms.RightToLeft.No>.<br /><br /> <xref:System.Windows.FlowDirection.RightToLeft> eşlendiği <xref:System.Windows.Forms.RightToLeft.Yes>.<br /><br /> <xref:System.Windows.Forms.RightToLeft.Inherit> eşlenmemiş.<br /><br /> <xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType> eşlendiği <xref:System.Windows.Forms.RightToLeft.Yes?displayProperty=nameWithType>.|  
|<xref:System.Windows.Controls.Control.FontStyle%2A>|<xref:System.Drawing.Font.Style%2A> barındırılan denetimin üzerinde <xref:System.Drawing.Font?displayProperty=nameWithType>|Kümesini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özellikleri, karşılık gelen içine çevrilir <xref:System.Drawing.Font>. Bu özelliklerden biri değiştiğinde, yeni bir <xref:System.Drawing.Font> oluşturulur. İçin <xref:System.Windows.FontStyles.Normal%2A>: <xref:System.Drawing.FontStyle.Italic> devre dışı bırakılır. İçin <xref:System.Windows.FontStyles.Italic%2A> veya <xref:System.Windows.FontStyles.Oblique%2A>: <xref:System.Drawing.FontStyle.Italic> etkinleştirilir.|  
|<xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Drawing.Font.Style%2A> barındırılan denetimin üzerinde <xref:System.Drawing.Font?displayProperty=nameWithType>|Kümesini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özellikleri, karşılık gelen içine çevrilir <xref:System.Drawing.Font>. Bu özelliklerden biri değiştiğinde, yeni bir <xref:System.Drawing.Font> oluşturulur. İçin <xref:System.Windows.FontWeights.Black%2A>, <xref:System.Windows.FontWeights.Bold%2A>, <xref:System.Windows.FontWeights.DemiBold%2A>, <xref:System.Windows.FontWeights.ExtraBold%2A>, <xref:System.Windows.FontWeights.Heavy%2A>, <xref:System.Windows.FontWeights.Medium%2A>, <xref:System.Windows.FontWeights.SemiBold%2A>, veya <xref:System.Windows.FontWeights.UltraBold%2A>: <xref:System.Drawing.FontStyle.Bold> etkinleştirilir. İçin <xref:System.Windows.FontWeights.ExtraLight%2A>, <xref:System.Windows.FontWeights.Light%2A>, <xref:System.Windows.FontWeights.Normal%2A>, <xref:System.Windows.FontWeights.Regular%2A>, <xref:System.Windows.FontWeights.Thin%2A>, veya <xref:System.Windows.FontWeights.UltraLight%2A>: <xref:System.Drawing.FontStyle.Bold> devre dışı bırakılır.|  
|<xref:System.Windows.Controls.Control.FontFamily%2A><br /><br /> <xref:System.Windows.Controls.Control.FontSize%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStretch%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStyle%2A><br /><br /> <xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Windows.Forms.Control.Font%2A><br /><br /> (<xref:System.Drawing.Font?displayProperty=nameWithType>)|Kümesini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özellikleri, karşılık gelen içine çevrilir <xref:System.Drawing.Font>. Bu özelliklerden biri değiştiğinde, yeni bir <xref:System.Drawing.Font> oluşturulur. Barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi yazı tipi boyutuna göre yeniden boyutlandırır.<br /><br /> Yazı tipi boyutunu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir doksan altıncı inç ve içinde olarak ifade edilen [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] bir yetmiş saniyelik inç olarak. İlgili dönüştürme şöyledir:<br /><br /> [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] yazı tipi boyutunu = [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yazı tipi boyutu * 72.0 / 96.0.|  
|<xref:System.Windows.Controls.Control.Foreground%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.ForeColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Foreground%2A> Özellik eşlemesi, aşağıdaki kuralları kullanarak gerçekleştirilir:<br /><br /> -İf <xref:System.Windows.Controls.Control.Foreground%2A> olan bir <xref:System.Windows.Media.SolidColorBrush>, kullanın <xref:System.Windows.Media.SolidColorBrush.Color%2A> için <xref:System.Windows.Forms.Control.ForeColor%2A>.<br />-İf <xref:System.Windows.Controls.Control.Foreground%2A> olan bir <xref:System.Windows.Media.GradientBrush>, rengi kullanmak <xref:System.Windows.Media.GradientStop> için en düşük uzaklık değeri ile <xref:System.Windows.Forms.Control.ForeColor%2A>.<br />-İçin diğer <xref:System.Windows.Media.Brush> yazın, bırakın <xref:System.Windows.Forms.Control.ForeColor%2A> değişmez. Başka bir deyişle varsayılan değer kullanılır.|  
|<xref:System.Windows.UIElement.IsEnabled%2A>|<xref:System.Windows.Forms.Control.Enabled%2A>|Zaman <xref:System.Windows.UIElement.IsEnabled%2A> ayarlanır, <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi kümeleri <xref:System.Windows.Forms.Control.Enabled%2A> barındırılan denetimi özelliği.|  
|<xref:System.Windows.Controls.Control.Padding%2A>|<xref:System.Windows.Forms.Control.Padding%2A>|Tüm dört değerden <xref:System.Windows.Forms.Control.Padding%2A> özelliği barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetim için aynı ayarlanır <xref:System.Windows.Thickness> değeri.<br /><br /> -Değerleri büyük <xref:System.Int32.MaxValue> ayarlanır <xref:System.Int32.MaxValue>.<br />-Değerleri değerinden <xref:System.Int32.MinValue> ayarlanır <xref:System.Int32.MinValue>.|  
|<xref:System.Windows.UIElement.Visibility%2A>|<xref:System.Windows.Forms.Control.Visible%2A>|-   <xref:System.Windows.Visibility.Visible> eşlendiği <xref:System.Windows.Forms.Control.Visible%2A>  =  `true`. Barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetim görülebilir. Açıkça ayarı <xref:System.Windows.Forms.Control.Visible%2A> barındırılan denetime özellikte `false` önerilmez.<br />-   <xref:System.Windows.Visibility.Collapsed> eşlendiği <xref:System.Windows.Forms.Control.Visible%2A>  =  `true` veya `false`. Barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi çizilmez ve alanı daraltılır.<br />-   <xref:System.Windows.Visibility.Hidden> : Barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi düzende yer kaplar ancak görünür değil. Bu durumda, <xref:System.Windows.Forms.Control.Visible%2A> özelliği ayarlanmış `true`. Açıkça ayarı <xref:System.Windows.Forms.Control.Visible%2A> barındırılan denetime özellikte `false` önerilmez.|  
  
 Kapsayıcı öğeler üzerinde ekli özellikler tarafından tam olarak desteklenmektedir <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi.  
  
 Daha fazla bilgi için bkz: [izlenecek yol: WindowsFormsHost Öğesi kullanarak eşleme özellikleri](../../../../docs/framework/wpf/advanced/walkthrough-mapping-properties-using-the-windowsformshost-element.md).  
  
## <a name="updates-to-parent-properties"></a>Üst özellikleri için güncelleştirmeler  
 Çoğu üst özelliklerine yapılan değişiklikler barındırılan alt denetim bildirimleri neden. Aşağıdaki listede değerlerine değiştirdiğinizde bildirimleri neden olmaz özellikleri açıklanmaktadır.  
  
-   <xref:System.Windows.Controls.Control.Background%2A>  
  
-   <xref:System.Windows.FrameworkElement.Cursor%2A>  
  
-   <xref:System.Windows.FrameworkElement.ForceCursor%2A>  
  
-   <xref:System.Windows.UIElement.Visibility%2A>  
  
 Değeri değiştirirseniz, örneğin, <xref:System.Windows.Controls.Control.Background%2A> özelliği <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi, <xref:System.Windows.Forms.Control.BackColor%2A> barındırılan denetimi özelliği değiştirmez.  
  
## <a name="property-mapping-with-the-elementhost-control"></a>ElementHost Denetimi ile özellik eşlemesi  
 Aşağıdaki özellikler, yerleşik değişiklik bildirimi sağlar. Çağırmayın <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> bu özellikleri eşlerken yöntemi:  
  
-   AutoSize  
  
-   Arka plan rengi  
  
-   BackgroundImage  
  
-   BackgroundImageLayout  
  
-   Bindingparameters'te  
  
-   CausesValidation  
  
-   ContextMenu  
  
-   ContextMenuStrip  
  
-   İmleç  
  
-   Yerleştirme  
  
-   Etkin  
  
-   Yazı tipi  
  
-   ForeColor  
  
-   Konum  
  
-   Kenar boşluğu  
  
-   Doldurma  
  
-   Üst  
  
-   Bölge  
  
-   RightToLeft  
  
-   Boyut  
  
-   TabIndex  
  
-   TabStop  
  
-   Metin  
  
-   Görünür  
  
 <xref:System.Windows.Forms.Integration.ElementHost> Denetimi çevirir varsayılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] özelliklerine kendi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aşağıdaki çeviri tablosunu kullanarak eşdeğerleri.  
  
 Daha fazla bilgi için bkz: [izlenecek yol: ElementHost Denetimi kullanarak eşleme özellikleri](../../../../docs/framework/wpf/advanced/walkthrough-mapping-properties-using-the-elementhost-control.md).  
  
|Windows Forms barındırma|Windows Presentation Foundation|Birlikte çalışabilirlik davranışı|  
|---------------------------|-------------------------------------|-----------------------------|  
|<xref:System.Windows.Forms.Control.BackColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) barındırılan öğesinde|Bu özellik ayarı ile yeniden çizmeyi zorlar bir <xref:System.Windows.Media.ImageBrush>. Varsa <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> özelliği ayarlanmış `false` (varsayılan değer) bu <xref:System.Windows.Media.ImageBrush> görüntüsünü temel <xref:System.Windows.Forms.Integration.ElementHost> denetimi dahil olmak üzere kendi <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, <xref:System.Windows.Forms.Control.BackgroundImageLayout%2A> özellikleri ve tüm ekli boyama işleyicileri.<br /><br /> Varsa <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> özelliği ayarlanmış `true`, <xref:System.Windows.Media.ImageBrush> görüntüsünü temel <xref:System.Windows.Forms.Integration.ElementHost> üst öğenin de dahil olmak üzere, denetimin üst <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, <xref:System.Windows.Forms.Control.BackgroundImageLayout%2A> özellikleri ve tüm ekli boyama işleyicileri.|  
|<xref:System.Windows.Forms.Control.BackgroundImage%2A><br /><br /> (<xref:System.Drawing.Image?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) barındırılan öğesinde|Bu özelliği ayarlamak için açıklanan aynı davranışa neden <xref:System.Windows.Forms.Control.BackColor%2A> eşleme.|  
|<xref:System.Windows.Forms.Control.BackgroundImageLayout%2A>|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) barındırılan öğesinde|Bu özelliği ayarlamak için açıklanan aynı davranışa neden <xref:System.Windows.Forms.Control.BackColor%2A> eşleme.|  
|<xref:System.Windows.Forms.Control.Cursor%2A><br /><br /> (<xref:System.Windows.Forms.Cursor?displayProperty=nameWithType>)|<xref:System.Windows.FrameworkElement.Cursor%2A><br /><br /> (<xref:System.Windows.Input.Cursor?displayProperty=nameWithType>)|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Standart imleci karşılık gelen çevrilir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] standart imleç. Varsa [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] standart bir imleç değil varsayılan atanır.|  
|<xref:System.Windows.Forms.Control.Enabled%2A>|<xref:System.Windows.UIElement.IsEnabled%2A>|Zaman <xref:System.Windows.Forms.Control.Enabled%2A> ayarlanır, <xref:System.Windows.Forms.Integration.ElementHost> denetleyen ayarlar <xref:System.Windows.UIElement.IsEnabled%2A> barındırılan öğesindeki özelliği.|  
|<xref:System.Windows.Forms.Control.Font%2A><br /><br /> (<xref:System.Drawing.Font?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.FontFamily%2A><br /><br /> <xref:System.Windows.Controls.Control.FontSize%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStretch%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStyle%2A><br /><br /> <xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Windows.Forms.Control.Font%2A> Değeri karşılık gelen bir dizi çevrilen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yazı tipi özellikleri.|  
|<xref:System.Drawing.Font.Bold%2A>|<xref:System.Windows.Controls.Control.FontWeight%2A> barındırılan|Varsa <xref:System.Drawing.Font.Bold%2A> olan `true`, <xref:System.Windows.Controls.Control.FontWeight%2A> ayarlanır <xref:System.Windows.FontWeights.Bold%2A>.<br /><br /> Varsa <xref:System.Drawing.Font.Bold%2A> olan `false`, <xref:System.Windows.Controls.Control.FontWeight%2A> ayarlanır <xref:System.Windows.FontWeights.Normal%2A>.|  
|<xref:System.Drawing.Font.Italic%2A>|<xref:System.Windows.Controls.Control.FontStyle%2A> barındırılan|Varsa <xref:System.Drawing.Font.Italic%2A> olan `true`, <xref:System.Windows.Controls.Control.FontStyle%2A> ayarlanır <xref:System.Windows.FontStyles.Italic%2A>.<br /><br /> Varsa <xref:System.Drawing.Font.Italic%2A> olan `false`, <xref:System.Windows.Controls.Control.FontStyle%2A> ayarlanır <xref:System.Windows.FontStyles.Normal%2A>.|  
|<xref:System.Drawing.Font.Strikeout%2A>|<xref:System.Windows.TextDecorations> barındırılan|Yalnızca barındırdığında geçerlidir bir <xref:System.Windows.Controls.TextBlock> denetim.|  
|<xref:System.Drawing.Font.Underline%2A>|<xref:System.Windows.TextDecorations> barındırılan|Yalnızca barındırdığında geçerlidir bir <xref:System.Windows.Controls.TextBlock> denetim.|  
|<xref:System.Windows.Forms.Control.RightToLeft%2A><br /><br /> (<xref:System.Windows.Forms.RightToLeft?displayProperty=nameWithType>)|<xref:System.Windows.FrameworkElement.FlowDirection%2A><br /><br /> (<xref:System.Windows.FlowDirection>)|<xref:System.Windows.Forms.RightToLeft.No> eşlendiği <xref:System.Windows.FlowDirection.LeftToRight>.<br /><br /> <xref:System.Windows.Forms.RightToLeft.Yes> eşlendiği <xref:System.Windows.FlowDirection.RightToLeft>.|  
|<xref:System.Windows.Forms.Control.Visible%2A>|<xref:System.Windows.UIElement.Visibility%2A>|<xref:System.Windows.Forms.Integration.ElementHost> Denetleyen ayarlar <xref:System.Windows.UIElement.Visibility%2A> aşağıdaki kuralları kullanarak barındırılan öğesindeki özelliği:<br /><br /> -   <xref:System.Windows.Forms.Control.Visible%2A> = `true` eşlendiği <xref:System.Windows.Visibility.Visible>.<br />-   <xref:System.Windows.Forms.Control.Visible%2A> = `false` eşlendiği <xref:System.Windows.Visibility.Hidden>.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [WPF ve Win32 Birlikte Çalışması](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)  
 [WPF ve Windows Forms Birlikte Çalışması](../../../../docs/framework/wpf/advanced/wpf-and-windows-forms-interoperation.md)  
 [İzlenecek yol: WindowsFormsHost Öğesi Kullanarak Özellikleri Eşleme](../../../../docs/framework/wpf/advanced/walkthrough-mapping-properties-using-the-windowsformshost-element.md)  
 [İzlenecek yol: ElementHost Denetimini Kullanarak Özellikleri Eşleme](../../../../docs/framework/wpf/advanced/walkthrough-mapping-properties-using-the-elementhost-control.md)
