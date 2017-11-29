---
title: "Nasıl yapılır: oluşturma ve uzun çalıştırma iş akışını çalıştıran"
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
ms.assetid: c0043c89-2192-43c9-986d-3ecec4dd8c9c
caps.latest.revision: "40"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4a266613b975065b37c176ec07ae404b5b17ddd7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-and-run-a-long-running-workflow"></a>Nasıl yapılır: oluşturma ve uzun çalıştırma iş akışını çalıştıran
Merkezi özelliklerinden biri [!INCLUDE[wf](../../../includes/wf-md.md)] kalıcı hale getirmek ve boşta iş akışları veritabanına unload zamanının yeteneği. ' Ndaki adımları [nasıl yapılır: bir iş akışını çalıştırma](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) bir konsol uygulaması kullanarak iş akışı barındırma temelleri gösterilmektedir. Örnekler başlangıç iş akışları, iş akışı yaşam döngüsü işleyicileri ve devam ettirme yer işaretleri gösterilmesine neden olan. İş akışı Kalıcılık etkili bir şekilde göstermek için daha karmaşık bir iş akışı ana gerekli değildir başlatılıyor ve birden çok iş akışı örneği sürdürme destekler. Bu adım öğreticide nasıl başlatma ve sürdürme birden çok iş akışı örnekleri, iş akışı Kalıcılık destekleyen ve izleme gibi gelişmiş özellikler için temel sağlayan uygulama ve olan sürüm oluşturma Windows form konağı oluşturulacağını gösterir sonraki öğretici adımlar gösterilmektedir.  
  
