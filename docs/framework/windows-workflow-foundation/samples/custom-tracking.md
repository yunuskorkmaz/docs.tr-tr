---
title: Özel İzleme
ms.date: 03/30/2017
ms.assetid: 2d191c9f-62f4-4c63-92dd-cda917fcf254
ms.openlocfilehash: 9a2ad2004c47ce76dcc35baf4ca28aa174409581
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094663"
---
# <a name="custom-tracking"></a>Özel İzleme
Bu örnek, bir özel izleme katılımcısının nasıl oluşturulacağını ve izleme verilerinin içeriğini konsola nasıl yazılacağını gösterir. Buna ek olarak, örnek, Kullanıcı tanımlı verilerle doldurulmuş <xref:System.Activities.Tracking.CustomTrackingRecord> nesnelerinin nasıl yayılacağını gösterir. Konsol tabanlı izleme katılımcısı, kod içinde oluşturulan bir izleme profili nesnesi kullanılarak iş akışı tarafından yayılan <xref:System.Activities.Tracking.TrackingRecord> nesnelerini filtreler.

## <a name="sample-details"></a>Örnek Ayrıntılar
 Windows Workflow Foundation (WF), bir iş akışı örneğinin yürütülmesini izlemek için bir izleme altyapısı sağlar. İzleme çalışma zamanı, iş akışı kullanım ömrü, iş akışı etkinliklerinin olayları ve özel izleme etkinlikleriyle ilgili olayları göstermek için bir iş akışı örneği uygular. Aşağıdaki tabloda izleme altyapısının birincil bileşenleri ayrıntılı olarak verilmiştir.

|Bileşen|Açıklama|
|---------------|-----------------|
|Çalışma zamanını izleme|İzleme kayıtlarını yaymakta olan altyapıyı sağlar.|
|Katılımcıları izleme|İzleme kayıtlarını tüketir. .NET Framework 4, izleme kayıtlarını Windows için olay Izleme (ETW) olayları olarak yazan izleme katılımcılarıyla birlikte gelir.|
|İzleme profili|Bir iş akışı örneğinden yayılan izleme kayıtlarının bir alt kümesi için bir izleme katılımcısının abone olmasına izin veren bir filtreleme mekanizması.|

 Aşağıdaki tabloda iş akışı çalışma zamanının yaydığı izleme kayıtlarının ayrıntıları verilmiştir.

|İzleme kaydı|Açıklama|
|---------------------|-----------------|
|İş akışı örneği izleme kayıtları.|İş akışı örneğinin yaşam döngüsünü açıklar. Örneğin, iş akışı başladığında veya tamamlandığında bir örnek kayıt yayınlanır.|
|Etkinlik durumu Izleme kayıtları.|Ayrıntıları etkinlik yürütmesi. Bu kayıtlar, bir etkinliğin zamanlandığı veya etkinliğin ne zaman tamamlandığı ya da bir hata oluşturulduğu zaman gibi bir iş akışı etkinliğinin durumunu gösterir.|
|Bookmark sürdürme kaydı.|Bir iş akışı örneği içindeki bir yer işareti kaldığı zaman yayınlanır.|
|Özel Izleme kayıtları.|Bir iş akışı yazarı özel Izleme kayıtları oluşturabilir ve bunları özel etkinlik içinde yayabilir.|

 İzleme, izleme profilleri kullanarak, yayılan <xref:System.Activities.Tracking.TrackingRecord> nesnelerinin bir alt kümesi için abone olur. Bir izleme profili, belirli bir izleme kayıt türü için abone 'e izin veren izleme sorguları içerir. İzleme profilleri kodda veya yapılandırmada belirtilebilir.

### <a name="custom-tracking-participant"></a>Özel Izleme Katılımcısı
 İzleme katılımcı API 'SI, iş akışı çalışma zamanı tarafından yayılan <xref:System.Activities.Tracking.TrackingRecord> nesneleri işlemek için özel mantık içerebilen kullanıcı tarafından belirtilen bir izleme katılımcısının bulunduğu izleme çalışma zamanının uzantısına izin verir.

 İzleme katılımcısı yazmak için kullanıcının <xref:System.Activities.Tracking.TrackingParticipant>uygulaması gerekir. Özellikle, <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> yönteminin özel katılımcı tarafından uygulanması gerekir. Bu yöntem, bir <xref:System.Activities.Tracking.TrackingRecord> iş akışı çalışma zamanı tarafından yayınlanarak çağrılır.

```csharp
public abstract class TrackingParticipant
{
    protected TrackingParticipant();

    public virtual TrackingProfile TrackingProfile { get; set; }
    public abstract void Track(TrackingRecord record, TimeSpan timeout);
}
```

 Tüm izleme katılımcısı ConsoleTrackingParticipant.cs dosyasında uygulanır. Aşağıdaki kod örneği, özel izleme katılımcısı için <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> yöntemidir.

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

 Aşağıdaki kod örneği, konsol katılımcısını iş akışı Invoker 'a ekler.

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

### <a name="emitting-custom-tracking-records"></a>Özel Izleme kayıtlarını yayma
 Bu örnek ayrıca, özel bir iş akışı etkinliğinden <xref:System.Activities.Tracking.CustomTrackingRecord> nesneleri yayma özelliğini gösterir:

- <xref:System.Activities.Tracking.CustomTrackingRecord> nesneler oluşturulur ve kaydıyla birlikte yayınlanmaları istenen kullanıcı tanımlı verilerle doldurulur.

- <xref:System.Activities.Tracking.CustomTrackingRecord>, <xref:System.Activities.ActivityContext>izleme yöntemi çağırarak yayılır.

 Aşağıdaki örnek, <xref:System.Activities.Tracking.CustomTrackingRecord> nesnelerinin özel bir etkinlik içinde nasıl yayılacağını gösterir.

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

#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için

1. Visual Studio 2010 kullanarak CustomTrackingSample. sln çözüm dosyasını açın.

2. Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.

3. Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.

> [!IMPORTANT]
> Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\CustomTracking`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [AppFabric Izleme örnekleri](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
