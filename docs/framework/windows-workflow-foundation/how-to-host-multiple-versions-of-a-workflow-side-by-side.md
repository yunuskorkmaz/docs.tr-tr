---
title: 'Nasıl yapılır: birden çok sürümünü bir iş akışı yan yana barındırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 09c575df-e0a3-4f3b-9e01-a7ac59d65287
ms.openlocfilehash: 04586f22076b6e2cf4175c7d9d985820ef7885c6
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50181626"
---
# <a name="how-to-host-multiple-versions-of-a-workflow-side-by-side"></a>Nasıl yapılır: birden çok sürümünü bir iş akışı yan yana barındırma
`WorkflowIdentity` Bu bilgiler bir kalıcı iş akışı örneğiyle ilişkili olmasını yanı sıra, bir adı ve sürümü, bir iş akışı tanımıyla ilişkilendirilecek iş akışı uygulama geliştiricileri için bir yol sağlar. Bu kimlik bilgileri birden çok iş akışı tanımı sürümünün yan yana yürütme gibi senaryoları etkinleştirmek için iş akışı uygulama geliştiricileri tarafından kullanılabilir ve dinamik güncelleştirme gibi diğer işlevleri için temel sağlar. Bu adım öğreticide nasıl kullanılacağını gösteren `WorkflowIdentity` aynı anda birden çok iş akışı sürümünü barındırmak için.

