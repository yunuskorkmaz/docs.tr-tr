---
title: İşlem WF etkinlikleri
ms.date: 03/30/2017
ms.assetid: fb33378e-82c6-4ea0-870f-76dc77e7f0fe
ms.openlocfilehash: 7ffd64abdc6edf45174d4b756833d65ec0ef747c
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57714781"
---
# <a name="transaction-activities-in-wf"></a>İşlem WF etkinlikleri
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] İşlemler ve Dengeleme iptal modelleme için birçok sistem tarafından sağlanan etkinlikleri içerir. Bu programlama modellerine ilerleme durumunda değişiklikler iş mantığı ve hata işleme devam etmek iş akışı sağlar. İşlemler ve Dengeleme iptal hakkında daha fazla bilgi için bkz: [işlemleri](workflow-transactions.md), [maaş](compensation.md), ve [iptal](modeling-cancellation-behavior-in-workflows.md).  
  
## <a name="transaction-activities"></a>İşlem etkinlikleri  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.CancellationScope>|Yürütme, ayrıca bir etkinlik ifade edilen bir ana yol biçiminde bir etkinlik iptal etme mantığı ilişkilendirir.|  
|<xref:System.Activities.Statements.CompensableActivity>|Alt etkinliklerinin maaş destekler.|  
|<xref:System.Activities.Statements.Compensate>|Açıkça'nin Dengeleme işleyicisini çağırır bir <xref:System.Activities.Statements.CompensableActivity>.|  
|<xref:System.Activities.Statements.Confirm>|Açıkça nin Dengeleme işleyicisini çağırır bir <xref:System.Activities.Statements.CompensableActivity>.|  
|<xref:System.Activities.Statements.TransactionScope>|Bir işlem sınırı demarcates.|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope>|Kapsamları ömrünü bir alınan ileti tarafından başlatılan bir işlem. İşlem iş akışı başlatma iletisi içine aktarılan, veya olabilir iletisi alındığında gönderici tarafından oluşturuldu. **Not:**  <xref:System.ServiceModel.Activities.TransactedReceiveScope> Bulunan **Mesajlaşma** bölümünü **araç kutusu**.|
