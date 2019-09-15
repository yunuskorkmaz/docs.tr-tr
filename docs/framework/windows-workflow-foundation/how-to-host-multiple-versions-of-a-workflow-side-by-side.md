---
title: 'Nasıl yapılır: İş Akışının Birden Fazla Sürümünü Yan Yana Barındırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 09c575df-e0a3-4f3b-9e01-a7ac59d65287
ms.openlocfilehash: 820ed324c8095e2f9f2823513a37965099f42c48
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989644"
---
# <a name="how-to-host-multiple-versions-of-a-workflow-side-by-side"></a><span data-ttu-id="2e460-102">Nasıl yapılır: İş Akışının Birden Fazla Sürümünü Yan Yana Barındırma</span><span class="sxs-lookup"><span data-stu-id="2e460-102">How to: Host Multiple Versions of a Workflow Side-by-Side</span></span>

<span data-ttu-id="2e460-103">`WorkflowIdentity`, iş akışı uygulama geliştiricilerinin bir adı ve sürümü bir iş akışı tanımıyla ilişkilendirmesi ve bu bilgilerin kalıcı bir iş akışı örneğiyle ilişkilendirilmesi için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="2e460-103">`WorkflowIdentity` provides a way for workflow application developers to associate a name and a version with a workflow definition, and for this information to be associated with a persisted workflow instance.</span></span> <span data-ttu-id="2e460-104">Bu kimlik bilgileri, bir iş akışı tanımının birden çok sürümünün yan yana yürütülmesi gibi senaryoları etkinleştirmek için iş akışı uygulama geliştiricileri tarafından kullanılabilir ve dinamik güncelleştirme gibi diğer işlevler için de temel pulu sağlar.</span><span class="sxs-lookup"><span data-stu-id="2e460-104">This identity information can be used by workflow application developers to enable scenarios such as side-by-side execution of multiple versions of a workflow definition, and provides the cornerstone for other functionality such as dynamic update.</span></span> <span data-ttu-id="2e460-105">Öğreticideki Bu adım, bir iş akışının birden `WorkflowIdentity` çok sürümünü aynı anda barındırmak için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2e460-105">This step in the tutorial demonstrates how to use `WorkflowIdentity` to host multiple versions of a workflow at the same time.</span></span>

