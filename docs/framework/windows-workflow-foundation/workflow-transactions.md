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
# <a name="workflow-transactions"></a><span data-ttu-id="a7576-102">İş Akışı İşlemleri</span><span class="sxs-lookup"><span data-stu-id="a7576-102">Workflow Transactions</span></span>

[!INCLUDE[wf1](../../../includes/wf1-md.md)]<span data-ttu-id="a7576-103">etkinliği, işledilen <xref:System.Transactions> bir iş <xref:System.Activities.Statements.TransactionScope> birimini kapsamak için kullanarak işlemlere katılmak için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="a7576-103">provides support for participating in <xref:System.Transactions> transactions by using the <xref:System.Activities.Statements.TransactionScope> activity to scope a transacted unit of work.</span></span> <span data-ttu-id="a7576-104"><xref:System.Transactions.TransactionScope?displayProperty=nameWithType> Etkinlik açıkça tamamlanmış olsa <xref:System.Activities.Statements.TransactionScope?displayProperty=nameWithType> da, başarılı bir şekilde tamamlandıktan sonra işlem üzerinde örtülü olarak tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="a7576-104">While the <xref:System.Transactions.TransactionScope?displayProperty=nameWithType> must be explicitly completed the <xref:System.Activities.Statements.TransactionScope?displayProperty=nameWithType> activity implicitly calls complete on the transaction upon successful completion.</span></span> <span data-ttu-id="a7576-105"><xref:System.Activities.Statements.TransactionScope> Faaliyetin <xref:System.Activities.Statements.TransactionScope.Body%2A> içinde yer alan tüm etkinlikler işlemle katılır.</span><span class="sxs-lookup"><span data-stu-id="a7576-105">Any activities that are contained in the <xref:System.Activities.Statements.TransactionScope.Body%2A> of the <xref:System.Activities.Statements.TransactionScope> activity participate in the transaction.</span></span> <span data-ttu-id="a7576-106">WF, <xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinlik kullanımı yoluyla hareketleri iş akışına akabilir.</span><span class="sxs-lookup"><span data-stu-id="a7576-106">WF can to flow transactions into a workflow through the use of the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="a7576-107"><xref:System.Activities.Statements.TransactionScope> Etkinlik gibi, harekette yer <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> alan herhangi bir etkinlik de işlemde yer alır.</span><span class="sxs-lookup"><span data-stu-id="a7576-107">Like the <xref:System.Activities.Statements.TransactionScope> activity, any activity contained in the <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> participates in the transaction.</span></span> <span data-ttu-id="a7576-108">WF, faaliyetlerin hem <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType> de .'nin her ikisiyle <xref:System.Activities.Statements.TransactionScope> ve <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span><span class="sxs-lookup"><span data-stu-id="a7576-108">WF ensures that activities dependent on <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType> works with both <xref:System.Activities.Statements.TransactionScope> and <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span></span> <span data-ttu-id="a7576-109">Sistem tarafından sağlanan etkinlikler tüm gereksinimleri karşılamazsa, gelişmiş <xref:System.Activities.RuntimeTransactionHandle> akış ve işlem denetimi senaryolarını etkinleştirmek için özel etkinlikler oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="a7576-109">If the system-provided activities do not address all requirements, custom activities can be built using the <xref:System.Activities.RuntimeTransactionHandle> to enable advanced flow and transaction control scenarios.</span></span>  
  
<span data-ttu-id="a7576-110">Aşağıdaki örnekte, bir etkinlik de dahil <xref:System.Activities.Statements.Sequence> olmak üzere alt etkinlikleri <xref:System.Activities.Statements.TransactionScope> içeren bir etkinlik ten oluşan bir iş akışı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a7576-110">In the following example, a workflow is constructed consisting of a <xref:System.Activities.Statements.Sequence> activity that contains child activities including a <xref:System.Activities.Statements.TransactionScope> activity.</span></span> <span data-ttu-id="a7576-111">İşlem altında <xref:System.Activities.Statements.TransactionScope.Body%2A> <xref:System.Activities.Statements.TransactionScope> yürütülen faaliyetler, etkinlik tarafından başlatıldı. <xref:System.Activities.Statements.TransactionScope></span><span class="sxs-lookup"><span data-stu-id="a7576-111">The <xref:System.Activities.Statements.TransactionScope.Body%2A> activities of the <xref:System.Activities.Statements.TransactionScope> execute under the transaction initialized by the <xref:System.Activities.Statements.TransactionScope> activity.</span></span>  
  
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
  
<span data-ttu-id="a7576-112">Daha fazla bilgi için <xref:System.ServiceModel.Activities.TransactedReceiveScope>bkz: İş [Akışı Hizmetlerine Giren ve Çıkan İşlemler](../wcf/feature-details/flowing-transactions-into-and-out-of-workflow-services.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="a7576-112">For more information, see about using <xref:System.ServiceModel.Activities.TransactedReceiveScope>, see [Flowing Transactions into and out of Workflow Services](../wcf/feature-details/flowing-transactions-into-and-out-of-workflow-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7576-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7576-113">See also</span></span>

- <xref:System.Activities.Statements.TransactionScope>
- <xref:System.Transactions.TransactionScope>
- <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType>
