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
ms.openlocfilehash: 76dad0c0b75d20627e9f57fd1bb467bf17c9294c
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088508"
---
# <a name="add-element-for-webrequestmodules-network-settings"></a>webRequestModules için > öğesi ekleme \<(ağ ayarları)
Uygulamaya özel bir Web isteği modülü ekler.  

[ **\<configuration >** ](../configuration-element.md) \
[**System. net >\<** ](system-net-element-network-settings.md) &nbsp;&nbsp;\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<webRequestModules**](webrequestmodules-element-network-settings.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<add >**

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
|`prefix`|Bu Web isteği modülü tarafından işlenen istekler için URI ön eki.|  
|`type`|Bu Web istek modülünü uygulayan, tam nitelikli tür adı (<xref:System.Type.FullName%2A> özelliği tarafından belirtilir) ve derleme adı (<xref:System.Reflection.Assembly.FullName%2A> özelliği tarafından belirtilir).|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Öğe**|**Açıklama**|  
|-----------------|---------------------|  
|[webRequestModules](webrequestmodules-element-network-settings.md)|Ağ konaklarından bilgi istemek için kullanılacak modülleri belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `prefix` özniteliği belirtilen Web isteği modülünü kullanan URI önekini tanımlar. Web isteği modülleri, genellikle HTTP veya FTP gibi belirli bir protokolü işlemek için kaydedilir, ancak bir sunucudaki belirli bir sunucuya veya yola yönelik bir isteği işlemek için kayıt yapılabilir.  
  
 Web isteği modülü, <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> yöntemine bir URI eşleştirme öneki geçirildiğinde oluşturulur.  
  
 `prefix` özniteliğin değeri geçerli bir URI 'nin baştaki karakterleri olmalıdır. Örneğin, `http` veya `http://www.contoso.com`.
  
 `type` özniteliğin değeri, virgülle ayrılmış olarak geçerli bir tür adı ve karşılık gelen derleme adı olmalıdır.
  
## <a name="configuration-files"></a>Yapılandırma Dosyaları  
 Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, HTTP için özel bir Web isteği modülü kaydeder. Version ve PublicKeyToken değerlerini belirtilen modülle ilgili doğru değerlerle değiştirmelisiniz.  
  
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
