---
title: Uzun süre çalışan bir iş akışı oluşturma ve çalıştırma
description: Bu makalede, birden çok iş akışı örneğini ve iş akışı kalıcılığını başlatmayı ve sürdürmeyi destekleyen bir Windows Forms ana bilgisayar uygulamasının nasıl oluşturulacağı gösterilmektedir.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c0043c89-2192-43c9-986d-3ecec4dd8c9c
ms.openlocfilehash: 557b3512e534198d47c0c6f6b0a7c5f92bb71739
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419557"
---
# <a name="how-to-create-and-run-a-long-running-workflow"></a>Uzun süre çalışan bir iş akışı oluşturma ve çalıştırma

Windows Workflow Foundation (WF) öğesinin merkezi özelliklerinden biri, çalışma zamanının boşta iş akışlarını bir veritabanına kalıcı ve kaldırma olanağıdır. [Nasıl yapılır: bir Iş akışını çalıştırma](how-to-run-a-workflow.md) , bir konsol uygulaması kullanarak iş akışı barındırma temelleri gösterilmektedir. Örnek olarak başlangıç iş akışları, iş akışı yaşam döngüsü işleyicileri gösterildi ve yer işaretleri sürdürülüyor. İş akışı kalıcılığını etkin bir şekilde göstermek için, birden çok iş akışı örneğini başlatmayı ve sürdürmeyi destekleyen daha karmaşık bir iş akışı konağı gerekir. Öğreticideki Bu adım, birden çok iş akışı örneğini başlatma ve sürdürmeyi destekleyen bir Windows form ana bilgisayar uygulamasının nasıl oluşturulduğunu, iş akışı kalıcılığını ve sonraki öğretici adımlarında gösterilen izleme ve sürüm oluşturma gibi gelişmiş özellikler için bir temel sağlar.

