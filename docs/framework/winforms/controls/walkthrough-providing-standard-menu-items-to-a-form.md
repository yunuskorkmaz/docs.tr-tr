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
ms.openlocfilehash: ebfacadfee3ea069359a72ea0402751e9e6280d7
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211513"
---
# <a name="walkthrough-providing-standard-menu-items-to-a-form"></a>İzlenecek yol: Bir Forma Standart Menü Öğeleri Sağlama

Formlarınızla için standart bir menü sağlayabilir <xref:System.Windows.Forms.MenuStrip> denetimi.

Bu izlenecek yolda nasıl kullanılacağını gösterir. bir <xref:System.Windows.Forms.MenuStrip> standart menü oluşturmak için denetimi. Bir kullanıcı bir menü öğesi seçtiğinde, form ayrıca yanıt verir. Aşağıdaki görevler bu kılavuzda gösterilen:

- Bir Windows Forms projesi oluşturma.

- Standart menü oluşturma.

- Oluşturma bir <xref:System.Windows.Forms.StatusStrip> denetimi.

- Menü öğesi seçimi işleme.

İşlemi tamamladığınızda, menü öğesi seçimleri görüntüleyen bir standart menü formla olacaktır bir <xref:System.Windows.Forms.StatusStrip> denetimi.

Bu konudaki tek bir liste olarak kodu kopyalamak için bkz: [nasıl yapılır: Bir forma standart menü öğeleri sağlama](how-to-provide-standard-menu-items-to-a-form.md).

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yolu tamamlamak için Visual Studio gerekir.

## <a name="create-the-project"></a>Projeyi oluşturma

1. Visual Studio'da adlı bir Windows uygulaması projesi oluşturmak **StandardMenuForm** (**dosya** > **yeni** > **proje**   >  **Visual C#**  veya **Visual Basic** > **Klasik Masaüstü**  >  **Windows Forms uygulamalarındaki**).

2. Formu Windows Form Tasarımcısı'nda seçin.

## <a name="create-a-standard-menu"></a>Standart menü oluşturma

Windows Form Tasarımcısı otomatik olarak doldurabilirsiniz bir <xref:System.Windows.Forms.MenuStrip> standart menü öğeleri ile denetimi.

1. Gelen **araç kutusu**, sürükleyin bir <xref:System.Windows.Forms.MenuStrip> denetimi formunuza sürükleyin.

2. Tıklayın <xref:System.Windows.Forms.MenuStrip> denetimin akıllı etiket karakterini (![akıllı etiket karakterini](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) seçip **standart öğeleri Ekle**.

     <xref:System.Windows.Forms.MenuStrip> Denetimi, standart menü öğeleri ile doldurulur.

3. Tıklayın **dosya** kendi varsayılan menü öğeleri ve ilişkili simgeleri görmek için menü öğesi.

## <a name="create-a-statusstrip-control"></a>StatusStrip denetimi oluşturma

Kullanım <xref:System.Windows.Forms.StatusStrip> denetimi Windows Forms uygulamaları için durumu görüntüler. Menü öğeleri, kullanıcı tarafından seçilen görüntülenen geçerli örnekte, bir <xref:System.Windows.Forms.StatusStrip> denetimi.

1. Gelen **araç kutusu**, sürükleyin bir <xref:System.Windows.Forms.StatusStrip> denetimi formunuza sürükleyin.

     <xref:System.Windows.Forms.StatusStrip> Denetimi otomatik olarak noktaları formun altına.

2. Tıklayın <xref:System.Windows.Forms.StatusStrip> denetimin açılan düğmesine ve select **StatusLabel** eklemek için bir <xref:System.Windows.Forms.ToolStripStatusLabel> denetimini <xref:System.Windows.Forms.StatusStrip> denetimi.

## <a name="handle-item-selection"></a>Tanıtıcı öğe seçimi

Tanıtıcı <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> olay kullanıcı menü öğesi seçtiğinde yanıtlayın.

1. Tıklayın **dosya** oluşturma içinde oluşturduğunuz bir menü öğesi bir standart menü bölümü.

2. İçinde **özellikleri** penceresinde tıklayın **olayları**.

3. Çift <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> olay.

     Windows Form Tasarımcısı için bir olay işleyicisi oluşturur <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> olay.

4. Olay işleyicisine aşağıdaki kodu ekleyin.

     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#3)]

5. INSERT `UpdateStatus` forma yardımcı yöntem tanımı.

     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#2)]

## <a name="checkpoint--test-your-form"></a>Checkpoint-formunuza test

1. Tuşuna **F5** derlemek ve formunuza çalıştırmak için.

2. Tıklayın **dosya** menüsünü açmak için menü öğesi.

3. Üzerinde **dosya** menüsünde seçmek için öğelerden birine tıklayın.

     <xref:System.Windows.Forms.StatusStrip> Denetim seçili öğeyi görüntüler.

## <a name="next-steps"></a>Sonraki adımlar

Bu kılavuzda, bir form içeren bir standart menü oluşturdunuz. Kullanabileceğiniz <xref:System.Windows.Forms.ToolStrip> birçok başka amaçlarla denetimlerin ailesi:

- Sahip, denetimler için kısayol menüleri oluşturma <xref:System.Windows.Forms.ContextMenuStrip>. Daha fazla bilgi için [ContextMenu bileşenine genel bakış](contextmenu-component-overview-windows-forms.md).

- Yerleştirme ile birden çok belge arabirimi (MDI) form oluşturma <xref:System.Windows.Forms.ToolStrip> kontrol eder. Daha fazla bilgi için [izlenecek yol: Menü birleştirme ve ToolStrip denetimleri içeren MDI formu oluşturma](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).

- Verin, <xref:System.Windows.Forms.ToolStrip> profesyonel bir görünümünü denetler. Daha fazla bilgi için [nasıl yapılır: Bir uygulama için ToolStrip oluşturucusunu ayarlama](how-to-set-the-toolstrip-renderer-for-an-application.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [MenuStrip Denetimi](menustrip-control-windows-forms.md)
