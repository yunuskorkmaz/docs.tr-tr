---
title: 'Nasıl yapılır: Sınıf ile Windows Communication Foundation Sözleşmesi Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1ad69393-3915-4e7f-9b91-b6fc59c6f5ba
ms.openlocfilehash: 296f500532040aaebf0f6d7d37a7a9aae99a3451
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491819"
---
# <a name="how-to-create-a-windows-communication-foundation-contract-with-a-class"></a>Nasıl yapılır: Sınıf ile Windows Communication Foundation Sözleşmesi Oluşturma
Windows Communication Foundation (WCF) sözleşme oluşturma tercih edilen bir arabirim kullanılarak yoludur. Daha fazla bilgi için bkz: [nasıl yapılır: bir hizmet sözleşmesini tanımlama](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md). Bir alternatif, Anahatlı burada olan bir sınıf oluşturun ve ardından uygulamak için <xref:System.ServiceModel.ServiceContractAttribute> sınıfa öznitelik doğrudan ve <xref:System.ServiceModel.OperationContractAttribute> özniteliği her sözleşmenin parçası sınıftaki yöntemleri.  
  
> [!WARNING]
>  `[ServiceContract]` ve `[ServiceContractAttribute]` aynı işlevi görür. True için aynı şeyi `[OperationContract]` ve `[OperationContractAttribute]`. Her durumda, ikinci için toplu eski özelliktir.  
  
 Hizmet sözleşmeleri hakkında daha fazla bilgi için bkz: [Hizmet sözleşmeleri tasarlama](../../../../docs/framework/wcf/designing-service-contracts.md).  
  
### <a name="creating-a-windows-communication-foundation-contract-with-a-class"></a>Bir sınıf ile Windows Communication Foundation sözleşmesi oluşturma  
  
1.  Visual Basic, C# veya herhangi diğer ortak dil çalışma zamanı dil kullanarak yeni bir sınıf oluşturun.  
  
2.  Uygulama <xref:System.ServiceModel.ServiceContractAttribute> sınıfı için sınıf.  
  
3.  Yöntemleri sınıfında oluşturun.  
  
4.  Uygulama <xref:System.ServiceModel.OperationContractAttribute> genel WCF sözleşmesinin bir parçası olarak sunulan her yönteme sınıf.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği bir hizmet sözleşmesini tanımlayan bir sınıf gösterir.  
  
 [!code-csharp[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithclass/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithclass/vb/source.vb#1)]  
  
 Sahip yöntemleri <xref:System.ServiceModel.OperationContractAttribute> sınıfı uygulanan varsayılan bir istek-yanıt iletisi desen kullanın. Bu ileti deseni hakkında daha fazla bilgi için bkz: [nasıl yapılır: istek-yanıt sözleşmesi oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md). Ayrıca, oluşturabilir ve öznitelik özelliklerini ayarlayarak diğer ileti modelleri kullanın. Daha fazla örnek için bkz: [nasıl yapılır: bir One-Way sözleşmesi oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) ve [nasıl yapılır: çift yönlü sözleşme oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>
