---
title: "&lt;mailSettings&gt; öğesi (ağ ayarları)"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mailSettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings
helpviewer_keywords:
- mailSettings element
- <mailSettings> element
ms.assetid: 54f0f153-17e5-4f49-afdc-deadb940c9c1
caps.latest.revision: "20"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 5ae9ecdfa9cccb7c70c153153b921151aad50e7c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltmailsettingsgt-element-network-settings"></a>&lt;mailSettings&gt; öğesi (ağ ayarları)
Posta gönderme seçenekleri yapılandırır.  

\<Yapılandırma >  
\<System.NET >  
\<mailSettings >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<mailSettings>
  <smtp> … </smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|[\<SMTP > öğesi (ağ ayarları)](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|Basit Posta Aktarım Protokolü seçenekleri yapılandırır.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Öğesi**|**Açıklama**|  
|-----------------|---------------------|  
|[\<system.Net > öğesi (ağ ayarları)](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|.NET Framework ağa nasıl bağlanacağını belirtin ayarları içerir.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, varsayılan ağ kimlik bilgilerini kullanarak e-posta göndermek için uygun SMTP parametreleri belirtir.  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="network">  
        <network  
          host="localhost"  
          port="25"  
          defaultCredentials="true"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Net.Mail.SmtpClient>  
 [Ağ Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
