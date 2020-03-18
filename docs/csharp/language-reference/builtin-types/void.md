---
title: void - C# referans
ms.date: 02/11/2020
f1_keywords:
- void_CSharpKeyword
- void
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
ms.openlocfilehash: c6c1c28e3d7a53a1dcadcf50d8d7f42c8c8aeee4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846222"
---
# <a name="void-c-reference"></a><span data-ttu-id="ca3a1-102">void (C# referansı)</span><span class="sxs-lookup"><span data-stu-id="ca3a1-102">void (C# reference)</span></span>

<span data-ttu-id="ca3a1-103">Yöntemin `void` bir değer döndürmediğini belirtmek için bir [yöntemin](../../programming-guide/classes-and-structs/methods.md) (veya [yerel işlevin)](../../programming-guide/classes-and-structs/local-functions.md)dönüş türü olarak kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="ca3a1-103">You use `void` as the return type of a [method](../../programming-guide/classes-and-structs/methods.md) (or a [local function](../../programming-guide/classes-and-structs/local-functions.md)) to specify that the method doesn't return a value.</span></span>

[!code-csharp[void method](snippets/VoidType.cs#VoidExample)]

<span data-ttu-id="ca3a1-104">Bir işaretçiyi bilinmeyen bir türe bildirmek için başvuru türü olarak da kullanabilirsiniz. `void`</span><span class="sxs-lookup"><span data-stu-id="ca3a1-104">You can also use `void` as a referent type to declare a pointer to an unknown type.</span></span> <span data-ttu-id="ca3a1-105">Daha fazla bilgi için [Işaretçi türlerine](../../programming-guide/unsafe-code-pointers/pointer-types.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="ca3a1-105">For more information, see [Pointer types](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span></span>

<span data-ttu-id="ca3a1-106">Değişken türü `void` olarak kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="ca3a1-106">You cannot use `void` as the type of a variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="ca3a1-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca3a1-107">See also</span></span>

- [<span data-ttu-id="ca3a1-108">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="ca3a1-108">C# reference</span></span>](../index.md)
- <xref:System.Void?displayProperty=nameWithType>
