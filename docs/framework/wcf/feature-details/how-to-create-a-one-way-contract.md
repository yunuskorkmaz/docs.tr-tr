---
title: 'Nasıl yapılır: Tek Yönlü Sözleşme Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 85084cd9-31cc-4e95-b667-42ef01336622
ms.openlocfilehash: 42c056c9b56ed1245290cd66833cc6565f517b66
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593457"
---
# <a name="how-to-create-a-one-way-contract"></a>Nasıl yapılır: Tek Yönlü Sözleşme Oluşturma
Bu konuda tek yönlü bir sözleşme kullanan Yöntemler oluşturmak için temel adımlar gösterilmektedir. Bu tür yöntemler bir istemciden Windows Communication Foundation (WCF) hizmetinde işlemleri çağırır ancak yanıt beklemez. Bu tür bir sözleşme, örneğin, birçok aboneye bildirim yayımlamak için kullanılabilir. Ayrıca, bir çift yönlü (çift yönlü) sözleşme oluştururken, istemcilerin ve sunucuların birbirleriyle yapılan çağrıları başlatabilmeleri için birbirinden bağımsız olarak birbirleriyle iletişim kurmasına olanak sağlayan tek yönlü sözleşmeleri de kullanabilirsiniz. Bu, özellikle sunucunun istemci için istemcinin olay olarak kabul edebilir tek yönlü çağrılar yapmasına izin verebilir. Tek yönlü yöntemler belirtme hakkında ayrıntılı bilgi için, bkz <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> . özelliği ve <xref:System.ServiceModel.OperationContractAttribute> sınıfı.  
  
 Bir çift yönlü sözleşme için istemci uygulaması oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: tek yönlü ve istek-yanıt sözleşmeleriyle hizmetlere erişme](how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md). Çalışan bir örnek için bkz. [tek yönlü](../samples/one-way.md) örnek.  
  
### <a name="to-create-a-one-way-contract"></a>Tek yönlü bir sözleşme oluşturmak için  
  
1. <xref:System.ServiceModel.ServiceContractAttribute>Sınıfı, hizmetin uygulanacağı yöntemleri tanımlayan arabirime uygulayarak hizmet sözleşmesini oluşturun.  
  
2. Bir istemcinin Arabirim içindeki hangi yöntemlerin bu sınıfa uygulama tarafından çağrılabileceğini belirtin <xref:System.ServiceModel.OperationContractAttribute> .  
  
3. Özelliğini olarak ayarlayarak çıkış olmaması gereken (dönüş değeri yok ve out veya ref parametreleri olmayan) işlemleri tek yönlü olarak belirleyin <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> `true` . <xref:System.ServiceModel.OperationContractAttribute>Özelliği varsayılan olarak olduğu için, sınıfı taşıyan işlemlerin varsayılan olarak bir istek-yanıt sözleşmesini karşıladığına unutmayın <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> `false` . Bu nedenle `true` , yöntemi için tek yönlü bir anlaşma istiyorsanız, öznitelik özelliğinin değerini açıkça belirtmeniz gerekir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, birkaç tek yönlü Yöntem içeren bir hizmet için bir sözleşme tanımlar. Tüm yöntemlerin tek yönlü sözleşmeleri vardır `Equals` ve bu, varsayılan olarak istek-yanıt verir ve bir sonuç döndürür.  
  
 [!code-csharp[S_Service_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_service_session/cs/service.cs#1)]
 [!code-vb[S_Service_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_service_session/vb/service.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- [Hizmetleri Tasarlama ve Uygulama](../designing-and-implementing-services.md)
- [Nasıl yapılır: Bir Hizmet Anlaşması Tanımlama](../how-to-define-a-wcf-service-contract.md)
- [Oturum](../samples/session.md)
- [Nasıl yapılır: Çift Yönlü Sözleşme Oluşturma](how-to-create-a-duplex-contract.md)