> [!NOTE]
> Bu öğretici adımı ve sonraki adımlarda, [nasıl yapılır: Iş akışı oluşturma](how-to-create-a-workflow.md)ile üç iş akışı türü kullanılır. Üç tür de tamamlamadıysanız, [Windows Workflow Foundation (WF45)-başlangıç öğreticisindeki](https://go.microsoft.com/fwlink/?LinkID=248976)adımların tamamlanmış bir sürümünü indirebilirsiniz.

> [!NOTE]
> Tamamlanmış bir sürümü indirmek veya öğreticiye ilişkin bir video kılavuzunu görüntülemek için, bkz. [Windows Workflow Foundation (WF45)-Başlangıç Öğreticisi](https://go.microsoft.com/fwlink/?LinkID=248976).

## <a name="to-create-the-persistence-database"></a>Kalıcılık veritabanını oluşturmak için

1. SQL Server Management Studio açın ve yerel sunucuya bağlanın, örneğin **.\Sqlexpress**. Yerel sunucuda **veritabanları** düğümüne sağ tıklayın ve **Yeni veritabanı**' nı seçin. Yeni veritabanını **WF45GettingStartedTutorial**olarak adlandırın, diğer tüm değerleri kabul edin ve **Tamam**' ı seçin.

    > [!NOTE]
    > Veritabanını oluşturmadan önce yerel sunucuda **Create Database** iznine sahip olduğunuzdan emin olun.

2. **Dosya** menüsünden **Aç**, **Dosya** ' yı seçin. Şu klasöre gidin: *C:\Windows\Microsoft.NET\Framework\v4.0.30319\sql\en*

    Aşağıdaki iki dosyayı seçin ve **Aç**' a tıklayın.

    - *Sqlworkflowcestorelogic. SQL*

    - *SqlWorkflowInstanceStoreSchema. SQL*

3. **Pencere** menüsünden **SqlWorkflowInstanceStoreSchema. SQL** öğesini seçin. **Kullanılabilir veritabanları** açılan menüsünde **WF45GettingStartedTutorial** ' nin seçili olduğundan emin olun ve **sorgu** menüsünden **Yürüt** ' ü seçin.

4. **Pencere** menüsünden **Sqlworkflowcestorelogic. SQL** öğesini seçin. **Kullanılabilir veritabanları** açılan menüsünde **WF45GettingStartedTutorial** ' nin seçili olduğundan emin olun ve **sorgu** menüsünden **Yürüt** ' ü seçin.

    > [!WARNING]
    > Önceki iki adımı doğru sırada gerçekleştirmek önemlidir. Sorgular sıra dışında yürütülürse hatalar oluşur ve Kalıcılık veritabanı doğru şekilde yapılandırılmaz.

## <a name="to-add-the-reference-to-the-durableinstancing-assemblies"></a>Başvuruyu Durableörnek oluşturma derlemelerine eklemek için

1. **Çözüm Gezgini** Için **Numberguessworkflowwhost** öğesine sağ tıklayın ve **Başvuru Ekle**' yi seçin.

2. **Başvuru Ekle** listesinden **derlemeler** ' i seçin ve `DurableInstancing` **derleme ara** kutusuna yazın. Bu, derlemelerin filtreleyeceğini ve istenen başvuruların seçimi daha kolay hale getirir.

3. **Arama sonuçları** listesinden **System. Activities. durableörnekınlist** ve **System. Runtime. durableörnekno** ' ın yanındaki onay kutusunu işaretleyin ve **Tamam**' a tıklayın.

## <a name="to-create-the-workflow-host-form"></a>İş akışı konak formunu oluşturmak için

> [!NOTE]
> Bu yordamdaki adımlarda, formun el ile nasıl ekleneceği ve yapılandırılacağı açıklanır. İsterseniz, öğreticinin çözüm dosyalarını indirebilir ve tamamlanmış formu projeye ekleyebilirsiniz. Öğretici dosyalarını indirmek için, bkz. [Windows Workflow Foundation (WF45)-Başlangıç Öğreticisi](https://go.microsoft.com/fwlink/?LinkID=248976). Dosyalar indirildikten sonra **Numberguessworkflowwhost** öğesine sağ tıklayın ve **Başvuru Ekle**' yi seçin. **System. Windows. Forms** ve **System. Drawing**için bir başvuru ekleyin. **Ekle**, **Yeni öğe** menüsünden Yeni bir form eklerseniz, ancak form içeri aktarılırken el ile eklenmesi gerekiyorsa, bu başvurular otomatik olarak eklenir. Başvurular eklendikten sonra, **Çözüm Gezgini** **Numberguessworkflowwhost** öğesine sağ tıklayın ve **Ekle**, **Varolan Öğe öğesini**seçin. `Form`Proje dosyalarındaki klasöre gidin, **WorkflowHostForm.cs** (veya **workflowwhostform. vb**) öğesini seçin ve **Ekle**' ye tıklayın. Formu içeri aktarmayı seçerseniz, [formun özellikler ve yardımcı yöntemleri eklemek için](#to-add-the-properties-and-helper-methods-of-the-form)sonraki bölüme atlayabilirsiniz.

1. **Çözüm Gezgini** Için **Numberguessworkflowwhost** öğesine sağ tıklayın ve **Ekle**, **Yeni öğe**seçeneğini belirleyin.

2. **Yüklü** şablonlar listesinde, **Windows formu**' nu seçin, `WorkflowHostForm` **ad** kutusuna yazın ve **Ekle**' ye tıklayın.

3. Formda aşağıdaki özellikleri yapılandırın.

    |Özellik|Değer|
    |--------------|-----------|
    |FormBorderStyle|FixedSingle|
    |MaximizeBox|False|
    |Boyut|400, 420|

4. Aşağıdaki denetimleri, belirtilen sırada forma ekleyin ve özellikleri yönlendirildiği şekilde yapılandırın.

    |Denetim|Özellik: değer|
    |-------------|---------------------|
    |**Düğme**|Ad: NewGame<br /><br /> Konum: 13, 13<br /><br /> Boyut: 75, 23<br /><br /> Metin: yeni oyun|
    |**Etiketle**|Konum: 94, 18<br /><br /> Metin: 1 ile arasında bir sayı tahmin edin|
    |**ComboBox**|Ad: NumberRange<br /><br /> DropDownStyle: DropDownList<br /><br /> Öğeler: 10, 100, 1000<br /><br /> Konum: 228, 12<br /><br /> Boyut: 143, 21|
    |**Etiketle**|Konum: 13, 43<br /><br /> Metin: Iş akışı türü|
    |**ComboBox**|Ad: WorkflowType<br /><br /> DropDownStyle: DropDownList<br /><br /> Öğeler: StateMachineNumberGuessWorkflow, FlowchartNumberGuessWorkflow, SequentialNumberGuessWorkflow<br /><br /> Konum: 94, 40<br /><br /> Boyut: 277, 21|
    |**Etiketle**|Ad: WorkflowVersion<br /><br /> Konum: 13, 362<br /><br /> Metin: Iş akışı sürümü|
    |**GroupBox**|Konum: 13, 67<br /><br /> Boyut: 358, 287<br /><br /> Metin: oyun|

    > [!NOTE]
    > Aşağıdaki denetimleri eklerken GroupBox içine yerleştirin.

    |Denetim|Özellik: değer|
    |-------------|---------------------|
    |**Etiketle**|Konum: 7, 20<br /><br /> Metin: Iş akışı örneği kimliği|
    |**ComboBox**|Ad: InstanceId<br /><br /> DropDownStyle: DropDownList<br /><br /> Konum: 121, 17<br /><br /> Boyut: 227, 21|
    |**Etiketle**|Konum: 7, 47<br /><br /> Metin: tahmin|
    |**TextBox**|Ad: tahmin<br /><br /> Konum: 50, 44<br /><br /> Boyut: 65, 20|
    |**Düğme**|Ad: Entertahmin<br /><br /> Konum: 121, 42<br /><br /> Boyut: 75, 23<br /><br /> Metin: tahmin girin|
    |**Düğme**|Ad: QuitGame<br /><br /> Konum: 274, 42<br /><br /> Boyut: 75, 23<br /><br /> Metin: çık|
    |**TextBox**|Ad: WorkflowStatus<br /><br /> Konum: 10, 73<br /><br /> Çoklu satır: doğru<br /><br /> ReadOnly: true<br /><br /> Kaydırma çubukları: dikey<br /><br /> Boyut: 338, 208|

5. Formun **AcceptButton** özelliğini **entertahmin**olarak ayarlayın.

 Aşağıdaki örnekte tamamlanan form gösterilmektedir.

 ![Windows Workflow Foundation Iş akışı konak formunun ekran görüntüsü.](./media/how-to-create-and-run-a-long-running-workflow/windows-workflow-foundation-workflowhostform.png)

## <a name="to-add-the-properties-and-helper-methods-of-the-form"></a>Formun özelliklerini ve yardımcı yöntemlerini eklemek için

Bu bölümdeki adımlarda, form sınıfına, çalışma ve tahmin sayısı tahmin iş akışlarına devam ettirmek için formun Kullanıcı arabirimini yapılandıran Özellikler ve yardımcı yöntemler ekleme.

1. **Çözüm Gezgini** ' de **Workflowwhostform** öğesine sağ tıklayın ve **kodu görüntüle**' yi seçin.

2. Aşağıdaki `using` (veya `Imports` ) deyimlerini, diğer `using` (veya `Imports` ) deyimleriyle dosyanın en üstüne ekleyin.

    ```vb
    Imports System.Activities
    Imports System.Activities.DurableInstancing
    Imports System.Data.SqlClient
    Imports System.IO
    Imports System.Windows.Forms
    ```

    ```csharp
    using System.Activities;
    using System.Activities.DurableInstancing;
    using System.Data.SqlClient;
    using System.IO;
    using System.Windows.Forms;
    ```

3. Aşağıdaki üye bildirimlerini **Workflowwhostform** sınıfına ekleyin.

    ```vb
    Const connectionString = "Server=.\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI"
    Dim store As SqlWorkflowInstanceStore
    Dim workflowStarting As Boolean
    ```

    ```csharp
    const string connectionString = "Server=.\\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI";
    SqlWorkflowInstanceStore store;
    bool workflowStarting;
    ```

    > [!NOTE]
    > Bağlantı dizeniz farklıysa, `connectionString` veritabanınıza başvuracak şekilde güncelleştirin.

4. Sınıfına bir `WorkflowInstanceId` özellik ekleyin `WorkflowFormHost` .

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

    `InstanceId`Birleşik giriş kutusu kalıcı iş akışı örneği kimliklerinin bir listesini görüntüler ve `WorkflowInstanceId` özelliği şu anda seçili olan iş akışını döndürür.

5. Form olayı için bir işleyici ekleyin `Load` . İşleyiciyi eklemek için form için **Tasarım görünümüne** geçin, **Özellikler** penceresinin üst kısmındaki **Olaylar** simgesine tıklayın ve **Yükle**' ye çift tıklayın.

    ```vb
    Private Sub WorkflowHostForm_Load(sender As Object, e As EventArgs) Handles Me.Load

    End Sub
    ```

    ```csharp
    private void WorkflowHostForm_Load(object sender, EventArgs e)
    {

    }
    ```

6. Aşağıdaki kodu `WorkflowHostForm_Load` içine ekleyin.

    ```vb
    ' Initialize the store and configure it so that it can be used for
    ' multiple WorkflowApplication instances.
    store = New SqlWorkflowInstanceStore(connectionString)
    WorkflowApplication.CreateDefaultInstanceOwner(store, Nothing, WorkflowIdentityFilter.Any)

    ' Set default ComboBox selections.
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

    Form yüklendiğinde,, `SqlWorkflowInstanceStore` Aralık ve iş akışı türü Birleşik giriş kutuları varsayılan değerlere ayarlanır ve kalıcı iş akışı örnekleri `InstanceId` açılan kutuya eklenir.

7. İçin bir `SelectedIndexChanged` işleyici ekleyin `InstanceId` . İşleyiciyi eklemek için form için **Tasarım görünümüne** geçiş yapın, `InstanceId` açılan kutuyu seçin, **Özellikler** penceresinin üst kısmındaki **Olaylar** simgesine tıklayın ve **SelectedIndexChanged**öğesine çift tıklayın.

    ```vb
    Private Sub InstanceId_SelectedIndexChanged(sender As Object, e As EventArgs) Handles InstanceId.SelectedIndexChanged

    End Sub
    ```

    ```csharp
    private void InstanceId_SelectedIndexChanged(object sender, EventArgs e)
    {

    }
    ```

8. Aşağıdaki kodu `InstanceId_SelectedIndexChanged` içine ekleyin. Kullanıcı açılan kutuyu kullanarak bir iş akışı seçtiğinde, bu işleyici durum penceresini güncelleştirir.

    ```vb
    If InstanceId.SelectedIndex = -1 Then
        Return
    End If

    ' Clear the status window.
    WorkflowStatus.Clear()

    ' Get the workflow version and display it.
    ' If the workflow is just starting then this info will not
    ' be available in the persistence store so do not try and retrieve it.
    If Not workflowStarting Then
        Dim instance As WorkflowApplicationInstance = _
            WorkflowApplication.GetInstance(WorkflowInstanceId, store)

        WorkflowVersion.Text = _
            WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity)

        ' Unload the instance.
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
    if (!workflowStarting)
    {
        WorkflowApplicationInstance instance =
            WorkflowApplication.GetInstance(this.WorkflowInstanceId, store);

        WorkflowVersion.Text =
            WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity);

        // Unload the instance.
        instance.Abandon();
    }
    ```

9. Aşağıdaki `ListPersistedWorkflows` yöntemi form sınıfına ekleyin.

    ```vb
    Private Sub ListPersistedWorkflows()
        Using localCon As New SqlConnection(connectionString)
            Dim localCmd As String = _
                "SELECT [InstanceId] FROM [System.Activities.DurableInstancing].[Instances] ORDER BY [CreationTime]"

            Dim cmd As SqlCommand = localCon.CreateCommand()
            cmd.CommandText = localCmd
            localCon.Open()
            Using reader As SqlDataReader = cmd.ExecuteReader(CommandBehavior.CloseConnection)

                While (reader.Read())
                    ' Get the InstanceId of the persisted Workflow.
                    Dim id As Guid = Guid.Parse(reader(0).ToString())
                    InstanceId.Items.Add(id)
                End While
            End Using
        End Using
    End Sub
    ```

    ```csharp
    using (var localCon = new SqlConnection(connectionString))
    {
        string localCmd =
            "SELECT [InstanceId] FROM [System.Activities.DurableInstancing].[Instances] ORDER BY [CreationTime]";

        SqlCommand cmd = localCon.CreateCommand();
        cmd.CommandText = localCmd;
        localCon.Open();
        using (SqlDataReader reader = cmd.ExecuteReader(CommandBehavior.CloseConnection))
        {
            while (reader.Read())
            {
                // Get the InstanceId of the persisted Workflow.
                Guid id = Guid.Parse(reader[0].ToString());
                InstanceId.Items.Add(id);
            }
        }
    }
    ```

    `ListPersistedWorkflows`kalıcı iş akışı örnekleri için örnek deposunu sorgular ve `cboInstanceId` Birleşik giriş kutusuna örnek kimliklerini ekler.

10. `UpdateStatus`Form sınıfına aşağıdaki yöntemi ve ilgili temsilciyi ekleyin. Bu yöntem, form üzerindeki durum penceresini Şu anda çalışan iş akışının durumuyla güncelleştirir.

    ```vb
    Private Delegate Sub UpdateStatusDelegate(msg As String)
    Public Sub UpdateStatus(msg As String)
        ' We may be on a different thread so we need to
        ' make this call using BeginInvoke.
        If InvokeRequired Then
            BeginInvoke(New UpdateStatusDelegate(AddressOf UpdateStatus), msg)
        Else
            If Not msg.EndsWith(vbCrLf) Then
                msg = msg & vbCrLf
            End If

            WorkflowStatus.AppendText(msg)

            ' Ensure that the newly added status is visible.
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

11. `GameOver`Form sınıfına aşağıdaki yöntemi ve ilgili temsilciyi ekleyin. Bir iş akışı tamamlandığında, bu yöntem, **InstanceId** Birleşik giriş kutusundan tamamlanan iş akışının örnek kimliğini kaldırarak form kullanıcı arabirimini güncelleştirir.

    ```vb
    Private Delegate Sub GameOverDelegate()
    Private Sub GameOver()
        If InvokeRequired Then
            BeginInvoke(New GameOverDelegate(AddressOf GameOver))
        Else
            ' Remove this instance from the InstanceId combo box.
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
            // Remove this instance from the combo box.
            InstanceId.Items.Remove(InstanceId.SelectedItem);
            InstanceId.SelectedIndex = -1;
        }
    }
    ```

## <a name="to-configure-the-instance-store-workflow-lifecycle-handlers-and-extensions"></a>Örnek deposunu, iş akışı yaşam döngüsü işleyicilerini ve uzantıları yapılandırmak için

1. `ConfigureWorkflowApplication`Form sınıfına bir yöntem ekleyin.

    ```vb
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)

    End Sub
    ```

    ```csharp
    private void ConfigureWorkflowApplication(WorkflowApplication wfApp)
    {
    }
    ```

    Bu yöntem, `WorkflowApplication` öğesini yapılandırır, istenen uzantıları ekler ve iş akışı yaşam döngüsü olayları için işleyiciler ekler.

2. İçinde, `ConfigureWorkflowApplication` için öğesini belirtin `SqlWorkflowInstanceStore` `WorkflowApplication` .

    ```vb
    ' Configure the persistence store.
    wfApp.InstanceStore = store
    ```

    ```csharp
    // Configure the persistence store.
    wfApp.InstanceStore = store;
    ```

3. Sonra bir örnek oluşturun `StringWriter` ve `Extensions` koleksiyonuna ekleyin `WorkflowApplication` . `StringWriter`Uzantılara eklendiğinde, tüm `WriteLine` etkinlik çıkışlarını yakalar. İş akışı boşta olduğunda, `WriteLine` Çıkış konumundan `StringWriter` ayıklanıp formda görüntülenebilir.

    ```vb
    ' Add a StringWriter to the extensions. This captures the output
    ' from the WriteLine activities so we can display it in the form.
    Dim sw As New StringWriter()
    wfApp.Extensions.Add(sw)
    ```

    ```csharp
    // Add a StringWriter to the extensions. This captures the output
    // from the WriteLine activities so we can display it in the form.
    var sw = new StringWriter();
    wfApp.Extensions.Add(sw);
    ```

4. Olay için aşağıdaki işleyiciyi ekleyin `Completed` . Bir iş akışı başarıyla tamamlandığında, sayıyı tahmin etmek için yapılan dönüşün sayısı durum penceresine görüntülenir. İş akışı sonlandığında, sonlandırmasına neden olan özel durum bilgileri görüntülenir. İşleyicinin sonunda `GameOver` yöntem çağrılır, bu, tamamlanan iş akışını iş akışı listesinden kaldırır.

    ```vb
    wfApp.Completed = _
        Sub(e As WorkflowApplicationCompletedEventArgs)
            If e.CompletionState = ActivityInstanceState.Faulted Then
                UpdateStatus($"Workflow Terminated. Exception: {e.TerminationException.GetType().FullName}{vbCrLf}{e.TerminationException.Message}")
            ElseIf e.CompletionState = ActivityInstanceState.Canceled Then
                UpdateStatus("Workflow Canceled.")
            Else
                Dim turns As Integer = Convert.ToInt32(e.Outputs("Turns"))
                UpdateStatus($"Congratulations, you guessed the number in {turns} turns.")
            End If
            GameOver()
        End Sub
    ```

    ```csharp
    wfApp.Completed = delegate(WorkflowApplicationCompletedEventArgs e)
    {
        if (e.CompletionState == ActivityInstanceState.Faulted)
        {
            UpdateStatus($"Workflow Terminated. Exception: {e.TerminationException.GetType().FullName}\r\n{e.TerminationException.Message}");
        }
        else if (e.CompletionState == ActivityInstanceState.Canceled)
        {
            UpdateStatus("Workflow Canceled.");
        }
        else
        {
            int turns = Convert.ToInt32(e.Outputs["Turns"]);
            UpdateStatus($"Congratulations, you guessed the number in {turns} turns.");
        }
        GameOver();
    };
    ```

5. Aşağıdakileri `Aborted` ve işleyicileri ekleyin `OnUnhandledException` . `GameOver`Yöntemi, `Aborted` bir iş akışı örneği iptal edildiğinde, Sonlanmadığı ve örneği daha sonra sürdürülmesi mümkün olduğu için işleyiciden çağrılmaz.

    ```vb
    wfApp.Aborted = _
        Sub(e As WorkflowApplicationAbortedEventArgs)
            UpdateStatus($"Workflow Aborted. Exception: {e.Reason.GetType().FullName}{vbCrLf}{e.Reason.Message}")
        End Sub

    wfApp.OnUnhandledException = _
        Function(e As WorkflowApplicationUnhandledExceptionEventArgs)
            UpdateStatus($"Unhandled Exception: {e.UnhandledException.GetType().FullName}{vbCrLf}{e.UnhandledException.Message}")
            GameOver()
            Return UnhandledExceptionAction.Terminate
        End Function
    ```

    ```csharp
    wfApp.Aborted = delegate(WorkflowApplicationAbortedEventArgs e)
    {
        UpdateStatus($"Workflow Aborted. Exception: {e.Reason.GetType().FullName}\r\n{e.Reason.Message}");
    };

    wfApp.OnUnhandledException = delegate(WorkflowApplicationUnhandledExceptionEventArgs e)
    {
        UpdateStatus($"Unhandled Exception: {e.UnhandledException.GetType().FullName}\r\n{e.UnhandledException.Message}");
        GameOver();
        return UnhandledExceptionAction.Terminate;
    };
    ```

6. Aşağıdaki işleyiciyi ekleyin `PersistableIdle` . Bu işleyici `StringWriter` eklenen uzantıyı alır, `WriteLine` etkinliklerdeki çıktıyı ayıklar ve durum penceresinde görüntüler.

    ```vb
    wfApp.PersistableIdle = _
        Function(e As WorkflowApplicationIdleEventArgs)
            ' Send the current WriteLine outputs to the status window.
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

    <xref:System.Activities.PersistableIdleAction>Numaralandırmada üç değer vardır: <xref:System.Activities.PersistableIdleAction.None> , <xref:System.Activities.PersistableIdleAction.Persist> , ve <xref:System.Activities.PersistableIdleAction.Unload> . <xref:System.Activities.PersistableIdleAction.Persist>iş akışının kalıcı olmasına neden olur, ancak iş akışının kaldırılmasına neden olmaz. <xref:System.Activities.PersistableIdleAction.Unload>iş akışının kalıcı ve kaldırılmış olmasına neden olur.

    Aşağıdaki örnek, tamamlanmış `ConfigureWorkflowApplication` yöntemidir.

    ```vb
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)
        ' Configure the persistence store.
        wfApp.InstanceStore = store

        ' Add a StringWriter to the extensions. This captures the output
        ' from the WriteLine activities so we can display it in the form.
        Dim sw As New StringWriter()
        wfApp.Extensions.Add(sw)

        wfApp.Completed = _
            Sub(e As WorkflowApplicationCompletedEventArgs)
                If e.CompletionState = ActivityInstanceState.Faulted Then
                    UpdateStatus($"Workflow Terminated. Exception: {e.TerminationException.GetType().FullName}{vbCrLf}{e.TerminationException.Message}")
                ElseIf e.CompletionState = ActivityInstanceState.Canceled Then
                    UpdateStatus("Workflow Canceled.")
                Else
                    Dim turns As Integer = Convert.ToInt32(e.Outputs("Turns"))
                    UpdateStatus($"Congratulations, you guessed the number in {turns} turns.")
                End If
                GameOver()
            End Sub

        wfApp.Aborted = _
            Sub(e As WorkflowApplicationAbortedEventArgs)
                UpdateStatus($"Workflow Aborted. Exception: {e.Reason.GetType().FullName}{vbCrLf}{e.Reason.Message}")
            End Sub

        wfApp.OnUnhandledException = _
            Function(e As WorkflowApplicationUnhandledExceptionEventArgs)
                UpdateStatus($"Unhandled Exception: {e.UnhandledException.GetType().FullName}{vbCrLf}{e.UnhandledException.Message}")
                GameOver()
                Return UnhandledExceptionAction.Terminate
            End Function

        wfApp.PersistableIdle = _
            Function(e As WorkflowApplicationIdleEventArgs)
                ' Send the current WriteLine outputs to the status window.
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
        var sw = new StringWriter();
        wfApp.Extensions.Add(sw);

        wfApp.Completed = delegate(WorkflowApplicationCompletedEventArgs e)
        {
            if (e.CompletionState == ActivityInstanceState.Faulted)
            {
                UpdateStatus($"Workflow Terminated. Exception: {e.TerminationException.GetType().FullName}\r\n{e.TerminationException.Message}");
            }
            else if (e.CompletionState == ActivityInstanceState.Canceled)
            {
                UpdateStatus("Workflow Canceled.");
            }
            else
            {
                int turns = Convert.ToInt32(e.Outputs["Turns"]);
                UpdateStatus($"Congratulations, you guessed the number in {turns} turns.");
            }
            GameOver();
        };

        wfApp.Aborted = delegate(WorkflowApplicationAbortedEventArgs e)
        {
            UpdateStatus($"Workflow Aborted. Exception: {e.Reason.GetType().FullName}\r\n{e.Reason.Message}");
        };

        wfApp.OnUnhandledException = delegate(WorkflowApplicationUnhandledExceptionEventArgs e)
        {
            UpdateStatus($"Unhandled Exception: {e.UnhandledException.GetType().FullName}\r\n{e.UnhandledException.Message}");
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

## <a name="to-enable-starting-and-resuming-multiple-workflow-types"></a>Birden çok iş akışı türünü başlatmayı ve sürdürmeyi etkinleştirmek için

Bir iş akışı örneğinin sürdürülmesi için, konağın iş akışı tanımını sağlaması gerekir. Bu öğreticide, üç iş akışı türü vardır ve sonraki öğretici adımları bu türlerin birden çok sürümünü ortaya çıkarabilir. `WorkflowIdentity`bir ana bilgisayar uygulamasının, tanımlayıcı bilgileri kalıcı bir iş akışı örneğiyle ilişkilendirmesi için bir yol sağlar. Bu bölümdeki adımlarda, kalıcı bir iş akışı örneğinden ilgili iş akışı tanımına iş akışı kimliğini eşleştirmeye yardımcı olması için bir yardımcı program sınıfının nasıl oluşturulacağı gösterilmektedir. Ve sürümü oluşturma hakkında daha fazla bilgi için `WorkflowIdentity` bkz. [Workflowwıdentity ve sürümü kullanma](using-workflowidentity-and-versioning.md).

1. **Çözüm Gezgini** Için **Numberguessworkflowwhost** öğesine sağ tıklayın ve **Ekle**, **sınıf**' i seçin. `WorkflowVersionMap` **Ad** kutusuna yazın ve **Ekle**' ye tıklayın.

2. Aşağıdaki veya deyimlerini `using` , `Imports` diğer `using` veya deyimleriyle dosyanın en üstüne ekleyin `Imports` .

    ```vb
    Imports System.Activities
    Imports NumberGuessWorkflowActivities
    ```

    ```csharp
    using System.Activities;
    using NumberGuessWorkflowActivities;
    ```

3. `WorkflowVersionMap`Sınıf bildirimini aşağıdaki bildirimle değiştirin.

    ```vb
    Public Module WorkflowVersionMap
        Dim map As Dictionary(Of WorkflowIdentity, Activity)

        ' Current version identities.
        Public StateMachineNumberGuessIdentity As WorkflowIdentity
        Public FlowchartNumberGuessIdentity As WorkflowIdentity
        Public SequentialNumberGuessIdentity As WorkflowIdentity

        Sub New()
            map = New Dictionary(Of WorkflowIdentity, Activity)

            ' Add the current workflow version identities.
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

    `WorkflowVersionMap`Bu öğreticideki üç iş akışı tanımına eşlenen üç iş akışı kimliği içerir ve iş akışları başlatıldığında ve sürdürüldüğünde aşağıdaki bölümlerde kullanılır.

## <a name="to-start-a-new-workflow"></a>Yeni bir iş akışı başlatmak için

1. İçin bir `Click` işleyici ekleyin `NewGame` . İşleyiciyi eklemek için form için **Tasarım görünümüne** geçin ve çift tıklayın `NewGame` . Bir `NewGame_Click` işleyici eklenir ve görünüm form için kod görünümüne geçer. Kullanıcı bu düğmeye her tıkladığında yeni bir iş akışı başlatılır.

    ```vb
    Private Sub NewGame_Click(sender As Object, e As EventArgs) Handles NewGame.Click

    End Sub
    ```

    ```csharp
    private void NewGame_Click(object sender, EventArgs e)
    {

    }
    ```

2. Aşağıdaki kodu tıklama işleyicisine ekleyin. Bu kod, iş akışı için bağımsız değişken adına göre anahtarlı bir giriş bağımsız değişkenlerinin sözlüğünü oluşturur. Bu sözlükte, Aralık Birleşik giriş kutusundan alınan rastgele oluşturulan sayı aralığını içeren bir giriş vardır.

    ```vb
    Dim inputs As New Dictionary(Of String, Object)()
    inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem))
    ```

    ```csharp
    var inputs = new Dictionary<string, object>();
    inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem));
    ```

3. Sonra, iş akışını başlatan aşağıdaki kodu ekleyin. `WorkflowIdentity`Seçilen iş akışı türüne karşılık gelen ve iş akışı tanımı `WorkflowVersionMap` yardımcı sınıfı kullanılarak alınır. Ardından, `WorkflowApplication` iş akışı tanımı, `WorkflowIdentity` ve giriş bağımsız değişkenlerinin sözlüğü kullanılarak yeni bir örnek oluşturulur.

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

4. Sonra, iş akışını iş akışı listesine ekleyen aşağıdaki kodu ekleyin ve iş akışının sürüm bilgilerini formda görüntüler.

    ```vb
    ' Add the workflow to the list and display the version information.
    workflowStarting = True
    InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id)
    WorkflowVersion.Text = identity.ToString()
    workflowStarting = False
    ```

    ```csharp
    // Add the workflow to the list and display the version information.
    workflowStarting = true;
    InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id);
    WorkflowVersion.Text = identity.ToString();
    workflowStarting = false;
    ```

5. `ConfigureWorkflowApplication`Örnek deposunu, uzantıları ve bu örnek için iş akışı yaşam döngüsü işleyicilerini yapılandırma çağrısı `WorkflowApplication` .

    ```vb
    ' Configure the instance store, extensions, and
    ' workflow lifecycle handlers.
    ConfigureWorkflowApplication(wfApp)
    ```

    ```csharp
    // Configure the instance store, extensions, and
    // workflow lifecycle handlers.
    ConfigureWorkflowApplication(wfApp);
    ```

6. Son olarak, çağırın `Run` .

    ```vb
    ' Start the workflow.
    wfApp.Run()
    ```

    ```csharp
    // Start the workflow.
    wfApp.Run();
    ```

     Aşağıdaki örnek, tamamlanan `NewGame_Click` işleyicidir.

    ```vb
    Private Sub NewGame_Click(sender As Object, e As EventArgs) Handles NewGame.Click
        ' Start a new workflow.
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

        ' Add the workflow to the list and display the version information.
        workflowStarting = True
        InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id)
        WorkflowVersion.Text = identity.ToString()
        workflowStarting = False

        ' Configure the instance store, extensions, and
        ' workflow lifecycle handlers.
        ConfigureWorkflowApplication(wfApp)

        ' Start the workflow.
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

        var wfApp = new WorkflowApplication(wf, inputs, identity);

        // Add the workflow to the list and display the version information.
        workflowStarting = true;
        InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id);
        WorkflowVersion.Text = identity.ToString();
        workflowStarting = false;

        // Configure the instance store, extensions, and
        // workflow lifecycle handlers.
        ConfigureWorkflowApplication(wfApp);

        // Start the workflow.
        wfApp.Run();
    }
    ```

## <a name="to-resume-a-workflow"></a>Bir iş akışını sürdürmesini sağlamak için

1. İçin bir `Click` işleyici ekleyin `EnterGuess` . İşleyiciyi eklemek için form için **Tasarım görünümüne** geçin ve çift tıklayın `EnterGuess` . Kullanıcı bu düğmeye tıkladığında bir iş akışı sürdürülür.

    ```vb
    Private Sub EnterGuess_Click(sender As Object, e As EventArgs) Handles EnterGuess.Click

    End Sub
    ```

    ```csharp
    private void EnterGuess_Click(object sender, EventArgs e)
    {

    }
    ```

2. İş akışı listesinde bir iş akışının seçildiğinden ve kullanıcının tahminin geçerli olduğundan emin olmak için aşağıdaki kodu ekleyin.

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

3. Sonra, `WorkflowApplicationInstance` kalıcı iş akışı örneğini alın. Bir `WorkflowApplicationInstance` iş akışı tanımıyla henüz ilişkilendirilmemiş kalıcı bir iş akışı örneğini temsil eder. `DefinitionIdentity`Öğesinin, `WorkflowApplicationInstance` `WorkflowIdentity` kalıcı iş akışı örneğinin içerir. Bu öğreticide `WorkflowVersionMap` yardımcı program sınıfı, `WorkflowIdentity` doğru iş akışı tanımıyla eşlemek için kullanılır. İş akışı tanımı alındıktan sonra, `WorkflowApplication` doğru iş akışı tanımı kullanılarak oluşturulur.

    ```vb
    Dim instance As WorkflowApplicationInstance = _
        WorkflowApplication.GetInstance(WorkflowInstanceId, store)

    ' Use the persisted WorkflowIdentity to retrieve the correct workflow
    ' definition from the dictionary.
    Dim wf As Activity = _
        WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity)

    ' Associate the WorkflowApplication with the correct definition
    Dim wfApp As New WorkflowApplication(wf, instance.DefinitionIdentity)
    ```

    ```csharp
    WorkflowApplicationInstance instance =
        WorkflowApplication.GetInstance(WorkflowInstanceId, store);

    // Use the persisted WorkflowIdentity to retrieve the correct workflow
    // definition from the dictionary.
    Activity wf =
        WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity);

    // Associate the WorkflowApplication with the correct definition
    var wfApp = new WorkflowApplication(wf, instance.DefinitionIdentity);
    ```

4. Oluşturulduktan sonra `WorkflowApplication` , çağırarak örnek deposunu, iş akışı yaşam döngüsü işleyicilerini ve Uzantıları yapılandırın `ConfigureWorkflowApplication` . Bu adımların her yeni `WorkflowApplication` oluşturulduğunda yapılması ve iş akışı örneği içine yüklenmeden önce yapılması gerekir `WorkflowApplication` . İş akışı yüklendikten sonra kullanıcının tahminiyle devam edilir.

    ```vb
    ' Configure the extensions and lifecycle handlers.
    ' Do this before the instance is loaded. Once the instance is
    ' loaded it is too late to add extensions.
    ConfigureWorkflowApplication(wfApp)

    ' Load the workflow.
    wfApp.Load(instance)

    ' Resume the workflow.
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

