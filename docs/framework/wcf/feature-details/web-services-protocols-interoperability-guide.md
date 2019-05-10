---
title: Web Hizmetleri Protokolleri Birlikte Çalışabilirlik Kılavuzu
ms.date: 03/30/2017
ms.assetid: f2981678-ebdb-433d-899b-467f7df95fb2
ms.openlocfilehash: ffa7da4c723a2cd0054f4f79dd22792a9db67068
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648389"
---
# <a name="web-services-protocols-interoperability-guide"></a>Web Hizmetleri Protokolleri Birlikte Çalışabilirlik Kılavuzu
Windows Communication Foundation (WCF) Web Hizmetleri protokolleri sayısı uygular. Çoğu bu protokolleri, bir dizi seçenekleri ve genişletilebilirlik noktaları uygulayan takdirine bağlı olarak sol içerir. Bu konuda, Web Hizmetleri protokolleri WCF uygulayan bir listesini sağlar. Bu bölüm içindeki diğer konular, desteklenen her protokol için uygulama ayrıntıları sağlar.  
  
## <a name="web-services-protocols-implemented-by-wcf"></a>WCF tarafından uygulanan protokoller Web Hizmetleri  
 WCF kanalları üzerinden Web Hizmetleri (WS) altyapı protokolleri için destek sağlar ve Web hizmeti uygulama protokolleri sözleşmeleri özelliği aracılığıyla. Birlikte çalışabilirlik uygulama protokolleri için XML Şeması Tanım Dili (XSD) 1.0 ve Web Hizmetleri Açıklama Dili (WSDL) 1.1 gerçekleştirilir.  
  
 Altyapı protokolleri birlikte çalışabilirlik sağlanır WS - tarafından * belirtimleri. WCF kanalları WS - sayısı için destek sağlar\* altyapı protokoller. WCF kanalları bağlama öğeleri kullanılarak yapılandırılır. Aşağıdaki tablolarda, WS - tam liste içeren\* çeşitli WCF bağlama öğeleri tarafından uygulanan altyapı protokoller.  
  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement> Aşağıdaki tabloda özellikleri destekler.  
  
