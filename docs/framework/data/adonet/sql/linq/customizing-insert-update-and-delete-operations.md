---
title: "Özelleştirme ekleme, güncelleştirme ve silme işlemleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 07eef055-8f6c-414d-850e-d323ff946cd0
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e48ac307087d5b90567c720d0c215ac0d52ccb6b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="customizing-insert-update-and-delete-operations"></a><span data-ttu-id="e6abf-102">Özelleştirme ekleme, güncelleştirme ve silme işlemleri</span><span class="sxs-lookup"><span data-stu-id="e6abf-102">Customizing Insert, Update, and Delete Operations</span></span>
<span data-ttu-id="e6abf-103">Varsayılan olarak, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] INSERT uygulamak, okuma, güncelleştirme ve silme işlemleri için dinamik SQL oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e6abf-103">By default, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates dynamic SQL to implement insert, read, update, and delete operations.</span></span> <span data-ttu-id="e6abf-104">Uygulamada, ancak, genellikle uygulamanız, iş gereksinimlerinize uyacak şekilde özelleştirin.</span><span class="sxs-lookup"><span data-stu-id="e6abf-104">In practice, however, you typically customize your application to suit your business needs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e6abf-105">Kullanıyorsanız [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], kullanabileceğiniz [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] INSERT özelleştirmek için güncelleştirme ve silme eylemlerinin.</span><span class="sxs-lookup"><span data-stu-id="e6abf-105">If you are using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], you can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to customize insert, update, and delete actions.</span></span>  
  
 <span data-ttu-id="e6abf-106">Konu bu bölümde teknikleri açıklar, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ekleme, okuma, güncelleştirme ve silme işlemleri, uygulamanızda özelleştirmek için sağlar.</span><span class="sxs-lookup"><span data-stu-id="e6abf-106">This section of topics describes the techniques that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides for customizing insert, read, update, and delete operations in your application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e6abf-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="e6abf-107">In This Section</span></span>  
 [<span data-ttu-id="e6abf-108">İşlem özelleştirme: genel bakış</span><span class="sxs-lookup"><span data-stu-id="e6abf-108">Customizing Operations: Overview</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-overview.md)  
 <span data-ttu-id="e6abf-109">Çeşitli teknikleri açıklar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ekleme, okuma, güncelleştirme ve silme işlemleri özelleştirmek için sağlar.</span><span class="sxs-lookup"><span data-stu-id="e6abf-109">Describes the various techniques [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides for customizing insert, read, update, and delete operations.</span></span>  
  
 [<span data-ttu-id="e6abf-110">INSERT, Update ve silme işlemleri</span><span class="sxs-lookup"><span data-stu-id="e6abf-110">Insert, Update, and Delete Operations</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/insert-update-and-delete-operations.md)  
 <span data-ttu-id="e6abf-111">Açıklar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] varsayılan veritabanı verileri işlemek için kullanılan işlemler.</span><span class="sxs-lookup"><span data-stu-id="e6abf-111">Describes the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default processes for manipulating database data.</span></span>  
  
 [<span data-ttu-id="e6abf-112">Varsayılan davranışı geçersiz kılma, geliştirici sorumlulukları</span><span class="sxs-lookup"><span data-stu-id="e6abf-112">Responsibilities of the Developer In Overriding Default Behavior</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)  
 <span data-ttu-id="e6abf-113">Geliştirici tarafından zorlanmazsa gereksinimleri uygulamaya rolü açıklanmaktadır [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e6abf-113">Describes the role of the developer in implementing requirements not enforced by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="e6abf-114">Kısmi yöntemler kullanarak iş mantığı ekleme</span><span class="sxs-lookup"><span data-stu-id="e6abf-114">Adding Business Logic By Using Partial Methods</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)  
 <span data-ttu-id="e6abf-115">Kısmi yöntemler otomatik olarak oluşturulur yöntemleri geçersiz kılmak için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="e6abf-115">Describes how to use partial methods to override autogenerated methods.</span></span>
