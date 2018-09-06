---
title: 'Nasıl yapılır: oluşturma ve uzun süre çalışan iş akışı'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c0043c89-2192-43c9-986d-3ecec4dd8c9c
ms.openlocfilehash: 2c3368bc73d54f2848cad3c1086b1d9733205d2b
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43747791"
---
# <a name="how-to-create-and-run-a-long-running-workflow"></a><span data-ttu-id="094d5-102">Nasıl yapılır: oluşturma ve uzun süre çalışan iş akışı</span><span class="sxs-lookup"><span data-stu-id="094d5-102">How to: Create and Run a Long Running Workflow</span></span>
<span data-ttu-id="094d5-103">Windows Workflow Foundation (WF) merkezi özelliklerinin kalıcı hale getirmek ve boşta iş akışları bir veritabanına kaldırın çalışma zamanının becerisidir.</span><span class="sxs-lookup"><span data-stu-id="094d5-103">One of the central features of Windows Workflow Foundation (WF) is the runtime’s ability to persist and unload idle workflows to a database.</span></span> <span data-ttu-id="094d5-104">Adımları [nasıl yapılır: bir iş akışı çalıştırma](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) bir konsol uygulaması kullanarak iş akışı barındırma ilişkin temel bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="094d5-104">The steps in [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) demonstrated the basics of workflow hosting using a console application.</span></span> <span data-ttu-id="094d5-105">Örnekler, başlangıç iş akışları, iş akışı yaşam döngüsü işleyicileri ve sürdürme yer işaretleri gösterilen.</span><span class="sxs-lookup"><span data-stu-id="094d5-105">Examples were shown of starting workflows, workflow lifecycle handlers, and resuming bookmarks.</span></span> <span data-ttu-id="094d5-106">İş akışı kalıcılığı etkili bir şekilde göstermek için daha karmaşık bir iş akışı ana bilgisayarı gereklidir başlatma ve birden çok iş akışı örnekleri sürdürme destekler.</span><span class="sxs-lookup"><span data-stu-id="094d5-106">In order to demonstrate workflow persistence effectively, a more complex workflow host is required that supports starting and resuming multiple workflow instances.</span></span> <span data-ttu-id="094d5-107">Öğreticide bu adım, bir Windows form konağı başlatılıyor ve sürdürme birden çok iş akışı örnekleri, iş akışı kalıcılığı destekler ve izleme gibi gelişmiş özellikler için temel sağlayan uygulama ve olan sürüm oluşturma işlemi gösterilmektedir sonraki öğretici adımlarda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="094d5-107">This step in the tutorial demonstrates how to create a Windows form host application that supports starting and resuming multiple workflow instances, workflow persistence, and provides a basis for the advanced features such as tracking and versioning that are demonstrated in subsequent tutorial steps.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="094d5-108">Bu öğretici adımı ve sonraki adımları, tüm üç iş akışı türlerinden kullanın [nasıl yapılır: bir iş akışı oluşturmak](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="094d5-108">This tutorial step and the subsequent steps use all three workflow types from [How to: Create a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md).</span></span> <span data-ttu-id="094d5-109">Üç tür tamamlanmadıysa yer alan adımları tamamlanmış bir sürümünü indirebilirsiniz [Windows Workflow Foundation (WF45) - başlangıç Öğreticisi](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="094d5-109">If you did not complete all three types you can download a completed version of the steps from [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="094d5-110">Tamamlanmış bir sürümünü indirin veya videosu öğreticinin görüntülemek için bkz: [Windows Workflow Foundation (WF45) - başlangıç Öğreticisi](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="094d5-110">To download a completed version or view a video walkthrough of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="in-this-topic"></a><span data-ttu-id="094d5-111">Bu konuda</span><span class="sxs-lookup"><span data-stu-id="094d5-111">In this topic</span></span>  
  
-   [<span data-ttu-id="094d5-112">Kalıcılık veritabanı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="094d5-112">To create the persistence database</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_CreatePersistenceDatabase)  
  
-   [<span data-ttu-id="094d5-113">DurableInstancing derlemelere başvuru eklemek için</span><span class="sxs-lookup"><span data-stu-id="094d5-113">To add the reference to the DurableInstancing assemblies</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_AddReference)  
  
-   [<span data-ttu-id="094d5-114">İş akışı ana form oluşturma</span><span class="sxs-lookup"><span data-stu-id="094d5-114">To create the workflow host form</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_CreateForm)  
  
-   [<span data-ttu-id="094d5-115">Formun yardımcı yöntemler ve özellikler eklemek için</span><span class="sxs-lookup"><span data-stu-id="094d5-115">To add the properties and helper methods of the form</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_AddHelperMethods)  
  
-   [<span data-ttu-id="094d5-116">Örnek deposu, iş akışı yaşam döngüsü işleyicileri ve Uzantıları'nı yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="094d5-116">To configure the instance store, workflow lifecycle handlers, and extensions</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_ConfigureWorkflowApplication)  
  
-   [<span data-ttu-id="094d5-117">Başlangıç ve birden çok iş akışı türlerini sürdürme etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="094d5-117">To enable starting and resuming multiple workflow types</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_WorkflowVersionMap)  
  
-   [<span data-ttu-id="094d5-118">Yeni bir iş akışını başlatmak için</span><span class="sxs-lookup"><span data-stu-id="094d5-118">To start a new workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_StartWorkflow)  
  
-   [<span data-ttu-id="094d5-119">Bir iş akışını sürdürmek için</span><span class="sxs-lookup"><span data-stu-id="094d5-119">To resume a workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_ResumeWorkflow)  
  
-   [<span data-ttu-id="094d5-120">Bir iş akışı sonlandırılmak üzere</span><span class="sxs-lookup"><span data-stu-id="094d5-120">To terminate a workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_TerminateWorkflow)  
  
-   [<span data-ttu-id="094d5-121">Derleme ve uygulamayı çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="094d5-121">To build and run the application</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_BuildAndRun)  
  
###  <a name="BKMK_CreatePersistenceDatabase"></a> <span data-ttu-id="094d5-122">Kalıcılık veritabanı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="094d5-122">To create the persistence database</span></span>  
  
1.  <span data-ttu-id="094d5-123">SQL Server Management Studio'yu açın ve yerel, örneğin sunucuya **. \SQLEXPRESS**.</span><span class="sxs-lookup"><span data-stu-id="094d5-123">Open SQL Server Management Studio and connect to the local server, for example **.\SQLEXPRESS**.</span></span> <span data-ttu-id="094d5-124">Sağ **veritabanları** düğümü seçin ve yerel sunucu **yeni veritabanı**.</span><span class="sxs-lookup"><span data-stu-id="094d5-124">Right-click the **Databases** node on the local server, and select **New Database**.</span></span> <span data-ttu-id="094d5-125">Yeni bir veritabanı adı **WF45GettingStartedTutorial**, diğer tüm değerleri kabul edin ve seçin **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="094d5-125">Name the new database **WF45GettingStartedTutorial**, accept all other values, and select **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="094d5-126">Sahip olduğunuzdan emin olun **Create Database** veritabanı oluşturmadan önce yerel sunucuda izni.</span><span class="sxs-lookup"><span data-stu-id="094d5-126">Ensure that you have **Create Database** permission on the local server before creating the database.</span></span>  
  
2.  <span data-ttu-id="094d5-127">Seçin **açık**, **dosya** gelen **dosya** menüsü.</span><span class="sxs-lookup"><span data-stu-id="094d5-127">Choose **Open**, **File** from the **File** menu.</span></span> <span data-ttu-id="094d5-128">Şu klasöre göz atın: `C:\Windows\Microsoft.NET\Framework\v4.0.30319\sql\en`</span><span class="sxs-lookup"><span data-stu-id="094d5-128">Browse to the following folder: `C:\Windows\Microsoft.NET\Framework\v4.0.30319\sql\en`</span></span>  
  
     <span data-ttu-id="094d5-129">Aşağıdaki iki dosyayı seçin ve tıklayın **açık**.</span><span class="sxs-lookup"><span data-stu-id="094d5-129">Select the following two files and click **Open**.</span></span>  
  
    -   <span data-ttu-id="094d5-130">SqlWorkflowInstanceStoreLogic.sql</span><span class="sxs-lookup"><span data-stu-id="094d5-130">SqlWorkflowInstanceStoreLogic.sql</span></span>  
  
    -   <span data-ttu-id="094d5-131">SqlWorkflowInstanceStoreSchema.sql</span><span class="sxs-lookup"><span data-stu-id="094d5-131">SqlWorkflowInstanceStoreSchema.sql</span></span>  
  
3.  <span data-ttu-id="094d5-132">Seçin **SqlWorkflowInstanceStoreSchema.sql** gelen **penceresi** menüsü.</span><span class="sxs-lookup"><span data-stu-id="094d5-132">Choose **SqlWorkflowInstanceStoreSchema.sql** from the **Window** menu.</span></span> <span data-ttu-id="094d5-133">Emin **WF45GettingStartedTutorial** seçili **kullanılabilir veritabanlarını** seçin ve açılır **yürütme** gelen **sorgu**menüsü.</span><span class="sxs-lookup"><span data-stu-id="094d5-133">Ensure that **WF45GettingStartedTutorial** is selected in the **Available Databases** drop-down and choose **Execute** from the **Query** menu.</span></span>  
  
4.  <span data-ttu-id="094d5-134">Seçin **SqlWorkflowInstanceStoreLogic.sql** gelen **penceresi** menüsü.</span><span class="sxs-lookup"><span data-stu-id="094d5-134">Choose **SqlWorkflowInstanceStoreLogic.sql** from the **Window** menu.</span></span> <span data-ttu-id="094d5-135">Emin **WF45GettingStartedTutorial** seçili **kullanılabilir veritabanlarını** seçin ve açılır **yürütme** gelen **sorgu**menüsü.</span><span class="sxs-lookup"><span data-stu-id="094d5-135">Ensure that **WF45GettingStartedTutorial** is selected in the **Available Databases** drop-down and choose **Execute** from the **Query** menu.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="094d5-136">Doğru sırayla önceki iki adımı gerçekleştirmek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="094d5-136">It is important to perform the previous two steps in the correct order.</span></span> <span data-ttu-id="094d5-137">Sorguları sıralamaya yürütülür, hataları ortaya çıkar ve Kalıcılık veritabanı düzgün yapılandırılmamış.</span><span class="sxs-lookup"><span data-stu-id="094d5-137">If the queries are executed out of order, errors occur and the persistence database is not configured correctly.</span></span>  
  
###  <a name="BKMK_AddReference"></a> <span data-ttu-id="094d5-138">DurableInstancing derlemelere başvuru eklemek için</span><span class="sxs-lookup"><span data-stu-id="094d5-138">To add the reference to the DurableInstancing assemblies</span></span>  
  
1.  <span data-ttu-id="094d5-139">Sağ **NumberGuessWorkflowHost** içinde **Çözüm Gezgini** seçip **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="094d5-139">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and select **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="094d5-140">Seçin **derlemeleri** gelen **Başvuru Ekle** listesi ve türü `DurableInstancing` içine **arama derlemeleri** kutusu.</span><span class="sxs-lookup"><span data-stu-id="094d5-140">Select **Assemblies** from the **Add Reference** list, and type `DurableInstancing` into the **Search Assemblies** box.</span></span> <span data-ttu-id="094d5-141">Bu derlemeler filtreler ve seçmek istenen başvurular kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="094d5-141">This filters the assemblies and makes the desired references easier to select.</span></span>  
  
3.  <span data-ttu-id="094d5-142">Yanında onay **System.Activities.durableınstancing** ve **System.Runtime.DurableInstancing** gelen **arama sonuçları** listesinde ve tıklayın**Tamam**.</span><span class="sxs-lookup"><span data-stu-id="094d5-142">Check the checkbox beside **System.Activities.DurableInstancing** and **System.Runtime.DurableInstancing** from the **Search Results** list, and click **OK**.</span></span>  
  
###  <a name="BKMK_CreateForm"></a> <span data-ttu-id="094d5-143">İş akışı ana form oluşturma</span><span class="sxs-lookup"><span data-stu-id="094d5-143">To create the workflow host form</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="094d5-144">Bu yordamdaki adımları eklemek ve form el ile yapılandırmak nasıl açıklar.</span><span class="sxs-lookup"><span data-stu-id="094d5-144">The steps in this procedure describe how to add and configure the form manually.</span></span> <span data-ttu-id="094d5-145">İsterseniz, Öğretici için çözüm dosyalarını indirin ve tamamlanmış formun projeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="094d5-145">If desired, you can download the solution files for the tutorial and add the completed form to the project.</span></span> <span data-ttu-id="094d5-146">Öğretici dosyaları indirmek için bkz [Windows Workflow Foundation (WF45) - başlangıç Öğreticisi](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="094d5-146">To download the tutorial files, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span> <span data-ttu-id="094d5-147">Dosyaları indirdikten sonra sağ **NumberGuessWorkflowHost** ve **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="094d5-147">Once the files are downloaded, right-click **NumberGuessWorkflowHost** and choose **Add Reference**.</span></span> <span data-ttu-id="094d5-148">Bir başvuru ekleyin **System.Windows.Forms** ve **System.Drawing**.</span><span class="sxs-lookup"><span data-stu-id="094d5-148">Add a reference to **System.Windows.Forms** and **System.Drawing**.</span></span> <span data-ttu-id="094d5-149">Yeni bir formdan eklerseniz bu başvuruları otomatik olarak eklenen **Ekle**, **yeni öğe** menüsünde, ancak bir form içeri aktarılırken el ile eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="094d5-149">These references are added automatically if you add a new form from the **Add**, **New Item** menu, but must be added manually when importing a form.</span></span> <span data-ttu-id="094d5-150">Başvuruları eklendikten sonra sağ **NumberGuessWorkflowHost** içinde **Çözüm Gezgini** ve **Ekle**, **var olan öğe**.</span><span class="sxs-lookup"><span data-stu-id="094d5-150">Once the references are added, right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **Existing Item**.</span></span> <span data-ttu-id="094d5-151">Gözat `Form` seçin proje dosyaları klasöründe **WorkflowHostForm.cs** (veya **WorkflowHostForm.vb**), tıklatıp **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="094d5-151">Browse to the `Form` folder in the project files, select **WorkflowHostForm.cs** (or **WorkflowHostForm.vb**), and click **Add**.</span></span> <span data-ttu-id="094d5-152">Formu almak seçtiğiniz sonra sonraki bölüm için aşağı, atlayabilirsiniz [formun yardımcı yöntemler ve özellikler eklemek için](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_AddHelperMethods).</span><span class="sxs-lookup"><span data-stu-id="094d5-152">If you choose to import the form, then you can skip down to the next section, [To add the properties and helper methods of the form](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_AddHelperMethods).</span></span>  
  
1.  <span data-ttu-id="094d5-153">Sağ **NumberGuessWorkflowHost** içinde **Çözüm Gezgini** ve **Ekle**, **yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="094d5-153">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **New Item**.</span></span>  
  
2.  <span data-ttu-id="094d5-154">İçinde **yüklü** şablonları listesinde **Windows Form**, türü `WorkflowHostForm` içinde **adı** ve'ı tıklatın **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="094d5-154">In the **Installed** templates list, choose **Windows Form**, type `WorkflowHostForm` in the **Name** box, and click **Add**.</span></span>  
  
3.  <span data-ttu-id="094d5-155">Form üzerinde aşağıdaki özellikleri yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="094d5-155">Configure the following properties on the form.</span></span>  
  
    |<span data-ttu-id="094d5-156">Özellik</span><span class="sxs-lookup"><span data-stu-id="094d5-156">Property</span></span>|<span data-ttu-id="094d5-157">Değer</span><span class="sxs-lookup"><span data-stu-id="094d5-157">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="094d5-158">FormBorderStyle</span><span class="sxs-lookup"><span data-stu-id="094d5-158">FormBorderStyle</span></span>|<span data-ttu-id="094d5-159">FixedSingle</span><span class="sxs-lookup"><span data-stu-id="094d5-159">FixedSingle</span></span>|  
    |<span data-ttu-id="094d5-160">MaximizeBox</span><span class="sxs-lookup"><span data-stu-id="094d5-160">MaximizeBox</span></span>|<span data-ttu-id="094d5-161">False</span><span class="sxs-lookup"><span data-stu-id="094d5-161">False</span></span>|  
    |<span data-ttu-id="094d5-162">Boyut</span><span class="sxs-lookup"><span data-stu-id="094d5-162">Size</span></span>|<span data-ttu-id="094d5-163">400, 420</span><span class="sxs-lookup"><span data-stu-id="094d5-163">400, 420</span></span>|  
  
4.  <span data-ttu-id="094d5-164">Forma sırayla aşağıdaki denetimleri belirtilen ve configure the properties yönergelerine uygun olarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="094d5-164">Add the following controls to the form in the order specified and configure the properties as directed.</span></span>  
  
    |<span data-ttu-id="094d5-165">Denetim</span><span class="sxs-lookup"><span data-stu-id="094d5-165">Control</span></span>|<span data-ttu-id="094d5-166">Özellik: değer</span><span class="sxs-lookup"><span data-stu-id="094d5-166">Property: Value</span></span>|  
    |-------------|---------------------|  
    |<span data-ttu-id="094d5-167">**Düğme**</span><span class="sxs-lookup"><span data-stu-id="094d5-167">**Button**</span></span>|<span data-ttu-id="094d5-168">Ad: NewGame</span><span class="sxs-lookup"><span data-stu-id="094d5-168">Name: NewGame</span></span><br /><br /> <span data-ttu-id="094d5-169">Konum: 13, 13</span><span class="sxs-lookup"><span data-stu-id="094d5-169">Location: 13, 13</span></span><br /><br /> <span data-ttu-id="094d5-170">Boyut: 75, 23</span><span class="sxs-lookup"><span data-stu-id="094d5-170">Size: 75, 23</span></span><br /><br /> <span data-ttu-id="094d5-171">Metin: Yeni bir oyun</span><span class="sxs-lookup"><span data-stu-id="094d5-171">Text: New Game</span></span>|  
    |<span data-ttu-id="094d5-172">**Etiket**</span><span class="sxs-lookup"><span data-stu-id="094d5-172">**Label**</span></span>|<span data-ttu-id="094d5-173">Konum: 94, 18</span><span class="sxs-lookup"><span data-stu-id="094d5-173">Location: 94, 18</span></span><br /><br /> <span data-ttu-id="094d5-174">Metin: 1 arasında bir sayı tahmin</span><span class="sxs-lookup"><span data-stu-id="094d5-174">Text: Guess a number from 1 to</span></span>|  
    |<span data-ttu-id="094d5-175">**ComboBox**</span><span class="sxs-lookup"><span data-stu-id="094d5-175">**ComboBox**</span></span>|<span data-ttu-id="094d5-176">Ad: NumberRange</span><span class="sxs-lookup"><span data-stu-id="094d5-176">Name: NumberRange</span></span><br /><br /> <span data-ttu-id="094d5-177">DropDownStyle: DropDownList</span><span class="sxs-lookup"><span data-stu-id="094d5-177">DropDownStyle: DropDownList</span></span><br /><br /> <span data-ttu-id="094d5-178">Öğeler: 10, 100, 1000</span><span class="sxs-lookup"><span data-stu-id="094d5-178">Items: 10, 100, 1000</span></span><br /><br /> <span data-ttu-id="094d5-179">Konum: 228, 12</span><span class="sxs-lookup"><span data-stu-id="094d5-179">Location: 228, 12</span></span><br /><br /> <span data-ttu-id="094d5-180">Boyut: 143, 21</span><span class="sxs-lookup"><span data-stu-id="094d5-180">Size: 143, 21</span></span>|  
    |<span data-ttu-id="094d5-181">**Etiket**</span><span class="sxs-lookup"><span data-stu-id="094d5-181">**Label**</span></span>|<span data-ttu-id="094d5-182">Konum: 13, 43</span><span class="sxs-lookup"><span data-stu-id="094d5-182">Location: 13, 43</span></span><br /><br /> <span data-ttu-id="094d5-183">Metin: İş akışı türü</span><span class="sxs-lookup"><span data-stu-id="094d5-183">Text: Workflow type</span></span>|  
    |<span data-ttu-id="094d5-184">**ComboBox**</span><span class="sxs-lookup"><span data-stu-id="094d5-184">**ComboBox**</span></span>|<span data-ttu-id="094d5-185">Ad: WorkflowType</span><span class="sxs-lookup"><span data-stu-id="094d5-185">Name: WorkflowType</span></span><br /><br /> <span data-ttu-id="094d5-186">DropDownStyle: DropDownList</span><span class="sxs-lookup"><span data-stu-id="094d5-186">DropDownStyle: DropDownList</span></span><br /><br /> <span data-ttu-id="094d5-187">Öğeleri: StateMachineNumberGuessWorkflow, FlowchartNumberGuessWorkflow, SequentialNumberGuessWorkflow</span><span class="sxs-lookup"><span data-stu-id="094d5-187">Items: StateMachineNumberGuessWorkflow, FlowchartNumberGuessWorkflow, SequentialNumberGuessWorkflow</span></span><br /><br /> <span data-ttu-id="094d5-188">Konum: 94, 40</span><span class="sxs-lookup"><span data-stu-id="094d5-188">Location: 94, 40</span></span><br /><br /> <span data-ttu-id="094d5-189">Boyut: 277, 21</span><span class="sxs-lookup"><span data-stu-id="094d5-189">Size: 277, 21</span></span>|  
    |<span data-ttu-id="094d5-190">**Etiket**</span><span class="sxs-lookup"><span data-stu-id="094d5-190">**Label**</span></span>|<span data-ttu-id="094d5-191">Ad: WorkflowVersion</span><span class="sxs-lookup"><span data-stu-id="094d5-191">Name: WorkflowVersion</span></span><br /><br /> <span data-ttu-id="094d5-192">Konum: 13, 362</span><span class="sxs-lookup"><span data-stu-id="094d5-192">Location: 13, 362</span></span><br /><br /> <span data-ttu-id="094d5-193">Metin: İş akışı sürümü</span><span class="sxs-lookup"><span data-stu-id="094d5-193">Text: Workflow version</span></span>|  
    |<span data-ttu-id="094d5-194">**GroupBox**</span><span class="sxs-lookup"><span data-stu-id="094d5-194">**GroupBox**</span></span>|<span data-ttu-id="094d5-195">Konum: 13, 67</span><span class="sxs-lookup"><span data-stu-id="094d5-195">Location: 13, 67</span></span><br /><br /> <span data-ttu-id="094d5-196">Boyut: 358, 287</span><span class="sxs-lookup"><span data-stu-id="094d5-196">Size: 358, 287</span></span><br /><br /> <span data-ttu-id="094d5-197">Metin: oyunu</span><span class="sxs-lookup"><span data-stu-id="094d5-197">Text: Game</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="094d5-198">Aşağıdaki denetimler eklerken, bunları GroupBox yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="094d5-198">When adding the following controls, put them into the GroupBox.</span></span>  
  
    |<span data-ttu-id="094d5-199">Denetim</span><span class="sxs-lookup"><span data-stu-id="094d5-199">Control</span></span>|<span data-ttu-id="094d5-200">Özellik: değer</span><span class="sxs-lookup"><span data-stu-id="094d5-200">Property: Value</span></span>|  
    |-------------|---------------------|  
    |<span data-ttu-id="094d5-201">**Etiket**</span><span class="sxs-lookup"><span data-stu-id="094d5-201">**Label**</span></span>|<span data-ttu-id="094d5-202">Konum: 7, 20</span><span class="sxs-lookup"><span data-stu-id="094d5-202">Location: 7, 20</span></span><br /><br /> <span data-ttu-id="094d5-203">Metin: İş akışı örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="094d5-203">Text: Workflow Instance Id</span></span>|  
    |<span data-ttu-id="094d5-204">**ComboBox**</span><span class="sxs-lookup"><span data-stu-id="094d5-204">**ComboBox**</span></span>|<span data-ttu-id="094d5-205">Ad: InstanceId</span><span class="sxs-lookup"><span data-stu-id="094d5-205">Name: InstanceId</span></span><br /><br /> <span data-ttu-id="094d5-206">DropDownStyle: DropDownList</span><span class="sxs-lookup"><span data-stu-id="094d5-206">DropDownStyle: DropDownList</span></span><br /><br /> <span data-ttu-id="094d5-207">Konum: 121, 17</span><span class="sxs-lookup"><span data-stu-id="094d5-207">Location: 121, 17</span></span><br /><br /> <span data-ttu-id="094d5-208">Boyut: 227, 21</span><span class="sxs-lookup"><span data-stu-id="094d5-208">Size: 227, 21</span></span>|  
    |<span data-ttu-id="094d5-209">**Etiket**</span><span class="sxs-lookup"><span data-stu-id="094d5-209">**Label**</span></span>|<span data-ttu-id="094d5-210">Konum: 7, 47</span><span class="sxs-lookup"><span data-stu-id="094d5-210">Location: 7, 47</span></span><br /><br /> <span data-ttu-id="094d5-211">Metin: tahmin</span><span class="sxs-lookup"><span data-stu-id="094d5-211">Text: Guess</span></span>|  
    |<span data-ttu-id="094d5-212">**TextBox**</span><span class="sxs-lookup"><span data-stu-id="094d5-212">**TextBox**</span></span>|<span data-ttu-id="094d5-213">Ad: tahmin</span><span class="sxs-lookup"><span data-stu-id="094d5-213">Name: Guess</span></span><br /><br /> <span data-ttu-id="094d5-214">Konum: 50, 44</span><span class="sxs-lookup"><span data-stu-id="094d5-214">Location: 50, 44</span></span><br /><br /> <span data-ttu-id="094d5-215">Boyut: 65, 20</span><span class="sxs-lookup"><span data-stu-id="094d5-215">Size: 65, 20</span></span>|  
    |<span data-ttu-id="094d5-216">**Düğme**</span><span class="sxs-lookup"><span data-stu-id="094d5-216">**Button**</span></span>|<span data-ttu-id="094d5-217">Ad: EnterGuess</span><span class="sxs-lookup"><span data-stu-id="094d5-217">Name: EnterGuess</span></span><br /><br /> <span data-ttu-id="094d5-218">Konum: 121, 42</span><span class="sxs-lookup"><span data-stu-id="094d5-218">Location: 121, 42</span></span><br /><br /> <span data-ttu-id="094d5-219">Boyut: 75, 23</span><span class="sxs-lookup"><span data-stu-id="094d5-219">Size: 75, 23</span></span><br /><br /> <span data-ttu-id="094d5-220">Metin: Tahmin girin</span><span class="sxs-lookup"><span data-stu-id="094d5-220">Text: Enter Guess</span></span>|  
    |<span data-ttu-id="094d5-221">**Düğme**</span><span class="sxs-lookup"><span data-stu-id="094d5-221">**Button**</span></span>|<span data-ttu-id="094d5-222">Ad: QuitGame</span><span class="sxs-lookup"><span data-stu-id="094d5-222">Name: QuitGame</span></span><br /><br /> <span data-ttu-id="094d5-223">Konum: 274, 42</span><span class="sxs-lookup"><span data-stu-id="094d5-223">Location: 274, 42</span></span><br /><br /> <span data-ttu-id="094d5-224">Boyut: 75, 23</span><span class="sxs-lookup"><span data-stu-id="094d5-224">Size: 75, 23</span></span><br /><br /> <span data-ttu-id="094d5-225">Metin: Çık</span><span class="sxs-lookup"><span data-stu-id="094d5-225">Text: Quit</span></span>|  
    |<span data-ttu-id="094d5-226">**TextBox**</span><span class="sxs-lookup"><span data-stu-id="094d5-226">**TextBox**</span></span>|<span data-ttu-id="094d5-227">Ad: WorkflowStatus</span><span class="sxs-lookup"><span data-stu-id="094d5-227">Name: WorkflowStatus</span></span><br /><br /> <span data-ttu-id="094d5-228">Konum: 10, 73</span><span class="sxs-lookup"><span data-stu-id="094d5-228">Location: 10, 73</span></span><br /><br /> <span data-ttu-id="094d5-229">Çok satırlı: True</span><span class="sxs-lookup"><span data-stu-id="094d5-229">Multiline: True</span></span><br /><br /> <span data-ttu-id="094d5-230">Salt okunur: True</span><span class="sxs-lookup"><span data-stu-id="094d5-230">ReadOnly: True</span></span><br /><br /> <span data-ttu-id="094d5-231">Kaydırma çubukları: dikey</span><span class="sxs-lookup"><span data-stu-id="094d5-231">ScrollBars: Vertical</span></span><br /><br /> <span data-ttu-id="094d5-232">Boyut: 338, 208 numaralı satırları</span><span class="sxs-lookup"><span data-stu-id="094d5-232">Size: 338, 208</span></span>|  
  
5.  <span data-ttu-id="094d5-233">Ayarlama **AcceptButton** özellik formun **EnterGuess**.</span><span class="sxs-lookup"><span data-stu-id="094d5-233">Set the **AcceptButton** property of the form to **EnterGuess**.</span></span>  
  
 <span data-ttu-id="094d5-234">Aşağıdaki örnekte, tamamlanmış form gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="094d5-234">The following example illustrates the completed form.</span></span>  
  
 <span data-ttu-id="094d5-235">![WF45 Çalışmaya başlama Öğreticisi iş akışı ana formu](../../../docs/framework/windows-workflow-foundation/media/wf45gettingstartedtutorialworkflowhostform.png "WF45GettingStartedTutorialWorkflowHostForm")</span><span class="sxs-lookup"><span data-stu-id="094d5-235">![WF45 Getting Started Tutorial Workflow Host Form](../../../docs/framework/windows-workflow-foundation/media/wf45gettingstartedtutorialworkflowhostform.png "WF45GettingStartedTutorialWorkflowHostForm")</span></span>  
  
###  <a name="BKMK_AddHelperMethods"></a> <span data-ttu-id="094d5-236">Formun yardımcı yöntemler ve özellikler eklemek için</span><span class="sxs-lookup"><span data-stu-id="094d5-236">To add the properties and helper methods of the form</span></span>  
 <span data-ttu-id="094d5-237">Bu bölümdeki adımlarda, özellikler ve yardımcı yöntemler çalıştıran ve sayı tahmin iş akışları sürdürme desteklemek için kullanıcı Arabirimi formun yapılandırma formu sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="094d5-237">The steps in this section add properties and helper methods to the form class that configure the UI of the form to support running and resuming number guess workflows.</span></span>  
  
1.  <span data-ttu-id="094d5-238">Sağ **WorkflowHostForm** içinde **Çözüm Gezgini** ve **kodu görüntüle**.</span><span class="sxs-lookup"><span data-stu-id="094d5-238">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>  
  
2.  <span data-ttu-id="094d5-239">Aşağıdaki `using` (veya `Imports`) deyimini dosyanın diğer üst `using` (veya `Imports`) ifadeleri.</span><span class="sxs-lookup"><span data-stu-id="094d5-239">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Windows.Forms  
    Imports System.Activities.DurableInstancing  
    Imports System.Activities  
    Imports System.Data.SqlClient  
    Imports System.IO  
    ```  
  
    ```csharp  
    using System.Windows.Forms;  
    using System.Activities.DurableInstancing;  
    using System.Activities;  
    using System.Data.SqlClient;  
    using System.IO;  
    ```  
  
3.  <span data-ttu-id="094d5-240">Aşağıdaki üye bildirimi ekleme **WorkflowHostForm** sınıfı.</span><span class="sxs-lookup"><span data-stu-id="094d5-240">Add the following member declarations to the **WorkflowHostForm** class.</span></span>  
  
    ```vb  
    Const connectionString = "Server=.\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI"  
    Dim store As SqlWorkflowInstanceStore  
    Dim WorkflowStarting As Boolean  
    ```  
  
    ```csharp  
    const string connectionString = "Server=.\\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI";  
    SqlWorkflowInstanceStore store;  
    bool WorkflowStarting;  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="094d5-241">Bağlantı dizenizi farklı ise, güncelleştirme `connectionString` veritabanınıza başvurmak için.</span><span class="sxs-lookup"><span data-stu-id="094d5-241">If your connection string is different, update `connectionString` to refer to your database.</span></span>  
  
4.  <span data-ttu-id="094d5-242">Ekleme bir `WorkflowInstanceId` özelliğini `WorkflowFormHost` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="094d5-242">Add a `WorkflowInstanceId` property to the `WorkflowFormHost` class.</span></span>  
  
    ```vb  
    Public ReadOnly Property WorkflowInstanceId() As Guid  
        Get  
            If InstanceId.SelectedIndex = -1 Then  
                Return Guid.Empty  
            Else  
                Return New Guid(InstanceId.SelectedItem.ToString())  
            End If  
        End Get  
    End Property  
    ```  
  
    ```csharp  
    public Guid WorkflowInstanceId  
    {  
        get  
        {  
            return InstanceId.SelectedIndex == -1 ? Guid.Empty : (Guid)InstanceId.SelectedItem;  
        }  
    }  
    ```  
  
     <span data-ttu-id="094d5-243">`InstanceId` Birleşik giriş kutusu kalıcı iş akışı örnek kimlikleri listesini görüntüler ve `WorkflowInstanceId` özelliği şu anda seçili iş akışına döndürür.</span><span class="sxs-lookup"><span data-stu-id="094d5-243">The `InstanceId` combo box displays a list of persisted workflow instance ids, and the `WorkflowInstanceId` property returns the currently selected workflow.</span></span>  
  
5.  <span data-ttu-id="094d5-244">Form için bir işleyici eklemek `Load` olay.</span><span class="sxs-lookup"><span data-stu-id="094d5-244">Add a handler for the form `Load` event.</span></span> <span data-ttu-id="094d5-245">İşleyiciyi eklemek için geçiş **Tasarım görünümü** formu için **olayları** simgesi en üstündeki **özellikleri** penceresi ve çift **yük**.</span><span class="sxs-lookup"><span data-stu-id="094d5-245">To add the handler, switch to **Design View** for the form, click the **Events** icon at the top of the **Properties** window, and double-click **Load**.</span></span>  
  
    ```vb  
    Private Sub WorkflowHostForm_Load(sender As Object, e As EventArgs) Handles Me.Load  
  
    End Sub  
    ```  
  
    ```csharp  
    private void WorkflowHostForm_Load(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
6.  <span data-ttu-id="094d5-246">Aşağıdaki kodu ekleyin `WorkflowHostForm_Load`.</span><span class="sxs-lookup"><span data-stu-id="094d5-246">Add the following code to `WorkflowHostForm_Load`.</span></span>  
  
    ```vb  
    'Initialize the store and configure it so that it can be used for  
    'multiple WorkflowApplication instances.  
    store = New SqlWorkflowInstanceStore(connectionString)  
    WorkflowApplication.CreateDefaultInstanceOwner(store, Nothing, WorkflowIdentityFilter.Any)  
  
    'Set default ComboBox selections.  
    NumberRange.SelectedIndex = 0  
    WorkflowType.SelectedIndex = 0  
  
    ListPersistedWorkflows()  
    ```  
  
    ```csharp  
    // Initialize the store and configure it so that it can be used for  
    // multiple WorkflowApplication instances.  
    store = new SqlWorkflowInstanceStore(connectionString);  
    WorkflowApplication.CreateDefaultInstanceOwner(store, null, WorkflowIdentityFilter.Any);  
  
    // Set default ComboBox selections.  
    NumberRange.SelectedIndex = 0;  
    WorkflowType.SelectedIndex = 0;  
  
    ListPersistedWorkflows();  
    ```  
  
     <span data-ttu-id="094d5-247">Formun yüklediğinde, `SqlWorkflowInstanceStore` olan yapılandırılmış, aralık ve iş akışı türü birleşik giriş kutuları varsayılan değerlere ayarlanır ve kalıcı iş akışı örnekleri eklenir `InstanceId` birleşik giriş kutusu.</span><span class="sxs-lookup"><span data-stu-id="094d5-247">When the form loads, the `SqlWorkflowInstanceStore` is configured, the range and workflow type combo boxes are set to default values, and the persisted workflow instances are added to the `InstanceId` combo box.</span></span>  
  
7.  <span data-ttu-id="094d5-248">Ekleme bir `SelectedIndexChanged` işleyicisi `InstanceId`.</span><span class="sxs-lookup"><span data-stu-id="094d5-248">Add a `SelectedIndexChanged` handler for `InstanceId`.</span></span> <span data-ttu-id="094d5-249">İşleyiciyi eklemek için geçiş **Tasarım görünümü** formu seçin `InstanceId` Kombo kutusu tıklayın **olayları** simgesi en üstündeki **özellikleri** penceresinde ve çift **SelectedIndexChanged**.</span><span class="sxs-lookup"><span data-stu-id="094d5-249">To add the handler, switch to **Design View** for the form, select the `InstanceId` combo box, click the **Events** icon at the top of the **Properties** window, and double-click **SelectedIndexChanged**.</span></span>  
  
    ```vb  
    Private Sub InstanceId_SelectedIndexChanged(sender As Object, e As EventArgs) Handles InstanceId.SelectedIndexChanged  
  
    End Sub  
    ```  
  
    ```csharp  
    private void InstanceId_SelectedIndexChanged(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
8.  <span data-ttu-id="094d5-250">Aşağıdaki kodu ekleyin `InstanceId_SelectedIndexChanged`.</span><span class="sxs-lookup"><span data-stu-id="094d5-250">Add the following code to `InstanceId_SelectedIndexChanged`.</span></span> <span data-ttu-id="094d5-251">Bu işleyici birleşik giriş kutusunu kullanarak bir iş akışı kullanıcının seçtiği her durum penceresi güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="094d5-251">Whenever the user selects a workflow by using the combo box this handler updates the status window.</span></span>  
  
    ```vb  
    If InstanceId.SelectedIndex = -1 Then  
        Return  
    End If  
  
    'Clear the status window.  
    WorkflowStatus.Clear()  
  
    'Get the workflow version and display it.  
    'If the workflow is just starting then this info will not  
    'be available in the persistence store so do not try and retrieve it.  
    If Not WorkflowStarting Then  
        Dim instance As WorkflowApplicationInstance = _  
            WorkflowApplication.GetInstance(WorkflowInstanceId, store)  
  
        WorkflowVersion.Text = _  
            WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity)  
  
        'Unload the instance.  
        instance.Abandon()  
    End If  
    ```  
  
    ```csharp  
    if (InstanceId.SelectedIndex == -1)  
    {  
        return;  
    }  
  
    // Clear the status window.  
    WorkflowStatus.Clear();  
  
    // Get the workflow version and display it.  
    // If the workflow is just starting then this info will not  
    // be available in the persistence store so do not try and retrieve it.  
    if (!WorkflowStarting)  
    {  
        WorkflowApplicationInstance instance =  
            WorkflowApplication.GetInstance(this.WorkflowInstanceId, store);  
  
        WorkflowVersion.Text =  
            WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity);  
  
        // Unload the instance.  
        instance.Abandon();  
    }  
    ```  
  
9. <span data-ttu-id="094d5-252">Aşağıdaki `ListPersistedWorkflows` form sınıfı için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="094d5-252">Add the following `ListPersistedWorkflows` method to the form class.</span></span>  
  
    ```vb  
    Private Sub ListPersistedWorkflows()  
        Using localCon As New SqlConnection(connectionString)  
            Dim localCmd As String = _  
                "Select [InstanceId] from [System.Activities.DurableInstancing].[Instances] Order By [CreationTime]"  
  
            Dim cmd As SqlCommand = localCon.CreateCommand()  
            cmd.CommandText = localCmd  
            localCon.Open()  
            Using reader As SqlDataReader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
  
                While (reader.Read())  
                    'Get the InstanceId of the persisted Workflow.  
                    Dim id As Guid = Guid.Parse(reader(0).ToString())  
                    InstanceId.Items.Add(id)  
                End While  
            End Using  
        End Using  
    End Sub  
    ```  
  
    ```csharp  
    using (SqlConnection localCon = new SqlConnection(connectionString))  
    {  
        string localCmd =  
            "Select [InstanceId] from [System.Activities.DurableInstancing].[Instances] Order By [CreationTime]";  
  
        SqlCommand cmd = localCon.CreateCommand();  
        cmd.CommandText = localCmd;  
        localCon.Open();  
        using (SqlDataReader reader = cmd.ExecuteReader(CommandBehavior.CloseConnection))  
        {  
            while (reader.Read())  
            {  
                // Get the InstanceId of the persisted Workflow  
                Guid id = Guid.Parse(reader[0].ToString());  
                InstanceId.Items.Add(id);  
            }  
        }  
    }  
    ```  
  
     <span data-ttu-id="094d5-253">`ListPersistedWorkflows` kalıcı iş akışı örnekleri için örnek deposuna sorgular ve ekler için örnek kimlikleri `cboInstanceId` birleşik giriş kutusu.</span><span class="sxs-lookup"><span data-stu-id="094d5-253">`ListPersistedWorkflows` queries the instance store for persisted workflow instances, and adds the instance ids to the `cboInstanceId` combo box.</span></span>  
  
10. <span data-ttu-id="094d5-254">Aşağıdaki `UpdateStatus` yöntemi ve form sınıfına karşılık gelen temsilci.</span><span class="sxs-lookup"><span data-stu-id="094d5-254">Add the following `UpdateStatus` method and corresponding delegate to the form class.</span></span> <span data-ttu-id="094d5-255">Bu yöntem form üzerindeki durum penceresi şu anda çalışan bir iş akışı durumunu güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="094d5-255">This method updates the status window on the form with the status of the currently running workflow.</span></span>  
  
    ```vb  
    Private Delegate Sub UpdateStatusDelegate(msg As String)  
    Public Sub UpdateStatus(msg As String)  
        'We may be on a different thread so we need to  
        'make this call using BeginInvoke.  
        If InvokeRequired Then  
            BeginInvoke(New UpdateStatusDelegate(AddressOf UpdateStatus), msg)  
        Else  
            If Not msg.EndsWith(vbCrLf) Then  
                msg = msg & vbCrLf  
            End If  
  
            WorkflowStatus.AppendText(msg)  
  
            'Ensure that the newly added status is visible.  
            WorkflowStatus.SelectionStart = WorkflowStatus.Text.Length  
            WorkflowStatus.ScrollToCaret()  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private delegate void UpdateStatusDelegate(string msg);  
    public void UpdateStatus(string msg)  
    {  
        // We may be on a different thread so we need to  
        // make this call using BeginInvoke.  
        if (InvokeRequired)  
        {  
            BeginInvoke(new UpdateStatusDelegate(UpdateStatus), msg);  
        }  
        else  
        {  
            if (!msg.EndsWith("\r\n"))  
            {  
                msg += "\r\n";  
            }  
            WorkflowStatus.AppendText(msg);  
  
            WorkflowStatus.SelectionStart = WorkflowStatus.Text.Length;  
            WorkflowStatus.ScrollToCaret();  
        }  
    }  
    ```  
  
11. <span data-ttu-id="094d5-256">Aşağıdaki `GameOver` yöntemi ve form sınıfına karşılık gelen temsilci.</span><span class="sxs-lookup"><span data-stu-id="094d5-256">Add the following `GameOver` method and corresponding delegate to the form class.</span></span> <span data-ttu-id="094d5-257">Bir iş akışı tamamlandığında, bu yöntem UI form tamamlanan iş akışı örnek kimliği kaldırarak güncelleştirmeleri gelen **InstanceId** birleşik giriş kutusu.</span><span class="sxs-lookup"><span data-stu-id="094d5-257">When a workflow completes, this method updates the form UI by removing the instance id of the completed workflow from the **InstanceId** combo box.</span></span>  
  
    ```vb  
    Private Delegate Sub GameOverDelegate()  
    Private Sub GameOver()  
        If InvokeRequired Then  
            BeginInvoke(New GameOverDelegate(AddressOf GameOver))  
        Else  
            'Remove this instance from the InstanceId combo box.  
            InstanceId.Items.Remove(InstanceId.SelectedItem)  
            InstanceId.SelectedIndex = -1  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private delegate void GameOverDelegate();  
    private void GameOver()  
    {  
        if (InvokeRequired)  
        {  
            BeginInvoke(new GameOverDelegate(GameOver));  
        }  
        else  
        {  
            // Remove this instance from the combo box  
            InstanceId.Items.Remove(InstanceId.SelectedItem);  
            InstanceId.SelectedIndex = -1;  
        }  
    }  
    ```  
  
###  <a name="BKMK_ConfigureWorkflowApplication"></a> <span data-ttu-id="094d5-258">Örnek deposu, iş akışı yaşam döngüsü işleyicileri ve Uzantıları'nı yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="094d5-258">To configure the instance store, workflow lifecycle handlers, and extensions</span></span>  
  
1.  <span data-ttu-id="094d5-259">Ekleme bir `ConfigureWorkflowApplication` form sınıfı için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="094d5-259">Add a `ConfigureWorkflowApplication` method to the form class.</span></span>  
  
    ```vb  
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)  
  
    End Sub  
    ```  
  
    ```csharp  
    private void ConfigureWorkflowApplication(WorkflowApplication wfApp)  
    {      
    }  
    ```  
  
     <span data-ttu-id="094d5-260">Bu yöntem yapılandırır `WorkflowApplication`, istenen uzantıların ekler ve iş akışı yaşam döngüsü olayları için işleyiciler ekler.</span><span class="sxs-lookup"><span data-stu-id="094d5-260">This method configures the `WorkflowApplication`, adds the desired extensions, and adds handlers for the workflow lifecycle events.</span></span>  
  
2.  <span data-ttu-id="094d5-261">İçinde `ConfigureWorkflowApplication`, belirtin `SqlWorkflowInstanceStore` için `WorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="094d5-261">In `ConfigureWorkflowApplication`, specify the `SqlWorkflowInstanceStore` for the `WorkflowApplication`.</span></span>  
  
    ```vb  
    'Configure the persistence store.  
    wfApp.InstanceStore = store  
    ```  
  
    ```csharp  
    // Configure the persistence store.  
    wfApp.InstanceStore = store;  
    ```  
  
3.  <span data-ttu-id="094d5-262">Ardından, oluşturun bir `StringWriter` ekleyin ve örnek `Extensions` koleksiyonunu `WorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="094d5-262">Next, create a `StringWriter` instance and add it to the `Extensions` collection of the `WorkflowApplication`.</span></span> <span data-ttu-id="094d5-263">Olduğunda bir `StringWriter` uzantılarını da yakalar tüm eklenir `WriteLine` etkinlik çıkışı.</span><span class="sxs-lookup"><span data-stu-id="094d5-263">When a `StringWriter` is added to the extensions it captures all `WriteLine` activity output.</span></span> <span data-ttu-id="094d5-264">İş akışı boş olduğunda `WriteLine` çıkış ayıklanan gelen `StringWriter` ve formda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="094d5-264">When the workflow becomes idle, the `WriteLine` output can be extracted from the `StringWriter` and displayed on the form.</span></span>  
  
    ```vb  
    'Add a StringWriter to the extensions. This captures the output  
    'from the WriteLine activities so we can display it in the form.  
    Dim sw As New StringWriter()  
    wfApp.Extensions.Add(sw)  
    ```  
  
    ```csharp  
    // Add a StringWriter to the extensions. This captures the output  
    // from the WriteLine activities so we can display it in the form.  
    StringWriter sw = new StringWriter();  
    wfApp.Extensions.Add(sw);  
    ```  
  
4.  <span data-ttu-id="094d5-265">Aşağıdaki işleyicisi eklemek `Completed` olay.</span><span class="sxs-lookup"><span data-stu-id="094d5-265">Add the following handler for the `Completed` event.</span></span> <span data-ttu-id="094d5-266">Bir iş akışı başarıyla tamamlandığında, sayısını numarası için durum penceresi görüntülenir tahmin çekildiği kapatır.</span><span class="sxs-lookup"><span data-stu-id="094d5-266">When a workflow successfully completes, the number of turns taken to guess the number is displayed to the status window.</span></span> <span data-ttu-id="094d5-267">İş akışı sona ererse, sonlandırma neden olan özel durum bilgileri görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="094d5-267">If the workflow terminates, the exception information that caused the termination is displayed.</span></span> <span data-ttu-id="094d5-268">İşleyici sonunda `GameOver` yöntemi çağrıldığında, tamamlanan iş akışı iş akışı listeden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="094d5-268">At the end of the handler the `GameOver` method is called, which removes the completed workflow from the workflow list.</span></span>  
  
    ```vb  
    wfApp.Completed = _  
        Sub(e As WorkflowApplicationCompletedEventArgs)  
            If e.CompletionState = ActivityInstanceState.Faulted Then  
                UpdateStatus(String.Format("Workflow Terminated. Exception: {0}" & vbCrLf & "{1}", _  
                    e.TerminationException.GetType().FullName, _  
                    e.TerminationException.Message))  
            ElseIf e.CompletionState = ActivityInstanceState.Canceled Then  
                UpdateStatus("Workflow Canceled.")  
            Else  
                Dim Turns As Integer = Convert.ToInt32(e.Outputs("Turns"))  
                UpdateStatus(String.Format("Congratulations, you guessed the number in {0} turns.", Turns))  
            End If  
            GameOver()  
        End Sub  
    ```  
  
    ```csharp  
    wfApp.Completed = delegate(WorkflowApplicationCompletedEventArgs e)  
    {  
        if (e.CompletionState == ActivityInstanceState.Faulted)  
        {  
            UpdateStatus(string.Format("Workflow Terminated. Exception: {0}\r\n{1}",  
                e.TerminationException.GetType().FullName,  
                e.TerminationException.Message));  
        }  
        else if (e.CompletionState == ActivityInstanceState.Canceled)  
        {  
            UpdateStatus("Workflow Canceled.");  
        }  
        else  
        {  
            int Turns = Convert.ToInt32(e.Outputs["Turns"]);  
            UpdateStatus(string.Format("Congratulations, you guessed the number in {0} turns.", Turns));  
        }  
        GameOver();  
    };  
    ```  
  
5.  <span data-ttu-id="094d5-269">Aşağıdaki `Aborted` ve `OnUnhandledException` işleyicileri.</span><span class="sxs-lookup"><span data-stu-id="094d5-269">Add the following `Aborted` and `OnUnhandledException` handlers.</span></span> <span data-ttu-id="094d5-270">`GameOver` Gelen yönteminin çağrılmaması `Aborted` işleyici ne zaman bir iş akışı örneği durduruldu çünkü değil sonlandırın ve daha sonraki bir zamanda örneği sürdürmek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="094d5-270">The `GameOver` method is not called from the `Aborted` handler because when a workflow instance is aborted, it does not terminate, and it is possible to resume the instance at a later time.</span></span>  
  
    ```vb  
    wfApp.Aborted = _  
        Sub(e As WorkflowApplicationAbortedEventArgs)  
            UpdateStatus(String.Format("Workflow Aborted. Exception: {0}" & vbCrLf & "{1}", _  
                e.Reason.GetType().FullName, _  
                e.Reason.Message))  
        End Sub  
  
    wfApp.OnUnhandledException = _  
        Function(e As WorkflowApplicationUnhandledExceptionEventArgs)  
            UpdateStatus(String.Format("Unhandled Exception: {0}" & vbCrLf & "{1}", _  
                e.UnhandledException.GetType().FullName, _  
                e.UnhandledException.Message))  
            GameOver()  
            Return UnhandledExceptionAction.Terminate  
        End Function  
    ```  
  
    ```csharp  
    wfApp.Aborted = delegate(WorkflowApplicationAbortedEventArgs e)  
    {  
        UpdateStatus(string.Format("Workflow Aborted. Exception: {0}\r\n{1}",  
                e.Reason.GetType().FullName,  
                e.Reason.Message));  
    };  
  
    wfApp.OnUnhandledException = delegate(WorkflowApplicationUnhandledExceptionEventArgs e)  
    {  
        UpdateStatus(string.Format("Unhandled Exception: {0}\r\n{1}",  
                e.UnhandledException.GetType().FullName,  
                e.UnhandledException.Message));  
        GameOver();  
        return UnhandledExceptionAction.Terminate;  
    };  
    ```  
  
6.  <span data-ttu-id="094d5-271">Aşağıdaki `PersistableIdle` işleyici.</span><span class="sxs-lookup"><span data-stu-id="094d5-271">Add the following `PersistableIdle` handler.</span></span> <span data-ttu-id="094d5-272">Bu işleyici alır `StringWriter` eklendikten sonra uzantı ayıklar çıktısı `WriteLine` etkinlikleri ve durum penceresinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="094d5-272">This handler retrieves the `StringWriter` extension that was added, extracts the output from the `WriteLine` activities, and displays it in the status window.</span></span>  
  
    ```vb  
    wfApp.PersistableIdle = _  
        Function(e As WorkflowApplicationIdleEventArgs)  
            'Send the current WriteLine outputs to the status window.  
            Dim writers = e.GetInstanceExtensions(Of StringWriter)()  
            For Each writer In writers  
                UpdateStatus(writer.ToString())  
            Next  
            Return PersistableIdleAction.Unload  
        End Function  
    ```  
  
    ```csharp  
    wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)  
    {  
        // Send the current WriteLine outputs to the status window.  
        var writers = e.GetInstanceExtensions<StringWriter>();  
        foreach (var writer in writers)  
        {  
            UpdateStatus(writer.ToString());  
        }  
        return PersistableIdleAction.Unload;  
    };  
    ```  
  
     <span data-ttu-id="094d5-273"><xref:System.Activities.PersistableIdleAction> Numaralandırması üç değer vardır: <xref:System.Activities.PersistableIdleAction.None>, <xref:System.Activities.PersistableIdleAction.Persist>, ve <xref:System.Activities.PersistableIdleAction.Unload>.</span><span class="sxs-lookup"><span data-stu-id="094d5-273">The <xref:System.Activities.PersistableIdleAction> enumeration has three values: <xref:System.Activities.PersistableIdleAction.None>, <xref:System.Activities.PersistableIdleAction.Persist>, and <xref:System.Activities.PersistableIdleAction.Unload>.</span></span> <span data-ttu-id="094d5-274"><xref:System.Activities.PersistableIdleAction.Persist> neden olur, kalıcı hale getirmek için iş akışını kaldırmak iş akışı neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="094d5-274"><xref:System.Activities.PersistableIdleAction.Persist> causes the workflow to persist but it does not cause the workflow to unload.</span></span> <span data-ttu-id="094d5-275"><xref:System.Activities.PersistableIdleAction.Unload> İş akışı kalıcı hale getirmek ve kaldırılmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="094d5-275"><xref:System.Activities.PersistableIdleAction.Unload> causes the workflow to persist and be unloaded.</span></span>  
  
     <span data-ttu-id="094d5-276">Aşağıdaki örnek, tamamlanan, `ConfigureWorkflowApplication` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="094d5-276">The following example is the completed `ConfigureWorkflowApplication` method.</span></span>  
  
    ```vb  
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)  
        'Configure the persistence store.  
        wfApp.InstanceStore = store  
  
        'Add a StringWriter to the extensions. This captures the output  
        'from the WriteLine activities so we can display it in the form.  
        Dim sw As New StringWriter()  
        wfApp.Extensions.Add(sw)  
  
        wfApp.Completed = _  
            Sub(e As WorkflowApplicationCompletedEventArgs)  
                If e.CompletionState = ActivityInstanceState.Faulted Then  
                    UpdateStatus(String.Format("Workflow Terminated. Exception: {0}" & vbCrLf & "{1}", _  
                        e.TerminationException.GetType().FullName, _  
                        e.TerminationException.Message))  
                ElseIf e.CompletionState = ActivityInstanceState.Canceled Then  
                    UpdateStatus("Workflow Canceled.")  
                Else  
                    Dim Turns As Integer = Convert.ToInt32(e.Outputs("Turns"))  
                    UpdateStatus(String.Format("Congratulations, you guessed the number in {0} turns.", Turns))  
                End If  
                GameOver()  
            End Sub  
  
        wfApp.Aborted = _  
            Sub(e As WorkflowApplicationAbortedEventArgs)  
                UpdateStatus(String.Format("Workflow Aborted. Exception: {0}" & vbCrLf & "{1}", _  
                    e.Reason.GetType().FullName, _  
                    e.Reason.Message))  
            End Sub  
  
        wfApp.OnUnhandledException = _  
            Function(e As WorkflowApplicationUnhandledExceptionEventArgs)  
                UpdateStatus(String.Format("Unhandled Exception: {0}" & vbCrLf & "{1}", _  
                    e.UnhandledException.GetType().FullName, _  
                    e.UnhandledException.Message))  
                GameOver()  
                Return UnhandledExceptionAction.Terminate  
            End Function  
  
        wfApp.PersistableIdle = _  
            Function(e As WorkflowApplicationIdleEventArgs)  
                'Send the current WriteLine outputs to the status window.  
                Dim writers = e.GetInstanceExtensions(Of StringWriter)()  
                For Each writer In writers  
                    UpdateStatus(writer.ToString())  
                Next  
                Return PersistableIdleAction.Unload  
            End Function  
    End Sub  
    ```  
  
    ```csharp  
    private void ConfigureWorkflowApplication(WorkflowApplication wfApp)  
    {  
        // Configure the persistence store.  
        wfApp.InstanceStore = store;  
  
        // Add a StringWriter to the extensions. This captures the output  
        // from the WriteLine activities so we can display it in the form.  
        StringWriter sw = new StringWriter();  
        wfApp.Extensions.Add(sw);  
  
        wfApp.Completed = delegate(WorkflowApplicationCompletedEventArgs e)  
        {  
            if (e.CompletionState == ActivityInstanceState.Faulted)  
            {  
                UpdateStatus(string.Format("Workflow Terminated. Exception: {0}\r\n{1}",  
                    e.TerminationException.GetType().FullName,  
                    e.TerminationException.Message));  
            }  
            else if (e.CompletionState == ActivityInstanceState.Canceled)  
            {  
                UpdateStatus("Workflow Canceled.");  
            }  
            else  
            {  
                int Turns = Convert.ToInt32(e.Outputs["Turns"]);  
                UpdateStatus(string.Format("Congratulations, you guessed the number in {0} turns.", Turns));  
            }  
            GameOver();  
        };  
  
        wfApp.Aborted = delegate(WorkflowApplicationAbortedEventArgs e)  
        {  
            UpdateStatus(string.Format("Workflow Aborted. Exception: {0}\r\n{1}",  
                    e.Reason.GetType().FullName,  
                    e.Reason.Message));  
        };  
  
        wfApp.OnUnhandledException = delegate(WorkflowApplicationUnhandledExceptionEventArgs e)  
        {  
            UpdateStatus(string.Format("Unhandled Exception: {0}\r\n{1}",  
                    e.UnhandledException.GetType().FullName,  
                    e.UnhandledException.Message));  
            GameOver();  
            return UnhandledExceptionAction.Terminate;  
        };  
  
        wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)  
        {  
            // Send the current WriteLine outputs to the status window.  
            var writers = e.GetInstanceExtensions<StringWriter>();  
            foreach (var writer in writers)  
            {  
                UpdateStatus(writer.ToString());  
            }  
            return PersistableIdleAction.Unload;  
        };  
    }  
    ```  
  
###  <a name="BKMK_WorkflowVersionMap"></a> <span data-ttu-id="094d5-277">Başlangıç ve birden çok iş akışı türlerini sürdürme etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="094d5-277">To enable starting and resuming multiple workflow types</span></span>  
 <span data-ttu-id="094d5-278">Bir iş akışı örneği sürdürmek için ana iş akışı tanımı sağlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="094d5-278">In order to resume a workflow instance, the host has to provide the workflow definition.</span></span> <span data-ttu-id="094d5-279">Bu öğreticide üç iş akışı türü vardır ve bu tür birden çok sürümünü sonraki öğretici adımlarını sunar.</span><span class="sxs-lookup"><span data-stu-id="094d5-279">In this tutorial there are three workflow types, and subsequent tutorial steps introduce multiple versions of these types.</span></span> <span data-ttu-id="094d5-280">`WorkflowIdentity` tanımlama bilgilerini kalıcı iş akışı örneği ile ilişkilendirmek bir ana bilgisayar uygulaması için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="094d5-280">`WorkflowIdentity` provides a way for a host application to associate identifying information with a persisted workflow instance.</span></span> <span data-ttu-id="094d5-281">Bu bölümdeki adımları kalıcı iş akışı örneği iş akışı kimlikten karşılık gelen iş akışı tanımı için eşleme ile yardımcı olmak için yardımcı program sınıfı oluşturmak nasıl ekleyebileceğiniz gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="094d5-281">The steps in this section demonstrate how to create a utility class to assist with mapping the workflow identity from a persisted workflow instance to the corresponding workflow definition.</span></span> <span data-ttu-id="094d5-282">Hakkında daha fazla bilgi için `WorkflowIdentity` ve sürüm oluşturma, bkz: [Workflowıdentity kullanma ve sürüm oluşturma](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="094d5-282">For more information about `WorkflowIdentity` and versioning, see [Using WorkflowIdentity and Versioning](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md).</span></span>  
  
1.  <span data-ttu-id="094d5-283">Sağ **NumberGuessWorkflowHost** içinde **Çözüm Gezgini** ve **Ekle**, **sınıfı**.</span><span class="sxs-lookup"><span data-stu-id="094d5-283">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **Class**.</span></span> <span data-ttu-id="094d5-284">Tür `WorkflowVersionMap` içine **adı** kutusuna ve tıklatın **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="094d5-284">Type `WorkflowVersionMap` into the **Name** box and click **Add**.</span></span>  
  
2.  <span data-ttu-id="094d5-285">Aşağıdaki `using` veya `Imports` deyimini dosyanın diğer üst `using` veya `Imports` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="094d5-285">Add the following `using` or `Imports` statements at the top of the file with the other `using` or `Imports` statements.</span></span>  
  
    ```vb  
    Imports NumberGuessWorkflowActivities  
    Imports System.Activities  
    ```  
  
    ```csharp  
    using NumberGuessWorkflowActivities;  
    using System.Activities;  
    ```  
  
3.  <span data-ttu-id="094d5-286">Değiştirin `WorkflowVersionMap` sınıf bildiriminin aşağıdaki bildirimi.</span><span class="sxs-lookup"><span data-stu-id="094d5-286">Replace the `WorkflowVersionMap` class declaration with the following declaration.</span></span>  
  
    ```vb  
    Public Module WorkflowVersionMap  
        Dim map As Dictionary(Of WorkflowIdentity, Activity)  
  
        'Current version identities.  
        Public StateMachineNumberGuessIdentity As WorkflowIdentity  
        Public FlowchartNumberGuessIdentity As WorkflowIdentity  
        Public SequentialNumberGuessIdentity As WorkflowIdentity  
  
        Sub New()  
            map = New Dictionary(Of WorkflowIdentity, Activity)  
  
            'Add the current workflow version identities.  
            StateMachineNumberGuessIdentity = New WorkflowIdentity With  
            {  
                .Name = "StateMachineNumberGuessWorkflow",  
                .Version = New Version(1, 0, 0, 0)  
            }  
  
            FlowchartNumberGuessIdentity = New WorkflowIdentity With  
            {  
                .Name = "FlowchartNumberGuessWorkflow",  
                .Version = New Version(1, 0, 0, 0)  
            }  
  
            SequentialNumberGuessIdentity = New WorkflowIdentity With  
            {  
                .Name = "SequentialNumberGuessWorkflow",  
                .Version = New Version(1, 0, 0, 0)  
            }  
  
            map.Add(StateMachineNumberGuessIdentity, New StateMachineNumberGuessWorkflow())  
            map.Add(FlowchartNumberGuessIdentity, New FlowchartNumberGuessWorkflow())  
            map.Add(SequentialNumberGuessIdentity, New SequentialNumberGuessWorkflow())  
        End Sub  
  
        Public Function GetWorkflowDefinition(identity As WorkflowIdentity) As Activity  
            Return map(identity)  
        End Function  
  
        Public Function GetIdentityDescription(identity As WorkflowIdentity) As String  
            Return identity.ToString()  
        End Function  
    End Module  
    ```  
  
    ```csharp  
    public static class WorkflowVersionMap  
    {  
        static Dictionary<WorkflowIdentity, Activity> map;  
  
        // Current version identities.  
        static public WorkflowIdentity StateMachineNumberGuessIdentity;  
        static public WorkflowIdentity FlowchartNumberGuessIdentity;  
        static public WorkflowIdentity SequentialNumberGuessIdentity;  
  
        static WorkflowVersionMap()  
        {  
            map = new Dictionary<WorkflowIdentity, Activity>();  
  
            // Add the current workflow version identities.  
            StateMachineNumberGuessIdentity = new WorkflowIdentity  
            {  
                Name = "StateMachineNumberGuessWorkflow",  
                Version = new Version(1, 0, 0, 0)  
            };  
  
            FlowchartNumberGuessIdentity = new WorkflowIdentity  
            {  
                Name = "FlowchartNumberGuessWorkflow",  
                Version = new Version(1, 0, 0, 0)  
            };  
  
            SequentialNumberGuessIdentity = new WorkflowIdentity  
            {  
                Name = "SequentialNumberGuessWorkflow",  
                Version = new Version(1, 0, 0, 0)  
            };  
  
            map.Add(StateMachineNumberGuessIdentity, new StateMachineNumberGuessWorkflow());  
            map.Add(FlowchartNumberGuessIdentity, new FlowchartNumberGuessWorkflow());  
            map.Add(SequentialNumberGuessIdentity, new SequentialNumberGuessWorkflow());  
        }  
  
        public static Activity GetWorkflowDefinition(WorkflowIdentity identity)  
        {  
            return map[identity];  
        }  
  
        public static string GetIdentityDescription(WorkflowIdentity identity)  
        {          
            return identity.ToString();  
       }  
    }  
    ```  
  
     <span data-ttu-id="094d5-287">`WorkflowVersionMap` Bu öğreticide üç iş akışı tanımları eşleyen üç iş akışı kimlikleri içeriyor ve iş akışları başlatıldığında ve devam aşağıdaki bölümlerde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="094d5-287">`WorkflowVersionMap` contains three workflow identities that map to the three workflow definitions from this tutorial and is used in the following sections when workflows are started and resumed.</span></span>  
  
###  <a name="BKMK_StartWorkflow"></a> <span data-ttu-id="094d5-288">Yeni bir iş akışını başlatmak için</span><span class="sxs-lookup"><span data-stu-id="094d5-288">To start a new workflow</span></span>  
  
1.  <span data-ttu-id="094d5-289">Ekleme bir `Click` işleyicisi `NewGame`.</span><span class="sxs-lookup"><span data-stu-id="094d5-289">Add a `Click` handler for `NewGame`.</span></span> <span data-ttu-id="094d5-290">Bu işleyiciyi eklemek için geçiş **Tasarım görünümü** form ve çift `NewGame`.</span><span class="sxs-lookup"><span data-stu-id="094d5-290">To add the handler, switch to **Design View** for the form, and double-click `NewGame`.</span></span> <span data-ttu-id="094d5-291">A `NewGame_Click` işleyicisi eklenir ve görünüm formu için kod görünümüne geçer.</span><span class="sxs-lookup"><span data-stu-id="094d5-291">A `NewGame_Click` handler is added and the view switches to code view for the form.</span></span> <span data-ttu-id="094d5-292">Kullanıcı bu düğmeyi tıkladığında, yeni bir iş akışı başlatılır.</span><span class="sxs-lookup"><span data-stu-id="094d5-292">Whenever the user clicks this button a new workflow is started.</span></span>  
  
    ```vb  
    Private Sub NewGame_Click(sender As Object, e As EventArgs) Handles NewGame.Click  
  
    End Sub  
    ```  
  
    ```csharp  
    private void NewGame_Click(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
2.  <span data-ttu-id="094d5-293">Tıklama işleyicisi için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="094d5-293">Add the following code to the click handler.</span></span> <span data-ttu-id="094d5-294">Bu kod, giriş bağımsız değişken bağımsız değişken adına göre anahtarlanır iş akışı için bir sözlük oluşturur.</span><span class="sxs-lookup"><span data-stu-id="094d5-294">This code creates a dictionary of input arguments for the workflow, keyed by argument name.</span></span> <span data-ttu-id="094d5-295">Bu sözlük aralığı birleşik giriş kutusundan alınan rastgele oluşturulmuş bir sayıya aralığını içeren bir girdiye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="094d5-295">This dictionary has one entry that contains the range of the randomly generated number retrieved from the range combo box.</span></span>  
  
    ```vb  
    Dim inputs As New Dictionary(Of String, Object)()  
    inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem))  
    ```  
  
    ```csharp  
    var inputs = new Dictionary<string, object>();  
    inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem));  
    ```  
  
3.  <span data-ttu-id="094d5-296">Ardından, iş akışını başlatan aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="094d5-296">Next, add the following code that starts the workflow.</span></span> <span data-ttu-id="094d5-297">`WorkflowIdentity` Ve seçili iş akışı türü için karşılık gelen iş akışı tanımı kullanılarak alınır `WorkflowVersionMap` yardımcı sınıfı.</span><span class="sxs-lookup"><span data-stu-id="094d5-297">The `WorkflowIdentity` and workflow definition corresponding to the type of workflow selected are retrieved using the `WorkflowVersionMap` helper class.</span></span> <span data-ttu-id="094d5-298">Ardından, yeni bir `WorkflowApplication` örneği iş akışı tanımı kullanılarak oluşturulan `WorkflowIdentity`ve giriş bağımsız değişkeni sözlüğü.</span><span class="sxs-lookup"><span data-stu-id="094d5-298">Next, a new `WorkflowApplication` instance is created using the workflow definition, `WorkflowIdentity`, and dictionary of input arguments.</span></span>  
  
    ```vb  
    Dim identity As WorkflowIdentity = Nothing  
    Select Case WorkflowType.SelectedItem.ToString()  
        Case "SequentialNumberGuessWorkflow"  
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity  
  
        Case "StateMachineNumberGuessWorkflow"  
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity  
  
        Case "FlowchartNumberGuessWorkflow"  
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity  
    End Select  
  
    Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(identity)  
  
    Dim wfApp = New WorkflowApplication(wf, inputs, identity)  
    ```  
  
    ```csharp  
    WorkflowIdentity identity = null;  
    switch (WorkflowType.SelectedItem.ToString())  
    {  
        case "SequentialNumberGuessWorkflow":  
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity;  
            break;  
  
        case "StateMachineNumberGuessWorkflow":  
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity;  
            break;  
  
        case "FlowchartNumberGuessWorkflow":  
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity;  
            break;  
    };  
  
    Activity wf = WorkflowVersionMap.GetWorkflowDefinition(identity);  
  
    WorkflowApplication wfApp = new WorkflowApplication(wf, inputs, identity);  
    ```  
  
4.  <span data-ttu-id="094d5-299">Ardından, iş akışı iş akışı listesine ekler ve form üzerinde iş akışının sürüm bilgilerini görüntüler aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="094d5-299">Next, add the following code which adds the workflow to the workflow list and displays the workflow's version information on the form.</span></span>  
  
    ```vb  
    'Add the workflow to the list and display the version information.  
    WorkflowStarting = True  
    InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id)  
    WorkflowVersion.Text = identity.ToString()  
    WorkflowStarting = False  
    ```  
  
    ```csharp  
    // Add the workflow to the list and display the version information.  
    WorkflowStarting = true;  
    InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id);  
    WorkflowVersion.Text = identity.ToString();  
    WorkflowStarting = false;  
    ```  
  
5.  <span data-ttu-id="094d5-300">Çağrı `ConfigureWorkflowApplication` Bu örnek depo, uzantıları ve iş akışı yaşam döngüsü işleyicileri yapılandırmak için `WorkflowApplication` örneği.</span><span class="sxs-lookup"><span data-stu-id="094d5-300">Call `ConfigureWorkflowApplication` to configure the instance store, extensions, and workflow lifecycle handlers for this `WorkflowApplication` instance.</span></span>  
  
    ```vb  
    'Configure the instance store, extensions, and   
    'workflow lifecycle handlers.  
    ConfigureWorkflowApplication(wfApp)  
    ```  
  
    ```csharp  
    // Configure the instance store, extensions, and   
    // workflow lifecycle handlers.  
    ConfigureWorkflowApplication(wfApp);  
    ```  
  
6.  <span data-ttu-id="094d5-301">Son olarak, arama `Run`.</span><span class="sxs-lookup"><span data-stu-id="094d5-301">Finally, call `Run`.</span></span>  
  
    ```vb  
    'Start the workflow.  
    wfApp.Run()  
    ```  
  
    ```  
    // Start the workflow.  
    wfApp.Run();  
    ```  
  
     <span data-ttu-id="094d5-302">Aşağıdaki örnek, tamamlanan, `NewGame_Click` işleyici.</span><span class="sxs-lookup"><span data-stu-id="094d5-302">The following example is the completed `NewGame_Click` handler.</span></span>  
  
    ```vb  
    Private Sub NewGame_Click(sender As Object, e As EventArgs) Handles NewGame.Click  
        'Start a new workflow.  
        Dim inputs As New Dictionary(Of String, Object)()  
        inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem))  
  
        Dim identity As WorkflowIdentity = Nothing  
        Select Case WorkflowType.SelectedItem.ToString()  
            Case "SequentialNumberGuessWorkflow"  
                identity = WorkflowVersionMap.SequentialNumberGuessIdentity  
  
            Case "StateMachineNumberGuessWorkflow"  
                identity = WorkflowVersionMap.StateMachineNumberGuessIdentity  
  
            Case "FlowchartNumberGuessWorkflow"  
                identity = WorkflowVersionMap.FlowchartNumberGuessIdentity  
        End Select  
  
        Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(identity)  
  
        Dim wfApp = New WorkflowApplication(wf, inputs, identity)  
  
        'Add the workflow to the list and display the version information.  
        WorkflowStarting = True  
        InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id)  
        WorkflowVersion.Text = identity.ToString()  
        WorkflowStarting = False  
  
        'Configure the instance store, extensions, and   
        'workflow lifecycle handlers.  
        ConfigureWorkflowApplication(wfApp)  
  
        'Start the workflow.  
        wfApp.Run()  
    End Sub  
    ```  
  
    ```csharp  
    private void NewGame_Click(object sender, EventArgs e)  
    {  
        var inputs = new Dictionary<string, object>();  
        inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem));  
  
        WorkflowIdentity identity = null;  
        switch (WorkflowType.SelectedItem.ToString())  
        {  
            case "SequentialNumberGuessWorkflow":  
                identity = WorkflowVersionMap.SequentialNumberGuessIdentity;  
                break;  
  
            case "StateMachineNumberGuessWorkflow":  
                identity = WorkflowVersionMap.StateMachineNumberGuessIdentity;  
                break;  
  
            case "FlowchartNumberGuessWorkflow":  
                identity = WorkflowVersionMap.FlowchartNumberGuessIdentity;  
                break;  
        };  
  
        Activity wf = WorkflowVersionMap.GetWorkflowDefinition(identity);  
  
        WorkflowApplication wfApp = new WorkflowApplication(wf, inputs, identity);  
  
        // Add the workflow to the list and display the version information.  
        WorkflowStarting = true;  
        InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id);  
        WorkflowVersion.Text = identity.ToString();  
        WorkflowStarting = false;  
  
        // Configure the instance store, extensions, and   
        // workflow lifecycle handlers.  
        ConfigureWorkflowApplication(wfApp);  
  
        // Start the workflow.  
        wfApp.Run();  
    }  
    ```  
  
###  <a name="BKMK_ResumeWorkflow"></a> <span data-ttu-id="094d5-303">Bir iş akışını sürdürmek için</span><span class="sxs-lookup"><span data-stu-id="094d5-303">To resume a workflow</span></span>  
  
1.  <span data-ttu-id="094d5-304">Ekleme bir `Click` işleyicisi `EnterGuess`.</span><span class="sxs-lookup"><span data-stu-id="094d5-304">Add a `Click` handler for `EnterGuess`.</span></span> <span data-ttu-id="094d5-305">Bu işleyiciyi eklemek için geçiş **Tasarım görünümü** form ve çift `EnterGuess`.</span><span class="sxs-lookup"><span data-stu-id="094d5-305">To add the handler, switch to **Design View** for the form, and double-click `EnterGuess`.</span></span> <span data-ttu-id="094d5-306">Bir iş akışı kullanıcı bu düğmeyi tıkladığında sürdürülür.</span><span class="sxs-lookup"><span data-stu-id="094d5-306">Whenever the user clicks this button a workflow is resumed.</span></span>  
  
    ```vb  
    Private Sub EnterGuess_Click(sender As Object, e As EventArgs) Handles EnterGuess.Click  
  
    End Sub  
    ```  
  
    ```csharp  
    private void EnterGuess_Click(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
2.  <span data-ttu-id="094d5-307">Bir iş akışı iş akışı listesinde seçili olduğunu ve kullanıcının tahmin geçerli olduğundan emin olmak için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="094d5-307">Add the following code to ensure that a workflow is selected in the workflow list, and that the user's guess is valid.</span></span>  
  
    ```vb  
    If WorkflowInstanceId = Guid.Empty Then  
        MessageBox.Show("Please select a workflow.")  
        Return  
    End If  
  
    Dim userGuess As Integer  
    If Not Int32.TryParse(Guess.Text, userGuess) Then  
        MessageBox.Show("Please enter an integer.")  
        Guess.SelectAll()  
        Guess.Focus()  
        Return  
    End If  
    ```  
  
    ```csharp  
    if (WorkflowInstanceId == Guid.Empty)  
    {  
        MessageBox.Show("Please select a workflow.");  
        return;  
    }  
  
    int guess;  
    if (!Int32.TryParse(Guess.Text, out guess))  
    {  
        MessageBox.Show("Please enter an integer.");  
        Guess.SelectAll();  
        Guess.Focus();  
        return;  
    }  
    ```  
  
3.  <span data-ttu-id="094d5-308">Ardından, almak `WorkflowApplicationInstance` kalıcı iş akışı örneği.</span><span class="sxs-lookup"><span data-stu-id="094d5-308">Next, retrieve the `WorkflowApplicationInstance` of the persisted workflow instance.</span></span> <span data-ttu-id="094d5-309">A `WorkflowApplicationInstance` henüz bir iş akışı tanımı ile ilişkilendirilmemiş bir kalıcı iş akışı örneğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="094d5-309">A `WorkflowApplicationInstance` represents a persisted workflow instance that has not yet been associated with a workflow definition.</span></span> <span data-ttu-id="094d5-310">`DefinitionIdentity` , `WorkflowApplicationInstance` İçeren `WorkflowIdentity` kalıcı iş akışı örneği.</span><span class="sxs-lookup"><span data-stu-id="094d5-310">The `DefinitionIdentity` of the `WorkflowApplicationInstance` contains the `WorkflowIdentity` of the persisted workflow instance.</span></span> <span data-ttu-id="094d5-311">Bu öğreticide `WorkflowVersionMap` eşlemek için kullanılan yardımcı program sınıfı `WorkflowIdentity` doğru iş akışı tanımı için.</span><span class="sxs-lookup"><span data-stu-id="094d5-311">In this tutorial, the `WorkflowVersionMap` utility class is used to map the `WorkflowIdentity` to the correct workflow definition.</span></span> <span data-ttu-id="094d5-312">İş akışı tanımı alındıktan sonra bir `WorkflowApplication` , doğru iş akışı tanımı kullanılarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="094d5-312">Once the workflow definition is retrieved, a `WorkflowApplication` is created, using the correct workflow definition.</span></span>  
  
    ```vb  
    Dim instance As WorkflowApplicationInstance = _  
        WorkflowApplication.GetInstance(WorkflowInstanceId, store)  
  
    'Use the persisted WorkflowIdentity to retrieve the correct workflow  
    'definition from the dictionary.  
    Dim wf As Activity = _  
        WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity)  
  
    'Associate the WorkflowApplication with the correct definition  
    Dim wfApp As WorkflowApplication = _  
        New WorkflowApplication(wf, instance.DefinitionIdentity)  
    ```  
  
    ```csharp  
    WorkflowApplicationInstance instance =  
        WorkflowApplication.GetInstance(WorkflowInstanceId, store);  
  
    // Use the persisted WorkflowIdentity to retrieve the correct workflow  
    // definition from the dictionary.  
    Activity wf =  
        WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity);  
  
    // Associate the WorkflowApplication with the correct definition  
    WorkflowApplication wfApp =  
        new WorkflowApplication(wf, instance.DefinitionIdentity);  
    ```  
  
4.  <span data-ttu-id="094d5-313">Bir kez `WorkflowApplication` olan oluşturulan örnek deposu, iş akışı yaşam döngüsü işleyicileri ve uzantıları çağırarak yapılandırın `ConfigureWorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="094d5-313">Once the `WorkflowApplication` is created, configure the instance store, workflow lifecycle handlers, and extensions by calling `ConfigureWorkflowApplication`.</span></span> <span data-ttu-id="094d5-314">Bu adımları her seferinde yeni bir yapılmalıdır `WorkflowApplication` oluşturulur, ve iş akışı örneği içine yüklenmeden önce bunlar yapılmalıdır `WorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="094d5-314">These steps must be done every time a new `WorkflowApplication` is created, and they must be done before the workflow instance is loaded into the `WorkflowApplication`.</span></span> <span data-ttu-id="094d5-315">İş akışı yüklendikten sonra kullanıcının tahmin ile sürdürülür.</span><span class="sxs-lookup"><span data-stu-id="094d5-315">After the workflow is loaded, it is resumed with the user's guess.</span></span>  
  
    ```vb  
    'Configure the extensions and lifecycle handlers.  
    'Do this before the instance is loaded. Once the instance is  
    'loaded it is too late to add extensions.  
    ConfigureWorkflowApplication(wfApp)  
  
    'Load the workflow.  
    wfApp.Load(instance)  
  
    'Resume the workflow.  
    wfApp.ResumeBookmark("EnterGuess", userGuess)  
    ```  
  
    ```csharp  
    // Configure the extensions and lifecycle handlers.  
    // Do this before the instance is loaded. Once the instance is  
    // loaded it is too late to add extensions.  
    ConfigureWorkflowApplication(wfApp);  
  
    // Load the workflow.  
    wfApp.Load(instance);  
  
    // Resume the workflow.  
    wfApp.ResumeBookmark("EnterGuess", guess);  
    ```  
  
5.  <span data-ttu-id="094d5-316">Son olarak, tahmin metin kutusunun işaretini kaldırın ve formun başka bir tahmin kabul etmek için hazırlayın.</span><span class="sxs-lookup"><span data-stu-id="094d5-316">Finally, clear the guess textbox and prepare the form to accept another guess.</span></span>  
  
    ```vb  
    'Clear the Guess textbox.  
    Guess.Clear()  
    Guess.Focus()  
    ```  
  
    ```csharp  
    // Clear the Guess textbox.  
    Guess.Clear();  
    Guess.Focus();  
    ```  
  
     <span data-ttu-id="094d5-317">Aşağıdaki örnek, tamamlanan, `EnterGuess_Click` işleyici.</span><span class="sxs-lookup"><span data-stu-id="094d5-317">The following example is the completed `EnterGuess_Click` handler.</span></span>  
  
    ```vb  
    Private Sub EnterGuess_Click(sender As Object, e As EventArgs) Handles EnterGuess.Click  
        If WorkflowInstanceId = Guid.Empty Then  
            MessageBox.Show("Please select a workflow.")  
            Return  
        End If  
  
        Dim userGuess As Integer  
        If Not Int32.TryParse(Guess.Text, userGuess) Then  
            MessageBox.Show("Please enter an integer.")  
            Guess.SelectAll()  
            Guess.Focus()  
            Return  
        End If  
  
        Dim instance As WorkflowApplicationInstance = _  
            WorkflowApplication.GetInstance(WorkflowInstanceId, store)  
  
        'Use the persisted WorkflowIdentity to retrieve the correct workflow  
        'definition from the dictionary.  
        Dim wf As Activity = _  
            WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity)  
  
        'Associate the WorkflowApplication with the correct definition  
        Dim wfApp As WorkflowApplication = _  
            New WorkflowApplication(wf, instance.DefinitionIdentity)  
  
        'Configure the extensions and lifecycle handlers.  
        'Do this before the instance is loaded. Once the instance is  
        'loaded it is too late to add extensions.  
        ConfigureWorkflowApplication(wfApp)  
  
        'Load the workflow.  
        wfApp.Load(instance)  
  
        'Resume the workflow.  
        wfApp.ResumeBookmark("EnterGuess", userGuess)  
  
        'Clear the Guess textbox.  
        Guess.Clear()  
        Guess.Focus()  
    End Sub  
    ```  
  
    ```csharp  
    private void EnterGuess_Click(object sender, EventArgs e)  
    {  
        if (WorkflowInstanceId == Guid.Empty)  
        {  
            MessageBox.Show("Please select a workflow.");  
            return;  
        }  
  
        int guess;  
        if (!Int32.TryParse(Guess.Text, out guess))  
        {  
            MessageBox.Show("Please enter an integer.");  
            Guess.SelectAll();  
            Guess.Focus();  
            return;  
        }  
  
        WorkflowApplicationInstance instance =  
            WorkflowApplication.GetInstance(WorkflowInstanceId, store);  
  
        // Use the persisted WorkflowIdentity to retrieve the correct workflow  
        // definition from the dictionary.  
        Activity wf =  
            WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity);  
  
        // Associate the WorkflowApplication with the correct definition  
        WorkflowApplication wfApp =  
            new WorkflowApplication(wf, instance.DefinitionIdentity);  
  
        // Configure the extensions and lifecycle handlers.  
        // Do this before the instance is loaded. Once the instance is  
        // loaded it is too late to add extensions.  
        ConfigureWorkflowApplication(wfApp);  
  
        // Load the workflow.  
        wfApp.Load(instance);  
  
        // Resume the workflow.  
        wfApp.ResumeBookmark("EnterGuess", guess);  
  
        // Clear the Guess textbox.  
        Guess.Clear();  
        Guess.Focus();  
    }  
    ```  
  
###  <a name="BKMK_TerminateWorkflow"></a> <span data-ttu-id="094d5-318">Bir iş akışı sonlandırılmak üzere</span><span class="sxs-lookup"><span data-stu-id="094d5-318">To terminate a workflow</span></span>  
  
1.  <span data-ttu-id="094d5-319">Ekleme bir `Click` işleyicisi `QuitGame`.</span><span class="sxs-lookup"><span data-stu-id="094d5-319">Add a `Click` handler for `QuitGame`.</span></span> <span data-ttu-id="094d5-320">Bu işleyiciyi eklemek için geçiş **Tasarım görünümü** form ve çift `QuitGame`.</span><span class="sxs-lookup"><span data-stu-id="094d5-320">To add the handler, switch to **Design View** for the form, and double-click `QuitGame`.</span></span> <span data-ttu-id="094d5-321">Seçili durumdaki iş akışı kullanıcı bu düğmeyi tıkladığında sonlandırılır.</span><span class="sxs-lookup"><span data-stu-id="094d5-321">Whenever the user clicks this button the currently selected workflow is terminated.</span></span>  
  
    ```vb  
    Private Sub QuitGame_Click(sender As Object, e As EventArgs) Handles QuitGame.Click  
  
    End Sub  
    ```  
  
    ```csharp  
    private void QuitGame_Click(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
2.  <span data-ttu-id="094d5-322">Aşağıdaki kodu ekleyin `QuitGame_Click` işleyici.</span><span class="sxs-lookup"><span data-stu-id="094d5-322">Add the following code to the `QuitGame_Click` handler.</span></span> <span data-ttu-id="094d5-323">Bu kod, bir iş akışı iş akışı listesinde seçili olduğundan emin olmak için ilk denetler.</span><span class="sxs-lookup"><span data-stu-id="094d5-323">This code first checks to ensure that a workflow is selected in the workflow list.</span></span> <span data-ttu-id="094d5-324">Kalıcı örneğine yüklendikten sonra bir `WorkflowApplicationInstance`, kullandığı `DefinitionIdentity` doğru iş akışı tanımı ve ardından başlatır belirlemek için `WorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="094d5-324">Then it loads the persisted instance into a `WorkflowApplicationInstance`, uses the `DefinitionIdentity` to determine the correct workflow definition, and then initializes the `WorkflowApplication`.</span></span> <span data-ttu-id="094d5-325">Sonraki iş akışı yaşam döngüsü işleyicileri ve uzantıları çağrısı ile yapılandırılan `ConfigureWorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="094d5-325">Next the extensions and workflow lifecycle handlers are configured with a call to `ConfigureWorkflowApplication`.</span></span> <span data-ttu-id="094d5-326">Bir kez `WorkflowApplication` olan yapılandırılmış, ancak yüklendikten ve ardından `Terminate` çağrılır.</span><span class="sxs-lookup"><span data-stu-id="094d5-326">Once the `WorkflowApplication` is configured, it is loaded, and then `Terminate` is called.</span></span>  
  
    ```vb  
    If WorkflowInstanceId = Guid.Empty Then  
        MessageBox.Show("Please select a workflow.")  
        Return  
    End If  
  
    Dim instance As WorkflowApplicationInstance = _  
        WorkflowApplication.GetInstance(WorkflowInstanceId, store)  
  
    'Use the persisted WorkflowIdentity to retrieve the correct workflow  
    'definition from the dictionary.  
    Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity)  
  
    'Associate the WorkflowApplication with the correct definition.  
    Dim wfApp As WorkflowApplication = _  
        New WorkflowApplication(wf, instance.DefinitionIdentity)  
  
    'Configure the extensions and lifecycle handlers.  
    ConfigureWorkflowApplication(wfApp)  
  
    'Load the workflow.  
    wfApp.Load(instance)  
  
    'Terminate the workflow.  
    wfApp.Terminate("User resigns.")  
    ```  
  
    ```csharp  
    if (WorkflowInstanceId == Guid.Empty)  
    {  
        MessageBox.Show("Please select a workflow.");  
        return;  
    }  
  
    WorkflowApplicationInstance instance =  
        WorkflowApplication.GetInstance(WorkflowInstanceId, store);  
  
    // Use the persisted WorkflowIdentity to retrieve the correct workflow  
    // definition from the dictionary.  
    Activity wf = WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity);  
  
    // Associate the WorkflowApplication with the correct definition  
    WorkflowApplication wfApp =  
        new WorkflowApplication(wf, instance.DefinitionIdentity);  
  
    // Configure the extensions and lifecycle handlers  
    ConfigureWorkflowApplication(wfApp);  
  
    // Load the workflow.  
    wfApp.Load(instance);  
  
    // Terminate the workflow.  
    wfApp.Terminate("User resigns.");  
    ```  
  
###  <a name="BKMK_BuildAndRun"></a> <span data-ttu-id="094d5-327">Derleme ve uygulamayı çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="094d5-327">To build and run the application</span></span>  
  
1.  <span data-ttu-id="094d5-328">Çift **Program.cs** (veya **Module1.vb**) içinde **Çözüm Gezgini** seçerek kodu görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="094d5-328">Double-click **Program.cs** (or **Module1.vb**) in **Solution Explorer** to display the code.</span></span>  
  
2.  <span data-ttu-id="094d5-329">Aşağıdaki `using` (veya `Imports`) deyimini dosyanın diğer üst `using` (veya `Imports`) ifadeleri.</span><span class="sxs-lookup"><span data-stu-id="094d5-329">Add the following `using` (or `Imports`) statement at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Windows.Forms  
    ```  
  
    ```csharp  
    using System.Windows.Forms;  
    ```  
  
