---
title: <filter> için <add> için <listeners> için <source> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#filter
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- <filter> element for <add> for <listeners> for <source>
- filter element for <add> for <listeners> for <source>
ms.assetid: 15808b80-4579-4c25-b385-178cfdf154ba
ms.openlocfilehash: 7207e72c537e8338f8c646750016c9b6c810bf9a
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55260586"
---
# <a name="filter-element-for-add-for-listeners-for-source"></a>\<Filtre > öğesi için \<Ekle > için \<dinleyicileri > için \<kaynak >
Bir dinleyicisi için bir filtre ekler `Listeners` koleksiyonu için bir izleme kaynağı.  
  
 \<Yapılandırma >  
\<System.Diagnostics >  
\<Kaynakları >  
\<Kaynak >  
\<dinleyicileri >  
\<Ekle >  
\<Filtre >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<filter   
  type="traceFilterClassName"   
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`type`|Gerekli öznitelik.<br /><br /> Devralınan filtre türünü belirtir <xref:System.Diagnostics.TraceFilter> sınıfı. Türün karşılık gelen türü ad alanıyla nitelenen adı kullanabileceğiniz <xref:System.Type.FullName%2A> özelliği veya karşılık gelen derleme bilgiler dahil olmak üzere tam olarak nitelenmiş tür adını kullanabilir <xref:System.Type.AssemblyQualifiedName%2A> özelliği. Tam olarak nitelenmiş tür adları hakkında daha fazla bilgi için bkz: [belirtme tam olarak nitelenmiş tür adlarını](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|`initializeData`|İsteğe bağlı öznitelik.<br /><br /> Dize için belirtilen filtreyi sınıf oluşturucusuna geçirilen.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`system.diagnostics`|Toplamak, depolamak ve iletileri ve bir izleme anahtarı ayarlandığı düzeyi izleme dinleyicilerini belirtir.|  
|`sources`|İzleme iletileri başlatmak iz kaynakları içerir.|  
|`source`|İzleme iletileri başlatan bir izleme kaynağı belirtir.|  
|`listeners`|Toplamak, depolamak ve iletileri yönlendirmek dinleyicileri içerir. Dinleyicileri bir uygun hedef izleme çıkışa doğrudan.|  
|`add`|Bir ekler `Listeners` koleksiyonu için bir izleme kaynağı.|  
  
## <a name="remarks"></a>Açıklamalar  
 `<filter>` Öğe bulunmalıdır bir `<add>` öğesi dinleyicisi türünü belirten bir izleme kaynağı dinleyicisi için yalnızca bir dinleyicisi adı tanımlanmış bir [ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md). Dinleyici olarak tanımlanırsa, bir [ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md), filtre bu dinleyici için bu öğesinde tanımlanmış olması gerekir.  
  
 Bu öğe, makine yapılandırma dosyası (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl kullanılacağını gösterir `<filter>` dinleyici için filtre eklemek için öğe `console` içinde `Listeners` iz kaynağı için koleksiyon `myTraceSource`, filtre olay düzeyi'olarak belirterek `Error`.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="myTraceSource" switchName="SourceSwitch"   
        switchType="System.Diagnostics.SourceSwitch"  >  
        <listeners>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener" >  
            <filter type="System.Diagnostics.EventTypeFilter"   
              initializeData="Error" />  
          </add>  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="SourceSwitch" value="Warning" />  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [İzleme ve Hata Ayıklama Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
