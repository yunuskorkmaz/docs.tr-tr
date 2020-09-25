---
title: 'İşlemleri Özelleştirme: Genel Bakış'
ms.date: 03/30/2017
ms.assetid: a3546296-1443-4b88-aa6e-d41011041ba7
ms.openlocfilehash: d4d375716e3199afcbbb9bbd8b8b04867ca0e5fa
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173529"
---
# <a name="customizing-operations-overview"></a><span data-ttu-id="37c44-102">İşlemleri Özelleştirme: Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="37c44-102">Customizing Operations: Overview</span></span>

<span data-ttu-id="37c44-103">Varsayılan olarak, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] eşlemeye göre INSERT, Update ve DELETE işlemleri için dınamık SQL oluşturur.</span><span class="sxs-lookup"><span data-stu-id="37c44-103">By default, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates dynamic SQL for insert, update, and delete operations based on mapping.</span></span> <span data-ttu-id="37c44-104">Bununla birlikte, pratikte güvenlik, doğrulama ve benzerlerini sağlamak üzere kendi iş mantığınızı eklemek istersiniz.</span><span class="sxs-lookup"><span data-stu-id="37c44-104">However, in practice you typically want to add your own business logic to provide for security, validation, and so forth.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="37c44-105">Bu işlemleri özelleştirmeye yönelik teknikler şunlardır.</span><span class="sxs-lookup"><span data-stu-id="37c44-105">techniques for customizing these operations include the following.</span></span>  
  
## <a name="loading-options"></a><span data-ttu-id="37c44-106">Yükleme seçenekleri</span><span class="sxs-lookup"><span data-stu-id="37c44-106">Loading Options</span></span>  

 <span data-ttu-id="37c44-107">Sorgularda, veritabanına bağlandığınızda ana Hedefinizdeki ilgili verilerin ne kadarının alındığını denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="37c44-107">In your queries, you can control how much data related to your main target is retrieved when you connect to the database.</span></span> <span data-ttu-id="37c44-108">Bu işlevsellik büyük ölçüde kullanılarak uygulanır <xref:System.Data.Linq.DataLoadOptions> .</span><span class="sxs-lookup"><span data-stu-id="37c44-108">This functionality is implemented largely by using <xref:System.Data.Linq.DataLoadOptions>.</span></span> <span data-ttu-id="37c44-109">Daha fazla bilgi için bkz. [ertelenmiş ve hemen yükleme](deferred-versus-immediate-loading.md).</span><span class="sxs-lookup"><span data-stu-id="37c44-109">For more information, see [Deferred versus Immediate Loading](deferred-versus-immediate-loading.md).</span></span>  
  
## <a name="partial-methods"></a><span data-ttu-id="37c44-110">Kısmi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="37c44-110">Partial Methods</span></span>  

 <span data-ttu-id="37c44-111">Varsayılan eşlemesinde, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] iş mantığınızı uygulamanıza yardımcı olacak kısmi yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="37c44-111">In its default mapping, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides partial methods to help you implement your business logic.</span></span> <span data-ttu-id="37c44-112">Daha fazla bilgi için bkz. [kısmi yöntemler kullanarak Iş mantığı ekleme](adding-business-logic-by-using-partial-methods.md).</span><span class="sxs-lookup"><span data-stu-id="37c44-112">For more information, see [Adding Business Logic By Using Partial Methods](adding-business-logic-by-using-partial-methods.md).</span></span>  
  
## <a name="stored-procedures-and-user-defined-functions"></a><span data-ttu-id="37c44-113">Saklı yordamlar ve Kullanıcı tanımlı Işlevler</span><span class="sxs-lookup"><span data-stu-id="37c44-113">Stored Procedures and User-Defined Functions</span></span>  

 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="37c44-114">, saklı yordamların ve Kullanıcı tanımlı işlevlerin kullanımını destekler.</span><span class="sxs-lookup"><span data-stu-id="37c44-114">supports the use of stored procedures and user-defined functions.</span></span> <span data-ttu-id="37c44-115">Saklı yordamlar, işlemleri özelleştirmek için sık sık kullanılır.</span><span class="sxs-lookup"><span data-stu-id="37c44-115">Stored procedures are frequently used to customize operations.</span></span> <span data-ttu-id="37c44-116">Daha fazla bilgi için bkz. [saklı yordamlar](stored-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="37c44-116">For more information, see [Stored Procedures](stored-procedures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37c44-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="37c44-117">See also</span></span>

- [<span data-ttu-id="37c44-118">Insert, Update ve Delete İşlemlerini Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="37c44-118">Customizing Insert, Update, and Delete Operations</span></span>](customizing-insert-update-and-delete-operations.md)
