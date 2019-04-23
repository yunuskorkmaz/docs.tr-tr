---
title: 'Nasıl yapılır: Akış Çizelgesi İş Akışı Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5280e816-ae17-48c4-8de0-a1e6895dd8f0
ms.openlocfilehash: c8a16dc0269fbd768a73e99f15f53e38c207a8d4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59326846"
---
# <a name="how-to-create-a-sequential-workflow"></a><span data-ttu-id="236b0-102">Nasıl yapılır: Akış Çizelgesi İş Akışı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="236b0-102">How to: Create a Sequential Workflow</span></span>
<span data-ttu-id="236b0-103">İş akışları yerleşik etkinliklerden yanı sıra özel etkinliklerden oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="236b0-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="236b0-104">Bu konu başlığı altında adımlar hem yerleşik etkinlikler gibi kullanan bir iş akışı oluşturma işleminde <xref:System.Activities.Statements.Sequence> etkinliği ve özel etkinlikler önceki [nasıl yapılır: Bir etkinlik oluşturursunuz](how-to-create-an-activity.md) konu.</span><span class="sxs-lookup"><span data-stu-id="236b0-104">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Sequence> activity, and the custom activities from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="236b0-105">İş akışı sayısını tahmin eden oyun modelleri.</span><span class="sxs-lookup"><span data-stu-id="236b0-105">The workflow models a number guessing game.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="236b0-106">Önceki konularıyla ilgili her konuda Başlarken Öğreticisi bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="236b0-106">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="236b0-107">Bu konuyu tamamlamak için önce tamamlamanız gereken [nasıl yapılır: Bir etkinlik oluşturursunuz](how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="236b0-107">To complete this topic, you must first complete [How to: Create an Activity](how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="236b0-108">Öğreticinin tamamlanmış bir sürümünü indirmek için bkz [Windows Workflow Foundation (WF45) - başlangıç Öğreticisi](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="236b0-108">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="to-create-the-workflow"></a><span data-ttu-id="236b0-109">İş akışını oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="236b0-109">To create the workflow</span></span>  
  
1. <span data-ttu-id="236b0-110">Sağ **NumberGuessWorkflowActivities** içinde **Çözüm Gezgini** seçip **Ekle**, **yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="236b0-110">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>  
  
2. <span data-ttu-id="236b0-111">İçinde **yüklü**, **ortak öğeler** düğümünü **iş akışı**.</span><span class="sxs-lookup"><span data-stu-id="236b0-111">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="236b0-112">Seçin **etkinlik** gelen **iş akışı** listesi.</span><span class="sxs-lookup"><span data-stu-id="236b0-112">Select **Activity** from the **Workflow** list.</span></span>  
  
