---
title: WCF'de Kimlik Doğrulama
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF]
- security [WCF], authentication
ms.assetid: 9254d873-843d-4c6e-bea4-8184ac3e44f4
ms.openlocfilehash: abe7aff025207ad8bdf8657daba3584e6a1b2e7f
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964690"
---
# <a name="authentication-in-wcf"></a>WCF'de Kimlik Doğrulama
Aşağıdaki konularda, kimlik doğrulaması (örneğin, Windows kimlik doğrulaması, X. 509.440 sertifikaları ve Kullanıcı adı ve parolalar) sağlayan Windows Communication Foundation (WCF) içinde çeşitli mekanizmalar gösterilmektedir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: ASP.NET Üyelik Sağlayıcısını Kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)  
 ASP.NET özellikleri bir üyelik ve rol sağlayıcısı, kimlik doğrulaması için Kullanıcı adı/parola çiftlerini depolamak üzere bir veritabanı ve yetkilendirme için Kullanıcı rolleri içerir. Bu konuda, WCF hizmetlerinin, kullanıcıların kimliğini doğrulamak ve yetkilendirmek için aynı veritabanını nasıl kullanabileceği açıklanmaktadır.  
  
 [Nasıl yapılır: Özel Bir Kullanıcı Adı ve Parola Doğrulayıcı Kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md)  
 Özel bir Kullanıcı adı/parola doğrulayıcının nasıl tümleştirileceğini gösterir.  
  
 [Kimlik Doğrulama ile Hizmet Kimliği](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 Bir istemci, ek bir güvenlik önlemi olarak hizmetin beklenen *kimliğini* belirterek hizmetin kimliğini doğrulayabilir. Beklenen kimlik ve hizmet tarafından döndürülen kimlik eşleşmiyorsa, kimlik doğrulaması başarısız olur.  
  
 [Güvenlik Görüşmeleri ve Zaman Aşımları](../../../../docs/framework/wcf/feature-details/security-negotiation-and-timeouts.md)  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> sınıfında <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> özelliğinin nasıl kullanılacağını açıklar.  
  
 [Windows Kimlik Doğrulama Hatalarını Ayıklama](../../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)  
 Windows kimlik doğrulaması kullanılırken karşılaşılan yaygın sorunlara odaklanır.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Ortak Güvenlik Senaryoları](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenliğe Genel Bakış](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Windows Server App Fabric için güvenlik modeli](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
