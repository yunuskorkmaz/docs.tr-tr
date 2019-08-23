---
title: İzleme Katılımcıları
ms.date: 03/30/2017
ms.assetid: f13e360c-eeb7-4a49-98a0-8f6a52d64f68
ms.openlocfilehash: 45a92c3ab710fc9bc86fbf269a4672f1d34737cc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963682"
---
# <a name="tracking-participants"></a>İzleme Katılımcıları
Katılımcıları izlemek, iş akışı geliştiricisinin nesnelere erişmesini <xref:System.Activities.Tracking.InteropTrackingRecord.TrackingRecord%2A> ve bunları işlemesini sağlayan genişletilebilirlik noktalarıdır. [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]izleme kayıtlarını Windows için olay Izleme (ETW) olayları olarak yazan standart bir izleme katılımcısı içerir. Gereksinimlerinizi karşılamıyorsa, özel bir izleme katılımcısı da yazabilirsiniz.  
  
## <a name="tracking-participants"></a>İzleme Katılımcıları  
 İzleme altyapısı, bir katılımcının kayıtların bir alt kümesine abone olabileceği gibi, giden izleme kayıtlarında bir filtrenin uygulamasına izin verir. Filtre uygulama mekanizması bir izleme profili aracılığıyla yapılır.  
  
 İçindeki [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] Windows Workflow Foundation (WF), izleme kayıtlarını bir ETW oturumuna yazan bir izleme katılımcısı sağlar. Katılımcı bir yapılandırma dosyasına izlemeye özgü bir davranış ekleyerek bir iş akışı hizmeti üzerinde yapılandırılır. ETW izleme katılımcısının etkinleştirilmesi, Olay Görüntüleyicisi 'nde izleme kayıtlarının görüntülenmesine izin verir. ETW tabanlı izleme için SDK örneği, ETW tabanlı izleme katılımcısını kullanarak WF izlemeye alışmanız için iyi bir yoldur.  
  
## <a name="etw-tracking-participant"></a>ETW Izleme Katılımcısı  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], izleme kayıtlarını bir ETW oturumuna yazan bir ETW Izleme katılımcısı içerir. Bu, uygulamanın performansına veya sunucunun aktarım hızına en az etkiyle çok verimli bir şekilde yapılır. Standart ETW izleme katılımcısı kullanmanın bir avantajı, aldığı izleme kayıtlarının Windows Olay Görüntüleyicisi diğer uygulama ve sistem günlükleri ile görüntülenebilmesini kullanmaktır.  
  
 Standart ETW izleme katılımcısı, aşağıdaki örnekte gösterildiği gibi Web. config dosyasında yapılandırılır.  
  
```xml  
<configuration>  
  <system.web>  
    <compilation debug="true" targetFramework="4.0" />  
  </system.web>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <etwTracking profileName="Sample Tracking Profile"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
   <tracking>  
      <profiles>  
        <trackingProfile name="Sample Tracking Profile">  
        ….  
       </trackingProfile>  
      </profiles>  
    </tracking>  
  </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
> Yalnızca `trackingProfile` [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] veya gibi`<etwTracking profileName=""/>`bir ad belirtilmemişse, Machine. config dosyasında ile yüklenen varsayılan izleme profili kullanılır. `<etwTracking/>`  
  
 Machine. config dosyasında, varsayılan izleme profili iş akışı örnek kayıtlarına ve hatalarına abone olur.  
  
 ETW 'de, olaylar bir sağlayıcı KIMLIĞI aracılığıyla ETW oturumuna yazılır. ETW izleme katılımcısının, izleme kayıtlarını ETW 'ye yazmak için kullandığı sağlayıcı KIMLIĞI, Web. config dosyasının Tanılama bölümünde tanımlanmıştır (altında `<system.serviceModel><diagnostics>`). Varsayılan olarak, ETW izleme katılımcısı, aşağıdaki örnekte gösterildiği gibi, biri belirtilmediğinde varsayılan bir sağlayıcı KIMLIĞI kullanır.  
  
```xml  
<system.serviceModel>  
        <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />  
