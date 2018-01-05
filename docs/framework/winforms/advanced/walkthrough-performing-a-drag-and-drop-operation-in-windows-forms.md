---
title: "İzlenecek yol: Windows Forms'ta Sürükle ve Bırak İşlemi Gerçekleştirme"
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
- Windows Forms, drag and drop operations
- drag and drop [Windows Forms], Windows Forms
ms.assetid: eb66f6bf-4a7d-4c2d-b276-40fefb2d3b6c
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 173af57f1ec5d9ed14afc0ef5d6ddd391e15d534
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a><span data-ttu-id="28500-102">İzlenecek yol: Windows Forms'ta Sürükle ve Bırak İşlemi Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="28500-102">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>
<span data-ttu-id="28500-103">Windows tabanlı uygulamalar içinde sürükle ve bırak işlemleri için bir dizi olay, özellikle işlemelidir <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, ve <xref:System.Windows.Forms.Control.DragDrop> olaylar.</span><span class="sxs-lookup"><span data-stu-id="28500-103">To perform drag-and-drop operations within Windows-based applications you must handle a series of events, most notably the <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span> <span data-ttu-id="28500-104">Kullanılabilir bilgilerle olay bağımsız değişkenleri bu olayların çalışarak sürükle ve bırak işlemleri kolayca kolaylaştırabilir.</span><span class="sxs-lookup"><span data-stu-id="28500-104">By working with the information available in the event arguments of these events, you can easily facilitate drag-and-drop operations.</span></span>  
  
## <a name="dragging-data"></a><span data-ttu-id="28500-105">Veriler sürükleme</span><span class="sxs-lookup"><span data-stu-id="28500-105">Dragging Data</span></span>  
 <span data-ttu-id="28500-106">Tüm sürükle ve bırak işlemleri sürükleyerek ile başlar.</span><span class="sxs-lookup"><span data-stu-id="28500-106">All drag-and-drop operations begin with dragging.</span></span> <span data-ttu-id="28500-107">Sürükleme işlemi başladığında, toplanacak veri sağlayan İşlevler uygulanan <xref:System.Windows.Forms.Control.DoDragDrop%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="28500-107">The functionality to enable data to be collected when dragging begins is implemented in the <xref:System.Windows.Forms.Control.DoDragDrop%2A> method.</span></span>  
  
 <span data-ttu-id="28500-108">Aşağıdaki örnekte, <xref:System.Windows.Forms.Control.MouseDown> olay en sezgisel olduğundan sürükleme işlemi başlatmak için kullanılır (fare düğmesini basılı çoğu sürükle ve bırak işlemleri başlamak).</span><span class="sxs-lookup"><span data-stu-id="28500-108">In the following example, the <xref:System.Windows.Forms.Control.MouseDown> event is used to start the drag operation because it is the most intuitive (most drag-and-drop actions begin with the mouse button being depressed).</span></span> <span data-ttu-id="28500-109">Bununla birlikte, herhangi bir olayın bir Sürükle ve bırak yordamı başlatmak için kullanılabilecek unutmayın.</span><span class="sxs-lookup"><span data-stu-id="28500-109">However, remember that any event could be used to initiate a drag-and-drop procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="28500-110">Bazı denetimler özel sürükleme özgü olaylar sahiptir.</span><span class="sxs-lookup"><span data-stu-id="28500-110">Certain controls have custom drag-specific events.</span></span> <span data-ttu-id="28500-111"><xref:System.Windows.Forms.ListView> Ve <xref:System.Windows.Forms.TreeView> denetimleri, örneğin, sahip bir <xref:System.Windows.Forms.TreeView.ItemDrag> olay.</span><span class="sxs-lookup"><span data-stu-id="28500-111">The <xref:System.Windows.Forms.ListView> and <xref:System.Windows.Forms.TreeView> controls, for example, have an <xref:System.Windows.Forms.TreeView.ItemDrag> event.</span></span>  
  
#### <a name="to-start-a-drag-operation"></a><span data-ttu-id="28500-112">Sürükleme işlemi başlatmak için</span><span class="sxs-lookup"><span data-stu-id="28500-112">To start a drag operation</span></span>  
  
