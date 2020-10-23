---
description: "C 'de void anahtar sözcüğü hakkında daha fazla bilgi edinin #"
title: void-C# başvurusu
ms.date: 02/11/2020
f1_keywords:
- void_CSharpKeyword
- void
- (void)
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
ms.openlocfilehash: fb22fffadeff4db9fcd8e1c8753d44455186aa5a
ms.sourcegitcommit: 870bc4b4087510f6fba3c7b1c0d391f02bcc1f3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2020
ms.locfileid: "92471643"
---
# <a name="void-c-reference"></a><span data-ttu-id="00369-103">void (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="00369-103">void (C# reference)</span></span>

<span data-ttu-id="00369-104">`void`Yöntemin bir değer döndürmediğini belirtmek için bir [yöntemin](../../programming-guide/classes-and-structs/methods.md) dönüş türü (veya [yerel bir işlev](../../programming-guide/classes-and-structs/local-functions.md)) olarak kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="00369-104">You use `void` as the return type of a [method](../../programming-guide/classes-and-structs/methods.md) (or a [local function](../../programming-guide/classes-and-structs/local-functions.md)) to specify that the method doesn't return a value.</span></span>

[!code-csharp[void method](snippets/shared/VoidType.cs#VoidExample)]

<span data-ttu-id="00369-105">Ayrıca, bilinmeyen bir `void` tür için bir işaretçi bildirmek üzere bir başvurulan türü olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00369-105">You can also use `void` as a referent type to declare a pointer to an unknown type.</span></span> <span data-ttu-id="00369-106">Daha fazla bilgi için bkz. [işaretçi türleri](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span><span class="sxs-lookup"><span data-stu-id="00369-106">For more information, see [Pointer types](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span></span>

<span data-ttu-id="00369-107">`void`Bir değişkenin türü olarak kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="00369-107">You cannot use `void` as the type of a variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="00369-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00369-108">See also</span></span>

- [<span data-ttu-id="00369-109">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="00369-109">C# reference</span></span>](../index.md)
- <xref:System.Void?displayProperty=nameWithType>
