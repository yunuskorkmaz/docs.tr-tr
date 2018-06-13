---
title: Lınq'ye giriş (C#)
ms.date: 07/20/2015
ms.assetid: 54874feb-55e5-4ca8-a9d6-1c1127fd7fb1
ms.openlocfilehash: 3c32c20efec55568a668c5dba55baf8f3ebbee7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33323322"
---
# <a name="introduction-to-linq-c"></a><span data-ttu-id="a75c4-102">Lınq'ye giriş (C#)</span><span class="sxs-lookup"><span data-stu-id="a75c4-102">Introduction to LINQ (C#)</span></span>
<span data-ttu-id="a75c4-103">Dil ile tümleşik sorgu (LINQ), bir yenilik .NET Framework sürüm 3.5 bu köprüleri world nesneleri ve veri world arasındaki boşluk sunulan ' dir.</span><span class="sxs-lookup"><span data-stu-id="a75c4-103">Language-Integrated Query (LINQ) is an innovation introduced in the .NET Framework version 3.5 that bridges the gap between the world of objects and the world of data.</span></span>  
  
 <span data-ttu-id="a75c4-104">Geleneksel olarak, veri sorguları zaman veya IntelliSense desteği tür adresindeki denetlemesi olmadan basit dizeler derleme olarak ifade edilir.</span><span class="sxs-lookup"><span data-stu-id="a75c4-104">Traditionally, queries against data are expressed as simple strings without type checking at compile time or IntelliSense support.</span></span> <span data-ttu-id="a75c4-105">Ayrıca, her veri kaynağı türü için farklı sorgu dili öğrenmeniz gerekir: SQL veritabanları, XML belgeleri, çeşitli Web Hizmetleri ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="a75c4-105">Furthermore, you have to learn a different query language for each type of data source: SQL databases, XML documents, various Web services, and so on.</span></span> <span data-ttu-id="a75c4-106">LINQ yapar bir *sorgu* C# birinci sınıf dil yapısı.</span><span class="sxs-lookup"><span data-stu-id="a75c4-106">LINQ makes a *query* a first-class language construct in C#.</span></span> <span data-ttu-id="a75c4-107">Dil anahtar sözcükleri ve tanıdık işleçleri kullanarak nesne türü kesin belirlenmiş koleksiyonları sorguları yazma.</span><span class="sxs-lookup"><span data-stu-id="a75c4-107">You write queries against strongly typed collections of objects by using language keywords and familiar operators.</span></span>  
  
 <span data-ttu-id="a75c4-108">LINQ sorgularını C# ' de SQL Server veritabanları, XML belgeleri, ADO.NET veri kümeleri ve destekleyen herhangi bir koleksiyonu nesnelerin yazabileceğiniz <xref:System.Collections.IEnumerable> veya genel <xref:System.Collections.Generic.IEnumerable%601> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="a75c4-108">You can write LINQ queries in C# for SQL Server databases, XML documents, ADO.NET Datasets, and any collection of objects that supports <xref:System.Collections.IEnumerable> or the generic <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="a75c4-109">LINQ desteği de birçok Web Hizmetleri ve diğer veritabanı uygulamaları için üçüncü taraflarca sağlanır.</span><span class="sxs-lookup"><span data-stu-id="a75c4-109">LINQ support is also provided by third parties for many Web services and other database implementations.</span></span>  
  
 <span data-ttu-id="a75c4-110">Yeni projeler veya mevcut projeleri olmayan LINQ sorgularında yanında LINQ sorgularını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a75c4-110">You can use LINQ queries in new projects, or alongside non-LINQ queries in existing projects.</span></span> <span data-ttu-id="a75c4-111">Projeyi .NET Framework 3.5 veya sonrasını hedefleyen tek gereksinimdir.</span><span class="sxs-lookup"><span data-stu-id="a75c4-111">The only requirement is that the project target .NET Framework 3.5 or later.</span></span>  
  
 <span data-ttu-id="a75c4-112">Tam tür denetleme ve IntelliSense desteği ile hem C# ve Visual Basic'te bir SQL Server veritabanında bir kısmen tamamlanmış LINQ Sorgu Visual Studio'dan aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a75c4-112">The following illustration from Visual Studio shows a partially-completed LINQ query against a SQL Server database in both C# and Visual Basic with full type checking and IntelliSense support.</span></span>  
  
 <span data-ttu-id="a75c4-113">![IntelliSense ile LINQ sorgusu](../../../../csharp/programming-guide/concepts/linq/media/query_intell.png "Query_Intell")</span><span class="sxs-lookup"><span data-stu-id="a75c4-113">![LINQ query with Intellisense](../../../../csharp/programming-guide/concepts/linq/media/query_intell.png "Query_Intell")</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="a75c4-114">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="a75c4-114">Next Steps</span></span>  
 <span data-ttu-id="a75c4-115">Başlarken bölümündeki bazı temel kavramları hakkında bilgi sahibi olma LINQ hakkında daha fazla ayrıntı öğrenmek için başlangıç [C# üzerinde LINQ ile çalışmaya başlama](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md), ve hangi, ilgi LINQ teknolojisi belgelerine bakın:</span><span class="sxs-lookup"><span data-stu-id="a75c4-115">To learn more details about LINQ, start by becoming familiar with some basic concepts in the Getting Started section [Getting Started with LINQ in C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md), and then read the documentation for the LINQ technology in which you are interested:</span></span>  
  
-   <span data-ttu-id="a75c4-116">SQL Server veritabanlarını: [LINQ-SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md)</span><span class="sxs-lookup"><span data-stu-id="a75c4-116">SQL Server databases: [LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md)</span></span>  
  
-   <span data-ttu-id="a75c4-117">XML belgeleri: [LINQ-XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="a75c4-117">XML documents: [LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)</span></span>  
  
-   <span data-ttu-id="a75c4-118">ADO.NET veri kümeleri: [LINQ-DataSet](../../../../framework/data/adonet/linq-to-dataset.md)</span><span class="sxs-lookup"><span data-stu-id="a75c4-118">ADO.NET Datasets: [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)</span></span>  
  
-   <span data-ttu-id="a75c4-119">.NET koleksiyonları, dosyaları, dizeleri vb.: [(C#) nesnelere LINQ](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)</span><span class="sxs-lookup"><span data-stu-id="a75c4-119">.NET collections, files, strings and so on: [LINQ to Objects (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a75c4-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a75c4-120">See Also</span></span>  
 [<span data-ttu-id="a75c4-121">Dil ile tümleşik sorgu (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="a75c4-121">Language-Integrated Query (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/index.md)
