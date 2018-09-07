---
title: 'Nasıl yapılır: çalışan iş akışı örneğinin tanımını güncelleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 26dfac36-ae23-4909-9867-62495b55fb5e
ms.openlocfilehash: c3d870e9e5ad8129a5cf24c63c2a7884e91f9630
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44081001"
---
# <a name="how-to-update-the-definition-of-a-running-workflow-instance"></a><span data-ttu-id="e336a-102">Nasıl yapılır: çalışan iş akışı örneğinin tanımını güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="e336a-102">How to: Update the Definition of a Running Workflow Instance</span></span>
<span data-ttu-id="e336a-103">Dinamik güncelleştirme, uygulama geliştiricilerinin'bir kalıcı iş akışı örneği iş akışı tanımını güncelleştirmek için iş akışı için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="e336a-103">Dynamic update provides a mechanism for workflow application developers to update the workflow definition of a persisted workflow instance.</span></span> <span data-ttu-id="e336a-104">Gerekli değişiklik, bir hata düzeltmesi, yeni gereksinimleri uygulamak için veya beklenmeyen değişiklikleri uyum sağlamak için olabilir.</span><span class="sxs-lookup"><span data-stu-id="e336a-104">The required change can be to implement a bug fix, new requirements, or to accommodate unexpected changes.</span></span> <span data-ttu-id="e336a-105">Bu adım öğreticide kalıcı örnekleri değiştirmek için dinamik güncelleştirme kullanmayı gösteren `v1` sürümünde bulunan yeni işlevleri eşleştirmek için iş akışı tahmin numarası [nasıl yapılır: bir iş akışı yan yana birden çok sürümünü konak ](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span><span class="sxs-lookup"><span data-stu-id="e336a-105">This step in the tutorial demonstrates how to use dynamic update to modify  persisted instances of the `v1` number guessing workflow to match the new functionality introduced in [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e336a-106">Tamamlanmış bir sürümünü indirin veya videosu öğreticinin görüntülemek için bkz: [Windows Workflow Foundation (WF45) - başlangıç Öğreticisi](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="e336a-106">To download a completed version or view a video walkthrough of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="in-this-topic"></a><span data-ttu-id="e336a-107">Bu konuda</span><span class="sxs-lookup"><span data-stu-id="e336a-107">In this topic</span></span>  
  
