---
title: 'Nasıl yapılır: Durum Makinesi İş Akışı Oluşturma'
description: Bu makale, StateMachine etkinliği ve özel etkinlikler gibi yerleşik etkinlikleri kullanan bir iş akışı oluşturur.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3ec60e8f-fad4-493e-a426-e7962d7aee8c
ms.openlocfilehash: 8a9342c07c15d65df0310c0cb35b4b2c6f2ba686
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419661"
---
# <a name="how-to-create-a-state-machine-workflow"></a><span data-ttu-id="74c6b-103">Nasıl yapılır: Durum Makinesi İş Akışı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="74c6b-103">How to: Create a State Machine Workflow</span></span>
<span data-ttu-id="74c6b-104">İş akışları, yerleşik etkinliklerin yanı sıra özel etkinliklerden de oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="74c6b-104">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="74c6b-105">Bu konu, etkinlik gibi yerleşik etkinlikleri <xref:System.Activities.Statements.StateMachine> ve önceki [nasıl yapılır: etkinlik oluşturma](how-to-create-an-activity.md) konusunun özel etkinliklerini kullanan bir iş akışı oluşturmaya yönelik adımları açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="74c6b-105">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.StateMachine> activity, and the custom activities from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="74c6b-106">İş akışı, sayıyı tahmin eden bir oyunu modelleyen.</span><span class="sxs-lookup"><span data-stu-id="74c6b-106">The workflow models a number guessing game.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="74c6b-107">Başlangıç öğreticisindeki her konu, önceki konulara bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="74c6b-107">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="74c6b-108">Bu konuyu tamamlayabilmeniz için öncelikle [nasıl yapılır: etkinlik oluşturma](how-to-create-an-activity.md)' yı tamamlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="74c6b-108">To complete this topic, you must first complete [How to: Create an Activity](how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="74c6b-109">Öğreticinin tamamlanmış bir sürümünü indirmek için, bkz. [Windows Workflow Foundation (WF45)-Başlangıç Öğreticisi](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="74c6b-109">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-workflow"></a><span data-ttu-id="74c6b-110">İş akışını oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="74c6b-110">To create the workflow</span></span>  
  
1. <span data-ttu-id="74c6b-111">**Çözüm Gezgini** 'de **NumberGuessWorkflowActivities** öğesine sağ tıklayın ve **Ekle**, **Yeni öğe**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="74c6b-111">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>  
  
2. <span data-ttu-id="74c6b-112">**Yüklü**, **ortak öğeler** düğümünde **iş akışı**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="74c6b-112">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="74c6b-113">**Iş akışı** listesinden **etkinlik** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="74c6b-113">Select **Activity** from the **Workflow** list.</span></span>  
  
