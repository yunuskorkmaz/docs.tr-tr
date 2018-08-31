---
title: 'İzlenecek yol: Menü Birleştirme ve ToolStrip Denetimleri ile bir MDI Formu Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripPanel control [Windows Forms]
- MDI [Windows Forms], creating forms
- multiple document interface forms
- MDI forms
- ToolStrip control [Windows Forms]
- MDI forms [Windows Forms], creating
- MDI forms [Windows Forms], walkthroughs
ms.assetid: fbab4221-74af-42d0-bbf4-3c97f7b2e544
ms.openlocfilehash: d5fa1ebcc044a18e21e57aa2f66bd8486369fe42
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2018
ms.locfileid: "43255699"
---
# <a name="walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a>İzlenecek yol: Menü Birleştirme ve ToolStrip Denetimleri ile bir MDI Formu Oluşturma
<xref:System.Windows.Forms?displayProperty=nameWithType> Ad alanı birden çok belge arabirimi (MDI) uygulamaları destekler ve <xref:System.Windows.Forms.MenuStrip> denetimi, menü birleştirmeyi destekler. MDI formları aynı zamanda <xref:System.Windows.Forms.ToolStrip> kontrol eder.  
  
 Bu izlenecek yolda nasıl kullanılacağını gösterir <xref:System.Windows.Forms.ToolStripPanel> denetimleriyle MDI formu. Formu ile alt menülerini birleştirme menüsünü de destekler. Aşağıdaki görevler bu kılavuzda gösterilen:  
  
-   Bir Windows Forms projesi oluşturma.  
  
-   Formunuz için ana menü oluşturuluyor. Menü gerçek adıyla değişir.  
  
-   Ekleme <xref:System.Windows.Forms.ToolStripPanel> denetimini **araç kutusu**.  
  
-   Bir alt form oluşturuluyor.  
  
