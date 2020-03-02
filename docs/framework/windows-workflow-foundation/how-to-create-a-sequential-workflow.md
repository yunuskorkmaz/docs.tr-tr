---
title: 'Nasıl yapılır: Akış Çizelgesi İş Akışı Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5280e816-ae17-48c4-8de0-a1e6895dd8f0
ms.openlocfilehash: 61e3f01b1259536ff15d71526e91aef42069722e
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989699"
---
# <a name="how-to-create-a-sequential-workflow"></a><span data-ttu-id="c6b40-102">Nasıl yapılır: Akış Çizelgesi İş Akışı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c6b40-102">How to: Create a Sequential Workflow</span></span>

<span data-ttu-id="c6b40-103">İş akışları, yerleşik etkinliklerin yanı sıra özel etkinliklerden de oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="c6b40-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="c6b40-104">Bu konu, <xref:System.Activities.Statements.Sequence> etkinliği gibi yerleşik etkinlikleri ve önceki [özel etkinlikleri kullanan bir iş akışı oluşturma adımları ile nasıl yapılır: Etkinlik](how-to-create-an-activity.md) konu başlığı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c6b40-104">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Sequence> activity, and the custom activities from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="c6b40-105">İş akışı, sayıyı tahmin eden bir oyunu modelleyen.</span><span class="sxs-lookup"><span data-stu-id="c6b40-105">The workflow models a number guessing game.</span></span>

> [!NOTE]
> <span data-ttu-id="c6b40-106">Başlangıç öğreticisindeki her konu, önceki konulara bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="c6b40-106">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="c6b40-107">Bu konuyu tamamlayabilmeniz için öncelikle [nasıl yapılacağını tamamlamalısınız: Etkinlik](how-to-create-an-activity.md)oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c6b40-107">To complete this topic, you must first complete [How to: Create an Activity](how-to-create-an-activity.md).</span></span>

