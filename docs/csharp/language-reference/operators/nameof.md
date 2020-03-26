---
title: ifade adı - C# referansı
ms.date: 07/12/2019
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof expression [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: 5a68161be7bb03122d2a63ccef4365c5853862b2
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507145"
---
# <a name="nameof-expression-c-reference"></a><span data-ttu-id="9ba15-102">ifade adı (C# referansı)</span><span class="sxs-lookup"><span data-stu-id="9ba15-102">nameof expression (C# reference)</span></span>

<span data-ttu-id="9ba15-103">Bir `nameof` ifade, dize sabiti olarak bir değişkenin, yazın veya üyenin adını üretir:</span><span class="sxs-lookup"><span data-stu-id="9ba15-103">A `nameof` expression produces the name of a variable, type, or member as the string constant:</span></span>

[!code-csharp-interactive[nameof expression](snippets/NameOfOperator.cs#Examples)]

<span data-ttu-id="9ba15-104">Yukarıdaki örnekte de görüldüğü gibi, bir tür ve ad alanı durumunda, üretilen ad genellikle [tam olarak nitelikli](~/_csharplang/spec/basic-concepts.md#fully-qualified-names)değildir.</span><span class="sxs-lookup"><span data-stu-id="9ba15-104">As the preceding example shows, in the case of a type and a namespace, the produced name is usually not [fully qualified](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span></span>

<span data-ttu-id="9ba15-105">Bir `nameof` ifade derleme zamanında değerlendirilir ve çalışma zamanında hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="9ba15-105">A `nameof` expression is evaluated at compile time and has no effect at run time.</span></span>

<span data-ttu-id="9ba15-106">Bağımsız değişken `nameof` denetleme kodunu daha koruyabilir hale getirmek için bir ifade kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9ba15-106">You can use a `nameof` expression to make the argument-checking code more maintainable:</span></span>

[!code-csharp[nameof and argument check](snippets/NameOfOperator.cs#ExceptionMessage)]

<span data-ttu-id="9ba15-107">C# `nameof` 6 ve sonraki bir ifade kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9ba15-107">A `nameof` expression is available in C# 6 and later.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="9ba15-108">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="9ba15-108">C# language specification</span></span>

<span data-ttu-id="9ba15-109">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [İfadeler](~/_csharplang/spec/expressions.md#nameof-expressions) Bölümü'ne bakın.</span><span class="sxs-lookup"><span data-stu-id="9ba15-109">For more information, see the [Nameof expressions](~/_csharplang/spec/expressions.md#nameof-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9ba15-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9ba15-110">See also</span></span>

- [<span data-ttu-id="9ba15-111">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="9ba15-111">C# reference</span></span>](../index.md)
- [<span data-ttu-id="9ba15-112">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="9ba15-112">C# operators</span></span>](index.md)
