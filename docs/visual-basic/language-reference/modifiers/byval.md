---
title: ByVal (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ByVal
- ByVal
helpviewer_keywords:
- ByVal keyword [Visual Basic], contexts
- ByVal keyword [Visual Basic]
ms.assetid: 1eaf4e58-b305-4785-9e3d-e416b9c75598
ms.openlocfilehash: 1fa4c1fa0a2def02dd56fa3728a8df4b5ff16b7f
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666854"
---
# <a name="byval-visual-basic"></a>ByVal (Visual Basic)
Çağrılan yordamın veya özelliğin, çağıran koddaki bağımsız değişkeni temel alan bir değişkenin değerini değiştirememesi için bir bağımsız değişkenin [değere göre](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)geçtiğini belirtir. Değiştirici belirtilmemişse, ByVal varsayılandır.

> [!NOTE]
> Varsayılan olduğu için, `ByVal` anahtar sözcüğünü Yöntem imzalarında açıkça belirtmeniz gerekmez. Gürültülü kod üretme eğilimi gösterir ve genellikle varsayılan `ByRef` olmayan anahtar kelimeye daha fazla bakmakta olur.

## <a name="remarks"></a>Açıklamalar
 `ByVal` Değiştirici şu bağlamlarda kullanılabilir:

 [Declare Deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)

 [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)
  
 [Operator Deyimi](../../../visual-basic/language-reference/statements/operator-statement.md)
  
 [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)
  
 [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir başvuru türü bağımsız değişkeniyle `ByVal` parametre geçirme mekanizmasının kullanımını gösterir. Örnekte, bağımsız değişkeni `c1`, sınıfının `Class1`bir örneğidir. `ByVal`yordamlardaki kodun başvuru bağımsız değişkeninin `c1`temel alınan değerini değiştirmesini önler, ancak erişilebilir alanları ve `c1`özellikleri korumaz.

 [!code-vb[VbVbalrKeywords#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class5.vb#10)]

## <a name="see-also"></a>Ayrıca bkz.

- [Anahtar Sözcükler](../../../visual-basic/language-reference/keywords/index.md)
- [Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
