---
title: bypasslist için <add> Öğesi (Ağ Ayarları)
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
ms.openlocfilehash: 652b8738a201aaa98fa2c5c435fee1a6da91673b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155083"
---
# <a name="add-element-for-bypasslist-network-settings"></a>\<bypasslist (Ağ Ayarları) için> Öğesi ekle
Proxy bypass listesine bir IP adresi veya DNS adı ekler.  
  
[**\<yapılandırma>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>ekleyin**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<add
  address="regular expression"
/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|**Öznitelik**|**Açıklama**|  
|-------------------|---------------------|  
|**Adres**|BIR IP adresi veya DNS adını açıklayan normal bir ifade.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Öğe**|**Açıklama**|  
|-----------------|---------------------|  
|[Bypasslist](bypasslist-element-network-settings.md)|Proxy kullanmayan adresleri açıklayan bir dizi düzenli ifade sağlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Öğe, `add` ip adreslerini veya DNS sunucu adlarını açıklayan düzenli ifadeler ekler ve proxy sunucusunu atlayan adresler listesine eklenir.  
  
 Öznitelik değeri `address` IP adresleri veya ana bilgisayar adları kümesi açıklayan normal bir ifade olmalıdır.  
  
 Bu öğe için düzenli bir ifade belirtirken dikkatli olmalısınız. Normal ifade "[a-z]+\\.contoso\\.com" contoso.com etki alanında herhangi bir ana bilgisayar eşleşir, ancak aynı zamanda contoso.com.cpandl.com etki alanında herhangi bir ana bilgisayar eşleşir. Yalnızca contoso.com etki alanında bir ana bilgisayarla eşleştirmek için bir bağlantı ("$"): "[a-z]+\\.contoso\\.com$" kullanın.  
  
 Normal ifadeler hakkında daha fazla bilgi için bkz. [.NET Framework Düzenli İfadeler](../../../../standard/base-types/regular-expressions.md).  
  
## <a name="configuration-files"></a>Yapılandırma Dosyaları  
 Bu öğe uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, baypas listesine iki adres ekler. İlki, contoso.com etki alanında bulunan tüm sunucular için proxy'yi atlar; ikincisi, IP adresi 192.168 ile başlayan tüm sunucular için proxy'yi atlar.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [Ağ Ayarları Şeması](index.md)
