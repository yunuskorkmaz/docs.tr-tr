---
title: String. Split kullanarak dizeleri ayrıştırma (C# kılavuz)
description: String. Split, bir sınırlayıcı kümesinden bölünen dizelerin dizisini döndürür. Dizeleri ayrıştırmak için kolay bir yoldur.
ms.date: 01/03/2018
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
ms.custom: mvc
ms.openlocfilehash: b46429f3b55658e1f2a7d21eed714c1d02236c57
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73973229"
---
# <a name="how-to-parse-strings-using-stringsplit-c-guide"></a><span data-ttu-id="dbb64-104">String. Split kullanarak dizeleri ayrıştırma (C# kılavuz)</span><span class="sxs-lookup"><span data-stu-id="dbb64-104">How to parse strings using String.Split (C# Guide)</span></span>

<span data-ttu-id="dbb64-105"><xref:System.String.Split%2A?displayProperty=nameWithType> yöntemi, giriş dizesini bir veya daha fazla sınırlayıcı temelinde bölerek bir alt dizeler dizisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dbb64-105">The <xref:System.String.Split%2A?displayProperty=nameWithType> method creates an array of substrings by splitting the input string based on one or more delimiters.</span></span> <span data-ttu-id="dbb64-106">Genellikle bir dizeyi sözcük sınırlarında ayırmanın en kolay yoludur.</span><span class="sxs-lookup"><span data-stu-id="dbb64-106">It is often the easiest way to separate a string on word boundaries.</span></span> <span data-ttu-id="dbb64-107">Ayrıca, diğer belirli karakter veya dizelerde dizeleri ayırmak için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dbb64-107">It is also used to split strings on other specific characters or strings.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="dbb64-108">Aşağıdaki kod, ortak bir tümceciği her sözcük için bir dizeler dizisine böler.</span><span class="sxs-lookup"><span data-stu-id="dbb64-108">The following code splits a common phrase into an array of strings for each word.</span></span>

[!code-csharp-interactive[split strings on word boundaries](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#1)]

<span data-ttu-id="dbb64-109">Bir ayırıcı karakterinin her örneği döndürülen dizide bir değer üretir.</span><span class="sxs-lookup"><span data-stu-id="dbb64-109">Every instance of a separator character produces a value in the returned array.</span></span> <span data-ttu-id="dbb64-110">Ardışık Ayırıcı karakterler boş dizeyi döndürülen dizide bir değer olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dbb64-110">Consecutive separator characters produce the empty string as a value in the returned array.</span></span>  <span data-ttu-id="dbb64-111">Bu, bir ayırıcı olarak boşluk kullanan aşağıdaki örnekte görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="dbb64-111">You can see this in the following example, which uses space as a separator:</span></span>

[!code-csharp-interactive[split strings with repeated separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#2)]

<span data-ttu-id="dbb64-112">Bu davranış, tablo verilerini temsil eden, virgülle ayrılmış değerler (CSV) dosyaları gibi biçimlerin daha kolay olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="dbb64-112">This behavior makes it easier for formats like comma separated values (CSV) files representing tabular data.</span></span> <span data-ttu-id="dbb64-113">Ardışık virgüller boş bir sütunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="dbb64-113">Consecutive commas represent a blank column.</span></span>

<span data-ttu-id="dbb64-114">Döndürülen dizide boş dizeleri hariç tutmak için isteğe bağlı bir <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> parametresi geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dbb64-114">You can pass an optional <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> parameter to exclude any empty strings in the returned array.</span></span> <span data-ttu-id="dbb64-115">Döndürülen koleksiyonun daha karmaşık işlenmesi için, [LINQ](../programming-guide/concepts/linq/index.md) kullanarak sonuç sırasını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dbb64-115">For more complicated processing of the returned collection, you can use [LINQ](../programming-guide/concepts/linq/index.md) to manipulate the result sequence.</span></span>

<span data-ttu-id="dbb64-116"><xref:System.String.Split%2A?displayProperty=nameWithType> birden çok ayırıcı karakter kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="dbb64-116"><xref:System.String.Split%2A?displayProperty=nameWithType> can use multiple separator characters.</span></span>
<span data-ttu-id="dbb64-117">Aşağıdaki örnek boşluk, virgül, nokta, iki nokta üst üste ve sekmelerini kullanır, bu karakterleri içeren bir dizide <xref:System.String.Split%2A>.</span><span class="sxs-lookup"><span data-stu-id="dbb64-117">The following example uses spaces, commas, periods, colons, and tabs, all passed in an array containing these separating characters, to <xref:System.String.Split%2A>.</span></span>
<span data-ttu-id="dbb64-118">Kodun alt kısmındaki döngü döndürülen dizideki her bir sözcüğü görüntüler.</span><span class="sxs-lookup"><span data-stu-id="dbb64-118">The loop at the bottom of the code displays each of the words in the returned array.</span></span>  

[!code-csharp-interactive[split strings using multiple separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#3)]

<span data-ttu-id="dbb64-119">Herhangi bir ayırıcıdaki ardışık örnekler, çıkış dizisinde boş dize üretir:</span><span class="sxs-lookup"><span data-stu-id="dbb64-119">Consecutive instances of any separator produce the empty string in the output array:</span></span>

[!code-csharp-interactive[split strings using multiple consecutive separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#4)]

<span data-ttu-id="dbb64-120"><xref:System.String.Split%2A?displayProperty=nameWithType> dize dizisini alabilir (tek karakterler yerine hedef dizeyi ayrıştırmak için ayırıcılar olarak davranan karakter dizileri).</span><span class="sxs-lookup"><span data-stu-id="dbb64-120"><xref:System.String.Split%2A?displayProperty=nameWithType> can take an array of strings (character sequences that act as separators for parsing the target string, instead of single characters).</span></span>  
  
[!code-csharp-interactive[split strings using strings as separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#5)]

<span data-ttu-id="dbb64-121">Bu örnekleri, [GitHub deponuzdaki](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings)koda bakarak deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dbb64-121">You can try these samples by looking at the code in our [GitHub repository](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings).</span></span> <span data-ttu-id="dbb64-122">Ya da örnekleri [zip dosyası olarak](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dbb64-122">Or you can download the samples [as a zip file](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).</span></span>

## <a name="see-also"></a><span data-ttu-id="dbb64-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dbb64-123">See also</span></span>

- [<span data-ttu-id="dbb64-124">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="dbb64-124">C# Programming Guide</span></span>](../programming-guide/index.md)
- [<span data-ttu-id="dbb64-125">Dizeler</span><span class="sxs-lookup"><span data-stu-id="dbb64-125">Strings</span></span>](../programming-guide/strings/index.md)
- [<span data-ttu-id="dbb64-126">.NET normal Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="dbb64-126">.NET Regular Expressions</span></span>](../../standard/base-types/regular-expressions.md)
