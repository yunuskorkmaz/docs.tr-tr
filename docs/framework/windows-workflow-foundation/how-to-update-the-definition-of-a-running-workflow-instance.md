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
# <a name="how-to-update-the-definition-of-a-running-workflow-instance"></a>Nasıl yapılır: Çalışan İş Akışı Örneğinin Tanımını Güncelleştirme

Dinamik güncelleştirme, iş akışı uygulama geliştiricilerinin kalıcı bir iş akışı örneğinin iş akışı tanımını güncelleştirmesine yönelik bir mekanizma sağlar. Gerekli değişiklik, hata düzeltmesini veya yeni gereksinimleri uygulayabilir ya da beklenmeyen değişikliklere uyum sağlayabilir. Öğreticideki Bu adım, `v1` [nasıl yapılır: bir Iş akışının birden çok sürümünü yan yana barındırma](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)bölümünde sunulan yeni işlevlerle eşleşecek şekilde tahmin iş akışının kalıcı örneklerini değiştirmek için dinamik güncelleştirme 'nin nasıl kullanılacağını gösterir.

## <a name="in-this-topic"></a>Bu konuda

- [CreateUpdateMaps projesi oluşturmak için](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_CreateProject)

- [StateMachineNumberGuessWorkflow öğesini güncelleştirmek için](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_StateMachine)

- [FlowchartNumberGuessWorkflow öğesini güncelleştirmek için](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_Flowchart)

- [SequentialNumberGuessWorkflow güncelleştirmek için](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_Sequential)

- [CreateUpdateMaps uygulamasını derlemek ve çalıştırmak için](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_CreateUpdateMaps)

- [Güncelleştirilmiş iş akışı derlemesini derlemek için](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_BuildAssembly)

