---
title: "Nasıl yapılır: Veri Akışı Bloğunu İptal Etme"
ms.date: 03/30/2017
ms.prod: .net
ms.technology: dotnet-standard
ms.topic: article
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
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3ef7fa62513072e1ee0dc7a8fecf3e600f9c26f2
ms.sourcegitcommit: 6a9030eb5bd0f00e1d144f81958adb195cfb1f6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-cancel-a-dataflow-block"></a><span data-ttu-id="25db1-102">Nasıl yapılır: Veri Akışı Bloğunu İptal Etme</span><span class="sxs-lookup"><span data-stu-id="25db1-102">How to: Cancel a Dataflow Block</span></span>
<span data-ttu-id="25db1-103">Bu belge, uygulamanızda iptalini etkinleştir gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="25db1-103">This document demonstrates how to enable cancellation in your application.</span></span> <span data-ttu-id="25db1-104">Bu örnekte, iş öğelerini bir veri akışı ardışık yanı sıra iptal etkilerini etkin olduğu göstermek için Windows Forms kullanır.</span><span class="sxs-lookup"><span data-stu-id="25db1-104">This example uses Windows Forms to show where work items are active in a dataflow pipeline and also the effects of cancellation.</span></span>  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="to-create-the-windows-forms-application"></a><span data-ttu-id="25db1-105">Form uygulama Windows oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="25db1-105">To Create the Windows Forms Application</span></span>  
  
1.  <span data-ttu-id="25db1-106">Bir C# veya Visual Basic oluşturma **Windows Forms uygulaması** projesi.</span><span class="sxs-lookup"><span data-stu-id="25db1-106">Create a C# or Visual Basic **Windows Forms Application** project.</span></span> <span data-ttu-id="25db1-107">Aşağıdaki adımlarda proje adı `CancellationWinForms`.</span><span class="sxs-lookup"><span data-stu-id="25db1-107">In the following steps, the project is named `CancellationWinForms`.</span></span>  
  
