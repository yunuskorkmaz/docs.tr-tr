---
title: İleti Aktarma Akışı
ms.date: 03/30/2017
ms.assetid: 72a47a51-e5e7-4b76-b24a-299d51e0ae5a
ms.openlocfilehash: 6f16ab16235c9fcbe0a151d5c404df96080192c6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64585936"
---
# <a name="streaming-message-transfer"></a>İleti Aktarma Akışı
Windows Communication Foundation (WCF) taşımalar iletileri aktarmak için iki modu destekler:  
  
- Arabelleğe alınan aktarımları aktarma işlemi tamamlanana kadar tüm ileti içinde bir bellek arabelleğini basılı tutun. Bir alıcı okumadan önce bir arabelleğe alınan ileti tamamen teslim edilmelidir.  
  
- Akış aktarımları ileti akışı olarak kullanıma sunar. Alıcı, tamamen teslim edilmeden önce iletiyi işlemeyi başlatır.  
  
- Akış aktarımları, büyük bellek arabelleği gereksinimini ortadan kaldırarak hizmet ölçeklenebilirliği artırabilirsiniz. Aktarım modunu değiştirme ölçeklenebilirliği iyileştirdi olmadığını aktarılan iletileri boyutuna bağlıdır. Büyük ileti boyutları, akış aktarımları kullanarak favor.  
  
 Varsayılan olarak HTTP, TCP/IP'yi ve adlandırılmış kanal taşıma arabelleğe alınan aktarımları kullanır. Bu belge, bu bir arabelleğe alınan taşımalar geçmek açıklar akış aktarım modu ve böylece sonuçlarını.  
  
## <a name="enabling-streamed-transfers"></a>Akış aktarımları etkinleştirme  
 Arabelleğe alınan ve akış aktarma modları arasında seçerek aktarım bağlama öğesi üzerindeki gerçekleştirilir. Bağlama öğesi olan bir <xref:System.ServiceModel.TransferMode> ayarlanabilir özelliği `Buffered`, `Streamed`, `StreamedRequest`, veya `StreamedResponse`. Aktarım Modu ayarını `Streamed` akış çift yönlü iletişimi sağlar. Aktarım Modu ayarını `StreamedRequest` veya `StreamedResponse` akış belirtilen yönde yalnızca iletişimi etkinleştirir.  
  
 <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.NetTcpBinding>, Ve <xref:System.ServiceModel.NetNamedPipeBinding> bağlamaları sunmaya <xref:System.ServiceModel.TransferMode> özelliği. Diğer aktarımı için aktarım modu ayarlamak için özel bir bağlama oluşturmanız gerekir.  
  
 Arabelleğe alınan ya da akış aktarımları karar, uç noktanın yerel bir karardır. HTTP taşımaları için bir bağlantı üzerinden ya da sunucuları ve diğer aracılar için aktarım modunu dağıtılmaz. Hizmet arabirimi açıklamasında aktarım modunu ayarlama yansıtılmaz. Hizmet istemci sınıf oluşturduktan sonra akış aktarımları ile modu ayarlamak için kullanılması hedeflenen hizmetler için yapılandırma dosyasını düzenlemeniz gerekir. TCP ve adlandırılmış kanal aktarımlar, aktarım modu İlkesi onaylama olarak yayılır.  
  
 Kod örnekleri için bkz. [nasıl yapılır: Akışı etkinleştir](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md).  
  
## <a name="enabling-asynchronous-streaming"></a>Zaman uyumsuz akış'ı etkinleştirme  
 Zaman uyumsuz akış etkinleştirmek için eklemeniz <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior> kümesini ve hizmet ana bilgisayarı için uç nokta davranışı, <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.AsynchronousSendEnabled%2A> özelliğini `true`.  
  
 WCF bu sürüm ayrıca adde doğru zaman uyumsuz gönderme tarafında akış yeteneği. Bu senaryolarda bazıları okuma yavaş olan birden çok istemciye iletileri burada akış hizmetinin ölçeklenebilirliği artırır; büyük olasılıkla Ağ Tıkanıklığı veya olan nedeniyle hiç okunmuyor. Bu senaryolarda WCF istemci başına hizmetine tek tek iş parçacığı artık engeller. Bu, hizmet birden çok daha fazla istemci böylece hizmetinin ölçeklenebilirliği artırma işleminin olmasını sağlar.  
  
## <a name="restrictions-on-streamed-transfers"></a>Akış aktarımları kısıtlamaları  
 Akış aktarım modunu kullanarak ek kısıtlamalar uygulamak çalışma zamanı neden olur.  
  
 Bir akış taşıma arasında gerçekleşen işlem, giriş veya çıkış en fazla bir parametre ile bir sözleşme olabilir. Bu parametre tüm ileti gövdesi ile karşılık gelir ve olmalıdır bir <xref:System.ServiceModel.Channels.Message>, bir türü türetilmiş <xref:System.IO.Stream>, veya bir <xref:System.Xml.Serialization.IXmlSerializable> uygulaması. Bir işlem için dönüş değeri bir output parametresi olmakla eşdeğerdir.  
  
 İletilerin aktarımları için arabelleğe işlemleri ve SOAP ileti düzeyi güvenliği, güvenilir Mesajlaşma gibi bazı WCF özellikleri kullanır. Bu özellikleri kullanmaya azaltın veya akış kullanılarak elde edilen performans avantajlarını ortadan kaldırır. Bir akış taşıma güvenliğini sağlamak için aktarım düzeyi güvenlik yalnızca kullanın veya aktarma düzeyinde güvenliğin yanı sıra yalnızca kimlik doğrulaması ileti güvenliği kullanın.  
  
 Hatta aktarım modunu akış ayarlandığında SOAP üstbilgileri her zaman, arabelleğe alınır. Bir ileti için üstbilgiler boyutunu aşamaz `MaxBufferSize` aktarım kotası. Bu ayar hakkında daha fazla bilgi için bkz. [taşıma kotaları](../../../../docs/framework/wcf/feature-details/transport-quotas.md).  
  
## <a name="differences-between-buffered-and-streamed-transfers"></a>Arabelleğe alınan ve akış aktarımları arasındaki farklar  
 Akış için arabelleğe alınan aktarma modundan değiştirme, TCP ve adlandırılmış kanal taşıma yerel kanal şeklini değiştirir. Arabelleğe alınan aktarımları için yerel kanal şekildir <xref:System.ServiceModel.Channels.IDuplexSessionChannel>. Yerel kanal akış aktarımları için olan <xref:System.ServiceModel.Channels.IRequestChannel> ve <xref:System.ServiceModel.Channels.IReplyChannel>. Doğrudan bu kullanan mevcut bir uygulamayı aktarım modu değiştirme taşır (diğer bir deyişle, bir hizmet sözleşmesini üzerinden değil) beklenen kanal şekli için kanal fabrikaları ve dinleyicileri değiştirilmesi gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Akışı etkinleştir](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md)
