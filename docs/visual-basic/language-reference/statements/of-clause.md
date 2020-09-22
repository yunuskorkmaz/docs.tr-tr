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
ms.openlocfilehash: 0595356fb75fc0ac73a49622d71fe1d28fa7b648
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90865911"
---
# <a name="of-clause-visual-basic"></a>Of Tümcesi (Visual Basic)

Bir `Of` *genel* sınıf, yapı, arabirim, temsilci veya yordamda bir *tür parametresi* tanımlayan bir yan tümce tanıtır. Genel türler hakkında bilgi için bkz. [Visual Basic genel türler](../../programming-guide/language-features/data-types/generic-types.md).  
  
## <a name="using-the-of-keyword"></a>Anahtar sözcüğünü kullanma  

 Aşağıdaki kod örneği, `Of` iki tür parametresi alan bir sınıfın ana hattını tanımlamak için anahtar sözcüğünü kullanır. Parametreyi *constrains* arabirimini kısıtlar `keyType` , bu da <xref:System.IComparable> tüketen kodun uygulayan bir tür bağımsız değişkeni sağlaması gerektiği anlamına gelir <xref:System.IComparable> . `add`Yordamın yöntemi çağırabilmesi için bu gereklidir <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> . Kısıtlamalar hakkında daha fazla bilgi için bkz. [tür listesi](type-list.md).  
  
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
  
 Önceki sınıf tanımını tamamlarınızda, bundan çok çeşitli `dictionary` sınıflar oluşturabilirsiniz. İçin sağladığınız türler, `entryType` `keyType` sınıfın ne tür bir girişi olduğunu ve her bir girdiyle ne tür bir anahtar ilişkilendiğini belirlersiniz. Kısıtlama nedeniyle, `keyType` uygulayan bir türe sağlamanız gerekir <xref:System.IComparable> .  
  
 Aşağıdaki kod örneği, `String` girdileri tutan ve bir anahtarı her biriyle ilişkilendiren bir nesne oluşturur `Integer` . `Integer` ' <xref:System.IComparable> i uygular ve bu nedenle üzerindeki kısıtlamayı karşılar `keyType` .  
  
```vb  
Dim d As New dictionary(Of String, Integer)  
```  
  
 `Of`Anahtar sözcüğü şu bağlamlarda kullanılabilir:  
  
 [Class Deyimi](class-statement.md)  
  
 [Delegate Deyimi](delegate-statement.md)  
  
 [Function Deyimi](function-statement.md)  
  
 [Interface Deyimi](interface-statement.md)  
  
 [Structure Yapısı](structure-statement.md)  
  
 [Sub Deyimi](sub-statement.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IComparable>
- [Tür Listesi](type-list.md)
- [Visual Basic genel türler](../../programming-guide/language-features/data-types/generic-types.md)
- [İçinde](../modifiers/in-generic-modifier.md)
- [Dışı](../modifiers/out-generic-modifier.md)
