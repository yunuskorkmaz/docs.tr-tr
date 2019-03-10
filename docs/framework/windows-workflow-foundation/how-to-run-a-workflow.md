---
title: 'Nasıl yapılır: İş akışı çalıştırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f814ff82-fe2b-4614-aebb-b768c3e61179
ms.openlocfilehash: a5866bae5217b8c8ea22ba66a344b464694583ac
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720987"
---
# <a name="how-to-run-a-workflow"></a><span data-ttu-id="01c7f-102">Nasıl yapılır: İş akışı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="01c7f-102">How to: Run a Workflow</span></span>
<span data-ttu-id="01c7f-103">Bu konu, Windows Workflow Foundation çalışmaya başlama Öğreticisi devamı niteliğindedir ve bir iş akışı ana bilgisayarı oluşturun ve önceki tanımlanan iş akışı çalıştırma anlatılmaktadır [nasıl yapılır: Bir iş akışı oluşturmak](how-to-create-a-workflow.md) konu.</span><span class="sxs-lookup"><span data-stu-id="01c7f-103">This topic is a continuation of the Windows Workflow Foundation Getting Started tutorial and discusses how to create a workflow host and run the workflow defined in the previous [How to: Create a Workflow](how-to-create-a-workflow.md) topic.</span></span>

