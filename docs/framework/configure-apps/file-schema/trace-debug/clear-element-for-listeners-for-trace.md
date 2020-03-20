---
title: <clear><listeners> Için element<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: 905dad8274fede80f4809ff3c7a014049f9df450
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153548"
---
# <a name="clear-element-for-listeners-for-trace"></a>\<izleme> \<için> \<dinleyiciler için açık> Element
İzleme için `Listeners` koleksiyonu temizler.  

[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<izleme>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dinleyici ler>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<açık>**

## <a name="syntax"></a>Sözdizimi  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`system.diagnostics`|İletileri toplayan, depolayan ve yönlendiren izleme dinleyicilerini ve izleme anahtarının ayarlandığı düzeyi belirtir.|  
|`trace`|İletileri toplayan, depolayan ve yönlendiren dinleyicileri içerir.|  
|`listeners`|İletileri toplayan, depolayan ve yönlendiren dinleyicileri içerir. Dinleyiciler izleme çıktısını uygun bir hedefe yönlendirir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Öğe `<clear>` izleme için `Listeners` koleksiyondaki tüm dinleyicileri kaldırır. Koleksiyonda başka `<clear>` etkin dinleyici `<add>` olmadığından emin olmak için öğeyi kullanmadan önce öğeyi kullanabilirsiniz.  
  
 Toplamayı, `Listeners` <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> özellikteki yöntemi arayarak programlı olarak`System.Diagnostics.Trace.Listeners.Clear()`temizleyebilirsiniz ( ).  
  
 Bu öğe makine yapılandırma dosyasında (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.  
  
> [!NOTE]
> `Listeners` Öğe, `<clear>` , <xref:System.Diagnostics.DefaultTraceListener> <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType> <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, ve <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> yöntemleri davranışını değiştirerek, koleksiyondan kaldırır. Bir `Assert` veya `Fail` yöntemin çağrılmak normalde bir ileti kutusunun görüntülenmesine neden olabilir. Ancak, `Listeners` koleksiyonda yoksa ileti <xref:System.Diagnostics.DefaultTraceListener> kutusu görüntülenmez.  
  
## <a name="example"></a>Örnek  
 `<clear>` Aşağıdaki örnek, dinleyiciyi `<add>` `console` izleme için koleksiyona eklemek için öğeyi kullanmadan önce öğenin nasıl kullanılacağını `Listeners` gösterir.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="false" indentsize="4">  
      <listeners>  
        <clear/>  
        <add name="console"
          type="System.Diagnostics.ConsoleTraceListener" >  
          <filter type="System.Diagnostics.EventTypeFilter"
            initializeData="Error" />  
        </add>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Diagnostics.Trace.Listeners%2A>
- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.TraceSource>
- [İzleme ve Hata Ayıklama Ayarları Şeması](index.md)
- [\<>kaldırmak](remove-element-for-listeners-for-trace.md)
- [İz Dinleyicileri](../../../debug-trace-profile/trace-listeners.md)
