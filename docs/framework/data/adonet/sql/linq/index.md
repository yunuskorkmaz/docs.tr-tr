---
title: LINQ - SQL
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73d13345-eece-471a-af40-4cc7a2f11655
caps.latest.revision: 4
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 7f303f5b7a7b8675f7d322c6855f4273ebe826ff
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="linq-to-sql"></a><span data-ttu-id="ddbab-102">LINQ - SQL</span><span class="sxs-lookup"><span data-stu-id="ddbab-102">LINQ to SQL</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="ddbab-103"> bir bileşeni olan [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] ilişkisel veri nesneleri olarak yönetmek için bir çalışma zamanı altyapısı sağlar sürüm 3.5.</span><span class="sxs-lookup"><span data-stu-id="ddbab-103"> is a component of [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] version 3.5 that provides a run-time infrastructure for managing relational data as objects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ddbab-104">İlişkisel veri iki boyutlu tablolar koleksiyonu olarak görüntülenir (*ilişkileri* veya *düz dosyalar*), burada ortak sütunları tabloları birbirleri ile.</span><span class="sxs-lookup"><span data-stu-id="ddbab-104">Relational data appears as a collection of two-dimensional tables (*relations* or *flat files*), where common columns relate tables to each other.</span></span> <span data-ttu-id="ddbab-105">Kullanılacak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] etkili bir şekilde ilişkisel veritabanları temel ilkeleri aşina olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ddbab-105">To use [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] effectively, you must have some familiarity with the underlying principles of relational databases.</span></span>  
  
 <span data-ttu-id="ddbab-106">İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], ilişkisel veritabanı veri modelinin Geliştirici programlama dilinde ifade nesne modeli eşlenir.</span><span class="sxs-lookup"><span data-stu-id="ddbab-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the data model of a relational database is mapped to an object model expressed in the programming language of the developer.</span></span> <span data-ttu-id="ddbab-107">Uygulama çalıştırıldığında [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] SQL'e nesne modelinde dil ile tümleşik sorgu dönüşür ve yürütme için veritabanı gönderir.</span><span class="sxs-lookup"><span data-stu-id="ddbab-107">When the application runs, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates into SQL the language-integrated queries in the object model and sends them to the database for execution.</span></span> <span data-ttu-id="ddbab-108">Veritabanı sonuçları döndürdüğünde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bunları kendi programlama dilinde çalışabilirsiniz nesnelere geri çevirir.</span><span class="sxs-lookup"><span data-stu-id="ddbab-108">When the database returns the results, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates them back to objects that you can work with in your own programming language.</span></span>  
  
 <span data-ttu-id="ddbab-109">Visual Studio genellikle kullanarak geliştiricilerin [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)], özelliklerinin çoğunu gerçekleştirmek için bir kullanıcı arabirimi sağlayan [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ddbab-109">Developers using Visual Studio typically use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)], which provides a user interface for implementing many of the features of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 <span data-ttu-id="ddbab-110">Bu sürümünden belgelere [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] temel yapı taşlarının, işlemleri ve yapı için gereken teknikleri açıklar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="ddbab-110">The documentation that is included with this release of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] describes the basic building blocks, processes, and techniques you need for building [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications.</span></span> <span data-ttu-id="ddbab-111">Microsoft Docs belirli sorunları için arama da yapabilirsiniz ve katılabilirsiniz [LINQ Forumu](http://go.microsoft.com/fwlink/?LinkId=76488), uzmanlarıyla ayrıntılı daha karmaşık konular burada ele.</span><span class="sxs-lookup"><span data-stu-id="ddbab-111">You can also search Microsoft Docs for specific issues, and you can participate in the [LINQ Forum](http://go.microsoft.com/fwlink/?LinkId=76488), where you can discuss more complex topics in detail with experts.</span></span> <span data-ttu-id="ddbab-112">Son olarak, [LINQ-SQL: ilişkisel veri .NET Language-Integrated sorgusu](http://go.microsoft.com/fwlink/?LinkId=93205) incelemeyi ayrıntıları [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] teknolojisi, Visual Basic ve C# kod örnekleri ile tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="ddbab-112">Finally, the [LINQ to SQL: .NET Language-Integrated Query for Relational Data](http://go.microsoft.com/fwlink/?LinkId=93205) white paper details [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology, complete with Visual Basic and C# code examples.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ddbab-113">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="ddbab-113">In This Section</span></span>  
 [<span data-ttu-id="ddbab-114">Başlarken</span><span class="sxs-lookup"><span data-stu-id="ddbab-114">Getting Started</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)  
 <span data-ttu-id="ddbab-115">Sıkıştırılmış bir bakış sağlar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kullanmaya başlama hakkında bilgi ile birlikte [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ddbab-115">Provides a condensed overview of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] along with information about how to get started using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="ddbab-116">Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ddbab-116">Programming Guide</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 <span data-ttu-id="ddbab-117">Eşleme, sorgulama, güncelleştirme, hata ayıklama ve benzer görevler için adımlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="ddbab-117">Provides steps for mapping, querying, updating, debugging, and similar tasks.</span></span>  
  
 [<span data-ttu-id="ddbab-118">Başvuru</span><span class="sxs-lookup"><span data-stu-id="ddbab-118">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)  
 <span data-ttu-id="ddbab-119">Çeşitli yönleri hakkında başvuru bilgileri sağlar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ddbab-119">Provides reference information about several aspects of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="ddbab-120">Konular SQL CLR türü eşleme, standart sorgu işleci çeviri ve daha fazlasını içerir.</span><span class="sxs-lookup"><span data-stu-id="ddbab-120">Topics include SQL-CLR Type Mapping, Standard Query Operator Translation, and more.</span></span>  
  
 [<span data-ttu-id="ddbab-121">Örnekler</span><span class="sxs-lookup"><span data-stu-id="ddbab-121">Samples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/samples.md)  
 <span data-ttu-id="ddbab-122">Visual Basic ve C# örnekleri için bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="ddbab-122">Provides links to Visual Basic and C# samples.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ddbab-123">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="ddbab-123">Related Sections</span></span>  
 [<span data-ttu-id="ddbab-124">LINQ (dil ile tümleşik sorgu)</span><span class="sxs-lookup"><span data-stu-id="ddbab-124">LINQ (Language-Integrated Query)</span></span>](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 <span data-ttu-id="ddbab-125">Genel bir bakış sağlar [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] teknolojileri.</span><span class="sxs-lookup"><span data-stu-id="ddbab-125">Provides an overview of [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] technologies.</span></span>  
  
 [<span data-ttu-id="ddbab-126">LINQ</span><span class="sxs-lookup"><span data-stu-id="ddbab-126">LINQ</span></span>](../../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 <span data-ttu-id="ddbab-127">Açıklar [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] teknolojileri Visual Basic kullanıcıları için.</span><span class="sxs-lookup"><span data-stu-id="ddbab-127">Describes [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] technologies for Visual Basic users.</span></span>  
  
 [<span data-ttu-id="ddbab-128">ADO.NET'e LINQ</span><span class="sxs-lookup"><span data-stu-id="ddbab-128">LINQ to ADO.NET</span></span>](http://msdn.microsoft.com/library/be3297b9-1b54-4d4c-82a8-add0d79c2006)  
 <span data-ttu-id="ddbab-129">Bağlantılar için [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] portal.</span><span class="sxs-lookup"><span data-stu-id="ddbab-129">Links to the [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] portal.</span></span>  
  
 [<span data-ttu-id="ddbab-130">LINQ-SQL izlenecek yollar</span><span class="sxs-lookup"><span data-stu-id="ddbab-130">LINQ to SQL Walkthroughs</span></span>](http://msdn.microsoft.com/library/308e66ac-f704-4e00-9b4e-7af0045a2374)  
 <span data-ttu-id="ddbab-131">İzlenecek yollar için kullanılabilir listeler [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ddbab-131">Lists walkthroughs available for [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="ddbab-132">Örnek Veritabanları İndirme</span><span class="sxs-lookup"><span data-stu-id="ddbab-132">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 <span data-ttu-id="ddbab-133">Belgelerde kullanılan örnek veritabanları indirmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="ddbab-133">Describes how to download sample databases used in the documentation.</span></span>  
  
 [<span data-ttu-id="ddbab-134">LinqDataSource teknoloji genel bakış</span><span class="sxs-lookup"><span data-stu-id="ddbab-134">LinqDataSource Technology Overview</span></span>](http://msdn.microsoft.com/library/104cfc3f-7385-47d3-8a51-830dfa791136)  
 <span data-ttu-id="ddbab-135">Açıklar nasıl <xref:System.Web.UI.WebControls.LinqDataSource> kontrol çıkarır [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)] aracılığıyla Web geliştiricileri için [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] veri kaynağı denetim mimarisi.</span><span class="sxs-lookup"><span data-stu-id="ddbab-135">Describes how the <xref:System.Web.UI.WebControls.LinqDataSource> control exposes [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)] to Web developers through the [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] data-source control architecture.</span></span>
