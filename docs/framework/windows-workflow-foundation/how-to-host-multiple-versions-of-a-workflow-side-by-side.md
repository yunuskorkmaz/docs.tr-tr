---
title: 'Nasıl yapılır: İş Akışının Birden Fazla Sürümünü Yan Yana Barındırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 09c575df-e0a3-4f3b-9e01-a7ac59d65287
ms.openlocfilehash: e47440110215d8e60744c26c6351211a2ac08f3a
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98191163"
---
# <a name="how-to-host-multiple-versions-of-a-workflow-side-by-side"></a><span data-ttu-id="355ec-102">Nasıl yapılır: İş Akışının Birden Fazla Sürümünü Yan Yana Barındırma</span><span class="sxs-lookup"><span data-stu-id="355ec-102">How to: Host Multiple Versions of a Workflow Side-by-Side</span></span>

<span data-ttu-id="355ec-103">`WorkflowIdentity` , iş akışı uygulama geliştiricilerinin bir adı ve sürümü bir iş akışı tanımıyla ilişkilendirmesi ve bu bilgilerin kalıcı bir iş akışı örneğiyle ilişkilendirilmesi için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="355ec-103">`WorkflowIdentity` provides a way for workflow application developers to associate a name and a version with a workflow definition, and for this information to be associated with a persisted workflow instance.</span></span> <span data-ttu-id="355ec-104">Bu kimlik bilgileri, bir iş akışı tanımının birden çok sürümünün yan yana yürütülmesi gibi senaryoları etkinleştirmek için iş akışı uygulama geliştiricileri tarafından kullanılabilir ve dinamik güncelleştirme gibi diğer işlevler için de temel pulu sağlar.</span><span class="sxs-lookup"><span data-stu-id="355ec-104">This identity information can be used by workflow application developers to enable scenarios such as side-by-side execution of multiple versions of a workflow definition, and provides the cornerstone for other functionality such as dynamic update.</span></span> <span data-ttu-id="355ec-105">Öğreticideki Bu adım `WorkflowIdentity` , bir iş akışının birden çok sürümünü aynı anda barındırmak için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="355ec-105">This step in the tutorial demonstrates how to use `WorkflowIdentity` to host multiple versions of a workflow at the same time.</span></span>

## <a name="in-this-topic"></a><span data-ttu-id="355ec-106">Bu konuda</span><span class="sxs-lookup"><span data-stu-id="355ec-106">In this topic</span></span>

<span data-ttu-id="355ec-107">Öğreticinin bu adımında, `WriteLine` iş akışındaki etkinlikler ek bilgi sağlamak için değiştirilir ve yeni bir `WriteLine` etkinlik eklenir.</span><span class="sxs-lookup"><span data-stu-id="355ec-107">In this step of the tutorial, the `WriteLine` activities in the workflow are modified to provide additional information, and a new `WriteLine` activity is added.</span></span> <span data-ttu-id="355ec-108">Özgün iş akışı derlemesinin bir kopyası depolanır ve ana bilgisayar uygulaması güncelleştirilir ve böylece hem orijinal hem de güncelleştirilmiş iş akışlarını aynı anda çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="355ec-108">A copy of the original workflow assembly is stored, and the host application is updated so that it can run both the original and the updated workflows at the same time.</span></span>

- [<span data-ttu-id="355ec-109">NumberGuessWorkflowActivities projesinin bir kopyasını oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="355ec-109">To make a copy of the NumberGuessWorkflowActivities project</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_BackupCopy)

- [<span data-ttu-id="355ec-110">İş akışlarını güncelleştirmek için</span><span class="sxs-lookup"><span data-stu-id="355ec-110">To update the workflows</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateWorkflows)

  - [<span data-ttu-id="355ec-111">StateMachine iş akışını güncelleştirmek için</span><span class="sxs-lookup"><span data-stu-id="355ec-111">To update the StateMachine workflow</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateStateMachine)

  - [<span data-ttu-id="355ec-112">Akış çizelgesi iş akışını güncelleştirmek için</span><span class="sxs-lookup"><span data-stu-id="355ec-112">To update the Flowchart workflow</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateFlowchart)

  - [<span data-ttu-id="355ec-113">Sıralı iş akışını güncelleştirmek için</span><span class="sxs-lookup"><span data-stu-id="355ec-113">To update the Sequential workflow</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateSequential)

