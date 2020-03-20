---
title: Özel İzleme
ms.date: 03/30/2017
ms.assetid: 2d191c9f-62f4-4c63-92dd-cda917fcf254
ms.openlocfilehash: 2b100b877bbc8c6d830f09a4a59decffde511511
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182847"
---
# <a name="custom-tracking"></a><span data-ttu-id="39bb4-102">Özel İzleme</span><span class="sxs-lookup"><span data-stu-id="39bb4-102">Custom Tracking</span></span>
<span data-ttu-id="39bb4-103">Bu örnek, özel bir izleme katılımcısının nasıl oluşturulup izleme verilerinin içeriğini konsola nasıl yazılabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="39bb4-103">This sample demonstrates how to create a custom tracking participant and write the contents of the tracking data to console.</span></span> <span data-ttu-id="39bb4-104">Buna ek olarak, örnek, kullanıcı <xref:System.Activities.Tracking.CustomTrackingRecord> tanımlı verilerle doldurulan nesneleri nasıl yayıştırılabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="39bb4-104">In addition, the sample demonstrates how to emit <xref:System.Activities.Tracking.CustomTrackingRecord> objects populated with user defined data.</span></span> <span data-ttu-id="39bb4-105">Konsol tabanlı izleme katılımcısı, <xref:System.Activities.Tracking.TrackingRecord> kodda oluşturulan bir izleme profili nesnesini kullanarak iş akışıtarafından yayılan nesneleri filtreler.</span><span class="sxs-lookup"><span data-stu-id="39bb4-105">The console-based tracking participant filters the <xref:System.Activities.Tracking.TrackingRecord> objects emitted by the workflow using a tracking profile object created in code.</span></span>

## <a name="sample-details"></a><span data-ttu-id="39bb4-106">Örnek Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="39bb4-106">Sample Details</span></span>
 <span data-ttu-id="39bb4-107">Windows İş Akışı Temeli (WF), iş akışı örneğinin yürütülmesini izlemek için bir izleme altyapısı sağlar.</span><span class="sxs-lookup"><span data-stu-id="39bb4-107">Windows Workflow Foundation (WF) provides a tracking infrastructure to track execution of a workflow instance.</span></span> <span data-ttu-id="39bb4-108">İzleme çalışma zamanı, iş akışı yaşam döngüsüyle ilgili olayları, iş akışı etkinliklerinden olayları ve özel izleme olaylarını yalamak için bir iş akışı örneği uygular.</span><span class="sxs-lookup"><span data-stu-id="39bb4-108">The tracking runtime implements a workflow instance to emit events related to the workflow lifecycle, events from workflow activities and custom tracking events.</span></span> <span data-ttu-id="39bb4-109">Aşağıdaki tabloizleme altyapısının birincil bileşenlerini ayrıntılarıyla anlatır.</span><span class="sxs-lookup"><span data-stu-id="39bb4-109">The following table details the primary components of the tracking infrastructure.</span></span>

|<span data-ttu-id="39bb4-110">Bileşen</span><span class="sxs-lookup"><span data-stu-id="39bb4-110">Component</span></span>|<span data-ttu-id="39bb4-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="39bb4-111">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="39bb4-112">Çalışma süresini izleme</span><span class="sxs-lookup"><span data-stu-id="39bb4-112">Tracking runtime</span></span>|<span data-ttu-id="39bb4-113">İzleme kayıtlarını yayışacak altyapıyı sağlar.</span><span class="sxs-lookup"><span data-stu-id="39bb4-113">Provides the infrastructure to emit tracking records.</span></span>|
|<span data-ttu-id="39bb4-114">Katılımcıları izleme</span><span class="sxs-lookup"><span data-stu-id="39bb4-114">Tracking participants</span></span>|<span data-ttu-id="39bb4-115">İzleme kayıtlarını tüketir.</span><span class="sxs-lookup"><span data-stu-id="39bb4-115">Consumes the tracking records.</span></span> <span data-ttu-id="39bb4-116">.NET Framework 4, Windows (ETW) olayları için Olay İzleme olarak izleme kayıtları yazan bir izleme katılımcısıyla birlikte gemiler.</span><span class="sxs-lookup"><span data-stu-id="39bb4-116">.NET Framework 4 ships with a tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span>|
|<span data-ttu-id="39bb4-117">İzleme profili</span><span class="sxs-lookup"><span data-stu-id="39bb4-117">Tracking profile</span></span>|<span data-ttu-id="39bb4-118">İzleme katılımcısının iş akışı örneğinden yayılan izleme kayıtlarının bir alt kümesine abone olmasını sağlayan bir filtreleme mekanizması.</span><span class="sxs-lookup"><span data-stu-id="39bb4-118">A filtering mechanism that allows a tracking participant to subscribe for a subset of the tracking records emitted from a workflow instance.</span></span>|

 <span data-ttu-id="39bb4-119">Aşağıdaki tablo, iş akışı çalışma zamanının yayıştığı izleme kayıtlarını ayrıntılarıyla tamamlar.</span><span class="sxs-lookup"><span data-stu-id="39bb4-119">The following table details the tracking records that the workflow runtime emits.</span></span>

