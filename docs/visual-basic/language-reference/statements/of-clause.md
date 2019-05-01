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
ms.openlocfilehash: 880570c714292b0c11eef4e2cd4c4b410bb075f1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61784156"
---
# <a name="of-clause-visual-basic"></a>Of Tümcesi (Visual Basic)
Tanıtır bir `Of` tanımlayan yan tümcesi bir *tür parametresi* üzerinde bir *genel* sınıfı, yapı, arabirim, temsilci veya yordam. Genel türler hakkında daha fazla bilgi için bkz: [Visual Basic'de genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).  
  
## <a name="using-the-of-keyword"></a>Kullanarak anahtar sözcüğü  
 Aşağıdaki kod örneğinde `Of` iki tür parametreleri alan sınıfının ana hattı tanımlamak için anahtar sözcüğü. Bunu *kısıtlar* `keyType` parametresiyle <xref:System.IComparable> kullanan kodu uygulayan bir tür bağımsız değişkeni sağlaması gerekir yani arabirimi <xref:System.IComparable>. Bunun gerekli olmasının böylece `add` yordam çağırabilir <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> yöntemi. Kısıtlamaları hakkında daha fazla bilgi için bkz. [tür listesi](../../../visual-basic/language-reference/statements/type-list.md).  
  
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
  
 Önceki bir sınıf tanımı tamamlarsanız, çeşitli oluşturabilirsiniz `dictionary` bu sınıflardan. Sağladığınız için türleri `entryType` ve `keyType` sınıf giriş türünü içerir ve her bir girdi ilişkilendirir anahtar türünü belirler. Kısıtlama nedeniyle, için sağlamalısınız `keyType` uygulayan bir tür <xref:System.IComparable>.  
  
 Aşağıdaki kod örneği içeren bir nesne oluşturur `String` girişleri ve associates bir `Integer` her bir anahtar. `Integer` uygulayan <xref:System.IComparable> ve bu nedenle üzerinde kısıtlamasına `keyType`.  
  
```  
Dim d As New dictionary(Of String, Integer)  
```  
  
 `Of` Anahtar sözcüğü bu bağlamda kullanılabilir:  
  
 [Class Deyimi](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Delegate Deyimi](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface Deyimi](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Structure Deyimi](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IComparable>
- [Tür Listesi](../../../visual-basic/language-reference/statements/type-list.md)
- [Visual Basic'de genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [İçinde](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [Çıkış](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
