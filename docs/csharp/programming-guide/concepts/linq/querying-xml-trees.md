---
title: "Sorgulama XML ağaçları (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 0913d81b-541a-4fd4-9cbf-7ec89fd817ea
caps.latest.revision: "4"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 66028510b57981879412a1c2a161652adde340bd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="querying-xml-trees-c"></a><span data-ttu-id="44cb4-102">Sorgulama XML ağaçları (C#)</span><span class="sxs-lookup"><span data-stu-id="44cb4-102">Querying XML Trees (C#)</span></span>
<span data-ttu-id="44cb4-103">Bu bölümde örnekleri [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgular.</span><span class="sxs-lookup"><span data-stu-id="44cb4-103">This section provides examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
 <span data-ttu-id="44cb4-104">Yazma hakkında daha fazla bilgi için [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorguları, bkz: [C# üzerinde LINQ ile çalışmaya başlama](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="44cb4-104">For more information about writing [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries, see [Getting Started with LINQ in C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md).</span></span>  
  
 <span data-ttu-id="44cb4-105">Bir XML ağacı örneği sonra sorguları yazma ağacından veri ayıklamak için en etkili yoldur.</span><span class="sxs-lookup"><span data-stu-id="44cb4-105">After you have instantiated an XML tree, writing queries is the most effective way to extract data from the tree.</span></span> <span data-ttu-id="44cb4-106">Ayrıca, işlev oluşturma ile birlikte sorgulama asıl belgeden farklı bir şekli sahip yeni bir XML belgesi oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="44cb4-106">Also, querying combined with functional construction enables you to generate a new XML document that has a different shape from the original document.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="44cb4-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="44cb4-107">In This Section</span></span>  
  
|<span data-ttu-id="44cb4-108">Konu</span><span class="sxs-lookup"><span data-stu-id="44cb4-108">Topic</span></span>|<span data-ttu-id="44cb4-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="44cb4-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="44cb4-110">Temel sorgu (LINQ-XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="44cb4-110">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)|<span data-ttu-id="44cb4-111">XML ağaçları sorgulama ortak örnekler verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="44cb4-111">Provides common examples of querying XML trees.</span></span>|  
|[<span data-ttu-id="44cb4-112">Projeksiyonlar ve dönüştürmeler (LINQ-XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="44cb4-112">Projections and Transformations (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)|<span data-ttu-id="44cb4-113">Gelen yansıtma ve XML ağaçları dönüştürme ortak örnekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="44cb4-113">Provides common examples of projecting from and transforming XML trees.</span></span>|  
|[<span data-ttu-id="44cb4-114">Gelişmiş sorgu teknikler (LINQ-XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="44cb4-114">Advanced Query Techniques (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)|<span data-ttu-id="44cb4-115">Daha gelişmiş senaryolarda kullanışlıdır sorgu teknikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="44cb4-115">Provides query techniques that are useful in more advanced scenarios.</span></span>|  
|[<span data-ttu-id="44cb4-116">LINQ-XML XPath kullanıcıların (C#)</span><span class="sxs-lookup"><span data-stu-id="44cb4-116">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)|<span data-ttu-id="44cb4-117">XPath ifadeleri sayısını gösterir ve bunların [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] eşdeğerleri.</span><span class="sxs-lookup"><span data-stu-id="44cb4-117">Presents a number of XPath expressions and their [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] equivalents.</span></span>|  
|[<span data-ttu-id="44cb4-118">Saf işlevsel dönüşümleri XML (C#)</span><span class="sxs-lookup"><span data-stu-id="44cb4-118">Pure Functional Transformations of XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)|<span data-ttu-id="44cb4-119">İşlevsel programlama stilde sorguları yazma küçük bir öğretici gösterir.</span><span class="sxs-lookup"><span data-stu-id="44cb4-119">Presents a small tutorial on writing queries in the style of functional programming.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="44cb4-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="44cb4-120">See Also</span></span>  
 [<span data-ttu-id="44cb4-121">Programlama Kılavuzu (LINQ-XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="44cb4-121">Programming Guide (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)  
 [<span data-ttu-id="44cb4-122">C# üzerinde LINQ ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="44cb4-122">Getting Started with LINQ in C#</span></span>](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
