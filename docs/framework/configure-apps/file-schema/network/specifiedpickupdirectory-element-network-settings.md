---
title: "&lt;specifiedPickupDirectory&gt; öğesi (ağ ayarları)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#specifiedPickupDirectory
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/specifiedPickupDirectory
helpviewer_keywords:
- specifiedPickupDirectory element
- <specifiedPickupDirectory> element
ms.assetid: 0121f49d-bff2-4bc6-af06-f1628dcd61f1
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 0df8cb46943862e3de66faa5551f550cb232f212
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltspecifiedpickupdirectorygt-element-network-settings"></a>&lt;specifiedPickupDirectory&gt; öğesi (ağ ayarları)
Basit Posta Aktarım Protokolü (SMTP) sunucusunun yerel dizin yapılandırır.  
  
 \<Yapılandırma >  
\<System.NET >  
\<mailSettings >  
\<SMTP >  
\<specifiedPickupDirectory >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"   
/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|Uygulamaları daha sonra SMTP sunucusu tarafından işlenmek için e-posta kaydetmek dizin.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<SMTP > öğesi (ağ ayarları)](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|Basit Posta Aktarım Protokolü (SMTP) posta gönderme seçenekleri yapılandırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `specifiedPickupDirectory` Öznitelik uygulamaları posta iletileri SMTP sunucusu tarafından işlenmek üzere kaydetmek dizini ayarlar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek c:\maildrop posta toplama dizini belirtir.  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="specifiedPickupDirectory">  
        <specifiedPickupDirectory  
          pickupDirectoryLocation="c:\maildrop"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>  
 [Ağ Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
