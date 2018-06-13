---
title: string (C# Başvurusu)
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
ms.openlocfilehash: f92a44283e59bd80421758a63b40bc5289c3628b
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2018
ms.locfileid: "34172168"
---
# <a name="string-c-reference"></a><span data-ttu-id="3aeaa-102">string (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="3aeaa-102">string (C# Reference)</span></span>
<span data-ttu-id="3aeaa-103">`string` Türü sıfır veya daha fazla Unicode karakterler dizisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3aeaa-103">The `string` type represents a sequence of zero or more Unicode characters.</span></span> <span data-ttu-id="3aeaa-104">`string` bir diğer adı için <xref:System.String> .NET içinde.</span><span class="sxs-lookup"><span data-stu-id="3aeaa-104">`string` is an alias for <xref:System.String> in .NET.</span></span>  
  
 <span data-ttu-id="3aeaa-105">Ancak `string` bir başvuru türü eşitlik işleçleri (`==` ve `!=`) değerlerini karşılaştırmak için tanımlanan `string` nesneleri, değil başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="3aeaa-105">Although `string` is a reference type, the equality operators (`==` and `!=`) are defined to compare the values of `string` objects, not references.</span></span> <span data-ttu-id="3aeaa-106">Bu, daha sezgisel dize eşitlik için test kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="3aeaa-106">This makes testing for string equality more intuitive.</span></span> <span data-ttu-id="3aeaa-107">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="3aeaa-107">For example:</span></span>  
  
```csharp  
string a = "hello";  
string b = "h";  
// Append to contents of 'b'  
b += "ello";  
Console.WriteLine(a == b);  
Console.WriteLine((object)a == (object)b);  
```  
  
 <span data-ttu-id="3aeaa-108">Bu "True" görüntüler ve ardından "False" dizeleri içeriğini eşdeğer olduğundan ancak `a` ve `b` aynı dize örneğine başvurmamasını sağlama.</span><span class="sxs-lookup"><span data-stu-id="3aeaa-108">This displays "True" and then "False" because the content of the strings are equivalent, but `a` and `b` do not refer to the same string instance.</span></span>  
  
 <span data-ttu-id="3aeaa-109">+ İşleci dizeleri art arda ekler:</span><span class="sxs-lookup"><span data-stu-id="3aeaa-109">The + operator concatenates strings:</span></span>  
  
```csharp  
string a = "good " + "morning";  
```  
  
 <span data-ttu-id="3aeaa-110">Bu, "Günaydın" içeren bir dize nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3aeaa-110">This creates a string object that contains "good morning".</span></span>  
  
 <span data-ttu-id="3aeaa-111">Dizelerdir *değişmez*--bir dize nesnesi içeriğini nesne oluşturulduktan sonra değiştirilemez, sözdizimi yapar ancak görünür Bunu yapmak gibi.</span><span class="sxs-lookup"><span data-stu-id="3aeaa-111">Strings are *immutable*--the contents of a string object cannot be changed after the object is created, although the syntax makes it appear as if you can do this.</span></span> <span data-ttu-id="3aeaa-112">Örneğin, bu kodu yazarken derleyici gerçekten yeni karakter dizisi tutmak için yeni bir dize nesnesi oluşturur ve bu yeni nesne B'ye atanır.</span><span class="sxs-lookup"><span data-stu-id="3aeaa-112">For example, when you write this code, the compiler actually creates a new string object to hold the new sequence of characters, and that new object is assigned to b.</span></span> <span data-ttu-id="3aeaa-113">"Y" dizesi sonra atık toplama için uygundur.</span><span class="sxs-lookup"><span data-stu-id="3aeaa-113">The string "h" is then eligible for garbage collection.</span></span>  
  
```csharp
string b = "h";  
b += "ello";  
```  
  
 <span data-ttu-id="3aeaa-114">[] İşleci tek tek karakter salt okunur erişim için kullanılan bir `string`:</span><span class="sxs-lookup"><span data-stu-id="3aeaa-114">The [] operator can be used for readonly access to individual characters of a `string`:</span></span>  
  
```csharp  
string str = "test";  
char x = str[2];  // x = 's';  
```  
  
 <span data-ttu-id="3aeaa-115">Dize değişmez değerleri türündedir `string` ve tırnak içine alınmış iki biçimde yazılabilir ve @-quoted.</span><span class="sxs-lookup"><span data-stu-id="3aeaa-115">String literals are of type `string` and can be written in two forms, quoted and @-quoted.</span></span> <span data-ttu-id="3aeaa-116">Değişmez değerler çift tırnak işaretleri (") arasına alınan sınırlandırılmış:</span><span class="sxs-lookup"><span data-stu-id="3aeaa-116">Quoted string literals are enclosed in double quotation marks ("):</span></span>  
  
```csharp  
"good morning"  // a string literal  
```  
  
 <span data-ttu-id="3aeaa-117">Dize değişmez değerleri değişmez değer herhangi bir karakter içerebilir.</span><span class="sxs-lookup"><span data-stu-id="3aeaa-117">String literals can contain any character literal.</span></span> <span data-ttu-id="3aeaa-118">Kaçış sıraları dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="3aeaa-118">Escape sequences are included.</span></span> <span data-ttu-id="3aeaa-119">Aşağıdaki örnek, kaçış sırası kullanır `\\` ters eğik çizgi için `\u0066` harfi f için ve `\n` yeni satır için.</span><span class="sxs-lookup"><span data-stu-id="3aeaa-119">The following example uses escape sequence `\\` for backslash, `\u0066` for the letter f, and `\n` for newline.</span></span>  
  
```csharp  
string a = "\\\u0066\n";  
Console.WriteLine(a);  
```  
  
> [!NOTE]
>  <span data-ttu-id="3aeaa-120">Çıkış kodu `\udddd` (burada `dddd` dört basamaklı bir sayı değil) Unicode karakteri U + temsil eden`dddd`.</span><span class="sxs-lookup"><span data-stu-id="3aeaa-120">The escape code `\udddd` (where `dddd` is a four-digit number) represents the Unicode character U+`dddd`.</span></span> <span data-ttu-id="3aeaa-121">Sekiz basamaklı Unicode çıkış kodları ayrıca tanınan: `\Udddddddd`.</span><span class="sxs-lookup"><span data-stu-id="3aeaa-121">Eight-digit Unicode escape codes are also recognized: `\Udddddddd`.</span></span>  
  
 <span data-ttu-id="3aeaa-122">Harfi harfine dize değişmez değerleri başlayarak `@` ve ayrıca çift tırnak işaretleri içine alınır.</span><span class="sxs-lookup"><span data-stu-id="3aeaa-122">Verbatim string literals start with `@` and are also enclosed in double quotation marks.</span></span> <span data-ttu-id="3aeaa-123">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="3aeaa-123">For example:</span></span>  
  
```csharp  
@"good morning"  // a string literal  
```  
  
 <span data-ttu-id="3aeaa-124">Harfi harfine dizeler avantajlarından kaçış sıraları olmasıdır *değil* işlenen, hangi kolaylaştırır yazma, örneğin, bir tam dosya adı:</span><span class="sxs-lookup"><span data-stu-id="3aeaa-124">The advantage of verbatim strings is that escape sequences are *not* processed, which makes it easy to write, for example, a fully qualified file name:</span></span>  
  
```csharp  
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"  
```  
  
 <span data-ttu-id="3aeaa-125">Çift tırnak işareti içinde dahil etmek için bir @-quoted dize, onu çift:</span><span class="sxs-lookup"><span data-stu-id="3aeaa-125">To include a double quotation mark in an @-quoted string, double it:</span></span>  
  
```csharp  
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.  
```  
  
 <span data-ttu-id="3aeaa-126">Diğer kullanımlar için `@` özel karakter bkz [@--verbatim tanımlayıcı](../tokens/verbatim.md).</span><span class="sxs-lookup"><span data-stu-id="3aeaa-126">For other uses of the `@` special character, see [@ -- verbatim identifier](../tokens/verbatim.md).</span></span>  
  
 <span data-ttu-id="3aeaa-127">C# dizeleri hakkında daha fazla bilgi için bkz: [dizeleri](../../../csharp/programming-guide/strings/index.md).</span><span class="sxs-lookup"><span data-stu-id="3aeaa-127">For more information about strings in C#, see [Strings](../../../csharp/programming-guide/strings/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3aeaa-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="3aeaa-128">Example</span></span>  
 [!code-csharp[csrefKeywordsTypes#17](../../../csharp/language-reference/keywords/codesnippet/CSharp/string_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="3aeaa-129">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="3aeaa-129">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3aeaa-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3aeaa-130">See Also</span></span>  
 [<span data-ttu-id="3aeaa-131">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="3aeaa-131">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="3aeaa-132">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="3aeaa-132">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="3aeaa-133">Dizeleri Kullanmak için En İyi Uygulamalar</span><span class="sxs-lookup"><span data-stu-id="3aeaa-133">Best Practices for Using Strings</span></span>](../../../standard/base-types/best-practices-strings.md)  
 [<span data-ttu-id="3aeaa-134">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="3aeaa-134">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="3aeaa-135">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="3aeaa-135">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="3aeaa-136">Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="3aeaa-136">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
 [<span data-ttu-id="3aeaa-137">Değer Türleri</span><span class="sxs-lookup"><span data-stu-id="3aeaa-137">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
 [<span data-ttu-id="3aeaa-138">Temel Dize İşlemleri</span><span class="sxs-lookup"><span data-stu-id="3aeaa-138">Basic String Operations</span></span>](../../../standard/base-types/basic-string-operations.md)  
 [<span data-ttu-id="3aeaa-139">Yeni Dizeler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="3aeaa-139">Creating New Strings</span></span>](../../../standard/base-types/creating-new.md)  
 [<span data-ttu-id="3aeaa-140">Sayısal Sonuçlar Tablosunu Biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="3aeaa-140">Formatting Numeric Results Table</span></span>](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md)
