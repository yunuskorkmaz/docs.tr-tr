---
title: ADO.NET'e LINQ (Portal Sayfası)
description: LINQ to ADO.NET, LINQ programlama modelini kullanarak ADO.NET içinde herhangi bir sıralanabilir nesne üzerinde sorgulama yapmanızı sağlar. Üç ADO.NET LINQ teknolojisi hakkında bilgi edinin.
ms.date: 07/20/2015
ms.assetid: 6bd269b4-3509-4688-b672-836008704182
ms.openlocfilehash: 6d8a6a7a90abe12dacec9a017f80c1ff1abd46f1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202558"
---
# <a name="linq-to-adonet-portal-page"></a><span data-ttu-id="b4d5b-104">ADO.NET'e LINQ (Portal Sayfası)</span><span class="sxs-lookup"><span data-stu-id="b4d5b-104">LINQ to ADO.NET (Portal Page)</span></span>

<span data-ttu-id="b4d5b-105">LINQ to ADO.NET, dil ile tümleşik sorgu (LINQ) programlama modelini kullanarak ADO.NET içinde herhangi bir sıralanabilir nesne üzerinde sorgulama yapmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b4d5b-105">LINQ to ADO.NET enables you to query over any enumerable object in ADO.NET by using the Language-Integrated Query (LINQ) programming model.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b4d5b-106">LINQ to ADO.NET belge .NET Framework SDK: [LINQ ve ADO.net](../../../../framework/data/adonet/linq-and-ado-net.md)' nin ADO.net bölümünde bulunur.</span><span class="sxs-lookup"><span data-stu-id="b4d5b-106">The LINQ to ADO.NET documentation is located in the ADO.NET section of the .NET Framework SDK: [LINQ and ADO.NET](../../../../framework/data/adonet/linq-and-ado-net.md).</span></span>  
  
 <span data-ttu-id="b4d5b-107">Üç ayrı ADO.NET dil ile tümleşik sorgu (LINQ) teknolojisi vardır: LINQ to DataSet, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] ve LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="b4d5b-107">There are three separate ADO.NET Language-Integrated Query (LINQ) technologies: LINQ to DataSet, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], and LINQ to Entities.</span></span> <span data-ttu-id="b4d5b-108">LINQ to DataSet üzerinde daha zengin, iyileştirilmiş sorgulama sağlar <xref:System.Data.DataSet> , [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] SQL Server veritabanı şemalarını doğrudan sorgulayabilir ve LINQ to Entities varlık veri modeli sorgulamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b4d5b-108">LINQ to DataSet provides richer, optimized querying over the <xref:System.Data.DataSet>, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] enables you to directly query SQL Server database schemas, and LINQ to Entities allows you to query an Entity Data Model.</span></span>  
  
