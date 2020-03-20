---
title: 'Walkthrough: Sürükle ve bırak işlemi gerçekleştirin'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drag and drop operations
- drag and drop [Windows Forms], Windows Forms
ms.assetid: eb66f6bf-4a7d-4c2d-b276-40fefb2d3b6c
ms.openlocfilehash: b5e4bf753733cb9bd010672f40e8fbeb0cf036bf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182437"
---
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a><span data-ttu-id="f28ba-102">İzlenecek yol: Windows Forms'ta Sürükle ve Bırak İşlemi Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="f28ba-102">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>
<span data-ttu-id="f28ba-103">Windows tabanlı uygulamalarda sürükle ve bırak işlemleri gerçekleştirmek için, en önemlisi <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>ve <xref:System.Windows.Forms.Control.DragDrop> olaylar olmak üzere bir dizi olayı ele almalısınız.</span><span class="sxs-lookup"><span data-stu-id="f28ba-103">To perform drag-and-drop operations within Windows-based applications you must handle a series of events, most notably the <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span> <span data-ttu-id="f28ba-104">Bu olayların olay argümanlarında bulunan bilgilerle çalışarak sürükle ve bırak işlemlerini kolayca kolaylaştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f28ba-104">By working with the information available in the event arguments of these events, you can easily facilitate drag-and-drop operations.</span></span>  
  
## <a name="dragging-data"></a><span data-ttu-id="f28ba-105">Verileri Sürükleme</span><span class="sxs-lookup"><span data-stu-id="f28ba-105">Dragging Data</span></span>  
 <span data-ttu-id="f28ba-106">Tüm sürükle ve bırak işlemleri sürükleme ile başlar.</span><span class="sxs-lookup"><span data-stu-id="f28ba-106">All drag-and-drop operations begin with dragging.</span></span> <span data-ttu-id="f28ba-107">Sürükleme başladığında verilerin toplanmasını etkinleştirme işlevi <xref:System.Windows.Forms.Control.DoDragDrop%2A> yöntemde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="f28ba-107">The functionality to enable data to be collected when dragging begins is implemented in the <xref:System.Windows.Forms.Control.DoDragDrop%2A> method.</span></span>  
  
 <span data-ttu-id="f28ba-108">Aşağıdaki örnekte, <xref:System.Windows.Forms.Control.MouseDown> en sezgisel olduğu için sürükle işlemini başlatmak için olay kullanılır (çoğu sürükle ve bırak eylemi fare düğmesinin depresif olmasıyla başlar).</span><span class="sxs-lookup"><span data-stu-id="f28ba-108">In the following example, the <xref:System.Windows.Forms.Control.MouseDown> event is used to start the drag operation because it is the most intuitive (most drag-and-drop actions begin with the mouse button being depressed).</span></span> <span data-ttu-id="f28ba-109">Ancak, herhangi bir olayın sürükle ve bırak yordamı başlatmak için kullanılabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f28ba-109">However, remember that any event could be used to initiate a drag-and-drop procedure.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f28ba-110">Bazı denetimlerde özel sürüme özel olaylar vardır.</span><span class="sxs-lookup"><span data-stu-id="f28ba-110">Certain controls have custom drag-specific events.</span></span> <span data-ttu-id="f28ba-111">Ve <xref:System.Windows.Forms.ListView> <xref:System.Windows.Forms.TreeView> denetimleri, örneğin, <xref:System.Windows.Forms.TreeView.ItemDrag> bir olay var.</span><span class="sxs-lookup"><span data-stu-id="f28ba-111">The <xref:System.Windows.Forms.ListView> and <xref:System.Windows.Forms.TreeView> controls, for example, have an <xref:System.Windows.Forms.TreeView.ItemDrag> event.</span></span>  
  
#### <a name="to-start-a-drag-operation"></a><span data-ttu-id="f28ba-112">Sürükleme işlemini başlatmak için</span><span class="sxs-lookup"><span data-stu-id="f28ba-112">To start a drag operation</span></span>  
  
