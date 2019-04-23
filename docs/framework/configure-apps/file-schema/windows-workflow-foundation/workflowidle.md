---
title: <workflowIdle>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
ms.openlocfilehash: 1dc186f5899935dab43c0d33894e659c4b19748c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59201123"
---
# <a name="workflowidle"></a>\<workflowIdle >
Boş iş akışı örnekleri zaman kaldırıldı ve kalıcı denetleyen bir hizmet davranışı.  
  
\<system.ServiceModel>  
\<davranışlar >  
\<serviceBehaviors>  
\<davranışı >  
\<workflowIdle >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowIdle timeToPersist="TimeSpan" 
                    timeToUnload="TimeSpan" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|timeToPersist|İş akışı boş olur ve kalıcı saat arasındaki süre belirten bir Timespan değeri. TimeSpan.MaxValue varsayılan değerdir.<br /><br /> İş akışı örneği boşta kaldığında geçmesini süresi başlar. Bu öznitelik, en çok bellekte hala örnek koruyarak bir iş akışı örneği daha agresif bir biçimde sürdürülmesi istiyorsanız kullanışlıdır. Bu öznitelik, yalnızca öğenin değeri ise geçerlidir'den az **timeToUnload** özniteliği. Büyükse, göz ardı edilir. Bu öznitelik ile belirtilen değer önce aşılırsa **timeToUnload** özniteliği Kalıcılık iş akışı kaldırıldı önce tamamlamalısınız. Bu iş akışı kalıcı kadar kaldırma işlemi gecikebilir anlamına gelir. Kalıcılık katman geçici hatalar için herhangi bir yeniden deneme işlenmesinden sorumludur ve yalnızca kurtarılabilir olmayan hataları üzerinde özel durum oluşturur. Bu nedenle, Kalıcılık sırasında oluşturulan özel durumlar olarak kabul edilir ve iş akışı örneği durduruldu.|  
|timeToUnload|Saat arasındaki süre belirten bir Timespan değeri iş akışı boş olur ve kaldırıldı. Varsayılan değer 1 dakikadır.<br /><br /> Bir iş akışı kaldırılırken ayrıca kalıcı anlamına gelir. Bu öznitelik iş akışı örneği kalıcı ve hemen sonra kaldırıldığında sıfır olarak ayarlanırsa, iş akışı boş olur. Bu öznitelik için TimeSpan.MaxValue etkili bir şekilde ayarlanması kaldırma işlemi devre dışı bırakır. Boş iş akışı örnekleri hiçbir zaman kaldırılır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<davranış >, \<serviceBehaviors >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|Bir davranış öğesi belirtir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
