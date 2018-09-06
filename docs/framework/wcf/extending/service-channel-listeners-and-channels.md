---
title: 'Hizmet: kanal dinleyicileri ve kanallar'
ms.date: 03/30/2017
ms.assetid: 8ccbe0e8-7e55-441d-80de-5765f67542fa
ms.openlocfilehash: 88bfdc879e4f3c7df6b2c4035c7ed7fdc2b4c41d
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43788794"
---
# <a name="service-channel-listeners-and-channels"></a>Hizmet: kanal dinleyicileri ve kanallar

Kanal nesnelerin üç kategoriye ayrılır: kanallar, kanal dinleyicileri ve kanal fabrikaları. Kanallar, uygulama ve kanal yığını arasındaki arabirim olan. Kanal dinleyicileri alma (ya da dinleme) tarafında, genellikle yeni bir gelen iletiyi veya bağlantı yanıttaki kanallar oluşturmak için sorumludur. Kanal fabrikası, bir uç nokta ile iletişim başlatmak için gönderme tarafında kanallar oluşturmak için sorumludur.

## <a name="channel-listeners-and-channels"></a>Kanal dinleyicileri ve kanallar

Kanal dinleyicileri oluşturma Kanallar ve alıcı iletileri için katmandan veya ağdan sorumludur. Alınan iletiler, kanal dinleyicisi tarafından oluşturulan bir kanal kullanarak yukarıda bir katmana dağıtılır.

Aşağıdaki diyagram, iletileri almak ve bunları üst katmanına teslim işlemini gösterir.

![Kanal dinleyicileri ve kanallar](./media/wcfc-wcfchannelsigure1highlevelc.gif "wcfc_WCFChannelsigure1HighLevelc")

İleti alma ve katmana kanal üzerinden teslim kanal dinleyicisi.

Ancak uygulama aslında bir kuyruk kullanabilirsiniz değil işlem olarak bir kuyruk her kanal içinde kavramsal olarak modellenebilir. Katmandan alıcı iletileri veya ağ ve bunları sıraya koymak için kanal dinleyicisi sorumludur. Kuyruktan ileti alma ve bunları bir katmana katman bir ileti için örneğin çağırarak sorduğunda yukarıda teslim etme için kanal sorumludur `Receive` kanal üzerinde.

WCF bu işlem için temel sınıfı Yardımcıları sağlar. (Bu makalede ele alınan kanal yardımcı sınıfları diyagramı için bkz: [kanal modeline genel bakış](channel-model-overview.md).)

- <xref:System.ServiceModel.Channels.CommunicationObject> Sınıfının Implements <xref:System.ServiceModel.ICommunicationObject> ve 2. adımda açıklanan Durum makinesi uygular [geliştirme kanalları](developing-channels.md).

- <xref:System.ServiceModel.Channels.ChannelManagerBase> Sınıfının Implements <xref:System.ServiceModel.Channels.CommunicationObject> ve birleşik bir temel sınıf için <xref:System.ServiceModel.Channels.ChannelFactoryBase> ve <xref:System.ServiceModel.Channels.ChannelListenerBase>. <xref:System.ServiceModel.Channels.ChannelManagerBase> Sınıfı çalışır birlikte <xref:System.ServiceModel.Channels.ChannelBase>, uygulayan bir temel sınıf olan <xref:System.ServiceModel.Channels.IChannel>.

- <xref:System.ServiceModel.Channels.ChannelFactoryBase> Sınıfının Implements <xref:System.ServiceModel.Channels.ChannelManagerBase> ve <xref:System.ServiceModel.Channels.IChannelFactory> ve birleştirir `CreateChannel` aşırı birine `OnCreateChannel` soyut yöntemi.

- <xref:System.ServiceModel.Channels.ChannelListenerBase> Sınıfının Implements <xref:System.ServiceModel.Channels.IChannelListener>. Bu temel durum yönetimini üstlenir.

Aşağıdaki tartışma temel aldığı [taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örnek.

## <a name="creating-a-channel-listener"></a>Bir kanal dinleyicisi oluşturma

`UdpChannelListener` Örnek uyguladığını türetildiği <xref:System.ServiceModel.Channels.ChannelListenerBase> sınıfı. Veri birimleri almak için tek bir UDP yuva kullanır. `OnOpen` Yöntemi zaman uyumsuz bir döngüde UDP yuvayı kullanan veri alır. Veriler daha sonra sistem kodlamasını kullanarak ileti dönüştürülür:

```csharp
message = UdpConstants.MessageEncoder.ReadMessage(
  new ArraySegment<byte>(buffer, 0, count),
  bufferManager
);
```

Birçok kaynaktan gelen iletileri aynı veri birimi kanalı temsil ettiğinden `UdpChannelListener` tekil dinleyici. Çoğu bir tane aktif yoktur <xref:System.ServiceModel.Channels.IChannel> aynı anda bu dinleyici ile ilişkili. Tarafından döndürülen bir kanal, başka bir örnek oluşturur <xref:System.ServiceModel.Channels.ChannelListenerBase%601.AcceptChannel%2A> yöntemi daha sonra atıldı. Bir ileti alındığında bu singleton kanal içine sıraya olur.

### <a name="udpinputchannel"></a>UdpInputChannel

`UdpInputChannel` Sınıfının Implements <xref:System.ServiceModel.Channels.IInputChannel>. Bir kuyruk tarafından doldurulur gelen iletilerin oluşan `UdpChannelListener`kullanıcının yuva. Bu iletiler tarafından çıkarıldığını <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A> yöntemi.