- [WorkflowVersionMap 'i yeni sürümlerle güncelleştirmek için](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_UpdateWorkflowVersionMap)

- [Dinamik güncelleştirmeleri uygulamak için](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_ApplyUpdate)

- [Uygulamayı güncelleştirilmiş iş akışlarıyla çalıştırmak için](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_BuildAndRun)

- [İş akışlarının önceki sürümlerini başlatmayı etkinleştirmek için](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_StartPreviousVersions)

### <a name="to-create-the-createupdatemaps-project"></a><a name="BKMK_CreateProject"></a> CreateUpdateMaps projesi oluşturmak için

1. **Çözüm Gezgini** 'de **WF45GettingStartedTutorial** öğesine sağ tıklayın ve **Ekle**, **Yeni proje** seçeneğini belirleyin.

2. **Yüklü** düğümde, **Visual C#**, **Windows** (veya **Visual Basic**, **Windows**) öğesini seçin.

    > [!NOTE]
    > Visual Studio 'da birincil dil olarak yapılandırılmış programlama diline bağlı olarak, **Visual C#** veya **Visual Basic** düğümü **yüklü** düğümdeki **diğer diller** düğümü altında olabilir.

     **.NET Framework 4,5** ' nin .NET Framework sürüm açılan listesinde seçildiğinden emin olun. **Windows** listesinden **konsol uygulaması** ' nı seçin. **Ad** kutusuna **Createupdatemaps** yazın ve **Tamam**' a tıklayın.

3. **Çözüm Gezgini** Içinde **Createupdatemaps** öğesine sağ tıklayın ve **Başvuru Ekle**' yi seçin.

4. **Başvuru Ekle** listesinde **derlemeler** düğümünden **Framework** ' ü seçin. Derlemeleri filtrelemek ve istenen başvuruların seçimi daha kolay hale getirmek için, **arama derlemeler** kutusuna **System. Activities** yazın.

5. **Arama sonuçları** listesinden **System. Activities** öğesinin yanındaki onay kutusunu işaretleyin.

6. **Derlemeleri ara** kutusuna **serileştirme** yazın ve **Arama sonuçları** listesinden **System. Runtime. Serialization** öğesinin yanındaki onay kutusunu işaretleyin.

7. **Derlemeleri ara** kutusuna **System. xaml** yazın ve **Arama sonuçları** listesinden **System. xaml** ' in yanındaki onay kutusunu işaretleyin.

8. **Başvuru Yöneticisi** ' ni kapatmak ve başvuruları eklemek için **Tamam** ' ı tıklatın.

9. Aşağıdaki `using` (veya `Imports` ) deyimlerini, diğer `using` (veya `Imports` ) deyimleriyle dosyanın en üstüne ekleyin.

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

10. Aşağıdaki iki dize üyesini `Program` sınıfına ekleyin (veya `Module1` ).

    ```vb
    Const mapPath = "..\..\..\PreviousVersions"
    Const definitionPath = "..\..\..\NumberGuessWorkflowActivities_du"
    ```

    ```csharp
    const string mapPath = @"..\..\..\PreviousVersions";
    const string definitionPath = @"..\..\..\NumberGuessWorkflowActivities_du";
    ```

11. `StartUpdate`Sınıfına aşağıdaki yöntemi ekleyin `Program` (veya `Module1` ). Bu yöntem, belirtilen XAML iş akışı tanımını bir öğesine yükler `ActivityBuilder` ve ardından çağırır `DynamicUpdate.PrepareForUpdate` . `PrepareForUpdate` içinde iş akışı tanımının bir kopyasını oluşturur `ActivityBuilder` . İş akışı tanımı değiştirildikten sonra, bu kopya, güncelleştirme haritasını oluşturmak için değiştirilen iş akışı tanımıyla birlikte kullanılır.

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

12. Sonra, aşağıdaki `CreateUpdateMethod` `Program` sınıfı (veya) sınıfına ekleyin `Module1` . Bu, DynamicUpdateServices. CreateUpdateMap 'i çağırarak dinamik bir güncelleştirme haritası oluşturur ve ardından belirtilen adı kullanarak güncelleştirme haritasını kaydeder. Bu güncelleştirme eşlemesi, iş akışı çalışma zamanının, ' de bulunan özgün iş akışı tanımı kullanılarak başlatılan, `ActivityBuilder` güncelleştirilmiş iş akışı tanımını kullanarak tamamlanması için gereken bilgileri içerir.

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

13. `SaveUpdatedDefinition`Sınıfına aşağıdaki yöntemi ekleyin `Program` (veya `Module1` ). Bu yöntem, güncelleştirme haritası oluşturulduktan sonra güncelleştirilmiş iş akışı tanımını kaydeder.

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

### <a name="to-update-statemachinenumberguessworkflow"></a><a name="BKMK_StateMachine"></a> StateMachineNumberGuessWorkflow öğesini güncelleştirmek için

1. Sınıfına bir ekleyin `CreateStateMachineUpdateMap` `Program` (veya `Module1` ).

    ```vb
    Private Sub CreateStateMachineUpdateMap()

    End Sub
    ```

    ```csharp
    private static void CreateStateMachineUpdateMap()
    {
    }
    ```

2. Bir çağrısı yapıp `StartUpdate` iş akışının kök etkinliğine bir başvuru alın `StateMachine` .

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

3. Ardından, `WriteLine` kullanıcının tahmininin çok yüksek veya çok düşük olduğunu görüntüleyen iki etkinliğin ifadelerini güncelleştirin; böylece [bir Iş akışının birden çok sürümünü yan yana barındırma](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).

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

4. Ardından, `WriteLine` Kapanış iletisini görüntüleyen yeni etkinliği ekleyin.

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

5. İş akışı güncelleştirildikten sonra `CreateUpdateMaps` ve çağırın `SaveUpdatedDefinition` . `CreateUpdateMaps` oluşturup kaydeder ve `DynamicUpdateMap` `SaveUpdatedDefinition` güncelleştirilmiş iş akışı tanımını kaydeder.

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

    Aşağıdaki örnek, tamamlanmış `CreateStateMachineUpdateMap` yöntemidir.

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

### <a name="to-update-flowchartnumberguessworkflow"></a><a name="BKMK_Flowchart"></a> FlowchartNumberGuessWorkflow öğesini güncelleştirmek için

1. Sınıfına aşağıdakileri ekleyin `CreateFlowchartUpdateMethod` `Program` (veya `Module1` ). Bu yöntem öğesine benzerdir `CreateStateMachineUpdateMap` . Bir çağrısıyla başlar `StartUpdate` , akış çizelgesi tanımını güncelleştirir ve güncelleştirme haritasını ve güncelleştirilmiş iş akışı tanımını kaydederek sonlanır.

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

### <a name="to-update-sequentialnumberguessworkflow"></a><a name="BKMK_Sequential"></a> SequentialNumberGuessWorkflow güncelleştirmek için

1. Sınıfına aşağıdakileri ekleyin `CreateSequentialUpdateMethod` `Program` (veya `Module1` ). Bu yöntem, diğer iki yönteme benzer. Bir çağrısıyla başlar `StartUpdate` , sıralı iş akışı tanımını güncelleştirir ve güncelleştirme haritasını ve güncelleştirilmiş iş akışı tanımını kaydederek tamamlanır.

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

### <a name="to-build-and-run-the-createupdatemaps-application"></a><a name="BKMK_CreateUpdateMaps"></a> CreateUpdateMaps uygulamasını derlemek ve çalıştırmak için

1. Yöntemini güncelleştirin `Main` ve aşağıdaki üç yöntem çağrılarını ekleyin. Bu yöntemler aşağıdaki bölümlere eklenir. Her yöntem, ilgili tahmin iş akışını güncelleştirir ve `DynamicUpdateMap` güncelleştirmeleri açıklayan bir oluşturur.

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

2. **Çözüm Gezgini** Içinde **Createupdatemaps** öğesine sağ tıklayın ve **Başlangıç projesi olarak ayarla**' yı seçin.

3. Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın ve ardından uygulamayı çalıştırmak için CTRL + F5 tuşlarına basın `CreateUpdateMaps` .

    > [!NOTE]
    > `CreateUpdateMaps`Uygulama çalışırken herhangi bir durum bilgisi görüntülemez, ancak **NumberGuessWorkflowActivities_du** klasörüne ve **PreviousVersions** klasörüne bakarsanız, güncelleştirilmiş iş akışı tanım dosyalarını ve güncelleştirme haritalarını görürsünüz.

    Güncelleştirme haritaları oluşturulduktan ve iş akışı tanımları güncelleştirildikten sonra, bir sonraki adım güncelleştirilmiş tanımları içeren güncelleştirilmiş bir iş akışı derlemesi oluşturmak için kullanılır.

### <a name="to-build-the-updated-workflow-assembly"></a><a name="BKMK_BuildAssembly"></a> Güncelleştirilmiş iş akışı derlemesini derlemek için

1. Visual Studio 2012 'nin ikinci bir örneğini açın.

2. **Dosya** menüsünden **Aç**, **Proje/çözüm** öğesini seçin.

3. [Nasıl yapılır: bir Iş akışının birden çok sürümünü yan yana barındırma](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)bölümünde oluşturduğunuz **NumberGuessWorkflowActivities_du** klasöre gidin, **NumberGuessWorkflowActivities. csproj** (veya **vbproj**) öğesini seçin ve **Aç**' a tıklayın.

4. **Çözüm Gezgini**' de, **SequentialNumberGuessWorkflow. xaml** ' e sağ tıklayıp **projeden çıkar**' ı seçin. **FlowchartNumberGuessWorkflow. xaml** ve **StateMachineNumberGuessWorkflow. xaml** için aynı şeyi yapın. Bu adım, iş akışı tanımlarının önceki sürümlerini projeden kaldırır.

5. **Proje** menüsünden **Varolan öğe Ekle** ' yi seçin.

6. [Nasıl yapılır: bir Iş akışının birden çok sürümünü yan yana barındırma](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)bölümünde oluşturduğunuz **NumberGuessWorkflowActivities_du** klasöre gidin.

7. **XAML dosyaları ( \* . xaml;) seçin \* . xoml)** açılır listesinden **dosya yazın** .

