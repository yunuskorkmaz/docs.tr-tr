---
title: "Katılımcıların izleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f13e360c-eeb7-4a49-98a0-8f6a52d64f68
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f335695c86037d792b17b98080b7a2e668ac1df5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="tracking-participants"></a>Katılımcıların izleme
İzleme katılımcıları erişmek bir iş akışı Geliştirici izin genişletilebilirlik noktaları olan <xref:System.Activities.Tracking.InteropTrackingRecord.TrackingRecord%2A> nesneleri ve bunları işlem. [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]Olay izleme için Windows (ETW) olayları olarak izleme kayıtları yazan standart izleme katılımcı içerir. Özel İzleme katılımcı Ayrıca, gereksinimlerinizi karşılamıyorsa yazabilirsiniz.  
  
## <a name="tracking-participants"></a>Katılımcıların izleme  
 İzleme altyapı, katılımcı kayıtların bir alt kümesini için abone olabilirsiniz gibi bir filtre uygulamayı giden izleme kayıtlarda sağlar. Bir filtre uygulamak için bir izleme profili mekanizmadır.  
  
 [!INCLUDE[wf](../../../includes/wf-md.md)]içinde [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] izleme kayıtları ETW oturumuna Yazar izleme katılımcı sağlar. Katılımcı bir iş akışı hizmeti yapılandırma dosyasında bir izleme özgü davranış ekleyerek yapılandırılır. Bir ETW etkinleştirme, izleme katılımcı olmasını kayıtları izleme Olay Görüntüleyicisi görüntülenemez sağlar. SDK'sı örneği ETW tabanlı izleme, ETW tabanlı izleme katılımcı kullanılarak WF izlemeyle hakkında bilgi edinmek için iyi bir yoludur.  
  
## <a name="etw-tracking-participant"></a>ETW İzleme katılımcı  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]bir ETW İzleme izleme kayıtları ETW oturumuna yazan Katılımcısı içerir. Bu, uygulamanızın performansı veya sunucunun işleme için en az etkiyle çok verimli bir şekilde gerçekleştirilir. Standart ETW İzleme katılımcı kullanmanın avantajı, aldığı izleme kayıtları başka bir uygulama ile görüntülenebilir ve Windows Olay Görüntüleyicisi'nde sistem günlüklerini olmasıdır.  
  
 Standart ETW İzleme katılımcı Web.config dosyasında aşağıdaki örnekte gösterildiği gibi yapılandırılır.  
  
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
>  Varsa bir `trackingProfile` adı belirtilmezse, gibi yalnızca `<etwTracking/>` veya `<etwTracking profileName=""/>`, ardından varsayılan profil yüklenmiş izleme [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] Machine.config dosyası kullanılır.  
  
 Machine.config dosyasının varsayılan profili izleme, iş akışı örneği kayıtlarını ve hataları için abone olur.  
  
 ETW ETW oturum sağlayıcı kimliğini üzerinden yazılır Sağlayıcı için ETW İzleme yazma katılımcı kullanır izleme ETW kayıt kimliği, Web.config dosyasının tanılama bölümünde tanımlanır (altında `<system.serviceModel><diagnostics>`). Varsayılan olarak, bir belirtilmemiş olduğunda ETW İzleme katılımcı aşağıdaki örnekte gösterildiği gibi bir varsayılan sağlayıcı kimliği kullanır.  
  
```xml  
<system.serviceModel>  
        <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />  
```  
  
 Aşağıdaki çizimde ETW İzleme katılımcı verilerine izleme akışı gösterilmektedir. İzleme verilerini ETW oturum ulaştığında, çeşitli yollarla erişilebilir. Bu olaylar erişmek için en kullanışlı yollarından biri, Olay Görüntüleyicisi'ni günlüklerine ve izlemelere uygulamaları ve hizmetleri görüntülemek için kullanılan genel bir Windows aracı aracılığıyladır.  
  
 ![İzleme ve ETW İzleme Sağlayıcısı akışını](../../../docs/framework/windows-workflow-foundation/media/trackingdatathroughetwparticipant.gif "TrackingDatathroughETWParticipant")  
  
