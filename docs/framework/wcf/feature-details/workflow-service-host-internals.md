---
title: "İş Akışı Hizmeti Konağı Dahili Bileşenleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af44596f-bf6a-4149-9f04-08d8e8f45250
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6761c044f166105a2e463d0f89ed0b3813d4b97a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="workflow-service-host-internals"></a>İş Akışı Hizmeti Konağı Dahili Bileşenleri
<xref:System.ServiceModel.WorkflowServiceHost>bir ana bilgisayar için iş akışı hizmetleri sağlar. Gelen iletiler için dinleme sorumludur ve bunları uygun iş akışı hizmeti örneğine yönlendirme, onu kaldırılması ve boşta iş akışları ve daha pek çok kalıcı denetler. Bu konuda, gelen iletileri WorkflowServiceHost nasıl işlediği açıklanmıştır.  
  
## <a name="workflowservicehost-overview"></a>WorkflowServiceHost genel bakış  
 <xref:System.ServiceModel.WorkflowServiceHost> Sınıfı, iş akışı hizmetlerini barındırmak için kullanılır. Gelen iletileri dinler ve yeni örnek oluşturulamadı veya var olan örneklerini dayanıklı depolama biriminden gerektiği gibi uygun hizmet örneği yönlendirir.  Aşağıdaki diyagramda bir üst düzey nasıl gösterilmektedir <xref:System.ServiceModel.WorkflowServiceHost> çalışır.  
  
 ![WorkflowServiceHost genel bakış](../../../../docs/framework/wcf/feature-details/media/wfshhighlevel.gif "WFSHHighLevel")  
  
 Bu diyagramda gösterilmektedir <xref:System.ServiceModel.WorkflowServiceHost> iş akışı hizmeti tanımları .xamlx dosyalarından yükler ve yapılandırma bilgileri yapılandırma dosyasından yükler. Ayrıca izleme yapılandırması izleme profilinden yükler. <xref:System.ServiceModel.WorkflowServiceHost>denetimi işlemleri için iş akışı örnekleri göndermenize olanak tanıyan bir iş akışı denetim uç noktasını kullanıma sunar.  Daha fazla bilgi için bkz: [iş akışı denetim uç noktası](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md) ve [iş akışı Yönetimi uç nokta örnek](../../../../docs/framework/windows-workflow-foundation/samples/workflow-management-endpoint-sample.md).  
  
 <xref:System.ServiceModel.WorkflowServiceHost>Ayrıca gelen uygulama iletiler için dinleme uygulama uç noktalarını kullanıma sunar. Gelen ileti ulaştığında (şu anda yüklüyse) uygun iş akışı hizmeti örneğine gönderilir. Yeni bir iş akışı örneği gerekirse oluşturulur. Veya var olan bir örneğini kalıcı ise sürdürme deposundan yüklenir.  
  