8. **SequentialNumberGuessWorkflow_du. xaml**, **FlowchartNumberGuessWorkflow_du. xaml** ve **StateMachineNumberGuessWorkflow_du. xaml** ' i seçin ve **Ekle**' ye tıklayın.

    > [!NOTE]
    > Tek seferde birden çok öğe seçmek için CTRL + tıklama.

    Bu adım, iş akışı tanımlarının güncelleştirilmiş sürümlerini projeye ekler.

9. Projeyi oluşturmak için CTRL+SHIFT+B tuşlarına basın.

10. **Dosya** menüsünden **çözümü kapat** ' ı seçin. Projenin çözüm dosyası gerekli değildir, bu nedenle Visual Studio 'Yu bir çözüm dosyası kaydetmeden kapatmak için **Hayır** ' a tıklayın. Visual Studio 'Yu kapatmak için **Dosya** menüsünden **Çıkış** ' ı seçin.

11. Windows Gezgini 'ni açın ve **NumberGuessWorkflowActivities_du \bin\Debug** klasörüne (veya proje ayarlarınıza bağlı olarak **bin\release** ) gidin.

12. **NumberGuessWorkflowActivities.dll** **NumberGuessWorkflowActivities_v15.dll** olarak yeniden adlandırın ve bunu [nasıl yapılır: bir iş akışının birden çok sürümünü yan yana barındırma](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)bölümünde oluşturduğunuz **PreviousVersions** klasörüne kopyalayın.