```  
  
 Aşağıdaki çizimde, ETW izleme katılımcısı aracılığıyla veri izleme akışı gösterilmektedir. İzleme verileri ETW oturumuna ulaştığında, bir dizi şekilde erişilebilir. Bu olaylara erişmenin en yararlı yöntemlerinden biri, uygulama ve hizmetlerden günlükleri ve izlemeleri görüntülemek için kullanılan ortak bir Windows aracı olan Olay Görüntüleyicisi.  
  
 ![ETW izleme sağlayıcısı aracılığıyla izleme verileri akışı.](./media/tracking-participants/tracking-data-event-tracing-windows-provider.gif)  
  
## <a name="tracking-participant-event-data"></a>Katılımcı olay verilerini izleme  
 Bir izleme katılımcısı, izlenen olay verilerini izleme kaydı başına bir olay biçiminde bir ETW oturumunda seri hale getirir.  Bir olay, 100 ile 199 arasında bir KIMLIK kullanılarak tanımlanır. İzleme katılımcısı tarafından yayılan izleme olayı kayıtlarının tanımları için, [olayları Izleme başvurusu](tracking-events-reference.md) konusuna bakın.  
  
 Bir ETW olayının boyutu ETW arabellek boyutuyla sınırlıdır veya bir ETW olayı için en yüksek yük tarafından, hangisi daha küçükse bu değer daha küçüktür. Olayın boyutu bu ETW limitlerinden birini aşarsa, olay kesilir ve içeriği rastgele bir şekilde kaldırılır. Değişkenler, bağımsız değişkenler, ek açıklamalar ve özel veriler seçmeli olarak kaldırılmaz. Kesme durumunda, bu durum, olay boyutunun ETW sınırını aşmasına neden olan değere bakılmaksızın kesilir.  Kaldırılan veriler ile `<item>..<item>`değiştirilmiştir.  
  
 Değişkenlerde, bağımsız değişkenlerde ve özel veri öğelerinde karmaşık türler [NetDataContractSerializer sınıfı](https://go.microsoft.com/fwlink/?LinkId=177537)kullanılarak ETW olay kaydına serileştirilir. Bu sınıf, seri hale getirilen XML tarafında CLR türü bilgilerini içerir.  
  
 ETW sınırları nedeniyle yük verilerinin kesilmesi, yinelenen izleme kayıtlarının bir ETW oturumuna gönderilmesine neden olabilir. Bu durum, olayları dinlerken birden fazla oturum varsa ve oturumlar için farklı yük sınırlarına sahip olduğunda meydana gelebilir.  
  
 Alt sınır ile oturum için olay kesilebilir. ETW izleme katılımcısı, olayları dinleyen oturum sayısı hakkında bilgi sahibi değildir; bir oturum için bir olay kesilmişse, ETW katılımcısı olayı bir kez göndermeyi yeniden dener. Bu durumda, daha büyük bir yük boyutunu kabul edecek şekilde yapılandırılan oturum, olayı iki kez alır (kesilmeyen ve kesilen olay). Aynı arabellek boyutu limitleriyle tüm ETW oturumları yapılandırılarak çoğaltma engellenebilir.  
  
## <a name="accessing-tracking-data-from-an-etw-participant-in-the-event-viewer"></a>Olay Görüntüleyicisi ETW katılımcılarından Izleme verilerine erişme  
 ETW izleme katılımcısı tarafından ETW oturumuna yazılan olaylara Olay Görüntüleyicisi aracılığıyla erişilebilir (varsayılan sağlayıcı KIMLIĞI kullanılırken). Bu, iş akışı tarafından yayınlanan kayıtları izlemeyi hızlı bir şekilde görüntülemenizi sağlar.  
  
> [!NOTE]
> Bir ETW oturumuna yayılan kayıt olaylarını izleme, 100 ile 199 arasındaki aralıktaki olay kimliklerini kullanır.  
  
#### <a name="to-enable-viewing-the-tracking-records-in-event-viewer"></a>Olay Görüntüleyicisi Izleme kayıtlarını görüntülemeyi etkinleştirmek için  
  
1. Olay Görüntüleyicisi başlatın (EVENTVWR. EXE  
  
2. **Olay Görüntüleyicisi, uygulama ve hizmet günlükleri, Microsoft, Windows, uygulama sunucusu-uygulamalar**' ı seçin.  
  
3. Sağ tıklayın ve **Görünüm, analitik ve hata ayıklama günlüklerini göster** ' in seçili olduğundan emin olun. Aksi takdirde, seçeneğinin yanında onay işaretinin görünmesi için bunu seçin. Bu, **analitik**, **perf**ve **hata ayıklama** günlüklerini görüntüler.  
  
4. **Analitik** günlüğe sağ tıklayın ve **günlüğü etkinleştir**' i seçin. Günlük%SystemRoot%\System32\Winevt\Logs\Microsoft-Windows-Application Server-Applications% 4 A nalytic. etl dosyasında mevcut olacaktır.  
  
## <a name="custom-tracking-participant"></a>Özel Izleme Katılımcısı  
 Katılımcı izleme API 'SI, iş akışı çalışma zamanı tarafından yayılan izleme kayıtlarını işlemek için özel mantık içerebilen kullanıcı tarafından sağlanmış bir izleme katılımcısına sahip izleme çalışma zamanının uzantısına izin verir. Özel bir izleme katılımcısı yazmak için, geliştiricinin `Track` metodu <xref:System.Activities.Tracking.TrackingParticipant> sınıfında uygulaması gerekir. Bu yöntem, bir izleme kaydı iş akışı çalışma zamanı tarafından yayıldığınızda çağrılır.  
  
 İzleme katılımcıları, <xref:System.Activities.Tracking.TrackingParticipant> sınıftan türetilir. Sistem tarafından sunulan <xref:System.Activities.Tracking.EtwTrackingParticipant> her izleme kaydı için bir Windows için olay izleme (ETW) olayı yayar. Özel bir izleme katılımcısı oluşturmak için, öğesinden <xref:System.Activities.Tracking.TrackingParticipant>türetilen bir sınıf oluşturulur. Temel izleme işlevlerini sağlamak için, öğesini <xref:System.Activities.Tracking.TrackingParticipant.Track%2A>geçersiz kılın. <xref:System.Activities.Tracking.TrackingParticipant.Track%2A>çalışma zamanı tarafından bir izleme kaydı gönderildiğinde ve istenen şekilde işlenebiliyor olduğunda çağrılır. Aşağıdaki örnekte, tüm izleme kayıtlarını konsol penceresine yayar ve özel bir izleme katılımcı sınıfı tanımlanmıştır. Ayrıca, <xref:System.Activities.Tracking.TrackingParticipant> `BeginTrack` ve yöntemlerinikullanarakizlemekayıtlarınızamanuyumsuzolarakişleyenbirnesnedauygulayabilirsiniz`EndTrack`  
  
```csharp  
class ConsoleTrackingParticipant : TrackingParticipant  
{  
    protected override void Track(TrackingRecord record, TimeSpan timeout)  
    {  
        if (record != null)  
        {  
            Console.WriteLine("=================================");  
            Console.WriteLine(record);  
        }  
    }  
}  
```  
  
 Belirli bir izleme katılımcısını kullanmak için, aşağıdaki örnekte gösterildiği gibi, izlemek istediğiniz iş akışı örneğiyle kaydedin.  
  
```csharp  
myInstance.Extensions.Add(new ConsoleTrackingParticipant());  
```  
  
 Aşağıdaki örnekte, <xref:System.Activities.Statements.Sequence> <xref:System.Activities.Statements.WriteLine> etkinlik içeren bir etkinlikten oluşan bir iş akışı oluşturulur. , `ConsoleTrackingParticipant` Uzantılara eklenir ve iş akışı çağrılır.  
  
```csharp  
Activity activity= new Sequence()  
{  
    Activities =  
    {  
        new WriteLine()  
        {  
            Text = "Hello World."  
        }  
    }  
};  
  
WorkflowApplication instance = new WorkflowApplication(activity);  
  
instance.Extensions.Add(new ConsoleTrackingParticipant());  
  instance.Completed = delegate(WorkflowApplicationCompletedEventArgs e)  
            {  
                Console.WriteLine("workflow instance completed, Id = " + instance.Id);  
                resetEvent.Set();  
            };  
            instance.Run();  
            Console.ReadLine();  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Server App Fabric Izleme](https://go.microsoft.com/fwlink/?LinkId=201273)
- [App Fabric ile uygulamaları izleme](https://go.microsoft.com/fwlink/?LinkId=201275)
