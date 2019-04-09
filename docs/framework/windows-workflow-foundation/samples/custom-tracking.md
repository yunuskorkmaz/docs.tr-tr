---
title: Özel İzleme
ms.date: 03/30/2017
ms.assetid: 2d191c9f-62f4-4c63-92dd-cda917fcf254
ms.openlocfilehash: ca53d74f31059532118f3b5d96760a25ed72b3d5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59161851"
---
# <a name="custom-tracking"></a><span data-ttu-id="03aab-102">Özel İzleme</span><span class="sxs-lookup"><span data-stu-id="03aab-102">Custom Tracking</span></span>
<span data-ttu-id="03aab-103">Bu örnek bir özel izleme Katılımcısı oluşturma ve izleme verilerini içeriğini konsola yazma gösterir.</span><span class="sxs-lookup"><span data-stu-id="03aab-103">This sample demonstrates how to create a custom tracking participant and write the contents of the tracking data to console.</span></span> <span data-ttu-id="03aab-104">Ayrıca, örnek yayma yapmayı gösteren <xref:System.Activities.Tracking.CustomTrackingRecord> doldurulmuş olan kullanıcı nesneleri tanımlanan veri.</span><span class="sxs-lookup"><span data-stu-id="03aab-104">In addition, the sample demonstrates how to emit <xref:System.Activities.Tracking.CustomTrackingRecord> objects populated with user defined data.</span></span> <span data-ttu-id="03aab-105">Konsol tabanlı izleme katılımcı filtreleri <xref:System.Activities.Tracking.TrackingRecord> nesneleri bir izleme profili kullanan iş akışı tarafından yayılan kod içinde oluşturulan bir nesne.</span><span class="sxs-lookup"><span data-stu-id="03aab-105">The console-based tracking participant filters the <xref:System.Activities.Tracking.TrackingRecord> objects emitted by the workflow using a tracking profile object created in code.</span></span>

## <a name="sample-details"></a><span data-ttu-id="03aab-106">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="03aab-106">Sample Details</span></span>
 <span data-ttu-id="03aab-107">Windows Workflow Foundation (WF) iş akışı örneği yürütülmesini izlemek için izleme altyapısı sağlar.</span><span class="sxs-lookup"><span data-stu-id="03aab-107">Windows Workflow Foundation (WF) provides a tracking infrastructure to track execution of a workflow instance.</span></span> <span data-ttu-id="03aab-108">İzleme çalışma zamanı olaylarını, iş akışı yaşam döngüsü için iş akışı etkinlikleri ve özel izleme olaylarından ilgili olayları yaymak için bir iş akışı örneği uygular.</span><span class="sxs-lookup"><span data-stu-id="03aab-108">The tracking runtime implements a workflow instance to emit events related to the workflow lifecycle, events from workflow activities and custom tracking events.</span></span> <span data-ttu-id="03aab-109">Aşağıdaki tabloda birincil izleme altyapısının bileşenleri ayrıntıları.</span><span class="sxs-lookup"><span data-stu-id="03aab-109">The following table details the primary components of the tracking infrastructure.</span></span>

|<span data-ttu-id="03aab-110">Bileşen</span><span class="sxs-lookup"><span data-stu-id="03aab-110">Component</span></span>|<span data-ttu-id="03aab-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="03aab-111">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="03aab-112">Çalışma zamanı izleme</span><span class="sxs-lookup"><span data-stu-id="03aab-112">Tracking runtime</span></span>|<span data-ttu-id="03aab-113">İzleme kayıtları yaymak için altyapı sağlar.</span><span class="sxs-lookup"><span data-stu-id="03aab-113">Provides the infrastructure to emit tracking records.</span></span>|
|<span data-ttu-id="03aab-114">İzleme katılımcıları</span><span class="sxs-lookup"><span data-stu-id="03aab-114">Tracking participants</span></span>|<span data-ttu-id="03aab-115">İzleme kayıtları kullanır.</span><span class="sxs-lookup"><span data-stu-id="03aab-115">Consumes the tracking records.</span></span> [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)] <span data-ttu-id="03aab-116">izleme kayıtları için olay izleme Windows (ETW) olayları olarak yazan bir izleme katılımcı birlikte verilir.</span><span class="sxs-lookup"><span data-stu-id="03aab-116">ships with a tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span>|
|<span data-ttu-id="03aab-117">İzleme profili</span><span class="sxs-lookup"><span data-stu-id="03aab-117">Tracking profile</span></span>|<span data-ttu-id="03aab-118">Bir iş akışı örneğinden yayılan izleme kayıtları bir alt kümesi için abone olmak izleme Katılımcısı sağlayan bir filtreleme mekanizması.</span><span class="sxs-lookup"><span data-stu-id="03aab-118">A filtering mechanism that allows a tracking participant to subscribe for a subset of the tracking records emitted from a workflow instance.</span></span>|

 <span data-ttu-id="03aab-119">Aşağıdaki tabloda, iş akışı çalışma zamanı yayan izleme kayıtları ayrıntıları.</span><span class="sxs-lookup"><span data-stu-id="03aab-119">The following table details the tracking records that the workflow runtime emits.</span></span>

