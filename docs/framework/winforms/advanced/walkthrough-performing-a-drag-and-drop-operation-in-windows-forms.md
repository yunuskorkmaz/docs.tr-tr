---
title: 'İzlenecek yol: sürükle ve bırak işlemi gerçekleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drag and drop operations
- drag and drop [Windows Forms], Windows Forms
ms.assetid: eb66f6bf-4a7d-4c2d-b276-40fefb2d3b6c
ms.openlocfilehash: 265e6d4f9e3370d28a18b86dea983bb0b556be41
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746797"
---
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a><span data-ttu-id="466ac-102">İzlenecek yol: Windows Forms'ta Sürükle ve Bırak İşlemi Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="466ac-102">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>
<span data-ttu-id="466ac-103">Windows tabanlı uygulamalarda sürükle ve bırak işlemleri gerçekleştirmek için, en önemlisi <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>ve <xref:System.Windows.Forms.Control.DragDrop> olaylarını bir dizi olayı işlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="466ac-103">To perform drag-and-drop operations within Windows-based applications you must handle a series of events, most notably the <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span> <span data-ttu-id="466ac-104">Bu olayların olay bağımsız değişkenlerinde bulunan bilgilerle çalışarak, sürükle ve bırak işlemlerini kolayca kolaylaştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="466ac-104">By working with the information available in the event arguments of these events, you can easily facilitate drag-and-drop operations.</span></span>  
  
## <a name="dragging-data"></a><span data-ttu-id="466ac-105">Verileri sürükleme</span><span class="sxs-lookup"><span data-stu-id="466ac-105">Dragging Data</span></span>  
 <span data-ttu-id="466ac-106">Tüm sürükle ve bırak işlemleri sürüklemeye başlar.</span><span class="sxs-lookup"><span data-stu-id="466ac-106">All drag-and-drop operations begin with dragging.</span></span> <span data-ttu-id="466ac-107">Sürükleme başladığında verilerin toplanmasına olanak sağlayan işlevsellik, <xref:System.Windows.Forms.Control.DoDragDrop%2A> yönteminde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="466ac-107">The functionality to enable data to be collected when dragging begins is implemented in the <xref:System.Windows.Forms.Control.DoDragDrop%2A> method.</span></span>  
  
 <span data-ttu-id="466ac-108">Aşağıdaki örnekte, <xref:System.Windows.Forms.Control.MouseDown> olayı, en sezgisel olduğu için (sürükleme ve bırakma eylemleri fare düğmesi basılı olarak başlar) sürükleme işlemini başlatmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="466ac-108">In the following example, the <xref:System.Windows.Forms.Control.MouseDown> event is used to start the drag operation because it is the most intuitive (most drag-and-drop actions begin with the mouse button being depressed).</span></span> <span data-ttu-id="466ac-109">Ancak, bir sürükle ve bırak yordamını başlatmak için herhangi bir olayın kullanılabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="466ac-109">However, remember that any event could be used to initiate a drag-and-drop procedure.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="466ac-110">Belirli denetimlerin özel sürüklemeye özgü olayları vardır.</span><span class="sxs-lookup"><span data-stu-id="466ac-110">Certain controls have custom drag-specific events.</span></span> <span data-ttu-id="466ac-111"><xref:System.Windows.Forms.ListView> ve <xref:System.Windows.Forms.TreeView> denetimleri (örneğin, bir <xref:System.Windows.Forms.TreeView.ItemDrag> olayına sahiptir).</span><span class="sxs-lookup"><span data-stu-id="466ac-111">The <xref:System.Windows.Forms.ListView> and <xref:System.Windows.Forms.TreeView> controls, for example, have an <xref:System.Windows.Forms.TreeView.ItemDrag> event.</span></span>  
  
#### <a name="to-start-a-drag-operation"></a><span data-ttu-id="466ac-112">Bir sürükleme işlemini başlatmak için</span><span class="sxs-lookup"><span data-stu-id="466ac-112">To start a drag operation</span></span>  
  
