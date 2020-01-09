---
title: İş akışı hizmetlerine genel bakış
ms.date: 03/30/2017
ms.assetid: e536dda3-e286-441e-99a7-49ddc004b646
ms.openlocfilehash: cb013dd419d09af61eaff290709164427b1b655f
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347857"
---
# <a name="workflow-services-overview"></a>İş akışı hizmetlerine genel bakış

İş akışı hizmetleri, iş akışları kullanılarak uygulanan WCF tabanlı hizmetlerdir. İş akışı hizmetleri, Windows Communication Foundation (WCF) iletileri göndermek ve almak için mesajlaşma etkinliklerini kullanan iş akışlarıdır. .NET Framework 4,5, bir iş akışı içinden ileti göndermenizi ve almanızı sağlayan bir dizi mesajlaşma etkinliği sunmaktadır. İleti oluşturma etkinlikleri ve farklı ileti değişimi desenleri uygulamak için nasıl kullanılabilecekleri hakkında daha fazla bilgi için bkz. [mesajlaşma etkinlikleri](messaging-activities.md).

## <a name="benefits-of-using-workflow-services"></a>İş akışı hizmetleri kullanmanın avantajları

Uygulamalar giderek daha fazla dağıtıldığı için, her bir hizmet, çalışmanın bazılarının yükünü devretmek için diğer hizmetleri çağırmanın sorumluluğundadır. Bu çağrıların zaman uyumsuz işlemler olarak uygulanması, kodun içinde bazı karmaşıklıklar sağlar. Hata işleme özel durum işleme ve ayrıntılı izleme bilgileri sağlama biçiminde ek karmaşıklık ekler. Bazı hizmetler genellikle uzun süredir çalışıyor ve giriş beklerken değerli sistem kaynakları alabilir. Bu sorunlar nedeniyle, dağıtılmış uygulamalar genellikle çok karmaşıktır ve yazma ve bakımını zorlaştırır. İş akışları, zaman uyumsuz çalışmanın koordinasyonu için doğal bir yoldur, özellikle de harici hizmetlere çağrı yapılır. İş akışları, uzun süreli iş süreçlerini temsil eden de etkilidir. Bu, iş akışını dağıtılmış bir ortamda hizmet oluşturmaya yönelik harika bir varlık oluşturan bu kalitedir.

## <a name="implementing-a-workflow-service"></a>İş akışı hizmeti uygulama

Bir WCF hizmetini uygularken, hizmeti ve gönderdiği ve aldığı verileri tanımlayan bir dizi sözleşme tanımlarsınız. Veriler, veri sözleşmeleri ve ileti sözleşmeleri olarak gösterilir. WCF ve Workflow Hizmetleri, hizmet açıklamalarının parçası olarak veri sözleşmesi ve ileti sözleşmesi tanımlarını kullanır. Hizmet, hizmetin işlemlerini anlatmak için meta verileri (WSDL biçiminde) kullanıma sunar. WCF 'de hizmet sözleşmeleri ve işlem sözleşmeleri, hizmeti ve desteklediği işlemleri tanımlar. Ancak, bir iş akışı hizmetinde, bu sözleşmeler iş sürecinin bir parçasıdır. Bunlar, anlaşma çıkarımı adlı bir işlem tarafından meta verilerde kullanıma sunulur. Bir iş akışı hizmeti <xref:System.ServiceModel.Activities.WorkflowServiceHost>kullanılarak barındırılıyorsa, iş akışı tanımı incelenir ve iş akışında bulunan mesajlaşma etkinlikleri kümesine göre bir sözleşme oluşturulur. Özellikle, aşağıdaki etkinlikler ve Özellikler sözleşmeyi oluşturmak için kullanılır:

<xref:System.ServiceModel.Activities.Receive> etkinliği

- <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>

- <xref:System.ServiceModel.Activities.Receive.OperationName%2A>

- <xref:System.ServiceModel.Activities.Receive.Action%2A>

<xref:System.ServiceModel.Activities.SendReply> etkinliği

- <xref:System.ServiceModel.Activities.SendReply.Action%2A>

<xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinliği

Sözleşme çıkarımı nihai sonucu, WCF Hizmetleri ve işlem sözleşmeleri ile aynı veri yapılarını kullanan hizmetin bir açıklamasıdır. Bu bilgiler daha sonra iş akışı hizmeti için WSDL 'yi göstermek üzere kullanılır.

