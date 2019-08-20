---
title: Verileri filtreleme (C#)
ms.date: 07/20/2015
ms.assetid: fbaece0d-0f23-47f7-89c5-f3ea8db692b6
ms.openlocfilehash: 17d3a65b6042c9679a263eff0048f5360c4aa546
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594399"
---
# <a name="filtering-data-c"></a><span data-ttu-id="6959a-102">Verileri filtreleme (C#)</span><span class="sxs-lookup"><span data-stu-id="6959a-102">Filtering Data (C#)</span></span>
<span data-ttu-id="6959a-103">Filtreleme, sonuç kümesini yalnızca belirtilen bir koşulu karşılayan öğeleri içerecek şekilde kısıtlama işlemini ifade eder.</span><span class="sxs-lookup"><span data-stu-id="6959a-103">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="6959a-104">Seçim olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="6959a-104">It is also known as selection.</span></span>  
  
 <span data-ttu-id="6959a-105">Aşağıdaki çizimde, bir karakter dizisinin filtrelenmesi sonuçları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6959a-105">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="6959a-106">Filtreleme işleminin koşulu, karakterin ' A ' olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6959a-106">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>  
  
 ![LINQ filtreleme işlemini gösteren diyagram](./media/filtering-data/linq-filter-operation.png)  
  
 <span data-ttu-id="6959a-108">Seçimi gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="6959a-108">The standard query operator methods that perform selection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6959a-109">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6959a-109">Methods</span></span>  
  
|<span data-ttu-id="6959a-110">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="6959a-110">Method Name</span></span>|<span data-ttu-id="6959a-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6959a-111">Description</span></span>|<span data-ttu-id="6959a-112">C#Sorgu Ifadesi söz dizimi</span><span class="sxs-lookup"><span data-stu-id="6959a-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="6959a-113">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="6959a-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="6959a-114">OfType</span><span class="sxs-lookup"><span data-stu-id="6959a-114">OfType</span></span>|<span data-ttu-id="6959a-115">Belirtilen türe atama becerisine bağlı olarak değerleri seçer.</span><span class="sxs-lookup"><span data-stu-id="6959a-115">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="6959a-116">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="6959a-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="6959a-117">Where</span><span class="sxs-lookup"><span data-stu-id="6959a-117">Where</span></span>|<span data-ttu-id="6959a-118">Bir koşul işlevini temel alan değerleri seçer.</span><span class="sxs-lookup"><span data-stu-id="6959a-118">Selects values that are based on a predicate function.</span></span>|`where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="6959a-119">Sorgu Ifadesi söz dizimi örneği</span><span class="sxs-lookup"><span data-stu-id="6959a-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="6959a-120">Aşağıdaki örnek, `where` belirli bir uzunluğa sahip dizelerin bulunduğu bir diziden filtrelemek için yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="6959a-120">The following example uses the `where` clause to filter from an array those strings that have a specific length.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6959a-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6959a-121">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="6959a-122">Standart sorgu Işleçlerine genelC#bakış ()</span><span class="sxs-lookup"><span data-stu-id="6959a-122">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="6959a-123">where yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="6959a-123">where clause</span></span>](../../../language-reference/keywords/where-clause.md)
- [<span data-ttu-id="6959a-124">Nasıl yapılır: Çalışma zamanında koşul filtrelerini dinamik olarak belirtme</span><span class="sxs-lookup"><span data-stu-id="6959a-124">How to: Dynamically Specify Predicate Filters at Runtime</span></span>](../../linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="6959a-125">Nasıl yapılır: Bir derlemenin meta verilerini yansıma ile sorgulama (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="6959a-125">How to: Query An Assembly's Metadata with Reflection (LINQ) (C#)</span></span>](./how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [<span data-ttu-id="6959a-126">Nasıl yapılır: Belirtilen bir özniteliğe veya ada (C#) sahip dosyaları sorgula</span><span class="sxs-lookup"><span data-stu-id="6959a-126">How to: Query for Files with a Specified Attribute or Name (C#)</span></span>](./how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [<span data-ttu-id="6959a-127">Nasıl yapılır: Her kelime veya alana göre metin verilerini sıralama veya filtreleme (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="6959a-127">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (C#)</span></span>](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
