---
title: <remove>İçin için <listeners> öğesi<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/remove
helpviewer_keywords:
- remove element for <listeners> for <source>
- <remove> element for <listeners> for <source>
ms.assetid: 3ff6b578-273d-407f-b07f-8251f1f9f5d0
ms.openlocfilehash: edd27dd262004aead7db4d81db8ecab0e831dac1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926987"
---
# <a name="remove-element-for-listeners-for-source"></a>\<Kaynak > için \<> \<dinleyicileri > öğesini kaldır
İzleme kaynağı için `Listeners` koleksiyondan bir dinleyiciyi kaldırır.  
  
 \<Yapılandırma >  
\<System. Diagnostics >  
\<Kaynaklar >  
\<Kaynak >  
\<dinleyiciler >  
\<> Kaldır  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<remove name="listenerName" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`name`|Gerekli öznitelik.<br /><br /> `Listeners` Koleksiyondan kaldırılacak dinleyicinin adı.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`system.diagnostics`|İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.|  
|`sources`|İzleme iletilerini Başlatan izleme kaynaklarını içerir.|  
|`source`|İzleme iletilerini Başlatan bir izleme kaynağını belirtir.|  
|`listeners`|İletileri toplayacak, depolayan ve yönlendiren dinleyicileri belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Öğesi `<remove>` , bir izleme kaynağı için belirtilen dinleyiciyi `Listeners` koleksiyondan kaldırır.  
  
 Örnek<xref:System.Diagnostics.TraceSource> `Listeners` özelliği<xref:System.Diagnostics.TraceSource.Listeners%2A> üzerinde <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> yöntemini çağırarak bir izleme kaynağı için koleksiyondan bir öğeyi programlı bir şekilde kaldırabilirsiniz.  
  
 Bu öğe makine yapılandırma dosyasında (Machine. config) ve uygulama yapılandırma dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, öğesini izleme kaynağı `<remove>` `console` `Listeners` `<add>` koleksiyonuna`TraceSourceApp`eklemek için öğesini kullanmadan önce öğesinin nasıl kullanılacağını gösterir.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="TraceSourceApp" switchName="sourceSwitch"   
         switchType="System.Diagnostics.SourceSwitch" >  
         <listeners>  
           <remove name="Default"/>  
           <add name="console"   
             type="System.Diagnostics.ConsoleTraceListener" />  
         </listeners>  
      </source>  
    </sources>  
  </system.diagnostics>  
</configuration>   
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Diagnostics.TraceSource.Listeners%2A>
- <xref:System.Diagnostics.TraceSource>
- [İzleme ve Hata Ayıklama Ayarları Şeması](index.md)
- [\<> Temizle](clear-element-for-listeners-for-source.md)
- [İzleme Dinleyicileri](../../../debug-trace-profile/trace-listeners.md)
