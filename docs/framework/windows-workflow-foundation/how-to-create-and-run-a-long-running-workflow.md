---
title: Uzun süre çalışan bir iş akışı oluşturma ve çalıştırma
description: Bu makalede, birden çok iş akışı örneğini ve iş akışı kalıcılığını başlatmayı ve sürdürmeyi destekleyen bir Windows Forms ana bilgisayar uygulamasının nasıl oluşturulacağı gösterilmektedir.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c0043c89-2192-43c9-986d-3ecec4dd8c9c
ms.openlocfilehash: 701788ac5575ad671afd56db3af4bd247efac8b1
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98188471"
---
# <a name="how-to-create-and-run-a-long-running-workflow"></a><span data-ttu-id="f6906-103">Uzun süre çalışan bir iş akışı oluşturma ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="f6906-103">How to create and run a long-running workflow</span></span>

<span data-ttu-id="f6906-104">Windows Workflow Foundation (WF) öğesinin merkezi özelliklerinden biri, çalışma zamanının boşta iş akışlarını bir veritabanına kalıcı ve kaldırma olanağıdır.</span><span class="sxs-lookup"><span data-stu-id="f6906-104">One of the central features of Windows Workflow Foundation (WF) is the runtime’s ability to persist and unload idle workflows to a database.</span></span> <span data-ttu-id="f6906-105">[Nasıl yapılır: bir Iş akışını çalıştırma](how-to-run-a-workflow.md) , bir konsol uygulaması kullanarak iş akışı barındırma temelleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f6906-105">The steps in [How to: Run a Workflow](how-to-run-a-workflow.md) demonstrated the basics of workflow hosting using a console application.</span></span> <span data-ttu-id="f6906-106">Örnek olarak başlangıç iş akışları, iş akışı yaşam döngüsü işleyicileri gösterildi ve yer işaretleri sürdürülüyor.</span><span class="sxs-lookup"><span data-stu-id="f6906-106">Examples were shown of starting workflows, workflow lifecycle handlers, and resuming bookmarks.</span></span> <span data-ttu-id="f6906-107">İş akışı kalıcılığını etkin bir şekilde göstermek için, birden çok iş akışı örneğini başlatmayı ve sürdürmeyi destekleyen daha karmaşık bir iş akışı konağı gerekir.</span><span class="sxs-lookup"><span data-stu-id="f6906-107">In order to demonstrate workflow persistence effectively, a more complex workflow host is required that supports starting and resuming multiple workflow instances.</span></span> <span data-ttu-id="f6906-108">Öğreticideki Bu adım, birden çok iş akışı örneğini başlatma ve sürdürmeyi destekleyen bir Windows form ana bilgisayar uygulamasının nasıl oluşturulduğunu, iş akışı kalıcılığını ve sonraki öğretici adımlarında gösterilen izleme ve sürüm oluşturma gibi gelişmiş özellikler için bir temel sağlar.</span><span class="sxs-lookup"><span data-stu-id="f6906-108">This step in the tutorial demonstrates how to create a Windows form host application that supports starting and resuming multiple workflow instances, workflow persistence, and provides a basis for the advanced features such as tracking and versioning that are demonstrated in subsequent tutorial steps.</span></span>

> [!NOTE]
> <span data-ttu-id="f6906-109">Bu öğretici adımı ve sonraki adımlarda, [nasıl yapılır: Iş akışı oluşturma](how-to-create-a-workflow.md)ile üç iş akışı türü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f6906-109">This tutorial step and the subsequent steps use all three workflow types from [How to: Create a Workflow](how-to-create-a-workflow.md).</span></span>

## <a name="to-create-the-persistence-database"></a><span data-ttu-id="f6906-110">Kalıcılık veritabanını oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="f6906-110">To create the persistence database</span></span>

1. <span data-ttu-id="f6906-111">SQL Server Management Studio açın ve yerel sunucuya bağlanın, örneğin **.\Sqlexpress**.</span><span class="sxs-lookup"><span data-stu-id="f6906-111">Open SQL Server Management Studio and connect to the local server, for example **.\SQLEXPRESS**.</span></span> <span data-ttu-id="f6906-112">Yerel sunucuda **veritabanları** düğümüne sağ tıklayın ve **Yeni veritabanı**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="f6906-112">Right-click the **Databases** node on the local server, and select **New Database**.</span></span> <span data-ttu-id="f6906-113">Yeni veritabanını **WF45GettingStartedTutorial** olarak adlandırın, diğer tüm değerleri kabul edin ve **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="f6906-113">Name the new database **WF45GettingStartedTutorial**, accept all other values, and select **OK**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="f6906-114">Veritabanını oluşturmadan önce yerel sunucuda **Create Database** iznine sahip olduğunuzdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="f6906-114">Ensure that you have **Create Database** permission on the local server before creating the database.</span></span>

2. <span data-ttu-id="f6906-115">**Dosya** menüsünden **Aç**, **Dosya** ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="f6906-115">Choose **Open**, **File** from the **File** menu.</span></span> <span data-ttu-id="f6906-116">Şu klasöre gidin: *C:\Windows\Microsoft.NET\Framework\v4.0.30319\sql\en*</span><span class="sxs-lookup"><span data-stu-id="f6906-116">Browse to the following folder: *C:\Windows\Microsoft.NET\Framework\v4.0.30319\sql\en*</span></span>

    <span data-ttu-id="f6906-117">Aşağıdaki iki dosyayı seçin ve **Aç**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f6906-117">Select the following two files and click **Open**.</span></span>

    - <span data-ttu-id="f6906-118">*Sqlworkflowcestorelogic. SQL*</span><span class="sxs-lookup"><span data-stu-id="f6906-118">*SqlWorkflowInstanceStoreLogic.sql*</span></span>

    - <span data-ttu-id="f6906-119">*SqlWorkflowInstanceStoreSchema. SQL*</span><span class="sxs-lookup"><span data-stu-id="f6906-119">*SqlWorkflowInstanceStoreSchema.sql*</span></span>

3. <span data-ttu-id="f6906-120">**Pencere** menüsünden **SqlWorkflowInstanceStoreSchema. SQL** öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="f6906-120">Choose **SqlWorkflowInstanceStoreSchema.sql** from the **Window** menu.</span></span> <span data-ttu-id="f6906-121">**Kullanılabilir veritabanları** açılan menüsünde **WF45GettingStartedTutorial** ' nin seçili olduğundan emin olun ve **sorgu** menüsünden **Yürüt** ' ü seçin.</span><span class="sxs-lookup"><span data-stu-id="f6906-121">Ensure that **WF45GettingStartedTutorial** is selected in the **Available Databases** drop-down and choose **Execute** from the **Query** menu.</span></span>

4. <span data-ttu-id="f6906-122">**Pencere** menüsünden **Sqlworkflowcestorelogic. SQL** öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="f6906-122">Choose **SqlWorkflowInstanceStoreLogic.sql** from the **Window** menu.</span></span> <span data-ttu-id="f6906-123">**Kullanılabilir veritabanları** açılan menüsünde **WF45GettingStartedTutorial** ' nin seçili olduğundan emin olun ve **sorgu** menüsünden **Yürüt** ' ü seçin.</span><span class="sxs-lookup"><span data-stu-id="f6906-123">Ensure that **WF45GettingStartedTutorial** is selected in the **Available Databases** drop-down and choose **Execute** from the **Query** menu.</span></span>

    > [!WARNING]
    > <span data-ttu-id="f6906-124">Önceki iki adımı doğru sırada gerçekleştirmek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="f6906-124">It is important to perform the previous two steps in the correct order.</span></span> <span data-ttu-id="f6906-125">Sorgular sıra dışında yürütülürse hatalar oluşur ve Kalıcılık veritabanı doğru şekilde yapılandırılmaz.</span><span class="sxs-lookup"><span data-stu-id="f6906-125">If the queries are executed out of order, errors occur and the persistence database is not configured correctly.</span></span>

## <a name="to-add-the-reference-to-the-durableinstancing-assemblies"></a><span data-ttu-id="f6906-126">Başvuruyu Durableörnek oluşturma derlemelerine eklemek için</span><span class="sxs-lookup"><span data-stu-id="f6906-126">To add the reference to the DurableInstancing assemblies</span></span>

1. <span data-ttu-id="f6906-127">**Çözüm Gezgini** Için **Numberguessworkflowwhost** öğesine sağ tıklayın ve **Başvuru Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="f6906-127">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and select **Add Reference**.</span></span>

2. <span data-ttu-id="f6906-128">**Başvuru Ekle** listesinden **derlemeler** ' i seçin ve `DurableInstancing` **derleme ara** kutusuna yazın.</span><span class="sxs-lookup"><span data-stu-id="f6906-128">Select **Assemblies** from the **Add Reference** list, and type `DurableInstancing` into the **Search Assemblies** box.</span></span> <span data-ttu-id="f6906-129">Bu, derlemelerin filtreleyeceğini ve istenen başvuruların seçimi daha kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="f6906-129">This filters the assemblies and makes the desired references easier to select.</span></span>

