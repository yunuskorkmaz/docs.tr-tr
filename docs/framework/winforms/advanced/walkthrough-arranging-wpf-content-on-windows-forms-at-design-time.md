---
title: "İzlenecek yol: Windows Forms'ta Tasarım Zamanında WPF İçeriğini Düzenleme"
ms.date: 03/30/2017
helpviewer_keywords:
- WPF user control [Windows Forms], hosting in a layout panel
- WPF content [Windows Forms], arranging at design time
- Windows Forms, arranging WPF content at design time
- WPF content [Windows Forms], hosting in Windows Forms
- Windows Forms, anchoring and docking WPF content
- interoperability [WPF]
ms.assetid: 5efb1c53-1484-43d6-aa8a-f4861b99bb8a
ms.openlocfilehash: 373a7f977a9dad59cd40fd29fdd39c8fc6996ad0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529308"
---
# <a name="walkthrough-arranging-wpf-content-on-windows-forms-at-design-time"></a>İzlenecek yol: Windows Forms'ta Tasarım Zamanında WPF İçeriğini Düzenleme
Bu kılavuzda Windows Forms düzeni özellikleri sabitleme ve dayama çizgileri, gibi Windows Presentation Foundation (WPF) denetimlerini düzenlemek için nasıl kullanılacağını gösterir.  
  
 Bu kılavuzda, aşağıdaki görevleri gerçekleştirin:  
  
-   Projesi oluşturun.  
  
-   WPF denetimi oluşturun.  
  
-   Düzen panelinde konak WPF denetimleri.  
  
-   WPF denetimleri hizalamak için kullanım dayama çizgileri.  
  
-   Sabitleme ve yerleştirme WPF denetimleri.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)].  
  
## <a name="creating-the-project"></a>Projeyi Oluşturma  
 Windows Forms projesi oluşturmak için ilk adımdır bakın.  
  
> [!NOTE]
>  WPF içeriği barındırma, yalnızca C# ve Visual Basic projeleri desteklenir.  
  
#### <a name="to-create-the-project"></a>Proje oluşturmak için  
  
-   Visual Basic veya Visual C# adlı yeni bir Windows Forms uygulaması projesi oluşturma `ArrangeElementHost`.  
  
## <a name="creating-the-wpf-control"></a>WPF denetimi oluşturma  
 Projeye bir WPF denetimi ekledikten sonra formdaki düzenleyebilirsiniz.  
  
#### <a name="to-create-wpf-controls"></a>WPF denetimleri oluşturmak için  
  
1.  Yeni bir WPF eklemek <xref:System.Windows.Controls.UserControl> projeye. Denetim türü için varsayılan adı kullanacak `UserControl1.xaml`. Daha fazla bilgi için bkz: [izlenecek yol: oluşturma yeni WPF içeriği Windows formlarında tasarım zamanında](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).  
  
