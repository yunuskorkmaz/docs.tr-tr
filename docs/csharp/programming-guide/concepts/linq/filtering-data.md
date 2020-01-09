---
title: Verileri filtreleme (C#)
ms.date: 07/20/2015
ms.assetid: fbaece0d-0f23-47f7-89c5-f3ea8db692b6
ms.openlocfilehash: 74399244990f8ff2deaa1d10576ea94a57c16bee
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346987"
---
# <a name="filtering-data-c"></a><span data-ttu-id="df16b-102">Verileri filtreleme (C#)</span><span class="sxs-lookup"><span data-stu-id="df16b-102">Filtering Data (C#)</span></span>
<span data-ttu-id="df16b-103">Filtreleme, sonuç kümesini yalnızca belirtilen bir koşulu karşılayan öğeleri içerecek şekilde kısıtlama işlemini ifade eder.</span><span class="sxs-lookup"><span data-stu-id="df16b-103">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="df16b-104">Seçim olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="df16b-104">It is also known as selection.</span></span>  
  
 <span data-ttu-id="df16b-105">Aşağıdaki çizimde, bir karakter dizisinin filtrelenmesi sonuçları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="df16b-105">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="df16b-106">Filtreleme işleminin koşulu, karakterin ' A ' olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="df16b-106">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>  
  
 ![LINQ filtreleme işlemini gösteren diyagram](./media/filtering-data/linq-filter-operation.png)  
  
 <span data-ttu-id="df16b-108">Seçimi gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="df16b-108">The standard query operator methods that perform selection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="df16b-109">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="df16b-109">Methods</span></span>  
  
|<span data-ttu-id="df16b-110">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="df16b-110">Method Name</span></span>|<span data-ttu-id="df16b-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="df16b-111">Description</span></span>|<span data-ttu-id="df16b-112">C#Sorgu Ifadesi söz dizimi</span><span class="sxs-lookup"><span data-stu-id="df16b-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="df16b-113">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="df16b-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="df16b-114">OfType</span><span class="sxs-lookup"><span data-stu-id="df16b-114">OfType</span></span>|<span data-ttu-id="df16b-115">Belirtilen türe atama becerisine bağlı olarak değerleri seçer.</span><span class="sxs-lookup"><span data-stu-id="df16b-115">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="df16b-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="df16b-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="df16b-117">Where</span><span class="sxs-lookup"><span data-stu-id="df16b-117">Where</span></span>|<span data-ttu-id="df16b-118">Bir koşul işlevini temel alan değerleri seçer.</span><span class="sxs-lookup"><span data-stu-id="df16b-118">Selects values that are based on a predicate function.</span></span>|`where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="df16b-119">Sorgu Ifadesi söz dizimi örneği</span><span class="sxs-lookup"><span data-stu-id="df16b-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="df16b-120">Aşağıdaki örnek, belirli bir uzunluğa sahip dizelerin bu dizilerle filtreleneceği `where` yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="df16b-120">The following example uses the `where` clause to filter from an array those strings that have a specific length.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="df16b-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="df16b-121">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="df16b-122">Standart sorgu Işleçlerine genelC#bakış ()</span><span class="sxs-lookup"><span data-stu-id="df16b-122">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="df16b-123">where yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="df16b-123">where clause</span></span>](../../../language-reference/keywords/where-clause.md)
- [<span data-ttu-id="df16b-124">Çalışma zamanında koşul filtrelerini dinamik olarak belirtme</span><span class="sxs-lookup"><span data-stu-id="df16b-124">Dynamically specify predicate filters at runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="df16b-125">Bir derlemenin meta verilerini yansıma ile sorgulama (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="df16b-125">How to query an assembly's metadata with Reflection (LINQ) (C#)</span></span>](./how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [<span data-ttu-id="df16b-126">Belirtilen bir özniteliğe veya ada (C#) sahip dosyaları sorgulama</span><span class="sxs-lookup"><span data-stu-id="df16b-126">How to query for files with a specified attribute or name (C#)</span></span>](./how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [<span data-ttu-id="df16b-127">Her kelime veya alana göre metin verilerini sıralama veya filtreleme (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="df16b-127">How to sort or filter text data by any word or field (LINQ) (C#)</span></span>](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