|<span data-ttu-id="39bb4-120">İzleme Kaydı</span><span class="sxs-lookup"><span data-stu-id="39bb4-120">Tracking Record</span></span>|<span data-ttu-id="39bb4-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="39bb4-121">Description</span></span>|
|---------------------|-----------------|
|<span data-ttu-id="39bb4-122">İş akışı örneği izleme kayıtları.</span><span class="sxs-lookup"><span data-stu-id="39bb4-122">Workflow instance tracking records.</span></span>|<span data-ttu-id="39bb4-123">İş akışı örneğinin yaşam döngüsünü açıklar.</span><span class="sxs-lookup"><span data-stu-id="39bb4-123">Describes the life cycle of the workflow instance.</span></span> <span data-ttu-id="39bb4-124">Örneğin, iş akışı başladığında veya tamamlandığında bir örnek kaydı yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="39bb4-124">For example, an instance record is emitted when the workflow starts or completes.</span></span>|
|<span data-ttu-id="39bb4-125">Etkinlik durumu İzleme Kayıtları.</span><span class="sxs-lookup"><span data-stu-id="39bb4-125">Activity state Tracking Records.</span></span>|<span data-ttu-id="39bb4-126">Ayrıntılar etkinlik yürütme.</span><span class="sxs-lookup"><span data-stu-id="39bb4-126">Details activity execution.</span></span> <span data-ttu-id="39bb4-127">Bu kayıtlar, bir etkinliğin zamanlandığında, etkinlik tamamlandığında veya bir hata atıldığında olduğu gibi bir iş akışı etkinliğinin durumunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="39bb4-127">These records indicate the state of a workflow activity such as when an activity is scheduled or when the activity completes or when a fault is thrown.</span></span>|
|<span data-ttu-id="39bb4-128">Yer imi yeniden kayıt.</span><span class="sxs-lookup"><span data-stu-id="39bb4-128">Bookmark resumption record.</span></span>|<span data-ttu-id="39bb4-129">İş akışı örneği içindeki yer imi devam ettiğinde yayılan.</span><span class="sxs-lookup"><span data-stu-id="39bb4-129">Emitted whenever a bookmark within a workflow instance is resumed.</span></span>|
|<span data-ttu-id="39bb4-130">Özel Takip Kayıtları.</span><span class="sxs-lookup"><span data-stu-id="39bb4-130">Custom Tracking Records.</span></span>|<span data-ttu-id="39bb4-131">İş akışı yazarı Özel İzleme Kayıtları oluşturabilir ve bunları özel etkinlik içinde yarayabilir.</span><span class="sxs-lookup"><span data-stu-id="39bb4-131">A workflow author can create Custom Tracking Records and emit them within the custom activity.</span></span>|

 <span data-ttu-id="39bb4-132">İzleme katılımcısı, izleme profillerini kullanarak yayılan <xref:System.Activities.Tracking.TrackingRecord> nesnelerin bir alt kümesine abone olur.</span><span class="sxs-lookup"><span data-stu-id="39bb4-132">The tracking participant subscribes for a subset of the emitted <xref:System.Activities.Tracking.TrackingRecord> objects using tracking profiles.</span></span> <span data-ttu-id="39bb4-133">İzleme profili, belirli bir izleme kaydı türüne abone olmak için izleme sorguları içerir.</span><span class="sxs-lookup"><span data-stu-id="39bb4-133">A tracking profile contains tracking queries that allow subscribing for a particular tracking record type.</span></span> <span data-ttu-id="39bb4-134">İzleme profilleri kodda veya yapılandırmada belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="39bb4-134">Tracking profiles can be specified in code or in configuration.</span></span>