2.  Tasarım görünümü içinde olduğundan emin olun `UserControl1` seçilir. Daha fazla bilgi için bkz: [nasıl yapılır: seçin ve tasarım yüzeyine taşıma öğelerde](http://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474).  
  
3.  İçinde **özellikleri** penceresindeki değerini ayarlayın <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerine `200`.  
  
4.  Değerini <xref:System.Windows.Controls.Control.Background%2A> özelliğine `Blue`.  
  
5.  Projeyi oluşturun.  
  
## <a name="hosting-wpf-controls-in-a-layout-panel"></a>WPF denetimlerini Düzen panelinde barındırma  
 WPF denetimleri Düzen panelleri diğer Windows Forms denetimleri kullandığınız şekilde kullanabilirsiniz.  
  
#### <a name="to-host-wpf-controls-in-a-layout-panel"></a>WPF barındırmak için bir düzen panelinde denetler.  
  
1.  Açık `Form1` Windows Forms Tasarımcısı'nda.  
  
2.  İçinde **araç**, sürükleyin bir <xref:System.Windows.Forms.TableLayoutPanel> forma denetim.  
  
3.  Üzerinde <xref:System.Windows.Forms.TableLayoutPanel> denetimin akıllı etiket paneli, select **son satırı Kaldır**.  
  
4.  Yeniden boyutlandırma <xref:System.Windows.Forms.TableLayoutPanel> denetimine büyük genişlik ve yükseklik.  
  
5.  İçinde **araç**, çift `UserControl1` bir örneğini oluşturmak için `UserControl1` ilk hücrenin <xref:System.Windows.Forms.TableLayoutPanel> denetim.  
  
     Örneğinin `UserControl1` yeni bir barındırılan <xref:System.Windows.Forms.Integration.ElementHost> adlı Denetim `elementHost1`.  
  
6.  İçinde **araç**, çift `UserControl1` ikinci hücresinde başka bir örnek oluşturmak için <xref:System.Windows.Forms.TableLayoutPanel> denetim.  
  
7.  İçinde **belge anahattı** penceresinde, seçin `tableLayoutPanel1`. Daha fazla bilgi için bkz: [Belge Anahattı penceresi](http://msdn.microsoft.com/library/9054f2bc-f6f8-4242-9fe0-be71089b12f8).  
  
8.  İçinde **özellikleri** penceresindeki değerini ayarlayın <xref:System.Windows.Forms.Control.Padding%2A> özelliğine `10, 10, 10, 10`.  
  
     Her ikisi de <xref:System.Windows.Forms.Integration.ElementHost> denetimleri yeni düzen sığması için yeniden boyutlandırılır.  
  
## <a name="using-snaplines-to-align-wpf-controls"></a>Dayama çizgileri kullanarak WPF denetimleri hizalama  
 Dayama çizgileri kolay bir form üzerinde denetimleri hizalama etkinleştirin. Dayama çizgileri WPF denetimleri de hizalamak için kullanabilirsiniz. Daha fazla bilgi için bkz: [izlenecek yol: Windows Forms kullanarak dayama çizgileri düzenleme denetimlerinde](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).  
  
#### <a name="to-use-snaplines-to-align-wpf-controls"></a>Dayama çizgileri WPF hizalamak için kullanmak üzere denetler  
  
1.  Gelen **araç**, bir örneğini sürükleyin `UserControl1` forma ve alanda yerleştirin <xref:System.Windows.Forms.TableLayoutPanel> denetim.  
  
     Örneğinin `UserControl1` yeni bir barındırılan <xref:System.Windows.Forms.Integration.ElementHost> adlı Denetim `elementHost3`.  
  
2.  Dayama çizgileri kullanarak, sol hizalar `elementHost3` sol kenarı ile <xref:System.Windows.Forms.TableLayoutPanel> denetim.  
  
3.  Dayama çizgileri kullanarak, boyut `elementHost3` aynı genişliğe <xref:System.Windows.Forms.TableLayoutPanel> denetim.  
  
4.  Taşıma `elementHost3` doğru <xref:System.Windows.Forms.TableLayoutPanel> merkezi snapline arasında denetimleri görünene kadar denetim.  
  
5.  İçinde **özellikleri** penceresinde ayarlamak için kenar boşluğu özelliğinin değeri `20, 20, 20, 20`.  
  
6.  Taşıma `elementHost3` merkezden <xref:System.Windows.Forms.TableLayoutPanel> merkezi snapline yeniden görünene kadar denetim. Merkezi snapline şimdi 20 kenar boşluğu belirtir.  
  
7.  Taşıma `elementHost3` sol kenarı sol ucuyla hizalar kadar sağa `elementHost1`.  
  
8.  Genişliğini değiştirme `elementHost3` sağ kenarı sağ ucuyla hizalar kadar `elementHost2`.  
  
## <a name="anchoring-and-docking-wpf-controls"></a>Sabitleme ve WPF denetimleri yerleştirme  
 Bir form üzerinde barındırılan bir WPF denetimi aynı sabitleme ve diğer Windows Forms denetimleri davranışı yerleştirme sahiptir.  
  
#### <a name="to-anchor-and-dock-wpf-controls"></a>Sabitleme ve yerleştirme WPF denetimleri için  
  
1.  Seçin `elementHost1`.  
  
2.  İçinde **özellikleri** penceresindeki ayarlayın <xref:System.Windows.Forms.Control.Anchor%2A> özelliğine **üst, alt, sol, sağ**.  
  
3.  Yeniden boyutlandırma <xref:System.Windows.Forms.TableLayoutPanel> daha büyük bir boyuta denetim.  
  
     `elementHost1` Denetimi hücre dolduracak şekilde yeniden boyutlandırır.  
  
4.  Seçin `elementHost2`.  
  
5.  İçinde **özellikleri** penceresindeki değerini ayarlayın <xref:System.Windows.Forms.Control.Dock%2A> özelliğine <xref:System.Windows.Forms.DockStyle.Fill>.  
  
     `elementHost2` Denetimi hücre dolduracak şekilde yeniden boyutlandırır.  
  
6.  Seçin <xref:System.Windows.Forms.TableLayoutPanel> denetim.  
  
7.  Değerini kendi <xref:System.Windows.Forms.Control.Dock%2A> özelliğine <xref:System.Windows.Forms.DockStyle.Top>.  
  
8.  Seçin `elementHost3`.  
  
9. Değerini kendi <xref:System.Windows.Forms.Control.Dock%2A> özelliğine <xref:System.Windows.Forms.DockStyle.Fill>.  
  
     `elementHost3` Denetimi formdaki kalan alanı dolduracak şekilde yeniden boyutlandırır.  
  
10. Formu yeniden boyutlandırın.  
  
     Üç <xref:System.Windows.Forms.Integration.ElementHost> denetimleri uygun şekilde yeniden boyutlandırın.  
  
     Daha fazla bilgi için bkz: [nasıl yapılır: bağlantı ve bir TableLayoutPanel denetiminde alt denetimleri yerleştirme](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Nasıl yapılır: TableLayoutPanel Denetiminde Alt Denetimleri Sabitleme ve Yerleştirme](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [Nasıl yapılır: Tasarım Zamanında Denetimi Formların Kenarlarına Hizalama](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 [İzlenecek yol: Dayama Çizgileri Kullanarak Windows Forms'da Denetimleri Düzenleme](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [Geçiş ve Birlikte Çalışabilirlik](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [WPF Denetimlerini Kullanma](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [WPF Tasarımcısı](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)
