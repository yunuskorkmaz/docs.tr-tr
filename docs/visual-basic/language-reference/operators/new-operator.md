---
title: New İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.new
- vb.NewConstraint
helpviewer_keywords:
- constraints, Visual Basic generic types
- generics [Visual Basic], constraints
- constraints, New keyword [Visual Basic]
- New constraint
- New keyword [Visual Basic]
ms.assetid: d7d566d7-fe0e-4336-91f7-641a542de4d0
ms.openlocfilehash: 36cf71529b1f81c27881638d788117222c37171d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955873"
---
# <a name="new-operator-visual-basic"></a>New İşleci (Visual Basic)
Yeni bir `New` nesne örneği oluşturmak için bir yan tümce tanıtır, bir tür parametresinde Oluşturucu kısıtlamasını belirtir veya bir `Sub` yordamı sınıf oluşturucusu olarak tanımlar.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir bildirimde veya atama ifadesinde, `New` yan tümce, örneği oluşturulabilecek tanımlanmış bir sınıf belirtmelidir. Bu, sınıfın, çağıran kodun erişebileceği bir veya daha fazla Oluşturucu kullanıma sunması gerektiği anlamına gelir.  
  
 Bir bildirim ifadesinde veya `New` atama ifadesinde bir yan tümce kullanabilirsiniz. İfade çalıştırıldığında, belirtilen sınıfın uygun oluşturucusunu çağırarak, sağladığınız tüm bağımsız değişkenleri geçer. Aşağıdaki örnek, bir parametre ve bir dize parametresi alan `Customer` bir tane olmak üzere iki Oluşturucusu olan bir sınıfın örneklerini oluşturarak bunu gösterir.  
  
 [!code-vb[VbVbalrKeywords#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#11)]  
  
 Diziler sınıflar olduğundan, `New` aşağıdaki örneklerde gösterildiği gibi yeni bir dizi örneği oluşturabilir.  
  
 [!code-vb[VbVbalrKeywords#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#12)]  
  
 Ortak dil çalışma zamanı (CLR), yeni <xref:System.OutOfMemoryException> örneği oluşturmak için yeterli bellek yoksa bir hata oluşturur.  
  
> [!NOTE]
> `New` Anahtar sözcüğü, sağlanan türün erişilebilir parametresiz bir oluşturucuyu kullanıma sunması gerektiğini belirtmek için tür parametresi listelerinde de kullanılır. Tür parametreleri ve kısıtlamaları hakkında daha fazla bilgi için bkz. [tür listesi](../../../visual-basic/language-reference/statements/type-list.md).  
  
 Bir sınıf için bir Oluşturucu yordamı oluşturmak için, bir `Sub` yordamın `New` adını anahtar sözcüğe ayarlayın. Daha fazla bilgi için bkz [. nesne ömrü: Nesneler nasıl oluşturulur ve yok edilir](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).  
  
 `New` Anahtar sözcüğü şu bağlamlarda kullanılabilir:  
  
 [Dim Deyimi](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Durumunu](../../../visual-basic/language-reference/statements/of-clause.md)  
  
 [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.OutOfMemoryException>
- [Anahtar Sözcükler](../../../visual-basic/language-reference/keywords/index.md)
- [Tür Listesi](../../../visual-basic/language-reference/statements/type-list.md)
- [Visual Basic genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Nesne ömrü: Nesneleri oluşturma ve yok etme](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
