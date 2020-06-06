---
title: <workflowRuntime>
ms.date: 03/30/2017
ms.assetid: 304c70fa-78d1-4d0f-b89f-0ca23d734c6f
ms.openlocfilehash: d12656b77fa219080382603fd04a542d2fa9064a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399082"
---
# \<workflowRuntime>
<xref:System.Workflow.Runtime.WorkflowRuntime>İş akışı tabanlı Windows Communication Foundation (WCF) hizmetlerini barındırmak için bir örneğinin ayarlarını belirtir.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowRuntime>**  
  
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
|CachedInstanceExpiration|<xref:System.TimeSpan>Bir iş akışı örneğinin, zorla kaldırılmadan veya durdurulmadan önce boşta durumunda kalabileceği en uzun süreyi belirten isteğe bağlı bir değer. WorkflowRuntime, `PersistenceService` UnloadOnIdle işlemini gerçekleştirirse, bu öznitelik yoksayılır.|  
|enablePerformanceCounters|Performans sayaçlarının etkin olup olmadığını belirten isteğe bağlı bir Boolean değeri. Performans sayaçları, iş akışı ile ilgili çeşitli istatistikler hakkında bilgi sağlar, ancak iş akışı çalışma zamanı altyapısı başladığında ve iş akışı örnekleri çalışırken performans cezasına neden olur. Varsayılan değer: `true`.|  
|name|İş akışı çalışma zamanı altyapısının adını içeren bir dize. Bu ad, bu çalışma zamanını sistemde çalışmakta olabilecek diğer çalışma zamanları (örneğin, performans sayaçları) ayırt etmek için çıktıda kullanılır.<br /><br /> Varsayılan değer boş bir dizedir.|  
|validateOnCreate|WorkflowServiceHost açıldığında iş akışı tanımı doğrulamasının gerçekleşmeyeceğini belirten isteğe bağlı bir Boolean değeri.  Bu öznitelik olarak ayarlandığında `true` , iş akışı doğrulama her `WorkflowServiceHost.Open` çağrıldığında yürütülür. Doğrulama hataları bulunursa bir <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> hata oluşur.<br /><br /> Bu özellik olarak ayarlandığında `false` , Iş akışı tanımı doğrulaması gerçekleşmeyecektir.<br /><br /> Bu özellik için varsayılan değer `true` .|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|commonParameters|Hizmetler tarafından kullanılan ortak parametrelerin bir koleksiyonu. Bu koleksiyon, genellikle dayanıklı hizmetler tarafından paylaşılabilen veritabanı bağlantı dizesini içerir.|  
|services|Altyapıya eklenecek hizmetlerden oluşan bir koleksiyon <xref:System.Workflow.Runtime.WorkflowRuntime> . Öğeler türündedir <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> .  Koleksiyonda belirtilen hizmetler, iş akışı çalışma zamanı altyapısı tarafından başlatılır ve uygun Oluşturucu çağrıldığında bu hizmetin hizmetlerine eklenir <xref:System.Workflow.Runtime.WorkflowRuntime> . Bu nedenle, koleksiyonda belirtilen hizmetler oluşturucuların imzaları hakkındaki belirli kurallara uymalıdır. Daha fazla bilgi edinmek için bkz. <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|Bir davranış öğesi belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir Windows Workflow Foundation ana bilgisayar uygulamasının bir nesnesinin davranışını denetlemek için yapılandırma dosyası kullanma hakkında daha fazla bilgi için <xref:System.Workflow.Runtime.WorkflowRuntime> bkz. [Iş akışı yapılandırma dosyaları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).  
  
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
