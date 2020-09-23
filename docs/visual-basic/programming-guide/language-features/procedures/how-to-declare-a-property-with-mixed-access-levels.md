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
ms.openlocfilehash: 78363f7b2fb5b251f7409e53b2802baf83b05810
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072710"
---
# <a name="how-to-declare-a-property-with-mixed-access-levels-visual-basic"></a>Nasıl yapılır: Bir Özelliği Karışık Erişim Düzeyleriyle Bildirme (Visual Basic)

`Get` `Set` Bir özellik üzerindeki ve yordamlarının farklı erişim düzeylerine sahip olmasını istiyorsanız, deyimdeki daha fazla izin düzeyini `Property` ve ya da ifadesinde daha kısıtlayıcı olan düzeyi kullanabilirsiniz `Get` `Set` . Kodun belirli bölümlerinin özelliğin değerini almasını ve kodun değeri değiştirebilmesini sağlamak için, bir özellik üzerinde karışık erişim düzeyleri kullanırsınız,.  
  
 Erişim düzeyleri hakkında daha fazla bilgi için bkz. [Visual Basic erişim düzeyleri](../declared-elements/access-levels.md).  
  
### <a name="to-declare-a-property-with-mixed-access-levels"></a>Karışık erişim düzeylerine sahip bir özelliği bildirmek için  
  
1. Özelliği normal şekilde bildirin ve deyimdeki daha az kısıtlayıcı erişim düzeyini (gibi `Public` ) belirtin `Property` .  
  
2. `Get`Ya da `Set` daha kısıtlayıcı erişim düzeyini (gibi) belirten yordamı bildirin `Friend` .  
  
3. Diğer özellik yordamında bir erişim düzeyi belirtmeyin. Bu, bildiriminde belirtilen erişim düzeyini varsayar `Property` . Yalnızca özellik yordamlarından birinde erişimi kısıtlayabilirsiniz.  
  
     [!code-vb[VbVbcnProcedures#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#10)]  
  
     Önceki örnekte, yordam, `Get` `Protected` özelliğin kendisiyle aynı erişime sahiptir, ancak `Set` yordam `Private` erişimidir. Öğesinden türetilen bir sınıf `employee` `salary` değeri okuyabilir, ancak yalnızca `employee` sınıfı ayarlayabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [Özellik Yordamları](./property-procedures.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Property Deyimi](../../../language-reference/statements/property-statement.md)
- [Visual Basic'de Özellikler ve Değişkenler Arasındaki Farklar](./differences-between-properties-and-variables.md)
- [Nasıl yapılır: Özellik Oluşturma](./how-to-create-a-property.md)
- [Nasıl yapılır: Bir Özellik Yordamı Çağırma](./how-to-call-a-property-procedure.md)
- [Nasıl yapılır: Visual Basic'de Varsayılan Bir Özelliği Bildirme ve Çağırma](./how-to-declare-and-call-a-default-property.md)
- [Nasıl yapılır: Bir Özelliğe Değer Ekleme](./how-to-put-a-value-in-a-property.md)
- [Nasıl yapılır: Bir Özellikten Değer Alma](./how-to-get-a-value-from-a-property.md)
