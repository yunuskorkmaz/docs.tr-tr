---
title: değer - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- value_CSharpKeyword
helpviewer_keywords:
- value keyword [C#]
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
ms.openlocfilehash: f0b9e2927eb288a27f926a740a967742b8cdaa9e
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236472"
---
# <a name="value-c-reference"></a><span data-ttu-id="c4187-102">value (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="c4187-102">value (C# Reference)</span></span>
<span data-ttu-id="c4187-103">Bağlamsal anahtar sözcüğü `value` sıradan özellik bildiriminde kümesi erişimcisi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c4187-103">The contextual keyword `value` is used in the set accessor in ordinary property declarations.</span></span> <span data-ttu-id="c4187-104">Yöntemi giriş parametresi benzerdir.</span><span class="sxs-lookup"><span data-stu-id="c4187-104">It is similar to an input parameter on a method.</span></span> <span data-ttu-id="c4187-105">Word `value` istemci kodu özelliğe atanacak çalışıyor değeri başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="c4187-105">The word `value` references the value that client code is attempting to assign to the property.</span></span> <span data-ttu-id="c4187-106">Aşağıdaki örnekte, `MyDerivedClass` adlı bir özelliğe sahiptir `Name` kullanan `value` yedekleme alanına yeni bir dize atamak için parametre `name`.</span><span class="sxs-lookup"><span data-stu-id="c4187-106">In the following example, `MyDerivedClass` has a property called `Name` that uses the `value` parameter to assign a new string to the backing field `name`.</span></span> <span data-ttu-id="c4187-107">Bakış açısıyla, istemci kodu, işlem bir basit atama yazılır.</span><span class="sxs-lookup"><span data-stu-id="c4187-107">From the point of view of client code, the operation is written as a simple assignment.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/value_1.cs)]  
  
 <span data-ttu-id="c4187-108">Kullanımıyla ilgili daha fazla bilgi için `value`, bkz: [özellikleri](../../../csharp/programming-guide/classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="c4187-108">For more information about the use of `value`, see [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="c4187-109">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="c4187-109">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c4187-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c4187-110">See Also</span></span>

- [<span data-ttu-id="c4187-111">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="c4187-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="c4187-112">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c4187-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="c4187-113">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="c4187-113">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
