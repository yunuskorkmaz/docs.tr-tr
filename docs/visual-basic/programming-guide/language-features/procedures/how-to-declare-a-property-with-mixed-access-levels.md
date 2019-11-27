---
title: 'Nasıl yapılır: Bir Özelliği Karışık Erişim Düzeyleriyle Bildirme'
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
ms.openlocfilehash: d74e23f33fbf7d9d29ab84b9b1bd4fc08863ac48
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349690"
---
# <a name="how-to-declare-a-property-with-mixed-access-levels-visual-basic"></a>Nasıl yapılır: Bir Özelliği Karışık Erişim Düzeyleriyle Bildirme (Visual Basic)
Bir özelliğin `Get` ve `Set` yordamlarının farklı erişim düzeylerine sahip olmasını istiyorsanız, `Property` deyimindeki daha fazla izin düzeyini ve `Get` veya `Set` deyimindeki daha kısıtlayıcı düzeyi kullanabilirsiniz. Kodun belirli bölümlerinin özelliğin değerini almasını ve kodun değeri değiştirebilmesini sağlamak için, bir özellik üzerinde karışık erişim düzeyleri kullanırsınız,.  
  
 Erişim düzeyleri hakkında daha fazla bilgi için bkz. [Visual Basic erişim düzeyleri](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
### <a name="to-declare-a-property-with-mixed-access-levels"></a>Karışık erişim düzeylerine sahip bir özelliği bildirmek için  
  
1. Özelliği normal şekilde bildirin ve `Property` bildiriminde daha az kısıtlayıcı erişim düzeyini (`Public`gibi) belirtin.  
  
2. Daha kısıtlayıcı erişim düzeyini (`Friend`gibi) belirten `Get` ya da `Set` yordamını bildirin.  
  
3. Diğer özellik yordamında bir erişim düzeyi belirtmeyin. `Property` bildiriminde belirtilen erişim düzeyini varsayar. Yalnızca özellik yordamlarından birinde erişimi kısıtlayabilirsiniz.  
  
     [!code-vb[VbVbcnProcedures#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#10)]  
  
     Yukarıdaki örnekte, `Get` yordamının özelliğin kendisiyle aynı `Protected` erişimi vardır, ancak `Set` yordamının `Private` erişimi vardır. `employee` türetilen bir sınıf `salary` değeri okuyabilir, ancak yalnızca `employee` Sınıfı ayarlayabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [Özellik Yordamları](./property-procedures.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Property Deyimi](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Visual Basic Özellikler ve değişkenler arasındaki farklar](./differences-between-properties-and-variables.md)
- [Nasıl yapılır: Özellik Oluşturma](./how-to-create-a-property.md)
- [Nasıl yapılır: Bir Özellik Yordamı Çağırma](./how-to-call-a-property-procedure.md)
- [Nasıl yapılır: Visual Basic varsayılan bir özellik bildirme ve çağırma](./how-to-declare-and-call-a-default-property.md)
- [Nasıl yapılır: Bir Özelliğe Değer Ekleme](./how-to-put-a-value-in-a-property.md)
- [Nasıl yapılır: Bir Özellikten Değer Alma](./how-to-get-a-value-from-a-property.md)
