---
title: 'İzlenecek yol: sürükle ve bırak işlemi gerçekleştirme'
description: En özellikle DragEnter, DragLeave ve DragDrop olaylarını bir dizi olayı işleyerek Windows Forms bir sürükle ve bırak işlemi gerçekleştirmeyi öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drag and drop operations
- drag and drop [Windows Forms], Windows Forms
ms.assetid: eb66f6bf-4a7d-4c2d-b276-40fefb2d3b6c
ms.openlocfilehash: 83bfda875e2fdec3981bbcb8f8f7be00db342440
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325822"
---
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a><span data-ttu-id="1c80a-103">İzlenecek yol: Windows Forms'ta Sürükle ve Bırak İşlemi Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="1c80a-103">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>
<span data-ttu-id="1c80a-104">Windows tabanlı uygulamalarda sürükle ve bırak işlemleri gerçekleştirmek için, bir dizi olayı, özellikle, <xref:System.Windows.Forms.Control.DragEnter> <xref:System.Windows.Forms.Control.DragLeave> ve olaylarını işlemeniz gerekir <xref:System.Windows.Forms.Control.DragDrop> .</span><span class="sxs-lookup"><span data-stu-id="1c80a-104">To perform drag-and-drop operations within Windows-based applications you must handle a series of events, most notably the <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span> <span data-ttu-id="1c80a-105">Bu olayların olay bağımsız değişkenlerinde bulunan bilgilerle çalışarak, sürükle ve bırak işlemlerini kolayca kolaylaştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1c80a-105">By working with the information available in the event arguments of these events, you can easily facilitate drag-and-drop operations.</span></span>  
  
## <a name="dragging-data"></a><span data-ttu-id="1c80a-106">Verileri sürükleme</span><span class="sxs-lookup"><span data-stu-id="1c80a-106">Dragging Data</span></span>  
 <span data-ttu-id="1c80a-107">Tüm sürükle ve bırak işlemleri sürüklemeye başlar.</span><span class="sxs-lookup"><span data-stu-id="1c80a-107">All drag-and-drop operations begin with dragging.</span></span> <span data-ttu-id="1c80a-108">Sürükleme başladığında verilerin toplanmasına olanak sağlayan işlevsellik, yöntemi içinde uygulanır <xref:System.Windows.Forms.Control.DoDragDrop%2A> .</span><span class="sxs-lookup"><span data-stu-id="1c80a-108">The functionality to enable data to be collected when dragging begins is implemented in the <xref:System.Windows.Forms.Control.DoDragDrop%2A> method.</span></span>  
  
 <span data-ttu-id="1c80a-109">Aşağıdaki örnekte, <xref:System.Windows.Forms.Control.MouseDown> en sezgisel olan (sürükleme ve bırakma eylemleri fare düğmesi basılı olarak başlar), sürükleme işlemini başlatmak için olay kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1c80a-109">In the following example, the <xref:System.Windows.Forms.Control.MouseDown> event is used to start the drag operation because it is the most intuitive (most drag-and-drop actions begin with the mouse button being depressed).</span></span> <span data-ttu-id="1c80a-110">Ancak, bir sürükle ve bırak yordamını başlatmak için herhangi bir olayın kullanılabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="1c80a-110">However, remember that any event could be used to initiate a drag-and-drop procedure.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1c80a-111">Belirli denetimlerin özel sürüklemeye özgü olayları vardır.</span><span class="sxs-lookup"><span data-stu-id="1c80a-111">Certain controls have custom drag-specific events.</span></span> <span data-ttu-id="1c80a-112"><xref:System.Windows.Forms.ListView>Ve <xref:System.Windows.Forms.TreeView> denetimleri, örneğin, bir <xref:System.Windows.Forms.TreeView.ItemDrag> olayıdır.</span><span class="sxs-lookup"><span data-stu-id="1c80a-112">The <xref:System.Windows.Forms.ListView> and <xref:System.Windows.Forms.TreeView> controls, for example, have an <xref:System.Windows.Forms.TreeView.ItemDrag> event.</span></span>  
  
