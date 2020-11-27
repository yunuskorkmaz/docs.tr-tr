---
title: Özel Durumlar, İşlemler ve Dengeleme
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], error handling
ms.assetid: 694db4f9-7387-4b13-8f9f-b923b18c7490
ms.openlocfilehash: 2d8574c0f0f6bd3f66214367c1ed15292adc24a9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96280253"
---
# <a name="exceptions-transactions-and-compensation"></a><span data-ttu-id="db2b0-102">Özel Durumlar, İşlemler ve Dengeleme</span><span class="sxs-lookup"><span data-stu-id="db2b0-102">Exceptions, Transactions, and Compensation</span></span>

[!INCLUDE[wf1](../../../includes/wf1-md.md)] <span data-ttu-id="db2b0-103">iş akışlarında çalışma zamanı hata koşullarını işlemek için birkaç farklı mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="db2b0-103">provides several different mechanisms for handling run-time error conditions in workflows.</span></span> <span data-ttu-id="db2b0-104">İş akışları, hata koşullarından sorunsuz bir şekilde işleme ve kurtarmaya yönelik özel durum işleyicileri, işlemler, iptal ve dengeleme birleşimini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="db2b0-104">Workflows can use a combination of exception handlers, transactions, cancellation, and compensation to handle and recover gracefully from error conditions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="db2b0-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="db2b0-105">In This Section</span></span>  

 [<span data-ttu-id="db2b0-106">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="db2b0-106">Exceptions</span></span>](exceptions.md)  
 <span data-ttu-id="db2b0-107"><xref:System.Activities.Statements.TryCatch>Bir iş akışındaki özel durumları işlemek için etkinliğin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="db2b0-107">Demonstrates how to use the <xref:System.Activities.Statements.TryCatch> activity to handle exceptions in a workflow.</span></span>  
  
 [<span data-ttu-id="db2b0-108">İşlemler</span><span class="sxs-lookup"><span data-stu-id="db2b0-108">Transactions</span></span>](workflow-transactions.md)  
 <span data-ttu-id="db2b0-109"><xref:System.Activities.Statements.TransactionScope>Bir iş akışındaki işlemleri kullanmak için etkinliğin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="db2b0-109">Demonstrates how to use the <xref:System.Activities.Statements.TransactionScope> activity to use transactions in a workflow.</span></span>  
  
 [<span data-ttu-id="db2b0-110">Dengeleme</span><span class="sxs-lookup"><span data-stu-id="db2b0-110">Compensation</span></span>](compensation.md)  
 <span data-ttu-id="db2b0-111">İş akışlarında dengelemeyi açıklar ve, ve gibi maaş etkinliklerinin nasıl kullanılacağını gösterir <xref:System.Activities.Statements.CompensableActivity> <xref:System.Activities.Statements.Compensate> <xref:System.Activities.Statements.Confirm> .</span><span class="sxs-lookup"><span data-stu-id="db2b0-111">Describes compensation in workflows and demonstrates how to use compensation activities such as <xref:System.Activities.Statements.CompensableActivity>, <xref:System.Activities.Statements.Compensate>, and <xref:System.Activities.Statements.Confirm>.</span></span>  
  
 [<span data-ttu-id="db2b0-112">İptal Etme</span><span class="sxs-lookup"><span data-stu-id="db2b0-112">Cancellation</span></span>](modeling-cancellation-behavior-in-workflows.md)  
 <span data-ttu-id="db2b0-113">Yerleşik etkinliklerin yanı sıra özel etkinlikler kullanılarak iş akışlarında iptal işlemenin nasıl gerçekleştirileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="db2b0-113">Describes how to perform cancellation handling in workflows using built-in activities as well as custom activities.</span></span>  
  
 [<span data-ttu-id="db2b0-114">İş Akışlarında Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="db2b0-114">Debugging Workflows</span></span>](debugging-workflows.md)  
 <span data-ttu-id="db2b0-115">İş akışlarının hatalarını ayıklama işlemini açıklar.</span><span class="sxs-lookup"><span data-stu-id="db2b0-115">Describes how to debug workflows.</span></span>
