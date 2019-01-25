---
title: "İzlenecek yol: Tasarım zamanında WPF içeriğini Windows Forms'ta düzenleme"
ms.date: 03/30/2017
helpviewer_keywords:
- WPF user control [Windows Forms], hosting in a layout panel
- WPF content [Windows Forms], arranging at design time
- Windows Forms, arranging WPF content at design time
- WPF content [Windows Forms], hosting in Windows Forms
- Windows Forms, anchoring and docking WPF content
- interoperability [WPF]
ms.assetid: 5efb1c53-1484-43d6-aa8a-f4861b99bb8a
ms.openlocfilehash: 66fb814bbf0a40ccaa9339eb24dcc49332861deb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54647678"
---
# <a name="walkthrough-arranging-wpf-content-on-windows-forms-at-design-time"></a>İzlenecek yol: Tasarım zamanında WPF içeriğini Windows Forms'ta düzenleme
Bu izlenecek yol sabitleme ve dayama çizgileri, gibi Windows Forms düzeni özellikleri Windows Presentation Foundation (WPF) denetimleri düzenlemek için nasıl kullanılacağını gösterir.

 Bu kılavuzda, aşağıdaki görevleri gerçekleştirin:

-   Projeyi oluşturun.

-   WPF denetimi oluşturun.

-   Konak WPF denetimleri Düzen paneli içinde.

-   WPF denetimleri hizalama dayama kullanın.

-   Sabitleme ve WPF denetimleri yerleştirme.

> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   Visual Studio 2012.  
  
## <a name="creating-the-project"></a>Projeyi Oluşturma  
 İlk adım Windows Forms projesi oluşturmaktır.  
  
> [!NOTE]
>  WPF içeriği barındırma, yalnızca C# ve Visual Basic projelerinde desteklenir.  
  
#### <a name="to-create-the-project"></a>Proje oluşturmak için  
  
-   Visual Basic veya Visual C# adlı yeni bir Windows Forms uygulaması projesi oluşturma `ArrangeElementHost`.  
  
## <a name="creating-the-wpf-control"></a>WPF denetimi oluşturma  
 Bir WPF denetiminde projeye ekledikten sonra form üzerinde düzenleyebilirsiniz.  
  
#### <a name="to-create-wpf-controls"></a>WPF denetimleri oluşturmak için  
  
1.  Yeni bir WPF ekleme <xref:System.Windows.Controls.UserControl> projeye. Denetim türü için varsayılan adı kullanacak `UserControl1.xaml`. Daha fazla bilgi için [izlenecek yol: Yeni bir WPF içeriği Windows formlarında tasarım zamanında oluşturma](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).  
  
