---
title: Veritabanı sorgulama
ms.date: 03/30/2017
ms.assetid: eefb8b0c-ff07-4e86-a3d3-567479523fe9
ms.openlocfilehash: fdcfaa3fc0d08df07027d44399612fb688b920d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33358670"
---
# <a name="querying-the-database"></a><span data-ttu-id="654f2-102">Veritabanı sorgulama</span><span class="sxs-lookup"><span data-stu-id="654f2-102">Querying the Database</span></span>
<span data-ttu-id="654f2-103">Bu konu grubu geliştirmek ve sorguları yürütmek açıklar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projeleri.</span><span class="sxs-lookup"><span data-stu-id="654f2-103">This group of topics describes how to develop and execute queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projects.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="654f2-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="654f2-104">In This Section</span></span>  
 [<span data-ttu-id="654f2-105">Nasıl yapılır: Bilgi Sorgulama</span><span class="sxs-lookup"><span data-stu-id="654f2-105">How to: Query for Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-query-for-information.md)  
 <span data-ttu-id="654f2-106">Kısaca gösterir nasıl [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorgular olan temelde aynı [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] genellikle sorgular.</span><span class="sxs-lookup"><span data-stu-id="654f2-106">Briefly shows how [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries are basically the same as [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] queries generally.</span></span>  
  
 [<span data-ttu-id="654f2-107">Nasıl yapılır: Bilgileri Salt Okunur Olarak Alma</span><span class="sxs-lookup"><span data-stu-id="654f2-107">How to: Retrieve Information As Read-Only</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-information-as-read-only.md)  
 <span data-ttu-id="654f2-108">Veriler için herhangi bir değişiklik planlı sorgu performansını artırmak açıklar.</span><span class="sxs-lookup"><span data-stu-id="654f2-108">Describes how to increase query performance when no change to the data is planned.</span></span>  
  
 [<span data-ttu-id="654f2-109">Nasıl yapılır: Ne Kadar İlgili Verilerin Alındığını Denetleme</span><span class="sxs-lookup"><span data-stu-id="654f2-109">How to: Control How Much Related Data Is Retrieved</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-control-how-much-related-data-is-retrieved.md)  
 <span data-ttu-id="654f2-110">Hangi ilgili verileri birlikte ana hedef alınır denetlemek açıklar.</span><span class="sxs-lookup"><span data-stu-id="654f2-110">Describes how to control which related data is retrieved together with the main target.</span></span>  
  
 [<span data-ttu-id="654f2-111">Nasıl yapılır: İlgili Verileri Filtreleme</span><span class="sxs-lookup"><span data-stu-id="654f2-111">How to: Filter Related Data</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-filter-related-data.md)  
 <span data-ttu-id="654f2-112">Bir alt sorgu kullanarak ilgili verileri almak açıklar.</span><span class="sxs-lookup"><span data-stu-id="654f2-112">Describes how to retrieve related data by using a sub-query.</span></span>  
  
 [<span data-ttu-id="654f2-113">Nasıl yapılır: Geciktirilmiş Yüklemeyi Kapatma</span><span class="sxs-lookup"><span data-stu-id="654f2-113">How to: Turn Off Deferred Loading</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-turn-off-deferred-loading.md)  
 <span data-ttu-id="654f2-114">Ertelenen yükleme devre dışı bırakmak açıklar.</span><span class="sxs-lookup"><span data-stu-id="654f2-114">Describes how to turn off deferred loading.</span></span>  
  
 [<span data-ttu-id="654f2-115">Nasıl yapılır: Doğrudan SQL Sorguları Yürütme</span><span class="sxs-lookup"><span data-stu-id="654f2-115">How to: Directly Execute SQL Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-directly-execute-sql-queries.md)  
 <span data-ttu-id="654f2-116">SQL dilini kullanarak sorguları göndermek açıklar.</span><span class="sxs-lookup"><span data-stu-id="654f2-116">Describes how to submit queries by using SQL language.</span></span>  
  
 [<span data-ttu-id="654f2-117">Nasıl yapılır: Sorguları Depolama ve Yeniden Kullanma</span><span class="sxs-lookup"><span data-stu-id="654f2-117">How to: Store and Reuse Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-store-and-reuse-queries.md)  
 <span data-ttu-id="654f2-118">Bir kez bir sorgu derleme ancak farklı parametrelerle birden çok kez kullanın açıklar.</span><span class="sxs-lookup"><span data-stu-id="654f2-118">Describes how to compile a query one time but use it multiple times with different parameters.</span></span>  
  
 [<span data-ttu-id="654f2-119">Nasıl yapılır: Sorgularda Bileşik Anahtarlar İşleme</span><span class="sxs-lookup"><span data-stu-id="654f2-119">How to: Handle Composite Keys in Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-handle-composite-keys-in-queries.md)  
 <span data-ttu-id="654f2-120">Burada işleci yalnızca tek bir bağımsız değişken alan bir sorguda birden fazla sütun eklemek açıklar.</span><span class="sxs-lookup"><span data-stu-id="654f2-120">Describes how to include more than one column in a query where the operator takes only a single argument.</span></span>  
  
 [<span data-ttu-id="654f2-121">Nasıl yapılır: Tek Seferde Birçok Nesne Alma</span><span class="sxs-lookup"><span data-stu-id="654f2-121">How to: Retrieve Many Objects At Once</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-many-objects-at-once.md)  
 <span data-ttu-id="654f2-122">Nasıl kullanılacağını açıklar <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span><span class="sxs-lookup"><span data-stu-id="654f2-122">Describes how to use <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span></span>  
  
 [<span data-ttu-id="654f2-123">Nasıl yapılır: DataContext Düzeyinde Filtreleme</span><span class="sxs-lookup"><span data-stu-id="654f2-123">How to: Filter at the DataContext Level</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-filter-at-the-datacontext-level.md)  
 <span data-ttu-id="654f2-124">Başka bir kullanımını açıklar <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span><span class="sxs-lookup"><span data-stu-id="654f2-124">Describes another use of <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span></span>  
  
 [<span data-ttu-id="654f2-125">Sorgu Örnekleri</span><span class="sxs-lookup"><span data-stu-id="654f2-125">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 <span data-ttu-id="654f2-126">Sorguların çoğu örnekler verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="654f2-126">Provides many examples of queries.</span></span>
