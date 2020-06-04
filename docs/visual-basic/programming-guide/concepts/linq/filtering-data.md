---
title: Verileri Filtreleme
ms.date: 07/20/2015
ms.assetid: 7749519a-7edc-49fe-aef9-6a353864af6c
ms.openlocfilehash: f7a1aa76dc93cc03952e55f5f8fc3f75176a3f9f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84383423"
---
# <a name="filtering-data-visual-basic"></a><span data-ttu-id="8c65d-102">Verileri filtreleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c65d-102">Filtering Data (Visual Basic)</span></span>

<span data-ttu-id="8c65d-103">Filtreleme, sonuç kümesini yalnızca belirtilen bir koşulu karşılayan öğeleri içerecek şekilde kısıtlama işlemini ifade eder.</span><span class="sxs-lookup"><span data-stu-id="8c65d-103">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="8c65d-104">Seçim olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="8c65d-104">It is also known as selection.</span></span>

<span data-ttu-id="8c65d-105">Aşağıdaki çizimde, bir karakter dizisinin filtrelenmesi sonuçları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8c65d-105">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="8c65d-106">Filtreleme işleminin koşulu, karakterin ' A ' olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8c65d-106">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>

![LINQ filtreleme işlemini gösteren diyagram](./media/filtering-data/linq-filter-operation.png)

<span data-ttu-id="8c65d-108">Seçimi gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="8c65d-108">The standard query operator methods that perform selection are listed in the following section.</span></span>

## <a name="methods"></a><span data-ttu-id="8c65d-109">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8c65d-109">Methods</span></span>

|<span data-ttu-id="8c65d-110">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="8c65d-110">Method Name</span></span>|<span data-ttu-id="8c65d-111">Description</span><span class="sxs-lookup"><span data-stu-id="8c65d-111">Description</span></span>|<span data-ttu-id="8c65d-112">Sorgu Ifadesi söz dizimini Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8c65d-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="8c65d-113">Daha Fazla Bilgi</span><span class="sxs-lookup"><span data-stu-id="8c65d-113">More Information</span></span>|
|-----------------|-----------------|------------------------------------------|----------------------|
|<span data-ttu-id="8c65d-114">OfType</span><span class="sxs-lookup"><span data-stu-id="8c65d-114">OfType</span></span>|<span data-ttu-id="8c65d-115">Belirtilen türe atama becerisine bağlı olarak değerleri seçer.</span><span class="sxs-lookup"><span data-stu-id="8c65d-115">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="8c65d-116">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="8c65d-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|
|<span data-ttu-id="8c65d-117">Konum</span><span class="sxs-lookup"><span data-stu-id="8c65d-117">Where</span></span>|<span data-ttu-id="8c65d-118">Bir koşul işlevini temel alan değerleri seçer.</span><span class="sxs-lookup"><span data-stu-id="8c65d-118">Selects values that are based on a predicate function.</span></span>|`Where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-example"></a><span data-ttu-id="8c65d-119">Sorgu Ifadesi söz dizimi örneği</span><span class="sxs-lookup"><span data-stu-id="8c65d-119">Query Expression Syntax Example</span></span>

<span data-ttu-id="8c65d-120">Aşağıdaki örnek, `Where` belirli bir uzunluğa sahip dizelerin bulunduğu bir diziden filtrelemek için öğesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="8c65d-120">The following example uses the `Where` to filter from an array those strings that have a specific length.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8c65d-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8c65d-121">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="8c65d-122">Standart sorgu Işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c65d-122">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="8c65d-123">WHERE yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="8c65d-123">Where Clause</span></span>](../../../language-reference/queries/where-clause.md)
- [<span data-ttu-id="8c65d-124">Nasıl yapılır: sorgu sonuçlarını filtreleme</span><span class="sxs-lookup"><span data-stu-id="8c65d-124">How to: Filter Query Results</span></span>](../../language-features/linq/how-to-filter-query-results-by-using-linq.md)
- [<span data-ttu-id="8c65d-125">Nasıl yapılır: bir derlemenin meta verilerini yansıma ile sorgulama (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c65d-125">How to: Query An Assembly's Metadata with Reflection (LINQ) (Visual Basic)</span></span>](how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [<span data-ttu-id="8c65d-126">Nasıl yapılır: belirtilen bir özniteliğe veya ada sahip dosyaları sorgulama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c65d-126">How to: Query for Files with a Specified Attribute or Name (Visual Basic)</span></span>](how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [<span data-ttu-id="8c65d-127">Nasıl yapılır: herhangi bir sözcük veya alana göre metin verilerini sıralama veya filtreleme (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c65d-127">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
