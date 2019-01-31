---
title: İş akışı hizmetlerine genel bakış - WCF
ms.date: 03/30/2017
ms.assetid: e536dda3-e286-441e-99a7-49ddc004b646
ms.openlocfilehash: 1461ef545c4b31f84e62d82453320179d9aa74e0
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55278674"
---
# <a name="workflow-services-overview"></a>İş akışı hizmetlerine genel bakış

İş akışı, iş akışları kullanılarak uygulanır ve WCF tabanlı Hizmetleri hizmetleridir. İş akışı, Windows Communication Foundation (WCF) ileti göndermek ve almak için ileti etkinlikleri kullanan iş akışları hizmetleridir. .NET framework 4.5 birkaç iş akışı içinden gelen iletiler gönderip izin Mesajlaşma etkinlikleri sunar. Etkinlikleri ve nasıl farklı ileti exchange desenleri uygulamak için kullanılabilmesi için Mesajlaşma hakkında daha fazla bilgi için bkz. [Mesajlaşma etkinlikleri](messaging-activities.md).

## <a name="benefits-of-using-workflow-services"></a>İş akışı hizmetleri kullanmanın avantajları

Gittikçe artan dağıtılmış uygulamalar duruma gibi tek başına hizmetlerinden işinin bir kısmını boşaltmak için diğer hizmetleri çağırmak için sorumlu olur. Bu çağrılar zaman uyumsuz işlemler olarak uygulama koduna bazı daha karmaşık hâle getirir. Hata işleme süreci daha karmaşık özel durumları işleme ve ayrıntılı izleme bilgilerini sağlayarak biçiminde ekler. Bazı hizmetler, genellikle uzun süre çalışan olur ve önemli sistem kaynakları için giriş beklerken alabilir. Bu sorunları nedeniyle dağıtılmış uygulamaların çoğunlukla çok karmaşık ve yazmanız ve korumanız zor olur. İş akışları, zaman uyumsuz işler, özellikle çağrıları dış hizmetlerle eşgüdümüyle ifade etmek için doğal bir yoludur. İş akışları da uzun süre çalışan iş süreçleri temsil eden en etkili olur. Bu iş akışı hizmetleri dağıtılmış bir ortamda oluşturmak için harika bir varlık olun. Bu kalitelerini olur.

## <a name="implementing-a-workflow-service"></a>Bir iş akışı hizmeti uygulama

Bir WCF Hizmeti uygularken, bir dizi hizmet ve veri gönderen ve alan açıklayan sözleşme tanımlayın. Verileri veri sözleşmeleri ve ileti sözleşmeleri temsil edilir. WCF hem iş akışı Hizmetleri, veri sözleşme ve ileti anlaşması tanımlarını hizmet açıklamaları bir parçası olarak kullanın. Hizmet, hizmet işlemleri tanımlamak için meta verileri (WSDL biçiminde) kullanıma sunar. WCF'de, hizmet sözleşmeleri ve işlem sözleşmeleri hizmeti ve desteklediği işlemleri tanımlayın. Ancak bir iş akışı hizmetinde, bu sözleşme iş süreci parçasıdır. Bunlar, meta verilerde sözleşme çıkarımı olarak adlandırılan bir işlem tarafından sunulur. Bir iş akışı hizmeti kullanarak barındırıldığında <xref:System.ServiceModel.Activities.WorkflowServiceHost>, iş akışı tanımı incelenir ve sözleşme Mesajlaşma etkinlikleriyle iş akışında bulunan kümesi temel alınarak oluşturulur. Özellikle, aşağıdaki etkinlikleri ve özellikleri sözleşme oluşturmak için kullanılır:

<xref:System.ServiceModel.Activities.Receive> Etkinlik

- <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>

- <xref:System.ServiceModel.Activities.Receive.OperationName%2A>

- <xref:System.ServiceModel.Activities.Receive.Action%2A>

<xref:System.ServiceModel.Activities.SendReply> Etkinlik

- <xref:System.ServiceModel.Activities.SendReply.Action%2A>

<xref:System.ServiceModel.Activities.TransactedReceiveScope> Etkinlik

Sözleşme çıkarımı nihai sonucu, WCF hizmetleri ve işlem sözleşmeleri aynı veri yapılarını kullanarak hizmeti açıklamasıdır. Bu bilgiler, sonra iş akışı hizmeti için WSDL göstermek için kullanılır.

