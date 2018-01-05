---
title: "Web Hizmetleri Protokolleri Birlikte Çalışabilirlik Kılavuzu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2981678-ebdb-433d-899b-467f7df95fb2
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6b962452b6127d259733418969f1fb7b5036b1e5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="web-services-protocols-interoperability-guide"></a>Web Hizmetleri Protokolleri Birlikte Çalışabilirlik Kılavuzu
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]Web Hizmetleri protokolleri sayısı uygular. Çoğu bu protokolleri, bir dizi seçenekleri ve uygulayan kendi takdirine bağlı sol genişletilebilirlik noktaları içerir. Bu konu, bir listesini Web Hizmetleri protokolleri sağlar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygular. Bu bölüm içindeki diğer konular, desteklenen her protokol için uygulama ayrıntıları sağlar.  
  
## <a name="web-services-protocols-implemented-by-wcf"></a>WCF tarafından uygulanan protokoller Web Hizmetleri  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Web Hizmetleri (WS) altyapısı protokolleri kanalları üzerinden ve Web Hizmetleri uygulama protokolleri sözleşmeleri özelliği aracılığıyla için destek sağlar. Birlikte çalışabilirlik uygulama protokolleri için XML Şeması Tanımlama Dili (XSD) 1.0 ve Web Hizmetleri Açıklama Dili (WSDL) 1.1 aracılığıyla gerçekleştirilir.  
  
 Altyapı protokolleri birlikte çalışabilirlik sağlanır WS - tarafından * belirtimleri. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Kanallar, WS - sayısı için destek sağlar\* altyapı protokoller. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Kanal bağlama öğeleri kullanılarak yapılandırılır. Aşağıdaki tablolarda tam WS - listesini içeren\* çeşitli tarafından uygulanan altyapı protokolleri [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bağlama öğeleri.  
  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>Aşağıdaki tabloda özelliklerini destekler.  
  
|Belirtim/belgesi|Bağlantı|  
|-----------------------------|----------|  
|HTTP 1.1|[RFC 2616](http://go.microsoft.com/fwlink/?LinkId=90372)|  
|SOAP 1.1 HTTP bağlama|[Basit Nesne Erişim Protokolü (SOAP) 1.1](http://go.microsoft.com/fwlink/?LinkId=90520), Bölüm 7|  
|SOAP 1.2 HTTP bağlama|[SOAP sürüm 1.2 Bölüm 2: Adjuncts (ikinci Edition)](http://go.microsoft.com/fwlink/?LinkId=95329), Bölüm 7|  
  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>ve <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> aşağıdaki tabloda özelliklerini destekler.  
  
|Belirtim/belgesi|Bağlantı|  
|-----------------------------|----------|  
|XML|[Genişletilebilir İşaretleme Dili (XML) 1.0 (Dördüncü Edition)](http://go.microsoft.com/fwlink/?LinkId=15139)|  
|SOAP 1.1|[Basit Nesne Erişim Protokolü (SOAP) 1.1](http://go.microsoft.com/fwlink/?LinkId=96687)|  
|SOAP 1.2 Çekirdek|[SOAP sürüm 1.2 Bölüm 1: Framework Mesajlaşma (ikinci Edition)](http://go.microsoft.com/fwlink/?LinkId=94664)|  
|WS-adresleme 2004/08|[Adresleme (WS-adresleme) Web Hizmetleri](http://go.microsoft.com/fwlink/?LinkId=81239)|  
|Adresleme 1.0 - çekirdek W3C Web Hizmetleri|[Adresleme 1.0 - çekirdek Web Hizmetleri](http://go.microsoft.com/fwlink/?LinkId=96688)|  
|Adresleme 1.0 - SOAP bağlama W3C Web Hizmetleri|[Adresleme 1.0 - SOAP bağlama Web Hizmetleri](http://go.microsoft.com/fwlink/?LinkId=96689)|  
|W3C Web adresleme 1.0 - WSDL bağlama * Hizmetleri|[Adresleme 1.0 - WSDL bağlama Web Hizmetleri](http://go.microsoft.com/fwlink/?LinkId=96690)|  
|1.0 meta verileri adresleme W3C Web Hizmetleri|[Adresleme 1.0 - meta veri Web Hizmetleri](http://www.w3.org/TR/ws-addr-metadata/)|  
|WSDL SOAP1.1 bağlama|[Web Hizmetleri Açıklama Dili (WSDL) 1.1](http://go.microsoft.com/fwlink/?LinkId=96160)|  
|WSDL SOAP1.2 bağlama|[WSDL 1.1 bağlama uzantısı SOAP 1.2](http://go.microsoft.com/fwlink/?LinkId=96691)|  
  
 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>Aşağıdaki tabloda özelliklerini destekler.  
  
|Belirtim/belgesi|Bağlantı|  
|-----------------------------|----------|  
|XOP|[XML ikili paketleme en iyi duruma getirilmiş](http://go.microsoft.com/fwlink/?LinkId=96714)|  
|MTOM + SOAP1.2 bağlama|[SOAP iletisi iletim iyileştirme mekanizması](http://go.microsoft.com/fwlink/?LinkId=96713)|  
|MTOM SOAP 1.1 bağlama|[SOAP 1.1 bağlama MTOM 1.0 için](http://go.microsoft.com/fwlink/?LinkId=96712)|  
|MTOM WS-PolicyAssertions|Yayımlanacak.|  
  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>Aşağıdaki tabloda özelliklerini destekler.  
  
|Belirtim/belgesi|Bağlantı|  
|-----------------------------|----------|  
|WSS: SOAP iletisi güvenlik 1.0|[Web Hizmetleri güvenliği: SOAP iletisi güvenlik 1.0](http://go.microsoft.com/fwlink/?LinkId=94684)|  
|WSS: Kullanıcı belirteci profili 1.0|[Güvenlik UsernameToken profili 1.0 Web Hizmetleri](http://go.microsoft.com/fwlink/?LinkId=95334)<br /><br /> gerektiren Password/@TypePasswordText (varsayılan) =|  
|WSS: X.509 belirteci profili 1.0|[Web Hizmetleri Güvenlik X.509 sertifikası belirteci profili](http://go.microsoft.com/fwlink/?LinkId=95335)|  
|WSS: SAML 1.1 belirteci profili 1.0|[Web Hizmetleri güvenlik: SAML belirteci profili](http://go.microsoft.com/fwlink/?LinkId=96693)|  
|WSS: SOAP iletisi güvenlik 1.1|[Web Hizmetleri güvenliği: SOAP iletisi güvenlik 1.1](http://go.microsoft.com/fwlink/?LinkId=91240)|  
|WSS kullanıcıadı belirteci Profil 1.1|[Güvenlik UsernameToken Profil 1.1 Web Hizmetleri](http://go.microsoft.com/fwlink/?LinkId=95331)<br /><br /> parola tabanlı anahtar türetme kullanılmaz;<br /><br /> gerektiren Password/@TypePasswordText (varsayılan) =|  
|WSS: X509 Profil 1.1 belirteci.|[Web Hizmetleri Güvenlik X.509 sertifikası belirteci Profil 1.1](http://go.microsoft.com/fwlink/?LinkId=95332)|  
|WSS: Kerberos belirteci Profil 1.1|[Güvenlik Kerberos belirteci Profil 1.1 Web Hizmetleri](http://go.microsoft.com/fwlink/?LinkId=95333)|  
|WSS: SAML 1.1 belirteci Profil 1.1|[Web Hizmetleri Güvenlik SAML belirteci Profil 1.1](http://go.microsoft.com/fwlink/?LinkId=96694)|  
|WS-güvenli konuşma|[Konuşma dilini güvenli Web Hizmetleri](http://go.microsoft.com/fwlink/?LinkId=95317)|  
|WS-Trust 1.4|[Web Hizmetleri dil güven](http://go.microsoft.com/fwlink/?LinkId=169514)|  
|WS-SecurityPolicy 2005/07|[Konuşma dilini güvenli Web Hizmetleri](http://go.microsoft.com/fwlink/?LinkId=95317)<br /><br /> OASIS WS-SX teknik komitesi gönderilen ayrıntıyla açıklayan hata bilgilerini tarafından dayanıklıdır gibi.<br /><br /> [ws-sx iletisi](http://go.microsoft.com/fwlink/?LinkId=96700)|  
|WS-ReliableMessaging 1.1|[Güvenilir Mesajlaşma Protokolü sürüm 1.1](../../../../docs/framework/wcf/feature-details/reliable-messaging-protocol-version-1-1.md)|  
  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>Aşağıdaki tabloda özelliklerini destekler.  
  
|Belirtim/belgesi|Bağlantı|  
|-----------------------------|----------|  
|WS-düzenleme|[Web Hizmetleri düzenleme](http://go.microsoft.com/fwlink/?LinkId=95324)|  
|WS-AtomicTransaction|[Atomik işlem Web Hizmetleri](http://go.microsoft.com/fwlink/?LinkId=95323)|  
  
 <xref:System.ServiceModel.Description.MetadataExporter>, <xref:System.ServiceModel.Description.MetadataImporter>, <!--zz <xref:System.ServiceModel.Description.WSDLExporter>, <xref:System.ServiceModel.Description.WSDLImporter>, --> `System.ServiceModel.Description.MetadataImporter`, `System.ServiceModel.Description.WSDLImporter`, Ve <xref:System.ServiceModel.Description.MetadataResolver> sınıfları aşağıdaki meta verileri özellikleri için destek sağlar:  
  
-   [XML şema bölüm 1: Yapıları ikinci sürüm](http://go.microsoft.com/fwlink/?LinkId=3536)  
  
-   [XML şema bölüm 2: Veri türleri ikinci sürüm](http://go.microsoft.com/fwlink/?LinkId=40138)  
  
-   [WSDL 1.1](http://go.microsoft.com/fwlink/?LinkId=96160)  
  
-   [WS-ilke 1.2](http://go.microsoft.com/fwlink/?LinkId=96705)  
  
-   [WS-Policy 1.5](http://go.microsoft.com/fwlink/?LinkId=96706)  
  
-   [WS-PolicyAttachment 1.2](http://go.microsoft.com/fwlink/?LinkId=96707)  
  
-   [WS-MetadataExchange 1.1](http://go.microsoft.com/fwlink/?LinkId=94868)  
  
-   [WS-aktarımı almak için meta veri alma](http://go.microsoft.com/fwlink/?LinkId=96708)  
  
 Ayrıca, aşağıdaki birlikte çalışabilirlik profilleri arasında uygulanan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:  
  
-   [Temel Profil 1.1](http://go.microsoft.com/fwlink/?LinkId=69313)  
  
-   [Basit SOAP 1.0 bağlama](http://go.microsoft.com/fwlink/?LinkId=96710)  
  
-   [Temel güvenlik profili 1.0 çalışma taslak](http://go.microsoft.com/fwlink/?LinkId=96711)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sistem Tarafından Sağlanan Birlikte Kullanılabilirlik Bağlamaları ile Desteklenen Web Hizmeti Protokolleri](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)  
 [Mesajlaşma Protokolleri](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)  
 [Veri Sözleşmesi Şema Başvurusu](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)  
 [WSDL ve İlke](../../../../docs/framework/wcf/feature-details/wsdl-and-policy.md)  
 [Güvenlik Protokolleri](../../../../docs/framework/wcf/feature-details/security-protocols.md)  
 [Güvenilir Mesajlaşma Protokolü sürüm 1.0](../../../../docs/framework/wcf/feature-details/reliable-messaging-protocol-version-1-0.md)  
 [Güvenilir Mesajlaşma Protokolü sürüm 1.1](../../../../docs/framework/wcf/feature-details/reliable-messaging-protocol-version-1-1.md)  
 [İşlem Protokolleri](../../../../docs/framework/wcf/feature-details/transaction-protocols.md)  
 [Bağlam Değişimi Protokolü](../../../../docs/framework/wcf/feature-details/context-exchange-protocol.md)
