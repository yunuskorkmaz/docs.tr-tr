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
ms.openlocfilehash: 124f822aeab25f49cea0ad542497a91a9e2030d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541625"
---
# <a name="walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a>İzlenecek yol: Menü Birleştirme ve ToolStrip Denetimleri ile bir MDI Formu Oluşturma
<xref:System.Windows.Forms?displayProperty=nameWithType> Ad alanı birden çok belge arabirimi (MDI) uygulamaları destekler ve <xref:System.Windows.Forms.MenuStrip> denetimi, menü birleştirme destekler. MDI formları için de <xref:System.Windows.Forms.ToolStrip> kontrol eder.  
  
 Bu kılavuzda nasıl kullanılacağı ortaya <xref:System.Windows.Forms.ToolStripPanel> denetimleriyle MDI formu. Formun alt menüler ile birleştirme menü de destekler. Aşağıdaki görevler bu kılavuzda gösterilmiştir:  
  
-   Windows Forms projesi oluşturma.  
  
-   Formunuz için ana menü oluşturma. Menü gerçek adını değişir.  
  
-   Ekleme <xref:System.Windows.Forms.ToolStripPanel> denetimini **araç**.  
  
-   Alt form oluşturma.  
  
-   Düzenleme <xref:System.Windows.Forms.ToolStripPanel> denetimlerinin z düzeni.  
  
 İşiniz bittiğinde, menü birleştirme ve taşınabilir destekleyen MDI Formu olacaktır <xref:System.Windows.Forms.ToolStrip> kontrol eder.  
  
 Bu konuda tek bir liste olarak kodu kopyalamak için bkz: [nasıl yapılır: menü birleştirme ve ToolStrip denetimleri içeren MDI formu oluşturma](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu kılavuzu tamamlamak için gerekir:  
  
-   Oluşturma ve Windows Forms uygulaması projeleri, Visual Studio yüklü olduğu bilgisayarda çalıştırmak için yeterli izinleri yok.  
  
## <a name="creating-the-project"></a>Projeyi Oluşturma  
 Projeyi oluşturmak ve formu ayarlamak için ilk adımdır bakın.  
  
#### <a name="to-create-the-project"></a>Proje oluşturmak için  
  
1.  Adlı bir Windows uygulaması projesi oluşturduğunuzda **MdiForm**.  
  
     Daha fazla bilgi için bkz: [nasıl yapılır: bir Windows uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  Windows Forms Tasarımcısı'nda formu seçin.  
  
3.  Özellikler penceresinde değerini <xref:System.Windows.Forms.Form.IsMdiContainer%2A> için `true`.  
  
## <a name="creating-the-main-menu"></a>Ana menü oluşturma  
 MDI Formu üst ana menü içerir. Ana menü öğesi adlı bir menü sahip **penceresi**. İle **penceresi** menü öğesi, alt formları oluşturabilirsiniz. Alt formlar menü öğelerinden ana menüye birleştirilir.  
  
#### <a name="to-create-the-main-menu"></a>Ana menü oluşturmak için  
  
1.  Gelen **araç**, sürükleyin bir <xref:System.Windows.Forms.MenuStrip> forma denetim.  
  
2.  Ekleme bir <xref:System.Windows.Forms.ToolStripMenuItem> için <xref:System.Windows.Forms.MenuStrip> denetlemek ve adlandırın **penceresi**.  
  
3.  Seçin <xref:System.Windows.Forms.MenuStrip> denetim.  
  
4.  Özellikler penceresinde değerini <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> özelliğine `ToolStripMenuItem1`.  
  
5.  Bir alt eklemek **penceresi** menü öğesini ve ardından ad alt **yeni**.  
  
6.  Özellikler penceresinde **olayları**.  
  
7.  Çift <xref:System.Windows.Forms.ToolStripItem.Click> olay.  
  
     Windows Form Tasarımcısı için bir olay işleyicisi oluşturur <xref:System.Windows.Forms.ToolStripItem.Click> olay.  
  
8.  Olay işleyicisi aşağıdaki kodu ekleyin.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#2)]  
  
## <a name="adding-the-toolstrippanel-control-to-the-toolbox"></a>ToolStripPanel denetimi araç kutusuna ekleme  
 Kullandığınızda <xref:System.Windows.Forms.MenuStrip> olmalıdır MDI Formu denetimleriyle <xref:System.Windows.Forms.ToolStripPanel> denetim. Eklemelisiniz <xref:System.Windows.Forms.ToolStripPanel> denetimini **araç** Windows Forms Tasarımcısı'nda, MDI formu oluşturmak için.  
  
#### <a name="to-add-the-toolstrippanel-control-to-the-toolbox"></a>ToolStripPanel denetimi araç kutusuna ekleme  
  
1.  Açık **araç**ve ardından **tüm Windows Formları** kullanılabilir Windows Forms denetimleri göstermek için sekmesi.  
  
2.  Kısayol menüsünü açmak için sağ tıklatın ve seçin **öğeleri Seç**.  
  
3.  İçinde **araç kutusu öğelerini Seç** iletişim kutusu, aşağı **adı** bulana kadar sütun **ToolStripPanel**.  
  
4.  Onay kutusunu seçin **ToolStripPanel**ve ardından **Tamam**.  
  
     <xref:System.Windows.Forms.ToolStripPanel> Denetimi görünür **araç**.  
  
## <a name="creating-a-child-form"></a>Alt Form oluşturma  
 Bu yordamda, kendi ayrı alt form sınıfı tanımlayacaksınız <xref:System.Windows.Forms.MenuStrip> denetim. Bu form için menü öğeleri üst formu olanlar birleştirilir.  
  
#### <a name="to-define-a-child-form"></a>Bir alt form tanımlamak için  
  
1.  Adlı yeni bir form ekleme `ChildForm` projeye.  
  
     Daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms projeye eklemek](http://msdn.microsoft.com/library/3d7bb25f-fd90-47cf-9378-fa0d764686c1).  
  
2.  Gelen **araç**, sürükleyin bir <xref:System.Windows.Forms.MenuStrip> alt forma denetim.  
  
3.  Tıklatın <xref:System.Windows.Forms.MenuStrip> denetimin akıllı etiket karakteri (![akıllı etiket karakteri](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) ve ardından **öğe düzenleme**.  
  
4.  İçinde **öğeleri koleksiyonu Düzenleyicisi** iletişim kutusunda, yeni bir ekleme <xref:System.Windows.Forms.ToolStripMenuItem> adlı **ChildMenuItem** alt menüsüne.  
  
     Daha fazla bilgi için bkz: [ToolStrip öğeleri koleksiyonu Düzenleyicisi](http://msdn.microsoft.com/library/e681f3ab-94ba-4b2b-ac64-1dfad46caa25).  
  
## <a name="testing-the-form"></a>Formun test etme  
  
#### <a name="to-test-your-form"></a>Formunuz sınamak için  
  
1.  Derleme ve formunuza çalıştırmak için F5 tuşuna basın.  
  
2.  Tıklatın **penceresi** menüsünü açın ve ardından menü öğesi **yeni**.  
  
     Yeni bir alt form formun MDI istemci alanında oluşturulur. Alt formun menüsünde ana menü ile birleştirilir.  
  
3.  Alt formu kapatın.  
  
     Alt formun menüsünde ana menüden kaldırılır.  
  
4.  Tıklatın **yeni** birkaç kez.  
  
     Alt formları otomatik olarak W altında listelenen**penceresi** menü öğesi için <xref:System.Windows.Forms.MenuStrip> denetimin <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> özelliğine atanır.  
  
## <a name="adding-toolstrip-support"></a>ToolStrip desteği ekleme  
 Bu yordamda, dört ekleyeceksiniz <xref:System.Windows.Forms.ToolStrip> MDI üst formu denetimleri. Her <xref:System.Windows.Forms.ToolStrip> denetimi içinde eklenir bir <xref:System.Windows.Forms.ToolStripPanel> formun kenarına yerleşik denetim.  
  
#### <a name="to-add-toolstrip-controls-to-the-mdi-parent-form"></a>MDI üst forma ToolStrip denetimleri ekleme  
  
1.  Gelen **araç**, sürükleyin bir <xref:System.Windows.Forms.ToolStripPanel> forma denetim.  
  
2.  İle <xref:System.Windows.Forms.ToolStripPanel> denetim seçilen, çift <xref:System.Windows.Forms.ToolStrip> denetim **araç**.  
  
     A <xref:System.Windows.Forms.ToolStrip> denetim oluşturulur <xref:System.Windows.Forms.ToolStripPanel> denetim.  
  
3.  Seçin <xref:System.Windows.Forms.ToolStripPanel> denetim.  
  
4.  Özellikler penceresinde denetimin değerini değiştirmek <xref:System.Windows.Forms.Control.Dock%2A> özelliğine <xref:System.Windows.Forms.DockStyle.Left>.  
  
     <xref:System.Windows.Forms.ToolStripPanel> Kontrol noktalarını formun ana menüye altına sol tarafına. MDI istemci alanını uyacak şekilde yeniden boyutlandırır <xref:System.Windows.Forms.ToolStripPanel> denetim.  
  
5.  1 ile 4 arasındaki adımları yineleyin.  
  
     Yeni yerleştirme <xref:System.Windows.Forms.ToolStripPanel> formun üstünde denetimine.  
  
     <xref:System.Windows.Forms.ToolStripPanel> Denetim ana menü altında ancak ilk sağındaki yerleştirilmiştir <xref:System.Windows.Forms.ToolStripPanel> denetim. Bu adım doğru konumlandırmada z-sırası önemini gösterir <xref:System.Windows.Forms.ToolStripPanel> kontrol eder.  
  
6.  Daha fazla iki için 1-4 arasındaki adımları yineleyin <xref:System.Windows.Forms.ToolStripPanel> kontrol eder.  
  
     Yeni yerleştirme <xref:System.Windows.Forms.ToolStripPanel> formun alt ve sağ denetimleri.  
  
## <a name="arranging-toolstrippanel-controls-by-z-order"></a>Z düzeni tarafından ToolStripPanel denetimleri düzenleme  
 Bir yerleşik konumunu <xref:System.Windows.Forms.ToolStripPanel> MDI formu denetimi z düzenini denetimin konumu tarafından belirlenir. Belge Anahattı penceresi, denetimlerinde z sıralamasını kolayca düzenleyebilirsiniz.  
  
#### <a name="to-arrange-toolstrippanel-controls-by-z-order"></a>Z düzeni tarafından ToolStripPanel denetimlerini düzenlemek için  
  
1.  İçinde **Görünüm** menüsünde tıklatın **diğer pencereler**ve ardından **belge anahattı**.  
  
     Düzenlenmesi, <xref:System.Windows.Forms.ToolStripPanel> denetimleri önceki yordamın standart olmayan. Z düzeni doğru olmadığından budur. Belge Anahattı penceresi denetimlerinin z sıralamasını değiştirmek için kullanın.  
  
2.  Belge Anahattı penceresi seçin **ToolStripPanel4**.  
  
3.  Aşağı ok düğmesine tıklayın kadar sürekli, **ToolStripPanel4** listenin alt kısmında vardır.  
  
     **ToolStripPanel4** denetim, formun diğer denetimleri altına altına yerleştirilmiştir.  
  
4.  Seçin **ToolStripPanel2**.  
  
5.  Aşağı ok düğmesine denetimi üçüncü listede konumlandırmak için bir kez tıklayın.  
  
     **ToolStripPanel2** denetim ana menü altında ve diğer denetimlerin yukarıdaki form üstüne yerleştirilmiştir.  
  
6.  İçindeki çeşitli denetimlerin seçin **belge anahattı** penceresi ve bunları z sırayla farklı konumlara taşıyın. Yerleşik denetimleri yerleştirme z düzenini etkisi unutmayın. CTRL-Z kullanın veya **geri** üzerinde **Düzenle** yaptığınız değişiklikleri geri almak için menüsü.  
  
## <a name="checkpoint"></a>Denetim noktası  
  
#### <a name="to-test-your-form"></a>Formunuz sınamak için  
  
1.  Derleme ve formunuza çalıştırmak için F5 tuşuna basın.  
  
2.  Tutamacı birini tıklatın bir <xref:System.Windows.Forms.ToolStrip> denetlemek ve denetimi form üzerinde farklı konumlara sürükleyin.  
  
     Sürükleyebilirsiniz bir <xref:System.Windows.Forms.ToolStrip> birinden denetim <xref:System.Windows.Forms.ToolStripPanel> başka bir denetim.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bu kılavuzda, MDI üst formu ile oluşturduğunuz <xref:System.Windows.Forms.ToolStrip> denetimleri ve menü birleştirme. Kullanabileceğiniz <xref:System.Windows.Forms.ToolStrip> birçok başka amaçlarla denetimlerin ailesi:  
  
-   İle denetimleri için kısayol menüleri oluşturma <xref:System.Windows.Forms.ContextMenuStrip>. Daha fazla bilgi için bkz: [ContextMenu bileşenine genel bakış](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).  
  
-   Bir form otomatik olarak doldurulan bir standart menüsüyle oluşturulur. Daha fazla bilgi için bkz: [izlenecek yol: bir forma standart menü öğeleri sağlama](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md).  
  
-   Verin, <xref:System.Windows.Forms.ToolStrip> profesyonel görünüm denetler. Daha fazla bilgi için bkz: [nasıl yapılır: bir uygulama için ToolStrip oluşturucusunu ayarlama](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [Nasıl yapılır: MDI Üst Formları Oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [Nasıl yapılır: MDI Alt Formları Oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [Nasıl yapılır: Bir MDI Açılan Menüsüne MenuStrip ekleme](../../../../docs/framework/winforms/controls/how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms.md)  
 [ToolStrip Denetimi](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