## <a name="tracking-participant-event-data"></a>Katılımcı olay verilerini izleme  
 İzleme katılımcı ETW oturum izleme kaydı başına bir olay biçiminde izlenen olay verilerini serileştirir.  Bir olay kimliği 100 199 ile aralığında kullanılarak tanımlanır. İzleme olay tanımları için bkz: kayıtları izleme katılımcı tarafından gösterilen [olayları başvuru izleme](../../../docs/framework/windows-workflow-foundation/tracking-events-reference.md) konu.  
  
 ETW olay boyutu ETW arabellek boyutuyla sınırlıdır veya ETW olay en fazla yük tarafından hangi küçük değerdir. Olay boyutu ya da bu ETW sınırları aşarsa, olay kesilir ve içeriği rasgele bir şekilde kaldırıldı. Değişkenleri, bağımsız değişken, ek açıklamalar ve özel verileri seçmeli olarak kaldırılmaz. Kesilmesi durumunda, bunların tümü olay boyutu ETW sınırının aşılmasına neden değer bağımsız olarak kısaltılır.  Kaldırılan verileri ile değiştirilir `<item>..<item>`.  
  
 Karmaşık türleri değişkenleri, bağımsız ve özel veri öğeleri ETW olayını kullanarak kaydı serileştirilir [NetDataContractSerializer sınıfı](http://go.microsoft.com/fwlink/?LinkId=177537). Bu sınıf CLR türünün serileştirilmiş XML akışı bilgilerdir.  
  
 ETW sınırları nedeniyle yük verilerinin kesilmesi ETW oturumuna gönderilen yinelenen izleme kayıtları neden olabilir. Birden fazla oturum olaylarını dinleme ve oturumları olayları için farklı yükü sınırları varsa bu durum ortaya çıkabilir.  
  
 Alt sınırı ile oturumu için olay kesilebilir. ETW İzleme katılımcı olaylarını dinleme oturum sayısını bilgisi yok; bir olay bir oturum sonra bir kez olay gönderme ETW katılımcı yeniden deneme kesilirse. Bu durumda daha büyük bir yükü boyutu kabul edecek şekilde yapılandırılmış oturum olay iki kez (kesilmiş olmayan ve kesilmiş olay) alır. Çoğaltma ile aynı arabellek boyutu sınırları tüm ETW oturumları yapılandırarak engellenebilir.  
  
## <a name="accessing-tracking-data-from-an-etw-participant-in-the-event-viewer"></a>Olay Görüntüleyicisi'ni bir ETW Katılımcısı veri izlemeyi erişme  
 ETW oturumuna ETW İzleme katılımcı tarafından yazılan olaylar (varsayılan sağlayıcı kimliği kullanırken) Olay Görüntüleyicisi'ni erişilebilir. Bu iş akışı tarafından gösterilen kayıtları izleme hızlı bir şekilde görüntülemek için sağlar.  
  
> [!NOTE]
>  Bir ETW oturum kullanım olay kimlikleri 100 199 ile aralığında yayılan kayıt olayları izleme.  
  
#### <a name="to-enable-viewing-the-tracking-records-in-event-viewer"></a>Olay Görüntüleyicisi'nde izleme kayıtları görüntüleme etkinleştirmek için  
  
1.  Olay Görüntüleyicisi'ni (EVENTVWR. Başlat EXE)  
  
2.  Seçin **Olay Görüntüleyicisi'ni, uygulama ve hizmet günlükleri, Microsoft, Windows, uygulama uygulamalarının**.  
  
3.  Sağ tıklayın ve emin **görünümü, Analitik ve hata ayıklama günlüklerini göster** seçilir. Aksi durumda, yanındaki onay işareti göründüğü şekilde seçin. Bu görüntüler **analitik**, **Perf**, ve **hata ayıklama** günlükleri.  
  
4.  Sağ **analitik** oturum açın ve ardından **günlüğü etkinleştir**. Günlük %SystemRoot%\System32\Winevt\Logs\Microsoft-Windows-Application Server-Applications%4Analytic.etl dosyasında bulunur.  
  
## <a name="custom-tracking-participant"></a>Özel İzleme katılımcı  
 İzleme katılımcı API izleme kayıtları iş akışı çalışma zamanı tarafından gösterilen işlemek için Özel mantık içerebilir bir kullanıcı tarafından sağlanan izleme katılımcı ile izleme çalışma zamanı uzantısı sağlar. Özel İzleme katılımcı yazmak için geliştirici uygulamalıdır `Track` yöntemi <xref:System.Activities.Tracking.TrackingParticipant> sınıfı. Bir izleme kaydı iş akışı çalışma zamanı tarafından gösterilen zaman bu yöntem çağrılır.  
  
 İzleme katılımcıları türetilen <xref:System.Activities.Tracking.TrackingParticipant> sınıfı. Sistem tarafından sağlanan <xref:System.Activities.Tracking.EtwTrackingParticipant> alınan her izleme kaydı için bir olay izleme için Windows (ETW) olayı yayar. Özel İzleme katılımcı oluşturmak için bir sınıf oluşturulur türetilen <xref:System.Activities.Tracking.TrackingParticipant>. Temel izleme işlevselliği sağlamak için geçersiz kılma <xref:System.Activities.Tracking.TrackingParticipant.Track%2A>. <xref:System.Activities.Tracking.TrackingParticipant.Track%2A>bir izleme kaydını çalışma zamanı tarafından gönderilen ve istenen biçimde işlenen olarak adlandırılır. Aşağıdaki örnekte, bir özel izleme katılımcı sınıf konsol penceresine tüm izleme kayıtları gösterdiği tanımlanır. Ayrıca uygulayabileceğiniz bir <xref:System.Activities.Tracking.TrackingParticipant> izleme işlemleri nesne kayıtları zaman uyumsuz olarak kullanarak kendi `BeginTrack` ve `EndTrack` yöntemleri  
  
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
  
 Belirli izleme katılımcı kullanmak için aşağıdaki örnekte gösterildiği gibi izlemek için istediğiniz iş akışı örneği ile kaydedin.  
  
```csharp  
myInstance.Extensions.Add(new ConsoleTrackingParticipant());  
```  
  
 Aşağıdaki örnekte, bir iş akışı, oluşur bir <xref:System.Activities.Statements.Sequence> içeren etkinliği bir <xref:System.Activities.Statements.WriteLine> etkinlik oluşturulur. `ConsoleTrackingParticipant` Uzantılara eklenir ve iş akışı çağrılır.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Server App Fabric izleme](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [App Fabric ile uygulamaları izleme](http://go.microsoft.com/fwlink/?LinkId=201275)