|<span data-ttu-id="03aab-120">Kayıt izleme</span><span class="sxs-lookup"><span data-stu-id="03aab-120">Tracking Record</span></span>|<span data-ttu-id="03aab-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="03aab-121">Description</span></span>|
|---------------------|-----------------|
|<span data-ttu-id="03aab-122">İş akışı örneği izleme kayıtları.</span><span class="sxs-lookup"><span data-stu-id="03aab-122">Workflow instance tracking records.</span></span>|<span data-ttu-id="03aab-123">İş akışı örneği yaşam döngüsünü açıklar.</span><span class="sxs-lookup"><span data-stu-id="03aab-123">Describes the life cycle of the workflow instance.</span></span> <span data-ttu-id="03aab-124">Örneğin, iş akışı başlatıldığında veya tamamlanan bir örnek kaydı yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="03aab-124">For example, an instance record is emitted when the workflow starts or completes.</span></span>|
|<span data-ttu-id="03aab-125">Etkinlik durumu izleme kayıtları.</span><span class="sxs-lookup"><span data-stu-id="03aab-125">Activity state Tracking Records.</span></span>|<span data-ttu-id="03aab-126">Etkinlik yürütme ayrıntıları.</span><span class="sxs-lookup"><span data-stu-id="03aab-126">Details activity execution.</span></span> <span data-ttu-id="03aab-127">Bu kayıtlar, bir etkinlik olduğunda zamanlanmış etkinlik tamamlandığında veya bir hata harekete geçirildiğinde gibi bir iş akışı etkinlik durumunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="03aab-127">These records indicate the state of a workflow activity such as when an activity is scheduled or when the activity completes or when a fault is thrown.</span></span>|
|<span data-ttu-id="03aab-128">Sürdürme kayıt yer işareti.</span><span class="sxs-lookup"><span data-stu-id="03aab-128">Bookmark resumption record.</span></span>|<span data-ttu-id="03aab-129">Her bir iş akışı örneği içinde yer sürdürüldü yayılır.</span><span class="sxs-lookup"><span data-stu-id="03aab-129">Emitted whenever a bookmark within a workflow instance is resumed.</span></span>|
|<span data-ttu-id="03aab-130">Özel izleme kayıtları.</span><span class="sxs-lookup"><span data-stu-id="03aab-130">Custom Tracking Records.</span></span>|<span data-ttu-id="03aab-131">Bir iş akışı Yazar özel izleme kayıtları oluşturabilir ve bunları özel bir etkinlik içinde gösterin.</span><span class="sxs-lookup"><span data-stu-id="03aab-131">A workflow author can create Custom Tracking Records and emit them within the custom activity.</span></span>|

 <span data-ttu-id="03aab-132">Bir alt kümesi yayılan için izleme katılımcı abone <xref:System.Activities.Tracking.TrackingRecord> izleme profilleri kullanarak nesne.</span><span class="sxs-lookup"><span data-stu-id="03aab-132">The tracking participant subscribes for a subset of the emitted <xref:System.Activities.Tracking.TrackingRecord> objects using tracking profiles.</span></span> <span data-ttu-id="03aab-133">Bir izleme profili belirli izleme kayıt türü için abone izin izleme sorguları içerir.</span><span class="sxs-lookup"><span data-stu-id="03aab-133">A tracking profile contains tracking queries that allow subscribing for a particular tracking record type.</span></span> <span data-ttu-id="03aab-134">İzleme profilleri kod veya yapılandırma belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="03aab-134">Tracking profiles can be specified in code or in configuration.</span></span>

### <a name="custom-tracking-participant"></a><span data-ttu-id="03aab-135">Özel İzleme katılımcı</span><span class="sxs-lookup"><span data-stu-id="03aab-135">Custom Tracking Participant</span></span>
 <span data-ttu-id="03aab-136">API izleme katılımcı izleme çalışma zamanı uzantısını işlemek için özel mantığı içeren bir kullanıcı tarafından sağlanan izleme katılımcı ile sağlar <xref:System.Activities.Tracking.TrackingRecord> iş akışı çalışma zamanı tarafından yayılan nesneleri.</span><span class="sxs-lookup"><span data-stu-id="03aab-136">The tracking participant API allows extension of the tracking runtime with a user provided tracking participant that can include custom logic to handle <xref:System.Activities.Tracking.TrackingRecord> objects emitted by the workflow runtime.</span></span>

 <span data-ttu-id="03aab-137">Bir izleme yazmak için katılımcı kullanıcı uygulamalıdır <xref:System.Activities.Tracking.TrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="03aab-137">To write a tracking participant the user must implement <xref:System.Activities.Tracking.TrackingParticipant>.</span></span> <span data-ttu-id="03aab-138">Özellikle, <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> özel katılımcı tarafından uygulanmak üzere yöntemi vardır.</span><span class="sxs-lookup"><span data-stu-id="03aab-138">Specifically, the <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> method has to be implemented by the custom participant.</span></span> <span data-ttu-id="03aab-139">Bu yöntem aldığında çağrılan bir <xref:System.Activities.Tracking.TrackingRecord> iş akışı çalışma zamanı tarafından yayılır.</span><span class="sxs-lookup"><span data-stu-id="03aab-139">This method is called when a <xref:System.Activities.Tracking.TrackingRecord> is emitted by the workflow runtime.</span></span>

