---
title: <idn> Öğesi (Uri Ayarları)
ms.date: 03/30/2017
ms.assetid: 16c8e869-1791-4cf5-9244-3d3c738f60ec
ms.openlocfilehash: f45922ecd5f7476362aab5348d91415d8e31c53f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195408"
---
# <a name="idn-element-uri-settings"></a>\<idn> Öğesi (Uri Ayarları)

Uluslararası etki alanı adı (ıDN) ayrıştırmanın bir etki alanı adına uygulandığını belirtir.
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<idn>**  
  
## <a name="syntax"></a>Syntax  
  
```xml
<idn
  enabled="All|AllExceptIntranet|None"
/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  

|**Dosyalarında**|**Açıklama**|  
|-----------------|---------------------|  
|`enabled`|Uluslararası etki alanı adı (ıDN) ayrıştırmanın bir etki alanı adına uygulandığını belirtir varsayılan değer None ' dır.|  

### <a name="child-elements"></a>Alt öğeleri

Yok
  
### <a name="parent-elements"></a>Üst öğeler

|**Dosyalarında**|**Açıklama**|  
|-----------------|---------------------|  
|[kullanılmamışsa](uri-element-uri-settings.md)|.NET Framework Tekdüzen Kaynak tanımlayıcıları (URI 'Ler) kullanarak ifade edilen Web adreslerini nasıl işleyeceğini belirten ayarları içerir.|  

## <a name="remarks"></a>Açıklamalar

Mevcut <xref:System.Uri> sınıf .NET Framework 3,5 ' de genişletildi. 3,0 SP1 ve 2,0 SP1 uluslararası kaynak tanımlayıcıları (IRI) ve uluslararası etki alanı adları (ıDN) desteğiyle desteklenir. IRI ve ıDN desteğini özellikle etkinleştirmedikleri takdirde geçerli kullanıcılar .NET Framework 2,0 davranışından herhangi bir değişiklik görmez. Bu, uygulamanın .NET Framework önceki sürümleriyle uyumluluğunu sağlar.

IRI desteğini etkinleştirmek için aşağıdaki iki değişiklik gereklidir:

1. Aşağıdaki satırı .NET Framework 2,0 dizinindeki machine.config dosyasına ekleyin:
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. Uluslararası etki alanı adı (ıDN) ayrıştırmayı etki alanı adına uygulanıp uygulanmayacağını ve IRI ayrıştırma kurallarının uygulanıp uygulanmayacağını belirtin. Bu, machine.config veya app.config dosyasında yapılabilir.

 Kullanılan DNS sunucularına bağlı olarak ıDN için üç olası değer vardır:

- IDN etkin = tümü  

     Bu değer, herhangi bir Unicode etki alanı adını, zayıf kod eşdeğerlerine (ıDN adları) dönüştürür.

- IDN etkin = AllExceptIntranet

     Bu değer, yerel Intranette bulunmayan tüm Unicode etki alanı adlarını, Punyıcode eşdeğerlerini (ıDN adları) kullanacak şekilde dönüştürür. Bu durumda, yerel Intranetteki uluslararası adları işlemek için, Intranet için kullanılan DNS sunucularının Unicode ad çözümlemesini desteklemesi gerekir.

- IDN etkin = yok

     Bu değer, herhangi bir Unicode etki alanı adını Punyıcode kullanacak şekilde dönüştürmez. Bu, .NET Framework 2,0 davranışıyla tutarlı olan varsayılan değerdir.

 IDN 'yi etkinleştirmek, bir etki alanı adındaki tüm Unicode etiketlerini atlama kodu eşdeğerlerine dönüştürür. Puni Code adları yalnızca ASCII karakterleri içerir ve her zaman xn--önekiyle başlar. Bunun nedeni, DNS sunucularının çoğu yalnızca ASCII karakterlerini desteklediği için Internet 'teki mevcut DNS sunucularını desteklemedir (bkz. RFC 3940).

### <a name="configuration-files"></a>Yapılandırma dosyaları

Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, <xref:System.Uri> IRI ayrıştırma ve IDN adlarını desteklemek için sınıfı tarafından kullanılan bir yapılandırmayı gösterir:

```xml
<configuration>
  <uri>
    <idn enabled="All" />
    <iriParsing enabled="true" />
  </uri>
</configuration>
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Configuration.IdnElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [Ağ ayarları şeması](index.md)
