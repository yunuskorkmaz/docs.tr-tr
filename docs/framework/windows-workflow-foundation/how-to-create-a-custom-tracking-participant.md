---
title: 'Nasıl yapılır: Özel İzleme Katılımcısı Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b612c7e-2381-4a7c-b07a-77030415f2a3
ms.openlocfilehash: 280f68c8b762562a56ce96f45f118702fb0e4d76
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962407"
---
# <a name="how-to-create-a-custom-tracking-participant"></a>Nasıl yapılır: Özel İzleme Katılımcısı Oluşturma
İş akışı izleme, iş akışı yürütme durumunun görünürlüğünü sağlar. İş akışı çalışma zamanı, iş akışı yaşam döngüsü olaylarını, etkinlik yaşam döngüsü olaylarını, yer işareti bağlantının sürdürülmesi ve hataları tanımlayan kayıt kayıtlarını yayar. Bu izleme kayıtları, katılımcıları izleme tarafından kullanılır. Windows Workflow Foundation (WF), izleme kayıtlarını Windows için olay Izleme (ETW) olayları olarak yazan standart bir izleme katılımcısı içerir. Gereksinimlerinizi karşılamıyorsa, özel bir izleme katılımcısı da yazabilirsiniz. Bu öğretici adımında, kullanıcıya görüntülenebilmeleri için `WriteLine` etkinliklerin çıkışını yakalayan özel bir izleme katılımcısı ve izleme profili oluşturma açıklanır.  
  
