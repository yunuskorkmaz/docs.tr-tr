---
title: 'Nasıl yapılır: Oturum Gerektiren Bir Hizmet Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8a7613ef-0df9-47c3-b8dc-47f42cb1fd8b
ms.openlocfilehash: 53b6c809103a2a32d544b8317164a5fa3aa81596
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61787640"
---
# <a name="how-to-create-a-service-that-requires-sessions"></a>Nasıl yapılır: Oturum Gerektiren Bir Hizmet Oluşturma
Oturumları, istemcilere hizmet örnekleri arasındaki ilişkilendirmeleri geri çağırmaları ve çok atlamalı güvenlik gibi yararlı özellikleri sağlayan iki veya daha fazla uç noktalar arasında paylaşılan bir durum oluşturur. Windows Communication Foundation (WCF) uygulamalarında oturumları hakkında daha fazla bilgi için bkz. [oturumları kullanarak](../../../../docs/framework/wcf/using-sessions.md).  
  
### <a name="to-specify-that-a-contract-require-its-binding-to-support-sessions"></a>Bir sözleşme bağlamasına oturumları desteklemek gerekli olduğunu belirtmek için  
  
1. Hizmet Sözleşmesi ile en az bir işlem oluşturun. Hizmet sözleşmesi oluşturma örneği için bkz: [nasıl yapılır: Bir hizmet sözleşmesini tanımlama](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).  
  
2. Değiştirme <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> ayarlayarak sözleşme bildiren <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> ya da özelliği:  
  
    - <xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType> Bu sözleşme bir oturumunda çalıştırmanız gerekir  
  
    - <xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType> Bu sözleşme bir oturumda çalıştırabilirsiniz  
  
    - <xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType> Bu sözleşme oturum içindeki çalıştırmamalıdır durumunda.  
  
3. Oturumlarının destekleyen bir bağlama kullanmak için hizmet uç noktasını yapılandırın. Aşağıdaki yapılandırma örnek kullanımını gösterir <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>, bir WS destekleyen`-`ReliableMessaging oturumu.  
  
     [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]   
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği bir sözleşme düzeyi oturumu gereksinim belirtin ve bu gereksinimi desteklemek için bir yapılandırma dosyası kullanma işlemi gösterilmektedir <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> bağlama.  
  
 [!code-csharp[SCA.Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/services.cs#1)] 
 [!code-vb[SCA.Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.session/vb/services.vb#1)]      
 [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]     
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType>
