---
title: "Nasıl yapılır: özel izleme katılımcı oluşturma"
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
ms.assetid: 1b612c7e-2381-4a7c-b07a-77030415f2a3
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 345fd696559ba52d41874ff774bd46a2d37f6e6f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-custom-tracking-participant"></a><span data-ttu-id="779c3-102">Nasıl yapılır: özel izleme katılımcı oluşturma</span><span class="sxs-lookup"><span data-stu-id="779c3-102">How to: Create a Custom Tracking Participant</span></span>
<span data-ttu-id="779c3-103">İş akışı izleme iş akışı yürütme durumu görünürlük sağlar.</span><span class="sxs-lookup"><span data-stu-id="779c3-103">Workflow tracking provides visibility into the status of workflow execution.</span></span> <span data-ttu-id="779c3-104">İş akışı çalışma zamanı iş akışı yaşam döngüsü olayları, etkinlik yaşam döngüsü olayları, yer işareti sürdürülmesi ve hataları açıklayan izleme kayıtları yayar.</span><span class="sxs-lookup"><span data-stu-id="779c3-104">The workflow runtime emits tracking records that describe workflow lifecycle events, activity lifecycle events, bookmark resumptions, and faults.</span></span> <span data-ttu-id="779c3-105">Bu izleme kayıtları katılımcıları izleme tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="779c3-105">These tracking records are consumed by tracking participants.</span></span> [!INCLUDE[wf](../../../includes/wf-md.md)]<span data-ttu-id="779c3-106">Olay izleme için Windows (ETW) olayları olarak izleme kayıtları yazan standart izleme katılımcı içerir.</span><span class="sxs-lookup"><span data-stu-id="779c3-106"> includes a standard tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span> <span data-ttu-id="779c3-107">Özel İzleme katılımcı Ayrıca, gereksinimlerinizi karşılamıyorsa yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="779c3-107">If that does not meet your requirements, you can also write a custom tracking participant.</span></span> <span data-ttu-id="779c3-108">Bu öğretici adım özel izleme katılımcı ve çıktısını yakalama izleme profili oluşturmayı açıklar `WriteLine` etkinlikleri böylece kullanıcıya gösterilir.</span><span class="sxs-lookup"><span data-stu-id="779c3-108">This tutorial step describes how to create a custom tracking participant and tracking profile that capture the output of `WriteLine` activities so that they can be displayed to the user.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="779c3-109">Başlarken Öğreticisi her bir konuda önceki konularda bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="779c3-109">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="779c3-110">Bu konuda tamamlamak için önce önceki konularını tamamlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="779c3-110">To complete this topic, you must first complete the previous topics.</span></span> <span data-ttu-id="779c3-111">Tamamlanmış sürümü indirme veya videosu öğreticinin görüntülemek için bkz: [Windows Workflow Foundation (WF45) - başlangıç Öğreticisi](http://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="779c3-111">To download a completed version or view a video walkthrough of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](http://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="in-this-topic"></a><span data-ttu-id="779c3-112">Bu konuda</span><span class="sxs-lookup"><span data-stu-id="779c3-112">In this topic</span></span>  
  
-   [<span data-ttu-id="779c3-113">Özel İzleme katılımcı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="779c3-113">To create the custom tracking participant</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_CustomTrackingParticipant)  
  
-   [<span data-ttu-id="779c3-114">İzleme profili oluşturma ve izleme katılımcı kaydetme</span><span class="sxs-lookup"><span data-stu-id="779c3-114">To create the tracking profile and register the tracking participant</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_TrackingProfile)  
  
-   [<span data-ttu-id="779c3-115">İzleme bilgilerini görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="779c3-115">To display the tracking information</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_DisplayTracking)  
  
-   [<span data-ttu-id="779c3-116">Derleme ve uygulamayı çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="779c3-116">To build and run the application</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_BuildAndRun)  
  
###  <a name="BKMK_CustomTrackingParticipant"></a><span data-ttu-id="779c3-117">Özel İzleme katılımcı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="779c3-117">To create the custom tracking participant</span></span>  
  
1.  <span data-ttu-id="779c3-118">Sağ **NumberGuessWorkflowHost** içinde **Çözüm Gezgini** ve **Ekle**, **sınıfı**.</span><span class="sxs-lookup"><span data-stu-id="779c3-118">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **Class**.</span></span> <span data-ttu-id="779c3-119">Tür `StatusTrackingParticipant` içine **adı** ve'ı tıklatın **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="779c3-119">Type `StatusTrackingParticipant` into the **Name** box, and click **Add**.</span></span>  
  
2.  <span data-ttu-id="779c3-120">Aşağıdakileri ekleyin `using` (veya `Imports`) diğer dosyanın en üstüne deyimlerini `using` (veya `Imports`) deyimleri.</span><span class="sxs-lookup"><span data-stu-id="779c3-120">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Activities.Tracking  
    Imports System.IO  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    using System.IO;  
    ```  
  
3.  <span data-ttu-id="779c3-121">Değiştirme `StatusTrackingParticipant` öğesinden devralınan sınıfının `TrackingParticipant`.</span><span class="sxs-lookup"><span data-stu-id="779c3-121">Modify the `StatusTrackingParticipant` class so that it inherits from `TrackingParticipant`.</span></span>  
  
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
  
4.  <span data-ttu-id="779c3-122">Aşağıdakileri ekleyin `Track` yöntemi geçersiz kılma.</span><span class="sxs-lookup"><span data-stu-id="779c3-122">Add the following `Track` method override.</span></span> <span data-ttu-id="779c3-123">Kayıtları İzleme birkaç farklı tür vardır.</span><span class="sxs-lookup"><span data-stu-id="779c3-123">There are several different types of tracking records.</span></span> <span data-ttu-id="779c3-124">Biz çıktısında ilgilendiğiniz `WriteLine` kayıtları izleme etkinlikte bulunan etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="779c3-124">We are interested in the output of `WriteLine` activities, which are contained in activity tracking records.</span></span> <span data-ttu-id="779c3-125">Varsa `TrackingRecord` olan bir `ActivityTrackingRecord` için bir `WriteLine` etkinliği `Text` , `WriteLine` sonra adlı bir dosyaya eklenir `InstanceId` iş akışı.</span><span class="sxs-lookup"><span data-stu-id="779c3-125">If the `TrackingRecord` is an `ActivityTrackingRecord` for a `WriteLine` activity, the `Text` of the `WriteLine` is appended to a file named after the `InstanceId` of the workflow.</span></span> <span data-ttu-id="779c3-126">Bu öğreticide, dosya geçerli ana bilgisayar uygulamasını klasörüne kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="779c3-126">In this tutorial, the file is saved to the current folder of the host application.</span></span>  
  
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
  
     <span data-ttu-id="779c3-127">İzleme profili belirtildiğinde, varsayılan profili izleme kullanılır.</span><span class="sxs-lookup"><span data-stu-id="779c3-127">When no tracking profile is specified, the default tracking profile is used.</span></span> <span data-ttu-id="779c3-128">Varsayılan profil izleme kullanıldığında, izleme kayıtları tüm gösterilen `ActivityStates`.</span><span class="sxs-lookup"><span data-stu-id="779c3-128">When the default tracking profile is used, tracking records are emitted for all `ActivityStates`.</span></span> <span data-ttu-id="779c3-129">Yalnızca bir kez yaşam döngüsü sırasında metni yakalamak ihtiyacımız çünkü `WriteLine` etkinlik, biz yalnızca Ayıkla metinden `ActivityStates.Executing` durumu.</span><span class="sxs-lookup"><span data-stu-id="779c3-129">Because we only need to capture the text one time during the lifecycle of the `WriteLine` activity, we only extract the text from the `ActivityStates.Executing` state.</span></span> <span data-ttu-id="779c3-130">İçinde [izleme profili oluşturma ve izleme katılımcı kaydetme](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_TrackingProfile), yalnızca belirten bir izleme profili oluşturulur `WriteLine` `ActivityStates.Executing` izleme kayıtları yayılan.</span><span class="sxs-lookup"><span data-stu-id="779c3-130">In [To create the tracking profile and register the tracking participant](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_TrackingProfile), a tracking profile is created that specifies that only `WriteLine` `ActivityStates.Executing` tracking records are emitted.</span></span>  
  
###  <a name="BKMK_TrackingProfile"></a><span data-ttu-id="779c3-131">İzleme profili oluşturma ve izleme katılımcı kaydetme</span><span class="sxs-lookup"><span data-stu-id="779c3-131">To create the tracking profile and register the tracking participant</span></span>  
  
1.  <span data-ttu-id="779c3-132">Sağ **WorkflowHostForm** içinde **Çözüm Gezgini** ve **görünümü kodu**.</span><span class="sxs-lookup"><span data-stu-id="779c3-132">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>  
  
2.  <span data-ttu-id="779c3-133">Aşağıdakileri ekleyin `using` (veya `Imports`) deyimini dosyanın üst kısmındaki diğer `using` (veya `Imports`) deyimleri.</span><span class="sxs-lookup"><span data-stu-id="779c3-133">Add the following `using` (or `Imports`) statement at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Activities.Tracking  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    ```  
  
3.  <span data-ttu-id="779c3-134">Aşağıdaki kodu ekleyin `ConfigureWorkflowApplication` ekleyen koddan sonra `StringWriter` iş akışı uzantıları ve iş akışı yaşam döngüsü işleyicileri önce.</span><span class="sxs-lookup"><span data-stu-id="779c3-134">Add the following code to `ConfigureWorkflowApplication` just after the code that adds the `StringWriter` to the workflow extensions and before the workflow lifecycle handlers.</span></span>  
  
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
  
     <span data-ttu-id="779c3-135">Bu izleme profili yalnızca etkinlik durumu için kaydeder belirten `WriteLine` aktivitelerde `Executing` durumu özel izleme katılımcı yayılan.</span><span class="sxs-lookup"><span data-stu-id="779c3-135">This tracking profile specifies that only activity state records for `WriteLine` activities in the `Executing` state are emitted to the custom tracking participant.</span></span>  
  
     <span data-ttu-id="779c3-136">Başlangıç kodu ekledikten sonra `ConfigureWorkflowApplication` aşağıdaki gibi görünür.</span><span class="sxs-lookup"><span data-stu-id="779c3-136">After adding the code, the start of `ConfigureWorkflowApplication` will look like the following example.</span></span>  
  
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
  
###  <a name="BKMK_DisplayTracking"></a><span data-ttu-id="779c3-137">İzleme bilgilerini görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="779c3-137">To display the tracking information</span></span>  
  
1.  <span data-ttu-id="779c3-138">Sağ **WorkflowHostForm** içinde **Çözüm Gezgini** ve **görünümü kodu**.</span><span class="sxs-lookup"><span data-stu-id="779c3-138">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>  
  
2.  <span data-ttu-id="779c3-139">İçinde `InstanceId_SelectedIndexChanged` işleyici, hemen durum penceresi temizler koddan sonra aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="779c3-139">In the `InstanceId_SelectedIndexChanged` handler, add the following code immediately after the code that clears the status window.</span></span>  
  
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
  
     <span data-ttu-id="779c3-140">Yeni bir iş akışı iş akışı listesinde seçili olduğunda, iş akışının izleme kayıtları yüklenen ve durum penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="779c3-140">When a new workflow is selected in the workflow list, the tracking records for that workflow are loaded and displayed in the status window.</span></span> <span data-ttu-id="779c3-141">Aşağıdaki örnekte tamamlanmış olan `InstanceId_SelectedIndexChanged` işleyici.</span><span class="sxs-lookup"><span data-stu-id="779c3-141">The following example is the completed `InstanceId_SelectedIndexChanged` handler.</span></span>  
  
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
  
###  <a name="BKMK_BuildAndRun"></a><span data-ttu-id="779c3-142">Derleme ve uygulamayı çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="779c3-142">To build and run the application</span></span>  
  
1.  <span data-ttu-id="779c3-143">Uygulamanızı oluşturmak için Ctrl + Shift + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="779c3-143">Press Ctrl+Shift+B to build the application.</span></span>  
  
2.  <span data-ttu-id="779c3-144">Uygulamayı başlatmak için CTRL + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="779c3-144">Press Ctrl+F5 to start the application.</span></span>  
  
3.  <span data-ttu-id="779c3-145">Tahmin eden oyun ve başlatın ve iş akışı türü için bir aralık seçmek **yeni oyun**.</span><span class="sxs-lookup"><span data-stu-id="779c3-145">Select a range for the guessing game and the type of workflow to start, and click **New Game**.</span></span> <span data-ttu-id="779c3-146">Bir tahmin girin **tahmin** kutusuna ve tıklatın **Git** , tahmin göndermek için.</span><span class="sxs-lookup"><span data-stu-id="779c3-146">Enter a guess in the **Guess** box and click **Go** to submit your guess.</span></span> <span data-ttu-id="779c3-147">İş akışının durumunu durum penceresinde görüntülendiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="779c3-147">Note that the status of the workflow is displayed in the status window.</span></span> <span data-ttu-id="779c3-148">Bu çıktı gelen yakalanan `WriteLine` etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="779c3-148">This output is captured from the `WriteLine` activities.</span></span> <span data-ttu-id="779c3-149">Geçiş için farklı bir iş akışı birinden seçerek **iş akışı örneği kimliği** birleşik giriş kutusu ve geçerli iş akışının durumunu kaldırdığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="779c3-149">Switch to a different workflow by selecting one from the **Workflow Instance Id** combo box and note that the status of the current workflow is removed.</span></span> <span data-ttu-id="779c3-150">Durum, aşağıdaki örneğe benzer şekilde geri yüklendiğini Not ve önceki iş akışı için dönün.</span><span class="sxs-lookup"><span data-stu-id="779c3-150">Switch back to the previous workflow and note that the status is restored, similar to the following example.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="779c3-151">İzleme etkinleştirilmeden önce başlatılan bir iş akışı için geçiş yaparsanız yok durumu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="779c3-151">If you switch to a workflow that was started before tracking was enabled no status is displayed.</span></span> <span data-ttu-id="779c3-152">Ancak ek tahmin yaparsanız, izleme artık etkin olmadığından durumlarını kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="779c3-152">However if you make additional guesses, their status is saved because tracking is now enabled.</span></span>  
  
 <span data-ttu-id="779c3-153">**Lütfen 1 ile 10 arasında bir sayı girin**</span><span class="sxs-lookup"><span data-stu-id="779c3-153">**Please enter a number between 1 and 10**</span></span>  
<span data-ttu-id="779c3-154">**Tahmin çok yüksektir.** </span><span class="sxs-lookup"><span data-stu-id="779c3-154">**Your guess is too high.** </span></span>  
<span data-ttu-id="779c3-155">**Lütfen 1 ile 10 arasında bir sayı girin**</span><span class="sxs-lookup"><span data-stu-id="779c3-155">**Please enter a number between 1 and 10**</span></span>    
    > [!NOTE]
    >  <span data-ttu-id="779c3-156">Bu bilgiler, rastgele sayı aralığı belirlemede yararlıdır, ancak hangi tahmin daha önce yaptığınız hakkında bilgi içermiyor.</span><span class="sxs-lookup"><span data-stu-id="779c3-156">This information is useful for determining the range of the random number, but it does not contain any information about what guesses have been previously made.</span></span> <span data-ttu-id="779c3-157">Bu bilgiler sonraki adımda olduğu [nasıl yapılır: bir iş akışı yan yana birden fazla sürümünü konak](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span><span class="sxs-lookup"><span data-stu-id="779c3-157">This information is in the next step, [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>  
  
     <span data-ttu-id="779c3-158">İş akışı örneği kimliği not edin ve onun tamamlanıncaya kadar oyun.</span><span class="sxs-lookup"><span data-stu-id="779c3-158">Make a note of the workflow instance id, and play the game through to its completion.</span></span>  
  
4.  <span data-ttu-id="779c3-159">Windows Gezgini'ni açın ve gidin **NumberGuessWorkflowHost\bin\debug** klasörü (veya **bin\release** proje ayarlarınızı bağlı olarak).</span><span class="sxs-lookup"><span data-stu-id="779c3-159">Open Windows Explorer and navigate to the **NumberGuessWorkflowHost\bin\debug** folder (or **bin\release** depending on your project settings).</span></span> <span data-ttu-id="779c3-160">Ek olarak proje GUID dosya adları dosyalarıyla yürütülebilir dosya olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="779c3-160">Note that in addition to the project executable files there are files with guid filenames.</span></span> <span data-ttu-id="779c3-161">Önceki adımda tamamlanmış iş akışından iş akışı örneği kimliğine karşılık gelen bir belirleyin ve Not Defteri'nde açın.</span><span class="sxs-lookup"><span data-stu-id="779c3-161">Identify the one that corresponds to the workflow instance id from the completed workflow in the previous step and open it in Notepad.</span></span> <span data-ttu-id="779c3-162">İzleme bilgileri aşağıdakine benzer bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="779c3-162">The tracking information contains information similar to the following.</span></span>  
  
 <span data-ttu-id="779c3-163">**Lütfen 1 ile 10 arasında bir sayı girin**</span><span class="sxs-lookup"><span data-stu-id="779c3-163">**Please enter a number between 1 and 10**</span></span>  
<span data-ttu-id="779c3-164">**Tahmin çok yüksektir.** </span><span class="sxs-lookup"><span data-stu-id="779c3-164">**Your guess is too high.** </span></span>  
<span data-ttu-id="779c3-165">**Lütfen 1 ile 10 arasında bir sayı girin** </span><span class="sxs-lookup"><span data-stu-id="779c3-165">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="779c3-166">**Tahmin çok yüksektir.** </span><span class="sxs-lookup"><span data-stu-id="779c3-166">**Your guess is too high.** </span></span>  
<span data-ttu-id="779c3-167">**Lütfen 1 ile 10 arasında bir sayı girin** kullanıcının tahmin olmaması ek olarak, bu izleme verilerine iş akışının son tahmin hakkında bilgi içermiyor.</span><span class="sxs-lookup"><span data-stu-id="779c3-167">**Please enter a number between 1 and 10**      In addition to the absence of the user's guesses, this tracking data does not contain information about the final guess of the workflow.</span></span> <span data-ttu-id="779c3-168">İzleme bilgileri yalnızca oluşan çünkü `WriteLine` iş akışından çıkış ve görüntülenen son iletisi nden yapılır `Completed` iş akışı tamamlandığında işleyici.</span><span class="sxs-lookup"><span data-stu-id="779c3-168">That is because the tracking information consists only of the `WriteLine` output from the workflow, and the final message that is displayed is done so from the `Completed` handler after the workflow completes.</span></span> <span data-ttu-id="779c3-169">Öğreticinin sonraki adımda [nasıl yapılır: bir iş akışı yan yana birden fazla sürümünü konak](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md), varolan `WriteLine` etkinlikleri kullanıcının tahmin ve ek bir görüntülemek için değiştirildiğinde `WriteLine` etkinlik, eklenir Son sonuçlarını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="779c3-169">In next step of the tutorial, [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md), the existing `WriteLine` activities are modified to display the user's guesses, and an additional `WriteLine` activity is added that displays the final results.</span></span> <span data-ttu-id="779c3-170">Bu değişiklikler tümleşik sonra [nasıl yapılır: bir iş akışı yan yana birden fazla sürümünü konak](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md) aynı anda birden çok iş akışı sürümü barındırmak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="779c3-170">After these changes are integrated, [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md) demonstrates how to host multiple versions of a workflow at the same time.</span></span>
