---
title: "Özel Bağlamalar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation, endpoints
- Windows Communication Foundation, configuration
ms.assetid: 58532b6d-4eea-4a4f-854f-a1c8c842564d
caps.latest.revision: "33"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2a3da437f742c46a2229aa00db732b5437ec15e3
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="custom-bindings"></a>Özel Bağlamalar
Kullanabileceğiniz <xref:System.ServiceModel.Channels.CustomBinding> sistem tarafından sağlanan bağlamalar birini hizmetinizi gereksinimlerini karşılamadığında sınıfı. Tüm bağlamaları bağlama öğelerinin sıralı bir kümesinden oluşturulur. Özel bağlamalar sistem tarafından sağlanan bağlama öğeleri kümesinden oluşturulabilir veya kullanıcı tanımlı özel bağlama öğelerini içerebilir. Özel bağlama öğeleri yeni taşımaları veya bir hizmet uç noktada kodlayıcılar kullanımını etkinleştirmek için kullanabilirsiniz. Çalışma örnekler için bkz: [özel bağlama örnekleri](http://msdn.microsoft.com/library/657e8143-beb0-472d-9cfe-ed1a19c2ab08). [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
## <a name="construction-of-a-custom-binding"></a>Özel bağlama oluşturma  
 Özel bağlama kullanılarak oluşturulan <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> bağlama "belirli bir sırada yığılma" öğelerinin bir koleksiyonu oluşturucudan:  
  
-   En üstte bir isteğe bağlı olduğu <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> akan sağlayan sınıfı işlemleri.  
  
-   Sonraki isteğe bağlı olduğu <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> bir oturum ve WS-ReliableMessaging belirtiminde tanımlanan mekanizmaları sipariş sağlayan sınıf. Bir oturum SOAP ve aktarım aracılar arası.  
  
-   Sonraki isteğe bağlı olduğu <xref:System.ServiceModel.Channels.SecurityBindingElement> yetkilendirme, kimlik doğrulama, koruma ve gizliliği gibi güvenlik özellikleri sağlayan sınıf.  
  
-   Sonraki isteğe bağlı olduğu <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> sahip çift yönlü iletişimi HTTP gibi yerel, desteklemeyen bir Aktarım Protokolü ile iki şekilde çift yönlü iletişim olanağı sağlayan sınıf.  
  
-   Sonraki isteğe bağlı olduğu <xref:System.ServiceModel.Channels.OneWayBindingElement>) tek yönlü iletişim sağlayan sınıf.  
  
-   Sonraki aşağıdakilerden biri olabilen bir isteğe bağlı Akış güvenlik bağlama öğedir.  
  
    -   <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
-   Sonraki gerekli ileti kodlama bağlama öğesi var. Kendi ileti Kodlayıcı veya üç ileti kodlama bağlamaları birini kullanabilirsiniz:  
  
    -   <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>  
  
 Pencerenin alt gerekli aktarım öğedir. Kendi taşıma veya aşağıdaki aktarım bağlama öğeleriyle birini kullanabilirsiniz [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] sağlar:  
  
-   <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.PeerTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>  
  
-   <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>  
  
-   <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
  
 Aşağıdaki tabloda, her katman için seçenekleri özetler.  
  
|Katman|Seçenekler|Gerekli|  
|-----------|-------------|--------------|  
|İşlemler|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|Hayır|  
|Güvenilirlik|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|Hayır|  
|Güvenlik|<xref:System.ServiceModel.Channels.SecurityBindingElement>|Hayır|  
|Encoding|İkili, ileti iletim en iyi duruma getirme mekanizmasını (MTOM) özel bir metin|Evet|  
|Taşıma|TCP, HTTP, HTTPS, adlandırılmış kanallar (IPC olarak da bilinir) eşler arası (P2P), Message Queuing (MSMQ olarak da bilinir), özel|Evet|  
  
 Ayrıca, kendi bağlama öğeleri tanımlamak ve herhangi bir önceki tanımlı katmanlar arasında ekleyin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uç Nokta Oluşturmaya Genel Bakış](../../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [Sistem Tarafından Sağlanan Bağlamalar](../../../../docs/framework/wcf/system-provided-bindings.md)  
 [Nasıl yapılır: Sistem Tarafından Sağlanan Bir Bağlamayı Özelleştirme](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)  
 [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [Özel Bağlama](../../../../docs/framework/wcf/samples/custom-binding.md)