3. <span data-ttu-id="236b0-113">Tür `SequentialNumberGuessWorkflow` içine **adı** kutusuna ve tıklatın **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="236b0-113">Type `SequentialNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>  
  
4. <span data-ttu-id="236b0-114">Sürükle bir **dizisi** etkinliğinden **akış denetimi** bölümünü **araç kutusu** üzerine bırakın **Buraya Bırak etkinlik** üzerindeki etiket İş akışı tasarım yüzeyi.</span><span class="sxs-lookup"><span data-stu-id="236b0-114">Drag a **Sequence** activity from the **Control Flow** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>  
  
## <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="236b0-115">Bağımsız değişkenler ve iş akışı değişkenlerini oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="236b0-115">To create the workflow variables and arguments</span></span>  
  
1. <span data-ttu-id="236b0-116">Çift **SequentialNumberGuessWorkflow.xaml** içinde **Çözüm Gezgini** zaten görüntülenmiyorsa, iş akışı Tasarımcısı'nda görüntülenecek.</span><span class="sxs-lookup"><span data-stu-id="236b0-116">Double-click **SequentialNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>  
  
2. <span data-ttu-id="236b0-117">Tıklayın **bağımsız değişkenleri** sol alt tarafında görüntülenecek iş akışı Tasarımcısı **bağımsız değişkenleri** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="236b0-117">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
3. <span data-ttu-id="236b0-118">Tıklayın **bağımsız değişken oluşturma**.</span><span class="sxs-lookup"><span data-stu-id="236b0-118">Click **Create Argument**.</span></span>  
  
4. <span data-ttu-id="236b0-119">Tür `MaxNumber` içine **adı** kutusunda **içinde** gelen **yönü** aşağı açılan listesinden **Int32** gelen**Bağımsız değişken türü** aşağı açılan liste ve bağımsız değişkeni kaydetmek için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="236b0-119">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
5. <span data-ttu-id="236b0-120">Tıklayın **bağımsız değişken oluşturma**.</span><span class="sxs-lookup"><span data-stu-id="236b0-120">Click **Create Argument**.</span></span>  
  
6. <span data-ttu-id="236b0-121">Tür `Turns` içine **adı** altında yeni eklenen kutusunu `MaxNumber` bağımsız değişkeni, select **kullanıma** gelen **yönü** aşağı açılan listesinden  **Int32** gelen **bağımsız değişken türü** aşağı açılan liste ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="236b0-121">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
7. <span data-ttu-id="236b0-122">Tıklayın **bağımsız değişkenleri** etkinlik Tasarımcısı kapatmak için sol alt tarafında **bağımsız değişkenleri** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="236b0-122">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
8. <span data-ttu-id="236b0-123">Tıklayın **değişkenleri** sol alt tarafında görüntülenecek iş akışı Tasarımcısı **değişkenleri** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="236b0-123">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>  
  
9. <span data-ttu-id="236b0-124">Tıklayın **değişken oluşturma**.</span><span class="sxs-lookup"><span data-stu-id="236b0-124">Click **Create Variable**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="236b0-125">Hayır ise **oluşturma değişken** kutusu görüntülenir, tıklayın **dizisi** seçmek için iş akışı Tasarımcı yüzeyine etkinliği.</span><span class="sxs-lookup"><span data-stu-id="236b0-125">If no **Create Variable** box is displayed, click the **Sequence** activity on the workflow designer surface to select it.</span></span>  
  
10. <span data-ttu-id="236b0-126">Tür `Guess` içine **adı** kutusunda **Int32** gelen **değişken türü** aşağı açılan liste ve değişkeni kaydetmek için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="236b0-126">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
11. <span data-ttu-id="236b0-127">Tıklayın **değişken oluşturma**.</span><span class="sxs-lookup"><span data-stu-id="236b0-127">Click **Create Variable**.</span></span>  
  
12. <span data-ttu-id="236b0-128">Tür `Target` içine **adı** kutusunda **Int32** gelen **değişken türü** aşağı açılan liste ve değişkeni kaydetmek için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="236b0-128">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
13. <span data-ttu-id="236b0-129">Tıklayın **değişkenleri** etkinlik Tasarımcısı kapatmak için sol alt tarafında **değişkenleri** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="236b0-129">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>  
  
## <a name="to-add-the-workflow-activities"></a><span data-ttu-id="236b0-130">İş akışı etkinlikleri eklemek için</span><span class="sxs-lookup"><span data-stu-id="236b0-130">To add the workflow activities</span></span>  
  
1. <span data-ttu-id="236b0-131">Sürükleme bir **atama** etkinliğinden **Temelleri** bölümünü **araç kutusu** üzerine bırakın **dizisi** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="236b0-131">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Sequence** activity.</span></span> <span data-ttu-id="236b0-132">Tür `Target` içine **için** kutusu ve içine aşağıdaki ifade **bir C# ifadesi girin** veya **zadejte Výraz jazyka vb.** kutusu.</span><span class="sxs-lookup"><span data-stu-id="236b0-132">Type `Target` into the **To** box and the following expression into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="236b0-133">Varsa **araç kutusu** penceresi görüntülenmiyorsa, seçin **araç kutusu** gelen **görünümü** menüsü.</span><span class="sxs-lookup"><span data-stu-id="236b0-133">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
2. <span data-ttu-id="236b0-134">Sürükleme bir **DoWhile** etkinliğinden **akış denetimi** bölümünü **araç kutusu** ve böylece altına iş akışını bırakın **atama** Etkinlik.</span><span class="sxs-lookup"><span data-stu-id="236b0-134">Drag a **DoWhile** activity from the **Control Flow** section of the **Toolbox** and drop it on the workflow so that it is below the **Assign** activity.</span></span>  
  
3. <span data-ttu-id="236b0-135">İçine aşağıdaki ifadeyi yazın **DoWhile** etkinliğin **koşul** özellik değer kutusu.</span><span class="sxs-lookup"><span data-stu-id="236b0-135">Type the following expression into the **DoWhile** activity’s **Condition** property value box.</span></span>  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
     <span data-ttu-id="236b0-136">A <xref:System.Activities.Statements.DoWhile> etkinlik kendi alt etkinlikleri yürütür ve ardından değerlendirir, <xref:System.Activities.Statements.DoWhile.Condition%2A>.</span><span class="sxs-lookup"><span data-stu-id="236b0-136">A <xref:System.Activities.Statements.DoWhile> activity executes its child activities and then evaluates its <xref:System.Activities.Statements.DoWhile.Condition%2A>.</span></span> <span data-ttu-id="236b0-137">Varsa <xref:System.Activities.Statements.DoWhile.Condition%2A> değerlendiren `True`, etkinlikler, ardından <xref:System.Activities.Statements.DoWhile> tekrar yürütün.</span><span class="sxs-lookup"><span data-stu-id="236b0-137">If the <xref:System.Activities.Statements.DoWhile.Condition%2A> evaluates to `True`, then the activities in the <xref:System.Activities.Statements.DoWhile> execute again.</span></span> <span data-ttu-id="236b0-138">Bu örnekte, kullanıcının tahmin değerlendirilir ve <xref:System.Activities.Statements.DoWhile> tahmin doğru olana kadar devam eder.</span><span class="sxs-lookup"><span data-stu-id="236b0-138">In this example, the user’s guess is evaluated and the <xref:System.Activities.Statements.DoWhile> continues until the guess is correct.</span></span>  
  
4. <span data-ttu-id="236b0-139">Sürükleme bir **istemi** etkinliğinden **NumberGuessWorkflowActivities** bölümünü **araç kutusu** sürükleyip **DoWhile** etkinliği Önceki adımda.</span><span class="sxs-lookup"><span data-stu-id="236b0-139">Drag a **Prompt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **DoWhile** activity from the previous step.</span></span>  
  
5. <span data-ttu-id="236b0-140">İçinde **Özellikler penceresi**, türü `"EnterGuess"` tırnak işaretleri içine dahil **YerİşaretiAdı** özellik değer kutusu **istemi** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="236b0-140">In the **Properties Window**, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box for the **Prompt** activity.</span></span> <span data-ttu-id="236b0-141">Tür `Guess` içine **sonucu** özellik değer kutusu ve içine aşağıdaki ifadeyi yazın **metin** özellik kutusu.</span><span class="sxs-lookup"><span data-stu-id="236b0-141">Type `Guess` into the **Result** property value box, and type the following expression into the **Text** property box.</span></span>  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="236b0-142">Varsa **Özellikler penceresi** görüntülenen, select değil **Özellikler penceresi** gelen **görünümü** menüsü.</span><span class="sxs-lookup"><span data-stu-id="236b0-142">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
6. <span data-ttu-id="236b0-143">Sürükle bir **atama** etkinliğinden **Temelleri** bölümünü **araç kutusu** sürükleyip **DoWhile** BT'nin böylece etkinliği **İstemi** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="236b0-143">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it in the **DoWhile** activity so that it follows the **Prompt** activity.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="236b0-144">Bıraktığınız zaman **atama** etkinliği, Not nasıl iş akışı Tasarımcısı otomatik olarak ekler bir **dizisi** hem de içerecek şekilde etkinlik **istemi** etkinliği ve yeni eklenen **Atama** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="236b0-144">When you drop the **Assign** activity, note how the workflow designer automatically adds a **Sequence** activity to contain both the **Prompt** activity and the newly added **Assign** activity.</span></span>  
  
7. <span data-ttu-id="236b0-145">Tür `Turns` içine **için** kutusu ve `Turns + 1` içine **bir C# ifadesi girin** veya **zadejte Výraz jazyka vb.** kutusu.</span><span class="sxs-lookup"><span data-stu-id="236b0-145">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
8. <span data-ttu-id="236b0-146">Sürükle bir **varsa** etkinliğinden **akış denetimi** bölümünü **araç kutusu** sürükleyip **dizisi** BT'nin böylece etkinliği Yeni eklenen **atama** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="236b0-146">Drag an **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Sequence** activity so that it follows the newly added **Assign** activity.</span></span>  
  
9. <span data-ttu-id="236b0-147">İçine aşağıdaki ifadeyi yazın **varsa** etkinliğin **koşul** özellik değer kutusu.</span><span class="sxs-lookup"><span data-stu-id="236b0-147">Type the following expression into the **If** activity’s **Condition** property value box.</span></span>  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
10. <span data-ttu-id="236b0-148">Başka bir sürükleyin **varsa** etkinliğinden **akış denetimi** bölümünü **araç kutusu** sürükleyip **ardından** ilkbölümünü**Varsa** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="236b0-148">Drag another **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Then** section of the first **If** activity.</span></span>  
  
11. <span data-ttu-id="236b0-149">Yeni eklenen aşağıdaki ifadeyi yazın **varsa** etkinliğin **koşul** özellik değer kutusu.</span><span class="sxs-lookup"><span data-stu-id="236b0-149">Type the following expression into the newly added **If** activity’s **Condition** property value box.</span></span>  
  
    ```
    Guess < Target  
    ```  
  
12. <span data-ttu-id="236b0-150">İki **WriteLine** etkinlikten **Temelleri** bölümünü **araç kutusu** ve böylece bir yer bırakın **ardından** bölümü Yeni eklenen **varsa** etkinliği ve bir **Else** bölümü.</span><span class="sxs-lookup"><span data-stu-id="236b0-150">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that one is in the **Then** section of the newly added **If** activity, and one is in the **Else** section.</span></span>  
  
13. <span data-ttu-id="236b0-151">Tıklayın **WriteLine** etkinliğinde **ardından** seçmek için bölüm ve içine aşağıdaki ifadeyi yazın **metin** özellik değer kutusu.</span><span class="sxs-lookup"><span data-stu-id="236b0-151">Click the **WriteLine** activity in the **Then** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```text
    "Your guess is too low."  
    ```  
  
14. <span data-ttu-id="236b0-152">Tıklayın **WriteLine** etkinliğinde **Else** seçmek için bölüm ve içine aşağıdaki ifadeyi yazın **metin** özellik değer kutusu.</span><span class="sxs-lookup"><span data-stu-id="236b0-152">Click the **WriteLine** activity in the **Else** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```text
    "Your guess is too high."  
    ```  
  
     <span data-ttu-id="236b0-153">Aşağıdaki örnekte, tamamlanmış bir iş akışı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="236b0-153">The following example illustrates the completed workflow:</span></span>  
  
     ![Tamamlanan sıralı iş akışı gösteren ekran görüntüsü.](./media/how-to-create-a-sequential-workflow/complete-sequential-workflow.jpg)  
  
## <a name="to-build-the-workflow"></a><span data-ttu-id="236b0-155">İş akışı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="236b0-155">To build the workflow</span></span>  
  
1. <span data-ttu-id="236b0-156">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="236b0-156">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="236b0-157">Lütfen iş akışının nasıl çalıştırılacağını yönergeleri görmek için bir sonraki konu [nasıl yapılır: İş akışı çalıştırma](how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="236b0-157">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span> <span data-ttu-id="236b0-158">Zaten tamamladıysanız [nasıl yapılır: İş akışı çalıştırma](how-to-run-a-workflow.md) adım iş akışı farklı bir stil ve çalıştırmak bu adımdaki sıralı iş akışı kullanarak istediğiniz, atlayın [uygulaması derleme ve çalıştırma için](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) bölümünü [nasıl yapılır: İş akışı çalıştırma](how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="236b0-158">If you have already completed the [How to: Run a Workflow](how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the sequential workflow from this step, skip ahead to the [To build and run the application](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="236b0-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="236b0-159">See also</span></span>

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [<span data-ttu-id="236b0-160">Windows Workflow Foundation Programlama</span><span class="sxs-lookup"><span data-stu-id="236b0-160">Windows Workflow Foundation Programming</span></span>](programming.md)
- [<span data-ttu-id="236b0-161">İş Akışları Tasarlama</span><span class="sxs-lookup"><span data-stu-id="236b0-161">Designing Workflows</span></span>](designing-workflows.md)
- [<span data-ttu-id="236b0-162">Başlangıç Öğreticisi</span><span class="sxs-lookup"><span data-stu-id="236b0-162">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="236b0-163">Nasıl yapılır: Bir etkinlik oluşturma</span><span class="sxs-lookup"><span data-stu-id="236b0-163">How to: Create an Activity</span></span>](how-to-create-an-activity.md)
- [<span data-ttu-id="236b0-164">Nasıl yapılır: İş akışı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="236b0-164">How to: Run a Workflow</span></span>](how-to-run-a-workflow.md)