### <a name="to-update-workflowversionmap-with-the-new-versions"></a><a name="BKMK_UpdateWorkflowVersionMap"></a> WorkflowVersionMap 'i yeni sürümlerle güncelleştirmek için

1. Visual Studio 2012 ' in ilk örneğine dönün.

2. # **Guessworkflowwhost** projesi altındaki **WorkflowVersionMap.cs** (veya **WorkflowVersionMap. vb**) öğesine çift tıklayarak açın.

3. Mevcut altı iş akışı kimlik bildiriminin hemen altına üç yeni iş akışı kimliği ekleyin. Bu öğreticide, `1.5.0.0` `WorkflowIdentity.Version` dinamik güncelleştirme kimlikleri için olarak kullanılır. Bu yeni `v15` iş akışı kimlikleri, dinamik olarak güncellenen kalıcı iş akışı örnekleri için doğru iş akışı tanımını sağlamak üzere kullanılacaktır.

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

4. Oluşturucunun sonuna aşağıdaki kodu ekleyin. Bu kod, dinamik güncelleştirme iş akışı kimliklerini başlatır, karşılık gelen iş akışı tanımlarını yükler ve bunları iş akışı sürüm sözlüğüne ekler.

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

     Aşağıdaki örnek tamamlanan `WorkflowVersionMap` sınıftır.

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

5. Projeyi oluşturmak için CTRL+SHIFT+B tuşlarına basın.

### <a name="to-apply-the-dynamic-updates"></a><a name="BKMK_ApplyUpdate"></a> Dinamik güncelleştirmeleri uygulamak için

1. **Çözüm Gezgini** 'de **WF45GettingStartedTutorial** öğesine sağ tıklayın ve **Ekle**, **Yeni proje** seçeneğini belirleyin.

2. **Yüklü** düğümde, **Visual C#**, **Windows** (veya **Visual Basic**, **Windows**) öğesini seçin.

    > [!NOTE]
    > Visual Studio 'da birincil dil olarak yapılandırılmış programlama diline bağlı olarak, **Visual C#** veya **Visual Basic** düğümü **yüklü** düğümdeki **diğer diller** düğümü altında olabilir.

    **.NET Framework 4,5** ' nin .NET Framework sürüm açılan listesinde seçildiğinden emin olun. **Windows** listesinden **konsol uygulaması** ' nı seçin. **Ad** kutusuna **applydynamicupdate** yazın ve **Tamam**' a tıklayın.

3. **Çözüm Gezgini** Içinde **applydynamicupdate** öğesine sağ tıklayın ve **Başvuru Ekle**' yi seçin.

4. **Çözüm** ' e tıklayın ve **Numberguessworkflowwhost**' nin yanındaki kutuyu işaretleyin. Bu başvuru `ApplyDynamicUpdate` , sınıfını kullanabilmeniz için gereklidir `NumberGuessWorkflowHost.WorkflowVersionMap` .

5. **Başvuru Ekle** listesinde **derlemeler** düğümünden **Framework** ' ü seçin. **System. Activities** öğesini **arama derlemeler** kutusuna yazın. Bu, derlemeleri filtreleyecek ve istenen başvuruların seçimi daha kolay hale getirir.

6. **Arama sonuçları** listesinden **System. Activities** öğesinin yanındaki onay kutusunu işaretleyin.

7. **Derlemeleri ara** kutusuna **serileştirme** yazın ve **Arama sonuçları** listesinden **System. Runtime. Serialization** öğesinin yanındaki onay kutusunu işaretleyin.

