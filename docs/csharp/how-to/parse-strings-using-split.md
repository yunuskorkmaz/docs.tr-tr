---
title: String.Split (C# Guide) kullanarak dizeleri ayrıştırma
description: String.Split, bir dizi sınırlayıcıdan bölünmüş dizeler dizisini döndürür. İpleri ayrışdırmanın kolay bir yolu.
ms.date: 01/03/2018
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
ms.custom: mvc
ms.openlocfilehash: b46429f3b55658e1f2a7d21eed714c1d02236c57
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73973229"
---
# <a name="how-to-parse-strings-using-stringsplit-c-guide"></a><span data-ttu-id="b9ffb-104">String.Split (C# Guide) kullanarak dizeleri ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="b9ffb-104">How to parse strings using String.Split (C# Guide)</span></span>

<span data-ttu-id="b9ffb-105">Yöntem, <xref:System.String.Split%2A?displayProperty=nameWithType> giriş dizesini bir veya daha fazla sınırlayıcıyı temel alarak bölerek bir dizi alt dizeleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b9ffb-105">The <xref:System.String.Split%2A?displayProperty=nameWithType> method creates an array of substrings by splitting the input string based on one or more delimiters.</span></span> <span data-ttu-id="b9ffb-106">Genellikle sözcük sınırları üzerinde bir dize ayırmak için en kolay yoludur.</span><span class="sxs-lookup"><span data-stu-id="b9ffb-106">It is often the easiest way to separate a string on word boundaries.</span></span> <span data-ttu-id="b9ffb-107">Ayrıca, diğer belirli karakterler veya dizeleri dizeleri bölmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b9ffb-107">It is also used to split strings on other specific characters or strings.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="b9ffb-108">Aşağıdaki kod, ortak bir tümceciği her sözcük için bir dizi dize ye böler.</span><span class="sxs-lookup"><span data-stu-id="b9ffb-108">The following code splits a common phrase into an array of strings for each word.</span></span>

[!code-csharp-interactive[split strings on word boundaries](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#1)]

<span data-ttu-id="b9ffb-109">Ayırıcı karakterin her örneği döndürülen dizide bir değer üretir.</span><span class="sxs-lookup"><span data-stu-id="b9ffb-109">Every instance of a separator character produces a value in the returned array.</span></span> <span data-ttu-id="b9ffb-110">Ardışık ayırıcı karakterler, boş dizeyi döndürülen dizide bir değer olarak üretir.</span><span class="sxs-lookup"><span data-stu-id="b9ffb-110">Consecutive separator characters produce the empty string as a value in the returned array.</span></span>  <span data-ttu-id="b9ffb-111">Bunu ayırıcı olarak alanı kullanan aşağıdaki örnekte görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b9ffb-111">You can see this in the following example, which uses space as a separator:</span></span>

[!code-csharp-interactive[split strings with repeated separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#2)]

<span data-ttu-id="b9ffb-112">Bu davranış, tabular verileri temsil eden virgülayrılmış değerler (CSV) dosyaları gibi biçimler için kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="b9ffb-112">This behavior makes it easier for formats like comma separated values (CSV) files representing tabular data.</span></span> <span data-ttu-id="b9ffb-113">Ardışık virgüller boş bir sütunu temsil ediyor.</span><span class="sxs-lookup"><span data-stu-id="b9ffb-113">Consecutive commas represent a blank column.</span></span>

<span data-ttu-id="b9ffb-114">Döndürülen dizideki <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> boş dizeleri hariç tutmak için isteğe bağlı bir parametre geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b9ffb-114">You can pass an optional <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> parameter to exclude any empty strings in the returned array.</span></span> <span data-ttu-id="b9ffb-115">Döndürülen koleksiyonun daha karmaşık işlenmesi için, sonuç sırasını işlemek için [LINQ'yi](../programming-guide/concepts/linq/index.md) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b9ffb-115">For more complicated processing of the returned collection, you can use [LINQ](../programming-guide/concepts/linq/index.md) to manipulate the result sequence.</span></span>

<span data-ttu-id="b9ffb-116"><xref:System.String.Split%2A?displayProperty=nameWithType>birden çok ayırıcı karakter kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b9ffb-116"><xref:System.String.Split%2A?displayProperty=nameWithType> can use multiple separator characters.</span></span>
<span data-ttu-id="b9ffb-117">Aşağıdaki örnek, bu ayıran karakterleri içeren bir dizi geçirilen boşluklar, virgüller, dönemler, üst <xref:System.String.Split%2A>üste ve sekmeler kullanır.</span><span class="sxs-lookup"><span data-stu-id="b9ffb-117">The following example uses spaces, commas, periods, colons, and tabs, all passed in an array containing these separating characters, to <xref:System.String.Split%2A>.</span></span>
<span data-ttu-id="b9ffb-118">Kodun altındaki döngü, döndürülen dizideki sözcüklerin her birini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="b9ffb-118">The loop at the bottom of the code displays each of the words in the returned array.</span></span>  

[!code-csharp-interactive[split strings using multiple separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#3)]

<span data-ttu-id="b9ffb-119">Herhangi bir ayırıcının ardışık örnekleri, çıktı dizisindeki boş dizeyi üretir:</span><span class="sxs-lookup"><span data-stu-id="b9ffb-119">Consecutive instances of any separator produce the empty string in the output array:</span></span>

[!code-csharp-interactive[split strings using multiple consecutive separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#4)]

<span data-ttu-id="b9ffb-120"><xref:System.String.Split%2A?displayProperty=nameWithType>bir dizi dize alabilir (tek karakterler yerine hedef dizeyi ayrıştırmak için ayırıcı görevi yapan karakter dizileri).</span><span class="sxs-lookup"><span data-stu-id="b9ffb-120"><xref:System.String.Split%2A?displayProperty=nameWithType> can take an array of strings (character sequences that act as separators for parsing the target string, instead of single characters).</span></span>  
  
[!code-csharp-interactive[split strings using strings as separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#5)]

<span data-ttu-id="b9ffb-121">Bu örnekleri [GitHub depomuzdaki](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings)koda bakarak deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b9ffb-121">You can try these samples by looking at the code in our [GitHub repository](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings).</span></span> <span data-ttu-id="b9ffb-122">Veya bir zip [dosyası olarak](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip)örnekleri indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b9ffb-122">Or you can download the samples [as a zip file](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).</span></span>

## <a name="see-also"></a><span data-ttu-id="b9ffb-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b9ffb-123">See also</span></span>

- [<span data-ttu-id="b9ffb-124">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b9ffb-124">C# Programming Guide</span></span>](../programming-guide/index.md)
- [<span data-ttu-id="b9ffb-125">Dize</span><span class="sxs-lookup"><span data-stu-id="b9ffb-125">Strings</span></span>](../programming-guide/strings/index.md)
- [<span data-ttu-id="b9ffb-126">.NET Düzenli İfadeler</span><span class="sxs-lookup"><span data-stu-id="b9ffb-126">.NET Regular Expressions</span></span>](../../standard/base-types/regular-expressions.md)
