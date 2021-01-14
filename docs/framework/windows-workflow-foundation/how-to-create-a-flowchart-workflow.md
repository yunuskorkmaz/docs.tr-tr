---
title: 'Nasıl yapılır: Akış Çizelgesi İş Akışı Oluşturma'
description: Bu makalede, önceki makaledeki yerleşik etkinlikleri ve özel etkinlikleri kullanan bir iş akışı oluşturma açıklanır.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 185d7aea-68a6-4bd8-adde-45050f33170a
ms.openlocfilehash: eb30a3a21ffc4cffe64d2f5d0bc741728f1ea87d
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98190487"
---
# <a name="how-to-create-a-flowchart-workflow"></a><span data-ttu-id="4ceab-103">Nasıl yapılır: Akış Çizelgesi İş Akışı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="4ceab-103">How to: Create a Flowchart Workflow</span></span>

<span data-ttu-id="4ceab-104">İş akışları, yerleşik etkinliklerin yanı sıra özel etkinliklerden de oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="4ceab-104">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="4ceab-105">Bu konu, etkinlik gibi yerleşik etkinlikleri <xref:System.Activities.Statements.Flowchart> ve önceki [nasıl yapılır: etkinlik oluşturma](how-to-create-an-activity.md) konusunun özel etkinliklerini kullanan bir iş akışı oluşturmaya yönelik adımları açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="4ceab-105">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Flowchart> activity, and the custom activities from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="4ceab-106">İş akışı, sayıyı tahmin eden bir oyunu modelleyen.</span><span class="sxs-lookup"><span data-stu-id="4ceab-106">The workflow models a number guessing game.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4ceab-107">Başlangıç öğreticisindeki her konu, önceki konulara bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="4ceab-107">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="4ceab-108">Bu konuyu tamamlayabilmeniz için öncelikle [nasıl yapılır: etkinlik oluşturma](how-to-create-an-activity.md)' yı tamamlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="4ceab-108">To complete this topic, you must first complete [How to: Create an Activity](how-to-create-an-activity.md).</span></span>  
  
### <a name="to-create-the-workflow"></a><span data-ttu-id="4ceab-109">İş akışını oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="4ceab-109">To create the workflow</span></span>  
  
1. <span data-ttu-id="4ceab-110">**Çözüm Gezgini** 'de **NumberGuessWorkflowActivities** öğesine sağ tıklayın ve **Ekle**, **Yeni öğe**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="4ceab-110">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>  
  
2. <span data-ttu-id="4ceab-111">**Yüklü**, **ortak öğeler** düğümünde **iş akışı**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="4ceab-111">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="4ceab-112">**Iş akışı** listesinden **etkinlik** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="4ceab-112">Select **Activity** from the **Workflow** list.</span></span>  
  
3. <span data-ttu-id="4ceab-113">`FlowchartNumberGuessWorkflow` **Ad** kutusuna yazın ve **Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4ceab-113">Type `FlowchartNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>  
  
4. <span data-ttu-id="4ceab-114">**Araç çubuğu** ' nın **akış çizelgesi** ' nden bir **akış çizelgesi** etkinliği sürükleyin ve iş akışı tasarım yüzeyinde **buraya bırakma etkinliği** etiketini bırakın.</span><span class="sxs-lookup"><span data-stu-id="4ceab-114">Drag a **Flowchart** activity from the **Flowchart** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="4ceab-115">İş akışı değişkenlerini ve bağımsız değişkenleri oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="4ceab-115">To create the workflow variables and arguments</span></span>  
  
1. <span data-ttu-id="4ceab-116">Henüz görüntülenmiyorsa, iş akışını tasarımcıda göstermek için **Çözüm Gezgini** Içinde **FlowchartNumberGuessWorkflow. xaml** öğesine çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4ceab-116">Double-click **FlowchartNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>  
  
