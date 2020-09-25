---
title: Verileri filtreleme (C#)
description: Seçim olarak da bilinen filtreleme, bir koşula bağlı olarak sonuçları kısıtlar. C# ' de, filtre uygulayan standart sorgu işleci yöntemleri hakkında bilgi edinin.
ms.date: 07/20/2015
ms.assetid: fbaece0d-0f23-47f7-89c5-f3ea8db692b6
ms.openlocfilehash: 51bf9f930ba67ba07c7c0f357910d5e36014138d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91186048"
---
# <a name="filtering-data-c"></a><span data-ttu-id="681a8-104">Verileri filtreleme (C#)</span><span class="sxs-lookup"><span data-stu-id="681a8-104">Filtering Data (C#)</span></span>

<span data-ttu-id="681a8-105">Filtreleme, sonuç kümesini yalnızca belirtilen bir koşulu karşılayan öğeleri içerecek şekilde kısıtlama işlemini ifade eder.</span><span class="sxs-lookup"><span data-stu-id="681a8-105">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="681a8-106">Seçim olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="681a8-106">It is also known as selection.</span></span>  
  
 <span data-ttu-id="681a8-107">Aşağıdaki çizimde, bir karakter dizisinin filtrelenmesi sonuçları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="681a8-107">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="681a8-108">Filtreleme işleminin koşulu, karakterin ' A ' olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="681a8-108">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>  
  
 ![LINQ filtreleme işlemini gösteren diyagram](./media/filtering-data/linq-filter-operation.png)  
  
 <span data-ttu-id="681a8-110">Seçimi gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="681a8-110">The standard query operator methods that perform selection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="681a8-111">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="681a8-111">Methods</span></span>  
  
|<span data-ttu-id="681a8-112">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="681a8-112">Method Name</span></span>|<span data-ttu-id="681a8-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="681a8-113">Description</span></span>|<span data-ttu-id="681a8-114">C# sorgu Ifadesi sözdizimi</span><span class="sxs-lookup"><span data-stu-id="681a8-114">C# Query Expression Syntax</span></span>|<span data-ttu-id="681a8-115">Daha Fazla Bilgi</span><span class="sxs-lookup"><span data-stu-id="681a8-115">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="681a8-116">OfType</span><span class="sxs-lookup"><span data-stu-id="681a8-116">OfType</span></span>|<span data-ttu-id="681a8-117">Belirtilen türe atama becerisine bağlı olarak değerleri seçer.</span><span class="sxs-lookup"><span data-stu-id="681a8-117">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="681a8-118">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="681a8-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="681a8-119">Konum</span><span class="sxs-lookup"><span data-stu-id="681a8-119">Where</span></span>|<span data-ttu-id="681a8-120">Bir koşul işlevini temel alan değerleri seçer.</span><span class="sxs-lookup"><span data-stu-id="681a8-120">Selects values that are based on a predicate function.</span></span>|`where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="681a8-121">Sorgu Ifadesi söz dizimi örneği</span><span class="sxs-lookup"><span data-stu-id="681a8-121">Query Expression Syntax Example</span></span>  

 <span data-ttu-id="681a8-122">Aşağıdaki örnek, `where` belirli bir uzunluğa sahip dizelerin bulunduğu bir diziden filtrelemek için yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="681a8-122">The following example uses the `where` clause to filter from an array those strings that have a specific length.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="681a8-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="681a8-123">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="681a8-124">Standart sorgu Işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="681a8-124">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="681a8-125">WHERE yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="681a8-125">where clause</span></span>](../../../language-reference/keywords/where-clause.md)
- [<span data-ttu-id="681a8-126">Çalışma zamanında koşul filtrelerini dinamik olarak belirtme</span><span class="sxs-lookup"><span data-stu-id="681a8-126">Dynamically specify predicate filters at runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="681a8-127">Bir derlemenin meta verilerini yansıma ile sorgulama (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="681a8-127">How to query an assembly's metadata with Reflection (LINQ) (C#)</span></span>](./how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [<span data-ttu-id="681a8-128">Belirtilen bir özniteliğe veya ada sahip dosyaları sorgulama (C#)</span><span class="sxs-lookup"><span data-stu-id="681a8-128">How to query for files with a specified attribute or name (C#)</span></span>](./how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [<span data-ttu-id="681a8-129">Her kelime veya alana göre metin verilerini sıralama veya filtreleme (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="681a8-129">How to sort or filter text data by any word or field (LINQ) (C#)</span></span>](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
