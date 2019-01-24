---
title: 'Nasıl yapılır: Tek yönlü anlaşma oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 85084cd9-31cc-4e95-b667-42ef01336622
ms.openlocfilehash: f7636d7013c236e0c51e5326a84ae47f2f98e283
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54693629"
---
# <a name="how-to-create-a-one-way-contract"></a>Nasıl yapılır: Tek yönlü anlaşma oluşturma
Bu konu, tek yönlü sözleşme kullanan yöntemleri oluşturmak için temel adımları gösterir. Bu tür yöntemler, istemciden gelen Windows Communication Foundation (WCF) hizmet işlemleri çağırma ancak yanıt beklemiyoruz. Bu sözleşme türü, örneğin, bildirimler birçok abonelerine yayımlamak için kullanılabilir. Tek yönlü sözleşmeler, istemciler ve sunucular ya da diğer çağrıları başlatabilir, böylece birbiriyle bağımsız olarak iletişim kurmasına izin veren bir çift yönlü (iki yönlü) sözleşmesi oluştururken de kullanabilirsiniz. Bu, özellikle, tek yönlü istemci olaylar olarak davranabileceğiniz istemci çağrı yapmak sunucu izin verebilirsiniz. Tek yönlü yöntemlerin belirtme hakkında ayrıntılı bilgi için bkz: <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> özelliği ve <xref:System.ServiceModel.OperationContractAttribute> sınıfı.  
  
 Bir istemci uygulaması için çift yönlü sözleşme oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Erişim Hizmetleri tek yönlü ve istek-yanıt sözleşmeleriyle](../../../../docs/framework/wcf/feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md). Çalışma örnek için bkz: [tek yönlü](../../../../docs/framework/wcf/samples/one-way.md) örnek.  
  
### <a name="to-create-a-one-way-contract"></a>Tek yönlü anlaşma oluşturma  
  
1.  Hizmet sözleşmesi uygulayarak oluşturma <xref:System.ServiceModel.ServiceContractAttribute> hizmetidir uygulanacak yöntemleri tanımlar arabirimi sınıfı.  
  
2.  Hangi yöntemlerin arabiriminde bir istemci uygulama tarafından çağrılan belirtebilirsiniz <xref:System.ServiceModel.OperationContractAttribute> onlara sınıfı.  
  
3.  Hiçbir çıktı olmalıdır işlemlerini belirleyin (değer döndürmez ve herhangi bir çıkış veya ref parametreleri) tek yönlü olarak ayarlayarak <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> özelliğini `true`. İşlemleri gerçekleştirmek Not <xref:System.ServiceModel.OperationContractAttribute> sınıfının çünkü bu bir istek-yanıt sözleşmesi varsayılan olarak karşılaması <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> özelliği `false` varsayılan olarak. Öznitelik özelliği olacak şekilde değeri açıkça belirtmeniz gerekir böylece `true` yöntemi için tek yönlü sözleşme istiyorsanız.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, tek yönlü çeşitli yöntemler içeren bir hizmet için bir sözleşmeyi tanımlar. Tek yönlü sözleşmeler dışındaki tüm yöntemleri sahip `Equals`, varsayılan olarak istek-yanıt ve bir sonuç döndürür.  
  
 [!code-csharp[S_Service_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_service_session/cs/service.cs#1)]
 [!code-vb[S_Service_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_service_session/vb/service.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- [Hizmetleri Tasarlama ve Uygulama](../../../../docs/framework/wcf/designing-and-implementing-services.md)
- [Nasıl yapılır: Bir hizmet sözleşmesini tanımlama](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)
- [Oturum](../../../../docs/framework/wcf/samples/session.md)
- [Nasıl yapılır: Çift yönlü sözleşme oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
