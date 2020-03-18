---
title: Veri Filtreleme (C#)
ms.date: 07/20/2015
ms.assetid: fbaece0d-0f23-47f7-89c5-f3ea8db692b6
ms.openlocfilehash: 74399244990f8ff2deaa1d10576ea94a57c16bee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75346987"
---
# <a name="filtering-data-c"></a><span data-ttu-id="e25af-102">Veri Filtreleme (C#)</span><span class="sxs-lookup"><span data-stu-id="e25af-102">Filtering Data (C#)</span></span>
<span data-ttu-id="e25af-103">Filtreleme, yalnızca belirli bir koşulu karşılayan öğeleri içerecek şekilde ayarlanan sonucu kısıtlama işlemini ifade eder.</span><span class="sxs-lookup"><span data-stu-id="e25af-103">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="e25af-104">Seçim olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="e25af-104">It is also known as selection.</span></span>  
  
 <span data-ttu-id="e25af-105">Aşağıdaki resimde, bir karakter dizisini filtrelemenin sonuçları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e25af-105">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="e25af-106">Filtreleme işleminin yüklemi, karakterin 'A' olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e25af-106">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>  
  
 ![LINQ filtreleme işlemini gösteren diyagram](./media/filtering-data/linq-filter-operation.png)  
  
 <span data-ttu-id="e25af-108">Seçimi gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenir.</span><span class="sxs-lookup"><span data-stu-id="e25af-108">The standard query operator methods that perform selection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e25af-109">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e25af-109">Methods</span></span>  
  
|<span data-ttu-id="e25af-110">Yöntem Adı</span><span class="sxs-lookup"><span data-stu-id="e25af-110">Method Name</span></span>|<span data-ttu-id="e25af-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e25af-111">Description</span></span>|<span data-ttu-id="e25af-112">C# Sorgu İfade Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e25af-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="e25af-113">Daha Fazla Bilgi</span><span class="sxs-lookup"><span data-stu-id="e25af-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="e25af-114">Oftype</span><span class="sxs-lookup"><span data-stu-id="e25af-114">OfType</span></span>|<span data-ttu-id="e25af-115">Belirli bir türe döküm yeteneğine bağlı olarak değerleri seçer.</span><span class="sxs-lookup"><span data-stu-id="e25af-115">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="e25af-116">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="e25af-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="e25af-117">Konum</span><span class="sxs-lookup"><span data-stu-id="e25af-117">Where</span></span>|<span data-ttu-id="e25af-118">Yüklem işlevini temel alan değerleri seçer.</span><span class="sxs-lookup"><span data-stu-id="e25af-118">Selects values that are based on a predicate function.</span></span>|`where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="e25af-119">Sorgu İfadesözdizimi Örneği</span><span class="sxs-lookup"><span data-stu-id="e25af-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="e25af-120">Aşağıdaki örnek, `where` belirli bir uzunluğa sahip dizeleri bir diziden filtrelemek için yan tümceyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="e25af-120">The following example uses the `where` clause to filter from an array those strings that have a specific length.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e25af-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e25af-121">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="e25af-122">Standart Sorgu Operatörlerine Genel Bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="e25af-122">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="e25af-123">where tümcesi</span><span class="sxs-lookup"><span data-stu-id="e25af-123">where clause</span></span>](../../../language-reference/keywords/where-clause.md)
- [<span data-ttu-id="e25af-124">Çalışma zamanında koşul filtrelerini dinamik olarak belirtme</span><span class="sxs-lookup"><span data-stu-id="e25af-124">Dynamically specify predicate filters at runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="e25af-125">Yansıma (LINQ) (C#) ile bir derlemenin meta verisi nasıl sorgulanır?</span><span class="sxs-lookup"><span data-stu-id="e25af-125">How to query an assembly's metadata with Reflection (LINQ) (C#)</span></span>](./how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [<span data-ttu-id="e25af-126">Belirli bir öznitelik veya ada sahip dosyalar için sorgulama (C#)</span><span class="sxs-lookup"><span data-stu-id="e25af-126">How to query for files with a specified attribute or name (C#)</span></span>](./how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [<span data-ttu-id="e25af-127">Metin verilerini herhangi bir sözcüğe veya alana göre sıralama veya filtreleme (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="e25af-127">How to sort or filter text data by any word or field (LINQ) (C#)</span></span>](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
