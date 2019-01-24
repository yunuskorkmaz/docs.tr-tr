---
title: Filtre verileri (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 7749519a-7edc-49fe-aef9-6a353864af6c
ms.openlocfilehash: d65b9941ceffa7ea23c4ead192ec6b97b7b4ead8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54527841"
---
# <a name="filtering-data-visual-basic"></a><span data-ttu-id="f6d0d-102">Filtre verileri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6d0d-102">Filtering Data (Visual Basic)</span></span>
<span data-ttu-id="f6d0d-103">Filtreleme işlemi yalnızca belirli bir koşulu karşılayan öğeleri içeren sonuç kısıtlama ifade eder.</span><span class="sxs-lookup"><span data-stu-id="f6d0d-103">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="f6d0d-104">Olarak da bilinir, seçim değildir.</span><span class="sxs-lookup"><span data-stu-id="f6d0d-104">It is also known as selection.</span></span>  
  
 <span data-ttu-id="f6d0d-105">Aşağıdaki çizimde bir karakter dizisi filtreleme sonuçlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f6d0d-105">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="f6d0d-106">Filtreleme işlemi için koşulu karakter 'A' olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f6d0d-106">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>  
  
 <span data-ttu-id="f6d0d-107">![Filtreleme işlemi LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_filter.png "LINQ_Filter")</span><span class="sxs-lookup"><span data-stu-id="f6d0d-107">![LINQ Filtering Operation](../../../../csharp/programming-guide/concepts/linq/media/linq_filter.png "LINQ_Filter")</span></span>  
  
 <span data-ttu-id="f6d0d-108">Seçimi gerçekleştirmek standart sorgu işleci yöntemleri aşağıdaki bölümünde listelenir.</span><span class="sxs-lookup"><span data-stu-id="f6d0d-108">The standard query operator methods that perform selection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f6d0d-109">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f6d0d-109">Methods</span></span>  
  
|<span data-ttu-id="f6d0d-110">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="f6d0d-110">Method Name</span></span>|<span data-ttu-id="f6d0d-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f6d0d-111">Description</span></span>|<span data-ttu-id="f6d0d-112">Visual Basic sorgu ifade sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f6d0d-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="f6d0d-113">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="f6d0d-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="f6d0d-114">OfType</span><span class="sxs-lookup"><span data-stu-id="f6d0d-114">OfType</span></span>|<span data-ttu-id="f6d0d-115">Değerleri belirtilen bir türe yayınlanması için kendi yeteneği bağlı olarak seçer.</span><span class="sxs-lookup"><span data-stu-id="f6d0d-115">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="f6d0d-116">Uygulanamaz.</span><span class="sxs-lookup"><span data-stu-id="f6d0d-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f6d0d-117">Where</span><span class="sxs-lookup"><span data-stu-id="f6d0d-117">Where</span></span>|<span data-ttu-id="f6d0d-118">Bir koşul işlevini temel alan değerleri seçer.</span><span class="sxs-lookup"><span data-stu-id="f6d0d-118">Selects values that are based on a predicate function.</span></span>|`Where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="f6d0d-119">Sorgu ifade sözdizimi örneği</span><span class="sxs-lookup"><span data-stu-id="f6d0d-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="f6d0d-120">Aşağıdaki örnekte `Where` bir diziden belirli bir uzunluğa sahip Bu dizelerin filtrelemek için.</span><span class="sxs-lookup"><span data-stu-id="f6d0d-120">The following example uses the `Where` to filter from an array those strings that have a specific length.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f6d0d-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f6d0d-121">See also</span></span>
- <xref:System.Linq>
- [<span data-ttu-id="f6d0d-122">Standart sorgu işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6d0d-122">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="f6d0d-123">Where Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="f6d0d-123">Where Clause</span></span>](../../../../visual-basic/language-reference/queries/where-clause.md)
- [<span data-ttu-id="f6d0d-124">Nasıl yapılır: Sorgu sonuçlarını filtreleme</span><span class="sxs-lookup"><span data-stu-id="f6d0d-124">How to: Filter Query Results</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-filter-query-results-by-using-linq.md)
- [<span data-ttu-id="f6d0d-125">Nasıl yapılır: Bir derlemenin meta verilerini (LINQ) (Visual Basic) yansıma ile sorgulama</span><span class="sxs-lookup"><span data-stu-id="f6d0d-125">How to: Query An Assembly's Metadata with Reflection (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [<span data-ttu-id="f6d0d-126">Nasıl yapılır: Belirli bir öznitelik veya ada (Visual Basic) sahip dosyaları sorgulama</span><span class="sxs-lookup"><span data-stu-id="f6d0d-126">How to: Query for Files with a Specified Attribute or Name (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [<span data-ttu-id="f6d0d-127">Nasıl yapılır: Herhangi bir sözcük veya alana (LINQ) (Visual Basic) göre filtre metin verilerini sıralama veya</span><span class="sxs-lookup"><span data-stu-id="f6d0d-127">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
