---
title: "İstemci: Kanal Fabrikaları ve Kanallar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef245191-fdab-4468-a0da-7c6f25d2110f
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 82e42a3dd4fbb29970b8e1a17333b66d85d2887b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="client-channel-factories-and-channels"></a>İstemci: Kanal Fabrikaları ve Kanallar
Bu konu, kanal fabrikaları ve kanallar oluşturulmasını açıklar.  
  
## <a name="channel-factories-and-channels"></a>Kanal fabrikaları ve kanallar  
 Kanal fabrikaları kanalları oluşturmaktan sorumlu. Kanal üreteçleri tarafından oluşturulan kanallar ileti göndermek için kullanılır. Katmandan ileti alma, gerekli işlemleri gerçekleştirip sonra katmana ileti göndermek için bu kanalları sorumludur. Aşağıdaki grafikte bu işlemi gösterilmektedir.  
  
 ![İstemci fabrikaları ve kanallar](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")  
Kanal fabrikası kanalları oluşturur.  
  
 Kapatıldığında, henüz kapatılmamış oluşturuldukları kanalları kapatma kanal fabrikaları sorumludur. Bir kanal dinleyicisi kapatıldığında, yalnızca yeni kanallar ancak iletileri almaya devam edebilmesi için varolan kanalları açmak bırakır kabul durdurduğu olduğundan model burada asimetrik olduğunu unutmayın.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Bu işlem için temel sınıfı Yardımcıları sağlar. (Bu konuda tartışılan kanal yardımcı sınıfları diyagramı için bkz: [kanal modeli genel bakış](../../../../docs/framework/wcf/extending/channel-model-overview.md).)  
  
-   <xref:System.ServiceModel.Channels.CommunicationObject> Uygulayan sınıf <xref:System.ServiceModel.ICommunicationObject> ve 2. adımda açıklanan durum makinesinin zorlar [geliştirme kanalları](../../../../docs/framework/wcf/extending/developing-channels.md).  
  
-   ''<xref:System.ServiceModel.Channels.ChannelManagerBase> Uygulayan sınıf <xref:System.ServiceModel.Channels.CommunicationObject> ve birleştirilmiş bir temel sınıf sağlar <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> ve <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType>. <xref:System.ServiceModel.Channels.ChannelManagerBase> Sınıfı çalışır birlikte <xref:System.ServiceModel.Channels.ChannelBase>, uygulayan bir temel sınıfı olan <xref:System.ServiceModel.Channels.IChannel>.  
  
-   ''<xref:System.ServiceModel.Channels.ChannelFactoryBase> Uygulayan sınıf <xref:System.ServiceModel.Channels.ChannelManagerBase> ve <xref:System.ServiceModel.Channels.IChannelFactory> ve birleştirir `CreateChannel` overloads birine `OnCreateChannel` soyut yöntemi.  
  
-   ''<xref:System.ServiceModel.Channels.ChannelListenerBase> Uygulayan sınıf <xref:System.ServiceModel.Channels.IChannelListener>. Bu temel durum yönetimini mvc'deki.  
  
 Aşağıdaki tartışma temel aldığı [taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örnek.  
  
### <a name="creating-a-channel-factory"></a>Kanal fabrikası oluşturma  
 `UdpChannelFactory` Türetilen <xref:System.ServiceModel.Channels.ChannelFactoryBase>. Örnek geçersiz kılmaları <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> ileti Kodlayıcı ileti sürümü erişim sağlamak için. Örnek ayrıca geçersiz kılar <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> bizim örneğini kesmeden <xref:System.ServiceModel.Channels.BufferManager> zaman durum makinesinin geçer.  
  
#### <a name="the-udp-output-channel"></a>UDP çıktı kanalı  
 `UdpOutputChannel` Uygulayan <xref:System.ServiceModel.Channels.IOutputChannel>. Oluşturucu bağımsız değişkenleri doğrular ve bir hedef oluşturur <xref:System.Net.EndPoint> nesne temel alarak <xref:System.ServiceModel.EndpointAddress> olarak geçirilir.  
  
 Geçersiz kılma <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> için ileti göndermek için kullanılan bir yuva oluşturur <xref:System.Net.EndPoint>.  
  
 `this.socket = new Socket(`  
  
 `this.remoteEndPoint.AddressFamily,`  
  
 `SocketType.Dgram,`  
  
 `ProtocolType.Udp`  
  
 `);`  
  
 Kanal düzgün biçimde veya ungracefully kapatılabilir. Kanal düzgün biçimde kapalıysa yuva kapatılır ve taban sınıfı için bir çağrı yapılır `OnClose` yöntemi. Bu bir özel durum oluşturursa, altyapı çağırır `Abort` kanal emin olmak için temizlendi.  
  
```  
this.socket.Close();  
base.OnClose(timeout);  
```  
  
 Uygulama `Send()` ve `BeginSend()` / `EndSend()`. Bu iki ana bölüme parçalara ayırır. İlk iletinin bir bayt dizisine sıralayın:  
  
```  
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 Ardından kablo sonuç verileri gönder:  
  
```  
this.socket.SendTo(  
  messageBuffer.Array,   
  messageBuffer.Offset,   
  messageBuffer.Count,   
  SocketFlags.None,   
  this.remoteEndPoint  
);  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Geliştirme Kanalları](../../../../docs/framework/wcf/extending/developing-channels.md)
