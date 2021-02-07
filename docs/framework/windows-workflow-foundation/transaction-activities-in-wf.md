---
description: "Daha fazla bilgi edinin: WF 'de Işlem etkinlikleri"
title: WF 'de işlem etkinlikleri
ms.date: 03/30/2017
ms.assetid: fb33378e-82c6-4ea0-870f-76dc77e7f0fe
ms.openlocfilehash: f088c586998d3dbec8b94dcf0f02603a68b55a40
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755141"
---
# <a name="transaction-activities-in-wf"></a>WF 'de işlem etkinlikleri

, [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] İşlemleri, dengelemesi ve iptali modellemek için sistem tarafından sunulan birkaç etkinliğe sahiptir. Bu programlama modelleri iş mantığı ve hata işlemede değişiklik durumunda iş akışının ilerlemeye devam etmesine olanak tanır. İşlemler, Dengeleme ve iptal hakkında daha fazla bilgi için bkz. [işlemler](workflow-transactions.md), [Dengeleme](compensation.md)ve [iptal](modeling-cancellation-behavior-in-workflows.md).  
  
## <a name="transaction-activities"></a>İşlem etkinlikleri  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.CancellationScope>|İptal mantığını, bir etkinlik biçiminde, aynı zamanda bir etkinlik olarak ifade edilen ana yürütme yoluyla ilişkilendirir.|  
|<xref:System.Activities.Statements.CompensableActivity>|Alt etkinliklerinin tazminatı destekler.|  
|<xref:System.Activities.Statements.Compensate>|Bir öğesinin dengeleme işleyicisini açıkça çağırır <xref:System.Activities.Statements.CompensableActivity> .|  
|<xref:System.Activities.Statements.Confirm>|Bir öğesinin onay işleyicisini açıkça çağırır <xref:System.Activities.Statements.CompensableActivity> .|  
|<xref:System.Activities.Statements.TransactionScope>|İşlem sınırının sınırlarını kaldırır.|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope>|Kapsam, alınan bir ileti tarafından başlatılan işlemin ömrünü. İşlem, başlatma iletisindeki iş akışına alınabilir veya ileti alındığında dağıtıcı tarafından oluşturulabilir. **Note:**  , <xref:System.ServiceModel.Activities.TransactedReceiveScope> **Araç kutusunun** **mesajlaşma** bölümünde bulunur.|
