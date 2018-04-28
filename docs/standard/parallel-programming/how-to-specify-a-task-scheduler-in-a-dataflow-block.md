---
title: 'Nasıl yapılır: Veri Akışı Bloğunda Görev Zamanlayıcısı Belirtme'
ms.date: 03/30/2017
ms.prod: .net
ms.technology: dotnet-standard
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TPL dataflow library, linking to task scheduler in TPL
- Task Parallel Library, dataflows
- task scheduler, linking from TPL
ms.assetid: 27ece374-ed5b-49ef-9cec-b20db34a65e8
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 15b1168c34a22394424f250e8ab1887ec8ee1a5e
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-specify-a-task-scheduler-in-a-dataflow-block"></a><span data-ttu-id="d5349-102">Nasıl yapılır: Veri Akışı Bloğunda Görev Zamanlayıcısı Belirtme</span><span class="sxs-lookup"><span data-stu-id="d5349-102">How to: Specify a Task Scheduler in a Dataflow Block</span></span>
<span data-ttu-id="d5349-103">Bu belge, veri akışı uygulamanızda kullandığınızda bir özel Görev Zamanlayıcı'yı ilişkilendirmek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d5349-103">This document demonstrates how to associate a specific task scheduler when you use dataflow in your application.</span></span> <span data-ttu-id="d5349-104">Örnek kullanır <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair?displayProperty=nameWithType> okuyucu görevleri etkin olduğunda ve bir yazıcı görev etkin olduğunda göstermek için bir Windows Forms uygulamasında sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d5349-104">The example uses the <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair?displayProperty=nameWithType> class in a Windows Forms application to show when reader tasks are active and when a writer task is active.</span></span> <span data-ttu-id="d5349-105">Ayrıca kullanır <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> kullanıcı arabirimi iş parçacığı üzerinde çalıştırmak bir veri akışı bloğu etkinleştirmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d5349-105">It also uses the <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> method to enable a dataflow block to run on the user-interface thread.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="to-create-the-windows-forms-application"></a><span data-ttu-id="d5349-106">Form uygulama Windows oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d5349-106">To Create the Windows Forms Application</span></span>  
  
1.  <span data-ttu-id="d5349-107">Bir Visual C# veya Visual Basic oluşturma **Windows Forms uygulaması** projesi.</span><span class="sxs-lookup"><span data-stu-id="d5349-107">Create a Visual C# or Visual Basic **Windows Forms Application** project.</span></span> <span data-ttu-id="d5349-108">Aşağıdaki adımlarda proje adı `WriterReadersWinForms`.</span><span class="sxs-lookup"><span data-stu-id="d5349-108">In the following steps, the project is named `WriterReadersWinForms`.</span></span>  
  
2.  <span data-ttu-id="d5349-109">Ana form için form Tasarımcısı üzerinde Form1.cs (Visual Basic Form1.vb) eklemek dört <xref:System.Windows.Forms.CheckBox> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="d5349-109">On the form designer for the main form, Form1.cs (Form1.vb for Visual Basic), add four <xref:System.Windows.Forms.CheckBox> controls.</span></span> <span data-ttu-id="d5349-110">Ayarlama <xref:System.Windows.Forms.Control.Text%2A> özelliğine **Okuyucu 1** için `checkBox1`, **okuyucu 2** için `checkBox2`, **okuyucu 3** için `checkBox3`, ve  **Yazıcı** için `checkBox4`.</span><span class="sxs-lookup"><span data-stu-id="d5349-110">Set the <xref:System.Windows.Forms.Control.Text%2A> property to **Reader 1** for `checkBox1`, **Reader 2** for `checkBox2`, **Reader 3** for `checkBox3`, and **Writer** for `checkBox4`.</span></span> <span data-ttu-id="d5349-111">Ayarlama <xref:System.Windows.Forms.Control.Enabled%2A> özelliği için her denetim için `False`.</span><span class="sxs-lookup"><span data-stu-id="d5349-111">Set the <xref:System.Windows.Forms.Control.Enabled%2A> property for each control to `False`.</span></span>  
  
