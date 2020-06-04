---
title: XML Ağaçlarını Sorgulama
ms.date: 07/20/2015
ms.assetid: 2e35c1ab-08c8-4378-9ca8-8ff344756eda
ms.openlocfilehash: 22e3dd873e2be8381f3d8da8f7c4284d09e45543
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411876"
---
# <a name="querying-xml-trees-visual-basic"></a><span data-ttu-id="ad846-102">XML ağaçlarını sorgulama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ad846-102">Querying XML Trees (Visual Basic)</span></span>
<span data-ttu-id="ad846-103">Bu bölümde sorgu örnekleri verilmiştir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ad846-103">This section provides examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
 <span data-ttu-id="ad846-104">LINQ sorguları yazma hakkında daha fazla bilgi için bkz. [VISUAL BASIC LINQ Ile çalışmaya](getting-started-with-linq.md)başlama.</span><span class="sxs-lookup"><span data-stu-id="ad846-104">For more information about writing LINQ queries, see [Getting Started with LINQ in Visual Basic](getting-started-with-linq.md).</span></span>  
  
 <span data-ttu-id="ad846-105">Bir XML ağacı örnekledikten sonra, verileri yazma, ağaçtan veri ayıklamaya yönelik en etkili yoldur.</span><span class="sxs-lookup"><span data-stu-id="ad846-105">After you have instantiated an XML tree, writing queries is the most effective way to extract data from the tree.</span></span> <span data-ttu-id="ad846-106">Ayrıca, işlevsel oluşturma ile birlikte sorgulama, orijinal belgeden farklı bir şekle sahip yeni bir XML belgesi oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="ad846-106">Also, querying combined with functional construction enables you to generate a new XML document that has a different shape from the original document.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ad846-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="ad846-107">In This Section</span></span>  
  
|<span data-ttu-id="ad846-108">Konu başlığı</span><span class="sxs-lookup"><span data-stu-id="ad846-108">Topic</span></span>|<span data-ttu-id="ad846-109">Description</span><span class="sxs-lookup"><span data-stu-id="ad846-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="ad846-110">Temel sorgular (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ad846-110">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](basic-queries-linq-to-xml.md)|<span data-ttu-id="ad846-111">XML ağaçlarının sorgulanmasına ilişkin yaygın örnekler sağlar.</span><span class="sxs-lookup"><span data-stu-id="ad846-111">Provides common examples of querying XML trees.</span></span>|  
|[<span data-ttu-id="ad846-112">Tahminler ve dönüşümler (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ad846-112">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](projections-and-transformations-linq-to-xml.md)|<span data-ttu-id="ad846-113">XML ağaçlarını yansıtma ve dönüştürme yaygın örneklerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="ad846-113">Provides common examples of projecting from and transforming XML trees.</span></span>|  
|[<span data-ttu-id="ad846-114">Gelişmiş sorgu teknikleri (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ad846-114">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](advanced-query-techniques-linq-to-xml.md)|<span data-ttu-id="ad846-115">Daha Gelişmiş senaryolarda yararlı olan sorgu teknikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="ad846-115">Provides query techniques that are useful in more advanced scenarios.</span></span>|  
|[<span data-ttu-id="ad846-116">XPath kullanıcıları için LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ad846-116">LINQ to XML for XPath Users (Visual Basic)</span></span>](linq-to-xml-for-xpath-users.md)|<span data-ttu-id="ad846-117">Bir dizi XPath ifadesi ve bunların [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] eşdeğerlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ad846-117">Presents a number of XPath expressions and their [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] equivalents.</span></span>|  
|[<span data-ttu-id="ad846-118">XML 'nin saf Işlevsel dönüştürmeleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ad846-118">Pure Functional Transformations of XML (Visual Basic)</span></span>](pure-functional-transformations-of-xml.md)|<span data-ttu-id="ad846-119">İşlevsel programlama stilinde sorgu yazma konusunda küçük bir öğretici sunar.</span><span class="sxs-lookup"><span data-stu-id="ad846-119">Presents a small tutorial on writing queries in the style of functional programming.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ad846-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ad846-120">See also</span></span>

- [<span data-ttu-id="ad846-121">Programlama Kılavuzu (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ad846-121">Programming Guide (LINQ to XML) (Visual Basic)</span></span>](programming-guide-linq-to-xml.md)
- [<span data-ttu-id="ad846-122">Visual Basic'te LINQ'e Başlarken</span><span class="sxs-lookup"><span data-stu-id="ad846-122">Getting Started with LINQ in Visual Basic</span></span>](getting-started-with-linq.md)
