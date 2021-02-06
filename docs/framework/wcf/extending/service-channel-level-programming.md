---
description: 'Daha fazla bilgi edinin: Service Channel-Level programlama'
title: Hizmet Kanal Düzeyi Programlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8d8dcd85-0a05-4c44-8861-4a0b3b90cca9
ms.openlocfilehash: 9d89b073430ccdf80bdcbdfc50fd1e002fc807ff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99644072"
---
# <a name="service-channel-level-programming"></a>Hizmet Kanal Düzeyi Programlama

Bu konuda, <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> ve ilişkili nesne modeli kullanılmadan Windows Communication Foundation (WCF) hizmet uygulamasının nasıl yazılacağı açıklanmaktadır.  
  
## <a name="receiving-messages"></a>Iletileri alma  

 İletileri almaya ve işlemeye hazırlamak için aşağıdaki adımlar gereklidir:  
  
1. Bağlama oluşturun.  
  
2. Kanal dinleyicisi oluşturun.  
  
3. Kanal dinleyicisini açın.  
  
4. İsteği okuyun ve yanıt gönderin.  
  
5. Tüm kanal nesnelerini kapatın.  
  
#### <a name="creating-a-binding"></a>Bağlama oluşturma  

 İletileri dinlemek ve almak için ilk adım bir bağlama oluşturmaktır. WCF, bunlardan birini örnekleyerek doğrudan kullanılabilecek çeşitli yerleşik veya sistem tarafından sağlanmış bağlamalarla birlikte gelir. Ayrıca, liste 1 ' deki kodun yaptığı CustomBinding sınıfını örnekleyerek kendi özel bağlamalarınızı oluşturabilirsiniz.  
  
 Aşağıdaki kod örneği, bir örneğini oluşturur <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> ve, <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> Kanal yığınını oluşturmak için kullanılan bağlama öğelerinin bir koleksiyonu olan öğeleri koleksiyonunu ekler. Bu örnekte, öğeler koleksiyonu yalnızca öğesine sahip olduğundan <xref:System.ServiceModel.Channels.HttpTransportBindingElement> , ortaya çıkan kanal yığınında yalnızca HTTP aktarım kanalı vardır.  
  
#### <a name="building-a-channellistener"></a>ChannelListener oluşturma  

 Bağlama oluşturduktan sonra, <xref:System.ServiceModel.Channels.Binding.BuildChannelListener%2A?displayProperty=nameWithType> tür parametresinin oluşturulacak Kanal şekli olduğu kanal dinleyicisini oluşturmak için çağrı yaptık. Bu örnekte, <xref:System.ServiceModel.Channels.IReplyChannel?displayProperty=nameWithType> bir istek/yanıt iletisi değişimi düzeninde gelen iletileri dinlemek istiyoruz.  
  
 <xref:System.ServiceModel.Channels.IReplyChannel> İstek iletilerinin alınması ve yanıt iletilerinin geri gönderilmesi için kullanılır. Çağırma <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A?displayProperty=nameWithType> <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType> , istek iletisini almak ve bir yanıt iletisini geri göndermek için kullanılabilen bir döndürür.  
  
 Dinleyiciyi oluştururken, dinlediği ağ adresini bu durumda geçiyoruz `http://localhost:8080/channelapp` . Genellikle, her bir aktarım kanalı bir veya muhtemelen birkaç adres düzenini destekler, örneğin, HTTP taşıması hem http hem de https düzenlerini destekler.  
  
 Dinleyici oluştururken de boş geçiririz <xref:System.ServiceModel.Channels.BindingParameterCollection?displayProperty=nameWithType> . Bağlama parametresi, dinleyicinin nasıl oluşturulması gerektiğini denetleyen parametreleri geçirmek için kullanılan bir mekanizmadır. Bizim örneğimizde, boş bir koleksiyon geçirdiğimiz için bu tür parametreleri kullanmıyoruz.  
  
#### <a name="listening-for-incoming-messages"></a>Gelen Iletileri dinleme  

 Sonra dinleyiciyi çağırıp <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> kanalları kabul etmeye başladık. Davranışı, <xref:System.ServiceModel.Channels.IChannelListener%601.AcceptChannel%2A?displayProperty=nameWithType> taşımanın bağlantıya dayalı veya bağlantı gibi olmasına bağlıdır. Bağlantı odaklı aktarımlar için, yeni <xref:System.ServiceModel.Channels.IChannelListener%601.AcceptChannel%2A> bir bağlantı isteğinin bu yeni bağlantıyı temsil eden yeni bir kanal döndürdüğü noktaya kadar engeller. HTTP gibi bağlantı açısından daha az ulaşım için, <xref:System.ServiceModel.Channels.IChannelListener%601.AcceptChannel%2A> Aktarım dinleyicisinin oluşturduğu tek ve tek bir kanalla hemen geri döner.  
  
 Bu örnekte, dinleyici uygulayan bir kanal döndürür <xref:System.ServiceModel.Channels.IReplyChannel> . Bu kanala ileti almak için ilk <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> olarak onu iletişim için hazırlamış bir duruma getirmek üzere çağırdık. Ardından, <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> bir ileti alınana kadar hangi blokları çağıracağız.  
  
#### <a name="reading-the-request-and-sending-a-reply"></a>Isteği okuma ve yanıt gönderme  

 <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A>Bir döndürdüğünde <xref:System.ServiceModel.Channels.RequestContext> , aldığı iletiyi özelliğini kullanarak aldık <xref:System.ServiceModel.Channels.RequestContext.RequestMessage%2A> . İletinin eylemini ve gövde içeriğini (bir dize olduğunu varsayıyoruz) yazdık.  
  
 Yanıt göndermek için, istekte aldığımız dize verilerini geri geçirerek bu durumda yeni bir yanıt iletisi oluşturacağız. Ardından <xref:System.ServiceModel.Channels.RequestContext.Reply%2A> yanıt iletisini göndermek için çağrı yaptık.  
  
#### <a name="closing-objects"></a>Nesneleri kapatma  

 Kaynak sızıntısına engel olmak için, artık gerekli olmadıklarında iletişimlerde kullanılan nesneleri kapatmak çok önemlidir. Bu örnekte istek iletisini, istek bağlamını, kanalı ve dinleyiciyi kapattık.  
  
 Aşağıdaki kod örneğinde, bir kanal dinleyicisinin yalnızca bir ileti aldığı temel bir hizmet gösterilmektedir. Gerçek bir hizmet, kanalları kabul eder ve hizmet çıkana kadar ileti alıyor.  
  
 [!code-csharp[ChannelProgrammingBasic#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/channelprogrammingbasic/cs/serviceprogram.cs#1)]
 [!code-vb[ChannelProgrammingBasic#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelprogrammingbasic/vb/serviceprogram.vb#1)]
