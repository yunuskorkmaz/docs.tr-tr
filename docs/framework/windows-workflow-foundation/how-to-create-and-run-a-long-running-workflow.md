---
title: 'Nasıl yapılır: uzun süre çalışan bir Iş akışı oluşturma ve çalıştırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c0043c89-2192-43c9-986d-3ecec4dd8c9c
ms.openlocfilehash: e5083b3d12cecc395500ef13405effa7b7e51633
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73420625"
---
# <a name="how-to-create-and-run-a-long-running-workflow"></a><span data-ttu-id="20620-102">Nasıl yapılır: uzun süre çalışan bir Iş akışı oluşturma ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="20620-102">How to: Create and Run a Long Running Workflow</span></span>

<span data-ttu-id="20620-103">Windows Workflow Foundation (WF) öğesinin merkezi özelliklerinden biri, çalışma zamanının boşta iş akışlarını bir veritabanına kalıcı ve kaldırma olanağıdır.</span><span class="sxs-lookup"><span data-stu-id="20620-103">One of the central features of Windows Workflow Foundation (WF) is the runtime’s ability to persist and unload idle workflows to a database.</span></span> <span data-ttu-id="20620-104">[Nasıl yapılır: bir Iş akışını çalıştırma](how-to-run-a-workflow.md) , bir konsol uygulaması kullanarak iş akışı barındırma temelleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="20620-104">The steps in [How to: Run a Workflow](how-to-run-a-workflow.md) demonstrated the basics of workflow hosting using a console application.</span></span> <span data-ttu-id="20620-105">Örnek olarak başlangıç iş akışları, iş akışı yaşam döngüsü işleyicileri gösterildi ve yer işaretleri sürdürülüyor.</span><span class="sxs-lookup"><span data-stu-id="20620-105">Examples were shown of starting workflows, workflow lifecycle handlers, and resuming bookmarks.</span></span> <span data-ttu-id="20620-106">İş akışı kalıcılığını etkin bir şekilde göstermek için, birden çok iş akışı örneğini başlatmayı ve sürdürmeyi destekleyen daha karmaşık bir iş akışı konağı gerekir.</span><span class="sxs-lookup"><span data-stu-id="20620-106">In order to demonstrate workflow persistence effectively, a more complex workflow host is required that supports starting and resuming multiple workflow instances.</span></span> <span data-ttu-id="20620-107">Öğreticideki Bu adım, birden çok iş akışı örneğini başlatma ve sürdürmeyi destekleyen bir Windows form ana bilgisayar uygulamasının nasıl oluşturulduğunu, iş akışı kalıcılığını ve izleme ve sürüm oluşturma gibi gelişmiş özellikler için bir temel sağlar. sonraki öğretici adımlarında gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="20620-107">This step in the tutorial demonstrates how to create a Windows form host application that supports starting and resuming multiple workflow instances, workflow persistence, and provides a basis for the advanced features such as tracking and versioning that are demonstrated in subsequent tutorial steps.</span></span>

