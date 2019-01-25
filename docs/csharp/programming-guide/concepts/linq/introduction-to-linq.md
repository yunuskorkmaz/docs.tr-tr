---
title: Lınq'ye giriş (C#)
ms.date: 07/20/2015
ms.assetid: 54874feb-55e5-4ca8-a9d6-1c1127fd7fb1
ms.openlocfilehash: c74c4d3261354bdd2b8194371b4b37f014397e85
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54626569"
---
# <a name="introduction-to-linq-c"></a><span data-ttu-id="9e025-102">Lınq'ye giriş (C#)</span><span class="sxs-lookup"><span data-stu-id="9e025-102">Introduction to LINQ (C#)</span></span>
<span data-ttu-id="9e025-103">Dil ile tümleşik sorgu (LINQ), bir yenilik .NET Framework sürüm 3.5 bir birine bağlayan dünyanın nesnelerin ve verilerin dünyasında arasındaki boşluk sunulan ' dir.</span><span class="sxs-lookup"><span data-stu-id="9e025-103">Language-Integrated Query (LINQ) is an innovation introduced in the .NET Framework version 3.5 that bridges the gap between the world of objects and the world of data.</span></span>  
  
 <span data-ttu-id="9e025-104">Geleneksel olarak, veri sorguları zaman veya IntelliSense desteği olmadan tür denetimini en basit dizeler derleme olarak ifade edilir.</span><span class="sxs-lookup"><span data-stu-id="9e025-104">Traditionally, queries against data are expressed as simple strings without type checking at compile time or IntelliSense support.</span></span> <span data-ttu-id="9e025-105">Ayrıca, her veri kaynağı türü için bir farklı bir sorgu dili öğrenmek zorunda: SQL veritabanlarını, XML belgeleri, çeşitli Web Hizmetleri ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="9e025-105">Furthermore, you have to learn a different query language for each type of data source: SQL databases, XML documents, various Web services, and so on.</span></span> <span data-ttu-id="9e025-106">LINQ yapar bir *sorgu* bir C# ' de birinci sınıf dil yapısı.</span><span class="sxs-lookup"><span data-stu-id="9e025-106">LINQ makes a *query* a first-class language construct in C#.</span></span> <span data-ttu-id="9e025-107">Dil anahtar sözcükleri ve tanıdık işleçleri kullanarak türü kesin belirlenmiş nesne koleksiyonları sorguları yazmanız.</span><span class="sxs-lookup"><span data-stu-id="9e025-107">You write queries against strongly typed collections of objects by using language keywords and familiar operators.</span></span>  
  
 <span data-ttu-id="9e025-108">LINQ sorguları C# ' de SQL Server veritabanlarını, XML belgeleri, ADO.NET veri kümeleri ve destekleyen tüm nesneleri koleksiyonu için yazabileceğiniz <xref:System.Collections.IEnumerable> veya genel <xref:System.Collections.Generic.IEnumerable%601> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="9e025-108">You can write LINQ queries in C# for SQL Server databases, XML documents, ADO.NET Datasets, and any collection of objects that supports <xref:System.Collections.IEnumerable> or the generic <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="9e025-109">LINQ desteği de, birçok Web Hizmetleri ve diğer veritabanı uygulamaları için üçüncü taraflarca sağlanır.</span><span class="sxs-lookup"><span data-stu-id="9e025-109">LINQ support is also provided by third parties for many Web services and other database implementations.</span></span>  
  
 <span data-ttu-id="9e025-110">LINQ sorguları yeni projeler veya mevcut projeleri olmayan LINQ sorgularında birlikte kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e025-110">You can use LINQ queries in new projects, or alongside non-LINQ queries in existing projects.</span></span> <span data-ttu-id="9e025-111">Projenin .NET Framework 3.5 veya sonraki bir sürümü hedeflemesi tek gereksinim olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="9e025-111">The only requirement is that the project target .NET Framework 3.5 or later.</span></span>  
  
 <span data-ttu-id="9e025-112">Tam tür denetlemesi ve IntelliSense desteği ile hem C# ve Visual Basic'te LINQ sorgusu yalnızca kısmen tamamlanmış bir SQL Server veritabanında Visual Studio'dan aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9e025-112">The following illustration from Visual Studio shows a partially-completed LINQ query against a SQL Server database in both C# and Visual Basic with full type checking and IntelliSense support.</span></span>  
  
 <span data-ttu-id="9e025-113">![LINQ query with Intellisense](../../../../csharp/programming-guide/concepts/linq/media/query_intell.png "Query_Intell")</span><span class="sxs-lookup"><span data-stu-id="9e025-113">![LINQ query with Intellisense](../../../../csharp/programming-guide/concepts/linq/media/query_intell.png "Query_Intell")</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="9e025-114">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="9e025-114">Next Steps</span></span>  
 <span data-ttu-id="9e025-115">Başlarken bölümünde bazı temel kavramları hakkında bilgi sahibi olma LINQ hakkında daha fazla bilgi edinmek için başlangıç [C# üzerinde LINQ ile çalışmaya başlama](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md), ve ardından, olduğu ilgilenen LINQ teknolojisi için belgeleri okuyun:</span><span class="sxs-lookup"><span data-stu-id="9e025-115">To learn more details about LINQ, start by becoming familiar with some basic concepts in the Getting Started section [Getting Started with LINQ in C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md), and then read the documentation for the LINQ technology in which you are interested:</span></span>  
  
-   <span data-ttu-id="9e025-116">SQL Server veritabanları: [LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md)</span><span class="sxs-lookup"><span data-stu-id="9e025-116">SQL Server databases: [LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md)</span></span>  
  
-   <span data-ttu-id="9e025-117">XML belgeleri: [LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="9e025-117">XML documents: [LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)</span></span>  
  
-   <span data-ttu-id="9e025-118">ADO.NET veri kümeleri: [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)</span><span class="sxs-lookup"><span data-stu-id="9e025-118">ADO.NET Datasets: [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)</span></span>  
  
-   <span data-ttu-id="9e025-119">.NET koleksiyonları, dosyaları, dizeleri ve bu şekilde devam eder: [LINQ to Objects'in (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)</span><span class="sxs-lookup"><span data-stu-id="9e025-119">.NET collections, files, strings and so on: [LINQ to Objects (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e025-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9e025-120">See also</span></span>

- [<span data-ttu-id="9e025-121">Dil ile tümleşik sorgu (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="9e025-121">Language-Integrated Query (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/index.md)
