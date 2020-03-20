---
title: İş Akışı İşlemleri
ms.date: 03/30/2017
ms.assetid: 6081fb02-c0f2-483d-97b8-f3b7dc03011d
ms.openlocfilehash: 223c18195c8ffd0b51eb5dff77aa81953f6e47a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182670"
---
# <a name="workflow-transactions"></a>İş Akışı İşlemleri

[!INCLUDE[wf1](../../../includes/wf1-md.md)]etkinliği, işledilen <xref:System.Transactions> bir iş <xref:System.Activities.Statements.TransactionScope> birimini kapsamak için kullanarak işlemlere katılmak için destek sağlar. <xref:System.Transactions.TransactionScope?displayProperty=nameWithType> Etkinlik açıkça tamamlanmış olsa <xref:System.Activities.Statements.TransactionScope?displayProperty=nameWithType> da, başarılı bir şekilde tamamlandıktan sonra işlem üzerinde örtülü olarak tamamlanır. <xref:System.Activities.Statements.TransactionScope> Faaliyetin <xref:System.Activities.Statements.TransactionScope.Body%2A> içinde yer alan tüm etkinlikler işlemle katılır. WF, <xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinlik kullanımı yoluyla hareketleri iş akışına akabilir. <xref:System.Activities.Statements.TransactionScope> Etkinlik gibi, harekette yer <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> alan herhangi bir etkinlik de işlemde yer alır. WF, faaliyetlerin hem <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType> de .'nin her ikisiyle <xref:System.Activities.Statements.TransactionScope> ve <xref:System.ServiceModel.Activities.TransactedReceiveScope>. Sistem tarafından sağlanan etkinlikler tüm gereksinimleri karşılamazsa, gelişmiş <xref:System.Activities.RuntimeTransactionHandle> akış ve işlem denetimi senaryolarını etkinleştirmek için özel etkinlikler oluşturulabilir.  
  
Aşağıdaki örnekte, bir etkinlik de dahil <xref:System.Activities.Statements.Sequence> olmak üzere alt etkinlikleri <xref:System.Activities.Statements.TransactionScope> içeren bir etkinlik ten oluşan bir iş akışı oluşturulur. İşlem altında <xref:System.Activities.Statements.TransactionScope.Body%2A> <xref:System.Activities.Statements.TransactionScope> yürütülen faaliyetler, etkinlik tarafından başlatıldı. <xref:System.Activities.Statements.TransactionScope>  
  
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
  
Daha fazla bilgi için <xref:System.ServiceModel.Activities.TransactedReceiveScope>bkz: İş [Akışı Hizmetlerine Giren ve Çıkan İşlemler](../wcf/feature-details/flowing-transactions-into-and-out-of-workflow-services.md)bölümüne bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Activities.Statements.TransactionScope>
- <xref:System.Transactions.TransactionScope>
- <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType>
