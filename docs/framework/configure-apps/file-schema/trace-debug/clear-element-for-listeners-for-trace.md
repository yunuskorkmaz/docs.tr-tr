---
title: <clear>İçin için <listeners> öğesi<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: 9816ba0f8e4ddd4c38537eb4e014a4240ff20407
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927179"
---
# <a name="clear-element-for-listeners-for-trace"></a>\<izleme için \< \<dinleyiciler > > öğeyi Temizle >
İzleme için `Listeners` koleksiyonu temizler.  
  
 \<Yapılandırma >  
\<System. Diagnostics >  
\<İzleme >  
\<dinleyiciler >  
\<> Temizle  
  
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
 Öğesi `<clear>` , izleme için `Listeners` koleksiyondaki tüm dinleyicileri kaldırır. Koleksiyonda başka hiçbir etkin `<clear>` dinleyici bulunmadığından emin olmak `<add>` için öğesini kullanmadan önce öğesini kullanabilirsiniz.  
  
 `Listeners` <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> Özelliği(`System.Diagnostics.Trace.Listeners.Clear()`) üzerinde yöntemini çağırarak koleksiyonu programlı bir şekilde temizleyebilirsiniz. <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType>  
  
 Bu öğe makine yapılandırma dosyasında (Machine. config) ve uygulama yapılandırma dosyasında kullanılabilir.  
  
> [!NOTE]
> <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> <xref:System.Diagnostics.DefaultTraceListener> `Listeners` Öğesi,<xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>,, ve yöntemlerinindavranışını<xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>değiştirerek koleksiyonundan kaldırır. <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> `<clear>` Bir `Assert` veya`Fail` yöntemini çağırmak normalde bir ileti kutusunun görüntüsüne neden olur. Ancak, <xref:System.Diagnostics.DefaultTraceListener> `Listeners` koleksiyonda değilse ileti kutusu görüntülenmez.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, öğesini `<clear>` izleme için `Listeners` koleksiyona eklemek `console` üzere `<add>` öğesini kullanmadan önce öğesinin nasıl kullanılacağını gösterir.  
  
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
