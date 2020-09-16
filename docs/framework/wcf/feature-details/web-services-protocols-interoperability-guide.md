---
title: Web Hizmetleri protokolleri birlikte çalışabilirlik Kılavuzu
ms.date: 03/30/2017
ms.assetid: f2981678-ebdb-433d-899b-467f7df95fb2
ms.openlocfilehash: 4169a796311c402a97358de5d52c52562b6ed357
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90553180"
---
# <a name="web-services-protocols-interoperability-guide"></a>Web Hizmetleri protokolleri birlikte çalışabilirlik Kılavuzu

Windows Communication Foundation (WCF), bir dizi Web hizmeti protokolünü uygular. Bu protokollerin birçoğu, uygulayıcının kararına kadar bir dizi seçenek ve genişletilebilirlik noktası içerir. Bu konu, WCF 'nin uyguladığı Web Hizmetleri protokollerinin bir listesini sağlar. Bu bölümdeki diğer konular desteklenen her protokol için uygulama ayrıntıları sağlar.

## <a name="web-services-protocols-implemented-by-wcf"></a>WCF tarafından uygulanan Web Hizmetleri protokolleri

WCF, sözleşmeler özelliği aracılığıyla kanallar ve Web Hizmetleri uygulama protokolleri aracılığıyla Web Hizmetleri (WS) altyapı protokolleri için destek sağlar. Uygulama protokolleri için birlikte çalışabilirlik, XML şeması Açıklama Dili 1,0 (XSD) ve Web Hizmetleri Açıklama Dili (WSDL) 1,1 aracılığıyla gerçekleştirilir.

Altyapı protokolleri birlikte çalışabilirliği WS-* belirtimleri tarafından sağlanır. WCF kanalları bir dizi WS-Infrastructure protokolü için destek sağlar \* . WCF kanalları bağlama öğeleri kullanılarak yapılandırılır. Aşağıdaki tablolar, \* ÇEŞITLI WCF bağlama öğeleri tarafından uygulanan WS-Infrastructure protokollerinin tam listesini içerir.

<xref:System.ServiceModel.Channels.HttpTransportBindingElement> , aşağıdaki tablodaki belirtimleri destekler.

