---
title: '@ - C# Referans'
ms.date: 02/09/2017
f1_keywords:
- '@_CSharpKeyword'
- '@'
helpviewer_keywords:
- '@ special character [C#]'
- '@ language element [C#]'
ms.assetid: 89bc7e53-85f5-478a-866d-1cca003c4e8c
ms.openlocfilehash: a3446eceb0d3c415e36ea1d2c7d8d6d34f65350d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712422"
---
# <a name="-c-reference"></a><span data-ttu-id="b0a3d-102">@ (C# Referans)</span><span class="sxs-lookup"><span data-stu-id="b0a3d-102">@ (C# Reference)</span></span>

<span data-ttu-id="b0a3d-103">Özel `@` karakter, tam anlamıyla tanımlayıcı olarak hizmet vermektedir.</span><span class="sxs-lookup"><span data-stu-id="b0a3d-103">The `@` special character serves as a verbatim identifier.</span></span> <span data-ttu-id="b0a3d-104">Aşağıdaki şekillerde kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="b0a3d-104">It can be used in the following ways:</span></span>

1. <span data-ttu-id="b0a3d-105">C# anahtar kelimelerinin tanımlayıcı olarak kullanılmasını sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="b0a3d-105">To enable C# keywords to be used as identifiers.</span></span> <span data-ttu-id="b0a3d-106">Karakter, `@` derleyicinin C# anahtar sözcüğü yerine tanımlayıcı olarak yorumlayabilmek için bir kod öğesi önekleri.</span><span class="sxs-lookup"><span data-stu-id="b0a3d-106">The `@` character prefixes a code element that the compiler is to interpret as an identifier rather than a C# keyword.</span></span> <span data-ttu-id="b0a3d-107">Aşağıdaki örnek, `@` bir `for` `for` döngüde kullandığı adlı bir tanımlayıcıtanımlamak için karakteri kullanır.</span><span class="sxs-lookup"><span data-stu-id="b0a3d-107">The following example uses the `@` character to define an identifier named `for` that it uses in a `for` loop.</span></span>

   [!code-csharp[verbatim1](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#1)]

1. <span data-ttu-id="b0a3d-108">Bir dize harfinin harfi harfine harfiharfini belirtmek için harfi harfi harfine yorumlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b0a3d-108">To indicate that a string literal is to be interpreted verbatim.</span></span> <span data-ttu-id="b0a3d-109">Bu `@` örnekteki *karakter, harfi harfine bir dize harfini*tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b0a3d-109">The `@` character in this instance defines a *verbatim string literal*.</span></span> <span data-ttu-id="b0a3d-110">Basit kaçış sekansları (ters eğik çizgi gibi), `"\\"` hexadecimal kaçış dizileri (büyük A `"\x0041"` için gibi) ve Unicode kaçış dizileri (a harfi `"\u0041"` için olduğu gibi) kelimenin tam anlamıyla yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="b0a3d-110">Simple escape sequences (such as `"\\"` for a backslash), hexadecimal escape sequences (such as `"\x0041"` for an uppercase A), and Unicode escape sequences (such as `"\u0041"` for an uppercase A) are interpreted literally.</span></span> <span data-ttu-id="b0a3d-111">Sadece bir alıntı`""`kaçış sırası ( ) kelimenin tam anlamıyla yorumlanmaz; tek bir tırnak işareti üretir.</span><span class="sxs-lookup"><span data-stu-id="b0a3d-111">Only a quote escape sequence (`""`) is not interpreted literally; it produces a single quotation mark.</span></span> <span data-ttu-id="b0a3d-112">Ayrıca, bir kelimenin tam olarak [interpolasyonlu dize](interpolated.md) `{{` ayraç kaçış dizileri durumunda ( ve `}}`) kelimenin tam anlamıyla yorumlanmaz; tek ayraç karakterleri üretirler.</span><span class="sxs-lookup"><span data-stu-id="b0a3d-112">Additionally, in case of a verbatim [interpolated string](interpolated.md) brace escape sequences (`{{` and `}}`) are not interpreted literally; they produce single brace characters.</span></span> <span data-ttu-id="b0a3d-113">Aşağıdaki örnek, biri normal bir dize literal, diğeri ise harfi harfine dize kullanarak iki özdeş dosya yolunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b0a3d-113">The following example defines two identical file paths, one by using a regular string literal and the other by using a verbatim string literal.</span></span> <span data-ttu-id="b0a3d-114">Bu, kelimenin tam anlamıyla dize literals daha yaygın kullanımlarından biridir.</span><span class="sxs-lookup"><span data-stu-id="b0a3d-114">This is one of the more common uses of verbatim string literals.</span></span>

   [!code-csharp[verbatim2](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#2)]

   <span data-ttu-id="b0a3d-115">Aşağıdaki örnekte, normal bir dize edebi ve aynı karakter dizilerini içeren bir harfi harfini tanımlamanın etkisi gösteriş verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b0a3d-115">The following example illustrates the effect of defining a regular string literal and a verbatim string literal that contain identical character sequences.</span></span>

   [!code-csharp[verbatim3](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#3)]

1. <span data-ttu-id="b0a3d-116">Derlemenin bir adlandırma çakışması durumlarında öznitelikleri ayırt etmesini sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="b0a3d-116">To enable the compiler to distinguish between attributes in cases of a naming conflict.</span></span> <span data-ttu-id="b0a3d-117">Öznitelik, <xref:System.Attribute>'den türeyen bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="b0a3d-117">An attribute is a class that derives from <xref:System.Attribute>.</span></span> <span data-ttu-id="b0a3d-118">Derleyici bu kuralı zorlamasa da, tür adı genellikle sonek **Özniteliğini**içerir.</span><span class="sxs-lookup"><span data-stu-id="b0a3d-118">Its type name typically includes the suffix **Attribute**, although the compiler does not enforce this convention.</span></span> <span data-ttu-id="b0a3d-119">Öznitelik daha sonra tam tür adı (örneğin, `[InfoAttribute]` ya da kısaltılmış adı (örneğin,) `[Info]`tarafından kod atıfta bulunulabilir.</span><span class="sxs-lookup"><span data-stu-id="b0a3d-119">The attribute can then be referenced in code either by its full type name (for example, `[InfoAttribute]` or its shortened name (for example, `[Info]`).</span></span> <span data-ttu-id="b0a3d-120">Ancak, iki kısaltılmış öznitelik türü adları aynıysa ve bir tür adı **Atöz** soneki içeriyorsa, ancak diğerinde yoksa bir adlandırma çakışması oluşur.</span><span class="sxs-lookup"><span data-stu-id="b0a3d-120">However, a naming conflict occurs if two shortened attribute type names are identical, and one type name includes the **Attribute** suffix but the other does not.</span></span> <span data-ttu-id="b0a3d-121">Örneğin, derleyici `Info` `InfoAttribute` `Example` sınıfa mı yoksa öznitelik mi uygulandığını belirleyemediğinden aşağıdaki kod derlenemez.</span><span class="sxs-lookup"><span data-stu-id="b0a3d-121">For example, the following code fails to compile because the compiler cannot determine whether the `Info` or `InfoAttribute` attribute is applied to the `Example` class.</span></span> <span data-ttu-id="b0a3d-122">Daha fazla bilgi için [CS1614'e](../compiler-messages/cs1614.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="b0a3d-122">See [CS1614](../compiler-messages/cs1614.md) for more information.</span></span>

   [!code-csharp[verbatim4](../../../../samples/snippets/csharp/language-reference/keywords/verbatim2.cs#1)]

## <a name="see-also"></a><span data-ttu-id="b0a3d-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0a3d-123">See also</span></span>

- [<span data-ttu-id="b0a3d-124">C# Referans</span><span class="sxs-lookup"><span data-stu-id="b0a3d-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b0a3d-125">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b0a3d-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b0a3d-126">C# Özel Karakterleri</span><span class="sxs-lookup"><span data-stu-id="b0a3d-126">C# Special Characters</span></span>](./index.md)
