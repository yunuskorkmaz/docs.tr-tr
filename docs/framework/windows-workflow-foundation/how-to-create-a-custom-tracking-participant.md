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
# <a name="how-to-create-a-custom-tracking-participant"></a><span data-ttu-id="c68fe-102">Nasıl yapılır: Özel İzleme Katılımcısı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c68fe-102">How to: Create a Custom Tracking Participant</span></span>
<span data-ttu-id="c68fe-103">İş akışı izleme, iş akışı yürütme durumunun görünürlüğünü sağlar.</span><span class="sxs-lookup"><span data-stu-id="c68fe-103">Workflow tracking provides visibility into the status of workflow execution.</span></span> <span data-ttu-id="c68fe-104">İş akışı çalışma zamanı, iş akışı yaşam döngüsü olaylarını, etkinlik yaşam döngüsü olaylarını, yer işareti bağlantının sürdürülmesi ve hataları tanımlayan kayıt kayıtlarını yayar.</span><span class="sxs-lookup"><span data-stu-id="c68fe-104">The workflow runtime emits tracking records that describe workflow lifecycle events, activity lifecycle events, bookmark resumptions, and faults.</span></span> <span data-ttu-id="c68fe-105">Bu izleme kayıtları, katılımcıları izleme tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c68fe-105">These tracking records are consumed by tracking participants.</span></span> <span data-ttu-id="c68fe-106">Windows Workflow Foundation (WF), izleme kayıtlarını Windows için olay Izleme (ETW) olayları olarak yazan standart bir izleme katılımcısı içerir.</span><span class="sxs-lookup"><span data-stu-id="c68fe-106">Windows Workflow Foundation (WF) includes a standard tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span> <span data-ttu-id="c68fe-107">Gereksinimlerinizi karşılamıyorsa, özel bir izleme katılımcısı da yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c68fe-107">If that does not meet your requirements, you can also write a custom tracking participant.</span></span> <span data-ttu-id="c68fe-108">Bu öğretici adımında, kullanıcıya görüntülenebilmeleri için `WriteLine` etkinliklerin çıkışını yakalayan özel bir izleme katılımcısı ve izleme profili oluşturma açıklanır.</span><span class="sxs-lookup"><span data-stu-id="c68fe-108">This tutorial step describes how to create a custom tracking participant and tracking profile that capture the output of `WriteLine` activities so that they can be displayed to the user.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c68fe-109">Başlangıç öğreticisindeki her konu, önceki konulara bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="c68fe-109">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="c68fe-110">Bu konuyu tamamlayabilmeniz için, önce önceki konuları doldurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c68fe-110">To complete this topic, you must first complete the previous topics.</span></span> <span data-ttu-id="c68fe-111">Tamamlanmış bir sürümü indirmek veya öğreticiye ilişkin bir video kılavuzunu görüntülemek için, bkz. [Windows Workflow Foundation (WF45)-Başlangıç Öğreticisi](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="c68fe-111">To download a completed version or view a video walkthrough of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="to-create-the-custom-tracking-participant"></a><span data-ttu-id="c68fe-112">Özel izleme katılımcısını oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="c68fe-112">To create the custom tracking participant</span></span>  
  
1. <span data-ttu-id="c68fe-113">**Çözüm Gezgini** Için **Numberguessworkflowwhost** öğesine sağ tıklayın ve **Ekle**, **sınıf**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="c68fe-113">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **Class**.</span></span> <span data-ttu-id="c68fe-114">Ad `StatusTrackingParticipant` kutusuna yazın ve **Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c68fe-114">Type `StatusTrackingParticipant` into the **Name** box, and click **Add**.</span></span>  
  
2. <span data-ttu-id="c68fe-115">Aşağıdaki `using` (veya `Imports`) deyimlerini, diğer `using` (veya `Imports`) deyimleriyle dosyanın en üstüne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c68fe-115">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Activities.Tracking  
    Imports System.IO  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    using System.IO;  
    ```  
  
3. <span data-ttu-id="c68fe-116">Sınıfından devramının ardından `StatusTrackingParticipant` sınıfını değiştirin `TrackingParticipant`.</span><span class="sxs-lookup"><span data-stu-id="c68fe-116">Modify the `StatusTrackingParticipant` class so that it inherits from `TrackingParticipant`.</span></span>  
  
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
  
4. <span data-ttu-id="c68fe-117">Aşağıdaki `Track` yöntemi geçersiz kılmayı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c68fe-117">Add the following `Track` method override.</span></span> <span data-ttu-id="c68fe-118">Birkaç farklı izleme kaydı türü vardır.</span><span class="sxs-lookup"><span data-stu-id="c68fe-118">There are several different types of tracking records.</span></span> <span data-ttu-id="c68fe-119">Etkinlik izleme kayıtlarında bulunan `WriteLine` etkinliklerin çıkışı ile ilgileniyoruz.</span><span class="sxs-lookup"><span data-stu-id="c68fe-119">We are interested in the output of `WriteLine` activities, which are contained in activity tracking records.</span></span> <span data-ttu-id="c68fe-120">`ActivityTrackingRecord` `InstanceId` Bir etkinlik için `TrackingRecord` ise, öğesinin`WriteLine`, iş akışının öğesinden sonra adlı bir dosyaya eklenir. `Text` `WriteLine`</span><span class="sxs-lookup"><span data-stu-id="c68fe-120">If the `TrackingRecord` is an `ActivityTrackingRecord` for a `WriteLine` activity, the `Text` of the `WriteLine` is appended to a file named after the `InstanceId` of the workflow.</span></span> <span data-ttu-id="c68fe-121">Bu öğreticide, dosya, ana bilgisayar uygulamasının geçerli klasörüne kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="c68fe-121">In this tutorial, the file is saved to the current folder of the host application.</span></span>  
  
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
  
     <span data-ttu-id="c68fe-122">İzleme profili belirtilmediğinde, varsayılan izleme profili kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c68fe-122">When no tracking profile is specified, the default tracking profile is used.</span></span> <span data-ttu-id="c68fe-123">Varsayılan izleme profili kullanıldığında, izleme kayıtları tümü `ActivityStates`için yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="c68fe-123">When the default tracking profile is used, tracking records are emitted for all `ActivityStates`.</span></span> <span data-ttu-id="c68fe-124">`WriteLine` Etkinliğin yaşam döngüsü boyunca yalnızca bir kez metin yakalamamız gerektiğinden, yalnızca bu metni `ActivityStates.Executing` durumdan çıkaracağız.</span><span class="sxs-lookup"><span data-stu-id="c68fe-124">Because we only need to capture the text one time during the lifecycle of the `WriteLine` activity, we only extract the text from the `ActivityStates.Executing` state.</span></span> <span data-ttu-id="c68fe-125">[İzleme profili oluşturmak ve izleme katılımcısını kaydetmek için](#to-create-the-tracking-profile-and-register-the-tracking-participant)' de, yalnızca `WriteLine` `ActivityStates.Executing` izleme kayıtlarının yayıldığını belirten bir izleme profili oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c68fe-125">In [To create the tracking profile and register the tracking participant](#to-create-the-tracking-profile-and-register-the-tracking-participant), a tracking profile is created that specifies that only `WriteLine` `ActivityStates.Executing` tracking records are emitted.</span></span>  
  
## <a name="to-create-the-tracking-profile-and-register-the-tracking-participant"></a><span data-ttu-id="c68fe-126">İzleme profili oluşturma ve izleme katılımcısını kaydetme</span><span class="sxs-lookup"><span data-stu-id="c68fe-126">To create the tracking profile and register the tracking participant</span></span>  
  
1. <span data-ttu-id="c68fe-127">**Çözüm Gezgini** ' de **Workflowwhostform** öğesine sağ tıklayın ve **kodu görüntüle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="c68fe-127">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>  
  
2. <span data-ttu-id="c68fe-128">Aşağıdaki `using` (veya `Imports`) deyimini, diğer `using` (veya `Imports`) deyimleriyle dosyanın en üstüne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c68fe-128">Add the following `using` (or `Imports`) statement at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Activities.Tracking  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    ```  
  
3. <span data-ttu-id="c68fe-129">Aşağıdaki kodu `ConfigureWorkflowApplication` , `StringWriter` iş akışı uzantılarına ve iş akışı yaşam döngüsü işleyicilerinden önce ekleyen koddan hemen sonra ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c68fe-129">Add the following code to `ConfigureWorkflowApplication` just after the code that adds the `StringWriter` to the workflow extensions and before the workflow lifecycle handlers.</span></span>  
  
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
  
     <span data-ttu-id="c68fe-130">Bu izleme profili, yalnızca `WriteLine` `Executing` durumdaki etkinliklere ait etkinlik durumu kayıtlarının özel izleme katılımcısına yayınlandığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c68fe-130">This tracking profile specifies that only activity state records for `WriteLine` activities in the `Executing` state are emitted to the custom tracking participant.</span></span>  
  
     <span data-ttu-id="c68fe-131">Kodu ekledikten sonra, başlangıcı `ConfigureWorkflowApplication` aşağıdaki örneğe benzer şekilde görünür.</span><span class="sxs-lookup"><span data-stu-id="c68fe-131">After adding the code, the start of `ConfigureWorkflowApplication` will look like the following example.</span></span>  
  
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
  
## <a name="to-display-the-tracking-information"></a><span data-ttu-id="c68fe-132">İzleme bilgilerini görüntüleme</span><span class="sxs-lookup"><span data-stu-id="c68fe-132">To display the tracking information</span></span>  
  
1. <span data-ttu-id="c68fe-133">**Çözüm Gezgini** ' de **Workflowwhostform** öğesine sağ tıklayın ve **kodu görüntüle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="c68fe-133">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>  
  
2. <span data-ttu-id="c68fe-134">`InstanceId_SelectedIndexChanged` İşleyicisinde, durum penceresini temizleyen kodun hemen ardından aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c68fe-134">In the `InstanceId_SelectedIndexChanged` handler, add the following code immediately after the code that clears the status window.</span></span>  
  
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
  
     <span data-ttu-id="c68fe-135">İş akışı listesinde yeni bir iş akışı seçildiğinde, bu iş akışının izleme kayıtları yüklenir ve durum penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c68fe-135">When a new workflow is selected in the workflow list, the tracking records for that workflow are loaded and displayed in the status window.</span></span> <span data-ttu-id="c68fe-136">Aşağıdaki örnek, tamamlanan `InstanceId_SelectedIndexChanged` işleyicidir.</span><span class="sxs-lookup"><span data-stu-id="c68fe-136">The following example is the completed `InstanceId_SelectedIndexChanged` handler.</span></span>  
  
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
  
## <a name="to-build-and-run-the-application"></a><span data-ttu-id="c68fe-137">Uygulamayı derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="c68fe-137">To build and run the application</span></span>  
  
1. <span data-ttu-id="c68fe-138">Uygulamayı derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="c68fe-138">Press Ctrl+Shift+B to build the application.</span></span>  
  
2. <span data-ttu-id="c68fe-139">Uygulamayı başlatmak için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="c68fe-139">Press Ctrl+F5 to start the application.</span></span>  
  
3. <span data-ttu-id="c68fe-140">Tahmin etme oyunu ve başlatılacak iş akışı türü için bir Aralık seçin ve **yeni oyun**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c68fe-140">Select a range for the guessing game and the type of workflow to start, and click **New Game**.</span></span> <span data-ttu-id="c68fe-141">Tahmin kutusuna bir tahmin girin ve tahmininizi göndermek için **Git** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c68fe-141">Enter a guess in the **Guess** box and click **Go** to submit your guess.</span></span> <span data-ttu-id="c68fe-142">İş akışının durumunun durum penceresinde görüntülendiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c68fe-142">Note that the status of the workflow is displayed in the status window.</span></span> <span data-ttu-id="c68fe-143">Bu çıktı `WriteLine` etkinliklerden yakalanır.</span><span class="sxs-lookup"><span data-stu-id="c68fe-143">This output is captured from the `WriteLine` activities.</span></span> <span data-ttu-id="c68fe-144">**İş akışı örneği kimliği** açılan kutusundan birini seçerek farklı bir iş akışına geçin ve geçerli iş akışının durumunun kaldırıldığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c68fe-144">Switch to a different workflow by selecting one from the **Workflow Instance Id** combo box and note that the status of the current workflow is removed.</span></span> <span data-ttu-id="c68fe-145">Önceki iş akışına dönün ve durumun geri yüklendiğini, örneğin aşağıdaki örneğe benzer olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c68fe-145">Switch back to the previous workflow and note that the status is restored, similar to the following example.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c68fe-146">İzleme etkinleştirilmeden önce başlatılan bir iş akışına geçiş yaparsanız hiçbir durum gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="c68fe-146">If you switch to a workflow that was started before tracking was enabled no status is displayed.</span></span> <span data-ttu-id="c68fe-147">Ancak, ek tahminler yaparsanız, izleme artık etkinleştirildiğinden, durumları kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="c68fe-147">However if you make additional guesses, their status is saved because tracking is now enabled.</span></span>  
  
    ```output
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    ```
    
    > [!NOTE]
    > <span data-ttu-id="c68fe-148">Bu bilgiler, rastgele sayının aralığını belirlemek için faydalıdır, ancak daha önce hangi tahminlerin yapıldığını öğrenmek için bir bilgi içermez.</span><span class="sxs-lookup"><span data-stu-id="c68fe-148">This information is useful for determining the range of the random number, but it does not contain any information about what guesses have been previously made.</span></span> <span data-ttu-id="c68fe-149">Bu bilgiler sonraki adımda, [nasıl yapılır: Bir Iş akışının](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)birden çok sürümünü yan yana barındırın.</span><span class="sxs-lookup"><span data-stu-id="c68fe-149">This information is in the next step, [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>

    <span data-ttu-id="c68fe-150">İş akışı örnek kimliğini bir yere getirin ve oyunu tamamlamada yürütün.</span><span class="sxs-lookup"><span data-stu-id="c68fe-150">Make a note of the workflow instance id, and play the game through to its completion.</span></span>
  
4. <span data-ttu-id="c68fe-151">Windows Gezgini 'ni açın ve **Numberguessworkflowwhost\bin\debug** klasörüne (veya proje ayarlarınıza bağlı olarak **bin\release** ) gidin.</span><span class="sxs-lookup"><span data-stu-id="c68fe-151">Open Windows Explorer and navigate to the **NumberGuessWorkflowHost\bin\debug** folder (or **bin\release** depending on your project settings).</span></span> <span data-ttu-id="c68fe-152">Proje yürütülebilir dosyalarına ek olarak, GUID dosya adlarıyla dosya olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c68fe-152">Note that in addition to the project executable files there are files with guid filenames.</span></span> <span data-ttu-id="c68fe-153">Önceki adımda tamamlanan iş akışından iş akışı örneği kimliğine karşılık gelen bir tane belirler ve Not defteri 'nde açın.</span><span class="sxs-lookup"><span data-stu-id="c68fe-153">Identify the one that corresponds to the workflow instance id from the completed workflow in the previous step and open it in Notepad.</span></span> <span data-ttu-id="c68fe-154">İzleme bilgileri aşağıdakine benzer bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="c68fe-154">The tracking information contains information similar to the following.</span></span>  
  
    ```output
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    ```

    <span data-ttu-id="c68fe-155">Bu izleme verileri, kullanıcının tahminlerini yokluğuna ek olarak, iş akışının nihai tahminine ilişkin bilgiler içermez.</span><span class="sxs-lookup"><span data-stu-id="c68fe-155">In addition to the absence of the user's guesses, this tracking data does not contain information about the final guess of the workflow.</span></span> <span data-ttu-id="c68fe-156">Bunun nedeni, izleme bilgilerinin yalnızca `WriteLine` iş akışındaki çıktıyı ve görüntülenen son iletiyi, iş akışı tamamlandıktan sonra `Completed` işleyiciden yapılır.</span><span class="sxs-lookup"><span data-stu-id="c68fe-156">That is because the tracking information consists only of the `WriteLine` output from the workflow, and the final message that is displayed is done so from the `Completed` handler after the workflow completes.</span></span> <span data-ttu-id="c68fe-157">Öğreticinin sonraki adımında, [nasıl yapılır: Bir iş akışının](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)birden çok sürümünü yan yana barındırın, mevcut `WriteLine` etkinlikler kullanıcının tahminlerini görüntüleyecek şekilde değiştirilir ve nihai sonuçları görüntüleyen ek `WriteLine` bir etkinlik eklenir.</span><span class="sxs-lookup"><span data-stu-id="c68fe-157">In next step of the tutorial, [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md), the existing `WriteLine` activities are modified to display the user's guesses, and an additional `WriteLine` activity is added that displays the final results.</span></span> <span data-ttu-id="c68fe-158">Bu değişiklikler tümleşik [olduktan sonra: Bir iş akışının birden çok sürümünü yan yana](how-to-host-multiple-versions-of-a-workflow-side-by-side.md) barındırma bir iş akışının birden çok sürümünü aynı anda nasıl barındırabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="c68fe-158">After these changes are integrated, [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md) demonstrates how to host multiple versions of a workflow at the same time.</span></span>
