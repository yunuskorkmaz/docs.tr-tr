---
title: değer bağlamsal anahtar kelime - C# Başvuru
ms.date: 07/20/2015
f1_keywords:
- value_CSharpKeyword
helpviewer_keywords:
- value keyword [C#]
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
ms.openlocfilehash: 84d0c51ddafb59144f4ba8c6e73412642fa8fa28
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712903"
---
# <a name="value-c-reference"></a><span data-ttu-id="5b284-102">value (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="5b284-102">value (C# Reference)</span></span>

<span data-ttu-id="5b284-103">Bağlamsal anahtar `value` [kelime, özellik](../../programming-guide/classes-and-structs/properties.md) `set` ve [dizinleyici](../../programming-guide/indexers/index.md) bildirimlerinde erişimde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5b284-103">The contextual keyword `value` is used in the `set` accessor in [property](../../programming-guide/classes-and-structs/properties.md) and [indexer](../../programming-guide/indexers/index.md) declarations.</span></span> <span data-ttu-id="5b284-104">Bir yöntemin giriş parametresine benzer.</span><span class="sxs-lookup"><span data-stu-id="5b284-104">It is similar to an input parameter of a method.</span></span> <span data-ttu-id="5b284-105">Sözcük, `value` istemci kodunun özellik veya dizinleyiciye atamaya çalıştığı değere başvurur.</span><span class="sxs-lookup"><span data-stu-id="5b284-105">The word `value` references the value that client code is attempting to assign to the property or indexer.</span></span> <span data-ttu-id="5b284-106">Aşağıdaki örnekte, `MyDerivedClass` destek alanına `Name` `name`yeni `value` bir dize atamak için parametre kullanan bir özellik vardır.</span><span class="sxs-lookup"><span data-stu-id="5b284-106">In the following example, `MyDerivedClass` has a property called `Name` that uses the `value` parameter to assign a new string to the backing field `name`.</span></span> <span data-ttu-id="5b284-107">İstemci kodu açısından, işlem basit bir atama olarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="5b284-107">From the point of view of client code, the operation is written as a simple assignment.</span></span>

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

<span data-ttu-id="5b284-108">Daha fazla bilgi için [Özellikler](../../programming-guide/classes-and-structs/properties.md) ve [Dizinleyiciler](../../programming-guide/indexers/index.md) makalelerini görün.</span><span class="sxs-lookup"><span data-stu-id="5b284-108">For more information, see the [Properties](../../programming-guide/classes-and-structs/properties.md) and [Indexeres](../../programming-guide/indexers/index.md) articles.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="5b284-109">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="5b284-109">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="5b284-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5b284-110">See also</span></span>

- [<span data-ttu-id="5b284-111">C# Referans</span><span class="sxs-lookup"><span data-stu-id="5b284-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="5b284-112">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5b284-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="5b284-113">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="5b284-113">C# Keywords</span></span>](index.md)
