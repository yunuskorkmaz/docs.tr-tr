---
title: "Nasıl yapılır: Sözleşme Arabirimi ile Hizmet Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 7b6803f6-d6f9-4cc2-9f1b-6f4c920475d5
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b00a7cbbab343eb209895affbbbba76ef2af2959
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-service-with-a-contract-interface"></a>Nasıl yapılır: Sözleşme Arabirimi ile Hizmet Oluşturma
Oluşturmak için tercih edilen yol bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] sözleşmedir bir arabirim kullanarak. Bu sözleşme koleksiyon ve işlemleri erişmek için gerekli iletileri yapısını belirtir hizmeti sunar. Bu arabirim uygulayarak giriş ve çıkış türlerini tanımlar <xref:System.ServiceModel.ServiceContractAttribute> arabirimi sınıfına ve <xref:System.ServiceModel.OperationContractAttribute> kullanıma sunmak istediğiniz yöntemleri sınıfına.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Hizmet sözleşmeleri için bkz: [Hizmet sözleşmeleri tasarlama](../../../../docs/framework/wcf/designing-service-contracts.md).  
  
### <a name="creating-a-wcf-contract-with-an-interface"></a>Bir WCF Sözleşmesi ile bir arabirim oluşturma  
  
1.  Kullanarak yeni bir arabirim oluşturmak [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], C# veya herhangi diğer ortak dil çalışma zamanı dili.  
  
2.  Uygulama <xref:System.ServiceModel.ServiceContractAttribute> arabirimi sınıfı.  
  
3.  Arabirim yöntemleri tanımlar.  
  
4.  Uygulama <xref:System.ServiceModel.OperationContractAttribute> ortak bir parçası olarak sunulan her yöntemi sınıfına [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sözleşme.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği bir hizmet sözleşmesini tanımlayan bir arabirimi gösterir.  
  
 [!code-csharp[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithinterface/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithinterface/vb/source.vb#1)]  
  
 Sahip yöntemleri <xref:System.ServiceModel.OperationContractAttribute> sınıfı uygulanan varsayılan bir istek-yanıt iletisi desen kullanın. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Bu ileti deseni bkz [nasıl yapılır: istek-yanıt sözleşmesi oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md). Ayrıca, oluşturabilir ve öznitelik özelliklerini ayarlayarak diğer ileti modelleri kullanın. Daha fazla örnek için bkz: [nasıl yapılır: bir One-Way sözleşmesi oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) ve [nasıl yapılır: çift yönlü sözleşme oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>
