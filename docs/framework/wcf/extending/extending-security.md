---
title: Güvenliği Genişletme
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], extending
ms.assetid: a015a040-9fdf-4147-9ea9-f83b570be1d4
ms.openlocfilehash: 2d2f1997534a33f246c85501e66b6aa8a684445f
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50190703"
---
# <a name="extending-security"></a>Güvenliği Genişletme
Yeni talep türlerini ve özel belirteçler uyum sağlamak için Windows Communication Foundation (WCF) güvenlik altyapısı genişletebilirsiniz. Bu bölümdeki konular, size nasıl yapıldığını gösterir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Güvenlik mimarisi](https://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f)  
 WCF güvenlik sistem mimarisi size yol gösterir.  
  
 [Özel Kimlik Bilgileri ve Kimlik Bilgileri Doğrulaması](../../../../docs/framework/wcf/extending/custom-credential-and-credential-validation.md)  
 Özel kimlik doğrulama sırasında kimlik modeli nasıl kullanıldığını açıklar.  
  
 [Özel Belirteçler](../../../../docs/framework/wcf/extending/custom-tokens.md)  
 Bir güvenlik belirteci hizmeti (STS) öğesinden verilen belirteçler genellikle SAML belirteçlerini cihazlardır. Bu konuda, özel bir belirteç türünün nasıl oluşturulacağı açıklanmaktadır.  
  
 [Özel Yetkilendirme](../../../../docs/framework/wcf/extending/custom-authorization.md)  
 Özel yetkilendirme uygulanacağını açıklar.  
  
 [Bir Hizmetin Kimliğini Kimlik Doğrulama için Geçersiz Kılma](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md)  
 Kimlik doğrulaması için bir hizmetin kimliğini geçersiz kılmayı açıklar.  
  
 [Nasıl yapılır: Özel İstemci Kimliği Doğrulayıcı Oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md)  
 Özel uç nokta kimlik doğrulama işlemi gösterilmektedir.  
  
 [Nasıl Yapılır: İmzalama ve Şifreleme için Ayrı X.509 Sertifikaları Kullanma](../../../../docs/framework/wcf/extending/how-to-use-separate-x-509-certificates-for-signing-and-encryption.md)  
 İletiler genellikle imzalı ve tek bir sertifika ile şifrelenir. Bu konu açıklar nasıl iki sertifika, gerekli olduğunda kullanılabilir.  
  
 [Nasıl yapılır: Bir X.509 Sertifikasının Şifreleme Sağlayıcısını Değiştirme](../../../../docs/framework/wcf/extending/change-cryptographic-provider-x509-certificate-private-key.md)  
 Nasıl bir X.509 sertifikasının özel anahtar sağlamak için kullanılan şifreleme sağlayıcısını değiştirme ve Windows Communication Foundation (WCF) altyapısına sağlayıcı tümleştirmek nasıl açıklar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Güvenlik](../../../../docs/framework/wcf/feature-details/security.md)  
  
 [Temel WCF Programlama](../../../../docs/framework/wcf/basic-wcf-programming.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenliğe Genel Bakış](../../../../docs/framework/wcf/feature-details/security-overview.md)
