---
title: 'Nasıl yapılır: Özel İzleme Katılımcısı Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b612c7e-2381-4a7c-b07a-77030415f2a3
ms.openlocfilehash: ea7a598a73f131d8ee33e285a39173fbf84a97f5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182904"
---
# <a name="how-to-create-a-custom-tracking-participant"></a>Nasıl yapılır: Özel İzleme Katılımcısı Oluşturma
İş akışı izleme, iş akışı yürütme durumuna görünürlük sağlar. İş akışı çalışma zamanı, iş akışı yaşam döngüsü olaylarını, etkinlik yaşam döngüsü olaylarını, yer imi yeniden başlamalarını ve hataları açıklayan izleme kayıtlarını yayar. Bu izleme kayıtları, izleme katılımcıları tarafından tüketilir. Windows İş Akışı Temeli (WF), Windows için Olay İzleme (ETW) olayları olarak izleme kayıtları yazan standart bir izleme katılımcısı içerir. Bu gereksinimlerinizi karşılamazsa, özel bir izleme katılımcısı da yazabilirsiniz. Bu öğretici adım, kullanıcıya görüntülenebilecek etkinliklerin çıktısını `WriteLine` yakalayan özel bir izleme katılımcısı ve izleme profilinin nasıl oluşturulabileceğini açıklar.  
  
