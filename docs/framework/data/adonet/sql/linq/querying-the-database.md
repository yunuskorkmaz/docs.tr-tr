---
title: Veritabanını Sorgulama
ms.date: 03/30/2017
ms.assetid: eefb8b0c-ff07-4e86-a3d3-567479523fe9
ms.openlocfilehash: b4ce48ee3d49769a353bf7371140b1f5a645f34e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91184887"
---
# <a name="querying-the-database"></a><span data-ttu-id="4eec0-102">Veritabanını Sorgulama</span><span class="sxs-lookup"><span data-stu-id="4eec0-102">Querying the Database</span></span>

<span data-ttu-id="4eec0-103">Bu konu grubu, projelerde sorguları geliştirmeyi ve yürütmeyi açıklamaktadır [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="4eec0-103">This group of topics describes how to develop and execute queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projects.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4eec0-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="4eec0-104">In This Section</span></span>  

 [<span data-ttu-id="4eec0-105">Nasıl yapılır: Bilgi Sorgulama</span><span class="sxs-lookup"><span data-stu-id="4eec0-105">How to: Query for Information</span></span>](how-to-query-for-information.md)  
 <span data-ttu-id="4eec0-106">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Sorguların temel olarak LINQ sorgularıyla genellikle nasıl aynı olduğunu kısaca gösterir.</span><span class="sxs-lookup"><span data-stu-id="4eec0-106">Briefly shows how [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries are basically the same as LINQ queries generally.</span></span>  
  
 [<span data-ttu-id="4eec0-107">Nasıl yapılır: Bilgileri Salt Okunur Olarak Alma</span><span class="sxs-lookup"><span data-stu-id="4eec0-107">How to: Retrieve Information As Read-Only</span></span>](how-to-retrieve-information-as-read-only.md)  
 <span data-ttu-id="4eec0-108">Verilerde hiçbir değişiklik planlanolmadığında sorgu performansının nasıl artırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="4eec0-108">Describes how to increase query performance when no change to the data is planned.</span></span>  
  
 [<span data-ttu-id="4eec0-109">Nasıl yapılır: Ne Kadar İlgili Verilerin Alındığını Denetleme</span><span class="sxs-lookup"><span data-stu-id="4eec0-109">How to: Control How Much Related Data Is Retrieved</span></span>](how-to-control-how-much-related-data-is-retrieved.md)  
 <span data-ttu-id="4eec0-110">Ana hedefle birlikte hangi ilgili verilerin birlikte alındığını nasıl denetleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="4eec0-110">Describes how to control which related data is retrieved together with the main target.</span></span>  
  
 [<span data-ttu-id="4eec0-111">Nasıl yapılır: İlgili Verileri Filtreleme</span><span class="sxs-lookup"><span data-stu-id="4eec0-111">How to: Filter Related Data</span></span>](how-to-filter-related-data.md)  
 <span data-ttu-id="4eec0-112">Bir alt sorgu kullanarak ilgili verilerin nasıl alınacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="4eec0-112">Describes how to retrieve related data by using a sub-query.</span></span>  
  
 [<span data-ttu-id="4eec0-113">Nasıl yapılır: Geciktirilmiş Yüklemeyi Kapatma</span><span class="sxs-lookup"><span data-stu-id="4eec0-113">How to: Turn Off Deferred Loading</span></span>](how-to-turn-off-deferred-loading.md)  
 <span data-ttu-id="4eec0-114">Ertelenmiş yüklemeyi devre dışı bırakma işlemini açıklar.</span><span class="sxs-lookup"><span data-stu-id="4eec0-114">Describes how to turn off deferred loading.</span></span>  
  
 [<span data-ttu-id="4eec0-115">Nasıl yapılır: Doğrudan SQL Sorguları Yürütme</span><span class="sxs-lookup"><span data-stu-id="4eec0-115">How to: Directly Execute SQL Queries</span></span>](how-to-directly-execute-sql-queries.md)  
 <span data-ttu-id="4eec0-116">SQL Language kullanılarak sorguların nasıl gönderileceği açıklanır.</span><span class="sxs-lookup"><span data-stu-id="4eec0-116">Describes how to submit queries by using SQL language.</span></span>  
  
 [<span data-ttu-id="4eec0-117">Nasıl yapılır: Sorguları Depolama ve Yeniden Kullanma</span><span class="sxs-lookup"><span data-stu-id="4eec0-117">How to: Store and Reuse Queries</span></span>](how-to-store-and-reuse-queries.md)  
 <span data-ttu-id="4eec0-118">Bir sorgunun bir kez nasıl derlenip farklı parametrelerle birden çok kez nasıl kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4eec0-118">Describes how to compile a query one time but use it multiple times with different parameters.</span></span>  
  
 [<span data-ttu-id="4eec0-119">Nasıl yapılır: Sorgularda Bileşik Anahtarlar İşleme</span><span class="sxs-lookup"><span data-stu-id="4eec0-119">How to: Handle Composite Keys in Queries</span></span>](how-to-handle-composite-keys-in-queries.md)  
 <span data-ttu-id="4eec0-120">Bir sorguda birden fazla sütunun, işlecin yalnızca tek bir bağımsız değişken aldığı bir sorguya nasıl ekleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="4eec0-120">Describes how to include more than one column in a query where the operator takes only a single argument.</span></span>  
  
 [<span data-ttu-id="4eec0-121">Nasıl yapılır: Tek Seferde Birçok Nesne Alma</span><span class="sxs-lookup"><span data-stu-id="4eec0-121">How to: Retrieve Many Objects At Once</span></span>](how-to-retrieve-many-objects-at-once.md)  
 <span data-ttu-id="4eec0-122">' Nin nasıl kullanılacağını açıklar <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> .</span><span class="sxs-lookup"><span data-stu-id="4eec0-122">Describes how to use <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span></span>  
  
 [<span data-ttu-id="4eec0-123">Nasıl yapılır: DataContext Düzeyinde Filtreleme</span><span class="sxs-lookup"><span data-stu-id="4eec0-123">How to: Filter at the DataContext Level</span></span>](how-to-filter-at-the-datacontext-level.md)  
 <span data-ttu-id="4eec0-124">Uygulamasının başka bir kullanımını açıklar <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> .</span><span class="sxs-lookup"><span data-stu-id="4eec0-124">Describes another use of <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span></span>  
  
 [<span data-ttu-id="4eec0-125">Sorgu örnekleri</span><span class="sxs-lookup"><span data-stu-id="4eec0-125">Query Examples</span></span>](query-examples.md)  
 <span data-ttu-id="4eec0-126">Birçok sorguya örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="4eec0-126">Provides many examples of queries.</span></span>
