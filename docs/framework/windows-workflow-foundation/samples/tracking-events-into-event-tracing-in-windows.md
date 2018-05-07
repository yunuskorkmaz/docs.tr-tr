---
title: Windows'da izleme olayı içine olayları izleme
ms.date: 03/30/2017
ms.assetid: f812659b-0943-45ff-9430-4defa733182b
ms.openlocfilehash: 82de8ee74c12019f815adc63f2ca4441ad95d325
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="tracking-events-into-event-tracing-in-windows"></a>Windows'da izleme olayı içine olayları izleme
Bu örnek, Windows Workflow Foundation (WF) iş akışı hizmeti üzerinde izleme etkinleştirin ve izleme olayları, olay izleme için Windows (ETW) yayma gösterilmiştir. Örnek iş akışı kayıtları ETW İzleme yaymak üzere ETW İzleme katılımcı kullanır (<xref:System.Activities.Tracking.EtwTrackingParticipant>).  
  
 Örnek iş akışında bir istek alırsa, giriş verilerinin devrik giriş değişkenine atar ve istemciye karşılıklı geri döndürür. Giriş verisi 0 olduğunda, bir sıfıra bölünme sıfır özel durum, işlenmemiş oluşan iptal etmek iş akışı neden olur. İzleme özelliği etkinleştirilmiş olan hata izleme kaydı hata daha sonra gidermenize yardımcı olacak ETW yayınlanır. ETW İzleme katılımcı kayıtları izleme için abone olmak için izleme profili ile yapılandırılır. İzleme profili Web.config dosyasında tanımlanmış ve bir yapılandırma parametresi ETW İzleme katılımcı sağlanan. ETW İzleme katılımcı iş akışı hizmeti Web.config dosyasında yapılandırılmış ve hizmet hizmet davranışı olarak uygulanır. Bu örnekte, Olay Görüntüleyicisi'ni kullanarak olay günlüğünde izleme olayları görüntüleyin.  
  
## <a name="workflow-tracking-details"></a>İş Akışı İzleme Ayrıntıları  
 Windows Workflow Foundation iş akışı örneğini yürütmeyi izlemek üzere bir izleme altyapısı sağlar. İzleme çalışma zamanı iş akışı yaşam döngüsü olayları için iş akışı etkinlikleri ve özel olaylar ilgili olayları yaymak üzere bir iş akışı örneği oluşturur. Aşağıdaki tabloda birincil bileşenleri izleme altyapısının ayrıntılı olarak açıklanmaktadır.  
  
|Bileşen|Açıklama|  
|---------------|-----------------|  
|Çalışma zamanı izleme|İzleme kayıtları yayma için altyapı sağlar.|  
|Katılımcıların izleme|İzleme kayıtları erişir. [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] Olay izleme için Windows (ETW) olayları olarak izleme kayıtları Yazar izleme katılımcı birlikte verilir.|  
|İzleme profili|Bir iş akışı örneğinden yayılan izleme kayıtları alt kümeleri için abone olmak izleme katılımcı sağlayan bir filtreleme mekanizması.|  
  
 Aşağıdaki tabloda, iş akışı çalışma zamanı yayar izleme kayıtları ayrıntıları verilmektedir.  
  
|İzleme kaydı|Açıklama|  
|---------------------|-----------------|  
|İş akışı örneği izleme kaydeder.|İş akışı örneği yaşam döngüsü açıklar. Örneğin, iş akışı başlatıldığında veya tamamlandıktan bir örnek kaydı yayınlanır.|  
|Etkinlik durumu izleme kaydeder.|Ayrıntılar Etkinlik yürütme. Bu kayıtları bir etkinlik olduğunda zamanlanmış veya etkinlik tamamlandığında veya bir hata olduğunda atılır gibi bir iş akışı etkinlik durumunu belirtir.|  
|Sürdürme kayıt yer işareti.|Bir iş akışı örneği yer işareti sürdürüldü her yayılan.|  
|Özel İzleme kaydeder.|Bir iş akışı yazarı özel izleme kayıtları oluşturmak ve bunları içinde özel Etkinlik yayma.|  
|<xref:System.Activities.Tracking.ActivityScheduledRecord>|Bir etkinliği başka bir etkinliğin zamanlarken bu kaydı yayınlanır.|  
|<xref:System.Activities.Tracking.FaultPropagationRecord>|Bir arıza etkinliği yayıldığında, bu kayıt yayınlanır.|  
|<xref:System.Activities.Tracking.CancelRequestedRecord>|Bir etkinliği başka bir etkinlik tarafından iptal edildiğinde bu kaydı yayınlanır.|  
  
 İzleme katılımcı izleme profilleri kullanarak verilmiş izleme kayıtları bir kısmı için abone olur. İzleme profili belirli izleme kayıt türü için abone izin izleme sorgularını içerir. Profilleri izleme kod veya yapılandırma belirtilebilir.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], EtwTrackingParticipantSample.sln çözüm dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
