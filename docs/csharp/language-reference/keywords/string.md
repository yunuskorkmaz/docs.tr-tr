---
title: dize - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- string
- string_CSharpKeyword
helpviewer_keywords:
- strings [C#], reference
- '@ string literal'
- string literals [C#]
- string keyword [C#]
ms.assetid: 3037e558-fb22-494d-bca1-a15ade11b11a
ms.openlocfilehash: f6c76f8effc5aef82803014b9a7257c2ad6865b8
ms.sourcegitcommit: d6e419f9d9cd7e8f21ebf5acde6d016c16332579
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/12/2018
ms.locfileid: "53286487"
---
# <a name="string-c-reference"></a><span data-ttu-id="fc855-102">string (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="fc855-102">string (C# Reference)</span></span>

<span data-ttu-id="fc855-103">`string` Türü bir dizi sıfır veya daha fazla Unicode karakteri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fc855-103">The `string` type represents a sequence of zero or more Unicode characters.</span></span> <span data-ttu-id="fc855-104">`string` için bir diğer addır <xref:System.String> .NET içinde.</span><span class="sxs-lookup"><span data-stu-id="fc855-104">`string` is an alias for <xref:System.String> in .NET.</span></span>

<span data-ttu-id="fc855-105">Ancak `string` bir başvuru türü eşitlik işleçleri (`==` ve `!=`) değerlerini karşılaştırmak için tanımlanan `string` nesnelerine, başvuruda değil.</span><span class="sxs-lookup"><span data-stu-id="fc855-105">Although `string` is a reference type, the equality operators (`==` and `!=`) are defined to compare the values of `string` objects, not references.</span></span> <span data-ttu-id="fc855-106">Bu, daha sezgisel dizeyi eşitlik için sınama yapar.</span><span class="sxs-lookup"><span data-stu-id="fc855-106">This makes testing for string equality more intuitive.</span></span> <span data-ttu-id="fc855-107">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="fc855-107">For example:</span></span>

```csharp
string a = "hello";
string b = "h";
// Append to contents of 'b'
b += "ello";
Console.WriteLine(a == b);
Console.WriteLine((object)a == (object)b);
```

<span data-ttu-id="fc855-108">Bu "True" görüntüler ve ardından "False" eşdeğer dizeler içeriğini çünkü ancak `a` ve `b` aynı dize örneğine işaret etmiyor.</span><span class="sxs-lookup"><span data-stu-id="fc855-108">This displays "True" and then "False" because the content of the strings are equivalent, but `a` and `b` do not refer to the same string instance.</span></span>

<span data-ttu-id="fc855-109">+ İşleci dizeleri birleştirir:</span><span class="sxs-lookup"><span data-stu-id="fc855-109">The + operator concatenates strings:</span></span>

```csharp
string a = "good " + "morning";
```

<span data-ttu-id="fc855-110">Bu, "Günaydın" içeren bir dize nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fc855-110">This creates a string object that contains "good morning".</span></span>

<span data-ttu-id="fc855-111">Dizelerdir *değişmez*--bir dize nesnesi, içeriğini nesne oluşturulduktan sonra değiştirilemez, söz dizimi sağlar ancak görünür Bunu yapmak gibi.</span><span class="sxs-lookup"><span data-stu-id="fc855-111">Strings are *immutable*--the contents of a string object cannot be changed after the object is created, although the syntax makes it appear as if you can do this.</span></span> <span data-ttu-id="fc855-112">Örneğin, bu kod yazdığınızda, derleyici, gerçekte yeni dizi karakteri tutmak için yeni bir dize nesnesi oluşturur ve yeni nesne b atanır.</span><span class="sxs-lookup"><span data-stu-id="fc855-112">For example, when you write this code, the compiler actually creates a new string object to hold the new sequence of characters, and that new object is assigned to b.</span></span> <span data-ttu-id="fc855-113">"H" dizesi, ardından çöp toplama için uygundur.</span><span class="sxs-lookup"><span data-stu-id="fc855-113">The string "h" is then eligible for garbage collection.</span></span>

```csharp
string b = "h";
b += "ello";
```

<span data-ttu-id="fc855-114">[] İşleci karakterlerin tek tek salt okunur erişim için kullanılan bir `string`:</span><span class="sxs-lookup"><span data-stu-id="fc855-114">The [] operator can be used for readonly access to individual characters of a `string`:</span></span>

```csharp
string str = "test";
char x = str[2];  // x = 's';
```

<span data-ttu-id="fc855-115">Benzer şekilde, [] işleci ayrıca her bir karakteri üzerinde yineleme için kullanılabilir bir `string`:</span><span class="sxs-lookup"><span data-stu-id="fc855-115">In similar fashion, the [] operator can also be used for iterating over each character in a `string`:</span></span>

```csharp
string str = "test";

for (int i = 0; i < str.Length; i++)
{
  Console.Write(str[i] + " ");
}
// Output: t e s t
``` 

<span data-ttu-id="fc855-116">Dize değişmez değerleri, tür `string` ve teklif iki biçimde yazılır ve @-quoted.</span><span class="sxs-lookup"><span data-stu-id="fc855-116">String literals are of type `string` and can be written in two forms, quoted and @-quoted.</span></span> <span data-ttu-id="fc855-117">Dize değişmez değerleri çift tırnak işaretleri (") içine alınan Teklif:</span><span class="sxs-lookup"><span data-stu-id="fc855-117">Quoted string literals are enclosed in double quotation marks ("):</span></span>

```csharp
"good morning"  // a string literal
```

<span data-ttu-id="fc855-118">Dize değişmez değerleri, sabit değer herhangi bir karakter içerebilir.</span><span class="sxs-lookup"><span data-stu-id="fc855-118">String literals can contain any character literal.</span></span> <span data-ttu-id="fc855-119">Kaçış dizileri dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="fc855-119">Escape sequences are included.</span></span> <span data-ttu-id="fc855-120">Aşağıdaki örnekte çıkış dizisi `\\` eğik için `\u0066` harfi f, için ve `\n` için yeni satır.</span><span class="sxs-lookup"><span data-stu-id="fc855-120">The following example uses escape sequence `\\` for backslash, `\u0066` for the letter f, and `\n` for newline.</span></span>

```csharp
string a = "\\\u0066\n";
Console.WriteLine(a);
```

> [!NOTE]
> <span data-ttu-id="fc855-121">Çıkış kodu `\udddd` (burada `dddd` bir dört basamaklı sayıdır) U + Unicode karakteri temsil eden`dddd`.</span><span class="sxs-lookup"><span data-stu-id="fc855-121">The escape code `\udddd` (where `dddd` is a four-digit number) represents the Unicode character U+`dddd`.</span></span> <span data-ttu-id="fc855-122">Sekiz basamağı Unicode atlatma kodları da tanınan: `\Udddddddd`.</span><span class="sxs-lookup"><span data-stu-id="fc855-122">Eight-digit Unicode escape codes are also recognized: `\Udddddddd`.</span></span>

<span data-ttu-id="fc855-123">Verbatim dize değişmez değerleri ile başlayıp `@` ve ayrıca çift tırnak işaretleri içine alınır.</span><span class="sxs-lookup"><span data-stu-id="fc855-123">Verbatim string literals start with `@` and are also enclosed in double quotation marks.</span></span> <span data-ttu-id="fc855-124">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="fc855-124">For example:</span></span>

```csharp
@"good morning"  // a string literal
```

<span data-ttu-id="fc855-125">Kaçış dizileri: avantajlarındandır harfi harfine dizeler *değil* işlenen, hangi kolaylaştırır, örneğin, tam olarak nitelenmiş dosya adını yazın:</span><span class="sxs-lookup"><span data-stu-id="fc855-125">The advantage of verbatim strings is that escape sequences are *not* processed, which makes it easy to write, for example, a fully qualified file name:</span></span>

```csharp
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"
```

<span data-ttu-id="fc855-126">Çift tırnak işareti eklemek için bir @-quoted , çift, dize:</span><span class="sxs-lookup"><span data-stu-id="fc855-126">To include a double quotation mark in an @-quoted string, double it:</span></span>

```csharp
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.
```

<span data-ttu-id="fc855-127">Diğer kullanımları için `@` özel karakter bkz [@--tam tanımlayıcı](../tokens/verbatim.md).</span><span class="sxs-lookup"><span data-stu-id="fc855-127">For other uses of the `@` special character, see [@ -- verbatim identifier](../tokens/verbatim.md).</span></span>

<span data-ttu-id="fc855-128">C# dizeleri hakkında daha fazla bilgi için bkz. [dizeleri](../../programming-guide/strings/index.md).</span><span class="sxs-lookup"><span data-stu-id="fc855-128">For more information about strings in C#, see [Strings](../../programming-guide/strings/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="fc855-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="fc855-129">Example</span></span>

[!code-csharp[csrefKeywordsTypes#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#17)]  

## <a name="c-language-specification"></a><span data-ttu-id="fc855-130">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="fc855-130">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="fc855-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc855-131">See also</span></span>

- [<span data-ttu-id="fc855-132">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="fc855-132">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="fc855-133">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="fc855-133">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="fc855-134">Dizeleri Kullanmak için En İyi Uygulamalar</span><span class="sxs-lookup"><span data-stu-id="fc855-134">Best Practices for Using Strings</span></span>](../../../standard/base-types/best-practices-strings.md)
- [<span data-ttu-id="fc855-135">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="fc855-135">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="fc855-136">Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="fc855-136">Reference Types</span></span>](reference-types.md)
- [<span data-ttu-id="fc855-137">Değer Türleri</span><span class="sxs-lookup"><span data-stu-id="fc855-137">Value Types</span></span>](value-types.md)
- [<span data-ttu-id="fc855-138">Temel Dize İşlemleri</span><span class="sxs-lookup"><span data-stu-id="fc855-138">Basic String Operations</span></span>](../../../standard/base-types/basic-string-operations.md)
- [<span data-ttu-id="fc855-139">Yeni Dizeler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fc855-139">Creating New Strings</span></span>](../../../standard/base-types/creating-new.md)
- [<span data-ttu-id="fc855-140">Sayısal Sonuçlar Tablosunu Biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="fc855-140">Formatting Numeric Results Table</span></span>](formatting-numeric-results-table.md)
