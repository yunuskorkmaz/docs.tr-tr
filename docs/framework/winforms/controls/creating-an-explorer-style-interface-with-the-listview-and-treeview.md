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
# <a name="walkthrough-creating-an-explorer-style-interface-with-the-listview-and-treeview-controls-using-the-designer"></a><span data-ttu-id="5cd67-103">İzlenecek yol: Tasarımcıyı Kullanarak ListView ve TreeView Denetimleri ile Gezgin Stilinde bir Arabirim Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5cd67-103">Walkthrough: Creating an Explorer Style Interface with the ListView and TreeView Controls Using the Designer</span></span>

<span data-ttu-id="5cd67-104">Visual Studio 'nun avantajlarından biri, profesyonel görünümlü Windows Forms uygulamalarını kısa sürede oluşturma olanağıdır.</span><span class="sxs-lookup"><span data-stu-id="5cd67-104">One of the benefits of Visual Studio is the ability to create professional-looking Windows Forms applications in a short of amount of time.</span></span> <span data-ttu-id="5cd67-105">Yaygın bir senaryo, <xref:System.Windows.Forms.ListView> ve <xref:System.Windows.Forms.TreeView> Windows Işletim sistemlerinin Windows Gezgini özelliğine benzeyen denetimlerle bir kullanıcı ARABIRIMI (UI) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5cd67-105">A common scenario is creating a user interface (UI) with <xref:System.Windows.Forms.ListView> and <xref:System.Windows.Forms.TreeView> controls that resembles the Windows Explorer feature of Windows operating systems.</span></span> <span data-ttu-id="5cd67-106">Windows Gezgini, bir kullanıcının bilgisayarındaki dosya ve klasörlerin hiyerarşik yapısını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="5cd67-106">Windows Explorer displays a hierarchical structure of the files and folders on a user's computer.</span></span>

### <a name="to-create-the-form-containing-a-listview-and-treeview-control"></a><span data-ttu-id="5cd67-107">ListView ve TreeView denetimi içeren formu oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="5cd67-107">To create the form containing a ListView and TreeView control</span></span>

1. <span data-ttu-id="5cd67-108">**Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **Proje**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="5cd67-108">On the **File** menu, point to **New**, and then click **Project**.</span></span>

2. <span data-ttu-id="5cd67-109">**Yeni Proje** iletişim kutusunda aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="5cd67-109">In the **New Project** dialog box, do the following:</span></span>

    1. <span data-ttu-id="5cd67-110">Kategoriler ' de **Visual Basic** veya **Visual C#**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="5cd67-110">In the categories, choose either **Visual Basic** or **Visual C#**.</span></span>

    2. <span data-ttu-id="5cd67-111">Şablon listesinde **Windows Forms uygulama**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="5cd67-111">In the list of templates, choose **Windows Forms Application**.</span></span>

3. <span data-ttu-id="5cd67-112">**Tamam** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="5cd67-112">Click **OK**.</span></span> <span data-ttu-id="5cd67-113">Yeni bir Windows Forms projesi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5cd67-113">A new Windows Forms project is created.</span></span>

4. <span data-ttu-id="5cd67-114">Forma bir <xref:System.Windows.Forms.SplitContainer> denetim ekleyin ve <xref:System.Windows.Forms.SplitContainer.Dock%2A> özelliğini olarak ayarlayın <xref:System.Windows.Forms.DockStyle.Fill> .</span><span class="sxs-lookup"><span data-stu-id="5cd67-114">Add a <xref:System.Windows.Forms.SplitContainer> control to the form and set its <xref:System.Windows.Forms.SplitContainer.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

5. <span data-ttu-id="5cd67-115"><xref:System.Windows.Forms.ImageList>Forma adlandırılmış bir ad ekleyin `imageList1` ve iki resim eklemek için Özellikler penceresi kullanın: bir klasör görüntüsü ve bir belge görüntüsü, bu sırada.</span><span class="sxs-lookup"><span data-stu-id="5cd67-115">Add an <xref:System.Windows.Forms.ImageList> named `imageList1` to the form and use the Properties window to add two images: a folder image and a document image, in that order.</span></span>

6. <span data-ttu-id="5cd67-116"><xref:System.Windows.Forms.TreeView>Forma adlı bir denetim ekleyin `treeview1` ve denetimin sol tarafında konumlandırın <xref:System.Windows.Forms.SplitContainer> .</span><span class="sxs-lookup"><span data-stu-id="5cd67-116">Add a <xref:System.Windows.Forms.TreeView> control named `treeview1` to the form, and position it on the left side of the <xref:System.Windows.Forms.SplitContainer> control.</span></span> <span data-ttu-id="5cd67-117">Özellikler penceresi için `treeView1` aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="5cd67-117">In the Properties window for `treeView1` do the following:</span></span>

    1. <span data-ttu-id="5cd67-118"><xref:System.Windows.Forms.Control.Dock%2A>Özelliğini olarak ayarlayın <xref:System.Windows.Forms.DockStyle.Fill> .</span><span class="sxs-lookup"><span data-stu-id="5cd67-118">Set the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

    2. <span data-ttu-id="5cd67-119"><xref:System.Windows.Forms.TreeView.ImageList%2A>Özelliğini olarak ayarlayın`imagelist1.`</span><span class="sxs-lookup"><span data-stu-id="5cd67-119">Set the <xref:System.Windows.Forms.TreeView.ImageList%2A> property to `imagelist1.`</span></span>

