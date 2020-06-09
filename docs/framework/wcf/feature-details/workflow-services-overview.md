---
title: İş akışı hizmetlerine genel bakış
ms.date: 03/30/2017
ms.assetid: e536dda3-e286-441e-99a7-49ddc004b646
ms.openlocfilehash: f752eca621f9d30f38d85d7e71228fdfe1343c32
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594874"
---
# <a name="workflow-services-overview"></a>İş akışı hizmetlerine genel bakış

İş akışı hizmetleri, iş akışları kullanılarak uygulanan WCF tabanlı hizmetlerdir. İş akışı hizmetleri, Windows Communication Foundation (WCF) iletileri göndermek ve almak için mesajlaşma etkinliklerini kullanan iş akışlarıdır. .NET Framework 4,5, bir iş akışı içinden ileti göndermenizi ve almanızı sağlayan bir dizi mesajlaşma etkinliği sunmaktadır. İleti oluşturma etkinlikleri ve farklı ileti değişimi desenleri uygulamak için nasıl kullanılabilecekleri hakkında daha fazla bilgi için bkz. [mesajlaşma etkinlikleri](messaging-activities.md).

## <a name="benefits-of-using-workflow-services"></a>İş akışı hizmetleri kullanmanın avantajları

Uygulamalar giderek daha fazla dağıtıldığı için, her bir hizmet, çalışmanın bazılarının yükünü devretmek için diğer hizmetleri çağırmanın sorumluluğundadır. Bu çağrıların zaman uyumsuz işlemler olarak uygulanması, kodun içinde bazı karmaşıklıklar sağlar. Hata işleme özel durum işleme ve ayrıntılı izleme bilgileri sağlama biçiminde ek karmaşıklık ekler. Bazı hizmetler genellikle uzun süredir çalışıyor ve giriş beklerken değerli sistem kaynakları alabilir. Bu sorunlar nedeniyle, dağıtılmış uygulamalar genellikle çok karmaşıktır ve yazma ve bakımını zorlaştırır. İş akışları, zaman uyumsuz çalışmanın koordinasyonu için doğal bir yoldur, özellikle de harici hizmetlere çağrı yapılır. İş akışları, uzun süreli iş süreçlerini temsil eden de etkilidir. Bu, iş akışını dağıtılmış bir ortamda hizmet oluşturmaya yönelik harika bir varlık oluşturan bu kalitedir.

## <a name="implementing-a-workflow-service"></a>İş akışı hizmeti uygulama

Bir WCF hizmetini uygularken, hizmeti ve gönderdiği ve aldığı verileri tanımlayan bir dizi sözleşme tanımlarsınız. Veriler, veri sözleşmeleri ve ileti sözleşmeleri olarak gösterilir. WCF ve Workflow Hizmetleri, hizmet açıklamalarının parçası olarak veri sözleşmesi ve ileti sözleşmesi tanımlarını kullanır. Hizmet, hizmetin işlemlerini anlatmak için meta verileri (WSDL biçiminde) kullanıma sunar. WCF 'de hizmet sözleşmeleri ve işlem sözleşmeleri, hizmeti ve desteklediği işlemleri tanımlar. Ancak, bir iş akışı hizmetinde, bu sözleşmeler iş sürecinin bir parçasıdır. Bunlar, anlaşma çıkarımı adlı bir işlem tarafından meta verilerde kullanıma sunulur. Bir iş akışı hizmeti kullanılarak barındırıldığı zaman, iş akışı <xref:System.ServiceModel.Activities.WorkflowServiceHost> tanımı incelenir ve iş akışında bulunan mesajlaşma etkinlikleri kümesine göre bir sözleşme oluşturulur. Özellikle, aşağıdaki etkinlikler ve Özellikler sözleşmeyi oluşturmak için kullanılır:

<xref:System.ServiceModel.Activities.Receive>Etkinlik

- <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>

- <xref:System.ServiceModel.Activities.Receive.OperationName%2A>

- <xref:System.ServiceModel.Activities.Receive.Action%2A>

<xref:System.ServiceModel.Activities.SendReply>Etkinlik

- <xref:System.ServiceModel.Activities.SendReply.Action%2A>

<xref:System.ServiceModel.Activities.TransactedReceiveScope>Etkinlik

Sözleşme çıkarımı nihai sonucu, WCF Hizmetleri ve işlem sözleşmeleri ile aynı veri yapılarını kullanan hizmetin bir açıklamasıdır. Bu bilgiler daha sonra iş akışı hizmeti için WSDL 'yi göstermek üzere kullanılır.