> [!NOTE]
> <span data-ttu-id="c6b40-108">Öğreticinin tamamlanmış bir sürümünü indirmek için, bkz. [Windows Workflow Foundation (WF45)-Başlangıç Öğreticisi](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="c6b40-108">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>

## <a name="to-create-the-workflow"></a><span data-ttu-id="c6b40-109">İş akışını oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="c6b40-109">To create the workflow</span></span>

1. <span data-ttu-id="c6b40-110">**Çözüm Gezgini** 'de **NumberGuessWorkflowActivities** öğesine sağ tıklayın ve **Ekle**, **Yeni öğe**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="c6b40-110">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>

2. <span data-ttu-id="c6b40-111">**Yüklü**, **ortak öğeler** düğümünde **iş akışı**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="c6b40-111">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="c6b40-112">**Iş akışı** listesinden **etkinlik** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="c6b40-112">Select **Activity** from the **Workflow** list.</span></span>

3. <span data-ttu-id="c6b40-113">**Ad** kutusuna `SequentialNumberGuessWorkflow` yazın ve **Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c6b40-113">Type `SequentialNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>

4. <span data-ttu-id="c6b40-114">**Araç kutusunun** **Denetim akışı** bölümünden bir **sıra** etkinliğini sürükleyin ve iş akışı tasarım yüzeyinde **buraya bırakma etkinliği** etiketini bırakın.</span><span class="sxs-lookup"><span data-stu-id="c6b40-114">Drag a **Sequence** activity from the **Control Flow** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>

## <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="c6b40-115">İş akışı değişkenlerini ve bağımsız değişkenleri oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="c6b40-115">To create the workflow variables and arguments</span></span>

1. <span data-ttu-id="c6b40-116">Henüz görüntülenmiyorsa, iş akışını tasarımcıda göstermek için **Çözüm Gezgini** içinde **SequentialNumberGuessWorkflow. xaml** öğesine çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c6b40-116">Double-click **SequentialNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>

2. <span data-ttu-id="c6b40-117">**Bağımsız değişkenler** bölmesini göstermek için iş akışı Tasarımcısı ' nın sol alt tarafındaki **bağımsız değişkenler** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c6b40-117">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>

3. <span data-ttu-id="c6b40-118">**Bağımsız değişken Oluştur**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c6b40-118">Click **Create Argument**.</span></span>

4. <span data-ttu-id="c6b40-119">**Ad** kutusuna `MaxNumber` yazın, **Yön** açılan listesinden Seç ' i seçin, **bağımsız değişken türü** açılan listesinden **Int32** ' **i seçin ve** sonra bağımsız değişkeni kaydetmek için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c6b40-119">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>

5. <span data-ttu-id="c6b40-120">**Bağımsız değişken Oluştur**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c6b40-120">Click **Create Argument**.</span></span>

6. <span data-ttu-id="c6b40-121">Yeni eklenen `MaxNumber` bağımsız değişkeninin altında bulunan **ad** kutusuna `Turns` yazın, **Yön** açılan **listesinden Seç ' i seçin,** **bağımsız değişken türü** AÇıLAN listesinden **Int32** ' yi seçin ve ardından ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c6b40-121">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>

7. <span data-ttu-id="c6b40-122">**Bağımsız değişkenler** bölmesini kapatmak için etkinlik tasarımcısının sol alt tarafındaki **bağımsız değişkenler** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c6b40-122">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>

8. <span data-ttu-id="c6b40-123">**Değişkenler** bölmesini göstermek için iş akışı Tasarımcısı ' nın sol alt tarafındaki **değişkenler** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c6b40-123">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>

9. <span data-ttu-id="c6b40-124">**Değişken Oluştur**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c6b40-124">Click **Create Variable**.</span></span>

    > [!TIP]
    > <span data-ttu-id="c6b40-125">**Değişken Oluştur** kutusu görüntülenmiyorsa, iş akışı Tasarımcısı yüzeyinde **dizi** etkinliğine tıklayarak seçin.</span><span class="sxs-lookup"><span data-stu-id="c6b40-125">If no **Create Variable** box is displayed, click the **Sequence** activity on the workflow designer surface to select it.</span></span>

10. <span data-ttu-id="c6b40-126">**Ad** kutusuna `Guess` yazın, **değişken türü** açılır listesinden **Int32** ' i SEÇIN ve ardından değişkeni kaydetmek için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c6b40-126">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>

11. <span data-ttu-id="c6b40-127">**Değişken Oluştur**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c6b40-127">Click **Create Variable**.</span></span>

12. <span data-ttu-id="c6b40-128">**Ad** kutusuna `Target` yazın, **değişken türü** açılır listesinden **Int32** ' i SEÇIN ve ardından değişkeni kaydetmek için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c6b40-128">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>

13. <span data-ttu-id="c6b40-129">**Değişkenler** bölmesini kapatmak için etkinlik tasarımcısının sol alt tarafındaki **değişkenler** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c6b40-129">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>

## <a name="to-add-the-workflow-activities"></a><span data-ttu-id="c6b40-130">İş akışı etkinliklerini eklemek için</span><span class="sxs-lookup"><span data-stu-id="c6b40-130">To add the workflow activities</span></span>

1. <span data-ttu-id="c6b40-131">**Araç kutusu** ' nu **temel elemanlar** bölümünden bir **atama** etkinliği sürükleyin ve **dizi** etkinliğine bırakın.</span><span class="sxs-lookup"><span data-stu-id="c6b40-131">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Sequence** activity.</span></span> <span data-ttu-id="c6b40-132">**Bir C# ifade gırın** veya bir **vb ifadesi girin** kutusuna **to** kutusuna `Target` ve aşağıdaki ifadeyi yazın.</span><span class="sxs-lookup"><span data-stu-id="c6b40-132">Type `Target` into the **To** box and the following expression into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>

    ```vb
    New System.Random().Next(1, MaxNumber + 1)
    ```

    ```csharp
    new System.Random().Next(1, MaxNumber + 1)
    ```

    > [!TIP]
    > <span data-ttu-id="c6b40-133">**Araç kutusu** penceresi görüntülenmiyorsa, **Görünüm** menüsünden **araç kutusu** ' nu seçin.</span><span class="sxs-lookup"><span data-stu-id="c6b40-133">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>

2. <span data-ttu-id="c6b40-134">**Araç kutusunun** **Denetim akışı** bölümünden bir **DoWhile** etkinliği sürükleyin ve **ata** etkinliğinin altında olması için iş akışına bırakın.</span><span class="sxs-lookup"><span data-stu-id="c6b40-134">Drag a **DoWhile** activity from the **Control Flow** section of the **Toolbox** and drop it on the workflow so that it is below the **Assign** activity.</span></span>

3. <span data-ttu-id="c6b40-135">**DoWhile** etkinliğinin **koşul** özelliği değeri kutusuna aşağıdaki ifadeyi yazın.</span><span class="sxs-lookup"><span data-stu-id="c6b40-135">Type the following expression into the **DoWhile** activity’s **Condition** property value box.</span></span>

    ```vb
    Guess <> Target
    ```

    ```csharp
    Guess != Target
    ```

     <span data-ttu-id="c6b40-136"><xref:System.Activities.Statements.DoWhile> bir etkinlik, alt etkinliklerini yürütür ve sonra <xref:System.Activities.Statements.DoWhile.Condition%2A>değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="c6b40-136">A <xref:System.Activities.Statements.DoWhile> activity executes its child activities and then evaluates its <xref:System.Activities.Statements.DoWhile.Condition%2A>.</span></span> <span data-ttu-id="c6b40-137"><xref:System.Activities.Statements.DoWhile.Condition%2A> `True`değerlendirilirse <xref:System.Activities.Statements.DoWhile> etkinlikler yeniden yürütülür.</span><span class="sxs-lookup"><span data-stu-id="c6b40-137">If the <xref:System.Activities.Statements.DoWhile.Condition%2A> evaluates to `True`, then the activities in the <xref:System.Activities.Statements.DoWhile> execute again.</span></span> <span data-ttu-id="c6b40-138">Bu örnekte, kullanıcının tahmini değerlendirilir ve <xref:System.Activities.Statements.DoWhile> tahmin doğru olana kadar devam eder.</span><span class="sxs-lookup"><span data-stu-id="c6b40-138">In this example, the user’s guess is evaluated and the <xref:System.Activities.Statements.DoWhile> continues until the guess is correct.</span></span>

4. <span data-ttu-id="c6b40-139">**Araç kutusunun** **NumberGuessWorkflowActivities** bölümünden bir **istem** etkinliğini sürükleyin ve önceki adımda **DoWhile** etkinliğinde bırakın.</span><span class="sxs-lookup"><span data-stu-id="c6b40-139">Drag a **Prompt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **DoWhile** activity from the previous step.</span></span>

5. <span data-ttu-id="c6b40-140">**Özellikler penceresinde**, **komut Istemi** etkinliğinin **BookmarkName** özellik değeri kutusuna tırnak işareti dahil `"EnterGuess"` yazın.</span><span class="sxs-lookup"><span data-stu-id="c6b40-140">In the **Properties Window**, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box for the **Prompt** activity.</span></span> <span data-ttu-id="c6b40-141">**Sonuç** özelliği değeri kutusuna `Guess` yazın ve **metin** özellik kutusuna aşağıdaki ifadeyi yazın.</span><span class="sxs-lookup"><span data-stu-id="c6b40-141">Type `Guess` into the **Result** property value box, and type the following expression into the **Text** property box.</span></span>

    ```vb
    "Please enter a number between 1 and " & MaxNumber
    ```

    ```csharp
    "Please enter a number between 1 and " + MaxNumber
    ```

    > [!TIP]
    > <span data-ttu-id="c6b40-142">**Özellikler penceresi** görüntülenmiyorsa, **Görünüm** menüsünden **Özellikler penceresi** ' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="c6b40-142">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>

6. <span data-ttu-id="c6b40-143">**Araç kutusu** ' nın **temel öğeler** bölümünden bir **atama** etkinliği sürükleyin ve **istem** etkinliğini takip etmek için **DoWhile** etkinliğine bırakın.</span><span class="sxs-lookup"><span data-stu-id="c6b40-143">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it in the **DoWhile** activity so that it follows the **Prompt** activity.</span></span>

    > [!NOTE]
    > <span data-ttu-id="c6b40-144">**Ata** etkinliğini bıraktığınızda, iş akışı tasarımcısının hem **istem** etkinliğini hem de yeni eklenen **atama** etkinliğini içerecek şekilde bir **dizi** etkinliği nasıl otomatik olarak eklediğini aklınızda bulundurın.</span><span class="sxs-lookup"><span data-stu-id="c6b40-144">When you drop the **Assign** activity, note how the workflow designer automatically adds a **Sequence** activity to contain both the **Prompt** activity and the newly added **Assign** activity.</span></span>

7. <span data-ttu-id="c6b40-145">**To** kutusuna `Turns` yazın ve  **C# BIR ifade girin** veya bir **vb ifadesi girin** kutusuna `Turns + 1`.</span><span class="sxs-lookup"><span data-stu-id="c6b40-145">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>

8. <span data-ttu-id="c6b40-146">**Araç kutusunun** **Denetim akışı** bölümünden bir **IF** etkinliği sürükleyin ve yeni eklenen **atama** etkinliğinin ardından onu **sıra** etkinliğine bırakın.</span><span class="sxs-lookup"><span data-stu-id="c6b40-146">Drag an **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Sequence** activity so that it follows the newly added **Assign** activity.</span></span>

9. <span data-ttu-id="c6b40-147">**IF** etkinliğinin **koşul** özelliği değeri kutusuna aşağıdaki ifadeyi yazın.</span><span class="sxs-lookup"><span data-stu-id="c6b40-147">Type the following expression into the **If** activity’s **Condition** property value box.</span></span>

    ```vb
    Guess <> Target
    ```

    ```csharp
    Guess != Target
    ```

10. <span data-ttu-id="c6b40-148">**Araç kutusunun** **Denetim akışı** bölümünden başka bir etkinlik **varsa** , **sonra** da ilk **IF** etkinliğinin bölümüne sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="c6b40-148">Drag another **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Then** section of the first **If** activity.</span></span>

11. <span data-ttu-id="c6b40-149">Yeni **eklenen etkinliğin** **koşul** özelliği değeri kutusuna aşağıdaki ifadeyi yazın.</span><span class="sxs-lookup"><span data-stu-id="c6b40-149">Type the following expression into the newly added **If** activity’s **Condition** property value box.</span></span>

    ```text
    Guess < Target
    ```

12. <span data-ttu-id="c6b40-150">**Araç kutusu** ' **nu** **temel elemanlar** bölümünden iki **WriteLine** etkinliği sürükleyin ve bir birinin yeni eklenen **IF** etkinliğinin bölümünde ve diğeri ise **Else** bölümünde olması için bırakın.</span><span class="sxs-lookup"><span data-stu-id="c6b40-150">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that one is in the **Then** section of the newly added **If** activity, and one is in the **Else** section.</span></span>

13. <span data-ttu-id="c6b40-151">**Daha sonra** seçmek Için bölümünde **WriteLine** etkinliğine tıklayın ve **metin** özelliği değeri kutusuna aşağıdaki ifadeyi yazın.</span><span class="sxs-lookup"><span data-stu-id="c6b40-151">Click the **WriteLine** activity in the **Then** section to select it, and type the following expression into the **Text** property value box.</span></span>

    ```text
    "Your guess is too low."
    ```

14. <span data-ttu-id="c6b40-152">Bunu seçmek için **Else** bölümünde **WriteLine** etkinliğine tıklayın ve **metin** özelliği değeri kutusuna aşağıdaki ifadeyi yazın.</span><span class="sxs-lookup"><span data-stu-id="c6b40-152">Click the **WriteLine** activity in the **Else** section to select it, and type the following expression into the **Text** property value box.</span></span>

    ```text
    "Your guess is too high."
    ```

     <span data-ttu-id="c6b40-153">Aşağıdaki örnek tamamlanan iş akışını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="c6b40-153">The following example illustrates the completed workflow:</span></span>

     ![Tamamlanmış sıralı iş akışını gösteren ekran görüntüsü.](./media/how-to-create-a-sequential-workflow/complete-sequential-workflow.jpg)

## <a name="to-build-the-workflow"></a><span data-ttu-id="c6b40-155">İş akışını derlemek için</span><span class="sxs-lookup"><span data-stu-id="c6b40-155">To build the workflow</span></span>

1. <span data-ttu-id="c6b40-156">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="c6b40-156">Press CTRL+SHIFT+B to build the solution.</span></span>

     <span data-ttu-id="c6b40-157">İş akışının nasıl çalıştırılacağı hakkında yönergeler için bkz. bir sonraki konu, [nasıl yapılır: ](how-to-run-a-workflow.md)Iş akışı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c6b40-157">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span> <span data-ttu-id="c6b40-158">[Şu anda tamamladıysanız: Farklı bir iş akışı stiliyle Iş akışı](how-to-run-a-workflow.md) adımı çalıştırın ve bu adımdaki sıralı iş akışını [kullanarak çalıştırmak istiyorsanız,](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) [nasıl yapılır: Iş akışı çalıştırın](how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="c6b40-158">If you have already completed the [How to: Run a Workflow](how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the sequential workflow from this step, skip ahead to the [To build and run the application](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c6b40-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6b40-159">See also</span></span>

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [<span data-ttu-id="c6b40-160">Windows Workflow Foundation Programlama</span><span class="sxs-lookup"><span data-stu-id="c6b40-160">Windows Workflow Foundation Programming</span></span>](programming.md)
- [<span data-ttu-id="c6b40-161">İş Akışları Tasarlama</span><span class="sxs-lookup"><span data-stu-id="c6b40-161">Designing Workflows</span></span>](designing-workflows.md)
- [<span data-ttu-id="c6b40-162">Başlangıç Öğreticisi</span><span class="sxs-lookup"><span data-stu-id="c6b40-162">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- <span data-ttu-id="c6b40-163">[Nasıl yapılır: Etkinlik](how-to-create-an-activity.md) oluşturma</span><span class="sxs-lookup"><span data-stu-id="c6b40-163">[How to: Create an Activity](how-to-create-an-activity.md)</span></span>
- [<span data-ttu-id="c6b40-164">Nasıl yapılır: Iş akışı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="c6b40-164">How to: Run a Workflow</span></span>](how-to-run-a-workflow.md)
