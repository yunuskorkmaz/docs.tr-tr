---
title: <filter><add> Için element<sharedListeners>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add/filter
helpviewer_keywords:
- filter element for <add> for <sharedListeners>
- initializeData attribute
- <filter> element for <add> for <sharedListeners>
- filters, trace listeners
- trace listeners, filters
ms.assetid: 7d4e7faa-2e4e-4379-ac76-f6cd7f2f8fac
ms.openlocfilehash: 6fb52cdfa5792ab6059b60d8dbb91c107cd666ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153459"
---
# <a name="filter-element-for-add-for-sharedlisteners"></a>\<paylaşılan Dinleyiciler \<için \<> eklemek için> Öğesi'ni filtreleme>
`sharedListeners` Koleksiyondaki bir dinleyiciye filtre ekler.  

[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<paylaşılanDinleyiciler>**](sharedlisteners-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>ekleyin**](add-element-for-sharedlisteners.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filtre>**

## <a name="syntax"></a>Sözdizimi  
  
```xml  
<filter type="System.Diagnostics.EventTypeFilter"
  initializeData="Warning" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|**Türü**|Gerekli öznitelik.<br /><br /> Filtrenin türünü belirtir. Yalnızca türün tam adını <xref:System.Type.FullName%2A?displayProperty=nameWithType> (özelliğin biçiminde) veya derleme bilgilerini de içeren tam nitelikli tür adını <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> (özelliğin biçiminde) kullanabilirsiniz. Tam nitelikli tür adı oluşturma hakkında bilgi için [bkz.](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)|  
|**initializeData**|İsteğe bağlı öznitelik.<br /><br /> Dize, belirtilen sınıfın oluşturucuya geçti.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`system.diagnostics`|İletileri toplayan, depolayan ve yönlendiren izleme dinleyicilerini ve izleme anahtarının ayarlandığı düzeyi belirtir.|  
|`sharedListeners`|Herhangi bir kaynak veya izleme öğesinin başvuruda bulunabileceği dinleyici koleksiyonu.|  
|`add`|**Paylaşılan Dinleyici** koleksiyonuna bir dinleyici ekler.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir `<add>` dinleyici `<sharedListeners>` öğenin bir öğesi nde tanımlanırsa, bu dinleyici için `<filter>` filtre `<add>` öğenin bir alt öğesi olan bir öğe tanımlanmalıdır.  
  
 Bu öğe makine yapılandırma dosyasında (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `<filter>` `console` koleksiyondaki izleme dinleyicisine bir filtre eklemek için `sharedListeners` öğenin nasıl kullanılacağını gösterir.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="myTraceSource" >  
        <listeners>  
          <add name="console" />  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="console"
        type="System.Diagnostics.ConsoleTraceListener" >  
        <filter type="System.Diagnostics.EventTypeFilter"
          initializeData="Error" />  
      </add>  
    </sharedListeners>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Diagnostics.TraceFilter>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceSource>
- [İzleme ve Hata Ayıklama Ayarları Şeması](index.md)
