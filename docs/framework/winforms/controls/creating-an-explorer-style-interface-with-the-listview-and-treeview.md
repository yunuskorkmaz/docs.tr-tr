---
title: 'İzlenecek yol: Tasarımcıyı Kullanarak ListView ve TreeView Denetimleri ile Gezgin Stilinde bir Arabirim Oluşturma'
description: Tasarımcıyı kullanarak Windows Forms ListView ve TreeView denetimleriyle bir gezgin stili arabirim oluşturmayı öğrenin.
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
ms.openlocfilehash: 44d4db1ef3da85dbf411498f486882b86a05c140
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174633"
---
# <a name="walkthrough-creating-an-explorer-style-interface-with-the-listview-and-treeview-controls-using-the-designer"></a>İzlenecek yol: Tasarımcıyı Kullanarak ListView ve TreeView Denetimleri ile Gezgin Stilinde bir Arabirim Oluşturma

Visual Studio 'nun avantajlarından biri, profesyonel görünümlü Windows Forms uygulamalarını kısa sürede oluşturma olanağıdır. Yaygın bir senaryo, <xref:System.Windows.Forms.ListView> ve <xref:System.Windows.Forms.TreeView> Windows Işletim sistemlerinin Windows Gezgini özelliğine benzeyen denetimlerle bir kullanıcı ARABIRIMI (UI) oluşturur. Windows Gezgini, bir kullanıcının bilgisayarındaki dosya ve klasörlerin hiyerarşik yapısını görüntüler.

### <a name="to-create-the-form-containing-a-listview-and-treeview-control"></a>ListView ve TreeView denetimi içeren formu oluşturmak için

1. **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **Proje**' ye tıklayın.

2. **Yeni Proje** iletişim kutusunda aşağıdakileri yapın:

    1. Kategoriler ' de **Visual Basic** veya **Visual C#**' yi seçin.

    2. Şablon listesinde **Windows Forms uygulama**' yı seçin.

3. **Tamam** düğmesine tıklayın. Yeni bir Windows Forms projesi oluşturulur.

4. Forma bir <xref:System.Windows.Forms.SplitContainer> denetim ekleyin ve <xref:System.Windows.Forms.SplitContainer.Dock%2A> özelliğini olarak ayarlayın <xref:System.Windows.Forms.DockStyle.Fill> .

5. <xref:System.Windows.Forms.ImageList>Forma adlandırılmış bir ad ekleyin `imageList1` ve iki resim eklemek için Özellikler penceresi kullanın: bir klasör görüntüsü ve bir belge görüntüsü, bu sırada.

6. <xref:System.Windows.Forms.TreeView>Forma adlı bir denetim ekleyin `treeview1` ve denetimin sol tarafında konumlandırın <xref:System.Windows.Forms.SplitContainer> . Özellikler penceresi için `treeView1` aşağıdakileri yapın:

    1. <xref:System.Windows.Forms.Control.Dock%2A>Özelliğini olarak ayarlayın <xref:System.Windows.Forms.DockStyle.Fill> .

    2. <xref:System.Windows.Forms.TreeView.ImageList%2A>Özelliğini olarak ayarlayın`imagelist1.`

