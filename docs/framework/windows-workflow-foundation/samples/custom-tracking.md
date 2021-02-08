---
description: 'Daha fazla bilgi edinin: özel Izleme'
title: Özel İzleme
ms.date: 03/30/2017
ms.assetid: 2d191c9f-62f4-4c63-92dd-cda917fcf254
ms.openlocfilehash: a06faaaa50a06d613f7183ca018438a8f2b4460b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792563"
---
# <a name="custom-tracking"></a><span data-ttu-id="fe6f2-103">Özel İzleme</span><span class="sxs-lookup"><span data-stu-id="fe6f2-103">Custom Tracking</span></span>

<span data-ttu-id="fe6f2-104">Bu örnek, bir özel izleme katılımcısının nasıl oluşturulacağını ve izleme verilerinin içeriğini konsola nasıl yazılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fe6f2-104">This sample demonstrates how to create a custom tracking participant and write the contents of the tracking data to console.</span></span> <span data-ttu-id="fe6f2-105">Buna ek olarak, örnek, <xref:System.Activities.Tracking.CustomTrackingRecord> Kullanıcı tanımlı verilerle doldurulmuş nesneleri nasıl yayılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fe6f2-105">In addition, the sample demonstrates how to emit <xref:System.Activities.Tracking.CustomTrackingRecord> objects populated with user defined data.</span></span> <span data-ttu-id="fe6f2-106">Konsol tabanlı izleme katılımcısı, <xref:System.Activities.Tracking.TrackingRecord> kod içinde oluşturulan bir izleme profili nesnesi kullanılarak iş akışı tarafından yayılan nesneleri filtreler.</span><span class="sxs-lookup"><span data-stu-id="fe6f2-106">The console-based tracking participant filters the <xref:System.Activities.Tracking.TrackingRecord> objects emitted by the workflow using a tracking profile object created in code.</span></span>

## <a name="sample-details"></a><span data-ttu-id="fe6f2-107">Örnek Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="fe6f2-107">Sample Details</span></span>

 <span data-ttu-id="fe6f2-108">Windows Workflow Foundation (WF), bir iş akışı örneğinin yürütülmesini izlemek için bir izleme altyapısı sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe6f2-108">Windows Workflow Foundation (WF) provides a tracking infrastructure to track execution of a workflow instance.</span></span> <span data-ttu-id="fe6f2-109">İzleme çalışma zamanı, iş akışı kullanım ömrü, iş akışı etkinliklerinin olayları ve özel izleme etkinlikleriyle ilgili olayları göstermek için bir iş akışı örneği uygular.</span><span class="sxs-lookup"><span data-stu-id="fe6f2-109">The tracking runtime implements a workflow instance to emit events related to the workflow lifecycle, events from workflow activities and custom tracking events.</span></span> <span data-ttu-id="fe6f2-110">Aşağıdaki tabloda izleme altyapısının birincil bileşenleri ayrıntılı olarak verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="fe6f2-110">The following table details the primary components of the tracking infrastructure.</span></span>

|<span data-ttu-id="fe6f2-111">Bileşen</span><span class="sxs-lookup"><span data-stu-id="fe6f2-111">Component</span></span>|<span data-ttu-id="fe6f2-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fe6f2-112">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="fe6f2-113">Çalışma zamanını izleme</span><span class="sxs-lookup"><span data-stu-id="fe6f2-113">Tracking runtime</span></span>|<span data-ttu-id="fe6f2-114">İzleme kayıtlarını yaymakta olan altyapıyı sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe6f2-114">Provides the infrastructure to emit tracking records.</span></span>|
|<span data-ttu-id="fe6f2-115">Katılımcıları izleme</span><span class="sxs-lookup"><span data-stu-id="fe6f2-115">Tracking participants</span></span>|<span data-ttu-id="fe6f2-116">İzleme kayıtlarını tüketir.</span><span class="sxs-lookup"><span data-stu-id="fe6f2-116">Consumes the tracking records.</span></span> <span data-ttu-id="fe6f2-117">.NET Framework 4, izleme kayıtlarını Windows için olay Izleme (ETW) olayları olarak yazan izleme katılımcılarıyla birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="fe6f2-117">.NET Framework 4 ships with a tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span>|
|<span data-ttu-id="fe6f2-118">İzleme profili</span><span class="sxs-lookup"><span data-stu-id="fe6f2-118">Tracking profile</span></span>|<span data-ttu-id="fe6f2-119">Bir iş akışı örneğinden yayılan izleme kayıtlarının bir alt kümesi için bir izleme katılımcısının abone olmasına izin veren bir filtreleme mekanizması.</span><span class="sxs-lookup"><span data-stu-id="fe6f2-119">A filtering mechanism that allows a tracking participant to subscribe for a subset of the tracking records emitted from a workflow instance.</span></span>|

 <span data-ttu-id="fe6f2-120">Aşağıdaki tabloda iş akışı çalışma zamanının yaydığı izleme kayıtlarının ayrıntıları verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="fe6f2-120">The following table details the tracking records that the workflow runtime emits.</span></span>