2.  Tasarım görünümünde emin `UserControl1` seçilir. Daha fazla bilgi için [nasıl yapılır: Seçin ve tasarım yüzeyine öğeleri Taşı](https://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474).  
  
3.  İçinde **özellikleri** penceresinde değerini ayarlayın <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerine `200`.  
  
4.  Değerini <xref:System.Windows.Controls.Control.Background%2A> özelliğini `Blue`.  
  
5.  Projeyi oluşturun.  
  
## <a name="hosting-wpf-controls-in-a-layout-panel"></a>Bir düzen paneli içinde WPF denetimleri barındırma  
 Düzen bölmeleri diğer Windows Forms denetimleri kullandığınız aynı şekilde WPF denetimleri kullanabilirsiniz.  
  
#### <a name="to-host-wpf-controls-in-a-layout-panel"></a>WPF barındırmak için bir düzen paneline denetler.  
  
1.  Açık `Form1` Windows Forms Tasarımcısı'nda.  
  
2.  İçinde **araç kutusu**, sürükleyin bir <xref:System.Windows.Forms.TableLayoutPanel> forma denetim.  
  
3.  Üzerinde <xref:System.Windows.Forms.TableLayoutPanel> denetimin akıllı etiket paneli, select **son satırı Kaldır**.  
  
4.  Yeniden boyutlandırma <xref:System.Windows.Forms.TableLayoutPanel> denetimine daha büyük genişliği ve yüksekliği.  
  
5.  İçinde **araç kutusu**, çift `UserControl1` bir örneğini oluşturmak için `UserControl1` ilk hücresindeki <xref:System.Windows.Forms.TableLayoutPanel> denetimi.  
  
     Örneğini `UserControl1` yeni bir barındırılan <xref:System.Windows.Forms.Integration.ElementHost> adlı Denetim `elementHost1`.  
  
6.  İçinde **araç kutusu**, çift `UserControl1` ikinci hücresinde başka bir örneğini oluşturmak için <xref:System.Windows.Forms.TableLayoutPanel> denetimi.  
  
7.  İçinde **belge anahattı** penceresinde `tableLayoutPanel1`. Daha fazla bilgi için [Belge Anahattı penceresi](https://msdn.microsoft.com/library/9054f2bc-f6f8-4242-9fe0-be71089b12f8).  
  
8.  İçinde **özellikleri** penceresinde değerini ayarlayın <xref:System.Windows.Forms.Control.Padding%2A> özelliğini `10, 10, 10, 10`.  
  
     Her ikisi de <xref:System.Windows.Forms.Integration.ElementHost> denetimleri yeni düzene uyacak şekilde yeniden boyutlandırılır.  
  
## <a name="using-snaplines-to-align-wpf-controls"></a>Dayama çizgileri kullanarak WPF denetimleri hizalama  
 Dayama çizgileri kolay bir form üzerinde denetimleri hizalama etkinleştirin. Dayama çizgileri WPF denetimleri de hizalamak için kullanabilirsiniz. Daha fazla bilgi için [izlenecek yol: Forms dayama çizgileri kullanarak Windows denetimleri düzenleme](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).  
  
#### <a name="to-use-snaplines-to-align-wpf-controls"></a>Dayama çizgileri WPF hizalamak için kullanılacağını denetler  
  
1.  Gelen **araç kutusu**, örneği sürükleyin `UserControl1` forma ve alanı yerleştirin <xref:System.Windows.Forms.TableLayoutPanel> denetimi.  
  
     Örneğini `UserControl1` yeni bir barındırılan <xref:System.Windows.Forms.Integration.ElementHost> adlı Denetim `elementHost3`.  
  
2.  Dayama çizgileri kullanarak, sol kenarı hizalama `elementHost3` sol kenarı <xref:System.Windows.Forms.TableLayoutPanel> denetimi.  
  
3.  Dayama çizgileri kullanarak, boyut `elementHost3` aynı genişliğe <xref:System.Windows.Forms.TableLayoutPanel> denetimi.  
  
4.  Taşıma `elementHost3` doğru <xref:System.Windows.Forms.TableLayoutPanel> denetimler arasında merkezi snapline görünene kadar denetim.  
  
5.  İçinde **özellikleri** penceresini ayarlamak için kenar boşluğu özelliğinin değeri `20, 20, 20, 20`.  
  
6.  Taşıma `elementHost3` UZAĞINIZDA <xref:System.Windows.Forms.TableLayoutPanel> merkezi snapline tekrar görünene kadar denetim. Merkezi snapline şimdi 20 kenar boşluğu belirtir.  
  
7.  Taşıma `elementHost3` sol kenarı sol kenarı ile hizalar kadar sağa doğru `elementHost1`.  
  
8.  Genişliğini değiştirme `elementHost3` öğenin sağ kenarı sağ kenarından hizalar kadar `elementHost2`.  
  
## <a name="anchoring-and-docking-wpf-controls"></a>Sabitleme ve yerleştirme WPF denetimleri  
 Bir form üzerinde barındırılan bir WPF denetiminde aynı sabitleme ve diğer Windows Forms denetimleri yerleşik davranışını sahiptir.  
  
#### <a name="to-anchor-and-dock-wpf-controls"></a>Sabitleme ve yerleştirme WPF denetimleri için  
  
1.  `elementHost1` öğesini seçin.  
  
2.  İçinde **özellikleri** penceresinde <xref:System.Windows.Forms.Control.Anchor%2A> özelliğini **üst, alt, sol, sağ**.  
  
3.  Yeniden boyutlandırma <xref:System.Windows.Forms.TableLayoutPanel> daha büyük bir boyuta denetimi.  
  
     `elementHost1` Denetimi hücreyi dolduracak şekilde yeniden boyutlandırır.  
  
4.  `elementHost2` öğesini seçin.  
  
5.  İçinde **özellikleri** penceresinde değerini ayarlayın <xref:System.Windows.Forms.Control.Dock%2A> özelliğini <xref:System.Windows.Forms.DockStyle.Fill>.  
  
     `elementHost2` Denetimi hücreyi dolduracak şekilde yeniden boyutlandırır.  
  
6.  Seçin <xref:System.Windows.Forms.TableLayoutPanel> denetimi.  
  
7.  Değerini kendi <xref:System.Windows.Forms.Control.Dock%2A> özelliğini <xref:System.Windows.Forms.DockStyle.Top>.  
  
8.  `elementHost3` öğesini seçin.  
  
9. Değerini kendi <xref:System.Windows.Forms.Control.Dock%2A> özelliğini <xref:System.Windows.Forms.DockStyle.Fill>.  
  
     `elementHost3` Denetimi form üzerinde kalan alanı dolduracak şekilde yeniden boyutlandırır.  
  
10. Formu yeniden boyutlandırın.  
  
     Üç <xref:System.Windows.Forms.Integration.ElementHost> denetimleri uygun şekilde yeniden boyutlandırın.  
  
     Daha fazla bilgi için [nasıl yapılır: TableLayoutPanel denetiminde alt denetimleri sabitleme ve yerleştirme](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Nasıl yapılır: Sabitleme ve TableLayoutPanel denetiminde alt denetimleri yerleştirme](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [Nasıl yapılır: Tasarım zamanında denetimi formların kenarlarına hizalama](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)
- [İzlenecek yol: Dayama çizgileri kullanarak Windows Forms'da denetimleri düzenleme](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [Geçiş ve Birlikte Çalışabilirlik](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)
- [WPF Denetimlerini Kullanma](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)
- [Visual Studio’da XAML tasarlama](/visualstudio/designers/designing-xaml-in-visual-studio)
