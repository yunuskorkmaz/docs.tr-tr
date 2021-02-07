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
# <a name="transaction-activities-in-wf"></a><span data-ttu-id="eb68a-103">WF 'de işlem etkinlikleri</span><span class="sxs-lookup"><span data-stu-id="eb68a-103">Transaction Activities in WF</span></span>

<span data-ttu-id="eb68a-104">, [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] İşlemleri, dengelemesi ve iptali modellemek için sistem tarafından sunulan birkaç etkinliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="eb68a-104">The [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] has several system-provided activities for modeling transactions, compensation, and cancellation.</span></span> <span data-ttu-id="eb68a-105">Bu programlama modelleri iş mantığı ve hata işlemede değişiklik durumunda iş akışının ilerlemeye devam etmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="eb68a-105">These programming models allow the workflow to continue forward progress in the event of changes in business logic and error handling.</span></span> <span data-ttu-id="eb68a-106">İşlemler, Dengeleme ve iptal hakkında daha fazla bilgi için bkz. [işlemler](workflow-transactions.md), [Dengeleme](compensation.md)ve [iptal](modeling-cancellation-behavior-in-workflows.md).</span><span class="sxs-lookup"><span data-stu-id="eb68a-106">For more information about transactions, compensation, and cancellation, see [Transactions](workflow-transactions.md), [Compensation](compensation.md), and [Cancellation](modeling-cancellation-behavior-in-workflows.md).</span></span>  
  
## <a name="transaction-activities"></a><span data-ttu-id="eb68a-107">İşlem etkinlikleri</span><span class="sxs-lookup"><span data-stu-id="eb68a-107">Transaction Activities</span></span>  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.CancellationScope>|<span data-ttu-id="eb68a-108">İptal mantığını, bir etkinlik biçiminde, aynı zamanda bir etkinlik olarak ifade edilen ana yürütme yoluyla ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="eb68a-108">Associates cancellation logic, in the form of an activity, with a main path of execution, also expressed as an activity.</span></span>|  
|<xref:System.Activities.Statements.CompensableActivity>|<span data-ttu-id="eb68a-109">Alt etkinliklerinin tazminatı destekler.</span><span class="sxs-lookup"><span data-stu-id="eb68a-109">Supports compensation of its child activities.</span></span>|  
|<xref:System.Activities.Statements.Compensate>|<span data-ttu-id="eb68a-110">Bir öğesinin dengeleme işleyicisini açıkça çağırır <xref:System.Activities.Statements.CompensableActivity> .</span><span class="sxs-lookup"><span data-stu-id="eb68a-110">Explicitly invokes the compensation handler of a <xref:System.Activities.Statements.CompensableActivity>.</span></span>|  
|<xref:System.Activities.Statements.Confirm>|<span data-ttu-id="eb68a-111">Bir öğesinin onay işleyicisini açıkça çağırır <xref:System.Activities.Statements.CompensableActivity> .</span><span class="sxs-lookup"><span data-stu-id="eb68a-111">Explicitly invokes the confirmation handler of a <xref:System.Activities.Statements.CompensableActivity>.</span></span>|  
|<xref:System.Activities.Statements.TransactionScope>|<span data-ttu-id="eb68a-112">İşlem sınırının sınırlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="eb68a-112">Demarcates a transaction boundary.</span></span>|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope>|<span data-ttu-id="eb68a-113">Kapsam, alınan bir ileti tarafından başlatılan işlemin ömrünü.</span><span class="sxs-lookup"><span data-stu-id="eb68a-113">Scopes the lifetime of a transaction that is initiated by a received message.</span></span> <span data-ttu-id="eb68a-114">İşlem, başlatma iletisindeki iş akışına alınabilir veya ileti alındığında dağıtıcı tarafından oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="eb68a-114">The transaction may be flowed into the workflow on the initiating message, or created by the dispatcher when the message is received.</span></span> <span data-ttu-id="eb68a-115">**Note:**  , <xref:System.ServiceModel.Activities.TransactedReceiveScope> **Araç kutusunun** **mesajlaşma** bölümünde bulunur.</span><span class="sxs-lookup"><span data-stu-id="eb68a-115">**Note:**  The <xref:System.ServiceModel.Activities.TransactedReceiveScope> is located in the **Messaging** section of the **Toolbox**.</span></span>|
