---
title: Özel Bağlamalarla Güvenlik Özellikleri
ms.date: 03/30/2017
ms.assetid: a2425679-484a-4e6c-9c98-7da7304f1516
ms.openlocfilehash: 48d17543f2b133c74bcfa82cfe1a2a0de28b1d01
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595199"
---
# <a name="security-capabilities-with-custom-bindings"></a>Özel Bağlamalarla Güvenlik Özellikleri
Sistem tarafından belirtilen bağlamalardan birini kullanarak en yaygın güvenlik görevlerini gerçekleştirebilirsiniz. Ancak, daha fazla denetime ihtiyacınız varsa, <xref:System.ServiceModel.Channels.SecurityBindingElement> Bu konularda açıklandığı gibi, ile özel bir bağlama oluşturabilirsiniz. Özel Bağlamalar hakkında daha fazla bilgi için bkz. [Özel Bağlamalar](../extending/custom-bindings.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [SecurityBindingElement Kimlik Doğrulama Modları](securitybindingelement-authentication-modes.md)  
 Özel bir bağlama ile mümkün olan kimlik doğrulama modlarını açıklar.  
  
 [Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma](how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 Bir güvenlik öğesiyle özel bağlama oluşturmaya yönelik temel adımları açıklar.  
  
 [Nasıl yapılır: Belirtilen Bir Kimlik Doğrulama Modu için SecurityBindingElement Oluşturma](how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)  
 Belirtilen bir kimlik doğrulama modu için bir güvenlik öğesinin nasıl oluşturulacağını açıklar.  
  
 [Nasıl yapılır: WSFederationHttpBinding Güvenli Oturumlarını Devre Dışı Bırakma](how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 Federasyon Hizmeti oluştururken güvenli oturumların nasıl devre dışı bırakılacağını açıklar.  
  
 [Nasıl yapılır: İleti Yeniden Yürütme Algılamayı Etkinleştirme](how-to-enable-message-replay-detection.md)  
 Bir yeniden yürütme saldırısının ne zaman gerçekleşeceğini nasıl belirleyebileceğinizi açıklar.  
  
 [Nasıl yapılır: Destekleyici Kimlik Bilgileri Oluşturma](how-to-create-a-supporting-credential.md)  
 Hizmeti gerektiriyorsa, bir hizmete destekleyici kimlik bilgisi sağlamayı açıklar.  
  
 [Nasıl yapılır: İmza Onayı Ayarlama](how-to-set-up-a-signature-confirmation.md)  
 İletileri dijital olarak imzalarken imzaları onaylama adımlarını açıklar.  
  
 [Nasıl yapılır: Maksimum Saat Eğriltme Ayarlama](how-to-set-a-max-clock-skew.md)  
 Bir hizmet ve istemci arasında izin verilen en uzun zaman farkının nasıl ayarlanacağını açıklar.  
  
 [Nasıl yapılır: Dijital İmzaların Şifrelenmesini Devre Dışı Bırakma](how-to-disable-encryption-of-digital-signatures.md)  
 Dijital imzaların şifrelenmesini devre dışı bırakmanın performans avantajına sahip olabilir.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
 [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md)  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Koruma Düzeylerini Anlama](../understanding-protection-level.md)  
  
 [Hizmet ve İstemcileri Güvenli Hale Getirme](securing-services-and-clients.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağlamalar ve Güvenlik](bindings-and-security.md)
- [Güvenliğe genel bakış](security-overview.md)
- [Sistem tarafından sağlanmış bağlamalar](../system-provided-bindings.md)
