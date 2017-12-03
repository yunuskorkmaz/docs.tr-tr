---
title: "Nasıl yapılır: Sınıf ile Windows Communication Foundation Sözleşmesi Oluşturma"
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
ms.assetid: 1ad69393-3915-4e7f-9b91-b6fc59c6f5ba
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cafdda20332bb6f690214a9a9d9c9b6eaa34e911
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-windows-communication-foundation-contract-with-a-class"></a>Nasıl yapılır: Sınıf ile Windows Communication Foundation Sözleşmesi Oluşturma
Oluşturma tercih edilen yol bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] sözleşmedir bir arabirim kullanarak. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Nasıl yapılır: bir hizmet sözleşmesini tanımlama](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md). Bir alternatif, Anahatlı burada olan bir sınıf oluşturun ve ardından uygulamak için <xref:System.ServiceModel.ServiceContractAttribute> sınıfa öznitelik doğrudan ve <xref:System.ServiceModel.OperationContractAttribute> özniteliği her sözleşmenin parçası sınıftaki yöntemleri.  
  
> [!WARNING]
>  `[ServiceContract]`ve `[ServiceContractAttribute]` aynı işlevi görür. True için aynı şeyi `[OperationContract]` ve `[OperationContractAttribute]`. Her durumda, ikinci için toplu eski özelliktir.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Hizmet sözleşmeleri için bkz: [Hizmet sözleşmeleri tasarlama](../../../../docs/framework/wcf/designing-service-contracts.md).  
  
### <a name="creating-a-windows-communication-foundation-contract-with-a-class"></a>Bir sınıf ile Windows Communication Foundation sözleşmesi oluşturma  
  
1.  Kullanarak yeni bir sınıf oluşturmak [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], C# veya herhangi diğer ortak dil çalışma zamanı dili.  
  
2.  Uygulama <xref:System.ServiceModel.ServiceContractAttribute> sınıfı için sınıf.  
  
3.  Yöntemleri sınıfında oluşturun.  
  
4.  Uygulama <xref:System.ServiceModel.OperationContractAttribute> ortak bir parçası olarak sunulan her yöntemi sınıfına [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sözleşme.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği bir hizmet sözleşmesini tanımlayan bir sınıf gösterir.  
  
 [!code-csharp[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithclass/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithclass/vb/source.vb#1)]  
  
 Sahip yöntemleri <xref:System.ServiceModel.OperationContractAttribute> sınıfı uygulanan varsayılan bir istek-yanıt iletisi desen kullanın. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Bu ileti deseni bkz [nasıl yapılır: istek-yanıt sözleşmesi oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md). Ayrıca, oluşturabilir ve öznitelik özelliklerini ayarlayarak diğer ileti modelleri kullanın. Daha fazla örnek için bkz: [nasıl yapılır: bir One-Way sözleşmesi oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) ve [nasıl yapılır: çift yönlü sözleşme oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>