7. <xref:System.Windows.Forms.ListView>Forma adlı bir denetim ekleyin `listView1` ve denetimin sağ tarafına konumlandırın <xref:System.Windows.Forms.SplitContainer> . Özellikler penceresi için `listview1` aşağıdakileri yapın:

    1. <xref:System.Windows.Forms.Control.Dock%2A>Özelliğini olarak ayarlayın <xref:System.Windows.Forms.DockStyle.Fill> .

    2. <xref:System.Windows.Forms.ListView.View%2A>Özelliğini olarak ayarlayın <xref:System.Windows.Forms.View.Details> .

    3. Özelliğindeki üç nokta (...) simgesine tıklayarak ColumnHeader koleksiyon düzenleyicisini açın ( ![ Visual Studio 'nun Özellikler penceresi). ](./media/visual-studio-ellipsis-button.png) <xref:System.Windows.Forms.ListView.Columns%2A> **.** Üç sütun ekleyin ve <xref:System.Windows.Forms.ColumnHeader.Text%2A> özelliğini `Name` sırasıyla, ve olarak ayarlayın `Type` `Last Modified` . **Tamam**’a tıklayarak iletişim kutusunu kapatın.

    4. <xref:System.Windows.Forms.ListView.SmallImageList%2A>Özelliğini olarak ayarlayın`imageList1.`

8. Node ve alt düğümlere doldurmak için kodu uygulayın <xref:System.Windows.Forms.TreeView> . Bu kodu `Form1` sınıfına ekleyin.

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#1)]

9. Önceki kod System.IO ad alanını kullandığından, formun üst kısmına uygun using veya import ifadesini ekleyin.

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#4)]

10. Formun Oluşturucusu veya olay işleme yönteminde, önceki adımda bulunan kurulum yöntemini çağırın <xref:System.Windows.Forms.Form.Load> . Form oluşturucusuna bu kodu ekleyin.

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#2)]

11. <xref:System.Windows.Forms.TreeView.NodeMouseClick>İçin olayını işleyin `treeview1` **,** ve `listview1` bir düğüm tıklandığında bir düğümün içeriğiyle doldurmak için kodu uygulayın. Bu kodu `Form1` sınıfına ekleyin.

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#3)]

     C# kullanıyorsanız, olay <xref:System.Windows.Forms.TreeView.NodeMouseClick> işleme yöntemiyle ilişkili olayın bulunduğundan emin olun. Form oluşturucusuna bu kodu ekleyin.

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#5)]

## <a name="testing-the-application"></a>Uygulamayı Test Etme

Artık, beklenen şekilde davrandığından emin olmak için formu test edebilirsiniz.

#### <a name="to-test-the-form"></a>Formu test etmek için

- Uygulamayı çalıştırmak için F5'e basın.

     <xref:System.Windows.Forms.TreeView>Sol tarafta proje dizininizi görüntüleyen bir denetim içeren bir bölünmüş form ve <xref:System.Windows.Forms.ListView> sağ tarafta üç sütunlu bir denetim görürsünüz. <xref:System.Windows.Forms.TreeView>Dizin düğümlerini seçerek ve <xref:System.Windows.Forms.ListView> Seçilen dizinin içeriğiyle doldurulmuş olarak gezinerek çapraz geçiş yapabilirsiniz.

## <a name="next-steps"></a>Sonraki Adımlar

Bu uygulama, size birlikte kullanabileceğiniz ve denetimleri kullanabileceğiniz bir yönteme örnek <xref:System.Windows.Forms.TreeView> verir <xref:System.Windows.Forms.ListView> . Bu denetimler hakkında daha fazla bilgi için aşağıdaki konulara bakın:

- [Nasıl yapılır: Bir TreeView veya ListView Denetimine Özel Bilgi Ekleme (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)

- [Nasıl yapılır: ListView Denetimine Arama Yetenekleri Ekleme](how-to-add-search-capabilities-to-a-listview-control.md)

- [Nasıl yapılır: TreeView Düğümüne ShortCut Menüsü Ekleme](how-to-attach-a-shortcut-menu-to-a-treeview-node.md)

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.TreeView>
- [ListView Denetimi](listview-control-windows-forms.md)
- [Nasıl yapılır: Windows Forms TreeView Denetimi ile Düğüm Ekleme ve Kaldırma](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [Nasıl yapılır: Windows Forms ListView Denetimi ile Öğe Ekleme ve Kaldırma](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [Nasıl yapılır: Windows Forms ListView Denetimine Sütun Ekleme](how-to-add-columns-to-the-windows-forms-listview-control.md)
