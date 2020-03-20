---
title: 'Nasıl yapılır: Oturum Gerektiren Bir Hizmet Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8a7613ef-0df9-47c3-b8dc-47f42cb1fd8b
ms.openlocfilehash: 495de5a926cfc0c5aab88337f5f33b991c49e71a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184983"
---
# <a name="how-to-create-a-service-that-requires-sessions"></a>Nasıl yapılır: Oturum Gerektiren Bir Hizmet Oluşturma
Oturumlar, geri aramalar, çoklu atlama güvenliği ve istemciler ve hizmet örnekleri arasındaki ilişkilendirmeler gibi yararlı özellikleri etkinleştiren iki veya daha fazla uç nokta arasında paylaşılan bir durum oluşturur. Windows Communication Foundation (WCF) uygulamalarındaki oturumlar hakkında daha fazla bilgi için, [Bkz. Oturumları Kullanma.](../../../../docs/framework/wcf/using-sessions.md)  
  
### <a name="to-specify-that-a-contract-require-its-binding-to-support-sessions"></a>Bir sözleşmenin oturumları desteklemek için bağlanmasını gerektirdiğini belirtmek için  
  
1. En az bir işlemle bir hizmet sözleşmesi oluşturun. Hizmet sözleşmesi oluşturma nın bir örneği için [bkz.](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)  
  
2. <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> Özelliği aşağıdakilerden biri için ayarlayarak sözleşmeyi bildiren ibareyi değiştirin: <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType>  
  
    - <xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType>bu sözleşmenin bir oturum içinde çalıştırılması gerekiyorsa.  
  
    - <xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType>bu sözleşme bir oturum içinde çalıştırılabilirse.  
  
    - <xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType>bu sözleşme nin bir oturum içinde çalıştırılmaması gerekiyorsa.  
  
3. Hizmet bitiş noktanızı oturumları destekleyen bir bağlama kullanacak şekilde yapılandırın. Aşağıdaki yapılandırma <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>örneği, WS`-`ReliableMessaging oturumunu destekleyen ,  
  
     [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kod, sözleşme düzeyinde oturum gereksiniminin nasıl belirtilen ve <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> bu gereksinimi bağlamayla desteklemek için bir yapılandırma dosyasının nasıl kullanılacağını gösterir.  
  
 [!code-csharp[SCA.Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/services.cs#1)]
 [!code-vb[SCA.Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.session/vb/services.vb#1)]
 [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType>
