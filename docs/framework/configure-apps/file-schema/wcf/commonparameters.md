---
title: <commonParameters>
ms.date: 03/30/2017
ms.assetid: ffc20832-34d6-4622-8174-81924fd53514
ms.openlocfilehash: ab21be7b5e2738ac6a7c9bea676d8180c69d1afd
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73968562"
---
# <a name="commonparameters"></a>\<commonParameters >
Birden çok hizmet arasında genel olarak kullanılan parametrelerin koleksiyonunu temsil eder. Bu koleksiyon, genellikle dayanıklı hizmetler tarafından paylaşılabilen veritabanı bağlantı dizesini içerir.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışları >** ](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Servicedavranışları >** ](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<workflowRuntime >** ](workflowruntime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<commonParameters >**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String"
         value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<> Ekle](add-of-commonparameters.md)|, Hizmet tarafından koleksiyona kullanılan ortak parametrelerin ad-değer çiftini ekler.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<workflowRuntime >](workflowruntime.md)|İş akışı tabanlı Windows Communication Foundation (WCF) Hizmetleri barındırmak için bir <xref:System.Workflow.Runtime.WorkflowRuntime> örneğinin ayarlarını belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `<commonParameters>` öğesi, birden çok hizmet arasında genel olarak kullanılan parametreleri tanımlar, örneğin <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>kullanılırken `ConnectionString`.  
  
> [!NOTE]
> `<commonParameters>` bölümünde belirtilmişse SQL Izleme hizmeti `ConnectionString` değeri sürekli olarak kullanmaz. `StateMachineWorkflowInstance.StateHistory` özelliğini alma gibi bazı işlemler başarısız olabilir. Bu sorunu geçici olarak belirlemek için, aşağıdaki örnekte gösterildiği gibi, İzleme sağlayıcısının yapılandırma bölümünde `ConnectionString` özniteliğini belirtin.  

```xml  
<add
type="System.Workflow.Runtime.Tracking.SqlTrackingService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" 
ConnectionString="Data Source=localhost;Initial Catalog=Partner20WFTP;Integrated Security=True;" />
```  
  
 <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> ve <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>gibi Kalıcılık depolarına iş toplu işleri uygulayan hizmetler için, aşağıdaki örnekte gösterildiği gibi `EnableRetries` parametresini kullanarak işlemlerini yeniden denemesini sağlayabilirsiniz:  
  
```xml  
<workflowRuntime name="SampleApplication"
                 unloadOnIdle="false">
  <commonParameters>
    <add name="ConnectionString"
         value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
    <add name="EnableRetries"
         value="True" />
  </commonParameters>
  <services>
    <add type="System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService, System.Workflow.Runtime,
               Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
         enableRetries="False" />
  </services>
</workflowRuntime>
```  
  
 `EnableRetries` parametresinin küresel bir düzeyde ( *CommonParameters* bölümünde gösterildiği gibi) veya `EnableRetries` destekleyen bireysel hizmetlerden ( *Hizmetler* bölümünde gösterildiği gibi) ayarlandığına dikkat edin.  
  
 Aşağıdaki örnek kod, programlama yoluyla ortak parametrelerin nasıl değiştirileceğini göstermektedir:
  
```csharp  
Configuration config = WebConfigurationManager.OpenWebConfiguration("/Workflow", "Default Web Site", null, "localhost");
var wfruntime = config.GetSection("WorkflowRuntime") as WorkflowRuntimeSection;  
NameValueConfigurationCollection commonParameters = wfruntime.CommonParameters;
commonParameters["ConnectionString"].Value="another connection string";  
config.Save();  
```  
  
 Bir Windows Workflow Foundation ana bilgisayar uygulamasının <xref:System.Workflow.Runtime.WorkflowRuntime> nesnesinin davranışını denetlemek için yapılandırma dosyası kullanma hakkında daha fazla bilgi için bkz. [Iş akışı yapılandırma dosyaları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).  
  
## <a name="example"></a>Örnek  
  
```xml  
<commonParameters>
   <add name="ConnectionString"
        value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
   <add name="EnableRetries"
        value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>
- <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>
- [İş akışı yapılandırma dosyaları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))
- [\<> Ekle](add-of-commonparameters.md)
