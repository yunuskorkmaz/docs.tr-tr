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
# <a name="how-to-create-a-custom-tracking-participant"></a><span data-ttu-id="5bb67-102">Nasıl yapılır: Özel İzleme Katılımcısı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5bb67-102">How to: Create a Custom Tracking Participant</span></span>
<span data-ttu-id="5bb67-103">İş akışı izleme, iş akışı yürütme durumuna görünürlük sağlar.</span><span class="sxs-lookup"><span data-stu-id="5bb67-103">Workflow tracking provides visibility into the status of workflow execution.</span></span> <span data-ttu-id="5bb67-104">İş akışı çalışma zamanı, iş akışı yaşam döngüsü olaylarını, etkinlik yaşam döngüsü olaylarını, yer imi yeniden başlamalarını ve hataları açıklayan izleme kayıtlarını yayar.</span><span class="sxs-lookup"><span data-stu-id="5bb67-104">The workflow runtime emits tracking records that describe workflow lifecycle events, activity lifecycle events, bookmark resumptions, and faults.</span></span> <span data-ttu-id="5bb67-105">Bu izleme kayıtları, izleme katılımcıları tarafından tüketilir.</span><span class="sxs-lookup"><span data-stu-id="5bb67-105">These tracking records are consumed by tracking participants.</span></span> <span data-ttu-id="5bb67-106">Windows İş Akışı Temeli (WF), Windows için Olay İzleme (ETW) olayları olarak izleme kayıtları yazan standart bir izleme katılımcısı içerir.</span><span class="sxs-lookup"><span data-stu-id="5bb67-106">Windows Workflow Foundation (WF) includes a standard tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span> <span data-ttu-id="5bb67-107">Bu gereksinimlerinizi karşılamazsa, özel bir izleme katılımcısı da yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5bb67-107">If that does not meet your requirements, you can also write a custom tracking participant.</span></span> <span data-ttu-id="5bb67-108">Bu öğretici adım, kullanıcıya görüntülenebilecek etkinliklerin çıktısını `WriteLine` yakalayan özel bir izleme katılımcısı ve izleme profilinin nasıl oluşturulabileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="5bb67-108">This tutorial step describes how to create a custom tracking participant and tracking profile that capture the output of `WriteLine` activities so that they can be displayed to the user.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5bb67-109">Başlarken öğreticideki her konu önceki konulara bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="5bb67-109">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="5bb67-110">Bu konuyu tamamlamak için önce önceki konuları tamamlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5bb67-110">To complete this topic, you must first complete the previous topics.</span></span> <span data-ttu-id="5bb67-111">Tamamlanmış bir sürümü indirmek veya öğreticinin video walkthrough'ını görüntülemek için [Windows İş Akışı Vakfı 'na (WF45) bakın - Eğitime Başlarken.](https://go.microsoft.com/fwlink/?LinkID=248976)</span><span class="sxs-lookup"><span data-stu-id="5bb67-111">To download a completed version or view a video walkthrough of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="to-create-the-custom-tracking-participant"></a><span data-ttu-id="5bb67-112">Özel izleme katılımcısı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="5bb67-112">To create the custom tracking participant</span></span>  
  
1. <span data-ttu-id="5bb67-113">**Solution Explorer'da** **NumberGuessWorkflowHost'a** sağ tıklayın ve **Ekle**, **Sınıf**seçin.</span><span class="sxs-lookup"><span data-stu-id="5bb67-113">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **Class**.</span></span> <span data-ttu-id="5bb67-114">`StatusTrackingParticipant` **Ad** kutusuna yazın ve **Ekle'yi**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="5bb67-114">Type `StatusTrackingParticipant` into the **Name** box, and click **Add**.</span></span>  
  
