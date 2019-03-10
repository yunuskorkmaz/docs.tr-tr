---
title: 'İzlenecek yol: Bir forma standart menü öğeleri sağlama'
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
ms.openlocfilehash: 846660fda37797e9d53d8f1d5a8a4f812d33e8df
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711765"
---
# <a name="walkthrough-providing-standard-menu-items-to-a-form"></a>İzlenecek yol: Bir forma standart menü öğeleri sağlama
Formlarınızla için standart bir menü sağlayabilir <xref:System.Windows.Forms.MenuStrip> denetimi.  
  
 Bu izlenecek yolda nasıl kullanılacağını gösterir. bir <xref:System.Windows.Forms.MenuStrip> standart menü oluşturmak için denetimi. Bir kullanıcı bir menü öğesi seçtiğinde, form ayrıca yanıt verir. Aşağıdaki görevler bu kılavuzda gösterilen:  
  
-   Bir Windows Forms projesi oluşturma.  
  
-   Standart menü oluşturma.  
  
-   Oluşturma bir <xref:System.Windows.Forms.StatusStrip> denetimi.  
  
-   Menü öğesi seçimi işleme.  
  
 İşlemi tamamladığınızda, menü öğesi seçimleri görüntüleyen bir standart menü formla olacaktır bir <xref:System.Windows.Forms.StatusStrip> denetimi.  
  
 Bu konudaki tek bir liste olarak kodu kopyalamak için bkz: [nasıl yapılır: Bir forma standart menü öğeleri sağlama](how-to-provide-standard-menu-items-to-a-form.md).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için şunlar gerekir:  
  
-   Oluşturma ve Windows Forms application projesi Visual Studio'nun yüklü bilgisayarda çalıştırmak için yeterli izinleri yok.  
  
## <a name="creating-the-project"></a>Projeyi Oluşturma  
 İlk adım projeyi oluşturmak ve formu ayarlamaktır.  
  
#### <a name="to-create-the-project"></a>Proje oluşturmak için  
  
1.  Adlı bir Windows uygulaması projesi oluşturmak **StandardMenuForm** (**dosya** > **yeni** > **proje**  >  **Visual C#** veya **Visual Basic** > **Klasik Masaüstü** > **Windows Forms Uygulama**).  
  
2.  Formu Windows Form Tasarımcısı'nda seçin.  
  
## <a name="creating-a-standard-menu"></a>Standart menü oluşturma  
 Windows Form Tasarımcısı otomatik olarak doldurabilirsiniz bir <xref:System.Windows.Forms.MenuStrip> standart menü öğeleri ile denetimi.  
  
#### <a name="to-create-a-standard-menu"></a>Standart menü oluşturmak için  
  
1.  Gelen **araç kutusu**, sürükleyin bir <xref:System.Windows.Forms.MenuStrip> denetimi formunuza sürükleyin.  
  
2.  Tıklayın <xref:System.Windows.Forms.MenuStrip> denetimin akıllı etiket karakterini (![akıllı etiket karakterini](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) seçip **standart öğeleri Ekle**.  
  
     <xref:System.Windows.Forms.MenuStrip> Denetimi, standart menü öğeleri ile doldurulur.  
  
3.  Tıklayın **dosya** kendi varsayılan menü öğeleri ve ilişkili simgeleri görmek için menü öğesi.  
  
## <a name="creating-a-statusstrip-control"></a>StatusStrip denetimi oluşturma  
 Kullanım <xref:System.Windows.Forms.StatusStrip> denetimi Windows Forms uygulamaları için durumu görüntüler. Menü öğeleri, kullanıcı tarafından seçilen görüntülenen geçerli örnekte, bir <xref:System.Windows.Forms.StatusStrip> denetimi.  
  
#### <a name="to-create-a-statusstrip-control"></a>StatusStrip denetimi oluşturmak için  
  
1.  Gelen **araç kutusu**, sürükleyin bir <xref:System.Windows.Forms.StatusStrip> denetimi formunuza sürükleyin.  
  
     <xref:System.Windows.Forms.StatusStrip> Denetimi otomatik olarak noktaları formun altına.  
  
2.  Tıklayın <xref:System.Windows.Forms.StatusStrip> denetimin açılan düğmesine ve select **StatusLabel** eklemek için bir <xref:System.Windows.Forms.ToolStripStatusLabel> denetimini <xref:System.Windows.Forms.StatusStrip> denetimi.  
  
## <a name="handling-item-selection"></a>İşleme öğe seçimi  
 Tanıtıcı <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> olay kullanıcı menü öğesi seçtiğinde yanıtlayın.  
  
#### <a name="to-handle-item-selection"></a>Öğe seçimi işlemek için  
  
1.  Tıklayın **dosya** oluşturma içinde oluşturduğunuz bir menü öğesi bir standart menü bölümü.  
  
2.  İçinde **özellikleri** penceresinde tıklayın **olayları**.  
  
3.  Çift <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> olay.  
  
     Windows Form Tasarımcısı için bir olay işleyicisi oluşturur <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> olay.  
  
4.  Olay işleyicisine aşağıdaki kodu ekleyin.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#3)]  
  
5.  INSERT `UpdateStatus` forma yardımcı yöntem tanımı.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#2)]  
  
## <a name="checkpoint"></a>Checkpoint  
  
#### <a name="to-test-your-form"></a>Formunuza test etmek için  
  
1.  Derlemek ve formunuza çalıştırmak için F5 tuşuna basın.  
  
2.  Tıklayın **dosya** menüsünü açmak için menü öğesi.  
  
3.  Üzerinde **dosya** menüsünde seçmek için öğelerden birine tıklayın.  
  
     <xref:System.Windows.Forms.StatusStrip> Denetim seçili öğeyi görüntüler.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bu kılavuzda, bir form içeren bir standart menü oluşturdunuz. Kullanabileceğiniz <xref:System.Windows.Forms.ToolStrip> birçok başka amaçlarla denetimlerin ailesi:  
  
-   Sahip, denetimler için kısayol menüleri oluşturma <xref:System.Windows.Forms.ContextMenuStrip>. Daha fazla bilgi için [ContextMenu bileşenine genel bakış](contextmenu-component-overview-windows-forms.md).  
  
-   Yerleştirme ile birden çok belge arabirimi (MDI) form oluşturma <xref:System.Windows.Forms.ToolStrip> kontrol eder. Daha fazla bilgi için [izlenecek yol: Menü birleştirme ve ToolStrip denetimleri içeren MDI formu oluşturma](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).  
  
-   Verin, <xref:System.Windows.Forms.ToolStrip> profesyonel bir görünümünü denetler. Daha fazla bilgi için [nasıl yapılır: Bir uygulama için ToolStrip oluşturucusunu ayarlama](how-to-set-the-toolstrip-renderer-for-an-application.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [MenuStrip Denetimi](menustrip-control-windows-forms.md)