## <a name="linq-to-dataset"></a><span data-ttu-id="b4d5b-109">LINQ - DataSet</span><span class="sxs-lookup"><span data-stu-id="b4d5b-109">LINQ to DataSet</span></span>  

 <span data-ttu-id="b4d5b-110">, <xref:System.Data.DataSet> ADO.net ' deki en yaygın olarak kullanılan bileşenlerden biridir ve ADO.net 'in üzerinde oluşturulduğu, bağlantısı kesilen programlama modelinin temel öğesidir.</span><span class="sxs-lookup"><span data-stu-id="b4d5b-110">The <xref:System.Data.DataSet> is one of the most widely used components in ADO.NET, and is a key element of the disconnected programming model that ADO.NET is built on.</span></span> <span data-ttu-id="b4d5b-111">Ancak, bu kadar belirgin olsa da, <xref:System.Data.DataSet> sınırlı sorgu yeteneklerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="b4d5b-111">Despite this prominence, however, the <xref:System.Data.DataSet> has limited query capabilities.</span></span>  
  
 <span data-ttu-id="b4d5b-112">LINQ to DataSet, <xref:System.Data.DataSet> diğer birçok veri kaynağı için kullanılabilen aynı sorgu işlevini kullanarak ' ye daha zengin sorgu özellikleri oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b4d5b-112">LINQ to DataSet enables you to build richer query capabilities into <xref:System.Data.DataSet> by using the same query functionality that is available for many other data sources.</span></span>  
  
 <span data-ttu-id="b4d5b-113">Daha fazla bilgi için bkz. [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="b4d5b-113">For more information, see [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md).</span></span>  
  
## <a name="linq-to-sql"></a><span data-ttu-id="b4d5b-114">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="b4d5b-114">LINQ to SQL</span></span>  

 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] <span data-ttu-id="b4d5b-115">ilişkisel verileri nesne olarak yönetmeye yönelik bir çalışma zamanı altyapısı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b4d5b-115">provides a run-time infrastructure for managing relational data as objects.</span></span> <span data-ttu-id="b4d5b-116">[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]' De, bir ilişkisel veritabanının veri modeli, geliştiricinin programlama dilinde ifade edilen bir nesne modeliyle eşleştirilir.</span><span class="sxs-lookup"><span data-stu-id="b4d5b-116">In [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], the data model of a relational database is mapped to an object model expressed in the programming language of the developer.</span></span> <span data-ttu-id="b4d5b-117">Uygulamayı yürüttüğünüzde, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] nesne modelindeki dil ile tümleşik SORGULARı SQL 'e çevirir ve yürütmek üzere veritabanına gönderir.</span><span class="sxs-lookup"><span data-stu-id="b4d5b-117">When you execute the application, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] translates language-integrated queries in the object model into SQL and sends them to the database for execution.</span></span> <span data-ttu-id="b4d5b-118">Veritabanı sonuçları döndürdüğünde, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] bunları işleyebileceğiniz nesnelere geri çevirir.</span><span class="sxs-lookup"><span data-stu-id="b4d5b-118">When the database returns the results, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] translates them back into objects that you can manipulate.</span></span>  
  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] <span data-ttu-id="b4d5b-119">, veritabanında saklı yordamlar ve Kullanıcı tanımlı işlevler ve nesne modelinde devralma için destek içerir.</span><span class="sxs-lookup"><span data-stu-id="b4d5b-119">includes support for stored procedures and user-defined functions in the database, and for inheritance in the object model.</span></span>  
  
 <span data-ttu-id="b4d5b-120">Daha fazla bilgi için bkz. [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="b4d5b-120">For more information, see [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md).</span></span>  
  
## <a name="linq-to-entities"></a><span data-ttu-id="b4d5b-121">LINQ - Varlıklar</span><span class="sxs-lookup"><span data-stu-id="b4d5b-121">LINQ to Entities</span></span>  

 <span data-ttu-id="b4d5b-122">Varlık Veri Modeli, ilişkisel veriler .NET ortamında nesneler olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="b4d5b-122">Through the Entity Data Model, relational data is exposed as objects in the .NET environment.</span></span> <span data-ttu-id="b4d5b-123">Bu, nesne katmanını LINQ desteği için ideal bir hedef haline getirir ve geliştiricilerin iş mantığını oluşturmak için kullanılan dilden sorguları veritabanına göre formüllemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="b4d5b-123">This makes the object layer an ideal target for LINQ support, allowing developers to formulate queries against the database from the language used to build the business logic.</span></span> <span data-ttu-id="b4d5b-124">Bu yetenek LINQ to Entities olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="b4d5b-124">This capability is known as LINQ to Entities.</span></span> <span data-ttu-id="b4d5b-125">Daha fazla bilgi için bkz. [LINQ to Entities](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md) .</span><span class="sxs-lookup"><span data-stu-id="b4d5b-125">See [LINQ to Entities](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md) for more information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4d5b-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b4d5b-126">See also</span></span>

- [<span data-ttu-id="b4d5b-127">LINQ ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b4d5b-127">LINQ and ADO.NET</span></span>](../../../../framework/data/adonet/linq-and-ado-net.md)
- [<span data-ttu-id="b4d5b-128">Dil ile tümleşik sorgu (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="b4d5b-128">Language-Integrated Query (LINQ) (C#)</span></span>](./index.md)