#### <a name="to-start-a-drag-operation"></a><span data-ttu-id="1c80a-113">Bir sürükleme işlemini başlatmak için</span><span class="sxs-lookup"><span data-stu-id="1c80a-113">To start a drag operation</span></span>  
  
1. <span data-ttu-id="1c80a-114"><xref:System.Windows.Forms.Control.MouseDown>Sürüklediğiniz denetimin başlayacağı olayda, `DoDragDrop` verileri sürüklenecektir ve izin verilen efekt sürüklemeye sahip olacak şekilde ayarlamak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="1c80a-114">In the <xref:System.Windows.Forms.Control.MouseDown> event for the control where the drag will begin, use the `DoDragDrop` method to set the data to be dragged and the allowed effect dragging will have.</span></span> <span data-ttu-id="1c80a-115">Daha fazla bilgi için <xref:System.Windows.Forms.DragEventArgs.Data%2A> ve <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A> bölümlerine bakın.</span><span class="sxs-lookup"><span data-stu-id="1c80a-115">For more information, see <xref:System.Windows.Forms.DragEventArgs.Data%2A> and <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.</span></span>  
  
     <span data-ttu-id="1c80a-116">Aşağıdaki örnek, bir sürükleme işleminin nasıl başlatılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1c80a-116">The following example shows how to initiate a drag operation.</span></span> <span data-ttu-id="1c80a-117">Sürükleme işleminin başladığı denetim bir <xref:System.Windows.Forms.Button> denetimdir, sürüklediğiniz veri denetimin özelliğini temsil eden dizedir <xref:System.Windows.Forms.Control.Text%2A> <xref:System.Windows.Forms.Button> ve izin verilen etkiler kopyalama veya taşıma olur.</span><span class="sxs-lookup"><span data-stu-id="1c80a-117">The control where the drag begins is a <xref:System.Windows.Forms.Button> control, the data being dragged is the string representing the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.Button> control, and the allowed effects are either copying or moving.</span></span>  
  
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
    > <span data-ttu-id="1c80a-118">Herhangi bir veri, yöntemde parametre olarak kullanılabilir `DoDragDrop` ; Yukarıdaki örnekte <xref:System.Windows.Forms.Control.Text%2A> <xref:System.Windows.Forms.Button> denetimin özelliği kullanılmıştır (bir değer kodlanması veya bir veri kümesinden veri almak yerine), özellik sürüklediğiniz konumla ilişkili olduğundan ( <xref:System.Windows.Forms.Button> Denetim).</span><span class="sxs-lookup"><span data-stu-id="1c80a-118">Any data can be used as a parameter in the `DoDragDrop` method; in the example above, the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.Button> control was used (rather than hard-coding a value or retrieving data from a dataset) because the property was related to the location being dragged from (the <xref:System.Windows.Forms.Button> control).</span></span> <span data-ttu-id="1c80a-119">Windows tabanlı uygulamalarınıza sürükle ve bırak işlemleri eklediğinizde bunu göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="1c80a-119">Keep this in mind as you incorporate drag-and-drop operations into your Windows-based applications.</span></span>  
  
 <span data-ttu-id="1c80a-120">Bir sürükleme işlemi etkin olsa da, <xref:System.Windows.Forms.Control.QueryContinueDrag> sürükleme işlemine devam etmek için sistemin "izin sorar" olayını işleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1c80a-120">While a drag operation is in effect, you can handle the <xref:System.Windows.Forms.Control.QueryContinueDrag> event, which "asks permission" of the system to continue the drag operation.</span></span> <span data-ttu-id="1c80a-121">Bu yöntemi işlerken, <xref:System.Windows.Forms.TreeNode> imleç üzerine geldiğinde bir denetimde genişletme gibi, sürükleme işleminde bir etkisi olan yöntemleri çağırdığınızda de uygun bir nokta vardır <xref:System.Windows.Forms.TreeView> .</span><span class="sxs-lookup"><span data-stu-id="1c80a-121">When handling this method, it is also the appropriate point for you to call methods that will have an effect on the drag operation, such as expanding a <xref:System.Windows.Forms.TreeNode> in a <xref:System.Windows.Forms.TreeView> control when the cursor hovers over it.</span></span>  
  
