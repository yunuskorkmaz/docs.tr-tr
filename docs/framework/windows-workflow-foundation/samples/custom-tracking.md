---
title: "Özel İzleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2d191c9f-62f4-4c63-92dd-cda917fcf254
caps.latest.revision: "16"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3a32e76bdee87d6f00a5f01893e76ccb3de9ef51
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="custom-tracking"></a>Özel İzleme
Bu örnek, özel izleme katılımcı oluşturmak ve izleme verilerini içeriğini konsola yazma gösterilmiştir. Ayrıca, örnek yayma gösterilmiştir <xref:System.Activities.Tracking.CustomTrackingRecord> kullanıcıyla doldurulmuş nesneleri tanımlanmış veri. Konsol tabanlı izleme katılımcı filtreleri <xref:System.Activities.Tracking.TrackingRecord> izleme profili kullanan iş akışı tarafından gösterilen nesneleri kodda oluşturulan nesne.  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 [!INCLUDE[wf](../../../../includes/wf-md.md)]bir iş akışı örneğini yürütmeyi izlemek üzere bir izleme altyapısı sağlar. İzleme çalışma zamanı iş akışı yaşam döngüsü olayları için iş akışı etkinlikleri ve özel izleme olaylarını ilgili olayları yaymak üzere bir iş akışı örneği uygular. Aşağıdaki tabloda birincil bileşenleri izleme altyapısının ayrıntılı olarak açıklanmaktadır.  
  
|Bileşen|Açıklama|  
|---------------|-----------------|  
|Çalışma zamanı izleme|İzleme kayıtları yayma için altyapı sağlar.|  
|Katılımcıların izleme|İzleme kayıtların tüketir. [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)]Olay izleme için Windows (ETW) olayları olarak izleme kayıtları Yazar izleme katılımcı birlikte verilir.|  
|İzleme profili|Bir iş akışı örneğinden yayılan izleme kayıtları alt kümeleri için abone olmak izleme katılımcı sağlayan bir filtreleme mekanizması.|  
  
 Aşağıdaki tabloda, iş akışı çalışma zamanı yayar izleme kayıtları ayrıntıları verilmektedir.  
  
|İzleme kaydı|Açıklama|  
|---------------------|-----------------|  
|İş akışı örneği izleme kaydeder.|İş akışı örneği yaşam döngüsünü açıklar. Örneğin, iş akışı başlatıldığında veya tamamlandıktan bir örnek kaydı yayınlanır.|  
|Etkinlik durumu izleme kaydeder.|Ayrıntılar Etkinlik yürütme. Bu kayıtları bir etkinlik olduğunda zamanlanmış veya etkinlik tamamlandığında veya bir hata olduğunda atılır gibi bir iş akışı etkinlik durumunu belirtir.|  
|Sürdürme kayıt yer işareti.|Bir iş akışı örneği yer işareti sürdürüldü her yayılan.|  
|Özel İzleme kaydeder.|Bir iş akışı yazarı özel izleme kayıtları oluşturmak ve bunları içinde özel Etkinlik yayma.|  
  
 Bir alt kümesi verilmiş için izleme katılımcı abone <xref:System.Activities.Tracking.TrackingRecord> izleme profilleri kullanarak nesneleri. İzleme profili belirli izleme kayıt türü için abone izin izleme sorgularını içerir. Profilleri izleme kod veya yapılandırma belirtilebilir.  
  
### <a name="custom-tracking-participant"></a>Özel İzleme katılımcı  
 İzleme katılımcı API izleme çalışma zamanı uzantısı işlemek için özel mantığı içeren bir kullanıcı tarafından sağlanan izleme katılımcı ile verir <xref:System.Activities.Tracking.TrackingRecord> iş akışı çalışma zamanı tarafından gösterilen nesneleri.  
  
 Bir izleme yazmak için katılımcı kullanıcı uygulamalıdır <xref:System.Activities.Tracking.TrackingParticipant>. Özellikle, <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> yöntemi özel katılımcı tarafından uygulanması gerekiyor. Bu yöntem aldığında çağrılan bir <xref:System.Activities.Tracking.TrackingRecord> iş akışı çalışma zamanı tarafından yayınlanır.  
  
```csharp  
public abstract class TrackingParticipant  
{  
    protected TrackingParticipant();  
  
    public virtual TrackingProfile TrackingProfile { get; set; }  
    public abstract void Track(TrackingRecord record, TimeSpan timeout);  
}  
```  
  
 Tam izleme katılımcı ConsoleTrackingParticipant.cs dosyasında uygulanır. Aşağıdaki kod örneğinde olduğu <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> özel izleme katılımcı yöntemi.  
  
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
  
 Aşağıdaki kod örneğinde, iş akışı çağırıcı konsol katılımcı ekler.  
  
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
 Bu örnek ayrıca yayma yeteneğini gösterir <xref:System.Activities.Tracking.CustomTrackingRecord> özel iş akışı etkinlik nesnelerden:  
  
-   <xref:System.Activities.Tracking.CustomTrackingRecord> Nesneleri oluşturulur ve istenen kayıtla yayınlaması için kullanıcı tarafından tanımlanan verilerle doldurulur.  
  
-   <xref:System.Activities.Tracking.CustomTrackingRecord> İzleme yöntemi çağrılarak gösterilen <xref:System.Activities.ActivityContext>.  
  
 Aşağıdaki örnek yayma gösterilmiştir <xref:System.Activities.Tracking.CustomTrackingRecord> özel etkinlik içindeki nesneler.  
  
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
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], CustomTrackingSample.sln çözüm dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
3.  Çözümü çalıştırmak için CTRL + F5 tuşuna basın.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\CustomTracking`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric izleme örnekleri](http://go.microsoft.com/fwlink/?LinkId=193959)
