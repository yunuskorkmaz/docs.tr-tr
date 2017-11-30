---
title: "İstemci Kanal Düzeyi Programlama"
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
ms.assetid: 3b787719-4e77-4e77-96a6-5b15a11b995a
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a6ffe482c8d04314b79ee5bb7029d2583c56c363
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="client-channel-level-programming"></a>İstemci Kanal Düzeyi Programlama
Bu konuda nasıl yazılacağını açıklar bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] kullanmadan istemci uygulaması <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> sınıfı ve onun ilişkili nesne modeli.  
  
## <a name="sending-messages"></a>İleti gönderme  
 İletileri göndermek ve almak ve yanıtları işlemek hazır olması için aşağıdaki adımlar gereklidir:  
  
1.  Bir bağlama oluşturun.  
  
2.  Kanal fabrikası oluşturun.  
  
3.  Bir kanal oluşturun.  
  
4.  Bir istek gönderin ve yanıt okuyun.  
  
5.  Tüm kanal nesneleri kapatın.  
  
#### <a name="creating-a-binding"></a>Bağlama oluşturma  
 Alıcı çalışmasına benzer (bkz [hizmet kanal düzeyi programlama](../../../../docs/framework/wcf/extending/service-channel-level-programming.md)), bir bağlama oluşturarak iletileri başlatır gönderme. Bu örnekte yeni bir oluşturur <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> ve ekleyen bir <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> , öğeler koleksiyonuna.  
  
#### <a name="building-a-channelfactory"></a>Bir ChannelFactory oluşturma  
 Oluşturmak yerine bir <xref:System.ServiceModel.Channels.IChannelListener?displayProperty=nameWithType>, biz bu oluşturduğunuzda bir <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> çağırarak <xref:System.ServiceModel.ChannelFactory.CreateFactory%2A?displayProperty=nameWithType> tür parametresi olduğu bağlama üzerinde <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>. Kanal dinleyicileri gelen iletiler için bekleyeceği yan yana kullanılırken, kanal fabrikaları bir kanal oluşturmak için iletişim başlatır yan yana kullanılır. Kanal dinleyicileri olduğu gibi kullanılabilmesi için önce kanal fabrikaları öncelikle açılmalıdır.  
  
#### <a name="creating-a-channel"></a>Bir kanal oluşturma  
 Ardından diyoruz <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> oluşturmak için bir <xref:System.ServiceModel.Channels.IRequestChannel>. Bu çağrı ile oluşturulan yeni kanal kullanarak iletişim kurmak istiyoruz uç noktası adresi alır. Bir kanal sahibiz sonra açık bir durumda iletişimi için hazır put dayanarak diyoruz. Taşıma yapısı, bağlı olarak bu çağrıyı açık hedef uç noktası ile bir bağlantı başlatmak veya ağ üzerinde hiç bir şey yapabilirsiniz.  
  
#### <a name="sending-a-request-and-reading-the-reply"></a>Bir istek göndermek ve yanıt okuma  
 Biz açılmış bir kanal olduktan sonra size bir ileti oluşturup isteği göndermek ve geri dönmeniz yanıt için beklemek için kanalın istek yöntemi kullanabilirsiniz. Bu yöntem döndürüldüğünde, biz uç noktanın yanıt neydi çıkışı bulmak için okuyabilecekleri bir yanıt iletisi sunuyoruz.  
  
#### <a name="closing-objects"></a>Nesneleri kapatma  
 Kaynakları sızmasını önlemek için biz artık gerekli olduklarında iletişimde kullanılan nesneleri kapatın.  
  
 Aşağıdaki kod örneği, ileti gönderme ve yanıt okumak için kanal fabrikası kullanarak temel bir istemci gösterir.  
  
 [!code-csharp[ChannelProgrammingBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/channelprogrammingbasic/cs/clientprogram.cs#2)]
 [!code-vb[ChannelProgrammingBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelprogrammingbasic/vb/clientprogram.vb#2)]
