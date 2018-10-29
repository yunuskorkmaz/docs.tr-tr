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
ms.openlocfilehash: 0d3feb168acbd623270a2038bf06a3c97126bd05
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50205158"
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
  
|**Öznitelik**|**Açıklama**|  
|-------------------|---------------------|  
|`maximumResponseHeadersLength`|Bir yanıt üstbilgisinin maksimum uzunluğunu kilobayt cinsinden belirtir. 64 varsayılandır. Boyut sınırı üzerinde yanıt üstbilgilerini uygulanan -1 değeri gösterir.|  
|`maximumErrorResponseLength`|Bir hata yanıtı uzunluğu en fazla kilobayt cinsinden belirtir. 64 varsayılandır. Boyut sınırı üzerinde hata yanıtı uygulanan -1 değeri gösterir.|  
|`maximumUnauthorizedUploadLength`|Karşıya yükleme uzunluğu en fazla bayt cinsinden bir yetkisiz hata koduna karşılık belirtir. Varsayılan değer -1'dir. Boyut sınırı karşıya yükleme sırasında uygulanan -1 değeri gösterir.|  
|`useUnsafeHeaderParsing`|Güvenli olmayan bir üst bilgi ayrıştırma etkinleştirilip etkinleştirilmeyeceğini belirtir. Varsayılan değer `false` şeklindedir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Öğe**|**Açıklama**|  
|-----------------|---------------------|  
|[Ayarlar](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|Temel ağ seçeneklerini yapılandırır <xref:System.Net> ad alanı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Varsayılan olarak, .NET Framework kesinlikle RFC 2616'urı ayrıştırmak için zorlar. Bazı sunucu yanıtları neden olur, izin verilmeyen alanlarına bir denetim karakteri içerebilir <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> yönteminin bir <xref:System.Net.WebException>. Varsa **useUnsafeHeaderParsing** ayarlanır **true**, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> oluşturmayacaksa bu durumda; ancak, uygulamanız URI saldırıları ayrıştırma birkaç biçimlerinin savunmasız olacaktır. En uygun çözümü sunucu yanıt denetim karakterleri içermeyen şekilde değiştirmektir.  
  
## <a name="configuration-files"></a>Yapılandırma Dosyaları  
 Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir büyük belirtmek gösterilmektedir normal maksimum üstbilgi uzunluğundan.  
  
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
- <xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A>  
- [Ağ Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