## <a name="dropping-data"></a><span data-ttu-id="1c80a-122">Verileri bırakma</span><span class="sxs-lookup"><span data-stu-id="1c80a-122">Dropping Data</span></span>  
 <span data-ttu-id="1c80a-123">Bir Windows formundaki veya denetimindeki bir konumdan veri sürüklemeye başladıktan sonra doğal olarak bir yere bırakmak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="1c80a-123">Once you have begun dragging data from a location on a Windows Form or control, you will naturally want to drop it somewhere.</span></span> <span data-ttu-id="1c80a-124">İmleç, veri bırakma için doğru şekilde yapılandırılmış bir formun veya denetimin bir alanını aştığında değişecektir.</span><span class="sxs-lookup"><span data-stu-id="1c80a-124">The cursor will change when it crosses an area of a form or control that is correctly configured for dropping data.</span></span> <span data-ttu-id="1c80a-125">Bir Windows form veya denetim içindeki herhangi bir alan, özelliği ayarlayarak ve olayları işleyerek bırakılan verileri kabul etmek için yapılabilir <xref:System.Windows.Forms.Control.AllowDrop%2A> <xref:System.Windows.Forms.Control.DragEnter> <xref:System.Windows.Forms.Control.DragDrop> .</span><span class="sxs-lookup"><span data-stu-id="1c80a-125">Any area within a Windows Form or control can be made to accept dropped data by setting the <xref:System.Windows.Forms.Control.AllowDrop%2A> property and handling the <xref:System.Windows.Forms.Control.DragEnter> and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span>  
  
#### <a name="to-perform-a-drop"></a><span data-ttu-id="1c80a-126">Bir bırakma işlemi gerçekleştirmek için</span><span class="sxs-lookup"><span data-stu-id="1c80a-126">To perform a drop</span></span>  
  
1. <span data-ttu-id="1c80a-127"><xref:System.Windows.Forms.Control.AllowDrop%2A>Özelliği true olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1c80a-127">Set the <xref:System.Windows.Forms.Control.AllowDrop%2A> property to true.</span></span>  
  
2. <span data-ttu-id="1c80a-128">`DragEnter`Bırakma işleminin gerçekleşeceği denetim olayında, sürüklenen verilerin kabul edilebilir bir tür (Bu durumda) olduğundan emin olun <xref:System.Windows.Forms.Control.Text%2A> .</span><span class="sxs-lookup"><span data-stu-id="1c80a-128">In the `DragEnter` event for the control where the drop will occur, ensure that the data being dragged is of an acceptable type (in this case, <xref:System.Windows.Forms.Control.Text%2A>).</span></span> <span data-ttu-id="1c80a-129">Kod daha sonra, Numaralandırmadaki bir değere bırakma gerçekleştiğinde gerçekleşecek etkiyi ayarlar <xref:System.Windows.Forms.DragDropEffects> .</span><span class="sxs-lookup"><span data-stu-id="1c80a-129">The code then sets the effect that will happen when the drop occurs to a value in the <xref:System.Windows.Forms.DragDropEffects> enumeration.</span></span> <span data-ttu-id="1c80a-130">Daha fazla bilgi için bkz. <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.</span><span class="sxs-lookup"><span data-stu-id="1c80a-130">For more information, see <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.</span></span>  
  
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
    > <span data-ttu-id="1c80a-131"><xref:System.Windows.Forms.DataFormats>Yöntemin parametresi olarak kendi nesneniz belirterek kendi uygulamanızı tanımlayabilirsiniz <xref:System.Object> <xref:System.Windows.Forms.DataObject.SetData%2A> .</span><span class="sxs-lookup"><span data-stu-id="1c80a-131">You can define your own <xref:System.Windows.Forms.DataFormats> by specifying your own object as the <xref:System.Object> parameter of the <xref:System.Windows.Forms.DataObject.SetData%2A> method.</span></span> <span data-ttu-id="1c80a-132">Bunu yaparken, belirtilen nesnenin seri hale getirilebilir olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="1c80a-132">Be sure, when doing this, that the object specified is serializable.</span></span> <span data-ttu-id="1c80a-133">Daha fazla bilgi için bkz. <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="1c80a-133">For more information, see <xref:System.Runtime.Serialization.ISerializable>.</span></span>  
  
