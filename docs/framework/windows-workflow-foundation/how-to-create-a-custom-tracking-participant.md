---
title: 'Nasıl yapılır: Özel İzleme Katılımcısı Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b612c7e-2381-4a7c-b07a-77030415f2a3
ms.openlocfilehash: 6fc8584b979c606a32e70e971be30a4bed89bdc2
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98190513"
---
# <a name="how-to-create-a-custom-tracking-participant"></a><span data-ttu-id="1d554-102">Nasıl yapılır: Özel İzleme Katılımcısı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1d554-102">How to: Create a Custom Tracking Participant</span></span>

<span data-ttu-id="1d554-103">İş akışı izleme, iş akışı yürütme durumunun görünürlüğünü sağlar.</span><span class="sxs-lookup"><span data-stu-id="1d554-103">Workflow tracking provides visibility into the status of workflow execution.</span></span> <span data-ttu-id="1d554-104">İş akışı çalışma zamanı, iş akışı yaşam döngüsü olaylarını, etkinlik yaşam döngüsü olaylarını, yer işareti bağlantının sürdürülmesi ve hataları tanımlayan kayıt kayıtlarını yayar.</span><span class="sxs-lookup"><span data-stu-id="1d554-104">The workflow runtime emits tracking records that describe workflow lifecycle events, activity lifecycle events, bookmark resumptions, and faults.</span></span> <span data-ttu-id="1d554-105">Bu izleme kayıtları, katılımcıları izleme tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1d554-105">These tracking records are consumed by tracking participants.</span></span> <span data-ttu-id="1d554-106">Windows Workflow Foundation (WF), izleme kayıtlarını Windows için olay Izleme (ETW) olayları olarak yazan standart bir izleme katılımcısı içerir.</span><span class="sxs-lookup"><span data-stu-id="1d554-106">Windows Workflow Foundation (WF) includes a standard tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span> <span data-ttu-id="1d554-107">Gereksinimlerinizi karşılamıyorsa, özel bir izleme katılımcısı da yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d554-107">If that does not meet your requirements, you can also write a custom tracking participant.</span></span> <span data-ttu-id="1d554-108">Bu öğretici adımında `WriteLine` , kullanıcıya görüntülenebilmeleri için etkinliklerin çıkışını yakalayan özel bir izleme katılımcısı ve izleme profili oluşturma açıklanır.</span><span class="sxs-lookup"><span data-stu-id="1d554-108">This tutorial step describes how to create a custom tracking participant and tracking profile that capture the output of `WriteLine` activities so that they can be displayed to the user.</span></span>  
  
## <a name="to-create-the-custom-tracking-participant"></a><span data-ttu-id="1d554-109">Özel izleme katılımcısını oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="1d554-109">To create the custom tracking participant</span></span>  
  
1. <span data-ttu-id="1d554-110">**Çözüm Gezgini** Için **Numberguessworkflowwhost** öğesine sağ tıklayın ve **Ekle**, **sınıf**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="1d554-110">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **Class**.</span></span> <span data-ttu-id="1d554-111">`StatusTrackingParticipant` **Ad** kutusuna yazın ve **Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="1d554-111">Type `StatusTrackingParticipant` into the **Name** box, and click **Add**.</span></span>  
  
