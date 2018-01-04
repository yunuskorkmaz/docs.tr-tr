---
title: "Ortak Güvenlik Senaryoları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: security [WCF], scenarios
ms.assetid: 201923b5-5162-4a8a-8d4c-e7bd242748d5
caps.latest.revision: "18"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: d8881768d66e95ce1391ce1be1663bdc3107a347
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="common-security-scenarios"></a>Ortak Güvenlik Senaryoları
Bu bölümdeki konular, bir dizi olası istemci ve hizmet güvenlik yapılandırması katalog. Yapılandırmalarını bir dizi etkene göre farklılık gösterir. Örneğin, bir hizmet veya istemci intranet üzerinde olup ya da güvenlik olup Windows veya taşıma (Örneğin HTTPS) tarafından sağlanır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [İnternet Güvenli Olmayan Hizmet ve İstemci](../../../../docs/framework/wcf/feature-details/internet-unsecured-client-and-service.md)  
 Bir ortak, güvenli olmayan bir istemci ve hizmet örneği.  
  
 [İntranet Güvenli Olmayan Hizmet ve İstemci](../../../../docs/framework/wcf/feature-details/intranet-unsecured-client-and-service.md)  
 Temel bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hizmet geliştirilen özel bir ağda güvenli için bilgi sağlamak için bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulama.  
  
 [Temel Kimlik Doğrulama ile Aktarım Güvenliği](../../../../docs/framework/wcf/feature-details/transport-security-with-basic-authentication.md)  
 Uygulama istemcilerinin özel kimlik doğrulaması kullanarak oturum olanak tanır.  
  
 [Windows Kimlik Doğrulaması ile Aktarım Güvenliği](../../../../docs/framework/wcf/feature-details/transport-security-with-windows-authentication.md)  
 Bir istemci ve hizmet Windows security tarafından korunan gösterir.  
  
 [Anonim İstemci ile Aktarım Güvenliği](../../../../docs/framework/wcf/feature-details/transport-security-with-an-anonymous-client.md)  
 Bu senaryo, gizliliği ve bütünlük sağlamak için Aktarım güvenliği (Örneğin HTTPS) kullanır.  
  
 [Sertifika Kimlik Doğrulama ile Aktarım Güvenliği](../../../../docs/framework/wcf/feature-details/transport-security-with-certificate-authentication.md)  
 Bir istemci ve hizmet sertifikası ile güvenli gösterir.  
  
 [Anonim İstemci ile İleti Güvenliği](../../../../docs/framework/wcf/feature-details/message-security-with-an-anonymous-client.md)  
 Bir istemci ve hizmet tarafından güvenli hale getirilmiş gösterir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ileti güvenlik.  
  
 [Kullanıcı Adı İstemcisi ile İleti Güvenliği](../../../../docs/framework/wcf/feature-details/message-security-with-a-user-name-client.md)  
 İstemci, bir etki alanı kullanıcı adı ve parola kullanarak oturum istemcilerin bir Windows Forms uygulamasıdır.  
  
 [Sertifika İstemcisi ile İleti Güvenliği](../../../../docs/framework/wcf/feature-details/message-security-with-a-certificate-client.md)  
 Sunucu sertifikalarına sahip olduğunu ve her bir istemci bir sertifikaya sahip. Bir güvenlik bağlamı, Aktarım Katmanı Güvenliği (TLS) anlaşması ile kurulur.  
  
 [Windows İstemcisi ile İleti Güvenliği](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client.md)  
 Sertifika istemcisi çeşidi. Sunucu sertifikalarına sahip olduğunu ve her bir istemci bir sertifikaya sahip. Bir güvenlik bağlamı TLS anlaşması ile kurulur.  
  
 [Windows İstemcisi ile Kimlik Bilgileri Görüşmesi Olmadan İleti Güvenliği](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client-without-credential-negotiation.md)  
 Bir istemci ve Kerberos etki alanı tarafından güvenli hale getirilmiş hizmet gösterir.  
  
 [Karşılıklı Sertifikalar ile İleti Güvenliği](../../../../docs/framework/wcf/feature-details/message-security-with-mutual-certificates.md)  
 Sunucu sertifikalarına sahip olduğunu ve her bir istemci bir sertifikaya sahip. Sunucu sertifikası uygulama ile dağıtılmış ve bant dışı kullanılabilir.  
  
 [Verilen Belirteçlerle İleti Güvenliği](../../../../docs/framework/wcf/feature-details/message-security-with-issued-tokens.md)  
 Bağımsız etki alanları arasında güven kurulması etkinleştirir federe güvenlik.  
  
 [Güvenilir Alt Sistem](../../../../docs/framework/wcf/feature-details/trusted-subsystem.md)  
 Bir istemci bir ağ üzerinden dağıtılan bir veya daha fazla Web Hizmetleri erişir. Web Hizmetleri güvenli hale getirilmelidir ek kaynaklar (örneğin, veritabanları veya diğer Web Hizmetleri) erişin.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Yetkilendirme](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
 [Güvenliğe Genel Bakış](../../../../docs/framework/wcf/feature-details/security-overview.md)  
  
 [Güvenlik](../../../../docs/framework/wcf/feature-details/security.md)  
  
 [Bağlamalar ve Güvenlik](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
  
 [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
  
 [Kimlik Doğrulaması](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
 [Yetkilendirme](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
 [Federasyon ve Verilen Belirteçler](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
  
 [Denetim](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenlik Kılavuzu ve En İyi Uygulamalar](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)  
 [Windows Server App Fabric için güvenlik modeli](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
