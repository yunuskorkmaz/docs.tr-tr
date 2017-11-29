---
title: "Öğretici: Sorguları birlikte (C#) zincirleme"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 44f54444-c4c5-4c23-9d19-986b957b8eda
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 08196f4780e566cc05e36b6cfe78caad3e9c96a1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="tutorial-chaining-queries-together-c"></a><span data-ttu-id="05907-102">Öğretici: Sorguları birlikte (C#) zincirleme</span><span class="sxs-lookup"><span data-stu-id="05907-102">Tutorial: Chaining Queries Together (C#)</span></span>
<span data-ttu-id="05907-103">Bu öğretici sorguları bir araya zincirleyebilirsiniz işleme modeli gösterir.</span><span class="sxs-lookup"><span data-stu-id="05907-103">This tutorial illustrates the processing model when you chain queries together.</span></span> <span data-ttu-id="05907-104">Sorguları birlikte zincirleme işlevsel dönüşümleri yazmaya önemli bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="05907-104">Chaining queries together is a key part of writing functional transformations.</span></span> <span data-ttu-id="05907-105">Tam olarak nasıl zincirleme sorguları iş anlamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="05907-105">It is important to understand exactly how chained queries work.</span></span>  
  
 <span data-ttu-id="05907-106">Office Açık XML belgeleri işlemek sorguları bu tekniği yaygın kullanın.</span><span class="sxs-lookup"><span data-stu-id="05907-106">The queries that process Office Open XML documents use this technique extensively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="05907-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="05907-107">In This Section</span></span>  
  
|<span data-ttu-id="05907-108">Konu</span><span class="sxs-lookup"><span data-stu-id="05907-108">Topic</span></span>|<span data-ttu-id="05907-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="05907-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="05907-110">Ertelenmiş yürütme ve geç değerlendirme LINQ-XML (C#)</span><span class="sxs-lookup"><span data-stu-id="05907-110">Deferred Execution and Lazy Evaluation in LINQ to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)|<span data-ttu-id="05907-111">Ertelenmiş yürütme ve geç değerlendirme kavramlarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="05907-111">Describes the concepts of deferred execution and lazy evaluation.</span></span>|  
|[<span data-ttu-id="05907-112">Ertelenmiş yürütme örneği (C#)</span><span class="sxs-lookup"><span data-stu-id="05907-112">Deferred Execution Example (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/deferred-execution-example.md)|<span data-ttu-id="05907-113">Ertelenmiş yürütme ilişkin bir örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="05907-113">Provides an example of deferred execution.</span></span>|  
|[<span data-ttu-id="05907-114">Zincirleme sorguları örnek (C#)</span><span class="sxs-lookup"><span data-stu-id="05907-114">Chaining Queries Example (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/chaining-queries-example.md)|<span data-ttu-id="05907-115">Nasıl ertelenmiş yürütme gösterir sorguları birlikte zincirleme olduğunda çalışır.</span><span class="sxs-lookup"><span data-stu-id="05907-115">Shows how deferred execution works when chaining queries together.</span></span>|  
|[<span data-ttu-id="05907-116">Ara Materialization (C#)</span><span class="sxs-lookup"><span data-stu-id="05907-116">Intermediate Materialization (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/intermediate-materialization.md)|<span data-ttu-id="05907-117">Tanımlar ve Ara materialization semantiği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="05907-117">Identifies and illustrates the semantics of intermediate materialization.</span></span>|  
|[<span data-ttu-id="05907-118">Zincirleme standart sorgu işleçleri birlikte (C#)</span><span class="sxs-lookup"><span data-stu-id="05907-118">Chaining Standard Query Operators Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/chaining-standard-query-operators-together.md)|<span data-ttu-id="05907-119">Standart sorgu işleçleri yavaş semantiği açıklar.</span><span class="sxs-lookup"><span data-stu-id="05907-119">Describes the lazy semantics of the standard query operators.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="05907-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="05907-120">See Also</span></span>  
 [<span data-ttu-id="05907-121">Saf işlevsel dönüşümleri XML (C#)</span><span class="sxs-lookup"><span data-stu-id="05907-121">Pure Functional Transformations of XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)
