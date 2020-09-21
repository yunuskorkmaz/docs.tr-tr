---
description: value bağlamsal anahtar sözcüğü-C# başvurusu
title: value bağlamsal anahtar sözcüğü-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- value_CSharpKeyword
helpviewer_keywords:
- value keyword [C#]
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
ms.openlocfilehash: ad2eb6f12d8c295dc5203994d6c570cd2377e3ee
ms.sourcegitcommit: 43ed174f085840ca18a791dc89fe833174da766d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/21/2020
ms.locfileid: "90828922"
---
# <a name="value-c-reference"></a><span data-ttu-id="8dd34-103">value (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="8dd34-103">value (C# Reference)</span></span>

<span data-ttu-id="8dd34-104">Bağlamsal anahtar sözcüğü, `value` `set` [özellik](../../programming-guide/classes-and-structs/properties.md) ve [Dizin Oluşturucu](../../programming-guide/indexers/index.md) bildirimlerinde erişimcisinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8dd34-104">The contextual keyword `value` is used in the `set` accessor in [property](../../programming-guide/classes-and-structs/properties.md) and [indexer](../../programming-guide/indexers/index.md) declarations.</span></span> <span data-ttu-id="8dd34-105">Yöntemin giriş parametresine benzerdir.</span><span class="sxs-lookup"><span data-stu-id="8dd34-105">It is similar to an input parameter of a method.</span></span> <span data-ttu-id="8dd34-106">Sözcük, `value` istemci kodunun özelliğe veya dizin oluşturucusuna atamaya çalışan değere başvurur.</span><span class="sxs-lookup"><span data-stu-id="8dd34-106">The word `value` references the value that client code is attempting to assign to the property or indexer.</span></span> <span data-ttu-id="8dd34-107">Aşağıdaki örnekte, `MyDerivedClass` `Name` `value` yedekleme alanına yeni bir dize atamak için parametresini kullanan adlı bir özelliğe sahiptir `name` .</span><span class="sxs-lookup"><span data-stu-id="8dd34-107">In the following example, `MyDerivedClass` has a property called `Name` that uses the `value` parameter to assign a new string to the backing field `name`.</span></span> <span data-ttu-id="8dd34-108">İstemci kodunun bakış noktasından, işlem basit atama olarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="8dd34-108">From the point of view of client code, the operation is written as a simple assignment.</span></span>

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

<span data-ttu-id="8dd34-109">Daha fazla bilgi için [Özellikler](../../programming-guide/classes-and-structs/properties.md) ve [Dizin oluşturucular](../../programming-guide/indexers/index.md) makalelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="8dd34-109">For more information, see the [Properties](../../programming-guide/classes-and-structs/properties.md) and [Indexers](../../programming-guide/indexers/index.md) articles.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="8dd34-110">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="8dd34-110">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="8dd34-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8dd34-111">See also</span></span>

- [<span data-ttu-id="8dd34-112">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="8dd34-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="8dd34-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="8dd34-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="8dd34-114">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="8dd34-114">C# Keywords</span></span>](index.md)
