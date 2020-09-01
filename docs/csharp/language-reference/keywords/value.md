---
description: value bağlamsal anahtar sözcüğü-C# başvurusu
title: value bağlamsal anahtar sözcüğü-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- value_CSharpKeyword
helpviewer_keywords:
- value keyword [C#]
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
ms.openlocfilehash: f72e9f097880d9de725a85a0973001baaefd9a9c
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141744"
---
# <a name="value-c-reference"></a><span data-ttu-id="653a2-103">value (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="653a2-103">value (C# Reference)</span></span>

<span data-ttu-id="653a2-104">Bağlamsal anahtar sözcüğü, `value` `set` [özellik](../../programming-guide/classes-and-structs/properties.md) ve [Dizin Oluşturucu](../../programming-guide/indexers/index.md) bildirimlerinde erişimcisinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="653a2-104">The contextual keyword `value` is used in the `set` accessor in [property](../../programming-guide/classes-and-structs/properties.md) and [indexer](../../programming-guide/indexers/index.md) declarations.</span></span> <span data-ttu-id="653a2-105">Yöntemin giriş parametresine benzerdir.</span><span class="sxs-lookup"><span data-stu-id="653a2-105">It is similar to an input parameter of a method.</span></span> <span data-ttu-id="653a2-106">Sözcük, `value` istemci kodunun özelliğe veya dizin oluşturucusuna atamaya çalışan değere başvurur.</span><span class="sxs-lookup"><span data-stu-id="653a2-106">The word `value` references the value that client code is attempting to assign to the property or indexer.</span></span> <span data-ttu-id="653a2-107">Aşağıdaki örnekte, `MyDerivedClass` `Name` `value` yedekleme alanına yeni bir dize atamak için parametresini kullanan adlı bir özelliğe sahiptir `name` .</span><span class="sxs-lookup"><span data-stu-id="653a2-107">In the following example, `MyDerivedClass` has a property called `Name` that uses the `value` parameter to assign a new string to the backing field `name`.</span></span> <span data-ttu-id="653a2-108">İstemci kodunun bakış noktasından, işlem basit atama olarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="653a2-108">From the point of view of client code, the operation is written as a simple assignment.</span></span>

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

<span data-ttu-id="653a2-109">Daha fazla bilgi için bkz. [Özellikler](../../programming-guide/classes-and-structs/properties.md) ve [Indexeres](../../programming-guide/indexers/index.md) makaleleri.</span><span class="sxs-lookup"><span data-stu-id="653a2-109">For more information, see the [Properties](../../programming-guide/classes-and-structs/properties.md) and [Indexeres](../../programming-guide/indexers/index.md) articles.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="653a2-110">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="653a2-110">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="653a2-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="653a2-111">See also</span></span>

- [<span data-ttu-id="653a2-112">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="653a2-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="653a2-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="653a2-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="653a2-114">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="653a2-114">C# Keywords</span></span>](index.md)