3. <span data-ttu-id="f6906-130">**Arama sonuçları** listesinden **System. Activities. durableörnekınlist** ve **System. Runtime. durableörnekno** ' ın yanındaki onay kutusunu işaretleyin ve **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f6906-130">Check the checkbox beside **System.Activities.DurableInstancing** and **System.Runtime.DurableInstancing** from the **Search Results** list, and click **OK**.</span></span>

## <a name="to-create-the-workflow-host-form"></a><span data-ttu-id="f6906-131">İş akışı konak formunu oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="f6906-131">To create the workflow host form</span></span>

1. <span data-ttu-id="f6906-132">**Çözüm Gezgini** Için **Numberguessworkflowwhost** öğesine sağ tıklayın ve **Ekle**, **Yeni öğe** seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="f6906-132">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **New Item**.</span></span>

2. <span data-ttu-id="f6906-133">**Yüklü** şablonlar listesinde, **Windows formu**' nu seçin, `WorkflowHostForm` **ad** kutusuna yazın ve **Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f6906-133">In the **Installed** templates list, choose **Windows Form**, type `WorkflowHostForm` in the **Name** box, and click **Add**.</span></span>

3. <span data-ttu-id="f6906-134">Formda aşağıdaki özellikleri yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="f6906-134">Configure the following properties on the form.</span></span>

    |<span data-ttu-id="f6906-135">Özellik</span><span class="sxs-lookup"><span data-stu-id="f6906-135">Property</span></span>|<span data-ttu-id="f6906-136">Değer</span><span class="sxs-lookup"><span data-stu-id="f6906-136">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="f6906-137">FormBorderStyle</span><span class="sxs-lookup"><span data-stu-id="f6906-137">FormBorderStyle</span></span>|<span data-ttu-id="f6906-138">FixedSingle</span><span class="sxs-lookup"><span data-stu-id="f6906-138">FixedSingle</span></span>|
    |<span data-ttu-id="f6906-139">MaximizeBox</span><span class="sxs-lookup"><span data-stu-id="f6906-139">MaximizeBox</span></span>|<span data-ttu-id="f6906-140">Yanlış</span><span class="sxs-lookup"><span data-stu-id="f6906-140">False</span></span>|
    |<span data-ttu-id="f6906-141">Boyut</span><span class="sxs-lookup"><span data-stu-id="f6906-141">Size</span></span>|<span data-ttu-id="f6906-142">400, 420</span><span class="sxs-lookup"><span data-stu-id="f6906-142">400, 420</span></span>|

4. <span data-ttu-id="f6906-143">Aşağıdaki denetimleri, belirtilen sırada forma ekleyin ve özellikleri yönlendirildiği şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="f6906-143">Add the following controls to the form in the order specified and configure the properties as directed.</span></span>

    |<span data-ttu-id="f6906-144">Denetim</span><span class="sxs-lookup"><span data-stu-id="f6906-144">Control</span></span>|<span data-ttu-id="f6906-145">Özellik: değer</span><span class="sxs-lookup"><span data-stu-id="f6906-145">Property: Value</span></span>|
    |-------------|---------------------|
    |<span data-ttu-id="f6906-146">**Düğme**</span><span class="sxs-lookup"><span data-stu-id="f6906-146">**Button**</span></span>|<span data-ttu-id="f6906-147">Ad: NewGame</span><span class="sxs-lookup"><span data-stu-id="f6906-147">Name: NewGame</span></span><br /><br /> <span data-ttu-id="f6906-148">Konum: 13, 13</span><span class="sxs-lookup"><span data-stu-id="f6906-148">Location: 13, 13</span></span><br /><br /> <span data-ttu-id="f6906-149">Boyut: 75, 23</span><span class="sxs-lookup"><span data-stu-id="f6906-149">Size: 75, 23</span></span><br /><br /> <span data-ttu-id="f6906-150">Metin: yeni oyun</span><span class="sxs-lookup"><span data-stu-id="f6906-150">Text: New Game</span></span>|
    |<span data-ttu-id="f6906-151">**Etiketle**</span><span class="sxs-lookup"><span data-stu-id="f6906-151">**Label**</span></span>|<span data-ttu-id="f6906-152">Konum: 94, 18</span><span class="sxs-lookup"><span data-stu-id="f6906-152">Location: 94, 18</span></span><br /><br /> <span data-ttu-id="f6906-153">Metin: 1 ile arasında bir sayı tahmin edin</span><span class="sxs-lookup"><span data-stu-id="f6906-153">Text: Guess a number from 1 to</span></span>|
    |<span data-ttu-id="f6906-154">**ComboBox**</span><span class="sxs-lookup"><span data-stu-id="f6906-154">**ComboBox**</span></span>|<span data-ttu-id="f6906-155">Ad: NumberRange</span><span class="sxs-lookup"><span data-stu-id="f6906-155">Name: NumberRange</span></span><br /><br /> <span data-ttu-id="f6906-156">DropDownStyle: DropDownList</span><span class="sxs-lookup"><span data-stu-id="f6906-156">DropDownStyle: DropDownList</span></span><br /><br /> <span data-ttu-id="f6906-157">Öğeler: 10, 100, 1000</span><span class="sxs-lookup"><span data-stu-id="f6906-157">Items: 10, 100, 1000</span></span><br /><br /> <span data-ttu-id="f6906-158">Konum: 228, 12</span><span class="sxs-lookup"><span data-stu-id="f6906-158">Location: 228, 12</span></span><br /><br /> <span data-ttu-id="f6906-159">Boyut: 143, 21</span><span class="sxs-lookup"><span data-stu-id="f6906-159">Size: 143, 21</span></span>|
    |<span data-ttu-id="f6906-160">**Etiketle**</span><span class="sxs-lookup"><span data-stu-id="f6906-160">**Label**</span></span>|<span data-ttu-id="f6906-161">Konum: 13, 43</span><span class="sxs-lookup"><span data-stu-id="f6906-161">Location: 13, 43</span></span><br /><br /> <span data-ttu-id="f6906-162">Metin: Iş akışı türü</span><span class="sxs-lookup"><span data-stu-id="f6906-162">Text: Workflow type</span></span>|
    |<span data-ttu-id="f6906-163">**ComboBox**</span><span class="sxs-lookup"><span data-stu-id="f6906-163">**ComboBox**</span></span>|<span data-ttu-id="f6906-164">Ad: WorkflowType</span><span class="sxs-lookup"><span data-stu-id="f6906-164">Name: WorkflowType</span></span><br /><br /> <span data-ttu-id="f6906-165">DropDownStyle: DropDownList</span><span class="sxs-lookup"><span data-stu-id="f6906-165">DropDownStyle: DropDownList</span></span><br /><br /> <span data-ttu-id="f6906-166">Öğeler: StateMachineNumberGuessWorkflow, FlowchartNumberGuessWorkflow, SequentialNumberGuessWorkflow</span><span class="sxs-lookup"><span data-stu-id="f6906-166">Items: StateMachineNumberGuessWorkflow, FlowchartNumberGuessWorkflow, SequentialNumberGuessWorkflow</span></span><br /><br /> <span data-ttu-id="f6906-167">Konum: 94, 40</span><span class="sxs-lookup"><span data-stu-id="f6906-167">Location: 94, 40</span></span><br /><br /> <span data-ttu-id="f6906-168">Boyut: 277, 21</span><span class="sxs-lookup"><span data-stu-id="f6906-168">Size: 277, 21</span></span>|
    |<span data-ttu-id="f6906-169">**Etiketle**</span><span class="sxs-lookup"><span data-stu-id="f6906-169">**Label**</span></span>|<span data-ttu-id="f6906-170">Ad: WorkflowVersion</span><span class="sxs-lookup"><span data-stu-id="f6906-170">Name: WorkflowVersion</span></span><br /><br /> <span data-ttu-id="f6906-171">Konum: 13, 362</span><span class="sxs-lookup"><span data-stu-id="f6906-171">Location: 13, 362</span></span><br /><br /> <span data-ttu-id="f6906-172">Metin: Iş akışı sürümü</span><span class="sxs-lookup"><span data-stu-id="f6906-172">Text: Workflow version</span></span>|
    |<span data-ttu-id="f6906-173">**GroupBox**</span><span class="sxs-lookup"><span data-stu-id="f6906-173">**GroupBox**</span></span>|<span data-ttu-id="f6906-174">Konum: 13, 67</span><span class="sxs-lookup"><span data-stu-id="f6906-174">Location: 13, 67</span></span><br /><br /> <span data-ttu-id="f6906-175">Boyut: 358, 287</span><span class="sxs-lookup"><span data-stu-id="f6906-175">Size: 358, 287</span></span><br /><br /> <span data-ttu-id="f6906-176">Metin: oyun</span><span class="sxs-lookup"><span data-stu-id="f6906-176">Text: Game</span></span>|

    > [!NOTE]
    > <span data-ttu-id="f6906-177">Aşağıdaki denetimleri eklerken GroupBox içine yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="f6906-177">When adding the following controls, put them into the GroupBox.</span></span>

    |<span data-ttu-id="f6906-178">Denetim</span><span class="sxs-lookup"><span data-stu-id="f6906-178">Control</span></span>|<span data-ttu-id="f6906-179">Özellik: değer</span><span class="sxs-lookup"><span data-stu-id="f6906-179">Property: Value</span></span>|
    |-------------|---------------------|
    |<span data-ttu-id="f6906-180">**Etiketle**</span><span class="sxs-lookup"><span data-stu-id="f6906-180">**Label**</span></span>|<span data-ttu-id="f6906-181">Konum: 7, 20</span><span class="sxs-lookup"><span data-stu-id="f6906-181">Location: 7, 20</span></span><br /><br /> <span data-ttu-id="f6906-182">Metin: Iş akışı örneği kimliği</span><span class="sxs-lookup"><span data-stu-id="f6906-182">Text: Workflow Instance Id</span></span>|
    |<span data-ttu-id="f6906-183">**ComboBox**</span><span class="sxs-lookup"><span data-stu-id="f6906-183">**ComboBox**</span></span>|<span data-ttu-id="f6906-184">Ad: InstanceId</span><span class="sxs-lookup"><span data-stu-id="f6906-184">Name: InstanceId</span></span><br /><br /> <span data-ttu-id="f6906-185">DropDownStyle: DropDownList</span><span class="sxs-lookup"><span data-stu-id="f6906-185">DropDownStyle: DropDownList</span></span><br /><br /> <span data-ttu-id="f6906-186">Konum: 121, 17</span><span class="sxs-lookup"><span data-stu-id="f6906-186">Location: 121, 17</span></span><br /><br /> <span data-ttu-id="f6906-187">Boyut: 227, 21</span><span class="sxs-lookup"><span data-stu-id="f6906-187">Size: 227, 21</span></span>|
    |<span data-ttu-id="f6906-188">**Etiketle**</span><span class="sxs-lookup"><span data-stu-id="f6906-188">**Label**</span></span>|<span data-ttu-id="f6906-189">Konum: 7, 47</span><span class="sxs-lookup"><span data-stu-id="f6906-189">Location: 7, 47</span></span><br /><br /> <span data-ttu-id="f6906-190">Metin: tahmin</span><span class="sxs-lookup"><span data-stu-id="f6906-190">Text: Guess</span></span>|
    |<span data-ttu-id="f6906-191">**TextBox**</span><span class="sxs-lookup"><span data-stu-id="f6906-191">**TextBox**</span></span>|<span data-ttu-id="f6906-192">Ad: tahmin</span><span class="sxs-lookup"><span data-stu-id="f6906-192">Name: Guess</span></span><br /><br /> <span data-ttu-id="f6906-193">Konum: 50, 44</span><span class="sxs-lookup"><span data-stu-id="f6906-193">Location: 50, 44</span></span><br /><br /> <span data-ttu-id="f6906-194">Boyut: 65, 20</span><span class="sxs-lookup"><span data-stu-id="f6906-194">Size: 65, 20</span></span>|
    |<span data-ttu-id="f6906-195">**Düğme**</span><span class="sxs-lookup"><span data-stu-id="f6906-195">**Button**</span></span>|<span data-ttu-id="f6906-196">Ad: Entertahmin</span><span class="sxs-lookup"><span data-stu-id="f6906-196">Name: EnterGuess</span></span><br /><br /> <span data-ttu-id="f6906-197">Konum: 121, 42</span><span class="sxs-lookup"><span data-stu-id="f6906-197">Location: 121, 42</span></span><br /><br /> <span data-ttu-id="f6906-198">Boyut: 75, 23</span><span class="sxs-lookup"><span data-stu-id="f6906-198">Size: 75, 23</span></span><br /><br /> <span data-ttu-id="f6906-199">Metin: tahmin girin</span><span class="sxs-lookup"><span data-stu-id="f6906-199">Text: Enter Guess</span></span>|
    |<span data-ttu-id="f6906-200">**Düğme**</span><span class="sxs-lookup"><span data-stu-id="f6906-200">**Button**</span></span>|<span data-ttu-id="f6906-201">Ad: QuitGame</span><span class="sxs-lookup"><span data-stu-id="f6906-201">Name: QuitGame</span></span><br /><br /> <span data-ttu-id="f6906-202">Konum: 274, 42</span><span class="sxs-lookup"><span data-stu-id="f6906-202">Location: 274, 42</span></span><br /><br /> <span data-ttu-id="f6906-203">Boyut: 75, 23</span><span class="sxs-lookup"><span data-stu-id="f6906-203">Size: 75, 23</span></span><br /><br /> <span data-ttu-id="f6906-204">Metin: çık</span><span class="sxs-lookup"><span data-stu-id="f6906-204">Text: Quit</span></span>|
    |<span data-ttu-id="f6906-205">**TextBox**</span><span class="sxs-lookup"><span data-stu-id="f6906-205">**TextBox**</span></span>|<span data-ttu-id="f6906-206">Ad: WorkflowStatus</span><span class="sxs-lookup"><span data-stu-id="f6906-206">Name: WorkflowStatus</span></span><br /><br /> <span data-ttu-id="f6906-207">Konum: 10, 73</span><span class="sxs-lookup"><span data-stu-id="f6906-207">Location: 10, 73</span></span><br /><br /> <span data-ttu-id="f6906-208">Çoklu satır: doğru</span><span class="sxs-lookup"><span data-stu-id="f6906-208">Multiline: True</span></span><br /><br /> <span data-ttu-id="f6906-209">ReadOnly: true</span><span class="sxs-lookup"><span data-stu-id="f6906-209">ReadOnly: True</span></span><br /><br /> <span data-ttu-id="f6906-210">Kaydırma çubukları: dikey</span><span class="sxs-lookup"><span data-stu-id="f6906-210">ScrollBars: Vertical</span></span><br /><br /> <span data-ttu-id="f6906-211">Boyut: 338, 208</span><span class="sxs-lookup"><span data-stu-id="f6906-211">Size: 338, 208</span></span>|

