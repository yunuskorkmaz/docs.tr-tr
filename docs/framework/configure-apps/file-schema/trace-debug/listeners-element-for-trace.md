---
title: "&lt;dinleyicileri&gt; öğesi için &lt;izleme&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners
helpviewer_keywords:
- <listeners> element
- listeners element
ms.assetid: 1394c2c3-6304-46db-87c1-8e8b16f5ad5b
caps.latest.revision: "17"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: b9c1f52f880a38791a9a8d5b5372b2ad53c5569f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltlistenersgt-element-for-lttracegt"></a>&lt;dinleyicileri&gt; öğesi için &lt;izleme&gt;
Toplar, depolar, bir dinleyici belirtir ve iletileri yönlendirir. Dinleyicileri uygun hedef İzleme çıkışı yönlendirir.  
  
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
|[\<ekleme >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-trace.md)|Bir dinleyici ekler `Listeners` koleksiyonu.|  
|[\<Clear >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-trace.md)|Temizler `Listeners` izleme için koleksiyonu.|  
|[\<kaldırma >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-trace.md)|Gelen bir dinleyici kaldırır `Listeners` koleksiyonu.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`system.diagnostics`|ASP.NET yapılandırma bölümü için kök öğesi belirtir.|  
|`trace`|Toplamak, depolamak ve izleme iletilerini yönlendirmek dinleyicileri içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 <xref:System.Diagnostics.Debug> Ve <xref:System.Diagnostics.Trace> sınıfları paylaşmak aynı **dinleyicileri** koleksiyonu. Bu sınıfların birinde koleksiyonuna bir dinleyici nesnesi eklerseniz, başka bir sınıf aynı dinleyicisi kullanır. .NET Framework ile birlikte gelen dinleyicisi sınıfları türetin <xref:System.Diagnostics.TraceListener> sınıfı.  
  
## <a name="configuration-file"></a>Yapılandırma Dosyası  
 Bu öğe makine yapılandırma dosyası (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte nasıl kullanılacağını gösterir  **\<dinleyicileri >** dinleyicileri eklemek için öğesi `MyListener` ve `MyEventListener` için **dinleyicileri** koleksiyonu. `MyListener`adlı bir dosya oluşturur `MyListener.log` ve çıkış dosyasına yazar. `MyEventListener`olay günlüğünde bir giriş oluşturur.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Diagnostics.TraceListener>  
 [İzleme ve Hata Ayıklama Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
