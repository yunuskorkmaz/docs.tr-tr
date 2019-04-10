---
title: İstemci Kanal Düzeyi Programlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3b787719-4e77-4e77-96a6-5b15a11b995a
ms.openlocfilehash: ea56c99d7d122dd20fc217f8ecb2937bcf81bec3
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59324142"
---
# <a name="client-channel-level-programming"></a>İstemci Kanal Düzeyi Programlama
Bu konu, kullanmadan bir Windows Communication Foundation (WCF) istemci uygulaması yazma açıklar <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> sınıf ve onun ilişkili nesne modeli.  
  
## <a name="sending-messages"></a>İleti gönderme  
 İleti göndermek ve almak ve yanıtları işlemek hazır olması için aşağıdaki adımlar gereklidir:  
  
1. Bir bağlama oluşturun.  
  
2. Kanal fabrikası oluşturun.  
  
3. Bir kanal oluşturun.  
  
4. Bir istek gönderir ve yanıtı okuyun.  
  
5. Tüm kanal nesneleri kapatın.  
  
#### <a name="creating-a-binding"></a>Bir bağlama oluşturma  
 Alıcı çalışmasına benzer (bkz [hizmet kanal düzeyi programlama](../../../../docs/framework/wcf/extending/service-channel-level-programming.md)), bir bağlama oluşturarak iletileri başlatır gönderme. Bu örnekte yeni bir oluşturur <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> ve ekler bir <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> alt öğeleri koleksiyonu.  
  
#### <a name="building-a-channelfactory"></a>Bir ChannelFactory oluşturma  
 Oluşturmak yerine bir <xref:System.ServiceModel.Channels.IChannelListener?displayProperty=nameWithType>, bu kez, oluşturduğumuz bir <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> çağırarak <xref:System.ServiceModel.ChannelFactory.CreateFactory%2A?displayProperty=nameWithType> tür parametresi olduğu bağlama üzerinde <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>. Kanal dinleyicileri gelen iletileri beklediği yan yana kullanılırken, kanal fabrikaları bir kanal oluşturmak için iletişim başlatır yan yana kullanılır. Kanal dinleyicileri olduğu gibi kanal fabrikaları ilk kullanılabilmesi için önce açılmalıdır.  
  
#### <a name="creating-a-channel"></a>Bir kanal oluşturma  
 Ardından diyoruz <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> oluşturmak için bir <xref:System.ServiceModel.Channels.IRequestChannel>. Bu çağrı ile oluşturulan yeni kanal kullanarak iletişim kurmak istiyoruz uç nokta adresini alır. Biz bir kanal oluşturduktan sonra açık bir durumuna iletişimi için hazır hale getirmek için üzerindeki diyoruz. Taşıma yapısı, bağlı olarak bu çağrıyı açık bağlantı hedef uç nokta ile başlatabilir veya ağ üzerinde hiç bir şey yapabilirsiniz.  
  
#### <a name="sending-a-request-and-reading-the-reply"></a>Bir isteği gönderme ve yanıt okuma  
 Biz açılan bir kanal oluşturduktan sonra size bir ileti oluşturup isteği gönderme ve geri dönmeniz yanıt için beklemek için kanal istek yöntemi kullanabilirsiniz. Bu yöntem döndürüldüğünde, uç noktanın yanıt neydi kullanıma bulmak için okuyabilecekleri bir yanıt iletisi sahibiz.  
  
#### <a name="closing-objects"></a>Nesnelerini kapatma  
 Kaynakları sızdırılmasını önlemek için şu nesneler artık gerekli olmayan iletişimde kullanılan kapatın.  
  
 Aşağıdaki kod örneği, bir ileti gönderin ve yanıt okumak için kanal fabrikası kullanarak temel bir istemci gösterir.  
  
 [!code-csharp[ChannelProgrammingBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/channelprogrammingbasic/cs/clientprogram.cs#2)]
 [!code-vb[ChannelProgrammingBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelprogrammingbasic/vb/clientprogram.vb#2)]
