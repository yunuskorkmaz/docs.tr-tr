---
title: 'Nasıl yapılır: Özel İzleme Katılımcısı Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b612c7e-2381-4a7c-b07a-77030415f2a3
ms.openlocfilehash: 64320a8f4799e79f54348e5381ed2d8ed49d496b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59338182"
---
# <a name="how-to-create-a-custom-tracking-participant"></a>Nasıl yapılır: Özel İzleme Katılımcısı Oluşturma
İş akışı izleme, iş akışı yürütme durumunu görünürlük sağlar. İş akışı çalışma zamanı iş akışı yaşam döngüsü olayları, etkinlik yaşam döngüsü olayları, yer işareti harcanması ve hataları tanımlayan izleme kayıtları gösterir. Bu izleme kayıtları izleme katılımcıları tarafından tüketilir. Windows Workflow Foundation (WF) izleme kayıtları için olay izleme Windows (ETW) olayları olarak yazan standart izleme katılımcı içerir. Gereksinimlerinizi karşılamıyorsa, özel izleme katılımcı de yazabilirsiniz. Bu öğretici adım özel izleme katılımcı ve çıktısını yakalamak izleme profili oluşturmayı açıklar `WriteLine` etkinlikleri ve böylece kullanıcıya gösterilir.  
  
> [!NOTE]
>  Önceki konularıyla ilgili her konuda Başlarken Öğreticisi bağlıdır. Bu konuyu tamamlamak için önceki konu tamamlamanız gerekir. Tamamlanmış bir sürümünü indirin veya videosu öğreticinin görüntülemek için bkz: [Windows Workflow Foundation (WF45) - başlangıç Öğreticisi](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
## <a name="to-create-the-custom-tracking-participant"></a>Özel İzleme Katılımcısı oluşturma  
  
1. Sağ **NumberGuessWorkflowHost** içinde **Çözüm Gezgini** ve **Ekle**, **sınıfı**. Tür `StatusTrackingParticipant` içine **adı** ve'ı tıklatın **Ekle**.  
  
2. Aşağıdaki `using` (veya `Imports`) deyimini dosyanın diğer üst `using` (veya `Imports`) ifadeleri.  
  
    ```vb  
    Imports System.Activities.Tracking  
    Imports System.IO  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    using System.IO;  
    ```  
  
3. Değiştirme `StatusTrackingParticipant` devraldığı sınıfının `TrackingParticipant`.  
  
    ```vb  
    Public Class StatusTrackingParticipant  
        Inherits TrackingParticipant  
  
    End Class  
    ```  
  
    ```csharp  
    class StatusTrackingParticipant : TrackingParticipant  
    {  
    }  
    ```  
  
4. Aşağıdaki `Track` yöntemi geçersiz kılma. Kayıtları İzleme birkaç farklı türleri vardır. Biz çıktısında ilgilendiğiniz `WriteLine` kayıtları izleme etkinliğinde bulunan etkinlikler. Varsa `TrackingRecord` olduğu bir `ActivityTrackingRecord` için bir `WriteLine` etkinliği `Text` , `WriteLine` sonra adlı bir dosyaya eklenir `InstanceId` iş akışı. Bu öğreticide, dosyanın ana uygulama geçerli klasöre kaydedilir.  
  
    ```vb  
    Protected Overrides Sub Track(record As TrackingRecord, timeout As TimeSpan)  
        Dim asr As ActivityStateRecord = TryCast(record, ActivityStateRecord)  
  
        If Not asr Is Nothing Then  
            If asr.State = ActivityStates.Executing And _  
            asr.Activity.TypeName = "System.Activities.Statements.WriteLine" Then  
  
                'Append the WriteLine output to the tracking  
                'file for this instance.  
                Using writer As StreamWriter = File.AppendText(record.InstanceId.ToString())  
                    writer.WriteLine(asr.Arguments("Text"))  
                    writer.Close()  
                End Using  
            End If  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    protected override void Track(TrackingRecord record, TimeSpan timeout)  
    {  
        ActivityStateRecord asr = record as ActivityStateRecord;  
  
        if (asr != null)  
        {  
            if (asr.State == ActivityStates.Executing &&  
                asr.Activity.TypeName == "System.Activities.Statements.WriteLine")  
            {  
                // Append the WriteLine output to the tracking  
                // file for this instance  
                using (StreamWriter writer = File.AppendText(record.InstanceId.ToString()))  
                {  
                    writer.WriteLine(asr.Arguments["Text"]);  
                    writer.Close();  
                }  
            }  
        }  
    }  
    ```  
  
     Varsayılan profil izleme, izleme profil belirtildiğinde kullanılır. Varsayılan profil izleme kullanıldığında, izleme kayıtları tüm yayılan `ActivityStates`. Biz yalnızca bir kez yaşam döngüsü sırasında metin yakalamak gerektiğinden `WriteLine` etkinlik, biz yalnızca Ayıkla metinden `ActivityStates.Executing` durumu. İçinde [izleme profili oluşturma ve izleme Katılımcısı kaydetmek için](#to-create-the-tracking-profile-and-register-the-tracking-participant), yalnızca belirten bir izleme profili oluşturulan `WriteLine` `ActivityStates.Executing` izleme kayıtları yayılan.  
  
## <a name="to-create-the-tracking-profile-and-register-the-tracking-participant"></a>İzleme profili oluşturma ve izleme Katılımcısı kaydetmek için  
  
1. Sağ **WorkflowHostForm** içinde **Çözüm Gezgini** ve **kodu görüntüle**.  
  
2. Aşağıdaki `using` (veya `Imports`) deyimini dosyanın diğer üst `using` (veya `Imports`) ifadeleri.  
  
    ```vb  
    Imports System.Activities.Tracking  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    ```  
  
3. Aşağıdaki kodu ekleyin `ConfigureWorkflowApplication` ekleyen koddan sonra `StringWriter` iş akışı uzantıları ve iş akışı yaşam döngüsü işleyicileri önce.  
  
    ```vb  
    'Add the custom tracking participant with a tracking profile  
    'that only emits tracking records for WriteLine activities.  
    Dim query As New ActivityStateQuery()  
    query.ActivityName = "WriteLine"  
    query.States.Add(ActivityStates.Executing)  
    query.Arguments.Add("Text")  
  
    Dim profile As New TrackingProfile()  
    profile.Queries.Add(query)  
  
    Dim stp As New StatusTrackingParticipant()  
    stp.TrackingProfile = profile  
  
    wfApp.Extensions.Add(stp)  
    ```  
  
    ```csharp  
    // Add the custom tracking participant with a tracking profile  
    // that only emits tracking records for WriteLine activities.  
    StatusTrackingParticipant stp = new StatusTrackingParticipant  
    {  
        TrackingProfile = new TrackingProfile  
        {  
            Queries =   
            {  
                new ActivityStateQuery  
                {  
                    ActivityName = "WriteLine",  
                    States = { ActivityStates.Executing },  
                    Arguments = { "Text" }  
                }  
            }  
        }  
    };  
  
    wfApp.Extensions.Add(stp);  
    ```  
  
     Bu izleme profili için yalnızca bir etkinlik durumu kayıt belirtir `WriteLine` etkinlikler `Executing` durum için özel izleme katılımcı yayılır.  
  
     Başlangıç kodu ekledikten sonra `ConfigureWorkflowApplication` aşağıdaki örnekteki gibi görünecektir.  
  
    ```vb  
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)  
        'Configure the persistence store.  
        wfApp.InstanceStore = store  
  
        'Add a StringWriter to the extensions. This captures the output  
        'from the WriteLine activities so we can display it in the form.  
        Dim sw As New StringWriter()  
        wfApp.Extensions.Add(sw)  
  
        'Add the custom tracking participant with a tracking profile  
        'that only emits tracking records for WriteLine activities.  
        Dim query As New ActivityStateQuery()  
        query.ActivityName = "WriteLine"  
        query.States.Add(ActivityStates.Executing)  
        query.Arguments.Add("Text")  
  
        Dim profile As New TrackingProfile()  
        profile.Queries.Add(query)  
  
        Dim stp As New StatusTrackingParticipant()  
        stp.TrackingProfile = profile  
  
        wfApp.Extensions.Add(stp)  
  
        'Workflow lifecycle handlers...  
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
  
        // Add the custom tracking participant with a tracking profile  
        // that only emits tracking records for WriteLine activities.  
        StatusTrackingParticipant stp = new StatusTrackingParticipant  
        {  
            TrackingProfile = new TrackingProfile  
            {  
                Queries =   
                {  
                    new ActivityStateQuery  
                    {  
                        ActivityName = "WriteLine",  
                        States = { ActivityStates.Executing },  
                        Arguments = { "Text" }  
                    }  
                }  
            }  
        };  
  
        wfApp.Extensions.Add(stp);  
  
        // Workflow lifecycle handlers...  
    ```  
  
## <a name="to-display-the-tracking-information"></a>İzleme bilgilerini görüntülemek için  
  
1. Sağ **WorkflowHostForm** içinde **Çözüm Gezgini** ve **kodu görüntüle**.  
  
2. İçinde `InstanceId_SelectedIndexChanged` işleyicisi hemen durum penceresi temizler koddan sonra aşağıdaki kodu ekleyin.  
  
    ```vb  
    'If there is tracking data for this workflow, display it  
    'in the status window.  
    If File.Exists(WorkflowInstanceId.ToString()) Then  
        Dim status As String = File.ReadAllText(WorkflowInstanceId.ToString())  
        UpdateStatus(status)  
    End If  
    ```  
  
    ```csharp  
    // If there is tracking data for this workflow, display it  
    // in the status window.  
    if (File.Exists(WorkflowInstanceId.ToString()))  
    {  
        string status = File.ReadAllText(WorkflowInstanceId.ToString());  
        UpdateStatus(status);  
    }  
    ```  
  
     Yeni bir iş akışı iş akışı listesinde seçildiğinde, izleme kayıtları için iş akışının yüklenir ve durum penceresinde görüntülenir. Aşağıdaki örnek, tamamlanan, `InstanceId_SelectedIndexChanged` işleyici.  
  
    ```vb  
    Private Sub InstanceId_SelectedIndexChanged(sender As Object, e As EventArgs) Handles InstanceId.SelectedIndexChanged  
        If InstanceId.SelectedIndex = -1 Then  
            Return  
        End If  
  
        'Clear the status window.  
        WorkflowStatus.Clear()  
  
        'If there is tracking data for this workflow, display it  
        'in the status window.  
        If File.Exists(WorkflowInstanceId.ToString()) Then  
            Dim status As String = File.ReadAllText(WorkflowInstanceId.ToString())  
            UpdateStatus(status)  
        End If  
  
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
    End Sub  
    ```  
  
    ```csharp  
    private void InstanceId_SelectedIndexChanged(object sender, EventArgs e)  
    {  
        if (InstanceId.SelectedIndex == -1)  
        {  
            return;  
        }  
  
        // Clear the status window.  
        WorkflowStatus.Clear();  
  
        // If there is tracking data for this workflow, display it  
        // in the status window.  
        if (File.Exists(WorkflowInstanceId.ToString()))  
        {  
            string status = File.ReadAllText(WorkflowInstanceId.ToString());  
            UpdateStatus(status);  
        }  
  
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
    }  
    ```  
  
## <a name="to-build-and-run-the-application"></a>Derleme ve uygulamayı çalıştırmak için  
  
1. Uygulamayı oluşturmak için Ctrl + Shift + B tuşlarına basın.  
  
2. Uygulamayı başlatmak için CTRL + F5 tuşlarına basın.  
  
3. Tahmin eden oyun ve başlangıç ve iş akışı türü için bir aralık seçmek **yeni oyun**. İçinde bir tahmin girin **tahmin** kutusuna ve tıklatın **Git** , tahmin göndermek için. İş akışı durumu durum penceresinde görüntülendiğine dikkat edin. Bu çıkış yakalanmıştır `WriteLine` etkinlikler. Geçiş için farklı bir iş akışı birini seçerek **iş akışı örnek kimliğini** birleşik giriş kutusu ve geçerli iş akışı durumunu kaldırıldığını unutmayın. Önceki iş akışını ve durum, aşağıdaki örneğe benzer şekilde geri yüklendiğini Not dönün.  
  
    > [!NOTE]
    > İzleme etkinleştirilmeden önce başlatıldığından bir iş akışına geçiş yaparsanız yok durumu görüntülenir. Ancak ek tahmin yaparsanız, izleme artık etkin olmadığından durumlarını kaydedilir.  
  
    ```output
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    ```
    
    > [!NOTE]
    > Bu bilgiler, rastgele sayı aralığı belirlemek için yararlıdır, ancak daha önce yapılmış hangi tahmin hakkında bilgi içermiyor. Bu bilgiler sonraki adımda olan [nasıl yapılır: Bir iş akışı yan yana birden çok sürümünü konak](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).

    İş akışı örnek kimliğini not edin ve kendi tamamlanana kadar oyun.
  
4. Windows Gezgini'ni açın ve gidin **NumberGuessWorkflowHost\bin\debug** klasörü (veya **bin\release** proje ayarlarınıza bağlı olarak). Ek olarak proje dosyaları GUID adlarıyla yürütülebilir dosyalar olduğunu unutmayın. Önceki adımda tamamlanan iş akışı'ndan iş akışı örneği kimliğine karşılık gelen bir belirleyin ve Not Defteri'nde açın. İzleme bilgileri aşağıdaki gibi bilgileri içerir.  
  
    ```output
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    ```

    Kullanıcının tahmin olmaması ek olarak, bu izleme verileri, iş akışının son tahmin hakkında bilgi içermiyor. İzleme bilgileri yalnızca oluşan çünkü `WriteLine` iş akışından çıkış ve görüntülenen son iletide nden yapılır `Completed` iş akışı tamamlandıktan sonra işleyici. Öğreticinin sonraki adımda [nasıl yapılır: Ana bilgisayar, bir iş akışı yan yana birden çok sürümünü](how-to-host-multiple-versions-of-a-workflow-side-by-side.md), varolan `WriteLine` etkinlikleri, kullanıcının tahminler ve ek görüntülenecek değiştirildiğinde `WriteLine` etkinliği, son sonuçları görüntüler eklenir. Bu değişiklikler tümleştirildikten sonra [nasıl yapılır: Ana bilgisayar, bir iş akışı yan yana birden çok sürümünü](how-to-host-multiple-versions-of-a-workflow-side-by-side.md) aynı anda birden çok iş akışı sürümünü barındırmak nasıl gösterir.
