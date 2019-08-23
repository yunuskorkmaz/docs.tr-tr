---
title: <trace> için <listeners> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners
helpviewer_keywords:
- <listeners> element
- listeners element
ms.assetid: 1394c2c3-6304-46db-87c1-8e8b16f5ad5b
ms.openlocfilehash: e4550d4c4cd9ff37c5937ad366cccf91387c0e3f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927015"
---
# <a name="listeners-element-for-trace"></a>\<Trace > için \<dinleyiciler > öğesi
İletileri toplayan, depolayan ve yönlendiren bir dinleyici belirtir. Dinleyiciler izleme çıkışını uygun bir hedefe yönlendirir.  
  
 \<Yapılandırma > öğesi  
\<System. Diagnostics > öğesi  
\<Trace > öğesi  
\<Trace > için \<dinleyiciler > öğesi  
  
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
|[\<> Ekle](add-element-for-listeners-for-trace.md)|`Listeners` Koleksiyona bir dinleyici ekler.|  
|[\<> Temizle](clear-element-for-listeners-for-trace.md)|İzleme için `Listeners` koleksiyonu temizler.|  
|[\<> Kaldır](remove-element-for-listeners-for-trace.md)|`Listeners` Koleksiyondan bir dinleyiciyi kaldırır.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`system.diagnostics`|ASP.NET yapılandırma bölümünün kök öğesini belirtir.|  
|`trace`|İzleme iletilerini toplayıp depolayan, depolayan ve yönlendiren dinleyicileri içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ve sınıfları aynı dinleyicileri toplamayı paylaşır. <xref:System.Diagnostics.Debug> <xref:System.Diagnostics.Trace> Bu sınıflardan birindeki koleksiyona bir dinleyici nesnesi eklerseniz, diğer sınıf aynı dinleyiciyi kullanır. .NET Framework ile birlikte gelen dinleyici sınıfları <xref:System.Diagnostics.TraceListener> sınıfından türetilir.  
  
## <a name="configuration-file"></a>Yapılandırma Dosyası  
 Bu öğe makine yapılandırma dosyasında (Machine. config) ve uygulama yapılandırma dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, dinleyicileri `MyListener` ve `MyEventListener` **dinleyici** koleksiyonuna eklemek için  **\<dinleyiciler >** öğesinin nasıl kullanılacağını gösterir. `MyListener`adlı `MyListener.log` bir dosya oluşturur ve çıktıyı dosyaya yazar. `MyEventListener`olay günlüğünde bir giriş oluşturur.  
  
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
- [İzleme ve Hata Ayıklama Ayarları Şeması](index.md)
