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
ms.openlocfilehash: 00ca0ad24231128b25a988921386d6bd3265e9a0
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843719"
---
# <a name="whileend-while-statement-visual-basic"></a>While...End While Deyimi (Visual Basic)
Belirli bir koşul olduğu sürece bir deyimler serisini çalıştırır `True`.  
  
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
|`condition`|Gerekli. `Boolean` ifade. Varsa `condition` olduğu `Nothing`, Visual Basic bunu algılar `False`.|  
|`statements`|İsteğe bağlı. Bir veya daha fazla deyimlerini aşağıdaki `While`, her zaman çalıştırdığınız `condition` olduğu `True`.|  
|`Continue While`|İsteğe bağlı. Denetim bir sonraki yinelemesine aktarır `While` blok.|  
|`Exit While`|İsteğe bağlı. Dışı denetim aktarır `While` blok.|  
|`End While`|Gerekli. Tanımını sonlandırır `While` blok.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanım bir `While...End While` yapısı deyimleri belirsiz numarası bir kez, bir dizi yinelemek istediğinizde bir koşul devam ettiği sürece `True`. Daha fazla esneklikle burada koşulunu test etmek veya ne neden test Bunu tercih edebilirsiniz için isterseniz [yapın... Döngü deyimi](../../../visual-basic/language-reference/statements/do-loop-statement.md). Bir kez sayıdaki deyimleri yinelemek istiyorsanız [için... Sonraki deyimi](../../../visual-basic/language-reference/statements/for-next-statement.md) genellikle daha iyi bir seçimdir.  
  
> [!NOTE]
>  `While` Anahtar sözcüğü kullanılan ayrıca [yapın... Döngü deyimi](../../../visual-basic/language-reference/statements/do-loop-statement.md), [Atla While yan tümcesi](../../../visual-basic/language-reference/queries/skip-while-clause.md) ve [Take While tümcesi](../../../visual-basic/language-reference/queries/take-while-clause.md).  
  
 Varsa `condition` olduğu `True`tüm, `statements` kadar çalıştırma `End While` deyimi karşılaştı. Denetim için verir `While` deyimi ve `condition` tekrar denetlenir. Varsa `condition` hala `True`, işlem tekrarlanır. Varsa `False`, Denetim izleyen deyime geçer `End While` deyimi.  
  
 `While` İfade her zaman, koşul döngünün başlamadan önce denetler. Döngü devam koşul kalırken `True`. Varsa `condition` olduğu `False` döngü ilk girdiğinizde, hatta bir kez çalışmaz.  
  
 `condition` Genellikle iki değer, ancak bir karşılaştırma sonuçlarını olarak değerlendirilen herhangi bir ifade olabilir bir [Boole veri türü](../../../visual-basic/language-reference/data-types/boolean-data-type.md) değeri (`True` veya `False`). Bu ifade için dönüştürülen sayısal tür gibi başka bir veri türünde bir değer içerebilir `Boolean`.  
  
 İç içe yerleştirebilirsiniz `While` içindeki başka bir döngü yerleştirerek döngüleri. Farklı türlerde denetim yapılarını içinde başka bir iç içe yerleştirebilirsiniz. Daha fazla bilgi için [iç içe geçmiş denetim yapıları](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
## <a name="exit-while"></a>Çıkış oluştu  
 [Çıkmak sırada](../../../visual-basic/language-reference/statements/exit-statement.md) deyimi, çıkmak için başka bir yol sağlayabilir bir `While` döngü. `Exit While` Denetim takip eden deyime hemen aktarır `End While` deyimi.  
  
 Tipik olarak kullandığınız `Exit While` bazı koşullar değerlendirildikten sonra (örneğin, bir `If...Then...Else` yapısı). Gereksiz veya hatalı bir değer veya bir sonlandırma isteği gibi yineleme devam etmek mümkün kılan bir koşul algılama bir döngüden çıkma isteyebilirsiniz. Kullanabileceğiniz `Exit While` test ettiğinizde, neden olabilecek bir koşul için bir *sonsuz bir döngüye*, bir son derece büyük veya hatta sonsuz sayıda çalıştırabileceğiniz bir döngü olduğu. Ardından `Exit While` döngüden çıkma.  
  
 Herhangi bir sayıda yerleştirebilirsiniz `Exit While` herhangi bir yere deyimleri `While` döngü.  
  
 Kullanıldığında içinde iç içe geçmiş `While` döngüleri `Exit While` denetimi iç döngü dışında ve iç içe geçme daha yüksek düzeydeki içine aktarır.  
  
 `Continue While` Deyime hemen denetimi döngünün sonraki yinelemesine aktarır. Daha fazla bilgi için [Continue deyimi](../../../visual-basic/language-reference/statements/continue-statement.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, Döngüdeki deyimler kadar çalışmaya devam `index` değişkendir 10'dan büyük.  
  
 [!code-vb[VbVbalrStatements#171](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#171)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, kullanımını gösterir `Continue While` ve `Exit While` deyimleri.  
  
 [!code-vb[VbVbalrStatements#172](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#172)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir metin dosyasındaki tüm satırları okur. <xref:System.IO.File.OpenText%2A> Yöntemi dosyayı açar ve döndüren bir <xref:System.IO.StreamReader> , bir karakter okur. İçinde `While` koşulu <xref:System.IO.StreamReader.Peek%2A> yöntemi `StreamReader` dosya ek karakterler içerip içermediğini belirler.  
  
 [!code-vb[VbVbalrStatements#173](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#173)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Döngü Yapıları](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Do...Loop Deyimi](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [For...Next Deyimi](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Boolean Veri Türü](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [İç İçe Geçmiş Denetim Yapıları](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit Deyimi](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Continue Deyimi](../../../visual-basic/language-reference/statements/continue-statement.md)