```csharp
public abstract class TrackingParticipant
{
    protected TrackingParticipant();

    public virtual TrackingProfile TrackingProfile { get; set; }
    public abstract void Track(TrackingRecord record, TimeSpan timeout);
}
```

 <span data-ttu-id="03aab-140">Tüm izleme katılımcı ConsoleTrackingParticipant.cs dosyasında uygulanır. Aşağıdaki kod örneği olan <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> özel izleme Katılımcısı için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="03aab-140">The complete tracking participant is implemented in the ConsoleTrackingParticipant.cs file.The following code example is the <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> method for the custom tracking participant.</span></span>

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

 <span data-ttu-id="03aab-141">Aşağıdaki kod örneği, iş akışı Başlatıcısı için konsol katılımcı ekler.</span><span class="sxs-lookup"><span data-stu-id="03aab-141">The following code example adds the console participant to the workflow invoker.</span></span>

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

### <a name="emitting-custom-tracking-records"></a><span data-ttu-id="03aab-142">Özel izleme kayıtları yayma</span><span class="sxs-lookup"><span data-stu-id="03aab-142">Emitting Custom Tracking Records</span></span>
 <span data-ttu-id="03aab-143">Bu örnek ayrıca yayma özelliği gösterir <xref:System.Activities.Tracking.CustomTrackingRecord> özel iş akışı etkinlik nesneleri:</span><span class="sxs-lookup"><span data-stu-id="03aab-143">This sample also demonstrates the ability to emit <xref:System.Activities.Tracking.CustomTrackingRecord> objects from a custom workflow activity:</span></span>

-   <span data-ttu-id="03aab-144"><xref:System.Activities.Tracking.CustomTrackingRecord> Nesnelerinin oluşturulduğu ve kayıtla derleyicisindeki istenen kullanıcı tarafından tanımlanan verilerle doldurulur.</span><span class="sxs-lookup"><span data-stu-id="03aab-144">The <xref:System.Activities.Tracking.CustomTrackingRecord> objects are created and populated with user-defined data that is desired to be emitted with the record.</span></span>

-   <span data-ttu-id="03aab-145"><xref:System.Activities.Tracking.CustomTrackingRecord> Track yöntemi çağırarak yayılan <xref:System.Activities.ActivityContext>.</span><span class="sxs-lookup"><span data-stu-id="03aab-145">The <xref:System.Activities.Tracking.CustomTrackingRecord> is emitted by calling the track method of the <xref:System.Activities.ActivityContext>.</span></span>

 <span data-ttu-id="03aab-146">Aşağıdaki örnek yayma gösterilmektedir <xref:System.Activities.Tracking.CustomTrackingRecord> özel bir etkinlik içinde nesneler.</span><span class="sxs-lookup"><span data-stu-id="03aab-146">The following example demonstrates how to emit <xref:System.Activities.Tracking.CustomTrackingRecord> objects within a custom activity.</span></span>

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

#### <a name="to-use-this-sample"></a><span data-ttu-id="03aab-147">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="03aab-147">To use this sample</span></span>

1.  <span data-ttu-id="03aab-148">Visual Studio 2010 kullanarak CustomTrackingSample.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="03aab-148">Using Visual Studio 2010, open the CustomTrackingSample.sln solution file.</span></span>

2.  <span data-ttu-id="03aab-149">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="03aab-149">To build the solution, press CTRL+SHIFT+B.</span></span>

3.  <span data-ttu-id="03aab-150">Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="03aab-150">To run the solution, press CTRL+F5.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="03aab-151">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="03aab-151">The samples may already be installed on your computer.</span></span> <span data-ttu-id="03aab-152">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="03aab-152">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="03aab-153">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="03aab-153">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="03aab-154">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="03aab-154">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\CustomTracking`  
  
## <a name="see-also"></a><span data-ttu-id="03aab-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="03aab-155">See also</span></span>

- [<span data-ttu-id="03aab-156">AppFabric izleme örnekleri</span><span class="sxs-lookup"><span data-stu-id="03aab-156">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