2. <span data-ttu-id="4ceab-117">**Bağımsız değişkenler** bölmesini göstermek için iş akışı Tasarımcısı ' nın sol alt tarafındaki **bağımsız değişkenler** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4ceab-117">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
3. <span data-ttu-id="4ceab-118">**Bağımsız değişken Oluştur**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4ceab-118">Click **Create Argument**.</span></span>  
  
4. <span data-ttu-id="4ceab-119">`MaxNumber` **Ad** kutusuna yazın, **Yön** açılan listesinden **'** i seçin, **bağımsız değişken türü** açılan listesinden **ıNT32** ' i seçin ve ardından bağımsız değişkeni kaydetmek için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="4ceab-119">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
5. <span data-ttu-id="4ceab-120">**Bağımsız değişken Oluştur**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4ceab-120">Click **Create Argument**.</span></span>  
  
6. <span data-ttu-id="4ceab-121">`Turns`Yeni eklenen bağımsız değişkenin altında bulunan **ad** kutusuna yazın `MaxNumber` , **Yön** açılan listesinden Seç  ' i seçin, **bağımsız değişken türü** açılan listesinden **Int32** ' i seçin ve ardından ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="4ceab-121">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
7. <span data-ttu-id="4ceab-122">**Bağımsız değişkenler** bölmesini kapatmak için etkinlik tasarımcısının sol alt tarafındaki **bağımsız değişkenler** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4ceab-122">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
8. <span data-ttu-id="4ceab-123">**Değişkenler** bölmesini göstermek için iş akışı Tasarımcısı ' nın sol alt tarafındaki **değişkenler** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4ceab-123">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>  
  
9. <span data-ttu-id="4ceab-124">**Değişken Oluştur**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4ceab-124">Click **Create Variable**.</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="4ceab-125">**Değişken Oluştur** kutusu görüntülenmiyorsa, <xref:System.Activities.Statements.Flowchart> iş akışı Tasarımcısı yüzeyinde etkinlik ' i tıklatarak seçin.</span><span class="sxs-lookup"><span data-stu-id="4ceab-125">If no **Create Variable** box is displayed, click the <xref:System.Activities.Statements.Flowchart> activity on the workflow designer surface to select it.</span></span>  
  
10. <span data-ttu-id="4ceab-126">`Guess` **Ad** kutusuna yazın, **değişken türü** açılır listesinden **Int32** ' i seçin ve ardından değişkeni kaydetmek için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="4ceab-126">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
11. <span data-ttu-id="4ceab-127">**Değişken Oluştur**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4ceab-127">Click **Create Variable**.</span></span>  
  
12. <span data-ttu-id="4ceab-128">`Target` **Ad** kutusuna yazın, **değişken türü** açılır listesinden **Int32** ' i seçin ve ardından değişkeni kaydetmek için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="4ceab-128">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
13. <span data-ttu-id="4ceab-129">**Değişkenler** bölmesini kapatmak için etkinlik tasarımcısının sol alt tarafındaki **değişkenler** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4ceab-129">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>  
  
### <a name="to-add-the-workflow-activities"></a><span data-ttu-id="4ceab-130">İş akışı etkinliklerini eklemek için</span><span class="sxs-lookup"><span data-stu-id="4ceab-130">To add the workflow activities</span></span>  
  
