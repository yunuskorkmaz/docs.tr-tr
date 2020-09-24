---
title: Ağ Ayarları Şeması
description: .NET Framework Internet 'e nasıl bağlandığını ve URI 'Leri nasıl işlediğini belirten ağ ayarlarının şeması hakkında bilgi edinin.
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
ms.openlocfilehash: 8071fcfcdb16b6e71d8d7af05a704d8842b3e963
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158922"
---
# <a name="network-settings-schema"></a>Ağ Ayarları Şeması

Ağ ayarları .NET Framework Internet 'e nasıl bağlandığını belirtir.

\<system.net>Ayarlar .NET Framework ağa nasıl bağlanacağını belirtir. Aşağıdaki tabloda, [ \<system.Net> öğesi (ağ ayarları)](system-net-element-network-settings.md)altındaki her bir alt yapılandırma öğesinin işlevi açıklanmaktadır.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<authenticationModules> Öğesi (ağ ayarları)](authenticationmodules-element-network-settings.md)|Internet isteklerinin kimliğini doğrulamak için kullanılan modülleri belirtir.|  
|[\<connectionManagement> Öğesi (ağ ayarları)](connectionmanagement-element-network-settings.md)|Internet ana bilgisayarlarına en fazla bağlantı sayısını belirtir.|  
|[\<defaultProxy> Öğesi (ağ ayarları)](defaultproxy-element-network-settings.md)|Internet 'e HTTP istekleri için kullanılan proxy sunucusunu belirtir.|  
|[\<mailSettings> Öğesi (ağ ayarları)](mailsettings-element-network-settings.md)|Posta gönderme seçeneklerinin ayarlarını içerir.|  
|[\<requestCaching> Öğesi (ağ ayarları)](requestcaching-element-network-settings.md)|Ağ istekleri için önbelleğe alma mekanizmasını denetler.|  
|[\<webRequestModules> Öğesi (ağ ayarları)](webrequestmodules-element-network-settings.md)|Internet konaklarından bilgi istemek için kullanılan modülleri belirtir.|  
  
\<uri>Ayarlar, .NET Framework Tekdüzen Kaynak tanımlayıcıları (URI) kullanarak ifade edilen Web adreslerini nasıl işleyeceğini belirtir. Aşağıdaki tabloda, öğesi altındaki her bir alt yapılandırma öğesinin işlevi açıklanmaktadır [ \<uri> (URI ayarları)](uri-element-uri-settings.md).  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<idn> Öğesi (URI ayarları)](idn-element-uri-settings.md)|Uluslararası etki alanı adı (ıDN) ayrıştırma 'nın etki alanı adlarına uygulandığını belirtir.|  
|[\<iriParsing> Öğesi (URI ayarları)](iriparsing-element-uri-settings.md)|Uluslararası kaynak tanımlayıcı (IRI) ayrıştırma 'nin bir öğesine uygulanıp uygulanmadığını <xref:System.Uri> ve IRI ayrıştırma kurallarının uygulanıp uygulanamayacağını belirtir.|  
|[\<schemeSettings> Öğesi (URI ayarları)](schemesettings-element-uri-settings.md)|<xref:System.Uri>Belirli düzenler için nasıl ayrıştırılacaksınız belirtir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İnternet Uygulamalarını Yapılandırma](../../../network-programming/configuring-internet-applications.md)
- [Yapılandırma dosyası şeması](../index.md)
