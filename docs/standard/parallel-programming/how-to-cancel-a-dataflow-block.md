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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b95f0a3535716c4a01dae52abe38eb850f080cf0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62018962"
---
# <a name="how-to-cancel-a-dataflow-block"></a><span data-ttu-id="7f0e9-102">Nasıl yapılır: Veri Akışı Bloğunu İptal Etme</span><span class="sxs-lookup"><span data-stu-id="7f0e9-102">How to: Cancel a Dataflow Block</span></span>
<span data-ttu-id="7f0e9-103">Bu belge, uygulamanızdaki iptalin gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7f0e9-103">This document demonstrates how to enable cancellation in your application.</span></span> <span data-ttu-id="7f0e9-104">Bu örnekte, iş öğelerini bir veri akışı işlem hattı ve ayrıca iptal etkilerini etkin olduğu göstermek için Windows Forms kullanır.</span><span class="sxs-lookup"><span data-stu-id="7f0e9-104">This example uses Windows Forms to show where work items are active in a dataflow pipeline and also the effects of cancellation.</span></span>  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="to-create-the-windows-forms-application"></a><span data-ttu-id="7f0e9-105">Formları uygulaması Windows oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="7f0e9-105">To Create the Windows Forms Application</span></span>  
  
1. <span data-ttu-id="7f0e9-106">Bir C# veya Visual Basic oluşturma **Windows Forms uygulaması** proje.</span><span class="sxs-lookup"><span data-stu-id="7f0e9-106">Create a C# or Visual Basic **Windows Forms Application** project.</span></span> <span data-ttu-id="7f0e9-107">Aşağıdaki adımlarda, proje adı `CancellationWinForms`.</span><span class="sxs-lookup"><span data-stu-id="7f0e9-107">In the following steps, the project is named `CancellationWinForms`.</span></span>  
  
2. <span data-ttu-id="7f0e9-108">Ana form için form tasarımcıda Form1.cs (Visual Basic için Form1.vb), ekleme bir <xref:System.Windows.Forms.ToolStrip> denetimi.</span><span class="sxs-lookup"><span data-stu-id="7f0e9-108">On the form designer for the main form, Form1.cs (Form1.vb for Visual Basic), add a <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
3. <span data-ttu-id="7f0e9-109">Ekleme bir <xref:System.Windows.Forms.ToolStripButton> denetimini <xref:System.Windows.Forms.ToolStrip> denetimi.</span><span class="sxs-lookup"><span data-stu-id="7f0e9-109">Add a <xref:System.Windows.Forms.ToolStripButton> control to the <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="7f0e9-110">Ayarlama <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> özelliğini <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> ve <xref:System.Windows.Forms.ToolStripItem.Text%2A> özelliğini **çalışma öğeleri ekleme**.</span><span class="sxs-lookup"><span data-stu-id="7f0e9-110">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> and the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to **Add Work Items**.</span></span>  
  
4. <span data-ttu-id="7f0e9-111">İkinci bir ekleme <xref:System.Windows.Forms.ToolStripButton> denetimini <xref:System.Windows.Forms.ToolStrip> denetimi.</span><span class="sxs-lookup"><span data-stu-id="7f0e9-111">Add a second <xref:System.Windows.Forms.ToolStripButton> control to the <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="7f0e9-112">Ayarlama <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> özelliğini <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, <xref:System.Windows.Forms.ToolStripItem.Text%2A> özelliğini **iptal**ve <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> özelliğini `False`.</span><span class="sxs-lookup"><span data-stu-id="7f0e9-112">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to **Cancel**, and the <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> property to `False`.</span></span>  
  
5. <span data-ttu-id="7f0e9-113">Dört ekleme <xref:System.Windows.Forms.ToolStripProgressBar> nesneleri için <xref:System.Windows.Forms.ToolStrip> denetimi.</span><span class="sxs-lookup"><span data-stu-id="7f0e9-113">Add four <xref:System.Windows.Forms.ToolStripProgressBar> objects to the <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
## <a name="creating-the-dataflow-pipeline"></a><span data-ttu-id="7f0e9-114">Veri akışı işlem hattı oluşturma</span><span class="sxs-lookup"><span data-stu-id="7f0e9-114">Creating the Dataflow Pipeline</span></span>  
 <span data-ttu-id="7f0e9-115">Bu bölümde iş öğelerini işler ve ilerleme çubukları güncelleştiren veri akışı işlem hattı oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="7f0e9-115">This section describes how to create the dataflow pipeline that processes work items and updates the progress bars.</span></span>  
  
