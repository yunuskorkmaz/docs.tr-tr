---
title: "&lt;kaldırma&gt; öğesi için &lt;dinleyicileri&gt; için &lt;izleme&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/remove
helpviewer_keywords:
- remove element
- <remove> element
ms.assetid: 9a5cd1b5-be1a-485f-8f0c-2890ad3ef3e0
caps.latest.revision: "12"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ff1eb93a6d81f83b60e2621296e0c9d995699898
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltremovegt-element-for-ltlistenersgt-for-lttracegt"></a>&lt;kaldırma&gt; öğesi için &lt;dinleyicileri&gt; için &lt;izleme&gt;
Gelen bir dinleyici kaldırır **dinleyicileri** koleksiyonu.  
  
 \<Yapılandırma >  
\<System.Diagnostics >  
\<İzleme >  
\<dinleyicileri >  
\<kaldırma >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<remove name="listener name" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|**adı**|Gerekli öznitelik.<br /><br /> Kaldırmak için dinleyicisinin adını **dinleyicileri** koleksiyonu.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`listeners`|Toplar, depolar, bir dinleyici belirtir ve iletileri yönlendirir. Dinleyicileri uygun hedef İzleme çıkışı yönlendirir.|  
|`system.diagnostics`|Toplamak, depolamak ve iletileri ve izleme anahtarı ayarlandığı düzeyi rota izleme dinleyicilerini belirtir.|  
|`trace`|ASP.NET izleme hizmetini yapılandırır.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Kaldırma <xref:System.Diagnostics.DefaultTraceListener> gelen `Listeners` koleksiyonu davranışını değiştiren <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, ve <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> yöntemleri. Çağıran bir `Assert` veya `Fail` yöntemi ileti kutusu görüntülenmez ancak bir ileti kutusu görüntüleme normalde sonuçları <xref:System.Diagnostics.DefaultTraceListener> bulunmayan `Listeners` koleksiyonu.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, varsayılan İzleme dinleyicisi izlemesinden kaldırmak gösterilmiştir **dinleyicileri** koleksiyonu.  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace autoflush="true" indentsize="0">  
         <listeners>  
            <remove name="Default" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.DefaultTraceListener>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 [İzleme ve hata ayıklama Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
