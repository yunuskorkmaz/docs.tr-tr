---
title: Iterator
ms.date: 07/20/2015
f1_keywords:
- vb.Iterator
helpviewer_keywords:
- Iterator keyword [Visual Basic]
ms.assetid: 69cb0b04-ac87-49d0-bcfe-810c0d60daff
ms.openlocfilehash: bb19289c69f4c523363e88e91a58f37d232b07df
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396239"
---
# <a name="iterator-visual-basic"></a>Yineleyici (Visual Basic)
Bir işlevin veya `Get` erişimcinin bir yineleyici olduğunu belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 *Yineleyici* bir koleksiyon üzerinde özel bir yineleme gerçekleştirir. Bir yineleyici, koleksiyondaki her öğeyi tek seferde döndürmek için [yield](../statements/yield-statement.md) ifadesini kullanır. Bir `Yield` ifadeye ulaşıldığında, koddaki geçerli konum korunur. Yürütme, yineleyici işlevinin bir sonraki çağrılmasında bu konumdan başlar.  
  
 Yineleyici, bir işlev olarak veya bir `Get` özellik tanımının erişimcisi olarak uygulanabilir. `Iterator`Değiştirici, Yineleyici işlevinin veya `Get` erişimcinin bildiriminde görüntülenir.  
  
 Her biri Için bir kullanarak istemci kodundan bir yineleyici çağırın [... Sonraki Ifade](../statements/for-each-next-statement.md).  
  
 Yineleyici işlevinin veya `Get` erişimcisinin dönüş türü <xref:System.Collections.IEnumerable> ,, <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.IEnumerator> , veya olabilir <xref:System.Collections.Generic.IEnumerator%601> .  
  
 Yineleyicinin herhangi bir `ByRef` parametresi olamaz.  
  
 Bir olay, örnek Oluşturucu, statik oluşturucu veya statik yok edicisi içinde yineleyici olamaz.  
  
 Yineleyici bir anonim işlev olabilir. Daha fazla bilgi için bkz. [yineleyiciler](../../programming-guide/concepts/iterators.md).  
  
## <a name="usage"></a>Kullanım  
 `Iterator`Değiştirici şu bağlamlarda kullanılabilir:  
  
- [Function Deyimi](../statements/function-statement.md)  
  
- [Property Deyimi](../statements/property-statement.md)  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir yineleyici işlevi gösterilmektedir. Yineleyici işlevinin, `Yield` için içindeki bir ifade vardır [... Sonraki](../statements/for-next-statement.md) döngü. İçindeki [her bir for](../statements/for-each-next-statement.md) Ifadesinin gövdesi için her yineleme, `Main` Yineleyici işlevine bir çağrı oluşturur `Power` . Yineleyici işlevine yapılan her çağrı, `Yield` döngüsünün bir sonraki yinelemesi sırasında ortaya çıkan deyimin bir sonraki yürütmeye ilerler `For…Next` .  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `Get` Yineleyici olan bir erişimciyi gösterir. `Iterator`Değiştirici, özellik bildirimidir.  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 Ek örnekler için bkz. [yineleyiciler](../../programming-guide/concepts/iterators.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute>
- [Yineleyiciler](../../programming-guide/concepts/iterators.md)
- [Yield Deyimi](../statements/yield-statement.md)
