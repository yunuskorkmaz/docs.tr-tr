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
# <a name="workflow-transactions"></a><span data-ttu-id="5025e-103">İş akışı Işlemleri</span><span class="sxs-lookup"><span data-stu-id="5025e-103">Workflow Transactions</span></span>

[!INCLUDE[wf1](../../../includes/wf1-md.md)] <span data-ttu-id="5025e-104">, <xref:System.Transactions> <xref:System.Activities.Statements.TransactionScope> işlenen bir iş biriminin kapsamını sağlamak için etkinliğini kullanarak işlemlere katılma desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="5025e-104">provides support for participating in <xref:System.Transactions> transactions by using the <xref:System.Activities.Statements.TransactionScope> activity to scope a transacted unit of work.</span></span> <span data-ttu-id="5025e-105"><xref:System.Transactions.TransactionScope?displayProperty=nameWithType>Açıkça tamamlanması gerekir, ancak başarılı bir şekilde <xref:System.Activities.Statements.TransactionScope?displayProperty=nameWithType> tamamlandıktan sonra etkinliğin işlem üzerinde tamamlanmış olarak tamamlandı çağrısı.</span><span class="sxs-lookup"><span data-stu-id="5025e-105">While the <xref:System.Transactions.TransactionScope?displayProperty=nameWithType> must be explicitly completed the <xref:System.Activities.Statements.TransactionScope?displayProperty=nameWithType> activity implicitly calls complete on the transaction upon successful completion.</span></span> <span data-ttu-id="5025e-106">Etkinliğin içinde yer alan tüm etkinlikler <xref:System.Activities.Statements.TransactionScope.Body%2A> <xref:System.Activities.Statements.TransactionScope> işleme katılır.</span><span class="sxs-lookup"><span data-stu-id="5025e-106">Any activities that are contained in the <xref:System.Activities.Statements.TransactionScope.Body%2A> of the <xref:System.Activities.Statements.TransactionScope> activity participate in the transaction.</span></span> <span data-ttu-id="5025e-107">WF, etkinliğin kullanımı aracılığıyla işlemleri bir iş akışına akabilir <xref:System.ServiceModel.Activities.TransactedReceiveScope> .</span><span class="sxs-lookup"><span data-stu-id="5025e-107">WF can to flow transactions into a workflow through the use of the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="5025e-108">Etkinlik gibi <xref:System.Activities.Statements.TransactionScope> , işlemde yer alan herhangi bir etkinlik gibi <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> .</span><span class="sxs-lookup"><span data-stu-id="5025e-108">Like the <xref:System.Activities.Statements.TransactionScope> activity, any activity contained in the <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> participates in the transaction.</span></span> <span data-ttu-id="5025e-109">WF, etkinliklerin <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType> hem hem de ile çalışmasına bağımlı olmasını sağlar <xref:System.Activities.Statements.TransactionScope> <xref:System.ServiceModel.Activities.TransactedReceiveScope> .</span><span class="sxs-lookup"><span data-stu-id="5025e-109">WF ensures that activities dependent on <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType> works with both <xref:System.Activities.Statements.TransactionScope> and <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span></span> <span data-ttu-id="5025e-110">Sistem tarafından sağlanmış etkinlikler tüm gereksinimleri ele alıyorsa, <xref:System.Activities.RuntimeTransactionHandle> Gelişmiş akış ve işlem denetimi senaryolarını etkinleştirmek için özel etkinlikler kullanılarak oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="5025e-110">If the system-provided activities do not address all requirements, custom activities can be built using the <xref:System.Activities.RuntimeTransactionHandle> to enable advanced flow and transaction control scenarios.</span></span>  
  
<span data-ttu-id="5025e-111">Aşağıdaki örnekte, bir <xref:System.Activities.Statements.Sequence> etkinlik dahil alt etkinlikler içeren bir etkinlikten oluşan bir iş akışı oluşturulur <xref:System.Activities.Statements.TransactionScope> .</span><span class="sxs-lookup"><span data-stu-id="5025e-111">In the following example, a workflow is constructed consisting of a <xref:System.Activities.Statements.Sequence> activity that contains child activities including a <xref:System.Activities.Statements.TransactionScope> activity.</span></span> <span data-ttu-id="5025e-112"><xref:System.Activities.Statements.TransactionScope.Body%2A> <xref:System.Activities.Statements.TransactionScope> Etkinliği tarafından başlatılan işlem altında yürütülen etkinlikler <xref:System.Activities.Statements.TransactionScope> .</span><span class="sxs-lookup"><span data-stu-id="5025e-112">The <xref:System.Activities.Statements.TransactionScope.Body%2A> activities of the <xref:System.Activities.Statements.TransactionScope> execute under the transaction initialized by the <xref:System.Activities.Statements.TransactionScope> activity.</span></span>  
  
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
  
<span data-ttu-id="5025e-113">Daha fazla bilgi için bkz. kullanma hakkında <xref:System.ServiceModel.Activities.TransactedReceiveScope> , bkz. [Iş akışı hizmetleri içine ve dışına akan işlemler](../wcf/feature-details/flowing-transactions-into-and-out-of-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="5025e-113">For more information, see about using <xref:System.ServiceModel.Activities.TransactedReceiveScope>, see [Flowing Transactions into and out of Workflow Services](../wcf/feature-details/flowing-transactions-into-and-out-of-workflow-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5025e-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5025e-114">See also</span></span>

- <xref:System.Activities.Statements.TransactionScope>
- <xref:System.Transactions.TransactionScope>
- <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType>
