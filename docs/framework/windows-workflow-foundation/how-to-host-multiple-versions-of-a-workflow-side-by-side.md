---
title: 'Nasıl yapılır: İş Akışının Birden Fazla Sürümünü Yan Yana Barındırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 09c575df-e0a3-4f3b-9e01-a7ac59d65287
ms.openlocfilehash: 061a8c7b73903b763de27e614e9b3067777afe58
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64756020"
---
# <a name="how-to-host-multiple-versions-of-a-workflow-side-by-side"></a><span data-ttu-id="cc0a1-102">Nasıl yapılır: İş Akışının Birden Fazla Sürümünü Yan Yana Barındırma</span><span class="sxs-lookup"><span data-stu-id="cc0a1-102">How to: Host Multiple Versions of a Workflow Side-by-Side</span></span>

<span data-ttu-id="cc0a1-103">`WorkflowIdentity` Bu bilgiler bir kalıcı iş akışı örneğiyle ilişkili olmasını yanı sıra, bir adı ve sürümü, bir iş akışı tanımıyla ilişkilendirilecek iş akışı uygulama geliştiricileri için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-103">`WorkflowIdentity` provides a way for workflow application developers to associate a name and a version with a workflow definition, and for this information to be associated with a persisted workflow instance.</span></span> <span data-ttu-id="cc0a1-104">Bu kimlik bilgileri birden çok iş akışı tanımı sürümünün yan yana yürütme gibi senaryoları etkinleştirmek için iş akışı uygulama geliştiricileri tarafından kullanılabilir ve dinamik güncelleştirme gibi diğer işlevleri için temel sağlar.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-104">This identity information can be used by workflow application developers to enable scenarios such as side-by-side execution of multiple versions of a workflow definition, and provides the cornerstone for other functionality such as dynamic update.</span></span> <span data-ttu-id="cc0a1-105">Bu adım öğreticide nasıl kullanılacağını gösteren `WorkflowIdentity` aynı anda birden çok iş akışı sürümünü barındırmak için.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-105">This step in the tutorial demonstrates how to use `WorkflowIdentity` to host multiple versions of a workflow at the same time.</span></span>