5. <span data-ttu-id="f6906-212">Formun **AcceptButton** özelliğini **entertahmin** olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f6906-212">Set the **AcceptButton** property of the form to **EnterGuess**.</span></span>

 <span data-ttu-id="f6906-213">Aşağıdaki örnekte tamamlanan form gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f6906-213">The following example illustrates the completed form.</span></span>

 ![Windows Workflow Foundation Iş akışı konak formunun ekran görüntüsü.](./media/how-to-create-and-run-a-long-running-workflow/windows-workflow-foundation-workflowhostform.png)

## <a name="to-add-the-properties-and-helper-methods-of-the-form"></a><span data-ttu-id="f6906-215">Formun özelliklerini ve yardımcı yöntemlerini eklemek için</span><span class="sxs-lookup"><span data-stu-id="f6906-215">To add the properties and helper methods of the form</span></span>

<span data-ttu-id="f6906-216">Bu bölümdeki adımlarda, form sınıfına, çalışma ve tahmin sayısı tahmin iş akışlarına devam ettirmek için formun Kullanıcı arabirimini yapılandıran Özellikler ve yardımcı yöntemler ekleme.</span><span class="sxs-lookup"><span data-stu-id="f6906-216">The steps in this section add properties and helper methods to the form class that configure the UI of the form to support running and resuming number guess workflows.</span></span>

1. <span data-ttu-id="f6906-217">**Çözüm Gezgini** ' de **Workflowwhostform** öğesine sağ tıklayın ve **kodu görüntüle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="f6906-217">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>

2. <span data-ttu-id="f6906-218">Aşağıdaki `using` (veya `Imports` ) deyimlerini, diğer `using` (veya `Imports` ) deyimleriyle dosyanın en üstüne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f6906-218">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>

    ```vb
    Imports System.Activities
    Imports System.Activities.DurableInstancing
    Imports System.Data.SqlClient
    Imports System.IO
    Imports System.Windows.Forms
    ```

    ```csharp
    using System.Activities;
    using System.Activities.DurableInstancing;
    using System.Data.SqlClient;
    using System.IO;
    using System.Windows.Forms;
    ```

3. <span data-ttu-id="f6906-219">Aşağıdaki üye bildirimlerini **Workflowwhostform** sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f6906-219">Add the following member declarations to the **WorkflowHostForm** class.</span></span>

    ```vb
    Const connectionString = "Server=.\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI"
    Dim store As SqlWorkflowInstanceStore
    Dim workflowStarting As Boolean
    ```

    ```csharp
    const string connectionString = "Server=.\\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI";
    SqlWorkflowInstanceStore store;
    bool workflowStarting;
    ```

    > [!NOTE]
    > <span data-ttu-id="f6906-220">Bağlantı dizeniz farklıysa, `connectionString` veritabanınıza başvuracak şekilde güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="f6906-220">If your connection string is different, update `connectionString` to refer to your database.</span></span>

4. <span data-ttu-id="f6906-221">Sınıfına bir `WorkflowInstanceId` özellik ekleyin `WorkflowFormHost` .</span><span class="sxs-lookup"><span data-stu-id="f6906-221">Add a `WorkflowInstanceId` property to the `WorkflowFormHost` class.</span></span>

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

    <span data-ttu-id="f6906-222">`InstanceId`Birleşik giriş kutusu kalıcı iş akışı örneği kimliklerinin bir listesini görüntüler ve `WorkflowInstanceId` özelliği şu anda seçili olan iş akışını döndürür.</span><span class="sxs-lookup"><span data-stu-id="f6906-222">The `InstanceId` combo box displays a list of persisted workflow instance ids, and the `WorkflowInstanceId` property returns the currently selected workflow.</span></span>

