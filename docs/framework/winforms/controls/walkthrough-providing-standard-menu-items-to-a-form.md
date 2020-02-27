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
ms.openlocfilehash: ee80aad445c00bb4b98b49c80495fa512150bcef
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628780"
---
# <a name="walkthrough-providing-standard-menu-items-to-a-form"></a>İzlenecek yol: Bir Forma Standart Menü Öğeleri Sağlama

<xref:System.Windows.Forms.MenuStrip> denetimi ile formlarınızın standart bir menü sağlayabilirsiniz.

Bu izlenecek yol, bir <xref:System.Windows.Forms.MenuStrip> denetiminin standart bir menü oluşturmak için nasıl kullanılacağını gösterir. Form, bir Kullanıcı bir menü öğesi seçtiğinde da yanıt verir. Aşağıdaki görevler Bu izlenecek yolda gösterilmektedir:

- Windows Forms projesi oluşturma.

- Standart menü oluşturma.

- <xref:System.Windows.Forms.StatusStrip> denetimi oluşturma.

- Menü öğesi seçimini işleme.

İşiniz bittiğinde, bir <xref:System.Windows.Forms.StatusStrip> denetimindeki menü öğesi seçimlerini görüntüleyen standart bir menü içeren bir formunuz olur.

Bu konudaki kodu tek bir liste olarak kopyalamak için bkz. [nasıl yapılır: bir forma standart menü öğeleri sağlama](how-to-provide-standard-menu-items-to-a-form.md).

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yolu tamamlamak için Visual Studio gerekir.

## <a name="create-the-project"></a>Proje oluşturma

1. Visual Studio 'da, **StandardMenuForm** adlı bir Windows **uygulama projesi oluşturun** ** >  > ** ** > (** **Visual C#**  veya **Visual Basic** > **Klasik Masaüstü** > Windows Forms **uygulaması**).

2. Windows Form Tasarımcısı, formunu seçin.

## <a name="create-a-standard-menu"></a>Standart menü oluşturma

Windows Form Tasarımcısı, standart menü öğeleriyle <xref:System.Windows.Forms.MenuStrip> denetimini otomatik olarak doldurabilir.

1. **Araç kutusundan**bir <xref:System.Windows.Forms.MenuStrip> denetimini formunuza sürükleyin.

2. <xref:System.Windows.Forms.MenuStrip> denetimin tasarımcı eylemleri simgesine (![küçük siyah ok](./media/designer-actions-glyph.gif)) tıklayın ve **standart öğeleri ekle**' yi seçin.

     <xref:System.Windows.Forms.MenuStrip> denetim standart menü öğeleriyle doldurulur.

3. Varsayılan menü öğelerini ve bunlara karşılık gelen simgeleri görmek için **Dosya** menü öğesine tıklayın.

## <a name="create-a-statusstrip-control"></a>StatusStrip denetimi oluşturma

Windows Forms uygulamalarınızın durumunu göstermek için <xref:System.Windows.Forms.StatusStrip> denetimini kullanın. Geçerli örnekte, Kullanıcı tarafından seçilen menü öğeleri <xref:System.Windows.Forms.StatusStrip> denetiminde görüntülenir.

1. **Araç kutusundan**bir <xref:System.Windows.Forms.StatusStrip> denetimini formunuza sürükleyin.

     <xref:System.Windows.Forms.StatusStrip> denetimi otomatik olarak formun alt kısmına göre yapılır.

2. <xref:System.Windows.Forms.StatusStrip> denetimine bir <xref:System.Windows.Forms.ToolStripStatusLabel> denetimi eklemek için <xref:System.Windows.Forms.StatusStrip> denetiminin açılan düğmesine tıklayın ve **Statuslabel** ' ı seçin.

## <a name="handle-item-selection"></a>Öğe seçimini işle

Kullanıcı bir menü öğesi seçtiğinde yanıt vermek için <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> olayı işleyin.

1. Standart menü oluşturma bölümünde oluşturduğunuz **Dosya** menü öğesine tıklayın.

2. **Özellikler** penceresinde **Olaylar**' a tıklayın.

3. <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> olayına çift tıklayın.

     Windows Form Tasarımcısı, <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> olayı için bir olay işleyicisi oluşturur.

4. Olay işleyicisine aşağıdaki kodu ekleyin.

     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#3)]

5. `UpdateStatus` yardımcı program yöntemi tanımını forma ekleyin.

     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#2)]

## <a name="checkpoint--test-your-form"></a>Kontrol noktası-formunuzu test etme

1. Formunuzu derlemek ve çalıştırmak için **F5** tuşuna basın.

2. Menüyü açmak için **Dosya** menü öğesine tıklayın.

3. **Dosya** menüsünde, seçmek istediğiniz öğelerden birine tıklayın.

     <xref:System.Windows.Forms.StatusStrip> Denetim seçili öğeyi görüntüler.

## <a name="next-steps"></a>Sonraki adımlar

Bu kılavuzda, standart bir menü içeren bir form oluşturdunuz. Denetimlerin <xref:System.Windows.Forms.ToolStrip> ailesini birçok farklı amaçla kullanabilirsiniz:

- <xref:System.Windows.Forms.ContextMenuStrip>denetimlerle ilgili kısayol menüleri oluşturun. Daha fazla bilgi için bkz. [ContextMenu bileşenine genel bakış](contextmenu-component-overview-windows-forms.md).

- Yerleştirme <xref:System.Windows.Forms.ToolStrip> denetimleri ile birden çok belge arabirimi (MDI) formu oluşturun. Daha fazla bilgi için bkz. [Izlenecek yol: menü birleştirme ve ToolStrip denetimleriyle BIR MDI formu oluşturma](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).

- <xref:System.Windows.Forms.ToolStrip> denetimlerine profesyonel bir görünüm kazandırın. Daha fazla bilgi için bkz. [nasıl yapılır: bir uygulama Için ToolStrip oluşturucuyu ayarlama](how-to-set-the-toolstrip-renderer-for-an-application.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [MenuStrip Denetimi](menustrip-control-windows-forms.md)
