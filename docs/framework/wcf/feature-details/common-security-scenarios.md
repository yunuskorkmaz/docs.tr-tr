---
title: Ortak Güvenlik Senaryoları
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], scenarios
ms.assetid: 201923b5-5162-4a8a-8d4c-e7bd242748d5
ms.openlocfilehash: af58d6b529fba32380bedb9a892a2b1fd4807d96
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59199277"
---
# <a name="common-security-scenarios"></a>Ortak Güvenlik Senaryoları
Bu bölümdeki konular, katalog hizmeti güvenlik yapılandırmalarını ve olası istemci bir numarası. Yapılandırmaları bir dizi etkene göre değişir. Örneğin, bir hizmet veya istemci intranet üzerinde olup veya olup Windows ya da (Örneğin HTTPS) aktarım güvenliği sağlanır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [İnternet Güvenli Olmayan Hizmet ve İstemci](../../../../docs/framework/wcf/feature-details/internet-unsecured-client-and-service.md)  
 Genel, güvenli olmayan bir istemci ve hizmet örneği.  
  
 [İntranet Güvenli Olmayan Hizmet ve İstemci](../../../../docs/framework/wcf/feature-details/intranet-unsecured-client-and-service.md)  
 WCF uygulaması için özel bir güvenli ağ üzerinden bilgi sağlamak için temel bir Windows Communication Foundation (WCF) hizmeti geliştirdi.  
  
 [Temel Kimlik Doğrulama ile Aktarım Güvenliği](../../../../docs/framework/wcf/feature-details/transport-security-with-basic-authentication.md)  
 Uygulamaya özel kimlik doğrulaması kullanarak oturum etmesine olanak tanır.  
  
 [Windows Kimlik Doğrulaması ile Aktarım Güvenliği](../../../../docs/framework/wcf/feature-details/transport-security-with-windows-authentication.md)  
 Bir istemci ve hizmet Windows güvenlik güvenli gösterir.  
  
 [Anonim İstemci ile Aktarım Güvenliği](../../../../docs/framework/wcf/feature-details/transport-security-with-an-anonymous-client.md)  
 Bu senaryo, gizliliği ve bütünlüğü sağlamak için Aktarım güvenliği (Örneğin HTTPS) kullanır.  
  
 [Sertifika Kimlik Doğrulama ile Aktarım Güvenliği](../../../../docs/framework/wcf/feature-details/transport-security-with-certificate-authentication.md)  
 Bir istemci ve hizmet güvenliği bir sertifika ile sağlanan gösterir.  
  
 [Anonim İstemci ile İleti Güvenliği](../../../../docs/framework/wcf/feature-details/message-security-with-an-anonymous-client.md)  
 Bir istemci ve hizmet tarafından WCF ileti güvenliğini güvenli gösterir.  
  
 [Kullanıcı Adı İstemcisi ile İleti Güvenliği](../../../../docs/framework/wcf/feature-details/message-security-with-a-user-name-client.md)  
 İstemci istemciler, bir etki alanı kullanıcı adı ve parola kullanarak oturum açmasına izin veren bir Windows Forms uygulamasıdır.  
  
 [Sertifika İstemcisi ile İleti Güvenliği](../../../../docs/framework/wcf/feature-details/message-security-with-a-certificate-client.md)  
 Sunucuları sertifikaları ve her bir istemciye bir sertifika gerekir. Bir güvenlik bağlamı anlaşması ile Aktarım Katmanı Güvenliği (TLS) oluşturulur.  
  
 [Windows İstemcisi ile İleti Güvenliği](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client.md)  
 Sertifika istemcisi çeşitlemesi. Sunucuları sertifikaları ve her bir istemciye bir sertifika gerekir. Bir güvenlik bağlamı TLS anlaşması ile oluşturulur.  
  
 [Windows İstemcisi ile Kimlik Bilgileri Görüşmesi Olmadan İleti Güvenliği](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client-without-credential-negotiation.md)  
 Bir istemci ve hizmet güvenli bir Kerberos etki alanı tarafından gösterilir.  
  
 [Karşılıklı Sertifikalar ile İleti Güvenliği](../../../../docs/framework/wcf/feature-details/message-security-with-mutual-certificates.md)  
 Sunucuları sertifikaları ve her bir istemciye bir sertifika gerekir. Sunucu sertifikası ile uygulama dağıtılır ve bant dışı kullanılabilir.  
  
 [Verilen Belirteçlerle İleti Güvenliği](../../../../docs/framework/wcf/feature-details/message-security-with-issued-tokens.md)  
 Bağımsız bir etki alanı arasında güven kurulması sağlayan birleşik güvenliği.  
  
 [Güvenilir Alt Sistem](../../../../docs/framework/wcf/feature-details/trusted-subsystem.md)  
 Bir istemci, bir ağ üzerinden dağıtılan bir veya daha fazla Web Hizmetleri erişir. Web Hizmetleri, korunması gereken ek kaynakları (örneğin, veritabanları veya diğer Web hizmetlerini) erişin.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenlik Kılavuzu ve En İyi Uygulamalar](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)
- [Windows Server AppFabric için güvenlik modeli](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