1.  <span data-ttu-id="28500-113">İçinde <xref:System.Windows.Forms.Control.MouseDown> yere sürükleyin başlayacak, kullanımını denetlemek için olay `DoDragDrop` sürüklenen için veri kümesi için yöntem ve sürükleyerek izin verilen etkili olacaktır.</span><span class="sxs-lookup"><span data-stu-id="28500-113">In the <xref:System.Windows.Forms.Control.MouseDown> event for the control where the drag will begin, use the `DoDragDrop` method to set the data to be dragged and the allowed effect dragging will have.</span></span> <span data-ttu-id="28500-114">Daha fazla bilgi için bkz. <xref:System.Windows.Forms.DragEventArgs.Data%2A> ve <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.</span><span class="sxs-lookup"><span data-stu-id="28500-114">For more information, see <xref:System.Windows.Forms.DragEventArgs.Data%2A> and <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.</span></span>  
  
     <span data-ttu-id="28500-115">Aşağıdaki örnek, bir sürükleme işlemi başlatmak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="28500-115">The following example shows how to initiate a drag operation.</span></span> <span data-ttu-id="28500-116">Sürükle başladığı denetimi bir <xref:System.Windows.Forms.Button> denetimi sürüklenen veri olduğu temsil eden dize <xref:System.Windows.Forms.Control.Text%2A> özelliği <xref:System.Windows.Forms.Button> denetim ve izin verilen efektleri kopyalama veya taşıma.</span><span class="sxs-lookup"><span data-stu-id="28500-116">The control where the drag begins is a <xref:System.Windows.Forms.Button> control, the data being dragged is the string representing the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.Button> control, and the allowed effects are either copying or moving.</span></span>  
  
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
    >  <span data-ttu-id="28500-117">Herhangi bir veriyi bir parametresi olarak kullanılabilir `DoDragDrop` yöntemi; yukarıdaki örnekte <xref:System.Windows.Forms.Control.Text%2A> özelliği <xref:System.Windows.Forms.Button> denetimi (yerine, kodlama sabit bir değer veya bir veri kümesinden veri alma) kullanıldı özelliği ilişkili nedeniyle gelen sürüklenen konumu ( <xref:System.Windows.Forms.Button> denetim).</span><span class="sxs-lookup"><span data-stu-id="28500-117">Any data can be used as a parameter in the `DoDragDrop` method; in the example above, the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.Button> control was used (rather than hard-coding a value or retrieving data from a dataset) because the property was related to the location being dragged from (the <xref:System.Windows.Forms.Button> control).</span></span> <span data-ttu-id="28500-118">Windows tabanlı uygulamalarınıza sürükle ve bırak işlemleri içerecek şekilde bunu göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="28500-118">Keep this in mind as you incorporate drag-and-drop operations into your Windows-based applications.</span></span>  
  
 <span data-ttu-id="28500-119">Sürükleme işlemi etkin durumdayken işleyebilir <xref:System.Windows.Forms.Control.QueryContinueDrag> "izin isteyen" olay sürükleme işlemi devam etmek için sistemi.</span><span class="sxs-lookup"><span data-stu-id="28500-119">While a drag operation is in effect, you can handle the <xref:System.Windows.Forms.Control.QueryContinueDrag> event, which "asks permission" of the system to continue the drag operation.</span></span> <span data-ttu-id="28500-120">Bu yöntem işlenirken, ayrıca, genişletme gibi sürükleme işlemi üzerinde bir etkisi olmaz yöntemleri çağırmak uygun bir noktasına olmasından bir <xref:System.Windows.Forms.TreeNode> içinde bir <xref:System.Windows.Forms.TreeView> zaman imleç üzerinde gezinen denetim.</span><span class="sxs-lookup"><span data-stu-id="28500-120">When handling this method, it is also the appropriate point for you to call methods that will have an effect on the drag operation, such as expanding a <xref:System.Windows.Forms.TreeNode> in a <xref:System.Windows.Forms.TreeView> control when the cursor hovers over it.</span></span>  
  
## <a name="dropping-data"></a><span data-ttu-id="28500-121">Veri bırakma</span><span class="sxs-lookup"><span data-stu-id="28500-121">Dropping Data</span></span>  
 <span data-ttu-id="28500-122">Bir Windows Form veya denetim bir konumdan veri sürükleme başlamıştır sonra doğal olarak herhangi bir yerde bırakma isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="28500-122">Once you have begun dragging data from a location on a Windows Form or control, you will naturally want to drop it somewhere.</span></span> <span data-ttu-id="28500-123">Bir form veya veri bırakma için doğru yapılandırıldığını denetim alanı kestiği yapıldığında imleci değişir.</span><span class="sxs-lookup"><span data-stu-id="28500-123">The cursor will change when it crosses an area of a form or control that is correctly configured for dropping data.</span></span> <span data-ttu-id="28500-124">Windows Form veya denetim içinde herhangi bir alan ayarlayarak bırakılan verileri kabul etmek için yapılan <xref:System.Windows.Forms.Control.AllowDrop%2A> özelliği ve işleme <xref:System.Windows.Forms.Control.DragEnter> ve <xref:System.Windows.Forms.Control.DragDrop> olaylar.</span><span class="sxs-lookup"><span data-stu-id="28500-124">Any area within a Windows Form or control can be made to accept dropped data by setting the <xref:System.Windows.Forms.Control.AllowDrop%2A> property and handling the <xref:System.Windows.Forms.Control.DragEnter> and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span>  
  
#### <a name="to-perform-a-drop"></a><span data-ttu-id="28500-125">Bir açılan gerçekleştirmek için</span><span class="sxs-lookup"><span data-stu-id="28500-125">To perform a drop</span></span>  
  