5. <span data-ttu-id="f6906-223">Form olayı için bir işleyici ekleyin `Load` .</span><span class="sxs-lookup"><span data-stu-id="f6906-223">Add a handler for the form `Load` event.</span></span> <span data-ttu-id="f6906-224">İşleyiciyi eklemek için form için **Tasarım görünümüne** geçin, **Özellikler** penceresinin üst kısmındaki **Olaylar** simgesine tıklayın ve **Yükle**' ye çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f6906-224">To add the handler, switch to **Design View** for the form, click the **Events** icon at the top of the **Properties** window, and double-click **Load**.</span></span>

    ```vb
    Private Sub WorkflowHostForm_Load(sender As Object, e As EventArgs) Handles Me.Load

    End Sub
    ```

    ```csharp
    private void WorkflowHostForm_Load(object sender, EventArgs e)
    {

    }
    ```

6. <span data-ttu-id="f6906-225">Aşağıdaki kodu `WorkflowHostForm_Load` içine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f6906-225">Add the following code to `WorkflowHostForm_Load`.</span></span>

    ```vb
    ' Initialize the store and configure it so that it can be used for
    ' multiple WorkflowApplication instances.
    store = New SqlWorkflowInstanceStore(connectionString)
    WorkflowApplication.CreateDefaultInstanceOwner(store, Nothing, WorkflowIdentityFilter.Any)

    ' Set default ComboBox selections.
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

    <span data-ttu-id="f6906-226">Form yüklendiğinde,, `SqlWorkflowInstanceStore` Aralık ve iş akışı türü Birleşik giriş kutuları varsayılan değerlere ayarlanır ve kalıcı iş akışı örnekleri `InstanceId` açılan kutuya eklenir.</span><span class="sxs-lookup"><span data-stu-id="f6906-226">When the form loads, the `SqlWorkflowInstanceStore` is configured, the range and workflow type combo boxes are set to default values, and the persisted workflow instances are added to the `InstanceId` combo box.</span></span>

7. <span data-ttu-id="f6906-227">İçin bir `SelectedIndexChanged` işleyici ekleyin `InstanceId` .</span><span class="sxs-lookup"><span data-stu-id="f6906-227">Add a `SelectedIndexChanged` handler for `InstanceId`.</span></span> <span data-ttu-id="f6906-228">İşleyiciyi eklemek için form için **Tasarım görünümüne** geçiş yapın, `InstanceId` açılan kutuyu seçin, **Özellikler** penceresinin üst kısmındaki **Olaylar** simgesine tıklayın ve **SelectedIndexChanged** öğesine çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f6906-228">To add the handler, switch to **Design View** for the form, select the `InstanceId` combo box, click the **Events** icon at the top of the **Properties** window, and double-click **SelectedIndexChanged**.</span></span>

    ```vb
    Private Sub InstanceId_SelectedIndexChanged(sender As Object, e As EventArgs) Handles InstanceId.SelectedIndexChanged

    End Sub
    ```

    ```csharp
    private void InstanceId_SelectedIndexChanged(object sender, EventArgs e)
    {

    }
    ```

8. <span data-ttu-id="f6906-229">Aşağıdaki kodu `InstanceId_SelectedIndexChanged` içine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f6906-229">Add the following code to `InstanceId_SelectedIndexChanged`.</span></span> <span data-ttu-id="f6906-230">Kullanıcı açılan kutuyu kullanarak bir iş akışı seçtiğinde, bu işleyici durum penceresini güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="f6906-230">Whenever the user selects a workflow by using the combo box this handler updates the status window.</span></span>

    ```vb
    If InstanceId.SelectedIndex = -1 Then
        Return
    End If

    ' Clear the status window.
    WorkflowStatus.Clear()

    ' Get the workflow version and display it.
    ' If the workflow is just starting then this info will not
    ' be available in the persistence store so do not try and retrieve it.
    If Not workflowStarting Then
        Dim instance As WorkflowApplicationInstance = _
            WorkflowApplication.GetInstance(WorkflowInstanceId, store)

        WorkflowVersion.Text = _
            WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity)

        ' Unload the instance.
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
    if (!workflowStarting)
    {
        WorkflowApplicationInstance instance =
            WorkflowApplication.GetInstance(this.WorkflowInstanceId, store);

        WorkflowVersion.Text =
            WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity);

        // Unload the instance.
        instance.Abandon();
    }
    ```

9. <span data-ttu-id="f6906-231">Aşağıdaki `ListPersistedWorkflows` yöntemi form sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f6906-231">Add the following `ListPersistedWorkflows` method to the form class.</span></span>

    ```vb
    Private Sub ListPersistedWorkflows()
        Using localCon As New SqlConnection(connectionString)
            Dim localCmd As String = _
                "SELECT [InstanceId] FROM [System.Activities.DurableInstancing].[Instances] ORDER BY [CreationTime]"

            Dim cmd As SqlCommand = localCon.CreateCommand()
            cmd.CommandText = localCmd
            localCon.Open()
            Using reader As SqlDataReader = cmd.ExecuteReader(CommandBehavior.CloseConnection)

                While (reader.Read())
                    ' Get the InstanceId of the persisted Workflow.
                    Dim id As Guid = Guid.Parse(reader(0).ToString())
                    InstanceId.Items.Add(id)
                End While
            End Using
        End Using
    End Sub
    ```

    ```csharp
    using (var localCon = new SqlConnection(connectionString))
    {
        string localCmd =
            "SELECT [InstanceId] FROM [System.Activities.DurableInstancing].[Instances] ORDER BY [CreationTime]";

        SqlCommand cmd = localCon.CreateCommand();
        cmd.CommandText = localCmd;
        localCon.Open();
        using (SqlDataReader reader = cmd.ExecuteReader(CommandBehavior.CloseConnection))
        {
            while (reader.Read())
            {
                // Get the InstanceId of the persisted Workflow.
                Guid id = Guid.Parse(reader[0].ToString());
                InstanceId.Items.Add(id);
            }
        }
    }
    ```

    <span data-ttu-id="f6906-232">`ListPersistedWorkflows` kalıcı iş akışı örnekleri için örnek deposunu sorgular ve `cboInstanceId` Birleşik giriş kutusuna örnek kimliklerini ekler.</span><span class="sxs-lookup"><span data-stu-id="f6906-232">`ListPersistedWorkflows` queries the instance store for persisted workflow instances, and adds the instance ids to the `cboInstanceId` combo box.</span></span>

10. <span data-ttu-id="f6906-233">`UpdateStatus`Form sınıfına aşağıdaki yöntemi ve ilgili temsilciyi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f6906-233">Add the following `UpdateStatus` method and corresponding delegate to the form class.</span></span> <span data-ttu-id="f6906-234">Bu yöntem, form üzerindeki durum penceresini Şu anda çalışan iş akışının durumuyla güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="f6906-234">This method updates the status window on the form with the status of the currently running workflow.</span></span>

    ```vb
    Private Delegate Sub UpdateStatusDelegate(msg As String)
    Public Sub UpdateStatus(msg As String)
        ' We may be on a different thread so we need to
        ' make this call using BeginInvoke.
        If InvokeRequired Then
            BeginInvoke(New UpdateStatusDelegate(AddressOf UpdateStatus), msg)
        Else
            If Not msg.EndsWith(vbCrLf) Then
                msg = msg & vbCrLf
            End If

            WorkflowStatus.AppendText(msg)

            ' Ensure that the newly added status is visible.
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

11. <span data-ttu-id="f6906-235">`GameOver`Form sınıfına aşağıdaki yöntemi ve ilgili temsilciyi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f6906-235">Add the following `GameOver` method and corresponding delegate to the form class.</span></span> <span data-ttu-id="f6906-236">Bir iş akışı tamamlandığında, bu yöntem, **InstanceId** Birleşik giriş kutusundan tamamlanan iş akışının örnek kimliğini kaldırarak form kullanıcı arabirimini güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="f6906-236">When a workflow completes, this method updates the form UI by removing the instance id of the completed workflow from the **InstanceId** combo box.</span></span>

    ```vb
    Private Delegate Sub GameOverDelegate()
    Private Sub GameOver()
        If InvokeRequired Then
            BeginInvoke(New GameOverDelegate(AddressOf GameOver))
        Else
            ' Remove this instance from the InstanceId combo box.
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
            // Remove this instance from the combo box.
            InstanceId.Items.Remove(InstanceId.SelectedItem);
            InstanceId.SelectedIndex = -1;
        }
    }
    ```

## <a name="to-configure-the-instance-store-workflow-lifecycle-handlers-and-extensions"></a><span data-ttu-id="f6906-237">Örnek deposunu, iş akışı yaşam döngüsü işleyicilerini ve uzantıları yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="f6906-237">To configure the instance store, workflow lifecycle handlers, and extensions</span></span>

