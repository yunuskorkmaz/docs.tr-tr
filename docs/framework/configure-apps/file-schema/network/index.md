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
ms.openlocfilehash: 0f5d762a2b688bebcb7c027be6c639b6d64c069d
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664116"
---
# <a name="network-settings-schema"></a>Ağ Ayarları Şeması
Ağ ayarları .NET Framework Internet 'e nasıl bağlandığını belirtir. Aşağıdaki tabloda, [ \<sistem .net > öğesi (ağ ayarları)](system-net-element-network-settings.md)altındaki her bir alt yapılandırma öğesinin işlevi açıklanmaktadır.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<authenticationModules > öğesi (ağ ayarları)](authenticationmodules-element-network-settings.md)|Internet isteklerinin kimliğini doğrulamak için kullanılan modülleri belirtir.|  
|[\<connectionManagement > öğesi (ağ ayarları)](connectionmanagement-element-network-settings.md)|Internet ana bilgisayarlarına en fazla bağlantı sayısını belirtir.|  
|[\<defaultProxy > öğesi (ağ ayarları)](defaultproxy-element-network-settings.md)|Internet 'e HTTP istekleri için kullanılan proxy sunucusunu belirtir.|  
|[\<mailSettings > öğesi (ağ ayarları)](mailsettings-element-network-settings.md)|Posta gönderme seçeneklerinin ayarlarını içerir.|  
|[\<requestCaching > öğesi (ağ ayarları)](requestcaching-element-network-settings.md)|Ağ istekleri için önbelleğe alma mekanizmasını denetler.|  
|[\<webRequestModules > öğesi (ağ ayarları)](webrequestmodules-element-network-settings.md)|Internet konaklarından bilgi istemek için kullanılan modülleri belirtir.|  
  
 URI ayarları .NET Framework, Tekdüzen Kaynak tanımlayıcıları (URI) kullanarak ifade edilen Web adreslerini nasıl işleyeceğini belirtir. Aşağıdaki tabloda, [ \<Uri > öğesi (URI ayarları)](uri-element-uri-settings.md)altındaki her bir alt yapılandırma öğesinin işlevi açıklanmaktadır.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<IDN > öğesi (Uri Ayarları)](idn-element-uri-settings.md)|Uluslararası etki alanı adı (ıDN) ayrıştırma 'nın etki alanı adlarına uygulandığını belirtir.|  
|[\<ıriayrıştırma > öğesi (URI ayarları)](iriparsing-element-uri-settings.md)|Uluslararası kaynak tanımlayıcı (IRI) ayrıştırma 'nin bir <xref:System.Uri> öğesine uygulanıp uygulanmadığını ve IRI ayrıştırma kurallarının uygulanıp uygulanamayacağını belirtir.|  
|[\<> düzeni öğesi (URI ayarları)](schemesettings-element-uri-settings.md)|Belirli düzenler için <xref:System.Uri> nasıl ayrıştırılacaksınız belirtir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İnternet Uygulamalarını Yapılandırma](../../../network-programming/configuring-internet-applications.md)
- [Yapılandırma Dosyası Şeması](../index.md)
