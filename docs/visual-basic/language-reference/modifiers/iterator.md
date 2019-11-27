---
title: Yineleyici
ms.date: 07/20/2015
f1_keywords:
- vb.Iterator
helpviewer_keywords:
- Iterator keyword [Visual Basic]
ms.assetid: 69cb0b04-ac87-49d0-bcfe-810c0d60daff
ms.openlocfilehash: 9d7eaf186bae544031487ce027505e1e0d4ae0f3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351531"
---
# <a name="iterator-visual-basic"></a>Yineleyici (Visual Basic)
Bir işlev veya `Get` erişimcisinin bir yineleyici olduğunu belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 *Yineleyici* bir koleksiyon üzerinde özel bir yineleme gerçekleştirir. Bir yineleyici, koleksiyondaki her öğeyi tek seferde döndürmek için [yield](../../../visual-basic/language-reference/statements/yield-statement.md) ifadesini kullanır. `Yield` ifadeye ulaşıldığında, koddaki geçerli konum korunur. Yürütme, yineleyici işlevinin bir sonraki çağrılmasında bu konumdan başlar.  
  
 Yineleyici, bir işlev olarak veya bir özellik tanımının `Get` erişimcisi olarak uygulanabilir. `Iterator` değiştiricisi yineleyici işlevin veya `Get` erişimcisinin bildiriminde görüntülenir.  
  
 Her biri Için bir kullanarak istemci kodundan bir yineleyici çağırın [... Sonraki Ifade](../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
 Yineleyici işlev veya `Get` erişimcisinin dönüş türü <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>veya <xref:System.Collections.Generic.IEnumerator%601>olabilir.  
  
 Bir yineleyici `ByRef` parametreye sahip olamaz.  
  
 Bir olay, örnek Oluşturucu, statik oluşturucu veya statik yok edicisi içinde yineleyici olamaz.  
  
 Yineleyici bir anonim işlev olabilir. Daha fazla bilgi için bkz. [yineleyiciler](../../programming-guide/concepts/iterators.md).  
  
## <a name="usage"></a>Kullanım  
 `Iterator` değiştiricisi şu bağlamlarda kullanılabilir:  
  
- [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)  
  
- [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir yineleyici işlevi gösterilmektedir. Yineleyici işlevi Için bir for... içinde olan bir `Yield` ifadeye sahip [... Sonraki](../../../visual-basic/language-reference/statements/for-next-statement.md) döngü. `Main` [for each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) deyimlerinin her yinelemesi, `Power` Yineleyici işlevine bir çağrı oluşturur. Yineleyici işlevine yapılan her çağrı, `For…Next` döngüsünün bir sonraki yinelemesi sırasında ortaya çıkan `Yield` deyimin bir sonraki yürütmeye ilerler.  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, yineleyici olan bir `Get` erişimcisini gösterir. `Iterator` değiştiricisi özellik bildiriminde bulunur.  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 Ek örnekler için bkz. [yineleyiciler](../../programming-guide/concepts/iterators.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute>
- [Yineleyiciler](../../programming-guide/concepts/iterators.md)
- [Yield Deyimi](../../../visual-basic/language-reference/statements/yield-statement.md)
