---
title: 'Nasıl yapılır: Tek Yönlü Sözleşme Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 85084cd9-31cc-4e95-b667-42ef01336622
ms.openlocfilehash: 80cab35b14dd3b7663405038f2afdea362cdb792
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490779"
---
# <a name="how-to-create-a-one-way-contract"></a>Nasıl yapılır: Tek Yönlü Sözleşme Oluşturma
Bu konuda, tek yönlü sözleşme kullanan yöntemleri oluşturmak için temel adımlar gösterilmektedir. Bu yöntemler bir istemciden bir Windows Communication Foundation (WCF) hizmet işlemlerini çağırma ancak yanıt beklemediğiniz. Bu tür bir sözleşme, örneğin, birçok abonelere bildirimleri yayımlamak için kullanılabilir. Tek yönlü sözleşmeler, istemcilerin ve sunucuların ya da diğer çağrıları başlatmak için birbiriyle bağımsız olarak iletişim kurması verir çift yönlü bir (iki yönlü) sözleşme oluştururken de kullanabilirsiniz. Bu, özellikle, sunucunun istemci olayları olarak davranabilirsiniz istemci tek yönlü çağrı yapmak izin verebilirsiniz. Tek yönlü yöntemleri belirtme hakkında ayrıntılı bilgi için bkz: <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> özelliği ve <xref:System.ServiceModel.OperationContractAttribute> sınıfı.  
  
 Bir istemci uygulaması için çift yönlü sözleşme oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: Erişim Hizmetleri tek yönlü ve istek-yanıt sözleşmeleriyle](../../../../docs/framework/wcf/feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md). Çalışma örnek için bkz: [tek yönlü](../../../../docs/framework/wcf/samples/one-way.md) örnek.  
  
### <a name="to-create-a-one-way-contract"></a>Tek yönlü sözleşme oluşturmak için  
  
1.  Hizmet sözleşmesi uygulayarak oluşturma <xref:System.ServiceModel.ServiceContractAttribute> hizmetidir uygulanacak yöntemleri tanımlar arabirimi sınıfı.  
  
2.  Hangi yöntemlerin arabiriminde bir istemci uygulama tarafından çağrılan belirtebilirsiniz <xref:System.ServiceModel.OperationContractAttribute> bunlara sınıfı.  
  
3.  Hiçbir çıktı olmalıdır işlemleri belirleyin (dönüş değeri yok ve hiçbir çıkış veya başvuru parametreleri) olarak ayarlayarak tek yönlü <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> özelliğine `true`. İşlemleri yürütmek Not <xref:System.ServiceModel.OperationContractAttribute> sınıfı çünkü bu bir istek-yanıt sözleşmesi varsayılan karşılamak <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> özelliği `false` varsayılan olarak. Öznitelik özelliğini değerini açıkça belirtmeniz gerekir böylece `true` yöntemi için tek yönlü sözleşme istiyorsanız.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde tek yönlü için birkaç yöntem içerir bir hizmet için bir sözleşmede tanımlar. Tüm yöntemleri dışında tek yönlü sözleşmeler sahip `Equals`, varsayılan olarak istek-yanıt ve bir sonuç döndürür.  
  
 [!code-csharp[S_Service_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_service_session/cs/service.cs#1)]
 [!code-vb[S_Service_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_service_session/vb/service.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>  
 [Hizmetleri Tasarlama ve Uygulama](../../../../docs/framework/wcf/designing-and-implementing-services.md)  
 [Nasıl yapılır: Bir Hizmet Anlaşması Tanımlama](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)  
 [Oturum](../../../../docs/framework/wcf/samples/session.md)  
 [Nasıl yapılır: Çift Yönlü Anlaşma Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