> [!NOTE]
> <span data-ttu-id="20620-108">Bu öğretici adımı ve sonraki adımlarda, [nasıl yapılır: Iş akışı oluşturma](how-to-create-a-workflow.md)ile üç iş akışı türü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="20620-108">This tutorial step and the subsequent steps use all three workflow types from [How to: Create a Workflow](how-to-create-a-workflow.md).</span></span> <span data-ttu-id="20620-109">Üç tür de tamamlamadıysanız, [Windows Workflow Foundation (WF45)-başlangıç öğreticisindeki](https://go.microsoft.com/fwlink/?LinkID=248976)adımların tamamlanmış bir sürümünü indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="20620-109">If you did not complete all three types you can download a completed version of the steps from [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>

> [!NOTE]
> <span data-ttu-id="20620-110">Tamamlanmış bir sürümü indirmek veya öğreticiye ilişkin bir video kılavuzunu görüntülemek için, bkz. [Windows Workflow Foundation (WF45)-Başlangıç Öğreticisi](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="20620-110">To download a completed version or view a video walkthrough of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>

## <a name="in-this-topic"></a><span data-ttu-id="20620-111">Bu konuda</span><span class="sxs-lookup"><span data-stu-id="20620-111">In this topic</span></span>

- [<span data-ttu-id="20620-112">Kalıcılık veritabanını oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="20620-112">To create the persistence database</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_CreatePersistenceDatabase)

- [<span data-ttu-id="20620-113">Başvuruyu Durableörnek oluşturma derlemelerine eklemek için</span><span class="sxs-lookup"><span data-stu-id="20620-113">To add the reference to the DurableInstancing assemblies</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_AddReference)

- [<span data-ttu-id="20620-114">İş akışı konak formunu oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="20620-114">To create the workflow host form</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_CreateForm)

- [<span data-ttu-id="20620-115">Formun özelliklerini ve yardımcı yöntemlerini eklemek için</span><span class="sxs-lookup"><span data-stu-id="20620-115">To add the properties and helper methods of the form</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_AddHelperMethods)

- [<span data-ttu-id="20620-116">Örnek deposunu, iş akışı yaşam döngüsü işleyicilerini ve uzantıları yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="20620-116">To configure the instance store, workflow lifecycle handlers, and extensions</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_ConfigureWorkflowApplication)

- [<span data-ttu-id="20620-117">Birden çok iş akışı türünü başlatmayı ve sürdürmeyi etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="20620-117">To enable starting and resuming multiple workflow types</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_WorkflowVersionMap)

- [<span data-ttu-id="20620-118">Yeni bir iş akışı başlatmak için</span><span class="sxs-lookup"><span data-stu-id="20620-118">To start a new workflow</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_StartWorkflow)

- [<span data-ttu-id="20620-119">Bir iş akışını sürdürmesini sağlamak için</span><span class="sxs-lookup"><span data-stu-id="20620-119">To resume a workflow</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_ResumeWorkflow)

- [<span data-ttu-id="20620-120">Bir iş akışını sonlandırmak için</span><span class="sxs-lookup"><span data-stu-id="20620-120">To terminate a workflow</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_TerminateWorkflow)

- [<span data-ttu-id="20620-121">Uygulamayı derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="20620-121">To build and run the application</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_BuildAndRun)

### <a name="BKMK_CreatePersistenceDatabase"></a><span data-ttu-id="20620-122">Kalıcılık veritabanını oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="20620-122">To create the persistence database</span></span>

1. <span data-ttu-id="20620-123">SQL Server Management Studio açın ve yerel sunucuya bağlanın, örneğin **.\Sqlexpress**.</span><span class="sxs-lookup"><span data-stu-id="20620-123">Open SQL Server Management Studio and connect to the local server, for example **.\SQLEXPRESS**.</span></span> <span data-ttu-id="20620-124">Yerel sunucuda **veritabanları** düğümüne sağ tıklayın ve **Yeni veritabanı**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="20620-124">Right-click the **Databases** node on the local server, and select **New Database**.</span></span> <span data-ttu-id="20620-125">Yeni veritabanını **WF45GettingStartedTutorial**olarak adlandırın, diğer tüm değerleri kabul edin ve **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="20620-125">Name the new database **WF45GettingStartedTutorial**, accept all other values, and select **OK**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="20620-126">Veritabanını oluşturmadan önce yerel sunucuda **Create Database** iznine sahip olduğunuzdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="20620-126">Ensure that you have **Create Database** permission on the local server before creating the database.</span></span>

2. <span data-ttu-id="20620-127">**Dosya** menüsünden **Aç**, **Dosya** ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="20620-127">Choose **Open**, **File** from the **File** menu.</span></span> <span data-ttu-id="20620-128">Şu klasöre gidin: `C:\Windows\Microsoft.NET\Framework\v4.0.30319\sql\en`</span><span class="sxs-lookup"><span data-stu-id="20620-128">Browse to the following folder: `C:\Windows\Microsoft.NET\Framework\v4.0.30319\sql\en`</span></span>

    <span data-ttu-id="20620-129">Aşağıdaki iki dosyayı seçin ve **Aç**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="20620-129">Select the following two files and click **Open**.</span></span>

    - <span data-ttu-id="20620-130">Sqlworkflowcestorelogic. SQL</span><span class="sxs-lookup"><span data-stu-id="20620-130">SqlWorkflowInstanceStoreLogic.sql</span></span>

    - <span data-ttu-id="20620-131">SqlWorkflowInstanceStoreSchema. SQL</span><span class="sxs-lookup"><span data-stu-id="20620-131">SqlWorkflowInstanceStoreSchema.sql</span></span>

3. <span data-ttu-id="20620-132">**Pencere** menüsünden **SqlWorkflowInstanceStoreSchema. SQL** öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="20620-132">Choose **SqlWorkflowInstanceStoreSchema.sql** from the **Window** menu.</span></span> <span data-ttu-id="20620-133">**Kullanılabilir veritabanları** açılan menüsünde **WF45GettingStartedTutorial** ' nin seçili olduğundan emin olun ve **sorgu** menüsünden **Yürüt** ' ü seçin.</span><span class="sxs-lookup"><span data-stu-id="20620-133">Ensure that **WF45GettingStartedTutorial** is selected in the **Available Databases** drop-down and choose **Execute** from the **Query** menu.</span></span>

4. <span data-ttu-id="20620-134">**Pencere** menüsünden **Sqlworkflowcestorelogic. SQL** öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="20620-134">Choose **SqlWorkflowInstanceStoreLogic.sql** from the **Window** menu.</span></span> <span data-ttu-id="20620-135">**Kullanılabilir veritabanları** açılan menüsünde **WF45GettingStartedTutorial** ' nin seçili olduğundan emin olun ve **sorgu** menüsünden **Yürüt** ' ü seçin.</span><span class="sxs-lookup"><span data-stu-id="20620-135">Ensure that **WF45GettingStartedTutorial** is selected in the **Available Databases** drop-down and choose **Execute** from the **Query** menu.</span></span>

    > [!WARNING]
    > <span data-ttu-id="20620-136">Önceki iki adımı doğru sırada gerçekleştirmek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="20620-136">It is important to perform the previous two steps in the correct order.</span></span> <span data-ttu-id="20620-137">Sorgular sıra dışında yürütülürse hatalar oluşur ve Kalıcılık veritabanı doğru şekilde yapılandırılmaz.</span><span class="sxs-lookup"><span data-stu-id="20620-137">If the queries are executed out of order, errors occur and the persistence database is not configured correctly.</span></span>

### <a name="BKMK_AddReference"></a><span data-ttu-id="20620-138">Başvuruyu Durableörnek oluşturma derlemelerine eklemek için</span><span class="sxs-lookup"><span data-stu-id="20620-138">To add the reference to the DurableInstancing assemblies</span></span>

1. <span data-ttu-id="20620-139">**Çözüm Gezgini** Için **Numberguessworkflowwhost** öğesine sağ tıklayın ve **Başvuru Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="20620-139">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and select **Add Reference**.</span></span>

2. <span data-ttu-id="20620-140">**Başvuru Ekle** listesinden **derlemeler** ' i seçin ve `DurableInstancing` **arama derlemeler** kutusuna yazın.</span><span class="sxs-lookup"><span data-stu-id="20620-140">Select **Assemblies** from the **Add Reference** list, and type `DurableInstancing` into the **Search Assemblies** box.</span></span> <span data-ttu-id="20620-141">Bu, derlemelerin filtreleyeceğini ve istenen başvuruların seçimi daha kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="20620-141">This filters the assemblies and makes the desired references easier to select.</span></span>

3. <span data-ttu-id="20620-142">**Arama sonuçları** listesinden **System. Activities. durableörnekınlist** ve **System. Runtime. durableörnekno** ' ın yanındaki onay kutusunu işaretleyin ve **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="20620-142">Check the checkbox beside **System.Activities.DurableInstancing** and **System.Runtime.DurableInstancing** from the **Search Results** list, and click **OK**.</span></span>

### <a name="BKMK_CreateForm"></a><span data-ttu-id="20620-143">İş akışı konak formunu oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="20620-143">To create the workflow host form</span></span>

> [!NOTE]
> <span data-ttu-id="20620-144">Bu yordamdaki adımlarda, formun el ile nasıl ekleneceği ve yapılandırılacağı açıklanır.</span><span class="sxs-lookup"><span data-stu-id="20620-144">The steps in this procedure describe how to add and configure the form manually.</span></span> <span data-ttu-id="20620-145">İsterseniz, öğreticinin çözüm dosyalarını indirebilir ve tamamlanmış formu projeye ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="20620-145">If desired, you can download the solution files for the tutorial and add the completed form to the project.</span></span> <span data-ttu-id="20620-146">Öğretici dosyalarını indirmek için, bkz. [Windows Workflow Foundation (WF45)-Başlangıç Öğreticisi](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="20620-146">To download the tutorial files, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span> <span data-ttu-id="20620-147">Dosyalar indirildikten sonra **Numberguessworkflowwhost** öğesine sağ tıklayın ve **Başvuru Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="20620-147">Once the files are downloaded, right-click **NumberGuessWorkflowHost** and choose **Add Reference**.</span></span> <span data-ttu-id="20620-148">**System. Windows. Forms** ve **System. Drawing**için bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="20620-148">Add a reference to **System.Windows.Forms** and **System.Drawing**.</span></span> <span data-ttu-id="20620-149">**Ekle**, **Yeni öğe** menüsünden Yeni bir form eklerseniz, ancak form içeri aktarılırken el ile eklenmesi gerekiyorsa, bu başvurular otomatik olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="20620-149">These references are added automatically if you add a new form from the **Add**, **New Item** menu, but must be added manually when importing a form.</span></span> <span data-ttu-id="20620-150">Başvurular eklendikten sonra, **Çözüm Gezgini** **Numberguessworkflowwhost** öğesine sağ tıklayın ve **Ekle**, **Varolan Öğe öğesini**seçin.</span><span class="sxs-lookup"><span data-stu-id="20620-150">Once the references are added, right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **Existing Item**.</span></span> <span data-ttu-id="20620-151">Proje dosyalarındaki `Form` klasörüne gidin, **WorkflowHostForm.cs** (veya **Workflowwhostform. vb**) öğesini seçin ve **Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="20620-151">Browse to the `Form` folder in the project files, select **WorkflowHostForm.cs** (or **WorkflowHostForm.vb**), and click **Add**.</span></span> <span data-ttu-id="20620-152">Formu içeri aktarmayı seçerseniz, [formun özellikler ve yardımcı yöntemleri eklemek için](how-to-create-and-run-a-long-running-workflow.md#BKMK_AddHelperMethods)sonraki bölüme atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="20620-152">If you choose to import the form, then you can skip down to the next section, [To add the properties and helper methods of the form](how-to-create-and-run-a-long-running-workflow.md#BKMK_AddHelperMethods).</span></span>

1. <span data-ttu-id="20620-153">**Çözüm Gezgini** Için **Numberguessworkflowwhost** öğesine sağ tıklayın ve **Ekle**, **Yeni öğe**seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="20620-153">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **New Item**.</span></span>

2. <span data-ttu-id="20620-154">**Yüklü** şablonlar listesinde, **Windows formu**' nu seçin, **ad** kutusuna `WorkflowHostForm` yazın ve **Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="20620-154">In the **Installed** templates list, choose **Windows Form**, type `WorkflowHostForm` in the **Name** box, and click **Add**.</span></span>

3. <span data-ttu-id="20620-155">Formda aşağıdaki özellikleri yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="20620-155">Configure the following properties on the form.</span></span>

    |<span data-ttu-id="20620-156">Özellik</span><span class="sxs-lookup"><span data-stu-id="20620-156">Property</span></span>|<span data-ttu-id="20620-157">Değer</span><span class="sxs-lookup"><span data-stu-id="20620-157">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="20620-158">FormBorderStyle</span><span class="sxs-lookup"><span data-stu-id="20620-158">FormBorderStyle</span></span>|<span data-ttu-id="20620-159">FixedSingle</span><span class="sxs-lookup"><span data-stu-id="20620-159">FixedSingle</span></span>|
    |<span data-ttu-id="20620-160">MaximizeBox</span><span class="sxs-lookup"><span data-stu-id="20620-160">MaximizeBox</span></span>|<span data-ttu-id="20620-161">False</span><span class="sxs-lookup"><span data-stu-id="20620-161">False</span></span>|
    |<span data-ttu-id="20620-162">Boyut</span><span class="sxs-lookup"><span data-stu-id="20620-162">Size</span></span>|<span data-ttu-id="20620-163">400, 420</span><span class="sxs-lookup"><span data-stu-id="20620-163">400, 420</span></span>|

4. <span data-ttu-id="20620-164">Aşağıdaki denetimleri, belirtilen sırada forma ekleyin ve özellikleri yönlendirildiği şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="20620-164">Add the following controls to the form in the order specified and configure the properties as directed.</span></span>

    |<span data-ttu-id="20620-165">Denetim</span><span class="sxs-lookup"><span data-stu-id="20620-165">Control</span></span>|<span data-ttu-id="20620-166">Özellik: değer</span><span class="sxs-lookup"><span data-stu-id="20620-166">Property: Value</span></span>|
    |-------------|---------------------|
    |<span data-ttu-id="20620-167">**Düğme**</span><span class="sxs-lookup"><span data-stu-id="20620-167">**Button**</span></span>|<span data-ttu-id="20620-168">Ad: NewGame</span><span class="sxs-lookup"><span data-stu-id="20620-168">Name: NewGame</span></span><br /><br /> <span data-ttu-id="20620-169">Konum: 13, 13</span><span class="sxs-lookup"><span data-stu-id="20620-169">Location: 13, 13</span></span><br /><br /> <span data-ttu-id="20620-170">Boyut: 75, 23</span><span class="sxs-lookup"><span data-stu-id="20620-170">Size: 75, 23</span></span><br /><br /> <span data-ttu-id="20620-171">Metin: yeni oyun</span><span class="sxs-lookup"><span data-stu-id="20620-171">Text: New Game</span></span>|
    |<span data-ttu-id="20620-172">**Etiket**</span><span class="sxs-lookup"><span data-stu-id="20620-172">**Label**</span></span>|<span data-ttu-id="20620-173">Konum: 94, 18</span><span class="sxs-lookup"><span data-stu-id="20620-173">Location: 94, 18</span></span><br /><br /> <span data-ttu-id="20620-174">Metin: 1 ile arasında bir sayı tahmin edin</span><span class="sxs-lookup"><span data-stu-id="20620-174">Text: Guess a number from 1 to</span></span>|
    |<span data-ttu-id="20620-175">**ComboBox**</span><span class="sxs-lookup"><span data-stu-id="20620-175">**ComboBox**</span></span>|<span data-ttu-id="20620-176">Ad: NumberRange</span><span class="sxs-lookup"><span data-stu-id="20620-176">Name: NumberRange</span></span><br /><br /> <span data-ttu-id="20620-177">DropDownStyle: DropDownList</span><span class="sxs-lookup"><span data-stu-id="20620-177">DropDownStyle: DropDownList</span></span><br /><br /> <span data-ttu-id="20620-178">Öğeler: 10, 100, 1000</span><span class="sxs-lookup"><span data-stu-id="20620-178">Items: 10, 100, 1000</span></span><br /><br /> <span data-ttu-id="20620-179">Konum: 228, 12</span><span class="sxs-lookup"><span data-stu-id="20620-179">Location: 228, 12</span></span><br /><br /> <span data-ttu-id="20620-180">Boyut: 143, 21</span><span class="sxs-lookup"><span data-stu-id="20620-180">Size: 143, 21</span></span>|
    |<span data-ttu-id="20620-181">**Etiket**</span><span class="sxs-lookup"><span data-stu-id="20620-181">**Label**</span></span>|<span data-ttu-id="20620-182">Konum: 13, 43</span><span class="sxs-lookup"><span data-stu-id="20620-182">Location: 13, 43</span></span><br /><br /> <span data-ttu-id="20620-183">Metin: Iş akışı türü</span><span class="sxs-lookup"><span data-stu-id="20620-183">Text: Workflow type</span></span>|
    |<span data-ttu-id="20620-184">**ComboBox**</span><span class="sxs-lookup"><span data-stu-id="20620-184">**ComboBox**</span></span>|<span data-ttu-id="20620-185">Ad: WorkflowType</span><span class="sxs-lookup"><span data-stu-id="20620-185">Name: WorkflowType</span></span><br /><br /> <span data-ttu-id="20620-186">DropDownStyle: DropDownList</span><span class="sxs-lookup"><span data-stu-id="20620-186">DropDownStyle: DropDownList</span></span><br /><br /> <span data-ttu-id="20620-187">Öğeler: StateMachineNumberGuessWorkflow, FlowchartNumberGuessWorkflow, SequentialNumberGuessWorkflow</span><span class="sxs-lookup"><span data-stu-id="20620-187">Items: StateMachineNumberGuessWorkflow, FlowchartNumberGuessWorkflow, SequentialNumberGuessWorkflow</span></span><br /><br /> <span data-ttu-id="20620-188">Konum: 94, 40</span><span class="sxs-lookup"><span data-stu-id="20620-188">Location: 94, 40</span></span><br /><br /> <span data-ttu-id="20620-189">Boyut: 277, 21</span><span class="sxs-lookup"><span data-stu-id="20620-189">Size: 277, 21</span></span>|
    |<span data-ttu-id="20620-190">**Etiket**</span><span class="sxs-lookup"><span data-stu-id="20620-190">**Label**</span></span>|<span data-ttu-id="20620-191">Ad: WorkflowVersion</span><span class="sxs-lookup"><span data-stu-id="20620-191">Name: WorkflowVersion</span></span><br /><br /> <span data-ttu-id="20620-192">Konum: 13, 362</span><span class="sxs-lookup"><span data-stu-id="20620-192">Location: 13, 362</span></span><br /><br /> <span data-ttu-id="20620-193">Metin: Iş akışı sürümü</span><span class="sxs-lookup"><span data-stu-id="20620-193">Text: Workflow version</span></span>|
    |<span data-ttu-id="20620-194">**GroupBox**</span><span class="sxs-lookup"><span data-stu-id="20620-194">**GroupBox**</span></span>|<span data-ttu-id="20620-195">Konum: 13, 67</span><span class="sxs-lookup"><span data-stu-id="20620-195">Location: 13, 67</span></span><br /><br /> <span data-ttu-id="20620-196">Boyut: 358, 287</span><span class="sxs-lookup"><span data-stu-id="20620-196">Size: 358, 287</span></span><br /><br /> <span data-ttu-id="20620-197">Metin: oyun</span><span class="sxs-lookup"><span data-stu-id="20620-197">Text: Game</span></span>|

    > [!NOTE]
    > <span data-ttu-id="20620-198">Aşağıdaki denetimleri eklerken GroupBox içine yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="20620-198">When adding the following controls, put them into the GroupBox.</span></span>

    |<span data-ttu-id="20620-199">Denetim</span><span class="sxs-lookup"><span data-stu-id="20620-199">Control</span></span>|<span data-ttu-id="20620-200">Özellik: değer</span><span class="sxs-lookup"><span data-stu-id="20620-200">Property: Value</span></span>|
    |-------------|---------------------|
    |<span data-ttu-id="20620-201">**Etiket**</span><span class="sxs-lookup"><span data-stu-id="20620-201">**Label**</span></span>|<span data-ttu-id="20620-202">Konum: 7, 20</span><span class="sxs-lookup"><span data-stu-id="20620-202">Location: 7, 20</span></span><br /><br /> <span data-ttu-id="20620-203">Metin: Iş akışı örneği kimliği</span><span class="sxs-lookup"><span data-stu-id="20620-203">Text: Workflow Instance Id</span></span>|
    |<span data-ttu-id="20620-204">**ComboBox**</span><span class="sxs-lookup"><span data-stu-id="20620-204">**ComboBox**</span></span>|<span data-ttu-id="20620-205">Ad: InstanceId</span><span class="sxs-lookup"><span data-stu-id="20620-205">Name: InstanceId</span></span><br /><br /> <span data-ttu-id="20620-206">DropDownStyle: DropDownList</span><span class="sxs-lookup"><span data-stu-id="20620-206">DropDownStyle: DropDownList</span></span><br /><br /> <span data-ttu-id="20620-207">Konum: 121, 17</span><span class="sxs-lookup"><span data-stu-id="20620-207">Location: 121, 17</span></span><br /><br /> <span data-ttu-id="20620-208">Boyut: 227, 21</span><span class="sxs-lookup"><span data-stu-id="20620-208">Size: 227, 21</span></span>|
    |<span data-ttu-id="20620-209">**Etiket**</span><span class="sxs-lookup"><span data-stu-id="20620-209">**Label**</span></span>|<span data-ttu-id="20620-210">Konum: 7, 47</span><span class="sxs-lookup"><span data-stu-id="20620-210">Location: 7, 47</span></span><br /><br /> <span data-ttu-id="20620-211">Metin: tahmin</span><span class="sxs-lookup"><span data-stu-id="20620-211">Text: Guess</span></span>|
    |<span data-ttu-id="20620-212">**TextBox**</span><span class="sxs-lookup"><span data-stu-id="20620-212">**TextBox**</span></span>|<span data-ttu-id="20620-213">Ad: tahmin</span><span class="sxs-lookup"><span data-stu-id="20620-213">Name: Guess</span></span><br /><br /> <span data-ttu-id="20620-214">Konum: 50, 44</span><span class="sxs-lookup"><span data-stu-id="20620-214">Location: 50, 44</span></span><br /><br /> <span data-ttu-id="20620-215">Boyut: 65, 20</span><span class="sxs-lookup"><span data-stu-id="20620-215">Size: 65, 20</span></span>|
    |<span data-ttu-id="20620-216">**Düğme**</span><span class="sxs-lookup"><span data-stu-id="20620-216">**Button**</span></span>|<span data-ttu-id="20620-217">Ad: Entertahmin</span><span class="sxs-lookup"><span data-stu-id="20620-217">Name: EnterGuess</span></span><br /><br /> <span data-ttu-id="20620-218">Konum: 121, 42</span><span class="sxs-lookup"><span data-stu-id="20620-218">Location: 121, 42</span></span><br /><br /> <span data-ttu-id="20620-219">Boyut: 75, 23</span><span class="sxs-lookup"><span data-stu-id="20620-219">Size: 75, 23</span></span><br /><br /> <span data-ttu-id="20620-220">Metin: tahmin girin</span><span class="sxs-lookup"><span data-stu-id="20620-220">Text: Enter Guess</span></span>|
    |<span data-ttu-id="20620-221">**Düğme**</span><span class="sxs-lookup"><span data-stu-id="20620-221">**Button**</span></span>|<span data-ttu-id="20620-222">Ad: QuitGame</span><span class="sxs-lookup"><span data-stu-id="20620-222">Name: QuitGame</span></span><br /><br /> <span data-ttu-id="20620-223">Konum: 274, 42</span><span class="sxs-lookup"><span data-stu-id="20620-223">Location: 274, 42</span></span><br /><br /> <span data-ttu-id="20620-224">Boyut: 75, 23</span><span class="sxs-lookup"><span data-stu-id="20620-224">Size: 75, 23</span></span><br /><br /> <span data-ttu-id="20620-225">Metin: çık</span><span class="sxs-lookup"><span data-stu-id="20620-225">Text: Quit</span></span>|
    |<span data-ttu-id="20620-226">**TextBox**</span><span class="sxs-lookup"><span data-stu-id="20620-226">**TextBox**</span></span>|<span data-ttu-id="20620-227">Ad: WorkflowStatus</span><span class="sxs-lookup"><span data-stu-id="20620-227">Name: WorkflowStatus</span></span><br /><br /> <span data-ttu-id="20620-228">Konum: 10, 73</span><span class="sxs-lookup"><span data-stu-id="20620-228">Location: 10, 73</span></span><br /><br /> <span data-ttu-id="20620-229">Çoklu satır: doğru</span><span class="sxs-lookup"><span data-stu-id="20620-229">Multiline: True</span></span><br /><br /> <span data-ttu-id="20620-230">ReadOnly: true</span><span class="sxs-lookup"><span data-stu-id="20620-230">ReadOnly: True</span></span><br /><br /> <span data-ttu-id="20620-231">Kaydırma çubukları: dikey</span><span class="sxs-lookup"><span data-stu-id="20620-231">ScrollBars: Vertical</span></span><br /><br /> <span data-ttu-id="20620-232">Boyut: 338, 208</span><span class="sxs-lookup"><span data-stu-id="20620-232">Size: 338, 208</span></span>|

5. <span data-ttu-id="20620-233">Formun **AcceptButton** özelliğini **entertahmin**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="20620-233">Set the **AcceptButton** property of the form to **EnterGuess**.</span></span>

 <span data-ttu-id="20620-234">Aşağıdaki örnekte tamamlanan form gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="20620-234">The following example illustrates the completed form.</span></span>

 ![Windows Workflow Foundation Iş akışı konak formunun ekran görüntüsü.](./media/how-to-create-and-run-a-long-running-workflow/windows-workflow-foundation-workflowhostform.png)

### <a name="BKMK_AddHelperMethods"></a><span data-ttu-id="20620-236">Formun özelliklerini ve yardımcı yöntemlerini eklemek için</span><span class="sxs-lookup"><span data-stu-id="20620-236">To add the properties and helper methods of the form</span></span>

<span data-ttu-id="20620-237">Bu bölümdeki adımlarda, form sınıfına, çalışma ve tahmin sayısı tahmin iş akışlarına devam ettirmek için formun Kullanıcı arabirimini yapılandıran Özellikler ve yardımcı yöntemler ekleme.</span><span class="sxs-lookup"><span data-stu-id="20620-237">The steps in this section add properties and helper methods to the form class that configure the UI of the form to support running and resuming number guess workflows.</span></span>

1. <span data-ttu-id="20620-238">**Çözüm Gezgini** ' de **Workflowwhostform** öğesine sağ tıklayın ve **kodu görüntüle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="20620-238">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>

2. <span data-ttu-id="20620-239">Aşağıdaki `using` (veya `Imports`) deyimlerini, diğer `using` (veya `Imports`) deyimleriyle dosyanın en üstüne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="20620-239">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>

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

3. <span data-ttu-id="20620-240">Aşağıdaki üye bildirimlerini **Workflowwhostform** sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="20620-240">Add the following member declarations to the **WorkflowHostForm** class.</span></span>

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
    > <span data-ttu-id="20620-241">Bağlantı dizeniz farklıysa, veritabanınıza başvurmak için `connectionString` güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="20620-241">If your connection string is different, update `connectionString` to refer to your database.</span></span>

4. <span data-ttu-id="20620-242">`WorkflowFormHost` sınıfına bir `WorkflowInstanceId` özelliği ekleyin.</span><span class="sxs-lookup"><span data-stu-id="20620-242">Add a `WorkflowInstanceId` property to the `WorkflowFormHost` class.</span></span>

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

    <span data-ttu-id="20620-243">`InstanceId` açılan kutusu, kalıcı iş akışı örneği kimliklerinin bir listesini görüntüler ve `WorkflowInstanceId` özelliği şu anda seçili olan iş akışını döndürür.</span><span class="sxs-lookup"><span data-stu-id="20620-243">The `InstanceId` combo box displays a list of persisted workflow instance ids, and the `WorkflowInstanceId` property returns the currently selected workflow.</span></span>

5. <span data-ttu-id="20620-244">Form `Load` olayı için bir işleyici ekleyin.</span><span class="sxs-lookup"><span data-stu-id="20620-244">Add a handler for the form `Load` event.</span></span> <span data-ttu-id="20620-245">İşleyiciyi eklemek için form için **Tasarım görünümüne** geçin, **Özellikler** penceresinin üst kısmındaki **Olaylar** simgesine tıklayın ve **Yükle**' ye çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="20620-245">To add the handler, switch to **Design View** for the form, click the **Events** icon at the top of the **Properties** window, and double-click **Load**.</span></span>

    ```vb
    Private Sub WorkflowHostForm_Load(sender As Object, e As EventArgs) Handles Me.Load

    End Sub
    ```

    ```csharp
    private void WorkflowHostForm_Load(object sender, EventArgs e)
    {

    }
    ```

6. <span data-ttu-id="20620-246">`WorkflowHostForm_Load`için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="20620-246">Add the following code to `WorkflowHostForm_Load`.</span></span>

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

    <span data-ttu-id="20620-247">Form yüklendiğinde, `SqlWorkflowInstanceStore` yapılandırılır, Aralık ve iş akışı türü Birleşik giriş kutuları varsayılan değerlere ayarlanır ve kalıcı iş akışı örnekleri `InstanceId` Birleşik giriş kutusuna eklenir.</span><span class="sxs-lookup"><span data-stu-id="20620-247">When the form loads, the `SqlWorkflowInstanceStore` is configured, the range and workflow type combo boxes are set to default values, and the persisted workflow instances are added to the `InstanceId` combo box.</span></span>

7. <span data-ttu-id="20620-248">`InstanceId`için `SelectedIndexChanged` işleyicisi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="20620-248">Add a `SelectedIndexChanged` handler for `InstanceId`.</span></span> <span data-ttu-id="20620-249">İşleyiciyi eklemek için form için **Tasarım görünümüne** geçiş yapın, `InstanceId` Birleşik giriş kutusunu seçin, **Özellikler** penceresinin üst kısmındaki **Olaylar** simgesine tıklayın ve **SelectedIndexChanged**öğesine çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="20620-249">To add the handler, switch to **Design View** for the form, select the `InstanceId` combo box, click the **Events** icon at the top of the **Properties** window, and double-click **SelectedIndexChanged**.</span></span>

    ```vb
    Private Sub InstanceId_SelectedIndexChanged(sender As Object, e As EventArgs) Handles InstanceId.SelectedIndexChanged

    End Sub
    ```

    ```csharp
    private void InstanceId_SelectedIndexChanged(object sender, EventArgs e)
    {

    }
    ```

8. <span data-ttu-id="20620-250">`InstanceId_SelectedIndexChanged`için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="20620-250">Add the following code to `InstanceId_SelectedIndexChanged`.</span></span> <span data-ttu-id="20620-251">Kullanıcı açılan kutuyu kullanarak bir iş akışı seçtiğinde, bu işleyici durum penceresini güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="20620-251">Whenever the user selects a workflow by using the combo box this handler updates the status window.</span></span>

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

9. <span data-ttu-id="20620-252">Aşağıdaki `ListPersistedWorkflows` yöntemini form sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="20620-252">Add the following `ListPersistedWorkflows` method to the form class.</span></span>

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

    <span data-ttu-id="20620-253">`ListPersistedWorkflows` kalıcı iş akışı örnekleri için örnek deposunu sorgular ve örnek kimliklerini `cboInstanceId` Birleşik giriş kutusuna ekler.</span><span class="sxs-lookup"><span data-stu-id="20620-253">`ListPersistedWorkflows` queries the instance store for persisted workflow instances, and adds the instance ids to the `cboInstanceId` combo box.</span></span>

10. <span data-ttu-id="20620-254">Aşağıdaki `UpdateStatus` yöntemini ve ilgili temsilciyi form sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="20620-254">Add the following `UpdateStatus` method and corresponding delegate to the form class.</span></span> <span data-ttu-id="20620-255">Bu yöntem, form üzerindeki durum penceresini Şu anda çalışan iş akışının durumuyla güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="20620-255">This method updates the status window on the form with the status of the currently running workflow.</span></span>

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

11. <span data-ttu-id="20620-256">Aşağıdaki `GameOver` yöntemini ve ilgili temsilciyi form sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="20620-256">Add the following `GameOver` method and corresponding delegate to the form class.</span></span> <span data-ttu-id="20620-257">Bir iş akışı tamamlandığında, bu yöntem, **InstanceId** Birleşik giriş kutusundan tamamlanan iş akışının örnek kimliğini kaldırarak form kullanıcı arabirimini güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="20620-257">When a workflow completes, this method updates the form UI by removing the instance id of the completed workflow from the **InstanceId** combo box.</span></span>

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

### <a name="BKMK_ConfigureWorkflowApplication"></a><span data-ttu-id="20620-258">Örnek deposunu, iş akışı yaşam döngüsü işleyicilerini ve uzantıları yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="20620-258">To configure the instance store, workflow lifecycle handlers, and extensions</span></span>

1. <span data-ttu-id="20620-259">Form sınıfına bir `ConfigureWorkflowApplication` yöntemi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="20620-259">Add a `ConfigureWorkflowApplication` method to the form class.</span></span>

    ```vb
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)

    End Sub
    ```

    ```csharp
    private void ConfigureWorkflowApplication(WorkflowApplication wfApp)
    {
    }
    ```

    <span data-ttu-id="20620-260">Bu yöntem `WorkflowApplication`yapılandırır, istenen uzantıları ekler ve iş akışı yaşam döngüsü olayları için işleyiciler ekler.</span><span class="sxs-lookup"><span data-stu-id="20620-260">This method configures the `WorkflowApplication`, adds the desired extensions, and adds handlers for the workflow lifecycle events.</span></span>

2. <span data-ttu-id="20620-261">`ConfigureWorkflowApplication`' de, `WorkflowApplication``SqlWorkflowInstanceStore` belirtin.</span><span class="sxs-lookup"><span data-stu-id="20620-261">In `ConfigureWorkflowApplication`, specify the `SqlWorkflowInstanceStore` for the `WorkflowApplication`.</span></span>

    ```vb
    'Configure the persistence store.
    wfApp.InstanceStore = store
    ```

    ```csharp
    // Configure the persistence store.
    wfApp.InstanceStore = store;
    ```

3. <span data-ttu-id="20620-262">Sonra, bir `StringWriter` örneği oluşturup `WorkflowApplication``Extensions` koleksiyonuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="20620-262">Next, create a `StringWriter` instance and add it to the `Extensions` collection of the `WorkflowApplication`.</span></span> <span data-ttu-id="20620-263">Uzantılara bir `StringWriter` eklendiğinde, tüm `WriteLine` etkinlik çıkışını yakalar.</span><span class="sxs-lookup"><span data-stu-id="20620-263">When a `StringWriter` is added to the extensions it captures all `WriteLine` activity output.</span></span> <span data-ttu-id="20620-264">İş akışı boşta kaldığında, `WriteLine` çıktısı `StringWriter` ayıklanıp formda görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="20620-264">When the workflow becomes idle, the `WriteLine` output can be extracted from the `StringWriter` and displayed on the form.</span></span>

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

4. <span data-ttu-id="20620-265">`Completed` olayı için aşağıdaki işleyiciyi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="20620-265">Add the following handler for the `Completed` event.</span></span> <span data-ttu-id="20620-266">Bir iş akışı başarıyla tamamlandığında, sayıyı tahmin etmek için yapılan dönüşün sayısı durum penceresine görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="20620-266">When a workflow successfully completes, the number of turns taken to guess the number is displayed to the status window.</span></span> <span data-ttu-id="20620-267">İş akışı sonlandığında, sonlandırmasına neden olan özel durum bilgileri görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="20620-267">If the workflow terminates, the exception information that caused the termination is displayed.</span></span> <span data-ttu-id="20620-268">İşleyicinin sonunda, tamamlanan iş akışını iş akışı listesinden kaldıran `GameOver` yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="20620-268">At the end of the handler the `GameOver` method is called, which removes the completed workflow from the workflow list.</span></span>

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
                UpdateStatus($"Congratulations, you guessed the number in {Turns} turns.")
            End If
            GameOver()
        End Sub
    ```

    ```csharp
    wfApp.Completed = delegate(WorkflowApplicationCompletedEventArgs e)
    {
        if (e.CompletionState == ActivityInstanceState.Faulted)
        {
            UpdateStatus($"Workflow Terminated. Exception: {e.TerminationException.GetType().FullName}\r\n{e.TerminationException.Message}");
        }
        else if (e.CompletionState == ActivityInstanceState.Canceled)
        {
            UpdateStatus("Workflow Canceled.");
        }
        else
        {
            int Turns = Convert.ToInt32(e.Outputs["Turns"]);
            UpdateStatus($"Congratulations, you guessed the number in {Turns} turns.");
        }
        GameOver();
    };
    ```

5. <span data-ttu-id="20620-269">Aşağıdaki `Aborted` ve `OnUnhandledException` işleyicileri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="20620-269">Add the following `Aborted` and `OnUnhandledException` handlers.</span></span> <span data-ttu-id="20620-270">`GameOver` yöntemi, bir iş akışı örneği iptal edildiğinde, Sonlanmadığı ve örneği daha sonra sürdürülmesi mümkün olduğu için `Aborted` işleyicisinden çağrılmaz.</span><span class="sxs-lookup"><span data-stu-id="20620-270">The `GameOver` method is not called from the `Aborted` handler because when a workflow instance is aborted, it does not terminate, and it is possible to resume the instance at a later time.</span></span>

    ```vb
    wfApp.Aborted = _
        Sub(e As WorkflowApplicationAbortedEventArgs)
            UpdateStatus($"Workflow Aborted. Exception: {0e.Reason.GetType().FullName}" & vbCrLf & $"{e.Reason.Message}")
        End Sub

    wfApp.OnUnhandledException = _
        Function(e As WorkflowApplicationUnhandledExceptionEventArgs)
            UpdateStatus($"Unhandled Exception: {e.UnhandledException.GetType().FullName}" & vbCrLf & $"{e.UnhandledException.Message}")
            GameOver()
            Return UnhandledExceptionAction.Terminate
        End Function
    ```

    ```csharp
    wfApp.Aborted = delegate(WorkflowApplicationAbortedEventArgs e)
    {
        UpdateStatus($"Workflow Aborted. Exception: {e.Reason.GetType().FullName}\r\n{e.Reason.Message}");
    };

    wfApp.OnUnhandledException = delegate(WorkflowApplicationUnhandledExceptionEventArgs e)
    {
        UpdateStatus($"Unhandled Exception: {e.UnhandledException.GetType().FullName}\r\n{e.UnhandledException.Message}");
        GameOver();
        return UnhandledExceptionAction.Terminate;
    };
    ```

6. <span data-ttu-id="20620-271">Aşağıdaki `PersistableIdle` işleyicisini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="20620-271">Add the following `PersistableIdle` handler.</span></span> <span data-ttu-id="20620-272">Bu işleyici, eklenen `StringWriter` uzantısını alır, `WriteLine` etkinliklerinden çıktıyı ayıklar ve durum penceresinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="20620-272">This handler retrieves the `StringWriter` extension that was added, extracts the output from the `WriteLine` activities, and displays it in the status window.</span></span>

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

    <span data-ttu-id="20620-273"><xref:System.Activities.PersistableIdleAction> numaralandırması üç değere sahiptir: <xref:System.Activities.PersistableIdleAction.None>, <xref:System.Activities.PersistableIdleAction.Persist>ve <xref:System.Activities.PersistableIdleAction.Unload>.</span><span class="sxs-lookup"><span data-stu-id="20620-273">The <xref:System.Activities.PersistableIdleAction> enumeration has three values: <xref:System.Activities.PersistableIdleAction.None>, <xref:System.Activities.PersistableIdleAction.Persist>, and <xref:System.Activities.PersistableIdleAction.Unload>.</span></span> <span data-ttu-id="20620-274"><xref:System.Activities.PersistableIdleAction.Persist> iş akışının devam etmesine neden olur, ancak iş akışının kaldırılmasına neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="20620-274"><xref:System.Activities.PersistableIdleAction.Persist> causes the workflow to persist but it does not cause the workflow to unload.</span></span> <span data-ttu-id="20620-275"><xref:System.Activities.PersistableIdleAction.Unload>, iş akışının kalıcı ve kaldırılmış olmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="20620-275"><xref:System.Activities.PersistableIdleAction.Unload> causes the workflow to persist and be unloaded.</span></span>

    <span data-ttu-id="20620-276">Aşağıdaki örnek, tamamlanmış `ConfigureWorkflowApplication` yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="20620-276">The following example is the completed `ConfigureWorkflowApplication` method.</span></span>

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
                    UpdateStatus($"Congratulations, you guessed the number in {Turns} turns.")
                End If
                GameOver()
            End Sub

        wfApp.Aborted = _
            Sub(e As WorkflowApplicationAbortedEventArgs)
                UpdateStatus($"Workflow Aborted. Exception: {e.Reason.GetType().FullName}" & vbCrLf & $"{e.Reason.Message}")
            End Sub

        wfApp.OnUnhandledException = _
            Function(e As WorkflowApplicationUnhandledExceptionEventArgs)
                UpdateStatus($"Unhandled Exception: {e.UnhandledException.GetType().FullName}" & vbCrLf & $"{e.UnhandledException.Message}")
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
                UpdateStatus($"Workflow Terminated. Exception: {e.TerminationException.GetType().FullName}\r\n{e.TerminationException.Message}");
            }
            else if (e.CompletionState == ActivityInstanceState.Canceled)
            {
                UpdateStatus("Workflow Canceled.");
            }
            else
            {
                int Turns = Convert.ToInt32(e.Outputs["Turns"]);
                UpdateStatus($"Congratulations, you guessed the number in {Turns} turns.");
            }
            GameOver();
        };

        wfApp.Aborted = delegate(WorkflowApplicationAbortedEventArgs e)
        {
            UpdateStatus($"Workflow Aborted. Exception: {e.Reason.GetType().FullName}\r\n{e.Reason.Message}");
        };

        wfApp.OnUnhandledException = delegate(WorkflowApplicationUnhandledExceptionEventArgs e)
        {
            UpdateStatus($"Unhandled Exception: {e.UnhandledException.GetType().FullName}\r\n{e.UnhandledException.Message}");
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

### <a name="BKMK_WorkflowVersionMap"></a><span data-ttu-id="20620-277">Birden çok iş akışı türünü başlatmayı ve sürdürmeyi etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="20620-277">To enable starting and resuming multiple workflow types</span></span>

<span data-ttu-id="20620-278">Bir iş akışı örneğinin sürdürülmesi için, konağın iş akışı tanımını sağlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="20620-278">In order to resume a workflow instance, the host has to provide the workflow definition.</span></span> <span data-ttu-id="20620-279">Bu öğreticide, üç iş akışı türü vardır ve sonraki öğretici adımları bu türlerin birden çok sürümünü ortaya çıkarabilir.</span><span class="sxs-lookup"><span data-stu-id="20620-279">In this tutorial there are three workflow types, and subsequent tutorial steps introduce multiple versions of these types.</span></span> <span data-ttu-id="20620-280">`WorkflowIdentity`, bir ana bilgisayar uygulamasının, tanımlayıcı bilgileri kalıcı bir iş akışı örneğiyle ilişkilendirmesi için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="20620-280">`WorkflowIdentity` provides a way for a host application to associate identifying information with a persisted workflow instance.</span></span> <span data-ttu-id="20620-281">Bu bölümdeki adımlarda, kalıcı bir iş akışı örneğinden ilgili iş akışı tanımına iş akışı kimliğini eşleştirmeye yardımcı olması için bir yardımcı program sınıfının nasıl oluşturulacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="20620-281">The steps in this section demonstrate how to create a utility class to assist with mapping the workflow identity from a persisted workflow instance to the corresponding workflow definition.</span></span> <span data-ttu-id="20620-282">`WorkflowIdentity` ve sürüm oluşturma hakkında daha fazla bilgi için bkz. [Workflowwıdentity ve sürüm oluşturmayı kullanma](using-workflowidentity-and-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="20620-282">For more information about `WorkflowIdentity` and versioning, see [Using WorkflowIdentity and Versioning](using-workflowidentity-and-versioning.md).</span></span>

1. <span data-ttu-id="20620-283">**Çözüm Gezgini** Için **Numberguessworkflowwhost** öğesine sağ tıklayın ve **Ekle**, **sınıf**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="20620-283">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **Class**.</span></span> <span data-ttu-id="20620-284">**Ad** kutusuna `WorkflowVersionMap` yazın ve **Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="20620-284">Type `WorkflowVersionMap` into the **Name** box and click **Add**.</span></span>

2. <span data-ttu-id="20620-285">Aşağıdaki `using` veya `Imports` deyimlerini, diğer `using` veya `Imports` deyimleriyle dosyanın en üstüne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="20620-285">Add the following `using` or `Imports` statements at the top of the file with the other `using` or `Imports` statements.</span></span>

    ```vb
    Imports NumberGuessWorkflowActivities
    Imports System.Activities
    ```

    ```csharp
    using NumberGuessWorkflowActivities;
    using System.Activities;
    ```

3. <span data-ttu-id="20620-286">`WorkflowVersionMap` sınıfı bildirimini aşağıdaki bildirimle değiştirin.</span><span class="sxs-lookup"><span data-stu-id="20620-286">Replace the `WorkflowVersionMap` class declaration with the following declaration.</span></span>

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

    <span data-ttu-id="20620-287">`WorkflowVersionMap`, bu öğreticideki üç iş akışı tanımına eşlenen üç iş akışı kimliği içerir ve iş akışları başlatıldığında ve devam ettirildiğinde aşağıdaki bölümlerde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="20620-287">`WorkflowVersionMap` contains three workflow identities that map to the three workflow definitions from this tutorial and is used in the following sections when workflows are started and resumed.</span></span>

### <a name="BKMK_StartWorkflow"></a><span data-ttu-id="20620-288">Yeni bir iş akışı başlatmak için</span><span class="sxs-lookup"><span data-stu-id="20620-288">To start a new workflow</span></span>

1. <span data-ttu-id="20620-289">`NewGame`için `Click` işleyicisi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="20620-289">Add a `Click` handler for `NewGame`.</span></span> <span data-ttu-id="20620-290">İşleyiciyi eklemek için form için **Tasarım görünümüne** geçin ve `NewGame`çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="20620-290">To add the handler, switch to **Design View** for the form, and double-click `NewGame`.</span></span> <span data-ttu-id="20620-291">`NewGame_Click` işleyicisi eklenir ve görünüm form için kod görünümüne geçer.</span><span class="sxs-lookup"><span data-stu-id="20620-291">A `NewGame_Click` handler is added and the view switches to code view for the form.</span></span> <span data-ttu-id="20620-292">Kullanıcı bu düğmeye her tıkladığında yeni bir iş akışı başlatılır.</span><span class="sxs-lookup"><span data-stu-id="20620-292">Whenever the user clicks this button a new workflow is started.</span></span>

    ```vb
    Private Sub NewGame_Click(sender As Object, e As EventArgs) Handles NewGame.Click

    End Sub
    ```

    ```csharp
    private void NewGame_Click(object sender, EventArgs e)
    {

    }
    ```

2. <span data-ttu-id="20620-293">Aşağıdaki kodu tıklama işleyicisine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="20620-293">Add the following code to the click handler.</span></span> <span data-ttu-id="20620-294">Bu kod, iş akışı için bağımsız değişken adına göre anahtarlı bir giriş bağımsız değişkenlerinin sözlüğünü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="20620-294">This code creates a dictionary of input arguments for the workflow, keyed by argument name.</span></span> <span data-ttu-id="20620-295">Bu sözlükte, Aralık Birleşik giriş kutusundan alınan rastgele oluşturulan sayı aralığını içeren bir giriş vardır.</span><span class="sxs-lookup"><span data-stu-id="20620-295">This dictionary has one entry that contains the range of the randomly generated number retrieved from the range combo box.</span></span>

    ```vb
    Dim inputs As New Dictionary(Of String, Object)()
    inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem))
    ```

    ```csharp
    var inputs = new Dictionary<string, object>();
    inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem));
    ```

3. <span data-ttu-id="20620-296">Sonra, iş akışını başlatan aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="20620-296">Next, add the following code that starts the workflow.</span></span> <span data-ttu-id="20620-297">Seçilen iş akışı türüne karşılık gelen `WorkflowIdentity` ve iş akışı tanımı `WorkflowVersionMap` yardımcı sınıfı kullanılarak alınır.</span><span class="sxs-lookup"><span data-stu-id="20620-297">The `WorkflowIdentity` and workflow definition corresponding to the type of workflow selected are retrieved using the `WorkflowVersionMap` helper class.</span></span> <span data-ttu-id="20620-298">Ardından, giriş bağımsız değişkenlerinin iş akışı tanımı, `WorkflowIdentity`ve sözlüğü kullanılarak yeni bir `WorkflowApplication` örneği oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="20620-298">Next, a new `WorkflowApplication` instance is created using the workflow definition, `WorkflowIdentity`, and dictionary of input arguments.</span></span>

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

4. <span data-ttu-id="20620-299">Sonra, iş akışını iş akışı listesine ekleyen aşağıdaki kodu ekleyin ve iş akışının sürüm bilgilerini formda görüntüler.</span><span class="sxs-lookup"><span data-stu-id="20620-299">Next, add the following code which adds the workflow to the workflow list and displays the workflow's version information on the form.</span></span>

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

5. <span data-ttu-id="20620-300">Bu `WorkflowApplication` örneği için örnek deposu, Uzantılar ve iş akışı yaşam döngüsü işleyicilerini yapılandırmak üzere `ConfigureWorkflowApplication` çağırın.</span><span class="sxs-lookup"><span data-stu-id="20620-300">Call `ConfigureWorkflowApplication` to configure the instance store, extensions, and workflow lifecycle handlers for this `WorkflowApplication` instance.</span></span>

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

6. <span data-ttu-id="20620-301">Son olarak, `Run`çağırın.</span><span class="sxs-lookup"><span data-stu-id="20620-301">Finally, call `Run`.</span></span>

    ```vb
    'Start the workflow.
    wfApp.Run()
    ```

    ```csharp
    // Start the workflow.
    wfApp.Run();
    ```

     <span data-ttu-id="20620-302">Aşağıdaki örnek, tamamlanmış `NewGame_Click` işleyicisidir.</span><span class="sxs-lookup"><span data-stu-id="20620-302">The following example is the completed `NewGame_Click` handler.</span></span>

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

### <a name="BKMK_ResumeWorkflow"></a><span data-ttu-id="20620-303">Bir iş akışını sürdürmesini sağlamak için</span><span class="sxs-lookup"><span data-stu-id="20620-303">To resume a workflow</span></span>

1. <span data-ttu-id="20620-304">`EnterGuess`için `Click` işleyicisi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="20620-304">Add a `Click` handler for `EnterGuess`.</span></span> <span data-ttu-id="20620-305">İşleyiciyi eklemek için form için **Tasarım görünümüne** geçin ve `EnterGuess`çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="20620-305">To add the handler, switch to **Design View** for the form, and double-click `EnterGuess`.</span></span> <span data-ttu-id="20620-306">Kullanıcı bu düğmeye tıkladığında bir iş akışı sürdürülür.</span><span class="sxs-lookup"><span data-stu-id="20620-306">Whenever the user clicks this button a workflow is resumed.</span></span>

    ```vb
    Private Sub EnterGuess_Click(sender As Object, e As EventArgs) Handles EnterGuess.Click

    End Sub
    ```

    ```csharp
    private void EnterGuess_Click(object sender, EventArgs e)
    {

    }
    ```

2. <span data-ttu-id="20620-307">İş akışı listesinde bir iş akışının seçildiğinden ve kullanıcının tahminin geçerli olduğundan emin olmak için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="20620-307">Add the following code to ensure that a workflow is selected in the workflow list, and that the user's guess is valid.</span></span>

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

3. <span data-ttu-id="20620-308">Sonra, kalıcı iş akışı örneğinin `WorkflowApplicationInstance` alın.</span><span class="sxs-lookup"><span data-stu-id="20620-308">Next, retrieve the `WorkflowApplicationInstance` of the persisted workflow instance.</span></span> <span data-ttu-id="20620-309">`WorkflowApplicationInstance`, henüz bir iş akışı tanımıyla ilişkilendirilmemiş kalıcı bir iş akışı örneğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="20620-309">A `WorkflowApplicationInstance` represents a persisted workflow instance that has not yet been associated with a workflow definition.</span></span> <span data-ttu-id="20620-310">`WorkflowApplicationInstance` `DefinitionIdentity`, kalıcı iş akışı örneğinin `WorkflowIdentity` içerir.</span><span class="sxs-lookup"><span data-stu-id="20620-310">The `DefinitionIdentity` of the `WorkflowApplicationInstance` contains the `WorkflowIdentity` of the persisted workflow instance.</span></span> <span data-ttu-id="20620-311">Bu öğreticide, `WorkflowVersionMap` yardımcı sınıfı, `WorkflowIdentity` doğru iş akışı tanımına eşlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="20620-311">In this tutorial, the `WorkflowVersionMap` utility class is used to map the `WorkflowIdentity` to the correct workflow definition.</span></span> <span data-ttu-id="20620-312">İş akışı tanımı alındıktan sonra, doğru iş akışı tanımı kullanılarak bir `WorkflowApplication` oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="20620-312">Once the workflow definition is retrieved, a `WorkflowApplication` is created, using the correct workflow definition.</span></span>

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

4. <span data-ttu-id="20620-313">`WorkflowApplication` oluşturulduktan sonra, `ConfigureWorkflowApplication`çağırarak örnek depoyu, iş akışı yaşam döngüsü işleyicilerini ve Uzantıları yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="20620-313">Once the `WorkflowApplication` is created, configure the instance store, workflow lifecycle handlers, and extensions by calling `ConfigureWorkflowApplication`.</span></span> <span data-ttu-id="20620-314">Bu adımların her yeni `WorkflowApplication` oluşturulduğunda yapılması ve iş akışı örneği `WorkflowApplication`yüklenmeden önce yapılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="20620-314">These steps must be done every time a new `WorkflowApplication` is created, and they must be done before the workflow instance is loaded into the `WorkflowApplication`.</span></span> <span data-ttu-id="20620-315">İş akışı yüklendikten sonra kullanıcının tahminiyle devam edilir.</span><span class="sxs-lookup"><span data-stu-id="20620-315">After the workflow is loaded, it is resumed with the user's guess.</span></span>

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

5. <span data-ttu-id="20620-316">Son olarak, tahmin metin kutusunu temizleyip formu başka bir tahmin kabul edecek şekilde hazırlayın.</span><span class="sxs-lookup"><span data-stu-id="20620-316">Finally, clear the guess textbox and prepare the form to accept another guess.</span></span>

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

    <span data-ttu-id="20620-317">Aşağıdaki örnek, tamamlanmış `EnterGuess_Click` işleyicisidir.</span><span class="sxs-lookup"><span data-stu-id="20620-317">The following example is the completed `EnterGuess_Click` handler.</span></span>

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

### <a name="BKMK_TerminateWorkflow"></a><span data-ttu-id="20620-318">Bir iş akışını sonlandırmak için</span><span class="sxs-lookup"><span data-stu-id="20620-318">To terminate a workflow</span></span>

1. <span data-ttu-id="20620-319">`QuitGame`için `Click` işleyicisi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="20620-319">Add a `Click` handler for `QuitGame`.</span></span> <span data-ttu-id="20620-320">İşleyiciyi eklemek için form için **Tasarım görünümüne** geçin ve `QuitGame`çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="20620-320">To add the handler, switch to **Design View** for the form, and double-click `QuitGame`.</span></span> <span data-ttu-id="20620-321">Kullanıcı bu düğmeye tıkladığında Şu anda seçili olan iş akışı sonlandırılır.</span><span class="sxs-lookup"><span data-stu-id="20620-321">Whenever the user clicks this button the currently selected workflow is terminated.</span></span>

    ```vb
    Private Sub QuitGame_Click(sender As Object, e As EventArgs) Handles QuitGame.Click

    End Sub
    ```

    ```csharp
    private void QuitGame_Click(object sender, EventArgs e)
    {

    }
    ```

2. <span data-ttu-id="20620-322">`QuitGame_Click` işleyicisine aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="20620-322">Add the following code to the `QuitGame_Click` handler.</span></span> <span data-ttu-id="20620-323">Bu kod ilk olarak iş akışı listesinde bir iş akışının seçili olduğundan emin olmak için kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="20620-323">This code first checks to ensure that a workflow is selected in the workflow list.</span></span> <span data-ttu-id="20620-324">Ardından, kalıcı örneği bir `WorkflowApplicationInstance`yükler, doğru iş akışı tanımını anlamak için `DefinitionIdentity` kullanır ve ardından `WorkflowApplication`başlatır.</span><span class="sxs-lookup"><span data-stu-id="20620-324">Then it loads the persisted instance into a `WorkflowApplicationInstance`, uses the `DefinitionIdentity` to determine the correct workflow definition, and then initializes the `WorkflowApplication`.</span></span> <span data-ttu-id="20620-325">Daha sonra Uzantılar ve iş akışı yaşam döngüsü işleyicileri bir `ConfigureWorkflowApplication`çağrısıyla yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="20620-325">Next the extensions and workflow lifecycle handlers are configured with a call to `ConfigureWorkflowApplication`.</span></span> <span data-ttu-id="20620-326">`WorkflowApplication` yapılandırıldıktan sonra, yüklenir ve ardından `Terminate` çağırılır.</span><span class="sxs-lookup"><span data-stu-id="20620-326">Once the `WorkflowApplication` is configured, it is loaded, and then `Terminate` is called.</span></span>

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

### <a name="BKMK_BuildAndRun"></a><span data-ttu-id="20620-327">Uygulamayı derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="20620-327">To build and run the application</span></span>

1. <span data-ttu-id="20620-328">Kodu göstermek için **Çözüm Gezgini** içindeki **program.cs** (veya **Module1. vb**) öğesine çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="20620-328">Double-click **Program.cs** (or **Module1.vb**) in **Solution Explorer** to display the code.</span></span>

2. <span data-ttu-id="20620-329">Aşağıdaki `using` (veya `Imports`) deyimini, diğer `using` (veya `Imports`) deyimleriyle dosyanın en üstüne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="20620-329">Add the following `using` (or `Imports`) statement at the top of the file with the other `using` (or `Imports`) statements.</span></span>

    ```vb
    Imports System.Windows.Forms
    ```

    ```csharp
    using System.Windows.Forms;
    ```

3. <span data-ttu-id="20620-330">[Nasıl yapılır: Iş akışı çalıştırma](how-to-run-a-workflow.md)ve aşağıdaki kodla değiştirme gibi mevcut iş akışı barındırma kodunu kaldırın</span><span class="sxs-lookup"><span data-stu-id="20620-330">Remove or comment out the existing workflow hosting code from [How to: Run a Workflow](how-to-run-a-workflow.md), and replace it with the following code.</span></span>

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

4. <span data-ttu-id="20620-331">**Çözüm Gezgini** Için **Numberguessworkflowwhost** öğesine sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="20620-331">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Properties**.</span></span> <span data-ttu-id="20620-332">**Uygulama** sekmesinde, **Çıkış türü**için **Windows uygulaması** ' nı belirtin.</span><span class="sxs-lookup"><span data-stu-id="20620-332">In the **Application** tab, specify **Windows Application** for the **Output type**.</span></span> <span data-ttu-id="20620-333">Bu adım isteğe bağlıdır, ancak bu değer izlenmezse, forma ek olarak konsol penceresi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="20620-333">This step is optional, but if it is not followed the console window is displayed in addition to the form.</span></span>

5. <span data-ttu-id="20620-334">Uygulamayı derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="20620-334">Press Ctrl+Shift+B to build the application.</span></span>

6. <span data-ttu-id="20620-335">**Numberguessworkflowwhost** ' nin başlangıç uygulaması olarak ayarlandığından emin olun ve uygulamayı başlatmak için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="20620-335">Ensure that **NumberGuessWorkflowHost** is set as the startup application, and press Ctrl+F5 to start the application.</span></span>

7. <span data-ttu-id="20620-336">Tahmin etme oyunu ve başlatılacak iş akışı türü için bir Aralık seçin ve **yeni oyun**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="20620-336">Select a range for the guessing game and the type of workflow to start, and click **New Game**.</span></span> <span data-ttu-id="20620-337">**Tahmin kutusuna bir** tahmin girin ve tahmininizi göndermek için **Git** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="20620-337">Enter a guess in the **Guess** box and click **Go** to submit your guess.</span></span> <span data-ttu-id="20620-338">`WriteLine` etkinliklerinden gelen çıktının formda görüntülendiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="20620-338">Note that the output from the `WriteLine` activities is displayed on the form.</span></span>

8. <span data-ttu-id="20620-339">Farklı iş akışı türleri ve sayı aralıkları kullanarak birkaç iş akışı başlatın, bazı tahminler girin ve **Iş akışı örneği kimliği** listesinden seçim yaparak iş akışları arasında geçiş yapın.</span><span class="sxs-lookup"><span data-stu-id="20620-339">Start several workflows using different workflow types and number ranges, enter some guesses, and switch between the workflows by selecting from the **Workflow Instance Id** list.</span></span>

    <span data-ttu-id="20620-340">Yeni bir iş akışına geçtiğinizde, iş akışının önceki tahminlerini ve ilerleme durumu durum penceresinde görüntülenmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="20620-340">Note that when you switch to a new workflow, the previous guesses and progress of the workflow are not displayed in the status window.</span></span> <span data-ttu-id="20620-341">Durumun, yakalanmadığı ve her yerde kaydedilmediği için durum kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="20620-341">The reason the status is not available is because it is not captured and saved anywhere.</span></span> <span data-ttu-id="20620-342">Öğreticinin bir sonraki adımında, [nasıl yapılır: özel bir Izleme katılımcısı oluşturma](how-to-create-a-custom-tracking-participant.md), bu bilgileri kaydeden özel bir izleme katılımcısı oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="20620-342">In the next step of the tutorial, [How to: Create a Custom Tracking Participant](how-to-create-a-custom-tracking-participant.md), you create a custom tracking participant that saves this information.</span></span>
