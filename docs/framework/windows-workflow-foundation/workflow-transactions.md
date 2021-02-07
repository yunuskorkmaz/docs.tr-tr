---
description: 'Daha fazla bilgi edinin: Iş akışı Işlemleri'
title: İş akışı Işlemleri
ms.date: 03/30/2017
ms.assetid: 6081fb02-c0f2-483d-97b8-f3b7dc03011d
ms.openlocfilehash: 105876179bcfe685bc65b209f0fbacb1d6eae5bc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754881"
---
# <a name="workflow-transactions"></a>İş akışı Işlemleri

[!INCLUDE[wf1](../../../includes/wf1-md.md)] , <xref:System.Transactions> <xref:System.Activities.Statements.TransactionScope> işlenen bir iş biriminin kapsamını sağlamak için etkinliğini kullanarak işlemlere katılma desteği sağlar. <xref:System.Transactions.TransactionScope?displayProperty=nameWithType>Açıkça tamamlanması gerekir, ancak başarılı bir şekilde <xref:System.Activities.Statements.TransactionScope?displayProperty=nameWithType> tamamlandıktan sonra etkinliğin işlem üzerinde tamamlanmış olarak tamamlandı çağrısı. Etkinliğin içinde yer alan tüm etkinlikler <xref:System.Activities.Statements.TransactionScope.Body%2A> <xref:System.Activities.Statements.TransactionScope> işleme katılır. WF, etkinliğin kullanımı aracılığıyla işlemleri bir iş akışına akabilir <xref:System.ServiceModel.Activities.TransactedReceiveScope> . Etkinlik gibi <xref:System.Activities.Statements.TransactionScope> , işlemde yer alan herhangi bir etkinlik gibi <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> . WF, etkinliklerin <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType> hem hem de ile çalışmasına bağımlı olmasını sağlar <xref:System.Activities.Statements.TransactionScope> <xref:System.ServiceModel.Activities.TransactedReceiveScope> . Sistem tarafından sağlanmış etkinlikler tüm gereksinimleri ele alıyorsa, <xref:System.Activities.RuntimeTransactionHandle> Gelişmiş akış ve işlem denetimi senaryolarını etkinleştirmek için özel etkinlikler kullanılarak oluşturulabilir.  
  
Aşağıdaki örnekte, bir <xref:System.Activities.Statements.Sequence> etkinlik dahil alt etkinlikler içeren bir etkinlikten oluşan bir iş akışı oluşturulur <xref:System.Activities.Statements.TransactionScope> . <xref:System.Activities.Statements.TransactionScope.Body%2A> <xref:System.Activities.Statements.TransactionScope> Etkinliği tarafından başlatılan işlem altında yürütülen etkinlikler <xref:System.Activities.Statements.TransactionScope> .  
  
```csharp  
static Activity ScenarioOne()  
{  
    return new Sequence  
    {  
        Activities =  
        {  
            new WriteLine { Text = "    Begin workflow" },  
  
            new TransactionScope  
            {  
                Body = new Sequence  
                {  
                    Activities =
                    {  
                        new WriteLine { Text = "    Begin TransactionScope" },  
  
                        new PrintTransactionId(),  
  
                        new TransactionScopeTest(),  
  
                        new WriteLine { Text = "    End TransactionScope" },  
                    },  
                },  
            },  
  
            new WriteLine { Text = "    End workflow" },  
        }  
    };  
}  
```  
  
Daha fazla bilgi için bkz. kullanma hakkında <xref:System.ServiceModel.Activities.TransactedReceiveScope> , bkz. [Iş akışı hizmetleri içine ve dışına akan işlemler](../wcf/feature-details/flowing-transactions-into-and-out-of-workflow-services.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Activities.Statements.TransactionScope>
- <xref:System.Transactions.TransactionScope>
- <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType>
