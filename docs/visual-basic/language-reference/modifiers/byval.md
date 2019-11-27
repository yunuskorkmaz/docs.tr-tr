---
title: ByVal
ms.date: 07/20/2015
f1_keywords:
- vb.ByVal
- ByVal
helpviewer_keywords:
- ByVal keyword [Visual Basic], contexts
- ByVal keyword [Visual Basic]
ms.assetid: 1eaf4e58-b305-4785-9e3d-e416b9c75598
ms.openlocfilehash: a96f871c6ce119f65ebbec54fdb1471ae105d504
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351592"
---
# <a name="byval-visual-basic"></a>ByVal (Visual Basic)
Çağrılan yordamın veya özelliğin, çağıran koddaki bağımsız değişkeni temel alan bir değişkenin değerini değiştirememesi için bir bağımsız değişkenin [değere göre](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)geçtiğini belirtir. Değiştirici belirtilmemişse, ByVal varsayılandır.

> [!NOTE]
> Varsayılan olduğundan, yöntem imzalarında `ByVal` anahtar sözcüğünü açıkça belirtmeniz gerekmez. Gürültülü kod üretme eğilimi gösterir ve genellikle varsayılan olmayan `ByRef` anahtar kelimesine çok daha fazla bakmaktadır.

## <a name="remarks"></a>Açıklamalar
 `ByVal` değiştiricisi şu bağlamlarda kullanılabilir:

 [Declare Deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)

 [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)
  
 [Operator Deyimi](../../../visual-basic/language-reference/statements/operator-statement.md)
  
 [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)
  
 [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir başvuru türü bağımsız değişkeniyle `ByVal` parametresi geçen mekanizmanın kullanımını gösterir. Örnekte, bağımsız değişken `c1`, `Class1`sınıfının bir örneğidir. `ByVal` yordamdaki kodun başvuru bağımsız değişkeninin temel alınan değerini değiştirmesini önler, `c1`, ancak `c1`erişilebilir alanları ve özelliklerini korumaz.

 [!code-vb[VbVbalrKeywords#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class5.vb#10)]

## <a name="see-also"></a>Ayrıca bkz.

- [Anahtar Sözcükler](../../../visual-basic/language-reference/keywords/index.md)
- [Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