2. <span data-ttu-id="5bb67-115">Dosyanın `using` üst `Imports`kısmındaki diğer `using` (veya ) deyimleriyle `Imports`birlikte aşağıdaki (veya) ifadeleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5bb67-115">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Activities.Tracking  
    Imports System.IO  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    using System.IO;  
    ```  
  
3. <span data-ttu-id="5bb67-116">`StatusTrackingParticipant` Sınıfı, 'den `TrackingParticipant`devralan olacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="5bb67-116">Modify the `StatusTrackingParticipant` class so that it inherits from `TrackingParticipant`.</span></span>  
  
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
  
4. <span data-ttu-id="5bb67-117">Aşağıdaki `Track` yöntem geçersiz kılma ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5bb67-117">Add the following `Track` method override.</span></span> <span data-ttu-id="5bb67-118">Birkaç farklı izleme kaydı türü vardır.</span><span class="sxs-lookup"><span data-stu-id="5bb67-118">There are several different types of tracking records.</span></span> <span data-ttu-id="5bb67-119">Faaliyet izleme kayıtlarında `WriteLine` yer alan faaliyetlerin çıktısı ile ilgileniyoruz.</span><span class="sxs-lookup"><span data-stu-id="5bb67-119">We are interested in the output of `WriteLine` activities, which are contained in activity tracking records.</span></span> <span data-ttu-id="5bb67-120">`TrackingRecord` `ActivityTrackingRecord` Bir `WriteLine` etkinlik için ise, `Text` `WriteLine` iş akışının adını `InstanceId` taşıyan bir dosyaya eklenir.</span><span class="sxs-lookup"><span data-stu-id="5bb67-120">If the `TrackingRecord` is an `ActivityTrackingRecord` for a `WriteLine` activity, the `Text` of the `WriteLine` is appended to a file named after the `InstanceId` of the workflow.</span></span> <span data-ttu-id="5bb67-121">Bu öğreticide, dosya ana bilgisayar uygulamasının geçerli klasörüne kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="5bb67-121">In this tutorial, the file is saved to the current folder of the host application.</span></span>  
  
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
  
     <span data-ttu-id="5bb67-122">Hiçbir izleme profili belirtilmediğinde, varsayılan izleme profili kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5bb67-122">When no tracking profile is specified, the default tracking profile is used.</span></span> <span data-ttu-id="5bb67-123">Varsayılan izleme profili kullanıldığında, izleme kayıtları herkes `ActivityStates`için yayılır.</span><span class="sxs-lookup"><span data-stu-id="5bb67-123">When the default tracking profile is used, tracking records are emitted for all `ActivityStates`.</span></span> <span data-ttu-id="5bb67-124">Etkinliğin yaşam döngüsü boyunca metni yalnızca bir kez `WriteLine` yakalamamız gerektiğinden, metni `ActivityStates.Executing` yalnızca devletten ayıklarız.</span><span class="sxs-lookup"><span data-stu-id="5bb67-124">Because we only need to capture the text one time during the lifecycle of the `WriteLine` activity, we only extract the text from the `ActivityStates.Executing` state.</span></span> <span data-ttu-id="5bb67-125">[İzleme profilini oluşturmak ve izleme katılımcısını kaydetmek](#to-create-the-tracking-profile-and-register-the-tracking-participant)için, yalnızca `WriteLine` `ActivityStates.Executing` izleme kayıtlarının yayıldığını belirten bir izleme profili oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5bb67-125">In [To create the tracking profile and register the tracking participant](#to-create-the-tracking-profile-and-register-the-tracking-participant), a tracking profile is created that specifies that only `WriteLine` `ActivityStates.Executing` tracking records are emitted.</span></span>  
  
## <a name="to-create-the-tracking-profile-and-register-the-tracking-participant"></a><span data-ttu-id="5bb67-126">İzleme profilini oluşturmak ve izleme katılımcısını kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="5bb67-126">To create the tracking profile and register the tracking participant</span></span>  
  
1. <span data-ttu-id="5bb67-127">**Solution Explorer'da** **İş AkışıHostForm'a** sağ tıklayın ve **Kodu Görüntüle'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="5bb67-127">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>  
  
2. <span data-ttu-id="5bb67-128">Aşağıdaki `using` `Imports`(veya ) deyimini dosyanın üst kısmındaki diğer `using` (veya) `Imports`deyimleriyle birlikte ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5bb67-128">Add the following `using` (or `Imports`) statement at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Activities.Tracking  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    ```  
  
3. <span data-ttu-id="5bb67-129">İş akışı uzantılarına ekleyen `ConfigureWorkflowApplication` `StringWriter` koddan hemen sonraya ve iş akışı yaşam döngüsü işleyicilerinden önce aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5bb67-129">Add the following code to `ConfigureWorkflowApplication` just after the code that adds the `StringWriter` to the workflow extensions and before the workflow lifecycle handlers.</span></span>  
  
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
  
     <span data-ttu-id="5bb67-130">Bu izleme profili, yalnızca eyaletteki `WriteLine` etkinliklere `Executing` ait etkinlik durumu kayıtlarının özel izleme katılımcısına yayDığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5bb67-130">This tracking profile specifies that only activity state records for `WriteLine` activities in the `Executing` state are emitted to the custom tracking participant.</span></span>  
  
     <span data-ttu-id="5bb67-131">Kodu ekledikten sonra, `ConfigureWorkflowApplication` başlangıç aşağıdaki örnek gibi görünecektir.</span><span class="sxs-lookup"><span data-stu-id="5bb67-131">After adding the code, the start of `ConfigureWorkflowApplication` will look like the following example.</span></span>  
  
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
  
