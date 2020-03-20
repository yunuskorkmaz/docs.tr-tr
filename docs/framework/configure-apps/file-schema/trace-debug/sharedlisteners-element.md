---
title: <sharedListeners> Öğesi
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
ms.openlocfilehash: 69f15cc9583b397017ac30a0c567914495867c18
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153327"
---
# <a name="sharedlisteners-element"></a>\<sharedListeners> Element
Herhangi bir kaynak veya izleme öğesinin başvuruedebileceği dinleyicileri içerir.  Bu dinleyiciler varsayılan olarak herhangi bir iz almazlar ve bu dinleyicileri çalışma zamanında almak mümkün değildir. Paylaşılan dinleyici olarak tanımlanan dinleyiciler kaynaklara veya izadile eklenebilir.  
  
[**\<yapılandırma>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<paylaşılanDinleyiciler>**  
  
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
|[\<>ekleyin](add-element-for-listeners-for-trace.md)|`sharedListeners` Koleksiyona bir dinleyici ekler.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`Configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`system.diagnostics`|ASP.NET yapılandırma bölümünün kök öğesini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Paylaşılan dinleyici koleksiyonuna dinleyici eklemek onu etkin bir dinleyici yapmaz. Yine de bir izleme kaynağına veya bir izleme `Listeners` için bu izleme öğesi için koleksiyona ekleyerek eklenmelidir. .NET Framework'deki dinleyici sınıfları sınıftan <xref:System.Diagnostics.TraceListener> türetilmiştir.  
  
 Bu öğe makine yapılandırma dosyasında (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, dinleyiciyi `<sharedListeners>` `Listeners` hem sınıflar hem `console` de <xref:System.Diagnostics.Trace> sınıflar için <xref:System.Diagnostics.TraceSource> koleksiyona eklemek için öğenin nasıl kullanılacağını gösterir. Konsol izleme dinleyicisi ya da <xref:System.Diagnostics.TraceSource> <xref:System.Diagnostics.Trace>aramalar yoluyla konsola izleme bilgileri yazar.  
  
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
</configuration>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Diagnostics.TraceListener>
- [İzleme ve Hata Ayıklama Ayarları Şeması](index.md)
- [İz Dinleyicileri](../../../debug-trace-profile/trace-listeners.md)