1. <span data-ttu-id="4ceab-131">**Araç kutusunun** **temel elemanlar** bölümünden bir **atama** etkinliği sürükleyin ve akış çizelgesinin en üstünde bulunan **Başlangıç** düğümünün üzerine gelin.</span><span class="sxs-lookup"><span data-stu-id="4ceab-131">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and hover it over the **Start** node, which is at the top of the flowchart.</span></span> <span data-ttu-id="4ceab-132">**Atama** etkinliği **Başlangıç** düğümünden üstündeyken, **Başlangıç** düğümü etrafında üç üçgen görünür.</span><span class="sxs-lookup"><span data-stu-id="4ceab-132">When the **Assign** activity is over the **Start** node, three triangles will appear around the **Start** node.</span></span> <span data-ttu-id="4ceab-133">**Ata** etkinliğini **Başlangıç** düğümünün doğrudan altındaki üçgende bırakın.</span><span class="sxs-lookup"><span data-stu-id="4ceab-133">Drop the **Assign** activity on the triangle that is directly below the **Start** node.</span></span> <span data-ttu-id="4ceab-134">Bu, iki öğeyi birbirine bağlar ve **atama** etkinliğini akış çizelgesinde ilk etkinlik olarak belirler.</span><span class="sxs-lookup"><span data-stu-id="4ceab-134">This will link the two items together and designates the **Assign** activity as the first activity in the flowchart.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="4ceab-135">Etkinlikler, iş akışındaki başlangıç etkinliği olarak, etkinlik etkinliklerini başlangıç düğümüne el ile bağlayarak da belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="4ceab-135">Activities can also be indicated as the starting activity in the workflow by manually linking them activity to the start node.</span></span> <span data-ttu-id="4ceab-136">Bunu yapmak için, fareyi **Başlangıç** düğümünün üzerine getirin, fare **Başlangıç** düğümünün üzerindeyken görüntülenen dikdörtgenlerden birine tıklayın ve bağlama satırı ' nı istenen etkinliğe sürükleyin ve görüntülenen dikdörtgenlerden birine bırakın.</span><span class="sxs-lookup"><span data-stu-id="4ceab-136">To do this, hover the mouse over the **Start** node, click one of the rectangles that appear when the mouse is over the **Start** node, and drag the connecting line down to the desired activity and drop it on one of the rectangles that appear.</span></span> <span data-ttu-id="4ceab-137">Ayrıca, bir etkinliği sağ tıklayıp **başlangıç düğümü olarak ayarla**' yı seçerek başlangıç etkinliği olarak da belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ceab-137">You can also designate an activity as the starting activity by right-clicking the it and choosing **Set as Start Node**.</span></span>  
  
