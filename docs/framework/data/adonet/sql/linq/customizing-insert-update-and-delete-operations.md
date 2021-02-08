---
description: 'Daha fazla bilgi edinin: ekleme, güncelleştirme ve silme Işlemlerini özelleştirme'
title: Insert, Update ve Delete İşlemlerini Özelleştirme
ms.date: 03/30/2017
ms.assetid: 07eef055-8f6c-414d-850e-d323ff946cd0
ms.openlocfilehash: 44bd76b61aff335019818b3c61040d10babe7301
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99773218"
---
# <a name="customizing-insert-update-and-delete-operations"></a><span data-ttu-id="57d2c-103">Insert, Update ve Delete İşlemlerini Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="57d2c-103">Customizing Insert, Update, and Delete Operations</span></span>

<span data-ttu-id="57d2c-104">Varsayılan olarak, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Insert, Read, Update ve DELETE işlemlerini uygulamak için dınamık SQL oluşturur.</span><span class="sxs-lookup"><span data-stu-id="57d2c-104">By default, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates dynamic SQL to implement insert, read, update, and delete operations.</span></span> <span data-ttu-id="57d2c-105">Ancak uygulamada, genellikle uygulamanızı iş gereksinimlerinize uyacak şekilde özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="57d2c-105">In practice, however, you typically customize your application to suit your business needs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="57d2c-106">Visual Studio kullanıyorsanız ekleme, güncelleştirme ve silme eylemlerini özelleştirmek için Nesne İlişkisel Tasarımcısı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="57d2c-106">If you are using Visual Studio, you can use the Object Relational Designer to customize insert, update, and delete actions.</span></span>  
  
 <span data-ttu-id="57d2c-107">Konuların bu bölümünde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , uygulamanızda ekleme, okuma, güncelleştirme ve silme işlemlerini özelleştirmek için sağlanan teknikler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="57d2c-107">This section of topics describes the techniques that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides for customizing insert, read, update, and delete operations in your application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="57d2c-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="57d2c-108">In This Section</span></span>  

 [<span data-ttu-id="57d2c-109">İşlemleri Özelleştirme: Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="57d2c-109">Customizing Operations: Overview</span></span>](customizing-operations-overview.md)  
 <span data-ttu-id="57d2c-110">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Ekleme, okuma, güncelleştirme ve silme işlemlerini özelleştirmek için çeşitli tekniklerin sağladığı açıklanır.</span><span class="sxs-lookup"><span data-stu-id="57d2c-110">Describes the various techniques [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides for customizing insert, read, update, and delete operations.</span></span>  
  
 [<span data-ttu-id="57d2c-111">Insert, Update ve Delete İşlemleri</span><span class="sxs-lookup"><span data-stu-id="57d2c-111">Insert, Update, and Delete Operations</span></span>](insert-update-and-delete-operations.md)  
 <span data-ttu-id="57d2c-112">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Veritabanı verilerini işlemek için varsayılan süreçler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="57d2c-112">Describes the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default processes for manipulating database data.</span></span>  
  
 [<span data-ttu-id="57d2c-113">Geliştiricinin Varsayılan Davranışı Geçersiz Kılma Sorumlulukları</span><span class="sxs-lookup"><span data-stu-id="57d2c-113">Responsibilities of the Developer In Overriding Default Behavior</span></span>](responsibilities-of-the-developer-in-overriding-default-behavior.md)  
 <span data-ttu-id="57d2c-114">Tarafından zorlanmayan gereksinimleri uygulamak için geliştiricinin rolünü açıklar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="57d2c-114">Describes the role of the developer in implementing requirements not enforced by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="57d2c-115">Kısmi Yöntemler Kullanarak İş Mantığı Ekleme</span><span class="sxs-lookup"><span data-stu-id="57d2c-115">Adding Business Logic By Using Partial Methods</span></span>](adding-business-logic-by-using-partial-methods.md)  
 <span data-ttu-id="57d2c-116">Kısmi yöntemlerin, otomatik olarak oluşturulan yöntemleri geçersiz kılmak için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="57d2c-116">Describes how to use partial methods to override autogenerated methods.</span></span>
