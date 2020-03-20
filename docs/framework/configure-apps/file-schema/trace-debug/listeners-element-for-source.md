---
title: <source> için <listeners> öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners
helpviewer_keywords:
- listeners element for <source>
- <listeners> element for <source>
ms.assetid: a2991f43-b4d3-4614-a8e7-da392de9697f
ms.openlocfilehash: 0eee325e01b41a15a19e4f40f479596f9d70f73b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153418"
---
# <a name="listeners-element-for-source"></a>\<kaynak> için \<Element> dinleyici
<xref:System.Diagnostics.TraceSource.Listeners%2A> Koleksiyondaki dinleyicileri ekler veya kaldırır. <xref:System.Diagnostics.TraceSource> Dinleyici, izleme çıktısını günlük, pencere veya metin dosyası gibi uygun bir hedefe yönlendirir.  
  
[**\<yapılandırma>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<kaynaklar>**](sources-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<kaynak>**](source-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dinleyici ler>**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<listeners>
  <add>...</add>  
  <remove ... />  
  <clear/>  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<>ekleyin](add-element-for-listeners-for-source.md)|`Listeners` Koleksiyona bir dinleyici ekler.|  
|[\<>kaldırmak](remove-element-for-listeners-for-source.md)|Dinleyiciyi `Listeners` koleksiyondan kaldırır.|  
|[\<açık>](clear-element-for-listeners-for-source.md)|Bir izleme `Listeners` kaynağı için koleksiyonu temizler.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`system.diagnostics`|İletileri toplayan, depolayan ve yönlendiren izleme dinleyicilerini ve izleme anahtarının ayarlandığı düzeyi belirtir.|  
|`sources`|İletileri izlemeyi başlatan izleme kaynakları içerir.|  
|`source`|İletilerin izlenmesini başlatan bir izleme kaynağı belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="configuration-file"></a>Yapılandırma Dosyası  
 Bu öğe makine yapılandırma dosyasında (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, kaynağa `<listeners>` konsol izleme dinleyicisi eklemek `mySource` ve varsayılan izleme dinleyicisini kaldırmak için öğenin nasıl kullanılacağını gösterir.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console"
            type="System.Diagnostics.ConsoleTraceListener">  
            <filter type="System.Diagnostics.EventTypeFilter"
              initializeData="Error"/>  
          </add>  
          <remove name="Default"/>  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Diagnostics.TraceListener>
- [İzleme ve Hata Ayıklama Ayarları Şeması](index.md)
- [İz Dinleyicileri](../../../debug-trace-profile/trace-listeners.md)
