---
title: '&lt;commonParameters&gt; &lt;ekleme&gt;'
ms.date: 03/30/2017
ms.assetid: 3713bf25-20c8-455f-bb85-de46b6487932
ms.openlocfilehash: 7973a1d759eaec06a6bd69822bbbf53ff77721ba
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746871"
---
# <a name="ltaddgt-of-ltcommonparametersgt"></a>&lt;commonParameters&gt; &lt;ekleme&gt;
Bir ad-değer çifti birden fazla hizmet genel olarak kullanılan parametreleri belirtir. Bu parametre genellikle sürekli hizmetler tarafından paylaşılan veritabanı bağlantı dizesi içerir.  
  
 \<system.ServiceModel>  
\<davranışları >  
\<serviceBehaviors>  
\<davranışı >  
\<İş akışı workflowRuntime >  
\<commonParameters >  
\<ekleme >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<workflowRuntime>  
   <commonParameters>  
      <add name="String" value="String" />  
   </commonParameters>  
</workflowRuntime>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|name|Bir hizmet için belirtilen parametre adı.|  
|value|Bir hizmet için belirtilen parametre değeri.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<commonParameters >](http://msdn.microsoft.com/library/d0e1e6fc-985a-4713-b7da-194e30dfab4c)|Hizmetler tarafından kullanılan ortak parametreleri topluluğu. Bu koleksiyon genellikle sürekli hizmetler tarafından paylaşılan veritabanı bağlantı dizesi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `<commonParameters>` Öğesi genel olarak birden fazla hizmet, örneğin kullanılan parametreleri tanımlar `ConnectionString` kullanırken <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.  
  
 İş yürütme Hizmetleri için Kalıcılık depolarına gibi toplu iş <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> ve <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, kendi işlem kullanarak yeniden etkinleştirebilirsiniz `EnableRetries` aşağıdaki örnekte gösterildiği gibi parametre:  
  
```xml  
<WorkflowRuntime Name="SampleApplication" UnloadOnIdle="false">  
    <commonParameters>  
        <add name="ConnectionString" value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />  
        <add name="EnableRetries" value="True" />  
    </commonParameters>  
    <Services>  
        <add type="System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" EnableRetries="False" />   
     </Services>  
</WorkflowRuntime>  
```  
  
 Dikkat `EnableRetries` parametresi ayarlanabilir da genel düzeyde (gösterildiği gibi *CommonParameters* bölüm) veya bireysel destekleyen Hizmetler `EnableRetries` (gösterildiği gibi *Hizmetleri*bölümü).  
  
 Davranışını denetlemek için bir yapılandırma dosyası kullanma hakkında daha fazla bilgi için bir <xref:System.Workflow.Runtime.WorkflowRuntime> nesnesi bir Windows Workflow Foundation ana bilgisayar uygulamasının bkz [iş akışı yapılandırma dosyalarını](http://msdn.microsoft.com/library/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909).  
  
## <a name="example"></a>Örnek  
  
```xml  
<commonParameters>  
   <add name="ConnectionString" value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;"/>  
   <add name="EnableRetries" value="true"/>  
</commonParameters>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>  
 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>  
 <xref:System.Workflow.Runtime.WorkflowRuntime>  
 <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>  
 <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>  
 [İş akışı yapılandırma dosyaları](http://msdn.microsoft.com/library/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909)  
 [\<commonParameters >](http://msdn.microsoft.com/library/d0e1e6fc-985a-4713-b7da-194e30dfab4c)