> [!NOTE]
> <span data-ttu-id="cc0a1-106">Tamamlanmış bir sürümünü indirin veya videosu öğreticinin görüntülemek için bkz: [Windows Workflow Foundation (WF45) - başlangıç Öğreticisi](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="cc0a1-106">To download a completed version or view a video walkthrough of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>

## <a name="in-this-topic"></a><span data-ttu-id="cc0a1-107">Bu konuda</span><span class="sxs-lookup"><span data-stu-id="cc0a1-107">In this topic</span></span>

<span data-ttu-id="cc0a1-108">Öğreticinin bu adımında `WriteLine` ek bilgiler ve yeni bir iş akışındaki etkinlikler değiştirildiğinde `WriteLine` etkinlik eklenir.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-108">In this step of the tutorial, the `WriteLine` activities in the workflow are modified to provide additional information, and a new `WriteLine` activity is added.</span></span> <span data-ttu-id="cc0a1-109">Özgün iş akışı derleme kopyası depolanır ve aynı anda hem özgün hem de güncelleştirilmiş iş akışı çalışması için ana bilgisayar uygulaması güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-109">A copy of the original workflow assembly is stored, and the host application is updated so that it can run both the original and the updated workflows at the same time.</span></span>

- [<span data-ttu-id="cc0a1-110">NumberGuessWorkflowActivities projenin bir kopyasını oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="cc0a1-110">To make a copy of the NumberGuessWorkflowActivities project</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_BackupCopy)

- [<span data-ttu-id="cc0a1-111">İş akışları güncelleştirmek için</span><span class="sxs-lookup"><span data-stu-id="cc0a1-111">To update the workflows</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateWorkflows)

    - [<span data-ttu-id="cc0a1-112">Durum makinesi iş akışını güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="cc0a1-112">To update the StateMachine workflow</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateStateMachine)

    - [<span data-ttu-id="cc0a1-113">Akış Çizelgesi iş akışını güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="cc0a1-113">To update the Flowchart workflow</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateFlowchart)

    - [<span data-ttu-id="cc0a1-114">Sıralı iş akışını güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="cc0a1-114">To update the Sequential workflow</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateSequential)

- [<span data-ttu-id="cc0a1-115">Önceki iş akışı sürümünün içerecek şekilde WorkflowVersionMap güncelleştirmek için</span><span class="sxs-lookup"><span data-stu-id="cc0a1-115">To update WorkflowVersionMap to include the previous workflow versions</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateWorkflowVersionMap)

- [<span data-ttu-id="cc0a1-116">Derleme ve uygulamayı çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="cc0a1-116">To build and run the application</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_BuildAndRun)

> [!NOTE]
> <span data-ttu-id="cc0a1-117">Bu konu başlığındaki adımları uygulayarak önce uygulamayı çalıştırmak, her türden çeşitli iş akışlarını başlatmak ve her biri için bir veya iki tahmin yapma.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-117">Before following the steps in this topic, run the application, start several workflows of each type, and making one or two guesses for each one.</span></span> <span data-ttu-id="cc0a1-118">Bu adım ve aşağıdaki adımı kalıcı bu iş akışları kullanılan [nasıl yapılır: Bir çalışan iş akışı örneğinin tanımını güncelleştirme](how-to-update-the-definition-of-a-running-workflow-instance.md).</span><span class="sxs-lookup"><span data-stu-id="cc0a1-118">These persisted workflows are used in this step and the following step, [How to: Update the Definition of a Running Workflow Instance](how-to-update-the-definition-of-a-running-workflow-instance.md).</span></span>

> [!NOTE]
> <span data-ttu-id="cc0a1-119">Başlarken Öğreticisi her adımda, önceki adımları bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-119">Each step in the Getting Started tutorial depends on the previous steps.</span></span> <span data-ttu-id="cc0a1-120">Önceki adımları tamamlanmadıysa öğreticinin tamamlanmış bir sürümünü indirebilirsiniz [Windows Workflow Foundation (WF45) - başlangıç Öğreticisi](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="cc0a1-120">If you did not complete the previous steps you can download a completed version of the tutorial from [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>

### <a name="BKMK_BackupCopy"></a> <span data-ttu-id="cc0a1-121">NumberGuessWorkflowActivities projenin bir kopyasını oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="cc0a1-121">To make a copy of the NumberGuessWorkflowActivities project</span></span>

1. <span data-ttu-id="cc0a1-122">Açık **WF45GettingStartedTutorial** çözüm açık değilse Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-122">Open the **WF45GettingStartedTutorial** solution in Visual Studio 2012 if it is not open.</span></span>

2. <span data-ttu-id="cc0a1-123">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-123">Press CTRL+SHIFT+B to build the solution.</span></span>

3. <span data-ttu-id="cc0a1-124">Kapat **WF45GettingStartedTutorial** çözüm.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-124">Close the **WF45GettingStartedTutorial** solution.</span></span>

4. <span data-ttu-id="cc0a1-125">Windows Gezgini'ni açın ve öğretici çözüm dosyası ve proje klasörleri bulunduğu klasöre gidin.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-125">Open Windows Explorer and navigate to the folder where the tutorial solution file and the project folders are located.</span></span>

5. <span data-ttu-id="cc0a1-126">Adlı yeni bir klasör oluşturun **PreviousVersions** aynı klasörde **NumberGuessWorkflowHost** ve **NumberGuessWorkflowActivities**.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-126">Create a new folder named **PreviousVersions** in the same folder as **NumberGuessWorkflowHost** and **NumberGuessWorkflowActivities**.</span></span> <span data-ttu-id="cc0a1-127">Bu klasör, sonraki öğretici adımlarda kullanılan iş akışları farklı sürümlerini içeren derlemeler kapsamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-127">This folder is used to contain the assemblies that contain the different versions of the workflows used in the subsequent tutorial steps.</span></span>

6. <span data-ttu-id="cc0a1-128">Gidin **NumberGuessWorkflowActivities\bin\debug** klasörü (veya **bin\release** proje ayarlarınıza bağlı olarak).</span><span class="sxs-lookup"><span data-stu-id="cc0a1-128">Navigate to the **NumberGuessWorkflowActivities\bin\debug** folder (or **bin\release** depending on your project settings).</span></span> <span data-ttu-id="cc0a1-129">Kopyalama **NumberGuessWorkflowActivities.dll** yapıştırın **PreviousVersions** klasör.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-129">Copy **NumberGuessWorkflowActivities.dll** and paste it into the **PreviousVersions** folder.</span></span>

7. <span data-ttu-id="cc0a1-130">Yeniden adlandırma **NumberGuessWorkflowActivities.dll** içinde **PreviousVersions** klasörüne **NumberGuessWorkflowActivities_v1.dll**.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-130">Rename **NumberGuessWorkflowActivities.dll** in the **PreviousVersions** folder to **NumberGuessWorkflowActivities_v1.dll**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="cc0a1-131">Bu konu başlığındaki adımları iş akışları birden çok sürümünü kapsamak için kullanılmış olan derlemeleri yönetmek için bir yol gösterir.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-131">The steps in this topic demonstrate one way to manage the assemblies used to contain multiple versions of the workflows.</span></span> <span data-ttu-id="cc0a1-132">Güçlü derlemelerini adlandırma ve bunları genel derleme önbelleğinde kaydetme gibi diğer yöntemleri de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-132">Other methods such as strong naming the assemblies and registering them in the global assembly cache could also be used.</span></span>

8. <span data-ttu-id="cc0a1-133">Adlı yeni bir klasör oluşturun **NumberGuessWorkflowActivities_du** aynı klasörde **NumberGuessWorkflowHost**, **NumberGuessWorkflowActivities**ve yeni eklenen **PreviousVersions** klasörünü ve tüm dosyaları ve alt klasörlerdeki kopyalayın **NumberGuessWorkflowActivities** yeni klasöre  **NumberGuessWorkflowActivities_du** klasör.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-133">Create a new folder named **NumberGuessWorkflowActivities_du** in the same folder as **NumberGuessWorkflowHost**, **NumberGuessWorkflowActivities**, and the newly added **PreviousVersions** folder, and copy all of the files and subfolders from the **NumberGuessWorkflowActivities** folder into the new **NumberGuessWorkflowActivities_du** folder.</span></span> <span data-ttu-id="cc0a1-134">Bu yedekleme kopyası proje etkinliklerinin ilk sürümü için kullanılan [nasıl yapılır: Bir çalışan iş akışı örneğinin tanımını güncelleştirme](how-to-update-the-definition-of-a-running-workflow-instance.md).</span><span class="sxs-lookup"><span data-stu-id="cc0a1-134">This backup copy of the project for the initial version of the activities is used in [How to: Update the Definition of a Running Workflow Instance](how-to-update-the-definition-of-a-running-workflow-instance.md).</span></span>

9. <span data-ttu-id="cc0a1-135">Yeniden açın **WF45GettingStartedTutorial** çözümü Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-135">Re-open the **WF45GettingStartedTutorial** solution in Visual Studio 2012.</span></span>

### <a name="BKMK_UpdateWorkflows"></a> <span data-ttu-id="cc0a1-136">İş akışları güncelleştirmek için</span><span class="sxs-lookup"><span data-stu-id="cc0a1-136">To update the workflows</span></span>

 <span data-ttu-id="cc0a1-137">Bu bölümde, iş akışı tanımları güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-137">In this section, the workflow definitions are updated.</span></span> <span data-ttu-id="cc0a1-138">İki `WriteLine` güncelleştirilmiş ve yeni bir kullanıcının tahmin geri bildirimde bulunun etkinlikleri `WriteLine` etkinlik sayısını tahmin sonra oyun hakkında ek bilgi sağlayan eklenir.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-138">The two `WriteLine` activities that give feedback on the user's guess are updated, and a new `WriteLine` activity is added that provides additional information about the game once the number is guessed.</span></span>

#### <a name="BKMK_UpdateStateMachine"></a> <span data-ttu-id="cc0a1-139">Durum makinesi iş akışını güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="cc0a1-139">To update the StateMachine workflow</span></span>

1. <span data-ttu-id="cc0a1-140">İçinde **Çözüm Gezgini**altında **NumberGuessWorkflowActivities** proje, çift **StateMachineNumberGuessWorkflow.xaml**.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-140">In **Solution Explorer**, under the **NumberGuessWorkflowActivities** project, double-click **StateMachineNumberGuessWorkflow.xaml**.</span></span>

2. <span data-ttu-id="cc0a1-141">Çift **yanlış tahmin** durum makinesinin geçişi.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-141">Double-click the **Guess Incorrect** transition on the state machine.</span></span>

3. <span data-ttu-id="cc0a1-142">Güncelleştirme `Text` en sol `WriteLine` içinde `If` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-142">Update the `Text` of the left-most `WriteLine` in the `If` activity.</span></span>

    ```vb
    Guess & " is too low."
    ```

    ```csharp
    Guess + " is too low."
    ```

4. <span data-ttu-id="cc0a1-143">Güncelleştirme `Text` en sağ `WriteLine` içinde `If` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-143">Update the `Text` of the right-most `WriteLine` in the `If` activity.</span></span>

    ```vb
    Guess & " is too high."
    ```

    ```csharp
    Guess + " is too high."
    ```

5. <span data-ttu-id="cc0a1-144">İade için genel durum makinesi iş akışı Tasarımcısı görünümünde tıklayarak **StateMachine** alan içerik haritasındaki iş akışı Tasarımcısı üst kısmında görüntüler.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-144">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>

6. <span data-ttu-id="cc0a1-145">Çift **doğru tahmin** durum makinesinin geçişi.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-145">Double-click the **Guess Correct** transition on the state machine.</span></span>

7. <span data-ttu-id="cc0a1-146">Sürükleme bir **WriteLine** etkinliğinden **Temelleri** bölümünü **araç kutusu** ve bırakın **Buraya Bırak eylem etkinliği** etiketi geçiş.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-146">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it on the **Drop Action activity here** label of the transition.</span></span>

8. <span data-ttu-id="cc0a1-147">İçine aşağıdaki ifadeyi yazın `Text` özellik kutusu.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-147">Type the following expression into the `Text` property box.</span></span>

    ```vb
    Guess & " is correct. You guessed it in " & Turns & " turns."
    ```

    ```csharp
    Guess + " is correct. You guessed it in " + Turns + " turns."
    ```

#### <a name="BKMK_UpdateFlowchart"></a> <span data-ttu-id="cc0a1-148">Akış Çizelgesi iş akışını güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="cc0a1-148">To update the Flowchart workflow</span></span>

1. <span data-ttu-id="cc0a1-149">İçinde **Çözüm Gezgini**altında **NumberGuessWorkflowActivities** proje, çift **FlowchartNumberGuessWorkflow.xaml**.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-149">In **Solution Explorer**, under the **NumberGuessWorkflowActivities** project, double-click **FlowchartNumberGuessWorkflow.xaml**.</span></span>

2. <span data-ttu-id="cc0a1-150">Güncelleştirme `Text` en sol `WriteLine` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-150">Update the `Text` of the left-most `WriteLine` activity.</span></span>

    ```vb
    Guess & " is too low."
    ```

    ```csharp
    Guess + " is too low."
    ```

3. <span data-ttu-id="cc0a1-151">Güncelleştirme `Text` en sağ `WriteLine` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-151">Update the `Text` of the right-most `WriteLine` activity.</span></span>

    ```vb
    Guess & " is too high."
    ```

    ```csharp
    Guess + " is too high."
    ```

4. <span data-ttu-id="cc0a1-152">Sürükleme bir **WriteLine** etkinliğinden **Temelleri** bölümünü **araç kutusu** sürükleyip bırakma noktasına `True` eylemi üstteki `FlowDecision` .</span><span class="sxs-lookup"><span data-stu-id="cc0a1-152">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it on the drop point of the `True` action of the topmost `FlowDecision`.</span></span> <span data-ttu-id="cc0a1-153">`WriteLine` Etkinliği için akış eklenir ve bağlantılı `True` eylemi `FlowDecision`.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-153">The `WriteLine` activity is added to the flowchart and linked to the `True` action of the `FlowDecision`.</span></span>

5. <span data-ttu-id="cc0a1-154">İçine aşağıdaki ifadeyi yazın `Text` özellik kutusu.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-154">Type the following expression into the `Text` property box.</span></span>

    ```vb
    Guess & " is correct. You guessed it in " & Turns & " turns."
    ```

    ```csharp
    Guess + " is correct. You guessed it in " + Turns + " turns."
    ```

#### <a name="BKMK_UpdateSequential"></a> <span data-ttu-id="cc0a1-155">Sıralı iş akışını güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="cc0a1-155">To update the Sequential workflow</span></span>

1. <span data-ttu-id="cc0a1-156">İçinde **Çözüm Gezgini**altında **NumberGuessWorkflowActivities** proje, çift **SequentialNumberGuessWorkflow.xaml**.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-156">In **Solution Explorer**, under the **NumberGuessWorkflowActivities** project, double-click **SequentialNumberGuessWorkflow.xaml**.</span></span>

2. <span data-ttu-id="cc0a1-157">Güncelleştirme `Text` en sol `WriteLine` içinde `If` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-157">Update the `Text` of the left-most `WriteLine` in the `If` activity.</span></span>

    ```vb
    Guess & " is too low."
    ```

    ```csharp
    Guess + " is too low."
    ```

3. <span data-ttu-id="cc0a1-158">Güncelleştirme `Text` en sağ `WriteLine` etkinliğinde `If` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-158">Update the `Text` of the right-most `WriteLine` activity in the `If` activity.</span></span>

    ```vb
    Guess & " is too high."
    ```

    ```csharp
    Guess + " is too high."
    ```

4. <span data-ttu-id="cc0a1-159">Sürükleme bir **WriteLine** etkinliğinden **Temelleri** bölümünü **araç kutusu** ve bundan sonra açılan **DoWhile** etkinlik böylece  **WriteLine** kök son etkinlik olduğu `Sequence` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-159">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it after the **DoWhile** activity so that the **WriteLine** is the final activity in the root `Sequence` activity.</span></span>

5. <span data-ttu-id="cc0a1-160">İçine aşağıdaki ifadeyi yazın `Text` özellik kutusu.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-160">Type the following expression into the `Text` property box.</span></span>

    ```vb
    Guess & " is correct. You guessed it in " & Turns & " turns."
    ```

    ```csharp
    Guess + " is correct. You guessed it in " + Turns + " turns."
    ```

### <a name="BKMK_UpdateWorkflowVersionMap"></a> <span data-ttu-id="cc0a1-161">Önceki iş akışı sürümünün içerecek şekilde WorkflowVersionMap güncelleştirmek için</span><span class="sxs-lookup"><span data-stu-id="cc0a1-161">To update WorkflowVersionMap to include the previous workflow versions</span></span>

1. <span data-ttu-id="cc0a1-162">Çift **WorkflowVersionMap.cs** (veya **WorkflowVersionMap.vb**) altında **NumberGuessWorkflowHost** açmak için proje.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-162">Double-click **WorkflowVersionMap.cs** (or **WorkflowVersionMap.vb**) under the **NumberGuessWorkflowHost** project to open it.</span></span>

2. <span data-ttu-id="cc0a1-163">Aşağıdaki `using` (veya `Imports`) diğer dosyasının en `using` (veya `Imports`) ifadeleri.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-163">Add the following `using` (or `Imports`) statements to the top of the file with the other `using` (or `Imports`) statements.</span></span>

    ```vb
    Imports System.Reflection
    Imports System.IO
    ```

    ```csharp
    using System.Reflection;
    using System.IO;
    ```

3. <span data-ttu-id="cc0a1-164">Üç mevcut iş akışı kimlik bildirimlerine hemen altına üç yeni iş akışı kimliklerini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-164">Add three new workflow identities just below the three existing workflow identity declarations.</span></span> <span data-ttu-id="cc0a1-165">Bu yeni `v1` kimlikleri kullanılabilir iş akışı güncelleştirmeleri yapılmadan önce başlatılan iş akışları için doğru iş akışı tanımı belirtin.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-165">These new `v1` workflow identities will be used provide the correct workflow definition to workflows started before the updates were made.</span></span>

    ```vb
    'Current version identities.
    Public StateMachineNumberGuessIdentity As WorkflowIdentity
    Public FlowchartNumberGuessIdentity As WorkflowIdentity
    Public SequentialNumberGuessIdentity As WorkflowIdentity

    'v1 Identities.
    Public StateMachineNumberGuessIdentity_v1 As WorkflowIdentity
    Public FlowchartNumberGuessIdentity_v1 As WorkflowIdentity
    Public SequentialNumberGuessIdentity_v1 As WorkflowIdentity
    ```

    ```csharp
    // Current version identities.
    static public WorkflowIdentity StateMachineNumberGuessIdentity;
    static public WorkflowIdentity FlowchartNumberGuessIdentity;
    static public WorkflowIdentity SequentialNumberGuessIdentity;

    // v1 identities.
    static public WorkflowIdentity StateMachineNumberGuessIdentity_v1;
    static public WorkflowIdentity FlowchartNumberGuessIdentity_v1;
    static public WorkflowIdentity SequentialNumberGuessIdentity_v1;
    ```

4. <span data-ttu-id="cc0a1-166">İçinde `WorkflowVersionMap` oluşturucusu, güncelleştirme `Version` üç geçerli iş akışı kimlikleri özelliği `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-166">In the `WorkflowVersionMap` constructor, update the `Version` property of the three current workflow identities to `2.0.0.0`.</span></span>

    ```vb
    'Add the current workflow version identities.
    StateMachineNumberGuessIdentity = New WorkflowIdentity With
    {
        .Name = "StateMachineNumberGuessWorkflow",
        .Version = New Version(2, 0, 0, 0)
    }

    FlowchartNumberGuessIdentity = New WorkflowIdentity With
    {
        .Name = "FlowchartNumberGuessWorkflow",
        .Version = New Version(2, 0, 0, 0)
    }

    SequentialNumberGuessIdentity = New WorkflowIdentity With
    {
        .Name = "SequentialNumberGuessWorkflow",
        .Version = New Version(2, 0, 0, 0)
    }

    map.Add(StateMachineNumberGuessIdentity, New StateMachineNumberGuessWorkflow())
    map.Add(FlowchartNumberGuessIdentity, New FlowchartNumberGuessWorkflow())
    map.Add(SequentialNumberGuessIdentity, New SequentialNumberGuessWorkflow())
    ```

    ```csharp
    // Add the current workflow version identities.
    StateMachineNumberGuessIdentity = new WorkflowIdentity
    {
        Name = "StateMachineNumberGuessWorkflow",
        // Version = new Version(1, 0, 0, 0),
        Version = new Version(2, 0, 0, 0)
    };

    FlowchartNumberGuessIdentity = new WorkflowIdentity
    {
        Name = "FlowchartNumberGuessWorkflow",
        // Version = new Version(1, 0, 0, 0),
        Version = new Version(2, 0, 0, 0)
    };

    SequentialNumberGuessIdentity = new WorkflowIdentity
    {
        Name = "SequentialNumberGuessWorkflow",
        // Version = new Version(1, 0, 0, 0),
        Version = new Version(2, 0, 0, 0)
    };

    map.Add(StateMachineNumberGuessIdentity, new StateMachineNumberGuessWorkflow());
    map.Add(FlowchartNumberGuessIdentity, new FlowchartNumberGuessWorkflow());
    map.Add(SequentialNumberGuessIdentity, new SequentialNumberGuessWorkflow());
    ```

    <span data-ttu-id="cc0a1-167">İş akışları sözlüğüne geçerli sürümleri kullanan iş akışı tanımları başlatan kodu güncelleştirilmesi gerekmez, projenizde başvurulan geçerli sürümleri, kodu ekler.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-167">The code in that adds the current versions of the workflows to the dictionary uses the current versions that are referenced in the project, so the code that initializes the workflow definitions does not need to be updated.</span></span>

5. <span data-ttu-id="cc0a1-168">Aşağıdaki kod oluşturucuda geçerli sürümler sözlüğe ekler koddan sonra ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-168">Add the following code in the constructor just after the code that adds the current versions to the dictionary.</span></span>

    ```vb
    'Initialize the previous workflow version identities.
    StateMachineNumberGuessIdentity_v1 = New WorkflowIdentity With
    {
        .Name = "StateMachineNumberGuessWorkflow",
        .Version = New Version(1, 0, 0, 0)
    }

    FlowchartNumberGuessIdentity_v1 = New WorkflowIdentity With
    {
        .Name = "FlowchartNumberGuessWorkflow",
        .Version = New Version(1, 0, 0, 0)
    }

    SequentialNumberGuessIdentity_v1 = New WorkflowIdentity With
    {
        .Name = "SequentialNumberGuessWorkflow",
        .Version = New Version(1, 0, 0, 0)
    }
    ```

    ```csharp
    // Initialize the previous workflow version identities.
    StateMachineNumberGuessIdentity_v1 = new WorkflowIdentity
    {
        Name = "StateMachineNumberGuessWorkflow",
        Version = new Version(1, 0, 0, 0)
    };

    FlowchartNumberGuessIdentity_v1 = new WorkflowIdentity
    {
        Name = "FlowchartNumberGuessWorkflow",
        Version = new Version(1, 0, 0, 0)
    };

    SequentialNumberGuessIdentity_v1 = new WorkflowIdentity
    {
        Name = "SequentialNumberGuessWorkflow",
        Version = new Version(1, 0, 0, 0)
    };
    ```

    <span data-ttu-id="cc0a1-169">Bu iş akışı kimlikleri, karşılık gelen iş akışı tanımları ilk sürümleri ile ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-169">These workflow identities are associated with the initial versions of the corresponding workflow definitions.</span></span>

6. <span data-ttu-id="cc0a1-170">Ardından, iş akışı tanımları'nin ilk sürümünden içeren derlemeyi yüklemek ve oluşturun ve karşılık gelen iş akışı tanımları sözlüğüne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-170">Next, load the assembly that contains the initial version of the workflow definitions, and create and add the corresponding workflow definitions to the dictionary.</span></span>

    ```vb
    'Add the previous version workflow identities to the dictionary along with
    'the corresponding workflow definitions loaded from the v1 assembly.
    'Assembly.LoadFile requires an absolute path so convert this relative path
    'to an absolute path.
    Dim v1AssemblyPath As String = "..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll"
    v1AssemblyPath = Path.GetFullPath(v1AssemblyPath)
    Dim v1Assembly As Assembly = Assembly.LoadFile(v1AssemblyPath)

    map.Add(StateMachineNumberGuessIdentity_v1,
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow"))

    map.Add(SequentialNumberGuessIdentity_v1,
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow"))

    map.Add(FlowchartNumberGuessIdentity_v1,
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow"))
    ```

    ```csharp
    // Add the previous version workflow identities to the dictionary along with
    // the corresponding workflow definitions loaded from the v1 assembly.
    // Assembly.LoadFile requires an absolute path so convert this relative path
    // to an absolute path.
    string v1AssemblyPath = @"..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll";
    v1AssemblyPath = Path.GetFullPath(v1AssemblyPath);
    Assembly v1Assembly = Assembly.LoadFile(v1AssemblyPath);

    map.Add(StateMachineNumberGuessIdentity_v1,
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow") as Activity);

    map.Add(SequentialNumberGuessIdentity_v1,
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow") as Activity);

    map.Add(FlowchartNumberGuessIdentity_v1,
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow") as Activity);
    ```

    <span data-ttu-id="cc0a1-171">Aşağıdaki örnek, tam listesi için güncelleştirilmiş `WorkflowVersionMap` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-171">The following example is the complete listing for the updated `WorkflowVersionMap` class.</span></span>

    ```vb
    Public Module WorkflowVersionMap
        Dim map As Dictionary(Of WorkflowIdentity, Activity)

        'Current version identities.
        Public StateMachineNumberGuessIdentity As WorkflowIdentity
        Public FlowchartNumberGuessIdentity As WorkflowIdentity
        Public SequentialNumberGuessIdentity As WorkflowIdentity

        'v1 Identities.
        Public StateMachineNumberGuessIdentity_v1 As WorkflowIdentity
        Public FlowchartNumberGuessIdentity_v1 As WorkflowIdentity
        Public SequentialNumberGuessIdentity_v1 As WorkflowIdentity

        Sub New()
            map = New Dictionary(Of WorkflowIdentity, Activity)

            'Add the current workflow version identities.
            StateMachineNumberGuessIdentity = New WorkflowIdentity With
            {
                .Name = "StateMachineNumberGuessWorkflow",
                .Version = New Version(2, 0, 0, 0)
            }

            FlowchartNumberGuessIdentity = New WorkflowIdentity With
            {
                .Name = "FlowchartNumberGuessWorkflow",
                .Version = New Version(2, 0, 0, 0)
            }

            SequentialNumberGuessIdentity = New WorkflowIdentity With
            {
                .Name = "SequentialNumberGuessWorkflow",
                .Version = New Version(2, 0, 0, 0)
            }

            map.Add(StateMachineNumberGuessIdentity, New StateMachineNumberGuessWorkflow())
            map.Add(FlowchartNumberGuessIdentity, New FlowchartNumberGuessWorkflow())
            map.Add(SequentialNumberGuessIdentity, New SequentialNumberGuessWorkflow())

            'Initialize the previous workflow version identities.
            StateMachineNumberGuessIdentity_v1 = New WorkflowIdentity With
            {
                .Name = "StateMachineNumberGuessWorkflow",
                .Version = New Version(1, 0, 0, 0)
            }

            FlowchartNumberGuessIdentity_v1 = New WorkflowIdentity With
            {
                .Name = "FlowchartNumberGuessWorkflow",
                .Version = New Version(1, 0, 0, 0)
            }

            SequentialNumberGuessIdentity_v1 = New WorkflowIdentity With
            {
                .Name = "SequentialNumberGuessWorkflow",
                .Version = New Version(1, 0, 0, 0)
            }

            'Add the previous version workflow identities to the dictionary along with
            'the corresponding workflow definitions loaded from the v1 assembly.
            'Assembly.LoadFile requires an absolute path so convert this relative path
            'to an absolute path.
            Dim v1AssemblyPath As String = "..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll"
            v1AssemblyPath = Path.GetFullPath(v1AssemblyPath)
            Dim v1Assembly As Assembly = Assembly.LoadFile(v1AssemblyPath)

            map.Add(StateMachineNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow"))

            map.Add(SequentialNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow"))

            map.Add(FlowchartNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow"))
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

        // v1 identities.
        static public WorkflowIdentity StateMachineNumberGuessIdentity_v1;
        static public WorkflowIdentity FlowchartNumberGuessIdentity_v1;
        static public WorkflowIdentity SequentialNumberGuessIdentity_v1;

        static WorkflowVersionMap()
        {
            map = new Dictionary<WorkflowIdentity, Activity>();

            // Add the current workflow version identities.
            StateMachineNumberGuessIdentity = new WorkflowIdentity
            {
                Name = "StateMachineNumberGuessWorkflow",
                // Version = new Version(1, 0, 0, 0),
                Version = new Version(2, 0, 0, 0)
            };

            FlowchartNumberGuessIdentity = new WorkflowIdentity
            {
                Name = "FlowchartNumberGuessWorkflow",
                // Version = new Version(1, 0, 0, 0),
                Version = new Version(2, 0, 0, 0)
            };

            SequentialNumberGuessIdentity = new WorkflowIdentity
            {
                Name = "SequentialNumberGuessWorkflow",
                // Version = new Version(1, 0, 0, 0),
                Version = new Version(2, 0, 0, 0)
            };

            map.Add(StateMachineNumberGuessIdentity, new StateMachineNumberGuessWorkflow());
            map.Add(FlowchartNumberGuessIdentity, new FlowchartNumberGuessWorkflow());
            map.Add(SequentialNumberGuessIdentity, new SequentialNumberGuessWorkflow());

            // Initialize the previous workflow version identities.
            StateMachineNumberGuessIdentity_v1 = new WorkflowIdentity
            {
                Name = "StateMachineNumberGuessWorkflow",
                Version = new Version(1, 0, 0, 0)
            };

            FlowchartNumberGuessIdentity_v1 = new WorkflowIdentity
            {
                Name = "FlowchartNumberGuessWorkflow",
                Version = new Version(1, 0, 0, 0)
            };

            SequentialNumberGuessIdentity_v1 = new WorkflowIdentity
            {
                Name = "SequentialNumberGuessWorkflow",
                Version = new Version(1, 0, 0, 0)
            };

            // Add the previous version workflow identities to the dictionary along with
            // the corresponding workflow definitions loaded from the v1 assembly.
            // Assembly.LoadFile requires an absolute path so convert this relative path
            // to an absolute path.
            string v1AssemblyPath = @"..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll";
            v1AssemblyPath = Path.GetFullPath(v1AssemblyPath);
            Assembly v1Assembly = Assembly.LoadFile(v1AssemblyPath);

            map.Add(StateMachineNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow") as Activity);

            map.Add(SequentialNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow") as Activity);

            map.Add(FlowchartNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow") as Activity);
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

### <a name="BKMK_BuildAndRun"></a> <span data-ttu-id="cc0a1-172">Derleme ve uygulamayı çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="cc0a1-172">To build and run the application</span></span>

1. <span data-ttu-id="cc0a1-173">Uygulamayı oluşturmak için CTRL + SHIFT + B ve başlatmak için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-173">Press CTRL+SHIFT+B to build the application, and then CTRL+F5 to start.</span></span>

2. <span data-ttu-id="cc0a1-174">Tıklayarak yeni bir iş akışının başlatılacağı **yeni oyun**.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-174">Start a new workflow by clicking **New Game**.</span></span> <span data-ttu-id="cc0a1-175">İş akışı sürümü altında durum penceresi görüntülenir ve güncelleştirilmiş sürümü ilişkili yansıtır `WorkflowIdentity`.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-175">The version of the workflow is displayed under the status window and reflects the updated version from the associated `WorkflowIdentity`.</span></span> <span data-ttu-id="cc0a1-176">Not `InstanceId` tamamlandığında, iş akışı için izleme dosyayı görüntülemek ve oyun tamamlanana kadar tahmin girin.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-176">Make a note of the `InstanceId` so you can view the tracking file for the workflow when it completes, and then enter guesses until the game is complete.</span></span> <span data-ttu-id="cc0a1-177">Kullanıcının tahmin güncelleştirmeleri temel durum penceresinde görüntülenen bilgileri nasıl görüntüleneceğini unutmayın `WriteLine` etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-177">Note how the user's guess is displayed in the information displayed in the status window based on the updates to the `WriteLine` activities.</span></span>

    ```
    Please enter a number between 1 and 10
    5 is too high.
    Please enter a number between 1 and 10
    3 is too high.
    Please enter a number between 1 and 10
    1 is too low.
    Please enter a number between 1 and 10
    Congratulations, you guessed the number in 4 turns.
    ```

    > [!NOTE]
    > <span data-ttu-id="cc0a1-178">Güncelleştirilmiş metinden `WriteLine` etkinlikleri görüntülenir, son çıktısını `WriteLine` bu konudaki eklendi etkinlik değil.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-178">The updated text from the `WriteLine` activities is displayed, but the output of the final `WriteLine` activity that was added in this topic is not.</span></span> <span data-ttu-id="cc0a1-179">Durum penceresi tarafından güncelleştirildiğinden olan `PersistableIdle` işleyici.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-179">That is because the status window is updated by the `PersistableIdle` handler.</span></span> <span data-ttu-id="cc0a1-180">İş akışı tamamlandıktan ve son etkinlikten sonra boşta geçmez, çünkü `PersistableIdle` işleyici çağrılmaz.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-180">Because the workflow completes and does not go idle after the final activity, the `PersistableIdle` handler is not called.</span></span> <span data-ttu-id="cc0a1-181">Ancak, durum penceresi tarafından benzer bir ileti görüntülenir `Completed` işleyici.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-181">However, a similar message is displayed in the status window by the `Completed` handler.</span></span> <span data-ttu-id="cc0a1-182">İçin isterseniz, kod eklenemedi `Completed` ından cümleler ayıklamak için işleyici `StringWriter` ve durum penceresi için görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-182">If desired, code could be added to the `Completed` handler to extract the text from the `StringWriter` and display it to the status window.</span></span>

3. <span data-ttu-id="cc0a1-183">Windows Gezgini'ni açın ve gidin **NumberGuessWorkflowHost\bin\debug** klasörü (veya **bin\release** proje ayarlarınıza bağlı olarak) karşılık gelen Not Defteri'ni kullanarak izleme dosyasını açın Tamamlanan iş akışı için.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-183">Open Windows Explorer and navigate to the **NumberGuessWorkflowHost\bin\debug** folder (or **bin\release** depending on your project settings) and open the tracking file using Notepad that corresponds to the completed workflow.</span></span> <span data-ttu-id="cc0a1-184">Not yapmadıysanız `InstanceId`, doğru izleme dosyası kullanarak tanımlayabilirsiniz **değiştirilme tarihi** Windows Explorer'da bilgileri.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-184">If you did not make a note of the `InstanceId`, you can identify the correct tracking file by using the **Date modified** information in Windows Explorer.</span></span>

    ```
    Please enter a number between 1 and 10
    5 is too high.
    Please enter a number between 1 and 10
    3 is too high.
    Please enter a number between 1 and 10
    1 is too low.
    Please enter a number between 1 and 10
    2 is correct. You guessed it in 4 turns.
    ```

    <span data-ttu-id="cc0a1-185">Güncelleştirilmiş `WriteLine` çıkış çıktısını dahil olmak üzere izleme dosyası içinde yer alan `WriteLine` bu konudaki eklendi.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-185">The updated `WriteLine` output is contained within the tracking file, including the output of the `WriteLine` that was added in this topic.</span></span>

4. <span data-ttu-id="cc0a1-186">Sayı tahmin eden uygulamaya geri geçin ve güncelleştirme yapılmadan önce başlatıldı iş akışları birini seçin.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-186">Switch back to the number guessing application and select one of the workflows that was started before the updates were made.</span></span> <span data-ttu-id="cc0a1-187">Seçili durumdaki iş akışı sürümü durum penceresi görüntülenir sürüm bilgilerine bakarak belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-187">You can identify the version of the currently selected workflow by looking at the version information that is displayed below the status window.</span></span> <span data-ttu-id="cc0a1-188">Tahminler girin ve eşleşme güncelleştirme durumu Not `WriteLine` etkinliği önceki bir sürümünden çıktı ve kullanıcının tahmin içermez.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-188">Enter some guesses and note that the status updates match the `WriteLine` activity output from the previous version, and do not include the user's guess.</span></span> <span data-ttu-id="cc0a1-189">Bu iş akışları sahip olmayan bir önceki iş akışı tanımı kullanıyorsunuz çünkü `WriteLine` güncelleştirmeleri.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-189">That is because these workflows are using the previous workflow definition that does not have the `WriteLine` updates.</span></span>

    <span data-ttu-id="cc0a1-190">Sonraki adımda [nasıl yapılır: Çalışan iş akışı örneğinin tanımını güncelleştirme](how-to-update-the-definition-of-a-running-workflow-instance.md), çalışan `v1` iş akışı örnekleri yeni işlevselliği içerdikleri için güncelleştirilmiş `v2` örnekleri.</span><span class="sxs-lookup"><span data-stu-id="cc0a1-190">In the next step, [How to: Update the Definition of a Running Workflow Instance](how-to-update-the-definition-of-a-running-workflow-instance.md), the running `v1` workflow instances are updated so they contain the new functionality as the `v2` instances.</span></span>