1.  <span data-ttu-id="28500-126">Ayarlama <xref:System.Windows.Forms.Control.AllowDrop%2A> özelliğinin true.</span><span class="sxs-lookup"><span data-stu-id="28500-126">Set the <xref:System.Windows.Forms.Control.AllowDrop%2A> property to true.</span></span>  
  
2.  <span data-ttu-id="28500-127">İçinde `DragEnter` burada açılan oluşur, denetim olayı sürüklenen verileri kabul edilebilir bir türde olduğundan emin olun (Bu durumda, <xref:System.Windows.Forms.Control.Text%2A>).</span><span class="sxs-lookup"><span data-stu-id="28500-127">In the `DragEnter` event for the control where the drop will occur, ensure that the data being dragged is of an acceptable type (in this case, <xref:System.Windows.Forms.Control.Text%2A>).</span></span> <span data-ttu-id="28500-128">Kod sonra açılan bir değere oluştuğunda olacağını etkisi ayarlar <xref:System.Windows.Forms.DragDropEffects> numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="28500-128">The code then sets the effect that will happen when the drop occurs to a value in the <xref:System.Windows.Forms.DragDropEffects> enumeration.</span></span> <span data-ttu-id="28500-129">Daha fazla bilgi için bkz. <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.</span><span class="sxs-lookup"><span data-stu-id="28500-129">For more information, see <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.</span></span>  
  
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
    >  <span data-ttu-id="28500-130">Kendi tanımlayabilirsiniz <xref:System.Windows.Forms.DataFormats> kendi nesnesi olarak belirterek <xref:System.Object> parametresinin <xref:System.Windows.Forms.DataObject.SetData%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="28500-130">You can define your own <xref:System.Windows.Forms.DataFormats> by specifying your own object as the <xref:System.Object> parameter of the <xref:System.Windows.Forms.DataObject.SetData%2A> method.</span></span> <span data-ttu-id="28500-131">Emin, bunu yaparken belirtilen nesne seri hale getirilebilir olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="28500-131">Be sure, when doing this, that the object specified is serializable.</span></span> <span data-ttu-id="28500-132">Daha fazla bilgi için bkz. <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="28500-132">For more information, see <xref:System.Runtime.Serialization.ISerializable>.</span></span>  
  
3.  <span data-ttu-id="28500-133">İçinde <xref:System.Windows.Forms.Control.DragDrop> burada açılan oluşur, kullanımını denetlemek için olay <xref:System.Windows.Forms.DataObject.GetData%2A> sürüklenen veri alma yöntemi.</span><span class="sxs-lookup"><span data-stu-id="28500-133">In the <xref:System.Windows.Forms.Control.DragDrop> event for the control where the drop will occur, use the <xref:System.Windows.Forms.DataObject.GetData%2A> method to retrieve the data being dragged.</span></span> <span data-ttu-id="28500-134">Daha fazla bilgi için bkz. <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.</span><span class="sxs-lookup"><span data-stu-id="28500-134">For more information, see <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.</span></span>  
  
     <span data-ttu-id="28500-135">Aşağıdaki örnekte bir <xref:System.Windows.Forms.TextBox> denetimidir (açılan gerçekleşeceği için) sürüklenen denetim.</span><span class="sxs-lookup"><span data-stu-id="28500-135">In the example below, a <xref:System.Windows.Forms.TextBox> control is the control being dragged to (where the drop will occur).</span></span> <span data-ttu-id="28500-136">Kod kümeleri <xref:System.Windows.Forms.Control.Text%2A> özelliği <xref:System.Windows.Forms.TextBox> sürüklenen veri eşit denetim.</span><span class="sxs-lookup"><span data-stu-id="28500-136">The code sets the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.TextBox> control equal to the data being dragged.</span></span>  
  
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
    >  <span data-ttu-id="28500-137">Ayrıca, birlikte çalışabilir <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> özelliği, bağlı olarak tuşlarını basılı sürükle ve bırak işlemi sırasında bazı efektler gerçekleşmesini (örneğin, CTRL tuşuna basıldığında sürüklenen verileri kopyalamak için standart öyledir).</span><span class="sxs-lookup"><span data-stu-id="28500-137">Additionally, you can work with the <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> property, so that, depending on keys depressed during the drag-and-drop operation, certain effects occur (for example, it is standard to copy the dragged data when the CTRL key is pressed).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28500-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="28500-138">See Also</span></span>  
 [<span data-ttu-id="28500-139">Nasıl yapılır: Panoya Veri Ekleme</span><span class="sxs-lookup"><span data-stu-id="28500-139">How to: Add Data to the Clipboard</span></span>](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)  
 [<span data-ttu-id="28500-140">Nasıl yapılır: Panodan Veri Alma</span><span class="sxs-lookup"><span data-stu-id="28500-140">How to: Retrieve Data from the Clipboard</span></span>](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)  
 [<span data-ttu-id="28500-141">Sürükle ve Bırak İşlemleri ve Pano Desteği</span><span class="sxs-lookup"><span data-stu-id="28500-141">Drag-and-Drop Operations and Clipboard Support</span></span>](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)
