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
ms.openlocfilehash: cf8307517213b54041b272843232eb595660b2e9
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389501"
---
# <a name="how-to-parse-strings-using-stringsplit-in-c"></a><span data-ttu-id="bd335-104">String.Split in C kullanarak dizeleri ayrışdırmak için nasıl\#</span><span class="sxs-lookup"><span data-stu-id="bd335-104">How to parse strings using String.Split in C\#</span></span>

<span data-ttu-id="bd335-105">Yöntem, <xref:System.String.Split%2A?displayProperty=nameWithType> giriş dizesini bir veya daha fazla sınırlayıcıyı temel alarak bölerek bir dizi alt dizeleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bd335-105">The <xref:System.String.Split%2A?displayProperty=nameWithType> method creates an array of substrings by splitting the input string based on one or more delimiters.</span></span> <span data-ttu-id="bd335-106">Genellikle sözcük sınırları üzerinde bir dize ayırmak için en kolay yoludur.</span><span class="sxs-lookup"><span data-stu-id="bd335-106">It is often the easiest way to separate a string on word boundaries.</span></span> <span data-ttu-id="bd335-107">Ayrıca, diğer belirli karakterler veya dizeleri dizeleri bölmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bd335-107">It is also used to split strings on other specific characters or strings.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="bd335-108">Aşağıdaki kod, ortak bir tümceciği her sözcük için bir dizi dize ye böler.</span><span class="sxs-lookup"><span data-stu-id="bd335-108">The following code splits a common phrase into an array of strings for each word.</span></span>

[!code-csharp-interactive[split strings on word boundaries](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#1)]

<span data-ttu-id="bd335-109">Ayırıcı karakterin her örneği döndürülen dizide bir değer üretir.</span><span class="sxs-lookup"><span data-stu-id="bd335-109">Every instance of a separator character produces a value in the returned array.</span></span> <span data-ttu-id="bd335-110">Ardışık ayırıcı karakterler, boş dizeyi döndürülen dizide bir değer olarak üretir.</span><span class="sxs-lookup"><span data-stu-id="bd335-110">Consecutive separator characters produce the empty string as a value in the returned array.</span></span> <span data-ttu-id="bd335-111">Boşluk karakterini ayırıcı olarak kullanan aşağıdaki örnekte boş bir dize nasıl oluşturulduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bd335-111">You can see how an empty string is created in the following example, which uses the space character as a separator.</span></span>

[!code-csharp-interactive[split strings with repeated separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#2)]

<span data-ttu-id="bd335-112">Bu davranış, tabular verileri temsil eden virgülden ayrılmış değerler (CSV) dosyaları gibi biçimler için kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="bd335-112">This behavior makes it easier for formats like comma-separated values (CSV) files representing tabular data.</span></span> <span data-ttu-id="bd335-113">Ardışık virgüller boş bir sütunu temsil ediyor.</span><span class="sxs-lookup"><span data-stu-id="bd335-113">Consecutive commas represent a blank column.</span></span>

<span data-ttu-id="bd335-114">Döndürülen dizideki <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> boş dizeleri hariç tutmak için isteğe bağlı bir parametre geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bd335-114">You can pass an optional <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> parameter to exclude any empty strings in the returned array.</span></span> <span data-ttu-id="bd335-115">Döndürülen koleksiyonun daha karmaşık işlenmesi için, sonuç sırasını işlemek için [LINQ'yi](../programming-guide/concepts/linq/index.md) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bd335-115">For more complicated processing of the returned collection, you can use [LINQ](../programming-guide/concepts/linq/index.md) to manipulate the result sequence.</span></span>

<span data-ttu-id="bd335-116"><xref:System.String.Split%2A?displayProperty=nameWithType>birden çok ayırıcı karakter kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bd335-116"><xref:System.String.Split%2A?displayProperty=nameWithType> can use multiple separator characters.</span></span>
<span data-ttu-id="bd335-117">Aşağıdaki örnek, bu ayıran karakterleri içeren bir dizi geçirilen boşluklar, virgüller, dönemler, üst <xref:System.String.Split%2A>üste ve sekmeler kullanır.</span><span class="sxs-lookup"><span data-stu-id="bd335-117">The following example uses spaces, commas, periods, colons, and tabs, all passed in an array containing these separating characters, to <xref:System.String.Split%2A>.</span></span>
<span data-ttu-id="bd335-118">Kodun altındaki döngü, döndürülen dizideki sözcüklerin her birini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="bd335-118">The loop at the bottom of the code displays each of the words in the returned array.</span></span>  

[!code-csharp-interactive[split strings using multiple separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#3)]

<span data-ttu-id="bd335-119">Herhangi bir ayırıcının ardışık örnekleri, çıktı dizisindeki boş dizeyi üretir:</span><span class="sxs-lookup"><span data-stu-id="bd335-119">Consecutive instances of any separator produce the empty string in the output array:</span></span>

[!code-csharp-interactive[split strings using multiple consecutive separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#4)]

<span data-ttu-id="bd335-120"><xref:System.String.Split%2A?displayProperty=nameWithType>bir dizi dize alabilir (tek karakterler yerine hedef dizeyi ayrıştırmak için ayırıcı görevi yapan karakter dizileri).</span><span class="sxs-lookup"><span data-stu-id="bd335-120"><xref:System.String.Split%2A?displayProperty=nameWithType> can take an array of strings (character sequences that act as separators for parsing the target string, instead of single characters).</span></span>  
  
[!code-csharp-interactive[split strings using strings as separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#5)]

<span data-ttu-id="bd335-121">Bu örnekleri [GitHub depomuzdaki](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings)koda bakarak deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bd335-121">You can try these samples by looking at the code in our [GitHub repository](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings).</span></span> <span data-ttu-id="bd335-122">Veya bir zip [dosyası olarak](../../../samples/snippets/csharp/how-to/strings.zip)örnekleri indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bd335-122">Or you can download the samples [as a zip file](../../../samples/snippets/csharp/how-to/strings.zip).</span></span>

## <a name="see-also"></a><span data-ttu-id="bd335-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bd335-123">See also</span></span>

- [<span data-ttu-id="bd335-124">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="bd335-124">C# Programming Guide</span></span>](../programming-guide/index.md)
- [<span data-ttu-id="bd335-125">Dizeler</span><span class="sxs-lookup"><span data-stu-id="bd335-125">Strings</span></span>](../programming-guide/strings/index.md)
- [<span data-ttu-id="bd335-126">.NET Düzenli İfadeler</span><span class="sxs-lookup"><span data-stu-id="bd335-126">.NET Regular Expressions</span></span>](../../standard/base-types/regular-expressions.md)
