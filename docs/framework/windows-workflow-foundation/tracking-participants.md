---
title: İzleme katılımcıları
ms.date: 03/30/2017
ms.assetid: f13e360c-eeb7-4a49-98a0-8f6a52d64f68
ms.openlocfilehash: 3165e08a02954facb7e016606e2f94662c6edfe9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54613563"
---
# <a name="tracking-participants"></a>İzleme katılımcıları
İzleme katılımcıları erişmek bir iş akışı Geliştirici tanıyan genişletilebilirlik noktaları olan <xref:System.Activities.Tracking.InteropTrackingRecord.TrackingRecord%2A> nesneleri ve bunları işlem. [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] izleme kayıtları için olay izleme Windows (ETW) olayları olarak yazan standart izleme katılımcı içerir. Gereksinimlerinizi karşılamıyorsa, özel izleme katılımcı de yazabilirsiniz.  
  
## <a name="tracking-participants"></a>İzleme katılımcıları  
 Katılımcı bir kayıt alt kümesi için abone olabilirsiniz, izleme altyapısı üzerinde giden izleme kayıtları bir filtre uygulamayı sağlar. Bir filtre uygulamak için bir izleme profili mekanizmadır.  
  
 Windows Workflow Foundation (WF) [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] izleme kayıtları bir ETW oturumu Yazar izleme katılımcı sağlar. Katılımcı bir iş akışı hizmeti yapılandırma dosyasında bir izleme özgü davranışı ekleyerek yapılandırılır. Etkinleştirme bir ETW İzleme katılımcı olacak şekilde kayıtları izleme Olay Görüntüleyicisi'görüntülemesini sağlar. ETW tabanlı izleme için SDK'sı örneği ile tabanlı ETW İzleme katılımcı kullanarak WF izleme hakkında bilgi edinmek için iyi bir yoludur.  
  
## <a name="etw-tracking-participant"></a>ETW İzleme katılımcı  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] bir ETW İzleme, izleme kayıtları bir ETW oturumu Yazar katılımcı içerir. Bu, uygulamanızın performansını veya sunucunun aktarım hızı için minimum etkiyle çok verimli bir şekilde gerçekleştirilir. Standart ETW İzleme katılımcı kullanmanın bir avantajı, aldığı izleme kayıtları başka bir uygulama ile görüntülenebilir ve Windows Olay Görüntüleyicisi'nde sistem günlükleri ' dir.  
  
 Standart ETW İzleme katılımcı Web.config dosyasında aşağıdaki örnekte gösterilen şekilde yapılandırılır.  
  
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
>  Varsa bir `trackingProfile` adı belirtilmezse gibi hemen `<etwTracking/>` veya `<etwTracking profileName=""/>`, ardından varsayılan profil ile yüklü izleme [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] Machine.config dosyasına dosyası kullanılır.  
  
 Machine.config dosyasında varsayılan profili izleme, iş akışı örneği kayıtları ve hatalar için abone olur.  
  
 ETW olayları ETW oturumu üzerinden bir sağlayıcı kimliği yazılır ETW İzleme katılımcı kullandığı izleme yazmak için ETW kayıt kimliği Web.config dosyasının tanılama bölümünde tanımlanan sağlayıcısı (altında `<system.serviceModel><diagnostics>`). Varsayılan olarak, bir belirtilmedi, ETW İzleme katılımcı aşağıdaki örnekte gösterildiği gibi varsayılan sağlayıcı kimliği kullanır.  
  
```xml  
<system.serviceModel>  
        <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />  
```  
  
 İzleme verilerini ETW İzleme katılımcı aracılığıyla akışı aşağıda gösterilmiştir. İzleme verilerini ETW oturumu ulaştığında, çeşitli yollarla erişilebilir. Olay Görüntüleyicisi, günlükler ve izlemeler, uygulamaları ve hizmetleri görüntülemek için kullanılan genel bir Windows aracı üzerinden bu olayları erişmek için en faydalı yollarından biridir.  
  
 ![Akışı izleme ve ETW İzleme Sağlayıcısı](../../../docs/framework/windows-workflow-foundation/media/trackingdatathroughetwparticipant.gif "TrackingDatathroughETWParticipant")  
  
