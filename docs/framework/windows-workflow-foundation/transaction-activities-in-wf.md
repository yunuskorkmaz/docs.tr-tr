---
title: "WF işlem etkinlikleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb33378e-82c6-4ea0-870f-76dc77e7f0fe
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f6132f1d9cbeef3ed7af5d2b711d04e8bd5755bb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="transaction-activities-in-wf"></a>WF işlem etkinlikleri
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] İşlemleri, maaş ve iptal modelleme için birkaç sistem tarafından sağlanan etkinlikler içeriyor. Bu programlama modellerine ilerleme durumunda değişiklikler iş mantığı ve hata işleme devam etmek iş akışı izin verir. [!INCLUDE[crabout](../../../includes/crabout-md.md)]işlemleri, maaş ve iptal etme, bkz: [işlemleri](../../../docs/framework/windows-workflow-foundation/workflow-transactions.md), [maaş](../../../docs/framework/windows-workflow-foundation/compensation.md), ve [iptal](../../../docs/framework/windows-workflow-foundation/modeling-cancellation-behavior-in-workflows.md).  
  
## <a name="transaction-activities"></a>İşlem etkinlikleri  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.CancellationScope>|Ana yol yürütme, ayrıca bir etkinlik olarak ifade edilen bir etkinlik biçiminde iptal mantığı ilişkilendirir.|  
|<xref:System.Activities.Statements.CompensableActivity>|Kendi alt etkinliklerin maaş destekler.|  
|<xref:System.Activities.Statements.Compensate>|Açıkça maaş işleyicisini çağıran bir <xref:System.Activities.Statements.CompensableActivity>.|  
|<xref:System.Activities.Statements.Confirm>|Açıkça, onay işleyiciyi çağırır bir <xref:System.Activities.Statements.CompensableActivity>.|  
|<xref:System.Activities.Statements.TransactionScope>|Bir işlem sınır demarcates.|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope>|Alınan ileti tarafından başlatılan bir işlem ömrü kapsamları. İşlem başlatma iletisi üzerinde iş akışına akışı yapılan işlem, veya olabilir iletisi alındığında gönderici tarafından oluşturuldu. **Not:** <xref:System.ServiceModel.Activities.TransactedReceiveScope> bulunan **ileti** bölümünü **araç**.|
