---
title: "Bölümleme veri (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 69c59379-b66e-422c-b324-5b5c07760ef7
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0ea305a67765e1b11ceebbf65c48a685024a41f3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="partitioning-data-visual-basic"></a><span data-ttu-id="fcf8f-102">Bölümleme veri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fcf8f-102">Partitioning Data (Visual Basic)</span></span>
<span data-ttu-id="fcf8f-103">LINQ bölümlendirme öğeleri yeniden düzenleme ve bölümlerden biri döndürme olmadan bir giriş sırası iki bölümlere ayırma işlemi ifade eder.</span><span class="sxs-lookup"><span data-stu-id="fcf8f-103">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="fcf8f-104">Aşağıdaki çizim üç farklı bölümleme işlemlerde bir dizi karakter sonuçlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fcf8f-104">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="fcf8f-105">İlk işlemi ilk üç öğeleri dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="fcf8f-105">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="fcf8f-106">İkinci bir işlem ilk üç öğeleri atlar ve kalan öğeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="fcf8f-106">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="fcf8f-107">Üçüncü işlem sırası ilk iki öğeleri atlar ve sonraki üç öğeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="fcf8f-107">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 <span data-ttu-id="fcf8f-108">![LINQ işlemleri bölümleme](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")</span><span class="sxs-lookup"><span data-stu-id="fcf8f-108">![LINQ Partitioning Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")</span></span>  
  
 <span data-ttu-id="fcf8f-109">Dizileri bölüm standart sorgu işleci yöntemler aşağıdaki bölümde listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="fcf8f-109">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="fcf8f-110">İşleçler</span><span class="sxs-lookup"><span data-stu-id="fcf8f-110">Operators</span></span>  
  
|<span data-ttu-id="fcf8f-111">İşleç Adı</span><span class="sxs-lookup"><span data-stu-id="fcf8f-111">Operator Name</span></span>|<span data-ttu-id="fcf8f-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fcf8f-112">Description</span></span>|<span data-ttu-id="fcf8f-113">Visual Basic sorgu ifade sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fcf8f-113">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="fcf8f-114">Daha Fazla Bilgi</span><span class="sxs-lookup"><span data-stu-id="fcf8f-114">More Information</span></span>|  
|-------------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="fcf8f-115">Atla</span><span class="sxs-lookup"><span data-stu-id="fcf8f-115">Skip</span></span>|<span data-ttu-id="fcf8f-116">Öğeleri bir sırada belirtilen konum kadar atlar.</span><span class="sxs-lookup"><span data-stu-id="fcf8f-116">Skips elements up to a specified position in a sequence.</span></span>|`Skip`|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="fcf8f-117">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="fcf8f-117">SkipWhile</span></span>|<span data-ttu-id="fcf8f-118">Bir öğe koşulu karşılamadığı kadar bir koşul işlevine bağlı öğeleri atlar.</span><span class="sxs-lookup"><span data-stu-id="fcf8f-118">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|`Skip While`|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="fcf8f-119">Take</span><span class="sxs-lookup"><span data-stu-id="fcf8f-119">Take</span></span>|<span data-ttu-id="fcf8f-120">Öğeleri bir sırada belirtilen konum kadar sürer.</span><span class="sxs-lookup"><span data-stu-id="fcf8f-120">Takes elements up to a specified position in a sequence.</span></span>|`Take`|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="fcf8f-121">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="fcf8f-121">TakeWhile</span></span>|<span data-ttu-id="fcf8f-122">Bir öğe koşulu karşılamadığı kadar bir koşul işlevine bağlı öğeleri alır.</span><span class="sxs-lookup"><span data-stu-id="fcf8f-122">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|`Take While`|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="fcf8f-123">Sorgu ifade sözdizimi örnekleri</span><span class="sxs-lookup"><span data-stu-id="fcf8f-123">Query Expression Syntax Examples</span></span>  
  
### <a name="skip"></a><span data-ttu-id="fcf8f-124">Atla</span><span class="sxs-lookup"><span data-stu-id="fcf8f-124">Skip</span></span>  
 <span data-ttu-id="fcf8f-125">Aşağıdaki kod örneğinde `Skip` yan tümcesinde [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kalan dizeleri dizideki döndürmeden önce bir dizeler dizisi ilk dört dizelerde üzerinden atlanacak.</span><span class="sxs-lookup"><span data-stu-id="fcf8f-125">The following code example uses the `Skip` clause in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] to skip over the first four strings in an array of strings before returning the remaining strings in the array.</span></span>  
  
 [!code-vb[CsLINQPartitioning#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_1.vb)]  
  
### <a name="skipwhile"></a><span data-ttu-id="fcf8f-126">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="fcf8f-126">SkipWhile</span></span>  
 <span data-ttu-id="fcf8f-127">Aşağıdaki kod örneğinde `Skip While` yan tümcesinde [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] dizenin ilk harfi sırasında bir dizi dizelerde atlamayı için "a".</span><span class="sxs-lookup"><span data-stu-id="fcf8f-127">The following code example uses the `Skip While` clause in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] to skip over the strings in an array while the first letter of the string is "a".</span></span> <span data-ttu-id="fcf8f-128">Dizi kalan dizelerde döndürülür.</span><span class="sxs-lookup"><span data-stu-id="fcf8f-128">The remaining strings in the array are returned.</span></span>  
  
 [!code-vb[CsLINQPartitioning#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_2.vb)]  
  
### <a name="take"></a><span data-ttu-id="fcf8f-129">Take</span><span class="sxs-lookup"><span data-stu-id="fcf8f-129">Take</span></span>  
 <span data-ttu-id="fcf8f-130">Aşağıdaki kod örneğinde `Take` yan tümcesinde [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] bir dizeler dizisi ilk iki dizeyi dönün.</span><span class="sxs-lookup"><span data-stu-id="fcf8f-130">The following code example uses the `Take` clause in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] to return the first two strings in an array of strings.</span></span>  
  
 [!code-vb[CsLINQPartitioning#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_3.vb)]  
  
### <a name="takewhile"></a><span data-ttu-id="fcf8f-131">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="fcf8f-131">TakeWhile</span></span>  
 <span data-ttu-id="fcf8f-132">Aşağıdaki kod örneğinde `Take While` yan tümcesinde [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] beş veya daha az dize uzunluğu iken dizeleri dizisinden dönün.</span><span class="sxs-lookup"><span data-stu-id="fcf8f-132">The following code example uses the `Take While` clause in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] to return strings from an array while the length of the string is five or less.</span></span>  
  
 [!code-vb[CsLINQPartitioning#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="fcf8f-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fcf8f-133">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="fcf8f-134">Standart sorgu işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fcf8f-134">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="fcf8f-135">Skip tümcesi</span><span class="sxs-lookup"><span data-stu-id="fcf8f-135">Skip Clause</span></span>](../../../../visual-basic/language-reference/queries/skip-clause.md)  
 [<span data-ttu-id="fcf8f-136">Skip While tümcesi</span><span class="sxs-lookup"><span data-stu-id="fcf8f-136">Skip While Clause</span></span>](../../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [<span data-ttu-id="fcf8f-137">Take tümcesi</span><span class="sxs-lookup"><span data-stu-id="fcf8f-137">Take Clause</span></span>](../../../../visual-basic/language-reference/queries/take-clause.md)  
 [<span data-ttu-id="fcf8f-138">Take While tümcesi</span><span class="sxs-lookup"><span data-stu-id="fcf8f-138">Take While Clause</span></span>](../../../../visual-basic/language-reference/queries/take-while-clause.md)
