---
title: 'Nasıl yapılır: Veri Akışı Bloğunu İptal Etme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- dataflow blocks, canceling in TPL
- TPL dataflow library,canceling dataflow blocks
ms.assetid: fbddda0d-da3b-4ec8-a1d6-67ab8573fcd7
ms.openlocfilehash: 530c231deeaba007975849ab6dc41f4da6a859ea
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84285553"
---
# <a name="how-to-cancel-a-dataflow-block"></a><span data-ttu-id="f42b2-102">Nasıl yapılır: Veri Akışı Bloğunu İptal Etme</span><span class="sxs-lookup"><span data-stu-id="f42b2-102">How to: Cancel a Dataflow Block</span></span>
<span data-ttu-id="f42b2-103">Bu belgede, uygulamanızda iptalin nasıl etkinleştirileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f42b2-103">This document demonstrates how to enable cancellation in your application.</span></span> <span data-ttu-id="f42b2-104">Bu örnek, iş öğelerinin bir veri akışı ardışık düzeninde etkin olduğunu ve ayrıca İptalin etkilerini göstermek için Windows Forms kullanır.</span><span class="sxs-lookup"><span data-stu-id="f42b2-104">This example uses Windows Forms to show where work items are active in a dataflow pipeline and also the effects of cancellation.</span></span>  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="to-create-the-windows-forms-application"></a><span data-ttu-id="f42b2-105">Windows Forms uygulamasını oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="f42b2-105">To Create the Windows Forms Application</span></span>  
  
1. <span data-ttu-id="f42b2-106">Bir C# veya Visual Basic **Windows Forms uygulama** projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f42b2-106">Create a C# or Visual Basic **Windows Forms Application** project.</span></span> <span data-ttu-id="f42b2-107">Aşağıdaki adımlarda proje adlandırılır `CancellationWinForms` .</span><span class="sxs-lookup"><span data-stu-id="f42b2-107">In the following steps, the project is named `CancellationWinForms`.</span></span>  
  
2. <span data-ttu-id="f42b2-108">Ana form için form tasarımcısında, Form1.cs (Visual Basic için Form1. vb), bir <xref:System.Windows.Forms.ToolStrip> denetim ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f42b2-108">On the form designer for the main form, Form1.cs (Form1.vb for Visual Basic), add a <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
3. <span data-ttu-id="f42b2-109"><xref:System.Windows.Forms.ToolStripButton>Denetime denetim ekleyin <xref:System.Windows.Forms.ToolStrip> .</span><span class="sxs-lookup"><span data-stu-id="f42b2-109">Add a <xref:System.Windows.Forms.ToolStripButton> control to the <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="f42b2-110"><xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> <xref:System.Windows.Forms.ToolStripItem.Text%2A> **Çalışma öğeleri eklemek**için özelliğini ve özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f42b2-110">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> and the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to **Add Work Items**.</span></span>  
  
4. <span data-ttu-id="f42b2-111">Denetime ikinci bir <xref:System.Windows.Forms.ToolStripButton> denetim ekleyin <xref:System.Windows.Forms.ToolStrip> .</span><span class="sxs-lookup"><span data-stu-id="f42b2-111">Add a second <xref:System.Windows.Forms.ToolStripButton> control to the <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="f42b2-112"><xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>Özelliğini <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> , <xref:System.Windows.Forms.ToolStripItem.Text%2A> **iptal**edilecek özelliği ve özelliğini olarak ayarlayın <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> `False` .</span><span class="sxs-lookup"><span data-stu-id="f42b2-112">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to **Cancel**, and the <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> property to `False`.</span></span>  
  
5. <span data-ttu-id="f42b2-113">Denetime dört <xref:System.Windows.Forms.ToolStripProgressBar> nesne ekleyin <xref:System.Windows.Forms.ToolStrip> .</span><span class="sxs-lookup"><span data-stu-id="f42b2-113">Add four <xref:System.Windows.Forms.ToolStripProgressBar> objects to the <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
## <a name="creating-the-dataflow-pipeline"></a><span data-ttu-id="f42b2-114">Veri akışı işlem hattı oluşturma</span><span class="sxs-lookup"><span data-stu-id="f42b2-114">Creating the Dataflow Pipeline</span></span>  
 <span data-ttu-id="f42b2-115">Bu bölümde, iş öğelerini işleyen ve ilerleme çubuğunu güncelleştiren veri akışı işlem hattının nasıl oluşturulacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f42b2-115">This section describes how to create the dataflow pipeline that processes work items and updates the progress bars.</span></span>  
  
