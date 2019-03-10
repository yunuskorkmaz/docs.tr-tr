---
title: İşlem WF etkinlikleri
ms.date: 03/30/2017
ms.assetid: fb33378e-82c6-4ea0-870f-76dc77e7f0fe
ms.openlocfilehash: 7ffd64abdc6edf45174d4b756833d65ec0ef747c
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57714781"
---
# <a name="transaction-activities-in-wf"></a><span data-ttu-id="03e1d-102">İşlem WF etkinlikleri</span><span class="sxs-lookup"><span data-stu-id="03e1d-102">Transaction Activities in WF</span></span>
<span data-ttu-id="03e1d-103">[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] İşlemler ve Dengeleme iptal modelleme için birçok sistem tarafından sağlanan etkinlikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="03e1d-103">The [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] has several system-provided activities for modeling transactions, compensation, and cancellation.</span></span> <span data-ttu-id="03e1d-104">Bu programlama modellerine ilerleme durumunda değişiklikler iş mantığı ve hata işleme devam etmek iş akışı sağlar.</span><span class="sxs-lookup"><span data-stu-id="03e1d-104">These programming models allow the workflow to continue forward progress in the event of changes in business logic and error handling.</span></span> <span data-ttu-id="03e1d-105">İşlemler ve Dengeleme iptal hakkında daha fazla bilgi için bkz: [işlemleri](workflow-transactions.md), [maaş](compensation.md), ve [iptal](modeling-cancellation-behavior-in-workflows.md).</span><span class="sxs-lookup"><span data-stu-id="03e1d-105">For more information about transactions, compensation, and cancellation, see [Transactions](workflow-transactions.md), [Compensation](compensation.md), and [Cancellation](modeling-cancellation-behavior-in-workflows.md).</span></span>  
  
## <a name="transaction-activities"></a><span data-ttu-id="03e1d-106">İşlem etkinlikleri</span><span class="sxs-lookup"><span data-stu-id="03e1d-106">Transaction Activities</span></span>  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.CancellationScope>|<span data-ttu-id="03e1d-107">Yürütme, ayrıca bir etkinlik ifade edilen bir ana yol biçiminde bir etkinlik iptal etme mantığı ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="03e1d-107">Associates cancellation logic, in the form of an activity, with a main path of execution, also expressed as an activity.</span></span>|  
|<xref:System.Activities.Statements.CompensableActivity>|<span data-ttu-id="03e1d-108">Alt etkinliklerinin maaş destekler.</span><span class="sxs-lookup"><span data-stu-id="03e1d-108">Supports compensation of its child activities.</span></span>|  
|<xref:System.Activities.Statements.Compensate>|<span data-ttu-id="03e1d-109">Açıkça'nin Dengeleme işleyicisini çağırır bir <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="03e1d-109">Explicitly invokes the compensation handler of a <xref:System.Activities.Statements.CompensableActivity>.</span></span>|  
|<xref:System.Activities.Statements.Confirm>|<span data-ttu-id="03e1d-110">Açıkça nin Dengeleme işleyicisini çağırır bir <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="03e1d-110">Explicitly invokes the confirmation handler of a <xref:System.Activities.Statements.CompensableActivity>.</span></span>|  
|<xref:System.Activities.Statements.TransactionScope>|<span data-ttu-id="03e1d-111">Bir işlem sınırı demarcates.</span><span class="sxs-lookup"><span data-stu-id="03e1d-111">Demarcates a transaction boundary.</span></span>|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope>|<span data-ttu-id="03e1d-112">Kapsamları ömrünü bir alınan ileti tarafından başlatılan bir işlem.</span><span class="sxs-lookup"><span data-stu-id="03e1d-112">Scopes the lifetime of a transaction that is initiated by a received message.</span></span> <span data-ttu-id="03e1d-113">İşlem iş akışı başlatma iletisi içine aktarılan, veya olabilir iletisi alındığında gönderici tarafından oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="03e1d-113">The transaction may be flowed into the workflow on the initiating message, or created by the dispatcher when the message is received.</span></span> <span data-ttu-id="03e1d-114">**Not:**  <xref:System.ServiceModel.Activities.TransactedReceiveScope> Bulunan **Mesajlaşma** bölümünü **araç kutusu**.</span><span class="sxs-lookup"><span data-stu-id="03e1d-114">**Note:**  The <xref:System.ServiceModel.Activities.TransactedReceiveScope> is located in the **Messaging** section of the **Toolbox**.</span></span>|