8. **Arama derlemeleri** kutusuna **durableörneklemesini** yazın ve **Arama sonuçları** listesinden **System. Activities. Durableörnekınlist** ve **System. Runtime. durableörnek** ' in yanındaki onay kutusunu işaretleyin.

9. **Başvuru Yöneticisi** ' ni kapatmak ve başvuruları eklemek için **Tamam** ' ı tıklatın.

10. Çözüm Gezgini içinde **Applydynamicupdate** öğesine sağ tıklayın ve **Ekle**, **sınıf**' i seçin. `DynamicUpdateInfo` **Ad** kutusuna yazın ve **Ekle**' ye tıklayın.

11. Aşağıdaki iki üyeyi `DynamicUpdateInfo` sınıfına ekleyin. Aşağıdaki örnek tamamlanan `DynamicUpdateInfo` sınıftır. Bu sınıf, bir iş akışı örneği güncelleştirilirken kullanılan güncelleştirme haritası ve yeni iş akışı kimliği hakkındaki bilgileri içerir.

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

12. Aşağıdaki `using` (veya `Imports` ) deyimlerini, diğer `using` (veya `Imports` ) deyimleriyle dosyanın en üstüne ekleyin.

    ```vb
    Imports System.Activities
    Imports System.Activities.DynamicUpdate
    ```

    ```csharp
    using System.Activities;
    using System.Activities.DynamicUpdate;
    ```

13. Çözüm Gezgini içinde **program.cs** (veya **Module1. vb**) öğesine çift tıklayın.

14. Aşağıdaki `using` (veya `Imports` ) deyimlerini, diğer `using` (veya `Imports` ) deyimleriyle dosyanın en üstüne ekleyin.

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

15. Aşağıdaki bağlantı dizesi üyesini `Program` sınıfına ekleyin (veya `Module1` ).

    ```vb
    Const connectionString = "Server=.\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI"
    ```

    ```csharp
    const string connectionString = "Server=.\\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI";
    ```

    > [!NOTE]
    > SQL Server sürümüne bağlı olarak, bağlantı dizesi sunucu adı farklı olabilir.

16. `GetIDs`Sınıfına aşağıdaki yöntemi ekleyin `Program` (veya `Module1` ). Bu yöntem, kalıcı iş akışı örnek kimliklerinin bir listesini döndürür.

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

17. `LoadMap`Sınıfına aşağıdaki yöntemi ekleyin `Program` (veya `Module1` ). Bu yöntem, `v1` iş akışı kimliklerini güncelleştirme haritaları ile eşleyen bir sözlük ve ilgili kalıcı iş akışı örneklerini güncelleştirmek için kullanılan yeni iş akışı kimliklerini oluşturur.

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

18. `LoadMaps`Sınıfına aşağıdaki yöntemi ekleyin `Program` (veya `Module1` ). Bu yöntem, üç güncelleştirme haritalarını yükler ve `v1` iş akışı kimliklerini güncelleştirme eşlemeleriyle eşleyen bir sözlük oluşturur.

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

19. Aşağıdaki kodu `Main` içine ekleyin. Bu kod kalıcı iş akışı örneklerini yineler ve her bir inceler `WorkflowIdentity` . Bir `WorkflowIdentity` `v1` iş akışı örneğiyle eşleniyorsa, `WorkflowApplication` güncelleştirilmiş iş akışı tanımıyla ve güncelleştirilmiş iş akışı kimliğiyle yapılandırılır. Ardından, `WorkflowApplication.Load` örneği ve güncelleştirme haritası ile çağırılır ve bu, dinamik güncelleştirme haritasını uygular. Güncelleştirme uygulandıktan sonra, güncelleştirilmiş örnek öğesine çağrısıyla kalıcı hale getirilir `Unload` .

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

20. **Çözüm Gezgini** Için **applydynamicupdate** öğesine sağ tıklayın ve **Başlangıç projesi olarak ayarla**' yı seçin.

21. Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın ve ardından `ApplyDynamicUpdate` uygulamayı çalıştırmak ve kalıcı iş akışı örneklerini güncelleştirmek IÇIN CTRL + F5 tuşlarına basın. Aşağıdakine benzer bir çıktı görmeniz gerekir. Sürüm 1.0.0.0 iş akışları sürüm 1.5.0.0 olarak güncelleştirilir, ancak sürüm 2.0.0.0 iş akışları güncellenmez.

    **İnceleniyor: StateMachineNumberGuessWorkflow; Sürüm = 1.0.0.0**\
    **Şu şekilde güncelleştirildi: StateMachineNumberGuessWorkflow; Sürüm = 1.5.0.0**\
    **İnceleniyor: StateMachineNumberGuessWorkflow; Sürüm = 1.0.0.0**\
    **Şu şekilde güncelleştirildi: StateMachineNumberGuessWorkflow; Sürüm = 1.5.0.0**\
    **İnceleniyor: FlowchartNumberGuessWorkflow; Sürüm = 1.0.0.0**\
    **Şu şekilde güncelleştirildi: FlowchartNumberGuessWorkflow; Sürüm = 1.5.0.0**\
    **İnceleniyor: FlowchartNumberGuessWorkflow; Sürüm = 1.0.0.0**\
    **Şu şekilde güncelleştirildi: FlowchartNumberGuessWorkflow; Sürüm = 1.5.0.0**\
    **İnceleniyor: SequentialNumberGuessWorkflow; Sürüm = 1.0.0.0**\
    **Güncelleştirilme tarihi: SequentialNumberGuessWorkflow; Sürüm = 1.5.0.0**\
    **İnceleniyor: SequentialNumberGuessWorkflow; Sürüm = 1.0.0.0**\
    **Güncelleştirilme tarihi: SequentialNumberGuessWorkflow; Sürüm = 1.5.0.0**\
    **İnceleniyor: SequentialNumberGuessWorkflow; Sürüm = 1.0.0.0**\
    **Güncelleştirilme tarihi: SequentialNumberGuessWorkflow; Sürüm = 1.5.0.0**\
    **İnceleniyor: StateMachineNumberGuessWorkflow; Sürüm = 1.0.0.0**\
    **Şu şekilde güncelleştirildi: StateMachineNumberGuessWorkflow; Sürüm = 1.5.0.0**\
    **İnceleniyor: FlowchartNumberGuessWorkflow; Sürüm = 1.0.0.0**\
    **Şu şekilde güncelleştirildi: FlowchartNumberGuessWorkflow; Sürüm = 1.5.0.0**\
    **İnceleniyor: StateMachineNumberGuessWorkflow; Sürüm = 2.0.0.0**\
    **İnceleniyor: StateMachineNumberGuessWorkflow; Sürüm = 2.0.0.0**\
    **İnceleniyor: FlowchartNumberGuessWorkflow; Sürüm = 2.0.0.0**\
    **İnceleniyor: FlowchartNumberGuessWorkflow; Sürüm = 2.0.0.0**\
    **İnceleniyor: SequentialNumberGuessWorkflow; Sürüm = 2.0.0.0**\
    **İnceleniyor: SequentialNumberGuessWorkflow; Sürüm = 2.0.0.0**\
    **Devam etmek için herhangi bir tuşa basın...**

### <a name="to-run-the-application-with-the-updated-workflows"></a><a name="BKMK_BuildAndRun"></a> Uygulamayı güncelleştirilmiş iş akışlarıyla çalıştırmak için

1. **Çözüm Gezgini** Için **Numberguessworkflowwhost** öğesine sağ tıklayın ve **Başlangıç projesi olarak ayarla**' yı seçin.

2. Uygulamayı çalıştırmak için CTRL+F5'e basın.

3. Yeni **oyun** ' e tıklayarak yeni bir iş akışı başlatın ve iş akışının bir iş akışı olduğunu belirten durum penceresinin altındaki sürüm bilgilerini unutmayın `v2` .

4. `v1` [Nasıl yapılır: birden çok Iş akışının çoklu sürümlerini barındırma](how-to-host-multiple-versions-of-a-workflow-side-by-side.md) konusunun başlangıcında başlattığınız iş akışlarından birini seçin. Durum penceresi altındaki sürüm bilgileri, iş akışının bir sürüm **1.5.0.0** iş akışı olduğunu gösterir. Önceki tahminlerle ilgili olarak, çok yüksek veya çok düşük olup olmadıkları hakkında hiçbir bilgi bulunmadığını unutmayın.

    **Lütfen 1 ile 10 arasında bir sayı girin**\
    **Tahmininiz çok düşük.**

