---
title: Özel Bağlamalar
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, endpoints
- Windows Communication Foundation, configuration
ms.assetid: 58532b6d-4eea-4a4f-854f-a1c8c842564d
ms.openlocfilehash: 314409f5ac4ecb4b18f3b8d3f2aeb08a507ec9e9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59207272"
---
# <a name="custom-bindings"></a>Özel Bağlamalar
Kullanabileceğiniz <xref:System.ServiceModel.Channels.CustomBinding> sınıfı, sistem tarafından sağlanan bağlamalar birini hizmetinizin gereksinimlerini karşılamıyor. Tüm bağlamalar bağlama öğelerinin sıralı bir kümesinden oluşturulur. Özel bağlamalar, sistem tarafından sağlanan bağlama öğeleri kümesinden oluşturulabilir veya kullanıcı tanımlı özel bağlama öğelerini içerebilir. Özel bağlama öğeleri, örneğin, yeni taşıma veya bir hizmet uç noktasında kodlayıcılar kullanımını etkinleştirmek için kullanabilirsiniz. Çalışan örnekler için bkz [özel bağlama örnekleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751479(v=vs.90)). Daha fazla bilgi için [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
## <a name="construction-of-a-custom-binding"></a>Özel bağlama oluşturma  
 Özel bağlama kullanılarak oluşturulur <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> bağlama "belirli bir sırayla dizilir" öğelerinin bir koleksiyondan Oluşturucusu:  
  
-   En üstünde isteğe bağlı olduğu <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> akmasını sağlar sınıfını işlemler.  
  
-   Sonraki isteğe bağlı olduğu <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> bir oturum ve mekanizmaları WS-ReliableMessaging belirtiminde tanımlanan sıralamasını sağlayan sınıf. Bir oturum SOAP ve aktarım aracılar arası.  
  
-   Sonraki isteğe bağlı olduğu <xref:System.ServiceModel.Channels.SecurityBindingElement> yetkilendirme, kimlik doğrulaması, koruma ve gizlilik gibi güvenlik özelliklerini sağlayan sınıf.  
  
-   Sonraki isteğe bağlı olduğu <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> çift yönlü iletişim, gibi HTTP desteği olmayan bir Aktarım Protokolü ile iki şekilde çift yönlü iletişim olanağı sağlayan sınıf.  
  
-   Sonraki isteğe bağlı olduğu <xref:System.ServiceModel.Channels.OneWayBindingElement>) tek yönlü iletişim sağlayan sınıf.  
  
-   Sonraki aşağıdakilerden biri olabilecek bir isteğe bağlı Akış güvenlik bağlama öğesi var.  
  
    -   <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
-   Sonraki gerekli ileti kodlama bağlama öğesi var. Kendi ileti Kodlayıcı veya üç ileti kodlama bağlamaları birini kullanabilirsiniz:  
  
    -   <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>  
  
 Altta bir gerekli aktarım öğesidir. Kendi taşıma veya Windows Communication Foundation (WCF) sağlayan aşağıdaki aktarım bağlama öğeleriyle birini kullanabilirsiniz:  
  
-   <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.PeerTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>  
  
-   <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>  
  
-   <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
  
 Aşağıdaki tabloda, her katman için seçenekler özetlenmektedir.  
  
|Katman|Seçenekler|Gerekli|  
|-----------|-------------|--------------|  
|İşlemler|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|Hayır|  
|Güvenilirlik|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|Hayır|  
|Güvenlik|<xref:System.ServiceModel.Channels.SecurityBindingElement>|Hayır|  
|Encoding|İkili, ileti aktarım en iyi duruma getirme mekanizması (MTOM) özel bir metin|Evet|  
|Taşıma|TCP, HTTP, HTTPS, adlandırılmış kanallar (IPC olarak da bilinir), eşler arası (P2P), Message Queuing (MSMQ olarak da bilinir), özel|Evet|  
  
 Ayrıca, kendi bağlama öğeleri tanımlayıp bunları herhangi bir önceki tanımlanmış katmanları arasında ekleyebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uç Nokta Oluşturmaya Genel Bakış](../../../../docs/framework/wcf/endpoint-creation-overview.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [Sistem Tarafından Sağlanan Bağlamalar](../../../../docs/framework/wcf/system-provided-bindings.md)
- [Nasıl yapılır: Sistem tarafından sağlanan bir bağlamayı özelleştirme](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)
- [\<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [Özel Bağlama](../../../../docs/framework/wcf/samples/custom-binding.md)
