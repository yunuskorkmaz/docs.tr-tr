---
title: void C# başvurusu
ms.date: 02/11/2020
f1_keywords:
- void_CSharpKeyword
- void
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
ms.openlocfilehash: f7ca3f83bc1980a16e45f22bbfd51e6861b0e5e7
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453834"
---
# <a name="void-c-reference"></a><span data-ttu-id="b5979-102">void (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="b5979-102">void (C# reference)</span></span>

<span data-ttu-id="b5979-103">Yöntemin bir değer döndürmediğini belirtmek için bir [yöntemin](../../programming-guide/classes-and-structs/methods.md) dönüş türü (veya [yerel bir işlev](../../programming-guide/classes-and-structs/local-functions.md)) olarak `void` kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="b5979-103">You use `void` as the return type of a [method](../../programming-guide/classes-and-structs/methods.md) (or a [local function](../../programming-guide/classes-and-structs/local-functions.md)) to specify that the method doesn't return a value.</span></span>

[!code-csharp[void method](~/samples/csharp/language-reference/builtin-types/VoidType.cs#VoidExample)]

<span data-ttu-id="b5979-104">`void`, bilinmeyen bir türe yönelik bir işaretçi bildirmek için, başvurulan tür olarak da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5979-104">You can also use `void` as a referent type to declare a pointer to an unknown type.</span></span> <span data-ttu-id="b5979-105">Daha fazla bilgi için bkz. [işaretçi türleri](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span><span class="sxs-lookup"><span data-stu-id="b5979-105">For more information, see [Pointer types](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span></span>

<span data-ttu-id="b5979-106">Bir değişkenin türü olarak `void` kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="b5979-106">You cannot use `void` as the type of a variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="b5979-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b5979-107">See also</span></span>

- [<span data-ttu-id="b5979-108">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="b5979-108">C# reference</span></span>](../index.md)
- <xref:System.Void?displayProperty=nameWithType>
