---
title: işlecinin adı - C# referansı
ms.date: 07/12/2019
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof operator [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: ffbc801acf61bf72db1c88912dc2142a478fa280
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846278"
---
# <a name="nameof-operator-c-reference"></a><span data-ttu-id="e150c-102">işlecinin adı (C# referansı)</span><span class="sxs-lookup"><span data-stu-id="e150c-102">nameof operator (C# reference)</span></span>

<span data-ttu-id="e150c-103">İşleç, `nameof` dize sabiti olarak bir değişkenin, yazın veya üyenin adını alır:</span><span class="sxs-lookup"><span data-stu-id="e150c-103">The `nameof` operator obtains the name of a variable, type, or member as the string constant:</span></span>

[!code-csharp-interactive[nameof operator](snippets/NameOfOperator.cs#Examples)]

<span data-ttu-id="e150c-104">Yukarıdaki örnekte de görüldüğü gibi, bir tür ve ad alanı durumunda, üretilen ad genellikle [tam olarak nitelikli](~/_csharplang/spec/basic-concepts.md#fully-qualified-names)değildir.</span><span class="sxs-lookup"><span data-stu-id="e150c-104">As the preceding example shows, in the case of a type and a namespace, the produced name is usually not [fully qualified](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span></span>

<span data-ttu-id="e150c-105">Operatör `nameof` derleme zamanında değerlendirilir ve çalışma zamanında hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="e150c-105">The `nameof` operator is evaluated at compile time and has no effect at run time.</span></span>

<span data-ttu-id="e150c-106">Bağımsız değişken `nameof` denetimi kodunu daha koruyabilir hale getirmek için işleci kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e150c-106">You can use the `nameof` operator to make the argument-checking code more maintainable:</span></span>

[!code-csharp[nameof and argument check](snippets/NameOfOperator.cs#ExceptionMessage)]

<span data-ttu-id="e150c-107">Operatör `nameof` C# 6 ve sonrası mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="e150c-107">The `nameof` operator is available in C# 6 and later.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e150c-108">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="e150c-108">C# language specification</span></span>

<span data-ttu-id="e150c-109">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [İfadeler](~/_csharplang/spec/expressions.md#nameof-expressions) Bölümü'ne bakın.</span><span class="sxs-lookup"><span data-stu-id="e150c-109">For more information, see the [Nameof expressions](~/_csharplang/spec/expressions.md#nameof-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e150c-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e150c-110">See also</span></span>

- [<span data-ttu-id="e150c-111">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="e150c-111">C# reference</span></span>](../index.md)
- [<span data-ttu-id="e150c-112">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="e150c-112">C# operators</span></span>](index.md)
