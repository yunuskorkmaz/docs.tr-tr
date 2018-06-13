---
title: İş akışı işlemleri
ms.date: 03/30/2017
ms.assetid: 6081fb02-c0f2-483d-97b8-f3b7dc03011d
ms.openlocfilehash: 2bb5f6498b365f3b773eea9a5adce1ec1158a289
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517260"
---
# <a name="workflow-transactions"></a>İş akışı işlemleri
[!INCLUDE[wf1](../../../includes/wf1-md.md)] katılan için destek sağlar <xref:System.Transactions> kullanarak işlemleri <xref:System.Activities.Statements.TransactionScope> hizmetteki bir iş birimine kapsam için etkinliği. Sırada <xref:System.Transactions.TransactionScope?displayProperty=nameWithType> açıkça doldurulmalıdır <xref:System.Activities.Statements.TransactionScope?displayProperty=nameWithType> etkinlik örtük olarak çağrılarını tamamlamak başarıyla tamamlandıktan sonra işlem üzerinde. İçerdiği tüm etkinlikleri <xref:System.Activities.Statements.TransactionScope.Body%2A> , <xref:System.Activities.Statements.TransactionScope> etkinlik katılmak işlemde. WF için bir iş akışı kullanarak akış işlemleri için <xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinlik. Gibi <xref:System.Activities.Statements.TransactionScope> etkinliği, bulunan herhangi bir etkinlik <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> işlemde katılır. WF üzerinde bu etkinlikleri bağımlı sağlar <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType> ikisi ile çalışır <xref:System.Activities.Statements.TransactionScope> ve <xref:System.ServiceModel.Activities.TransactedReceiveScope>. Sistem tarafından sağlanan etkinlikler tüm gereksinimlere değil, özel etkinlikler kullanılarak oluşturulabilir <xref:System.Activities.RuntimeTransactionHandle> Gelişmiş Akış ve işlem denetimi senaryoları etkinleştirmek için.  
  
 Aşağıdaki örnekte, geçen [temel TransactionScope](../../../docs/framework/windows-workflow-foundation/samples/basic-transactionscope.md) örnek, bir iş akışı oluşan yapılandırılmıştır bir <xref:System.Activities.Statements.Sequence> alt etkinlikler dahil olmak üzere içeren etkinliği bir <xref:System.Activities.Statements.TransactionScope> etkinlik. <xref:System.Activities.Statements.TransactionScope.Body%2A> Etkinliklerini <xref:System.Activities.Statements.TransactionScope> altında tarafından başlatılan işlem yürütme <xref:System.Activities.Statements.TransactionScope> etkinlik.  
  
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
  
 Temel daha fazla bilgi için bkz: [işlemleri](../../../docs/framework/windows-workflow-foundation/samples/transactions.md) örnekleri ve temel senaryo [işlemleri](../../../docs/framework/windows-workflow-foundation/samples/transactions.md) örnekleri. Kullanma hakkında daha fazla bilgi için bkz: <xref:System.ServiceModel.Activities.TransactedReceiveScope>, bkz: [içine ve dışına iş akışı hizmetlerine işlemlerin akan](../../../docs/framework/wcf/feature-details/flowing-transactions-into-and-out-of-workflow-services.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Activities.Statements.TransactionScope>  
 <xref:System.Transactions.TransactionScope>  
 <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType>
