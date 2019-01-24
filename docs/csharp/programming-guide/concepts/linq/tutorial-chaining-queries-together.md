---
title: 'Öğretici: Sorguları birbirine zincirleme (C#)'
ms.date: 07/20/2015
ms.assetid: 44f54444-c4c5-4c23-9d19-986b957b8eda
ms.openlocfilehash: 3beed32aa276f218a80267748e74707941957e53
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54737422"
---
# <a name="tutorial-chaining-queries-together-c"></a><span data-ttu-id="8457b-102">Öğretici: Sorguları birbirine zincirleme (C#)</span><span class="sxs-lookup"><span data-stu-id="8457b-102">Tutorial: Chaining Queries Together (C#)</span></span>
<span data-ttu-id="8457b-103">Bu öğreticide, sorguları birbirine bağladığınızda işleme modeli gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8457b-103">This tutorial illustrates the processing model when you chain queries together.</span></span> <span data-ttu-id="8457b-104">Sorguları birbirine zincirleme işlevsel dönüşümlere yazma önemli bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="8457b-104">Chaining queries together is a key part of writing functional transformations.</span></span> <span data-ttu-id="8457b-105">Tam olarak nasıl zincirleme sorguları iş anlamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="8457b-105">It is important to understand exactly how chained queries work.</span></span>  
  
 <span data-ttu-id="8457b-106">Office Open XML belgeleri işlem sorguları, kapsamlı bir şekilde bu tekniği kullanın.</span><span class="sxs-lookup"><span data-stu-id="8457b-106">The queries that process Office Open XML documents use this technique extensively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8457b-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="8457b-107">In This Section</span></span>  
  
|<span data-ttu-id="8457b-108">Konu</span><span class="sxs-lookup"><span data-stu-id="8457b-108">Topic</span></span>|<span data-ttu-id="8457b-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8457b-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="8457b-110">Ertelenmiş yürütme ve geç değerlendirme LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="8457b-110">Deferred Execution and Lazy Evaluation in LINQ to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)|<span data-ttu-id="8457b-111">Ertelenmiş yürütme ve geç değerlendirme kavramlarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="8457b-111">Describes the concepts of deferred execution and lazy evaluation.</span></span>|  
|[<span data-ttu-id="8457b-112">Ertelenmiş yürütme örneği (C#)</span><span class="sxs-lookup"><span data-stu-id="8457b-112">Deferred Execution Example (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/deferred-execution-example.md)|<span data-ttu-id="8457b-113">Ertelenmiş yürütme örneği sağlar.</span><span class="sxs-lookup"><span data-stu-id="8457b-113">Provides an example of deferred execution.</span></span>|  
|[<span data-ttu-id="8457b-114">Zincirleme örneği sorgular (C#)</span><span class="sxs-lookup"><span data-stu-id="8457b-114">Chaining Queries Example (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/chaining-queries-example.md)|<span data-ttu-id="8457b-115">Nasıl ertelenmiş yürütme gösteren sorguları birbirine zincirleme olduğunda çalışır.</span><span class="sxs-lookup"><span data-stu-id="8457b-115">Shows how deferred execution works when chaining queries together.</span></span>|  
|[<span data-ttu-id="8457b-116">Ara gerçekleştirme (C#)</span><span class="sxs-lookup"><span data-stu-id="8457b-116">Intermediate Materialization (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/intermediate-materialization.md)|<span data-ttu-id="8457b-117">Tanımlar ve Ara gerçekleştirme semantiği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8457b-117">Identifies and illustrates the semantics of intermediate materialization.</span></span>|  
|[<span data-ttu-id="8457b-118">Zincirleme standart sorgu işleçleri (C#)</span><span class="sxs-lookup"><span data-stu-id="8457b-118">Chaining Standard Query Operators Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/chaining-standard-query-operators-together.md)|<span data-ttu-id="8457b-119">Standart sorgu işleçlerinin yavaş semantiği açıklar.</span><span class="sxs-lookup"><span data-stu-id="8457b-119">Describes the lazy semantics of the standard query operators.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8457b-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8457b-120">See also</span></span>

- [<span data-ttu-id="8457b-121">Saf işlevsel dönüşümlere XML (C#)</span><span class="sxs-lookup"><span data-stu-id="8457b-121">Pure Functional Transformations of XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)