1. <span data-ttu-id="466ac-113">Sürüklediğiniz denetimin başlayacağı denetim için <xref:System.Windows.Forms.Control.MouseDown> olayında, verileri sürüklemek üzere ve izin verilen efekt sürüklemeye sahip olacak şekilde ayarlamak için `DoDragDrop` yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="466ac-113">In the <xref:System.Windows.Forms.Control.MouseDown> event for the control where the drag will begin, use the `DoDragDrop` method to set the data to be dragged and the allowed effect dragging will have.</span></span> <span data-ttu-id="466ac-114">Daha fazla bilgi için bkz. <xref:System.Windows.Forms.DragEventArgs.Data%2A> ve <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.</span><span class="sxs-lookup"><span data-stu-id="466ac-114">For more information, see <xref:System.Windows.Forms.DragEventArgs.Data%2A> and <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.</span></span>  
  
     <span data-ttu-id="466ac-115">Aşağıdaki örnek, bir sürükleme işleminin nasıl başlatılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="466ac-115">The following example shows how to initiate a drag operation.</span></span> <span data-ttu-id="466ac-116">Sürükleme işleminin başladığı denetim bir <xref:System.Windows.Forms.Button> denetimidir, sürüklediğiniz veriler <xref:System.Windows.Forms.Button> denetiminin <xref:System.Windows.Forms.Control.Text%2A> özelliğini temsil eden dizedir ve izin verilen efektler kopyalama veya taşıma olur.</span><span class="sxs-lookup"><span data-stu-id="466ac-116">The control where the drag begins is a <xref:System.Windows.Forms.Button> control, the data being dragged is the string representing the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.Button> control, and the allowed effects are either copying or moving.</span></span>  
  
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
    > <span data-ttu-id="466ac-117">Tüm veriler `DoDragDrop` yönteminde parametre olarak kullanılabilir; Yukarıdaki örnekte, özelliği Sürüklenmekte olan konumla (<xref:System.Windows.Forms.Button> denetim) ilişkili olduğundan, <xref:System.Windows.Forms.Button> denetiminin <xref:System.Windows.Forms.Control.Text%2A> özelliği kullanılmıştır (bir değer kodlamak veya bir veri kümesinden verileri almak yerine).</span><span class="sxs-lookup"><span data-stu-id="466ac-117">Any data can be used as a parameter in the `DoDragDrop` method; in the example above, the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.Button> control was used (rather than hard-coding a value or retrieving data from a dataset) because the property was related to the location being dragged from (the <xref:System.Windows.Forms.Button> control).</span></span> <span data-ttu-id="466ac-118">Windows tabanlı uygulamalarınıza sürükle ve bırak işlemleri eklediğinizde bunu göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="466ac-118">Keep this in mind as you incorporate drag-and-drop operations into your Windows-based applications.</span></span>  
  
 <span data-ttu-id="466ac-119">Bir sürükleme işlemi etkin olsa da, sürükleme işlemine devam etmek için sistemin "izin sorar" olayını <xref:System.Windows.Forms.Control.QueryContinueDrag> olayı işleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="466ac-119">While a drag operation is in effect, you can handle the <xref:System.Windows.Forms.Control.QueryContinueDrag> event, which "asks permission" of the system to continue the drag operation.</span></span> <span data-ttu-id="466ac-120">Bu yöntemi işlerken, imleç onun üzerine geldiğinde, bir <xref:System.Windows.Forms.TreeView> denetimindeki <xref:System.Windows.Forms.TreeNode> genişletme gibi, sürükleme işleminde bir etkisi olan yöntemleri çağırmanız için de uygun bir noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="466ac-120">When handling this method, it is also the appropriate point for you to call methods that will have an effect on the drag operation, such as expanding a <xref:System.Windows.Forms.TreeNode> in a <xref:System.Windows.Forms.TreeView> control when the cursor hovers over it.</span></span>  
  
## <a name="dropping-data"></a><span data-ttu-id="466ac-121">Verileri bırakma</span><span class="sxs-lookup"><span data-stu-id="466ac-121">Dropping Data</span></span>  
 <span data-ttu-id="466ac-122">Bir Windows formundaki veya denetimindeki bir konumdan veri sürüklemeye başladıktan sonra doğal olarak bir yere bırakmak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="466ac-122">Once you have begun dragging data from a location on a Windows Form or control, you will naturally want to drop it somewhere.</span></span> <span data-ttu-id="466ac-123">İmleç, veri bırakma için doğru şekilde yapılandırılmış bir formun veya denetimin bir alanını aştığında değişecektir.</span><span class="sxs-lookup"><span data-stu-id="466ac-123">The cursor will change when it crosses an area of a form or control that is correctly configured for dropping data.</span></span> <span data-ttu-id="466ac-124">Bir Windows form veya denetim içindeki herhangi bir alan, <xref:System.Windows.Forms.Control.AllowDrop%2A> özelliğini ayarlayarak ve <xref:System.Windows.Forms.Control.DragEnter> ve <xref:System.Windows.Forms.Control.DragDrop> olaylarını işleyerek bırakılan verileri kabul etmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="466ac-124">Any area within a Windows Form or control can be made to accept dropped data by setting the <xref:System.Windows.Forms.Control.AllowDrop%2A> property and handling the <xref:System.Windows.Forms.Control.DragEnter> and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span>  
  
#### <a name="to-perform-a-drop"></a><span data-ttu-id="466ac-125">Bir bırakma işlemi gerçekleştirmek için</span><span class="sxs-lookup"><span data-stu-id="466ac-125">To perform a drop</span></span>  
  
1. <span data-ttu-id="466ac-126"><xref:System.Windows.Forms.Control.AllowDrop%2A> özelliğini true olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="466ac-126">Set the <xref:System.Windows.Forms.Control.AllowDrop%2A> property to true.</span></span>  
  