### <a name="custom-tracking-participant"></a><span data-ttu-id="39bb4-135">Özel İzleme Katılımcısı</span><span class="sxs-lookup"><span data-stu-id="39bb4-135">Custom Tracking Participant</span></span>
 <span data-ttu-id="39bb4-136">İzleme katılımcısı API, iş akışı çalışma zamanı tarafından yayılan nesneleri işlemek <xref:System.Activities.Tracking.TrackingRecord> için özel mantık içerebilen bir kullanıcı tarafından sağlanan izleme katılımcısı ile izleme çalışma süresinin uzatılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="39bb4-136">The tracking participant API allows extension of the tracking runtime with a user provided tracking participant that can include custom logic to handle <xref:System.Activities.Tracking.TrackingRecord> objects emitted by the workflow runtime.</span></span>

 <span data-ttu-id="39bb4-137">Bir izleme katılımcısı yazmak <xref:System.Activities.Tracking.TrackingParticipant>için kullanıcının uygulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="39bb4-137">To write a tracking participant the user must implement <xref:System.Activities.Tracking.TrackingParticipant>.</span></span> <span data-ttu-id="39bb4-138">Özellikle, <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> yöntem özel katılımcı tarafından uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="39bb4-138">Specifically, the <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> method has to be implemented by the custom participant.</span></span> <span data-ttu-id="39bb4-139">İş akışı çalışma <xref:System.Activities.Tracking.TrackingRecord> zamanı tarafından yayılan bir yöntem denir.</span><span class="sxs-lookup"><span data-stu-id="39bb4-139">This method is called when a <xref:System.Activities.Tracking.TrackingRecord> is emitted by the workflow runtime.</span></span>

```csharp
public abstract class TrackingParticipant
{
    protected TrackingParticipant();

    public virtual TrackingProfile TrackingProfile { get; set; }
    public abstract void Track(TrackingRecord record, TimeSpan timeout);
}
```

 <span data-ttu-id="39bb4-140">Tam izleme katılımcısı ConsoleTrackingParticipant.cs dosyasında uygulanır.</span><span class="sxs-lookup"><span data-stu-id="39bb4-140">The complete tracking participant is implemented in the ConsoleTrackingParticipant.cs file.</span></span> <span data-ttu-id="39bb4-141">Aşağıdaki kod örneği, <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> özel izleme katılımcısı için yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="39bb4-141">The following code example is the <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> method for the custom tracking participant.</span></span>

```csharp
protected override void Track(TrackingRecord record, TimeSpan timeout)
{
    ...
    WorkflowInstanceRecord workflowInstanceRecord = record as WorkflowInstanceRecord;
    if (workflowInstanceRecord != null)
    {
        Console.WriteLine(String.Format(CultureInfo.InvariantCulture,
            " Workflow InstanceID: {0} Workflow instance state: {1}",
            record.InstanceId, workflowInstanceRecord.State));
    }

    ActivityStateRecord activityStateRecord = record as ActivityStateRecord;
    if (activityStateRecord != null)
    {
        IDictionary<String, object> variables = activityStateRecord.Variables;
        StringBuilder vars = new StringBuilder();

        if (variables.Count > 0)
        {
            vars.AppendLine("\n\tVariables:");
            foreach (KeyValuePair<string, object> variable in variables)
            {
                vars.AppendLine(String.Format(
                    "\t\tName: {0} Value: {1}", variable.Key, variable.Value));
            }
        }
        Console.WriteLine(String.Format(CultureInfo.InvariantCulture,
            " :Activity DisplayName: {0} :ActivityInstanceState: {1} {2}",
                activityStateRecord.Activity.Name, activityStateRecord.State,
            ((variables.Count > 0) ? vars.ToString() : String.Empty)));
    }

    CustomTrackingRecord customTrackingRecord = record as CustomTrackingRecord;

    if ((customTrackingRecord != null) && (customTrackingRecord.Data.Count > 0))
    {
        ...
    }
    Console.WriteLine();

}
```

 <span data-ttu-id="39bb4-142">Aşağıdaki kod örneği, konsol katılımcısını iş akışı çağıranına ekler.</span><span class="sxs-lookup"><span data-stu-id="39bb4-142">The following code example adds the console participant to the workflow invoker.</span></span>