## <a name="to-display-the-tracking-information"></a><span data-ttu-id="5bb67-132">İzleme bilgilerini görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="5bb67-132">To display the tracking information</span></span>  
  
1. <span data-ttu-id="5bb67-133">**Solution Explorer'da** **İş AkışıHostForm'a** sağ tıklayın ve **Kodu Görüntüle'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="5bb67-133">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>  
  
2. <span data-ttu-id="5bb67-134">İşleyicide, `InstanceId_SelectedIndexChanged` durum penceresini temizleyen koddan hemen sonra aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5bb67-134">In the `InstanceId_SelectedIndexChanged` handler, add the following code immediately after the code that clears the status window.</span></span>  
  
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
  
     <span data-ttu-id="5bb67-135">İş akışı listesinde yeni bir iş akışı seçildiğinde, bu iş akışına ait izleme kayıtları yüklenir ve durum penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="5bb67-135">When a new workflow is selected in the workflow list, the tracking records for that workflow are loaded and displayed in the status window.</span></span> <span data-ttu-id="5bb67-136">Aşağıdaki örnek tamamlanmış `InstanceId_SelectedIndexChanged` işleyicidir.</span><span class="sxs-lookup"><span data-stu-id="5bb67-136">The following example is the completed `InstanceId_SelectedIndexChanged` handler.</span></span>  
  
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
  
## <a name="to-build-and-run-the-application"></a><span data-ttu-id="5bb67-137">Uygulamayı oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="5bb67-137">To build and run the application</span></span>  
  
1. <span data-ttu-id="5bb67-138">Uygulamayı oluşturmak için Ctrl+Shift+B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="5bb67-138">Press Ctrl+Shift+B to build the application.</span></span>  
  
2. <span data-ttu-id="5bb67-139">Uygulamayı başlatmak için Ctrl+F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="5bb67-139">Press Ctrl+F5 to start the application.</span></span>  
  
