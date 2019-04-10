---
title: Hizmet Kanal Düzeyi Programlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8d8dcd85-0a05-4c44-8861-4a0b3b90cca9
ms.openlocfilehash: be5c73e2ac9fcc45d136280c869148326cd91315
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59329136"
---
# <a name="service-channel-level-programming"></a>Hizmet Kanal Düzeyi Programlama
Bu konu, bir Windows Communication Foundation (WCF) hizmet uygulaması kullanmadan yazma açıklar <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> ve onun ilişkili nesne modeli.  
  
## <a name="receiving-messages"></a>İleti alma  
 İletileri almak ve işlemek hazır olması için aşağıdaki adımlar gereklidir:  
  
1. Bir bağlama oluşturun.  
  
2. Bir kanal dinleyicisi oluşturun.  
  
3. Kanal dinleyicisi açın.  
  
4. İsteği okumak ve bir yanıt gönderir.  
  
5. Tüm kanal nesneleri kapatın.  
  
#### <a name="creating-a-binding"></a>Bir bağlama oluşturma  
 Bir bağlama ilk adımı dinleyen ve iletileri alma oluşturmaktır. WCF, doğrudan bir tanesi örneği tarafından kullanılan birkaç yerleşik veya sistem tarafından sağlanan bağlamaları ile birlikte gelir. Ayrıca, kendi özel bağlama 1 kod yaptığı bir CustomBinding sınıfı örneği tarafından da oluşturabilirsiniz.  
  
 Aşağıdaki kod örneği bir örneğini oluşturur <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> ve ekler bir <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> bağlama kanal yığın oluşturmak için kullanılan öğelerinin bir koleksiyonu, öğeleri koleksiyonu. Bu örnekte, yalnızca öğe koleksiyonunu bulunduğundan <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, yalnızca HTTP taşıma kanalının elde edilen kanal yığın vardır.  
  
#### <a name="building-a-channellistener"></a>Da ChannelListener oluşturmak  
 Diyoruz bağlama oluşturduktan sonra <xref:System.ServiceModel.Channels.Binding.BuildChannelListener%2A?displayProperty=nameWithType> tür parametresi oluşturmak için kanal şekli olduğu kanal dinleyicisi oluşturmak için. Bu örnekte kullanıyoruz <xref:System.ServiceModel.Channels.IReplyChannel?displayProperty=nameWithType> istek/yanıt ileti değişim deseni gelen iletileri dinlemek istediğimizden.  
  
 <xref:System.ServiceModel.Channels.IReplyChannel> istek iletileri ve geri gönderme iletilerini yanıt almak için kullanılır. Çağırma <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A?displayProperty=nameWithType> döndürür bir <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>, kullanılabilir istek iletisi alırsınız ve bir yanıt iletisi geri göndermek için.  
  
 Dinleyici oluştururken, biz bunu dinlediği, bu durumda ağ adresi geçirmek `http://localhost:8080/channelapp`. Genel olarak, her taşıma kanalının bir ya da büyük olasılıkla birden fazla adres düzenleri destekler, örneğin, HTTP aktarımı hem http hem de https şemasını destekler.  
  
 Biz de boş geçmesi <xref:System.ServiceModel.Channels.BindingParameterCollection?displayProperty=nameWithType> dinleyici oluştururken. Bağlama parametresi, dinleyici nasıl oluşturulması gerektiğini denetleyen parametreleri geçirmek için kullanılan bir mekanizmadır. Biz boş bir koleksiyon geçirmek için Bizim örneğimizde, biz herhangi bir parametre kullanmıyor.  
  
#### <a name="listening-for-incoming-messages"></a>Gelen iletiler için dinleme  
 Ardından diyoruz <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> dinleyici ve kanalları kabul Başlat. Davranışını <xref:System.ServiceModel.Channels.IChannelListener%601.AcceptChannel%2A?displayProperty=nameWithType> aktarım bağlantı odaklı veya bağlantı daha az olmasına göre değişir. Bağlantıya dayalı aktarımı için <xref:System.ServiceModel.Channels.IChannelListener%601.AcceptChannel%2A> hangi noktası bu yeni bağlantı temsil eden yeni bir kanal döndürür yeni bir bağlantı isteği geldiğinde kadar engeller. HTTP gibi bağlantı olmayan aktarımlar için <xref:System.ServiceModel.Channels.IChannelListener%601.AcceptChannel%2A> bir ve yalnızca Aktarım dinleyicisi oluşturur kanalı olmadan hemen döndürür.  
  
 Bu örnekte, dinleyici uygulayan bir kanal döndürür <xref:System.ServiceModel.Channels.IReplyChannel>. Almak için bu iletilerin kanal biz ilk çağrı <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> dayanarak bir durumda iletişimi için hazır hale getirin. Ardından diyoruz <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> bir ileti gelirse kadar hangi engeller.  
  
#### <a name="reading-the-request-and-sending-a-reply"></a>İstek okunurken ve yanıt gönderme  
 Zaman <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> döndürür bir <xref:System.ServiceModel.Channels.RequestContext>, alınan iletiyi kullanarak alın, <xref:System.ServiceModel.Channels.RequestContext.RequestMessage%2A> özelliği. Biz (bir dize olduğu varsayılır) ileti eylem ve gövde içeriği yazın.  
  
 Bir yanıt göndermesi için biz istekte aldık Bu örnekte dize verileri geri geçirme yeni bir yanıt iletisi oluşturun. Ardından diyoruz <xref:System.ServiceModel.Channels.RequestContext.Reply%2A> yanıt iletisi.  
  
#### <a name="closing-objects"></a>Nesnelerini kapatma  
 Kaynakları sızdırılmasını önlemek için artık gerekli olmayan iletişimde kullanılan nesneleri kapatmak çok önemlidir. Bu örnekte, istek iletisi, istek bağlamını, kanal ve dinleyici kapatın.  
  
 Aşağıdaki kod örneği, temel bir hizmet bir kanal dinleyicisi yalnızca bir ileti aldığı gösterilmektedir. Gerçek bir hizmet kanalları kabul ve hizmet çıkana kadar iletilerini alma tutar.  
  
 [!code-csharp[ChannelProgrammingBasic#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/channelprogrammingbasic/cs/serviceprogram.cs#1)]
 [!code-vb[ChannelProgrammingBasic#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelprogrammingbasic/vb/serviceprogram.vb#1)]