> [!NOTE]
> [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)], ek araç desteği olmadan, mevcut bir sözleşme tanımını kullanarak iş akışı hizmetleri yazmanıza izin vermez. İş akışı hizmeti sözleşmeleri, daha önce ele alınan sözleşme çıkarım işlemi tarafından oluşturulur. Ancak, ileti sözleşmeleri ve veri sözleşmeleri tam olarak desteklenir, ancak.

## <a name="workflow-services-and-msmq-based-bindings"></a>İş akışı hizmetleri ve MSMQ tabanlı bağlamalar

WCF <xref:System.ServiceModel.NetMsmqBinding> ve <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>iki MSMQ tabanlı bağlama tanımlar.  MSMQ tabanlı bağlamalar, genellikle bu tür hizmetlerin uzun süre çalışan doğası nedeniyle iş akışı hizmetleriyle birlikte kullanılır. MSMQ tabanlı bağlamalar, MSMQ iletilerinin ne kadar süreyle geçerli olduğunu belirten bir `ValidityDuration` özelliğine sahiptir. İş akışı hizmetlerinin uzun süre çalışan doğası nedeniyle, bir MSMQ iletisinin geçerlilik süresinin, iş akışı hizmeti tarafından işlem yapılmadan önce geçmesi mümkündür. Bu nedenle, MSMQ bağlamasının geçerlilik süresini uygun bir değere ayarlamak çok önemlidir. Bu değer, iş akışına göre seçilmelidir ve iletileri nasıl işler. Örneğin, bir <xref:System.ServiceModel.Activities.Receive> etkinliği olan bir iş akışınız varsa, bunu çalıştırmak için 10 dakika geçen özel bir etkinlik ve sonra başka bir <xref:System.ServiceModel.Activities.Receive> etkinliği, `ValidityDuration` için doğru değer 10 dakikadan fazla olur.

## <a name="hosting-a-workflow-service"></a>Bir iş akışı hizmeti barındırma

WCF Hizmetleri gibi iş akışı hizmetleri de barındırılmalıdır. WCF Hizmetleri, hizmetleri ve iş akışı hizmetlerini barındırmak için <xref:System.ServiceModel.ServiceHost> sınıfını kullanır ve Hizmetleri barındırmak için <xref:System.ServiceModel.Activities.WorkflowServiceHost> kullanır. WCF Hizmetleri gibi, iş akışı hizmetleri çeşitli yollarla barındırılabilir, örneğin:

- Bir yönetilen .NET Framework uygulamasında.

- Internet Information Services (IIS) içinde.

- Windows Işlem etkinleştirme hizmeti 'nde (WAS).

- Yönetilen bir Windows hizmetinde.

Yönetilen bir .NET Framework uygulamasında veya yönetilen bir Windows hizmetinde barındırılan iş akışı hizmetleri, <xref:System.ServiceModel.Activities.WorkflowServiceHost> sınıfının bir örneğini oluşturur ve onu <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> özelliği içinde iş akışı tanımını içeren bir <xref:System.ServiceModel.Activities.WorkflowService> örneğine iletir. Mesajlaşma etkinliklerini içeren bir iş akışı tanımı, bir iş akışı hizmeti olarak sunulur.

Bir iş akışı hizmetini IIS 'de veya WAS 'de barındırmak için, iş akışı hizmeti tanımını içeren. xamlx dosyasını bir sanal dizine yerleştirin. Varsayılan uç nokta (<xref:System.ServiceModel.BasicHttpBinding>kullanarak), daha fazla bilgi Için otomatik olarak oluşturulur, bkz. [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md). Ayrıca, kendi uç noktalarınızı belirtmek için sanal dizine bir Web. config dosyası yerleştirebilirsiniz. İş akışı tanımınızda bir derlemede yer alıyorsa, bir. svc dosyasını sanal dizine ve App_Code dizinindeki iş akışı derlemesine yerleştirebilirsiniz. . Svc dosyası, hizmet ana bilgisayarı fabrikası ve iş akışı hizmetini uygulayan sınıfı belirtmelidir. Aşağıdaki örnek, hizmet ana bilgisayar fabrikasının nasıl ekleneceğini ve iş akışı hizmetini uygulayan sınıfın nasıl kullanılacağını gösterir.

```
<%@ServiceHost Factory=" System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory
Service="EchoService"%>
```
