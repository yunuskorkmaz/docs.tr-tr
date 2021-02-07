---
description: 'Hakkında daha fazla bilgi edinin: özelleştirme Işlemleri: genel bakış'
title: 'İşlemleri Özelleştirme: Genel Bakış'
ms.date: 03/30/2017
ms.assetid: a3546296-1443-4b88-aa6e-d41011041ba7
ms.openlocfilehash: bdcaf482f49b9c55fb7a1834b19b683ac2fa16bb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729607"
---
# <a name="customizing-operations-overview"></a><span data-ttu-id="fa101-103">İşlemleri Özelleştirme: Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="fa101-103">Customizing Operations: Overview</span></span>

<span data-ttu-id="fa101-104">Varsayılan olarak, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] eşlemeye göre INSERT, Update ve DELETE işlemleri için dınamık SQL oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fa101-104">By default, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates dynamic SQL for insert, update, and delete operations based on mapping.</span></span> <span data-ttu-id="fa101-105">Bununla birlikte, pratikte güvenlik, doğrulama ve benzerlerini sağlamak üzere kendi iş mantığınızı eklemek istersiniz.</span><span class="sxs-lookup"><span data-stu-id="fa101-105">However, in practice you typically want to add your own business logic to provide for security, validation, and so forth.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="fa101-106">Bu işlemleri özelleştirmeye yönelik teknikler şunlardır.</span><span class="sxs-lookup"><span data-stu-id="fa101-106">techniques for customizing these operations include the following.</span></span>  
  
## <a name="loading-options"></a><span data-ttu-id="fa101-107">Yükleme seçenekleri</span><span class="sxs-lookup"><span data-stu-id="fa101-107">Loading Options</span></span>  

 <span data-ttu-id="fa101-108">Sorgularda, veritabanına bağlandığınızda ana Hedefinizdeki ilgili verilerin ne kadarının alındığını denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa101-108">In your queries, you can control how much data related to your main target is retrieved when you connect to the database.</span></span> <span data-ttu-id="fa101-109">Bu işlevsellik büyük ölçüde kullanılarak uygulanır <xref:System.Data.Linq.DataLoadOptions> .</span><span class="sxs-lookup"><span data-stu-id="fa101-109">This functionality is implemented largely by using <xref:System.Data.Linq.DataLoadOptions>.</span></span> <span data-ttu-id="fa101-110">Daha fazla bilgi için bkz. [ertelenmiş ve hemen yükleme](deferred-versus-immediate-loading.md).</span><span class="sxs-lookup"><span data-stu-id="fa101-110">For more information, see [Deferred versus Immediate Loading](deferred-versus-immediate-loading.md).</span></span>  
  
## <a name="partial-methods"></a><span data-ttu-id="fa101-111">Kısmi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="fa101-111">Partial Methods</span></span>  

 <span data-ttu-id="fa101-112">Varsayılan eşlemesinde, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] iş mantığınızı uygulamanıza yardımcı olacak kısmi yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="fa101-112">In its default mapping, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides partial methods to help you implement your business logic.</span></span> <span data-ttu-id="fa101-113">Daha fazla bilgi için bkz. [kısmi yöntemler kullanarak Iş mantığı ekleme](adding-business-logic-by-using-partial-methods.md).</span><span class="sxs-lookup"><span data-stu-id="fa101-113">For more information, see [Adding Business Logic By Using Partial Methods](adding-business-logic-by-using-partial-methods.md).</span></span>  
  
## <a name="stored-procedures-and-user-defined-functions"></a><span data-ttu-id="fa101-114">Saklı yordamlar ve User-Defined Işlevleri</span><span class="sxs-lookup"><span data-stu-id="fa101-114">Stored Procedures and User-Defined Functions</span></span>  

 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="fa101-115">, saklı yordamların ve Kullanıcı tanımlı işlevlerin kullanımını destekler.</span><span class="sxs-lookup"><span data-stu-id="fa101-115">supports the use of stored procedures and user-defined functions.</span></span> <span data-ttu-id="fa101-116">Saklı yordamlar, işlemleri özelleştirmek için sık sık kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fa101-116">Stored procedures are frequently used to customize operations.</span></span> <span data-ttu-id="fa101-117">Daha fazla bilgi için bkz. [saklı yordamlar](stored-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="fa101-117">For more information, see [Stored Procedures](stored-procedures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa101-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fa101-118">See also</span></span>

- [<span data-ttu-id="fa101-119">Insert, Update ve Delete İşlemlerini Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="fa101-119">Customizing Insert, Update, and Delete Operations</span></span>](customizing-insert-update-and-delete-operations.md)
