---
title: 'Nasıl yapılır: String.Split kullanarak dizeleri ayrıştırma (C# Kılavuzu)'
description: String.Split sınırlayıcılar kümesinden bölme dizisini döndürür. Dizeleri ayrıştırma kolay bir yoludur.
ms.date: 01/03/2018
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
ms.custom: mvc
ms.openlocfilehash: a8cb3a62497379f60e9cc6dec3d342192361f865
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54603735"
---
# <a name="how-to-parse-strings-using-stringsplit-c-guide"></a><span data-ttu-id="2d113-104">Nasıl yapılır: String.Split kullanarak dizeleri ayrıştırma (C# Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="2d113-104">How to: Parse Strings Using String.Split (C# Guide)</span></span>

<span data-ttu-id="2d113-105"><xref:System.String.Split%2A?displayProperty=nameWithType> Yöntemi, bir veya daha fazla ayırıcıları göre giriş dizesini bölerek alt dizeler dizisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2d113-105">The <xref:System.String.Split%2A?displayProperty=nameWithType> method creates an array of substrings by splitting the input string based on one or more delimiters.</span></span> <span data-ttu-id="2d113-106">Bir sözcük sınırlarından dizesine ayırmak için genellikle en kolay yoludur.</span><span class="sxs-lookup"><span data-stu-id="2d113-106">It is often the easiest way to separate a string on word boundaries.</span></span> <span data-ttu-id="2d113-107">Ayrıca, diğer belirli karakterler veya dizelerin dizeleri bölmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2d113-107">It is also used to split strings on other specific characters or strings.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="2d113-108">Aşağıdaki kodu ortak bir deyim için her bir sözcüğün bir dize dizisi halinde böler.</span><span class="sxs-lookup"><span data-stu-id="2d113-108">The following code splits a common phrase into an array of strings for each word.</span></span>

[!code-csharp-interactive[split strings on word boundaries](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#1)]

<span data-ttu-id="2d113-109">Her örnek bir ayırıcı karakteri döndürülen dizideki bir değer üretir.</span><span class="sxs-lookup"><span data-stu-id="2d113-109">Every instance of a separator character produces a value in the returned array.</span></span> <span data-ttu-id="2d113-110">Ardışık ayırıcı karakter, döndürülen dizi değer olarak boş bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2d113-110">Consecutive separator characters produce the empty string as a value in the returned array.</span></span>  <span data-ttu-id="2d113-111">Bu alanı bir ayırıcı olarak kullanan aşağıdaki örnekte görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2d113-111">You can see this in the following example, which uses space as a separator:</span></span>

[!code-csharp-interactive[split strings with repeated separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#2)]

<span data-ttu-id="2d113-112">Bu davranış biçimlerini tablosal verileri temsil eden virgülle ayrılmış değerler (CSV) dosyaları gibi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="2d113-112">This behavior makes it easier for formats like comma separated values (CSV) files representing tabular data.</span></span> <span data-ttu-id="2d113-113">Art arda virgüllerle boş bir sütunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2d113-113">Consecutive commas represent a blank column.</span></span>

<span data-ttu-id="2d113-114">İsteğe bağlı geçirebilirsiniz <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> döndürülen dizideki herhangi bir boş dizeler hariç tutmak için parametre.</span><span class="sxs-lookup"><span data-stu-id="2d113-114">You can pass an optional <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> parameter to exclude any empty strings in the returned array.</span></span> <span data-ttu-id="2d113-115">Daha karmaşık döndürülen koleksiyon işleme için kullanabileceğiniz [LINQ](../programming-guide/concepts/linq/index.md) Sonuç dizisini değiştirmek için.</span><span class="sxs-lookup"><span data-stu-id="2d113-115">For more complicated processing of the returned collection, you can use [LINQ](../programming-guide/concepts/linq/index.md) to manipulate the result sequence.</span></span>

<span data-ttu-id="2d113-116"><xref:System.String.Split%2A?displayProperty=nameWithType> birden fazla ayırıcı karakter kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2d113-116"><xref:System.String.Split%2A?displayProperty=nameWithType> can use multiple separator characters.</span></span>
<span data-ttu-id="2d113-117">Aşağıdaki örnek, boşluk, virgül, nokta, iki nokta üst üste ve sekmeler, tüm bu karakterler için ayırma içeren bir dizi içinde geçirilen kullanır <xref:System.String.Split%2A>.</span><span class="sxs-lookup"><span data-stu-id="2d113-117">The following example uses spaces, commas, periods, colons, and tabs, all passed in an array containing these separating characters, to <xref:System.String.Split%2A>.</span></span>
<span data-ttu-id="2d113-118">Döngü kodunun altındaki her bir kelimelerin döndürülen dizideki görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2d113-118">The loop at the bottom of the code displays each of the words in the returned array.</span></span>  

[!code-csharp-interactive[split strings using multiple separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#3)]

<span data-ttu-id="2d113-119">Tüm ayırıcı ardışık örnekleri bir çıkış dizisinde boş dize üretir:</span><span class="sxs-lookup"><span data-stu-id="2d113-119">Consecutive instances of any separator produce the empty string in the output array:</span></span>

[!code-csharp-interactive[split strings using multiple consecutive separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#4)]

<span data-ttu-id="2d113-120"><xref:System.String.Split%2A?displayProperty=nameWithType> (tek karakter yerine hedef dizesini ayrıştırmak için ayırıcı olarak davranmak karakter dizileri) dize dizisi alabilir.</span><span class="sxs-lookup"><span data-stu-id="2d113-120"><xref:System.String.Split%2A?displayProperty=nameWithType> can take an array of strings (character sequences that act as separators for parsing the target string, instead of single characters).</span></span>  
  
[!code-csharp-interactive[split strings using strings as separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#5)]

<span data-ttu-id="2d113-121">Bu örnekler kodda bakarak deneyebilirsiniz bizim [GitHub deposu](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings).</span><span class="sxs-lookup"><span data-stu-id="2d113-121">You can try these samples by looking at the code in our [GitHub repository](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings).</span></span> <span data-ttu-id="2d113-122">Örnekleri indirebilirsiniz [zip dosyası olarak](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).</span><span class="sxs-lookup"><span data-stu-id="2d113-122">Or you can download the samples [as a zip file](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).</span></span>

## <a name="see-also"></a><span data-ttu-id="2d113-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d113-123">See also</span></span>

- [<span data-ttu-id="2d113-124">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="2d113-124">C# Programming Guide</span></span>](../programming-guide/index.md)
- [<span data-ttu-id="2d113-125">Dizeler</span><span class="sxs-lookup"><span data-stu-id="2d113-125">Strings</span></span>](../programming-guide/strings/index.md)
- [<span data-ttu-id="2d113-126">.NET normal ifadeler</span><span class="sxs-lookup"><span data-stu-id="2d113-126">.NET Regular Expressions</span></span>](../../standard/base-types/regular-expressions.md)
