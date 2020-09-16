---
title: Özel Bağlamalar
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, endpoints
- Windows Communication Foundation, configuration
ms.assetid: 58532b6d-4eea-4a4f-854f-a1c8c842564d
ms.openlocfilehash: 062aba26227fedeea3e5f462ebf5d55cf0cba56c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90540003"
---
# <a name="custom-bindings"></a>Özel Bağlamalar

<xref:System.ServiceModel.Channels.CustomBinding>Sistem tarafından belirtilen bağlamalardan biri hizmetinizin gereksinimlerini karşılamadığında sınıfı kullanabilirsiniz. Tüm bağlamalar sıralı bir bağlama öğeleri kümesinden oluşturulur. Özel Bağlamalar, sistem tarafından sağlanmış bir bağlama öğelerinden oluşturulabilir veya Kullanıcı tanımlı özel bağlama öğeleri içerebilir. Bir hizmet uç noktasında yeni aktarımların veya kodlayıcıların kullanımını etkinleştirmek için, örneğin, özel bağlama öğelerini kullanabilirsiniz. Çalışma örnekleri için bkz. [özel bağlama örnekleri](/previous-versions/dotnet/netframework-3.5/ms751479(v=vs.90)). Daha fazla bilgi için bkz. [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md).

## <a name="construction-of-a-custom-binding"></a>Özel bağlama oluşturma

Özel bağlama, <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> belirli bir sırada "yığılmış" olan bağlama öğeleri koleksiyonundan Oluşturucu kullanılarak oluşturulur:

- En üstte, <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> akan işlemlere izin veren isteğe bağlı bir sınıftır.

- Next, <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> WS-ReliableMessaging belirtiminde tanımlanan bir oturum ve sıralama mekanizmalarını sağlayan isteğe bağlı bir sınıftır. Bir oturum, SOAP ve aktarım aracıları arası olabilir.

- Daha sonra <xref:System.ServiceModel.Channels.SecurityBindingElement> Yetkilendirme, kimlik doğrulama, koruma ve gizlilik gibi güvenlik özellikleri sağlayan isteğe bağlı bir sınıftır.

- Daha sonra, <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> http gibi çift yönlü iletişimi desteklemeyen bir Aktarım Protokolü ile iki yönlü çift yönlü iletişim olanağı sağlayan isteğe bağlı bir sınıftır.

- Next, <xref:System.ServiceModel.Channels.OneWayBindingElement> tek yönlü iletişim sağlayan bir isteğe bağlı) sınıftır.

- Next, aşağıdakilerden biri olabilecek isteğe bağlı bir akış güvenlik bağlama öğesidir.

  - <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>

- Next, gerekli bir ileti kodlama bağlama öğesidir. Kendi ileti kodlayıcısını veya üç ileti kodlama bağlamalarından birini kullanabilirsiniz:

  - <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>

En altta gerekli bir taşıma öğesidir. Kendi taşıyıcıyı veya aşağıdaki taşıma bağlama öğelerinden birini Windows Communication Foundation (WCF) aşağıdakileri sağlar:

- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>

- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>

- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>

- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>

- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>

- <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>

- <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>

Aşağıdaki tabloda her bir katmanın seçenekleri özetlenmektedir.

|Katman|Seçenekler|Gerekli|
|-----------|-------------|--------------|
|İşlemler|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|No|
|Güvenilirlik|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|No|
|Güvenlik|<xref:System.ServiceModel.Channels.SecurityBindingElement>|No|
|Encoding|Metin, ikili, Ileti Iletimi Iyileştirme mekanizması (MTOM), özel|Yes|
|Aktarım|TCP, HTTP, HTTPS, adlandırılmış kanallar (IPC olarak da bilinir), eşler arası (P2P), Message Queuing (MSMQ olarak da bilinir), özel|Yes|

Ayrıca, kendi bağlama öğelerinizi tanımlayabilir ve bunları önceki tanımlı katmanlardan herhangi biri arasına ekleyebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Uç Noktası Oluşturma Genel Bakış](../endpoint-creation-overview.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../using-bindings-to-configure-services-and-clients.md)
- [Sistem Tarafından Sağlanan Bağlamalar](../system-provided-bindings.md)
- [Nasıl yapılır: Sistem Tarafından Sağlanan Bir Bağlamayı Özelleştirme](how-to-customize-a-system-provided-binding.md)
- [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md)
- [Özel Bağlama](../samples/custom-binding.md)