1. <span data-ttu-id="f28ba-113">Sürüklemenin <xref:System.Windows.Forms.Control.MouseDown> başlayacağı denetim durumunda, sürükleme nin `DoDragDrop` verilen verileri ayarlamak için yöntemi kullanın ve izin verilen efekt sürükleme olacaktır.</span><span class="sxs-lookup"><span data-stu-id="f28ba-113">In the <xref:System.Windows.Forms.Control.MouseDown> event for the control where the drag will begin, use the `DoDragDrop` method to set the data to be dragged and the allowed effect dragging will have.</span></span> <span data-ttu-id="f28ba-114">Daha fazla bilgi için <xref:System.Windows.Forms.DragEventArgs.Data%2A> ve <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A> bölümlerine bakın.</span><span class="sxs-lookup"><span data-stu-id="f28ba-114">For more information, see <xref:System.Windows.Forms.DragEventArgs.Data%2A> and <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.</span></span>  
  
     <span data-ttu-id="f28ba-115">Aşağıdaki örnek, sürükleme işleminin nasıl başlatılabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f28ba-115">The following example shows how to initiate a drag operation.</span></span> <span data-ttu-id="f28ba-116">Sürüklemenin başladığı denetim bir <xref:System.Windows.Forms.Button> denetimdir, sürüklenen veriler <xref:System.Windows.Forms.Control.Text%2A> <xref:System.Windows.Forms.Button> denetimin özelliğini temsil eden dizedir ve izin verilen efektler kopyalama veya taşımadır.</span><span class="sxs-lookup"><span data-stu-id="f28ba-116">The control where the drag begins is a <xref:System.Windows.Forms.Button> control, the data being dragged is the string representing the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.Button> control, and the allowed effects are either copying or moving.</span></span>  
  
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
    > <span data-ttu-id="f28ba-117">Herhangi bir veri `DoDragDrop` yöntemde bir parametre olarak kullanılabilir; yukarıdaki örnekte, <xref:System.Windows.Forms.Control.Text%2A> denetimin <xref:System.Windows.Forms.Button> özelliği (bir değeri zor kodlamak veya veri kümesinden veri almak yerine) kullanılmıştır, çünkü özellik sürüklenen <xref:System.Windows.Forms.Button> konumla (denetim) ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="f28ba-117">Any data can be used as a parameter in the `DoDragDrop` method; in the example above, the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.Button> control was used (rather than hard-coding a value or retrieving data from a dataset) because the property was related to the location being dragged from (the <xref:System.Windows.Forms.Button> control).</span></span> <span data-ttu-id="f28ba-118">Sürükle ve bırak işlemlerini Windows tabanlı uygulamalarınıza dahil ederken bunu aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="f28ba-118">Keep this in mind as you incorporate drag-and-drop operations into your Windows-based applications.</span></span>  
  
 <span data-ttu-id="f28ba-119">Sürükleme işlemi etkinken, sürükle işlemine devam etmek için sistemin "izin istediği" <xref:System.Windows.Forms.Control.QueryContinueDrag> olayı işleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f28ba-119">While a drag operation is in effect, you can handle the <xref:System.Windows.Forms.Control.QueryContinueDrag> event, which "asks permission" of the system to continue the drag operation.</span></span> <span data-ttu-id="f28ba-120">Bu yöntemi işlerken, imleç üzerinde gezinirken bir <xref:System.Windows.Forms.TreeNode> denetimi <xref:System.Windows.Forms.TreeView> genişletmek gibi sürükleme işlemini etkileyecek yöntemleri aramanız da uygun bir noktadır.</span><span class="sxs-lookup"><span data-stu-id="f28ba-120">When handling this method, it is also the appropriate point for you to call methods that will have an effect on the drag operation, such as expanding a <xref:System.Windows.Forms.TreeNode> in a <xref:System.Windows.Forms.TreeView> control when the cursor hovers over it.</span></span>  
  
## <a name="dropping-data"></a><span data-ttu-id="f28ba-121">Veri Bırakma</span><span class="sxs-lookup"><span data-stu-id="f28ba-121">Dropping Data</span></span>  
 <span data-ttu-id="f28ba-122">Windows Formu veya denetimindeki bir konumdan veri sürüklemeye başladıktan sonra, doğal olarak verileri bir yere bırakmak isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="f28ba-122">Once you have begun dragging data from a location on a Windows Form or control, you will naturally want to drop it somewhere.</span></span> <span data-ttu-id="f28ba-123">İmleç, veri bırakmak için doğru şekilde yapılandırılan bir form veya denetim alanını geçtiğinde değişir.</span><span class="sxs-lookup"><span data-stu-id="f28ba-123">The cursor will change when it crosses an area of a form or control that is correctly configured for dropping data.</span></span> <span data-ttu-id="f28ba-124">Windows Formu veya denetimi içindeki herhangi bir alan, <xref:System.Windows.Forms.Control.AllowDrop%2A> özelliği ayarlayarak ve <xref:System.Windows.Forms.Control.DragEnter> <xref:System.Windows.Forms.Control.DragDrop> olayları işleyerek bırakılan verileri kabul etmek için yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="f28ba-124">Any area within a Windows Form or control can be made to accept dropped data by setting the <xref:System.Windows.Forms.Control.AllowDrop%2A> property and handling the <xref:System.Windows.Forms.Control.DragEnter> and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span>  
  
#### <a name="to-perform-a-drop"></a><span data-ttu-id="f28ba-125">Bir damla gerçekleştirmek için</span><span class="sxs-lookup"><span data-stu-id="f28ba-125">To perform a drop</span></span>  
  
1. <span data-ttu-id="f28ba-126">Özelliği <xref:System.Windows.Forms.Control.AllowDrop%2A> gerçeğe ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f28ba-126">Set the <xref:System.Windows.Forms.Control.AllowDrop%2A> property to true.</span></span>  
  