2. <span data-ttu-id="4ceab-138">`Target` **Bir C# ifadesi girin** veya bir **vb ifadesi girin** kutusuna **to** kutusuna ve aşağıdaki ifadeye yazın.</span><span class="sxs-lookup"><span data-stu-id="4ceab-138">Type `Target` into the **To** box and the following expression into the **Enter a C# Expression** or **Enter a VB expression** box.</span></span>  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    > <span data-ttu-id="4ceab-139">**Araç kutusu** penceresi görüntülenmiyorsa, **Görünüm** menüsünden **araç kutusu** ' nu seçin.</span><span class="sxs-lookup"><span data-stu-id="4ceab-139">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
3. <span data-ttu-id="4ceab-140">**Araç kutusu**'Nun **NumberGuessWorkflowActivities** bölümünden bir **istem** etkinliğini sürükleyin, önceki adımdan **atama** etkinliğinin altına bırakın ve **istem** etkinliğini **ata** etkinliğine bağlayın.</span><span class="sxs-lookup"><span data-stu-id="4ceab-140">Drag a **Prompt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox**, drop it below the **Assign** activity from the previous step, and connect the **Prompt** activity to the **Assign** activity.</span></span> <span data-ttu-id="4ceab-141">İki etkinliği bağlamak için üç yol vardır.</span><span class="sxs-lookup"><span data-stu-id="4ceab-141">There are three ways to connect the two activities.</span></span> <span data-ttu-id="4ceab-142">İlk yöntem, iş akışı üzerinde **istem** etkinliğini bıraktığınızda bunları birbirine bağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4ceab-142">The first way is to connect them as you drop the **Prompt** activity on the workflow.</span></span> <span data-ttu-id="4ceab-143">**İstem** etkinliğini iş akışına sürüklerken, **ata** etkinliğinin üzerine gelin ve **Prompt** etkinliği **ata** etkinliğinin üzerindeyken görüntülenen dört üçgenden birine bırakın.</span><span class="sxs-lookup"><span data-stu-id="4ceab-143">As you are dragging the **Prompt** activity to the workflow, hover it over the **Assign** activity and drop it onto one of the four triangles that appear when the **Prompt** activity is over the **Assign** activity.</span></span> <span data-ttu-id="4ceab-144">İkinci yol, **Prompt** etkinliğinin istenen konumdaki iş akışına düşürülme yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="4ceab-144">The second way is to drop the **Prompt** activity onto the workflow at the desired location.</span></span> <span data-ttu-id="4ceab-145">Ardından, fareyi **ata** etkinliğinin üzerine getirin ve **komut istemi** etkinliğine aşağı doğru görünen dikdörtgenlerden birini sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="4ceab-145">Then, hover the mouse over the **Assign** activity and drag one of the rectangles that appears down to the **Prompt** activity.</span></span> <span data-ttu-id="4ceab-146">**Ata** etkinliğinin bağlantı çizgisinin, **istem** etkinliğinin dikdörtgenlerinin birine bağlanmasını sağlamak için fareyi sürükleyin, sonra fare düğmesini bırakın.</span><span class="sxs-lookup"><span data-stu-id="4ceab-146">Drag the mouse so that the connecting line from the **Assign** activity connects to one of the rectangles of the **Prompt** activity, and then release the mouse button.</span></span> <span data-ttu-id="4ceab-147">Üçüncü yol, **araç kutusu**'ndan **istem** etkinliğini sürüklemek yerine, iş akışı tasarım yüzeyindeki konumundan Sürükleyeceğinize, bu dosyayı **ata** etkinliğinin üzerine getirdiğinizde ve görüntülenen üçgenlerden birine bırakmalısınız.</span><span class="sxs-lookup"><span data-stu-id="4ceab-147">The third way is very similar to the first way, except that instead of dragging the **Prompt** activity from the **Toolbox**, you drag it from its location on the workflow design surface, hover it over the **Assign** activity, and drop it onto one of the triangles that appears.</span></span>  
  
4. <span data-ttu-id="4ceab-148">**İstem** etkinliğinin **Özellikler penceresinde** , `"EnterGuess"` tırnak işareti **adı** Özellik değeri kutusuna tırnak işareti ekleme yazın.</span><span class="sxs-lookup"><span data-stu-id="4ceab-148">In the **Properties Window** for the **Prompt** activity, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box.</span></span> <span data-ttu-id="4ceab-149">`Guess` **Sonuç** özelliği değeri kutusuna yazın ve **metin** özellik kutusuna aşağıdaki ifadeyi yazın.</span><span class="sxs-lookup"><span data-stu-id="4ceab-149">Type `Guess` into the **Result** property value box, and type the following expression into the **Text** property box.</span></span>  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    > <span data-ttu-id="4ceab-150">**Özellikler penceresi** görüntülenmiyorsa, **Görünüm** menüsünden **Özellikler penceresi** ' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="4ceab-150">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
5. <span data-ttu-id="4ceab-151">**Araç kutusunun** **temel elemanlar** bölümünden bir **atama** etkinliği sürükleyin ve bu eylemi, önceki adımda açıklanan yöntemlerden birini kullanarak bağlayın, böylece **istem** etkinliğinin altında olur.</span><span class="sxs-lookup"><span data-stu-id="4ceab-151">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and connect it using one of the methods described in the previous step so that it is below the **Prompt** activity.</span></span>  
  
6. <span data-ttu-id="4ceab-152">`Turns` **To** kutusuna ve `Turns + 1` **bir C# IFADESI girin** veya **bir vb ifadesi kutusu girin** .</span><span class="sxs-lookup"><span data-stu-id="4ceab-152">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression**  or **Enter a VB expression** box.</span></span>  
  
