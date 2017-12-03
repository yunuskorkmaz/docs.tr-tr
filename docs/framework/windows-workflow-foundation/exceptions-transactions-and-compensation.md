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
ms.openlocfilehash: 7fab7247540ba4e098a793adebab54ca4219e503
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="exceptions-transactions-and-compensation"></a><span data-ttu-id="d44be-102">Özel durumlar, işlemleri ve Dengeleme</span><span class="sxs-lookup"><span data-stu-id="d44be-102">Exceptions, Transactions, and Compensation</span></span>
[!INCLUDE[wf1](../../../includes/wf1-md.md)]<span data-ttu-id="d44be-103">iş akışlarında çalışma zamanı hata koşullarını işleme için birkaç farklı mekanizmaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="d44be-103"> provides several different mechanisms for handling run-time error conditions in workflows.</span></span> <span data-ttu-id="d44be-104">İş akışlarını işlemek ve düzgün bir şekilde hata koşulları kurtarmak için özel durum işleyicileri, işlemleri, iptal etme ve maaş bileşimini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d44be-104">Workflows can use a combination of exception handlers, transactions, cancellation, and compensation to handle and recover gracefully from error conditions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d44be-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="d44be-105">In This Section</span></span>  
 [<span data-ttu-id="d44be-106">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="d44be-106">Exceptions</span></span>](../../../docs/framework/windows-workflow-foundation/exceptions.md)  
 <span data-ttu-id="d44be-107">Nasıl kullanılacağı ortaya <xref:System.Activities.Statements.TryCatch> bir iş akışında özel durumları işleme etkinlik.</span><span class="sxs-lookup"><span data-stu-id="d44be-107">Demonstrates how to use the <xref:System.Activities.Statements.TryCatch> activity to handle exceptions in a workflow.</span></span>  
  
 [<span data-ttu-id="d44be-108">İşlemler</span><span class="sxs-lookup"><span data-stu-id="d44be-108">Transactions</span></span>](../../../docs/framework/windows-workflow-foundation/workflow-transactions.md)  
 <span data-ttu-id="d44be-109">Nasıl kullanılacağı ortaya <xref:System.Activities.Statements.TransactionScope> etkinliğini bir iş akışında işlemleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="d44be-109">Demonstrates how to use the <xref:System.Activities.Statements.TransactionScope> activity to use transactions in a workflow.</span></span>  
  
 [<span data-ttu-id="d44be-110">Maaş</span><span class="sxs-lookup"><span data-stu-id="d44be-110">Compensation</span></span>](../../../docs/framework/windows-workflow-foundation/compensation.md)  
 <span data-ttu-id="d44be-111">İş akışlarında maaş açıklar ve maaş etkinlikleri gibi kullanımı gösterilmiştir <xref:System.Activities.Statements.CompensableActivity>, <xref:System.Activities.Statements.Compensate>, ve <xref:System.Activities.Statements.Confirm>.</span><span class="sxs-lookup"><span data-stu-id="d44be-111">Describes compensation in workflows and demonstrates how to use compensation activities such as <xref:System.Activities.Statements.CompensableActivity>, <xref:System.Activities.Statements.Compensate>, and <xref:System.Activities.Statements.Confirm>.</span></span>  
  
 [<span data-ttu-id="d44be-112">İptal etme</span><span class="sxs-lookup"><span data-stu-id="d44be-112">Cancellation</span></span>](../../../docs/framework/windows-workflow-foundation/modeling-cancellation-behavior-in-workflows.md)  
 <span data-ttu-id="d44be-113">Özel etkinlikler yanı sıra yerleşik etkinlikler kullanan iş akışlarında işleme iptal gerçekleştirmeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="d44be-113">Describes how to perform cancellation handling in workflows using built-in activities as well as custom activities.</span></span>  
  
 [<span data-ttu-id="d44be-114">İş akışları hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="d44be-114">Debugging Workflows</span></span>](../../../docs/framework/windows-workflow-foundation/debugging-workflows.md)  
 <span data-ttu-id="d44be-115">İş akışları hata ayıklamak açıklar.</span><span class="sxs-lookup"><span data-stu-id="d44be-115">Describes how to debug workflows.</span></span>
