---
title: 'Nasıl yapılır: Sınıf ile Windows Communication Foundation Sözleşmesi Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1ad69393-3915-4e7f-9b91-b6fc59c6f5ba
ms.openlocfilehash: 0be2400ef3da5f0bbc218032ecd69af23f82cabd
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597143"
---
# <a name="how-to-create-a-windows-communication-foundation-contract-with-a-class"></a>Nasıl yapılır: Sınıf ile Windows Communication Foundation Sözleşmesi Oluşturma
Windows Communication Foundation (WCF) sözleşmesinin oluşturulması için tercih edilen yöntem bir arabirim kullanmaktır. Daha fazla bilgi için bkz. [nasıl yapılır: hizmet sözleşmesi tanımlama](../how-to-define-a-wcf-service-contract.md). Burada özetlenen alternatif, bir sınıf oluşturmak ve ardından <xref:System.ServiceModel.ServiceContractAttribute> doğrudan sınıfa ve <xref:System.ServiceModel.OperationContractAttribute> özniteliği, sözleşmenin bir parçası olan sınıftaki yöntemlerin her birine uygular.  
  
> [!WARNING]
> `[ServiceContract]`ve `[ServiceContractAttribute]` aynı şeyi yapın. Ve için aynı şey doğrudur `[OperationContract]` `[OperationContractAttribute]` . Her durumda, ilki ikinci için toplu bir özelliktir.  
  
 Hizmet sözleşmeleri hakkında daha fazla bilgi için bkz. [hizmet sözleşmeleri tasarlama](../designing-service-contracts.md).  
  
### <a name="creating-a-windows-communication-foundation-contract-with-a-class"></a>Bir sınıfla Windows Communication Foundation sözleşmesi oluşturma  
  
1. Visual Basic, C# veya başka bir ortak dil çalışma zamanı dili kullanarak yeni bir sınıf oluşturun.  
  
2. Sınıfını <xref:System.ServiceModel.ServiceContractAttribute> sınıfına uygulayın.  
  
3. Sınıfında yöntem oluşturun.  
  
4. Sınıfı, <xref:System.ServiceModel.OperationContractAttribute> genel WCF sözleşmesinin bir parçası olarak kullanıma sunulacak her bir yönteme uygulayın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, bir hizmet sözleşmesini tanımlayan bir sınıfı gösterir.  
  
 [!code-csharp[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithclass/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithclass/vb/source.vb#1)]  
  
 <xref:System.ServiceModel.OperationContractAttribute>Sınıf uygulanmış Yöntemler varsayılan olarak bir istek-yanıt iletisi model kullanır. Bu ileti düzeniyle ilgili daha fazla bilgi için bkz. [nasıl yapılır: istek-yanıt sözleşmesi oluşturma](how-to-create-a-request-reply-contract.md). Ayrıca, özniteliğin özelliklerini ayarlayarak diğer ileti düzenlerini de oluşturabilir ve kullanabilirsiniz. Daha fazla örnek için bkz. [nasıl yapılır: tek yönlü sözleşme oluşturma](how-to-create-a-one-way-contract.md) ve [nasıl yapılır: çift yönlü sözleşme oluşturma](how-to-create-a-duplex-contract.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
