---
title: "&lt;İş akışı workflowRuntime&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 304c70fa-78d1-4d0f-b89f-0ca23d734c6f
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: db891e9d967f4471e2b0a3778db433adb62e121c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltworkflowruntimegt"></a>&lt;İş akışı workflowRuntime&gt;
Öğesinin bir örneği için ayarları belirtir <xref:System.Workflow.Runtime.WorkflowRuntime> iş akışı tabanlı barındırmak için [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Hizmetleri.  
  
 \<Sistem. ServiceModel >  
\<davranışları >  
\<serviceBehaviors >  
\<davranışı >  
\<İş akışı workflowRuntime >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<workflowRuntime cachedInstanceExpiration="TimeSpan"  
                                  enablePerformanceCounters="Boolean"  
                                  name="String"  
                                  validateOnCreate="Boolean">  
                 <commonParameters>  
                    <add name="String" value="String" />  
                 </commonParameters>  
                 <services>  
                    <add type="String"/>  
                 </services>  
</workflowRuntime>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|cachedInstanceExpiration|İsteğe bağlı bir <xref:System.TimeSpan> bir iş akışı örneği bellek içi kalarak en uzun süreyi belirten değer zorla yüklenmemiş veya iptal önce boşta durumda. Workflowruntime varsa `PersistenceService` unloadOnIdle gerçekleştirir, bu öznitelik dikkate alınmaz.|  
|enablePerformanceCounters|Performans sayaçları etkinleştirilip etkinleştirilmediğini belirten isteğe bağlı bir Boole değeri. Performans sayaçları bilgisi çeşitli iş akışı ile ilgili istatistikler sağlar. ancak iş akışı çalışma zamanı altyapısı başladığında ve iş akışı örnekleri çalışırken performans cezası neden olurlar. Varsayılan değer `true` şeklindedir.|  
|name|İş akışı çalışma zamanı altyapısı adını içeren dize. Çıktıda sistemde, örneğin, performans sayaçları çalışan diğer çalışma zamanları ile bu çalışma zamanı birbirinden ayırmak için kullanılan adı.<br /><br /> Varsayılan boş bir dizedir.|  
|validateOnCreate|WorkflowServiceHost açık olduğunda doğrulama iş akışı tanımının oluşup oluşmadığına belirten isteğe bağlı bir Boole değeri.  Bu öznitelik ayarlandığında `true`, iş akışı doğrulama her zaman yürütülür `WorkflowServiceHost.Open` olarak adlandırılır. Doğrulama hataları bulunursa, bir <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> hata oluşur.<br /><br /> Bu özellik ayarlandığında `false`, bir iş akışı tanımı doğrulama gerçekleşecek.<br /><br /> Bu özellik için varsayılan değer `true`.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|commonParameters|Hizmetler tarafından kullanılan ortak parametreleri topluluğu. Bu koleksiyon genellikle sürekli hizmetler tarafından paylaşılan veritabanı bağlantı dizesi içerir.|  
|hizmetler|Eklenecek hizmetler koleksiyonu <xref:System.Workflow.Runtime.WorkflowRuntime> altyapısı. Tür öğeleridir <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.  Koleksiyonda belirtilen hizmetler iş akışı çalışma zamanı altyapısı tarafından başlatılan ve hizmetlerinin için eklenen zaman uygun <xref:System.Workflow.Runtime.WorkflowRuntime> Oluşturucusu çağrılır. Bu nedenle, koleksiyonda belirtilen hizmetlerden kendi oluşturucular imzalarını hakkında belirli kurallara uymalıdır. Daha fazla bilgi edinmek için bkz. <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<davranışı >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Bir davranış öğesi belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Davranışını denetlemek için bir yapılandırma dosyası kullanma hakkında daha fazla bilgi için bir <xref:System.Workflow.Runtime.WorkflowRuntime> nesnesi bir Windows Workflow Foundation ana bilgisayar uygulamasının bkz [iş akışı yapılandırma dosyalarını](http://msdn.microsoft.com/en-us/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909).  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>  
 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>  
 <xref:System.Workflow.Runtime.WorkflowRuntime>  
 [İş akışı yapılandırma dosyaları](http://msdn.microsoft.com/en-us/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909)
