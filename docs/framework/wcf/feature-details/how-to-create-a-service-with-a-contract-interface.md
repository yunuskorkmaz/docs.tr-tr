---
title: 'Nasıl yapılır: Sözleşme Arabirimi ile Hizmet Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7b6803f6-d6f9-4cc2-9f1b-6f4c920475d5
ms.openlocfilehash: c7d4bce174790b97db6b95aa5d15af455f261f82
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597169"
---
# <a name="how-to-create-a-service-with-a-contract-interface"></a>Nasıl yapılır: Sözleşme Arabirimi ile Hizmet Oluşturma
Windows Communication Foundation (WCF) sözleşmesinin oluşturulması için tercih edilen yol, bir arabirim kullanmaktır. Bu sözleşme, hizmet sunduğu işlemlere erişmek için gereken iletilerin toplanmasını ve yapısını belirtir. Bu arabirim, <xref:System.ServiceModel.ServiceContractAttribute> sınıfının arabirime ve sınıfına sınıfını uygulayarak giriş ve çıkış türlerini, <xref:System.ServiceModel.OperationContractAttribute> göstermek istediğiniz yöntemlere tanımlar.  
  
 Hizmet sözleşmeleri hakkında daha fazla bilgi için bkz. [hizmet sözleşmeleri tasarlama](../designing-service-contracts.md).  
  
### <a name="creating-a-wcf-contract-with-an-interface"></a>Arabirim ile WCF sözleşmesi oluşturma  
  
1. Visual Basic, C# veya başka bir ortak dil çalışma zamanı dili kullanarak yeni bir arabirim oluşturun.  
  
2. <xref:System.ServiceModel.ServiceContractAttribute>Sınıfı arabirime uygulayın.  
  
3. Arabirimindeki yöntemleri tanımlayın.  
  
4. Sınıfı, <xref:System.ServiceModel.OperationContractAttribute> genel WCF sözleşmesinin bir parçası olarak kullanıma sunulacak her bir yönteme uygulayın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde, bir hizmet sözleşmesini tanımlayan bir arabirim gösterilmektedir.  
  
 [!code-csharp[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithinterface/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithinterface/vb/source.vb#1)]  
  
 <xref:System.ServiceModel.OperationContractAttribute>Sınıf uygulanmış Yöntemler varsayılan olarak bir istek-yanıt iletisi model kullanır. Bu ileti düzeniyle ilgili daha fazla bilgi için bkz. [nasıl yapılır: istek-yanıt sözleşmesi oluşturma](how-to-create-a-request-reply-contract.md). Ayrıca, özniteliğin özelliklerini ayarlayarak diğer ileti düzenlerini de oluşturabilir ve kullanabilirsiniz. Daha fazla örnek için bkz. [nasıl yapılır: tek yönlü sözleşme oluşturma](how-to-create-a-one-way-contract.md) ve [nasıl yapılır: çift yönlü sözleşme oluşturma](how-to-create-a-duplex-contract.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
