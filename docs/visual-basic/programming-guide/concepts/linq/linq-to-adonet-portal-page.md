---
description: 'Hakkında daha fazla bilgi edinin: LINQ to ADO.NET (portal sayfası)'
title: ADO.NET'e LINQ (Portal Sayfası)
ms.date: 07/20/2015
ms.assetid: bbbd7c76-2981-4b91-b8d2-437547181f52
ms.openlocfilehash: 5fe670be0bb87fb9a18ee73b3c3ea341d787b13e
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100426757"
---
# <a name="linq-to-adonet-portal-page"></a><span data-ttu-id="c5c94-103">ADO.NET'e LINQ (Portal Sayfası)</span><span class="sxs-lookup"><span data-stu-id="c5c94-103">LINQ to ADO.NET (Portal Page)</span></span>

<span data-ttu-id="c5c94-104">LINQ to ADO.NET, Language-Integrated Query (LINQ) programlama modelini kullanarak ADO.NET içinde herhangi bir numaralandırılabilir nesne üzerinde sorgulama yapmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5c94-104">LINQ to ADO.NET enables you to query over any enumerable object in ADO.NET by using the Language-Integrated Query (LINQ) programming model.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c5c94-105">LINQ to ADO.NET belge .NET Framework SDK: [LINQ ve ADO.net](../../../../framework/data/adonet/linq-and-ado-net.md)' nin ADO.net bölümünde bulunur.</span><span class="sxs-lookup"><span data-stu-id="c5c94-105">The LINQ to ADO.NET documentation is located in the ADO.NET section of the .NET Framework SDK: [LINQ and ADO.NET](../../../../framework/data/adonet/linq-and-ado-net.md).</span></span>
  
 <span data-ttu-id="c5c94-106">Üç ayrı ADO.NET Language-Integrated Query (LINQ) teknolojisi vardır: LINQ to DataSet, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] ve LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="c5c94-106">There are three separate ADO.NET Language-Integrated Query (LINQ) technologies: LINQ to DataSet, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], and LINQ to Entities.</span></span> <span data-ttu-id="c5c94-107">LINQ to DataSet üzerinde daha zengin, iyileştirilmiş sorgulama sağlar <xref:System.Data.DataSet> , [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] SQL Server veritabanı şemalarını doğrudan sorgulayabilir ve LINQ to Entities varlık veri modeli sorgulamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5c94-107">LINQ to DataSet provides richer, optimized querying over the <xref:System.Data.DataSet>, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] enables you to directly query SQL Server database schemas, and LINQ to Entities allows you to query an Entity Data Model.</span></span>  
  
