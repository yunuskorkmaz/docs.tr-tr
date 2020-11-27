---
title: İstemci Kanal Düzeyi Programlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3b787719-4e77-4e77-96a6-5b15a11b995a
ms.openlocfilehash: cf6ee310e034ad7b2e53206e1bdba68007b1a268
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275586"
---
# <a name="client-channel-level-programming"></a>İstemci Kanal Düzeyi Programlama

Bu konuda, <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> sınıfı ve ilişkili nesne modeli kullanılmadan Windows Communication Foundation (WCF) istemci uygulamasının nasıl yazılacağı açıklanmaktadır.  
  
## <a name="sending-messages"></a>Ileti gönderme  

 İletileri göndermeye ve yanıtları almaya ve işlemeye hazırlamak için aşağıdaki adımlar gereklidir:  
  
1. Bağlama oluşturun.  
  
2. Bir kanal fabrikası oluşturun.  
  
3. Kanal oluşturun.  
  
4. İstek gönderin ve yanıtı okuyun.  
  
5. Tüm kanal nesnelerini kapatın.  
  
#### <a name="creating-a-binding"></a>Bağlama oluşturma  

 Alıcı çalışmasına benzer şekilde (bkz. [Service Channel-Level programlama](service-channel-level-programming.md)), gönderme iletileri bir bağlama oluşturarak başlar. Bu örnek, yeni bir oluşturur <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> ve <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> öğesi koleksiyonuna ekler.  
  
#### <a name="building-a-channelfactory"></a>ChannelFactory oluşturma  

 Oluşturma yerine <xref:System.ServiceModel.Channels.IChannelListener?displayProperty=nameWithType> , bu kez, <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> <xref:System.ServiceModel.ChannelFactory.CreateFactory%2A?displayProperty=nameWithType> tür parametresinin bulunduğu bağlamayı çağırarak oluşturuyoruz <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType> . Kanal dinleyicileri gelen iletiler için bekleyen bir tarafında kullanıldığında, kanal fabrikaları bir kanal oluşturma iletişimini Başlatan tarafında kullanılır. Yalnızca Kanal dinleyicileri gibi, kanal fabrikaları kullanılmadan önce açılmalıdır.  
  
#### <a name="creating-a-channel"></a>Kanal oluşturma  

 Daha sonra <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> bir oluşturmak için öğesini çağırıyoruz <xref:System.ServiceModel.Channels.IRequestChannel> . Bu çağrı, oluşturulmakta olan yeni kanalı kullanarak iletişim kurmak istediğimiz bitiş noktasının adresini alır. Kanalımız olduktan sonra, iletişim için hazırlamak üzere açık duruma getirmek için üzerinde aç çağrısı yaptık. Taşımanın yapısına bağlı olarak, bu açmaya yapılan çağrı hedef uç noktayla bir bağlantı başlatabilir veya ağda hiçbir şey yapmaz.  
  
#### <a name="sending-a-request-and-reading-the-reply"></a>Istek gönderme ve yanıtı okuma  

 Açık bir kanaldan karşılaştığımız bir ileti oluşturabilir ve kanalın Istek yöntemini kullanarak isteği gönderebilir ve yanıtın geri gelmesini bekleyebilirsiniz. Bu yöntem döndürüldüğünde, bitiş noktasının yanıtının ne olduğunu öğrenmek için okuyabilmemiz gereken bir yanıt iletisi vardır.  
  
#### <a name="closing-objects"></a>Nesneleri kapatma  

 Sızan kaynakların sızmasını önlemek için, iletişimlerdeki nesneleri artık gerekli olmadıklarında kapattık.  
  
 Aşağıdaki kod örneği, bir ileti göndermek ve yanıtı okumak için kanal fabrikası kullanan temel bir istemciyi gösterir.  
  
 [!code-csharp[ChannelProgrammingBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/channelprogrammingbasic/cs/clientprogram.cs#2)]
 [!code-vb[ChannelProgrammingBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelprogrammingbasic/vb/clientprogram.vb#2)]
