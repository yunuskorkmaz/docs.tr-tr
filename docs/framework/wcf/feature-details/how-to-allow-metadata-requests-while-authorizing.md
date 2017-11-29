---
title: "Nasıl yapılır: Yetkilendirirken Meta Veri İsteklerine İzin Verme"
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
helpviewer_keywords: allowing metadata requests while authorizing [WCF]
ms.assetid: 90cec34f-b619-452b-a056-8b1c0de49d05
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 103aba5118810064c1cafb7c82634ef000ced667
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [Beyanlar ve yetkilendirmeyi kimlik modeliyle yönetme](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
