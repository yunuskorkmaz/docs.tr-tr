---
title: "Nasıl yapılır: Yetkilendirirken Meta Veri İsteklerine İzin Verme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- allowing metadata requests while authorizing [WCF]
ms.assetid: 90cec34f-b619-452b-a056-8b1c0de49d05
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7661cf3c0f13ebf2f077318e022e8f5fd115e2a1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-allow-metadata-requests-while-authorizing"></a>Nasıl yapılır: Yetkilendirirken Meta Veri İsteklerine İzin Verme
Özel yetkilendirme sırasında işlenmesi için meta veriler için bir istek izin vermek gerekli olabilir. Aşağıdaki konu böyle bir istek doğrulamak için adımlarda size yol gösterir.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)][!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] yetkilendirme, bkz: [yetkilendirme](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).  
  
### <a name="to-allow-metadata-requests-during-authorization"></a>Yetkilendirme sırasında meta veri isteklerine izin vermek için  
  
1.  Uzantısı oluşturma <xref:System.ServiceModel.ServiceAuthorizationManager> sınıfı.  
  
2.  Geçersiz kılma <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> yöntemi. Yöntem `true` veya `false` yetkilendirme verilip verilmediğine bağlı olarak. Geçerli yordam hakkında bilgi içinde bulunan <xref:System.ServiceModel.OperationContext> yönteme parametre olarak geçirilen.  
  
3.  Geçersiz sözleşme adı, ad alanı ve aşağıdaki örnekte gösterildiği gibi eylem denetleyin. Koşullar geçerli olduğunda, ardından Döndür`true.`  
  
4.  Sınıf kullanımlar için genişletilebilirlik noktası kullanın. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Nasıl yapılır: bir hizmet için özel Yetkilendirme Yöneticisi oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir geçersiz kılma gösterir <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> yöntemi.  
  
 [!code-csharp[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/cs/source.cs#1)]
 [!code-vb[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/vb/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
 [Yetkilendirme](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
 [Kimlik Modeliyle Talep ve Yetkilendirmeyi Yönetme](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
