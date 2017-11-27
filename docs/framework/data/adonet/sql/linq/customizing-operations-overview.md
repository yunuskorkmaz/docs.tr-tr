---
title: "İşlem özelleştirme: genel bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a3546296-1443-4b88-aa6e-d41011041ba7
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7653ca137c93da5174e0ddcd1ced8bdfceaa9edc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="customizing-operations-overview"></a><span data-ttu-id="9fa07-102">İşlem özelleştirme: genel bakış</span><span class="sxs-lookup"><span data-stu-id="9fa07-102">Customizing Operations: Overview</span></span>
<span data-ttu-id="9fa07-103">Varsayılan olarak, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dinamik SQL ekleme, güncelleştirme ve silme işlemleri eşlemesini göre oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9fa07-103">By default, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates dynamic SQL for insert, update, and delete operations based on mapping.</span></span> <span data-ttu-id="9fa07-104">Bununla birlikte, pratikte genellikle güvenlik, doğrulama ve benzeri için sağlamak için kendi iş mantığı eklemek istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="9fa07-104">However, in practice you typically want to add your own business logic to provide for security, validation, and so forth.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="9fa07-105">Bu işlemler özelleştirme teknikler arasında şunlar yer alır.</span><span class="sxs-lookup"><span data-stu-id="9fa07-105"> techniques for customizing these operations include the following.</span></span>  
  
## <a name="loading-options"></a><span data-ttu-id="9fa07-106">Yükleme Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="9fa07-106">Loading Options</span></span>  
 <span data-ttu-id="9fa07-107">Sorgularınızda, veritabanına bağlandığında ana hedefiniz ilgili ne kadar veri alındığını kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9fa07-107">In your queries, you can control how much data related to your main target is retrieved when you connect to the database.</span></span> <span data-ttu-id="9fa07-108">Bu işlev büyük ölçüde kullanılarak uygulanır <xref:System.Data.Linq.DataLoadOptions>.</span><span class="sxs-lookup"><span data-stu-id="9fa07-108">This functionality is implemented largely by using <xref:System.Data.Linq.DataLoadOptions>.</span></span> <span data-ttu-id="9fa07-109">Daha fazla bilgi için bkz: [hemen yüklenirken karşı ertelenmiş](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span><span class="sxs-lookup"><span data-stu-id="9fa07-109">For more information, see [Deferred versus Immediate Loading](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span></span>  
  
## <a name="partial-methods"></a><span data-ttu-id="9fa07-110">Kısmi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="9fa07-110">Partial Methods</span></span>  
 <span data-ttu-id="9fa07-111">Kendi varsayılan eşlemesinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , iş mantığı uygulamanıza yardımcı olmak için kısmi yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9fa07-111">In its default mapping, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides partial methods to help you implement your business logic.</span></span> <span data-ttu-id="9fa07-112">Daha fazla bilgi için bkz: [ekleme iş mantığı tarafından kısmi yöntemlerini kullanarak](../../../../../../docs/framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md).</span><span class="sxs-lookup"><span data-stu-id="9fa07-112">For more information, see [Adding Business Logic By Using Partial Methods](../../../../../../docs/framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md).</span></span>  
  
## <a name="stored-procedures-and-user-defined-functions"></a><span data-ttu-id="9fa07-113">Saklı yordamlar ve kullanıcı tanımlı işlevler</span><span class="sxs-lookup"><span data-stu-id="9fa07-113">Stored Procedures and User-Defined Functions</span></span>  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="9fa07-114">saklı yordamlar ve kullanıcı tanımlı işlevler kullanımını destekler.</span><span class="sxs-lookup"><span data-stu-id="9fa07-114"> supports the use of stored procedures and user-defined functions.</span></span> <span data-ttu-id="9fa07-115">Saklı yordamlar operations özelleştirmek için sık kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9fa07-115">Stored procedures are frequently used to customize operations.</span></span> <span data-ttu-id="9fa07-116">Daha fazla bilgi için bkz: [saklı yordamlar](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="9fa07-116">For more information, see [Stored Procedures](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fa07-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9fa07-117">See Also</span></span>  
 [<span data-ttu-id="9fa07-118">Özelleştirme ekleme, güncelleştirme ve silme işlemleri</span><span class="sxs-lookup"><span data-stu-id="9fa07-118">Customizing Insert, Update, and Delete Operations</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
