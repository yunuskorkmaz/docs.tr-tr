---
title: Veritabanını Sorgulama
ms.date: 03/30/2017
ms.assetid: eefb8b0c-ff07-4e86-a3d3-567479523fe9
ms.openlocfilehash: 3c48879d8e3ae699ef749fc14923358174010aae
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782077"
---
# <a name="querying-the-database"></a><span data-ttu-id="73dff-102">Veritabanını Sorgulama</span><span class="sxs-lookup"><span data-stu-id="73dff-102">Querying the Database</span></span>
<span data-ttu-id="73dff-103">Bu konu grubu, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projelerde sorguları geliştirmeyi ve yürütmeyi açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="73dff-103">This group of topics describes how to develop and execute queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projects.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="73dff-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="73dff-104">In This Section</span></span>  
 [<span data-ttu-id="73dff-105">Nasıl yapılır: Bilgi sorgula</span><span class="sxs-lookup"><span data-stu-id="73dff-105">How to: Query for Information</span></span>](how-to-query-for-information.md)  
 <span data-ttu-id="73dff-106">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Sorguların genellikle [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] sorgularla aynı olduğunu kısaca gösterir.</span><span class="sxs-lookup"><span data-stu-id="73dff-106">Briefly shows how [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries are basically the same as [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] queries generally.</span></span>  
  
 [<span data-ttu-id="73dff-107">Nasıl yapılır: Bilgileri salt okuma olarak alma</span><span class="sxs-lookup"><span data-stu-id="73dff-107">How to: Retrieve Information As Read-Only</span></span>](how-to-retrieve-information-as-read-only.md)  
 <span data-ttu-id="73dff-108">Verilerde hiçbir değişiklik planlanolmadığında sorgu performansının nasıl artırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="73dff-108">Describes how to increase query performance when no change to the data is planned.</span></span>  
  
 [<span data-ttu-id="73dff-109">Nasıl yapılır: Ilgili verilerin ne kadar alındığını denetleme</span><span class="sxs-lookup"><span data-stu-id="73dff-109">How to: Control How Much Related Data Is Retrieved</span></span>](how-to-control-how-much-related-data-is-retrieved.md)  
 <span data-ttu-id="73dff-110">Ana hedefle birlikte hangi ilgili verilerin birlikte alındığını nasıl denetleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="73dff-110">Describes how to control which related data is retrieved together with the main target.</span></span>  
  
 [<span data-ttu-id="73dff-111">Nasıl yapılır: Ilgili verileri filtrele</span><span class="sxs-lookup"><span data-stu-id="73dff-111">How to: Filter Related Data</span></span>](how-to-filter-related-data.md)  
 <span data-ttu-id="73dff-112">Bir alt sorgu kullanarak ilgili verilerin nasıl alınacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="73dff-112">Describes how to retrieve related data by using a sub-query.</span></span>  
  
 [<span data-ttu-id="73dff-113">Nasıl yapılır: Ertelenmiş yüklemeyi kapat</span><span class="sxs-lookup"><span data-stu-id="73dff-113">How to: Turn Off Deferred Loading</span></span>](how-to-turn-off-deferred-loading.md)  
 <span data-ttu-id="73dff-114">Ertelenmiş yüklemeyi devre dışı bırakma işlemini açıklar.</span><span class="sxs-lookup"><span data-stu-id="73dff-114">Describes how to turn off deferred loading.</span></span>  
  
 [<span data-ttu-id="73dff-115">Nasıl yapılır: SQL sorgularını doğrudan Yürüt</span><span class="sxs-lookup"><span data-stu-id="73dff-115">How to: Directly Execute SQL Queries</span></span>](how-to-directly-execute-sql-queries.md)  
 <span data-ttu-id="73dff-116">SQL Language kullanılarak sorguların nasıl gönderileceği açıklanır.</span><span class="sxs-lookup"><span data-stu-id="73dff-116">Describes how to submit queries by using SQL language.</span></span>  
  
 [<span data-ttu-id="73dff-117">Nasıl yapılır: Sorguları depolayın ve yeniden kullanın</span><span class="sxs-lookup"><span data-stu-id="73dff-117">How to: Store and Reuse Queries</span></span>](how-to-store-and-reuse-queries.md)  
 <span data-ttu-id="73dff-118">Bir sorgunun bir kez nasıl derlenip farklı parametrelerle birden çok kez nasıl kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="73dff-118">Describes how to compile a query one time but use it multiple times with different parameters.</span></span>  
  
 [<span data-ttu-id="73dff-119">Nasıl yapılır: Sorgularda bileşik anahtarları işle</span><span class="sxs-lookup"><span data-stu-id="73dff-119">How to: Handle Composite Keys in Queries</span></span>](how-to-handle-composite-keys-in-queries.md)  
 <span data-ttu-id="73dff-120">Bir sorguda birden fazla sütunun, işlecin yalnızca tek bir bağımsız değişken aldığı bir sorguya nasıl ekleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="73dff-120">Describes how to include more than one column in a query where the operator takes only a single argument.</span></span>  
  
 [<span data-ttu-id="73dff-121">Nasıl yapılır: Aynı anda birçok nesneyi al</span><span class="sxs-lookup"><span data-stu-id="73dff-121">How to: Retrieve Many Objects At Once</span></span>](how-to-retrieve-many-objects-at-once.md)  
 <span data-ttu-id="73dff-122">' Nin nasıl <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="73dff-122">Describes how to use <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span></span>  
  
 [<span data-ttu-id="73dff-123">Nasıl yapılır: DataContext düzeyinde filtrele</span><span class="sxs-lookup"><span data-stu-id="73dff-123">How to: Filter at the DataContext Level</span></span>](how-to-filter-at-the-datacontext-level.md)  
 <span data-ttu-id="73dff-124">Uygulamasının <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>başka bir kullanımını açıklar.</span><span class="sxs-lookup"><span data-stu-id="73dff-124">Describes another use of <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span></span>  
  
 [<span data-ttu-id="73dff-125">Sorgu Örnekleri</span><span class="sxs-lookup"><span data-stu-id="73dff-125">Query Examples</span></span>](query-examples.md)  
 <span data-ttu-id="73dff-126">Birçok sorguya örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="73dff-126">Provides many examples of queries.</span></span>
