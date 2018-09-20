---
title: (, C# Başvurusu)
ms.date: 02/09/2017
f1_keywords:
- '@_CSharpKeyword'
- '@'
helpviewer_keywords:
- '@ special character [C#]'
- '@ language element [C#]'
ms.assetid: 89bc7e53-85f5-478a-866d-1cca003c4e8c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6d6da87159e3ec9184eaa76ad069102204e2fcfc
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46470931"
---
# <a name="-c-reference"></a><span data-ttu-id="778ad-102">(, C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="778ad-102">@ (C# Reference)</span></span>

<span data-ttu-id="778ad-103">`@` Özel karakter bir tam tanımlayıcı işlevi görür.</span><span class="sxs-lookup"><span data-stu-id="778ad-103">The `@` special character serves as a verbatim identifier.</span></span> <span data-ttu-id="778ad-104">Aşağıdaki şekillerde kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="778ad-104">It can be used in the following ways:</span></span>

1. <span data-ttu-id="778ad-105">Tanımlayıcı olarak kullanılacak C# anahtar sözcükleri etkinleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="778ad-105">To enable C# keywords to be used as identifiers.</span></span> <span data-ttu-id="778ad-106">`@` Karakter derleyici C# anahtar sözcüğü yerine bir tanımlayıcı olarak yorumlamak için bir kod öğesi ekler.</span><span class="sxs-lookup"><span data-stu-id="778ad-106">The `@` character prefixes a code element that the compiler is to interpret as an identifier rather than a C# keyword.</span></span> <span data-ttu-id="778ad-107">Aşağıdaki örnekte `@` adlı bir tanımlayıcının tanımlamak için karakter `for` de kullanan bir `for` döngü.</span><span class="sxs-lookup"><span data-stu-id="778ad-107">The following example uses the `@` character to define an identifier named `for` that it uses in a `for` loop.</span></span>

   [!code-csharp[verbatim1](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#1)]

1. <span data-ttu-id="778ad-108">Bir dize sabit değeri verbatim yorumlanacağını olduğunu belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="778ad-108">To indicate that a string literal is to be interpreted verbatim.</span></span> <span data-ttu-id="778ad-109">`@` Karakterin bu örneğinde tanımlayan bir *verbatim dize sabit değeri*.</span><span class="sxs-lookup"><span data-stu-id="778ad-109">The `@` character in this instance defines a *verbatim string literal*.</span></span> <span data-ttu-id="778ad-110">Basit çıkış sıraları (gibi `"\\"` için ters eğik çizgi), onaltılık kaçış dizilerine (gibi `"\x0041"` bir büyük harf a) ve Unicode kaçış dizileri (gibi `"\u0041"` bir büyük harf a) genel anlamıyla yorumlanması.</span><span class="sxs-lookup"><span data-stu-id="778ad-110">Simple escape sequences (such as `"\\"` for a backslash), hexadecimal escape sequences (such as `"\x0041"` for an uppercase A), and Unicode escape sequences (such as `"\u0041"` for an uppercase A) are interpreted literally.</span></span> <span data-ttu-id="778ad-111">Yalnızca bir teklif kaçış dizisi (`""`) yorumlanmaması tam anlamıyla; bu tek tırnak işareti üretir.</span><span class="sxs-lookup"><span data-stu-id="778ad-111">Only a quote escape sequence (`""`) is not interpreted literally; it produces a single quotation mark.</span></span> <span data-ttu-id="778ad-112">Ayrıca, durumunda bir verbatim [ilişkilendirilmiş bir dizedir](interpolated.md) küme ayracı kaçış dizilerine (`{{` ve `}}`) değil olarak yorumlanır tek küme ayracı karakterleri tam anlamıyla; ürettikleri.</span><span class="sxs-lookup"><span data-stu-id="778ad-112">Additionally, in case of a verbatim [interpolated string](interpolated.md) brace escape sequences (`{{` and `}}`) are not interpreted literally; they produce single brace characters.</span></span> <span data-ttu-id="778ad-113">Aşağıdaki örnek, bir normal bir dize sabit değeri ve diğer verbatim dize değişmez değeri kullanarak iki aynı dosya yolları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="778ad-113">The following example defines two identical file paths, one by using a regular string literal and the other by using a verbatim string literal.</span></span> <span data-ttu-id="778ad-114">Bu, aynen dize değişmez değerleri daha yaygın kullanımlarından biridir.</span><span class="sxs-lookup"><span data-stu-id="778ad-114">This is one of the more common uses of verbatim string literals.</span></span>

   [!code-csharp[verbatim2](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#2)]

   <span data-ttu-id="778ad-115">Aşağıdaki örnek, normal bir dize sabit değeri ve aynı karakter dizileri içeren sabit bir verbatim dizesi tanımlama etkisini gösterir.</span><span class="sxs-lookup"><span data-stu-id="778ad-115">The following example illustrates the effect of defining a regular string literal and a verbatim string literal that contain identical character sequences.</span></span>

   [!code-csharp[verbatim3](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#3)]

1. <span data-ttu-id="778ad-116">Ad çakışması örneklerini öznitelikleri arasında ayrım yapmak derleyici etkinleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="778ad-116">To enable the compiler to distinguish between attributes in cases of a naming conflict.</span></span> <span data-ttu-id="778ad-117">Türetilen bir sınıf bir özniteliktir <xref:System.Attribute>.</span><span class="sxs-lookup"><span data-stu-id="778ad-117">An attribute is a class that derives from <xref:System.Attribute>.</span></span> <span data-ttu-id="778ad-118">Tür adı genellikle soneki içerir **özniteliği**, ancak derleyici, bu kural uygulamaz.</span><span class="sxs-lookup"><span data-stu-id="778ad-118">Its type name typically includes the suffix **Attribute**, although the compiler does not enforce this convention.</span></span> <span data-ttu-id="778ad-119">Öznitelik başvurulabilir tam tür adıyla ya da kod (örneğin, `[InfoAttribute]` ya da kısaltılmış adını (örneğin, `[Info]`).</span><span class="sxs-lookup"><span data-stu-id="778ad-119">The attribute can then be referenced in code either by its full type name (for example, `[InfoAttribute]` or its shortened name (for example, `[Info]`).</span></span> <span data-ttu-id="778ad-120">İki kısalttık, ancak bir adlandırma çakışması öznitelik türü adları aynıdır ve bir tür adını içeren meydana gelir **özniteliği** soneki ancak diğer desteklemez.</span><span class="sxs-lookup"><span data-stu-id="778ad-120">However, a naming conflict occurs if two shortened attribute type names are identical, and one type name includes the **Attribute** suffix but the other does not.</span></span> <span data-ttu-id="778ad-121">Örneğin, aşağıdaki kod derleyici belirlenemiyor çünkü derleme başarısız olup olmadığını `Info` veya `InfoAttribute` özniteliği uygulandığı `Example` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="778ad-121">For example, the following code fails to compile because the compiler cannot determine whether the `Info` or `InfoAttribute` attribute is applied to the `Example` class.</span></span> <span data-ttu-id="778ad-122">Bkz: [CS1614](../compiler-messages/cs1614.md) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="778ad-122">See [CS1614](../compiler-messages/cs1614.md) for more information.</span></span>

   [!code-csharp[verbatim4](../../../../samples/snippets/csharp/language-reference/keywords/verbatim2.cs#1)]

## <a name="see-also"></a><span data-ttu-id="778ad-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="778ad-123">See Also</span></span>

- [<span data-ttu-id="778ad-124">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="778ad-124">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="778ad-125">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="778ad-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="778ad-126">C# Özel Karakterleri</span><span class="sxs-lookup"><span data-stu-id="778ad-126">C# Special Characters</span></span>](../../../csharp/language-reference/tokens/index.md)
