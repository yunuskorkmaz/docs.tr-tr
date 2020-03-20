---
title: 'İstemci: Kanal Fabrikaları ve Kanallar'
ms.date: 03/30/2017
ms.assetid: ef245191-fdab-4468-a0da-7c6f25d2110f
ms.openlocfilehash: 25e2c034d1fefc7728667231040a97c3aeecabbd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185688"
---
# <a name="client-channel-factories-and-channels"></a>İstemci: Kanal Fabrikaları ve Kanallar
Bu konu kanal fabrikaları ve kanalların oluşturulması nı tartışır.  
  
## <a name="channel-factories-and-channels"></a>Kanal Fabrikaları ve Kanallar  
 Kanal fabrikaları kanal oluşturmaktan sorumludur. Kanal fabrikaları tarafından oluşturulan kanallar ileti göndermek için kullanılır. Bu kanallar, yukarıdaki katmandan iletiyi almak, gerekli olan işlemleri gerçekleştirmek ve ardından mesajı aşağıdaki katmana göndermekten sorumludur. Aşağıdaki grafik bu işlemi göstermektedir.  
  
 ![Müşteri Fabrikaları ve Kanalları](./media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")  
Kanal fabrikası kanallar oluşturur.  
  
 Kapandığında, kanal fabrikaları oluşturmuşve henüz kapatılmayan kanalların kapatılmasından sorumludur. Bir kanal dinleyicisi kapatıldığında, yalnızca yeni kanalları kabul etmeyi durdurur, ancak ileti almaya devam edebilmeleri için varolan kanalları açık bırakır, çünkü modelin burada asimetrik olduğunu unutmayın.  
  
 WCF bu işlem için taban sınıf yardımcıları sağlar. (Bu konuda tartışılan kanal yardımcı sınıflarının diyagramı için [Kanal Modeline Genel Bakış](channel-model-overview.md)bölümüne bakın.)  
  
- Sınıf, <xref:System.ServiceModel.Channels.CommunicationObject> <xref:System.ServiceModel.ICommunicationObject> [Gelişen Kanallar'ın](developing-channels.md)2.  
  
- Sınıf <xref:System.ServiceModel.Channels.ChannelManagerBase> uygular <xref:System.ServiceModel.Channels.CommunicationObject> ve birleşik bir taban <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType>sınıfı sağlar ve. Sınıf, <xref:System.ServiceModel.Channels.ChannelManagerBase> uygulayan bir <xref:System.ServiceModel.Channels.ChannelBase>taban sınıf olan ile <xref:System.ServiceModel.Channels.IChannel>birlikte çalışır.
  
- Sınıf, <xref:System.ServiceModel.Channels.ChannelFactoryBase> <xref:System.ServiceModel.Channels.ChannelManagerBase> <xref:System.ServiceModel.Channels.IChannelFactory> `CreateChannel` aşırı yüklemeleri tek bir `OnCreateChannel` soyut yöntemde uygular ve birleştirir.
  
- Sınıf <xref:System.ServiceModel.Channels.ChannelListenerBase> uygular. <xref:System.ServiceModel.Channels.IChannelListener> Temel devlet yönetimini hallediyor.
  
 Aşağıdaki tartışma [Transport: UDP](../samples/transport-udp.md) örneğine dayanmaktadır.  
  
### <a name="creating-a-channel-factory"></a>Kanal Fabrikası Oluşturma  
 <xref:System.ServiceModel.Channels.ChannelFactoryBase>Türetilmiştir. `UdpChannelFactory` Örnek, ileti <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> kodlayıcısının ileti sürümüne erişim sağlamak için geçersiz kılar. Örnek aynı zamanda <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> durum makine <xref:System.ServiceModel.Channels.BufferManager> geçişleri bizim örnek yıkmak için geçersiz kılar.  
  
#### <a name="the-udp-output-channel"></a>UDP Çıkış Kanalı  
 Uygular `UdpOutputChannel` <xref:System.ServiceModel.Channels.IOutputChannel>. Oluşturucu bağımsız değişkenleri doğrular ve <xref:System.Net.EndPoint> geçirilene <xref:System.ServiceModel.EndpointAddress> göre bir hedef nesnesi inşa eder.  
  
 Geçersiz kılma, <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> bu <xref:System.Net.EndPoint>ileti göndermek için kullanılan bir soket oluşturur.  
  
 ```csharp
this.socket = new Socket(  
this.remoteEndPoint.AddressFamily,
   SocketType.Dgram,
   ProtocolType.Udp
);  
```  

 Kanal zarif veya zarif bir şekilde kapatılabilir. Kanal incelikle kapatılırsa soket kapatılır ve taban sınıf `OnClose` yöntemine çağrı yapılır. Bu bir özel durum oluşturursa, altyapı kanalının temizlenmesini sağlamak için çağırır. `Abort`  
  
```csharp  
this.socket.Close();  
base.OnClose(timeout);  
```  
  
 Uygula `Send()` `BeginSend()` / `EndSend()`ve . Bu iki ana bölüme ayrılır. Önce iletiyi bayt dizilimi halinde serihale getirin:  
  
```csharp  
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 Ardından, elde edilen verileri kabloya gönderin:  
  
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
