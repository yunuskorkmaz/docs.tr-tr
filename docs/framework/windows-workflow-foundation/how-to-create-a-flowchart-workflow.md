---
title: "Nasıl yapılır: bir akış iş akışı oluşturma"
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
ms.assetid: 185d7aea-68a6-4bd8-adde-45050f33170a
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3df93a876522ccdc001bc3f6bc8c780bc80dc21b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-flowchart-workflow"></a><span data-ttu-id="d55eb-102">Nasıl yapılır: bir akış iş akışı oluşturma</span><span class="sxs-lookup"><span data-stu-id="d55eb-102">How to: Create a Flowchart Workflow</span></span>
<span data-ttu-id="d55eb-103">İş akışları yerleşik etkinliklerden yanı sıra özel etkinliklerden oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="d55eb-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="d55eb-104">Bu konudaki adımları hem yerleşik etkinlikler gibi kullanan bir iş akışı oluşturma aracılığıyla <xref:System.Activities.Statements.Flowchart> etkinliği ve önceki özel etkinlikler [nasıl yapılır: bir etkinlik oluşturmak](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) konu.</span><span class="sxs-lookup"><span data-stu-id="d55eb-104">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Flowchart> activity, and the custom activities from the previous [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="d55eb-105">Sayı tahmin eden oyun iş akışını modeller.</span><span class="sxs-lookup"><span data-stu-id="d55eb-105">The workflow models a number guessing game.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d55eb-106">Başlarken Öğreticisi her bir konuda önceki konularda bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="d55eb-106">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="d55eb-107">Bu konuda tamamlamak için önce tamamlamanız gereken [nasıl yapılır: bir etkinlik oluşturmak](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="d55eb-107">To complete this topic, you must first complete [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d55eb-108">Öğreticinin tamamlanmış bir sürümünü indirmek için bkz: [Windows Workflow Foundation (WF45) - başlangıç Öğreticisi](http://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="d55eb-108">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](http://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-workflow"></a><span data-ttu-id="d55eb-109">İş akışını oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d55eb-109">To create the workflow</span></span>  
  
1.  <span data-ttu-id="d55eb-110">Sağ **NumberGuessWorkflowActivities** içinde **Çözüm Gezgini** seçip **Ekle**, **yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="d55eb-110">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>  
  
2.  <span data-ttu-id="d55eb-111">İçinde **yüklü**, **ortak öğeler** düğümü, select **iş akışı**.</span><span class="sxs-lookup"><span data-stu-id="d55eb-111">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="d55eb-112">Seçin **etkinlik** gelen **iş akışı** listesi.</span><span class="sxs-lookup"><span data-stu-id="d55eb-112">Select **Activity** from the **Workflow** list.</span></span>  
  
3.  <span data-ttu-id="d55eb-113">Tür `FlowchartNumberGuessWorkflow` içine **adı** kutusuna ve tıklatın **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="d55eb-113">Type `FlowchartNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>  
  
4.  <span data-ttu-id="d55eb-114">Sürükleme bir **akış çizelgesi** etkinliğinden **akış çizelgesi** bölümünü **araç** ve üzerine bırakın **etkinliğini Drop burada** üzerindeki etiket İş akışı tasarım yüzeyi.</span><span class="sxs-lookup"><span data-stu-id="d55eb-114">Drag a **Flowchart** activity from the **Flowchart** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="d55eb-115">İş akışı değişkenleri ve bağımsız değişkenler oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d55eb-115">To create the workflow variables and arguments</span></span>  
  
1.  <span data-ttu-id="d55eb-116">Çift **FlowchartNumberGuessWorkflow.xaml** içinde **Çözüm Gezgini** zaten görüntülenmiyorsa, iş akışı Tasarımcısı'nda görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="d55eb-116">Double-click **FlowchartNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>  
  
2.  <span data-ttu-id="d55eb-117">Tıklatın **bağımsız değişkenleri** görüntülemek için iş akışı Tasarımcısı sol tarafındaki **bağımsız değişkenleri** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="d55eb-117">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
3.  <span data-ttu-id="d55eb-118">Tıklatın **bağımsız değişkeni oluşturma**.</span><span class="sxs-lookup"><span data-stu-id="d55eb-118">Click **Create Argument**.</span></span>  
  
4.  <span data-ttu-id="d55eb-119">Tür `MaxNumber` içine **adı** kutusunda **içinde** gelen **yönü** aşağı açılan listesinden, **Int32** gelen**Bağımsız değişken türü** aşağı açılan liste ve bağımsız değişkeni kaydetmek için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d55eb-119">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
5.  <span data-ttu-id="d55eb-120">Tıklatın **bağımsız değişkeni oluşturma**.</span><span class="sxs-lookup"><span data-stu-id="d55eb-120">Click **Create Argument**.</span></span>  
  
6.  <span data-ttu-id="d55eb-121">Tür `Turns` içine **adı** altında yeni eklenen kutusuna `MaxNumber` bağımsız değişkeni, select **çıkışı** gelen **yönü** aşağı açılan listesinden,  **Int32** gelen **bağımsız değişken türü** aşağı açılan liste ve ENTER tuşuna BASIN.</span><span class="sxs-lookup"><span data-stu-id="d55eb-121">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
7.  <span data-ttu-id="d55eb-122">Tıklatın **bağımsız değişkenleri** kapatmak için etkinlik Tasarımcısı sol tarafındaki **bağımsız değişkenleri** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="d55eb-122">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
8.  <span data-ttu-id="d55eb-123">Tıklatın **değişkenleri** görüntülemek için iş akışı Tasarımcısı sol tarafındaki **değişkenleri** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="d55eb-123">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>  
  
9. <span data-ttu-id="d55eb-124">Tıklatın **değişken oluşturma**.</span><span class="sxs-lookup"><span data-stu-id="d55eb-124">Click **Create Variable**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="d55eb-125">Yoksa **oluşturma değişken** kutusu görüntülenir, tıklatın <xref:System.Activities.Statements.Flowchart> seçmek için iş akışı Tasarımcısı yüzey üzerinde etkinlik.</span><span class="sxs-lookup"><span data-stu-id="d55eb-125">If no **Create Variable** box is displayed, click the <xref:System.Activities.Statements.Flowchart> activity on the workflow designer surface to select it.</span></span>  
  
10. <span data-ttu-id="d55eb-126">Tür `Guess` içine **adı** kutusunda **Int32** gelen **değişken türü** aşağı açılan liste ve değişkeni kaydetmek için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d55eb-126">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
11. <span data-ttu-id="d55eb-127">Tıklatın **değişken oluşturma**.</span><span class="sxs-lookup"><span data-stu-id="d55eb-127">Click **Create Variable**.</span></span>  
  
12. <span data-ttu-id="d55eb-128">Tür `Target` içine **adı** kutusunda **Int32** gelen **değişken türü** aşağı açılan liste ve değişkeni kaydetmek için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d55eb-128">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
13. <span data-ttu-id="d55eb-129">Tıklatın **değişkenleri** kapatmak için etkinlik Tasarımcısı sol tarafındaki **değişkenleri** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="d55eb-129">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>  
  
### <a name="to-add-the-workflow-activities"></a><span data-ttu-id="d55eb-130">İş akışı etkinlikleri eklemek için</span><span class="sxs-lookup"><span data-stu-id="d55eb-130">To add the workflow activities</span></span>  
  
1.  <span data-ttu-id="d55eb-131">Sürükle bir **atamak** etkinliğinden **Temelleri** bölümünü **araç** ve üzerine gelin, üzerinden **Başlat** en üstünde olduğu düğümü Akış Çizelgesi.</span><span class="sxs-lookup"><span data-stu-id="d55eb-131">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and hover it over the **Start** node, which is at the top of the flowchart.</span></span> <span data-ttu-id="d55eb-132">Zaman **atamak** etkinliktir üzerinden **Başlat** düğümü, üç üçgenler etrafında görünür **Başlat** düğümü.</span><span class="sxs-lookup"><span data-stu-id="d55eb-132">When the **Assign** activity is over the **Start** node, three triangles will appear around the **Start** node.</span></span> <span data-ttu-id="d55eb-133">Bırakma **atamak** doğrudan aşağıdaki üçgen faaliyete **Başlat** düğümü.</span><span class="sxs-lookup"><span data-stu-id="d55eb-133">Drop the **Assign** activity on the triangle that is directly below the **Start** node.</span></span> <span data-ttu-id="d55eb-134">Bu iki öğeyi birbirine bağlamak ve atar **atamak** etkinlik akış ilk etkinlik olarak.</span><span class="sxs-lookup"><span data-stu-id="d55eb-134">This will link the two items together and designates the **Assign** activity as the first activity in the flowchart.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d55eb-135">Etkinlikler de başlangıç etkinliği iş akışı olarak el ile etkinlik başlangıç düğümü bağlayarak belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="d55eb-135">Activities can also be indicated as the starting activity in the workflow by manually linking them activity to the start node.</span></span> <span data-ttu-id="d55eb-136">Bunu yapmak için fareyi üzerine gelerek **Başlat** düğümü, fare üzerinden olduğunda görüntülenen dikdörtgenler birini tıklatın **Başlat** düğümü ve bağlanma satır istenen etkinlik aşağı kaydırın ve aşağıdakilerden birini bırakma sürükleyin görünen dikdörtgenler.</span><span class="sxs-lookup"><span data-stu-id="d55eb-136">To do this, hover the mouse over the **Start** node, click one of the rectangles that appear when the mouse is over the **Start** node, and drag the connecting line down to the desired activity and drop it on one of the rectangles that appear.</span></span> <span data-ttu-id="d55eb-137">Ayrıca belirleyebilirsiniz ve BT sağ tıklayarak ve seçme başlangıç etkinliği gibi etkinlik **Başlat düğüm kümesi**.</span><span class="sxs-lookup"><span data-stu-id="d55eb-137">You can also designate and activity as the starting activity by right-clicking the it and choosing **Set as Start Node**.</span></span>  
  
2.  <span data-ttu-id="d55eb-138">Tür `Target` içine **için** kutusu ve aşağıdaki ifadesine **bir C# ifadesi girin** veya **bir VB ifadesi girin** kutusu.</span><span class="sxs-lookup"><span data-stu-id="d55eb-138">Type `Target` into the **To** box and the following expression into the **Enter a C# Expression** or **Enter a VB expression** box.</span></span>  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="d55eb-139">Varsa **araç** penceresi görüntülenmez, seçin **araç** gelen **Görünüm** menüsü.</span><span class="sxs-lookup"><span data-stu-id="d55eb-139">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
3.  <span data-ttu-id="d55eb-140">Sürükleme bir **komut istemi** etkinliğinden **NumberGuessWorkflowActivities** bölümünü **araç**, aşağıdaki bırakma **atamak** etkinliği Önceki adım ve bağlanın **komut istemi** etkinliğe **atamak** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="d55eb-140">Drag a **Prompt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox**, drop it below the **Assign** activity from the previous step, and connect the **Prompt** activity to the **Assign** activity.</span></span> <span data-ttu-id="d55eb-141">İki etkinlik bağlanmak için üç yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="d55eb-141">There are three ways to connect the two activities.</span></span> <span data-ttu-id="d55eb-142">Bıraktığınız gibi bunları bağlamak için ilk yoludur **komut istemi** iş akışı etkinliği.</span><span class="sxs-lookup"><span data-stu-id="d55eb-142">The first way is to connect them as you drop the **Prompt** activity on the workflow.</span></span> <span data-ttu-id="d55eb-143">Sürüklediğiniz gibi **komut istemi** iş akışına aktivite üzerine gelin, üzerinden **atamak** etkinliği ve ne zaman görünür dört üçgenler birini üzerine bırakın **komut istemi** etkinliktir üzerinden **atamak** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="d55eb-143">As you are dragging the **Prompt** activity to the workflow, hover it over the **Assign** activity and drop it onto one of the four triangles that appear when the **Prompt** activity is over the **Assign** activity.</span></span> <span data-ttu-id="d55eb-144">Bırakmak için ikinci yoludur **komut istemi** etkinliği iş akışı istenen konuma üzerine.</span><span class="sxs-lookup"><span data-stu-id="d55eb-144">The second way is to drop the **Prompt** activity onto the workflow at the desired location.</span></span> <span data-ttu-id="d55eb-145">Fare ardından üzerine gelerek **atamak** etkinliği ve sürükleme aşağı görünüyor dikdörtgenler birini **komut istemi** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="d55eb-145">Then, hover the mouse over the **Assign** activity and drag one of the rectangles that appears down to the **Prompt** activity.</span></span> <span data-ttu-id="d55eb-146">Böylece bağlanma satır fareyi sürükleyin **atamak** etkinlik dikdörtgen birine bağlayan **komut istemi** etkinliği ve ardından yayın fare düğmesini.</span><span class="sxs-lookup"><span data-stu-id="d55eb-146">Drag the mouse so that the connecting line from the **Assign** activity connects to one of the rectangles of the **Prompt** activity, and then release the mouse button.</span></span> <span data-ttu-id="d55eb-147">Üçüncü yolu çok hariç sürükleyerek yerine ilk yol benzer **komut istemi** etkinliğinden **araç**, konumundan iş akışı tasarım yüzeyine sürükleyin, getirin **Ata** etkinliği ve görünür üçgenler birini üzerine bırakın.</span><span class="sxs-lookup"><span data-stu-id="d55eb-147">The third way is very similar to the first way, except that instead of dragging the **Prompt** activity from the **Toolbox**, you drag it from its location on the workflow design surface, hover it over the **Assign** activity, and drop it onto one of the triangles that appears.</span></span>  
  
4.  <span data-ttu-id="d55eb-148">İçinde **Özellikler penceresini** için **komut istemi** etkinliği, türü `"EnterGuess"` tırnak işaretleri içine dahil **YerİşaretiAdı** özellik değeri kutusu.</span><span class="sxs-lookup"><span data-stu-id="d55eb-148">In the **Properties Window** for the **Prompt** activity, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box.</span></span> <span data-ttu-id="d55eb-149">Tür `Guess` içine **sonuç** özelliği değeri kutusunu ve içine aşağıdaki ifadeyi yazın **metin** özellik kutusu.</span><span class="sxs-lookup"><span data-stu-id="d55eb-149">Type `Guess` into the **Result** property value box, and type the following expression into the **Text** property box.</span></span>  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="d55eb-150">Varsa **Özellikler penceresini** görüntülenen, select değil **Özellikler penceresini** gelen **Görünüm** menüsü.</span><span class="sxs-lookup"><span data-stu-id="d55eb-150">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
5.  <span data-ttu-id="d55eb-151">Sürükleme bir **atamak** etkinliğinden **Temelleri** bölümünü **araç** ve olmasınısağlamaköncekiadımdaaçıklananyöntemlerdenbirinikullanarakbağlanın **Komut İstemi** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="d55eb-151">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and connect it using one of the methods described in the previous step so that it is below the **Prompt** activity.</span></span>  
  
6.  <span data-ttu-id="d55eb-152">Tür `Turns` içine **için** kutusu ve `Turns + 1` içine **bir C# ifadesi girin** veya **bir VB ifadesi girin** kutusu.</span><span class="sxs-lookup"><span data-stu-id="d55eb-152">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression**  or **Enter a VB expression** box.</span></span>  
  
7.  <span data-ttu-id="d55eb-153">Sürükleme bir **FlowDecision** gelen **akış çizelgesi** bölümünü **araç** ve aşağıdaki bağlanmak **atamak** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="d55eb-153">Drag a **FlowDecision** from the **Flowchart** section of the **Toolbox** and connect it below the **Assign** activity.</span></span> <span data-ttu-id="d55eb-154">İçinde **Özellikler penceresini**, içine aşağıdaki ifadeyi yazın **koşulu** özellik değeri kutusu.</span><span class="sxs-lookup"><span data-stu-id="d55eb-154">In the **Properties Window**, type the following expression into the **Condition** property value box.</span></span>  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
8.  <span data-ttu-id="d55eb-155">Başka bir sürükleyin **FlowDecision** etkinliğinden **araç** ve birinci bırakın.</span><span class="sxs-lookup"><span data-stu-id="d55eb-155">Drag another **FlowDecision** activity from the **Toolbox** and drop it below the first one.</span></span> <span data-ttu-id="d55eb-156">Etiketli dikdörtgen sürükleyerek iki etkinlik bağlanmak **False** üstte **FlowDecision** dikdörtgen etkinliğe ikinci üstündeki **FlowDecision**etkinlik.</span><span class="sxs-lookup"><span data-stu-id="d55eb-156">Connect the two activities by dragging from the rectangle that is labeled **False** on the top **FlowDecision** activity to the rectangle at the top of the second **FlowDecision** activity.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="d55eb-157">Görmüyorsanız, **True** ve **False** üzerinde etiketler **FlowDecision**, fare üzerine gelerek **FlowDecision**.</span><span class="sxs-lookup"><span data-stu-id="d55eb-157">If you do not see the **True** and **False** labels on the **FlowDecision**, hover the mouse over the **FlowDecision**.</span></span>  
  
9. <span data-ttu-id="d55eb-158">İkinci tıklatın **FlowDecision** etkinliği seçin.</span><span class="sxs-lookup"><span data-stu-id="d55eb-158">Click the second **FlowDecision** activity to select it.</span></span> <span data-ttu-id="d55eb-159">İçinde **Özellikler penceresini**, içine aşağıdaki ifadeyi yazın **koşulu** özellik değeri kutusu.</span><span class="sxs-lookup"><span data-stu-id="d55eb-159">In the **Properties Window**, type the following expression into the **Condition** property value box.</span></span>  
  
    ```
    Guess < Target  
    ```  
  
10. <span data-ttu-id="d55eb-160">İki **WriteLine** etkinliklerden **Temelleri** bölümünü **araç** ve böylece yan yana iki oldukları bırakın **FlowDecision**  etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="d55eb-160">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that they are side by side below the two **FlowDecision** activities.</span></span> <span data-ttu-id="d55eb-161">Bağlanma **True** alt eylem **FlowDecision** etkinliğe soldaki **WriteLine** etkinliği ve **False** eyleme en sağdaki **WriteLine** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="d55eb-161">Connect the **True** action of the bottom **FlowDecision** activity to the leftmost **WriteLine** activity, and the **False** action to the rightmost **WriteLine** activity.</span></span>  
  
11. <span data-ttu-id="d55eb-162">Soldaki tıklatın **WriteLine** seçin ve içine aşağıdaki ifadeyi yazın etkinlik **metin** özellik değeri kutusunda **Özellikler penceresini**.</span><span class="sxs-lookup"><span data-stu-id="d55eb-162">Click the leftmost **WriteLine** activity to select it, and type the following expression into the **Text** property value box in the **Properties Window**.</span></span>  
  
    ```
    "Your guess is too low."  
    ```  
  
12. <span data-ttu-id="d55eb-163">Bağlantı **WriteLine** sol tarafına **komut istemi** üstüne etkinliğini.</span><span class="sxs-lookup"><span data-stu-id="d55eb-163">Connect the **WriteLine** to the left side of the **Prompt** activity that is above it.</span></span>  
  
13. <span data-ttu-id="d55eb-164">En sağdaki tıklatın **WriteLine** seçin ve içine aşağıdaki ifadeyi yazın etkinlik **metin** özellik değeri kutusunda **Özellikler penceresini**.</span><span class="sxs-lookup"><span data-stu-id="d55eb-164">Click the rightmost **WriteLine** activity to select it, and type the following expression into the **Text** property value box in the **Properties Window**.</span></span>  
  
    ```
    "Your guess is too high."  
    ```  
  
14. <span data-ttu-id="d55eb-165">Bağlantı **WriteLine** etkinliğinin sağ tarafına **komut istemi** üstündeki etkinlik.</span><span class="sxs-lookup"><span data-stu-id="d55eb-165">Connect the **WriteLine** activity to the right side of the **Prompt** activity above it.</span></span>  
  
     <span data-ttu-id="d55eb-166">Aşağıdaki örnek, tamamlanan iş akışı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d55eb-166">The following example illustrates the completed workflow.</span></span>  
  
     <span data-ttu-id="d55eb-167">![Windows Workflow Foundation tamamlandı](../../../docs/framework/windows-workflow-foundation/media/gettingstartedtutorialcompletedflowchart.PNG "GettingStartedTutorialCompletedFlowchart")</span><span class="sxs-lookup"><span data-stu-id="d55eb-167">![Completed Windows Workflow Foundation](../../../docs/framework/windows-workflow-foundation/media/gettingstartedtutorialcompletedflowchart.PNG "GettingStartedTutorialCompletedFlowchart")</span></span>  
  
### <a name="to-build-the-workflow"></a><span data-ttu-id="d55eb-168">İş akışı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d55eb-168">To build the workflow</span></span>  
  
1.  <span data-ttu-id="d55eb-169">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d55eb-169">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="d55eb-170">İş akışını çalıştırmak yönergeler Lütfen görmek için sonraki konuyu [nasıl yapılır: bir iş akışını çalıştırma](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="d55eb-170">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span></span> <span data-ttu-id="d55eb-171">Zaten tamamladıysanız [nasıl yapılır: bir iş akışını çalıştırma](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) adım farklı bir iş akışı stil ile ve çalıştırmak bu adımı akış iş akışını kullanarak istediğiniz, için İleri atlayabilirsiniz [oluşturmak veuygulamayıçalıştırmakiçin](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication)bölümünü [nasıl yapılır: bir iş akışını çalıştırma](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="d55eb-171">If you have already completed the [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the flowchart workflow from this step, skip ahead to the [To build and run the application](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d55eb-172">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d55eb-172">See Also</span></span>  
 <xref:System.Activities.Statements.Flowchart>  
 <xref:System.Activities.Statements.FlowDecision>  
 [<span data-ttu-id="d55eb-173">Windows Workflow Foundation programlama</span><span class="sxs-lookup"><span data-stu-id="d55eb-173">Windows Workflow Foundation Programming</span></span>](../../../docs/framework/windows-workflow-foundation/programming.md)  
 [<span data-ttu-id="d55eb-174">İş akışları tasarlama</span><span class="sxs-lookup"><span data-stu-id="d55eb-174">Designing Workflows</span></span>](../../../docs/framework/windows-workflow-foundation/designing-workflows.md)  
 [<span data-ttu-id="d55eb-175">Başlangıç Öğreticisi</span><span class="sxs-lookup"><span data-stu-id="d55eb-175">Getting Started Tutorial</span></span>](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [<span data-ttu-id="d55eb-176">Nasıl yapılır: bir etkinlik oluşturmak</span><span class="sxs-lookup"><span data-stu-id="d55eb-176">How to: Create an Activity</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)  
 [<span data-ttu-id="d55eb-177">Nasıl yapılır: bir iş akışını çalıştırma</span><span class="sxs-lookup"><span data-stu-id="d55eb-177">How to: Run a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)
