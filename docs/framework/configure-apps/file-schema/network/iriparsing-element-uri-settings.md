---
title: <iriParsing> Öğesi (Uri Ayarları)
ms.date: 03/30/2017
ms.assetid: 953d0b53-445e-41f9-b302-77c4030852ce
ms.openlocfilehash: fd617d1b4ac8e532c6f9aeaa01465e9866b059e9
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698099"
---
# <a name="iriparsing-element-uri-settings"></a>\<ıriayrıştırma > öğesi (URI ayarları)
Uluslararası kaynak tanımlayıcı (IRI) ayrıştırmanın bir <xref:System.Uri> uygulanıp uygulanmadığını ve IRI ayrıştırma kurallarının uygulanıp uygulanmayacağını belirtir.  
  
[ **\<Yapılandırma >** ](../configuration-element.md)  
&nbsp;&nbsp;[ **\<URI >** ](uri-element-uri-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp; **\<ıriayrıştırma >**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<iriParsing  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|**Öğe**|**Açıklama**|  
|-----------------|---------------------|  
|`enabled`|IRI ayrıştırma özelliğinin etkinleştirilip etkinleştirilmeyeceğini belirtir. Varsayılan değer `false` şeklindedir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Öğe**|**Açıklama**|  
|-----------------|---------------------|  
|[uri](uri-element-uri-settings.md)|.NET Framework Tekdüzen Kaynak tanımlayıcıları (URI 'Ler) kullanarak ifade edilen Web adreslerini nasıl işleyeceğini belirten ayarları içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Mevcut <xref:System.Uri> sınıfı .NET Framework 3,5 ' de genişletildi. 3,0 SP1 ve 2,0 SP1 uluslararası kaynak tanımlayıcıları (IRI) ve uluslararası etki alanı adları (ıDN) için destek sağlar. IRI ve ıDN desteğini özellikle etkinleştirmedikleri takdirde geçerli kullanıcılar .NET Framework 2,0 davranışından herhangi bir değişiklik görmez. Bu, uygulamanın .NET Framework önceki sürümleriyle uyumluluğunu sağlar.  
  
 IRI desteğini etkinleştirmek için aşağıdaki iki değişiklik gereklidir:  
  
1. Aşağıdaki satırı .NET Framework 2,0 dizinindeki Machine. config dosyasına ekleyin  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. IRI ayrıştırma kurallarının uygulanıp uygulanmayacağını belirtin. Bu, Machine. config veya App. config dosyasında yapılabilir.  
  
 IRI ayrıştırma (ıriayrıştırmayı etkin = `true`) etkinleştirildiğinde, RFC 3987 ' deki en son IRI kurallarına göre normalleştirme ve karakter denetimi yapılır. Varsayılan değer `false`, RFC 2396 ve RFC 3986 ' e (IPv6 sabit değerleri için) göre normalleştirme ve karakter denetimi yapılır.  
  
### <a name="configuration-files"></a>Yapılandırma Dosyaları  
 Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnekte, IRI ayrıştırma ve ıDN adlarını desteklemek için <xref:System.Uri> sınıfı tarafından kullanılan bir yapılandırma gösterilmektedir.  
  
### <a name="code"></a>Kod  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [Ağ Ayarları Şeması](index.md)
