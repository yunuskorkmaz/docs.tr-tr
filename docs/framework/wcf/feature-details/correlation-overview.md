---
title: Bağıntı Genel Bakış
ms.date: 03/30/2017
ms.assetid: edcc0315-5d26-44d6-a36d-ea554c418e9f
ms.openlocfilehash: 65f87195fde0c3dbda610804260f0ebfbf599073
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84586981"
---
# <a name="correlation-overview"></a>Bağıntı Genel Bakış
Bağıntı, iş akışı hizmeti iletilerini birbirleriyle veya bir başlangıç isteği yanıtı gibi uygulama örneği durumuyla veya bir sıra işleme iş akışının kalıcı durumuna bir sıra KIMLIĞIYLE ilişkilendirmek için bir mekanizmadır. Bu konuda bağıntılı bir genel bakış sunulmaktadır. Bu bölümdeki diğer konular her bir bağıntı türü için ek bilgi sağlar.  
  
## <a name="types-of-correlation"></a>Bağıntı türleri  
 Bağıntı, protokol tabanlı veya içerik tabanlı olabilir. Protokol tabanlı bağıntılar iletiler arasında eşleme sağlamak için ileti teslim altyapısı tarafından belirtilen verileri kullanır. Protokol tabanlı bağıntı kullanılarak bağıntılı iletiler <xref:System.ServiceModel.Channels.RequestContext> , bir veya Aktarım Protokolü tarafından sunulan bir belirteç tarafından bellekteki bir nesne kullanılarak birbirleriyle ilişkilidir. İçerik tabanlı bağıntılar, uygulama tarafından belirtilen verileri kullanarak iletileri birbirleriyle ilişkilendirir. İçerik tabanlı bağıntı kullanılarak bağıntılı iletiler, iletideki müşteri numarası gibi bazı uygulama tanımlı verilerle birbirleriyle ilişkilidir.  
  
 Bağıntıya katılan etkinlikler <xref:System.ServiceModel.Activities.CorrelationHandle> , mesajlaşma etkinliklerini birbirine bağlamak için bir kullanır. Örneğin, bir <xref:System.ServiceModel.Activities.Send> hizmeti çağırmak için kullanılan ve <xref:System.ServiceModel.Activities.Receive> hizmeti, hizmetten geri çağrı almak için kullanılan bir ile, aynı şekilde paylaşır <xref:System.ServiceModel.Activities.CorrelationHandle> . Bu temel model, bağıntı içerik tabanlı veya protokol tabanlı olup olmadığı için kullanılır. Bağıntı tanıtıcısı her etkinlik üzerinde açık olarak ayarlanabilir veya etkinlikler bir etkinliğin içinde yer alabilir <xref:System.ServiceModel.Activities.CorrelationScope> . İçinde yer alan etkinliklerin <xref:System.ServiceModel.Activities.CorrelationScope> bağıntıları tarafından yönetilen <xref:System.ServiceModel.Activities.CorrelationScope> ve <xref:System.ServiceModel.Activities.CorrelationHandle> açıkça ayarlanmış olması gerekmez. <xref:System.ServiceModel.Activities.CorrelationScope>Kapsam, <xref:System.ServiceModel.Activities.CorrelationHandle> İstek-Yanıt Bağıntısı ve bir ek bağıntı türü için yönetim sağlar. Kullanılarak barındırılan iş akışı Hizmetleri <xref:System.ServiceModel.Activities.WorkflowServiceHost> , etkinlikle aynı varsayılan bağıntı yönetimine sahiptir <xref:System.ServiceModel.Activities.CorrelationScope> . Bu varsayılan bağıntı yönetimi genellikle pek çok senaryoda, bir <xref:System.ServiceModel.Activities.CorrelationScope> veya bir iş akışı hizmetindeki mesajlaşma etkinliklerinin, paralel veya örtüşmediği veya iki etkinliğin ardından iki etkinlik <xref:System.ServiceModel.Activities.CorrelationHandle> <xref:System.ServiceModel.Activities.Receive> takip ettiği sürece kendi kümesini gerektirmediği anlamına gelir <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.Receive> . Bu bölümdeki her bir bağıntı türünü kapsayan konularda Varsayılan bağıntı hakkında daha fazla bilgi verilmiştir. Mesajlaşma etkinlikleri hakkında daha fazla bilgi için bkz. ileti [etkinlikleri](messaging-activities.md) ve [nasıl yapılır: mesajlaşma etkinlikleriyle Iş akışı hizmeti oluşturma](how-to-create-a-workflow-service-with-messaging-activities.md).  
  
## <a name="protocol-based-correlation"></a>Protokol tabanlı bağıntı

Protokol tabanlı bağıntı, iletileri birbirleriyle ve uygun örnekle ilişkilendirmek için taşıma mekanizmasını kullanır. Sistem tarafından sunulan bazı protokol bağıntıları, istek-yanıt bağıntısını ve bağlam tabanlı bağıntıyı içerir. İstek-Yanıt Bağıntısı, tek bir adet ileti etkinliklerini ilişkilendirmek için, veya ile eşleştirilmiş gibi iki yönlü bir işlem oluşturmak için kullanılır <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> . Visual Studio İş Akışı Tasarımcısı Ayrıca bu düzenin hızlı bir şekilde uygulanması için bir dizi etkinlik şablonu sağlar. Bağlam tabanlı bir bağıntı, [.net bağlam değişimi protokol belirtiminde](https://docs.microsoft.com/openspecs/windows_protocols/mc-netcex/a7f26280-491f-465b-9914-c5eb5322dbb4)açıklanan bağlam değişim mekanizmasına dayalıdır. Bağlam tabanlı bağıntı kullanmak için, veya gibi bir bağlam tabanlı bağlama ve <xref:System.ServiceModel.BasicHttpContextBinding> <xref:System.ServiceModel.WSHttpContextBinding> <xref:System.ServiceModel.NetTcpContextBinding> uç noktada kullanılması gerekir.  
  
Protokol bağıntısı hakkında daha fazla bilgi için bkz. [dayanıklı çift yönlü](durable-duplex-correlation.md) ve [istek-yanıt](request-reply-correlation.md). Visual Studio İş Akışı Tasarımcısı etkinlik şablonlarını kullanma hakkında daha fazla bilgi için bkz. [mesajlaşma etkinlikleri](messaging-activities.md). Örnek kod için bkz. [NetContextExchangeCorrelation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee662963%28v%3dvs.100%29) örneği.  
  
## <a name="content-based-correlation"></a>İçerik Temelli Bağıntı

İçerik tabanlı bağıntı, iletideki bazı bilgileri belirli bir örnekle ilişkilendirmek için kullanır. Protokol tabanlı bağıntı aksine, içerik tabanlı bağıntı, uygulama yazarının bu verilerin ilgili her iletide nerede bulunanların açık durumda olmasını gerektirir. İçerik tabanlı bağıntı kullanan etkinlikler, kullanarak bu ileti verilerini belirtir <xref:System.ServiceModel.MessageQuerySet> . İçerik tabanlı bağıntı, gibi bağlam bağlamalarından birini kullanmayan hizmetlerle iletişim kurarken yararlı olur <xref:System.ServiceModel.BasicHttpContextBinding> .
  
## <a name="see-also"></a>Ayrıca bkz.

- [NetContextExchangeCorrelation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee662963%28v%3dvs.100%29)