|<span data-ttu-id="fe6f2-121">İzleme kaydı</span><span class="sxs-lookup"><span data-stu-id="fe6f2-121">Tracking Record</span></span>|<span data-ttu-id="fe6f2-122">Description</span><span class="sxs-lookup"><span data-stu-id="fe6f2-122">Description</span></span>|
|---------------------|-----------------|
|<span data-ttu-id="fe6f2-123">İş akışı örneği izleme kayıtları.</span><span class="sxs-lookup"><span data-stu-id="fe6f2-123">Workflow instance tracking records.</span></span>|<span data-ttu-id="fe6f2-124">İş akışı örneğinin yaşam döngüsünü açıklar.</span><span class="sxs-lookup"><span data-stu-id="fe6f2-124">Describes the life cycle of the workflow instance.</span></span> <span data-ttu-id="fe6f2-125">Örneğin, iş akışı başladığında veya tamamlandığında bir örnek kayıt yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="fe6f2-125">For example, an instance record is emitted when the workflow starts or completes.</span></span>|
|<span data-ttu-id="fe6f2-126">Etkinlik durumu Izleme kayıtları.</span><span class="sxs-lookup"><span data-stu-id="fe6f2-126">Activity state Tracking Records.</span></span>|<span data-ttu-id="fe6f2-127">Ayrıntıları etkinlik yürütmesi.</span><span class="sxs-lookup"><span data-stu-id="fe6f2-127">Details activity execution.</span></span> <span data-ttu-id="fe6f2-128">Bu kayıtlar, bir etkinliğin zamanlandığı veya etkinliğin ne zaman tamamlandığı ya da bir hata oluşturulduğu zaman gibi bir iş akışı etkinliğinin durumunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="fe6f2-128">These records indicate the state of a workflow activity such as when an activity is scheduled or when the activity completes or when a fault is thrown.</span></span>|
|<span data-ttu-id="fe6f2-129">Bookmark sürdürme kaydı.</span><span class="sxs-lookup"><span data-stu-id="fe6f2-129">Bookmark resumption record.</span></span>|<span data-ttu-id="fe6f2-130">Bir iş akışı örneği içindeki bir yer işareti kaldığı zaman yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="fe6f2-130">Emitted whenever a bookmark within a workflow instance is resumed.</span></span>|
|<span data-ttu-id="fe6f2-131">Özel Izleme kayıtları.</span><span class="sxs-lookup"><span data-stu-id="fe6f2-131">Custom Tracking Records.</span></span>|<span data-ttu-id="fe6f2-132">Bir iş akışı yazarı özel Izleme kayıtları oluşturabilir ve bunları özel etkinlik içinde yayabilir.</span><span class="sxs-lookup"><span data-stu-id="fe6f2-132">A workflow author can create Custom Tracking Records and emit them within the custom activity.</span></span>|

 <span data-ttu-id="fe6f2-133">İzleme, izleme profilleri kullanılarak oluşturulan nesnelerin bir alt kümesi için abone olur <xref:System.Activities.Tracking.TrackingRecord> .</span><span class="sxs-lookup"><span data-stu-id="fe6f2-133">The tracking participant subscribes for a subset of the emitted <xref:System.Activities.Tracking.TrackingRecord> objects using tracking profiles.</span></span> <span data-ttu-id="fe6f2-134">Bir izleme profili, belirli bir izleme kayıt türü için abone 'e izin veren izleme sorguları içerir.</span><span class="sxs-lookup"><span data-stu-id="fe6f2-134">A tracking profile contains tracking queries that allow subscribing for a particular tracking record type.</span></span> <span data-ttu-id="fe6f2-135">İzleme profilleri kodda veya yapılandırmada belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="fe6f2-135">Tracking profiles can be specified in code or in configuration.</span></span>

### <a name="custom-tracking-participant"></a><span data-ttu-id="fe6f2-136">Özel Izleme Katılımcısı</span><span class="sxs-lookup"><span data-stu-id="fe6f2-136">Custom Tracking Participant</span></span>

 <span data-ttu-id="fe6f2-137">İzleme katılımcı API 'SI, <xref:System.Activities.Tracking.TrackingRecord> iş akışı çalışma zamanı tarafından yayılan nesneleri işlemek için özel mantık içerebilen bir kullanıcı tarafından belirtilen izleme katılımcısından izleme çalışma zamanının uzantısına izin verir.</span><span class="sxs-lookup"><span data-stu-id="fe6f2-137">The tracking participant API allows extension of the tracking runtime with a user provided tracking participant that can include custom logic to handle <xref:System.Activities.Tracking.TrackingRecord> objects emitted by the workflow runtime.</span></span>

 <span data-ttu-id="fe6f2-138">Kullanıcının uygulaması gereken bir izleme katılımcısı yazmak için <xref:System.Activities.Tracking.TrackingParticipant> .</span><span class="sxs-lookup"><span data-stu-id="fe6f2-138">To write a tracking participant the user must implement <xref:System.Activities.Tracking.TrackingParticipant>.</span></span> <span data-ttu-id="fe6f2-139">Özellikle, <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> yöntemi özel katılımcı tarafından uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fe6f2-139">Specifically, the <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> method has to be implemented by the custom participant.</span></span> <span data-ttu-id="fe6f2-140">Bu yöntem <xref:System.Activities.Tracking.TrackingRecord> , bir iş akışı çalışma zamanı tarafından yayınlanarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="fe6f2-140">This method is called when a <xref:System.Activities.Tracking.TrackingRecord> is emitted by the workflow runtime.</span></span>

