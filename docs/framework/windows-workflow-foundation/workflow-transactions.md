---
title: İş akışı işlemleri
ms.date: 03/30/2017
ms.assetid: 6081fb02-c0f2-483d-97b8-f3b7dc03011d
ms.openlocfilehash: e2a0c301abac562904e976fe09e5a68697b191e5
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48779965"
---
# <a name="workflow-transactions"></a><span data-ttu-id="8f2e3-102">İş akışı işlemleri</span><span class="sxs-lookup"><span data-stu-id="8f2e3-102">Workflow Transactions</span></span>

[!INCLUDE[wf1](../../../includes/wf1-md.md)] <span data-ttu-id="8f2e3-103">katılmak için destek sağlayan <xref:System.Transactions> kullanarak işlemleri <xref:System.Activities.Statements.TransactionScope> işlem temelli bir iş birimi kapsamını belirlemek için etkinlik.</span><span class="sxs-lookup"><span data-stu-id="8f2e3-103"> provides support for participating in <xref:System.Transactions> transactions by using the <xref:System.Activities.Statements.TransactionScope> activity to scope a transacted unit of work.</span></span> <span data-ttu-id="8f2e3-104">Sırada <xref:System.Transactions.TransactionScope?displayProperty=nameWithType> açıkça tamamlanması gereken <xref:System.Activities.Statements.TransactionScope?displayProperty=nameWithType> etkinliği örtük olarak çağrıları tamamlamak işlemin başarıyla tamamlanmasından sonra üzerinde.</span><span class="sxs-lookup"><span data-stu-id="8f2e3-104">While the <xref:System.Transactions.TransactionScope?displayProperty=nameWithType> must be explicitly completed the <xref:System.Activities.Statements.TransactionScope?displayProperty=nameWithType> activity implicitly calls complete on the transaction upon successful completion.</span></span> <span data-ttu-id="8f2e3-105">Bulunan herhangi bir etkinlik <xref:System.Activities.Statements.TransactionScope.Body%2A> , <xref:System.Activities.Statements.TransactionScope> etkinliği bir işlemde katılmak.</span><span class="sxs-lookup"><span data-stu-id="8f2e3-105">Any activities that are contained in the <xref:System.Activities.Statements.TransactionScope.Body%2A> of the <xref:System.Activities.Statements.TransactionScope> activity participate in the transaction.</span></span> <span data-ttu-id="8f2e3-106">WF için bir iş akışı kullanarak akış işlemleri için <xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="8f2e3-106">WF can to flow transactions into a workflow through the use of the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="8f2e3-107">Gibi <xref:System.Activities.Statements.TransactionScope> etkinliği, bulunan herhangi bir etkinliği <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> harekete katılan.</span><span class="sxs-lookup"><span data-stu-id="8f2e3-107">Like the <xref:System.Activities.Statements.TransactionScope> activity, any activity contained in the <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> participates in the transaction.</span></span> <span data-ttu-id="8f2e3-108">WF üzerinde bu etkinlikleri bağımlı sağlar <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType> çalışır ikisiyle <xref:System.Activities.Statements.TransactionScope> ve <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span><span class="sxs-lookup"><span data-stu-id="8f2e3-108">WF ensures that activities dependent on <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType> works with both <xref:System.Activities.Statements.TransactionScope> and <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span></span> <span data-ttu-id="8f2e3-109">Sistem tarafından sağlanan etkinlikler tüm gereksinimleri adres değil, özel etkinlikler kullanılarak oluşturulabilir <xref:System.Activities.RuntimeTransactionHandle> Gelişmiş Akış ve işlem denetimi senaryoları etkinleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="8f2e3-109">If the system-provided activities do not address all requirements, custom activities can be built using the <xref:System.Activities.RuntimeTransactionHandle> to enable advanced flow and transaction control scenarios.</span></span>  
  
<span data-ttu-id="8f2e3-110">Aşağıdaki örnekte, bir iş akışı oluşan oluşturulan bir <xref:System.Activities.Statements.Sequence> alt etkinlikleri içeren etkinlik bir <xref:System.Activities.Statements.TransactionScope> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="8f2e3-110">In the following example, a workflow is constructed consisting of a <xref:System.Activities.Statements.Sequence> activity that contains child activities including a <xref:System.Activities.Statements.TransactionScope> activity.</span></span> <span data-ttu-id="8f2e3-111"><xref:System.Activities.Statements.TransactionScope.Body%2A> Etkinliklerini <xref:System.Activities.Statements.TransactionScope> tarafından başlatılan işlem altında yürütme <xref:System.Activities.Statements.TransactionScope> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="8f2e3-111">The <xref:System.Activities.Statements.TransactionScope.Body%2A> activities of the <xref:System.Activities.Statements.TransactionScope> execute under the transaction initialized by the <xref:System.Activities.Statements.TransactionScope> activity.</span></span>  
  
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
  
<span data-ttu-id="8f2e3-112">Kullanma hakkında daha fazla bilgi için bkz. <xref:System.ServiceModel.Activities.TransactedReceiveScope>, bkz: [içine ve iş akışı hizmetlerine işlemlerin akan](../../../docs/framework/wcf/feature-details/flowing-transactions-into-and-out-of-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="8f2e3-112">For more information, see about using <xref:System.ServiceModel.Activities.TransactedReceiveScope>, see [Flowing Transactions into and out of Workflow Services](../../../docs/framework/wcf/feature-details/flowing-transactions-into-and-out-of-workflow-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f2e3-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8f2e3-113">See Also</span></span>  
 <xref:System.Activities.Statements.TransactionScope>  
 <xref:System.Transactions.TransactionScope>  
 <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType>
