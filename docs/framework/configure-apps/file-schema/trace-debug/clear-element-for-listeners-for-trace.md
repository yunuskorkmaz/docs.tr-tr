---
title: <trace> için <listeners> <clear> öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: 049b8e7ed17633c0f34b062915afaf719927dad6
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088924"
---
# <a name="clear-element-for-listeners-for-trace"></a>\<Trace için \<dinleyicileri > için > \<Temizle >
İzleme için `Listeners` koleksiyonunu temizler.  

[ **\<configuration >** ](../configuration-element.md) \
[**System. diagnostics\<** ](system-diagnostics-element.md) &nbsp;&nbsp;\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<izleme >** ](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<dinleyicileri >** ](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<clear >**

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
|`system.diagnostics`|İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.|  
|`trace`|İzleme iletilerini toplayıp depolayan, depolayan ve yönlendiren dinleyicileri içerir.|  
|`listeners`|İletileri toplayacak, depolayan ve yönlendiren dinleyicileri içerir. Dinleyiciler izleme çıkışını uygun bir hedefe yönlendirir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `<clear>` öğesi, izleme için `Listeners` koleksiyonundan tüm dinleyicileri kaldırır. Koleksiyonda başka hiçbir etkin dinleyici bulunmadığından emin olmak için `<add>` öğesini kullanmadan önce `<clear>` öğesini kullanabilirsiniz.  
  
 <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> özelliğinde <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> yöntemini çağırarak `Listeners` koleksiyonunu programlama yoluyla temizleyebilirsiniz (`System.Diagnostics.Trace.Listeners.Clear()`).  
  
 Bu öğe makine yapılandırma dosyasında (Machine. config) ve uygulama yapılandırma dosyasında kullanılabilir.  
  
> [!NOTE]
> `<clear>` öğesi, <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>ve <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> yöntemlerinin davranışını değiştirerek `Listeners` koleksiyonundan <xref:System.Diagnostics.DefaultTraceListener> kaldırır. Bir `Assert` veya `Fail` yöntemini çağırmak normalde bir ileti kutusunun görüntüsüne neden olur. Ancak, <xref:System.Diagnostics.DefaultTraceListener> `Listeners` koleksiyonunda değilse ileti kutusu görüntülenmez.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, izleme için `Listeners` koleksiyonuna dinleyici `console` eklemek için `<add>` öğesini kullanmadan önce `<clear>` öğesinin nasıl kullanılacağını gösterir.  
  
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
- [\<> Kaldır](remove-element-for-listeners-for-trace.md)
- [İzleme Dinleyicileri](../../../debug-trace-profile/trace-listeners.md)
