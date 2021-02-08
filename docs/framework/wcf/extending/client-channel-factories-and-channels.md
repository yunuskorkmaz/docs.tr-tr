---
description: 'Istemci: kanal fabrikaları ve kanallar hakkında daha fazla bilgi edinin'
title: 'İstemci: Kanal Fabrikaları ve Kanallar'
ms.date: 03/30/2017
ms.assetid: ef245191-fdab-4468-a0da-7c6f25d2110f
ms.openlocfilehash: b61c37743899b8ba74ec18cc84397e4521e7bde7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803041"
---
# <a name="client-channel-factories-and-channels"></a>İstemci: Kanal Fabrikaları ve Kanallar

Bu konuda, kanal fabrikaları ve kanallarının oluşturulması ele alınmaktadır.  
  
## <a name="channel-factories-and-channels"></a>Kanal Fabrikaları ve Kanallar  

 Kanal fabrikaları kanalların oluşturulmasından sorumludur. Kanal fabrikaları tarafından oluşturulan kanallar, ileti göndermek için kullanılır. Bu kanallar, yukarıdaki katmandan ileti alma, gerekli her türlü işlemi gerçekleştirme ve sonra iletiyi aşağıdaki katmana gönderme sorumluluğundadır. Aşağıdaki grafik bu süreci göstermektedir.  
  
 ![İstemci fabrikaları ve kanallar](./media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")  
Kanal fabrikası kanallar oluşturur.  
  
 Kapalı olduğunda, kanal fabrikaları, henüz kapanmamış oluşturdukları kanalları kapatmaktan sorumludur. Bir kanal dinleyicisi kapatıldığında, yalnızca yeni kanalları kabul etmeyi ve mevcut kanalları açık bırakır, böylece ileti almaya devam edebilmek için modelin burada asimetrik olduğunu unutmayın.  
  
 WCF bu işlem için temel sınıf yardımcıları sağlar. (Bu konuda tartışılan kanal Yardımcısı sınıflarının bir diyagramı için bkz. [Kanal modeline genel bakış](channel-model-overview.md).)  
  
- <xref:System.ServiceModel.Channels.CommunicationObject>Sınıfı, <xref:System.ServiceModel.ICommunicationObject> [Kanal geliştirme](developing-channels.md)ve adım 2 ' de açıklanan durum makinesini uygular ve uygular.  
  
- <xref:System.ServiceModel.Channels.ChannelManagerBase>Sınıfı, <xref:System.ServiceModel.Channels.CommunicationObject> ve için Birleşik bir temel sınıf sağlar <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType> . <xref:System.ServiceModel.Channels.ChannelManagerBase>Sınıfı ile birlikte çalışarak <xref:System.ServiceModel.Channels.ChannelBase> , uygulayan bir temel sınıf olan <xref:System.ServiceModel.Channels.IChannel> .
  
- <xref:System.ServiceModel.Channels.ChannelFactoryBase>Sınıfı, <xref:System.ServiceModel.Channels.ChannelManagerBase> ve <xref:System.ServiceModel.Channels.IChannelFactory> `CreateChannel` yüklerini tek bir soyut yöntemde uygular ve birleştirir `OnCreateChannel` .
  
- <xref:System.ServiceModel.Channels.ChannelListenerBase>Sınıfı uygular <xref:System.ServiceModel.Channels.IChannelListener> . Temel durum yönetiminden çok dikkat edin.
  
 Aşağıdaki tartışma, [taşıma: UDP](../samples/transport-udp.md) örneğine dayalıdır.  
  
### <a name="creating-a-channel-factory"></a>Kanal fabrikası oluşturma  

 `UdpChannelFactory`Öğesinden türetilir <xref:System.ServiceModel.Channels.ChannelFactoryBase> . Örnek, <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> ileti kodlayıcının ileti sürümüne erişim sağlamak için geçersiz kılar. Örnek ayrıca <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> <xref:System.ServiceModel.Channels.BufferManager> durum makinesi geçişi sırasında örneğimizi kaldırmak için geçersiz kılar.  
  
#### <a name="the-udp-output-channel"></a>UDP çıkış kanalı  

 `UdpOutputChannel`Uygular <xref:System.ServiceModel.Channels.IOutputChannel> . Oluşturucu bağımsız değişkenleri doğrular ve geçirilen öğesine bağlı olarak bir hedef <xref:System.Net.EndPoint> nesnesi oluşturur <xref:System.ServiceModel.EndpointAddress> .  
  
 Geçersiz kılma, <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> Bu iletiye ileti göndermek için kullanılan bir yuva oluşturur <xref:System.Net.EndPoint> .  
  
 ```csharp
this.socket = new Socket(  
this.remoteEndPoint.AddressFamily,
   SocketType.Dgram,
   ProtocolType.Udp
);  
```  

 Kanal düzgün şekilde kapatılabilir veya düzgün şekilde kapatılabilir. Kanal kapalıysa, yuva kapanır ve temel sınıf yöntemine bir çağrı yapılır `OnClose` . Bu, bir özel durum oluşturursa, `Abort` kanalın temizlendiğinden emin olmak için altyapı çağrılır.  
  
```csharp  
this.socket.Close();  
base.OnClose(timeout);  
```  
  
 `Send()`Ve uygulayın `BeginSend()` / `EndSend()` . Bu, iki ana bölümde kesilir. İlk olarak iletiyi bir bayt dizisine seri hale getirme:  
  
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
