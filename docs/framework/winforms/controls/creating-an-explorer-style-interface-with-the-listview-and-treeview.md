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
# <a name="walkthrough-creating-an-explorer-style-interface-with-the-listview-and-treeview-controls-using-the-designer"></a><span data-ttu-id="4c028-102">İzlenecek yol: Tasarımcıyı Kullanarak ListView ve TreeView Denetimleri ile Gezgin Stilinde bir Arabirim Oluşturma</span><span class="sxs-lookup"><span data-stu-id="4c028-102">Walkthrough: Creating an Explorer Style Interface with the ListView and TreeView Controls Using the Designer</span></span>

<span data-ttu-id="4c028-103">Visual Studio 'nun avantajlarından biri, profesyonel görünümlü Windows Forms uygulamalarını kısa sürede oluşturma olanağıdır.</span><span class="sxs-lookup"><span data-stu-id="4c028-103">One of the benefits of Visual Studio is the ability to create professional-looking Windows Forms applications in a short of amount of time.</span></span> <span data-ttu-id="4c028-104">Yaygın bir senaryo, <xref:System.Windows.Forms.ListView> ve <xref:System.Windows.Forms.TreeView> Windows işletim sistemlerinin Windows Gezgini özelliğine benzeyen denetimlerle bir kullanıcı arabirimi (UI) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4c028-104">A common scenario is creating a user interface (UI) with <xref:System.Windows.Forms.ListView> and <xref:System.Windows.Forms.TreeView> controls that resembles the Windows Explorer feature of Windows operating systems.</span></span> <span data-ttu-id="4c028-105">Windows Gezgini, bir kullanıcının bilgisayarındaki dosya ve klasörlerin hiyerarşik yapısını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="4c028-105">Windows Explorer displays a hierarchical structure of the files and folders on a user's computer.</span></span>

### <a name="to-create-the-form-containing-a-listview-and-treeview-control"></a><span data-ttu-id="4c028-106">ListView ve TreeView denetimi içeren formu oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="4c028-106">To create the form containing a ListView and TreeView control</span></span>

1. <span data-ttu-id="4c028-107">**Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **Proje**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4c028-107">On the **File** menu, point to **New**, and then click **Project**.</span></span>

2. <span data-ttu-id="4c028-108">**Yeni proje** iletişim kutusunda, şunları yapın:</span><span class="sxs-lookup"><span data-stu-id="4c028-108">In the **New Project** dialog box, do the following:</span></span>

    1. <span data-ttu-id="4c028-109">Kategoriler ' de **Visual Basic** veya **görsel C#** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="4c028-109">In the categories, choose either **Visual Basic** or **Visual C#**.</span></span>

    2. <span data-ttu-id="4c028-110">Şablon listesinde **Windows Forms uygulama**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="4c028-110">In the list of templates, choose **Windows Forms Application**.</span></span>

3. <span data-ttu-id="4c028-111">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="4c028-111">Click **OK**.</span></span> <span data-ttu-id="4c028-112">Yeni bir Windows Forms projesi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="4c028-112">A new Windows Forms project is created.</span></span>

4. <span data-ttu-id="4c028-113">Forma bir <xref:System.Windows.Forms.SplitContainer> denetim ekleyin ve <xref:System.Windows.Forms.SplitContainer.Dock%2A> özelliğini olarak <xref:System.Windows.Forms.DockStyle.Fill>ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4c028-113">Add a <xref:System.Windows.Forms.SplitContainer> control to the form and set its <xref:System.Windows.Forms.SplitContainer.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

5. <span data-ttu-id="4c028-114">Forma adlandırılmış <xref:System.Windows.Forms.ImageList> bir `imageList1` ad ekleyin ve iki resim eklemek için Özellikler penceresi kullanın: bir klasör görüntüsü ve bir belge görüntüsü, bu sırada.</span><span class="sxs-lookup"><span data-stu-id="4c028-114">Add an <xref:System.Windows.Forms.ImageList> named `imageList1` to the form and use the Properties window to add two images: a folder image and a document image, in that order.</span></span>

6. <span data-ttu-id="4c028-115">Forma adlı <xref:System.Windows.Forms.TreeView> `treeview1` bir denetim ekleyin ve <xref:System.Windows.Forms.SplitContainer> denetimin sol tarafında konumlandırın.</span><span class="sxs-lookup"><span data-stu-id="4c028-115">Add a <xref:System.Windows.Forms.TreeView> control named `treeview1` to the form, and position it on the left side of the <xref:System.Windows.Forms.SplitContainer> control.</span></span> <span data-ttu-id="4c028-116">Özellikler penceresi için `treeView1` aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="4c028-116">In the Properties window for `treeView1` do the following:</span></span>

    1. <span data-ttu-id="4c028-117">Ayarlama <xref:System.Windows.Forms.Control.Dock%2A> özelliğini <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="4c028-117">Set the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

    2. <span data-ttu-id="4c028-118"><xref:System.Windows.Forms.TreeView.ImageList%2A> Özelliğini olarak ayarlayın`imagelist1.`</span><span class="sxs-lookup"><span data-stu-id="4c028-118">Set the <xref:System.Windows.Forms.TreeView.ImageList%2A> property to `imagelist1.`</span></span>

