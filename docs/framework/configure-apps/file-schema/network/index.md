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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: c080ff7ebef680712581d1f77fd4eb1ec99c6a86
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742620"
---
# <a name="network-settings-schema"></a>Ağ Ayarları Şeması
Ağ ayarları, .NET Framework Internet'e nasıl bağlanacağını belirtin. Aşağıdaki tabloda her bir alt yapılandırma öğesinin altında işlevi açıklanmaktadır [ \<system.Net > öğesi (ağ ayarları)](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md).  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<authenticationModules > öğesi (ağ ayarları)](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|Internet istekleri kimliğini doğrulamak için kullanılan modülleri belirtir.|  
|[\<connectionManagement > öğesi (ağ ayarları)](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|Internet konaklar bağlantıları en fazla sayısını belirtir.|  
|[\<defaultProxy > öğesi (ağ ayarları)](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|HTTP istekleri Internet için kullanılan proxy sunucusunu belirtir.|  
|[\<mailSettings > öğesi (ağ ayarları)](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|Posta seçenekleri gönderme ayarlarını içerir.|  
|[\<requestCaching > öğesi (ağ ayarları)](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|Internet ana bilgisayarlardan bilgi istemek için kullanılan modülleri belirtir.|  
|[\<requestCaching > öğesi (ağ ayarları)](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|Temel ağ seçeneklerini yapılandırır <xref:System.Net?displayProperty=nameWithType> ad alanı.|  
|[\<webRequestModules > öğesi (ağ ayarları)](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|Internet ana bilgisayarlardan bilgi istemek için kullanılan modülleri belirtir.|  
  
 .NET Framework Tekdüzen Kaynak Tanımlayıcıları (URI'ler) kullanılarak ifade web adresleri nasıl işlediğini URI ayarlarını belirtin. Aşağıdaki tabloda her bir alt yapılandırma öğesinin altında işlevi açıklanmaktadır [ \<URI > öğesi (URI ayarları)](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md).  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<IDN > öğesi (URI ayarları)](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)|Etki alanı adlarının Uluslararası yapılan etki alanı adı (IDN) ayrıştırma uygulanmış olup olmadığını belirtir.|  
|[\<iriParsing > öğesi (URI ayarları)](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)|Uluslararası kaynak tanımlayıcısı (IRI) ayrıştırma için uygulanmış olup olmadığını belirten bir <xref:System.Uri> ve kuralları ayrıştırma IRI uygulanıp.|  
|[\<schemeSettings > öğesi (URI ayarları)](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|Belirtir nasıl bir <xref:System.Uri> için belirli düzenleri ayrıştırılır.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İnternet Uygulamalarını Yapılandırma](../../../../../docs/framework/network-programming/configuring-internet-applications.md)  
 [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)