5. Son olarak, tahmin metin kutusunu temizleyip formu başka bir tahmin kabul edecek şekilde hazırlayın.

    ```vb
    ' Clear the Guess textbox.
    Guess.Clear()
    Guess.Focus()
    ```

    ```csharp
    // Clear the Guess textbox.
    Guess.Clear();
    Guess.Focus();
    ```

    Aşağıdaki örnek, tamamlanan `EnterGuess_Click` işleyicidir.

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

        ' Use the persisted WorkflowIdentity to retrieve the correct workflow
        ' definition from the dictionary.
        Dim wf As Activity = _
            WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity)

        ' Associate the WorkflowApplication with the correct definition
        Dim wfApp As New WorkflowApplication(wf, instance.DefinitionIdentity)

        ' Configure the extensions and lifecycle handlers.
        ' Do this before the instance is loaded. Once the instance is
        ' loaded it is too late to add extensions.
        ConfigureWorkflowApplication(wfApp)

        ' Load the workflow.
        wfApp.Load(instance)

        ' Resume the workflow.
        wfApp.ResumeBookmark("EnterGuess", userGuess)

        ' Clear the Guess textbox.
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
        var wfApp = new WorkflowApplication(wf, instance.DefinitionIdentity);

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

## <a name="to-terminate-a-workflow"></a>Bir iş akışını sonlandırmak için

