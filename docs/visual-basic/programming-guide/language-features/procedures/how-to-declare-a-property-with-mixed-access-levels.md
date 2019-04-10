---
title: 'Nasıl yapılır: Bir özelliği karışık erişim düzeyleri (Visual Basic) bildirme'
ms.date: 07/20/2015
helpviewer_keywords:
- access levels [Visual Basic], properties
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- mixed access levels
- Visual Basic code, properties
- properties [Visual Basic], access levels
- Property statement [Visual Basic], declaring mixed access levels
ms.assetid: fdbb2d97-279a-4956-b26c-cbdfbc34915a
ms.openlocfilehash: e899b57e02f492b0e4909aca84c069e5b7688618
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59339820"
---
# <a name="how-to-declare-a-property-with-mixed-access-levels-visual-basic"></a>Nasıl yapılır: Bir özelliği karışık erişim düzeyleri (Visual Basic) bildirme
İsterseniz `Get` ve `Set` yordamları farklı erişim düzeylerine sahip bir özellik üzerinde daha fazla izin veremez düzeyinde kullanabilirsiniz `Property` deyimi ve ya da daha kısıtlayıcı düzeyinde `Get` veya `Set` deyimi. Belirli bölümlerini özelliğin değerini almak kod ve belirli bir değeri değiştirmek kod bölümlerini istediğinizde bir özelliği karışık erişim düzeyleriyle kullanın.  
  
 Erişim düzeyleri hakkında daha fazla bilgi için bkz. [erişim düzeyini Visual Basic'te](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
### <a name="to-declare-a-property-with-mixed-access-levels"></a>Bir özelliği karışık erişim düzeyleriyle bildirme  
  
1. Normal bir şekilde özelliği bildirme ve daha az kısıtlayıcı erişim düzeyini belirtin (gibi `Public`) içinde `Property` deyimi.  
  
2. Ya da bildirmek `Get` veya `Set` daha kısıtlayıcı erişim düzeyini belirterek yordamı (gibi `Friend`).  
  
3. Bir özellik yordamı üzerinde bir erişim düzeyi belirtmeyin. Bildirilen erişim düzeyi varsayar `Property` deyimi. Özellik yordamları yalnızca birinde erişimi kısıtlayabilirsiniz.  
  
     [!code-vb[VbVbcnProcedures#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#10)]  
  
     Önceki örnekte, `Get` yordamı sahip aynı `Protected` özellik kendisine erişim sırasında `Set` yordamı sahip `Private` erişim. Öğesinden türetilen bir sınıf `employee` okuyabilirsiniz `salary` değeri, ancak yalnızca `employee` sınıf ayarlayabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [Özellik Yordamları](./property-procedures.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Property Deyimi](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Visual Basic'de Özellikler ve Değişkenler Arasındaki Farklar](./differences-between-properties-and-variables.md)
- [Nasıl yapılır: Özellik Oluşturma](./how-to-create-a-property.md)
- [Nasıl yapılır: Bir Özellik Yordamı Çağırma](./how-to-call-a-property-procedure.md)
- [Nasıl yapılır: Bildirme ve Visual Basic'te bir varsayılan özelliğini çağırın](./how-to-declare-and-call-a-default-property.md)
- [Nasıl yapılır: Bir Özelliğe Değer Ekleme](./how-to-put-a-value-in-a-property.md)
- [Nasıl yapılır: Bir Özellikten Değer Alma](./how-to-get-a-value-from-a-property.md)
