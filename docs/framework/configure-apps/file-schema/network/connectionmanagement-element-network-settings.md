---
title: <connectionManagement> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement
- http://schemas.microsoft.com/.NetConfiguration/v2.0#connectionManagement
helpviewer_keywords:
- <connectionManagement> element
- connectionManagement element
ms.assetid: bedccaab-12a2-4511-8f67-e961f249aec6
ms.openlocfilehash: b769dd8d3ed0c617d0d8f908e7ef516615da09a7
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088454"
---
# <a name="connectionmanagement-element-network-settings"></a>\<connectionManagement > öğesi (ağ ayarları)
Bir ağ konağına en fazla bağlantı sayısını belirtir.  

[ **\<configuration >** ](../configuration-element.md) \
[**System. net >\<** ](system-net-element-network-settings.md) &nbsp;&nbsp;\
&nbsp;&nbsp;&nbsp;&nbsp; **\<connectionManagement >**

## <a name="syntax"></a>Sözdizimi  
  
```xml  
<connectionManagement>   
</connectionManagement>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|**Öğe**|**Açıklama**|  
|-----------------|---------------------|  
|[add](add-element-for-connectionmanagement-network-settings.md)|Bağlantı yönetimi listesine bir IP adresi veya DNS adı ekler.|  
|[lediğiniz](clear-element-for-connectionmanagement-network-settings.md)|Bağlantı yönetimi listesini temizler.|  
|[remove](remove-element-for-connectionmanagement-network-settings.md)|Bağlantı yönetimi listesinden bir IP adresini veya DNS adını kaldırır.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Öğe**|**Açıklama**|  
|-----------------|---------------------|  
|[system.net](system-net-element-network-settings.md)|.NET Framework ağa nasıl bağlanacağını belirten ayarları içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `connectionManagement` öğesi, bir sunucu veya sunucu grubu için en fazla bağlantı sayısını tanımlar.  
  
## <a name="configuration-files"></a>Yapılandırma Dosyaları  
 Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir uygulamayı sunucu `www.contoso.com` dört bağlantı ve diğer tüm sunuculara iki bağlantı kullanacak şekilde yapılandırır.  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <add address = "http://www.contoso.com" maxconnection = "4" />  
      <add address = "*" maxconnection = "2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [Ağ Ayarları Şeması](index.md)