7. <span data-ttu-id="4ceab-153">**Araç kutusunun** **akış çizelgesi** bölümünden bir **flowkararı** sürükleyin ve **assign** etkinliğinin altına bağlayın.</span><span class="sxs-lookup"><span data-stu-id="4ceab-153">Drag a **FlowDecision** from the **Flowchart** section of the **Toolbox** and connect it below the **Assign** activity.</span></span> <span data-ttu-id="4ceab-154">**Özellikler penceresinde**, **koşul** özelliği değeri kutusuna aşağıdaki ifadeyi yazın.</span><span class="sxs-lookup"><span data-stu-id="4ceab-154">In the **Properties Window**, type the following expression into the **Condition** property value box.</span></span>  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
8. <span data-ttu-id="4ceab-155">**Araç kutusu** 'ndan başka bir **flowkarar** etkinliği sürükleyin ve ilk birinin altına bırakın.</span><span class="sxs-lookup"><span data-stu-id="4ceab-155">Drag another **FlowDecision** activity from the **Toolbox** and drop it below the first one.</span></span> <span data-ttu-id="4ceab-156">En üstteki **Flowkararı** etkinliğinde **false** etiketli dikdörtgenden ikinci **flowkarar** etkinliğinin en üstündeki dikdörtgene sürükleyerek iki etkinliği bağlayın.</span><span class="sxs-lookup"><span data-stu-id="4ceab-156">Connect the two activities by dragging from the rectangle that is labeled **False** on the top **FlowDecision** activity to the rectangle at the top of the second **FlowDecision** activity.</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="4ceab-157">**Flowkararı** üzerinde **doğru** ve **yanlış** etiketlerini görmüyorsanız, fareyi **flowkararı** üzerine getirin.</span><span class="sxs-lookup"><span data-stu-id="4ceab-157">If you do not see the **True** and **False** labels on the **FlowDecision**, hover the mouse over the **FlowDecision**.</span></span>  
  
9. <span data-ttu-id="4ceab-158">İkinci **Flowkarar** etkinliğine tıklayarak seçin.</span><span class="sxs-lookup"><span data-stu-id="4ceab-158">Click the second **FlowDecision** activity to select it.</span></span> <span data-ttu-id="4ceab-159">**Özellikler penceresinde**, **koşul** özelliği değeri kutusuna aşağıdaki ifadeyi yazın.</span><span class="sxs-lookup"><span data-stu-id="4ceab-159">In the **Properties Window**, type the following expression into the **Condition** property value box.</span></span>  
  
    ```text
    Guess < Target
    ```  
  
10. <span data-ttu-id="4ceab-160">İki **WriteLine** etkinliğini **araç kutusunun** **temel öğeler** bölümünden sürükleyin ve iki **flowkarar** etkinliklerinin altında yan yana olacak şekilde bırakın.</span><span class="sxs-lookup"><span data-stu-id="4ceab-160">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that they are side by side below the two **FlowDecision** activities.</span></span> <span data-ttu-id="4ceab-161">En alttaki **Flowkarar** etkinliğinin **doğru** eylemini en soldaki **WriteLine** etkinliğine ve **false** eylemini en sağdaki **WriteLine** etkinliğine bağlayın.</span><span class="sxs-lookup"><span data-stu-id="4ceab-161">Connect the **True** action of the bottom **FlowDecision** activity to the leftmost **WriteLine** activity, and the **False** action to the rightmost **WriteLine** activity.</span></span>  
  
11. <span data-ttu-id="4ceab-162">En soldaki **WriteLine** etkinliğine tıklayarak bunu seçin ve **Özellikler penceresindeki** **metin** özelliği değeri kutusuna aşağıdaki ifadeyi yazın.</span><span class="sxs-lookup"><span data-stu-id="4ceab-162">Click the leftmost **WriteLine** activity to select it, and type the following expression into the **Text** property value box in the **Properties Window**.</span></span>  
  
    ```text
    "Your guess is too low."  
    ```  
  