3.  <span data-ttu-id="094d5-330">Kaldırın veya koddan barındıran mevcut iş akışı açıklama [nasıl yapılır: bir iş akışı çalıştırma](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md), aşağıdaki kod ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="094d5-330">Remove or comment out the existing workflow hosting code from [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md), and replace it with the following code.</span></span>  
  
    ```vb  
    Sub Main()  
        Application.EnableVisualStyles()  
        Application.Run(New WorkflowHostForm())  
    End Sub  
    ```  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        Application.EnableVisualStyles();  
        Application.Run(new WorkflowHostForm());  
    }  
    ```  
  
4.  <span data-ttu-id="094d5-331">Sağ **NumberGuessWorkflowHost** içinde **Çözüm Gezgini** ve **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="094d5-331">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Properties**.</span></span> <span data-ttu-id="094d5-332">İçinde **uygulama** sekmesinde, belirtin **Windows uygulama** için **çıkış türü**.</span><span class="sxs-lookup"><span data-stu-id="094d5-332">In the **Application** tab, specify **Windows Application** for the **Output type**.</span></span> <span data-ttu-id="094d5-333">Bu adım isteğe bağlıdır, ancak bunu takip edilmemesi durumunda konsol penceresinde ek olarak form görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="094d5-333">This step is optional, but if it is not followed the console window is displayed in addition to the form.</span></span>  
  
5.  <span data-ttu-id="094d5-334">Uygulamayı oluşturmak için Ctrl + Shift + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="094d5-334">Press Ctrl+Shift+B to build the application.</span></span>  
  
6.  <span data-ttu-id="094d5-335">Emin **NumberGuessWorkflowHost** başlangıç uygulaması ayarlayın ve uygulamayı başlatmak için Ctrl + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="094d5-335">Ensure that **NumberGuessWorkflowHost** is set as the startup application, and press Ctrl+F5 to start the application.</span></span>  
  
7.  <span data-ttu-id="094d5-336">Tahmin eden oyun ve başlangıç ve iş akışı türü için bir aralık seçmek **yeni oyun**.</span><span class="sxs-lookup"><span data-stu-id="094d5-336">Select a range for the guessing game and the type of workflow to start, and click **New Game**.</span></span> <span data-ttu-id="094d5-337">İçinde bir tahmin girin **tahmin** kutusuna ve tıklatın **Git** , tahmin göndermek için.</span><span class="sxs-lookup"><span data-stu-id="094d5-337">Enter a guess in the **Guess** box and click **Go** to submit your guess.</span></span> <span data-ttu-id="094d5-338">Unutmayın çıktısı `WriteLine` etkinlikleri formda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="094d5-338">Note that the output from the `WriteLine` activities is displayed on the form.</span></span>  
  
8.  <span data-ttu-id="094d5-339">Farklı iş akışı türü ve numarası aralıkları kullanarak çeşitli iş akışlarını başlatmak, bazı tahminler girin ve gelen seçerek iş akışları arasında geçiş **iş akışı örnek kimliğini** listesi.</span><span class="sxs-lookup"><span data-stu-id="094d5-339">Start several workflows using different workflow types and number ranges, enter some guesses, and switch between the workflows by selecting from the **Workflow Instance Id** list.</span></span>  
  
     <span data-ttu-id="094d5-340">Yeni bir iş akışına geçiş yaptığınızda, önceki tahminler ve iş akışı ilerlemesini durumu penceresinde görüntülenmez olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="094d5-340">Note that when you switch to a new workflow, the previous guesses and progress of the workflow are not displayed in the status window.</span></span> <span data-ttu-id="094d5-341">Değil yakalanan olduğundan ve herhangi bir kaydedilmiş durum kullanılamıyor nedeni.</span><span class="sxs-lookup"><span data-stu-id="094d5-341">The reason the status is not available is because it is not captured and saved anywhere.</span></span> <span data-ttu-id="094d5-342">Öğreticinin sonraki adımda [nasıl yapılır: bir özel izleme Katılımcısı oluşturma](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md), bu bilgileri kaydeden bir özel izleme Katılımcısı oluşturma.</span><span class="sxs-lookup"><span data-stu-id="094d5-342">In the next step of the tutorial, [How to: Create a Custom Tracking Participant](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md), you create a custom tracking participant that saves this information.</span></span>
