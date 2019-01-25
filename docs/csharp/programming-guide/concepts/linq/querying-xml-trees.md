---
title: XML ağaçlarını sorgulama (C#)
ms.date: 07/20/2015
ms.assetid: 0913d81b-541a-4fd4-9cbf-7ec89fd817ea
ms.openlocfilehash: 71a3d8538d96a9a5c273188a1bbb920ad6fa2d37
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54741736"
---
# <a name="querying-xml-trees-c"></a><span data-ttu-id="e95bb-102">XML ağaçlarını sorgulama (C#)</span><span class="sxs-lookup"><span data-stu-id="e95bb-102">Querying XML Trees (C#)</span></span>
<span data-ttu-id="e95bb-103">Bu bölümdeki örnekler [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgular.</span><span class="sxs-lookup"><span data-stu-id="e95bb-103">This section provides examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
 <span data-ttu-id="e95bb-104">Yazma hakkında daha fazla bilgi için [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgularını görmek [C# üzerinde LINQ ile çalışmaya başlama](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="e95bb-104">For more information about writing [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries, see [Getting Started with LINQ in C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md).</span></span>  
  
 <span data-ttu-id="e95bb-105">Bir XML ağacı örneği sonra sorgu yazma ağaçtan verileri ayıklamak için en etkili yoludur.</span><span class="sxs-lookup"><span data-stu-id="e95bb-105">After you have instantiated an XML tree, writing queries is the most effective way to extract data from the tree.</span></span> <span data-ttu-id="e95bb-106">Ayrıca, işlevsel bir oluşturucuyla birlikte sorgulama, farklı bir şekil asıl belgeden sahip yeni bir XML belgesi oluşturmak sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bb-106">Also, querying combined with functional construction enables you to generate a new XML document that has a different shape from the original document.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e95bb-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="e95bb-107">In This Section</span></span>  
  
|<span data-ttu-id="e95bb-108">Konu</span><span class="sxs-lookup"><span data-stu-id="e95bb-108">Topic</span></span>|<span data-ttu-id="e95bb-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e95bb-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="e95bb-110">Temel sorgular (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="e95bb-110">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)|<span data-ttu-id="e95bb-111">XML ağaçlarını sorgulama ortak örnekler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bb-111">Provides common examples of querying XML trees.</span></span>|  
|[<span data-ttu-id="e95bb-112">Projeksiyonlar ve Dönüşümler (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="e95bb-112">Projections and Transformations (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)|<span data-ttu-id="e95bb-113">XML ağaçlarını dönüştürmek ve gelen yansıtma ortak örnekler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bb-113">Provides common examples of projecting from and transforming XML trees.</span></span>|  
|[<span data-ttu-id="e95bb-114">Gelişmiş sorgu teknikleri (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="e95bb-114">Advanced Query Techniques (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)|<span data-ttu-id="e95bb-115">Daha gelişmiş senaryolarda yararlı olan sorgu teknikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="e95bb-115">Provides query techniques that are useful in more advanced scenarios.</span></span>|  
|[<span data-ttu-id="e95bb-116">LINQ to XML için XPath kullanıcıları (C#)</span><span class="sxs-lookup"><span data-stu-id="e95bb-116">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)|<span data-ttu-id="e95bb-117">XPath ifadeleri sayısını gösterir ve bunların [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] eşdeğerleri.</span><span class="sxs-lookup"><span data-stu-id="e95bb-117">Presents a number of XPath expressions and their [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] equivalents.</span></span>|  
|[<span data-ttu-id="e95bb-118">Saf işlevsel dönüşümlere XML (C#)</span><span class="sxs-lookup"><span data-stu-id="e95bb-118">Pure Functional Transformations of XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)|<span data-ttu-id="e95bb-119">İşlevsel programlama stilinde sorgu yazmakla ilgili küçük bir eğitim sunar.</span><span class="sxs-lookup"><span data-stu-id="e95bb-119">Presents a small tutorial on writing queries in the style of functional programming.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e95bb-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e95bb-120">See also</span></span>

- [<span data-ttu-id="e95bb-121">Programlama Kılavuzu (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="e95bb-121">Programming Guide (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
- [<span data-ttu-id="e95bb-122">C#'de LINQ Kullanmaya Başlama</span><span class="sxs-lookup"><span data-stu-id="e95bb-122">Getting Started with LINQ in C#</span></span>](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
