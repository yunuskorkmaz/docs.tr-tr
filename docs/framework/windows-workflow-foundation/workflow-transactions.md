---
title: İş akışı işlemleri
ms.date: 03/30/2017
ms.assetid: 6081fb02-c0f2-483d-97b8-f3b7dc03011d
ms.openlocfilehash: 17e4b712f5b6955ab777168d60d8a28e8b0ebd63
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59153302"
---
# <a name="workflow-transactions"></a>İş akışı işlemleri

[!INCLUDE[wf1](../../../includes/wf1-md.md)] katılmak için destek sağlayan <xref:System.Transactions> kullanarak işlemleri <xref:System.Activities.Statements.TransactionScope> işlem temelli bir iş birimi kapsamını belirlemek için etkinlik. Sırada <xref:System.Transactions.TransactionScope?displayProperty=nameWithType> açıkça tamamlanması gereken <xref:System.Activities.Statements.TransactionScope?displayProperty=nameWithType> etkinliği örtük olarak çağrıları tamamlamak işlemin başarıyla tamamlanmasından sonra üzerinde. Bulunan herhangi bir etkinlik <xref:System.Activities.Statements.TransactionScope.Body%2A> , <xref:System.Activities.Statements.TransactionScope> etkinliği bir işlemde katılmak. WF için bir iş akışı kullanarak akış işlemleri için <xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinlik. Gibi <xref:System.Activities.Statements.TransactionScope> etkinliği, bulunan herhangi bir etkinliği <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> harekete katılan. WF üzerinde bu etkinlikleri bağımlı sağlar <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType> çalışır ikisiyle <xref:System.Activities.Statements.TransactionScope> ve <xref:System.ServiceModel.Activities.TransactedReceiveScope>. Sistem tarafından sağlanan etkinlikler tüm gereksinimleri adres değil, özel etkinlikler kullanılarak oluşturulabilir <xref:System.Activities.RuntimeTransactionHandle> Gelişmiş Akış ve işlem denetimi senaryoları etkinleştirmek için.  
  
Aşağıdaki örnekte, bir iş akışı oluşan oluşturulan bir <xref:System.Activities.Statements.Sequence> alt etkinlikleri içeren etkinlik bir <xref:System.Activities.Statements.TransactionScope> etkinlik. <xref:System.Activities.Statements.TransactionScope.Body%2A> Etkinliklerini <xref:System.Activities.Statements.TransactionScope> tarafından başlatılan işlem altında yürütme <xref:System.Activities.Statements.TransactionScope> etkinlik.  
  
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
  
Kullanma hakkında daha fazla bilgi için bkz. <xref:System.ServiceModel.Activities.TransactedReceiveScope>, bkz: [içine ve iş akışı hizmetlerine işlemlerin akan](../wcf/feature-details/flowing-transactions-into-and-out-of-workflow-services.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Activities.Statements.TransactionScope>
- <xref:System.Transactions.TransactionScope>
- <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType>
