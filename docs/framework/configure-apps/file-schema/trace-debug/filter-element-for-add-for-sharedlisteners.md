---
title: <filter> Öğe için <add> için <sharedListeners>
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
ms.openlocfilehash: 2bef729f179b41509d3c0381b26e38e364dbf86b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673725"
---
# <a name="filter-element-for-add-for-sharedlisteners"></a>\<Filtre > öğesi için \<Ekle > için \<sharedListeners >
Bir dinleyicisi için bir filtre ekler `sharedListeners` koleksiyonu.  
  
 \<Yapılandırma >  
\<System.Diagnostics >  
\<sharedListeners > öğesi  
\<Ekle >  
\<Filtre >  
  
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
|**type**|Gerekli öznitelik.<br /><br /> Filtre türünü belirtir. Türünün tam adını kullanabilirsiniz (biçimi <xref:System.Type.FullName%2A?displayProperty=nameWithType> özelliği), veya derleme bilgiler dahil olmak üzere tam olarak nitelenmiş tür adını kullanabilirsiniz (biçimi <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> özelliği). Tam nitelikli tür adı oluşturma hakkında daha fazla bilgi için bkz. [belirtme tam olarak nitelenmiş tür adlarını](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|**initializeData**|İsteğe bağlı öznitelik.<br /><br /> Belirtilen sınıf için oluşturucuya geçirilen dizesi.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`system.diagnostics`|Toplamak, depolamak ve iletileri ve bir izleme anahtarı ayarlandığı düzeyi izleme dinleyicilerini belirtir.|  
|`sharedListeners`|Herhangi bir kaynak veya trace ögesi başvurabilirsiniz dinleyicileri koleksiyonudur.|  
|`add`|Bir ekler **sharedListeners** koleksiyonu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Dinleyici olarak tanımlanırsa, bir `<add>` öğesinin `<sharedListeners>` öğesi, bu dinleyici için filtre tanımlanmalıdır bir `<filter>` alt öğe `<add>` öğesi.  
  
 Bu öğe, makine yapılandırma dosyası (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl kullanılacağını gösterir `<filter>` İzleme dinleyicisi için bir filtre eklemek için öğe `console` içinde `sharedListeners` koleksiyonu.  
  
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
- [İzleme ve Hata Ayıklama Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
