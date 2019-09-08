---
title: Özel Bağlamalar
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, endpoints
- Windows Communication Foundation, configuration
ms.assetid: 58532b6d-4eea-4a4f-854f-a1c8c842564d
ms.openlocfilehash: a4b3abfe9be25c9080a362eb4a6e4c7b070528f1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797231"
---
# <a name="custom-bindings"></a>Özel Bağlamalar

Sistem tarafından belirtilen bağlamalardan biri hizmetinizin gereksinimlerini karşılamadığında <xref:System.ServiceModel.Channels.CustomBinding> sınıfı kullanabilirsiniz. Tüm bağlamalar sıralı bir bağlama öğeleri kümesinden oluşturulur. Özel Bağlamalar, sistem tarafından sağlanmış bir bağlama öğelerinden oluşturulabilir veya Kullanıcı tanımlı özel bağlama öğeleri içerebilir. Bir hizmet uç noktasında yeni aktarımların veya kodlayıcıların kullanımını etkinleştirmek için, örneğin, özel bağlama öğelerini kullanabilirsiniz. Çalışma örnekleri için bkz. [özel bağlama örnekleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751479(v=vs.90)). Daha fazla bilgi için bkz [ \<. CustomBinding >](../../configure-apps/file-schema/wcf/custombinding.md).

## <a name="construction-of-a-custom-binding"></a>Özel bağlama oluşturma

Özel bağlama, belirli bir sırada " <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> yığılmış" olan bağlama öğeleri koleksiyonundan Oluşturucu kullanılarak oluşturulur:

- En üstte, akan işlemlere izin <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> veren isteğe bağlı bir sınıftır.

- Next, WS- <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> ReliableMessaging belirtiminde tanımlanan bir oturum ve sıralama mekanizmalarını sağlayan isteğe bağlı bir sınıftır. Bir oturum, SOAP ve aktarım aracıları arası olabilir.

- Daha sonra yetkilendirme, <xref:System.ServiceModel.Channels.SecurityBindingElement> kimlik doğrulama, koruma ve gizlilik gibi güvenlik özellikleri sağlayan isteğe bağlı bir sınıftır.

- Daha sonra, http <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> gibi çift yönlü iletişimi desteklemeyen bir Aktarım Protokolü ile iki yönlü çift yönlü iletişim olanağı sağlayan isteğe bağlı bir sınıftır.

- Next, tek yönlü <xref:System.ServiceModel.Channels.OneWayBindingElement>iletişim sağlayan bir isteğe bağlı) sınıftır.

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
|İşlemler|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|Hayır|
|Güvenilirlik|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|Hayır|
|Güvenlik|<xref:System.ServiceModel.Channels.SecurityBindingElement>|Hayır|
|Encoding|Metin, ikili, Ileti Iletimi Iyileştirme mekanizması (MTOM), özel|Evet|
|Aktarım|TCP, HTTP, HTTPS, adlandırılmış kanallar (IPC olarak da bilinir), eşler arası (P2P), Message Queuing (MSMQ olarak da bilinir), özel|Evet|

Ayrıca, kendi bağlama öğelerinizi tanımlayabilir ve bunları önceki tanımlı katmanlardan herhangi biri arasına ekleyebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Uç Nokta Oluşturmaya Genel Bakış](../endpoint-creation-overview.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../using-bindings-to-configure-services-and-clients.md)
- [Sistem Tarafından Sağlanan Bağlamalar](../system-provided-bindings.md)
- [Nasıl yapılır: Sistem tarafından sağlanmış bağlamayı özelleştirme](how-to-customize-a-system-provided-binding.md)
- [\<customBinding >](../../configure-apps/file-schema/wcf/custombinding.md)
- [Özel Bağlama](../samples/custom-binding.md)