-   Düzenleme <xref:System.Windows.Forms.ToolStripPanel> z sırasına göre denetimler.  
  
 İşlemi tamamladığınızda, menü birleştirme ve taşınabilir destekleyen MDI Formu olacaktır <xref:System.Windows.Forms.ToolStrip> kontrol eder.  
  
 Bu konudaki tek bir liste olarak kodu kopyalamak için bkz: [nasıl yapılır: menü birleştirme ve ToolStrip denetimleri içeren MDI formu oluşturma](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için şunlar gerekir:  
  
-   Oluşturma ve Windows Forms application projesi Visual Studio'nun yüklü bilgisayarda çalıştırmak için yeterli izinleri yok.  
  
## <a name="creating-the-project"></a>Projeyi Oluşturma  
 İlk adım projeyi oluşturmak ve formu ayarlamaktır.  
  
#### <a name="to-create-the-project"></a>Proje oluşturmak için  
  
1.  Adlı bir Windows uygulaması projesi oluşturmak **MdiForm** (**dosya** > **yeni** > **proje**  >  **Visual C#** veya **Visual Basic** > **Klasik Masaüstü** > **Windows Forms uygulamalarındaki**).  
  
2.  Formu Windows Form Tasarımcısı'nda seçin.  
  
3.  Özellikler penceresinde ayarlayın <xref:System.Windows.Forms.Form.IsMdiContainer%2A> için `true`.  
  
## <a name="creating-the-main-menu"></a>Ana menü oluşturma  
 Üst MDI formu ana menü içerir. Ana menü öğesi adlı tek menü sahip **penceresi**. İle **penceresi** menü öğesi alt formları oluşturabilirsiniz. Ana menüye menü öğeleri alt formları birleştirilir.  
  
#### <a name="to-create-the-main-menu"></a>Ana menü oluşturmak için  
  
1.  Gelen **araç kutusu**, sürükleyin bir <xref:System.Windows.Forms.MenuStrip> forma denetim.  
  
2.  Ekleme bir <xref:System.Windows.Forms.ToolStripMenuItem> için <xref:System.Windows.Forms.MenuStrip> denetlemek ve adlandırın **penceresi**.  
  
3.  Seçin <xref:System.Windows.Forms.MenuStrip> denetimi.  
  
4.  Özellikler penceresinde ayarlayın <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> özelliğini `ToolStripMenuItem1`.  
  
5.  Eklemek için bir alt **penceresi** menü öğesini ve ardından ad alt **yeni**.  
  
6.  Özellikler penceresinde tıklayın **olayları**.  
  
7.  Çift <xref:System.Windows.Forms.ToolStripItem.Click> olay.  
  
     Windows Form Tasarımcısı için bir olay işleyicisi oluşturur <xref:System.Windows.Forms.ToolStripItem.Click> olay.  
  
8.  Olay işleyicisine aşağıdaki kodu ekleyin.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#2)]  
  
## <a name="adding-the-toolstrippanel-control-to-the-toolbox"></a>ToolStripPanel denetimi araç kutusuna ekleme  
 Kullanırken <xref:System.Windows.Forms.MenuStrip> denetimleriyle MDI Formu olmalıdır <xref:System.Windows.Forms.ToolStripPanel> denetimi. Eklemelisiniz <xref:System.Windows.Forms.ToolStripPanel> denetimini **araç kutusu** , MDI Formu Windows Form Tasarımcısı'nda oluşturulacak.  
  
#### <a name="to-add-the-toolstrippanel-control-to-the-toolbox"></a>ToolStripPanel denetimi araç kutusuna eklemek için  
  
1.  Açık **araç kutusu**ve ardından **tüm Windows Formları** kullanılabilir Windows Forms denetimleri göstermek için sekmesinde.  
  
2.  Kısayol menüsünü açmak için sağ tıklatın ve seçin **öğelerini Seç**.  
  
3.  İçinde **araç kutusu öğelerini Seç** iletişim kutusu, aşağı kaydırın **adı** bulana kadar sütun **ToolStripPanel**.  
  
4.  Onay kutusunu **ToolStripPanel**ve ardından **Tamam**.  
  
     <xref:System.Windows.Forms.ToolStripPanel> Denetimi görünür **araç kutusu**.  
  
## <a name="creating-a-child-form"></a>Bir alt Form oluşturma  
 Bu yordamda, kendi ayrı bir alt form sınıfı tanımlayacak <xref:System.Windows.Forms.MenuStrip> denetimi. Bu form için menü öğeleri bu üst formu ile birleştirilir.  
  
#### <a name="to-define-a-child-form"></a>Bir alt form tanımlamak için  
  
1.  Adlı yeni bir form ekleyin `ChildForm` projeye.  
  
     Daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms bir proje eklemek](http://msdn.microsoft.com/library/3d7bb25f-fd90-47cf-9378-fa0d764686c1).  
  
2.  Gelen **araç kutusu**, sürükleyin bir <xref:System.Windows.Forms.MenuStrip> alt forma denetim.  
  
3.  Tıklayın <xref:System.Windows.Forms.MenuStrip> denetimin akıllı etiket karakterini (![akıllı etiket karakterini](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) ve ardından **öğe düzenleme**.  
  
4.  İçinde **öğeler Koleksiyonu Düzenleyicisi** iletişim kutusunda, yeni bir <xref:System.Windows.Forms.ToolStripMenuItem> adlı **ChildMenuItem** alt menüsü.  
  
     Daha fazla bilgi için [ToolStrip öğeler Koleksiyonu Düzenleyicisi](http://msdn.microsoft.com/library/e681f3ab-94ba-4b2b-ac64-1dfad46caa25).  
  
## <a name="testing-the-form"></a>Form test etme  
  
#### <a name="to-test-your-form"></a>Formunuza test etmek için  
  
1.  Derlemek ve formunuza çalıştırmak için F5 tuşuna basın.  
  
2.  Tıklayın **penceresi** menüsünü açın ve ardından menü öğesi **yeni**.  
  
     Yeni bir alt form, form denetiminin MDI istemci alanında oluşturulur. Alt formun menüsünde ana menü ile birleştirilir.  
  
3.  Alt formu kapatın.  
  
     Alt formun menüsü, ana menüden kaldırılır.  
  
4.  Tıklayın **yeni** birkaç kez.  
  
     Alt formları otomatik olarak W altında listelenen**pencere** menü öğesi olduğundan <xref:System.Windows.Forms.MenuStrip> denetimin <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> özelliğine atanır.  
  
## <a name="adding-toolstrip-support"></a>ToolStrip desteği ekleme  
 Bu yordamda, dört ekleyeceksiniz <xref:System.Windows.Forms.ToolStrip> MDI üst formu için denetimler. Her <xref:System.Windows.Forms.ToolStrip> denetimi içinde eklenir bir <xref:System.Windows.Forms.ToolStripPanel> form kenarına yerleştirildiğini denetimi.  
  
#### <a name="to-add-toolstrip-controls-to-the-mdi-parent-form"></a>MDI üst formu için ToolStrip denetimleri eklemek için  
  
1.  Gelen **araç kutusu**, sürükleyin bir <xref:System.Windows.Forms.ToolStripPanel> forma denetim.  
  
2.  İle <xref:System.Windows.Forms.ToolStripPanel> çift tıklayın, Denetim seçili <xref:System.Windows.Forms.ToolStrip> denetim **araç kutusu**.  
  
     A <xref:System.Windows.Forms.ToolStrip> denetim oluşturuldu <xref:System.Windows.Forms.ToolStripPanel> denetimi.  
  
3.  Seçin <xref:System.Windows.Forms.ToolStripPanel> denetimi.  
  
4.  Özellikler penceresinde, denetimin değiştirin <xref:System.Windows.Forms.Control.Dock%2A> özelliğini <xref:System.Windows.Forms.DockStyle.Left>.  
  
     <xref:System.Windows.Forms.ToolStripPanel> Kontrol noktalarını sol tarafındaki formun ana menü altında. MDI istemci alanını uyacak şekilde yeniden boyutlandırır <xref:System.Windows.Forms.ToolStripPanel> denetimi.  
  
5.  1 ile 4 arasındaki adımları yineleyin.  
  
     Yeni dock <xref:System.Windows.Forms.ToolStripPanel> üst form denetimi.  
  
     <xref:System.Windows.Forms.ToolStripPanel> Denetim ana menü altında ancak ilk sağındaki yerleştirilmiştir <xref:System.Windows.Forms.ToolStripPanel> denetimi. Bu adım doğru konumlandırmada z düzenini önemini gösterir <xref:System.Windows.Forms.ToolStripPanel> kontrol eder.  
  
6.  Daha fazla iki için 1 ile 4 arasındaki adımları yineleyin <xref:System.Windows.Forms.ToolStripPanel> kontrol eder.  
  
     Yeni dock <xref:System.Windows.Forms.ToolStripPanel> sağa ve formun altına denetimleri.  
  
## <a name="arranging-toolstrippanel-controls-by-z-order"></a>Z sırasına ToolStripPanel denetimleri düzenleme  
 Bir yerleşik konumunu <xref:System.Windows.Forms.ToolStripPanel> , MDI formu denetimi, z düzenini denetimin konumu tarafından belirlenir. Belge Anahattı penceresi içinde denetimlerin z düzenini kolayca düzenleyebilirsiniz.  
  
#### <a name="to-arrange-toolstrippanel-controls-by-z-order"></a>Z düzenini ToolStripPanel denetimleriyle düzenlemek için  
  
1.  İçinde **görünümü** menüsünde tıklatın **diğer Windows**ve ardından **belge anahattı**.  
  
     Düzenlemesini, <xref:System.Windows.Forms.ToolStripPanel> denetimleri önceki yordamın bildiriliyor. Z düzenini doğru olmadığı için budur. Belge Anahattı penceresi denetimlerinin z sıralamasını değiştirmek için kullanın.  
  
2.  Belge Anahattı penceresini seçin **ToolStripPanel4**.  
  
3.  Aşağı ok düğmesini tekrar tekrar kadar **ToolStripPanel4** listesinin alt.  
  
     **ToolStripPanel4** denetim, diğer denetimlerin altında formun altına yerleştirilmiştir.  
  
4.  Seçin **ToolStripPanel2**.  
  
5.  Aşağı ok düğmesini denetimi üçüncü listede konumlandırmak için bir kez tıklayın.  
  
     **ToolStripPanel2** denetimi için ana menü altında ve diğer denetimleri yukarıda formun üst yerleştirilmiştir.  
  
6.  Çeşitli denetimleri seçin **belge anahattı** penceresi ve z düzeninde farklı konumlara taşıyabilirsiniz. Yerleşik denetimler yerleşimini z düzenini etkisini unutmayın. CTRL-Z kullanın veya **geri** üzerinde **Düzenle** değişikliklerinizi geri almak için menü.  
  
## <a name="checkpoint"></a>Denetim noktası  
  
#### <a name="to-test-your-form"></a>Formunuza test etmek için  
  
1.  Derlemek ve formunuza çalıştırmak için F5 tuşuna basın.  
  
2.  Tutamacı tıklayın bir <xref:System.Windows.Forms.ToolStrip> denetlemek ve denetimi form üzerinde farklı konumlara sürükleyin.  
  
     Sürükleyebilirsiniz bir <xref:System.Windows.Forms.ToolStrip> bir denetimden <xref:System.Windows.Forms.ToolStripPanel> başka bir denetim.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bu kılavuzda, MDI üst formu ile oluşturduğunuz <xref:System.Windows.Forms.ToolStrip> denetimleri ve menü birleştirme. Kullanabileceğiniz <xref:System.Windows.Forms.ToolStrip> birçok başka amaçlarla denetimlerin ailesi:  
  
-   Sahip, denetimler için kısayol menüleri oluşturma <xref:System.Windows.Forms.ContextMenuStrip>. Daha fazla bilgi için [ContextMenu bileşenine genel bakış](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).  
  
-   Bir formu otomatik olarak doldurulan bir standart menü ile oluşturuldu. Daha fazla bilgi için [izlenecek yol: bir forma standart menü öğeleri sağlama](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md).  
  
-   Verin, <xref:System.Windows.Forms.ToolStrip> profesyonel bir görünümünü denetler. Daha fazla bilgi için [nasıl yapılır: bir uygulama için ToolStrip oluşturucusunu ayarlama](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [Nasıl yapılır: MDI Üst Formları Oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [Nasıl yapılır: MDI Alt Formları Oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [Nasıl yapılır: Bir MDI Açılan Menüsüne MenuStrip ekleme](../../../../docs/framework/winforms/controls/how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms.md)  
 [ToolStrip Denetimi](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
