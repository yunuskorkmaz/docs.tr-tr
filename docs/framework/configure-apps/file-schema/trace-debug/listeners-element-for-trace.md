---
title: <trace> için <listeners> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners
helpviewer_keywords:
- <listeners> element
- listeners element
ms.assetid: 1394c2c3-6304-46db-87c1-8e8b16f5ad5b
ms.openlocfilehash: f9f12d9e61e2472b897169727bbb4fbf9833efd6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701352"
---
# <a name="listeners-element-for-trace"></a>\<dinleyicileri > öğesi için \<İzleme >
Toplar, depolar, bir dinleyici belirtir ve iletileri yönlendirir. Dinleyicileri bir uygun hedef izleme çıkışa doğrudan.  
  
 \<Yapılandırma > öğesi  
\<System.Diagnostics > öğesi  
\<İzleme > öğesi  
\<dinleyicileri > öğesi için \<İzleme >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<listeners>   
  <add>...</add>  
  <clear/>  
  <remove ... />  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Ekle >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-trace.md)|Bir ekler `Listeners` koleksiyonu.|  
|[\<Temizleme >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-trace.md)|Temizler `Listeners` izleme için koleksiyon.|  
|[\<kaldırma >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-trace.md)|Bir dinleyicisinden kaldırır `Listeners` koleksiyonu.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`system.diagnostics`|ASP.NET yapılandırma bölümü için olan kök öğesini belirtir.|  
|`trace`|Toplamak, depolamak ve izleme iletilerini yönlendirmek dinleyicileri içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 <xref:System.Diagnostics.Debug> Ve <xref:System.Diagnostics.Trace> sınıfları paylaşma aynı **dinleyicileri** koleksiyonu. Bu sınıflardan birine koleksiyonuna bir dinleyici nesne eklerseniz, başka bir sınıfın aynı dinleyicisi kullanır. .NET Framework ile birlikte gelen dinleyici sınıfların türetilmesi <xref:System.Diagnostics.TraceListener> sınıfı.  
  
## <a name="configuration-file"></a>Yapılandırma Dosyası  
 Bu öğe, makine yapılandırma dosyası (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl kullanılacağını gösterir  **\<dinleyicileri >** dinleyiciler eklemek için öğe `MyListener` ve `MyEventListener` için **dinleyicileri** koleksiyonu. `MyListener` adlı bir dosya oluşturur `MyListener.log` ve çıkış dosyasına yazar. `MyEventListener` olay günlüğünde bir giriş oluşturur.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="true" indentsize="0">  
      <listeners>  
        <add name="myListener"   
          type="System.Diagnostics.TextWriterTraceListener,   
            system, version=1.0.3300.0, Culture=neutral,   
            PublicKeyToken=b77a5c561934e089"   
          initializeData="c:\myListener.log" />  
        <add name="MyEventListener"  
          type="System.Diagnostics.EventLogTraceListener,   
            system, version=1.0.3300.0, Culture=neutral,   
            PublicKeyToken=b77a5c561934e089"  
          initializeData="MyConfigEventLog"/>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Diagnostics.TraceListener>
- [İzleme ve Hata Ayıklama Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
