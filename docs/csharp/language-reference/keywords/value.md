---
title: değer bağlamsal anahtar sözcüğü - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- value_CSharpKeyword
helpviewer_keywords:
- value keyword [C#]
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
ms.openlocfilehash: cfd370df771998057fd421a0917b3e2fcd96d9f8
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633031"
---
# <a name="value-c-reference"></a><span data-ttu-id="c44a2-102">value (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="c44a2-102">value (C# Reference)</span></span>

<span data-ttu-id="c44a2-103">Bağlamsal anahtar sözcüğü `value` sıradan özellik bildiriminde kümesi erişimcisi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c44a2-103">The contextual keyword `value` is used in the set accessor in ordinary property declarations.</span></span> <span data-ttu-id="c44a2-104">Yöntemi giriş parametresi benzerdir.</span><span class="sxs-lookup"><span data-stu-id="c44a2-104">It is similar to an input parameter on a method.</span></span> <span data-ttu-id="c44a2-105">Word `value` istemci kodu özelliğe atanacak çalışıyor değeri başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="c44a2-105">The word `value` references the value that client code is attempting to assign to the property.</span></span> <span data-ttu-id="c44a2-106">Aşağıdaki örnekte, `MyDerivedClass` adlı bir özelliğe sahiptir `Name` kullanan `value` yedekleme alanına yeni bir dize atamak için parametre `name`.</span><span class="sxs-lookup"><span data-stu-id="c44a2-106">In the following example, `MyDerivedClass` has a property called `Name` that uses the `value` parameter to assign a new string to the backing field `name`.</span></span> <span data-ttu-id="c44a2-107">Bakış açısıyla, istemci kodu, işlem bir basit atama yazılır.</span><span class="sxs-lookup"><span data-stu-id="c44a2-107">From the point of view of client code, the operation is written as a simple assignment.</span></span>

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

<span data-ttu-id="c44a2-108">Kullanımıyla ilgili daha fazla bilgi için `value`, bkz: [özellikleri](../../programming-guide/classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="c44a2-108">For more information about the use of `value`, see [Properties](../../programming-guide/classes-and-structs/properties.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="c44a2-109">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="c44a2-109">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="c44a2-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c44a2-110">See also</span></span>

- [<span data-ttu-id="c44a2-111">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="c44a2-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c44a2-112">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c44a2-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c44a2-113">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="c44a2-113">C# Keywords</span></span>](index.md)
