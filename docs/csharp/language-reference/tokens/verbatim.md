---
description: '@-C# başvurusu'
title: '@-C# başvurusu'
ms.date: 02/09/2017
f1_keywords:
- '@_CSharpKeyword'
- '@'
helpviewer_keywords:
- '@ special character [C#]'
- '@ language element [C#]'
ms.assetid: 89bc7e53-85f5-478a-866d-1cca003c4e8c
ms.openlocfilehash: 7d78b28479ed6128321207073dc94976710f10b6
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89138910"
---
# <a name="-c-reference"></a><span data-ttu-id="0113d-103">@ (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="0113d-103">@ (C# Reference)</span></span>

<span data-ttu-id="0113d-104">`@`Özel karakter, tam tanımlayıcı işlevi görür.</span><span class="sxs-lookup"><span data-stu-id="0113d-104">The `@` special character serves as a verbatim identifier.</span></span> <span data-ttu-id="0113d-105">Aşağıdaki yollarla kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="0113d-105">It can be used in the following ways:</span></span>

1. <span data-ttu-id="0113d-106">C# anahtar sözcüklerini tanımlayıcı olarak kullanılacak şekilde etkinleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="0113d-106">To enable C# keywords to be used as identifiers.</span></span> <span data-ttu-id="0113d-107">`@`Karakter, derleyicinin bir C# anahtar sözcüğü yerine bir tanımlayıcı olarak yorumlanacağı bir kod öğesi ön ekine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="0113d-107">The `@` character prefixes a code element that the compiler is to interpret as an identifier rather than a C# keyword.</span></span> <span data-ttu-id="0113d-108">Aşağıdaki örnek, `@` bir döngüsünde kullandığı adlı bir tanımlayıcıyı tanımlamak için karakterini kullanır `for` `for` .</span><span class="sxs-lookup"><span data-stu-id="0113d-108">The following example uses the `@` character to define an identifier named `for` that it uses in a `for` loop.</span></span>

   [!code-csharp[verbatim1](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#1)]

1. <span data-ttu-id="0113d-109">Dize sabit değerinin tam olarak yorumlandığını göstermek için.</span><span class="sxs-lookup"><span data-stu-id="0113d-109">To indicate that a string literal is to be interpreted verbatim.</span></span> <span data-ttu-id="0113d-110">`@`Bu örnekteki karakter, tam bir *dize sabit değeri*tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0113d-110">The `@` character in this instance defines a *verbatim string literal*.</span></span> <span data-ttu-id="0113d-111">Basit kaçış dizileri ( `"\\"` ters eğik çizgi gibi), onaltılık kaçış dizileri ( `"\x0041"` büyük a için gibi) ve Unicode kaçış dizileri (örn `"\u0041"` . bir büyük harf a), tam olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="0113d-111">Simple escape sequences (such as `"\\"` for a backslash), hexadecimal escape sequences (such as `"\x0041"` for an uppercase A), and Unicode escape sequences (such as `"\u0041"` for an uppercase A) are interpreted literally.</span></span> <span data-ttu-id="0113d-112">Yalnızca bir Quote kaçış sırası ( `""` ), tam olarak yorumlanmaz; bir çift tırnak işareti üretir.</span><span class="sxs-lookup"><span data-stu-id="0113d-112">Only a quote escape sequence (`""`) is not interpreted literally; it produces one double quotation mark.</span></span> <span data-ttu-id="0113d-113">Bunlara ek olarak, tam olarak bulunan bir [dize](interpolated.md) ayracı kaçış dizileri ( `{{` ve), tam olarak `}}` yorumlanmaz; tek küme ayracı karakterleri üretir.</span><span class="sxs-lookup"><span data-stu-id="0113d-113">Additionally, in case of a verbatim [interpolated string](interpolated.md) brace escape sequences (`{{` and `}}`) are not interpreted literally; they produce single brace characters.</span></span> <span data-ttu-id="0113d-114">Aşağıdaki örnek, biri normal dize değişmez değeri ve diğeri de tam olarak bir dize sabiti kullanarak iki özdeş dosya yolunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0113d-114">The following example defines two identical file paths, one by using a regular string literal and the other by using a verbatim string literal.</span></span> <span data-ttu-id="0113d-115">Bu, tam dize değişmez değerlerinin yaygın kullanımlarındaki bir biridir.</span><span class="sxs-lookup"><span data-stu-id="0113d-115">This is one of the more common uses of verbatim string literals.</span></span>

   [!code-csharp[verbatim2](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#2)]

   <span data-ttu-id="0113d-116">Aşağıdaki örnek, bir normal dize sabit değeri ve özdeş karakter dizileri içeren tam bir dize sabiti tanımlamanın etkisini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0113d-116">The following example illustrates the effect of defining a regular string literal and a verbatim string literal that contain identical character sequences.</span></span>

   [!code-csharp[verbatim3](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#3)]

1. <span data-ttu-id="0113d-117">Derleyicinin, bir adlandırma çakışması durumunda öznitelikleri birbirinden ayırt etmek üzere etkinleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="0113d-117">To enable the compiler to distinguish between attributes in cases of a naming conflict.</span></span> <span data-ttu-id="0113d-118">Öznitelik, öğesinden türetilen bir sınıftır <xref:System.Attribute> .</span><span class="sxs-lookup"><span data-stu-id="0113d-118">An attribute is a class that derives from <xref:System.Attribute>.</span></span> <span data-ttu-id="0113d-119">Tür adı genellikle sonek **özniteliğini**içerir, ancak derleyici bu kuralı zorlamaz.</span><span class="sxs-lookup"><span data-stu-id="0113d-119">Its type name typically includes the suffix **Attribute**, although the compiler does not enforce this convention.</span></span> <span data-ttu-id="0113d-120">Daha sonra özniteliğe, tam tür adı (örneğin, `[InfoAttribute]` veya kısaltılmış adı) ile (örneğin,) başvuruda bulunabilir `[Info]` .</span><span class="sxs-lookup"><span data-stu-id="0113d-120">The attribute can then be referenced in code either by its full type name (for example, `[InfoAttribute]` or its shortened name (for example, `[Info]`).</span></span> <span data-ttu-id="0113d-121">Ancak, iki kısaltılmış öznitelik türü adı özdeş ise ve bir tür adı **öznitelik** sonekini içeriyorsa ancak diğeri yoksa, bir adlandırma çakışması oluşur.</span><span class="sxs-lookup"><span data-stu-id="0113d-121">However, a naming conflict occurs if two shortened attribute type names are identical, and one type name includes the **Attribute** suffix but the other does not.</span></span> <span data-ttu-id="0113d-122">Örneğin, derleyici `Info` veya `InfoAttribute` özniteliğinin sınıfa uygulanıp uygulanmadığını belirleyemediği için aşağıdaki kod derlenemiyor `Example` .</span><span class="sxs-lookup"><span data-stu-id="0113d-122">For example, the following code fails to compile because the compiler cannot determine whether the `Info` or `InfoAttribute` attribute is applied to the `Example` class.</span></span> <span data-ttu-id="0113d-123">Daha fazla bilgi için bkz. [CS1614](../compiler-messages/cs1614.md) .</span><span class="sxs-lookup"><span data-stu-id="0113d-123">See [CS1614](../compiler-messages/cs1614.md) for more information.</span></span>

   [!code-csharp[verbatim4](../../../../samples/snippets/csharp/language-reference/keywords/verbatim2.cs#1)]

## <a name="see-also"></a><span data-ttu-id="0113d-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0113d-124">See also</span></span>

- [<span data-ttu-id="0113d-125">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="0113d-125">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0113d-126">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0113d-126">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="0113d-127">C# özel karakterleri</span><span class="sxs-lookup"><span data-stu-id="0113d-127">C# Special Characters</span></span>](./index.md)
