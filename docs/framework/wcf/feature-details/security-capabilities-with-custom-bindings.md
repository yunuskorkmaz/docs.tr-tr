---
title: "Özel Bağlamalarla Güvenlik Özellikleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2425679-484a-4e6c-9c98-7da7304f1516
caps.latest.revision: "11"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 9d252dca363c952dde44b499363e285d4bb7eb82
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="security-capabilities-with-custom-bindings"></a>Özel Bağlamalarla Güvenlik Özellikleri
Sistem tarafından sağlanan bağlamalar birini kullanarak en yaygın güvenlik görevlerini gerçekleştirebilirsiniz. Daha fazla denetim ihtiyacınız varsa, ancak, özel bağlama ile oluşturabileceğiniz bir <xref:System.ServiceModel.Channels.SecurityBindingElement>, bu konu başlıklarında açıklandığı gibi. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Özel bağlamalar bkz [özel bağlamalar](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [SecurityBindingElement kimlik doğrulama modları](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)  
 Özel bağlama ile olası kimlik doğrulama modları açıklanır.  
  
 [Nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 Özel bağlama olan bir güvenlik öğesi oluşturmak için temel adımlar açıklanmıştır.  
  
 [Nasıl yapılır: belirtilen kimlik doğrulama modu için SecurityBindingElement oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)  
 Belirtilen kimlik doğrulama modu için bir güvenlik öğesi oluşturmayı açıklar.  
  
 [Nasıl yapılır: Güvenli WSFederationHttpBinding gücenli oturumlarını devre dışı bırak](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 Güvenli oturumlar devre dışı bırakma açıklayan bir Federasyon Hizmeti oluştururken.  
  
 [Nasıl yapılır: ileti yeniden yürütme algılamayı etkinleştirme](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)  
 Yeniden yürütme saldırısını oluştuğunda belirlemek açıklar.  
  
 [Nasıl yapılır: destekleyici kimlik bilgileri oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-supporting-credential.md)  
 Hizmet gerektiriyorsa bir hizmete destekleyen bir kimlik bilgisi sağlamayı açıklar.  
  
 [Nasıl yapılır: bir imza onayı ayarlama](../../../../docs/framework/wcf/feature-details/how-to-set-up-a-signature-confirmation.md)  
 Dijital olarak iletileri imzalarken imzaları doğrulamak için gereken adımları açıklar.  
  
 [Nasıl yapılır: maksimum saat eğriltme ayarlama](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)  
 Bir hizmet ve istemci arasındaki en fazla izin verilen zaman farkı ayarlanacağını açıklar.  
  
 [Nasıl yapılır: dijital imzaların şifrelenmesini devre dışı bırakma](../../../../docs/framework/wcf/feature-details/how-to-disable-encryption-of-digital-signatures.md)  
 Dijital imzaların şifrelenmesi devre dışı bırakma performans avantajı nasıl sağlayabilirsiniz açıklar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
 [\<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Koruma düzeylerini anlama](../../../../docs/framework/wcf/understanding-protection-level.md)  
  
 [Hizmetler ve istemcileri güvenli hale getirme](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bağlamalar ve güvenlik](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
 [Güvenlik genel bakış](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Sistem tarafından sağlanan bağlamalar](../../../../docs/framework/wcf/system-provided-bindings.md)
