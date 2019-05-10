---
title: Lınq'ye giriş (Visual Basic)
ms.date: 07/20/2015
ms.assetid: c6339c12-9b2d-433e-961c-0d2b7f0091c2
ms.openlocfilehash: 95c1d99604ba9f87e34b5bb423d42bf97c0cd29e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648791"
---
# <a name="introduction-to-linq-visual-basic"></a><span data-ttu-id="2d938-102">Lınq'ye giriş (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2d938-102">Introduction to LINQ (Visual Basic)</span></span>
<span data-ttu-id="2d938-103">Dil ile tümleşik sorgu (LINQ), bir yenilik .NET Framework sürüm 3.5 bir birine bağlayan dünyanın nesnelerin ve verilerin dünyasında arasındaki boşluk sunulan ' dir.</span><span class="sxs-lookup"><span data-stu-id="2d938-103">Language-Integrated Query (LINQ) is an innovation introduced in the .NET Framework version 3.5 that bridges the gap between the world of objects and the world of data.</span></span>  
  
 <span data-ttu-id="2d938-104">Geleneksel olarak, veri sorguları zaman veya IntelliSense desteği olmadan tür denetimini en basit dizeler derleme olarak ifade edilir.</span><span class="sxs-lookup"><span data-stu-id="2d938-104">Traditionally, queries against data are expressed as simple strings without type checking at compile time or IntelliSense support.</span></span> <span data-ttu-id="2d938-105">Ayrıca, her veri kaynağı türü için bir farklı bir sorgu dili öğrenmek zorunda: SQL veritabanlarını, XML belgeleri, çeşitli Web Hizmetleri ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="2d938-105">Furthermore, you have to learn a different query language for each type of data source: SQL databases, XML documents, various Web services, and so on.</span></span> <span data-ttu-id="2d938-106">LINQ yapar bir *sorgu* Visual Basic'te bir birinci sınıf dil yapısı.</span><span class="sxs-lookup"><span data-stu-id="2d938-106">LINQ makes a *query* a first-class language construct in Visual Basic.</span></span> <span data-ttu-id="2d938-107">Dil anahtar sözcükleri ve tanıdık işleçleri kullanarak türü kesin belirlenmiş nesne koleksiyonları sorguları yazmanız.</span><span class="sxs-lookup"><span data-stu-id="2d938-107">You write queries against strongly typed collections of objects by using language keywords and familiar operators.</span></span>  
  
 <span data-ttu-id="2d938-108">SQL Server veritabanlarını, XML belgeleri, ADO.NET veri kümeleri ve destekleyen herhangi bir koleksiyonu nesnelerin Visual Basic'te LINQ sorgularınızı yazabilirsiniz <xref:System.Collections.IEnumerable> veya genel <xref:System.Collections.Generic.IEnumerable%601> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="2d938-108">You can write LINQ queries in Visual Basic for SQL Server databases, XML documents, ADO.NET Datasets, and any collection of objects that supports <xref:System.Collections.IEnumerable> or the generic <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="2d938-109">LINQ desteği de, birçok Web Hizmetleri ve diğer veritabanı uygulamaları için üçüncü taraflarca sağlanır.</span><span class="sxs-lookup"><span data-stu-id="2d938-109">LINQ support is also provided by third parties for many Web services and other database implementations.</span></span>  
  
 <span data-ttu-id="2d938-110">LINQ sorguları yeni projeler veya mevcut projeleri olmayan LINQ sorgularında birlikte kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2d938-110">You can use LINQ queries in new projects, or alongside non-LINQ queries in existing projects.</span></span> <span data-ttu-id="2d938-111">Projenin .NET Framework 3.5 veya sonraki bir sürümü hedeflemesi tek gereksinim olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="2d938-111">The only requirement is that the project target .NET Framework 3.5 or later.</span></span>  
  
 <span data-ttu-id="2d938-112">Tam tür denetlemesi ve IntelliSense desteği ile hem C# ve Visual Basic'te LINQ sorgusu yalnızca kısmen tamamlanmış bir SQL Server veritabanında Visual Studio'dan aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2d938-112">The following illustration from Visual Studio shows a partially-completed LINQ query against a SQL Server database in both C# and Visual Basic with full type checking and IntelliSense support.</span></span>  
  
 ![Bu shwos IntelliSense ile bir LINQ Sorgu Diyagram.](./media/introduction-to-linq/linq-query-intellisense.png)  
  
## <a name="next-steps"></a><span data-ttu-id="2d938-114">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="2d938-114">Next Steps</span></span>  
 <span data-ttu-id="2d938-115">Başlarken bölümünde bazı temel kavramları hakkında bilgi sahibi olma LINQ hakkında daha fazla bilgi edinmek için başlangıç [Visual Basic'te lınq'e Başlarken](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md), ve ardından, olduğu LINQ teknolojisi belgelerini okuyun ister misiniz:</span><span class="sxs-lookup"><span data-stu-id="2d938-115">To learn more details about LINQ, start by becoming familiar with some basic concepts in the Getting Started section [Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md), and then read the documentation for the LINQ technology in which you are interested:</span></span>  
  
- <span data-ttu-id="2d938-116">SQL Server veritabanları: [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)</span><span class="sxs-lookup"><span data-stu-id="2d938-116">SQL Server databases: [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)</span></span>  
  
- <span data-ttu-id="2d938-117">XML belgeleri: [LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="2d938-117">XML documents: [LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)</span></span>  
  
- <span data-ttu-id="2d938-118">ADO.NET veri kümeleri: [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)</span><span class="sxs-lookup"><span data-stu-id="2d938-118">ADO.NET Datasets: [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)</span></span>  
  
- <span data-ttu-id="2d938-119">.NET koleksiyonları, dosyaları, dizeleri ve bu şekilde devam eder: [LINQ to Objects'in (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)</span><span class="sxs-lookup"><span data-stu-id="2d938-119">.NET collections, files, strings and so on: [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d938-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d938-120">See also</span></span>

- [<span data-ttu-id="2d938-121">Dil ile tümleşik sorgu (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2d938-121">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/index.md)
