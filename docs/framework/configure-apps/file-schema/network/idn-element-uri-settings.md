---
title: '&lt;IDN&gt; öğesi (URI ayarları)'
ms.date: 03/30/2017
ms.assetid: 16c8e869-1791-4cf5-9244-3d3c738f60ec
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 17f68fbb92797928be911e530232e8638793687f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742578"
---
# <a name="ltidngt-element-uri-settings"></a>&lt;IDN&gt; öğesi (URI ayarları)
Bir etki alanı adı Uluslararası yapılan etki alanı adı (IDN) ayrıştırma uygulanmış olup olmadığını belirtir.  
  
## <a name="schema-hierarchy"></a>Şema hiyerarşisi  
 [\<Yapılandırma > öğesi](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<URI > öğesi (URI ayarları)](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
 [\<IDN >](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<idn  
  enabled="All|AllExceptIntranet|None"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|**Öğesi**|**Açıklama**|  
|-----------------|---------------------|  
|`enabled`|Bir etki alanı adı Uluslararası yapılan etki alanı adı (IDN) ayrıştırma uygulanırsa Yok'tur varsayılan değer belirtir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Öğesi**|**Açıklama**|  
|-----------------|---------------------|  
|[URI](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|.NET Framework Tekdüzen Kaynak Tanımlayıcıları (URI'ler) kullanılarak ifade web adresleri işleme biçimini belirten ayarları içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Varolan <xref:System.Uri> sınıf .NET Framework 3. 5 ' genişletilmişse. 3.0 SP1 ve 2.0 SP1 uluslararası kaynak tanımlayıcıları (IRI) ve Uluslararası yapılan etki alanı adları (IDN) desteği. Geçerli kullanıcı özellikle IRI ve IDN etkinleştirmediğiniz sürece herhangi bir değişiklik .NET Framework 2.0 davranış görmezsiniz destekler. Bu, .NET Framework'ün önceki sürümler ile uygulama uyumluluğunu sağlar.  
  
 IRI desteğini etkinleştirmek için aşağıdaki iki değişiklik gereklidir:  
  
1.  .NET Framework 2.0 dizini altındaki machine.config dosyasının aşağıdaki satırı ekleyin  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2.  Uluslararası yapılan etki alanı adı (IDN) ayrıştırma için etki alanı adı uygulanan isteyip istemediğinizi ve kuralları ayrıştırma IRI uygulanıp belirtin. Machine.config veya app.config dosyasında yapılabilir.  
  
 IDN için kullanılan DNS sunucularını bağlı olarak üç olası değerler şunlardır:  
  
-   Etkin IDN = All  
  
     Bu değer, zayıf kod eşdeğerlerine (IDN adları) Unicode etki alanı adlarını dönüştürür.  
  
-   Etkin IDN AllExceptIntranet =  
  
     Bu değer Punycode eşdeğerleri (IDN adları) kullanmak için değil yerel Intranet üzerindeki tüm Unicode etki alanı adlarını dönüştürür. Bu durumda yerel Intranet üzerindeki uluslararası adları işlemek için Intranet için kullanılan DNS sunucularını Unicode ad çözümlemesi desteklemelidir.  
  
-   Etkin IDN = yok  
  
     Bu değer, zayıf kod kullanmak için Unicode etki alanı adlarını dönüşmez. .NET Framework 2.0 davranışa tutarlı olan varsayılan değer budur.  
  
 Bir etki alanı adındaki tüm Unicode etiketleri IDN etkinleştirme Punycode eşdeğerlerine dönüştürür. Zayıf kod adları yalnızca ASCII karakterler içeren ve her zaman xn--önekiyle başlatın. Bunun nedeni çoğu DNS sunucuları, yalnızca ASCII karakterleri (RFC 3940 bakın) destekler beri Internet'te var olan DNS sunucuları desteklemektir.  
  
### <a name="configuration-files"></a>Yapılandırma Dosyaları  
 Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek tarafından kullanılan bir yapılandırma gösterir <xref:System.Uri> IRI ayrıştırma ve IDN adları desteklemek için sınıf.  
  
### <a name="code"></a>Kod  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Configuration.IdnElement?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 [Ağ Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
