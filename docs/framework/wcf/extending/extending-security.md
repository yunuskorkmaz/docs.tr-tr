---
title: Güvenliği Genişletme
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], extending
ms.assetid: a015a040-9fdf-4147-9ea9-f83b570be1d4
ms.openlocfilehash: d91f4812dbccb7807be2e0780cccd1d0c38b1f40
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273067"
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
  
 [Nasıl yapılır: Özel İstemci Kimliği Doğrulayıcı Oluşturma](how-to-create-a-custom-client-identity-verifier.md)  
 Özel bir uç nokta kimliğinin nasıl doğrulandığını gösterir.  
  
 [Nasıl yapılır: İmzalama ve Şifreleme için Ayrı X.509 Sertifikaları Kullanma](how-to-use-separate-x-509-certificates-for-signing-and-encryption.md)  
 İletiler genellikle tek bir sertifikayla imzalanıp şifrelenir. Bu konuda, gerektiğinde iki sertifikanın nasıl kullanılabileceği açıklanmaktadır.  
  
 [Nasıl yapılır: Bir X.509 Sertifikasının Şifreleme Sağlayıcısını Değiştirme](change-cryptographic-provider-x509-certificate-private-key.md)  
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

- [Güvenliğe genel bakış](../feature-details/security-overview.md)
