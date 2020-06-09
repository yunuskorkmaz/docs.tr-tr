---
title: İleti Aktarma Akışı
ms.date: 03/30/2017
ms.assetid: 72a47a51-e5e7-4b76-b24a-299d51e0ae5a
ms.openlocfilehash: 462144856750a1b8726b574fdc82746da2d72ff7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594796"
---
# <a name="streaming-message-transfer"></a>İleti Aktarma Akışı
Windows Communication Foundation (WCF) aktarımları, iletileri aktarmaya yönelik iki modu destekler:  
  
- Arabelleğe alınan aktarımlar, aktarım tamamlanana kadar tüm iletiyi bir bellek arabelleğine tutar. Bir alıcının okuyabilmesi için, arabelleğe alınmış bir iletinin tamamen teslim edilmesi gerekir.  
  
- Akışlı aktarımlar, iletiyi bir akış olarak kullanıma sunar. Alıcı, tamamen teslim edilmeden önce iletiyi işlemeye başlar.  
  
- Akışlı aktarımlar, büyük bellek arabelleklerinin gereksinimini ortadan kaldırarak bir hizmetin ölçeklenebilirliğini iyileştirebilir. Aktarım modunun değiştirilmesi, ölçeklenebilirliği artırmak için, aktarılmakta olan iletilerin boyutuna bağlıdır. Büyük ileti boyutları akan aktarımları kullanmayı tercih eder.  
  
 Varsayılan olarak, HTTP, TCP/IP ve adlandırılmış kanal aktarımları, arabelleğe alınmış aktarımları kullanır. Bu belgede, Bu aktarımların arabelleğe alınan aktarım modundan akışlı aktarım moduna nasıl değiştirileceği ve bunu yapmanın sonuçları açıklanmaktadır.  
  
## <a name="enabling-streamed-transfers"></a>Akışlı aktarımları etkinleştirme  
 Arabelleğe alınan ve akış aktarım modları arasında seçim yapmak, taşımanın bağlama öğesinde yapılır. Binding öğesi,,, <xref:System.ServiceModel.TransferMode> veya olarak ayarlanabilir bir özelliğine sahiptir `Buffered` `Streamed` `StreamedRequest` `StreamedResponse` . Aktarım modunun, `Streamed` her iki yönde de akış iletişimini sağlamak üzere ayarlanması. Aktarım modunu `StreamedRequest` `StreamedResponse` yalnızca belirtilen yönde veya akış iletişimini için olarak ayarlama.  
  
 <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.NetTcpBinding> Ve <xref:System.ServiceModel.NetNamedPipeBinding> bağlamaları özelliğini kullanıma sunar <xref:System.ServiceModel.TransferMode> . Diğer aktarımlar için, aktarım modunu ayarlamak üzere özel bir bağlama oluşturmanız gerekir.  
  
 Ara belleğe alınmış veya akış aktarımları kullanma kararı, uç noktanın yerel bir karardır. HTTP aktarımları için, aktarım modu bir bağlantı veya sunuculara ve diğer aracılar arasında yayılmaz. Aktarım modunun ayarlanması, hizmet arabiriminin açıklamasına yansıtılmaz. Bir hizmet için istemci sınıfı oluşturduktan sonra, modu ayarlamak için akışlı aktarımlarla kullanılması amaçlanan hizmetler için yapılandırma dosyasını düzenlemeniz gerekir. TCP ve adlandırılmış kanal aktarımları için, aktarım modu bir ilke onaylama işlemi olarak dağıtılır.  
  
 Kod örnekleri için bkz. [nasıl yapılır: akışı etkinleştirme](how-to-enable-streaming.md).  
  
## <a name="enabling-asynchronous-streaming"></a>Zaman uyumsuz akışı etkinleştirme  
 Zaman uyumsuz akışı etkinleştirmek için, <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior> uç nokta davranışını hizmet konağına ekleyin ve <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.AsynchronousSendEnabled%2A> özelliğini olarak ayarlayın `true` .  
  
 WCF 'nin bu sürümü, gönderme tarafında gerçek zaman uyumsuz akış özelliğini de de de ektir. Bu, hizmetin bir kısmını okurken yavaş olan birden çok istemciye akış yaptığı senaryolarda hizmetin ölçeklenebilirliğini geliştirir; büyük olasılıkla ağ tıkanıklığı nedeniyle veya hiç okunmayan. Bu senaryolarda, WCF artık istemci başına hizmette bireysel iş parçacıklarını engeller. Bu, hizmetin daha fazla istemciyi işleyebilmesini sağlar ve bu sayede hizmetin ölçeklenebilirliğini geliştirir.  
  
## <a name="restrictions-on-streamed-transfers"></a>Akış aktarımları için kısıtlamalar  
 Akan aktarım modunun kullanılması, çalışma süresinin ek kısıtlamalar zorlamasına neden olur.  
  
 Akışlı bir aktarımda oluşan işlemler, en fazla bir giriş veya çıkış parametresi olan bir sözleşmeye sahip olabilir. Bu parametre ileti gövdesinin tamamına karşılık gelir ve bir <xref:System.ServiceModel.Channels.Message> , türetilmiş türü <xref:System.IO.Stream> veya bir uygulama olmalıdır <xref:System.Xml.Serialization.IXmlSerializable> . Bir işlem için dönüş değeri olması, çıkış parametresine sahip olmaya eşdeğerdir.  
  
 Güvenilir Mesajlaşma, işlemler ve SOAP ileti düzeyi güvenliği gibi bazı WCF özellikleri, iletimlere yönelik arabelleğe alma iletilerini kullanır. Bu özelliklerin kullanılması, akış kullanılarak kazanılan performans avantajlarını azaltabilir veya ortadan kaldırabilir. Akışlı bir taşımanın güvenliğini sağlamak için yalnızca aktarım düzeyi güvenlik kullanın veya aktarım düzeyi güvenlik ' i ve yalnızca kimlik doğrulama iletisi güvenliği ' ni kullanın.  
  
 Aktarım modu akış olarak ayarlandığında bile SOAP üstbilgileri her zaman arabelleğe alınır. İleti üstbilgileri, `MaxBufferSize` Aktarım kotasının boyutunu aşmamalıdır. Bu ayar hakkında daha fazla bilgi için bkz. [Aktarım kotaları](transport-quotas.md).  
  
## <a name="differences-between-buffered-and-streamed-transfers"></a>Arabellekli ve akışlı aktarımlar arasındaki farklılıklar  
 Aktarım modunun arabelleğe alınıp akışlı olarak değiştirilmesi, TCP ve adlandırılmış kanal taşımalarının yerel kanal şeklini de değiştirir. Arabelleğe alınan aktarımlar için, yerel kanal şekli olur <xref:System.ServiceModel.Channels.IDuplexSessionChannel> . Akışlı aktarımlar için, yerel kanallar ve ' <xref:System.ServiceModel.Channels.IRequestChannel> dir <xref:System.ServiceModel.Channels.IReplyChannel> . Bu taşımaları doğrudan kullanan mevcut bir uygulamada (bir hizmet sözleşmesi aracılığıyla değil) aktarım modunun değiştirilmesi, kanal fabrikaları ve dinleyicileri için beklenen kanal şeklinin değiştirilmesini gerektirir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Akışı Etkinleştirme](how-to-enable-streaming.md)
