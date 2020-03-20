---
title: <commonParameters>
ms.date: 03/30/2017
ms.assetid: ffc20832-34d6-4622-8174-81924fd53514
ms.openlocfilehash: 73d8549f68e8ca77115619431c857c4a2aac3fdf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153028"
---
# <a name="commonparameters"></a>\<yaygın Parametreler>
Birden çok hizmet arasında genel olarak kullanılan parametre koleksiyonunu temsil eder. Bu koleksiyon genellikle dayanıklı hizmetler tarafından paylaşılabilecek veritabanı bağlantı dizesini içerir.  
  
[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<davranışlar>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<davranış>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<iş akışıRuntime>**](workflowruntime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<commonParametreler>**  
  
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
|[\<>ekleyin](add-of-commonparameters.md)|Koleksiyona hizmetler tarafından kullanılan ortak parametrelerin ad değeri çiftini ekler.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<iş akışıRuntime>](workflowruntime.md)|İş akışı tabanlı Windows <xref:System.Workflow.Runtime.WorkflowRuntime> Communication Foundation (WCF) hizmetlerini barındırmak için ayarları belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Öğe, `<commonParameters>` örneğin `ConnectionString` . <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>  
  
> [!NOTE]
> SQL Tracking `ConnectionString` `<commonParameters>` hizmeti, bölümde belirtilmişse değeri sürekli olarak kullanmaz. `StateMachineWorkflowInstance.StateHistory` Özelliğigeri almak gibi bazı işlemleri başarısız olabilir. Bu geçici çözüm için, aşağıdaki örnekte belirtildiği gibi, izleme sağlayıcısı için yapılandırma bölümünde `ConnectionString` özniteliği belirtin.  

```xml  
<add
type="System.Workflow.Runtime.Tracking.SqlTrackingService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
ConnectionString="Data Source=localhost;Initial Catalog=Partner20WFTP;Integrated Security=True;" />
```  
  
 Aşağıdaki örnekte gösterildiği gibi <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService> `EnableRetries` parametreyi kullanarak işlemlerini yeniden denemelerini sağlayabilirsiniz:  
  
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
  
 Parametrenin `EnableRetries` genel düzeyde *(Ortak Parametreler* bölümünde gösterildiği gibi) veya destekleyen `EnableRetries` tek tek hizmetler için *(Hizmetler* bölümünde gösterildiği gibi) ayarlanabildiği ne dikkat edin.  
  
 Aşağıdaki örnek kod, ortak parametrelerin programlı olarak nasıl değiştirilebildiğini gösterir:
  
```csharp  
Configuration config = WebConfigurationManager.OpenWebConfiguration("/Workflow", "Default Web Site", null, "localhost");
var wfruntime = config.GetSection("WorkflowRuntime") as WorkflowRuntimeSection;  
NameValueConfigurationCollection commonParameters = wfruntime.CommonParameters;
commonParameters["ConnectionString"].Value="another connection string";  
config.Save();  
```  
  
 Bir Windows İş Akışı Temeli ana bilgisayarı <xref:System.Workflow.Runtime.WorkflowRuntime> uygulamasının nesnesinin davranışını denetlemek için yapılandırma dosyası kullanma hakkında daha fazla bilgi için [Bkz. İş Akışı Yapılandırma Dosyaları.](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))  
  
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
- [İş Akışı Yapılandırma Dosyaları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))
- [\<>ekleyin](add-of-commonparameters.md)
