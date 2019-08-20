---
title: '@- C# Reference'
ms.custom: seodec18
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
ms.openlocfilehash: b2290c87f7d4d2ba8da122d4f5ddb9ea423852ec
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608726"
---
# <a name="-c-reference"></a><span data-ttu-id="25dfb-102">@ (C# Başvuru)</span><span class="sxs-lookup"><span data-stu-id="25dfb-102">@ (C# Reference)</span></span>

<span data-ttu-id="25dfb-103">Özel `@` karakter, tam tanımlayıcı işlevi görür.</span><span class="sxs-lookup"><span data-stu-id="25dfb-103">The `@` special character serves as a verbatim identifier.</span></span> <span data-ttu-id="25dfb-104">Aşağıdaki yollarla kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="25dfb-104">It can be used in the following ways:</span></span>

1. <span data-ttu-id="25dfb-105">Anahtar kelimeleri C# tanımlayıcı olarak kullanılacak şekilde etkinleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="25dfb-105">To enable C# keywords to be used as identifiers.</span></span> <span data-ttu-id="25dfb-106">Karakter, derleyicinin bir C# anahtar sözcük yerine bir tanımlayıcı olarak yorumlanacağı bir kod öğesi ön ekine sahiptir. `@`</span><span class="sxs-lookup"><span data-stu-id="25dfb-106">The `@` character prefixes a code element that the compiler is to interpret as an identifier rather than a C# keyword.</span></span> <span data-ttu-id="25dfb-107">Aşağıdaki örnek, bir `@` `for` döngüsünde kullandığı adlı `for` bir tanımlayıcıyı tanımlamak için karakterini kullanır.</span><span class="sxs-lookup"><span data-stu-id="25dfb-107">The following example uses the `@` character to define an identifier named `for` that it uses in a `for` loop.</span></span>

   [!code-csharp[verbatim1](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#1)]

1. <span data-ttu-id="25dfb-108">Dize sabit değerinin tam olarak yorumlandığını göstermek için.</span><span class="sxs-lookup"><span data-stu-id="25dfb-108">To indicate that a string literal is to be interpreted verbatim.</span></span> <span data-ttu-id="25dfb-109">Bu `@` örnekteki karakter, tam bir *dize sabit değeri*tanımlar.</span><span class="sxs-lookup"><span data-stu-id="25dfb-109">The `@` character in this instance defines a *verbatim string literal*.</span></span> <span data-ttu-id="25dfb-110">Basit kaçış dizileri ( `"\\"` ters eğik çizgi gibi), onaltılık kaçış dizileri ( `"\x0041"` büyük a için gibi) ve Unicode kaçış dizileri (örn. bir büyük harf a `"\u0041"` ), tam olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="25dfb-110">Simple escape sequences (such as `"\\"` for a backslash), hexadecimal escape sequences (such as `"\x0041"` for an uppercase A), and Unicode escape sequences (such as `"\u0041"` for an uppercase A) are interpreted literally.</span></span> <span data-ttu-id="25dfb-111">Yalnızca bir Quote kaçış sırası (`""`), tam olarak yorumlanmaz; tek tırnak işareti üretir.</span><span class="sxs-lookup"><span data-stu-id="25dfb-111">Only a quote escape sequence (`""`) is not interpreted literally; it produces a single quotation mark.</span></span> <span data-ttu-id="25dfb-112">Bunlara ek olarak, tam olarak bulunan bir [dize](interpolated.md) ayracı kaçış dizileri (`{{` ve `}}`), tam olarak yorumlanmaz; tek küme ayracı karakterleri üretir.</span><span class="sxs-lookup"><span data-stu-id="25dfb-112">Additionally, in case of a verbatim [interpolated string](interpolated.md) brace escape sequences (`{{` and `}}`) are not interpreted literally; they produce single brace characters.</span></span> <span data-ttu-id="25dfb-113">Aşağıdaki örnek, biri normal dize değişmez değeri ve diğeri de tam olarak bir dize sabiti kullanarak iki özdeş dosya yolunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="25dfb-113">The following example defines two identical file paths, one by using a regular string literal and the other by using a verbatim string literal.</span></span> <span data-ttu-id="25dfb-114">Bu, tam dize değişmez değerlerinin yaygın kullanımlarındaki bir biridir.</span><span class="sxs-lookup"><span data-stu-id="25dfb-114">This is one of the more common uses of verbatim string literals.</span></span>

   [!code-csharp[verbatim2](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#2)]

   <span data-ttu-id="25dfb-115">Aşağıdaki örnek, bir normal dize sabit değeri ve özdeş karakter dizileri içeren tam bir dize sabiti tanımlamanın etkisini gösterir.</span><span class="sxs-lookup"><span data-stu-id="25dfb-115">The following example illustrates the effect of defining a regular string literal and a verbatim string literal that contain identical character sequences.</span></span>

   [!code-csharp[verbatim3](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#3)]

1. <span data-ttu-id="25dfb-116">Derleyicinin, bir adlandırma çakışması durumunda öznitelikleri birbirinden ayırt etmek üzere etkinleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="25dfb-116">To enable the compiler to distinguish between attributes in cases of a naming conflict.</span></span> <span data-ttu-id="25dfb-117">Öznitelik, öğesinden <xref:System.Attribute>türetilen bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="25dfb-117">An attribute is a class that derives from <xref:System.Attribute>.</span></span> <span data-ttu-id="25dfb-118">Tür adı genellikle sonek **özniteliğini**içerir, ancak derleyici bu kuralı zorlamaz.</span><span class="sxs-lookup"><span data-stu-id="25dfb-118">Its type name typically includes the suffix **Attribute**, although the compiler does not enforce this convention.</span></span> <span data-ttu-id="25dfb-119">Daha sonra özniteliğe, tam tür adı (örneğin, `[InfoAttribute]` veya kısaltılmış adı) ile (örneğin, `[Info]`) başvuruda bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="25dfb-119">The attribute can then be referenced in code either by its full type name (for example, `[InfoAttribute]` or its shortened name (for example, `[Info]`).</span></span> <span data-ttu-id="25dfb-120">Ancak, iki kısaltılmış öznitelik türü adı özdeş ise ve bir tür adı **öznitelik** sonekini içeriyorsa ancak diğeri yoksa, bir adlandırma çakışması oluşur.</span><span class="sxs-lookup"><span data-stu-id="25dfb-120">However, a naming conflict occurs if two shortened attribute type names are identical, and one type name includes the **Attribute** suffix but the other does not.</span></span> <span data-ttu-id="25dfb-121">Örneğin, derleyici `Info` veya `InfoAttribute` `Example` özniteliğinin sınıfa uygulanıp uygulanmadığını belirleyemediği için aşağıdaki kod derlenemiyor.</span><span class="sxs-lookup"><span data-stu-id="25dfb-121">For example, the following code fails to compile because the compiler cannot determine whether the `Info` or `InfoAttribute` attribute is applied to the `Example` class.</span></span> <span data-ttu-id="25dfb-122">Daha fazla bilgi için bkz. [CS1614](../compiler-messages/cs1614.md) .</span><span class="sxs-lookup"><span data-stu-id="25dfb-122">See [CS1614](../compiler-messages/cs1614.md) for more information.</span></span>

   [!code-csharp[verbatim4](../../../../samples/snippets/csharp/language-reference/keywords/verbatim2.cs#1)]

## <a name="see-also"></a><span data-ttu-id="25dfb-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="25dfb-123">See also</span></span>

- [<span data-ttu-id="25dfb-124">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="25dfb-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="25dfb-125">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="25dfb-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="25dfb-126">C# Özel Karakterleri</span><span class="sxs-lookup"><span data-stu-id="25dfb-126">C# Special Characters</span></span>](./index.md)