7. <span data-ttu-id="5cd67-120"><xref:System.Windows.Forms.ListView>Forma adlı bir denetim ekleyin `listView1` ve denetimin sağ tarafına konumlandırın <xref:System.Windows.Forms.SplitContainer> .</span><span class="sxs-lookup"><span data-stu-id="5cd67-120">Add a <xref:System.Windows.Forms.ListView> control named `listView1` to the form, and position it on the right side of the <xref:System.Windows.Forms.SplitContainer> control.</span></span> <span data-ttu-id="5cd67-121">Özellikler penceresi için `listview1` aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="5cd67-121">In the Properties window for `listview1` do the following:</span></span>

    1. <span data-ttu-id="5cd67-122"><xref:System.Windows.Forms.Control.Dock%2A>Özelliğini olarak ayarlayın <xref:System.Windows.Forms.DockStyle.Fill> .</span><span class="sxs-lookup"><span data-stu-id="5cd67-122">Set the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

    2. <span data-ttu-id="5cd67-123"><xref:System.Windows.Forms.ListView.View%2A>Özelliğini olarak ayarlayın <xref:System.Windows.Forms.View.Details> .</span><span class="sxs-lookup"><span data-stu-id="5cd67-123">Set the <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Details>.</span></span>

    3. <span data-ttu-id="5cd67-124">Özelliğindeki üç nokta (...) simgesine tıklayarak ColumnHeader koleksiyon düzenleyicisini açın ( ![ Visual Studio 'nun Özellikler penceresi). ](./media/visual-studio-ellipsis-button.png) <xref:System.Windows.Forms.ListView.Columns%2A> **.**</span><span class="sxs-lookup"><span data-stu-id="5cd67-124">Open the ColumnHeader Collection Editor by clicking the ellipses (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) in the <xref:System.Windows.Forms.ListView.Columns%2A> property **.**</span></span> <span data-ttu-id="5cd67-125">Üç sütun ekleyin ve <xref:System.Windows.Forms.ColumnHeader.Text%2A> özelliğini `Name` sırasıyla, ve olarak ayarlayın `Type` `Last Modified` .</span><span class="sxs-lookup"><span data-stu-id="5cd67-125">Add three columns and set their <xref:System.Windows.Forms.ColumnHeader.Text%2A> property to `Name`, `Type`, and `Last Modified`, respectively.</span></span> <span data-ttu-id="5cd67-126">**Tamam**’a tıklayarak iletişim kutusunu kapatın.</span><span class="sxs-lookup"><span data-stu-id="5cd67-126">Click **OK** to close the dialog box.</span></span>

    4. <span data-ttu-id="5cd67-127"><xref:System.Windows.Forms.ListView.SmallImageList%2A>Özelliğini olarak ayarlayın`imageList1.`</span><span class="sxs-lookup"><span data-stu-id="5cd67-127">Set the <xref:System.Windows.Forms.ListView.SmallImageList%2A> property to `imageList1.`</span></span>

8. <span data-ttu-id="5cd67-128">Node ve alt düğümlere doldurmak için kodu uygulayın <xref:System.Windows.Forms.TreeView> .</span><span class="sxs-lookup"><span data-stu-id="5cd67-128">Implement the code to populate the <xref:System.Windows.Forms.TreeView> with nodes and subnodes.</span></span> <span data-ttu-id="5cd67-129">Bu kodu `Form1` sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5cd67-129">Add this code to the `Form1` class.</span></span>

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#1)]

9. <span data-ttu-id="5cd67-130">Önceki kod System.IO ad alanını kullandığından, formun üst kısmına uygun using veya import ifadesini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5cd67-130">Since the previous code uses the System.IO namespace, add the appropriate using or import statement at the top of the form.</span></span>

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#4)]

10. <span data-ttu-id="5cd67-131">Formun Oluşturucusu veya olay işleme yönteminde, önceki adımda bulunan kurulum yöntemini çağırın <xref:System.Windows.Forms.Form.Load> .</span><span class="sxs-lookup"><span data-stu-id="5cd67-131">Call the set-up method from the previous step in the form's constructor or <xref:System.Windows.Forms.Form.Load> event-handling method.</span></span> <span data-ttu-id="5cd67-132">Form oluşturucusuna bu kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5cd67-132">Add this code to the form constructor.</span></span>

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#2)]

11. <span data-ttu-id="5cd67-133"><xref:System.Windows.Forms.TreeView.NodeMouseClick>İçin olayını işleyin `treeview1` **,** ve `listview1` bir düğüm tıklandığında bir düğümün içeriğiyle doldurmak için kodu uygulayın.</span><span class="sxs-lookup"><span data-stu-id="5cd67-133">Handle the <xref:System.Windows.Forms.TreeView.NodeMouseClick> event for `treeview1`**,** and implement the code to populate `listview1` with a node's contents when a node is clicked.</span></span> <span data-ttu-id="5cd67-134">Bu kodu `Form1` sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5cd67-134">Add this code to the `Form1` class.</span></span>

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#3)]

     <span data-ttu-id="5cd67-135">C# kullanıyorsanız, olay <xref:System.Windows.Forms.TreeView.NodeMouseClick> işleme yöntemiyle ilişkili olayın bulunduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="5cd67-135">If you are using C#, make sure you have the <xref:System.Windows.Forms.TreeView.NodeMouseClick> event associated with its event-handling method.</span></span> <span data-ttu-id="5cd67-136">Form oluşturucusuna bu kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5cd67-136">Add this code to the form constructor.</span></span>

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#5)]

## <a name="testing-the-application"></a><span data-ttu-id="5cd67-137">Uygulamayı Test Etme</span><span class="sxs-lookup"><span data-stu-id="5cd67-137">Testing the Application</span></span>

<span data-ttu-id="5cd67-138">Artık, beklenen şekilde davrandığından emin olmak için formu test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5cd67-138">You can now test the form to make sure it behaves as expected.</span></span>

#### <a name="to-test-the-form"></a><span data-ttu-id="5cd67-139">Formu test etmek için</span><span class="sxs-lookup"><span data-stu-id="5cd67-139">To test the form</span></span>

- <span data-ttu-id="5cd67-140">Uygulamayı çalıştırmak için F5'e basın.</span><span class="sxs-lookup"><span data-stu-id="5cd67-140">Press F5 to run the application.</span></span>

     <span data-ttu-id="5cd67-141"><xref:System.Windows.Forms.TreeView>Sol tarafta proje dizininizi görüntüleyen bir denetim içeren bir bölünmüş form ve <xref:System.Windows.Forms.ListView> sağ tarafta üç sütunlu bir denetim görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="5cd67-141">You will see a split form containing a <xref:System.Windows.Forms.TreeView> control that displays your project directory on the left side, and a <xref:System.Windows.Forms.ListView> control on the right side with three columns.</span></span> <span data-ttu-id="5cd67-142"><xref:System.Windows.Forms.TreeView>Dizin düğümlerini seçerek ve <xref:System.Windows.Forms.ListView> Seçilen dizinin içeriğiyle doldurulmuş olarak gezinerek çapraz geçiş yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5cd67-142">You can traverse the <xref:System.Windows.Forms.TreeView> by selecting directory nodes, and the <xref:System.Windows.Forms.ListView> is populated with the contents of the selected directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="5cd67-143">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="5cd67-143">Next Steps</span></span>

<span data-ttu-id="5cd67-144">Bu uygulama, size birlikte kullanabileceğiniz ve denetimleri kullanabileceğiniz bir yönteme örnek <xref:System.Windows.Forms.TreeView> verir <xref:System.Windows.Forms.ListView> .</span><span class="sxs-lookup"><span data-stu-id="5cd67-144">This application gives you an example of a way you can use <xref:System.Windows.Forms.TreeView> and <xref:System.Windows.Forms.ListView> controls together.</span></span> <span data-ttu-id="5cd67-145">Bu denetimler hakkında daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="5cd67-145">For more information on these controls, see the following topics:</span></span>

- [<span data-ttu-id="5cd67-146">Nasıl yapılır: Bir TreeView veya ListView Denetimine Özel Bilgi Ekleme (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="5cd67-146">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)

- [<span data-ttu-id="5cd67-147">Nasıl yapılır: ListView Denetimine Arama Yetenekleri Ekleme</span><span class="sxs-lookup"><span data-stu-id="5cd67-147">How to: Add Search Capabilities to a ListView Control</span></span>](how-to-add-search-capabilities-to-a-listview-control.md)

- [<span data-ttu-id="5cd67-148">Nasıl yapılır: TreeView Düğümüne ShortCut Menüsü Ekleme</span><span class="sxs-lookup"><span data-stu-id="5cd67-148">How to: Attach a ShortCut Menu to a TreeView Node</span></span>](how-to-attach-a-shortcut-menu-to-a-treeview-node.md)

## <a name="see-also"></a><span data-ttu-id="5cd67-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5cd67-149">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.TreeView>
- [<span data-ttu-id="5cd67-150">ListView Denetimi</span><span class="sxs-lookup"><span data-stu-id="5cd67-150">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="5cd67-151">Nasıl yapılır: Windows Forms TreeView Denetimi ile Düğüm Ekleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="5cd67-151">How to: Add and Remove Nodes with the Windows Forms TreeView Control</span></span>](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [<span data-ttu-id="5cd67-152">Nasıl yapılır: Windows Forms ListView Denetimi ile Öğe Ekleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="5cd67-152">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="5cd67-153">Nasıl yapılır: Windows Forms ListView Denetimine Sütun Ekleme</span><span class="sxs-lookup"><span data-stu-id="5cd67-153">How to: Add Columns to the Windows Forms ListView Control</span></span>](how-to-add-columns-to-the-windows-forms-listview-control.md)
