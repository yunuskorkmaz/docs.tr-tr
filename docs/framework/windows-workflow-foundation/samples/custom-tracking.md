---
title: Özel İzleme
ms.date: 03/30/2017
ms.assetid: 2d191c9f-62f4-4c63-92dd-cda917fcf254
ms.openlocfilehash: b53b22b485a7ac340821073d2f2914b13a7b7011
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044297"
---
# <a name="custom-tracking"></a><span data-ttu-id="b4ec6-102">Özel İzleme</span><span class="sxs-lookup"><span data-stu-id="b4ec6-102">Custom Tracking</span></span>
<span data-ttu-id="b4ec6-103">Bu örnek, bir özel izleme katılımcısının nasıl oluşturulacağını ve izleme verilerinin içeriğini konsola nasıl yazılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b4ec6-103">This sample demonstrates how to create a custom tracking participant and write the contents of the tracking data to console.</span></span> <span data-ttu-id="b4ec6-104">Buna ek olarak, örnek, Kullanıcı tanımlı verilerle <xref:System.Activities.Tracking.CustomTrackingRecord> doldurulmuş nesneleri nasıl yayılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b4ec6-104">In addition, the sample demonstrates how to emit <xref:System.Activities.Tracking.CustomTrackingRecord> objects populated with user defined data.</span></span> <span data-ttu-id="b4ec6-105">Konsol tabanlı izleme katılımcısı, kod içinde oluşturulan <xref:System.Activities.Tracking.TrackingRecord> bir izleme profili nesnesi kullanılarak iş akışı tarafından yayılan nesneleri filtreler.</span><span class="sxs-lookup"><span data-stu-id="b4ec6-105">The console-based tracking participant filters the <xref:System.Activities.Tracking.TrackingRecord> objects emitted by the workflow using a tracking profile object created in code.</span></span>

## <a name="sample-details"></a><span data-ttu-id="b4ec6-106">Örnek Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="b4ec6-106">Sample Details</span></span>
 <span data-ttu-id="b4ec6-107">Windows Workflow Foundation (WF), bir iş akışı örneğinin yürütülmesini izlemek için bir izleme altyapısı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b4ec6-107">Windows Workflow Foundation (WF) provides a tracking infrastructure to track execution of a workflow instance.</span></span> <span data-ttu-id="b4ec6-108">İzleme çalışma zamanı, iş akışı kullanım ömrü, iş akışı etkinliklerinin olayları ve özel izleme etkinlikleriyle ilgili olayları göstermek için bir iş akışı örneği uygular.</span><span class="sxs-lookup"><span data-stu-id="b4ec6-108">The tracking runtime implements a workflow instance to emit events related to the workflow lifecycle, events from workflow activities and custom tracking events.</span></span> <span data-ttu-id="b4ec6-109">Aşağıdaki tabloda izleme altyapısının birincil bileşenleri ayrıntılı olarak verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b4ec6-109">The following table details the primary components of the tracking infrastructure.</span></span>

|<span data-ttu-id="b4ec6-110">Bileşen</span><span class="sxs-lookup"><span data-stu-id="b4ec6-110">Component</span></span>|<span data-ttu-id="b4ec6-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b4ec6-111">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="b4ec6-112">Çalışma zamanını izleme</span><span class="sxs-lookup"><span data-stu-id="b4ec6-112">Tracking runtime</span></span>|<span data-ttu-id="b4ec6-113">İzleme kayıtlarını yaymakta olan altyapıyı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b4ec6-113">Provides the infrastructure to emit tracking records.</span></span>|
|<span data-ttu-id="b4ec6-114">Katılımcıları izleme</span><span class="sxs-lookup"><span data-stu-id="b4ec6-114">Tracking participants</span></span>|<span data-ttu-id="b4ec6-115">İzleme kayıtlarını tüketir.</span><span class="sxs-lookup"><span data-stu-id="b4ec6-115">Consumes the tracking records.</span></span> [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)]<span data-ttu-id="b4ec6-116">izleme kayıtlarını Windows için olay Izleme (ETW) olayları olarak yazan bir izleme katılımcısına sahip olarak gelir.</span><span class="sxs-lookup"><span data-stu-id="b4ec6-116">ships with a tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span>|
|<span data-ttu-id="b4ec6-117">İzleme profili</span><span class="sxs-lookup"><span data-stu-id="b4ec6-117">Tracking profile</span></span>|<span data-ttu-id="b4ec6-118">Bir iş akışı örneğinden yayılan izleme kayıtlarının bir alt kümesi için bir izleme katılımcısının abone olmasına izin veren bir filtreleme mekanizması.</span><span class="sxs-lookup"><span data-stu-id="b4ec6-118">A filtering mechanism that allows a tracking participant to subscribe for a subset of the tracking records emitted from a workflow instance.</span></span>|

 <span data-ttu-id="b4ec6-119">Aşağıdaki tabloda iş akışı çalışma zamanının yaydığı izleme kayıtlarının ayrıntıları verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b4ec6-119">The following table details the tracking records that the workflow runtime emits.</span></span>

