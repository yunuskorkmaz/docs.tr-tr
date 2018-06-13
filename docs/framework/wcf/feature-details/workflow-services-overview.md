---
title: İş Akışı Hizmetleri Genel Bakış
ms.date: 03/30/2017
ms.assetid: e536dda3-e286-441e-99a7-49ddc004b646
ms.openlocfilehash: eaf5fb4b20aca0983dcbe00724ab81803834940a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33502734"
---
# <a name="workflow-services-overview"></a>İş Akışı Hizmetleri Genel Bakış
İş akışı, iş akışları kullanılarak uygulanan WCF tabanlı hizmetler hizmetleridir. İş akışı, Windows Communication Foundation (WCF) ileti gönderme ve alma için Mesajlaşma etkinlikleri kullanan iş akışları hizmetleridir. .NET framework 4.5 birkaç iş akışı içinden iletilerini gönderip izin Mesajlaşma etkinlikleri tanıtır. Etkinlikleri ve nasıl farklı ileti exchange desenleri uygulamak için kullanılabilmesi için Mesajlaşma hakkında daha fazla bilgi için bkz: [Mesajlaşma etkinlikleri](../../../../docs/framework/wcf/feature-details/messaging-activities.md).  
  
## <a name="benefits-of-using-workflow-services"></a>İş akışı hizmetleri kullanmanın yararları  
 Giderek dağıtılmış uygulamalar hale gibi tek tek Hizmetleri işinin bir kısmını boşaltmak için diğer hizmetler çağırmak için sorumlu olur. Zaman uyumsuz işlemler olarak bu çağrıları uygulama karmaşıklık koda getirir. Hata işleme karmaşıklık özel durumları işleme ve ayrıntılı izleme bilgilerini sağlama biçiminde ekler. Bazı hizmetler çoğunlukla uzun süre çalışan olur ve önemli sistem kaynakları için giriş beklerken alabilir. Bu sorunları nedeniyle dağıtılmış uygulamaların çoğunlukla çok karmaşık ve zordur yazma ve korumak. İş akışları, zaman uyumsuz iş, özellikle dış hizmetler çağrıları eşgüdümünü express doğal bir yoludur. İş akışları da uzun süre çalışan iş süreçlerini temsil eden en etkili olur. Dağıtılmış bir ortama hizmetler oluşturma için harika bir varlık iş akışının olmasını bu niteliklerini olur.  
  
## <a name="implementing-a-workflow-service"></a>Bir iş akışı hizmeti uygulama  
 Bir WCF Hizmeti uygularken, bir dizi hizmet ve gönderen ve alan verileri açıklayan sözleşme tanımlayın. Verileri veri sözleşmeleri ve ileti sözleşmeleri temsil edilir. WCF ve iş akışı Hizmetleri veri sözleşmesi ve ileti sözleşmesi tanımlarını hizmeti açıklamaları bir parçası olarak kullanın. Hizmet, hizmet işlemleri tanımlamak için meta verileri (WSDL biçiminde) gösterir. WCF'de, hizmet sözleşmeleri ve işlem sözleşmeleri hizmet ve desteklediği işlemleri tanımlayın. Ancak bir iş akışı hizmetinde Bu sözleşmeler, iş sürecini parçasıdır. Bunlar, meta verilerde sözleşme çıkarım adlı bir işlem tarafından sunulur. Bir iş akışı hizmeti kullanarak barındırıldığında <xref:System.ServiceModel.Activities.WorkflowServiceHost>, iş akışı tanımı incelenir ve bir sözleşme Mesajlaşma etkinlikleriyle iş akışında bulunan kümesini temel alınarak oluşturulur. Özellikle, aşağıdaki etkinliklerin ve özellikleri sözleşme oluşturmak için kullanılır:  
  
 <xref:System.ServiceModel.Activities.Receive> Etkinlik  
  
-   <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>  
  
-   <!--zz <xref:System.ServiceModel.Activities.Receive.OperationContractName%2A>  --> `System.ServiceModel.Activities.Receive.OperationContractName`
  
-   <xref:System.ServiceModel.Activities.Receive.Action%2A>  
  
-   <!--zz <xref:System.ServiceModel.Activities.Receive.ValueType%2A>  --> `System.ServiceModel.Activities.Receive.ValueType`
  
 <xref:System.ServiceModel.Activities.SendReply> Etkinlik  
  
-   <xref:System.ServiceModel.Activities.SendReply.Action%2A>  
  
