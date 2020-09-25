---
title: <proxy> Öğesi (Ağ Ayarları)
description: <proxy>Ağ ayarları öğesi .NET Framework proxy sunucu seçeneklerini tanımlar. Bu makale bir örnek içerir.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/proxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#proxy
helpviewer_keywords:
- <proxy> element
- proxy element
ms.assetid: 37a548d8-fade-4ac5-82ec-b49b6c6cb22a
ms.openlocfilehash: 54b324dcd27d5827159bc2d773365e388a367d26
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91190221"
---
# <a name="proxy-element-network-settings"></a>\<proxy> Öğesi (Ağ Ayarları)

Bir ara sunucu tanımlar.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<proxy>**

## <a name="syntax"></a>Syntax  
  
```xml  
<proxy
  autoDetect="True|False|Unspecified"
  bypassonlocal="True|False|Unspecified"
  proxyaddress="uriString"
  scriptLocation="uriString"
  usesystemdefault="True|False|Unspecified"
/>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|**Öznitelik**|**Açıklama**|  
|-------------------|---------------------|  
|`autoDetect`|Proxy 'nin otomatik olarak algılanıp algılanmayacağını belirtir. Varsayılan değer: `Unspecified`.|  
|`bypassonlocal`|Yerel kaynaklar için proxy 'nin atlanıp atlanmayacağını belirtir. Yerel sunucu ( `http://localhost` , `http://loopback` , veya `http://127.0.0.1` ) ve nokta () olmayan bir URI 'yi içerir `http://webserver` . Varsayılan değer: `Unspecified`.|  
|`proxyaddress`|Kullanılacak proxy URI 'sini belirtir.|  
|`scriptLocation`|Yapılandırma betiğinin konumunu belirtir. `bypassonlocal`Bu öznitelikle özniteliğini kullanmayın. |  
|`usesystemdefault`|Internet Explorer proxy ayarlarının kullanılıp kullanılmayacağını belirtir. Olarak ayarlanırsa `True` , sonraki öznitelikler Internet Explorer proxy ayarlarını geçersiz kılar. Varsayılan değer: `Unspecified`.|  
  
### <a name="child-elements"></a>Alt Öğeler  

 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Dosyalarında**|**Açıklama**|  
|-----------------|---------------------|  
|[defaultProxy](defaultproxy-element-network-settings.md)|Köprü Metni Aktarım Protokolü (HTTP) proxy sunucusunu yapılandırır.|  
  
## <a name="text-value"></a>Metin Değeri  
  
## <a name="remarks"></a>Açıklamalar  

 `proxy`Öğesi, bir uygulama için ara sunucu tanımlar. Yapılandırma dosyasında bu öğe eksikse .NET Framework, Internet Explorer 'daki proxy ayarlarını kullanacaktır.  
  
 `proxyaddress`Özniteliğin değeri iyi biçimlendirilmiş bir Tekdüzen Kaynak göstergesi (URI) olmalıdır.  
  
 `scriptLocation`Öznitelik, proxy yapılandırma betikleri otomatik olarak algılanmasını ifade eder. <xref:System.Net.WebProxy>Bu sınıf, Internet Explorer 'da **otomatik yapılandırma betiği kullan** seçeneği belirlendiğinde bir yapılandırma betiğini (genellikle WPAD. dat olarak adlandırılır) bulmaya çalışır. `bypassonlocal`Herhangi bir değere ayarlanırsa, `scriptLocation` yok sayılır.
  
 `usesystemdefault`2,0 sürümüne geçiş yapan .NET Framework sürüm 1,1 uygulamaları için özniteliğini kullanın.  
  
 `proxyaddress`Öznitelik geçersiz bir varsayılan proxy belirtiyorsa bir özel durum oluşur. <xref:System.Exception.InnerException%2A>Özel durum üzerindeki özelliği, hatanın kök nedeni hakkında daha fazla bilgi içermelidir.  
  
## <a name="configuration-files"></a>Yapılandırma Dosyaları  

 Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, Internet Explorer proxy 'sinin varsayılan değerlerini kullanır, proxy adresini belirtir ve yerel erişim için ara sunucuyu atlar.  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="True"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="True"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [Ağ ayarları şeması](index.md)