|<span data-ttu-id="b4ec6-120">İzleme kaydı</span><span class="sxs-lookup"><span data-stu-id="b4ec6-120">Tracking Record</span></span>|<span data-ttu-id="b4ec6-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b4ec6-121">Description</span></span>|
|---------------------|-----------------|
|<span data-ttu-id="b4ec6-122">İş akışı örneği izleme kayıtları.</span><span class="sxs-lookup"><span data-stu-id="b4ec6-122">Workflow instance tracking records.</span></span>|<span data-ttu-id="b4ec6-123">İş akışı örneğinin yaşam döngüsünü açıklar.</span><span class="sxs-lookup"><span data-stu-id="b4ec6-123">Describes the life cycle of the workflow instance.</span></span> <span data-ttu-id="b4ec6-124">Örneğin, iş akışı başladığında veya tamamlandığında bir örnek kayıt yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="b4ec6-124">For example, an instance record is emitted when the workflow starts or completes.</span></span>|
|<span data-ttu-id="b4ec6-125">Etkinlik durumu Izleme kayıtları.</span><span class="sxs-lookup"><span data-stu-id="b4ec6-125">Activity state Tracking Records.</span></span>|<span data-ttu-id="b4ec6-126">Ayrıntıları etkinlik yürütmesi.</span><span class="sxs-lookup"><span data-stu-id="b4ec6-126">Details activity execution.</span></span> <span data-ttu-id="b4ec6-127">Bu kayıtlar, bir etkinliğin zamanlandığı veya etkinliğin ne zaman tamamlandığı ya da bir hata oluşturulduğu zaman gibi bir iş akışı etkinliğinin durumunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="b4ec6-127">These records indicate the state of a workflow activity such as when an activity is scheduled or when the activity completes or when a fault is thrown.</span></span>|
|<span data-ttu-id="b4ec6-128">Bookmark sürdürme kaydı.</span><span class="sxs-lookup"><span data-stu-id="b4ec6-128">Bookmark resumption record.</span></span>|<span data-ttu-id="b4ec6-129">Bir iş akışı örneği içindeki bir yer işareti kaldığı zaman yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="b4ec6-129">Emitted whenever a bookmark within a workflow instance is resumed.</span></span>|
|<span data-ttu-id="b4ec6-130">Özel Izleme kayıtları.</span><span class="sxs-lookup"><span data-stu-id="b4ec6-130">Custom Tracking Records.</span></span>|<span data-ttu-id="b4ec6-131">Bir iş akışı yazarı özel Izleme kayıtları oluşturabilir ve bunları özel etkinlik içinde yayabilir.</span><span class="sxs-lookup"><span data-stu-id="b4ec6-131">A workflow author can create Custom Tracking Records and emit them within the custom activity.</span></span>|

 <span data-ttu-id="b4ec6-132">İzleme, izleme profilleri kullanılarak oluşturulan <xref:System.Activities.Tracking.TrackingRecord> nesnelerin bir alt kümesi için abone olur.</span><span class="sxs-lookup"><span data-stu-id="b4ec6-132">The tracking participant subscribes for a subset of the emitted <xref:System.Activities.Tracking.TrackingRecord> objects using tracking profiles.</span></span> <span data-ttu-id="b4ec6-133">Bir izleme profili, belirli bir izleme kayıt türü için abone 'e izin veren izleme sorguları içerir.</span><span class="sxs-lookup"><span data-stu-id="b4ec6-133">A tracking profile contains tracking queries that allow subscribing for a particular tracking record type.</span></span> <span data-ttu-id="b4ec6-134">İzleme profilleri kodda veya yapılandırmada belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="b4ec6-134">Tracking profiles can be specified in code or in configuration.</span></span>

### <a name="custom-tracking-participant"></a><span data-ttu-id="b4ec6-135">Özel Izleme Katılımcısı</span><span class="sxs-lookup"><span data-stu-id="b4ec6-135">Custom Tracking Participant</span></span>
 <span data-ttu-id="b4ec6-136">İzleme katılımcı API 'si, iş akışı çalışma zamanı tarafından yayılan nesneleri işlemek <xref:System.Activities.Tracking.TrackingRecord> için özel mantık içerebilen bir kullanıcı tarafından belirtilen izleme katılımcısından izleme çalışma zamanının uzantısına izin verir.</span><span class="sxs-lookup"><span data-stu-id="b4ec6-136">The tracking participant API allows extension of the tracking runtime with a user provided tracking participant that can include custom logic to handle <xref:System.Activities.Tracking.TrackingRecord> objects emitted by the workflow runtime.</span></span>

 <span data-ttu-id="b4ec6-137">Kullanıcının uygulaması <xref:System.Activities.Tracking.TrackingParticipant>gereken bir izleme katılımcısı yazmak için.</span><span class="sxs-lookup"><span data-stu-id="b4ec6-137">To write a tracking participant the user must implement <xref:System.Activities.Tracking.TrackingParticipant>.</span></span> <span data-ttu-id="b4ec6-138">Özellikle, <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> yöntemi özel katılımcı tarafından uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b4ec6-138">Specifically, the <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> method has to be implemented by the custom participant.</span></span> <span data-ttu-id="b4ec6-139">Bu yöntem, bir <xref:System.Activities.Tracking.TrackingRecord> iş akışı çalışma zamanı tarafından yayınlanarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="b4ec6-139">This method is called when a <xref:System.Activities.Tracking.TrackingRecord> is emitted by the workflow runtime.</span></span>

