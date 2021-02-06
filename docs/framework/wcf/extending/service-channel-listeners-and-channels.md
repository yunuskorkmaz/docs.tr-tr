---
description: 'Şu konuda daha fazla bilgi edinin: hizmet: Kanal dinleyicileri ve kanalları'
title: 'Hizmet: Kanal dinleyicileri ve kanallar'
ms.date: 03/30/2017
ms.assetid: 8ccbe0e8-7e55-441d-80de-5765f67542fa
ms.openlocfilehash: 2a092813faaa6f8964158adb55d11f21bf3ee60a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99644001"
---
# <a name="service-channel-listeners-and-channels"></a>Hizmet: Kanal dinleyicileri ve kanallar

Kanal nesnelerinin üç kategorisi vardır: kanallar, kanal dinleyicileri ve kanal fabrikaları. Kanallar, uygulama ve kanal yığını arasındaki arabirimdir. Kanal dinleyicileri, genellikle yeni bir gelen iletiye veya bağlantıya yanıt olarak alma (veya dinleme) tarafında kanal oluşturmaktan sorumludur. Kanal fabrikaları, bir uç noktayla iletişim başlatmak için gönderme tarafında kanal oluşturmaktan sorumludur.

## <a name="channel-listeners-and-channels"></a>Kanal dinleyicileri ve kanalları

Kanal dinleyicileri, kanalların oluşturulması ve ağ üzerinden veya ağdan ileti almaktan sorumludur. Alınan iletiler, kanal dinleyicisi tarafından oluşturulan bir kanalı kullanarak yukarıdaki katmana dağıtılır.

Aşağıdaki diyagramda ileti alma ve bunları yukarıdaki katmana sunma süreci gösterilmektedir.

![Kanal dinleyicileri ve kanalları](./media/wcfc-wcfchannelsigure1highlevelc.gif "wcfc_WCFChannelsigure1HighLevelc")

Kanallar aracılığıyla iletileri alan ve katmana teslim eden bir kanal dinleyicisi.

Bu işlem, uygulama gerçekten bir kuyruk kullanmayabilir ancak her kanaldaki bir sıra olarak kavramsal olarak modellenebilir. Kanal dinleyicisi, aşağıdaki katmandan veya ağdan ileti almaktan ve bunları sıraya yerleştirmekten sorumludur. Kanal, kuyruktan ileti almak ve bu katman bir ileti istediğinde, örneğin kanala çağrı yaparak yukarıdaki katmana teslim etmeden sorumludur `Receive` .

WCF bu işlem için temel sınıf yardımcıları sağlar. Bu makalede ele alınan kanal Yardımcısı sınıflarının bir diyagramı için bkz. [Kanal modeline genel bakış](channel-model-overview.md).

- <xref:System.ServiceModel.Channels.CommunicationObject>Sınıfı, <xref:System.ServiceModel.ICommunicationObject> [Kanal geliştirme](developing-channels.md)ve adım 2 ' de açıklanan durum makinesini uygular ve uygular.

- <xref:System.ServiceModel.Channels.ChannelManagerBase>Sınıfı, <xref:System.ServiceModel.Channels.CommunicationObject> ve için Birleşik bir temel sınıf sağlar <xref:System.ServiceModel.Channels.ChannelFactoryBase> <xref:System.ServiceModel.Channels.ChannelListenerBase> . <xref:System.ServiceModel.Channels.ChannelManagerBase>Sınıfı ile birlikte çalışarak <xref:System.ServiceModel.Channels.ChannelBase> , uygulayan bir temel sınıf olan <xref:System.ServiceModel.Channels.IChannel> .

- <xref:System.ServiceModel.Channels.ChannelFactoryBase>Sınıfı, <xref:System.ServiceModel.Channels.ChannelManagerBase> ve <xref:System.ServiceModel.Channels.IChannelFactory> `CreateChannel` yüklerini tek bir soyut yöntemde uygular ve birleştirir `OnCreateChannel` .

- <xref:System.ServiceModel.Channels.ChannelListenerBase>Sınıfı uygular <xref:System.ServiceModel.Channels.IChannelListener> . Temel durum yönetiminden çok dikkat edin.

Aşağıdaki tartışma, [taşıma: UDP](../samples/transport-udp.md) örneğine dayalıdır.

## <a name="creating-a-channel-listener"></a>Kanal dinleyicisi oluşturma

`UdpChannelListener`Örneğin uyguladığı örnek sınıfından türetiliyor <xref:System.ServiceModel.Channels.ChannelListenerBase> . Veri birimlerini almak için tek bir UDP yuvası kullanır. `OnOpen`Yöntemi, UDP yuvasını zaman uyumsuz bir döngüde kullanarak verileri alır. Veriler daha sonra ileti kodlama sistemi kullanılarak iletilere dönüştürülür:

```csharp
message = UdpConstants.MessageEncoder.ReadMessage(
  new ArraySegment<byte>(buffer, 0, count),
  bufferManager
);
```

Aynı veri birimi kanalı, bir dizi kaynaktan gelen iletileri temsil ettiğinden, `UdpChannelListener` tek bir dinleyici olur. Tek seferde bu dinleyiciyle ilişkili en fazla bir etkin bulunur <xref:System.ServiceModel.Channels.IChannel> . Örnek, yalnızca yöntemi tarafından döndürülen bir kanal <xref:System.ServiceModel.Channels.ChannelListenerBase%601.AcceptChannel%2A> daha sonra atıldığı takdirde bir tane oluşturur. Bir ileti alındığında, bu Singleton kanalında sıraya alınır.

### <a name="udpinputchannel"></a>UdpInputChannel

`UdpInputChannel`Sınıfı uygular <xref:System.ServiceModel.Channels.IInputChannel> . Bu, kendi yuvası tarafından doldurulan bir gelen ileti kuyruğundan oluşur `UdpChannelListener` . Bu iletiler yöntemi tarafından kaldırılır <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A> .
