---
title: Olaya içinde Windows izleme olayları izleme
ms.date: 03/30/2017
ms.assetid: f812659b-0943-45ff-9430-4defa733182b
ms.openlocfilehash: 70c75be09528b31572bdf0dc322af5bcd7e3ca5d
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48837290"
---
# <a name="tracking-events-into-event-tracing-in-windows"></a>Olaya içinde Windows izleme olayları izleme
Bu örnek, Windows Workflow Foundation (WF) iş akışı hizmeti izleme etkinleştirme ve izleme olayları, olay izleme için Windows (ETW) yayma gösterir. Örnek iş akışı ETW kayıtları izleme yaymak için ETW İzleme katılımcı kullanır (<xref:System.Activities.Tracking.EtwTrackingParticipant>).

 Örnek iş akışında bir istek alırsa, giriş verilerinin karşıtını giriş değişkenine atar ve istemciye karşılıklı geri döndürür. Giriş verilerini 0 olduğunda sıfır özel durum ile bir bölme, işlenmemiş oluşan iptal etmek iş akışının sağlar. Etkin izleme ile hata izleme kaydının daha sonra hata gidermenize yardımcı olacak ETW yayılır. ETW İzleme katılımcı abone izleme kayıtları için bir izleme profili ile yapılandırılır. İzleme profili Web.config dosyasında tanımlanır ve ETW İzleme katılımcı için bir yapılandırma parametresi sağlanan. ETW İzleme katılımcı iş akışı hizmetinin Web.config dosyasında yapılandırılmış ve hizmeti bir hizmet davranışı olarak uygulanır. Bu örnekte, Olay Görüntüleyicisi'ni kullanarak olay günlüğüne izleme olayları görüntüleyin.

## <a name="workflow-tracking-details"></a>İş Akışı İzleme Ayrıntıları
 Windows Workflow Foundation iş akışı örneği yürütülmesini izlemek için izleme altyapısı sağlar. İzleme çalışma zamanı olaylarını, iş akışı yaşam döngüsü için iş akışı etkinlikleri ve özel olaylar ilgili olayları yaymak için bir iş akışı örneği oluşturur. Aşağıdaki tabloda birincil izleme altyapısının bileşenleri ayrıntıları.

|Bileşen|Açıklama|
|---------------|-----------------|
|Çalışma zamanı izleme|İzleme kayıtları yaymak için altyapı sağlar.|
|İzleme katılımcıları|İzleme kayıtları erişir. [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] izleme kayıtları için olay izleme Windows (ETW) olayları olarak yazan bir izleme katılımcı birlikte verilir.|
|İzleme profili|Bir iş akışı örneğinden yayılan izleme kayıtları bir alt kümesi için abone olmak izleme Katılımcısı sağlayan bir filtreleme mekanizması.|

 Aşağıdaki tabloda, iş akışı çalışma zamanı yayan izleme kayıtları ayrıntıları.

|Kayıt izleme|Açıklama|
|---------------------|-----------------|
|İş akışı örneği izleme kayıtları.|İş akışı örneği yaşam döngüsü açıklar. Örneğin, iş akışı başlatıldığında veya tamamlanan bir örnek kaydı yayınlanır.|
|Etkinlik durumu izleme kayıtları.|Etkinlik yürütme ayrıntıları. Bu kayıtlar, bir etkinlik olduğunda zamanlanmış etkinlik tamamlandığında veya bir hata harekete geçirildiğinde gibi bir iş akışı etkinlik durumunu gösterir.|
|Sürdürme kayıt yer işareti.|Her bir iş akışı örneği içinde yer sürdürüldü yayılır.|
|Özel izleme kayıtları.|Bir iş akışı Yazar özel izleme kayıtları oluşturabilir ve bunları özel bir etkinlik içinde gösterin.|
|<xref:System.Activities.Tracking.ActivityScheduledRecord>|Bu kayıt, bir etkinlik başka bir etkinlik zamanlarken yayınlanır.|
|<xref:System.Activities.Tracking.FaultPropagationRecord>|Bu kayıt, bir hata etkinliği yayıldığında yayınlanır.|
|<xref:System.Activities.Tracking.CancelRequestedRecord>|Bu kayıt, başka bir etkinlik tarafından bir etkinlik iptal edildiğinde yayınlanır.|

 İzleme profilleri kullanarak yayılan izleme kayıtları bir alt kümesi için izleme katılımcı abone. Bir izleme profili belirli izleme kayıt türü için abone izin izleme sorguları içerir. İzleme profilleri kod veya yapılandırma belirtilebilir.

#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için

1.  Visual Studio 2010 kullanarak EtwTrackingParticipantSample.sln çözüm dosyasını açın.

2.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.