5. İş akışı tamamlanana kadar tahmin edilecek şekilde, ve değerlerini bir yere göz önünde `InstanceId` yazın. Durum penceresi, `WriteLine` etkinlik dinamik güncelleştirme tarafından güncelleştirildiğinden tahmin içeriğiyle ilgili bilgileri görüntüler.

    **Lütfen 1 ile 10 arasında bir sayı girin**\
    **Tahmininiz çok düşük.**\
    **Lütfen 1 ile 10 arasında bir sayı girin**\
    **5 çok düşük.**\
    **Lütfen 1 ile 10 arasında bir sayı girin**\
    **7 çok yüksek.**\
    **Lütfen 1 ile 10 arasında bir sayı girin**\
    **Tebrikler, sayıyı 4 ' te tahmin edersiniz.**

6. Windows Gezgini 'ni açın ve **Numberguessworkflowwhost\bin\debug** klasörüne (veya proje ayarlarınıza bağlı olarak **bin\release** ) gidin ve tamamlanan Iş akışına karşılık gelen Not defteri 'ni kullanarak izleme dosyasını açın. ' İ Not oluşturmadınız, `InstanceId` Windows Gezgini 'nde **değiştirilme tarihi** bilgilerini kullanarak doğru izleme dosyasını belirleyebilirsiniz. İzleme bilgilerinin son satırı, yeni eklenen etkinliğin çıktısını içerir `WriteLine` .

    **Lütfen 1 ile 10 arasında bir sayı girin**\
    **Tahmininiz çok düşük.**\
    **Lütfen 1 ile 10 arasında bir sayı girin**\
    **5 çok düşük.**\
    **Lütfen 1 ile 10 arasında bir sayı girin**\
    **7 çok yüksek.**\
    **Lütfen 1 ile 10 arasında bir sayı girin**\
    **6 doğru. Bunu 4 ' te tahmin edersiniz.**

### <a name="to-enable-starting-previous-versions-of-the-workflows"></a><a name="BKMK_StartPreviousVersions"></a> İş akışlarının önceki sürümlerini başlatmayı etkinleştirmek için

Güncelleştirmek için iş akışlarının dışında çalıştırırsanız, `NumberGuessWorkflowHost` iş akışlarının önceki sürümlerinin başlamasını sağlamak için uygulamayı değiştirebilirsiniz.

1. **Çözüm Gezgini**' de **Workflowwhostform** ' a çift tıklayın ve **WorkflowType** Birleşik giriş kutusunu seçin.

2. **Özellikler** **penceresinde, öğeler özelliğini seçin** ve **öğeler** koleksiyonunu düzenlemek için üç nokta düğmesine tıklayın.

3. Aşağıdaki üç öğeyi koleksiyona ekleyin.

    ```
    StateMachineNumberGuessWorkflow v1
    FlowchartNumberGuessWorkflow v1
    SequentialNumberGuessWorkflow v1
    ```

    Tamamlanan `Items` koleksiyonda altı öğe olacak.

    ```
    StateMachineNumberGuessWorkflow
    FlowchartNumberGuessWorkflow
    SequentialNumberGuessWorkflow
    StateMachineNumberGuessWorkflow v1
    FlowchartNumberGuessWorkflow v1
    SequentialNumberGuessWorkflow v1
    ```

4. **Çözüm Gezgini**' de **Workflowwhostform** ' a çift tıklayın ve **kodu görüntüle**' yi seçin.

5. `switch` `Select Case` `NewGame_Click` **WorkflowType** Birleşik giriş kutusundaki yeni öğeleri eşleşen iş akışı kimliklerine eşlemek için işleyicisindeki (veya) ifadeye üç yeni durum ekleyin.

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

    Aşağıdaki örnek, tüm `switch` (veya `Select Case` ) ifadesini içerir.

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

6. Uygulamayı derlemek ve çalıştırmak için CTRL + F5 tuşlarına basın. Artık `v1` iş akışının sürümlerini de ve geçerli sürümleri başlatabilirsiniz. Bu yeni örnekleri dinamik olarak güncelleştirmek için **Applydynamicupdate** uygulamasını çalıştırın.
