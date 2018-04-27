---
title: 'Nasıl yapılır: özel izleme katılımcı oluşturma'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 1b612c7e-2381-4a7c-b07a-77030415f2a3
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d53035c2fb41800a91d3cdea134ae811a09fa3e9
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-create-a-custom-tracking-participant"></a>Nasıl yapılır: özel izleme katılımcı oluşturma
İş akışı izleme iş akışı yürütme durumu görünürlük sağlar. İş akışı çalışma zamanı iş akışı yaşam döngüsü olayları, etkinlik yaşam döngüsü olayları, yer işareti sürdürülmesi ve hataları açıklayan izleme kayıtları yayar. Bu izleme kayıtları katılımcıları izleme tarafından kullanılır. Windows Workflow Foundation (WF) izleme kayıtları olay Windows için izleme (ETW) olayları olarak yazan standart izleme katılımcı içerir. Özel İzleme katılımcı Ayrıca, gereksinimlerinizi karşılamıyorsa yazabilirsiniz. Bu öğretici adım özel izleme katılımcı ve çıktısını yakalama izleme profili oluşturmayı açıklar `WriteLine` etkinlikleri böylece kullanıcıya gösterilir.  
  
> [!NOTE]
>  Başlarken Öğreticisi her bir konuda önceki konularda bağlıdır. Bu konuda tamamlamak için önce önceki konularını tamamlamanız gerekir. Tamamlanmış sürümü indirme veya videosu öğreticinin görüntülemek için bkz: [Windows Workflow Foundation (WF45) - başlangıç Öğreticisi](http://go.microsoft.com/fwlink/?LinkID=248976).  
  
## <a name="in-this-topic"></a>Bu konuda  
  
-   [Özel İzleme katılımcı oluşturmak için](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_CustomTrackingParticipant)  
  
-   [İzleme profili oluşturma ve izleme katılımcı kaydetme](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_TrackingProfile)  
  
-   [İzleme bilgilerini görüntülemek için](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_DisplayTracking)  
  
-   [Derleme ve uygulamayı çalıştırmak için](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_BuildAndRun)  
  
###  <a name="BKMK_CustomTrackingParticipant"></a> Özel İzleme katılımcı oluşturmak için  
  
1.  Sağ **NumberGuessWorkflowHost** içinde **Çözüm Gezgini** ve **Ekle**, **sınıfı**. Tür `StatusTrackingParticipant` içine **adı** ve'ı tıklatın **Ekle**.  
  
2.  Aşağıdakileri ekleyin `using` (veya `Imports`) diğer dosyanın en üstüne deyimlerini `using` (veya `Imports`) deyimleri.  
  
    ```vb  
    Imports System.Activities.Tracking  
    Imports System.IO  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    using System.IO;  
    ```  
  
3.  Değiştirme `StatusTrackingParticipant` öğesinden devralınan sınıfının `TrackingParticipant`.  
  
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
  
4.  Aşağıdakileri ekleyin `Track` yöntemi geçersiz kılma. Kayıtları İzleme birkaç farklı tür vardır. Biz çıktısında ilgilendiğiniz `WriteLine` kayıtları izleme etkinlikte bulunan etkinlikler. Varsa `TrackingRecord` olan bir `ActivityTrackingRecord` için bir `WriteLine` etkinliği `Text` , `WriteLine` sonra adlı bir dosyaya eklenir `InstanceId` iş akışı. Bu öğreticide, dosya geçerli ana bilgisayar uygulamasını klasörüne kaydedilir.  
  
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
  
     İzleme profili belirtildiğinde, varsayılan profili izleme kullanılır. Varsayılan profil izleme kullanıldığında, izleme kayıtları tüm gösterilen `ActivityStates`. Yalnızca bir kez yaşam döngüsü sırasında metni yakalamak ihtiyacımız çünkü `WriteLine` etkinlik, biz yalnızca Ayıkla metinden `ActivityStates.Executing` durumu. İçinde [izleme profili oluşturma ve izleme katılımcı kaydetme](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_TrackingProfile), yalnızca belirten bir izleme profili oluşturulur `WriteLine` `ActivityStates.Executing` izleme kayıtları yayılan.  
  
###  <a name="BKMK_TrackingProfile"></a> İzleme profili oluşturma ve izleme katılımcı kaydetme  
  
1.  Sağ **WorkflowHostForm** içinde **Çözüm Gezgini** ve **görünümü kodu**.  
  
2.  Aşağıdakileri ekleyin `using` (veya `Imports`) deyimini dosyanın üst kısmındaki diğer `using` (veya `Imports`) deyimleri.  
  
    ```vb  
    Imports System.Activities.Tracking  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    ```  
  
3.  Aşağıdaki kodu ekleyin `ConfigureWorkflowApplication` ekleyen koddan sonra `StringWriter` iş akışı uzantıları ve iş akışı yaşam döngüsü işleyicileri önce.  
  
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
  
     Bu izleme profili yalnızca etkinlik durumu için kaydeder belirten `WriteLine` aktivitelerde `Executing` durumu özel izleme katılımcı yayılan.  
  
     Başlangıç kodu ekledikten sonra `ConfigureWorkflowApplication` aşağıdaki gibi görünür.  
  
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
  
###  <a name="BKMK_DisplayTracking"></a> İzleme bilgilerini görüntülemek için  
  
1.  Sağ **WorkflowHostForm** içinde **Çözüm Gezgini** ve **görünümü kodu**.  
  
2.  İçinde `InstanceId_SelectedIndexChanged` işleyici, hemen durum penceresi temizler koddan sonra aşağıdaki kodu ekleyin.  
  
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
  
     Yeni bir iş akışı iş akışı listesinde seçili olduğunda, iş akışının izleme kayıtları yüklenen ve durum penceresinde görüntülenir. Aşağıdaki örnekte tamamlanmış olan `InstanceId_SelectedIndexChanged` işleyici.  
  
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
  
###  <a name="BKMK_BuildAndRun"></a> Derleme ve uygulamayı çalıştırmak için  
  
1.  Uygulamanızı oluşturmak için Ctrl + Shift + B tuşuna basın.  
  
2.  Uygulamayı başlatmak için CTRL + F5 tuşuna basın.  
  
3.  Tahmin eden oyun ve başlatın ve iş akışı türü için bir aralık seçmek **yeni oyun**. Bir tahmin girin **tahmin** kutusuna ve tıklatın **Git** , tahmin göndermek için. İş akışının durumunu durum penceresinde görüntülendiğine dikkat edin. Bu çıktı gelen yakalanan `WriteLine` etkinlikler. Geçiş için farklı bir iş akışı birinden seçerek **iş akışı örneği kimliği** birleşik giriş kutusu ve geçerli iş akışının durumunu kaldırdığını unutmayın. Durum, aşağıdaki örneğe benzer şekilde geri yüklendiğini Not ve önceki iş akışı için dönün.  
  
    > [!NOTE]
    >  İzleme etkinleştirilmeden önce başlatılan bir iş akışı için geçiş yaparsanız yok durumu görüntülenir. Ancak ek tahmin yaparsanız, izleme artık etkin olmadığından durumlarını kaydedilir.  
  
 **Lütfen 1 ile 10 arasında bir sayı girin**  
**Tahmin çok yüksektir.**   
**Lütfen 1 ile 10 arasında bir sayı girin**    
    > [!NOTE]
    >  Bu bilgiler, rastgele sayı aralığı belirlemede yararlıdır, ancak hangi tahmin daha önce yaptığınız hakkında bilgi içermiyor. Bu bilgiler sonraki adımda olduğu [nasıl yapılır: bir iş akışı yan yana birden fazla sürümünü konak](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).  
  
     İş akışı örneği kimliği not edin ve onun tamamlanıncaya kadar oyun.  
  
4.  Windows Gezgini'ni açın ve gidin **NumberGuessWorkflowHost\bin\debug** klasörü (veya **bin\release** proje ayarlarınızı bağlı olarak). Ek olarak proje GUID dosya adları dosyalarıyla yürütülebilir dosya olduğunu unutmayın. Önceki adımda tamamlanmış iş akışından iş akışı örneği kimliğine karşılık gelen bir belirleyin ve Not Defteri'nde açın. İzleme bilgileri aşağıdakine benzer bilgiler içerir.  
  
 **Lütfen 1 ile 10 arasında bir sayı girin**  
**Tahmin çok yüksektir.**   
**Lütfen 1 ile 10 arasında bir sayı girin**   
**Tahmin çok yüksektir.**   
**Lütfen 1 ile 10 arasında bir sayı girin** kullanıcının tahmin olmaması ek olarak, bu izleme verilerine iş akışının son tahmin hakkında bilgi içermiyor. İzleme bilgileri yalnızca oluşan çünkü `WriteLine` iş akışından çıkış ve görüntülenen son iletisi nden yapılır `Completed` iş akışı tamamlandığında işleyici. Öğreticinin sonraki adımda [nasıl yapılır: bir iş akışı yan yana birden fazla sürümünü konak](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md), varolan `WriteLine` etkinlikleri kullanıcının tahmin ve ek bir görüntülemek için değiştirildiğinde `WriteLine` etkinlik, eklenir Son sonuçlarını görüntüler. Bu değişiklikler tümleşik sonra [nasıl yapılır: bir iş akışı yan yana birden fazla sürümünü konak](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md) aynı anda birden çok iş akışı sürümü barındırmak gösterilmiştir.
