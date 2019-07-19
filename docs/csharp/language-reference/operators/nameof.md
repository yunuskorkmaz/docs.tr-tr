---
title: NameOf işleci- C# başvuru
ms.custom: seodec18
ms.date: 07/12/2019
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof operator [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: 965b3e96a20906187df4c8693f050c550a747091
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331443"
---
# <a name="nameof-operator-c-reference"></a><span data-ttu-id="10f78-102">NameOf işleci (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="10f78-102">nameof operator (C# reference)</span></span>

<span data-ttu-id="10f78-103">`nameof` İşleci, dize sabiti olarak bir değişkenin, türün veya üyenin adını edinir:</span><span class="sxs-lookup"><span data-stu-id="10f78-103">The `nameof` operator obtains the name of a variable, type, or member as the string constant:</span></span>

[!code-csharp-interactive[nameof operator](~/samples/csharp/language-reference/operators/NameOfOperator.cs#Examples)]

<span data-ttu-id="10f78-104">Yukarıdaki örnekte gösterildiği gibi, bir tür ve ad alanı durumunda, oluşturulan ad genellikle [tam olarak nitelenir](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span><span class="sxs-lookup"><span data-stu-id="10f78-104">As the preceding example shows, in the case of a type and a namespace, the produced name is usually not [fully qualified](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span></span>

<span data-ttu-id="10f78-105">`nameof` İşleci derleme zamanında değerlendirilir ve çalışma zamanında hiçbir etkiye sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="10f78-105">The `nameof` operator is evaluated at compile time, and has no effect at run time.</span></span>

<span data-ttu-id="10f78-106">Bağımsız değişken denetleme kodunun `nameof` daha sürdürülebilir olması için işlecini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="10f78-106">You can use the `nameof` operator to make the argument-checking code more maintainable:</span></span>

[!code-csharp[nameof and argument check](~/samples/csharp/language-reference/operators/NameOfOperator.cs#ExceptionMessage)]

<span data-ttu-id="10f78-107">`nameof` İşleci C# 6 ve üzeri sürümlerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="10f78-107">The `nameof` operator is available in C# 6 and later.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="10f78-108">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="10f78-108">C# language specification</span></span>

<span data-ttu-id="10f78-109">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [NameOf ifadeleri](~/_csharplang/spec/expressions.md#nameof-expressions) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="10f78-109">For more information, see the [Nameof expressions](~/_csharplang/spec/expressions.md#nameof-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="10f78-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="10f78-110">See also</span></span>

- [<span data-ttu-id="10f78-111">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="10f78-111">C# reference</span></span>](../index.md)
- [<span data-ttu-id="10f78-112">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="10f78-112">C# operators</span></span>](index.md)
