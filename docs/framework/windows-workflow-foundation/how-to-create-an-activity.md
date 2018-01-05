---
title: "Nasıl yapılır: bir etkinlik oluşturmak"
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
ms.assetid: c09b1e99-21b5-4d96-9c04-ec31db3f4436
caps.latest.revision: "39"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4a3b9698d6a060120addff52e6600916a2de19fc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-an-activity"></a><span data-ttu-id="e26a2-102">Nasıl yapılır: bir etkinlik oluşturmak</span><span class="sxs-lookup"><span data-stu-id="e26a2-102">How to: Create an Activity</span></span>
<span data-ttu-id="e26a2-103">Etkinliklerin davranışını çekirdek biriminin olduğundan [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e26a2-103">Activities are the core unit of behavior in [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span></span> <span data-ttu-id="e26a2-104">Yönetilen kodda bir etkinlik yürütme mantığını uygulanabilir veya diğer etkinlikleri kullanarak uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="e26a2-104">The execution logic of an activity can be implemented in managed code or it can be implemented by using other activities.</span></span> <span data-ttu-id="e26a2-105">Bu konuda iki etkinlik oluşturma gösterilir.</span><span class="sxs-lookup"><span data-stu-id="e26a2-105">This topic demonstrates how to create two activities.</span></span> <span data-ttu-id="e26a2-106">İlk etkinlik, yürütme mantığını uygulamak için kod kullanan basit bir etkinliktir.</span><span class="sxs-lookup"><span data-stu-id="e26a2-106">The first activity is a simple activity that uses code to implement its execution logic.</span></span> <span data-ttu-id="e26a2-107">İkinci etkinlik uyarlamasını diğer etkinlikleri kullanarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="e26a2-107">The implementation of the second activity is defined by using other activities.</span></span> <span data-ttu-id="e26a2-108">Bu etkinlikler içindeki adımları izleyerek öğreticide kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e26a2-108">These activities are used in following steps in the tutorial.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e26a2-109">Öğreticinin tamamlanmış bir sürümünü indirmek için bkz: [Windows Workflow Foundation (WF45) - başlangıç Öğreticisi](http://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="e26a2-109">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](http://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-activity-library-project"></a><span data-ttu-id="e26a2-110">Etkinlik kitaplığı projesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e26a2-110">To create the activity library project</span></span>  
  
1.  <span data-ttu-id="e26a2-111">Açık [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] ve **yeni**, **proje** gelen **dosya** menüsü.</span><span class="sxs-lookup"><span data-stu-id="e26a2-111">Open [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] and choose **New**,  **Project** from the **File** menu.</span></span>  
  
2.  <span data-ttu-id="e26a2-112">Genişletme **diğer proje türleri** düğümünde **yüklü**, **şablonları** listesinde ve seçin **Visual Studio çözümleri**.</span><span class="sxs-lookup"><span data-stu-id="e26a2-112">Expand the **Other Project Types** node in the **Installed**, **Templates** list and select **Visual Studio Solutions**.</span></span>  
  
3.  <span data-ttu-id="e26a2-113">Seçin **boş çözüm** gelen **Visual Studio çözümleri** listesi.</span><span class="sxs-lookup"><span data-stu-id="e26a2-113">Select **Blank Solution** from the **Visual Studio Solutions** list.</span></span> <span data-ttu-id="e26a2-114">Emin **.NET Framework 4.5** .NET Framework sürüm aşağı açılan listesinde seçilir.</span><span class="sxs-lookup"><span data-stu-id="e26a2-114">Ensure that **.NET Framework 4.5** is selected in the .NET Framework version drop-down list.</span></span> <span data-ttu-id="e26a2-115">Tür `WF45GettingStartedTutorial` içinde **adı** kutusuna ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="e26a2-115">Type `WF45GettingStartedTutorial` in the **Name** box and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="e26a2-116">Sağ **WF45GettingStartedTutorial** içinde **Çözüm Gezgini** ve **Ekle**, **yeni proje**.</span><span class="sxs-lookup"><span data-stu-id="e26a2-116">Right-click **WF45GettingStartedTutorial** in **Solution Explorer** and choose **Add**, **New Project**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="e26a2-117">Varsa **Çözüm Gezgini** penceresi görüntülenmez, seçin **Çözüm Gezgini** gelen **Görünüm** menüsü.</span><span class="sxs-lookup"><span data-stu-id="e26a2-117">If the **Solution Explorer** window is not displayed, select **Solution Explorer** from the **View** menu.</span></span>  
  
5.  <span data-ttu-id="e26a2-118">İçinde **yüklü** düğümü, select **Visual C#**, **iş akışı** (veya **Visual Basic**, **iş akışı**).</span><span class="sxs-lookup"><span data-stu-id="e26a2-118">In the **Installed** node, select **Visual C#**, **Workflow** (or **Visual Basic**, **Workflow**).</span></span> <span data-ttu-id="e26a2-119">Emin **.NET Framework 4.5** seçildiyse [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] sürüm aşağı açılan listesi.</span><span class="sxs-lookup"><span data-stu-id="e26a2-119">Ensure that **.NET Framework 4.5** is selected in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] version drop-down list.</span></span> <span data-ttu-id="e26a2-120">Seçin **etkinlik Kitaplığı** gelen **iş akışı** listesi.</span><span class="sxs-lookup"><span data-stu-id="e26a2-120">Select **Activity Library** from the **Workflow** list.</span></span> <span data-ttu-id="e26a2-121">Tür `NumberGuessWorkflowActivities` içinde **adı** kutusuna ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="e26a2-121">Type `NumberGuessWorkflowActivities` in the **Name** box and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e26a2-122">Hangi programlama dili bağlı olarak birincil dilinde olarak yapılandırılan [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], **Visual C#** veya **Visual Basic** düğümü altında olabilir **diğer diller**düğümünde **yüklü** düğümü.</span><span class="sxs-lookup"><span data-stu-id="e26a2-122">Depending on which programming language is configured as the primary language in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], the **Visual C#** or **Visual Basic** node may be under the **Other Languages** node in the **Installed** node.</span></span>  
  
6.  <span data-ttu-id="e26a2-123">Sağ **Activity1.xaml** içinde **Çözüm Gezgini** ve **silmek**.</span><span class="sxs-lookup"><span data-stu-id="e26a2-123">Right-click **Activity1.xaml** in **Solution Explorer** and choose **Delete**.</span></span> <span data-ttu-id="e26a2-124">Tıklatın **Tamam** onaylamak için.</span><span class="sxs-lookup"><span data-stu-id="e26a2-124">Click **OK** to confirm.</span></span>  
  
### <a name="to-create-the-readint-activity"></a><span data-ttu-id="e26a2-125">ReadInt etkinlik oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e26a2-125">To create the ReadInt activity</span></span>  
  
1.  <span data-ttu-id="e26a2-126">Seçin **Yeni Öğe Ekle** gelen **proje** menüsü.</span><span class="sxs-lookup"><span data-stu-id="e26a2-126">Choose **Add New Item** from the **Project** menu.</span></span>  
  
2.  <span data-ttu-id="e26a2-127">İçinde **yüklü**, **ortak öğeler** düğümü, select **iş akışı**.</span><span class="sxs-lookup"><span data-stu-id="e26a2-127">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="e26a2-128">Seçin **kodunu aktivite** gelen **iş akışı** listesi.</span><span class="sxs-lookup"><span data-stu-id="e26a2-128">Select **Code Activity** from the **Workflow** list.</span></span>  
  
3.  <span data-ttu-id="e26a2-129">Tür `ReadInt` içine **adı** kutusuna ve ardından **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="e26a2-129">Type `ReadInt` into the **Name** box and then click **Add**.</span></span>  
  
4.  <span data-ttu-id="e26a2-130">Varolan `ReadInt` aşağıdaki tanımını tanımıyla.</span><span class="sxs-lookup"><span data-stu-id="e26a2-130">Replace the existing `ReadInt` definition with the following definition.</span></span>  
  
     [!code-csharp[CFX_WF_GettingStarted#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/readint.cs#1)]
     [!code-vb[CFX_WF_GettingStarted#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/readint.vb#1)]  
  
    > [!NOTE]
    >  <span data-ttu-id="e26a2-131">`ReadInt` Etkinlik türer <xref:System.Activities.NativeActivity%601> yerine <xref:System.Activities.CodeActivity>, kod etkinlik şablonu için varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="e26a2-131">The `ReadInt` activity derives from <xref:System.Activities.NativeActivity%601> instead of <xref:System.Activities.CodeActivity>, which is the default for the code activity template.</span></span> <span data-ttu-id="e26a2-132"><xref:System.Activities.CodeActivity%601>Etkinlik aracılığıyla kullanıma sunulan tek bir sonuç sağlıyorsa kullanılabilir <xref:System.Activities.Activity%601.Result%2A> bağımsız değişkeni, ancak <xref:System.Activities.CodeActivity%601> kullanımı yer işaretleri, bu nedenle desteklemiyor <xref:System.Activities.NativeActivity%601> kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e26a2-132"><xref:System.Activities.CodeActivity%601> can be used if the activity provides a single result, which is exposed through the <xref:System.Activities.Activity%601.Result%2A> argument, but <xref:System.Activities.CodeActivity%601> does not support the use of bookmarks, so <xref:System.Activities.NativeActivity%601> is used.</span></span>  
  
### <a name="to-create-the-prompt-activity"></a><span data-ttu-id="e26a2-133">Komut istemi etkinlik oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e26a2-133">To create the Prompt activity</span></span>  
  
1.  <span data-ttu-id="e26a2-134">Projeyi oluşturmak için CTRL+SHIFT+B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="e26a2-134">Press CTRL+SHIFT+B to build the project.</span></span> <span data-ttu-id="e26a2-135">Proje etkinleştirir oluşturma `ReadInt` etkinlik bu projede bu adımdaki özel etkinlik oluşturmak için kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="e26a2-135">Building the project enables the `ReadInt` activity in this project to be used to build the custom activity from this step.</span></span>  
  
2.  <span data-ttu-id="e26a2-136">Seçin **Yeni Öğe Ekle** gelen **proje** menüsü.</span><span class="sxs-lookup"><span data-stu-id="e26a2-136">Choose **Add New Item** from the **Project** menu.</span></span>  
  
3.  <span data-ttu-id="e26a2-137">İçinde **yüklü**, **ortak öğeler** düğümü, select **iş akışı**.</span><span class="sxs-lookup"><span data-stu-id="e26a2-137">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="e26a2-138">Seçin **etkinlik** gelen **iş akışı** listesi.</span><span class="sxs-lookup"><span data-stu-id="e26a2-138">Select **Activity** from the **Workflow** list.</span></span>  
  
4.  <span data-ttu-id="e26a2-139">Tür `Prompt` içine **adı** kutusuna ve ardından **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="e26a2-139">Type `Prompt` into the **Name** box and then click **Add**.</span></span>  
  
5.  <span data-ttu-id="e26a2-140">Çift **Prompt.xaml** içinde **Çözüm Gezgini** zaten görüntülenmiyorsa, Tasarımcısı'nda görüntülenecek.</span><span class="sxs-lookup"><span data-stu-id="e26a2-140">Double-click **Prompt.xaml** in **Solution Explorer** to display it in the designer if it is not already displayed.</span></span>  
  
6.  <span data-ttu-id="e26a2-141">Tıklatın **bağımsız değişkenleri** görüntülenecek etkinlik Tasarımcısı sol tarafındaki **bağımsız değişkenleri** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="e26a2-141">Click **Arguments** in the lower-left side of the activity designer to display the **Arguments** pane.</span></span>  
  
7.  <span data-ttu-id="e26a2-142">Tıklatın **bağımsız değişkeni oluşturma**.</span><span class="sxs-lookup"><span data-stu-id="e26a2-142">Click **Create Argument**.</span></span>  
  
8.  <span data-ttu-id="e26a2-143">Tür `BookmarkName` içine **adı** kutusunda **içinde** gelen **yönü** aşağı açılan listesinden, **dize** gelen**Bağımsız değişken türü** aşağı açılan liste ve bağımsız değişkeni kaydetmek için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="e26a2-143">Type `BookmarkName` into the **Name** box, select **In** from the **Direction** drop-down list, select **String** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
9. <span data-ttu-id="e26a2-144">Tıklatın **bağımsız değişkeni oluşturma**.</span><span class="sxs-lookup"><span data-stu-id="e26a2-144">Click **Create Argument**.</span></span>  
  
10. <span data-ttu-id="e26a2-145">Türü `Result` içine **adı** altında yeni eklenen kutusuna `BookmarkName` bağımsız değişkeni, select **çıkışı** gelen **yönü** aşağı açılan listesinde, seçin **Int32** gelen **bağımsız değişken türü** aşağı açılan liste ve ENTER tuşuna BASIN.</span><span class="sxs-lookup"><span data-stu-id="e26a2-145">Type `Result` into the **Name** box that is underneath the newly added `BookmarkName` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
11. <span data-ttu-id="e26a2-146">Tıklatın **bağımsız değişkeni oluşturma**.</span><span class="sxs-lookup"><span data-stu-id="e26a2-146">Click **Create Argument**.</span></span>  
  
12. <span data-ttu-id="e26a2-147">Tür `Text` içine **adı** kutusunda **içinde** gelen **yönü** aşağı açılan listesinden, **dize** gelen**Bağımsız değişken türü** aşağı açılan liste ve bağımsız değişkeni kaydetmek için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="e26a2-147">Type `Text` into the **Name** box, select **In** from the **Direction** drop-down list, select **String** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
     <span data-ttu-id="e26a2-148">Bu üç bağımsız değişken için karşılık gelen bağımsız bağlı <xref:System.Activities.Statements.WriteLine> ve `ReadInt` eklenen etkinlikler `Prompt` aşağıdaki adımlarda etkinlik.</span><span class="sxs-lookup"><span data-stu-id="e26a2-148">These three arguments are bound to the corresponding arguments of the <xref:System.Activities.Statements.WriteLine> and `ReadInt` activities that are added to the `Prompt` activity in the following steps.</span></span>  
  
13. <span data-ttu-id="e26a2-149">Tıklatın **bağımsız değişkenleri** kapatmak için etkinlik Tasarımcısı sol tarafındaki **bağımsız değişkenleri** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="e26a2-149">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
14. <span data-ttu-id="e26a2-150">Sürükleme bir **dizisi** etkinliğinden **akış denetimi** bölümünü **araç** ve üzerine bırakın **etkinliğini Drop burada** etiketi **Komut istemi** etkinlik Tasarımcısı.</span><span class="sxs-lookup"><span data-stu-id="e26a2-150">Drag a **Sequence** activity from the **Control Flow** section of the **Toolbox** and drop it onto the **Drop activity here** label of the **Prompt** activity designer.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="e26a2-151">Varsa **araç** penceresi görüntülenmez, seçin **araç** gelen **Görünüm** menüsü.</span><span class="sxs-lookup"><span data-stu-id="e26a2-151">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
15. <span data-ttu-id="e26a2-152">Sürükleme bir **WriteLine** etkinliğinden **Temelleri** bölümünü **araç** ve üzerine bırakın **etkinliğini Drop burada** etiketi **Dizisi** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="e26a2-152">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Drop activity here** label of the **Sequence** activity.</span></span>  
  
16. <span data-ttu-id="e26a2-153">Bağlama **metin** bağımsız değişkeni **WriteLine** etkinliğe **metin** bağımsız değişkeni **komut istemi** yazarak etkinlik `Text` içine **bir C# ifadesi girin** veya **bir VB ifadesi girin** kutusunda **özellikleri** iki kez anahtar penceresi ve ardından SEKME tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="e26a2-153">Bind the **Text** argument of the **WriteLine** activity to the **Text** argument of the **Prompt** activity by typing `Text` into the **Enter a C# expression** or **Enter a VB expression** box in the **Properties** window, and then press the TAB key two times.</span></span> <span data-ttu-id="e26a2-154">Bu, IntelliSense listesi üyeleri penceresini kapatır ve seçim özelliği devre dışı taşıyarak özellik değeri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="e26a2-154">This dismisses the IntelliSense list members window and saves the property value by moving the selection off the property.</span></span> <span data-ttu-id="e26a2-155">Bu özellik yazarak da ayarlanabilir `Text` içine **bir C# ifadesi girin** veya **bir VB ifadesi girin** etkinliğini kutusu.</span><span class="sxs-lookup"><span data-stu-id="e26a2-155">This property can also be set by typing `Text` into the **Enter a C# expression** or **Enter a VB expression** box on the activity itself.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="e26a2-156">Varsa **Özellikler penceresini** görüntülenen, select değil **Özellikler penceresini** gelen **Görünüm** menüsü.</span><span class="sxs-lookup"><span data-stu-id="e26a2-156">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
17. <span data-ttu-id="e26a2-157">Sürükleme bir **readInt** etkinliğinden **NumberGuessWorkflowActivities** bölümünü **araç** sürükleyip bırakın **dizisi** onun aşağıdaki şekilde etkinlik **WriteLine** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="e26a2-157">Drag a **ReadInt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **Sequence** activity so that it follows the **WriteLine** activity.</span></span>  
  
18. <span data-ttu-id="e26a2-158">Bağlama **YerİşaretiAdı** bağımsız değişkeni **readInt** etkinliğe **YerİşaretiAdı** bağımsız değişkeni **komut istemi** yazaraketkinliği`BookmarkName` içine **bir VB ifadesi girin** kutusunun sağındaki **YerİşaretiAdı** değişkeninde **Özellikler penceresini**ve ardından iki SEKME tuşuna basın IntelliSense listesi üyeleri penceresini kapatın ve özelliğini kaydetmek için zaman.</span><span class="sxs-lookup"><span data-stu-id="e26a2-158">Bind the **BookmarkName** argument of the **ReadInt** activity to the **BookmarkName** argument of the **Prompt** activity by typing `BookmarkName` into the **Enter a VB expression** box to the right of the **BookmarkName** argument in the **Properties Window**, and then press the TAB key two times to close the IntelliSense list members window and save the property.</span></span>  
  
19. <span data-ttu-id="e26a2-159">Bağlama **sonuç** bağımsız değişkeni **readInt** etkinliğe **sonuç** bağımsız değişkeni **komut istemi** yazarak etkinlik `Result` içine **bir VB ifadesi girin** kutusunun sağındaki **sonuç** değişkeninde **Özellikler penceresini**ve ardından SEKME tuşuna iki kez basın.</span><span class="sxs-lookup"><span data-stu-id="e26a2-159">Bind the **Result** argument of the **ReadInt** activity to the **Result** argument of the **Prompt** activity by typing `Result` into the **Enter a VB expression** box to the right of the **Result** argument in the **Properties Window**, and then press the TAB key two times.</span></span>  
  
20. <span data-ttu-id="e26a2-160">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="e26a2-160">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="e26a2-161">Öğreticide, bir sonraki adım için bu etkinlikleri kullanarak bir iş akışı oluşturmak yönergeler bkz [nasıl yapılır: bir iş akışı oluşturmak](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="e26a2-161">For instructions on how to create a workflow by using these activities, see the next step in the tutorial, [How to: Create a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e26a2-162">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e26a2-162">See Also</span></span>  
 <xref:System.Activities.CodeActivity>  
 <xref:System.Activities.NativeActivity%601>  
 [<span data-ttu-id="e26a2-163">Özel Etkinlikler Tasarlama ve Uygulama</span><span class="sxs-lookup"><span data-stu-id="e26a2-163">Designing and Implementing Custom Activities</span></span>](../../../docs/framework/windows-workflow-foundation/designing-and-implementing-custom-activities.md)  
 [<span data-ttu-id="e26a2-164">Başlangıç Öğreticisi</span><span class="sxs-lookup"><span data-stu-id="e26a2-164">Getting Started Tutorial</span></span>](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [<span data-ttu-id="e26a2-165">Nasıl yapılır: İş Akışı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e26a2-165">How to: Create a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md)  
 [<span data-ttu-id="e26a2-166">Özel Etkinlik Tasarımcısında ExpressionTextBox Kullanma</span><span class="sxs-lookup"><span data-stu-id="e26a2-166">Using the ExpressionTextBox in a Custom Activity Designer</span></span>](../../../docs/framework/windows-workflow-foundation/samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)