```csharp
public abstract class TrackingParticipant
{
    protected TrackingParticipant();

    public virtual TrackingProfile TrackingProfile { get; set; }
    public abstract void Track(TrackingRecord record, TimeSpan timeout);
}
```

 <span data-ttu-id="fe6f2-141">Tüm izleme katılımcısı ConsoleTrackingParticipant.cs dosyasında uygulanır.</span><span class="sxs-lookup"><span data-stu-id="fe6f2-141">The complete tracking participant is implemented in the ConsoleTrackingParticipant.cs file.</span></span> <span data-ttu-id="fe6f2-142">Aşağıdaki kod örneği, <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> özel izleme katılımcısının yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="fe6f2-142">The following code example is the <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> method for the custom tracking participant.</span></span>

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

 <span data-ttu-id="fe6f2-143">Aşağıdaki kod örneği, konsol katılımcısını iş akışı Invoker 'a ekler.</span><span class="sxs-lookup"><span data-stu-id="fe6f2-143">The following code example adds the console participant to the workflow invoker.</span></span>

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

### <a name="emitting-custom-tracking-records"></a><span data-ttu-id="fe6f2-144">Özel Izleme kayıtlarını yayma</span><span class="sxs-lookup"><span data-stu-id="fe6f2-144">Emitting Custom Tracking Records</span></span>

 <span data-ttu-id="fe6f2-145">Bu örnek ayrıca <xref:System.Activities.Tracking.CustomTrackingRecord> özel bir iş akışı etkinliğinden nesneleri yayma özelliğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="fe6f2-145">This sample also demonstrates the ability to emit <xref:System.Activities.Tracking.CustomTrackingRecord> objects from a custom workflow activity:</span></span>

- <span data-ttu-id="fe6f2-146"><xref:System.Activities.Tracking.CustomTrackingRecord>Nesneler oluşturulur ve kaydıyla birlikte yayınlanmaları istenen kullanıcı tanımlı verilerle doldurulur.</span><span class="sxs-lookup"><span data-stu-id="fe6f2-146">The <xref:System.Activities.Tracking.CustomTrackingRecord> objects are created and populated with user-defined data that is desired to be emitted with the record.</span></span>

- <span data-ttu-id="fe6f2-147">, <xref:System.Activities.Tracking.CustomTrackingRecord> Öğesinin Track yöntemi çağırarak yayılır <xref:System.Activities.ActivityContext> .</span><span class="sxs-lookup"><span data-stu-id="fe6f2-147">The <xref:System.Activities.Tracking.CustomTrackingRecord> is emitted by calling the track method of the <xref:System.Activities.ActivityContext>.</span></span>

 <span data-ttu-id="fe6f2-148">Aşağıdaki örnek, <xref:System.Activities.Tracking.CustomTrackingRecord> nesneleri özel bir etkinlik içinde nasıl yayılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fe6f2-148">The following example demonstrates how to emit <xref:System.Activities.Tracking.CustomTrackingRecord> objects within a custom activity.</span></span>

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

#### <a name="to-use-this-sample"></a><span data-ttu-id="fe6f2-149">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="fe6f2-149">To use this sample</span></span>

1. <span data-ttu-id="fe6f2-150">Visual Studio 2010 kullanarak CustomTrackingSample. sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="fe6f2-150">Using Visual Studio 2010, open the CustomTrackingSample.sln solution file.</span></span>

2. <span data-ttu-id="fe6f2-151">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="fe6f2-151">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="fe6f2-152">Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="fe6f2-152">To run the solution, press CTRL+F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fe6f2-153">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="fe6f2-153">The samples may already be installed on your computer.</span></span> <span data-ttu-id="fe6f2-154">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="fe6f2-154">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="fe6f2-155">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="fe6f2-155">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fe6f2-156">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="fe6f2-156">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\CustomTracking`  
  
## <a name="see-also"></a><span data-ttu-id="fe6f2-157">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe6f2-157">See also</span></span>

- <span data-ttu-id="fe6f2-158">[AppFabric Izleme örnekleri](/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="fe6f2-158">[AppFabric Monitoring Samples](/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
