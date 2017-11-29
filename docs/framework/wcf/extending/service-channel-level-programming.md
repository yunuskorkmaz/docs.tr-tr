---
title: "Hizmet Kanal Düzeyi Programlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 8d8dcd85-0a05-4c44-8861-4a0b3b90cca9
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e296cc2d8960280c6af278a79eaeaa3984f07eff
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="service-channel-level-programming"></a>Hizmet Kanal Düzeyi Programlama
Bu konuda nasıl yazılacağını açıklar bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hizmet uygulaması kullanmadan <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> ve onun ilişkili nesne modeli.  
  
## <a name="receiving-messages"></a>İleti alma  
 İletileri almak ve işlemek için hazır olması için aşağıdaki adımlar gereklidir:  
  
1.  Bir bağlama oluşturun.  
  
2.  Bir kanal dinleyicisi oluşturun.  
  
3.  Kanal dinleyicisi açın.  
  
4.  İstek okuyun ve yanıt gönderebilir.  
  
5.  Tüm kanal nesneleri kapatın.  
  
#### <a name="creating-a-binding"></a>Bağlama oluşturma  
 İleti alma ve dinleme ilk adımı, bir bağlama oluşturuyor. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]doğrudan bunlardan birini örneği tarafından kullanılan birkaç yerleşik veya sistem tarafından sağlanan bağlamaları birlikte verilir. Ayrıca, kendi özel bağlama 1 kod yaptığı bir CustomBinding sınıfı örneği tarafından da oluşturabilirsiniz.  
  
 Aşağıdaki kod örneği bir örneğini oluşturur <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> ve ekleyen bir <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> bağlama kanal yığını oluşturmak için kullanılan öğelerinin bir koleksiyonu olan, öğeler koleksiyonuna. Bu örnekte, yalnızca öğe koleksiyonunu sahip olduğundan <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, yalnızca HTTP taşıma kanalı elde edilen kanal yığınına sahiptir.  
  
#### <a name="building-a-channellistener"></a>Bir ChannelListener oluşturma  
 Bir bağlama oluşturduktan sonra sizi arayarak <!--zz<xref:System.ServiceModel.Channels.Binding.BuildChannelListener%601%2A?displayProperty=nameWithType>--> `System.ServiceModel.Channels.Binding.BuildChannelListener` tür parametresi oluşturmak için kanal şekli olduğu kanal dinleyicisi oluşturmak için. Bu örnekte kullanıyoruz <xref:System.ServiceModel.Channels.IReplyChannel?displayProperty=nameWithType> çünkü bir istek/yanıt ileti değişim deseni gelen iletiler için dinleme istiyoruz.  
  
 <xref:System.ServiceModel.Channels.IReplyChannel>istek iletileri ve geri göndererek iletileri yanıt almak için kullanılır. Çağırma <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A?displayProperty=nameWithType> döndüren bir <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>, kullanılabilecek istek iletisi almak ve bir yanıt iletisi geri gönderilecek.  
  
 Dinleyici oluştururken, biz bunu dinlediği, bu durumda ağ adresi geçirmek `http://localhost:8080/channelapp`. Genel olarak, bir veya büyük olasılıkla birden fazla adres düzenleri her taşıma kanalını destekleyen, örneğin, http ve https şemasını HTTP aktarımı destekler.  
  
 Biz de boş geçmesi <xref:System.ServiceModel.Channels.BindingParameterCollection?displayProperty=nameWithType> dinleyicisi oluştururken. Bir bağlayıcı parametre dinleyicisi yerleşik nasıl kontrol parametreleri geçirmek için bir mekanizmadır. Biz boş bir koleksiyon geçirmek için Bizim örneğimizde, biz herhangi bir parametre kullanmıyor.  
  
#### <a name="listening-for-incoming-messages"></a>Gelen iletiler için dinleme  
 Ardından diyoruz <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> dinleyicisi ve kanallar kabul Başlat. Davranışını <xref:System.ServiceModel.Channels.IChannelListener%601.AcceptChannel%2A?displayProperty=nameWithType> taşıma bağlantısı odaklı veya bağlantı daha az olduğuna bağlıdır. Bağlantı yönelimli taşıma için <xref:System.ServiceModel.Channels.IChannelListener%601.AcceptChannel%2A> yeni bir bağlantı isteği hangi noktası bu yeni bağlantı temsil eden yeni bir kanal döndürdüğü adresindeki gelene kadar engeller. HTTP gibi daha az bağlantı taşıma için <xref:System.ServiceModel.Channels.IChannelListener%601.AcceptChannel%2A> hemen bir ve yalnızca Aktarım dinleyiciyi oluşturur kanalı ile döndürür.  
  
 Bu örnekte, uygulayan bir kanal dinleyicisi döndürür <xref:System.ServiceModel.Channels.IReplyChannel>. Almak için bu iletileri kanal biz ilk çağrıda <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> dayanarak bir durumda iletişimi için hazır yerleştirin. Ardından diyoruz <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> bir ileti gelene kadar engellenir.  
  
#### <a name="reading-the-request-and-sending-a-reply"></a>İstek okunurken ve yanıt gönderme  
 Zaman <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> döndüren bir <xref:System.ServiceModel.Channels.RequestContext>, kullanarak alınan ileti almak kendi <xref:System.ServiceModel.Channels.RequestContext.RequestMessage%2A> özelliği. Biz (bir dizedir varsayıyoruz) ileti eylem ve gövde içeriği, yazma.  
  
 Bir yanıt göndermek için istek aldık bu durumda dize verilerini geri geçirme yeni bir yanıt iletisi oluşturuyoruz. Ardından diyoruz <xref:System.ServiceModel.Channels.RequestContext.Reply%2A> yanıt iletisi göndermek için.  
  
#### <a name="closing-objects"></a>Nesneleri kapatma  
 Kaynakları sızmasını önlemek için artık gerekli olduklarında iletişimde kullanılan nesneleri kapatmak çok önemlidir. Bu örnekte, istek iletisi, istek bağlamını, kanal ve dinleyiciyi kapatın.  
  
 Aşağıdaki kod örneği, temel bir hizmet bir kanal dinleyicisi yalnızca bir ileti alır gösterir. Gerçek bir hizmet kanalları kabul tutar ve hizmet çıkar kadar iletileri alma.  
  
 [!code-csharp[ChannelProgrammingBasic#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/channelprogrammingbasic/cs/serviceprogram.cs#1)]
 [!code-vb[ChannelProgrammingBasic#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelprogrammingbasic/vb/serviceprogram.vb#1)]
