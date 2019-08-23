---
title: 'Nasıl yapılır: Akış Çizelgesi İş Akışı Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5280e816-ae17-48c4-8de0-a1e6895dd8f0
ms.openlocfilehash: 9c9746305b251e7d48ee34c2cccd5afae174ee90
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962363"
---
# <a name="how-to-create-a-sequential-workflow"></a><span data-ttu-id="903ba-102">Nasıl yapılır: Akış Çizelgesi İş Akışı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="903ba-102">How to: Create a Sequential Workflow</span></span>
<span data-ttu-id="903ba-103">İş akışları, yerleşik etkinliklerin yanı sıra özel etkinliklerden de oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="903ba-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="903ba-104">Bu konu, <xref:System.Activities.Statements.Sequence> etkinlik gibi yerleşik etkinlikleri ve önceki [nasıl yapılacağı özel etkinlikleri kullanan bir iş akışı oluşturma ile ilgili adımları izleyerek yapılır: Etkinlik](how-to-create-an-activity.md) konusu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="903ba-104">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Sequence> activity, and the custom activities from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="903ba-105">İş akışı, sayıyı tahmin eden bir oyunu modelleyen.</span><span class="sxs-lookup"><span data-stu-id="903ba-105">The workflow models a number guessing game.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="903ba-106">Başlangıç öğreticisindeki her konu, önceki konulara bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="903ba-106">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="903ba-107">Bu konuyu tamamlayabilmeniz için öncelikle [şunları yapmanız gerekir: Etkinlik](how-to-create-an-activity.md)oluşturun.</span><span class="sxs-lookup"><span data-stu-id="903ba-107">To complete this topic, you must first complete [How to: Create an Activity](how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="903ba-108">Öğreticinin tamamlanmış bir sürümünü indirmek için, bkz. [Windows Workflow Foundation (WF45)-Başlangıç Öğreticisi](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="903ba-108">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="to-create-the-workflow"></a><span data-ttu-id="903ba-109">İş akışını oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="903ba-109">To create the workflow</span></span>  
  
1. <span data-ttu-id="903ba-110">**Çözüm Gezgini** 'de **NumberGuessWorkflowActivities** öğesine sağ tıklayın ve **Ekle**, **Yeni öğe**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="903ba-110">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>  
  
2. <span data-ttu-id="903ba-111">**Yüklü**, **ortak öğeler** düğümünde **iş akışı**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="903ba-111">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="903ba-112">**Iş akışı** listesinden **etkinlik** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="903ba-112">Select **Activity** from the **Workflow** list.</span></span>  
  
