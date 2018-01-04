---
title: "Nasıl yapılır: bir iş akışı yan yana birden fazla sürümünü ana bilgisayar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 09c575df-e0a3-4f3b-9e01-a7ac59d65287
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 96ae4d3e02b923187b3e0f88a7b18e84094fa584
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-host-multiple-versions-of-a-workflow-side-by-side"></a>Nasıl yapılır: bir iş akışı yan yana birden fazla sürümünü ana bilgisayar
`WorkflowIdentity`bir adı ve sürümü bir iş akışı tanımı ile ilişkilendirmek iş akışı uygulama geliştiricilerinin ve kalıcı iş akışı örneği ile ilişkili olması için bu bilgileri için bir yol sağlar. Bu kimlik bilgileri, iş akışı uygulama geliştiriciler tarafından birden çok iş akışı tanımı sürümlerinin yan yana yürütme gibi senaryoları etkinleştirmek için kullanılabilir ve dinamik güncelleştirme gibi diğer işlevleri için dönüm sağlar. Bu adım öğreticide nasıl kullanılacağını göstermektedir `WorkflowIdentity` aynı anda birden çok iş akışı sürümü barındırmak için.  
  
> [!NOTE]
>  Tamamlanmış sürümü indirme veya videosu öğreticinin görüntülemek için bkz: [Windows Workflow Foundation (WF45) - başlangıç Öğreticisi](http://go.microsoft.com/fwlink/?LinkID=248976).  
  
## <a name="in-this-topic"></a>Bu konuda  
 Öğreticinin bu adımında `WriteLine` iş akışı etkinlikleri ek bilgi ve yeni bir sağlamak için değiştirildiğinde `WriteLine` etkinlik eklenir. Özgün iş akışı derleme kopyası saklanır ve onu özgün ve güncelleştirilmiş iş akışları aynı anda çalıştırabilmeniz için ana bilgisayar uygulamasını güncelleştirilir.  
  
-   [NumberGuessWorkflowActivities proje bir kopyasını oluşturmak için](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_BackupCopy)  
  
-   [İş akışları güncelleştirmek için](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateWorkflows)  
  
    -   [Durum makinesi iş akışını güncelleştirmek için](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateStateMachine)  
  
    -   [Akış iş akışı güncelleştirmek için](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateFlowchart)  
  
    -   [Sıralı iş akışı güncelleştirmek için](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateSequential)  
  
-   [İş akışı önceki içerecek şekilde WorkflowVersionMap güncelleştirmek için](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateWorkflowVersionMap)  
  
-   [Derleme ve uygulamayı çalıştırmak için](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_BuildAndRun)  
  
> [!NOTE]
>  Bu konudaki adımları izleyerek önce uygulamayı çalıştırmak, her tür çeşitli iş akışlarını başlatmak ve her biri için bir veya iki tahmin yapma. Bu adım ve aşağıdaki adımı kalıcı bu iş akışları kullanılan [nasıl yapılır: iş akışı örneği çalışma tanım güncelleştirme](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md).  
  
> [!NOTE]
>  Başlarken Öğreticisi her adımı için önceki adımları değişir. Önceki adımları tamamlanmadıysa tamamen tamamlanmış bir sürümünü yükleyebilirsiniz [Windows Workflow Foundation (WF45) - başlangıç Öğreticisi](http://go.microsoft.com/fwlink/?LinkID=248976).  
  
###  <a name="BKMK_BackupCopy"></a>NumberGuessWorkflowActivities proje bir kopyasını oluşturmak için  
  
1.  Açık **WF45GettingStartedTutorial** çözümde [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] açık değilse.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
3.  Kapat **WF45GettingStartedTutorial** çözümü.  
  
4.  Windows Gezgini'ni açın ve Öğreticisi çözümünü dosya ve proje klasörleri bulunduğu klasöre gidin.  
  
5.  Adlı yeni bir klasör oluşturun **PreviousVersions** aynı klasörde **NumberGuessWorkflowHost** ve **NumberGuessWorkflowActivities**. Bu klasör, sonraki öğretici adımlarda kullanılan iş akışları farklı sürümlerini içeren derlemeler kapsamak için kullanılır.  
  
6.  Gidin **NumberGuessWorkflowActivities\bin\debug** klasörü (veya **bin\release** proje ayarlarınızı bağlı olarak). Kopya **NumberGuessWorkflowActivities.dll** ve yapıştırın **PreviousVersions** klasör.  
  
7.  Yeniden Adlandır **NumberGuessWorkflowActivities.dll** içinde **PreviousVersions** klasörüne **NumberGuessWorkflowActivities_v1.dll**.  
  
    > [!NOTE]
    >  Bu konudaki adımlarda, iş akışları birden fazla sürümünü kapsamak için kullanılmış derlemeleri yönetmenin bir yolu gösterilmektedir. Güçlü adlandırma derlemeler ve genel derleme önbelleğinde kaydetme gibi başka yöntemler de kullanılabilir.  
  
8.  Adlı yeni bir klasör oluşturun **NumberGuessWorkflowActivities_du** aynı klasörde **NumberGuessWorkflowHost**, **NumberGuessWorkflowActivities**ve yeni eklenen **PreviousVersions** klasörünü ve tüm dosyaları ve alt kopyalayın **NumberGuessWorkflowActivities** yeni klasöre  **NumberGuessWorkflowActivities_du** klasör. Proje etkinlikleri ilk sürümü için bu yedek kopyasını kullanılan [nasıl yapılır: iş akışı örneği çalışma tanım güncelleştirme](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md).  
  
9. Yeniden açın **WF45GettingStartedTutorial** çözümde [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].  
  
###  <a name="BKMK_UpdateWorkflows"></a>İş akışları güncelleştirmek için  
 Bu bölümde, iş akışı tanımları güncelleştirilir. İki `WriteLine` kullanıcının tahmin üzerinde görüş etkinlikleri güncelleştirilmiş ve yeni bir `WriteLine` etkinlik sayısını tahmin sonra oyun hakkında ek bilgi sağlayan eklenir.  
  
####  <a name="BKMK_UpdateStateMachine"></a>Durum makinesi iş akışını güncelleştirmek için  
  
1.  İçinde **Çözüm Gezgini**altında **NumberGuessWorkflowActivities** projesi, çift **StateMachineNumberGuessWorkflow.xaml**.  
  
2.  Çift **tahmin yanlış** durum makinesinin geçişi.  
  
3.  Güncelleştirme `Text` sol en `WriteLine` içinde `If` etkinlik.  
  
    ```vb  
    Guess & " is too low."  
    ```  
  
    ```csharp  
    Guess + " is too low."  
    ```  
  
4.  Güncelleştirme `Text` sağ en `WriteLine` içinde `If` etkinlik.  
  
    ```vb  
    Guess & " is too high."  
    ```  
  
    ```csharp  
    Guess + " is too high."  
    ```  
  
5.  Dönmek için genel durum makine görünümünde iş akışı Tasarımcısı'nı tıklatarak **Durum makinesi** haritasındaki iş akışı Tasarımcısı'nı üstünde görüntüle.  
  
6.  Çift **tahmin doğru** durum makinesinin geçişi.  
  
7.  Sürükleme bir **WriteLine** etkinliğinden **Temelleri** bölümünü **araç** ve bırakın **burada bırakma eylem etkinliği** etiketi Geçişi.  
  
8.  İçine aşağıdaki ifadeyi yazın `Text` özellik kutusu.  
  
    ```vb  
    Guess & " is correct. You guessed it in " & Turns & " turns."  
    ```  
  
    ```csharp  
    Guess + " is correct. You guessed it in " + Turns + " turns."  
    ```  
  
####  <a name="BKMK_UpdateFlowchart"></a>Akış iş akışı güncelleştirmek için  
  
1.  İçinde **Çözüm Gezgini**altında **NumberGuessWorkflowActivities** projesi, çift **FlowchartNumberGuessWorkflow.xaml**.  
  
2.  Güncelleştirme `Text` sol en `WriteLine` etkinlik.  
  
    ```vb  
    Guess & " is too low."  
    ```  
  
    ```csharp  
    Guess + " is too low."  
    ```  
  
3.  Güncelleştirme `Text` sağ en `WriteLine` etkinlik.  
  
    ```vb  
    Guess & " is too high."  
    ```  
  
    ```csharp  
    Guess + " is too high."  
    ```  
  
4.  Sürükleme bir **WriteLine** etkinliğinden **Temelleri** bölümünü **araç** ve açılan noktasında bırakma `True` eylemi en üstteki `FlowDecision` . `WriteLine` Etkinlik akış eklenir ve bağlantılı `True` eylemi `FlowDecision`.  
  
5.  İçine aşağıdaki ifadeyi yazın `Text` özellik kutusu.  
  
    ```vb  
    Guess & " is correct. You guessed it in " & Turns & " turns."  
    ```  
  
    ```csharp  
    Guess + " is correct. You guessed it in " + Turns + " turns."  
    ```  
  
####  <a name="BKMK_UpdateSequential"></a>Sıralı iş akışı güncelleştirmek için  
  
1.  İçinde **Çözüm Gezgini**altında **NumberGuessWorkflowActivities** projesi, çift **SequentialNumberGuessWorkflow.xaml**.  
  
2.  Güncelleştirme `Text` sol en `WriteLine` içinde `If` etkinlik.  
  
    ```vb  
    Guess & " is too low."  
    ```  
  
    ```csharp  
    Guess + " is too low."  
    ```  
  
3.  Güncelleştirme `Text` sağ en `WriteLine` etkinliğinde `If` etkinlik.  
  
    ```vb  
    Guess & " is too high."  
    ```  
  
    ```csharp  
    Guess + " is too high."  
    ```  
  
4.  Sürükleme bir **WriteLine** etkinliğinden **Temelleri** bölümünü **araç** ve bundan sonra bırakma **DoWhile** etkinlik böylece  **WriteLine** kök son etkinlik olduğu `Sequence` etkinlik.  
  
5.  İçine aşağıdaki ifadeyi yazın `Text` özellik kutusu.  
  
    ```vb  
    Guess & " is correct. You guessed it in " & Turns & " turns."  
    ```  
  
    ```csharp  
    Guess + " is correct. You guessed it in " + Turns + " turns."  
    ```  
  
###  <a name="BKMK_UpdateWorkflowVersionMap"></a>İş akışı önceki içerecek şekilde WorkflowVersionMap güncelleştirmek için  
  
1.  Çift **WorkflowVersionMap.cs** (veya **WorkflowVersionMap.vb**) altında **NumberGuessWorkflowHost** projeyi açın.  
  
2.  Aşağıdakileri ekleyin `using` (veya `Imports`) diğer dosyanın en üstüne deyimlerini `using` (veya `Imports`) deyimleri.  
  
    ```vb  
    Imports System.Reflection  
    Imports System.IO  
    ```  
  
    ```csharp  
    using System.Reflection;  
    using System.IO;  
    ```  
  
3.  Üç yeni iş akışı kimlikleri üç mevcut iş akışı kimliği bildirimleri hemen altına ekleyin. Bu yeni `v1` iş akışı kimlikleri kullanılacak doğru iş akışı tanımı güncelleştirmeleri yapılmadan önce başlatılan iş akışları sağlar.  
  
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
  
4.  İçinde `WorkflowVersionMap` oluşturucusu, güncelleştirme `Version` üç geçerli iş akışı kimlikleri özelliğinin `2.0.0.0`.  
  
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
  
     İş akışları sözlüğüne geçerli sürümleri kullanan iş akışı tanımları başlatır kod güncelleştirilmesi gerek yoktur, böylece projesinde başvurulan geçerli sürümleri, kodda ekler.  
  
5.  Geçerli sürümler sözlüğe ekler koddan sonra oluşturucuda aşağıdaki kodu ekleyin.  
  
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
  
     Bu iş akışı kimlikleri karşılık gelen iş akışı tanımları ilk sürümleri ile ilişkilendirilir.  
  
6.  Ardından, iş akışı tanımları ilk sürümünü içeren derleme yükleme ve oluşturun ve karşılık gelen iş akışı tanımları sözlüğe ekleyin.  
  
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
  
     Aşağıdaki örnek tam listesi için güncelleştirilmiş olan `WorkflowVersionMap` sınıfı.  
  
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
  
###  <a name="BKMK_BuildAndRun"></a>Derleme ve uygulamayı çalıştırmak için  
  
1.  Uygulamanızı oluşturmak için CTRL + SHIFT + B ve başlatmak için CTRL + F5 tuşuna basın.  
  
2.  Tıklayarak yeni bir iş akışı Başlat **yeni bir oyun**. İş akışı sürümü altında durum penceresi görüntülenir ve güncelleştirilmiş sürümü ilişkili yansıtır `WorkflowIdentity`. Not `InstanceId` tamamlandığında iş akışı için izleme dosyasını görüntülemek ve oyun tamamlanana kadar tahmin girin. Kullanıcının tahmin güncelleştirmeler göre durum penceresinde görüntülenen bilgileri nasıl görüntüleneceğini unutmayın `WriteLine` etkinlikler.  
  
 **Lütfen 1 ile 10 arasında bir sayı girin**  
**5 çok yüksektir.**   
**Lütfen 1 ile 10 arasında bir sayı girin**   
**3 çok yüksektir.**   
**Lütfen 1 ile 10 arasında bir sayı girin**   
**1 çok düşük olur.**   
**Lütfen 1 ile 10 arasında bir sayı girin**   
**Tebrikler, sayı 4 kapatır tahmin.**    
    > [!NOTE]
    >  Güncelleştirilmiş metinden `WriteLine` etkinlikler görüntülenir, son çıktısını `WriteLine` bu konudaki eklendi etkinliği değil. Durum penceresi tarafından güncelleştirilir çünkü `PersistableIdle` işleyicisi. İş akışı tamamlandıktan ve son etkinlik sonra boşta geçmez çünkü `PersistableIdle` işleyici çağrılmaz. Ancak, durum penceresinde tarafından benzer bir ileti görüntülenir `Completed` işleyicisi. İsterseniz, kod eklenemedi `Completed` Metinden ayıklamak için işleyici `StringWriter` ve durum penceresi görüntüleyin.  
  
3.  Windows Gezgini'ni açın ve gidin **NumberGuessWorkflowHost\bin\debug** klasörü (veya **bin\release** proje ayarlarınızı bağlı olarak) ve karşılık gelen Not Defteri'ni kullanarak izleme dosyasını açın Tamamlanan iş akışına. Not yapmadınız varsa `InstanceId`, doğru izleme dosyası kullanarak tanımlayabilirsiniz **değiştirilme tarihi** Windows Gezgini'nde bilgi.  
  
 **Lütfen 1 ile 10 arasında bir sayı girin**  
**5 çok yüksektir.**   
**Lütfen 1 ile 10 arasında bir sayı girin**   
**3 çok yüksektir.**   
**Lütfen 1 ile 10 arasında bir sayı girin**   
**1 çok düşük olur.**   
**Lütfen 1 ile 10 arasında bir sayı girin**   
**2 doğrudur. Bu 4 kapatır tahmin.**      Güncelleştirilmiş `WriteLine` çıkış çıktısını dahil olmak üzere izleme dosyasında bulunan `WriteLine` bu konudaki eklendi.  
  
4.  Geri sayı tahmin eden uygulamaya geçin ve güncelleştirme yapılmadan önce başlatıldı iş akışları birini seçin. Şu anda seçili iş akışı sürümü durum penceresi görüntülenen sürüm bilgilerini bakarak belirleyebilirsiniz. Tahminler girin ve durum eşleşme güncelleştirildiğine dikkat `WriteLine` etkinlik çıkış önceki bir sürümden ve kullanıcının tahmin içermez. Bu iş akışları sahip olmayan önceki iş akışı tanımı kullandığından olan `WriteLine` güncelleştirmeler.  
  
     Sonraki adımda [nasıl yapılır: iş akışı örneği çalışma tanım güncelleştirme](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md), çalışan `v1` iş akışı örnekleri olarak yeni işlevsellik içerdikleri şekilde güncelleştirilir `v2` örnekleri.