> [!NOTE]
> <span data-ttu-id="2e460-106">Tamamlanmış bir sürümü indirmek veya öğreticiye ilişkin bir video kılavuzunu görüntülemek için, bkz. [Windows Workflow Foundation (WF45)-Başlangıç Öğreticisi](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="2e460-106">To download a completed version or view a video walkthrough of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>

## <a name="in-this-topic"></a><span data-ttu-id="2e460-107">Bu konuda</span><span class="sxs-lookup"><span data-stu-id="2e460-107">In this topic</span></span>

<span data-ttu-id="2e460-108">Öğreticinin bu adımında, `WriteLine` iş akışındaki etkinlikler ek bilgi sağlamak için değiştirilir ve yeni `WriteLine` bir etkinlik eklenir.</span><span class="sxs-lookup"><span data-stu-id="2e460-108">In this step of the tutorial, the `WriteLine` activities in the workflow are modified to provide additional information, and a new `WriteLine` activity is added.</span></span> <span data-ttu-id="2e460-109">Özgün iş akışı derlemesinin bir kopyası depolanır ve ana bilgisayar uygulaması güncelleştirilir ve böylece hem orijinal hem de güncelleştirilmiş iş akışlarını aynı anda çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2e460-109">A copy of the original workflow assembly is stored, and the host application is updated so that it can run both the original and the updated workflows at the same time.</span></span>

- [<span data-ttu-id="2e460-110">NumberGuessWorkflowActivities projesinin bir kopyasını oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="2e460-110">To make a copy of the NumberGuessWorkflowActivities project</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_BackupCopy)

- [<span data-ttu-id="2e460-111">İş akışlarını güncelleştirmek için</span><span class="sxs-lookup"><span data-stu-id="2e460-111">To update the workflows</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateWorkflows)

  - [<span data-ttu-id="2e460-112">StateMachine iş akışını güncelleştirmek için</span><span class="sxs-lookup"><span data-stu-id="2e460-112">To update the StateMachine workflow</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateStateMachine)

  - [<span data-ttu-id="2e460-113">Akış çizelgesi iş akışını güncelleştirmek için</span><span class="sxs-lookup"><span data-stu-id="2e460-113">To update the Flowchart workflow</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateFlowchart)

  - [<span data-ttu-id="2e460-114">Sıralı iş akışını güncelleştirmek için</span><span class="sxs-lookup"><span data-stu-id="2e460-114">To update the Sequential workflow</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateSequential)

- [<span data-ttu-id="2e460-115">WorkflowVersionMap 'i önceki iş akışı sürümlerini içerecek şekilde güncelleştirmek için</span><span class="sxs-lookup"><span data-stu-id="2e460-115">To update WorkflowVersionMap to include the previous workflow versions</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateWorkflowVersionMap)

- [<span data-ttu-id="2e460-116">Uygulamayı derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="2e460-116">To build and run the application</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_BuildAndRun)

> [!NOTE]
> <span data-ttu-id="2e460-117">Bu konudaki adımları takip etmeden önce, uygulamayı çalıştırın, her türden birkaç iş akışını başlatın ve her biri için bir veya iki tahmin yaparak.</span><span class="sxs-lookup"><span data-stu-id="2e460-117">Before following the steps in this topic, run the application, start several workflows of each type, and making one or two guesses for each one.</span></span> <span data-ttu-id="2e460-118">Bu kalıcı iş akışları bu adımda ve aşağıdaki adımda [kullanılır: Çalışan bir Iş akışı örneğinin](how-to-update-the-definition-of-a-running-workflow-instance.md)tanımını güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="2e460-118">These persisted workflows are used in this step and the following step, [How to: Update the Definition of a Running Workflow Instance](how-to-update-the-definition-of-a-running-workflow-instance.md).</span></span>

> [!NOTE]
> <span data-ttu-id="2e460-119">Başlangıç öğreticisindeki her adım önceki adımlara bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="2e460-119">Each step in the Getting Started tutorial depends on the previous steps.</span></span> <span data-ttu-id="2e460-120">Önceki adımları tamamlamadıysanız, [Windows Workflow Foundation (WF45)-başlangıç öğreticisindeki](https://go.microsoft.com/fwlink/?LinkID=248976)öğreticinin tamamlanmış bir sürümünü indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2e460-120">If you did not complete the previous steps you can download a completed version of the tutorial from [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>

### <a name="BKMK_BackupCopy"></a><span data-ttu-id="2e460-121">NumberGuessWorkflowActivities projesinin bir kopyasını oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="2e460-121">To make a copy of the NumberGuessWorkflowActivities project</span></span>

1. <span data-ttu-id="2e460-122">Açık değilse, Visual Studio 2012 'de **WF45GettingStartedTutorial** çözümünü açın.</span><span class="sxs-lookup"><span data-stu-id="2e460-122">Open the **WF45GettingStartedTutorial** solution in Visual Studio 2012 if it is not open.</span></span>

2. <span data-ttu-id="2e460-123">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="2e460-123">Press CTRL+SHIFT+B to build the solution.</span></span>

3. <span data-ttu-id="2e460-124">**WF45GettingStartedTutorial** çözümünü kapatın.</span><span class="sxs-lookup"><span data-stu-id="2e460-124">Close the **WF45GettingStartedTutorial** solution.</span></span>

4. <span data-ttu-id="2e460-125">Windows Gezgini 'ni açın ve öğretici çözüm dosyasının ve proje klasörlerinin bulunduğu klasöre gidin.</span><span class="sxs-lookup"><span data-stu-id="2e460-125">Open Windows Explorer and navigate to the folder where the tutorial solution file and the project folders are located.</span></span>

5. <span data-ttu-id="2e460-126">**Numberguessworkflowwhost** ve **NumberGuessWorkflowActivities**aynı klasörde **PreviousVersions** adlı yeni bir klasör oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2e460-126">Create a new folder named **PreviousVersions** in the same folder as **NumberGuessWorkflowHost** and **NumberGuessWorkflowActivities**.</span></span> <span data-ttu-id="2e460-127">Bu klasör, sonraki öğretici adımlarda kullanılan iş akışlarının farklı sürümlerini içeren derlemeleri içermesi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2e460-127">This folder is used to contain the assemblies that contain the different versions of the workflows used in the subsequent tutorial steps.</span></span>

6. <span data-ttu-id="2e460-128">**NumberGuessWorkflowActivities\bin\debug** klasörüne gidin (veya proje ayarlarınıza bağlı olarak **bin\release** ).</span><span class="sxs-lookup"><span data-stu-id="2e460-128">Navigate to the **NumberGuessWorkflowActivities\bin\debug** folder (or **bin\release** depending on your project settings).</span></span> <span data-ttu-id="2e460-129">**NumberGuessWorkflowActivities. dll dosyasını** kopyalayın ve **PreviousVersions** klasörüne yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="2e460-129">Copy **NumberGuessWorkflowActivities.dll** and paste it into the **PreviousVersions** folder.</span></span>

7. <span data-ttu-id="2e460-130">**PreviousVersions** klasöründeki **NumberGuessWorkflowActivities. dll dosyasını** **NumberGuessWorkflowActivities_v1. dll**olarak yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="2e460-130">Rename **NumberGuessWorkflowActivities.dll** in the **PreviousVersions** folder to **NumberGuessWorkflowActivities_v1.dll**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="2e460-131">Bu konudaki adımlarda, iş akışlarının birden çok sürümünü içerecek şekilde kullanılan derlemeleri yönetmenin bir yolu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2e460-131">The steps in this topic demonstrate one way to manage the assemblies used to contain multiple versions of the workflows.</span></span> <span data-ttu-id="2e460-132">Derlemeleri tanımlayıcı adlandırma ve genel derleme önbelleğinde kaydetme gibi diğer yöntemler de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2e460-132">Other methods such as strong naming the assemblies and registering them in the global assembly cache could also be used.</span></span>

8. <span data-ttu-id="2e460-133">**Numberguessworkflowwhost**, **NumberGuessWorkflowActivities**ve yeni eklenen **PreviousVersions** klasörüyle aynı klasörde **NumberGuessWorkflowActivities_du** adlı yeni bir klasör oluşturun ve tüm dosyaları kopyalayın ve **NumberGuessWorkflowActivities** klasöründen yeni **NumberGuessWorkflowActivities_du** klasörüne alt klasörler.</span><span class="sxs-lookup"><span data-stu-id="2e460-133">Create a new folder named **NumberGuessWorkflowActivities_du** in the same folder as **NumberGuessWorkflowHost**, **NumberGuessWorkflowActivities**, and the newly added **PreviousVersions** folder, and copy all of the files and subfolders from the **NumberGuessWorkflowActivities** folder into the new **NumberGuessWorkflowActivities_du** folder.</span></span> <span data-ttu-id="2e460-134">Etkinliğin ilk sürümü için projenin bu yedek kopyası şu şekilde kullanılır [: Çalışan bir Iş akışı örneğinin](how-to-update-the-definition-of-a-running-workflow-instance.md)tanımını güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="2e460-134">This backup copy of the project for the initial version of the activities is used in [How to: Update the Definition of a Running Workflow Instance](how-to-update-the-definition-of-a-running-workflow-instance.md).</span></span>

9. <span data-ttu-id="2e460-135">Visual Studio 2012 ' de **WF45GettingStartedTutorial** çözümünü yeniden açın.</span><span class="sxs-lookup"><span data-stu-id="2e460-135">Re-open the **WF45GettingStartedTutorial** solution in Visual Studio 2012.</span></span>

### <a name="BKMK_UpdateWorkflows"></a><span data-ttu-id="2e460-136">İş akışlarını güncelleştirmek için</span><span class="sxs-lookup"><span data-stu-id="2e460-136">To update the workflows</span></span>

<span data-ttu-id="2e460-137">Bu bölümde, iş akışı tanımları güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="2e460-137">In this section, the workflow definitions are updated.</span></span> <span data-ttu-id="2e460-138">Kullanıcının tahminlerine geri bildirimde bulunan iki `WriteLine` etkinlik güncelleştirilir ve sayı tahmin edildikten sonra oyun hakkında ek bilgiler sağlayan yeni `WriteLine` bir etkinlik eklenir.</span><span class="sxs-lookup"><span data-stu-id="2e460-138">The two `WriteLine` activities that give feedback on the user's guess are updated, and a new `WriteLine` activity is added that provides additional information about the game once the number is guessed.</span></span>

#### <a name="BKMK_UpdateStateMachine"></a><span data-ttu-id="2e460-139">StateMachine iş akışını güncelleştirmek için</span><span class="sxs-lookup"><span data-stu-id="2e460-139">To update the StateMachine workflow</span></span>

1. <span data-ttu-id="2e460-140">**Çözüm Gezgini**, **NumberGuessWorkflowActivities** projesi altında **StateMachineNumberGuessWorkflow. xaml**' ye çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="2e460-140">In **Solution Explorer**, under the **NumberGuessWorkflowActivities** project, double-click **StateMachineNumberGuessWorkflow.xaml**.</span></span>

2. <span data-ttu-id="2e460-141">Durum makinesinde **tahmin yanlış** geçişi ' ne çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="2e460-141">Double-click the **Guess Incorrect** transition on the state machine.</span></span>

3. <span data-ttu-id="2e460-142">Etkinliğin en `WriteLine`solundakigüncelleştirmeyigüncelleştirin. `Text` `If`</span><span class="sxs-lookup"><span data-stu-id="2e460-142">Update the `Text` of the left-most `WriteLine` in the `If` activity.</span></span>

    ```vb
    Guess & " is too low."
    ```

    ```csharp
    Guess + " is too low."
    ```

4. <span data-ttu-id="2e460-143">Etkinliğin en `WriteLine` sağdaki bölümünü güncelleştirin. `Text` `If`</span><span class="sxs-lookup"><span data-stu-id="2e460-143">Update the `Text` of the right-most `WriteLine` in the `If` activity.</span></span>

    ```vb
    Guess & " is too high."
    ```

    ```csharp
    Guess + " is too high."
    ```

5. <span data-ttu-id="2e460-144">İş akışı Tasarımcısı ' nın en üstünde bulunan içerik haritası ' nda **StateMachine** ' e tıklayarak iş akışı tasarımcısında genel durum makinesi görünümüne geri dönün.</span><span class="sxs-lookup"><span data-stu-id="2e460-144">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>

6. <span data-ttu-id="2e460-145">Durum makinesinde **tahmin doğru** geçişi ' ne çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="2e460-145">Double-click the **Guess Correct** transition on the state machine.</span></span>

7. <span data-ttu-id="2e460-146">**Araç kutusu** ' nu **temel elemanlar** bölümünden bir **WriteLine** etkinliği sürükleyin ve **bırakma eylemi etkinliğine buraya** bırakın.</span><span class="sxs-lookup"><span data-stu-id="2e460-146">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it on the **Drop Action activity here** label of the transition.</span></span>

8. <span data-ttu-id="2e460-147">`Text` Özellik kutusuna aşağıdaki ifadeyi yazın.</span><span class="sxs-lookup"><span data-stu-id="2e460-147">Type the following expression into the `Text` property box.</span></span>

    ```vb
    Guess & " is correct. You guessed it in " & Turns & " turns."
    ```

    ```csharp
    Guess + " is correct. You guessed it in " + Turns + " turns."
    ```

#### <a name="BKMK_UpdateFlowchart"></a><span data-ttu-id="2e460-148">Akış çizelgesi iş akışını güncelleştirmek için</span><span class="sxs-lookup"><span data-stu-id="2e460-148">To update the Flowchart workflow</span></span>

1. <span data-ttu-id="2e460-149">**Çözüm Gezgini**, **NumberGuessWorkflowActivities** projesi altında **FlowchartNumberGuessWorkflow. xaml**' e çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="2e460-149">In **Solution Explorer**, under the **NumberGuessWorkflowActivities** project, double-click **FlowchartNumberGuessWorkflow.xaml**.</span></span>

2. <span data-ttu-id="2e460-150">`Text` En`WriteLine` soldaki etkinliğin güncelleştirmesini güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="2e460-150">Update the `Text` of the left-most `WriteLine` activity.</span></span>

    ```vb
    Guess & " is too low."
    ```

    ```csharp
    Guess + " is too low."
    ```

3. <span data-ttu-id="2e460-151">`Text` En`WriteLine` sağdaki etkinliğin güncelleştirmesini güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="2e460-151">Update the `Text` of the right-most `WriteLine` activity.</span></span>

    ```vb
    Guess & " is too high."
    ```

    ```csharp
    Guess + " is too high."
    ```

4. <span data-ttu-id="2e460-152">**Araç kutusu** ' nun `True` **temel öğeler** bölümünden bir **WriteLine** etkinliğini sürükleyin ve en üstteki `FlowDecision`eylemin bırakma noktasına bırakın.</span><span class="sxs-lookup"><span data-stu-id="2e460-152">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it on the drop point of the `True` action of the topmost `FlowDecision`.</span></span> <span data-ttu-id="2e460-153">Etkinlik, akış çizelgesine eklenir ve `True` eylemine `FlowDecision`bağlanır. `WriteLine`</span><span class="sxs-lookup"><span data-stu-id="2e460-153">The `WriteLine` activity is added to the flowchart and linked to the `True` action of the `FlowDecision`.</span></span>

5. <span data-ttu-id="2e460-154">`Text` Özellik kutusuna aşağıdaki ifadeyi yazın.</span><span class="sxs-lookup"><span data-stu-id="2e460-154">Type the following expression into the `Text` property box.</span></span>

    ```vb
    Guess & " is correct. You guessed it in " & Turns & " turns."
    ```

    ```csharp
    Guess + " is correct. You guessed it in " + Turns + " turns."
    ```

#### <a name="BKMK_UpdateSequential"></a><span data-ttu-id="2e460-155">Sıralı iş akışını güncelleştirmek için</span><span class="sxs-lookup"><span data-stu-id="2e460-155">To update the Sequential workflow</span></span>

1. <span data-ttu-id="2e460-156">**Çözüm Gezgini**, **NumberGuessWorkflowActivities** projesi altında **SequentialNumberGuessWorkflow. xaml**' ye çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="2e460-156">In **Solution Explorer**, under the **NumberGuessWorkflowActivities** project, double-click **SequentialNumberGuessWorkflow.xaml**.</span></span>

2. <span data-ttu-id="2e460-157">Etkinliğin en `WriteLine`solundakigüncelleştirmeyigüncelleştirin. `Text` `If`</span><span class="sxs-lookup"><span data-stu-id="2e460-157">Update the `Text` of the left-most `WriteLine` in the `If` activity.</span></span>

    ```vb
    Guess & " is too low."
    ```

    ```csharp
    Guess + " is too low."
    ```

3. <span data-ttu-id="2e460-158">Etkinliğin en `WriteLine`sağdakietkinliğinigüncelleştirin. `Text` `If`</span><span class="sxs-lookup"><span data-stu-id="2e460-158">Update the `Text` of the right-most `WriteLine` activity in the `If` activity.</span></span>

    ```vb
    Guess & " is too high."
    ```

    ```csharp
    Guess + " is too high."
    ```

4. <span data-ttu-id="2e460-159">**Araç kutusunun** **temel elemanlar** bölümünden bir **WriteLine** etkinliğini sürükleyin ve **DoWhile** etkinliğinden sonra, **WriteLine** 'ın kök `Sequence` etkinliğinde son etkinlik olması için onu bırakın.</span><span class="sxs-lookup"><span data-stu-id="2e460-159">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it after the **DoWhile** activity so that the **WriteLine** is the final activity in the root `Sequence` activity.</span></span>

5. <span data-ttu-id="2e460-160">`Text` Özellik kutusuna aşağıdaki ifadeyi yazın.</span><span class="sxs-lookup"><span data-stu-id="2e460-160">Type the following expression into the `Text` property box.</span></span>

    ```vb
    Guess & " is correct. You guessed it in " & Turns & " turns."
    ```

    ```csharp
    Guess + " is correct. You guessed it in " + Turns + " turns."
    ```

### <a name="BKMK_UpdateWorkflowVersionMap"></a><span data-ttu-id="2e460-161">WorkflowVersionMap 'i önceki iş akışı sürümlerini içerecek şekilde güncelleştirmek için</span><span class="sxs-lookup"><span data-stu-id="2e460-161">To update WorkflowVersionMap to include the previous workflow versions</span></span>

1. <span data-ttu-id="2e460-162"># **Guessworkflowwhost** projesi altındaki **WorkflowVersionMap.cs** (veya **WorkflowVersionMap. vb**) öğesine çift tıklayarak açın.</span><span class="sxs-lookup"><span data-stu-id="2e460-162">Double-click **WorkflowVersionMap.cs** (or **WorkflowVersionMap.vb**) under the **NumberGuessWorkflowHost** project to open it.</span></span>

2. <span data-ttu-id="2e460-163">Aşağıdaki `using` (veya `Imports`) deyimlerini, diğer `using` (veya `Imports`) deyimleriyle dosyanın en üstüne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2e460-163">Add the following `using` (or `Imports`) statements to the top of the file with the other `using` (or `Imports`) statements.</span></span>

    ```vb
    Imports System.Reflection
    Imports System.IO
    ```

    ```csharp
    using System.Reflection;
    using System.IO;
    ```

3. <span data-ttu-id="2e460-164">Mevcut üç iş akışı kimlik bildiriminin hemen altına üç yeni iş akışı kimliği ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2e460-164">Add three new workflow identities just below the three existing workflow identity declarations.</span></span> <span data-ttu-id="2e460-165">Bu yeni `v1` iş akışı kimlikleri, güncelleştirmeler yapılmadan önce başlatılan iş akışlarına doğru iş akışı tanımını sağlamak üzere kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="2e460-165">These new `v1` workflow identities will be used provide the correct workflow definition to workflows started before the updates were made.</span></span>

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

4. <span data-ttu-id="2e460-166">Oluşturucuda, üç geçerli iş akışı `Version` kimliği özelliğini ' e `2.0.0.0`güncelleştirin. `WorkflowVersionMap`</span><span class="sxs-lookup"><span data-stu-id="2e460-166">In the `WorkflowVersionMap` constructor, update the `Version` property of the three current workflow identities to `2.0.0.0`.</span></span>

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

    <span data-ttu-id="2e460-167">İçindeki iş akışlarının geçerli sürümlerini sözlüğe ekleyen kod, projede başvurulan geçerli sürümleri kullanır, bu nedenle iş akışı tanımlarını Başlatan kodun güncelleştirilmesine gerek kalmaz.</span><span class="sxs-lookup"><span data-stu-id="2e460-167">The code in that adds the current versions of the workflows to the dictionary uses the current versions that are referenced in the project, so the code that initializes the workflow definitions does not need to be updated.</span></span>

5. <span data-ttu-id="2e460-168">Aşağıdaki kodu, geçerli sürümleri sözlüğe ekleyen koddan hemen sonra oluşturucuya ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2e460-168">Add the following code in the constructor just after the code that adds the current versions to the dictionary.</span></span>

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

    <span data-ttu-id="2e460-169">Bu iş akışı kimlikleri, karşılık gelen iş akışı tanımlarının başlangıç sürümleriyle ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="2e460-169">These workflow identities are associated with the initial versions of the corresponding workflow definitions.</span></span>

6. <span data-ttu-id="2e460-170">Sonra, iş akışı tanımlarının ilk sürümünü içeren derlemeyi yükleyin ve ilgili iş akışı tanımlarını oluşturun ve sözlüğe ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2e460-170">Next, load the assembly that contains the initial version of the workflow definitions, and create and add the corresponding workflow definitions to the dictionary.</span></span>

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

    <span data-ttu-id="2e460-171">Aşağıdaki örnek, güncelleştirilmiş `WorkflowVersionMap` sınıfın tüm listesidir.</span><span class="sxs-lookup"><span data-stu-id="2e460-171">The following example is the complete listing for the updated `WorkflowVersionMap` class.</span></span>

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

### <a name="BKMK_BuildAndRun"></a><span data-ttu-id="2e460-172">Uygulamayı derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="2e460-172">To build and run the application</span></span>

1. <span data-ttu-id="2e460-173">Uygulamayı derlemek için CTRL + SHIFT + B tuşlarına basın ve ardından başlatmak için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="2e460-173">Press CTRL+SHIFT+B to build the application, and then CTRL+F5 to start.</span></span>

2. <span data-ttu-id="2e460-174">Yeni **oyun**' i tıklatarak yeni bir iş akışı başlatın.</span><span class="sxs-lookup"><span data-stu-id="2e460-174">Start a new workflow by clicking **New Game**.</span></span> <span data-ttu-id="2e460-175">İş akışının sürümü durum penceresi altında görüntülenir ve güncelleştirilmiş sürümü ilişkili `WorkflowIdentity`dosyadan yansıtır.</span><span class="sxs-lookup"><span data-stu-id="2e460-175">The version of the workflow is displayed under the status window and reflects the updated version from the associated `WorkflowIdentity`.</span></span> <span data-ttu-id="2e460-176">İşlem tamamlandığında iş akışı için `InstanceId` izleme dosyasını görüntüleyebilmeniz ve ardından oyun tamamlanana kadar tahmin edilecek şekilde girmeniz için, ' yi bir yere göz önünde bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2e460-176">Make a note of the `InstanceId` so you can view the tracking file for the workflow when it completes, and then enter guesses until the game is complete.</span></span> <span data-ttu-id="2e460-177">Kullanıcı tahminin, `WriteLine` etkinliklerdeki güncelleştirmelere bağlı olarak durum penceresinde görünen bilgilere nasıl görüntülendiğini aklınızda yapın.</span><span class="sxs-lookup"><span data-stu-id="2e460-177">Note how the user's guess is displayed in the information displayed in the status window based on the updates to the `WriteLine` activities.</span></span>

    ```console
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
    > <span data-ttu-id="2e460-178">`WriteLine` Etkinliklerdeki güncelleştirilmiş metin görüntülenir, ancak bu konuya eklenen son `WriteLine` etkinliğin çıktısı değildir.</span><span class="sxs-lookup"><span data-stu-id="2e460-178">The updated text from the `WriteLine` activities is displayed, but the output of the final `WriteLine` activity that was added in this topic is not.</span></span> <span data-ttu-id="2e460-179">Yani durum penceresi `PersistableIdle` işleyici tarafından güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="2e460-179">That is because the status window is updated by the `PersistableIdle` handler.</span></span> <span data-ttu-id="2e460-180">İş akışı tamamlandığından ve son etkinlikten sonra boşta çalışmadığından, `PersistableIdle` işleyici çağrılmaz.</span><span class="sxs-lookup"><span data-stu-id="2e460-180">Because the workflow completes and does not go idle after the final activity, the `PersistableIdle` handler is not called.</span></span> <span data-ttu-id="2e460-181">Ancak, benzer bir ileti `Completed` işleyicinin durum penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="2e460-181">However, a similar message is displayed in the status window by the `Completed` handler.</span></span> <span data-ttu-id="2e460-182">İsterseniz, metni `StringWriter` öğesinden ayıklamak ve durum penceresine göstermek `Completed` için, kod işleyiciye eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="2e460-182">If desired, code could be added to the `Completed` handler to extract the text from the `StringWriter` and display it to the status window.</span></span>

3. <span data-ttu-id="2e460-183">Windows Gezgini 'ni açın ve **Numberguessworkflowwhost\bin\debug** klasörüne (veya proje ayarlarınıza bağlı olarak **bin\release** ) gidin ve tamamlanan Iş akışına karşılık gelen Not defteri 'ni kullanarak izleme dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="2e460-183">Open Windows Explorer and navigate to the **NumberGuessWorkflowHost\bin\debug** folder (or **bin\release** depending on your project settings) and open the tracking file using Notepad that corresponds to the completed workflow.</span></span> <span data-ttu-id="2e460-184">`InstanceId`' İ Not yapmadıysanız, Windows Gezgini 'nde **değiştirme tarihi** bilgilerini kullanarak doğru izleme dosyasını tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2e460-184">If you did not make a note of the `InstanceId`, you can identify the correct tracking file by using the **Date modified** information in Windows Explorer.</span></span>

    ```console
    Please enter a number between 1 and 10
    5 is too high.
    Please enter a number between 1 and 10
    3 is too high.
    Please enter a number between 1 and 10
    1 is too low.
    Please enter a number between 1 and 10
    2 is correct. You guessed it in 4 turns.
    ```

    <span data-ttu-id="2e460-185">Güncelleştirilmiş `WriteLine` çıktı, bu konuya eklenen `WriteLine` öğesinin çıktısı da dahil olmak üzere izleme dosyası içinde yer alır.</span><span class="sxs-lookup"><span data-stu-id="2e460-185">The updated `WriteLine` output is contained within the tracking file, including the output of the `WriteLine` that was added in this topic.</span></span>

4. <span data-ttu-id="2e460-186">Tahmin sayısı uygulamasına geri dönün ve güncelleştirmeler yapılmadan önce başlatılan iş akışlarından birini seçin.</span><span class="sxs-lookup"><span data-stu-id="2e460-186">Switch back to the number guessing application and select one of the workflows that was started before the updates were made.</span></span> <span data-ttu-id="2e460-187">Durum penceresinin altında görüntülenen sürüm bilgilerine bakarak şu anda seçili olan iş akışının sürümünü tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2e460-187">You can identify the version of the currently selected workflow by looking at the version information that is displayed below the status window.</span></span> <span data-ttu-id="2e460-188">Bazı tahminler girin ve durum güncelleştirmelerinin önceki sürümden gelen `WriteLine` etkinlik çıkışıyla eşleştiğini ve kullanıcının tahminlerini dahil edileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2e460-188">Enter some guesses and note that the status updates match the `WriteLine` activity output from the previous version, and do not include the user's guess.</span></span> <span data-ttu-id="2e460-189">Bunun nedeni, bu iş akışlarının `WriteLine` güncelleştirmeleri olmayan önceki iş akışı tanımını kullanıyor olması.</span><span class="sxs-lookup"><span data-stu-id="2e460-189">That is because these workflows are using the previous workflow definition that does not have the `WriteLine` updates.</span></span>

    <span data-ttu-id="2e460-190">Sonraki adımda, [nasıl yapılır: Çalışan bir iş akışı örneğinin](how-to-update-the-definition-of-a-running-workflow-instance.md)tanımını güncelleştirme, çalışan `v1` iş akışı örnekleri, `v2` örnekler olarak yeni işlevleri içerecek şekilde güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="2e460-190">In the next step, [How to: Update the Definition of a Running Workflow Instance](how-to-update-the-definition-of-a-running-workflow-instance.md), the running `v1` workflow instances are updated so they contain the new functionality as the `v2` instances.</span></span>
