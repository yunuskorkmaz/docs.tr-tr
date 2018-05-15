---
title: Özel İzleme
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d191c9f-62f4-4c63-92dd-cda917fcf254
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 559557b34cf284b6dba5b300ef7270ec8d49ca84
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="custom-tracking"></a><span data-ttu-id="cb797-102">Özel İzleme</span><span class="sxs-lookup"><span data-stu-id="cb797-102">Custom Tracking</span></span>
<span data-ttu-id="cb797-103">Bu örnek, özel izleme katılımcı oluşturmak ve izleme verilerini içeriğini konsola yazma gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="cb797-103">This sample demonstrates how to create a custom tracking participant and write the contents of the tracking data to console.</span></span> <span data-ttu-id="cb797-104">Ayrıca, örnek yayma gösterilmiştir <xref:System.Activities.Tracking.CustomTrackingRecord> kullanıcıyla doldurulmuş nesneleri tanımlanmış veri.</span><span class="sxs-lookup"><span data-stu-id="cb797-104">In addition, the sample demonstrates how to emit <xref:System.Activities.Tracking.CustomTrackingRecord> objects populated with user defined data.</span></span> <span data-ttu-id="cb797-105">Konsol tabanlı izleme katılımcı filtreleri <xref:System.Activities.Tracking.TrackingRecord> izleme profili kullanan iş akışı tarafından gösterilen nesneleri kodda oluşturulan nesne.</span><span class="sxs-lookup"><span data-stu-id="cb797-105">The console-based tracking participant filters the <xref:System.Activities.Tracking.TrackingRecord> objects emitted by the workflow using a tracking profile object created in code.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="cb797-106">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="cb797-106">Sample Details</span></span>  
 <span data-ttu-id="cb797-107">Windows Workflow Foundation (WF) iş akışı örneğini yürütmeyi izlemek üzere bir izleme altyapısı sağlar.</span><span class="sxs-lookup"><span data-stu-id="cb797-107">Windows Workflow Foundation (WF) provides a tracking infrastructure to track execution of a workflow instance.</span></span> <span data-ttu-id="cb797-108">İzleme çalışma zamanı iş akışı yaşam döngüsü olayları için iş akışı etkinlikleri ve özel izleme olaylarını ilgili olayları yaymak üzere bir iş akışı örneği uygular.</span><span class="sxs-lookup"><span data-stu-id="cb797-108">The tracking runtime implements a workflow instance to emit events related to the workflow lifecycle, events from workflow activities and custom tracking events.</span></span> <span data-ttu-id="cb797-109">Aşağıdaki tabloda birincil bileşenleri izleme altyapısının ayrıntılı olarak açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cb797-109">The following table details the primary components of the tracking infrastructure.</span></span>  
  
|<span data-ttu-id="cb797-110">Bileşen</span><span class="sxs-lookup"><span data-stu-id="cb797-110">Component</span></span>|<span data-ttu-id="cb797-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cb797-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cb797-112">Çalışma zamanı izleme</span><span class="sxs-lookup"><span data-stu-id="cb797-112">Tracking runtime</span></span>|<span data-ttu-id="cb797-113">İzleme kayıtları yayma için altyapı sağlar.</span><span class="sxs-lookup"><span data-stu-id="cb797-113">Provides the infrastructure to emit tracking records.</span></span>|  
|<span data-ttu-id="cb797-114">Katılımcıların izleme</span><span class="sxs-lookup"><span data-stu-id="cb797-114">Tracking participants</span></span>|<span data-ttu-id="cb797-115">İzleme kayıtların tüketir.</span><span class="sxs-lookup"><span data-stu-id="cb797-115">Consumes the tracking records.</span></span> [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)]<span data-ttu-id="cb797-116"> Olay izleme için Windows (ETW) olayları olarak izleme kayıtları Yazar izleme katılımcı birlikte verilir.</span><span class="sxs-lookup"><span data-stu-id="cb797-116"> ships with a tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span>|  
|<span data-ttu-id="cb797-117">İzleme profili</span><span class="sxs-lookup"><span data-stu-id="cb797-117">Tracking profile</span></span>|<span data-ttu-id="cb797-118">Bir iş akışı örneğinden yayılan izleme kayıtları alt kümeleri için abone olmak izleme katılımcı sağlayan bir filtreleme mekanizması.</span><span class="sxs-lookup"><span data-stu-id="cb797-118">A filtering mechanism that allows a tracking participant to subscribe for a subset of the tracking records emitted from a workflow instance.</span></span>|  
  
 <span data-ttu-id="cb797-119">Aşağıdaki tabloda, iş akışı çalışma zamanı yayar izleme kayıtları ayrıntıları verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="cb797-119">The following table details the tracking records that the workflow runtime emits.</span></span>  
  
