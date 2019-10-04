---
title: 'Hizmet: Kanal dinleyicileri ve kanallar'
ms.date: 03/30/2017
ms.assetid: 8ccbe0e8-7e55-441d-80de-5765f67542fa
ms.openlocfilehash: 4367d844867db7fdad013e30d047f9385addbce5
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834792"
---
# <a name="service-channel-listeners-and-channels"></a>Hizmet: Kanal dinleyicileri ve kanallar

Kanal nesnelerinin üç kategorisi vardır: kanallar, kanal dinleyicileri ve kanal fabrikaları. Kanallar, uygulama ve kanal yığını arasındaki arabirimdir. Kanal dinleyicileri, genellikle yeni bir gelen iletiye veya bağlantıya yanıt olarak alma (veya dinleme) tarafında kanal oluşturmaktan sorumludur. Kanal fabrikaları, bir uç noktayla iletişim başlatmak için gönderme tarafında kanal oluşturmaktan sorumludur.

## <a name="channel-listeners-and-channels"></a>Kanal dinleyicileri ve kanalları

Kanal dinleyicileri, kanalların oluşturulması ve ağ üzerinden veya ağdan ileti almaktan sorumludur. Alınan iletiler, kanal dinleyicisi tarafından oluşturulan bir kanalı kullanarak yukarıdaki katmana dağıtılır.

Aşağıdaki diyagramda ileti alma ve bunları yukarıdaki katmana sunma süreci gösterilmektedir.

![Kanal dinleyicileri ve kanallar](./media/wcfc-wcfchannelsigure1highlevelc.gif "wcfc_WCFChannelsigure1HighLevelc")

Kanallar aracılığıyla iletileri alan ve katmana teslim eden bir kanal dinleyicisi.

Bu işlem, uygulama gerçekten bir kuyruk kullanmayabilir ancak her kanaldaki bir sıra olarak kavramsal olarak modellenebilir. Kanal dinleyicisi, aşağıdaki katmandan veya ağdan ileti almaktan ve bunları sıraya yerleştirmekten sorumludur. Kanal, kuyruktan ileti alma ve bu katman bir ileti istediğinde yukarıdaki katmana teslim etme işleminden sorumludur. Örneğin, kanalda `Receive` ' ı çağırarak.

WCF bu işlem için temel sınıf yardımcıları sağlar. Bu makalede ele alınan kanal Yardımcısı sınıflarının bir diyagramı için bkz. [Kanal modeline genel bakış](channel-model-overview.md).

- @No__t-0 sınıfı <xref:System.ServiceModel.ICommunicationObject> uygular ve [Kanal geliştirmenin](developing-channels.md)2. adımında açıklanan durum makinesini zorlar.

- @No__t-0 sınıfı <xref:System.ServiceModel.Channels.CommunicationObject> uygular ve <xref:System.ServiceModel.Channels.ChannelFactoryBase> ve <xref:System.ServiceModel.Channels.ChannelListenerBase> için Birleşik bir temel sınıf sağlar. @No__t-0 sınıfı, <xref:System.ServiceModel.Channels.IChannel> uygulayan temel bir sınıf olan <xref:System.ServiceModel.Channels.ChannelBase> ile birlikte çalışıyor.

- @No__t-0 sınıfı <xref:System.ServiceModel.Channels.ChannelManagerBase> ' i ve <xref:System.ServiceModel.Channels.IChannelFactory> ' i uygular ve `CreateChannel` yüklerini tek bir @no__t 4 soyut yönteminde birleştirir.

- @No__t-0 sınıfı @no__t uygular-1. Temel durum yönetiminden çok dikkat edin.

Aşağıdaki tartışma, [taşıma: UDP](../samples/transport-udp.md) örneğine dayalıdır.

## <a name="creating-a-channel-listener"></a>Kanal dinleyicisi oluşturma

Örneğin uyguladığı `UdpChannelListener` <xref:System.ServiceModel.Channels.ChannelListenerBase> sınıfından türetilir. Veri birimlerini almak için tek bir UDP yuvası kullanır. @No__t-0 yöntemi, zaman uyumsuz bir döngüde UDP yuvasını kullanarak verileri alır. Veriler daha sonra ileti kodlama sistemi kullanılarak iletilere dönüştürülür:

```csharp
message = UdpConstants.MessageEncoder.ReadMessage(
  new ArraySegment<byte>(buffer, 0, count),
  bufferManager
);
```

Aynı veri birimi kanalı, bir dizi kaynaktan gelen iletileri temsil ettiğinden, `UdpChannelListener` tek bir dinleyici olur. Aynı anda bu dinleyiciyle ilişkili en fazla bir etkin <xref:System.ServiceModel.Channels.IChannel> var. Örnek yalnızca <xref:System.ServiceModel.Channels.ChannelListenerBase%601.AcceptChannel%2A> yöntemi tarafından döndürülen bir kanal daha sonra atıldığı takdirde bir tane oluşturur. Bir ileti alındığında, bu Singleton kanalında sıraya alınır.

### <a name="udpinputchannel"></a>UdpInputChannel

@No__t-0 sınıfı @no__t uygular-1. @No__t-0 ' ın yuvası tarafından doldurulan bir gelen ileti kuyruğundan oluşur. Bu iletiler <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A> yöntemiyle sıraya alınır.