1. <span data-ttu-id="f6906-238">`ConfigureWorkflowApplication`Form sınıfına bir yöntem ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f6906-238">Add a `ConfigureWorkflowApplication` method to the form class.</span></span>

    ```vb
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)

    End Sub
    ```

    ```csharp
    private void ConfigureWorkflowApplication(WorkflowApplication wfApp)
    {
    }
    ```

    <span data-ttu-id="f6906-239">Bu yöntem, `WorkflowApplication` öğesini yapılandırır, istenen uzantıları ekler ve iş akışı yaşam döngüsü olayları için işleyiciler ekler.</span><span class="sxs-lookup"><span data-stu-id="f6906-239">This method configures the `WorkflowApplication`, adds the desired extensions, and adds handlers for the workflow lifecycle events.</span></span>

2. <span data-ttu-id="f6906-240">İçinde, `ConfigureWorkflowApplication` için öğesini belirtin `SqlWorkflowInstanceStore` `WorkflowApplication` .</span><span class="sxs-lookup"><span data-stu-id="f6906-240">In `ConfigureWorkflowApplication`, specify the `SqlWorkflowInstanceStore` for the `WorkflowApplication`.</span></span>

    ```vb
    ' Configure the persistence store.
    wfApp.InstanceStore = store
    ```

    ```csharp
    // Configure the persistence store.
    wfApp.InstanceStore = store;
    ```

3. <span data-ttu-id="f6906-241">Sonra bir örnek oluşturun `StringWriter` ve `Extensions` koleksiyonuna ekleyin `WorkflowApplication` .</span><span class="sxs-lookup"><span data-stu-id="f6906-241">Next, create a `StringWriter` instance and add it to the `Extensions` collection of the `WorkflowApplication`.</span></span> <span data-ttu-id="f6906-242">`StringWriter`Uzantılara eklendiğinde, tüm `WriteLine` etkinlik çıkışlarını yakalar.</span><span class="sxs-lookup"><span data-stu-id="f6906-242">When a `StringWriter` is added to the extensions it captures all `WriteLine` activity output.</span></span> <span data-ttu-id="f6906-243">İş akışı boşta olduğunda, `WriteLine` Çıkış konumundan `StringWriter` ayıklanıp formda görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="f6906-243">When the workflow becomes idle, the `WriteLine` output can be extracted from the `StringWriter` and displayed on the form.</span></span>

    ```vb
    ' Add a StringWriter to the extensions. This captures the output
    ' from the WriteLine activities so we can display it in the form.
    Dim sw As New StringWriter()
    wfApp.Extensions.Add(sw)
    ```

    ```csharp
    // Add a StringWriter to the extensions. This captures the output
    // from the WriteLine activities so we can display it in the form.
    var sw = new StringWriter();
    wfApp.Extensions.Add(sw);
    ```

4. <span data-ttu-id="f6906-244">Olay için aşağıdaki işleyiciyi ekleyin `Completed` .</span><span class="sxs-lookup"><span data-stu-id="f6906-244">Add the following handler for the `Completed` event.</span></span> <span data-ttu-id="f6906-245">Bir iş akışı başarıyla tamamlandığında, sayıyı tahmin etmek için yapılan dönüşün sayısı durum penceresine görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f6906-245">When a workflow successfully completes, the number of turns taken to guess the number is displayed to the status window.</span></span> <span data-ttu-id="f6906-246">İş akışı sonlandığında, sonlandırmasına neden olan özel durum bilgileri görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f6906-246">If the workflow terminates, the exception information that caused the termination is displayed.</span></span> <span data-ttu-id="f6906-247">İşleyicinin sonunda `GameOver` yöntem çağrılır, bu, tamamlanan iş akışını iş akışı listesinden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="f6906-247">At the end of the handler the `GameOver` method is called, which removes the completed workflow from the workflow list.</span></span>

    ```vb
    wfApp.Completed = _
        Sub(e As WorkflowApplicationCompletedEventArgs)
            If e.CompletionState = ActivityInstanceState.Faulted Then
                UpdateStatus($"Workflow Terminated. Exception: {e.TerminationException.GetType().FullName}{vbCrLf}{e.TerminationException.Message}")
            ElseIf e.CompletionState = ActivityInstanceState.Canceled Then
                UpdateStatus("Workflow Canceled.")
            Else
                Dim turns As Integer = Convert.ToInt32(e.Outputs("Turns"))
                UpdateStatus($"Congratulations, you guessed the number in {turns} turns.")
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
            int turns = Convert.ToInt32(e.Outputs["Turns"]);
            UpdateStatus($"Congratulations, you guessed the number in {turns} turns.");
        }
        GameOver();
    };
    ```