> [!NOTE]
> [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)], ek araç desteği olmadan, mevcut bir sözleşme tanımını kullanarak iş akışı hizmetleri yazmanıza izin vermez. İş akışı hizmeti sözleşmeleri, daha önce ele alınan sözleşme çıkarım işlemi tarafından oluşturulur. Ancak, ileti sözleşmeleri ve veri sözleşmeleri tam olarak desteklenir, ancak.

## <a name="workflow-services-and-msmq-based-bindings"></a>İş akışı hizmetleri ve MSMQ tabanlı bağlamalar

WCF, iki MSMQ tabanlı bağlama <xref:System.ServiceModel.NetMsmqBinding> ve tanımlar <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> .  MSMQ tabanlı bağlamalar, genellikle bu tür hizmetlerin uzun süre çalışan doğası nedeniyle iş akışı hizmetleriyle birlikte kullanılır. MSMQ tabanlı bağlamalar, `ValidityDuration` MSMQ iletilerinin ne kadar süreyle geçerli olduğunu belirten bir özelliğe sahiptir. İş akışı hizmetlerinin uzun süre çalışan doğası nedeniyle, bir MSMQ iletisinin geçerlilik süresinin, iş akışı hizmeti tarafından işlem yapılmadan önce geçmesi mümkündür. Bu nedenle, MSMQ bağlamasının geçerlilik süresini uygun bir değere ayarlamak çok önemlidir. Bu değer, iş akışına göre seçilmelidir ve iletileri nasıl işler. Örneğin, bir etkinliği olan bir iş akışınız varsa ve ardından <xref:System.ServiceModel.Activities.Receive> başka bir etkinlik tarafından çalıştırılması için 10 dakika geçen özel bir etkinlik varsa <xref:System.ServiceModel.Activities.Receive> , için doğru değer `ValidityDuration` 10 dakikadan fazla olur.

## <a name="hosting-a-workflow-service"></a>Bir iş akışı hizmeti barındırma

WCF Hizmetleri gibi iş akışı hizmetleri de barındırılmalıdır. WCF Hizmetleri, Hizmetleri <xref:System.ServiceModel.ServiceHost> ve iş akışı hizmetleri 'ni barındırmak için kullanmak üzere sınıfını kullanır <xref:System.ServiceModel.Activities.WorkflowServiceHost> . WCF Hizmetleri gibi, iş akışı hizmetleri çeşitli yollarla barındırılabilir, örneğin:

- Bir yönetilen .NET Framework uygulamasında.

- Internet Information Services (IIS) içinde.

- Windows Işlem etkinleştirme hizmeti 'nde (WAS).

- Yönetilen bir Windows hizmetinde.

Yönetilen bir .NET Framework uygulamasında veya yönetilen bir Windows hizmetinde barındırılan iş akışı hizmetleri, sınıfının bir örneğini oluşturur <xref:System.ServiceModel.Activities.WorkflowServiceHost> ve bunu <xref:System.ServiceModel.Activities.WorkflowService> özelliği içinde iş akışı tanımını içeren bir örneğini iletir <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> . Mesajlaşma etkinliklerini içeren bir iş akışı tanımı, bir iş akışı hizmeti olarak sunulur.

Bir iş akışı hizmetini IIS 'de veya WAS 'de barındırmak için, iş akışı hizmeti tanımını içeren. xamlx dosyasını bir sanal dizine yerleştirin. Daha fazla bilgi Için varsayılan uç nokta (using <xref:System.ServiceModel.BasicHttpBinding> ) otomatik olarak oluşturulur, bkz. [Basitleştirilmiş yapılandırma](../simplified-configuration.md). Ayrıca, kendi uç noktalarınızı belirtmek için sanal dizine bir Web. config dosyası yerleştirebilirsiniz. İş akışı tanımınızda bir derlemede yer alıyorsa, bir. svc dosyasını sanal dizine ve App_Code dizinindeki iş akışı derlemesine yerleştirebilirsiniz. . Svc dosyası, hizmet ana bilgisayarı fabrikası ve iş akışı hizmetini uygulayan sınıfı belirtmelidir. Aşağıdaki örnek, hizmet ana bilgisayar fabrikasının nasıl ekleneceğini ve iş akışı hizmetini uygulayan sınıfın nasıl kullanılacağını gösterir.

```
<%@ServiceHost Factory=" System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory
Service="EchoService"%>
```
