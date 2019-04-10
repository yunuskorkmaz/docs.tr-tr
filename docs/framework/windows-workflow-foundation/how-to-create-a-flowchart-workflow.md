---
title: 'Nasıl yapılır: Akış Çizelgesi İş Akışı Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 185d7aea-68a6-4bd8-adde-45050f33170a
ms.openlocfilehash: 15cf94d5ea191435723f754f35e43d65632142e2
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59311207"
---
# <a name="how-to-create-a-flowchart-workflow"></a><span data-ttu-id="1e62d-102">Nasıl yapılır: Akış Çizelgesi İş Akışı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1e62d-102">How to: Create a Flowchart Workflow</span></span>
<span data-ttu-id="1e62d-103">İş akışları yerleşik etkinliklerden yanı sıra özel etkinliklerden oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="1e62d-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="1e62d-104">Bu konu başlığı altında adımlar hem yerleşik etkinlikler gibi kullanan bir iş akışı oluşturma işleminde <xref:System.Activities.Statements.Flowchart> etkinliği ve özel etkinlikler önceki [nasıl yapılır: Bir etkinlik oluşturursunuz](how-to-create-an-activity.md) konu.</span><span class="sxs-lookup"><span data-stu-id="1e62d-104">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Flowchart> activity, and the custom activities from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="1e62d-105">İş akışı sayısını tahmin eden oyun modelleri.</span><span class="sxs-lookup"><span data-stu-id="1e62d-105">The workflow models a number guessing game.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1e62d-106">Önceki konularıyla ilgili her konuda Başlarken Öğreticisi bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="1e62d-106">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="1e62d-107">Bu konuyu tamamlamak için önce tamamlamanız gereken [nasıl yapılır: Bir etkinlik oluşturursunuz](how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="1e62d-107">To complete this topic, you must first complete [How to: Create an Activity](how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1e62d-108">Öğreticinin tamamlanmış bir sürümünü indirmek için bkz [Windows Workflow Foundation (WF45) - başlangıç Öğreticisi](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="1e62d-108">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-workflow"></a><span data-ttu-id="1e62d-109">İş akışını oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="1e62d-109">To create the workflow</span></span>  
  
1. <span data-ttu-id="1e62d-110">Sağ **NumberGuessWorkflowActivities** içinde **Çözüm Gezgini** seçip **Ekle**, **yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="1e62d-110">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>  
  
2. <span data-ttu-id="1e62d-111">İçinde **yüklü**, **ortak öğeler** düğümünü **iş akışı**.</span><span class="sxs-lookup"><span data-stu-id="1e62d-111">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="1e62d-112">Seçin **etkinlik** gelen **iş akışı** listesi.</span><span class="sxs-lookup"><span data-stu-id="1e62d-112">Select **Activity** from the **Workflow** list.</span></span>  
  
3. <span data-ttu-id="1e62d-113">Tür `FlowchartNumberGuessWorkflow` içine **adı** kutusuna ve tıklatın **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="1e62d-113">Type `FlowchartNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>  
  
4. <span data-ttu-id="1e62d-114">Sürükle bir **akış** etkinliğinden **akış** bölümünü **araç kutusu** üzerine bırakın **bırak etkinliği Buraya** üzerindeki etiket İş akışı tasarım yüzeyi.</span><span class="sxs-lookup"><span data-stu-id="1e62d-114">Drag a **Flowchart** activity from the **Flowchart** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="1e62d-115">Bağımsız değişkenler ve iş akışı değişkenlerini oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="1e62d-115">To create the workflow variables and arguments</span></span>  
  
1. <span data-ttu-id="1e62d-116">Çift **FlowchartNumberGuessWorkflow.xaml** içinde **Çözüm Gezgini** zaten görüntülenmiyorsa, iş akışı Tasarımcısı'nda görüntülenecek.</span><span class="sxs-lookup"><span data-stu-id="1e62d-116">Double-click **FlowchartNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>  
  
2. <span data-ttu-id="1e62d-117">Tıklayın **bağımsız değişkenleri** sol alt tarafında görüntülenecek iş akışı Tasarımcısı **bağımsız değişkenleri** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="1e62d-117">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
3. <span data-ttu-id="1e62d-118">Tıklayın **bağımsız değişken oluşturma**.</span><span class="sxs-lookup"><span data-stu-id="1e62d-118">Click **Create Argument**.</span></span>  
  
4. <span data-ttu-id="1e62d-119">Tür `MaxNumber` içine **adı** kutusunda **içinde** gelen **yönü** aşağı açılan listesinden **Int32** gelen**Bağımsız değişken türü** aşağı açılan liste ve bağımsız değişkeni kaydetmek için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="1e62d-119">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
5. <span data-ttu-id="1e62d-120">Tıklayın **bağımsız değişken oluşturma**.</span><span class="sxs-lookup"><span data-stu-id="1e62d-120">Click **Create Argument**.</span></span>  
  
6. <span data-ttu-id="1e62d-121">Tür `Turns` içine **adı** altında yeni eklenen kutusunu `MaxNumber` bağımsız değişkeni, select **kullanıma** gelen **yönü** aşağı açılan listesinden  **Int32** gelen **bağımsız değişken türü** aşağı açılan liste ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="1e62d-121">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
7. <span data-ttu-id="1e62d-122">Tıklayın **bağımsız değişkenleri** etkinlik Tasarımcısı kapatmak için sol alt tarafında **bağımsız değişkenleri** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="1e62d-122">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
8. <span data-ttu-id="1e62d-123">Tıklayın **değişkenleri** sol alt tarafında görüntülenecek iş akışı Tasarımcısı **değişkenleri** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="1e62d-123">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>  
  
9. <span data-ttu-id="1e62d-124">Tıklayın **değişken oluşturma**.</span><span class="sxs-lookup"><span data-stu-id="1e62d-124">Click **Create Variable**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="1e62d-125">Hayır ise **oluşturma değişken** kutusu görüntülenir, tıklayın <xref:System.Activities.Statements.Flowchart> seçmek için iş akışı Tasarımcı yüzeyine etkinliği.</span><span class="sxs-lookup"><span data-stu-id="1e62d-125">If no **Create Variable** box is displayed, click the <xref:System.Activities.Statements.Flowchart> activity on the workflow designer surface to select it.</span></span>  
  
10. <span data-ttu-id="1e62d-126">Tür `Guess` içine **adı** kutusunda **Int32** gelen **değişken türü** aşağı açılan liste ve değişkeni kaydetmek için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="1e62d-126">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
11. <span data-ttu-id="1e62d-127">Tıklayın **değişken oluşturma**.</span><span class="sxs-lookup"><span data-stu-id="1e62d-127">Click **Create Variable**.</span></span>  
  
12. <span data-ttu-id="1e62d-128">Tür `Target` içine **adı** kutusunda **Int32** gelen **değişken türü** aşağı açılan liste ve değişkeni kaydetmek için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="1e62d-128">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
13. <span data-ttu-id="1e62d-129">Tıklayın **değişkenleri** etkinlik Tasarımcısı kapatmak için sol alt tarafında **değişkenleri** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="1e62d-129">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>  
  
### <a name="to-add-the-workflow-activities"></a><span data-ttu-id="1e62d-130">İş akışı etkinlikleri eklemek için</span><span class="sxs-lookup"><span data-stu-id="1e62d-130">To add the workflow activities</span></span>  
  
1. <span data-ttu-id="1e62d-131">Sürükle bir **atama** etkinliğinden **Temelleri** bölümünü **araç kutusu** ve onu kutucuğunun üzerine gelin **Başlat** üstünde olan düğüm Akış Çizelgesi.</span><span class="sxs-lookup"><span data-stu-id="1e62d-131">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and hover it over the **Start** node, which is at the top of the flowchart.</span></span> <span data-ttu-id="1e62d-132">Zaman **atama** etkinliktir üzerinden **Başlat** düğüm, üç üçgenler geçici olarak görünür **Başlat** düğümü.</span><span class="sxs-lookup"><span data-stu-id="1e62d-132">When the **Assign** activity is over the **Start** node, three triangles will appear around the **Start** node.</span></span> <span data-ttu-id="1e62d-133">DROP **atama** doğrudan aşağıdaki üçgen faaliyete **Başlat** düğümü.</span><span class="sxs-lookup"><span data-stu-id="1e62d-133">Drop the **Assign** activity on the triangle that is directly below the **Start** node.</span></span> <span data-ttu-id="1e62d-134">Bu iki öğeyi birbirine bağlamak ve atar **atama** akış ilk etkinlik olarak etkinlik.</span><span class="sxs-lookup"><span data-stu-id="1e62d-134">This will link the two items together and designates the **Assign** activity as the first activity in the flowchart.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1e62d-135">Etkinlikler de başlangıç etkinliği iş akışı olarak el ile etkinlik başlangıç düğümüne bağlayarak belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="1e62d-135">Activities can also be indicated as the starting activity in the workflow by manually linking them activity to the start node.</span></span> <span data-ttu-id="1e62d-136">Bunu yapmak için fareyi üzerine **Başlat** düğümü, fareyi üzerine geldiğinde görünen dikdörtgen birine tıklayın **Başlat** düğümü ile bağlanma ve satır aşağı istenen etkinlik birinde bırakın sürükleyin görünen dikdörtgen.</span><span class="sxs-lookup"><span data-stu-id="1e62d-136">To do this, hover the mouse over the **Start** node, click one of the rectangles that appear when the mouse is over the **Start** node, and drag the connecting line down to the desired activity and drop it on one of the rectangles that appear.</span></span> <span data-ttu-id="1e62d-137">Ayrıca bir etkinliğin başlangıç etkinliği olarak BT sağ tıklayıp seçerek belirleyebilirsiniz **başlangıç düğümü olarak ayarlamak**.</span><span class="sxs-lookup"><span data-stu-id="1e62d-137">You can also designate an activity as the starting activity by right-clicking the it and choosing **Set as Start Node**.</span></span>  
  
2. <span data-ttu-id="1e62d-138">Tür `Target` içine **için** kutusu ve içine aşağıdaki ifade **bir C# ifadesi girin** veya **zadejte Výraz jazyka vb.** kutusu.</span><span class="sxs-lookup"><span data-stu-id="1e62d-138">Type `Target` into the **To** box and the following expression into the **Enter a C# Expression** or **Enter a VB expression** box.</span></span>  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="1e62d-139">Varsa **araç kutusu** penceresi görüntülenmiyorsa, seçin **araç kutusu** gelen **görünümü** menüsü.</span><span class="sxs-lookup"><span data-stu-id="1e62d-139">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
3. <span data-ttu-id="1e62d-140">Sürükle bir **istemi** etkinliğinden **NumberGuessWorkflowActivities** bölümünü **araç kutusu**, aşağıdaki açılan **atama** etkinliği Önceki adım ve connect **komut istemi** etkinliğini **atama** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="1e62d-140">Drag a **Prompt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox**, drop it below the **Assign** activity from the previous step, and connect the **Prompt** activity to the **Assign** activity.</span></span> <span data-ttu-id="1e62d-141">İki etkinliği bağlanmak için üç yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="1e62d-141">There are three ways to connect the two activities.</span></span> <span data-ttu-id="1e62d-142">Bıraktığınız gibi bunları bağlamak için ilk yoludur **istemi** iş akışı etkinliği.</span><span class="sxs-lookup"><span data-stu-id="1e62d-142">The first way is to connect them as you drop the **Prompt** activity on the workflow.</span></span> <span data-ttu-id="1e62d-143">Sürüklediğiniz gibi **komut istemi** etkinlik iş akışı için bunu kutucuğunun üzerine gelin **atama** etkinlik görünür dört üçgenler birini üzerine bırakın **istemi** Etkinlik bittikten **atama** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="1e62d-143">As you are dragging the **Prompt** activity to the workflow, hover it over the **Assign** activity and drop it onto one of the four triangles that appear when the **Prompt** activity is over the **Assign** activity.</span></span> <span data-ttu-id="1e62d-144">Bırakmak ikinci yoludur **istemi** etkinlik iş akışı istenen konuma sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="1e62d-144">The second way is to drop the **Prompt** activity onto the workflow at the desired location.</span></span> <span data-ttu-id="1e62d-145">Fareyi üzerine ardından **atama** etkinliği ve dikdörtgenlerden görünen aşağı sürükleyin **istemi** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="1e62d-145">Then, hover the mouse over the **Assign** activity and drag one of the rectangles that appears down to the **Prompt** activity.</span></span> <span data-ttu-id="1e62d-146">Fareyi sürükleyin, böylece bağlanma satır gelen **atama** etkinlik bağlayan bir dikdörtgen **istemi** etkinliği ve ardından sürüm fare düğmesini.</span><span class="sxs-lookup"><span data-stu-id="1e62d-146">Drag the mouse so that the connecting line from the **Assign** activity connects to one of the rectangles of the **Prompt** activity, and then release the mouse button.</span></span> <span data-ttu-id="1e62d-147">Üçüncü yolu çok hariç sürükleyerek yerine ilk yol benzer **istemi** etkinliğinden **araç kutusu**, iş akışı tasarım yüzeyinde konumundan sürükleyin, gelin **Ata** etkinliği ve görüntülenen üçgenler birini üzerine bırakın.</span><span class="sxs-lookup"><span data-stu-id="1e62d-147">The third way is very similar to the first way, except that instead of dragging the **Prompt** activity from the **Toolbox**, you drag it from its location on the workflow design surface, hover it over the **Assign** activity, and drop it onto one of the triangles that appears.</span></span>  
  
4. <span data-ttu-id="1e62d-148">İçinde **Özellikler penceresi** için **istemi** etkinliği, türü `"EnterGuess"` tırnak işaretleri içine dahil **YerİşaretiAdı** özellik değer kutusu.</span><span class="sxs-lookup"><span data-stu-id="1e62d-148">In the **Properties Window** for the **Prompt** activity, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box.</span></span> <span data-ttu-id="1e62d-149">Tür `Guess` içine **sonucu** özellik değer kutusu ve içine aşağıdaki ifadeyi yazın **metin** özellik kutusu.</span><span class="sxs-lookup"><span data-stu-id="1e62d-149">Type `Guess` into the **Result** property value box, and type the following expression into the **Text** property box.</span></span>  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="1e62d-150">Varsa **Özellikler penceresi** görüntülenen, select değil **Özellikler penceresi** gelen **görünümü** menüsü.</span><span class="sxs-lookup"><span data-stu-id="1e62d-150">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
5. <span data-ttu-id="1e62d-151">Sürükle bir **atama** etkinliğinden **Temelleri** bölümünü **araç kutusu** ve olmasıöncekiadımdaaçıklananyöntemlerdenbirinikullanarakbağlanma **Komut İstemi** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="1e62d-151">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and connect it using one of the methods described in the previous step so that it is below the **Prompt** activity.</span></span>  
  
6. <span data-ttu-id="1e62d-152">Tür `Turns` içine **için** kutusu ve `Turns + 1` içine **bir C# ifadesi girin** veya **zadejte Výraz jazyka vb.** kutusu.</span><span class="sxs-lookup"><span data-stu-id="1e62d-152">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression**  or **Enter a VB expression** box.</span></span>  
  
7. <span data-ttu-id="1e62d-153">Sürükleme bir **FlowDecision** gelen **akış** bölümünü **araç kutusu** ve aşağıdaki bağlantı **atama** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="1e62d-153">Drag a **FlowDecision** from the **Flowchart** section of the **Toolbox** and connect it below the **Assign** activity.</span></span> <span data-ttu-id="1e62d-154">İçinde **Özellikler penceresi**, içine aşağıdaki ifadeyi yazın **koşul** özellik değer kutusu.</span><span class="sxs-lookup"><span data-stu-id="1e62d-154">In the **Properties Window**, type the following expression into the **Condition** property value box.</span></span>  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
8. <span data-ttu-id="1e62d-155">Başka bir sürükleyin **FlowDecision** etkinliğinden **araç kutusu** ilki bırakın.</span><span class="sxs-lookup"><span data-stu-id="1e62d-155">Drag another **FlowDecision** activity from the **Toolbox** and drop it below the first one.</span></span> <span data-ttu-id="1e62d-156">Etiketli dikdörtgenden sürükleyerek iki etkinliklerini bağlama **False** üst **FlowDecision** dikdörtgen etkinliğe ikinci üst kısmındaki **FlowDecision**etkinlik.</span><span class="sxs-lookup"><span data-stu-id="1e62d-156">Connect the two activities by dragging from the rectangle that is labeled **False** on the top **FlowDecision** activity to the rectangle at the top of the second **FlowDecision** activity.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="1e62d-157">Görmüyorsanız, **True** ve **False** üzerinde etiketler **FlowDecision**, fareyi üzerine **FlowDecision**.</span><span class="sxs-lookup"><span data-stu-id="1e62d-157">If you do not see the **True** and **False** labels on the **FlowDecision**, hover the mouse over the **FlowDecision**.</span></span>  
  
9. <span data-ttu-id="1e62d-158">İkinci tıklama **FlowDecision** etkinliği seçin.</span><span class="sxs-lookup"><span data-stu-id="1e62d-158">Click the second **FlowDecision** activity to select it.</span></span> <span data-ttu-id="1e62d-159">İçinde **Özellikler penceresi**, içine aşağıdaki ifadeyi yazın **koşul** özellik değer kutusu.</span><span class="sxs-lookup"><span data-stu-id="1e62d-159">In the **Properties Window**, type the following expression into the **Condition** property value box.</span></span>  
  
    ```
    Guess < Target  
    ```  
  
10. <span data-ttu-id="1e62d-160">İki **WriteLine** etkinlikten **Temelleri** bölümünü **araç kutusu** ve bunlar yan yana iki altında olacak şekilde bırakın **FlowDecision**  etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="1e62d-160">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that they are side by side below the two **FlowDecision** activities.</span></span> <span data-ttu-id="1e62d-161">Bağlanmak **True** alt eylem **FlowDecision** etkinliğini en soldaki **WriteLine** etkinliği ve **False** eylemi en sağdaki **WriteLine** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="1e62d-161">Connect the **True** action of the bottom **FlowDecision** activity to the leftmost **WriteLine** activity, and the **False** action to the rightmost **WriteLine** activity.</span></span>  
  
11. <span data-ttu-id="1e62d-162">En soldaki tıklayın **WriteLine** etkinliği seçin ve içine aşağıdaki ifadeyi yazın **metin** özellik değeri kutusunda **Özellikler penceresi**.</span><span class="sxs-lookup"><span data-stu-id="1e62d-162">Click the leftmost **WriteLine** activity to select it, and type the following expression into the **Text** property value box in the **Properties Window**.</span></span>  
  
    ```
    "Your guess is too low."  
    ```  
  
12. <span data-ttu-id="1e62d-163">Connect **WriteLine** sol tarafına **istemi** üzerinde etkinlik.</span><span class="sxs-lookup"><span data-stu-id="1e62d-163">Connect the **WriteLine** to the left side of the **Prompt** activity that is above it.</span></span>  
  
13. <span data-ttu-id="1e62d-164">En sağdaki tıklayın **WriteLine** etkinliği seçin ve içine aşağıdaki ifadeyi yazın **metin** özellik değeri kutusunda **Özellikler penceresi**.</span><span class="sxs-lookup"><span data-stu-id="1e62d-164">Click the rightmost **WriteLine** activity to select it, and type the following expression into the **Text** property value box in the **Properties Window**.</span></span>  
  
    ```
    "Your guess is too high."  
    ```  
  
14. <span data-ttu-id="1e62d-165">Bağlama **WriteLine** etkinliğinin sağındaki **istemi** üstündeki etkinlik.</span><span class="sxs-lookup"><span data-stu-id="1e62d-165">Connect the **WriteLine** activity to the right side of the **Prompt** activity above it.</span></span>  
  
     <span data-ttu-id="1e62d-166">Aşağıdaki örnekte, tamamlanmış bir iş akışı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1e62d-166">The following example illustrates the completed workflow.</span></span>  
  
     <span data-ttu-id="1e62d-167">![Windows Workflow Foundation tamamlandı](./media/gettingstartedtutorialcompletedflowchart.PNG "GettingStartedTutorialCompletedFlowchart")</span><span class="sxs-lookup"><span data-stu-id="1e62d-167">![Completed Windows Workflow Foundation](./media/gettingstartedtutorialcompletedflowchart.PNG "GettingStartedTutorialCompletedFlowchart")</span></span>  
  
### <a name="to-build-the-workflow"></a><span data-ttu-id="1e62d-168">İş akışı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="1e62d-168">To build the workflow</span></span>  
  
1. <span data-ttu-id="1e62d-169">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="1e62d-169">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="1e62d-170">Lütfen iş akışının nasıl çalıştırılacağını yönergeleri görmek için bir sonraki konu [nasıl yapılır: İş akışı çalıştırma](how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="1e62d-170">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span> <span data-ttu-id="1e62d-171">Zaten tamamladıysanız [nasıl yapılır: İş akışı çalıştırma](how-to-run-a-workflow.md) adım iş akışı farklı bir stil ve çalıştırmak bu adımdaki akış çizelgesi iş akışı kullanarak istediğiniz, atlayın [uygulaması derleme ve çalıştırma için](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) bölümünü [nasıl yapılır: İş akışı çalıştırma](how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="1e62d-171">If you have already completed the [How to: Run a Workflow](how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the flowchart workflow from this step, skip ahead to the [To build and run the application](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e62d-172">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1e62d-172">See also</span></span>

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [<span data-ttu-id="1e62d-173">Windows Workflow Foundation Programlama</span><span class="sxs-lookup"><span data-stu-id="1e62d-173">Windows Workflow Foundation Programming</span></span>](programming.md)
- [<span data-ttu-id="1e62d-174">İş Akışları Tasarlama</span><span class="sxs-lookup"><span data-stu-id="1e62d-174">Designing Workflows</span></span>](designing-workflows.md)
- [<span data-ttu-id="1e62d-175">Başlangıç Öğreticisi</span><span class="sxs-lookup"><span data-stu-id="1e62d-175">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="1e62d-176">Nasıl yapılır: Etkinlik Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1e62d-176">How to: Create an Activity</span></span>](how-to-create-an-activity.md)
- [<span data-ttu-id="1e62d-177">Nasıl yapılır: İş Akışı Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="1e62d-177">How to: Run a Workflow</span></span>](how-to-run-a-workflow.md)
