---
title: "&lt;Assert&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/assert
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assert
helpviewer_keywords:
- <assert> element
- assert element
ms.assetid: ef4c3229-b151-4d85-8091-e6456af9b935
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 9670cf0faa3e7f69b8f99b09fa26741991a60481
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltassertgt-element"></a>&lt;Assert&gt; öğesi
Bir ileti kutusu çağırdığınızda görüntülenip görüntülenmeyeceğini belirtir <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> yöntemi; ayrıca iletileri yazmak için dosya adını belirtir.  
  
 \<Yapılandırma >  
\<System.Diagnostics >  
\<Assert >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<assert assertuienabled="true|false" logfilename="file name"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`assertuienabled`|İsteğe bağlı öznitelik.<br /><br /> Görüntülenecek bir ileti kutusunu olup olmadığını belirtir **Debug.Assert** yöntemi hesaplar için **false**.|  
|`logfilename`|İsteğe bağlı öznitelik.<br /><br /> İf ileti yazmak için dosya adını belirtir **Debug.Assert** değerlendiren **false**.|  
  
## <a name="assertuienabled-attribute"></a>assertuienabled özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`true`|İleti kutusu görüntüler. Bu varsayılandır.|  
|`false`|İleti kutusu görüntülemez.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`system.diagnostics`|Toplamak, depolamak ve iletileri ve izleme anahtarı ayarlandığı düzeyi rota izleme dinleyicilerini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Her iki öznitelik  **\<assert >** öğesi isteğe bağlıdır. İletileri yazmak için bir dosya belirtmeden ileti kutuları devre dışı bırakabilir veya ileti kutuları etkin bırakarak çalışırken iletiler yazmak için bir dosya belirtebilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek çağırdığınızda görüntüleme ileti kutuları devre dışı bırakma gösterir **Debug.Assert** ve iletileri yazma `c:\log.txt`.  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <assert assertuienabled="false" logfilename="c:\log.txt"/>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Diagnostics.Debug>  
 [İzleme ve Hata Ayıklama Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
