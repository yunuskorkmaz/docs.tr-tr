---
title: Ortak Güvenlik Senaryoları
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], scenarios
ms.assetid: 201923b5-5162-4a8a-8d4c-e7bd242748d5
ms.openlocfilehash: cfd29f8cae8ac362a5fa1709864dce4ae11b5af6
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558894"
---
# <a name="common-security-scenarios"></a>Ortak Güvenlik Senaryoları
Bu bölümdeki konularda, bir dizi olası istemci ve hizmet güvenlik yapılandırması kataloglayın. Konfigürasyonlar bir dizi etkene göre farklılık gösterir. Örneğin, bir hizmet veya istemcinin intranette olup olmadığı ya da güvenliğin Windows ya da taşıma (HTTPS gibi) tarafından sağlandığını belirtir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [İnternet Güvenli Olmayan Hizmet ve İstemci](internet-unsecured-client-and-service.md)  
 Ortak, güvenli olmayan bir istemci ve hizmet örneği.  
  
 [Intranet Güvenli Olmayan Hizmet ve İstemci](intranet-unsecured-client-and-service.md)  
 Bir WCF uygulamasına güvenli bir özel ağ hakkında bilgi sağlamak için geliştirilen temel bir Windows Communication Foundation (WCF) hizmetidir.  
  
 [Temel Kimlik Doğrulama ile Taşıma Güvenliği](transport-security-with-basic-authentication.md)  
 Uygulama, istemcilerin özel kimlik doğrulaması kullanarak oturum açmasına olanak tanır.  
  
 [Windows Kimlik Doğrulama ile Taşıma Güvenliği](transport-security-with-windows-authentication.md)  
 Windows güvenliği tarafından güvenliği sağlanmış bir istemciyi ve hizmeti gösterir.  
  
 [Anonim İstemci ile Aktarım Güvenliği](transport-security-with-an-anonymous-client.md)  
 Bu senaryo gizlilik ve bütünlüğü sağlamak için taşıma güvenliği (HTTPS gibi) kullanır.  
  
 [Sertifika Kimlik Doğrulama ile Taşıma Güvenliği](transport-security-with-certificate-authentication.md)  
 Bir sertifika tarafından güvenliği sağlanmış bir istemciyi ve hizmeti gösterir.  
  
 [Anonim İstemci ile İleti Güvenliği](message-security-with-an-anonymous-client.md)  
 WCF ileti güvenliği tarafından güvenli hale getirilmiş bir istemciyi ve hizmeti gösterir.  
  
 [Kullaıcı Adı İstemcisi ile İleti Güvenliği](message-security-with-a-user-name-client.md)  
 İstemci, istemcilerin bir etki alanı Kullanıcı adı ve parola kullanarak oturum açmasına izin veren bir Windows Forms uygulamasıdır.  
  
 [Sertifika İstemcisi ile İleti Güvenliği](message-security-with-a-certificate-client.md)  
 Sunucularda sertifikalar vardır ve her bir istemcinin sertifikası vardır. Aktarım Katmanı Güvenliği (TLS) anlaşması aracılığıyla bir güvenlik bağlamı oluşturulur.  
  
 [Windows İstemcisi ile İleti Güvenliği](message-security-with-a-windows-client.md)  
 Sertifika istemcisinin bir çeşitlemesi. Sunucularda sertifikalar vardır ve her bir istemcinin sertifikası vardır. TLS anlaşması ile bir güvenlik bağlamı oluşturulur.  
  
 [Windows İstemcisi ile Kimlik Bilgileri Görüşmesi Olmadan İleti Güvenliği](message-security-with-a-windows-client-without-credential-negotiation.md)  
 Kerberos etki alanı tarafından güvenliği sağlanmış bir istemciyi ve hizmeti gösterir.  
  
 [Karşılıklı Sertifikalar ile İleti Güvenliği](message-security-with-mutual-certificates.md)  
 Sunucularda sertifikalar vardır ve her bir istemcinin sertifikası vardır. Sunucu sertifikası uygulamayla birlikte dağıtılır ve bant dışı kullanılabilir.  
  
 [Verilen Belirteçlerle İleti Güvenliği](message-security-with-issued-tokens.md)  
 Bağımsız etki alanları arasında güven kurulmasını sağlayan Federe güvenlik.  
  
 [Güvenilir Alt Sistem](trusted-subsystem.md)  
 İstemci bir ağ üzerinde dağıtılan bir veya daha fazla Web hizmetine erişir. Web Hizmetleri, güvenli olması gereken ek kaynaklara (veritabanları veya diğer Web Hizmetleri gibi) erişir.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Yetkilendirme](authorization-in-wcf.md)  
  
 [Güvenliğe genel bakış](security-overview.md)  
  
 [Güvenlik](security.md)  
  
 [Bağlamalar ve Güvenlik](bindings-and-security.md)  
  
 [Hizmet ve İstemcileri Güvenli Hale Getirme](securing-services-and-clients.md)  
  
 [Kimlik Doğrulaması](authentication-in-wcf.md)  
  
 [Yetkilendirme](authorization-in-wcf.md)  
  
 [Federasyon ve Verilen Belirteçler](federation-and-issued-tokens.md)  
  
 [Denetim](auditing-security-events.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenlik Kılavuzu ve En İyi Uygulamalar](security-guidance-and-best-practices.md)
- [Windows Server App Fabric için güvenlik modeli](/previous-versions/appfabric/ee677202(v=azure.10))