> [!NOTE]
>  Tamamlanmış bir sürümünü indirin veya videosu öğreticinin görüntülemek için bkz: [Windows Workflow Foundation (WF45) - başlangıç Öğreticisi](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
## <a name="in-this-topic"></a>Bu konuda  
 Öğreticinin bu adımında `WriteLine` ek bilgiler ve yeni bir iş akışındaki etkinlikler değiştirildiğinde `WriteLine` etkinlik eklenir. Özgün iş akışı derleme kopyası depolanır ve aynı anda hem özgün hem de güncelleştirilmiş iş akışı çalışması için ana bilgisayar uygulaması güncelleştirilir.  
  
-   [NumberGuessWorkflowActivities projenin bir kopyasını oluşturmak için](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_BackupCopy)  
  
-   [İş akışları güncelleştirmek için](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateWorkflows)  
  
    -   [Durum makinesi iş akışını güncelleştirme](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateStateMachine)  
  
    -   [Akış Çizelgesi iş akışını güncelleştirme](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateFlowchart)  
  
    -   [Sıralı iş akışını güncelleştirme](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateSequential)  
  
-   [Önceki iş akışı sürümünün içerecek şekilde WorkflowVersionMap güncelleştirmek için](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateWorkflowVersionMap)  
  
-   [Derleme ve uygulamayı çalıştırmak için](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_BuildAndRun)  
  
> [!NOTE]
>  Bu konu başlığındaki adımları uygulayarak önce uygulamayı çalıştırmak, her türden çeşitli iş akışlarını başlatmak ve her biri için bir veya iki tahmin yapma. Bu adım ve aşağıdaki adımı kalıcı bu iş akışları kullanılan [nasıl yapılır: çalışan iş akışı örneğinin tanımını güncelleştirme](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md).

> [!NOTE]
>  Başlarken Öğreticisi her adımda, önceki adımları bağlıdır. Önceki adımları tamamlanmadıysa öğreticinin tamamlanmış bir sürümünü indirebilirsiniz [Windows Workflow Foundation (WF45) - başlangıç Öğreticisi](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
###  <a name="BKMK_BackupCopy"></a> NumberGuessWorkflowActivities projenin bir kopyasını oluşturmak için  
  
1.  Açık **WF45GettingStartedTutorial** çözüm açık değilse Visual Studio 2012.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
3.  Kapat **WF45GettingStartedTutorial** çözüm.  
  
4.  Windows Gezgini'ni açın ve öğretici çözüm dosyası ve proje klasörleri bulunduğu klasöre gidin.  
  
5.  Adlı yeni bir klasör oluşturun **PreviousVersions** aynı klasörde **NumberGuessWorkflowHost** ve **NumberGuessWorkflowActivities**. Bu klasör, sonraki öğretici adımlarda kullanılan iş akışları farklı sürümlerini içeren derlemeler kapsamak için kullanılır.  
  
6.  Gidin **NumberGuessWorkflowActivities\bin\debug** klasörü (veya **bin\release** proje ayarlarınıza bağlı olarak). Kopyalama **NumberGuessWorkflowActivities.dll** yapıştırın **PreviousVersions** klasör.  
  
7.  Yeniden adlandırma **NumberGuessWorkflowActivities.dll** içinde **PreviousVersions** klasörüne **NumberGuessWorkflowActivities_v1.dll**.  
  
    > [!NOTE]
    >  Bu konu başlığındaki adımları iş akışları birden çok sürümünü kapsamak için kullanılmış olan derlemeleri yönetmek için bir yol gösterir. Güçlü derlemelerini adlandırma ve bunları genel derleme önbelleğinde kaydetme gibi diğer yöntemleri de kullanılabilir.

8.  Adlı yeni bir klasör oluşturun **NumberGuessWorkflowActivities_du** aynı klasörde **NumberGuessWorkflowHost**, **NumberGuessWorkflowActivities**ve yeni eklenen **PreviousVersions** klasörünü ve tüm dosyaları ve alt klasörlerdeki kopyalayın **NumberGuessWorkflowActivities** yeni klasöre  **NumberGuessWorkflowActivities_du** klasör. Bu yedekleme kopyası proje etkinliklerinin ilk sürümü için kullanılan [nasıl yapılır: çalışan iş akışı örneğinin tanımını güncelleştirme](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md).

9. Yeniden açın **WF45GettingStartedTutorial** çözümü Visual Studio 2012.

###  <a name="BKMK_UpdateWorkflows"></a> İş akışları güncelleştirmek için
 Bu bölümde, iş akışı tanımları güncelleştirilir. İki `WriteLine` güncelleştirilmiş ve yeni bir kullanıcının tahmin geri bildirimde bulunun etkinlikleri `WriteLine` etkinlik sayısını tahmin sonra oyun hakkında ek bilgi sağlayan eklenir.

####  <a name="BKMK_UpdateStateMachine"></a> Durum makinesi iş akışını güncelleştirme

1.  İçinde **Çözüm Gezgini**altında **NumberGuessWorkflowActivities** proje, çift **StateMachineNumberGuessWorkflow.xaml**.

2.  Çift **yanlış tahmin** durum makinesinin geçişi.

3.  Güncelleştirme `Text` en sol `WriteLine` içinde `If` etkinlik.

    ```vb
    Guess & " is too low."
    ```

    ```csharp
    Guess + " is too low."
    ```

4.  Güncelleştirme `Text` en sağ `WriteLine` içinde `If` etkinlik.

    ```vb
    Guess & " is too high."
    ```

    ```csharp
    Guess + " is too high."
    ```

5.  İade için genel durum makinesi iş akışı Tasarımcısı görünümünde tıklayarak **StateMachine** alan içerik haritasındaki iş akışı Tasarımcısı üst kısmında görüntüler.

6.  Çift **doğru tahmin** durum makinesinin geçişi.

7.  Sürükleme bir **WriteLine** etkinliğinden **Temelleri** bölümünü **araç kutusu** ve bırakın **Buraya Bırak eylem etkinliği** etiketi geçiş.

8.  İçine aşağıdaki ifadeyi yazın `Text` özellik kutusu.

    ```vb
    Guess & " is correct. You guessed it in " & Turns & " turns."
    ```

    ```csharp
    Guess + " is correct. You guessed it in " + Turns + " turns."
    ```

####  <a name="BKMK_UpdateFlowchart"></a> Akış Çizelgesi iş akışını güncelleştirme

1.  İçinde **Çözüm Gezgini**altında **NumberGuessWorkflowActivities** proje, çift **FlowchartNumberGuessWorkflow.xaml**.

2.  Güncelleştirme `Text` en sol `WriteLine` etkinlik.

    ```vb
    Guess & " is too low."
    ```

    ```csharp
    Guess + " is too low."
    ```

3.  Güncelleştirme `Text` en sağ `WriteLine` etkinlik.

    ```vb
    Guess & " is too high."
    ```

    ```csharp
    Guess + " is too high."
    ```

4.  Sürükleme bir **WriteLine** etkinliğinden **Temelleri** bölümünü **araç kutusu** sürükleyip bırakma noktasına `True` eylemi üstteki `FlowDecision` . `WriteLine` Etkinliği için akış eklenir ve bağlantılı `True` eylemi `FlowDecision`.

5.  İçine aşağıdaki ifadeyi yazın `Text` özellik kutusu.

    ```vb
    Guess & " is correct. You guessed it in " & Turns & " turns."
    ```

    ```csharp
    Guess + " is correct. You guessed it in " + Turns + " turns."
    ```

####  <a name="BKMK_UpdateSequential"></a> Sıralı iş akışını güncelleştirme

1.  İçinde **Çözüm Gezgini**altında **NumberGuessWorkflowActivities** proje, çift **SequentialNumberGuessWorkflow.xaml**.

2.  Güncelleştirme `Text` en sol `WriteLine` içinde `If` etkinlik.

    ```vb
    Guess & " is too low."
    ```

    ```csharp
    Guess + " is too low."
    ```

3.  Güncelleştirme `Text` en sağ `WriteLine` etkinliğinde `If` etkinlik.

    ```vb
    Guess & " is too high."
    ```

    ```csharp
    Guess + " is too high."
    ```

4.  Sürükleme bir **WriteLine** etkinliğinden **Temelleri** bölümünü **araç kutusu** ve bundan sonra açılan **DoWhile** etkinlik böylece  **WriteLine** kök son etkinlik olduğu `Sequence` etkinlik.

5.  İçine aşağıdaki ifadeyi yazın `Text` özellik kutusu.

    ```vb
    Guess & " is correct. You guessed it in " & Turns & " turns."
    ```

    ```csharp
    Guess + " is correct. You guessed it in " + Turns + " turns."
    ```

###  <a name="BKMK_UpdateWorkflowVersionMap"></a> Önceki iş akışı sürümünün içerecek şekilde WorkflowVersionMap güncelleştirmek için

1.  Çift **WorkflowVersionMap.cs** (veya **WorkflowVersionMap.vb**) altında **NumberGuessWorkflowHost** açmak için proje.

2.  Aşağıdaki `using` (veya `Imports`) diğer dosyasının en `using` (veya `Imports`) ifadeleri.

    ```vb
    Imports System.Reflection
    Imports System.IO
    ```

    ```csharp
    using System.Reflection;
    using System.IO;
    ```

3.  Üç mevcut iş akışı kimlik bildirimlerine hemen altına üç yeni iş akışı kimliklerini ekleyin. Bu yeni `v1` kimlikleri kullanılabilir iş akışı güncelleştirmeleri yapılmadan önce başlatılan iş akışları için doğru iş akışı tanımı belirtin.

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

4.  İçinde `WorkflowVersionMap` oluşturucusu, güncelleştirme `Version` üç geçerli iş akışı kimlikleri özelliği `2.0.0.0`.

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

     İş akışları sözlüğüne geçerli sürümleri kullanan iş akışı tanımları başlatan kodu güncelleştirilmesi gerekmez, projenizde başvurulan geçerli sürümleri, kodu ekler.

5.  Aşağıdaki kod oluşturucuda geçerli sürümler sözlüğe ekler koddan sonra ekleyin.

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

     Bu iş akışı kimlikleri, karşılık gelen iş akışı tanımları ilk sürümleri ile ilişkilidir.

6.  Ardından, iş akışı tanımları'nin ilk sürümünden içeren derlemeyi yüklemek ve oluşturun ve karşılık gelen iş akışı tanımları sözlüğüne ekleyin.

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

     Aşağıdaki örnek, tam listesi için güncelleştirilmiş `WorkflowVersionMap` sınıfı.

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

###  <a name="BKMK_BuildAndRun"></a> Derleme ve uygulamayı çalıştırmak için

1.  Uygulamayı oluşturmak için CTRL + SHIFT + B ve başlatmak için CTRL + F5 tuşlarına basın.

2.  Tıklayarak yeni bir iş akışının başlatılacağı **yeni oyun**. İş akışı sürümü altında durum penceresi görüntülenir ve güncelleştirilmiş sürümü ilişkili yansıtır `WorkflowIdentity`. Not `InstanceId` tamamlandığında, iş akışı için izleme dosyayı görüntülemek ve oyun tamamlanana kadar tahmin girin. Kullanıcının tahmin güncelleştirmeleri temel durum penceresinde görüntülenen bilgileri nasıl görüntüleneceğini unutmayın `WriteLine` etkinlikler.

 **Lütfen 1 ile 10 arasında bir sayı girin**  
**5 çok yüksektir.**  
**Lütfen 1 ile 10 arasında bir sayı girin**  
**3 çok yüksektir.**  
**Lütfen 1 ile 10 arasında bir sayı girin**  
**1 çok düşüktür.**  
**Lütfen 1 ile 10 arasında bir sayı girin**  
**Tebrikler, sayı 4 kapatır tahmin.**  

    > [!NOTE]
    >  Güncelleştirilmiş metinden `WriteLine` etkinlikleri görüntülenir, son çıktısını `WriteLine` bu konudaki eklendi etkinlik değil. Durum penceresi tarafından güncelleştirildiğinden olan `PersistableIdle` işleyici. İş akışı tamamlandıktan ve son etkinlikten sonra boşta geçmez, çünkü `PersistableIdle` işleyici çağrılmaz. Ancak, durum penceresi tarafından benzer bir ileti görüntülenir `Completed` işleyici. İçin isterseniz, kod eklenemedi `Completed` ından cümleler ayıklamak için işleyici `StringWriter` ve durum penceresi için görüntüleyin.

3.  Windows Gezgini'ni açın ve gidin **NumberGuessWorkflowHost\bin\debug** klasörü (veya **bin\release** proje ayarlarınıza bağlı olarak) karşılık gelen Not Defteri'ni kullanarak izleme dosyasını açın Tamamlanan iş akışı için. Not yapmadıysanız `InstanceId`, doğru izleme dosyası kullanarak tanımlayabilirsiniz **değiştirilme tarihi** Windows Explorer'da bilgileri.

 **Lütfen 1 ile 10 arasında bir sayı girin**
**5 çok yüksek.** 
 **Lütfen 1 ile 10 arasında bir sayı girin**
**3, çok yüksek.** 
 **Lütfen 1 ile 10 arasında bir sayı girin**
**1. çok düşük.** 
 **Lütfen 1 ile 10 arasında bir sayı girin**
**2 doğru. Bu 4 kapatır tahmin.**      Güncelleştirilmiş `WriteLine` çıkış çıktısını dahil olmak üzere izleme dosyası içinde yer alan `WriteLine` bu konudaki eklendi.

4.  Sayı tahmin eden uygulamaya geri geçin ve güncelleştirme yapılmadan önce başlatıldı iş akışları birini seçin. Seçili durumdaki iş akışı sürümü durum penceresi görüntülenir sürüm bilgilerine bakarak belirleyebilirsiniz. Tahminler girin ve eşleşme güncelleştirme durumu Not `WriteLine` etkinliği önceki bir sürümünden çıktı ve kullanıcının tahmin içermez. Bu iş akışları sahip olmayan bir önceki iş akışı tanımı kullanıyorsunuz çünkü `WriteLine` güncelleştirmeleri.

     Sonraki adımda [nasıl yapılır: çalışan iş akışı örneğinin tanımını güncelleştirme](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md), çalışan `v1` iş akışı örnekleri yeni işlevselliği içerdikleri şekilde güncelleştirilir `v2` örnekleri.