3.  <span data-ttu-id="d5349-112">Ekleme bir <xref:System.Windows.Forms.Timer> forma denetim.</span><span class="sxs-lookup"><span data-stu-id="d5349-112">Add a <xref:System.Windows.Forms.Timer> control to the form.</span></span> <span data-ttu-id="d5349-113">Ayarlama <xref:System.Windows.Forms.Timer.Interval%2A> özelliğine `2500`.</span><span class="sxs-lookup"><span data-stu-id="d5349-113">Set the <xref:System.Windows.Forms.Timer.Interval%2A> property to `2500`.</span></span>  
  
## <a name="adding-dataflow-functionality"></a><span data-ttu-id="d5349-114">Veri akışı işlevsellik ekleme</span><span class="sxs-lookup"><span data-stu-id="d5349-114">Adding Dataflow Functionality</span></span>  
 <span data-ttu-id="d5349-115">Bu bölümde uygulamasında katılmak veri akışı blokları oluşturma ve Görev Zamanlayıcısı her biriyle ilişkilendirmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="d5349-115">This section describes how to create the dataflow blocks that participate in the application and how to associate each one with a task scheduler.</span></span>  
  
### <a name="to-add-dataflow-functionality-to-the-application"></a><span data-ttu-id="d5349-116">Uygulama veri akışı işlevsellik eklemek için</span><span class="sxs-lookup"><span data-stu-id="d5349-116">To Add Dataflow Functionality to the Application</span></span>  
  
1.  <span data-ttu-id="d5349-117">Projenizde, System.Threading.Tasks.Dataflow.dll bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d5349-117">In your project, add a reference to System.Threading.Tasks.Dataflow.dll.</span></span>  
  