-   [<span data-ttu-id="e336a-108">CreateUpdateMaps projeyi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e336a-108">To create the CreateUpdateMaps project</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_CreateProject)  
  
-   [<span data-ttu-id="e336a-109">StateMachineNumberGuessWorkflow güncelleştirmek için</span><span class="sxs-lookup"><span data-stu-id="e336a-109">To update StateMachineNumberGuessWorkflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_StateMachine)  
  
-   [<span data-ttu-id="e336a-110">FlowchartNumberGuessWorkflow güncelleştirmek için</span><span class="sxs-lookup"><span data-stu-id="e336a-110">To update FlowchartNumberGuessWorkflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_Flowchart)  
  
-   [<span data-ttu-id="e336a-111">SequentialNumberGuessWorkflow güncelleştirmek için</span><span class="sxs-lookup"><span data-stu-id="e336a-111">To update SequentialNumberGuessWorkflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_Sequential)  
  
-   [<span data-ttu-id="e336a-112">CreateUpdateMaps uygulaması derleme ve çalıştırma için</span><span class="sxs-lookup"><span data-stu-id="e336a-112">To build and run the CreateUpdateMaps application</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_CreateUpdateMaps)  
  
-   [<span data-ttu-id="e336a-113">Güncelleştirilmiş iş akışı derlemesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e336a-113">To build the updated workflow assembly</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_BuildAssembly)  
  
-   [<span data-ttu-id="e336a-114">Yeni sürümlerle WorkflowVersionMap güncelleştirmek için</span><span class="sxs-lookup"><span data-stu-id="e336a-114">To update WorkflowVersionMap with the new versions</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_UpdateWorkflowVersionMap)  
  
-   [<span data-ttu-id="e336a-115">Dinamik güncelleştirmeleri uygulamak için</span><span class="sxs-lookup"><span data-stu-id="e336a-115">To apply the dynamic updates</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_ApplyUpdate)  
  
-   [<span data-ttu-id="e336a-116">Güncelleştirilmiş iş akışlarıyla uygulamayı çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="e336a-116">To run the application with the updated workflows</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_BuildAndRun)  
  
-   [<span data-ttu-id="e336a-117">İş Akışları'nın önceki sürümlerini başlangıç etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="e336a-117">To enable starting previous versions of the workflows</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_StartPreviousVersions)  
  
###  <a name="BKMK_CreateProject"></a> <span data-ttu-id="e336a-118">CreateUpdateMaps projeyi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e336a-118">To create the CreateUpdateMaps project</span></span>  
  
1.  <span data-ttu-id="e336a-119">Sağ **WF45GettingStartedTutorial** içinde **Çözüm Gezgini** ve **Ekle**, **yeni proje**.</span><span class="sxs-lookup"><span data-stu-id="e336a-119">Right-click **WF45GettingStartedTutorial** in **Solution Explorer** and choose **Add**, **New Project**.</span></span>  
  
2.  <span data-ttu-id="e336a-120">İçinde **yüklü** düğümünü **Visual C#**, **Windows** (veya **Visual Basic**, **Windows**).</span><span class="sxs-lookup"><span data-stu-id="e336a-120">In the **Installed** node, select **Visual C#**, **Windows** (or **Visual Basic**, **Windows**).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e336a-121">Hangi programlama diline bağlı olarak, Visual Studio'da birincil dili olarak yapılandırılmış **Visual C#** veya **Visual Basic** düğümü altında olabilir **diğer diller** düğümünde **yüklü** düğümü.</span><span class="sxs-lookup"><span data-stu-id="e336a-121">Depending on which programming language is configured as the primary language in Visual Studio, the **Visual C#** or **Visual Basic** node may be under the **Other Languages** node in the **Installed** node.</span></span>  
  
     <span data-ttu-id="e336a-122">Emin **.NET Framework 4.5** .NET Framework sürüm aşağı açılan listeden seçilen.</span><span class="sxs-lookup"><span data-stu-id="e336a-122">Ensure that **.NET Framework 4.5** is selected in the .NET Framework version drop-down list.</span></span> <span data-ttu-id="e336a-123">Seçin **konsol uygulaması** gelen **Windows** listesi.</span><span class="sxs-lookup"><span data-stu-id="e336a-123">Select **Console Application** from the **Windows** list.</span></span> <span data-ttu-id="e336a-124">Tür **CreateUpdateMaps** içine **adı** kutusuna ve tıklatın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="e336a-124">Type **CreateUpdateMaps** into the **Name** box and click **OK**.</span></span>  
  
3.  <span data-ttu-id="e336a-125">Sağ **CreateUpdateMaps** içinde **Çözüm Gezgini** ve **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="e336a-125">Right-click **CreateUpdateMaps** in **Solution Explorer** and choose **Add Reference**.</span></span>  
  
4.  <span data-ttu-id="e336a-126">Seçin **Framework** gelen **derlemeleri** düğümünde **Başvuru Ekle** listesi.</span><span class="sxs-lookup"><span data-stu-id="e336a-126">Select **Framework** from the **Assemblies** node in the **Add Reference** list.</span></span> <span data-ttu-id="e336a-127">Tür **System.Activities** içine **arama derlemeleri** derlemeleri filtrelemek ve istenen başvurular seçmek daha kolay hale getirmek için kutusu.</span><span class="sxs-lookup"><span data-stu-id="e336a-127">Type **System.Activities** into the **Search Assemblies** box to filter the assemblies and make the desired references easier to select.</span></span>  
  
5.  <span data-ttu-id="e336a-128">Yanında onay **System.Activities** gelen **arama sonuçları** listesi.</span><span class="sxs-lookup"><span data-stu-id="e336a-128">Check the checkbox beside **System.Activities** from the **Search Results** list.</span></span>  
  
6.  <span data-ttu-id="e336a-129">Türü **serileştirme** içine **arama derlemeleri** kutusuna ve yanında onay **System.Runtime.Serialization** gelen **arama sonuçları**  listesi.</span><span class="sxs-lookup"><span data-stu-id="e336a-129">Type **Serialization** into the **Search Assemblies** box, and check the checkbox beside **System.Runtime.Serialization** from the **Search Results** list.</span></span>  
  
7.  <span data-ttu-id="e336a-130">Türü **System.Xaml** içine **arama derlemeleri** kutusuna ve yanında onay **System.Xaml** gelen **arama sonuçları** listesi.</span><span class="sxs-lookup"><span data-stu-id="e336a-130">Type **System.Xaml** into the **Search Assemblies** box, and check the checkbox beside **System.Xaml** from the **Search Results** list.</span></span>  
  
8.  <span data-ttu-id="e336a-131">Tıklayın **Tamam** kapatmak için **başvuru Yöneticisi** ve başvuruları ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e336a-131">Click **OK** to close **Reference Manager** and add the references.</span></span>  
  
9. <span data-ttu-id="e336a-132">Aşağıdaki `using` (veya `Imports`) deyimini dosyanın diğer üst `using` (veya `Imports`) ifadeleri.</span><span class="sxs-lookup"><span data-stu-id="e336a-132">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
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
  
10. <span data-ttu-id="e336a-133">Aşağıdaki iki dize üye ekleme `Program` sınıfı (veya `Module1`).</span><span class="sxs-lookup"><span data-stu-id="e336a-133">Add the following two string members to the `Program` class (or `Module1`).</span></span>  
  
    ```vb  
    Const mapPath = "..\..\..\PreviousVersions"  
    Const definitionPath = "..\..\..\NumberGuessWorkflowActivities_du"  
    ```  
  
    ```csharp  
    const string mapPath = @"..\..\..\PreviousVersions";  
    const string definitionPath = @"..\..\..\NumberGuessWorkflowActivities_du";  
    ```  
  
11. <span data-ttu-id="e336a-134">Aşağıdaki `StartUpdate` yönteme `Program` sınıfı (veya `Module1`).</span><span class="sxs-lookup"><span data-stu-id="e336a-134">Add the following `StartUpdate` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="e336a-135">Bu yöntem, belirtilen xaml iş akışı tanımında'kurmak yükler bir `ActivityBuilder`ve ardından çağırır `DynamicUpdate.PrepareForUpdate`.</span><span class="sxs-lookup"><span data-stu-id="e336a-135">This method loads up the specified xaml workflow definition into an `ActivityBuilder`, and then calls `DynamicUpdate.PrepareForUpdate`.</span></span> <span data-ttu-id="e336a-136">`PrepareForUpdate` İş akışı tanımı içinde bir kopyasını oluşturur `ActivityBuilder`.</span><span class="sxs-lookup"><span data-stu-id="e336a-136">`PrepareForUpdate` makes a copy of the workflow definition inside the `ActivityBuilder`.</span></span> <span data-ttu-id="e336a-137">İş akışı tanımı değiştirildikten sonra bu kopya güncelleştirme eşlemesi oluşturmak için değiştirilmiş iş akışı tanımı ile birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e336a-137">After the workflow definition is modified, this copy is used along with the modified workflow definition to create the update map.</span></span>  
  
    ```vb  
    Private Function StartUpdate(name As String) As ActivityBuilder  
        'Create the XamlXmlReaderSettings.  
        Dim readerSettings As XamlReaderSettings = New XamlXmlReaderSettings()  
        'In the XAML the "local" namespace referes to artifacts that come from   
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
            // In the XAML the "local" namespace referes to artifacts that come from   
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
  
12. <span data-ttu-id="e336a-138">Ardından, aşağıdaki ekleyin `CreateUpdateMethod` için `Program` sınıfı (veya `Module1`).</span><span class="sxs-lookup"><span data-stu-id="e336a-138">Next, add the following `CreateUpdateMethod` to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="e336a-139">Bir dinamik güncelleştirme eşlemesi tarafından çağıran DynamicUpdateServices.CreateUpdateMap oluşturur ve sonra belirtilen adı kullanarak güncelleştirme eşlemesi kaydeder.</span><span class="sxs-lookup"><span data-stu-id="e336a-139">This creates a dynamic update map by calling DynamicUpdateServices.CreateUpdateMap, and then saves the update map using the specified name.</span></span> <span data-ttu-id="e336a-140">Bu güncelleştirme eşlemesi iş akışı çalışma zamanı tarafından bulunan özgün iş akışı tanımı kullanılarak başlatıldı bir kalıcı iş akışı örneği güncelleştirmek için gereken bilgileri içeren `ActivityBuilder` böylece güncelleştirilmiş iş akışı tanımı kullanılarak tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="e336a-140">This update map contains the information needed by the workflow runtime to update a persisted workflow instance that was started using the original workflow definition contained in the `ActivityBuilder` so that it completes using the updated workflow definition.</span></span>  
  
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
  
13. <span data-ttu-id="e336a-141">Aşağıdaki `SaveUpdatedDefinition` yönteme `Program` sınıfı (veya `Module1`).</span><span class="sxs-lookup"><span data-stu-id="e336a-141">Add the following `SaveUpdatedDefinition` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="e336a-142">Güncelleştirme eşlemesi oluşturulduktan sonra bu yöntem, güncelleştirilmiş iş akışı tanımı kaydeder.</span><span class="sxs-lookup"><span data-stu-id="e336a-142">This method saves the updated workflow definition once the update map is created.</span></span>  
  
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
  
###  <a name="BKMK_StateMachine"></a> <span data-ttu-id="e336a-143">StateMachineNumberGuessWorkflow güncelleştirmek için</span><span class="sxs-lookup"><span data-stu-id="e336a-143">To update StateMachineNumberGuessWorkflow</span></span>  
  
1.  <span data-ttu-id="e336a-144">Ekleme bir `CreateStateMachineUpdateMap` için `Program` sınıfı (veya `Module1`).</span><span class="sxs-lookup"><span data-stu-id="e336a-144">Add a `CreateStateMachineUpdateMap` to the `Program` class (or `Module1`).</span></span>  
  
    ```vb  
    Private Sub CreateStateMachineUpdateMap()  
  
    End Sub  
    ```  
  
    ```csharp  
    private static void CreateStateMachineUpdateMap()  
    {    
    }  
    ```  
  
2.  <span data-ttu-id="e336a-145">Çağrı yapmak `StartUpdate` ve ardından kök bir başvuru almak `StateMachine` iş akışı etkinlik.</span><span class="sxs-lookup"><span data-stu-id="e336a-145">Make a call to `StartUpdate` and then get a reference to the root `StateMachine` activity of the workflow.</span></span>  
  
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
  
3.  <span data-ttu-id="e336a-146">Ardından, iki ifadelerin güncelleştirme `WriteLine` kullanıcının tahmin çok yüksek veya düşük olduğunu yapılan güncelleştirmeler eşleştikleri böylece görüntüleyen etkinlikleri [nasıl yapılır: bir iş akışı yan yana birden çok sürümünü konak](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span><span class="sxs-lookup"><span data-stu-id="e336a-146">Next, update the expressions of the two `WriteLine` activities that display whether the user's guess is too high or too low so that they match the updates made in [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>  
  
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
  
4.  <span data-ttu-id="e336a-147">Ardından, yeni ekleme `WriteLine` kapanış iletisini gösteren bir etkinlik.</span><span class="sxs-lookup"><span data-stu-id="e336a-147">Next, add the new `WriteLine` activity that displays the closing message.</span></span>  
  
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
  
5.  <span data-ttu-id="e336a-148">İş akışı güncelleştirildikten sonra çağrı `CreateUpdateMaps` ve `SaveUpdatedDefinition`.</span><span class="sxs-lookup"><span data-stu-id="e336a-148">After the workflow is updated, call `CreateUpdateMaps` and `SaveUpdatedDefinition`.</span></span> <span data-ttu-id="e336a-149">`CreateUpdateMaps` oluşturur ve kaydeder `DynamicUpdateMap`, ve `SaveUpdatedDefinition` güncelleştirilmiş iş akışı tanımı kaydeder.</span><span class="sxs-lookup"><span data-stu-id="e336a-149">`CreateUpdateMaps` creates and saves the `DynamicUpdateMap`, and `SaveUpdatedDefinition` saves the updated workflow definition.</span></span>  
  
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
  
     <span data-ttu-id="e336a-150">Aşağıdaki örnek, tamamlanan, `CreateStateMachineUpdateMap` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e336a-150">The following example is the completed `CreateStateMachineUpdateMap` method.</span></span>  
  
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
  
###  <a name="BKMK_Flowchart"></a> <span data-ttu-id="e336a-151">FlowchartNumberGuessWorkflow güncelleştirmek için</span><span class="sxs-lookup"><span data-stu-id="e336a-151">To update FlowchartNumberGuessWorkflow</span></span>  
  
1.  <span data-ttu-id="e336a-152">Aşağıdaki `CreateFlowchartUpdateMethod` için `Program` sınıfı (veya `Module1`).</span><span class="sxs-lookup"><span data-stu-id="e336a-152">Add the following `CreateFlowchartUpdateMethod` to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="e336a-153">Bu yöntem benzer `CreateStateMachineUpdateMap`.</span><span class="sxs-lookup"><span data-stu-id="e336a-153">This method is similar to `CreateStateMachineUpdateMap`.</span></span> <span data-ttu-id="e336a-154">Bir çağrı ile başlar `StartUpdate`akış çizelgesi iş akışı tanım güncelleştirmeleri ve güncelleştirme harita ve güncelleştirilmiş iş akışı tanımı kaydederek tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="e336a-154">It starts with a call to `StartUpdate`, updates the flowchart workflow definition, and finishes by saving the update map and the updated workflow definition.</span></span>  
  
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
  
###  <a name="BKMK_Sequential"></a> <span data-ttu-id="e336a-155">SequentialNumberGuessWorkflow güncelleştirmek için</span><span class="sxs-lookup"><span data-stu-id="e336a-155">To update SequentialNumberGuessWorkflow</span></span>  
  
1.  <span data-ttu-id="e336a-156">Aşağıdaki `CreateSequentialUpdateMethod` için `Program` sınıfı (veya `Module1`).</span><span class="sxs-lookup"><span data-stu-id="e336a-156">Add the following `CreateSequentialUpdateMethod` to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="e336a-157">Bu yöntem diğer iki yöntemler ile benzerdir.</span><span class="sxs-lookup"><span data-stu-id="e336a-157">This method is similar to the other two methods.</span></span> <span data-ttu-id="e336a-158">Bir çağrı ile başlar `StartUpdate`sıralı iş akışı tanım güncelleştirmeleri ve güncelleştirme harita ve güncelleştirilmiş iş akışı tanımı kaydederek tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="e336a-158">It starts with a call to `StartUpdate`, updates the sequential workflow definition, and finishes by saving the update map and the updated workflow definition.</span></span>  
  
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
  
###  <a name="BKMK_CreateUpdateMaps"></a> <span data-ttu-id="e336a-159">CreateUpdateMaps uygulaması derleme ve çalıştırma için</span><span class="sxs-lookup"><span data-stu-id="e336a-159">To build and run the CreateUpdateMaps application</span></span>  
  
1.  <span data-ttu-id="e336a-160">Güncelleştirme `Main` yöntemi ve aşağıdaki üç yöntem çağrıları ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e336a-160">Update the `Main` method and add the following three method calls.</span></span> <span data-ttu-id="e336a-161">Bu yöntemleri aşağıdaki bölümlerde eklenir.</span><span class="sxs-lookup"><span data-stu-id="e336a-161">These methods are added in the following sections.</span></span> <span data-ttu-id="e336a-162">Her bir yöntemin karşılık gelen numara tahmin iş akışı güncelleştirir ve oluşturur bir `DynamicUpdateMap` , güncelleştirmeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="e336a-162">Each method updates the corresponding number guess workflow and creates a `DynamicUpdateMap` that describes the updates.</span></span>  
  
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
  
2.  <span data-ttu-id="e336a-163">Sağ **CreateUpdateMaps** içinde **Çözüm Gezgini** ve **başlangıç projesi olarak ayarla**.</span><span class="sxs-lookup"><span data-stu-id="e336a-163">Right-click **CreateUpdateMaps** in **Solution Explorer** and choose **Set as StartUp Project**.</span></span>  
  
3.  <span data-ttu-id="e336a-164">Çözümü derlemek için CTRL + SHIFT + B ve çalıştırmak için CTRL + F5 tuşlarına basın `CreateUpdateMaps` uygulama.</span><span class="sxs-lookup"><span data-stu-id="e336a-164">Press CTRL+SHIFT+B to build the solution, and then CTRL+F5 to run the `CreateUpdateMaps` application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e336a-165">`CreateUpdateMaps` Uygulama çalışırken, konum, ancak herhangi bir durum bilgi görüntülemez **NumberGuessWorkflowActivities_du** klasörü ve **PreviousVersions** klasörü göreceksiniz güncelleştirilmiş iş akışı tanım dosyalarını ve güncelleştirme eşlemeleri.</span><span class="sxs-lookup"><span data-stu-id="e336a-165">The `CreateUpdateMaps` application does not display any status information while running, but if you look in the **NumberGuessWorkflowActivities_du** folder and the **PreviousVersions** folder you will see the updated workflow definition files and the update maps.</span></span>  
  
     <span data-ttu-id="e336a-166">Sonra güncelleştirme haritalar oluşturulur ve güncelleştirilmiş iş akışı tanımları, sonraki adımda güncelleştirilmiş tanımlarını içeren güncelleştirilmiş iş akışı derleme oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="e336a-166">Once the update maps are created and the workflow definitions updated, the next step is to build an updated workflow assembly containing the updated definitions.</span></span>  
  
###  <a name="BKMK_BuildAssembly"></a> <span data-ttu-id="e336a-167">Güncelleştirilmiş iş akışı derlemesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e336a-167">To build the updated workflow assembly</span></span>  
  
1.  <span data-ttu-id="e336a-168">İkinci bir örneğini açın [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e336a-168">Open a second instance of [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="e336a-169">Seçin **açık**, **proje/çözüm** gelen **dosya** menüsü.</span><span class="sxs-lookup"><span data-stu-id="e336a-169">Choose **Open**, **Project/Solution** from the **File** menu.</span></span>  
  
3.  <span data-ttu-id="e336a-170">Gidin **NumberGuessWorkflowActivities_du** oluşturduğunuz klasör [nasıl yapılır: bir iş akışı yan yana birden çok sürümünü konak](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md)seçin **NumberGuessWorkflowActivities.csproj**  (veya **vbproj**), tıklatıp **açık**.</span><span class="sxs-lookup"><span data-stu-id="e336a-170">Navigate to the **NumberGuessWorkflowActivities_du** folder you created in [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md), select **NumberGuessWorkflowActivities.csproj** (or **vbproj**), and click **Open**.</span></span>  
  
4.  <span data-ttu-id="e336a-171">İçinde **Çözüm Gezgini**, sağ tıklayın **SequentialNumberGuessWorkflow.xaml** ve **projeden Çıkart**.</span><span class="sxs-lookup"><span data-stu-id="e336a-171">In **Solution Explorer**, right click **SequentialNumberGuessWorkflow.xaml** and choose **Exclude From Project**.</span></span> <span data-ttu-id="e336a-172">Aynı şeyi yapmak **FlowchartNumberGuessWorkflow.xaml** ve **StateMachineNumberGuessWorkflow.xaml**.</span><span class="sxs-lookup"><span data-stu-id="e336a-172">Do the same thing for **FlowchartNumberGuessWorkflow.xaml** and **StateMachineNumberGuessWorkflow.xaml**.</span></span> <span data-ttu-id="e336a-173">Bu adım, iş akışı tanımları önceki sürümlerini projeden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="e336a-173">This step removes the previous versions of the workflow definitions from the project.</span></span>  
  
5.  <span data-ttu-id="e336a-174">Seçin **varolan öğeyi Ekle** gelen **proje** menüsü.</span><span class="sxs-lookup"><span data-stu-id="e336a-174">Choose **Add Existing Item** from the **Project** menu.</span></span>  
  
6.  <span data-ttu-id="e336a-175">Gidin **NumberGuessWorkflowActivities_du** oluşturduğunuz klasör [nasıl yapılır: bir iş akışı yan yana birden çok sürümünü konak](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span><span class="sxs-lookup"><span data-stu-id="e336a-175">Navigate to the **NumberGuessWorkflowActivities_du** folder you created in [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>  
  
7.  <span data-ttu-id="e336a-176">Seçin **XAML dosyaları (\*.xaml;\*. xoml)** gelen **dosya türü** aşağı açılan listesi.</span><span class="sxs-lookup"><span data-stu-id="e336a-176">Choose **XAML Files (\*.xaml;\*.xoml)** from the **Files of type** drop-down list.</span></span>  
  
8.  <span data-ttu-id="e336a-177">Seçin **SequentialNumberGuessWorkflow_du.xaml**, **FlowchartNumberGuessWorkflow_du.xaml**, ve **StateMachineNumberGuessWorkflow_du.xaml** tıklayın **Ekleme**.</span><span class="sxs-lookup"><span data-stu-id="e336a-177">Select **SequentialNumberGuessWorkflow_du.xaml**, **FlowchartNumberGuessWorkflow_du.xaml**, and **StateMachineNumberGuessWorkflow_du.xaml** and click **Add**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e336a-178">Aynı anda birden çok öğe seçmek için CTRL + tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e336a-178">CTRL+Click to select multiple items at a time.</span></span>  
  
     <span data-ttu-id="e336a-179">Bu adım, iş akışı tanımlarının güncelleştirilmiş sürümleri projeye ekler.</span><span class="sxs-lookup"><span data-stu-id="e336a-179">This step adds the updated versions of the workflow definitions to the project.</span></span>  
  
9. <span data-ttu-id="e336a-180">Projeyi oluşturmak için CTRL+SHIFT+B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="e336a-180">Press CTRL+SHIFT+B to build the project.</span></span>  
  
10. <span data-ttu-id="e336a-181">Seçin **çözümü Kapat** gelen **dosya** menüsü.</span><span class="sxs-lookup"><span data-stu-id="e336a-181">Choose **Close Solution** from the **File** menu.</span></span> <span data-ttu-id="e336a-182">Bir çözüm dosyası için proje gerekli değildir. Bu nedenle tıklayın **Hayır** Visual Studio çözüm dosyası kaydetmeden kapatın.</span><span class="sxs-lookup"><span data-stu-id="e336a-182">A solution file for the project is not required, so click **No** to close Visual Studio without saving a solution file.</span></span> <span data-ttu-id="e336a-183">Seçin **çıkış** gelen **dosya** menüsünde Visual Studio'yu kapatın.</span><span class="sxs-lookup"><span data-stu-id="e336a-183">Choose **Exit** from the **File** menu to close Visual Studio.</span></span>  
  
11. <span data-ttu-id="e336a-184">Windows Gezgini'ni açın ve gidin **NumberGuessWorkflowActivities_du\bin\Debug** klasörü (veya **bin\Release** proje ayarlarınıza bağlı olarak).</span><span class="sxs-lookup"><span data-stu-id="e336a-184">Open Windows Explorer and navigate to the **NumberGuessWorkflowActivities_du\bin\Debug** folder (or **bin\Release** depending on your project settings).</span></span>  
  
12. <span data-ttu-id="e336a-185">Yeniden adlandırma **NumberGuessWorkflowActivities.dll** için **NumberGuessWorkflowActivities_v15.dll**ve kopyalayıp **PreviousVersions** içindeoluşturduğunuzklasör[Nasıl yapılır: bir iş akışı yan yana birden çok sürümünü konak](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span><span class="sxs-lookup"><span data-stu-id="e336a-185">Rename **NumberGuessWorkflowActivities.dll** to **NumberGuessWorkflowActivities_v15.dll**, and copy it to the **PreviousVersions** folder you created in [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>  
  
###  <a name="BKMK_UpdateWorkflowVersionMap"></a> <span data-ttu-id="e336a-186">Yeni sürümlerle WorkflowVersionMap güncelleştirmek için</span><span class="sxs-lookup"><span data-stu-id="e336a-186">To update WorkflowVersionMap with the new versions</span></span>  
  
1.  <span data-ttu-id="e336a-187">Geçiş ilk örneğine [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e336a-187">Switch back to the initial instance of [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="e336a-188">Çift **WorkflowVersionMap.cs** (veya **WorkflowVersionMap.vb**) altında **NumberGuessWorkflowHost** açmak için proje.</span><span class="sxs-lookup"><span data-stu-id="e336a-188">Double-click **WorkflowVersionMap.cs** (or **WorkflowVersionMap.vb**) under the **NumberGuessWorkflowHost** project to open it.</span></span>  
  
3.  <span data-ttu-id="e336a-189">Altı mevcut iş akışı kimlik bildirimlerine hemen altına üç yeni iş akışı kimliklerini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e336a-189">Add three new workflow identities just below the six existing workflow identity declarations.</span></span> <span data-ttu-id="e336a-190">Bu öğreticide `1.5.0.0` olarak kullanılan `WorkflowIdentity.Version` dinamik güncelleştirme kimlikleri için.</span><span class="sxs-lookup"><span data-stu-id="e336a-190">In this tutorial, `1.5.0.0` is used as the `WorkflowIdentity.Version` for the dynamic update identities.</span></span> <span data-ttu-id="e336a-191">Bu yeni `v15` kimlikleri kullanılabilir iş akışı dinamik olarak güncelleştirilen kalıcı iş akışı örnekleri için doğru iş akışı tanımı belirtin.</span><span class="sxs-lookup"><span data-stu-id="e336a-191">These new `v15` workflow identities will be used provide the correct workflow definition for the dynamically updated persisted workflow instances.</span></span>  
  
    ```vb  
    'Current version identities.  
    Public StateMachineNumberGuessIdentity As WorkflowIdentity  
    Public FlowchartNumberGuessIdentity As WorkflowIdentity  
    Public SequentialNumberGuessIdentity As WorkflowIdentity  
  
    'v1 identities.  
    Public StateMachineNumberGuessIdentity_v1 As WorkflowIdentity  
    Public FlowchartNumberGuessIdentity_v1 As WorkflowIdentity  
    Public SequentialNumberGuessIdentity_v1 As WorkflowIdentity  
  
    'v1.5 (Dynamimc Update) identities.  
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
  
4.  <span data-ttu-id="e336a-192">Oluşturucu sonuna aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e336a-192">Add the following code at the end of the constructor.</span></span> <span data-ttu-id="e336a-193">Bu kod, dinamik güncelleştirme iş akışı kimlikleri başlatır, ilgili iş akışı tanımları yükler ve bunları iş akışı sürümü sözlüğe ekler.</span><span class="sxs-lookup"><span data-stu-id="e336a-193">This code initializes the dynamic update workflow identities, loads the corresponding workflow definitions, and adds them to the workflow version dictionary.</span></span>  
  
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
  
     <span data-ttu-id="e336a-194">Aşağıdaki örnek, tamamlanan, `WorkflowVersionMap` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e336a-194">The following example is the completed `WorkflowVersionMap` class.</span></span>  
  
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
  
        'v1.5 (Dynamimc Update) identities.  
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
  
5.  <span data-ttu-id="e336a-195">Projeyi oluşturmak için CTRL+SHIFT+B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="e336a-195">Press CTRL+SHIFT+B to build the project.</span></span>  
  
###  <a name="BKMK_ApplyUpdate"></a> <span data-ttu-id="e336a-196">Dinamik güncelleştirmeleri uygulamak için</span><span class="sxs-lookup"><span data-stu-id="e336a-196">To apply the dynamic updates</span></span>  
  
1.  <span data-ttu-id="e336a-197">Sağ **WF45GettingStartedTutorial** içinde **Çözüm Gezgini** ve **Ekle**, **yeni proje**.</span><span class="sxs-lookup"><span data-stu-id="e336a-197">Right-click **WF45GettingStartedTutorial** in **Solution Explorer** and choose **Add**, **New Project**.</span></span>  
  
2.  <span data-ttu-id="e336a-198">İçinde **yüklü** düğümünü **Visual C#**, **Windows** (veya **Visual Basic**, **Windows**).</span><span class="sxs-lookup"><span data-stu-id="e336a-198">In the **Installed** node, select **Visual C#**, **Windows** (or **Visual Basic**, **Windows**).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e336a-199">Hangi programlama diline bağlı olarak, Visual Studio'da birincil dili olarak yapılandırılmış **Visual C#** veya **Visual Basic** düğümü altında olabilir **diğer diller** düğümünde **yüklü** düğümü.</span><span class="sxs-lookup"><span data-stu-id="e336a-199">Depending on which programming language is configured as the primary language in Visual Studio, the **Visual C#** or **Visual Basic** node may be under the **Other Languages** node in the **Installed** node.</span></span>  
  
     <span data-ttu-id="e336a-200">Emin **.NET Framework 4.5** .NET Framework sürüm aşağı açılan listeden seçilen.</span><span class="sxs-lookup"><span data-stu-id="e336a-200">Ensure that **.NET Framework 4.5** is selected in the .NET Framework version drop-down list.</span></span> <span data-ttu-id="e336a-201">Seçin **konsol uygulaması** gelen **Windows** listesi.</span><span class="sxs-lookup"><span data-stu-id="e336a-201">Select **Console Application** from the **Windows** list.</span></span> <span data-ttu-id="e336a-202">Tür **ApplyDynamicUpdate** içine **adı** kutusuna ve tıklatın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="e336a-202">Type **ApplyDynamicUpdate** into the **Name** box and click **OK**.</span></span>  
  
3.  <span data-ttu-id="e336a-203">Sağ **ApplyDynamicUpdate** içinde **Çözüm Gezgini** ve **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="e336a-203">Right-click **ApplyDynamicUpdate** in **Solution Explorer** and choose **Add Reference**.</span></span>  
  
4.  <span data-ttu-id="e336a-204">Tıklayın **çözüm** ve yanındaki kutuyu işaretleyin **NumberGuessWorkflowHost**.</span><span class="sxs-lookup"><span data-stu-id="e336a-204">Click **Solution** and check the box next to **NumberGuessWorkflowHost**.</span></span> <span data-ttu-id="e336a-205">Bu başvuru gerektiği şekilde `ApplyDynamicUpdate` kullanabilirsiniz `NumberGuessWorkflowHost.WorkflowVersionMap` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e336a-205">This reference is needed so that `ApplyDynamicUpdate` can use the `NumberGuessWorkflowHost.WorkflowVersionMap` class.</span></span>  
  
5.  <span data-ttu-id="e336a-206">Seçin **Framework** gelen **derlemeleri** düğümünde **Başvuru Ekle** listesi.</span><span class="sxs-lookup"><span data-stu-id="e336a-206">Select **Framework** from the **Assemblies** node in the **Add Reference** list.</span></span> <span data-ttu-id="e336a-207">Tür **System.Activities** içine **arama derlemeleri** kutusu.</span><span class="sxs-lookup"><span data-stu-id="e336a-207">Type **System.Activities** into the **Search Assemblies** box.</span></span> <span data-ttu-id="e336a-208">Bu derlemeleri filtreleyin ve istenen başvurular seçmeyi kolaylaştırmak.</span><span class="sxs-lookup"><span data-stu-id="e336a-208">This will filter the assemblies and make the desired references easier to select.</span></span>  
  
6.  <span data-ttu-id="e336a-209">Yanında onay **System.Activities** gelen **arama sonuçları** listesi.</span><span class="sxs-lookup"><span data-stu-id="e336a-209">Check the checkbox beside **System.Activities** from the **Search Results** list.</span></span>  
  
7.  <span data-ttu-id="e336a-210">Türü **serileştirme** içine **arama derlemeleri** kutusuna ve yanında onay **System.Runtime.Serialization** gelen **arama sonuçları**  listesi.</span><span class="sxs-lookup"><span data-stu-id="e336a-210">Type **Serialization** into the **Search Assemblies** box, and check the checkbox beside **System.Runtime.Serialization** from the **Search Results** list.</span></span>  
  
8.  <span data-ttu-id="e336a-211">Tür **DurableInstancing** içine **arama derlemeleri** kutusuna ve yanında onay **System.Activities.durableınstancing** ve  **System.Runtime.DurableInstancing** gelen **arama sonuçları** listesi.</span><span class="sxs-lookup"><span data-stu-id="e336a-211">Type **DurableInstancing** into the **Search Assemblies** box, and check the checkbox beside **System.Activities.DurableInstancing** and **System.Runtime.DurableInstancing** from the **Search Results** list.</span></span>  
  
9. <span data-ttu-id="e336a-212">Tıklayın **Tamam** kapatmak için **başvuru Yöneticisi** ve başvuruları ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e336a-212">Click **OK** to close **Reference Manager** and add the references.</span></span>  
  
10. <span data-ttu-id="e336a-213">Sağ **ApplyDynamicUpdate** Çözüm Gezgini'nde seçin **Ekle**, **sınıfı**.</span><span class="sxs-lookup"><span data-stu-id="e336a-213">Right-click **ApplyDynamicUpdate** in Solution Explorer and choose **Add**, **Class**.</span></span> <span data-ttu-id="e336a-214">Tür `DynamicUpdateInfo` içine **adı** kutusuna ve tıklatın **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="e336a-214">Type `DynamicUpdateInfo` into the **Name** box and click **Add**.</span></span>  
  
11. <span data-ttu-id="e336a-215">Aşağıdaki iki üye ekleme `DynamicUpdateInfo` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e336a-215">Add the following two members to the `DynamicUpdateInfo` class.</span></span> <span data-ttu-id="e336a-216">Aşağıdaki örnek, tamamlanan, `DynamicUpdateInfo` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e336a-216">The following example is the completed `DynamicUpdateInfo` class.</span></span> <span data-ttu-id="e336a-217">Bu sınıf, bir iş akışı örneği güncelleştirildiğinde kullanılan yeni bir iş akışı kimliği ve güncelleştirme eşlemesi hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="e336a-217">This class contains information on the update map and new workflow identity used when a workflow instance is updated.</span></span>  
  
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
  
12. <span data-ttu-id="e336a-218">Aşağıdaki `using` (veya `Imports`) deyimini dosyanın diğer üst `using` (veya `Imports`) ifadeleri.</span><span class="sxs-lookup"><span data-stu-id="e336a-218">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Activities  
    Imports System.Activities.DynamicUpdate  
    ```  
  
    ```csharp  
    using System.Activities;  
    using System.Activities.DynamicUpdate;  
    ```  
  
13. <span data-ttu-id="e336a-219">Çift **Program.cs** (veya **Module1.vb**) Çözüm Gezgini'nde.</span><span class="sxs-lookup"><span data-stu-id="e336a-219">Double-click **Program.cs** (or **Module1.vb**) in Solution Explorer.</span></span>  
  
14. <span data-ttu-id="e336a-220">Aşağıdaki `using` (veya `Imports`) deyimini dosyanın diğer üst `using` (veya `Imports`) ifadeleri.</span><span class="sxs-lookup"><span data-stu-id="e336a-220">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
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
  
15. <span data-ttu-id="e336a-221">Aşağıdaki bağlantı dizesi üye eklemek `Program` sınıfı (veya `Module1`).</span><span class="sxs-lookup"><span data-stu-id="e336a-221">Add the following connection string member to the `Program` class (or `Module1`).</span></span>  
  
    ```vb  
    Const connectionString = "Server=.\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI"  
    ```  
  
    ```csharp  
    const string connectionString = "Server=.\\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI";  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="e336a-222">Bağlantı dizesi sunucu adı SQL Server sürümüne bağlı olarak farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="e336a-222">Depending on your edition of SQL Server, the connection string server name may be different.</span></span>  
  
16. <span data-ttu-id="e336a-223">Aşağıdaki `GetIDs` yönteme `Program` sınıfı (veya `Module1`).</span><span class="sxs-lookup"><span data-stu-id="e336a-223">Add the following `GetIDs` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="e336a-224">Bu yöntem, kalıcı iş akışı örnek kimlikleri listesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="e336a-224">This method returns a list of persisted workflow instance ids.</span></span>  
  
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
  
17. <span data-ttu-id="e336a-225">Aşağıdaki `LoadMap` yönteme `Program` sınıfı (veya `Module1`).</span><span class="sxs-lookup"><span data-stu-id="e336a-225">Add the following `LoadMap` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="e336a-226">Bu yöntem eşleyen sözlük oluşturur `v1` iş akışı kimlikleri güncelleştirme haritalara ve karşılık gelen güncelleştirmek için kullanılan yeni bir iş akışı kimlikleri iş akışı örneği kalıcı.</span><span class="sxs-lookup"><span data-stu-id="e336a-226">This method creates a dictionary that maps `v1` workflow identities to the update maps and new workflow identities used to update the corresponding persisted workflow instances.</span></span>  
  
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
  
18. <span data-ttu-id="e336a-227">Aşağıdaki `LoadMaps` yönteme `Program` sınıfı (veya `Module1`).</span><span class="sxs-lookup"><span data-stu-id="e336a-227">Add the following `LoadMaps` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="e336a-228">Bu yöntem, üç güncelleştirme haritalar yükler ve eşleyen sözlük oluşturur `v1` iş akışı kimlikleri güncelleştirme eşlemeleri.</span><span class="sxs-lookup"><span data-stu-id="e336a-228">This method loads the three update maps and creates a dictionary that maps `v1` workflow identities to the update maps.</span></span>  
  
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
  
19. <span data-ttu-id="e336a-229">Aşağıdaki kodu ekleyin `Main`.</span><span class="sxs-lookup"><span data-stu-id="e336a-229">Add the following code to `Main`.</span></span> <span data-ttu-id="e336a-230">Bu kod kalıcı iş akışı örnekleri ve her inceler yinelenir `WorkflowIdentity`.</span><span class="sxs-lookup"><span data-stu-id="e336a-230">This code iterates the persisted workflow instances and examines each `WorkflowIdentity`.</span></span> <span data-ttu-id="e336a-231">Varsa `WorkflowIdentity` eşleyen bir `v1` iş akışı örneği bir `WorkflowApplication` güncelleştirilmiş iş akışı tanımı ve güncelleştirilmiş iş akışı kimliği ile yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="e336a-231">If the `WorkflowIdentity` maps to a `v1` workflow instance, a `WorkflowApplication` is configured with the updated workflow definition and an updated workflow identity.</span></span> <span data-ttu-id="e336a-232">Ardından, `WorkflowApplication.Load` örneği ve dinamik güncelleştirme eşlemesi geçerli güncelleştirme eşlemesi ile adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="e336a-232">Next, `WorkflowApplication.Load` is called with the instance and the update map, which applies the dynamic update map.</span></span> <span data-ttu-id="e336a-233">Güncelleştirme uygulandıktan sonra güncelleştirilmiş örneği çağrısıyla kalıcıdır `Unload`.</span><span class="sxs-lookup"><span data-stu-id="e336a-233">Once the update is applied, the updated instance is persisted with a call to `Unload`.</span></span>  
  
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
  
20. <span data-ttu-id="e336a-234">Sağ **ApplyDynamicUpdate** içinde **Çözüm Gezgini** ve **başlangıç projesi olarak ayarla**.</span><span class="sxs-lookup"><span data-stu-id="e336a-234">Right-click **ApplyDynamicUpdate** in **Solution Explorer** and choose **Set as StartUp Project**.</span></span>  
  
21. <span data-ttu-id="e336a-235">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın ve çalıştırmak için CTRL + F5 tuşuna basarak `ApplyDynamicUpdate` uygulama ve kalıcı iş akışı örnekleri güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="e336a-235">Press CTRL+SHIFT+B to build the solution, and then press CTRL+F5 to run the `ApplyDynamicUpdate` application and update the persisted workflow instances.</span></span> <span data-ttu-id="e336a-236">Aşağıdakine benzer bir çıktı görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e336a-236">You should see output similar to the following.</span></span> <span data-ttu-id="e336a-237">Güncelleştirilmiş sürüm 2.0.0.0 iş akışlarının sırada sürüm 1.0.0.0 iş akışları 1.5.0.0, sürümüne güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e336a-237">The version 1.0.0.0 workflows are updated to version 1.5.0.0, while the version 2.0.0.0 workflows are not updated.</span></span>  
  
 <span data-ttu-id="e336a-238">**İnceleme: StateMachineNumberGuessWorkflow; Sürüm 1.0.0.0 =**</span><span class="sxs-lookup"><span data-stu-id="e336a-238">**Inspecting: StateMachineNumberGuessWorkflow; Version=1.0.0.0**</span></span>  
<span data-ttu-id="e336a-239">**İçin güncelleştirilmiştir: StateMachineNumberGuessWorkflow; Sürüm 1.5.0.0 =** </span><span class="sxs-lookup"><span data-stu-id="e336a-239">**Updated to: StateMachineNumberGuessWorkflow; Version=1.5.0.0** </span></span>  
<span data-ttu-id="e336a-240">**İnceleme: StateMachineNumberGuessWorkflow; Sürüm 1.0.0.0 =** </span><span class="sxs-lookup"><span data-stu-id="e336a-240">**Inspecting: StateMachineNumberGuessWorkflow; Version=1.0.0.0** </span></span>  
<span data-ttu-id="e336a-241">**İçin güncelleştirilmiştir: StateMachineNumberGuessWorkflow; Sürüm 1.5.0.0 =** </span><span class="sxs-lookup"><span data-stu-id="e336a-241">**Updated to: StateMachineNumberGuessWorkflow; Version=1.5.0.0** </span></span>  
<span data-ttu-id="e336a-242">**İnceleme: FlowchartNumberGuessWorkflow; Sürüm 1.0.0.0 =** </span><span class="sxs-lookup"><span data-stu-id="e336a-242">**Inspecting: FlowchartNumberGuessWorkflow; Version=1.0.0.0** </span></span>  
<span data-ttu-id="e336a-243">**İçin güncelleştirilmiştir: FlowchartNumberGuessWorkflow; Sürüm 1.5.0.0 =** </span><span class="sxs-lookup"><span data-stu-id="e336a-243">**Updated to: FlowchartNumberGuessWorkflow; Version=1.5.0.0** </span></span>  
<span data-ttu-id="e336a-244">**İnceleme: FlowchartNumberGuessWorkflow; Sürüm 1.0.0.0 =** </span><span class="sxs-lookup"><span data-stu-id="e336a-244">**Inspecting: FlowchartNumberGuessWorkflow; Version=1.0.0.0** </span></span>  
<span data-ttu-id="e336a-245">**İçin güncelleştirilmiştir: FlowchartNumberGuessWorkflow; Sürüm 1.5.0.0 =** </span><span class="sxs-lookup"><span data-stu-id="e336a-245">**Updated to: FlowchartNumberGuessWorkflow; Version=1.5.0.0** </span></span>  
<span data-ttu-id="e336a-246">**İnceleme: SequentialNumberGuessWorkflow; Sürüm 1.0.0.0 =** </span><span class="sxs-lookup"><span data-stu-id="e336a-246">**Inspecting: SequentialNumberGuessWorkflow; Version=1.0.0.0** </span></span>  
<span data-ttu-id="e336a-247">**İçin güncelleştirilmiştir: SequentialNumberGuessWorkflow; Sürüm 1.5.0.0 =** </span><span class="sxs-lookup"><span data-stu-id="e336a-247">**Updated to: SequentialNumberGuessWorkflow; Version=1.5.0.0** </span></span>  
<span data-ttu-id="e336a-248">**İnceleme: SequentialNumberGuessWorkflow; Sürüm 1.0.0.0 =** </span><span class="sxs-lookup"><span data-stu-id="e336a-248">**Inspecting: SequentialNumberGuessWorkflow; Version=1.0.0.0** </span></span>  
<span data-ttu-id="e336a-249">**İçin güncelleştirilmiştir: SequentialNumberGuessWorkflow; Sürüm 1.5.0.0 =** </span><span class="sxs-lookup"><span data-stu-id="e336a-249">**Updated to: SequentialNumberGuessWorkflow; Version=1.5.0.0** </span></span>  
<span data-ttu-id="e336a-250">**İnceleme: SequentialNumberGuessWorkflow; Sürüm 1.0.0.0 =** </span><span class="sxs-lookup"><span data-stu-id="e336a-250">**Inspecting: SequentialNumberGuessWorkflow; Version=1.0.0.0** </span></span>  
<span data-ttu-id="e336a-251">**İçin güncelleştirilmiştir: SequentialNumberGuessWorkflow; Sürüm 1.5.0.0 =** </span><span class="sxs-lookup"><span data-stu-id="e336a-251">**Updated to: SequentialNumberGuessWorkflow; Version=1.5.0.0** </span></span>  
<span data-ttu-id="e336a-252">**İnceleme: StateMachineNumberGuessWorkflow; Sürüm 1.0.0.0 =** </span><span class="sxs-lookup"><span data-stu-id="e336a-252">**Inspecting: StateMachineNumberGuessWorkflow; Version=1.0.0.0** </span></span>  
<span data-ttu-id="e336a-253">**İçin güncelleştirilmiştir: StateMachineNumberGuessWorkflow; Sürüm 1.5.0.0 =** </span><span class="sxs-lookup"><span data-stu-id="e336a-253">**Updated to: StateMachineNumberGuessWorkflow; Version=1.5.0.0** </span></span>  
<span data-ttu-id="e336a-254">**İnceleme: FlowchartNumberGuessWorkflow; Sürüm 1.0.0.0 =** </span><span class="sxs-lookup"><span data-stu-id="e336a-254">**Inspecting: FlowchartNumberGuessWorkflow; Version=1.0.0.0** </span></span>  
<span data-ttu-id="e336a-255">**İçin güncelleştirilmiştir: FlowchartNumberGuessWorkflow; Sürüm 1.5.0.0 =** </span><span class="sxs-lookup"><span data-stu-id="e336a-255">**Updated to: FlowchartNumberGuessWorkflow; Version=1.5.0.0** </span></span>  
<span data-ttu-id="e336a-256">**İnceleme: StateMachineNumberGuessWorkflow; Sürüm 2.0.0.0 =** </span><span class="sxs-lookup"><span data-stu-id="e336a-256">**Inspecting: StateMachineNumberGuessWorkflow; Version=2.0.0.0** </span></span>  
<span data-ttu-id="e336a-257">**İnceleme: StateMachineNumberGuessWorkflow; Sürüm 2.0.0.0 =** </span><span class="sxs-lookup"><span data-stu-id="e336a-257">**Inspecting: StateMachineNumberGuessWorkflow; Version=2.0.0.0** </span></span>  
<span data-ttu-id="e336a-258">**İnceleme: FlowchartNumberGuessWorkflow; Sürüm 2.0.0.0 =** </span><span class="sxs-lookup"><span data-stu-id="e336a-258">**Inspecting: FlowchartNumberGuessWorkflow; Version=2.0.0.0** </span></span>  
<span data-ttu-id="e336a-259">**İnceleme: FlowchartNumberGuessWorkflow; Sürüm 2.0.0.0 =** </span><span class="sxs-lookup"><span data-stu-id="e336a-259">**Inspecting: FlowchartNumberGuessWorkflow; Version=2.0.0.0** </span></span>  
<span data-ttu-id="e336a-260">**İnceleme: SequentialNumberGuessWorkflow; Sürüm 2.0.0.0 =** </span><span class="sxs-lookup"><span data-stu-id="e336a-260">**Inspecting: SequentialNumberGuessWorkflow; Version=2.0.0.0** </span></span>  
<span data-ttu-id="e336a-261">**İnceleme: SequentialNumberGuessWorkflow; Sürüm 2.0.0.0 =** </span><span class="sxs-lookup"><span data-stu-id="e336a-261">**Inspecting: SequentialNumberGuessWorkflow; Version=2.0.0.0** </span></span>  
<span data-ttu-id="e336a-262">**Devam etmek için herhangi bir tuşa basın...**</span><span class="sxs-lookup"><span data-stu-id="e336a-262">**Press any key to continue . . .**</span></span>  
  
###  <a name="BKMK_BuildAndRun"></a> <span data-ttu-id="e336a-263">Güncelleştirilmiş iş akışlarıyla uygulamayı çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="e336a-263">To run the application with the updated workflows</span></span>  
  
1.  <span data-ttu-id="e336a-264">Sağ **NumberGuessWorkflowHost** içinde **Çözüm Gezgini** ve **başlangıç projesi olarak ayarla**.</span><span class="sxs-lookup"><span data-stu-id="e336a-264">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Set as StartUp Project**.</span></span>  
  
2.  <span data-ttu-id="e336a-265">Uygulamayı çalıştırmak için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="e336a-265">Press CTRL+F5 to run the application.</span></span>  
  
3.  <span data-ttu-id="e336a-266">Tıklayın **yeni oyun** yeni iş akışını başlatmak ve iş akışını gösteren durum pencere sürümü aşağıdaki bilgileri not için bir `v2` iş akışı.</span><span class="sxs-lookup"><span data-stu-id="e336a-266">Click **New Game** to start a new workflow and note the version information below the status window that indicates the workflow is a `v2` workflow.</span></span>  
  
4.  <span data-ttu-id="e336a-267">Birini seçin `v1` başında başlattığınız iş akışları [nasıl yapılır: bir iş akışı yan yana birden çok sürümünü konak](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md) konu.</span><span class="sxs-lookup"><span data-stu-id="e336a-267">Select one of the `v1` workflows you started at the beginning of the [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md) topic.</span></span> <span data-ttu-id="e336a-268">Sürüm bilgileri durum penceresi altında iş akışı bir sürüm olduğunu gösteren Not **1.5.0.0** iş akışı.</span><span class="sxs-lookup"><span data-stu-id="e336a-268">Note that the version information under the status window indicates that the workflow is a version **1.5.0.0** workflow.</span></span> <span data-ttu-id="e336a-269">Bunlar çok yüksek veya düşük dışında hiçbir bilgi hakkında önceki tahmin belirtilen olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e336a-269">Note that there is no information indicated about previous guesses other than whether they were too high or too low.</span></span>  
  
 <span data-ttu-id="e336a-270">**Lütfen 1 ile 10 arasında bir sayı girin**</span><span class="sxs-lookup"><span data-stu-id="e336a-270">**Please enter a number between 1 and 10**</span></span>  
<span data-ttu-id="e336a-271">**Çok düşük tahmininizdir.**</span><span class="sxs-lookup"><span data-stu-id="e336a-271">**Your guess is too low.**</span></span>  
  
5.  <span data-ttu-id="e336a-272">Not `InstanceId` ve iş akışı tamamlanana kadar tahmin girin.</span><span class="sxs-lookup"><span data-stu-id="e336a-272">Make a note of the `InstanceId` and then enter guesses until the workflow completes.</span></span> <span data-ttu-id="e336a-273">Durum penceresi tahmin içeriği hakkında bilgi gösterir çünkü `WriteLine` etkinlikleri, dinamik güncelleştirme ile güncelleştirildi.</span><span class="sxs-lookup"><span data-stu-id="e336a-273">The status window displays information about the content of the guess because the `WriteLine` activities were updated by the dynamic update.</span></span>  
  
 <span data-ttu-id="e336a-274">**Lütfen 1 ile 10 arasında bir sayı girin**</span><span class="sxs-lookup"><span data-stu-id="e336a-274">**Please enter a number between 1 and 10**</span></span>  
<span data-ttu-id="e336a-275">**Çok düşük tahmininizdir.** </span><span class="sxs-lookup"><span data-stu-id="e336a-275">**Your guess is too low.** </span></span>  
<span data-ttu-id="e336a-276">**Lütfen 1 ile 10 arasında bir sayı girin** </span><span class="sxs-lookup"><span data-stu-id="e336a-276">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="e336a-277">**5 çok düşüktür.** </span><span class="sxs-lookup"><span data-stu-id="e336a-277">**5 is too low.** </span></span>  
<span data-ttu-id="e336a-278">**Lütfen 1 ile 10 arasında bir sayı girin** </span><span class="sxs-lookup"><span data-stu-id="e336a-278">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="e336a-279">**7 çok yüksektir.** </span><span class="sxs-lookup"><span data-stu-id="e336a-279">**7 is too high.** </span></span>  
<span data-ttu-id="e336a-280">**Lütfen 1 ile 10 arasında bir sayı girin** </span><span class="sxs-lookup"><span data-stu-id="e336a-280">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="e336a-281">**Tebrikler, sayı 4 kapatır tahmin.**</span><span class="sxs-lookup"><span data-stu-id="e336a-281">**Congratulations, you guessed the number in 4 turns.**</span></span>  
  
6.  <span data-ttu-id="e336a-282">Windows Gezgini'ni açın ve gidin **NumberGuessWorkflowHost\bin\debug** klasörü (veya **bin\release** proje ayarlarınıza bağlı olarak) karşılık gelen Not Defteri'ni kullanarak izleme dosyasını açın Tamamlanan iş akışı için.</span><span class="sxs-lookup"><span data-stu-id="e336a-282">Open Windows Explorer and navigate to the **NumberGuessWorkflowHost\bin\debug** folder (or **bin\release** depending on your project settings) and open the tracking file using Notepad that corresponds to the completed workflow.</span></span> <span data-ttu-id="e336a-283">Not yapmadıysanız `InstanceId` doğru izleme dosyası kullanarak tanımlamak çözebileceğiniz **değiştirilme tarihi** Windows Explorer'da bilgileri.</span><span class="sxs-lookup"><span data-stu-id="e336a-283">If you did not make a note of the `InstanceId` you may be able to identify the correct tracking file by using the **Date modified** information in Windows Explorer.</span></span> <span data-ttu-id="e336a-284">İzleme bilgilerini son satırının yeni eklenen çıktısını içeren `WriteLine` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="e336a-284">The last line of the tracking information contains the output of the newly added `WriteLine` activity.</span></span>  
  
 <span data-ttu-id="e336a-285">**Lütfen 1 ile 10 arasında bir sayı girin**</span><span class="sxs-lookup"><span data-stu-id="e336a-285">**Please enter a number between 1 and 10**</span></span>  
<span data-ttu-id="e336a-286">**Çok düşük tahmininizdir.** </span><span class="sxs-lookup"><span data-stu-id="e336a-286">**Your guess is too low.** </span></span>  
<span data-ttu-id="e336a-287">**Lütfen 1 ile 10 arasında bir sayı girin** </span><span class="sxs-lookup"><span data-stu-id="e336a-287">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="e336a-288">**5 çok düşüktür.** </span><span class="sxs-lookup"><span data-stu-id="e336a-288">**5 is too low.** </span></span>  
<span data-ttu-id="e336a-289">**Lütfen 1 ile 10 arasında bir sayı girin** </span><span class="sxs-lookup"><span data-stu-id="e336a-289">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="e336a-290">**7 çok yüksektir.** </span><span class="sxs-lookup"><span data-stu-id="e336a-290">**7 is too high.** </span></span>  
<span data-ttu-id="e336a-291">**Lütfen 1 ile 10 arasında bir sayı girin** </span><span class="sxs-lookup"><span data-stu-id="e336a-291">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="e336a-292">**6 doğrudur. Bu 4 kapatır tahmin.**</span><span class="sxs-lookup"><span data-stu-id="e336a-292">**6 is correct. You guessed it in 4 turns.**</span></span>  
  
###  <a name="BKMK_StartPreviousVersions"></a> <span data-ttu-id="e336a-293">İş Akışları'nın önceki sürümlerini başlangıç etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="e336a-293">To enable starting previous versions of the workflows</span></span>  
 <span data-ttu-id="e336a-294">Güncelleştirilecek iş akışları dışında çalıştırırsanız, değiştirebileceğiniz `NumberGuessWorkflowHost` iş akışları'nın önceki sürümlerini başlangıç etkinleştirmek için uygulama.</span><span class="sxs-lookup"><span data-stu-id="e336a-294">If you run out of workflows to update, you can modify the `NumberGuessWorkflowHost` application to enable starting previous versions of the workflows.</span></span>  
  
1.  <span data-ttu-id="e336a-295">Çift **WorkflowHostForm** içinde **Çözüm Gezgini**seçip **WorkflowType** birleşik giriş kutusu.</span><span class="sxs-lookup"><span data-stu-id="e336a-295">Double-click **WorkflowHostForm** in **Solution Explorer**, and select the **WorkflowType** combo box.</span></span>  
  
2.  <span data-ttu-id="e336a-296">İçinde **özellikleri** penceresinde **öğeleri** özelliği ve düzenlemek için üç nokta düğmesini tıklatın **öğeleri** koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="e336a-296">In the **Properties** window, select the **Items** property and click the ellipsis button to edit the **Items** collection.</span></span>  
  
3.  <span data-ttu-id="e336a-297">Aşağıdaki üç öğe koleksiyonuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e336a-297">Add the following three items to the collection.</span></span>  
  
    ```
    StateMachineNumberGuessWorkflow v1  
    FlowchartNumberGuessWorkflow v1  
    SequentialNumberGuessWorkflow v1  
    ```  
  
     <span data-ttu-id="e336a-298">Tamamlanan `Items` altı öğe koleksiyonu olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e336a-298">The completed `Items` collection will have six items.</span></span>  
  
    ```
    StateMachineNumberGuessWorkflow  
    FlowchartNumberGuessWorkflow  
    SequentialNumberGuessWorkflow  
    StateMachineNumberGuessWorkflow v1  
    FlowchartNumberGuessWorkflow v1  
    SequentialNumberGuessWorkflow v1  
    ```  
  
4.  <span data-ttu-id="e336a-299">Çift **WorkflowHostForm** içinde **Çözüm Gezgini**seçip **kodu görüntüle**.</span><span class="sxs-lookup"><span data-stu-id="e336a-299">Double-click **WorkflowHostForm** in **Solution Explorer**, and select **View Code**.</span></span>  
  
5.  <span data-ttu-id="e336a-300">Üç yeni durumuna eklemek `switch` (veya `Select Case`) deyiminde `NewGame_Click` yeni öğeleri eşlemek için işleyici **WorkflowType** eşleşen iş akışı kimlikleri için birleşik giriş kutusu.</span><span class="sxs-lookup"><span data-stu-id="e336a-300">Add three new cases to the `switch` (or `Select Case`) statement in the `NewGame_Click` handler to map the new items in the **WorkflowType** combo box to the matching workflow identities.</span></span>  
  
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
  
     <span data-ttu-id="e336a-301">Aşağıdaki örnek, tam içerir `switch` (veya `Select Case`) deyimi.</span><span class="sxs-lookup"><span data-stu-id="e336a-301">The following example contains the complete `switch` (or `Select Case`) statement.</span></span>  
  
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
  
6.  <span data-ttu-id="e336a-302">Derleme ve uygulamayı çalıştırmak için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="e336a-302">Press CTRL+F5 to build and run the application.</span></span> <span data-ttu-id="e336a-303">Şimdi başlayabilirsiniz `v1` geçerli sürümler yanı sıra iş akışı sürümleri.</span><span class="sxs-lookup"><span data-stu-id="e336a-303">You can now start the `v1` versions of the workflow as well as the current versions.</span></span> <span data-ttu-id="e336a-304">Bu yeni örnekler dinamik olarak güncelleştirmek için çalıştırın **ApplyDynamicUpdate** uygulama.</span><span class="sxs-lookup"><span data-stu-id="e336a-304">To dynamically update these new instances, run the **ApplyDynamicUpdate** application.</span></span>
