---
title: GoTo Deyimi
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 22a6315e69cd6c797d462d0835e85bb1dde67dcc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="goto-statement"></a>GoTo Deyimi
Belirtilen satır yordamdaki koşulsuz olarak dallara.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
GoTo line  
```  
  
## <a name="part"></a>Bölümü  
 `line`  
 Gerekli. Herhangi bir satır etiketi.  
  
## <a name="remarks"></a>Açıklamalar  
 `GoTo` Deyimi göründüğü yordamdaki satırlar için dal. Satır etiketi bir satırda olmalıdır `GoTo` başvurabilirsiniz. Daha fazla bilgi için bkz: [nasıl yapılır: Etiket deyimleri](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).  
  
> [!NOTE]
>  `GoTo`deyimleri kodu okuma ve korumak zorlaştırabilir. Mümkün olduğunda, bir denetim yapısı kullanın. Daha fazla bilgi için bkz: [akış denetimi](../../../visual-basic/programming-guide/language-features/control-flow/index.md).  
  
 Kullanarak bir `GoTo` daldan dışında ifadesine bir `For`... `Next`, `For Each`... `Next`, `SyncLock`... `End SyncLock`, `Try`... `Catch`... `Finally`, `With`... `End With`, veya `Using`... `End Using` içinde bir etiket oluşturma.  
  
## <a name="branching-and-try-constructions"></a>Dal oluşturma ve kurulumlarını deneyin  
 İçinde bir `Try`... `Catch`... `Finally` oluşturma, aşağıdaki kurallar geçerli ile dallanma `GoTo` deyimi.  
  
|Blok veya bölge|Dallara ayırma, gelen dışında|Dallara ayırma çıkışı gelen içinde|  
|---------------------|-------------------------------|-------------------------------|  
|`Try`engelle|Yalnızca bir `Catch` aynı Yapı bloğu <sup>1</sup>|Yalnızca tüm yapım dışında|  
|`Catch`engelle|Hiçbir zaman izin verilir|Yalnızca tüm yapım dışında veya çok `Try` aynı Yapı bloğu <sup>1</sup>|  
|`Finally`engelle|Hiçbir zaman izin verilir|Hiçbir zaman izin verilir|  
  
 <sup>1</sup> varsa `Try`... `Catch`... `Finally` yapım iç içe başka içinde bir `Catch` bloğu dallanma içine `Try` blok kendi iç içe geçmiş düzeyinde, ancak diğer `Try` bloğu. İç içe bir `Try`... `Catch`... `Finally` yapım tamamen buna içerilmelidir bir `Try` veya `Catch` içinde bu iç içe geçmiş yapım bloğu.  
  
 Aşağıdaki çizimde bir gösterir `Try` yapı içinde başka bir iç içe. İki kurulumlarını bloklarını arasında çeşitli dalları geçerli veya geçersiz olarak belirtilir.  
  
 ![Try kurulumlarını dallanma grafik diyagramı](../../../visual-basic/language-reference/statements/media/trybranching.gif "TryBranching")  
Try kurulumlarını geçersiz ve geçerli dal  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `GoTo` satır etiketleri yordamdaki dala ifadesine.  
  
 [!code-vb[VbVbalrStatements#31](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/goto-statement_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yapın... Loop deyimi](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [İçin... Sonraki deyim](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [For Each... Sonraki deyim](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [If... Then... Else deyimi](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [Seçin... Case deyimi](../../../visual-basic/language-reference/statements/select-case-statement.md)  
 [Try... Catch... Finally ifadesi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [While... End While deyimi](../../../visual-basic/language-reference/statements/while-end-while-statement.md)  
 [İle... End With deyimi](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
