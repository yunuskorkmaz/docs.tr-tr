---
title: Birlikte çalışma etkinliği bir .NET Framework 4 akışında kullanma
ms.date: 03/30/2017
ms.assetid: 9bb747f0-eb33-4f70-84cd-317382372dcd
ms.openlocfilehash: 02eeaf5bb7ff484ba5982197fc395e247cd5a87f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43466731"
---
# <a name="using-the-interop-activity-in-a-net-framework-4-workflow"></a><span data-ttu-id="30bc9-102">Birlikte çalışma etkinliği bir .NET Framework 4 akışında kullanma</span><span class="sxs-lookup"><span data-stu-id="30bc9-102">Using the Interop Activity in a .NET Framework 4 Workflow</span></span>
<span data-ttu-id="30bc9-103">Kullanılarak oluşturulan etkinlikleri [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] veya [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] kullanılabilir bir [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] kullanarak iş akışı <xref:System.Activities.Statements.Interop> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="30bc9-103">Activities created using [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] or [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] can be used in a [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow by using the <xref:System.Activities.Statements.Interop> activity.</span></span> <span data-ttu-id="30bc9-104">Bu konuda kullanarak genel bir bakış sağlar <xref:System.Activities.Statements.Interop> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="30bc9-104">This topic provides an overview of using the <xref:System.Activities.Statements.Interop> activity.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="30bc9-105"><xref:System.Activities.Statements.Interop> İş akışının proje sahip olmadığı sürece etkinlik iş akışı Tasarımcısı araç kutusunda görünmüyor, **hedef Framework'ü** ayarının **.Net Framework 4** veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="30bc9-105">The <xref:System.Activities.Statements.Interop> activity does not appear in the workflow designer toolbox unless the workflow's project has its **Target Framework** setting set to **.Net Framework 4** or later.</span></span>  
  
## <a name="using-the-interop-activity-in-net-framework-45-workflows"></a><span data-ttu-id="30bc9-106">.NET Framework 4.5 iş akışlarında birlikte çalışma etkinliği kullanma</span><span class="sxs-lookup"><span data-stu-id="30bc9-106">Using the Interop Activity in .NET Framework 4.5 Workflows</span></span>  
 <span data-ttu-id="30bc9-107">Bu konuda, bir [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] etkinlik kitaplığı içeren oluşturulur bir `DiscountCalculator` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="30bc9-107">In this topic, a [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] activity library is created that contains a `DiscountCalculator` activity.</span></span> <span data-ttu-id="30bc9-108">`DiscountCalculator` Bir satın alma tutarını temel bir hesaplar ve oluşan bir <xref:System.Workflow.Activities.SequenceActivity> içeren bir <xref:System.Workflow.Activities.PolicyActivity>.</span><span class="sxs-lookup"><span data-stu-id="30bc9-108">The `DiscountCalculator` calculates a discount based on a purchase amount and consists of a <xref:System.Workflow.Activities.SequenceActivity> that contains a <xref:System.Workflow.Activities.PolicyActivity>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="30bc9-109">[!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] Bu konu başlığında oluşturduğunuz etkinliğini kullanan bir <xref:System.Workflow.Activities.PolicyActivity> etkinliğin mantığını uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="30bc9-109">The [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] activity created in this topic uses a <xref:System.Workflow.Activities.PolicyActivity> to implement the logic of the activity.</span></span> <span data-ttu-id="30bc9-110">Özel bir kullanmak için gerekli olmayan [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] etkinlik veya <xref:System.Activities.Statements.Interop> kullanmak için etkinlik kuralları içinde bir [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] iş akışı.</span><span class="sxs-lookup"><span data-stu-id="30bc9-110">It is not required to use a custom [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] activity or the <xref:System.Activities.Statements.Interop> activity in order to use rules in a [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow.</span></span> <span data-ttu-id="30bc9-111">Kuralları kullanma örneği için bir [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] kullanmadan iş akışı <xref:System.Activities.Statements.Interop> etkinliğine bakın [.NET Framework 4. 5'te ilke etkinliği](../../../docs/framework/windows-workflow-foundation/samples/policy-activity-in-net-framework-4-5.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="30bc9-111">For an example of using rules in a [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow without using the <xref:System.Activities.Statements.Interop> activity, see the [Policy Activity in .NET Framework 4.5](../../../docs/framework/windows-workflow-foundation/samples/policy-activity-in-net-framework-4-5.md) sample.</span></span>  
  
#### <a name="to-create-the-net-framework-35-activity-library-project"></a><span data-ttu-id="30bc9-112">.NET Framework 3.5 etkinliği kitaplık projesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="30bc9-112">To create the .NET Framework 3.5 activity library project</span></span>  
  
1.  <span data-ttu-id="30bc9-113">Açık [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] seçip **yeni** ardından **proje...**</span><span class="sxs-lookup"><span data-stu-id="30bc9-113">Open [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] and select **New** and then **Project…**</span></span> <span data-ttu-id="30bc9-114">gelen **dosya** menüsü.</span><span class="sxs-lookup"><span data-stu-id="30bc9-114">from the **File** menu.</span></span>  
  
2.  <span data-ttu-id="30bc9-115">Genişletin **diğer proje türleri** düğümünde **yüklü şablonlar** bölmesi ve select **Visual Studio çözümleri**.</span><span class="sxs-lookup"><span data-stu-id="30bc9-115">Expand the **Other Project Types** node in the **Installed Templates** pane and select **Visual Studio Solutions**.</span></span>  
  
3.  <span data-ttu-id="30bc9-116">Seçin **boş çözüm** gelen **Visual Studio çözümleri** listesi.</span><span class="sxs-lookup"><span data-stu-id="30bc9-116">Select **Blank Solution** from the **Visual Studio Solutions** list.</span></span> <span data-ttu-id="30bc9-117">Tür `PolicyInteropDemo` içinde **adı** kutusuna ve tıklatın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="30bc9-117">Type `PolicyInteropDemo` in the **Name** box and click **OK**.</span></span>  
  
4.  <span data-ttu-id="30bc9-118">Sağ **PolicyInteropDemo** içinde **Çözüm Gezgini** seçip **Ekle** ardından **yeni proje...** .</span><span class="sxs-lookup"><span data-stu-id="30bc9-118">Right-click **PolicyInteropDemo** in **Solution Explorer** and select **Add** and then **New Project…**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="30bc9-119">Varsa **Çözüm Gezgini** pencere görünür, select değil **Çözüm Gezgini** gelen **görünümü** menüsü.</span><span class="sxs-lookup"><span data-stu-id="30bc9-119">If the **Solution Explorer** window is not visible, select **Solution Explorer** from the **View** menu.</span></span>  
  
5.  <span data-ttu-id="30bc9-120">İçinde **yüklü şablonlar** listesinden **Visual C#** ardından **iş akışı**.</span><span class="sxs-lookup"><span data-stu-id="30bc9-120">In the **Installed Templates** list, select **Visual C#** and then **Workflow**.</span></span> <span data-ttu-id="30bc9-121">Seçin **.NET Framework 3.5** seçin ve .NET Framework sürümü açılır listede **iş akışı etkinlik Kitaplığı** gelen **şablonları** listesi.</span><span class="sxs-lookup"><span data-stu-id="30bc9-121">Select **.NET Framework 3.5** from the .NET Framework version drop-down list, and then select **Workflow Activity Library** from the **Templates** list.</span></span>  
  
6.  <span data-ttu-id="30bc9-122">Tür `PolicyActivityLibrary` içinde **adı** kutusuna ve tıklatın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="30bc9-122">Type `PolicyActivityLibrary` in the **Name** box and click **OK**.</span></span>  
  
7.  <span data-ttu-id="30bc9-123">Sağ **Activity1.cs** içinde **Çözüm Gezgini** seçip **Sil**.</span><span class="sxs-lookup"><span data-stu-id="30bc9-123">Right-click **Activity1.cs** in **Solution Explorer** and select **Delete**.</span></span> <span data-ttu-id="30bc9-124">Tıklayın **Tamam** onaylamak için.</span><span class="sxs-lookup"><span data-stu-id="30bc9-124">Click **OK** to confirm.</span></span>  
  
#### <a name="to-create-the-discountcalculator-activity"></a><span data-ttu-id="30bc9-125">DiscountCalculator etkinlik oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="30bc9-125">To create the DiscountCalculator activity</span></span>  
  
1.  <span data-ttu-id="30bc9-126">Sağ **PolicyActivityLibrary** içinde **Çözüm Gezgini** seçip **Ekle** ardından **etkinlik...** .</span><span class="sxs-lookup"><span data-stu-id="30bc9-126">Right-click **PolicyActivityLibrary** in **Solution Explorer** and select **Add** and then **Activity…**.</span></span>  
  
2.  <span data-ttu-id="30bc9-127">Seçin **etkinlik (kod ayırma ile)** gelen **Visual C# öğeleri** listesi.</span><span class="sxs-lookup"><span data-stu-id="30bc9-127">Select **Activity (with code separation)** from the **Visual C# Items** list.</span></span> <span data-ttu-id="30bc9-128">Tür `DiscountCalculator` içinde **adı** kutusuna ve tıklatın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="30bc9-128">Type `DiscountCalculator` in the **Name** box and click **OK**.</span></span>  
  
3.  <span data-ttu-id="30bc9-129">Sağ **DiscountCalculator.xoml** içinde **Çözüm Gezgini** seçip **kodu görüntüle**.</span><span class="sxs-lookup"><span data-stu-id="30bc9-129">Right-click **DiscountCalculator.xoml** in **Solution Explorer** and select **View Code**.</span></span>  
  
4.  <span data-ttu-id="30bc9-130">Aşağıdaki üç özelliği Ekle `DiscountCalculator` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="30bc9-130">Add the following three properties to the `DiscountCalculator` class.</span></span>  
  
    ```csharp  
    public partial class DiscountCalculator : SequenceActivity  
    {  
        public double Subtotal { get; set; }  
        public double DiscountPercent { get; set; }  
        public double Total { get; set; }  
    }  
    ```  
  
5.  <span data-ttu-id="30bc9-131">Sağ **DiscountCalculator.xoml** içinde **Çözüm Gezgini** seçip **Görünüm Tasarımcısı**.</span><span class="sxs-lookup"><span data-stu-id="30bc9-131">Right-click **DiscountCalculator.xoml** in **Solution Explorer** and select **View Designer**.</span></span>  
  
6.  <span data-ttu-id="30bc9-132">Sürükleme bir **ilke** etkinliğinden **Windows iş akışı v3.0** bölümünü **araç kutusu** sürükleyip **DiscountCalculator** etkinliği .</span><span class="sxs-lookup"><span data-stu-id="30bc9-132">Drag a **Policy** activity from the **Windows Workflow v3.0** section of the **Toolbox** and drop it in the **DiscountCalculator** activity.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="30bc9-133">Varsa **araç kutusu** pencere görünür, select değil **araç kutusu** gelen **görünümü** menüsü.</span><span class="sxs-lookup"><span data-stu-id="30bc9-133">If the **Toolbox** window is not visible, select **Toolbox** from the **View** menu.</span></span>  
  
#### <a name="to-configure-the-rules"></a><span data-ttu-id="30bc9-134">Kurallarını yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="30bc9-134">To configure the rules</span></span>  
  
1.  <span data-ttu-id="30bc9-135">Yeni eklenen tıklayın **ilke** etkinliği zaten seçili değilse bunu seçin.</span><span class="sxs-lookup"><span data-stu-id="30bc9-135">Click the newly added **Policy** activity to select it, if it is not already selected.</span></span>  
  
2.  <span data-ttu-id="30bc9-136">Tıklayın **RuleSetReference** özelliğinde **özellikleri** penceresini seçin ve özellik sağındaki elips düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="30bc9-136">Click the **RuleSetReference** property in the **Properties** window to select it, and click the ellipsis button to the right of the property.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="30bc9-137">Varsa **özellikleri** penceresi görünür değilse, seçin **Özellikler penceresi** gelen **görünümü** menüsü.</span><span class="sxs-lookup"><span data-stu-id="30bc9-137">If the **Properties** window is not visible, choose **Properties Window** from the **View** menu.</span></span>  
  
3.  <span data-ttu-id="30bc9-138">Seçin **Yeni'ye tıklayın...** .</span><span class="sxs-lookup"><span data-stu-id="30bc9-138">Select **Click New…**.</span></span>  
  
4.  <span data-ttu-id="30bc9-139">Tıklayın **Kuralı Ekle**.</span><span class="sxs-lookup"><span data-stu-id="30bc9-139">Click **Add Rule**.</span></span>  
  
5.  <span data-ttu-id="30bc9-140">İçine aşağıdaki ifadeyi yazın **koşul** kutusu.</span><span class="sxs-lookup"><span data-stu-id="30bc9-140">Type the following expression into the **Condition** box.</span></span>  
  
    ```  
    this.Subtotal >= 50 && this.Subtotal < 100  
    ```  
  
6.  <span data-ttu-id="30bc9-141">İçine aşağıdaki ifadeyi yazın **ardından Eylemler** kutusu.</span><span class="sxs-lookup"><span data-stu-id="30bc9-141">Type the following expression into the **Then Actions** box.</span></span>  
  
    ```  
    this.DiscountPercent = 0.075  
    ```  
  
7.  <span data-ttu-id="30bc9-142">Tıklayın **Kuralı Ekle**.</span><span class="sxs-lookup"><span data-stu-id="30bc9-142">Click **Add Rule**.</span></span>  
  
8.  <span data-ttu-id="30bc9-143">İçine aşağıdaki ifadeyi yazın **koşul** kutusu.</span><span class="sxs-lookup"><span data-stu-id="30bc9-143">Type the following expression into the **Condition** box.</span></span>  
  
    ```  
    this.Subtotal >= 100  
    ```  
  
9. <span data-ttu-id="30bc9-144">İçine aşağıdaki ifadeyi yazın **ardından Eylemler** kutusu.</span><span class="sxs-lookup"><span data-stu-id="30bc9-144">Type the following expression into the **Then Actions** box.</span></span>  
  
    ```  
    this.DiscountPercent = 0.15  
    ```  
  
10. <span data-ttu-id="30bc9-145">Tıklayın **Kuralı Ekle**.</span><span class="sxs-lookup"><span data-stu-id="30bc9-145">Click **Add Rule**.</span></span>  
  
11. <span data-ttu-id="30bc9-146">İçine aşağıdaki ifadeyi yazın **koşul** kutusu.</span><span class="sxs-lookup"><span data-stu-id="30bc9-146">Type the following expression into the **Condition** box.</span></span>  
  
    ```  
    this.DiscountPercent > 0  
    ```  
  
12. <span data-ttu-id="30bc9-147">İçine aşağıdaki ifadeyi yazın **ardından Eylemler** kutusu.</span><span class="sxs-lookup"><span data-stu-id="30bc9-147">Type the following expression into the **Then Actions** box.</span></span>  
  
    ```  
    this.Total = this.Subtotal - this.Subtotal * this.DiscountPercent  
    ```  
  
13. <span data-ttu-id="30bc9-148">İçine aşağıdaki ifadeyi yazın **başka eylemler** kutusu.</span><span class="sxs-lookup"><span data-stu-id="30bc9-148">Type the following expression into the **Else Actions** box.</span></span>  
  
    ```  
    this.Total = this.Subtotal  
    ```  
  
14. <span data-ttu-id="30bc9-149">Tıklayın **Tamam** kapatmak için **kural kümesi Düzenleyicisi** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="30bc9-149">Click **OK** to close the **Rule Set Editor** dialog box.</span></span>  
  
15. <span data-ttu-id="30bc9-150">Yeni oluşturulan emin <xref:System.Workflow.Activities.Rules.RuleSet> seçili **adı** listesinde ve tıklayın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="30bc9-150">Ensure that the newly-created <xref:System.Workflow.Activities.Rules.RuleSet> is selected in the **Name** list, and click **OK**.</span></span>  
  
16. <span data-ttu-id="30bc9-151">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="30bc9-151">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
 <span data-ttu-id="30bc9-152">Eklenen Kurallar `DiscountCalculator` etkinlik bu yordamda aşağıdaki kod örneğinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="30bc9-152">The rules added to the `DiscountCalculator` activity in this procedure are shown in the following code example.</span></span>  
  
```  
Rule1: IF this.Subtotal >= 50 && this.Subtotal < 100   
       THEN this.DiscountPercent = 0.075   
  
Rule2: IF this. Subtotal >= 100   
       THEN this.DiscountPercent = 0.15   
  
Rule3: IF this.DiscountPercent > 0   
       THEN this.Total = this.Subtotal - this.Subtotal * this.DiscountPercent   
       ELSE this.Total = this.Subtotal  
```  
  
 <span data-ttu-id="30bc9-153">Zaman <xref:System.Workflow.Activities.PolicyActivity> yürütür, bu üç kuralları değerlendirin ve değiştirme `Subtotal`, `DiscountPercent`, ve `Total` özellik değerlerini `DiscountCalculator` istenen indirimi hesaplamak için etkinlik.</span><span class="sxs-lookup"><span data-stu-id="30bc9-153">When the <xref:System.Workflow.Activities.PolicyActivity> executes, these three rules evaluate and modify the `Subtotal`, `DiscountPercent`, and `Total` property values of the `DiscountCalculator` activity to calculate the desired discount.</span></span>  
  
## <a name="using-the-discountcalculator-activity-with-the-interop-activity"></a><span data-ttu-id="30bc9-154">Birlikte çalışma etkinliği ile DiscountCalculator etkinliği kullanma</span><span class="sxs-lookup"><span data-stu-id="30bc9-154">Using the DiscountCalculator Activity with the Interop Activity</span></span>  
 <span data-ttu-id="30bc9-155">Kullanılacak `DiscountCalculator` etkinliği içinde bir [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] iş akışı, <xref:System.Activities.Statements.Interop> etkinliği kullanılır.</span><span class="sxs-lookup"><span data-stu-id="30bc9-155">To use the `DiscountCalculator` activity inside a [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow, the <xref:System.Activities.Statements.Interop> activity is used.</span></span> <span data-ttu-id="30bc9-156">Bu bölümde iki iş akışları oluşturulur, bir kod ve iş akışı Tasarımcısı kullanarak bir tane kullanarak gösteren nasıl kullanılacağını <xref:System.Activities.Statements.Interop> etkinliğiyle `DiscountCalculator` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="30bc9-156">In this section two workflows are created, one using code and one using the workflow designer, which show how to use the <xref:System.Activities.Statements.Interop> activity with the `DiscountCalculator` activity.</span></span> <span data-ttu-id="30bc9-157">Aynı ana bilgisayar uygulaması hem de iş akışları için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="30bc9-157">The same host application is used for both workflows.</span></span>  
  
#### <a name="to-create-the-host-application"></a><span data-ttu-id="30bc9-158">Ana bilgisayar uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="30bc9-158">To create the host application</span></span>  
  
1.  <span data-ttu-id="30bc9-159">Sağ **PolicyInteropDemo** içinde **Çözüm Gezgini** seçip **Ekle**, ardından **yeni proje...** .</span><span class="sxs-lookup"><span data-stu-id="30bc9-159">Right-click **PolicyInteropDemo** in **Solution Explorer** and select **Add**, and then **New Project…**.</span></span>  
  
2.  <span data-ttu-id="30bc9-160">Emin **.NET Framework 4.5** .NET Framework sürüm aşağı açılan listesinde seçili olduğunu doğrulayıp, seçin **iş akışı konsol uygulaması** gelen **Visual C# öğeleri** listesi.</span><span class="sxs-lookup"><span data-stu-id="30bc9-160">Ensure that **.NET Framework 4.5** is selected in the .NET Framework version drop-down list, and select  **Workflow Console Application** from the **Visual C# Items** list.</span></span>  
  
3.  <span data-ttu-id="30bc9-161">Tür `PolicyInteropHost` içine **adı** kutusuna ve tıklatın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="30bc9-161">Type `PolicyInteropHost` into the **Name** box and click **OK**.</span></span>  
  
4.  <span data-ttu-id="30bc9-162">Sağ **PolicyInteropHost** içinde **Çözüm Gezgini** seçip **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="30bc9-162">Right-click **PolicyInteropHost** in **Solution Explorer** and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="30bc9-163">İçinde **hedef Framework'ü** aşağı açılan listesinde, seçimi değiştirme **.NET Framework 4 istemci profili** için **.NET Framework 4.5**.</span><span class="sxs-lookup"><span data-stu-id="30bc9-163">In the **Target framework** drop-down list, change the selection from **.NET Framework 4 Client Profile** to **.NET Framework 4.5**.</span></span> <span data-ttu-id="30bc9-164">Tıklayın **Evet** onaylamak için.</span><span class="sxs-lookup"><span data-stu-id="30bc9-164">Click **Yes** to confirm.</span></span>  
  
6.  <span data-ttu-id="30bc9-165">Sağ **PolicyInteropHost** içinde **Çözüm Gezgini** seçip **Başvuru Ekle...** .</span><span class="sxs-lookup"><span data-stu-id="30bc9-165">Right-click **PolicyInteropHost** in **Solution Explorer** and select **Add Reference…**.</span></span>  
  
7.  <span data-ttu-id="30bc9-166">Seçin **PolicyActivityLibrary** gelen **projeleri** sekmesine **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="30bc9-166">Select **PolicyActivityLibrary** from the **Projects** tab and click **OK**.</span></span>  
  
8.  <span data-ttu-id="30bc9-167">Sağ **PolicyInteropHost** içinde **Çözüm Gezgini** seçip **Başvuru Ekle...** .</span><span class="sxs-lookup"><span data-stu-id="30bc9-167">Right-click **PolicyInteropHost** in **Solution Explorer** and select **Add Reference…**.</span></span>  
  
9. <span data-ttu-id="30bc9-168">Seçin **System.Workflow.Activities**, **System.Workflow.ComponentModel**, ardından **System.Workflow.Runtime** gelen **.NET**sekmesine **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="30bc9-168">Select **System.Workflow.Activities**, **System.Workflow.ComponentModel**, and then **System.Workflow.Runtime** from the **.NET** tab and click **OK**.</span></span>  
  
10. <span data-ttu-id="30bc9-169">Sağ **PolicyInteropHost** içinde **Çözüm Gezgini** seçip **başlangıç projesi olarak ayarla**.</span><span class="sxs-lookup"><span data-stu-id="30bc9-169">Right-click **PolicyInteropHost** in **Solution Explorer** and select **Set as StartUp Project**.</span></span>  
  
11. <span data-ttu-id="30bc9-170">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="30bc9-170">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
### <a name="using-the-interop-activity-in-code"></a><span data-ttu-id="30bc9-171">Kod içinde birlikte çalışma etkinliği kullanma</span><span class="sxs-lookup"><span data-stu-id="30bc9-171">Using the Interop Activity in Code</span></span>  
 <span data-ttu-id="30bc9-172">Bu örnekte, bir iş akışı tanımını içeren kod kullanılarak oluşturulan <xref:System.Activities.Statements.Interop> etkinlik ve `DiscountCalculator` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="30bc9-172">In this example, a workflow definition is created using code that contains the <xref:System.Activities.Statements.Interop> activity and the `DiscountCalculator` activity.</span></span> <span data-ttu-id="30bc9-173">Bu iş akışı kullanılarak çağrılan <xref:System.Activities.WorkflowInvoker> ve kuralı değerlendirme sonuçlarını konsolunu kullanarak yazılır bir <xref:System.Activities.Statements.WriteLine> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="30bc9-173">This workflow is invoked using <xref:System.Activities.WorkflowInvoker> and the results of the rule evaluation are written to the console using a <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
##### <a name="to-use-the-interop-activity-in-code"></a><span data-ttu-id="30bc9-174">Birlikte çalışma etkinliği kodu kullanmak için</span><span class="sxs-lookup"><span data-stu-id="30bc9-174">To use the Interop activity in code</span></span>  
  
1.  <span data-ttu-id="30bc9-175">Sağ **Program.cs** içinde **Çözüm Gezgini** seçip **kodu görüntüle**.</span><span class="sxs-lookup"><span data-stu-id="30bc9-175">Right-click **Program.cs** in **Solution Explorer** and select **View Code**.</span></span>  
  
2.  <span data-ttu-id="30bc9-176">Aşağıdaki `using` deyimini dosyanın üst.</span><span class="sxs-lookup"><span data-stu-id="30bc9-176">Add the following `using` statement at the top of the file.</span></span>  
  
    ```csharp  
    using PolicyActivityLibrary;  
    ```  
  
3.  <span data-ttu-id="30bc9-177">İçeriği kaldırmak `Main` yöntemi ve aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="30bc9-177">Remove the contents of the `Main` method and replace with the following code.</span></span>  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        CalculateDiscountUsingCodeWorkflow();  
    }  
    ```  
  
4.  <span data-ttu-id="30bc9-178">İçinde yeni bir yöntem oluşturma `Program` adlı sınıf `CalculateDiscountUsingCodeWorkflow` , aşağıdaki kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="30bc9-178">Create a new method in the `Program` class called `CalculateDiscountUsingCodeWorkflow` that contains the following code.</span></span>  
  
    ```csharp  
    static void CalculateDiscountUsingCodeWorkflow()  
    {  
        Variable<double> Subtotal = new Variable<double>  
        {  
            Default = 75.99,  
            Name = "Subtotal"  
        };  
  
        Variable<double> DiscountPercent = new Variable<double>  
        {  
            Name = "DiscountPercent"  
        };  
  
        Variable<double> Total = new Variable<double>  
        {  
            Name = "Total"  
        };  
  
        Activity wf = new Sequence  
        {  
            Variables = { Subtotal, DiscountPercent, Total },  
            Activities =   
            {  
                new Interop  
                {  
                    ActivityType = typeof(DiscountCalculator),  
                    ActivityProperties =   
                    {  
                        { "Subtotal", new InArgument<double>(Subtotal) },  
                        { "DiscountPercentOut", new OutArgument<double>(DiscountPercent) },  
                        { "TotalOut", new OutArgument<double>(Total) }  
                    }  
                },  
                new WriteLine  
                {  
                    Text =  new InArgument<string>(env =>   
                        string.Format("Subtotal: {0:C}, Discount {1}%, Total {2:C}",   
                        Subtotal.Get(env), DiscountPercent.Get(env) * 100, Total.Get(env)))  
                }  
            }  
        };  
  
        WorkflowInvoker.Invoke(wf);  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="30bc9-179">`Subtotal`, `DiscountPercent`, Ve `Total` özelliklerini `DiscountCalculator` etkinlik bağımsız değişkenleri ortaya <xref:System.Activities.Statements.Interop> etkinliği ve yerel ilişkili iş akışı değişkenleri <xref:System.Activities.Statements.Interop> etkinliğin <xref:System.Activities.Statements.Interop.ActivityProperties%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="30bc9-179">The `Subtotal`, `DiscountPercent`, and `Total` properties of the `DiscountCalculator` activity are surfaced as arguments of the <xref:System.Activities.Statements.Interop> activity, and bound to local workflow variables in the <xref:System.Activities.Statements.Interop> activity’s <xref:System.Activities.Statements.Interop.ActivityProperties%2A> collection.</span></span> <span data-ttu-id="30bc9-180">`Subtotal` olarak eklenir bir <xref:System.Activities.ArgumentDirection.In> bağımsız değişken olduğundan `Subtotal` veri akışları halinde <xref:System.Activities.Statements.Interop> etkinliği ve `DiscountPercent` ve `Total` olarak eklenir <xref:System.Activities.ArgumentDirection.Out> bağımsız değişkenleri tanesi kendi veri akışları için <xref:System.Activities.Statements.Interop> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="30bc9-180">`Subtotal` is added as an <xref:System.Activities.ArgumentDirection.In> argument because the `Subtotal` data flows into the <xref:System.Activities.Statements.Interop> activity, and `DiscountPercent` and `Total` are added as <xref:System.Activities.ArgumentDirection.Out> arguments because their data flows out of the <xref:System.Activities.Statements.Interop> activity.</span></span> <span data-ttu-id="30bc9-181">Unutmayın iki <xref:System.Activities.ArgumentDirection.Out> bağımsız değişken adları ile eklenen `DiscountPercentOut` ve `TotalOut` temsil ettikleri belirtmek için <xref:System.Activities.ArgumentDirection.Out> bağımsız değişkenler.</span><span class="sxs-lookup"><span data-stu-id="30bc9-181">Note that the two <xref:System.Activities.ArgumentDirection.Out> arguments are added with the names `DiscountPercentOut` and `TotalOut` to indicate that they represent <xref:System.Activities.ArgumentDirection.Out> arguments.</span></span> <span data-ttu-id="30bc9-182">`DiscountCalculator` Türü olarak belirtildiğinde <xref:System.Activities.Statements.Interop> etkinliğin <xref:System.Activities.Statements.Interop.ActivityType%2A>.</span><span class="sxs-lookup"><span data-stu-id="30bc9-182">The `DiscountCalculator` type is specified as the <xref:System.Activities.Statements.Interop> activity’s <xref:System.Activities.Statements.Interop.ActivityType%2A>.</span></span>  
  
5.  <span data-ttu-id="30bc9-183">Derleme ve uygulamayı çalıştırmak için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="30bc9-183">Press CTRL+F5 to build and run the application.</span></span> <span data-ttu-id="30bc9-184">Yedek için farklı değerler `Subtotal` farklı indirim düzeyleri tarafından sağlanan çıkış test etmek için değer `DiscountCalculator` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="30bc9-184">Substitute different values for the `Subtotal` value to test out the different discount levels provided by the `DiscountCalculator` activity.</span></span>  
  
    ```csharp  
    Variable<double> Subtotal = new Variable<double>  
    {  
        Default = 75.99, // Change this value.  
        Name = "Subtotal"  
    };  
    ```  
  
### <a name="using-the-interop-activity-in-the-workflow-designer"></a><span data-ttu-id="30bc9-185">Birlikte çalışma etkinliği iş akışı Tasarımcısı'nda kullanma</span><span class="sxs-lookup"><span data-stu-id="30bc9-185">Using the Interop Activity in the Workflow Designer</span></span>  
 <span data-ttu-id="30bc9-186">Bu örnekte, iş akışı Tasarımcısı'nı kullanarak bir iş akışı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="30bc9-186">In this example, a workflow is created using the workflow designer.</span></span> <span data-ttu-id="30bc9-187">Bu iş akışı önceki örnekle aynı işlevselliği dışında daha kullanmak yerine sahip bir <xref:System.Activities.Statements.WriteLine> indirim görüntülemek için etkinliği ana bilgisayar uygulamasını alır ve iş akışı tamamlandığında indirim bilgilerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="30bc9-187">This workflow has the same functionality as the previous example, except than instead of using a <xref:System.Activities.Statements.WriteLine> activity to display the discount, the host application retrieves and displays the discount information when the workflow completes.</span></span> <span data-ttu-id="30bc9-188">Ayrıca, verileri içerecek şekilde yerel iş akışı değişkenlerini kullanarak yerine bağımsız değişkenler iş akışı Tasarımcısı'nda oluşturulan ve iş akışı çağrıldığında değerleri konaktan geçirilir.</span><span class="sxs-lookup"><span data-stu-id="30bc9-188">Also, instead of using local workflow variables to contain the data, arguments are created in the workflow designer and the values are passed in from the host when the workflow is invoked.</span></span>  
  
##### <a name="to-host-the-policyactivity-using-a-workflow-designer-created-workflow"></a><span data-ttu-id="30bc9-189">Bir iş akışı tasarımcısı tarafından oluşturulan iş akışı kullanarak PolicyActivity barındırmak için</span><span class="sxs-lookup"><span data-stu-id="30bc9-189">To host the PolicyActivity using a Workflow Designer-created workflow</span></span>  
  
1.  <span data-ttu-id="30bc9-190">Sağ **Workflow1.xaml** içinde **Çözüm Gezgini** seçip **Sil**.</span><span class="sxs-lookup"><span data-stu-id="30bc9-190">Right-click **Workflow1.xaml** in **Solution Explorer** and select **Delete**.</span></span> <span data-ttu-id="30bc9-191">Tıklayın **Tamam** onaylamak için.</span><span class="sxs-lookup"><span data-stu-id="30bc9-191">Click **OK** to confirm.</span></span>  
  
2.  <span data-ttu-id="30bc9-192">Sağ **PolicyInteropHost** içinde **Çözüm Gezgini** seçip **Ekle**, **yeni öğe...** .</span><span class="sxs-lookup"><span data-stu-id="30bc9-192">Right-click **PolicyInteropHost** in **Solution Explorer** and select **Add**, **New Item…**.</span></span>  
  
3.  <span data-ttu-id="30bc9-193">Genişletin **Visual C# öğeleri** düğümünü seçip alt **iş akışı**.</span><span class="sxs-lookup"><span data-stu-id="30bc9-193">Expand the **Visual C# Items** node and select **Workflow**.</span></span> <span data-ttu-id="30bc9-194">Seçin **etkinlik** gelen **Visual C# öğeleri** listesi.</span><span class="sxs-lookup"><span data-stu-id="30bc9-194">Select **Activity** from the **Visual C# Items** list.</span></span>  
  
4.  <span data-ttu-id="30bc9-195">Tür `DiscountWorkflow` içine **adı** kutusuna ve tıklatın **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="30bc9-195">Type `DiscountWorkflow` into the **Name** box and click **Add**.</span></span>  
  
5.  <span data-ttu-id="30bc9-196">Tıklayın **bağımsız değişkenleri** görüntülemek için iş akışı Tasarımcısı'nın bir alt sol taraftaki düğmeyi **bağımsız değişkenleri** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="30bc9-196">Click the **Arguments** button on the lower left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
6.  <span data-ttu-id="30bc9-197">Tıklayın **bağımsız değişken oluşturma**.</span><span class="sxs-lookup"><span data-stu-id="30bc9-197">Click **Create Argument**.</span></span>  
  
7.  <span data-ttu-id="30bc9-198">Tür `Subtotal` içine **adı** kutusunda **içinde** gelen **yönü** açılan listesinde, select **çift** gelen**Bağımsız değişken türü** açılır ve bağımsız değişkeni kaydetmek için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="30bc9-198">Type `Subtotal` into the **Name** box, select **In** from the **Direction** drop-down, select **Double** from the **Argument type** drop-down, and then press ENTER to save the argument.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="30bc9-199">Varsa **çift** kullanımda olmayan **bağımsız değişken türü** aşağı açılan listesinden **vyhledat Typy...** , türü `System.Double` içinde **tür adı** ve'ı tıklatın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="30bc9-199">If **Double** is not in the **Argument type** drop-down list, select **Browse for Types …**, type `System.Double` in the **Type Name** box, and click **OK**.</span></span>  
  
8.  <span data-ttu-id="30bc9-200">Tıklayın **bağımsız değişken oluşturma**.</span><span class="sxs-lookup"><span data-stu-id="30bc9-200">Click **Create Argument**.</span></span>  
  
9. <span data-ttu-id="30bc9-201">Tür `DiscountPercent` içine **adı** kutusunda **kullanıma** gelen **yönü** açılan listesinde, select **çift** gelen**Bağımsız değişken türü** açılır ve bağımsız değişkeni kaydetmek için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="30bc9-201">Type `DiscountPercent` into the **Name** box, select **Out** from the **Direction** drop-down, select **Double** from the **Argument type** drop-down, and then press ENTER to save the argument.</span></span>  
  
10. <span data-ttu-id="30bc9-202">Tıklayın **bağımsız değişken oluşturma**.</span><span class="sxs-lookup"><span data-stu-id="30bc9-202">Click **Create Argument**.</span></span>  
  
11. <span data-ttu-id="30bc9-203">Tür `Total` içine **adı** kutusunda **kullanıma** gelen **yönü** açılan listesinde, select **çift** gelen**Bağımsız değişken türü** açılır ve bağımsız değişkeni kaydetmek için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="30bc9-203">Type `Total` into the **Name** box, select **Out** from the **Direction** drop-down, select **Double** from the **Argument type** drop-down, and then press ENTER to save the argument.</span></span>  
  
12. <span data-ttu-id="30bc9-204">Tıklayın **bağımsız değişkenleri** iş akışı tasarımcısını kapatmak için sol alt köşesine düğmesinde **bağımsız değişkenleri** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="30bc9-204">Click the **Arguments** button on the lower left side of the workflow designer to close the **Arguments** pane.</span></span>  
  
13. <span data-ttu-id="30bc9-205">Sürükleme bir **dizisi** etkinliğinden **akış denetimi** bölümünü **araç kutusu** ve iş akışı Tasarımcısı yüzeyine bırakın.</span><span class="sxs-lookup"><span data-stu-id="30bc9-205">Drag a **Sequence** activity from the **Control Flow** section of the **Toolbox** and drop it onto the workflow designer surface.</span></span>  
  
14. <span data-ttu-id="30bc9-206">Sürükleme bir **Interop** etkinliğinden **geçiş** bölümünü **araç kutusu** sürükleyip **dizisi** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="30bc9-206">Drag an **Interop** activity from the **Migration** section of the **Toolbox** and drop it in the **Sequence** activity.</span></span>  
  
15. <span data-ttu-id="30bc9-207">Tıklayın **Interop** faaliyete **göz atmak için tıklatın...**</span><span class="sxs-lookup"><span data-stu-id="30bc9-207">Click the **Interop** activity on the **Click to browse…**</span></span> <span data-ttu-id="30bc9-208">Etiket, tip **DiscountCalculator** içinde **tür adı** ve'ı tıklatın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="30bc9-208">label, type **DiscountCalculator** in the **Type Name** box, and click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="30bc9-209">Zaman <xref:System.Activities.Statements.Interop> etkinlik iş akışına eklenen ve `DiscountCalculator` türü olarak belirtilen kendi <xref:System.Activities.Statements.Interop.ActivityType%2A>, <xref:System.Activities.Statements.Interop> etkinliği gösteren üç <xref:System.Activities.ArgumentDirection.In> bağımsız değişkenleri ve üç <xref:System.Activities.ArgumentDirection.Out> temsil eden üç genel bağımsız değişkenleri özelliklerini `DiscountCalculator` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="30bc9-209">When the <xref:System.Activities.Statements.Interop> activity is added to the workflow and the `DiscountCalculator` type is specified as its <xref:System.Activities.Statements.Interop.ActivityType%2A>, the <xref:System.Activities.Statements.Interop> activity exposes three <xref:System.Activities.ArgumentDirection.In> arguments and three <xref:System.Activities.ArgumentDirection.Out> arguments that represent the three public properties of the `DiscountCalculator` activity.</span></span> <span data-ttu-id="30bc9-210"><xref:System.Activities.ArgumentDirection.In> Bağımsız değişkenleri üç genel özellikleri ve üç aynı ada sahip <xref:System.Activities.ArgumentDirection.Out> bağımsız değişkenlere sahip aynı adlarla **kullanıma** özellik adına eklenir.</span><span class="sxs-lookup"><span data-stu-id="30bc9-210">The <xref:System.Activities.ArgumentDirection.In> arguments have the same name as the three public properties, and the three <xref:System.Activities.ArgumentDirection.Out> arguments have the same names with **Out** appended to the property name.</span></span> <span data-ttu-id="30bc9-211">Aşağıdaki adımlarda önceki adımlarda oluşturulan iş akışı bağımsız değişkenleri bağlı <xref:System.Activities.Statements.Interop> etkinliğin bağımsız değişkenler.</span><span class="sxs-lookup"><span data-stu-id="30bc9-211">In the following steps, the workflow arguments created in the previous steps are bound to the <xref:System.Activities.Statements.Interop> activity’s arguments.</span></span>  
  
16. <span data-ttu-id="30bc9-212">Tür `DiscountPercent` içine **zadejte Výraz jazyka vb.** kutusunun sağındaki **DiscountPercentOut** özelliği ve SEKME tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="30bc9-212">Type `DiscountPercent` into the **Enter a VB expression** box to the right of the **DiscountPercentOut** property and press TAB.</span></span>  
  
17. <span data-ttu-id="30bc9-213">Tür `Subtotal` içine **zadejte Výraz jazyka vb.** kutusunun sağındaki **Subtotal** özelliği ve SEKME tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="30bc9-213">Type `Subtotal` into the **Enter a VB expression** box to the right of the **Subtotal** property and press TAB.</span></span>  
  
18. <span data-ttu-id="30bc9-214">Tür `Total` içine **zadejte Výraz jazyka vb.** kutusunun sağındaki **TotalOut** özelliği ve SEKME tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="30bc9-214">Type `Total` into the **Enter a VB expression** box to the right of the **TotalOut** property and press TAB.</span></span>  
  
19. <span data-ttu-id="30bc9-215">Sağ **Program.cs** içinde **Çözüm Gezgini** seçip **kodu görüntüle**.</span><span class="sxs-lookup"><span data-stu-id="30bc9-215">Right-click **Program.cs** in **Solution Explorer** and select **View Code**.</span></span>  
  
20. <span data-ttu-id="30bc9-216">Aşağıdaki `using` deyimini dosyanın üst.</span><span class="sxs-lookup"><span data-stu-id="30bc9-216">Add the following `using` statement at the top of the file.</span></span>  
  
    ```csharp  
    using System.Collections.Generic;  
    ```  
  
21. <span data-ttu-id="30bc9-217">Çağrı yorum `CalculateDiscountInCode` yönteminde `Main` yöntemi ve aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="30bc9-217">Comment out the call to the `CalculateDiscountInCode` method in the `Main` method and add the following code.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="30bc9-218">Önceki yordamda ve varsayılan takip ettiğiniz değil, `Main` kodu varsa, içeriği değiştirin `Main` aşağıdaki kod ile.</span><span class="sxs-lookup"><span data-stu-id="30bc9-218">If you did not follow the previous procedure and the default `Main` code is present, replace the contents of `Main` with the following code.</span></span>  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        CalculateDiscountUsingDesignerWorkflow();  
        //CalculateDiscountUsingCodeWorkflow();  
    }  
    ```  
  
22. <span data-ttu-id="30bc9-219">İçinde yeni bir yöntem oluşturma `Program` adlı sınıf `CalculateDiscountUsingDesignerWorkflow` , aşağıdaki kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="30bc9-219">Create a new method in the `Program` class called `CalculateDiscountUsingDesignerWorkflow` that contains the following code.</span></span>  
  
    ```csharp  
    static void CalculateDiscountUsingDesignerWorkflow()  
    {  
        double SubtotalValue = 125.99;  
        Dictionary<string, object> wfargs = new Dictionary<string, object>  
        {  
            {"Subtotal", SubtotalValue}  
        };  
  
        Activity wf = new DiscountWorkflow();  
  
        IDictionary<string, object> outputs =  
            WorkflowInvoker.Invoke(wf, wfargs);  
  
        Console.WriteLine("Subtotal: {0:C}, Discount {1}%, Total {2:C}",  
            SubtotalValue, (double)outputs["DiscountPercent"] * 100,  
            outputs["Total"]);  
    }  
    ```  
  
23. <span data-ttu-id="30bc9-220">Derleme ve uygulamayı çalıştırmak için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="30bc9-220">Press CTRL+F5 to build and run the application.</span></span> <span data-ttu-id="30bc9-221">Farklı bir belirtmek için `Subtotal` tutar, değiştirin `SubtotalValue` aşağıdaki kodda.</span><span class="sxs-lookup"><span data-stu-id="30bc9-221">To specify a different `Subtotal` amount, change the value of `SubtotalValue` in the following code.</span></span>  
  
    ```csharp  
    double SubtotalValue = 125.99; // Change this value.  
    ```  
  
## <a name="rules-features-overview"></a><span data-ttu-id="30bc9-222">Kuralları özelliklerine genel bakış</span><span class="sxs-lookup"><span data-stu-id="30bc9-222">Rules Features Overview</span></span>  
 <span data-ttu-id="30bc9-223">[!INCLUDE[wf1](../../../includes/wf1-md.md)] Kurallar altyapısı kuralları İleri zincirleme desteğiyle önceliğe dayalı bir şekilde işlemek için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="30bc9-223">The [!INCLUDE[wf1](../../../includes/wf1-md.md)] rules engine provides support for processing rules in a priority-based manner with support for forward chaining.</span></span> <span data-ttu-id="30bc9-224">Kurallar, tek bir öğe veya bir koleksiyondaki öğelerin değerlendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="30bc9-224">Rules can be evaluated for a single item or for items in a collection.</span></span> <span data-ttu-id="30bc9-225">Kuralları ve belirli kurallar işlevler hakkında bilgi genel bakış için lütfen aşağıdaki tabloya bakın.</span><span class="sxs-lookup"><span data-stu-id="30bc9-225">For an overview of rules and information on specific rules functionality, please refer to the following table.</span></span>  
  
|<span data-ttu-id="30bc9-226">Kuralları özelliği</span><span class="sxs-lookup"><span data-stu-id="30bc9-226">Rules Feature</span></span>|<span data-ttu-id="30bc9-227">Belgeler</span><span class="sxs-lookup"><span data-stu-id="30bc9-227">Documentation</span></span>|  
|-------------------|-------------------|  
|<span data-ttu-id="30bc9-228">Kurallarına genel bakış</span><span class="sxs-lookup"><span data-stu-id="30bc9-228">Rules Overview</span></span>|[<span data-ttu-id="30bc9-229">Windows Workflow Foundation kurallar altyapısı giriş</span><span class="sxs-lookup"><span data-stu-id="30bc9-229">Introduction to the Windows Workflow Foundation Rules Engine</span></span>](https://go.microsoft.com/fwlink/?LinkID=152836)|  
|<span data-ttu-id="30bc9-230">Kural kümesi</span><span class="sxs-lookup"><span data-stu-id="30bc9-230">RuleSet</span></span>|<span data-ttu-id="30bc9-231">[İş akışlarında RuleSets kullanma](https://go.microsoft.com/fwlink/?LinkId=178516) ve <xref:System.Workflow.Activities.Rules.RuleSet></span><span class="sxs-lookup"><span data-stu-id="30bc9-231">[Using RuleSets in Workflows](https://go.microsoft.com/fwlink/?LinkId=178516) and <xref:System.Workflow.Activities.Rules.RuleSet></span></span>|  
|<span data-ttu-id="30bc9-232">Değerlendirme kuralları</span><span class="sxs-lookup"><span data-stu-id="30bc9-232">Evaluation of Rules</span></span>|[<span data-ttu-id="30bc9-233">RuleSets değerlendirme kuralları</span><span class="sxs-lookup"><span data-stu-id="30bc9-233">Rules Evaluation in RuleSets</span></span>](https://go.microsoft.com/fwlink/?LinkId=178517)|  
|<span data-ttu-id="30bc9-234">Zincirleme kuralları</span><span class="sxs-lookup"><span data-stu-id="30bc9-234">Rules Chaining</span></span>|<span data-ttu-id="30bc9-235">[İleri denetim zincirleme](https://go.microsoft.com/fwlink/?LinkId=178518) ve [İleri kuralları zincirleme](https://go.microsoft.com/fwlink/?LinkId=178519)</span><span class="sxs-lookup"><span data-stu-id="30bc9-235">[Forward Chaining Control](https://go.microsoft.com/fwlink/?LinkId=178518) and [Forward Chaining of Rules](https://go.microsoft.com/fwlink/?LinkId=178519)</span></span>|  
|<span data-ttu-id="30bc9-236">Kural koleksiyonlarında işleme</span><span class="sxs-lookup"><span data-stu-id="30bc9-236">Processing Collections in Rules</span></span>|[<span data-ttu-id="30bc9-237">Kural koleksiyonlarında işleme</span><span class="sxs-lookup"><span data-stu-id="30bc9-237">Processing Collections in Rules</span></span>](https://go.microsoft.com/fwlink/?LinkId=178520)|  
|<span data-ttu-id="30bc9-238">PolicyActivity kullanma</span><span class="sxs-lookup"><span data-stu-id="30bc9-238">Using the PolicyActivity</span></span>|<span data-ttu-id="30bc9-239">[PolicyActivity etkinliğini kullanarak](https://go.microsoft.com/fwlink/?LinkId=178521) ve <xref:System.Workflow.Activities.PolicyActivity></span><span class="sxs-lookup"><span data-stu-id="30bc9-239">[Using the PolicyActivity Activity](https://go.microsoft.com/fwlink/?LinkId=178521) and <xref:System.Workflow.Activities.PolicyActivity></span></span>|  
  
 <span data-ttu-id="30bc9-240">Oluşturulan iş akışları [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] tarafından sağlanan kuralları özelliklerin tümünü kullanmayan [!INCLUDE[wf1](../../../includes/wf1-md.md)]bildirim temelli etkinlik koşullar ve gibi koşullu etkinlikler gibi <xref:System.Workflow.Activities.ConditionedActivityGroup> ve <xref:System.Workflow.Activities.ReplicatorActivity>.</span><span class="sxs-lookup"><span data-stu-id="30bc9-240">Workflows created in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] do not use all of the rules features provided by [!INCLUDE[wf1](../../../includes/wf1-md.md)], such as declarative activity conditions and conditional activities such as the <xref:System.Workflow.Activities.ConditionedActivityGroup> and <xref:System.Workflow.Activities.ReplicatorActivity>.</span></span> <span data-ttu-id="30bc9-241">Gerekirse, bu işlev kullanılarak oluşturulan iş akışları için kullanılabilir [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] ve [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="30bc9-241">If required, this functionality is available for workflows created using [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] and [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)].</span></span> <span data-ttu-id="30bc9-242">Daha fazla bilgi için [geçiş kılavuzuna](../../../docs/framework/windows-workflow-foundation/migration-guidance.md).</span><span class="sxs-lookup"><span data-stu-id="30bc9-242">For more information, see [Migration Guidance](../../../docs/framework/windows-workflow-foundation/migration-guidance.md).</span></span>
