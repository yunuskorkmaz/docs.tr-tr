---
title: "Dijital İmzaların Şifrelenmesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- encryption of digital signatures [WCF]
- digital signatures [WCF], encryption
- digital signatures [WCF]
ms.assetid: 0868866d-40b4-4341-8e42-eee3b7f15b69
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 541e8a60797dca5db632ad8bd383cf926ec0d6dc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="encryption-of-digital-signatures"></a>Dijital İmzaların Şifrelenmesi
Varsayılan olarak, bir ileti imzalanır ve şifrelenir ve imza dijital olarak şifrelenir. Bu örneği ile özel bağlama oluşturarak kontrol <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> veya <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> ve ardından ayarlar `MessageProtectionOrder` özelliği için her iki sınıfın bir <xref:System.ServiceModel.Security.MessageProtectionOrder> numaralandırma değeri. Varsayılan, <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature> değeridir. Bu işlem 10-40 yüzde sadece imzalama ve şifreleme daha uzun sürer. İmza şifrelemeyi devre dışı bırakmak ancak, bir saldırganın iletinin içeriğini tahmin sağlayabilir. Düz metin iletisi imzalı her bölümünün karma kodunu imza öğesi içerdiği için bu mümkün olur. Örneğin, varsayılan ileti gövdesi şifrelenmesine rağmen şifrelenmemiş imza ileti gövdesinin karma kodunu içerir. İleti küçükse, bir saldırganın içeriği türetme olabilir. İmza şifreleme küçültür veya bu olasılığını ortadan kaldırır.  
  
 Bu nedenle, şifreleme imza yalnızca içeriğin değerinin düşük olduğunda ve performans kazancı Örneğin, hiçbir güvenlik uygulamalarını sahip büyük ikili dosyaları gönderirken önemli olacaktır devre dışı bırakın.  
  
### <a name="to-disable-digital-signing"></a>Dijital imzasını devre dışı bırakmak için  
  
1.  Oluşturma bir <xref:System.ServiceModel.Channels.CustomBinding>. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
2.  Ekleyip ya da bir <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> veya <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> bağlama koleksiyonuna.  
  
3.  Ayarlama <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> özelliğine <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>, veya <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> özelliğine <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]özel bağlama oluşturma, bkz: [Creating User-Defined bağlamaları](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Özel kimlik doğrulama modu için özel bağlama oluşturma [nasıl yapılır: belirtilen kimlik doğrulama modu için SecurityBindingElement oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Security.MessageProtectionOrder>  
 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
 [Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [Kullanıcı Tanımlı Bağlamalar Oluşturma](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)  
 [Nasıl yapılır: Belirtilen Bir Kimlik Doğrulama Modu için SecurityBindingElement Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