5. <span data-ttu-id="f6906-248">Aşağıdakileri `Aborted` ve işleyicileri ekleyin `OnUnhandledException` .</span><span class="sxs-lookup"><span data-stu-id="f6906-248">Add the following `Aborted` and `OnUnhandledException` handlers.</span></span> <span data-ttu-id="f6906-249">`GameOver`Yöntemi, `Aborted` bir iş akışı örneği iptal edildiğinde, Sonlanmadığı ve örneği daha sonra sürdürülmesi mümkün olduğu için işleyiciden çağrılmaz.</span><span class="sxs-lookup"><span data-stu-id="f6906-249">The `GameOver` method is not called from the `Aborted` handler because when a workflow instance is aborted, it does not terminate, and it is possible to resume the instance at a later time.</span></span>

    ```vb
    wfApp.Aborted = _
        Sub(e As WorkflowApplicationAbortedEventArgs)
            UpdateStatus($"Workflow Aborted. Exception: {e.Reason.GetType().FullName}{vbCrLf}{e.Reason.Message}")
        End Sub

    wfApp.OnUnhandledException = _
        Function(e As WorkflowApplicationUnhandledExceptionEventArgs)
            UpdateStatus($"Unhandled Exception: {e.UnhandledException.GetType().FullName}{vbCrLf}{e.UnhandledException.Message}")
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

6. <span data-ttu-id="f6906-250">Aşağıdaki işleyiciyi ekleyin `PersistableIdle` .</span><span class="sxs-lookup"><span data-stu-id="f6906-250">Add the following `PersistableIdle` handler.</span></span> <span data-ttu-id="f6906-251">Bu işleyici `StringWriter` eklenen uzantıyı alır, `WriteLine` etkinliklerdeki çıktıyı ayıklar ve durum penceresinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f6906-251">This handler retrieves the `StringWriter` extension that was added, extracts the output from the `WriteLine` activities, and displays it in the status window.</span></span>

    ```vb
    wfApp.PersistableIdle = _
        Function(e As WorkflowApplicationIdleEventArgs)
            ' Send the current WriteLine outputs to the status window.
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

    <span data-ttu-id="f6906-252"><xref:System.Activities.PersistableIdleAction>Numaralandırmada üç değer vardır: <xref:System.Activities.PersistableIdleAction.None> , <xref:System.Activities.PersistableIdleAction.Persist> , ve <xref:System.Activities.PersistableIdleAction.Unload> .</span><span class="sxs-lookup"><span data-stu-id="f6906-252">The <xref:System.Activities.PersistableIdleAction> enumeration has three values: <xref:System.Activities.PersistableIdleAction.None>, <xref:System.Activities.PersistableIdleAction.Persist>, and <xref:System.Activities.PersistableIdleAction.Unload>.</span></span> <span data-ttu-id="f6906-253"><xref:System.Activities.PersistableIdleAction.Persist> iş akışının kalıcı olmasına neden olur, ancak iş akışının kaldırılmasına neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="f6906-253"><xref:System.Activities.PersistableIdleAction.Persist> causes the workflow to persist but it does not cause the workflow to unload.</span></span> <span data-ttu-id="f6906-254"><xref:System.Activities.PersistableIdleAction.Unload> iş akışının kalıcı ve kaldırılmış olmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="f6906-254"><xref:System.Activities.PersistableIdleAction.Unload> causes the workflow to persist and be unloaded.</span></span>

    <span data-ttu-id="f6906-255">Aşağıdaki örnek, tamamlanmış `ConfigureWorkflowApplication` yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="f6906-255">The following example is the completed `ConfigureWorkflowApplication` method.</span></span>

    ```vb
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)
        ' Configure the persistence store.
        wfApp.InstanceStore = store

        ' Add a StringWriter to the extensions. This captures the output
        ' from the WriteLine activities so we can display it in the form.
        Dim sw As New StringWriter()
        wfApp.Extensions.Add(sw)

        wfApp.Completed = _
            Sub(e As WorkflowApplicationCompletedEventArgs)
                If e.CompletionState = ActivityInstanceState.Faulted Then
                    UpdateStatus($"Workflow Terminated. Exception: {e.TerminationException.GetType().FullName}{vbCrLf}{e.TerminationException.Message}")
                ElseIf e.CompletionState = ActivityInstanceState.Canceled Then
                    UpdateStatus("Workflow Canceled.")
                Else
                    Dim turns As Integer = Convert.ToInt32(e.Outputs("Turns"))
                    UpdateStatus($"Congratulations, you guessed the number in {turns} turns.")
                End If
                GameOver()
            End Sub

        wfApp.Aborted = _
            Sub(e As WorkflowApplicationAbortedEventArgs)
                UpdateStatus($"Workflow Aborted. Exception: {e.Reason.GetType().FullName}{vbCrLf}{e.Reason.Message}")
            End Sub

        wfApp.OnUnhandledException = _
            Function(e As WorkflowApplicationUnhandledExceptionEventArgs)
                UpdateStatus($"Unhandled Exception: {e.UnhandledException.GetType().FullName}{vbCrLf}{e.UnhandledException.Message}")
                GameOver()
                Return UnhandledExceptionAction.Terminate
            End Function

        wfApp.PersistableIdle = _
            Function(e As WorkflowApplicationIdleEventArgs)
                ' Send the current WriteLine outputs to the status window.
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
        var sw = new StringWriter();
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
                int turns = Convert.ToInt32(e.Outputs["Turns"]);
                UpdateStatus($"Congratulations, you guessed the number in {turns} turns.");
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

## <a name="to-enable-starting-and-resuming-multiple-workflow-types"></a><span data-ttu-id="f6906-256">Birden çok iş akışı türünü başlatmayı ve sürdürmeyi etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="f6906-256">To enable starting and resuming multiple workflow types</span></span>

<span data-ttu-id="f6906-257">Bir iş akışı örneğinin sürdürülmesi için, konağın iş akışı tanımını sağlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f6906-257">In order to resume a workflow instance, the host has to provide the workflow definition.</span></span> <span data-ttu-id="f6906-258">Bu öğreticide, üç iş akışı türü vardır ve sonraki öğretici adımları bu türlerin birden çok sürümünü ortaya çıkarabilir.</span><span class="sxs-lookup"><span data-stu-id="f6906-258">In this tutorial there are three workflow types, and subsequent tutorial steps introduce multiple versions of these types.</span></span> <span data-ttu-id="f6906-259">`WorkflowIdentity` bir ana bilgisayar uygulamasının, tanımlayıcı bilgileri kalıcı bir iş akışı örneğiyle ilişkilendirmesi için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="f6906-259">`WorkflowIdentity` provides a way for a host application to associate identifying information with a persisted workflow instance.</span></span> <span data-ttu-id="f6906-260">Bu bölümdeki adımlarda, kalıcı bir iş akışı örneğinden ilgili iş akışı tanımına iş akışı kimliğini eşleştirmeye yardımcı olması için bir yardımcı program sınıfının nasıl oluşturulacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f6906-260">The steps in this section demonstrate how to create a utility class to assist with mapping the workflow identity from a persisted workflow instance to the corresponding workflow definition.</span></span> <span data-ttu-id="f6906-261">Ve sürümü oluşturma hakkında daha fazla bilgi için `WorkflowIdentity` bkz. [Workflowwıdentity ve sürümü kullanma](using-workflowidentity-and-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="f6906-261">For more information about `WorkflowIdentity` and versioning, see [Using WorkflowIdentity and Versioning](using-workflowidentity-and-versioning.md).</span></span>

1. <span data-ttu-id="f6906-262">**Çözüm Gezgini** Için **Numberguessworkflowwhost** öğesine sağ tıklayın ve **Ekle**, **sınıf**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="f6906-262">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **Class**.</span></span> <span data-ttu-id="f6906-263">`WorkflowVersionMap` **Ad** kutusuna yazın ve **Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f6906-263">Type `WorkflowVersionMap` into the **Name** box and click **Add**.</span></span>

2. <span data-ttu-id="f6906-264">Aşağıdaki veya deyimlerini `using` , `Imports` diğer `using` veya deyimleriyle dosyanın en üstüne ekleyin `Imports` .</span><span class="sxs-lookup"><span data-stu-id="f6906-264">Add the following `using` or `Imports` statements at the top of the file with the other `using` or `Imports` statements.</span></span>

    ```vb
    Imports System.Activities
    Imports NumberGuessWorkflowActivities
    ```

    ```csharp
    using System.Activities;
    using NumberGuessWorkflowActivities;
    ```

3. <span data-ttu-id="f6906-265">`WorkflowVersionMap`Sınıf bildirimini aşağıdaki bildirimle değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f6906-265">Replace the `WorkflowVersionMap` class declaration with the following declaration.</span></span>

    ```vb
    Public Module WorkflowVersionMap
        Dim map As Dictionary(Of WorkflowIdentity, Activity)

        ' Current version identities.
        Public StateMachineNumberGuessIdentity As WorkflowIdentity
        Public FlowchartNumberGuessIdentity As WorkflowIdentity
        Public SequentialNumberGuessIdentity As WorkflowIdentity

        Sub New()
            map = New Dictionary(Of WorkflowIdentity, Activity)

            ' Add the current workflow version identities.
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

    <span data-ttu-id="f6906-266">`WorkflowVersionMap` Bu öğreticideki üç iş akışı tanımına eşlenen üç iş akışı kimliği içerir ve iş akışları başlatıldığında ve sürdürüldüğünde aşağıdaki bölümlerde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f6906-266">`WorkflowVersionMap` contains three workflow identities that map to the three workflow definitions from this tutorial and is used in the following sections when workflows are started and resumed.</span></span>

## <a name="to-start-a-new-workflow"></a><span data-ttu-id="f6906-267">Yeni bir iş akışı başlatmak için</span><span class="sxs-lookup"><span data-stu-id="f6906-267">To start a new workflow</span></span>

1. <span data-ttu-id="f6906-268">İçin bir `Click` işleyici ekleyin `NewGame` .</span><span class="sxs-lookup"><span data-stu-id="f6906-268">Add a `Click` handler for `NewGame`.</span></span> <span data-ttu-id="f6906-269">İşleyiciyi eklemek için form için **Tasarım görünümüne** geçin ve çift tıklayın `NewGame` .</span><span class="sxs-lookup"><span data-stu-id="f6906-269">To add the handler, switch to **Design View** for the form, and double-click `NewGame`.</span></span> <span data-ttu-id="f6906-270">Bir `NewGame_Click` işleyici eklenir ve görünüm form için kod görünümüne geçer.</span><span class="sxs-lookup"><span data-stu-id="f6906-270">A `NewGame_Click` handler is added and the view switches to code view for the form.</span></span> <span data-ttu-id="f6906-271">Kullanıcı bu düğmeye her tıkladığında yeni bir iş akışı başlatılır.</span><span class="sxs-lookup"><span data-stu-id="f6906-271">Whenever the user clicks this button a new workflow is started.</span></span>

    ```vb
    Private Sub NewGame_Click(sender As Object, e As EventArgs) Handles NewGame.Click

    End Sub
    ```

    ```csharp
    private void NewGame_Click(object sender, EventArgs e)
    {

    }
    ```

2. <span data-ttu-id="f6906-272">Aşağıdaki kodu tıklama işleyicisine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f6906-272">Add the following code to the click handler.</span></span> <span data-ttu-id="f6906-273">Bu kod, iş akışı için bağımsız değişken adına göre anahtarlı bir giriş bağımsız değişkenlerinin sözlüğünü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f6906-273">This code creates a dictionary of input arguments for the workflow, keyed by argument name.</span></span> <span data-ttu-id="f6906-274">Bu sözlükte, Aralık Birleşik giriş kutusundan alınan rastgele oluşturulan sayı aralığını içeren bir giriş vardır.</span><span class="sxs-lookup"><span data-stu-id="f6906-274">This dictionary has one entry that contains the range of the randomly generated number retrieved from the range combo box.</span></span>

    ```vb
    Dim inputs As New Dictionary(Of String, Object)()
    inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem))
    ```

    ```csharp
    var inputs = new Dictionary<string, object>();
    inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem));
    ```

3. <span data-ttu-id="f6906-275">Sonra, iş akışını başlatan aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f6906-275">Next, add the following code that starts the workflow.</span></span> <span data-ttu-id="f6906-276">`WorkflowIdentity`Seçilen iş akışı türüne karşılık gelen ve iş akışı tanımı `WorkflowVersionMap` yardımcı sınıfı kullanılarak alınır.</span><span class="sxs-lookup"><span data-stu-id="f6906-276">The `WorkflowIdentity` and workflow definition corresponding to the type of workflow selected are retrieved using the `WorkflowVersionMap` helper class.</span></span> <span data-ttu-id="f6906-277">Ardından, `WorkflowApplication` iş akışı tanımı, `WorkflowIdentity` ve giriş bağımsız değişkenlerinin sözlüğü kullanılarak yeni bir örnek oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f6906-277">Next, a new `WorkflowApplication` instance is created using the workflow definition, `WorkflowIdentity`, and dictionary of input arguments.</span></span>

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

4. <span data-ttu-id="f6906-278">Sonra, iş akışını iş akışı listesine ekleyen aşağıdaki kodu ekleyin ve iş akışının sürüm bilgilerini formda görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f6906-278">Next, add the following code which adds the workflow to the workflow list and displays the workflow's version information on the form.</span></span>

    ```vb
    ' Add the workflow to the list and display the version information.
    workflowStarting = True
    InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id)
    WorkflowVersion.Text = identity.ToString()
    workflowStarting = False
    ```

    ```csharp
    // Add the workflow to the list and display the version information.
    workflowStarting = true;
    InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id);
    WorkflowVersion.Text = identity.ToString();
    workflowStarting = false;
    ```