1. İçin bir `Click` işleyici ekleyin `QuitGame` . İşleyiciyi eklemek için form için **Tasarım görünümüne** geçin ve çift tıklayın `QuitGame` . Kullanıcı bu düğmeye tıkladığında Şu anda seçili olan iş akışı sonlandırılır.

    ```vb
    Private Sub QuitGame_Click(sender As Object, e As EventArgs) Handles QuitGame.Click

    End Sub
    ```

    ```csharp
    private void QuitGame_Click(object sender, EventArgs e)
    {

    }
    ```

2. Aşağıdaki kodu `QuitGame_Click` işleyiciye ekleyin. Bu kod ilk olarak iş akışı listesinde bir iş akışının seçili olduğundan emin olmak için kontrol eder. Ardından kalıcı örneği öğesine yükler `WorkflowApplicationInstance` , `DefinitionIdentity` doğru iş akışı tanımını anlamak için öğesini kullanır ve sonra öğesini başlatır `WorkflowApplication` . Sonraki Uzantılar ve iş akışı yaşam döngüsü işleyicileri bir çağrısıyla yapılandırılır `ConfigureWorkflowApplication` . Yapılandırıldıktan sonra, `WorkflowApplication` yüklenir ve ardından `Terminate` çağırılır.

    ```vb
    If WorkflowInstanceId = Guid.Empty Then
        MessageBox.Show("Please select a workflow.")
        Return
    End If

    Dim instance As WorkflowApplicationInstance = _
        WorkflowApplication.GetInstance(WorkflowInstanceId, store)

    ' Use the persisted WorkflowIdentity to retrieve the correct workflow
    ' definition from the dictionary.
    Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity)

    ' Associate the WorkflowApplication with the correct definition.
    Dim wfApp As New WorkflowApplication(wf, instance.DefinitionIdentity)

    ' Configure the extensions and lifecycle handlers.
    ConfigureWorkflowApplication(wfApp)

    ' Load the workflow.
    wfApp.Load(instance)

    ' Terminate the workflow.
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
    var wfApp = new WorkflowApplication(wf, instance.DefinitionIdentity);

    // Configure the extensions and lifecycle handlers
    ConfigureWorkflowApplication(wfApp);

    // Load the workflow.
    wfApp.Load(instance);

    // Terminate the workflow.
    wfApp.Terminate("User resigns.");
    ```