|Belirtimi/belge|Bağlantı|  
|-----------------------------|----------|  
|HTTP 1.1|[RFC 2616](https://go.microsoft.com/fwlink/?LinkId=90372)|  
|SOAP 1.1 HTTP bağlama|[Basit Nesne Erişim Protokolü (SOAP) 1.1](https://go.microsoft.com/fwlink/?LinkId=90520), Bölüm 7|  
|SOAP 1.2 HTTP bağlama|[SOAP sürüm 1.2 Bölüm 2: Adjuncts (ikinci sürüm)](https://go.microsoft.com/fwlink/?LinkId=95329), Bölüm 7|  
  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> ve <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> belirtimleri aşağıdaki tabloda destekler.  
  
|Belirtimi/belge|Bağlantı|  
|-----------------------------|----------|  
|XML|[Genişletilebilir Biçimlendirme Dili (XML) 1.0 (Dördüncü sürümüdür)](https://go.microsoft.com/fwlink/?LinkId=15139)|  
|SOAP 1.1|[Basit Nesne Erişim Protokolü (SOAP) 1.1](https://go.microsoft.com/fwlink/?LinkId=96687)|  
|SOAP 1.2 Çekirdek|[SOAP sürüm 1.2 Bölüm 1: Framework Mesajlaşma (ikinci sürüm)](https://go.microsoft.com/fwlink/?LinkId=94664)|  
|WS-Addressing 2004/08|[Adresleme (WS-Addressing) Web Hizmetleri](https://go.microsoft.com/fwlink/?LinkId=81239)|  
|Adresleme 1.0 - çekirdek W3C Web Hizmetleri|[Adresleme 1.0 - çekirdek Web Hizmetleri](https://go.microsoft.com/fwlink/?LinkId=96688)|  
|Adresleme 1.0 - SOAP bağlama W3C Web Hizmetleri|[Web Hizmetleri adresleme 1.0 - SOAP bağlama](https://go.microsoft.com/fwlink/?LinkId=96689)|  
|W3C Web adresleme 1.0 - WSDL bağlama * Hizmetleri|[Web Hizmetleri adresleme 1.0 - WSDL bağlama](https://go.microsoft.com/fwlink/?LinkId=96690)|  
|1.0 meta verileri adresleme W3C Web Hizmetleri|[Adresleme 1.0 - meta veri Web Hizmetleri](https://www.w3.org/TR/ws-addr-metadata/)|  
|WSDL SOAP1.1 bağlama|[Web Hizmetleri Açıklama Dili (WSDL) 1.1](https://go.microsoft.com/fwlink/?LinkId=96160)|  
|WSDL SOAP1.2 bağlama|[WSDL 1.1 bağlama uzantısı için SOAP 1.2](https://go.microsoft.com/fwlink/?LinkId=96691)|  
  
 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> Aşağıdaki tabloda özellikleri destekler.  
  
|Belirtimi/belge|Bağlantı|  
|-----------------------------|----------|  
|XOP|[XML ikili paketleme en iyi duruma getirilmiş](https://go.microsoft.com/fwlink/?LinkId=96714)|  
|MTOM + SOAP1.2 bağlama|[SOAP ileti aktarım en iyi duruma getirme mekanizması](https://go.microsoft.com/fwlink/?LinkId=96713)|  
|MTOM SOAP 1.1 bağlama|[SOAP 1.1 bağını MTOM 1.0](https://go.microsoft.com/fwlink/?LinkId=96712)|  
|MTOM WS-PolicyAssertions|Yayımlanacak.|  
  
 <xref:System.ServiceModel.Channels.SecurityBindingElement> Aşağıdaki tabloda özellikleri destekler.  
  
|Belirtimi/belge|Bağlantı|  
|-----------------------------|----------|  
|WSS: SOAP ileti güvenliği 1.0|[Web Hizmetleri güvenlik: SOAP ileti güvenliği 1.0](https://go.microsoft.com/fwlink/?LinkId=94684)|  
|WSS: Kullanıcı adı belirteci profili 1.0|[Güvenlik UsernameToken profili 1.0 Web Hizmetleri](https://go.microsoft.com/fwlink/?LinkId=95334)<br /><br /> gerekli Password/@TypePasswordText (varsayılan) =|  
|WSS: X.509 belirteci profili 1.0|[Web Hizmetleri Güvenlik X.509 Sertifika belirteci profili](https://go.microsoft.com/fwlink/?LinkId=95335)|  
|WSS: SAML 1.1 belirteç profili 1.0|[Web Hizmetleri güvenlik: SAML belirteci profili](https://go.microsoft.com/fwlink/?LinkId=96693)|  
|WSS: SOAP ileti güvenliği 1.1|[Web Hizmetleri güvenlik: SOAP ileti güvenliği 1.1](https://go.microsoft.com/fwlink/?LinkId=91240)|  
|WSS kullanıcı adı belirteci Profil 1.1|[Güvenlik UsernameToken Profil 1.1 Web Hizmetleri](https://go.microsoft.com/fwlink/?LinkId=95331)<br /><br /> parola tabanlı anahtar türetme uygulamaz;<br /><br /> gerekli Password/@TypePasswordText (varsayılan) =|  
|WSS: Profil 1.1 X509 belirteç|[Web Hizmetleri Güvenlik X.509 sertifikası belirteci Profil 1.1](https://go.microsoft.com/fwlink/?LinkId=95332)|  
|WSS: Kerberos belirteci Profil 1.1|[Güvenlik Kerberos belirteci Profil 1.1 Web Hizmetleri](https://go.microsoft.com/fwlink/?LinkId=95333)|  
|WSS: SAML 1.1 belirteç Profil 1.1|[Web Hizmetleri Güvenlik SAML belirteci Profil 1.1](https://go.microsoft.com/fwlink/?LinkId=96694)|  
|WS-Secure Conversation|[Web Hizmetleri güvenli konuşma dili](https://go.microsoft.com/fwlink/?LinkId=95317)|  
|WS-Trust 1.4|[Web Hizmetleri dil güven](https://go.microsoft.com/fwlink/?LinkId=169514)|  
|WS-SecurityPolicy 2005/07|[Web Hizmetleri güvenli konuşma dili](https://go.microsoft.com/fwlink/?LinkId=95317)<br /><br /> OASIS WS-SX teknik komitesi gönderilen errata tarafından düzeltilir gibi.<br /><br /> [ws-sx iletisi](https://go.microsoft.com/fwlink/?LinkId=96700)|  
|WS-ReliableMessaging 1.1|[Güvenilir Mesajlaşma Protokolü sürüm 1.1](../../../../docs/framework/wcf/feature-details/reliable-messaging-protocol-version-1-1.md)|  
  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> Aşağıdaki tabloda özellikleri destekler.  
  
|Belirtimi/belge|Bağlantı|  
|-----------------------------|----------|  
|WS-düzenleme|[Web Hizmetleri düzenleme](https://go.microsoft.com/fwlink/?LinkId=95324)|  
|WS-AtomicTransaction|[Atomik işlem Web Hizmetleri](https://go.microsoft.com/fwlink/?LinkId=95323)|  
  
 <xref:System.ServiceModel.Description.MetadataExporter>, <xref:System.ServiceModel.Description.MetadataImporter>, <xref:System.ServiceModel.Description.WsdlExporter>, <xref:System.ServiceModel.Description.WsdlImporter>, Ve <xref:System.ServiceModel.Description.MetadataResolver> sınıfları aşağıdaki meta verileri belirtimler için destek sağlar:  
  
- [XML Şeması Kısım 1: Yapıları ikinci sürüm](https://go.microsoft.com/fwlink/?LinkId=3536)  
  
- [XML şema bölümü 2: İkinci Sürüm veri türleri](https://go.microsoft.com/fwlink/?LinkId=40138)  
  
- [WSDL 1.1](https://go.microsoft.com/fwlink/?LinkId=96160)  
  
- [WS-Policy 1.2](https://go.microsoft.com/fwlink/?LinkId=96705)  
  
- [WS-Policy 1.5](https://go.microsoft.com/fwlink/?LinkId=96706)  
  
- [WS-PolicyAttachment 1.2](https://go.microsoft.com/fwlink/?LinkId=96707)  
  
- [WS-MetadataExchange 1.1](https://go.microsoft.com/fwlink/?LinkId=94868)  
  
- [WS aktarım almak için meta verileri alma](https://go.microsoft.com/fwlink/?LinkId=96708)  
  
 Ayrıca, aşağıdaki birlikte çalışabilirlik profilleri arasında WCF uygulanır:  
  
- [Temel Profil 1.1](https://go.microsoft.com/fwlink/?LinkId=69313)  
  
- [Basit SOAP 1.0 bağlama](https://go.microsoft.com/fwlink/?LinkId=96710)  
  
- [Temel güvenlik profili 1.0 çalışma taslak](https://go.microsoft.com/fwlink/?LinkId=96711)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sistem Tarafından Sağlanan Birlikte Kullanılabilirlik Bağlamaları ile Desteklenen Web Hizmeti Protokolleri](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)
- [Mesajlaşma Protokolleri](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)
- [Veri Sözleşmesi Şema Başvurusu](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)
- [WSDL ve İlke](../../../../docs/framework/wcf/feature-details/wsdl-and-policy.md)
- [Güvenlik Protokolleri](../../../../docs/framework/wcf/feature-details/security-protocols.md)
- [Güvenilir Mesajlaşma Protokolü sürüm 1.0](../../../../docs/framework/wcf/feature-details/reliable-messaging-protocol-version-1-0.md)
- [Güvenilir Mesajlaşma Protokolü sürüm 1.1](../../../../docs/framework/wcf/feature-details/reliable-messaging-protocol-version-1-1.md)
- [İşlem Protokolleri](../../../../docs/framework/wcf/feature-details/transaction-protocols.md)
- [Bağlam Değişimi Protokolü](../../../../docs/framework/wcf/feature-details/context-exchange-protocol.md)
