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
ms.openlocfilehash: 41cabcbce13409b0842cbbd625028b51d32d59d0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926977"
---
# <a name="sharedlisteners-element"></a>\<sharedListeners > öğesi
Herhangi bir kaynak veya izleme öğesinin başvurmasına yönelik dinleyicileri içerir.  Bu dinleyiciler, varsayılan olarak herhangi bir izleme almaz ve çalışma zamanında bu dinleyicileri almak mümkün değildir. Paylaşılan dinleyiciler ada göre kaynaklara veya izlemelere eklenebilir olarak tanımlanan dinleyiciler.  
  
 \<Yapılandırma >  
\<System. Diagnostics >  
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
|[\<> Ekle](add-element-for-listeners-for-trace.md)|`sharedListeners` Koleksiyona bir dinleyici ekler.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`Configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`system.diagnostics`|ASP.NET yapılandırma bölümünün kök öğesini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Paylaşılan dinleyiciler koleksiyonuna dinleyici eklemek, etkin bir dinleyici yapmaz. Yine de bu izleme öğesi için `Listeners` koleksiyona ekleyerek bir izleme kaynağına veya bir izlemeye eklenmeli. .NET Framework dinleyici sınıfları <xref:System.Diagnostics.TraceListener> sınıfından türetilir.  
  
 Bu öğe makine yapılandırma dosyasında (Machine. config) ve uygulama yapılandırma dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  
 `<sharedListeners>` Aşağıdaki örnek, <xref:System.Diagnostics.TraceSource> ve `Listeners` `console` sınıflarının<xref:System.Diagnostics.Trace> her ikisi için de dinleyiciyi koleksiyona eklemek için öğesinin nasıl kullanılacağını gösterir. Konsol izleme dinleyicisi, <xref:System.Diagnostics.TraceSource> veya <xref:System.Diagnostics.Trace>çağrıları aracılığıyla konsola izleme bilgilerini yazar.  
  
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
- [İzleme Dinleyicileri](../../../debug-trace-profile/trace-listeners.md)
