---
title: "Özel Kimlik Bilgileri ve Kimlik Bilgileri Doğrulaması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- credentials [WCF], custom
- credentials [WCF]
- custom credentials [WCF]
- credential validation [WCF]
- credentials [WCF], validation
ms.assetid: da831bec-e281-4d44-b343-437b5eef688e
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c3ca7726f3a6a0c5faaab1cbbd0b31125ce0c1d6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="custom-credential-and-credential-validation"></a>Özel Kimlik Bilgileri ve Kimlik Bilgileri Doğrulaması
Güvenlik [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] exchange Hizmetleri ve istemciler arasında kimlik bilgilerinin temel alır. Çoğu güvenlik senaryoları Windows (Kerberos), kullanıcı adı ve parolaları ve sertifikaları gibi ortak kimlik bilgisi türlerini kullanarak karşılanabilir. Yeni bir kimlik bilgisi türünü gerekliyse, ancak, bu bölümdeki konular, işlemek ve yeni türleri doğrulamak açıklanmaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: özel bir sertifika Doğrulayıcı kullanan bir hizmet oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 Nasıl özelleştirileceği açıklanır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] içinden devralma tarafından doğrulama <xref:System.IdentityModel.Selectors.X509CertificateValidator> sınıfı.  
  
 [İzlenecek yol: Özel istemci ve hizmet kimlik bilgileri oluşturma](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)  
 Nasıl genişletileceğini gösterir <xref:System.ServiceModel.Description.ClientCredentials> ve <xref:System.ServiceModel.Description.ServiceCredentials> sınıfları yeni uyum sağlamak için kimlik bilgisi türü. Bu özel kimlik bilgisi türlerinin oluşturulmasını sağlamak konuları serisinde ilktir.  
  
 [Nasıl yapılır: özel güvenlik belirteci sağlayıcı oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
 Yeni kimlik bilgisi türlerinin işlemek ve kimlik bilgisi için yeni belirteçleri dönmek için bir güvenlik belirteci sağlayıcı oluşturma açıklanmaktadır. Bu serideki ikinci konudur.  
  
 [Nasıl yapılır: özel güvenlik belirteci kimlik doğrulayıcı oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
 Yeni bir kimlik bilgisi türü kimlik doğrulaması yapmak için özel bir kimlik doğrulayıcı oluşturma açıklanmaktadır. Bu serideki üçüncü konudur.  
  
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
  
 [Federasyon ve verilen belirteçler](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
  
 [Yetkilendirme](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenlik](../../../../docs/framework/wcf/feature-details/security.md)
