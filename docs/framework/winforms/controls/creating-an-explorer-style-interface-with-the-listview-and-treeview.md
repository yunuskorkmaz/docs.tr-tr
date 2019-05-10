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
ms.openlocfilehash: c8f6e51b5ab8242ba8253a04160c40e59fce0088
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648198"
---
# <a name="walkthrough-creating-an-explorer-style-interface-with-the-listview-and-treeview-controls-using-the-designer"></a>İzlenecek yol: Tasarımcıyı Kullanarak ListView ve TreeView Denetimleri ile Gezgin Stilinde bir Arabirim Oluşturma
Visual Studio'nun avantajlarından biri kısa bir süre, profesyonel görünümlü Windows Forms uygulamaları oluşturmak için olanağıdır. Sık karşılaşılan bir senaryodur ile bir kullanıcı arabirimi (UI) oluşturma <xref:System.Windows.Forms.ListView> ve <xref:System.Windows.Forms.TreeView> Windows işletim sistemlerinin Windows Explorer özelliğine benzer kontrol eder. Windows Gezgini, bir kullanıcının bilgisayarında dosyaları ve klasörleri hiyerarşik yapısını görüntüler.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-create-the-form-containing-a-listview-and-treeview-control"></a>Bir ListView ve TreeView denetimi içeren form oluşturma  
  
1. Üzerinde **dosya** menüsünde **yeni**ve ardından **proje**.  
  
2. İçinde **yeni proje** iletişim kutusunda, aşağıdakileri yapın:  
  
    1. Kategorilerde seçin ya da **Visual Basic** veya **Visual C#**.  
  
    2. Şablonlar listesinde seçin **Windows Forms uygulaması**.  
  
3. **Tamam**'ı tıklatın. Yeni bir Windows Forms projesi oluşturulur.  
  
4. Ekleme bir <xref:System.Windows.Forms.SplitContainer> forma denetim ve ayarlayın, <xref:System.Windows.Forms.SplitContainer.Dock%2A> özelliğini <xref:System.Windows.Forms.DockStyle.Fill>.  
  
5. Ekleme bir <xref:System.Windows.Forms.ImageList> adlı `imageList1` form ve iki görüntü eklemek için Özellikler penceresini kullanabilirsiniz: bir klasör görüntüsü ve o sırada bir belge görüntüsü.  
  
6. Ekleme bir <xref:System.Windows.Forms.TreeView> adlı Denetim `treeview1` forma ve sol tarafında konumlandırın <xref:System.Windows.Forms.SplitContainer> denetimi. Özellikler penceresinde `treeView1` aşağıdakileri yapın:  
  
    1. Ayarlama <xref:System.Windows.Forms.Control.Dock%2A> özelliğini <xref:System.Windows.Forms.DockStyle.Fill>.  
  
    2. Ayarlama <xref:System.Windows.Forms.TreeView.ImageList%2A> özelliği `imagelist1.`  
  
7. Ekleme bir <xref:System.Windows.Forms.ListView> adlı Denetim `listView1` forma ve sağ tarafında konumlandırın <xref:System.Windows.Forms.SplitContainer> denetimi. Özellikler penceresinde `listview1` aşağıdakileri yapın:  
  
    1. Ayarlama <xref:System.Windows.Forms.Control.Dock%2A> özelliğini <xref:System.Windows.Forms.DockStyle.Fill>.  
  
    2. Ayarlama <xref:System.Windows.Forms.ListView.View%2A> özelliğini <xref:System.Windows.Forms.View.Details>.  
  
    3. Üç noktaya tıklayarak ColumnHeader Koleksiyonu Düzenleyicisi'ni açın (![VisualStudioEllipsesButton ekran](../media/vbellipsesbutton.png "vbEllipsesButton")) içinde <xref:System.Windows.Forms.ListView.Columns%2A> özelliği **.** Üç sütun ekleme ve bunların <xref:System.Windows.Forms.ColumnHeader.Text%2A> özelliğini `Name`, `Type`, ve `Last Modified`sırasıyla. İletişim kutusunu kapatmak için **Tamam** 'ı tıklatın.  
  
    4. Ayarlama <xref:System.Windows.Forms.ListView.SmallImageList%2A> özelliği `imageList1.`  
  
8. Doldurmak için kodu Uygula <xref:System.Windows.Forms.TreeView> düğümleri ve alt düğümleri. Bu kodu ekleyin `Form1` sınıfı.  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#1)]  
  
9. Önceki kod System.IO ad alanı kullandığından, uygun kullanarak ekleyebilir veya formun üstünde deyimini içeri aktar.  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#4)]  
  
10. Formun oluşturucuda önceki adımdan Kurulum yöntemi çağırın veya <xref:System.Windows.Forms.Form.Load> olay işleme yöntemi. Bu kod, form oluşturucuyu ekleyin.  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#2)]  
  
11. Tanıtıcı <xref:System.Windows.Forms.TreeView.NodeMouseClick> olayı için `treeview1` **,** ve doldurmak için kodu Uygula `listview1` bir düğüm tıklandığında bir düğümün içeriğe sahip. Bu kodu ekleyin `Form1` sınıfı.  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#3)]  
  
     C# kullanıyorsanız olduğundan emin olun <xref:System.Windows.Forms.TreeView.NodeMouseClick> olay, olay işleme yöntemi ile ilişkili. Bu kod, form oluşturucuyu ekleyin.  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#5)]  
  
## <a name="testing-the-application"></a>Uygulamayı Test Etme  
 Şimdi beklendiği gibi davrandığından emin olmak için form test edebilirsiniz.  
  
#### <a name="to-test-the-form"></a>Formu sınamak için  
  
- Uygulamayı çalıştırmak için F5'e basın.  
  
     Form içeren bir bölme görürsünüz bir <xref:System.Windows.Forms.TreeView> sol tarafta, proje dizinine görüntüleyen denetim ve <xref:System.Windows.Forms.ListView> işlecin sağ tarafındaki üç sütun ile denetimi. Çapraz geçiş yapabilirsiniz <xref:System.Windows.Forms.TreeView> dizin düğümleri seçerek ve <xref:System.Windows.Forms.ListView> seçili dizin içeriğiyle doldurulur.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bu uygulama, örnek olarak kullanabileceğiniz bir yol sunar <xref:System.Windows.Forms.TreeView> ve <xref:System.Windows.Forms.ListView> birlikte denetler. Bu denetimler hakkında daha fazla bilgi için aşağıdaki konulara bakın:  
  
- [Nasıl yapılır: Bir TreeView veya ListView denetimi (Windows Forms) özel bilgi ekleme](add-custom-information-to-a-treeview-or-listview-control-wf.md)  
  
- [Nasıl yapılır: Bir ListView denetimine arama yetenekleri ekleme](how-to-add-search-capabilities-to-a-listview-control.md)  
  
- [Nasıl yapılır: TreeView düğümüne ShortCut menüsü ekleme](how-to-attach-a-shortcut-menu-to-a-treeview-node.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.TreeView>
- [ListView Denetimi](listview-control-windows-forms.md)
- [Nasıl yapılır: Ekleme ve Windows Forms TreeView denetimi ile düğüm kaldırma](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [Nasıl yapılır: Windows Forms ListView denetimi ile öğe ekleyip](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [Nasıl yapılır: Windows Forms ListView denetimine sütun ekleme](how-to-add-columns-to-the-windows-forms-listview-control.md)
