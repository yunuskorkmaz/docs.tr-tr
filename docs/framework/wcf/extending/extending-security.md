---
title: Güvenliği Genişletme
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], extending
ms.assetid: a015a040-9fdf-4147-9ea9-f83b570be1d4
ms.openlocfilehash: 45216493a3afa23f24a085964a2c43e19b197d4b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797125"
---
# <a name="extending-security"></a>Güvenliği Genişletme
Yeni talep türlerini ve özel belirteçleri barındırmak için Windows Communication Foundation (WCF) güvenlik altyapısını genişletebilirsiniz. Bu bölümdeki konular, bunun nasıl yapıldığını göstermektedir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
 [Özel Kimlik Bilgileri ve Kimlik Bilgileri Doğrulaması](custom-credential-and-credential-validation.md)  
 Özel kimlik bilgileri doğrulanırken kimlik modelinin nasıl kullanıldığını açıklar.  
  
 [Özel Belirteçler](custom-tokens.md)  
 Bir güvenlik belirteci hizmetinden (STS) verilen belirteçler genellikle SAML belirteçleridir. Bu konu başlığı altında, özel bir belirteç türünün nasıl oluşturulacağı açıklanmaktadır.  
  
 [Özel Yetkilendirme](custom-authorization.md)  
 Özel yetkilendirmenin nasıl uygulanacağını açıklar.  
  
 [Bir Hizmetin Kimliğini Kimlik Doğrulama için Geçersiz Kılma](overriding-the-identity-of-a-service-for-authentication.md)  
 Kimlik doğrulaması için bir hizmetin kimliğini geçersiz kılmayı açıklar.  
  
 [Nasıl yapılır: Özel bir Istemci Kimliği Doğrulayıcısı oluşturma](how-to-create-a-custom-client-identity-verifier.md)  
 Özel bir uç nokta kimliğinin nasıl doğrulandığını gösterir.  
  
 [Nasıl yapılır: Imzalama ve şifreleme için ayrı X. 509.440 sertifikaları kullanma](how-to-use-separate-x-509-certificates-for-signing-and-encryption.md)  
 İletiler genellikle tek bir sertifikayla imzalanıp şifrelenir. Bu konuda, gerektiğinde iki sertifikanın nasıl kullanılabileceği açıklanmaktadır.  
  
 [Nasıl yapılır: X. 509.440 sertifikasının özel anahtarı için şifreleme sağlayıcısını değiştirme](change-cryptographic-provider-x509-certificate-private-key.md)  
 X. 509.440 sertifikasının özel anahtarını sağlamak için kullanılan şifreleme sağlayıcısının ve sağlayıcının Windows Communication Foundation (WCF) çerçevesiyle nasıl tümleştirileceği açıklanmaktadır.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Güvenlik](../feature-details/security.md)  
  
 [Temel WCF Programlama](../basic-wcf-programming.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenliğe Genel Bakış](../feature-details/security-overview.md)
