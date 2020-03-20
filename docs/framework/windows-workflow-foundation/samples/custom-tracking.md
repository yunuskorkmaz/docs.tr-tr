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
# <a name="custom-tracking"></a>Özel İzleme
Bu örnek, özel bir izleme katılımcısının nasıl oluşturulup izleme verilerinin içeriğini konsola nasıl yazılabildiğini gösterir. Buna ek olarak, örnek, kullanıcı <xref:System.Activities.Tracking.CustomTrackingRecord> tanımlı verilerle doldurulan nesneleri nasıl yayıştırılabildiğini gösterir. Konsol tabanlı izleme katılımcısı, <xref:System.Activities.Tracking.TrackingRecord> kodda oluşturulan bir izleme profili nesnesini kullanarak iş akışıtarafından yayılan nesneleri filtreler.

## <a name="sample-details"></a>Örnek Ayrıntılar
 Windows İş Akışı Temeli (WF), iş akışı örneğinin yürütülmesini izlemek için bir izleme altyapısı sağlar. İzleme çalışma zamanı, iş akışı yaşam döngüsüyle ilgili olayları, iş akışı etkinliklerinden olayları ve özel izleme olaylarını yalamak için bir iş akışı örneği uygular. Aşağıdaki tabloizleme altyapısının birincil bileşenlerini ayrıntılarıyla anlatır.

|Bileşen|Açıklama|
|---------------|-----------------|
|Çalışma süresini izleme|İzleme kayıtlarını yayışacak altyapıyı sağlar.|
|Katılımcıları izleme|İzleme kayıtlarını tüketir. .NET Framework 4, Windows (ETW) olayları için Olay İzleme olarak izleme kayıtları yazan bir izleme katılımcısıyla birlikte gemiler.|
|İzleme profili|İzleme katılımcısının iş akışı örneğinden yayılan izleme kayıtlarının bir alt kümesine abone olmasını sağlayan bir filtreleme mekanizması.|

 Aşağıdaki tablo, iş akışı çalışma zamanının yayıştığı izleme kayıtlarını ayrıntılarıyla tamamlar.

|İzleme Kaydı|Açıklama|
|---------------------|-----------------|
|İş akışı örneği izleme kayıtları.|İş akışı örneğinin yaşam döngüsünü açıklar. Örneğin, iş akışı başladığında veya tamamlandığında bir örnek kaydı yayımlanır.|
|Etkinlik durumu İzleme Kayıtları.|Ayrıntılar etkinlik yürütme. Bu kayıtlar, bir etkinliğin zamanlandığında, etkinlik tamamlandığında veya bir hata atıldığında olduğu gibi bir iş akışı etkinliğinin durumunu gösterir.|
|Yer imi yeniden kayıt.|İş akışı örneği içindeki yer imi devam ettiğinde yayılan.|
|Özel Takip Kayıtları.|İş akışı yazarı Özel İzleme Kayıtları oluşturabilir ve bunları özel etkinlik içinde yarayabilir.|

 İzleme katılımcısı, izleme profillerini kullanarak yayılan <xref:System.Activities.Tracking.TrackingRecord> nesnelerin bir alt kümesine abone olur. İzleme profili, belirli bir izleme kaydı türüne abone olmak için izleme sorguları içerir. İzleme profilleri kodda veya yapılandırmada belirtilebilir.

### <a name="custom-tracking-participant"></a>Özel İzleme Katılımcısı
 İzleme katılımcısı API, iş akışı çalışma zamanı tarafından yayılan nesneleri işlemek <xref:System.Activities.Tracking.TrackingRecord> için özel mantık içerebilen bir kullanıcı tarafından sağlanan izleme katılımcısı ile izleme çalışma süresinin uzatılmasına izin verir.

 Bir izleme katılımcısı yazmak <xref:System.Activities.Tracking.TrackingParticipant>için kullanıcının uygulaması gerekir. Özellikle, <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> yöntem özel katılımcı tarafından uygulanmalıdır. İş akışı çalışma <xref:System.Activities.Tracking.TrackingRecord> zamanı tarafından yayılan bir yöntem denir.

```csharp
public abstract class TrackingParticipant
{
    protected TrackingParticipant();

    public virtual TrackingProfile TrackingProfile { get; set; }
    public abstract void Track(TrackingRecord record, TimeSpan timeout);
}
```

 Tam izleme katılımcısı ConsoleTrackingParticipant.cs dosyasında uygulanır. Aşağıdaki kod örneği, <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> özel izleme katılımcısı için yöntemdir.

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

 Aşağıdaki kod örneği, konsol katılımcısını iş akışı çağıranına ekler.

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

### <a name="emitting-custom-tracking-records"></a>Özel İzleme Kayıtları Yayan
 Bu örnek, özel bir iş <xref:System.Activities.Tracking.CustomTrackingRecord> akışı etkinliğinden nesneleri yayış yeteneğini de gösterir:

- Nesneler <xref:System.Activities.Tracking.CustomTrackingRecord> oluşturulur ve kayıt la birlikte yayımlamak istenen kullanıcı tanımlı verilerle doldurulur.

- The' nin <xref:System.Activities.Tracking.CustomTrackingRecord> parça metodu çağrılarak <xref:System.Activities.ActivityContext>yayılır.

 Aşağıdaki örnek, özel bir etkinlik <xref:System.Activities.Tracking.CustomTrackingRecord> içinde nesnelerin nasıl yayıltılabildiğini gösterir.

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

1. Visual Studio 2010'u kullanarak CustomTrackingSample.sln çözüm dosyasını açın.

2. Çözümü oluşturmak için CTRL+SHIFT+B tuşuna basın.

3. Çözümü çalıştırmak için CTRL+F5 tuşuna basın.

> [!IMPORTANT]
> Örnekler bilgisayarınıza zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\CustomTracking`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [AppFabric İzleme Örnekleri](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
