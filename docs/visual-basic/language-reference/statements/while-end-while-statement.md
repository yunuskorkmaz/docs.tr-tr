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
ms.openlocfilehash: 5da05835998b2e9ef9aeefe5b00faf9e1ecb9ce2
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582266"
---
# <a name="whileend-while-statement-visual-basic"></a>While...End While Deyimi (Visual Basic)
Belirli bir koşul `True` olduğu sürece bir dizi deyim çalıştırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
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
|`condition`|Gerekli. `Boolean` ifadesi. @No__t_0 `Nothing`, Visual Basic `False` olarak değerlendirir.|  
|`statements`|İsteğe bağlı. @No__t_0 aşağıdaki `condition` her seferinde çalışan bir veya daha fazla deyim `True`.|  
|`Continue While`|İsteğe bağlı. Denetimi `While` bloğunun bir sonraki yinelemesine aktarır.|  
|`Exit While`|İsteğe bağlı. @No__t_0 bloğunun denetimini aktarır.|  
|`End While`|Gerekli. @No__t_0 bloğunun tanımını sonlandırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir koşulun bir kümesini sınırsız sayıda yinelemek istediğinizde, bir koşul `True` kaldığı sürece bir `While...End While` yapısını kullanın. Koşulu test ettiğiniz veya ne sonuçla test ettiğiniz hakkında daha fazla esneklik istiyorsanız [Do... seçeneğini tercih edebilirsiniz. Loop deyimleri](../../../visual-basic/language-reference/statements/do-loop-statement.md). Deyimlerini bir dizi defa yinelemek istiyorsanız, [için... Sonraki Ifade](../../../visual-basic/language-reference/statements/for-next-statement.md) genellikle daha iyi bir seçimdir.  
  
> [!NOTE]
> @No__t_0 anahtar sözcüğü de [Do... içinde kullanılır. Loop deyimi](../../../visual-basic/language-reference/statements/do-loop-statement.md), [Skip While yan tümcesi](../../../visual-basic/language-reference/queries/skip-while-clause.md) ve [Take While yan tümcesi](../../../visual-basic/language-reference/queries/take-while-clause.md).  
  
 @No__t_0 `True`, `statements` `End While` ifadesiyle karşılaşana kadar çalışır. Sonra Denetim `While` ifadeye döner ve `condition` yeniden denetlenir. @No__t_0 hala `True`, işlem tekrarlanır. @No__t_0, denetim `End While` bildirisini izleyen ifadeye geçer.  
  
 @No__t_0 ifade, döngüyü başlamadan önce her zaman koşulu kontrol eder. Koşul `True` kaldığı sürece döngü devam eder. Döngüyü ilk girdiğinizde `condition` `False` bir kez çalışmaz.  
  
 @No__t_0 genellikle iki değerin karşılaştırılmasının sonucunu verir, ancak [Boolean veri türü](../../../visual-basic/language-reference/data-types/boolean-data-type.md) değeri (`True` veya `False`) değerlendirilen herhangi bir ifade olabilir. Bu ifade, `Boolean` dönüştürülmüş bir sayısal tür gibi başka bir veri türünün değerini içerebilir.  
  
 Bir döngüyü diğerinin içine yerleştirerek `While` döngüleri iç içe geçirebilirsiniz. Ayrıca, farklı türlerde denetim yapılarını bir diğeri içinde iç içe geçirebilirsiniz. Daha fazla bilgi için bkz. [Iç Içe denetim yapıları](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
## <a name="exit-while"></a>Çıkış sırasında çıkış  
 [Exit While](../../../visual-basic/language-reference/statements/exit-statement.md) deyimleri `While` döngüsünden çıkmak için başka bir yol sağlayabilir. `Exit While`, denetimi hemen `End While` bildirisini izleyen deyime aktarır.  
  
 Genellikle `Exit While` bir koşul hesaplandıktan sonra (örneğin, bir `If...Then...Else` yapısında) kullanılır. Hatalı bir değer veya sonlandırma isteği gibi yineleme işleminin devam etmesi için gereksiz veya imkansız hale getiren bir koşul tespit ederseniz bir döngüden çıkmak isteyebilirsiniz. Sonsuz *döngüye*neden olabilecek bir durum için test ettiğinizde `Exit While` kullanabilirsiniz. Bu, son derece büyük veya hatta sonsuz bir sayı çalışabilen bir döngüdür. Sonra döngüyü atlamak için `Exit While` kullanabilirsiniz.  
  
 Herhangi bir sayıda `Exit While` deyimi `While` döngüsünde yerleştirebilirsiniz.  
  
 İç içe geçmiş `While` döngüleri içinde kullanıldığında, `Exit While` denetimi en içteki döngüden ve sonraki daha yüksek iç içe geçme düzeyine aktarır.  
  
 @No__t_0 deyimleri, denetimi hemen döngüsünün bir sonraki yinelemesine aktarır. Daha fazla bilgi için bkz. [Continue bildirisi](../../../visual-basic/language-reference/statements/continue-statement.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, döngü içindeki deyimler `index` değişkeni 10 ' dan büyük olana kadar çalışmaya devam eder.  
  
 [!code-vb[VbVbalrStatements#171](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#171)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `Continue While` ve `Exit While` deyimlerinin kullanımı gösterilmektedir.  
  
 [!code-vb[VbVbalrStatements#172](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#172)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir metin dosyasındaki tüm satırları okur. @No__t_0 yöntemi dosyayı açar ve karakterleri okuyan bir <xref:System.IO.StreamReader> döndürür. @No__t_0 koşulunda, `StreamReader` <xref:System.IO.StreamReader.Peek%2A> yöntemi dosyanın ek karakterler içerip içermediğini belirler.  
  
 [!code-vb[VbVbalrStatements#173](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#173)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Döngü Yapıları](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Do...Loop Deyimi](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [For...Next Deyimi](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Boolean Veri Türü](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [İç İçe Geçmiş Denetim Yapıları](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit Deyimi](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Continue Deyimi](../../../visual-basic/language-reference/statements/continue-statement.md)
