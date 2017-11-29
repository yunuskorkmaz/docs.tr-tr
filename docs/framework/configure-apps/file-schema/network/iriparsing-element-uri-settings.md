---
title: "&lt;iriParsing&gt; öğesi (URI ayarları)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 953d0b53-445e-41f9-b302-77c4030852ce
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: aad2ea9a9255a6fc11465bae92f693065db21cb3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltiriparsinggt-element-uri-settings"></a>&lt;iriParsing&gt; öğesi (URI ayarları)
Uluslararası kaynak tanımlayıcısı (IRI) ayrıştırma için uygulanmış olup olmadığını belirten bir <xref:System.Uri> ve kuralları ayrıştırma IRI uygulanıp.  
  
## <a name="schema-hierarchy"></a>Şema hiyerarşisi  
 [\<Yapılandırma > öğesi](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<URI > öğesi (URI ayarları)](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
 [\<iriParsing >](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<iriParsing  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|**Öğesi**|**Açıklama**|  
|-----------------|---------------------|  
|`enabled`|IRI ayrıştırma etkinleştirilip etkinleştirilmeyeceğini belirtir. Varsayılan değer `false` şeklindedir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Öğesi**|**Açıklama**|  
|-----------------|---------------------|  
|[URI](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|.NET Framework Tekdüzen Kaynak Tanımlayıcıları (URI'ler) kullanılarak ifade web adresleri işleme biçimini belirten ayarları içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Varolan <xref:System.Uri> sınıf .NET Framework 3. 5 ' genişletilmişse. 3.0 SP1 ve 2.0 SP1 uluslararası kaynak tanımlayıcıları (IRI) ve Uluslararası yapılan etki alanı adları (IDN) desteği sağlamak için. Geçerli kullanıcı özellikle IRI ve IDN etkinleştirmediğiniz sürece herhangi bir değişiklik .NET Framework 2.0 davranış görmezsiniz destekler. Bu, .NET Framework'ün önceki sürümler ile uygulama uyumluluğunu sağlar.  
  
 IRI desteğini etkinleştirmek için aşağıdaki iki değişiklik gereklidir:  
  
1.  .NET Framework 2.0 dizini altındaki machine.config dosyasının aşağıdaki satırı ekleyin  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2.  Kuralları ayrıştırma IRI uygulanmış olup olmadığını belirtin. Machine.config veya app.config dosyasında yapılabilir.  
  
 IRI ayrıştırma etkinleştirme (etkin iriParsing = `true`) normalleştirme ne yapacağını ve en son IRI göre denetimi karakter 3987 RFC kuralları. Varsayılan değer `false` ve normalleştirme yapın ve RFC 2396 göre denetleme ve RFC 3986 (IPv6 değişmez değerleri için) karakter.  
  
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
 <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 [Ağ Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
