---
description: 'Şu konuda daha fazla bilgi edinin: nasıl yapılır: çalışan bir Iş akışı örneğinin tanımını güncelleştirme'
title: 'Nasıl yapılır: Çalışan İş Akışı Örneğinin Tanımını Güncelleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 26dfac36-ae23-4909-9867-62495b55fb5e
ms.openlocfilehash: a3b1faa933cb79301946427823ef3e9f114823f5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631232"
---
# <a name="how-to-update-the-definition-of-a-running-workflow-instance"></a><span data-ttu-id="156fb-103">Nasıl yapılır: Çalışan İş Akışı Örneğinin Tanımını Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="156fb-103">How to: Update the Definition of a Running Workflow Instance</span></span>

<span data-ttu-id="156fb-104">Dinamik güncelleştirme, iş akışı uygulama geliştiricilerinin kalıcı bir iş akışı örneğinin iş akışı tanımını güncelleştirmesine yönelik bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="156fb-104">Dynamic update provides a mechanism for workflow application developers to update the workflow definition of a persisted workflow instance.</span></span> <span data-ttu-id="156fb-105">Gerekli değişiklik, hata düzeltmesini veya yeni gereksinimleri uygulayabilir ya da beklenmeyen değişikliklere uyum sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="156fb-105">The required change can be to implement a bug fix, new requirements, or to accommodate unexpected changes.</span></span> <span data-ttu-id="156fb-106">Öğreticideki Bu adım, `v1` [nasıl yapılır: bir Iş akışının birden çok sürümünü yan yana barındırma](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)bölümünde sunulan yeni işlevlerle eşleşecek şekilde tahmin iş akışının kalıcı örneklerini değiştirmek için dinamik güncelleştirme 'nin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="156fb-106">This step in the tutorial demonstrates how to use dynamic update to modify  persisted instances of the `v1` number guessing workflow to match the new functionality introduced in [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>

## <a name="in-this-topic"></a><span data-ttu-id="156fb-107">Bu konuda</span><span class="sxs-lookup"><span data-stu-id="156fb-107">In this topic</span></span>

- [<span data-ttu-id="156fb-108">CreateUpdateMaps projesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="156fb-108">To create the CreateUpdateMaps project</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_CreateProject)

- [<span data-ttu-id="156fb-109">StateMachineNumberGuessWorkflow öğesini güncelleştirmek için</span><span class="sxs-lookup"><span data-stu-id="156fb-109">To update StateMachineNumberGuessWorkflow</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_StateMachine)

- [<span data-ttu-id="156fb-110">FlowchartNumberGuessWorkflow öğesini güncelleştirmek için</span><span class="sxs-lookup"><span data-stu-id="156fb-110">To update FlowchartNumberGuessWorkflow</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_Flowchart)

- [<span data-ttu-id="156fb-111">SequentialNumberGuessWorkflow güncelleştirmek için</span><span class="sxs-lookup"><span data-stu-id="156fb-111">To update SequentialNumberGuessWorkflow</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_Sequential)

- [<span data-ttu-id="156fb-112">CreateUpdateMaps uygulamasını derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="156fb-112">To build and run the CreateUpdateMaps application</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_CreateUpdateMaps)

- [<span data-ttu-id="156fb-113">Güncelleştirilmiş iş akışı derlemesini derlemek için</span><span class="sxs-lookup"><span data-stu-id="156fb-113">To build the updated workflow assembly</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_BuildAssembly)

