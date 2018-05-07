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
ms.openlocfilehash: 9ace0ad55d9eb1618dbdafb0d49d1ff4b169a877
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="of-clause-visual-basic"></a>Of Tümcesi (Visual Basic)
Tanıtır bir `Of` tanımlayan yan tümcesi bir *tür parametresi* üzerinde bir *genel* sınıfı, yapısı, arabirim, temsilci veya yordam. Genel türler hakkında daha fazla bilgi için bkz: [Visual Basic'de genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).  
  
## <a name="using-the-of-keyword"></a>Kullanarak anahtar sözcüğü  
 Aşağıdaki kod örneğinde `Of` iki tür parametre alan bir sınıfın anahat tanımlamak için anahtar sözcüğü. Bu *kısıtlar* `keyType` parametresiyle <xref:System.IComparable> kullanıcı kodu uygulayan bir tür bağımsız değişkeni sağlamanız gerekir anlamına gelir arabirimi <xref:System.IComparable>. Bu işlem gereklidir böylece `add` yordam çağırabilir <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> yöntemi. Kısıtlamaları hakkında daha fazla bilgi için bkz: [türü listesinde](../../../visual-basic/language-reference/statements/type-list.md).  
  
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
  
 Önceki sınıf tanımını tamamlarsanız, çeşitli oluşturabileceğiniz `dictionary` bu sınıflardan. Sağladığınız için türleri `entryType` ve `keyType` sınıf ne tür bir giriş içerir ve isteğe bağlı olarak anahtar türüne sahip her girişi ilişkilendirir belirler. İçin sağlamalısınız kısıtlama nedeniyle `keyType` uygulayan bir tür <xref:System.IComparable>.  
  
 Aşağıdaki kod örneğinde tutan bir nesne oluşturur `String` girişleri ve ilişkilendirilmiş bir `Integer` her bir anahtar. `Integer` uygulayan <xref:System.IComparable> ve bu nedenle üzerinde kısıtlamasına `keyType`.  
  
```  
Dim d As New dictionary(Of String, Integer)  
```  
  
 `Of` Anahtar sözcüğü bu bağlamlarında kullanılabilir:  
  
 [Class Deyimi](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Delegate Deyimi](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface Deyimi](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Structure Deyimi](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IComparable>  
 [Tür Listesi](../../../visual-basic/language-reference/statements/type-list.md)  
 [Visual Basic'de genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [İçinde](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)  
 [Çıkışı](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