3. <span data-ttu-id="903ba-113">Ad `SequentialNumberGuessWorkflow` kutusuna yazın ve **Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="903ba-113">Type `SequentialNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>  
  
4. <span data-ttu-id="903ba-114">**Araç kutusunun** **Denetim akışı** bölümünden bir **sıra** etkinliğini sürükleyin ve iş akışı tasarım yüzeyinde **buraya bırakma etkinliği** etiketini bırakın.</span><span class="sxs-lookup"><span data-stu-id="903ba-114">Drag a **Sequence** activity from the **Control Flow** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>  
  
## <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="903ba-115">İş akışı değişkenlerini ve bağımsız değişkenleri oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="903ba-115">To create the workflow variables and arguments</span></span>  
  
1. <span data-ttu-id="903ba-116">Henüz görüntülenmiyorsa, iş akışını tasarımcıda göstermek için **Çözüm Gezgini** içinde **SequentialNumberGuessWorkflow. xaml** öğesine çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="903ba-116">Double-click **SequentialNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>  
  
2. <span data-ttu-id="903ba-117">**Bağımsız değişkenler** bölmesini göstermek için iş akışı Tasarımcısı ' nın sol alt tarafındaki **bağımsız değişkenler** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="903ba-117">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
3. <span data-ttu-id="903ba-118">**Bağımsız değişken Oluştur**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="903ba-118">Click **Create Argument**.</span></span>  
  
4. <span data-ttu-id="903ba-119">Ad `MaxNumber` kutusuna yazın , **Yön** açılan listesinden **'** i seçin, **bağımsız değişken türü** açılan listesinden **Int32** ' i seçin ve ardından bağımsız değişkeni kaydetmek için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="903ba-119">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
5. <span data-ttu-id="903ba-120">**Bağımsız değişken Oluştur**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="903ba-120">Click **Create Argument**.</span></span>  
  
6. <span data-ttu-id="903ba-121">Yeni `Turns` eklenen bağımsız`MaxNumber` değişkenin altında bulunan ad kutusuna yazın, Yön açılan listesinden Seç ' i seçin, **bağımsız değişken türü** açılan listesinden Int32 ' i seçin ve ardından ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="903ba-121">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
7. <span data-ttu-id="903ba-122">**Bağımsız değişkenler** bölmesini kapatmak için etkinlik tasarımcısının sol alt tarafındaki **bağımsız değişkenler** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="903ba-122">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
8. <span data-ttu-id="903ba-123">**Değişkenler** bölmesini göstermek için iş akışı Tasarımcısı ' nın sol alt tarafındaki **değişkenler** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="903ba-123">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>  
  
9. <span data-ttu-id="903ba-124">**Değişken Oluştur**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="903ba-124">Click **Create Variable**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="903ba-125">**Değişken Oluştur** kutusu görüntülenmiyorsa, iş akışı Tasarımcısı yüzeyinde **dizi** etkinliğine tıklayarak seçin.</span><span class="sxs-lookup"><span data-stu-id="903ba-125">If no **Create Variable** box is displayed, click the **Sequence** activity on the workflow designer surface to select it.</span></span>  
  
10. <span data-ttu-id="903ba-126">Ad `Guess` kutusuna yazın , **değişken türü** açılır listesinden **Int32** ' i seçin ve ardından değişkeni kaydetmek için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="903ba-126">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
11. <span data-ttu-id="903ba-127">**Değişken Oluştur**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="903ba-127">Click **Create Variable**.</span></span>  
  
12. <span data-ttu-id="903ba-128">Ad `Target` kutusuna yazın , **değişken türü** açılır listesinden **Int32** ' i seçin ve ardından değişkeni kaydetmek için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="903ba-128">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
13. <span data-ttu-id="903ba-129">**Değişkenler** bölmesini kapatmak için etkinlik tasarımcısının sol alt tarafındaki **değişkenler** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="903ba-129">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>  
  
## <a name="to-add-the-workflow-activities"></a><span data-ttu-id="903ba-130">İş akışı etkinliklerini eklemek için</span><span class="sxs-lookup"><span data-stu-id="903ba-130">To add the workflow activities</span></span>  
  
1. <span data-ttu-id="903ba-131">**Araç kutusu** ' nu **temel elemanlar** bölümünden bir **atama** etkinliği sürükleyin ve **dizi** etkinliğine bırakın.</span><span class="sxs-lookup"><span data-stu-id="903ba-131">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Sequence** activity.</span></span> <span data-ttu-id="903ba-132">Buraya `Target` yazın veya bir  **C# ifade girin** veya bir **vb ifadesi girin** .</span><span class="sxs-lookup"><span data-stu-id="903ba-132">Type `Target` into the **To** box and the following expression into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="903ba-133">**Araç kutusu** penceresi görüntülenmiyorsa, **Görünüm** menüsünden **araç kutusu** ' nu seçin.</span><span class="sxs-lookup"><span data-stu-id="903ba-133">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
2. <span data-ttu-id="903ba-134">**Araç kutusunun** **Denetim akışı** bölümünden bir **DoWhile** etkinliği sürükleyin ve **ata** etkinliğinin altında olması için iş akışına bırakın.</span><span class="sxs-lookup"><span data-stu-id="903ba-134">Drag a **DoWhile** activity from the **Control Flow** section of the **Toolbox** and drop it on the workflow so that it is below the **Assign** activity.</span></span>  
  
3. <span data-ttu-id="903ba-135">**DoWhile** etkinliğinin **koşul** özelliği değeri kutusuna aşağıdaki ifadeyi yazın.</span><span class="sxs-lookup"><span data-stu-id="903ba-135">Type the following expression into the **DoWhile** activity’s **Condition** property value box.</span></span>  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
     <span data-ttu-id="903ba-136">Bir <xref:System.Activities.Statements.DoWhile> etkinlik, alt etkinliklerini yürütür ve sonra <xref:System.Activities.Statements.DoWhile.Condition%2A>değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="903ba-136">A <xref:System.Activities.Statements.DoWhile> activity executes its child activities and then evaluates its <xref:System.Activities.Statements.DoWhile.Condition%2A>.</span></span> <span data-ttu-id="903ba-137"><xref:System.Activities.Statements.DoWhile.Condition%2A> Olarak <xref:System.Activities.Statements.DoWhile> değerlendirilirse, içindeki etkinlikler yeniden yürütün. `True`</span><span class="sxs-lookup"><span data-stu-id="903ba-137">If the <xref:System.Activities.Statements.DoWhile.Condition%2A> evaluates to `True`, then the activities in the <xref:System.Activities.Statements.DoWhile> execute again.</span></span> <span data-ttu-id="903ba-138">Bu örnekte, kullanıcının tahmini değerlendirilir ve <xref:System.Activities.Statements.DoWhile> tahmin doğru olana kadar devam eder.</span><span class="sxs-lookup"><span data-stu-id="903ba-138">In this example, the user’s guess is evaluated and the <xref:System.Activities.Statements.DoWhile> continues until the guess is correct.</span></span>  
  
4. <span data-ttu-id="903ba-139">**Araç kutusunun** **NumberGuessWorkflowActivities** bölümünden bir **istem** etkinliğini sürükleyin ve önceki adımda **DoWhile** etkinliğinde bırakın.</span><span class="sxs-lookup"><span data-stu-id="903ba-139">Drag a **Prompt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **DoWhile** activity from the previous step.</span></span>  
  
5. <span data-ttu-id="903ba-140">**Özellikler penceresinde**, **komut istemi** etkinliğinin `"EnterGuess"` **BookmarkName** Özellik değeri kutusuna tırnak işareti ekleme yazın.</span><span class="sxs-lookup"><span data-stu-id="903ba-140">In the **Properties Window**, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box for the **Prompt** activity.</span></span> <span data-ttu-id="903ba-141">Sonuç `Guess` özelliği değeri kutusuna yazın ve **metin** özellik kutusuna aşağıdaki ifadeyi yazın.</span><span class="sxs-lookup"><span data-stu-id="903ba-141">Type `Guess` into the **Result** property value box, and type the following expression into the **Text** property box.</span></span>  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="903ba-142">**Özellikler penceresi** görüntülenmiyorsa, **Görünüm** menüsünden **Özellikler penceresi** ' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="903ba-142">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
6. <span data-ttu-id="903ba-143">**Araç kutusu** ' nın **temel öğeler** bölümünden bir **atama** etkinliği sürükleyin ve **istem** etkinliğini takip etmek için **DoWhile** etkinliğine bırakın.</span><span class="sxs-lookup"><span data-stu-id="903ba-143">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it in the **DoWhile** activity so that it follows the **Prompt** activity.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="903ba-144">**Ata** etkinliğini bıraktığınızda, iş akışı tasarımcısının hem **istem** etkinliğini hem de yeni eklenen **atama** etkinliğini içerecek şekilde bir **dizi** etkinliği nasıl otomatik olarak eklediğini aklınızda bulundurın.</span><span class="sxs-lookup"><span data-stu-id="903ba-144">When you drop the **Assign** activity, note how the workflow designer automatically adds a **Sequence** activity to contain both the **Prompt** activity and the newly added **Assign** activity.</span></span>  
  
7. <span data-ttu-id="903ba-145">To `Turns` kutusuna ve `Turns + 1` **bir C# ifade girin** veya bir **vb ifadesi girin** kutusuna yazın.</span><span class="sxs-lookup"><span data-stu-id="903ba-145">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
8. <span data-ttu-id="903ba-146">**Araç kutusunun** **Denetim akışı** bölümünden bir **IF** etkinliği sürükleyin ve yeni eklenen **atama** etkinliğinin ardından onu **sıra** etkinliğine bırakın.</span><span class="sxs-lookup"><span data-stu-id="903ba-146">Drag an **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Sequence** activity so that it follows the newly added **Assign** activity.</span></span>  
  
9. <span data-ttu-id="903ba-147">**IF** etkinliğinin **koşul** özelliği değeri kutusuna aşağıdaki ifadeyi yazın.</span><span class="sxs-lookup"><span data-stu-id="903ba-147">Type the following expression into the **If** activity’s **Condition** property value box.</span></span>  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
10. <span data-ttu-id="903ba-148">**Araç kutusunun** **Denetim akışı** bölümünden başka bir etkinlik **varsa** , **sonra** da ilk **IF** etkinliğinin bölümüne sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="903ba-148">Drag another **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Then** section of the first **If** activity.</span></span>  
  
11. <span data-ttu-id="903ba-149">Yeni eklenen etkinliğin **koşul** özelliği değeri kutusuna aşağıdaki ifadeyi yazın.</span><span class="sxs-lookup"><span data-stu-id="903ba-149">Type the following expression into the newly added **If** activity’s **Condition** property value box.</span></span>  
  
    ```
    Guess < Target  
    ```  
  
12. <span data-ttu-id="903ba-150">**Araç kutusu** ' **nu** **temel elemanlar** bölümünden iki **WriteLine** etkinliği sürükleyin ve bir birinin yeni eklenen **IF** etkinliğinin bölümünde ve diğeri ise **Else** bölümünde olması için bırakın.</span><span class="sxs-lookup"><span data-stu-id="903ba-150">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that one is in the **Then** section of the newly added **If** activity, and one is in the **Else** section.</span></span>  
  
13. <span data-ttu-id="903ba-151">**Daha sonra** seçmek Için bölümünde **WriteLine** etkinliğine tıklayın ve **metin** özelliği değeri kutusuna aşağıdaki ifadeyi yazın.</span><span class="sxs-lookup"><span data-stu-id="903ba-151">Click the **WriteLine** activity in the **Then** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```text
    "Your guess is too low."  
    ```  
  
14. <span data-ttu-id="903ba-152">Bunu seçmek için **Else** bölümünde **WriteLine** etkinliğine tıklayın ve **metin** özelliği değeri kutusuna aşağıdaki ifadeyi yazın.</span><span class="sxs-lookup"><span data-stu-id="903ba-152">Click the **WriteLine** activity in the **Else** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```text
    "Your guess is too high."  
    ```  
  
     <span data-ttu-id="903ba-153">Aşağıdaki örnek tamamlanan iş akışını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="903ba-153">The following example illustrates the completed workflow:</span></span>  
  
     ![Tamamlanmış sıralı iş akışını gösteren ekran görüntüsü.](./media/how-to-create-a-sequential-workflow/complete-sequential-workflow.jpg)  
  
## <a name="to-build-the-workflow"></a><span data-ttu-id="903ba-155">İş akışını derlemek için</span><span class="sxs-lookup"><span data-stu-id="903ba-155">To build the workflow</span></span>  
  
1. <span data-ttu-id="903ba-156">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="903ba-156">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="903ba-157">İş akışının nasıl çalıştırılacağı hakkında yönergeler için lütfen sonraki konuya [bakın: Bir Iş akışı](how-to-run-a-workflow.md)çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="903ba-157">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span> <span data-ttu-id="903ba-158">' Nin [nasıl yapılacağını zaten tamamladıysanız: Farklı bir iş](how-to-run-a-workflow.md) akışı stili ile bir iş akışı adımı çalıştırın ve bu adımda [](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) [sıralı iş akışını kullanarak çalıştırmak istiyorsanız, nasıl yapılır: Bir Iş akışı](how-to-run-a-workflow.md)çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="903ba-158">If you have already completed the [How to: Run a Workflow](how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the sequential workflow from this step, skip ahead to the [To build and run the application](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="903ba-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="903ba-159">See also</span></span>

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [<span data-ttu-id="903ba-160">Windows Workflow Foundation Programlama</span><span class="sxs-lookup"><span data-stu-id="903ba-160">Windows Workflow Foundation Programming</span></span>](programming.md)
- [<span data-ttu-id="903ba-161">İş Akışları Tasarlama</span><span class="sxs-lookup"><span data-stu-id="903ba-161">Designing Workflows</span></span>](designing-workflows.md)
- [<span data-ttu-id="903ba-162">Başlangıç Öğreticisi</span><span class="sxs-lookup"><span data-stu-id="903ba-162">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="903ba-163">Nasıl yapılır: Etkinlik oluşturma</span><span class="sxs-lookup"><span data-stu-id="903ba-163">How to: Create an Activity</span></span>](how-to-create-an-activity.md)
- [<span data-ttu-id="903ba-164">Nasıl yapılır: Iş akışı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="903ba-164">How to: Run a Workflow</span></span>](how-to-run-a-workflow.md)
