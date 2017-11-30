---
title: "Nasıl yapılır: Sıralı iş akışı oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 5280e816-ae17-48c4-8de0-a1e6895dd8f0
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3bf6d8b499903522ee09021bb9339ece6a5894eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-sequential-workflow"></a><span data-ttu-id="efb81-102">Nasıl yapılır: Sıralı iş akışı oluşturma</span><span class="sxs-lookup"><span data-stu-id="efb81-102">How to: Create a Sequential Workflow</span></span>
<span data-ttu-id="efb81-103">İş akışları yerleşik etkinliklerden yanı sıra özel etkinliklerden oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="efb81-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="efb81-104">Bu konudaki adımları hem yerleşik etkinlikler gibi kullanan bir iş akışı oluşturma aracılığıyla <xref:System.Activities.Statements.Sequence> etkinliği ve önceki özel etkinlikler [nasıl yapılır: bir etkinlik oluşturmak](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) konu.</span><span class="sxs-lookup"><span data-stu-id="efb81-104">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Sequence> activity, and the custom activities from the previous [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="efb81-105">Sayı tahmin eden oyun iş akışını modeller.</span><span class="sxs-lookup"><span data-stu-id="efb81-105">The workflow models a number guessing game.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="efb81-106">Başlarken Öğreticisi her bir konuda önceki konularda bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="efb81-106">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="efb81-107">Bu konuda tamamlamak için önce tamamlamanız gereken [nasıl yapılır: bir etkinlik oluşturmak](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="efb81-107">To complete this topic, you must first complete [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="efb81-108">Öğreticinin tamamlanmış bir sürümünü indirmek için bkz: [Windows Workflow Foundation (WF45) - başlangıç Öğreticisi](http://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="efb81-108">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](http://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-workflow"></a><span data-ttu-id="efb81-109">İş akışını oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="efb81-109">To create the workflow</span></span>  
  
1.  <span data-ttu-id="efb81-110">Sağ **NumberGuessWorkflowActivities** içinde **Çözüm Gezgini** seçip **Ekle**, **yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="efb81-110">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>  
  
2.  <span data-ttu-id="efb81-111">İçinde **yüklü**, **ortak öğeler** düğümü, select **iş akışı**.</span><span class="sxs-lookup"><span data-stu-id="efb81-111">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="efb81-112">Seçin **etkinlik** gelen **iş akışı** listesi.</span><span class="sxs-lookup"><span data-stu-id="efb81-112">Select **Activity** from the **Workflow** list.</span></span>  
  