3. <span data-ttu-id="5bb67-140">Tahmin oyunu ve başlamak için iş akışı türü için bir aralık seçin ve **Yeni Oyun'u**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="5bb67-140">Select a range for the guessing game and the type of workflow to start, and click **New Game**.</span></span> <span data-ttu-id="5bb67-141">**Tahmin** kutusuna bir tahmin girin ve tahmininizi göndermek için **Git'i** tıklatın.</span><span class="sxs-lookup"><span data-stu-id="5bb67-141">Enter a guess in the **Guess** box and click **Go** to submit your guess.</span></span> <span data-ttu-id="5bb67-142">İş akışının durumunun durum penceresinde görüntülendiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="5bb67-142">Note that the status of the workflow is displayed in the status window.</span></span> <span data-ttu-id="5bb67-143">Bu çıktı `WriteLine` etkinliklerden yakalanır.</span><span class="sxs-lookup"><span data-stu-id="5bb67-143">This output is captured from the `WriteLine` activities.</span></span> <span data-ttu-id="5bb67-144">**İş Akışı Örneği Id** açılan kutusundan birini seçerek farklı bir iş akışına geçin ve geçerli iş akışının durumunun kaldırıldığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="5bb67-144">Switch to a different workflow by selecting one from the **Workflow Instance Id** combo box and note that the status of the current workflow is removed.</span></span> <span data-ttu-id="5bb67-145">Önceki iş akışına geri dön ve aşağıdaki örneğe benzer şekilde durumun geri yüklenmiş olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="5bb67-145">Switch back to the previous workflow and note that the status is restored, similar to the following example.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="5bb67-146">İzleme etkinleştirilmeden önce başlatılan bir iş akışına geçerseniz hiçbir durum görüntülenmez.</span><span class="sxs-lookup"><span data-stu-id="5bb67-146">If you switch to a workflow that was started before tracking was enabled no status is displayed.</span></span> <span data-ttu-id="5bb67-147">Ancak ek tahminleryaparsanız, izleme artık etkinleştirildiğinden durumları kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="5bb67-147">However if you make additional guesses, their status is saved because tracking is now enabled.</span></span>  
  
    ```output
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    ```

    > [!NOTE]
    > <span data-ttu-id="5bb67-148">Bu bilgiler rasgele sayının aralığını belirlemek için yararlıdır, ancak daha önce hangi tahminlerin yapıldığı hakkında herhangi bir bilgi içermez.</span><span class="sxs-lookup"><span data-stu-id="5bb67-148">This information is useful for determining the range of the random number, but it does not contain any information about what guesses have been previously made.</span></span> <span data-ttu-id="5bb67-149">Bu bilgiler bir sonraki adımda, [Nasıl yapılır: İş Akışının Birden Çok Sürümü Yan Yana.](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)</span><span class="sxs-lookup"><span data-stu-id="5bb67-149">This information is in the next step, [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>

    <span data-ttu-id="5bb67-150">İş akışı örneği id'ini not edin ve oyunu tamamlanmasına kadar oynayın.</span><span class="sxs-lookup"><span data-stu-id="5bb67-150">Make a note of the workflow instance id, and play the game through to its completion.</span></span>
  
4. <span data-ttu-id="5bb67-151">Windows Gezgini'ni açın ve **NumberGuessWorkflowHost\bin\debug** klasörüne gidin (veya proje ayarlarınıza bağlı olarak **bin\release).**</span><span class="sxs-lookup"><span data-stu-id="5bb67-151">Open Windows Explorer and navigate to the **NumberGuessWorkflowHost\bin\debug** folder (or **bin\release** depending on your project settings).</span></span> <span data-ttu-id="5bb67-152">Proje yürütülebilir dosyalara ek olarak kılavuz dosya adlarına sahip dosyalar olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="5bb67-152">Note that in addition to the project executable files there are files with guid filenames.</span></span> <span data-ttu-id="5bb67-153">Önceki adımda tamamlanan iş akışı kimliğinden iş akışı örneği kimliğine karşılık geleni belirleyin ve Not Defteri'nde açın.</span><span class="sxs-lookup"><span data-stu-id="5bb67-153">Identify the one that corresponds to the workflow instance id from the completed workflow in the previous step and open it in Notepad.</span></span> <span data-ttu-id="5bb67-154">İzleme bilgileri aşağıdakine benzer bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="5bb67-154">The tracking information contains information similar to the following.</span></span>  
  
    ```output
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    ```

    <span data-ttu-id="5bb67-155">Kullanıcının tahminlerinin olmamasına ek olarak, bu izleme verileri iş akışının son tahmini hakkında bilgi içermez.</span><span class="sxs-lookup"><span data-stu-id="5bb67-155">In addition to the absence of the user's guesses, this tracking data does not contain information about the final guess of the workflow.</span></span> <span data-ttu-id="5bb67-156">Bunun nedeni, izleme bilgilerinin `WriteLine` yalnızca iş akışından çıkan çıktıdan oluşması ve görüntülenen `Completed` son iletinin iş akışı tamamlandıktan sonra işleyiciden yapılmasıdır.</span><span class="sxs-lookup"><span data-stu-id="5bb67-156">That is because the tracking information consists only of the `WriteLine` output from the workflow, and the final message that is displayed is done so from the `Completed` handler after the workflow completes.</span></span> <span data-ttu-id="5bb67-157">Öğreticinin bir sonraki adımında, [Nasıl Yapılır: İş Akışının Birden Çok](how-to-host-multiple-versions-of-a-workflow-side-by-side.md) `WriteLine` Sürümü Yan Yana, varolan etkinlikler kullanıcının `WriteLine` tahminlerini görüntülemek üzere değiştirilir ve nihai sonuçları görüntüleyen ek bir etkinlik eklenir.</span><span class="sxs-lookup"><span data-stu-id="5bb67-157">In next step of the tutorial, [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md), the existing `WriteLine` activities are modified to display the user's guesses, and an additional `WriteLine` activity is added that displays the final results.</span></span> <span data-ttu-id="5bb67-158">Bu değişiklikler tümleşik olduktan sonra, [Nasıl Yapılır: İş Akışının Birden Çok Sürümü Yan Yana](how-to-host-multiple-versions-of-a-workflow-side-by-side.md) Nasıl Barındırılır, aynı anda bir iş akışının birden çok sürümü nasıl barındırılabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5bb67-158">After these changes are integrated, [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md) demonstrates how to host multiple versions of a workflow at the same time.</span></span>
