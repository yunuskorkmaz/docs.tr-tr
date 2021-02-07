---
description: 'Daha fazla bilgi edinin: özel durumlar, Işlemler ve Dengeleme'
title: Özel Durumlar, İşlemler ve Dengeleme
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], error handling
ms.assetid: 694db4f9-7387-4b13-8f9f-b923b18c7490
ms.openlocfilehash: 3188b0238b1909847c289bb56274671ff4b307b4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99720195"
---
# <a name="exceptions-transactions-and-compensation"></a><span data-ttu-id="ddaaa-103">Özel Durumlar, İşlemler ve Dengeleme</span><span class="sxs-lookup"><span data-stu-id="ddaaa-103">Exceptions, Transactions, and Compensation</span></span>

[!INCLUDE[wf1](../../../includes/wf1-md.md)] <span data-ttu-id="ddaaa-104">iş akışlarında çalışma zamanı hata koşullarını işlemek için birkaç farklı mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="ddaaa-104">provides several different mechanisms for handling run-time error conditions in workflows.</span></span> <span data-ttu-id="ddaaa-105">İş akışları, hata koşullarından sorunsuz bir şekilde işleme ve kurtarmaya yönelik özel durum işleyicileri, işlemler, iptal ve dengeleme birleşimini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="ddaaa-105">Workflows can use a combination of exception handlers, transactions, cancellation, and compensation to handle and recover gracefully from error conditions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ddaaa-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="ddaaa-106">In This Section</span></span>  

 [<span data-ttu-id="ddaaa-107">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="ddaaa-107">Exceptions</span></span>](exceptions.md)  
 <span data-ttu-id="ddaaa-108"><xref:System.Activities.Statements.TryCatch>Bir iş akışındaki özel durumları işlemek için etkinliğin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ddaaa-108">Demonstrates how to use the <xref:System.Activities.Statements.TryCatch> activity to handle exceptions in a workflow.</span></span>  
  
 [<span data-ttu-id="ddaaa-109">İşlemler</span><span class="sxs-lookup"><span data-stu-id="ddaaa-109">Transactions</span></span>](workflow-transactions.md)  
 <span data-ttu-id="ddaaa-110"><xref:System.Activities.Statements.TransactionScope>Bir iş akışındaki işlemleri kullanmak için etkinliğin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ddaaa-110">Demonstrates how to use the <xref:System.Activities.Statements.TransactionScope> activity to use transactions in a workflow.</span></span>  
  
 [<span data-ttu-id="ddaaa-111">Dengeleme</span><span class="sxs-lookup"><span data-stu-id="ddaaa-111">Compensation</span></span>](compensation.md)  
 <span data-ttu-id="ddaaa-112">İş akışlarında dengelemeyi açıklar ve, ve gibi maaş etkinliklerinin nasıl kullanılacağını gösterir <xref:System.Activities.Statements.CompensableActivity> <xref:System.Activities.Statements.Compensate> <xref:System.Activities.Statements.Confirm> .</span><span class="sxs-lookup"><span data-stu-id="ddaaa-112">Describes compensation in workflows and demonstrates how to use compensation activities such as <xref:System.Activities.Statements.CompensableActivity>, <xref:System.Activities.Statements.Compensate>, and <xref:System.Activities.Statements.Confirm>.</span></span>  
  
 [<span data-ttu-id="ddaaa-113">İptal</span><span class="sxs-lookup"><span data-stu-id="ddaaa-113">Cancellation</span></span>](modeling-cancellation-behavior-in-workflows.md)  
 <span data-ttu-id="ddaaa-114">Yerleşik etkinliklerin yanı sıra özel etkinlikler kullanılarak iş akışlarında iptal işlemenin nasıl gerçekleştirileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="ddaaa-114">Describes how to perform cancellation handling in workflows using built-in activities as well as custom activities.</span></span>  
  
 [<span data-ttu-id="ddaaa-115">İş Akışlarında Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="ddaaa-115">Debugging Workflows</span></span>](debugging-workflows.md)  
 <span data-ttu-id="ddaaa-116">İş akışlarının hatalarını ayıklama işlemini açıklar.</span><span class="sxs-lookup"><span data-stu-id="ddaaa-116">Describes how to debug workflows.</span></span>