2. <span data-ttu-id="1d554-112">Aşağıdaki `using` (veya `Imports` ) deyimlerini, diğer `using` (veya `Imports` ) deyimleriyle dosyanın en üstüne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1d554-112">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Activities.Tracking  
    Imports System.IO  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    using System.IO;  
    ```  
  
3. <span data-ttu-id="1d554-113">Sınıfından `StatusTrackingParticipant` devramının ardından sınıfını değiştirin `TrackingParticipant` .</span><span class="sxs-lookup"><span data-stu-id="1d554-113">Modify the `StatusTrackingParticipant` class so that it inherits from `TrackingParticipant`.</span></span>  
  
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
  
4. <span data-ttu-id="1d554-114">Aşağıdaki `Track` yöntemi geçersiz kılmayı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1d554-114">Add the following `Track` method override.</span></span> <span data-ttu-id="1d554-115">Birkaç farklı izleme kaydı türü vardır.</span><span class="sxs-lookup"><span data-stu-id="1d554-115">There are several different types of tracking records.</span></span> <span data-ttu-id="1d554-116">`WriteLine`Etkinlik izleme kayıtlarında bulunan etkinliklerin çıkışı ile ilgileniyoruz.</span><span class="sxs-lookup"><span data-stu-id="1d554-116">We are interested in the output of `WriteLine` activities, which are contained in activity tracking records.</span></span> <span data-ttu-id="1d554-117">Bir `TrackingRecord` `ActivityTrackingRecord` etkinlik için ise, öğesinin, `WriteLine` `Text` `WriteLine` iş akışının öğesinden sonra adlı bir dosyaya eklenir `InstanceId` .</span><span class="sxs-lookup"><span data-stu-id="1d554-117">If the `TrackingRecord` is an `ActivityTrackingRecord` for a `WriteLine` activity, the `Text` of the `WriteLine` is appended to a file named after the `InstanceId` of the workflow.</span></span> <span data-ttu-id="1d554-118">Bu öğreticide, dosya, ana bilgisayar uygulamasının geçerli klasörüne kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="1d554-118">In this tutorial, the file is saved to the current folder of the host application.</span></span>  
  
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
  
     <span data-ttu-id="1d554-119">İzleme profili belirtilmediğinde, varsayılan izleme profili kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1d554-119">When no tracking profile is specified, the default tracking profile is used.</span></span> <span data-ttu-id="1d554-120">Varsayılan izleme profili kullanıldığında, izleme kayıtları tümü için yayınlanır `ActivityStates` .</span><span class="sxs-lookup"><span data-stu-id="1d554-120">When the default tracking profile is used, tracking records are emitted for all `ActivityStates`.</span></span> <span data-ttu-id="1d554-121">Etkinliğin yaşam döngüsü boyunca yalnızca bir kez metin yakalamamız gerektiğinden `WriteLine` , yalnızca bu metni durumdan çıkaracağız `ActivityStates.Executing` .</span><span class="sxs-lookup"><span data-stu-id="1d554-121">Because we only need to capture the text one time during the lifecycle of the `WriteLine` activity, we only extract the text from the `ActivityStates.Executing` state.</span></span> <span data-ttu-id="1d554-122">[İzleme profili oluşturmak ve izleme katılımcısını kaydetmek için](#to-create-the-tracking-profile-and-register-the-tracking-participant)' de, yalnızca `WriteLine` `ActivityStates.Executing` izleme kayıtlarının yayıldığını belirten bir izleme profili oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1d554-122">In [To create the tracking profile and register the tracking participant](#to-create-the-tracking-profile-and-register-the-tracking-participant), a tracking profile is created that specifies that only `WriteLine` `ActivityStates.Executing` tracking records are emitted.</span></span>  
  
## <a name="to-create-the-tracking-profile-and-register-the-tracking-participant"></a><span data-ttu-id="1d554-123">İzleme profili oluşturma ve izleme katılımcısını kaydetme</span><span class="sxs-lookup"><span data-stu-id="1d554-123">To create the tracking profile and register the tracking participant</span></span>  
  
1. <span data-ttu-id="1d554-124">**Çözüm Gezgini** ' de **Workflowwhostform** öğesine sağ tıklayın ve **kodu görüntüle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="1d554-124">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>  
  
2. <span data-ttu-id="1d554-125">Aşağıdaki `using` (veya `Imports` ) deyimini, diğer `using` (veya `Imports` ) deyimleriyle dosyanın en üstüne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1d554-125">Add the following `using` (or `Imports`) statement at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Activities.Tracking  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    ```  
  
3. <span data-ttu-id="1d554-126">Aşağıdaki kodu `ConfigureWorkflowApplication` , `StringWriter` iş akışı uzantılarına ve iş akışı yaşam döngüsü işleyicilerinden önce ekleyen koddan hemen sonra ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1d554-126">Add the following code to `ConfigureWorkflowApplication` just after the code that adds the `StringWriter` to the workflow extensions and before the workflow lifecycle handlers.</span></span>  
  
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
  
     <span data-ttu-id="1d554-127">Bu izleme profili, yalnızca durumdaki etkinliklere ait etkinlik durumu kayıtlarının `WriteLine` `Executing` özel izleme katılımcısına yayınlandığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1d554-127">This tracking profile specifies that only activity state records for `WriteLine` activities in the `Executing` state are emitted to the custom tracking participant.</span></span>  
  
     <span data-ttu-id="1d554-128">Kodu ekledikten sonra, başlangıcı `ConfigureWorkflowApplication` aşağıdaki örneğe benzer şekilde görünür.</span><span class="sxs-lookup"><span data-stu-id="1d554-128">After adding the code, the start of `ConfigureWorkflowApplication` will look like the following example.</span></span>  
  
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
  
