---
title: 'Nasıl yapılır: Etkinlik Oluşturma'
description: "Bu makalede, Workflow Foundation 'da iki etkinlik oluşturma gösterilmektedir: bir tane, mantığını uygulamak için kod kullanan ve diğeri diğer etkinlikleri kullanarak tanımlanmış."
ms.date: 09/14/2018
dev_langs:
- csharp
- vb
ms.assetid: c09b1e99-21b5-4d96-9c04-ec31db3f4436
ms.openlocfilehash: c7610d8612eb944afa9c23e1bf2abceeb3a6d38b
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98190773"
---
# <a name="how-to-create-an-activity"></a><span data-ttu-id="b6824-103">Nasıl yapılır: Etkinlik Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b6824-103">How to: Create an Activity</span></span>

<span data-ttu-id="b6824-104">Etkinlikler, içindeki temel davranış birimidir [!INCLUDE[wf1](../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="b6824-104">Activities are the core unit of behavior in [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span></span> <span data-ttu-id="b6824-105">Bir etkinliğin yürütme mantığı yönetilen kodda uygulanabilir veya diğer etkinlikler kullanılarak uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="b6824-105">The execution logic of an activity can be implemented in managed code or it can be implemented by using other activities.</span></span> <span data-ttu-id="b6824-106">Bu konuda, iki etkinliğin nasıl oluşturulacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b6824-106">This topic demonstrates how to create two activities.</span></span> <span data-ttu-id="b6824-107">İlk etkinlik, yürütme mantığını uygulamak için kod kullanan basit bir etkinliktir.</span><span class="sxs-lookup"><span data-stu-id="b6824-107">The first activity is a simple activity that uses code to implement its execution logic.</span></span> <span data-ttu-id="b6824-108">İkinci etkinliğin uygulanması diğer etkinlikler kullanılarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="b6824-108">The implementation of the second activity is defined by using other activities.</span></span> <span data-ttu-id="b6824-109">Bu etkinlikler öğreticideki aşağıdaki adımlarda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b6824-109">These activities are used in following steps in the tutorial.</span></span>

## <a name="create-the-activity-library-project"></a><span data-ttu-id="b6824-110">Etkinlik kitaplığı projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="b6824-110">Create the activity library project</span></span>

1. <span data-ttu-id="b6824-111">Visual Studio 'yu açın ve   >  **Dosya** menüsünden Yeni **Proje** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="b6824-111">Open Visual Studio and choose **New** > **Project** from the **File** menu.</span></span>

2. <span data-ttu-id="b6824-112">**Yeni proje** iletişim kutusunda, **yüklü** kategori altında, **Visual C#**  >  **iş akışı** (veya **Visual Basic**  >  **iş akışı**) öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="b6824-112">In the **New Project** dialog, under the **Installed** category, select **Visual C#** > **Workflow** (or **Visual Basic** > **Workflow**).</span></span>

    > [!NOTE]
    > <span data-ttu-id="b6824-113">**Iş akışı** şablonu kategorisini görmüyorsanız, Visual Studio 'nun **Windows Workflow Foundation** bileşenini yüklemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="b6824-113">If you don't see the **Workflow** template category, you may need to install the **Windows Workflow Foundation** component of Visual Studio.</span></span> <span data-ttu-id="b6824-114">**Yeni proje** iletişim kutusunun sol tarafındaki **Visual Studio yükleyicisi aç** bağlantısını seçin.</span><span class="sxs-lookup"><span data-stu-id="b6824-114">Choose the **Open Visual Studio Installer** link on the left-hand side of the **New Project** dialog.</span></span> <span data-ttu-id="b6824-115">Visual Studio Yükleyicisi, **tek tek bileşenler** sekmesini seçin. Ardından, **geliştirme etkinlikleri** kategorisi altında **Windows Workflow Foundation** bileşenini seçin.</span><span class="sxs-lookup"><span data-stu-id="b6824-115">In Visual Studio Installer, select the **Individual components** tab. Then, under the **Development activities** category, select the **Windows Workflow Foundation** component.</span></span> <span data-ttu-id="b6824-116">Bileşeni yüklemek için **Değiştir** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="b6824-116">Choose **Modify** to install the component.</span></span>

3. <span data-ttu-id="b6824-117">**Etkinlik kitaplığı** proje şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="b6824-117">Select the **Activity Library** project template.</span></span> <span data-ttu-id="b6824-118">`NumberGuessWorkflowActivities` **Ad** kutusuna yazın ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b6824-118">Type `NumberGuessWorkflowActivities` in the **Name** box and then click **OK**.</span></span>

4. <span data-ttu-id="b6824-119">**Çözüm Gezgini** 'de **Activity1. xaml** öğesine sağ tıklayın ve **Sil**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="b6824-119">Right-click **Activity1.xaml** in **Solution Explorer** and choose **Delete**.</span></span> <span data-ttu-id="b6824-120">Onaylamak için **Tamam** ' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="b6824-120">Click **OK** to confirm.</span></span>

## <a name="create-the-readint-activity"></a><span data-ttu-id="b6824-121">ReadInt etkinliğini oluşturma</span><span class="sxs-lookup"><span data-stu-id="b6824-121">Create the ReadInt activity</span></span>

1. <span data-ttu-id="b6824-122">**Proje** menüsünden **Yeni öğe Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="b6824-122">Choose **Add New Item** from the **Project** menu.</span></span>

2. <span data-ttu-id="b6824-123">**Yüklü**  >  **ortak öğeler** düğümünde **iş akışı**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="b6824-123">In the **Installed** > **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="b6824-124">**Iş akışı** listesinden **kod etkinliği** ' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="b6824-124">Select **Code Activity** from the **Workflow** list.</span></span>

3. <span data-ttu-id="b6824-125">`ReadInt` **Ad** kutusuna yazın ve ardından **Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b6824-125">Type `ReadInt` into the **Name** box and then click **Add**.</span></span>

4. <span data-ttu-id="b6824-126">Mevcut `ReadInt` tanımı aşağıdaki tanım ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b6824-126">Replace the existing `ReadInt` definition with the following definition.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#1](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/readint.cs#1)]
     [!code-vb[CFX_WF_GettingStarted#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/readint.vb#1)]

    > [!NOTE]
    > <span data-ttu-id="b6824-127">`ReadInt`Etkinlik, <xref:System.Activities.NativeActivity%601> <xref:System.Activities.CodeActivity> kod etkinlik şablonu için varsayılan olan yerine öğesinden türetilir.</span><span class="sxs-lookup"><span data-stu-id="b6824-127">The `ReadInt` activity derives from <xref:System.Activities.NativeActivity%601> instead of <xref:System.Activities.CodeActivity>, which is the default for the code activity template.</span></span> <span data-ttu-id="b6824-128"><xref:System.Activities.CodeActivity%601> etkinlik bağımsız değişken aracılığıyla ortaya çıkarılan <xref:System.Activities.Activity%601.Result%2A> ancak <xref:System.Activities.CodeActivity%601> yer işaretlerinin kullanımını desteklemeyen tek bir sonuç sağlıyorsa, bu nedenle kullanılır <xref:System.Activities.NativeActivity%601> .</span><span class="sxs-lookup"><span data-stu-id="b6824-128"><xref:System.Activities.CodeActivity%601> can be used if the activity provides a single result, which is exposed through the <xref:System.Activities.Activity%601.Result%2A> argument, but <xref:System.Activities.CodeActivity%601> does not support the use of bookmarks, so <xref:System.Activities.NativeActivity%601> is used.</span></span>

## <a name="create-the-prompt-activity"></a><span data-ttu-id="b6824-129">Istem etkinliğini oluşturma</span><span class="sxs-lookup"><span data-stu-id="b6824-129">Create the Prompt activity</span></span>

1. <span data-ttu-id="b6824-130"> +  + Projeyi derlemek için CTRL SHIFT **B** tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="b6824-130">Press **Ctrl**+**Shift**+**B** to build the project.</span></span> <span data-ttu-id="b6824-131">Projeyi oluşturmak, bu `ReadInt` projedeki etkinliğin özel etkinlik oluşturmak için kullanılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="b6824-131">Building the project enables the `ReadInt` activity in this project to be used to build the custom activity from this step.</span></span>

2. <span data-ttu-id="b6824-132">**Proje** menüsünden **Yeni öğe Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="b6824-132">Choose **Add New Item** from the **Project** menu.</span></span>

3. <span data-ttu-id="b6824-133">**Yüklü**  >  **ortak öğeler** düğümünde **iş akışı**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="b6824-133">In the **Installed** > **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="b6824-134">**Iş akışı** listesinden **etkinlik** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="b6824-134">Select **Activity** from the **Workflow** list.</span></span>

4. <span data-ttu-id="b6824-135">`Prompt` **Ad** kutusuna yazın ve ardından **Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b6824-135">Type `Prompt` into the **Name** box and then click **Add**.</span></span>

5. <span data-ttu-id="b6824-136">Daha önce görüntülenmiyorsa, tasarımcıda göstermek için **Çözüm Gezgini** **. xaml** öğesine çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b6824-136">Double-click **Prompt.xaml** in **Solution Explorer** to display it in the designer if it is not already displayed.</span></span>

6. <span data-ttu-id="b6824-137">**Bağımsız değişkenler** bölmesini göstermek için etkinlik tasarımcısının sol alt tarafındaki **bağımsız değişkenler** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b6824-137">Click **Arguments** in the lower-left side of the activity designer to display the **Arguments** pane.</span></span>

7. <span data-ttu-id="b6824-138">**Bağımsız değişken Oluştur**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b6824-138">Click **Create Argument**.</span></span>

8. <span data-ttu-id="b6824-139">`BookmarkName` **Ad** kutusuna yazın, **Yön** açılan listesinden **'** ı seçin, **bağımsız değişken türü** açılan listesinden **dize** ' yi seçin ve sonra bağımsız değişkeni kaydetmek için **ENTER** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="b6824-139">Type `BookmarkName` into the **Name** box, select **In** from the **Direction** drop-down list, select **String** from the **Argument type** drop-down list, and then press **Enter** to save the argument.</span></span>

9. <span data-ttu-id="b6824-140">**Bağımsız değişken Oluştur**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b6824-140">Click **Create Argument**.</span></span>

10. <span data-ttu-id="b6824-141">`Result`Yeni eklenen bağımsız değişkenin altında bulunan **ad** kutusuna yazın `BookmarkName` , **Yön** açılan listesinden Seç  ' i seçin, **bağımsız değişken türü** açılan listesinden **Int32** ' i seçin ve ardından **ENTER** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="b6824-141">Type `Result` into the **Name** box that is underneath the newly added `BookmarkName` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press **Enter**.</span></span>

11. <span data-ttu-id="b6824-142">**Bağımsız değişken Oluştur**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b6824-142">Click **Create Argument**.</span></span>

12. <span data-ttu-id="b6824-143">`Text` **Ad** kutusuna yazın, **Yön** açılan listesinden **'** ı seçin, **bağımsız değişken türü** açılan listesinden **dize** ' yi seçin ve sonra bağımsız değişkeni kaydetmek için **ENTER** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="b6824-143">Type `Text` into the **Name** box, select **In** from the **Direction** drop-down list, select **String** from the **Argument type** drop-down list, and then press **Enter** to save the argument.</span></span>

     <span data-ttu-id="b6824-144">Bu üç bağımsız değişken, <xref:System.Activities.Statements.WriteLine> `ReadInt` Aşağıdaki adımlarda etkinliğe eklenen ve etkinliklerinin karşılık gelen bağımsız değişkenlerine bağlanır `Prompt` .</span><span class="sxs-lookup"><span data-stu-id="b6824-144">These three arguments are bound to the corresponding arguments of the <xref:System.Activities.Statements.WriteLine> and `ReadInt` activities that are added to the `Prompt` activity in the following steps.</span></span>

13. <span data-ttu-id="b6824-145">**Bağımsız değişkenler** bölmesini kapatmak için etkinlik tasarımcısının sol alt tarafındaki **bağımsız değişkenler** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b6824-145">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>

14. <span data-ttu-id="b6824-146">**Araç kutusunun** **Denetim akışı** bölümünden bir **dizi** etkinliği sürükleyin ve **sor** etkinlik Tasarımcısı ' nın **buradan bırakma etkinliği** etiketine bırakın.</span><span class="sxs-lookup"><span data-stu-id="b6824-146">Drag a **Sequence** activity from the **Control Flow** section of the **Toolbox** and drop it onto the **Drop activity here** label of the **Prompt** activity designer.</span></span>

    > [!TIP]
    > <span data-ttu-id="b6824-147">**Araç kutusu** penceresi görüntülenmiyorsa, **Görünüm** menüsünden **araç kutusu** ' nu seçin.</span><span class="sxs-lookup"><span data-stu-id="b6824-147">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>

15. <span data-ttu-id="b6824-148">**Araç kutusu** ' nu **temel elemanlar** bölümünden bir **WriteLine** etkinliği sürükleyin ve **dizi** etkinliğinin **buraya bırakma etkinliğine** bırakın.</span><span class="sxs-lookup"><span data-stu-id="b6824-148">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Drop activity here** label of the **Sequence** activity.</span></span>

16. <span data-ttu-id="b6824-149">**WriteLine** etkinliğinin **metin** **bağımsız değişkenini,**  `Text` **bir C# ifadesi girin** veya **Özellikler** penceresinde **bir vb ifadesi girin** ve ardından SEKME tuşuna iki kez basın ve ardından **sekme** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="b6824-149">Bind the **Text** argument of the **WriteLine** activity to the **Text** argument of the **Prompt** activity by typing `Text` into the **Enter a C# expression** or **Enter a VB expression** box in the **Properties** window, and then press the **Tab** key two times.</span></span> <span data-ttu-id="b6824-150">Bu, IntelliSense liste üyeleri penceresini devre dışı bırakır ve seçimi özelliğin dışına taşıyarak özellik değerini kaydeder.</span><span class="sxs-lookup"><span data-stu-id="b6824-150">This dismisses the IntelliSense list members window and saves the property value by moving the selection off the property.</span></span> <span data-ttu-id="b6824-151">Bu özellik ayrıca, `Text` **bir C# ifadesi girin** veya etkinliğin kendısı için **bir vb ifadesi** kutusu girerek ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="b6824-151">This property can also be set by typing `Text` into the **Enter a C# expression** or **Enter a VB expression** box on the activity itself.</span></span>

    > [!TIP]
    > <span data-ttu-id="b6824-152">**Özellikler penceresi** görüntülenmiyorsa, **Görünüm** menüsünden **Özellikler penceresi** ' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="b6824-152">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>

17. <span data-ttu-id="b6824-153">**Araç kutusu** 'Nun **NumberGuessWorkflowActivities** bölümünden bir **readInt** etkinliği sürükleyin ve **WriteLine** etkinliğinin ardından onu **sıraya** koyun.</span><span class="sxs-lookup"><span data-stu-id="b6824-153">Drag a **ReadInt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **Sequence** activity so that it follows the **WriteLine** activity.</span></span>

18. <span data-ttu-id="b6824-154">**ReadInt** etkinliğinin **BookmarkName** bağımsız değişkenini,   `BookmarkName` **Özellikler penceresinde** **BookmarkName** bağımsız değişkeninin sağ tarafındaki **bir vb ifadesi girin** kutusuna yazarak istem etkinliğinin BookmarkName bağımsız değişkenine bağlayın ve sonra IntelliSense liste üyeleri penceresini kapatmak ve özelliği kaydetmek için iki kez **Tab** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="b6824-154">Bind the **BookmarkName** argument of the **ReadInt** activity to the **BookmarkName** argument of the **Prompt** activity by typing `BookmarkName` into the **Enter a VB expression** box to the right of the **BookmarkName** argument in the **Properties Window**, and then press the **Tab** key two times to close the IntelliSense list members window and save the property.</span></span>

19. <span data-ttu-id="b6824-155">**ReadInt** etkinliğinin **sonuç** bağımsız değişkenini,   `Result` **Özellikler penceresinde** **sonuç** bağımsız değişkeninin sağ tarafındaki **bir vb ifadesi girin** kutusuna yazarak istem etkinliğinin sonuç bağımsız değişkenine bağlayın ve ardından **sekme** tuşuna iki kez basın.</span><span class="sxs-lookup"><span data-stu-id="b6824-155">Bind the **Result** argument of the **ReadInt** activity to the **Result** argument of the **Prompt** activity by typing `Result` into the **Enter a VB expression** box to the right of the **Result** argument in the **Properties Window**, and then press the **Tab** key two times.</span></span>

20. <span data-ttu-id="b6824-156"> +  + Çözümü derlemek için CTRL SHIFT **B** tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="b6824-156">Press **Ctrl**+**Shift**+**B** to build the solution.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b6824-157">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="b6824-157">Next steps</span></span>

<span data-ttu-id="b6824-158">Bu etkinlikleri kullanarak iş akışı oluşturma yönergeleri için bkz. öğreticideki bir sonraki adım, [nasıl yapılır: Iş akışı oluşturma](how-to-create-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="b6824-158">For instructions on how to create a workflow by using these activities, see the next step in the tutorial, [How to: Create a Workflow](how-to-create-a-workflow.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b6824-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b6824-159">See also</span></span>

- <xref:System.Activities.CodeActivity>
- <xref:System.Activities.NativeActivity%601>
- [<span data-ttu-id="b6824-160">Özel Etkinlikler Tasarlama ve Uygulama</span><span class="sxs-lookup"><span data-stu-id="b6824-160">Designing and Implementing Custom Activities</span></span>](designing-and-implementing-custom-activities.md)
- [<span data-ttu-id="b6824-161">Başlangıç Öğreticisi</span><span class="sxs-lookup"><span data-stu-id="b6824-161">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="b6824-162">Nasıl yapılır: İş Akışı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b6824-162">How to: Create a Workflow</span></span>](how-to-create-a-workflow.md)
- [<span data-ttu-id="b6824-163">Özel Etkinlik Tasarımcısında ExpressionTextBox Kullanma</span><span class="sxs-lookup"><span data-stu-id="b6824-163">Using the ExpressionTextBox in a Custom Activity Designer</span></span>](./samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)
