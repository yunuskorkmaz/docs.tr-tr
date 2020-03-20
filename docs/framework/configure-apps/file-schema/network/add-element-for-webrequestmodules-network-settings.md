---
title: webRequestModules için <add> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
helpviewer_keywords:
- <webRequestModules>, add element
- webRequestModules, add element
- add element, webRequestModules
- <add> element, webRequestModules
ms.assetid: 47ec4adc-f39f-4bcd-8680-1ec21fd26890
ms.openlocfilehash: f4edce948033478aab59a2aff61abadc55a327ce
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155030"
---
# <a name="add-element-for-webrequestmodules-network-settings"></a>\<webRequestModules (Ağ Ayarları) için> Öğesi ekle
Uygulamaya özel bir Web isteği modülü ekler.  

[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>ekleyin**

## <a name="syntax"></a>Sözdizimi  
  
```xml  
<add
  prefix="URI prefix"
  type="type_fullname, assembly_fullname"
/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|**Öznitelik**|**Açıklama**|  
|-------------------|---------------------|  
|`prefix`|Bu Web istek modülü tarafından işlenen istekler için URI öneki.|  
|`type`|Tam nitelikli tür adı <xref:System.Type.FullName%2A> (özellik tarafından gösterilir) ve montaj <xref:System.Reflection.Assembly.FullName%2A> adı (özellik tarafından gösterilir), virgülle ayrılmış, bu Web istek modüllerini uygular.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Öğe**|**Açıklama**|  
|-----------------|---------------------|  
|[webRequestModules](webrequestmodules-element-network-settings.md)|Ağ ana bilgisayarlarından bilgi istemek için kullanılacak modülleri belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Öznitelik, `prefix` belirtilen Web isteği modüllerini kullanan URI önekini tanımlar. Web istek modülleri genellikle HTTP veya FTP gibi belirli bir protokolü işlemek için kaydedilir, ancak bir isteği bir sunucuda belirli bir sunucuya veya yola işlemek için kaydedilebilir.  
  
 Uri eşleştirme öneki <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> yönteme geçirildiğinde Web isteği modülü oluşturulur.  
  
 Öznitelik değeri `prefix` geçerli bir URI'nin önde gelen karakterleri olmalıdır. Örneğin `http` veya `http://www.contoso.com` olabilir.
  
 Öznitelik için `type` değer geçerli bir tür adı ve ilgili derleme adı, bir virgül ile ayrılmış olmalıdır.
  
## <a name="configuration-files"></a>Yapılandırma Dosyaları  
 Bu öğe uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte HTTP için özel bir Web isteği modülü kaydedilir. Sürüm ve PublicKeyToken değerlerini belirtilen modül için doğru değerlerle değiştirmelisiniz.  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.WebRequest>
- [Ağ Ayarları Şeması](index.md)