## <a name="to-display-the-tracking-information"></a><span data-ttu-id="1d554-129">İzleme bilgilerini görüntüleme</span><span class="sxs-lookup"><span data-stu-id="1d554-129">To display the tracking information</span></span>  
  
1. <span data-ttu-id="1d554-130">**Çözüm Gezgini** ' de **Workflowwhostform** öğesine sağ tıklayın ve **kodu görüntüle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="1d554-130">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>  
  
2. <span data-ttu-id="1d554-131">`InstanceId_SelectedIndexChanged`İşleyicisinde, durum penceresini temizleyen kodun hemen ardından aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1d554-131">In the `InstanceId_SelectedIndexChanged` handler, add the following code immediately after the code that clears the status window.</span></span>  
  
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
  
     <span data-ttu-id="1d554-132">İş akışı listesinde yeni bir iş akışı seçildiğinde, bu iş akışının izleme kayıtları yüklenir ve durum penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="1d554-132">When a new workflow is selected in the workflow list, the tracking records for that workflow are loaded and displayed in the status window.</span></span> <span data-ttu-id="1d554-133">Aşağıdaki örnek, tamamlanan `InstanceId_SelectedIndexChanged` işleyicidir.</span><span class="sxs-lookup"><span data-stu-id="1d554-133">The following example is the completed `InstanceId_SelectedIndexChanged` handler.</span></span>  
  
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
  
## <a name="to-build-and-run-the-application"></a><span data-ttu-id="1d554-134">Uygulamayı derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="1d554-134">To build and run the application</span></span>  
  
1. <span data-ttu-id="1d554-135">Uygulamayı derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="1d554-135">Press Ctrl+Shift+B to build the application.</span></span>  
  
2. <span data-ttu-id="1d554-136">Uygulamayı başlatmak için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="1d554-136">Press Ctrl+F5 to start the application.</span></span>  
  
