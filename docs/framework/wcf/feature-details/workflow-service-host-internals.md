---
title: İş Akışı Hizmeti Ana Bilgisayar Dahili Bileşenleri
ms.date: 03/30/2017
ms.assetid: af44596f-bf6a-4149-9f04-08d8e8f45250
ms.openlocfilehash: 7b47293211ee8143b1ce713c64ff1d5b22161b45
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594887"
---
# <a name="workflow-service-host-internals"></a>İş Akışı Hizmeti Ana Bilgisayar Dahili Bileşenleri
<xref:System.ServiceModel.WorkflowServiceHost>iş akışı hizmetleri için bir konak sağlar. Gelen iletileri dinlemeden ve bunları uygun iş akışı hizmeti örneğine yönlendirmekten sorumludur, boşta iş akışlarının kaldırılmasını ve kalıcı olarak kaldırılmasını ve daha fazlasını denetler. Bu konuda, WorkflowServiceHost 'ın gelen iletileri nasıl işlediği açıklanmaktadır.  
  
## <a name="workflowservicehost-overview"></a>WorkflowServiceHost genel bakış  

<xref:System.ServiceModel.WorkflowServiceHost>Sınıfı, iş akışı hizmetlerini barındırmak için kullanılır. Gelen iletileri dinler ve bunları uygun hizmet örneğine yönlendirir, yeni örnekler oluşturuyor ya da gerektiğinde dayanıklı depolama alanından mevcut örnekleri yüklüyor. Aşağıdaki diyagramda, üst düzey nasıl çalıştığı aşağıda gösterilmektedir <xref:System.ServiceModel.WorkflowServiceHost> :
  
 ![Iş akışı hizmeti ana bilgisayarına genel bakış gösteren diyagram.](./media/workflow-service-host-internals/workflow-service-host-high-level-overview.gif)  
  
 Bu diyagramda, <xref:System.ServiceModel.WorkflowServiceHost> . xamlx dosyalarından iş akışı hizmeti tanımlarının yüklendiği ve yapılandırma bilgileri bir yapılandırma dosyasından yüklendiği gösterilmektedir. İzleme profilinden izleme yapılandırmasını da yükler. <xref:System.ServiceModel.WorkflowServiceHost>iş akışı örneklerine denetim işlemleri göndermenizi sağlayan bir iş akışı denetim uç noktası sunar.  Daha fazla bilgi için bkz. [Workflow Control Endpoint Sample](workflow-control-endpoint.md).  
  
 <xref:System.ServiceModel.WorkflowServiceHost>Ayrıca, gelen uygulama iletilerini dinleyen uygulama uç noktalarını da kullanıma sunar. Gelen bir ileti geldiğinde ilgili iş akışı hizmet örneğine (o anda yüklenmişse) gönderilir. Gerekirse, yeni bir iş akışı örneği oluşturulur. Ya da var olan bir örnek kalıcıda bulunursa kalıcılık deposundan yüklenir.  
  
