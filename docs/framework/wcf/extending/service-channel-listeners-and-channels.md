---
title: 'Hizmet: Kanal dinleyicileri ve kanalları'
ms.date: 03/30/2017
ms.assetid: 8ccbe0e8-7e55-441d-80de-5765f67542fa
ms.openlocfilehash: 0a740f5dcf682c3c140adb9c4c7c9678c4eae132
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797174"
---
# <a name="service-channel-listeners-and-channels"></a>Hizmet: Kanal dinleyicileri ve kanalları

Kanal nesnelerinin üç kategorisi vardır: kanallar, kanal dinleyicileri ve kanal fabrikaları. Kanallar, uygulama ve kanal yığını arasındaki arabirimdir. Kanal dinleyicileri, genellikle yeni bir gelen iletiye veya bağlantıya yanıt olarak alma (veya dinleme) tarafında kanal oluşturmaktan sorumludur. Kanal fabrikaları, bir uç noktayla iletişim başlatmak için gönderme tarafında kanal oluşturmaktan sorumludur.

## <a name="channel-listeners-and-channels"></a>Kanal dinleyicileri ve kanalları

Kanal dinleyicileri, kanalların oluşturulması ve ağ üzerinden veya ağdan ileti almaktan sorumludur. Alınan iletiler, kanal dinleyicisi tarafından oluşturulan bir kanalı kullanarak yukarıdaki katmana dağıtılır.

Aşağıdaki diyagramda ileti alma ve bunları yukarıdaki katmana sunma süreci gösterilmektedir.

![Kanal dinleyicileri ve kanalları](./media/wcfc-wcfchannelsigure1highlevelc.gif "wcfc_WCFChannelsigure1HighLevelc")

Kanallar aracılığıyla iletileri alan ve katmana teslim eden bir kanal dinleyicisi.

Bu işlem, uygulama gerçekten bir kuyruk kullanmayabilir ancak her kanaldaki bir sıra olarak kavramsal olarak modellenebilir. Kanal dinleyicisi, aşağıdaki katmandan veya ağdan ileti almaktan ve bunları sıraya yerleştirmekten sorumludur. Kanal, kuyruktan ileti almak ve bu katman bir ileti istediğinde, örneğin kanala çağrı `Receive` yaparak yukarıdaki katmana teslim etmeden sorumludur.

WCF bu işlem için temel sınıf yardımcıları sağlar. (Bu makalede ele alınan kanal Yardımcısı sınıflarının bir diyagramı için bkz. [Kanal modeline genel bakış](channel-model-overview.md).)

- Sınıfı, [Kanal geliştirme](developing-channels.md)ve adım 2 ' de açıklanan durum makinesini uygular <xref:System.ServiceModel.ICommunicationObject> ve uygular. <xref:System.ServiceModel.Channels.CommunicationObject>

- Sınıfı, <xref:System.ServiceModel.Channels.ChannelManagerBase>ve içinBirleşikbir<xref:System.ServiceModel.Channels.ChannelFactoryBase>temel sınıfsağlar.<xref:System.ServiceModel.Channels.ChannelListenerBase> <xref:System.ServiceModel.Channels.CommunicationObject> Sınıfı ile <xref:System.ServiceModel.Channels.ChannelBase>birlikte çalışarak, uygulayan <xref:System.ServiceModel.Channels.IChannel>bir temel sınıf olan. <xref:System.ServiceModel.Channels.ChannelManagerBase>

- `CreateChannel` <xref:System.ServiceModel.Channels.ChannelManagerBase> Sınıfı,<xref:System.ServiceModel.Channels.IChannelFactory> ve yüklerini tek bir`OnCreateChannel` soyut yöntemde uygular ve birleştirir. <xref:System.ServiceModel.Channels.ChannelFactoryBase>

- <xref:System.ServiceModel.Channels.ChannelListenerBase> Sınıfı uygular<xref:System.ServiceModel.Channels.IChannelListener>. Temel durum yönetiminden çok dikkat edin.

Aşağıdaki tartışma, [aktarıma dayalıdır: UDP](../samples/transport-udp.md) örneği.

## <a name="creating-a-channel-listener"></a>Kanal dinleyicisi oluşturma

Örneğin uyguladığı örnek <xref:System.ServiceModel.Channels.ChannelListenerBase> sınıfından türetiliyor. `UdpChannelListener` Veri birimlerini almak için tek bir UDP yuvası kullanır. Yöntemi `OnOpen` , UDP yuvasını zaman uyumsuz bir döngüde kullanarak verileri alır. Veriler daha sonra ileti kodlama sistemi kullanılarak iletilere dönüştürülür:

```csharp
message = UdpConstants.MessageEncoder.ReadMessage(
  new ArraySegment<byte>(buffer, 0, count),
  bufferManager
);
```

Aynı veri birimi kanalı, bir dizi kaynaktan `UdpChannelListener` gelen iletileri temsil ettiğinden, tek bir dinleyici olur. Tek seferde bu dinleyiciyle ilişkili <xref:System.ServiceModel.Channels.IChannel> en fazla bir etkin bulunur. Örnek, yalnızca <xref:System.ServiceModel.Channels.ChannelListenerBase%601.AcceptChannel%2A> yöntemi tarafından döndürülen bir kanal daha sonra atıldığı takdirde bir tane oluşturur. Bir ileti alındığında, bu Singleton kanalında sıraya alınır.

### <a name="udpinputchannel"></a>UdpInputChannel

`UdpInputChannel` Sınıfı uygular<xref:System.ServiceModel.Channels.IInputChannel>. Bu, `UdpChannelListener`kendi yuvası tarafından doldurulan bir gelen ileti kuyruğundan oluşur. Bu iletiler <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A> yöntemi tarafından kaldırılır.
