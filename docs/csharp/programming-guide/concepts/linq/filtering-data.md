---
title: Verileri filtreleme (C#)
ms.date: 07/20/2015
ms.assetid: fbaece0d-0f23-47f7-89c5-f3ea8db692b6
ms.openlocfilehash: 61d80674fd858063e77749342a33d714e3a57c6e
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826073"
---
# <a name="filtering-data-c"></a><span data-ttu-id="56827-102">Verileri filtreleme (C#)</span><span class="sxs-lookup"><span data-stu-id="56827-102">Filtering Data (C#)</span></span>
<span data-ttu-id="56827-103">Filtreleme işlemi yalnızca belirli bir koşulu karşılayan öğeleri içeren sonuç kısıtlama ifade eder.</span><span class="sxs-lookup"><span data-stu-id="56827-103">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="56827-104">Olarak da bilinir, seçim değildir.</span><span class="sxs-lookup"><span data-stu-id="56827-104">It is also known as selection.</span></span>  
  
 <span data-ttu-id="56827-105">Aşağıdaki çizimde bir karakter dizisi filtreleme sonuçlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="56827-105">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="56827-106">Filtreleme işlemi için koşulu karakter 'A' olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="56827-106">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>  
  
 ![Filtreleme işlemi bir LINQ gösteren diyagram](./media/filtering-data/linq-filter-operation.png)  
  
 <span data-ttu-id="56827-108">Seçimi gerçekleştirmek standart sorgu işleci yöntemleri aşağıdaki bölümünde listelenir.</span><span class="sxs-lookup"><span data-stu-id="56827-108">The standard query operator methods that perform selection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="56827-109">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="56827-109">Methods</span></span>  
  
|<span data-ttu-id="56827-110">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="56827-110">Method Name</span></span>|<span data-ttu-id="56827-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="56827-111">Description</span></span>|<span data-ttu-id="56827-112">C# sorgu ifade sözdizimi</span><span class="sxs-lookup"><span data-stu-id="56827-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="56827-113">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="56827-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="56827-114">OfType</span><span class="sxs-lookup"><span data-stu-id="56827-114">OfType</span></span>|<span data-ttu-id="56827-115">Değerleri belirtilen bir türe yayınlanması için kendi yeteneği bağlı olarak seçer.</span><span class="sxs-lookup"><span data-stu-id="56827-115">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="56827-116">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="56827-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="56827-117">Where</span><span class="sxs-lookup"><span data-stu-id="56827-117">Where</span></span>|<span data-ttu-id="56827-118">Bir koşul işlevini temel alan değerleri seçer.</span><span class="sxs-lookup"><span data-stu-id="56827-118">Selects values that are based on a predicate function.</span></span>|`where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="56827-119">Sorgu ifade sözdizimi örneği</span><span class="sxs-lookup"><span data-stu-id="56827-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="56827-120">Aşağıdaki örnekte `where` bir diziden belirli bir uzunluğa sahip Bu dizelerin filtrelemek için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="56827-120">The following example uses the `where` clause to filter from an array those strings that have a specific length.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="56827-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="56827-121">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="56827-122">Standart sorgu işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="56827-122">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="56827-123">where yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="56827-123">where clause</span></span>](../../../../csharp/language-reference/keywords/where-clause.md)
- [<span data-ttu-id="56827-124">Nasıl yapılır: Çalışma zamanında koşul filtrelerini dinamik olarak belirtme</span><span class="sxs-lookup"><span data-stu-id="56827-124">How to: Dynamically Specify Predicate Filters at Runtime</span></span>](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="56827-125">Nasıl yapılır: Bir derlemenin meta verilerini (LINQ) yansıma ile sorgulama (C#)</span><span class="sxs-lookup"><span data-stu-id="56827-125">How to: Query An Assembly's Metadata with Reflection (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [<span data-ttu-id="56827-126">Nasıl yapılır: Belirtilen öznitelik veya ada sahip dosyaları sorgulama (C#)</span><span class="sxs-lookup"><span data-stu-id="56827-126">How to: Query for Files with a Specified Attribute or Name (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [<span data-ttu-id="56827-127">Nasıl yapılır: Herhangi bir sözcük veya alana (LINQ) göre filtre metin verilerini sıralama veya (C#)</span><span class="sxs-lookup"><span data-stu-id="56827-127">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
