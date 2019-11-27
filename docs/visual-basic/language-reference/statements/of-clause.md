---
title: Of Yan Tümcesi
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
ms.openlocfilehash: d88c43efe858d6b81b7d8d2470b234ff5d40632a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353834"
---
# <a name="of-clause-visual-basic"></a>Of Tümcesi (Visual Basic)
Bir *genel* sınıf, yapı, arabirim, temsilci veya yordamda bir *tür parametresi* tanımlayan bir `Of` yan tümcesi tanıtır. Genel türler hakkında bilgi için bkz. [Visual Basic genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).  
  
## <a name="using-the-of-keyword"></a>Anahtar sözcüğünü kullanma  
 Aşağıdaki kod örneği, iki tür parametresi alan bir sınıfın ana hattını tanımlamak için `Of` anahtar sözcüğünü kullanır. `keyType` parametresini <xref:System.IComparable> arabirimi ile *kısıtlar* ; bu, tüketen kodun <xref:System.IComparable>uygulayan bir tür bağımsız değişkeni sağlaması gerektiği anlamına gelir. Bu, `add` yordamının <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> yöntemini çağırabilmesi için gereklidir. Kısıtlamalar hakkında daha fazla bilgi için bkz. [tür listesi](../../../visual-basic/language-reference/statements/type-list.md).  
  
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
  
 Önceki sınıf tanımını tamamlarınızda, bundan çok çeşitli `dictionary` sınıfları oluşturabilirsiniz. `entryType` ve `keyType` için sağladığınız türler, sınıfın ne tür bir girişi olduğunu ve her bir girdiyle ne tür bir anahtarın ilişkilendirildiğini belirlemektir. Kısıtlama nedeniyle, <xref:System.IComparable>uygulayan bir tür `keyType` sağlamanız gerekir.  
  
 Aşağıdaki kod örneği, `String` girdileri tutan ve `Integer` anahtarı her biriyle ilişkilendiren bir nesne oluşturur. `Integer` <xref:System.IComparable> uygular ve bu nedenle `keyType`kısıtlamasını karşılar.  
  
```vb  
Dim d As New dictionary(Of String, Integer)  
```  
  
 `Of` anahtar sözcüğü şu bağlamlarda kullanılabilir:  
  
 [Class Deyimi](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Delegate Deyimi](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface Deyimi](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Structure Deyimi](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IComparable>
- [Tür Listesi](../../../visual-basic/language-reference/statements/type-list.md)
- [Visual Basic genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- ['Ndaki](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [Dışı](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
