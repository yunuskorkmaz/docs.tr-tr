---
title: "WF işlem etkinlikleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb33378e-82c6-4ea0-870f-76dc77e7f0fe
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e6c72a54d596468e1ae6948ff9f177e026458628
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="transaction-activities-in-wf"></a><span data-ttu-id="d61e8-102">WF işlem etkinlikleri</span><span class="sxs-lookup"><span data-stu-id="d61e8-102">Transaction Activities in WF</span></span>
<span data-ttu-id="d61e8-103">[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] İşlemleri, maaş ve iptal modelleme için birkaç sistem tarafından sağlanan etkinlikler içeriyor.</span><span class="sxs-lookup"><span data-stu-id="d61e8-103">The [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] has several system-provided activities for modeling transactions, compensation, and cancellation.</span></span> <span data-ttu-id="d61e8-104">Bu programlama modellerine ilerleme durumunda değişiklikler iş mantığı ve hata işleme devam etmek iş akışı izin verir.</span><span class="sxs-lookup"><span data-stu-id="d61e8-104">These programming models allow the workflow to continue forward progress in the event of changes in business logic and error handling.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="d61e8-105">işlemleri, maaş ve iptal etme, bkz: [işlemleri](../../../docs/framework/windows-workflow-foundation/workflow-transactions.md), [maaş](../../../docs/framework/windows-workflow-foundation/compensation.md), ve [iptal](../../../docs/framework/windows-workflow-foundation/modeling-cancellation-behavior-in-workflows.md).</span><span class="sxs-lookup"><span data-stu-id="d61e8-105"> transactions, compensation, and cancellation, see [Transactions](../../../docs/framework/windows-workflow-foundation/workflow-transactions.md), [Compensation](../../../docs/framework/windows-workflow-foundation/compensation.md), and [Cancellation](../../../docs/framework/windows-workflow-foundation/modeling-cancellation-behavior-in-workflows.md).</span></span>  
  
## <a name="transaction-activities"></a><span data-ttu-id="d61e8-106">İşlem etkinlikleri</span><span class="sxs-lookup"><span data-stu-id="d61e8-106">Transaction Activities</span></span>  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.CancellationScope>|<span data-ttu-id="d61e8-107">Ana yol yürütme, ayrıca bir etkinlik olarak ifade edilen bir etkinlik biçiminde iptal mantığı ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="d61e8-107">Associates cancellation logic, in the form of an activity, with a main path of execution, also expressed as an activity.</span></span>|  
|<xref:System.Activities.Statements.CompensableActivity>|<span data-ttu-id="d61e8-108">Kendi alt etkinliklerin maaş destekler.</span><span class="sxs-lookup"><span data-stu-id="d61e8-108">Supports compensation of its child activities.</span></span>|  
|<xref:System.Activities.Statements.Compensate>|<span data-ttu-id="d61e8-109">Açıkça maaş işleyicisini çağıran bir <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="d61e8-109">Explicitly invokes the compensation handler of a <xref:System.Activities.Statements.CompensableActivity>.</span></span>|  
|<xref:System.Activities.Statements.Confirm>|<span data-ttu-id="d61e8-110">Açıkça, onay işleyiciyi çağırır bir <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="d61e8-110">Explicitly invokes the confirmation handler of a <xref:System.Activities.Statements.CompensableActivity>.</span></span>|  
|<xref:System.Activities.Statements.TransactionScope>|<span data-ttu-id="d61e8-111">Bir işlem sınır demarcates.</span><span class="sxs-lookup"><span data-stu-id="d61e8-111">Demarcates a transaction boundary.</span></span>|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope>|<span data-ttu-id="d61e8-112">Alınan ileti tarafından başlatılan bir işlem ömrü kapsamları.</span><span class="sxs-lookup"><span data-stu-id="d61e8-112">Scopes the lifetime of a transaction that is initiated by a received message.</span></span> <span data-ttu-id="d61e8-113">İşlem başlatma iletisi üzerinde iş akışına akışı yapılan işlem, veya olabilir iletisi alındığında gönderici tarafından oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="d61e8-113">The transaction may be flowed into the workflow on the initiating message, or created by the dispatcher when the message is received.</span></span> <span data-ttu-id="d61e8-114">**Not:** <xref:System.ServiceModel.Activities.TransactedReceiveScope> bulunan **ileti** bölümünü **araç**.</span><span class="sxs-lookup"><span data-stu-id="d61e8-114">**Note:**  The <xref:System.ServiceModel.Activities.TransactedReceiveScope> is located in the **Messaging** section of the **Toolbox**.</span></span>|
