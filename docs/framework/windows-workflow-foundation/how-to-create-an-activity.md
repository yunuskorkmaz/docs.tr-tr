---
title: 'Nasıl yapılır: Bir etkinlik oluşturma'
ms.date: 09/14/2018
dev_langs:
- csharp
- vb
ms.assetid: c09b1e99-21b5-4d96-9c04-ec31db3f4436
ms.openlocfilehash: 271f26888e8b140b64464f5c9c4eabb7170afe05
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57709024"
---
# <a name="how-to-create-an-activity"></a><span data-ttu-id="1981d-102">Nasıl yapılır: Bir etkinlik oluşturma</span><span class="sxs-lookup"><span data-stu-id="1981d-102">How to: Create an Activity</span></span>

<span data-ttu-id="1981d-103">Etkinlikleri olan çekirdek birimi davranış [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1981d-103">Activities are the core unit of behavior in [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span></span> <span data-ttu-id="1981d-104">Bir etkinlik yürütülme mantığı yönetilen kodda uygulanabilir veya diğer etkinlikleri kullanarak uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="1981d-104">The execution logic of an activity can be implemented in managed code or it can be implemented by using other activities.</span></span> <span data-ttu-id="1981d-105">Bu konu, iki etkinliği oluşturma işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="1981d-105">This topic demonstrates how to create two activities.</span></span> <span data-ttu-id="1981d-106">İlk Etkinlik yürütme mantığını uygulamak için kodu kullanan basit bir etkinliktir.</span><span class="sxs-lookup"><span data-stu-id="1981d-106">The first activity is a simple activity that uses code to implement its execution logic.</span></span> <span data-ttu-id="1981d-107">İkinci etkinlik uygulaması, diğer etkinlikleri kullanarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="1981d-107">The implementation of the second activity is defined by using other activities.</span></span> <span data-ttu-id="1981d-108">Bu etkinlikler, aşağıdaki adımlarda öğreticide kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1981d-108">These activities are used in following steps in the tutorial.</span></span>

> [!NOTE]
> <span data-ttu-id="1981d-109">Öğreticinin tamamlanmış bir sürümünü indirmek için bkz [Windows Workflow Foundation (WF45) - başlangıç Öğreticisi](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="1981d-109">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>

## <a name="create-the-activity-library-project"></a><span data-ttu-id="1981d-110">Etkinlik kitaplığı projesi oluşturun</span><span class="sxs-lookup"><span data-stu-id="1981d-110">Create the activity library project</span></span>

1.  <span data-ttu-id="1981d-111">Visual Studio açıp seçin **yeni** > **proje** gelen **dosya** menüsü.</span><span class="sxs-lookup"><span data-stu-id="1981d-111">Open Visual Studio and choose **New** > **Project** from the **File** menu.</span></span>

2.  <span data-ttu-id="1981d-112">İçinde **yeni proje** iletişim altında **yüklü** kategorisi, select **Visual C#** > **iş akışı** (veya **Visual Basic** > **iş akışı**).</span><span class="sxs-lookup"><span data-stu-id="1981d-112">In the **New Project** dialog, under the **Installed** category, select **Visual C#** > **Workflow** (or **Visual Basic** > **Workflow**).</span></span>

    > [!NOTE]
    > <span data-ttu-id="1981d-113">Görmüyorsanız **iş akışı** şablon kategorisi yüklemeniz gerekebilir **Windows Workflow Foundation** Visual Studio bileşen.</span><span class="sxs-lookup"><span data-stu-id="1981d-113">If you don't see the **Workflow** template category, you may need to install the **Windows Workflow Foundation** component of Visual Studio.</span></span> <span data-ttu-id="1981d-114">Seçin **açık Visual Studio yükleyicisi** sol tarafındaki bağlantıyı **yeni proje** iletişim.</span><span class="sxs-lookup"><span data-stu-id="1981d-114">Choose the **Open Visual Studio Installer** link on the left-hand side of the **New Project** dialog.</span></span> <span data-ttu-id="1981d-115">Visual Studio Yükleyicisi'nde seçin **tek tek bileşenler** sekmesi. Ardından, altında **geliştirme etkinliklerini** kategorisi seçin **Windows Workflow Foundation** bileşeni.</span><span class="sxs-lookup"><span data-stu-id="1981d-115">In Visual Studio Installer, select the **Individual components** tab. Then, under the **Development activities** category, select the **Windows Workflow Foundation** component.</span></span> <span data-ttu-id="1981d-116">Seçin **Değiştir** bileşeni.</span><span class="sxs-lookup"><span data-stu-id="1981d-116">Choose **Modify** to install the component.</span></span>

3. <span data-ttu-id="1981d-117">Seçin **etkinlik Kitaplığı** proje şablonu.</span><span class="sxs-lookup"><span data-stu-id="1981d-117">Select the **Activity Library** project template.</span></span> <span data-ttu-id="1981d-118">Tür `NumberGuessWorkflowActivities` içinde **adı** kutusuna ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="1981d-118">Type `NumberGuessWorkflowActivities` in the **Name** box and then click **OK**.</span></span>

4.  <span data-ttu-id="1981d-119">Sağ **gt;activity1.XAML** içinde **Çözüm Gezgini** ve **Sil**.</span><span class="sxs-lookup"><span data-stu-id="1981d-119">Right-click **Activity1.xaml** in **Solution Explorer** and choose **Delete**.</span></span> <span data-ttu-id="1981d-120">Tıklayın **Tamam** onaylamak için.</span><span class="sxs-lookup"><span data-stu-id="1981d-120">Click **OK** to confirm.</span></span>

## <a name="create-the-readint-activity"></a><span data-ttu-id="1981d-121">ReadInt etkinliği oluşturma</span><span class="sxs-lookup"><span data-stu-id="1981d-121">Create the ReadInt activity</span></span>

1.  <span data-ttu-id="1981d-122">Seçin **Yeni Öğe Ekle** gelen **proje** menüsü.</span><span class="sxs-lookup"><span data-stu-id="1981d-122">Choose **Add New Item** from the **Project** menu.</span></span>

2.  <span data-ttu-id="1981d-123">İçinde **yüklü** > **ortak öğeler** düğümünü **iş akışı**.</span><span class="sxs-lookup"><span data-stu-id="1981d-123">In the **Installed** > **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="1981d-124">Seçin **kod etkinliği** gelen **iş akışı** listesi.</span><span class="sxs-lookup"><span data-stu-id="1981d-124">Select **Code Activity** from the **Workflow** list.</span></span>

3.  <span data-ttu-id="1981d-125">Tür `ReadInt` içine **adı** kutusuna ve ardından **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="1981d-125">Type `ReadInt` into the **Name** box and then click **Add**.</span></span>

4.  <span data-ttu-id="1981d-126">Varolan `ReadInt` aşağıdaki tanımını tanımıyla.</span><span class="sxs-lookup"><span data-stu-id="1981d-126">Replace the existing `ReadInt` definition with the following definition.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#1](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/readint.cs#1)]
     [!code-vb[CFX_WF_GettingStarted#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/readint.vb#1)]

    > [!NOTE]
    > <span data-ttu-id="1981d-127">`ReadInt` Etkinlik türetilir <xref:System.Activities.NativeActivity%601> yerine <xref:System.Activities.CodeActivity>, kod etkinlik şablonu için varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="1981d-127">The `ReadInt` activity derives from <xref:System.Activities.NativeActivity%601> instead of <xref:System.Activities.CodeActivity>, which is the default for the code activity template.</span></span> <span data-ttu-id="1981d-128"><xref:System.Activities.CodeActivity%601> Etkinlik aracılığıyla sunulan tek bir sonuç sağlıyorsa kullanılabilir <xref:System.Activities.Activity%601.Result%2A> bağımsız değişkeni, ancak <xref:System.Activities.CodeActivity%601> kullanımı yer işaretleri, bu nedenle desteklemiyor <xref:System.Activities.NativeActivity%601> kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1981d-128"><xref:System.Activities.CodeActivity%601> can be used if the activity provides a single result, which is exposed through the <xref:System.Activities.Activity%601.Result%2A> argument, but <xref:System.Activities.CodeActivity%601> does not support the use of bookmarks, so <xref:System.Activities.NativeActivity%601> is used.</span></span>

## <a name="create-the-prompt-activity"></a><span data-ttu-id="1981d-129">Komut istemi etkinliği oluşturma</span><span class="sxs-lookup"><span data-stu-id="1981d-129">Create the Prompt activity</span></span>

1.  <span data-ttu-id="1981d-130">Tuşuna **Ctrl**+**Shift**+**B** Projeyi derlemek için.</span><span class="sxs-lookup"><span data-stu-id="1981d-130">Press **Ctrl**+**Shift**+**B** to build the project.</span></span> <span data-ttu-id="1981d-131">Proje etkinleştirir oluşturmaya `ReadInt` etkinlik bu projede Bu adımdan özel etkinlik oluşturmak için kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="1981d-131">Building the project enables the `ReadInt` activity in this project to be used to build the custom activity from this step.</span></span>

2.  <span data-ttu-id="1981d-132">Seçin **Yeni Öğe Ekle** gelen **proje** menüsü.</span><span class="sxs-lookup"><span data-stu-id="1981d-132">Choose **Add New Item** from the **Project** menu.</span></span>

3.  <span data-ttu-id="1981d-133">İçinde **yüklü** > **ortak öğeler** düğümünü **iş akışı**.</span><span class="sxs-lookup"><span data-stu-id="1981d-133">In the **Installed** > **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="1981d-134">Seçin **etkinlik** gelen **iş akışı** listesi.</span><span class="sxs-lookup"><span data-stu-id="1981d-134">Select **Activity** from the **Workflow** list.</span></span>

4.  <span data-ttu-id="1981d-135">Tür `Prompt` içine **adı** kutusuna ve ardından **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="1981d-135">Type `Prompt` into the **Name** box and then click **Add**.</span></span>

5.  <span data-ttu-id="1981d-136">Çift **Prompt.xaml** içinde **Çözüm Gezgini** zaten görüntülenmiyorsa, tasarımcıda görüntülenecek.</span><span class="sxs-lookup"><span data-stu-id="1981d-136">Double-click **Prompt.xaml** in **Solution Explorer** to display it in the designer if it is not already displayed.</span></span>

6.  <span data-ttu-id="1981d-137">Tıklayın **bağımsız değişkenleri** sol alt tarafında görüntülenecek etkinlik Tasarımcısı **bağımsız değişkenleri** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="1981d-137">Click **Arguments** in the lower-left side of the activity designer to display the **Arguments** pane.</span></span>

7.  <span data-ttu-id="1981d-138">Tıklayın **bağımsız değişken oluşturma**.</span><span class="sxs-lookup"><span data-stu-id="1981d-138">Click **Create Argument**.</span></span>

8.  <span data-ttu-id="1981d-139">Tür `BookmarkName` içine **adı** kutusunda **içinde** gelen **yönü** aşağı açılan listesinden **dize** gelen**Bağımsız değişken türü** aşağı açılan liste ve ENTER tuşuna **Enter** bağımsız değişkeni kaydetmek için.</span><span class="sxs-lookup"><span data-stu-id="1981d-139">Type `BookmarkName` into the **Name** box, select **In** from the **Direction** drop-down list, select **String** from the **Argument type** drop-down list, and then press **Enter** to save the argument.</span></span>

9. <span data-ttu-id="1981d-140">Tıklayın **bağımsız değişken oluşturma**.</span><span class="sxs-lookup"><span data-stu-id="1981d-140">Click **Create Argument**.</span></span>

10. <span data-ttu-id="1981d-141">Tür `Result` içine **adı** altında yeni eklenen kutusunu `BookmarkName` bağımsız değişkeni, select **kullanıma** gelen **yönü** aşağı açılan listesinde seçin **Int32** gelen **bağımsız değişken türü** aşağı açılan liste ve ENTER tuşuna **Enter**.</span><span class="sxs-lookup"><span data-stu-id="1981d-141">Type `Result` into the **Name** box that is underneath the newly added `BookmarkName` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press **Enter**.</span></span>

11. <span data-ttu-id="1981d-142">Tıklayın **bağımsız değişken oluşturma**.</span><span class="sxs-lookup"><span data-stu-id="1981d-142">Click **Create Argument**.</span></span>

12. <span data-ttu-id="1981d-143">Tür `Text` içine **adı** kutusunda **içinde** gelen **yönü** aşağı açılan listesinden **dize** gelen**Bağımsız değişken türü** aşağı açılan liste ve ENTER tuşuna **Enter** bağımsız değişkeni kaydetmek için.</span><span class="sxs-lookup"><span data-stu-id="1981d-143">Type `Text` into the **Name** box, select **In** from the **Direction** drop-down list, select **String** from the **Argument type** drop-down list, and then press **Enter** to save the argument.</span></span>

     <span data-ttu-id="1981d-144">Bu üç bağımsız değişken için karşılık gelen bağımsız bağlı <xref:System.Activities.Statements.WriteLine> ve `ReadInt` eklenen etkinlikler `Prompt` aşağıdaki adımlarda etkinlik.</span><span class="sxs-lookup"><span data-stu-id="1981d-144">These three arguments are bound to the corresponding arguments of the <xref:System.Activities.Statements.WriteLine> and `ReadInt` activities that are added to the `Prompt` activity in the following steps.</span></span>

13. <span data-ttu-id="1981d-145">Tıklayın **bağımsız değişkenleri** etkinlik Tasarımcısı kapatmak için sol alt tarafında **bağımsız değişkenleri** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="1981d-145">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>

14. <span data-ttu-id="1981d-146">Sürükle bir **dizisi** etkinliğinden **akış denetimi** bölümünü **araç kutusu** üzerine bırakın **Buraya Bırak etkinlik** etiketi **İstemi** etkinlik Tasarımcısı.</span><span class="sxs-lookup"><span data-stu-id="1981d-146">Drag a **Sequence** activity from the **Control Flow** section of the **Toolbox** and drop it onto the **Drop activity here** label of the **Prompt** activity designer.</span></span>

    > [!TIP]
    > <span data-ttu-id="1981d-147">Varsa **araç kutusu** penceresi görüntülenmiyorsa, seçin **araç kutusu** gelen **görünümü** menüsü.</span><span class="sxs-lookup"><span data-stu-id="1981d-147">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>

15. <span data-ttu-id="1981d-148">Sürükle bir **WriteLine** etkinliğinden **Temelleri** bölümünü **araç kutusu** üzerine bırakın **Buraya Bırak etkinlik** etiketi **Dizisi** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="1981d-148">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Drop activity here** label of the **Sequence** activity.</span></span>

16. <span data-ttu-id="1981d-149">Bağlama **metin** bağımsız değişkeni **WriteLine** etkinliğini **metin** bağımsız değişkeni **istemi** yazarak etkinlik `Text` içine **bir C# ifadesi girin** veya **zadejte Výraz jazyka vb.** kutusunda **özellikleri** penceresi ve ENTER tuşuna **sekmesini** iki kez anahtarı.</span><span class="sxs-lookup"><span data-stu-id="1981d-149">Bind the **Text** argument of the **WriteLine** activity to the **Text** argument of the **Prompt** activity by typing `Text` into the **Enter a C# expression** or **Enter a VB expression** box in the **Properties** window, and then press the **Tab** key two times.</span></span> <span data-ttu-id="1981d-150">Bu, IntelliSense listesi üyeleri penceresi kapatılır ve özellik değeri özelliği devre dışı seçim taşıyarak kaydeder.</span><span class="sxs-lookup"><span data-stu-id="1981d-150">This dismisses the IntelliSense list members window and saves the property value by moving the selection off the property.</span></span> <span data-ttu-id="1981d-151">Bu özellik ayrıca yazarak ayarlanabilir `Text` içine **bir C# ifadesi girin** veya **zadejte Výraz jazyka vb.** etkinlik çubuğundaki.</span><span class="sxs-lookup"><span data-stu-id="1981d-151">This property can also be set by typing `Text` into the **Enter a C# expression** or **Enter a VB expression** box on the activity itself.</span></span>

    > [!TIP]
    > <span data-ttu-id="1981d-152">Varsa **Özellikler penceresi** görüntülenen, select değil **Özellikler penceresi** gelen **görünümü** menüsü.</span><span class="sxs-lookup"><span data-stu-id="1981d-152">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>

17. <span data-ttu-id="1981d-153">Sürükleme bir **readInt** etkinliğinden **NumberGuessWorkflowActivities** bölümünü **araç kutusu** sürükleyip **dizisi** Böylece onun etkinlik **WriteLine** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="1981d-153">Drag a **ReadInt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **Sequence** activity so that it follows the **WriteLine** activity.</span></span>

18. <span data-ttu-id="1981d-154">Bağlama **YerİşaretiAdı** bağımsız değişkeni **readInt** etkinliğini **YerİşaretiAdı** bağımsız değişkeni **istemi** yazaraketkinliği`BookmarkName` içine **zadejte Výraz jazyka vb.** kutusunun sağındaki **YerİşaretiAdı** değişkeninde **Özellikler penceresi**ve tuşuna**Sekmesini** anahtar IntelliSense liste üyelerini penceresini kapatın ve özelliğini kaydetmek için iki kez.</span><span class="sxs-lookup"><span data-stu-id="1981d-154">Bind the **BookmarkName** argument of the **ReadInt** activity to the **BookmarkName** argument of the **Prompt** activity by typing `BookmarkName` into the **Enter a VB expression** box to the right of the **BookmarkName** argument in the **Properties Window**, and then press the **Tab** key two times to close the IntelliSense list members window and save the property.</span></span>

19. <span data-ttu-id="1981d-155">Bağlama **sonucu** bağımsız değişkeni **readInt** etkinliğini **sonucu** bağımsız değişkeni **istemi** yazarak etkinlik `Result` içine **zadejte Výraz jazyka vb.** kutusunun sağındaki **sonucu** değişkeninde **Özellikler penceresi**ve tuşuna **sekmesi** anahtar iki kez.</span><span class="sxs-lookup"><span data-stu-id="1981d-155">Bind the **Result** argument of the **ReadInt** activity to the **Result** argument of the **Prompt** activity by typing `Result` into the **Enter a VB expression** box to the right of the **Result** argument in the **Properties Window**, and then press the **Tab** key two times.</span></span>

20. <span data-ttu-id="1981d-156">Tuşuna **Ctrl**+**Shift**+**B** çözümü derlemek için.</span><span class="sxs-lookup"><span data-stu-id="1981d-156">Press **Ctrl**+**Shift**+**B** to build the solution.</span></span>

## <a name="next-steps"></a><span data-ttu-id="1981d-157">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="1981d-157">Next steps</span></span>

<span data-ttu-id="1981d-158">Öğreticide, bir sonraki adım için bkz. Bu etkinlikleri kullanarak bir iş akışı oluşturmak yönergeler [nasıl yapılır: Bir iş akışı oluşturmak](how-to-create-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="1981d-158">For instructions on how to create a workflow by using these activities, see the next step in the tutorial, [How to: Create a Workflow](how-to-create-a-workflow.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1981d-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1981d-159">See also</span></span>

- <xref:System.Activities.CodeActivity>
- <xref:System.Activities.NativeActivity%601>
- [<span data-ttu-id="1981d-160">Özel Etkinlikler Tasarlama ve Uygulama</span><span class="sxs-lookup"><span data-stu-id="1981d-160">Designing and Implementing Custom Activities</span></span>](designing-and-implementing-custom-activities.md)
- [<span data-ttu-id="1981d-161">Başlangıç Öğreticisi</span><span class="sxs-lookup"><span data-stu-id="1981d-161">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="1981d-162">Nasıl yapılır: Bir iş akışı oluşturma</span><span class="sxs-lookup"><span data-stu-id="1981d-162">How to: Create a Workflow</span></span>](how-to-create-a-workflow.md)
- [<span data-ttu-id="1981d-163">Özel Etkinlik Tasarımcısında ExpressionTextBox Kullanma</span><span class="sxs-lookup"><span data-stu-id="1981d-163">Using the ExpressionTextBox in a Custom Activity Designer</span></span>](./samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)