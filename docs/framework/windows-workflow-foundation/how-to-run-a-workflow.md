---
title: 'Nasıl yapılır: bir iş akışını çalıştırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f814ff82-fe2b-4614-aebb-b768c3e61179
ms.openlocfilehash: 704527bde2ac6bf555d40db836baf938c0c5cd96
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33519525"
---
# <a name="how-to-run-a-workflow"></a><span data-ttu-id="8838a-102">Nasıl yapılır: bir iş akışını çalıştırma</span><span class="sxs-lookup"><span data-stu-id="8838a-102">How to: Run a Workflow</span></span>
<span data-ttu-id="8838a-103">Bu konu, Windows Workflow Foundation Başlarken Öğreticisi devamıdır ve bir iş akışı ana bilgisayarı oluşturmak ve önceki tanımlanan iş akışını çalıştırmak nasıl ele [nasıl yapılır: bir iş akışı oluşturmak](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) konu.</span><span class="sxs-lookup"><span data-stu-id="8838a-103">This topic is a continuation of the Windows Workflow Foundation Getting Started tutorial and discusses how to create a workflow host and run the workflow defined in the previous [How to: Create a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8838a-104">Başlarken Öğreticisi her bir konuda önceki konularda bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="8838a-104">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="8838a-105">Bu konunun ilk tamamlanmalıdır tamamlamak için [nasıl yapılır: bir etkinlik oluşturmak](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) ve [nasıl yapılır: bir iş akışı oluşturmak](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="8838a-105">To complete this topic you must first complete [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) and [How to: Create a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8838a-106">Öğreticinin tamamlanmış bir sürümünü indirmek için bkz: [Windows Workflow Foundation (WF45) - başlangıç Öğreticisi](http://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="8838a-106">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](http://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-workflow-host-project"></a><span data-ttu-id="8838a-107">İş akışı konak projesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="8838a-107">To create the workflow host project</span></span>  
  
1.  <span data-ttu-id="8838a-108">Çözüm önceki açın [nasıl yapılır: bir etkinlik oluşturmak](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) kullanarak konu [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8838a-108">Open the solution from the previous [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) topic by using [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="8838a-109">Sağ **WF45GettingStartedTutorial** çözümde **Çözüm Gezgini** seçip **Ekle**, **yeni proje**.</span><span class="sxs-lookup"><span data-stu-id="8838a-109">Right-click the **WF45GettingStartedTutorial** solution in **Solution Explorer** and select **Add**, **New Project**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="8838a-110">Varsa **Çözüm Gezgini** penceresi görüntülenmez, seçin **Çözüm Gezgini** gelen **Görünüm** menüsü.</span><span class="sxs-lookup"><span data-stu-id="8838a-110">If the **Solution Explorer** window is not displayed, select **Solution Explorer** from the **View** menu.</span></span>  
  
3.  <span data-ttu-id="8838a-111">İçinde **yüklü** düğümü, select **Visual C#**, **iş akışı** (veya **Visual Basic**, **iş akışı**).</span><span class="sxs-lookup"><span data-stu-id="8838a-111">In the **Installed** node, select **Visual C#**, **Workflow** (or **Visual Basic**, **Workflow**).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8838a-112">Visual Studio'da birincil dili olarak programlama dili bağlı olarak yapılandırılmış **Visual C#** veya **Visual Basic** düğümü altında olabilir **diğer diller** düğümünde **yüklü** düğümü.</span><span class="sxs-lookup"><span data-stu-id="8838a-112">Depending on which programming language is configured as the primary language in Visual Studio, the **Visual C#** or **Visual Basic** node may be under the **Other Languages** node in the **Installed** node.</span></span>  
  
     <span data-ttu-id="8838a-113">Emin **.NET Framework 4.5** .NET Framework sürüm aşağı açılan listesinde seçilir.</span><span class="sxs-lookup"><span data-stu-id="8838a-113">Ensure that **.NET Framework 4.5** is selected in the .NET Framework version drop-down list.</span></span> <span data-ttu-id="8838a-114">Seçin **iş akışı konsol uygulaması** gelen **iş akışı** listesi.</span><span class="sxs-lookup"><span data-stu-id="8838a-114">Select **Workflow Console Application** from the **Workflow** list.</span></span> <span data-ttu-id="8838a-115">Tür `NumberGuessWorkflowHost` içine **adı** kutusuna ve tıklatın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="8838a-115">Type `NumberGuessWorkflowHost` into the **Name** box and click **OK**.</span></span> <span data-ttu-id="8838a-116">Bu destek barındırma temel iş akışı ile başlangıç iş akışı uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8838a-116">This creates a starter workflow application with basic workflow hosting support.</span></span> <span data-ttu-id="8838a-117">Bu temel barındırma kodu değiştirilebilir ve iş akışı uygulamayı çalıştırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8838a-117">This basic hosting code is modified and used to run the workflow application.</span></span>  
  
4.  <span data-ttu-id="8838a-118">Yeni eklenen sağ **NumberGuessWorkflowHost** proje **Çözüm Gezgini** seçip **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="8838a-118">Right-click the newly added **NumberGuessWorkflowHost** project in **Solution Explorer** and select **Add Reference**.</span></span> <span data-ttu-id="8838a-119">Seçin **çözüm** gelen **Başvuru Ekle** listesinde, yanındaki onay kutusunu işaretleyin **NumberGuessWorkflowActivities**ve ardından **Tamam** .</span><span class="sxs-lookup"><span data-stu-id="8838a-119">Select **Solution** from the **Add Reference** list, check the checkbox beside **NumberGuessWorkflowActivities**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="8838a-120">Sağ **Workflow1.xaml** içinde **Çözüm Gezgini** ve **silmek**.</span><span class="sxs-lookup"><span data-stu-id="8838a-120">Right-click **Workflow1.xaml** in **Solution Explorer** and choose **Delete**.</span></span> <span data-ttu-id="8838a-121">Tıklatın **Tamam** onaylamak için.</span><span class="sxs-lookup"><span data-stu-id="8838a-121">Click **OK** to confirm.</span></span>  
  
### <a name="to-modify-the-workflow-hosting-code"></a><span data-ttu-id="8838a-122">Kod barındırma iş akışını değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="8838a-122">To modify the workflow hosting code</span></span>  
  
1.  <span data-ttu-id="8838a-123">Çift **Program.cs** veya **Module1.vb** içinde **Çözüm Gezgini** kodunu görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="8838a-123">Double-click **Program.cs** or **Module1.vb** in **Solution Explorer** to display the code.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="8838a-124">Varsa **Çözüm Gezgini** penceresi görüntülenmez, seçin **Çözüm Gezgini** gelen **Görünüm** menüsü.</span><span class="sxs-lookup"><span data-stu-id="8838a-124">If the **Solution Explorer** window is not displayed, select **Solution Explorer** from the **View** menu.</span></span>  
  
     <span data-ttu-id="8838a-125">Bu proje kullanarak oluşturulduğundan **iş akışı konsol uygulaması** şablon **Program.cs** veya **Module1.vb** aşağıdaki temel iş akışı barındırma içerir kod.</span><span class="sxs-lookup"><span data-stu-id="8838a-125">Because this project was created by using the **Workflow Console Application** template, **Program.cs** or **Module1.vb** contains the following basic workflow hosting code.</span></span>  
  
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
  
     <span data-ttu-id="8838a-126">Bu barındırma kodu kullandığı oluşturulan <xref:System.Activities.WorkflowInvoker>.</span><span class="sxs-lookup"><span data-stu-id="8838a-126">This generated hosting code uses <xref:System.Activities.WorkflowInvoker>.</span></span> <span data-ttu-id="8838a-127"><xref:System.Activities.WorkflowInvoker> yöntem çağrısı sırasında ve Kalıcılık kullanmayan yalnızca iş akışları için kullanılabilir gibi bir iş akışı çağırma için basit bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="8838a-127"><xref:System.Activities.WorkflowInvoker> provides a simple way for invoking a workflow as if it were a method call and can be used only for workflows that do not use persistence.</span></span> <span data-ttu-id="8838a-128"><xref:System.Activities.WorkflowApplication> yaşam döngüsü olayları, yürütme denetimi, yer işareti sürdürme ve kalıcılığı bildirimi içeren iş akışlarını yürütmek için daha zengin bir modeli sağlar.</span><span class="sxs-lookup"><span data-stu-id="8838a-128"><xref:System.Activities.WorkflowApplication> provides a richer model for executing workflows that includes notification of life-cycle events, execution control, bookmark resumption, and persistence.</span></span> <span data-ttu-id="8838a-129">Bu örnekte yer işaretleri kullanır ve <xref:System.Activities.WorkflowApplication> iş akışı barındırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8838a-129">This example uses bookmarks and <xref:System.Activities.WorkflowApplication> is used for hosting the workflow.</span></span> <span data-ttu-id="8838a-130">Aşağıdakileri ekleyin `using` veya **içeri aktarmalar** deyimi en üstündeki **Program.cs** veya **Module1.vb** varolan aşağıda **kullanarak** veya **içeri aktarmalar** deyimleri.</span><span class="sxs-lookup"><span data-stu-id="8838a-130">Add the following `using` or **Imports** statement at the top of **Program.cs** or **Module1.vb** below the existing **using** or **Imports** statements.</span></span>  
  
    ```vb  
    Imports NumberGuessWorkflowActivities  
    Imports System.Threading  
    ```  
  
    ```csharp  
    using NumberGuessWorkflowActivities;  
    using System.Threading;  
    ```  
  
     <span data-ttu-id="8838a-131">Kullanın kod satırlarını Değiştir <xref:System.Activities.WorkflowInvoker> aşağıdaki basic ile <xref:System.Activities.WorkflowApplication> kod barındırma.</span><span class="sxs-lookup"><span data-stu-id="8838a-131">Replace the lines of code that use <xref:System.Activities.WorkflowInvoker> with the following basic <xref:System.Activities.WorkflowApplication> hosting code.</span></span> <span data-ttu-id="8838a-132">Bu örnek kodu barındırma barındırma ve bir iş akışı çağırma için temel adımlar gösterilmektedir, ancak henüz başarılı bir şekilde bu konudan iş akışını çalıştırmak için işlevsellik içermiyor.</span><span class="sxs-lookup"><span data-stu-id="8838a-132">This sample hosting code demonstrates the basic steps for hosting and invoking a workflow, but does not yet contain the functionality to successfully run the workflow from this topic.</span></span> <span data-ttu-id="8838a-133">Aşağıdaki adımlarda bu temel kod değiştirilebilir ve uygulama işlemi tamamlanana kadar ek özellikler eklenir.</span><span class="sxs-lookup"><span data-stu-id="8838a-133">In the following steps, this basic code is modified and additional features are added until the application is complete.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8838a-134">Lütfen değiştirin `Workflow1` ile bu örneklerde `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, veya `StateMachineNumberGuessWorkflow`önceki tamamlanan iş akışı bağlı olarak [nasıl yapılır: bir iş akışı oluşturmak](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) adım.</span><span class="sxs-lookup"><span data-stu-id="8838a-134">Please replace `Workflow1` in these examples with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow you completed in the previous [How to: Create a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) step.</span></span> <span data-ttu-id="8838a-135">Yerini varsa `Workflow1` deneyin ve yapı veya iş akışını çalıştırdığınızda derleme hataları alırsınız.</span><span class="sxs-lookup"><span data-stu-id="8838a-135">If you do not replace `Workflow1` then you will get build errors when you try and build or run the workflow.</span></span>  
  
     [!code-csharp[CFX_WF_GettingStarted#4](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#4)]
     [!code-vb[CFX_WF_GettingStarted#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#4)]  
  
     <span data-ttu-id="8838a-136">Bu kod oluşturur bir <xref:System.Activities.WorkflowApplication>, üç iş akışı yaşam döngüsü olayları kaydeder, iş akışı için bir çağrı ile başlayan <xref:System.Activities.WorkflowApplication.Run%2A>ve sonra tamamlamak iş akışı için bekler.</span><span class="sxs-lookup"><span data-stu-id="8838a-136">This code creates a <xref:System.Activities.WorkflowApplication>, subscribes to three workflow life-cycle events, starts the workflow with a call to <xref:System.Activities.WorkflowApplication.Run%2A>, and then waits for the workflow to complete.</span></span> <span data-ttu-id="8838a-137">İş akışı tamamlandığında <xref:System.Threading.AutoResetEvent> ayarlanır ve ana bilgisayar uygulaması tamamlar.</span><span class="sxs-lookup"><span data-stu-id="8838a-137">When the workflow completes, the <xref:System.Threading.AutoResetEvent> is set and the host application completes.</span></span>  
  
### <a name="to-set-input-arguments-of-a-workflow"></a><span data-ttu-id="8838a-138">Giriş bağımsız değişkenleri bir iş akışının ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="8838a-138">To set input arguments of a workflow</span></span>  
  
1.  <span data-ttu-id="8838a-139">En üstünde aşağıdaki deyimine **Program.cs** veya **Module1.vb** varolan aşağıda `using` veya `Imports` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="8838a-139">Add the following statement at the top of **Program.cs** or **Module1.vb** below the existing `using` or `Imports` statements.</span></span>  
  
     [!code-csharp[CFX_WF_GettingStarted#5](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#5)]
     [!code-vb[CFX_WF_GettingStarted#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#5)]  
  
2.  <span data-ttu-id="8838a-140">Yeni oluşturulan kod satırı değiştirin <xref:System.Activities.WorkflowApplication> aşağıdaki kodla oluşturur ve oluşturulduğunda iş akışına parametreleri sözlüğü geçirir.</span><span class="sxs-lookup"><span data-stu-id="8838a-140">Replace the line of code that creates the new <xref:System.Activities.WorkflowApplication> with the following code that creates and passes a dictionary of parameters to the workflow when it is created.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8838a-141">Lütfen değiştirin `Workflow1` ile bu örneklerde `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, veya `StateMachineNumberGuessWorkflow`önceki tamamlanan iş akışı bağlı olarak [nasıl yapılır: bir iş akışı oluşturmak](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) adım.</span><span class="sxs-lookup"><span data-stu-id="8838a-141">Please replace `Workflow1` in these examples with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow you completed in the previous [How to: Create a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) step.</span></span> <span data-ttu-id="8838a-142">Yerini varsa `Workflow1` deneyin ve yapı veya iş akışını çalıştırdığınızda derleme hataları alırsınız.</span><span class="sxs-lookup"><span data-stu-id="8838a-142">If you do not replace `Workflow1` then you will get build errors when you try and build or run the workflow.</span></span>  
  
     [!code-csharp[CFX_WF_GettingStarted#6](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]  
  
     <span data-ttu-id="8838a-143">Tek bir öğe anahtarı ile bu sözlük içeren `MaxNumber`.</span><span class="sxs-lookup"><span data-stu-id="8838a-143">This dictionary contains one element with a key of `MaxNumber`.</span></span> <span data-ttu-id="8838a-144">Giriş sözlüğündeki anahtarları bağımsız değişkenler iş akışı Kök etkinlik üzerinde giriş karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="8838a-144">Keys in the input dictionary correspond to input arguments on the root activity of the workflow.</span></span> <span data-ttu-id="8838a-145">`MaxNumber` İş akışı tarafından rastgele oluşturulmuş sayısı için üst sınır belirlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8838a-145">`MaxNumber` is used by the workflow to determine the upper bound for the randomly generated number.</span></span>  
  
### <a name="to-retrieve-output-arguments-of-a-workflow"></a><span data-ttu-id="8838a-146">Bir iş akışının çıkış değişkenlerini almak için</span><span class="sxs-lookup"><span data-stu-id="8838a-146">To retrieve output arguments of a workflow</span></span>  
  
1.  <span data-ttu-id="8838a-147">Değiştirme <xref:System.Activities.WorkflowApplication.Completed%2A> almak ve iş akışı tarafından kullanılan kapatır sayısını görüntülemek için işleyici.</span><span class="sxs-lookup"><span data-stu-id="8838a-147">Modify the <xref:System.Activities.WorkflowApplication.Completed%2A> handler to retrieve and display the number of turns used by the workflow.</span></span>  
  
     [!code-csharp[CFX_WF_GettingStarted#7](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#7)]
     [!code-vb[CFX_WF_GettingStarted#7](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#7)]  
  
### <a name="to-resume-a-bookmark"></a><span data-ttu-id="8838a-148">Yer işareti sürdürmek için</span><span class="sxs-lookup"><span data-stu-id="8838a-148">To resume a bookmark</span></span>  
  
1.  <span data-ttu-id="8838a-149">En üstte aşağıdaki kodu ekleyin `Main` varolan sonra yöntemi <xref:System.Threading.AutoResetEvent> bildirimi.</span><span class="sxs-lookup"><span data-stu-id="8838a-149">Add the following code at the top of the `Main` method just after the existing <xref:System.Threading.AutoResetEvent> declaration.</span></span>  
  
     [!code-csharp[CFX_WF_GettingStarted#8](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#8)]
     [!code-vb[CFX_WF_GettingStarted#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#8)]  
  
2.  <span data-ttu-id="8838a-150">Aşağıdakileri ekleyin <xref:System.Activities.WorkflowApplication.Idle%2A> varolan üç iş akışı yaşam döngüsü işleyiciler hemen altındaki işleyici `Main`.</span><span class="sxs-lookup"><span data-stu-id="8838a-150">Add the following <xref:System.Activities.WorkflowApplication.Idle%2A> handler just below the existing three workflow life-cycle handlers in `Main`.</span></span>  
  
     [!code-csharp[CFX_WF_GettingStarted#9](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#9)]
     [!code-vb[CFX_WF_GettingStarted#9](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#9)]  
  
     <span data-ttu-id="8838a-151">İş akışı için sonraki tahmin, bekleyen boşta her zaman bu işleyici olarak adlandırılır ve `idleAction` <xref:System.Threading.AutoResetEvent> ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="8838a-151">Each time the workflow becomes idle waiting for the next guess, this handler is called and the `idleAction` <xref:System.Threading.AutoResetEvent> is set.</span></span> <span data-ttu-id="8838a-152">Sonraki adımda kodu kullanan `idleEvent` ve `syncEvent` iş akışı için sonraki tahmin bekliyor veya tamamlandıktan belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="8838a-152">The code in the following step uses `idleEvent` and `syncEvent` to determine whether the workflow is waiting for the next guess or is complete.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8838a-153">Bu örnekte, ana bilgisayar uygulamasını otomatik sıfırlama olayları kullanan <xref:System.Activities.WorkflowApplication.Completed%2A> ve <xref:System.Activities.WorkflowApplication.Idle%2A> konak uygulama iş akışı ilerleme ile eşitlemek için işleyiciler.</span><span class="sxs-lookup"><span data-stu-id="8838a-153">In this example, the host application uses auto-reset events in the <xref:System.Activities.WorkflowApplication.Completed%2A> and <xref:System.Activities.WorkflowApplication.Idle%2A> handlers to synchronize the host application with the progress of the workflow.</span></span> <span data-ttu-id="8838a-154">Engelleme ve boşta durumuna yer işareti devam etmeden önce iş akışı için beklemek gerekli değildir, ancak bu örnekte, iş akışını tam olup veya kullanarakdahafazlakullanıcıgirdisiolupbekliyorkonakbilmesiiçineşitlemeolaylarıgereklidir<xref:System.Activities.Bookmark>.</span><span class="sxs-lookup"><span data-stu-id="8838a-154">It is not necessary to block and wait for the workflow to become idle before resuming a bookmark, but in this example the synchronization events are required so the host knows whether the workflow is complete or whether it is waiting on more user input by using the <xref:System.Activities.Bookmark>.</span></span> <span data-ttu-id="8838a-155">Daha fazla bilgi için bkz: [yer işaretleri](../../../docs/framework/windows-workflow-foundation/bookmarks.md).</span><span class="sxs-lookup"><span data-stu-id="8838a-155">For more information, see [Bookmarks](../../../docs/framework/windows-workflow-foundation/bookmarks.md).</span></span>  
  
3.  <span data-ttu-id="8838a-156">Çağrı kaldırmak `WaitOne`ve kullanıcı ve sürdürme giriş toplamak için kod ile değiştirin <xref:System.Activities.Bookmark>.</span><span class="sxs-lookup"><span data-stu-id="8838a-156">Remove the call to `WaitOne`, and replace it with code to gather input from the user and resume the <xref:System.Activities.Bookmark>.</span></span>  
  
     <span data-ttu-id="8838a-157">Aşağıdaki kod satırını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="8838a-157">Remove the following line of code.</span></span>  
  
     [!code-csharp[CFX_WF_GettingStarted#10](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#10)]
     [!code-vb[CFX_WF_GettingStarted#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#10)]  
  
     <span data-ttu-id="8838a-158">Aşağıdaki örnek ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="8838a-158">Replace it with the following example.</span></span>  
  
     [!code-csharp[CFX_WF_GettingStarted#11](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#11)]
     [!code-vb[CFX_WF_GettingStarted#11](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#11)]  
  
##  <a name="BKMK_ToRunTheApplication"></a> <span data-ttu-id="8838a-159">Derleme ve uygulamayı çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="8838a-159">To build and run the application</span></span>  
  
1.  <span data-ttu-id="8838a-160">Sağ **NumberGuessWorkflowHost** içinde **Çözüm Gezgini** seçip **başlangıç projesi olarak ayarla**.</span><span class="sxs-lookup"><span data-stu-id="8838a-160">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and select **Set as StartUp Project**.</span></span>  
  
2.  <span data-ttu-id="8838a-161">Derleme ve uygulamayı çalıştırmak için CTRL + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="8838a-161">Press CTRL+F5 to build and run the application.</span></span> <span data-ttu-id="8838a-162">Mümkün olduğunca az tasarrufludur sayısını tahmin etmeye çalışın.</span><span class="sxs-lookup"><span data-stu-id="8838a-162">Try to guess the number in as few turns as possible.</span></span>  
  
     <span data-ttu-id="8838a-163">Diğer stilleri biri ile uygulama iş akışının denemek için değiştirme `Workflow1` oluşturan kodu <xref:System.Activities.WorkflowApplication> ile `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, veya `StateMachineNumberGuessWorkflow`istediğiniz hangi iş akışı stili bağlı olarak.</span><span class="sxs-lookup"><span data-stu-id="8838a-163">To try the application with one of the other styles of workflow, replace `Workflow1` in the code that creates the <xref:System.Activities.WorkflowApplication> with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow style you desire.</span></span>  
  
     [!code-csharp[CFX_WF_GettingStarted#6](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]  
  
     <span data-ttu-id="8838a-164">Kalıcılığı bir iş akışı uygulamasına ekleme hakkında yönergeler görmek için sonraki konu [nasıl yapılır: oluşturun ve uzun çalışan iş akışını çalıştırma](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="8838a-164">For instructions about how to add persistence to a workflow application, see the next topic, [How to: Create and Run a Long Running Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8838a-165">Örnek</span><span class="sxs-lookup"><span data-stu-id="8838a-165">Example</span></span>  
 <span data-ttu-id="8838a-166">Aşağıdaki örnek, için listeleme eksiksiz koddur `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8838a-166">The following example is the complete code listing for the `Main` method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8838a-167">Lütfen değiştirin `Workflow1` ile bu örneklerde `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, veya `StateMachineNumberGuessWorkflow`önceki tamamlanan iş akışı bağlı olarak [nasıl yapılır: bir iş akışı oluşturmak](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) adım.</span><span class="sxs-lookup"><span data-stu-id="8838a-167">Please replace `Workflow1` in these examples with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow you completed in the previous [How to: Create a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) step.</span></span> <span data-ttu-id="8838a-168">Yerini varsa `Workflow1` deneyin ve yapı veya iş akışını çalıştırdığınızda derleme hataları alırsınız.</span><span class="sxs-lookup"><span data-stu-id="8838a-168">If you do not replace `Workflow1` then you will get build errors when you try and build or run the workflow.</span></span>  
  
 [!code-csharp[CFX_WF_GettingStarted#12](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#12)]
 [!code-vb[CFX_WF_GettingStarted#12](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#12)]  
  
## <a name="see-also"></a><span data-ttu-id="8838a-169">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8838a-169">See Also</span></span>  
 <xref:System.Activities.WorkflowApplication>  
 <xref:System.Activities.Bookmark>  
 [<span data-ttu-id="8838a-170">Windows Workflow Foundation Programlama</span><span class="sxs-lookup"><span data-stu-id="8838a-170">Windows Workflow Foundation Programming</span></span>](../../../docs/framework/windows-workflow-foundation/programming.md)  
 [<span data-ttu-id="8838a-171">Başlangıç Öğreticisi</span><span class="sxs-lookup"><span data-stu-id="8838a-171">Getting Started Tutorial</span></span>](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [<span data-ttu-id="8838a-172">Nasıl yapılır: İş Akışı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="8838a-172">How to: Create a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md)  
 [<span data-ttu-id="8838a-173">Nasıl yapılır: Uzun Süre Çalışan İş Akışı Oluşturma ve Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="8838a-173">How to: Create and Run a Long Running Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md)  
 [<span data-ttu-id="8838a-174">Bir iş akışında giriş bekleme</span><span class="sxs-lookup"><span data-stu-id="8838a-174">Waiting for Input in a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/waiting-for-input-in-a-workflow.md)  
 [<span data-ttu-id="8838a-175">İş Akışları Barındırma</span><span class="sxs-lookup"><span data-stu-id="8838a-175">Hosting Workflows</span></span>](../../../docs/framework/windows-workflow-foundation/hosting-workflows.md)
