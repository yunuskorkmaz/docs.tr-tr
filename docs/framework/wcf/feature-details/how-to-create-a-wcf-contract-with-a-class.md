---
title: 'Nasıl yapılır: Sınıf ile Windows Communication Foundation sözleşmesi oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1ad69393-3915-4e7f-9b91-b6fc59c6f5ba
ms.openlocfilehash: 2cd757107d9f62ce749d98db1d4968c02a09c5d2
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988741"
---
# <a name="how-to-create-a-windows-communication-foundation-contract-with-a-class"></a>Nasıl yapılır: Sınıf ile Windows Communication Foundation sözleşmesi oluşturma
Windows Communication Foundation (WCF) sözleşmesinin oluşturulması için tercih edilen yöntem bir arabirim kullanmaktır. Daha fazla bilgi için [nasıl yapılır: Bir hizmet sözleşmesi](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)tanımlayın. Burada özetlenen alternatif, bir sınıf oluşturmak ve ardından doğrudan sınıfa <xref:System.ServiceModel.ServiceContractAttribute> <xref:System.ServiceModel.OperationContractAttribute> ve özniteliği, sözleşmenin bir parçası olan sınıftaki yöntemlerin her birine uygular.  
  
> [!WARNING]
> `[ServiceContract]`ve `[ServiceContractAttribute]` aynı şeyi yapın. `[OperationContract]` Ve`[OperationContractAttribute]`için aynı şey doğrudur. Her durumda, ilki ikinci için toplu bir özelliktir.  
  
 Hizmet sözleşmeleri hakkında daha fazla bilgi için bkz. [hizmet sözleşmeleri tasarlama](../../../../docs/framework/wcf/designing-service-contracts.md).  
  
### <a name="creating-a-windows-communication-foundation-contract-with-a-class"></a>Bir sınıfla Windows Communication Foundation sözleşmesi oluşturma  
  
1. Visual Basic, C#veya diğer tüm ortak dil çalışma zamanı dilini kullanarak yeni bir sınıf oluşturun.  
  
2. <xref:System.ServiceModel.ServiceContractAttribute> Sınıfını sınıfına uygulayın.  
  
3. Sınıfında yöntem oluşturun.  
  
4. <xref:System.ServiceModel.OperationContractAttribute> Sınıfı, genel WCF sözleşmesinin bir parçası olarak kullanıma sunulacak her bir yönteme uygulayın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, bir hizmet sözleşmesini tanımlayan bir sınıfı gösterir.  
  
 [!code-csharp[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithclass/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithclass/vb/source.vb#1)]  
  
 <xref:System.ServiceModel.OperationContractAttribute> Sınıf uygulanmış Yöntemler varsayılan olarak bir istek-yanıt iletisi model kullanır. Bu ileti düzeniyle ilgili daha fazla bilgi için bkz [. nasıl yapılır: Istek-yanıt Sözleşmesi](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md)oluşturun. Ayrıca, özniteliğin özelliklerini ayarlayarak diğer ileti düzenlerini de oluşturabilir ve kullanabilirsiniz. Daha fazla örnek için bkz [. nasıl yapılır: Tek yönlü bir sözleşme](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) oluşturun ve [şunları yapın: Çift yönlü sözleşme](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)oluşturun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
