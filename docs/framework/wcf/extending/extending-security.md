---
title: Güvenliği Genişletme
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], extending
ms.assetid: a015a040-9fdf-4147-9ea9-f83b570be1d4
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 6ba6df24163064ee65c563253fa56a1ec574cffc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="extending-security"></a>Güvenliği Genişletme
Yeni talep türlerini ve özel belirteçler uyum sağlamak için Windows Communication Foundation (WCF) güvenlik altyapısı genişletebilirsiniz. Bu bölümdeki konular, bunun nasıl yapılacağı gösterilmektedir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Güvenlik mimarisi](http://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f)  
 Mimarisi anlatılmaktadır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] güvenlik sistemi.  
  
 [Özel Kimlik Bilgileri ve Kimlik Bilgileri Doğrulaması](../../../../docs/framework/wcf/extending/custom-credential-and-credential-validation.md)  
 Özel kimlik doğrulama sırasında kimlik modeli nasıl kullanıldığını açıklar.  
  
 [Özel Belirteçler](../../../../docs/framework/wcf/extending/custom-tokens.md)  
 Verilen belirteçler bir güvenlik belirteci hizmeti (STS) normal SAML belirteçleri uygulanır. Bu konuda bir özel belirteç türünün nasıl oluşturulacağı açıklanmaktadır.  
  
 [Özel Yetkilendirme](../../../../docs/framework/wcf/extending/custom-authorization.md)  
 Özel yetkilendirme uygulamak açıklanmaktadır.  
  
 [Bir Hizmetin Kimliğini Kimlik Doğrulama için Geçersiz Kılma](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md)  
 Kimlik doğrulaması için bir hizmetin kimliğini geçersiz kılmayı açıklar.  
  
 [Nasıl yapılır: Özel İstemci Kimliği Doğrulayıcı Oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md)  
 Özel uç noktası kimlik doğrulamak gösterilmiştir.  
  
 [Nasıl Yapılır: İmzalama ve Şifreleme için Ayrı X.509 Sertifikaları Kullanma](../../../../docs/framework/wcf/extending/how-to-use-separate-x-509-certificates-for-signing-and-encryption.md)  
 İletiler genellikle imzalı ve tek bir sertifika ile şifrelenir. Bu konu nasıl iki sertifika açıklar, gerekli olduğunda kullanılabilir.  
  
 [Nasıl yapılır: Bir X.509 Sertifikasının Şifreleme Sağlayıcısını Değiştirme](../../../../docs/framework/wcf/extending/change-cryptographic-provider-x509-certificate-private-key.md)  
 Bir X.509 sertifikasının özel anahtarı sağlamak için kullanılan şifreleme sağlayıcısını değiştirme ve Windows Communication Foundation (WCF) Framework'e sağlayıcı tümleştirme açıklanmaktadır.  
  
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
