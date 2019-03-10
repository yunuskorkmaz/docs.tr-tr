---
title: Özel durumlar, işlemler ve Dengeleme
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], error handling
ms.assetid: 694db4f9-7387-4b13-8f9f-b923b18c7490
ms.openlocfilehash: c4d66e252561ad7b896ff8092e80013c51bd463c
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57709477"
---
# <a name="exceptions-transactions-and-compensation"></a><span data-ttu-id="7e372-102">Özel durumlar, işlemler ve Dengeleme</span><span class="sxs-lookup"><span data-stu-id="7e372-102">Exceptions, Transactions, and Compensation</span></span>
[!INCLUDE[wf1](../../../includes/wf1-md.md)] <span data-ttu-id="7e372-103">iş akışlarında çalışma zamanı hata koşullarını işleme için birkaç farklı mekanizmaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="7e372-103">provides several different mechanisms for handling run-time error conditions in workflows.</span></span> <span data-ttu-id="7e372-104">İş akışları işlemek ve düzgün bir şekilde hata koşulları kurtarmak için bir özel durum işleyicileri, işlemler, iptal ve maaş birleşimini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7e372-104">Workflows can use a combination of exception handlers, transactions, cancellation, and compensation to handle and recover gracefully from error conditions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7e372-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="7e372-105">In This Section</span></span>  
 [<span data-ttu-id="7e372-106">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="7e372-106">Exceptions</span></span>](exceptions.md)  
 <span data-ttu-id="7e372-107">Nasıl kullanılacağını gösteren <xref:System.Activities.Statements.TryCatch> bir iş akışında özel durumları işlemek için etkinlik.</span><span class="sxs-lookup"><span data-stu-id="7e372-107">Demonstrates how to use the <xref:System.Activities.Statements.TryCatch> activity to handle exceptions in a workflow.</span></span>  
  
 [<span data-ttu-id="7e372-108">İşlemler</span><span class="sxs-lookup"><span data-stu-id="7e372-108">Transactions</span></span>](workflow-transactions.md)  
 <span data-ttu-id="7e372-109">Nasıl kullanılacağını gösteren <xref:System.Activities.Statements.TransactionScope> etkinliğini bir iş akışında hareketlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="7e372-109">Demonstrates how to use the <xref:System.Activities.Statements.TransactionScope> activity to use transactions in a workflow.</span></span>  
  
 [<span data-ttu-id="7e372-110">Dengeleme</span><span class="sxs-lookup"><span data-stu-id="7e372-110">Compensation</span></span>](compensation.md)  
 <span data-ttu-id="7e372-111">İş akışlarında maaş açıklar ve maaş etkinlikleri gibi nasıl yapılacağı açıklanır <xref:System.Activities.Statements.CompensableActivity>, <xref:System.Activities.Statements.Compensate>, ve <xref:System.Activities.Statements.Confirm>.</span><span class="sxs-lookup"><span data-stu-id="7e372-111">Describes compensation in workflows and demonstrates how to use compensation activities such as <xref:System.Activities.Statements.CompensableActivity>, <xref:System.Activities.Statements.Compensate>, and <xref:System.Activities.Statements.Confirm>.</span></span>  
  
 [<span data-ttu-id="7e372-112">İptal</span><span class="sxs-lookup"><span data-stu-id="7e372-112">Cancellation</span></span>](modeling-cancellation-behavior-in-workflows.md)  
 <span data-ttu-id="7e372-113">Yerleşik etkinlikler, hem de özel etkinlikler kullanma akışlarında işleme iptal yerine getirilmesi anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7e372-113">Describes how to perform cancellation handling in workflows using built-in activities as well as custom activities.</span></span>  
  
 [<span data-ttu-id="7e372-114">İş Akışlarında Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="7e372-114">Debugging Workflows</span></span>](debugging-workflows.md)  
 <span data-ttu-id="7e372-115">İş akışlarında hata ayıklamak açıklar.</span><span class="sxs-lookup"><span data-stu-id="7e372-115">Describes how to debug workflows.</span></span>