### <a name="to-create-the-dataflow-pipeline"></a><span data-ttu-id="7f0e9-116">Veri akışı işlem hattını oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="7f0e9-116">To Create the Dataflow Pipeline</span></span>  
  
1. <span data-ttu-id="7f0e9-117">Projenizde, System.Threading.Tasks.Dataflow.dll'ye birer başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7f0e9-117">In your project, add a reference to System.Threading.Tasks.Dataflow.dll.</span></span>  
  
2. <span data-ttu-id="7f0e9-118">Form1.cs (Visual Basic için Form1.vb) aşağıdaki içerdiğinden emin olun `using` deyimleri (`Imports` Visual Basic'te).</span><span class="sxs-lookup"><span data-stu-id="7f0e9-118">Ensure that Form1.cs (Form1.vb for Visual Basic) contains the following `using` statements (`Imports` in Visual Basic).</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#1)]  
  
3. <span data-ttu-id="7f0e9-119">Ekleme `WorkItem` sınıfı iç bir tür olarak `Form1` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7f0e9-119">Add the `WorkItem` class as an inner type of the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#2)]  
  
4. <span data-ttu-id="7f0e9-120">Aşağıdaki veri üyelerini ekleyin `Form1` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7f0e9-120">Add the following data members to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#3)]  
  
5. <span data-ttu-id="7f0e9-121">Aşağıdaki yöntemi ekleyin `CreatePipeline`, `Form1` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7f0e9-121">Add the following method, `CreatePipeline`, to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#4)]  
  
 <span data-ttu-id="7f0e9-122">Çünkü `incrementProgress` ve `decrementProgress` veri akışı blokları hareket kullanıcı arabiriminde, önemlidir bu eylemler kullanıcı arabirimi iş parçacığı üzerinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="7f0e9-122">Because the `incrementProgress` and `decrementProgress` dataflow blocks act on the user interface, it is important that these actions occur on the user-interface thread.</span></span> <span data-ttu-id="7f0e9-123">Bu, bu nesnelerin her sağlamak yapım sırasında gerçekleştirmek için bir <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> nesnesi <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> özelliğini <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7f0e9-123">To accomplish this, during construction these objects each provide a <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> object that has the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> property set to <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7f0e9-124"><xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> Yöntemi oluşturur bir <xref:System.Threading.Tasks.TaskScheduler> geçerli eşitleme kapsamının üzerinde işini gerçekleştiren nesne.</span><span class="sxs-lookup"><span data-stu-id="7f0e9-124">The <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> method creates a <xref:System.Threading.Tasks.TaskScheduler> object that performs work on the current synchronization context.</span></span> <span data-ttu-id="7f0e9-125">Çünkü `Form1` Oluşturucusu eylemleri için kullanıcı arabirimi iş parçacığından çağrılır `incrementProgress` ve `decrementProgress` veri akışı bloklarının kullanıcı arabirimi iş parçacığı üzerinde de çalışır.</span><span class="sxs-lookup"><span data-stu-id="7f0e9-125">Because the `Form1` constructor is called from the user-interface thread, the actions for the `incrementProgress` and `decrementProgress` dataflow blocks also run on the user-interface thread.</span></span>  
  
 <span data-ttu-id="7f0e9-126">Bu örnekte ayarlar <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> üyeleri işlem hattının yapılandırdığında özelliği.</span><span class="sxs-lookup"><span data-stu-id="7f0e9-126">This example sets the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> property when it constructs the members of the pipeline.</span></span> <span data-ttu-id="7f0e9-127">Çünkü <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> özelliği veri akışı bloğu yürütme kalıcı olarak iptal eder, kullanıcı işlemi iptal eder ve daha fazla iş öğelerini işlem hattının eklemek istiyor sonra işlem hattının tamamını yeniden oluşturulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7f0e9-127">Because the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> property permanently cancels dataflow block execution, the whole pipeline must be recreated after the user cancels the operation and then wants to add more work items to the pipeline.</span></span> <span data-ttu-id="7f0e9-128">Böylece bir işlem iptal edildikten sonra diğer iş gerçekleştirilebilir bir veri akışı bloğunu iptal etme alternatif bir yolu gösteren bir örnek için bkz: [izlenecek yol: Veri akışı kullanarak bir Windows Forms uygulamalarındaki](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).</span><span class="sxs-lookup"><span data-stu-id="7f0e9-128">For an example that demonstrates an alternative way to cancel a dataflow block so that other work can be performed after an operation is canceled, see [Walkthrough: Using Dataflow in a Windows Forms Application](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).</span></span>  
  
## <a name="connecting-the-dataflow-pipeline-to-the-user-interface"></a><span data-ttu-id="7f0e9-129">Veri akışı işlem hattı kullanıcı arabirimine bağlanma</span><span class="sxs-lookup"><span data-stu-id="7f0e9-129">Connecting the Dataflow Pipeline to the User Interface</span></span>  
 <span data-ttu-id="7f0e9-130">Bu bölümde, veri akışı işlem hattı kullanıcı arabirimine bağlamak açıklar.</span><span class="sxs-lookup"><span data-stu-id="7f0e9-130">This section describes how to connect the dataflow pipeline to the user interface.</span></span> <span data-ttu-id="7f0e9-131">İşlem hattı oluşturmak ve iş öğelerini işlem hattının ekleme için olay işleyicisi tarafından denetlenen **iş öğeleri ekleme** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="7f0e9-131">Both creating the pipeline and adding work items to the pipeline are controlled by the event handler for the **Add Work Items** button.</span></span> <span data-ttu-id="7f0e9-132">İptal tarafından başlatılır **iptal** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="7f0e9-132">Cancellation is initiated by the **Cancel** button.</span></span> <span data-ttu-id="7f0e9-133">Kullanıcı bir düğmeye tıkladığında, uygun eylemi zaman uyumsuz olarak başlatılır.</span><span class="sxs-lookup"><span data-stu-id="7f0e9-133">When the user clicks either of these buttons, the appropriate action is initiated in an asynchronous manner.</span></span>  
  
### <a name="to-connect-the-dataflow-pipeline-to-the-user-interface"></a><span data-ttu-id="7f0e9-134">Veri akışı işlem hattı kullanıcı arabirimine bağlamak için</span><span class="sxs-lookup"><span data-stu-id="7f0e9-134">To Connect the Dataflow Pipeline to the User Interface</span></span>  
  
1. <span data-ttu-id="7f0e9-135">Ana form için form tasarımcıda oluşturmak için bir olay işleyicisi <xref:System.Windows.Forms.ToolStripItem.Click> olayı **çalışma öğeleri ekleme** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="7f0e9-135">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Add Work Items** button.</span></span>  
  
2. <span data-ttu-id="7f0e9-136">Uygulama <xref:System.Windows.Forms.ToolStripItem.Click> olayı **çalışma öğeleri ekleme** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="7f0e9-136">Implement the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Add Work Items** button.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#5)]  
  
3. <span data-ttu-id="7f0e9-137">Ana form için form tasarımcıda oluşturmak için bir olay işleyicisi <xref:System.Windows.Forms.ToolStripItem.Click> için olay işleyicisi **iptal** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="7f0e9-137">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for the **Cancel** button.</span></span>  
  
4. <span data-ttu-id="7f0e9-138">Uygulama <xref:System.Windows.Forms.ToolStripItem.Click> için olay işleyicisi **iptal** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="7f0e9-138">Implement the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for the **Cancel** button.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="7f0e9-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="7f0e9-139">Example</span></span>  
 <span data-ttu-id="7f0e9-140">Aşağıdaki örnek, Form1.cs (Visual Basic için Form1.vb) için tam kod gösterilir.</span><span class="sxs-lookup"><span data-stu-id="7f0e9-140">The following example shows the complete code for Form1.cs (Form1.vb for Visual Basic).</span></span>  
  
 [!code-csharp[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#100)]  
  
 <span data-ttu-id="7f0e9-141">Aşağıdaki çizim, çalışan uygulamayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="7f0e9-141">The following illustration shows the running application.</span></span>  
  
 <span data-ttu-id="7f0e9-142">![Windows Forms uygulamalarındaki](../../../docs/standard/parallel-programming/media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")</span><span class="sxs-lookup"><span data-stu-id="7f0e9-142">![The Windows Forms Application](../../../docs/standard/parallel-programming/media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")</span></span>  

## <a name="see-also"></a><span data-ttu-id="7f0e9-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f0e9-143">See also</span></span>

- [<span data-ttu-id="7f0e9-144">Veri akışı</span><span class="sxs-lookup"><span data-stu-id="7f0e9-144">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
