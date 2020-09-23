---
title: LINQ'ye Giriş
ms.date: 07/20/2015
ms.assetid: c6339c12-9b2d-433e-961c-0d2b7f0091c2
ms.openlocfilehash: e99da74eb69511b92ddccfb42f8002adc7be83d1
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91098287"
---
# <a name="introduction-to-linq-visual-basic"></a><span data-ttu-id="e953c-102">LINQ 'e giriş (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e953c-102">Introduction to LINQ (Visual Basic)</span></span>

<span data-ttu-id="e953c-103">Dil ile tümleşik sorgu (LINQ), .NET Framework sürüm 3,5 ' de sunulan ve nesnelerin dünyası ve veri dünyası arasındaki boşluğu bağlayan bir yeniliği.</span><span class="sxs-lookup"><span data-stu-id="e953c-103">Language-Integrated Query (LINQ) is an innovation introduced in the .NET Framework version 3.5 that bridges the gap between the world of objects and the world of data.</span></span>  
  
 <span data-ttu-id="e953c-104">Geleneksel olarak, verilere karşı sorgular derleme zamanında veya IntelliSense desteğiyle tür denetlemesi olmadan basit dizeler olarak ifade edilir.</span><span class="sxs-lookup"><span data-stu-id="e953c-104">Traditionally, queries against data are expressed as simple strings without type checking at compile time or IntelliSense support.</span></span> <span data-ttu-id="e953c-105">Ayrıca, her veri kaynağı türü için farklı bir sorgu dili öğrenirsiniz: SQL veritabanları, XML belgeleri, çeşitli Web Hizmetleri ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="e953c-105">Furthermore, you have to learn a different query language for each type of data source: SQL databases, XML documents, various Web services, and so on.</span></span> <span data-ttu-id="e953c-106">LINQ, Visual Basic ' de bir *sorgu* birinci sınıf dil yapısı yapar.</span><span class="sxs-lookup"><span data-stu-id="e953c-106">LINQ makes a *query* a first-class language construct in Visual Basic.</span></span> <span data-ttu-id="e953c-107">Dil anahtar sözcükleri ve tanıdık işleçleri kullanarak, türü kesin belirlenmiş nesne koleksiyonlara karşı sorgular yazarsınız.</span><span class="sxs-lookup"><span data-stu-id="e953c-107">You write queries against strongly typed collections of objects by using language keywords and familiar operators.</span></span>  
  
 <span data-ttu-id="e953c-108">SQL Server veritabanları, XML belgeleri, ADO.NET veri kümeleri ve ya da genel arabirimi destekleyen herhangi bir nesne koleksiyonu için Visual Basic LINQ sorguları yazabilirsiniz <xref:System.Collections.IEnumerable> <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="e953c-108">You can write LINQ queries in Visual Basic for SQL Server databases, XML documents, ADO.NET Datasets, and any collection of objects that supports <xref:System.Collections.IEnumerable> or the generic <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="e953c-109">Ayrıca, LINQ desteği birçok Web hizmeti ve diğer veritabanı uygulamaları için üçüncü taraflar tarafından da sağlanır.</span><span class="sxs-lookup"><span data-stu-id="e953c-109">LINQ support is also provided by third parties for many Web services and other database implementations.</span></span>  
  
 <span data-ttu-id="e953c-110">LINQ sorgularını yeni projelerde veya mevcut projelerde LINQ dışı sorguların yanı sıra kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e953c-110">You can use LINQ queries in new projects, or alongside non-LINQ queries in existing projects.</span></span> <span data-ttu-id="e953c-111">Tek gereksinim, proje hedefinin 3,5 veya üzeri .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e953c-111">The only requirement is that the project target .NET Framework 3.5 or later.</span></span>  
  
 <span data-ttu-id="e953c-112">Visual Studio 'daki aşağıdaki çizimde, hem C# hem de tam tür denetimi ve IntelliSense desteğiyle Visual Basic SQL Server veritabanında kısmen tamamlanmış bir LINQ sorgusu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e953c-112">The following illustration from Visual Studio shows a partially-completed LINQ query against a SQL Server database in both C# and Visual Basic with full type checking and IntelliSense support.</span></span>  
  
 ![IntelliSense ile bir LINQ sorgusu gösteren diyagram.](./media/introduction-to-linq/linq-query-intellisense.png)  
  
## <a name="next-steps"></a><span data-ttu-id="e953c-114">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="e953c-114">Next Steps</span></span>  

 <span data-ttu-id="e953c-115">LINQ hakkında daha fazla bilgi edinmek için, Başlangıç bölümündeki [VISUAL BASIC LINQ Ile çalışmaya](getting-started-with-linq.md)başlama bölümünde bazı temel kavramlara tanıdık giderek başlayın ve ardından ilgilendiğiniz LINQ teknolojisinin belgelerini okuyun:</span><span class="sxs-lookup"><span data-stu-id="e953c-115">To learn more details about LINQ, start by becoming familiar with some basic concepts in the Getting Started section [Getting Started with LINQ in Visual Basic](getting-started-with-linq.md), and then read the documentation for the LINQ technology in which you are interested:</span></span>  
  
- <span data-ttu-id="e953c-116">SQL Server veritabanları: [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)</span><span class="sxs-lookup"><span data-stu-id="e953c-116">SQL Server databases: [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)</span></span>  
  
- <span data-ttu-id="e953c-117">XML belgeleri: [LINQ to XML (Visual Basic)](../../../../standard/linq/linq-xml-overview.md)</span><span class="sxs-lookup"><span data-stu-id="e953c-117">XML documents: [LINQ to XML (Visual Basic)](../../../../standard/linq/linq-xml-overview.md)</span></span>  
  
- <span data-ttu-id="e953c-118">ADO.NET veri kümeleri: [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)</span><span class="sxs-lookup"><span data-stu-id="e953c-118">ADO.NET Datasets: [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)</span></span>  
  
- <span data-ttu-id="e953c-119">.NET koleksiyonları, dosyalar, dizeler ve benzeri: [LINQ to Objects (Visual Basic)](linq-to-objects.md)</span><span class="sxs-lookup"><span data-stu-id="e953c-119">.NET collections, files, strings and so on: [LINQ to Objects (Visual Basic)](linq-to-objects.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e953c-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e953c-120">See also</span></span>

- [<span data-ttu-id="e953c-121">Dil ile tümleşik sorgu (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e953c-121">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](index.md)
