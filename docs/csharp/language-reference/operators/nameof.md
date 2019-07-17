---
title: nameof işlecinin - C# başvurusu
ms.custom: seodec18
ms.date: 07/12/2019
f1_keywords:
- nameof_CSharpKeyword
- nameof
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: 945a8a8ff6d96cb505fa10e85c21a93347661a23
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68238692"
---
# <a name="nameof-operator-c-reference"></a><span data-ttu-id="27e0c-102">nameof işlecinin (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="27e0c-102">nameof operator (C# reference)</span></span>

<span data-ttu-id="27e0c-103">`nameof` İşleci bir değişken, türü veya dize sabiti olarak üye adını alır:</span><span class="sxs-lookup"><span data-stu-id="27e0c-103">The `nameof` operator obtains the name of a variable, type, or member as the string constant:</span></span>

[!code-csharp-interactive[nameof operator](~/samples/csharp/language-reference/operators/NameOfOperator.cs#Examples)]

<span data-ttu-id="27e0c-104">Bir tür ve ad alanı, söz konusu olduğunda yukarıdaki örnekte gösterildiği gibi üretilen adı genellikle değil [tam](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span><span class="sxs-lookup"><span data-stu-id="27e0c-104">As the preceding example shows, in the case of a type and a namespace, the produced name is usually not [fully qualified](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span></span>

<span data-ttu-id="27e0c-105">`nameof` İşleci derleme zamanında değerlendirilir ve çalışma zamanında hiçbir etkisi olmaz.</span><span class="sxs-lookup"><span data-stu-id="27e0c-105">The `nameof` operator is evaluated at compile time, and has no effect at run time.</span></span>

<span data-ttu-id="27e0c-106">Kullanabileceğiniz `nameof` bağımsız değişken denetimi kod daha sürdürülebilir hale getirmek için işleç:</span><span class="sxs-lookup"><span data-stu-id="27e0c-106">You can use the `nameof` operator to make the argument-checking code more maintainable:</span></span>

[!code-csharp[nameof and argument check](~/samples/csharp/language-reference/operators/NameOfOperator.cs#ExceptionMessage)]

<span data-ttu-id="27e0c-107">`nameof` İşleci kullanılabilir C# 6 ve üzeri.</span><span class="sxs-lookup"><span data-stu-id="27e0c-107">The `nameof` operator is available in C# 6 and later.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="27e0c-108">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="27e0c-108">C# language specification</span></span>

<span data-ttu-id="27e0c-109">Daha fazla bilgi için [Nameof ifadeleri](~/_csharplang/spec/expressions.md#nameof-expressions) bölümünü [ C# dil belirtimi](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="27e0c-109">For more information, see the [Nameof expressions](~/_csharplang/spec/expressions.md#nameof-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="27e0c-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="27e0c-110">See also</span></span>

- [<span data-ttu-id="27e0c-111">C#başvuru</span><span class="sxs-lookup"><span data-stu-id="27e0c-111">C# reference</span></span>](../index.md)
- [<span data-ttu-id="27e0c-112">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="27e0c-112">C# operators</span></span>](index.md)
