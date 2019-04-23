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
ms.openlocfilehash: 71d945e6046a8648a812de939f197429bc695808
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59148297"
---
# <a name="network-settings-schema"></a>Ağ Ayarları Şeması
Ağ ayarları, .NET Framework Internet'e nasıl bağlandığını belirtin. Aşağıdaki tabloda her bir alt yapılandırma öğesinin altında işlevi açıklanmaktadır [ \<system.Net > öğesi (ağ ayarları)](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md).  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<authenticationModules > öğesi (ağ ayarları)](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|Internet isteklerini kimliğini doğrulamak için kullanılan modülleri belirtir.|  
|[\<connectionManagement > öğesi (ağ ayarları)](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|Bağlantılar Internet ana bilgisayarları için en yüksek sayısını belirtir.|  
|[\<defaultProxy > öğesi (ağ ayarları)](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|İnternet'e HTTP istekleri için kullanılan proxy sunucusunu belirtir.|  
|[\<mailSettings > öğesi (ağ ayarları)](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|Posta gönderme seçeneklerini ayarlarını içerir.|  
|[\<requestCaching > öğesi (ağ ayarları)](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|Ağ istekleri için önbelleğe alma mekanizması denetler.|  
|[\<webRequestModules > öğesi (ağ ayarları)](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|Internet konaklarından bilgi istemek için kullanılan modülleri belirtir.|  
  
 .NET Framework web adresleri Tekdüzen Kaynak Tanımlayıcıları (URI'lar) kullanılarak ifade nasıl işlediğini URI ayarlarını belirtin. Aşağıdaki tabloda her bir alt yapılandırma öğesinin altında işlevi açıklanmaktadır [ \<URI > öğesi (Uri ayarları)](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md).  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<IDN > öğesi (Uri ayarları)](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)|Etki alanı adları için Uluslararası yapılan etki alanı adı (IDN) ayrıştırma uygulanıp uygulanmadığını belirtir.|  
|[\<iriParsing > öğesi (Uri ayarları)](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)|Uluslararası kaynak tanımlayıcı (IRI) ayrıştırma için uygulanmış olup olmadığını belirten bir <xref:System.Uri> ve IRI ayrıştırma kurallarını uygulanıp.|  
|[\<schemeSettings > öğesi (Uri ayarları)](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|Belirtir nasıl bir <xref:System.Uri> belirli düzenleri için ayrıştırılacak.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İnternet Uygulamalarını Yapılandırma](../../../../../docs/framework/network-programming/configuring-internet-applications.md)
- [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)
