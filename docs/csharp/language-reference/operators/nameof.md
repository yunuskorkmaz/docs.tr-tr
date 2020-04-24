---
title: NameOf ifadesi-C# başvurusu
ms.date: 04/23/2020
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof expression [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: d71acf0cf7d5cdcfa5310455af2120fa1f82d567
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135925"
---
# <a name="nameof-expression-c-reference"></a><span data-ttu-id="353ef-102">NameOf ifadesi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="353ef-102">nameof expression (C# reference)</span></span>

<span data-ttu-id="353ef-103">Bir `nameof` ifade, dize sabiti olarak bir değişkenin, türün veya üyenin adını üretir:</span><span class="sxs-lookup"><span data-stu-id="353ef-103">A `nameof` expression produces the name of a variable, type, or member as the string constant:</span></span>

[!code-csharp-interactive[nameof expression](snippets/NameOfOperator.cs#Examples)]

<span data-ttu-id="353ef-104">Yukarıdaki örnekte gösterildiği gibi, bir tür ve ad alanı durumunda, oluşturulan ad genellikle [tam olarak nitelenir](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span><span class="sxs-lookup"><span data-stu-id="353ef-104">As the preceding example shows, in the case of a type and a namespace, the produced name is usually not [fully qualified](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span></span>

<span data-ttu-id="353ef-105">Tam [tanımlayıcılar](../tokens/verbatim.md)söz konusu olduğunda, aşağıdaki örnekte `@` gösterildiği gibi karakter bir adın parçası değildir:</span><span class="sxs-lookup"><span data-stu-id="353ef-105">In the case of [verbatim identifiers](../tokens/verbatim.md), the `@` character is not the part of a name, as the following example shows:</span></span>

[!code-csharp-interactive[nameof verbatim](snippets/NameOfOperator.cs#Verbatim)]

<span data-ttu-id="353ef-106">Bir `nameof` ifade derleme zamanında değerlendirilir ve çalışma zamanında hiçbir etkiye sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="353ef-106">A `nameof` expression is evaluated at compile time and has no effect at run time.</span></span>

<span data-ttu-id="353ef-107">Bağımsız değişken denetleme kodunun `nameof` daha sürdürülebilir olması için bir ifade kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="353ef-107">You can use a `nameof` expression to make the argument-checking code more maintainable:</span></span>

[!code-csharp[nameof and argument check](snippets/NameOfOperator.cs#ExceptionMessage)]

<span data-ttu-id="353ef-108">C# `nameof` 6 ve sonrasında bir ifade mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="353ef-108">A `nameof` expression is available in C# 6 and later.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="353ef-109">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="353ef-109">C# language specification</span></span>

<span data-ttu-id="353ef-110">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [NameOf ifadeleri](~/_csharplang/spec/expressions.md#nameof-expressions) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="353ef-110">For more information, see the [Nameof expressions](~/_csharplang/spec/expressions.md#nameof-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="353ef-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="353ef-111">See also</span></span>

- [<span data-ttu-id="353ef-112">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="353ef-112">C# reference</span></span>](../index.md)
- [<span data-ttu-id="353ef-113">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="353ef-113">C# operators</span></span>](index.md)
