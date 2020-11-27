---
title: WF 'de işlem etkinlikleri
ms.date: 03/30/2017
ms.assetid: fb33378e-82c6-4ea0-870f-76dc77e7f0fe
ms.openlocfilehash: c40799f7f0456a13ab975a766a36e9425a2144df
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293344"
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