3. <span data-ttu-id="1c80a-134"><xref:System.Windows.Forms.Control.DragDrop>Bırakma işleminin gerçekleşeceği denetim olayında, <xref:System.Windows.Forms.DataObject.GetData%2A> sürüklediğiniz verileri almak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="1c80a-134">In the <xref:System.Windows.Forms.Control.DragDrop> event for the control where the drop will occur, use the <xref:System.Windows.Forms.DataObject.GetData%2A> method to retrieve the data being dragged.</span></span> <span data-ttu-id="1c80a-135">Daha fazla bilgi için bkz. <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.</span><span class="sxs-lookup"><span data-stu-id="1c80a-135">For more information, see <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.</span></span>  
  
     <span data-ttu-id="1c80a-136">Aşağıdaki örnekte, bir <xref:System.Windows.Forms.TextBox> Denetim Sürüklenmekte olan denetimdir (bırakma gerçekleşir).</span><span class="sxs-lookup"><span data-stu-id="1c80a-136">In the example below, a <xref:System.Windows.Forms.TextBox> control is the control being dragged to (where the drop will occur).</span></span> <span data-ttu-id="1c80a-137">Kod, <xref:System.Windows.Forms.Control.Text%2A> <xref:System.Windows.Forms.TextBox> denetimin özelliğini sürüklenen verilere eşit olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1c80a-137">The code sets the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.TextBox> control equal to the data being dragged.</span></span>  
  
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
    > <span data-ttu-id="1c80a-138">Ayrıca, özelliği ile birlikte çalışarak, <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> sürükle ve bırak işlemi sırasında tuşlara bağlı olarak belirli etkileri oluşur (örneğin, CTRL tuşuna basıldığında sürüklenen verileri kopyalamak standart olur).</span><span class="sxs-lookup"><span data-stu-id="1c80a-138">Additionally, you can work with the <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> property, so that, depending on keys depressed during the drag-and-drop operation, certain effects occur (for example, it is standard to copy the dragged data when the CTRL key is pressed).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c80a-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c80a-139">See also</span></span>

- [<span data-ttu-id="1c80a-140">Nasıl yapılır: Panoya Veri Ekleme</span><span class="sxs-lookup"><span data-stu-id="1c80a-140">How to: Add Data to the Clipboard</span></span>](how-to-add-data-to-the-clipboard.md)
- [<span data-ttu-id="1c80a-141">Nasıl yapılır: Panodan Veri Alma</span><span class="sxs-lookup"><span data-stu-id="1c80a-141">How to: Retrieve Data from the Clipboard</span></span>](how-to-retrieve-data-from-the-clipboard.md)
- [<span data-ttu-id="1c80a-142">Sürükle ve Bırak İşlemleri ve Pano Desteği</span><span class="sxs-lookup"><span data-stu-id="1c80a-142">Drag-and-Drop Operations and Clipboard Support</span></span>](drag-and-drop-operations-and-clipboard-support.md)
