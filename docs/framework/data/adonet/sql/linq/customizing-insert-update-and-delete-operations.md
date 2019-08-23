---
title: Insert, Update ve Delete İşlemlerini Özelleştirme
ms.date: 03/30/2017
ms.assetid: 07eef055-8f6c-414d-850e-d323ff946cd0
ms.openlocfilehash: f75f4b4caf6b72076a83bde2f2c659aab4c9707d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912573"
---
# <a name="customizing-insert-update-and-delete-operations"></a><span data-ttu-id="7bc42-102">Insert, Update ve Delete İşlemlerini Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="7bc42-102">Customizing Insert, Update, and Delete Operations</span></span>
<span data-ttu-id="7bc42-103">Varsayılan olarak, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] INSERT, Read, Update ve DELETE işlemlerini uygulamak için dinamik SQL oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7bc42-103">By default, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates dynamic SQL to implement insert, read, update, and delete operations.</span></span> <span data-ttu-id="7bc42-104">Ancak uygulamada, genellikle uygulamanızı iş gereksinimlerinize uyacak şekilde özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7bc42-104">In practice, however, you typically customize your application to suit your business needs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7bc42-105">Visual Studio kullanıyorsanız ekleme, güncelleştirme ve silme eylemlerini özelleştirmek için Nesne İlişkisel Tasarımcısı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7bc42-105">If you are using Visual Studio, you can use the Object Relational Designer to customize insert, update, and delete actions.</span></span>  
  
 <span data-ttu-id="7bc42-106">Konuların bu bölümünde, uygulamanızda ekleme, okuma [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , güncelleştirme ve silme işlemlerini özelleştirmek için sağlanan teknikler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7bc42-106">This section of topics describes the techniques that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides for customizing insert, read, update, and delete operations in your application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7bc42-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="7bc42-107">In This Section</span></span>  
 [<span data-ttu-id="7bc42-108">Işlemleri özelleştirme: Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7bc42-108">Customizing Operations: Overview</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-overview.md)  
 <span data-ttu-id="7bc42-109">Ekleme, okuma, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] güncelleştirme ve silme işlemlerini özelleştirmek için çeşitli tekniklerin sağladığı açıklanır.</span><span class="sxs-lookup"><span data-stu-id="7bc42-109">Describes the various techniques [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides for customizing insert, read, update, and delete operations.</span></span>  
  
 [<span data-ttu-id="7bc42-110">Insert, Update ve Delete İşlemleri</span><span class="sxs-lookup"><span data-stu-id="7bc42-110">Insert, Update, and Delete Operations</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/insert-update-and-delete-operations.md)  
 <span data-ttu-id="7bc42-111">Veritabanı verilerini işlemek için varsayılansüreçleraçıklanmaktadır.[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bc42-111">Describes the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default processes for manipulating database data.</span></span>  
  
 [<span data-ttu-id="7bc42-112">Geliştiricinin Varsayılan Davranışı Geçersiz Kılma Sorumlulukları</span><span class="sxs-lookup"><span data-stu-id="7bc42-112">Responsibilities of the Developer In Overriding Default Behavior</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)  
 <span data-ttu-id="7bc42-113">Tarafından [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]zorlanmayan gereksinimleri uygulamak için geliştiricinin rolünü açıklar.</span><span class="sxs-lookup"><span data-stu-id="7bc42-113">Describes the role of the developer in implementing requirements not enforced by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="7bc42-114">Kısmi Yöntemler Kullanarak İş Mantığı Ekleme</span><span class="sxs-lookup"><span data-stu-id="7bc42-114">Adding Business Logic By Using Partial Methods</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)  
 <span data-ttu-id="7bc42-115">Kısmi yöntemlerin, otomatik olarak oluşturulan yöntemleri geçersiz kılmak için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="7bc42-115">Describes how to use partial methods to override autogenerated methods.</span></span>
