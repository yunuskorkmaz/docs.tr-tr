---
title: Yineleyici (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Iterator
helpviewer_keywords:
- Iterator keyword [Visual Basic]
ms.assetid: 69cb0b04-ac87-49d0-bcfe-810c0d60daff
ms.openlocfilehash: 499949d1f4c20e1f465355bd076ba39f1496779b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61920724"
---
# <a name="iterator-visual-basic"></a>Yineleyici (Visual Basic)
Belirleyen bir işlev veya `Get` erişimcisinin yineleyici olduğunu.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir *yineleyici* bir koleksiyon üzerinde özel yineleme gerçekleştirir. Yineleyici [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) her öğe aynı anda koleksiyonundaki bir dönüş deyimi. Olduğunda bir `Yield` deyimine ulaşıldığında, kodun geçerli konumu korunur. Yürütme, yineleyici işlevinin bir sonraki çağrılmasında bu konumdan başlar.  
  
 Bir yineleyiciyi bir işlev veya olarak uygulanabilir bir `Get` erişimci özelliği tanımı. `Iterator` Değiştirici görünür yineleyici işlevi bildiriminde veya `Get` erişimcisi.  
  
 Bir yineleyici kullanarak istemci koddan çağırmak bir [her biri için... Sonraki deyimi](../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
 Bir yineleyici işlevinin dönüş türü veya `Get` erişimcisi olabilir <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, veya <xref:System.Collections.Generic.IEnumerator%601>.  
  
 Bir yineleyicinin içeremez `ByRef` parametreleri.  
  
 Bir yineleyiciyi bir olay, örnek oluşturucusu, statik oluşturucu veya statik yok Edicisi olamaz.  
  
 Bir yineleyici anonim bir işlevdir olabilir. Daha fazla bilgi için [yineleyiciler](../../programming-guide/concepts/iterators.md).  
  
## <a name="usage"></a>Kullanım  
 `Iterator` Bu bağlamda değiştirici kullanılabilir:  
  
- [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)  
  
- [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir yineleyici işlevi gösterir. Yineleyici işleve sahip bir `Yield` içindeki bir [için... Sonraki](../../../visual-basic/language-reference/statements/for-next-statement.md) döngü. Her bir yinelemesini [her](../../../visual-basic/language-reference/statements/for-each-next-statement.md) deyiminin gövdesinde `Main` bir çağrı oluşturur `Power` yineleyici işlevi. Her yineleyici işleve çağrı için sonraki yürütme devam eder `Yield` sıradaki yinelemesi süresince gerçekleşen deyimi `For…Next` döngü.  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, gösterir bir `Get` bir yineleyici erişimcisi. `Iterator` Özellik bildiriminde bir değiştiricidir.  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 Diğer örnekler için [yineleyiciler](../../programming-guide/concepts/iterators.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute>
- [Yineleyiciler](../../programming-guide/concepts/iterators.md)
- [Yield Deyimi](../../../visual-basic/language-reference/statements/yield-statement.md)
