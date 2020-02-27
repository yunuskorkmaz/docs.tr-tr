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
ms.openlocfilehash: e0343b98cb71521b35418e70550a93e0bfe20fa8
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628793"
---
# <a name="walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a>İzlenecek yol: Menü Birleştirme ve ToolStrip Denetimleri ile bir MDI Formu Oluşturma

<xref:System.Windows.Forms?displayProperty=nameWithType> ad alanı birden çok belge arabirimi (MDI) uygulamasını destekler ve <xref:System.Windows.Forms.MenuStrip> denetimi menüyü birleştirmeyi destekler. MDI Forms denetimleri de <xref:System.Windows.Forms.ToolStrip>.

Bu izlenecek yol, <xref:System.Windows.Forms.ToolStripPanel> denetimlerinin MDI formu ile nasıl kullanılacağını gösterir. Form Ayrıca alt menülerle menü birleştirmeyi destekler. Aşağıdaki görevler Bu izlenecek yolda gösterilmektedir:

- Windows Forms projesi oluşturma.

- Formunuz için ana menü oluşturma. Menünün gerçek adı farklılık gösterecektir.

- **Araç kutusuna**<xref:System.Windows.Forms.ToolStripPanel> denetimi ekleme.

- Alt form oluşturma.

- <xref:System.Windows.Forms.ToolStripPanel> denetimleri z düzeninde düzenleme.

İşiniz bittiğinde, menü birleştirme ve taşınabilir <xref:System.Windows.Forms.ToolStrip> denetimlerini destekleyen bir MDI formunuza sahip olursunuz.