- [<span data-ttu-id="156fb-114">WorkflowVersionMap 'i yeni sürümlerle güncelleştirmek için</span><span class="sxs-lookup"><span data-stu-id="156fb-114">To update WorkflowVersionMap with the new versions</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_UpdateWorkflowVersionMap)

- [<span data-ttu-id="156fb-115">Dinamik güncelleştirmeleri uygulamak için</span><span class="sxs-lookup"><span data-stu-id="156fb-115">To apply the dynamic updates</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_ApplyUpdate)

- [<span data-ttu-id="156fb-116">Uygulamayı güncelleştirilmiş iş akışlarıyla çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="156fb-116">To run the application with the updated workflows</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_BuildAndRun)

- [<span data-ttu-id="156fb-117">İş akışlarının önceki sürümlerini başlatmayı etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="156fb-117">To enable starting previous versions of the workflows</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_StartPreviousVersions)

### <a name="to-create-the-createupdatemaps-project"></a><a name="BKMK_CreateProject"></a> <span data-ttu-id="156fb-118">CreateUpdateMaps projesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="156fb-118">To create the CreateUpdateMaps project</span></span>

1. <span data-ttu-id="156fb-119">**Çözüm Gezgini** 'de **WF45GettingStartedTutorial** öğesine sağ tıklayın ve **Ekle**, **Yeni proje** seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="156fb-119">Right-click **WF45GettingStartedTutorial** in **Solution Explorer** and choose **Add**, **New Project**.</span></span>

2. <span data-ttu-id="156fb-120">**Yüklü** düğümde, **Visual C#**, **Windows** (veya **Visual Basic**, **Windows**) öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="156fb-120">In the **Installed** node, select **Visual C#**, **Windows** (or **Visual Basic**, **Windows**).</span></span>

    > [!NOTE]
    > <span data-ttu-id="156fb-121">Visual Studio 'da birincil dil olarak yapılandırılmış programlama diline bağlı olarak, **Visual C#** veya **Visual Basic** düğümü **yüklü** düğümdeki **diğer diller** düğümü altında olabilir.</span><span class="sxs-lookup"><span data-stu-id="156fb-121">Depending on which programming language is configured as the primary language in Visual Studio, the **Visual C#** or **Visual Basic** node may be under the **Other Languages** node in the **Installed** node.</span></span>

     <span data-ttu-id="156fb-122">**.NET Framework 4,5** ' nin .NET Framework sürüm açılan listesinde seçildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="156fb-122">Ensure that **.NET Framework 4.5** is selected in the .NET Framework version drop-down list.</span></span> <span data-ttu-id="156fb-123">**Windows** listesinden **konsol uygulaması** ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="156fb-123">Select **Console Application** from the **Windows** list.</span></span> <span data-ttu-id="156fb-124">**Ad** kutusuna **Createupdatemaps** yazın ve **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="156fb-124">Type **CreateUpdateMaps** into the **Name** box and click **OK**.</span></span>

3. <span data-ttu-id="156fb-125">**Çözüm Gezgini** Içinde **Createupdatemaps** öğesine sağ tıklayın ve **Başvuru Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="156fb-125">Right-click **CreateUpdateMaps** in **Solution Explorer** and choose **Add Reference**.</span></span>

4. <span data-ttu-id="156fb-126">**Başvuru Ekle** listesinde **derlemeler** düğümünden **Framework** ' ü seçin.</span><span class="sxs-lookup"><span data-stu-id="156fb-126">Select **Framework** from the **Assemblies** node in the **Add Reference** list.</span></span> <span data-ttu-id="156fb-127">Derlemeleri filtrelemek ve istenen başvuruların seçimi daha kolay hale getirmek için, **arama derlemeler** kutusuna **System. Activities** yazın.</span><span class="sxs-lookup"><span data-stu-id="156fb-127">Type **System.Activities** into the **Search Assemblies** box to filter the assemblies and make the desired references easier to select.</span></span>

5. <span data-ttu-id="156fb-128">**Arama sonuçları** listesinden **System. Activities** öğesinin yanındaki onay kutusunu işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="156fb-128">Check the checkbox beside **System.Activities** from the **Search Results** list.</span></span>

6. <span data-ttu-id="156fb-129">**Derlemeleri ara** kutusuna **serileştirme** yazın ve **Arama sonuçları** listesinden **System. Runtime. Serialization** öğesinin yanındaki onay kutusunu işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="156fb-129">Type **Serialization** into the **Search Assemblies** box, and check the checkbox beside **System.Runtime.Serialization** from the **Search Results** list.</span></span>

7. <span data-ttu-id="156fb-130">**Derlemeleri ara** kutusuna **System. xaml** yazın ve **Arama sonuçları** listesinden **System. xaml** ' in yanındaki onay kutusunu işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="156fb-130">Type **System.Xaml** into the **Search Assemblies** box, and check the checkbox beside **System.Xaml** from the **Search Results** list.</span></span>

8. <span data-ttu-id="156fb-131">**Başvuru Yöneticisi** ' ni kapatmak ve başvuruları eklemek için **Tamam** ' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="156fb-131">Click **OK** to close **Reference Manager** and add the references.</span></span>

9. <span data-ttu-id="156fb-132">Aşağıdaki `using` (veya `Imports` ) deyimlerini, diğer `using` (veya `Imports` ) deyimleriyle dosyanın en üstüne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="156fb-132">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>

    ```vb
    Imports System.Activities
    Imports System.Activities.Statements
    Imports System.Xaml
    Imports System.Reflection
    Imports System.IO
    Imports System.Activities.XamlIntegration
    Imports System.Activities.DynamicUpdate
    Imports System.Runtime.Serialization
    Imports Microsoft.VisualBasic.Activities
    ```

    ```csharp
    using System.Activities;
    using System.Activities.Statements;
    using System.IO;
    using System.Xaml;
    using System.Reflection;
    using System.Activities.XamlIntegration;
    using System.Activities.DynamicUpdate;
    using System.Runtime.Serialization;
    using Microsoft.CSharp.Activities;
    ```

10. <span data-ttu-id="156fb-133">Aşağıdaki iki dize üyesini `Program` sınıfına ekleyin (veya `Module1` ).</span><span class="sxs-lookup"><span data-stu-id="156fb-133">Add the following two string members to the `Program` class (or `Module1`).</span></span>

    ```vb
    Const mapPath = "..\..\..\PreviousVersions"
    Const definitionPath = "..\..\..\NumberGuessWorkflowActivities_du"
    ```

    ```csharp
    const string mapPath = @"..\..\..\PreviousVersions";
    const string definitionPath = @"..\..\..\NumberGuessWorkflowActivities_du";
    ```

11. <span data-ttu-id="156fb-134">`StartUpdate`Sınıfına aşağıdaki yöntemi ekleyin `Program` (veya `Module1` ).</span><span class="sxs-lookup"><span data-stu-id="156fb-134">Add the following `StartUpdate` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="156fb-135">Bu yöntem, belirtilen XAML iş akışı tanımını bir öğesine yükler `ActivityBuilder` ve ardından çağırır `DynamicUpdate.PrepareForUpdate` .</span><span class="sxs-lookup"><span data-stu-id="156fb-135">This method loads up the specified xaml workflow definition into an `ActivityBuilder`, and then calls `DynamicUpdate.PrepareForUpdate`.</span></span> <span data-ttu-id="156fb-136">`PrepareForUpdate` içinde iş akışı tanımının bir kopyasını oluşturur `ActivityBuilder` .</span><span class="sxs-lookup"><span data-stu-id="156fb-136">`PrepareForUpdate` makes a copy of the workflow definition inside the `ActivityBuilder`.</span></span> <span data-ttu-id="156fb-137">İş akışı tanımı değiştirildikten sonra, bu kopya, güncelleştirme haritasını oluşturmak için değiştirilen iş akışı tanımıyla birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="156fb-137">After the workflow definition is modified, this copy is used along with the modified workflow definition to create the update map.</span></span>

    ```vb
    Private Function StartUpdate(name As String) As ActivityBuilder
        'Create the XamlXmlReaderSettings.
        Dim readerSettings As XamlReaderSettings = New XamlXmlReaderSettings()
        'In the XAML the "local" namespace refers to artifacts that come from
        'the same project as the XAML. When loading XAML if the currently executing
        'assembly is not the same assembly that was referred to as "local" in the XAML
        'LocalAssembly must be set to the assembly containing the artifacts.
        'Assembly.LoadFile requires an absolute path so convert this relative path
        'to an absolute path.
        readerSettings.LocalAssembly = Assembly.LoadFile(
            Path.GetFullPath(Path.Combine(mapPath, "NumberGuessWorkflowActivities_v1.dll")))

        Dim fullPath As String = Path.Combine(definitionPath, name)
        Dim xamlReader As XamlXmlReader = New XamlXmlReader(fullPath, readerSettings)

        'Load the workflow definition into an ActivityBuilder.
        Dim wf As ActivityBuilder = XamlServices.Load(
            ActivityXamlServices.CreateBuilderReader(xamlReader))

        'PrepareForUpdate makes a copy of the workflow definition in the
        'ActivityBuilder that is used for comparison when the update
        'map is created.
        DynamicUpdateServices.PrepareForUpdate(wf)

        Return wf
    End Function
    ```

    ```csharp
    private static ActivityBuilder StartUpdate(string name)
    {
        // Create the XamlXmlReaderSettings.
        XamlXmlReaderSettings readerSettings = new XamlXmlReaderSettings()
        {
            // In the XAML the "local" namespace refers to artifacts that come from
            // the same project as the XAML. When loading XAML if the currently executing
            // assembly is not the same assembly that was referred to as "local" in the XAML
            // LocalAssembly must be set to the assembly containing the artifacts.
            // Assembly.LoadFile requires an absolute path so convert this relative path
            // to an absolute path.
            LocalAssembly = Assembly.LoadFile(
                Path.GetFullPath(Path.Combine(mapPath, "NumberGuessWorkflowActivities_v1.dll")))
        };

        string path = Path.Combine(definitionPath, name);
        XamlXmlReader xamlReader = new XamlXmlReader(path, readerSettings);

        // Load the workflow definition into an ActivityBuilder.
        ActivityBuilder wf = XamlServices.Load(
            ActivityXamlServices.CreateBuilderReader(xamlReader))
            as ActivityBuilder;

        // PrepareForUpdate makes a copy of the workflow definition in the
        // ActivityBuilder that is used for comparison when the update
        // map is created.
        DynamicUpdateServices.PrepareForUpdate(wf);

        return wf;
    }
    ```

12. <span data-ttu-id="156fb-138">Sonra, aşağıdaki `CreateUpdateMethod` `Program` sınıfı (veya) sınıfına ekleyin `Module1` .</span><span class="sxs-lookup"><span data-stu-id="156fb-138">Next, add the following `CreateUpdateMethod` to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="156fb-139">Bu, DynamicUpdateServices. CreateUpdateMap 'i çağırarak dinamik bir güncelleştirme haritası oluşturur ve ardından belirtilen adı kullanarak güncelleştirme haritasını kaydeder.</span><span class="sxs-lookup"><span data-stu-id="156fb-139">This creates a dynamic update map by calling DynamicUpdateServices.CreateUpdateMap, and then saves the update map using the specified name.</span></span> <span data-ttu-id="156fb-140">Bu güncelleştirme eşlemesi, iş akışı çalışma zamanının, ' de bulunan özgün iş akışı tanımı kullanılarak başlatılan, `ActivityBuilder` güncelleştirilmiş iş akışı tanımını kullanarak tamamlanması için gereken bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="156fb-140">This update map contains the information needed by the workflow runtime to update a persisted workflow instance that was started using the original workflow definition contained in the `ActivityBuilder` so that it completes using the updated workflow definition.</span></span>

    ```vb
    Private Sub CreateUpdateMaps(wf As ActivityBuilder, name As String)
        'Create the UpdateMap.
        Dim map As DynamicUpdateMap =
            DynamicUpdateServices.CreateUpdateMap(wf)

        'Serialize it to a file.
        Dim mapFullPath As String = Path.Combine(mapPath, name)
        Dim sz As DataContractSerializer = New DataContractSerializer(GetType(DynamicUpdateMap))
        Using fs As FileStream = File.Open(mapFullPath, FileMode.Create)
            sz.WriteObject(fs, map)
        End Using
    End Sub
    ```

    ```csharp
    private static void CreateUpdateMaps(ActivityBuilder wf, string name)
    {
        // Create the UpdateMap.
        DynamicUpdateMap map =
            DynamicUpdateServices.CreateUpdateMap(wf);

        // Serialize it to a file.
        string path = Path.Combine(mapPath, name);
        DataContractSerializer sz = new DataContractSerializer(typeof(DynamicUpdateMap));
        using (FileStream fs = System.IO.File.Open(path, FileMode.Create))
        {
            sz.WriteObject(fs, map);
        }
    }
    ```

13. <span data-ttu-id="156fb-141">`SaveUpdatedDefinition`Sınıfına aşağıdaki yöntemi ekleyin `Program` (veya `Module1` ).</span><span class="sxs-lookup"><span data-stu-id="156fb-141">Add the following `SaveUpdatedDefinition` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="156fb-142">Bu yöntem, güncelleştirme haritası oluşturulduktan sonra güncelleştirilmiş iş akışı tanımını kaydeder.</span><span class="sxs-lookup"><span data-stu-id="156fb-142">This method saves the updated workflow definition once the update map is created.</span></span>

    ```vb
    Private Sub SaveUpdatedDefinition(wf As ActivityBuilder, name As String)
        Dim xamlPath As String = Path.Combine(definitionPath, name)
        Dim sw As StreamWriter = File.CreateText(xamlPath)
        Dim xw As XamlWriter = ActivityXamlServices.CreateBuilderWriter(
            New XamlXmlWriter(sw, New XamlSchemaContext()))
        XamlServices.Save(xw, wf)
        sw.Close()
    End Sub
    ```

    ```csharp
    private static void SaveUpdatedDefinition(ActivityBuilder wf, string name)
    {
        string xamlPath = Path.Combine(definitionPath, name);
        StreamWriter sw = File.CreateText(xamlPath);
        XamlWriter xw = ActivityXamlServices.CreateBuilderWriter(
            new XamlXmlWriter(sw, new XamlSchemaContext()));
        XamlServices.Save(xw, wf);
        sw.Close();
    }
    ```

### <a name="to-update-statemachinenumberguessworkflow"></a><a name="BKMK_StateMachine"></a> <span data-ttu-id="156fb-143">StateMachineNumberGuessWorkflow öğesini güncelleştirmek için</span><span class="sxs-lookup"><span data-stu-id="156fb-143">To update StateMachineNumberGuessWorkflow</span></span>

1. <span data-ttu-id="156fb-144">Sınıfına bir ekleyin `CreateStateMachineUpdateMap` `Program` (veya `Module1` ).</span><span class="sxs-lookup"><span data-stu-id="156fb-144">Add a `CreateStateMachineUpdateMap` to the `Program` class (or `Module1`).</span></span>

    ```vb
    Private Sub CreateStateMachineUpdateMap()

    End Sub
    ```

    ```csharp
    private static void CreateStateMachineUpdateMap()
    {
    }
    ```

2. <span data-ttu-id="156fb-145">Bir çağrısı yapıp `StartUpdate` iş akışının kök etkinliğine bir başvuru alın `StateMachine` .</span><span class="sxs-lookup"><span data-stu-id="156fb-145">Make a call to `StartUpdate` and then get a reference to the root `StateMachine` activity of the workflow.</span></span>

    ```vb
    Dim wf As ActivityBuilder = StartUpdate("StateMachineNumberGuessWorkflow.xaml")

    'Get a reference to the root StateMachine activity.
    Dim sm As StateMachine = wf.Implementation
    ```

    ```csharp
    ActivityBuilder wf = StartUpdate("StateMachineNumberGuessWorkflow.xaml");

    // Get a reference to the root StateMachine activity.
    StateMachine sm = wf.Implementation as StateMachine;
    ```

3. <span data-ttu-id="156fb-146">Ardından, `WriteLine` kullanıcının tahmininin çok yüksek veya çok düşük olduğunu görüntüleyen iki etkinliğin ifadelerini güncelleştirin; böylece [bir Iş akışının birden çok sürümünü yan yana barındırma](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span><span class="sxs-lookup"><span data-stu-id="156fb-146">Next, update the expressions of the two `WriteLine` activities that display whether the user's guess is too high or too low so that they match the updates made in [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>

    ```vb
    'Update the Text of the two WriteLine activities that write the
    'results of the user's guess. They are contained in the workflow as the
    'Then and Else action of the If activity in sm.States[1].Transitions[1].Action.
    Dim guessLow As Statements.If = sm.States(1).Transitions(1).Action

    'Update the "too low" message.
    Dim tooLow As WriteLine = guessLow.Then
    tooLow.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too low.""")

    'Update the "too high" message.
    Dim tooHigh As WriteLine = guessLow.Else
    tooHigh.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too high.""")
    ```

    ```csharp
    // Update the Text of the two WriteLine activities that write the
    // results of the user's guess. They are contained in the workflow as the
    // Then and Else action of the If activity in sm.States[1].Transitions[1].Action.
    If guessLow = sm.States[1].Transitions[1].Action as If;

    // Update the "too low" message.
    WriteLine tooLow = guessLow.Then as WriteLine;
    tooLow.Text = new CSharpValue<string>("Guess.ToString() + \" is too low.\"");

    // Update the "too high" message.
    WriteLine tooHigh = guessLow.Else as WriteLine;
    tooHigh.Text = new CSharpValue<string>("Guess.ToString() + \" is too high.\"");
    ```

4. <span data-ttu-id="156fb-147">Ardından, `WriteLine` Kapanış iletisini görüntüleyen yeni etkinliği ekleyin.</span><span class="sxs-lookup"><span data-stu-id="156fb-147">Next, add the new `WriteLine` activity that displays the closing message.</span></span>

    ```vb
    'Create the new WriteLine that displays the closing message.
    Dim wl As New WriteLine() With
    {
        .Text = New VisualBasicValue(Of String) _
            ("Guess.ToString() + "" is correct. You guessed it in "" & Turns.ToString() & "" turns.""")
    }

    'Add it as the Action for the Guess Correct transition. The Guess Correct
    'transition is the first transition of States[1]. The transitions are listed
    'at the bottom of the State activity designer.
    sm.States(1).Transitions(0).Action = wl
    ```

    ```csharp
    // Create the new WriteLine that displays the closing message.
    WriteLine wl = new WriteLine
    {
        Text = new CSharpValue<string>("Guess.ToString() + \" is correct. You guessed it in \" + Turns.ToString() + \" turns.\"")
    };

    // Add it as the Action for the Guess Correct transition. The Guess Correct
    // transition is the first transition of States[1]. The transitions are listed
    // at the bottom of the State activity designer.
    sm.States[1].Transitions[0].Action = wl;
    ```

5. <span data-ttu-id="156fb-148">İş akışı güncelleştirildikten sonra `CreateUpdateMaps` ve çağırın `SaveUpdatedDefinition` .</span><span class="sxs-lookup"><span data-stu-id="156fb-148">After the workflow is updated, call `CreateUpdateMaps` and `SaveUpdatedDefinition`.</span></span> <span data-ttu-id="156fb-149">`CreateUpdateMaps` oluşturup kaydeder ve `DynamicUpdateMap` `SaveUpdatedDefinition` güncelleştirilmiş iş akışı tanımını kaydeder.</span><span class="sxs-lookup"><span data-stu-id="156fb-149">`CreateUpdateMaps` creates and saves the `DynamicUpdateMap`, and `SaveUpdatedDefinition` saves the updated workflow definition.</span></span>

    ```vb
    'Create the update map.
    CreateUpdateMaps(wf, "StateMachineNumberGuessWorkflow.map")

    'Save the updated workflow definition.
    SaveUpdatedDefinition(wf, "StateMachineNumberGuessWorkflow_du.xaml")
    ```

    ```csharp
    // Create the update map.
    CreateUpdateMaps(wf, "StateMachineNumberGuessWorkflow.map");

    // Save the updated workflow definition.
    SaveUpdatedDefinition(wf, "StateMachineNumberGuessWorkflow_du.xaml");
    ```

    <span data-ttu-id="156fb-150">Aşağıdaki örnek, tamamlanmış `CreateStateMachineUpdateMap` yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="156fb-150">The following example is the completed `CreateStateMachineUpdateMap` method.</span></span>

    ```vb
    Private Sub CreateStateMachineUpdateMap()
        Dim wf As ActivityBuilder = StartUpdate("StateMachineNumberGuessWorkflow.xaml")

        'Get a reference to the root StateMachine activity.
        Dim sm As StateMachine = wf.Implementation

        'Update the Text of the two WriteLine activities that write the
        'results of the user's guess. They are contained in the workflow as the
        'Then and Else action of the If activity in sm.States[1].Transitions[1].Action.
        Dim guessLow As Statements.If = sm.States(1).Transitions(1).Action

        'Update the "too low" message.
        Dim tooLow As WriteLine = guessLow.Then
        tooLow.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too low.""")

        'Update the "too high" message.
        Dim tooHigh As WriteLine = guessLow.Else
        tooHigh.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too high.""")

        'Create the new WriteLine that displays the closing message.
        Dim wl As New WriteLine() With
        {
            .Text = New VisualBasicValue(Of String) _
                ("Guess.ToString() + "" is correct. You guessed it in "" & Turns.ToString() & "" turns.""")
        }

        'Add it as the Action for the Guess Correct transition. The Guess Correct
        'transition is the first transition of States[1]. The transitions are listed
        'at the bottom of the State activity designer.
        sm.States(1).Transitions(0).Action = wl

        'Create the update map.
        CreateUpdateMaps(wf, "StateMachineNumberGuessWorkflow.map")

        'Save the updated workflow definition.
        SaveUpdatedDefinition(wf, "StateMachineNumberGuessWorkflow_du.xaml")
    End Sub
    ```

    ```csharp
    private static void CreateStateMachineUpdateMap()
    {
        ActivityBuilder wf = StartUpdate("StateMachineNumberGuessWorkflow.xaml");

        // Get a reference to the root StateMachine activity.
        StateMachine sm = wf.Implementation as StateMachine;

        // Update the Text of the two WriteLine activities that write the
        // results of the user's guess. They are contained in the workflow as the
        // Then and Else action of the If activity in sm.States[1].Transitions[1].Action.
        If guessLow = sm.States[1].Transitions[1].Action as If;

        // Update the "too low" message.
        WriteLine tooLow = guessLow.Then as WriteLine;
        tooLow.Text = new CSharpValue<string>("Guess.ToString() + \" is too low.\"");

        // Update the "too high" message.
        WriteLine tooHigh = guessLow.Else as WriteLine;
        tooHigh.Text = new CSharpValue<string>("Guess.ToString() + \" is too high.\"");

        // Create the new WriteLine that displays the closing message.
        WriteLine wl = new WriteLine
        {
            Text = new CSharpValue<string>("Guess.ToString() + \" is correct. You guessed it in \" + Turns.ToString() + \" turns.\"")
        };

        // Add it as the Action for the Guess Correct transition. The Guess Correct
        // transition is the first transition of States[1]. The transitions are listed
        // at the bottom of the State activity designer.
        sm.States[1].Transitions[0].Action = wl;

        // Create the update map.
        CreateUpdateMaps(wf, "StateMachineNumberGuessWorkflow.map");

        // Save the updated workflow definition.
        SaveUpdatedDefinition(wf, "StateMachineNumberGuessWorkflow_du.xaml");
    }
    ```

### <a name="to-update-flowchartnumberguessworkflow"></a><a name="BKMK_Flowchart"></a> <span data-ttu-id="156fb-151">FlowchartNumberGuessWorkflow öğesini güncelleştirmek için</span><span class="sxs-lookup"><span data-stu-id="156fb-151">To update FlowchartNumberGuessWorkflow</span></span>

1. <span data-ttu-id="156fb-152">Sınıfına aşağıdakileri ekleyin `CreateFlowchartUpdateMethod` `Program` (veya `Module1` ).</span><span class="sxs-lookup"><span data-stu-id="156fb-152">Add the following `CreateFlowchartUpdateMethod` to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="156fb-153">Bu yöntem öğesine benzerdir `CreateStateMachineUpdateMap` .</span><span class="sxs-lookup"><span data-stu-id="156fb-153">This method is similar to `CreateStateMachineUpdateMap`.</span></span> <span data-ttu-id="156fb-154">Bir çağrısıyla başlar `StartUpdate` , akış çizelgesi tanımını güncelleştirir ve güncelleştirme haritasını ve güncelleştirilmiş iş akışı tanımını kaydederek sonlanır.</span><span class="sxs-lookup"><span data-stu-id="156fb-154">It starts with a call to `StartUpdate`, updates the flowchart workflow definition, and finishes by saving the update map and the updated workflow definition.</span></span>

    ```vb
    Private Sub CreateFlowchartUpdateMap()
        Dim wf As ActivityBuilder = StartUpdate("FlowchartNumberGuessWorkflow.xaml")

        'Get a reference to the root Flowchart activity.
        Dim fc As Flowchart = wf.Implementation

        'Update the Text of the two WriteLine activities that write the
        'results of the user's guess. They are contained in the workflow as the
        'True and False action of the "Guess < Target" FlowDecision, which is
        'Nodes[4].
        Dim guessLow As FlowDecision = fc.Nodes(4)

        'Update the "too low" message.
        Dim trueStep As FlowStep = guessLow.True
        Dim tooLow As WriteLine = trueStep.Action
        tooLow.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too low.""")

        'Update the "too high" message.
        Dim falseStep As FlowStep = guessLow.False
        Dim tooHigh As WriteLine = falseStep.Action
        tooHigh.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too high.""")

        'Create the new WriteLine that displays the closing message.
        Dim wl As New WriteLine() With
        {
            .Text = New VisualBasicValue(Of String) _
                ("Guess.ToString() + "" is correct. You guessed it in "" & Turns.ToString() & "" turns.""")
        }

        'Create a FlowStep to hold the WriteLine.
        Dim closingStep As New FlowStep() With
        {
            .Action = wl
        }

        'Add this new FlowStep to the True action of the
        '"Guess = Guess" FlowDecision
        Dim guessCorrect As FlowDecision = fc.Nodes(3)
        guessCorrect.True = closingStep

        'Add the new FlowStep to the Nodes collection.
        'If closingStep was replacing an existing node then
        'we would need to remove that Step from the collection.
        'In this example there was no existing True step to remove.
        fc.Nodes.Add(closingStep)

        'Create the update map.
        CreateUpdateMaps(wf, "FlowchartNumberGuessWorkflow.map")

        'Save the updated workflow definition.
        SaveUpdatedDefinition(wf, "FlowchartNumberGuessWorkflow_du.xaml")
    End Sub
    ```

    ```csharp
    private static void CreateFlowchartUpdateMap()
    {
        ActivityBuilder wf = StartUpdate("FlowchartNumberGuessWorkflow.xaml");

        // Get a reference to the root Flowchart activity.
        Flowchart fc = wf.Implementation as Flowchart;

        // Update the Text of the two WriteLine activities that write the
        // results of the user's guess. They are contained in the workflow as the
        // True and False action of the "Guess < Target" FlowDecision, which is
        // Nodes[4].
        FlowDecision guessLow = fc.Nodes[4] as FlowDecision;

        // Update the "too low" message.
        FlowStep trueStep = guessLow.True as FlowStep;
        WriteLine tooLow = trueStep.Action as WriteLine;
        tooLow.Text = new CSharpValue<string>("Guess.ToString() + \" is too low.\"");

        // Update the "too high" message.
        FlowStep falseStep = guessLow.False as FlowStep;
        WriteLine tooHigh = falseStep.Action as WriteLine;
        tooHigh.Text = new CSharpValue<string>("Guess.ToString() + \" is too high.\"");

        // Add the new WriteLine that displays the closing message.
        WriteLine wl = new WriteLine
        {
            Text = new CSharpValue<string>("Guess.ToString() + \" is correct. You guessed it in \" + Turns.ToString() + \" turns.\"")
        };

        // Create a FlowStep to hold the WriteLine.
        FlowStep closingStep = new FlowStep
        {
            Action = wl
        };

        // Add this new FlowStep to the True action of the
        // "Guess == Guess" FlowDecision
        FlowDecision guessCorrect = fc.Nodes[3] as FlowDecision;
        guessCorrect.True = closingStep;

        // Add the new FlowStep to the Nodes collection.
        // If closingStep was replacing an existing node then
        // we would need to remove that Step from the collection.
        // In this example there was no existing True step to remove.
        fc.Nodes.Add(closingStep);

        // Create the update map.
        CreateUpdateMaps(wf, "FlowchartNumberGuessWorkflow.map");

        //  Save the updated workflow definition.
        SaveUpdatedDefinition(wf, "FlowchartNumberGuessWorkflow_du.xaml");
    }
    ```

### <a name="to-update-sequentialnumberguessworkflow"></a><a name="BKMK_Sequential"></a> <span data-ttu-id="156fb-155">SequentialNumberGuessWorkflow güncelleştirmek için</span><span class="sxs-lookup"><span data-stu-id="156fb-155">To update SequentialNumberGuessWorkflow</span></span>

1. <span data-ttu-id="156fb-156">Sınıfına aşağıdakileri ekleyin `CreateSequentialUpdateMethod` `Program` (veya `Module1` ).</span><span class="sxs-lookup"><span data-stu-id="156fb-156">Add the following `CreateSequentialUpdateMethod` to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="156fb-157">Bu yöntem, diğer iki yönteme benzer.</span><span class="sxs-lookup"><span data-stu-id="156fb-157">This method is similar to the other two methods.</span></span> <span data-ttu-id="156fb-158">Bir çağrısıyla başlar `StartUpdate` , sıralı iş akışı tanımını güncelleştirir ve güncelleştirme haritasını ve güncelleştirilmiş iş akışı tanımını kaydederek tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="156fb-158">It starts with a call to `StartUpdate`, updates the sequential workflow definition, and finishes by saving the update map and the updated workflow definition.</span></span>

    ```vb
    Private Sub CreateSequentialUpdateMap()
        Dim wf As ActivityBuilder = StartUpdate("SequentialNumberGuessWorkflow.xaml")

        'Get a reference to the root activity in the workflow.
        Dim rootSequence As Sequence = wf.Implementation

        'Update the Text of the two WriteLine activities that write the
        'results of the user's guess. They are contained in the workflow as the
        'Then and Else action of the "Guess < Target" If activity.
        'Sequence[1]->DoWhile->Body->Sequence[2]->If->Then->If
        Dim gameLoop As Statements.DoWhile = rootSequence.Activities(1)
        Dim gameBody As Sequence = gameLoop.Body
        Dim guessCorrect As Statements.If = gameBody.Activities(2)
        Dim guessLow As Statements.If = guessCorrect.Then
        Dim tooLow As WriteLine = guessLow.Then
        tooLow.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too low.""")
        Dim tooHigh As WriteLine = guessLow.Else
        tooHigh.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too high.""")

        'Create the new WriteLine that displays the closing message.
        Dim wl As New WriteLine() With
        {
            .Text = New VisualBasicValue(Of String) _
                ("Guess.ToString() + "" is correct. You guessed it in "" & Turns.ToString() & "" turns.""")
        }

        'Insert it as the third activity in the root sequence
        rootSequence.Activities.Insert(2, wl)

        'Create the update map.
        CreateUpdateMaps(wf, "SequentialNumberGuessWorkflow.map")

        'Save the updated workflow definition.
        SaveUpdatedDefinition(wf, "SequentialNumberGuessWorkflow_du.xaml")
    End Sub
    ```

    ```csharp
    private static void CreateSequentialUpdateMap()
    {
        ActivityBuilder wf = StartUpdate("SequentialNumberGuessWorkflow.xaml");

        // Get a reference to the root activity in the workflow.
        Sequence rootSequence = wf.Implementation as Sequence;

        // Update the Text of the two WriteLine activities that write the
        // results of the user's guess. They are contained in the workflow as the
        // Then and Else action of the "Guess < Target" If activity.
        // Sequence[1]->DoWhile->Body->Sequence[2]->If->Then->If
        DoWhile gameLoop = rootSequence.Activities[1] as DoWhile;
        Sequence gameBody = gameLoop.Body as Sequence;
        If guessCorrect = gameBody.Activities[2] as If;
        If guessLow = guessCorrect.Then as If;
        WriteLine tooLow = guessLow.Then as WriteLine;
        tooLow.Text = new CSharpValue<string>("Guess.ToString() + \" is too low.\"");
        WriteLine tooHigh = guessLow.Else as WriteLine;
        tooHigh.Text = new CSharpValue<string>("Guess.ToString() + \" is too high.\"");

        // Add the new WriteLine that displays the closing message.
        WriteLine wl = new WriteLine
        {
            Text = new CSharpValue<string>("Guess.ToString() + \" is correct. You guessed it in \" + Turns.ToString() + \" turns.\"")
        };

        // Insert it as the third activity in the root sequence
        rootSequence.Activities.Insert(2, wl);

        // Create the update map.
        CreateUpdateMaps(wf, "SequentialNumberGuessWorkflow.map");

        // Save the updated workflow definition.
        SaveUpdatedDefinition(wf, "SequentialNumberGuessWorkflow_du.xaml");
    }
    ```

### <a name="to-build-and-run-the-createupdatemaps-application"></a><a name="BKMK_CreateUpdateMaps"></a> <span data-ttu-id="156fb-159">CreateUpdateMaps uygulamasını derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="156fb-159">To build and run the CreateUpdateMaps application</span></span>

1. <span data-ttu-id="156fb-160">Yöntemini güncelleştirin `Main` ve aşağıdaki üç yöntem çağrılarını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="156fb-160">Update the `Main` method and add the following three method calls.</span></span> <span data-ttu-id="156fb-161">Bu yöntemler aşağıdaki bölümlere eklenir.</span><span class="sxs-lookup"><span data-stu-id="156fb-161">These methods are added in the following sections.</span></span> <span data-ttu-id="156fb-162">Her yöntem, ilgili tahmin iş akışını güncelleştirir ve `DynamicUpdateMap` güncelleştirmeleri açıklayan bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="156fb-162">Each method updates the corresponding number guess workflow and creates a `DynamicUpdateMap` that describes the updates.</span></span>

    ```vb
    Sub Main()
        'Create the update maps for the changes needed to the v1 activities
        'so they match the v2 activities.
        CreateSequentialUpdateMap()
        CreateFlowchartUpdateMap()
        CreateStateMachineUpdateMap()
    End Sub
    ```

    ```csharp
    static void Main(string[] args)
    {
        // Create the update maps for the changes needed to the v1 activities
        // so they match the v2 activities.
        CreateSequentialUpdateMap();
        CreateFlowchartUpdateMap();
        CreateStateMachineUpdateMap();
    }
    ```

2. <span data-ttu-id="156fb-163">**Çözüm Gezgini** Içinde **Createupdatemaps** öğesine sağ tıklayın ve **Başlangıç projesi olarak ayarla**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="156fb-163">Right-click **CreateUpdateMaps** in **Solution Explorer** and choose **Set as StartUp Project**.</span></span>

3. <span data-ttu-id="156fb-164">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın ve ardından uygulamayı çalıştırmak için CTRL + F5 tuşlarına basın `CreateUpdateMaps` .</span><span class="sxs-lookup"><span data-stu-id="156fb-164">Press CTRL+SHIFT+B to build the solution, and then CTRL+F5 to run the `CreateUpdateMaps` application.</span></span>

    > [!NOTE]
    > <span data-ttu-id="156fb-165">`CreateUpdateMaps`Uygulama çalışırken herhangi bir durum bilgisi görüntülemez, ancak **NumberGuessWorkflowActivities_du** klasörüne ve **PreviousVersions** klasörüne bakarsanız, güncelleştirilmiş iş akışı tanım dosyalarını ve güncelleştirme haritalarını görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="156fb-165">The `CreateUpdateMaps` application does not display any status information while running, but if you look in the **NumberGuessWorkflowActivities_du** folder and the **PreviousVersions** folder you will see the updated workflow definition files and the update maps.</span></span>

    <span data-ttu-id="156fb-166">Güncelleştirme haritaları oluşturulduktan ve iş akışı tanımları güncelleştirildikten sonra, bir sonraki adım güncelleştirilmiş tanımları içeren güncelleştirilmiş bir iş akışı derlemesi oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="156fb-166">Once the update maps are created and the workflow definitions updated, the next step is to build an updated workflow assembly containing the updated definitions.</span></span>

### <a name="to-build-the-updated-workflow-assembly"></a><a name="BKMK_BuildAssembly"></a> <span data-ttu-id="156fb-167">Güncelleştirilmiş iş akışı derlemesini derlemek için</span><span class="sxs-lookup"><span data-stu-id="156fb-167">To build the updated workflow assembly</span></span>

1. <span data-ttu-id="156fb-168">Visual Studio 2012 'nin ikinci bir örneğini açın.</span><span class="sxs-lookup"><span data-stu-id="156fb-168">Open a second instance of Visual Studio 2012.</span></span>

2. <span data-ttu-id="156fb-169">**Dosya** menüsünden **Aç**, **Proje/çözüm** öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="156fb-169">Choose **Open**, **Project/Solution** from the **File** menu.</span></span>

3. <span data-ttu-id="156fb-170">[Nasıl yapılır: bir Iş akışının birden çok sürümünü yan yana barındırma](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)bölümünde oluşturduğunuz **NumberGuessWorkflowActivities_du** klasöre gidin, **NumberGuessWorkflowActivities. csproj** (veya **vbproj**) öğesini seçin ve **Aç**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="156fb-170">Navigate to the **NumberGuessWorkflowActivities_du** folder you created in [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md), select **NumberGuessWorkflowActivities.csproj** (or **vbproj**), and click **Open**.</span></span>

4. <span data-ttu-id="156fb-171">**Çözüm Gezgini**' de, **SequentialNumberGuessWorkflow. xaml** ' e sağ tıklayıp **projeden çıkar**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="156fb-171">In **Solution Explorer**, right click **SequentialNumberGuessWorkflow.xaml** and choose **Exclude From Project**.</span></span> <span data-ttu-id="156fb-172">**FlowchartNumberGuessWorkflow. xaml** ve **StateMachineNumberGuessWorkflow. xaml** için aynı şeyi yapın.</span><span class="sxs-lookup"><span data-stu-id="156fb-172">Do the same thing for **FlowchartNumberGuessWorkflow.xaml** and **StateMachineNumberGuessWorkflow.xaml**.</span></span> <span data-ttu-id="156fb-173">Bu adım, iş akışı tanımlarının önceki sürümlerini projeden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="156fb-173">This step removes the previous versions of the workflow definitions from the project.</span></span>

5. <span data-ttu-id="156fb-174">**Proje** menüsünden **Varolan öğe Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="156fb-174">Choose **Add Existing Item** from the **Project** menu.</span></span>

6. <span data-ttu-id="156fb-175">[Nasıl yapılır: bir Iş akışının birden çok sürümünü yan yana barındırma](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)bölümünde oluşturduğunuz **NumberGuessWorkflowActivities_du** klasöre gidin.</span><span class="sxs-lookup"><span data-stu-id="156fb-175">Navigate to the **NumberGuessWorkflowActivities_du** folder you created in [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>

7. <span data-ttu-id="156fb-176">**XAML dosyaları ( \* . xaml;) seçin \* . xoml)** açılır listesinden **dosya yazın** .</span><span class="sxs-lookup"><span data-stu-id="156fb-176">Choose **XAML Files (\*.xaml;\*.xoml)** from the **Files of type** drop-down list.</span></span>

8. <span data-ttu-id="156fb-177">**SequentialNumberGuessWorkflow_du. xaml**, **FlowchartNumberGuessWorkflow_du. xaml** ve **StateMachineNumberGuessWorkflow_du. xaml** ' i seçin ve **Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="156fb-177">Select **SequentialNumberGuessWorkflow_du.xaml**, **FlowchartNumberGuessWorkflow_du.xaml**, and **StateMachineNumberGuessWorkflow_du.xaml** and click **Add**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="156fb-178">Tek seferde birden çok öğe seçmek için CTRL + tıklama.</span><span class="sxs-lookup"><span data-stu-id="156fb-178">CTRL+Click to select multiple items at a time.</span></span>

    <span data-ttu-id="156fb-179">Bu adım, iş akışı tanımlarının güncelleştirilmiş sürümlerini projeye ekler.</span><span class="sxs-lookup"><span data-stu-id="156fb-179">This step adds the updated versions of the workflow definitions to the project.</span></span>

9. <span data-ttu-id="156fb-180">Projeyi oluşturmak için CTRL+SHIFT+B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="156fb-180">Press CTRL+SHIFT+B to build the project.</span></span>

10. <span data-ttu-id="156fb-181">**Dosya** menüsünden **çözümü kapat** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="156fb-181">Choose **Close Solution** from the **File** menu.</span></span> <span data-ttu-id="156fb-182">Projenin çözüm dosyası gerekli değildir, bu nedenle Visual Studio 'Yu bir çözüm dosyası kaydetmeden kapatmak için **Hayır** ' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="156fb-182">A solution file for the project is not required, so click **No** to close Visual Studio without saving a solution file.</span></span> <span data-ttu-id="156fb-183">Visual Studio 'Yu kapatmak için **Dosya** menüsünden **Çıkış** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="156fb-183">Choose **Exit** from the **File** menu to close Visual Studio.</span></span>

11. <span data-ttu-id="156fb-184">Windows Gezgini 'ni açın ve **NumberGuessWorkflowActivities_du \bin\Debug** klasörüne (veya proje ayarlarınıza bağlı olarak **bin\release** ) gidin.</span><span class="sxs-lookup"><span data-stu-id="156fb-184">Open Windows Explorer and navigate to the **NumberGuessWorkflowActivities_du\bin\Debug** folder (or **bin\Release** depending on your project settings).</span></span>

12. <span data-ttu-id="156fb-185">**NumberGuessWorkflowActivities.dll** **NumberGuessWorkflowActivities_v15.dll** olarak yeniden adlandırın ve bunu [nasıl yapılır: bir iş akışının birden çok sürümünü yan yana barındırma](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)bölümünde oluşturduğunuz **PreviousVersions** klasörüne kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="156fb-185">Rename **NumberGuessWorkflowActivities.dll** to **NumberGuessWorkflowActivities_v15.dll**, and copy it to the **PreviousVersions** folder you created in [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>

### <a name="to-update-workflowversionmap-with-the-new-versions"></a><a name="BKMK_UpdateWorkflowVersionMap"></a> <span data-ttu-id="156fb-186">WorkflowVersionMap 'i yeni sürümlerle güncelleştirmek için</span><span class="sxs-lookup"><span data-stu-id="156fb-186">To update WorkflowVersionMap with the new versions</span></span>

1. <span data-ttu-id="156fb-187">Visual Studio 2012 ' in ilk örneğine dönün.</span><span class="sxs-lookup"><span data-stu-id="156fb-187">Switch back to the initial instance of Visual Studio 2012.</span></span>

2. <span data-ttu-id="156fb-188"># **Guessworkflowwhost** projesi altındaki **WorkflowVersionMap.cs** (veya **WorkflowVersionMap. vb**) öğesine çift tıklayarak açın.</span><span class="sxs-lookup"><span data-stu-id="156fb-188">Double-click **WorkflowVersionMap.cs** (or **WorkflowVersionMap.vb**) under the **NumberGuessWorkflowHost** project to open it.</span></span>

3. <span data-ttu-id="156fb-189">Mevcut altı iş akışı kimlik bildiriminin hemen altına üç yeni iş akışı kimliği ekleyin.</span><span class="sxs-lookup"><span data-stu-id="156fb-189">Add three new workflow identities just below the six existing workflow identity declarations.</span></span> <span data-ttu-id="156fb-190">Bu öğreticide, `1.5.0.0` `WorkflowIdentity.Version` dinamik güncelleştirme kimlikleri için olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="156fb-190">In this tutorial, `1.5.0.0` is used as the `WorkflowIdentity.Version` for the dynamic update identities.</span></span> <span data-ttu-id="156fb-191">Bu yeni `v15` iş akışı kimlikleri, dinamik olarak güncellenen kalıcı iş akışı örnekleri için doğru iş akışı tanımını sağlamak üzere kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="156fb-191">These new `v15` workflow identities will be used provide the correct workflow definition for the dynamically updated persisted workflow instances.</span></span>

    ```vb
    'Current version identities.
    Public StateMachineNumberGuessIdentity As WorkflowIdentity
    Public FlowchartNumberGuessIdentity As WorkflowIdentity
    Public SequentialNumberGuessIdentity As WorkflowIdentity

    'v1 identities.
    Public StateMachineNumberGuessIdentity_v1 As WorkflowIdentity
    Public FlowchartNumberGuessIdentity_v1 As WorkflowIdentity
    Public SequentialNumberGuessIdentity_v1 As WorkflowIdentity

    'v1.5 (Dynamic Update) identities.
    Public StateMachineNumberGuessIdentity_v15 As WorkflowIdentity
    Public FlowchartNumberGuessIdentity_v15 As WorkflowIdentity
    Public SequentialNumberGuessIdentity_v15 As WorkflowIdentity
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

    // v1.5 (Dynamic Update) identities.
    static public WorkflowIdentity StateMachineNumberGuessIdentity_v15;
    static public WorkflowIdentity FlowchartNumberGuessIdentity_v15;
    static public WorkflowIdentity SequentialNumberGuessIdentity_v15;
    ```

4. <span data-ttu-id="156fb-192">Oluşturucunun sonuna aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="156fb-192">Add the following code at the end of the constructor.</span></span> <span data-ttu-id="156fb-193">Bu kod, dinamik güncelleştirme iş akışı kimliklerini başlatır, karşılık gelen iş akışı tanımlarını yükler ve bunları iş akışı sürüm sözlüğüne ekler.</span><span class="sxs-lookup"><span data-stu-id="156fb-193">This code initializes the dynamic update workflow identities, loads the corresponding workflow definitions, and adds them to the workflow version dictionary.</span></span>

    ```vb
    'Initialize the dynamic update workflow identities.
    StateMachineNumberGuessIdentity_v15 = New WorkflowIdentity With
    {
        .Name = "StateMachineNumberGuessWorkflow",
        .Version = New Version(1, 5, 0, 0)
    }

    FlowchartNumberGuessIdentity_v15 = New WorkflowIdentity With
    {
        .Name = "FlowchartNumberGuessWorkflow",
        .Version = New Version(1, 5, 0, 0)
    }

    SequentialNumberGuessIdentity_v15 = New WorkflowIdentity With
    {
        .Name = "SequentialNumberGuessWorkflow",
        .Version = New Version(1, 5, 0, 0)
    }

    'Add the dynamic update workflow identities to the dictionary along with
    'the corresponding workflow definitions loaded from the v15 assembly.
    'Assembly.LoadFile requires an absolute path so convert this relative path
    'to an absolute path.
    Dim v15AssemblyPath As String = "..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v15.dll"
    v15AssemblyPath = Path.GetFullPath(v15AssemblyPath)
    Dim v15Assembly As Assembly = Assembly.LoadFile(v15AssemblyPath)

    map.Add(StateMachineNumberGuessIdentity_v15,
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow"))

    map.Add(SequentialNumberGuessIdentity_v15,
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow"))

    map.Add(FlowchartNumberGuessIdentity_v15,
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow"))
    ```

    ```csharp
    // Initialize the dynamic update workflow identities.
    StateMachineNumberGuessIdentity_v15 = new WorkflowIdentity
    {
        Name = "StateMachineNumberGuessWorkflow",
        Version = new Version(1, 5, 0, 0)
    };

    FlowchartNumberGuessIdentity_v15 = new WorkflowIdentity
    {
        Name = "FlowchartNumberGuessWorkflow",
        Version = new Version(1, 5, 0, 0)
    };

    SequentialNumberGuessIdentity_v15 = new WorkflowIdentity
    {
        Name = "SequentialNumberGuessWorkflow",
        Version = new Version(1, 5, 0, 0)
    };

    // Add the dynamic update workflow identities to the dictionary along with
    // the corresponding workflow definitions loaded from the v15 assembly.
    // Assembly.LoadFile requires an absolute path so convert this relative path
    // to an absolute path.
    string v15AssemblyPath = @"..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v15.dll";
    v15AssemblyPath = Path.GetFullPath(v15AssemblyPath);
    Assembly v15Assembly = Assembly.LoadFile(v15AssemblyPath);

    map.Add(StateMachineNumberGuessIdentity_v15,
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow") as Activity);

    map.Add(SequentialNumberGuessIdentity_v15,
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow") as Activity);

    map.Add(FlowchartNumberGuessIdentity_v15,
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow") as Activity);
    ```

     <span data-ttu-id="156fb-194">Aşağıdaki örnek tamamlanan `WorkflowVersionMap` sınıftır.</span><span class="sxs-lookup"><span data-stu-id="156fb-194">The following example is the completed `WorkflowVersionMap` class.</span></span>

    ```vb
    Public Module WorkflowVersionMap
        Dim map As Dictionary(Of WorkflowIdentity, Activity)

        'Current version identities.
        Public StateMachineNumberGuessIdentity As WorkflowIdentity
        Public FlowchartNumberGuessIdentity As WorkflowIdentity
        Public SequentialNumberGuessIdentity As WorkflowIdentity

        'v1 identities.
        Public StateMachineNumberGuessIdentity_v1 As WorkflowIdentity
        Public FlowchartNumberGuessIdentity_v1 As WorkflowIdentity
        Public SequentialNumberGuessIdentity_v1 As WorkflowIdentity

        'v1.5 (Dynamic Update) identities.
        Public StateMachineNumberGuessIdentity_v15 As WorkflowIdentity
        Public FlowchartNumberGuessIdentity_v15 As WorkflowIdentity
        Public SequentialNumberGuessIdentity_v15 As WorkflowIdentity

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

            'Initialize the dynamic update workflow identities.
            StateMachineNumberGuessIdentity_v15 = New WorkflowIdentity With
            {
                .Name = "StateMachineNumberGuessWorkflow",
                .Version = New Version(1, 5, 0, 0)
            }

            FlowchartNumberGuessIdentity_v15 = New WorkflowIdentity With
            {
                .Name = "FlowchartNumberGuessWorkflow",
                .Version = New Version(1, 5, 0, 0)
            }

            SequentialNumberGuessIdentity_v15 = New WorkflowIdentity With
            {
                .Name = "SequentialNumberGuessWorkflow",
                .Version = New Version(1, 5, 0, 0)
            }

            'Add the dynamic update workflow identities to the dictionary along with
            'the corresponding workflow definitions loaded from the v15 assembly.
            'Assembly.LoadFile requires an absolute path so convert this relative path
            'to an absolute path.
            Dim v15AssemblyPath As String = "..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v15.dll"
            v15AssemblyPath = Path.GetFullPath(v15AssemblyPath)
            Dim v15Assembly As Assembly = Assembly.LoadFile(v15AssemblyPath)

            map.Add(StateMachineNumberGuessIdentity_v15,
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow"))

            map.Add(SequentialNumberGuessIdentity_v15,
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow"))

            map.Add(FlowchartNumberGuessIdentity_v15,
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow"))
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

        // v1.5 (Dynamic Update) identities.
        static public WorkflowIdentity StateMachineNumberGuessIdentity_v15;
        static public WorkflowIdentity FlowchartNumberGuessIdentity_v15;
        static public WorkflowIdentity SequentialNumberGuessIdentity_v15;

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

            // Initialize the dynamic update workflow identities.
            StateMachineNumberGuessIdentity_v15 = new WorkflowIdentity
            {
                Name = "StateMachineNumberGuessWorkflow",
                Version = new Version(1, 5, 0, 0)
            };

            FlowchartNumberGuessIdentity_v15 = new WorkflowIdentity
            {
                Name = "FlowchartNumberGuessWorkflow",
                Version = new Version(1, 5, 0, 0)
            };

            SequentialNumberGuessIdentity_v15 = new WorkflowIdentity
            {
                Name = "SequentialNumberGuessWorkflow",
                Version = new Version(1, 5, 0, 0)
            };

            // Add the dynamic update workflow identities to the dictionary along with
            // the corresponding workflow definitions loaded from the v15 assembly.
            // Assembly.LoadFile requires an absolute path so convert this relative path
            // to an absolute path.
            string v15AssemblyPath = @"..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v15.dll";
            v15AssemblyPath = Path.GetFullPath(v15AssemblyPath);
            Assembly v15Assembly = Assembly.LoadFile(v15AssemblyPath);

            map.Add(StateMachineNumberGuessIdentity_v15,
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow") as Activity);

            map.Add(SequentialNumberGuessIdentity_v15,
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow") as Activity);

            map.Add(FlowchartNumberGuessIdentity_v15,
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow") as Activity);
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

5. <span data-ttu-id="156fb-195">Projeyi oluşturmak için CTRL+SHIFT+B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="156fb-195">Press CTRL+SHIFT+B to build the project.</span></span>

### <a name="to-apply-the-dynamic-updates"></a><a name="BKMK_ApplyUpdate"></a> <span data-ttu-id="156fb-196">Dinamik güncelleştirmeleri uygulamak için</span><span class="sxs-lookup"><span data-stu-id="156fb-196">To apply the dynamic updates</span></span>

1. <span data-ttu-id="156fb-197">**Çözüm Gezgini** 'de **WF45GettingStartedTutorial** öğesine sağ tıklayın ve **Ekle**, **Yeni proje** seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="156fb-197">Right-click **WF45GettingStartedTutorial** in **Solution Explorer** and choose **Add**, **New Project**.</span></span>

2. <span data-ttu-id="156fb-198">**Yüklü** düğümde, **Visual C#**, **Windows** (veya **Visual Basic**, **Windows**) öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="156fb-198">In the **Installed** node, select **Visual C#**, **Windows** (or **Visual Basic**, **Windows**).</span></span>

    > [!NOTE]
    > <span data-ttu-id="156fb-199">Visual Studio 'da birincil dil olarak yapılandırılmış programlama diline bağlı olarak, **Visual C#** veya **Visual Basic** düğümü **yüklü** düğümdeki **diğer diller** düğümü altında olabilir.</span><span class="sxs-lookup"><span data-stu-id="156fb-199">Depending on which programming language is configured as the primary language in Visual Studio, the **Visual C#** or **Visual Basic** node may be under the **Other Languages** node in the **Installed** node.</span></span>

    <span data-ttu-id="156fb-200">**.NET Framework 4,5** ' nin .NET Framework sürüm açılan listesinde seçildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="156fb-200">Ensure that **.NET Framework 4.5** is selected in the .NET Framework version drop-down list.</span></span> <span data-ttu-id="156fb-201">**Windows** listesinden **konsol uygulaması** ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="156fb-201">Select **Console Application** from the **Windows** list.</span></span> <span data-ttu-id="156fb-202">**Ad** kutusuna **applydynamicupdate** yazın ve **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="156fb-202">Type **ApplyDynamicUpdate** into the **Name** box and click **OK**.</span></span>

3. <span data-ttu-id="156fb-203">**Çözüm Gezgini** Içinde **applydynamicupdate** öğesine sağ tıklayın ve **Başvuru Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="156fb-203">Right-click **ApplyDynamicUpdate** in **Solution Explorer** and choose **Add Reference**.</span></span>

4. <span data-ttu-id="156fb-204">**Çözüm** ' e tıklayın ve **Numberguessworkflowwhost**' nin yanındaki kutuyu işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="156fb-204">Click **Solution** and check the box next to **NumberGuessWorkflowHost**.</span></span> <span data-ttu-id="156fb-205">Bu başvuru `ApplyDynamicUpdate` , sınıfını kullanabilmeniz için gereklidir `NumberGuessWorkflowHost.WorkflowVersionMap` .</span><span class="sxs-lookup"><span data-stu-id="156fb-205">This reference is needed so that `ApplyDynamicUpdate` can use the `NumberGuessWorkflowHost.WorkflowVersionMap` class.</span></span>

5. <span data-ttu-id="156fb-206">**Başvuru Ekle** listesinde **derlemeler** düğümünden **Framework** ' ü seçin.</span><span class="sxs-lookup"><span data-stu-id="156fb-206">Select **Framework** from the **Assemblies** node in the **Add Reference** list.</span></span> <span data-ttu-id="156fb-207">**System. Activities** öğesini **arama derlemeler** kutusuna yazın.</span><span class="sxs-lookup"><span data-stu-id="156fb-207">Type **System.Activities** into the **Search Assemblies** box.</span></span> <span data-ttu-id="156fb-208">Bu, derlemeleri filtreleyecek ve istenen başvuruların seçimi daha kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="156fb-208">This will filter the assemblies and make the desired references easier to select.</span></span>

6. <span data-ttu-id="156fb-209">**Arama sonuçları** listesinden **System. Activities** öğesinin yanındaki onay kutusunu işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="156fb-209">Check the checkbox beside **System.Activities** from the **Search Results** list.</span></span>

7. <span data-ttu-id="156fb-210">**Derlemeleri ara** kutusuna **serileştirme** yazın ve **Arama sonuçları** listesinden **System. Runtime. Serialization** öğesinin yanındaki onay kutusunu işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="156fb-210">Type **Serialization** into the **Search Assemblies** box, and check the checkbox beside **System.Runtime.Serialization** from the **Search Results** list.</span></span>

8. <span data-ttu-id="156fb-211">**Arama derlemeleri** kutusuna **durableörneklemesini** yazın ve **Arama sonuçları** listesinden **System. Activities. Durableörnekınlist** ve **System. Runtime. durableörnek** ' in yanındaki onay kutusunu işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="156fb-211">Type **DurableInstancing** into the **Search Assemblies** box, and check the checkbox beside **System.Activities.DurableInstancing** and **System.Runtime.DurableInstancing** from the **Search Results** list.</span></span>

9. <span data-ttu-id="156fb-212">**Başvuru Yöneticisi** ' ni kapatmak ve başvuruları eklemek için **Tamam** ' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="156fb-212">Click **OK** to close **Reference Manager** and add the references.</span></span>

10. <span data-ttu-id="156fb-213">Çözüm Gezgini içinde **Applydynamicupdate** öğesine sağ tıklayın ve **Ekle**, **sınıf**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="156fb-213">Right-click **ApplyDynamicUpdate** in Solution Explorer and choose **Add**, **Class**.</span></span> <span data-ttu-id="156fb-214">`DynamicUpdateInfo` **Ad** kutusuna yazın ve **Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="156fb-214">Type `DynamicUpdateInfo` into the **Name** box and click **Add**.</span></span>

11. <span data-ttu-id="156fb-215">Aşağıdaki iki üyeyi `DynamicUpdateInfo` sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="156fb-215">Add the following two members to the `DynamicUpdateInfo` class.</span></span> <span data-ttu-id="156fb-216">Aşağıdaki örnek tamamlanan `DynamicUpdateInfo` sınıftır.</span><span class="sxs-lookup"><span data-stu-id="156fb-216">The following example is the completed `DynamicUpdateInfo` class.</span></span> <span data-ttu-id="156fb-217">Bu sınıf, bir iş akışı örneği güncelleştirilirken kullanılan güncelleştirme haritası ve yeni iş akışı kimliği hakkındaki bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="156fb-217">This class contains information on the update map and new workflow identity used when a workflow instance is updated.</span></span>

    ```vb
    Public Class DynamicUpdateInfo
        Public updateMap As DynamicUpdateMap
        Public newIdentity As WorkflowIdentity
    End Class
    ```

    ```csharp
    class DynamicUpdateInfo
    {
        public DynamicUpdateMap updateMap;
        public WorkflowIdentity newIdentity;
    }
    ```

12. <span data-ttu-id="156fb-218">Aşağıdaki `using` (veya `Imports` ) deyimlerini, diğer `using` (veya `Imports` ) deyimleriyle dosyanın en üstüne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="156fb-218">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>

    ```vb
    Imports System.Activities
    Imports System.Activities.DynamicUpdate
    ```

    ```csharp
    using System.Activities;
    using System.Activities.DynamicUpdate;
    ```

13. <span data-ttu-id="156fb-219">Çözüm Gezgini içinde **program.cs** (veya **Module1. vb**) öğesine çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="156fb-219">Double-click **Program.cs** (or **Module1.vb**) in Solution Explorer.</span></span>

14. <span data-ttu-id="156fb-220">Aşağıdaki `using` (veya `Imports` ) deyimlerini, diğer `using` (veya `Imports` ) deyimleriyle dosyanın en üstüne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="156fb-220">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>

    ```vb
    Imports NumberGuessWorkflowHost
    Imports System.Data.SqlClient
    Imports System.Activities.DynamicUpdate
    Imports System.IO
    Imports System.Runtime.Serialization
    Imports System.Activities
    Imports System.Activities.DurableInstancing
    ```

    ```csharp
    using NumberGuessWorkflowHost;
    using System.Data;
    using System.Data.SqlClient;
    using System.Activities;
    using System.Activities.DynamicUpdate;
    using System.IO;
    using System.Runtime.Serialization;
    using System.Activities.DurableInstancing;
    ```

15. <span data-ttu-id="156fb-221">Aşağıdaki bağlantı dizesi üyesini `Program` sınıfına ekleyin (veya `Module1` ).</span><span class="sxs-lookup"><span data-stu-id="156fb-221">Add the following connection string member to the `Program` class (or `Module1`).</span></span>

    ```vb
    Const connectionString = "Server=.\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI"
    ```

    ```csharp
    const string connectionString = "Server=.\\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI";
    ```

    > [!NOTE]
    > <span data-ttu-id="156fb-222">SQL Server sürümüne bağlı olarak, bağlantı dizesi sunucu adı farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="156fb-222">Depending on your edition of SQL Server, the connection string server name may be different.</span></span>

16. <span data-ttu-id="156fb-223">`GetIDs`Sınıfına aşağıdaki yöntemi ekleyin `Program` (veya `Module1` ).</span><span class="sxs-lookup"><span data-stu-id="156fb-223">Add the following `GetIDs` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="156fb-224">Bu yöntem, kalıcı iş akışı örnek kimliklerinin bir listesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="156fb-224">This method returns a list of persisted workflow instance ids.</span></span>

    ```vb
    Function GetIds() As IList(Of Guid)
        Dim Ids As New List(Of Guid)
        Dim localCmd = _
            String.Format("Select [InstanceId] from [System.Activities.DurableInstancing].[Instances] Order By [CreationTime]")
        Using localCon = New SqlConnection(connectionString)
            Dim cmd As SqlCommand = localCon.CreateCommand()
            cmd.CommandText = localCmd
            localCon.Open()
            Using reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)
                While reader.Read()
                    'Get the InstanceId of the persisted Workflow
                    Dim id As Guid = Guid.Parse(reader(0).ToString())

                    'Add it to the list.
                    Ids.Add(id)
                End While
            End Using
        End Using

        Return Ids
    End Function
    ```

    ```csharp
    static IList<Guid> GetIds()
    {
        List<Guid> Ids = new List<Guid>();
        string localCmd = string.Format("Select [InstanceId] from [System.Activities.DurableInstancing].[Instances] Order By [CreationTime]");
        using (SqlConnection localCon = new SqlConnection(connectionString))
        {
            SqlCommand cmd = localCon.CreateCommand();
            cmd.CommandText = localCmd;
            localCon.Open();
            using (SqlDataReader reader = cmd.ExecuteReader(CommandBehavior.CloseConnection))
            {
                while (reader.Read())
                {
                    // Get the InstanceId of the persisted Workflow
                    Guid id = Guid.Parse(reader[0].ToString());

                    // Add it to the list.
                    Ids.Add(id);
                }
            }
        }

        return Ids;
    }
    ```

17. <span data-ttu-id="156fb-225">`LoadMap`Sınıfına aşağıdaki yöntemi ekleyin `Program` (veya `Module1` ).</span><span class="sxs-lookup"><span data-stu-id="156fb-225">Add the following `LoadMap` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="156fb-226">Bu yöntem, `v1` iş akışı kimliklerini güncelleştirme haritaları ile eşleyen bir sözlük ve ilgili kalıcı iş akışı örneklerini güncelleştirmek için kullanılan yeni iş akışı kimliklerini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="156fb-226">This method creates a dictionary that maps `v1` workflow identities to the update maps and new workflow identities used to update the corresponding persisted workflow instances.</span></span>

    ```vb
    Function LoadMap(mapName As String) As DynamicUpdateMap
        Dim mapPath As String = Path.Combine("..\..\..\PreviousVersions", mapName)

        Dim map As DynamicUpdateMap
        Using fs As FileStream = File.Open(mapPath, FileMode.Open)
            Dim serializer As DataContractSerializer = New DataContractSerializer(GetType(DynamicUpdateMap))
            Dim updateMap = serializer.ReadObject(fs)
            If updateMap Is Nothing Then
                Throw New ApplicationException("DynamicUpdateMap is null.")
            End If

            map = updateMap
        End Using

        Return map
    End Function
    ```

    ```csharp
    static DynamicUpdateMap LoadMap(string mapName)
    {
        string path = Path.Combine(@"..\..\..\PreviousVersions", mapName);

        DynamicUpdateMap map;
        using (FileStream fs = File.Open(path, FileMode.Open))
        {
            DataContractSerializer serializer = new DataContractSerializer(typeof(DynamicUpdateMap));
            object updateMap = serializer.ReadObject(fs);
            if (updateMap == null)
            {
                throw new ApplicationException("DynamicUpdateMap is null.");
            }

            map = updateMap as DynamicUpdateMap;
        }

        return map;
    }
    ```

18. <span data-ttu-id="156fb-227">`LoadMaps`Sınıfına aşağıdaki yöntemi ekleyin `Program` (veya `Module1` ).</span><span class="sxs-lookup"><span data-stu-id="156fb-227">Add the following `LoadMaps` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="156fb-228">Bu yöntem, üç güncelleştirme haritalarını yükler ve `v1` iş akışı kimliklerini güncelleştirme eşlemeleriyle eşleyen bir sözlük oluşturur.</span><span class="sxs-lookup"><span data-stu-id="156fb-228">This method loads the three update maps and creates a dictionary that maps `v1` workflow identities to the update maps.</span></span>

    ```vb
    Function LoadMaps() As IDictionary(Of WorkflowIdentity, DynamicUpdateInfo)
        'There are 3 update maps to describe the changes to update v1 workflows,
        'one for reach of the 3 workflow types in the tutorial.
        Dim maps = New Dictionary(Of WorkflowIdentity, DynamicUpdateInfo)()

        Dim sequentialMap As DynamicUpdateMap = LoadMap("SequentialNumberGuessWorkflow.map")
        Dim sequentialInfo = New DynamicUpdateInfo With
        {
            .updateMap = sequentialMap,
            .newIdentity = WorkflowVersionMap.SequentialNumberGuessIdentity_v15
        }
        maps.Add(WorkflowVersionMap.SequentialNumberGuessIdentity_v1, sequentialInfo)

        Dim stateMap As DynamicUpdateMap = LoadMap("StateMachineNumberGuessWorkflow.map")
        Dim stateInfo = New DynamicUpdateInfo With
        {
            .updateMap = stateMap,
            .newIdentity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v15
        }
        maps.Add(WorkflowVersionMap.StateMachineNumberGuessIdentity_v1, stateInfo)

        Dim flowchartMap As DynamicUpdateMap = LoadMap("FlowchartNumberGuessWorkflow.map")
        Dim flowchartInfo = New DynamicUpdateInfo With
        {
            .updateMap = flowchartMap,
            .newIdentity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v15
        }
        maps.Add(WorkflowVersionMap.FlowchartNumberGuessIdentity_v1, flowchartInfo)

        Return maps
    End Function
    ```

    ```csharp
    static IDictionary<WorkflowIdentity, DynamicUpdateInfo> LoadMaps()
    {
        // There are 3 update maps to describe the changes to update v1 workflows,
        // one for reach of the 3 workflow types in the tutorial.
        Dictionary<WorkflowIdentity, DynamicUpdateInfo> maps =
            new Dictionary<WorkflowIdentity, DynamicUpdateInfo>();

        DynamicUpdateMap sequentialMap = LoadMap("SequentialNumberGuessWorkflow.map");
        DynamicUpdateInfo sequentialInfo = new DynamicUpdateInfo
        {
            updateMap = sequentialMap,
            newIdentity = WorkflowVersionMap.SequentialNumberGuessIdentity_v15
        };
        maps.Add(WorkflowVersionMap.SequentialNumberGuessIdentity_v1, sequentialInfo);

        DynamicUpdateMap stateMap = LoadMap("StateMachineNumberGuessWorkflow.map");
        DynamicUpdateInfo stateInfo = new DynamicUpdateInfo
        {
            updateMap = stateMap,
            newIdentity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v15
        };
        maps.Add(WorkflowVersionMap.StateMachineNumberGuessIdentity_v1, stateInfo);

        DynamicUpdateMap flowchartMap = LoadMap("FlowchartNumberGuessWorkflow.map");
        DynamicUpdateInfo flowchartInfo = new DynamicUpdateInfo
        {
            updateMap = flowchartMap,
            newIdentity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v15
        };
        maps.Add(WorkflowVersionMap.FlowchartNumberGuessIdentity_v1, flowchartInfo);

        return maps;
    }
    ```

19. <span data-ttu-id="156fb-229">Aşağıdaki kodu `Main` içine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="156fb-229">Add the following code to `Main`.</span></span> <span data-ttu-id="156fb-230">Bu kod kalıcı iş akışı örneklerini yineler ve her bir inceler `WorkflowIdentity` .</span><span class="sxs-lookup"><span data-stu-id="156fb-230">This code iterates the persisted workflow instances and examines each `WorkflowIdentity`.</span></span> <span data-ttu-id="156fb-231">Bir `WorkflowIdentity` `v1` iş akışı örneğiyle eşleniyorsa, `WorkflowApplication` güncelleştirilmiş iş akışı tanımıyla ve güncelleştirilmiş iş akışı kimliğiyle yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="156fb-231">If the `WorkflowIdentity` maps to a `v1` workflow instance, a `WorkflowApplication` is configured with the updated workflow definition and an updated workflow identity.</span></span> <span data-ttu-id="156fb-232">Ardından, `WorkflowApplication.Load` örneği ve güncelleştirme haritası ile çağırılır ve bu, dinamik güncelleştirme haritasını uygular.</span><span class="sxs-lookup"><span data-stu-id="156fb-232">Next, `WorkflowApplication.Load` is called with the instance and the update map, which applies the dynamic update map.</span></span> <span data-ttu-id="156fb-233">Güncelleştirme uygulandıktan sonra, güncelleştirilmiş örnek öğesine çağrısıyla kalıcı hale getirilir `Unload` .</span><span class="sxs-lookup"><span data-stu-id="156fb-233">Once the update is applied, the updated instance is persisted with a call to `Unload`.</span></span>

    ```vb
    Dim store = New SqlWorkflowInstanceStore(connectionString)
    WorkflowApplication.CreateDefaultInstanceOwner(store, Nothing, WorkflowIdentityFilter.Any)

    Dim updateMaps As IDictionary(Of WorkflowIdentity, DynamicUpdateInfo) = LoadMaps()

    For Each id As Guid In GetIds()
        'Get a proxy to the instance.
        Dim instance As WorkflowApplicationInstance = WorkflowApplication.GetInstance(id, store)

        Console.WriteLine("Inspecting: {0}", instance.DefinitionIdentity)

        'Only update v1 workflows.
        If Not instance.DefinitionIdentity Is Nothing AndAlso _
            instance.DefinitionIdentity.Version.Equals(New Version(1, 0, 0, 0)) Then

            Dim info As DynamicUpdateInfo = updateMaps(instance.DefinitionIdentity)

            'Associate the persisted WorkflowApplicationInstance with
            'a WorkflowApplication that is configured with the updated
            'definition and updated WorkflowIdentity.
            Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(info.newIdentity)
            Dim wfApp = New WorkflowApplication(wf, info.newIdentity)

            'Apply the Dynamic Update.
            wfApp.Load(instance, info.updateMap)

            'Persist the updated instance.
            wfApp.Unload()

            Console.WriteLine("Updated to: {0}", info.newIdentity)
        Else
            'Not updating this instance, so unload it.
            instance.Abandon()
        End If
    Next
    ```

    ```csharp
    SqlWorkflowInstanceStore store = new SqlWorkflowInstanceStore(connectionString);
    WorkflowApplication.CreateDefaultInstanceOwner(store, null, WorkflowIdentityFilter.Any);

    IDictionary<WorkflowIdentity, DynamicUpdateInfo> updateMaps = LoadMaps();

    foreach (Guid id in GetIds())
    {
        // Get a proxy to the instance.
        WorkflowApplicationInstance instance =
            WorkflowApplication.GetInstance(id, store);

        Console.WriteLine("Inspecting: {0}", instance.DefinitionIdentity);

        // Only update v1 workflows.
        if (instance.DefinitionIdentity != null &&
            instance.DefinitionIdentity.Version.Equals(new Version(1, 0, 0, 0)))
        {
            DynamicUpdateInfo info = updateMaps[instance.DefinitionIdentity];

            // Associate the persisted WorkflowApplicationInstance with
            // a WorkflowApplication that is configured with the updated
            // definition and updated WorkflowIdentity.
            Activity wf = WorkflowVersionMap.GetWorkflowDefinition(info.newIdentity);
            WorkflowApplication wfApp =
                new WorkflowApplication(wf, info.newIdentity);

            // Apply the Dynamic Update.
            wfApp.Load(instance, info.updateMap);

            // Persist the updated instance.
            wfApp.Unload();

            Console.WriteLine("Updated to: {0}", info.newIdentity);
        }
        else
        {
            // Not updating this instance, so unload it.
            instance.Abandon();
        }
    }
    ```

20. <span data-ttu-id="156fb-234">**Çözüm Gezgini** Için **applydynamicupdate** öğesine sağ tıklayın ve **Başlangıç projesi olarak ayarla**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="156fb-234">Right-click **ApplyDynamicUpdate** in **Solution Explorer** and choose **Set as StartUp Project**.</span></span>

21. <span data-ttu-id="156fb-235">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın ve ardından `ApplyDynamicUpdate` uygulamayı çalıştırmak ve kalıcı iş akışı örneklerini güncelleştirmek IÇIN CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="156fb-235">Press CTRL+SHIFT+B to build the solution, and then press CTRL+F5 to run the `ApplyDynamicUpdate` application and update the persisted workflow instances.</span></span> <span data-ttu-id="156fb-236">Aşağıdakine benzer bir çıktı görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="156fb-236">You should see output similar to the following.</span></span> <span data-ttu-id="156fb-237">Sürüm 1.0.0.0 iş akışları sürüm 1.5.0.0 olarak güncelleştirilir, ancak sürüm 2.0.0.0 iş akışları güncellenmez.</span><span class="sxs-lookup"><span data-stu-id="156fb-237">The version 1.0.0.0 workflows are updated to version 1.5.0.0, while the version 2.0.0.0 workflows are not updated.</span></span>

    <span data-ttu-id="156fb-238">**İnceleniyor: StateMachineNumberGuessWorkflow; Sürüm = 1.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="156fb-238">**Inspecting: StateMachineNumberGuessWorkflow; Version=1.0.0.0**</span></span>\
    <span data-ttu-id="156fb-239">**Şu şekilde güncelleştirildi: StateMachineNumberGuessWorkflow; Sürüm = 1.5.0.0**</span><span class="sxs-lookup"><span data-stu-id="156fb-239">**Updated to: StateMachineNumberGuessWorkflow; Version=1.5.0.0**</span></span>\
    <span data-ttu-id="156fb-240">**İnceleniyor: StateMachineNumberGuessWorkflow; Sürüm = 1.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="156fb-240">**Inspecting: StateMachineNumberGuessWorkflow; Version=1.0.0.0**</span></span>\
    <span data-ttu-id="156fb-241">**Şu şekilde güncelleştirildi: StateMachineNumberGuessWorkflow; Sürüm = 1.5.0.0**</span><span class="sxs-lookup"><span data-stu-id="156fb-241">**Updated to: StateMachineNumberGuessWorkflow; Version=1.5.0.0**</span></span>\
    <span data-ttu-id="156fb-242">**İnceleniyor: FlowchartNumberGuessWorkflow; Sürüm = 1.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="156fb-242">**Inspecting: FlowchartNumberGuessWorkflow; Version=1.0.0.0**</span></span>\
    <span data-ttu-id="156fb-243">**Şu şekilde güncelleştirildi: FlowchartNumberGuessWorkflow; Sürüm = 1.5.0.0**</span><span class="sxs-lookup"><span data-stu-id="156fb-243">**Updated to: FlowchartNumberGuessWorkflow; Version=1.5.0.0**</span></span>\
    <span data-ttu-id="156fb-244">**İnceleniyor: FlowchartNumberGuessWorkflow; Sürüm = 1.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="156fb-244">**Inspecting: FlowchartNumberGuessWorkflow; Version=1.0.0.0**</span></span>\
    <span data-ttu-id="156fb-245">**Şu şekilde güncelleştirildi: FlowchartNumberGuessWorkflow; Sürüm = 1.5.0.0**</span><span class="sxs-lookup"><span data-stu-id="156fb-245">**Updated to: FlowchartNumberGuessWorkflow; Version=1.5.0.0**</span></span>\
    <span data-ttu-id="156fb-246">**İnceleniyor: SequentialNumberGuessWorkflow; Sürüm = 1.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="156fb-246">**Inspecting: SequentialNumberGuessWorkflow; Version=1.0.0.0**</span></span>\
    <span data-ttu-id="156fb-247">**Güncelleştirilme tarihi: SequentialNumberGuessWorkflow; Sürüm = 1.5.0.0**</span><span class="sxs-lookup"><span data-stu-id="156fb-247">**Updated to: SequentialNumberGuessWorkflow; Version=1.5.0.0**</span></span>\
    <span data-ttu-id="156fb-248">**İnceleniyor: SequentialNumberGuessWorkflow; Sürüm = 1.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="156fb-248">**Inspecting: SequentialNumberGuessWorkflow; Version=1.0.0.0**</span></span>\
    <span data-ttu-id="156fb-249">**Güncelleştirilme tarihi: SequentialNumberGuessWorkflow; Sürüm = 1.5.0.0**</span><span class="sxs-lookup"><span data-stu-id="156fb-249">**Updated to: SequentialNumberGuessWorkflow; Version=1.5.0.0**</span></span>\
    <span data-ttu-id="156fb-250">**İnceleniyor: SequentialNumberGuessWorkflow; Sürüm = 1.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="156fb-250">**Inspecting: SequentialNumberGuessWorkflow; Version=1.0.0.0**</span></span>\
    <span data-ttu-id="156fb-251">**Güncelleştirilme tarihi: SequentialNumberGuessWorkflow; Sürüm = 1.5.0.0**</span><span class="sxs-lookup"><span data-stu-id="156fb-251">**Updated to: SequentialNumberGuessWorkflow; Version=1.5.0.0**</span></span>\
    <span data-ttu-id="156fb-252">**İnceleniyor: StateMachineNumberGuessWorkflow; Sürüm = 1.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="156fb-252">**Inspecting: StateMachineNumberGuessWorkflow; Version=1.0.0.0**</span></span>\
    <span data-ttu-id="156fb-253">**Şu şekilde güncelleştirildi: StateMachineNumberGuessWorkflow; Sürüm = 1.5.0.0**</span><span class="sxs-lookup"><span data-stu-id="156fb-253">**Updated to: StateMachineNumberGuessWorkflow; Version=1.5.0.0**</span></span>\
    <span data-ttu-id="156fb-254">**İnceleniyor: FlowchartNumberGuessWorkflow; Sürüm = 1.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="156fb-254">**Inspecting: FlowchartNumberGuessWorkflow; Version=1.0.0.0**</span></span>\
    <span data-ttu-id="156fb-255">**Şu şekilde güncelleştirildi: FlowchartNumberGuessWorkflow; Sürüm = 1.5.0.0**</span><span class="sxs-lookup"><span data-stu-id="156fb-255">**Updated to: FlowchartNumberGuessWorkflow; Version=1.5.0.0**</span></span>\
    <span data-ttu-id="156fb-256">**İnceleniyor: StateMachineNumberGuessWorkflow; Sürüm = 2.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="156fb-256">**Inspecting: StateMachineNumberGuessWorkflow; Version=2.0.0.0**</span></span>\
    <span data-ttu-id="156fb-257">**İnceleniyor: StateMachineNumberGuessWorkflow; Sürüm = 2.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="156fb-257">**Inspecting: StateMachineNumberGuessWorkflow; Version=2.0.0.0**</span></span>\
    <span data-ttu-id="156fb-258">**İnceleniyor: FlowchartNumberGuessWorkflow; Sürüm = 2.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="156fb-258">**Inspecting: FlowchartNumberGuessWorkflow; Version=2.0.0.0**</span></span>\
    <span data-ttu-id="156fb-259">**İnceleniyor: FlowchartNumberGuessWorkflow; Sürüm = 2.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="156fb-259">**Inspecting: FlowchartNumberGuessWorkflow; Version=2.0.0.0**</span></span>\
    <span data-ttu-id="156fb-260">**İnceleniyor: SequentialNumberGuessWorkflow; Sürüm = 2.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="156fb-260">**Inspecting: SequentialNumberGuessWorkflow; Version=2.0.0.0**</span></span>\
    <span data-ttu-id="156fb-261">**İnceleniyor: SequentialNumberGuessWorkflow; Sürüm = 2.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="156fb-261">**Inspecting: SequentialNumberGuessWorkflow; Version=2.0.0.0**</span></span>\
    <span data-ttu-id="156fb-262">**Devam etmek için herhangi bir tuşa basın...**</span><span class="sxs-lookup"><span data-stu-id="156fb-262">**Press any key to continue . . .**</span></span>

### <a name="to-run-the-application-with-the-updated-workflows"></a><a name="BKMK_BuildAndRun"></a> <span data-ttu-id="156fb-263">Uygulamayı güncelleştirilmiş iş akışlarıyla çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="156fb-263">To run the application with the updated workflows</span></span>

1. <span data-ttu-id="156fb-264">**Çözüm Gezgini** Için **Numberguessworkflowwhost** öğesine sağ tıklayın ve **Başlangıç projesi olarak ayarla**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="156fb-264">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Set as StartUp Project**.</span></span>

2. <span data-ttu-id="156fb-265">Uygulamayı çalıştırmak için CTRL+F5'e basın.</span><span class="sxs-lookup"><span data-stu-id="156fb-265">Press CTRL+F5 to run the application.</span></span>

3. <span data-ttu-id="156fb-266">Yeni **oyun** ' e tıklayarak yeni bir iş akışı başlatın ve iş akışının bir iş akışı olduğunu belirten durum penceresinin altındaki sürüm bilgilerini unutmayın `v2` .</span><span class="sxs-lookup"><span data-stu-id="156fb-266">Click **New Game** to start a new workflow and note the version information below the status window that indicates the workflow is a `v2` workflow.</span></span>

4. <span data-ttu-id="156fb-267">`v1` [Nasıl yapılır: birden çok Iş akışının çoklu sürümlerini barındırma](how-to-host-multiple-versions-of-a-workflow-side-by-side.md) konusunun başlangıcında başlattığınız iş akışlarından birini seçin.</span><span class="sxs-lookup"><span data-stu-id="156fb-267">Select one of the `v1` workflows you started at the beginning of the [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md) topic.</span></span> <span data-ttu-id="156fb-268">Durum penceresi altındaki sürüm bilgileri, iş akışının bir sürüm **1.5.0.0** iş akışı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="156fb-268">Note that the version information under the status window indicates that the workflow is a version **1.5.0.0** workflow.</span></span> <span data-ttu-id="156fb-269">Önceki tahminlerle ilgili olarak, çok yüksek veya çok düşük olup olmadıkları hakkında hiçbir bilgi bulunmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="156fb-269">Note that there is no information indicated about previous guesses other than whether they were too high or too low.</span></span>

    <span data-ttu-id="156fb-270">**Lütfen 1 ile 10 arasında bir sayı girin**</span><span class="sxs-lookup"><span data-stu-id="156fb-270">**Please enter a number between 1 and 10**</span></span>\
    <span data-ttu-id="156fb-271">**Tahmininiz çok düşük.**</span><span class="sxs-lookup"><span data-stu-id="156fb-271">**Your guess is too low.**</span></span>

5. <span data-ttu-id="156fb-272">İş akışı tamamlanana kadar tahmin edilecek şekilde, ve değerlerini bir yere göz önünde `InstanceId` yazın.</span><span class="sxs-lookup"><span data-stu-id="156fb-272">Make a note of the `InstanceId` and then enter guesses until the workflow completes.</span></span> <span data-ttu-id="156fb-273">Durum penceresi, `WriteLine` etkinlik dinamik güncelleştirme tarafından güncelleştirildiğinden tahmin içeriğiyle ilgili bilgileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="156fb-273">The status window displays information about the content of the guess because the `WriteLine` activities were updated by the dynamic update.</span></span>

    <span data-ttu-id="156fb-274">**Lütfen 1 ile 10 arasında bir sayı girin**</span><span class="sxs-lookup"><span data-stu-id="156fb-274">**Please enter a number between 1 and 10**</span></span>\
    <span data-ttu-id="156fb-275">**Tahmininiz çok düşük.**</span><span class="sxs-lookup"><span data-stu-id="156fb-275">**Your guess is too low.**</span></span>\
    <span data-ttu-id="156fb-276">**Lütfen 1 ile 10 arasında bir sayı girin**</span><span class="sxs-lookup"><span data-stu-id="156fb-276">**Please enter a number between 1 and 10**</span></span>\
    <span data-ttu-id="156fb-277">**5 çok düşük.**</span><span class="sxs-lookup"><span data-stu-id="156fb-277">**5 is too low.**</span></span>\
    <span data-ttu-id="156fb-278">**Lütfen 1 ile 10 arasında bir sayı girin**</span><span class="sxs-lookup"><span data-stu-id="156fb-278">**Please enter a number between 1 and 10**</span></span>\
    <span data-ttu-id="156fb-279">**7 çok yüksek.**</span><span class="sxs-lookup"><span data-stu-id="156fb-279">**7 is too high.**</span></span>\
    <span data-ttu-id="156fb-280">**Lütfen 1 ile 10 arasında bir sayı girin**</span><span class="sxs-lookup"><span data-stu-id="156fb-280">**Please enter a number between 1 and 10**</span></span>\
    <span data-ttu-id="156fb-281">**Tebrikler, sayıyı 4 ' te tahmin edersiniz.**</span><span class="sxs-lookup"><span data-stu-id="156fb-281">**Congratulations, you guessed the number in 4 turns.**</span></span>

6. <span data-ttu-id="156fb-282">Windows Gezgini 'ni açın ve **Numberguessworkflowwhost\bin\debug** klasörüne (veya proje ayarlarınıza bağlı olarak **bin\release** ) gidin ve tamamlanan Iş akışına karşılık gelen Not defteri 'ni kullanarak izleme dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="156fb-282">Open Windows Explorer and navigate to the **NumberGuessWorkflowHost\bin\debug** folder (or **bin\release** depending on your project settings) and open the tracking file using Notepad that corresponds to the completed workflow.</span></span> <span data-ttu-id="156fb-283">' İ Not oluşturmadınız, `InstanceId` Windows Gezgini 'nde **değiştirilme tarihi** bilgilerini kullanarak doğru izleme dosyasını belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="156fb-283">If you did not make a note of the `InstanceId` you may be able to identify the correct tracking file by using the **Date modified** information in Windows Explorer.</span></span> <span data-ttu-id="156fb-284">İzleme bilgilerinin son satırı, yeni eklenen etkinliğin çıktısını içerir `WriteLine` .</span><span class="sxs-lookup"><span data-stu-id="156fb-284">The last line of the tracking information contains the output of the newly added `WriteLine` activity.</span></span>

    <span data-ttu-id="156fb-285">**Lütfen 1 ile 10 arasında bir sayı girin**</span><span class="sxs-lookup"><span data-stu-id="156fb-285">**Please enter a number between 1 and 10**</span></span>\
    <span data-ttu-id="156fb-286">**Tahmininiz çok düşük.**</span><span class="sxs-lookup"><span data-stu-id="156fb-286">**Your guess is too low.**</span></span>\
    <span data-ttu-id="156fb-287">**Lütfen 1 ile 10 arasında bir sayı girin**</span><span class="sxs-lookup"><span data-stu-id="156fb-287">**Please enter a number between 1 and 10**</span></span>\
    <span data-ttu-id="156fb-288">**5 çok düşük.**</span><span class="sxs-lookup"><span data-stu-id="156fb-288">**5 is too low.**</span></span>\
    <span data-ttu-id="156fb-289">**Lütfen 1 ile 10 arasında bir sayı girin**</span><span class="sxs-lookup"><span data-stu-id="156fb-289">**Please enter a number between 1 and 10**</span></span>\
    <span data-ttu-id="156fb-290">**7 çok yüksek.**</span><span class="sxs-lookup"><span data-stu-id="156fb-290">**7 is too high.**</span></span>\
    <span data-ttu-id="156fb-291">**Lütfen 1 ile 10 arasında bir sayı girin**</span><span class="sxs-lookup"><span data-stu-id="156fb-291">**Please enter a number between 1 and 10**</span></span>\
    <span data-ttu-id="156fb-292">**6 doğru. Bunu 4 ' te tahmin edersiniz.**</span><span class="sxs-lookup"><span data-stu-id="156fb-292">**6 is correct. You guessed it in 4 turns.**</span></span>

### <a name="to-enable-starting-previous-versions-of-the-workflows"></a><a name="BKMK_StartPreviousVersions"></a> <span data-ttu-id="156fb-293">İş akışlarının önceki sürümlerini başlatmayı etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="156fb-293">To enable starting previous versions of the workflows</span></span>

<span data-ttu-id="156fb-294">Güncelleştirmek için iş akışlarının dışında çalıştırırsanız, `NumberGuessWorkflowHost` iş akışlarının önceki sürümlerinin başlamasını sağlamak için uygulamayı değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="156fb-294">If you run out of workflows to update, you can modify the `NumberGuessWorkflowHost` application to enable starting previous versions of the workflows.</span></span>

1. <span data-ttu-id="156fb-295">**Çözüm Gezgini**' de **Workflowwhostform** ' a çift tıklayın ve **WorkflowType** Birleşik giriş kutusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="156fb-295">Double-click **WorkflowHostForm** in **Solution Explorer**, and select the **WorkflowType** combo box.</span></span>

2. <span data-ttu-id="156fb-296">**Özellikler** **penceresinde, öğeler özelliğini seçin** ve **öğeler** koleksiyonunu düzenlemek için üç nokta düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="156fb-296">In the **Properties** window, select the **Items** property and click the ellipsis button to edit the **Items** collection.</span></span>

3. <span data-ttu-id="156fb-297">Aşağıdaki üç öğeyi koleksiyona ekleyin.</span><span class="sxs-lookup"><span data-stu-id="156fb-297">Add the following three items to the collection.</span></span>

    ```
    StateMachineNumberGuessWorkflow v1
    FlowchartNumberGuessWorkflow v1
    SequentialNumberGuessWorkflow v1
    ```

    <span data-ttu-id="156fb-298">Tamamlanan `Items` koleksiyonda altı öğe olacak.</span><span class="sxs-lookup"><span data-stu-id="156fb-298">The completed `Items` collection will have six items.</span></span>

    ```
    StateMachineNumberGuessWorkflow
    FlowchartNumberGuessWorkflow
    SequentialNumberGuessWorkflow
    StateMachineNumberGuessWorkflow v1
    FlowchartNumberGuessWorkflow v1
    SequentialNumberGuessWorkflow v1
    ```

4. <span data-ttu-id="156fb-299">**Çözüm Gezgini**' de **Workflowwhostform** ' a çift tıklayın ve **kodu görüntüle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="156fb-299">Double-click **WorkflowHostForm** in **Solution Explorer**, and select **View Code**.</span></span>

5. <span data-ttu-id="156fb-300">`switch` `Select Case` `NewGame_Click` **WorkflowType** Birleşik giriş kutusundaki yeni öğeleri eşleşen iş akışı kimliklerine eşlemek için işleyicisindeki (veya) ifadeye üç yeni durum ekleyin.</span><span class="sxs-lookup"><span data-stu-id="156fb-300">Add three new cases to the `switch` (or `Select Case`) statement in the `NewGame_Click` handler to map the new items in the **WorkflowType** combo box to the matching workflow identities.</span></span>

    ```vb
    Case "SequentialNumberGuessWorkflow v1"
        identity = WorkflowVersionMap.SequentialNumberGuessIdentity_v1

    Case "StateMachineNumberGuessWorkflow v1"
        identity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v1

    Case "FlowchartNumberGuessWorkflow v1"
        identity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v1
    ```

    ```csharp
    case "SequentialNumberGuessWorkflow v1":
        identity = WorkflowVersionMap.SequentialNumberGuessIdentity_v1;
        break;

    case "StateMachineNumberGuessWorkflow v1":
        identity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v1;
        break;

    case "FlowchartNumberGuessWorkflow v1":
        identity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v1;
        break;
    ```

    <span data-ttu-id="156fb-301">Aşağıdaki örnek, tüm `switch` (veya `Select Case` ) ifadesini içerir.</span><span class="sxs-lookup"><span data-stu-id="156fb-301">The following example contains the complete `switch` (or `Select Case`) statement.</span></span>

    ```vb
    Select Case WorkflowType.SelectedItem.ToString()
        Case "SequentialNumberGuessWorkflow"
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity

        Case "StateMachineNumberGuessWorkflow"
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity

        Case "FlowchartNumberGuessWorkflow"
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity

        Case "SequentialNumberGuessWorkflow v1"
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity_v1

        Case "StateMachineNumberGuessWorkflow v1"
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v1

        Case "FlowchartNumberGuessWorkflow v1"
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v1
    End Select
    ```

    ```csharp
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

        case "SequentialNumberGuessWorkflow v1":
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity_v1;
            break;

        case "StateMachineNumberGuessWorkflow v1":
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v1;
            break;

        case "FlowchartNumberGuessWorkflow v1":
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v1;
            break;
    };
    ```

6. <span data-ttu-id="156fb-302">Uygulamayı derlemek ve çalıştırmak için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="156fb-302">Press CTRL+F5 to build and run the application.</span></span> <span data-ttu-id="156fb-303">Artık `v1` iş akışının sürümlerini de ve geçerli sürümleri başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="156fb-303">You can now start the `v1` versions of the workflow as well as the current versions.</span></span> <span data-ttu-id="156fb-304">Bu yeni örnekleri dinamik olarak güncelleştirmek için **Applydynamicupdate** uygulamasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="156fb-304">To dynamically update these new instances, run the **ApplyDynamicUpdate** application.</span></span>
