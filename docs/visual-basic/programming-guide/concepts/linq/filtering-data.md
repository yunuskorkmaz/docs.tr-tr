---
title: Filtre veri (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7749519a-7edc-49fe-aef9-6a353864af6c
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 31e3a4729a98e1f4b588cd415a15fff270587234
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="filtering-data-visual-basic"></a><span data-ttu-id="8749a-102">Filtre veri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8749a-102">Filtering Data (Visual Basic)</span></span>
<span data-ttu-id="8749a-103">Filtreleme, yalnızca belirtilen koşulu karşılıyor öğeleri içeren sonuç kısıtlama işlemi ifade eder.</span><span class="sxs-lookup"><span data-stu-id="8749a-103">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="8749a-104">Olarak da bilinen, seçim değildir.</span><span class="sxs-lookup"><span data-stu-id="8749a-104">It is also known as selection.</span></span>  
  
 <span data-ttu-id="8749a-105">Aşağıdaki çizimde bir karakter dizisi filtreleme sonuçlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8749a-105">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="8749a-106">Filtreleme işlemi için koşulu karakter 'A' olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8749a-106">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>  
  
 <span data-ttu-id="8749a-107">![İşlemi filtreleme LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_filter.png "LINQ_Filter")</span><span class="sxs-lookup"><span data-stu-id="8749a-107">![LINQ Filtering Operation](../../../../csharp/programming-guide/concepts/linq/media/linq_filter.png "LINQ_Filter")</span></span>  
  
 <span data-ttu-id="8749a-108">Seçim gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="8749a-108">The standard query operator methods that perform selection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8749a-109">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8749a-109">Methods</span></span>  
  
|<span data-ttu-id="8749a-110">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="8749a-110">Method Name</span></span>|<span data-ttu-id="8749a-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8749a-111">Description</span></span>|<span data-ttu-id="8749a-112">Visual Basic sorgu ifade sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8749a-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="8749a-113">Daha Fazla Bilgi</span><span class="sxs-lookup"><span data-stu-id="8749a-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="8749a-114">OfType</span><span class="sxs-lookup"><span data-stu-id="8749a-114">OfType</span></span>|<span data-ttu-id="8749a-115">Değerleri, bir belirtilen türe yeteneğini bağlı olarak seçer.</span><span class="sxs-lookup"><span data-stu-id="8749a-115">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="8749a-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="8749a-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="8749a-117">Where</span><span class="sxs-lookup"><span data-stu-id="8749a-117">Where</span></span>|<span data-ttu-id="8749a-118">Bir koşul işlevine dayalı değerleri seçer.</span><span class="sxs-lookup"><span data-stu-id="8749a-118">Selects values that are based on a predicate function.</span></span>|`Where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="8749a-119">Sorgu ifade sözdizimi örneği</span><span class="sxs-lookup"><span data-stu-id="8749a-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="8749a-120">Aşağıdaki örnek kullanır `Where` dizisinden belirli bir uzunluğa sahip Bu dizelerin filtre uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="8749a-120">The following example uses the `Where` to filter from an array those strings that have a specific length.</span></span>  
  
```vb  
Dim words() As String = {"the", "quick", "brown", "fox", "jumps"}  
  
Dim query = From word In words   
            Where word.Length = 3   
            Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In query  
    sb.AppendLine(str)  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' the  
' fox  
```  
  
## <a name="see-also"></a><span data-ttu-id="8749a-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8749a-121">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="8749a-122">Standart sorgu işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8749a-122">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="8749a-123">Burada yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="8749a-123">Where Clause</span></span>](../../../../visual-basic/language-reference/queries/where-clause.md)  
 [<span data-ttu-id="8749a-124">Nasıl yapılır: sorgu sonuçlarını filtreleme</span><span class="sxs-lookup"><span data-stu-id="8749a-124">How to: Filter Query Results</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-filter-query-results-by-using-linq.md)  
 [<span data-ttu-id="8749a-125">Nasıl yapılır: bir derlemenin meta verilerini yansıma (LINQ) (Visual Basic) ile sorgulama</span><span class="sxs-lookup"><span data-stu-id="8749a-125">How to: Query An Assembly's Metadata with Reflection (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-assembly-s-metadata-with-reflection-linq.md)  
 [<span data-ttu-id="8749a-126">Nasıl yapılır: belirli bir öznitelik veya ad (Visual Basic) sahip dosyaları sorgulama</span><span class="sxs-lookup"><span data-stu-id="8749a-126">How to: Query for Files with a Specified Attribute or Name (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)  
 [<span data-ttu-id="8749a-127">Nasıl yapılır: sıralama veya filtre metni verilerle herhangi bir sözcük veya alana (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8749a-127">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
