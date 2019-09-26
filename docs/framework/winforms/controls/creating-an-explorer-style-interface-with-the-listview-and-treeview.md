---
title: 'İzlenecek yol: Tasarımcıyı Kullanarak ListView ve TreeView Denetimleri ile Gezgin Stilinde bir Arabirim Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Explorer-style applications [Windows Forms], walkthroughs
- TreeView control [Windows Forms], ListView controls used with
- ListView control [Windows Forms], TreeView controls used with
- Explorer-style applications
- TreeView control [Windows Forms], using for explorer-style interface
- ListView control [Windows Forms], explorer style interface
- ListView control [Windows Forms], explorer-style interface
ms.assetid: 9e5e7721-19e2-4890-b273-a43589fe99ff
ms.openlocfilehash: d80f8e3bc729689b274af520bc37fda8417b0407
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2019
ms.locfileid: "69658577"
---
# <a name="walkthrough-creating-an-explorer-style-interface-with-the-listview-and-treeview-controls-using-the-designer"></a>İzlenecek yol: Tasarımcıyı Kullanarak ListView ve TreeView Denetimleri ile Gezgin Stilinde bir Arabirim Oluşturma

Visual Studio 'nun avantajlarından biri, profesyonel görünümlü Windows Forms uygulamalarını kısa sürede oluşturma olanağıdır. Yaygın bir senaryo, <xref:System.Windows.Forms.ListView> ve <xref:System.Windows.Forms.TreeView> Windows işletim sistemlerinin Windows Gezgini özelliğine benzeyen denetimlerle bir kullanıcı arabirimi (UI) oluşturur. Windows Gezgini, bir kullanıcının bilgisayarındaki dosya ve klasörlerin hiyerarşik yapısını görüntüler.

### <a name="to-create-the-form-containing-a-listview-and-treeview-control"></a>ListView ve TreeView denetimi içeren formu oluşturmak için

1. **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **Proje**' ye tıklayın.

2. **Yeni proje** iletişim kutusunda, şunları yapın:

    1. Kategoriler ' de **Visual Basic** veya **görsel C#** ' i seçin.

    2. Şablon listesinde **Windows Forms uygulama**' yı seçin.

3. **Tamam**'ı tıklatın. Yeni bir Windows Forms projesi oluşturulur.

4. Forma bir <xref:System.Windows.Forms.SplitContainer> denetim ekleyin ve <xref:System.Windows.Forms.SplitContainer.Dock%2A> özelliğini olarak <xref:System.Windows.Forms.DockStyle.Fill>ayarlayın.

5. Forma adlandırılmış <xref:System.Windows.Forms.ImageList> bir `imageList1` ad ekleyin ve iki resim eklemek için Özellikler penceresi kullanın: bir klasör görüntüsü ve bir belge görüntüsü, bu sırada.

6. Forma adlı <xref:System.Windows.Forms.TreeView> `treeview1` bir denetim ekleyin ve <xref:System.Windows.Forms.SplitContainer> denetimin sol tarafında konumlandırın. Özellikler penceresi için `treeView1` aşağıdakileri yapın:

    1. Ayarlama <xref:System.Windows.Forms.Control.Dock%2A> özelliğini <xref:System.Windows.Forms.DockStyle.Fill>.

    2. <xref:System.Windows.Forms.TreeView.ImageList%2A> Özelliğini olarak ayarlayın`imagelist1.`