> [!NOTE]
>  <span data-ttu-id="01c7f-104">Önceki konularıyla ilgili her konuda Başlarken Öğreticisi bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="01c7f-104">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="01c7f-105">Önce tamamlamanız için bu konuyu tamamlamak için [nasıl yapılır: Bir etkinlik oluşturursunuz](how-to-create-an-activity.md) ve [nasıl yapılır: Bir iş akışı oluşturmak](how-to-create-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="01c7f-105">To complete this topic you must first complete [How to: Create an Activity](how-to-create-an-activity.md) and [How to: Create a Workflow](how-to-create-a-workflow.md).</span></span>

> [!NOTE]
>  <span data-ttu-id="01c7f-106">Öğreticinin tamamlanmış bir sürümünü indirmek için bkz [Windows Workflow Foundation (WF45) - başlangıç Öğreticisi](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="01c7f-106">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-workflow-host-project"></a><span data-ttu-id="01c7f-107">İş akışı ana projeyi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="01c7f-107">To create the workflow host project</span></span>  
  
1.  <span data-ttu-id="01c7f-108">Çözüm önceki açın [nasıl yapılır: Bir etkinlik oluşturursunuz](how-to-create-an-activity.md) Visual Studio 2012 kullanarak konu.</span><span class="sxs-lookup"><span data-stu-id="01c7f-108">Open the solution from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic by using Visual Studio 2012.</span></span>  
  
2.  <span data-ttu-id="01c7f-109">Sağ **WF45GettingStartedTutorial** çözümde **Çözüm Gezgini** seçip **Ekle**, **yeni proje**.</span><span class="sxs-lookup"><span data-stu-id="01c7f-109">Right-click the **WF45GettingStartedTutorial** solution in **Solution Explorer** and select **Add**, **New Project**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="01c7f-110">Varsa **Çözüm Gezgini** penceresi görüntülenmiyorsa, seçin **Çözüm Gezgini** gelen **görünümü** menüsü.</span><span class="sxs-lookup"><span data-stu-id="01c7f-110">If the **Solution Explorer** window is not displayed, select **Solution Explorer** from the **View** menu.</span></span>

3.  <span data-ttu-id="01c7f-111">İçinde **yüklü** düğümünü **Visual C#**, **iş akışı** (veya **Visual Basic**, **iş akışı**).</span><span class="sxs-lookup"><span data-stu-id="01c7f-111">In the **Installed** node, select **Visual C#**, **Workflow** (or **Visual Basic**, **Workflow**).</span></span>

    > [!NOTE]
    >  <span data-ttu-id="01c7f-112">Hangi programlama diline bağlı olarak, Visual Studio'da birincil dili olarak yapılandırılmış **Visual C#** veya **Visual Basic** düğümü altında olabilir **diğer diller** düğümünde **yüklü** düğümü.</span><span class="sxs-lookup"><span data-stu-id="01c7f-112">Depending on which programming language is configured as the primary language in Visual Studio, the **Visual C#** or **Visual Basic** node may be under the **Other Languages** node in the **Installed** node.</span></span>

     <span data-ttu-id="01c7f-113">Emin **.NET Framework 4.5** .NET Framework sürüm aşağı açılan listeden seçilen.</span><span class="sxs-lookup"><span data-stu-id="01c7f-113">Ensure that **.NET Framework 4.5** is selected in the .NET Framework version drop-down list.</span></span> <span data-ttu-id="01c7f-114">Seçin **iş akışı konsol uygulaması** gelen **iş akışı** listesi.</span><span class="sxs-lookup"><span data-stu-id="01c7f-114">Select **Workflow Console Application** from the **Workflow** list.</span></span> <span data-ttu-id="01c7f-115">Tür `NumberGuessWorkflowHost` içine **adı** kutusuna ve tıklatın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="01c7f-115">Type `NumberGuessWorkflowHost` into the **Name** box and click **OK**.</span></span> <span data-ttu-id="01c7f-116">Bu destek barındırma temel iş akışı ile bir başlangıç akışı uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="01c7f-116">This creates a starter workflow application with basic workflow hosting support.</span></span> <span data-ttu-id="01c7f-117">Bu temel barındırma kodu değiştirilebilir ve iş akışı uygulamayı çalıştırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="01c7f-117">This basic hosting code is modified and used to run the workflow application.</span></span>

4.  <span data-ttu-id="01c7f-118">Yeni eklenen sağ **NumberGuessWorkflowHost** projesi **Çözüm Gezgini** seçip **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="01c7f-118">Right-click the newly added **NumberGuessWorkflowHost** project in **Solution Explorer** and select **Add Reference**.</span></span> <span data-ttu-id="01c7f-119">Seçin **çözüm** gelen **Başvuru Ekle** listesinde, yanında onay **NumberGuessWorkflowActivities**ve ardından **Tamam** .</span><span class="sxs-lookup"><span data-stu-id="01c7f-119">Select **Solution** from the **Add Reference** list, check the checkbox beside **NumberGuessWorkflowActivities**, and then click **OK**.</span></span>

5.  <span data-ttu-id="01c7f-120">Sağ **Workflow1.xaml** içinde **Çözüm Gezgini** ve **Sil**.</span><span class="sxs-lookup"><span data-stu-id="01c7f-120">Right-click **Workflow1.xaml** in **Solution Explorer** and choose **Delete**.</span></span> <span data-ttu-id="01c7f-121">Tıklayın **Tamam** onaylamak için.</span><span class="sxs-lookup"><span data-stu-id="01c7f-121">Click **OK** to confirm.</span></span>

### <a name="to-modify-the-workflow-hosting-code"></a><span data-ttu-id="01c7f-122">İş akışı barındırma kodunu değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="01c7f-122">To modify the workflow hosting code</span></span>

1.  <span data-ttu-id="01c7f-123">Çift **Program.cs** veya **Module1.vb** içinde **Çözüm Gezgini** seçerek kodu görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="01c7f-123">Double-click **Program.cs** or **Module1.vb** in **Solution Explorer** to display the code.</span></span>

    > [!TIP]
    >  <span data-ttu-id="01c7f-124">Varsa **Çözüm Gezgini** penceresi görüntülenmiyorsa, seçin **Çözüm Gezgini** gelen **görünümü** menüsü.</span><span class="sxs-lookup"><span data-stu-id="01c7f-124">If the **Solution Explorer** window is not displayed, select **Solution Explorer** from the **View** menu.</span></span>

     <span data-ttu-id="01c7f-125">Bu proje kullanılarak oluşturulduğundan **iş akışı konsol uygulaması** şablon **Program.cs** veya **Module1.vb** aşağıdaki temel iş akışı barındırma içerir kodu.</span><span class="sxs-lookup"><span data-stu-id="01c7f-125">Because this project was created by using the **Workflow Console Application** template, **Program.cs** or **Module1.vb** contains the following basic workflow hosting code.</span></span>

    ```vb
    ' Create and cache the workflow definition
    Activity workflow1 = new Workflow1()
    WorkflowInvoker.Invoke(workflow1)
    ```

    ```csharp
    // Create and cache the workflow definition
    Activity workflow1 = new Workflow1();
    WorkflowInvoker.Invoke(workflow1);
    ```

     <span data-ttu-id="01c7f-126">Bu barındırma kodu kullanan oluşturulan <xref:System.Activities.WorkflowInvoker>.</span><span class="sxs-lookup"><span data-stu-id="01c7f-126">This generated hosting code uses <xref:System.Activities.WorkflowInvoker>.</span></span> <span data-ttu-id="01c7f-127"><xref:System.Activities.WorkflowInvoker> bir yöntem çağrısının olan ve kalıcılığı kullanmayan yalnızca iş akışları için kullanılabilir gibi bir iş akışı çalıştırmak için basit bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="01c7f-127"><xref:System.Activities.WorkflowInvoker> provides a simple way for invoking a workflow as if it were a method call and can be used only for workflows that do not use persistence.</span></span> <span data-ttu-id="01c7f-128"><xref:System.Activities.WorkflowApplication> yaşam döngüsü olayları, yürütme denetimi, yer imi sürdürme ve Kalıcılık bildirimi içeren iş akışlarını yürütmek için daha zengin bir model sağlar.</span><span class="sxs-lookup"><span data-stu-id="01c7f-128"><xref:System.Activities.WorkflowApplication> provides a richer model for executing workflows that includes notification of life-cycle events, execution control, bookmark resumption, and persistence.</span></span> <span data-ttu-id="01c7f-129">Bu örnekte yer işaretleri ve <xref:System.Activities.WorkflowApplication> iş akışı barındırma için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="01c7f-129">This example uses bookmarks and <xref:System.Activities.WorkflowApplication> is used for hosting the workflow.</span></span> <span data-ttu-id="01c7f-130">Aşağıdaki `using` veya **içeri aktarmalar** en üstündeki deyimi **Program.cs** veya **Module1.vb** varolan aşağıda **kullanarak** veya **içeri aktarmalar** deyimleri.</span><span class="sxs-lookup"><span data-stu-id="01c7f-130">Add the following `using` or **Imports** statement at the top of **Program.cs** or **Module1.vb** below the existing **using** or **Imports** statements.</span></span>

    ```vb
    Imports NumberGuessWorkflowActivities
    Imports System.Threading
    ```

    ```csharp
    using NumberGuessWorkflowActivities;
    using System.Threading;
    ```

     <span data-ttu-id="01c7f-131">Kullanan kod satırlarını değiştirin <xref:System.Activities.WorkflowInvoker> aşağıdaki temel ile <xref:System.Activities.WorkflowApplication> kod barındırma.</span><span class="sxs-lookup"><span data-stu-id="01c7f-131">Replace the lines of code that use <xref:System.Activities.WorkflowInvoker> with the following basic <xref:System.Activities.WorkflowApplication> hosting code.</span></span> <span data-ttu-id="01c7f-132">Bu örnek kodu barındıran barındırma ve bir iş akışı çağırırken temel adımları gösterir, ancak henüz başarıyla bu konudan iş akışı çalıştırmak için işlevsellik içermiyor.</span><span class="sxs-lookup"><span data-stu-id="01c7f-132">This sample hosting code demonstrates the basic steps for hosting and invoking a workflow, but does not yet contain the functionality to successfully run the workflow from this topic.</span></span> <span data-ttu-id="01c7f-133">Aşağıdaki adımlarda, bu temel kod değiştirilir ve uygulama tamamlanana kadar ek özellikler eklenir.</span><span class="sxs-lookup"><span data-stu-id="01c7f-133">In the following steps, this basic code is modified and additional features are added until the application is complete.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="01c7f-134">Lütfen değiştirin `Workflow1` ile bu örneklerde `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, veya `StateMachineNumberGuessWorkflow`önceki tamamlanan iş akışı bağlı olarak [nasıl yapılır: Bir iş akışı oluşturmak](how-to-create-a-workflow.md) adım.</span><span class="sxs-lookup"><span data-stu-id="01c7f-134">Please replace `Workflow1` in these examples with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow you completed in the previous [How to: Create a Workflow](how-to-create-a-workflow.md) step.</span></span> <span data-ttu-id="01c7f-135">Değil değiştirirseniz `Workflow1` deneyin ve derlediğinizde veya iş akışı çalıştırma derleme hataları alırsınız.</span><span class="sxs-lookup"><span data-stu-id="01c7f-135">If you do not replace `Workflow1` then you will get build errors when you try and build or run the workflow.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#4](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#4)]
     [!code-vb[CFX_WF_GettingStarted#4](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#4)]

     <span data-ttu-id="01c7f-136">Bu kod oluşturur bir <xref:System.Activities.WorkflowApplication>, üç iş akışı yaşam döngüsü olayları kaydeder, iş akışı için bir çağrı ile başlar <xref:System.Activities.WorkflowApplication.Run%2A>ve sonra tamamlamak iş akışı için bekler.</span><span class="sxs-lookup"><span data-stu-id="01c7f-136">This code creates a <xref:System.Activities.WorkflowApplication>, subscribes to three workflow life-cycle events, starts the workflow with a call to <xref:System.Activities.WorkflowApplication.Run%2A>, and then waits for the workflow to complete.</span></span> <span data-ttu-id="01c7f-137">İş akışı tamamlandığında <xref:System.Threading.AutoResetEvent> kümesi ve ana bilgisayar uygulaması tamamlar.</span><span class="sxs-lookup"><span data-stu-id="01c7f-137">When the workflow completes, the <xref:System.Threading.AutoResetEvent> is set and the host application completes.</span></span>

### <a name="to-set-input-arguments-of-a-workflow"></a><span data-ttu-id="01c7f-138">Bir iş akışının giriş bağımsız değişkenleri ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="01c7f-138">To set input arguments of a workflow</span></span>

1.  <span data-ttu-id="01c7f-139">Üstüne aşağıdaki ifadeyi ekleyin **Program.cs** veya **Module1.vb** varolan aşağıda `using` veya `Imports` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="01c7f-139">Add the following statement at the top of **Program.cs** or **Module1.vb** below the existing `using` or `Imports` statements.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#5](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#5)]
     [!code-vb[CFX_WF_GettingStarted#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#5)]

2.  <span data-ttu-id="01c7f-140">Yeni oluşturan kod satırına değiştirin <xref:System.Activities.WorkflowApplication> aşağıdaki kodla oluşturur ve oluşturulduğu sırada iş akışına parametreleri sözlüğü geçirir.</span><span class="sxs-lookup"><span data-stu-id="01c7f-140">Replace the line of code that creates the new <xref:System.Activities.WorkflowApplication> with the following code that creates and passes a dictionary of parameters to the workflow when it is created.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="01c7f-141">Lütfen değiştirin `Workflow1` ile bu örneklerde `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, veya `StateMachineNumberGuessWorkflow`önceki tamamlanan iş akışı bağlı olarak [nasıl yapılır: Bir iş akışı oluşturmak](how-to-create-a-workflow.md) adım.</span><span class="sxs-lookup"><span data-stu-id="01c7f-141">Please replace `Workflow1` in these examples with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow you completed in the previous [How to: Create a Workflow](how-to-create-a-workflow.md) step.</span></span> <span data-ttu-id="01c7f-142">Değil değiştirirseniz `Workflow1` deneyin ve derlediğinizde veya iş akışı çalıştırma derleme hataları alırsınız.</span><span class="sxs-lookup"><span data-stu-id="01c7f-142">If you do not replace `Workflow1` then you will get build errors when you try and build or run the workflow.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#6](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]

     <span data-ttu-id="01c7f-143">Bu sözlüğün bir anahtar ile bir öğe içeren `MaxNumber`.</span><span class="sxs-lookup"><span data-stu-id="01c7f-143">This dictionary contains one element with a key of `MaxNumber`.</span></span> <span data-ttu-id="01c7f-144">İş akışının Kök etkinlik bağımsız değişkenler girişi için giriş sözlüğündeki anahtarları karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="01c7f-144">Keys in the input dictionary correspond to input arguments on the root activity of the workflow.</span></span> <span data-ttu-id="01c7f-145">`MaxNumber` İş akışı tarafından rastgele oluşturulan sayı için üst sınır belirlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="01c7f-145">`MaxNumber` is used by the workflow to determine the upper bound for the randomly generated number.</span></span>

### <a name="to-retrieve-output-arguments-of-a-workflow"></a><span data-ttu-id="01c7f-146">Bir iş akışının çıkış değişkenlerini almak için</span><span class="sxs-lookup"><span data-stu-id="01c7f-146">To retrieve output arguments of a workflow</span></span>

1.  <span data-ttu-id="01c7f-147">Değiştirme <xref:System.Activities.WorkflowApplication.Completed%2A> almak ve iş akışı tarafından kullanılan kapatır sayısını görüntülemek için işleyici.</span><span class="sxs-lookup"><span data-stu-id="01c7f-147">Modify the <xref:System.Activities.WorkflowApplication.Completed%2A> handler to retrieve and display the number of turns used by the workflow.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#7](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#7)]
     [!code-vb[CFX_WF_GettingStarted#7](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#7)]

### <a name="to-resume-a-bookmark"></a><span data-ttu-id="01c7f-148">Bir yer işareti sürdürmek için</span><span class="sxs-lookup"><span data-stu-id="01c7f-148">To resume a bookmark</span></span>

1.  <span data-ttu-id="01c7f-149">Üstüne aşağıdaki kodu ekleyin `Main` varolan sonra yöntemi <xref:System.Threading.AutoResetEvent> bildirimi.</span><span class="sxs-lookup"><span data-stu-id="01c7f-149">Add the following code at the top of the `Main` method just after the existing <xref:System.Threading.AutoResetEvent> declaration.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#8](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#8)]
     [!code-vb[CFX_WF_GettingStarted#8](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#8)]

2.  <span data-ttu-id="01c7f-150">Aşağıdaki <xref:System.Activities.WorkflowApplication.Idle%2A> işleyici hemen altındaki mevcut üç iş akışı yaşam döngüsü işleyiciler `Main`.</span><span class="sxs-lookup"><span data-stu-id="01c7f-150">Add the following <xref:System.Activities.WorkflowApplication.Idle%2A> handler just below the existing three workflow life-cycle handlers in `Main`.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#9](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#9)]
     [!code-vb[CFX_WF_GettingStarted#9](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#9)]

     <span data-ttu-id="01c7f-151">Bu işleyici iş akışı için bir sonraki tahmin, bekleyen boşta olur her zaman çağrılır ve `idleAction` <xref:System.Threading.AutoResetEvent> ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="01c7f-151">Each time the workflow becomes idle waiting for the next guess, this handler is called and the `idleAction` <xref:System.Threading.AutoResetEvent> is set.</span></span> <span data-ttu-id="01c7f-152">Sonraki adımda kod `idleEvent` ve `syncEvent` iş akışı için sonraki tahmin bekliyor veya tamamlandığında belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="01c7f-152">The code in the following step uses `idleEvent` and `syncEvent` to determine whether the workflow is waiting for the next guess or is complete.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="01c7f-153">Bu örnekte, ana bilgisayar uygulaması otomatik sıfırlama olayları kullanan <xref:System.Activities.WorkflowApplication.Completed%2A> ve <xref:System.Activities.WorkflowApplication.Idle%2A> ana uygulama iş akışı ilerlemesini ile eşitlemek için işleyiciler.</span><span class="sxs-lookup"><span data-stu-id="01c7f-153">In this example, the host application uses auto-reset events in the <xref:System.Activities.WorkflowApplication.Completed%2A> and <xref:System.Activities.WorkflowApplication.Idle%2A> handlers to synchronize the host application with the progress of the workflow.</span></span> <span data-ttu-id="01c7f-154">Blok ve iş akışının bir yer işareti devam etmeden önce boşta beklemesi gerekli değildir, ancak bu örnekte ana iş akışının tamamını olup veya kullanarakdahafazlakullanıcıgirdisiolupbekliyorolduğunubilmesiiçineşitlemeolaylarıgereklidir<xref:System.Activities.Bookmark>.</span><span class="sxs-lookup"><span data-stu-id="01c7f-154">It is not necessary to block and wait for the workflow to become idle before resuming a bookmark, but in this example the synchronization events are required so the host knows whether the workflow is complete or whether it is waiting on more user input by using the <xref:System.Activities.Bookmark>.</span></span> <span data-ttu-id="01c7f-155">Daha fazla bilgi için [yer işaretleri](bookmarks.md).</span><span class="sxs-lookup"><span data-stu-id="01c7f-155">For more information, see [Bookmarks](bookmarks.md).</span></span>

3.  <span data-ttu-id="01c7f-156">Çağrısını kaldırın `WaitOne`, sürdürme ve kullanıcı girişleri toplamak için kodu değiştirin <xref:System.Activities.Bookmark>.</span><span class="sxs-lookup"><span data-stu-id="01c7f-156">Remove the call to `WaitOne`, and replace it with code to gather input from the user and resume the <xref:System.Activities.Bookmark>.</span></span>

     <span data-ttu-id="01c7f-157">Aşağıdaki kod satırını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="01c7f-157">Remove the following line of code.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#10](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#10)]
     [!code-vb[CFX_WF_GettingStarted#10](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#10)]

     <span data-ttu-id="01c7f-158">Aşağıdaki örnek ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="01c7f-158">Replace it with the following example.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#11](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#11)]
     [!code-vb[CFX_WF_GettingStarted#11](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#11)]

## <a name="BKMK_ToRunTheApplication"></a> <span data-ttu-id="01c7f-159">Derleme ve uygulamayı çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="01c7f-159">To build and run the application</span></span>

1.  <span data-ttu-id="01c7f-160">Sağ **NumberGuessWorkflowHost** içinde **Çözüm Gezgini** seçip **başlangıç projesi olarak ayarla**.</span><span class="sxs-lookup"><span data-stu-id="01c7f-160">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and select **Set as StartUp Project**.</span></span>

2.  <span data-ttu-id="01c7f-161">Derleme ve uygulamayı çalıştırmak için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="01c7f-161">Press CTRL+F5 to build and run the application.</span></span> <span data-ttu-id="01c7f-162">Mümkün olduğunca az kapatır, sayısını tahmin etmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="01c7f-162">Try to guess the number in as few turns as possible.</span></span>

     <span data-ttu-id="01c7f-163">İş akışının diğer stilleri biri ile bir uygulamayı denemek için değiştirin `Workflow1` oluşturan kodu içinde <xref:System.Activities.WorkflowApplication> ile `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, veya `StateMachineNumberGuessWorkflow`istediğiniz hangi iş akışı stili bağlı olarak.</span><span class="sxs-lookup"><span data-stu-id="01c7f-163">To try the application with one of the other styles of workflow, replace `Workflow1` in the code that creates the <xref:System.Activities.WorkflowApplication> with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow style you desire.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#6](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]

     <span data-ttu-id="01c7f-164">Kalıcılık bir iş akışı uygulamaya ekleme hakkında yönergeler görmek için bir sonraki konu [nasıl yapılır: Oluşturma ve uzun süre çalışan iş akışı](how-to-create-and-run-a-long-running-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="01c7f-164">For instructions about how to add persistence to a workflow application, see the next topic, [How to: Create and Run a Long Running Workflow](how-to-create-and-run-a-long-running-workflow.md).</span></span>

## <a name="example"></a><span data-ttu-id="01c7f-165">Örnek</span><span class="sxs-lookup"><span data-stu-id="01c7f-165">Example</span></span>
 <span data-ttu-id="01c7f-166">Aşağıdaki örnek için tam kodu, `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="01c7f-166">The following example is the complete code listing for the `Main` method.</span></span>

> [!NOTE]
>  <span data-ttu-id="01c7f-167">Lütfen değiştirin `Workflow1` ile bu örneklerde `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, veya `StateMachineNumberGuessWorkflow`önceki tamamlanan iş akışı bağlı olarak [nasıl yapılır: Bir iş akışı oluşturmak](how-to-create-a-workflow.md) adım.</span><span class="sxs-lookup"><span data-stu-id="01c7f-167">Please replace `Workflow1` in these examples with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow you completed in the previous [How to: Create a Workflow](how-to-create-a-workflow.md) step.</span></span> <span data-ttu-id="01c7f-168">Değil değiştirirseniz `Workflow1` deneyin ve derlediğinizde veya iş akışı çalıştırma derleme hataları alırsınız.</span><span class="sxs-lookup"><span data-stu-id="01c7f-168">If you do not replace `Workflow1` then you will get build errors when you try and build or run the workflow.</span></span>

 [!code-csharp[CFX_WF_GettingStarted#12](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#12)]
 [!code-vb[CFX_WF_GettingStarted#12](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#12)]

## <a name="see-also"></a><span data-ttu-id="01c7f-169">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="01c7f-169">See also</span></span>

- <xref:System.Activities.WorkflowApplication>
- <xref:System.Activities.Bookmark>
- [<span data-ttu-id="01c7f-170">Windows Workflow Foundation Programlama</span><span class="sxs-lookup"><span data-stu-id="01c7f-170">Windows Workflow Foundation Programming</span></span>](programming.md)
- [<span data-ttu-id="01c7f-171">Başlangıç Öğreticisi</span><span class="sxs-lookup"><span data-stu-id="01c7f-171">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="01c7f-172">Nasıl yapılır: Bir iş akışı oluşturma</span><span class="sxs-lookup"><span data-stu-id="01c7f-172">How to: Create a Workflow</span></span>](how-to-create-a-workflow.md)
- [<span data-ttu-id="01c7f-173">Nasıl yapılır: Oluşturma ve uzun süre çalışan iş akışı</span><span class="sxs-lookup"><span data-stu-id="01c7f-173">How to: Create and Run a Long Running Workflow</span></span>](how-to-create-and-run-a-long-running-workflow.md)
- [<span data-ttu-id="01c7f-174">Bir iş akışında giriş bekleme</span><span class="sxs-lookup"><span data-stu-id="01c7f-174">Waiting for Input in a Workflow</span></span>](waiting-for-input-in-a-workflow.md)
- [<span data-ttu-id="01c7f-175">İş Akışları Barındırma</span><span class="sxs-lookup"><span data-stu-id="01c7f-175">Hosting Workflows</span></span>](hosting-workflows.md)