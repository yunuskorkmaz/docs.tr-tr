---
title: Insert, Update ve Delete İşlemlerini Özelleştirme
ms.date: 03/30/2017
ms.assetid: 07eef055-8f6c-414d-850e-d323ff946cd0
ms.openlocfilehash: 114447fd45806e567b4fde8e9e74138c096bff07
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743562"
---
# <a name="customizing-insert-update-and-delete-operations"></a><span data-ttu-id="cfac0-102">Insert, Update ve Delete İşlemlerini Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="cfac0-102">Customizing Insert, Update, and Delete Operations</span></span>
<span data-ttu-id="cfac0-103">Varsayılan olarak, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uygulamak ekleme, okuma, güncelleştirme ve silme işlemleri için dinamik SQL oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cfac0-103">By default, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates dynamic SQL to implement insert, read, update, and delete operations.</span></span> <span data-ttu-id="cfac0-104">Uygulamada, Bununla birlikte, genellikle iş ihtiyaçlarınıza uygun şekilde uygulamanızı özelleştirin.</span><span class="sxs-lookup"><span data-stu-id="cfac0-104">In practice, however, you typically customize your application to suit your business needs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cfac0-105">Visual Studio kullanıyorsanız, Object Relational Designer INSERT özelleştirmek için kullanabileceğiniz güncelleştirme ve silme eylemlerini.</span><span class="sxs-lookup"><span data-stu-id="cfac0-105">If you are using Visual Studio, you can use the Object Relational Designer to customize insert, update, and delete actions.</span></span>  
  
 <span data-ttu-id="cfac0-106">Bu bölümde konu teknikleri açıklar, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ekleme, okuma, güncelleştirme ve silme işlemleri, uygulamanızda özelleştirmek için sağlar.</span><span class="sxs-lookup"><span data-stu-id="cfac0-106">This section of topics describes the techniques that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides for customizing insert, read, update, and delete operations in your application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cfac0-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="cfac0-107">In This Section</span></span>  
 [<span data-ttu-id="cfac0-108">İşlemleri özelleştirme: Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="cfac0-108">Customizing Operations: Overview</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-overview.md)  
 <span data-ttu-id="cfac0-109">Çeşitli teknikler açıklanır [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ekleme, okuma, güncelleştirme ve silme işlemleri özelleştirmek için sağlar.</span><span class="sxs-lookup"><span data-stu-id="cfac0-109">Describes the various techniques [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides for customizing insert, read, update, and delete operations.</span></span>  
  
 [<span data-ttu-id="cfac0-110">Insert, Update ve Delete İşlemleri</span><span class="sxs-lookup"><span data-stu-id="cfac0-110">Insert, Update, and Delete Operations</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/insert-update-and-delete-operations.md)  
 <span data-ttu-id="cfac0-111">Açıklar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] varsayılan veritabanı verileri işlemek için kullanılan işlemler.</span><span class="sxs-lookup"><span data-stu-id="cfac0-111">Describes the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default processes for manipulating database data.</span></span>  
  
 [<span data-ttu-id="cfac0-112">Geliştiricinin Varsayılan Davranışı Geçersiz Kılma Sorumlulukları</span><span class="sxs-lookup"><span data-stu-id="cfac0-112">Responsibilities of the Developer In Overriding Default Behavior</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)  
 <span data-ttu-id="cfac0-113">Uygulama tarafından zorlanan değil gereksinimleri de Geliştirici rolünü açıklar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cfac0-113">Describes the role of the developer in implementing requirements not enforced by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="cfac0-114">Kısmi Yöntemler Kullanarak İş Mantığı Ekleme</span><span class="sxs-lookup"><span data-stu-id="cfac0-114">Adding Business Logic By Using Partial Methods</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)  
 <span data-ttu-id="cfac0-115">Otomatik olarak oluşturulan yöntemleri geçersiz kılmak için kısmi yöntemler kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="cfac0-115">Describes how to use partial methods to override autogenerated methods.</span></span>