3.  <span data-ttu-id="efb81-113">Tür `SequentialNumberGuessWorkflow` içine **adı** kutusuna ve tıklatın **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="efb81-113">Type `SequentialNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>  
  
4.  <span data-ttu-id="efb81-114">Sürükleme bir **dizisi** etkinliğinden **akış denetimi** bölümünü **araç** ve üzerine bırakın **etkinliğini Drop burada** üzerindeki etiket İş akışı tasarım yüzeyi.</span><span class="sxs-lookup"><span data-stu-id="efb81-114">Drag a **Sequence** activity from the **Control Flow** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="efb81-115">İş akışı değişkenleri ve bağımsız değişkenler oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="efb81-115">To create the workflow variables and arguments</span></span>  
  
1.  <span data-ttu-id="efb81-116">Çift **SequentialNumberGuessWorkflow.xaml** içinde **Çözüm Gezgini** zaten görüntülenmiyorsa, iş akışı Tasarımcısı'nda görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="efb81-116">Double-click **SequentialNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>  
  
2.  <span data-ttu-id="efb81-117">Tıklatın **bağımsız değişkenleri** görüntülemek için iş akışı Tasarımcısı sol tarafındaki **bağımsız değişkenleri** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="efb81-117">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
3.  <span data-ttu-id="efb81-118">Tıklatın **bağımsız değişkeni oluşturma**.</span><span class="sxs-lookup"><span data-stu-id="efb81-118">Click **Create Argument**.</span></span>  
  
4.  <span data-ttu-id="efb81-119">Tür `MaxNumber` içine **adı** kutusunda **içinde** gelen **yönü** aşağı açılan listesinden, **Int32** gelen**Bağımsız değişken türü** aşağı açılan liste ve bağımsız değişkeni kaydetmek için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="efb81-119">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
5.  <span data-ttu-id="efb81-120">Tıklatın **bağımsız değişkeni oluşturma**.</span><span class="sxs-lookup"><span data-stu-id="efb81-120">Click **Create Argument**.</span></span>  
  
6.  <span data-ttu-id="efb81-121">Tür `Turns` içine **adı** altında yeni eklenen kutusuna `MaxNumber` bağımsız değişkeni, select **çıkışı** gelen **yönü** aşağı açılan listesinden,  **Int32** gelen **bağımsız değişken türü** aşağı açılan liste ve ENTER tuşuna BASIN.</span><span class="sxs-lookup"><span data-stu-id="efb81-121">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
7.  <span data-ttu-id="efb81-122">Tıklatın **bağımsız değişkenleri** kapatmak için etkinlik Tasarımcısı sol tarafındaki **bağımsız değişkenleri** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="efb81-122">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
8.  <span data-ttu-id="efb81-123">Tıklatın **değişkenleri** görüntülemek için iş akışı Tasarımcısı sol tarafındaki **değişkenleri** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="efb81-123">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>  
  
9. <span data-ttu-id="efb81-124">Tıklatın **değişken oluşturma**.</span><span class="sxs-lookup"><span data-stu-id="efb81-124">Click **Create Variable**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="efb81-125">Yoksa **oluşturma değişken** kutusu görüntülenir, tıklatın **dizisi** seçmek için iş akışı Tasarımcısı yüzey üzerinde etkinlik.</span><span class="sxs-lookup"><span data-stu-id="efb81-125">If no **Create Variable** box is displayed, click the **Sequence** activity on the workflow designer surface to select it.</span></span>  
  
10. <span data-ttu-id="efb81-126">Tür `Guess` içine **adı** kutusunda **Int32** gelen **değişken türü** aşağı açılan liste ve değişkeni kaydetmek için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="efb81-126">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
11. <span data-ttu-id="efb81-127">Tıklatın **değişken oluşturma**.</span><span class="sxs-lookup"><span data-stu-id="efb81-127">Click **Create Variable**.</span></span>  
  
12. <span data-ttu-id="efb81-128">Tür `Target` içine **adı** kutusunda **Int32** gelen **değişken türü** aşağı açılan liste ve değişkeni kaydetmek için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="efb81-128">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
13. <span data-ttu-id="efb81-129">Tıklatın **değişkenleri** kapatmak için etkinlik Tasarımcısı sol tarafındaki **değişkenleri** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="efb81-129">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>  
  
### <a name="to-add-the-workflow-activities"></a><span data-ttu-id="efb81-130">İş akışı etkinlikleri eklemek için</span><span class="sxs-lookup"><span data-stu-id="efb81-130">To add the workflow activities</span></span>  
  
1.  <span data-ttu-id="efb81-131">Sürükleme bir **atamak** etkinliğinden **Temelleri** bölümünü **araç** ve üzerine bırakın **dizisi** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="efb81-131">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Sequence** activity.</span></span> <span data-ttu-id="efb81-132">Tür `Target` içine **için** kutusu ve aşağıdaki ifadesine **bir C# ifadesi girin** veya **bir VB ifadesi girin** kutusu.</span><span class="sxs-lookup"><span data-stu-id="efb81-132">Type `Target` into the **To** box and the following expression into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="efb81-133">Varsa **araç** penceresi görüntülenmez, seçin **araç** gelen **Görünüm** menüsü.</span><span class="sxs-lookup"><span data-stu-id="efb81-133">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
2.  <span data-ttu-id="efb81-134">Sürükleme bir **DoWhile** etkinliğinden **akış denetimi** bölümünü **araç** ve aşağıda olmasını sağlamak iş akışında bırakma **Ata** Etkinlik.</span><span class="sxs-lookup"><span data-stu-id="efb81-134">Drag a **DoWhile** activity from the **Control Flow** section of the **Toolbox** and drop it on the workflow so that it is below the **Assign** activity.</span></span>  
  
3.  <span data-ttu-id="efb81-135">İçine aşağıdaki ifadeyi yazın **DoWhile** etkinliğin **koşulu** özellik değeri kutusu.</span><span class="sxs-lookup"><span data-stu-id="efb81-135">Type the following expression into the **DoWhile** activity’s **Condition** property value box.</span></span>  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
     <span data-ttu-id="efb81-136">A <xref:System.Activities.Statements.DoWhile> etkinlik kendi alt etkinlikleri yürütür ve ardından değerlendirir kendi <xref:System.Activities.Statements.DoWhile.Condition%2A>.</span><span class="sxs-lookup"><span data-stu-id="efb81-136">A <xref:System.Activities.Statements.DoWhile> activity executes its child activities and then evaluates its <xref:System.Activities.Statements.DoWhile.Condition%2A>.</span></span> <span data-ttu-id="efb81-137">Varsa <xref:System.Activities.Statements.DoWhile.Condition%2A> değerlendiren `True`, ardından aktivitelerde <xref:System.Activities.Statements.DoWhile> yeniden yürütün.</span><span class="sxs-lookup"><span data-stu-id="efb81-137">If the <xref:System.Activities.Statements.DoWhile.Condition%2A> evaluates to `True`, then the activities in the <xref:System.Activities.Statements.DoWhile> execute again.</span></span> <span data-ttu-id="efb81-138">Bu örnekte, kullanıcının tahmin değerlendirilir ve <xref:System.Activities.Statements.DoWhile> tahmin doğru olana kadar devam eder.</span><span class="sxs-lookup"><span data-stu-id="efb81-138">In this example, the user’s guess is evaluated and the <xref:System.Activities.Statements.DoWhile> continues until the guess is correct.</span></span>  
  
4.  <span data-ttu-id="efb81-139">Sürükleme bir **komut istemi** etkinliğinden **NumberGuessWorkflowActivities** bölümünü **araç** sürükleyip bırakın **DoWhile** etkinliği Önceki adımda.</span><span class="sxs-lookup"><span data-stu-id="efb81-139">Drag a **Prompt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **DoWhile** activity from the previous step.</span></span>  
  
5.  <span data-ttu-id="efb81-140">İçinde **Özellikler penceresini**, türü `"EnterGuess"` tırnak işaretleri içine dahil **YerİşaretiAdı** özellik değeri kutusu **komut istemi** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="efb81-140">In the **Properties Window**, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box for the **Prompt** activity.</span></span> <span data-ttu-id="efb81-141">Tür `Guess` içine **sonuç** özelliği değeri kutusunu ve içine aşağıdaki ifadeyi yazın **metin** özellik kutusu.</span><span class="sxs-lookup"><span data-stu-id="efb81-141">Type `Guess` into the **Result** property value box, and type the following expression into the **Text** property box.</span></span>  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="efb81-142">Varsa **Özellikler penceresini** görüntülenen, select değil **Özellikler penceresini** gelen **Görünüm** menüsü.</span><span class="sxs-lookup"><span data-stu-id="efb81-142">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
6.  <span data-ttu-id="efb81-143">Sürükleme bir **atamak** etkinliğinden **Temelleri** bölümünü **araç** sürükleyip bırakın **DoWhile** onun aşağıdaki şekilde etkinliği **Komut istemi** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="efb81-143">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it in the **DoWhile** activity so that it follows the **Prompt** activity.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="efb81-144">Bıraktığınız zaman **atamak** etkinliği, nasıl iş akışı Tasarımcısı'nı otomatik olarak ekler Not bir **dizisi** her ikisi de içerecek şekilde etkinlik **komut istemi** etkinliği ve yeni eklenen **Atamak** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="efb81-144">When you drop the **Assign** activity, note how the workflow designer automatically adds a **Sequence** activity to contain both the **Prompt** activity and the newly added **Assign** activity.</span></span>  
  
7.  <span data-ttu-id="efb81-145">Tür `Turns` içine **için** kutusu ve `Turns + 1` içine **bir C# ifadesi girin** veya **bir VB ifadesi girin** kutusu.</span><span class="sxs-lookup"><span data-stu-id="efb81-145">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
8.  <span data-ttu-id="efb81-146">Sürükleme bir **varsa** etkinliğinden **akış denetimi** bölümünü **araç** sürükleyip bırakın **dizisi** onun aşağıdaki şekilde etkinliği Yeni eklenen **atamak** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="efb81-146">Drag an **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Sequence** activity so that it follows the newly added **Assign** activity.</span></span>  
  
9. <span data-ttu-id="efb81-147">İçine aşağıdaki ifadeyi yazın **varsa** etkinliğin **koşulu** özellik değeri kutusu.</span><span class="sxs-lookup"><span data-stu-id="efb81-147">Type the following expression into the **If** activity’s **Condition** property value box.</span></span>  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
10. <span data-ttu-id="efb81-148">Başka bir sürükleyin **varsa** etkinliğinden **akış denetimi** bölümünü **araç** sürükleyip bırakın **sonra** ilkbölümünü**Varsa** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="efb81-148">Drag another **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Then** section of the first **If** activity.</span></span>  
  
11. <span data-ttu-id="efb81-149">Aşağıdaki ifade yeni eklenen yazın **varsa** etkinliğin **koşulu** özellik değeri kutusu.</span><span class="sxs-lookup"><span data-stu-id="efb81-149">Type the following expression into the newly added **If** activity’s **Condition** property value box.</span></span>  
  
    ```
    Guess < Target  
    ```  
  
12. <span data-ttu-id="efb81-150">İki **WriteLine** etkinliklerden **Temelleri** bölümünü **araç** ve böylece içinde biridir bırakın **sonra** bölümü Yeni eklenen **varsa** etkinliği ve bir **Else** bölümü.</span><span class="sxs-lookup"><span data-stu-id="efb81-150">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that one is in the **Then** section of the newly added **If** activity, and one is in the **Else** section.</span></span>  
  
13. <span data-ttu-id="efb81-151">Tıklatın **WriteLine** etkinliğinde **sonra** seçmek için bölümünde ve içine aşağıdaki ifadeyi yazın **metin** özellik değeri kutusu.</span><span class="sxs-lookup"><span data-stu-id="efb81-151">Click the **WriteLine** activity in the **Then** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```vb  
    "Your guess is too low."  
    ```  
  
14. <span data-ttu-id="efb81-152">Tıklatın **WriteLine** etkinliğinde **Else** seçmek için bölümünde ve içine aşağıdaki ifadeyi yazın **metin** özellik değeri kutusu.</span><span class="sxs-lookup"><span data-stu-id="efb81-152">Click the **WriteLine** activity in the **Else** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```vb  
    "Your guess is too high."  
    ```  
  
     <span data-ttu-id="efb81-153">Aşağıdaki örnek, tamamlanan iş akışı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="efb81-153">The following example illustrates the completed workflow.</span></span>  
  
     <span data-ttu-id="efb81-154">![Sıralı iş akışı tamamlandı](../../../docs/framework/windows-workflow-foundation/media/wfsequentialgettingstartedtutorialcomplete.JPG "WFSequentialGettingStartedTutorialComplete")</span><span class="sxs-lookup"><span data-stu-id="efb81-154">![Completed Sequential Workflow](../../../docs/framework/windows-workflow-foundation/media/wfsequentialgettingstartedtutorialcomplete.JPG "WFSequentialGettingStartedTutorialComplete")</span></span>  
  
### <a name="to-build-the-workflow"></a><span data-ttu-id="efb81-155">İş akışı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="efb81-155">To build the workflow</span></span>  
  
1.  <span data-ttu-id="efb81-156">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="efb81-156">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="efb81-157">İş akışını çalıştırmak yönergeler Lütfen görmek için sonraki konuyu [nasıl yapılır: bir iş akışını çalıştırma](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="efb81-157">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span></span> <span data-ttu-id="efb81-158">Zaten tamamladıysanız [nasıl yapılır: bir iş akışını çalıştırma](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) adım farklı bir iş akışı stil ile ve çalıştırmak bu adımı sıralı iş akışını kullanarak istediğiniz, için İleri atlayabilirsiniz [oluşturmak veuygulamayıçalıştırmakiçin](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication)bölümünü [nasıl yapılır: bir iş akışını çalıştırma](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="efb81-158">If you have already completed the [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the sequential workflow from this step, skip ahead to the [To build and run the application](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efb81-159">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="efb81-159">See Also</span></span>  
 <xref:System.Activities.Statements.Flowchart>  
 <xref:System.Activities.Statements.FlowDecision>  
 [<span data-ttu-id="efb81-160">Windows Workflow Foundation programlama</span><span class="sxs-lookup"><span data-stu-id="efb81-160">Windows Workflow Foundation Programming</span></span>](../../../docs/framework/windows-workflow-foundation/programming.md)  
 [<span data-ttu-id="efb81-161">İş akışları tasarlama</span><span class="sxs-lookup"><span data-stu-id="efb81-161">Designing Workflows</span></span>](../../../docs/framework/windows-workflow-foundation/designing-workflows.md)  
 [<span data-ttu-id="efb81-162">Başlangıç Öğreticisi</span><span class="sxs-lookup"><span data-stu-id="efb81-162">Getting Started Tutorial</span></span>](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [<span data-ttu-id="efb81-163">Nasıl yapılır: bir etkinlik oluşturmak</span><span class="sxs-lookup"><span data-stu-id="efb81-163">How to: Create an Activity</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)  
 [<span data-ttu-id="efb81-164">Nasıl yapılır: bir iş akışını çalıştırma</span><span class="sxs-lookup"><span data-stu-id="efb81-164">How to: Run a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)
