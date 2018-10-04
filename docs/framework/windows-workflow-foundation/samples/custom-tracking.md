---
title: Özel İzleme
ms.date: 03/30/2017
ms.assetid: 2d191c9f-62f4-4c63-92dd-cda917fcf254
ms.openlocfilehash: 5f603d991748439890a31a0a25fc65ad270a5083
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48266695"
---
# <a name="custom-tracking"></a>Özel İzleme
Bu örnek bir özel izleme Katılımcısı oluşturma ve izleme verilerini içeriğini konsola yazma gösterir. Ayrıca, örnek yayma yapmayı gösteren <xref:System.Activities.Tracking.CustomTrackingRecord> doldurulmuş olan kullanıcı nesneleri tanımlanan veri. Konsol tabanlı izleme katılımcı filtreleri <xref:System.Activities.Tracking.TrackingRecord> nesneleri bir izleme profili kullanan iş akışı tarafından yayılan kod içinde oluşturulan bir nesne.

## <a name="sample-details"></a>Örnek Ayrıntıları
 Windows Workflow Foundation (WF) iş akışı örneği yürütülmesini izlemek için izleme altyapısı sağlar. İzleme çalışma zamanı olaylarını, iş akışı yaşam döngüsü için iş akışı etkinlikleri ve özel izleme olaylarından ilgili olayları yaymak için bir iş akışı örneği uygular. Aşağıdaki tabloda birincil izleme altyapısının bileşenleri ayrıntıları.

|Bileşen|Açıklama|
|---------------|-----------------|
|Çalışma zamanı izleme|İzleme kayıtları yaymak için altyapı sağlar.|
|İzleme katılımcıları|İzleme kayıtları kullanır. [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)] izleme kayıtları için olay izleme Windows (ETW) olayları olarak yazan bir izleme katılımcı birlikte verilir.|
|İzleme profili|Bir iş akışı örneğinden yayılan izleme kayıtları bir alt kümesi için abone olmak izleme Katılımcısı sağlayan bir filtreleme mekanizması.|

 Aşağıdaki tabloda, iş akışı çalışma zamanı yayan izleme kayıtları ayrıntıları.

|Kayıt izleme|Açıklama|
|---------------------|-----------------|
|İş akışı örneği izleme kayıtları.|İş akışı örneği yaşam döngüsünü açıklar. Örneğin, iş akışı başlatıldığında veya tamamlanan bir örnek kaydı yayınlanır.|
|Etkinlik durumu izleme kayıtları.|Etkinlik yürütme ayrıntıları. Bu kayıtlar, bir etkinlik olduğunda zamanlanmış etkinlik tamamlandığında veya bir hata harekete geçirildiğinde gibi bir iş akışı etkinlik durumunu gösterir.|
|Sürdürme kayıt yer işareti.|Her bir iş akışı örneği içinde yer sürdürüldü yayılır.|
|Özel izleme kayıtları.|Bir iş akışı Yazar özel izleme kayıtları oluşturabilir ve bunları özel bir etkinlik içinde gösterin.|

 Bir alt kümesi yayılan için izleme katılımcı abone <xref:System.Activities.Tracking.TrackingRecord> izleme profilleri kullanarak nesne. Bir izleme profili belirli izleme kayıt türü için abone izin izleme sorguları içerir. İzleme profilleri kod veya yapılandırma belirtilebilir.

### <a name="custom-tracking-participant"></a>Özel İzleme katılımcı
 API izleme katılımcı izleme çalışma zamanı uzantısını işlemek için özel mantığı içeren bir kullanıcı tarafından sağlanan izleme katılımcı ile sağlar <xref:System.Activities.Tracking.TrackingRecord> iş akışı çalışma zamanı tarafından yayılan nesneleri.

 Bir izleme yazmak için katılımcı kullanıcı uygulamalıdır <xref:System.Activities.Tracking.TrackingParticipant>. Özellikle, <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> özel katılımcı tarafından uygulanmak üzere yöntemi vardır. Bu yöntem aldığında çağrılan bir <xref:System.Activities.Tracking.TrackingRecord> iş akışı çalışma zamanı tarafından yayılır.

```csharp
public abstract class TrackingParticipant
{
    protected TrackingParticipant();

    public virtual TrackingProfile TrackingProfile { get; set; }
    public abstract void Track(TrackingRecord record, TimeSpan timeout);
}
```

 Tüm izleme katılımcı ConsoleTrackingParticipant.cs dosyasında uygulanır. Aşağıdaki kod örneği olan <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> özel izleme Katılımcısı için yöntemi.

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

 Aşağıdaki kod örneği, iş akışı Başlatıcısı için konsol katılımcı ekler.

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

### <a name="emitting-custom-tracking-records"></a>Özel izleme kayıtları yayma
 Bu örnek ayrıca yayma özelliği gösterir <xref:System.Activities.Tracking.CustomTrackingRecord> özel iş akışı etkinlik nesneleri:

-   <xref:System.Activities.Tracking.CustomTrackingRecord> Nesnelerinin oluşturulduğu ve kayıtla derleyicisindeki istenen kullanıcı tarafından tanımlanan verilerle doldurulur.

-   <xref:System.Activities.Tracking.CustomTrackingRecord> Track yöntemi çağırarak yayılan <xref:System.Activities.ActivityContext>.

 Aşağıdaki örnek yayma gösterilmektedir <xref:System.Activities.Tracking.CustomTrackingRecord> özel bir etkinlik içinde nesneler.

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

1.  Visual Studio 2010 kullanarak CustomTrackingSample.sln çözüm dosyasını açın.

2.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.

3.  Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.

> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\CustomTracking`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric izleme örnekleri](https://go.microsoft.com/fwlink/?LinkId=193959)