-   <!--zz <xref:System.ServiceModel.Activities.SendReply.ValueType%2A> -->
`xref:System.ServiceModel.Activities.SendReply.ValueType`
  
 <xref:System.ServiceModel.Activities.TransactedReceiveScope> Etkinlik  
  
 Sözleşme çıkarım nihai sonucu, WCF hizmetleri ve işlem sözleşmeleri aynı veri yapılarını kullanarak hizmet açıklamasıdır. Bu bilgiler daha sonra WSDL için iş akışı hizmeti kullanıma sunmak için kullanılır.  
  
> [!NOTE]
>  [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] Varolan bir sözleşme tanımına bazı ek araç desteği olmadan kullanarak iş akışı hizmetleri yazmanıza izin vermiyor. İş akışı Hizmet sözleşmeleri daha önce ele alınan sözleşme çıkarım işlem tarafından oluşturulur. İleti sözleşmeleri ve veri sözleşmeleri tam, ancak desteklenir.  
  
## <a name="workflow-services-and-msmq-based-bindings"></a>İş akışı hizmetleri ve MSMQ tabanlı bağlamalar  
 WCF tanımlayan iki MSMQ tabanlı bağlamalar <xref:System.ServiceModel.NetMsmqBinding> ve <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.  MSMQ tabanlı bağlamalar genellikle bu tür hizmetlerin uzun süre çalışan doğası nedeniyle iş akışı Hizmetleri ile kullanılır. MSMQ tabanlı bağlamalar sahip bir `ValidityDuration` MSMQ iletileri geçerli olması için ne kadar süreyle varsayabilirsiniz belirten özellik. İş akışı hizmetleri uzun süre çalışan yapısı nedeniyle iş akışı hizmeti işleyebilmesi için önce bir MSMQ iletisi geçerlilik süresini geçmesini mümkündür. Bu nedenle bir MSMQ bağlama geçerlilik süresini uygun bir değere ayarlamak çok önemlidir. Bu değer, iş akışı ve nasıl iletileri işleyen göre seçilmelidir. Örneğin bir iş akışıyla varsa bir <xref:System.ServiceModel.Activities.Receive> etkinliği çalıştırmak için 10 dakika sürer özel bir etkinlik tarafından izlenen bir başkası tarafından izlenen <xref:System.ServiceModel.Activities.Receive> etkinliği, doğru değeri `ValidityDuration` 10 dakikadan fazla olacaktır.  
  
## <a name="hosting-a-workflow-service"></a>Bir iş akışı hizmeti barındırma  
 WCF hizmetleri gibi iş akışı hizmetleri barındırılması gerekir. WCF hizmetleri kullanım <xref:System.ServiceModel.ServiceHost> sınıfı için ana bilgisayar hizmetlerini ve iş akışı hizmetleri kullanım <xref:System.ServiceModel.Activities.WorkflowServiceHost> hizmetlerini barındırmak için. WCF hizmetleri gibi çeşitli yollarla, örneğin iş akışı hizmetleri barındırılabilir:  
  
-   Yönetilen içinde [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] uygulama.  
  
-   Internet Information Services (IIS).  
  
-   Windows İşlem Etkinleştirme Hizmeti (WAS).  
  
-   Yönetilen bir Windows hizmetinde.  
  
 Yönetilen bir barındırılan iş akışı Hizmetleri [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] uygulaması veya yönetilen bir Windows hizmet örneği oluşturma <xref:System.ServiceModel.Activities.WorkflowServiceHost> sınıfı ve örneği geçirin <xref:System.ServiceModel.Activities.WorkflowService> iş akışı tanımı içinde içeren <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> özelliği. Mesajlaşma etkinlikleri içeren bir iş akışı tanımı bir iş akışı hizmeti olarak sunulur.  
  
 Bir iş akışı hizmeti IIS ya da WAS barındırmak için sanal bir dizine iş akışı hizmet tanımını içeren .xamlx dosyası yerleştirin. Varsayılan bir uç (kullanarak <xref:System.ServiceModel.BasicHttpBinding>) olan otomatik olarak oluşturulup daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md). Ayrıca, kendi uç noktaları belirtmek için sanal dizinde bir Web.config dosyası yerleştirebilirsiniz. İş akışı tanımınızı bir derlemede ise sanal dizinde ve iş akışı derleme App_Code dizinindeki .svc dosya yerleştirebilirsiniz. .Svc dosya hizmeti ana bilgisayar üreteci ve iş akışı hizmeti uygulayan sınıfa belirtmeniz gerekir. Aşağıdaki örnek, hizmet ana bilgisayar üreteci belirtin ve iş akışı hizmeti uygulayan sınıfa belirtin gösterilmektedir.  
  
```  
<%@ServiceHost Factory=" System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory  
Service="EchoService"%>  
```