2. <span data-ttu-id="f28ba-127">`DragEnter` Bırakmanın gerçekleşeceği denetim durumunda, sürüklenen verilerin kabul edilebilir bir türde olduğundan emin <xref:System.Windows.Forms.Control.Text%2A>olun (bu durumda).</span><span class="sxs-lookup"><span data-stu-id="f28ba-127">In the `DragEnter` event for the control where the drop will occur, ensure that the data being dragged is of an acceptable type (in this case, <xref:System.Windows.Forms.Control.Text%2A>).</span></span> <span data-ttu-id="f28ba-128">Kod daha sonra, numaralandırmadaki <xref:System.Windows.Forms.DragDropEffects> bir değerde düşüş oluştuğunda oluşacak efekti ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f28ba-128">The code then sets the effect that will happen when the drop occurs to a value in the <xref:System.Windows.Forms.DragDropEffects> enumeration.</span></span> <span data-ttu-id="f28ba-129">Daha fazla bilgi için bkz. <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.</span><span class="sxs-lookup"><span data-stu-id="f28ba-129">For more information, see <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.</span></span>  
  
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
    > <span data-ttu-id="f28ba-130">Yöntemin <xref:System.Windows.Forms.DataFormats> <xref:System.Object> parametresi <xref:System.Windows.Forms.DataObject.SetData%2A> olarak kendi nesnenizi belirterek kendi nesnenizi tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f28ba-130">You can define your own <xref:System.Windows.Forms.DataFormats> by specifying your own object as the <xref:System.Object> parameter of the <xref:System.Windows.Forms.DataObject.SetData%2A> method.</span></span> <span data-ttu-id="f28ba-131">Bunu yaparken, belirtilen nesnenin serileştirilebilir olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="f28ba-131">Be sure, when doing this, that the object specified is serializable.</span></span> <span data-ttu-id="f28ba-132">Daha fazla bilgi için bkz. <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="f28ba-132">For more information, see <xref:System.Runtime.Serialization.ISerializable>.</span></span>  
  
3. <span data-ttu-id="f28ba-133"><xref:System.Windows.Forms.Control.DragDrop> Bırakmanın gerçekleşeceği denetim durumunda, sürüklenen <xref:System.Windows.Forms.DataObject.GetData%2A> verileri almak için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="f28ba-133">In the <xref:System.Windows.Forms.Control.DragDrop> event for the control where the drop will occur, use the <xref:System.Windows.Forms.DataObject.GetData%2A> method to retrieve the data being dragged.</span></span> <span data-ttu-id="f28ba-134">Daha fazla bilgi için bkz. <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.</span><span class="sxs-lookup"><span data-stu-id="f28ba-134">For more information, see <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.</span></span>  
  
     <span data-ttu-id="f28ba-135">Aşağıdaki örnekte, <xref:System.Windows.Forms.TextBox> denetim sürülmekte olan denetimdir (bırakmanın gerçekleşeceği yer).</span><span class="sxs-lookup"><span data-stu-id="f28ba-135">In the example below, a <xref:System.Windows.Forms.TextBox> control is the control being dragged to (where the drop will occur).</span></span> <span data-ttu-id="f28ba-136">Kod, denetimin <xref:System.Windows.Forms.Control.Text%2A> özelliğini <xref:System.Windows.Forms.TextBox> sürüklenen verilere eşit olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f28ba-136">The code sets the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.TextBox> control equal to the data being dragged.</span></span>  
  
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
    > <span data-ttu-id="f28ba-137">Ayrıca, <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> sürükle ve bırak işlemi sırasında bunalıma girmiş anahtarlara bağlı olarak belirli efektlerin oluşması (örneğin, CTRL tuşuna basıldığında sürüklenen verileri kopyalamak standarttır) özelliğiyle birlikte çalışabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f28ba-137">Additionally, you can work with the <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> property, so that, depending on keys depressed during the drag-and-drop operation, certain effects occur (for example, it is standard to copy the dragged data when the CTRL key is pressed).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f28ba-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f28ba-138">See also</span></span>

- [<span data-ttu-id="f28ba-139">Nasıl yapılır: Panoya Veri Ekleme</span><span class="sxs-lookup"><span data-stu-id="f28ba-139">How to: Add Data to the Clipboard</span></span>](how-to-add-data-to-the-clipboard.md)
- [<span data-ttu-id="f28ba-140">Nasıl yapılır: Panodan Veri Alma</span><span class="sxs-lookup"><span data-stu-id="f28ba-140">How to: Retrieve Data from the Clipboard</span></span>](how-to-retrieve-data-from-the-clipboard.md)
- [<span data-ttu-id="f28ba-141">Sürükle ve Bırak İşlemleri ve Pano Desteği</span><span class="sxs-lookup"><span data-stu-id="f28ba-141">Drag-and-Drop Operations and Clipboard Support</span></span>](drag-and-drop-operations-and-clipboard-support.md)
