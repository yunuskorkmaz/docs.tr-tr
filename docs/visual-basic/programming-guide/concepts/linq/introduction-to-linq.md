---
title: "Lınq'ye giriş (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c6339c12-9b2d-433e-961c-0d2b7f0091c2
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: de34f27bc520c4e814738e0ba22620ed80f7f23e
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="introduction-to-linq-visual-basic"></a><span data-ttu-id="74826-102">Lınq'ye giriş (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="74826-102">Introduction to LINQ (Visual Basic)</span></span>
<span data-ttu-id="74826-103">Dil ile tümleşik sorgu (LINQ), bir yenilik .NET Framework sürüm 3.5 bu köprüleri world nesneleri ve veri world arasındaki boşluk sunulan ' dir.</span><span class="sxs-lookup"><span data-stu-id="74826-103">Language-Integrated Query (LINQ) is an innovation introduced in the .NET Framework version 3.5 that bridges the gap between the world of objects and the world of data.</span></span>  
  
 <span data-ttu-id="74826-104">Geleneksel olarak, veri sorguları zaman veya IntelliSense desteği tür adresindeki denetlemesi olmadan basit dizeler derleme olarak ifade edilir.</span><span class="sxs-lookup"><span data-stu-id="74826-104">Traditionally, queries against data are expressed as simple strings without type checking at compile time or IntelliSense support.</span></span> <span data-ttu-id="74826-105">Ayrıca, her veri kaynağı türü için farklı sorgu dili öğrenmeniz gerekir: SQL veritabanları, XML belgeleri, çeşitli Web Hizmetleri ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="74826-105">Furthermore, you have to learn a different query language for each type of data source: SQL databases, XML documents, various Web services, and so on.</span></span> <span data-ttu-id="74826-106">LINQ yapar bir *sorgu* Visual Basic'te birinci sınıf dil yapısı.</span><span class="sxs-lookup"><span data-stu-id="74826-106">LINQ makes a *query* a first-class language construct in Visual Basic.</span></span> <span data-ttu-id="74826-107">Dil anahtar sözcükleri ve tanıdık işleçleri kullanarak nesne türü kesin belirlenmiş koleksiyonları sorguları yazma.</span><span class="sxs-lookup"><span data-stu-id="74826-107">You write queries against strongly typed collections of objects by using language keywords and familiar operators.</span></span>  
  
 <span data-ttu-id="74826-108">SQL Server veritabanları, XML belgeleri, ADO.NET veri kümeleri ve destekleyen herhangi bir koleksiyonu nesnelerin Visual Basic'te LINQ sorgularını yazabilirsiniz <xref:System.Collections.IEnumerable> veya genel <xref:System.Collections.Generic.IEnumerable%601> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="74826-108">You can write LINQ queries in Visual Basic for SQL Server databases, XML documents, ADO.NET Datasets, and any collection of objects that supports <xref:System.Collections.IEnumerable> or the generic <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="74826-109">LINQ desteği de birçok Web Hizmetleri ve diğer veritabanı uygulamaları için üçüncü taraflarca sağlanır.</span><span class="sxs-lookup"><span data-stu-id="74826-109">LINQ support is also provided by third parties for many Web services and other database implementations.</span></span>  
  
 <span data-ttu-id="74826-110">Yeni projeler veya mevcut projeleri olmayan LINQ sorgularında yanında LINQ sorgularını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74826-110">You can use LINQ queries in new projects, or alongside non-LINQ queries in existing projects.</span></span> <span data-ttu-id="74826-111">Projeyi .NET Framework 3.5 veya sonrasını hedefleyen tek gereksinimdir.</span><span class="sxs-lookup"><span data-stu-id="74826-111">The only requirement is that the project target .NET Framework 3.5 or later.</span></span>  
  
 <span data-ttu-id="74826-112">Tam tür denetleme ve IntelliSense desteği ile hem C# ve Visual Basic'te bir SQL Server veritabanında bir kısmen tamamlanmış LINQ Sorgu Visual Studio'dan aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="74826-112">The following illustration from Visual Studio shows a partially-completed LINQ query against a SQL Server database in both C# and Visual Basic with full type checking and IntelliSense support.</span></span>  
  
 <span data-ttu-id="74826-113">![IntelliSense ile LINQ sorgusu](../../../../csharp/programming-guide/concepts/linq/media/query_intell.png "Query_Intell")</span><span class="sxs-lookup"><span data-stu-id="74826-113">![LINQ query with Intellisense](../../../../csharp/programming-guide/concepts/linq/media/query_intell.png "Query_Intell")</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="74826-114">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="74826-114">Next Steps</span></span>  
 <span data-ttu-id="74826-115">Başlarken bölümündeki bazı temel kavramları hakkında bilgi sahibi olma LINQ hakkında daha fazla ayrıntı öğrenmek için başlangıç [Visual Basic'te LINQ ile çalışmaya başlama](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md), ve hangi olduğunuz LINQ teknolojisi belgelerini okuyun ilginizi çekiyor:</span><span class="sxs-lookup"><span data-stu-id="74826-115">To learn more details about LINQ, start by becoming familiar with some basic concepts in the Getting Started section [Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md), and then read the documentation for the LINQ technology in which you are interested:</span></span>  
  
-   <span data-ttu-id="74826-116">SQL Server veritabanlarını: [LINQ-SQL](../../../../framework/data/adonet/sql/linq/index.md)</span><span class="sxs-lookup"><span data-stu-id="74826-116">SQL Server databases: [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)</span></span>  
  
-   <span data-ttu-id="74826-117">XML belgeleri: [LINQ-XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="74826-117">XML documents: [LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)</span></span>  
  
-   <span data-ttu-id="74826-118">ADO.NET veri kümeleri: [LINQ-DataSet](../../../../framework/data/adonet/linq-to-dataset.md)</span><span class="sxs-lookup"><span data-stu-id="74826-118">ADO.NET Datasets: [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)</span></span>  
  
-   <span data-ttu-id="74826-119">.NET koleksiyonları, dosyaları, dizeleri vb.: [(Visual Basic) nesnelere LINQ](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)</span><span class="sxs-lookup"><span data-stu-id="74826-119">.NET collections, files, strings and so on: [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74826-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="74826-120">See Also</span></span>  
 [<span data-ttu-id="74826-121">Dil ile tümleşik sorgu (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="74826-121">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/index.md)
