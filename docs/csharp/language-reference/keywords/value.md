---
title: "value (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: value_CSharpKeyword
helpviewer_keywords: value keyword [C#]
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2501bc8964ed76534dba6c7cc519e095c57cb898
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="value-c-reference"></a><span data-ttu-id="1d145-102">value (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="1d145-102">value (C# Reference)</span></span>
<span data-ttu-id="1d145-103">Bağlamsal anahtar sözcüğü `value` sıradan özelliği bildirimlerden set erişimcisi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1d145-103">The contextual keyword `value` is used in the set accessor in ordinary property declarations.</span></span> <span data-ttu-id="1d145-104">Giriş parametresi bir metot benzerdir.</span><span class="sxs-lookup"><span data-stu-id="1d145-104">It is similar to an input parameter on a method.</span></span> <span data-ttu-id="1d145-105">Word `value` özelliğine atamak için istemci kodu deniyor değeri başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="1d145-105">The word `value` references the value that client code is attempting to assign to the property.</span></span> <span data-ttu-id="1d145-106">Aşağıdaki örnekte, `MyDerivedClass` adlı bir özelliği vardır `Name` kullanan `value` yedekleme alanına yeni bir dize atamak için parametre `name`.</span><span class="sxs-lookup"><span data-stu-id="1d145-106">In the following example, `MyDerivedClass` has a property called `Name` that uses the `value` parameter to assign a new string to the backing field `name`.</span></span> <span data-ttu-id="1d145-107">Açısından bakıldığında, istemci kodu, işlemi basit atama yazılır.</span><span class="sxs-lookup"><span data-stu-id="1d145-107">From the point of view of client code, the operation is written as a simple assignment.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/value_1.cs)]  
  
 <span data-ttu-id="1d145-108">Kullanımı hakkında daha fazla bilgi için `value`, bkz: [özellikleri](../../../csharp/programming-guide/classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="1d145-108">For more information about the use of `value`, see [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="1d145-109">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="1d145-109">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1d145-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1d145-110">See Also</span></span>  
 [<span data-ttu-id="1d145-111">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="1d145-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="1d145-112">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="1d145-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1d145-113">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="1d145-113">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