Bu konudaki kodu tek bir liste olarak kopyalamak için bkz. [nasıl yapılır: menü birleştirme ve ToolStrip denetimleri Ile MDI formu oluşturma](how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yolu tamamlamak için Visual Studio gerekir.

## <a name="create-the-project"></a>Proje oluşturma

1. Visual Studio 'da, **MDIForm** adlı bir Windows uygulama projesi**oluşturun (** **Visual C#**  veya **Visual Basic** > **Klasik Masaüstü** > Windows Forms **uygulaması** **) > ** ** >  > .**

2. Windows Form Tasarımcısı, formunu seçin.

3. Özellikler penceresi, <xref:System.Windows.Forms.Form.IsMdiContainer%2A> değerini `true`olarak ayarlayın.

## <a name="create-the-main-menu"></a>Ana menüyü oluşturma

Üst MDI formu ana menüyü içerir. Ana menüde **pencere**adlı bir menü öğesi vardır. **Pencere** menü öğesiyle alt formlar oluşturabilirsiniz. Alt formlardan menü öğeleri ana menüde birleştirilir.

1. **Araç kutusundan**bir <xref:System.Windows.Forms.MenuStrip> denetimini form üzerine sürükleyin.

2. <xref:System.Windows.Forms.MenuStrip> denetimine <xref:System.Windows.Forms.ToolStripMenuItem> ekleyin ve **pencereye**adlandırın.

3. <xref:System.Windows.Forms.MenuStrip> denetimini seçin.

4. Özellikler penceresi, <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> özelliğinin değerini `ToolStripMenuItem1`olarak ayarlayın.

5. **Pencere** menü öğesine bir alt öğe ekleyin ve ardından **Yeni**alt öğesi adlandırın.

6. Özellikler penceresi, **Olaylar**' a tıklayın.

7. <xref:System.Windows.Forms.ToolStripItem.Click> olayına çift tıklayın.

     Windows Form Tasarımcısı, <xref:System.Windows.Forms.ToolStripItem.Click> olayı için bir olay işleyicisi oluşturur.

8. Olay işleyicisine aşağıdaki kodu ekleyin.

     [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#2)]

## <a name="add-the-toolstrippanel-control-to-the-toolbox"></a>Araç kutusuna ToolStripPanel denetimini ekleme

MDI formuyla <xref:System.Windows.Forms.MenuStrip> denetimleri kullandığınızda <xref:System.Windows.Forms.ToolStripPanel> denetimine sahip olmanız gerekir. Windows Form Tasarımcısı MDI formunuzu oluşturmak için **araç kutusuna** <xref:System.Windows.Forms.ToolStripPanel> denetimini eklemeniz gerekir.

1. **Araç kutusunu**açın ve kullanılabilir Windows Forms denetimlerini göstermek için **tüm Windows Forms** sekmesine tıklayın.

2. Sağ tıklayarak kısayol menüsünü açın ve **öğeleri seç**' i seçin.

3. **Araç kutusu öğelerini Seç** iletişim kutusunda, **ToolStripPanel**' i bulana kadar **ad** sütununu aşağı kaydırın.

4. **ToolStripPanel**'e göre onay kutusunu seçin ve ardından **Tamam**' a tıklayın.

     <xref:System.Windows.Forms.ToolStripPanel> denetimi **araç kutusunda**görünür.

## <a name="create-a-child-form"></a>Alt form oluşturma

Bu yordamda, kendi <xref:System.Windows.Forms.MenuStrip> denetimine sahip ayrı bir alt form sınıfı tanımlayacaksınız. Bu formun menü öğeleri üst form ile birleştirilir.

1. Projeye `ChildForm` adlı yeni bir form ekleyin.

     Daha fazla bilgi için bkz. [nasıl yapılır: bir projeye Windows Forms ekleme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y2xxdce3(v=vs.100)).

2. **Araç kutusundan**bir <xref:System.Windows.Forms.MenuStrip> denetimini alt form üzerine sürükleyin.

3. <xref:System.Windows.Forms.MenuStrip> denetimin tasarımcı eylemleri glifsimgesine (![küçük siyah ok](./media/designer-actions-glyph.gif)) tıklayın ve ardından **öğeleri Düzenle**' yi seçin.

4. **Öğeler koleksiyonu Düzenleyicisi** iletişim kutusunda alt menüye **ChildMenuItem** adlı yeni bir <xref:System.Windows.Forms.ToolStripMenuItem> ekleyin.

     Daha fazla bilgi için bkz. [ToolStrip öğeleri koleksiyon Düzenleyicisi](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233643(v=vs.100)).

## <a name="test-the-form"></a>Formu test etme

1. Formunuzu derlemek ve çalıştırmak için **F5** tuşuna basın.

2. Menüyü açmak için **pencere** menü öğesine tıklayın ve sonra **Yeni**' ye tıklayın.

     Formun MDI istemci alanında yeni bir alt form oluşturulur. Alt formun menüsü, ana menü ile birleştirilir.

3. Alt formu kapatın.

     Alt formun menüsü, ana menüden kaldırılır.

4. **Yeni** birkaç kez tıklayın.

     <xref:System.Windows.Forms.MenuStrip> denetiminin <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> özelliği atandığından, alt formlar **pencere** menü öğesi altında otomatik olarak listelenir.

## <a name="add-toolstrip-support"></a>ToolStrip desteği ekle

Bu yordamda, MDI parent form 'a dört <xref:System.Windows.Forms.ToolStrip> denetimi ekleyeceksiniz. Her <xref:System.Windows.Forms.ToolStrip> denetimi, formun kenarına yerleştirilen bir <xref:System.Windows.Forms.ToolStripPanel> denetiminin içine eklenir.

1. **Araç kutusundan**bir <xref:System.Windows.Forms.ToolStripPanel> denetimini form üzerine sürükleyin.

2. <xref:System.Windows.Forms.ToolStripPanel> denetimi seçiliyken **araç kutusunda**<xref:System.Windows.Forms.ToolStrip> denetimine çift tıklayın.

     <xref:System.Windows.Forms.ToolStripPanel> denetiminde <xref:System.Windows.Forms.ToolStrip> denetimi oluşturulur.

3. <xref:System.Windows.Forms.ToolStripPanel> denetimini seçin.

4. Özellikler penceresi, denetimin <xref:System.Windows.Forms.Control.Dock%2A> özelliğinin değerini <xref:System.Windows.Forms.DockStyle.Left>olarak değiştirin.

     <xref:System.Windows.Forms.ToolStripPanel> denetim noktaları formun sol tarafına, ana menünün altına göre yapılır. MDI istemci alanı, <xref:System.Windows.Forms.ToolStripPanel> denetimine uyacak şekilde yeniden boyutlandırılır.

5. 1 ile 4 arasındaki adımları tekrarlayın.

     Yeni <xref:System.Windows.Forms.ToolStripPanel> denetimini formun en üstüne yerleştirin.

     <xref:System.Windows.Forms.ToolStripPanel> denetimi ana menünün altına, ancak ilk <xref:System.Windows.Forms.ToolStripPanel> denetiminin sağına yerleştirilir. Bu adımda, <xref:System.Windows.Forms.ToolStripPanel> denetimlerinde doğru şekilde konumlama ile z düzeninin önemi gösterilmektedir.

6. İki <xref:System.Windows.Forms.ToolStripPanel> denetimi için 1 ile 4 arasındaki adımları tekrarlayın.

     Yeni <xref:System.Windows.Forms.ToolStripPanel> denetimlerini formun sağına ve sonuna yerleştirin.

## <a name="arrange-toolstrippanel-controls-by-z-order"></a>ToolStripPanel denetimlerini Z sırasına göre düzenleme

MDI formunuzdaki yerleşik bir <xref:System.Windows.Forms.ToolStripPanel> denetiminin konumu, denetimin z düzeninde bulunduğu konuma göre belirlenir. Belge Anahattı penceresinde, denetimlerinizin z düzenini kolayca düzenleyebilirsiniz.

1. **Görünüm** menüsünde **diğer pencereler**' e ve ardından **Belge Anahattı**' na tıklayın.

     Önceki yordamdan <xref:System.Windows.Forms.ToolStripPanel> denetimlerinizi düzenleme işlemi standart dışı. Bunun nedeni, z düzeninin doğru olmaması. Denetimlerin z düzenini değiştirmek için belge anahattı penceresini kullanın.

2. Belge Anahattı penceresinde **ToolStripPanel4**' yi seçin.

3. **ToolStripPanel4** listenin en altında olana kadar aşağı ok düğmesine tekrar tekrar tıklayın.

     **ToolStripPanel4** denetimi, formun alt kısmına, diğer denetimlerin altına yerleştirilir.

4. **ToolStripPanel2**öğesini seçin.

5. Listeyi listede üçüncü olarak konumlandırmak için aşağı ok düğmesine bir kez tıklayın.

     **ToolStripPanel2** denetimi formun en üstüne, ana menünün altına ve diğer denetimlerin üstüne yerleştirilir.

6. **Belge ana hattı** penceresinde çeşitli denetimler ' i seçin ve z düzeninde farklı konumlara taşıyın. Sabitlenmiş denetimlerin yerleştirilme üzerinde z düzeninin etkisini göz önünde edin. Değişikliklerinizi geri almak için **düzenleme** menüsünde CTRL-Z veya **geri al** komutunu kullanın.

## <a name="checkpoint---test-your-form"></a>Kontrol noktası-formunuzu test etme

1. Formunuzu derlemek ve çalıştırmak için **F5** tuşuna basın.

2. <xref:System.Windows.Forms.ToolStrip> denetimin bir öğesine tıklayın ve denetimi formdaki farklı konumlara sürükleyin.

     Bir <xref:System.Windows.Forms.ToolStrip> denetimini, bir <xref:System.Windows.Forms.ToolStripPanel> denetiminden diğerine sürükleyebilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Bu kılavuzda, <xref:System.Windows.Forms.ToolStrip> denetimleri ve menü birleştirme ile bir MDI parent formu oluşturdunuz. Denetimlerin <xref:System.Windows.Forms.ToolStrip> ailesini birçok farklı amaçla kullanabilirsiniz:

- <xref:System.Windows.Forms.ContextMenuStrip>denetimlerle ilgili kısayol menüleri oluşturun. Daha fazla bilgi için bkz. [ContextMenu bileşenine genel bakış](contextmenu-component-overview-windows-forms.md).

- Otomatik olarak doldurulmuş bir standart menü içeren bir form oluşturuldu. Daha fazla bilgi için bkz. [Izlenecek yol: bir forma standart menü öğeleri sağlama](walkthrough-providing-standard-menu-items-to-a-form.md).

- <xref:System.Windows.Forms.ToolStrip> denetimlerine profesyonel bir görünüm kazandırın. Daha fazla bilgi için bkz. [nasıl yapılır: bir uygulama Için ToolStrip oluşturucuyu ayarlama](how-to-set-the-toolstrip-renderer-for-an-application.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [Nasıl yapılır: MDI Üst Formları Oluşturma](../advanced/how-to-create-mdi-parent-forms.md)
- [Nasıl yapılır: MDI Alt Formları Oluşturma](../advanced/how-to-create-mdi-child-forms.md)
- [Nasıl yapılır: Bir MDI Açılan Menüsüne MenuStrip ekleme](how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms.md)
- [ToolStrip Denetimi](toolstrip-control-windows-forms.md)
