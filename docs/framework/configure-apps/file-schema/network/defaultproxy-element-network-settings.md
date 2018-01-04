---
title: "&lt;defaultProxy&gt; öğesi (ağ ayarları)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultProxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy
helpviewer_keywords:
- defaultProxy element
- <defaultProxy> element
ms.assetid: 9d663c4b-07b4-4f6f-9b12-efbd3630354f
caps.latest.revision: "21"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: d0b09f5c845fc9a18c2a1dd919272c2924478eaf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltdefaultproxygt-element-network-settings"></a>&lt;defaultProxy&gt; öğesi (ağ ayarları)
Köprü Metni Aktarım Protokolü (HTTP) proxy sunucusu yapılandırır.  
  
 \<Yapılandırma >  
\<System.NET >  
\<defaultProxy >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
      <defaultProxy  
        enabled="true|false"  
        useDefaultCredentials="true|false">  
           <bypasslist> … </bypasslist>  
           <proxy> … </proxy>  
           <module> … </module>  
      </defaultProxy>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|**Öğesi**|**Açıklama**|  
|-----------------|---------------------|  
|`enabled`|Bir web proxy kullanılıp kullanılmayacağını belirtir. Varsayılan değer `true` şeklindedir.|  
|`useDefaultCredentials`|Bu ana bilgisayarın varsayılan kimlik bilgilerini web proxy sunucusuna erişmek için kullanılıp kullanılmayacağını belirtir. Varsayılan değer `false` şeklindedir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|**Öğesi**|**Açıklama**|  
|-----------------|---------------------|  
|[olarak ayarlanıyor](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|Proxy kullanmayın adresleri açıklamak normal bir ifade kümesi sağlar.|  
|[Modülü](../../../../../docs/framework/configure-apps/file-schema/network/module-element-network-settings.md)|Yeni bir proxy modülü uygulamaya ekler.|  
|[Proxy](../../../../../docs/framework/configure-apps/file-schema/network/proxy-element-network-settings.md)|Bir proxy sunucu tanımlar.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Öğesi**|**Açıklama**|  
|-----------------|---------------------|  
|[System.NET](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|.NET Framework ağa nasıl bağlanacağını belirtin ayarları içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 DefaultProxy öğesi boş ise, Internet Explorer proxy ayarları kullanılır. Bu davranış, .NET Framework 1.1 sürümünden farklıdır.  
  
 Bir özel durum [Modülü](../../../../../docs/framework/configure-apps/file-schema/network/module-element-network-settings.md) öğesi genel türü belirttiğinden, türü öğesinden türetilen değil <xref:System.Net.IWebProxy> sınıfı, bu nesnenin varsayılan oluşturucusundan özel durum oluştu ya da bir özel durum oluştu sırada Sistem tarafından belirlenen varsayılan proxy alınıyor. <xref:System.Exception.InnerException%2A> Özel durum özelliği hatasının kök nedeni hakkında daha fazla bilgi sahip olmalıdır.  
  
## <a name="configuration-files"></a>Yapılandırma Dosyaları  
 Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, varsayılan Internet Explorer proxy adlardan kullanır, proxy adresi belirtir ve yerel erişim ve contoso.com için proxy atlar.  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="true"  
      />  
      <bypasslist>  
        <add address="[a-z]+\.contoso\.com" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [Ağ Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