## <a name="to-build-and-run-the-application"></a>Uygulamayı derlemek ve çalıştırmak için

1. Kodu göstermek için **Çözüm Gezgini** içindeki **program.cs** (veya **Module1. vb**) öğesine çift tıklayın.

2. Aşağıdaki `using` (veya `Imports` ) deyimini, diğer `using` (veya `Imports` ) deyimleriyle dosyanın en üstüne ekleyin.

    ```vb
    Imports System.Windows.Forms
    ```

    ```csharp
    using System.Windows.Forms;
    ```

3. [Nasıl yapılır: Iş akışı çalıştırma](how-to-run-a-workflow.md)ve aşağıdaki kodla değiştirme gibi mevcut iş akışı barındırma kodunu kaldırın

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

4. **Çözüm Gezgini** Için **Numberguessworkflowwhost** öğesine sağ tıklayın ve **Özellikler**' i seçin. **Uygulama** sekmesinde, **Çıkış türü**için **Windows uygulaması** ' nı belirtin. Bu adım isteğe bağlıdır, ancak bu değer izlenmezse, forma ek olarak konsol penceresi görüntülenir.

5. Uygulamayı derlemek için CTRL + SHIFT + B tuşlarına basın.

6. **Numberguessworkflowwhost** ' nin başlangıç uygulaması olarak ayarlandığından emin olun ve uygulamayı başlatmak için CTRL + F5 tuşlarına basın.

7. Tahmin etme oyunu ve başlatılacak iş akışı türü için bir Aralık seçin ve **yeni oyun**' e tıklayın. **Tahmin kutusuna bir** tahmin girin ve tahmininizi göndermek için **Git** ' e tıklayın. `WriteLine`Etkinliklerdeki çıktının formda görüntülendiğini unutmayın.

8. Farklı iş akışı türleri ve sayı aralıkları kullanarak birkaç iş akışı başlatın, bazı tahminler girin ve **Iş akışı örneği kimliği** listesinden seçim yaparak iş akışları arasında geçiş yapın.

    Yeni bir iş akışına geçtiğinizde, iş akışının önceki tahminlerini ve ilerleme durumu durum penceresinde görüntülenmediğini unutmayın. Durumun, yakalanmadığı ve her yerde kaydedilmediği için durum kullanılamaz. Öğreticinin bir sonraki adımında, [nasıl yapılır: özel bir Izleme katılımcısı oluşturma](how-to-create-a-custom-tracking-participant.md), bu bilgileri kaydeden özel bir izleme katılımcısı oluşturursunuz.
