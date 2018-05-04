---
title: '&lt;workflowIdle&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
ms.openlocfilehash: 65bcc1ccd357fb7f331665aefbd975b11a2378cd
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltworkflowidlegt"></a>&lt;workflowIdle&gt;
Boşta iş akışı örnekleri zaman kaldırıldı ve kalıcı denetimleri hizmet davranışı.  
  
\<system.ServiceModel>  
\<davranışları >  
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
|timeToPersist|Zaman yayılımı değeri iş akışı boş olur ve kalıcı saat arasındaki süreyi belirtir. TimeSpan.MaxValue varsayılan değerdir.<br /><br /> İş akışı örneği boşta kaldığında geçmesini süresi başlar. Bu öznitelik, bir iş akışı örneği daha agresif mümkün olduğunca uzun bir süre bellekte hala örneği tutarken kalıcı hale getirmek istiyorsanız kullanışlıdır. Bu öznitelik yalnızca değerini ise geçerlidir küçük **timeToUnload** özniteliği. Büyükse, göz ardı edilir. Bu öznitelik ile belirtilen değer önce aşılırsa, **timeToUnload** özniteliği Kalıcılık iş akışı kaldırılmadan önce tamamlanmalıdır. Bu iş akışı kalıcı kadar kaldırma işlemi gecikebilir anlamına gelir. Saklama katmanını geçici hatalar için herhangi bir yeniden deneme işlemekten sorumludur ve kurtarılabilir olmayan hataları üzerinde yalnızca özel durum oluşturur. Bu nedenle, Kalıcılık sırasında karşılaşılan özel durumlar olarak kabul edilir ve iş akışı örneği durduruldu.|  
|timeToUnload|Saat arasındaki süre belirten bir Timespan değeri iş akışı boş olur ve kaldırıldı. Varsayılan değer 1 dakikadır.<br /><br /> Bir iş akışı kaldırılırken ayrıca kalıcı anlamına gelir. İş akışı örneği kalıcı ve hemen sonra kaldırıldığında sıfır bu öznitelik ayarlanırsa iş akışı boş olur. Bu öznitelik için TimeSpan.MaxValue etkili bir şekilde ayarlanması kaldırma işlemi devre dışı bırakır. Boş iş akışı örnekleri hiçbir zaman kaldırılır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<davranış >, \<serviceBehaviors >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|Bir davranış öğesi belirtir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
