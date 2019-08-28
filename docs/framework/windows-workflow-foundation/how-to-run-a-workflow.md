---
title: 'Nasıl yapılır: İş Akışı Çalıştırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f814ff82-fe2b-4614-aebb-b768c3e61179
ms.openlocfilehash: 07f0e5dc232411633626add460ffc29cc7a79d81
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044347"
---
# <a name="how-to-run-a-workflow"></a><span data-ttu-id="cdd2c-102">Nasıl yapılır: İş Akışı Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="cdd2c-102">How to: Run a Workflow</span></span>
<span data-ttu-id="cdd2c-103">Bu konu, başlangıç öğreticisini Windows Workflow Foundation ve bir iş akışı konağının nasıl oluşturulacağını ve önceki [nasıl yapılır: Bir iş akışı](how-to-create-a-workflow.md) konusu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-103">This topic is a continuation of the Windows Workflow Foundation Getting Started tutorial and discusses how to create a workflow host and run the workflow defined in the previous [How to: Create a Workflow](how-to-create-a-workflow.md) topic.</span></span>

> [!NOTE]
> <span data-ttu-id="cdd2c-104">Başlangıç öğreticisindeki her konu, önceki konulara bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-104">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="cdd2c-105">Bu konuyu tamamlayabilmeniz için öncelikle [şunları yapmanız gerekir: Etkinlik](how-to-create-an-activity.md) oluşturun ve [şunları yapın: Bir Iş akışı](how-to-create-a-workflow.md)oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-105">To complete this topic you must first complete [How to: Create an Activity](how-to-create-an-activity.md) and [How to: Create a Workflow](how-to-create-a-workflow.md).</span></span>

