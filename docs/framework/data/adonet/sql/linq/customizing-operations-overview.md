---
title: 'İşlemleri Özelleştirme: Genel Bakış'
ms.date: 03/30/2017
ms.assetid: a3546296-1443-4b88-aa6e-d41011041ba7
ms.openlocfilehash: 48116887471709c60c9666f68c7ebdd0e6d128a1
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70247525"
---
# <a name="customizing-operations-overview"></a><span data-ttu-id="aef10-102">İşlemleri Özelleştirme: Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="aef10-102">Customizing Operations: Overview</span></span>
<span data-ttu-id="aef10-103">Varsayılan olarak, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] eşlemeye göre INSERT, Update ve DELETE işlemleri için dinamik SQL oluşturur.</span><span class="sxs-lookup"><span data-stu-id="aef10-103">By default, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates dynamic SQL for insert, update, and delete operations based on mapping.</span></span> <span data-ttu-id="aef10-104">Bununla birlikte, pratikte güvenlik, doğrulama ve benzerlerini sağlamak üzere kendi iş mantığınızı eklemek istersiniz.</span><span class="sxs-lookup"><span data-stu-id="aef10-104">However, in practice you typically want to add your own business logic to provide for security, validation, and so forth.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="aef10-105">Bu işlemleri özelleştirmeye yönelik teknikler şunlardır.</span><span class="sxs-lookup"><span data-stu-id="aef10-105">techniques for customizing these operations include the following.</span></span>  
  
## <a name="loading-options"></a><span data-ttu-id="aef10-106">Yükleme seçenekleri</span><span class="sxs-lookup"><span data-stu-id="aef10-106">Loading Options</span></span>  
 <span data-ttu-id="aef10-107">Sorgularda, veritabanına bağlandığınızda ana Hedefinizdeki ilgili verilerin ne kadarının alındığını denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aef10-107">In your queries, you can control how much data related to your main target is retrieved when you connect to the database.</span></span> <span data-ttu-id="aef10-108">Bu işlevsellik büyük ölçüde kullanılarak <xref:System.Data.Linq.DataLoadOptions>uygulanır.</span><span class="sxs-lookup"><span data-stu-id="aef10-108">This functionality is implemented largely by using <xref:System.Data.Linq.DataLoadOptions>.</span></span> <span data-ttu-id="aef10-109">Daha fazla bilgi için bkz. [ertelenmiş ve hemen yükleme](deferred-versus-immediate-loading.md).</span><span class="sxs-lookup"><span data-stu-id="aef10-109">For more information, see [Deferred versus Immediate Loading](deferred-versus-immediate-loading.md).</span></span>  
  
## <a name="partial-methods"></a><span data-ttu-id="aef10-110">Kısmi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="aef10-110">Partial Methods</span></span>  
 <span data-ttu-id="aef10-111">Varsayılan eşlemesinde, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] iş mantığınızı uygulamanıza yardımcı olacak kısmi yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="aef10-111">In its default mapping, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides partial methods to help you implement your business logic.</span></span> <span data-ttu-id="aef10-112">Daha fazla bilgi için bkz. [kısmi yöntemler kullanarak Iş mantığı ekleme](adding-business-logic-by-using-partial-methods.md).</span><span class="sxs-lookup"><span data-stu-id="aef10-112">For more information, see [Adding Business Logic By Using Partial Methods](adding-business-logic-by-using-partial-methods.md).</span></span>  
  
## <a name="stored-procedures-and-user-defined-functions"></a><span data-ttu-id="aef10-113">Saklı yordamlar ve Kullanıcı tanımlı Işlevler</span><span class="sxs-lookup"><span data-stu-id="aef10-113">Stored Procedures and User-Defined Functions</span></span>  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="aef10-114">, saklı yordamların ve Kullanıcı tanımlı işlevlerin kullanımını destekler.</span><span class="sxs-lookup"><span data-stu-id="aef10-114">supports the use of stored procedures and user-defined functions.</span></span> <span data-ttu-id="aef10-115">Saklı yordamlar, işlemleri özelleştirmek için sık sık kullanılır.</span><span class="sxs-lookup"><span data-stu-id="aef10-115">Stored procedures are frequently used to customize operations.</span></span> <span data-ttu-id="aef10-116">Daha fazla bilgi için bkz. [saklı yordamlar](stored-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="aef10-116">For more information, see [Stored Procedures](stored-procedures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aef10-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aef10-117">See also</span></span>

- [<span data-ttu-id="aef10-118">Insert, Update ve Delete İşlemlerini Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="aef10-118">Customizing Insert, Update, and Delete Operations</span></span>](customizing-insert-update-and-delete-operations.md)
