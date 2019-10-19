---
title: Of Tümcesi (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: c0cfbb5109d5b49f995028944e735c96440c9ab2
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583504"
---
# <a name="of-clause-visual-basic"></a><span data-ttu-id="e562c-102">Of Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e562c-102">Of Clause (Visual Basic)</span></span>
<span data-ttu-id="e562c-103">Bir *genel* sınıf, yapı, arabirim, temsilci veya yordamda bir *tür parametresi* tanımlayan bir `Of` yan tümcesi tanıtır.</span><span class="sxs-lookup"><span data-stu-id="e562c-103">Introduces an `Of` clause, which identifies a *type parameter* on a *generic* class, structure, interface, delegate, or procedure.</span></span> <span data-ttu-id="e562c-104">Genel türler hakkında bilgi için bkz. [Visual Basic genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span><span class="sxs-lookup"><span data-stu-id="e562c-104">For information on generic types, see [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span></span>  
  
## <a name="using-the-of-keyword"></a><span data-ttu-id="e562c-105">Anahtar sözcüğünü kullanma</span><span class="sxs-lookup"><span data-stu-id="e562c-105">Using the Of Keyword</span></span>  
 <span data-ttu-id="e562c-106">Aşağıdaki kod örneği, iki tür parametresi alan bir sınıfın ana hattını tanımlamak için `Of` anahtar sözcüğünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="e562c-106">The following code example uses the `Of` keyword to define the outline of a class that takes two type parameters.</span></span> <span data-ttu-id="e562c-107">@No__t_1 parametresini <xref:System.IComparable> arabirimi ile *kısıtlar* ; bu, tüketen kodun <xref:System.IComparable> uygulayan bir tür bağımsız değişkeni sağlaması gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e562c-107">It *constrains* the `keyType` parameter by the <xref:System.IComparable> interface, which means the consuming code must supply a type argument that implements <xref:System.IComparable>.</span></span> <span data-ttu-id="e562c-108">Bu, `add` yordamının <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> yöntemini çağırabilmesi için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e562c-108">This is necessary so that the `add` procedure can call the <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="e562c-109">Kısıtlamalar hakkında daha fazla bilgi için bkz. [tür listesi](../../../visual-basic/language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="e562c-109">For more information on constraints, see [Type List](../../../visual-basic/language-reference/statements/type-list.md).</span></span>  
  
```vb  
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
  
 <span data-ttu-id="e562c-110">Önceki sınıf tanımını tamamlarınızda, bundan çok çeşitli `dictionary` sınıfları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e562c-110">If you complete the preceding class definition, you can construct a variety of `dictionary` classes from it.</span></span> <span data-ttu-id="e562c-111">@No__t_0 ve `keyType` için sağladığınız türler, sınıfın ne tür bir girişi olduğunu ve her bir girdiyle ne tür bir anahtarın ilişkilendirildiğini belirlemektir.</span><span class="sxs-lookup"><span data-stu-id="e562c-111">The types you supply to `entryType` and `keyType` determine what type of entry the class holds and what type of key it associates with each entry.</span></span> <span data-ttu-id="e562c-112">Kısıtlama nedeniyle, <xref:System.IComparable> uygulayan bir tür `keyType` sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e562c-112">Because of the constraint, you must supply to `keyType` a type that implements <xref:System.IComparable>.</span></span>  
  
 <span data-ttu-id="e562c-113">Aşağıdaki kod örneği, `String` girdileri tutan ve `Integer` anahtarı her biriyle ilişkilendiren bir nesne oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e562c-113">The following code example creates an object that holds `String` entries and associates an `Integer` key with each one.</span></span> <span data-ttu-id="e562c-114">`Integer` <xref:System.IComparable> uygular ve bu nedenle `keyType` kısıtlamasını karşılar.</span><span class="sxs-lookup"><span data-stu-id="e562c-114">`Integer` implements <xref:System.IComparable> and therefore satisfies the constraint on `keyType`.</span></span>  
  
```vb  
Dim d As New dictionary(Of String, Integer)  
```  
  
 <span data-ttu-id="e562c-115">@No__t_0 anahtar sözcüğü şu bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="e562c-115">The `Of` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="e562c-116">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="e562c-116">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="e562c-117">Delegate Deyimi</span><span class="sxs-lookup"><span data-stu-id="e562c-117">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="e562c-118">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="e562c-118">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="e562c-119">Interface Deyimi</span><span class="sxs-lookup"><span data-stu-id="e562c-119">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="e562c-120">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="e562c-120">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="e562c-121">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="e562c-121">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="e562c-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e562c-122">See also</span></span>

- <xref:System.IComparable>
- [<span data-ttu-id="e562c-123">Tür Listesi</span><span class="sxs-lookup"><span data-stu-id="e562c-123">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
- [<span data-ttu-id="e562c-124">Visual Basic genel türler</span><span class="sxs-lookup"><span data-stu-id="e562c-124">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="e562c-125">'Ndaki</span><span class="sxs-lookup"><span data-stu-id="e562c-125">In</span></span>](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [<span data-ttu-id="e562c-126">Dışı</span><span class="sxs-lookup"><span data-stu-id="e562c-126">Out</span></span>](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
