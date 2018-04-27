---
title: Özelleştirme ekleme, güncelleştirme ve silme işlemleri
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 07eef055-8f6c-414d-850e-d323ff946cd0
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 410385d1689a9fd15a1399411f601e407d590830
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="customizing-insert-update-and-delete-operations"></a><span data-ttu-id="98976-102">Özelleştirme ekleme, güncelleştirme ve silme işlemleri</span><span class="sxs-lookup"><span data-stu-id="98976-102">Customizing Insert, Update, and Delete Operations</span></span>
<span data-ttu-id="98976-103">Varsayılan olarak, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] INSERT uygulamak, okuma, güncelleştirme ve silme işlemleri için dinamik SQL oluşturur.</span><span class="sxs-lookup"><span data-stu-id="98976-103">By default, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates dynamic SQL to implement insert, read, update, and delete operations.</span></span> <span data-ttu-id="98976-104">Uygulamada, ancak, genellikle uygulamanız, iş gereksinimlerinize uyacak şekilde özelleştirin.</span><span class="sxs-lookup"><span data-stu-id="98976-104">In practice, however, you typically customize your application to suit your business needs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="98976-105">Visual Studio kullanıyorsanız, kullanabileceğiniz [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] INSERT özelleştirmek için güncelleştirme ve silme eylemlerinin.</span><span class="sxs-lookup"><span data-stu-id="98976-105">If you are using Visual Studio, you can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to customize insert, update, and delete actions.</span></span>  
  
 <span data-ttu-id="98976-106">Konu bu bölümde teknikleri açıklar, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ekleme, okuma, güncelleştirme ve silme işlemleri, uygulamanızda özelleştirmek için sağlar.</span><span class="sxs-lookup"><span data-stu-id="98976-106">This section of topics describes the techniques that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides for customizing insert, read, update, and delete operations in your application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="98976-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="98976-107">In This Section</span></span>  
 [<span data-ttu-id="98976-108">İşlemleri Özelleştirme: Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="98976-108">Customizing Operations: Overview</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-overview.md)  
 <span data-ttu-id="98976-109">Çeşitli teknikleri açıklar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ekleme, okuma, güncelleştirme ve silme işlemleri özelleştirmek için sağlar.</span><span class="sxs-lookup"><span data-stu-id="98976-109">Describes the various techniques [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides for customizing insert, read, update, and delete operations.</span></span>  
  
 [<span data-ttu-id="98976-110">Insert, Update ve Delete İşlemleri</span><span class="sxs-lookup"><span data-stu-id="98976-110">Insert, Update, and Delete Operations</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/insert-update-and-delete-operations.md)  
 <span data-ttu-id="98976-111">Açıklar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] varsayılan veritabanı verileri işlemek için kullanılan işlemler.</span><span class="sxs-lookup"><span data-stu-id="98976-111">Describes the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default processes for manipulating database data.</span></span>  
  
 [<span data-ttu-id="98976-112">Geliştiricinin Varsayılan Davranışı Geçersiz Kılma Sorumlulukları</span><span class="sxs-lookup"><span data-stu-id="98976-112">Responsibilities of the Developer In Overriding Default Behavior</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)  
 <span data-ttu-id="98976-113">Geliştirici tarafından zorlanmazsa gereksinimleri uygulamaya rolü açıklanmaktadır [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="98976-113">Describes the role of the developer in implementing requirements not enforced by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="98976-114">Kısmi Yöntemler Kullanarak İş Mantığı Ekleme</span><span class="sxs-lookup"><span data-stu-id="98976-114">Adding Business Logic By Using Partial Methods</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)  
 <span data-ttu-id="98976-115">Kısmi yöntemler otomatik olarak oluşturulur yöntemleri geçersiz kılmak için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="98976-115">Describes how to use partial methods to override autogenerated methods.</span></span>
