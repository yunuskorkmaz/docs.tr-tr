---
title: XML Ağaçlarını Sorgulama
ms.date: 07/20/2015
ms.assetid: 2e35c1ab-08c8-4378-9ca8-8ff344756eda
ms.openlocfilehash: 643b19a0cfcd2a81c6f685de65979f83ca32d918
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636906"
---
# <a name="querying-xml-trees-visual-basic"></a><span data-ttu-id="72b76-102">XML ağaçlarını sorgulama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="72b76-102">Querying XML Trees (Visual Basic)</span></span>
<span data-ttu-id="72b76-103">Bu bölümde [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgularının örnekleri verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="72b76-103">This section provides examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
 <span data-ttu-id="72b76-104">LINQ sorguları yazma hakkında daha fazla bilgi için bkz. [VISUAL BASIC LINQ Ile çalışmaya](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)başlama.</span><span class="sxs-lookup"><span data-stu-id="72b76-104">For more information about writing LINQ queries, see [Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span></span>  
  
 <span data-ttu-id="72b76-105">Bir XML ağacı örnekledikten sonra, verileri yazma, ağaçtan veri ayıklamaya yönelik en etkili yoldur.</span><span class="sxs-lookup"><span data-stu-id="72b76-105">After you have instantiated an XML tree, writing queries is the most effective way to extract data from the tree.</span></span> <span data-ttu-id="72b76-106">Ayrıca, işlevsel oluşturma ile birlikte sorgulama, orijinal belgeden farklı bir şekle sahip yeni bir XML belgesi oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="72b76-106">Also, querying combined with functional construction enables you to generate a new XML document that has a different shape from the original document.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="72b76-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="72b76-107">In This Section</span></span>  
  
|<span data-ttu-id="72b76-108">Konu</span><span class="sxs-lookup"><span data-stu-id="72b76-108">Topic</span></span>|<span data-ttu-id="72b76-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="72b76-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="72b76-110">Temel sorgular (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="72b76-110">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)|<span data-ttu-id="72b76-111">XML ağaçlarının sorgulanmasına ilişkin yaygın örnekler sağlar.</span><span class="sxs-lookup"><span data-stu-id="72b76-111">Provides common examples of querying XML trees.</span></span>|  
|[<span data-ttu-id="72b76-112">Tahminler ve dönüşümler (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="72b76-112">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)|<span data-ttu-id="72b76-113">XML ağaçlarını yansıtma ve dönüştürme yaygın örneklerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="72b76-113">Provides common examples of projecting from and transforming XML trees.</span></span>|  
|[<span data-ttu-id="72b76-114">Gelişmiş sorgu teknikleri (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="72b76-114">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)|<span data-ttu-id="72b76-115">Daha Gelişmiş senaryolarda yararlı olan sorgu teknikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="72b76-115">Provides query techniques that are useful in more advanced scenarios.</span></span>|  
|[<span data-ttu-id="72b76-116">XPath kullanıcıları için LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="72b76-116">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)|<span data-ttu-id="72b76-117">Bir dizi XPath ifadesi ve bunların [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] eşdeğerlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="72b76-117">Presents a number of XPath expressions and their [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] equivalents.</span></span>|  
|[<span data-ttu-id="72b76-118">XML 'nin saf Işlevsel dönüştürmeleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="72b76-118">Pure Functional Transformations of XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)|<span data-ttu-id="72b76-119">İşlevsel programlama stilinde sorgu yazma konusunda küçük bir öğretici sunar.</span><span class="sxs-lookup"><span data-stu-id="72b76-119">Presents a small tutorial on writing queries in the style of functional programming.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="72b76-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72b76-120">See also</span></span>

- [<span data-ttu-id="72b76-121">Programlama Kılavuzu (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="72b76-121">Programming Guide (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
- [<span data-ttu-id="72b76-122">Visual Basic LINQ ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="72b76-122">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
