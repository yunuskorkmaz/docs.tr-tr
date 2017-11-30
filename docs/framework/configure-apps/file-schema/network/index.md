---
title: "Ağ Ayarları Şeması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ca4a0000d85c8fbac9a723beeda51f9c7886ed8c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [Internet uygulamaları yapılandırma](../../../../../docs/framework/network-programming/configuring-internet-applications.md)  
 [Yapılandırma dosyası şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)
