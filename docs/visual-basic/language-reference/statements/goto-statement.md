---
title: GoTo Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.GoTo
helpviewer_keywords:
- GoTo statement [Visual Basic]
- control flow [Visual Basic], branching
- unconditional branching [Visual Basic]
- branching [Visual Basic]
- branching [Visual Basic], unconditional
- branching [Visual Basic], conditional
- conditional statements [Visual Basic], GoTo statement
- GoTo statement [Visual Basic], syntax
ms.assetid: 313274c2-8ab3-4b9c-9ba3-0fd6798e4f6d
ms.openlocfilehash: 000f6754575bcce6b2d79d85541e755219aca956
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866617"
---
# <a name="goto-statement"></a>GoTo Deyimi

Bir yordamda belirtilen satıra koşulsuz olarak dallandırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
GoTo line  
```  
  
## <a name="part"></a>Bölüm  

 `line`  
 Gereklidir. Herhangi bir satır etiketi.  
  
## <a name="remarks"></a>Açıklamalar  

 `GoTo`İfadesi yalnızca, göründüğü yordamdaki satırlara dallandırır. Çizginin, başvurabilen bir çizgi etiketi olmalıdır `GoTo` . Daha fazla bilgi için bkz. [nasıl yapılır: Label deyimleri](../../programming-guide/program-structure/how-to-label-statements.md).  
  
> [!NOTE]
> `GoTo` deyimler kodun okunmasını ve bakımını kolaylaştırabilir. Mümkün olduğunda, bunun yerine bir denetim yapısı kullanın. Daha fazla bilgi için bkz. [Denetim akışı](../../programming-guide/language-features/control-flow/index.md).  
  
 Bir... `GoTo` `For` `Next` , `For Each` ... `Next` , `SyncLock` ... `End SyncLock` , `Try` .. `Catch` .,... dışında dallandırmak için bir ifade kullanamazsınız ... `Finally` , `With` ... `End With` , veya `Using` ... `End Using` oluşturma içindeki bir etikete.  
  
## <a name="branching-and-try-constructions"></a>Dallandırma ve TRY kurulumlarını  

 Bir `Try` . `Catch` .. içinde ...`Finally` oluşturma, aşağıdaki kurallar ifadesiyle dallandırma için geçerlidir `GoTo` .  
  
|Blok veya bölge|Dışarıdan içinde dallanma|İçinden dallanma|  
|---------------------|-------------------------------|-------------------------------|  
|`Try` engelleyin|Yalnızca `Catch` aynı yapım <sup>1</sup> bloğundan|Yalnızca tüm oluşturma dışında|  
|`Catch` engelleyin|Hiçbir izin verilmiyor|Yalnızca tüm oluşturma veya `Try` aynı yapı <sup>1</sup> bloğunun dışında|  
|`Finally` engelleyin|Hiçbir izin verilmiyor|Hiçbir izin verilmiyor|  
  
 <sup>1</sup> varsa `Try` ... `Catch` ...`Finally` oluşturma diğeri içinde iç içe yerleştirilmiş bir `Catch` blok, `Try` bloğa kendi iç içe geçme düzeyinde dallandırır, ancak başka bir blok içinde yer alamaz `Try` . İç içe geçmiş `Try` ... `Catch` ...`Finally` oluşturma `Try` `Catch` , içinde iç içe olan bir veya bir blok içinde tamamen bulunmalıdır.  
  
 Aşağıdaki çizimde, `Try` bir oluşturma diğeri içinde iç içe gösterilmiştir. İki kurulumlarını blokları arasındaki çeşitli dallar geçerli veya geçersiz olarak belirtilir.  
  
 ![TRY kurulumlarını içinde dallanma grafik Diyagramı](./media/goto-statement/try-construction-branching.gif)  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `GoTo` bir yordamdaki çizgi etiketlerine dallandırmak için ifadesini kullanır.  
  
 [!code-vb[VbVbalrStatements#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#31)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Do...Loop Deyimi](do-loop-statement.md)
- [For...Next Deyimi](for-next-statement.md)
- [For Each...Next Deyimi](for-each-next-statement.md)
- [If...Then...Else Deyimi](if-then-else-statement.md)
- [Select...Case Deyimi](select-case-statement.md)
- [Try...Catch...Finally Deyimi](try-catch-finally-statement.md)
- [While...End While Deyimi](while-end-while-statement.md)
- [With...End With Deyimi](with-end-with-statement.md)
