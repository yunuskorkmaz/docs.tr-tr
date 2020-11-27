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
# <a name="transaction-activities-in-wf"></a><span data-ttu-id="df15c-102">WF 'de işlem etkinlikleri</span><span class="sxs-lookup"><span data-stu-id="df15c-102">Transaction Activities in WF</span></span>

<span data-ttu-id="df15c-103">, [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] İşlemleri, dengelemesi ve iptali modellemek için sistem tarafından sunulan birkaç etkinliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="df15c-103">The [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] has several system-provided activities for modeling transactions, compensation, and cancellation.</span></span> <span data-ttu-id="df15c-104">Bu programlama modelleri iş mantığı ve hata işlemede değişiklik durumunda iş akışının ilerlemeye devam etmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="df15c-104">These programming models allow the workflow to continue forward progress in the event of changes in business logic and error handling.</span></span> <span data-ttu-id="df15c-105">İşlemler, Dengeleme ve iptal hakkında daha fazla bilgi için bkz. [işlemler](workflow-transactions.md), [Dengeleme](compensation.md)ve [iptal](modeling-cancellation-behavior-in-workflows.md).</span><span class="sxs-lookup"><span data-stu-id="df15c-105">For more information about transactions, compensation, and cancellation, see [Transactions](workflow-transactions.md), [Compensation](compensation.md), and [Cancellation](modeling-cancellation-behavior-in-workflows.md).</span></span>  
  
## <a name="transaction-activities"></a><span data-ttu-id="df15c-106">İşlem etkinlikleri</span><span class="sxs-lookup"><span data-stu-id="df15c-106">Transaction Activities</span></span>  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.CancellationScope>|<span data-ttu-id="df15c-107">İptal mantığını, bir etkinlik biçiminde, aynı zamanda bir etkinlik olarak ifade edilen ana yürütme yoluyla ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="df15c-107">Associates cancellation logic, in the form of an activity, with a main path of execution, also expressed as an activity.</span></span>|  
|<xref:System.Activities.Statements.CompensableActivity>|<span data-ttu-id="df15c-108">Alt etkinliklerinin tazminatı destekler.</span><span class="sxs-lookup"><span data-stu-id="df15c-108">Supports compensation of its child activities.</span></span>|  
|<xref:System.Activities.Statements.Compensate>|<span data-ttu-id="df15c-109">Bir öğesinin dengeleme işleyicisini açıkça çağırır <xref:System.Activities.Statements.CompensableActivity> .</span><span class="sxs-lookup"><span data-stu-id="df15c-109">Explicitly invokes the compensation handler of a <xref:System.Activities.Statements.CompensableActivity>.</span></span>|  
|<xref:System.Activities.Statements.Confirm>|<span data-ttu-id="df15c-110">Bir öğesinin onay işleyicisini açıkça çağırır <xref:System.Activities.Statements.CompensableActivity> .</span><span class="sxs-lookup"><span data-stu-id="df15c-110">Explicitly invokes the confirmation handler of a <xref:System.Activities.Statements.CompensableActivity>.</span></span>|  
|<xref:System.Activities.Statements.TransactionScope>|<span data-ttu-id="df15c-111">İşlem sınırının sınırlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="df15c-111">Demarcates a transaction boundary.</span></span>|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope>|<span data-ttu-id="df15c-112">Kapsam, alınan bir ileti tarafından başlatılan işlemin ömrünü.</span><span class="sxs-lookup"><span data-stu-id="df15c-112">Scopes the lifetime of a transaction that is initiated by a received message.</span></span> <span data-ttu-id="df15c-113">İşlem, başlatma iletisindeki iş akışına alınabilir veya ileti alındığında dağıtıcı tarafından oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="df15c-113">The transaction may be flowed into the workflow on the initiating message, or created by the dispatcher when the message is received.</span></span> <span data-ttu-id="df15c-114">**Note:**  , <xref:System.ServiceModel.Activities.TransactedReceiveScope> **Araç kutusunun** **mesajlaşma** bölümünde bulunur.</span><span class="sxs-lookup"><span data-stu-id="df15c-114">**Note:**  The <xref:System.ServiceModel.Activities.TransactedReceiveScope> is located in the **Messaging** section of the **Toolbox**.</span></span>|