```csharp
public abstract class TrackingParticipant
{
    protected TrackingParticipant();

    public virtual TrackingProfile TrackingProfile { get; set; }
    public abstract void Track(TrackingRecord record, TimeSpan timeout);
}
```

 <span data-ttu-id="b4ec6-140">Tüm izleme katılımcısı ConsoleTrackingParticipant.cs dosyasında uygulanır. Aşağıdaki kod örneği <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> , özel izleme katılımcısının yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="b4ec6-140">The complete tracking participant is implemented in the ConsoleTrackingParticipant.cs file.The following code example is the <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> method for the custom tracking participant.</span></span>

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

 <span data-ttu-id="b4ec6-141">Aşağıdaki kod örneği, konsol katılımcısını iş akışı Invoker 'a ekler.</span><span class="sxs-lookup"><span data-stu-id="b4ec6-141">The following code example adds the console participant to the workflow invoker.</span></span>

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

### <a name="emitting-custom-tracking-records"></a><span data-ttu-id="b4ec6-142">Özel Izleme kayıtlarını yayma</span><span class="sxs-lookup"><span data-stu-id="b4ec6-142">Emitting Custom Tracking Records</span></span>
 <span data-ttu-id="b4ec6-143">Bu örnek ayrıca özel bir iş akışı etkinliğinden <xref:System.Activities.Tracking.CustomTrackingRecord> nesneleri yayma özelliğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="b4ec6-143">This sample also demonstrates the ability to emit <xref:System.Activities.Tracking.CustomTrackingRecord> objects from a custom workflow activity:</span></span>

- <span data-ttu-id="b4ec6-144"><xref:System.Activities.Tracking.CustomTrackingRecord> Nesneler oluşturulur ve kaydıyla birlikte yayınlanmaları istenen kullanıcı tanımlı verilerle doldurulur.</span><span class="sxs-lookup"><span data-stu-id="b4ec6-144">The <xref:System.Activities.Tracking.CustomTrackingRecord> objects are created and populated with user-defined data that is desired to be emitted with the record.</span></span>

- <span data-ttu-id="b4ec6-145">, Öğesinin Track yöntemi çağırarak yayılır. <xref:System.Activities.ActivityContext> <xref:System.Activities.Tracking.CustomTrackingRecord></span><span class="sxs-lookup"><span data-stu-id="b4ec6-145">The <xref:System.Activities.Tracking.CustomTrackingRecord> is emitted by calling the track method of the <xref:System.Activities.ActivityContext>.</span></span>

 <span data-ttu-id="b4ec6-146">Aşağıdaki örnek, nesneleri özel bir etkinlik <xref:System.Activities.Tracking.CustomTrackingRecord> içinde nasıl yayılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b4ec6-146">The following example demonstrates how to emit <xref:System.Activities.Tracking.CustomTrackingRecord> objects within a custom activity.</span></span>

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

#### <a name="to-use-this-sample"></a><span data-ttu-id="b4ec6-147">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="b4ec6-147">To use this sample</span></span>

1. <span data-ttu-id="b4ec6-148">Visual Studio 2010 kullanarak CustomTrackingSample. sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="b4ec6-148">Using Visual Studio 2010, open the CustomTrackingSample.sln solution file.</span></span>

2. <span data-ttu-id="b4ec6-149">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="b4ec6-149">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="b4ec6-150">Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="b4ec6-150">To run the solution, press CTRL+F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b4ec6-151">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="b4ec6-151">The samples may already be installed on your computer.</span></span> <span data-ttu-id="b4ec6-152">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="b4ec6-152">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="b4ec6-153">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin.</span><span class="sxs-lookup"><span data-stu-id="b4ec6-153">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b4ec6-154">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="b4ec6-154">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\CustomTracking`  
  
## <a name="see-also"></a><span data-ttu-id="b4ec6-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b4ec6-155">See also</span></span>

- [<span data-ttu-id="b4ec6-156">AppFabric Izleme örnekleri</span><span class="sxs-lookup"><span data-stu-id="b4ec6-156">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
