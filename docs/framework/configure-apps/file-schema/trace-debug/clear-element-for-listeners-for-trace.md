---
title: '&lt;Temizle&gt; öğesi için &lt;dinleyicileri&gt; için &lt;izleme&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: c0bb2cabafbaba33f8dde7cbf3399387876e0158
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/26/2019
ms.locfileid: "55083593"
---
# <a name="ltcleargt-element-for-ltlistenersgt-for-lttracegt"></a>&lt;Temizle&gt; öğesi için &lt;dinleyicileri&gt; için &lt;izleme&gt;
Temizler `Listeners` izleme için koleksiyon.  
  
 \<Yapılandırma >  
\<System.Diagnostics >  
\<İzleme >  
\<dinleyicileri >  
\<Temizleme >  
  
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
|`system.diagnostics`|Toplamak, depolamak ve iletileri ve bir izleme anahtarı ayarlandığı düzeyi izleme dinleyicilerini belirtir.|  
|`trace`|Toplamak, depolamak ve izleme iletilerini yönlendirmek dinleyicileri içerir.|  
|`listeners`|Toplamak, depolamak ve iletileri yönlendirmek dinleyicileri içerir. Dinleyicileri bir uygun hedef izleme çıkışa doğrudan.|  
  
## <a name="remarks"></a>Açıklamalar  
 `<clear>` Öğeyi kaldırır gelen tüm dinleyicileri `Listeners` izleme için koleksiyon. Kullanabileceğiniz `<clear>` kullanmadan önce öğesi `<add>` koleksiyondaki herhangi bir etkin dinleyiciler vardır emin olmak için öğesi.  
  
 Temizleyebilir `Listeners` çağırarak programlama yoluyla koleksiyonu <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> metodunda <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> özelliği (`System.Diagnostics.Trace.Listeners.Clear()`).  
  
 Bu öğe, makine yapılandırma dosyası (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.  
  
> [!NOTE]
>  `<clear>` Öğeyi kaldırır <xref:System.Diagnostics.DefaultTraceListener> gelen `Listeners` davranışını değiştirme koleksiyonu <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, ve <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> yöntemleri. Çağırma bir `Assert` veya `Fail` yöntem normal olarak görüntülenen bir ileti kutusu sonuçlanır. Ancak, ileti kutusu varsa görüntülenmez <xref:System.Diagnostics.DefaultTraceListener> kullanımda olmayan `Listeners` koleksiyonu.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl kullanılacağını gösterir `<clear>` kullanmadan önce öğesi `<add>` dinleyici eklemek için öğe `console` için `Listeners` izleme için koleksiyon.  
  
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
- [İzleme ve Hata Ayıklama Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [\<kaldırma >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-trace.md)
- [İzleme Dinleyicileri](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
