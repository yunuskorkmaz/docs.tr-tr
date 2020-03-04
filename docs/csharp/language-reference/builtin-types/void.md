---
title: void C# başvurusu
ms.date: 02/11/2020
f1_keywords:
- void_CSharpKeyword
- void
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
ms.openlocfilehash: c37492f3c8f61c042e94848b838d7f5b445bdd1f
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239722"
---
# <a name="void-c-reference"></a><span data-ttu-id="03497-102">void (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="03497-102">void (C# reference)</span></span>

<span data-ttu-id="03497-103">Yöntemin bir değer döndürmediğini belirtmek için bir [yöntemin](../../programming-guide/classes-and-structs/methods.md) dönüş türü (veya [yerel bir işlev](../../programming-guide/classes-and-structs/local-functions.md)) olarak `void` kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="03497-103">You use `void` as the return type of a [method](../../programming-guide/classes-and-structs/methods.md) (or a [local function](../../programming-guide/classes-and-structs/local-functions.md)) to specify that the method doesn't return a value.</span></span>

[!code-csharp[void method](~/samples/snippets/csharp/language-reference/builtin-types/VoidType.cs#VoidExample)]

<span data-ttu-id="03497-104">`void`, bilinmeyen bir türe yönelik bir işaretçi bildirmek için, başvurulan tür olarak da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="03497-104">You can also use `void` as a referent type to declare a pointer to an unknown type.</span></span> <span data-ttu-id="03497-105">Daha fazla bilgi için bkz. [işaretçi türleri](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span><span class="sxs-lookup"><span data-stu-id="03497-105">For more information, see [Pointer types](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span></span>

<span data-ttu-id="03497-106">Bir değişkenin türü olarak `void` kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="03497-106">You cannot use `void` as the type of a variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="03497-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="03497-107">See also</span></span>

- [<span data-ttu-id="03497-108">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="03497-108">C# reference</span></span>](../index.md)
- <xref:System.Void?displayProperty=nameWithType>
