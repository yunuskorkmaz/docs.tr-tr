---
title: value bağlamsal anahtar sözcüğü C# -başvuru
ms.date: 07/20/2015
f1_keywords:
- value_CSharpKeyword
helpviewer_keywords:
- value keyword [C#]
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
ms.openlocfilehash: 84d0c51ddafb59144f4ba8c6e73412642fa8fa28
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712903"
---
# <a name="value-c-reference"></a><span data-ttu-id="fd4c9-102">value (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="fd4c9-102">value (C# Reference)</span></span>

<span data-ttu-id="fd4c9-103">Bağlamsal anahtar sözcük `value`, [özellik](../../programming-guide/classes-and-structs/properties.md) ve [dizin oluşturucu](../../programming-guide/indexers/index.md) bildirimlerinde `set` erişimcisinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fd4c9-103">The contextual keyword `value` is used in the `set` accessor in [property](../../programming-guide/classes-and-structs/properties.md) and [indexer](../../programming-guide/indexers/index.md) declarations.</span></span> <span data-ttu-id="fd4c9-104">Yöntemin giriş parametresine benzerdir.</span><span class="sxs-lookup"><span data-stu-id="fd4c9-104">It is similar to an input parameter of a method.</span></span> <span data-ttu-id="fd4c9-105">Sözcük `value`, istemci kodunun özelliğe veya dizin oluşturucusuna atamaya çalışan değere başvurur.</span><span class="sxs-lookup"><span data-stu-id="fd4c9-105">The word `value` references the value that client code is attempting to assign to the property or indexer.</span></span> <span data-ttu-id="fd4c9-106">Aşağıdaki örnekte `MyDerivedClass`, `name`yedekleme alanına yeni bir dize atamak için `value` parametresini kullanan `Name` adlı bir özelliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="fd4c9-106">In the following example, `MyDerivedClass` has a property called `Name` that uses the `value` parameter to assign a new string to the backing field `name`.</span></span> <span data-ttu-id="fd4c9-107">İstemci kodunun bakış noktasından, işlem basit atama olarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="fd4c9-107">From the point of view of client code, the operation is written as a simple assignment.</span></span>

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

<span data-ttu-id="fd4c9-108">Daha fazla bilgi için bkz. [Özellikler](../../programming-guide/classes-and-structs/properties.md) ve [Indexeres](../../programming-guide/indexers/index.md) makaleleri.</span><span class="sxs-lookup"><span data-stu-id="fd4c9-108">For more information, see the [Properties](../../programming-guide/classes-and-structs/properties.md) and [Indexeres](../../programming-guide/indexers/index.md) articles.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="fd4c9-109">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="fd4c9-109">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="fd4c9-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd4c9-110">See also</span></span>

- [<span data-ttu-id="fd4c9-111">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="fd4c9-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="fd4c9-112">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="fd4c9-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="fd4c9-113">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="fd4c9-113">C# Keywords</span></span>](index.md)
