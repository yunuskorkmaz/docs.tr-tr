---
title: İş Akışı Hizmeti Ana Bilgisayar Dahili Bileşenleri
ms.date: 03/30/2017
ms.assetid: af44596f-bf6a-4149-9f04-08d8e8f45250
ms.openlocfilehash: b95a59b0e1715b3cc18ccfea44d6c4ccd04ca5ad
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184171"
---
# <a name="workflow-service-host-internals"></a>İş Akışı Hizmeti Ana Bilgisayar Dahili Bileşenleri
<xref:System.ServiceModel.WorkflowServiceHost>iş akışı hizmetleri için bir ana bilgisayar sağlar. Gelen iletileri dinlemekten ve bunları uygun iş akışı hizmeti örneğine yönlendirmekten sorumludur, boşta kalan iş akışlarının boşaltılmasını ve kalıcı hale getirinve daha fazlasını denetler. Bu konu, WorkflowServiceHost'un gelen iletileri nasıl işlediğini açıklar.  
  
## <a name="workflowservicehost-overview"></a>İş AkışıServiceHost Genel Bakış  

Sınıf, <xref:System.ServiceModel.WorkflowServiceHost> iş akışı hizmetlerini barındırmak için kullanılır. Gelen iletileri dinler ve bunları uygun servis örneğine yönlendirir, yeni örnekler oluşturur veya gerektiğinde dayanıklı depolamadan varolan örnekleri yükler. Aşağıdaki diyagram, nasıl <xref:System.ServiceModel.WorkflowServiceHost> çalıştığını yüksek düzeyde göstermektedir:
  
 ![İş Akışı Hizmeti Ana Bilgisayarı'na genel bir bakış gösteren diyagram.](./media/workflow-service-host-internals/workflow-service-host-high-level-overview.gif)  
  
 Bu diyagram, <xref:System.ServiceModel.WorkflowServiceHost> .xamlx dosyalarından iş akışı hizmeti tanımlarını yükler ve yapılandırma dosyalarından yapılandırma bilgilerini yükler gösterir. Ayrıca izleme profilinden izleme yapılandırmasını yükler. <xref:System.ServiceModel.WorkflowServiceHost>denetim işlemlerini iş akışı örneklerine göndermenize olanak tanıyan bir iş akışı denetimi bitiş noktasını ortaya çıkarır.  Daha fazla bilgi için Bkz. [İş Akışı Denetimi Bitiş Noktası örneği.](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md)  
  
 <xref:System.ServiceModel.WorkflowServiceHost>ayrıca gelen uygulama iletilerini dinleyen uygulama uç noktalarını da ortaya çıkarır. Gelen bir ileti geldiğinde, ilgili iş akışı hizmeti örneğine gönderilir (şu anda yüklenmişse). Gerekirse yeni bir iş akışı örneği oluşturulur. Veya varolan bir örnek kalıcı hale geçmişse, kalıcılık deposundan yüklenir.  
  
## <a name="workflowservicehost-details"></a>İş AkışıServiceHost Detayları  
 Aşağıdaki diyagram, <xref:System.ServiceModel.WorkflowServiceHost> iletileri biraz daha ayrıntılı olarak nasıl işleyeceğini gösterir:  
  
 ![İş Akışı Hizmeti Ana Bilgisayar ileti akışını gösteren diyagram.](./media/workflow-service-host-internals/workflow-service-host-message-flow.gif)  
  
 Bu diyagram üç farklı uç nokta, bir uygulama bitiş noktası, bir iş akışı denetimi bitiş noktası ve bir iş akışı barındırma bitiş noktasını gösterir. Uygulama bitiş noktası, belirli bir iş akışı örneği için bağlı iletileri alır. İş akışı denetimi uç noktası denetim işlemleri için dinler. Uç noktayı barındıran iş akışı, hizmet <xref:System.ServiceModel.WorkflowServiceHost> dışı iş akışlarını yüklemeye ve yürütmeye neden olan iletileri dinler. Diyagramda gösterildiği gibi tüm iletiler WCF çalışma süresi boyunca işlenir.  İş akışı hizmeti örnek azaltma <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> özelliği kullanılarak elde edilir. Bu özellik eşzamanlı iş akışı hizmeti örneklerinin sayısını sınırlandıracaktır. Bu gaz yeni iş akışı hizmeti örnekleri için ek istekler aşıldığında veya kalıcı iş akışı örneklerini etkinleştirme istekleri sıraya alınır. Sıralanan istekler, yeni bir örnek veya çalışan, kalıcı bir örnek için istek olup olmadıklarına bakılmaksızın FIFO sırasına göre işlenir. İşlenmemiş özel durumların nasıl ele alınılacağını ve boşta kalan iş akışı hizmetlerinin nasıl boşaltılacağını ve kalıcı olduğunu belirleyen ana bilgisayar ilkesi bilgileri yüklenir. Bu konular hakkında daha fazla bilgi [için bkz: İş Akışı İş Akışı İşlenmemiş Özel Durum Davranışını İş Akışı Hizmeti Host ile Yapılandırın](../../../../docs/framework/wcf/feature-details/config-workflow-unhandled-exception-workflowservicehost.md) ve [Nasıl Yapılır: Boşta Kalan Davranışı WorkflowServiceHost ile yapılandırma.](../../../../docs/framework/wcf/feature-details/how-to-configure-idle-behavior-with-workflowservicehost.md) İş akışı örnekleri ana bilgisayar ilkelerine göre kalıcıdır ve gerektiğinde yeniden yüklenir. İş akışı kalıcılığı hakkında daha fazla bilgi için [bkz: Nasıl: İş AkışıServiceHost ile Kalıcılığı Yapılandırma,](../../../../docs/framework/wcf/feature-details/how-to-configure-persistence-with-workflowservicehost.md) [Uzun süren Bir İş Akışı Hizmeti Oluşturma](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md)ve İş Akışı [Kalıcılığı](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md).  
  
 Aşağıdaki resimde WorkflowServiceHost.Open çağrıldığında akış gösterir:  
  
 ![WorkflowServiceHost.Open çağrıldığında akışı gösteren diyagram.](./media/workflow-service-host-internals/workflow-service-host-open.gif)  
  
 İş akışı XAML'den yüklenir ve etkinlik ağacı oluşturulur. <xref:System.ServiceModel.WorkflowServiceHost>etkinlik ağacını yürüer ve hizmet açıklamasını oluşturur. Yapılandırma ana bilgisayara uygulanır. Son olarak ev sahibi gelen iletileri dinlemeye başlar.  
  
 Aşağıdaki resimde, CanCreateInstance olarak ayarlanmış bir Alma etkinliği için bağlı bir ileti aldığında ne <xref:System.ServiceModel.WorkflowServiceHost> yaptığı `true`gösterilmektedir:  
  
 ![WFS Ana Bilgisayar tarafından bir ileti aldığında ve CanCreateInstance doğru olduğunda kullanılan karar ağacı.](./media/workflow-service-host-internals/workflow-service-host-receive-message-cancreateinstance.gif)  
  
 İleti gelir ve WCF kanal yığını tarafından işlenir. Throttles denetlenir ve korelasyon sorguları yürütülür. İleti varolan bir örneğe bağlıysa ileti teslim edilir. Yeni bir örnek oluşturulması gerekiyorsa, Al etkinliğinin CanCreateInstance özelliği denetlenir. Doğru olarak ayarlanırsa, yeni bir örnek oluşturulur ve ileti teslim edilir.  
  
 Aşağıdaki resimde, CanCreateInstance'ı yanlış olarak ayarlanmış bir Alma etkinliği için bağlı bir ileti aldığında ne <xref:System.ServiceModel.WorkflowServiceHost> yaptığı gösterilmektedir.  
  
 ![WFS Ana Bilgisayar tarafından bir ileti aldığında ve CanCreateInstance yanlış olduğunda kullanılan karar ağacı.](./media/workflow-service-host-internals/workflow-service-host-receive-message.gif)  
  
 İleti gelir ve WCF kanal yığını tarafından işlenir. Throttles denetlenir ve korelasyon sorguları yürütülür. İleti varolan bir örneğe bağlanır (CanCreateInstance yanlış olduğundan) böylece örnek kalıcılık deposundan yüklenir, yer imi devam ettirilir ve iş akışı yürütülür.  
  
> [!WARNING]
> SQL Server yalnızca AdPipe protokolünde dinleyecek şekilde yapılandırılırsa, İş Akışı Hizmeti Ana Bilgisayarı açılmaz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Hizmetleri](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [İş Akışı Hizmetlerini Barındırma](../../../../docs/framework/wcf/feature-details/hosting-workflow-services.md)
- [İş Akışı Denetim Uç Noktası](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md)
- [Nasıl yapılır: WorkflowServiceHost ile İş Akışı Tarafından İşlenmeyen Özel Durum Davranışını Yapılandırma](../../../../docs/framework/wcf/feature-details/config-workflow-unhandled-exception-workflowservicehost.md)
- [Uzun Süre Çalışan Bir İş Akışı Hizmeti Oluşturma](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md)
- [İş Akışı Kalıcılığı](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)