3. <span data-ttu-id="1d554-137">Tahmin etme oyunu ve başlatılacak iş akışı türü için bir Aralık seçin ve **yeni oyun**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="1d554-137">Select a range for the guessing game and the type of workflow to start, and click **New Game**.</span></span> <span data-ttu-id="1d554-138">**Tahmin kutusuna bir** tahmin girin ve tahmininizi göndermek için **Git** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="1d554-138">Enter a guess in the **Guess** box and click **Go** to submit your guess.</span></span> <span data-ttu-id="1d554-139">İş akışının durumunun durum penceresinde görüntülendiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="1d554-139">Note that the status of the workflow is displayed in the status window.</span></span> <span data-ttu-id="1d554-140">Bu çıktı `WriteLine` etkinliklerden yakalanır.</span><span class="sxs-lookup"><span data-stu-id="1d554-140">This output is captured from the `WriteLine` activities.</span></span> <span data-ttu-id="1d554-141">**İş akışı örneği kimliği** açılan kutusundan birini seçerek farklı bir iş akışına geçin ve geçerli iş akışının durumunun kaldırıldığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="1d554-141">Switch to a different workflow by selecting one from the **Workflow Instance Id** combo box and note that the status of the current workflow is removed.</span></span> <span data-ttu-id="1d554-142">Önceki iş akışına dönün ve durumun geri yüklendiğini, örneğin aşağıdaki örneğe benzer olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="1d554-142">Switch back to the previous workflow and note that the status is restored, similar to the following example.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="1d554-143">İzleme etkinleştirilmeden önce başlatılan bir iş akışına geçiş yaparsanız hiçbir durum gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="1d554-143">If you switch to a workflow that was started before tracking was enabled no status is displayed.</span></span> <span data-ttu-id="1d554-144">Ancak, ek tahminler yaparsanız, izleme artık etkinleştirildiğinden, durumları kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="1d554-144">However if you make additional guesses, their status is saved because tracking is now enabled.</span></span>  
  
    ```output
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    ```

    > [!NOTE]
    > <span data-ttu-id="1d554-145">Bu bilgiler, rastgele sayının aralığını belirlemek için faydalıdır, ancak daha önce hangi tahminlerin yapıldığını öğrenmek için bir bilgi içermez.</span><span class="sxs-lookup"><span data-stu-id="1d554-145">This information is useful for determining the range of the random number, but it does not contain any information about what guesses have been previously made.</span></span> <span data-ttu-id="1d554-146">Bu bilgiler bir sonraki adımda, [nasıl yapılır: bir Iş akışının birden çok sürümünü yan yana barındırma](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span><span class="sxs-lookup"><span data-stu-id="1d554-146">This information is in the next step, [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>

    <span data-ttu-id="1d554-147">İş akışı örnek kimliğini bir yere getirin ve oyunu tamamlamada yürütün.</span><span class="sxs-lookup"><span data-stu-id="1d554-147">Make a note of the workflow instance id, and play the game through to its completion.</span></span>
  
4. <span data-ttu-id="1d554-148">Windows Gezgini 'ni açın ve **Numberguessworkflowwhost\bin\debug** klasörüne (veya proje ayarlarınıza bağlı olarak **bin\release** ) gidin.</span><span class="sxs-lookup"><span data-stu-id="1d554-148">Open Windows Explorer and navigate to the **NumberGuessWorkflowHost\bin\debug** folder (or **bin\release** depending on your project settings).</span></span> <span data-ttu-id="1d554-149">Proje yürütülebilir dosyalarına ek olarak, GUID dosya adlarıyla dosya olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="1d554-149">Note that in addition to the project executable files there are files with guid filenames.</span></span> <span data-ttu-id="1d554-150">Önceki adımda tamamlanan iş akışından iş akışı örneği kimliğine karşılık gelen bir tane belirler ve Not defteri 'nde açın.</span><span class="sxs-lookup"><span data-stu-id="1d554-150">Identify the one that corresponds to the workflow instance id from the completed workflow in the previous step and open it in Notepad.</span></span> <span data-ttu-id="1d554-151">İzleme bilgileri aşağıdakine benzer bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="1d554-151">The tracking information contains information similar to the following.</span></span>  
  
    ```output
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    ```

    <span data-ttu-id="1d554-152">Bu izleme verileri, kullanıcının tahminlerini yokluğuna ek olarak, iş akışının nihai tahminine ilişkin bilgiler içermez.</span><span class="sxs-lookup"><span data-stu-id="1d554-152">In addition to the absence of the user's guesses, this tracking data does not contain information about the final guess of the workflow.</span></span> <span data-ttu-id="1d554-153">Bunun nedeni, izleme bilgilerinin yalnızca `WriteLine` iş akışındaki çıktıyı ve görüntülenen son iletiyi, `Completed` iş akışı tamamlandıktan sonra işleyiciden yapılır.</span><span class="sxs-lookup"><span data-stu-id="1d554-153">That is because the tracking information consists only of the `WriteLine` output from the workflow, and the final message that is displayed is done so from the `Completed` handler after the workflow completes.</span></span> <span data-ttu-id="1d554-154">Öğreticinin bir sonraki adımında, [nasıl yapılır: bir Iş akışının birden çok sürümünü](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)yan yana barındırma, mevcut `WriteLine` Etkinlikler kullanıcının tahminlerini görüntüleyecek şekilde değiştirilir ve `WriteLine` nihai sonuçları görüntüleyen ek bir etkinlik eklenir.</span><span class="sxs-lookup"><span data-stu-id="1d554-154">In next step of the tutorial, [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md), the existing `WriteLine` activities are modified to display the user's guesses, and an additional `WriteLine` activity is added that displays the final results.</span></span> <span data-ttu-id="1d554-155">Bu değişiklikler tümleştirildiğinde, [nasıl yapılır: bir Iş akışının birden çok sürümünü](how-to-host-multiple-versions-of-a-workflow-side-by-side.md) yan yana barındırmak, bir iş akışının birden çok sürümünü aynı anda nasıl barındırabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="1d554-155">After these changes are integrated, [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md) demonstrates how to host multiple versions of a workflow at the same time.</span></span>
