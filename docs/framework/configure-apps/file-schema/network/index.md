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
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698158"
---
# <a name="network-settings-schema"></a>Ağ Ayarları Şeması
Ağ ayarları .NET Framework Internet 'e nasıl bağlandığını belirtir.

@No__t -0system. net > ayarları .NET Framework ağa nasıl bağlanacağını belirtir. Aşağıdaki tabloda, [\<Sistem .net > öğesi (ağ ayarları)](system-net-element-network-settings.md)altındaki her bir alt yapılandırma öğesinin işlevi açıklanmaktadır.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<authenticationModules > öğesi (ağ ayarları)](authenticationmodules-element-network-settings.md)|Internet isteklerinin kimliğini doğrulamak için kullanılan modülleri belirtir.|  
|[\<connectionManagement > öğesi (ağ ayarları)](connectionmanagement-element-network-settings.md)|Internet ana bilgisayarlarına en fazla bağlantı sayısını belirtir.|  
|[\<defaultProxy > öğesi (ağ ayarları)](defaultproxy-element-network-settings.md)|Internet 'e HTTP istekleri için kullanılan proxy sunucusunu belirtir.|  
|[\<mailSettings > öğesi (ağ ayarları)](mailsettings-element-network-settings.md)|Posta gönderme seçeneklerinin ayarlarını içerir.|  
|[\<requestCaching > öğesi (ağ ayarları)](requestcaching-element-network-settings.md)|Ağ istekleri için önbelleğe alma mekanizmasını denetler.|  
|[\<webRequestModules > öğesi (ağ ayarları)](webrequestmodules-element-network-settings.md)|Internet konaklarından bilgi istemek için kullanılan modülleri belirtir.|  
  
@No__t-0uri > ayarları, .NET Framework Tekdüzen Kaynak tanımlayıcıları (URI) kullanarak ifade edilen Web adreslerini nasıl işleyeceğini belirtir. Aşağıdaki tabloda, [\<urı > öğesi (URI ayarları)](uri-element-uri-settings.md)altındaki her bir alt yapılandırma öğesinin işlevi açıklanmaktadır.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<ıdn > öğesi (URI ayarları)](idn-element-uri-settings.md)|Uluslararası etki alanı adı (ıDN) ayrıştırma 'nın etki alanı adlarına uygulandığını belirtir.|  
|[\<ıriayrıştırma > öğesi (Uri Ayarları)](iriparsing-element-uri-settings.md)|Uluslararası kaynak tanımlayıcı (IRI) ayrıştırma <xref:System.Uri> ' a uygulanıp uygulanmadığını ve IRI ayrıştırma kurallarının uygulanıp uygulanamayacağını belirtir.|  
|[\<Ramesettings > öğesi (Uri Ayarları)](schemesettings-element-uri-settings.md)|Belirli düzenler için <xref:System.Uri> ' ın nasıl ayrıştıralınacağını belirtir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İnternet Uygulamalarını Yapılandırma](../../../network-programming/configuring-internet-applications.md)
- [Yapılandırma Dosyası Şeması](../index.md)