2.  <span data-ttu-id="d5349-118">Form1.cs (Visual Basic Form1.vb) aşağıdaki içerdiğinden emin olun `using` deyimleri (`Imports` Visual Basic'te).</span><span class="sxs-lookup"><span data-stu-id="d5349-118">Ensure that Form1.cs (Form1.vb for Visual Basic) contains the following `using` statements (`Imports` in Visual Basic).</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#1)]  
  
3.  <span data-ttu-id="d5349-119">Ekleme bir <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> veri üyesini `Form1` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d5349-119">Add a <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> data member to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#2)]  
  
4.  <span data-ttu-id="d5349-120">İçinde `Form1` çağrısından sonra Oluşturucusu `InitializeComponent`, oluşturma bir <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> durumunu değiştirir nesne <xref:System.Windows.Forms.CheckBox> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="d5349-120">In the `Form1` constructor, after the call to `InitializeComponent`, create an <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object that toggles the state of <xref:System.Windows.Forms.CheckBox> objects.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#3)]  
  
5.  <span data-ttu-id="d5349-121">İçinde `Form1` oluşturucusu, oluşturma bir <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> nesne ve dört <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> nesneleri, bir <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> her nesne <xref:System.Windows.Forms.CheckBox> nesne.</span><span class="sxs-lookup"><span data-stu-id="d5349-121">In the `Form1` constructor, create a <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> object and four <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objects, one <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object for each <xref:System.Windows.Forms.CheckBox> object.</span></span> <span data-ttu-id="d5349-122">Her <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> nesne, belirtin bir <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> olan nesneyi <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> özelliğini <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ConcurrentScheduler%2A> okuyucular için özellik ve <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ExclusiveScheduler%2A> yazıcı için özellik.</span><span class="sxs-lookup"><span data-stu-id="d5349-122">For each <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object, specify a <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> object that has the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> property set to the <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ConcurrentScheduler%2A> property for the readers, and the <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ExclusiveScheduler%2A> property for the writer.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#4)]  
  
6.  <span data-ttu-id="d5349-123">İçinde `Form1` oluşturucusu, başlangıç <xref:System.Windows.Forms.Timer> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="d5349-123">In the `Form1` constructor, start the <xref:System.Windows.Forms.Timer> object.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#5)]  
  
7.  <span data-ttu-id="d5349-124">Ana form için form designer'ı oluşturmak için bir olay işleyicisi <xref:System.Windows.Forms.Timer.Tick> süreölçer olayı.</span><span class="sxs-lookup"><span data-stu-id="d5349-124">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.Timer.Tick> event for the timer.</span></span>  
  
8.  <span data-ttu-id="d5349-125">Uygulama <xref:System.Windows.Forms.Timer.Tick> süreölçer olayı.</span><span class="sxs-lookup"><span data-stu-id="d5349-125">Implement the <xref:System.Windows.Forms.Timer.Tick> event for the timer.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#6)]  
  
 <span data-ttu-id="d5349-126">Çünkü `toggleCheckBox` veri akışı bloğu davranır kullanıcı arabiriminde, bu eylem kullanıcı arabirimi iş parçacığı üzerinde gerçekleşmesi önemli.</span><span class="sxs-lookup"><span data-stu-id="d5349-126">Because the `toggleCheckBox` dataflow block acts on the user interface, it is important that this action occur on the user-interface thread.</span></span> <span data-ttu-id="d5349-127">Bu nesne sağlar oluşturma sırasında Bunu başarmak için bir <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> olan nesneyi <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> özelliğini <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d5349-127">To accomplish this, during construction this object provides a <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> object that has the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> property set to <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d5349-128"><xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A> Yöntemi oluşturur bir <xref:System.Threading.Tasks.TaskScheduler> geçerli eşitleme bağlamı üzerinde çalışmayı gerçekleştiren nesne.</span><span class="sxs-lookup"><span data-stu-id="d5349-128">The <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A> method creates a <xref:System.Threading.Tasks.TaskScheduler> object that performs work on the current synchronization context.</span></span> <span data-ttu-id="d5349-129">Çünkü `Form1` Oluşturucusu eylem için kullanıcı arabirimi iş parçacığı çağrılır `toggleCheckBox` veri akışı bloğu kullanıcı arabirimi iş parçacığı üzerinde de çalışır.</span><span class="sxs-lookup"><span data-stu-id="d5349-129">Because the `Form1` constructor is called from the user-interface thread, the action for the `toggleCheckBox` dataflow block also runs on the user-interface thread.</span></span>  
  
 <span data-ttu-id="d5349-130">Bu örnek ayrıca kullanır <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> eşzamanlı olarak davranacak şekilde bazı veri akışı blokları etkinleştirmek için sınıf ve başka bir veri akışı bloğu aynı çalıştıran diğer tüm veri akışı blokları göre özel hareket <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="d5349-130">This example also uses the <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> class to enable some dataflow blocks to act concurrently, and another dataflow block to act exclusive with respect to all other dataflow blocks that run on the same <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> object.</span></span> <span data-ttu-id="d5349-131">Bu kaynağa erişim el ile eşitlemek için gereksinim attığından Bu teknik birden çok veri akışı blokları kaynak paylaşma ve bazı bu kaynağa özel erişim gerektiren kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="d5349-131">This technique is useful when multiple dataflow blocks share a resource and some require exclusive access to that resource, because it eliminates the requirement to manually synchronize access to that resource.</span></span> <span data-ttu-id="d5349-132">El ile eşitleme eleme kodu daha verimli hale getirebilir.</span><span class="sxs-lookup"><span data-stu-id="d5349-132">The elimination of manual synchronization can make code more efficient.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5349-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="d5349-133">Example</span></span>  
 <span data-ttu-id="d5349-134">Aşağıdaki örnek eksiksiz kod Form1.cs (Visual Basic Form1.vb) gösterir.</span><span class="sxs-lookup"><span data-stu-id="d5349-134">The following example shows the complete code for Form1.cs (Form1.vb for Visual Basic).</span></span>  
  
 [!code-csharp[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#100)]  
  
## <a name="see-also"></a><span data-ttu-id="d5349-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d5349-135">See Also</span></span>  
 [<span data-ttu-id="d5349-136">Veri akışı</span><span class="sxs-lookup"><span data-stu-id="d5349-136">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
