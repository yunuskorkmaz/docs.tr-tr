---
title: "İzlenecek yol: Tasarımcıyı Kullanarak ListView ve TreeView Denetimleri ile Gezgin Stilinde bir Arabirim Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1d8d7991f706f8098e4ac475ae057771de200197
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-creating-an-explorer-style-interface-with-the-listview-and-treeview-controls-using-the-designer"></a><span data-ttu-id="3c48f-102">İzlenecek yol: Tasarımcıyı Kullanarak ListView ve TreeView Denetimleri ile Gezgin Stilinde bir Arabirim Oluşturma</span><span class="sxs-lookup"><span data-stu-id="3c48f-102">Walkthrough: Creating an Explorer Style Interface with the ListView and TreeView Controls Using the Designer</span></span>
<span data-ttu-id="3c48f-103">Visual Studio avantajlarından biri kısa bir süre, profesyonel görünümlü Windows Forms uygulamaları oluşturmak için yeteneğidir.</span><span class="sxs-lookup"><span data-stu-id="3c48f-103">One of the benefits of Visual Studio is the ability to create professional-looking Windows Forms applications in a short of amount of time.</span></span> <span data-ttu-id="3c48f-104">Yaygın bir senaryo, bir kullanıcı arabirimi (UI) ile oluşturuyor <xref:System.Windows.Forms.ListView> ve <xref:System.Windows.Forms.TreeView> Windows işletim sistemlerinin Windows Explorer özelliğine benzer kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="3c48f-104">A common scenario is creating a user interface (UI) with <xref:System.Windows.Forms.ListView> and <xref:System.Windows.Forms.TreeView> controls that resembles the Windows Explorer feature of Windows operating systems.</span></span> <span data-ttu-id="3c48f-105">Windows Gezgini, bir kullanıcının bilgisayarda dosya ve klasörlerin hiyerarşik bir yapı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="3c48f-105">Windows Explorer displays a hierarchical structure of the files and folders on a user's computer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3c48f-106">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="3c48f-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="3c48f-107">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="3c48f-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="3c48f-108">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="3c48f-108">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-create-the-form-containing-a-listview-and-treeview-control"></a><span data-ttu-id="3c48f-109">ListView ve TreeView denetimi içeren form oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="3c48f-109">To create the form containing a ListView and TreeView control</span></span>  
  
1.  <span data-ttu-id="3c48f-110">Üzerinde **dosya** menüsündeki **yeni**ve ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="3c48f-110">On the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="3c48f-111">İçinde **yeni proje** iletişim kutusunda, aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="3c48f-111">In the **New Project** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="3c48f-112">Kategorilerde seçin **Visual Basic** veya **Visual C#**.</span><span class="sxs-lookup"><span data-stu-id="3c48f-112">In the categories, choose either **Visual Basic** or **Visual C#**.</span></span>  
  
    2.  <span data-ttu-id="3c48f-113">Şablonları listesinden seçip **Windows Forms uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="3c48f-113">In the list of templates, choose **Windows Forms Application**.</span></span>  
  
3.  <span data-ttu-id="3c48f-114">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="3c48f-114">Click **OK**.</span></span> <span data-ttu-id="3c48f-115">Yeni bir Windows Forms projesi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3c48f-115">A new Windows Forms project is created.</span></span>  
  
4.  <span data-ttu-id="3c48f-116">Ekleme bir <xref:System.Windows.Forms.SplitContainer> forma denetleyin ve ayarlayın, <xref:System.Windows.Forms.SplitContainer.Dock%2A> özelliğine <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="3c48f-116">Add a <xref:System.Windows.Forms.SplitContainer> control to the form and set its <xref:System.Windows.Forms.SplitContainer.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
5.  <span data-ttu-id="3c48f-117">Ekleme bir <xref:System.Windows.Forms.ImageList> adlı `imageList1` form ve iki görüntü eklemek için Özellikler penceresini kullanın: bir klasör görüntüsü ve o sırada bir belge görüntüsü.</span><span class="sxs-lookup"><span data-stu-id="3c48f-117">Add an <xref:System.Windows.Forms.ImageList> named `imageList1` to the form and use the Properties window to add two images: a folder image and a document image, in that order.</span></span>  
  
6.  <span data-ttu-id="3c48f-118">Ekleme bir <xref:System.Windows.Forms.TreeView> adlı Denetim `treeview1` forma ve sol tarafında Yerleştir <xref:System.Windows.Forms.SplitContainer> denetim.</span><span class="sxs-lookup"><span data-stu-id="3c48f-118">Add a <xref:System.Windows.Forms.TreeView> control named `treeview1` to the form, and position it on the left side of the <xref:System.Windows.Forms.SplitContainer> control.</span></span> <span data-ttu-id="3c48f-119">Özellikler penceresinde `treeView1` aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="3c48f-119">In the Properties window for `treeView1` do the following:</span></span>  
  
    1.  <span data-ttu-id="3c48f-120">Ayarlama <xref:System.Windows.Forms.Control.Dock%2A> özelliğine <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="3c48f-120">Set the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
    2.  <span data-ttu-id="3c48f-121">Ayarlama <xref:System.Windows.Forms.TreeView.ImageList%2A> özelliği`imagelist1.`</span><span class="sxs-lookup"><span data-stu-id="3c48f-121">Set the <xref:System.Windows.Forms.TreeView.ImageList%2A> property to `imagelist1.`</span></span>  
  
