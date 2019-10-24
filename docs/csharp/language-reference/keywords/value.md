---
title: value bağlamsal anahtar sözcüğü C# -başvuru
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- value_CSharpKeyword
helpviewer_keywords:
- value keyword [C#]
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
ms.openlocfilehash: 34b192d17bd96b6b893c9f14f0d4a77274a32f78
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771749"
---
# <a name="value-c-reference"></a><span data-ttu-id="16fc8-102">value (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="16fc8-102">value (C# Reference)</span></span>

<span data-ttu-id="16fc8-103">Bağlamsal anahtar sözcük `value`, [özellik](../../programming-guide/classes-and-structs/properties.md) ve [dizin oluşturucu](../../programming-guide/indexers/index.md) bildirimlerinde `set` erişimcisinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="16fc8-103">The contextual keyword `value` is used in the `set` accessor in [property](../../programming-guide/classes-and-structs/properties.md) and [indexer](../../programming-guide/indexers/index.md) declarations.</span></span> <span data-ttu-id="16fc8-104">Yöntemin giriş parametresine benzerdir.</span><span class="sxs-lookup"><span data-stu-id="16fc8-104">It is similar to an input parameter of a method.</span></span> <span data-ttu-id="16fc8-105">Sözcük `value`, istemci kodunun özelliğe veya dizin oluşturucusuna atamaya çalışan değere başvurur.</span><span class="sxs-lookup"><span data-stu-id="16fc8-105">The word `value` references the value that client code is attempting to assign to the property or indexer.</span></span> <span data-ttu-id="16fc8-106">Aşağıdaki örnekte `MyDerivedClass`, `name`yedekleme alanına yeni bir dize atamak için `value` parametresini kullanan `Name` adlı bir özelliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="16fc8-106">In the following example, `MyDerivedClass` has a property called `Name` that uses the `value` parameter to assign a new string to the backing field `name`.</span></span> <span data-ttu-id="16fc8-107">İstemci kodunun bakış noktasından, işlem basit atama olarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="16fc8-107">From the point of view of client code, the operation is written as a simple assignment.</span></span>

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

<span data-ttu-id="16fc8-108">Daha fazla bilgi için bkz. [Özellikler](../../programming-guide/classes-and-structs/properties.md) ve [Indexeres](../../programming-guide/indexers/index.md) makaleleri.</span><span class="sxs-lookup"><span data-stu-id="16fc8-108">For more information, see the [Properties](../../programming-guide/classes-and-structs/properties.md) and [Indexeres](../../programming-guide/indexers/index.md) articles.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="16fc8-109">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="16fc8-109">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="16fc8-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="16fc8-110">See also</span></span>

- [<span data-ttu-id="16fc8-111">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="16fc8-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="16fc8-112">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="16fc8-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="16fc8-113">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="16fc8-113">C# Keywords</span></span>](index.md)
