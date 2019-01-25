---
title: "İzlenecek yol: Windows Forms'ta sürükle ve bırak işlemi gerçekleştirme"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drag and drop operations
- drag and drop [Windows Forms], Windows Forms
ms.assetid: eb66f6bf-4a7d-4c2d-b276-40fefb2d3b6c
ms.openlocfilehash: b582043b3b576b3750b897b17a5f6e0cbdeb84f8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54647640"
---
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a><span data-ttu-id="36419-102">İzlenecek yol: Windows Forms'ta sürükle ve bırak işlemi gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="36419-102">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>
<span data-ttu-id="36419-103">Windows tabanlı uygulamalar sürükle-bırak işlemlerini gerçekleştirmek için bir dizi olayı, özellikle işlemelidir <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, ve <xref:System.Windows.Forms.Control.DragDrop> olayları.</span><span class="sxs-lookup"><span data-stu-id="36419-103">To perform drag-and-drop operations within Windows-based applications you must handle a series of events, most notably the <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span> <span data-ttu-id="36419-104">Kullanılabilir bilgilerle olay bağımsız değişkenleri bu olayların çalışarak, sürükle ve bırak işlemleri kolayca kolaylaştırabilir.</span><span class="sxs-lookup"><span data-stu-id="36419-104">By working with the information available in the event arguments of these events, you can easily facilitate drag-and-drop operations.</span></span>  
  
## <a name="dragging-data"></a><span data-ttu-id="36419-105">Veriler sürükleme</span><span class="sxs-lookup"><span data-stu-id="36419-105">Dragging Data</span></span>  
 <span data-ttu-id="36419-106">Tüm sürükle ve bırak işlemleri sürüklemeye ile başlayın.</span><span class="sxs-lookup"><span data-stu-id="36419-106">All drag-and-drop operations begin with dragging.</span></span> <span data-ttu-id="36419-107">Sürükleme işlemi başladığında, toplanacak veri geliştirebilme işlevselliği uygulanan <xref:System.Windows.Forms.Control.DoDragDrop%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="36419-107">The functionality to enable data to be collected when dragging begins is implemented in the <xref:System.Windows.Forms.Control.DoDragDrop%2A> method.</span></span>  
  
 <span data-ttu-id="36419-108">Aşağıdaki örnekte, <xref:System.Windows.Forms.Control.MouseDown> olayını en sezgisel çünkü bu sürükleme işlemi başlatmak için kullanılır (çoğu sürükle ve bırak Eylemler fare düğmesini basılı ile başlar).</span><span class="sxs-lookup"><span data-stu-id="36419-108">In the following example, the <xref:System.Windows.Forms.Control.MouseDown> event is used to start the drag operation because it is the most intuitive (most drag-and-drop actions begin with the mouse button being depressed).</span></span> <span data-ttu-id="36419-109">Ancak, herhangi bir olay, bir Sürükle ve bırak yordam başlatmak için kullanılabilir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="36419-109">However, remember that any event could be used to initiate a drag-and-drop procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="36419-110">Belirli denetimler özel Sürükle özgü olaylar sahiptir.</span><span class="sxs-lookup"><span data-stu-id="36419-110">Certain controls have custom drag-specific events.</span></span> <span data-ttu-id="36419-111"><xref:System.Windows.Forms.ListView> Ve <xref:System.Windows.Forms.TreeView> denetimleri, örneğin, sahip bir <xref:System.Windows.Forms.TreeView.ItemDrag> olay.</span><span class="sxs-lookup"><span data-stu-id="36419-111">The <xref:System.Windows.Forms.ListView> and <xref:System.Windows.Forms.TreeView> controls, for example, have an <xref:System.Windows.Forms.TreeView.ItemDrag> event.</span></span>  
  
#### <a name="to-start-a-drag-operation"></a><span data-ttu-id="36419-112">Bir sürükleme işlemi başlatmak için</span><span class="sxs-lookup"><span data-stu-id="36419-112">To start a drag operation</span></span>  
  
