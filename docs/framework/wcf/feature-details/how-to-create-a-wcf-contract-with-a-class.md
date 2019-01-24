---
title: 'Nasıl yapılır: Bir Windows Communication Foundation sözleşme sınıfı ile oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1ad69393-3915-4e7f-9b91-b6fc59c6f5ba
ms.openlocfilehash: b32d4feb03daac33af8b7ca3b533a0b7013bb090
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54658932"
---
# <a name="how-to-create-a-windows-communication-foundation-contract-with-a-class"></a>Nasıl yapılır: Bir Windows Communication Foundation sözleşme sınıfı ile oluşturma
Bir Windows Communication Foundation (WCF) sözleşmesi oluşturma tercih edilen yol, bir arabirim kullanmaktır. Daha fazla bilgi için [nasıl yapılır: Bir hizmet sözleşmesini tanımlama](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md). Bir alternatif, Anahatlı burayı olan bir sınıf oluşturun ve ardından uygulama <xref:System.ServiceModel.ServiceContractAttribute> sınıfı özniteliği doğrudan ve <xref:System.ServiceModel.OperationContractAttribute> her sözleşmesinin bir parçası olan yöntemler için özniteliği.  
  
> [!WARNING]
>  `[ServiceContract]` ve `[ServiceContractAttribute]` aynı işlevi görür. Aynı şeyi true `[OperationContract]` ve `[OperationContractAttribute]`. Her durumda, önceki ikincisi için Toplu özellik var.  
  
 Hizmet sözleşmeleri hakkında daha fazla bilgi için bkz: [Hizmet sözleşmeleri tasarlama](../../../../docs/framework/wcf/designing-service-contracts.md).  
  
### <a name="creating-a-windows-communication-foundation-contract-with-a-class"></a>Bir Windows Communication Foundation sözleşme sınıfı ile oluşturma  
  
1.  Visual Basic kullanarak yeni bir sınıf oluşturun C#, veya tüm diğer ortak dil çalışma zamanı dil.  
  
2.  Uygulama <xref:System.ServiceModel.ServiceContractAttribute> sınıfı için sınıf.  
  
3.  Sınıfı yöntemleri oluşturun.  
  
4.  Uygulama <xref:System.ServiceModel.OperationContractAttribute> genel WCF sözleşmesinin bir parçası sunulan her yöntem için sınıf.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği bir hizmet anlaşmasını tanımlayan bir sınıf gösterir.  
  
 [!code-csharp[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithclass/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithclass/vb/source.vb#1)]  
  
 Sahip yöntemleri <xref:System.ServiceModel.OperationContractAttribute> uygulanan sınıfı, varsayılan olarak istek-yanıt iletisi deseni kullanın. Bu ileti düzeni hakkında daha fazla bilgi için bkz. [nasıl yapılır: İstek-yanıt anlaşması oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md). Ayrıca, oluşturabilir ve diğer ileti desenleri öznitelik özelliklerini ayarlayarak kullanın. Daha fazla örnek için bkz. [nasıl yapılır: Tek yönlü anlaşma oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) ve [nasıl yapılır: Çift yönlü sözleşme oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
