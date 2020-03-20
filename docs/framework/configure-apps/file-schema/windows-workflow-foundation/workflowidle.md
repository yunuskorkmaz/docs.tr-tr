---
title: <workflowIdle>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
ms.openlocfilehash: d9eb182ef9c35d2e4c6f5d434e6b200ae2e7ca26
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151851"
---
# <a name="workflowidle"></a>\<iş akışıBoş>
Boşta kalan iş akışı örnekleri boşaldığında ve kalıcı olduğunda denetleyen bir hizmet davranışı.  
  
[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<Sistem. ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<davranışlar>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<davranış>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<iş akışıBoş>**  
  
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
|timeToPersist|İş akışının boşta kalıp kalıcı olduğu süreyi belirten bir Zaman Dilimi değeri. Varsayılan değer TimeSpan.MaxValue'dir.<br /><br /> İş akışı örneği boşta kaldığında geçmesini süresi başlar. Bu öznitelik, bir iş akışı örneğini mümkün olduğunca uzun süre bellekte tutarken daha agresif bir şekilde sürdürmek istiyorsanız yararlıdır. Bu öznitelik yalnızca değeri **timeToUnload** özniteliğinden daha azsa geçerlidir. Büyükse, göz ardı edilir. Bu **öznitelik, zaman ToUnload** özniteliği tarafından belirtilen değerden önce atılırsa, iş akışı kaldırılmadan önce kalıcılığın tamamlanması gerekir. Bu iş akışı kalıcı kadar kaldırma işlemi gecikebilir anlamına gelir. Kalıcılık katmanı geçici hatalar için herhangi bir yeniden deneme işlemek için sorumludur ve yalnızca kurtarılamaz hatalar üzerinde özel durumlar atar. Bu nedenle, kalıcılık sırasında atılan tüm özel durumlar ölümcül olarak kabul edilir ve iş akışı örneği iptal edilir.|  
|timeToUnload|Saat arasındaki süre belirten bir Timespan değeri iş akışı boş olur ve kaldırıldı. Varsayılan değer 1 dakikadır.<br /><br /> Bir iş akışı kaldırılırken ayrıca kalıcı anlamına gelir. Bu öznitelik sıfırolarak ayarlanırsa, iş akışı örneği kalıcı dır ve iş akışı boşta kaldıktan hemen sonra boşaltılır. Bu özniteliği TimeSpan.MaxValue olarak ayarlamak, boşaltma işlemini etkin bir şekilde devre dışı eder. Boş iş akışı örnekleri hiçbir zaman kaldırılır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<hizmet davranış \<>Davranışlar>](behavior-of-servicebehaviors-of-workflow.md)|Bir davranış öğesi belirtir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