### <a name="to-create-the-dataflow-pipeline"></a><span data-ttu-id="f42b2-116">Veri akışı ardışık düzeni oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="f42b2-116">To Create the Dataflow Pipeline</span></span>  
  
1. <span data-ttu-id="f42b2-117">Projenizde, System. Threading. Tasks. Dataflow. dll ' ye bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f42b2-117">In your project, add a reference to System.Threading.Tasks.Dataflow.dll.</span></span>  
  
2. <span data-ttu-id="f42b2-118">Form1.cs (Visual Basic için Form1. vb) 'in aşağıdaki deyimlerini (Visual Basic) içerdiğinden emin olun `using` `Imports` .</span><span class="sxs-lookup"><span data-stu-id="f42b2-118">Ensure that Form1.cs (Form1.vb for Visual Basic) contains the following `using` statements (`Imports` in Visual Basic).</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#1)]  
  
3. <span data-ttu-id="f42b2-119">Sınıfını `WorkItem` sınıfının bir iç türü olarak ekleyin `Form1` .</span><span class="sxs-lookup"><span data-stu-id="f42b2-119">Add the `WorkItem` class as an inner type of the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#2)]  
  
4. <span data-ttu-id="f42b2-120">Sınıfına aşağıdaki veri üyelerini ekleyin `Form1` .</span><span class="sxs-lookup"><span data-stu-id="f42b2-120">Add the following data members to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#3)]  
  
5. <span data-ttu-id="f42b2-121">Aşağıdaki yöntemini `CreatePipeline` `Form1` sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f42b2-121">Add the following method, `CreatePipeline`, to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#4)]  
  
 <span data-ttu-id="f42b2-122">`incrementProgress`Ve `decrementProgress` veri akışı blokları Kullanıcı arabiriminde işlem yaptığından, bu eylemlerin Kullanıcı arabirimi iş parçacığında gerçekleştirilmesi önemlidir.</span><span class="sxs-lookup"><span data-stu-id="f42b2-122">Because the `incrementProgress` and `decrementProgress` dataflow blocks act on the user interface, it is important that these actions occur on the user-interface thread.</span></span> <span data-ttu-id="f42b2-123">Bunu gerçekleştirmek için, oluşturma sırasında bu nesnelerin her biri, <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> özelliği olarak ayarlanmış bir nesne sağlar <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="f42b2-123">To accomplish this, during construction these objects each provide a <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> object that has the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> property set to <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f42b2-124"><xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>Yöntemi, <xref:System.Threading.Tasks.TaskScheduler> geçerli eşitleme bağlamında çalışmayı gerçekleştiren bir nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f42b2-124">The <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> method creates a <xref:System.Threading.Tasks.TaskScheduler> object that performs work on the current synchronization context.</span></span> <span data-ttu-id="f42b2-125">`Form1`Oluşturucu kullanıcı arabirimi iş parçacığından çağrıldığı için, `incrementProgress` ve `decrementProgress` veri akışı blokları için Eylemler kullanıcı arabirimi iş parçacığında da çalışır.</span><span class="sxs-lookup"><span data-stu-id="f42b2-125">Because the `Form1` constructor is called from the user-interface thread, the actions for the `incrementProgress` and `decrementProgress` dataflow blocks also run on the user-interface thread.</span></span>  
  
 <span data-ttu-id="f42b2-126">Bu örnek, <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> işlem hattının üyelerini oluştururken özelliği ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f42b2-126">This example sets the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> property when it constructs the members of the pipeline.</span></span> <span data-ttu-id="f42b2-127">Özelliği, <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> veri akışı blok yürütmeyi kalıcı olarak iptal ettiğinden, Kullanıcı işlemi iptal ettikten sonra işlem hattına daha fazla iş öğesi eklemek istediğinde tüm işlem hattının yeniden oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f42b2-127">Because the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> property permanently cancels dataflow block execution, the whole pipeline must be recreated after the user cancels the operation and then wants to add more work items to the pipeline.</span></span> <span data-ttu-id="f42b2-128">Bir işlem iptal edildikten sonra diğer çalışmanın gerçekleştirilebilmesi için bir veri akışı bloğunu iptal etmenin alternatif bir yolunu gösteren bir örnek için, bkz. [Izlenecek yol: Windows Forms uygulamasında veri akışı kullanma](walkthrough-using-dataflow-in-a-windows-forms-application.md).</span><span class="sxs-lookup"><span data-stu-id="f42b2-128">For an example that demonstrates an alternative way to cancel a dataflow block so that other work can be performed after an operation is canceled, see [Walkthrough: Using Dataflow in a Windows Forms Application](walkthrough-using-dataflow-in-a-windows-forms-application.md).</span></span>  
  
