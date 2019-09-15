---
title: 'Nasıl yapılır: Akış Çizelgesi İş Akışı Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 185d7aea-68a6-4bd8-adde-45050f33170a
ms.openlocfilehash: 0faf4d77b1ea2881ba8e029d544f2e42cf552349
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989681"
---
# <a name="how-to-create-a-flowchart-workflow"></a><span data-ttu-id="80e34-102">Nasıl yapılır: Akış Çizelgesi İş Akışı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="80e34-102">How to: Create a Flowchart Workflow</span></span>
<span data-ttu-id="80e34-103">İş akışları, yerleşik etkinliklerin yanı sıra özel etkinliklerden de oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="80e34-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="80e34-104">Bu konu, <xref:System.Activities.Statements.Flowchart> etkinlik gibi yerleşik etkinlikleri ve önceki [nasıl yapılacağı özel etkinlikleri kullanan bir iş akışı oluşturma ile ilgili adımları izleyerek yapılır: Etkinlik](how-to-create-an-activity.md) konusu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="80e34-104">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Flowchart> activity, and the custom activities from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="80e34-105">İş akışı, sayıyı tahmin eden bir oyunu modelleyen.</span><span class="sxs-lookup"><span data-stu-id="80e34-105">The workflow models a number guessing game.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="80e34-106">Başlangıç öğreticisindeki her konu, önceki konulara bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="80e34-106">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="80e34-107">Bu konuyu tamamlayabilmeniz için öncelikle [şunları yapmanız gerekir: Etkinlik](how-to-create-an-activity.md)oluşturun.</span><span class="sxs-lookup"><span data-stu-id="80e34-107">To complete this topic, you must first complete [How to: Create an Activity](how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="80e34-108">Öğreticinin tamamlanmış bir sürümünü indirmek için, bkz. [Windows Workflow Foundation (WF45)-Başlangıç Öğreticisi](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="80e34-108">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-workflow"></a><span data-ttu-id="80e34-109">İş akışını oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="80e34-109">To create the workflow</span></span>  
  
1. <span data-ttu-id="80e34-110">**Çözüm Gezgini** 'de **NumberGuessWorkflowActivities** öğesine sağ tıklayın ve **Ekle**, **Yeni öğe**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="80e34-110">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>  
  
2. <span data-ttu-id="80e34-111">**Yüklü**, **ortak öğeler** düğümünde **iş akışı**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="80e34-111">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="80e34-112">**Iş akışı** listesinden **etkinlik** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="80e34-112">Select **Activity** from the **Workflow** list.</span></span>  
  
