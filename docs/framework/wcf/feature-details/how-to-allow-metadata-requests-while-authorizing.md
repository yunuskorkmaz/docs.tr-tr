---
title: 'Nasıl yapılır: Yetkilendirirken Meta Veri İsteklerine İzin Verme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- allowing metadata requests while authorizing [WCF]
ms.assetid: 90cec34f-b619-452b-a056-8b1c0de49d05
ms.openlocfilehash: bea4f7e90df29678697fe6708bdc6a73145522db
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62047808"
---
# <a name="how-to-allow-metadata-requests-while-authorizing"></a>Nasıl yapılır: Yetkilendirirken Meta Veri İsteklerine İzin Verme
Özel yetkilendirme sırasında işlenecek meta veri isteği izin vermek gerekli olabilir. Aşağıdaki konuda bu tür bir istek doğrulamak için adımlarda size yol gösterir.  
  
 Windows Communication Foundation (WCF) yetkilendirme hakkında daha fazla bilgi için bkz: [yetkilendirme](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).  
  
### <a name="to-allow-metadata-requests-during-authorization"></a>Yetkilendirme sırasında meta veri isteklerine izin vermek için  
  
1. Oluşturma uzantısı <xref:System.ServiceModel.ServiceAuthorizationManager> sınıfı.  
  
2. Geçersiz kılma <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> yöntemi. Yöntem döndürür `true` veya `false` yetkilendirme verilip verilmediğine bağlı olarak. Geçerli yordam hakkında bilgi de ulaşabilirsiniz <xref:System.ServiceModel.OperationContext> yönteme parametre olarak.  
  
3. Geçersiz sözleşme adı, ad alanı ve aşağıdaki örnekte gösterildiği gibi bir eylem denetleyin. Koşullar geçerli olduğunda, ardından dönün `true.`  
  
4. Sınıf kullanmak istemiyorsunuz genişletilebilirlik noktası kullanın. Daha fazla bilgi için [nasıl yapılır: Bir hizmet için özel Yetkilendirme Yöneticisi oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, geçersiz kılma gösterir <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> yöntemi.  
  
 [!code-csharp[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/cs/source.cs#1)]
 [!code-vb[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/vb/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [Yetkilendirme](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)
- [Kimlik Modeliyle Talep ve Yetkilendirmeyi Yönetme](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