|Belirtim/belge|Bağlantı|
|-----------------------------|----------|
|HTTP 1,1|[RFC 2616](https://www.rfc-editor.org/rfc/rfc2616.txt)|
|SOAP 1,1 HTTP bağlama|[Basit nesne erişim Protokolü (SOAP) 1,1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/), Bölüm 7|
|SOAP 1,2 HTTP bağlama|[SOAP sürüm 1,2 Bölüm 2: Adjuncts (Second Edition)](https://www.w3.org/TR/soap12-part2/), Bölüm 7|

<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> ve <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> aşağıdaki tablodaki belirtimleri destekler.

|Belirtim/belge|Bağlantı|
|-----------------------------|----------|
|XML|[Genişletilebilir biçimlendirme dili (XML) 1,0 (dördüncü sürüm)](https://www.w3.org/TR/REC-xml/)|
|SOAP 1,1|[Basit nesne erişim Protokolü (SOAP) 1,1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/)|
|SOAP 1,2 Core|[SOAP sürüm 1,2 Bölüm 1: mesajlaşma çerçevesi (Ikinci sürüm)](https://www.w3.org/TR/2007/REC-soap12-part1-20070427/)|
|WS-Addressing 2004/08|[Web Hizmetleri adresleme (WS-Addressing)](https://www.w3.org/Submission/2004/SUBM-ws-addressing-20040810/)|
|W3C Web Hizmetleri adresleme 1,0-çekirdek|[Web Hizmetleri adresleme 1,0-çekirdek](https://www.w3.org/TR/2006/REC-ws-addr-core-20060509/)|
|W3C Web Hizmetleri adresleme 1,0-SOAP bağlama|[Web Hizmetleri adresleme 1,0-SOAP bağlama](https://www.w3.org/TR/2006/REC-ws-addr-soap-20060509/)|
|W3C Web Hizmetleri adresleme 1,0-WSDL Binding *|[Web Hizmetleri adresleme 1,0-WSDL bağlama](https://www.w3.org/TR/2006/CR-ws-addr-wsdl-20060529/)|
|W3C Web Hizmetleri adresleme 1,0 meta verileri|[Web Hizmetleri adresleme 1,0-meta veriler](https://www.w3.org/TR/ws-addr-metadata/)|
|WSDL SOAP 1.1 bağlama|[Web Hizmetleri Açıklama Dili (WSDL) 1,1](https://www.w3.org/TR/wsdl/)|
|WSDL SOAP 1.2 bağlama|[SOAP 1,2 için WSDL 1,1 bağlama uzantısı](https://www.w3.org/Submission/wsdl11soap12/)|

<xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> , aşağıdaki tablodaki belirtimleri destekler.

|Belirtim/belge|Bağlantı|
|-----------------------------|----------|
|XOP ıNCLUDE|[XML-ikili Iyileştirilmiş paketleme](https://www.w3.org/TR/xop10/)|
|MTOM + SOAP 1.2 bağlama|[SOAP Ileti Iletimi Iyileştirme mekanizması](https://www.w3.org/TR/soap12-mtom/)|
|MTOM SOAP 1,1 bağlaması|[MTOM 1,0 için SOAP 1,1 bağlaması](https://www.w3.org/Submission/soap11mtom10/)|
|MTOM WS-Poliyasyıtions|[MTOM serileştirme Ilkesi onaylama (WS-MTOMPolicy)](https://www.w3.org/Submission/WS-MTOMPolicy/)|

<xref:System.ServiceModel.Channels.SecurityBindingElement> , aşağıdaki tablodaki belirtimleri destekler.

|Belirtim/belge|Bağlantı|
|-----------------------------|----------|
|WSS: SOAP Iletisi güvenliği 1,0|[Web Hizmetleri Güvenliği: SOAP Iletisi güvenlik 1,0](https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf)|
|WSS: Kullanıcı adı belirteç profili 1,0|[Web Hizmetleri Güvenliği UsernameToken profili 1,0](https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf)<br /><br /> gerektir Password/@Type = PasswordText (varsayılan)|
|WSS: X. 509.440 belirteç profili 1,0|[Web Hizmetleri Güvenliği X. 509.440 sertifika belirteci profili](https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf)|
|WSS: SAML 1,1 belirteç profili 1,0|[Web Hizmetleri Güvenliği: SAML belirteci profili](https://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.0.pdf)|
|WSS: SOAP Iletisi güvenliği 1,1|[Web Hizmetleri Güvenliği: SOAP Iletisi güvenlik 1,1](https://www.oasis-open.org/committees/download.php/16790/wss-v1.1-spec-os-SOAPMessageSecurity.pdf)|
|WSS Kullanıcı adı belirteç profili 1,1|[Web Hizmetleri Güvenliği UsernameToken profili 1,1](https://www.oasis-open.org/committees/download.php/16782/wss-v1.1-spec-os-UsernameTokenProfile.pdf)<br /><br /> parola tabanlı anahtar türetme gerçekleştirmeyin;<br /><br /> gerektir Password/@Type = PasswordText (varsayılan)|
|WSS: x509 belirteç profili 1,1|[Web Hizmetleri Güvenliği X. 509.440 sertifika belirteci profili 1,1](https://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf)|
|WSS: Kerberos belirteç profili 1,1|[Web Hizmetleri Güvenliği Kerberos belirteç profili 1,1](https://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf)|
|WSS: SAML 1,1 belirteç profili 1,1|[Web Hizmetleri Güvenliği SAML belirteci profili 1,1](https://www.oasis-open.org/committees/download.php/16768/wss-v1.1-spec-os-SAMLTokenProfile.pdf)|
|WS-Secure konuşması|[Web hizmetleri güvenli konuşma dili](https://specs.xmlsoap.org/ws/2005/02/sc/ws-secureconversation.pdf)|
|WS-Trust 1,4|[Web Hizmetleri güven dili](https://docs.oasis-open.org/ws-sx/ws-trust/200802)|
|WS-SecurityPolicy 2005/07|[Web hizmetleri güvenli konuşma dili](https://specs.xmlsoap.org/ws/2005/02/sc/ws-secureconversation.pdf)<br /><br /> Errata tarafından değiştirilmiş olarak OASTO WS-SX Technical komite 'a gönderildi.<br /><br /> [WS-SX iletisi](https://lists.oasis-open.org/archives/ws-sx/200512/msg00017.html)|
|WS-ReliableMessaging 1,1|[Güvenilir Mesajlaşma Protokolü sürüm 1.1](reliable-messaging-protocol-version-1-1.md)|

<xref:System.ServiceModel.Channels.TransactionFlowBindingElement> , aşağıdaki tablodaki belirtimleri destekler.

|Belirtim/belge|Bağlantı|
|-----------------------------|----------|
|WS koordinasyonu|[Web Hizmetleri düzenlemesi](/previous-versions/ms951231(v=msdn.10))|
|WS-AtomicTransaction|[Web Hizmetleri atomik Işlem](https://specs.xmlsoap.org/ws/2004/10/wsat/wsat.pdf)|

<xref:System.ServiceModel.Description.MetadataExporter>,, <xref:System.ServiceModel.Description.MetadataImporter> , <xref:System.ServiceModel.Description.WsdlExporter> <xref:System.ServiceModel.Description.WsdlImporter> Ve <xref:System.ServiceModel.Description.MetadataResolver> sınıfları aşağıdaki meta veri belirtimleri için destek sağlar:

- [XML şeması Bölüm 1: yapılar Ikinci sürüm](https://www.w3.org/TR/xmlschema-1/)

- [XML şeması Bölüm 2: veri türleri Ikinci sürüm](https://www.w3.org/TR/xmlschema-2/)

- [WSDL 1,1](https://www.w3.org/TR/wsdl/)

- [WS-Policy 1,2](https://www.w3.org/Submission/2006/SUBM-WS-Policy-20060425/)

- [WS-Policy 1,5](https://www.w3.org/TR/ws-policy/)

- [WS-PolicyAttachment 1,2](https://www.w3.org/Submission/2006/SUBM-WS-PolicyAttachment-20060425/)

- [WS-MetadataExchange 1,1](https://specs.xmlsoap.org/ws/2004/09/mex/WS-MetadataExchange.pdf)

- [WS-aktarım meta verileri alma için al](https://www.w3.org/Submission/2006/SUBM-WS-Transfer-20060315/)

Ayrıca, aşağıdaki birlikte çalışabilirlik profilleri WCF genelinde uygulanır:

- [Temel profil 1,1](http://www.ws-i.org/Profiles/BasicProfile-1.1-2004-08-24.html)

- [Basit SOAP bağlama 1,0](http://www.ws-i.org/Profiles/SimpleSoapBindingProfile-1.0-2004-08-24.html)

- [Temel güvenlik profili 1,0 çalışma taslağı](http://www.ws-i.org/Profiles/BasicSecurityProfile-1.0-2006-03-29.html)

## <a name="see-also"></a>Ayrıca bkz.

- [Sistem Tarafından Sağlanan Birlikte Kullanılabilirlik Bağlamaları ile Desteklenen Web Hizmeti Protokolleri](web-services-protocols-supported-by-system-provided-interoperability-bindings.md)
- [Mesajlaşma Protokolleri](messaging-protocols.md)
- [Veri Sözleşmesi Şema Başvurusu](data-contract-schema-reference.md)
- [WSDL ve İlke](wsdl-and-policy.md)
- [Güvenlik Protokolleri](security-protocols.md)
- [Güvenilir Mesajlaşma Protokolü sürüm 1.0](reliable-messaging-protocol-version-1-0.md)
- [Güvenilir Mesajlaşma Protokolü sürüm 1.1](reliable-messaging-protocol-version-1-1.md)
- [İşlem Protokolleri](transaction-protocols.md)
- [Bağlam Değişimi Protokolü](context-exchange-protocol.md)