3.  Çözümü çalıştırmak için F5 tuşuna basın.  
  
     Varsayılan olarak, hizmet 53797 bağlantı noktasında dinleme (http://localhost:53797/SampleWorkflowService.xamlx).  
  
4.  Kullanarak [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], WCF test İstemcisi'ni açın.  
  
     WCF test istemcisi (WcfTestClient.exe) bulunan \< [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] yükleme klasörü > \Common7\IDE\ klasör.  
  
     Varsayılan [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] yükleme klasörüdür C:\Program Files\Microsoft Visual Studio 10.0.  
  
5.  WCF test istemcisi seçin **Hizmet Ekle** gelen **dosya** menüsü.  
  
     Uç nokta adresi giriş kutusuna ekleyin. Varsayılan, http://localhost:53797/SampleWorkflowService.xamlx değeridir.  
  
6.  Olay Görüntüleyicisi'ni uygulamasını açın.  
  
     Olay Görüntüleyicisi'nden başlatmak Hizmeti'ni çağırmadan önce **Başlat** menüsünde, select **çalıştırmak** ve yazın `eventvwr.exe`. Olay günlüğü iş akışı hizmetinden gösterilen olayları izlemek için dinlediğinden emin olun.  
  
7.  Olay Görüntüleyicisi'ni ağaç görünümünde gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, ve **Microsoft**. Sağ **Microsoft** seçip **Görünüm** ve ardından **Analitik ve hata ayıklama günlüklerini göster** etkinleştirme Analitik ve hata ayıklama günlüklerini  
  
     Emin **Analitik ve hata ayıklama günlüklerini göster** seçeneği denetlenir.  
  
8.  Olay Görüntüleyicisi'nde ağaç görünümünde gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**,  **Uygulama sunucusu-uygulamalar**. Sağ **analitik** seçip **günlüğü etkinleştir** etkinleştirmek için **analitik** günlük.  
  
9. Çift tıklatarak WCF test istemcisi kullanarak hizmeti test `GetData`.  
  
     Bu açılır `GetData` yöntemi. İstek bir parametre kabul eder ve değeri 0, varsayılan olan olmasını sağlar.  
  
     Tıklatın **çağırma**.  
  
10. İş akışını gösterilen olayları gözlemektir.  
  
     Olay Görüntüleyici'ye geçiş yapın ve gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**,  **Uygulama sunucusu-uygulamalar**. Sağ **analitik** seçip **yenileme**.  
  
     İş akışı olayları Olay Görüntüleyicisi'nde görüntülenir. İş akışı yürütme olayları görüntülenir ve bunlardan birini iş akışında hata karşılık gelen işlenmeyen bir özel durum olduğuna dikkat edin. Ayrıca, bir uyarı olayı etkinliği bir arıza atma olduğunu gösteren iş akışı etkinliğinden yayınlanır.  
  
11. Herhangi bir hata durum 9 ve 10 veri 0 dışında bir girdi ile adımları yineleyin.  
  
 İzleme profili, bir iş akışı örneğinin durumu değiştiğinde, çalışma zamanı tarafından gösterilen olaylarına abone olma olanak tanır. İzleme gereksinimlerinize bağlı olarak çok kaba bir profili oluşturabilirsiniz, üst düzey durum değişiklikleri bir iş akışında, küçük bir kümesini için abone olur. Diğer taraftan, çıktısı yürütme daha sonra yeniden oluşturmak için zengin çok hassas bir profil oluşturabilirsiniz. Örnek iş akışı çalışma zamanı ETW kullanmaya gösterilen olayları gösterir `HealthMonitoring Tracking Profile`, olaylar, küçük bir kümesini yayar. Daha fazla iş akışı olayları izleme yayar farklı bir profil de adlı Web.config dosyasında sağlanan `Troubleshooting Tracking Profile`. Zaman [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] olan yüklü, boş bir ada sahip bir varsayılan profili Machine.config dosyasında yapılandırılır. Bu profil profil adı yok veya boş profil adı belirtildiğinde davranış yapılandırma izleme ETW tarafından kullanılır.  
  
 Sistem durumu izleme profili izleme, iş akışı örneği kayıtları ve etkinlik hataya yayma kayıtları yayar. Bu profili, bir Web.config yapılandırma dosyası için aşağıdaki izleme profili ekleyerek oluşturulur.  
  
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
  
2.  Gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**, **uygulama Sunucu uygulamaları**. Sağ **analitik** seçip **günlüğü devre dışı**.  
  
3.  Gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**, **uygulama Sunucu uygulamaları**. Sağ **analitik** seçip **Günlüğü Temizle**.  
  
4.  Seçin **temizleyin** olayları temizlemek için seçeneği.  
  
## <a name="known-issue"></a>Bilinen bir sorun  
  
> [!NOTE]
>  Olay burada ETW olayları çözecek başlatılamayabilir Görüntüleyicisi'nde bilinen bir sorun yoktur. Aşağıdakine benzer bir hata iletisi görebilirsiniz.  
>   
>  Olay kimliği için açıklama \<kimliği > kaynağından Microsoft Windows uygulaması uygulamalarının bulunamıyor. Bu olayı oluşturan bileşen, yerel bilgisayarda yüklü değil ya da yüklemesi bozuk. Yükleme veya yerel bilgisayarda bileşen onarın.  
>   
>  Bu hatayla karşılaşırsanız, Eylemler bölmesinde Yenile'yi tıklatın. Olay şimdi düzgün bir şekilde kod çözme.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\EtwTracking`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric izleme örnekleri](http://go.microsoft.com/fwlink/?LinkId=193959)