7. <span data-ttu-id="4c028-119">Forma adlı <xref:System.Windows.Forms.ListView> `listView1` bir denetim ekleyin ve <xref:System.Windows.Forms.SplitContainer> denetimin sağ tarafına konumlandırın.</span><span class="sxs-lookup"><span data-stu-id="4c028-119">Add a <xref:System.Windows.Forms.ListView> control named `listView1` to the form, and position it on the right side of the <xref:System.Windows.Forms.SplitContainer> control.</span></span> <span data-ttu-id="4c028-120">Özellikler penceresi için `listview1` aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="4c028-120">In the Properties window for `listview1` do the following:</span></span>

    1. <span data-ttu-id="4c028-121">Ayarlama <xref:System.Windows.Forms.Control.Dock%2A> özelliğini <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="4c028-121">Set the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

    2. <span data-ttu-id="4c028-122">Ayarlama <xref:System.Windows.Forms.ListView.View%2A> özelliğini <xref:System.Windows.Forms.View.Details>.</span><span class="sxs-lookup"><span data-stu-id="4c028-122">Set the <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Details>.</span></span>

    3. <span data-ttu-id="4c028-123">Özelliğindeki üç nokta (...) simgesine tıklayarak ColumnHeader koleksiyon düzenleyicisini![açın (Visual Studio 'nun Özellikler penceresi). ](./media/visual-studio-ellipsis-button.png) <xref:System.Windows.Forms.ListView.Columns%2A></span><span class="sxs-lookup"><span data-stu-id="4c028-123">Open the ColumnHeader Collection Editor by clicking the ellipses (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) in the <xref:System.Windows.Forms.ListView.Columns%2A> property **.**</span></span> <span data-ttu-id="4c028-124"><xref:System.Windows.Forms.ColumnHeader.Text%2A> Üç sütun ekleyin ve `Name`özelliğini sırasıyla, `Type`ve `Last Modified`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4c028-124">Add three columns and set their <xref:System.Windows.Forms.ColumnHeader.Text%2A> property to `Name`, `Type`, and `Last Modified`, respectively.</span></span> <span data-ttu-id="4c028-125">İletişim kutusunu kapatmak için **Tamam** 'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="4c028-125">Click **OK** to close the dialog box.</span></span>

    4. <span data-ttu-id="4c028-126"><xref:System.Windows.Forms.ListView.SmallImageList%2A> Özelliğini olarak ayarlayın`imageList1.`</span><span class="sxs-lookup"><span data-stu-id="4c028-126">Set the <xref:System.Windows.Forms.ListView.SmallImageList%2A> property to `imageList1.`</span></span>

8. <span data-ttu-id="4c028-127">Node ve alt düğümlere doldurmak <xref:System.Windows.Forms.TreeView> için kodu uygulayın.</span><span class="sxs-lookup"><span data-stu-id="4c028-127">Implement the code to populate the <xref:System.Windows.Forms.TreeView> with nodes and subnodes.</span></span> <span data-ttu-id="4c028-128">Bu kodu `Form1` sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4c028-128">Add this code to the `Form1` class.</span></span>

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#1)]

9. <span data-ttu-id="4c028-129">Önceki kod System.IO ad alanını kullandığından, formun üst kısmına uygun using veya import ifadesini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4c028-129">Since the previous code uses the System.IO namespace, add the appropriate using or import statement at the top of the form.</span></span>

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#4)]

10. <span data-ttu-id="4c028-130">Formun Oluşturucusu veya <xref:System.Windows.Forms.Form.Load> olay işleme yönteminde, önceki adımda bulunan kurulum yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="4c028-130">Call the set-up method from the previous step in the form's constructor or <xref:System.Windows.Forms.Form.Load> event-handling method.</span></span> <span data-ttu-id="4c028-131">Form oluşturucusuna bu kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4c028-131">Add this code to the form constructor.</span></span>

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#2)]

11. <span data-ttu-id="4c028-132">`listview1` İçin <xref:System.Windows.Forms.TreeView.NodeMouseClick> olayınıişleyinvebirdüğümtıklandığındabirdüğümün`treeview1`içeriğiyle doldurmak için kodu uygulayın.</span><span class="sxs-lookup"><span data-stu-id="4c028-132">Handle the <xref:System.Windows.Forms.TreeView.NodeMouseClick> event for `treeview1`**,** and implement the code to populate `listview1` with a node's contents when a node is clicked.</span></span> <span data-ttu-id="4c028-133">Bu kodu `Form1` sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4c028-133">Add this code to the `Form1` class.</span></span>

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#3)]

     <span data-ttu-id="4c028-134">Kullanıyorsanız C#, olay işleme yöntemiyle ilişkili <xref:System.Windows.Forms.TreeView.NodeMouseClick> olayın bulunduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="4c028-134">If you are using C#, make sure you have the <xref:System.Windows.Forms.TreeView.NodeMouseClick> event associated with its event-handling method.</span></span> <span data-ttu-id="4c028-135">Form oluşturucusuna bu kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4c028-135">Add this code to the form constructor.</span></span>

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#5)]

## <a name="testing-the-application"></a><span data-ttu-id="4c028-136">Uygulamayı Test Etme</span><span class="sxs-lookup"><span data-stu-id="4c028-136">Testing the Application</span></span>

<span data-ttu-id="4c028-137">Artık, beklenen şekilde davrandığından emin olmak için formu test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c028-137">You can now test the form to make sure it behaves as expected.</span></span>

#### <a name="to-test-the-form"></a><span data-ttu-id="4c028-138">Formu test etmek için</span><span class="sxs-lookup"><span data-stu-id="4c028-138">To test the form</span></span>

- <span data-ttu-id="4c028-139">Uygulamayı çalıştırmak için F5'e basın.</span><span class="sxs-lookup"><span data-stu-id="4c028-139">Press F5 to run the application.</span></span>

     <span data-ttu-id="4c028-140">Sol tarafta proje dizininizi görüntüleyen bir <xref:System.Windows.Forms.TreeView> denetim içeren bir bölünmüş form ve sağ tarafta üç sütunlu bir <xref:System.Windows.Forms.ListView> denetim görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="4c028-140">You will see a split form containing a <xref:System.Windows.Forms.TreeView> control that displays your project directory on the left side, and a <xref:System.Windows.Forms.ListView> control on the right side with three columns.</span></span> <span data-ttu-id="4c028-141">Dizin düğümlerini seçerek <xref:System.Windows.Forms.ListView> ve <xref:System.Windows.Forms.TreeView> seçilen dizinin içeriğiyle doldurulmuş olarak gezinerek çapraz geçiş yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c028-141">You can traverse the <xref:System.Windows.Forms.TreeView> by selecting directory nodes, and the <xref:System.Windows.Forms.ListView> is populated with the contents of the selected directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4c028-142">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="4c028-142">Next Steps</span></span>

<span data-ttu-id="4c028-143">Bu uygulama, size birlikte kullanabileceğiniz <xref:System.Windows.Forms.TreeView> ve <xref:System.Windows.Forms.ListView> denetimleri kullanabileceğiniz bir yönteme örnek verir.</span><span class="sxs-lookup"><span data-stu-id="4c028-143">This application gives you an example of a way you can use <xref:System.Windows.Forms.TreeView> and <xref:System.Windows.Forms.ListView> controls together.</span></span> <span data-ttu-id="4c028-144">Bu denetimler hakkında daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="4c028-144">For more information on these controls, see the following topics:</span></span>

- [<span data-ttu-id="4c028-145">Nasıl yapılır: Bir TreeView veya ListView denetimine özel bilgi ekleme (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="4c028-145">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)

- [<span data-ttu-id="4c028-146">Nasıl yapılır: ListView Denetimine arama yetenekleri ekleme</span><span class="sxs-lookup"><span data-stu-id="4c028-146">How to: Add Search Capabilities to a ListView Control</span></span>](how-to-add-search-capabilities-to-a-listview-control.md)

- [<span data-ttu-id="4c028-147">Nasıl yapılır: Bir TreeView düğümüne kısayol menüsü iliştirme</span><span class="sxs-lookup"><span data-stu-id="4c028-147">How to: Attach a ShortCut Menu to a TreeView Node</span></span>](how-to-attach-a-shortcut-menu-to-a-treeview-node.md)

## <a name="see-also"></a><span data-ttu-id="4c028-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4c028-148">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.TreeView>
- [<span data-ttu-id="4c028-149">ListView Denetimi</span><span class="sxs-lookup"><span data-stu-id="4c028-149">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="4c028-150">Nasıl yapılır: Windows Forms TreeView denetimi ile düğüm ekleme ve kaldırma</span><span class="sxs-lookup"><span data-stu-id="4c028-150">How to: Add and Remove Nodes with the Windows Forms TreeView Control</span></span>](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [<span data-ttu-id="4c028-151">Nasıl yapılır: Windows Forms ListView denetimiyle öğe ekleme ve kaldırma</span><span class="sxs-lookup"><span data-stu-id="4c028-151">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="4c028-152">Nasıl yapılır: Windows Forms ListView Denetimine sütun ekleme</span><span class="sxs-lookup"><span data-stu-id="4c028-152">How to: Add Columns to the Windows Forms ListView Control</span></span>](how-to-add-columns-to-the-windows-forms-listview-control.md)
