---
title: 'İstemci: Kanal Fabrikaları ve Kanallar'
ms.date: 03/30/2017
ms.assetid: ef245191-fdab-4468-a0da-7c6f25d2110f
ms.openlocfilehash: bfa5d2478d5c12f16c2d9531de02e1c868eab560
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59166263"
---
# <a name="client-channel-factories-and-channels"></a>İstemci: Kanal Fabrikaları ve Kanallar
Bu konu, kanal fabrikaları ve kanallar oluşturulmasını açıklar.  
  
## <a name="channel-factories-and-channels"></a>Kanal Fabrikaları ve Kanallar  
 Kanal fabrikaları kanallar oluşturmak için sorumludur. Kanal fabrikaları tarafından oluşturulan Kanallar, ileti göndermek için kullanılır. Bu Kanallar, katmandan ileti alma, gerekli işlemleri gerçekleştirip ve ardından katmana ileti gönderilirken sorumludur. Aşağıdaki grafikte, bu işlemi göstermektedir.  
  
 ![İstemci fabrikaları ve kanallar](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")  
Kanal fabrikası kanalı oluşturur.  
  
 Kapatıldığında, kanal fabrikaları henüz kapatılmadı oluşturdukları tüm kanalları kapatma için sorumlu olursunuz. Bir kanal dinleyicisi kapalı olduğunda, yalnızca yeni kanallar ancak iletiler almaya devam edebilmesi için mevcut kanallar açın leaves kabul etme işlemini durdurur olduğundan model burada asimetrik olduğunu unutmayın.  
  
 WCF bu işlem için temel sınıfı Yardımcıları sağlar. (Bu konuda tartışılan kanal yardımcı sınıfları diyagramı için bkz: [kanal modeline genel bakış](../../../../docs/framework/wcf/extending/channel-model-overview.md).)  
  
-   <xref:System.ServiceModel.Channels.CommunicationObject> Sınıfının Implements <xref:System.ServiceModel.ICommunicationObject> ve 2. adımda açıklanan Durum makinesi uygular [geliştirme kanalları](../../../../docs/framework/wcf/extending/developing-channels.md).  
  
-   <xref:System.ServiceModel.Channels.ChannelManagerBase> Sınıfının Implements <xref:System.ServiceModel.Channels.CommunicationObject> ve birleşik bir temel sınıf için <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> ve <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType>. <xref:System.ServiceModel.Channels.ChannelManagerBase> Sınıfı çalışır birlikte <xref:System.ServiceModel.Channels.ChannelBase>, uygulayan bir temel sınıf olan <xref:System.ServiceModel.Channels.IChannel>.
  
-   <xref:System.ServiceModel.Channels.ChannelFactoryBase> Sınıfının Implements <xref:System.ServiceModel.Channels.ChannelManagerBase> ve <xref:System.ServiceModel.Channels.IChannelFactory> ve birleştirir `CreateChannel` aşırı birine `OnCreateChannel` soyut yöntemi.
  
-   <xref:System.ServiceModel.Channels.ChannelListenerBase> Sınıfının Implements <xref:System.ServiceModel.Channels.IChannelListener>. Bu temel durum yönetimini üstlenir. 
  
 Aşağıdaki tartışma temel aldığı [taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örnek.  
  
### <a name="creating-a-channel-factory"></a>Kanal fabrikası oluşturma  
 `UdpChannelFactory` Türetildiği <xref:System.ServiceModel.Channels.ChannelFactoryBase>. Örnek geçersiz kılmalar <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> ileti Kodlayıcı ileti sürümüne erişim sağlamak için. Örnek ayrıca geçersiz kılar <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> bizim örneğini kaldırmak için <xref:System.ServiceModel.Channels.BufferManager> durum makinesinin zaman geçer.  
  
#### <a name="the-udp-output-channel"></a>UDP Çıkış kanalı  
 `UdpOutputChannel` Uygulayan <xref:System.ServiceModel.Channels.IOutputChannel>. Oluşturucu bağımsız değişkenlerini doğrular ve bir hedef oluşturur <xref:System.Net.EndPoint> nesnesini temel alan <xref:System.ServiceModel.EndpointAddress> olarak geçirilir.  
  
 Geçersiz kılmasını <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> için ileti göndermek için kullanılan bir yuva oluşturur <xref:System.Net.EndPoint>.  
  
 ```csharp 
this.socket = new Socket(  
this.remoteEndPoint.AddressFamily,
   SocketType.Dgram,
   ProtocolType.Udp
);  
```  

 Kanal ungracefully ya da düzgün biçimde kapatılabilir. Kanal düzgün bir şekilde kapanırsa yuva kapatıldı ve temel sınıf için bir çağrı yapılır `OnClose` yöntemi. Bu bir özel durum oluşturursa, altyapı çağırır `Abort` kanal emin olmak için temizlenir.  
  
```csharp  
this.socket.Close();  
base.OnClose(timeout);  
```  
  
 Uygulama `Send()` ve `BeginSend()` / `EndSend()`. Bu iki ana bölüme ayırır. İlk iletinin bir bayt dizisine okunamayacak seri hale getirme:  
  
```csharp  
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 Sonra elde edilen veriler kablo gönderin:  
  
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

- [Geliştirme Kanalları](../../../../docs/framework/wcf/extending/developing-channels.md)