2.  <span data-ttu-id="25db1-108">Form1.cs ana form için form tasarımcısında (Form1.vb için [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), ekleme bir <xref:System.Windows.Forms.ToolStrip> denetim.</span><span class="sxs-lookup"><span data-stu-id="25db1-108">On the form designer for the main form, Form1.cs (Form1.vb for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), add a <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
3.  <span data-ttu-id="25db1-109">Ekleme bir <xref:System.Windows.Forms.ToolStripButton> denetimini <xref:System.Windows.Forms.ToolStrip> denetim.</span><span class="sxs-lookup"><span data-stu-id="25db1-109">Add a <xref:System.Windows.Forms.ToolStripButton> control to the <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="25db1-110">Ayarlama <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> özelliğine <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> ve <xref:System.Windows.Forms.ToolStripItem.Text%2A> özelliğine **çalışma öğeleri ekleme**.</span><span class="sxs-lookup"><span data-stu-id="25db1-110">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> and the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to **Add Work Items**.</span></span>  
  
4.  <span data-ttu-id="25db1-111">İkinci bir ekleme <xref:System.Windows.Forms.ToolStripButton> denetimini <xref:System.Windows.Forms.ToolStrip> denetim.</span><span class="sxs-lookup"><span data-stu-id="25db1-111">Add a second <xref:System.Windows.Forms.ToolStripButton> control to the <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="25db1-112">Ayarlama <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> özelliğine <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, <xref:System.Windows.Forms.ToolStripItem.Text%2A> özelliğine **iptal**ve <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> özelliğine `False`.</span><span class="sxs-lookup"><span data-stu-id="25db1-112">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to **Cancel**, and the <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> property to `False`.</span></span>  
  
5.  <span data-ttu-id="25db1-113">Dört eklemek <xref:System.Windows.Forms.ToolStripProgressBar> nesneleri <xref:System.Windows.Forms.ToolStrip> denetim.</span><span class="sxs-lookup"><span data-stu-id="25db1-113">Add four <xref:System.Windows.Forms.ToolStripProgressBar> objects to the <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
## <a name="creating-the-dataflow-pipeline"></a><span data-ttu-id="25db1-114">Veri akışı ardışık düzenleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="25db1-114">Creating the Dataflow Pipeline</span></span>  
 <span data-ttu-id="25db1-115">Bu bölümde, iş öğelerini işler ve ilerleme çubukları güncelleştiren veri akışı ardışık düzen oluşturmak açıklar.</span><span class="sxs-lookup"><span data-stu-id="25db1-115">This section describes how to create the dataflow pipeline that processes work items and updates the progress bars.</span></span>  
  
### <a name="to-create-the-dataflow-pipeline"></a><span data-ttu-id="25db1-116">Veri akışı ardışık düzen oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="25db1-116">To Create the Dataflow Pipeline</span></span>  
  
1.  <span data-ttu-id="25db1-117">Projenizde, System.Threading.Tasks.Dataflow.dll bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="25db1-117">In your project, add a reference to System.Threading.Tasks.Dataflow.dll.</span></span>  
  
2.  <span data-ttu-id="25db1-118">Sağlamak Bu Form1.cs (Form1.vb için [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) aşağıdakileri içerir `using` deyimleri (`Imports` içinde [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="25db1-118">Ensure that Form1.cs (Form1.vb for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) contains the following `using` statements (`Imports` in [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]).</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#1)]  
  
3.  <span data-ttu-id="25db1-119">Ekleme `WorkItem` sınıfı bir iç türü olarak `Form1` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="25db1-119">Add the `WorkItem` class as an inner type of the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#2)]  
  
4.  <span data-ttu-id="25db1-120">Aşağıdaki veri üye ekleme `Form1` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="25db1-120">Add the following data members to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#3)]  
  
5.  <span data-ttu-id="25db1-121">Aşağıdaki yöntemi ekleyin `CreatePipeline`, `Form1` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="25db1-121">Add the following method, `CreatePipeline`, to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#4)]  
  
 <span data-ttu-id="25db1-122">Çünkü `incrementProgress` ve `decrementProgress` veri akışı blokları hareket kullanıcı arabiriminde, onu önemlidir bu eylemler kullanıcı arabirimi iş parçacığı üzerinde gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="25db1-122">Because the `incrementProgress` and `decrementProgress` dataflow blocks act on the user interface, it is important that these actions occur on the user-interface thread.</span></span> <span data-ttu-id="25db1-123">Bu, oluşturma sırasında bu nesnelerin her sağlamak gerçekleştirmek için bir <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> olan nesneyi <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> özelliğini <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="25db1-123">To accomplish this, during construction these objects each provide a <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> object that has the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> property set to <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="25db1-124"><xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> Yöntemi oluşturur bir <xref:System.Threading.Tasks.TaskScheduler> geçerli eşitleme bağlamı üzerinde çalışmayı gerçekleştiren nesne.</span><span class="sxs-lookup"><span data-stu-id="25db1-124">The <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> method creates a <xref:System.Threading.Tasks.TaskScheduler> object that performs work on the current synchronization context.</span></span> <span data-ttu-id="25db1-125">Çünkü `Form1` Oluşturucusu eylemleri için kullanıcı arabirimi iş parçacığı çağrılır `incrementProgress` ve `decrementProgress` veri akışı blokları kullanıcı arabirimi iş parçacığı üzerinde de çalışır.</span><span class="sxs-lookup"><span data-stu-id="25db1-125">Because the `Form1` constructor is called from the user-interface thread, the actions for the `incrementProgress` and `decrementProgress` dataflow blocks also run on the user-interface thread.</span></span>  
  
 <span data-ttu-id="25db1-126">Bu örnek ayarlar <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> ardışık düzen üyeleri yapılandırdığında özelliği.</span><span class="sxs-lookup"><span data-stu-id="25db1-126">This example sets the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> property when it constructs the members of the pipeline.</span></span> <span data-ttu-id="25db1-127">Çünkü <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> özelliği kalıcı olarak veri akışı bloğu yürütme iptal eder, sonra kullanıcı işlemi iptal ve ardışık düzene daha fazla iş öğelerini eklemek istediği tüm ardışık düzeni yeniden oluşturulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="25db1-127">Because the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> property permanently cancels dataflow block execution, the whole pipeline must be recreated after the user cancels the operation and then wants to add more work items to the pipeline.</span></span> <span data-ttu-id="25db1-128">Böylece bir işlem iptal edildikten sonra diğer iş gerçekleştirilebilir veri akışı bloğunu iptal etmek için alternatif bir yol gösteren bir örnek için bkz: [izlenecek yol: veri akışı kullanarak bir Windows Forms uygulamasında](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).</span><span class="sxs-lookup"><span data-stu-id="25db1-128">For an example that demonstrates an alternative way to cancel a dataflow block so that other work can be performed after an operation is canceled, see [Walkthrough: Using Dataflow in a Windows Forms Application](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).</span></span>  
  
## <a name="connecting-the-dataflow-pipeline-to-the-user-interface"></a><span data-ttu-id="25db1-129">Veri akışı ardışık düzeni için kullanıcı arabirimi bağlanma</span><span class="sxs-lookup"><span data-stu-id="25db1-129">Connecting the Dataflow Pipeline to the User Interface</span></span>  
 <span data-ttu-id="25db1-130">Bu bölümde, veri akışı ardışık düzeni için kullanıcı arabirimi bağlanmak açıklar.</span><span class="sxs-lookup"><span data-stu-id="25db1-130">This section describes how to connect the dataflow pipeline to the user interface.</span></span> <span data-ttu-id="25db1-131">Ardışık düzen oluşturma hem çalışma öğelerini ardışık düzenine eklemek için olay işleyicisi tarafından denetlenen **çalışma öğeleri ekleme** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="25db1-131">Both creating the pipeline and adding work items to the pipeline are controlled by the event handler for the **Add Work Items** button.</span></span> <span data-ttu-id="25db1-132">İptal tarafından başlatılır **iptal** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="25db1-132">Cancellation is initiated by the **Cancel** button.</span></span> <span data-ttu-id="25db1-133">Kullanıcı ya da bu düğmeleri tıkladığında, uygun eylemi bir zaman uyumsuz olarak başlatılır.</span><span class="sxs-lookup"><span data-stu-id="25db1-133">When the user clicks either of these buttons, the appropriate action is initiated in an asynchronous manner.</span></span>  
  
### <a name="to-connect-the-dataflow-pipeline-to-the-user-interface"></a><span data-ttu-id="25db1-134">Veri akışı ardışık düzeni için kullanıcı arabirimi bağlanmak için</span><span class="sxs-lookup"><span data-stu-id="25db1-134">To Connect the Dataflow Pipeline to the User Interface</span></span>  
  
1.  <span data-ttu-id="25db1-135">Ana form için form designer'ı oluşturmak için bir olay işleyicisi <xref:System.Windows.Forms.ToolStripItem.Click> olayı için **çalışma öğeleri ekleme** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="25db1-135">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Add Work Items** button.</span></span>  
  
2.  <span data-ttu-id="25db1-136">Uygulama <xref:System.Windows.Forms.ToolStripItem.Click> olayı için **çalışma öğeleri ekleme** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="25db1-136">Implement the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Add Work Items** button.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#5)]  
  
3.  <span data-ttu-id="25db1-137">Ana form için form designer'ı oluşturmak için bir olay işleyicisi <xref:System.Windows.Forms.ToolStripItem.Click> için olay işleyicisini **iptal** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="25db1-137">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for the **Cancel** button.</span></span>  
  
4.  <span data-ttu-id="25db1-138">Uygulama <xref:System.Windows.Forms.ToolStripItem.Click> için olay işleyicisini **iptal** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="25db1-138">Implement the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for the **Cancel** button.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="25db1-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="25db1-139">Example</span></span>  
 <span data-ttu-id="25db1-140">Aşağıdaki örnek Form1.cs için tam kod gösterilir (Form1.vb için [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="25db1-140">The following example shows the complete code for Form1.cs (Form1.vb for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]).</span></span>  
  
 [!code-csharp[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#100)]  
  
 <span data-ttu-id="25db1-141">Aşağıdaki çizimde çalışan uygulama gösterir.</span><span class="sxs-lookup"><span data-stu-id="25db1-141">The following illustration shows the running application.</span></span>  
  
 <span data-ttu-id="25db1-142">![Windows Forms uygulaması](../../../docs/standard/parallel-programming/media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")</span><span class="sxs-lookup"><span data-stu-id="25db1-142">![The Windows Forms Application](../../../docs/standard/parallel-programming/media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")</span></span>  

## <a name="see-also"></a><span data-ttu-id="25db1-143">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="25db1-143">See Also</span></span>  
 [<span data-ttu-id="25db1-144">Veri akışı</span><span class="sxs-lookup"><span data-stu-id="25db1-144">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
