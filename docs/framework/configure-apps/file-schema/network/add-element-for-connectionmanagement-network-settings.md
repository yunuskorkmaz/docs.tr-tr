---
title: "&lt;ekleme&gt; öğesi connectionManagement (ağ ayarları) için"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/add
helpviewer_keywords:
- <add> element, connectionManagement
- <connectionManagement>, add element
- add element, connectionManagement
- connectionManagement, add element
ms.assetid: 856bf57d-1c63-46c7-a178-03d97b0a4149
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 654ada55d30ad95937fa05475ebcbf23ca86652d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-element-for-connectionmanagement-network-settings"></a>&lt;ekleme&gt; öğesi connectionManagement (ağ ayarları) için
Bir IP adresi veya DNS adı bağlantısı Yönetim listesine ekler.  
  
 \<Yapılandırma >  
\<System.NET >  
\<connectionManagement >  
\<ekleme >  
  
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
  
|**Özniteliği**|**Açıklama**|  
|-------------------|---------------------|  
|`address`|Bir IP adresi veya DNS adını tanımlayan bir dize.|  
|`maxconnection`|Sunucusu için izin verilen bağlantılarının maksimum sayısı. Sağlanmazsa, varsayılan 2'dir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Öğesi**|**Açıklama**|  
|-----------------|---------------------|  
|[connectionManagement](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|Bir ağ ana bilgisayar için bağlantı sayısını belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Değeri `address` özniteliği tüm bağlantıları göstermek için bir yıldız işareti ya da biçiminde bir dize olmalıdır `<schema>://<idn_hostname>[:<port>]`.  
  
 Tüm HTTP API'lerine geçirilen URI Unicode içeriyorsa, adı dahili olarak kullanılarak dönüştürülecek <xref:System.Uri.DnsSafeHost%2A> punicode dize (davranış geçerli IDN yapılandırmasına bağımlı) döndürebilir.  
  
## <a name="configuration-files"></a>Yapılandırma Dosyaları  
 Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir uygulama sunucusu www.contoso.com için dört bağlantıları ve diğer tüm sunucular iki bağlantıları kullanmak için yapılandırır.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Net.ServicePoint>  
 <xref:System.Net.ServicePointManager>  
 [Ağ Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