|<span data-ttu-id="cb797-120">İzleme kaydı</span><span class="sxs-lookup"><span data-stu-id="cb797-120">Tracking Record</span></span>|<span data-ttu-id="cb797-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cb797-121">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="cb797-122">İş akışı örneği izleme kaydeder.</span><span class="sxs-lookup"><span data-stu-id="cb797-122">Workflow instance tracking records.</span></span>|<span data-ttu-id="cb797-123">İş akışı örneği yaşam döngüsünü açıklar.</span><span class="sxs-lookup"><span data-stu-id="cb797-123">Describes the life cycle of the workflow instance.</span></span> <span data-ttu-id="cb797-124">Örneğin, iş akışı başlatıldığında veya tamamlandıktan bir örnek kaydı yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="cb797-124">For example, an instance record is emitted when the workflow starts or completes.</span></span>|  
|<span data-ttu-id="cb797-125">Etkinlik durumu izleme kaydeder.</span><span class="sxs-lookup"><span data-stu-id="cb797-125">Activity state Tracking Records.</span></span>|<span data-ttu-id="cb797-126">Ayrıntılar Etkinlik yürütme.</span><span class="sxs-lookup"><span data-stu-id="cb797-126">Details activity execution.</span></span> <span data-ttu-id="cb797-127">Bu kayıtları bir etkinlik olduğunda zamanlanmış veya etkinlik tamamlandığında veya bir hata olduğunda atılır gibi bir iş akışı etkinlik durumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="cb797-127">These records indicate the state of a workflow activity such as when an activity is scheduled or when the activity completes or when a fault is thrown.</span></span>|  
|<span data-ttu-id="cb797-128">Sürdürme kayıt yer işareti.</span><span class="sxs-lookup"><span data-stu-id="cb797-128">Bookmark resumption record.</span></span>|<span data-ttu-id="cb797-129">Bir iş akışı örneği yer işareti sürdürüldü her yayılan.</span><span class="sxs-lookup"><span data-stu-id="cb797-129">Emitted whenever a bookmark within a workflow instance is resumed.</span></span>|  
|<span data-ttu-id="cb797-130">Özel İzleme kaydeder.</span><span class="sxs-lookup"><span data-stu-id="cb797-130">Custom Tracking Records.</span></span>|<span data-ttu-id="cb797-131">Bir iş akışı yazarı özel izleme kayıtları oluşturmak ve bunları içinde özel Etkinlik yayma.</span><span class="sxs-lookup"><span data-stu-id="cb797-131">A workflow author can create Custom Tracking Records and emit them within the custom activity.</span></span>|  
  
 <span data-ttu-id="cb797-132">Bir alt kümesi verilmiş için izleme katılımcı abone <xref:System.Activities.Tracking.TrackingRecord> izleme profilleri kullanarak nesneleri.</span><span class="sxs-lookup"><span data-stu-id="cb797-132">The tracking participant subscribes for a subset of the emitted <xref:System.Activities.Tracking.TrackingRecord> objects using tracking profiles.</span></span> <span data-ttu-id="cb797-133">İzleme profili belirli izleme kayıt türü için abone izin izleme sorgularını içerir.</span><span class="sxs-lookup"><span data-stu-id="cb797-133">A tracking profile contains tracking queries that allow subscribing for a particular tracking record type.</span></span> <span data-ttu-id="cb797-134">Profilleri izleme kod veya yapılandırma belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="cb797-134">Tracking profiles can be specified in code or in configuration.</span></span>  
  
### <a name="custom-tracking-participant"></a><span data-ttu-id="cb797-135">Özel İzleme katılımcı</span><span class="sxs-lookup"><span data-stu-id="cb797-135">Custom Tracking Participant</span></span>  
 <span data-ttu-id="cb797-136">İzleme katılımcı API izleme çalışma zamanı uzantısı işlemek için özel mantığı içeren bir kullanıcı tarafından sağlanan izleme katılımcı ile verir <xref:System.Activities.Tracking.TrackingRecord> iş akışı çalışma zamanı tarafından gösterilen nesneleri.</span><span class="sxs-lookup"><span data-stu-id="cb797-136">The tracking participant API allows extension of the tracking runtime with a user provided tracking participant that can include custom logic to handle <xref:System.Activities.Tracking.TrackingRecord> objects emitted by the workflow runtime.</span></span>  
  
 <span data-ttu-id="cb797-137">Bir izleme yazmak için katılımcı kullanıcı uygulamalıdır <xref:System.Activities.Tracking.TrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="cb797-137">To write a tracking participant the user must implement <xref:System.Activities.Tracking.TrackingParticipant>.</span></span> <span data-ttu-id="cb797-138">Özellikle, <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> yöntemi özel katılımcı tarafından uygulanması gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="cb797-138">Specifically, the <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> method has to be implemented by the custom participant.</span></span> <span data-ttu-id="cb797-139">Bu yöntem aldığında çağrılan bir <xref:System.Activities.Tracking.TrackingRecord> iş akışı çalışma zamanı tarafından yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="cb797-139">This method is called when a <xref:System.Activities.Tracking.TrackingRecord> is emitted by the workflow runtime.</span></span>  
  
