---
title: <httpWebRequest> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/httpWebRequest
- http://schemas.microsoft.com/.NetConfiguration/v2.0#httpWebRequest
helpviewer_keywords:
- <httpWebRequest> element
- httpWebRequest element
ms.assetid: 52acd9d2-5bdc-4dc4-9c2a-f0a476ccbb31
ms.openlocfilehash: d33dadc14510feb00e05ca557b507b0cf8fa0dd0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74087453"
---
# <a name="httpwebrequest-element-network-settings"></a>\<httpWebRequest> Öğesi (Ağ Ayarları)
Web isteği parametrelerini özelleştirir.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpWebRequest>**

## <a name="syntax"></a>Sözdizimi  
  
```xml  
<httpWebRequest  
  maximumResponseHeadersLength="size"  
  maximumErrorResponseLength="size"  
  maximumUnauthorizedUploadLength="size"  
  useUnsafeHeaderParsing="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|**Öznitelik**|**Açıklama**|  
|-------------------|---------------------|  
|`maximumResponseHeadersLength`|Yanıt üst bilgisinin kilobayt cinsinden uzunluk üst sınırını belirtir. Varsayılan değer 64 ' dir. -1 değeri, yanıt üst bilgilerine hiçbir boyut sınırının kullanılmayacağını gösterir.|  
|`maximumErrorResponseLength`|Bir hata yanıtının kilobayt cinsinden uzunluk üst sınırını belirtir. Varsayılan değer 64 ' dir. -1 değeri, hata yanıtına hiçbir boyut sınırının kullanılamayacağını gösterir.|  
|`maximumUnauthorizedUploadLength`|Yetkisiz bir hata koduna yanıt olarak, bir karşıya yükleme işleminin bayt cinsinden uzunluk üst sınırını belirtir. Varsayılan değer-1 ' dir. -1 değeri, karşıya yükleme sırasında hiçbir boyut sınırının kullanılamayacağını gösterir.|  
|`useUnsafeHeaderParsing`|Güvenli olmayan üstbilgi ayrıştırma özelliğinin etkinleştirilip etkinleştirilmeyeceğini belirtir. Varsayılan değer: `false`.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Dosyalarında**|**Açıklama**|  
|-----------------|---------------------|  
|[ayarlar](settings-element-network-settings.md)|Ad alanı için temel ağ seçeneklerini yapılandırır <xref:System.Net> .|  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework, varsayılan olarak, URI ayrıştırma için RFC 2616 ' i kesinlikle uygular. Bazı sunucu yanıtları yasaklanmış alanlardaki denetim karakterlerini içerebilir ve bu, metodun bir oluşturmasına neden olur <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> <xref:System.Net.WebException> . **Useunsafeheaderayrıştırma** **true**olarak ayarlanırsa, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> Bu durumda throw olmaz; ancak, uygulamanız bazı URI ayrıştırma saldırılarına karşı savunmasız olacaktır. En iyi çözüm, yanıtın denetim karakterleri içermediği şekilde sunucuyu değiştirmemelidir.  
  
## <a name="configuration-files"></a>Yapılandırma Dosyaları  
 Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, normal en büyük üstbilgi uzunluğundan daha büyük bir değer belirtmeyi gösterir.  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <httpWebRequest  
        maximumResponseHeadersLength="128"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A>
- [Ağ Ayarları Şeması](index.md)
