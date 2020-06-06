---
title: <uri> Öğesi (Uri Ayarları)
ms.date: 03/30/2017
ms.assetid: c22bab8b-477c-4ae4-8498-65ad409e0847
ms.openlocfilehash: a492baf9951466383ca0277a2927b8554e5bb332
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "71697434"
---
# <a name="uri-element-uri-settings"></a>\<uri> Öğesi (Uri Ayarları)
.NET Framework Tekdüzen Kaynak tanımlayıcıları (URI 'Ler) kullanarak ifade edilen Web adreslerini nasıl işleyeceğini belirten ayarları içerir.  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<uri>**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<uri>  
</uri>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|**Dosyalarında**|**Açıklama**|  
|-----------------|---------------------|  
|[IDN](idn-element-uri-settings.md)|Uluslararası etki alanı adı (ıDN) ayrıştırma 'nın etki alanı adlarına uygulandığını belirtir.|  
|[iriParsing](iriparsing-element-uri-settings.md)|Uluslararası kaynak tanımlayıcı (IRI) ayrıştırmanın uygulanıp uygulanmadığını <xref:System.Uri> ve IRI ayrıştırma kurallarının uygulanıp uygulanamayacağını belirtir.|  
|[schemeSettings](schemesettings-element-uri-settings.md)|<xref:System.Uri>Belirli düzenler için nasıl ayrıştırılacaksınız belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Dosyalarında**|**Açıklama**|  
|-----------------|---------------------|  
|[yapılandırmada](../configuration-element.md)|Tüm ad alanları için ayarları içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `uri`Öğesi, <xref:System.Uri> ad alanındaki sınıflar tarafından kullanılan sınıf üyeleri için ayarları içerir <xref:System.Net> . Ayarlar IRI ve ıDN desteğini yapılandırır.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek, <xref:System.Uri> IRI ayrıştırma ve IDN adlarını desteklemek için sınıfı tarafından kullanılan bir yapılandırmayı gösterir. Örnek, tüm düzen ayarlarını da temizler ve ardından http şeması için tam olmayan yüzde kodlamalı yol sınırlayıcıları için destek ekler.  
  
### <a name="code"></a>Kod  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
    <schemeSettings>  
      <clear/>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ağ Ayarları Şeması](index.md)
