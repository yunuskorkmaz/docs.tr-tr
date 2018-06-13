---
title: Filtre veri (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 7749519a-7edc-49fe-aef9-6a353864af6c
ms.openlocfilehash: d3f44d0b6478103a10fb731988aeebc005cde82e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33644348"
---
# <a name="filtering-data-visual-basic"></a><span data-ttu-id="6e8b9-102">Filtre veri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6e8b9-102">Filtering Data (Visual Basic)</span></span>
<span data-ttu-id="6e8b9-103">Filtreleme, yalnızca belirtilen koşulu karşılıyor öğeleri içeren sonuç kısıtlama işlemi ifade eder.</span><span class="sxs-lookup"><span data-stu-id="6e8b9-103">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="6e8b9-104">Olarak da bilinen, seçim değildir.</span><span class="sxs-lookup"><span data-stu-id="6e8b9-104">It is also known as selection.</span></span>  
  
 <span data-ttu-id="6e8b9-105">Aşağıdaki çizimde bir karakter dizisi filtreleme sonuçlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6e8b9-105">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="6e8b9-106">Filtreleme işlemi için koşulu karakter 'A' olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6e8b9-106">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>  
  
 <span data-ttu-id="6e8b9-107">![İşlemi filtreleme LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_filter.png "LINQ_Filter")</span><span class="sxs-lookup"><span data-stu-id="6e8b9-107">![LINQ Filtering Operation](../../../../csharp/programming-guide/concepts/linq/media/linq_filter.png "LINQ_Filter")</span></span>  
  
 <span data-ttu-id="6e8b9-108">Seçim gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="6e8b9-108">The standard query operator methods that perform selection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6e8b9-109">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6e8b9-109">Methods</span></span>  
  
|<span data-ttu-id="6e8b9-110">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="6e8b9-110">Method Name</span></span>|<span data-ttu-id="6e8b9-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6e8b9-111">Description</span></span>|<span data-ttu-id="6e8b9-112">Visual Basic sorgu ifade sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6e8b9-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="6e8b9-113">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="6e8b9-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="6e8b9-114">OfType</span><span class="sxs-lookup"><span data-stu-id="6e8b9-114">OfType</span></span>|<span data-ttu-id="6e8b9-115">Değerleri, bir belirtilen türe yeteneğini bağlı olarak seçer.</span><span class="sxs-lookup"><span data-stu-id="6e8b9-115">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="6e8b9-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="6e8b9-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="6e8b9-117">Where</span><span class="sxs-lookup"><span data-stu-id="6e8b9-117">Where</span></span>|<span data-ttu-id="6e8b9-118">Bir koşul işlevine dayalı değerleri seçer.</span><span class="sxs-lookup"><span data-stu-id="6e8b9-118">Selects values that are based on a predicate function.</span></span>|`Where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="6e8b9-119">Sorgu ifade sözdizimi örneği</span><span class="sxs-lookup"><span data-stu-id="6e8b9-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="6e8b9-120">Aşağıdaki örnek kullanır `Where` dizisinden belirli bir uzunluğa sahip Bu dizelerin filtre uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="6e8b9-120">The following example uses the `Where` to filter from an array those strings that have a specific length.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6e8b9-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6e8b9-121">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="6e8b9-122">Standart sorgu işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6e8b9-122">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="6e8b9-123">Where Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="6e8b9-123">Where Clause</span></span>](../../../../visual-basic/language-reference/queries/where-clause.md)  
 [<span data-ttu-id="6e8b9-124">Nasıl yapılır: sorgu sonuçlarını filtreleme</span><span class="sxs-lookup"><span data-stu-id="6e8b9-124">How to: Filter Query Results</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-filter-query-results-by-using-linq.md)  
 [<span data-ttu-id="6e8b9-125">Nasıl yapılır: bir derlemenin meta verilerini yansıma (LINQ) (Visual Basic) ile sorgulama</span><span class="sxs-lookup"><span data-stu-id="6e8b9-125">How to: Query An Assembly's Metadata with Reflection (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-assembly-s-metadata-with-reflection-linq.md)  
 [<span data-ttu-id="6e8b9-126">Nasıl yapılır: belirli bir öznitelik veya ad (Visual Basic) sahip dosyaları sorgulama</span><span class="sxs-lookup"><span data-stu-id="6e8b9-126">How to: Query for Files with a Specified Attribute or Name (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)  
 [<span data-ttu-id="6e8b9-127">Nasıl yapılır: sıralama veya filtre metni verilerle herhangi bir sözcük veya alana (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6e8b9-127">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
