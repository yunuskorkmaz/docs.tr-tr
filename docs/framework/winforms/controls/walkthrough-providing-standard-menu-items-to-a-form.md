---
title: 'İzlenecek yol: Bir Forma Standart Menü Öğeleri Sağlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- menu items [Windows Forms], standard
- toolbars [Windows Forms], walkthroughs
- StatusStrip control [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: dac37d98-589e-4d6d-9673-6437e8943122
ms.openlocfilehash: c0e3a9471afd05ec0e07e8d8a71ffd76c91ec14d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541492"
---
# <a name="walkthrough-providing-standard-menu-items-to-a-form"></a>İzlenecek yol: Bir Forma Standart Menü Öğeleri Sağlama
Formlarınızı ile için standart menü sağlayabilirsiniz <xref:System.Windows.Forms.MenuStrip> denetim.  
  
 Bu kılavuzda nasıl kullanılacağını gösteren bir <xref:System.Windows.Forms.MenuStrip> standart menü oluşturmak için denetim. Bir kullanıcı bir menü öğesi seçtiğinde formun ayrıca yanıt verir. Aşağıdaki görevler bu kılavuzda gösterilmiştir:  
  
-   Windows Forms projesi oluşturma.  
  
-   Standart menü oluşturma.  
  
-   Oluşturma bir <xref:System.Windows.Forms.StatusStrip> denetim.  
  
-   Menü öğesi seçimi işleme.  
  
 İşiniz bittiğinde, menü öğesi seçimleri görüntüleyen bir standart menü ile bir biçimde olacaktır bir <xref:System.Windows.Forms.StatusStrip> denetim.  
  
 Bu konuda tek bir liste olarak kodu kopyalamak için bkz: [nasıl yapılır: bir forma standart menü öğeleri sağlayan](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu kılavuzu tamamlamak için gerekir:  
  
-   Oluşturma ve Windows Forms uygulaması projeleri, Visual Studio yüklü olduğu bilgisayarda çalıştırmak için yeterli izinleri yok.  
  
## <a name="creating-the-project"></a>Projeyi Oluşturma  
 Projeyi oluşturmak ve formu ayarlamak için ilk adımdır bakın.  
  
#### <a name="to-create-the-project"></a>Proje oluşturmak için  
  
1.  Adlı bir Windows uygulaması projesi oluşturduğunuzda **StandardMenuForm**.  
  
     Daha fazla bilgi için bkz: [nasıl yapılır: bir Windows uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  Windows Forms Tasarımcısı'nda formu seçin.  
  
## <a name="creating-a-standard-menu"></a>Standart menü oluşturma  
 Windows Form Tasarımcısı otomatik olarak doldurur bir <xref:System.Windows.Forms.MenuStrip> standart menü öğeleri denetimiyle.  
  
#### <a name="to-create-a-standard-menu"></a>Standart menü oluşturmak için  
  
1.  Gelen **araç**, sürükleyin bir <xref:System.Windows.Forms.MenuStrip> Formunuza denetim.  
  
2.  Tıklatın <xref:System.Windows.Forms.MenuStrip> denetimin akıllı etiket karakteri (![akıllı etiket karakteri](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) seçip **standart öğeleri Ekle**.  
  
     <xref:System.Windows.Forms.MenuStrip> Denetim standart menü öğeleri ile doldurulur.  
  
3.  Tıklatın **dosya** varsayılan menü öğeleri ve ilişkili simgeleri görmek için menü öğesi.  
  
## <a name="creating-a-statusstrip-control"></a>StatusStrip denetimi oluşturma  
 Kullanım <xref:System.Windows.Forms.StatusStrip> Windows Forms uygulamalarının durumunu görüntülemek için denetimi. Menü öğeleri kullanıcı tarafından seçilen görüntülenen geçerli örnekte bir <xref:System.Windows.Forms.StatusStrip> denetim.  
  
#### <a name="to-create-a-statusstrip-control"></a>StatusStrip denetimi oluşturmak için  
  
1.  Gelen **araç**, sürükleyin bir <xref:System.Windows.Forms.StatusStrip> Formunuza denetim.  
  
     <xref:System.Windows.Forms.StatusStrip> Denetimi otomatik olarak noktalarını formun altına.  
  
2.  Tıklatın <xref:System.Windows.Forms.StatusStrip> denetimin açılan düğmesine ve select **StatusLabel'i** eklemek için bir <xref:System.Windows.Forms.ToolStripStatusLabel> denetimini <xref:System.Windows.Forms.StatusStrip> denetim.  
  
## <a name="handling-item-selection"></a>İşleme öğe seçimi  
 Tanıtıcı <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> kullanıcı menü öğesi seçtiğinde yanıt olay.  
  
#### <a name="to-handle-item-selection"></a>Öğe seçimi işlemek için  
  
1.  Tıklatın **dosya** oluşturma oluşturulan menü öğesi bir standart menü bölümü.  
  
2.  İçinde **özellikleri** penceresinde tıklatın **olayları**.  
  
3.  Çift <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> olay.  
  
     Windows Form Tasarımcısı için bir olay işleyicisi oluşturur <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> olay.  
  
4.  Olay işleyicisi aşağıdaki kodu ekleyin.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#3)]  
  
5.  INSERT `UpdateStatus` forma yardımcı yöntem tanımı.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#2)]  
  
## <a name="checkpoint"></a>Denetim noktası  
  
#### <a name="to-test-your-form"></a>Formunuz sınamak için  
  
1.  Derleme ve formunuza çalıştırmak için F5 tuşuna basın.  
  
2.  Tıklatın **dosya** menüsünü açmak için menü öğesi.  
  
3.  Üzerinde **dosya** menüsünde seçmek için öğelerden birini tıklatın.  
  
     <xref:System.Windows.Forms.StatusStrip> Denetimi, seçilen öğeyi görüntüler.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bu kılavuzda, bir forma standart menü ile oluşturdunuz. Kullanabileceğiniz <xref:System.Windows.Forms.ToolStrip> birçok başka amaçlarla denetimlerin ailesi:  
  
-   İle denetimleri için kısayol menüleri oluşturma <xref:System.Windows.Forms.ContextMenuStrip>. Daha fazla bilgi için bkz: [ContextMenu bileşenine genel bakış](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).  
  
-   Yerleştirme ile birden çok belge arabirimi (MDI) form oluşturma <xref:System.Windows.Forms.ToolStrip> kontrol eder. Daha fazla bilgi için bkz: [izlenecek yol: menü birleştirme ve ToolStrip denetimleri içeren MDI formu oluşturma](../../../../docs/framework/winforms/controls/walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).  
  
-   Verin, <xref:System.Windows.Forms.ToolStrip> profesyonel görünüm denetler. Daha fazla bilgi için bkz: [nasıl yapılır: bir uygulama için ToolStrip oluşturucusunu ayarlama](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [MenuStrip Denetimi](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)
