---
title: "Of Tümcesi (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- Of
- vb.Of
- vb.of
helpviewer_keywords:
- Of keyword [Visual Basic]
- arguments [Visual Basic], data types
- constraints, Visual Basic generic types
- generic parameters
- generics [Visual Basic], constraints
- parameters [Visual Basic], type
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- type parameters
- data type arguments
ms.assetid: 0db8f65c-65af-4089-ab7f-6fcfecb60444
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5ef3ac4ac88727b1dcae50fa14abde03f29a16fb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="of-clause-visual-basic"></a><span data-ttu-id="97cdd-102">Of Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="97cdd-102">Of Clause (Visual Basic)</span></span>
<span data-ttu-id="97cdd-103">Tanıtır bir `Of` tanımlayan yan tümcesi bir *tür parametresi* üzerinde bir *genel* sınıfı, yapısı, arabirim, temsilci veya yordam.</span><span class="sxs-lookup"><span data-stu-id="97cdd-103">Introduces an `Of` clause, which identifies a *type parameter* on a *generic* class, structure, interface, delegate, or procedure.</span></span> <span data-ttu-id="97cdd-104">Genel türler hakkında daha fazla bilgi için bkz: [Visual Basic'de genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span><span class="sxs-lookup"><span data-stu-id="97cdd-104">For information on generic types, see [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span></span>  
  
## <a name="using-the-of-keyword"></a><span data-ttu-id="97cdd-105">Kullanarak anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="97cdd-105">Using the Of Keyword</span></span>  
 <span data-ttu-id="97cdd-106">Aşağıdaki kod örneğinde `Of` iki tür parametre alan bir sınıfın anahat tanımlamak için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="97cdd-106">The following code example uses the `Of` keyword to define the outline of a class that takes two type parameters.</span></span> <span data-ttu-id="97cdd-107">Bu *kısıtlar* `keyType` parametresiyle <xref:System.IComparable> kullanıcı kodu uygulayan bir tür bağımsız değişkeni sağlamanız gerekir anlamına gelir arabirimi <xref:System.IComparable>.</span><span class="sxs-lookup"><span data-stu-id="97cdd-107">It *constrains* the `keyType` parameter by the <xref:System.IComparable> interface, which means the consuming code must supply a type argument that implements <xref:System.IComparable>.</span></span> <span data-ttu-id="97cdd-108">Bu işlem gereklidir böylece `add` yordam çağırabilir <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="97cdd-108">This is necessary so that the `add` procedure can call the <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="97cdd-109">Kısıtlamaları hakkında daha fazla bilgi için bkz: [türü listesinde](../../../visual-basic/language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="97cdd-109">For more information on constraints, see [Type List](../../../visual-basic/language-reference/statements/type-list.md).</span></span>  
  
```  
Public Class Dictionary(Of entryType, keyType As IComparable)  
    Public Sub add(ByVal e As entryType, ByVal k As keyType)  
        Dim dk As keyType  
        If k.CompareTo(dk) = 0 Then  
        End If  
    End Sub  
    Public Function find(ByVal k As keyType) As entryType  
    End Function  
End Class  
```  
  
 <span data-ttu-id="97cdd-110">Önceki sınıf tanımını tamamlarsanız, çeşitli oluşturabileceğiniz `dictionary` bu sınıflardan.</span><span class="sxs-lookup"><span data-stu-id="97cdd-110">If you complete the preceding class definition, you can construct a variety of `dictionary` classes from it.</span></span> <span data-ttu-id="97cdd-111">Sağladığınız için türleri `entryType` ve `keyType` sınıf ne tür bir giriş içerir ve isteğe bağlı olarak anahtar türüne sahip her girişi ilişkilendirir belirler.</span><span class="sxs-lookup"><span data-stu-id="97cdd-111">The types you supply to `entryType` and `keyType` determine what type of entry the class holds and what type of key it associates with each entry.</span></span> <span data-ttu-id="97cdd-112">İçin sağlamalısınız kısıtlama nedeniyle `keyType` uygulayan bir tür <xref:System.IComparable>.</span><span class="sxs-lookup"><span data-stu-id="97cdd-112">Because of the constraint, you must supply to `keyType` a type that implements <xref:System.IComparable>.</span></span>  
  
 <span data-ttu-id="97cdd-113">Aşağıdaki kod örneğinde tutan bir nesne oluşturur `String` girişleri ve ilişkilendirilmiş bir `Integer` her bir anahtar.</span><span class="sxs-lookup"><span data-stu-id="97cdd-113">The following code example creates an object that holds `String` entries and associates an `Integer` key with each one.</span></span> <span data-ttu-id="97cdd-114">`Integer`uygulayan <xref:System.IComparable> ve bu nedenle üzerinde kısıtlamasına `keyType`.</span><span class="sxs-lookup"><span data-stu-id="97cdd-114">`Integer` implements <xref:System.IComparable> and therefore satisfies the constraint on `keyType`.</span></span>  
  
```  
Dim d As New dictionary(Of String, Integer)  
```  
  
 <span data-ttu-id="97cdd-115">`Of` Anahtar sözcüğü bu bağlamlarında kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="97cdd-115">The `Of` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="97cdd-116">Class deyimi</span><span class="sxs-lookup"><span data-stu-id="97cdd-116">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="97cdd-117">Delegate deyimi</span><span class="sxs-lookup"><span data-stu-id="97cdd-117">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="97cdd-118">Function deyimi</span><span class="sxs-lookup"><span data-stu-id="97cdd-118">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="97cdd-119">Interface deyimi</span><span class="sxs-lookup"><span data-stu-id="97cdd-119">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="97cdd-120">Structure deyimi</span><span class="sxs-lookup"><span data-stu-id="97cdd-120">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="97cdd-121">Sub deyimi</span><span class="sxs-lookup"><span data-stu-id="97cdd-121">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="97cdd-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="97cdd-122">See Also</span></span>  
 <xref:System.IComparable>  
 [<span data-ttu-id="97cdd-123">Tür listesi</span><span class="sxs-lookup"><span data-stu-id="97cdd-123">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)  
 [<span data-ttu-id="97cdd-124">Visual Basic'de genel türler</span><span class="sxs-lookup"><span data-stu-id="97cdd-124">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="97cdd-125">İçinde</span><span class="sxs-lookup"><span data-stu-id="97cdd-125">In</span></span>](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)  
 [<span data-ttu-id="97cdd-126">Çıkışı</span><span class="sxs-lookup"><span data-stu-id="97cdd-126">Out</span></span>](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
