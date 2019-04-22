---
title: İş Akışı Hizmeti Ana Bilgisayar Dahili Bileşenleri
ms.date: 03/30/2017
ms.assetid: af44596f-bf6a-4149-9f04-08d8e8f45250
ms.openlocfilehash: 0596e15e27460a08f859ec3398afbeae752c86fc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58826034"
---
# <a name="workflow-service-host-internals"></a>İş Akışı Hizmeti Ana Bilgisayar Dahili Bileşenleri
<xref:System.ServiceModel.WorkflowServiceHost> bir konak için iş akışı hizmetleri sağlar. Gelen iletileri dinlemek üzere sorumludur ve bunları uygun iş akışı hizmet örneği için yönlendirme, kaldırma ve boşta iş akışları ve daha pek çok kalıcı denetlediğini. Bu konuda, WorkflowServiceHost gelen iletilerin nasıl işlediği açıklanmıştır.  
  
## <a name="workflowservicehost-overview"></a>WorkflowServiceHost genel bakış  

<xref:System.ServiceModel.WorkflowServiceHost> Sınıfı iş akışı hizmetlerini barındırmak için kullanılır. Bu, gelen iletileri dinler ve bunları yeni kopyalarını oluşturmak veya mevcut örneklerdeki gerektiği gibi kalıcı depolama alanından yüklenirken uygun hizmet örneği yönlendirir. Aşağıdaki diyagramda bir üst düzey yönergeler gösterilir <xref:System.ServiceModel.WorkflowServiceHost> çalışır: 
  
 ![İş akışı hizmeti konağı genel bakışını gösteren diyagram.](./media/workflow-service-host-internals/workflow-service-host-high-level-overview.gif)  
  
 Bu diyagramda gösterilmektedir <xref:System.ServiceModel.WorkflowServiceHost> iş akışı hizmet tanımları .xamlx dosyalardan yükler ve bir yapılandırma dosyasından yapılandırma bilgilerini yükler. Ayrıca izleme yapılandırma izleme profilini yükler. <xref:System.ServiceModel.WorkflowServiceHost> denetimi işlemleri için iş akışı örnekleri göndermenize olanak tanıyan bir iş akışı denetim uç noktasını kullanıma sunar.  Daha fazla bilgi için [iş akışı denetim uç noktası örnek](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md).  
  
 <xref:System.ServiceModel.WorkflowServiceHost> Ayrıca, gelen uygulama iletiler için dinleme yapan bir uygulama uç noktalarını kullanıma sunar. Gelen ileti ulaştığında (şu anda yüklenmişse) uygun iş akışı hizmeti örneğine gönderilir. Yeni bir iş akışı örneği gerektiğinde oluşturulur. Veya, varsa var olan bir örneğini kalıcı sürdürme deposundan yüklenir.  
  
