---
title: '&lt;workflowIdle&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
ms.openlocfilehash: 9d9eb45090367fb2cc18fc357c219e74d63fb667
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54628108"
---
# <a name="ltworkflowidlegt"></a>&lt;workflowIdle&gt;
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
