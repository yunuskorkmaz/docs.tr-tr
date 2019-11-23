---
title: <uri> Öğesi (Uri Ayarları)
ms.date: 03/30/2017
ms.assetid: c22bab8b-477c-4ae4-8498-65ad409e0847
ms.openlocfilehash: a492baf9951466383ca0277a2927b8554e5bb332
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697434"
---
# <a name="uri-element-uri-settings"></a>\<URI > öğesi (Uri Ayarları)
.NET Framework Tekdüzen Kaynak tanımlayıcıları (URI 'Ler) kullanarak ifade edilen Web adreslerini nasıl işleyeceğini belirten ayarları içerir.  
  
[ **\<Yapılandırma >** ](../configuration-element.md)  
&nbsp;&nbsp; **\<urı >**  
  
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
  
|**Öğe**|**Açıklama**|  
|-----------------|---------------------|  
|[IDN](idn-element-uri-settings.md)|Uluslararası etki alanı adı (ıDN) ayrıştırma 'nın etki alanı adlarına uygulandığını belirtir.|  
|[iriParsing](iriparsing-element-uri-settings.md)|<xref:System.Uri> için uluslararası kaynak tanımlayıcı (IRI) ayrıştırma uygulanıp uygulanmadığını ve IRI ayrıştırma kurallarının uygulanıp uygulanamayacağını belirtir.|  
|[schemeSettings](schemesettings-element-uri-settings.md)|Belirli düzenler için <xref:System.Uri> nasıl ayrıştırılagösterir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Öğe**|**Açıklama**|  
|-----------------|---------------------|  
|[yapılandırmada](../configuration-element.md)|Tüm ad alanları için ayarları içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `uri` öğesi, <xref:System.Net> ad alanındaki sınıflar tarafından kullanılan <xref:System.Uri> sınıfının üyelerine yönelik ayarları içerir. Ayarlar IRI ve ıDN desteğini yapılandırır.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnekte, IRI ayrıştırma ve ıDN adlarını desteklemek için <xref:System.Uri> sınıfı tarafından kullanılan bir yapılandırma gösterilmektedir. Örnek, tüm düzen ayarlarını da temizler ve ardından http şeması için tam olmayan yüzde kodlamalı yol sınırlayıcıları için destek ekler.  
  
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
