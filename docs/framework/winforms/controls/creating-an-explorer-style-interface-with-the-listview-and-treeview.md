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
ms.openlocfilehash: 0a0208194bd6cf24f61c58ece88e41b674e924fc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529214"
---
# <a name="walkthrough-creating-an-explorer-style-interface-with-the-listview-and-treeview-controls-using-the-designer"></a>İzlenecek yol: Tasarımcıyı Kullanarak ListView ve TreeView Denetimleri ile Gezgin Stilinde bir Arabirim Oluşturma
Visual Studio avantajlarından biri kısa bir süre, profesyonel görünümlü Windows Forms uygulamaları oluşturmak için yeteneğidir. Yaygın bir senaryo, bir kullanıcı arabirimi (UI) ile oluşturuyor <xref:System.Windows.Forms.ListView> ve <xref:System.Windows.Forms.TreeView> Windows işletim sistemlerinin Windows Explorer özelliğine benzer kontrol eder. Windows Gezgini, bir kullanıcının bilgisayarda dosya ve klasörlerin hiyerarşik bir yapı görüntüler.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-create-the-form-containing-a-listview-and-treeview-control"></a>ListView ve TreeView denetimi içeren form oluşturmak için  
  
1.  Üzerinde **dosya** menüsündeki **yeni**ve ardından **proje**.  
  
2.  İçinde **yeni proje** iletişim kutusunda, aşağıdakileri yapın:  
  
    1.  Kategorilerde seçin **Visual Basic** veya **Visual C#**.  
  
    2.  Şablonları listesinden seçip **Windows Forms uygulaması**.  
  
3.  **Tamam**'ı tıklatın. Yeni bir Windows Forms projesi oluşturulur.  
  
4.  Ekleme bir <xref:System.Windows.Forms.SplitContainer> forma denetleyin ve ayarlayın, <xref:System.Windows.Forms.SplitContainer.Dock%2A> özelliğine <xref:System.Windows.Forms.DockStyle.Fill>.  
  
5.  Ekleme bir <xref:System.Windows.Forms.ImageList> adlı `imageList1` form ve iki görüntü eklemek için Özellikler penceresini kullanın: bir klasör görüntüsü ve o sırada bir belge görüntüsü.  
  
6.  Ekleme bir <xref:System.Windows.Forms.TreeView> adlı Denetim `treeview1` forma ve sol tarafında Yerleştir <xref:System.Windows.Forms.SplitContainer> denetim. Özellikler penceresinde `treeView1` aşağıdakileri yapın:  
  
    1.  Ayarlama <xref:System.Windows.Forms.Control.Dock%2A> özelliğine <xref:System.Windows.Forms.DockStyle.Fill>.  
  
    2.  Ayarlama <xref:System.Windows.Forms.TreeView.ImageList%2A> özelliği `imagelist1.`  
  
7.  Ekleme bir <xref:System.Windows.Forms.ListView> adlı Denetim `listView1` forma ve sağ tarafında Yerleştir <xref:System.Windows.Forms.SplitContainer> denetim. Özellikler penceresinde `listview1` aşağıdakileri yapın:  
  
    1.  Ayarlama <xref:System.Windows.Forms.Control.Dock%2A> özelliğine <xref:System.Windows.Forms.DockStyle.Fill>.  
  
    2.  Ayarlama <xref:System.Windows.Forms.ListView.View%2A> özelliğine <xref:System.Windows.Forms.View.Details>.  
  
    3.  Üç nokta düğmesine tıklayarak sütun üstbilgisi Koleksiyonu Düzenleyicisi'ni açın (![VisualStudioEllipsesButton ekran](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) içinde <xref:System.Windows.Forms.ListView.Columns%2A> özelliği **.** Üç sütun ekleyin ve ayarlayın kendi <xref:System.Windows.Forms.ColumnHeader.Text%2A> özelliğine `Name`, `Type`, ve `Last Modified`sırasıyla. İletişim kutusunu kapatmak için **Tamam** 'ı tıklatın.  
  
    4.  Ayarlama <xref:System.Windows.Forms.ListView.SmallImageList%2A> özelliği `imageList1.`  
  
8.  Doldurmak için kodu uygulamak <xref:System.Windows.Forms.TreeView> düğümler ve alt düğümleri. Bu kodu ekleyin `Form1` sınıfı.  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#1)]  
  
9. Önceki kod System.IO ad kullandığından, uygun kullanma ekleyin veya formun üstünde deyimi alın.  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#4)]  
  
10. Formun Oluşturucusu önceki adımda Kurulum yöntemi çağırmanıza veya <xref:System.Windows.Forms.Form.Load> olay işleme yöntemi. Bu kodu form oluşturucu ekleyin.  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#2)]  
  
11. İşlemek <xref:System.Windows.Forms.TreeView.NodeMouseClick> olayı için `treeview1` **,** ve doldurmak için kodu uygulamanıza `listview1` bir düğüm tıklatıldığında bir düğümün içeriğe sahip. Bu kodu ekleyin `Form1` sınıfı.  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#3)]  
  
     C# kullanıyorsanız olduğundan emin olun <xref:System.Windows.Forms.TreeView.NodeMouseClick> kendi olay işleme yöntemiyle ilişkili olay. Bu kodu form oluşturucu ekleyin.  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#5)]  
  
## <a name="testing-the-application"></a>Uygulamayı Test Etme  
 Artık formun beklendiği gibi davranır emin olmak için test edebilirsiniz.  
  
#### <a name="to-test-the-form"></a>Formu sınamak için  
  
-   Uygulamayı çalıştırmak için F5 tuşuna basın.  
  
     Formu içeren bir bölme görürsünüz bir <xref:System.Windows.Forms.TreeView> sol tarafta, proje dizinine görüntüleyen denetim ve <xref:System.Windows.Forms.ListView> üç sütunlarla sağ tarafındaki denetim. Çapraz geçiş yapabileceğini <xref:System.Windows.Forms.TreeView> directory düğümleri seçerek ve <xref:System.Windows.Forms.ListView> seçili dizin içeriğiyle doldurulur.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bu uygulamaya kullanabileceğiniz bir yolunun bir örneği sunar <xref:System.Windows.Forms.TreeView> ve <xref:System.Windows.Forms.ListView> birlikte denetler. Bu denetimler hakkında daha fazla bilgi için aşağıdaki konulara bakın:  
  
-   [Nasıl yapılır: Bir TreeView veya ListView Denetimine Özel Bilgi Ekleme (Windows Forms)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)  
  
-   [Nasıl yapılır: ListView Denetimine Arama Yetenekleri Ekleme](../../../../docs/framework/winforms/controls/how-to-add-search-capabilities-to-a-listview-control.md)  
  
-   [Nasıl yapılır: TreeView Düğümüne ShortCut Menüsü Ekleme](../../../../docs/framework/winforms/controls/how-to-attach-a-shortcut-menu-to-a-treeview-node.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.TreeView>  
 [ListView Denetimi](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [Nasıl yapılır: Windows Forms TreeView Denetimi ile Düğüm Ekleme ve Kaldırma](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)  
 [Nasıl yapılır: Windows Forms ListView Denetimi ile Öğe Ekleme ve Kaldırma](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 [Nasıl yapılır: Windows Forms ListView Denetimine Sütun Ekleme](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)
