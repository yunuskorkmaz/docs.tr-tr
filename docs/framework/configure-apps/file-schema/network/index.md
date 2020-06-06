---
title: Ağ Ayarları Şeması
ms.date: 03/30/2017
helpviewer_keywords:
- elements [.NET Framework], network configuration elements
- sending data, network configuration elements
- receiving data, network configuration elements
- configuration settings [.NET Framework], networks
- Internet, network configuration elements
- network configuration elements
- network settings
- connections [.NET Framework], network configuration elements
- network resources, network configuration elements
ms.assetid: f1de5a0f-76c5-4833-819f-5222b8146340
ms.openlocfilehash: 5e3bd1b1734fc7fba50b72785531a8b001d6d741
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "71698158"
---
# <a name="network-settings-schema"></a>Ağ Ayarları Şeması
Ağ ayarları .NET Framework Internet 'e nasıl bağlandığını belirtir.

\<system.net>Ayarlar .NET Framework ağa nasıl bağlanacağını belirtir. Aşağıdaki tabloda, [ \<system.Net> öğesi (ağ ayarları)](system-net-element-network-settings.md)altındaki her bir alt yapılandırma öğesinin işlevi açıklanmaktadır.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<authenticationModules>Öğesi (ağ ayarları)](authenticationmodules-element-network-settings.md)|Internet isteklerinin kimliğini doğrulamak için kullanılan modülleri belirtir.|  
|[\<connectionManagement>Öğesi (ağ ayarları)](connectionmanagement-element-network-settings.md)|Internet ana bilgisayarlarına en fazla bağlantı sayısını belirtir.|  
|[\<defaultProxy>Öğesi (ağ ayarları)](defaultproxy-element-network-settings.md)|Internet 'e HTTP istekleri için kullanılan proxy sunucusunu belirtir.|  
|[\<mailSettings>Öğesi (ağ ayarları)](mailsettings-element-network-settings.md)|Posta gönderme seçeneklerinin ayarlarını içerir.|  
|[\<requestCaching>Öğesi (ağ ayarları)](requestcaching-element-network-settings.md)|Ağ istekleri için önbelleğe alma mekanizmasını denetler.|  
|[\<webRequestModules>Öğesi (ağ ayarları)](webrequestmodules-element-network-settings.md)|Internet konaklarından bilgi istemek için kullanılan modülleri belirtir.|  
  
\<uri>Ayarlar, .NET Framework Tekdüzen Kaynak tanımlayıcıları (URI) kullanarak ifade edilen Web adreslerini nasıl işleyeceğini belirtir. Aşağıdaki tabloda, öğesi altındaki her bir alt yapılandırma öğesinin işlevi açıklanmaktadır [ \<uri> (URI ayarları)](uri-element-uri-settings.md).  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<idn>Öğesi (URI ayarları)](idn-element-uri-settings.md)|Uluslararası etki alanı adı (ıDN) ayrıştırma 'nın etki alanı adlarına uygulandığını belirtir.|  
|[\<iriParsing>Öğesi (URI ayarları)](iriparsing-element-uri-settings.md)|Uluslararası kaynak tanımlayıcı (IRI) ayrıştırma 'nin bir öğesine uygulanıp uygulanmadığını <xref:System.Uri> ve IRI ayrıştırma kurallarının uygulanıp uygulanamayacağını belirtir.|  
|[\<schemeSettings>Öğesi (URI ayarları)](schemesettings-element-uri-settings.md)|<xref:System.Uri>Belirli düzenler için nasıl ayrıştırılacaksınız belirtir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İnternet Uygulamalarını Yapılandırma](../../../network-programming/configuring-internet-applications.md)
- [Yapılandırma dosyası şeması](../index.md)