```csharp
ConsoleTrackingParticipant customTrackingParticipant = new ConsoleTrackingParticipant()
{
    ...
    // The tracking profile is set here, refer to Program.CS
...
}

WorkflowInvoker invoker = new WorkflowInvoker(BuildSampleWorkflow());
invoker.Extensions.Add(customTrackingParticipant);
```

### <a name="emitting-custom-tracking-records"></a><span data-ttu-id="39bb4-143">Özel İzleme Kayıtları Yayan</span><span class="sxs-lookup"><span data-stu-id="39bb4-143">Emitting Custom Tracking Records</span></span>
 <span data-ttu-id="39bb4-144">Bu örnek, özel bir iş <xref:System.Activities.Tracking.CustomTrackingRecord> akışı etkinliğinden nesneleri yayış yeteneğini de gösterir:</span><span class="sxs-lookup"><span data-stu-id="39bb4-144">This sample also demonstrates the ability to emit <xref:System.Activities.Tracking.CustomTrackingRecord> objects from a custom workflow activity:</span></span>

- <span data-ttu-id="39bb4-145">Nesneler <xref:System.Activities.Tracking.CustomTrackingRecord> oluşturulur ve kayıt la birlikte yayımlamak istenen kullanıcı tanımlı verilerle doldurulur.</span><span class="sxs-lookup"><span data-stu-id="39bb4-145">The <xref:System.Activities.Tracking.CustomTrackingRecord> objects are created and populated with user-defined data that is desired to be emitted with the record.</span></span>

- <span data-ttu-id="39bb4-146">The' nin <xref:System.Activities.Tracking.CustomTrackingRecord> parça metodu çağrılarak <xref:System.Activities.ActivityContext>yayılır.</span><span class="sxs-lookup"><span data-stu-id="39bb4-146">The <xref:System.Activities.Tracking.CustomTrackingRecord> is emitted by calling the track method of the <xref:System.Activities.ActivityContext>.</span></span>

 <span data-ttu-id="39bb4-147">Aşağıdaki örnek, özel bir etkinlik <xref:System.Activities.Tracking.CustomTrackingRecord> içinde nesnelerin nasıl yayıltılabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="39bb4-147">The following example demonstrates how to emit <xref:System.Activities.Tracking.CustomTrackingRecord> objects within a custom activity.</span></span>

```csharp
// Create the Custom Tracking Record
CustomTrackingRecord customRecord = new CustomTrackingRecord("OrderIn")
{
    Data =
    {
        {"OrderId", 200},
        {"OrderDate", "20 Aug 2001"}
    }
};

// Emit custom tracking record
context.Track(customRecord);
```

#### <a name="to-use-this-sample"></a><span data-ttu-id="39bb4-148">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="39bb4-148">To use this sample</span></span>

1. <span data-ttu-id="39bb4-149">Visual Studio 2010'u kullanarak CustomTrackingSample.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="39bb4-149">Using Visual Studio 2010, open the CustomTrackingSample.sln solution file.</span></span>

2. <span data-ttu-id="39bb4-150">Çözümü oluşturmak için CTRL+SHIFT+B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="39bb4-150">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="39bb4-151">Çözümü çalıştırmak için CTRL+F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="39bb4-151">To run the solution, press CTRL+F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="39bb4-152">Örnekler bilgisayarınıza zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="39bb4-152">The samples may already be installed on your computer.</span></span> <span data-ttu-id="39bb4-153">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="39bb4-153">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="39bb4-154">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="39bb4-154">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="39bb4-155">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="39bb4-155">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\CustomTracking`  
  
## <a name="see-also"></a><span data-ttu-id="39bb4-156">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="39bb4-156">See also</span></span>

- <span data-ttu-id="39bb4-157">[AppFabric İzleme Örnekleri](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="39bb4-157">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