7. Forma adlı <xref:System.Windows.Forms.ListView> `listView1` bir denetim ekleyin ve <xref:System.Windows.Forms.SplitContainer> denetimin sağ tarafına konumlandırın. Özellikler penceresi için `listview1` aşağıdakileri yapın:

    1. Ayarlama <xref:System.Windows.Forms.Control.Dock%2A> özelliğini <xref:System.Windows.Forms.DockStyle.Fill>.

    2. Ayarlama <xref:System.Windows.Forms.ListView.View%2A> özelliğini <xref:System.Windows.Forms.View.Details>.

    3. Özelliğindeki üç nokta (...) simgesine tıklayarak ColumnHeader koleksiyon düzenleyicisini![açın (Visual Studio 'nun Özellikler penceresi). ](./media/visual-studio-ellipsis-button.png) <xref:System.Windows.Forms.ListView.Columns%2A> <xref:System.Windows.Forms.ColumnHeader.Text%2A> Üç sütun ekleyin ve `Name`özelliğini sırasıyla, `Type`ve `Last Modified`olarak ayarlayın. İletişim kutusunu kapatmak için **Tamam** 'ı tıklatın.

    4. <xref:System.Windows.Forms.ListView.SmallImageList%2A> Özelliğini olarak ayarlayın`imageList1.`

8. Node ve alt düğümlere doldurmak <xref:System.Windows.Forms.TreeView> için kodu uygulayın. Bu kodu `Form1` sınıfına ekleyin.

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#1)]

9. Önceki kod System.IO ad alanını kullandığından, formun üst kısmına uygun using veya import ifadesini ekleyin.

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#4)]

10. Formun Oluşturucusu veya <xref:System.Windows.Forms.Form.Load> olay işleme yönteminde, önceki adımda bulunan kurulum yöntemini çağırın. Form oluşturucusuna bu kodu ekleyin.

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#2)]

11. `listview1` İçin <xref:System.Windows.Forms.TreeView.NodeMouseClick> olayınıişleyinvebirdüğümtıklandığındabirdüğümün`treeview1`içeriğiyle doldurmak için kodu uygulayın. Bu kodu `Form1` sınıfına ekleyin.

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#3)]

     Kullanıyorsanız C#, olay işleme yöntemiyle ilişkili <xref:System.Windows.Forms.TreeView.NodeMouseClick> olayın bulunduğundan emin olun. Form oluşturucusuna bu kodu ekleyin.

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#5)]

## <a name="testing-the-application"></a>Uygulamayı Test Etme

Artık, beklenen şekilde davrandığından emin olmak için formu test edebilirsiniz.

#### <a name="to-test-the-form"></a>Formu test etmek için

- Uygulamayı çalıştırmak için F5'e basın.

     Sol tarafta proje dizininizi görüntüleyen bir <xref:System.Windows.Forms.TreeView> denetim içeren bir bölünmüş form ve sağ tarafta üç sütunlu bir <xref:System.Windows.Forms.ListView> denetim görürsünüz. Dizin düğümlerini seçerek <xref:System.Windows.Forms.ListView> ve <xref:System.Windows.Forms.TreeView> seçilen dizinin içeriğiyle doldurulmuş olarak gezinerek çapraz geçiş yapabilirsiniz.

## <a name="next-steps"></a>Sonraki Adımlar

Bu uygulama, size birlikte kullanabileceğiniz <xref:System.Windows.Forms.TreeView> ve <xref:System.Windows.Forms.ListView> denetimleri kullanabileceğiniz bir yönteme örnek verir. Bu denetimler hakkında daha fazla bilgi için aşağıdaki konulara bakın:

- [Nasıl yapılır: Bir TreeView veya ListView denetimine özel bilgi ekleme (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)

- [Nasıl yapılır: ListView Denetimine arama yetenekleri ekleme](how-to-add-search-capabilities-to-a-listview-control.md)

- [Nasıl yapılır: Bir TreeView düğümüne kısayol menüsü iliştirme](how-to-attach-a-shortcut-menu-to-a-treeview-node.md)

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.TreeView>
- [ListView Denetimi](listview-control-windows-forms.md)
- [Nasıl yapılır: Windows Forms TreeView denetimi ile düğüm ekleme ve kaldırma](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [Nasıl yapılır: Windows Forms ListView denetimiyle öğe ekleme ve kaldırma](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [Nasıl yapılır: Windows Forms ListView Denetimine sütun ekleme](how-to-add-columns-to-the-windows-forms-listview-control.md)
