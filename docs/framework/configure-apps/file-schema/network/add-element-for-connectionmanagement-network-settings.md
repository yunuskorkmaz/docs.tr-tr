---
title: connectionManagement için <add> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/add
helpviewer_keywords:
- <add> element, connectionManagement
- <connectionManagement>, add element
- add element, connectionManagement
- connectionManagement, add element
ms.assetid: 856bf57d-1c63-46c7-a178-03d97b0a4149
ms.openlocfilehash: 093b68d31e03094bedefa96a2f2d53eb3d84edf0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155017"
---
# <a name="add-element-for-connectionmanagement-network-settings"></a>\<bağlantı Yönetimi için> Öğesi ekle (Ağ Ayarları)
Bağlantı yönetim listesine bir IP adresi veya DNS adı ekler.  

[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bağlantıYönetim>**](connectionmanagement-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>ekleyin**

## <a name="syntax"></a>Sözdizimi  
  
```xml  
<add
  address="address expression"
  maxconnection="integer"
/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|**Öznitelik**|**Açıklama**|  
|-------------------|---------------------|  
|`address`|IP adresini veya DNS adını açıklayan dize.|  
|`maxconnection`|Sunucuya izin verilen maksimum bağlantı sayısı. Sağlanmazsa, varsayılan değer 2'dir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Öğe**|**Açıklama**|  
|-----------------|---------------------|  
|[bağlantıYönetim](connectionmanagement-element-network-settings.md)|Bir ağ ana bilgisayarına en fazla bağlantı sayısını belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Özniteliğin `address` değeri, tüm bağlantıları belirtmek için bir yıldız işareti veya formun `<schema>://<idn_hostname>[:<port>]`bir dizesi olmalıdır.  
  
 URI herhangi bir HTTP API'sine geçtiyse Unicode içeriyorsa, ad bir punicode dizesi (geçerli IDN yapılandırmasına bağlı davranış) döndürebilecek <xref:System.Uri.DnsSafeHost%2A> şekilde dahili olarak dönüştürülür.  
  
## <a name="configuration-files"></a>Yapılandırma Dosyaları  
 Bu öğe uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir uygulamayı sunucuya `www.contoso.com` dört, diğer tüm sunuculara iki bağlantı kullanacak şekilde yapılandırır.  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <add address="http://www.contoso.com" maxconnection="4" />  
      <add address="*" maxconnection="2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [Ağ Ayarları Şeması](index.md)
