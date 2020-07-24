---
title: Verileri filtreleme (C#)
description: Seçim olarak da bilinen filtreleme, bir koşula bağlı olarak sonuçları kısıtlar. C# ' de, filtre uygulayan standart sorgu işleci yöntemleri hakkında bilgi edinin.
ms.date: 07/20/2015
ms.assetid: fbaece0d-0f23-47f7-89c5-f3ea8db692b6
ms.openlocfilehash: f9f6d691da73b566e5135f6692c87ba3a8978005
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103925"
---
# <a name="filtering-data-c"></a><span data-ttu-id="e5ee1-104">Verileri filtreleme (C#)</span><span class="sxs-lookup"><span data-stu-id="e5ee1-104">Filtering Data (C#)</span></span>
<span data-ttu-id="e5ee1-105">Filtreleme, sonuç kümesini yalnızca belirtilen bir koşulu karşılayan öğeleri içerecek şekilde kısıtlama işlemini ifade eder.</span><span class="sxs-lookup"><span data-stu-id="e5ee1-105">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="e5ee1-106">Seçim olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="e5ee1-106">It is also known as selection.</span></span>  
  
 <span data-ttu-id="e5ee1-107">Aşağıdaki çizimde, bir karakter dizisinin filtrelenmesi sonuçları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e5ee1-107">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="e5ee1-108">Filtreleme işleminin koşulu, karakterin ' A ' olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e5ee1-108">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>  
  
 ![LINQ filtreleme işlemini gösteren diyagram](./media/filtering-data/linq-filter-operation.png)  
  
 <span data-ttu-id="e5ee1-110">Seçimi gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="e5ee1-110">The standard query operator methods that perform selection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e5ee1-111">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e5ee1-111">Methods</span></span>  
  
|<span data-ttu-id="e5ee1-112">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="e5ee1-112">Method Name</span></span>|<span data-ttu-id="e5ee1-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e5ee1-113">Description</span></span>|<span data-ttu-id="e5ee1-114">C# sorgu Ifadesi sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e5ee1-114">C# Query Expression Syntax</span></span>|<span data-ttu-id="e5ee1-115">Daha Fazla Bilgi</span><span class="sxs-lookup"><span data-stu-id="e5ee1-115">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="e5ee1-116">OfType</span><span class="sxs-lookup"><span data-stu-id="e5ee1-116">OfType</span></span>|<span data-ttu-id="e5ee1-117">Belirtilen türe atama becerisine bağlı olarak değerleri seçer.</span><span class="sxs-lookup"><span data-stu-id="e5ee1-117">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="e5ee1-118">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="e5ee1-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="e5ee1-119">Konum</span><span class="sxs-lookup"><span data-stu-id="e5ee1-119">Where</span></span>|<span data-ttu-id="e5ee1-120">Bir koşul işlevini temel alan değerleri seçer.</span><span class="sxs-lookup"><span data-stu-id="e5ee1-120">Selects values that are based on a predicate function.</span></span>|`where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="e5ee1-121">Sorgu Ifadesi söz dizimi örneği</span><span class="sxs-lookup"><span data-stu-id="e5ee1-121">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="e5ee1-122">Aşağıdaki örnek, `where` belirli bir uzunluğa sahip dizelerin bulunduğu bir diziden filtrelemek için yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="e5ee1-122">The following example uses the `where` clause to filter from an array those strings that have a specific length.</span></span>  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            where word.Length == 3  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    fox  
*/  
```  
  
## <a name="see-also"></a><span data-ttu-id="e5ee1-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5ee1-123">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="e5ee1-124">Standart sorgu Işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="e5ee1-124">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="e5ee1-125">where tümcesi</span><span class="sxs-lookup"><span data-stu-id="e5ee1-125">where clause</span></span>](../../../language-reference/keywords/where-clause.md)
- [<span data-ttu-id="e5ee1-126">Çalışma zamanında koşul filtrelerini dinamik olarak belirtme</span><span class="sxs-lookup"><span data-stu-id="e5ee1-126">Dynamically specify predicate filters at runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="e5ee1-127">Bir derlemenin meta verilerini yansıma ile sorgulama (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="e5ee1-127">How to query an assembly's metadata with Reflection (LINQ) (C#)</span></span>](./how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [<span data-ttu-id="e5ee1-128">Belirtilen bir özniteliğe veya ada sahip dosyaları sorgulama (C#)</span><span class="sxs-lookup"><span data-stu-id="e5ee1-128">How to query for files with a specified attribute or name (C#)</span></span>](./how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [<span data-ttu-id="e5ee1-129">Her kelime veya alana göre metin verilerini sıralama veya filtreleme (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="e5ee1-129">How to sort or filter text data by any word or field (LINQ) (C#)</span></span>](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