3.  Çözümü çalıştırmak için F5 tuşuna basın.

     Varsayılan olarak, hizmet bağlantı noktasını 53797 dinlediğini (http://localhost:53797/SampleWorkflowService.xamlx).

4.  Kullanarak [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], WCF test İstemcisi'ni açın.

     WCF test istemcisi (WcfTestClient.exe) bulunan \<Visual Studio 2010 yükleme klasörü > \Common7\IDE\ klasör.

     Varsayılan Visual Studio 2010 yükleme klasörü C:\Program Files\Microsoft Visual Studio 10.0 ' dir.

5.  WCF test İstemcisi'nde seçin **Hizmet Ekle** gelen **dosya** menüsü.

     Uç nokta adresi giriş kutusuna ekleyin. Varsayılan, `http://localhost:53797/SampleWorkflowService.xamlx` değeridir.

6.  Olay Görüntüleyici uygulamasını açın.

     Hizmeti'ni çağırmadan önce Olay Görüntüleyicisi'ni Başlat **Başlat** menüsünde **çalıştırma** ve yazın `eventvwr.exe`. İş akışı hizmetinden yayılan olayları izlemek için olay günlüğüne dinlediğinden emin olun.

7.  Olay Görüntüleyicisi'nin ağaç görünümünde gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, ve **Microsoft**. Sağ **Microsoft** seçip **görünümü** ve ardından **Analitik ve hata ayıklama günlüklerini göster** analitik etkinleştirmek ve hata ayıklama günlükleri için

     Emin **Analitik ve hata ayıklama günlüklerini göster** seçeneği denetlenir.

8.  Olay Görüntüleyicisi'nde ağaç görünümünde gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**,  **Uygulama uygulamalarının**. Sağ **analitik** seçip **günlüğü etkinleştir** etkinleştirmek için **analitik** günlük.

9. Çift tıklayarak WCF test İstemcisi'ı kullanarak hizmeti test `GetData`.

     Bu açılır `GetData` yöntemi. İstek bir parametreyi kabul eden ve varsayılan değer 0, olmasını sağlar.

     Tıklayın **çağırma**.

10. Yayılan olayları gözlemektir.

     Olay Görüntüleyicisi'ne geçin ve gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**,  **Uygulama uygulamalarının**. Sağ **analitik** seçip **Yenile**.

     İş akışı olayları Olay Görüntüleyicisi'nde görüntülenir. İş akışı yürütme olayları görüntülenir ve bunlardan birinin iş akışı hataya karşılık gelen işlenmeyen bir özel durum olduğuna dikkat edin. Ayrıca, bir uyarı olayı etkinliği bir hata atma olduğunu gösteren iş akışı etkinliklerine ilişkin yayılır.

11. Adım 9 ve 10 veri 0 dışında bir giriş ile hata oluşturulmayacak şekilde yineleyin.

 İzleme profilleri, bir iş akışı örneği durumu değiştiğinde yayılan çalışma zamanı tarafından iş olaylarına abone olma olanak tanır. İzleme gereksinimlerinize bağlı olarak çok kaba bir profili oluşturabilmeniz için bir iş akışı üzerinde üst düzey durum değişikliklerini küçük bir kümesi için abone olur. Öte yandan, çıktısı yürütme daha sonra yeniden oluşturmak için zengin çok hassas bir profil oluşturabilirsiniz. Örnek iş akışı çalışma zamanını şuradan ETW kullanmaya yayılan olayları gösterir `HealthMonitoring Tracking Profile`, olayları küçük bir dizi yayar. Daha fazla iş akışı olayları izleme yayan farklı bir profil de adlı Web.config sağlanır `Troubleshooting Tracking Profile`. Zaman [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] olan yüklü, boş bir ada sahip bir varsayılan profili Machine.config dosyasında yapılandırılır. Bu profil davranışını yapılandırma profili adı yok ya da boş bir profil adı belirtildiğinde, izleme, ETW tarafından kullanılır.

 Sistem durumu izleme profili izleme, iş akışı örneği kayıtları ve etkinlik hata yayma kayıtları gösterir. Bu profil, aşağıdaki izleme profili Web.config yapılandırma dosyasına ekleyerek oluşturulur.

```xml
<<tracking>
      <profiles>
        <trackingProfile name="HealthMonitoring Tracking Profile">
          <workflow activityDefinitionId="*">
            <workflowInstanceQueries>
              <workflowInstanceQuery>
                <states>
                  <state name="Started"/>
                  <state name="Completed"/>
                  <state name="Aborted"/>
                  <state name="UnhandledException"/>
                </states>
            </workflowInstanceQuery>
           </workflowInstanceQueries>
            <faultPropagationQueries>
              <faultPropagationQuery faultSourceActivityName ="*" faultHandlerActivityName="*"/>
            </faultPropagationQueries>
          </workflow>
        </trackingProfile>
       </profiles>
</tracking>
```

 Profil değiştirerek değiştirilebilir `EtwTrackingParticipant` aşağıdaki yapılandırma.

```xml
<behaviors>
      <serviceBehaviors>
        <behavior>
          <etwTracking profileName="HealthMonitoring Tracking Profile"/>
        </behavior>
      </serviceBehaviors>
    </behaviors>
```

#### <a name="to-clean-up-optional"></a>(İsteğe bağlı) temizlemek için

1.  Olay Görüntüleyicisi'ni açın.

2.  Gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**, **uygulama Sunucu uygulamaları**. Sağ **analitik** seçip **devre dışı günlük**.

3.  Gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**, **uygulama Sunucu uygulamaları**. Sağ **analitik** seçip **Günlüğü Temizle**.

4.  Seçin **Temizle** olayları silmek için seçeneği.

## <a name="known-issue"></a>Bilinen sorun

> [!NOTE]
>  Burada ETW olaylarının kodunu çözmek için çalışmayabilir Olay Görüntüleyicisi'nde bilinen bir sorun yoktur. Aşağıdakine benzer bir hata iletisi görebilirsiniz.
>
>  Olay kimliği için açıklama \<kimliği > kaynağından Microsoft Windows uygulaması uygulamalarının bulunamıyor. Bu olayı oluşturan bileşen, yerel bilgisayarınızda yüklü değil veya yüklemenin bozuk. Yüklediğinizde veya yerel bilgisayarda bileşen onarın.
>
>  Bu hatayla karşılaşırsanız, yenileme Eylemler bölmesinde'e tıklayın. Olay artık düzgün bir şekilde kod çözme.

> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\EtwTracking`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric izleme örnekleri](https://go.microsoft.com/fwlink/?LinkId=193959)