12. <span data-ttu-id="4ceab-163">**WriteLine** 'ı Yukarıdaki **istem** etkinliğinin sol tarafına bağlayın.</span><span class="sxs-lookup"><span data-stu-id="4ceab-163">Connect the **WriteLine** to the left side of the **Prompt** activity that is above it.</span></span>  
  
13. <span data-ttu-id="4ceab-164">Bunu seçmek için en sağdaki **WriteLine** etkinliğine tıklayın ve **Özellikler penceresindeki** **metin** özelliği değeri kutusuna aşağıdaki ifadeyi yazın.</span><span class="sxs-lookup"><span data-stu-id="4ceab-164">Click the rightmost **WriteLine** activity to select it, and type the following expression into the **Text** property value box in the **Properties Window**.</span></span>  
  
    ```text
    "Your guess is too high."  
    ```  
  
14. <span data-ttu-id="4ceab-165">**WriteLine** etkinliğini Yukarıdaki **istem** etkinliğinin sağ tarafına bağlayın.</span><span class="sxs-lookup"><span data-stu-id="4ceab-165">Connect the **WriteLine** activity to the right side of the **Prompt** activity above it.</span></span>  
  
     <span data-ttu-id="4ceab-166">Aşağıdaki örnekte tamamlanan iş akışı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4ceab-166">The following example illustrates the completed workflow.</span></span>  
  
     ![Tamamlanmış bir Windows Workflow Foundation akış çizelgesi gösteren diyagram.](./media/how-to-create-a-flowchart-workflow/completed-windows-workflow-flowchart.png)  
  
### <a name="to-build-the-workflow"></a><span data-ttu-id="4ceab-168">İş akışını derlemek için</span><span class="sxs-lookup"><span data-stu-id="4ceab-168">To build the workflow</span></span>  
  
1. <span data-ttu-id="4ceab-169">Çözümü derlemek için CTRL+SHIFT+B'ye basın.</span><span class="sxs-lookup"><span data-stu-id="4ceab-169">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="4ceab-170">İş akışının nasıl çalıştırılacağı hakkında yönergeler için, bkz. [nasıl yapılır: Iş akışını çalıştırma](how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="4ceab-170">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span> <span data-ttu-id="4ceab-171">[Nasıl yapılır: bir](how-to-run-a-workflow.md) iş akışı adımını farklı bir iş akışı ile çalıştırma ve bu adımda akış çizelgesi iş akışını kullanarak çalıştırmak istediğinizde, nasıl [yapılır: iş akışı çalıştırma](how-to-run-a-workflow.md)konusunun [Uygulama bölümünü derlemek ve çalıştırmak için](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) ' a atlayın.</span><span class="sxs-lookup"><span data-stu-id="4ceab-171">If you have already completed the [How to: Run a Workflow](how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the flowchart workflow from this step, skip ahead to the [To build and run the application](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ceab-172">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4ceab-172">See also</span></span>

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [<span data-ttu-id="4ceab-173">Windows Workflow Foundation Programlama</span><span class="sxs-lookup"><span data-stu-id="4ceab-173">Windows Workflow Foundation Programming</span></span>](programming.md)
- [<span data-ttu-id="4ceab-174">İş Akışları Tasarlama</span><span class="sxs-lookup"><span data-stu-id="4ceab-174">Designing Workflows</span></span>](designing-workflows.md)
- [<span data-ttu-id="4ceab-175">Başlangıç Öğreticisi</span><span class="sxs-lookup"><span data-stu-id="4ceab-175">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="4ceab-176">Nasıl yapılır: Etkinlik Oluşturma</span><span class="sxs-lookup"><span data-stu-id="4ceab-176">How to: Create an Activity</span></span>](how-to-create-an-activity.md)
- [<span data-ttu-id="4ceab-177">Nasıl yapılır: İş Akışı Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="4ceab-177">How to: Run a Workflow</span></span>](how-to-run-a-workflow.md)
