---
title: 'Nasıl yapılır: Bir çalışan iş akışı örneğinin tanımını güncelleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 26dfac36-ae23-4909-9867-62495b55fb5e
ms.openlocfilehash: d3ff9d217d085e3afe5171cce9d80f8dbc32ff36
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57722912"
---
# <a name="how-to-update-the-definition-of-a-running-workflow-instance"></a>Nasıl yapılır: Bir çalışan iş akışı örneğinin tanımını güncelleştirme

Dinamik güncelleştirme, uygulama geliştiricilerinin'bir kalıcı iş akışı örneği iş akışı tanımını güncelleştirmek için iş akışı için bir mekanizma sağlar. Gerekli değişiklik, bir hata düzeltmesi, yeni gereksinimleri uygulamak için veya beklenmeyen değişiklikleri uyum sağlamak için olabilir. Bu adım öğreticide kalıcı örnekleri değiştirmek için dinamik güncelleştirme kullanmayı gösteren `v1` sürümünde bulunan yeni işlevleri eşleştirmek için iş akışı tahmin numarası [nasıl yapılır: Bir iş akışı yan yana birden çok sürümünü konak](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).

> [!NOTE]
> Tamamlanmış bir sürümünü indirin veya videosu öğreticinin görüntülemek için bkz: [Windows Workflow Foundation (WF45) - başlangıç Öğreticisi](https://go.microsoft.com/fwlink/?LinkID=248976).

## <a name="in-this-topic"></a>Bu konuda

- [CreateUpdateMaps projeyi oluşturmak için](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_CreateProject)

- [StateMachineNumberGuessWorkflow güncelleştirmek için](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_StateMachine)

- [FlowchartNumberGuessWorkflow güncelleştirmek için](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_Flowchart)

- [SequentialNumberGuessWorkflow güncelleştirmek için](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_Sequential)

- [CreateUpdateMaps uygulaması derleme ve çalıştırma için](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_CreateUpdateMaps)

- [Güncelleştirilmiş iş akışı derlemesi oluşturmak için](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_BuildAssembly)

- [Yeni sürümlerle WorkflowVersionMap güncelleştirmek için](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_UpdateWorkflowVersionMap)

- [Dinamik güncelleştirmeleri uygulamak için](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_ApplyUpdate)

- [Güncelleştirilmiş iş akışlarıyla uygulamayı çalıştırmak için](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_BuildAndRun)

- [İş Akışları'nın önceki sürümlerini başlangıç etkinleştirmek için](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_StartPreviousVersions)

### <a name="BKMK_CreateProject"></a> CreateUpdateMaps projeyi oluşturmak için

1. Sağ **WF45GettingStartedTutorial** içinde **Çözüm Gezgini** ve **Ekle**, **yeni proje**.

2. İçinde **yüklü** düğümünü **Visual C#**, **Windows** (veya **Visual Basic**, **Windows**).

    > [!NOTE]
    > Hangi programlama diline bağlı olarak, Visual Studio'da birincil dili olarak yapılandırılmış **Visual C#** veya **Visual Basic** düğümü altında olabilir **diğer diller** düğümünde **yüklü** düğümü.

     Emin **.NET Framework 4.5** .NET Framework sürüm aşağı açılan listeden seçilen. Seçin **konsol uygulaması** gelen **Windows** listesi. Tür **CreateUpdateMaps** içine **adı** kutusuna ve tıklatın **Tamam**.

3. Sağ **CreateUpdateMaps** içinde **Çözüm Gezgini** ve **Başvuru Ekle**.

4. Seçin **Framework** gelen **derlemeleri** düğümünde **Başvuru Ekle** listesi. Tür **System.Activities** içine **arama derlemeleri** derlemeleri filtrelemek ve istenen başvurular seçmek daha kolay hale getirmek için kutusu.

5. Yanında onay **System.Activities** gelen **arama sonuçları** listesi.

6. Türü **serileştirme** içine **arama derlemeleri** kutusuna ve yanında onay **System.Runtime.Serialization** gelen **arama sonuçları**  listesi.

7. Türü **System.Xaml** içine **arama derlemeleri** kutusuna ve yanında onay **System.Xaml** gelen **arama sonuçları** listesi.

8. Tıklayın **Tamam** kapatmak için **başvuru Yöneticisi** ve başvuruları ekleyin.

9. Aşağıdaki `using` (veya `Imports`) deyimini dosyanın diğer üst `using` (veya `Imports`) ifadeleri.

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

10. Aşağıdaki iki dize üye ekleme `Program` sınıfı (veya `Module1`).

    ```vb
    Const mapPath = "..\..\..\PreviousVersions"
    Const definitionPath = "..\..\..\NumberGuessWorkflowActivities_du"
    ```

    ```csharp
    const string mapPath = @"..\..\..\PreviousVersions";
    const string definitionPath = @"..\..\..\NumberGuessWorkflowActivities_du";
    ```

11. Aşağıdaki `StartUpdate` yönteme `Program` sınıfı (veya `Module1`). Bu yöntem, belirtilen xaml iş akışı tanımında'kurmak yükler bir `ActivityBuilder`ve ardından çağırır `DynamicUpdate.PrepareForUpdate`. `PrepareForUpdate` İş akışı tanımı içinde bir kopyasını oluşturur `ActivityBuilder`. İş akışı tanımı değiştirildikten sonra bu kopya güncelleştirme eşlemesi oluşturmak için değiştirilmiş iş akışı tanımı ile birlikte kullanılır.

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

12. Ardından, aşağıdaki ekleyin `CreateUpdateMethod` için `Program` sınıfı (veya `Module1`). Bir dinamik güncelleştirme eşlemesi tarafından çağıran DynamicUpdateServices.CreateUpdateMap oluşturur ve sonra belirtilen adı kullanarak güncelleştirme eşlemesi kaydeder. Bu güncelleştirme eşlemesi iş akışı çalışma zamanı tarafından bulunan özgün iş akışı tanımı kullanılarak başlatıldı bir kalıcı iş akışı örneği güncelleştirmek için gereken bilgileri içeren `ActivityBuilder` böylece güncelleştirilmiş iş akışı tanımı kullanılarak tamamlanır.

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

13. Aşağıdaki `SaveUpdatedDefinition` yönteme `Program` sınıfı (veya `Module1`). Güncelleştirme eşlemesi oluşturulduktan sonra bu yöntem, güncelleştirilmiş iş akışı tanımı kaydeder.

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

### <a name="BKMK_StateMachine"></a> StateMachineNumberGuessWorkflow güncelleştirmek için

1. Ekleme bir `CreateStateMachineUpdateMap` için `Program` sınıfı (veya `Module1`).

    ```vb
    Private Sub CreateStateMachineUpdateMap()

    End Sub
    ```

    ```csharp
    private static void CreateStateMachineUpdateMap()
    {
    }
    ```

2. Çağrı yapmak `StartUpdate` ve ardından kök bir başvuru almak `StateMachine` iş akışı etkinlik.

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

3. Ardından, iki ifadelerin güncelleştirme `WriteLine` kullanıcının tahmin çok yüksek veya düşük olduğunu yapılan güncelleştirmeler eşleştikleri böylece görüntüleyen etkinlikleri [nasıl yapılır: Bir iş akışı yan yana birden çok sürümünü konak](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).

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

4. Ardından, yeni ekleme `WriteLine` kapanış iletisini gösteren bir etkinlik.

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

5. İş akışı güncelleştirildikten sonra çağrı `CreateUpdateMaps` ve `SaveUpdatedDefinition`. `CreateUpdateMaps` oluşturur ve kaydeder `DynamicUpdateMap`, ve `SaveUpdatedDefinition` güncelleştirilmiş iş akışı tanımı kaydeder.

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

    Aşağıdaki örnek, tamamlanan, `CreateStateMachineUpdateMap` yöntemi.

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

### <a name="BKMK_Flowchart"></a> FlowchartNumberGuessWorkflow güncelleştirmek için

1. Aşağıdaki `CreateFlowchartUpdateMethod` için `Program` sınıfı (veya `Module1`). Bu yöntem benzer `CreateStateMachineUpdateMap`. Bir çağrı ile başlar `StartUpdate`akış çizelgesi iş akışı tanım güncelleştirmeleri ve güncelleştirme harita ve güncelleştirilmiş iş akışı tanımı kaydederek tamamlanır.

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

### <a name="BKMK_Sequential"></a> SequentialNumberGuessWorkflow güncelleştirmek için

1. Aşağıdaki `CreateSequentialUpdateMethod` için `Program` sınıfı (veya `Module1`). Bu yöntem diğer iki yöntemler ile benzerdir. Bir çağrı ile başlar `StartUpdate`sıralı iş akışı tanım güncelleştirmeleri ve güncelleştirme harita ve güncelleştirilmiş iş akışı tanımı kaydederek tamamlanır.

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

### <a name="BKMK_CreateUpdateMaps"></a> CreateUpdateMaps uygulaması derleme ve çalıştırma için

1. Güncelleştirme `Main` yöntemi ve aşağıdaki üç yöntem çağrıları ekleyin. Bu yöntemleri aşağıdaki bölümlerde eklenir. Her bir yöntemin karşılık gelen numara tahmin iş akışı güncelleştirir ve oluşturur bir `DynamicUpdateMap` , güncelleştirmeleri açıklar.

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

2. Sağ **CreateUpdateMaps** içinde **Çözüm Gezgini** ve **başlangıç projesi olarak ayarla**.

3. Çözümü derlemek için CTRL + SHIFT + B ve çalıştırmak için CTRL + F5 tuşlarına basın `CreateUpdateMaps` uygulama.

    > [!NOTE]
    > `CreateUpdateMaps` Uygulama çalışırken, konum, ancak herhangi bir durum bilgi görüntülemez **NumberGuessWorkflowActivities_du** klasörü ve **PreviousVersions** klasörü göreceksiniz güncelleştirilmiş iş akışı tanım dosyalarını ve güncelleştirme eşlemeleri.

    Sonra güncelleştirme haritalar oluşturulur ve güncelleştirilmiş iş akışı tanımları, sonraki adımda güncelleştirilmiş tanımlarını içeren güncelleştirilmiş iş akışı derleme oluşturmaktır.

### <a name="BKMK_BuildAssembly"></a> Güncelleştirilmiş iş akışı derlemesi oluşturmak için

1. Visual Studio 2012 ikinci bir örneğini açın.

2. Seçin **açık**, **proje/çözüm** gelen **dosya** menüsü.

3. Gidin **NumberGuessWorkflowActivities_du** oluşturduğunuz klasör [nasıl yapılır: Ana bilgisayar, bir iş akışı yan yana birden çok sürümünü](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)seçin **NumberGuessWorkflowActivities.csproj** (veya **vbproj**), tıklatıp **açık**.

4. İçinde **Çözüm Gezgini**, sağ tıklayın **SequentialNumberGuessWorkflow.xaml** ve **projeden Çıkart**. Aynı şeyi yapmak **FlowchartNumberGuessWorkflow.xaml** ve **StateMachineNumberGuessWorkflow.xaml**. Bu adım, iş akışı tanımları önceki sürümlerini projeden kaldırır.

5. Seçin **varolan öğeyi Ekle** gelen **proje** menüsü.

6. Gidin **NumberGuessWorkflowActivities_du** oluşturduğunuz klasör [nasıl yapılır: Bir iş akışı yan yana birden çok sürümünü konak](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).

7. Seçin **XAML dosyaları (\*.xaml;\*. xoml)** gelen **dosya türü** aşağı açılan listesi.

8. Seçin **SequentialNumberGuessWorkflow_du.xaml**, **FlowchartNumberGuessWorkflow_du.xaml**, ve **StateMachineNumberGuessWorkflow_du.xaml** tıklayın **Ekleme**.

    > [!NOTE]
    > Aynı anda birden çok öğe seçmek için CTRL + tıklayın.

    Bu adım, iş akışı tanımlarının güncelleştirilmiş sürümleri projeye ekler.

9. Projeyi oluşturmak için CTRL+SHIFT+B tuşlarına basın.

10. Seçin **çözümü Kapat** gelen **dosya** menüsü. Bir çözüm dosyası için proje gerekli değildir. Bu nedenle tıklayın **Hayır** Visual Studio çözüm dosyası kaydetmeden kapatın. Seçin **çıkış** gelen **dosya** menüsünde Visual Studio'yu kapatın.

11. Windows Gezgini'ni açın ve gidin **NumberGuessWorkflowActivities_du\bin\Debug** klasörü (veya **bin\Release** proje ayarlarınıza bağlı olarak).

12. Yeniden adlandırma **NumberGuessWorkflowActivities.dll** için **NumberGuessWorkflowActivities_v15.dll**ve kopyalayıp **PreviousVersions** içindeoluşturduğunuzklasör[Nasıl yapılır: Bir iş akışı yan yana birden çok sürümünü konak](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).

### <a name="BKMK_UpdateWorkflowVersionMap"></a> Yeni sürümlerle WorkflowVersionMap güncelleştirmek için

1. Visual Studio 2012'in ilk örneğine geçin.

2. Çift **WorkflowVersionMap.cs** (veya **WorkflowVersionMap.vb**) altında **NumberGuessWorkflowHost** açmak için proje.

3. Altı mevcut iş akışı kimlik bildirimlerine hemen altına üç yeni iş akışı kimliklerini ekleyin. Bu öğreticide `1.5.0.0` olarak kullanılan `WorkflowIdentity.Version` dinamik güncelleştirme kimlikleri için. Bu yeni `v15` kimlikleri kullanılabilir iş akışı dinamik olarak güncelleştirilen kalıcı iş akışı örnekleri için doğru iş akışı tanımı belirtin.

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

4. Oluşturucu sonuna aşağıdaki kodu ekleyin. Bu kod, dinamik güncelleştirme iş akışı kimlikleri başlatır, ilgili iş akışı tanımları yükler ve bunları iş akışı sürümü sözlüğe ekler.

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

     Aşağıdaki örnek, tamamlanan, `WorkflowVersionMap` sınıfı.

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

### <a name="BKMK_ApplyUpdate"></a> Dinamik güncelleştirmeleri uygulamak için

1. Sağ **WF45GettingStartedTutorial** içinde **Çözüm Gezgini** ve **Ekle**, **yeni proje**.

2. İçinde **yüklü** düğümünü **Visual C#**, **Windows** (veya **Visual Basic**, **Windows**).

    > [!NOTE]
    > Hangi programlama diline bağlı olarak, Visual Studio'da birincil dili olarak yapılandırılmış **Visual C#** veya **Visual Basic** düğümü altında olabilir **diğer diller** düğümünde **yüklü** düğümü.

    Emin **.NET Framework 4.5** .NET Framework sürüm aşağı açılan listeden seçilen. Seçin **konsol uygulaması** gelen **Windows** listesi. Tür **ApplyDynamicUpdate** içine **adı** kutusuna ve tıklatın **Tamam**.

3. Sağ **ApplyDynamicUpdate** içinde **Çözüm Gezgini** ve **Başvuru Ekle**.

4. Tıklayın **çözüm** ve yanındaki kutuyu işaretleyin **NumberGuessWorkflowHost**. Bu başvuru gerektiği şekilde `ApplyDynamicUpdate` kullanabilirsiniz `NumberGuessWorkflowHost.WorkflowVersionMap` sınıfı.

5. Seçin **Framework** gelen **derlemeleri** düğümünde **Başvuru Ekle** listesi. Tür **System.Activities** içine **arama derlemeleri** kutusu. Bu derlemeleri filtreleyin ve istenen başvurular seçmeyi kolaylaştırmak.

6. Yanında onay **System.Activities** gelen **arama sonuçları** listesi.

7. Türü **serileştirme** içine **arama derlemeleri** kutusuna ve yanında onay **System.Runtime.Serialization** gelen **arama sonuçları**  listesi.

8. Tür **DurableInstancing** içine **arama derlemeleri** kutusuna ve yanında onay **System.Activities.durableınstancing** ve  **System.Runtime.DurableInstancing** gelen **arama sonuçları** listesi.

9. Tıklayın **Tamam** kapatmak için **başvuru Yöneticisi** ve başvuruları ekleyin.

10. Sağ **ApplyDynamicUpdate** Çözüm Gezgini'nde seçin **Ekle**, **sınıfı**. Tür `DynamicUpdateInfo` içine **adı** kutusuna ve tıklatın **Ekle**.

11. Aşağıdaki iki üye ekleme `DynamicUpdateInfo` sınıfı. Aşağıdaki örnek, tamamlanan, `DynamicUpdateInfo` sınıfı. Bu sınıf, bir iş akışı örneği güncelleştirildiğinde kullanılan yeni bir iş akışı kimliği ve güncelleştirme eşlemesi hakkında bilgi içerir.

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

12. Aşağıdaki `using` (veya `Imports`) deyimini dosyanın diğer üst `using` (veya `Imports`) ifadeleri.

    ```vb
    Imports System.Activities
    Imports System.Activities.DynamicUpdate
    ```

    ```csharp
    using System.Activities;
    using System.Activities.DynamicUpdate;
    ```

13. Çift **Program.cs** (veya **Module1.vb**) Çözüm Gezgini'nde.

14. Aşağıdaki `using` (veya `Imports`) deyimini dosyanın diğer üst `using` (veya `Imports`) ifadeleri.

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

15. Aşağıdaki bağlantı dizesi üye eklemek `Program` sınıfı (veya `Module1`).

    ```vb
    Const connectionString = "Server=.\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI"
    ```

    ```csharp
    const string connectionString = "Server=.\\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI";
    ```

    > [!NOTE]
    > Bağlantı dizesi sunucu adı SQL Server sürümüne bağlı olarak farklı olabilir.

16. Aşağıdaki `GetIDs` yönteme `Program` sınıfı (veya `Module1`). Bu yöntem, kalıcı iş akışı örnek kimlikleri listesini döndürür.

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

17. Aşağıdaki `LoadMap` yönteme `Program` sınıfı (veya `Module1`). Bu yöntem eşleyen sözlük oluşturur `v1` iş akışı kimlikleri güncelleştirme haritalara ve karşılık gelen güncelleştirmek için kullanılan yeni bir iş akışı kimlikleri iş akışı örneği kalıcı.

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

18. Aşağıdaki `LoadMaps` yönteme `Program` sınıfı (veya `Module1`). Bu yöntem, üç güncelleştirme haritalar yükler ve eşleyen sözlük oluşturur `v1` iş akışı kimlikleri güncelleştirme eşlemeleri.

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

19. Aşağıdaki kodu ekleyin `Main`. Bu kod kalıcı iş akışı örnekleri ve her inceler yinelenir `WorkflowIdentity`. Varsa `WorkflowIdentity` eşleyen bir `v1` iş akışı örneği bir `WorkflowApplication` güncelleştirilmiş iş akışı tanımı ve güncelleştirilmiş iş akışı kimliği ile yapılandırılır. Ardından, `WorkflowApplication.Load` örneği ve dinamik güncelleştirme eşlemesi geçerli güncelleştirme eşlemesi ile adlandırılır. Güncelleştirme uygulandıktan sonra güncelleştirilmiş örneği çağrısıyla kalıcıdır `Unload`.

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

20. Sağ **ApplyDynamicUpdate** içinde **Çözüm Gezgini** ve **başlangıç projesi olarak ayarla**.

21. Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın ve çalıştırmak için CTRL + F5 tuşuna basarak `ApplyDynamicUpdate` uygulama ve kalıcı iş akışı örnekleri güncelleştirin. Aşağıdakine benzer bir çıktı görmeniz gerekir. Güncelleştirilmiş sürüm 2.0.0.0 iş akışlarının sırada sürüm 1.0.0.0 iş akışları 1.5.0.0, sürümüne güncelleştirilir.

    **İnceleme: StateMachineNumberGuessWorkflow; Sürüm 1.0.0.0 =**\
    **İçin güncelleştirilmiştir: StateMachineNumberGuessWorkflow; Sürüm 1.5.0.0 =**\
    **İnceleme: StateMachineNumberGuessWorkflow; Sürüm 1.0.0.0 =**\
    **İçin güncelleştirilmiştir: StateMachineNumberGuessWorkflow; Sürüm 1.5.0.0 =**\
    **İnceleme: FlowchartNumberGuessWorkflow; Version=1.0.0.0**\
    **İçin güncelleştirilmiştir: FlowchartNumberGuessWorkflow; Version=1.5.0.0**\
    **İnceleme: FlowchartNumberGuessWorkflow; Version=1.0.0.0**\
    **İçin güncelleştirilmiştir: FlowchartNumberGuessWorkflow; Version=1.5.0.0**\
    **İnceleme: SequentialNumberGuessWorkflow; Sürüm 1.0.0.0 =**\
    **İçin güncelleştirilmiştir: SequentialNumberGuessWorkflow; Sürüm 1.5.0.0 =**\
    **İnceleme: SequentialNumberGuessWorkflow; Sürüm 1.0.0.0 =**\
    **İçin güncelleştirilmiştir: SequentialNumberGuessWorkflow; Sürüm 1.5.0.0 =**\
    **İnceleme: SequentialNumberGuessWorkflow; Sürüm 1.0.0.0 =**\
    **İçin güncelleştirilmiştir: SequentialNumberGuessWorkflow; Sürüm 1.5.0.0 =**\
    **İnceleme: StateMachineNumberGuessWorkflow; Sürüm 1.0.0.0 =**\
    **İçin güncelleştirilmiştir: StateMachineNumberGuessWorkflow; Sürüm 1.5.0.0 =**\
    **İnceleme: FlowchartNumberGuessWorkflow; Version=1.0.0.0**\
    **İçin güncelleştirilmiştir: FlowchartNumberGuessWorkflow; Version=1.5.0.0**\
    **İnceleme: StateMachineNumberGuessWorkflow; Version=2.0.0.0**\
    **İnceleme: StateMachineNumberGuessWorkflow; Version=2.0.0.0**\
    **İnceleme: FlowchartNumberGuessWorkflow; Version=2.0.0.0**\
    **İnceleme: FlowchartNumberGuessWorkflow; Version=2.0.0.0**\
    **İnceleme: SequentialNumberGuessWorkflow; Sürüm 2.0.0.0 =**\
    **İnceleme: SequentialNumberGuessWorkflow; Sürüm 2.0.0.0 =**\
    **Devam etmek için herhangi bir tuşa basın...**

### <a name="BKMK_BuildAndRun"></a> Güncelleştirilmiş iş akışlarıyla uygulamayı çalıştırmak için

1. Sağ **NumberGuessWorkflowHost** içinde **Çözüm Gezgini** ve **başlangıç projesi olarak ayarla**.

2. Uygulamayı çalıştırmak için CTRL + F5 tuşlarına basın.

3. Tıklayın **yeni oyun** yeni iş akışını başlatmak ve iş akışını gösteren durum pencere sürümü aşağıdaki bilgileri not için bir `v2` iş akışı.

4. Birini `v1` başında başlattığınız iş akışları [nasıl yapılır: Ana bilgisayar, bir iş akışı yan yana birden çok sürümünü](how-to-host-multiple-versions-of-a-workflow-side-by-side.md) konu. Sürüm bilgileri durum penceresi altında iş akışı bir sürüm olduğunu gösteren Not **1.5.0.0** iş akışı. Bunlar çok yüksek veya düşük dışında hiçbir bilgi hakkında önceki tahmin belirtilen olduğunu unutmayın.

    **Lütfen 1 ile 10 arasında bir sayı girin**\
    **Çok düşük tahmininizdir.**

5. Not `InstanceId` ve iş akışı tamamlanana kadar tahmin girin. Durum penceresi tahmin içeriği hakkında bilgi gösterir çünkü `WriteLine` etkinlikleri, dinamik güncelleştirme ile güncelleştirildi.

    **Lütfen 1 ile 10 arasında bir sayı girin**\
    **Çok düşük tahmininizdir.**\
    **Lütfen 1 ile 10 arasında bir sayı girin**\
    **5 çok düşüktür.**\
    **Lütfen 1 ile 10 arasında bir sayı girin**\
    **7 çok yüksektir.**\
    **Lütfen 1 ile 10 arasında bir sayı girin**\
    **Tebrikler, sayı 4 kapatır tahmin.**

6. Windows Gezgini'ni açın ve gidin **NumberGuessWorkflowHost\bin\debug** klasörü (veya **bin\release** proje ayarlarınıza bağlı olarak) karşılık gelen Not Defteri'ni kullanarak izleme dosyasını açın Tamamlanan iş akışı için. Not yapmadıysanız `InstanceId` doğru izleme dosyası kullanarak tanımlamak çözebileceğiniz **değiştirilme tarihi** Windows Explorer'da bilgileri. İzleme bilgilerini son satırının yeni eklenen çıktısını içeren `WriteLine` etkinlik.

    **Lütfen 1 ile 10 arasında bir sayı girin**\
    **Çok düşük tahmininizdir.**\
    **Lütfen 1 ile 10 arasında bir sayı girin**\
    **5 çok düşüktür.**\
    **Lütfen 1 ile 10 arasında bir sayı girin**\
    **7 çok yüksektir.**\
    **Lütfen 1 ile 10 arasında bir sayı girin**\
    **6 doğrudur. Bu 4 kapatır tahmin.**

### <a name="BKMK_StartPreviousVersions"></a> İş Akışları'nın önceki sürümlerini başlangıç etkinleştirmek için

Güncelleştirilecek iş akışları dışında çalıştırırsanız, değiştirebileceğiniz `NumberGuessWorkflowHost` iş akışları'nın önceki sürümlerini başlangıç etkinleştirmek için uygulama.

1. Çift **WorkflowHostForm** içinde **Çözüm Gezgini**seçip **WorkflowType** birleşik giriş kutusu.

2. İçinde **özellikleri** penceresinde **öğeleri** özelliği ve düzenlemek için üç nokta düğmesini tıklatın **öğeleri** koleksiyonu.

3. Aşağıdaki üç öğe koleksiyonuna ekleyin.

    ```
    StateMachineNumberGuessWorkflow v1
    FlowchartNumberGuessWorkflow v1
    SequentialNumberGuessWorkflow v1
    ```

    Tamamlanan `Items` altı öğe koleksiyonu olacaktır.

    ```
    StateMachineNumberGuessWorkflow
    FlowchartNumberGuessWorkflow
    SequentialNumberGuessWorkflow
    StateMachineNumberGuessWorkflow v1
    FlowchartNumberGuessWorkflow v1
    SequentialNumberGuessWorkflow v1
    ```

4. Çift **WorkflowHostForm** içinde **Çözüm Gezgini**seçip **kodu görüntüle**.

5. Üç yeni durumuna eklemek `switch` (veya `Select Case`) deyiminde `NewGame_Click` yeni öğeleri eşlemek için işleyici **WorkflowType** eşleşen iş akışı kimlikleri için birleşik giriş kutusu.

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

    Aşağıdaki örnek, tam içerir `switch` (veya `Select Case`) deyimi.

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

6. Derleme ve uygulamayı çalıştırmak için CTRL + F5 tuşlarına basın. Şimdi başlayabilirsiniz `v1` geçerli sürümler yanı sıra iş akışı sürümleri. Bu yeni örnekler dinamik olarak güncelleştirmek için çalıştırın **ApplyDynamicUpdate** uygulama.