## <a name="linq-to-dataset"></a><span data-ttu-id="c5c94-108">LINQ - DataSet</span><span class="sxs-lookup"><span data-stu-id="c5c94-108">LINQ to DataSet</span></span>  

 <span data-ttu-id="c5c94-109">, <xref:System.Data.DataSet> ADO.net ' deki en yaygın olarak kullanılan bileşenlerden biridir ve ADO.net 'in üzerinde oluşturulduğu, bağlantısı kesilen programlama modelinin temel öğesidir.</span><span class="sxs-lookup"><span data-stu-id="c5c94-109">The <xref:System.Data.DataSet> is one of the most widely used components in ADO.NET, and is a key element of the disconnected programming model that ADO.NET is built on.</span></span> <span data-ttu-id="c5c94-110">Ancak, bu kadar belirgin olsa da, <xref:System.Data.DataSet> sınırlı sorgu yeteneklerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="c5c94-110">Despite this prominence, however, the <xref:System.Data.DataSet> has limited query capabilities.</span></span>  
  
 <span data-ttu-id="c5c94-111">LINQ to DataSet, <xref:System.Data.DataSet> diğer birçok veri kaynağı için kullanılabilen aynı sorgu işlevini kullanarak ' ye daha zengin sorgu özellikleri oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5c94-111">LINQ to DataSet enables you to build richer query capabilities into <xref:System.Data.DataSet> by using the same query functionality that is available for many other data sources.</span></span>  
  
 <span data-ttu-id="c5c94-112">Daha fazla bilgi için bkz. [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="c5c94-112">For more information, see [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md).</span></span>  
  
## <a name="linq-to-sql"></a><span data-ttu-id="c5c94-113">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="c5c94-113">LINQ to SQL</span></span>  

 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] <span data-ttu-id="c5c94-114">ilişkisel verileri nesne olarak yönetmeye yönelik bir çalışma zamanı altyapısı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5c94-114">provides a run-time infrastructure for managing relational data as objects.</span></span> <span data-ttu-id="c5c94-115">[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]' De, bir ilişkisel veritabanının veri modeli, geliştiricinin programlama dilinde ifade edilen bir nesne modeliyle eşleştirilir.</span><span class="sxs-lookup"><span data-stu-id="c5c94-115">In [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], the data model of a relational database is mapped to an object model expressed in the programming language of the developer.</span></span> <span data-ttu-id="c5c94-116">Uygulamayı yürüttüğünüzde, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] nesne modelindeki dil ile tümleşik SORGULARı SQL 'e çevirir ve yürütmek üzere veritabanına gönderir.</span><span class="sxs-lookup"><span data-stu-id="c5c94-116">When you execute the application, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] translates language-integrated queries in the object model into SQL and sends them to the database for execution.</span></span> <span data-ttu-id="c5c94-117">Veritabanı sonuçları döndürdüğünde, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] bunları işleyebileceğiniz nesnelere geri çevirir.</span><span class="sxs-lookup"><span data-stu-id="c5c94-117">When the database returns the results, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] translates them back into objects that you can manipulate.</span></span>  
  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] <span data-ttu-id="c5c94-118">, veritabanında saklı yordamlar ve Kullanıcı tanımlı işlevler ve nesne modelinde devralma için destek içerir.</span><span class="sxs-lookup"><span data-stu-id="c5c94-118">includes support for stored procedures and user-defined functions in the database, and for inheritance in the object model.</span></span>  
  
 <span data-ttu-id="c5c94-119">Daha fazla bilgi için bkz. [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="c5c94-119">For more information, see [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md).</span></span>  
  
## <a name="linq-to-entities"></a><span data-ttu-id="c5c94-120">LINQ - Varlıklar</span><span class="sxs-lookup"><span data-stu-id="c5c94-120">LINQ to Entities</span></span>  

 <span data-ttu-id="c5c94-121">Varlık Veri Modeli, ilişkisel veriler .NET ortamında nesneler olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="c5c94-121">Through the Entity Data Model, relational data is exposed as objects in the .NET environment.</span></span> <span data-ttu-id="c5c94-122">Bu, nesne katmanını LINQ desteği için ideal bir hedef haline getirir ve geliştiricilerin iş mantığını oluşturmak için kullanılan dilden sorguları veritabanına göre formüllemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5c94-122">This makes the object layer an ideal target for LINQ support, allowing developers to formulate queries against the database from the language used to build the business logic.</span></span> <span data-ttu-id="c5c94-123">Bu yetenek LINQ to Entities olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="c5c94-123">This capability is known as LINQ to Entities.</span></span> <span data-ttu-id="c5c94-124">Daha fazla bilgi için bkz. [LINQ to Entities](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md) .</span><span class="sxs-lookup"><span data-stu-id="c5c94-124">See [LINQ to Entities](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md) for more information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5c94-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c5c94-125">See also</span></span>

- [<span data-ttu-id="c5c94-126">LINQ ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c5c94-126">LINQ and ADO.NET</span></span>](../../../../framework/data/adonet/linq-and-ado-net.md)
- [<span data-ttu-id="c5c94-127">Dil ile tümleşik sorgu (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c5c94-127">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](index.md)