5. <span data-ttu-id="f6906-279">`ConfigureWorkflowApplication`Örnek deposunu, uzantıları ve bu örnek için iş akışı yaşam döngüsü işleyicilerini yapılandırma çağrısı `WorkflowApplication` .</span><span class="sxs-lookup"><span data-stu-id="f6906-279">Call `ConfigureWorkflowApplication` to configure the instance store, extensions, and workflow lifecycle handlers for this `WorkflowApplication` instance.</span></span>

    ```vb
    ' Configure the instance store, extensions, and
    ' workflow lifecycle handlers.
    ConfigureWorkflowApplication(wfApp)
    ```

    ```csharp
    // Configure the instance store, extensions, and
    // workflow lifecycle handlers.
    ConfigureWorkflowApplication(wfApp);
    ```

6. <span data-ttu-id="f6906-280">Son olarak, çağırın `Run` .</span><span class="sxs-lookup"><span data-stu-id="f6906-280">Finally, call `Run`.</span></span>

    ```vb
    ' Start the workflow.
    wfApp.Run()
    ```

    ```csharp
    // Start the workflow.
    wfApp.Run();
    ```

     <span data-ttu-id="f6906-281">Aşağıdaki örnek, tamamlanan `NewGame_Click` işleyicidir.</span><span class="sxs-lookup"><span data-stu-id="f6906-281">The following example is the completed `NewGame_Click` handler.</span></span>

    ```vb
    Private Sub NewGame_Click(sender As Object, e As EventArgs) Handles NewGame.Click
        ' Start a new workflow.
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

        ' Add the workflow to the list and display the version information.
        workflowStarting = True
        InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id)
        WorkflowVersion.Text = identity.ToString()
        workflowStarting = False

        ' Configure the instance store, extensions, and
        ' workflow lifecycle handlers.
        ConfigureWorkflowApplication(wfApp)

        ' Start the workflow.
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

        var wfApp = new WorkflowApplication(wf, inputs, identity);

        // Add the workflow to the list and display the version information.
        workflowStarting = true;
        InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id);
        WorkflowVersion.Text = identity.ToString();
        workflowStarting = false;

        // Configure the instance store, extensions, and
        // workflow lifecycle handlers.
        ConfigureWorkflowApplication(wfApp);

        // Start the workflow.
        wfApp.Run();
    }
    ```

## <a name="to-resume-a-workflow"></a><span data-ttu-id="f6906-282">Bir iş akışını sürdürmesini sağlamak için</span><span class="sxs-lookup"><span data-stu-id="f6906-282">To resume a workflow</span></span>

1. <span data-ttu-id="f6906-283">İçin bir `Click` işleyici ekleyin `EnterGuess` .</span><span class="sxs-lookup"><span data-stu-id="f6906-283">Add a `Click` handler for `EnterGuess`.</span></span> <span data-ttu-id="f6906-284">İşleyiciyi eklemek için form için **Tasarım görünümüne** geçin ve çift tıklayın `EnterGuess` .</span><span class="sxs-lookup"><span data-stu-id="f6906-284">To add the handler, switch to **Design View** for the form, and double-click `EnterGuess`.</span></span> <span data-ttu-id="f6906-285">Kullanıcı bu düğmeye tıkladığında bir iş akışı sürdürülür.</span><span class="sxs-lookup"><span data-stu-id="f6906-285">Whenever the user clicks this button a workflow is resumed.</span></span>

    ```vb
    Private Sub EnterGuess_Click(sender As Object, e As EventArgs) Handles EnterGuess.Click

    End Sub
    ```

    ```csharp
    private void EnterGuess_Click(object sender, EventArgs e)
    {

    }
    ```

2. <span data-ttu-id="f6906-286">İş akışı listesinde bir iş akışının seçildiğinden ve kullanıcının tahminin geçerli olduğundan emin olmak için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f6906-286">Add the following code to ensure that a workflow is selected in the workflow list, and that the user's guess is valid.</span></span>

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

3. <span data-ttu-id="f6906-287">Sonra, `WorkflowApplicationInstance` kalıcı iş akışı örneğini alın.</span><span class="sxs-lookup"><span data-stu-id="f6906-287">Next, retrieve the `WorkflowApplicationInstance` of the persisted workflow instance.</span></span> <span data-ttu-id="f6906-288">Bir `WorkflowApplicationInstance` iş akışı tanımıyla henüz ilişkilendirilmemiş kalıcı bir iş akışı örneğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f6906-288">A `WorkflowApplicationInstance` represents a persisted workflow instance that has not yet been associated with a workflow definition.</span></span> <span data-ttu-id="f6906-289">`DefinitionIdentity`Öğesinin, `WorkflowApplicationInstance` `WorkflowIdentity` kalıcı iş akışı örneğinin içerir.</span><span class="sxs-lookup"><span data-stu-id="f6906-289">The `DefinitionIdentity` of the `WorkflowApplicationInstance` contains the `WorkflowIdentity` of the persisted workflow instance.</span></span> <span data-ttu-id="f6906-290">Bu öğreticide `WorkflowVersionMap` yardımcı program sınıfı, `WorkflowIdentity` doğru iş akışı tanımıyla eşlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f6906-290">In this tutorial, the `WorkflowVersionMap` utility class is used to map the `WorkflowIdentity` to the correct workflow definition.</span></span> <span data-ttu-id="f6906-291">İş akışı tanımı alındıktan sonra, `WorkflowApplication` doğru iş akışı tanımı kullanılarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f6906-291">Once the workflow definition is retrieved, a `WorkflowApplication` is created, using the correct workflow definition.</span></span>

    ```vb
    Dim instance As WorkflowApplicationInstance = _
        WorkflowApplication.GetInstance(WorkflowInstanceId, store)

    ' Use the persisted WorkflowIdentity to retrieve the correct workflow
    ' definition from the dictionary.
    Dim wf As Activity = _
        WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity)

    ' Associate the WorkflowApplication with the correct definition
    Dim wfApp As New WorkflowApplication(wf, instance.DefinitionIdentity)
    ```

    ```csharp
    WorkflowApplicationInstance instance =
        WorkflowApplication.GetInstance(WorkflowInstanceId, store);

    // Use the persisted WorkflowIdentity to retrieve the correct workflow
    // definition from the dictionary.
    Activity wf =
        WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity);

    // Associate the WorkflowApplication with the correct definition
    var wfApp = new WorkflowApplication(wf, instance.DefinitionIdentity);
    ```

