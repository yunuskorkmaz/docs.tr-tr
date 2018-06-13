---
title: '&lt;httpWebRequest&gt; öğesi (ağ ayarları)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/httpWebRequest
- http://schemas.microsoft.com/.NetConfiguration/v2.0#httpWebRequest
helpviewer_keywords:
- <httpWebRequest> element
- httpWebRequest element
ms.assetid: 52acd9d2-5bdc-4dc4-9c2a-f0a476ccbb31
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 1d1dce38e5188824ba1412d3f2a285bd2304f147
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32741974"
---
# <a name="lthttpwebrequestgt-element-network-settings"></a>&lt;httpWebRequest&gt; öğesi (ağ ayarları)
Web isteği parametreleri özelleştirir.  
  
 \<Yapılandırma >  
\<system.net>  
\<Ayarlar >  
\<httpWebRequest >  
  
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
  
|**Özniteliği**|**Açıklama**|  
|-------------------|---------------------|  
|`maximumResponseHeadersLength`|Bir yanıt üstbilgisi uzunluğu en fazla kilobayt cinsinden belirtir. 64 varsayılandır. Boyut sınırı yanıt üstbilgileri uygulanan -1 değeri gösterir.|  
|`maximumErrorResponseLength`|Bir hata yanıtı uzunluğu en fazla kilobayt cinsinden belirtir. 64 varsayılandır. Boyut sınırı hata yanıtta uygulanan -1 değeri gösterir.|  
|`maximumUnauthorizedUploadLength`|Karşıya yükleme uzunluğu en fazla bayt bir yetkisiz hata koduna karşılık belirtir. Varsayılan değer -1 ' dir. Boyut sınırı karşıya yükleme sırasında uygulanan -1 değeri gösterir.|  
|`useUnsafeHeaderParsing`|Güvenli olmayan üstbilgi ayrıştırma etkinleştirilip etkinleştirilmeyeceğini belirtir. Varsayılan değer `false` şeklindedir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Öğesi**|**Açıklama**|  
|-----------------|---------------------|  
|[Ayarlar](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|Temel ağ seçeneklerini yapılandırır <xref:System.Net> ad alanı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Varsayılan olarak, .NET Framework kesinlikle RFC 2616 URI ayrıştırmak için zorlar. Bazı sunucu yanıtlarını neden olur, izin verilmeyen alanlarında denetim karakterleri içerebilir <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> throw yöntemi bir <xref:System.Net.WebException>. Varsa **useUnsafeHeaderParsing** ayarlanır **true**, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> oluşturmayacaksa bu durumda; ancak, uygulamanızın saldırıları ayrıştırma URI birkaç formlara savunmasız olacaktır. Sunucu yanıtı denetim karakterleri içermeyen şekilde değiştirmek için en iyi çözüm olur.  
  
## <a name="configuration-files"></a>Yapılandırma Dosyaları  
 Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, daha geniş bir belirtmek gösterilmiştir normal maksimum üstbilgi uzunluğundan.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A>  
 [Ağ Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
