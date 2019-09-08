---
title: 'İstemci: Kanal Fabrikaları ve Kanallar'
ms.date: 03/30/2017
ms.assetid: ef245191-fdab-4468-a0da-7c6f25d2110f
ms.openlocfilehash: 3dfcca0d5492a3fa376ec184f4bdd9bfa03b53c0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795867"
---
# <a name="client-channel-factories-and-channels"></a>İstemci: Kanal Fabrikaları ve Kanallar
Bu konuda, kanal fabrikaları ve kanallarının oluşturulması ele alınmaktadır.  
  
## <a name="channel-factories-and-channels"></a>Kanal Fabrikaları ve Kanallar  
 Kanal fabrikaları kanalların oluşturulmasından sorumludur. Kanal fabrikaları tarafından oluşturulan kanallar, ileti göndermek için kullanılır. Bu kanallar, yukarıdaki katmandan ileti alma, gerekli her türlü işlemi gerçekleştirme ve sonra iletiyi aşağıdaki katmana gönderme sorumluluğundadır. Aşağıdaki grafik bu süreci göstermektedir.  
  
 ![Istemci fabrikaları ve kanallar](./media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")  
Kanal fabrikası kanallar oluşturur.  
  
 Kapalı olduğunda, kanal fabrikaları, henüz kapanmamış oluşturdukları kanalları kapatmaktan sorumludur. Bir kanal dinleyicisi kapatıldığında, yalnızca yeni kanalları kabul etmeyi ve mevcut kanalları açık bırakır, böylece ileti almaya devam edebilmek için modelin burada asimetrik olduğunu unutmayın.  
  
 WCF bu işlem için temel sınıf yardımcıları sağlar. (Bu konuda tartışılan kanal Yardımcısı sınıflarının bir diyagramı için bkz. [Kanal modeline genel bakış](channel-model-overview.md).)  
  
- Sınıfı, [Kanal geliştirme](developing-channels.md)ve adım 2 ' de açıklanan durum makinesini uygular <xref:System.ServiceModel.ICommunicationObject> ve uygular. <xref:System.ServiceModel.Channels.CommunicationObject>  
  
- Sınıfı, <xref:System.ServiceModel.Channels.ChannelManagerBase>ve içinBirleşikbir<xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType>temel sınıfsağlar.<xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType> <xref:System.ServiceModel.Channels.CommunicationObject> Sınıfı ile <xref:System.ServiceModel.Channels.ChannelBase>birlikte çalışarak, uygulayan <xref:System.ServiceModel.Channels.IChannel>bir temel sınıf olan. <xref:System.ServiceModel.Channels.ChannelManagerBase>
  
- `CreateChannel` <xref:System.ServiceModel.Channels.ChannelManagerBase> Sınıfı,<xref:System.ServiceModel.Channels.IChannelFactory> ve yüklerini tek bir`OnCreateChannel` soyut yöntemde uygular ve birleştirir. <xref:System.ServiceModel.Channels.ChannelFactoryBase>
  
- <xref:System.ServiceModel.Channels.ChannelListenerBase> Sınıfı uygular<xref:System.ServiceModel.Channels.IChannelListener>. Temel durum yönetiminden çok dikkat edin. 
  
 Aşağıdaki tartışma, [aktarıma dayalıdır: UDP](../samples/transport-udp.md) örneği.  
  
### <a name="creating-a-channel-factory"></a>Kanal fabrikası oluşturma  
 `UdpChannelFactory` Öğesinden<xref:System.ServiceModel.Channels.ChannelFactoryBase>türetilir. Örnek, ileti <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> kodlayıcının ileti sürümüne erişim sağlamak için geçersiz kılar. Örnek ayrıca durum makinesi <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> geçişi <xref:System.ServiceModel.Channels.BufferManager> sırasında örneğimizi kaldırmak için geçersiz kılar.  
  
#### <a name="the-udp-output-channel"></a>UDP çıkış kanalı  
 `UdpOutputChannel` Uygular .<xref:System.ServiceModel.Channels.IOutputChannel> Oluşturucu bağımsız değişkenleri doğrular ve geçirilen öğesine bağlı <xref:System.Net.EndPoint> <xref:System.ServiceModel.EndpointAddress> olarak bir hedef nesnesi oluşturur.  
  
 Geçersiz kılma <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> , bu <xref:System.Net.EndPoint>iletiye ileti göndermek için kullanılan bir yuva oluşturur.  
  
 ```csharp 
this.socket = new Socket(  
this.remoteEndPoint.AddressFamily,
   SocketType.Dgram,
   ProtocolType.Udp
);  
```  

 Kanal düzgün şekilde kapatılabilir veya düzgün şekilde kapatılabilir. Kanal kapalıysa, yuva kapanır ve temel sınıf `OnClose` yöntemine bir çağrı yapılır. Bu, bir özel durum oluşturursa, kanalın temizlendiğinden `Abort` emin olmak için altyapı çağrılır.  
  
```csharp  
this.socket.Close();  
base.OnClose(timeout);  
```  
  
 Ve `Send()` `BeginSend()` uygulayın./ `EndSend()` Bu, iki ana bölümde kesilir. İlk olarak iletiyi bir bayt dizisine seri hale getirme:  
  
```csharp  
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 Sonra elde edilen verileri tel gönderin:  
  
```csharp  
this.socket.SendTo(  
  messageBuffer.Array,   
  messageBuffer.Offset,   
  messageBuffer.Count,   
  SocketFlags.None,   
  this.remoteEndPoint  
);  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Geliştirme Kanalları](developing-channels.md)
