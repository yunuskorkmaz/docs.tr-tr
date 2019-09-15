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
# <a name="how-to-host-multiple-versions-of-a-workflow-side-by-side"></a>Nasıl yapılır: İş Akışının Birden Fazla Sürümünü Yan Yana Barındırma

`WorkflowIdentity`, iş akışı uygulama geliştiricilerinin bir adı ve sürümü bir iş akışı tanımıyla ilişkilendirmesi ve bu bilgilerin kalıcı bir iş akışı örneğiyle ilişkilendirilmesi için bir yol sağlar. Bu kimlik bilgileri, bir iş akışı tanımının birden çok sürümünün yan yana yürütülmesi gibi senaryoları etkinleştirmek için iş akışı uygulama geliştiricileri tarafından kullanılabilir ve dinamik güncelleştirme gibi diğer işlevler için de temel pulu sağlar. Öğreticideki Bu adım, bir iş akışının birden `WorkflowIdentity` çok sürümünü aynı anda barındırmak için nasıl kullanılacağını gösterir.

> [!NOTE]
> Tamamlanmış bir sürümü indirmek veya öğreticiye ilişkin bir video kılavuzunu görüntülemek için, bkz. [Windows Workflow Foundation (WF45)-Başlangıç Öğreticisi](https://go.microsoft.com/fwlink/?LinkID=248976).

## <a name="in-this-topic"></a>Bu konuda

Öğreticinin bu adımında, `WriteLine` iş akışındaki etkinlikler ek bilgi sağlamak için değiştirilir ve yeni `WriteLine` bir etkinlik eklenir. Özgün iş akışı derlemesinin bir kopyası depolanır ve ana bilgisayar uygulaması güncelleştirilir ve böylece hem orijinal hem de güncelleştirilmiş iş akışlarını aynı anda çalıştırabilirsiniz.

- [NumberGuessWorkflowActivities projesinin bir kopyasını oluşturmak için](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_BackupCopy)

- [İş akışlarını güncelleştirmek için](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateWorkflows)

  - [StateMachine iş akışını güncelleştirmek için](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateStateMachine)

  - [Akış çizelgesi iş akışını güncelleştirmek için](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateFlowchart)

  - [Sıralı iş akışını güncelleştirmek için](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateSequential)

- [WorkflowVersionMap 'i önceki iş akışı sürümlerini içerecek şekilde güncelleştirmek için](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateWorkflowVersionMap)

- [Uygulamayı derlemek ve çalıştırmak için](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_BuildAndRun)

> [!NOTE]
> Bu konudaki adımları takip etmeden önce, uygulamayı çalıştırın, her türden birkaç iş akışını başlatın ve her biri için bir veya iki tahmin yaparak. Bu kalıcı iş akışları bu adımda ve aşağıdaki adımda [kullanılır: Çalışan bir Iş akışı örneğinin](how-to-update-the-definition-of-a-running-workflow-instance.md)tanımını güncelleştirin.

> [!NOTE]
> Başlangıç öğreticisindeki her adım önceki adımlara bağlıdır. Önceki adımları tamamlamadıysanız, [Windows Workflow Foundation (WF45)-başlangıç öğreticisindeki](https://go.microsoft.com/fwlink/?LinkID=248976)öğreticinin tamamlanmış bir sürümünü indirebilirsiniz.

### <a name="BKMK_BackupCopy"></a>NumberGuessWorkflowActivities projesinin bir kopyasını oluşturmak için

1. Açık değilse, Visual Studio 2012 'de **WF45GettingStartedTutorial** çözümünü açın.

2. Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.

3. **WF45GettingStartedTutorial** çözümünü kapatın.

4. Windows Gezgini 'ni açın ve öğretici çözüm dosyasının ve proje klasörlerinin bulunduğu klasöre gidin.

5. **Numberguessworkflowwhost** ve **NumberGuessWorkflowActivities**aynı klasörde **PreviousVersions** adlı yeni bir klasör oluşturun. Bu klasör, sonraki öğretici adımlarda kullanılan iş akışlarının farklı sürümlerini içeren derlemeleri içermesi için kullanılır.

6. **NumberGuessWorkflowActivities\bin\debug** klasörüne gidin (veya proje ayarlarınıza bağlı olarak **bin\release** ). **NumberGuessWorkflowActivities. dll dosyasını** kopyalayın ve **PreviousVersions** klasörüne yapıştırın.

7. **PreviousVersions** klasöründeki **NumberGuessWorkflowActivities. dll dosyasını** **NumberGuessWorkflowActivities_v1. dll**olarak yeniden adlandırın.

    > [!NOTE]
    > Bu konudaki adımlarda, iş akışlarının birden çok sürümünü içerecek şekilde kullanılan derlemeleri yönetmenin bir yolu gösterilmektedir. Derlemeleri tanımlayıcı adlandırma ve genel derleme önbelleğinde kaydetme gibi diğer yöntemler de kullanılabilir.

8. **Numberguessworkflowwhost**, **NumberGuessWorkflowActivities**ve yeni eklenen **PreviousVersions** klasörüyle aynı klasörde **NumberGuessWorkflowActivities_du** adlı yeni bir klasör oluşturun ve tüm dosyaları kopyalayın ve **NumberGuessWorkflowActivities** klasöründen yeni **NumberGuessWorkflowActivities_du** klasörüne alt klasörler. Etkinliğin ilk sürümü için projenin bu yedek kopyası şu şekilde kullanılır [: Çalışan bir Iş akışı örneğinin](how-to-update-the-definition-of-a-running-workflow-instance.md)tanımını güncelleştirin.

9. Visual Studio 2012 ' de **WF45GettingStartedTutorial** çözümünü yeniden açın.

### <a name="BKMK_UpdateWorkflows"></a>İş akışlarını güncelleştirmek için

Bu bölümde, iş akışı tanımları güncelleştirilir. Kullanıcının tahminlerine geri bildirimde bulunan iki `WriteLine` etkinlik güncelleştirilir ve sayı tahmin edildikten sonra oyun hakkında ek bilgiler sağlayan yeni `WriteLine` bir etkinlik eklenir.

#### <a name="BKMK_UpdateStateMachine"></a>StateMachine iş akışını güncelleştirmek için

1. **Çözüm Gezgini**, **NumberGuessWorkflowActivities** projesi altında **StateMachineNumberGuessWorkflow. xaml**' ye çift tıklayın.

2. Durum makinesinde **tahmin yanlış** geçişi ' ne çift tıklayın.

3. Etkinliğin en `WriteLine`solundakigüncelleştirmeyigüncelleştirin. `Text` `If`

    ```vb
    Guess & " is too low."
    ```

    ```csharp
    Guess + " is too low."
    ```

4. Etkinliğin en `WriteLine` sağdaki bölümünü güncelleştirin. `Text` `If`

    ```vb
    Guess & " is too high."
    ```

    ```csharp
    Guess + " is too high."
    ```

5. İş akışı Tasarımcısı ' nın en üstünde bulunan içerik haritası ' nda **StateMachine** ' e tıklayarak iş akışı tasarımcısında genel durum makinesi görünümüne geri dönün.

6. Durum makinesinde **tahmin doğru** geçişi ' ne çift tıklayın.

7. **Araç kutusu** ' nu **temel elemanlar** bölümünden bir **WriteLine** etkinliği sürükleyin ve **bırakma eylemi etkinliğine buraya** bırakın.

8. `Text` Özellik kutusuna aşağıdaki ifadeyi yazın.

    ```vb
    Guess & " is correct. You guessed it in " & Turns & " turns."
    ```

    ```csharp
    Guess + " is correct. You guessed it in " + Turns + " turns."
    ```

#### <a name="BKMK_UpdateFlowchart"></a>Akış çizelgesi iş akışını güncelleştirmek için

1. **Çözüm Gezgini**, **NumberGuessWorkflowActivities** projesi altında **FlowchartNumberGuessWorkflow. xaml**' e çift tıklayın.

2. `Text` En`WriteLine` soldaki etkinliğin güncelleştirmesini güncelleştirin.

    ```vb
    Guess & " is too low."
    ```

    ```csharp
    Guess + " is too low."
    ```

3. `Text` En`WriteLine` sağdaki etkinliğin güncelleştirmesini güncelleştirin.

    ```vb
    Guess & " is too high."
    ```

    ```csharp
    Guess + " is too high."
    ```

4. **Araç kutusu** ' nun `True` **temel öğeler** bölümünden bir **WriteLine** etkinliğini sürükleyin ve en üstteki `FlowDecision`eylemin bırakma noktasına bırakın. Etkinlik, akış çizelgesine eklenir ve `True` eylemine `FlowDecision`bağlanır. `WriteLine`

5. `Text` Özellik kutusuna aşağıdaki ifadeyi yazın.

    ```vb
    Guess & " is correct. You guessed it in " & Turns & " turns."
    ```

    ```csharp
    Guess + " is correct. You guessed it in " + Turns + " turns."
    ```

#### <a name="BKMK_UpdateSequential"></a>Sıralı iş akışını güncelleştirmek için

1. **Çözüm Gezgini**, **NumberGuessWorkflowActivities** projesi altında **SequentialNumberGuessWorkflow. xaml**' ye çift tıklayın.

2. Etkinliğin en `WriteLine`solundakigüncelleştirmeyigüncelleştirin. `Text` `If`

    ```vb
    Guess & " is too low."
    ```

    ```csharp
    Guess + " is too low."
    ```

3. Etkinliğin en `WriteLine`sağdakietkinliğinigüncelleştirin. `Text` `If`

    ```vb
    Guess & " is too high."
    ```

    ```csharp
    Guess + " is too high."
    ```

4. **Araç kutusunun** **temel elemanlar** bölümünden bir **WriteLine** etkinliğini sürükleyin ve **DoWhile** etkinliğinden sonra, **WriteLine** 'ın kök `Sequence` etkinliğinde son etkinlik olması için onu bırakın.

5. `Text` Özellik kutusuna aşağıdaki ifadeyi yazın.

    ```vb
    Guess & " is correct. You guessed it in " & Turns & " turns."
    ```

    ```csharp
    Guess + " is correct. You guessed it in " + Turns + " turns."
    ```

### <a name="BKMK_UpdateWorkflowVersionMap"></a>WorkflowVersionMap 'i önceki iş akışı sürümlerini içerecek şekilde güncelleştirmek için

1. # **Guessworkflowwhost** projesi altındaki **WorkflowVersionMap.cs** (veya **WorkflowVersionMap. vb**) öğesine çift tıklayarak açın.

2. Aşağıdaki `using` (veya `Imports`) deyimlerini, diğer `using` (veya `Imports`) deyimleriyle dosyanın en üstüne ekleyin.

    ```vb
    Imports System.Reflection
    Imports System.IO
    ```

    ```csharp
    using System.Reflection;
    using System.IO;
    ```

3. Mevcut üç iş akışı kimlik bildiriminin hemen altına üç yeni iş akışı kimliği ekleyin. Bu yeni `v1` iş akışı kimlikleri, güncelleştirmeler yapılmadan önce başlatılan iş akışlarına doğru iş akışı tanımını sağlamak üzere kullanılacaktır.

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

4. Oluşturucuda, üç geçerli iş akışı `Version` kimliği özelliğini ' e `2.0.0.0`güncelleştirin. `WorkflowVersionMap`

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

    İçindeki iş akışlarının geçerli sürümlerini sözlüğe ekleyen kod, projede başvurulan geçerli sürümleri kullanır, bu nedenle iş akışı tanımlarını Başlatan kodun güncelleştirilmesine gerek kalmaz.

5. Aşağıdaki kodu, geçerli sürümleri sözlüğe ekleyen koddan hemen sonra oluşturucuya ekleyin.

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

    Bu iş akışı kimlikleri, karşılık gelen iş akışı tanımlarının başlangıç sürümleriyle ilişkilendirilir.

6. Sonra, iş akışı tanımlarının ilk sürümünü içeren derlemeyi yükleyin ve ilgili iş akışı tanımlarını oluşturun ve sözlüğe ekleyin.

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

    Aşağıdaki örnek, güncelleştirilmiş `WorkflowVersionMap` sınıfın tüm listesidir.

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

### <a name="BKMK_BuildAndRun"></a>Uygulamayı derlemek ve çalıştırmak için

1. Uygulamayı derlemek için CTRL + SHIFT + B tuşlarına basın ve ardından başlatmak için CTRL + F5 tuşlarına basın.

2. Yeni **oyun**' i tıklatarak yeni bir iş akışı başlatın. İş akışının sürümü durum penceresi altında görüntülenir ve güncelleştirilmiş sürümü ilişkili `WorkflowIdentity`dosyadan yansıtır. İşlem tamamlandığında iş akışı için `InstanceId` izleme dosyasını görüntüleyebilmeniz ve ardından oyun tamamlanana kadar tahmin edilecek şekilde girmeniz için, ' yi bir yere göz önünde bulabilirsiniz. Kullanıcı tahminin, `WriteLine` etkinliklerdeki güncelleştirmelere bağlı olarak durum penceresinde görünen bilgilere nasıl görüntülendiğini aklınızda yapın.

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
    > `WriteLine` Etkinliklerdeki güncelleştirilmiş metin görüntülenir, ancak bu konuya eklenen son `WriteLine` etkinliğin çıktısı değildir. Yani durum penceresi `PersistableIdle` işleyici tarafından güncelleştirilir. İş akışı tamamlandığından ve son etkinlikten sonra boşta çalışmadığından, `PersistableIdle` işleyici çağrılmaz. Ancak, benzer bir ileti `Completed` işleyicinin durum penceresinde görüntülenir. İsterseniz, metni `StringWriter` öğesinden ayıklamak ve durum penceresine göstermek `Completed` için, kod işleyiciye eklenebilir.

3. Windows Gezgini 'ni açın ve **Numberguessworkflowwhost\bin\debug** klasörüne (veya proje ayarlarınıza bağlı olarak **bin\release** ) gidin ve tamamlanan Iş akışına karşılık gelen Not defteri 'ni kullanarak izleme dosyasını açın. `InstanceId`' İ Not yapmadıysanız, Windows Gezgini 'nde **değiştirme tarihi** bilgilerini kullanarak doğru izleme dosyasını tanımlayabilirsiniz.

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

    Güncelleştirilmiş `WriteLine` çıktı, bu konuya eklenen `WriteLine` öğesinin çıktısı da dahil olmak üzere izleme dosyası içinde yer alır.

4. Tahmin sayısı uygulamasına geri dönün ve güncelleştirmeler yapılmadan önce başlatılan iş akışlarından birini seçin. Durum penceresinin altında görüntülenen sürüm bilgilerine bakarak şu anda seçili olan iş akışının sürümünü tanımlayabilirsiniz. Bazı tahminler girin ve durum güncelleştirmelerinin önceki sürümden gelen `WriteLine` etkinlik çıkışıyla eşleştiğini ve kullanıcının tahminlerini dahil edileceğini unutmayın. Bunun nedeni, bu iş akışlarının `WriteLine` güncelleştirmeleri olmayan önceki iş akışı tanımını kullanıyor olması.

    Sonraki adımda, [nasıl yapılır: Çalışan bir iş akışı örneğinin](how-to-update-the-definition-of-a-running-workflow-instance.md)tanımını güncelleştirme, çalışan `v1` iş akışı örnekleri, `v2` örnekler olarak yeni işlevleri içerecek şekilde güncelleştirilir.
