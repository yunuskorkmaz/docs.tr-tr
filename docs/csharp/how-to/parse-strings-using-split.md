---
title: String. Split kullanarak dizeleri ayrıştırma (C# Kılavuzu)
description: String. Split, bir sınırlayıcı kümesinden bölünen dizelerin dizisini döndürür. Dizeleri ayrıştırmak için kolay bir yoldur.
ms.date: 01/03/2018
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
ms.custom: mvc
ms.openlocfilehash: 4f0056426fb29ec3d76093e57fa45e2046f27a4f
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662998"
---
# <a name="how-to-parse-strings-using-stringsplit-in-c"></a><span data-ttu-id="98b09-104">C 'de dize. Split kullanarak dizeleri ayrıştırma\#</span><span class="sxs-lookup"><span data-stu-id="98b09-104">How to parse strings using String.Split in C\#</span></span>

<span data-ttu-id="98b09-105"><xref:System.String.Split%2A?displayProperty=nameWithType>Yöntemi, giriş dizesini bir veya daha fazla sınırlayıcı temelinde bölerek bir alt dizeler dizisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="98b09-105">The <xref:System.String.Split%2A?displayProperty=nameWithType> method creates an array of substrings by splitting the input string based on one or more delimiters.</span></span> <span data-ttu-id="98b09-106">Genellikle bir dizeyi sözcük sınırlarında ayırmanın en kolay yoludur.</span><span class="sxs-lookup"><span data-stu-id="98b09-106">It is often the easiest way to separate a string on word boundaries.</span></span> <span data-ttu-id="98b09-107">Ayrıca, diğer belirli karakter veya dizelerde dizeleri ayırmak için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="98b09-107">It is also used to split strings on other specific characters or strings.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="98b09-108">Aşağıdaki kod, ortak bir tümceciği her sözcük için bir dizeler dizisine böler.</span><span class="sxs-lookup"><span data-stu-id="98b09-108">The following code splits a common phrase into an array of strings for each word.</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet1":::

<span data-ttu-id="98b09-109">Bir ayırıcı karakterinin her örneği döndürülen dizide bir değer üretir.</span><span class="sxs-lookup"><span data-stu-id="98b09-109">Every instance of a separator character produces a value in the returned array.</span></span> <span data-ttu-id="98b09-110">Ardışık Ayırıcı karakterler boş dizeyi döndürülen dizide bir değer olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="98b09-110">Consecutive separator characters produce the empty string as a value in the returned array.</span></span> <span data-ttu-id="98b09-111">Bir ayırıcı olarak boşluk karakterini kullanan aşağıdaki örnekte boş bir dizenin nasıl oluşturulduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="98b09-111">You can see how an empty string is created in the following example, which uses the space character as a separator.</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet2":::

<span data-ttu-id="98b09-112">Bu davranış, tablo verilerini temsil eden, virgülle ayrılmış değerler (CSV) dosyaları gibi biçimlerin daha kolay olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="98b09-112">This behavior makes it easier for formats like comma-separated values (CSV) files representing tabular data.</span></span> <span data-ttu-id="98b09-113">Ardışık virgüller boş bir sütunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="98b09-113">Consecutive commas represent a blank column.</span></span>

<span data-ttu-id="98b09-114"><xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType>Döndürülen dizide boş dizeleri hariç tutmak için isteğe bağlı bir parametre geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="98b09-114">You can pass an optional <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> parameter to exclude any empty strings in the returned array.</span></span> <span data-ttu-id="98b09-115">Döndürülen koleksiyonun daha karmaşık işlenmesi için, [LINQ](../programming-guide/concepts/linq/index.md) kullanarak sonuç sırasını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="98b09-115">For more complicated processing of the returned collection, you can use [LINQ](../programming-guide/concepts/linq/index.md) to manipulate the result sequence.</span></span>

<span data-ttu-id="98b09-116"><xref:System.String.Split%2A?displayProperty=nameWithType>birden çok ayırıcı karakter kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="98b09-116"><xref:System.String.Split%2A?displayProperty=nameWithType> can use multiple separator characters.</span></span>
<span data-ttu-id="98b09-117">Aşağıdaki örnek boşluk, virgül, nokta, iki nokta üst üste ve sekmelerini kullanır ve bu karakterleri içeren bir dizide öğesine <xref:System.String.Split%2A> .</span><span class="sxs-lookup"><span data-stu-id="98b09-117">The following example uses spaces, commas, periods, colons, and tabs, all passed in an array containing these separating characters, to <xref:System.String.Split%2A>.</span></span>
<span data-ttu-id="98b09-118">Kodun alt kısmındaki döngü döndürülen dizideki her bir sözcüğü görüntüler.</span><span class="sxs-lookup"><span data-stu-id="98b09-118">The loop at the bottom of the code displays each of the words in the returned array.</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet3":::

<span data-ttu-id="98b09-119">Herhangi bir ayırıcıdaki ardışık örnekler, çıkış dizisinde boş dize üretir:</span><span class="sxs-lookup"><span data-stu-id="98b09-119">Consecutive instances of any separator produce the empty string in the output array:</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet4":::

<span data-ttu-id="98b09-120"><xref:System.String.Split%2A?displayProperty=nameWithType>bir dizi dizeyi alabilir (tek karakterler yerine hedef dizeyi ayrıştırmak için ayırıcı olarak davranan karakter dizileri).</span><span class="sxs-lookup"><span data-stu-id="98b09-120"><xref:System.String.Split%2A?displayProperty=nameWithType> can take an array of strings (character sequences that act as separators for parsing the target string, instead of single characters).</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet5":::

## <a name="see-also"></a><span data-ttu-id="98b09-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="98b09-121">See also</span></span>

- [<span data-ttu-id="98b09-122">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="98b09-122">C# programming guide</span></span>](../programming-guide/index.md)
- [<span data-ttu-id="98b09-123">Dizeler</span><span class="sxs-lookup"><span data-stu-id="98b09-123">Strings</span></span>](../programming-guide/strings/index.md)
- [<span data-ttu-id="98b09-124">.NET normal ifadeleri</span><span class="sxs-lookup"><span data-stu-id="98b09-124">.NET regular expressions</span></span>](../../standard/base-types/regular-expressions.md)