7.  <span data-ttu-id="3c48f-122">Ekleme bir <xref:System.Windows.Forms.ListView> adlı Denetim `listView1` forma ve sağ tarafında Yerleştir <xref:System.Windows.Forms.SplitContainer> denetim.</span><span class="sxs-lookup"><span data-stu-id="3c48f-122">Add a <xref:System.Windows.Forms.ListView> control named `listView1` to the form, and position it on the right side of the <xref:System.Windows.Forms.SplitContainer> control.</span></span> <span data-ttu-id="3c48f-123">Özellikler penceresinde `listview1` aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="3c48f-123">In the Properties window for `listview1` do the following:</span></span>  
  
    1.  <span data-ttu-id="3c48f-124">Ayarlama <xref:System.Windows.Forms.Control.Dock%2A> özelliğine <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="3c48f-124">Set the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
    2.  <span data-ttu-id="3c48f-125">Ayarlama <xref:System.Windows.Forms.ListView.View%2A> özelliğine <xref:System.Windows.Forms.View.Details>.</span><span class="sxs-lookup"><span data-stu-id="3c48f-125">Set the <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Details>.</span></span>  
  
    3.  <span data-ttu-id="3c48f-126">Üç nokta düğmesine tıklayarak sütun üstbilgisi Koleksiyonu Düzenleyicisi'ni açın (![VisualStudioEllipsesButton ekran](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) içinde <xref:System.Windows.Forms.ListView.Columns%2A> özelliği**.**</span><span class="sxs-lookup"><span data-stu-id="3c48f-126">Open the ColumnHeader Collection Editor by clicking the ellipses (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) in the <xref:System.Windows.Forms.ListView.Columns%2A> property**.**</span></span> <span data-ttu-id="3c48f-127">Üç sütun ekleyin ve ayarlayın kendi <xref:System.Windows.Forms.ColumnHeader.Text%2A> özelliğine `Name`, `Type`, ve `Last Modified`sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="3c48f-127">Add three columns and set their <xref:System.Windows.Forms.ColumnHeader.Text%2A> property to `Name`, `Type`, and `Last Modified`, respectively.</span></span> <span data-ttu-id="3c48f-128">İletişim kutusunu kapatmak için **Tamam** 'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="3c48f-128">Click **OK** to close the dialog box.</span></span>  
  
    4.  <span data-ttu-id="3c48f-129">Ayarlama <xref:System.Windows.Forms.ListView.SmallImageList%2A> özelliği`imageList1.`</span><span class="sxs-lookup"><span data-stu-id="3c48f-129">Set the <xref:System.Windows.Forms.ListView.SmallImageList%2A> property to `imageList1.`</span></span>  
  
8.  <span data-ttu-id="3c48f-130">Doldurmak için kodu uygulamak <xref:System.Windows.Forms.TreeView> düğümler ve alt düğümleri.</span><span class="sxs-lookup"><span data-stu-id="3c48f-130">Implement the code to populate the <xref:System.Windows.Forms.TreeView> with nodes and subnodes.</span></span> <span data-ttu-id="3c48f-131">Bu kodu ekleyin `Form1` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="3c48f-131">Add this code to the `Form1` class.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#1)]  
  
9. <span data-ttu-id="3c48f-132">Önceki kod System.IO ad kullandığından, uygun kullanma ekleyin veya formun üstünde deyimi alın.</span><span class="sxs-lookup"><span data-stu-id="3c48f-132">Since the previous code uses the System.IO namespace, add the appropriate using or import statement at the top of the form.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#4)]  
  
10. <span data-ttu-id="3c48f-133">Formun Oluşturucusu önceki adımda Kurulum yöntemi çağırmanıza veya <xref:System.Windows.Forms.Form.Load> olay işleme yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3c48f-133">Call the set-up method from the previous step in the form's constructor or <xref:System.Windows.Forms.Form.Load> event-handling method.</span></span> <span data-ttu-id="3c48f-134">Bu kodu form oluşturucu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3c48f-134">Add this code to the form constructor.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#2)]  
  