1.  <span data-ttu-id="36419-113">İçinde <xref:System.Windows.Forms.Control.MouseDown> yeri sürükleme başlayacak, kullanımını denetlemek için olay `DoDragDrop` sürüklenmesi için veri kümesi için yöntem ve sürükleme izin verilen etkin olacaktır.</span><span class="sxs-lookup"><span data-stu-id="36419-113">In the <xref:System.Windows.Forms.Control.MouseDown> event for the control where the drag will begin, use the `DoDragDrop` method to set the data to be dragged and the allowed effect dragging will have.</span></span> <span data-ttu-id="36419-114">Daha fazla bilgi için bkz. <xref:System.Windows.Forms.DragEventArgs.Data%2A> ve <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.</span><span class="sxs-lookup"><span data-stu-id="36419-114">For more information, see <xref:System.Windows.Forms.DragEventArgs.Data%2A> and <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.</span></span>  
  
     <span data-ttu-id="36419-115">Aşağıdaki örnek, bir sürükleme işlemi başlatmak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="36419-115">The following example shows how to initiate a drag operation.</span></span> <span data-ttu-id="36419-116">Sürükleme başladığı denetimi bir <xref:System.Windows.Forms.Button> denetimi, sürüklenen veri olduğu temsil eden dize <xref:System.Windows.Forms.Control.Text%2A> özelliği <xref:System.Windows.Forms.Button> denetimi ve izin verilen efektleri kopyalama veya taşıma.</span><span class="sxs-lookup"><span data-stu-id="36419-116">The control where the drag begins is a <xref:System.Windows.Forms.Button> control, the data being dragged is the string representing the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.Button> control, and the allowed effects are either copying or moving.</span></span>  
  
    ```vb  
    Private Sub Button1_MouseDown(ByVal sender As Object, ByVal e As System.Windows.Forms.MouseEventArgs) Handles Button1.MouseDown  
       Button1.DoDragDrop(Button1.Text, DragDropEffects.Copy Or DragDropEffects.Move)  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_MouseDown(object sender,   
    System.Windows.Forms.MouseEventArgs e)  
    {  
       button1.DoDragDrop(button1.Text, DragDropEffects.Copy |   
          DragDropEffects.Move);  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="36419-117">Tüm veriler, bir parametre olarak kullanılabilir `DoDragDrop` yöntemi; yukarıdaki örnekte, <xref:System.Windows.Forms.Control.Text%2A> özelliği <xref:System.Windows.Forms.Button> denetim kullanıldı (yerine, kodlama sabit bir değer veya bir veri kümesinden veri alma) özelliği ilişkili için gelen sürüklenen konumu ( <xref:System.Windows.Forms.Button> denetim).</span><span class="sxs-lookup"><span data-stu-id="36419-117">Any data can be used as a parameter in the `DoDragDrop` method; in the example above, the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.Button> control was used (rather than hard-coding a value or retrieving data from a dataset) because the property was related to the location being dragged from (the <xref:System.Windows.Forms.Button> control).</span></span> <span data-ttu-id="36419-118">Sürükle ve bırak işlemleri Windows tabanlı uygulamalarınıza eklemenizi olarak bunu aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="36419-118">Keep this in mind as you incorporate drag-and-drop operations into your Windows-based applications.</span></span>  
  
 <span data-ttu-id="36419-119">Bir sürükleme işlemi etkin durumdayken işleyebilirsiniz <xref:System.Windows.Forms.Control.QueryContinueDrag> "izin isteyen" olayı, sürükle işlemini devam etmek için sistemin.</span><span class="sxs-lookup"><span data-stu-id="36419-119">While a drag operation is in effect, you can handle the <xref:System.Windows.Forms.Control.QueryContinueDrag> event, which "asks permission" of the system to continue the drag operation.</span></span> <span data-ttu-id="36419-120">Bu yöntem işlenirken, ayrıca, genişletme gibi sürükleme işlemi üzerinde bir etkisi olmayacak yöntemleri çağırmak uygun bir noktasına olduğu bir <xref:System.Windows.Forms.TreeNode> içinde bir <xref:System.Windows.Forms.TreeView> imleci üzerine geldiğinde denetim.</span><span class="sxs-lookup"><span data-stu-id="36419-120">When handling this method, it is also the appropriate point for you to call methods that will have an effect on the drag operation, such as expanding a <xref:System.Windows.Forms.TreeNode> in a <xref:System.Windows.Forms.TreeView> control when the cursor hovers over it.</span></span>  
  
## <a name="dropping-data"></a><span data-ttu-id="36419-121">Veri bırakılıyor</span><span class="sxs-lookup"><span data-stu-id="36419-121">Dropping Data</span></span>  
 <span data-ttu-id="36419-122">Verileri bir konumdan bir Windows Form veya denetim üzerinde sürükleyerek başlamıştır sonra doğal olarak yere bırak isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="36419-122">Once you have begun dragging data from a location on a Windows Form or control, you will naturally want to drop it somewhere.</span></span> <span data-ttu-id="36419-123">İmleç, bir form veya denetim verilerini silmek için doğru şekilde yapılandırıldığı bir alanı geçtiğinde değişecektir.</span><span class="sxs-lookup"><span data-stu-id="36419-123">The cursor will change when it crosses an area of a form or control that is correctly configured for dropping data.</span></span> <span data-ttu-id="36419-124">Bırakılan veri ayarlayarak kabul etmek için bir Windows Form veya denetim içinde herhangi bir alan yapılabilir <xref:System.Windows.Forms.Control.AllowDrop%2A> özelliği ve işleme <xref:System.Windows.Forms.Control.DragEnter> ve <xref:System.Windows.Forms.Control.DragDrop> olayları.</span><span class="sxs-lookup"><span data-stu-id="36419-124">Any area within a Windows Form or control can be made to accept dropped data by setting the <xref:System.Windows.Forms.Control.AllowDrop%2A> property and handling the <xref:System.Windows.Forms.Control.DragEnter> and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span>  
  
#### <a name="to-perform-a-drop"></a><span data-ttu-id="36419-125">Bir bırakma gerçekleştirmek için</span><span class="sxs-lookup"><span data-stu-id="36419-125">To perform a drop</span></span>  
  
1.  <span data-ttu-id="36419-126">Ayarlama <xref:System.Windows.Forms.Control.AllowDrop%2A> özelliği true.</span><span class="sxs-lookup"><span data-stu-id="36419-126">Set the <xref:System.Windows.Forms.Control.AllowDrop%2A> property to true.</span></span>  
  
2.  <span data-ttu-id="36419-127">İçinde `DragEnter` burada açılan gerçekleşir, denetim için olay sürüklenen veri kabul edilebilir bir tür olduğundan emin olun (Bu durumda, <xref:System.Windows.Forms.Control.Text%2A>).</span><span class="sxs-lookup"><span data-stu-id="36419-127">In the `DragEnter` event for the control where the drop will occur, ensure that the data being dragged is of an acceptable type (in this case, <xref:System.Windows.Forms.Control.Text%2A>).</span></span> <span data-ttu-id="36419-128">Kodun ardından açılan bir değere oluştuğunda gerçekleşir etkisini ayarlar <xref:System.Windows.Forms.DragDropEffects> sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="36419-128">The code then sets the effect that will happen when the drop occurs to a value in the <xref:System.Windows.Forms.DragDropEffects> enumeration.</span></span> <span data-ttu-id="36419-129">Daha fazla bilgi için bkz. <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.</span><span class="sxs-lookup"><span data-stu-id="36419-129">For more information, see <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.</span></span>  
  
    ```vb  
    Private Sub TextBox1_DragEnter(ByVal sender As Object, ByVal e As System.Windows.Forms.DragEventArgs) Handles TextBox1.DragEnter  
       If (e.Data.GetDataPresent(DataFormats.Text)) Then  
         e.Effect = DragDropEffects.Copy  
       Else  
         e.Effect = DragDropEffects.None  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_DragEnter(object sender,   
    System.Windows.Forms.DragEventArgs e)  
    {  
       if (e.Data.GetDataPresent(DataFormats.Text))   
          e.Effect = DragDropEffects.Copy;  
       else  
          e.Effect = DragDropEffects.None;  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="36419-130">Kendi tanımlayabilirsiniz <xref:System.Windows.Forms.DataFormats> kendi nesnesi olarak belirterek <xref:System.Object> parametresinin <xref:System.Windows.Forms.DataObject.SetData%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="36419-130">You can define your own <xref:System.Windows.Forms.DataFormats> by specifying your own object as the <xref:System.Object> parameter of the <xref:System.Windows.Forms.DataObject.SetData%2A> method.</span></span> <span data-ttu-id="36419-131">Bunu yaparken belirtilen bir nesne seri hale getirilebilir olduğunu denetleyin.</span><span class="sxs-lookup"><span data-stu-id="36419-131">Be sure, when doing this, that the object specified is serializable.</span></span> <span data-ttu-id="36419-132">Daha fazla bilgi için bkz. <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="36419-132">For more information, see <xref:System.Runtime.Serialization.ISerializable>.</span></span>  
  
3.  <span data-ttu-id="36419-133">İçinde <xref:System.Windows.Forms.Control.DragDrop> burada açılan gerçekleşir, kullanımını denetlemek için olay <xref:System.Windows.Forms.DataObject.GetData%2A> sürüklenen verileri almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="36419-133">In the <xref:System.Windows.Forms.Control.DragDrop> event for the control where the drop will occur, use the <xref:System.Windows.Forms.DataObject.GetData%2A> method to retrieve the data being dragged.</span></span> <span data-ttu-id="36419-134">Daha fazla bilgi için bkz. <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.</span><span class="sxs-lookup"><span data-stu-id="36419-134">For more information, see <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.</span></span>  
  
     <span data-ttu-id="36419-135">Aşağıdaki örnekte bir <xref:System.Windows.Forms.TextBox> (açılan gerçekleşeceği için) sürüklenen denetimi bir denetimdir.</span><span class="sxs-lookup"><span data-stu-id="36419-135">In the example below, a <xref:System.Windows.Forms.TextBox> control is the control being dragged to (where the drop will occur).</span></span> <span data-ttu-id="36419-136">Kod kümeleri <xref:System.Windows.Forms.Control.Text%2A> özelliği <xref:System.Windows.Forms.TextBox> sürüklenen verilere eşit denetim.</span><span class="sxs-lookup"><span data-stu-id="36419-136">The code sets the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.TextBox> control equal to the data being dragged.</span></span>  
  
    ```vb  
    Private Sub TextBox1_DragDrop(ByVal sender As Object, ByVal e As System.Windows.Forms.DragEventArgs) Handles TextBox1.DragDrop  
       TextBox1.Text = e.Data.GetData(DataFormats.Text).ToString  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_DragDrop(object sender,   
    System.Windows.Forms.DragEventArgs e)  
    {  
       textBox1.Text = e.Data.GetData(DataFormats.Text).ToString();  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="36419-137">Ayrıca, çalışabilirsiniz <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> özelliğine bağlı olarak tuşları basılı sürükle ve bırak işlemi sırasında böylece bazı efektler ortaya (örneğin, CTRL tuşuna basıldığında sürüklenen veri kopyalamak için standart olmadığı).</span><span class="sxs-lookup"><span data-stu-id="36419-137">Additionally, you can work with the <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> property, so that, depending on keys depressed during the drag-and-drop operation, certain effects occur (for example, it is standard to copy the dragged data when the CTRL key is pressed).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36419-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36419-138">See also</span></span>
- [<span data-ttu-id="36419-139">Nasıl yapılır: Panoya veri ekleme</span><span class="sxs-lookup"><span data-stu-id="36419-139">How to: Add Data to the Clipboard</span></span>](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)
- [<span data-ttu-id="36419-140">Nasıl yapılır: Panodan veri alma</span><span class="sxs-lookup"><span data-stu-id="36419-140">How to: Retrieve Data from the Clipboard</span></span>](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)
- [<span data-ttu-id="36419-141">Sürükle ve Bırak İşlemleri ve Pano Desteği</span><span class="sxs-lookup"><span data-stu-id="36419-141">Drag-and-Drop Operations and Clipboard Support</span></span>](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)