3. <span data-ttu-id="74c6b-114">`StateMachineNumberGuessWorkflow` **Ad** kutusuna yazın ve **Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="74c6b-114">Type `StateMachineNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>  
  
4. <span data-ttu-id="74c6b-115">**Araç kutusunun** **durum makinesi** ' nden bir **StateMachine** etkinliğini sürükleyin ve iş akışı tasarım yüzeyinde **buraya bırakma etkinliği** etiketini bırakın.</span><span class="sxs-lookup"><span data-stu-id="74c6b-115">Drag a **StateMachine** activity from the **State Machine** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="74c6b-116">İş akışı değişkenlerini ve bağımsız değişkenleri oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="74c6b-116">To create the workflow variables and arguments</span></span>  
  
1. <span data-ttu-id="74c6b-117">Henüz görüntülenmiyorsa, iş akışını tasarımcıda göstermek için **Çözüm Gezgini** Içindeki **StateMachineNumberGuessWorkflow. xaml** öğesine çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="74c6b-117">Double-click **StateMachineNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>  
  
2. <span data-ttu-id="74c6b-118">**Bağımsız değişkenler** bölmesini göstermek için iş akışı Tasarımcısı ' nın sol alt tarafındaki **bağımsız değişkenler** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="74c6b-118">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
3. <span data-ttu-id="74c6b-119">**Bağımsız değişken Oluştur**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="74c6b-119">Click **Create Argument**.</span></span>  
  
4. <span data-ttu-id="74c6b-120">`MaxNumber` **Ad** kutusuna yazın, **Yön** açılan listesinden **'** i seçin, **bağımsız değişken türü** açılan listesinden **ıNT32** ' i seçin ve ardından bağımsız değişkeni kaydetmek için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="74c6b-120">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
5. <span data-ttu-id="74c6b-121">**Bağımsız değişken Oluştur**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="74c6b-121">Click **Create Argument**.</span></span>  
  
6. <span data-ttu-id="74c6b-122">`Turns`Yeni eklenen bağımsız değişkenin altında bulunan **ad** kutusuna yazın `MaxNumber` , **Yön** açılan listesinden Seç **Out** ' i seçin, **bağımsız değişken türü** açılan listesinden **Int32** ' i seçin ve ardından ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="74c6b-122">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
7. <span data-ttu-id="74c6b-123">**Bağımsız değişkenler** bölmesini kapatmak için etkinlik tasarımcısının sol alt tarafındaki **bağımsız değişkenler** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="74c6b-123">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
8. <span data-ttu-id="74c6b-124">**Değişkenler** bölmesini göstermek için iş akışı Tasarımcısı ' nın sol alt tarafındaki **değişkenler** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="74c6b-124">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>  
  
9. <span data-ttu-id="74c6b-125">**Değişken Oluştur**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="74c6b-125">Click **Create Variable**.</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="74c6b-126">**Değişken Oluştur** kutusu görüntülenmiyorsa, <xref:System.Activities.Statements.StateMachine> iş akışı Tasarımcısı yüzeyinde etkinlik ' i tıklatarak seçin.</span><span class="sxs-lookup"><span data-stu-id="74c6b-126">If no **Create Variable** box is displayed, click the <xref:System.Activities.Statements.StateMachine> activity on the workflow designer surface to select it.</span></span>  
  
10. <span data-ttu-id="74c6b-127">`Guess` **Ad** kutusuna yazın, **değişken türü** açılır listesinden **Int32** ' i seçin ve ardından değişkeni kaydetmek için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="74c6b-127">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
11. <span data-ttu-id="74c6b-128">**Değişken Oluştur**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="74c6b-128">Click **Create Variable**.</span></span>  
  
12. <span data-ttu-id="74c6b-129">`Target` **Ad** kutusuna yazın, **değişken türü** açılır listesinden **Int32** ' i seçin ve ardından değişkeni kaydetmek için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="74c6b-129">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
13. <span data-ttu-id="74c6b-130">**Değişkenler** bölmesini kapatmak için etkinlik tasarımcısının sol alt tarafındaki **değişkenler** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="74c6b-130">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>  
  
### <a name="to-add-the-workflow-activities"></a><span data-ttu-id="74c6b-131">İş akışı etkinliklerini eklemek için</span><span class="sxs-lookup"><span data-stu-id="74c6b-131">To add the workflow activities</span></span>  
  
1. <span data-ttu-id="74c6b-132">Seçmek için **State1** öğesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="74c6b-132">Click **State1** to select it.</span></span> <span data-ttu-id="74c6b-133">**Özellikler penceresinde** **DisplayName** olarak değiştirin `Initialize Target` .</span><span class="sxs-lookup"><span data-stu-id="74c6b-133">In the **Properties Window**, change the **DisplayName** to `Initialize Target`.</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="74c6b-134">**Özellikler penceresi** görüntülenmiyorsa, **Görünüm** menüsünden **Özellikler penceresi** ' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="74c6b-134">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
2. <span data-ttu-id="74c6b-135">İş akışı tasarımcısında yeni yeniden adlandırılmış **başlatma hedefini** açmak için çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="74c6b-135">Double-click the newly renamed **Initialize Target** state in the workflow designer to expand it.</span></span>  
  
3. <span data-ttu-id="74c6b-136">**Araç kutusunun** **temel öğeler** bölümünden bir **atama** etkinliği sürükleyin ve durumun **giriş** bölümüne bırakın.</span><span class="sxs-lookup"><span data-stu-id="74c6b-136">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Entry** section of the state.</span></span> <span data-ttu-id="74c6b-137">`Target` **Bir C# ifadesi girin** veya bir **vb ifadesi girin** kutusuna **to** kutusuna ve aşağıdaki ifadeye yazın.</span><span class="sxs-lookup"><span data-stu-id="74c6b-137">Type `Target` into the **To** box and the following expression into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    > <span data-ttu-id="74c6b-138">**Araç kutusu** penceresi görüntülenmiyorsa, **Görünüm** menüsünden **araç kutusu** ' nu seçin.</span><span class="sxs-lookup"><span data-stu-id="74c6b-138">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
4. <span data-ttu-id="74c6b-139">İş akışı Tasarımcısı ' nın en üstünde bulunan içerik haritası ' nda **StateMachine** ' e tıklayarak iş akışı tasarımcısında genel durum makinesi görünümüne geri dönün.</span><span class="sxs-lookup"><span data-stu-id="74c6b-139">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
5. <span data-ttu-id="74c6b-140">**Araç kutusunun** **durum makinesi** bölümünden bir **durum** etkinliğini, Iş akışı tasarımcısına sürükleyin ve **hedefi başlatma** durumuna getirin.</span><span class="sxs-lookup"><span data-stu-id="74c6b-140">Drag a **State** activity from the **State Machine** section of the **Toolbox** onto the workflow designer and hover it over the **Initialize Target** state.</span></span> <span data-ttu-id="74c6b-141">Yeni durum bunun üzerinde olduğunda, **hedefi Başlat** durumunun etrafında dört üçgenin görüneceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="74c6b-141">Note that four triangles will appear around the **Initialize Target** state when the new state is over it.</span></span> <span data-ttu-id="74c6b-142">Yeni durumu, **başlatma hedefi** durumunun hemen altındaki üçgende bırakın.</span><span class="sxs-lookup"><span data-stu-id="74c6b-142">Drop the new state on the triangle that is immediately below the **Initialize Target** state.</span></span> <span data-ttu-id="74c6b-143">Bu, yeni durumu iş akışına koyar ve **hedef başlatma** durumundan yeni duruma bir geçiş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="74c6b-143">This places the new state onto the workflow and creates a transition from the **Initialize Target** state to the new state.</span></span>  
  
6. <span data-ttu-id="74c6b-144">Seçmek için **State1** ' e tıklayın, **DisplayName** olarak değiştirin `Enter Guess` ve ardından iş akışı tasarımcısında duruma çift tıklayarak genişletin.</span><span class="sxs-lookup"><span data-stu-id="74c6b-144">Click **State1** to select it, change the **DisplayName** to `Enter Guess`, and then double-click the state in the workflow designer to expand it.</span></span>  
  
7. <span data-ttu-id="74c6b-145">**Araç kutusunun** **temel öğeler** bölümünden bir **WriteLine** etkinliği sürükleyin ve durumun **giriş** bölümüne bırakın.</span><span class="sxs-lookup"><span data-stu-id="74c6b-145">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Entry** section of the state.</span></span>  
  
8. <span data-ttu-id="74c6b-146">**WriteLine**'ın **Text** özellik kutusuna aşağıdaki ifadeyi yazın.</span><span class="sxs-lookup"><span data-stu-id="74c6b-146">Type the following expression into the **Text** property box of the **WriteLine**.</span></span>  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
9. <span data-ttu-id="74c6b-147">**Araç kutusu** ' nu **temel elemanlar** bölümünden bir **atama** etkinliği sürükleyin ve durumun **Çıkış** bölümüne bırakın.</span><span class="sxs-lookup"><span data-stu-id="74c6b-147">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop onto the **Exit** section of the state.</span></span>  
  
10. <span data-ttu-id="74c6b-148">`Turns` **To** kutusuna ve `Turns + 1` **bir C# IFADESI girin** veya **bir vb ifadesi kutusu girin** .</span><span class="sxs-lookup"><span data-stu-id="74c6b-148">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
11. <span data-ttu-id="74c6b-149">İş akışı Tasarımcısı ' nın en üstünde bulunan içerik haritası ' nda **StateMachine** ' e tıklayarak iş akışı tasarımcısında genel durum makinesi görünümüne geri dönün.</span><span class="sxs-lookup"><span data-stu-id="74c6b-149">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
12. <span data-ttu-id="74c6b-150">**Araç kutusunun** **durum makinesi** ' nden bir **FinalState** etkinliği sürükleyin **, tahmin etme** durumunun üzerine gelin ve **tahmin ve** **sonlandırmasız**değer arasında bir geçiş oluşturulacak şekilde, **tahmin durumu gir** ' in sağında görüntülenen üçgenin üzerine bırakın.</span><span class="sxs-lookup"><span data-stu-id="74c6b-150">Drag a **FinalState** activity from the **State Machine** section of the **Toolbox**, hover it over the **Enter Guess** state, and drop it onto the triangle that appears to the right of the **Enter Guess** state so that a transition is created between **Enter Guess** and **FinalState**.</span></span>  
  
13. <span data-ttu-id="74c6b-151">Geçişin varsayılan adı **T2**'dir.</span><span class="sxs-lookup"><span data-stu-id="74c6b-151">The default name of the transition is **T2**.</span></span> <span data-ttu-id="74c6b-152">İş akışı tasarımcısında geçişe tıklayarak seçin ve **DisplayName** değerini **tahmin**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="74c6b-152">Click the transition in the workflow designer to select it, and set its **DisplayName** to **Guess Correct**.</span></span> <span data-ttu-id="74c6b-153">Ardından, **sonlandırıdurumu**' na tıklayıp seçin ve tam geçiş adının iki durumdan birinin üzerine bulunmadığından görüntülenecek bir oda olması için sağa sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="74c6b-153">Then click and select the **FinalState**, and drag it to the right so that there is room for the full transition name to be displayed without overlaying either of the two states.</span></span> <span data-ttu-id="74c6b-154">Bu, öğreticideki kalan adımların tamamlanmasını daha kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="74c6b-154">This will make it easier to complete the remaining steps in the tutorial.</span></span>  
  
14. <span data-ttu-id="74c6b-155">İş akışı tasarımcısında yeni yeniden adlandırılmış **tahmin doğru** geçişine çift tıklayarak genişletin.</span><span class="sxs-lookup"><span data-stu-id="74c6b-155">Double-click the newly renamed **Guess Correct** transition in the workflow designer to expand it.</span></span>  
  
15. <span data-ttu-id="74c6b-156">**Araç kutusunun** **NumberGuessWorkflowActivities** bölümünden **readInt** etkinliğini sürükleyin ve geçişin **tetikleyici** bölümüne bırakın.</span><span class="sxs-lookup"><span data-stu-id="74c6b-156">Drag a **ReadInt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **Trigger** section of the transition.</span></span>  
  
16. <span data-ttu-id="74c6b-157">**ReadInt** etkinliğinin **Özellikler penceresinde** , `"EnterGuess"` tırnak işareti **adı** Özellik değeri kutusuna tırnak işareti dahil yazın ve `Guess` **sonuç** özelliği değeri kutusuna yazın</span><span class="sxs-lookup"><span data-stu-id="74c6b-157">In the **Properties Window** for the **ReadInt** activity, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box, and type `Guess` into the **Result** property value box</span></span>  
  
17. <span data-ttu-id="74c6b-158">**Tahmin doğru** geçişinin **koşul** özelliği değeri kutusuna aşağıdaki ifadeyi yazın.</span><span class="sxs-lookup"><span data-stu-id="74c6b-158">Type the following expression into the **Guess Correct** transition’s **Condition** property value box.</span></span>  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
18. <span data-ttu-id="74c6b-159">İş akışı Tasarımcısı ' nın en üstünde bulunan içerik haritası ' nda **StateMachine** ' e tıklayarak iş akışı tasarımcısında genel durum makinesi görünümüne geri dönün.</span><span class="sxs-lookup"><span data-stu-id="74c6b-159">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="74c6b-160">Tetikleyici olayı alındığında ve varsa, olarak değerlendirilen bir geçiş gerçekleşir <xref:System.Activities.Statements.Transition.Condition%2A> `True` .</span><span class="sxs-lookup"><span data-stu-id="74c6b-160">A transition occurs when the trigger event is received and the <xref:System.Activities.Statements.Transition.Condition%2A>, if present, evaluates to `True`.</span></span> <span data-ttu-id="74c6b-161">Bu geçiş için, Kullanıcı `Guess` rastgele oluşturulmuş ile eşleşiyorsa `Target` Denetim **sonlandırna** geçer ve iş akışı tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="74c6b-161">For this transition, if the user’s `Guess` matches the randomly generated `Target`, then control passes to the **FinalState** and the workflow completes.</span></span>  
  
19. <span data-ttu-id="74c6b-162">Tahminin doğru olup olmadığına bağlı olarak, iş akışı, başka bir TRY için **FinalState** 'e ya da tahmin durumuna **gir** 'e geçiş yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="74c6b-162">Depending on whether the guess is correct, the workflow should transition either to the **FinalState** or back to the **Enter Guess** state for another try.</span></span> <span data-ttu-id="74c6b-163">Her iki geçiş de, kullanıcının tahminin **readInt** etkinliği aracılığıyla alınması için bekleyen tetikleyiciyi paylaşır.</span><span class="sxs-lookup"><span data-stu-id="74c6b-163">Both transitions share the same trigger of waiting for the user’s guess to be received via the **ReadInt** activity.</span></span> <span data-ttu-id="74c6b-164">Buna paylaşılan geçiş adı verilir.</span><span class="sxs-lookup"><span data-stu-id="74c6b-164">This is called a shared transition.</span></span> <span data-ttu-id="74c6b-165">Paylaşılan bir geçiş oluşturmak için, **tahmin doğru** geçişinin başlangıcını belirten daireye tıklayın ve istediğiniz duruma sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="74c6b-165">To create a shared transition, click the circle that indicates the start of the **Guess Correct** transition and drag it to the desired state.</span></span> <span data-ttu-id="74c6b-166">Bu durumda, geçiş bir kendinden geçiştir, bu nedenle **tahmin doğru** geçişinin başlangıç noktasını sürükleyin ve **tahmin** durumunun sonuna geri bırakın.</span><span class="sxs-lookup"><span data-stu-id="74c6b-166">In this case the transition is a self-transition, so drag the start point of the **Guess Correct** transition and drop it back onto the bottom of the **Enter Guess** state.</span></span> <span data-ttu-id="74c6b-167">Geçişi oluşturduktan sonra iş akışı tasarımcısında seçin ve **DisplayName** özelliğini **tahmin yanlış**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="74c6b-167">After creating the transition, select it in the workflow designer and set its **DisplayName** property to **Guess Incorrect**.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="74c6b-168">Paylaşılan geçişler, geçiş Tasarımcısı ' nın altında **Paylaşılan tetikleyici geçişi ekle** ' ye tıklayarak geçiş Tasarımcısı içinden de oluşturulabilir ve sonra, bağlantı açılan listesinden, **kullanılabilir durumlar** ' da istenen hedef durumu seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74c6b-168">Shared transitions can also be created from within the transition designer by clicking **Add shared trigger transition** at the bottom of the transition designer, and then selecting the desired target state from the **Available states to connect** drop-down.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="74c6b-169"><xref:System.Activities.Statements.Transition.Condition%2A>Bir geçiş işleminin `false` (veya paylaşılan bir tetikleyici geçişinin tüm koşullarını değerlendirmesi `false` ) değerlendirilirse, geçişin gerçekleşmeyeceğini ve durumdan gelen tüm geçişlerin her tetikleyicisinin yeniden planlanacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="74c6b-169">Note that if the <xref:System.Activities.Statements.Transition.Condition%2A> of a transition evaluates to `false` (or all of the conditions of a shared trigger transition evaluate to `false`), the transition will not occur and all triggers for all the transitions from the state will be rescheduled.</span></span> <span data-ttu-id="74c6b-170">Bu öğreticide, koşulların yapılandırıldığı şekilde bu durum gerçekleşmemelidir (tahminin doğru veya hatalı olması için özel eylemlerdir).</span><span class="sxs-lookup"><span data-stu-id="74c6b-170">In this tutorial, this situation cannot happen because of the way the conditions are configured (we have specific actions for whether the guess is correct or incorrect).</span></span>  
  
20. <span data-ttu-id="74c6b-171">İş akışı tasarımcısında **tahmin yanlış** geçişine çift tıklayarak genişletin.</span><span class="sxs-lookup"><span data-stu-id="74c6b-171">Double-click the **Guess Incorrect** transition in the workflow designer to expand it.</span></span> <span data-ttu-id="74c6b-172">**Tetikleyicinin** , **tahmin doğru** geçişi tarafından kullanılan **readInt** etkinliğine zaten ayarlanmış olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="74c6b-172">Note that the **Trigger** is already set to the same **ReadInt** activity that was used by the **Guess Correct** transition.</span></span>  
  
21. <span data-ttu-id="74c6b-173">**Koşul** özelliği değeri kutusuna aşağıdaki ifadeyi yazın.</span><span class="sxs-lookup"><span data-stu-id="74c6b-173">Type the following expression into the **Condition** property value box.</span></span>  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
22. <span data-ttu-id="74c6b-174">**Araç kutusunun** **Denetim akışı** bölümünden bir **IF** etkinliği sürükleyin ve geçişin **eylem** bölümüne bırakın.</span><span class="sxs-lookup"><span data-stu-id="74c6b-174">Drag an **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Action** section of the transition.</span></span>  
  
23. <span data-ttu-id="74c6b-175">**IF** etkinliğinin **koşul** özelliği değeri kutusuna aşağıdaki ifadeyi yazın.</span><span class="sxs-lookup"><span data-stu-id="74c6b-175">Type the following expression into the **If** activity’s **Condition** property value box.</span></span>  
  
    ```text
    Guess < Target
    ```  
  
24. <span data-ttu-id="74c6b-176">**Araç kutusu** ' **nu** **temel elemanlar** bölümünden iki **WriteLine** etkinliği sürükleyin ve bir tane, bir diğeri **ise** **Else** bölümünde olacak şekilde bırakın.</span><span class="sxs-lookup"><span data-stu-id="74c6b-176">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that one is in the **Then** section of the **If** activity, and one is in the **Else** section.</span></span>  
  
25. <span data-ttu-id="74c6b-177">**Daha sonra** seçmek Için bölümünde **WriteLine** etkinliğine tıklayın ve **metin** özelliği değeri kutusuna aşağıdaki ifadeyi yazın.</span><span class="sxs-lookup"><span data-stu-id="74c6b-177">Click the **WriteLine** activity in the **Then** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```text
    "Your guess is too low."  
    ```  
  
26. <span data-ttu-id="74c6b-178">Bunu seçmek için **Else** bölümünde **WriteLine** etkinliğine tıklayın ve **metin** özelliği değeri kutusuna aşağıdaki ifadeyi yazın.</span><span class="sxs-lookup"><span data-stu-id="74c6b-178">Click the **WriteLine** activity in the **Else** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```text
    "Your guess is too high."  
    ```  
  
27. <span data-ttu-id="74c6b-179">İş akışı Tasarımcısı ' nın en üstünde bulunan içerik haritası ' nda **StateMachine** ' e tıklayarak iş akışı tasarımcısında genel durum makinesi görünümüne geri dönün.</span><span class="sxs-lookup"><span data-stu-id="74c6b-179">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
     <span data-ttu-id="74c6b-180">Aşağıdaki örnekte tamamlanan iş akışı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="74c6b-180">The following example illustrates the completed workflow.</span></span>  
  
     ![Tamamlanan durum makinesi iş akışını gösteren çizim.](./media/how-to-create-a-state-machine-workflow/complete-state-machine-workflow.jpg)  
  
### <a name="to-build-the-workflow"></a><span data-ttu-id="74c6b-182">İş akışını derlemek için</span><span class="sxs-lookup"><span data-stu-id="74c6b-182">To build the workflow</span></span>  
  
1. <span data-ttu-id="74c6b-183">Çözümü derlemek için CTRL+SHIFT+B'ye basın.</span><span class="sxs-lookup"><span data-stu-id="74c6b-183">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="74c6b-184">İş akışının nasıl çalıştırılacağı hakkında yönergeler için, bkz. [nasıl yapılır: Iş akışını çalıştırma](how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="74c6b-184">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span> <span data-ttu-id="74c6b-185">[Nasıl yapılır: bir](how-to-run-a-workflow.md) iş akışı adımını farklı bir iş akışı ile çalıştırma ve bu adımdaki durum makinesi iş akışını kullanarak çalıştırmak istediğinizde, nasıl [yapılır: iş akışı çalıştırma](how-to-run-a-workflow.md)konusunun [Uygulama bölümünü derlemek ve çalıştırmak için](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) ' a atlayın.</span><span class="sxs-lookup"><span data-stu-id="74c6b-185">If you have already completed the [How to: Run a Workflow](how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the state machine workflow from this step, skip ahead to the [To build and run the application](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74c6b-186">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="74c6b-186">See also</span></span>

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [<span data-ttu-id="74c6b-187">Windows Workflow Foundation Programlama</span><span class="sxs-lookup"><span data-stu-id="74c6b-187">Windows Workflow Foundation Programming</span></span>](programming.md)
- [<span data-ttu-id="74c6b-188">İş Akışları Tasarlama</span><span class="sxs-lookup"><span data-stu-id="74c6b-188">Designing Workflows</span></span>](designing-workflows.md)
- [<span data-ttu-id="74c6b-189">Başlangıç Öğreticisi</span><span class="sxs-lookup"><span data-stu-id="74c6b-189">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="74c6b-190">Nasıl Yapılır: Etkinlik Oluşturma</span><span class="sxs-lookup"><span data-stu-id="74c6b-190">How to: Create an Activity</span></span>](how-to-create-an-activity.md)
- [<span data-ttu-id="74c6b-191">Nasıl yapılır: İş Akışı Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="74c6b-191">How to: Run a Workflow</span></span>](how-to-run-a-workflow.md)