11. <span data-ttu-id="3c48f-135">İşlemek <xref:System.Windows.Forms.TreeView.NodeMouseClick> olayı için `treeview1` **,** ve doldurmak için kodu uygulamanıza `listview1` bir düğüm tıklatıldığında bir düğümün içeriğe sahip.</span><span class="sxs-lookup"><span data-stu-id="3c48f-135">Handle the <xref:System.Windows.Forms.TreeView.NodeMouseClick> event for `treeview1`**,** and implement the code to populate `listview1` with a node's contents when a node is clicked.</span></span> <span data-ttu-id="3c48f-136">Bu kodu ekleyin `Form1` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="3c48f-136">Add this code to the `Form1` class.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#3)]  
  
     <span data-ttu-id="3c48f-137">C# kullanıyorsanız olduğundan emin olun <xref:System.Windows.Forms.TreeView.NodeMouseClick> kendi olay işleme yöntemiyle ilişkili olay.</span><span class="sxs-lookup"><span data-stu-id="3c48f-137">If you are using C#, make sure you have the <xref:System.Windows.Forms.TreeView.NodeMouseClick> event associated with its event-handling method.</span></span> <span data-ttu-id="3c48f-138">Bu kodu form oluşturucu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3c48f-138">Add this code to the form constructor.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#5)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="3c48f-139">Uygulamayı Test Etme</span><span class="sxs-lookup"><span data-stu-id="3c48f-139">Testing the Application</span></span>  
 <span data-ttu-id="3c48f-140">Artık formun beklendiği gibi davranır emin olmak için test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c48f-140">You can now test the form to make sure it behaves as expected.</span></span>  
  
#### <a name="to-test-the-form"></a><span data-ttu-id="3c48f-141">Formu sınamak için</span><span class="sxs-lookup"><span data-stu-id="3c48f-141">To test the form</span></span>  
  
-   <span data-ttu-id="3c48f-142">Uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="3c48f-142">Press F5 to run the application.</span></span>  
  
     <span data-ttu-id="3c48f-143">Formu içeren bir bölme görürsünüz bir <xref:System.Windows.Forms.TreeView> sol tarafta, proje dizinine görüntüleyen denetim ve <xref:System.Windows.Forms.ListView> üç sütunlarla sağ tarafındaki denetim.</span><span class="sxs-lookup"><span data-stu-id="3c48f-143">You will see a split form containing a <xref:System.Windows.Forms.TreeView> control that displays your project directory on the left side, and a <xref:System.Windows.Forms.ListView> control on the right side with three columns.</span></span> <span data-ttu-id="3c48f-144">Çapraz geçiş yapabileceğini <xref:System.Windows.Forms.TreeView> directory düğümleri seçerek ve <xref:System.Windows.Forms.ListView> seçili dizin içeriğiyle doldurulur.</span><span class="sxs-lookup"><span data-stu-id="3c48f-144">You can traverse the <xref:System.Windows.Forms.TreeView> by selecting directory nodes, and the <xref:System.Windows.Forms.ListView> is populated with the contents of the selected directory.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="3c48f-145">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="3c48f-145">Next Steps</span></span>  
 <span data-ttu-id="3c48f-146">Bu uygulamaya kullanabileceğiniz bir yolunun bir örneği sunar <xref:System.Windows.Forms.TreeView> ve <xref:System.Windows.Forms.ListView> birlikte denetler.</span><span class="sxs-lookup"><span data-stu-id="3c48f-146">This application gives you an example of a way you can use <xref:System.Windows.Forms.TreeView> and <xref:System.Windows.Forms.ListView> controls together.</span></span> <span data-ttu-id="3c48f-147">Bu denetimler hakkında daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="3c48f-147">For more information on these controls, see the following topics:</span></span>  
  
-   [<span data-ttu-id="3c48f-148">Nasıl yapılır: Bir TreeView veya ListView Denetimine Özel Bilgi Ekleme (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="3c48f-148">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)  
  
-   [<span data-ttu-id="3c48f-149">Nasıl yapılır: ListView Denetimine Arama Yetenekleri Ekleme</span><span class="sxs-lookup"><span data-stu-id="3c48f-149">How to: Add Search Capabilities to a ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-search-capabilities-to-a-listview-control.md)  
  
-   [<span data-ttu-id="3c48f-150">Nasıl yapılır: TreeView Düğümüne ShortCut Menüsü Ekleme</span><span class="sxs-lookup"><span data-stu-id="3c48f-150">How to: Attach a ShortCut Menu to a TreeView Node</span></span>](../../../../docs/framework/winforms/controls/how-to-attach-a-shortcut-menu-to-a-treeview-node.md)  
  
## <a name="see-also"></a><span data-ttu-id="3c48f-151">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3c48f-151">See Also</span></span>  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.TreeView>  
 [<span data-ttu-id="3c48f-152">ListView Denetimi</span><span class="sxs-lookup"><span data-stu-id="3c48f-152">ListView Control</span></span>](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [<span data-ttu-id="3c48f-153">Nasıl yapılır: Windows Forms TreeView Denetimi ile Düğüm Ekleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="3c48f-153">How to: Add and Remove Nodes with the Windows Forms TreeView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)  
 [<span data-ttu-id="3c48f-154">Nasıl yapılır: Windows Forms ListView Denetimi ile Öğe Ekleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="3c48f-154">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="3c48f-155">Nasıl yapılır: Windows Forms ListView Denetimine Sütun Ekleme</span><span class="sxs-lookup"><span data-stu-id="3c48f-155">How to: Add Columns to the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)
