---
description: 'Hakkında daha fazla bilgi edinin: verileri filtreleme (Visual Basic)'
title: Verileri Filtreleme
ms.date: 07/20/2015
ms.assetid: 7749519a-7edc-49fe-aef9-6a353864af6c
ms.openlocfilehash: 2e259209df35a89eb4730f79ffccfee7cb64b9e9
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100428603"
---
# <a name="filtering-data-visual-basic"></a><span data-ttu-id="bd681-103">Verileri filtreleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bd681-103">Filtering Data (Visual Basic)</span></span>

<span data-ttu-id="bd681-104">Filtreleme, sonuç kümesini yalnızca belirtilen bir koşulu karşılayan öğeleri içerecek şekilde kısıtlama işlemini ifade eder.</span><span class="sxs-lookup"><span data-stu-id="bd681-104">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="bd681-105">Seçim olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="bd681-105">It is also known as selection.</span></span>

<span data-ttu-id="bd681-106">Aşağıdaki çizimde, bir karakter dizisinin filtrelenmesi sonuçları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bd681-106">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="bd681-107">Filtreleme işleminin koşulu, karakterin ' A ' olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="bd681-107">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>

![LINQ filtreleme işlemini gösteren diyagram](./media/filtering-data/linq-filter-operation.png)

<span data-ttu-id="bd681-109">Seçimi gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="bd681-109">The standard query operator methods that perform selection are listed in the following section.</span></span>

## <a name="methods"></a><span data-ttu-id="bd681-110">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="bd681-110">Methods</span></span>

|<span data-ttu-id="bd681-111">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="bd681-111">Method Name</span></span>|<span data-ttu-id="bd681-112">Description</span><span class="sxs-lookup"><span data-stu-id="bd681-112">Description</span></span>|<span data-ttu-id="bd681-113">Sorgu Ifadesi söz dizimini Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bd681-113">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="bd681-114">Daha Fazla Bilgi</span><span class="sxs-lookup"><span data-stu-id="bd681-114">More Information</span></span>|
|-----------------|-----------------|------------------------------------------|----------------------|
|<span data-ttu-id="bd681-115">OfType</span><span class="sxs-lookup"><span data-stu-id="bd681-115">OfType</span></span>|<span data-ttu-id="bd681-116">Belirtilen türe atama becerisine bağlı olarak değerleri seçer.</span><span class="sxs-lookup"><span data-stu-id="bd681-116">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="bd681-117">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="bd681-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|
|<span data-ttu-id="bd681-118">Konum</span><span class="sxs-lookup"><span data-stu-id="bd681-118">Where</span></span>|<span data-ttu-id="bd681-119">Bir koşul işlevini temel alan değerleri seçer.</span><span class="sxs-lookup"><span data-stu-id="bd681-119">Selects values that are based on a predicate function.</span></span>|`Where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-example"></a><span data-ttu-id="bd681-120">Sorgu Ifadesi söz dizimi örneği</span><span class="sxs-lookup"><span data-stu-id="bd681-120">Query Expression Syntax Example</span></span>

<span data-ttu-id="bd681-121">Aşağıdaki örnek, `Where` belirli bir uzunluğa sahip dizelerin bulunduğu bir diziden filtrelemek için öğesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="bd681-121">The following example uses the `Where` to filter from an array those strings that have a specific length.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="bd681-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bd681-122">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="bd681-123">Standart sorgu Işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bd681-123">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="bd681-124">WHERE yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="bd681-124">Where Clause</span></span>](../../../language-reference/queries/where-clause.md)
- [<span data-ttu-id="bd681-125">Nasıl yapılır: sorgu sonuçlarını filtreleme</span><span class="sxs-lookup"><span data-stu-id="bd681-125">How to: Filter Query Results</span></span>](../../language-features/linq/how-to-filter-query-results-by-using-linq.md)
- [<span data-ttu-id="bd681-126">Nasıl yapılır: bir derlemenin meta verilerini yansıma ile sorgulama (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bd681-126">How to: Query An Assembly's Metadata with Reflection (LINQ) (Visual Basic)</span></span>](how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [<span data-ttu-id="bd681-127">Nasıl yapılır: belirtilen bir özniteliğe veya ada sahip dosyaları sorgulama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bd681-127">How to: Query for Files with a Specified Attribute or Name (Visual Basic)</span></span>](how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [<span data-ttu-id="bd681-128">Nasıl yapılır: herhangi bir sözcük veya alana göre metin verilerini sıralama veya filtreleme (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bd681-128">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
