---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: oturum gerektiren bir hizmet oluşturma'
title: 'Nasıl yapılır: Oturum Gerektiren Bir Hizmet Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8a7613ef-0df9-47c3-b8dc-47f42cb1fd8b
ms.openlocfilehash: 362aee23437bb7f45af5a265a9d3ef47bf62915c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734470"
---
# <a name="how-to-create-a-service-that-requires-sessions"></a>Nasıl yapılır: Oturum Gerektiren Bir Hizmet Oluşturma

Oturumlar, geri çağrılar, çok duraklı güvenlik ve istemciler ile hizmet örnekleri arasındaki ilişkilendirmeler gibi faydalı özellikleri sağlayan iki veya daha fazla uç nokta arasında paylaşılan bir durum oluşturur. Windows Communication Foundation (WCF) uygulamalarındaki oturumlar hakkında daha fazla bilgi için bkz. [oturumları kullanma](../using-sessions.md).  
  
### <a name="to-specify-that-a-contract-require-its-binding-to-support-sessions"></a>Bir sözleşmenin, oturumları desteklemek için bağlamasını gerektirdiğini belirtmek için  
  
1. En az bir işlemle bir hizmet sözleşmesi oluşturun. Hizmet sözleşmesinin nasıl oluşturulacağı hakkında bir örnek için bkz. [nasıl yapılır: bir hizmet sözleşmesi tanımlama](../how-to-define-a-wcf-service-contract.md).  
  
2. Özelliği şu <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> şekilde ayarlayarak sözleşmeyi bildiren ' i değiştirin <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> :  
  
    - <xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType> Bu sözleşmenin bir oturum içinde çalıştırılması gerekiyorsa.  
  
    - <xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType> Bu sözleşme bir oturum içinde çalıştırılabilirler.  
  
    - <xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType> Bu sözleşmenin bir oturum içinde çalıştırılmamalıdır.  
  
3. Hizmet uç noktanızı oturumları destekleyen bir bağlama kullanacak şekilde yapılandırın. Aşağıdaki yapılandırma örneği, <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> BIR WS ReliableMessaging oturumunu destekleyen öğesinin kullanımını gösterir `-` .  
  
     [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek kod, bir sözleşme düzeyi oturum gereksinimini belirtmeyi ve bağlamakla bu gereksinimi desteklemek için bir yapılandırma dosyası kullanmayı gösterir <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> .  
  
 [!code-csharp[SCA.Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/services.cs#1)]
 [!code-vb[SCA.Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.session/vb/services.vb#1)]
 [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType>
