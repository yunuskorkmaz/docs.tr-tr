---
title: '&lt;ekleme&gt; öğesi olarak ayarlanıyor (ağ ayarları) için'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
helpviewer_keywords:
- <bypasslist>, add element
- bypasslist, add element
- <add> element, bypasslist
- add element, bypasslist
ms.assetid: a0b86e28-86b4-4497-abe8-d5fd614c7926
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: d786d4fd7e6663649408b36fb518db06063ef916
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754525"
---
# <a name="ltaddgt-element-for-bypasslist-network-settings"></a>&lt;ekleme&gt; öğesi olarak ayarlanıyor (ağ ayarları) için
Bir IP adresi veya DNS adı proxy atlama listesine ekler.  
  
 \<Yapılandırma >  
\<system.net>  
\<defaultProxy >  
\<olarak ayarlanıyor >  
\<ekleme >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<add   
  address="regular expression"   
/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|**Özniteliği**|**Açıklama**|  
|-------------------|---------------------|  
|**Adres**|Bir IP adresi veya DNS adı açıklayan bir normal ifade.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Öğesi**|**Açıklama**|  
|-----------------|---------------------|  
|[olarak ayarlanıyor](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|Bir proxy kullanmayın adresleri açıklamak normal bir ifade kümesi sağlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 `add` Öğesi IP adreslerini veya DNS sunucu adları için proxy sunucuyu atla adresleri listesi açıklayan normal ifadeler ekler.  
  
 Değeri `address` özniteliği, bir IP adresi veya ana bilgisayar adlarını açıklar normal bir ifade olmalıdır.  
  
 Bu öğe için normal bir ifade belirtirken dikkatli olmanız gerekir. Normal ifade "[a-z] +\\.contoso\\.com" barındıran tüm contoso.com etki alanı, ancak bunu eşleşmeleri ayrıca contoso.com.cpandl.com etki alanındaki herhangi bir ana eşleşir. Yalnızca bir ana bilgisayar contoso.com etki alanındaki eşleştirmek için bir yer işareti ("$") kullanın: "[a-z] +\\.contoso\\.com$".  
  
 Normal ifadeler hakkında daha fazla bilgi için bkz. [.NET framework normal ifadeleri](../../../../../docs/standard/base-types/regular-expressions.md).  
  
## <a name="configuration-files"></a>Yapılandırma Dosyaları  
 Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte iki adres atlama listesine ekler. İlk contoso.com etki alanındaki tüm sunucular için proxy atlar; İkinci IP adresini başlar 192.168 olan tüm sunucular için proxy atlar.  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
        <add address="[a-z]+\.contoso\.com$" />  
        <add address="192\.168\.\d{1,3}\.\d{1,3}" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [Ağ Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
