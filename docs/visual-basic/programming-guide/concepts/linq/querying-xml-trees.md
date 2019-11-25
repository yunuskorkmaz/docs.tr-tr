---
title: XML Ağaçlarını Sorgulama
ms.date: 07/20/2015
ms.assetid: 2e35c1ab-08c8-4378-9ca8-8ff344756eda
ms.openlocfilehash: c8103820a231ba0fb5e8e7c15b7a2b9e7c996e65
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346575"
---
# <a name="querying-xml-trees-visual-basic"></a><span data-ttu-id="2be61-102">Querying XML Trees (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2be61-102">Querying XML Trees (Visual Basic)</span></span>
<span data-ttu-id="2be61-103">This section provides examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span><span class="sxs-lookup"><span data-stu-id="2be61-103">This section provides examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
 <span data-ttu-id="2be61-104">For more information about writing [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries, see [Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="2be61-104">For more information about writing [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries, see [Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span></span>  
  
 <span data-ttu-id="2be61-105">After you have instantiated an XML tree, writing queries is the most effective way to extract data from the tree.</span><span class="sxs-lookup"><span data-stu-id="2be61-105">After you have instantiated an XML tree, writing queries is the most effective way to extract data from the tree.</span></span> <span data-ttu-id="2be61-106">Also, querying combined with functional construction enables you to generate a new XML document that has a different shape from the original document.</span><span class="sxs-lookup"><span data-stu-id="2be61-106">Also, querying combined with functional construction enables you to generate a new XML document that has a different shape from the original document.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2be61-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="2be61-107">In This Section</span></span>  
  
|<span data-ttu-id="2be61-108">Konu</span><span class="sxs-lookup"><span data-stu-id="2be61-108">Topic</span></span>|<span data-ttu-id="2be61-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2be61-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="2be61-110">Basic Queries (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2be61-110">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)|<span data-ttu-id="2be61-111">Provides common examples of querying XML trees.</span><span class="sxs-lookup"><span data-stu-id="2be61-111">Provides common examples of querying XML trees.</span></span>|  
|[<span data-ttu-id="2be61-112">Projections and Transformations (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2be61-112">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)|<span data-ttu-id="2be61-113">Provides common examples of projecting from and transforming XML trees.</span><span class="sxs-lookup"><span data-stu-id="2be61-113">Provides common examples of projecting from and transforming XML trees.</span></span>|  
|[<span data-ttu-id="2be61-114">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2be61-114">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)|<span data-ttu-id="2be61-115">Provides query techniques that are useful in more advanced scenarios.</span><span class="sxs-lookup"><span data-stu-id="2be61-115">Provides query techniques that are useful in more advanced scenarios.</span></span>|  
|[<span data-ttu-id="2be61-116">LINQ to XML for XPath Users (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2be61-116">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)|<span data-ttu-id="2be61-117">Presents a number of XPath expressions and their [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] equivalents.</span><span class="sxs-lookup"><span data-stu-id="2be61-117">Presents a number of XPath expressions and their [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] equivalents.</span></span>|  
|[<span data-ttu-id="2be61-118">Pure Functional Transformations of XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2be61-118">Pure Functional Transformations of XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)|<span data-ttu-id="2be61-119">Presents a small tutorial on writing queries in the style of functional programming.</span><span class="sxs-lookup"><span data-stu-id="2be61-119">Presents a small tutorial on writing queries in the style of functional programming.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2be61-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2be61-120">See also</span></span>

- [<span data-ttu-id="2be61-121">Programming Guide (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2be61-121">Programming Guide (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
- [<span data-ttu-id="2be61-122">Getting Started with LINQ in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2be61-122">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