2. <span data-ttu-id="466ac-127">Bırakma işleminin gerçekleşeceği denetim için `DragEnter` olayında, sürüklenen verilerin kabul edilebilir bir tür olduğundan emin olun (Bu durumda, <xref:System.Windows.Forms.Control.Text%2A>).</span><span class="sxs-lookup"><span data-stu-id="466ac-127">In the `DragEnter` event for the control where the drop will occur, ensure that the data being dragged is of an acceptable type (in this case, <xref:System.Windows.Forms.Control.Text%2A>).</span></span> <span data-ttu-id="466ac-128">Kod daha sonra, <xref:System.Windows.Forms.DragDropEffects> Numaralandırmadaki bir değere bırakma gerçekleştiğinde gerçekleştirilecek etkiyi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="466ac-128">The code then sets the effect that will happen when the drop occurs to a value in the <xref:System.Windows.Forms.DragDropEffects> enumeration.</span></span> <span data-ttu-id="466ac-129">Daha fazla bilgi için bkz. <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.</span><span class="sxs-lookup"><span data-stu-id="466ac-129">For more information, see <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.</span></span>  
  
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
    > <span data-ttu-id="466ac-130">Kendi <xref:System.Windows.Forms.DataFormats>, kendi nesneniz <xref:System.Windows.Forms.DataObject.SetData%2A> yönteminin <xref:System.Object> parametresi olarak belirterek tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="466ac-130">You can define your own <xref:System.Windows.Forms.DataFormats> by specifying your own object as the <xref:System.Object> parameter of the <xref:System.Windows.Forms.DataObject.SetData%2A> method.</span></span> <span data-ttu-id="466ac-131">Bunu yaparken, belirtilen nesnenin seri hale getirilebilir olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="466ac-131">Be sure, when doing this, that the object specified is serializable.</span></span> <span data-ttu-id="466ac-132">Daha fazla bilgi için bkz. <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="466ac-132">For more information, see <xref:System.Runtime.Serialization.ISerializable>.</span></span>  
  
3. <span data-ttu-id="466ac-133">Bırakma işleminin gerçekleşeceği denetimin <xref:System.Windows.Forms.Control.DragDrop> olayında, sürüklediğiniz verileri almak için <xref:System.Windows.Forms.DataObject.GetData%2A> metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="466ac-133">In the <xref:System.Windows.Forms.Control.DragDrop> event for the control where the drop will occur, use the <xref:System.Windows.Forms.DataObject.GetData%2A> method to retrieve the data being dragged.</span></span> <span data-ttu-id="466ac-134">Daha fazla bilgi için bkz. <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.</span><span class="sxs-lookup"><span data-stu-id="466ac-134">For more information, see <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.</span></span>  
  
     <span data-ttu-id="466ac-135">Aşağıdaki örnekte, <xref:System.Windows.Forms.TextBox> denetim Sürüklenmekte olan denetimdir (bırakma gerçekleşir).</span><span class="sxs-lookup"><span data-stu-id="466ac-135">In the example below, a <xref:System.Windows.Forms.TextBox> control is the control being dragged to (where the drop will occur).</span></span> <span data-ttu-id="466ac-136">Kod, <xref:System.Windows.Forms.TextBox> denetiminin <xref:System.Windows.Forms.Control.Text%2A> özelliğini sürüklenen verilere eşit olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="466ac-136">The code sets the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.TextBox> control equal to the data being dragged.</span></span>  
  
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
    > <span data-ttu-id="466ac-137">Ayrıca, sürükle ve bırak işlemi sırasında anahtarlara bağlı olarak, bazı etkileri meydana geldiğinden (örneğin, CTRL tuşuna basıldığında sürüklenen verileri kopyalamak için standart olan) <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> özelliğiyle çalışabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="466ac-137">Additionally, you can work with the <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> property, so that, depending on keys depressed during the drag-and-drop operation, certain effects occur (for example, it is standard to copy the dragged data when the CTRL key is pressed).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="466ac-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="466ac-138">See also</span></span>

- [<span data-ttu-id="466ac-139">Nasıl yapılır: Panoya Veri Ekleme</span><span class="sxs-lookup"><span data-stu-id="466ac-139">How to: Add Data to the Clipboard</span></span>](how-to-add-data-to-the-clipboard.md)
- [<span data-ttu-id="466ac-140">Nasıl yapılır: Panodan Veri Alma</span><span class="sxs-lookup"><span data-stu-id="466ac-140">How to: Retrieve Data from the Clipboard</span></span>](how-to-retrieve-data-from-the-clipboard.md)
- [<span data-ttu-id="466ac-141">Sürükle ve Bırak İşlemleri ve Pano Desteği</span><span class="sxs-lookup"><span data-stu-id="466ac-141">Drag-and-Drop Operations and Clipboard Support</span></span>](drag-and-drop-operations-and-clipboard-support.md)