4. <span data-ttu-id="f6906-292">Oluşturulduktan sonra `WorkflowApplication` , çağırarak örnek deposunu, iş akışı yaşam döngüsü işleyicilerini ve Uzantıları yapılandırın `ConfigureWorkflowApplication` .</span><span class="sxs-lookup"><span data-stu-id="f6906-292">Once the `WorkflowApplication` is created, configure the instance store, workflow lifecycle handlers, and extensions by calling `ConfigureWorkflowApplication`.</span></span> <span data-ttu-id="f6906-293">Bu adımların her yeni `WorkflowApplication` oluşturulduğunda yapılması ve iş akışı örneği içine yüklenmeden önce yapılması gerekir `WorkflowApplication` .</span><span class="sxs-lookup"><span data-stu-id="f6906-293">These steps must be done every time a new `WorkflowApplication` is created, and they must be done before the workflow instance is loaded into the `WorkflowApplication`.</span></span> <span data-ttu-id="f6906-294">İş akışı yüklendikten sonra kullanıcının tahminiyle devam edilir.</span><span class="sxs-lookup"><span data-stu-id="f6906-294">After the workflow is loaded, it is resumed with the user's guess.</span></span>

    ```vb
    ' Configure the extensions and lifecycle handlers.
    ' Do this before the instance is loaded. Once the instance is
    ' loaded it is too late to add extensions.
    ConfigureWorkflowApplication(wfApp)

    ' Load the workflow.
    wfApp.Load(instance)

    ' Resume the workflow.
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

5. <span data-ttu-id="f6906-295">Son olarak, tahmin metin kutusunu temizleyip formu başka bir tahmin kabul edecek şekilde hazırlayın.</span><span class="sxs-lookup"><span data-stu-id="f6906-295">Finally, clear the guess textbox and prepare the form to accept another guess.</span></span>

    ```vb
    ' Clear the Guess textbox.
    Guess.Clear()
    Guess.Focus()
    ```

    ```csharp
    // Clear the Guess textbox.
    Guess.Clear();
    Guess.Focus();
    ```

    <span data-ttu-id="f6906-296">Aşağıdaki örnek, tamamlanan `EnterGuess_Click` işleyicidir.</span><span class="sxs-lookup"><span data-stu-id="f6906-296">The following example is the completed `EnterGuess_Click` handler.</span></span>

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

        ' Use the persisted WorkflowIdentity to retrieve the correct workflow
        ' definition from the dictionary.
        Dim wf As Activity = _
            WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity)

        ' Associate the WorkflowApplication with the correct definition
        Dim wfApp As New WorkflowApplication(wf, instance.DefinitionIdentity)

        ' Configure the extensions and lifecycle handlers.
        ' Do this before the instance is loaded. Once the instance is
        ' loaded it is too late to add extensions.
        ConfigureWorkflowApplication(wfApp)

        ' Load the workflow.
        wfApp.Load(instance)

        ' Resume the workflow.
        wfApp.ResumeBookmark("EnterGuess", userGuess)

        ' Clear the Guess textbox.
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
        var wfApp = new WorkflowApplication(wf, instance.DefinitionIdentity);

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

## <a name="to-terminate-a-workflow"></a><span data-ttu-id="f6906-297">Bir iş akışını sonlandırmak için</span><span class="sxs-lookup"><span data-stu-id="f6906-297">To terminate a workflow</span></span>

1. <span data-ttu-id="f6906-298">İçin bir `Click` işleyici ekleyin `QuitGame` .</span><span class="sxs-lookup"><span data-stu-id="f6906-298">Add a `Click` handler for `QuitGame`.</span></span> <span data-ttu-id="f6906-299">İşleyiciyi eklemek için form için **Tasarım görünümüne** geçin ve çift tıklayın `QuitGame` .</span><span class="sxs-lookup"><span data-stu-id="f6906-299">To add the handler, switch to **Design View** for the form, and double-click `QuitGame`.</span></span> <span data-ttu-id="f6906-300">Kullanıcı bu düğmeye tıkladığında Şu anda seçili olan iş akışı sonlandırılır.</span><span class="sxs-lookup"><span data-stu-id="f6906-300">Whenever the user clicks this button the currently selected workflow is terminated.</span></span>

    ```vb
    Private Sub QuitGame_Click(sender As Object, e As EventArgs) Handles QuitGame.Click

    End Sub
    ```

    ```csharp
    private void QuitGame_Click(object sender, EventArgs e)
    {

    }
    ```

2. <span data-ttu-id="f6906-301">Aşağıdaki kodu `QuitGame_Click` işleyiciye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f6906-301">Add the following code to the `QuitGame_Click` handler.</span></span> <span data-ttu-id="f6906-302">Bu kod ilk olarak iş akışı listesinde bir iş akışının seçili olduğundan emin olmak için kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="f6906-302">This code first checks to ensure that a workflow is selected in the workflow list.</span></span> <span data-ttu-id="f6906-303">Ardından kalıcı örneği öğesine yükler `WorkflowApplicationInstance` , `DefinitionIdentity` doğru iş akışı tanımını anlamak için öğesini kullanır ve sonra öğesini başlatır `WorkflowApplication` .</span><span class="sxs-lookup"><span data-stu-id="f6906-303">Then it loads the persisted instance into a `WorkflowApplicationInstance`, uses the `DefinitionIdentity` to determine the correct workflow definition, and then initializes the `WorkflowApplication`.</span></span> <span data-ttu-id="f6906-304">Sonraki Uzantılar ve iş akışı yaşam döngüsü işleyicileri bir çağrısıyla yapılandırılır `ConfigureWorkflowApplication` .</span><span class="sxs-lookup"><span data-stu-id="f6906-304">Next the extensions and workflow lifecycle handlers are configured with a call to `ConfigureWorkflowApplication`.</span></span> <span data-ttu-id="f6906-305">Yapılandırıldıktan sonra, `WorkflowApplication` yüklenir ve ardından `Terminate` çağırılır.</span><span class="sxs-lookup"><span data-stu-id="f6906-305">Once the `WorkflowApplication` is configured, it is loaded, and then `Terminate` is called.</span></span>

    ```vb
    If WorkflowInstanceId = Guid.Empty Then
        MessageBox.Show("Please select a workflow.")
        Return
    End If

    Dim instance As WorkflowApplicationInstance = _
        WorkflowApplication.GetInstance(WorkflowInstanceId, store)

    ' Use the persisted WorkflowIdentity to retrieve the correct workflow
    ' definition from the dictionary.
    Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity)

    ' Associate the WorkflowApplication with the correct definition.
    Dim wfApp As New WorkflowApplication(wf, instance.DefinitionIdentity)

    ' Configure the extensions and lifecycle handlers.
    ConfigureWorkflowApplication(wfApp)

    ' Load the workflow.
    wfApp.Load(instance)

    ' Terminate the workflow.
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
    var wfApp = new WorkflowApplication(wf, instance.DefinitionIdentity);

    // Configure the extensions and lifecycle handlers
    ConfigureWorkflowApplication(wfApp);

    // Load the workflow.
    wfApp.Load(instance);

    // Terminate the workflow.
    wfApp.Terminate("User resigns.");
    ```

## <a name="to-build-and-run-the-application"></a><span data-ttu-id="f6906-306">Uygulamayı derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="f6906-306">To build and run the application</span></span>

1. <span data-ttu-id="f6906-307">Kodu göstermek için **Çözüm Gezgini** içindeki **program.cs** (veya **Module1. vb**) öğesine çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f6906-307">Double-click **Program.cs** (or **Module1.vb**) in **Solution Explorer** to display the code.</span></span>

2. <span data-ttu-id="f6906-308">Aşağıdaki `using` (veya `Imports` ) deyimini, diğer `using` (veya `Imports` ) deyimleriyle dosyanın en üstüne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f6906-308">Add the following `using` (or `Imports`) statement at the top of the file with the other `using` (or `Imports`) statements.</span></span>

    ```vb
    Imports System.Windows.Forms
    ```

    ```csharp
    using System.Windows.Forms;
    ```

3. <span data-ttu-id="f6906-309">[Nasıl yapılır: Iş akışı çalıştırma](how-to-run-a-workflow.md)ve aşağıdaki kodla değiştirme gibi mevcut iş akışı barındırma kodunu kaldırın</span><span class="sxs-lookup"><span data-stu-id="f6906-309">Remove or comment out the existing workflow hosting code from [How to: Run a Workflow](how-to-run-a-workflow.md), and replace it with the following code.</span></span>

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

4. <span data-ttu-id="f6906-310">**Çözüm Gezgini** Için **Numberguessworkflowwhost** öğesine sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="f6906-310">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Properties**.</span></span> <span data-ttu-id="f6906-311">**Uygulama** sekmesinde, **Çıkış türü** için **Windows uygulaması** ' nı belirtin.</span><span class="sxs-lookup"><span data-stu-id="f6906-311">In the **Application** tab, specify **Windows Application** for the **Output type**.</span></span> <span data-ttu-id="f6906-312">Bu adım isteğe bağlıdır, ancak bu değer izlenmezse, forma ek olarak konsol penceresi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f6906-312">This step is optional, but if it is not followed the console window is displayed in addition to the form.</span></span>

5. <span data-ttu-id="f6906-313">Uygulamayı derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="f6906-313">Press Ctrl+Shift+B to build the application.</span></span>

6. <span data-ttu-id="f6906-314">**Numberguessworkflowwhost** ' nin başlangıç uygulaması olarak ayarlandığından emin olun ve uygulamayı başlatmak için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="f6906-314">Ensure that **NumberGuessWorkflowHost** is set as the startup application, and press Ctrl+F5 to start the application.</span></span>

7. <span data-ttu-id="f6906-315">Tahmin etme oyunu ve başlatılacak iş akışı türü için bir Aralık seçin ve **yeni oyun**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f6906-315">Select a range for the guessing game and the type of workflow to start, and click **New Game**.</span></span> <span data-ttu-id="f6906-316">**Tahmin kutusuna bir** tahmin girin ve tahmininizi göndermek için **Git** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f6906-316">Enter a guess in the **Guess** box and click **Go** to submit your guess.</span></span> <span data-ttu-id="f6906-317">`WriteLine`Etkinliklerdeki çıktının formda görüntülendiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f6906-317">Note that the output from the `WriteLine` activities is displayed on the form.</span></span>

8. <span data-ttu-id="f6906-318">Farklı iş akışı türleri ve sayı aralıkları kullanarak birkaç iş akışı başlatın, bazı tahminler girin ve **Iş akışı örneği kimliği** listesinden seçim yaparak iş akışları arasında geçiş yapın.</span><span class="sxs-lookup"><span data-stu-id="f6906-318">Start several workflows using different workflow types and number ranges, enter some guesses, and switch between the workflows by selecting from the **Workflow Instance Id** list.</span></span>

    <span data-ttu-id="f6906-319">Yeni bir iş akışına geçtiğinizde, iş akışının önceki tahminlerini ve ilerleme durumu durum penceresinde görüntülenmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f6906-319">Note that when you switch to a new workflow, the previous guesses and progress of the workflow are not displayed in the status window.</span></span> <span data-ttu-id="f6906-320">Durumun, yakalanmadığı ve her yerde kaydedilmediği için durum kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="f6906-320">The reason the status is not available is because it is not captured and saved anywhere.</span></span> <span data-ttu-id="f6906-321">Öğreticinin bir sonraki adımında, [nasıl yapılır: özel bir Izleme katılımcısı oluşturma](how-to-create-a-custom-tracking-participant.md), bu bilgileri kaydeden özel bir izleme katılımcısı oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="f6906-321">In the next step of the tutorial, [How to: Create a Custom Tracking Participant](how-to-create-a-custom-tracking-participant.md), you create a custom tracking participant that saves this information.</span></span>
