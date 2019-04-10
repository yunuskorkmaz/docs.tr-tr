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
ms.openlocfilehash: 3b1ff700010f471a4d9be117f363083b6cbed493
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59210639"
---
# <a name="custom-credential-and-credential-validation"></a>Özel Kimlik Bilgileri ve Kimlik Bilgileri Doğrulaması
Güvenlik Windows Communication Foundation (WCF) hizmet ve istemcileri arasında kimlik bilgilerinin exchange temel alır. Çoğu güvenlik senaryoları Windows (Kerberos), kullanıcı adı ve parolalar ve sertifikalar gibi ortak kimlik bilgisi türlerinin kullanarak karşılanabilir. Ancak, yeni bir kimlik bilgisi türü gerekiyorsa, bu bölümdeki konular, yeni türleri doğrulamak ve işlemek nasıl açıklanmaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Özel Bir Sertifika Doğrulayıcı Kullanan Bir Hizmet Oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 WCF doğrulama devralarak özelleştirmek nasıl açıklar <xref:System.IdentityModel.Selectors.X509CertificateValidator> sınıfı.  
  
 [İzlenecek yol: Özel İstemci ve Hizmet Kimlik Bilgileri Oluşturma](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)  
 Nasıl genişleteceğinizi gösterir <xref:System.ServiceModel.Description.ClientCredentials> ve <xref:System.ServiceModel.Description.ServiceCredentials> sınıfları yeni uyum sağlamak için kimlik bilgisi türü. Özel kimlik bilgisi türlerinin oluşturulmasını sağlayan konuları bir dizi içinde ilk budur.  
  
 [Nasıl yapılır: Özel Güvenlik Belirteci Sağlayıcı Oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
 Yeni kimlik bilgisi türlerinin işlemek ve kimlik bilgisi için yeni belirteçleri döndürmek için bir güvenlik belirteci sağlayıcı oluşturma açıklanmaktadır. Serinin ikinci bölümüne budur.  
  
 [Nasıl yapılır: Özel Güvenlik Belirteci Kimlik Doğrulayıcı Oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
 Yeni bir kimlik bilgisi türü kimlik doğrulaması için özel bir kimlik doğrulayıcı oluşturma açıklanmaktadır. Bu, serideki üçüncü konudur.  
  
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
 [Kimlik doğrulaması](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
 [Federasyon ve Verilen Belirteçler](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
  
 [Yetkilendirme](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenlik](../../../../docs/framework/wcf/feature-details/security.md)