> [!NOTE]
> [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] Bazı ek araç desteği olmadan var olan bir sözleşme tanımı kullanarak iş akışı hizmetleri yazmanıza izin vermez. İş akışı Hizmet sözleşmeleri, yukarıda bahsedilen sözleşme çıkarımı işlem tarafından oluşturulur. İleti sözleşmeleri ve veri sözleşmeleri tam, ancak desteklenir.

## <a name="workflow-services-and-msmq-based-bindings"></a>İş akışı hizmetleri ve MSMQ tabanlı bağlamalar

WCF tanımlayan iki MSMQ tabanlı bağlamalar <xref:System.ServiceModel.NetMsmqBinding> ve <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.  MSMQ tabanlı bağlamalar, genellikle bu hizmetler uzun süre çalışan yapısı nedeniyle iş akışı Hizmetleri ile kullanılır. MSMQ tabanlı bağlamalar sahip bir `ValidityDuration` MSMQ iletileri geçerli olması için ne kadar süreyle varsayabilirsiniz belirten özelliği. Uzun süre çalışan iş akışı hizmetleri yapısı nedeniyle iş akışı hizmeti onu işlemeden önce bir MSMQ iletisinin geçerlilik süresini geçmesini mümkündür. Bu nedenle uygun bir değere bir MSMQ bağlama geçerlilik süresini ayarlamak çok önemlidir. Bu değer, iş akışı ve iletileri işlediğinden nasıl göre seçilmelidir. Örneğin bir iş akışıyla varsa bir <xref:System.ServiceModel.Activities.Receive> etkinliği çalıştırmak için 10 dakika sürer özel bir etkinlik tarafından izlenen bir başkası tarafından izlenen <xref:System.ServiceModel.Activities.Receive> etkinliği, doğru değeri `ValidityDuration` 10 dakikadan uzun olacaktır.

## <a name="hosting-a-workflow-service"></a>Bir iş akışı hizmeti barındırma

WCF hizmetlerinde olduğu gibi iş akışı hizmetleri barındırılması gerekir. WCF hizmetleri kullanma <xref:System.ServiceModel.ServiceHost> sınıfı hizmetlerini barındırmak ve iş akışı hizmetleri kullanım <xref:System.ServiceModel.Activities.WorkflowServiceHost> hizmetlerini barındırmak için. WCF hizmetlerinde olduğu gibi çeşitli şekillerde örneğin iş akışı hizmetleri barındırılabilir:

- Yönetilen bir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] uygulama.

- Internet Information Services (IIS).

- Windows İşlem Etkinleştirme Hizmeti (WAS).

- Yönetilen bir Windows hizmetinde.

Yönetilen bir barındırılan iş akışı Hizmetleri [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] uygulama veya yönetilen bir Windows hizmet örneği oluşturma <xref:System.ServiceModel.Activities.WorkflowServiceHost> sınıfı ve bir örneğini geçirin <xref:System.ServiceModel.Activities.WorkflowService> içinde iş akışı tanımını içeren <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> özelliği. Mesajlaşma etkinlikleri içeren bir iş akışı tanımı, bir iş akışı hizmeti kullanıma sunulur.

Bir iş akışı hizmetinde IIS ya da WAS barındırmak için sanal bir dizine iş akışı hizmet tanımını içeren .xamlx dosyası yerleştirin. Varsayılan uç nokta (kullanarak <xref:System.ServiceModel.BasicHttpBinding>) olan otomatik olarak oluşturulan daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md). Bir Web.config dosyası, ayrıca kendi uç noktalarınız belirtmek için sanal dizin yerleştirebilirsiniz. İş akışı tanımınızı bir derlemede ise sanal dizin ve iş akışı derleme App_Code dizinindeki .svc dosya yerleştirebilirsiniz. .Svc dosyası, hizmet barındırma ortamı fabrikası ve iş akışı hizmeti uygulayan sınıf belirtmeniz gerekir. Aşağıdaki örnek, hizmet barındırma ortamı fabrikası belirtin ve iş akışı hizmeti uygulayan bir sınıf belirtmek gösterilmektedir.

```
<%@ServiceHost Factory=" System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory
Service="EchoService"%>
```