## <a name="workflowservicehost-details"></a>WorkflowServiceHost ayrıntıları  
 Aşağıdaki diyagramda gösterildiği nasıl <xref:System.ServiceModel.WorkflowServiceHost> biraz daha ayrıntılı iletileri işler:  
  
 ![İş akışı hizmeti konağı ileti akışı gösteren diyagram.](./media/workflow-service-host-internals/workflow-service-host-message-flow.gif)  
  
 Bu diyagram, üç farklı uç noktalar, bir uygulama uç noktası, bir iş akışı denetim uç noktası ve bir iş akışı barındırma uç noktası gösterir. Uygulama uç noktası, belirli bir iş akışı örneği için bağlı olan iletileri alır. İş akışı denetim uç noktası denetimi işlemleri için dinler. Uç noktayı barındıran iş akışı için neden olan iletileri dinler <xref:System.ServiceModel.WorkflowServiceHost> yüklemek ve hizmet olmayan iş akışlarını yürütmek için. Diyagramda gösterildiği gibi tüm iletileri WCF çalışma zamanı işlenir.  İş akışı hizmeti örneği azaltma kullanılarak gerçekleştirilir <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> özelliği. Bu özellik, eş zamanlı iş akışı hizmeti örnek sayısını sınırlar. Bu kısıtlama diğer aşıldığında, yeni iş akışı hizmet örneklerine yönelik istekler ya kalıcı iş akışı örnekleri etkinleştirmek için istekler kuyruğa alınır. Kuyruğa alınan istekler, yeni bir örneği veya bir çalışan, kalıcı örnek istekleri olup olmadıkları bakılmaksızın FIFO sırayla işlenir. Ana bilgisayar ilke bilgilerini nasıl işlenmeyen özel durumları ile dağıtılır ve nasıl belirleyen yüklendiği boş iş akışı hizmetleri kaldırıldı ve kalıcı. Bu konular hakkında daha fazla bilgi için bkz: [nasıl yapılır: İş akışı yapılandırma işlenmeyen özel durum davranışını WorkflowServiceHost ile](../../../../docs/framework/wcf/feature-details/config-workflow-unhandled-exception-workflowservicehost.md) ve [nasıl yapılır: WorkflowServiceHost ile boşta davranışı yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-idle-behavior-with-workflowservicehost.md). İş akışı örnekleri, konak ilkelerine göre kalıcı ve gerektiğinde yeniden yükleniyor. İş akışı kalıcılığı bakın hakkında daha fazla bilgi için: [Nasıl yapılır: WorkflowServiceHost ile kalıcılığı yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-persistence-with-workflowservicehost.md), [uzun süre çalışan iş akışı hizmeti oluşturma](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md), ve [iş akışı kalıcılığı](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md).  
  
 WorkflowServiceHost.Open çağrıldığında aşağıdaki çizimde akışı gösterilmektedir:  
  
 ![WorkflowServiceHost.Open çağrıldığında akışını gösteren diyagram.](./media/workflow-service-host-internals/workflow-service-host-open.gif)  
  
 İş akışı XAML ' yüklenir ve stromu oluşturulur. <xref:System.ServiceModel.WorkflowServiceHost> Etkinlik ağacı gezer ve hizmet açıklaması oluşturur. Yapılandırma, konağa uygulanır. Son olarak, gelen iletileri dinlemek konak başlar.  
  
 Aşağıdaki çizim ne gösterir <xref:System.ServiceModel.WorkflowServiceHost> CanCreateInstance kümesine sahip bir Al etkinliğinin bağlı bir ileti aldığında mu `true`:  
  
 ![Bir iletiyi alır ve CanCreateInstance true olduğunda WFS ana bilgisayar tarafından kullanılan ağaç karar.](./media/workflow-service-host-internals/workflow-service-host-receive-message-cancreateinstance.gif)  
  
 İleti ulaşır ve WCF kanalı yığını tarafından işlenir. Kısıtlamalar denetlenir ve bağıntı sorgu yürütülür. İleti için var olan bir örneğini bağlıysa ileti teslim edilir. Yeni bir örneğini oluşturulması gerekiyorsa alma etkinliğin CanCreateInstance özelliği denetlenir. Bu ayarlanırsa true, yeni bir örneği oluşturulur ve ileti teslim edilir.  
  
 Aşağıdaki çizim ne gösterir <xref:System.ServiceModel.WorkflowServiceHost> CanCreateInstance false olarak ayarlanmış olan bir Al etkinliğinin bağlı bir ileti aldığında yapar.  
  
 ![Bir iletiyi alır ve CanCreateInstance false olduğunda WFS ana bilgisayar tarafından kullanılan ağaç karar.](./media/workflow-service-host-internals/workflow-service-host-receive-message.gif)  
  
 İleti ulaşır ve WCF kanalı yığını tarafından işlenir. Kısıtlamalar denetlenir ve bağıntı sorgu yürütülür. İleti (CanCreateInstance false olduğundan) var olan bir örneği için sürdürme deposundan örneği yüklenir, yer işareti sürdürüldü ve iş akışı yürüten bağlıdır.  
  
> [!WARNING]
> İş akışı hizmeti konağı, SQL Server yalnızca NamedPipe protokolünde dinleyecek şekilde yapılandırıldıysa açmak başarısız olur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Hizmetleri](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [İş Akışı Hizmetlerini Barındırma](../../../../docs/framework/wcf/feature-details/hosting-workflow-services.md)
- [İş Akışı Denetim Uç Noktası](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md)
- [Nasıl yapılır: İş akışı yapılandırma işlenmeyen özel durum davranışını WorkflowServiceHost ile](../../../../docs/framework/wcf/feature-details/config-workflow-unhandled-exception-workflowservicehost.md)
- [Uzun Süre Çalışan Bir İş Akışı Hizmeti Oluşturma](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md)
- [İş Akışı Kalıcılığı](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)
