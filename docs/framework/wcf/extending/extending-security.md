---
title: "Güvenliği Genişletme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: security [WCF], extending
ms.assetid: a015a040-9fdf-4147-9ea9-f83b570be1d4
caps.latest.revision: "23"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: a3950b156ede806382bbe4e013db5d94a8b20a23
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="extending-security"></a>Güvenliği Genişletme
Yeni talep türlerini ve özel belirteçler uyum sağlamak için güvenlik altyapısı genişletebilirsiniz [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. Bu bölümdeki konular, bunun nasıl yapılacağı gösterilmektedir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Güvenlik mimarisi](http://msdn.microsoft.com/en-us/16593476-d36a-408d-808c-ae6fd483e28f)  
 Mimarisi anlatılmaktadır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] güvenlik sistemi.  
  
 [Özel kimlik bilgileri ve kimlik bilgileri doğrulaması](../../../../docs/framework/wcf/extending/custom-credential-and-credential-validation.md)  
 Özel kimlik doğrulama sırasında kimlik modeli nasıl kullanıldığını açıklar.  
  
 [Özel belirteçler](../../../../docs/framework/wcf/extending/custom-tokens.md)  
 Verilen belirteçler bir güvenlik belirteci hizmeti (STS) normal SAML belirteçleri uygulanır. Bu konuda bir özel belirteç türünün nasıl oluşturulacağı açıklanmaktadır.  
  
 [Özel yetkilendirme](../../../../docs/framework/wcf/extending/custom-authorization.md)  
 Özel yetkilendirme uygulamak açıklanmaktadır.  
  
 [Kimlik doğrulaması için bir hizmetin kimliğini geçersiz kılma](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md)  
 Kimlik doğrulaması için bir hizmetin kimliğini geçersiz kılmayı açıklar.  
  
 [Nasıl yapılır: Özel İstemci Kimliği Doğrulayıcı oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md)  
 Özel uç noktası kimlik doğrulamak gösterilmiştir.  
  
 [Nasıl yapılır: ayrı X.509 sertifikaları imzalamak için kullanın ve şifreleme](../../../../docs/framework/wcf/extending/how-to-use-separate-x-509-certificates-for-signing-and-encryption.md)  
 İletiler genellikle imzalı ve tek bir sertifika ile şifrelenir. Bu konu nasıl iki sertifika açıklar, gerekli olduğunda kullanılabilir.  
  
 [Nasıl yapılır: bir X.509 sertifikasının özel anahtar şifreleme sağlayıcısını değiştirme](../../../../docs/framework/wcf/extending/change-cryptographic-provider-x509-certificate-private-key.md)  
 Bir X.509 sertifikasının özel anahtarı sağlamak için kullanılan şifreleme sağlayıcısını değiştirme ve sağlayıcısını tümleştirme açıklanmaktadır [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] framework.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Güvenlik](../../../../docs/framework/wcf/feature-details/security.md)  
  
 [Temel WCF programlama](../../../../docs/framework/wcf/basic-wcf-programming.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenlik genel bakış](../../../../docs/framework/wcf/feature-details/security-overview.md)
