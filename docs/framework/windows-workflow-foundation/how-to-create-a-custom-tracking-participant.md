---
title: 'Nasıl Yapılır: Özel İzleme Katılımcısı oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b612c7e-2381-4a7c-b07a-77030415f2a3
ms.openlocfilehash: 0f8d21ca4f08ad4dc2e5f5e62695b9b14aff13d5
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53156707"
---
# <a name="how-to-create-a-custom-tracking-participant"></a><span data-ttu-id="06e67-102">Nasıl Yapılır: Özel İzleme Katılımcısı oluşturma</span><span class="sxs-lookup"><span data-stu-id="06e67-102">How to: Create a Custom Tracking Participant</span></span>
<span data-ttu-id="06e67-103">İş akışı izleme, iş akışı yürütme durumunu görünürlük sağlar.</span><span class="sxs-lookup"><span data-stu-id="06e67-103">Workflow tracking provides visibility into the status of workflow execution.</span></span> <span data-ttu-id="06e67-104">İş akışı çalışma zamanı iş akışı yaşam döngüsü olayları, etkinlik yaşam döngüsü olayları, yer işareti harcanması ve hataları tanımlayan izleme kayıtları gösterir.</span><span class="sxs-lookup"><span data-stu-id="06e67-104">The workflow runtime emits tracking records that describe workflow lifecycle events, activity lifecycle events, bookmark resumptions, and faults.</span></span> <span data-ttu-id="06e67-105">Bu izleme kayıtları izleme katılımcıları tarafından tüketilir.</span><span class="sxs-lookup"><span data-stu-id="06e67-105">These tracking records are consumed by tracking participants.</span></span> <span data-ttu-id="06e67-106">Windows Workflow Foundation (WF) izleme kayıtları için olay izleme Windows (ETW) olayları olarak yazan standart izleme katılımcı içerir.</span><span class="sxs-lookup"><span data-stu-id="06e67-106">Windows Workflow Foundation (WF) includes a standard tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span> <span data-ttu-id="06e67-107">Gereksinimlerinizi karşılamıyorsa, özel izleme katılımcı de yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="06e67-107">If that does not meet your requirements, you can also write a custom tracking participant.</span></span> <span data-ttu-id="06e67-108">Bu öğretici adım özel izleme katılımcı ve çıktısını yakalamak izleme profili oluşturmayı açıklar `WriteLine` etkinlikleri ve böylece kullanıcıya gösterilir.</span><span class="sxs-lookup"><span data-stu-id="06e67-108">This tutorial step describes how to create a custom tracking participant and tracking profile that capture the output of `WriteLine` activities so that they can be displayed to the user.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="06e67-109">Önceki konularıyla ilgili her konuda Başlarken Öğreticisi bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="06e67-109">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="06e67-110">Bu konuyu tamamlamak için önceki konu tamamlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="06e67-110">To complete this topic, you must first complete the previous topics.</span></span> <span data-ttu-id="06e67-111">Tamamlanmış bir sürümünü indirin veya videosu öğreticinin görüntülemek için bkz: [Windows Workflow Foundation (WF45) - başlangıç Öğreticisi](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="06e67-111">To download a completed version or view a video walkthrough of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="in-this-topic"></a><span data-ttu-id="06e67-112">Bu konuda</span><span class="sxs-lookup"><span data-stu-id="06e67-112">In this topic</span></span>  
  
-   [<span data-ttu-id="06e67-113">Özel İzleme Katılımcısı oluşturma</span><span class="sxs-lookup"><span data-stu-id="06e67-113">To create the custom tracking participant</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_CustomTrackingParticipant)  
  
-   [<span data-ttu-id="06e67-114">İzleme profili oluşturma ve izleme Katılımcısı kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="06e67-114">To create the tracking profile and register the tracking participant</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_TrackingProfile)  
  
-   [<span data-ttu-id="06e67-115">İzleme bilgilerini görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="06e67-115">To display the tracking information</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_DisplayTracking)  
  
-   [<span data-ttu-id="06e67-116">Derleme ve uygulamayı çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="06e67-116">To build and run the application</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_BuildAndRun)  
  
###  <a name="BKMK_CustomTrackingParticipant"></a> <span data-ttu-id="06e67-117">Özel İzleme Katılımcısı oluşturma</span><span class="sxs-lookup"><span data-stu-id="06e67-117">To create the custom tracking participant</span></span>  
  
1.  <span data-ttu-id="06e67-118">Sağ **NumberGuessWorkflowHost** içinde **Çözüm Gezgini** ve **Ekle**, **sınıfı**.</span><span class="sxs-lookup"><span data-stu-id="06e67-118">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **Class**.</span></span> <span data-ttu-id="06e67-119">Tür `StatusTrackingParticipant` içine **adı** ve'ı tıklatın **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="06e67-119">Type `StatusTrackingParticipant` into the **Name** box, and click **Add**.</span></span>  
  
2.  <span data-ttu-id="06e67-120">Aşağıdaki `using` (veya `Imports`) deyimini dosyanın diğer üst `using` (veya `Imports`) ifadeleri.</span><span class="sxs-lookup"><span data-stu-id="06e67-120">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Activities.Tracking  
    Imports System.IO  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    using System.IO;  
    ```  
  
3.  <span data-ttu-id="06e67-121">Değiştirme `StatusTrackingParticipant` devraldığı sınıfının `TrackingParticipant`.</span><span class="sxs-lookup"><span data-stu-id="06e67-121">Modify the `StatusTrackingParticipant` class so that it inherits from `TrackingParticipant`.</span></span>  
  
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
  
4.  <span data-ttu-id="06e67-122">Aşağıdaki `Track` yöntemi geçersiz kılma.</span><span class="sxs-lookup"><span data-stu-id="06e67-122">Add the following `Track` method override.</span></span> <span data-ttu-id="06e67-123">Kayıtları İzleme birkaç farklı türleri vardır.</span><span class="sxs-lookup"><span data-stu-id="06e67-123">There are several different types of tracking records.</span></span> <span data-ttu-id="06e67-124">Biz çıktısında ilgilendiğiniz `WriteLine` kayıtları izleme etkinliğinde bulunan etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="06e67-124">We are interested in the output of `WriteLine` activities, which are contained in activity tracking records.</span></span> <span data-ttu-id="06e67-125">Varsa `TrackingRecord` olduğu bir `ActivityTrackingRecord` için bir `WriteLine` etkinliği `Text` , `WriteLine` sonra adlı bir dosyaya eklenir `InstanceId` iş akışı.</span><span class="sxs-lookup"><span data-stu-id="06e67-125">If the `TrackingRecord` is an `ActivityTrackingRecord` for a `WriteLine` activity, the `Text` of the `WriteLine` is appended to a file named after the `InstanceId` of the workflow.</span></span> <span data-ttu-id="06e67-126">Bu öğreticide, dosyanın ana uygulama geçerli klasöre kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="06e67-126">In this tutorial, the file is saved to the current folder of the host application.</span></span>  
  
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
  
     <span data-ttu-id="06e67-127">Varsayılan profil izleme, izleme profil belirtildiğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="06e67-127">When no tracking profile is specified, the default tracking profile is used.</span></span> <span data-ttu-id="06e67-128">Varsayılan profil izleme kullanıldığında, izleme kayıtları tüm yayılan `ActivityStates`.</span><span class="sxs-lookup"><span data-stu-id="06e67-128">When the default tracking profile is used, tracking records are emitted for all `ActivityStates`.</span></span> <span data-ttu-id="06e67-129">Biz yalnızca bir kez yaşam döngüsü sırasında metin yakalamak gerektiğinden `WriteLine` etkinlik, biz yalnızca Ayıkla metinden `ActivityStates.Executing` durumu.</span><span class="sxs-lookup"><span data-stu-id="06e67-129">Because we only need to capture the text one time during the lifecycle of the `WriteLine` activity, we only extract the text from the `ActivityStates.Executing` state.</span></span> <span data-ttu-id="06e67-130">İçinde [izleme profili oluşturma ve izleme Katılımcısı kaydetmek için](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_TrackingProfile), yalnızca belirten bir izleme profili oluşturulan `WriteLine` `ActivityStates.Executing` izleme kayıtları yayılan.</span><span class="sxs-lookup"><span data-stu-id="06e67-130">In [To create the tracking profile and register the tracking participant](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_TrackingProfile), a tracking profile is created that specifies that only `WriteLine` `ActivityStates.Executing` tracking records are emitted.</span></span>  
  
###  <a name="BKMK_TrackingProfile"></a> <span data-ttu-id="06e67-131">İzleme profili oluşturma ve izleme Katılımcısı kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="06e67-131">To create the tracking profile and register the tracking participant</span></span>  
  
1.  <span data-ttu-id="06e67-132">Sağ **WorkflowHostForm** içinde **Çözüm Gezgini** ve **kodu görüntüle**.</span><span class="sxs-lookup"><span data-stu-id="06e67-132">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>  
  
2.  <span data-ttu-id="06e67-133">Aşağıdaki `using` (veya `Imports`) deyimini dosyanın diğer üst `using` (veya `Imports`) ifadeleri.</span><span class="sxs-lookup"><span data-stu-id="06e67-133">Add the following `using` (or `Imports`) statement at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Activities.Tracking  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    ```  
  
3.  <span data-ttu-id="06e67-134">Aşağıdaki kodu ekleyin `ConfigureWorkflowApplication` ekleyen koddan sonra `StringWriter` iş akışı uzantıları ve iş akışı yaşam döngüsü işleyicileri önce.</span><span class="sxs-lookup"><span data-stu-id="06e67-134">Add the following code to `ConfigureWorkflowApplication` just after the code that adds the `StringWriter` to the workflow extensions and before the workflow lifecycle handlers.</span></span>  
  
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
  
     <span data-ttu-id="06e67-135">Bu izleme profili için yalnızca bir etkinlik durumu kayıt belirtir `WriteLine` etkinlikler `Executing` durum için özel izleme katılımcı yayılır.</span><span class="sxs-lookup"><span data-stu-id="06e67-135">This tracking profile specifies that only activity state records for `WriteLine` activities in the `Executing` state are emitted to the custom tracking participant.</span></span>  
  
     <span data-ttu-id="06e67-136">Başlangıç kodu ekledikten sonra `ConfigureWorkflowApplication` aşağıdaki örnekteki gibi görünecektir.</span><span class="sxs-lookup"><span data-stu-id="06e67-136">After adding the code, the start of `ConfigureWorkflowApplication` will look like the following example.</span></span>  
  
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
  
###  <a name="BKMK_DisplayTracking"></a> <span data-ttu-id="06e67-137">İzleme bilgilerini görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="06e67-137">To display the tracking information</span></span>  
  
1.  <span data-ttu-id="06e67-138">Sağ **WorkflowHostForm** içinde **Çözüm Gezgini** ve **kodu görüntüle**.</span><span class="sxs-lookup"><span data-stu-id="06e67-138">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>  
  
2.  <span data-ttu-id="06e67-139">İçinde `InstanceId_SelectedIndexChanged` işleyicisi hemen durum penceresi temizler koddan sonra aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="06e67-139">In the `InstanceId_SelectedIndexChanged` handler, add the following code immediately after the code that clears the status window.</span></span>  
  
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
  
     <span data-ttu-id="06e67-140">Yeni bir iş akışı iş akışı listesinde seçildiğinde, izleme kayıtları için iş akışının yüklenir ve durum penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="06e67-140">When a new workflow is selected in the workflow list, the tracking records for that workflow are loaded and displayed in the status window.</span></span> <span data-ttu-id="06e67-141">Aşağıdaki örnek, tamamlanan, `InstanceId_SelectedIndexChanged` işleyici.</span><span class="sxs-lookup"><span data-stu-id="06e67-141">The following example is the completed `InstanceId_SelectedIndexChanged` handler.</span></span>  
  
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
  
###  <a name="BKMK_BuildAndRun"></a> <span data-ttu-id="06e67-142">Derleme ve uygulamayı çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="06e67-142">To build and run the application</span></span>  
  
1.  <span data-ttu-id="06e67-143">Uygulamayı oluşturmak için Ctrl + Shift + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="06e67-143">Press Ctrl+Shift+B to build the application.</span></span>  
  
2.  <span data-ttu-id="06e67-144">Uygulamayı başlatmak için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="06e67-144">Press Ctrl+F5 to start the application.</span></span>  
  
3.  <span data-ttu-id="06e67-145">Tahmin eden oyun ve başlangıç ve iş akışı türü için bir aralık seçmek **yeni oyun**.</span><span class="sxs-lookup"><span data-stu-id="06e67-145">Select a range for the guessing game and the type of workflow to start, and click **New Game**.</span></span> <span data-ttu-id="06e67-146">İçinde bir tahmin girin **tahmin** kutusuna ve tıklatın **Git** , tahmin göndermek için.</span><span class="sxs-lookup"><span data-stu-id="06e67-146">Enter a guess in the **Guess** box and click **Go** to submit your guess.</span></span> <span data-ttu-id="06e67-147">İş akışı durumu durum penceresinde görüntülendiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="06e67-147">Note that the status of the workflow is displayed in the status window.</span></span> <span data-ttu-id="06e67-148">Bu çıkış yakalanmıştır `WriteLine` etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="06e67-148">This output is captured from the `WriteLine` activities.</span></span> <span data-ttu-id="06e67-149">Geçiş için farklı bir iş akışı birini seçerek **iş akışı örnek kimliğini** birleşik giriş kutusu ve geçerli iş akışı durumunu kaldırıldığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="06e67-149">Switch to a different workflow by selecting one from the **Workflow Instance Id** combo box and note that the status of the current workflow is removed.</span></span> <span data-ttu-id="06e67-150">Önceki iş akışını ve durum, aşağıdaki örneğe benzer şekilde geri yüklendiğini Not dönün.</span><span class="sxs-lookup"><span data-stu-id="06e67-150">Switch back to the previous workflow and note that the status is restored, similar to the following example.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="06e67-151">İzleme etkinleştirilmeden önce başlatıldığından bir iş akışına geçiş yaparsanız yok durumu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="06e67-151">If you switch to a workflow that was started before tracking was enabled no status is displayed.</span></span> <span data-ttu-id="06e67-152">Ancak ek tahmin yaparsanız, izleme artık etkin olmadığından durumlarını kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="06e67-152">However if you make additional guesses, their status is saved because tracking is now enabled.</span></span>  
  
 <span data-ttu-id="06e67-153">**Lütfen 1 ile 10 arasında bir sayı girin**</span><span class="sxs-lookup"><span data-stu-id="06e67-153">**Please enter a number between 1 and 10**</span></span>  
<span data-ttu-id="06e67-154">**Çok yüksek tahmininizdir.** </span><span class="sxs-lookup"><span data-stu-id="06e67-154">**Your guess is too high.** </span></span>  
<span data-ttu-id="06e67-155">**Lütfen 1 ile 10 arasında bir sayı girin**</span><span class="sxs-lookup"><span data-stu-id="06e67-155">**Please enter a number between 1 and 10**</span></span>    

    > [!NOTE]
    >  <span data-ttu-id="06e67-156">Bu bilgiler, rastgele sayı aralığı belirlemek için yararlıdır, ancak daha önce yapılmış hangi tahmin hakkında bilgi içermiyor.</span><span class="sxs-lookup"><span data-stu-id="06e67-156">This information is useful for determining the range of the random number, but it does not contain any information about what guesses have been previously made.</span></span> <span data-ttu-id="06e67-157">Bu bilgiler sonraki adımda olan [nasıl yapılır: Bir iş akışı yan yana birden çok sürümünü konak](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span><span class="sxs-lookup"><span data-stu-id="06e67-157">This information is in the next step, [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>  
  
     <span data-ttu-id="06e67-158">İş akışı örnek kimliğini not edin ve kendi tamamlanana kadar oyun.</span><span class="sxs-lookup"><span data-stu-id="06e67-158">Make a note of the workflow instance id, and play the game through to its completion.</span></span>  
  
4.  <span data-ttu-id="06e67-159">Windows Gezgini'ni açın ve gidin **NumberGuessWorkflowHost\bin\debug** klasörü (veya **bin\release** proje ayarlarınıza bağlı olarak).</span><span class="sxs-lookup"><span data-stu-id="06e67-159">Open Windows Explorer and navigate to the **NumberGuessWorkflowHost\bin\debug** folder (or **bin\release** depending on your project settings).</span></span> <span data-ttu-id="06e67-160">Ek olarak proje dosyaları GUID adlarıyla yürütülebilir dosyalar olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="06e67-160">Note that in addition to the project executable files there are files with guid filenames.</span></span> <span data-ttu-id="06e67-161">Önceki adımda tamamlanan iş akışı'ndan iş akışı örneği kimliğine karşılık gelen bir belirleyin ve Not Defteri'nde açın.</span><span class="sxs-lookup"><span data-stu-id="06e67-161">Identify the one that corresponds to the workflow instance id from the completed workflow in the previous step and open it in Notepad.</span></span> <span data-ttu-id="06e67-162">İzleme bilgileri aşağıdaki gibi bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="06e67-162">The tracking information contains information similar to the following.</span></span>  
  
 <span data-ttu-id="06e67-163">**Lütfen 1 ile 10 arasında bir sayı girin**</span><span class="sxs-lookup"><span data-stu-id="06e67-163">**Please enter a number between 1 and 10**</span></span>  
<span data-ttu-id="06e67-164">**Çok yüksek tahmininizdir.** </span><span class="sxs-lookup"><span data-stu-id="06e67-164">**Your guess is too high.** </span></span>  
<span data-ttu-id="06e67-165">**Lütfen 1 ile 10 arasında bir sayı girin** </span><span class="sxs-lookup"><span data-stu-id="06e67-165">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="06e67-166">**Çok yüksek tahmininizdir.** </span><span class="sxs-lookup"><span data-stu-id="06e67-166">**Your guess is too high.** </span></span>  
<span data-ttu-id="06e67-167">**Lütfen 1 ile 10 arasında bir sayı girin** kullanıcının tahmin olmaması ek olarak, bu izleme verileri, iş akışının son tahmin hakkında bilgi içermiyor.</span><span class="sxs-lookup"><span data-stu-id="06e67-167">**Please enter a number between 1 and 10**      In addition to the absence of the user's guesses, this tracking data does not contain information about the final guess of the workflow.</span></span> <span data-ttu-id="06e67-168">İzleme bilgileri yalnızca oluşan çünkü `WriteLine` iş akışından çıkış ve görüntülenen son iletide nden yapılır `Completed` iş akışı tamamlandıktan sonra işleyici.</span><span class="sxs-lookup"><span data-stu-id="06e67-168">That is because the tracking information consists only of the `WriteLine` output from the workflow, and the final message that is displayed is done so from the `Completed` handler after the workflow completes.</span></span> <span data-ttu-id="06e67-169">Öğreticinin sonraki adımda [nasıl yapılır: Ana bilgisayar, bir iş akışı yan yana birden çok sürümünü](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md), varolan `WriteLine` etkinlikleri, kullanıcının tahminler ve ek görüntülenecek değiştirildiğinde `WriteLine` etkinliği, son sonuçları görüntüler eklenir.</span><span class="sxs-lookup"><span data-stu-id="06e67-169">In next step of the tutorial, [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md), the existing `WriteLine` activities are modified to display the user's guesses, and an additional `WriteLine` activity is added that displays the final results.</span></span> <span data-ttu-id="06e67-170">Bu değişiklikler tümleştirildikten sonra [nasıl yapılır: Ana bilgisayar, bir iş akışı yan yana birden çok sürümünü](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md) aynı anda birden çok iş akışı sürümünü barındırmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="06e67-170">After these changes are integrated, [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md) demonstrates how to host multiple versions of a workflow at the same time.</span></span>
