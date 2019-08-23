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
ms.openlocfilehash: 7ea0814c587f65ddc1f114d2314ac7147143d40d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965806"
---
# <a name="whileend-while-statement-visual-basic"></a>While...End While Deyimi (Visual Basic)
Belirli bir koşul olduğu `True`sürece bir dizi deyim çalıştırır.  
  
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
|`condition`|Gerekli. `Boolean`ifadesini. İse, Visual Basic olduğu gibi `False`davranır. `Nothing` `condition`|  
|`statements`|İsteğe bağlı. Aşağıdaki `While` `condition` her`True`seferinde çalıştırılan bir veya daha fazla deyim.|  
|`Continue While`|İsteğe bağlı. Denetimi `While` bloğun bir sonraki yinelemesine aktarır.|  
|`Exit While`|İsteğe bağlı. Denetimi `While` bloğunun dışına aktarır.|  
|`End While`|Gerekli. `While` Bloğunun tanımını sonlandırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir koşul `While...End While` , bir koşulun kaldığı `True`sürece belirsiz sayıda deyim yinelemek istediğinizde bir yapı kullanın. Koşulu test ettiğiniz veya ne sonuçla test ettiğiniz hakkında daha fazla esneklik istiyorsanız [Do... seçeneğini tercih edebilirsiniz. Loop deyimleri](../../../visual-basic/language-reference/statements/do-loop-statement.md). Deyimlerini bir dizi defa yinelemek istiyorsanız, [için... Sonraki Ifade](../../../visual-basic/language-reference/statements/for-next-statement.md) genellikle daha iyi bir seçimdir.  
  
> [!NOTE]
> `While` Anahtar sözcüğü de [Do... içinde kullanılır. Loop deyimi](../../../visual-basic/language-reference/statements/do-loop-statement.md), [Skip While yan tümcesi](../../../visual-basic/language-reference/queries/skip-while-clause.md) ve [Take While yan tümcesi](../../../visual-basic/language-reference/queries/take-while-clause.md).  
  
 İse, `End While` deyimle karşılaşana kadar tüm `statements`çalıştırmayasahipolur. `condition` `True` Sonra Denetim `While` ifadeye döner ve `condition` tekrar denetlenir. `condition` Hala`True`varsa, işlem tekrarlanır. Eğer ise denetim, `End While` ifadesiyle takip eden deyime geçer. `False`  
  
 `While` İfade, döngüyü başlamadan önce her zaman koşulu denetler. Durum, koşul kaldığı `True`sürece devam eder. `condition` Döngüyüilkkezgirdiğinizde,`False` bir kez daha çalışır.  
  
 Genellikle iki değerin karşılaştırılmasının sonuçları, ancak [Boolean veri türü](../../../visual-basic/language-reference/data-types/boolean-data-type.md) değeri (`True` veya `False`) olarak değerlendirilen herhangi bir ifade olabilir. `condition` Bu ifade, olarak dönüştürülmüş `Boolean`bir sayısal tür gibi başka bir veri türünün değerini içerebilir.  
  
 Bir döngüyü diğerinin `While` içine yerleştirerek iç içe geçirebilirsiniz. Ayrıca, farklı türlerde denetim yapılarını bir diğeri içinde iç içe geçirebilirsiniz. Daha fazla bilgi için bkz. [Iç Içe denetim yapıları](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
## <a name="exit-while"></a>Çıkış sırasında çıkış  
 [Exit While](../../../visual-basic/language-reference/statements/exit-statement.md) deyimleri, bir `While` döngüden çıkmak için başka bir yol sağlayabilir. `Exit While`, `End While` denetimi hemen takip eden deyime aktarır.  
  
 Genellikle bir koşul `Exit While` hesaplandıktan sonra (örneğin, bir `If...Then...Else` yapıda) kullanırsınız. Hatalı bir değer veya sonlandırma isteği gibi yineleme işleminin devam etmesi için gereksiz veya imkansız hale getiren bir koşul tespit ederseniz bir döngüden çıkmak isteyebilirsiniz. Sonsuz döngüye neden `Exit While` olabilecek bir koşul için test ettiğinizde kullanabilirsiniz. Bu,son derece büyük veya hatta sonsuz bir sayı çalışabilen bir döngüdür. Ardından, döngüyü atlamak `Exit While` için kullanabilirsiniz.  
  
 Döngüde herhangi bir yere herhangi bir `Exit While` sayıda deyim yerleştirebilirsiniz. `While`  
  
 İç içe `While` döngüler içinde kullanıldığında, `Exit While` denetimi en içteki döngünün dışına ve sonraki yüksek iç içe geçme düzeyine aktarır.  
  
 `Continue While` Ekstre, denetimi hemen döngüsünün bir sonraki yinelemesine aktarır. Daha fazla bilgi için bkz. [Continue bildirisi](../../../visual-basic/language-reference/statements/continue-statement.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, döngü içindeki deyimler, `index` değişken 10 ' dan büyük olana kadar çalışmaya devam eder.  
  
 [!code-vb[VbVbalrStatements#171](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#171)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `Continue While` ve `Exit While` deyimlerinin kullanımını gösterir.  
  
 [!code-vb[VbVbalrStatements#172](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#172)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir metin dosyasındaki tüm satırları okur. Yöntemi dosyayı açar ve karakterleri okuyan bir <xref:System.IO.StreamReader> döndürür. <xref:System.IO.File.OpenText%2A> Koşulunda, öğesinin`StreamReader` yöntemi dosyanın ek karakterler içerip içermediğini belirler. <xref:System.IO.StreamReader.Peek%2A> `While`  
  
 [!code-vb[VbVbalrStatements#173](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#173)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Döngü Yapıları](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Do...Loop Deyimi](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [For...Next Deyimi](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Boolean Veri Türü](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [İç İçe Geçmiş Denetim Yapıları](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit Deyimi](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Continue Deyimi](../../../visual-basic/language-reference/statements/continue-statement.md)
