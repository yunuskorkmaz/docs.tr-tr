---
title: '&lt;sharedListeners&gt; öğesi'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#sharedListeners
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners
helpviewer_keywords:
- <sharedListeners> element
- listeners
- shared listeners
- trace listeners, <sharedListeners> element
- sharedListeners element
ms.assetid: de200534-19dd-4156-86cf-c50521802c4c
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 57927d09f10e84e73c3da424c283846bd79b5044
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltsharedlistenersgt-element"></a>&lt;sharedListeners&gt; öğesi
Herhangi bir kaynak veya trace ögesi başvurabilir dinleyicileri içerir.  Bu dinleyicileri varsayılan olarak tüm izlemeleri almaz ve bu dinleyicileri çalışma zamanında almak mümkün değildir. Paylaşılan dinleyiciler tanımlanan dinleyicileri kaynakları veya izlemeleri adıyla eklenebilir.  
  
 \<Yapılandırma >  
\<System.Diagnostics >  
\<sharedListeners >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<sharedListeners>   
  <add>...</add>  
</sharedListeners>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<ekleme >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-trace.md)|Bir dinleyici ekler `sharedListeners` koleksiyonu.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`Configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`system.diagnostics`|ASP.NET yapılandırma bölümü için kök öğesi belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Paylaşılan dinleyiciler koleksiyona bir dinleyici ekleme etkin olan bir dinleyici yapmaz. Bunu hala bir izleme kaynağı veya bir izleme ekleyerek eklenmelidir `Listeners` söz konusu izleme öğenin koleksiyonu. .NET Framework dinleyicisi sınıflarda türetin <xref:System.Diagnostics.TraceListener> sınıfı.  
  
 Bu öğe makine yapılandırma dosyası (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte nasıl kullanılacağını gösterir `<sharedListeners>` dinleyicisi eklemek için öğesi `console` için `Listeners` koleksiyonu her ikisi için de <xref:System.Diagnostics.TraceSource> ve <xref:System.Diagnostics.Trace> sınıfları. Konsol İzleme dinleyicisi izleme bilgilerini ya da çağrıları aracılığıyla konsola yazar <xref:System.Diagnostics.TraceSource> veya <xref:System.Diagnostics.Trace>.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sharedListeners>  
      <add name="console" type="System.Diagnostics.ConsoleTraceListener" >  
        <filter type="System.Diagnostics.EventTypeFilter"  
          initializeData="Warning" />  
      </add>  
    </sharedListeners>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"  >  
        <listeners>  
          <add name="console" />  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Verbose"/>  
    </switches>  
    <trace>  
      <listeners>  
        <add name="console" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration></system.diagnostics>   
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Diagnostics.TraceListener>  
 [İzleme ve Hata Ayıklama Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [İzleme Dinleyicileri](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