## <a name="workflowservicehost-details"></a>WorkflowServiceHost ayrıntıları  
 Aşağıdaki diyagramda, <xref:System.ServiceModel.WorkflowServiceHost> iletilerin bir bit daha detaylı şekilde nasıl işlediği gösterilmektedir:  
  
 ![Iş akışı hizmeti ana bilgisayar ileti akışını gösteren diyagram.](./media/workflow-service-host-internals/workflow-service-host-message-flow.gif)  
  
 Bu diyagramda üç farklı uç nokta, bir uygulama uç noktası, iş akışı denetim uç noktası ve bir iş akışı barındırma uç noktası gösterilmektedir. Uygulama uç noktası, belirli bir iş akışı örneği için bağlanan iletileri alır. İş akışı denetim uç noktası denetim işlemlerini dinler. İş akışı barındırma uç noktası, <xref:System.ServiceModel.WorkflowServiceHost> hizmet dışı iş akışlarını yüklemeye ve yürütmeye neden olan iletileri dinler. Diyagramda gösterildiği gibi, tüm iletiler WCF çalışma zamanı aracılığıyla işlenir.  İş akışı hizmeti örneği azaltma özelliği kullanılarak elde edilir <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> . Bu özellik, eşzamanlı iş akışı hizmeti örneklerinin sayısını sınırlandırır. Bu kısıtlama, yeni iş akışı hizmet örnekleri veya kalıcı iş akışı örneklerinin etkinleştirilme istekleri için ek istek aşıldığında sıraya alınır. Sıraya alınan istekler, yeni bir örnek veya çalışan, kalıcı bir örnek için istek olup olmadıklarından bağımsız olarak, FıFO sırasında işlenir. İşlenmemiş özel durumların nasıl ele alınacağını ve boşta iş akışı hizmetlerinin nasıl kaldırılacağına ve kalıcı olduğunu belirleyen konak ilkesi bilgileri yüklenir. Bu konular hakkında daha fazla bilgi için bkz. [nasıl yapılır: Iş akışı Işlenmemiş özel durum davranışını WorkflowServiceHost ile](config-workflow-unhandled-exception-workflowservicehost.md) yapılandırma ve [nasıl yapılır: WorkflowServiceHost Ile boşta davranışı yapılandırma](how-to-configure-idle-behavior-with-workflowservicehost.md). İş akışı örnekleri, ana bilgisayar ilkelerine göre kalıcı hale getirilir ve gerektiğinde yeniden yüklenir. İş akışı kalıcılığı hakkında daha fazla bilgi için bkz. [nasıl yapılır: WorkflowServiceHost Ile kalıcılığı yapılandırma](how-to-configure-persistence-with-workflowservicehost.md), [uzun süre çalışan bir iş akışı hizmeti oluşturma](creating-a-long-running-workflow-service.md)ve [iş akışı kalıcılığı](../../windows-workflow-foundation/workflow-persistence.md).  
  
 Aşağıdaki çizimde, WorkflowServiceHost. Open çağrıldığında akış gösterilmektedir:  
  
 ![WorkflowServiceHost. Open çağrıldığında akışı gösteren diyagram.](./media/workflow-service-host-internals/workflow-service-host-open.gif)  
  
 İş akışı XAML 'den yüklenir ve etkinlik ağacı oluşturulur. <xref:System.ServiceModel.WorkflowServiceHost>Etkinlik ağacını açıklar ve hizmet açıklamasını oluşturur. Yapılandırma konağa uygulandı. Son olarak, ana bilgisayar gelen iletileri dinlemeye başlar.  
  
 Aşağıdaki çizimde, <xref:System.ServiceModel.WorkflowServiceHost> CanCreateInstance 'ya ayarlanmış bir alma etkinliği için bir ileti aldığında ne olduğu gösterilmektedir `true` :  
  
 ![WFS ana bilgisayarı tarafından bir ileti alındığında kullanılan karar ağacı ve CanCreateInstance doğru.](./media/workflow-service-host-internals/workflow-service-host-receive-message-cancreateinstance.gif)  
  
 İleti ulaşır ve WCF kanal yığını tarafından işlenir. Kısıtlar ve bağıntı sorguları yürütülür. İleti, mevcut bir örnek için bağlıysa ileti teslim edilir. Yeni bir örneğin oluşturulması gerekiyorsa, alma etkinliğinin CanCreateInstance özelliği denetlenir. True olarak ayarlanırsa, yeni bir örnek oluşturulur ve ileti teslim edilir.  
  
 Aşağıdaki çizimde, <xref:System.ServiceModel.WorkflowServiceHost> CanCreateInstance değeri false olarak ayarlanmış bir alma etkinliği için bir ileti aldığında ne olduğu gösterilmektedir.  
  
 ![WFS ana bilgisayarı tarafından bir ileti alındığında kullanılan karar ağacı ve CanCreateInstance yanlış.](./media/workflow-service-host-internals/workflow-service-host-receive-message.gif)  
  
 İleti ulaşır ve WCF kanal yığını tarafından işlenir. Kısıtlar ve bağıntı sorguları yürütülür. İleti, var olan bir örneğe bağlanır (CanCreateInstance yanlış olduğu için) Örneğin kalıcılık deposundan yüklenmesi durumunda, yer işareti sürdürülür ve iş akışı yürütülür.  
  
> [!WARNING]
> SQL Server, yalnızca NamedPipe protokolünü dinlemek üzere yapılandırılmışsa, iş akışı hizmeti ana bilgisayarı açılmaz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Hizmetleri](workflow-services.md)
- [İş Akışı Hizmetlerini Barındırma](hosting-workflow-services.md)
- [İş Akışı Denetim Uç Noktası](workflow-control-endpoint.md)
- [Nasıl yapılır: WorkflowServiceHost ile İş Akışı Tarafından İşlenmeyen Özel Durum Davranışını Yapılandırma](config-workflow-unhandled-exception-workflowservicehost.md)
- [Uzun Süre Çalışan Bir İş Akışı Hizmeti Oluşturma](creating-a-long-running-workflow-service.md)
- [İş Akışı Kalıcılığı](../../windows-workflow-foundation/workflow-persistence.md)
