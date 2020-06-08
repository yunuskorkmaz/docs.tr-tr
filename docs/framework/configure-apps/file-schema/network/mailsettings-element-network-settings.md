---
title: <mailSettings> Öğesi (Ağ Ayarları)
description: <mailSettings>Ağ ayarları öğesi .NET Framework posta gönderme seçeneklerini yapılandırır.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mailSettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings
helpviewer_keywords:
- mailSettings element
- <mailSettings> element
ms.assetid: 54f0f153-17e5-4f49-afdc-deadb940c9c1
ms.openlocfilehash: ce7b8564e4ee5ea73d42259612c077420d36645b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504569"
---
# <a name="mailsettings-element-network-settings"></a>\<mailSettings> Öğesi (Ağ Ayarları)
Posta gönderme seçeneklerini yapılandırır.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<mailSettings>**

## <a name="syntax"></a>Sözdizimi  
  
```xml  
<mailSettings>
  <smtp>...</smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|[\<smtp>Öğesi (ağ ayarları)](smtp-element-network-settings.md)|Basit Posta Aktarım Protokolü seçeneklerini yapılandırır.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Dosyalarında**|**Açıklama**|  
|-----------------|---------------------|  
|[\<system.Net>Öğesi (ağ ayarları)](system-net-element-network-settings.md)|.NET Framework ağa nasıl bağlanacağını belirten ayarları içerir.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, varsayılan ağ kimlik bilgilerini kullanarak e-posta göndermek için uygun SMTP parametrelerini belirtir.  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="Network">  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.Mail.SmtpClient>
- [Ağ Ayarları Şeması](index.md)
