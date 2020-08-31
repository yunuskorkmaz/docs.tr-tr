---
description: NameOf ifadesi-C# başvurusu
title: NameOf ifadesi-C# başvurusu
ms.date: 04/23/2020
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof expression [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: 04109cde2a1f9146bf9bb44f301272808797ded0
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89118318"
---
# <a name="nameof-expression-c-reference"></a><span data-ttu-id="f4942-103">NameOf ifadesi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="f4942-103">nameof expression (C# reference)</span></span>

<span data-ttu-id="f4942-104">Bir `nameof` ifade, dize sabiti olarak bir değişkenin, türün veya üyenin adını üretir:</span><span class="sxs-lookup"><span data-stu-id="f4942-104">A `nameof` expression produces the name of a variable, type, or member as the string constant:</span></span>

[!code-csharp-interactive[nameof expression](snippets/shared/NameOfOperator.cs#Examples)]

<span data-ttu-id="f4942-105">Yukarıdaki örnekte gösterildiği gibi, bir tür ve ad alanı durumunda, oluşturulan ad genellikle [tam olarak nitelenir](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span><span class="sxs-lookup"><span data-stu-id="f4942-105">As the preceding example shows, in the case of a type and a namespace, the produced name is usually not [fully qualified](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span></span>

<span data-ttu-id="f4942-106">Tam [tanımlayıcılar](../tokens/verbatim.md)söz konusu olduğunda, `@` Aşağıdaki örnekte gösterildiği gibi karakter bir adın parçası değildir:</span><span class="sxs-lookup"><span data-stu-id="f4942-106">In the case of [verbatim identifiers](../tokens/verbatim.md), the `@` character is not the part of a name, as the following example shows:</span></span>

[!code-csharp-interactive[nameof verbatim](snippets/shared/NameOfOperator.cs#Verbatim)]

<span data-ttu-id="f4942-107">Bir `nameof` ifade derleme zamanında değerlendirilir ve çalışma zamanında hiçbir etkiye sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="f4942-107">A `nameof` expression is evaluated at compile time and has no effect at run time.</span></span>

<span data-ttu-id="f4942-108">`nameof`Bağımsız değişken denetleme kodunun daha sürdürülebilir olması için bir ifade kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f4942-108">You can use a `nameof` expression to make the argument-checking code more maintainable:</span></span>

[!code-csharp[nameof and argument check](snippets/shared/NameOfOperator.cs#ExceptionMessage)]

<span data-ttu-id="f4942-109">`nameof`C# 6 ve sonrasında bir ifade mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="f4942-109">A `nameof` expression is available in C# 6 and later.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f4942-110">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="f4942-110">C# language specification</span></span>

<span data-ttu-id="f4942-111">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [NameOf ifadeleri](~/_csharplang/spec/expressions.md#nameof-expressions) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="f4942-111">For more information, see the [Nameof expressions](~/_csharplang/spec/expressions.md#nameof-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f4942-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f4942-112">See also</span></span>

- [<span data-ttu-id="f4942-113">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="f4942-113">C# reference</span></span>](../index.md)
- [<span data-ttu-id="f4942-114">C# işleçleri ve ifadeleri</span><span class="sxs-lookup"><span data-stu-id="f4942-114">C# operators and expressions</span></span>](index.md)
