---
title: <iriParsing> Öğesi (Uri Ayarları)
ms.date: 03/30/2017
ms.assetid: 953d0b53-445e-41f9-b302-77c4030852ce
ms.openlocfilehash: ec2610e47957d5560bc7f51e0641afc9ba60c814
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158896"
---
# <a name="iriparsing-element-uri-settings"></a>\<iriParsing> Öğesi (Uri Ayarları)

Uluslararası kaynak tanımlayıcı (IRI) ayrıştırma 'nin bir öğesine uygulanıp uygulanmadığını <xref:System.Uri> ve IRI ayrıştırma kurallarının uygulanıp uygulanamayacağını belirtir.  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<iriParsing>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<iriParsing  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|**Dosyalarında**|**Açıklama**|  
|-----------------|---------------------|  
|`enabled`|IRI ayrıştırma özelliğinin etkinleştirilip etkinleştirilmeyeceğini belirtir. Varsayılan değer: `false`.|  
  
### <a name="child-elements"></a>Alt Öğeler  

 Hiçbiri  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Dosyalarında**|**Açıklama**|  
|-----------------|---------------------|  
|[kullanılmamışsa](uri-element-uri-settings.md)|.NET Framework Tekdüzen Kaynak tanımlayıcıları (URI 'Ler) kullanarak ifade edilen Web adreslerini nasıl işleyeceğini belirten ayarları içerir.|  
  
## <a name="remarks"></a>Açıklamalar  

 Mevcut <xref:System.Uri> sınıf .NET Framework 3,5 ' de genişletildi. 3,0 SP1 ve 2,0 SP1 uluslararası kaynak tanımlayıcıları (IRI) ve uluslararası etki alanı adları (ıDN) için destek sağlar. IRI ve ıDN desteğini özellikle etkinleştirmedikleri takdirde geçerli kullanıcılar .NET Framework 2,0 davranışından herhangi bir değişiklik görmez. Bu, uygulamanın .NET Framework önceki sürümleriyle uyumluluğunu sağlar.  
  
 IRI desteğini etkinleştirmek için aşağıdaki iki değişiklik gereklidir:  
  
1. Aşağıdaki satırı .NET Framework 2,0 dizinindeki machine.config dosyasına ekleyin  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. IRI ayrıştırma kurallarının uygulanıp uygulanmayacağını belirtin. Bu, machine.config veya app.config dosyasında yapılabilir.  
  
 IRI ayrıştırma (ıriayrıştırmayı etkin = `true` ) etkinleştirildiğinde, RFC 3987 ' deki en son IRI kurallarına göre normalleştirme ve karakter denetimi yapılır. Varsayılan değer, `false` rfc 2396 ve rfc 3986 (IPv6 sabit değerleri için) öğesine göre normalleştirme ve karakter denetimi yapar.  
  
### <a name="configuration-files"></a>Yapılandırma Dosyaları  

 Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  

 Aşağıdaki örnek, <xref:System.Uri> IRI ayrıştırma ve IDN adlarını desteklemek için sınıfı tarafından kullanılan bir yapılandırmayı gösterir.  
  
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
- [Ağ ayarları şeması](index.md)
