---
title: 'Hizmet: Kanal Dinleyicileri ve Kanallar'
ms.date: 03/30/2017
ms.assetid: 8ccbe0e8-7e55-441d-80de-5765f67542fa
ms.openlocfilehash: eca7061243fa7f006079d19c3eaaf86ba906bca2
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809657"
---
# <a name="service-channel-listeners-and-channels"></a>Hizmet: Kanal Dinleyicileri ve Kanallar
Kanal nesneleri üç kategorisi vardır: kanalları, kanal dinleyicileri ve kanal fabrikaları. Kanallar uygulama ve kanal yığını arasındaki arabirim olan. Kanal dinleyicileri alma (veya dinleme) tarafında, genellikle yeni gelen ileti veya bağlantısı yanıtında kanalları oluşturmaktan sorumlu. Kanal fabrikaları bir uç nokta ile iletişim başlatmasını gönderme tarafında kanalları oluşturmaktan sorumlu.  
  
## <a name="channel-listeners-and-channels"></a>Kanal dinleyicileri ve kanallar  
 Kanal dinleyicileri oluşturma kanalları ve alıcı iletileri katmandan veya ağdan sorumludur. Alınan iletilerin kanal dinleyicisi tarafından oluşturulan bir kanalı kullanılarak yukarıda katman teslim edilir.  
  
 Aşağıdaki diyagramda ileti alma ve yukarıdaki katmana ileterek işlemi gösterilmektedir.  
  
 ![Kanal dinleyicileri ve kanallar](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigure1highlevelc.gif "wcfc_WCFChannelsigure1HighLevelc")  
İleti alma ve katmana kanalları üzerinden ileterek kanal dinleyicisi.  
  
 Uygulama bir sıra gerçekte kullanamazsınız olsa da her kanal içinde bir sıra olarak kavramsal olarak işlem modellenebilir. Kanal dinleyicisi katmandan alıcı iletileri veya ağ ve sıraya koyma sorumludur. Kanal sıradan ileti alma ve bunları ne zaman katman soran bir ileti için örneğin çağırarak yukarıda katmana gönderdikten sorumludur `Receive` kanalda.  
  
 WCF bu işlem için temel sınıfı Yardımcıları sağlar. (Bu konuda tartışılan kanal yardımcı sınıfları diyagramı için bkz: [kanal modeli genel bakış](../../../../docs/framework/wcf/extending/channel-model-overview.md).)  
  
-   <xref:System.ServiceModel.Channels.CommunicationObject> Uygulayan sınıf <xref:System.ServiceModel.ICommunicationObject> ve 2. adımda açıklanan durum makinesinin zorlar [geliştirme kanalları](../../../../docs/framework/wcf/extending/developing-channels.md).  
  
-   <xref:System.ServiceModel.Channels.ChannelManagerBase> Uygulayan sınıf <xref:System.ServiceModel.Channels.CommunicationObject> ve birleştirilmiş bir temel sınıf sağlar <xref:System.ServiceModel.Channels.ChannelFactoryBase> ve <xref:System.ServiceModel.Channels.ChannelListenerBase>. <xref:System.ServiceModel.Channels.ChannelManagerBase> Sınıfı çalışır birlikte <xref:System.ServiceModel.Channels.ChannelBase>, uygulayan bir temel sınıfı olan <xref:System.ServiceModel.Channels.IChannel>.  
  
-   ''<xref:System.ServiceModel.Channels.ChannelFactoryBase> Uygulayan sınıf <xref:System.ServiceModel.Channels.ChannelManagerBase> ve <xref:System.ServiceModel.Channels.IChannelFactory> ve birleştirir `CreateChannel` overloads birine `OnCreateChannel` soyut yöntemi.  
  
-   <xref:System.ServiceModel.Channels.ChannelListenerBase> Uygulayan sınıf <xref:System.ServiceModel.Channels.IChannelListener>. Bu temel durum yönetimini mvc'deki.  
  
 Aşağıdaki tartışma temel aldığı [taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örnek.  
  
## <a name="creating-a-channel-listener"></a>Bir kanal dinleyicisi oluşturma  
 '' Örnek uygulayan UdpChannelListener türer <xref:System.ServiceModel.Channels.ChannelListenerBase> sınıfı. Veri birimleri almak için tek bir UDP yuva kullanır. `OnOpen` Yöntemi zaman uyumsuz bir döngü UDP yuvaya kullanarak verileri alır. Veri sonra sistem kodlama iletiyi kullanarak iletilere dönüştürülür:  
  
```  
message = UdpConstants.MessageEncoder.ReadMessage(  
  new ArraySegment<byte>(buffer, 0, count),   
  bufferManager  
);  
```  
  
 Bir dizi kaynaktan, gelen iletileri aynı veri birimi kanal olabilmesinden dolayı `UdpChannelListener` bir singleton dinleyicisi. Çoğu bir etkin olduğundan <xref:System.ServiceModel.Channels.IChannel>'' aynı anda bu dinleyicisi ile ilişkilendirilmiş. Tarafından döndürülen bir kanal, başka bir örnek oluşturur <xref:System.ServiceModel.Channels.ChannelListenerBase%601.AcceptChannel%2A> yöntemi sonradan atıldı. Bir ileti alındığında, sıraya alınan bu singleton kanal içine var.  
  
### <a name="udpinputchannel"></a>UdpInputChannel  
 `UdpInputChannel` Uygulayan sınıf <xref:System.ServiceModel.Channels.IInputChannel>. Tarafından doldurulur gelen iletileri kuyruğunu oluşan `UdpChannelListener`kullanıcının yuva. Tarafından bu iletilerin kuyruktan çıkarıldı <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A> yöntemi.