## <a name="workflowservicehost-details"></a>WorkflowServiceHost ayrıntıları  
 Aşağıdaki diyagramda gösterildiği nasıl <xref:System.ServiceModel.WorkflowServiceHost> biraz daha ayrıntılı iletiler işler.  
  
 ![İş akışı hizmeti ana bilgisayarı ileti akışı](../../../../docs/framework/wcf/feature-details/media/wfshmessageflow.gif "WFSHMessageFlow")  
  
 Bu diyagramda, üç farklı uç noktalar, bir uygulama uç noktası, bir iş akışı denetim uç noktası ve bir iş akışı barındırma uç noktası gösterilmektedir. Uygulama uç noktasını belirli iş akışı örneği için bağlı iletilerini alır. İş akışı denetim uç noktası denetimi işlemleri için dinler. Uç noktayı barındıran iş akışı neden olan iletileri için dinler <xref:System.ServiceModel.WorkflowServiceHost> yüklemek ve hizmet olmayan iş akışlarını yürütmek için. Aşağıdaki çizimde gösterildiği gibi tüm iletileri WCF çalışma zamanı işlenir.  İş akışı hizmeti örneği azaltma kullanılarak gerçekleştirilir <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> özelliği. Bu özellik, eş zamanlı iş akışı hizmeti örneklerinin sayısını sınırlar. Bu kısıtlama ek aşıldığında yeni iş akışı hizmeti örnekleri için istekleri veya kalıcı iş akışı örnekleri etkinleştirmek için istekleri sıraya alınır. Kuyruğa alınan istekler, yeni bir örnek veya çalışan, kalıcı bir örnek için istekleri olup olmadıkları bağımsız olarak FIFO sırada işlenir. Ana bilgisayar ilke bilgilerini nasıl işlenmeyen özel durum ile dağıtılır ve nasıl belirleyen yüklenir boşta iş akışı hizmetleri kaldırıldı ve kalıcı. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]şu konulara bakın [nasıl yapılır: yapılandırma iş akışı işlenmeyen özel durum davranışını WorkflowServiceHost ile](../../../../docs/framework/wcf/feature-details/config-workflow-unhandled-exception-workflowservicehost.md) ve [nasıl yapılır: WorkflowServiceHost ile boşta davranışı yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-idle-behavior-with-workflowservicehost.md). İş akışı örnekleri konak ilkelerine göre kalıcı ve gerektiğinde yeniden yüklendi. İş akışını sürdürme hakkında daha fazla bilgi için bkz: [nasıl yapılır: WorkflowServiceHost ile kalıcılığı yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-persistence-with-workflowservicehost.md), [uzun süre çalışan iş akışı hizmeti oluşturma](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md), ve [iş akışı kalıcılığı ](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md).  
  
 Aşağıdaki çizimde WorkflowServiceHost.Open olarak adlandırılan gösterir.  
  
 ![WorkflowServiceHost.Open zaman çağrılır](../../../../docs/framework/wcf/feature-details/media/wfhostopen.gif "WFHostOpen")  
  
 İş akışı XAML yüklenir ve etkinlik ağaç oluşturulur. <xref:System.ServiceModel.WorkflowServiceHost>Etkinlik ağaç anlatılmaktadır ve hizmet açıklaması oluşturur. Yapılandırma ana bilgisayara uygulanır. Son olarak ana bilgisayar gelen iletiler için dinleme başlar.  
  
 Aşağıdaki resimde ne gösterilmektedir <xref:System.ServiceModel.WorkflowServiceHost> CanCreateInstance kümesine sahip bir Al etkinliğinin bağlı bir ileti aldığında mu `true`.  
  
 ![İş akışı hizmeti ana bilgisayarı bir ileti alır](../../../../docs/framework/wcf/feature-details/media/wfhreceivemessagecci.gif "WFHReceiveMessageCCI")  
  
 İleti ulaşan ve WCF kanalı yığını tarafından işlenir. Kısıtlamaları denetlenir ve bağıntı sorguları yürütülür. Var olan bir örneği için ileti bağlıysa ileti teslim edilir. Yeni bir örneğini oluşturulması gerekiyorsa alma etkinliğin CanCreateInstance özelliği denetlenir. Bu ayarı etkinse true, yeni bir örneği oluşturulur ve ileti teslim edilir.  
  
 Aşağıdaki resimde ne gösterilmektedir <xref:System.ServiceModel.WorkflowServiceHost> CanCreateInstance false olarak ayarlanmış bir Al etkinliğinin bağlı bir ileti aldığında yapar.  
  
 ![WorkflowServiceHost bir ileti alır](../../../../docs/framework/wcf/feature-details/media/wfshreceivemessage.gif "WFSHReceiveMessage")  
  
 İleti ulaşan ve WCF kanalı yığını tarafından işlenir. Kısıtlamaları denetlenir ve bağıntı sorguları yürütülür. (CanCreateInstance yanlış olduğundan) ileti var olan bir örneği için örnek sürdürme deposundan yüklenir, yer işareti sürdürüldü ve iş akışı yürütür bağlı.  
  
> [!WARNING]
>  İş akışı hizmeti ana bilgisayarı, SQL Server yalnızca NamedPipe protokolünü dinleyemedi yapılandırılmışsa açmak başarısız olur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İş Akışı Hizmetleri](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [İş Akışı Hizmetlerini Barındırma](../../../../docs/framework/wcf/feature-details/hosting-workflow-services.md)  
 [İş Akışı Denetim Uç Noktası](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md)  
 [İş Akışı Yönetimi Uç Nokta Örneği](../../../../docs/framework/windows-workflow-foundation/samples/workflow-management-endpoint-sample.md)  
 [Nasıl yapılır: WorkflowServiceHost ile İş Akışı Tarafından İşlenmeyen Özel Durum Davranışını Yapılandırma](../../../../docs/framework/wcf/feature-details/config-workflow-unhandled-exception-workflowservicehost.md)  
 [Uzun Süre Çalışan Bir İş Akışı Hizmeti Oluşturma](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md)  
 [İş Akışı Kalıcılığı](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)
