---
title: Özel Kimlik Bilgileri ve Kimlik Bilgileri Doğrulaması
ms.date: 03/30/2017
helpviewer_keywords:
- credentials [WCF], custom
- credentials [WCF]
- custom credentials [WCF]
- credential validation [WCF]
- credentials [WCF], validation
ms.assetid: da831bec-e281-4d44-b343-437b5eef688e
ms.openlocfilehash: 5f2909bb088a5f3d3203fe3c9e24b2df3450aa3f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96257834"
---
# <a name="custom-credential-and-credential-validation"></a>Özel Kimlik Bilgileri ve Kimlik Bilgileri Doğrulaması

Windows Communication Foundation (WCF) güvenliği, hizmetler ve istemciler arasındaki kimlik bilgilerinin değişimini temel alır. Çoğu güvenlik senaryosu Windows (Kerberos), Kullanıcı adı ve parolalar ve sertifikalar gibi ortak kimlik bilgisi türleri kullanılarak karşılanabilir. Ancak, yeni bir kimlik bilgisi türü gerekliyse, bu bölümdeki konular yeni türlerin nasıl işleneceğini ve doğrulanacağını açıklamaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  

 [Nasıl yapılır: Özel Bir Sertifika Doğrulayıcı Kullanan Bir Hizmet Oluşturma](how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 Sınıfından devralarak WCF doğrulamasının nasıl özelleştirileceğini açıklar <xref:System.IdentityModel.Selectors.X509CertificateValidator> .  
  
 [İzlenecek yol: Özel İstemci ve Hizmet Kimlik Bilgileri Oluşturma](walkthrough-creating-custom-client-and-service-credentials.md)  
 <xref:System.ServiceModel.Description.ClientCredentials>Ve <xref:System.ServiceModel.Description.ServiceCredentials> sınıflarının yeni kimlik bilgisi türlerini kapsayacak şekilde nasıl genişletileceğini gösterir. Bu, ilk olarak özel kimlik bilgisi türlerinin oluşturulmasını sağlayan bir dizi konuda yer alan bir konu sayısıdır.  
  
 [Nasıl yapılır: Özel Güvenlik Belirteci Sağlayıcı Oluşturma](how-to-create-a-custom-security-token-provider.md)  
 Yeni kimlik bilgisi türlerini işlemek ve kimlik bilgileri için yeni belirteçleri döndürmek üzere bir güvenlik belirteci sağlayıcısının nasıl oluşturulacağını açıklar. Bu, serideki ikinci konudur.  
  
 [Nasıl yapılır: Özel Güvenlik Belirteci Kimlik Doğrulayıcı Oluşturma](how-to-create-a-custom-security-token-authenticator.md)  
 Yeni bir kimlik bilgisi türünün kimliğini doğrulamak için özel bir Authenticator oluşturmayı açıklar. Bu, serideki üçüncü konudur.  
  
## <a name="reference"></a>Başvuru  

 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Selectors.X509CertificateValidator>  
  
 <xref:System.ServiceModel.Description.ClientCredentials>  
  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
  
## <a name="related-sections"></a>İlgili Bölümler  

 [Kimlik Doğrulaması](../feature-details/authentication-in-wcf.md)  
  
 [Federasyon ve Verilen Belirteçler](../feature-details/federation-and-issued-tokens.md)  
  
 [Yetkilendirme](../feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenlik](../feature-details/security.md)