- [<span data-ttu-id="355ec-114">WorkflowVersionMap 'i önceki iş akışı sürümlerini içerecek şekilde güncelleştirmek için</span><span class="sxs-lookup"><span data-stu-id="355ec-114">To update WorkflowVersionMap to include the previous workflow versions</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateWorkflowVersionMap)

- [<span data-ttu-id="355ec-115">Uygulamayı derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="355ec-115">To build and run the application</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_BuildAndRun)

> [!NOTE]
> <span data-ttu-id="355ec-116">Bu konudaki adımları takip etmeden önce, uygulamayı çalıştırın, her türden birkaç iş akışını başlatın ve her biri için bir veya iki tahmin yaparak.</span><span class="sxs-lookup"><span data-stu-id="355ec-116">Before following the steps in this topic, run the application, start several workflows of each type, and making one or two guesses for each one.</span></span> <span data-ttu-id="355ec-117">Bu kalıcı iş akışları, bu adımda ve aşağıdaki adımda, [nasıl yapılır: çalışan bir Iş akışı örneğinin tanımını güncelleştirme](how-to-update-the-definition-of-a-running-workflow-instance.md)' de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="355ec-117">These persisted workflows are used in this step and the following step, [How to: Update the Definition of a Running Workflow Instance](how-to-update-the-definition-of-a-running-workflow-instance.md).</span></span>

### <a name="to-make-a-copy-of-the-numberguessworkflowactivities-project"></a><a name="BKMK_BackupCopy"></a> <span data-ttu-id="355ec-118">NumberGuessWorkflowActivities projesinin bir kopyasını oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="355ec-118">To make a copy of the NumberGuessWorkflowActivities project</span></span>

1. <span data-ttu-id="355ec-119">Açık değilse, Visual Studio 2012 'de **WF45GettingStartedTutorial** çözümünü açın.</span><span class="sxs-lookup"><span data-stu-id="355ec-119">Open the **WF45GettingStartedTutorial** solution in Visual Studio 2012 if it is not open.</span></span>

2. <span data-ttu-id="355ec-120">Çözümü derlemek için CTRL+SHIFT+B'ye basın.</span><span class="sxs-lookup"><span data-stu-id="355ec-120">Press CTRL+SHIFT+B to build the solution.</span></span>

3. <span data-ttu-id="355ec-121">**WF45GettingStartedTutorial** çözümünü kapatın.</span><span class="sxs-lookup"><span data-stu-id="355ec-121">Close the **WF45GettingStartedTutorial** solution.</span></span>

4. <span data-ttu-id="355ec-122">Windows Gezgini 'ni açın ve öğretici çözüm dosyasının ve proje klasörlerinin bulunduğu klasöre gidin.</span><span class="sxs-lookup"><span data-stu-id="355ec-122">Open Windows Explorer and navigate to the folder where the tutorial solution file and the project folders are located.</span></span>

5. <span data-ttu-id="355ec-123">**Numberguessworkflowwhost** ve **NumberGuessWorkflowActivities** aynı klasörde **PreviousVersions** adlı yeni bir klasör oluşturun.</span><span class="sxs-lookup"><span data-stu-id="355ec-123">Create a new folder named **PreviousVersions** in the same folder as **NumberGuessWorkflowHost** and **NumberGuessWorkflowActivities**.</span></span> <span data-ttu-id="355ec-124">Bu klasör, sonraki öğretici adımlarda kullanılan iş akışlarının farklı sürümlerini içeren derlemeleri içermesi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="355ec-124">This folder is used to contain the assemblies that contain the different versions of the workflows used in the subsequent tutorial steps.</span></span>

6. <span data-ttu-id="355ec-125">**NumberGuessWorkflowActivities\bin\debug** klasörüne gidin (veya proje ayarlarınıza bağlı olarak **bin\release** ).</span><span class="sxs-lookup"><span data-stu-id="355ec-125">Navigate to the **NumberGuessWorkflowActivities\bin\debug** folder (or **bin\release** depending on your project settings).</span></span> <span data-ttu-id="355ec-126">**NumberGuessWorkflowActivities.dll** kopyalayın ve **PreviousVersions** klasörüne yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="355ec-126">Copy **NumberGuessWorkflowActivities.dll** and paste it into the **PreviousVersions** folder.</span></span>

7. <span data-ttu-id="355ec-127">**PreviousVersions** klasöründeki **NumberGuessWorkflowActivities.dll** **NumberGuessWorkflowActivities_v1.dll** olarak yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="355ec-127">Rename **NumberGuessWorkflowActivities.dll** in the **PreviousVersions** folder to **NumberGuessWorkflowActivities_v1.dll**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="355ec-128">Bu konudaki adımlarda, iş akışlarının birden çok sürümünü içerecek şekilde kullanılan derlemeleri yönetmenin bir yolu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="355ec-128">The steps in this topic demonstrate one way to manage the assemblies used to contain multiple versions of the workflows.</span></span> <span data-ttu-id="355ec-129">Derlemeleri tanımlayıcı adlandırma ve genel derleme önbelleğinde kaydetme gibi diğer yöntemler de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="355ec-129">Other methods such as strong naming the assemblies and registering them in the global assembly cache could also be used.</span></span>

8. <span data-ttu-id="355ec-130">**Numberguessworkflowwhost**, **NumberGuessWorkflowActivities** ve yeni eklenen **previousversions** klasörüyle aynı klasörde **NumberGuessWorkflowActivities_du** adlı yeni bir klasör oluşturun ve tüm dosyaları ve alt klasörleri **NumberGuessWorkflowActivities** klasöründen yeni **NumberGuessWorkflowActivities_du** klasörüne kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="355ec-130">Create a new folder named **NumberGuessWorkflowActivities_du** in the same folder as **NumberGuessWorkflowHost**, **NumberGuessWorkflowActivities**, and the newly added **PreviousVersions** folder, and copy all of the files and subfolders from the **NumberGuessWorkflowActivities** folder into the new **NumberGuessWorkflowActivities_du** folder.</span></span> <span data-ttu-id="355ec-131">Etkinliğin ilk sürümü için projenin bu yedek kopyası, [nasıl yapılır: çalışan bir Iş akışı örneğinin tanımını güncelleştirme](how-to-update-the-definition-of-a-running-workflow-instance.md)bölümünde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="355ec-131">This backup copy of the project for the initial version of the activities is used in [How to: Update the Definition of a Running Workflow Instance](how-to-update-the-definition-of-a-running-workflow-instance.md).</span></span>

9. <span data-ttu-id="355ec-132">Visual Studio 2012 ' de **WF45GettingStartedTutorial** çözümünü yeniden açın.</span><span class="sxs-lookup"><span data-stu-id="355ec-132">Re-open the **WF45GettingStartedTutorial** solution in Visual Studio 2012.</span></span>

### <a name="to-update-the-workflows"></a><a name="BKMK_UpdateWorkflows"></a> <span data-ttu-id="355ec-133">İş akışlarını güncelleştirmek için</span><span class="sxs-lookup"><span data-stu-id="355ec-133">To update the workflows</span></span>

<span data-ttu-id="355ec-134">Bu bölümde, iş akışı tanımları güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="355ec-134">In this section, the workflow definitions are updated.</span></span> <span data-ttu-id="355ec-135">`WriteLine`Kullanıcının tahminlerine geri bildirimde bulunan iki etkinlik güncelleştirilir ve `WriteLine` sayı tahmin edildikten sonra oyun hakkında ek bilgiler sağlayan yeni bir etkinlik eklenir.</span><span class="sxs-lookup"><span data-stu-id="355ec-135">The two `WriteLine` activities that give feedback on the user's guess are updated, and a new `WriteLine` activity is added that provides additional information about the game once the number is guessed.</span></span>

#### <a name="to-update-the-statemachine-workflow"></a><a name="BKMK_UpdateStateMachine"></a> <span data-ttu-id="355ec-136">StateMachine iş akışını güncelleştirmek için</span><span class="sxs-lookup"><span data-stu-id="355ec-136">To update the StateMachine workflow</span></span>

1. <span data-ttu-id="355ec-137">**Çözüm Gezgini**, **NumberGuessWorkflowActivities** projesi altında **StateMachineNumberGuessWorkflow. xaml**' ye çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="355ec-137">In **Solution Explorer**, under the **NumberGuessWorkflowActivities** project, double-click **StateMachineNumberGuessWorkflow.xaml**.</span></span>

2. <span data-ttu-id="355ec-138">Durum makinesinde **tahmin yanlış** geçişi ' ne çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="355ec-138">Double-click the **Guess Incorrect** transition on the state machine.</span></span>

3. <span data-ttu-id="355ec-139">`Text`Etkinliğin en solundaki güncelleştirmeyi güncelleştirin `WriteLine` `If` .</span><span class="sxs-lookup"><span data-stu-id="355ec-139">Update the `Text` of the left-most `WriteLine` in the `If` activity.</span></span>

    ```vb
    Guess & " is too low."
    ```

    ```csharp
    Guess + " is too low."
    ```

4. <span data-ttu-id="355ec-140">`Text`Etkinliğin en sağdaki bölümünü güncelleştirin `WriteLine` `If` .</span><span class="sxs-lookup"><span data-stu-id="355ec-140">Update the `Text` of the right-most `WriteLine` in the `If` activity.</span></span>

    ```vb
    Guess & " is too high."
    ```

    ```csharp
    Guess + " is too high."
    ```

5. <span data-ttu-id="355ec-141">İş akışı Tasarımcısı ' nın en üstünde bulunan içerik haritası ' nda **StateMachine** ' e tıklayarak iş akışı tasarımcısında genel durum makinesi görünümüne geri dönün.</span><span class="sxs-lookup"><span data-stu-id="355ec-141">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>

6. <span data-ttu-id="355ec-142">Durum makinesinde **tahmin doğru** geçişi ' ne çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="355ec-142">Double-click the **Guess Correct** transition on the state machine.</span></span>

7. <span data-ttu-id="355ec-143">**Araç kutusu** ' nu **temel elemanlar** bölümünden bir **WriteLine** etkinliği sürükleyin ve **bırakma eylemi etkinliğine buraya** bırakın.</span><span class="sxs-lookup"><span data-stu-id="355ec-143">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it on the **Drop Action activity here** label of the transition.</span></span>

8. <span data-ttu-id="355ec-144">Özellik kutusuna aşağıdaki ifadeyi yazın `Text` .</span><span class="sxs-lookup"><span data-stu-id="355ec-144">Type the following expression into the `Text` property box.</span></span>

    ```vb
    Guess & " is correct. You guessed it in " & Turns & " turns."
    ```

    ```csharp
    Guess + " is correct. You guessed it in " + Turns + " turns."
    ```

#### <a name="to-update-the-flowchart-workflow"></a><a name="BKMK_UpdateFlowchart"></a> <span data-ttu-id="355ec-145">Akış çizelgesi iş akışını güncelleştirmek için</span><span class="sxs-lookup"><span data-stu-id="355ec-145">To update the Flowchart workflow</span></span>

1. <span data-ttu-id="355ec-146">**Çözüm Gezgini**, **NumberGuessWorkflowActivities** projesi altında **FlowchartNumberGuessWorkflow. xaml**' e çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="355ec-146">In **Solution Explorer**, under the **NumberGuessWorkflowActivities** project, double-click **FlowchartNumberGuessWorkflow.xaml**.</span></span>

2. <span data-ttu-id="355ec-147">`Text`En soldaki etkinliğin güncelleştirmesini güncelleştirin `WriteLine` .</span><span class="sxs-lookup"><span data-stu-id="355ec-147">Update the `Text` of the left-most `WriteLine` activity.</span></span>

    ```vb
    Guess & " is too low."
    ```

    ```csharp
    Guess + " is too low."
    ```

3. <span data-ttu-id="355ec-148">`Text`En sağdaki etkinliğin güncelleştirmesini güncelleştirin `WriteLine` .</span><span class="sxs-lookup"><span data-stu-id="355ec-148">Update the `Text` of the right-most `WriteLine` activity.</span></span>

    ```vb
    Guess & " is too high."
    ```

    ```csharp
    Guess + " is too high."
    ```

4. <span data-ttu-id="355ec-149">**Araç kutusu** ' nun **temel öğeler** bölümünden bir **WriteLine** etkinliğini sürükleyin ve `True` en üstteki eylemin bırakma noktasına bırakın `FlowDecision` .</span><span class="sxs-lookup"><span data-stu-id="355ec-149">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it on the drop point of the `True` action of the topmost `FlowDecision`.</span></span> <span data-ttu-id="355ec-150">`WriteLine`Etkinlik, akış çizelgesine eklenir ve `True` eylemine bağlanır `FlowDecision` .</span><span class="sxs-lookup"><span data-stu-id="355ec-150">The `WriteLine` activity is added to the flowchart and linked to the `True` action of the `FlowDecision`.</span></span>

5. <span data-ttu-id="355ec-151">Özellik kutusuna aşağıdaki ifadeyi yazın `Text` .</span><span class="sxs-lookup"><span data-stu-id="355ec-151">Type the following expression into the `Text` property box.</span></span>

    ```vb
    Guess & " is correct. You guessed it in " & Turns & " turns."
    ```

    ```csharp
    Guess + " is correct. You guessed it in " + Turns + " turns."
    ```

#### <a name="to-update-the-sequential-workflow"></a><a name="BKMK_UpdateSequential"></a> <span data-ttu-id="355ec-152">Sıralı iş akışını güncelleştirmek için</span><span class="sxs-lookup"><span data-stu-id="355ec-152">To update the Sequential workflow</span></span>

1. <span data-ttu-id="355ec-153">**Çözüm Gezgini**, **NumberGuessWorkflowActivities** projesi altında **SequentialNumberGuessWorkflow. xaml**' ye çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="355ec-153">In **Solution Explorer**, under the **NumberGuessWorkflowActivities** project, double-click **SequentialNumberGuessWorkflow.xaml**.</span></span>

2. <span data-ttu-id="355ec-154">`Text`Etkinliğin en solundaki güncelleştirmeyi güncelleştirin `WriteLine` `If` .</span><span class="sxs-lookup"><span data-stu-id="355ec-154">Update the `Text` of the left-most `WriteLine` in the `If` activity.</span></span>

    ```vb
    Guess & " is too low."
    ```

    ```csharp
    Guess + " is too low."
    ```

3. <span data-ttu-id="355ec-155">`Text`Etkinliğin en sağdaki `WriteLine` etkinliğini güncelleştirin `If` .</span><span class="sxs-lookup"><span data-stu-id="355ec-155">Update the `Text` of the right-most `WriteLine` activity in the `If` activity.</span></span>

    ```vb
    Guess & " is too high."
    ```

    ```csharp
    Guess + " is too high."
    ```

4. <span data-ttu-id="355ec-156">**Araç kutusunun** **temel elemanlar** bölümünden bir **WriteLine** etkinliğini sürükleyin ve **DoWhile** etkinliğinden sonra, **WriteLine** 'ın kök etkinliğinde son etkinlik olması için onu bırakın `Sequence` .</span><span class="sxs-lookup"><span data-stu-id="355ec-156">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it after the **DoWhile** activity so that the **WriteLine** is the final activity in the root `Sequence` activity.</span></span>

5. <span data-ttu-id="355ec-157">Özellik kutusuna aşağıdaki ifadeyi yazın `Text` .</span><span class="sxs-lookup"><span data-stu-id="355ec-157">Type the following expression into the `Text` property box.</span></span>

    ```vb
    Guess & " is correct. You guessed it in " & Turns & " turns."
    ```

    ```csharp
    Guess + " is correct. You guessed it in " + Turns + " turns."
    ```

### <a name="to-update-workflowversionmap-to-include-the-previous-workflow-versions"></a><a name="BKMK_UpdateWorkflowVersionMap"></a> <span data-ttu-id="355ec-158">WorkflowVersionMap 'i önceki iş akışı sürümlerini içerecek şekilde güncelleştirmek için</span><span class="sxs-lookup"><span data-stu-id="355ec-158">To update WorkflowVersionMap to include the previous workflow versions</span></span>

1. <span data-ttu-id="355ec-159"># **Guessworkflowwhost** projesi altındaki **WorkflowVersionMap.cs** (veya **WorkflowVersionMap. vb**) öğesine çift tıklayarak açın.</span><span class="sxs-lookup"><span data-stu-id="355ec-159">Double-click **WorkflowVersionMap.cs** (or **WorkflowVersionMap.vb**) under the **NumberGuessWorkflowHost** project to open it.</span></span>

2. <span data-ttu-id="355ec-160">Aşağıdaki `using` (veya `Imports` ) deyimlerini, diğer `using` (veya `Imports` ) deyimleriyle dosyanın en üstüne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="355ec-160">Add the following `using` (or `Imports`) statements to the top of the file with the other `using` (or `Imports`) statements.</span></span>

    ```vb
    Imports System.Reflection
    Imports System.IO
    ```

    ```csharp
    using System.Reflection;
    using System.IO;
    ```

3. <span data-ttu-id="355ec-161">Mevcut üç iş akışı kimlik bildiriminin hemen altına üç yeni iş akışı kimliği ekleyin.</span><span class="sxs-lookup"><span data-stu-id="355ec-161">Add three new workflow identities just below the three existing workflow identity declarations.</span></span> <span data-ttu-id="355ec-162">Bu yeni `v1` iş akışı kimlikleri, güncelleştirmeler yapılmadan önce başlatılan iş akışlarına doğru iş akışı tanımını sağlamak üzere kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="355ec-162">These new `v1` workflow identities will be used provide the correct workflow definition to workflows started before the updates were made.</span></span>

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

4. <span data-ttu-id="355ec-163">`WorkflowVersionMap`Oluşturucuda, `Version` üç geçerli iş akışı kimliği özelliğini ' e güncelleştirin `2.0.0.0` .</span><span class="sxs-lookup"><span data-stu-id="355ec-163">In the `WorkflowVersionMap` constructor, update the `Version` property of the three current workflow identities to `2.0.0.0`.</span></span>

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

    <span data-ttu-id="355ec-164">İçindeki iş akışlarının geçerli sürümlerini sözlüğe ekleyen kod, projede başvurulan geçerli sürümleri kullanır, bu nedenle iş akışı tanımlarını Başlatan kodun güncelleştirilmesine gerek kalmaz.</span><span class="sxs-lookup"><span data-stu-id="355ec-164">The code in that adds the current versions of the workflows to the dictionary uses the current versions that are referenced in the project, so the code that initializes the workflow definitions does not need to be updated.</span></span>

5. <span data-ttu-id="355ec-165">Aşağıdaki kodu, geçerli sürümleri sözlüğe ekleyen koddan hemen sonra oluşturucuya ekleyin.</span><span class="sxs-lookup"><span data-stu-id="355ec-165">Add the following code in the constructor just after the code that adds the current versions to the dictionary.</span></span>

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

    <span data-ttu-id="355ec-166">Bu iş akışı kimlikleri, karşılık gelen iş akışı tanımlarının başlangıç sürümleriyle ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="355ec-166">These workflow identities are associated with the initial versions of the corresponding workflow definitions.</span></span>

6. <span data-ttu-id="355ec-167">Sonra, iş akışı tanımlarının ilk sürümünü içeren derlemeyi yükleyin ve ilgili iş akışı tanımlarını oluşturun ve sözlüğe ekleyin.</span><span class="sxs-lookup"><span data-stu-id="355ec-167">Next, load the assembly that contains the initial version of the workflow definitions, and create and add the corresponding workflow definitions to the dictionary.</span></span>

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

    <span data-ttu-id="355ec-168">Aşağıdaki örnek, güncelleştirilmiş sınıfın tüm listesidir `WorkflowVersionMap` .</span><span class="sxs-lookup"><span data-stu-id="355ec-168">The following example is the complete listing for the updated `WorkflowVersionMap` class.</span></span>

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

### <a name="to-build-and-run-the-application"></a><a name="BKMK_BuildAndRun"></a> <span data-ttu-id="355ec-169">Uygulamayı derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="355ec-169">To build and run the application</span></span>

1. <span data-ttu-id="355ec-170">Uygulamayı derlemek için CTRL + SHIFT + B tuşlarına basın ve ardından başlatmak için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="355ec-170">Press CTRL+SHIFT+B to build the application, and then CTRL+F5 to start.</span></span>

2. <span data-ttu-id="355ec-171">Yeni **oyun**' i tıklatarak yeni bir iş akışı başlatın.</span><span class="sxs-lookup"><span data-stu-id="355ec-171">Start a new workflow by clicking **New Game**.</span></span> <span data-ttu-id="355ec-172">İş akışının sürümü durum penceresi altında görüntülenir ve güncelleştirilmiş sürümü ilişkili dosyadan yansıtır `WorkflowIdentity` .</span><span class="sxs-lookup"><span data-stu-id="355ec-172">The version of the workflow is displayed under the status window and reflects the updated version from the associated `WorkflowIdentity`.</span></span> <span data-ttu-id="355ec-173">`InstanceId`İşlem tamamlandığında iş akışı için izleme dosyasını görüntüleyebilmeniz ve ardından oyun tamamlanana kadar tahmin edilecek şekilde girmeniz için, ' yi bir yere göz önünde bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="355ec-173">Make a note of the `InstanceId` so you can view the tracking file for the workflow when it completes, and then enter guesses until the game is complete.</span></span> <span data-ttu-id="355ec-174">Kullanıcı tahminin, etkinliklerdeki güncelleştirmelere bağlı olarak durum penceresinde görünen bilgilere nasıl görüntülendiğini aklınızda yapın `WriteLine` .</span><span class="sxs-lookup"><span data-stu-id="355ec-174">Note how the user's guess is displayed in the information displayed in the status window based on the updates to the `WriteLine` activities.</span></span>

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
    > <span data-ttu-id="355ec-175">`WriteLine`Etkinliklerdeki güncelleştirilmiş metin görüntülenir, ancak `WriteLine` Bu konuya eklenen son etkinliğin çıktısı değildir.</span><span class="sxs-lookup"><span data-stu-id="355ec-175">The updated text from the `WriteLine` activities is displayed, but the output of the final `WriteLine` activity that was added in this topic is not.</span></span> <span data-ttu-id="355ec-176">Yani durum penceresi işleyici tarafından güncelleştirilir `PersistableIdle` .</span><span class="sxs-lookup"><span data-stu-id="355ec-176">That is because the status window is updated by the `PersistableIdle` handler.</span></span> <span data-ttu-id="355ec-177">İş akışı tamamlandığından ve son etkinlikten sonra boşta çalışmadığından, `PersistableIdle` işleyici çağrılmaz.</span><span class="sxs-lookup"><span data-stu-id="355ec-177">Because the workflow completes and does not go idle after the final activity, the `PersistableIdle` handler is not called.</span></span> <span data-ttu-id="355ec-178">Ancak, benzer bir ileti işleyicinin durum penceresinde görüntülenir `Completed` .</span><span class="sxs-lookup"><span data-stu-id="355ec-178">However, a similar message is displayed in the status window by the `Completed` handler.</span></span> <span data-ttu-id="355ec-179">İsterseniz, `Completed` metni öğesinden ayıklamak `StringWriter` ve durum penceresine göstermek için, kod işleyiciye eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="355ec-179">If desired, code could be added to the `Completed` handler to extract the text from the `StringWriter` and display it to the status window.</span></span>

3. <span data-ttu-id="355ec-180">Windows Gezgini 'ni açın ve **Numberguessworkflowwhost\bin\debug** klasörüne (veya proje ayarlarınıza bağlı olarak **bin\release** ) gidin ve tamamlanan Iş akışına karşılık gelen Not defteri 'ni kullanarak izleme dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="355ec-180">Open Windows Explorer and navigate to the **NumberGuessWorkflowHost\bin\debug** folder (or **bin\release** depending on your project settings) and open the tracking file using Notepad that corresponds to the completed workflow.</span></span> <span data-ttu-id="355ec-181">`InstanceId`' İ Not yapmadıysanız, Windows Gezgini 'nde **değiştirme tarihi** bilgilerini kullanarak doğru izleme dosyasını tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="355ec-181">If you did not make a note of the `InstanceId`, you can identify the correct tracking file by using the **Date modified** information in Windows Explorer.</span></span>

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

    <span data-ttu-id="355ec-182">Güncelleştirilmiş `WriteLine` çıktı, bu konuya eklenen öğesinin çıktısı da dahil olmak üzere izleme dosyası içinde yer alır `WriteLine` .</span><span class="sxs-lookup"><span data-stu-id="355ec-182">The updated `WriteLine` output is contained within the tracking file, including the output of the `WriteLine` that was added in this topic.</span></span>

4. <span data-ttu-id="355ec-183">Tahmin sayısı uygulamasına geri dönün ve güncelleştirmeler yapılmadan önce başlatılan iş akışlarından birini seçin.</span><span class="sxs-lookup"><span data-stu-id="355ec-183">Switch back to the number guessing application and select one of the workflows that was started before the updates were made.</span></span> <span data-ttu-id="355ec-184">Durum penceresinin altında görüntülenen sürüm bilgilerine bakarak şu anda seçili olan iş akışının sürümünü tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="355ec-184">You can identify the version of the currently selected workflow by looking at the version information that is displayed below the status window.</span></span> <span data-ttu-id="355ec-185">Bazı tahminler girin ve durum güncelleştirmelerinin `WriteLine` önceki sürümden gelen etkinlik çıkışıyla eşleştiğini ve kullanıcının tahminlerini dahil edileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="355ec-185">Enter some guesses and note that the status updates match the `WriteLine` activity output from the previous version, and do not include the user's guess.</span></span> <span data-ttu-id="355ec-186">Bunun nedeni, bu iş akışlarının güncelleştirmeleri olmayan önceki iş akışı tanımını kullanıyor olması `WriteLine` .</span><span class="sxs-lookup"><span data-stu-id="355ec-186">That is because these workflows are using the previous workflow definition that does not have the `WriteLine` updates.</span></span>

    <span data-ttu-id="355ec-187">Sonraki adımda, [nasıl yapılır: çalışan bir Iş akışı örneğinin tanımını güncelleştirme](how-to-update-the-definition-of-a-running-workflow-instance.md), çalışan `v1` iş akışı örnekleri, örnekler olarak yeni işlevleri içerecek şekilde güncelleştirilir `v2` .</span><span class="sxs-lookup"><span data-stu-id="355ec-187">In the next step, [How to: Update the Definition of a Running Workflow Instance](how-to-update-the-definition-of-a-running-workflow-instance.md), the running `v1` workflow instances are updated so they contain the new functionality as the `v2` instances.</span></span>