> [!NOTE]
>  Bu öğretici adımı ve sonraki adımları tüm üç iş akışı türlerinden kullanmak [nasıl yapılır: bir iş akışı oluşturmak](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md). Üç tür tamamlanmadıysa yer alan adımları tamamlanmış bir sürümünü yükleyebilirsiniz [Windows Workflow Foundation (WF45) - başlangıç Öğreticisi](http://go.microsoft.com/fwlink/?LinkID=248976).  
  
> [!NOTE]
>  Tamamlanmış sürümü indirme veya videosu öğreticinin görüntülemek için bkz: [Windows Workflow Foundation (WF45) - başlangıç Öğreticisi](http://go.microsoft.com/fwlink/?LinkID=248976).  
  
## <a name="in-this-topic"></a>Bu konuda  
  
-   [Kalıcılık veritabanı oluşturmak için](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_CreatePersistenceDatabase)  
  
-   [DurableInstancing derlemelerine başvuru eklemek için](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_AddReference)  
  
-   [İş akışı ana form oluşturmak için](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_CreateForm)  
  
-   [Formun yardımcı yöntemler ve özellikler eklemek için](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_AddHelperMethods)  
  
-   [Örnek deposu, iş akışı yaşam döngüsü işleyicileri ve uzantıları yapılandırmak için](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_ConfigureWorkflowApplication)  
  
-   [Başlangıç ve birden çok iş akışı türü sürdürme etkinleştirmek için](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_WorkflowVersionMap)  
  
-   [Yeni bir iş akışını başlatmak için](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_StartWorkflow)  
  
-   [Bir iş akışını sürdürmek için](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_ResumeWorkflow)  
  
-   [Bir iş akışı sonlanmaya](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_TerminateWorkflow)  
  
-   [Derleme ve uygulamayı çalıştırmak için](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_BuildAndRun)  
  
###  <a name="BKMK_CreatePersistenceDatabase"></a>Kalıcılık veritabanı oluşturmak için  
  
1.  SQL Server Management Studio'yu açın ve yerel, örneğin sunucuya **. \SQLEXPRESS**. Sağ **veritabanları** düğüm seçin ve yerel sunucu üzerinde **yeni veritabanı**. Yeni bir veritabanı adı **WF45GettingStartedTutorial**, diğer tüm değerleri kabul edin ve seçin **Tamam**.  
  
    > [!NOTE]
    >  Sahip olduğundan emin olun **Create Database** veritabanı oluşturmadan önce yerel sunucuda izni.  
  
2.  Seçin **açık**, **dosya** gelen **dosya** menüsü. Aşağıdaki klasöre göz atın:`C:\Windows\Microsoft.NET\Framework\4.0.30319\sql\en`  
  
     Aşağıdaki iki dosyasını seçin ve tıklatın **açık**.  
  
    -   SqlWorkflowInstanceStoreLogic.sql  
  
    -   SqlWorkflowInstanceStoreSchema.sql  
  
3.  Seçin **SqlWorkflowInstanceStoreSchema.sql** gelen **penceresi** menüsü. Emin **WF45GettingStartedTutorial** seçildiyse **kullanılabilir veritabanları** açılır ve seçin **yürütme** gelen **sorgu**menüsü.  
  
4.  Seçin **SqlWorkflowInstanceStoreLogic.sql** gelen **penceresi** menüsü. Emin **WF45GettingStartedTutorial** seçildiyse **kullanılabilir veritabanları** açılır ve seçin **yürütme** gelen **sorgu**menüsü.  
  
    > [!WARNING]
    >  Önceki iki adımı doğru sırayla gerçekleştirilmesi önemlidir. Sorguları bozuk yürütüldüğünden, hataları oluşur ve kalıcılığı veritabanı doğru yapılandırılmamış.  
  
###  <a name="BKMK_AddReference"></a>DurableInstancing derlemelerine başvuru eklemek için  
  
1.  Sağ **NumberGuessWorkflowHost** içinde **Çözüm Gezgini** seçip **Başvuru Ekle**.  
  
2.  Seçin **derlemeleri** gelen **Başvuru Ekle** listesi ve türü `DurableInstancing` içine **arama derlemeleri** kutusu. Bu derlemeler filtreler ve seçmek istenen başvuruları kolaylaştırır.  
  
3.  Yanındaki onay kutusunu işaretleyin **System.Activities.DurableInstancing** ve **System.Runtime.DurableInstancing** gelen **arama sonuçları** liste öğesini tıklatıp **Tamam**.  
  
###  <a name="BKMK_CreateForm"></a>İş akışı ana form oluşturmak için  
  
> [!NOTE]
>  Bu yordamdaki adımları eklemek ve form el ile yapılandırmak nasıl açıklar. İsterseniz, Öğretici için çözüm dosyalarını indirin ve tamamlanmış formu projeye ekleyin. Öğretici dosyaları indirmek için bkz: [Windows Workflow Foundation (WF45) - başlangıç Öğreticisi](http://go.microsoft.com/fwlink/?LinkID=248976). İndirilen dosyaları sonra sağ **NumberGuessWorkflowHost** ve **Başvuru Ekle**. Bir başvuru ekleyin **System.Windows.Forms** ve **System.Drawing**. Yeni bir formdan eklerseniz, bu başvuruları otomatik olarak eklenen **Ekle**, **yeni öğe** menüsünde bir form alırken el ile eklenmesi gerekir, ancak. Başvuruları eklendikten sonra sağ tıklatın **NumberGuessWorkflowHost** içinde **Çözüm Gezgini** ve **Ekle**, **varolan öğeyi**. Gözat `Form` select proje dosyalarını klasöründe **WorkflowHostForm.cs** (veya **WorkflowHostForm.vb**), tıklatıp **Ekle**. Formun içe aktarmayı seçin sonra bir sonraki bölüm aşağıya doğru atlayabilirsiniz [biçiminde yardımcı yöntemler ve özellikler eklemek için](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_AddHelperMethods).  
  
1.  Sağ **NumberGuessWorkflowHost** içinde **Çözüm Gezgini** ve **Ekle**, **yeni öğe**.  
  
2.  İçinde **yüklü** şablonları listesinde, seçin **Windows formu**, türü `WorkflowHostForm` içinde **adı** ve'ı tıklatın **Ekle**.  
  
3.  Aşağıdaki özellikler form üzerinde yapılandırın.  
  
    |Özellik|Değer|  
    |--------------|-----------|  
    |FormBorderStyle|FixedSingle|  
    |MaximizeBox|False|  
    |Boyut|400, 420|  
  
4.  Aşağıdaki denetimleri form sırada belirtilen özelliklerini ve yönergelerine uygun olarak yapılandırın ekleyin.  
  
    |Denetim|Özellik: değer|  
    |-------------|---------------------|  
    |**Düğmesi**|Ad: NewGame<br /><br /> Konum: 13, 13<br /><br /> Boyut: 75, 23<br /><br /> Metin: Yeni bir oyun|  
    |**Etiket**|Konum: 94, 18<br /><br /> Metin: tahmin ettiğiniz bir sayı 1'den|  
    |**ComboBox**|Ad: NumberRange<br /><br /> DropDownStyle: DropDownList<br /><br /> Öğeleri: 10, 100, 1000<br /><br /> Konum: 228, 12<br /><br /> Boyut: 143, 21|  
    |**Etiket**|Konum: 13, 43<br /><br /> Metin: İş akışı türü|  
    |**ComboBox**|Ad: WorkflowType<br /><br /> DropDownStyle: DropDownList<br /><br /> Öğeleri: StateMachineNumberGuessWorkflow, FlowchartNumberGuessWorkflow, SequentialNumberGuessWorkflow<br /><br /> Konum: 94, 40<br /><br /> Boyut: 277, 21|  
    |**Etiket**|Ad: WorkflowVersion<br /><br /> Konum: 13, 362<br /><br /> Metin: İş akışı sürümü|  
    |**GroupBox**|Konum: 13, 67<br /><br /> Boyut: 358, 287<br /><br /> Metin: oyun|  
  
    > [!NOTE]
    >  Aşağıdaki denetimleri eklerken, bunları GroupBox yerleştirin.  
  
    |Denetim|Özellik: değer|  
    |-------------|---------------------|  
    |**Etiket**|Konum: 7, 20<br /><br /> Metin: İş akışı örneği kimliği|  
    |**ComboBox**|Name: örnek kimliği<br /><br /> DropDownStyle: DropDownList<br /><br /> Konum: 121, 17<br /><br /> Boyut: 227, 21|  
    |**Etiket**|Konum: 7, 47<br /><br /> Metin: tahmin|  
    |**Metin kutusu**|Ad: tahmin<br /><br /> Konum: 50, 44<br /><br /> Boyut: 65, 20|  
    |**Düğmesi**|Ad: EnterGuess<br /><br /> Konum: 121, 42<br /><br /> Boyut: 75, 23<br /><br /> Metin: Tahmin girin|  
    |**Düğmesi**|Ad: QuitGame<br /><br /> Konum: 274, 42<br /><br /> Boyut: 75, 23<br /><br /> Metin: çıkın|  
    |**Metin kutusu**|Ad: WorkflowStatus<br /><br /> Konum: 10, 73<br /><br /> Çok satırlı: True<br /><br /> Salt okunur: True<br /><br /> Kaydırma çubukları: dikey<br /><br /> Boyut: 338, 208|  
  
5.  Ayarlama **AcceptButton** forma özelliğinin **EnterGuess**.  
  
 Aşağıdaki örnek, tamamlanmış form gösterilmektedir.  
  
 ![WF45 Öğreticisi iş akışı ana Form Başlarken](../../../docs/framework/windows-workflow-foundation/media/wf45gettingstartedtutorialworkflowhostform.png "WF45GettingStartedTutorialWorkflowHostForm")  
  
###  <a name="BKMK_AddHelperMethods"></a>Formun yardımcı yöntemler ve özellikler eklemek için  
 Bu bölümdeki adımları özellikleri ve yardımcı yöntemler çalıştıran ve sayı tahmin iş akışları sürdürme desteklemek için kullanıcı Arabirimi formun Yapılandır form sınıfına ekleyin.  
  
1.  Sağ **WorkflowHostForm** içinde **Çözüm Gezgini** ve **görünümü kodu**.  
  
2.  Aşağıdakileri ekleyin `using` (veya `Imports`) diğer dosyanın en üstüne deyimlerini `using` (veya `Imports`) deyimleri.  
  
    ```vb  
    Imports System.Windows.Forms  
    Imports System.Activities.DurableInstancing  
    Imports System.Activities  
    Imports System.Data.SqlClient  
    Imports System.IO  
    ```  
  
    ```csharp  
    using System.Windows.Forms;  
    using System.Activities.DurableInstancing;  
    using System.Activities;  
    using System.Data.SqlClient;  
    using System.IO;  
    ```  
  
3.  Aşağıdaki üye bildirimleri ekleme **WorkflowHostForm** sınıfı.  
  
    ```vb  
    Const connectionString = "Server=.\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI"  
    Dim store As SqlWorkflowInstanceStore  
    Dim WorkflowStarting As Boolean  
    ```  
  
    ```csharp  
    const string connectionString = "Server=.\\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI";  
    SqlWorkflowInstanceStore store;  
    bool WorkflowStarting;  
    ```  
  
    > [!NOTE]
    >  Bağlantı dizenizi farklıysa, güncelleştirme `connectionString` veritabanınıza başvurmak için.  
  
4.  Ekleme bir `WorkflowInstanceId` özelliğine `WorkflowFormHost` sınıfı.  
  
    ```vb  
    Public ReadOnly Property WorkflowInstanceId() As Guid  
        Get  
            If InstanceId.SelectedIndex = -1 Then  
                Return Guid.Empty  
            Else  
                Return New Guid(InstanceId.SelectedItem.ToString())  
            End If  
        End Get  
    End Property  
    ```  
  
    ```csharp  
    public Guid WorkflowInstanceId  
    {  
        get  
        {  
            return InstanceId.SelectedIndex == -1 ? Guid.Empty : (Guid)InstanceId.SelectedItem;  
        }  
    }  
    ```  
  
     `InstanceId` Birleşik giriş kutusu kalıcı iş akışı örneği kimlikleri listesini görüntüler ve `WorkflowInstanceId` özelliği şu anda seçili iş akışı döndürür.  
  
5.  Form için bir işleyici ekleyin `Load` olay. İşleyici eklemek için geçiş **Tasarım görünümünde** form için tıklatın **olayları** en üstündeki simgesi **özellikleri** penceresi ve çift **yük**.  
  
    ```vb  
    Private Sub WorkflowHostForm_Load(sender As Object, e As EventArgs) Handles Me.Load  
  
    End Sub  
    ```  
  
    ```csharp  
    private void WorkflowHostForm_Load(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
6.  Aşağıdaki kodu ekleyin `WorkflowHostForm_Load`.  
  
    ```vb  
    'Initialize the store and configure it so that it can be used for  
    'multiple WorkflowApplication instances.  
    store = New SqlWorkflowInstanceStore(connectionString)  
    WorkflowApplication.CreateDefaultInstanceOwner(store, Nothing, WorkflowIdentityFilter.Any)  
  
    'Set default ComboBox selections.  
    NumberRange.SelectedIndex = 0  
    WorkflowType.SelectedIndex = 0  
  
    ListPersistedWorkflows()  
    ```  
  
    ```csharp  
    // Initialize the store and configure it so that it can be used for  
    // multiple WorkflowApplication instances.  
    store = new SqlWorkflowInstanceStore(connectionString);  
    WorkflowApplication.CreateDefaultInstanceOwner(store, null, WorkflowIdentityFilter.Any);  
  
    // Set default ComboBox selections.  
    NumberRange.SelectedIndex = 0;  
    WorkflowType.SelectedIndex = 0;  
  
    ListPersistedWorkflows();  
    ```  
  
     Form yüklediğinde, `SqlWorkflowInstanceStore` olan yapılandırılmış, aralık ve iş akışı türü birleşik giriş kutuları varsayılan değerlere ayarlanır ve kalıcı iş akışı örnekleri eklenir `InstanceId` birleşik giriş kutusu.  
  
7.  Ekleme bir `SelectedIndexChanged` işleyicisi `InstanceId`. İşleyici eklemek için geçiş **Tasarım görünümünde** form için seçin `InstanceId` birleşik giriş kutusu tıklatın **olayları** en üstündeki simgesi **özellikleri** penceresinde ve çift **SelectedIndexChanged**.  
  
    ```vb  
    Private Sub InstanceId_SelectedIndexChanged(sender As Object, e As EventArgs) Handles InstanceId.SelectedIndexChanged  
  
    End Sub  
    ```  
  
    ```csharp  
    private void InstanceId_SelectedIndexChanged(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
8.  Aşağıdaki kodu ekleyin `InstanceId_SelectedIndexChanged`. Kullanıcı bir iş akışı açılan kutuyu kullanarak seçtiğinde Bu işleyici durum penceresi güncelleştirir.  
  
    ```vb  
    If InstanceId.SelectedIndex = -1 Then  
        Return  
    End If  
  
    'Clear the status window.  
    WorkflowStatus.Clear()  
  
    'Get the workflow version and display it.  
    'If the workflow is just starting then this info will not  
    'be available in the persistence store so do not try and retrieve it.  
    If Not WorkflowStarting Then  
        Dim instance As WorkflowApplicationInstance = _  
            WorkflowApplication.GetInstance(WorkflowInstanceId, store)  
  
        WorkflowVersion.Text = _  
            WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity)  
  
        'Unload the instance.  
        instance.Abandon()  
    End If  
    ```  
  
    ```csharp  
    if (InstanceId.SelectedIndex == -1)  
    {  
        return;  
    }  
  
    // Clear the status window.  
    WorkflowStatus.Clear();  
  
    // Get the workflow version and display it.  
    // If the workflow is just starting then this info will not  
    // be available in the persistence store so do not try and retrieve it.  
    if (!WorkflowStarting)  
    {  
        WorkflowApplicationInstance instance =  
            WorkflowApplication.GetInstance(this.WorkflowInstanceId, store);  
  
        WorkflowVersion.Text =  
            WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity);  
  
        // Unload the instance.  
        instance.Abandon();  
    }  
    ```  
  
9. Aşağıdakileri ekleyin `ListPersistedWorkflows` form sınıfına yöntemi.  
  
    ```vb  
    Private Sub ListPersistedWorkflows()  
        Using localCon As New SqlConnection(connectionString)  
            Dim localCmd As String = _  
                "Select [InstanceId] from [System.Activities.DurableInstancing].[Instances] Order By [CreationTime]"  
  
            Dim cmd As SqlCommand = localCon.CreateCommand()  
            cmd.CommandText = localCmd  
            localCon.Open()  
            Using reader As SqlDataReader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
  
                While (reader.Read())  
                    'Get the InstanceId of the persisted Workflow.  
                    Dim id As Guid = Guid.Parse(reader(0).ToString())  
                    InstanceId.Items.Add(id)  
                End While  
            End Using  
        End Using  
    End Sub  
    ```  
  
    ```csharp  
    using (SqlConnection localCon = new SqlConnection(connectionString))  
    {  
        string localCmd =  
            "Select [InstanceId] from [System.Activities.DurableInstancing].[Instances] Order By [CreationTime]";  
  
        SqlCommand cmd = localCon.CreateCommand();  
        cmd.CommandText = localCmd;  
        localCon.Open();  
        using (SqlDataReader reader = cmd.ExecuteReader(CommandBehavior.CloseConnection))  
        {  
            while (reader.Read())  
            {  
                // Get the InstanceId of the persisted Workflow  
                Guid id = Guid.Parse(reader[0].ToString());  
                InstanceId.Items.Add(id);  
            }  
        }  
    }  
    ```  
  
     `ListPersistedWorkflows`kalıcı iş akışı örnekleri için örnek deposuna sorgular ve örnek kimlikleri ekler `cboInstanceId` birleşik giriş kutusu.  
  
10. Aşağıdakileri ekleyin `UpdateStatus` yöntemi ve form sınıfına karşılık gelen temsilci. Bu yöntem durum penceresi form üzerinde çalışmakta olan iş akışı durumunu güncelleştirir.  
  
    ```vb  
    Private Delegate Sub UpdateStatusDelegate(msg As String)  
    Public Sub UpdateStatus(msg As String)  
        'We may be on a different thread so we need to  
        'make this call using BeginInvoke.  
        If InvokeRequired Then  
            BeginInvoke(New UpdateStatusDelegate(AddressOf UpdateStatus), msg)  
        Else  
            If Not msg.EndsWith(vbCrLf) Then  
                msg = msg & vbCrLf  
            End If  
  
            WorkflowStatus.AppendText(msg)  
  
            'Ensure that the newly added status is visible.  
            WorkflowStatus.SelectionStart = WorkflowStatus.Text.Length  
            WorkflowStatus.ScrollToCaret()  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private delegate void UpdateStatusDelegate(string msg);  
    public void UpdateStatus(string msg)  
    {  
        // We may be on a different thread so we need to  
        // make this call using BeginInvoke.  
        if (InvokeRequired)  
        {  
            BeginInvoke(new UpdateStatusDelegate(UpdateStatus), msg);  
        }  
        else  
        {  
            if (!msg.EndsWith("\r\n"))  
            {  
                msg += "\r\n";  
            }  
            WorkflowStatus.AppendText(msg);  
  
            WorkflowStatus.SelectionStart = WorkflowStatus.Text.Length;  
            WorkflowStatus.ScrollToCaret();  
        }  
    }  
    ```  
  
11. Aşağıdakileri ekleyin `GameOver` yöntemi ve form sınıfına karşılık gelen temsilci. Bir iş akışı tamamlandığında, bu yöntem formun UI tamamlanmış bir iş akışı örneği kimliği kaldırarak güncelleştirmeleri gelen **InstanceId** birleşik giriş kutusu.  
  
    ```vb  
    Private Delegate Sub GameOverDelegate()  
    Private Sub GameOver()  
        If InvokeRequired Then  
            BeginInvoke(New GameOverDelegate(AddressOf GameOver))  
        Else  
            'Remove this instance from the InstanceId combo box.  
            InstanceId.Items.Remove(InstanceId.SelectedItem)  
            InstanceId.SelectedIndex = -1  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private delegate void GameOverDelegate();  
    private void GameOver()  
    {  
        if (InvokeRequired)  
        {  
            BeginInvoke(new GameOverDelegate(GameOver));  
        }  
        else  
        {  
            // Remove this instance from the combo box  
            InstanceId.Items.Remove(InstanceId.SelectedItem);  
            InstanceId.SelectedIndex = -1;  
        }  
    }  
    ```  
  
###  <a name="BKMK_ConfigureWorkflowApplication"></a>Örnek deposu, iş akışı yaşam döngüsü işleyicileri ve uzantıları yapılandırmak için  
  
1.  Ekleme bir `ConfigureWorkflowApplication` form sınıfına yöntemi.  
  
    ```vb  
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)  
  
    End Sub  
    ```  
  
    ```csharp  
    private void ConfigureWorkflowApplication(WorkflowApplication wfApp)  
    {      
    }  
    ```  
  
     Bu yöntem yapılandırır `WorkflowApplication`, istenen uzantılar ekler ve iş akışı yaşam döngüsü olayları için işleyiciler ekler.  
  
2.  İçinde `ConfigureWorkflowApplication`, belirtin `SqlWorkflowInstanceStore` için `WorkflowApplication`.  
  
    ```vb  
    'Configure the persistence store.  
    wfApp.InstanceStore = store  
    ```  
  
    ```csharp  
    // Configure the persistence store.  
    wfApp.InstanceStore = store;  
    ```  
  
3.  Ardından, oluşturun bir `StringWriter` örneği ve ekleyin `Extensions` koleksiyonu `WorkflowApplication`. Zaman bir `StringWriter` onu yakalar tüm uzantılar eklenen `WriteLine` etkinlik çıkışı. İş akışı boşta olduğunda `WriteLine` çıkış ayıklanan gelen `StringWriter` ve form üzerinde görüntülenir.  
  
    ```vb  
    'Add a StringWriter to the extensions. This captures the output  
    'from the WriteLine activities so we can display it in the form.  
    Dim sw As New StringWriter()  
    wfApp.Extensions.Add(sw)  
    ```  
  
    ```csharp  
    // Add a StringWriter to the extensions. This captures the output  
    // from the WriteLine activities so we can display it in the form.  
    StringWriter sw = new StringWriter();  
    wfApp.Extensions.Add(sw);  
    ```  
  
4.  Aşağıdaki işleyicisi ekleme `Completed` olay. Bir iş akışı başarıyla tamamlandığında, sayısı numarası durum penceresi görüntülenir tahmin çekildiği etkinleştirir. İş akışı sona ererse, sonlandırmanın nedeni özel durum bilgileri görüntülenir. İşleyici sonunda `GameOver` yöntemi çağrıldığında, hangi tamamlanan iş akışı iş akışı listesinden kaldırır.  
  
    ```vb  
    wfApp.Completed = _  
        Sub(e As WorkflowApplicationCompletedEventArgs)  
            If e.CompletionState = ActivityInstanceState.Faulted Then  
                UpdateStatus(String.Format("Workflow Terminated. Exception: {0}" & vbCrLf & "{1}", _  
                    e.TerminationException.GetType().FullName, _  
                    e.TerminationException.Message))  
            ElseIf e.CompletionState = ActivityInstanceState.Canceled Then  
                UpdateStatus("Workflow Canceled.")  
            Else  
                Dim Turns As Integer = Convert.ToInt32(e.Outputs("Turns"))  
                UpdateStatus(String.Format("Congratulations, you guessed the number in {0} turns.", Turns))  
            End If  
            GameOver()  
        End Sub  
    ```  
  
    ```csharp  
    wfApp.Completed = delegate(WorkflowApplicationCompletedEventArgs e)  
    {  
        if (e.CompletionState == ActivityInstanceState.Faulted)  
        {  
            UpdateStatus(string.Format("Workflow Terminated. Exception: {0}\r\n{1}",  
                e.TerminationException.GetType().FullName,  
                e.TerminationException.Message));  
        }  
        else if (e.CompletionState == ActivityInstanceState.Canceled)  
        {  
            UpdateStatus("Workflow Canceled.");  
        }  
        else  
        {  
            int Turns = Convert.ToInt32(e.Outputs["Turns"]);  
            UpdateStatus(string.Format("Congratulations, you guessed the number in {0} turns.", Turns));  
        }  
        GameOver();  
    };  
    ```  
  
5.  Aşağıdakileri ekleyin `Aborted` ve `OnUnhandledException` işleyicileri. `GameOver` Yöntemi çağrılmaz gelen `Aborted` işleyici ne zaman bir iş akışı örneği durduruldu çünkü değil sonlandırmak ve örnek daha sonra devam etmek mümkündür.  
  
    ```vb  
    wfApp.Aborted = _  
        Sub(e As WorkflowApplicationAbortedEventArgs)  
            UpdateStatus(String.Format("Workflow Aborted. Exception: {0}" & vbCrLf & "{1}", _  
                e.Reason.GetType().FullName, _  
                e.Reason.Message))  
        End Sub  
  
    wfApp.OnUnhandledException = _  
        Function(e As WorkflowApplicationUnhandledExceptionEventArgs)  
            UpdateStatus(String.Format("Unhandled Exception: {0}" & vbCrLf & "{1}", _  
                e.UnhandledException.GetType().FullName, _  
                e.UnhandledException.Message))  
            GameOver()  
            Return UnhandledExceptionAction.Terminate  
        End Function  
    ```  
  
    ```csharp  
    wfApp.Aborted = delegate(WorkflowApplicationAbortedEventArgs e)  
    {  
        UpdateStatus(string.Format("Workflow Aborted. Exception: {0}\r\n{1}",  
                e.Reason.GetType().FullName,  
                e.Reason.Message));  
    };  
  
    wfApp.OnUnhandledException = delegate(WorkflowApplicationUnhandledExceptionEventArgs e)  
    {  
        UpdateStatus(string.Format("Unhandled Exception: {0}\r\n{1}",  
                e.UnhandledException.GetType().FullName,  
                e.UnhandledException.Message));  
        GameOver();  
        return UnhandledExceptionAction.Terminate;  
    };  
    ```  
  
6.  Aşağıdakileri ekleyin `PersistableIdle` işleyicisi. Bu işleyici alır `StringWriter` eklenmiş olan uzantı ayıklar çıktısını `WriteLine` etkinlikleri ve durum penceresinde görüntüler.  
  
    ```vb  
    wfApp.PersistableIdle = _  
        Function(e As WorkflowApplicationIdleEventArgs)  
            'Send the current WriteLine outputs to the status window.  
            Dim writers = e.GetInstanceExtensions(Of StringWriter)()  
            For Each writer In writers  
                UpdateStatus(writer.ToString())  
            Next  
            Return PersistableIdleAction.Unload  
        End Function  
    ```  
  
    ```csharp  
    wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)  
    {  
        // Send the current WriteLine outputs to the status window.  
        var writers = e.GetInstanceExtensions<StringWriter>();  
        foreach (var writer in writers)  
        {  
            UpdateStatus(writer.ToString());  
        }  
        return PersistableIdleAction.Unload;  
    };  
    ```  
  
     <xref:System.Activities.PersistableIdleAction> Numaralandırması üç değeri vardır: <xref:System.Activities.PersistableIdleAction.None>, <xref:System.Activities.PersistableIdleAction.Persist>, ve <xref:System.Activities.PersistableIdleAction.Unload>. <xref:System.Activities.PersistableIdleAction.Persist>neden olur, ancak kalıcı hale getirmek için iş akışını kaldırmak iş akışı neden olmaz. <xref:System.Activities.PersistableIdleAction.Unload>kalıcı ve boşaltılması için iş akışı neden olur.  
  
     Aşağıdaki örnekte tamamlanmış olan `ConfigureWorkflowApplication` yöntemi.  
  
    ```vb  
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)  
        'Configure the persistence store.  
        wfApp.InstanceStore = store  
  
        'Add a StringWriter to the extensions. This captures the output  
        'from the WriteLine activities so we can display it in the form.  
        Dim sw As New StringWriter()  
        wfApp.Extensions.Add(sw)  
  
        wfApp.Completed = _  
            Sub(e As WorkflowApplicationCompletedEventArgs)  
                If e.CompletionState = ActivityInstanceState.Faulted Then  
                    UpdateStatus(String.Format("Workflow Terminated. Exception: {0}" & vbCrLf & "{1}", _  
                        e.TerminationException.GetType().FullName, _  
                        e.TerminationException.Message))  
                ElseIf e.CompletionState = ActivityInstanceState.Canceled Then  
                    UpdateStatus("Workflow Canceled.")  
                Else  
                    Dim Turns As Integer = Convert.ToInt32(e.Outputs("Turns"))  
                    UpdateStatus(String.Format("Congratulations, you guessed the number in {0} turns.", Turns))  
                End If  
                GameOver()  
            End Sub  
  
        wfApp.Aborted = _  
            Sub(e As WorkflowApplicationAbortedEventArgs)  
                UpdateStatus(String.Format("Workflow Aborted. Exception: {0}" & vbCrLf & "{1}", _  
                    e.Reason.GetType().FullName, _  
                    e.Reason.Message))  
            End Sub  
  
        wfApp.OnUnhandledException = _  
            Function(e As WorkflowApplicationUnhandledExceptionEventArgs)  
                UpdateStatus(String.Format("Unhandled Exception: {0}" & vbCrLf & "{1}", _  
                    e.UnhandledException.GetType().FullName, _  
                    e.UnhandledException.Message))  
                GameOver()  
                Return UnhandledExceptionAction.Terminate  
            End Function  
  
        wfApp.PersistableIdle = _  
            Function(e As WorkflowApplicationIdleEventArgs)  
                'Send the current WriteLine outputs to the status window.  
                Dim writers = e.GetInstanceExtensions(Of StringWriter)()  
                For Each writer In writers  
                    UpdateStatus(writer.ToString())  
                Next  
                Return PersistableIdleAction.Unload  
            End Function  
    End Sub  
    ```  
  
    ```csharp  
    private void ConfigureWorkflowApplication(WorkflowApplication wfApp)  
    {  
        // Configure the persistence store.  
        wfApp.InstanceStore = store;  
  
        // Add a StringWriter to the extensions. This captures the output  
        // from the WriteLine activities so we can display it in the form.  
        StringWriter sw = new StringWriter();  
        wfApp.Extensions.Add(sw);  
  
        wfApp.Completed = delegate(WorkflowApplicationCompletedEventArgs e)  
        {  
            if (e.CompletionState == ActivityInstanceState.Faulted)  
            {  
                UpdateStatus(string.Format("Workflow Terminated. Exception: {0}\r\n{1}",  
                    e.TerminationException.GetType().FullName,  
                    e.TerminationException.Message));  
            }  
            else if (e.CompletionState == ActivityInstanceState.Canceled)  
            {  
                UpdateStatus("Workflow Canceled.");  
            }  
            else  
            {  
                int Turns = Convert.ToInt32(e.Outputs["Turns"]);  
                UpdateStatus(string.Format("Congratulations, you guessed the number in {0} turns.", Turns));  
            }  
            GameOver();  
        };  
  
        wfApp.Aborted = delegate(WorkflowApplicationAbortedEventArgs e)  
        {  
            UpdateStatus(string.Format("Workflow Aborted. Exception: {0}\r\n{1}",  
                    e.Reason.GetType().FullName,  
                    e.Reason.Message));  
        };  
  
        wfApp.OnUnhandledException = delegate(WorkflowApplicationUnhandledExceptionEventArgs e)  
        {  
            UpdateStatus(string.Format("Unhandled Exception: {0}\r\n{1}",  
                    e.UnhandledException.GetType().FullName,  
                    e.UnhandledException.Message));  
            GameOver();  
            return UnhandledExceptionAction.Terminate;  
        };  
  
        wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)  
        {  
            // Send the current WriteLine outputs to the status window.  
            var writers = e.GetInstanceExtensions<StringWriter>();  
            foreach (var writer in writers)  
            {  
                UpdateStatus(writer.ToString());  
            }  
            return PersistableIdleAction.Unload;  
        };  
    }  
    ```  
  
###  <a name="BKMK_WorkflowVersionMap"></a>Başlangıç ve birden çok iş akışı türü sürdürme etkinleştirmek için  
 Bir iş akışı örneği sürdürmek için bir iş akışı tanımını sağlamak üzere ana bilgisayar sahiptir. Bu öğreticide üç iş akışı türü vardır ve bu tür birden fazla sürümünü sonraki öğretici adımları tanıtır. `WorkflowIdentity`tanımlama bilgilerini kalıcı iş akışı örneği ile ilişkilendirilecek bir ana bilgisayar uygulaması için bir yol sağlar. Bu bölümdeki adımları kalıcı iş akışı örneği iş akışı kimliği karşılık gelen iş akışı tanımı için eşleme ile yardımcı olması için bir yardımcı sınıf oluşturmak nasıl ekleyebileceğiniz gösterilmektedir. [!INCLUDE[crabout](../../../includes/crabout-md.md)]`WorkflowIdentity` ve sürüm oluşturma, bkz: [kullanarak WorkflowIdentity ve sürüm oluşturma](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md).  
  
1.  Sağ **NumberGuessWorkflowHost** içinde **Çözüm Gezgini** ve **Ekle**, **sınıfı**. Tür `WorkflowVersionMap` içine **adı** kutusuna ve tıklatın **Ekle**.  
  
2.  Aşağıdakileri ekleyin `using` veya `Imports` deyimlerini dosyanın üst kısmındaki diğer `using` veya `Imports` deyimleri.  
  
    ```vb  
    Imports NumberGuessWorkflowActivities  
    Imports System.Activities  
    ```  
  
    ```csharp  
    using NumberGuessWorkflowActivities;  
    using System.Activities;  
    ```  
  
3.  Değiştir `WorkflowVersionMap` sınıf bildiriminin aşağıdaki bildirimiyle.  
  
    ```vb  
    Public Module WorkflowVersionMap  
        Dim map As Dictionary(Of WorkflowIdentity, Activity)  
  
        'Current version identities.  
        Public StateMachineNumberGuessIdentity As WorkflowIdentity  
        Public FlowchartNumberGuessIdentity As WorkflowIdentity  
        Public SequentialNumberGuessIdentity As WorkflowIdentity  
  
        Sub New()  
            map = New Dictionary(Of WorkflowIdentity, Activity)  
  
            'Add the current workflow version identities.  
            StateMachineNumberGuessIdentity = New WorkflowIdentity With  
            {  
                .Name = "StateMachineNumberGuessWorkflow",  
                .Version = New Version(1, 0, 0, 0)  
            }  
  
            FlowchartNumberGuessIdentity = New WorkflowIdentity With  
            {  
                .Name = "FlowchartNumberGuessWorkflow",  
                .Version = New Version(1, 0, 0, 0)  
            }  
  
            SequentialNumberGuessIdentity = New WorkflowIdentity With  
            {  
                .Name = "SequentialNumberGuessWorkflow",  
                .Version = New Version(1, 0, 0, 0)  
            }  
  
            map.Add(StateMachineNumberGuessIdentity, New StateMachineNumberGuessWorkflow())  
            map.Add(FlowchartNumberGuessIdentity, New FlowchartNumberGuessWorkflow())  
            map.Add(SequentialNumberGuessIdentity, New SequentialNumberGuessWorkflow())  
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
  
        static WorkflowVersionMap()  
        {  
            map = new Dictionary<WorkflowIdentity, Activity>();  
  
            // Add the current workflow version identities.  
            StateMachineNumberGuessIdentity = new WorkflowIdentity  
            {  
                Name = "StateMachineNumberGuessWorkflow",  
                Version = new Version(1, 0, 0, 0)  
            };  
  
            FlowchartNumberGuessIdentity = new WorkflowIdentity  
            {  
                Name = "FlowchartNumberGuessWorkflow",  
                Version = new Version(1, 0, 0, 0)  
            };  
  
            SequentialNumberGuessIdentity = new WorkflowIdentity  
            {  
                Name = "SequentialNumberGuessWorkflow",  
                Version = new Version(1, 0, 0, 0)  
            };  
  
            map.Add(StateMachineNumberGuessIdentity, new StateMachineNumberGuessWorkflow());  
            map.Add(FlowchartNumberGuessIdentity, new FlowchartNumberGuessWorkflow());  
            map.Add(SequentialNumberGuessIdentity, new SequentialNumberGuessWorkflow());  
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
  
     `WorkflowVersionMap`üç iş akışı tanımları Bu öğretici harita üç iş akışı kimlikleri içerir ve iş akışı başlatıldığında ve sürdürüldü aşağıdaki bölümlerde kullanılır.  
  
###  <a name="BKMK_StartWorkflow"></a>Yeni bir iş akışını başlatmak için  
  
1.  Ekleme bir `Click` işleyicisi `NewGame`. İşleyici eklemek için geçiş **Tasarım görünümünde** form ve çift `NewGame`. A `NewGame_Click` işleyici eklenir ve form için kod görüntülemek için görünümü geçer. Kullanıcı bu düğmesine tıkladığında yeni bir iş akışı başlatılır.  
  
    ```vb  
    Private Sub NewGame_Click(sender As Object, e As EventArgs) Handles NewGame.Click  
  
    End Sub  
    ```  
  
    ```csharp  
    private void NewGame_Click(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
2.  Aşağıdaki kod tıklatın işleyicisine ekleyin. Bu kodu bir bağımsız değişken adıyla anahtarlı iş akışı için giriş bağımsız değişkeni sözlüğü oluşturur. Bu sözlük Aralık açılan kutusundan alınan rastgele oluşturulmuş bir sayıya aralığı içeren bir girdiye sahiptir.  
  
    ```vb  
    Dim inputs As New Dictionary(Of String, Object)()  
    inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem))  
    ```  
  
    ```csharp  
    var inputs = new Dictionary<string, object>();  
    inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem));  
    ```  
  
3.  Ardından, iş akışı başlar aşağıdaki kodu ekleyin. `WorkflowIdentity` Ve seçili iş akışı türü için karşılık gelen iş akışı tanımı kullanılarak alınır `WorkflowVersionMap` yardımcı sınıfı. Sonraki, yeni bir `WorkflowApplication` örnek iş akışı tanımı kullanılarak oluşturulan `WorkflowIdentity`ve giriş bağımsız değişkeni sözlüğü.  
  
    ```vb  
    Dim identity As WorkflowIdentity = Nothing  
    Select Case WorkflowType.SelectedItem.ToString()  
        Case "SequentialNumberGuessWorkflow"  
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity  
  
        Case "StateMachineNumberGuessWorkflow"  
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity  
  
        Case "FlowchartNumberGuessWorkflow"  
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity  
    End Select  
  
    Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(identity)  
  
    Dim wfApp = New WorkflowApplication(wf, inputs, identity)  
    ```  
  
    ```csharp  
    WorkflowIdentity identity = null;  
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
    };  
  
    Activity wf = WorkflowVersionMap.GetWorkflowDefinition(identity);  
  
    WorkflowApplication wfApp = new WorkflowApplication(wf, inputs, identity);  
    ```  
  
4.  Ardından, iş akışını iş akışı listesine ekler ve form üzerinde iş akışının sürüm bilgilerini görüntüler aşağıdaki kodu ekleyin.  
  
    ```vb  
    'Add the workflow to the list and display the version information.  
    WorkflowStarting = True  
    InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id)  
    WorkflowVersion.Text = identity.ToString()  
    WorkflowStarting = False  
    ```  
  
    ```csharp  
    // Add the workflow to the list and display the version information.  
    WorkflowStarting = true;  
    InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id);  
    WorkflowVersion.Text = identity.ToString();  
    WorkflowStarting = false;  
    ```  
  
5.  Çağrı `ConfigureWorkflowApplication` örnek deposu, uzantıları ve iş akışı yaşam döngüsü işleyicileri için bunu yapılandırmak için `WorkflowApplication` örneği.  
  
    ```vb  
    'Configure the instance store, extensions, and   
    'workflow lifecycle handlers.  
    ConfigureWorkflowApplication(wfApp)  
    ```  
  
    ```csharp  
    // Configure the instance store, extensions, and   
    // workflow lifecycle handlers.  
    ConfigureWorkflowApplication(wfApp);  
    ```  
  
6.  Son olarak, arama `Run`.  
  
    ```vb  
    'Start the workflow.  
    wfApp.Run()  
    ```  
  
    ```  
    // Start the workflow.  
    wfApp.Run();  
    ```  
  
     Aşağıdaki örnekte tamamlanmış olan `NewGame_Click` işleyici.  
  
    ```vb  
    Private Sub NewGame_Click(sender As Object, e As EventArgs) Handles NewGame.Click  
        'Start a new workflow.  
        Dim inputs As New Dictionary(Of String, Object)()  
        inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem))  
  
        Dim identity As WorkflowIdentity = Nothing  
        Select Case WorkflowType.SelectedItem.ToString()  
            Case "SequentialNumberGuessWorkflow"  
                identity = WorkflowVersionMap.SequentialNumberGuessIdentity  
  
            Case "StateMachineNumberGuessWorkflow"  
                identity = WorkflowVersionMap.StateMachineNumberGuessIdentity  
  
            Case "FlowchartNumberGuessWorkflow"  
                identity = WorkflowVersionMap.FlowchartNumberGuessIdentity  
        End Select  
  
        Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(identity)  
  
        Dim wfApp = New WorkflowApplication(wf, inputs, identity)  
  
        'Add the workflow to the list and display the version information.  
        WorkflowStarting = True  
        InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id)  
        WorkflowVersion.Text = identity.ToString()  
        WorkflowStarting = False  
  
        'Configure the instance store, extensions, and   
        'workflow lifecycle handlers.  
        ConfigureWorkflowApplication(wfApp)  
  
        'Start the workflow.  
        wfApp.Run()  
    End Sub  
    ```  
  
    ```csharp  
    private void NewGame_Click(object sender, EventArgs e)  
    {  
        var inputs = new Dictionary<string, object>();  
        inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem));  
  
        WorkflowIdentity identity = null;  
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
        };  
  
        Activity wf = WorkflowVersionMap.GetWorkflowDefinition(identity);  
  
        WorkflowApplication wfApp = new WorkflowApplication(wf, inputs, identity);  
  
        // Add the workflow to the list and display the version information.  
        WorkflowStarting = true;  
        InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id);  
        WorkflowVersion.Text = identity.ToString();  
        WorkflowStarting = false;  
  
        // Configure the instance store, extensions, and   
        // workflow lifecycle handlers.  
        ConfigureWorkflowApplication(wfApp);  
  
        // Start the workflow.  
        wfApp.Run();  
    }  
    ```  
  
###  <a name="BKMK_ResumeWorkflow"></a>Bir iş akışını sürdürmek için  
  
1.  Ekleme bir `Click` işleyicisi `EnterGuess`. İşleyici eklemek için geçiş **Tasarım görünümünde** form ve çift `EnterGuess`. Kullanıcı bu düğmesine tıkladığında bir iş akışı devam ettirilir.  
  
    ```vb  
    Private Sub EnterGuess_Click(sender As Object, e As EventArgs) Handles EnterGuess.Click  
  
    End Sub  
    ```  
  
    ```csharp  
    private void EnterGuess_Click(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
2.  Bir iş akışı iş akışı listesinde seçili olduğunu ve kullanıcının tahmin geçerli olduğundan emin olmak için aşağıdaki kodu ekleyin.  
  
    ```vb  
    If WorkflowInstanceId = Guid.Empty Then  
        MessageBox.Show("Please select a workflow.")  
        Return  
    End If  
  
    Dim userGuess As Integer  
    If Not Int32.TryParse(Guess.Text, userGuess) Then  
        MessageBox.Show("Please enter an integer.")  
        Guess.SelectAll()  
        Guess.Focus()  
        Return  
    End If  
    ```  
  
    ```csharp  
    if (WorkflowInstanceId == Guid.Empty)  
    {  
        MessageBox.Show("Please select a workflow.");  
        return;  
    }  
  
    int guess;  
    if (!Int32.TryParse(Guess.Text, out guess))  
    {  
        MessageBox.Show("Please enter an integer.");  
        Guess.SelectAll();  
        Guess.Focus();  
        return;  
    }  
    ```  
  
3.  Ardından, almak `WorkflowApplicationInstance` kalıcı iş akışı örneğinin. A `WorkflowApplicationInstance` henüz bir iş akışı tanımı ile ilişkilendirilmemiş bir kalıcı iş akışı örneği temsil eder. `DefinitionIdentity` , `WorkflowApplicationInstance` İçeren `WorkflowIdentity` kalıcı iş akışı örneğinin. Bu öğreticide `WorkflowVersionMap` eşlemek için kullanılan yardımcı program sınıfı `WorkflowIdentity` doğru iş akışı tanımı. İş akışı tanımı alındıktan sonra bir `WorkflowApplication` , doğru iş akışı tanımı kullanılarak oluşturulur.  
  
    ```vb  
    Dim instance As WorkflowApplicationInstance = _  
        WorkflowApplication.GetInstance(WorkflowInstanceId, store)  
  
    'Use the persisted WorkflowIdentity to retrieve the correct workflow  
    'definition from the dictionary.  
    Dim wf As Activity = _  
        WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity)  
  
    'Associate the WorkflowApplication with the correct definition  
    Dim wfApp As WorkflowApplication = _  
        New WorkflowApplication(wf, instance.DefinitionIdentity)  
    ```  
  
    ```csharp  
    WorkflowApplicationInstance instance =  
        WorkflowApplication.GetInstance(WorkflowInstanceId, store);  
  
    // Use the persisted WorkflowIdentity to retrieve the correct workflow  
    // definition from the dictionary.  
    Activity wf =  
        WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity);  
  
    // Associate the WorkflowApplication with the correct definition  
    WorkflowApplication wfApp =  
        new WorkflowApplication(wf, instance.DefinitionIdentity);  
    ```  
  
4.  Bir kez `WorkflowApplication` olan oluşturulan örnek deposu, iş akışı yaşam döngüsü işleyicileri ve uzantıları çağırarak yapılandırma `ConfigureWorkflowApplication`. Bu adımları her seferinde yeni bir yapılmalıdır `WorkflowApplication` oluşturulduğu ve iş akışı örneği içine yüklenmeden önce bunlar yapılmalıdır `WorkflowApplication`. İş akışı yüklendikten sonra kullanıcının tahmin ile devam ettirilir.  
  
    ```vb  
    'Configure the extensions and lifecycle handlers.  
    'Do this before the instance is loaded. Once the instance is  
    'loaded it is too late to add extensions.  
    ConfigureWorkflowApplication(wfApp)  
  
    'Load the workflow.  
    wfApp.Load(instance)  
  
    'Resume the workflow.  
    wfApp.ResumeBookmark("EnterGuess", userGuess)  
    ```  
  
    ```csharp  
    // Configure the extensions and lifecycle handlers.  
    // Do this before the instance is loaded. Once the instance is  
    // loaded it is too late to add extensions.  
    ConfigureWorkflowApplication(wfApp);  
  
    // Load the workflow.  
    wfApp.Load(instance);  
  
    // Resume the workflow.  
    wfApp.ResumeBookmark("EnterGuess", guess);  
    ```  
  
5.  Son olarak, tahmin textbox temizleyin ve formun başka bir tahmin kabul etmek için hazırlayın.  
  
    ```vb  
    'Clear the Guess textbox.  
    Guess.Clear()  
    Guess.Focus()  
    ```  
  
    ```csharp  
    // Clear the Guess textbox.  
    Guess.Clear();  
    Guess.Focus();  
    ```  
  
     Aşağıdaki örnekte tamamlanmış olan `EnterGuess_Click` işleyici.  
  
    ```vb  
    Private Sub EnterGuess_Click(sender As Object, e As EventArgs) Handles EnterGuess.Click  
        If WorkflowInstanceId = Guid.Empty Then  
            MessageBox.Show("Please select a workflow.")  
            Return  
        End If  
  
        Dim userGuess As Integer  
        If Not Int32.TryParse(Guess.Text, userGuess) Then  
            MessageBox.Show("Please enter an integer.")  
            Guess.SelectAll()  
            Guess.Focus()  
            Return  
        End If  
  
        Dim instance As WorkflowApplicationInstance = _  
            WorkflowApplication.GetInstance(WorkflowInstanceId, store)  
  
        'Use the persisted WorkflowIdentity to retrieve the correct workflow  
        'definition from the dictionary.  
        Dim wf As Activity = _  
            WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity)  
  
        'Associate the WorkflowApplication with the correct definition  
        Dim wfApp As WorkflowApplication = _  
            New WorkflowApplication(wf, instance.DefinitionIdentity)  
  
        'Configure the extensions and lifecycle handlers.  
        'Do this before the instance is loaded. Once the instance is  
        'loaded it is too late to add extensions.  
        ConfigureWorkflowApplication(wfApp)  
  
        'Load the workflow.  
        wfApp.Load(instance)  
  
        'Resume the workflow.  
        wfApp.ResumeBookmark("EnterGuess", userGuess)  
  
        'Clear the Guess textbox.  
        Guess.Clear()  
        Guess.Focus()  
    End Sub  
    ```  
  
    ```csharp  
    private void EnterGuess_Click(object sender, EventArgs e)  
    {  
        if (WorkflowInstanceId == Guid.Empty)  
        {  
            MessageBox.Show("Please select a workflow.");  
            return;  
        }  
  
        int guess;  
        if (!Int32.TryParse(Guess.Text, out guess))  
        {  
            MessageBox.Show("Please enter an integer.");  
            Guess.SelectAll();  
            Guess.Focus();  
            return;  
        }  
  
        WorkflowApplicationInstance instance =  
            WorkflowApplication.GetInstance(WorkflowInstanceId, store);  
  
        // Use the persisted WorkflowIdentity to retrieve the correct workflow  
        // definition from the dictionary.  
        Activity wf =  
            WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity);  
  
        // Associate the WorkflowApplication with the correct definition  
        WorkflowApplication wfApp =  
            new WorkflowApplication(wf, instance.DefinitionIdentity);  
  
        // Configure the extensions and lifecycle handlers.  
        // Do this before the instance is loaded. Once the instance is  
        // loaded it is too late to add extensions.  
        ConfigureWorkflowApplication(wfApp);  
  
        // Load the workflow.  
        wfApp.Load(instance);  
  
        // Resume the workflow.  
        wfApp.ResumeBookmark("EnterGuess", guess);  
  
        // Clear the Guess textbox.  
        Guess.Clear();  
        Guess.Focus();  
    }  
    ```  
  
###  <a name="BKMK_TerminateWorkflow"></a>Bir iş akışı sonlanmaya  
  
1.  Ekleme bir `Click` işleyicisi `QuitGame`. İşleyici eklemek için geçiş **Tasarım görünümünde** form ve çift `QuitGame`. Kullanıcı bu düğmesine tıkladığında seçili iş akışı sonlandırılır.  
  
    ```vb  
    Private Sub QuitGame_Click(sender As Object, e As EventArgs) Handles QuitGame.Click  
  
    End Sub  
    ```  
  
    ```csharp  
    private void QuitGame_Click(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
2.  Aşağıdaki kodu ekleyin `QuitGame_Click` işleyicisi. Bu kod, ilk bir iş akışı iş akışı listesinde seçili olduğundan emin olmak için kontrol eder. Kalıcı örneğine yükler sonra bir `WorkflowApplicationInstance`, kullanan `DefinitionIdentity` doğru iş akışı tanımı ve ardından başlatır belirlemek için `WorkflowApplication`. Uzantılar ve iş akışı yaşam döngüsü işleyicileri çağrısıyla sonraki yapılandırılmış `ConfigureWorkflowApplication`. Bir kez `WorkflowApplication` olan yapılandırılmış, yüklendiği ve ardından `Terminate` olarak adlandırılır.  
  
    ```vb  
    If WorkflowInstanceId = Guid.Empty Then  
        MessageBox.Show("Please select a workflow.")  
        Return  
    End If  
  
    Dim instance As WorkflowApplicationInstance = _  
        WorkflowApplication.GetInstance(WorkflowInstanceId, store)  
  
    'Use the persisted WorkflowIdentity to retrieve the correct workflow  
    'definition from the dictionary.  
    Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity)  
  
    'Associate the WorkflowApplication with the correct definition.  
    Dim wfApp As WorkflowApplication = _  
        New WorkflowApplication(wf, instance.DefinitionIdentity)  
  
    'Configure the extensions and lifecycle handlers.  
    ConfigureWorkflowApplication(wfApp)  
  
    'Load the workflow.  
    wfApp.Load(instance)  
  
    'Terminate the workflow.  
    wfApp.Terminate("User resigns.")  
    ```  
  
    ```csharp  
    if (WorkflowInstanceId == Guid.Empty)  
    {  
        MessageBox.Show("Please select a workflow.");  
        return;  
    }  
  
    WorkflowApplicationInstance instance =  
        WorkflowApplication.GetInstance(WorkflowInstanceId, store);  
  
    // Use the persisted WorkflowIdentity to retrieve the correct workflow  
    // definition from the dictionary.  
    Activity wf = WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity);  
  
    // Associate the WorkflowApplication with the correct definition  
    WorkflowApplication wfApp =  
        new WorkflowApplication(wf, instance.DefinitionIdentity);  
  
    // Configure the extensions and lifecycle handlers  
    ConfigureWorkflowApplication(wfApp);  
  
    // Load the workflow.  
    wfApp.Load(instance);  
  
    // Terminate the workflow.  
    wfApp.Terminate("User resigns.");  
    ```  
  
###  <a name="BKMK_BuildAndRun"></a>Derleme ve uygulamayı çalıştırmak için  
  
1.  Çift **Program.cs** (veya **Module1.vb**) içinde **Çözüm Gezgini** kodunu görüntülemek için.  
  
2.  Aşağıdakileri ekleyin `using` (veya `Imports`) deyimini dosyanın üst kısmındaki diğer `using` (veya `Imports`) deyimleri.  
  
    ```vb  
    Imports System.Windows.Forms  
    ```  
  
    ```csharp  
    using System.Windows.Forms;  
    ```  
  
3.  Kaldırın veya açıklama koddan barındırma mevcut iş akışı çıkışı [nasıl yapılır: bir iş akışını çalıştırma](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)ve aşağıdaki kod ile değiştirin.  
  
    ```vb  
    Sub Main()  
        Application.EnableVisualStyles()  
        Application.Run(New WorkflowHostForm())  
    End Sub  
    ```  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        Application.EnableVisualStyles();  
        Application.Run(new WorkflowHostForm());  
    }  
    ```  
  
4.  Sağ **NumberGuessWorkflowHost** içinde **Çözüm Gezgini** ve **özellikleri**. İçinde **uygulama** sekmesinde, belirtin **Windows uygulaması** için **çıktı türü**. Bu adım isteğe bağlıdır, ancak takip edilmemesi durumunda formun yanı sıra konsol penceresi görüntülenir.  
  
5.  Uygulamanızı oluşturmak için Ctrl + Shift + B tuşuna basın.  
  
6.  Emin **NumberGuessWorkflowHost** başlangıç uygulaması ayarlayın ve uygulamayı başlatmak için Ctrl + F5'e basın.  
  
7.  Tahmin eden oyun ve başlatın ve iş akışı türü için bir aralık seçmek **yeni oyun**. Bir tahmin girin **tahmin** kutusuna ve tıklatın **Git** , tahmin göndermek için. Unutmayın çıktısını `WriteLine` etkinlikleri form üzerinde görüntülenir.  
  
8.  Farklı iş akışı türü ve numarası aralıkları kullanarak çeşitli iş akışlarını başlatmak, bazı tahmin girin ve geçiş gelen seçerek iş akışları arasında **iş akışı örneği kimliği** listesi.  
  
     Yeni bir iş akışı geçiş yaptığınızda, önceki tahmin ve iş akışının ilerleme durumu penceresinde görüntülenmez olduğunu unutmayın. Değil yakalanan olduğundan ve her yerden kaydedilmiş durumu kullanılamıyor nedenidir. Öğreticinin sonraki adımda [nasıl yapılır: özel bir izleme katılımcı oluşturma](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md), bu bilgileri kaydeden özel izleme katılımcı oluşturun.
