---
title: While...End While Deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.While
- vb.While...EndWhile
helpviewer_keywords:
- While statement [Visual Basic], While...End While
- While statement [Visual Basic]
- While...End While statements [Visual Basic]
ms.assetid: b931d1ce-e8ed-44d8-a13d-92a4f5458a1e
ms.openlocfilehash: 9f46a6ec65faef4448bdd25e30a6cc0c605cd0f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="whileend-while-statement-visual-basic"></a>While...End While Deyimi (Visual Basic)
Verilen bir koşul olduğu sürece bir dizi ifadeleri çalıştırır `True`.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
While condition  
    [ statements ]  
    [ Continue While ]  
    [ statements ]  
    [ Exit While ]  
    [ statements ]  
End While  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`condition`|Gerekli. `Boolean` İfade. Varsa `condition` olan `Nothing`, Visual Basic da işler `False`.|  
|`statements`|İsteğe bağlı. Bir veya daha fazla deyimleri aşağıdaki `While`, her çalıştırma `condition` olan `True`.|  
|`Continue While`|İsteğe bağlı. Sonraki yinelemesini denetim aktarır `While` bloğu.|  
|`Exit While`|İsteğe bağlı. Denetimin dışarı aktarır `While` bloğu.|  
|`End While`|Gerekli. Tanımını sonlandırır `While` bloğu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanım bir `While...End While` yapısı deyimleri sonsuz numarası bir kez, bir dizi yinelenecek istediğinizde bir koşul devam ettiği sürece `True`. Koşulu test burada veya ne sonuç daha fazla esneklik test, bu, tercih edebilirsiniz için istiyorsanız [yapın... Loop deyimi](../../../visual-basic/language-reference/statements/do-loop-statement.md). İfadeler kümesi birkaç kez yineleyin istiyorsanız [için... Sonraki deyim](../../../visual-basic/language-reference/statements/for-next-statement.md) genellikle daha iyi bir seçimdir.  
  
> [!NOTE]
>  `While` Anahtar sözcüğü kullanılan de [yapın... Loop deyimi](../../../visual-basic/language-reference/statements/do-loop-statement.md), [Skip While tümcesi](../../../visual-basic/language-reference/queries/skip-while-clause.md) ve [Take While tümcesi](../../../visual-basic/language-reference/queries/take-while-clause.md).  
  
 Varsa `condition` olan `True`, tüm, `statements` kadar çalışma `End While` deyimi karşılaştı. Denetim sonra geri döner `While` deyimi, ve `condition` yeniden teslim edilebilir. Varsa `condition` hala `True`, işlem tekrarlanır. Varsa `False`, Denetim geçişleri izleyen deyimine `End While` deyimi.  
  
 `While` Döngü başlamadan önce koşul ifadesi her zaman denetler. Döngü koşulunu kalırken devam `True`. Varsa `condition` olan `False` döngü ilk girdiğinizde bile bir kez çalıştırmaz.  
  
 `condition` Genellikle bir karşılaştırma sonuçlarından iki değer, ancak veren herhangi bir ifade olabilir bir [Boole veri türü](../../../visual-basic/language-reference/data-types/boolean-data-type.md) değeri (`True` veya `False`). Bu ifade için dönüştürülen sayısal bir tür gibi başka bir veri türünde bir değer içerebilir `Boolean`.  
  
 Geçirebilmenize `While` içinde başka bir döngü yerleştirerek döngüler. Ayrıca, değişik içinde bir diğer denetim yapıları yerleştirebilirsiniz. Daha fazla bilgi için bkz: [iç içe geçmiş denetim yapıları](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
## <a name="exit-while"></a>Çıkış sırasında  
 [Çıkmak sırada](../../../visual-basic/language-reference/statements/exit-statement.md) deyimi, çıkmak için başka bir yol sağlayabilir bir `While` döngü. `Exit While` aşağıdaki deyim denetim hemen aktarır `End While` deyimi.  
  
 Tipik olarak kullandığınız `Exit While` bazı koşul değerlendirildikten sonra (örneğin, bir `If...Then...Else` yapısı). Gereksiz veya hatalı bir değer veya bir sonlandırma isteği gibi yineleme devam mümkün kılan bir koşul algılama döngü çıkmak isteyebilirsiniz. Kullanabileceğiniz `Exit While` test zaman neden olabilecek bir koşul için bir *sonsuz bir döngüde*, bir son derece büyük ya da hatta sonsuz sayıda çalışacak bir döngü değil. Daha sonra kullanabilirsiniz `Exit While` döngü kaçınmak için.  
  
 Herhangi bir sayıda yerleştirebilirsiniz `Exit While` deyimlerinde herhangi bir yere `While` döngü.  
  
 Kullanıldığında içinde iç içe geçmiş `While` döngüler, `Exit While` denetimi en içteki döngü dışında ve iç içe geçme sonraki daha yüksek düzeyde uygulamasına aktarır.  
  
 `Continue While` Deyimi hemen sonraki döngü için Denetim aktarır. Daha fazla bilgi için bkz: [devam deyimi](../../../visual-basic/language-reference/statements/continue-statement.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, döngü deyimlerinde kadar çalışmaya devam `index` değişkenidir 10'dan büyük.  
  
 [!code-vb[VbVbalrStatements#171](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/while-end-while-statement_1.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanımını göstermektedir `Continue While` ve `Exit While` deyimleri.  
  
 [!code-vb[VbVbalrStatements#172](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/while-end-while-statement_2.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir metin dosyasındaki tüm satırları okur. <xref:System.IO.File.OpenText%2A> Yöntemi dosyayı açar ve döndürür bir <xref:System.IO.StreamReader> karakterleri okur. İçinde `While` koşulu <xref:System.IO.StreamReader.Peek%2A> yöntemi `StreamReader` dosyanın ek karakterler içerip içermediğini belirler.  
  
 [!code-vb[VbVbalrStatements#173](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/while-end-while-statement_3.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Döngü Yapıları](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [Do...Loop Deyimi](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [For...Next Deyimi](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Boolean Veri Türü](../../../visual-basic/language-reference/data-types/boolean-data-type.md)  
 [İç İçe Geçmiş Denetim Yapıları](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [Exit Deyimi](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [Continue Deyimi](../../../visual-basic/language-reference/statements/continue-statement.md)