## <a name="tracking-participant-event-data"></a>İzleme katılımcı olay verileri  
 İzleme katılımcı, izleme kaydı başına bir olay biçiminde bir ETW oturumu izlenen olay verilerini serileştirir.  Bir olay 199-100 aralığında bir kimliği kullanılarak tanımlanır. İzleme olayı tanımları için bir izleme katılımcı tarafından yayılan kayıtları görüntüle [izleme olayları başvurusu](../../../docs/framework/windows-workflow-foundation/tracking-events-reference.md) konu.  
  
 ETW olay boyutu ETW arabellek boyutuyla sınırlıdır veya ETW olayı için en fazla yükü tarafından hangi değerin daha küçük. Olay boyutu ya da ETW limitler aşarsa, olay kesilmiş ve içeriği rastgele bir şekilde kaldırıldı. Değişkenleri, bağımsız değişkenler, ek açıklamalar ve özel verileri seçmeli olarak kaldırılmaz. Kesme söz konusu olduğunda, bunların tümünün olay boyutu ETW sınırını aşmasına neden değeri bağımsız olarak kesilir.  Kaldırılan veriler ile değiştirilir `<item>..<item>`.  
  
 Karmaşık türleri değişkenleri, bağımsız ve özel veri öğeleri, ETW olay kullanarak kayıt serileştirilme [NetDataContractSerializer sınıfı](https://go.microsoft.com/fwlink/?LinkId=177537). Bu sınıf serileştirilmiş XML akışı CLR türü bilgilerini içerir.  
  
 Yük verisi ETW sınırı nedeniyle kesildi yinelenen izleme kayıtları bir ETW oturumu gönderilen neden olabilir. Birden fazla oturum olayları dinleyen ve oturumları olaylar için farklı yükü sınırları varsa bu durum oluşabilir.  
  
 Alt sınır oturum olay kesilebilir. ETW İzleme katılımcı olayları dinleme oturum sayısı, tüm bilgilere sahip değildir; bir olay oturumu sonra bir kez olayı gönderirken ETW katılımcı yeniden denemeler için grafik kesilmişse. Bu durumda daha büyük bir yükü boyutu kabul edecek şekilde yapılandırılmış oturum olayı iki kez (kesilmiş olmayan ve kesilmiş) alırsınız. Çoğaltma ile aynı arabellek boyutu sınırları tüm ETW oturumlarına yapılandırarak önlenebilir.  
  
## <a name="accessing-tracking-data-from-an-etw-participant-in-the-event-viewer"></a>Olay Görüntüleyicisi'ni bir ETW Katılımcısı veri izlemeyi erişme  
 Bir ETW oturumu ETW İzleme katılımcı tarafından yazılan olayları Olay Görüntüleyicisi'ni (varsayılan sağlayıcı kimliği kullanırken) erişilebilir. Bu, iş akışı tarafından yayılan kayıtları izleme hızlı bir şekilde görüntülemek için sağlar.  
  
> [!NOTE]
>  Olayların bir ETW oturumu kullanın olay kimlikleri 199-100 aralığında yayılan izleme.  
  
#### <a name="to-enable-viewing-the-tracking-records-in-event-viewer"></a>Olay Görüntüleyicisi'nde izleme kayıtları görüntüleme olanağı  
  
1.  Olay Görüntüleyicisi'ni (EVENTVWR. başlatma EXE)  
  
2.  Seçin **Olay Görüntüleyicisi, uygulama ve hizmet günlükleri, Microsoft, Windows, uygulama uygulamalarının**.  
  
3.  Sağ tıklayın ve emin **görünümü, Analitik ve hata ayıklama günlüklerini göster** seçilir. Aksi durumda, onay işaretine yanında görünecek şekilde seçin. Bu görüntüler **analitik**, **Perf**, ve **hata ayıklama** günlükleri.  
  
4.  Sağ **analitik** oturum açın ve ardından **günlüğü etkinleştir**. Günlük %SystemRoot%\System32\Winevt\Logs\Microsoft-Windows-Application Server-Applications%4Analytic.etl dosyasında bulunur.  
  
## <a name="custom-tracking-participant"></a>Özel İzleme katılımcı  
 API izleme katılımcı, izleme çalışma zamanı uzantısı, iş akışı çalışma zamanı tarafından yayılan izleme kayıtları işlemek için Özel mantık dahil edebilirsiniz bir kullanıcı tarafından sağlanan izleme katılımcı ile sağlar. Özel İzleme katılımcı yazmak için geliştirici uygulamalıdır `Track` metodunda <xref:System.Activities.Tracking.TrackingParticipant> sınıfı. Bu yöntem, bir izleme kaydını yayılan iş akışı çalışma zamanı tarafından çağrılır.  
  
 İzleme katılımcıları türetilen <xref:System.Activities.Tracking.TrackingParticipant> sınıfı. Sistem tarafından sağlanan <xref:System.Activities.Tracking.EtwTrackingParticipant> bir olay izleme için Windows (ETW) olayı, alınan her bir izleme kaydını gösterir. Özel İzleme katılımcı oluşturmak için bir sınıf oluşturulur türetildiği <xref:System.Activities.Tracking.TrackingParticipant>. Temel izleme işlevselliği sağlamak için geçersiz kılma <xref:System.Activities.Tracking.TrackingParticipant.Track%2A>. <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> bir izleme kaydını çalışma zamanı tarafından gönderilir ve istenen şekilde işlenebilir çağrılır. Aşağıdaki örnekte, tüm izleme kayıtları konsol penceresine yayan bir özel izleme katılımcı sınıf tanımlanır. Aynı zamanda uygulayabileceğiniz bir <xref:System.Activities.Tracking.TrackingParticipant> izleme işlemleri nesnesini kullanarak zaman uyumsuz olarak kaydeder, `BeginTrack` ve `EndTrack` yöntemleri  
  
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
  
 Belirli izleme katılımcı kullanmak için istediğiniz izlemek için aşağıdaki örnekte gösterildiği gibi iş akışı örneği ile kaydedin.  
  
```csharp  
myInstance.Extensions.Add(new ConsoleTrackingParticipant());  
```  
  
 Aşağıdaki örnekte, bir iş akışı, oluşur bir <xref:System.Activities.Statements.Sequence> içeren etkinlik bir <xref:System.Activities.Statements.WriteLine> etkinlik oluşturulur. `ConsoleTrackingParticipant` Uzantılarını eklenir ve iş akışı çağrılır.  
  
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
- [Windows Server App Fabric izleme](https://go.microsoft.com/fwlink/?LinkId=201273)
- [App Fabric ile uygulamaları izleme](https://go.microsoft.com/fwlink/?LinkId=201275)
