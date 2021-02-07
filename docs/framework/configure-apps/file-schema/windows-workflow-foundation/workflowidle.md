---
description: 'Hakkında daha fazla bilgi edinin: <workflowIdle>'
title: <workflowIdle>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
ms.openlocfilehash: c1707ab5c633a358846a8ddf529bbfab90d3012d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697965"
---
# \<workflowIdle>

Boştaki iş akışı örneklerinin ne zaman kaldırılabileceğini ve kalıcı olduğunu denetleyen bir hizmet davranışı.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowIdle>**  
  
## <a name="syntax"></a>Syntax  
  
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
|timeToPersist|İş akışının boşta olduğu ve kalıcı olduğu zaman arasındaki süreyi belirten bir TimeSpan değeri. Varsayılan değer TimeSpan. MaxValue ' dır.<br /><br /> İş akışı örneği boşta kaldığında geçmesini süresi başlar. Bu öznitelik, bir iş akışı örneğini daha fazla kararlılık halinde kalıcı hale getirmek istiyorsanız yararlıdır, ancak örneğin, örneği mümkün olduğunca uzun süre tutarken Bu öznitelik yalnızca değeri **TimeToUnload** özniteliğinden daha küçükse geçerlidir. Büyükse, göz ardı edilir. Bu öznitelik **TimeToUnload** özniteliği tarafından belirtilen değerden önce geçtiğinde, iş akışı kaldırılmadan önce Kalıcılık tamamlanmalıdır. Bu iş akışı kalıcı kadar kaldırma işlemi gecikebilir anlamına gelir. Kalıcılık katmanı, geçici hatalara yönelik yeniden denemeleri işlemekten sorumludur ve yalnızca kurtarılamaz hatalarda özel durumlar oluşturur. Bu nedenle, kalıcılık sırasında oluşan tüm özel durumlar önemli olarak değerlendirilir ve iş akışı örneği iptal edilir.|  
|timeToUnload|Saat arasındaki süre belirten bir Timespan değeri iş akışı boş olur ve kaldırıldı. Varsayılan değer 1 dakikadır.<br /><br /> Bir iş akışı kaldırılırken ayrıca kalıcı anlamına gelir. Bu öznitelik sıfır olarak ayarlandıysa iş akışı örneği kalıcıdır ve iş akışı boşta olduktan hemen sonra kaldırılır. Bu özniteliğin TimeSpan. MaxValue olarak ayarlanması, kaldırma işlemini etkin bir şekilde devre dışı bırakır. Boş iş akışı örnekleri hiçbir zaman kaldırılır.|  
  
### <a name="child-elements"></a>Alt Öğeler  

 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<behavior> durumunu \<serviceBehaviors>](behavior-of-servicebehaviors-of-workflow.md)|Bir davranış öğesi belirtir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
