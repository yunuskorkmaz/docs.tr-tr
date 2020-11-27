---
title: 'Nasıl yapılır: Yetkilendirirken Meta Veri İsteklerine İzin Verme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- allowing metadata requests while authorizing [WCF]
ms.assetid: 90cec34f-b619-452b-a056-8b1c0de49d05
ms.openlocfilehash: 9acc007ea7837f7b8e6c958fa81547fe4fa5b2c0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96257619"
---
# <a name="how-to-allow-metadata-requests-while-authorizing"></a>Nasıl yapılır: Yetkilendirirken Meta Veri İsteklerine İzin Verme

Özel yetkilendirme sırasında, meta verilerin işlenmesine yönelik bir isteğin işlenmesine izin vermek gerekli olabilir. Aşağıdaki konu, bu tür bir isteği doğrulamaya yönelik adımları adım adım göstermektedir.  
  
 Windows Communication Foundation (WCF) yetkilendirmesi hakkında daha fazla bilgi için bkz. [Yetkilendirme](authorization-in-wcf.md).  
  
### <a name="to-allow-metadata-requests-during-authorization"></a>Yetkilendirme sırasında meta veri isteklerine izin vermek için  
  
1. Sınıfın bir uzantısını oluşturun <xref:System.ServiceModel.ServiceAuthorizationManager> .  
  
2. Yöntemini geçersiz kılın <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> . Yöntemi, `true` `false` yetkilendirime izin verilip verilmeyeceğini belirtir. Geçerli yordam hakkındaki bilgiler, <xref:System.ServiceModel.OperationContext> metoduna bir parametre olarak geçirilmiş içinde bulunur.  
  
3. Geçersiz kılma ' da, aşağıdaki örnekte gösterildiği gibi sözleşme adını, ad alanını ve eylemi kontrol edin. Koşullar geçerliyse, dön `true.`  
  
4. Sınıfı kullanmak için genişletilebilirlik noktasını kullanın. Daha fazla bilgi için bkz. [nasıl yapılır: bir hizmet Için özel Yetkilendirme Yöneticisi oluşturma](../extending/how-to-create-a-custom-authorization-manager-for-a-service.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek yöntemi geçersiz kılmayı gösterir <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> .  
  
 [!code-csharp[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/cs/source.cs#1)]
 [!code-vb[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/vb/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [Yetkilendirme](authorization-in-wcf.md)
- [Kimlik Modeliyle Beyanlar ve Yetkilendirmeyi Yönetme](managing-claims-and-authorization-with-the-identity-model.md)