> [!NOTE]
> <span data-ttu-id="cdd2c-106">Öğreticinin tamamlanmış bir sürümünü indirmek için, bkz. [Windows Workflow Foundation (WF45)-Başlangıç Öğreticisi](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="cdd2c-106">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-workflow-host-project"></a><span data-ttu-id="cdd2c-107">İş akışı konak projesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="cdd2c-107">To create the workflow host project</span></span>  
  
1. <span data-ttu-id="cdd2c-108">Çözümü önceki [konumundan açın: Visual Studio 2012](how-to-create-an-activity.md) kullanarak bir etkinlik konusu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-108">Open the solution from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic by using Visual Studio 2012.</span></span>  
  
2. <span data-ttu-id="cdd2c-109">**Çözüm Gezgini** 'de **WF45GettingStartedTutorial** çözümüne sağ tıklayın ve **Ekle**, **Yeni proje**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-109">Right-click the **WF45GettingStartedTutorial** solution in **Solution Explorer** and select **Add**, **New Project**.</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="cdd2c-110">**Çözüm Gezgini** penceresi görüntülenmiyorsa, **Görünüm** menüsünden **Çözüm Gezgini** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-110">If the **Solution Explorer** window is not displayed, select **Solution Explorer** from the **View** menu.</span></span>

3. <span data-ttu-id="cdd2c-111">**Yüklü** düğümde, **C#görsel**, **iş akışı** (veya **Visual Basic**, **iş akışı**) öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-111">In the **Installed** node, select **Visual C#**, **Workflow** (or **Visual Basic**, **Workflow**).</span></span>

    > [!NOTE]
    > <span data-ttu-id="cdd2c-112">Visual Studio 'da birincil dil olarak yapılandırılmış programlama diline bağlı olarak, **Visual C#**  veya **Visual Basic** düğümü **yüklü** düğümdeki **diğer diller** düğümü altında olabilir.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-112">Depending on which programming language is configured as the primary language in Visual Studio, the **Visual C#** or **Visual Basic** node may be under the **Other Languages** node in the **Installed** node.</span></span>

     <span data-ttu-id="cdd2c-113">**.NET Framework 4,5** ' nin .NET Framework sürüm açılan listesinde seçildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-113">Ensure that **.NET Framework 4.5** is selected in the .NET Framework version drop-down list.</span></span> <span data-ttu-id="cdd2c-114">İş akışı listesinden iş akışı **konsol uygulaması** ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-114">Select **Workflow Console Application** from the **Workflow** list.</span></span> <span data-ttu-id="cdd2c-115">Ad `NumberGuessWorkflowHost` kutusuna yazın ve **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-115">Type `NumberGuessWorkflowHost` into the **Name** box and click **OK**.</span></span> <span data-ttu-id="cdd2c-116">Bu, temel iş akışı barındırma desteğiyle bir başlatıcı iş akışı uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-116">This creates a starter workflow application with basic workflow hosting support.</span></span> <span data-ttu-id="cdd2c-117">Bu temel barındırma kodu değiştirilir ve iş akışı uygulamasını çalıştırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-117">This basic hosting code is modified and used to run the workflow application.</span></span>

4. <span data-ttu-id="cdd2c-118">**Çözüm Gezgini** ' de yeni eklenen **Numberguessworkflowwhost** projesine sağ tıklayın ve **Başvuru Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-118">Right-click the newly added **NumberGuessWorkflowHost** project in **Solution Explorer** and select **Add Reference**.</span></span> <span data-ttu-id="cdd2c-119">**Başvuru Ekle** listesinden **çözüm** ' i seçin, **NumberGuessWorkflowActivities**yanındaki onay kutusunu işaretleyin ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-119">Select **Solution** from the **Add Reference** list, check the checkbox beside **NumberGuessWorkflowActivities**, and then click **OK**.</span></span>

5. <span data-ttu-id="cdd2c-120">**Çözüm Gezgini** 'de **Workflow1. xaml** öğesine sağ tıklayın ve **Sil**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-120">Right-click **Workflow1.xaml** in **Solution Explorer** and choose **Delete**.</span></span> <span data-ttu-id="cdd2c-121">Onaylamak için **Tamam** ' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-121">Click **OK** to confirm.</span></span>

### <a name="to-modify-the-workflow-hosting-code"></a><span data-ttu-id="cdd2c-122">İş akışı barındırma kodunu değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="cdd2c-122">To modify the workflow hosting code</span></span>

1. <span data-ttu-id="cdd2c-123">Kodu göstermek için **Çözüm Gezgini** 'de **program.cs** veya **Module1. vb** öğesine çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-123">Double-click **Program.cs** or **Module1.vb** in **Solution Explorer** to display the code.</span></span>

    > [!TIP]
    > <span data-ttu-id="cdd2c-124">**Çözüm Gezgini** penceresi görüntülenmiyorsa, **Görünüm** menüsünden **Çözüm Gezgini** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-124">If the **Solution Explorer** window is not displayed, select **Solution Explorer** from the **View** menu.</span></span>

     <span data-ttu-id="cdd2c-125">Bu proje **Iş akışı konsol uygulaması** şablonu kullanılarak oluşturulduğundan, **program.cs** veya **Module1. vb** , aşağıdaki temel iş akışı barındırma kodunu içerir.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-125">Because this project was created by using the **Workflow Console Application** template, **Program.cs** or **Module1.vb** contains the following basic workflow hosting code.</span></span>

    ```vb
    ' Create and cache the workflow definition.
    Dim workflow1 As Activity = New Workflow1()
    WorkflowInvoker.Invoke(workflow1)
    ```

    ```csharp
    // Create and cache the workflow definition.
    Activity workflow1 = new Workflow1();
    WorkflowInvoker.Invoke(workflow1);
    ```

     <span data-ttu-id="cdd2c-126">Oluşturulan bu barındırma kodu kullanılır <xref:System.Activities.WorkflowInvoker>.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-126">This generated hosting code uses <xref:System.Activities.WorkflowInvoker>.</span></span> <span data-ttu-id="cdd2c-127"><xref:System.Activities.WorkflowInvoker>bir iş akışını Yöntem çağrısı gibi çağırmak için basit bir yol sağlar ve yalnızca kalıcılığı kullanmayan iş akışları için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-127"><xref:System.Activities.WorkflowInvoker> provides a simple way for invoking a workflow as if it were a method call and can be used only for workflows that do not use persistence.</span></span> <span data-ttu-id="cdd2c-128"><xref:System.Activities.WorkflowApplication>yaşam döngüsü olaylarının, yürütme denetiminin, yer işaretinin sürdürme ve kalıcılığın bildirimini içeren iş akışlarını yürütmek için daha zengin bir model sağlar.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-128"><xref:System.Activities.WorkflowApplication> provides a richer model for executing workflows that includes notification of life-cycle events, execution control, bookmark resumption, and persistence.</span></span> <span data-ttu-id="cdd2c-129">Bu örnek, yer işaretlerini <xref:System.Activities.WorkflowApplication> kullanır ve iş akışını barındırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-129">This example uses bookmarks and <xref:System.Activities.WorkflowApplication> is used for hosting the workflow.</span></span> <span data-ttu-id="cdd2c-130">Var `using` olan **using** veya **Imports** deyimlerinin altındaki **program.cs** veya **Module1. vb** üst kısmına aşağıdaki veya **Imports** deyimini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-130">Add the following `using` or **Imports** statement at the top of **Program.cs** or **Module1.vb** below the existing **using** or **Imports** statements.</span></span>

    ```vb
    Imports NumberGuessWorkflowActivities
    Imports System.Threading
    ```

    ```csharp
    using NumberGuessWorkflowActivities;
    using System.Threading;
    ```

     <span data-ttu-id="cdd2c-131">Aşağıdaki temel <xref:System.Activities.WorkflowInvoker> <xref:System.Activities.WorkflowApplication> barındırma koduyla kullanılan kod satırlarını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-131">Replace the lines of code that use <xref:System.Activities.WorkflowInvoker> with the following basic <xref:System.Activities.WorkflowApplication> hosting code.</span></span> <span data-ttu-id="cdd2c-132">Bu örnek barındırma kodu, bir iş akışını barındırmak ve çağırmak için temel adımları gösterir, ancak henüz bu konudan iş akışını başarıyla çalıştırmaya yönelik işlevselliği içermez.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-132">This sample hosting code demonstrates the basic steps for hosting and invoking a workflow, but does not yet contain the functionality to successfully run the workflow from this topic.</span></span> <span data-ttu-id="cdd2c-133">Aşağıdaki adımlarda, bu temel kod değiştirilir ve uygulama tamamlanana kadar ek özellikler eklenir.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-133">In the following steps, this basic code is modified and additional features are added until the application is complete.</span></span>

    > [!NOTE]
    > <span data-ttu-id="cdd2c-134">Lütfen bu `Workflow1` örneklerde, önceki `FlowchartNumberGuessWorkflow` `StateMachineNumberGuessWorkflow` `SequentialNumberGuessWorkflow` adımdatamamladığınızişakışınabağlıolarak,[veya ile değiştirin: Bir iş akışı](how-to-create-a-workflow.md) adımı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-134">Please replace `Workflow1` in these examples with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow you completed in the previous [How to: Create a Workflow](how-to-create-a-workflow.md) step.</span></span> <span data-ttu-id="cdd2c-135">' Yi değiştirip `Workflow1` iş akışını oluşturup oluştururken veya çalıştırdığınızda yapı hataları alırsınız.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-135">If you do not replace `Workflow1` then you will get build errors when you try and build or run the workflow.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#4](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#4)]
     [!code-vb[CFX_WF_GettingStarted#4](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#4)]

     <span data-ttu-id="cdd2c-136">Bu kod bir <xref:System.Activities.WorkflowApplication>oluşturur, üç iş akışı yaşam döngüsü olayına abone olur, bir <xref:System.Activities.WorkflowApplication.Run%2A>çağrısıyla iş akışını başlatır ve sonra iş akışının tamamlanmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-136">This code creates a <xref:System.Activities.WorkflowApplication>, subscribes to three workflow life-cycle events, starts the workflow with a call to <xref:System.Activities.WorkflowApplication.Run%2A>, and then waits for the workflow to complete.</span></span> <span data-ttu-id="cdd2c-137">İş akışı tamamlandığında, <xref:System.Threading.AutoResetEvent> ayarlanır ve ana bilgisayar uygulaması tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-137">When the workflow completes, the <xref:System.Threading.AutoResetEvent> is set and the host application completes.</span></span>

### <a name="to-set-input-arguments-of-a-workflow"></a><span data-ttu-id="cdd2c-138">Bir iş akışının giriş bağımsız değişkenlerini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="cdd2c-138">To set input arguments of a workflow</span></span>

1. <span data-ttu-id="cdd2c-139">Aşağıdaki deyimi, var olan `using` or `Imports` deyimlerinin altındaki **program.cs** veya **Module1. vb** öğesinin üstüne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-139">Add the following statement at the top of **Program.cs** or **Module1.vb** below the existing `using` or `Imports` statements.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#5](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#5)]
     [!code-vb[CFX_WF_GettingStarted#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#5)]

2. <span data-ttu-id="cdd2c-140">Yeni <xref:System.Activities.WorkflowApplication> oluşturan kod satırını, oluşturulduğunda iş akışına bir parametre sözlüğü oluşturup ileten aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-140">Replace the line of code that creates the new <xref:System.Activities.WorkflowApplication> with the following code that creates and passes a dictionary of parameters to the workflow when it is created.</span></span>

    > [!NOTE]
    > <span data-ttu-id="cdd2c-141">Lütfen bu `Workflow1` örneklerde, önceki `FlowchartNumberGuessWorkflow` `StateMachineNumberGuessWorkflow` `SequentialNumberGuessWorkflow` adımdatamamladığınızişakışınabağlıolarak,[veya ile değiştirin: Bir iş akışı](how-to-create-a-workflow.md) adımı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-141">Please replace `Workflow1` in these examples with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow you completed in the previous [How to: Create a Workflow](how-to-create-a-workflow.md) step.</span></span> <span data-ttu-id="cdd2c-142">' Yi değiştirip `Workflow1` iş akışını oluşturup oluştururken veya çalıştırdığınızda yapı hataları alırsınız.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-142">If you do not replace `Workflow1` then you will get build errors when you try and build or run the workflow.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#6](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]

     <span data-ttu-id="cdd2c-143">Bu sözlük, `MaxNumber`anahtarı olan bir öğesi içerir.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-143">This dictionary contains one element with a key of `MaxNumber`.</span></span> <span data-ttu-id="cdd2c-144">Giriş sözlüğündeki anahtarlar, iş akışının kök etkinliğinin giriş bağımsız değişkenlerine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-144">Keys in the input dictionary correspond to input arguments on the root activity of the workflow.</span></span> <span data-ttu-id="cdd2c-145">`MaxNumber`, rastgele oluşturulan sayı için üst sınırı belirlemede iş akışı tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-145">`MaxNumber` is used by the workflow to determine the upper bound for the randomly generated number.</span></span>

### <a name="to-retrieve-output-arguments-of-a-workflow"></a><span data-ttu-id="cdd2c-146">Bir iş akışının çıkış bağımsız değişkenlerini almak için</span><span class="sxs-lookup"><span data-stu-id="cdd2c-146">To retrieve output arguments of a workflow</span></span>

1. <span data-ttu-id="cdd2c-147"><xref:System.Activities.WorkflowApplication.Completed%2A> İşleyiciyi, iş akışı tarafından kullanılan dönüşler sayısını almak ve görüntüleyecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-147">Modify the <xref:System.Activities.WorkflowApplication.Completed%2A> handler to retrieve and display the number of turns used by the workflow.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#7](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#7)]
     [!code-vb[CFX_WF_GettingStarted#7](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#7)]

### <a name="to-resume-a-bookmark"></a><span data-ttu-id="cdd2c-148">Bir yer işaretini sürdürülmesi için</span><span class="sxs-lookup"><span data-stu-id="cdd2c-148">To resume a bookmark</span></span>

1. <span data-ttu-id="cdd2c-149">Aşağıdaki kodu, mevcut `Main` <xref:System.Threading.AutoResetEvent> bildiriminden hemen sonra yönteminin en üstüne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-149">Add the following code at the top of the `Main` method just after the existing <xref:System.Threading.AutoResetEvent> declaration.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#8](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#8)]
     [!code-vb[CFX_WF_GettingStarted#8](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#8)]

2. <span data-ttu-id="cdd2c-150">' De <xref:System.Activities.WorkflowApplication.Idle%2A> `Main`var olan üç iş akışı yaşam döngüsü işleyicisinin hemen altına aşağıdaki işleyiciyi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-150">Add the following <xref:System.Activities.WorkflowApplication.Idle%2A> handler just below the existing three workflow life-cycle handlers in `Main`.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#9](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#9)]
     [!code-vb[CFX_WF_GettingStarted#9](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#9)]

     <span data-ttu-id="cdd2c-151">Her iş akışı bir sonraki tahmin için bekleme durumunda olduğunda, bu işleyici çağrılır ve `idleAction` <xref:System.Threading.AutoResetEvent> ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-151">Each time the workflow becomes idle waiting for the next guess, this handler is called and the `idleAction` <xref:System.Threading.AutoResetEvent> is set.</span></span> <span data-ttu-id="cdd2c-152">Aşağıdaki adımdaki kod, iş akışının bir `idleEvent` sonraki `syncEvent` tahmin için mi beklediğini yoksa tamamlanıp tamamlanmadığını mı öğrenmek için ve kullanır.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-152">The code in the following step uses `idleEvent` and `syncEvent` to determine whether the workflow is waiting for the next guess or is complete.</span></span>

    > [!NOTE]
    > <span data-ttu-id="cdd2c-153">Bu örnekte, ana bilgisayar uygulaması, <xref:System.Activities.WorkflowApplication.Completed%2A> ve <xref:System.Activities.WorkflowApplication.Idle%2A> işleyicilerinde otomatik sıfırlama olaylarını kullanarak konak uygulamasını iş akışının ilerlemesiyle eşitler.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-153">In this example, the host application uses auto-reset events in the <xref:System.Activities.WorkflowApplication.Completed%2A> and <xref:System.Activities.WorkflowApplication.Idle%2A> handlers to synchronize the host application with the progress of the workflow.</span></span> <span data-ttu-id="cdd2c-154">Blok ve iş akışının bir yer işareti devam etmeden önce boşta beklemesi gerekli değildir, ancak bu örnekte ana iş akışının tamamını olup veya kullanarakdahafazlakullanıcıgirdisiolupbekliyorolduğunubilmesiiçineşitlemeolaylarıgereklidir<xref:System.Activities.Bookmark>.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-154">It is not necessary to block and wait for the workflow to become idle before resuming a bookmark, but in this example the synchronization events are required so the host knows whether the workflow is complete or whether it is waiting on more user input by using the <xref:System.Activities.Bookmark>.</span></span> <span data-ttu-id="cdd2c-155">Daha fazla bilgi için bkz. [yer işaretleri](bookmarks.md).</span><span class="sxs-lookup"><span data-stu-id="cdd2c-155">For more information, see [Bookmarks](bookmarks.md).</span></span>

3. <span data-ttu-id="cdd2c-156">`WaitOne`' A çağrıyı kaldırın ve kullanıcıdan giriş toplamak için kodu kodla değiştirin ve ' ı <xref:System.Activities.Bookmark>sürdürülemez.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-156">Remove the call to `WaitOne`, and replace it with code to gather input from the user and resume the <xref:System.Activities.Bookmark>.</span></span>

     <span data-ttu-id="cdd2c-157">Aşağıdaki kod satırını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-157">Remove the following line of code.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#10](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#10)]
     [!code-vb[CFX_WF_GettingStarted#10](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#10)]

     <span data-ttu-id="cdd2c-158">Aşağıdaki örnekle değiştirin.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-158">Replace it with the following example.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#11](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#11)]
     [!code-vb[CFX_WF_GettingStarted#11](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#11)]

## <a name="BKMK_ToRunTheApplication"></a><span data-ttu-id="cdd2c-159">Uygulamayı derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="cdd2c-159">To build and run the application</span></span>

1. <span data-ttu-id="cdd2c-160">**Çözüm Gezgini** Için **Numberguessworkflowwhost** öğesine sağ tıklayın ve **Başlangıç projesi olarak ayarla**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-160">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and select **Set as StartUp Project**.</span></span>

2. <span data-ttu-id="cdd2c-161">Uygulamayı derlemek ve çalıştırmak için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-161">Press CTRL+F5 to build and run the application.</span></span> <span data-ttu-id="cdd2c-162">Sayıyı olabildiğince az sürede tahmin etmeye çalışın.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-162">Try to guess the number in as few turns as possible.</span></span>

     <span data-ttu-id="cdd2c-163">Uygulamayı diğer iş akışı stillerinden biriyle denemek için `Workflow1` , veya <xref:System.Activities.WorkflowApplication> ile `FlowchartNumberGuessWorkflow` `SequentialNumberGuessWorkflow`oluşturan kodda, ya `StateMachineNumberGuessWorkflow`da istediğiniz iş akışı stiline bağlı olarak öğesini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-163">To try the application with one of the other styles of workflow, replace `Workflow1` in the code that creates the <xref:System.Activities.WorkflowApplication> with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow style you desire.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#6](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]

     <span data-ttu-id="cdd2c-164">Bir iş akışı uygulamasına Kalıcılık ekleme hakkında yönergeler için, bir sonraki konuya [bkz. nasıl yapılır: Uzun süre çalışan bir Iş akışı](how-to-create-and-run-a-long-running-workflow.md)oluşturun ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-164">For instructions about how to add persistence to a workflow application, see the next topic, [How to: Create and Run a Long Running Workflow](how-to-create-and-run-a-long-running-workflow.md).</span></span>

## <a name="example"></a><span data-ttu-id="cdd2c-165">Örnek</span><span class="sxs-lookup"><span data-stu-id="cdd2c-165">Example</span></span>
 <span data-ttu-id="cdd2c-166">Aşağıdaki örnek, `Main` yöntemi için kod listesinin tamamdır.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-166">The following example is the complete code listing for the `Main` method.</span></span>

> [!NOTE]
> <span data-ttu-id="cdd2c-167">Lütfen bu `Workflow1` örneklerde, önceki `FlowchartNumberGuessWorkflow` `StateMachineNumberGuessWorkflow` `SequentialNumberGuessWorkflow` adımdatamamladığınızişakışınabağlıolarak,[veya ile değiştirin: Bir iş akışı](how-to-create-a-workflow.md) adımı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-167">Please replace `Workflow1` in these examples with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow you completed in the previous [How to: Create a Workflow](how-to-create-a-workflow.md) step.</span></span> <span data-ttu-id="cdd2c-168">' Yi değiştirip `Workflow1` iş akışını oluşturup oluştururken veya çalıştırdığınızda yapı hataları alırsınız.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-168">If you do not replace `Workflow1` then you will get build errors when you try and build or run the workflow.</span></span>

 [!code-csharp[CFX_WF_GettingStarted#12](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#12)]
 [!code-vb[CFX_WF_GettingStarted#12](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#12)]

## <a name="see-also"></a><span data-ttu-id="cdd2c-169">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cdd2c-169">See also</span></span>

- <xref:System.Activities.WorkflowApplication>
- <xref:System.Activities.Bookmark>
- [<span data-ttu-id="cdd2c-170">Windows Workflow Foundation Programlama</span><span class="sxs-lookup"><span data-stu-id="cdd2c-170">Windows Workflow Foundation Programming</span></span>](programming.md)
- [<span data-ttu-id="cdd2c-171">Başlangıç Öğreticisi</span><span class="sxs-lookup"><span data-stu-id="cdd2c-171">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="cdd2c-172">Nasıl yapılır: Iş akışı oluşturma</span><span class="sxs-lookup"><span data-stu-id="cdd2c-172">How to: Create a Workflow</span></span>](how-to-create-a-workflow.md)
- [<span data-ttu-id="cdd2c-173">Nasıl yapılır: Uzun süre çalışan bir Iş akışı oluşturma ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="cdd2c-173">How to: Create and Run a Long Running Workflow</span></span>](how-to-create-and-run-a-long-running-workflow.md)
- [<span data-ttu-id="cdd2c-174">Bir iş akışında giriş bekleme</span><span class="sxs-lookup"><span data-stu-id="cdd2c-174">Waiting for Input in a Workflow</span></span>](waiting-for-input-in-a-workflow.md)
- [<span data-ttu-id="cdd2c-175">İş Akışları Barındırma</span><span class="sxs-lookup"><span data-stu-id="cdd2c-175">Hosting Workflows</span></span>](hosting-workflows.md)
