---
title: Ortak Güvenlik Senaryoları
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], scenarios
ms.assetid: 201923b5-5162-4a8a-8d4c-e7bd242748d5
ms.openlocfilehash: 578ec2d7d5abe1285007ad22d8bacd69e695b1d3
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964278"
---
# <a name="common-security-scenarios"></a>Ortak Güvenlik Senaryoları
Bu bölümdeki konularda, bir dizi olası istemci ve hizmet güvenlik yapılandırması kataloglayın. Konfigürasyonlar bir dizi etkene göre farklılık gösterir. Örneğin, bir hizmet veya istemcinin intranette olup olmadığı ya da güvenliğin Windows ya da taşıma (HTTPS gibi) tarafından sağlandığını belirtir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [İnternet Güvenli Olmayan Hizmet ve İstemci](../../../../docs/framework/wcf/feature-details/internet-unsecured-client-and-service.md)  
 Ortak, güvenli olmayan bir istemci ve hizmet örneği.  
  
 [İntranet Güvenli Olmayan Hizmet ve İstemci](../../../../docs/framework/wcf/feature-details/intranet-unsecured-client-and-service.md)  
 Bir WCF uygulamasına güvenli bir özel ağ hakkında bilgi sağlamak için geliştirilen temel bir Windows Communication Foundation (WCF) hizmetidir.  
  
 [Temel Kimlik Doğrulama ile Aktarım Güvenliği](../../../../docs/framework/wcf/feature-details/transport-security-with-basic-authentication.md)  
 Uygulama, istemcilerin özel kimlik doğrulaması kullanarak oturum açmasına olanak tanır.  
  
 [Windows Kimlik Doğrulaması ile Aktarım Güvenliği](../../../../docs/framework/wcf/feature-details/transport-security-with-windows-authentication.md)  
 Windows güvenliği tarafından güvenliği sağlanmış bir istemciyi ve hizmeti gösterir.  
  
 [Anonim İstemci ile Aktarım Güvenliği](../../../../docs/framework/wcf/feature-details/transport-security-with-an-anonymous-client.md)  
 Bu senaryo gizlilik ve bütünlüğü sağlamak için taşıma güvenliği (HTTPS gibi) kullanır.  
  
 [Sertifika Kimlik Doğrulama ile Aktarım Güvenliği](../../../../docs/framework/wcf/feature-details/transport-security-with-certificate-authentication.md)  
 Bir sertifika tarafından güvenliği sağlanmış bir istemciyi ve hizmeti gösterir.  
  
 [Anonim İstemci ile İleti Güvenliği](../../../../docs/framework/wcf/feature-details/message-security-with-an-anonymous-client.md)  
 WCF ileti güvenliği tarafından güvenli hale getirilmiş bir istemciyi ve hizmeti gösterir.  
  
 [Kullanıcı Adı İstemcisi ile İleti Güvenliği](../../../../docs/framework/wcf/feature-details/message-security-with-a-user-name-client.md)  
 İstemci, istemcilerin bir etki alanı Kullanıcı adı ve parola kullanarak oturum açmasına izin veren bir Windows Forms uygulamasıdır.  
  
 [Sertifika İstemcisi ile İleti Güvenliği](../../../../docs/framework/wcf/feature-details/message-security-with-a-certificate-client.md)  
 Sunucularda sertifikalar vardır ve her bir istemcinin sertifikası vardır. Aktarım Katmanı Güvenliği (TLS) anlaşması aracılığıyla bir güvenlik bağlamı oluşturulur.  
  
 [Windows İstemcisi ile İleti Güvenliği](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client.md)  
 Sertifika istemcisinin bir çeşitlemesi. Sunucularda sertifikalar vardır ve her bir istemcinin sertifikası vardır. TLS anlaşması ile bir güvenlik bağlamı oluşturulur.  
  
 [Windows İstemcisi ile Kimlik Bilgileri Görüşmesi Olmadan İleti Güvenliği](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client-without-credential-negotiation.md)  
 Kerberos etki alanı tarafından güvenliği sağlanmış bir istemciyi ve hizmeti gösterir.  
  
 [Karşılıklı Sertifikalar ile İleti Güvenliği](../../../../docs/framework/wcf/feature-details/message-security-with-mutual-certificates.md)  
 Sunucularda sertifikalar vardır ve her bir istemcinin sertifikası vardır. Sunucu sertifikası uygulamayla birlikte dağıtılır ve bant dışı kullanılabilir.  
  
 [Verilen Belirteçlerle İleti Güvenliği](../../../../docs/framework/wcf/feature-details/message-security-with-issued-tokens.md)  
 Bağımsız etki alanları arasında güven kurulmasını sağlayan Federe güvenlik.  
  
 [Güvenilir Alt Sistem](../../../../docs/framework/wcf/feature-details/trusted-subsystem.md)  
 İstemci bir ağ üzerinde dağıtılan bir veya daha fazla Web hizmetine erişir. Web Hizmetleri, güvenli olması gereken ek kaynaklara (veritabanları veya diğer Web Hizmetleri gibi) erişir.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Yetkilendirme](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
 [Güvenliğe Genel Bakış](../../../../docs/framework/wcf/feature-details/security-overview.md)  
  
 [Security](../../../../docs/framework/wcf/feature-details/security.md)  
  
 [Bağlamalar ve Güvenlik](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
  
 [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
  
 [Kimlik Doğrulaması](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
 [Yetkilendirme](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
 [Federasyon ve Verilen Belirteçler](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
  
 [Denetim](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenlik Kılavuzu ve En İyi Uygulamalar](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)
- [Windows Server App Fabric için güvenlik modeli](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