```csharp  
public abstract class TrackingParticipant  
{  
    protected TrackingParticipant();  
  
    public virtual TrackingProfile TrackingProfile { get; set; }  
    public abstract void Track(TrackingRecord record, TimeSpan timeout);  
}  
```  
  
 <span data-ttu-id="cb797-140">Tam izleme katılımcı ConsoleTrackingParticipant.cs dosyasında uygulanır. Aşağıdaki kod örneğinde olduğu <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> özel izleme katılımcı yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cb797-140">The complete tracking participant is implemented in the ConsoleTrackingParticipant.cs file.The following code example is the <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> method for the custom tracking participant.</span></span>  
  
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
  
 <span data-ttu-id="cb797-141">Aşağıdaki kod örneğinde, iş akışı çağırıcı konsol katılımcı ekler.</span><span class="sxs-lookup"><span data-stu-id="cb797-141">The following code example adds the console participant to the workflow invoker.</span></span>  
  
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
  
### <a name="emitting-custom-tracking-records"></a><span data-ttu-id="cb797-142">Özel izleme kayıtları yayma</span><span class="sxs-lookup"><span data-stu-id="cb797-142">Emitting Custom Tracking Records</span></span>  
 <span data-ttu-id="cb797-143">Bu örnek ayrıca yayma yeteneğini gösterir <xref:System.Activities.Tracking.CustomTrackingRecord> özel iş akışı etkinlik nesnelerden:</span><span class="sxs-lookup"><span data-stu-id="cb797-143">This sample also demonstrates the ability to emit <xref:System.Activities.Tracking.CustomTrackingRecord> objects from a custom workflow activity:</span></span>  
  
-   <span data-ttu-id="cb797-144"><xref:System.Activities.Tracking.CustomTrackingRecord> Nesneleri oluşturulur ve istenen kayıtla yayınlaması için kullanıcı tarafından tanımlanan verilerle doldurulur.</span><span class="sxs-lookup"><span data-stu-id="cb797-144">The <xref:System.Activities.Tracking.CustomTrackingRecord> objects are created and populated with user-defined data that is desired to be emitted with the record.</span></span>  
  
-   <span data-ttu-id="cb797-145"><xref:System.Activities.Tracking.CustomTrackingRecord> İzleme yöntemi çağrılarak gösterilen <xref:System.Activities.ActivityContext>.</span><span class="sxs-lookup"><span data-stu-id="cb797-145">The <xref:System.Activities.Tracking.CustomTrackingRecord> is emitted by calling the track method of the <xref:System.Activities.ActivityContext>.</span></span>  
  
 <span data-ttu-id="cb797-146">Aşağıdaki örnek yayma gösterilmiştir <xref:System.Activities.Tracking.CustomTrackingRecord> özel etkinlik içindeki nesneler.</span><span class="sxs-lookup"><span data-stu-id="cb797-146">The following example demonstrates how to emit <xref:System.Activities.Tracking.CustomTrackingRecord> objects within a custom activity.</span></span>  
  
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
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="cb797-147">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="cb797-147">To use this sample</span></span>  
  
1.  <span data-ttu-id="cb797-148">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], CustomTrackingSample.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="cb797-148">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the CustomTrackingSample.sln solution file.</span></span>  
  
2.  <span data-ttu-id="cb797-149">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="cb797-149">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="cb797-150">Çözümü çalıştırmak için CTRL + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="cb797-150">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cb797-151">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="cb797-151">The samples may already be installed on your computer.</span></span> <span data-ttu-id="cb797-152">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="cb797-152">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="cb797-153">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="cb797-153">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cb797-154">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="cb797-154">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\CustomTracking`  
  
## <a name="see-also"></a><span data-ttu-id="cb797-155">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cb797-155">See Also</span></span>  
 [<span data-ttu-id="cb797-156">AppFabric izleme örnekleri</span><span class="sxs-lookup"><span data-stu-id="cb797-156">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
