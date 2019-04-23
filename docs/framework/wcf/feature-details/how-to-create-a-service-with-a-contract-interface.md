---
title: 'Nasıl yapılır: Sözleşme Arabirimi ile Hizmet Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7b6803f6-d6f9-4cc2-9f1b-6f4c920475d5
ms.openlocfilehash: 0aa5429d771aeda0b392b89ec4cc1a07de30973f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59772901"
---
# <a name="how-to-create-a-service-with-a-contract-interface"></a>Nasıl yapılır: Sözleşme Arabirimi ile Hizmet Oluşturma
Windows Communication Foundation (WCF) sözleşme oluşturmak için tercih edilen bir arabirim kullanarak yoludur. Bu sözleşme koleksiyon ve işlemleri erişmek için gerekli iletileri yapısını belirtir hizmet sunar. Bu arabirim uygulayarak girdi ve çıktı türleri tanımlar. <xref:System.ServiceModel.ServiceContractAttribute> sınıf arabirimine ve <xref:System.ServiceModel.OperationContractAttribute> kullanıma sunmak istediğiniz yöntemleri sınıfı.  
  
 Hizmet sözleşmeleri hakkında daha fazla bilgi için bkz: [Hizmet sözleşmeleri tasarlama](../../../../docs/framework/wcf/designing-service-contracts.md).  
  
### <a name="creating-a-wcf-contract-with-an-interface"></a>Bir WCF Sözleşmesi ile bir arabirim oluşturma  
  
1. Visual Basic kullanarak yeni bir arabirim oluşturma C#, veya tüm diğer ortak dil çalışma zamanı dil.  
  
2. Uygulama <xref:System.ServiceModel.ServiceContractAttribute> arabirimi sınıfı.  
  
3. Yöntemler arabirimi tanımlar.  
  
4. Uygulama <xref:System.ServiceModel.OperationContractAttribute> genel WCF sözleşmesinin bir parçası sunulan her yöntem için sınıf.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği bir hizmet anlaşmasını tanımlayan bir arabirimi gösterir.  
  
 [!code-csharp[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithinterface/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithinterface/vb/source.vb#1)]  
  
 Sahip yöntemleri <xref:System.ServiceModel.OperationContractAttribute> uygulanan sınıfı, varsayılan olarak istek-yanıt iletisi deseni kullanın. Bu ileti düzeni hakkında daha fazla bilgi için bkz. [nasıl yapılır: İstek-yanıt anlaşması oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md). Ayrıca, oluşturabilir ve diğer ileti desenleri öznitelik özelliklerini ayarlayarak kullanın. Daha fazla örnek için bkz. [nasıl yapılır: Tek yönlü anlaşma oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) ve [nasıl yapılır: Çift yönlü sözleşme oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