> [!NOTE]
> Başlarken öğreticideki her konu önceki konulara bağlıdır. Bu konuyu tamamlamak için önce önceki konuları tamamlamanız gerekir. Tamamlanmış bir sürümü indirmek veya öğreticinin video walkthrough'ını görüntülemek için [Windows İş Akışı Vakfı 'na (WF45) bakın - Eğitime Başlarken.](https://go.microsoft.com/fwlink/?LinkID=248976)  
  
## <a name="to-create-the-custom-tracking-participant"></a>Özel izleme katılımcısı oluşturmak için  
  
1. **Solution Explorer'da** **NumberGuessWorkflowHost'a** sağ tıklayın ve **Ekle**, **Sınıf**seçin. `StatusTrackingParticipant` **Ad** kutusuna yazın ve **Ekle'yi**tıklatın.  
  
2. Dosyanın `using` üst `Imports`kısmındaki diğer `using` (veya ) deyimleriyle `Imports`birlikte aşağıdaki (veya) ifadeleri ekleyin.  
  
    ```vb  
    Imports System.Activities.Tracking  
    Imports System.IO  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    using System.IO;  
    ```  
  
3. `StatusTrackingParticipant` Sınıfı, 'den `TrackingParticipant`devralan olacak şekilde değiştirin.  
  
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
  
4. Aşağıdaki `Track` yöntem geçersiz kılma ekleyin. Birkaç farklı izleme kaydı türü vardır. Faaliyet izleme kayıtlarında `WriteLine` yer alan faaliyetlerin çıktısı ile ilgileniyoruz. `TrackingRecord` `ActivityTrackingRecord` Bir `WriteLine` etkinlik için ise, `Text` `WriteLine` iş akışının adını `InstanceId` taşıyan bir dosyaya eklenir. Bu öğreticide, dosya ana bilgisayar uygulamasının geçerli klasörüne kaydedilir.  
  
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
  
     Hiçbir izleme profili belirtilmediğinde, varsayılan izleme profili kullanılır. Varsayılan izleme profili kullanıldığında, izleme kayıtları herkes `ActivityStates`için yayılır. Etkinliğin yaşam döngüsü boyunca metni yalnızca bir kez `WriteLine` yakalamamız gerektiğinden, metni `ActivityStates.Executing` yalnızca devletten ayıklarız. [İzleme profilini oluşturmak ve izleme katılımcısını kaydetmek](#to-create-the-tracking-profile-and-register-the-tracking-participant)için, yalnızca `WriteLine` `ActivityStates.Executing` izleme kayıtlarının yayıldığını belirten bir izleme profili oluşturulur.  
  
## <a name="to-create-the-tracking-profile-and-register-the-tracking-participant"></a>İzleme profilini oluşturmak ve izleme katılımcısını kaydetmek için  
  
1. **Solution Explorer'da** **İş AkışıHostForm'a** sağ tıklayın ve **Kodu Görüntüle'yi**seçin.  
  
2. Aşağıdaki `using` `Imports`(veya ) deyimini dosyanın üst kısmındaki diğer `using` (veya) `Imports`deyimleriyle birlikte ekleyin.  
  
    ```vb  
    Imports System.Activities.Tracking  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    ```  
  
3. İş akışı uzantılarına ekleyen `ConfigureWorkflowApplication` `StringWriter` koddan hemen sonraya ve iş akışı yaşam döngüsü işleyicilerinden önce aşağıdaki kodu ekleyin.  
  
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
  
     Bu izleme profili, yalnızca eyaletteki `WriteLine` etkinliklere `Executing` ait etkinlik durumu kayıtlarının özel izleme katılımcısına yayDığını belirtir.  
  
     Kodu ekledikten sonra, `ConfigureWorkflowApplication` başlangıç aşağıdaki örnek gibi görünecektir.  
  
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
  
1. **Solution Explorer'da** **İş AkışıHostForm'a** sağ tıklayın ve **Kodu Görüntüle'yi**seçin.  
  
2. İşleyicide, `InstanceId_SelectedIndexChanged` durum penceresini temizleyen koddan hemen sonra aşağıdaki kodu ekleyin.  
  
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
  
     İş akışı listesinde yeni bir iş akışı seçildiğinde, bu iş akışına ait izleme kayıtları yüklenir ve durum penceresinde görüntülenir. Aşağıdaki örnek tamamlanmış `InstanceId_SelectedIndexChanged` işleyicidir.  
  
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
  
## <a name="to-build-and-run-the-application"></a>Uygulamayı oluşturmak ve çalıştırmak için  
  
1. Uygulamayı oluşturmak için Ctrl+Shift+B tuşuna basın.  
  
2. Uygulamayı başlatmak için Ctrl+F5 tuşuna basın.  
  
3. Tahmin oyunu ve başlamak için iş akışı türü için bir aralık seçin ve **Yeni Oyun'u**tıklatın. **Tahmin** kutusuna bir tahmin girin ve tahmininizi göndermek için **Git'i** tıklatın. İş akışının durumunun durum penceresinde görüntülendiğini unutmayın. Bu çıktı `WriteLine` etkinliklerden yakalanır. **İş Akışı Örneği Id** açılan kutusundan birini seçerek farklı bir iş akışına geçin ve geçerli iş akışının durumunun kaldırıldığını unutmayın. Önceki iş akışına geri dön ve aşağıdaki örneğe benzer şekilde durumun geri yüklenmiş olduğunu unutmayın.  
  
    > [!NOTE]
    > İzleme etkinleştirilmeden önce başlatılan bir iş akışına geçerseniz hiçbir durum görüntülenmez. Ancak ek tahminleryaparsanız, izleme artık etkinleştirildiğinden durumları kaydedilir.  
  
    ```output
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    ```

    > [!NOTE]
    > Bu bilgiler rasgele sayının aralığını belirlemek için yararlıdır, ancak daha önce hangi tahminlerin yapıldığı hakkında herhangi bir bilgi içermez. Bu bilgiler bir sonraki adımda, [Nasıl yapılır: İş Akışının Birden Çok Sürümü Yan Yana.](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)

    İş akışı örneği id'ini not edin ve oyunu tamamlanmasına kadar oynayın.
  
4. Windows Gezgini'ni açın ve **NumberGuessWorkflowHost\bin\debug** klasörüne gidin (veya proje ayarlarınıza bağlı olarak **bin\release).** Proje yürütülebilir dosyalara ek olarak kılavuz dosya adlarına sahip dosyalar olduğunu unutmayın. Önceki adımda tamamlanan iş akışı kimliğinden iş akışı örneği kimliğine karşılık geleni belirleyin ve Not Defteri'nde açın. İzleme bilgileri aşağıdakine benzer bilgiler içerir.  
  
    ```output
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    ```

    Kullanıcının tahminlerinin olmamasına ek olarak, bu izleme verileri iş akışının son tahmini hakkında bilgi içermez. Bunun nedeni, izleme bilgilerinin `WriteLine` yalnızca iş akışından çıkan çıktıdan oluşması ve görüntülenen `Completed` son iletinin iş akışı tamamlandıktan sonra işleyiciden yapılmasıdır. Öğreticinin bir sonraki adımında, [Nasıl Yapılır: İş Akışının Birden Çok](how-to-host-multiple-versions-of-a-workflow-side-by-side.md) `WriteLine` Sürümü Yan Yana, varolan etkinlikler kullanıcının `WriteLine` tahminlerini görüntülemek üzere değiştirilir ve nihai sonuçları görüntüleyen ek bir etkinlik eklenir. Bu değişiklikler tümleşik olduktan sonra, [Nasıl Yapılır: İş Akışının Birden Çok Sürümü Yan Yana](how-to-host-multiple-versions-of-a-workflow-side-by-side.md) Nasıl Barındırılır, aynı anda bir iş akışının birden çok sürümü nasıl barındırılabildiğini gösterir.
