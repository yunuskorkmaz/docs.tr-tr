---
title: "Özel durumlar, işlemleri ve Dengeleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: programming [WF], error handling
ms.assetid: 694db4f9-7387-4b13-8f9f-b923b18c7490
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e83661ba66ca6a71f26c11172902d5bc602a2f6e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="exceptions-transactions-and-compensation"></a><span data-ttu-id="3bdd4-102">Özel durumlar, işlemleri ve Dengeleme</span><span class="sxs-lookup"><span data-stu-id="3bdd4-102">Exceptions, Transactions, and Compensation</span></span>
[!INCLUDE[wf1](../../../includes/wf1-md.md)]<span data-ttu-id="3bdd4-103">iş akışlarında çalışma zamanı hata koşullarını işleme için birkaç farklı mekanizmaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="3bdd4-103"> provides several different mechanisms for handling run-time error conditions in workflows.</span></span> <span data-ttu-id="3bdd4-104">İş akışlarını işlemek ve düzgün bir şekilde hata koşulları kurtarmak için özel durum işleyicileri, işlemleri, iptal etme ve maaş bileşimini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3bdd4-104">Workflows can use a combination of exception handlers, transactions, cancellation, and compensation to handle and recover gracefully from error conditions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3bdd4-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="3bdd4-105">In This Section</span></span>  
 [<span data-ttu-id="3bdd4-106">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="3bdd4-106">Exceptions</span></span>](../../../docs/framework/windows-workflow-foundation/exceptions.md)  
 <span data-ttu-id="3bdd4-107">Nasıl kullanılacağı ortaya <xref:System.Activities.Statements.TryCatch> bir iş akışında özel durumları işleme etkinlik.</span><span class="sxs-lookup"><span data-stu-id="3bdd4-107">Demonstrates how to use the <xref:System.Activities.Statements.TryCatch> activity to handle exceptions in a workflow.</span></span>  
  
 [<span data-ttu-id="3bdd4-108">İşlemler</span><span class="sxs-lookup"><span data-stu-id="3bdd4-108">Transactions</span></span>](../../../docs/framework/windows-workflow-foundation/workflow-transactions.md)  
 <span data-ttu-id="3bdd4-109">Nasıl kullanılacağı ortaya <xref:System.Activities.Statements.TransactionScope> etkinliğini bir iş akışında işlemleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="3bdd4-109">Demonstrates how to use the <xref:System.Activities.Statements.TransactionScope> activity to use transactions in a workflow.</span></span>  
  
 [<span data-ttu-id="3bdd4-110">Dengeleme</span><span class="sxs-lookup"><span data-stu-id="3bdd4-110">Compensation</span></span>](../../../docs/framework/windows-workflow-foundation/compensation.md)  
 <span data-ttu-id="3bdd4-111">İş akışlarında maaş açıklar ve maaş etkinlikleri gibi kullanımı gösterilmiştir <xref:System.Activities.Statements.CompensableActivity>, <xref:System.Activities.Statements.Compensate>, ve <xref:System.Activities.Statements.Confirm>.</span><span class="sxs-lookup"><span data-stu-id="3bdd4-111">Describes compensation in workflows and demonstrates how to use compensation activities such as <xref:System.Activities.Statements.CompensableActivity>, <xref:System.Activities.Statements.Compensate>, and <xref:System.Activities.Statements.Confirm>.</span></span>  
  
 [<span data-ttu-id="3bdd4-112">İptal</span><span class="sxs-lookup"><span data-stu-id="3bdd4-112">Cancellation</span></span>](../../../docs/framework/windows-workflow-foundation/modeling-cancellation-behavior-in-workflows.md)  
 <span data-ttu-id="3bdd4-113">Özel etkinlikler yanı sıra yerleşik etkinlikler kullanan iş akışlarında işleme iptal gerçekleştirmeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="3bdd4-113">Describes how to perform cancellation handling in workflows using built-in activities as well as custom activities.</span></span>  
  
 [<span data-ttu-id="3bdd4-114">İş Akışlarında Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="3bdd4-114">Debugging Workflows</span></span>](../../../docs/framework/windows-workflow-foundation/debugging-workflows.md)  
 <span data-ttu-id="3bdd4-115">İş akışları hata ayıklamak açıklar.</span><span class="sxs-lookup"><span data-stu-id="3bdd4-115">Describes how to debug workflows.</span></span>
