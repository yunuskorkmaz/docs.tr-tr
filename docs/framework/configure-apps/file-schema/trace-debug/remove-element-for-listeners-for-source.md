---
title: '&lt;kaldırma&gt; öğesi için &lt;dinleyicileri&gt; için &lt;kaynak&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/remove
helpviewer_keywords:
- remove element for <listeners> for <source>
- <remove> element for <listeners> for <source>
ms.assetid: 3ff6b578-273d-407f-b07f-8251f1f9f5d0
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 5cfed154af93d72f69efc24c6475b432d0963580
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2018
ms.locfileid: "47400848"
---
# <a name="ltremovegt-element-for-ltlistenersgt-for-ltsourcegt"></a>&lt;kaldırma&gt; öğesi için &lt;dinleyicileri&gt; için &lt;kaynak&gt;
Bir dinleyicisinden kaldırır `Listeners` koleksiyonu için bir izleme kaynağı.  
  
 \<Yapılandırma >  
\<System.Diagnostics >  
\<Kaynakları >  
\<Kaynak >  
\<dinleyicileri >  
\<kaldırma >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<remove name="listenerName" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`name`|Gerekli öznitelik.<br /><br /> Dinleyiciyi kaldırmak için adını `Listeners` koleksiyonu.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`system.diagnostics`|Toplamak, depolamak ve iletileri ve bir izleme anahtarı ayarlandığı düzeyi izleme dinleyicilerini belirtir.|  
|`sources`|İzleme iletileri başlatmak iz kaynakları içerir.|  
|`source`|İzleme iletileri başlatan bir izleme kaynağı belirtir.|  
|`listeners`|Toplamak, depolamak ve iletileri yönlendirmek dinleyicilerini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `<remove>` Öğeyi kaldırır belirtilen dinleyicisinden `Listeners` koleksiyonu için bir izleme kaynağı.  
  
 Bir öğeyi kaldırmanız `Listeners` koleksiyonu için bir izleme kaynağı çağırarak programlama yoluyla <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> metodunda <xref:System.Diagnostics.TraceSource.Listeners%2A> özelliği <xref:System.Diagnostics.TraceSource> örneği.  
  
 Bu öğe, makine yapılandırma dosyası (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl kullanılacağını gösterir `<remove>` kullanmadan önce öğesi `<add>` dinleyici eklemek için öğe `console` için `Listeners` iz kaynağı için koleksiyon `TraceSourceApp`.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Diagnostics.TraceSource.Listeners%2A>  
 <xref:System.Diagnostics.TraceSource>  
 [İzleme ve Hata Ayıklama Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [\<Temizleme >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-source.md)  
 [İzleme Dinleyicileri](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
