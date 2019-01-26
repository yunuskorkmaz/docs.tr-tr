---
title: '&lt;Assert&gt; öğesi'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/assert
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assert
helpviewer_keywords:
- <assert> element
- assert element
ms.assetid: ef4c3229-b151-4d85-8091-e6456af9b935
ms.openlocfilehash: 450ff1a6e4b5705a33f8869ed8a99ebd674b96e7
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/26/2019
ms.locfileid: "55084490"
---
# <a name="ltassertgt-element"></a>&lt;Assert&gt; öğesi
Bir ileti kutusu çağırdığınızda görüntülenip görüntülenmeyeceğini belirtir <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> yöntemi de ileti yazmak için dosya adını belirtir.  
  
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
|`assertuienabled`|İsteğe bağlı öznitelik.<br /><br /> Görüntülenecek bir ileti kutusunu olup olmadığını belirtir **Debug.Assert** yöntemi değerlendirilen **false**.|  
|`logfilename`|İsteğe bağlı öznitelik.<br /><br /> Eğer ileti yazmak için dosya adını belirtir **Debug.Assert** değerlendiren **false**.|  
  
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
|`system.diagnostics`|Toplamak, depolamak ve iletileri ve bir izleme anahtarı ayarlandığı düzeyi izleme dinleyicilerini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Her iki öznitelikleri  **\<assert >** öğe isteğe bağlıdır. İleti yazmak için bir dosya belirtmeden ileti kutularını devre dışı bırakabilir veya ileti kutuları etkin bırakılması while iletiler yazmak için bir dosya belirtebilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, ileti kutularını görüntüleme çağırdığınızda devre dışı bırakmak gösterilmektedir **Debug.Assert** ve iletileri yazma `c:\log.txt`.  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <assert assertuienabled="false" logfilename="c:\log.txt"/>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Diagnostics.Debug>
- [İzleme ve Hata Ayıklama Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
