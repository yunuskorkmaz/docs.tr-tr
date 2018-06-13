---
title: Sorgulama XML ağaçları (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 2e35c1ab-08c8-4378-9ca8-8ff344756eda
ms.openlocfilehash: e26ff23d5278bcaaeb2c8e26303c2380bbb1f1e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33645336"
---
# <a name="querying-xml-trees-visual-basic"></a><span data-ttu-id="d0e87-102">Sorgulama XML ağaçları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d0e87-102">Querying XML Trees (Visual Basic)</span></span>
<span data-ttu-id="d0e87-103">Bu bölümde örnekleri [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgular.</span><span class="sxs-lookup"><span data-stu-id="d0e87-103">This section provides examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
 <span data-ttu-id="d0e87-104">Yazma hakkında daha fazla bilgi için [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorguları, bkz: [Visual Basic'te LINQ ile çalışmaya başlama](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="d0e87-104">For more information about writing [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries, see [Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span></span>  
  
 <span data-ttu-id="d0e87-105">Bir XML ağacı örneği sonra sorguları yazma ağacından veri ayıklamak için en etkili yoldur.</span><span class="sxs-lookup"><span data-stu-id="d0e87-105">After you have instantiated an XML tree, writing queries is the most effective way to extract data from the tree.</span></span> <span data-ttu-id="d0e87-106">Ayrıca, işlev oluşturma ile birlikte sorgulama asıl belgeden farklı bir şekli sahip yeni bir XML belgesi oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="d0e87-106">Also, querying combined with functional construction enables you to generate a new XML document that has a different shape from the original document.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d0e87-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="d0e87-107">In This Section</span></span>  
  
|<span data-ttu-id="d0e87-108">Konu</span><span class="sxs-lookup"><span data-stu-id="d0e87-108">Topic</span></span>|<span data-ttu-id="d0e87-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0e87-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="d0e87-110">Temel sorgu (LINQ-XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d0e87-110">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)|<span data-ttu-id="d0e87-111">XML ağaçları sorgulama ortak örnekler verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d0e87-111">Provides common examples of querying XML trees.</span></span>|  
|[<span data-ttu-id="d0e87-112">Projeksiyonlar ve dönüştürmeler (LINQ-XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d0e87-112">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)|<span data-ttu-id="d0e87-113">Gelen yansıtma ve XML ağaçları dönüştürme ortak örnekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="d0e87-113">Provides common examples of projecting from and transforming XML trees.</span></span>|  
|[<span data-ttu-id="d0e87-114">Gelişmiş sorgu teknikler (LINQ-XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d0e87-114">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)|<span data-ttu-id="d0e87-115">Daha gelişmiş senaryolarda kullanışlıdır sorgu teknikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="d0e87-115">Provides query techniques that are useful in more advanced scenarios.</span></span>|  
|[<span data-ttu-id="d0e87-116">LINQ-XML XPath kullanıcıların (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d0e87-116">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)|<span data-ttu-id="d0e87-117">XPath ifadeleri sayısını gösterir ve bunların [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] eşdeğerleri.</span><span class="sxs-lookup"><span data-stu-id="d0e87-117">Presents a number of XPath expressions and their [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] equivalents.</span></span>|  
|[<span data-ttu-id="d0e87-118">Saf işlevsel dönüşümleri XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d0e87-118">Pure Functional Transformations of XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)|<span data-ttu-id="d0e87-119">İşlevsel programlama stilde sorguları yazma küçük bir öğretici gösterir.</span><span class="sxs-lookup"><span data-stu-id="d0e87-119">Presents a small tutorial on writing queries in the style of functional programming.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d0e87-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d0e87-120">See Also</span></span>  
 [<span data-ttu-id="d0e87-121">Programlama Kılavuzu (LINQ-XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d0e87-121">Programming Guide (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)  
 [<span data-ttu-id="d0e87-122">Visual Basic'te Lınq'e Başlarken</span><span class="sxs-lookup"><span data-stu-id="d0e87-122">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