## <a name="connecting-the-dataflow-pipeline-to-the-user-interface"></a><span data-ttu-id="f42b2-129">Veri akışı ardışık düzenini Kullanıcı arabirimine bağlama</span><span class="sxs-lookup"><span data-stu-id="f42b2-129">Connecting the Dataflow Pipeline to the User Interface</span></span>  
 <span data-ttu-id="f42b2-130">Bu bölümde, veri akışı ardışık düzeninin Kullanıcı arabirimine nasıl bağlanacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f42b2-130">This section describes how to connect the dataflow pipeline to the user interface.</span></span> <span data-ttu-id="f42b2-131">İşlem hattının oluşturulması ve iş öğelerinin işlem hattına eklenmesi, **Iş öğeleri ekle** düğmesi için olay işleyicisi tarafından denetlenir.</span><span class="sxs-lookup"><span data-stu-id="f42b2-131">Both creating the pipeline and adding work items to the pipeline are controlled by the event handler for the **Add Work Items** button.</span></span> <span data-ttu-id="f42b2-132">İptali, **iptal** düğmesi tarafından başlatılır.</span><span class="sxs-lookup"><span data-stu-id="f42b2-132">Cancellation is initiated by the **Cancel** button.</span></span> <span data-ttu-id="f42b2-133">Kullanıcı bu düğmelerden birini tıkladığında, uygun eylem zaman uyumsuz bir şekilde başlatılır.</span><span class="sxs-lookup"><span data-stu-id="f42b2-133">When the user clicks either of these buttons, the appropriate action is initiated in an asynchronous manner.</span></span>  
  
### <a name="to-connect-the-dataflow-pipeline-to-the-user-interface"></a><span data-ttu-id="f42b2-134">Veri akışı ardışık düzenini Kullanıcı arabirimine bağlamak için</span><span class="sxs-lookup"><span data-stu-id="f42b2-134">To Connect the Dataflow Pipeline to the User Interface</span></span>  
  
1. <span data-ttu-id="f42b2-135">Ana form için form tasarımcısında, <xref:System.Windows.Forms.ToolStripItem.Click> **Iş öğeleri ekle** düğmesine yönelik olay için bir olay işleyicisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f42b2-135">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Add Work Items** button.</span></span>  
  
2. <span data-ttu-id="f42b2-136"><xref:System.Windows.Forms.ToolStripItem.Click> **Iş öğeleri ekle** düğmesine yönelik olayı uygulayın.</span><span class="sxs-lookup"><span data-stu-id="f42b2-136">Implement the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Add Work Items** button.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#5)]  
  
3. <span data-ttu-id="f42b2-137">Ana form için form tasarımcısında, <xref:System.Windows.Forms.ToolStripItem.Click> **iptal** düğmesine yönelik olay işleyicisi için bir olay işleyicisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f42b2-137">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for the **Cancel** button.</span></span>  
  
4. <span data-ttu-id="f42b2-138"><xref:System.Windows.Forms.ToolStripItem.Click> **İptal** düğmesi için olay işleyicisini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="f42b2-138">Implement the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for the **Cancel** button.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="f42b2-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="f42b2-139">Example</span></span>  
 <span data-ttu-id="f42b2-140">Aşağıdaki örnek, Form1.cs için tüm kodu gösterir (Visual Basic için Form1. vb).</span><span class="sxs-lookup"><span data-stu-id="f42b2-140">The following example shows the complete code for Form1.cs (Form1.vb for Visual Basic).</span></span>  
  
 [!code-csharp[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#100)]  
  
 <span data-ttu-id="f42b2-141">Aşağıdaki çizimde çalışan uygulama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f42b2-141">The following illustration shows the running application.</span></span>  
  
 <span data-ttu-id="f42b2-142">![Windows Forms uygulaması](media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")</span><span class="sxs-lookup"><span data-stu-id="f42b2-142">![The Windows Forms Application](media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")</span></span>  

## <a name="see-also"></a><span data-ttu-id="f42b2-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f42b2-143">See also</span></span>

- [<span data-ttu-id="f42b2-144">Veri akışı</span><span class="sxs-lookup"><span data-stu-id="f42b2-144">Dataflow</span></span>](dataflow-task-parallel-library.md)