3. <span data-ttu-id="80e34-113">Ad `FlowchartNumberGuessWorkflow` kutusuna yazın ve **Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="80e34-113">Type `FlowchartNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>  
  
4. <span data-ttu-id="80e34-114">**Araç çubuğu** ' nın **akış çizelgesi** ' nden bir **akış çizelgesi** etkinliği sürükleyin ve iş akışı tasarım yüzeyinde **buraya bırakma etkinliği** etiketini bırakın.</span><span class="sxs-lookup"><span data-stu-id="80e34-114">Drag a **Flowchart** activity from the **Flowchart** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="80e34-115">İş akışı değişkenlerini ve bağımsız değişkenleri oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="80e34-115">To create the workflow variables and arguments</span></span>  
  
1. <span data-ttu-id="80e34-116">Henüz görüntülenmiyorsa, iş akışını tasarımcıda göstermek için **Çözüm Gezgini** Içinde **FlowchartNumberGuessWorkflow. xaml** öğesine çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="80e34-116">Double-click **FlowchartNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>  
  
2. <span data-ttu-id="80e34-117">**Bağımsız değişkenler** bölmesini göstermek için iş akışı Tasarımcısı ' nın sol alt tarafındaki **bağımsız değişkenler** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="80e34-117">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
3. <span data-ttu-id="80e34-118">**Bağımsız değişken Oluştur**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="80e34-118">Click **Create Argument**.</span></span>  
  
4. <span data-ttu-id="80e34-119">Ad `MaxNumber` kutusuna yazın , **Yön** açılan listesinden **'** i seçin, **bağımsız değişken türü** açılan listesinden **Int32** ' i seçin ve ardından bağımsız değişkeni kaydetmek için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="80e34-119">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
5. <span data-ttu-id="80e34-120">**Bağımsız değişken Oluştur**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="80e34-120">Click **Create Argument**.</span></span>  
  
6. <span data-ttu-id="80e34-121">Yeni `Turns` eklenen bağımsız değişkenin altında bulunan ad kutusuna yazın, Yön açılan listesinden Seç ' i seçin, bağımsız değişken türü açılan listesinden Int32 ' i seçin ve ardından ENTER tuşuna basın. `MaxNumber`</span><span class="sxs-lookup"><span data-stu-id="80e34-121">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
7. <span data-ttu-id="80e34-122">**Bağımsız değişkenler** bölmesini kapatmak için etkinlik tasarımcısının sol alt tarafındaki **bağımsız değişkenler** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="80e34-122">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
8. <span data-ttu-id="80e34-123">**Değişkenler** bölmesini göstermek için iş akışı Tasarımcısı ' nın sol alt tarafındaki **değişkenler** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="80e34-123">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>  
  
9. <span data-ttu-id="80e34-124">**Değişken Oluştur**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="80e34-124">Click **Create Variable**.</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="80e34-125">**Değişken Oluştur** kutusu görüntülenmiyorsa, iş akışı Tasarımcısı yüzeyinde <xref:System.Activities.Statements.Flowchart> etkinlik ' i tıklatarak seçin.</span><span class="sxs-lookup"><span data-stu-id="80e34-125">If no **Create Variable** box is displayed, click the <xref:System.Activities.Statements.Flowchart> activity on the workflow designer surface to select it.</span></span>  
  
10. <span data-ttu-id="80e34-126">Ad `Guess` kutusuna yazın , **değişken türü** açılır listesinden **Int32** ' i seçin ve ardından değişkeni kaydetmek için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="80e34-126">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
11. <span data-ttu-id="80e34-127">**Değişken Oluştur**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="80e34-127">Click **Create Variable**.</span></span>  
  
12. <span data-ttu-id="80e34-128">Ad `Target` kutusuna yazın , **değişken türü** açılır listesinden **Int32** ' i seçin ve ardından değişkeni kaydetmek için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="80e34-128">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
13. <span data-ttu-id="80e34-129">**Değişkenler** bölmesini kapatmak için etkinlik tasarımcısının sol alt tarafındaki **değişkenler** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="80e34-129">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>  
  
### <a name="to-add-the-workflow-activities"></a><span data-ttu-id="80e34-130">İş akışı etkinliklerini eklemek için</span><span class="sxs-lookup"><span data-stu-id="80e34-130">To add the workflow activities</span></span>  
  
1. <span data-ttu-id="80e34-131">**Araç kutusunun** **temel elemanlar** bölümünden bir **atama** etkinliği sürükleyin ve akış çizelgesinin en üstünde bulunan **Başlangıç** düğümünün üzerine gelin.</span><span class="sxs-lookup"><span data-stu-id="80e34-131">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and hover it over the **Start** node, which is at the top of the flowchart.</span></span> <span data-ttu-id="80e34-132">**Atama** etkinliği **Başlangıç** düğümünden üstündeyken, **Başlangıç** düğümü etrafında üç üçgen görünür.</span><span class="sxs-lookup"><span data-stu-id="80e34-132">When the **Assign** activity is over the **Start** node, three triangles will appear around the **Start** node.</span></span> <span data-ttu-id="80e34-133">**Ata** etkinliğini **Başlangıç** düğümünün doğrudan altındaki üçgende bırakın.</span><span class="sxs-lookup"><span data-stu-id="80e34-133">Drop the **Assign** activity on the triangle that is directly below the **Start** node.</span></span> <span data-ttu-id="80e34-134">Bu, iki öğeyi birbirine bağlar ve **atama** etkinliğini akış çizelgesinde ilk etkinlik olarak belirler.</span><span class="sxs-lookup"><span data-stu-id="80e34-134">This will link the two items together and designates the **Assign** activity as the first activity in the flowchart.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="80e34-135">Etkinlikler, iş akışındaki başlangıç etkinliği olarak, etkinlik etkinliklerini başlangıç düğümüne el ile bağlayarak da belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="80e34-135">Activities can also be indicated as the starting activity in the workflow by manually linking them activity to the start node.</span></span> <span data-ttu-id="80e34-136">Bunu yapmak için, fareyi **Başlangıç** düğümünün üzerine getirin, fare **Başlangıç** düğümünün üzerindeyken görüntülenen dikdörtgenlerden birine tıklayın ve bağlama satırı ' nı istenen etkinliğe sürükleyin ve görüntülenen dikdörtgenlerden birine bırakın.</span><span class="sxs-lookup"><span data-stu-id="80e34-136">To do this, hover the mouse over the **Start** node, click one of the rectangles that appear when the mouse is over the **Start** node, and drag the connecting line down to the desired activity and drop it on one of the rectangles that appear.</span></span> <span data-ttu-id="80e34-137">Ayrıca, bir etkinliği sağ tıklayıp **başlangıç düğümü olarak ayarla**' yı seçerek başlangıç etkinliği olarak da belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80e34-137">You can also designate an activity as the starting activity by right-clicking the it and choosing **Set as Start Node**.</span></span>  
  
2. <span data-ttu-id="80e34-138">Buraya `Target` yazın veya bir  **C# ifade girin** veya bir **vb ifadesi girin** .</span><span class="sxs-lookup"><span data-stu-id="80e34-138">Type `Target` into the **To** box and the following expression into the **Enter a C# Expression** or **Enter a VB expression** box.</span></span>  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    > <span data-ttu-id="80e34-139">**Araç kutusu** penceresi görüntülenmiyorsa, **Görünüm** menüsünden **araç kutusu** ' nu seçin.</span><span class="sxs-lookup"><span data-stu-id="80e34-139">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
3. <span data-ttu-id="80e34-140">**Araç kutusu**'Nun **NumberGuessWorkflowActivities** bölümünden bir **istem** etkinliğini sürükleyin, önceki adımdan **atama** etkinliğinin altına bırakın ve **istem** etkinliğini **ata** etkinliğine bağlayın.</span><span class="sxs-lookup"><span data-stu-id="80e34-140">Drag a **Prompt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox**, drop it below the **Assign** activity from the previous step, and connect the **Prompt** activity to the **Assign** activity.</span></span> <span data-ttu-id="80e34-141">İki etkinliği bağlamak için üç yol vardır.</span><span class="sxs-lookup"><span data-stu-id="80e34-141">There are three ways to connect the two activities.</span></span> <span data-ttu-id="80e34-142">İlk yöntem, iş akışı üzerinde **istem** etkinliğini bıraktığınızda bunları birbirine bağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="80e34-142">The first way is to connect them as you drop the **Prompt** activity on the workflow.</span></span> <span data-ttu-id="80e34-143">**İstem** etkinliğini iş akışına sürüklerken, **ata** etkinliğinin üzerine gelin ve **Prompt** etkinliği **ata** etkinliğinin üzerindeyken görüntülenen dört üçgenden birine bırakın.</span><span class="sxs-lookup"><span data-stu-id="80e34-143">As you are dragging the **Prompt** activity to the workflow, hover it over the **Assign** activity and drop it onto one of the four triangles that appear when the **Prompt** activity is over the **Assign** activity.</span></span> <span data-ttu-id="80e34-144">İkinci yol, **Prompt** etkinliğinin istenen konumdaki iş akışına düşürülme yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="80e34-144">The second way is to drop the **Prompt** activity onto the workflow at the desired location.</span></span> <span data-ttu-id="80e34-145">Ardından, fareyi **ata** etkinliğinin üzerine getirin ve **komut istemi** etkinliğine aşağı doğru görünen dikdörtgenlerden birini sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="80e34-145">Then, hover the mouse over the **Assign** activity and drag one of the rectangles that appears down to the **Prompt** activity.</span></span> <span data-ttu-id="80e34-146">**Ata** etkinliğinin bağlantı çizgisinin, **istem** etkinliğinin dikdörtgenlerinin birine bağlanmasını sağlamak için fareyi sürükleyin, sonra fare düğmesini bırakın.</span><span class="sxs-lookup"><span data-stu-id="80e34-146">Drag the mouse so that the connecting line from the **Assign** activity connects to one of the rectangles of the **Prompt** activity, and then release the mouse button.</span></span> <span data-ttu-id="80e34-147">Üçüncü yol, **araç kutusu**'ndan **istem** etkinliğini sürüklemek yerine, iş akışı tasarım yüzeyindeki konumundan sürükledikten sonra **atama** etkinliğinin üzerine getirdiğinizde ve bunu bir ' dan birine bırakarak görüntülenen üçgenler.</span><span class="sxs-lookup"><span data-stu-id="80e34-147">The third way is very similar to the first way, except that instead of dragging the **Prompt** activity from the **Toolbox**, you drag it from its location on the workflow design surface, hover it over the **Assign** activity, and drop it onto one of the triangles that appears.</span></span>  
  
4. <span data-ttu-id="80e34-148">**İstem** etkinliğinin **Özellikler penceresinde** , tırnak işareti **adı** Özellik değeri `"EnterGuess"` kutusuna tırnak işareti ekleme yazın.</span><span class="sxs-lookup"><span data-stu-id="80e34-148">In the **Properties Window** for the **Prompt** activity, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box.</span></span> <span data-ttu-id="80e34-149">Sonuç `Guess` özelliği değeri kutusuna yazın ve **metin** özellik kutusuna aşağıdaki ifadeyi yazın.</span><span class="sxs-lookup"><span data-stu-id="80e34-149">Type `Guess` into the **Result** property value box, and type the following expression into the **Text** property box.</span></span>  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    > <span data-ttu-id="80e34-150">**Özellikler penceresi** görüntülenmiyorsa, **Görünüm** menüsünden **Özellikler penceresi** ' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="80e34-150">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
5. <span data-ttu-id="80e34-151">**Araç kutusunun** **temel elemanlar** bölümünden bir **atama** etkinliği sürükleyin ve bu eylemi, önceki adımda açıklanan yöntemlerden birini kullanarak bağlayın, böylece **istem** etkinliğinin altında olur.</span><span class="sxs-lookup"><span data-stu-id="80e34-151">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and connect it using one of the methods described in the previous step so that it is below the **Prompt** activity.</span></span>  
  
6. <span data-ttu-id="80e34-152">To `Turns` kutusuna ve `Turns + 1` **bir C# ifade girin** veya bir **vb ifadesi girin** kutusuna yazın.</span><span class="sxs-lookup"><span data-stu-id="80e34-152">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression**  or **Enter a VB expression** box.</span></span>  
  
7. <span data-ttu-id="80e34-153">**Araç kutusunun** **akış çizelgesi** bölümünden bir **flowkararı** sürükleyin ve **assign** etkinliğinin altına bağlayın.</span><span class="sxs-lookup"><span data-stu-id="80e34-153">Drag a **FlowDecision** from the **Flowchart** section of the **Toolbox** and connect it below the **Assign** activity.</span></span> <span data-ttu-id="80e34-154">**Özellikler penceresinde**, **koşul** özelliği değeri kutusuna aşağıdaki ifadeyi yazın.</span><span class="sxs-lookup"><span data-stu-id="80e34-154">In the **Properties Window**, type the following expression into the **Condition** property value box.</span></span>  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
8. <span data-ttu-id="80e34-155">**Araç kutusu** 'ndan başka bir **flowkarar** etkinliği sürükleyin ve ilk birinin altına bırakın.</span><span class="sxs-lookup"><span data-stu-id="80e34-155">Drag another **FlowDecision** activity from the **Toolbox** and drop it below the first one.</span></span> <span data-ttu-id="80e34-156">En üstteki **Flowkararı** etkinliğinde **false** etiketli dikdörtgenden ikinci **flowkarar** etkinliğinin en üstündeki dikdörtgene sürükleyerek iki etkinliği bağlayın.</span><span class="sxs-lookup"><span data-stu-id="80e34-156">Connect the two activities by dragging from the rectangle that is labeled **False** on the top **FlowDecision** activity to the rectangle at the top of the second **FlowDecision** activity.</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="80e34-157">**Flowkararı**üzerinde **doğru** ve **yanlış** etiketlerini görmüyorsanız, fareyi **flowkararı**üzerine getirin.</span><span class="sxs-lookup"><span data-stu-id="80e34-157">If you do not see the **True** and **False** labels on the **FlowDecision**, hover the mouse over the **FlowDecision**.</span></span>  
  
9. <span data-ttu-id="80e34-158">İkinci **Flowkarar** etkinliğine tıklayarak seçin.</span><span class="sxs-lookup"><span data-stu-id="80e34-158">Click the second **FlowDecision** activity to select it.</span></span> <span data-ttu-id="80e34-159">**Özellikler penceresinde**, **koşul** özelliği değeri kutusuna aşağıdaki ifadeyi yazın.</span><span class="sxs-lookup"><span data-stu-id="80e34-159">In the **Properties Window**, type the following expression into the **Condition** property value box.</span></span>  
  
    ```text
    Guess < Target
    ```  
  
10. <span data-ttu-id="80e34-160">İki **WriteLine** etkinliğini **araç kutusunun** **temel öğeler** bölümünden sürükleyin ve iki **flowkarar** etkinliklerinin altında yan yana olacak şekilde bırakın.</span><span class="sxs-lookup"><span data-stu-id="80e34-160">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that they are side by side below the two **FlowDecision** activities.</span></span> <span data-ttu-id="80e34-161">En alttaki **Flowkarar** etkinliğinin **doğru** eylemini en soldaki **WriteLine** etkinliğine ve **false** eylemini en sağdaki **WriteLine** etkinliğine bağlayın.</span><span class="sxs-lookup"><span data-stu-id="80e34-161">Connect the **True** action of the bottom **FlowDecision** activity to the leftmost **WriteLine** activity, and the **False** action to the rightmost **WriteLine** activity.</span></span>  
  
11. <span data-ttu-id="80e34-162">En soldaki **WriteLine** etkinliğine tıklayarak bunu seçin ve **Özellikler penceresindeki** **metin** özelliği değeri kutusuna aşağıdaki ifadeyi yazın.</span><span class="sxs-lookup"><span data-stu-id="80e34-162">Click the leftmost **WriteLine** activity to select it, and type the following expression into the **Text** property value box in the **Properties Window**.</span></span>  
  
    ```text
    "Your guess is too low."  
    ```  
  
12. <span data-ttu-id="80e34-163">**WriteLine** 'ı Yukarıdaki **istem** etkinliğinin sol tarafına bağlayın.</span><span class="sxs-lookup"><span data-stu-id="80e34-163">Connect the **WriteLine** to the left side of the **Prompt** activity that is above it.</span></span>  
  
13. <span data-ttu-id="80e34-164">Bunu seçmek için en sağdaki **WriteLine** etkinliğine tıklayın ve **Özellikler penceresindeki** **metin** özelliği değeri kutusuna aşağıdaki ifadeyi yazın.</span><span class="sxs-lookup"><span data-stu-id="80e34-164">Click the rightmost **WriteLine** activity to select it, and type the following expression into the **Text** property value box in the **Properties Window**.</span></span>  
  
    ```text
    "Your guess is too high."  
    ```  
  
14. <span data-ttu-id="80e34-165">**WriteLine** etkinliğini Yukarıdaki **istem** etkinliğinin sağ tarafına bağlayın.</span><span class="sxs-lookup"><span data-stu-id="80e34-165">Connect the **WriteLine** activity to the right side of the **Prompt** activity above it.</span></span>  
  
     <span data-ttu-id="80e34-166">Aşağıdaki örnekte tamamlanan iş akışı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="80e34-166">The following example illustrates the completed workflow.</span></span>  
  
     ![Tamamlanmış bir Windows Workflow Foundation akış çizelgesi gösteren diyagram.](./media/how-to-create-a-flowchart-workflow/completed-windows-workflow-flowchart.png)  
  
### <a name="to-build-the-workflow"></a><span data-ttu-id="80e34-168">İş akışını derlemek için</span><span class="sxs-lookup"><span data-stu-id="80e34-168">To build the workflow</span></span>  
  
1. <span data-ttu-id="80e34-169">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="80e34-169">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="80e34-170">İş akışının nasıl çalıştırılacağı hakkında yönergeler için lütfen sonraki konuya [bakın: Bir Iş akışı](how-to-run-a-workflow.md)çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="80e34-170">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span> <span data-ttu-id="80e34-171">' Nin [nasıl yapılacağını zaten tamamladıysanız: Farklı bir iş](how-to-run-a-workflow.md) akışı stili ile bir iş akışı adımı çalıştırın ve bu adımda akış çizelgesi iş akışını [kullanarak çalıştırmak istiyorsanız,](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) [nasıl yapılır: Bir Iş akışı](how-to-run-a-workflow.md)çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="80e34-171">If you have already completed the [How to: Run a Workflow](how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the flowchart workflow from this step, skip ahead to the [To build and run the application](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80e34-172">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="80e34-172">See also</span></span>

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [<span data-ttu-id="80e34-173">Windows Workflow Foundation Programlama</span><span class="sxs-lookup"><span data-stu-id="80e34-173">Windows Workflow Foundation Programming</span></span>](programming.md)
- [<span data-ttu-id="80e34-174">İş Akışları Tasarlama</span><span class="sxs-lookup"><span data-stu-id="80e34-174">Designing Workflows</span></span>](designing-workflows.md)
- [<span data-ttu-id="80e34-175">Başlangıç Öğreticisi</span><span class="sxs-lookup"><span data-stu-id="80e34-175">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="80e34-176">Nasıl yapılır: Etkinlik oluşturma</span><span class="sxs-lookup"><span data-stu-id="80e34-176">How to: Create an Activity</span></span>](how-to-create-an-activity.md)
- [<span data-ttu-id="80e34-177">Nasıl yapılır: Iş akışı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="80e34-177">How to: Run a Workflow</span></span>](how-to-run-a-workflow.md)
