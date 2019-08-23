---
title: <workflowRuntime>
ms.date: 03/30/2017
ms.assetid: 304c70fa-78d1-4d0f-b89f-0ca23d734c6f
ms.openlocfilehash: 0cd04f66cc4b73eb5f1c43bd6c8dc9189dfceff1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915210"
---
# <a name="workflowruntime"></a>\<workflowRuntime >
İş akışı tabanlı Windows Communication Foundation (WCF <xref:System.Workflow.Runtime.WorkflowRuntime> ) hizmetlerini barındırmak için bir örneğinin ayarlarını belirtir.  
  
 \<system.ServiceModel>  
\<davranışlar >  
\<serviceBehaviors>  
\<davranış >  
\<workflowRuntime >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<workflowRuntime cachedInstanceExpiration="TimeSpan"
                 enablePerformanceCounters="Boolean"
                 name="String"
                 validateOnCreate="Boolean">
  <commonParameters>
    <add name="String"
         value="String" />
  </commonParameters>
  <services>
    <add type="String" />
  </services>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|CachedInstanceExpiration|Bir iş <xref:System.TimeSpan> akışı örneğinin, zorla kaldırılmadan veya durdurulmadan önce boşta durumunda kalabileceği en uzun süreyi belirten isteğe bağlı bir değer. WorkflowRuntime `PersistenceService` , UnloadOnIdle işlemini gerçekleştirirse, bu öznitelik yoksayılır.|  
|enablePerformanceCounters|Performans sayaçlarının etkin olup olmadığını belirten isteğe bağlı bir Boolean değeri. Performans sayaçları, iş akışı ile ilgili çeşitli istatistikler hakkında bilgi sağlar, ancak iş akışı çalışma zamanı altyapısı başladığında ve iş akışı örnekleri çalışırken performans cezasına neden olur. Varsayılan değer `true` şeklindedir.|  
|name|İş akışı çalışma zamanı altyapısının adını içeren bir dize. Bu ad, bu çalışma zamanını sistemde çalışmakta olabilecek diğer çalışma zamanları (örneğin, performans sayaçları) ayırt etmek için çıktıda kullanılır.<br /><br /> Varsayılan değer boş bir dizedir.|  
|validateOnCreate|WorkflowServiceHost açıldığında iş akışı tanımı doğrulamasının gerçekleşmeyeceğini belirten isteğe bağlı bir Boolean değeri.  Bu öznitelik olarak `true`ayarlandığında, iş akışı doğrulama `WorkflowServiceHost.Open` her çağrıldığında yürütülür. Doğrulama hataları bulunursa bir <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> hata oluşur.<br /><br /> Bu özellik olarak `false`ayarlandığında, iş akışı tanımı doğrulaması gerçekleşmeyecektir.<br /><br /> Bu özellik `true`için varsayılan değer.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|commonParameters|Hizmetler tarafından kullanılan ortak parametrelerin bir koleksiyonu. Bu koleksiyon, genellikle dayanıklı hizmetler tarafından paylaşılabilen veritabanı bağlantı dizesini içerir.|  
|hizmetler|<xref:System.Workflow.Runtime.WorkflowRuntime> Altyapıya eklenecek hizmetlerden oluşan bir koleksiyon. Öğeler türündedir <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.  Koleksiyonda belirtilen hizmetler, iş akışı çalışma zamanı altyapısı tarafından başlatılır ve uygun <xref:System.Workflow.Runtime.WorkflowRuntime> Oluşturucu çağrıldığında bu hizmetin hizmetlerine eklenir. Bu nedenle, koleksiyonda belirtilen hizmetler oluşturucuların imzaları hakkındaki belirli kurallara uymalıdır. Daha fazla bilgi edinmek için bkz. <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<davranış >](behavior-of-endpointbehaviors.md)|Bir davranış öğesi belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir Windows Workflow Foundation ana bilgisayar uygulamasının bir <xref:System.Workflow.Runtime.WorkflowRuntime> nesnesinin davranışını denetlemek için yapılandırma dosyası kullanma hakkında daha fazla bilgi için bkz. [iş akışı yapılandırma dosyaları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).  
  
## <a name="example"></a>Örnek  
  
```xml  
<serviceBehaviors>
   <behavior name="ServiceBehavior">
      <workflowRuntime name="WorkflowServiceHostRuntime"
                       validateOnCreate="true"
                       enablePerformanceCounters="true">
         <commonParameters>
            <add name="ConnectionString" value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
            <add name="EnableRetries" value="True" />
         </commonParameters>
         <services>
             <add type="NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common.TestPersistenceService.FilePersistenceService, NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common"/>
         </services>
      </workflowRuntime>
   </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- [İş akışı yapılandırma dosyaları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))
