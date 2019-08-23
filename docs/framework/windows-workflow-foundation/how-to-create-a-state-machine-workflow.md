---
title: 'Nasıl yapılır: Durum Makinesi İş Akışı Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3ec60e8f-fad4-493e-a426-e7962d7aee8c
ms.openlocfilehash: 3f1c1beda7519a113ea15c5fed84bcb017afae12
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962357"
---
# <a name="how-to-create-a-state-machine-workflow"></a><span data-ttu-id="7ca37-102">Nasıl yapılır: Durum Makinesi İş Akışı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="7ca37-102">How to: Create a State Machine Workflow</span></span>
<span data-ttu-id="7ca37-103">İş akışları, yerleşik etkinliklerin yanı sıra özel etkinliklerden de oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="7ca37-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="7ca37-104">Bu konu, <xref:System.Activities.Statements.StateMachine> etkinlik gibi yerleşik etkinlikleri ve önceki [nasıl yapılacağı özel etkinlikleri kullanan bir iş akışı oluşturma ile ilgili adımları izleyerek yapılır: Etkinlik](how-to-create-an-activity.md) konusu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7ca37-104">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.StateMachine> activity, and the custom activities from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="7ca37-105">İş akışı, sayıyı tahmin eden bir oyunu modelleyen.</span><span class="sxs-lookup"><span data-stu-id="7ca37-105">The workflow models a number guessing game.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7ca37-106">Başlangıç öğreticisindeki her konu, önceki konulara bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="7ca37-106">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="7ca37-107">Bu konuyu tamamlayabilmeniz için öncelikle [şunları yapmanız gerekir: Etkinlik](how-to-create-an-activity.md)oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7ca37-107">To complete this topic, you must first complete [How to: Create an Activity](how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7ca37-108">Öğreticinin tamamlanmış bir sürümünü indirmek için, bkz. [Windows Workflow Foundation (WF45)-Başlangıç Öğreticisi](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="7ca37-108">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-workflow"></a><span data-ttu-id="7ca37-109">İş akışını oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="7ca37-109">To create the workflow</span></span>  
  
1. <span data-ttu-id="7ca37-110">**Çözüm Gezgini** 'de **NumberGuessWorkflowActivities** öğesine sağ tıklayın ve **Ekle**, **Yeni öğe**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="7ca37-110">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>  
  
2. <span data-ttu-id="7ca37-111">**Yüklü**, **ortak öğeler** düğümünde **iş akışı**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="7ca37-111">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="7ca37-112">**Iş akışı** listesinden **etkinlik** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="7ca37-112">Select **Activity** from the **Workflow** list.</span></span>  
  
3. <span data-ttu-id="7ca37-113">Ad `StateMachineNumberGuessWorkflow` kutusuna yazın ve **Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7ca37-113">Type `StateMachineNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>  
  
4. <span data-ttu-id="7ca37-114">**Araç kutusunun** **durum makinesi** ' nden bir **StateMachine** etkinliğini sürükleyin ve iş akışı tasarım yüzeyinde **buraya bırakma etkinliği** etiketini bırakın.</span><span class="sxs-lookup"><span data-stu-id="7ca37-114">Drag a **StateMachine** activity from the **State Machine** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="7ca37-115">İş akışı değişkenlerini ve bağımsız değişkenleri oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="7ca37-115">To create the workflow variables and arguments</span></span>  
  
1. <span data-ttu-id="7ca37-116">Henüz görüntülenmiyorsa, iş akışını tasarımcıda göstermek için **Çözüm Gezgini** Içindeki **StateMachineNumberGuessWorkflow. xaml** öğesine çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7ca37-116">Double-click **StateMachineNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>  
  
2. <span data-ttu-id="7ca37-117">**Bağımsız değişkenler** bölmesini göstermek için iş akışı Tasarımcısı ' nın sol alt tarafındaki **bağımsız değişkenler** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7ca37-117">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
3. <span data-ttu-id="7ca37-118">**Bağımsız değişken Oluştur**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7ca37-118">Click **Create Argument**.</span></span>  
  
4. <span data-ttu-id="7ca37-119">Ad `MaxNumber` kutusuna yazın , **Yön** açılan listesinden **'** i seçin, **bağımsız değişken türü** açılan listesinden **Int32** ' i seçin ve ardından bağımsız değişkeni kaydetmek için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="7ca37-119">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
5. <span data-ttu-id="7ca37-120">**Bağımsız değişken Oluştur**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7ca37-120">Click **Create Argument**.</span></span>  
  
6. <span data-ttu-id="7ca37-121">Yeni `Turns` eklenen bağımsız`MaxNumber` değişkenin altında bulunan ad kutusuna yazın, Yön açılan listesinden Seç ' i seçin, **bağımsız değişken türü** açılan listesinden Int32 ' i seçin ve ardından ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="7ca37-121">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
7. <span data-ttu-id="7ca37-122">**Bağımsız değişkenler** bölmesini kapatmak için etkinlik tasarımcısının sol alt tarafındaki **bağımsız değişkenler** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7ca37-122">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
8. <span data-ttu-id="7ca37-123">**Değişkenler** bölmesini göstermek için iş akışı Tasarımcısı ' nın sol alt tarafındaki **değişkenler** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7ca37-123">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>  
  
9. <span data-ttu-id="7ca37-124">**Değişken Oluştur**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7ca37-124">Click **Create Variable**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="7ca37-125">**Değişken Oluştur** kutusu görüntülenmiyorsa, iş akışı Tasarımcısı yüzeyinde <xref:System.Activities.Statements.StateMachine> etkinlik ' i tıklatarak seçin.</span><span class="sxs-lookup"><span data-stu-id="7ca37-125">If no **Create Variable** box is displayed, click the <xref:System.Activities.Statements.StateMachine> activity on the workflow designer surface to select it.</span></span>  
  
10. <span data-ttu-id="7ca37-126">Ad `Guess` kutusuna yazın , **değişken türü** açılır listesinden **Int32** ' i seçin ve ardından değişkeni kaydetmek için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="7ca37-126">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
11. <span data-ttu-id="7ca37-127">**Değişken Oluştur**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7ca37-127">Click **Create Variable**.</span></span>  
  
12. <span data-ttu-id="7ca37-128">Ad `Target` kutusuna yazın , **değişken türü** açılır listesinden **Int32** ' i seçin ve ardından değişkeni kaydetmek için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="7ca37-128">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
13. <span data-ttu-id="7ca37-129">**Değişkenler** bölmesini kapatmak için etkinlik tasarımcısının sol alt tarafındaki **değişkenler** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7ca37-129">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>  
  
### <a name="to-add-the-workflow-activities"></a><span data-ttu-id="7ca37-130">İş akışı etkinliklerini eklemek için</span><span class="sxs-lookup"><span data-stu-id="7ca37-130">To add the workflow activities</span></span>  
  
1. <span data-ttu-id="7ca37-131">Seçmek için **State1** öğesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7ca37-131">Click **State1** to select it.</span></span> <span data-ttu-id="7ca37-132">**Özellikler penceresinde** **DisplayName** olarak `Initialize Target`değiştirin.</span><span class="sxs-lookup"><span data-stu-id="7ca37-132">In the **Properties Window**, change the **DisplayName** to `Initialize Target`.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="7ca37-133">**Özellikler penceresi** görüntülenmiyorsa, **Görünüm** menüsünden **Özellikler penceresi** ' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="7ca37-133">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
2. <span data-ttu-id="7ca37-134">İş akışı tasarımcısında yeni yeniden adlandırılmış **başlatma hedefini** açmak için çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7ca37-134">Double-click the newly renamed **Initialize Target** state in the workflow designer to expand it.</span></span>  
  
3. <span data-ttu-id="7ca37-135">**Araç kutusunun** **temel öğeler** bölümünden bir **atama** etkinliği sürükleyin ve durumun **giriş** bölümüne bırakın.</span><span class="sxs-lookup"><span data-stu-id="7ca37-135">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Entry** section of the state.</span></span> <span data-ttu-id="7ca37-136">Buraya `Target` yazın veya bir  **C# ifade girin** veya bir **vb ifadesi girin** .</span><span class="sxs-lookup"><span data-stu-id="7ca37-136">Type `Target` into the **To** box and the following expression into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="7ca37-137">**Araç kutusu** penceresi görüntülenmiyorsa, **Görünüm** menüsünden **araç kutusu** ' nu seçin.</span><span class="sxs-lookup"><span data-stu-id="7ca37-137">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
4. <span data-ttu-id="7ca37-138">İş akışı Tasarımcısı ' nın en üstünde bulunan içerik haritası ' nda **StateMachine** ' e tıklayarak iş akışı tasarımcısında genel durum makinesi görünümüne geri dönün.</span><span class="sxs-lookup"><span data-stu-id="7ca37-138">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
5. <span data-ttu-id="7ca37-139">**Araç kutusunun** **durum makinesi** bölümünden bir **durum** etkinliğini, Iş akışı tasarımcısına sürükleyin ve **hedefi başlatma** durumuna getirin.</span><span class="sxs-lookup"><span data-stu-id="7ca37-139">Drag a **State** activity from the **State Machine** section of the **Toolbox** onto the workflow designer and hover it over the **Initialize Target** state.</span></span> <span data-ttu-id="7ca37-140">Yeni durum bunun üzerinde olduğunda, **hedefi Başlat** durumunun etrafında dört üçgenin görüneceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="7ca37-140">Note that four triangles will appear around the **Initialize Target** state when the new state is over it.</span></span> <span data-ttu-id="7ca37-141">Yeni durumu, **başlatma hedefi** durumunun hemen altındaki üçgende bırakın.</span><span class="sxs-lookup"><span data-stu-id="7ca37-141">Drop the new state on the triangle that is immediately below the **Initialize Target** state.</span></span> <span data-ttu-id="7ca37-142">Bu, yeni durumu iş akışına koyar ve **hedef başlatma** durumundan yeni duruma bir geçiş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7ca37-142">This places the new state onto the workflow and creates a transition from the **Initialize Target** state to the new state.</span></span>  
  
6. <span data-ttu-id="7ca37-143">Seçmek için **State1** ' e tıklayın, **DisplayName** olarak `Enter Guess`değiştirin ve ardından iş akışı tasarımcısında duruma çift tıklayarak genişletin.</span><span class="sxs-lookup"><span data-stu-id="7ca37-143">Click **State1** to select it, change the **DisplayName** to `Enter Guess`, and then double-click the state in the workflow designer to expand it.</span></span>  
  
7. <span data-ttu-id="7ca37-144">**Araç kutusunun** **temel öğeler** bölümünden bir **WriteLine** etkinliği sürükleyin ve durumun **giriş** bölümüne bırakın.</span><span class="sxs-lookup"><span data-stu-id="7ca37-144">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Entry** section of the state.</span></span>  
  
8. <span data-ttu-id="7ca37-145">**WriteLine**'ın **Text** özellik kutusuna aşağıdaki ifadeyi yazın.</span><span class="sxs-lookup"><span data-stu-id="7ca37-145">Type the following expression into the **Text** property box of the **WriteLine**.</span></span>  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
9. <span data-ttu-id="7ca37-146">**Araç kutusu** ' nu **temel elemanlar** bölümünden bir **atama** etkinliği sürükleyin ve durumun **Çıkış** bölümüne bırakın.</span><span class="sxs-lookup"><span data-stu-id="7ca37-146">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop onto the **Exit** section of the state.</span></span>  
  
10. <span data-ttu-id="7ca37-147">To `Turns` kutusuna ve `Turns + 1` **bir C# ifade girin** veya bir **vb ifadesi girin** kutusuna yazın.</span><span class="sxs-lookup"><span data-stu-id="7ca37-147">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
11. <span data-ttu-id="7ca37-148">İş akışı Tasarımcısı ' nın en üstünde bulunan içerik haritası ' nda **StateMachine** ' e tıklayarak iş akışı tasarımcısında genel durum makinesi görünümüne geri dönün.</span><span class="sxs-lookup"><span data-stu-id="7ca37-148">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
12. <span data-ttu-id="7ca37-149">**Araç kutusunun** **durum makinesi** bölümünden bir **FinalState** etkinliği sürükleyin, **tahmin** etme durumunun üzerine gelin ve bir geçişin doğru olması için **tahmin** durumunun sağında görüntülenen üçgene bırakın **ENTER tahmini** ve **FinalState**arasında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="7ca37-149">Drag a **FinalState** activity from the **State Machine** section of the **Toolbox**, hover it over the **Enter Guess** state, and drop it onto the triangle that appears to the right of the **Enter Guess** state so that a transition is created between **Enter Guess** and **FinalState**.</span></span>  
  
13. <span data-ttu-id="7ca37-150">Geçişin varsayılan adı **T2**'dir.</span><span class="sxs-lookup"><span data-stu-id="7ca37-150">The default name of the transition is **T2**.</span></span> <span data-ttu-id="7ca37-151">İş akışı tasarımcısında geçişe tıklayarak seçin ve **DisplayName** değerini **tahmin**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7ca37-151">Click the transition in the workflow designer to select it, and set its **DisplayName** to **Guess Correct**.</span></span> <span data-ttu-id="7ca37-152">Ardından, **sonlandırıdurumu**' na tıklayıp seçin ve tam geçiş adının iki durumdan birinin üzerine bulunmadığından görüntülenecek bir oda olması için sağa sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="7ca37-152">Then click and select the **FinalState**, and drag it to the right so that there is room for the full transition name to be displayed without overlaying either of the two states.</span></span> <span data-ttu-id="7ca37-153">Bu, öğreticideki kalan adımların tamamlanmasını daha kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="7ca37-153">This will make it easier to complete the remaining steps in the tutorial.</span></span>  
  
14. <span data-ttu-id="7ca37-154">İş akışı tasarımcısında yeni yeniden adlandırılmış **tahmin doğru** geçişine çift tıklayarak genişletin.</span><span class="sxs-lookup"><span data-stu-id="7ca37-154">Double-click the newly renamed **Guess Correct** transition in the workflow designer to expand it.</span></span>  
  
15. <span data-ttu-id="7ca37-155">**Araç kutusunun** **NumberGuessWorkflowActivities** bölümünden **readInt** etkinliğini sürükleyin ve geçişin **tetikleyici** bölümüne bırakın.</span><span class="sxs-lookup"><span data-stu-id="7ca37-155">Drag a **ReadInt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **Trigger** section of the transition.</span></span>  
  
16. <span data-ttu-id="7ca37-156">**ReadInt** `"EnterGuess"` etkinliğinin **Özellikler penceresinde** , tırnak işareti **adı** Özellik değeri kutusuna tırnak işareti dahil yazın ve `Guess` **sonuç** özelliği değeri kutusuna yazın</span><span class="sxs-lookup"><span data-stu-id="7ca37-156">In the **Properties Window** for the **ReadInt** activity, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box, and type `Guess` into the **Result** property value box</span></span>  
  
17. <span data-ttu-id="7ca37-157">**Tahmin doğru** geçişinin **koşul** özelliği değeri kutusuna aşağıdaki ifadeyi yazın.</span><span class="sxs-lookup"><span data-stu-id="7ca37-157">Type the following expression into the **Guess Correct** transition’s **Condition** property value box.</span></span>  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
18. <span data-ttu-id="7ca37-158">İş akışı Tasarımcısı ' nın en üstünde bulunan içerik haritası ' nda **StateMachine** ' e tıklayarak iş akışı tasarımcısında genel durum makinesi görünümüne geri dönün.</span><span class="sxs-lookup"><span data-stu-id="7ca37-158">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="7ca37-159">Tetikleyici olayı alındığında ve <xref:System.Activities.Statements.Transition.Condition%2A>varsa, olarak `True`değerlendirilen bir geçiş gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="7ca37-159">A transition occurs when the trigger event is received and the <xref:System.Activities.Statements.Transition.Condition%2A>, if present, evaluates to `True`.</span></span> <span data-ttu-id="7ca37-160">Bu geçiş için, Kullanıcı `Guess` rastgele oluşturulmuş `Target`ile eşleşiyorsa denetim **sonlandırna** geçer ve iş akışı tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="7ca37-160">For this transition, if the user’s `Guess` matches the randomly generated `Target`, then control passes to the **FinalState** and the workflow completes.</span></span>  
  
19. <span data-ttu-id="7ca37-161">Tahminin doğru olup olmadığına bağlı olarak, iş akışı, başka bir TRY için **FinalState** 'e ya da tahmin durumuna **gir** 'e geçiş yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7ca37-161">Depending on whether the guess is correct, the workflow should transition either to the **FinalState** or back to the **Enter Guess** state for another try.</span></span> <span data-ttu-id="7ca37-162">Her iki geçiş de, kullanıcının tahminin **readInt** etkinliği aracılığıyla alınması için bekleyen tetikleyiciyi paylaşır.</span><span class="sxs-lookup"><span data-stu-id="7ca37-162">Both transitions share the same trigger of waiting for the user’s guess to be received via the **ReadInt** activity.</span></span> <span data-ttu-id="7ca37-163">Buna paylaşılan geçiş adı verilir.</span><span class="sxs-lookup"><span data-stu-id="7ca37-163">This is called a shared transition.</span></span> <span data-ttu-id="7ca37-164">Paylaşılan bir geçiş oluşturmak için, **tahmin doğru** geçişinin başlangıcını belirten daireye tıklayın ve istediğiniz duruma sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="7ca37-164">To create a shared transition, click the circle that indicates the start of the **Guess Correct** transition and drag it to the desired state.</span></span> <span data-ttu-id="7ca37-165">Bu durumda, geçiş bir kendinden geçiştir, bu nedenle **tahmin doğru** geçişinin başlangıç noktasını sürükleyin ve **tahmin** durumunun sonuna geri bırakın.</span><span class="sxs-lookup"><span data-stu-id="7ca37-165">In this case the transition is a self-transition, so drag the start point of the **Guess Correct** transition and drop it back onto the bottom of the **Enter Guess** state.</span></span> <span data-ttu-id="7ca37-166">Geçişi oluşturduktan sonra iş akışı tasarımcısında seçin ve **DisplayName** özelliğini **tahmin yanlış**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7ca37-166">After creating the transition, select it in the workflow designer and set its **DisplayName** property to **Guess Incorrect**.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="7ca37-167">Paylaşılan geçişler, geçiş Tasarımcısı ' nın altında **Paylaşılan tetikleyici geçişi ekle** ' ye tıklayıp, ardından **bağlantı kurmak için kullanılabilir durumlar** ' da istenen hedef durumu seçilerek geçiş Tasarımcısı içinden da oluşturulabilir açılır liste.</span><span class="sxs-lookup"><span data-stu-id="7ca37-167">Shared transitions can also be created from within the transition designer by clicking **Add shared trigger transition** at the bottom of the transition designer, and then selecting the desired target state from the **Available states to connect** drop-down.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="7ca37-168">Bir geçiş `false` `false`işleminin (veya paylaşılan bir tetikleyici geçişinin tüm koşullarını değerlendirmesi) değerlendirilirse, geçişin gerçekleşmeyeceğini ve durumdan gelen tüm geçişler için tüm tetikleyicilerinin olacağını unutmayın. <xref:System.Activities.Statements.Transition.Condition%2A> zamanlandı.</span><span class="sxs-lookup"><span data-stu-id="7ca37-168">Note that if the <xref:System.Activities.Statements.Transition.Condition%2A> of a transition evaluates to `false` (or all of the conditions of a shared trigger transition evaluate to `false`), the transition will not occur and all triggers for all the transitions from the state will be rescheduled.</span></span> <span data-ttu-id="7ca37-169">Bu öğreticide, koşulların yapılandırıldığı şekilde bu durum gerçekleşmemelidir (tahminin doğru veya hatalı olması için özel eylemlerdir).</span><span class="sxs-lookup"><span data-stu-id="7ca37-169">In this tutorial, this situation cannot happen because of the way the conditions are configured (we have specific actions for whether the guess is correct or incorrect).</span></span>  
  
20. <span data-ttu-id="7ca37-170">İş akışı tasarımcısında **tahmin yanlış** geçişine çift tıklayarak genişletin.</span><span class="sxs-lookup"><span data-stu-id="7ca37-170">Double-click the **Guess Incorrect** transition in the workflow designer to expand it.</span></span> <span data-ttu-id="7ca37-171">**Tetikleyicinin** , **tahmin doğru** geçişi tarafından kullanılan **readInt** etkinliğine zaten ayarlanmış olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="7ca37-171">Note that the **Trigger** is already set to the same **ReadInt** activity that was used by the **Guess Correct** transition.</span></span>  
  
21. <span data-ttu-id="7ca37-172">**Koşul** özelliği değeri kutusuna aşağıdaki ifadeyi yazın.</span><span class="sxs-lookup"><span data-stu-id="7ca37-172">Type the following expression into the **Condition** property value box.</span></span>  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
22. <span data-ttu-id="7ca37-173">**Araç kutusunun** **Denetim akışı** bölümünden bir **IF** etkinliği sürükleyin ve geçişin **eylem** bölümüne bırakın.</span><span class="sxs-lookup"><span data-stu-id="7ca37-173">Drag an **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Action** section of the transition.</span></span>  
  
23. <span data-ttu-id="7ca37-174">**IF** etkinliğinin **koşul** özelliği değeri kutusuna aşağıdaki ifadeyi yazın.</span><span class="sxs-lookup"><span data-stu-id="7ca37-174">Type the following expression into the **If** activity’s **Condition** property value box.</span></span>  
  
    ```
    Guess < Target  
    ```  
  
24. <span data-ttu-id="7ca37-175">**Araç kutusu** ' **nu** **temel elemanlar** bölümünden iki **WriteLine** etkinliği sürükleyin ve bir tane, bir diğeri **ise** **Else** bölümünde olacak şekilde bırakın.</span><span class="sxs-lookup"><span data-stu-id="7ca37-175">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that one is in the **Then** section of the **If** activity, and one is in the **Else** section.</span></span>  
  
25. <span data-ttu-id="7ca37-176">**Daha sonra** seçmek Için bölümünde **WriteLine** etkinliğine tıklayın ve **metin** özelliği değeri kutusuna aşağıdaki ifadeyi yazın.</span><span class="sxs-lookup"><span data-stu-id="7ca37-176">Click the **WriteLine** activity in the **Then** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```
    "Your guess is too low."  
    ```  
  
26. <span data-ttu-id="7ca37-177">Bunu seçmek için **Else** bölümünde **WriteLine** etkinliğine tıklayın ve **metin** özelliği değeri kutusuna aşağıdaki ifadeyi yazın.</span><span class="sxs-lookup"><span data-stu-id="7ca37-177">Click the **WriteLine** activity in the **Else** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```
    "Your guess is too high."  
    ```  
  
27. <span data-ttu-id="7ca37-178">İş akışı Tasarımcısı ' nın en üstünde bulunan içerik haritası ' nda **StateMachine** ' e tıklayarak iş akışı tasarımcısında genel durum makinesi görünümüne geri dönün.</span><span class="sxs-lookup"><span data-stu-id="7ca37-178">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
     <span data-ttu-id="7ca37-179">Aşağıdaki örnekte tamamlanan iş akışı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7ca37-179">The following example illustrates the completed workflow.</span></span>  
  
     ![Tamamlanan durum makinesi iş akışını gösteren çizim.](./media/how-to-create-a-state-machine-workflow/complete-state-machine-workflow.jpg)  
  
### <a name="to-build-the-workflow"></a><span data-ttu-id="7ca37-181">İş akışını derlemek için</span><span class="sxs-lookup"><span data-stu-id="7ca37-181">To build the workflow</span></span>  
  
1. <span data-ttu-id="7ca37-182">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="7ca37-182">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="7ca37-183">İş akışının nasıl çalıştırılacağı hakkında yönergeler için lütfen sonraki konuya [bakın: Bir Iş akışı](how-to-run-a-workflow.md)çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7ca37-183">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span> <span data-ttu-id="7ca37-184">' Nin [nasıl yapılacağını zaten tamamladıysanız: Farklı bir iş](how-to-run-a-workflow.md) akışı stiliyle iş akışı adımı çalıştırın ve bu adımda durum makinesi iş akışını kullanarak çalıştırmak istiyorsanız, [](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) [nasıl yapılır: Bir Iş akışı](how-to-run-a-workflow.md)çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7ca37-184">If you have already completed the [How to: Run a Workflow](how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the state machine workflow from this step, skip ahead to the [To build and run the application](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ca37-185">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ca37-185">See also</span></span>

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [<span data-ttu-id="7ca37-186">Windows Workflow Foundation Programlama</span><span class="sxs-lookup"><span data-stu-id="7ca37-186">Windows Workflow Foundation Programming</span></span>](programming.md)
- [<span data-ttu-id="7ca37-187">İş Akışları Tasarlama</span><span class="sxs-lookup"><span data-stu-id="7ca37-187">Designing Workflows</span></span>](designing-workflows.md)
- [<span data-ttu-id="7ca37-188">Başlangıç Öğreticisi</span><span class="sxs-lookup"><span data-stu-id="7ca37-188">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="7ca37-189">Nasıl yapılır: Etkinlik oluşturma</span><span class="sxs-lookup"><span data-stu-id="7ca37-189">How to: Create an Activity</span></span>](how-to-create-an-activity.md)
- [<span data-ttu-id="7ca37-190">Nasıl yapılır: Iş akışı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="7ca37-190">How to: Run a Workflow</span></span>](how-to-run-a-workflow.md)