> [!NOTE]
> Başlangıç öğreticisindeki her konu, önceki konulara bağlıdır. Bu konuyu tamamlayabilmeniz için, önce önceki konuları doldurmanız gerekir. Tamamlanmış bir sürümü indirmek veya öğreticiye ilişkin bir video kılavuzunu görüntülemek için, bkz. [Windows Workflow Foundation (WF45)-Başlangıç Öğreticisi](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
## <a name="to-create-the-custom-tracking-participant"></a>Özel izleme katılımcısını oluşturmak için  
  
1. **Çözüm Gezgini** Için **Numberguessworkflowwhost** öğesine sağ tıklayın ve **Ekle**, **sınıf**' i seçin. Ad `StatusTrackingParticipant` kutusuna yazın ve **Ekle**' ye tıklayın.  
  
2. Aşağıdaki `using` (veya `Imports`) deyimlerini, diğer `using` (veya `Imports`) deyimleriyle dosyanın en üstüne ekleyin.  
  
    ```vb  
    Imports System.Activities.Tracking  
    Imports System.IO  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    using System.IO;  
    ```  
  
3. Sınıfından devramının ardından `StatusTrackingParticipant` sınıfını değiştirin `TrackingParticipant`.  
  
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
  
4. Aşağıdaki `Track` yöntemi geçersiz kılmayı ekleyin. Birkaç farklı izleme kaydı türü vardır. Etkinlik izleme kayıtlarında bulunan `WriteLine` etkinliklerin çıkışı ile ilgileniyoruz. `ActivityTrackingRecord` `InstanceId` Bir etkinlik için `TrackingRecord` ise, öğesinin`WriteLine`, iş akışının öğesinden sonra adlı bir dosyaya eklenir. `Text` `WriteLine` Bu öğreticide, dosya, ana bilgisayar uygulamasının geçerli klasörüne kaydedilir.  
  
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
  
     İzleme profili belirtilmediğinde, varsayılan izleme profili kullanılır. Varsayılan izleme profili kullanıldığında, izleme kayıtları tümü `ActivityStates`için yayınlanır. `WriteLine` Etkinliğin yaşam döngüsü boyunca yalnızca bir kez metin yakalamamız gerektiğinden, yalnızca bu metni `ActivityStates.Executing` durumdan çıkaracağız. [İzleme profili oluşturmak ve izleme katılımcısını kaydetmek için](#to-create-the-tracking-profile-and-register-the-tracking-participant)' de, yalnızca `WriteLine` `ActivityStates.Executing` izleme kayıtlarının yayıldığını belirten bir izleme profili oluşturulur.  
  
## <a name="to-create-the-tracking-profile-and-register-the-tracking-participant"></a>İzleme profili oluşturma ve izleme katılımcısını kaydetme  
  
1. **Çözüm Gezgini** ' de **Workflowwhostform** öğesine sağ tıklayın ve **kodu görüntüle**' yi seçin.  
  
2. Aşağıdaki `using` (veya `Imports`) deyimini, diğer `using` (veya `Imports`) deyimleriyle dosyanın en üstüne ekleyin.  
  
    ```vb  
    Imports System.Activities.Tracking  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    ```  
  
3. Aşağıdaki kodu `ConfigureWorkflowApplication` , `StringWriter` iş akışı uzantılarına ve iş akışı yaşam döngüsü işleyicilerinden önce ekleyen koddan hemen sonra ekleyin.  
  
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
  
     Bu izleme profili, yalnızca `WriteLine` `Executing` durumdaki etkinliklere ait etkinlik durumu kayıtlarının özel izleme katılımcısına yayınlandığını belirtir.  
  
     Kodu ekledikten sonra, başlangıcı `ConfigureWorkflowApplication` aşağıdaki örneğe benzer şekilde görünür.  
  
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
  
## <a name="to-display-the-tracking-information"></a>İzleme bilgilerini görüntüleme  
  
1. **Çözüm Gezgini** ' de **Workflowwhostform** öğesine sağ tıklayın ve **kodu görüntüle**' yi seçin.  
  
2. `InstanceId_SelectedIndexChanged` İşleyicisinde, durum penceresini temizleyen kodun hemen ardından aşağıdaki kodu ekleyin.  
  
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
  
     İş akışı listesinde yeni bir iş akışı seçildiğinde, bu iş akışının izleme kayıtları yüklenir ve durum penceresinde görüntülenir. Aşağıdaki örnek, tamamlanan `InstanceId_SelectedIndexChanged` işleyicidir.  
  
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
  
## <a name="to-build-and-run-the-application"></a>Uygulamayı derlemek ve çalıştırmak için  
  
1. Uygulamayı derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
2. Uygulamayı başlatmak için CTRL + F5 tuşlarına basın.  
  
3. Tahmin etme oyunu ve başlatılacak iş akışı türü için bir Aralık seçin ve **yeni oyun**' e tıklayın. Tahmin kutusuna bir tahmin girin ve tahmininizi göndermek için **Git** ' e tıklayın. İş akışının durumunun durum penceresinde görüntülendiğini unutmayın. Bu çıktı `WriteLine` etkinliklerden yakalanır. **İş akışı örneği kimliği** açılan kutusundan birini seçerek farklı bir iş akışına geçin ve geçerli iş akışının durumunun kaldırıldığını unutmayın. Önceki iş akışına dönün ve durumun geri yüklendiğini, örneğin aşağıdaki örneğe benzer olduğunu unutmayın.  
  
    > [!NOTE]
    > İzleme etkinleştirilmeden önce başlatılan bir iş akışına geçiş yaparsanız hiçbir durum gösterilmez. Ancak, ek tahminler yaparsanız, izleme artık etkinleştirildiğinden, durumları kaydedilir.  
  
    ```output
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    ```
    
    > [!NOTE]
    > Bu bilgiler, rastgele sayının aralığını belirlemek için faydalıdır, ancak daha önce hangi tahminlerin yapıldığını öğrenmek için bir bilgi içermez. Bu bilgiler sonraki adımda, [nasıl yapılır: Bir Iş akışının](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)birden çok sürümünü yan yana barındırın.

    İş akışı örnek kimliğini bir yere getirin ve oyunu tamamlamada yürütün.
  
4. Windows Gezgini 'ni açın ve **Numberguessworkflowwhost\bin\debug** klasörüne (veya proje ayarlarınıza bağlı olarak **bin\release** ) gidin. Proje yürütülebilir dosyalarına ek olarak, GUID dosya adlarıyla dosya olduğunu unutmayın. Önceki adımda tamamlanan iş akışından iş akışı örneği kimliğine karşılık gelen bir tane belirler ve Not defteri 'nde açın. İzleme bilgileri aşağıdakine benzer bilgiler içerir.  
  
    ```output
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    ```

    Bu izleme verileri, kullanıcının tahminlerini yokluğuna ek olarak, iş akışının nihai tahminine ilişkin bilgiler içermez. Bunun nedeni, izleme bilgilerinin yalnızca `WriteLine` iş akışındaki çıktıyı ve görüntülenen son iletiyi, iş akışı tamamlandıktan sonra `Completed` işleyiciden yapılır. Öğreticinin sonraki adımında, [nasıl yapılır: Bir iş akışının](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)birden çok sürümünü yan yana barındırın, mevcut `WriteLine` etkinlikler kullanıcının tahminlerini görüntüleyecek şekilde değiştirilir ve nihai sonuçları görüntüleyen ek `WriteLine` bir etkinlik eklenir. Bu değişiklikler tümleşik [olduktan sonra: Bir iş akışının birden çok sürümünü yan yana](how-to-host-multiple-versions-of-a-workflow-side-by-side.md) barındırma bir iş akışının birden çok sürümünü aynı anda nasıl barındırabileceğinizi gösterir.
