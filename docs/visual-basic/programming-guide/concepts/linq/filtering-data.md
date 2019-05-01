---
title: Filtre verileri (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 7749519a-7edc-49fe-aef9-6a353864af6c
ms.openlocfilehash: a673126d928a97bf522783e73fc254debe2a9de8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051464"
---
# <a name="filtering-data-visual-basic"></a><span data-ttu-id="217f4-102">Filtre verileri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="217f4-102">Filtering Data (Visual Basic)</span></span>
<span data-ttu-id="217f4-103">Filtreleme işlemi yalnızca belirli bir koşulu karşılayan öğeleri içeren sonuç kısıtlama ifade eder.</span><span class="sxs-lookup"><span data-stu-id="217f4-103">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="217f4-104">Olarak da bilinir, seçim değildir.</span><span class="sxs-lookup"><span data-stu-id="217f4-104">It is also known as selection.</span></span>  
  
 <span data-ttu-id="217f4-105">Aşağıdaki çizimde bir karakter dizisi filtreleme sonuçlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="217f4-105">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="217f4-106">Filtreleme işlemi için koşulu karakter 'A' olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="217f4-106">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>  
  
 ![Filtreleme işlemi bir LINQ gösteren diyagram](./media/filtering-data/linq-filter-operation.png)  
  
 <span data-ttu-id="217f4-108">Seçimi gerçekleştirmek standart sorgu işleci yöntemleri aşağıdaki bölümünde listelenir.</span><span class="sxs-lookup"><span data-stu-id="217f4-108">The standard query operator methods that perform selection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="217f4-109">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="217f4-109">Methods</span></span>  
  
|<span data-ttu-id="217f4-110">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="217f4-110">Method Name</span></span>|<span data-ttu-id="217f4-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="217f4-111">Description</span></span>|<span data-ttu-id="217f4-112">Visual Basic sorgu ifade sözdizimi</span><span class="sxs-lookup"><span data-stu-id="217f4-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="217f4-113">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="217f4-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="217f4-114">OfType</span><span class="sxs-lookup"><span data-stu-id="217f4-114">OfType</span></span>|<span data-ttu-id="217f4-115">Değerleri belirtilen bir türe yayınlanması için kendi yeteneği bağlı olarak seçer.</span><span class="sxs-lookup"><span data-stu-id="217f4-115">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="217f4-116">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="217f4-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="217f4-117">Where</span><span class="sxs-lookup"><span data-stu-id="217f4-117">Where</span></span>|<span data-ttu-id="217f4-118">Bir koşul işlevini temel alan değerleri seçer.</span><span class="sxs-lookup"><span data-stu-id="217f4-118">Selects values that are based on a predicate function.</span></span>|`Where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="217f4-119">Sorgu ifade sözdizimi örneği</span><span class="sxs-lookup"><span data-stu-id="217f4-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="217f4-120">Aşağıdaki örnekte `Where` bir diziden belirli bir uzunluğa sahip Bu dizelerin filtrelemek için.</span><span class="sxs-lookup"><span data-stu-id="217f4-120">The following example uses the `Where` to filter from an array those strings that have a specific length.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="217f4-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="217f4-121">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="217f4-122">Standart sorgu işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="217f4-122">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="217f4-123">Where Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="217f4-123">Where Clause</span></span>](../../../../visual-basic/language-reference/queries/where-clause.md)
- [<span data-ttu-id="217f4-124">Nasıl yapılır: Sorgu sonuçlarını filtreleme</span><span class="sxs-lookup"><span data-stu-id="217f4-124">How to: Filter Query Results</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-filter-query-results-by-using-linq.md)
- [<span data-ttu-id="217f4-125">Nasıl yapılır: Bir derlemenin meta verilerini (LINQ) (Visual Basic) yansıma ile sorgulama</span><span class="sxs-lookup"><span data-stu-id="217f4-125">How to: Query An Assembly's Metadata with Reflection (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [<span data-ttu-id="217f4-126">Nasıl yapılır: Belirli bir öznitelik veya ada (Visual Basic) sahip dosyaları sorgulama</span><span class="sxs-lookup"><span data-stu-id="217f4-126">How to: Query for Files with a Specified Attribute or Name (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [<span data-ttu-id="217f4-127">Nasıl yapılır: Herhangi bir sözcük veya alana (LINQ) (Visual Basic) göre filtre metin verilerini sıralama veya</span><span class="sxs-lookup"><span data-stu-id="217f4-127">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
