---
title: 'Nasıl yapılır: Sözleşme Arabirimi ile Hizmet Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7b6803f6-d6f9-4cc2-9f1b-6f4c920475d5
ms.openlocfilehash: 796870b80ed72db2353e79db3e4e3fc164c22875
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-service-with-a-contract-interface"></a>Nasıl yapılır: Sözleşme Arabirimi ile Hizmet Oluşturma
Windows Communication Foundation (WCF) sözleşme oluşturmak için tercih edilen bir arabirim kullanılarak yoludur. Bu sözleşme koleksiyon ve işlemleri erişmek için gerekli iletileri yapısını belirtir hizmeti sunar. Bu arabirim uygulayarak giriş ve çıkış türlerini tanımlar <xref:System.ServiceModel.ServiceContractAttribute> arabirimi sınıfına ve <xref:System.ServiceModel.OperationContractAttribute> kullanıma sunmak istediğiniz yöntemleri sınıfına.  
  
 Hizmet sözleşmeleri hakkında daha fazla bilgi için bkz: [Hizmet sözleşmeleri tasarlama](../../../../docs/framework/wcf/designing-service-contracts.md).  
  
### <a name="creating-a-wcf-contract-with-an-interface"></a>Bir WCF Sözleşmesi ile bir arabirim oluşturma  
  
1.  Visual Basic, C# veya herhangi diğer ortak dil çalışma zamanı dil kullanarak yeni bir arabirim oluşturun.  
  
2.  Uygulama <xref:System.ServiceModel.ServiceContractAttribute> arabirimi sınıfı.  
  
3.  Arabirim yöntemleri tanımlar.  
  
4.  Uygulama <xref:System.ServiceModel.OperationContractAttribute> genel WCF sözleşmesinin bir parçası olarak sunulan her yönteme sınıf.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği bir hizmet sözleşmesini tanımlayan bir arabirimi gösterir.  
  
 [!code-csharp[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithinterface/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithinterface/vb/source.vb#1)]  
  
 Sahip yöntemleri <xref:System.ServiceModel.OperationContractAttribute> sınıfı uygulanan varsayılan bir istek-yanıt iletisi desen kullanın. Bu ileti deseni hakkında daha fazla bilgi için bkz: [nasıl yapılır: istek-yanıt sözleşmesi oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md). Ayrıca, oluşturabilir ve öznitelik özelliklerini ayarlayarak diğer ileti modelleri kullanın. Daha fazla örnek için bkz: [nasıl yapılır: bir One-Way sözleşmesi oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) ve [nasıl yapılır: çift yönlü sözleşme oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>
